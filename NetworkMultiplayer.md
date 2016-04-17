## Introduction ##

This page contains information about the network multiplayer feature (starting with version 1.5).

## Quick guide ##
  1. To Join a game: Go to the Single Race -> Multiplayer tab and press the Refresh list -button.
    * This will connect to the master server for available games (see chapter below)
  1. Select a game you wish to join and press the Join game -button
  1. Alternatively you can host your own game by pressing the Create game -button (the game will show up in the list for others to join).
    * You can also connect directly to an IP:port by choosing _Direct connect_
  1. Press Ready-button in the game lobby tab and wait for others to become ready too.
  1. The game shall start when the host presses the button.
  1. It is possible (since 2.2) for host to continue game on other track (or restart on current)
    * When host presses new game (same button as start) curent game will end, peers will have shown menu
    * Host can now change track (and game settings) and after all peers have pressed ready, game can start again

### Players? ###
Don't expect available games to appear on server list.

Someday there may be simultaneous games to join at any given moment, but before (and if) that happens,

you should enlist your friends to play with you. (All players need to have ports forwarded)

Or alternatively come to #stuntrally IRC channel at the Freenode network to challenge one of the devs or hang-arounds.

There is a webpage with status of available games http://stuntrally.dy.fi/.

<br>
<h2>Troubleshooting</h2>

<b>Q:</b> I get a "Network error" message box when I try to join or create a game.<br>
<br>
<b>A:</b> Maybe some other program is currently using the local port. Try a different one by changing it in the Settings-tab. Also make sure your firewall isn't blocking Stunt Rally - it needs permissions to both access the internet as well as listen for connections (i.e. permission to be a server).<br>
<br>
<br>
<b>Q:</b> Other players can't connect to me!<br>
<br>
<b>A:</b> Most likely your router is blocking access. Configure it to forward the traffic coming to the Stunt Rally local port (check it from Multiplayer's Settings-tab) to your computer. You might find <a href='http://portforward.com/'>http://portforward.com/</a> helpful.<br>
<br>
<br>
<b>Q:</b> I cannot connect to some players!<br>
<br>
<b>A:</b> This is the previous problem reversed - their firewall is misconfigured. If you have your router properly configured, the others should be able to connect to you and as such you don't need to connect to them anymore. Obviously this doesn't apply if you are the host.<br>
<br>
<br>
<b>Q:</b> I get errors about protocol versions!<br>
<br>
<b>A:</b> This means that your version of Stunt Rally is incompatible with the master-server and/or other players (depending on with whom you are trying to communicate). Your best bet is to make sure you are running the latest release of SR. Otherwise, tell your fellow players or master-server administrator (that's us most likely) to upgrade.<br>
<br>
<br>
<b>Q:</b> How can I change my nickname?<br>
<br>
<b>A:</b> Go to the Settings-tab under the Multiplayer main tab.<br>
<br>
<br>
<h3>Technical details</h3>
Stunt Rally uses a lightweight master server for tracking available games. All other networking is based on the peer-to-peer architecture, meaning all players are connected to each others and there is no separate game server.<br>
<br>
The underlying protocol used is UDP, though ENet, the networking library, builds it's own layer on top of that, so using generic UDP sockets for communicating with SR or master server is not possible.<br>
<br>
<h3>Master server</h3>
Master server is a simple command-line server (can be daemonized on Linux) that accepts game announcements and passes a list of them to anyone who asks. Clients must update the games periodically or they will timeout in the master server.<br>
<br>
Anyone can build and host a master server, but players need to set the correct address and port in the Multiplayer | Settings tab in order to connect to it.