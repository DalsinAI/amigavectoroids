Vectoroids 1.1.2 for AmigaOS 3.x
================================

Vectoroids (Bill Kendrick, New Breed Software), the vector asteroids game:
steer your ship through the rocks over a Voyager photograph of Jupiter,
shoot them into smaller and smaller pieces, an extra ship every 10,000
points; quit any time and carry on later. For AmigaOS 3.x on a 68040 or
68060 with an FPU and an RTG screen, on OpenGPU's SDL 2.

Base: vectoroids_1.1.2.orig.tar.xz from Debian (sha256
1698bab62ed8c532cebf23fb6b46461a1bcb7945e43ee425c93fb6c5a788896e), with
Debian's patches (1.1.2-1, its makefile) as the second commit. Branch
team2/vectoroids-amiga.

Status: plays in the lab (Instance-45 on GFOpenUp 0.8.19, 6 November
2026): the title, Start, level 1 (the ship turned, thrusting and firing,
the rocks drifting), Escape back to the title, Escape again back to the
Shell, and a second start with Continue picking the game up where it was
left; vectoroids-state written in the drawer. The lab is muted, so the
music and sounds were not heard there.


What you need
-------------

- A 68040 or 68060 with an FPU, AmigaOS 3.x, an RTG card (or the
  AmigaChrome lab).
- GFOpenUp 0.8.18 or later: LIBS:OpenGPU/SDL2.module, SDL2_image.module
  and SDL2_mixer.module.


How to play
-----------

Open the Vectoroids icon, or run Vectoroids from a Shell. It opens a
640x480 window (Vectoroids --fullscreen for the full screen, --nosound
for none). Click Start (or Continue) on the title screen. Left and right
turn the ship, Up thrusts, Space fires, Shift brings a new ship in;
Escape goes back to the title, and Escape there quits. A joystick works
too. ReadMe-upstream in the drawer is upstream's README. The pictures,
sounds and music are in the drawer's data/; the high score and the game
left off are vectoroids-state in the drawer.


Building
--------

    make -f amiga/Makefile.amigaos -j2 dist

with GFOpenAmigaGCC 16.2.0-open4, the OpenNDK headers and the OpenGPU kit
(see the Makefile's head). The drawer is dist/Vectoroids (and
dist/Vectoroids.info).


What was changed
----------------

- vectoroids.c: main() first moves into the drawer and deals at exit with
  the screens OpenGPU's SDL2.module can leave after a full screen game
  (amiga/amiga_start.c and amiga/amiga_screens.c, from the Legend of
  Edgar port); the high score and the game left off are
  PROGDIR:vectoroids-state.
- amiga/Makefile.amigaos builds upstream's vectoroids with its sound and
  joystick settings, the data at PROGDIR:data/, on the kit's SDL2,
  SDL2_image and SDL2_mixer.
- amiga/stack.c: 256 KB of stack.


Licences
--------

Vectoroids: GPL 2 or later (COPYING.txt). Its data, as upstream's README
credits it: the Jupiter picture is NASA's Voyager 1 photograph (public
domain); the sounds come from free sound-effect archives; the music,
"Decision" (decision.s3m), is by Mike Faltiss (Hadji, Digital Music
Kings), 1995. The Amiga files (amiga/): the AmiCradle Team, GPL 2 or
later; the icon is upstream's data/images/icon.png.
