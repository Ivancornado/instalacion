# Definiciones:
EFI: son las siglas de Extensible Firmware Interface y es un estándar que pretende sustituir a la BIOS, el sistema de arranque que se ha venido utilizando en los PCs desde sus inicios. El sistema EFI utiliza varios sensores para detectar el estado del motor y el estado del vehculo en marcha. Y la ECU del motor calcula el volumen de inyeccin de combustible ptimo y provoca que los inyectores lo inyecten.

UEFI: es el acrónimo de "Unified Extensible Firmware Interface" o "Interfaz de Firmware Extensible Unificada". Es el firmware sucesor, escrito en C, del BIOS, sistema al que empezó a suceder a partir del año 2005, 30 años después del nacimiento de la BIOS.

BIOS: La BIOS pone las funciones básicas de un ordenador a disposición del usuario. Al encenderlo, comprueba si las partes más importantes son funcionales, como la memoria, la CPU y otros componentes de hardware. Esta prueba se denomina autoprueba de arranque o power on self test (POST).

GPT: La tabla de partición GUID (GPT) es un nuevo estilo de partición que forma parte de la especificación de interfaz de firmware extensible unificada (UEFI). Esto se utiliza para instalaciones de fábrica con Windows 8, 8.1 y 10 para mayor flexibilidad de partición y más funciones avanzadas de Windows.

MBR: o master boot recordes el primer sector físico de un portador de datos (por ejemplo, un disco duro, una memoria USB) que se utiliza para arrancar (iniciar) los ordenadores. Para esto, el ordenador debe disponer de un BIOS y un sistema operativo x86.

GUID: El identificador único global, en inglés: globally unique identifier (GUID) es un número pseudoaleatorio empleado en aplicaciones de software. El GUID es una implementación de Microsoft de un estándar llamado universally unique identifier (UUID), especificado por la Open Software Foundation (OSF).

UUID:Son las siglas de Universally Unique IDentifier, que en inglés significa, literalmente, 'identificador único universal'. Como tal, el UUID es un código identificador estándar empleado en el proceso de construcción de software.
# 1. Create and Configure a Virtual Machine
## 1.1 Creation
Vamos a crear una maquina Arch, para eso seguiremos estos pasos en VirtualBox:

Paso 1: Insertar un nombre para la maquina, sistema operativo y versión del sistema operativo:

![nombre](./capturas-arch/nombre.PNG)

Paso 2: Seleccionar tamaña de la memoría RAM (en este paso dejaremos suficiente espacio para la maquina real).

![memoria](./capturas-arch/memoria.PNG)

Paso 3: Indicaremos que queremos reservar el disco dinamicamente (Con esto evitaremos acaparar espacio del disco real que no contiene información).

![](./capturas-arch/formatodisco.PNG)

Paso 4: Seleccionaremos como formato de disco VDI.

![](./capturas-arch/disco2.PNG)

Paso 5: Selecionamremos el tamaño del disco duro que necesitamos.

![](./capturas-arch/tamdisco.PNG)

## 1.2 Extra Configuration

Unha vez tenemos la maquina creada en VirtualBox tendremos que configurar sus parametros y insertar la ISO de instalación.

Paso 1: Seleccionamos los núcleos del procesador real que queremos usar para la maquina virtual.

 ![config](./capturas-arch/config1.PNG)

Paso 2: Aumentamos a memoria de vídeo al maximo permitido y cambiaremos el controlador gráfico por VBoxSVGA.

![config](./capturas-arch/config2.PNG)

Paso 3: Insertamos la ISO en el apartado almacenamiento.

![config](./capturas-arch/config3.PNG)

Paso 4: Cambiamos la configuración de red a Adaptador puente.
![config](./capturas-arch/config4.PNG)

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