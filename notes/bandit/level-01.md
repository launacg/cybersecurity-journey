# Level 1

## 🎯 Objetivo

Leer el contenido de un archivo cuyo nombre es un solo guion (`-`), un
caso especial que confunde a los comandos de Linux si no se maneja
correctamente.

## 💡 Conceptos aprendidos

- Un archivo puede tener un nombre poco común, incluso un solo carácter
  como `-`.
- La mayoría de comandos interpretan un `-` como el inicio de una opción
  (ej. `ls -l`), no como un nombre de archivo, por lo que escribir
  `cat -` no funciona como se espera.
- Anteponer `./` a un nombre de archivo le indica explícitamente a la
  terminal "esto es un archivo en el directorio actual", evitando que
  se confunda con una opción del comando.

## ⚙️ Comandos utilizados

`ls` 
`cat ./-`


- `ls` — lista los archivos del directorio actual (muestra el archivo `-`).
- `cat ./-` — muestra el contenido del archivo llamado `-`, usando `./`
  para que no se interprete como una opción.

## 📝 Notas personales

Este fue el primer nivel que requirió pensar más allá del comando básico:
no basta con saber qué hace `cat`, también hay que entender cómo la
terminal interpreta los argumentos que recibe.

## 📚 Recursos de consulta

- [explainshell.com](https://explainshell.com/) — para desglosar `cat ./-` y ver cómo se interpreta cada parte
