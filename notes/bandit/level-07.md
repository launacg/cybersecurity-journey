# Level 7

## 🎯 Objetivo

Encontrar la contraseña dentro de un archivo `data.txt`, ubicada en la
misma línea que la palabra "millionth".

## 💡 Conceptos aprendidos

- `grep` busca un patrón de texto dentro de un archivo y muestra solo
  las líneas donde aparece, en vez de mostrar el archivo completo.
- Antes de abrir un archivo desconocido con `cat`, es buena práctica
  revisar su tamaño primero con `ls -l`, o su número de líneas con
  `wc -l`, para evitar saturar la terminal con archivos muy grandes.
- `less` permite navegar un archivo grande pantalla por pantalla (en
  vez de imprimirlo todo de golpe como `cat`), y admite búsqueda interna
  con `/palabra`.
- El comando `file` (ya usado en el nivel 4) también sirve aquí para
  confirmar el tipo de archivo antes de decidir cómo abrirlo.

## ⚙️ Comandos utilizados
`ls -l data.txt`
`file data.txt`
`grep millionth data.txt`

- `ls -l data.txt` — revisa el tamaño del archivo antes de decidir cómo abrirlo.
- `file data.txt` — confirma que el archivo es de texto legible.
- `grep millionth data.txt` — muestra solo la línea que contiene la palabra "millionth", junto con la contraseña.
- 
- ## 📝 Notas personales

Antes de abrir el archivo, usé `ls -l` para ver su tamaño y confirmar
que era demasiado grande para `cat`. Luego revisé el tipo con `file`
(como aprendí en el nivel 4) y finalmente usé `grep` para encontrar
directamente la línea que necesitaba, en vez de mostrar todo el
contenido

## 📚 Recursos de consulta

- [man grep](https://man7.org/linux/man-pages/man1/grep.1.html)
- [man less](https://man7.org/linux/man-pages/man1/less.1.html)
