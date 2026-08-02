# Level 11

## 🎯 Objetivo

Encontrar la contraseña dentro de `data.txt`, donde todas las letras
minúsculas y mayúsculas han sido rotadas 13 posiciones en el alfabeto
(cifrado ROT13).

## 💡 Conceptos aprendidos

### ROT13: un cifrado que es su propio inverso

ROT13 reemplaza cada letra por la que está 13 posiciones adelante en
el alfabeto (A→N, B→O, etc.). Como el alfabeto tiene 26 letras y 13
es exactamente la mitad, aplicar la rotación **dos veces** regresa al
texto original. Por eso el mismo proceso sirve tanto para "codificar"
como para "decodificar", no existe una opción de decodificado
separada, a diferencia de base64 (nivel 10).

### `tr`: reemplazo posición por posición

`tr` no entiende de "alfabetos" ni de "rotaciones", solo hace un
reemplazo mecánico: estira ambos conjuntos de caracteres en una fila,
y empareja la posición 1 con la posición 1, la 2 con la 2, y así
sucesivamente.

Comando usado:

`cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'`

Tabla de correspondencia (mostrando solo mayúsculas como ejemplo):

| Posición | 1 | 2 | 3 | ... | 13 | 14 | ... | 26 |
|---|---|---|---|---|---|---|---|---|
| Original | A | B | C | ... | M | N | ... | Z |
| Rotado (+13) | N | O | P | ... | Z | A | ... | M |

El segundo conjunto (`N-ZA-Mn-za-m`) parece raro porque en realidad son
cuatro pedazos pegados: `N-Z` (13 letras) + `A-M` (13 letras) para
mayúsculas rotadas, y `n-z` + `a-m` para minúsculas rotadas; sumando
52 posiciones en total, exactamente las mismas que el primer conjunto
(`A-Za-z` = 26 mayúsculas + 26 minúsculas). Si el segundo conjunto
fuera más corto, `tr` se quedaría sin letras con qué emparejar el
resto del primero.

### Alternativa: Python con la librería `codecs`

`python3 -c "import codecs; print(codecs.decode(open('data.txt').read(), 'rot13'))"`

Python ya trae ROT13 como una codificación reconocida dentro de la
librería `codecs`, por lo que no es necesario armar el mapeo de letras
a mano como con `tr`. Antes de usar este método, confirmé que Python
estuviera disponible **en el servidor de Bandit**  con:

`python3 --version` y `which python3`

### Recordatorio importante: SSH controla una máquina remota, no la propia

Al estar conectada por SSH, todos los comandos (incluyendo
`python3 --version`) se ejecutan en el servidor de Bandit, una máquina
compartida por muchos usuarios distintos, no en mi computadora local.

## ⚙️ Comandos utilizados
`cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'`

`python3 -c "import codecs; print(codecs.decode(open('data.txt').read(), 'rot13'))"`

- `cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'` — decodifica ROT13 usando reemplazo de caracteres letra por letra.
- `python3 -c "..."` — decodifica ROT13 usando la librería `codecs` de Python, sin necesidad de mapear el alfabeto manualmente.

## 📝 Notas personales

Entender la sintaxis de `tr` me costó bastante, en particular, por qué
el segundo conjunto de caracteres necesita estar partido en cuatro
pedazos en vez de ser simplemente "N-Zn-z". Verlo como una tabla de
posiciones  o como un círculo (en vez de solo memorizar el patrón) fue lo que finalmente
lo aclaró. Resolver el mismo nivel también con Python me ayudó a
confirmar el resultado y a ver que un mismo problema puede resolverse
con distintas herramientas, cada una con su propio nivel de
abstracción.

## 📚 Recursos de consulta

- [man tr](https://man7.org/linux/man-pages/man1/tr.1.html)
- [Linux Command Library: rot13](https://linuxcommandlibrary.com/man/rot13)
- [ROT13 Explained: Inventive HQ Team](https://inventivehq.com/blog/what-is-rot13-and-how-does-it-differ-from-other-ciphers)

