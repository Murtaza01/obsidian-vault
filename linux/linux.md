# nmtui

For network managing, its a UI in the command line that manages your networks

# pavucontrol

a GUI for managing sound system

# Alias
to add alias in linux you edit the `.bashrc` and add your alias
then you should use the source .bashrc everytime you open the 
terminal, which you can do with editing the .bash_profile and adding 
source .bashrc

# [autologin with lightMD](https://wiki.archlinux.org/title/LightDM#Enabling_autologin)

# xsetroot

to change the background color, we use it like this:

```zsh
 xsetroot -solid "ccc"
```

# feh 

we use it to add background image and to view images from terminal

```zsh
 feh --bg-scale /usr/shar/backgrounds/bg.png
```

# change curser 

we can do that with the lxappearance package, which is a gui that manages several things
like the border colors and style and courser style.

in order to download a new curser theme we simply download it using a site like 
gnome-look and pick any curser, then move this folder to /usr/share/icons
which is where curser would be located

in there we will find a default folder that will contain a index.theme which will have
a inheart that will be the current curser, change this name to whatever curser you downloaded

# extracting tar files

we can do that with the following command:

```zsh
 tar -xfv <name>.tar.xz
```

where;

x == extract
f == file
v == verbose

# rofi

rofi is a application lancher we just like dmenu

there is a github page with pre-configured styles to rofi
we can use it instead of the default one, it essetionally 
has a launcher that we can open and that would be the app 
instead of rofi, so in i3 configration its something like this:

```zsh
 bindsym $mod+d exec /home/Mertda/.config/rofi/launchers/type-3/launcher.sh 
```

that code will exectue the lancher weich is rofi with styles

# xautolock

is a package that runs programs when there is no user activity,
it essentionally track the mointer to see if there is any activity

we can use it to run a lockscreen app, for example xscreensaver like this:

```zsh
 xatuolock -time 10 -locker xscreensaver -activie
```

# wget

is a package for donwloading files using a url, it is similar to curl, you can
use it to download things.

> wget2

the better and faster version 

# timeshift

a tool that takes snapshots of the file system so that you can roll back to an earlier 
version

# pandoc

a tool that can convert file types, such as pdf epub and md.

it needs lots of [tex_live](https://wiki.archlinux.org/title/TeX_Live) dependences
in order to work

> convert md to pdf

``` zsh
pandoc MANUAL.md -o example13.pdf
```
# yay: error fetching object file is empty 

this problem happens when the yay package crashes while installing a package or updating
to fix this we would first remove the package from the yay folder manually from

~/.cache/yay/package_folder

this folder is where yay download packages from, so it would keep a .git folder that
will give us this problem

# cloudflare [Warp](https://developers.cloudflare.com/warp-client/get-started/linux/)

a tool to change your that hides your DNS, it is similar to a vpn.

in arch you need the [AUR](https://aur.archlinux.org/packages/cloudflare-warp-bin)

we also need to enable or lunch the service 

```zsh
sudo systemctl enable --now warp-svc.service
```

this however will keep it running in the background so you need to disable it later


# show disk usage

we can do that with the command

```zsh
du --summarize --human-readable *
// OR
du -sh *
```

du == disk usage

# libreoffice

we can use the libreoffice command to convert odt to pdf

``` zsh
libreoffice --convert-to pdf *.odt
```
