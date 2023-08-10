# Gestión de Permisos

## Parte 1: Gestión de Usuarios

### Creación de Usuarios:
### estos se creán con el comando

- adduser "usuario1"
- adduser "usuario2"
- adduser "usuario3"

### salida usuario 1

Añadiendo el usuario `usuario1' ...
Añadiendo el nuevo grupo `usuario1' (1001) ...
Añadiendo el nuevo usuario `usuario1' (1001) con grupo `usuario1' ...
Creando el directorio personal `/home/usuario1' ...
Copiando los ficheros desde `/etc/skel' ...
Nueva contraseña: 
CONTRASEÑA INCORRECTA: No se ha proporcionado ninguna contraseña
Vuelva a escribir la nueva contraseña: 
No se ha proporcionado ninguna contraseña.
passwd: Error de manipulación del testigo de autenticación
passwd: no se ha cambiado la contraseña
¿Intentar de nuevo? [s/N] n
Cambiando la información de usuario para usuario1
Introduzca el nuevo valor, o presione INTRO para el predeterminado
	Nombre completo []: 
	Número de habitación []: 
	Teléfono del trabajo []: 
	Teléfono de casa []: 
	Otro []: 
¿Es correcta la información? [S/n] s


### salida usuario2

Añadiendo el usuario `usuario2' ...
Añadiendo el nuevo grupo `usuario2' (1002) ...
Añadiendo el nuevo usuario `usuario2' (1002) con grupo `usuario2' ...
Creando el directorio personal `/home/usuario2' ...
Copiando los ficheros desde `/etc/skel' ...
Nueva contraseña: 
CONTRASEÑA INCORRECTA: No se ha proporcionado ninguna contraseña
Vuelva a escribir la nueva contraseña: 
No se ha proporcionado ninguna contraseña.
passwd: Error de manipulación del testigo de autenticación
passwd: no se ha cambiado la contraseña
¿Intentar de nuevo? [s/N] n
Cambiando la información de usuario para usuario2
Introduzca el nuevo valor, o presione INTRO para el predeterminado
	Nombre completo []: 
	Número de habitación []: 
	Teléfono del trabajo []: 
	Teléfono de casa []: 
	Otro []: 
¿Es correcta la información? [S/n] s


### salida usuario3

Añadiendo el usuario `usuario3' ...
Añadiendo el nuevo grupo `usuario3' (1003) ...
Añadiendo el nuevo usuario `usuario3' (1003) con grupo `usuario3' ...
Creando el directorio personal `/home/usuario3' ...
Copiando los ficheros desde `/etc/skel' ...
Nueva contraseña: 
CONTRASEÑA INCORRECTA: No se ha proporcionado ninguna contraseña
Vuelva a escribir la nueva contraseña: 
No se ha proporcionado ninguna contraseña.
passwd: Error de manipulación del testigo de autenticación
passwd: no se ha cambiado la contraseña
¿Intentar de nuevo? [s/N] n
Cambiando la información de usuario para usuario3
Introduzca el nuevo valor, o presione INTRO para el predeterminado
	Nombre completo []: 
	Número de habitación []: 
	Teléfono del trabajo []: 
	Teléfono de casa []: 
	Otro []: 
¿Es correcta la información? [S/n] s


### si se revisa los usuarios tenemos lo siguiente

usuario1:x:1001:1001:,,,:/home/usuario1:/bin/bash
usuario2:x:1002:1002:,,,:/home/usuario2:/bin/bash
usuario3:x:1003:1003:,,,:/home/usuario3:/bin/bash


### Asignación de contraseñas

### Cambio de contraseña usuario 1

sudo passwd "usuario1"

### salida
Nueva contraseña: 
Vuelva a escribir la nueva contraseña: 
passwd: contraseña actualizada correctamente


### Cambio de contraseña usuario 2
sudo passwd "usuario2"
Nueva contraseña: 
Vuelva a escribir la nueva contraseña: 
passwd: contraseña actualizada correctamente


### Cambio de contraseña usuario 3
sudo passwd "usuario3"
Nueva contraseña: 
Vuelva a escribir la nueva contraseña: 
passwd: contraseña actualizada correctamente


###  Información de Usuarios

id "usuario1"
uid=1001(usuario1) gid=1001(usuario1) grupos=1001(usuario1)


### Eliminación de Usuarios
sudo userdel "usuario3"




## Parte 2: Gestión de Grupos

### Creación de Grupos

sudo groupadd "grupo1"
sudo groupadd "grupo2"

### Agregar usuarios a grupos y Verificación de membresía

### antes del cambio
comando: groups "usuario1"
salida: usuario1 : usuario1

### comando de cambio
sudo usermod -g grupo1 usuario1

### luego del cambio
groups "usuario1"
usuario1 : grupo1


### antes del cambio
groups "usuario2"
usuario2 : usuario2


### comando de cambio
sudo usermod -g grupo2 usuario2


### luego del cambio
groups "usuario2"
usuario2 : grupo2



### Eliminar Grupo
### para eliminar el grupo se debe de eliminar el usuario ya que da el siguiente inconveniente

comando: sudo groupdel "grupo2"
salida: groupdel: no se pudo eliminar el grupo primario del usuario «usuario2»



## Parte 3: Gestión de Permisos

### Creación de Archivos y Directorios
### cambio de usuario
    comando: su usuario1
    salida: Contraseña: 

    usuario1@robin-Inspiron-3543:~$ 

### creación de archivo
 comando para crear archivo vacio: touch archivo1.txt
 comando para escribir en archivo: nano archivo1.txt
 comando para leer archivo cat archivo1.txt
 salida de lectura de archivo: hola mundo

### creación de directorio
 comando para crear directorio: mkdir directorio1
 comando para cambiar a carpeta creada: cd directorio1
 comando para crear archivo dentro de carpeta: touch archivo2.txt
 comando para escribir en archivo: nano archivo2.txt


### Verificar Permisos
comando: ls -l
salida: total 8
        -rw-r--r-- 1 usuario1 grupo1   11 ago  9 19:10 archivo1.txt
        drwxr-xr-x 2 usuario1 grupo1 4096 ago  9 19:14 directorio1

comando: ls -ld
salida: drwxr-x--- 4 usuario1 grupo1 4096 ago  9 19:12 .


comando: ls -l
salida: total 4
        -rw-r--r-- 1 usuario1 grupo1 23 ago  9 19:14 archivo2.txt

comando: ls -ld
salida: drwxr-xr-x 2 usuario1 grupo1 4096 ago  9 19:14 .


### Modificar Permisos usando `chmod` con Modo Numérico
comando: chmod 640
validación: ls -l
            total 8
            -rw-r----- 1 usuario1 grupo1   11 ago  9 19:10 archivo1.txt


### Modificar Permisos usando `chmod` con Modo Simbólico
### antes del cambio
comando: ls -l
salida: total 4
        -rw-r--r-- 1 usuario1 grupo1 23 ago  9 19:14 archivo2.txt

### luego del cambio
comando: chmod u=rwx archivo2.txt
comando: ls -l
salida: total 4
        -rwxr--r-- 1 usuario1 grupo1 23 ago  9 19:14 archivo2.txt


### Configurar Permisos de Directorio
### antes del cambio
comando: ls -ld directorio1/
salida: drwxr-xr-x 2 usuario1 grupo1 4096 ago  9 19:14 directorio1/

### luego del cambio
comando: chmod 740 directorio1/
comando: ls -ld directorio1/
salida: drwxr----- 2 usuario1 grupo1 4096 ago  9 19:14 directorio1/
 

###  Comprobación de Acceso:

### usuario2@robin-Inspiron-3543:/home$ cd usuario1
### bash: cd: usuario1: Permiso denegado













