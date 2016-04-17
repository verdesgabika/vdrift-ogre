

<br>
<h1>Pre-built dependencies</h1>

<blockquote><i>Since May 2014, a happening occurred that changed the..</i><br>
Ugh nope, scratch that..<i></blockquote></i>

<h2>Warning</h2>

<i>This way is very new and tested only by me (tell us on IRC if it worked).</i><br>

There is a risk that this won't work, but if it will,<br>
it can save you <b>A LOT</b> of time, or simply make this even possible.<br>

<blockquote><i>Note: I'm not a fan of this way, since you learn nothing by this and is quite risky.</i><br>
But it surely is the quickest way to jump-start developing SR on Windows.<br>
PS. You still can do it faster and safer on Ubuntu.<i></blockquote></i>

<h2>Intro</h2>

The pre-built dependencies have been built using Visual Studio 2010 Express (is with SP1),<br>
and can work <b>only</b> for that version.<br>
<br>
It is an archive with all compiled libraries needed to build SR.<br>

<blockquote>Simply a result of all, that has been done here below (in the compiling dependencies, nightmare section).<br>
The minimal version of it, that should be enough, to unpack<br>
and let building SR using the same VS (both Debug and Release possible).</blockquote>

<h2>How to use</h2>

I will be referring here to paragraphs from below, since they are already described there.<br>
<br>
Firstly you need to install VS 2010 Express, <a href='CompilingOnWindows#Visual_Studio_C++_2010_Express.md'>read here</a>.<br>
<br>
Then download, the archive (<code>SR_deps_VS10exp.7z</code>) from <a href='http://sourceforge.net/projects/stuntrally/files/2.3/SR_deps_VS10exp.7z/download'>here</a>.<br>
<br>
To unpack it, use <a href='http://www.7-zip.org/download.html'>7-zip</a> or any decent File Commander that can.<br>
<br>
Fastest way would be to unpack in <code>e:\v</code>, but you may not have <code>e:</code>,<br>
it is also possible to use it from other dir.<br>
<br>
<blockquote><i>The archive itself has only dependency headers, their built libs, and .dll files in <code>stuntrally\proj</code>.</i><br>
Also in <code>proj</code> there are build exe's (could be tested after you clone repos).<br>
And lastly I included all from mygui/bin/bin/release, but would need MyGui data to start it.</blockquote>

No dependencies are needed, all are there (Boost, Bullet, Ogg, Vorbis, MyGui, Ogre, SDL2).<br>
<br>
Next, you need to download (clone) the SR repositories, read <a href='CompilingOnWindows#Get_Sources.md'>Get Sources</a>.<br>
<i>If clone won't work when it sees already the stuntrally dir which came from archive just rename it.</i><br>
Clone both stuntrally and tracks, <code>tracks</code> dir should be inside <code>stuntrally\data</code>.<br>
Copy contents from archive's <code>stuntrally\proj</code>, to your <code>stuntrally\proj</code> dir, the one you got from Git repo.<br>

Now, if you don't use <code>e:\v</code> you need to replace all occurrences of that to your path.<br>
I recommend just taking a text editor and using <i>replace all</i> in files StuntRally1.vcxproj and SR_Editor1.vcxproj.<br>
Is really the fastest way.<br>

<i>Note: the archive's vcx projects (with 1 in name) will soon be outdated (not having some new cpp files in etc.)</i><br>
<i>If so, use the original VS 2008 files from repo (without 1 in name), read <a href='CompilingOnWindows#Projects.md'>Projects</a> on how to setup them.</i>

Go inside stuntrally\proj and open solution StuntRally.sln or SR_Editor.sln (or the ones with 1 in name).<br>
<br>
Since Output dir isn't saved in project, clear it, as shown here: <a href='CompilingOnWindows#Output_dir.md'>Output dir</a>.<br>
Build the project.<br>
Needed .dll files to run are already there so build should start.<br>
<br>
<b>THE END</b>

<br>
<hr />
<h1>Compiling Dependencies</h1>
<hr />

<br>
<h2>Warning</h2>

If you do build on Windows and already have experience with this you can skip this paragraph.<br>
Also if you don't like my comments or want to do this really fast, <i>avoid text in italic</i>.<br>
<blockquote><i>Especially formatted like this.</i></blockquote>

<br>
This page provides a detailed description that could guide you through the <i>nightmare</i> process of building on <a href='http://en.windows7sins.org/'>Windows</a>.<br>
<br>
It is considered difficult and tedious, <i>annoying and stupid too</i>.<br>
<br>
<blockquote><i>If you have never build any medium size, Linux projects and libraries on Windows, you should probably leave this page now.</i><br> Instead see <a href='http://code.google.com/p/vdrift-ogre/wiki/Compiling'>building on Ubuntu</a>.<i></blockquote></i>

<blockquote><i>Seriously, I believe it is easier and quicker to install Ubuntu and build SR there. If you just want to build SR for fun, and you aren't too old to switch to a better OS. You could learn a new OS by the way and save yourself this nightmare.</i></blockquote>

I only recommend reading this page if you e.g. want to learn how to deal with the <i>idiotic</i> process of building something from sources on Windows, with many dependencies. <i>Or if you build on Linux and want to have a good laugh.</i>

Taking a week of holiday will be useful to complete this (or 2 days if you did this already few times).<br>
<i>Also needed: a metric f<code>**</code>kton of patience. Still, it is said that Chuck Norris has built SR within 3 hours.</i>

Lastly, it is likely that you will have errors / issues, not mentioned here,<br>
I recommend just putting them in <a href='http://www.stackoverflow.com'>stackoverflow</a> or <a href='http://www.google.com'>google</a> search.<br>
<br>
<br>
<br>
<h2>Introduction</h2>

Stunt Rally and SR Editor are 32-bit applications. <i>Don't even try building with 64-bit compilers.</i>

I build on Windows 7 64-bit <i>(with Visual Studio 2008 because it builds really fast,</i><br> so fast that next versions are even unusable at <a href='http://yosoygames.com.ar/wp/2013/12/microsoft-we-need-to-talk-about-visual-studio/'>developing games</a>)<i>.</i><br>
This page shows how to do it with VS 2010 Express. VS 2012 works too.<br>

Using <a href='http://www.fsf.org/windows8'>Windows 8</a> or VS 2013 wasn't tested <i>(and I don't know if those work, tell us if you tried)</i>.<br>
<i>Possibly could fail with some new stupid issue wasting another day of your life.</i>


<hr />
<br>
<h2>Software Requirements</h2>

<h3>Visual Studio C++ 2010 Express</h3>
Express versions are available for free (as in free beer) here: <a href='http://www.visualstudio.com/en-us/downloads/download-visual-studio-vs#DownloadFamilies_4'>link</a>.<br>
<i>? It must be registered (free) with MS otherwise it only works for a 30 days trial-period.</i>

Install doesn't need SQL Server or Silverlight.<br>

<img src='http://wiki.vdrift-ogre.googlecode.com/git/vs/02vs10.png' />

<h3>Client for Git</h3>
To download the SR sources from repository you can get the client <a href='http://git-scm.com/downloads'>here</a>,<br>
which comes with a simple GUI and integrates with the Windows File Explorer.<br>

<i>That should do the task, but you can also use <a href='http://code.google.com/p/tortoisegit/wiki/Download'>TortoiseGit</a> or <a href='https://github.com/gitextensions/gitextensions/releases'>GitExtensions</a>, it's up to you.</i><br>
<i>If you really don't want to quickly update it later, you can download an archive <a href='https://github.com/stuntrally/stuntrally/tags'>here</a> and tracks <a href='https://github.com/stuntrally/tracks/tags'>here</a>.</i>


<h3>CMake</h3>
We need CMake to create the project and solution files for <code>MyGui</code> library (also can be used for few other).<br>
Download from <a href='http://www.cmake.org/'>http://www.cmake.org/</a>

<blockquote>CMake is the best approach, since it is a layer above project files, it can be used to generate them for various IDEs.<br>
It is used to build SR on Linux, and also could be used for SR projects, but currently that is broken.<br>
When having trouble with paths, I recommend to add/modify them in CMake, not in Visual Studio.<br>
Every time you use CMake your edits to vs projects are destroyed.<br>
So Keep in mind if you do alter something in vs proj, don't use CMake after (or make a copy and merge/edit vcproj by hand).<br>
Also CMake Gui is much more convenient (can be all done with keyboard) than VS stupid dialogs <i>(that remember the times of '95 and are resizable only since 2013 but at the cost of broken colors).</i>
<hr /></blockquote>


<br>
<h2>Dependencies</h2>

Since I document here the quickest way possible,<br>we will use pre-built packages (archives) for Boost, SDL, and Ogre (with Ogre dependencies),<br>rest has to be build from sources.<br>
<blockquote><i>I personally always build everything from sources (lately except boost), since this is the only way to have full debug (in dependencies too), and is much safer to release. But that is the slowest way of all.</i></blockquote>

<blockquote>Note: SR needs specific version of Bullet library.<br>
We will also use Boost 1.55 (this version is in Ogre 1.9 SDK, so to minimize possible complications and damage).<br>
Otherwise newer versions can be used, but aren't needed.<br>
<i>If you build everything from sources and like to live dangerously, you can try latest development versions.</i><br></blockquote>

I recommend to install/unpack all dependencies to a common folder.<br>
On this wiki and its images it will appear as <code>e:\v</code>. <i>(Why? because it's much faster when you have to input it 50 times by hand.)</i><br>

<br>
Now, download those by clicking on all Links.<br>
If the Download Link doesn't work use Downloads and pick version, if even that is broken visit Website and find downloads.<br>
<br>
<table><thead><th> <b>Library</b> </th><th> Version used </th><th> Website </th><th> Downloads </th><th> <b>Download Link</b> </th></thead><tbody>
<tr><td> Ogre           </td><td> 1.9<sup>*</sup> </td><td> <a href='http://www.ogre3d.org'>http://www.ogre3d.org</a> </td><td> <a href='http://www.ogre3d.org/download/sdk'>Downloads</a> </td><td> <a href='http://sourceforge.net/projects/ogre/files/ogre/1.9/1.9/OgreSDK_vc10_v1-9-0.exe/download'>Link</a> </td></tr>
<tr><td> Bullet         </td><td> 2.79<sup>*</sup> </td><td> <a href='http://bulletphysics.org'>http://bulletphysics.org</a> </td><td> <a href='https://code.google.com/p/bullet/downloads/list'>Downloads</a> </td><td> <a href='http://code.google.com/p/bullet/downloads/detail?name=bullet-2.79-rev2440.zip&can=4&q='>Link</a> </td></tr>
<tr><td> MyGui          </td><td> 3.2          </td><td> <a href='http://mygui.info'>http://mygui.info</a> </td><td> <a href='http://www.sourceforge.net/p/my-gui/code/HEAD/tree/'>Downloads</a> </td><td> <a href='http://sourceforge.net/p/my-gui/code/HEAD/tarball'>Link</a> </td></tr>
<tr><td> SDL2           </td><td> 2.0.3        </td><td> <a href='http://www.libsdl.org'>http://www.libsdl.org</a> </td><td> <a href='http://www.libsdl.org/download-2.0.php'>Downloads</a> </td><td> <a href='http://www.libsdl.org/release/SDL2-devel-2.0.3-VC.zip'>Link</a> </td></tr>
<tr><td> Boost          </td><td> 1.55<sup>*</sup> </td><td> <a href='http://www.boost.org'>http://www.boost.org</a> </td><td> <a href='https://sourceforge.net/projects/boost/files/boost-binaries/'>Downloads</a> </td><td> <a href='http://sourceforge.net/projects/boost/files/boost-binaries/1.55.0-build2/boost_1_55_0-msvc-10.0-32.exe/download'>Link</a> </td></tr>
<tr><td> Enet           </td><td> 1.3.12       </td><td> <a href='http://enet.bespin.org'>http://enet.bespin.org</a> </td><td> <a href='http://enet.bespin.org/SourceDistro.html'>Downloads</a> </td><td> <a href='http://enet.bespin.org/download/enet-1.3.12.tar.gz'>Link</a></td></tr>
<tr><td> Ogg            </td><td> 1.3.1        </td><td> <a href='http://xiph.org'>http://xiph.org</a> </td><td> <a href='http://xiph.org/downloads/'>Downloads</a> </td><td> <a href='http://downloads.xiph.org/releases/ogg/libogg-1.3.1.zip'>Link</a> </td></tr>
<tr><td> Vorbis         </td><td> 1.3.4        </td><td> <a href='http://xiph.org'>http://xiph.org</a> </td><td> <a href='http://xiph.org/downloads/'>Downloads</a> </td><td> <a href='http://downloads.xiph.org/releases/vorbis/libvorbis-1.3.4.zip'>Link</a> </td></tr></tbody></table>

<br>
On this screen you can see them all unpacked in <code>e:\v</code>, the downloads are on right in <code>_Install</code>, stuntrally dir will come later.<br>
<br>
<i>Game needs all, editor only uses Ogre, Bullet, MyGui, SDL2, Boost, it's easier to build editor. Enet is not needed in latest version.</i>

<img src='http://wiki.vdrift-ogre.googlecode.com/git/vs/00dnl.png' />


<br>
<h3>Build Runtime Mode</h3>

Basically we only need Debug and Relase.<br>

<blockquote><i>So don't bother setting up other versions when building dependencies.</i><br>
If you're feeling lucky you can try even only Release.<br>
Much later the RelWithDbgInfo config can be useful, if you test a lot.<i></blockquote></i>

<blockquote><i>Debug is extremely slow (like 30 fps on empty map), but it will let you use breakpoints, step code, see variable values, call stack, etc.</i><br>
Relase is the fastest, but if it crashes you usually don't know where or what caused it, only output to .log can help here.<br>
RelWithDbgInfo is between, it is a bit slower than Release but you can use breakpoints, step code, and see call stack, e.g. what caused a crash.<i></blockquote></i>

All libraries <b>MUST</b> be build using Runtime set as <b>Multi-threaded Debug DLL (/MDd</b>) in Debug Configuration,<br>
and <b>Multi-threaded DLL (/MD</b>) for Release configuration.<br>

It is very crucial to check every project in everything you will build to have those set so.<br>
This is wrong in Bullet, others seem to have it set properly.<br>

<blockquote><i>If you don't you might be cursing a lot when seeing 100s of weird linker errors out of nowhere.</i><br>
And is is quite tricky to find out which .lib caused it, if you didn't check. See e.g. <a href='http://stackoverflow.com/questions/604484/linker-errors-between-multiple-projects-in-visual-c'>here</a>.<i></blockquote></i>

<img src='http://vdrift-ogre.googlecode.com/files/IMG20121117_1s.png' />


<br>
<h3>Ogg</h3>

Let's start with something simple.<br>
Unpack libogg-1.3.1.zip to your dev folder (here e:\v) do the same with libvorbis-1.3.4.zip.<br>
Go inside <code>e:\v\libogg-1.3.1\win32\VS2010</code> and open libogg_dynamic.sln.<br>
Build should be easy, build both Debug and Release.<br>
<br>
When finished you should see similar Output (I use it as Tabbed window).<br>
It also shows where the generated .lib and .dll are, we need to know those paths to set them later in SR projects.<br>
Close libogg VS now, we don't need it.<br>
<br>
<img src='http://wiki.vdrift-ogre.googlecode.com/git/vs/05ogg.png' />

<h3>Vorbis</h3>

Now go into <code>e:\v\libvorbis-1.3.4\win32\VS2010</code> and open vorbis_dynamic.sln.<br>

In Solution explorer, select both projects vorbisdec and vorbisenc, right click and Unload project. We don't need those and setting up takes time.<br>
<br>
Then, select libvorbis and libvorbisfile, right click and Properties (or press R).<br>
<i>Since this is stupid building on Windows, and vorbis depends on ogg, yet it has no idea where you put it or which version, you have to set paths to it.</i>

In Properties, VC++ Directories, pick Include Directories, then click the down arrow on right and then Edit...<br>
New dialog will show, as seen on next screen. Click the yellow button to add new entry.<br>

Put there the path to your ogg headers, for me it was <code>e:\v\libogg-1.3.1\include</code>.<br>
Do the same for Library Directories. It should show subdirs if you type it.<br>
The path is <code>e:\v\libogg-1.3.1\win32\VS2010\Win32\Debug</code>.<br>

<img src='http://wiki.vdrift-ogre.googlecode.com/git/vs/07vorbis.png' />

Now change the configuration to Release. And do the same.<br>
Include is the same but library is <code>e:\v\libogg-1.3.1\win32\VS2010\Win32\Release</code>.<br>
<br>
Now you should build without problems. Build both Debug and Release.<br>
You will get 2 dll's (for vorbis and vorbisfile).<br>
<br>
<img src='http://wiki.vdrift-ogre.googlecode.com/git/vs/08vorbisd.png' />


<br>
<h3>Bullet</h3>

Unpack downloaded bullet-2.79-rev2440.zip.<br>
Go inside into <code>e:\v\bullet-2.79\msvc\vs2010</code> and open the solution 0BulletSolution.sln.<br>
You can skip building all Demos, select all with shift, right click, Unload Project.<br>

We need only BulletCollision, BulletDynamics, BulletFileLoader, BulletWorldImporter, LinearMath, you can unload rest.<br>
Crucial: select only those we need and set Runtime to Multi-threaded DLL (/MD) in Release and Multi-threaded Debug DLL (/MDd) in Debug.<br>

<img src='http://wiki.vdrift-ogre.googlecode.com/git/vs/09md.png' />

<h3>SDL</h3>

We downloaded already a build SDL2 archive, so just need to unpack it (SDL2-devel-2.0.3-VC.zip).<br>

<i>If you want to build SDL from sources (not needed), download <a href='http://www.libsdl.org/release/SDL2-2.0.3.zip'>this</a>.</i><br>
Then extract in <code>e:\v</code> and go into <code>e:\v\SDL2-2.0.3\VisualC</code> dir and open SDL_VS2010.sln.<br>
<br>
<h4>Enet</h4>

<i>Not needed.</i><br>
Note: on current master version, the Stunt Rally game project has Enet inside sources, so it's build with game, no need to build it outside.<br>
For older SR versions: Download the VS 2010 project files for Enet from <a href='http://vdrift-ogre.googlecode.com/files/enet_1.3.5_prj_files_vs2010.zip'>here</a>, then open it and build project (in Debug and Release as always).<br>


<hr />
<br>
<h3>Boost</h3>

<i>Welcome to the last, hardest trio Boost + Ogre + MyGui. Good luck.</i>

Start the downloaded boost_1_55_0-msvc-10.0-32.exe to install the pre-built boost archives, set dir to <code>e:\v</code>.<br>
<br>
<img src='http://wiki.vdrift-ogre.googlecode.com/git/vs/04boost.png' />

<blockquote><i>Side note: Boost consists of huge amount of really small (header/source) files and big ones (libs).</i><br>
It will be like 4GB after install, later you can just delete most of it (still need like 1GB).<br>
Because of our config we need only the files ending with <code>-mt-1_55.lib</code> and <code>-mt-gd-1_55.lib</code>.<br>
Small files will take 2x more space on HDD than actual size, depending on cluster size.<br>
I usually keep it on c:\, so when I run a search in folders (or in file contents),<br>
it doesn't spend an eternity (much less on SSD) searching inside boost dir.<i></blockquote></i>

<blockquote>If you want to build boost from sources (really not needed), download sources <a href='http://sourceforge.net/projects/boost/files/boost/1.55.0/boost_1_55_0.7z/download'>here</a> and<br> read how to build <a href='http://www.boost.org/doc/libs/1_55_0/more/getting_started/windows.html#simplified-build-from-source'>here</a> (just 2 commands in visual studio command prompt, but might take several minutes).</blockquote>


<br>
<h3>Ogre</h3>

Start the downloaded OgreSDK_vc10_v1-9-0.exe.<br>
This will install Ogre build, it already includes debug and release lib files <i>(also a piece of boost, and what not :) ).</i><br>
For reference you can read <a href='http://www.ogre3d.org/tikiwiki/tiki-index.php?page=Installing+the+Ogre+SDK'>Ogre Wiki</a>.<br>

You'll need to install also DirectX SDK June 2010 (Runtime/redist), <a href='http://www.microsoft.com/en-au/download/details.aspx?id=8109'>link here</a>.<br>
Extract that and start DXSETUP.exe.<br>
<i>(you can delete other date files leaving just Jun2010<code>_*</code>.cab and the short name files starting with d)</i>.<br>
<br>
Now its time to set the environment variables (paths) that will be needed when building MyGui.<br>
Start cmd.exe as an Administrator and use the setx command like below.<br>

<i>This way, surprisingly you don't even have to restart Windows after that.</i><br>
If you change those for CMake, just close CMake and start again,<br>
it will remember your setup and last path, and will have the env. vars changed.<br>
<br>
<img src='http://wiki.vdrift-ogre.googlecode.com/git/vs/10env.png' />

<br>
<h4>NOT needed, Optional, Building Ogre</h4>
<blockquote>Building Ogre from sources is very time consuming (and not needed to build SR).<br>
<i>Also takes like 6GB of disk space (mostly intermediate garbage).</i><br>
But if you want to or you had troubles with Ogre SDK, then I recommend this <a href='http://www.ogre3d.org/tikiwiki/tiki-index.php?page=Building+Ogre'>Building Ogre Wiki</a> on how to do it.<br></blockquote>

<blockquote><i>My short guide:</i><br>
You need to install full DirectX SDK June 2010 (samples not needed, but still 572MB to download), link <a href='http://www.microsoft.com/en-us/download/confirmation.aspx?id=6812'>here</a>.<br>
Install <a href='http://bitbucket.org/tortoisehg/files/downloads/tortoisehg-2.11.2-hg-2.9.2-x64.msi'>TortoiseHg</a> to get the sources.<br>
Clone these 2 repositories:<br>
<a href='https://bitbucket.org/cabalistic/ogredeps'>https://bitbucket.org/cabalistic/ogredeps</a> - Ogre Dependencies - into e:\v\ogre\Dependencies <br>
<a href='https://bitbucket.org/sinbad/ogre/'>https://bitbucket.org/sinbad/ogre/</a> - Ogre sources - into e:\v\ogre <br></blockquote>

<blockquote>Then use CMake for Ogre dependencies and build them.<br>
Set environment paths for BOOST_ROOT, OGRE_HOME, OGRE_DEPENDENCIES_DIR <i>(surprisingly not needed if you have <code>Dependencies</code> dir inside Ogre dir)</i>.<br>
After that use CMake for Ogre and build.<br></blockquote>

<blockquote>Other links: <a href='http://www.ogre3d.org/developers/mercurial'>Ogre Mercurial Wiki</a>, <a href='http://www.ogre3d.org/tikiwiki/tiki-index.php?page=Prerequisites'>Ogre Prerequisites</a><br>
<i>And above all, sit straight and don't curse. Also give your hands a rest, if you don't use an ergonomic keyboard or still use the layout from year <a href='http://www.dvzine.org/zine/'>1878</a>.</i></blockquote>


<br>
<h3>MyGui</h3>

<blockquote><i>Welcome to the last, worst and longest step of building dependencies.</i><br>
Here there be monsters. Btw, say hi to CMake from me.<br>
Luckily though, CMake is not that horrible if you use Ogre from SDK, it finds it.<br>
But it doesn't find freetype and <b>always</b> some paths have to be set manually.<i></blockquote></i>

Unpack MyGui (e.g. my-gui-code-5298-trunk.zip) to <code>e:\v\mygui</code>.<br>
Run CMake-Gui from start menu.<br>
Set the source path to your dir, and build dir to same path with <code>/bin</code> at end.<br>
Like on on the next screen.<br>
Press Configure, and pick Visual Studio 10 for the generator.<br>
<br>
<img src='http://wiki.vdrift-ogre.googlecode.com/git/vs/11myg0vs.png' />

The configuration will fail. Not finding freetype (and possibly Ogre).<br>
Read CMake errors to know what failed. In this Wiki's process only freetype was missing.<br>

Set the checkboxes Grouped and Advanced.<br>
Input the 4 paths for freetype like seen here. <i>If Ogre wasn't found also, then for it too.</i><br>
<i>You can select and copy if they are similar, also move with up/down, and when typing you'll get contents listed.</i><br>
This is much better to do here than in VS.<br>
<br>
<img src='http://wiki.vdrift-ogre.googlecode.com/git/vs/12myg1ft.png' />

Press Configure again. If there are no errors, you should get new options for MyGui, they'll appear in red.<br>
Press Configure again, they will stop being red (means applied).<br>
I used such options for them as below.<br>

<blockquote>Crucial are:<br>
MYGUI_USE_FREETYPE - on <i>(otherwise you won't have any text)</i>,<br>
MYGUI_RENDERSYSTEM - see hint for possible values, pick the one with Ogre<br>
MYGUI_SAMPLES_INPUT - can be just Win32,<br>
<br>
Now, if you care only about speed, to build this for SR, consider only<br>
MYGUI_BUILD_TOOLS - if on you'll get LayoutEditor which is used to edit Gui for SR.<br>
<br>
If you want to check out MyGui, check (on) - MYGUI_BUILD_DEMOS, MYGUI_BUILD_PLUGINS<br>
and MYGUI_BUILD_UNITTESTS - those are actually more demos with new Gui controls (tree, spline etc).<br>
MYGUI_DONT_USE_OBSOLETE - is not important now but I always set it on.</blockquote>

Set up the values and guess what..<br>
Press Configure again.<br>
<br>
<img src='http://wiki.vdrift-ogre.googlecode.com/git/vs/12myg2my.png' />

Lastly, to not wait forever to build (and every time to just see errors),<br>
add the /MP switch <i>(that everyone seems to forget)</i> to CXX compiler flags. <i>Don't do it in VS, it's wasting time.</i>

<img src='http://wiki.vdrift-ogre.googlecode.com/git/vs/12myg3mp.png' />

<br>
Now press Configure and then Generate.<br>
You should now have the .vcxproj and .sln files for VS.<br>
Go inside <code>e:\v\mygui\bin</code> and open MYGUI.sln.<br>
<br>
Try to build it. Don't expect this to succeed though. It will fail.<br>
It spits out an error not finding boost, which is actually an Ogre dependency now.<br>
See Error List (I also recommend showing the Project column, right click on tab).<br>
<i>Output has always more info on errors, but if there are many, Error List has a better/shorter view.</i>

<img src='http://wiki.vdrift-ogre.googlecode.com/git/vs/13myg4er.png' />

To fix this, in Solution Explorer, select all projects, except the ones with CAPITAL letters.<br>
Right click, then R (or Properties). In VC++ Directories (just like for libvorbis),<br>
add paths to boost in Include and Library Directories as seen here:<br>
<br>
<img src='http://wiki.vdrift-ogre.googlecode.com/git/vs/13myg5pr.png' />

Now it should build.<br>
<i>ATM I don't know any better way (i.e. how to fix this in CMake).</i><br>

After the build you should have LayoutEditor.exe in <code>e:\v\mygui\bin\bin\release</code>. You can try to run it.<br>
<br>
<hr />
<br>
<h2>Build Stunt Rally</h2>

<h3>Get Sources</h3>

Depending on what you installed back in <a href='http://code.google.com/p/vdrift-ogre/wiki/CompilingOnWindows#Client_for_Git'>this paragraph</a>,<br>
you may have various options to clone from git.<br>
<i>They can have the <code>--depth=1</code> parameter not available, which would result in 1GB more to download, see <a href='http://code.google.com/p/vdrift-ogre/wiki/Compiling#Get_sources'>in Wiki here</a> for size info.</i><br>

Whatever you do, keep in mind you need to have <b>tracks</b> dir inside <b>stuntrally/data</b> dir.<br>
<i>Game should start if not, but what's the point if you can't drive anywhere.</i><br>
<i>Don't worry though, after a clone to bad place, you can just move the whole directory or rename it, all will work.</i>

If you only installed Git-scm, you will have in start menu Git Bash (console), and Git GUI (which apparently doesn't have the depth parameter).<br>
Start Git Bash, navigate to our e:\v dir<br>
<pre><code>cd e:<br>
cd v<br>
</code></pre>

Then use these commands to get latest sources<br>
<i>Note: It's more than 800 MB to download, so the clone process will take a while depending on your connection speed.</i>

<pre><code>git clone --depth=1 git://github.com/stuntrally/stuntrally.git stuntrally<br>
cd stuntrally/data<br>
git clone --depth=1 git://github.com/stuntrally/tracks.git tracks<br>
</code></pre>

<br>
When using TortoiseGit, this is how to do the first command.<br>
After that you have to clone tracks inside data, so Directory will be <code>e:\v\stuntrally\data\tracks</code>.<br>
<br>
<img src='http://wiki.vdrift-ogre.googlecode.com/git/vs/14tortgit.png' />


<br>
<h3>Projects</h3>

SR comes with Visual Studio 2008 project and solution files inside <code>proj</code> dir (<code>e:\v\stuntrally\proj</code>).<br>
Those can be opened with VS 2010 Express and later, conversion dialog will pop up.<br>
<br>
<i>If you build with VS 2008, there is a known issue <code>__declspec(align('16'))</code> to solve it read:<br>
<a href='http://code.google.com/p/vdrift-ogre/issues/detail?id=135'>link</a>.</i>

Open StuntRally.sln for game (or SR_Editor.sln for editor).<br>
Projects can't be build yet. We need the correct paths to dependencies (includes and libraries).<br>

Open Project Properties, VC++ Directories, and edit Include and Library Directories.<br>
This has to be done for both projects (game and editor) in both configurations (Debug and Relase).<br>
<i>Of course if you aren't sure it will work, just do it once to test first.</i><br>
I recommend just selecting the whole line and replacing it with one from here.<br>
If you have other path than <code>e:\v</code>, copy this line and in some text editor (or even in VS) do a <i>replace all</i> for <code>e:\v</code> to your path.<br>
<br>
<h4>VC Directories</h4>

<i>This is same for both game and editor. Warning: horribly long lines.</i>

Include Directories, (same for both Debug and Release)<br>
<pre><code>e:\v\mygui\Platforms\Ogre\OgrePlatform\include;e:\v\mygui\MyGUIEngine\include;e:\v\OgreSDK_vc10_v1-9-0\include\OGRE\Plugins\ParticleFX;e:\v\OgreSDK_vc10_v1-9-0\include\OGRE\Overlay;e:\v\OgreSDK_vc10_v1-9-0\include\OGRE\Paging;e:\v\OgreSDK_vc10_v1-9-0\include\OGRE\Terrain;e:\v\OgreSDK_vc10_v1-9-0\include\OGRE;e:\v\boost_1_55_0;e:\v\libogg-1.3.1\include;e:\v\libvorbis-1.3.4\include;e:\v\SDL2-2.0.3\include;$(IncludePath)<br>
</code></pre>
Library Directories, Release<br>
<pre><code>e:\v\bullet-2.79\Extras\lib;e:\v\bullet-2.79\lib;e:\v\mygui\bin\lib\Release;e:\v\OgreSDK_vc10_v1-9-0\lib\Release;e:\v\boost_1_55_0\lib32-msvc-10.0;e:\v\libvorbis-1.3.4\win32\VS2010\Win32\Release;e:\v\libogg-1.3.1\win32\VS2010\Win32\Release;e:\v\SDL2-2.0.3\lib\x86;$(LibraryPath)<br>
</code></pre>
Library Directories, Debug<br>
<pre><code>e:\v\bullet-2.79\Extras\lib;e:\v\bullet-2.79\lib;e:\v\mygui\bin\lib\Debug;e:\v\OgreSDK_vc10_v1-9-0\lib\debug;e:\v\boost_1_55_0\lib32-msvc-10.0;e:\v\libvorbis-1.3.4\win32\VS2010\Win32\Debug;e:\v\libogg-1.3.1\win32\VS2010\Win32\Debug;e:\v\SDL2-2.0.3\lib\x86;$(LibraryPath)<br>
</code></pre>

<img src='http://wiki.vdrift-ogre.googlecode.com/git/vs/15ed2.png' />

<h4>Output dir</h4>

Last thing we need, is to set empty Output dir.<br>
Open Project properties and on General tab, select the Output Directory and just delete it.<br>
<i>Need to do it for both projects and both configurations.</i>

<img src='http://wiki.vdrift-ogre.googlecode.com/git/vs/25out.png' />


<h3>Build</h3>

With the above settings and paths set, you should be able to build game or editor finally.<br>
It will take a minute or two.<br>
So, if you don't see any errors and you got your new shiny exe (in project dir), I can now say:<br>
<br>
Congratulations ! The nightmare is over.<br>
<br>
<i>Still, depending on how you built all dependencies and if there were any problems, it can happen that you'll need to rebuild them. So best is to just keep all dirs untouched.</i>

<br>
<hr />
<h3>Run</h3>

The executable requires a number of dll files, when you first start it, it will surely crash since none are there.<br>
So, gather all the .dll files that were build or installed <i>(all are in e:\v, in all lib's output release/debug dirs)</i>.<br>
<i>You can use Find Files (alt-F7 in Double Commander) with <code>*.dll</code> to save you the manual search.</i>

<img src='http://wiki.vdrift-ogre.googlecode.com/git/vs/28find.png' />

And copy them into <code>e:\v\stuntrally\proj</code> dir <i>(same where executables should appear)</i>.<br>
<br>
<i>It should be noted that some (ogg,vorbis,SDL) have same names for Debug and Release .dll and .lib output (this is wrong), so we use Release only.</i>

The exact list is (those with <code>_d</code> are for debug):<br>
<pre><code>libogg.dll<br>
libvorbis.dll<br>
libvorbisfile.dll<br>
MyGUIEngine.dll<br>
MyGUIEngine_d.dll<br>
OgreMain.dll<br>
OgreMain_d.dll<br>
OgreOverlay.dll<br>
OgreOverlay_d.dll<br>
OgrePaging.dll<br>
OgrePaging_d.dll<br>
OgreTerrain.dll<br>
OgreTerrain_d.dll<br>
Plugin_ParticleFX.dll<br>
Plugin_ParticleFX_d.dll<br>
RenderSystem_Direct3D9.dll<br>
RenderSystem_Direct3D9_d.dll<br>
RenderSystem_GL.dll<br>
RenderSystem_GL_d.dll<br>
SDL2.dll<br>
</code></pre>

After that it should really start.<br>
If it doesn't check out <a href='http://code.google.com/p/vdrift-ogre/wiki/Running'>Running wiki page</a>, see Ogre.log, etc.<br>
<br>
<img src='http://wiki.vdrift-ogre.googlecode.com/git/vs/32run.jpg' />

Have fun.<br>
<br>
<hr />