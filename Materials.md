

### Introduction ###

This page is for ver 2.3 and above it explains what to do when adding new content.

I.e. where to put your new data and which files need to be edited so it can appear and look good.

Since ver 2.3 editor uses config/presets.xml. Nothing new will appear in editor unless you add a line for it in that file.

It is quite simple, just copy a similar line and add it (keep it alphabetically sorted). Change the 3rd param to your resource name.

See comments inside presets.xml for (short) info on each param.

Later you can setup values for parameters, e.g. layer scaling or model size etc. that are set (by default) when picking (less manual setup needed).

Note, for release make sure that data dirs ending with `_`s have the new textures resized for small size.

### Skies ###

Sky textures are in data/skies.

Those are 360x90 degree spherical textures. One texture for whole skydome, size 4096x1024.

Materials are in data/materials/scene/sky.mat. Have to add new there, just copy last and replace texture for yours.

### Terrain ###

Textures for terrain layers are in data/terrain. See about.txt for sources.

They are all .jpg saved at about 97%. Size is 1024x1024.

Name endings mean:

`_`d - diffuse texture (main)

`_`s - specular amount (not color)<br>if not present, will be black (no specular)<br>
<br>
<code>_</code>n - normal map (needed, if not provided can be made with some tool)<br>You can use flat_n.png before real normalmap for quicker test.<br>
<br>
<code>_</code>h - height (optional, if none will be white)<br>this is only for parallax, and not used now, since it's broken<br>
<br>
Unlike other things, terrain has its own material so only adding to presets.xml is needed.<br>
<br>
<h3>Road</h3>

Road textures are in data/road.<br>
<br>
Materials in data/materials/scene/road.mat.<br>
<br>
When adding a new road material you need to add two materials e.g. roadJungle_ter and roadJungle. The one with <code>_</code>ter is for road on terrain, it has more bumps, and alpha border/texture. The other is for bridged roads and is more flat, can also use other textures.<br>
<br>
Also for editor adding a line in presets.xml is needed.<br>
<br>
Other road materials are in data/materials/scene/pipe.mat: road wall, pipe, pipe glass, pipe wall, column.<br>
<br>
<h3>Grass</h3>

Grass textures are in data/grass. They are transparent .png and mostly 512x512.<br>
<br>
Materials in data/materials/scene/grass.mat. Just copy a line and change texture name (and color if needed).<br>
<br>
Lastly adding a line in presets.xml is needed.<br>
<br>
<h3>Vegetation</h3>

Models (meshes) are in data/trees.<br>
<br>
Materials in data/materials/scene/trees.mat.<br>
<br>
<h3>Objects</h3>

Objects have their own wiki page, it also has more info on material editing (.mat files).