# Level 6

## 🎯 Objetivo

Encontrar, en cualquier parte del **servidor**,
un archivo con las siguientes propiedades: propiedad del usuario
bandit7, propiedad del grupo bandit6, y 33 bytes de tamaño.

## 💡 Conceptos aprendidos

- `find /` busca desde la raíz del sistema, es decir, en absolutamente
  todas las carpetas a las que el usuario tenga acceso — necesario
  cuando el objetivo dice "somewhere on the server" en vez de referirse
  a una carpeta específica.
- `-user nombre` filtra archivos por el usuario propietario.
- `-group nombre` filtra archivos por el grupo propietario.
- Al buscar en todo el sistema, es normal recibir muchos mensajes de
  "Permission denied" — significa que el usuario actual no tiene
  acceso a ciertas carpetas de otros usuarios, no que algo esté roto.
- Cada comando tiene dos canales de salida: `1` (resultado normal,
  stdout) y `2` (errores, stderr). Redirigir con `2>/dev/null` envía
  los mensajes de error a un destino que los descarta, dejando en
  pantalla solo los resultados reales.

## ⚙️ Comandos utilizados
`find / -user bandit7 -group bandit6 -size 33c 2>/dev/null`

- `find /` — busca en todo el sistema desde la raíz.
- `-user bandit7` / `-group bandit6` — filtra por propietario y grupo.
- `-size 33c` — filtra por tamaño exacto.
- `2>/dev/null` — oculta los mensajes de error de permisos, mostrando solo resultados válidos.

## 📝 Notas personales

Al principio corrí el comando sin el filtro de tamaño y sin
`2>/dev/null`, y la pantalla se llenó de "Permission denied" que
tapaban cualquier resultado útil. Entender la diferencia entre stdout
y stderr fue clave para limpiar la salida y quedarme solo con lo que
necesitaba.

## 📚 Recursos de consulta

- [man find](https://man7.org/linux/man-pages/man1/find.1.html)
- [/dev/Null] (https://es.unixlinux.online/ix/1002012316.html) - sitio que explica que es /dev/null
