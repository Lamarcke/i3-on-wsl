# i3-on-wsl
Custom i3 config that "just works" for WSL2

## Why?
I wanted to have a WM setup for my development work (i really like using the keyboard), so i wanted to have WSL low overhead (and really great performance) instead of a full VM.

If for some reason you need to use i3 directly on WSL2, this is the config for you.


## What does this fixes?
For some reason, the default i3 installation doesn't work well in WSL, the config is generated on the first run, and the status bar appears. After that, you simply get a black screen (you can still open the d-menu and terminals, but the status bar doesn't work anymore)  

I couldn't find a fix for it, no matter how much i searched (DE/WMs in WSL are not that popular, too.  
However, the config at [i3-starterpack](https://github.com/addy-dclxvi/i3-starterpack) works. It also provides some niceties (like wallpapers, compton).  
So i used it as base.

I also made some changes relative to usage in WSL2 (removed unused icons in the status bar), increased font size (to 12), and changed most (if not all) keybinds to i3 defaults. We are also using Kanagawa colors (though there's not much to color), with an optional Kanagawa wallpaper.

# Installation
I highly recommend using [GWSL](https://opticos.github.io/gwsl/) to setup your X-Server.  

While this tutorial is based on Ubuntu, it should work with any WSL distro, just use your native package manager.  

Install all packages mentioned in [i3-starterpack](https://github.com/addy-dclxvi/i3-starterpack).  
For this, just run these commands:  
`sudo apt install i3`  
To be safe:  
`sudo apt install i3-wm dunst i3lock i3status suckless-tools`  

And the extra packages:
`sudo apt install compton hsetroot rxvt-unicode xsel rofi fonts-noto fonts-mplus xsettingsd lxappearance scrot viewnior`

Check [i3-starterpack](https://github.com/addy-dclxvi/i3-starterpack) README for a detailed description of the extra packages.

I highly recommed installing xfce4 and it's goodies as extra packages, otherwise you get no file manager, settings screen, etc.  
To install it:
`sudo apt install xfce4 xfce4-goodies`

Clone/download this repo and open "paste-in-home", copy everything there to your home directory (`~` or `/home/your-username`).  
This will overwrite your i3 config. You can also do it step by step by copying each file and seeing what it's doing, it's your call.

Run this to start i3, or use GWSL shortcut if you want to:
`exec i3`

## Customizing

### Use alt as mod key
If you are planning to use this in a window, and not in full screen with exclusive keybinds (see below), make sure that you change the default `$mod` key to Alt.

To do this, head over to `paste-in-home/.config/i3/config` using any text editor, and change these:  
`$mod` to `Mod1` (which is Alt)
`$alt` to `Mod4` (which is the Windows key)

I still highly recommend using this with exclusive keyboard access (see below), i3 was not made to be run as a simple window.

All i3 related settings are stored in `.config`, in the respective folders. You can customize i3status to your liking, too.

# Exclusive keyboard access
This tutorial is for VcXsrv. Either with GWSL or directly.

Basically, run VcXsrv with these flags:
`path-to-vcxsrv/vcxsrv.exe -br -swcursor -keyhook -fullscreen`

The most important bits here are `-fullscreen`, which runs your XServer in a fullscreen window, and `-keyhook`, which runs it with exclusive access to your keyboard.

If you are on GWSL, right-click on GWSL icons on the traybar > XServer Profiles > Add a profile  
Give it a name and add these flags:  
`-br -swcursor -keyhook -fullscreen`

This solution is not perfect, however.  
As with VMs, a lot of the Windows keyboard shortcuts (like Win+G for GameBar, Win+L for logout, Alt+F4 to close, Alt+Tab to change windows) will still work, so please be mindful of them. I'm still looking for ways to improve this workflow and i wil update this repo accordingly.


## Final result
![image](https://user-images.githubusercontent.com/23425058/206305326-e753431a-27a3-4075-a0f7-638e84ec2e80.png)
