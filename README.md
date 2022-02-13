# swaybg with Multi Monitor support

swaybg is a wallpaper utility for Wayland compositors. It is compatible with any
Wayland compositor which implements the following Wayland protocols:

- wlr-layer-shell
- xdg-output
- xdg-shell

See the man page, `swaybg(1)`, for instructions on using swaybg.

## Description
This is a very poorly implementation of multi monitor support for swaybg, this project adds a flag to make swaybg able to span wallpapers across multiple screens.

There are some restrictions, this new flag will only work properly with:
- Two monitors with the same resolution horizontally placed 
- A wallpaper: heigth x 2 * width (3840x1080) 

If you meet these requirements, all you have to do is launch swaybg as follows:

```
swaybg -i Wallpaper.png -m multi-monitor
```

In my configuration DP-2 is my Left monitor and DP-1 is the Right one.
Your configuration may be different from mine and create some troubles, in this case try to play around with `display_counter` variable and `render_background_image` function.

### Compiling from Source

Install dependencies:

* meson \*
* wayland
* wayland-protocols \*
* cairo
* gdk-pixbuf2 (optional: image formats other than PNG)
* [scdoc](https://git.sr.ht/~sircmpwn/scdoc) (optional: man pages) \*
* git (optional: version information) \*

_\* Compile-time dep_

Run these commands:

    meson build/
    ninja -C build/
    sudo ninja -C build/ install

