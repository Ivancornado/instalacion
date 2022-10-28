# Ejercicio 2

- [Ejercicio 2](#ejercicio-2)
- [Resumen "/etc"](#resumen-etc)
  - [1.0 Descripción do cometido do ficheiro ```/etc/passwd```](#10-descripción-do-cometido-do-ficheiro-etcpasswd)
  - [1.1 Estructura /etc/passwd](#11-estructura-etcpasswd)
  - [1.2 Formato /etc/passwd](#12-formato-etcpasswd)
- [2.0 Descripción /etc/shadow](#20-descripción-etcshadow)

# Resumen "/etc"

· /etc/passwd Información de configuración sobre las cuentas de usuario del sistema.

· /etc/shadow Contraseñas de las cuentas de usuario

· /etc/group Información sobre los grupos del sistema.
## 1.0 Descripción do cometido do ficheiro ```/etc/passwd```

El contenido del fichero ```/etc/passwd``` determina quien puede acceder al sistema de manera legitima y que se puede hacer una vez dentro del sistema. Este fichero es la primera linea de defensa del sistema contra accesos no deseados. Debe de mantenerse escrupulosamente y libre de errores y fallos de seguridad. En el tenemos registrados las cuentas de usuarios, asi como las claves de accesos y privilegios.

## 1.1 Estructura /etc/passwd
/etc/passwd contiene una entrada por línea para cada usuario (cuenta de usuario) del sistema. Todos los campos están separados por un (:). Total de siete campos de la siguiente manera. En general, la entrada del archivo /etc/passwd tiene el siguiente aspecto:

![Captura estructura etc/passwd](./Capturas-passwd/Captura.PNG)

## 1.2 Formato /etc/passwd

**1. Nombre de usuario:** se utiliza cuando el usuario inicia sesión. Debe tener entre 1 y 32 caracteres de longitud.

**2. Contraseña:** un carácter x indica que la contraseña cifrada se almacena en el archivo /etc/shadow. Tenga en cuenta que debe usar el comando passwd para calcular el hash de una contraseña escrita en la CLI o para almacenar / actualizar el hash de la contraseña en el archivo /etc/shadow.

**3. ID de usuario (UID):** a cada usuario se le debe asignar una ID de usuario (UID). El UID 0 (cero) está reservado para root y los UID 1-99 están reservados para otras cuentas predefinidas. El sistema reserva UID 100-999 adicionales para cuentas / grupos administrativos y del sistema.

**4. ID de grupo (GID):** la ID de grupo principal (almacenada en /etc/group file).

**5. Información de ID de usuario:** El campo de comentario. Le permite agregar información adicional sobre los usuarios, como el nombre completo del usuario, el número de teléfono, etc. Este campo se utiliza mediante un comando de dedo.

**6. Directorio de inicio:** La ruta absoluta al directorio en el que estará el usuario cuando inicie sesión. Si este directorio no existe, el directorio de usuarios se convierte en /.

**7. Comando/shell:** La ruta absoluta de un comando o shell (/bin/bash). Típicamente, esto es un caparazón. Tenga en cuenta que no tiene que ser un shell.

# 2.0 Descripción /etc/shadow
El fichero /etc/shadow almacena las contraseñas de las cuentas de usuario. Se utiliza este fichero por seguridad. /etc/shadow es un archivo de texto que contiene información sobre las contraseñas de los usuarios del sistema. Es propiedad del usuario root y del grupo oculto y tiene 640 permisos (*El usuario propietario puede leer y escribir, el grupo puede leer el archivo y otros no pueden hacer nada*).

