# Actividade 4: cuotas de disco

    Documenta todo o proceso na carpeta correspondente do teu repo Github
    Documenta todos os comandos con todos os flags que utilices!!!
    Utilizar como base unha instalación mínima de Ubuntu 22

# 1 Cal é o páquete que permite manexar cuotas
O paquete para manexar cuotas denominase ```quota```, este non ven enstalado por defecto en ubuntu 22.04 ou anteriores. 
Para instalar o devandito paquete usaremos o seguinte comando.
```
sudo apt install quota
```

# 2 Cómo saber se o noso sistema ten instalados os módulos do kernel que permiten o manexo de cuotas

## 2.1 Find
O comando find ven instalado por defecto en Ubuntu 22.04 incluso na versión minima. Isto podemos comprobalo con ```which find```

![](./caps/find.PNG)

### 2.1.1 Que é ```find```.

Find pode ser usado para encontrar arquivos en Linux, este inicia unha busqueda recursiva en unha xerarquía de directorios seguindo uns certos criterios.

### 2.1.2 Como usar ```find```

Dende a liña de comandos escribiremos a seguinte estructura:

find <span style="color:red">  *<directory_path>*</span>  <span style="color:blue"><search_parameter></span>.


<span style="color:red">  directory_path: </span>Primeiro, escríbese o comando propiamente dito (find), seguido da ruta de directorio e un número variable de parámetros de procura. Despois un espazo e o valor do parámetro. Algúns dos parametros a introducir poderían ser os seguintes:

![](./caps/parametros%20find.PNG)

<span style="color:blue">search_parameter: </span> Tamén se pode combinar varios parámetros de búsqueda. O comando asume implícitamente que é unha operación lóxica AND. Esto pode escribirse explícitamente. Ademáis, podese utilizar un enlace OR ou negar una condición:

![](./caps/parametros%20find2.PNG)


Axuda:

    Explica o comando find, e os flags:
        -type (e os valores predeterminados que admite).
        -name
    Cómo podemos utilizar o comando find para saber se o noso sistema ten instalados os módulos do kernel que permiten o manexo de cuotas?
    Qué paquete teriamos que instalar se non tivésemos eses módulos kernel instalados?

# 3 Onde debemos activar/declarar as cuotas de usuario e grupo

    Fai os cambios pertinentes ao(s) ficheiro(s) adecuado(s)
    Que hai que facer co disco afectado? (FAINO grin)
    Comproba que as opcións de disco son correctas (PISTA: qué hai en /proc/mounts)?

# 4 Activando as cuotas (tanto de usuario coma de grupo)

    Creación de ficheiros necesarios
    Recorda: verifica que se crearon os ficheiros adecuados
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