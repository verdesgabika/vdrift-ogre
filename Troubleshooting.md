## Introduction ##

This page describes how to properly report bugs etc. as well as self help tips.

## Where to report problems ##

  * IRC: #stuntrally @ freenode network, [webchat](http://webchat.freenode.net/?channels=#stuntrally)<br>(fastest way (instant if someone is awake), but then again you might need to stick around and wait)<br>
<ul><li><a href='http://forum.freegamedev.net/viewforum.php?f=78'>Bugs &amp; Help forum</a>
</li><li><a href='http://code.google.com/p/vdrift-ogre/issues/list'>Issue tracker</a> (only if you can't use the above)</li></ul>

<h2>What we will ask from you</h2>

So how about saving your time as well as ours and providing the answers before we get a chance to ask them? You might also find the cause by yourself.<br>
<br>
<ol><li><b>Do you have an integrated Intel graphics card (e.g. a non-gaming laptop)?</b>
<ul><li>There is your cause for the crash - Stunt Rally needs a decent GPU, nothing we can do apart from recommending you to upgrade your hardware (or visit a friend with better hardware)<br>
</li></ul></li><li><b>What operating system are you using? What version of Stunt Rally? From where did you install SR?</b>
<ul><li>If you are not using the latest release version of SR, we'll probably ask you to upgrade and test that<br>
</li></ul></li><li><b>When did the crash occur? Did you get any graphics? Did you get to the menu? After loading a track?</b>
</li><li><b>Please post log.txt and ogre.log files, their location is given in the <a href='Paths.md'>Paths</a> wiki page</b>
<ul><li>Use attachments if on forum or issue tracker<br>
</li><li>Use pastebin.com or similar if on IRC<br>
</li></ul></li><li><b>Please follow up</b>
<ul><li>Fixing bugs might take days or even longer<br>
<ul><li>We are not always able to reproduce the problem (e.g. due to missing hardware), even if we acknowledge its existance, so we rely on your testing and confirmation of fixes<br>
</li></ul></li><li>If using IRC:<br>
<ul><li>Please don't leave if there is no immediate answer<br>
</li><li>If after waiting, no one still seems to be around, come back another day, or file an issue to forum (or tracker)</li></ul></li></ul></li></ol>

<h2>Debugging yourself</h2>

If you wish to be extra helpful (and are on Linux), you can provide a stack trace of the crash.<br>
<br>
<ol><li>Install <code>gdb</code>, the GNU Debugger<br>
</li><li>Install <code>stuntrally-dbg</code> or similar, i.e. Stunt Rally with debugging symbols. You can also compile the game yourself with the debugging info.<br>
</li><li>Run SR through the debugger:<br>
<ul><li><code>$ gdb stuntrally</code>
</li><li><i>(you are taken to gdb prompt)</i>
</li><li><code>run</code>
</li><li><i>(wait for the crash)</i>
</li><li><code>bt</code> <i>(stands for backtrace)</i>
</li><li>Copy-paste the resulting trace to use as with the log files