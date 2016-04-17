

<br>
<h2>Introduction</h2>

This page describes where the game searches for its data and configuration files.<br>
<br>
The information is useful if you are e.g.:<br>
<ul><li>submitting a bug/crash (you have to include your configs and logs)<br>
</li><li>need to reset or backup settigs<br>
</li><li>doing manual configuration (without the GUI)<br>
</li><li>or packaging Stunt Rally</li></ul>

<h2>Location of User's dir</h2>

<b><i>Since version 1.9 you can see the path used, directly in game, in Gui, on Help page, under User Path. You can mark it and copy.</i></b>

On Windows Vista and 7, the user's directory is located in<br>
<pre><code>`C:\Users\USERNAME\AppData\Roaming\stuntrally`<br>
</code></pre>
Earlier versions of Windows probably use<br>
<pre><code>`C:\Documents and Settings\USERNAME\Application Data\stuntrally`<br>
</code></pre>
Note that the actual directory names might be affected by localization of your Windows.<br>
<br>
On Linux (and other similar systems), the user's dir is most likely<br>
<pre><code>`~/.config/stuntrally`<br>
</code></pre>
(where tilde means the user's home directory).<br>
<br>
However, <code>$XDG_CONFIG_HOME/stuntrally</code> takes precedence if the environment variable is set.<br>
<br>
<br>
<h2>User Configs and Logs</h2>

The <b>default</b> configuration files are located in the data path, under <code>config</code>-subdirectory. The game creates dedicated configuration files for each users and they take precedence over the defaults. If you want to reset your configuration to defaults, just delete your user's dir game.cfg, input<code>*</code>.xml, editor.cfg.<br>
<br>
Files in user's dir are:<br>
<ul><li><b>Configs</b>
<ul><li>editor.cfg - settings for editor<br>
</li><li>game.cfg - settings for game<br>
</li><li>input.xml - game input bindings from General page only<br>
</li><li>input_p0.xml .. input_p3.xml - input bindings for players 1..4 (you can copy them for backup, and replace files to have different setups)<br>
</li><li>progress.xml - championships progress<br>
</li><li>progress_rev.xml - same as above but for reverse direction<br>
</li><li>progressL.xml, progressL_rev.xml - challenges progress<br>
</li></ul></li><li><b>Logs</b>
<ul><li>ogre.log - rendering and game log (most important)<br>
</li><li>ogre_ed.log - editor log<br>
</li><li>log.txt - VDrift simulation log<br>
</li><li>MyGUI.log - not important, stuff from GUI</li></ul></li></ul>

<h2>User data</h2>

As the game's installation directory might very well be write protected from non-administrators, your user generated data is saved in user's dir. This data might be critical to the game or editor, but they can start without it with default settings.<br>
<br>
Subdirs are: <i>(mode is easy or normal, both simulation modes)</i>
<ul><li>cache - see more below<br>
</li><li>data/carsim/mode/cars - if you edit car (Alt-Z) and save it, then it will be here<br>
</li><li>data/carsim/mode/tires - if you edit tires (one of graphs mode F9), and then save them (Alt-Z, Tires tab), they will appear here<br>
</li><li>ghosts/mode - best laps for each car on each track are saved here<br>
</li><li>records/mode - .txt files for best times on tracks<br>
</li><li>replays - if you save replays they land here<br>
</li><li>screenshots - filled when making screens in game or editor (by default F12)<br>
</li><li>tracks - user made tracks are located here. To share a track just pack the track's dir. Then unpacking here makes the track available.</li></ul>

If you want to reset record time for a track just go inside records/ and delete the .txt file with same track name (or edit it and remove section for a car name).<br>
<br>
To completely remove the game you need to delete your user's dir. Ghosts and replays may become big (e.g. 1GB).<br>
<br>
<br>
<h2>Game Data</h2>

As a rule of thumb, Stunt Rally doesn't care what its working directory is (i.e. from where you run the game). It will detect the actual executable location and search the data in relation to that.<br>
<br>
There are few different possibilities here, making it possible to run the game from the Git source tree as well as from <code>make install</code>ed prefix. On Linux, common system data installation paths as well as <code>XDG_DATA_DIRS</code> are checked too.<br>
<br>
If you have your data in a really obscure path, you can always define <code>STUNTRALLY_DATA_ROOT</code> environment variable.<br>
<br>
<h2>Cache</h2>

Cache is used for automatically generated files. Deleting cache files is safe - the application will re-create them when they are next needed, although this might result in a temporary slow-down.<br>
<br>
On Windows, this is currently the same as user's config directory.<br>
<br>
On Linux (and other similar systems), the cache dir is most likely <code>~/.cache/stuntrally</code> (where tilde means the user's home directory). However, <code>$XDG_CACHE_HOME/stuntrally</code> takes precedence if the environment variable is set.<br>
<br>
<br>
<h2>OGRE plugins</h2>

On Windows, Ogre plugins should be in the same directory with the exe. On Linux, the following paths are searched (in that order):<br>
<br>
<ol><li><code>/usr/local/lib64/OGRE</code> (only on 64 bit systems)<br>
</li><li><code>/usr/local/lib64/ogre</code> (only on 64 bit systems)<br>
</li><li><code>/usr/lib64/OGRE</code> (only on 64 bit systems)<br>
</li><li><code>/usr/lib64/ogre</code> (only on 64 bit systems)<br>
</li><li><code>/usr/local/lib32/OGRE</code> (only on 32 bit systems)<br>
</li><li><code>/usr/local/lib32/ogre</code> (only on 32 bit systems)<br>
</li><li><code>/usr/lib32/OGRE</code> (only on 32 bit systems)<br>
</li><li><code>/usr/lib32/ogre</code> (only on 32 bit systems)<br>
</li><li><code>/usr/local/lib/OGRE</code>
</li><li><code>/usr/local/lib/ogre</code>
</li><li><code>/usr/lib/OGRE</code>
</li><li><code>/usr/lib/ogre</code></li></ol>

On all platforms, you can specify a custom location for the plugins by setting the environment variable <code>OGRE_PLUGIN_DIR</code>.<br>
<br>
<br>
<h2>Config XMLs</h2>

Here is a list of config files used in game and editor. Changing them isn't needed.<br>
<br>
This can be useful for those who want to know, tinker or extend the content (no need to build).<br>
<br>
<ul><li>Game<br>
<ul><li>config/championships.xml - contains all championships with tracks<br>
</li><li>config/challenges.xml - has all challeges setup, see top of file for complete reference<br>if you want to edit or make your own challenges<br>
</li><li>config/cars.xml - has all what is shown in cars list and some timing factors<br>
</li><li>data/cars/cameras.xml - all cameras with their parameters, own camera setups can be made there<br>
</li></ul></li><li>Common<br>
<ul><li>config/tracks.ini - all track stats shown in tracks list, and track time, more info in file at top<br>
</li><li>data/materials2/fluids.xml - has all params for water/mud buoyancy<br>
</li><li>data/trees/collisions.xml - setup for all vegetation models collision (single capsule for trees, trimesh for rocks etc)<br>can be edited and tested directly in game<br>
</li><li>data/materials/scene/<code>*</code>.mat - has most materials, useful eg. when addig new skies, grasses, trees, road and object materials and/or tweaking their look<br>
</li></ul></li><li>Editor<br>
<ul><li>config/presets.xml - <i>since ver 2.3</i>, contains parameter values for terrain layers, road,<br>grasses and vegetation (shown in lists in pick window)<br>adding here is needed if you make any new material (so it is shown in editor and can be picked)<br><i>if not then only way is to put in scene.xml in track</li></ul></li></ul></i>
