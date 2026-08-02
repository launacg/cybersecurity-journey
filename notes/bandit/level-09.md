# Level 9

## 🎯 Objetivo

Encontrar la contraseña dentro de `data.txt`, un archivo que mezcla
datos binarios con texto legible. La contraseña aparece como una de
las pocas cadenas de texto legible, precedida por varios signos `=`.

## 💡 Conceptos aprendidos

### `grep`: búsqueda de patrones de texto

`grep` es un comando que busca un patrón (una palabra, símbolo o
expresión) dentro de un archivo, y muestra **solo las líneas** donde
ese patrón aparece, en vez de mostrar el archivo completo, filtra y
entrega justo lo que se busca. Se usa constantemente para:
- Encontrar una palabra específica dentro de un archivo grande (nivel 7).
- Filtrar resultados de otro comando a través de un pipe (ej. `find | grep`).
- Confirmar si cierto patrón existe en un archivo antes de abrirlo completo.

**Comportamiento por defecto con archivos binarios:**
Si `grep` detecta que un archivo no es texto puro (tiene contenido
binario mezclado, como `data.txt` en este nivel), por seguridad no
imprime la línea completa, solo avisa `binary file matches`, para
evitar volcar caracteres extraños que puedan afectar la terminal.

**La opción `-a`:**
`-a` fuerza a `grep` a tratar el archivo como texto de todas formas,
mostrando la línea completa aunque contenga bytes binarios alrededor.
Es necesaria para poder ver el contenido real cuando se sabe que el
archivo mezcla binario y texto.

**Error común: `grep` sin archivo especificado**
Si se ejecuta `grep "patrón"` sin indicar un archivo al final, `grep`
asume que el patrón se debe buscar en lo que el usuario escriba por
teclado en tiempo real (entrada estándar), por eso el comando parece
"quedarse esperando", en vez de dar un error. Siempre hay que indicar
el archivo donde buscar al final del comando.

### `strings`: extraer solo texto legible

`strings` escanea un archivo y devuelve únicamente las secuencias de
caracteres que forman texto legible, ignorando por completo los bytes
binarios que no se pueden interpretar como texto. Es la herramienta
más adecuada cuando el objetivo menciona explícitamente "human-readable
strings" dentro de un archivo binario.

### Comparando dos formas de combinar `grep` y `strings`

Ambas combinaciones llegan al mismo resultado, pero limpian el ruido
binario en momentos distintos:

- `strings data.txt | grep "=="` → primero extrae **todo** el texto
  legible del archivo (limpia una sola vez), y luego busca `==`
  dentro de ese resultado ya limpio. Es la forma más simple y directa.
- `grep -a "===" data.txt | strings` → primero busca `===` en el
  archivo binario completo (usando `-a` para forzar a que `grep`
  entregue la línea, aunque tenga ruido), y luego pasa esa línea
  específica por `strings` para limpiarla. Funciona igual, pero
  limpia después de buscar, no antes.

## ⚙️ Comandos utilizados
`grep -a "===" data.txt`
`strings data.txt | grep "=="`

- `grep -a "===" data.txt` — primer intento: encuentra la línea con el patrón, pero mezclada con ruido binario.
- `strings data.txt | grep "=="` — versión limpia: extrae el texto legible primero, y de ahí filtra la línea con `==`.

## 📝 Notas personales

Mi primer intento con `grep -a "==="` sí encontró la contraseña, pero
el resultado venía rodeado de muchos caracteres binarios ilegibles,
dificultando la lectura. Cambiar el orden a `strings | grep` limpió el
archivo antes de buscar, dando un resultado mucho más claro. Este nivel
me ayudó a entender que el orden de los comandos en un pipe no siempre
da el mismo resultado visual, aunque técnicamente ambos "funcionen".

## 📚 Recursos de consulta

- [man grep](https://man7.org/linux/man-pages/man1/grep.1.html)
- [man strings](https://man7.org/linux/man-pages/man1/strings.1.html)
