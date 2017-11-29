# CubieDLNA
Install Debian Stretch on CubieBoard 2 - setup MiniDLNA, SMB, NFS and pi-hole

## Install Armbian
Download latest debian **server** image from the Armbian project: https://www.armbian.com/cubieboard-2/

At the time of writing this it is Debian 9.2 Stretch: https://dl.armbian.com/cubieboard2/Debian_stretch_next.7z

Unpack and write to sd-card using Win32DiskImager: https://sourceforge.net/projects/win32diskimager/

Plug into CubieBoard and waaaiiittt.

When device is booted, connect using shh. Username: **root** - Password: **1234**

Follow instructions to change password and create new user - Username: **cubie**

Run 
```
sudo armbian-config
```
to change timezone etc.

Update installed packages using 
```
sudo apt-get update && sudo apt-get upgrade
```

## Mount HDD
Find **UUID** of HDD using
```
sudo blkid
```
Find **UID** and **GID** of **cubie** user using
````
id
````
Edit file table to auto mount on reboot using
````
sudo nano /etc/fstab
````
Add the following line to the end of the file
````
UUID=[UUID_from_above] /media/hdd ntfs uid=[UID_from_above],gid=[GID_from_above],dmask=0000,fmask=0000 0 0
````
Create the mount directory
````
sudo mkdir /media/hdd
````
Mount and verify using
````
sudo mount -a
df -h
ls -l /media/hdd
````

## Install MiniDLNA (ReadyMedia)
Find out latest version of MiniDLNA using
```
apt-cache policy minidlna
```
Install latest version using
```
sudo apt-get install minidlna=[version_from_above]
```



## Podget
sudo dpkg -i podget_<version>_all.deb


run podget
rm -R POD/

crontab -e

15 04 * * * /usr/bin/podget -s

