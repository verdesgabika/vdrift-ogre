Since version 1.7 static and dynamic objects can appear in game and can be inserted on tracks in editor.

Check also wiki [CreateObjects](CreateObjects.md), this here is a short list for developers.

#### Procedure of adding new objects ####

  1. download (must be GPL,CC-BY,CC0,etc.) or create a model in Blender
  1. once seen the model is ok, and can be useful:
    * create dir with a good\_name - to have some consistency, when picking model in editor, etc.
    * convert tga to png, obj to .blend
    * add readme.txt - a must: with original model name, author, license, url
    * possibly attach preview.jpg - so people may be interested in working with the model further
    * upload to blendfiles repo
  1. export from Blender to Ogre .mesh, check the look in game, remember scale
  1. bullet
    * if starting a new (dynamic) object watch this: [video](http://www.youtube.com/watch?v=fv-Oq5oe8Nw) and add that to logic, then pressing P twice should start physics and export .bullet file
    * for dynamic objects: add simple physics shape(s), make actor (rigid body)
    * on material tab under Physics set friction
    * on physics tab set mass, damping (linear and angular, check in game)
    * don't forget to set the Margin to eg. 0.1 under collision bounds
    * remember to reset all transforms (Ctrl A) before exports
    * for static models: if too high poly create 1 simple mesh for it
    * if low poly (like 0AD) do nothing, will have trimesh made in code
  1. done (be happy, suggest adding it to some tracks, or make a new with it, use other too)