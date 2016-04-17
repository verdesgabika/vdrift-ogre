

<br>
<h2>Introduction</h2>

<i>Compiling on Windows, is usually a nightmare. Yes, it is, and thus should be avoided.</i><br>
For compiling on Windows, using VS2010 Express see this <a href='CompilingOnWindows.md'>Wiki page</a>.<br>
<br>
<br>
Compiling Stunt Rally on Ubuntu using CMake is quite easy.<br>
Recently (on 14.04) all dependencies can be just installed using apt-get.<br>
<br>
This is the recommended way, even if you don't know any <a href='http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29'>Ubuntu OS</a> or GNU/Linux at all.<br>
<br>
On other GNU/Linux distributions building probably isn't much trouble,<br>
if you know how to build 1 or 2 dependencies from sources (if they aren't available).<br>
<br>
<br>
<h2>Get sources</h2>

It is recommended that you get the latest version directly from the Git code repository.<br>
Use software manager to install git or this command:<br>
<pre><code>sudo apt-get install git<br>
</code></pre>
Then, use these commands to get sources:<br>
<br>
<pre><code>git clone --depth=1 git://github.com/stuntrally/stuntrally.git stuntrally<br>
cd stuntrally/data<br>
git clone --depth=1 git://github.com/stuntrally/tracks.git tracks<br>
</code></pre>

<br>
This will get sources to a directory called "stuntrally" and inside it will download the tracks to a subdirectory "data/tracks".<br>
If you got sources some other way, be sure to have tracks/ inside data/.<br>
<br>
<blockquote>Note: The parameter --depth=1 tells git to not get history (to lower download time and space).<br>
This way data is about: 300 MB and 500 MB for tracks.<br>With history it's quite big: 500 MB and 1,5 GB for tracks.</blockquote>

<blockquote>You can use other depth value to get some recent commits.<br>
Or download an archive from github: <a href='https://github.com/stuntrally/stuntrally/tags'>here</a> and tracks <a href='https://github.com/stuntrally/tracks/tags'>here</a>.</blockquote>

<br>
If you want to use a (stable) release version, instead of the (latest) cutting edge development version,<br>
use the following command (replace 2.3 with the desired version number):<br>
<pre><code>git checkout 2.3<br>
</code></pre>
You can see the available versions with the following:<br>
<pre><code>git tag<br>
</code></pre>

<br>
<h2>Dependencies</h2>

Here's a list of libraries you need (newer versions can be used):<br>
<table><thead><th> Library </th><th> Downloads link </th></thead><tbody>
<tr><td> OGRE 1.9 with plugins:<br> OgrePaging, OgreTerrain, Plugin_ParticleFX </td><td> <a href='http://www.ogre3d.org/download'>http://www.ogre3d.org/download</a> </td></tr>
<tr><td> MyGUI 3.2 with Ogre support </td><td> <a href='http://mygui.info'>http://mygui.info</a> <a href='http://github.com/MyGUI/mygui'>Sources</a> </td></tr>
<tr><td> SDL2    </td><td> <a href='http://libsdl.org/download-2.0.php'>http://libsdl.org/download-2.0.php</a> </td></tr>
<tr><td> OGG, VorbisFile </td><td> <a href='http://xiph.org/downloads'>http://xiph.org/downloads</a> </td></tr>
<tr><td> Boost (system, thread, filesystem, wave) </td><td> <a href='http://www.boost.org/users/download'>http://www.boost.org/users/download</a> </td></tr>
<tr><td> ENet    </td><td> <a href='http://enet.bespin.org/SourceDistro.html'>http://enet.bespin.org/SourceDistro.html</a> </td></tr></tbody></table>

Either install them from your distribution's package manager (including the -dev packages), or download and compile them yourself.<br>
<br>
<br>
In Ubuntu, those commands should get you all dependencies.<br>
<br>
<pre><code>sudo apt-get update<br>
sudo apt-get install --assume-yes git cmake g++<br>
<br>
# boost<br>
sudo apt-get install --assume-yes libboost-wave-dev libboost-system-dev libboost-filesystem-dev libboost-thread-dev<br>
<br>
# ogre<br>
sudo apt-get install --assume-yes libogre-1.9-dev libmygui-dev libsdl2-dev<br>
<br>
# sound<br>
sudo apt-get install --assume-yes libogg-dev libvorbis-dev libenet-dev<br>
</code></pre>

<br>
These are included in sources and compiled with project (no need to do anything):<br>
<ul><li>Bullet 2.79 (need this version)<br>
</li><li>BtOgre #<br>
</li><li>OICS #<br>
</li><li>PagedGeometry 1.1.1 #<br>
</li><li>shiny<br>
</li><li>TinyXML,TinyXML2<br>
Marked modified sources with #.</li></ul>

<br>
<h2>Compiling</h2>

Project is written in C++. For compilation, we use CMake.<br>
Use following commands (for Unix-like shell environments, such as Bash or MSYS):<br>
<br>
<pre><code>cd stuntrally   # Change directory to the game sources<br>
mkdir build     # Create a build directory<br>
cd build        # Change to the build directory<br>
cmake ..        # Create build files<br>
make -j4        # Compile using 4 threads (change to your number of CPUs)<br>
# Optionally install everything (you can run without installing)<br>
make install    # might need administrator privileges<br>
</code></pre>

<br>
<h2>Troubleshooting</h2>
If you get errors on the "cmake"-step, you are most likely missing some library or CMake couldn't find it. Install the development files for the library in question and if automatic finding fails, tell the paths to CMake manually. On Windows you should be able to open up a graphical interface by double-clicking the CMakeCache.txt file in the build directory. Similar interface is also available on other platforms, but the command-line alternative "ccmake" is also quite popular on GNU/Linux.<br>
<br>
CMake has <a href='http://www.vtk.org/Wiki/CMake_Generator_Specific_Information'>various generators</a> besides Makefiles for you to choose from, including Visual Studio, Eclipse CDT and Code::Blocks project files.<br>
<br>
<h4>Useful CMake variables</h4>
Here's some variables that come in handy frequently. You can set them on command line by: <code>cmake -DVARIABLE_NAME=VALUE</code> or use one of the GUIs.<br>
<br>
<ul><li>CMAKE_BUILD_TYPE - this determines release/debug builds, possible values are Release, Debug, MinSizeRel, RelWithDebInfo, defaulting to the last one.<br>
</li><li>CMAKE_INSTALL_PREFIX - Specify the path where files are copied if <code>make install</code> is invoked (on GNU/Linux, usually /usr or /usr/local).<br>
</li><li>BUILD_EDITOR - Disable editor compilation by setting this to OFF.</li></ul>

For more information about CMake, see the <a href='http://www.cmake.org/cmake/help/documentation.html'>documentation</a> and <a href='http://www.vtk.org/Wiki/CMake'>wiki</a>.<br>
<br>
<br>
<br>
<h2>Running</h2>

Once everything is compiled, you can run the game from the build directory (<code>./stuntrally</code>).<br>
If you didn't use CMake, you'll probably have the exe in the source root, from where you can also run the game.<br>
Same also applies to the editor, which is called <code>sr-editor</code>.<br>
<br>
More information available in the <a href='Running.md'>Running</a> wiki page.