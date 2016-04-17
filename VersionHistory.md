| [Newer versions changelog here.](Changelog.md) |
|:-----------------------------------------------|

<br>
<table><thead><th> <b>Version 2.2.1</b> </th><th> 28. 11. 2013 </th></thead><tbody></tbody></table>

<ul><li>Fixed crash, happened in track loading, for tracks that have pipe transition segments.<br>
</li><li>Updated Italian translation</li></ul>

<br>
<table><thead><th> <b>Version 2.2</b> </th><th> 25. 11. 2013 </th></thead><tbody></tbody></table>

<ul><li>146 tracks (19 new)<br>
</li><li>Game<br>
<ul><li>Challenges (new game mode)<br>
<ul><li>Short series of tracks. Only the best drivers will succeed. <br>Drive with no mistakes to win bronze,silver or gold prize.<br>Normal simulation, no driving aids.<br>
</li></ul></li><li>Multiplayer updated<br>
<ul><li>Host can press new game and continue on other track (no need to quit and create)<br>
</li><li>Game info text, track info now on track tab<br>
</li></ul></li><li>Hud<br>
<ul><li>New layout (gauges on right, minimap on left)<br>
</li><li>Times bar shows current points and time difference each checkpoint<br>
</li><li>Lap result window (last, best times, final points) on right<br>
</li></ul></li><li>Input checkbox to bind 1 axis to both throttle and brake<br>
</li><li>Rocks with better collision (triangle mesh)<br>
</li><li>Better water and mud particles<br>
</li><li>Damage repair each lap option<br>
</li><li>Auto camera change in loops (by marking checkpoints in editor, key 7)<br>
</li></ul></li><li>Common<br>
<ul><li>Gui reworked, more icons, also on Input tab<br>
</li><li>Graphics presets now on Screen tab (need to quit after change)<br>
</li><li>All sliders have default value, press RMB on slider to reset<br>
</li></ul></li><li>Other<br>
<ul><li>New objects for caves, pipe obstacles, column for rocks<br>
</li><li>New loading screens<br>
</li><li>Tire force circles visualization<br>
</li><li>Separated differential settings in .car, center of mass length offset, better TW handling<br>
</li><li>Road total on-pipe percentage (need to mark segments in editor, key 8)<br>
</li><li>Road stats banked angle average and max<br>
</li></ul></li><li>Editor<br>
<ul><li>Some edit fields now also with slider and sliders with edits<br>
</li><li>Checkpoint radius restrictions (1 to 2.5 on terrain, constant on bridges and pipes), force with ctrl<br>
</li><li>Objects<br>
<ul><li>Selection mark (glow)<br>
</li><li>Better mouse picking<br>
</li><li>Selection scale, rotate (only simple works)<br>
</li></ul></li><li>Gui revamp<br>
<ul><li>Split tabs into Track window, Grasses tab, Settings on 3 tabs<br>
</li></ul></li><li>Change in road point keys<br>
<ul><li>1,2 Roll, 3,4 Yaw, alt-1,2 angle type, 5,6 snap, alt-shift-1 zero angles<br>
</li></ul></li></ul></li><li>Fixes<br>
<ul><li>Optimization, less batches for Hud, opponents list hidden by default<br>
</li><li>Fixed broken translations (wrong check, loading etc.)<br>
</li><li>Fixed input on gui edits (ctrl is stuck, press it to fix) in chat after network game or in find box<br>
</li><li>Linux release archive was outputting user data into wrong location (was in .local/data)<br>
</li><li>Fixed minimap road preview save in editor (shader errors)<br>
</li><li>No simulation before game start (fix multiplayer jumps, but shows car landing more)<br>
</li></ul></li><li>Sources<br>
<ul><li>Huge changes in headers and cpp, split to more (CGame,CHud,CGui,CApp), fixed includes<br>
</li><li>Gui Init code shorter, grouped controls in CGui.h, common Gui code in GuiCom class<br>
</li><li>Using own classes SliderValue and Check</li></ul></li></ul>

<br>
<table><thead><th> <b>Version 2.1</b> </th><th> 07. 08. 2013 </th></thead><tbody></tbody></table>

<ul><li>127 tracks (11 new)<br>
</li><li>5 new cars: UV, HR, OT, FR4, TW<br>
</li><li>Game<br>
<ul><li>Input reimplemented with SDL2 (shoud fix input issues), using OICS (not OIS and OISB)<br>
</li><li>Simulation fix (steering, too big car inertia, updated aerodynamics)<br>
</li><li>Next checkpoint beam<br>
</li><li>Other car ghost (when current unavailable)<br>
</li><li>Track's ghost (best drive for all tracks) (green ES car, from normal simulation mode)<br>
</li><li>Simple car damage<br>
<ul><li>damage % indicator, no visual changes yet<br>
</li><li>decreased performance when over 50 %, car destroyed at 100 %<br>
</li></ul></li><li>Reworked scoring, now points and race position<br>
</li><li>Brake lights flares<br>
</li><li>New championships and tutorials, higher pass score, reverse option<br>
</li><li>Steering range sliders on Gui tab setup<br>
</li><li>Adaptive fov effect when boosting<br>
</li></ul></li><li>Gui<br>
<ul><li>Gui rework, added icons to main tabs, all tab colors<br>
</li><li>Car paint reflectiveness, new slider<br>
</li><li>Car tab shows car speed and type<br>
</li><li>Track tab shows track time for current car, points<br>
</li><li>Championship groups, info text, times in list<br>
</li><li>Sections in .car editor<br>
</li></ul></li><li>Editor<br>
<ul><li>Terrain brushes<br>
<ul><li>new presets (87 total)<br>
</li><li>new functions: Noise2 (inversed), N-gon (regular polygon)<br>
</li></ul></li><li>Terrain generator<br>
<ul><li>preview image (green up, blue down)<br>
</li><li>add/substract/multiply to current terrain<br>
</li><li>omit road possible<br>
</li></ul></li><li>Context help for current mode Ctrl-F1<br>
</li><li>Top view toggle Alt-Z<br>
</li><li>Warnings tab showing track errors,warnings and hints after save<br>
</li><li>Road mirror selected segments Alt-Home<br>
</li><li>Rearranged keys (-= <a href='.md'>.md</a> ;' ,. now also on 9,0 O,P K,L N,M)<br>
</li><li>Using key scan codes (regional keyboards shouldn't matter)<br>
</li></ul></li><li>Fixes<br>
<ul><li>Fix editor crash on align road U and simulate objects C<br>
</li><li>Fix auto gearbox change oscillations<br>
</li><li>Fix car particles emit on pause<br>
</li><li>cg is now not required to run<br>
</li><li>Small fixes in input bind Gui</li></ul></li></ul>

<br>
<table><thead><th> <b>Version 2.0</b> </th><th> 06. 05. 2013 </th></thead><tbody></tbody></table>

<ul><li>116 tracks (5 new, 18 renewed)<br>
</li><li>4 new cars: N1, S8, XZ, LK4, also renewed 3S and some wheels<br>
</li><li>Updated wiki pages with navigation and new car pages<br>
</li><li>Graphics<br>
<ul><li>New pines and rocks in winter<br>
</li><li>Height fog and 2 color fog on some tracks<br>
</li><li>Better materials, specular on glass pipes, objects<br>
</li><li>Blending between road materials<br>
</li><li>Terrain triplanar 1 layer option (more Fps than full)<br>
</li><li>2 more graphics presets<br>
</li></ul></li><li>Game<br>
<ul><li>Car body glossiness, new slider<br>
</li><li>Grass deform under car<br>
</li><li>Minimap border option<br>
</li><li>Rewind ghost<br>
</li><li>Camera distance ray (shortens when near mountains)<br>
</li></ul></li><li>Fixes<br>
<ul><li>No memory leak (crashed after some New Games)<br>
</li><li>Optimisations for batch count, more Fps on big tracks<br>
</li><li>Proper start after loading (no camera jump, good reflections, preloaded impostors)<br>
</li><li>Fixed crashes, VDrift splitscreen, replay load, championship stage end<br>
</li></ul></li><li>Editor<br>
<ul><li>3D preview for vegetation models and objects<br>
</li><li>Objects editing improvements<br>
</li><li>Fixed align terrain to road issue with objects and fluids sizing<br>
</li><li>Default terrain error for track on HMap tab (more for high terrains)<br>
</li><li>Triplanar 1 checkbox on Layer tab (to mark high mountains)<br>
</li><li>Road wall, column materials, scale multipliers</li></ul></li></ul>

<br>
<table><thead><th> <b>Version 1.9</b> </th><th> 15. 01. 2013 </th></thead><tbody></tbody></table>

<ul><li>111 tracks (7 new)<br>
</li><li>All tracks renewed<br>
</li><li>2 new sceneries: Autumn and Moss (mossy jungle)<br>
</li><li>Simulation<br>
<ul><li>Easy (beginner) and Normal (simulation) modes<br>
</li><li>Simulation fixes (Big changes): <a href='http://code.google.com/p/vdrift-ogre/issues/detail?id=183'>details here</a>
<ul><li>New Tires - more grip driving and more control when sliding<br>
</li><li>Torque curve - fixed unrealistic behaviour at low rpm<br>
</li><li>No control in air after jump (only by flip)<br>
</li><li>Flip car speed and boost reduced<br>
</li><li>Suspension - soft for terrain, hard in jumps and pipes<br>
</li><li>Downforce - better handling at high speed<br>
</li><li>Proper center of mass, more mass<br>
</li></ul></li><li>Car performance statistics on Gui (acceleration times, engine power etc.)<br>
</li><li>New graphs in game (for torque curves, power, clutch, diffs)<br>
</li></ul></li><li>Graphics<br>
<ul><li>New grasses on all tracks<br>
</li><li>New trees (generated with <code>SnappyTree</code>)<br>
</li><li>Decreased shadows options - better Fps<br>
</li><li>More trees 1,5x, grass range 2x<br>
</li><li>Option for Impostors Only (low quality trees but fast smooth fps)<br>
</li><li>Fixed black terrain issue on some cards<br>
</li></ul></li><li>Editor<br>
<ul><li>Grass layers<br>
</li><li>Surface combobox with presets (no changing all params)<br>
</li><li>Alt-1,2 prev/next layer tab<br>
</li><li>Fixed car start box, visible now<br>
<br>
<table><thead><th> <b>Version 1.8</b> </th><th> 27. 10. 2012 </th></thead><tbody></li></ul></li></ul></tbody></table>

<ul><li>104 tracks (5 new)<br>
</li><li>Graphics<br>
<ul><li>Using new materials generator: <a href='https://github.com/scrawl/shiny'>shiny</a>
</li><li>New water and mud looks<br>
</li><li>Triplanar terrain option (high slopes with good texturing)<br>
</li><li>Fixed crash on amd and intel cards<br>
</li></ul></li><li>Editor<br>
<ul><li>Tweak page (in Options) for adjusting material parameters (for developers)<br>
</li></ul></li><li>Game<br>
<ul><li>New car S1<br>
</li><li>Fixed replay load crash<br>
<br>
<table><thead><th> <b>Version 1.7</b> </th><th> 02. 09. 2012 </th></thead><tbody></li></ul></li></ul></tbody></table>

<ul><li>99 tracks (12 new, 20 old renewed, with 8 VDrift tracks)<br>
</li><li>Gameplay<br>
<ul><li>Rewind - lets you take your car back in time after crash, spin out etc (default key: Backspace (hold)).<br>
</li><li>VDrift tracks (with all game features)<br>
</li><li>Static and Dynamic objects on tracks (barrels, boxes, buildings etc)<br>
</li><li>3D sounds, new car hit sounds - scrap and screech<br>
</li></ul></li><li>Simulation<br>
<ul><li>Asphalt tires (on VDrift tracks)<br>
</li><li>Fixed all cars parameters<br>
</li></ul></li><li>Editor<br>
<ul><li>New video tutorial (10 chapters)<br>
</li><li>Align terrain to road tool (for selected segments, key U)<br>
</li><li>Terrain brush presets (quick change)<br>
</li><li>Objects inserting and simulating<br>
</li><li>Auto update blendmap<br>
</li><li>Color images (on Sun tab and road trail)<br>
</li><li>Weather particles<br>
</li></ul></li><li>Tools in game<br>
<ul><li>Graphs (for car values debug, eg. tires slip, suspension, sound)<br>
</li><li>Tires editing (Pacejka coefficients)<br>
</li></ul></li><li>Graphics<br>
<ul><li>Shadow fixes (now on road wall and columns, shadowed road bug in DirectX)<br>
</li><li>God Rays effect (sun glare)<br>
</li><li>HDR, HQ Bloom and Vignetting (beta, too saturated)<br>
</li><li>Motion blur broken (on GL)<br>
<br>
<table><thead><th> <b>Version 1.6</b> </th><th> 19. 04. 2012 </th></thead><tbody></li></ul></li></ul></tbody></table>

<ul><li>79 tracks (9 new)<br>
</li><li>Gameplay<br>
<ul><li>Camera auto tilt on slopes<br>
</li><li>5 new gauge types (for rpm and velocity)<br>
</li></ul></li><li>Editor<br>
<ul><li>Filter brush (key F), filters terrain bumps<br>
</li></ul></li><li>Bug fixes<br>
<ul><li>split screen game crash from more to less players<br>
</li><li>car hood camera jumps<br>
</li><li>grass bad looking issue with effects<br>
</li><li>track percent for ghost and in replay<br>
<br>
<table><thead><th> <b>Version 1.5</b> </th><th> 08. 04. 2012 </th></thead><tbody></li></ul></li></ul></tbody></table>

<ul><li>70 tracks (+5 new, 5 renewed, -6 old deleted)<br>
</li><li>Gameplay<br>
<ul><li>Championships and tutorials (game mode to drive series of tracks for score)<br>
</li><li>Multiplayer (beta)<br>
</li><li>Keyboard sensitivity and return speed, also presets (slow,medium,fast)<br>
</li><li>Multi-threaded game (smoother play at lower fps)<br>
</li></ul></li><li>Game main menu, new help screen<br>
</li><li>Graphics<br>
<ul><li>Water reflection and refraction (screen effect), smooth transition to terrain<br>
</li><li>New screen effects: Soft particles, Depth of field<br>
</li><li>New HUD code (gauges, minimap work in split screen and with effects)<br>
</li></ul></li><li>Replays<br>
<ul><li>Fluid particles and sounds, hit sparks saved in replays<br>
</li><li>Viewing replays for more players with fewer viewports, changing player<br>
</li></ul></li><li>Editor<br>
<ul><li>Fixed surfaces saving/editing bug<br>
<br>
<table><thead><th> <b>Version 1.4</b> </th><th> 04. 01. 2012 </th></thead><tbody></li></ul></li></ul></tbody></table>

<ul><li>71 tracks<br>
</li><li>2 new cars TC6, NS<br>
</li><li>Graphics<br>
<ul><li>Proper shadows (depth/self shadows, terrain lightmap on car, road, trees...)<br>
</li><li>Improved shader effects (powered by a dynamic material & shader generator)<br>
</li><li>Car fresnel effect, reflectivity/specular maps<br>
</li><li>New effects "Screen Space Ambient Occlusion" and Antialiasing SSAA<br>
</li></ul></li><li>Gameplay<br>
<ul><li>Mud (on tracks J14-Muddy, D9-Mud)<br>
</li><li>F12: Go to last checkpoint, F4: Restart race (without loading)<br>
</li><li>New sounds (boost, water, mud) and particles<br>
</li><li>Track completion percentage indicator<br>
</li><li>Distance to other cars / ghost indicator<br>
</li><li>All cars / ghost on minimap (partial)<br>
</li><li>Improved in-car camera<br>
</li><li>Rear gear throttle-brake inverse option<br>
</li></ul></li><li>Performance<br>
<ul><li>Car paint color instant change<br>
</li><li>Option to turn off impostors (2D trees in the distance)<br>
</li><li>Customizable shader quality<br>
</li><li>Newer Paged Geometry version (faster vegetation)<br>
</li></ul></li><li>Editor<br>
<ul><li>Fluids editing (water, mud areas)<br>
</li></ul></li><li>Other<br>
<ul><li>Now using MyGUI3.2 (MyGUI 3.0 will NOT work anymore)<br>
<br>
<table><thead><th> <b>Version 1.3</b> </th><th> 19. 10. 2011 </th></thead><tbody></li></ul></li></ul></tbody></table>

<ul><li>Terrain blendmap from angles and height<br>
</li><li>Tracks info icons<br>
</li><li>Glass material fixed (now proper, not add)<br>
</li><li>Editor<br>
<ul><li>auto yaw angle (for road points)<br>
</li><li>new brush types: noise, set height<br>
</li><li>brush shapes (sinus, triangle, noise)<br>
</li><li>brush preview image<br>
</li></ul></li><li>Minimap circle (zoomed and rotated minimap)<br>
</li><li>Water (1st version)<br>
</li><li>New crash sounds and sparks<br>
</li><li>Graphics presets (low,med,high..)<br>
</li><li>Game controllers support<br>
</li><li>Checkpoint arrow (shows direction)<br>
</li><li>Improved motion blur<br>
<br>
<table><thead><th> <b>Version 1.2</b> </th><th> 31. 07. 2011 </th></thead><tbody></li></ul></tbody></table>

<ul><li>Replays<br>
</li><li>Ghost (best lap (or last) drive)<br>
</li><li>Split screen, for 2-4 players<br>
</li><li>Localization (translated to en,de,pl)<br>
</li><li>Keys rebinding, using oisb<br>
<br>
<table><thead><th> <b>Version 1.1.1</b> </th><th> 05. 04. 2011 </th></thead><tbody></li></ul></tbody></table>

<ul><li>bugfixes<br>
</li><li>optimized tree collisions</li></ul>

<table><thead><th> <b>Version 1.1</b> </th><th> 02. 04. 2011 </th></thead><tbody></tbody></table>

<ul><li>Linux (package for Ubuntu, sources compilable)<br>
</li><li>Using CMake (build system)<br>
</li><li>User config files (in user folder)<br>
</li><li>Tree collisions<br>
</li><li>Gui improvements<br>
</li><li>Effects (motion blur, bloom, hdr)<br>
</li><li>Screen tab (resolution)<br>
</li><li>New camera type (ext ang)</li></ul>

<br>