# Notas sobre VIM y NeoVIM

## Modo Normal

### Copiar del sistema a VIM

Copiar como en cualquier sistema y pegar con `Ctrl+V` en VIM

### Setear texto de todo el documento a 80 columnas

By [Michael Madsen](https://stackoverflow.com/a/3033455/9062331) in StackOverflow

Mover al principio del archivo (se puede hacer con `Ctrl-Home` o `gg`), y tipear `gqG`.

`gqG` formatea el texto comenzando desde la posición actual hasta el final del archivo.
Unirá automáticamente líneas consecutivas cuando sea posible. Puede poner una línea en
blanco entre dos líneas si no desea que esas cosas pasen.

## Modo Inserción

### Insertar cálculos aritméticos mientras escribes

El registro de expresión *(expression registry)* nos permite realizar cálculos y luego
insertar el resultado directamente en nuestro documento.

Supongamos que acabamos de escribir lo siguiente:

```console
5 bolsas de cemento, cada una cuesta $ 455, total $
```

No es necesario salir del editor para hacer el cálculo del total. Con VIM lo podemos
hacer de la siguiente manera (y no tenemos que salir del "modo de inserción")

| Tecla | Contenido del Buffer |
| ----- | -------------------- |
|  `A`  | 5 bolsas de cemento, cada una cuesta $ 455, total $ |
| `<C-r>=`5*455`<CR>` | 5 bolsas de cemento, cada una cuesta $ 455, total $ 2275 |

## Modo Visual

### Copiar y Pegar de VIM al sistema

Seleccionar el texto con `shift+v` y luego presionar `"+y` para copiar al portapapeles
del sistema. Luego pegar, fuera de VIM, con `Ctrl+v` como en cualquier sistema.

## Notas sobre pluggins que uso

### NERDTree

#### Crear un nuevo archivo o directorio desde Vim con NERDTree

Con NERDTree activo y posicionados en el directorio en el cual queremos agregar un nuevo
archivo o directorio, precionamos `m` para abrir el menu de archivos de NERDTree. Este
menu nos permite agregar, rename o eliminar archivos y/o directorios.

Si tipeamos `a` seguido del nombre de archivo y presionamos enter. Vamos a crear un
nuevo archivo en la ruta seleccionada. Para crear un nuevo directorio hacemos lo mismo
pero anteponiendo un `/` al nombre.
