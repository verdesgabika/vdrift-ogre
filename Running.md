## Hardware requirements ##

The **minimum** hardware is:

| **CPU:**| with 2 cores, 2.0 GHz |
|:|:----------------------|
| **GPU:**| GeForce 9600 GT or Radeon HD 3870 |
| | with Shader Model 3.0 supported and 256 MB GPU RAM|

It is possible to run on older, (e.g. on 1 core CPU and GeForce 7600 GT, with 30 Fps and Low settings),

As for laptops: newer laptops are best suited for the game.<br>
Integrated graphics processors (from Intel and AMD) will work, but may be slow, especially the older ones.<br>
<br>
In any case, if you get graphic errors, try updating your graphic driver.<br>
<br>
<br>
The game is developed on a PC with GeForce GTX 560 Ti, which is the <b>recommended</b> hardware.<br>
<br>
Using default settings (Higher), and with no effects, it achieves above 60 Fps on all tracks (more on smaller ones).<br>
<br>
Also tested with GT 640 with reduced settings at about 40 Fps.<br>
<br>
<br>
<h2>Running</h2>
<ol><li>Esc/Tab key shows/hides GUI (F1 or ` in Editor).<br>
</li><li>At first, go to Options and adjust resolution (on Screen, Main tab).<br>
</li><li>Then pick Graphics preset according to your GPU.<br>
</li><li>Quit game to save settings.<br>
</li><li>Press New Game button to start driving.<br>
</li><li>For new users, read the Hints shown on welcome screen at game start<br>
</li><li>Visit help page in game to read Quick help.<br>
</li><li>Have Fun !</li></ol>

<br>
<h2>Input</h2>

Keys used in game can be seen in Options on tab <code>[</code>Input<code>]</code>.<br>
<br>
If you want to reassign keys, or have a <i>game controller</i> go to tab <code>[</code>Player1<code>]</code> to bind it and test range.<br>
<br>
For keyboard input, there is a sensitivity setting. You can change it for each control, or pick for all from combo (preset).<br>
<br>
There are also speed sensitive steering and steering range settings on Setup tab in single race window.<br>
<br>
<br>
By default, in game you can change <b>cameras</b> with C/X (with shift for main cameras only).<br>
<br>
Cameras can be adjusted in game, by mouse - move mouse to see actions.<br>
<br>
<br>
<h3>Controllers</h3>

Click button to start binding, then move axis or press button or key to bind it.<br>
<br>
Click on Edit > to change Inverse for a control (for analog axis).<br>
<br>
Press RMB (right mouse) on button to unbind.<br>
<br>
<br>
Check your axes range on those bars displayed.<br>
<br>
If moving an axis from start to end also moves the bar from left to right completely (and without moving over the range) then configuration is done properly.<br>
<br>
<br>
<i>Binding both controller axis and keyboard keys is possible.</i>

<i>To check if your device was detected search for <code>&lt;Joystick&gt;</code> in ogre.log</i>

<br>
After your configuration is complete you can restart game to have the settings saved.<br>
<br>
You may want to backup your input_p0.xml (for Player1) in user settings dir (see <a href='Paths.md'>Paths</a> wiki page) or create presets this way.<br>
<br>
<br>
<br>
<h2>Graphics Options</h2>

Using preset combobox (which changes all settings) should be enough. Remember to quit and restart after change.<br>
<br>
You may want to change some options individually.<br>
There are few <code>[</code>Graphics<code>]</code> options that are more important and have more impact on performance than the rest.<br>
<br>
<i>Fps - Frames per second. The first value shown in upper left corner of the screen.</i><br> Higher values mean smoother play. It is recommended to play with at least 30 Fps.<br>
<br>
<ul><li>Effects - have very big impact on Fps (usually any will half the Fps). It is recommended to turn them off for smooth play. Bloom is the only one less Fps intensitive.</li></ul>

<ul><li>Shadows - the biggest Fps killer. If you have low Fps turn them off (None) also this is recommended for split screen, since the Fps drops there with each new player viewport.</li></ul>

<ul><li>Vegetation - also a Fps killer, reduce Trees and Grass multipliers for more fps. For newer GPUs you can set them higher to have a denser vegetation.</li></ul>

<ul><li>Materials tab - if you have an old GPU, you should lower Anisotropy (0-16, 4 is enough), Terrain (Low, Normal, Parallax) and Shaders. Turning off Triplanar can reduce Fps very much, especially on demanding tracks (big and with high mountains).</li></ul>

For minimum settings just pick Lowest from preset combobox and restart.<br>
<br>
<br>
<h2>Configs</h2>

All settings are saved in <code>game.cfg</code> file or in <code>editor.cfg</code>.<br>
<br>
<b>For help on how to locate these files, see <a href='http://code.google.com/p/vdrift-ogre/wiki/Paths'>Paths</a> wiki page.</b>

Deleting this file(s) will force using default settings at next start of game or editor.<br>
<br>
If problems occur check <code>ogre.log</code> and <code>log.txt</code> for errors (or <code>ogre_ed.log</code> for editor).<br>
<br>
<br>
<h2>Feedback</h2>

If you have problems running, best way is to tell us on IRC (see homepage for info). Or post on Forum. Last way is using Issues here.<br>
<br>
Testing and reporting is very welcome. Especially if you can build the game from sources.