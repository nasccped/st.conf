ST (Suckless Terminal) config
=============================

My personal configurations for ST (Suckless Terminal) program 💻

> [!WARNING]
>
> This isn't the official README!
>
> The old README can be found at `README.old.txt` file. All content
> this page bellow was written by me!

## What's the Suckless Terminal?

The [Suckless Terminal] (aka **st**) is a terminal emulator developed
by the [suckless.org community].

[Suckless Terminal]: https://st.suckless.org/
[suckless.org community]: https://suckless.org/

It works the same as [Alacritty], [Kitty] and many others, but it's
famous because of its simplicity and weightlessness.

[Alacritty]: https://alacritty.org/
[Kitty]: https://sw.kovidgoyal.net/kitty/

## Get the program

First things first, here are some requeriments:

- `pkg-config`
- `Iosevka font`
- `xorg-libs`

> [!NOTE]
>
> The `xorg-libs` is a bunch of graphical/event libraries
> (_Xinerama_, _Xlib_, _..._) to run Xorg-based programs. You'll need
> to install the `pkg-config` by your own *package manager**, but the
> `xorg-libs` will be listed at my personal [dwm config repository].
> The Iosevka font can be downloaded from the
> [Iosevka official repository].
>
> ---
>
> I will not talk about the obvious one such as the `C compiler` and
> `git`.

[dwm config repository]: https://github.com/nasccped/dwm.conf
[Iosevka official repository]: https://github.com/be5invis/Iosevka

Follow these steps...

1. Clone the repo, `cd` into it and remove git folder:

```sh
git clone https://github.com/nasccped/dwm.conf && \
cd dwm.conf && \
rm -rf .git/
```

2. Install the `pkg-config` and `xorg-libs`

3. Build the program with root privileges:

```sh
make clean && sudo make install # you'll need to be sudo + enter your pass
```

4. Congrats. You now have the **st** program 🎉🎉🎉

## Changes that I've done (or patches added)

### manual changes

- font
- cursor shape
- bordersize(pixel)
- zoom in/out/reset (manual changes at `config.def.h`, check the
  **Extra** section)
- tabspaces (from 8 to 4)
- colors (using `#define` at **config.def.h**)

### patches

- [anysize]
- [blinking cursor]
- [boxdraw] _(read [Boxdraw patch])_

[anysize]: https://st.suckless.org/patches/anysize/
[blinking cursor]: https://st.suckless.org/patches/blinking_cursor/
[boxdraw]: https://st.suckless.org/patches/boxdraw/
[Boxdraw patch]: #boxdraw-patch

## Extra

Extra info about my config!

### Cursor style

I've defined my mouse cursor as blinking underline both in `st` and
in `bash PS1`. You can set these values as you want by modifying the
`config.def.h` file (before make building or just `config.h` after
make building).

I've also applied the [unfocused cursor patch]. It's applied by
commenting a `XftDrawRect` function at `x.c` file _(within the
xdrawcursor function)_.

[unfocused cursor patch]: https://st.suckless.org/patches/unfocused_cursor/

### Border pixel

I've setted my `st` border pixel to 4. After using `anysize` patch,
the terminal background color escaping (i.e., neovim) was looking
wrong (about border dimension). Setting boderpixel to a bigger value
can solve this problem!

### Zoom shortcuts

Like other terminal emulators, `Ctrl` | `Shift` with the _plus_ or
_minus_ sign can increase or decrease the font dimension rendering
(zoom in/out). I came from **WindowsPowershell** and **Alacritty**.
This change is very helpfull for common workflows. Here are my
changes:

1. Zoom in:
    - `Ctrl` + `=` (non numeric keyboard)
    - `Ctrl` + `+` (from numeric keyboard)
2. Zoom out:
    - `Ctrl` + `-` (non numeric keyboard)
    - `Ctrl` + `-` (from numeric keyboard)
3. Zoom reset:
    - `Ctrl` + `0` (not numeric keyboard)

### Boxdraw patch

Boxdraw is a patch for st that can fix the
[box-drawing characters] display _(making more precise and
font-independent)_. It's added to the program by a patch but will
only be enabled if the **config.def.h** variable is true:

[box-drawing characters]: https://en.wikipedia.org/wiki/Box-drawing_characters

```c
/* Set this value to 0 to disable boxdraw feature */
const int boxdraw = 1;
```

Also, boxdraw characters can sometimes be bold and it can broke the
boxdraw feature, so I've disabled it: (also **config.def.h**)

```c
/* Set this value to 1 to enable boxdraw feature on bold */
const int boxdraw_bold = 0;
```
