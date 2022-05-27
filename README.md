# .plan
Like a blog, but with less effort

## May 27th, 2022

I've been thinking a lot lately about some of my older projects, and I think it is time for one of them to go into the wild.

I have already released everything for [Kindle Touch Kiosk](https://github.com/bishopdynamics/kindle-touch-kiosk), 
which is a collection of hacks allowing you to run a VNC Client on an old Kindle Touch.
I also prepared a docker container which serves as the VNC server, with a Chromium window full-screen to a specified URL.
I use this for my Home Assistant setup at home, and it works quite well. 

It should be noted: that project is entirely made up of other people's work, the only original contribution from me is the docker stuff, and even that is based on other people's work.
I have released it without license. Any of my original work you are free to do whatever you want without restrictions, much of the work it is based on also lacks license. 
Generally speaking, it would not be appropriate to use this in any kind of commercial context.

---
There is a second project that I will be releasing Real Soon Now, called NetbootStudio.

NetbootStudio is a tool for automating OS installations via network booting. 
I developed it because I found I was re-installing Debian and Ubuntu VMs quite often, and it was starting to get annoying having to do it by hand.

NetbootStudio revolves around iPXE, is written in Python3, and is capable of automating installations of Debian, Ubuntu, VMware ESXi, and Windows 8 thru 11. 
Automation for Windows is definitely second-class (I despise Windows), but it works well enough; arm64 edition of Windows 11 should work, but it was not well tested. 
I use it to re-image my gaming PC every 6 months.

A lot more could be said about this project here, but I'll let the project readme speak for itself.

I actually have two iterations of this project. 
The first iteration was very jury-rigged, and although it worked pretty darn well, I had a huge list of improvements I wanted to make long before it got to a "complete" stage.
In some ways, it could be viewed as still a more complete version because it includes the "Create Image" wizard.

The second iteration was basically a project reboot. I threw away most of the original code and tried to focus on better handling of multithreading. 
This version includes its own embedded TFTP server, which allowed me finer control over how it behaved.
I also added in this version, support for arm64 targets, presuming they use uboot.
I used this version extensively in my home lab, particularly for rapidly imaging RockPi boards.
Unfortunately, I never got around to building the "Create Image" wizard for this version, so you have to build your images by hand.

In the past year, I haven't used NetbootStudio much, mainly because I've moved away from hosting everything in VMs to using Docker containers instead; the performance difference is night and day.
I have also migrated all my infrastructure to arm64 hardware (goodbye x86!). These two combined have led me to use NetbootStudio significantly less, and as a result I have been less interested in working on it.

Once I've had a chance to clean things up a bit, I will upload both versions to Github with the hope that someone will learn something. 
Unless I encounter any issues, both should be GPL licensed. Should be some time next week.

 Stay tuned.


## May 26th, 2022

I recently read through all of John Carmack's .plans from about 1996 through 2010, and oh boy
what a fascinating read! 

I thought it might be interesting to start writing in a similar style, not that I'm under any
delusions about myself being a comparable engineer to Carmack.

I've been reading a LOT of code lately, almost exclusively C++. It started when I stumbled across an old
archive of early alpha builds of Unreal from ~1995. I had played with one before, but previously I had thought
that there was only one "unreal '95 alpha". 

Boy was I surprised to discover that there are actually [14 separate alpha builds available](https://geocities.ws/yrex/mojunreal/beta/games.html)!
These builds range from 1995 through 1998, with the last one (build 99) containing almost all the final maps of the game.
Furthermore, 6 of these builds came with source code!

For a more complete history of the development of the original Unreal, check out [this thread on BetaArchive](https://www.betaarchive.com/forum/viewtopic.php?t=17420&sid=fad69ecdd577d55d0adc4fb4b1647548).

Things got a little out of hand after that, as I quickly discovered that there are a surprisingly large number
of leaked builds of various Unreal-based games out in the wild. I was able to find examples, with source, for every generation
of the Unreal engine.

I should probably take a step back and talk little about my history with the Unreal engine. 
I was first introduced to Unreal Tournament by my older step-brother, and I was instantly obsessed.
For reasons that weren't entirely clear to me, he was unwilling to actually give me a copy of the game. 
In hindsight, he probably grabbed it from someone on IRC and didn't want to deal with explaining to me what that entailed.
I immediately convinced my mom to let me buy a copy of Unreal Gold, and I was disappointed to discover that it was a completely different game!
But that changed nothing, I played the heck out of that game. 

And then I discovered the console. 

Now, it is important to remember that Unreal Gold shipped with a broken build of UnrealEd. Eventually, someone put out a patch to fix it, but I
would not find that til much later. In the meantime, I started picking apart this game from within the console, and taking apart every file in the System folder
trying to understand how the whole thing works.

Eventually, I can't remember exactly when, but I got myself a copy of Unreal Tournament GOTY and then things really took off. With a functional editor I 
suddenly had a much bigger world available to me, and I quickly started building maps, textures, and scripts. UnrealScript seemed very natural to me, 
even though my only experience at the time was with QBasic (yup), and I certainly had never encountered Object-Oriented paradigm before.

I really enjoyed playing the first three Harry Potter games for PC, made by [KnowWonder](https://www.pcgamingwiki.com/wiki/Company:KnowWonder) studios, but I probably
wouldn't have bought the 2nd and 3rd game if I had not discovered that they were running on the Unreal engine!
The first two games are developed on Unreal Engine 1 build 443 (with a few subsystems back-ported from v2), and the third game is on Unreal Engine 2 (I haven't figured out what build yet).

I tore these games to pieces. If these games were physical toys, I ripped them apart into a sea of pieces strewn across the floor.
For the third game, I grafted pieces from the [Unreal Engine 2 Runtime](https://docs.unrealengine.com/udk/Two/UnrealEngine2Runtime22262002.html) to get myself a pretty decently working editor, and
used that to stitch together a single map of the entire interior of Hogwarts. I remember I even managed to get character animations and logic going well enough to have students
milling about, who would say random lines when you bumped into them. I also had the moving staircases working better than the original implementation, in my opinion.
Sadly, all that work happened before I discovered proper source control, or any real backup practices, and its all been lost. 

If you are ever interested in playing around with the Harry Potter PC games, there is now a [community-provided editor](https://www.moddb.com/games/harry-potter-and-the-sorcerers-stone) available that works much better than my earlier attempts.

So back to modern day. 
I started down on a bit of a rabbit hole with collecting source to old games, and one of the games I was able to find the full source code for, was the second Harry Potter game for PC! 
I played around with it a bunch, and it's all functional with source for scripts and assets. 
If you are interested, you can find it easily with a [quick Google search](https://www.google.com/search?q=archive+harry+potter+2+source).
I recommend you setup a Windows XP VM, and use Visual C++ 6.0 SP4. Again, [Google is your friend](https://www.google.com/search?q=archive+visual+cpp+6+sp5)

I will probably end up developing some extra tooling/features/content for HP2 in the future. 

So right about now, you're probably thinking "But Bishop, why are you talking about Unreal engine and John Carmack? You know Tim Sweeney wrote Unreal right?". 
Totally right, and thats what I'm getting to. 

After finding all this source code so easily available, I decided I wanted to read ALL OF IT. I wanted to know how everything worked. 
So I started looking at the oldest complete iteration of the Unreal engine source I have (v0.83, from 1996) with the idea that I should start at the bottom and work my way up to 
the more recent, more complex, engines. 

I got a little ways in before I realized that I needed to start somewhere more elemental, particularly because I'm not all that familiar with C or C++ (I usually work in Python for my day job).

So, I figured The Right Way, was to study the real master: John Carmack. If you're reading this, I think its safe to say you are probably aware that ID has released the source
for their first four engines under GPL, and these days it is [easily found on Github](https://github.com/orgs/id-Software/repositories). If not, you should check that out.

Sadly, John left ID software in 2011 to pursue more VR oriented games (oh yeah, checkout the Oculus Quest 2, and then check out all the ID games that have been ported by DrBeef!), and ID was subsequently bought up by Bethesda. 
As a result, they stopped publishing source to their engines, and I think that's a real bummer; these engines are an incredible learning resource and several generations of engineers got their start by learning from these engines.

(For the record, Bethesda seems to have done pretty well with the rebooted Doom franchise, as well as MachineGames' excellent Wolfenstein series, all of which are powered by engines evolved from Carmack's work)

Anyway, I started reading the code for Wolfenstein 3D, and while doing that I also searched around for accompanying documentation, and that's when I discovered [Fabien Sanglard](https://fabiensanglard.net).
Fabien has put a LOT of time into reviewing the code for the first four generations of ID engines, and it is a really educational read. I highly recommend reading all his code reviews. 
Fabien has also written the series of Game Engine Black Books, which I also highly recommend reading, as they go into even further detail than his code reviews.

Fabien mentioned Carmack's .plans were very interesting to read; he has a few PDFs of the compiled text, and I was also able to find a [Git repo with everything archived](https://github.com/ESWAT/john-carmack-plan-archive).

It really is quite interesting to read everything John was thinking as he researched and developed his engines. 
I just finished reading all of that yesterday, and now I think the best path forward is to read each of Fabien's code reviews, followed by the full source for that game, for each of the engines starting with Wolf3d.

I did take a break yesterday to setup Visual Studio 2022 (gaawd Windows is an awful OS), and follow through a C++/OpenGL tutorial. 
I had always avoided C++ thinking "oh that is too hard", but it really isn't as bad as I had expected. 
C++ syntax certainly leaves something to be desired in terms of readability, but I guess you get used to it.
I can see this easily sucking me down a rabbit hole for the foreseeable future.

