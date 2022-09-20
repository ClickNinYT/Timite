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

Please note that if you are using **Windows** then the build process will be painfully slow, so because of that I recommend you build Timite on GNU/Linux or macOS instead. Windows is also not the best platform to develop Paper or any of its forks. But if you still insist on using Windows, make sure to use Windows 10 20H1 or newer.

## Applying Patches
And yeah, sometimes when you upstream or adding patches from another fork (if you don't know what you are doing, for example), you may run into issues like this when applying patches:
```
Applying: Rebrand
Patch failed at 0001 Rebrand
When you have resolved this problem, run "git am --continue".
If you prefer to skip this patch, run "git am --skip" instead.
To restore the original branch and stop patching, run "git am --abort".
error: invalid object 100644 b9c0d8d598aeac99e1fbc77063e5e2f280ca1693 for 'src/main/java/org/bukkit/craftbukkit/CraftServer.java'
error: Repository lacks necessary blobs to fall back on 3-way merge.
hint: Use 'git am --show-current-patch=diff' to see the failed patch
***   Please review above details and finish the apply then
***   save the changes with `./gradlew rebuildPatches`
```
(this is only an example btw)

In this case, other than resolving the conflict by yourself, you can ask `apatch` to help!

### apatch.sh
apatch is a script written by Aikar, it can (hopefully) automatically fix these conflicts for you.

To get started, you need to install `wiggle` using your package manager. This tool only available on GNU/Linux (rip Windows users, also Windows is not the best choice to develop Paper or any of its forks, as shown above in the Building section). Then:
* `cd` into either Timite-API (if API patches fail to apply) or Timite-Server (for server patches)
* run `../scripts/apatch.sh`

If it manage to fix the conflicts, it will show a bunch of `APPLIED CLEAN` (no failed apply), else it will show you the patch file and some failed apply, which in that case press `q` to exit and fix the conflict by yourself. In case it applies successfully, run `git add .` and `git am --continue`, then `cd ..`, rebuild patches with `./gradlew rebuildPatches` and continue with the Building section.