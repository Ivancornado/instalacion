## Indice

- [1.0 Instalacion Ubuntu](#10-instalacion-ubuntu)
- [2.0 Actualizacion do sistema](#20-actualizacion-do-sistema)
  - [2.1 Actualización de Ubuntu en un paso](#21-actualización-de-ubuntu-en-un-paso)
- [3.0 Instalación cURL](#30-instalación-curl)
- [4.0 Instalación Fish](#40-instalación-fish)
- [5.0 Instalación Fisher](#50-instalación-fisher)
- [6.0 Instalación Pure (Plungin fish)](#60-instalación-pure-plungin-fish)

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

Usaremos o comando da imaxe:
´´´
sudo apt install fish
´´´

# 6.0 Instalación Pure (Plungin fish)

