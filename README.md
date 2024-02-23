# Config


## Dual Boot Configuration
Generally aesthecially speaking I want the GRUB bootloader to be the main bootloader instead of the prebuilt windows one. Though, it isn't a big deal If it's not possible.

## Windows Setup

## Ubuntu Setup


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

### Windows 
To mount the NAS on windows you go to "Add a Network Location", and then type `\\{ip_address_of_NAS}\{shared_folder}` with both the `ip_address_of_NAS` and `shared_folder` being replaced by their respective counterparts.

Then you type the username and password of the user designated by OpenMediaVault.

