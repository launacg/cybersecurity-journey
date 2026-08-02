# Level 10

## 🎯 Objetivo

Encontrar la contraseña dentro de `data.txt`, un archivo cuyo contenido
está codificado en base64.

## 💡 Conceptos aprendidos

### Base64: codificación, no cifrado

Base64 es un método para representar datos usando únicamente caracteres
de texto normal (letras, números, `+`, `/`, `=`), útil para transportar
datos por canales que solo aceptan texto plano (como email o URLs).
**No es un método de seguridad ni cifrado** cualquiera puede revertirlo
sin necesitar ninguna clave, ya que es una transformación reversible y
pública.

### El comando `base64` tiene dos direcciones

- `base64 archivo` (sin opciones) → **codifica** el contenido del
  archivo a base64. Si el archivo ya estaba en base64, esto lo codifica
  una segunda vez, generando un resultado sin sentido.
- `base64 -d archivo` (o `--decode`) → **decodifica**, revirtiendo el
  proceso y devolviendo el texto original.

Mi primer intento fue `base64 data.txt` sin la opción `-d`, lo cual
codificó el archivo otra vez en vez de revertirlo, por eso el
resultado no servía como contraseña.

### `file` describe el formato, no el significado del contenido

Al correr `file data.txt`, el resultado fue "ASCII text", lo cual es
correcto, porque el texto en base64 está compuesto por caracteres
normales y legibles. Pero `file` no puede saber qué *representa* ese
texto: no distingue "esto es texto normal" de "esto es texto normal
que, al decodificarse, revela otra cosa". Es similar a mirar una hoja
escrita en código Morse: técnicamente son caracteres válidos y
legibles, pero el significado real solo aparece al traducirlos.



## ⚙️ Comandos utilizados
`file data.txt` 
`base64 -d data.txt`


- `file data.txt` — confirma que el archivo es texto ASCII (consistente con base64, aunque no lo identifica como tal).
- `base64 -d data.txt` — decodifica el contenido base64 y revela el texto original, incluyendo la contraseña.

## 📝 Notas personales

Mi primer error fue no agregar `-d`, lo que generó una doble
codificación sin sentido. También aprendí que base64 es
solo es una forma de representar datos como texto, un concepto
importante para no confundir codificación con cifrado en niveles
futuros.

## 📚 Recursos de consulta

- [man base64](https://man7.org/linux/man-pages/man1/base64.1.html)
- [man file](https://man7.org/linux/man-pages/man1/file.1.html)
