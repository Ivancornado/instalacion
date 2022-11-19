# Actividade 4: cuotas de disco

    Documenta todo o proceso na carpeta correspondente do teu repo Github
    Documenta todos os comandos con todos os flags que utilices!!!
    Utilizar como base unha instalación mínima de Ubuntu 22

# 1 Cal é o páquete que permite manexar cuotas?
O paquete para manexar cuotas denominase ```quota```, este non ven enstalado por defecto en ubuntu 22.04 ou anteriores. 

Para instalar o devandito paquete usaremos o seguinte comando:
```
sudo apt install quota
```


## 2.1 Find
O comando find ven instalado por defecto en Ubuntu 22.04 incluso na versión minima. Isto podemos comprobalo con ```which find```

![](./caps/find.PNG)


### 2.1.1 Que é ```find```.

Find pode ser usado para encontrar arquivos en Linux, este inicia unha busqueda recursiva en unha xerarquía de directorios seguindo uns certos criterios.


### 2.1.2 Explicación flags ```-type``` e ```-name```

`-type` Permite filtrar según o tipo de arquivo.

Aquí podemos ver a forma de distinguir entre Arquivos, Directorios e Enlaces:

![](./caps/typepar.PNG)

Exemplo de `-type`:
```
find . -type f
```

`-name` Para filtrar por nomes de archivo, utiliza el parámetro `-name`. Esto require un nome de arquivo exacto e distingue entre maiúsculas y minúsculas, para evitar que distinga entre maiúsculas e minusculas podemos engadir `-i` antes de `-name` e escribiríase `-iname`.

Exemplo de `-name`:
```
find . -name <File_Name>
```
Exemplo de `-iname` (Para que pase por alto as mayusculas):

```
find . -iname <File_Name>
```

### 2.1.3 Exemplo de uso, `find` para confirmar que os modulos kernel de `quota` están instalados.
Exemplo de busqueda con `-type` e `-name`  para buscar arquivos:
```
find <Ruta que queremos buscar> -type f name <File_Name>
```
![](./caps/kernel.PNG)

Esta sería unha forma de saber se están instalados os módulos do kernel que permiten o manexo de cuotas con ```find```.

# 3 Onde debemos activar/declarar as cuotas de usuario e grupo

## 3.1 Debemos editar o ficheiro `/etc/fstab`

Editamos `/etc/fstab` para indicar cal dos sistemas de arquivos terá cuotas. Para iso engadimos `usrquota` e `grpquota`.

![](./caps/usrquota.PNG)

Como se pode ver na captura anterior  engadimos `usrquota` e `grpquota` na particion a cal engadiremos *cuotas*.

## 3.2 Posteriormente teremos que remontar o filesystem que modificamos.
Usaremnos o seguinte comando:
```
mount -vo remount < directorio donde está montado >
```
![](./caps/mount.PNG)

## 3.3 Ahora comprobaremos que as opcións de disco son correctas
Para iso miraremos os contido de `/proc/mounts`

![](./caps/proc.PNG)

Como podemos ver a particion que editamos está montada correctamente.

# 4 Activando as cuotas (tanto de usuario coma de grupo)

## 4.1 Creación de ficheiros necesarios
Usaremos o comando `sudo quotacheck -ugm < directorio donde está montada a particion >` para crear os arquivos `aquota.user` e `aquota.group`.

Definición dos parámetros:
- `-u:` simboliza que se creará un arquivo de cuota basado no usuario chamado `aquota.user`
- `-g:` indica que se creará un arquivo de cuota basado en grupos chamado `aquota.group`
- `-m:` deshabilita o remontaxe do sistema de arquivos como de solo lectura e, ao mesmo tempo, brinda resultados precisos en un entorno no que o usuario sigue guardando archivos.

![](./caps/creararchivos.PNG)

## 4.2 verificamos que se crearon os ficheiros adecuados
Usaremos `ls` seguido de `/` para confirmar que se crearon `aquota.user` e `aquota.group` neste ultimo directorio.

![](./caps/ls.PNG)

    Engade os módulos de quota ao kernel (se fose necesario)

## 4.3 Añadir modulos de quota al kernel.
Non sería necesario añadilos ao kernel pero en caso de que queiramos facerlo usaremos o comando.
```
sudo apt install linux-image-extra-virtual
```

Este paquete instala controladores adicionais que quedan fora do paquete básico del núcleo.

## 4.3 Activa o sistema de cuotas
En este momento las cuotas están desactivadas, para activarlas usaremos el comado.
```
sudo quotaon -v < directorio donde está montado >
```
Significado del flag:
- `-v` Imprimir mas informacion

![](./caps/encender.PNG)

# 5 Cuotas de usuario e de grupo.

## 5.1 Creación usuarios con el comando `useradd`.
![](./caps/usuarios.PNG)

## 5.2 Creación de grupos con el comando `groupadd`.
![](./caps/group.PNG)

## 5.3 Incluir *veronica-lake, gene-tierney e hedy-lamarr* no grupo *actresses* con el comando `sudo usermod`.
```
sudo usermod -a -G <grupos> <usuario>
```
Flags:


![](./caps/a%C3%B1adirg.PNG)


## 5.3 Incluir *ada-lovelace* no grupo *scientists* con el comando `sudo usermod`.

![](./caps/ada.PNG)

## 5.4 Establecer cuotas de usuario
Para establecer cuotas usamos o comando `edquota`
```
sudo edquota -u < nombre do usuario >
```
Ao introducir o devandito comando abrirase un editor de texto no cal introduciremos os parametros requeridos.

Flags:
- -u editar usuario

### 5.4.1 Engadir cuotas usuarios creados anteriormente.
veronica-lake 100M soft e 150M hard.
![](./caps/veronica.PNG)

gene-tierney 200M soft e 250M hard.
![](./caps/gene.PNG)

ada-lovelace 500M soft e 600M hard.
![](./caps/adaquota.PNG)

En este caso podese ver que ao salir e volver entrar os tamaños se mostran en bytes.

hedy-lamarr 800M soft e 1G hard.
![](./caps/hedy.PNG)

### 5.4.2 Comprobación cuotas usuarios
Para comprobar que as cuotas se crearon correctamente usaremos o comando `cuota` 
```
sudo quota -vs <Nome do usuario>
```
Flags:
- -v imprimir máis información
- -s mostrar unidades en (MB, GB...)

![](./caps/comprobaci%C3%B3nveronica.PNG)

## 5.5 Establecer cuotas de grupo
Para establecer cuotas de grupo tamén usamos o comando `edquota`
```
sudo edquota -g < nombre do grupo >
```
Ao introducir o devandito comando abrirase un editor de texto no cal introduciremos os parametros requeridos.

Flags:
- -g editar grupo
  
### 5.5.1 Engadir cuotas grupos creados anteriormente.
actresses 400M soft e 450M hard
![](./caps/actresses.PNG)

scientist 900M soft e 1G hard
![](./caps/acientists.PNG)

Como ocorre cos usuarios ainda que asignemos os tamaños en Mb se salimos e volvemos entrar ao arquivo o formato cambia.

### 5.5.2 Comprobación cuotas grupos 
Para comprobar que as cuotas se crearon correctamente volveremos usar o comando `cuota` 
```
sudo quota -vs <Nome do grupo>
```
Flags:
- -v imprimir máis información
- -s mostrar unidades en (MB, GB...)
- -g mostrar informacion de los grupos
![](./caps/comprobargrupos.PNG)


# 6.0 Efectos do solapamento das cuotas entre gupos e usuarios.

## 6.1 Cómo funcionan as cuotas nun grupo?

No caso dos grupos se asignamos 500Mb repartense entre os usuarios do grupo e a parte correspondetente sumase a cuota hard de cada usuario.

## 6.2 Cómo afectan aos usuarios do grupo?

 A cuota do grupo afecta aos membros do grupo (sumada)


# 7.0 Informes de cuotas

Xeraremos un informe global das cuotas creadas,usaremos o seguinte comando.
```
sudo repquota -vug /
```
Flags:
- -v mostrar también usuarios/grupos sin ningún uso
- -u mostrar informacion a cerca de usuarios
- -g mostrar informacion a cerca de grupos 
  
![](./caps/hitorial.PNG)






Cando remates, establece un tag chamado v4 e con mensaxe "Entrega actividade 4" point_down

git tag -a v4 <derradeiro-hash-commit> -m "Entrega actividade 4"
git push origin v4