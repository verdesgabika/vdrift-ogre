### Release checklist ###
The process of releasing and things that need to be checked before.

#### 1. Code ####
  * Fix crashes and critical bugs
  * Be sure the code works and there is nothing that would make it broken
  * Make sure all tools in code use #if 0, search for `_Tool_`
  * Try a clean rebuild and check `make install`

#### 2. Update ####
  * Content
    * For new tracks: add to champs and challs, make track's ghosts
    * Run editor tools to check tracks (errors, presets, etc)
    * For new cars: check in-car cameras, perf test etc
  * Readme.txt (links, track count, etc)
  * Version numbers
    * in gui, file `*_`en.tag.xml, tag name="`GameVersion`"
    * in installer.nsi script, at top
  * Localization
    * run locale/tx\_1upd-all.bat so there are no #{MyGUI Tags} in GUI
    * run it again after translations have been made

#### 3. Test ####
  * Check all the game modes (Championship, Challenge, Split screen, Multiplayer, Replays)
  * Check at least new features and important older ones (see [Features](Features.md) wiki page)
  * Delete/rename your user dir to check default config and cache generation
  * Try a few different cars and tracks
  * Test graphics presets from combo and effects
  * Try editor (duplicate a track, save, and at least basic editing)

#### 4. Packages ####
  * Create packages for supported systems and test them
    * Linux binaries - need VM (was 12.04), info how to here [dist/linux-archive/Readme.md](https://github.com/stuntrally/stuntrally/tree/master/dist/linux-archive)
    * Windows installer - use dist/installer.nsi
  * Make sure all packages use the same version of the sources
  * Once the packages work, tag the version number to all repositories (stuntrally and tracks)
  * Upload packages, download back and test (or check checksums) to make sure there wasn't corruption

#### 5. Websites ####
  * Update websites
    * [Homepage](http://code.google.com/p/vdrift-ogre/), tracks count, release date, downloads link
    * [Changelog](Changelog.md), [ReleaseStats](ReleaseStats.md), [Features](Features.md)
  * Update Tracks Browser
    * rename tracks.ini to .txt, use dist/make\_roadstats\_xml.py, push to repo
    * also cars.xml for Car Browser, remove unnecessary comments
  * For significant look changes update home screen, and pics on other websites
  * Notify known third-party packagers about new release
  * Announce release (on forums, etc)