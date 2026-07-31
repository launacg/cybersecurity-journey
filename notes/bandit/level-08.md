# Level 8

## 🎯 Objetivo

Encontrar, dentro de `data.txt`, la única línea de texto que aparece
exactamente una vez (todas las demás líneas están repetidas).

## 💡 Conceptos aprendidos

- `du` muestra el tamaño de un archivo o carpeta en disco — útil para
  decidir de antemano si un archivo es manejable con `cat` o si conviene
  usar otras herramientas (como ya hice con `ls -l` en el nivel 7).
- `sort` ordena las líneas de un archivo alfabéticamente. Esto es un
  paso necesario antes de `uniq`, porque:
- `uniq` **no** elimina duplicados en todo el archivo — solo colapsa
  líneas **repetidas y consecutivas** en una sola copia. Si las líneas
  iguales no están una al lado de la otra, `uniq` no las detecta como
  duplicadas. Por eso siempre se usa después de `sort`, que agrupa las
  líneas iguales juntas.
- `uniq` sin opciones muestra una copia de cada línea distinta, sin
  importar cuántas veces se repitió originalmente (una línea repetida
  5 veces y una que solo aparecía 1 vez se ven exactamente igual en
  el resultado).
- `uniq -u` sí filtra por unicidad real: muestra **solo** las líneas
  que aparecían exactamente una vez en el archivo, descartando por
  completo cualquier línea que se haya repetido aunque sea 2 veces.
  Esta es la opción que resuelve el objetivo del nivel.
- El pipe (`|`) conecta la salida de un comando con la entrada del
  siguiente, sin necesidad de guardar resultados intermedios en un
  archivo temporal. Es como una banda transportadora entre dos
  "estaciones de trabajo", donde cada comando hace una sola tarea
  simple y el resultado viaja directo al siguiente.

## ⚙️ Comandos utilizados

du -h data.txt
sort data.txt | uniq -u


- `du -h data.txt` — revisa el tamaño del archivo antes de decidir cómo trabajarlo.
- `sort data.txt` — ordena las líneas alfabéticamente, agrupando las repetidas.
- `| uniq -u` — de las líneas ya ordenadas, muestra solo la que aparece exactamente una vez.

## 📝 Notas personales

Al principio pensé que `uniq` solo ya filtraba por líneas únicas en
todo el archivo, pero en realidad solo colapsa repeticiones consecutivas
a una copia; sin la opción `-u`, hubiera visto una copia de líneas que
sí se repetían, mezcladas con la que realmente buscaba. Entender la
diferencia entre "una copia de cada línea distinta" y "líneas que
ocurren exactamente una vez" fue clave para resolver el nivel
correctamente.

## 📚 Recursos de consulta

- [man sort](https://man7.org/linux/man-pages/man1/sort.1.html)
- [man uniq](https://man7.org/linux/man-pages/man1/uniq.1.html)
- [Ryan's Tutorials: Piping](https://ryanstutorials.net/linuxtutorial/piping.php)
- [Geeks for Geeks: uniq Command in Linux with Examples](https://www.geeksforgeeks.org/linux-unix/uniq-command-in-linux-with-examples/)
