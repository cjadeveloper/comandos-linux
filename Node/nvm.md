# Node Version Manager (nvm)

## Comandos Básicos

### Listar versiones de Node instaladas

```sh
nvm ls
```

### Instalar una version

```sh
nvm install <version>
```

### Documentar la versión de Node actual en nuestro proyecto

Escribimos el archivo `.nvmrc` en la raiz del proyecto

```sh
node -v > .nvmrc
```

Luego activamos la version con `nvm use`

### Documentar una versión de Node distinta a la actual en nuestro proyecto

```sh
12.13.1 > .nvmrc
```

## Al iniciar un archivo de node usando nvm

On Mac/Linux: Previously to run `node <app_name>`, create a symbolic-link with terminal 
command:

- if use nvm: 

  ```sh
  sudo ln -s `nvm which current` /usr/local/bin/node
  ```

- if use only a single node version: 

  ```sh
  sudo ln -s `which node` /usr/local/bin/node
  ```

Then, on top, every `.js` single file

```js
#! /usr/local/bin/node

// rest of your code
// ...
```
