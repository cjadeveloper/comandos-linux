# Configurar Plantilla Cookiecutter-Django

[Cookiecutter Django](https://github.com/pydanny/cookiecutter-django) es un marco para poner en marcha rápidamente los proyectos de Django listos para producción.

## Instalar [cookiecutter](https://github.com/audreyr/cookiecutter) (si no lo tenemos ya) globalmente.

```console
$ pip install "cookiecutter>=1.4.0"
```

## Instalar cookiecutter-django y correrlo localmente para desarrollo.

1. Crearse un entorno virtual con python 3.6
2. Con el entorno activo, ejecutamos cookiecutter contra el repositorio de cookiecutter-django.
3. Instalamos los requerimientos para desarrollo local
4. Creamos y configuramos la base de datos en PostgreSQL para usarla con Django

### 1. Crearse un entorno virtual con python 3.6

Con [virtualenvwrapper](https://virtualenvwrapper.readthedocs.io/en/latest/projects.html) podemos aprovechar su potencia y crear ya un proyecto que nos cree un entorno virtual en el directorio WORKON_HOME que tengamos configurado y una carpeta de projecto en el directorio PROJECT_HOME que tengamos configurado en nuestra variable de entorno, lo active y nos quede listo ya para trabajar.



### 2. Con el entorno activo, ejecutamos cookiecutter contra el repositorio de cookiecutter-django.

```console
(venv_name)$ cookiecutter https://github.com/pydanny/cookiecutter-django
```

### 3. Instalamos los requerimientos para desarrollo local

(venv_name)$ pip install -r requirements/local.txt
