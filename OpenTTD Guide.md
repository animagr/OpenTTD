# OpenTTD Guide

A complete beginner-to-intermediate guide to **OpenTTD**, built from the official wiki manual. It opens with the getting-started tutorial (bus route, train route, plane route), then covers world generation for your first real map, and then goes topic by topic through the detailed construction, fleet-management and settings articles.

Part 1 is the walkthrough. Follow it top to bottom and you will have a working transport company in about 30 minutes. Everything after it is reference: read a section when you need it.

**Tip that applies everywhere:** hover the mouse over any button for two seconds and a tooltip explains it. Right-clicking a button does the same if your hover delay is set to 0.

---

## Quick Reference

### The core loop

- Find two places that want to trade: a coal mine and a power station, two towns, an oil rig and a refinery.
- Build a station at each end, covering the industry or the houses.
- Connect them with road or rail. Planes and ships need no infrastructure between the endpoints.
- Build a depot, buy a vehicle inside it, give it orders, then press the red **Stopped** button to start it.

### Money facts

- The further you carry cargo, the more it pays. Do not pick two industries that sit right next to each other.
- Coal mine to power station is the simplest and most profitable starting route.
- Income depends on the total time between loading and delivering, so slow trains and long waits cost you money.
- Removing rail track refunds some money. Removing road costs you money.
- Raising land out of the sea is extremely expensive and can bankrupt a young company.

### Essential hotkeys

- A - Autorail. Hold Ctrl while dragging to remove track instead.
- R - toggle the Remove tool on any construction toolbar.
- D - Dynamite, also the clear-land tool.
- X - toggle transparency of trees and buildings. Very useful while building.
- Q - raise land. W - lower land. E - level land.
- U - buy land. I - plant trees. O - place a sign.
- 5 - build road vehicle depot. 7 - build train depot.

### The three rules that prevent most beginner disasters

- Only place a signal where you are happy for a train to stop and wait.
- Never place a signal so close to a junction that a waiting train sticks out into it. Count the tiles of your longest train.
- Make station platforms long enough for the whole train, or loading takes much longer.

---

## Part 1: Getting Started

This is the wiki general gameplay tutorial. It takes about 30 minutes and ends with a bus service, a train route and an air route all running.

### Starting the game

When OpenTTD opens you get the main menu.

- Click **New Game**. This opens the World Generation screen, which is full of options. Leave them all at their defaults for now.
- The four images at the top of that screen change the climate. Ignore them for this run.
- Click the big green **Generate** button. The game builds a world and drops you into it.

### Inside the game

The green landscape in the middle of the screen is the world you will be taming with roads, railways, docks and airports. You may see an industry, a town or a forest already.

- Along the top is the menu bar. Every construction toolbar opens from here.
- Some buttons open menus. Hold the left mouse button down, move down the menu, and release on the option you want.
- Hold the **right** mouse button and drag to scroll the map around. You will do this constantly.

### The grid and the viewing angle

You always view the world from the South, and the world is a grid of square tiles.

- Almost everything must follow the gridlines on the Northwest-Southeast or Southwest-Northeast axes.
- One of the few exceptions is level railway track, which can also run horizontally or vertically.
- Bus stations, hill slopes, bridges and tunnels all follow the grid.

## Your First Bus Service

A passenger bus route inside one town is the cheapest thing you can build and the easiest way to learn the interface.

### Finding a town

- Right-click and drag to move around the map until you find a group of houses. That is a town.
- Each town shows its name in the middle, with its population in brackets after it.
- Look for a town of **500 inhabitants or more**.

### Building bus stations

1. Click the **Road construction** button on the menu bar. A toolbar of road-related buttons appears.
2. Click **Build Bus Station**. The Bus Station Orientation window appears with six choices.
3. The left four orientations are dead-end bus termini that you build on a tile next to a road. The right two are drive-through stops that you build on top of an existing road.
4. Find a free tile next to a road, near some houses.
5. Choose the orientation that puts the station entrance facing the road.
6. Left-click the tile to build. A red number floats up showing what you just spent. If you got the orientation right, the road extends into your bus station.
7. Repeat for a second bus station in a different part of the same town.

### Buying a bus

All vehicles of every type are built inside depots.

1. Click the **Depot** button on the Road construction toolbar and place a road vehicle depot the same way you placed the stations. Build it near one of the bus stations. It does not need houses around it.
2. Click your new depot. The depot window opens, listing the vehicles inside it, currently none.
3. Click **New Vehicles** at the bottom. A window lists every vehicle available to you right now. At the top of an early-game list you will find the **MPS Regal** bus.
4. Click the bus to select it, then click **Buy Vehicle**. A vehicle window opens for your new bus.
5. Close the depot window with the x in its top-left corner. You do not need it any more.

### Giving orders to your bus

1. In the vehicle window, click the **Orders** button.
2. Click **Go To**, then click your first bus station on the map with the special go-to cursor. This adds the instruction **Go to (station name)**.
3. Click **Go To** again and add your second station the same way.
4. When a vehicle reaches the end of its order list it starts again from the top, so two orders make a loop.
5. In the vehicle window, click the red **Stopped** bar at the bottom. Your bus leaves the depot and starts driving.

Passengers gather at the stations over time, your bus collects them, and green numbers float out of it when it delivers them. That is income.

This route will not be very profitable. It is short and a bus carries few passengers. That is fine. You need many services to build an empire, and you have just learned the pattern that all of them follow.

## Your First Train Route

Trains are faster than road vehicles and carry far more, but they cost more and need real planning.

The simplest and most profitable thing in the game is hauling **Coal** from a **Coal Mine** to a **Power Station**, so that is what we will build.

### Locating your route

- Scroll around until you find a coal mine and a power station reasonably near each other.
- For the tutorial the distance does not matter much. In a real game, do not pick them too close, because longer hauls pay more.

### Building the train stations

1. Open the **Railway Construction** toolbar from the menu bar.
2. Click **Build railroad station**. The station selection window appears.
3. Set **Number of Tracks** to 1 and **Platform Length** to 3. Each length unit holds two carriages, so a 3-tile station fits one locomotive and five carriages.
4. Pick the orientation that lets you run track in the direction you need.
5. Find ground next to the coal mine that is flat and clear of everything except trees, long enough for the station in the orientation you chose.
6. Turn on **Coverage area highlight** to see the tiles the station will serve. Make sure the coverage covers the coal mine.
7. If you cannot find flat ground, try the other orientation, or move a little further from the mine. Not so far that the coverage no longer touches it, or you will pick up no coal.
8. Click to place the station.
9. Build a second station next to the power station the same way.

### Connecting the stations

1. Click the **Autorail** button on the Railway Construction toolbar, shortcut **A**.
2. Drag in a straight line from one station towards the other to lay track.
3. Keep adding sections until you reach the other station. A simple route is often just two drags: one long straight, one approach.
4. If you make a mistake, use the **Dynamite** tool, shortcut **D**, to remove track.

### Adding a train

Trains cannot appear on your track by magic. You need a train depot.

1. Click **Build train depot** on the Railway Construction toolbar. A window offers you orientations.
2. Place the depot so its front entrance faces onto your track. Both the depot tile and the adjacent track tile must be on flat ground.
3. Connecting rails are added automatically so trains can enter and leave.
4. Click the new depot to open the depot window. It is empty.
5. Click **New Vehicles**, pick a locomotive from the top of the list, and click **Buy Vehicle**. A train window opens.
6. Scroll down the new vehicles list and buy six coal wagons.
7. Six is one too many for a 3-tile station. Drag any wagon onto the sell button in the depot window and release. It is sold back and you get money returned.

### Giving orders to your train

1. Give the train orders exactly as you did with the bus: **Orders**, then **Go To** each station.
2. In the order list, click the coal mine station line to select it, then click **Full Load**. The train now waits until it is completely full of coal before leaving.
3. Click the **Stopped** button at the bottom of the train window to start it.

Once the train loads and delivers, you will see it makes far more money than the bus.

This is the simplest railway in the game and it can handle **exactly one train**. Buy a second one and it will just sit in the depot, because there is nowhere for the two to pass. Part 2 fixes that.

## Your First Plane Route

Airports and aircraft are expensive, but they are easy. You do not have to build anything between them.

### Finding airport locations

- Right-click and drag to move around the map. Look for a town with **1000 inhabitants or more**.
- The town also needs enough clear room for a Small Airport, which is 3 by 4 tiles.

### Building an airport

1. Click the **Airport** button on the main toolbar to open the Airport Construction toolbar.
2. Click **Build Airport**. The Airport Selection window opens.
3. At the start of the game only the **Small Airport** is available. Better airports unlock as the years pass.
4. Turn on **Coverage area highlight**.
5. Move the cursor over the map. White squares show where the airport will sit; purple squares show which houses and industry tiles will actually use it. Houses outside the purple squares will not use your airport, so place it to cover as many houses as possible.
6. For an industrial airport, watch the **Accepts** and **Supplies** lines at the bottom of the Airport Selection window instead. Just make sure your cargo is listed there.
7. Left-click to build. You may need to level the ground first with the landscaping tools.
8. Build a second airport in another town. Leave real distance between the two or your planes will not earn much. You need at least two airports before you can run a service.

### Buying a plane

1. Click the **hangar** building inside the airport you want the plane to start from. The Aircraft Hangar window opens.
2. Click **New Aircraft** at the lower left. The New Aircraft window opens.
3. Browse the list, select an aircraft, and press **Build Aircraft**. By default it is fitted for maximum passengers plus some mail.
4. Give it orders the same way as the bus and the train, then start it.

## Where To Go From Here

You now have a transport company with three kinds of service running. What happens next is up to you: a thousand bus routes across the map, or a forest feeding a nearby sawmill. Keep the company profitable and you might end up the greatest Transport Tycoon by 2050.

When you are ready to abandon the tutorial map and start a real game, the next section explains every option on the World Generation screen. After that, Part 2 turns a one-train railway into a real network, and the remaining parts cover each construction tool, the fleet-management screens, and the settings menus in detail.

### The in-game interactive tutorial

OpenTTD ships with a downloadable interactive tutorial that covers much the same ground as this walkthrough but guides you inside the game.

Its chapters are Introduction, Navigation, Aircraft, Ships, Trucks and industry chains, Buses and town growth, and Rail, which is incomplete.

1. Click **Play Scenario** in the main menu.
2. Click **Check Online Content** at the lower left.
3. Download the **Beginner Tutorial**. Use the filter to narrow the list if you like.
4. Close the download window.
5. Select **Beginner Tutorial** in the Load Scenario window.
6. If you see red text about missing files, click **find missing content online** and download the NewGRF the tutorial needs.
7. Click **Load** and follow the instructions in the game.

---

## Starting a Real Game: World Generation

Part 1 told you to leave the World Generation screen alone, and the defaults do make a perfectly good first game. This section explains what every option on that screen actually does, so you can shape the map deliberately next time.

**Play Heightmap**, next to New Game on the main menu, starts a game on a map generated from a heightmap image instead of a random one.

### Recommended settings for a first real game

- **Climate:** Temperate. It has no special rules to learn and the full vehicle selection.
- **Map size:** 512 by 512. Plenty of room for a single-player game.
- **Terrain type:** Flat or Hilly. Mountains look great but eat your construction budget in terraforming.
- **Date:** 1950, the default. Early enough for the vehicle progression to be interesting, late enough that the starting vehicles are not painful.
- **No. of Towns and No. of Industries:** Normal.
- **Rivers and Sea Level:** defaults are fine. Rivers give you something to bridge.
- Leave everything else alone until you know what you want to change.

### Climate

The top row of four images selects the climate: **Temperate**, **Sub-arctic**, **Sub-tropical**, and **Toyland**, left to right.

- Sub-arctic and sub-tropical have their own special rules about where industries appear and what towns need to grow.
- Toyland has a limited vehicle selection.
- Temperate is the one to learn the game in.

### Map size

How big the map is, from 64 tiles up to 4096.

For single-player, **512 by 512 gives you plenty of room**. Bigger maps are not automatically better; they mostly mean more scrolling and slower town and industry coverage.

### Terrain type

This sets the height of hills and mountains by setting the map maximum height. The presets are Very flat, Flat, Hilly, Mountainous and Alpinist.

- With **Custom height** selected you set the limit yourself. The default is 30 and the range is 1 to 255.
- With any preset selected, the height limit is **scaled to the length of the shortest map edge**.
- That scaling exists because OpenTTD cannot support a slope steeper than 1 to 1. Without it, a single mountain on a small map would cover the whole thing in slopes.

### Maximum map height by preset and map size

Each line gives the height limit for that preset at shortest-edge lengths of 64, 128, 256, 512, 1024, 2048 and 4096 tiles.

- Very flat: 3, 3, 3, 3, 4, 5, 7
- Flat: 5, 7, 8, 9, 14, 19, 31
- Hilly: 8, 9, 10, 15, 23, 37, 61
- Mountainous: 10, 11, 17, 19, 49, 63, 73
- Alpinist: 12, 19, 25, 31, 67, 75, 87

The practical takeaway: on a small map, picking Alpinist does far less than you would expect. Alpinist on a 64-tile map tops out at height 12, barely above Very flat on a 4096-tile map.

### Variety distribution

Controls whether the map mixes mountains and flat areas rather than being uniformly one or the other. The higher the variety, the bigger the difference in elevation between the mountainous parts and the flat parts.

### Smoothness

Controls the shape and number of hills.

- **Smooth** landscapes have fewer, wider hills.
- **Rough** landscapes have more, smaller hills.

Wider hills are easier to build across, because you get long consistent slopes instead of constant small changes.

### Rivers

How many rivers to generate. Rivers are the only way to get inland water without paying for canals, so they are worth having if you intend to run ships.

### Snow coverage

Only available in the **Sub-arctic** climate. Sets the approximate percentage of the map covered in snow.

Snow is not just decoration: it affects industry generation and town growth requirements. Sea level and coast tiles never have snow.

How it works, which explains its one quirk:

- The generator picks a height such that roughly your chosen percentage of tiles sit above it, then fills everything above that height with snow.
- Choose 10 percent coverage and it finds the height with about 10 percent of tiles above it.
- Land you raise later by terraforming above that line **does** become snowy.
- But the calculation runs **only once**, when the map is first generated. Terraforming never moves the snow line itself.

### Date

The year your game starts. The default is 1950.

The year controls the availability of vehicles and infrastructure, among other things. Starting earlier means a longer technology progression and weaker starting vehicles; starting later hands you better equipment immediately.

### No. of Towns

How many towns are generated. The actual count also depends on map size.

Options are Very Low, Low, Normal, High and **Custom**, which lets you set anywhere from 1 to 5000.

### No. of Industries

How many industries are on the map, again scaled by map size. Options are User funded, Minimal, Very Low, Low, Normal, High and Custom.

- **User funded** generates no industries at all. You have to fund every one yourself.
- **Minimal** generates exactly one of each industry.
- **Custom** lets you set anywhere from 1 to 9999.
- For the Very Low to High range, the useful pairing is inverted from what you might guess: **lower values suit larger maps, higher values suit smaller maps**.

### Sea Level

The percentage of the map that is ocean. With **Custom** selected you can set it anywhere from 1 to 90 percent.

### Map Edges

Controls whether the map edges are at sea level or whether land can run right up to them.

- **Random** lets the generator decide independently for each edge.
- **Manual** gives you four buttons, one per edge. Set an edge to **Water** to make the whole edge ocean, or **Freeform** to allow both water and land along it.

### AI, Game Script and NewGRF settings

The **AI settings**, **Game Script Settings** and **NewGRF Settings** buttons on this screen open the same menus you can reach from the main menu.

They are duplicated here so you can change them without leaving the New Game screen and losing the world settings you have already chosen.

Setting up AI competitors is covered in Part 9.

When everything is set, press **Generate**.

---

## Part 2: Growing the Railway

Part 1 left you with two stations, one length of track and one train. This part adds platforms, signals, a second track and finally a second mine, which turns the line into a network. Work through it in order.

### Why one train is the limit

Only one train is allowed in a **block**, the section of track between two signals, and that is how the game prevents collisions. With no signals at all, your whole line is one block, so it holds one train.

Everything in this part is about splitting the line into more blocks and giving trains places to pass each other.

## Adding a Second Platform

The single-platform layout is inefficient: you pay to maintain all that track and only one train can use it.

If the coal mine produces enough, you want a second train. Always having a train ready to load raises your station rating, which means the industry delivers more of its output to your station.

Before a second train is useful, it needs somewhere to stand at the mine. Then while one train loads, the other runs to the power station, unloads and comes back.

### Building the platform

- Build an extra platform next to the original coal mine station. As long as the new platform **touches** the original station, it joins that station rather than becoming a separate one.
- Build track to connect the new platform to your existing line.
- Leave at least one piece of straight track in front of each platform. Signals go there.
- Make sure both platforms can be reached from the depot.
- If the old depot is in the way, blow it up with the Dynamite tool and build a new one elsewhere.

## Signals

Signals stop trains crashing into each other. You need a couple before you run a second train.

Click **Build Railway Signals** on the Railway Construction toolbar to open the Signal Selection toolbar.

### How many signal types you actually need

There are six signal types in OpenTTD, and almost every need is met by two of them: the **path signals**. Ignore the other four until you are building something unusual.

- The default Signal Selection toolbar shows only path signals. The advanced toolbar shows all of them.
- If your toolbar shows twelve buttons rather than six, the upper six are **semaphores**. They are functionally identical to the light signals below them and only look different, giving track a more classical look.
- Semaphores are placed automatically instead of light signals before the year set by **Automatically build semaphores before**, which defaults to 1950. That setting is in Advanced Settings under Construction, then Signals.
- Broadly, semaphores suit games before the 1970s and modern light signals suit later ones. It is purely cosmetic.

### The two path signals

- The **two-way path signal** can be passed from both sides, but a train only obeys it if the driver can see the light from the front.
- The **one-way path signal**, which has a horizontal red bar, behaves the same but can only be passed from the front.

### How path signals think

Path signals are smart: they consider the route a train wants to take.

- When a train reaches a path signal it **reserves** its route through to the next signal.
- A second train may enter the same junction as long as its own path does not cross that reservation.
- If it does need to cross a reserved path, it waits at the signal until it can make its own reservation.
- The one rule that follows from this: **only place a signal where you want a train to be able to wait**.

You can see reservations in-game by enabling Advanced Settings, then Interface, then Display options, then **Show reserved tracks**. Reserved track is drawn darker. It is off by default.

### Placing your first signals

1. Select the **two-way path signal**.
2. Click the first piece of track in front of a platform to build a signal there.
3. Make sure the signal faces the platform. You may need to click the tile a second time to turn it around.
4. Repeat for the other platform.

You do **not** need a signal in front of a depot. Depots have built-in signals.

You may read elsewhere that stations do not need path signals in front of them. That is partly true for terminus stations but false for through stations. If you are new to signalling, put signals in front of terminus stations anyway. They look better, and if you later convert the terminus into a through station you will not have to remember to add them.

### Telling block and path signals apart

- Block signals are **smaller** and show a green light when no train is blocking the section after them.
- Path signals are **taller** and show red until a train reserves a path through them.
- If that is confusing, just use path signals everywhere. The placement rules are the same.

## Adding a Second Train

Everything is ready for train number two. Click the depot to open the depot window.

- You can buy it from scratch exactly as before.
- Or click **Clone Train** at the bottom of the depot window and then click the first train. You get an identical copy including its orders, and only need to start it.
- Hold **Ctrl** while clicking the train you are cloning and the two trains will **share** orders instead of copying them. Change one order list and the other changes automatically. This is worth doing.

## Using Two Tracks

With multiple trains on a single track, a train can wait a long time for the track to clear, especially on a long line. There are two fixes: a passing siding, or fully doubling the track.

### The passing siding

A passing siding is a short doubled section guarded by signals. It is cheap, but it causes delays when trains are not well synchronised.

- Make the siding long enough for the longest train that will use it. If your platforms are five tiles, make the siding five tiles too.
- A signal also occupies a tile, so the finished siding ends up somewhat longer than five tiles.
- Use **one-way path signals**. Two-way path signals work, but in some situations trains sneak ahead; the one-way version prevents that.
- Leave enough space for a train to wait at each signal.

On a long route you can add several passing sidings at different points. If that still is not enough for your traffic, double the whole track.

### Completely doubling the track

Double track gives one one-way track in each direction. It handles many more trains because they never meet head-on and are never forced to reverse.

- The first step is basically building one very long passing siding between the two stations. That alone is enough to run a third train.
- But with only the two end signals, the line still only handles one train in each direction, because there are still only two blocks.

### Adding intermediate signals

More signals means more blocks means more trains in the same direction.

- On a plain stretch with no junctions you do not need path magic, so the basic **standard block signal**, the leftmost button on the signal toolbar, is fine.
- Signal spacing is not critical. For a realistic look, space them at least a train length apart. For higher capacity, place them close together.
- Only place a signal where you want a train to wait.
- **Never** place a signal immediately after a junction. A train waiting there blocks the junction. Count the tiles of your longest train from the junction and place the signal on the next tile after that. For a five-tile train, count five tiles and put the signal on the sixth.

### Making block signals one-way

Standard block signals are two-way by default.

- Click a tile to place the signal.
- Click the same tile again with the signal tool active to make it one-way.
- Click once more to make it one-way in the other direction.
- Click again to return it to two-way.

Trains can never pass a one-way standard block signal from the wrong side.

A doubled line with intermediate signals in the tutorial example has room for six trains, although four run much more smoothly. One track is dedicated to trains heading for the power plant, the other to trains returning to the mine.

### A second platform at the other end

You already built a second platform at the coal mine. If traffic gets heavy, add one at the power plant too. The principle is identical.

If the two stations are far apart, consider a depot at the other end of the line as well. With **Breakdowns** enabled this gives trains a second chance to be serviced, which means fewer breakdowns.

## Building a Basic Network

Point-to-point lines work well. The next step is combining several of them, which is all a network is.

The advantage is reuse: existing track serves more than one purpose. In this example we connect a second coal mine to the platforms at the power plant we already have.

### Connecting the new line

- Build the station at the second mine and add signals exactly as you did before.
- Where you join the existing network matters less than you would think, but some places are more practical than others. The best way to learn is by doing.

The obvious simple connection has a trap in it. If your new junction leaves only four tiles of track before the next signal, a five-tile train waiting at that signal will stick out and block the path to and from the second mine.

With few trains this only causes small delays. The fix is to move the signal one tile further from the junction.

### Removing and moving signals

Moving a signal means placing a new one and removing the old one. Dynamite removes the track along with the signal, which is not what you want.

1. Click **Place Railway Signal** on the Railway Construction toolbar.
2. Click the **Bulldozer** button. The signal tool switches from building to removing, and the white square turns red.
3. Click a signal to remove it. Click and drag to remove a line of signals.
4. Click the Bulldozer button again to go back to building. Shortcut **R**.

**Warning:** removing signals in a live network can cause crashes. To be safe, stop all trains near the area first, make your signal changes, then restart the trains one at a time.

### Bridges in a network

The simple connection above leaves a piece of single track towards the second mine. With a lot of trains that becomes a bottleneck.

A bridge fixes it: trains heading to the power plant run on one side and trains leaving it run on the other, so the two flows never share a tile. Use the **Build Bridge** button on the Railway Construction toolbar.

Every large, impressive OpenTTD network is built from exactly the techniques in this part. They are just repeated more times.

---

## Part 3: Railway Construction in Detail

Everything about rail, in the order you tend to need it: laying track, station layouts, depot placement, signal mechanics, buying and rebuilding trains, and upgrading a line to a new rail type.

## Laying Track

Open the railway construction toolbar with the railway build button on the menu bar. There are two ways to lay track.

- The four directional track buttons: easy but slow.
- The **Autorail** tool: fast, slightly less obvious. Shortcut **A**.

Besides flat land you can also build on slopes, controlled by the **Build on slopes** setting.

### Using the directional track buttons

1. Click one of the four rail building buttons.
2. Move the cursor over the tile where the track should start.
3. Click and drag to where the track should end.
4. Release. The new track appears.

### Using Autorail

1. Select the **Autorail** button, or press **A**. The cursor changes.
2. For horizontal or vertical straight pieces, put the cursor on a tile and click and drag along the tiles. White lines preview the track.
3. Click in a tile and move the mouse in different directions to see how the track would be laid before you commit.
4. Release to build.
5. Diagonal track works the same way: click and drag from one tile to another.
6. A diagonal track occupies only half a tile, so **two diagonal tracks fit in one tile**. A horizontal or vertical track uses the whole tile.
7. Autorail previews correctly on hilly ground, but terrain must be sloped appropriately, and you cannot lay diagonal track over hills.

### Removing track

- The quick way: **hold Ctrl** and click and drag along existing track, exactly as if you were building it. Release and the track is removed.
- The other way: select the **Remove** tool, shortcut **R**. The white rail lines turn red. Click and drag along the track to remove it. Click the button again to deselect.
- Where two diagonal pieces share a tile, you must click the actual piece you want gone. Clicking anywhere in the tile is not enough.
- Unlike road, removing track gives you some money back.
- Dynamite, shortcut **D**, also works but clears the whole tile.

### Track connection angles

- A **45 degree** connection can be taken at full speed. But a train sitting on more than one 45 degree connection at the same time slows down.
- A **90 degree** connection slows a train down considerably every single time.
- With the advanced setting **Forbid trains and ships to make 90 degree turns** enabled, trains cannot take a 90 degree connection at all. They stop and reverse as if at the end of the line.

Mastering **A** for Autorail, **Ctrl** plus drag for removal, **D** for dynamite and **X** for transparency makes track laying dramatically faster.

## Railway Stations

1. Open the **Railway Construction** toolbar.
2. Click **Build railroad station**. The Rail Station Selection window appears.
3. Set **Number of Tracks** and **Platform Length**. Each length unit holds two carriages or engines, so a platform length of 3 accepts one engine and five carriages. Longer trains can still stop there, but loading and unloading will be slow.
4. Select the orientation that runs the track in the direction you need.
5. Find a place on the map. You can build on slopes as well as flat land, and you can build over existing straight track.
6. Click to build.

### Two rules for any station design

- Trains should not cause traffic jams entering or leaving.
- Platforms should be long enough for trains to fit completely, or loading times get long.

When signalling a station, remember your longest train must be able to wait at every signal without blocking a junction.

### Single stations

- A **single terminus station** serves one train at a time. Fine when there is not much cargo to move.
- A **single Ro-Ro station**, short for roll-on roll-off, lets incoming trains avoid waiting for outgoing trains to leave. The benefit is small at one platform but grows a lot with more platforms.
- Good practice for Ro-Ro: run the loading-exit and unloading-entrance lines straight into the station, and let the loading-entrance and unloading-exit lines loop around. Cargo gets delivered faster and loaded trains leave faster.
- A single Ro-Ro station needs no path signals at all, because it is effectively a single one-way track. Adding them changes nothing.

### Double stations

Two platforms are preferable for any station handling real volume, and this is the type you will build most often. As soon as one train finishes loading the next can start, with no wait for the first to clear the station.

- The **double terminus station** is cheaper and takes less space, but trains must cross at the junction either entering or leaving.
- The **double Ro-Ro station** avoids all crossing and waiting. It performs considerably better than the double terminus once more than three trains use the station.

### Multi-track stations

When many trains use a station, more platforms is the simple answer. **If more than one train is waiting to enter a station, it has too few platforms.**

- Four-track terminus and four-track Ro-Ro stations both work well. Bigger is no harder: add platforms, make sure trains can enter and exit each one, and signal it properly.
- The four-track terminus is a good alternative to Ro-Ro when space is tight, accepting that trains sometimes wait to let others pass.
- The four-track Ro-Ro means incoming trains never wait for departing ones.

### Through stations

A through station can be entered and left from both ends. It suits passenger lines that hop from town to town to town.

- The **double one-way through station** has one platform per direction. It is just a double-track railway with platforms on it: no junctions, no special signals.
- The **double two-way through station** lets trains from both directions use both platforms, which needs junctions and signalling. If two trains arrive from the same direction in quick succession and nothing is coming the other way, the second can use the far platform. This layout only works with path signals, and it is prone to deadlocks if several of them sit close together.
- The **multi-track through station with dedicated platforms** solves that deadlock. You need at least three platforms: the outer platform on each side is one-way, one per direction, and the middle platforms are two-way. Trains from either direction always have a platform available.
- A **double through station with depots** puts a depot on each side. Trains inside can leave in either direction, and because trains can duck out of a platform into the depot, it deadlocks far less than the depot-less version.

## Railway Depots

Depots are where you build new trains and where existing trains are serviced. Trains must be able to both enter and leave them.

### Placing a depot

1. Click the railway build button on the menu bar to open the railway construction toolbar.
2. Click the **new depot** button, or press **7**. The Train Depot Orientation window opens.
3. Select the direction the depot should face. This decides how trains enter and leave.
4. Place the depot next to your track with the exit facing the track. Slopes are allowed as well as flat land.
5. Click to place it. If there are rails adjacent, connecting track is added automatically.

Dynamite removes a depot.

### Where to put depots

Two goals: trains get serviced effectively, and servicing does not cause traffic jams. Two broad strategies:

- Service trains at set time intervals, or add a depot to the train orders list. Depots go into orders exactly like stations and waypoints.
- Or build the rails so trains are **forced** through a depot every time they pass a station or a stretch of track.

### Common depot problems

- Fast trains slow down entering and exiting a depot, which slows the trains behind them. On a crowded network this causes jams.
- Sharp corners near a depot slow trains down.
- Under heavy traffic, trains **accumulate** inside depots. If a depot sits at the end of a station and holds a train, a new train arriving on the same line can block the first from leaving. Several trains can end up trapped.

### Advanced depot configurations

- **Depots on both lines** lets trains accelerate in and out of a depot without slowing traffic on the main lines.
- **Forced service** puts the depot where trains must pass through it, usually right after delivering cargo or right before loading. This matters because income depends on the elapsed time between loading and delivery, so you want servicing to happen outside that window. It needs minimal space, slows a long train only once for both servicing and passing the station, and avoids sharp turns. The same trick turns a vehicle 180 degrees.
- **Overflow depot**: put a depot at the entrance of a Ro-Ro loading station so the only route to the platforms runs through it. Empty trains wait inside the depot instead of queuing on the approach. Put a path signal in front of the depot entrance.
- **Emergency overflow depot**: when a crash or a disaster blocks the line and trains start stacking up, build a temporary forced depot to absorb the incoming trains and keep the jam from spreading. When the blockage clears they leave on their own and continue. You may need to remove a signal or a piece of track to fit it. Stop the trains before modifying track or signals around them, or you will cause another crash.
- **Right-of-way depots** use pre-signals to make trains leaving a depot wait for main-line traffic, which matters because trains exiting a depot are much slower than trains already running. Understanding pre-signals helps here.
- If traffic is heavy, split the track into two before the depots so two trains can be serviced at once. Trains slow entering depots, so a queue otherwise builds up. This does not reduce the average speed on the main line.

## Building Signals

### Where signals cannot go

- Not on a tile containing a junction or a level crossing over a road.
- Not on bridges or inside tunnels.

### Constructing a signal

1. Click the **Build railway track** button on the menu bar to open the Railway Construction toolbar.
2. Click **Build railway signals** to open the Signal Selection toolbar.
3. Select a signal type and position the cursor over the track tile where you want it.
4. **Click once** to build. Unless you chose a path signal you get a **two-way** signal. Path signals always face one direction only.
5. **Click again** to convert it to a **one-way** signal. Only trains approaching from the direction it faces can pass.
6. **Click again** to flip it to face the other way.
7. **Click again** to return it to two-way.

### Building a line of signals

- With the **Build railway signals** tool active, click and drag along the track to place many signals of the same type at once.
- Starting the drag from an existing signal makes the whole line face the same way as that signal.
- Hold **Ctrl** and drag one or more tiles and signals are built automatically in that direction until a station, another signal, or a fork in the track is reached.
- Spacing comes from the **Dragging signal density** button on the Signal Selection toolbar. The default places a signal every 4 tiles. Use the left and right arrows to change it.
- Dragging from an entry, exit or combo signal builds block signals facing the same direction.

### Removing signals

- Click the **Bulldozer** button on the Railway Construction toolbar. The white square turns red.
- Click individual signals to remove them, or click and drag to clear a line of them.
- Click the Bulldozer button again to deselect. Shortcut **R**.
- Line removal also uses the **Dragging signal density** value.

### Converting signals

- Click **Signal Convert** on the Signal Selection toolbar, then click an existing signal to convert it to the currently selected type. Click the button again to go back to building.
- With signal conversion **off**, holding Ctrl and clicking a signal cycles it through the available signal types.
- With signal conversion **on**, holding Ctrl and clicking changes the signal style between semaphores and modern signals. This costs money.

### Which signal type to use

Unless you are building something genuinely exotic, **standard path signals are all you need**.

- Assuming every track is used in one direction only, place a one-way path signal anywhere a train could safely stop, facing the direction trains come from.
- Factor in the length of your longest train.
- Avoid placing signals where a long train would block a junction.

Block signals have their uses in more advanced constructions, but you can build a large, working network without ever touching them.

## Buying and Modifying Trains

Trains are bought inside train depots, and they start from the depot you built them in.

### Buying

1. Click the depot to open the Train Depot window. It lists every train currently inside.
2. Click **New Vehicle**.
3. The window shows every engine and cargo wagon available to you, with a description of the selected one. Pick an engine and click **Build Vehicle**.
4. A train window opens showing where your train is. This is also where you give it orders later. If you close it, reopen it by clicking the train in the depot.
5. Now choose wagons the same way and click **Build Vehicle** once per wagon. If there is only one train in the depot, wagons attach to it automatically.
6. Different wagon types can be mixed on one train, for example five grain hoppers and three livestock vans.

### Train length

- Every engine and wagon takes up **half a tile**, so an eight-piece train, one engine plus seven wagons, occupies four tiles.
- Engines built from two parts count as two pieces, not one.
- A train too long for its station takes **much** longer to load and unload. Build stations to fit your trains.
- NewGRF vehicles can be longer or shorter than half a tile. In that case the train building window shows the train length in tiles to the right of the train.

### Multiple engines

You can put more than one engine on a train: build the train with one engine, then build a second engine and drag and drop it onto the existing train.

This matters most with **Realistic acceleration** turned on, because extra power means faster acceleration and better hill climbing. The difference is most obvious on trains of ten wagons or more, which might otherwise never reach top speed.

### Selling trains

- To sell **one piece** or the engine alone, click and drag that piece to the **topmost** icon in the Train Depot window.
- To sell a piece **and everything to the right of it**, drag it to the **second** icon from the top. Alternatively hold Ctrl while dragging to the topmost icon.
- To delete an **entire train**, drag the engine to the second icon.
- To sell **every train in the depot**, click the **third** icon from the top. You will be asked to confirm.

### Rearranging wagons and engines

Drag pieces to move them.

- Wagons can move from one position in a train to another, or from one train to another.
- Engines can move to another train to act as an additional engine, or from a multi-engine train onto an empty depot slot to become a separate train.
- Hold **Ctrl** while dragging a wagon to move it **and every wagon to its right**. Ctrl-dragging the first wagon behind the engine transfers the whole rake to another train.

## Converting Rail Types

To pick the rail type to convert to, click and hold the railway build button on the main menu. Depending on your choice you get the normal, electrified, monorail or maglev construction toolbar.

Click the **convert rail** button, then drag to select an area to convert. The tool works on track, depots, bridges, tunnels, stations and waypoints.

### Rules and limits

- To convert bridges and tunnels, select at least one end.
- To convert a station, convert every tile of the platform. A single station can mix rail types, controlled by the **Nonuniform stations** setting.
- **Normal to electrified** rail can be converted with trains still running on the line. No emptying needed.
- For any other conversion, clear the line first. Send trains to the depot, and possibly sell them.
- You can only convert to rail types that are currently available to you.
- A tile can hold only one type of track, with the normal and electrified pair as the exception. To mix types on diagonal lines you may need to rebuild, leaving separate tiles for each type.

### Conversion tips

- When converting to electrified track, **convert your depots too**. Otherwise you cannot buy new electric engines or upgrade existing ones.
- To electrify a whole network at once, zoom out until you can see all of it, open the Electrified Railway Construction toolbar, click Convert, and drag a box over everything. Track, stations, depots and bridges all upgrade.
- **Warning:** after you close and reload a save, the rail tool defaults back to standard track. Switch to electrified rail again before laying new track.
- Steam and diesel trains run fine on electrified rails, so you do not have to replace trains immediately. Electric trains cannot run on non-electrified tiles.
- Autoreplace between rail types only works for standard and electrified trains. You cannot automatically replace anything with monorail or maglev.
- To move a train with a long order list to monorail or maglev, send it to a depot of the old type and sell it. **Keeping the depot window open**, convert the depot to the new rail type. The next train built there inherits the old train orders. One train at a time, and only while the window stays open. Convert the depot back to do the next one.
- To clear a line for conversion, give every train on it a **go to depot** order, or use the vehicle list to send all trains, or a group of them, to the nearest depot.

---

## Part 4: Roads and Road Vehicles

Roads are cheap, forgiving and need no signalling. This part covers laying road, placing stops, road depots, and buying and selling road vehicles.

## Building Roads

Click the **Road construction** button on the menu bar to open the road construction toolbar. There are two ways to lay road: the two directional road buttons, or the Autoroad tool.

### Using the directional buttons

1. Click one of the directional road building buttons.
2. Move the cursor to the tile where the road starts.
3. Drag to where it should end and release.

This works with **half-tile precision**. Click in the right half of a tile and drag right, and the road covers only half of that first tile. The same applies at the end tile.

### Using Autoroad

1. Click the **Autoroad** button. The cursor changes.
2. Place roads along the straight edges of tiles: put the cursor on a tile and click and drag.
3. Move the mouse in different directions before releasing to preview how the road will run.
4. Release to build.
5. You **cannot** place diagonal roads.
6. Autoroad works on hilly terrain too.

### Removing roads

- Hold **Ctrl** and click and drag along existing road, just as if building. Release and it is removed.
- Or select the **Remove** tool, shortcut **R**. White squares turn red. Click and drag along the road. Click the button again to deselect.
- Dynamite also works.
- Unlike track, you **lose** money when removing road.

## Bus Stops and Loading Bays

Road vehicles are best at moving passengers from town to town, or from one side of a town to the other. Once you have the hang of simple routes you can use them for cargo too.

### Choosing a bus stop location

Right-click and drag to move around the map and look for a town of **500 inhabitants or more**.

1. Click the **Road construction** button to open the toolbar.
2. Click **Build Bus Station**. The Bus Station Orientation window appears with four dead-end orientations plus two options for building a stop on an existing road.
3. Look for a free tile next to a road, near some houses.
4. Click the orientation that puts the station entrance facing the road.
5. Left-click the tile to build. A red number shows the cost, and the road extends into your station if the orientation is right. Slopes work as well as flat ground.
6. Repeat for a second stop elsewhere in town.

## Road Depots

Road depots are where road vehicles are built and serviced. Make sure your vehicles can reach the road network from the depot.

1. Click the road build button on the menu bar to open the road construction toolbar.
2. Click **build road vehicle depot**, or press **5**. The Road Depot Orientation window opens.
3. Select the direction the depot faces. This is how vehicles enter and leave.
4. Place the depot next to a road with the exit facing the road. Slopes are allowed.
5. Click to place it. If there is road adjacent, a connecting section is added automatically.

Dynamite removes a depot.

## Buying Road Vehicles

1. Place a depot, then click it.
2. The Road Vehicle Depot window opens. Click **New Vehicles** to list everything available.
3. Select one and click **Buy Vehicle** at the bottom.
4. The vehicle appears in the depot window and its own vehicle window opens.
5. Give it orders, and refit it if needed.
6. Click the red **Stopped** button to send it on its way.

### Giving orders to a road vehicle

1. In the Road Vehicle window, click the **Orders** button.
2. Click **Go To** and click the first station the vehicle should visit. This adds **Go to (station name)**.
3. Click **Go To** again and add the second station.
4. At the end of the list the vehicle starts over from the beginning.
5. Click the red **Stopped** button to start it.

### Selling road vehicles

A vehicle must be inside a depot to be sold, so send it there first.

1. Click the vehicle to open its Road Vehicle window.
2. Click **Send vehicle to depot** on the right of the window. It heads for the nearest depot.
3. Wait for it to arrive.
4. Click the depot to open the Road Vehicle Depot window and find the vehicle.
5. Drag the vehicle onto the sell icon, or click **Sell all vehicles** to sell everything in the depot. You will be asked to confirm the bulk sale.

---

## Part 5: Airports and Aircraft

Airports are where aircraft take off, land, load, unload and get serviced. They are expensive, but easy, because nothing has to be built between them. Once you have a few air services running, aircraft can be quite profitable.

### Building an airport in detail

1. Click **Build Airports** on the main toolbar to open the Airport Construction toolbar.
2. Click **Build Airport** to open the Airport Selection window.
3. Choose the airport type. Early on only the **Small Airport** is available.
4. Turn on **Coverage area highlight**.
5. Move the cursor over the map. White squares are the airport footprint; purple squares are the industry tiles and houses that will use it.
6. For an **industrial** airport, just check the **Accepts** and **Supplies** lines at the bottom of the Airport Selection window and make sure your cargo is listed.
7. For a **passenger** airport, pick the spot that covers the most houses. Houses outside the purple squares will not use your airport.
8. Left-click to build. You may have to terraform a little first.
9. Repeat for more airports. You need at least two before you can run a service.

### Buying an aircraft

1. Click the hangar inside the airport you want the aircraft based at. The Aircraft Hangar window opens.
2. Click **New Aircraft** at the lower left.
3. Select an aircraft and press **Build Aircraft**. By default it carries maximum passengers plus some mail.

Then give it orders and start it, exactly like any other vehicle.

Note one quirk for aircraft: **Full load any cargo** means "wait for passengers". This is inconsistent with other vehicle types but is usually the behaviour you want.

---

## Part 6: Water Transport

A classic ship route is hauling **Oil** from an **Oil Rig** to an **Oil Refinery**. Once you have the pattern, ships work for other cargo too.

## Docks

### Choosing a dock location

Find an oil rig and an oil refinery you want to trade between. **Oil rigs have a built-in dock**, so the only dock you need to build is at the refinery. Refineries are only found near the coast.

### Building a dock

1. Click the waterways button to open the **Waterways construction** toolbar.
2. Click **Build ship dock**. The Dock window appears.
3. Move the cursor along the water edge. A dock must sit on a **sloped tile connected to a water tile**.
4. Check that **Oil** appears next to **Accepts** in the Dock window before you build. Turn on Coverage area highlight and make sure the coverage reaches the refinery.
5. When the cursor shows two white squares **and** your cargo is accepted, click to place the dock. You may need to terraform first.

## Ship Depots

Ship depots are where ships are bought, serviced and sold.

- A ship depot must be placed on **water tiles**, and ships must be able to reach it from **both sides**.
- A depot is two tiles long, and ships enter and leave at the narrow ends.
- Ships need to visit a depot regularly for servicing, so put it near the route. Next to the dock is a good choice.

1. Click the waterways button to open the **Waterways Construction** toolbar.
2. Click **Build ship depot**. The Ship Depot Orientation window opens.
3. Select an orientation.
4. Two white squares show the future location. Move the cursor where you want it and click. Keep both the entrance and the exit clear.

## Buoys

Buoys are waypoints for ships. There are two reasons to use them.

- The ship pathfinder may not find a route between two distant docks at all.
- Guiding ships between nearby points reduces CPU load, because there are fewer possible routes to evaluate.

### Placing buoys

- Place a buoy roughly every **20 tiles** along the route the ship should take. Use a few more around complex bends.
- Do not overdo it. Every buoy has to be added to the ship orders by hand.

1. Open the **Waterways construction** toolbar.
2. Click **Place buoy**.
3. A white square shows where the buoy will go. Move the cursor to a **water tile** and click.
4. Repeat along the route.

## Buying and Running Ships

1. Click your ship depot to open the Ship Depot window.
2. Click **New Ships** at the bottom left.
3. Browse the catalogue. Click a ship in the upper half of the window to see speed, cargo capacity and other statistics.
4. With the right ship selected, click **Build Ship** at the bottom left.
5. A vehicle window appears. Close the Build Ship and Ship Depot windows with the x in the upper left if you are done buying.

### Ship orders, including the buoys

Every buoy on the route has to be in the order list, in sequence, out and back. A full oil run looks like this.

1. Click **Orders** in the vehicle window.
2. Click **Go To** and click your **first buoy**. This adds **Go to via (buoy name)**.
3. Click **Go To** and add the **second buoy**.
4. Click **Go To** and add the **oil rig**.
5. Click **Go To** and add the **second buoy** again.
6. Click **Go To** and add the **first buoy** again.
7. Click **Go To** and add your **dock**.
8. Click **Go To** and add your **ship depot**.
9. Select the oil rig line in the order list and click **Full Load**, so the ship waits until it is full of oil.
10. Select the dock line and click **Unload all**.
11. Select the ship depot line and click **Service**.
12. Click **Stopped** at the bottom of the ship window to start it.

At the end of the list the ship loops back to the beginning.

### Refitting and selling ships

Some ships are **refittable**, meaning you can change the cargo they carry. A cargo ship that carries Goods by default can often be refitted to something else. See the Refit section in Part 8.

Selling works like road vehicles: the ship must be stopped inside a depot.

1. Click the ship to open its vehicle window.
2. Click **Send ship to depot**. You can close the vehicle window while it travels.
3. When it arrives, click the depot to open the Ship Depot window and find the ship.
4. Drag the ship onto the sell icon, or click **Sell all ships** to sell everything stopped in the depot. Bulk sales ask for confirmation.

## Canals, Locks and Aqueducts

Boats can travel inland on rivers and canals. **Rivers** are created during world generation; **canals** you build yourself, on any flat land tile.

Canals, locks and aqueducts are expensive, but they are how you connect separate bodies of water and reach inland industries.

### Things to know before you dig

- To turn around, a boat needs a **2 by 2 area of water**, or a dead-end canal. If you put docks alongside a single-width canal, boats cannot turn until they reach the end of it.
- Rivers run downhill, but ships cannot climb their slopes. **Locks** are how ships change elevation, on rivers and canals alike.
- **Aqueducts** are bridges for ships.

### Building a canal

1. Open the **Waterways construction** toolbar.
2. Click **Build canal**.
3. Place the cursor on any flat land tile and left-click. Click and drag for longer stretches.

If you need a dock partway along, build a large, expensive open area for ships to manoeuvre in and put the dock there.

### Building locks

1. Open the **Waterways construction** toolbar.
2. Click **Build lock**.
3. Find a spot with **two full flat tiles connected by a single slope**.
4. Click on the slope to build the lock.
5. Repeat for further locks as the elevation changes.

### Building aqueducts

1. Open the **Waterways construction** toolbar.
2. Click **Build aqueduct**.
3. Put the mouse where the aqueduct should start. White squares show where it will be built. Unlike rail and road bridges you do **not** click and drag to the far end.
4. Left-click to build.

---

## Part 7: Terrain, Bridges and Tunnels

The tools for getting past ground you cannot build on: bridging over it, tunnelling under it, or reshaping it.

## Bridges

Bridges get you over valleys, rivers, competitor track and even your own lines. Many advanced junctions and station designs depend on them to keep opposing flows from crossing.

### Building a bridge

1. Open the Railway construction toolbar from the menu bar.
2. Select the **Bridge** building tool.
3. Find where the bridge should go.
4. Place the mouse at the **starting point**. It does not matter whether track already runs up to it. For a river crossing this is the sloped tile next to the water.
5. Click and drag to the **ending point**, the sloped tile on the far side, and release. A window pops up.
6. Choose a bridge type. **The more expensive the bridge, the faster trains can cross it.** Scroll for more types.
7. Click your choice and the bridge is built.

### What bridges can and cannot span

- Bridges over deeper valleys work as long as the bridge starts and ends **at the same height** on sloped tiles.
- You can generally build over sloped land as long as it slopes **towards the direction of the bridge**.
- If the land under the bridge slopes some other way, you cannot place it. Either landscape the valley or run the track through it instead.
- Start and end points may differ in height by **no more than one level**, which is occasionally very useful.
- Bridges are the clean way to cross a competitor track or road.

### Road bridges

Road bridges work identically. Open the Road Construction Toolbar and select the Road Bridge tool, then place it the same way. They come in the same variety of types and lengths.

A road bridge over a railway is safer than a level crossing, where a fast train may crash into your truck or bus. The train is undamaged; you have to buy a new road vehicle. The tradeoff is that the vehicle slows climbing the bridge, though it speeds up again coming down.

Bridges for boats are **aqueducts** and are built differently. See Part 6.

## Tunnels

Tunnels go under things you cannot move or cannot afford to remove, such as large mountains. You cannot bridge over cities, stations or industries, but you **can** tunnel under them.

Tunnels are also useful in junctions, because vehicles pass through them without slowing down, unlike some bridges.

### Building a tunnel

You can dig tunnels for road and for rail. You cannot switch between road and rail in an existing tunnel without rebuilding it, though you can change between rail types.

- Move the cursor around the map to find a spot. **You cannot dig a tunnel on flat land, only into a hillside.**
- Move the cursor over a slope and the path of the tunnel is highlighted in white.
- Click the sloped tile to build.

### Awkward tunnel ends

- If the land at the far end slopes the wrong way, the game **automatically lowers** it so the tunnel can be dug.
- You cannot **start** digging at such a slope. Terraform the entrance first.
- Sometimes automatic lowering is impossible because of obstacles on surrounding tiles, and you get an error window. Raise the land manually so the tunnel end tile is a flat slope, then build.

### Tunnel limitations

- Tunnels cannot cross each other underground, and you will be warned if you try. You also cannot excavate from above where a tunnel runs below.
- **You cannot place signals inside a tunnel**, so a tunnel holds only one train at a time. Very long tunnels can throttle a busy network.
- Every tunnel and bridge piece costs the maintenance of **4** regular track pieces, making them expensive to keep for the same distance.
- Air drag in a rail tunnel is twice what it is outside.

## Landscaping

Landscaping means terraforming: raising, lowering and levelling land. Press the landscape button on the menu bar to open the landscaping toolbar.

### The toolbar buttons

From left to right, with their shortcuts:

- Raise land - **Q**
- Lower land - **W**
- Level land - **E**
- Clear land - **D**
- Buy land - **U**. Sets land aside so towns cannot develop on it and rivals cannot use it.
- Plant trees - **I**. Opens the tree planting toolbar.
- Place signs - **O**

### Raising land

Select the raise tool and click a **corner** of a tile.

- Raising the top of a mountain also grows its base. You pay for the **volume** of change, not the height.
- **Avoid raising land out of the sea.** It is extremely expensive and can bankrupt a young company.
- You can also click and drag: the starting tile is raised by one, then the selected area is levelled to match that edge. It is a combined raise and level.
- Hold **Ctrl** to rotate the selected area by 45 degrees.

### Lowering land

Select the lower tool and click a corner of a tile.

- Land can be lowered to sea level, but **tiles at sea level are prone to flooding** and will be washed away.
- Click and drag works the same combined way as raising, and Ctrl rotates the selection by 45 degrees.

### Levelling land

Use the level tool to flatten a large area.

1. Click and hold where you want to start. The finished height will match the tile you started on.
2. Drag over the area to level. Hold **Ctrl** to rotate the selection by 45 degrees.
3. Release and the area is levelled.

Two things to know: the level tool changes as much land as it can inside your selection, and any tile that the individual raise or lower tools could not change will not change either. Infrastructure, buildings and obstacles inside the area stay standing.

### Autoslope

**Autoslope** is an advanced setting under Construction. It relaxes terraforming restrictions considerably and lets you terraform **under** objects that would otherwise have to be removed first, adding and removing foundations automatically.

Some objects never allow foundations to be added or changed regardless of the setting: canals, certain NewGRF industries and town buildings, and competitor-owned land.

---

## Part 8: Orders and Fleet Management

Building the network is half the game. This part is the other half: telling vehicles what to do, changing what they carry, upgrading them en masse, and organising them once you have too many to track individually.

## Orders

Orders are fundamental. Without them your vehicles wander and you make no money. An order list is simply instructions of the form "go here, pick up cargo, take it there".

### Giving orders

1. Click the vehicle. It may be sitting in a depot or already moving. For a train, clicking any carriage works. The vehicle window opens.
2. Click the **Orders** button. The Orders window shows the current order list.
3. Click **Go To**, then click the target station on the map.
4. Click the order you just created to select it, then click what the vehicle should do there, for example **Full Load**.

The vehicle current destination is shown in its status bar and in the Orders window, where a black triangle points at the active order.

### Go To

**Go To** inserts a new order **before** the highlighted order, or appends it to the end if nothing is selected. Valid targets:

- Your own stations, but only ones that accept this vehicle type. You cannot send a bus to an airport with no bus station, and you can never send a vehicle to a competitor station.
- **Depots**, which changes some of the other buttons to Service and Refit.
- **Vehicles of the same type**, to copy orders or share orders.
- **Waypoints**, to influence which track a train takes, or to keep a vehicle from getting lost when stations are far apart. A **buoy** is the waypoint equivalent for ships on long routes.

The Go To button itself has options: plain **Go to**, **Go to nearest depot**, and **Conditional order jump**, which can skip stations when a condition is met, such as the train already being full.

### Delete and Skip

- **Delete** removes the highlighted order, which cancels that vehicle service to that station. If the **End of Orders** line is highlighted instead, Delete wipes the entire list. On a shared list the line reads **End of Shared Orders** and behaves differently.
- **Skip** abandons the order being fulfilled and moves to the next one. Pressing Skip on the last order sends the vehicle back to the first.

### Station instructions

Select an order first, which enables the instruction buttons, then click the instruction. Road vehicles, boats and planes get Full Load, Unload and Transfer. Trains also get **Non Stop**.

For a **go to station** order you can change stopping behaviour, loading behaviour, and unloading behaviour. For a **go to depot** order those become **Refit** and **Service**.

### Loading options

- **Load if available** takes whatever is there and leaves. This is the default, and it is usually the wrong choice, because you want vehicles leaving full to cut down travel time per unit. The exception is passengers and mail.
- **Full load all cargo** waits until the vehicle is completely full. Ctrl-clicking a station when adding the order sets this automatically.
- **Full load any cargo** leaves once it is full of any one of the cargoes it can carry. For **aircraft** this means "wait for passengers", which is inconsistent but usually what you want.
- **No loading** passes through without picking anything up.

### Unloading options

- **Unload if accepted** drops everything the station accepts and moves on. This is the default.
- **Unload all** dumps everything, accepted or not. You are paid for accepted cargo as usual. Cargo the station does not accept is still unloaded and left for another vehicle, showing as **En route from (source)** in the waiting list, and you are **not** paid for it.
- **Transfer** unloads regardless of acceptance like Unload all, but you receive **part payment** for the distance covered so far. This is how you run a feeder service without the feeder vehicles showing a loss.
- **No unloading** passes through without dropping anything.

None of the unloading options stop the vehicle from picking up new cargo. Set the loading behaviour separately if you need that.

One trap with **Transfer**: by default the vehicle also collects waiting cargo, and the order reads **Transfer and take cargo**. That can include the cargo it just dropped off. Set the loading option to **No loading** and the order becomes **Transfer and Leave Empty**.

### Stopping options

- **Go to** and **Go non-stop to**
- **Go via** and **Go non-stop via**

**Non-stop** stops a vehicle calling at stations it passes on the way to the destination. **Go via** uses a station as a waypoint, and every station can also be set non-stop.

### Service and Refit orders

**Service** is available when a **go to depot** order is selected. **Refit** replaces the loading behaviour on a depot order and prompts you for the cargo type to refit to. Refit orders are of limited use, since normally you refit a vehicle once and leave it, and you pay the refit cost every time it triggers.

### Timetables

Timetables let you specify how long a vehicle should take on each leg, how long to spend in each station, and speed limits between orders.

### Copying orders

Setting up five buses on the same five-station loop by hand is tedious. Copy the list instead.

1. Give the first vehicle its orders normally.
2. Click the next vehicle, open its order window, and press **Go To**.
3. Instead of clicking a destination, **click the first vehicle**, wherever it is - in a depot, or out on the road.
4. The second vehicle now has the same orders.

You can only copy orders onto a vehicle that has **no** orders yet. That guard exists so you cannot accidentally click a working vehicle in a busy station and overwrite its list.

Copying still means editing every vehicle individually later. Sharing is better.

### Shared orders

Shared orders let many vehicles use **one** order list. Update it on any of them and every vehicle sharing it changes.

1. Open the order list of the vehicle that should join the share and click **Go To**.
2. Hold **Ctrl** and click a vehicle that already has the orders you want.
3. The two are now linked. The last line reads **End of Shared Orders**.

There is no limit on how many vehicles share a list, but they must all be the same vehicle type, since they use the same stations.

To stop sharing:

1. Open the order list of the vehicle you want to remove.
2. Select the last line, **End of Shared Orders**.
3. Click **Stop sharing**.

That vehicle keeps a private copy and every other vehicle in the share is unaffected.

The **Shared Orders** button to the right of the Orders window, also on the Timetable window, lists every vehicle sharing the current list. It is only enabled when the vehicle is actually sharing.

### Shared orders notes

- Unlike copying, sharing works on a vehicle that already has orders, because holding Ctrl makes accidental loss unlikely. The vehicle loses its own orders and takes the shared ones.
- **Clone vehicle** in the depot window and **buy a copy** in the vehicle window both copy orders by default. Hold **Ctrl** while clicking the vehicle to clone and you get shared orders instead.
- There is no master copy that you could delete by mistake. As long as one vehicle with those orders exists, the list survives.

### Order problems the game warns you about

The order review system runs in the background and raises a news message for four common mistakes.

- **Too few orders.** A vehicle needs at least two stations to make a profit. Depots and waypoints do not count, because you cannot pick up or drop off there.
- **Duplicated order.** The same station selected twice in a row. This confuses the pathfinder badly, for instance an aircraft that takes off and immediately lands at the same airport.
- **Invalid orders.** Delete a station and its ghost remains for a while as a grey name label. Build a new station of the right type in the same place and it takes the old name, and vehicles resume calling there with no order changes. Leave it too long and the ghost disappears, and every order referring to it becomes **Invalid Order** and is skipped. Removing a **depot** leaves no ghost at all, so orders referring to it become invalid immediately.
- **Invalid station.** Delete part of a station, such as the bus stop attached to a train station, and the order stays valid because the station still exists, but the vehicle can never reach it. The same happens with a bus routed to a train-only station, an articulated vehicle sent to a station without drive-through stops, or a train sent to a station with an incompatible rail type such as railway on maglev. The vehicle searches for the station forever.

## Refit

Refitting changes the cargo a vehicle can carry. Some train engines, cargo ships and planes are refittable; you have to buy a refittable vehicle in the first place.

To refit, the vehicle must be **stopped inside a depot**.

1. In the vehicle window, click the **third** button down, the pair of boxes.
2. The refit options for that vehicle appear.
3. Click the new cargo type.
4. The bottom of the window shows the cost and the resulting capacity.
5. Click **refit vehicle**.
6. The cost is deducted and the vehicle is ready for its new cargo.

You can also refit via a **go to depot** order carrying the Refit instruction: run out with coal, refit to iron ore, run back. You pay the refit cost every single time it triggers, so this only makes sense on long routes.

## Replacing Vehicles

### Manual replace

You can replace one vehicle without losing its order list:

1. Send the vehicle to a depot.
2. Sell it. For a train, sell the engine only.
3. The **first** new engine or vehicle built there inherits the order list of the one you just sold. Build the replacement.

### Autoreplace

Autoreplace upgrades a whole fleet of one vehicle type to another without touching them individually. Forty buses and a better bus model just arrived is exactly the case it exists for. Engines can be replaced with other engines, and wagons with other wagons, which matters most with NewGRF sets that introduce faster wagons over time.

If you want to replace old vehicles with the **same** model, use the vehicle autorenew settings instead.

1. Open the vehicle listing for the type you want to replace.
2. From the **Manage list** menu, click **Replace vehicles**.
3. The left pane shows what you use now; the right pane shows what you could upgrade to. Click one on each side to define the replacement.
4. For trains, choose the rail type from the menu at the bottom centre, and toggle the **Replacing: Engines** button to switch between engines and wagons.
5. Click **Start Replacing Vehicles**.
6. When every vehicle of that type has been replaced, the old type turns grey in the list. Click it and click **Stop Replacing Vehicles** to finish, and it disappears from the list.

You cannot autoreplace across incompatible train types, because the train would have to enter a depot of one type and leave as another. The exception is normal to electric trains, if you have electrified rails, since both run on electrified track and can be built from electrified depots.

### Wagon removal

The **Wagon removal on/off** button sits in the bottom-right of the replace window. With it on, replacing a 1-unit engine with a 2-unit engine sells the first carriage to keep the train the same overall length.

It only works in that direction. Replacing a two-part engine with a single-part one shortens the train, and the game does not pad it back out, because it cannot know which carriage you would want added.

### When replacement actually happens

Starting a replacement does not send anything anywhere. Each vehicle is replaced the next time it **arrives at a depot for maintenance**.

To upgrade everything immediately, use **Send for Maintenance** on the vehicle manager window for the group you are upgrading, or a sub-group of it, or click **Send to Depot** on individual vehicles.

That matters especially if you play with **Vehicle breakdowns** set to None and **Disable servicing when breakdowns set to none** enabled, because then trains are never serviced automatically and would otherwise never be replaced.

### What autoreplace will offer you

The candidate list is filtered to vehicles that can be refitted to the correct cargo, which mostly affects ships, road vehicles and aircraft, and that use the same infrastructure: ships on water, maglev on maglev track, helicopters on helipads and so on.

There is also a money rule. The company needs more money than the autoreplace money limit plus **twice** the price of the new vehicles. The sell price of the old vehicles is not counted. That limit is the same one as the autorenew minimum needed money in Advanced Settings.

## Vehicle Groups

Groups organise a fleet. A vehicle can be in **only one group at a time**, and only with vehicles of its own type: trains, road, air or sea.

The group interface lives in the vehicle list, and needs the **Use the advanced vehicle list** setting. It defaults to Own company, so you see groups for your own vehicles but not for opponents.

### Creating a group

1. Click the **create group** button.
2. Click the new unnamed **Group 0** to select it. The count next to the name shows zero vehicles.
3. Click **rename group** and type a name. Naming it after the route the vehicles share works well.

### Filling a group

- Drag a vehicle onto the group to add it.
- Drag a vehicle onto **ungrouped vehicles** to remove it from its group.
- Use **remove all vehicles** from the Manage list menu to empty a group while keeping its name.
- The fast way: add one vehicle, then use **add shared vehicles** from the Manage list menu. Every vehicle with the same shared orders joins the group at once.

### What groups are for

A group gives the vehicle list a context, much like shared orders, except a group can hold vehicles running different routes. You might later split those buses so some use full load orders while still managing them as one group. From the Manage list menu you can then:

- **Replace vehicles** to upgrade the whole group to a new model.
- Send them all for a service, or into the depot for manual changes.

Groups also **protect** vehicles from automatic upgrades. If you have set replacement rules for All vehicles, click the **no autoreplace** button under the group list and it shows a small gold shield. Use it to keep a decorative steam train exactly as it is while everything else upgrades to diesels.

Since version 1.9 you can also give a group its own **livery**. Your company colour might be red while freight trains run blue, which makes routes and services much easier to tell apart at a glance.

---

## Part 9: Options, AI Opponents and Sandbox Tools

Settings that live outside the world generation screen: the Game Options window for interface, graphics and sound, the AI configuration for competitors, and the sandbox options for when you want to bend the rules.

## The Game Options Window

The Game Options window holds the basic options: interface, base graphics, sound, and social integration plugins.

It deliberately does **not** contain gameplay settings, user-created content, AIs or Game Scripts. Those live in their own menus.

### Language

The interface language. The official translation website lists every supported language along with how many of its translations are missing or outdated.

### Autosave

How often the game saves itself, in **real-life minutes**, in case of a crash or if you want to roll back.

- The options are Off, every 10, 30, 60 or 120 minutes.
- Autosaves land in the `save\autosave\` directory.
- Leave this on. There is no good reason to disable it.

### Currency units

The main currency for the game. Pounds Sterling is the base currency the game works in internally.

Selecting **Custom** lets you build your own currency and set:

- The exchange rate against GBP
- The decimal separator
- The prefix and the suffix
- The year your currency automatically switches to the Euro, if ever

### Automated survey

When enabled, an automated survey is sent when you leave a game. This is **opt-in**, and the game asks you once on first launch.

- **Preview survey result** shows exactly what would be sent.
- **About survey and privacy** opens the details page.
- The survey records no personal information and no data that could be used to track a specific user. Published summaries of the results are available online.

### Interface size

Scales the interface by a factor between 1 and 5.

- The slider snaps to tick marks every 0.25 units, so 1x, 1.25x, 1.5x and so on.
- Hold **Ctrl** to move the slider continuously to any value in between.
- At a non-integer scale the default font can look rough around the edges. Fix it by enabling **anti-alias fonts**, or by switching to the **traditional sprite font**, which does not have the problem.

### Font and scaling options

- **Auto-detect size** picks an interface size appropriate for your monitor. Changing the size by hand disables it.
- **Scale bevels** scales the bevelled edges of buttons along with the interface slider.
- **Use traditional sprite font** swaps the new font for the traditional fixed-size one.
- **Anti-alias fonts** softens jagged edges on the font. It can only be enabled when the traditional sprite font is **disabled**.

### Screen and performance

- **Screen resolution** sets the resolution in fullscreen, or the window size in windowed mode.
- **Display refresh rate** should match your monitor. Changing it does not affect frames per second, and setting it above your monitor rate does nothing.
- **Fullscreen** is true exclusive fullscreen. Borderless or windowed-fullscreen mode is **not** currently supported by OpenTTD.
- **Hardware acceleration** only takes effect after a game restart.
- **VSync** also only takes effect after a restart, and can only be enabled when hardware acceleration is on.

### Base graphics set

Picks which base graphics to use when you have more than one source installed, such as the DOS or Windows original files, or OpenGFX.

### Sound and music

- **Volume** sets the level for sound effects, such as vehicle and level crossing noises, and for music.
- **Base sounds set** picks between installed sound sources, such as the original set or OpenSFX.
- **Base music set** picks between music sources such as TTD, OpenMSX or the Scott Joplin Anthology. Unlike the other base sets, **the music set can be changed while in a game**.

### Social integration plugins

OpenTTD can integrate with social platforms through a plugin per platform. Plugins currently exist for **Discord**, **Steam** and **GOG Galaxy**.

- Installing through Steam or GOG comes with some plugins already in place. Downloading the game from the OpenTTD website installs none.
- The **Social** tab of the Game Options menu shows which plugins are installed.

To install one manually:

- On **Windows and Linux**, extract the downloaded archive into the `social_integration` folder inside your OpenTTD data directory. On Windows that is generally `Documents\OpenTTD`; on Linux the location varies.
- On **macOS**, run the Install script included in the download.

After installing, check the status in the Social tab. **Green** means the plugin is working, **yellow** means it works but the program it integrates with is not running, and **red** means something is wrong with the plugin or that program.

## AI Opponents

OpenTTD ships with the NoAI framework, which lets people write their own AI opponents. You manage them in the **AI Configuration** window, reached from the **AI Settings** button on the main menu.

**No AIs are included with the game**, so nothing will happen until you download some.

### Downloading AIs

1. Open the AI Configuration window.
2. Click **Check Online Content**.
3. Download the AIs you want.

The online content system automatically selects the AI libraries each AI depends on. If instead you download an AI from the forums or elsewhere, you have to make sure you also get the right versions of the libraries it uses.

### Selecting AIs

1. Click **AI settings** in the main menu.
2. Set the number of AI competitors you want in the game.
3. Click one of the company slots, then click **Select AI**.
4. Pick an AI from the list of the ones you have downloaded, then click **Accept**.

### Configuring AIs

Click a company slot, then click **Configure**.

- Apart from the first setting, every option here is defined by that AI author and controls how the AI plays.
- You can run **multiple instances of the same AI with different settings**, which is a good way to get varied opponents from a small set of downloads.
- AIs start automatically after a given number of days, with some minor random variation.

### Managing AIs from the console

The in-game console can start and stop AIs directly:

- `list_ai` lists the currently installed AIs.
- `rescan_ai` rescans the AI folder. You need this if you install an AI while the game is already running.
- `start_ai <ainame> <parameters>` starts the next AI immediately. Naming an AI loads that one instead of the one set in the AI settings window, and the parameters do the same job as the Configure button. For example: `start_ai admiralai use_planes=0,use_trains=1`
- `reload_ai <company_slot>` deletes that company and restarts the AI. The **Reload AI** button in the AI Debug window does the same thing.
- `stop_ai <company_slot>` stops the AI in that slot and deletes the company.

## Sandbox Options

Sandbox options, historically called cheats, make the game easier. They work in single-player only.

### Opening the sandbox menu

- Press **Ctrl + Alt + C**.
- If another program on your machine already responds to that combination, try **Ctrl + Alt + Windows + C** instead.
- If your keyboard has no Windows key, you have to free up Ctrl + Alt + C by changing the other program settings, closing it, or editing `hotkeys.cfg`.
- On **macOS**, press **Control + Cmd + C**, or failing that **Ctrl + Alt + C**.

### Increase money by 10,000,000

Adds or subtracts 10,000,000 pounds, roughly 20,000,000 in dollar currencies. Press it as many times as you like. The decrease button will not take you below zero.

### Playing as company

Lets you take over any company, whether an AI or another human company from a loaded multiplayer save, and control their vehicles.

**Save your game first.** This option can trigger an assertion error and lose everything you have been working on. Valid company numbers are 1 to 15.

### Magic bulldozer

Lets you destroy industries and other normally immovable objects such as lighthouses and telephone poles. On or off.

### Tunnels may cross each other

Lets you build tunnels that intersect underground, which the game normally forbids. On or off.

### Jetplanes will not crash frequently on small airports

Stops large aircraft from constantly crashing at small airports. They still crash **occasionally**, at the same rate as crashes at any other airport. On or off.

### Enable modifying production values

Lets you change how much cargo an industry produces. On or off. The maximum production value is 2,040 tonnes.

### Fix station ratings at 100 percent

Pins station ratings at 100 percent, which stops a station losing cargo because of a poor rating. On or off.

### Edit the maximum map height

Changes the maximum map height for the current game, anywhere from 15 to 255.

You cannot set it lower than the height of the tallest mountain already on the map.

### Change date

Travel forward or backward in time. Click the date to type a year directly rather than stepping it with the arrows. The range is year 0 to 5,000,000.

Three caveats worth knowing before you use it:

- It does **not** affect inflation or expired vehicles. To get expired trains back, open the console and type `reset_engines`.
- Anything that becomes available while you are in the future, including vehicles and later airport types, **stays** available when you return to the original date.
- Travelling to before the year your game began breaks the financial information.

### Deprecated sandbox options

Three options that used to live here have moved or been removed:

- **Allow Electric Trains to run on normal track** moved to Advanced Settings under Vehicles, then Trains, as of 0.7.0. It disables electric rails altogether.
- **Build while in pause mode** moved to Advanced Settings under Limitations as of 1.1.0.
- **Switch climate** was removed in 1.2 and later. It was an unreliable hack that tended to break games badly and was not really useful.

### Sandbox options in multiplayer

The sandbox menu is not available in multiplayer. There are only two ways around that:

- Modify the source code and recompile the game running on the server, which is not remotely easy.
- Enable the options in a single-player save, then load that game from the **Start Server** menu.

### What using sandbox options costs you

- The game no longer marks each used option with a tickbox the way it once did.
- The save file itself **does** record whether any sandbox option was ever used, and a savegame analyser can read that.
- Using any sandbox option currently keeps your score out of the High Score list. That is a bug rather than a design decision, and will likely be fixed at some point.
