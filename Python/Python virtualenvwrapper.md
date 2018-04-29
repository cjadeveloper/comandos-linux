# Usando Virtualenvwrapper, un conjunto de extensiones para Virtualenv

## Introducción

Un entorno virtual de Python es un espacio completamente independiente de otros entornos virtuales y de los paquetes instalados globalmente en el sistema http://rukbottoland.com/blog/tutorial-de-python-virtualenvwrapper/

## Instalacion

Fedora
$ sudo dnf install python-virtualenvwrapper

Debian, Ubuntu
$ sudo apt-get install virtualenvwrapper

## Configuración de virtualenvwrapper

Por defecto virtualenvwrapper crea los virtualenvs en la carpeta `~/.virtualenvs`.
Sin embargo ese comportamiento se puede cambiar. Para eso se necesita agregar un par de variables de entorno al archivo `~/.bashrc` ó `~/.bash_profile`:

```bash
export WORKON_HOME=/opt/virtualenvs
export VIRTUALENVWRAPPER_HOOK_DIR=$WORKON_HOME/hooks
```

La variable WORKON_HOME determina en que directorio se deben crear los virtualenvs al ejecutar el comando mkvirtualenv.

La segunda variable, VIRTUALENVWRAPPER_HOOK_DIR, establece el directorio en donde se instalaran algunos scripts muy útiles que pueden ser usados para automatizar ciertas tareas, como por ejemplo hacer un commit a un repositorio justo antes de desactivar el virtualenv.

Por último, se debe agregar una línea al archivo `~/.bashrc` ó `~/.bash_profile` para especificar en dónde esta ubicado el ejecutable de virtualenvwrapper:

```bash
source /usr/bin/virtualenvwrapper.sh
```

Si se ha instalado virtualenvwrapper en Debian usando el gestor de paquetes, es probable que la línea de arriba no funcione. Intente la siguiente:

```bash
source /etc/bash_completion.d/virtualenvwrapper
```

Si las dos líneas anteriores han fallado, es posible que el archivo virtualenvwrapper.sh se encuentre ubicado
en el directorio `/usr/local/bin/`:

```bash
source /usr/local/bin/virtualenvwrapper.sh
```

Lo que hace este último comando es procesar el código contenido en el script virtualenvwrapper.sh dentro del shell o terminal que estamos utilizando para que los comandos `mkvirtualenv`, `rmvirtualenv` y `workon` estén disponibles.

## Cómo crear un Python virtualenv con virtualenvwrapper

Se debe ejecutar el comando mkvirtualenv más el nombre del virtualenv. Las extensiones se encargan de manera automática de crear el virtualenv en el directorio correspondiente:

mkvirtualenv [-a project_path] [-i package] [-r requirements_file] [virtualenv options] ENVNAME

La opción -a se puede usar para asociar un directorio de proyecto existente con el nuevo entorno.
La opción -i se puede usar para instalar uno o más paquetes (repitiendo la opción) después de crear el entorno.
La opción -r se puede utilizar para especificar un archivo de texto que enumera los paquetes que se instalarán. El valor del argumento se pasa a pip -r para ser instalado.

```bash
mkvirtualenv mi_proyecto
```

## Cómo eliminar Python virtualenvs con virtualenvwrapper

Al ejecutar el comando rmvirtualenv más el nombre del virtualenv, virtualenvwrapper se encarga de borrar el virtualenv con todas los paquetes que hayamos instalado en él:

```bash
rmvirtualenv mi_env
```

## Cómo activar un Python virtualenv con virtualenvwrapper

Para activar un virtualenv solamente se necesita ejecutar el comando workon más el nombre del virtualenv en la terminal:

```bash
workon mi_env
```

## Creando Projectos con virtualenvwrapper

Creamos un nuevo entorno virtual en el `WORKON_HOME` y un nuevo directorio de proyecto en `PROJECT_HOME` definidas en el archivo `~/.bashrc` haciendo

```bash
mkproject [virtualenv options] ENVNAME
```

Por ejemplo, para crear un nuevo entorno virtual llamado `portfolio` en el directorio de mis entornos virtuales `~/.virtualenvs/` y un directorio `portfolio` en mi directorio de projecto `~/djprojects/` utilizando Python 3.6.4 escribo:

```bash
mkproject -p python3.6 portfolio
```

Luego podemos vincular un virtualenv existente a un proyecto existente haciendo:

```bash
setvirtualenvproject [virtualenv_path project_path]
```

Los argumentos para `setvirtualenvproject` son las rutas completas al directorio virtualenv y project. Se establece una asociación para que cuando `workon` active el virtualenv, el proyecto también se active.

Cuando no se dan argumentos, se supone el directorio virtualenv actual y el actual.

Cualquier número de virtualenvs puede referirse al mismo directorio de proyectos, lo que facilita el cambio entre las versiones de Python u otras dependencias para la prueba.
