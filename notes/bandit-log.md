# 🧭 Bandit log

## 🗺️ Qué es esto

[OverTheWire Bandit](https://overthewire.org/wargames/bandit/) es un wargame de seguridad: un servidor real al que te conectas por SSH, donde cada nivel esconde la contraseña del siguiente dentro de retos de línea de comandos (Linux, permisos, procesos, etc.). Por las reglas del sitio, no publico contraseñas sino que documento el objetivo con mis palabras, el comando usado y qué aprendí.

---

## 🧭 Bandit Level 0 → 1

### 🎯 Objetivo del nivel
Conectarme por SSH al servidor y leer el contenido de un archivo de texto ubicado en el directorio home, donde está la contraseña del siguiente nivel.

### 📂 Comandos usados
- `ssh usuario@servidor -p puerto` — conexión remota segura
- `ls` — listar archivos del directorio actual
- `cat archivo` — mostrar contenido de un archivo
  
### 🧠 Aprendizajes
- `cat` muestra el contenido completo de un archivo de texto en la terminal.

