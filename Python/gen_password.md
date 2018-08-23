# Generar Password Aleatoria de 15 dígitos por Consola

Generamos un password de 15 dígitos aleatorios con letras, números y signos de puntuación y lo guarda en un archivo pwd.txt
  
```console
python -c "import random,string; print(''.join([random.choice(string.asscii_letters + string.digit + string.punctuation) for i in range(15)]))" >> pwd.txt
```
Si se ejecuta x veces, genera x password.

Se podría mejorar
