# Config


## Dual Boot Configuration
Generally aesthecially speaking I want the GRUB bootloader to be the main bootloader instead of the prebuilt windows one. Though, it isn't a big deal If it's not possible.

Windows installs just fine on my Laptop, spam F5 on reboot and go through the boot loader thingy.

https://ubuntu.com/download/desktop

Go for the not LTS version release but the absolute most latest version at the time of writing it was Ubuntu 23.10. This is because there was issues installing i3wm-gaps last time I installed, but it's probably been fixed by now.

https://www.youtube.com/watch?v=mXyN1aJYefc
https://askubuntu.com/questions/52963/how-do-i-set-windows-to-boot-as-the-default-in-the-boot-loader


## ROG Zephyrus GA502DU
https://ubuntuforums.org/showthread.php?t=2440670
https://github.com/gortbrown/ga502-ubuntu
https://gitlab.com/asus-linux/asusctl


## Ubuntu
https://github.com/i3/i3
https://github.com/yshui/picom
https://github.com/borisfaure/terminology
https://github.com/dylanaraps/neofetch
https://github.com/aristocratos/bashtop
https://github.com/powerline/powerline I think I used something else not sure forgot to document
https://github.com/derf/feh If I'm not mistaken I used feh to set the wallpaper

Wallpaper credit: https://twitter.com/dino_illus/status/1618947057192173568?t=iWFKlDRCUYe3LteniwmAjg


## WireGuard Configuration
https://github.com/pirate/wireguard-docs

I use wireguard as my way to connect to my raspberry pi

I want to subnet since I have two seperate networks that I want to manage
`Address = 10.10.26.1/25, 10.10.26.129/25`

For future you might want to look at this: https://docs.pivpn.io/wireguard/#pi-hole-with-pivpn


## Storage
For storage I wanted something that could both be accessible from both my laptop and desktop and something that I could access in a linux environment. I thought about using Syncthing for syncthing files across all devices, but decided against it, since I wanted it centralized.

I also wanted to try something new and seeing whether this is something that I will like better in the long run rather than syncthing.


### Installing OpenMediaVault
To install OpenMediaVault on the Raspberry Pi use this install script.
```
sudo wget -O - https://github.com/OpenMediaVault-Plugin-Developers/installScript/raw/master/install | sudo bash
```

You want to locate the IP address of your NAS since it has now changed. You do this by going to your default gateway and locating it that way.

You then want to login using these credentials.

```
username: admin
password: OpenMediaVault
```

look to change the password to something stronger after you log in.

I wiped my Hard drive and configured it to use EXT4 so that both windows and linux can use it. You need to set the auto logout timer to 1 day so that you can be sure the harddrive has actually wiped.

Created a shared folder named `TurtleNAS`

From there I enabled:
 - NFS (For Linux and Mac) with the client set as my local network subnet mask
 - SMB (For Windows)
 - Added the shared folder for both of these.

change the port as well because PiHole and a bunch of other things will use it.


### Windows 
To mount the NAS on windows you go to "Add a Network Location", and then type `\\{ip_address_of_NAS}\{shared_folder}` with both the `ip_address_of_NAS` and `shared_folder` being replaced by their respective counterparts.

Then you type the username and password of the user designated by OpenMediaVault.

