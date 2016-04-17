## Introduction ##



<br>
<hr />
<h3>Modeling</h3>
To model a car from start requires weeks of work and good knowledge of modeling techniques and how to do it.<br>
<br>
Modifying an existing car (e.g. extending its quality) is much easier.<br>
<br>
<h3>Model websites</h3>
There are already pretty good car models, available on <a href='http://blendswap.com'>blendswap</a>.<br>
<br>
See our forum topic, <a href='http://forum.freegamedev.net/viewtopic.php?f=80&t=5593'>this post</a> shows the list of cars.<br>
<br>
Some are too high poly or too low. And some just don't fit the game.<br>
<br>
The license for the art must be GPL, CC-BY-SA, CC-BY, CC0, etc so we could use it.<br>
<br>
They still require some work (to have in game):<br>
<ul><li>Lowering polygon count. No subdivisions. Decimate if necessary.<br>
</li><li>UV unwrap and mapping various car parts to texture parts.<br>
</li><li>Making interior (if not present). Texturing.</li></ul>

<h3>Blender</h3>
We are using and recommend <a href='http://www.blender.org/'>Blender</a> to do all of the modeling tasks.<br>
<br>
At least basic knowledge of Blender is required.<br>
<br>
There are several good resources on internet to learn it.<br>
<ul><li>Best way to start is to read <a href='http://wiki.blender.org/index.php/Doc:2.6/Manual'>Blender Manual</a>. <br>Only few chapters are useful, Introduction, Modeling, and Texturing/Unwrapping.<br>
</li><li><a href='http://wiki.blender.org/index.php/Doc:2.6/Tutorials'>Blender Tutorials</a>
</li><li>Basically any common task in Blender is shown on some video (eg. search youtube). <br>Keep in mind the version used should be close to yours and recent (now Blender 2.66).<br>
</li><li>There are also video tutorials specifically on car modeling.<br>
</li><li>Also various websites with Blender key shorcuts: <a href='http://www.katsbits.com/tutorials/blender/useful-keyboard-shortcuts.php'>katsbits</a>, <a href='http://blendertips.com/hotkeys.html'>blendertips</a>, <a href='http://www.keyxl.com/aaac91e/403/Blender-keyboard-shortcuts.htm'>keyxl</a>.</li></ul>

<br>
<hr />
<h2>Model requirements</h2>

Things to keep in mind when modeling (required by game):<br>
<br>
<h3>Triangles count</h3>
Keep resonable triangles count (faces, polygons). You can see it in top bar in Blender.<br>
<br>
For good looking car, total of 50 000 triangles would be required, let's say up to 80 000.<br>
<br>
One wheel (including brake disc and caliper) should be about 4 000 triangles.<br>
<br>
See <a href='http://code.google.com/p/vdrift-ogre/wiki/CarModeling#Example'>Example</a> at bottom of page and <a href='http://code.google.com/p/vdrift-ogre/wiki/CarModeling#Comments'>Comments</a> for more info.<br>
<br>
More detail can (and should) be put in textures. More triangles will unnecessary reduce game Fps.<br>
<br>
<h4>Baking Normal Map (Advanced)</h4>
Also Normal map and Ambient Occlusion map can be baked in Blender.<br>
<br>
This is usually difficult and time consuming. Normalmap is generated from high poly model.<br>
<br>
Ambient occlusion is easier and gives good feeling.<br>
<br>
<h3>Detail</h3>
Make as much detail as possible, but check out other cars.<br>
<br>
ES car is the best here, it has a lot of detail, but some of it is baked in normal map.<br>
<br>
To check geometry (triangles) just start game and press F10 to toggle wireframe.<br>
<br>
Since version 2.0 game logs car meshes info in ogre.log (how to find it in <a href='Paths.md'>Paths</a> wiki).<br>
<br>
Look for "MESH info: " it says how many submeshes (subs, materials) and how many triangles (tris) each part has and the total amounts.<br>
<br>
ES car is best because it only has 1 submesh and 1 material in each .mesh file. This is most optimal and preferred.<br>
<br>
<h4>Normals</h4>
Keep in mind that faces in blender can be two sided, but in game are one sided.<br>
<br>
Thus the face normals (in blender) must be flipped to proper side. They won't be visible in game if on the other side.<br>
<br>
<h4>Data Size</h4>
Cars (just like tracks) aren't big in size.<br>
<br>
ES is biggest and after export the Ogre, all .mesh files are about 1MB, and all textures 5MB.<br>
<br>
It's best to keep the size not higher than that.<br>
<br>
<h4>Repositories</h4>
We have git repository with .blend files of some cars<br>
<br>
<a href='https://github.com/stuntrally/blendfiles/tree/master/cars'>https://github.com/stuntrally/blendfiles/tree/master/cars</a>

The best and most complicated is ES, it has high poly model and baking normalmap and ambient occlusion was done for it.<br>
<br>
S8 and XZ are good, they have a simple unwrap and interior.<br>
<br>
<br>
<hr />
<h2>Parts (in Blender)</h2>
Note: replace ES with the in-game car name you work with.<br>
<br>
Name the body parts (and the geometries): ES_body, ES_interior, ES_glass.<br>
<br>
If you have a wheel then use: ES_wheel. ES_brake for brake disc and caliper (not necessary).<br>
<br>
Car gets exported to such meshes:<br>
<ul><li>ES_body - this is car body, only 1 material, covering the metal parts that will be colored in game using car color. Don't include any geometry here that doesn't have car paint on it in Blender.<br>
</li><li>ES_glass - this is car glass (windows) and also can have front or rear lights glass (makes lights look better).<br>
</li><li>ES_interior - has not only interior (seats and all inside car stuff) but also front/rear lights, exhaust pipe, car bottom, rubber (dark) parts between car metail and so on. Simply all model parts that don't get colored by car paint.<br>
</li><li>ES_wheel - car wheel rim (metal) and car tire, may also have brake disc. It is best to use 1 material, and put parts in in different places (UV) of texture.<br>
</li><li>ES_brake - (optional)</li></ul>

This makes the exported files already named properly for game, so just copying there works.<br>
<br>
<i>(We use such short names, simply because it is not possible to use original car names).</i>

This Blender screenshot shows (for XZ car):<br>
<ol><li>3D view of interior faces<br>
</li><li>joined geometry parts with good names<br>
</li><li>material names, still too many<br>
</li><li>UV editor with unwrapped faces to texture <br>(note this is a work in progress, only interior and car bottom are mapped properly, rest is moslty garbage, not done yet)</li></ol>

<img src='http://vdrift-ogre.googlecode.com/files/blenderXZ.png' />

A finished interior with good UV map would look similar to this (for ES car):<br>
<br>
<img src='http://vdrift-ogre.googlecode.com/files/ble-evo-int.png' />

Exporting models from Blender to Ogre (see <a href='CreateObjects#Preparations.md'>Objects</a> Wiki on how to install exporter) is done from menu File|Export|Ogre3D.<br>
<br>
From the exporter options pick axes as "xz-y", use tangents (mark checked), uncheck edges-list (we don't need them).<br>
<br>
<img src='http://vdrift-ogre.googlecode.com/files/ogre-exp.png' />

If succesfull, you will find files in the selected folder (1 mesh file in xml format and 1 binary mesh fie) for each selected geometry in blender.<br>
<br>
Copy the binary .mesh files (parts) into the data/cars/ES dir in Stuntrally (replacing the older/original ones).<br>
<br>
Start Stuntrally and check how it looks.<br>
<br>
<h3>Materials</h3>

Name all materials in Blender with car prefix, e.g. ES_body, ES_glass, ES_interior, ES_wheel, etc.<br>
<br>
Keep the material count at minimum. This is crucial.<br>
<br>
We can't have each car part like front/rear lamps, seats, steering wheel etc as separate parts, they must be on 1 mesh (geometry) and have UV mapped to different parts of texture.<br>
<br>
It is best to have each body part with 1 material, with the same name as geometry (ES_interior, ES_glass etc).<br>
<br>
<i>(Each material represents new batch (draw call) and parameter changes which reduces game Fps).</i>

So, join (Ctrl-J) all geometry in interior. Mark seams on edges that will get cut. Unwrap (U) parts.<br>
<br>
Use UV editor to move and scale parts to according places on texture. Don't make parts overlap on texture.<br>
<br>
Use bigger scale for parts that require more texturing (detail).<br>
<br>
In game we can use:<br>
<ul><li>diffuse map - to add texture to objects, change color, etc. This is required, but it can be simple 1 color at start.<br>
</li><li>specular map - if parts have different shininess (color in rgb and power in alpha), e.g. this is obvious for wheel rim (shiny) and tire (matte), still can be on 1 texture which is more optimal (more Fps).<br>
</li><li>reflection map - to mark shiny parts with environment reflection (eg. glass, rim), or deny reflections (tire)</li></ul>

<br />
<hr />
<h2>Data (in game)</h2>

Desired file structure in data/cars/3S (for already exported car).<br>
<br>
<h4>main dir, meshes</h4>
3S_body.mesh<br>
<br>
3S_interior.mesh<br>
<br>
3S_interior.mesh<br>
<br>
3S_wheel.mesh<br>
<br>
3S_brake.mesh<br>
<br>
Those files were already described.<br>
<br>
<h4>main dir, other files</h4>
about.txt - Contains info of the model, credits, changes.<br>
<br>
description.txt - This text file contains the info text which is displayed in game. It has general info about the car and how it handles in game.<br>
<br>
engine.wav - The engine sound file (at 7000 rpm). Must be wav and 44100 Hz, mono or stereo 16-bit.<br>
<br>
<h4>in textures/ subdir</h4>

3S_body00_red.png - Main body texture. It has to be colored in saturated red, because it will change depending on car paint chosen in game. Can just be whole red texture at start of car creation.<br>
<br>
3S_body00_add.png - Old version cars used this to add detail to red texture. Can be full transparent at start.<br>
<br>
3S_body00_brake.png - Same as add but with rear brakes lit. The texture add is replaced to brake when car brake is on.<br>
<br>
3S_interior.png - interior texture (with various car parts mapped too) possibly with 3S_interior_normal.jpg.<br>
<br>
3S_glass.png - the transparent glass texture (usually small)<br>
<br>
optional: 3S_spec.png, 3S_refl.png - to map specular parts and reflection, or deny them on matte parts.<br>
<br>
3S_Tire.png, 3S_Tire_norm.png - diffuse and normal texture for tire model<br>
<br>
<h3>Materials file</h3>
Materials for all cars are defined in data/materials/cars.mat<br>
<br>
<i>(thanks to shiny material generator its syntax is simple while materials are powerful)</i>

A very basic example for 3S, you can comment out lines with //.<br>
<pre><code>material car_body_3S<br>
{<br>
	parent car_body<br>
	specMap 3S_spec.png<br>
}<br>
<br>
material 3S_glass<br>
{<br>
	parent car_glass2<br>
	diffuseMap 3S_glass.png<br>
}<br>
material 3S_interior<br>
{<br>
	parent car_interior<br>
	diffuseMap 3S_interior.png<br>
}<br>
material 3S_wheel<br>
{<br>
	parent car_wheel<br>
	diffuseMap 3S_wheel.png<br>
}<br>
</code></pre>

More complicated example for ES wheel<br>
<pre><code>material ES_wheel<br>
{<br>
	parent car_wheel<br>
	diffuseMap ES_wheel.png<br>
	normalMap ES_wheel_normal.jpg<br>
	specMap ES_wheel_spec.png<br>
	reflMap ES_wheel_spec.png<br>
}<br>
</code></pre>

Another for XZ wheel<br>
<pre><code>material XZ_wheel_chrome  // rim<br>
{<br>
	parent car_base<br>
	diffuseMap XZ_Tire.png<br>
	ambient 0.1 0.1 0.1<br>
	diffuse 0.1 0.1 0.1<br>
	specular 1 1 1 4<br>
	env_map true<br>
	fresnel true<br>
	fresnelScaleBiasPower 0.6 0.15 4<br>
}<br>
</code></pre>

<br>
<hr />
<h2>Example</h2>
Car XZ in game<br>
<br>
<img src='http://vdrift-ogre.googlecode.com/files/viewXZ.jpg' />

XZ wireframe<br>
<br>
<img src='http://vdrift-ogre.googlecode.com/files/viewXZwire.jpg' />

<br>
<hr />
<h3>Comments</h3>
No car is perfect, and every one has some smaller or bigger issues.<br>
<br>
I describe here what could be done to improve those cars. They were released in version 2.0 (with those issues).<br>
<br>
BTW. We are looking for artists who could improve cars (use IRC or Forum to contact us if you want to help).<br>
<br>
The ALL (total) counts are computed as sum of body, interior, glass and 4 times wheel and brake.<br>
<br>
<h4>ES</h4>
As mentioned few times this car is nearly perfect. It has also taken a lot of time to do, and to transform all the detail from high poly version to low poly with details placed on textures, and baked maps.<br>
<br>
The dashboard is so good it could actually be used for in car camera view. This is the only car that can be driven so, rest is not done at all.<br>
<br>
Only thing to improve would be to reduce the interior faces count (tri), since its 2x more than body and you mostly see body in game.<br>
<br>
Also, since normal map was baked, it introduced a distortion, seen on body, from close. It is not so smooth as without it, and those are errors from baking. Thus I don't recommend normalmap baking, just ambient occlusion.<br>
<br>
Brake.mesh tri count is also too high.<br>
<br>
You can see the lines in wireframe are quite dense.<br>
<br>
<pre><code>ES_body.mesh	 sub: 1  tri: 19.0k<br>
ES_interior.mesh sub: 1  tri: 38.0k<br>
ES_glass.mesh	 sub: 1  tri:  1.0k<br>
ES_wheel.mesh	 sub: 1  tri:  4.1k<br>
ES_brake.mesh	 sub: 1  tri:  3.1k<br>
ES	 ALL sub: 11  tri: 86.9k<br>
</code></pre>
<img src='http://vdrift-ogre.googlecode.com/files/wireES.jpg' />

<h4>S1</h4>
S1 has very good textured interior, with very low tri count and still looks good. In car camera view is ok.<br>
<br>
But it has far too many submeshes (sub) on body, interior and wheel. This needs to be reduced, and all parts merged to 1 uv space, and textures combined to 1.<br>
<br>
As you can see on wireframe body and interior lines show low poly count.<br>
<br>
<pre><code>S1_body.mesh	 sub: 4  tri: 12.0k<br>
S1_interior.mesh sub: 12 tri:  8.6k<br>
S1_glass.mesh	 sub: 1  tri:  0.5k<br>
S1_wheel.mesh	 sub: 3  tri:  3.9k<br>
S1_brake.mesh	 sub: 1  tri:  3.1k<br>
S1	 ALL sub: 33  tri: 49.4k<br>
</code></pre>
<img src='http://vdrift-ogre.googlecode.com/files/wireS1.jpg' />

<h4>S8</h4>
S8 has extremely high sub and tri counts (far too many faces). It needs all interior parts merged into 1 mesh and 1 material and uv unwrap (Done).<br>
<br>
Also some triangle reduction is necessary (at least by half), be sure there is no Subdivision applied, and use Decimation modifier if necessary.<br>
<br>
<pre><code>S8_body.mesh	 sub: 1  tri: 43.0k<br>
S8_interior.mesh sub: 16 tri: 82.0k<br>
S8_glass.mesh	 sub: 3  tri: 16.8k<br>
S8_wheel.mesh	 sub: 2  tri:  3.9k<br>
S8_brake.mesh	 sub: 1  tri:  3.1k<br>
S8	 ALL sub: 32  tri: 169.9k<br>
</code></pre>
<img src='http://vdrift-ogre.googlecode.com/files/wireS8.jpg' />

<h4>XZ</h4>
This car has very smooth body with good tri count.<br>
<br>
Interior was made by me and thus is rather poor. I copied seats from S8, and made the rest of interior by extruding 1 line and adjusting it. It has also poor texturing there.<br>
<br>
But still it's an interior and better than none (the original model didn't have it).<br>
<br>
Next thing is that the body has holes. They are visible from close. It is needed to add triangles to interior which would be dark and would cover those holes.<br>
<br>
Also ALL sub count is much too high, mostly because of wheel and brake not having 1 submesh, and also interior not merged. Next, wheel rim has too many faces (about 2x more) but I left it so since decimation can produce unwanted distortion to mesh.<br>
<br>
<pre><code>XZ_body.mesh	 sub: 2  tri: 22.0k<br>
XZ_interior.mesh sub: 6  tri: 19.6k<br>
XZ_glass.mesh	 sub: 1  tri:  1.0k<br>
XZ_wheel.mesh	 sub: 3  tri: 11.4k<br>
XZ_brake.mesh	 sub: 2  tri:  0.7k<br>
XZ	 ALL sub: 29  tri: 91.3k<br>
</code></pre>
<img src='http://vdrift-ogre.googlecode.com/files/wireXZ.jpg' />

Like with many cars, roof and door frames are gone, when seen from car outside (or from down left to upper part of car). Need to add more interior faces there. Shown here:<br>
<br>
This happens because faces are 1 sided in game. When adding the second, interior faces, keep high distance, because if it is too low shadows are blinking on those parts.<br>
<br>
<img src='http://vdrift-ogre.googlecode.com/files/XZ-roof.jpg' />