# Backup del Sistema Linux Ubuntu

## Copia de Respaldo del Sistema

Hace el backup de la carpeta raiz dentro del directorio de usuario, excluyendo los directorios especificados. Luego, esos directorios tendran que volver a crearse al finalizarla restauracion 

```console
sudo tar czf ~/backup-ubuntu.tar.gz --exclude=/run --exclude=/home --exclude=/dev --exclude=/mnt --exclude=/proc --exclude=/sys --exclude=/tmp --exclude=/lost+found /
```

Tambien podriamos crearlo especificando la fecha de creacion asi podemos automatizar en un script el comando e ir guardando  ~/backup-ubuntu-$(date +%Y%m%d-%H%M%S).tar.gz

## Restauracion del Backup de Sistema

Para restaurar el backup debemos movernos a la raiz de nuestro sistema y hacer lo siguiente. Esto puede tardar un buen rato.

```console
tar -xzvf ~/backup-archive.tar.gz
```

Las opciones especificadas tienen los siguientes efectos: `-x` extrae el contenido del archivo, `-z` filtra el archivo a través de la herramienta de compresión *gzip*, `-v` habilita la salida detallada que imprime una lista de archivos a medida que se extraen del archivo, y `-f` especifica que *tar* leerá la entrada del archivo especificado posteriormente a archivo `~/backup-archive.tar.gz`

Luego de recuperar el backup y antes que nada, hay que volver a crear los directorios que hemos excluido al hacer el backup

```console
mkdir run
mkdir home
mkdir dev
mkdir lost+found
etc...
```

Si el sistema esta danado, podemos recuperar el backup desde un LiveCD de Ubuntu tambien y luego crear las carpetas faltantes.
