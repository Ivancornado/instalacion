## Indice

- [1.0 Instalacion Ubuntu](#10-instalacion-ubuntu)
- [2.0 Actualizacion do sistema](#20-actualizacion-do-sistema)
  - [2.1 Actualización de Ubuntu en un paso](#21-actualización-de-ubuntu-en-un-paso)
- [3.0 Instalación cURL](#30-instalación-curl)
- [4.0 Instalación Fish](#40-instalación-fish)
- [5.0 Instalación Fisher](#50-instalación-fisher)
- [6.0 Instalación Pure (Plungin fish)](#60-instalación-pure-plungin-fish)
- [7.0 Preparacion entorno git en Ubuntu](#70-preparacion-entorno-git-en-ubuntu)
  - [7.1 Instalación git](#71-instalación-git)
  - [7.1.1 Confirmacion de que git está instalado](#711-confirmacion-de-que-git-está-instalado)
  - [7.2 Configuración parametrods globales de git](#72-configuración-parametrods-globales-de-git)
  - [7.3 Engadir e xerar claves ssh a GitHub](#73-engadir-e-xerar-claves-ssh-a-github)
- [8.0 Copiar repositorios en outro equipo](#80-copiar-repositorios-en-outro-equipo)
- [9.0 Modificar .gitconfig](#90-modificar-gitconfig)
- [10.0 Solución erros](#100-solución-erros)

# 1.0 Instalacion Ubuntu

En este exercicio ecplicaremos a instalación de ubuntu paso a paso. Para iso necesitaremos unha imaxe de dito sistema operativo.

![Primera captura de la instalación](./capturas%20ubuntu/Captura1.PNG)

En esta imaxe podemos ver que nos ofrece "Instalar ubuntu" e "Probar ubuntu" ademáis de decirnos cal é a liguaxe que precisamos.

![Segunda captura de la instalacion](./capturas%20ubuntu/Captura2.PNG)

Ahora indicaremoslle ao sistema que configuración de teclado precisamos (Como sabedes en algún linguaxes teremos caracteres distintos, o caso máis cercano a nos sería a ausencia do **Ñ** na lingua inglesa).

![Tercera captura de la instalación](./capturas%20ubuntu/Captura3.PNG)

Ahora indicaremos que tipo de instalación precisamos "Instalación normal" (para dispoñer de todas as funcionalidades do sistema) e "Descargar actualizaciones" (para que o sistema esté na última versión e aforrar ese pasto posteriormente).

![Cuarta captura de la instalación](./capturas%20ubuntu/Captura4.PNG)

Seleccionaremos a opción de borrar o disco e instalar ubuntu para que elimine outro sistema operativo que poida estar almaceado e aforrar erros.

![Quinta captura de la instalación](./capturas%20ubuntu/Captura5.PNG)

Indicaranos os cambios que fará no disco.

![Sexta captura de la instalación](./capturas%20ubuntu/Captura6.PNG)

Elexiremos a zona que nos corresponda.

![Septima captura de la instalación](./capturas%20ubuntu/Captura7.PNG)

Completaremos os campos cos datos que precisemos (Contraseña recomendada en equipos de uso ocasional **"abc123."**).

![Octava captura de la instalación](./capturas%20ubuntu/Captura8.PNG)

Esperamos a q se complete a instalación e a descarga das actualizacións.

![Novena captura de la instalación](./capturas%20ubuntu/Captura9.PNG)

Aceptaremos para que o equipo se reinicie.

![Decima captura de la instalación](./capturas%20ubuntu/Captura10.PNG)

Como a unidade coa imaxe de ubuntu estaba ainda insertada salta esta mensaxe, prememos intro e o equipo explusara automaticamente

![Onceava captura de la instalación](./capturas%20ubuntu/Captura11.PNG)

A instalación está completa e Ubuntu presentanos todas as funcionalidades do sistema, eu omitireinas.

![Doceava captura de la instalación](./capturas%20ubuntu/Captura12.PNG)

Por ultimo presentanos a pantalla de inicio e a instalación estaría completada.

# 2.0 Actualizacion do sistema

![Primeira captura de actualización](./capturas%20ubuntu/actualizar%20sistema%201.PNG)

Para actualizar o sistema por comandos usaremos o comando que se ve na imaxe.

```
sudo apt update
```

![Segunda captura de actualización](./capturas%20ubuntu/actualizacion%20sistema%202.PNG)

Por ultimo Usaremos este comado para finalizar a actualización.

```
sudo apt upgrade
```

## 2.1 Actualización de Ubuntu en un paso

![Primera captura de actualización un paso](./capturas%20ubuntu/actualizacion%20sistema%20en%20un%20paso.PNG)

Para actualizar en un paso usaremos os comandos anteriores separados por **;**

```
sudo apt update; sudo apt upgrade
```

# 3.0 Instalación cURL
Ahora instalaremos cURL, cURL é unha ferramenta de liña de comandos e bibliotecas coa cal é posible transferir datos a través duna URL con diversas opcions de seguridade.

![Primera captura curl](./capturas%20ubuntu/instalacion%20curl.PNG)


# 4.0 Instalación Fish

Instalaremos cURL, cURL é unha ferramenta de liña de comandos e bibliotecas coa cal é posible transferir datos a través dunha URL con diversas opcións de seguridade.

![Instalacion fish](./capturas%20ubuntu/fis%20install.PNG)

Uaremos o camando da imaxe:

```
sudo apt install fish
```

# 5.0 Instalación Fisher

Para a instalacion de fisher, un administrador de plugins de fish o cal se encargará de xestinar os plugins intalados en fish.

![Instalacion fisher](./capturas%20ubuntu/instalacion%20fisher.PNG)

Usaremos o comando da imaxe tendo fish iniciado:
´´´
sudo apt install fish
´´´

# 6.0 Instalación Pure (Plungin fish)

Na instalación de Pure, un plugin que corrixe erros de fish e engade algúns caracteres a mallores.

![Instalacion fisher](./capturas%20ubuntu/instalacion%20pure.PNG)

Para a instalacion usaremos o comando da imaxe con fish iniciado:

```
fisher install pure-fish/pure
```

# 7.0 Preparacion entorno git en Ubuntu

![primera captura git](./capturas%20git/Captura.PNG)

Crearemos o directorio sobre o cal vamos a traballar e con **pwd** confirmaremos que nos atopamos en dito directorio.
```
pwd
```
## 7.1 Instalación git
Ahora faremos a instalación de git, para iso engadiremos o directorio do cal o vamos a descargar tal e como se ve na imaxe.
![segunda captura git](./capturas%20git/Captura2.PNG)

Ahora faremos o comando da imaxe para actualizar os repositorios.
![terceira captura git](./capturas%20git/Captura3.PNG)

Por ultimo instalaremos git co comado da seguinte imaxe.
![cuarta captura git](./capturas%20git/Captura4.PNG)

## 7.1.1 Confirmacion de que git está instalado

Ahora co comando ```git version``` confirmaremos que git está instalado tal como vemos nesta imaxe.

![quinta captura git](./capturas%20git/Captura5.PNG)

## 7.2 Configuración parametrods globales de git

Vamos a configurar nome, email, e defaultBranch.

![sexta captura git](./capturas%20git/Captura6.PNG)

Para iso usaremos
```
 cd ~
 git config --global user.name "AQUI VA TU NOMBRE"
 git config --global user.email AQUI_VA_TU_EMAIL@WHATEVER.COM
 git config --global core.editor AQUI_VA_TU_EDITOR en mi caso code
 git config --global init.defaultBranch main
```
## 7.3 Engadir e xerar claves ssh a GitHub

Usaremos o comando ```ssh-keygen -t ed25519 -C "EMAIL_USADO_EN_REGISTRO_DE_GITHUB"``` pero para iso iremos ao directorio home con ```cd ~```.
![septima captura git](./capturas%20git/Captura7.PNG)

Ahora iniciaremos o axente SSH (faremolo obligatoriamente dende bash).

![octava captura git](./capturas%20git/Captura8.PNG)


Primeiro debemos obter a clave publica con ```cat .ssh/id_ed25519.pub```.

![cpubli captura git](./capturas%20git/cat.PNG)

Para configurar o SSH modificaremos o directorio .ssh/.config/

![19 captura git](./capturas%20git/clave%20publica.PNG)

Por ultimo creamos a clave ssh en git

![clave ssh git](./capturas%20git/Capturaq.PNG)

# 8.0 Copiar repositorios en outro equipo

Primeiro teremos q copiar os repositorios de git na maquina, iso faremolo con ```git clone (clave ssh do repositorio)```

![clone](./capturas%20git/Captura%20clone.PNG)

Ahora importaremos o repositorio con ```git pull (clave ssh do repositorio)```

![pull](./capturas%20git/Captura%20pull.PNG)

# 9.0 Modificar .gitconfig

Para isto aseguraremonos de estar no home ```~``` , unha vez no home modifivaromos o directorio .config ```nano .gitconfig```

![.config](./capturas%20git/format.PNG)

# 10.0 Solución erros

Como se pode ver na captura origin estaba mal configurado.

![origin](./capturas%20ubuntu/fallo%20origin%201.PNG)

Por tanto eliminaremos o origin con ``` git remote remove origin```.

![origin2](./capturas%20ubuntu/origin2.PNG)

Comprobamos que se borrou correctamente.

![origin3](./capturas%20ubuntu/origin3.PNG)

Redefinimos origin correctamente.

![origin4](./capturas%20ubuntu/origin4.PNG)