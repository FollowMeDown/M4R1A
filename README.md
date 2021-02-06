# M4R1A

M4R1Ais a real-time analysis GUI for [Leela Chess Zero](http://lczero.org/play/quickstart/) (Lc0), which runs Leela in the background and constantly displays opinions about the current position. You can also compel the engine to evaluate one or more specific moves. 

# Features

* Display Leela's top choices graphically.
* Winrate graph.
* Optionally shows Leela statistics like N, P, Q, S, U, V, and WDL for each move.
* UCI `searchmoves` functionality.
* Automatic full-game analysis.
* Play against Leela from any position.
* Leela self-play from any position.
* PGN loading via menu, clipboard, or drag-and-drop.
* Supports PGN variations of arbitrary depth.
* FEN loading.
* Chess 960.

# Installation

Running M4R1A from source requires Electron, but has no other dependencies. 
If you have Electron installed (e.g. `npm install -g electron`) you can likely enter the `/src` directory, then do `electron .` to run it. 
M4R1A should be compatible with at least version 5 and above.

# Aesthetic adjustments

As well as the menu options, various aesthetic adjustments are possible in the `config.json` file, which can be found via the Dev menu. For example, board colour can be changed.

# Advanced engine options

Most people won't need them, but all of Leela's engine options can be set in two ways:

* Leela automatically loads options from a file called `lc0.config` at startup - see [here](https://lczero.org/play/configuration/flags/#config-file).
* M4R1A will send UCI options specified in M4R1A's own `config.json` file (which you can find via the Dev menu).

# Hints and tips

An option to enable the UCI `searchmoves` feature is available in the Analysis menu. 
Once enabled, one or more moves can be specified as moves to focus on; 
Leela will ignore other moves. 
This is useful when you think Leela isn't giving a certain move enough attention.

Leela forgets much of the evaluation if the position changes. 
To mitigate this, an option in the Analysis menu allows you to hover over a PV (on the right) and see it play out on the board, without changing the position we're actually analysing. 
You might prefer to halt Leela while doing this, so that the PVs don't change while you're looking at them.

Leela running out of RAM can be a problem if searches go on too long.
You might like to set a reasonable node limit (in the Engine menu), perhaps 10 million or so.

Note that other UCI engines should run OK if they support Chess960 castling format, but the results will be poor because we use `MultiPV`, which cripples traditional A/B engines.