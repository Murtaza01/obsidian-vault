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
