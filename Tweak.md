

<br />
## Tools list ##
This Wiki describes most tools available in game (found on Tweak tab).<br>
How to use them and what are they for.<br>
Mainly they are helpful in visualizing the result of edited .car sections.<br>
<br>
They are listed here for quick guide:<br>
<br>
<table><thead><th> <b>Key</b> </th><th> <b>Tool name</b> </th><th> <b>Description</b> </th></thead><tbody>
<tr><td> F11        </td><td> Fps bar          </td><td> show/hide the Fps bar </td></tr>
<tr><td> F10        </td><td> Wireframe        </td><td> changes normal rendering to wireframe lines, Ctrl-F11 in editor </td></tr>
<tr><td> Ctrl-F10   </td><td> Bullet Debug Lines </td><td> show collision shapes as lines </td></tr>
<tr><td> F9         </td><td> Graphs           </td><td> many types, show detailed change of some values, life over time period </td></tr>
<tr><td> Shift-F9   </td><td> Car debug Text   </td><td> shows text values from simulation </td></tr>
<tr><td> Alt-Z      </td><td> Car file Editor  </td><td> allows editing .car file in game, Alt-Shift-Z will save changes and restart  </td></tr>
<tr><td> Ctrl-F5    </td><td> Perf Test        </td><td> Starts car performance test, results show eg. 0-100 kmh time etc. </td></tr></tbody></table>

<br />
<h2>Common</h2>
In game and editor.<br>
<br>
<br />
<h3>Fps bar</h3>
Toggle Fps bar showing with F11.<br>
<br>
This small left top bar shows 4 values (that change, especially when moving):<br>
<ol><li>Rendered Frames per second (Fps), it's best to play with at least 30, 60 being optimal for most monitors.<br>
</li><li>Triangle count, e.g. 821k means there are 821 000 triangles drawn each frame.<br>
</li><li>Batches count, e.g. 254 means there were 254 draw calls to render geometry on GPU.<br>
</li><li>GPU Memory use. e.g. 261M means 261 MB are occupied (by textures, geometry etc).</li></ol>

<br />
<h3>Wireframe</h3>
Toggle wireframe mode with F10. In editor use Ctrl-F11.<br>
<br>
It is useful to check how dense are triangles in car/wheel model (or also for whole track).<br>
<br>
<br />
<h2>Game tools</h2>

<br />
<h3>Bullet Debug Lines</h3>
This is useful to check and adjust the shape of car body that collides.<br>
<br>
To use bullet lines first check the global (Startup) option, and restart game.<br>
<br>
<img src='http://wiki.vdrift-ogre.googlecode.com/git/tweak/1.jpg' />

<br>
If game was started with it enabled, you can toggle bullet debug lines with Ctrl-F10 or the next checkbox.<br>
<br>
<img src='http://wiki.vdrift-ogre.googlecode.com/git/tweak/2.jpg' />

If you just need to edit car collision, don't use official tracks.<br>
<i>They have a lot of vegetation and it will be horribly slow to draw all lines (and this stays until you quit and restart game).</i><br>
Use test tracks which are usually quite empty (and also reload fast).<br>
<br>
<br />
<h3>Developer keys</h3>

If you mark the checkbox 'Developer keys..', also shown on previous screen (Tweak tab), you can:<br>
<br>
1. Use alt-shift-digit to quickly start a test track, without using menu.<br>
See <a href='https://github.com/stuntrally/stuntrally/blob/master/source/ogre/Gui_KeyPress.cpp#L123'>here in sources</a> for which track is on which digit key.<br>
So e.g. Alt-Shift-1 will load Test1-Flat, Alt-Shift-3 loads TestC4-ow, etc.<br>
<br>
2. Press Ctrl-F at any time to show Gui and focus cursor in track search edit.<br>
<br>
<br>
<br />
<h3>Tree collisions</h3>

As shown on previous screen, you can see yellow capsule shapes for palms.<br>
We use such simple shapes for trees. No need for full trimesh and should be faster.<br>
<br>
Editing those tree collisions, is done in game, file collisions.xml.<br>
<br>
Open Tweak window and switch to collisions tab, to edit that file.<br>
Shift-Alt-Z will save your modifications, and restart game.<br>
See the top of this file for more info (e.g. how to disable collision or use full trimesh for model).<br>
<br>
<br>
<br />
<h3>Car file Editor</h3>
Editing car settings (.car file) is done in game.<br>
<pre><code>Alt-Z - toggles car editor in game.<br>
<br>
Alt-Shift-Z - saves changes and restarts game.<br>
</code></pre>
Use tracks Test1-Flat or Test2-Asphalt etc, to reduce reloading time and concentrate on editing car.<br>
<br>
<i>You can use your Text Editor (e.g. to have syntax coloring) and press F5 to reload game after saving .car file.</i>

If the .car file for current car wasn't modified, Editor will show cyan "Original" text and file path.<br>
After saving changes, yellow "User" path will appear.<br>
<br>
Edited .car file is located in user dir path (see <a href='Paths.md'>Paths</a>) in data/carsim/mode/cars/ subdir,<br>where mode is current simulation mode (easy or normal).<br>
<br>
<br />
<h3>Graphs</h3>
Graphs in game can be used to test more advanced car behaviour and simulation.<br>
<br>
Press F9 to show/hide, F2,F3 will cycle through various graph types. Or use Gui to pick from combo.<br>
<br>
E.g. Car engine torque curve can be seen, all gear ratios for car speed.<br>
Those are explained more in <a href='CarEditing.md'>CarEditing</a>.<br>
<br>
<br>
<br />
<h3>Car debug Text</h3>
This was the first simulation visualisation and it is still useful if you want to check the values (if they don't change too fast).<br>
<br>
Use this checkbox to toggle it or Shift-F9.<br>
<br>
On Gui you can also change how many text sections are displayed and change text color to black or white.<br>
<br>
<img src='http://wiki.vdrift-ogre.googlecode.com/git/tweak/3.jpg' />

<br />
<h3>Performance test</h3>

Car performance test is automatic. It's used to get car performance info, which is shown on Gui, tab Car.<br>
<br>
Also useful to check this when editing car (especially engine torque).<br>
<br>
Press Ctrl-F5 to run test for current car (it will load track <code>Test10-FlatPerf</code>).<br>
<br>
The car will accelerate to top speed and then brake. Simulation is speed up for this (to not wait long for results, factor in game.cfg section sim, perf_speed, use 1 for normal).<br>
<br>
After it finishes it will show up results, and save them in user dir. This is in user path /data/cars/ES/ES_stats.xml<br>
<br>
Perf test stats contain info like max engine torque and power, top speed, acceleration times to 60, 100, 160, 200 km/h (with downforce and drag at those speeds) and brake time from 100, 60 to 0 km/h.<br>
<br>
Most of those stats are then shown in info panel on Gui when when picking car in game.<br>
<br>
<i>Run it for each sim mode (provided you made it different as game requires). See bottom of page for differences list.</i>

<img src='http://wiki.vdrift-ogre.googlecode.com/git/tweak/4.jpg' />


<br />
<h2>Game (advanced)</h2>

<br />
<h3>Surfaces</h3>

<img src='http://wiki.vdrift-ogre.googlecode.com/git/tweak/12.jpg' />

<br />
<h3>Tires</h3>
<img src='http://wiki.vdrift-ogre.googlecode.com/git/tweak/10.jpg' />

<img src='http://wiki.vdrift-ogre.googlecode.com/git/tweak/11.jpg' />

Tire editing is meant only for people with good knowledge of simulation, who know Pacejka Magic Formula.<br>
<br>
It can be very time consuming/wasting, and produce no better results.<br>
<br>
Other and simpler parameters are in surfaces.cfg.