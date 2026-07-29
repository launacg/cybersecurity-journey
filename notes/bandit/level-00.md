# Level 0

## 🎯 Objetivo

Conectarme por primera vez al servidor de Bandit usando SSH y leer el
contenido de un archivo de texto ubicado en el directorio home, donde
se encuentra la contraseña del siguiente nivel.



## 💡 Conceptos aprendidos

- SSH (Secure Shell) permite conectarse de forma remota y segura a otra
  máquina usando solo la terminal, sin interfaz gráfica.
- El formato de conexión es `usuario@servidor`
- Un archivo de texto plano puede leerse directamente en la terminal
  sin necesidad de un editor.

## ⚙️ Comandos utilizados

ssh bandit0@bandit.labs.overthewire.org -p 2220
ls
cat readme


- `ssh` — inicia la conexión remota al servidor.
- `ls` — lista los archivos del directorio actual.
- `cat` — muestra el contenido completo de un archivo.

## 📝 Notas personales

El nivel 0 usa una credencial pública de inicio (no es un reto que se
resuelve, es el punto de partida del juego):
- contraseña: `bandit0`
- La contraseña no se muestra en pantalla mientras se escribe (ni con
asteriscos ni puntos): es el comportamiento normal de las terminales
Linux por seguridad, no un error.

## 📚 Recursos de consulta

- [man ssh](https://man7.org/linux/man-pages/man1/ssh.1.html)
- [explainshell.com](https://explainshell.com/) — para desglosar cualquier comando línea por línea
