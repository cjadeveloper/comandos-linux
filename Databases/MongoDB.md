# MongoDB Notes

## Instalar MondoDB Comunity Server en Ubuntu 19.04

>La orden `apt-cache` puede mostrar gran parte de la información almacenada en la base de datos interna de APT. Esta información es una especie de caché, ya que se obtiene de las diferentes fuentes definidas en el archivo sources.list. Esto ocurre durante la operación `apt update`. ("El Manual del Administrador de Debian" Hertzog y Mas)

```console
$ sudo apt-cache policy mongodb
mongodb:
  Instalados: (ninguno)
  Candidato:  1:3.6.9+really3.6.8+90~g8e540c0b6d-0ubuntu2
  Tabla de versión:
     1:3.6.9+really3.6.8+90~g8e540c0b6d-0ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu disco/universe amd64 Packages
```

Vemos que no está instalada, así que actualizamos los paquetes

```console
sudo apt update
sudo apt install mongodb
```

Comprobar si mongodb está corriendo: "Active: active (running)"

```console
$ sudo systemctl status mongodb
[sudo] contraseña para cjadeveloper:
● mongodb.service - An object/document-oriented database
   Loaded: loaded (/lib/systemd/system/mongodb.service; enabled; vendor preset: enabled)
   Active: active (running) since Sat 2019-09-21 11:38:30 -03; 43min ago
     Docs: man:mongod(1)
 Main PID: 16321 (mongod)
    Tasks: 23 (limit: 4915)
   Memory: 39.9M
   CGroup: /system.slice/mongodb.service
           └─16321 /usr/bin/mongod --unixSocketPrefix=/run/mongodb --config /etc/mongodb.conf

sep 21 11:38:30 cris-nb systemd[1]: Started An object/document-oriented database.
```

Ejecutar mongodb shell

```console
$ mongo
MongoDB shell version v3.6.8
connecting to: mongodb://127.0.0.1:27017
Implicit session: session { "id" : UUID("dd9acdbd-36da-4a01-ab2e-305f1debdc99") }
MongoDB server version: 3.6.8
Welcome to the MongoDB shell.
For interactive help, type "help".
For more comprehensive documentation, see
    http://docs.mongodb.org/
Questions? Try the support group
    http://groups.google.com/group/mongodb-user
Server has startup warnings: 
2019-09-21T11:38:30.796-0300 I STORAGE  [initandlisten]
```
