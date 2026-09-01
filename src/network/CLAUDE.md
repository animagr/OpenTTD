# src/network/ — multiplayer, coordinator, content and admin

Five separate protocols share this directory. [core/](core/) holds the transport layer common to all of them — packets, TCP/UDP sockets, address handling, HTTP backends (curl / WinHTTP / none) — and the files one level up implement each protocol on top.

| Protocol | Files | Purpose |
| --- | --- | --- |
| Game | `network_client.cpp`, `network_server.cpp`, `core/tcp_game.*` | The actual multiplayer session |
| Coordinator | `network_coordinator.cpp`, `network_stun.cpp`, `network_turn.cpp` | Server listing and NAT traversal, so servers work without port forwarding |
| Content | `network_content*.cpp` | Downloading NewGRFs, AIs, scenarios, base sets |
| Admin | `network_admin.cpp`, `core/tcp_admin.*` | External tools controlling a server; documented in [../../docs/admin_network.md](../../docs/admin_network.md) |
| Survey | `network_survey.cpp` | Opt-in anonymous statistics |

## Protocol versions are compatibility contracts

Each protocol carries its own version constant in [core/config.h](core/config.h):

```cpp
static const uint8_t NETWORK_GAME_ADMIN_VERSION  = 3;
static const uint8_t NETWORK_GAME_INFO_VERSION   = 7;
static const uint8_t NETWORK_COORDINATOR_VERSION = 6;
static const uint8_t NETWORK_SURVEY_VERSION      = 2;
```

These are not the game version and do not move with it. Bump one only when the wire format of *that* protocol changes, and keep the reader able to handle older versions — the coordinator, the content server and third-party admin tools are all deployed independently of any given client. Adding a field to game-info means bumping `NETWORK_GAME_INFO_VERSION` **and** leaving the parse path for versions 1..6 intact.

Client/server game compatibility is separate again: clients only join servers with a matching build revision (`NETWORK_REVISION_LENGTH`), so the in-session protocol does not carry a version of its own.

## Packets

Everything is written and read through `Packet` ([core/packet.h](core/packet.h)) with explicit-width, big-endian `Send_uint8` / `Recv_uint16` style calls. Never memcpy a struct onto the wire — layout and endianness differ across the platforms OpenTTD ships on.

Sizes worth knowing: `UDP_MTU` is 1460, `TCP_MTU` is 32767 (with an encoding that leaves room to grow past it — see the comment in `config.h`), and `COMPAT_MTU` of 1460 is what older peers assume. Field length limits (`NETWORK_CLIENT_NAME_LENGTH`, `NETWORK_CHAT_LENGTH`, …) are also in `config.h` and are part of the protocol; a receiver must not trust the sender to respect them.

**Treat every incoming packet as hostile.** Validate lengths and enum ranges on receive; a malformed packet must disconnect the peer, not crash the server or index out of bounds.

## Desyncs

Multiplayer synchronisation works by shipping a savegame at join time and then replaying only *commands* — see [../../docs/desync.md](../../docs/desync.md) and the "Game state vs. client-local state" section of [../CLAUDE.md](../CLAUDE.md). The practical rule: this directory transports commands but must never *change* what they do. Anything that makes command execution depend on which machine ran it is a desync.

`-DRANDOM_DEBUG` in `CXXFLAGS` and the recording facilities described in [../../docs/debugging_desyncs.md](../../docs/debugging_desyncs.md) are the tools for chasing one down.

## Crypto

`network_crypto.cpp` / `network_crypto_internal.h` implement the authentication handshake (X25519 key exchange, password-authenticated) on top of [../3rdparty/monocypher/](../3rdparty/monocypher/). This is the one part of the directory with unit-test coverage: `test_network_crypto.cpp` in [../tests/](../tests/). Do not modify the handshake without running it, and do not invent new key handling — use what monocypher provides.

## Conditional sources

Networking is always compiled in — there is no `ENABLE_NETWORK` switch — but the HTTP backend is picked at configure time in [core/CMakeLists.txt](core/CMakeLists.txt): `http_curl.cpp` when curl is found, `http_winhttp.cpp` on Win32, and the stub `http_none.cpp` otherwise. Anything you add to the HTTP path needs to work, or be absent, in all three.
