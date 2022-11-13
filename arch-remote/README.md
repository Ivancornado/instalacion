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

## 1.3 Configuración del teclado
Al iniciar la máquina, nos encontraremos dentro de la ISO de instalacin, donde recoge algunos recursos para instalar el SO.

El problema que tendremos es que tendremos el teclado estara en una distrubucion que no es la española, para cambiarlo usaremos el comando:
```
loadkeys es
```

## 1.4 Intalación y configuración SSH
Lo siguiente que haremos, sera instalar el ```openssh```, para que la instalacion se dificulte lo menos posible, y podamos copiar los comandos, y reflector nos servira para que la lista de servidores de replica estea actualizada.

```
pacman -Syy reflector openssh
```
Y lo iniciaremos:

```
systemctl start sshd
```

Ahora, miraremos la ip de la máquina, ya que necesitaremos su IP para realizar el ssh:
```
ip a
```

Ahora, estableceremos una contraseña para root, para el ssh, y evitar editar ficheros:
```
passwd root
```

Abriremos un terminal (en mi caso PuTTY), y pondremos el comando para realizar el ssh como root, en este caso usaremos root, ya que no tenemos un usuario creado:
```
ssh root@[ip de la maquina]10.0.8.99
```

Esto nos permitira conectarnos remotamente a la máquina, lo cual nos facilitara la instalacion.

## 1.5 Timedatectl
A continuación, miraremos si el reloj esta sincronizado (por lo general no lo esta):
```
timedatectl set-ntp true
```

## 1.6 Refrescar servidores
Ahora, refrescaremos los servidores con ```reflector```
```
reflector -c Spain -a 10 --sort rate --save /etc/pacman.d/mirrorlist
```

## 1.7 Particionar discos con ```lsblk```
Antes de particionar, debemos ver los discos que tenemos, el comando para ello es:
```
lsblk
```

## 1.8 Crear particiones con ```gdisk```
Ahora crearemos las particiones con gdisk, para ello usaremos el siguiente comando, donde elegiremos el tipo de particion, que será EFI, en ese menu sera ef00:
```
gdisk /dev/sda
```

![gdisk](./maquina/crear%20particiones.jpeg)

Como se pode ver na captura anterior faremos duas particions:
Partición 1:
```
-Partition number: 1 (indicamos que estamos creando la partición 1).
-First sector: (Indicamos el sector no que comezará la partición, en este caso seleccionamos el sector por defecto).
-Last sector: (Como queremos crear otra partición indicamos que requerimos solo 200 MB)
Hex code or GUID: (Como queremos crear una partición EFI escribimos ef00)
```

Partición 2:
```
-Partition number: 1 (indicamos que estamos creando la partición 2).
-First sector: (Indicamos el sector en el que comezará la partición,  seleccionamos el sector por defecto).
-Last sector: (Como solo haremos dos particiónes indicaremos que ocupe el resto del discomo marcando o ultimo sector).
Hex code or GUID: (Indicaremos el codigo 8300 que se corresponde con Ubuntu).
```

## 1.9.1 Creación carpetas para montar particiones.
Primeiro debemos formatear las particiónes:

Formato partición 1:
```
mkfs.fat -F 32 /dev/sda1
```
Formatearemos a partición en FAT32

Formato partición 1:
```
mkfs.ext4 /dev/sda2
```
Formatearemos a partición en EXT4

### 1.9.2 Montar carpetas
Ahora montaremos las particiones 

Montaje partición 2:
```
mount /dev/sda2 /mnt 
```
Para montar la partición 1 precisamos crear la carpeta
```
mkdir -p /mnt/boot
```

Montaje partición 2:
```
mount /dev/sda1 /mnt/boot
```

Por ultimo haremos ```lsblk``` para confirmar que están bien montadas.

![montaje](./maquina/lsblkconparticionescreadas.PNG)

## 1.10 Instalar firmware de vim.
E instalaremos el firmware de linux y vim:
```
pacstrap /mnt base linux linux-firmware vim
```
## 1.11 Generar ```fstab```
Ahora generaremos el archivo fstab para quedefina las UUID de los discos:
```
genfstab -U /mnt  
```
```
/mnt/etc/fstab
```

# 2.0 Configuración del sistema operativo instalado
Ahora entraremos, al sistema operatvo que hemos instalado:
```
arch-chroot /mnt
```

## 2.1 Zona horaria

Una vez dentro estableceremos la zona horaria, para eso usaremos
```
ln -sf /usr/share/zoneinfo/Spain /etc/localtime
```
![](./maquina/hora.PNG)

Ahora generaremos el fichero que contiene información descriptiva sobre el reloj del modo de hardware:
```
hwclock --systohc
```
![](./maquina/hora%202.PNG)

## 2.1 Establecer idioma y distribución del teclado:
```
echo LANG=es_ES.UTF-8 /etc/locale.conf
echo KEYMAP=es /etc/vconsole.conf
```
![](./maquina/teclado%20idioma.PNG)


## 2.2 Establecer nombre para la maquina desde Vim
Ahora creamos el archivo ```/etc/hostname``` y ```/etc/hosts``` estableceremos un nombre para la máquina:
```
vim /etc/hostname
```
![](./maquina/etchostname.PNG)

```
vim /etc/hosts
```
![](./maquina/etchosts.PNG)


# 3.0 Instalación de utilidades en el SO
Instalaremos las utilidades utilidades que podemos ver en el comando:
```
pacman -Sy grub efibootmgr networkmanager network-manager-applet dialog os-prober mtools dosfstools base-devel linux-headers cups reflector openssh xdg-utils xdg-user-dirs virtualbox-guest-utils
```
![](./maquina/inst.PNG)

Ahora instalaremos y configuraremos grub:
```
grub-install

grub-mkconfig -o /boot/grub/grub.cfg
```

## 3.1 Iniciaremos el servicio NetworkManager y el sshd
Ahora iniciaremos el servicio NetworkManager y el sshd, que al estar en la instalacion se encuentran instalados pero no iniciados:
```
systemctl enable NetworkManager sshd
```

## 3.1 Creación de usuario sudo en el sistema
Ahora crearemos un usuario sudo, para eso lo crearemos en el grupo wheel.
```
useradd -m -G wheel -s /bin/bash alumno
```

El significado de las flags es:

**-m/--create-home:** crea el directorio del usuario como /home/usuario. Dentro de este directorio, un usuario que no es superusuario puede escribir archivos, eliminarlos, instalar programas, etc.

**-G/--groups:** introduce una lista de grupos suplementarios de los que el usuario también es miembro. Cada grupo está separado del siguiente mediante una coma, sin espacios intermedios. Por defecto el usuario pertenece solo al grupo inicial.

**-s/--shell:** define la ruta y el nombre de archivo del intérprete de línea de órdenes de inicio de sesión predeterminado del usuario. Una vez que se completa el arranque, el intérprete de línea de órdenes de inicio de sesión predeterminado es el que se especifica aquí. Asegúrese de que el intérprete de línea de órdenes elegido esté instalado si es distinto a Bash.

## 3.2 Asignación de contraseña para el usuario.
Crearemos una contraseña con ```passwd```
```
passwd alumno
```
## 3.2 Establecer editor predeterminado de nuestro usuario, para eso editaremos ```/etc/profile/````añadiendo lo sigiente en la linea 23:
```
export EDITOR = vim
```

## 3.3 Edición de ```visudo```
Abriremos el archivo sudoers con el comando visudo, donde descomentaremos '```%wheel ALL=(ALL:ALL) ALL:```'

![](./maquina/visudo.PNG)

Ahora reiniciaremos la máquina, y nos entrará al SO, accederemos con el usuario previamente creado. Ahora, actualizaremos los repositorios:
```
sudo pacman -Syy
```

# 4.0 Inicio del SO
Una vez inicimos el SO y accedesmos con el usuario creado procedemos a actualizar los repositorios:
```
sudo pacman -Syy
```

## 4.1 Instalación de programas y e entorno.
Para la instalación del entorno usaremos el comando
```
sudo pacman -S xf86-video-vmware xorg lightdm lightdm-gtk-greeter xfce4 xfce4-goodies firefox materia-gtk-theme papirus-icon-theme
```


## 4.2 Gestor de extensiones
Habilitaremos el gestor de extrensiones que hemos instalado, para luego reiniciar y tener el entorno grafico:
```
sudo systemctl enable lightdm
```

## 4.3 Instalación nano
Para instalación usaremos o comando:
```
sudo pacman nano -Syy
```

# 5.0 Instalación de entorno alternativo
GNOME es un entorno gráfico (gestor de ventanas) amigable que permite a los usuarios usar y configurar sus ordenadores de una forma sencilla. GNOME incluye un panel (para inicar aplicaciones y mostrar el estado de funcionamiento), un escritorio ( donde se pueden situar los datos y las aplicaciones), un conjunto estándar de aplicaciones y herramientas de escritorio, y un conjunto de convenciones que facilitan la operación y consistencia de las aplicaciones entre sí.

Algunas de las características de este entorno de escritorio son:

- GNOME es en su totalidad código abierto (software libre), con el código fuente disponible libremente y desarrollado por cientos de programadores en todo el mundo. Si quiere saber más sobre el proyecto Gnome puede visitar la página web de Gnome: http://www.gnome.org

- GNOME tiene una serie de ventajas para los usuarios. Facilita el uso y la configuración de aplicaciones usando una simple pero potente interfaz gráfica.
  
- GNOME es altamente configurable, permitiéndole ajustar su escritorio con el aspecto que desee. El gestor de sesiones de GNOME recuerda la configuración previa, de manera que una vez que haya configurado las cosas a su gusto, las mantendrá así.

- GNOME soporta muchos idiomas, y puede añadir más sin cambiar el software. GNOME soporta incluso varios protocolos de arrastrar y soltar (drag and drop D&D) para una máxima interoperabilidad con aplicaciones que no sean compatibles con GNOME.

- GNOME tiene también una serie de ventajas para los programadores que indirectamente benefician también a los usuarios. Los programadores no necesitan comprar una cara licencia de software para hacer compatibles sus aplicaciones comerciales. De hecho, GNOME es independiente de cualquier compañía - ningún componente del interfaz esta controlado únicamente por una compañía o tiene restringidas la modificación o redistribución. Finalmente, GNOME funciona en numerosos sistemas operativos de tipo Unix, incluido Linux.
  
```
sudo pacman -S gnome gnome-extra gnome-power-manager gnome-tweak-tool gnome-packagekit gnome-settings-daemon-updates polkit-gnome
```

Una vez instalado iniciaremos sesión con el usuario creado anteriormente y nos cargará el escritorio.

![](./maquina/escrit.PNG)
