# Level 3

## 🎯 Objetivo

Encontrar la contraseña dentro del directorio `inhere`, donde el archivo
que la contiene está oculto a simple vista.

## 💡 Conceptos aprendidos

- En Linux, cualquier archivo o carpeta cuyo nombre empiece con un punto
  (`.`) se considera "oculto" — `ls` no lo muestra por defecto.
- `ls -a` muestra **todos** los archivos, incluyendo los ocultos (la `-a`
  significa "all").
- `.` y `..` no son archivos reales, son referencias especiales que
  existen en cada carpeta: `.` significa "esta misma carpeta" y `..`
  significa "la carpeta de arriba" (el directorio padre).
- `cd ..` es la forma más común de moverse un nivel hacia atrás sin
  escribir la ruta completa.

## ⚙️ Comandos utilizados

cd inhere
ls -a
cat ...Hiding-From-You


- `cd inhere` — entra al directorio del reto.
- `ls -a` — revela los archivos ocultos, incluyendo uno con nombre poco común.
- `cat ...Hiding-From-You` — muestra el contenido del archivo real (no confundir con `.` o `..`).

## 📝 Notas personales

El archivo real tenía un nombre diseñado
para parecer "otro punto oculto más", pero llevaba texto adicional
después de los puntos.

## 📚 Recursos de consulta

- [explainshell.com](https://explainshell.com/) — para ver qué hace `ls -a` en detalle
