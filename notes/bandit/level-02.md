# Level 2

## 🎯 Objetivo

Leer el contenido de un archivo cuyo nombre contiene espacios y guiones
al inicio y al final: `--spaces in this filename--`.

## 💡 Conceptos aprendidos

- Cuando un nombre de archivo tiene espacios, la terminal interpreta
  cada espacio como una separación entre argumentos distintos; por eso
  escribir el nombre tal cual, sin ningún tratamiento especial, rompe
  el comando (la terminal cree que le estás pasando varios archivos
  en vez de uno solo con espacios en el nombre).
- Existen tres formas de decirle a la terminal "esto es un solo nombre,
  con espacios incluidos":
  1. **Autocompletado con Tab**: escribir el inicio del nombre y
     presionar `Tab`:  la terminal completa el resto automáticamente,
     incluyendo los espacios de forma segura.
  2. **Comillas**: escribir el nombre completo entre comillas dobles,
     ej. `cat "--spaces in this filename--"`, para que la terminal lo
     trate como un único argumento.
  3. **Backslash (`\`) antes de cada espacio**: escribir el nombre
     escapando cada espacio individualmente, ej.
     `cat --spaces\ in\ this\ filename--` — el `\` le dice a la terminal
     "el siguiente carácter (el espacio) es parte del nombre, no una
     separación".
- El nombre también empieza con `--`, lo cual normalmente se confundiría
  con una opción del comando (como vimos en el nivel 1), el
  autocompletado con Tab resuelve ambos problemas a la vez.

## ⚙️ Comandos utilizados
ls
cat --sp[Tab]


- `ls` — lista los archivos del directorio, mostrando el nombre completo con espacios.
- `cat --sp` + `Tab` — la terminal autocompleta el nombre exacto del archivo, manejando los espacios y los guiones iniciales sin que se interpreten como opciones.

## 📝 Notas personales
El autocompletado con Tab no es solo un atajo cómodo,  en este caso es
la forma más segura de escribir nombres de archivo complicados, porque
elimina el riesgo de errores de tipeo con espacios o caracteres especiales.
También se puede resolver con comillas dobles alrededor del
nombre completo; lo dejo anotado como alternativa.

## 📚 Recursos de consulta

- [explainshell.com](https://explainshell.com/) — para ver cómo se interpretan los espacios en la línea de comandos
