KODItorrent
===========

What it is
----------
KODItorrent is a fork of XBMCtorret. Koditorrent allows you to stream bittorrent magnet links right from XBMC/KODI, without having to wait for the whole file to download, thanks to sequential download (see FAQ).

XBMCtorrent was created by [steeve](https://github.com/steeve) but is no longer receiving updates. I created KODItorrent to add some improvements to its original design. Check out [Pulsar](http://forum.kodi.tv/showthread.php?tid=200957) to see steeve's newest project.

How is it different from XBMCtorrent?
-------------------------------------
KODItorrent has a more simple design and comes with more options. 
Some of the extra options include being able to download the whole file instead of streaming it, have users be able to set their own buffer size, and having the option to download all MP4's and M4V's so you will no longer get playback issues like you see with XBMCtorrent. MAKE SURE TO CHECK OUT THE NEW SETTINGS!

Screenshots
-----------

![KODItorrent Screenshot1]
(http://i.imgur.com/drapd4z.png)
![KODItorrent Screenshot2]
(http://i.imgur.com/pTPqomt.png)
![KODItorrent Screenshot3]
(http://i.imgur.com/D40lFzT.png)
![KODItorrent Screenshot4]
(http://i.imgur.com/V7wFGfA.png)
![KODItorrent Screenshot5]
(http://i.imgur.com/vOBsanL.png)
![KODItorrent Screenshot6]
(http://i.imgur.com/eDpfrNk.png)
![KODItorrent Screenshot7]
(http://i.imgur.com/HfywRUf.png)

Download
--------
[Download link](https://mega.co.nz/#!rVxgAJiC!G94zLiwq3s4u5SCRuTMLcK4jshnoKtGzS8n268uLRjk)

Supported Platforms
-------------------
* Windows x32 x64
* OS X x32 and x64
* Linux x32 and x64
* Raspberry Pi
* Android 4.0+

How it works
------------
KODItorrent is actually two parts:
* _KODItorrent_: the addon written in Python.
* `torrent2http`: a custom bittorrent client written in Go and leveraging libtorrent-rasterbar, that turns magnet links into HTTP endpoints, using sequential download.

If you feel adventurous, you can find the `torrent2http` and `libtorrent-go` sources at:
* https://github.com/steeve/libtorrent-go
* https://github.com/steeve/torrent2http

FAQ
---
#### I can't code. How can I help?
Spread the word. Talk about it with your friends, show them, make videos, tutorials. Talk about it on social networks, blogs etc...

#### Does it work with all torrents?
Almost all torrents can be played from KODItorrent. MP4's and M4V's were know to cause issues in XBMCtorrent due to the index not being located at the beginning of the files, but in KODItorrent you have to option to download the whole MP4 and M4V files first so they will now play.

#### The plugin doesn't work at all, what can I do?
First of all, we need to make sure it's not the torrent fault. I usually test this by searching for small serie episodes on Piratebay. Try that, if it does't work, send me your xbmc.log.

#### Can I seek in a video?
Yes, although now if you try to seek to a part you haven't downloaded yet, XBMC will wait for that part to be available

#### Can it stream HD?
Of course! 720p and 1080p work fine, provided you have enough bandwidth, and there are enough people on the torrent (see video).

#### Doesn't sequential download on bittorrent is bad?
Generally, yes. However, KODItorrent respects the same [requirements "defined" by uTorrent 3](http://www.utorrent.com/help/faq/ut3#faq2[/url]). Also, KODItorrent tries to make it up to the swarm by seeding while you watch the movie.

#### What about seeding?
KODItorrent will seed the file you're watching until it's finished playing. For instance, if the download of a 2 hours long movie is finished in 10 minutes, you'll continue seeding it until you finish watching the movie. This is by design, to make up for the fact that we are using sequential download.

#### Does it downloads the whole file? Do I need the space? Is it ever deleted?
Yes and yes. KODItorrent will pre-allocate the whole file before download. So if you want to watch a 4GB video, you'll need the 4GB. The file is deleted once you stop watching it.

#### Can I keep the file after playback?
Yes, just enable this option in the addon settings.

#### Can I set it to download directly to my NAS and keep it after playback?
Yes of course. Just set the download directly to your NAS location, and make sure you have enabled "Keep files after playback" option.

#### Why are you using Google Analytics? Can I disable it?
First of all, your whole IP isn't tracked. Only the first 3 parts of it, thanks to Analytics [Anonymous Mode](https://developers.google.com/analytics/devguides/collection/gajs/methods/gaJSApi_gat?csw=1#_gat._anonymizeIp). So for instance, if your IP is A.B.C.D, only A.B.C.0 will be logged.
Second, this is my only tool to track audience interest, this is great information, and it really helps.
Finally if you really want to, you can disable it in the addon settings (except for 1 GA event when you go in the addon).
If you are blocking GA on your computer altogether, you'll still be able to use the addon.

#### How can I report a bug?
Please, file an issue :)

#### Torrents are suddenly paused and then interrupted/stopped. What can I do ?
Probably your network is too slow and you are hitting a timeout used for HTTP on
XBMC. You can increase the timeout as documented
[here](http://wiki.xbmc.org/?title=Advancedsettings.xml#playlisttimeout). Please
note that increasing the timeout won't make your network faster, you just will
wait more time before the torrent is interrupted.

#### Provider X is blocked in my country/ISP, how can I set another domain?
Enable Auto-Unblock in the settings.
If it still doesn't work, you can go in Advanced > Custom Domains. Here to you can set each provider with whatever proxy you choose.
