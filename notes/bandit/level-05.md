# Level 5

## 🎯 Objetivo

Encontrar, entre 20 subdirectorios dentro de `inhere`, el único archivo
con las siguientes propiedades: legible por humanos, 1033 bytes de
tamaño, y no ejecutable.

## 💡 Conceptos aprendidos

- `find` permite buscar archivos dentro de una carpeta y todas sus
  subcarpetas de forma automática, a diferencia de `ls` que solo
  muestra el nivel actual.
- `-type f` filtra para mostrar solo archivos (no carpetas).
- `-size 1033c` busca archivos de un tamaño exacto en bytes (`c` = bytes).
- `!` antes de una condición significa "negación" — `! -executable`
  busca archivos que NO sean ejecutables.
- Cuando el filtrado por tamaño y permisos deja pocos resultados,
  `file` (aprendido en el nivel 4) ayuda a confirmar cuál es
  realmente legible antes de usar `cat`.

## ⚙️ Comandos utilizados

`find . -type f -size 1033c ! -executable` 

- `find .` — busca desde la carpeta actual, incluyendo subcarpetas.
- `-type f` — solo archivos, no directorios.
- `-size 1033c` — filtra por tamaño exacto en bytes.
- `! -executable` — excluye archivos ejecutables.

## 📝 Notas personales

Este nivel mostró por qué `find` es mucho más potente que `ls` cuando
hay muchos subdirectorios: en vez de entrar carpeta por carpeta,
describí las características del archivo que buscaba y dejé que el
sistema lo encontrara por mí.

## 📚 Recursos de consulta

- [man find](https://man7.org/linux/man-pages/man1/find.1.html)
