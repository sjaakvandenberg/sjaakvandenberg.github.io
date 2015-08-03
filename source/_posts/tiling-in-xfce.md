title: Tiling in XFCE
date: 2015-07-19 09:44:40
intro: A Python script to improve XFCE with custom tiling.
---
<img class="noshadow" src="xfce-mouse.svg" alt="XFCE logo">

> Xfce is a lightweight desktop environment for UNIX-like operating systems. It aims to be fast and low on system resources, while still being visually appealing and user friendly.

XFCE is awesome, and it has thousands of [themes](https://wiki.xfce.org/howto/install_new_themes) to allow you to make it look just the way you want it to. It's not as heavy on resources as [Gnome 3](https://www.gnome.org/gnome-3/), and not as nimble as [Openbox](http://openbox.org/wiki/Main_Page), but for me it strikes the perfect balance between aesthetics and performance.

XFCE is a stacking window manager, that treats windows like pieces of paper that can be stacked, like in Microsoft Windows or Apple Mac OS. There are also tiling window managers that are much lower on resources but usually don't offer the aesthetics of a stacking WM. ArchWiki has an extensive [list](https://wiki.archlinux.org/index.php/Window_manager).

## Custom Tiling in a Stacking WM

While Gnome does offer tiling extensions, I don't want that high of a resource burden. I like XFCE just fine, but the tiling features that it offers are a little lacking. XFCE 4.12 did introduce quarter screen corner tiling in addition to half screen tiling, but I'd like to define my own grid. On my laptop, I'd like to have my editor take up as much space as it needs for me to have a 100 character line length, and the rest is for my terminal. And I want to be able to tile or un-tile my windows to my grid using hotkeys. And I have no need for window decorations once a window is tiled, but want them back sometimes when it isn't.

## Python to the Rescue

![tiling.py](tiling.png)

I've written a [Python script](https://github.com/sjaakvandenberg/gtk-tiling) that does exactly that. Here is the grid I've defined in the XFCE Settings Editor under `xfce4-keyboard-shortcuts`.

```md
Property             Value
/commands/custom/... /home/user/Scripts/...
------------------------------------------------
<Super>Up            tiling.py 100 70 0 0 -d 0
<Super>Down          tiling.py 100 30 0 70 -d 0
<Super>Left          tiling.py 60 100 0 0 -d 0
<Super>Right         tiling.py 40 100 0 60 -d 0
<Super><Alt>Page_Up  tiling.py 28 50 0 0 -d 0
<Super><Alt>Left     tiling.py 28 50 0 50 -d 0
<Super>Page_Up       tiling.py 28 100 0 0 -d 0
<Super>Page_Down     tiling.py 72 100 28 0 -d 0
<Super><Alt>Up       tiling.py 74 74 13 13 -d 1
<Super><Alt>Down     tiling.py 100 100 0 0 -d 1
```

This gives me the following setup on my 1366 x 768 laptop:

```md
. . 400px . . . . . . . . . . 966px . . . . . . . .
.             .                                   .
.             .                                   .
.  terminal   .              editor               .
. 28% x 100%  .            72% x 100%             .
.             .                                   .
.             .                                   .
.             .                                   .
. . . . . . . . . . . . . . . . . . . . . . . . . .

. . 400px . . . . . . . . . . 966px . . . . . . . .
.             .                                   .
.  28% x 50%  .                                   .
.  terminal   .              editor               .
. . . . . . . .            72% x 100%             .
.             .                                   .
.  28% x 50%  .                                   .
.  terminal   .                                   .
. . . . . . . . . . . . . . . . . . . . . . . . . .

. . . . . . 820px . . . . . . . . . . 546px . . . .
.                            .                    .
.                            .                    .
.       editor/browser       .   editor/browser   .
.         60% x 100%         .     40% x 100%     .
.                            .                    .
.                            .                    .
.                            .                    .
. . . . . . . . . . . . . . . . . . . . . . . . . .

. . . . . . . . . . . 1366px. . . . . . . . . . . .
.                                                 .
.                      editor                     .
.                    72% x 100%                   .
.                                                 .
.                                                 .
. . . . . . . . . . . . . . . . . . . . . . . . . .
.               terminal  100% x 28%              .
. . . . . . . . . . . . . . . . . . . . . . . . . .

. . . . . . . . . . . 1366px. . . . . . . . . . . .
.    ================ 1011px ================     .
.    .                                      .     .
.    .                                      .     .
.    .        editor/browser/terminal       .     .
.    .               74% x 74%              .     .
.    .                                      .     .
.    ........................................     .
. . . . . . . . . . . . . . . . . . . . . . . . . .
```

This allows me to quickly tile a new window to the left 60% of my screen with <kbd>Super</kbd>+<kbd>Left</kbd>, open another one and tile it to 40% right with <kbd>Super</kbd>+<kbd>Right</kbd>.

If I want to move it, I can center the window and turn the window decorations back on with <kbd>Super</kbd>+<kbd>Alt</kbd>+<kbd>Up</kbd>, or hold <kbd>Alt</kbd> and drag it with my mouse.

## The Python Script

```python
#! /usr/bin/python2.7

# tiling.py
# Simple tiling for GTK

from gtk.gdk import *
import argparse

TITLE_BAR = 22  # Put the height of your title bar here

# Parse the command line arguments

parser = argparse.ArgumentParser(description="Simple tiling for GTK")
parser.add_argument("w", type=int,
                    help="Frame width (in percentage of screen width)")
parser.add_argument("h", type=int,
                    help="Frame height (in percentage of screen height)")
parser.add_argument("x", type=int,
                    help="Frame x coordinate (in percentage of screen width)")
parser.add_argument("y", type=int,
                    help="Frame y coordinate (in percentage of screen height)")
parser.add_argument("-d", type=int, choices=[0, 1], default=1,
                    help="1 for window decorations, 0 for none")
args = parser.parse_args()

win = window_foreign_new((get_default_root_window()
                          .property_get('_NET_ACTIVE_WINDOW')[2][0]))
state = win.property_get('_NET_WM_STATE')[2]

# Get the screen's width and height

screen_width = screen_width()
screen_height = screen_height()

# Calculate the frame dimensions and location in pixels

w = int(round(args.w / 100.0 * screen_width))
h = int(round(args.h / 100.0 * screen_height))
x = int(round(args.x / 100.0 * screen_width))
y = int(round(args.y / 100.0 * screen_height))

# Check whether decorations are desired

if args.d == 1:
    win.set_decorations(DECOR_TITLE)  # or DECOR_ALL for all decorations
    win.move_resize(x, y, w, (h - TITLE_BAR))
if args.d == 0:
    win.set_decorations(0)
    win.move_resize(x, y, w, h)

# Apply changes to window

window_process_all_updates()
flush()
```

To download, just copy/paste the thing, save the repo as a zip or run `git clone https://github.com/sjaakvandenberg/gtk-tiling.git`. You'll also need `python2`, and `pygtk`.

```md
$ ./tiling.py -h
usage: tiling.py [-h] [-d {0,1}] w h x y

Simple tiling for GTK

positional arguments:
  w           Frame width (in percentage of screen width)
  h           Frame height (in percentage of screen height)
  x           Frame x coordinate (in percentage of screen width)
  y           Frame y coordinate (in percentage of screen height)

optional arguments:
  -h, --help  show this help message and exit
  -d {0,1}    1 for window decorations, 0 for none
```

Make sure to give the script executable permissions with `chmod +x tiling.py`. To see it in use, here's a [video walkthrough](https://vimeo.com/133853415).

Happy tiling!
