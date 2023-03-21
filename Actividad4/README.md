<h1>Actividad 4 </h1>

<p>
  Esta actividad se muestra la manera en que se crea un archivo bash y este es incluido en un servicio que luego ejecutaremos. Dicho servicio se encuentra en el directorio de systemd, por lo que se explicara brevemente desde la creación del archivo bash hasta llegar a la creación del archivo que contiene el servicio.
</p>

## Pasos para crear archivo Bash
- `Paso 1` : crear el archivo bash en el directorio <b>/usr/local/bin</b>, utilizando el siguiente comando <b>nano /usr/local/bin/Nombre-bash.sh</b>, (Nombre-bash es el nombre del archivo) 
- `Paso 2` : agregar permisos a dicho archivo con el comando <b> sudo chmod +x /urs/local/bin/Nombre-Bash.sh </b>

En nuestro caso el nombre del archivo se llama <b>ServicioActividad4.sh</b> y la estructura del archivo es la siguiente


```bash
#!/bin/bash
#Este es un programa para actividad 4

echo Esto es un saludo para crear un Systemd

FECHA=$(date +%d/%m/%y)
echo La fecha es : $FECHA

```


## Pasos para crear archivo del servicio
- `Paso 1` : validar que el nombre del servicio que crearemos no exista con el comando `sudo systemctl list-unit-files --type=service | grep NombreServicio` si al ejecutarse no aparece nada indica que se puede utilizar dicho nombre, en nuestro caso se llamara `actividad-4`
- `Paso 2` : Creacion del archivo con el comando `sudo nano actividad-4` en la ruta `/etc/systemd/system/NombreServicio`, la extension del archivo debe ser service, en nuestro ejemplo se crearia de la siguiente manera `sudo nano /etc/systemd/system/actividad-4`
- `Paso 3` : Luego de crear el archivo se debe de dar permisos al mismo con el siguiente comanto `sudo chmod 777 /etc/systemd/system/actividad-4.service`


Con esto se tiene creado el archivo y dado los permisos necesarios, la estructura de nuestro archivo quedo de la siguiente manera

``` service
[Unit]
Description=Servicio de prueba Actividad 4

[Service]
ExecStart=/usr/local/bin/ServicioActividad4.sh

[Install]
WantedBy=multi-user.target

```

## Pasos para ejecutar el archivo servidio

- `Paso 1` : Se debe de validar el estatus del servicio con el comando `sudo systemctl status actividad-4`, donde actividad-4 es el nombre del servicio.

```
![Captura desde 2023-03-20 23-15-30](https://user-images.githubusercontent.com/70467966/226524332-3be11993-d410-4d02-84a5-89c972d11026.png)

```


