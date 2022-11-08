# 1. Create and Configure a Virtual Machine

## 1.1 Creation
## 1.2 Extra Configuration
## 1.3 Setting up SSH
## 1.4 Plugging in Arch ISO
# 2. Start the VM
# 3. Keyboard
4. Extra packages needed
5. Which is my IP?
## 5.1 Start ssh daemon
## 5.2 Password for the ISO's root user
## 5.3 The IP
6. ```ssh``` from terminal
7. sync Network Time Protocol
8. ```reflector```, mirror list, fastest server available AKA Refresh the servers with ```pacman -Syy```
## 8.1 Get the best servers (reflector)
Recorda explicar os flags:

```-c```
```-a```
```--sort rate```
```--save <mirror-list-directory>```
## 8.2 Refresh servers
Recorda explicar os flags:

```-S``` or ```--sync```
```-y ```or ```--refresh```
# 9 Disks and partitions
## 9.1 Check status
## 9.2 Partitions for a EFI system
## 9.3 gdisk, utility to create GPT Tables
# 10 Formating partitions
# 11 Mounting partitions
## 11.1 ```sda1```
## 11.2 ```sda2```
# 12 Installation of the base packages to ```/mnt``` with ```pacstrap```
# 13 Generating the FileSystem Table (```fstab```)
Recorda explicar o flag:

```-U```:
# 14 Enter the installation AKA Chroot in with arch-chroot ```/mnt```
# 15 Create a 2GB swap file
## 15.1 A 2GB swap file
## 15.2 Permissions
## 15.3 Formatting as swap
## 15.4 Activating the ```/swapfile```
## 15.5 Generating its FileSystem Table Entry (```fstab```)
# 16 Timezone
## 16.1 What's my timezone (GOTCHA)
## 16.2 Setting the timezone
Recorda explicar os flags:

```-s``` or ```--symbolic```
```-for``` or ```--force```
## 16.3 Syncing the HW Clock & the System Clock
## 16.4 Setting which locales to be generated
Recorda explicar:

Qué é un locale.
## 16.5 Generating the locales
## 16.6 ```/etc/locale.conf```
## 16.7 ```/etc/vconsole.conf```
# 17 The ```/etc/hostname``` file
# 18 The ```/etc/hosts``` file
´´´
127.0.0.1   localhost
::1         localhost
127.0.1.1   <hostame>.localdomain    <hostname>
´´´
# 19 A password for the ```root``` user
# 20 Bootloader & some moar packages
Instala e explica brevemente que fan os seguintes paquetes:

grub
efibootmgr
networkmanager
network-manager-applet
dialog
os-prober
mtools
dosfstools
base-devel
linux-headers
cups
reflector
openssh
git
xdg-utils
xdg-user-dirs
virtualbox-guest-utils
# 21 Installing and setting up ```grub```
## 21.1 Installing grub
## 21.2 Configuring grub
# 22 Enabling some services
## 22.1 ```NetworkManager```
## 22.2 ```sshd```
## 22.3 ```cupsd``` (GOTCHA)
# 23 Create a new user
## 23.1 Creation
Recorda explicar:

O grupo ```wheel```.
O flag ```-m```.
O flag ```-G```.
## 23.2 Password
## 23.3 ```sudo``` privileges
Recorda explicar o comando ```visudo```, por qué é importante e a que ficheiro afecta.

# 24 EXIT the installation!!!!
# 25 Unmounting and Rebooting
## 25.1 ```umount``` all the partions
## 25.2 Reboot
# 26 Log into Arch ...and check if we have an IP
# 27 ```ssh``` into the VM ...again
# 28 Desktop environment
## 28.1 Installation of xfce4
Instala e explica brevemente que fan os seguintes paquetes:

```xf86-video-vmware```
```xorg```
```lightdm``` and ```lightdm-gtk-greeter```
```xfce4``` and ```xfce4-goodies```
```materia-gtk-theme``` and ```papirus-icon-theme```
```firefox```... Vale... Este no fai falla que o expliquedes 🥳
## 28.2 Enable ```lightdm``` display manager
## 29 Exit ssh and reboot
# 30 Moar (EXTRA!!! 💰💰💰)
## 30.1 Install ```nano```
```
$ pacman -S nano
```
## 30.2 Install some other desktop environment (you know which 😙)