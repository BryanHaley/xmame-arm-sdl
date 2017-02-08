 *********************
 XMAME-ARM-SDL README
 *********************
 
 **BUILD**
 
 The instructions for building and running xmame-arm-sdl are almost the same as [xmame-arm](https://www.anavi.org/article/204/).
 
 1. Open the terminal
 2. Install necessary packages
 
 `sudo apt-get update`
 
 `sudo apt-get install -y build-essential libgtk2.0-dev libgnome2-dev libsdl1.2-dev libxv-dev libxv1 git`
 
 3. Clone this repository
 
 `git clone https://github.com/BryanHaley/xmame-arm-sdl.git`
 
 4. Build the executable (this may take several hours)
 
 `cd xmame-arm-sdl`
 
 `make`
 
 **RUN**
 
 Run games the same way you would MAME 0.106 via the command line. Theoritically, it may even be compatible with existing MAME front-ends, provided they can be successfully built on armhf Debian. I have not tested any at this time.
 
 You can download a free, noncommercial ROM from mame.net to test. For example:
 
 `cd ~/xmame-arm-sdl`
 
 `wget -P roms www.mame.net/roms/supertnk/supertnk.zip`
 
 To run it:
 
 `./xmame.SDL ./supertnk.zip`
 
 Many of the commandline arguments for MAME 0.106 *should* work. Run './xmame.SDL -help | more' to see them.
 
 Of particular note:
 * Use `-fullscreen` to run the game in fullscreen mode.
 * Use `-scale <int>` (e.g. '-scale 2') to scale the display (see known issues).
 * Use `-fsr 1` to enable the enhanced frameskipper. This can reduce slowdown in some games.
 * Use `-joytype 5` to enable the usage of SDL-compatible gamepads/controllers/etc.
 
 So, for example:
 
 `./xmame.SDL -fullscreen -fsr 1 ./supertnk.zip`
 
 Or, if you have a large enough display (e.g. over VGA or HDMI):
 
 `./xmame.SDL -fullscreen -scale 2 -fsr 1 ./supertnk.zip`
 
 **KNOWN ISSUES**
 
 * Sound is relatively quiet by default. Turn your volume up and/or boost the volume within MAME. I will investigate a better fix later.
 * Scaling the game display to a higher resolution than your CHIP is running at will cause an exeption. In addition, currently the game display can only scale by integer values. This is particularly a problem on composite displays, as most games run at a resolution just slightly higher than half the CHIP's resolution, meaning they cannot be scaled up and also only take up a relatively small amount of the screen (see planned features). Therefore, use VGA or HDMI if possible.
 
 **PLANNED FEATURES**
 
 * Allow non-integer display scaling. Though not ideal as it may make images blurry, this will improve compatibility greatly with composite displays.
 * Add the ability to use buttons connected to GPIO pins as in-game inputs.

 *********************
 ORIGINAL XMAME/XMESS README
 *********************

 Quick Readme by Matt Lowry
 Last Updated : 12th April 2001

Q: What is xmame?
Q: What is xmess?

A: Xmame/xmess is the Unix and Unix-like port of the highly esteemed MAME/MESS
   system.


Q: What is MAME/MESS?

A: MAME stands for Multi Arcade Machine Emulator. As the name suggests, it is
    a program that emulates the hardware (and low-level firmware) of a massive
    variety of arcade machines.
   MESS stands for Multi Emulator Super System. It is an emulator for the
    hardware of many different games consules (e.g. Sega, NES, SNES, etc.)
    as well as many different old games-oriented home computers (e.g. C64,
    C128, ZX80, etc.)
   While the two programs are conceptually different, and have different
    development teams, they share a lot of code and are distributed together.


Q: I'm interested! Where can I get more info?

A: You will find documentation (of sorts) in the doc/ subdirectory.
   You will probably want to go straight to the xmame/xmess doco:
     doc/xmame-doc.lyx  -> Source LyX file.
     doc/xmame-doc.html -> Top level page for HTML version.
     doc/xmame-doc.sgml -> For those suitably persuaded.
     doc/xmame-doc.ps   -> Here's some Postscript we prepared earlier ...
     doc/xmame-doc.txt  -> Plain old boring text.
   Don't be fooled by the name, the above doco is for _both_ xmame and xmess.

   There are also some Unix man pages:
     doc/xmame.6
     doc/xmess.6

   There are various other files in the doc/ directory that contain information
    you may find interesting or useful.

   Also you can check out the xmame/xmess homepage at:
                       http://x.mame.net
    (Deutsche version: http://x.mame.net/german.html)


Q: How do I compile XMAME/XMESS?

A: The documentation (doc/xmame-doc.*) contains detailed instructions, 
    including extra notes specific to particular hardware/OS combinations.
   READ THE DOCUMENTATION FIRST!
   Then edit the Makefile (it contains lots of helpful hints).
   Then run make.
   No, there is no configure script. Feel free to write one yourself and
    contribute it to the project. :)

Q: What platforms can I run XMAME/XMESS on?

A: Lots! :)
   Currently the following CPU bases are explicitly supported in the Makefile:
   i386  /  ia64   /  alpha  /  m68k  /  risc (various flavours)

   The following OSes are also explicitly supported:
   Linux / FreeBSD / NetBSD / OpenBSD / Solaris / NeXT / MacOS-X / IRIX / AIX

   The following display methods are explicitly supported:
   X11(R6) / SVGAlib (Linux only) / GGI (only tested on Linux) / 
   XGL (i.e. X with OpenGL) / XFX (i.e. X with 3Dfx) / 
   SVGAfx (i.e. SVGAlib with 3Dfx) / OpenStep / SDL / Photon2

   If your OS is not listed above, then there is also a "generic unix"
    compilation target that may work for you.
   The display method of choice is X11. If you have an X server on your
    system the xmame/xmess will talk to it. The other display methods are
    aimed at improving the framerate the xmame/xmess runs at, but may not
    be available on your system.


Q: When I tried compiling <xyz> went wrong. Help?

A: Read the documentation. In particular the section of the main documentation
    that discussed compilation.


Q: OK, I've got the source and compiled it. How do I run a game?

A: Xmame/xmess are __emulators__. They make the hardware in front of you
    (an X86 box, say) pretend to be the specialist hardware that arcade
    machines contain. In this way the original game code can run on your
    PC. So to play a game you need that original game code as well.
   The documentation discusses this matter in some detail.


Q: I've got more questions!

A: Read the documentation. :)


