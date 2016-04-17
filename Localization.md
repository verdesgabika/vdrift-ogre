

<br>
<h2>Introduction</h2>

Stunt Rally supports translating (nearly all) visible strings in Game and Editor.<br>
<i>Supplying translations, even small typo fixes, is a great way to contribute.</i>

You can easily and conveniently translate on the webpage:<br>
<a href='https://www.transifex.com/projects/p/stuntrally/'>https://www.transifex.com/projects/p/stuntrally/</a><br>

<i>You can also download the translation from there and translate it locally using a tool like eg. <a href='http://sourceforge.net/projects/poedit/'>PoEdit</a>.</i><br>

<br>
<h2>How to start</h2>

<ol><li>Get yourself an account on Transifex, if you don't have one already<br>
</li><li>Pick your language and join its translation team (on website, link above)<br>
</li><li>Add a language if it is not there (if you intend to translate at least 20% of it)<br>
</li><li>You can tell us on IRC that you did, so we can approve it faster<br>
</li><li>Start translating</li></ol>

<br>
<h2>Order</h2>

There are lots of strings to translate, above 1100.<br>
This is the recommended order in which to translate.<br>
<br>
<ol><li>First translate the strings that have 'HUD' or 'MAIN' in <b>Developer comment</b><br><i>This way even with few translations a language can already be useful</i>
</li><li>Next translate only one word strings (for game and editor, Gui tab captions etc.)<br>
</li><li>Then short game strings, related to challenges etc.<br>
</li><li>Game Hints and other contents of Welcome screen<br>
</li><li>Editor Input texts (keys shown in editor help window, long but crucial for editor users)<br>
</li><li>Leave tooltips for last (they have 'TIP' in Developer comment and are quite long)</li></ol>

<br>
<h2>General Hints</h2>

<ul><li>Try to keep your translated strings at equal length (or shorter) of the english strings,<br>to make sure they will fit into the GUI (for tooltips this doesn't matter).<br>
</li><li>Full translation requires time and patience, also good game and editor experience to catch the text meaning.</li></ul>

<ul><li>Check <b>Developer note:</b>
<ul><li>This is my comment, usually a group name for few strings telling what are they for.<br>
</li><li>Those having 'Main' are more important than others.<br>
</li><li>Usually if this comment has a long group name it's not that important as the shorter ones.<br>
</li><li>If you see 'Input' then this is a text for either mouse or keyboard action<br>
</li><li>Only few strings have some unusual longer remarks<br>
</li></ul></li><li>See <a href='http://i.imgur.com/hgmuHyJ.png'>this image</a> for reference<br>
</li><li>Unwind the pane More details, it shows more info, namely:<br>
</li><li><b>Occurrences</b>
<ul><li>for Gui .layout files shows in which, at which line and<br><b>Widget name hierarchy</b> (parent widget captions)<br>ending with widget <b>type</b> on which this string is.<br>
</li><li>for source .cpp files shows path (inside source/), file name and at which line.<br>
</li></ul></li><li>Context, this is a string id from xml<br>e.g. all input texts start with Input, tips start with Tip etc. (apart from that it's not very helpful)</li></ul>

<br>
<h2>How to read the occurrences text</h2>

Example for Boost string:<br>
<pre><code>Game.layout :1076..SingleRace.Game.Main.Text<br>
 :1133..SingleRace.Game.Tab<br>
 :2842..Options.View.Camera.Check<br>
ogre/Challenges.cpp:596<br>
ogre/Gui_Init.cpp:521<br>
ogre/Gui_Network.cpp:132<br>
</code></pre>
So, this string Boost, can be found in Gui:<br>
<ul><li>file Game.layout lines 1076,1133 and 2842<br>
</li><li>in 'Single Race' window, tab 'Game', subtab 'Main' as a Text<br>
</li><li>in 'Single Race' window, tab 'Game', as Tab caption<br>
</li><li>in 'Options' window, tab 'View', subtab 'Camera' as CheckBox caption</li></ul>

And in above mentioned source files with line numbers.<br>
<br>
Line numbers are combined if in same file e.g.<br>
<pre><code>ogre/Gui_Network.cpp:29:345:567<br>
</code></pre>

<br>
<h2>How to check your strings back</h2>

To do this you need to get the .po file back from webpage (download).<br>
Or if you translate with a program locally just save it and get the new .po file.<br>

Run the python script locale/xml_po_parser.py on the .po file to get a <code>*_</code>tag.xml file back.<br>
e.g. inside locale/<br>
<pre><code>xml_po_parser.py de.po core_language_de_tag.xml<br>
</code></pre>
Move the xml into data/gui. Start game or editor and test.<br>
<br>
<br>
<h2>Sync translations</h2>

If you build from sources, and you translated something recently, then<br>
when you see on master a commit 'Sync translations.' this means that<br>
translations have been updated and you can now check them (after pull).<br>
<br>
<br>
<hr />

<br>
<h2>Technical Details</h2>

We use gettext's .po and .pot files for web translations, it is a very popular text format.<br>
<br>
All strings in Stunt Rally are in <b>the xml file</b> data/gui/core_language_en_tag.xml.<br>
Used by MyGUI's own translation system.<br>

This file is edited manually, each new string is added there.<br>
It also has xml comments with group names,<br>
which then show up as Develeoper comment on web (as #. in .pot file).<br>
<br>
A C++ program (source/transl/main.cpp) generates sr.pot templates file from the xml file.<br>
<i>It also searches for string references in sources and Gui layouts, also getting widgets hierarchy.</i>

Web translation gives translated .po files back, which are then converted to<br>
MyGUI's translations (other languages <code>*_</code>tag.xml)<br>
by the locale/xml_po_parser.py python script.<br>
<br>
<br>
<br>
<h2>Setup Transifex</h2>

This is a section for developers, who want to do fast translation updates.<br>
<br>
Download the <a href='http://docs.transifex.com/developer/client/setup'>Transifex client</a> (command line tool).<br>
It can both pull new .po translations from website and push new .pot to it.<br>
The commands for that are: 'tx pull -a' and 'tx push -s'.<br>
<br>
See Transifex documentation: <a href='http://docs.transifex.com/developer/client/'>http://docs.transifex.com/developer/client/</a>

To setup, I used (in our locale/ dir):<br>
<pre><code>tx init<br>
tx set --auto-remote<br>
</code></pre>
and manually edited .tx/config file to put repo url, and source_file with .pot.<br>
<br>
This is the final .tx/config file used:<br>
<pre><code>[main]<br>
host = https://www.transifex.com<br>
<br>
[stuntrally.srpot]<br>
file_filter = translations/stuntrally.srpot/&lt;lang&gt;.po<br>
source_lang = en<br>
source_file = sr.pot<br>
type = PO<br>
</code></pre>

For reference the user config file .transifexrc in your OS user dir:<br>
<pre><code>[https://www.transifex.com]<br>
hostname = https://www.transifex.com<br>
password = pass<br>
token = <br>
username = user<br>
</code></pre>
Replace user and pass with your login.<br>
<br>
<br>
<br>
<h2>Doing Sync translations</h2>

Currently to sync translations on Windows you need to have in locale/ dir:<br>
sr_transl.exe  - is build from source/transl/main.cpp, open project proj/sr_transl.vcproj<br>
tx.exe  - is the downloaded Transifex client.<br>
<br>
Having that set up, run in locale/ dir:<br>
tx_1upd-all.bat<br>
<i>(to update .pot, push it, pull .po and convert all to .xml)</i><br>
and then<br>
tx_2git.bat<br>
<i>(to commit and push).</i><br>


<br>
<h2>Adding new languages</h2>

See example commit adding Czech (cs) language: <a href='https://github.com/stuntrally/stuntrally/commit/18018ecff5ddc27eea7d26f023e2ecea554d5e88'>link</a>

Needs to be added in 4 places:<br>
<br>
data/gui/core_language.xml<br>
<pre><code>&lt;Info name="cs"&gt;<br>
  &lt;Source&gt;core_language_cs_tag.xml&lt;/Source&gt;<br>
&lt;/Info&gt;<br>
</code></pre>

data/gui/core_language_en_tag.xml<br>
<pre><code>&lt;Tag name="LANG_CS"&gt;Čeština&lt;/Tag&gt;<br>
</code></pre>
Language name in this language (found on e.g. Wikipedia).<br>
This will be visible in combobox on Gui.<br>
Note that it needs translation update after, to have the new tag in all languages.<br>
<br>
source/ogre/Localization.h<br>
<pre><code>else if (!strcmp(buf,"Czech")) loc = "cs";<br>
</code></pre>
English name of language from windows GetLocaleInfoA function.<br>
<br>
source/ogre/common/GuiCom_Util.cpp<br>
<pre><code>languages["cs"] = TR("#{LANG_CS}");<br>
</code></pre>

<br>