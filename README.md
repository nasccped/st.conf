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

The [Suckless Terminal](https://st.suckless.org/) (aka **st**) is a
terminal emulator developed by the
[suckless.org community](https://suckless.org/).

It works the same as [Alacritty](https://alacritty.org/),
[Kitty](https://sw.kovidgoyal.net/kitty/) and many others, but it's
famous because of its simplicity and weightlessness.

## Get the program

First things first, here are some requeriments:

- `pkg-config`
- `JetBrains Mono Font`
- `xorg-libs`

> [!NOTE]
>
> The `xorg-libs` is a bunch of graphical/event libraries
> (_Xinerama_, _Xlib_, _..._) to run Xorg-based programs. You'll need
> to install the `pkg-config` by your own *package manager**, but the
> `xorg-libs` will be listed at my personal
> [dwm config repository](https://github.com/nasccped/dwm.conf). The
> JetBrains Mono font can be downloaded from the
> [original sources](https://www.jetbrains.com/lp/mono/).
>
> ---
>
> I will not talk about the obvious one such as the `C compiler` and
> `git`.

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

### config.def.h

- font
- cursor shape
- bordersize(pixel)

### patches

- [anysize](https://st.suckless.org/patches/anysize/)
- [blinking cursor](https://st.suckless.org/patches/blinking_cursor/)
