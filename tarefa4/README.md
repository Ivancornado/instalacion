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
mount -vo remount < donde está montado >
```
![](./caps/mount.PNG)

## 3.3 Ahora comprobaremos que as opcións de disco son correctas
Para iso miraremos os contido de `/proc/mounts`

![](./caps/proc.PNG)

Como podemos ver a particion que editamos está montada correctamente.

# 4 Activando as cuotas (tanto de usuario coma de grupo)

## 4.1 Creación de ficheiros necesarios
Usaremos o comando `sudo quotacheck -ugm < directorio donde está montada a particion >` para crear os arquivos `aquota.user` e `aquota.group`.

![](./caps/creararchivos.PNG)

## 4.2 verificamos que se crearon os ficheiros adecuados
Usaremos `ls` seguido de `/` para confirmar que se crearon `aquota.user` e `aquota.group` neste ultimo directorio.

![](./caps/ls.PNG)


    Engade os módulos de quota ao kernel (se fose necesario)
    Activa o sistema de cuotas

# 5 Cuotas de usuario e de grupo

NOTA: warningbiohazardradioactive non usar setquota radioactivebiohazardwarning

Cada vez que establezas unha cuota comproba cun comando que a estableciches correctamente.

    Creade as usuarias veronica-lake, gene-tierney, ada-lovelace e hedy-lamarr.
    Creade os grupos de usuarias actresses e scientists.
    Incluide a veronica-lake, gene-tierney e hedy-lamarr no grupo actresses
    Incluide a ada-lovelace e hedy-lamarr no grupo scientists.
    Establece as seguintes cuotas de usuario:
        veronica-lake 100M soft e 150M hard.
        gene-tierney 200M soft e 250M hard.
        ada-lovelace 500M soft e 600M hard.
        hedy-lamarr 800M soft e 1G hard.
    Establecede as seguintes cuotas de grupo:
        actresses 400M soft e 450M hard
        scientist 900M soft e 1G hard

Comprobade os efectos que ten o solapamento das cuotas entre grupos e usuarias e explicádeos:

    Cómo funcionan as cuotas nun grupo?
    Cómo afectan aos usuarios do grupo?
    Posibilidades:
        A cuota do grupo afecta aos membros do grupo (sumada)
        A cuota do grupo afecta a cada membro do grupo (individualmente)

# 6 Informes de cuotas

Xera un informe global das cuotas creadas
7 Entrega

Cando remates, establece un tag chamado v4 e con mensaxe "Entrega actividade 4" point_down

git tag -a v4 <derradeiro-hash-commit> -m "Entrega actividade 4"
git push origin v4