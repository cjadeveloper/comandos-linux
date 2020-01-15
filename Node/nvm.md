# Node Version Manager (nvm)

## Comandos Básicos

Listar versiones de Node instaladas

```sh
nvm ls
```

Documentar la versión de Node del proyecto actual

```sh
node -v > .nvmrc
```

## Al iniciar un archivo de node usando nvm

On Mac/Linux: Previously to run `node <app_name>`, create a symbolic-link with terminal command:

- if use nvm: ```sudo ln -s `nvm which current` /usr/local/bin/node```
- if use only a single node version: ```sudo ln -s `which node` /usr/local/bin/node```

Then, on top, every `.js` single file

```js
#! /usr/local/bin/node

// rest of your code
// ...
```
