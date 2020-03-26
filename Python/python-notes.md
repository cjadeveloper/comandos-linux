# Notas de Python

## Abriendo el apetito

### Python más Pythónico

Charla dictada por Roberto Alsina -[@ralsina](https://twitter.com/ralsina?lang=es)- en el Python Meetup del 07/11/2019

#### 1. Python es EXPRESIVO

#### 2. Usa Python

#### 3. Usá más Python

#### 4. Usá estructuras de Datos (correcta)

La fuente mas común de ineficiencia y errores en los programas Python es usar la estructura de datos equivocada. 

Por ejemplo si *vamos a buscar algo* y hacemos

```py
if x in datos:
    algo(x)
```

Ese código puede ser muy lenta si `datos` es una lista o una tupla, a medida que `datos` es más grande. En cambio si `datos` fuera un set o un diccionario, esto tarda lo mismo si tuvieramos 5 elementos que si tuvieramos 1 millon.

Si *vamos a modificar algo* y hacemos:

```py
data.pop(0)
```

Si `data` fuera una lista, sacar *de adelante*, osea del lado izquierdo `pop(0)`, es ineficiente en listas. Sacar del lado derecho, osea del último elemento, si es eficiente.

```bash
>>> q = []
>>> q.append('eat')
>>> q.append('sleep')
>>> q.append('code')
>>> q
['eat', 'sleep', 'code']

# Cuidado con ésto! Puede ser muy lento para muchos elementos
>>> q.pop(0)
['eat']
```

Si tenés que sacar de adelante, tenés que usar un `collections.deque`. Python’s deque objects are implemented as doubly-linked lists. This
gives them excellent and consistent performance for inserting and
deleting elements, but poor O(n) performance for randomly access-
ing elements in the middle of the stack.

```bash
>>> from collections import deque
>>> q = deque()
>>> q.append('eat')
>>> q.append('sleep')
>>> q.append('code')
>>> q
deque(['eat', 'sleep', 'code'])

>>> q.popleft()
'eat'
>>> q.popleft()
'sleep'
>>> q.popleft()
'code'
>>> q.popleft()
IndexError: "pop from an empty queue"
```

Si tenemos:

```py
x = x + y
```

Si `x` e `y` son strings lo que va hacer la sobrecarga del operador "sumar" es crear un nuevo string `x` con el tamaño de los dos strings concatenados (sumados), copiar todos los datos al nuevo string `x`. Sumamente ineficiente si estamos dentro de un loop por ejemplo.

Si se va a sumar muchos strings, lo que hay que hacer es un `join()` de los strings y no iterar y sumar.

#### Usa PyPI

Buscá primero en PyPI si no está lo que querés hacer, que seguro va a estar mejor hecho y probado.

#### Simple es mejor que Complejo

Pero **MAINTANABLE code is more important que CLEVER code**

Entonces, **Programa como si lo fuera a leer Fantino**

### Invocando al intérprete

La forma de operar del intérprete es parecida a la línea de comandos de Unix: cuando se la llama con la entrada estándar conectada a una terminal lee y ejecuta comandos en forma interactiva; cuando es llamada con un nombre de archivo como argumento o con un archivo como entrada estándar, lee y ejecuta un script del archivo.

Una segunda forma de iniciar el intérprete es `python -c comando [arg] ...`, que ejecuta las sentencias en comando, similar a la opción `-c` de la línea de comandos. Ya que las sentencias de Python suelen tener espacios en blanco u otros caracteres que son especiales en la línea de comandos, es normalmente recomendado citar comando entre comillas dobles.

Algunos módulos de Python son también útiles como scripts. Pueden invocarse usando `python -m module [arg] ...`, que ejecuta el código de module como si se hubiese ingresado su nombre completo en la línea de comandos.

Cuando se usa un script, a veces es útil correr primero el script y luego entrar al modo interactivo. Esto se puede hacer pasándole la opción `-i` antes del nombre del script.

### Programas ejecutables de Python

En los sistemas Unix y tipo BSD, los programas Python pueden convertirse directamente en ejecutables, como programas del intérprete de comandos, poniendo la linea:

```py
#! /usr/bin/env python3.7
```

...al principio del script y dándole al archivo permisos de ejecución (asumiendo que el intérprete están en la variable de
entorno PATH del usuario). `#!` deben ser los primeros dos caracteres del archivo. En algunas plataformas, la primera línea
debe terminar al estilo Unix ('\n'), no como en Windows ('\r\n'). Notá que el caracter numeral '#' se usa en Python
para comenzar un comentario.

Se le puede dar permisos de ejecución al script usando el comando chmod:

```bash
chmod +x myscript.py
```

En sistemas Windows, no existe la noción de *modo ejecutable*. El instalador de Python asocia automáticamente la
extensión `.py` con `python.exe` para que al hacerle doble click a un archivo Python se corra el script. La extensión
también puede ser `.pyw`, en este caso se omite la ventana con la consola que normalmente aparece.

### El archivo de inicio interactivo

Cuando usás Python en forma interactiva, suele ser útil que algunos comandos estándar se ejecuten cada vez que el intérprete se inicia. Podés hacer esto configurando la variable de entorno **PYTHONSTARTUP** con el nombre de un archivo que contenga tus comandos de inicio. Esto es similar al archivo `.profile` en los intérpretes de comandos de Unix.

Este archivo es solo leído en las sesiones interactivas del intérprete, no cuando Python lee comandos de un script ni cuando `/dev/tty` se explicita como una fuente de comandos (que de otro modo se comporta como una sesión interactiva). Se ejecuta en el mismo espacio de nombres en el que los comandos interactivos se ejecutan, entonces los objetos que define o importa pueden ser usados sin cualificaciones en la sesión interactiva. En este archivo también podés cambiar los prompts `sys.ps1` y `sys.ps2`.

## Comprensión de listas

Las comprensiones de listas proporcionan una alternativa al uso de las funciones integradas `maps()` y `filter()` y se prefieren en el uso a éstas últimas.

La función `maps(f, S)` es equivalente a `[f(x) for x in S]`, mientras que `filter(P, S)` es equivalente a `[x for x in S if P(x)]`.
