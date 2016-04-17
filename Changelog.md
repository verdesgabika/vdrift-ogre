### What's coming next ###

This section lists stuff that is not yet released, but committed to [repository](https://github.com/stuntrally/stuntrally/commits/) (master).


## ChangeLog ##
Info about changes in each released version. How did they look like can be seen in [gallery](http://picasaweb.google.com/CryHam/).

  * 172 tracks (5 New)
  * Updates in tires tweak tab
  * Updated and new alien buildings

<br>
<table><thead><th> <b>Version 2.5</b> </th><th> 03. 11. 2014 </th></thead><tbody></tbody></table>

<ul><li>167 tracks (20 New)<br>
</li><li>5 New sceneries: Surreal, Stone, Space, Alien, BlackDesert<br>
</li><li>Common<br>
<ul><li>Renamed all tracks with 3 letter prefixes, showing short name in list<br>On Replays tab there is a button to "Rename All Old" replays,ghosts and records<br>
</li></ul></li><li>Game<br>
<ul><li>New challenges and championships<br>
</li><li>Solid fluids (e.g. ice, lava, added in editor fluids mode, but solid and flat)<br>
</li><li>Rewind cooldown, after rewind 1 sec delay until next use is possible<br>
</li><li>Fixed game setup update in multiplayer (before was updated only after track change)<br>
</li></ul></li><li>GUI - Tracks list<br>
<ul><li>Now with short name, difficulty and length ratings (in default short view)<br>
</li><li>Selectable columns, and filtering, button Y, Ctrl-F twice to toggle<br>
</li></ul></li><li>Common<br>
<ul><li>Fixed black terrain on ATI/AMD Radeon cards<br>
</li><li>Many smaller fixes<br>
</li><li>Changed translations, more info for strings, own program to generate .pot, <a href='http://forum.freegamedev.net/viewtopic.php?f=81&t=5729'>topic</a>, <a href='https://code.google.com/p/vdrift-ogre/wiki/Localization'>Wiki</a>
</li><li>New user log files with errors and warnings only, ogre.err and ogre_ed.err<br>
</li></ul></li><li>Editor<br>
<ul><li><a href='http://i.imgur.com/IGHsGQG.jpg'>Easier on pipe</a> creating, mark (key 8) now also moves pipe down (ctrl-8 the old way)<br>
</li><li>On pipe sections now marked on minimap as orange<br>
</li><li>Up/down keys working in pick window and objects lists, buildings groups list<br>
</li><li>Checkbox to ignore all "Wrong checkpoint" messages on track (for curly tracks where checks overlap road)<br>
</li><li>Better checkpoints in pipe, now in center and radius 1<br>
</li></ul></li><li>Tweak<br>
<ul><li>Reference graph for tires, loading tires<br>
</li></ul></li><li>Code<br>
<ul><li>Reworked Road_Rebuild.cpp, cleaner, data stucts, split to Road_Prepass.cpp<br>
</li><li>Split common .cfg to settings_com.h and cpp<br>
</li><li>specMap_rgb option in .mat (for rgb only specular maps)<br>
</li><li>Check if tracks and cars exist before replay load<br>
</li><li>Fixed most CppCheck warnings</li></ul></li></ul>

<br>
<table><thead><th> <b>Version 2.4</b> </th><th> 09. 08. 2014 </th></thead><tbody></tbody></table>

<ul><li>147 tracks (6 new, 12 old deleted, some renewed)<br>
</li><li>2 New sceneries: Crystals, GreeceWhite<br>
</li><li>Cars<br>
<ul><li>3 New: TU, SZ, FN (old FM)<br>
</li><li>4 renewed: XZ, LK4, S1, UV<br>
<ul><li>better materials, less submeshes, baked AO<br>
</li></ul></li><li>2 old deleted: XM, NS<br>
</li></ul></li><li>Simulation<br>
<ul><li>Spaceship hovercrafts, Not drivable in pipes<br>
<ul><li>3 New: V1, V2, V3 in cars list<br>
</li></ul></li><li>Sphere, O in cars list, Too bouncy<br>
</li></ul></li><li>Common<br>
<ul><li>New sky textures, on half of tracks<br>
</li><li>New static objects on few tracks<br>
</li><li>Dropped SceneryID, each track has own cache<br>
</li></ul></li><li>Gui<br>
<ul><li><a href='http://i.imgur.com/DkuMS6p.jpg'>Car tab</a> with bars for stats, speed graph, short list view<br>
</li><li>Split, to new Graphics and Tweak tabs<br>
</li><li>Fonts bigger and resized with resolution<br>
</li></ul></li><li>Game<br>
<ul><li><a href='http://i.imgur.com/jaRlksI.jpg'>Welcome screen</a> with game Hints, shown on first run<br>
</li><li>Sounds for win, loose, lap, best time, wrong checkpoint<br>
</li><li>Fixed multiplayer (<a href='http://forum.freegamedev.net/viewtopic.php?f=78&t=5650#p57946'>nick appeared twice</a>)<br>
</li><li>Damage from terrain, height fog, fluids on few tracks<br>
</li><li>Possible to have different road surfaces on 1 track<br>
</li></ul></li><li>Editor<br>
<ul><li><a href='http://forum.freegamedev.net/viewtopic.php?f=79&t=5581#p57754'>Color pick window</a> with H,S,V sliders (for light,fog,trail colors)<br>
</li><li>Mode is now an image (not text Cam,Edit,Gui)<br>
</li><li>Pick window for skies, sky rotation<br>
</li><li>Height brush, Space - pick height from cursor<br>
</li><li>Fixed edit mouse move crash<br>
</li></ul></li><li>Tweak<br>
<ul><li>Linear speed sensitive steering, <a href='http://imgur.com/1r4AH0Y'>graph on Gui</a>
</li><li>New graph (visualization) to help developing tire parameters<br>
</li><li>Edit surfaces in game's car tweak window</li></ul></li></ul>

<br>
<table><thead><th> <b>Version 2.3</b> </th><th> 11. 05. 2014 </th></thead><tbody></tbody></table>

<ul><li>153 tracks (7 new, 27 renamed)<br>
</li><li>Common<br>
<ul><li>All tracks renewed, new look<br>
</li><li>Terrain<br>
<ul><li>New textures, bigger 1k, with CC 0 license, more info in <a href='https://github.com/stuntrally/stuntrally/blob/master/data/terrain/about.txt'>data/terrain/about.txt</a>
</li><li>Blendmap noise with many parameters<br>
</li><li>Fixed triplanar uv swap, also now max 2 layers can be picked<br>
</li><li>Emissive light, on few tracks<br>
</li></ul></li><li>Grass<br>
<ul><li>Channels - different setups for grasses (e.g. white grass in higher mountains)<br>
</li><li>Grass density is a RenderToTexture<br>
</li></ul></li><li>Tracks tab: list sorting fix, more scenery colors, icons hiding, start position<br>
</li><li>Frames per second limitting option<br>
</li><li>Disabled parallax, broken<br>
</li><li>Updated Compiling Wiki, made Windows pre-built dependencies archive<br>
</li></ul></li><li>Game<br>
<ul><li>Dynamic camera bouncing, camera view angle sliders<br>
</li><li>Boost fuel depending on track length, more boost options<br>
</li></ul></li><li>Editor<br>
<ul><li>Pick window for terrain textures, grasses and vegetation models<br>
<ul><li>Tab key show/hide, bigger list, mouse wheel on button picks next/previous<br>
</li><li>Fill settings (marked with .) from presets.xml (optional)<br>
</li></ul></li><li>Game tab with track settings: gravity, wind, deny reversed, etc.<br>
</li><li>Terrain<br>
<ul><li>Test blendmap F9<br>
</li><li>Faster terrain editing, blendmap is now a RTT with shader<br>
</li><li>Swap layer buttons<br>
</li><li>Enter - lock brush position (use for big brushes to avoid blur)<br>
</li></ul></li><li>Fixed selected objects rotation (many) and copy<br>
</li><li>Start position rotation also global and roll<br>
</li><li>Update button on Layers, Grasses, Vegetation for faster update (same for F8)<br>
</li><li>Vegetation model info: count and real sizes <code>[</code>m<code>]</code>
</li><li>Surface tab for terrain and road surface params (split from Layers tab)<br>
</li><li>Test SceneryID button, shows % difference</li></ul></li></ul>

<br>
<table><thead><th> <a href='VersionHistory.md'>Older versions continued here</a>. </th></thead><tbody>