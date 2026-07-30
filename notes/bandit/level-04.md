# Level 4

## 🎯 Objetivo

Encontrar, dentro del directorio `inhere`, el único archivo "legible
por humanos" entre nueve archivos con nombres similares, y leer su
contenido.

## 💡 Conceptos aprendidos

- No todos los archivos con extensión o nombre similar contienen el
  mismo tipo de datos: algunos pueden ser binarios o datos no legibles,
  aunque el nombre no lo indique.
- El comando `file` inspecciona el contenido real de un archivo y
  dice qué tipo de dato es (texto ASCII, binario, imagen, etc.), sin
  necesidad de abrirlo primero.
- El comodín `*` en la terminal representa "cualquier texto que siga",
  permitiendo aplicar un comando a varios archivos a la vez en lugar
  de escribirlos uno por uno.

## ⚙️ Comandos utilizados

**Lo que usé para resolverlo (ensayo y error):**
`ls`
`cat ./-file00` `cat ./-file01` 
...


**Forma más eficiente que aprendí después:**

`file ./-file*`

Esto identifica de inmediato cuál archivo es "ASCII text" (legible),
evitando revisar los nueve uno por uno.

## 📝 Notas personales

Resolví este nivel probando archivo por archivo con `cat`. Después de resolverlo, descubrí el
comando `file`, que hubiera identificado el archivo correcto en un solo
paso. Lo dejo documentado porque es más valioso entender la forma
eficiente que solo la fuerza bruta que usé la primera vez.

## 📚 Recursos de consulta

- [man file](https://man7.org/linux/man-pages/man1/file.1.html)
