

## Introduction ##
This page walks you through the steps to create new static objects and to add them to Stuntrally.

_WARNING_: The learning curve for Blender is quite steep, you need to invest a serious amount of time to learn and use it efficiently. Fortunately there are plenty of tutorials, websites and books to pick up the skills.

Currently static and dynamic objects are stored in the **\data\objects** folder in the folder you choosed to install Stuntrally. It contains Ogre mesh files (binary), surface images (textures) and bullet files for the dynamic objects.

![http://vdrift-ogre.googlecode.com/files/img20121230_1.png](http://vdrift-ogre.googlecode.com/files/img20121230_1.png)

<br>
<h2>Tutorial 1</h2>

<h3>Requirements</h3>
<ul><li>Blender 2.6 + (current version is 2.65 as of December 2012)<br>Download it from <a href='http://www.blender.org/download/get-blender/'>http://www.blender.org/download/get-blender/</a></li></ul>

<h3>Preparations</h3>

<ul><li>Blender comes with plenty of import and export plugins, but the ogre export plugin we need to download separately.<br>Download the latest <b>blender2ogre</b> plugin from <a href='http://code.google.com/p/blender2ogre/downloads/list'>http://code.google.com/p/blender2ogre/downloads/list</a> (currently version 0.5.9) and unzip the file python file.</li></ul>

<ul><li>Install the plugin in Blender<br>Open preferences (menu|file), Add-Ons, Install from file.<br><img src='http://vdrift-ogre.googlecode.com/files/img20121230_3.png' /><br><img src='http://vdrift-ogre.googlecode.com/files/img20121230_2.png' /></li></ul>

<ul><li>Install the Ogre Command Line tools.<br>Windows: Download it from <a href='http://www.ogre3d.org/download/tools'>http://www.ogre3d.org/download/tools</a> and unzip it to the default folder (C:\OgreCommandLineTools)<br>Linux: Should be included with your Ogre package. On Ubuntu, it is included in the ogre-1.9-tools package. The binary we are looking for is "OgreXMLConverter", so try running that to see whether you have it installed.</li></ul>

<br>

<h3>Create a simple <b>static</b> object</h3>
<ul><li>For testing purpose we just export a Blender default object (the box, or maybe the monkey)<br><img src='http://vdrift-ogre.googlecode.com/files/img20121230_4.png' />
</li><li>Export to mesh (File|export|Ogre3D)<br>If succesfull, you will find 2 files in the selected folder (1 mesh file in xml format and 1 binary mesh fie)<br>From the exporter options pick axes as "xz-y", use tangents (mark checked), uncheck edges-list (we don't need them).<br>
</li><li><b>Copy the binary mesh</b> into the objects folder of Stuntrally<br>
</li><li>Start <b>Stuntrally Editor</b> and place the object.<br><img src='http://vdrift-ogre.googlecode.com/files/img20121230_5.png' />.<br><img src='http://vdrift-ogre.googlecode.com/files/img20121230_6.png' /><br>Works ! Now we have Suzanne (the monkey) in our track. <br>Not much interaction, other than you can collide with the object, but it will not move. Thats why we continue to create a dynamic object, by creating a binary bullet file containing all necessary physical information.</li></ul>

<br>

<h3>Create a <b>dynamic</b> object</h3>

Blender can export the dynamics of an object (to be more exact of the whole world in your blender project) to binary dump. This part of the tutorial will walk through the necessary steps.<br>
<br>
<ul><li>Start Blender, we can continue with the previous test object.<br>
</li><li>Change to the Game Mode<br><img src='http://vdrift-ogre.googlecode.com/files/img20121231_9.png' />
</li><li>Open the Blender text editor<br><img src='http://vdrift-ogre.googlecode.com/files/img20121231_11.png' /><br> and enter this code<br>
<pre><code>import PhysicsConstraints;<br>
PhysicsConstraints.exportBulletFile("object.bullet")<br>
</code></pre>
</li><li>Save it as <i>bulletexp</i><br><img src='http://vdrift-ogre.googlecode.com/files/img20121231_13.png' /></li></ul>

<ul><li>You cannot execute the script from here, we need to do this via the running game engine.<br>Open a logic editor window<br><img src='http://vdrift-ogre.googlecode.com/files/img20121231_15.png' /><br>Select the cube object in the 3D view. Add a sensor for keyboard input ("p" key) and connect it to a controller to execute our script from above <br><img src='http://vdrift-ogre.googlecode.com/files/img20121231_14.png' /></li></ul>

<ul><li>Open the physics attributes for our object and do the following settings<br>Physics Type: dynamic<br>Actor<br>Collision bounds box<br><img src='http://vdrift-ogre.googlecode.com/files/img20121231_16.png' /></li></ul>

<ul><li>Click into the 3D window and start the engine by pressing "p"<br>For a short moment you will see the object falling down.Press "p" again (for our keyboard sensor).</li></ul>

<ul><li>The script creates an object.bullet file in the blender folder<br><img src='http://vdrift-ogre.googlecode.com/files/img20121231_18.png' /></li></ul>

<ul><li>Copy the file to the same object folder as our meshfile, it must have the same filename as the mesh file (eg. object.mesh and object.bullet)</li></ul>

<ul><li>Start the editor, place the object. Press "C" to simulate physics, if OK check out your track.</li></ul>

<h4>Remarks on objects</h4>
Keep it low poly and use only 1 material if possible.<br>
I depends on how many times an object will be on track.<br>
<br>
Example, triangle counts for various objects:<br>
<table><thead><th> 300 </th><th> small rock </th></thead><tbody>
<tr><td> 600 </td><td> fern, plant </td></tr>
<tr><td> 1k  </td><td> small tree, rock, barrel etc </td></tr>
<tr><td> 3k  </td><td> big tree (less on track) </td></tr>
<tr><td> 10k </td><td> static object, eg. temple, that won't be many times </td></tr>
<tr><td> 50k </td><td> a detailed object, meant to be once on a track<br>(eg. inside of pyramid, or spaceship, etc.) </td></tr></tbody></table>

Generally, using a Higher graphics preset, triangle count should be up to 800k and batch count up to 300 (max 500), having 2 cars, vegetation, terrain visible, in a view position that covers over half of the track.<br>
<br>
<br>
<h2>Tutorial 2</h2>

<h3>Create new objects</h3>
Creating a new objects from the scratch with Blender requires at least basic Blender skills.<br>
<ul><li>Stick to low poly meshes and dont get templted to download an objects with thousands of vertexes, it will pull down the framerate.</li></ul>

<h3>Use objects from other websites</h3>
Download from one of the model web portals like <a href='http://opengameart.org/'>http://opengameart.org/</a> or <a href='http://www.blendswap.com/'>http://www.blendswap.com/</a>
<ul><li>Important: Check the license under which the objects are released (at least if you plan to submit the object to become part of Stuntrally distributable), preferrably CC0, CC-BY, GPL or similar</li></ul>

<h3>Materials</h3>
It is needed to name materials in blender with some prefix (e.g. from your object) so that all material names are unique in game.<br>
Then knowing your material names, it's needed to add them in .mat.<br>
For static objects edit file data/materials/objects_static.mat or objects_dynamic.mat if your object is dynamic (has .bullet file and can move).<br>
<br>
The simplest material is white, not that diffuseMap parameter must be present.<br>
<pre><code>material my_new_object<br>
{<br>
	parent base<br>
	diffuseMap white.png<br>
}<br>
</code></pre>

The syntax is quite simple and powerful. It allows using all implemented material features with few lines.<br>
<pre><code>material my_new_object<br>
{<br>
	parent base<br>
	diffuseMap pers_struct.dds<br>
	normalMap pers_struct_norm.png<br>
	ambient 0.9 0.9 0.9<br>
	diffuse 1.0 1.0 1.0<br>
	specular 0.4 0.4 0.3 6<br>
	terrain_light_map true<br>
	bump_scale 1.3<br>
}<br>
</code></pre>
Your texture file name should be after diffuseMap. This file should also be copied to data/objects (same place where .mesh and .bullet).<br>
<br>
Use ambient, diffuse and specular for colors of different lighting, all have Red,Green,Blue values. Ambient is constant (this is what you see when objects is in shadow). Diffuse depends on light direction (only the lit side). And specular also has a power exponent, the 4th value, after R,G,B. Small values e.g. 4 make matte-like surfaces, where high e.g. 64 make it quite shiny.<br>
<br>
Comments are made with //. So if you don't want to use a line you can either delete it or add // in front.<br>
<br>
If you have a normalMap use it in material (remember to have tangents generated during export). Normal map could be either already provided, or you can generate it using GIMP normal map plugin.<br>
The last parameter bump_scale can be used to scale normal map's effect. Default value is 1.0. More will make it bumpier.<br>
<br>
You can use own texture for specular in specMap.<br>
It's either RGBA and alpha is the exponent. But that is tedious to edit everytime.<br>
To use only RGB add line specMap_rgb true, then specMap can also be jpg and exponent is in alpha of specular color like usual.