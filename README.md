## Timite
A fork of Purpur for my server.

This fork is based on Purpur with some patches from other forks and some open Pull Requests from Paper. In the future I might add some events and some new API stuff to assist in our server's plugin development.

The list of patches from this fork includes:
* Async Pathfinding (Petal)
* Multithreaded Tracker (Petal)
* Reduce Sensor Work (Petal)
* Improve Game Event System (Petal)
* Ignore Durability Change in Equipment Update (Slice)
* Don't send fire packet if player have Fire Resistence (Slice)
* Don't save fireworks in chunks (EmpireCraft)
* Persistent Wither (EmpireCraft)
* Fix piglin loved items (Paper PR)
* Fix a bunch of vanilla bugs (Paper PR)
* Set position before send player on dimension change (Paper PR)
* Add missing effect cause (Paper PR)
* Stop large look changes from crashing the server (Paper PR)

## Building
To build Timite, simply clone this repository and
* Run `./gradlew applyPatches` first.
* Then run `./gradlew build` to compile a full server jar or `./gradlew createReobfPaperclipJar` to compile a paperclip jar (for distribute).

Please note that if you are using **Windows** then the build process will be painfully slow, so because of that I recommend you build Timite on GNU/Linux or macOS instead.