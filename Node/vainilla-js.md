# Vainilla Javascript Notes

## Funciones Arrow

Un ejemplo de una función javascript, en su forma tradicional, que acepte un parámetro y retorne un mensaje por consola, se puede escribir de la siguiente manera:

```js
function saludar (nombre) {
  return "Hola " + nombre
 }
```

La misma función, escrita en "modo flecha", quedaría del siguiente modo

```js
var saludar = nombre => "Hola " + nombre;
```

Vemos que, para este caso tan sencillo, queda definido en una sola línea con el nombre de la función como variable, el parámetro (en éste caso como tiene uno solo, no es necesario ponerlo entre paréntesis), el signo igual y el símbolo de mayor que denotarían la palabra clave `return` y luego el cuerpo de la función (que, nuevamente, como es de una sola línea, puede no estar encerrada entre llaves `{}`.
