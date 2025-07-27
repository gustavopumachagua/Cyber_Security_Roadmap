| **Inicio**         | **Siguiente 2**                                                     |
| ------------------ | ------------------------------------------------------------------- |
| [🏠](../README.md) | [⏩](./7_2_Introduccion_a_la_Administracion_de_Servidores_Linux.md) |

---

## **Índice**

| Temario                                                                                                |
| ------------------------------------------------------------------------------------------------------ |
| [590. ¿Qué es la terminal?](#590-qué-es-la-terminal)                                                   |
| [591. Instalar WSL - usa Linux dentro de Windows](#591-instalar-wsl---usa-linux-dentro-de-windows)     |
| [592. Aprendiendo a caminar en la terminal](#592-aprendiendo-a-caminar-en-la-terminal)                 |
| [593. Manipulando archivos y directorios](#593-manipulando-archivos-y-directorios)                     |
| [594. Explorando el contenido de nuestros archivos](#594-explorando-el-contenido-de-nuestros-archivos) |
| [595. ¿Qué es un comando?](#595-qué-es-un-comando)                                                     |
| [596. Wildcards](#596-wildcards)                                                                       |
| [597. Redirecciones: cómo funciona la shell](#597-redirecciones-cómo-funciona-la-shell)                |
| [598. Redirecciones: pipe operator](#598-redirecciones-pipe-operator)                                  |
| [599. Encadenando comandos: operadores de control](#599-encadenando-comandos-operadores-de-control)    |
| [600. Cómo se manejan los permisos](#600-cómo-se-manejan-los-permisos)                                 |
| [601. Modificando permisos en la terminal](#601-modificando-permisos-en-la-terminal)                   |
| [602. Cómo configurar variables de entorno](#602-cómo-configurar-variables-de-entorno)                 |
| [603. Comandos de búsqueda](#603-comandos-de-búsqueda)                                                 |
| [604. Usando el comando grep](#604-usando-el-comando-grep)                                             |
| [605. Utilidades de red](#605-utilidades-de-red)                                                       |
| [606. Comprimiendo archivos tar y zip](#606-comprimiendo-archivos-tar-y-zip)                           |
| [607. Manejo de procesos](#607-manejo-de-procesos)                                                     |
| [608. Procesos en foreground y background](#608-procesos-en-foreground-y-background)                   |
| [609. Editores de texto en la terminal](#609-editores-de-texto-en-la-terminal)                         |
| [610. Personalizar la terminal de comandos](#610-personalizar-la-terminal-de-comandos)                 |

---

# **Introducción a la Terminal y Línea de Comandos**

## **590. ¿Qué es la terminal?**

### ✅ ¿Qué es la terminal?

La **terminal** (también llamada **línea de comandos**, **CLI** por Command Line Interface o **consola**) es una **herramienta de texto** que te permite **comunicarte con el sistema operativo** escribiendo comandos.

En vez de hacer clic en botones como en una interfaz gráfica (GUI), con la terminal **escribes instrucciones directamente** al sistema.

#### 📌 ¿Para qué sirve?

- Navegar por carpetas y archivos.
- Instalar o desinstalar programas.
- Automatizar tareas.
- Desarrollar software.
- Administrar servidores.
- Usar herramientas como `git`, `npm`, `python`, `ping`, etc.
- Acceder al sistema si la interfaz gráfica falla.

---

### 🖥️ Tipos de terminal según tu sistema operativo

| Sistema Operativo | Terminal principal                               |
| ----------------- | ------------------------------------------------ |
| Windows           | **CMD** o **PowerShell**, o **Windows Terminal** |
| Linux             | **Bash**, **Zsh**, **Terminal de GNOME**, etc.   |
| macOS             | **Terminal** (aplicación preinstalada)           |

---

### 🔧 ¿Cómo se instala o accede?

#### 🟦 En Windows

1. **CMD o PowerShell**:

   - Presiona `Win + R`, escribe `cmd` o `powershell` y presiona Enter.

2. **Windows Terminal** (más moderno):

   - Si no lo tienes, instálalo desde la Microsoft Store.
   - Abre el menú de inicio y escribe "Windows Terminal".

> También puedes usar **Git Bash** (cuando instalas Git) o **WSL** (Subsistema de Windows para Linux).

---

#### 🐧 En Linux

- La terminal **ya viene preinstalada**.
- Puedes abrirla con:

  - El atajo: `Ctrl + Alt + T`
  - Buscando “Terminal” en el menú de aplicaciones.

---

#### 🍎 En macOS

- La terminal también **ya está incluida**.
- Ve a:

  - `Aplicaciones` > `Utilidades` > `Terminal`.

---

### 🧠 Conceptos clave (con ejemplos simples)

| Comando         | ¿Qué hace?                            | Ejemplo                    |
| --------------- | ------------------------------------- | -------------------------- |
| `pwd`           | Muestra la ruta donde estás           | `/home/gustavo/Documentos` |
| `ls` o `dir`    | Lista archivos/carpetas               | `ls`                       |
| `cd`            | Cambia de carpeta                     | `cd Descargas`             |
| `mkdir`         | Crea una nueva carpeta                | `mkdir proyecto1`          |
| `touch`         | Crea un archivo vacío (Linux/mac)     | `touch notas.txt`          |
| `echo`          | Escribe texto en consola o en archivo | `echo Hola mundo`          |
| `cls` o `clear` | Limpia la pantalla                    | `clear`                    |
| `exit`          | Cierra la terminal                    | `exit`                     |

---

### ✅ Ejemplo completo paso a paso

Imaginemos que quieres crear un proyecto de texto en una carpeta, todo usando la terminal.

#### 🔹 Objetivo:

Crear una carpeta llamada `mi_proyecto`, con un archivo llamado `notas.txt` que diga **"Hola Gustavo"**.

---

#### 👣 Pasos:

1. **Abrir la terminal**.

   - En Windows: busca `cmd` o `PowerShell`.
   - En Linux/macOS: presiona `Ctrl + Alt + T`.

---

2. **Ver dónde estás**:

   ```bash
   pwd
   ```

   Salida posible:

   ```
   /home/gustavo
   ```

---

3. **Crear la carpeta**:

   ```bash
   mkdir mi_proyecto
   ```

---

4. **Entrar a esa carpeta**:

   ```bash
   cd mi_proyecto
   ```

---

5. **Crear el archivo de texto**:

   ```bash
   touch notas.txt  # En Linux o macOS
   ```

   En Windows usa:

   ```cmd
   echo. > notas.txt
   ```

---

6. **Escribir en el archivo**:

   ```bash
   echo Hola Gustavo > notas.txt
   ```

---

7. **Ver el contenido del archivo**:

   - En Linux/macOS:

     ```bash
     cat notas.txt
     ```

   - En Windows:

     ```cmd
     type notas.txt
     ```

   Resultado:

   ```
   Hola Gustavo
   ```

---

### 🧩 ¿Y qué más se puede hacer con la terminal?

- Instalar paquetes (como `npm install`, `apt install`, `pip install`).
- Controlar Git para proyectos de programación.
- Conectarse a servidores remotos con `ssh`.
- Ejecutar scripts (`.sh`, `.py`, `.js`).
- Usar herramientas como Docker, Node.js, Python, etc.

---

### 🧠 Conclusión

La **terminal** es como una **puerta directa al sistema operativo**, mucho más poderosa que la interfaz gráfica. Aprenderla te da **más control, velocidad y flexibilidad**, sobre todo como desarrollador o especialista en ciberseguridad.

---

[🔼](#índice)

---

## **591. Instalar WSL - usa Linux dentro de Windows**

### 🐧 ¿Qué es WSL?

**WSL** significa **Windows Subsystem for Linux** (**Subsistema de Windows para Linux**).

> Es una **función de Windows** que te permite **usar una distribución de Linux** (como Ubuntu, Debian, Kali, etc.) **dentro de Windows**, **sin necesidad de una máquina virtual** o de borrar tu sistema operativo.

En otras palabras:

> **Puedes usar Linux en Windows como si fuera una app**, desde la terminal.

---

### 🎯 ¿Para qué sirve?

- Usar herramientas de desarrollo que solo existen en Linux (como `bash`, `apt`, `curl`, `vim`, etc.).
- Practicar comandos de Linux sin salir de Windows.
- Usar Docker, Python, Node.js, Git, etc. como en un entorno de servidor.
- Hacer tareas de ciberseguridad y pentesting (si usas Kali Linux en WSL).

---

### 🧰 Requisitos para instalar WSL

- Tener **Windows 10 (versión 2004 o superior)** o **Windows 11**.
- Tener habilitado el **Subsistema de Windows para Linux**.
- Tener conexión a Internet.

---

### 🧭 ✅ Cómo instalar WSL paso a paso (fácil)

#### 🔹 Paso 1: Abre PowerShell como administrador

1. Pulsa `Inicio`, escribe **PowerShell**.
2. Haz clic derecho en **Windows PowerShell** y selecciona **"Ejecutar como administrador"**.

---

#### 🔹 Paso 2: Ejecuta el siguiente comando

```powershell
wsl --install
```

Esto hará lo siguiente:

- Instala WSL automáticamente.
- Descarga e instala **Ubuntu** (por defecto).
- Configura el entorno Linux.

🔁 Espera a que termine. Luego se reiniciará tu computadora.

---

#### 🔹 Paso 3: Configura tu usuario de Linux

Cuando reinicie tu PC, verás algo así:

```
Installing, this may take a few minutes...
Please create a default UNIX user account.
Enter new UNIX username:
```

➡ Escribe un nombre de usuario (ej. `gustavo`), y una contraseña.

🎉 ¡Listo! Ya estás usando **Linux dentro de Windows** con Ubuntu.

---

#### 📝 Opcional: Instalar otra distribución de Linux

Puedes elegir otras distribuciones como:

```powershell
wsl --list --online
```

Ejemplo para instalar Debian:

```powershell
wsl --install -d Debian
```

---

### 🖥️ Cómo abrir WSL (Ubuntu o la distro que hayas instalado)

Puedes abrirlo de varias formas:

1. Abre el menú de inicio y busca “**Ubuntu**” (o “Debian”, “Kali Linux”, etc.)
2. O desde Windows Terminal, selecciona la pestaña de tu distro Linux.
3. También puedes usar:

```powershell
wsl
```

Desde PowerShell o CMD.

---

### 🎯 ¿Cómo saber si WSL está funcionando?

Una vez que tengas la terminal Linux abierta, prueba escribir:

```bash
uname -a
```

Salida esperada:

```
Linux GUSSOFT 5.15.90.1-microsoft-standard-WSL2 ...
```

O prueba un comando clásico de Linux:

```bash
ls
```

---

### ✅ Ejemplo completo: crear un proyecto desde WSL

#### 🎯 Objetivo:

Crear una carpeta llamada `mi_app`, con un archivo `app.py` de Python que imprima "Hola desde WSL".

---

#### 👣 Pasos desde la terminal WSL (Ubuntu)

1. **Abrir la terminal WSL** (Ubuntu).

---

2. **Ir a tu carpeta personal**:

```bash
cd ~
```

---

3. **Crear una carpeta nueva**:

```bash
mkdir mi_app
```

---

4. **Entrar a esa carpeta**:

```bash
cd mi_app
```

---

5. **Crear un archivo Python**:

```bash
nano app.py
```

Escribe esto dentro:

```python
print("Hola desde WSL")
```

Luego presiona:

- `Ctrl + O` (para guardar),
- Enter (para confirmar),
- `Ctrl + X` (para salir).

---

6. **Ejecutar el archivo**:

```bash
python3 app.py
```

🟢 Resultado:

```
Hola desde WSL
```

---

### 🧠 Conclusión

| Ventajas de WSL en Windows                         |
| -------------------------------------------------- |
| Usas Linux sin máquina virtual.                    |
| Acceso a herramientas de desarrollo potentes.      |
| Ideal para programadores, DevOps y ciberseguridad. |
| Fácil de instalar y ligero.                        |

---

### 💡 ¿Y después?

Puedes instalar cosas como:

- `git`, `curl`, `htop`, `vim`, etc.
- Usar `pip` para Python, `npm` para Node.js.
- Conectarte con VS Code (`code .`) usando la extensión **Remote - WSL**.
- Incluso usar herramientas de **hacking ético** con **Kali Linux en WSL**.

---

[🔼](#índice)

---

## **592. Aprendiendo a caminar en la terminal**

### 🧭 ¿Qué significa “caminar en la terminal”?

“Caminar” significa **navegar entre carpetas y archivos** del sistema usando solo comandos, sin el mouse.

Es como abrir el Explorador de archivos, pero con texto.

---

#### 🧱 Conceptos básicos para caminar

#### 📂 Directorios (o carpetas)

- Son lugares donde se agrupan archivos o más carpetas.
- Se representan como una estructura jerárquica, ejemplo:

  ```
  /home/gustavo/proyectos/mi_app
  ```

#### 📄 Archivos

- Son contenidos dentro de carpetas, como documentos, scripts, imágenes, etc.

---

### 🧠 Comandos básicos para caminar (navegar) en la terminal

| Comando         | Significado                             | Ejemplo           |
| --------------- | --------------------------------------- | ----------------- |
| `pwd`           | Muestra en qué carpeta estás            | `/home/gustavo`   |
| `ls`            | Lista el contenido de la carpeta actual | `ls`              |
| `cd NOMBRE`     | Cambia de carpeta                       | `cd Documentos`   |
| `cd ..`         | Sube un nivel (a la carpeta anterior)   | `cd ..`           |
| `cd /`          | Ir al inicio del sistema (root)         | `cd /`            |
| `mkdir NOMBRE`  | Crea una nueva carpeta                  | `mkdir proyectos` |
| `touch archivo` | Crea un archivo vacío                   | `touch notas.txt` |
| `clear`         | Limpia la pantalla                      | `clear`           |

---

### 📍 Ejemplo visual de estructura de carpetas

```
/home/gustavo
├── Documentos
│   └── cv.pdf
├── Proyectos
│   ├── web
│   │   └── index.html
│   └── app
│       └── main.py
```

---

### ✅ ¿Cómo instalar y abrir la terminal?

Esto depende de tu sistema:

| Sistema | Cómo abrir la terminal                   |
| ------- | ---------------------------------------- |
| WSL     | Busca “Ubuntu” o abre `Windows Terminal` |
| Windows | `Win + R` → escribe `cmd` o `powershell` |
| Linux   | `Ctrl + Alt + T` o busca “Terminal”      |
| macOS   | Aplicaciones > Utilidades > Terminal     |

---

### 🧪 Ejemplo completo paso a paso: **Caminar, crear y moverte por carpetas**

Vamos a simular que estás **explorando tu propio sistema**, como si caminaras por tu casa.

---

### 🎯 Objetivo

1. Ver dónde estás.
2. Crear una carpeta llamada `exploracion`.
3. Entrar a ella.
4. Crear una carpeta `notas` y un archivo `lista.txt`.
5. Subir una carpeta hacia atrás.
6. Ver todo con `ls`.

---

#### 👣 Paso 1: Ver tu ubicación actual

```bash
pwd
```

📌 Resultado:

```
/home/gustavo
```

Esto te dice: “Estás en la carpeta personal llamada `gustavo`”.

---

#### 👣 Paso 2: Crear una carpeta nueva

```bash
mkdir exploracion
```

Acabas de crear una carpeta llamada `exploracion`.

---

#### 👣 Paso 3: Entra a esa carpeta

```bash
cd exploracion
```

Ahora estás **dentro** de la carpeta `exploracion`.

---

#### 👣 Paso 4: Crear más cosas dentro

```bash
mkdir notas
touch lista.txt
```

Esto crea:

- Una carpeta `notas`.
- Un archivo vacío `lista.txt`.

---

#### 👣 Paso 5: Subir una carpeta (regresar)

```bash
cd ..
```

Ahora volviste a tu carpeta inicial (`/home/gustavo`).

---

#### 👣 Paso 6: Ver lo que tienes

```bash
ls
```

📌 Resultado esperado:

```
Documentos  exploracion  Descargas
```

---

#### 👣 Paso 7: Ver lo que hay dentro de `exploracion`

```bash
ls exploracion
```

📌 Resultado esperado:

```
lista.txt  notas
```

---

### 🛠️ Nivel Extra (si quieres)

Si escribes:

```bash
tree exploracion
```

Verás algo como:

```
exploracion
├── lista.txt
└── notas
```

(Si `tree` no está instalado, puedes instalarlo en Ubuntu con: `sudo apt install tree`)

---

### 🧠 Resumen gráfico de comandos de navegación

```
pwd           ← Dónde estoy
ls            ← Qué hay aquí
cd carpeta    ← Entra a una carpeta
cd ..         ← Regresa una carpeta atrás
mkdir         ← Crea una carpeta
touch         ← Crea un archivo vacío
clear         ← Limpia la pantalla
```

---

### 🎓 Conclusión

> Aprender a **caminar en la terminal** te da libertad, poder y velocidad. Ya no dependes del mouse para trabajar. Es fundamental para desarrolladores, sysadmins, ciberseguridad, y más.

---

[🔼](#índice)

---

## **593. Manipulando archivos y directorios**

### 🧠 ¿Qué significa “manipular archivos y directorios”?

Significa usar comandos para **hacer acciones sobre archivos o carpetas**, como:

| Acción        | Ejemplo en la vida real                   |
| ------------- | ----------------------------------------- |
| Crear         | Crear una nueva carpeta o archivo         |
| Mover         | Cambiar de lugar un archivo o carpeta     |
| Copiar        | Hacer una copia de algo                   |
| Renombrar     | Cambiar el nombre de un archivo o carpeta |
| Eliminar      | Borrar un archivo o carpeta               |
| Ver contenido | Leer lo que hay dentro de un archivo      |

---

### ✅ Cómo manipular archivos y carpetas desde la terminal

A continuación te muestro los comandos más importantes con ejemplos **fáciles y reales**.

---

#### 📁 1. Crear archivos y carpetas

| Acción        | Comando            | Ejemplo           |
| ------------- | ------------------ | ----------------- |
| Crear carpeta | `mkdir nombre`     | `mkdir proyectos` |
| Crear archivo | `touch nombre.ext` | `touch notas.txt` |

---

#### 📂 2. Ver archivos y carpetas

| Comando | Significado                               |
| ------- | ----------------------------------------- |
| `ls`    | Ver contenido de una carpeta              |
| `ls -l` | Ver detalles (tamaño, permisos, fechas)   |
| `ls -a` | Ver archivos ocultos también              |
| `tree`  | Ver en forma de árbol (si está instalado) |

---

#### 🚚 3. Mover y renombrar archivos

Usamos el mismo comando: `mv`

| Acción            | Comando                           | Ejemplo                           |
| ----------------- | --------------------------------- | --------------------------------- |
| Mover archivo     | `mv archivo carpeta/`             | `mv carta.txt Documentos/`        |
| Renombrar         | `mv viejo.txt nuevo.txt`          | `mv lista.txt tareas.txt`         |
| Mover y renombrar | `mv archivo carpeta/nuevo_nombre` | `mv imagen.jpg Fotos/perrito.jpg` |

---

#### 📄 4. Copiar archivos o carpetas

Usamos el comando `cp`

| Acción                  | Comando                       | Ejemplo                            |
| ----------------------- | ----------------------------- | ---------------------------------- |
| Copiar archivo          | `cp archivo copia`            | `cp notas.txt copia_notas.txt`     |
| Copiar en otra carpeta  | `cp archivo carpeta/`         | `cp datos.txt respaldo/`           |
| Copiar carpeta completa | `cp -r carpeta nueva_carpeta` | `cp -r proyectos proyectos_backup` |

📌 El `-r` significa **"recursivo"**, y es necesario para copiar carpetas enteras.

---

#### 🗑️ 5. Eliminar archivos o carpetas

| Acción             | Comando          | Ejemplo                  |
| ------------------ | ---------------- | ------------------------ |
| Eliminar archivo   | `rm archivo`     | `rm tareas.txt`          |
| Eliminar carpeta   | `rm -r carpeta`  | `rm -r proyectos_viejos` |
| Forzar eliminación | `rm -rf carpeta` | `rm -rf temp`            |

⚠️ **¡Cuidado con `rm -rf`!** No pide confirmación y **borra todo sin posibilidad de recuperación**.

---

#### 📖 6. Leer archivos de texto

| Acción              | Comando            | Ejemplo              |
| ------------------- | ------------------ | -------------------- |
| Ver contenido       | `cat archivo.txt`  | `cat notas.txt`      |
| Leer por páginas    | `less archivo.txt` | `less historial.log` |
| Ver primeras líneas | `head archivo.txt` | `head notas.txt`     |
| Ver últimas líneas  | `tail archivo.txt` | `tail notas.txt`     |

---

### ✅ Ejemplo completo paso a paso

#### 🎯 Objetivo

Simulemos una actividad de trabajo:

1. Crear un directorio `clientes`.
2. Crear un archivo `listado.txt` con nombres.
3. Hacer una copia del archivo.
4. Mover esa copia a una carpeta `respaldo`.
5. Renombrar el archivo original.
6. Leer el archivo renombrado.
7. Eliminar el archivo de respaldo y la carpeta.

---

#### 👣 Paso a paso en la terminal (WSL, Linux o macOS)

##### Paso 1: Crear la carpeta principal

```bash
mkdir clientes
cd clientes
```

---

##### Paso 2: Crear un archivo con contenido

```bash
echo "Ana\nPedro\nLuisa" > listado.txt
```

✅ Crea un archivo con tres nombres.

---

##### Paso 3: Hacer una copia

```bash
cp listado.txt copia_listado.txt
```

---

##### Paso 4: Crear una carpeta de respaldo y mover la copia

```bash
mkdir respaldo
mv copia_listado.txt respaldo/
```

---

##### Paso 5: Renombrar el archivo original

```bash
mv listado.txt clientes_vip.txt
```

---

##### Paso 6: Leer el contenido del archivo

```bash
cat clientes_vip.txt
```

🟢 Resultado:

```
Ana
Pedro
Luisa
```

---

##### Paso 7: Eliminar archivo y carpeta de respaldo

```bash
rm respaldo/copia_listado.txt
rmdir respaldo
```

✅ ¡Listo! Acabas de practicar **crear, copiar, mover, renombrar, leer y eliminar** archivos y carpetas.

---

### 🧠 Resumen de comandos usados

```bash
mkdir          → crear carpeta
touch          → crear archivo
echo           → escribir texto en archivo
cp             → copiar archivo o carpeta
mv             → mover o renombrar
rm             → eliminar archivo
rmdir          → eliminar carpeta vacía
cat            → mostrar contenido
```

---

[🔼](#índice)

---

## **594. Explorando el contenido de nuestros archivos**

### 🔍 ¿Qué significa "explorar el contenido de nuestros archivos"?

Significa **leer o visualizar archivos directamente desde la terminal** para:

- Ver su contenido línea por línea.
- Buscar palabras clave dentro del archivo.
- Mostrar solo ciertas partes (principio, final, coincidencias).
- Navegar por archivos largos.
- Revisar configuraciones o scripts rápidamente.

---

### 📄 Tipos de archivos que puedes explorar fácilmente

- Archivos de texto (`.txt`)
- Scripts (`.sh`, `.py`, `.js`)
- Archivos de configuración (`.conf`, `.ini`)
- Archivos de log (`.log`)
- CSVs (`.csv`)
- Markdown (`.md`)

⚠️ **No se usa para abrir imágenes, PDF o binarios.**

---

### 🧠 Comandos principales para explorar contenido

Aquí tienes los más usados, explicados con ejemplos simples.

---

#### 🧾 1. `cat` → Mostrar el contenido completo

```bash
cat archivo.txt
```

📌 Muestra todo el archivo en una sola salida.

**Ejemplo:**

```bash
cat lista.txt
```

Salida:

```
Ana
Pedro
Luisa
```

---

#### 📖 2. `less` → Leer por páginas (ideal para archivos largos)

```bash
less archivo.txt
```

Te permite **navegar con flechas**, avanzar con espacio, y salir con `q`.

**Ejemplo:**

```bash
less libro.txt
```

---

#### 📚 3. `more` → Similar a `less`, más simple

```bash
more archivo.txt
```

Navegas con barra espaciadora, sales con `q`.

---

#### 🔍 4. `head` → Ver las primeras líneas

```bash
head archivo.txt
```

🔸 Por defecto muestra las **primeras 10 líneas**.

**Ejemplo:**

```bash
head listado.log
```

👉 Para ver 5 líneas:

```bash
head -n 5 listado.log
```

---

#### 🔻 5. `tail` → Ver las últimas líneas

```bash
tail archivo.txt
```

🔸 Ideal para monitorear logs.

**Ejemplo:**

```bash
tail -n 10 error.log
```

👉 Para ver las últimas 50 líneas:

```bash
tail -n 50 acceso.log
```

---

#### 📡 6. `tail -f` → Seguir archivo en tiempo real

```bash
tail -f archivo.log
```

🔄 Muy usado para **ver en tiempo real lo que se escribe en un archivo** (logs de servidores, por ejemplo).

---

#### 🔎 7. `grep` → Buscar palabras dentro de un archivo

```bash
grep palabra archivo.txt
```

🔍 Muestra **líneas que contienen la palabra buscada**.

**Ejemplo:**

```bash
grep "error" sistema.log
```

👉 Para que no distinga mayúsculas:

```bash
grep -i "error" sistema.log
```

👉 Para buscar varias palabras:

```bash
grep -E "error|fail|fatal" sistema.log
```

---

### 🧪 Ejemplo completo paso a paso

#### 🎯 Objetivo

Simulemos que tienes un archivo llamado `clientes.txt` con esta información:

```
# clientes.txt
Ana, Lima
Pedro, Cusco
Luisa, Arequipa
Carlos, Lima
Lucía, Trujillo
Mario, Cusco
```

Vamos a:

1. Leer todo el archivo.
2. Ver solo las primeras líneas.
3. Buscar clientes de "Cusco".
4. Ver si hay algún cliente de "Piura".
5. Ver el archivo con paginación.

---

#### 👣 Paso 1: Crear el archivo (si no lo tienes)

```bash
echo -e "Ana, Lima\nPedro, Cusco\nLuisa, Arequipa\nCarlos, Lima\nLucía, Trujillo\nMario, Cusco" > clientes.txt
```

---

#### 👣 Paso 2: Leer todo con `cat`

```bash
cat clientes.txt
```

Resultado:

```
Ana, Lima
Pedro, Cusco
Luisa, Arequipa
Carlos, Lima
Lucía, Trujillo
Mario, Cusco
```

---

#### 👣 Paso 3: Ver las primeras 3 líneas

```bash
head -n 3 clientes.txt
```

Resultado:

```
Ana, Lima
Pedro, Cusco
Luisa, Arequipa
```

---

#### 👣 Paso 4: Buscar clientes de Cusco

```bash
grep "Cusco" clientes.txt
```

Resultado:

```
Pedro, Cusco
Mario, Cusco
```

---

#### 👣 Paso 5: Buscar si hay alguien de Piura

```bash
grep "Piura" clientes.txt
```

Resultado:
(Sin resultados, lo que indica que no hay nadie de Piura)

---

#### 👣 Paso 6: Ver el archivo con paginación

```bash
less clientes.txt
```

Usa flechas arriba/abajo o espacio, y presiona `q` para salir.

---

### 🧠 Resumen gráfico

| Comando         | ¿Para qué sirve?                  |
| --------------- | --------------------------------- |
| `cat`           | Ver todo el contenido             |
| `less` / `more` | Leer por páginas                  |
| `head` / `tail` | Ver principio o final del archivo |
| `grep`          | Buscar dentro del archivo         |
| `tail -f`       | Seguir en tiempo real             |

---

### 🧰 ¿Cómo instalar si algún comando no está?

En distribuciones Linux (como Ubuntu en WSL), puedes instalar con:

```bash
sudo apt update
sudo apt install less grep coreutils
```

En Windows con PowerShell no están disponibles directamente, pero **en WSL sí los tienes** por defecto.

---

### 🎓 Conclusión

Explorar el contenido de archivos en la terminal te permite:

- Revisar logs y configuraciones sin abrir un editor.
- Buscar errores o datos específicos rápidamente.
- Hacer análisis básico sin abrir VS Code ni Notepad.

---

[🔼](#índice)

---

## **595. ¿Qué es un comando?**

### 🧠 ¿Qué es un comando?

Un **comando** es una **instrucción escrita que tú le das al sistema operativo a través de la terminal** para que haga algo por ti.

> Es como hablarle directamente al sistema con una frase específica que él entiende y ejecuta.

---

### 🗣️ Ejemplo comparativo:

| Lo que haces con el mouse       | Comando equivalente en terminal |
| ------------------------------- | ------------------------------- |
| Abrir el explorador de archivos | `ls` (lista el contenido)       |
| Abrir una carpeta               | `cd nombre-de-carpeta`          |
| Crear una carpeta               | `mkdir nombre`                  |
| Eliminar un archivo             | `rm archivo.txt`                |
| Ver un documento de texto       | `cat archivo.txt`               |

---

### 🔄 Cómo se ejecuta un comando

Simplemente **escribes el comando en la terminal y presionas Enter**.

#### Ejemplo:

```bash
echo "Hola Gustavo"
```

💬 Salida:

```
Hola Gustavo
```

---

### 📦 ¿De dónde vienen los comandos?

Los comandos pueden ser:

| Tipo de comando               | Descripción                                         | Ejemplo                         |
| ----------------------------- | --------------------------------------------------- | ------------------------------- |
| Comando del sistema (interno) | Vienen con el sistema operativo (bash, Linux, etc.) | `cd`, `ls`, `echo`              |
| Comando externo (programa)    | Se instalan por separado                            | `git`, `python`, `node`, `htop` |
| Alias o script                | Son comandos que tú puedes crear                    | `ll` (alias para `ls -l`)       |

---

### ✅ ¿Cómo se “instala” un comando?

Hay comandos que **ya vienen listos** en tu sistema (como `ls`, `cd`, `mkdir`), y otros que **tienes que instalar** como programas.

#### 🐧 En Ubuntu (Linux, WSL, macOS con Homebrew), puedes instalar con:

```bash
sudo apt update
sudo apt install nombre-del-comando
```

🔸 Ejemplo: instalar el comando `htop` (monitor de recursos):

```bash
sudo apt install htop
```

---

### ⚠️ ¿Y si el comando no está instalado?

Si escribes un comando que **no existe**, te saldrá algo como:

```
comando: no se encontró la orden
```

O en inglés:

```
command not found
```

---

### 🧪 Comandos más comunes (y fáciles de entender)

| Comando | ¿Qué hace?                           |
| ------- | ------------------------------------ |
| `pwd`   | Muestra la carpeta actual            |
| `ls`    | Lista archivos y carpetas            |
| `cd`    | Cambia de carpeta                    |
| `mkdir` | Crea una nueva carpeta               |
| `touch` | Crea un archivo vacío                |
| `echo`  | Imprime texto en pantalla o archivo  |
| `cat`   | Muestra el contenido de un archivo   |
| `rm`    | Elimina un archivo                   |
| `cp`    | Copia archivos o carpetas            |
| `mv`    | Mueve o renombra archivos o carpetas |

---

### 🧠 Cómo saber más sobre un comando

| Comando de ayuda | ¿Para qué sirve?                          |
| ---------------- | ----------------------------------------- |
| `man comando`    | Muestra el manual del comando             |
| `comando --help` | Muestra una ayuda corta sobre cómo usarlo |

🔸 Ejemplo:

```bash
ls --help
```

---

### ✅ Ejemplo completo paso a paso

#### 🎯 Objetivo: Practicar 5 comandos básicos y entender qué hacen

---

#### 👣 Paso 1: Abrir la terminal

Si estás usando **WSL o Linux/macOS**, abre la terminal. En Windows puedes usar WSL o CMD/Powershell (aunque algunos comandos no funcionan igual fuera de WSL).

---

#### 👣 Paso 2: Ver dónde estás

```bash
pwd
```

🟢 Resultado:

```
/home/gustavo
```

✅ El comando `pwd` te dice “¿En qué carpeta estoy parado?”

---

#### 👣 Paso 3: Ver lo que hay en tu carpeta

```bash
ls
```

🟢 Resultado:

```
Documentos  Descargas  Escritorio
```

✅ El comando `ls` es como abrir una carpeta y mirar lo que hay dentro.

---

#### 👣 Paso 4: Crear una nueva carpeta

```bash
mkdir prueba_comandos
```

✅ Acabas de usar el comando `mkdir` para **crear una carpeta nueva**.

---

#### 👣 Paso 5: Entrar a esa carpeta

```bash
cd prueba_comandos
```

✅ Ahora estás **dentro** de la carpeta.

---

#### 👣 Paso 6: Crear un archivo

```bash
echo "Hola Gustavo desde la terminal" > saludo.txt
```

✅ El comando `echo` imprimió un texto y `>` lo guardó en un archivo.

---

#### 👣 Paso 7: Ver el contenido del archivo

```bash
cat saludo.txt
```

🟢 Resultado:

```
Hola Gustavo desde la terminal
```

✅ Usaste el comando `cat` para **leer el archivo**.

---

### 🧠 Conclusión rápida

| Concepto       | Explicación                                      |
| -------------- | ------------------------------------------------ |
| Comando        | Instrucción escrita para el sistema              |
| Se ejecuta con | Escribirlo en la terminal y presionar Enter      |
| Tipos          | Internos, externos (programas), o personalizados |
| Para ver ayuda | `--help` o `man comando`                         |
| Instalación    | Algunos ya vienen, otros se instalan con `apt`   |

---

[🔼](#índice)

---

## **596. Wildcards**

### 🌟 ¿Qué son los Wildcards?

Los **wildcards** (comodines) son **símbolos especiales** que te permiten **trabajar con múltiples archivos o carpetas al mismo tiempo**, sin tener que escribir cada nombre exacto.

> ✅ Piensa en los wildcards como cuando buscas archivos con “\*.jpg” o “doc\_??.txt” en tu explorador.

---

### 🧠 ¿Para qué sirven los Wildcards?

- Buscar archivos que coincidan con un patrón.
- Copiar, mover o borrar varios archivos a la vez.
- Filtrar resultados con comandos como `ls`, `rm`, `cp`, `mv`, `cat`, etc.

---

### 🧩 Tipos de Wildcards principales

| Wildcard | Significado                                       | Ejemplo                             |
| -------- | ------------------------------------------------- | ----------------------------------- |
| `*`      | Cualquier **cantidad** de caracteres (cero o más) | `*.txt` = todos los `.txt`          |
| `?`      | Cualquier **un solo carácter**                    | `a?.txt` = `a1.txt`, `ab.txt`       |
| `[ ]`    | Cualquier **carácter dentro del grupo**           | `a[12].txt` = `a1.txt`, `a2.txt`    |
| `[! ]`   | Cualquier carácter **que no esté dentro**         | `a[!3].txt` = todo excepto `a3.txt` |

---

### 🎯 ¿Cómo se usan los Wildcards?

Se usan **como parte del nombre de archivo o carpeta** en comandos.

```bash
comando patron
```

Ejemplos:

```bash
ls *.txt         # muestra todos los archivos que terminan en .txt
rm file?.txt     # elimina file1.txt, fileA.txt, pero NO file10.txt
cp data[1-3].csv backup/   # copia data1.csv, data2.csv y data3.csv
```

---

### ⚙️ ¿Se necesita instalar algo?

✅ **No.** Los wildcards vienen **integrados en Bash (Linux, macOS, WSL)** y también funcionan en CMD/Powershell con pequeñas diferencias. **No hay que instalar nada**.

---

### 🧪 Ejemplo completo paso a paso: Usar Wildcards

#### 🎯 Objetivo:

1. Crear varios archivos de prueba.
2. Listar archivos por patrón.
3. Copiar o eliminar archivos usando comodines.
4. Ver cómo el sistema reconoce patrones.

---

#### 👣 Paso 1: Crear una carpeta de prueba

```bash
mkdir prueba_wildcards
cd prueba_wildcards
```

---

#### 👣 Paso 2: Crear varios archivos

```bash
touch archivo1.txt archivo2.txt archivo3.txt
touch imagen1.jpg imagen2.jpg
touch notaA.txt notaB.txt
touch datos1.csv datos2.csv
```

---

#### 👣 Paso 3: Usar `*` (cualquier cosa)

```bash
ls *.txt
```

🟢 Resultado:

```
archivo1.txt  archivo2.txt  archivo3.txt  notaA.txt  notaB.txt
```

✅ Muestra todos los archivos que terminan en `.txt`

---

#### 👣 Paso 4: Usar `?` (un solo carácter)

```bash
ls archivo?.txt
```

🟢 Resultado:

```
archivo1.txt  archivo2.txt  archivo3.txt
```

✅ Muestra archivos con un solo carácter después de “archivo”.

```bash
ls nota?.txt
```

🟢 Resultado:

```
notaA.txt  notaB.txt
```

---

#### 👣 Paso 5: Usar rangos con `[ ]`

```bash
ls archivo[1-2].txt
```

🟢 Resultado:

```
archivo1.txt  archivo2.txt
```

✅ Solo los archivos que terminan en 1 o 2.

---

#### 👣 Paso 6: Usar exclusiones con `[! ]`

```bash
ls archivo[!3].txt
```

🟢 Resultado:

```
archivo1.txt  archivo2.txt
```

✅ Excluye el archivo que termina en `3`.

---

#### 👣 Paso 7: Copiar archivos usando wildcards

```bash
mkdir respaldo
cp *.jpg respaldo/
```

✅ Copia todos los archivos `.jpg` a la carpeta `respaldo`.

---

#### 👣 Paso 8: Eliminar archivos con wildcard

⚠️ **Cuidado con este paso**, solo hazlo si estás seguro.

```bash
rm *.csv
```

✅ Elimina todos los archivos `.csv`.

---

### 🧠 Resumen de patrones útiles

| Patrón          | Qué hace                                                     |
| --------------- | ------------------------------------------------------------ |
| `*.txt`         | Todos los archivos que terminan en `.txt`                    |
| `a*.txt`        | Archivos que comienzan con `a` y terminan en `.txt`          |
| `*1*`           | Archivos que contienen un `1` en el nombre                   |
| `data[1-3].csv` | Solo `data1.csv`, `data2.csv`, `data3.csv`                   |
| `file?.log`     | Archivos como `file1.log`, `fileA.log`, pero NO `file10.log` |
| `[!3]*.txt`     | Archivos que **no** comienzan con `3` y terminan en `.txt`   |

---

### 🎓 Conclusión

✅ Los **wildcards** hacen que trabajar con muchos archivos sea más rápido, flexible y poderoso.

| Ventaja                     | Ejemplo                         |
| --------------------------- | ------------------------------- |
| Ahorras tiempo              | `rm *.log` borra todos los logs |
| Automatizas tareas masivas  | `cp *.txt backup/`              |
| Filtras archivos fácilmente | `ls nota?.txt`                  |

---

[🔼](#índice)

---

## **597. Redirecciones: cómo funciona la shell**

### 🧠 ¿Qué son las redirecciones?

Las **redirecciones** permiten **controlar a dónde va la salida de un comando** (como un resultado o un mensaje) o **de dónde viene su entrada** (como un archivo o texto).

> 🎯 En resumen: le dices al sistema “en lugar de mostrar esto en pantalla, guárdalo” o “en lugar de escribir algo ahora, léelo de este archivo”.

---

### 🎓 ¿Por qué son útiles?

Imagina que:

- Quieres **guardar el resultado de un comando** en un archivo.
- Quieres **usar un archivo como entrada** para otro programa.
- Quieres **ver solo los errores** que salieron de un programa.
- Quieres **unir comandos** y procesar datos paso a paso.

✅ ¡Todo eso se hace con redirecciones!

---

### 🔧 Tipos de redirecciones

| Símbolo | Se llama               | ¿Qué hace?                                                                    |                                                        |
| ------- | ---------------------- | ----------------------------------------------------------------------------- | ------------------------------------------------------ |
| `>`     | Redirección de salida  | Redirige la **salida estándar** a un archivo (y **sobrescribe** si ya existe) |                                                        |
| `>>`    | Redirección de salida  | Redirige la salida y **agrega al final** del archivo                          |                                                        |
| `<`     | Redirección de entrada | Toma **entrada desde un archivo**                                             |                                                        |
| `2>`    | Redirección de error   | Redirige **solo los errores** a un archivo                                    |                                                        |
| `&>`    | Salida y error juntos  | Redirige **salida + errores** a un archivo                                    |                                                        |
| \`      | \`                     | Pipe (tubería)                                                                | Envía la salida de un comando como **entrada de otro** |

---

### 📦 ¿Hay que instalar algo?

✅ **No.** Las redirecciones son parte de **la shell (bash)**. Si usas **Linux, macOS o WSL en Windows**, **ya están listas para usar**.

---

### 🧪 Ejemplos fáciles de entender

---

#### 🟩 1. Redirigir salida a un archivo (`>`)

```bash
echo "Hola Gustavo" > saludo.txt
```

🔹 Crea un archivo llamado `saludo.txt` con el contenido `Hola Gustavo`.

> ⚠️ Si `saludo.txt` ya existía, **se borra lo anterior**.

---

#### 🟩 2. Agregar contenido a un archivo (`>>`)

```bash
echo "¿Cómo estás?" >> saludo.txt
```

🔹 Agrega una línea al final sin borrar el contenido anterior.

📝 Ahora `saludo.txt` tiene:

```
Hola Gustavo
¿Cómo estás?
```

---

#### 🟨 3. Leer entrada desde un archivo (`<`)

```bash
cat < saludo.txt
```

🔹 Le dice al comando `cat` que **use `saludo.txt` como su entrada**.

> Aunque `cat saludo.txt` hace lo mismo, aquí usamos `<` para mostrar la idea.

---

#### 🟥 4. Guardar errores en un archivo (`2>`)

```bash
cat archivo_que_no_existe.txt 2> errores.txt
```

🔹 El error “No existe el archivo” se guarda en `errores.txt`, y **no aparece en pantalla**.

---

#### 🟦 5. Guardar salida + errores (`&>`)

```bash
ls carpeta_valida carpeta_falsa &> salida.txt
```

🔹 Guarda **todo** (resultado correcto y errores) en `salida.txt`.

---

#### 🟪 6. Usar un pipe (`|`)

```bash
ls | grep .txt
```

🔹 La salida de `ls` (lista de archivos) **se pasa** como entrada al comando `grep .txt`, que filtra y muestra solo los archivos `.txt`.

---

### ✅ Ejemplo completo paso a paso

#### 🎯 Objetivo:

Crear archivos, redirigir salidas y errores, y unir comandos.

---

#### 👣 Paso 1: Crear carpeta de prueba

```bash
mkdir practica_redireccion
cd practica_redireccion
```

---

#### 👣 Paso 2: Crear archivos

```bash
echo "Soy Gustavo" > hola.txt
echo "Aprendiendo Bash" >> hola.txt
```

---

#### 👣 Paso 3: Ver el contenido

```bash
cat hola.txt
```

🟢 Resultado:

```
Soy Gustavo
Aprendiendo Bash
```

---

#### 👣 Paso 4: Probar un error y redirigirlo

```bash
cat noexiste.txt 2> error.log
```

🔹 El error de “archivo no encontrado” se guarda en `error.log`.

---

#### 👣 Paso 5: Usar pipe para filtrar texto

```bash
cat hola.txt | grep Gustavo
```

🟢 Resultado:

```
Soy Gustavo
```

---

#### 👣 Paso 6: Combinar salida y error

```bash
ls hola.txt noexiste.txt &> resultado.log
```

📝 `resultado.log` tendrá tanto:

- ✅ `hola.txt`
- ❌ El error de `noexiste.txt`

---

### 🧠 Resumen visual

```
echo "Hola" > archivo.txt     # salida a archivo (sobrescribe)
echo "Mundo" >> archivo.txt   # salida a archivo (agrega)
cat < archivo.txt             # entrada desde archivo
comando 2> errores.txt        # solo errores
comando &> todo.txt           # errores + salida
comando1 | comando2           # salida -> entrada (pipe)
```

---

[🔼](#índice)

---

## **598. Redirecciones: pipe operator**

### 🧠 ¿Qué es el pipe operator (`|`)?

El **pipe (`|`)** es un **operador de redirección** en la terminal que **toma la salida de un comando y la envía como entrada a otro comando**.

> 📦 Piensa en el pipe como una **tubería**: lo que sale de un lado entra en el otro.

---

### 🎯 ¿Para qué sirve?

Sirve para **conectar varios comandos entre sí** sin necesidad de guardar resultados intermedios en archivos. Así puedes:

- Filtrar resultados
- Ordenarlos
- Contarlos
- Buscar dentro de ellos
- Encadenar comandos complejos en una sola línea

---

### 📦 ¿Necesito instalar algo?

✅ **No necesitas instalar nada.** El operador pipe `|` es parte de la **shell (como Bash)** y viene integrado en **Linux, macOS, WSL en Windows** y hasta en muchas consolas de sistemas Unix-like.

---

### 🔧 Sintaxis básica

```bash
comando1 | comando2
```

- `comando1` genera una **salida** (output)
- `comando2` **recibe esa salida** como su **entrada** (input)

---

### 🎓 Ejemplos fáciles de entender

---

#### 🟩 1. Listar archivos y filtrar con `grep`

```bash
ls | grep ".txt"
```

🟢 Muestra solo los archivos que **terminan en `.txt`** en el directorio actual.

---

#### 🟨 2. Ver contenido de un archivo y buscar palabra

```bash
cat archivo.txt | grep "clave"
```

🟢 Muestra solo las líneas del archivo que contienen la palabra **clave**.

---

#### 🟥 3. Contar líneas de una salida

```bash
ls | wc -l
```

🟢 Muestra **cuántos archivos** hay en el directorio (el resultado de `ls` se pasa a `wc -l`).

---

#### 🟦 4. Ordenar una lista

```bash
cat lista.txt | sort
```

🟢 Muestra las líneas de `lista.txt` en orden alfabético.

---

#### 🟪 5. Combinación múltiple

```bash
cat archivo.txt | grep "error" | sort | uniq
```

🟢 Busca la palabra "error", ordena las líneas encontradas, y elimina duplicados.

---

### 💡 ¿Qué comandos funcionan bien con pipe?

Comandos que **leen entrada estándar** y **generan salida estándar** como:

- `cat`: mostrar contenido
- `grep`: buscar texto
- `sort`: ordenar
- `uniq`: eliminar duplicados
- `wc`: contar líneas, palabras o caracteres
- `head`, `tail`: mostrar primeros o últimos registros
- `cut`, `awk`, `sed`: manipulación de texto

---

### ✅ Ejemplo completo paso a paso

#### 🎯 Objetivo:

Buscar errores en un archivo de registro (`log.txt`), contarlos y mostrar solo los únicos.

---

#### 👣 Paso 1: Crear una carpeta de trabajo

```bash
mkdir practica_pipe
cd practica_pipe
```

---

#### 👣 Paso 2: Crear un archivo de registro

```bash
cat << EOF > log.txt
[INFO] El sistema inició correctamente
[ERROR] No se pudo conectar a la base de datos
[INFO] Se recibió nueva solicitud
[ERROR] No se pudo conectar a la base de datos
[WARNING] Espacio en disco bajo
[ERROR] Usuario no autorizado
EOF
```

---

#### 👣 Paso 3: Usar pipe para buscar errores

```bash
cat log.txt | grep "ERROR"
```

🟢 Resultado:

```
[ERROR] No se pudo conectar a la base de datos
[ERROR] No se pudo conectar a la base de datos
[ERROR] Usuario no autorizado
```

---

#### 👣 Paso 4: Eliminar duplicados

```bash
cat log.txt | grep "ERROR" | uniq
```

🟢 Resultado:

```
[ERROR] No se pudo conectar a la base de datos
[ERROR] Usuario no autorizado
```

---

#### 👣 Paso 5: Contar cuántos errores hay

```bash
cat log.txt | grep "ERROR" | wc -l
```

🟢 Resultado:

```
3
```

---

#### 👣 Paso 6: Contar errores únicos

```bash
cat log.txt | grep "ERROR" | sort | uniq | wc -l
```

🟢 Resultado:

```
2
```

---

### 🧠 Resumen visual

| Tarea                          | Comando                                                               |     |
| ------------------------------ | --------------------------------------------------------------------- | --- |
| Buscar archivos `.txt`         | `ls                                                   \| grep ".txt"` |
| Contar líneas de un archivo    | `cat archivo.txt                                      \| wc -l`       |
| Ordenar contenido              | `cat archivo.txt                                      \| sort`        |
| Buscar y contar errores únicos | `cat log.txt \| grep "ERROR" \| sort \| uniq \| wc -l`                |     |

---

[🔼](#índice)

---

## **599. Encadenando comandos: operadores de control**

### 🧠 ¿Qué son los operadores de control?

Los **operadores de control** en la terminal permiten **encadenar comandos**, controlando **cuál se ejecuta primero, después y bajo qué condiciones**.

> 📦 Imagina que quieres que un comando se ejecute **solo si el anterior fue exitoso**, o que quieres lanzar **varios comandos uno tras otro**. Eso es lo que permiten estos operadores.

---

### 🧪 ¿Necesito instalar algo?

✅ **NO.** Estos operadores ya vienen integrados en cualquier shell de Unix/Linux (como **Bash**, usado en Linux, macOS, WSL de Windows, etc.).

---

### 🎯 ¿Para qué sirven?

Te permiten hacer cosas como:

- Ejecutar comandos uno tras otro sin tener que esperar manualmente.
- Ejecutar un comando **solo si otro tuvo éxito**.
- Ejecutar un comando **solo si otro falló**.
- Ejecutar múltiples comandos **en una sola línea**.

---

### 🔧 Tipos de operadores de control

| Operador      | Nombre           | ¿Qué hace?                                                             |     |     |
| ------------- | ---------------- | ---------------------------------------------------------------------- | --- | --- |
| `;`           | Secuencia        | Ejecuta **todos los comandos**, uno tras otro, sin importar errores    |     |     |
| `&&`          | Y lógico (AND)   | Ejecuta el **segundo comando solo si el primero fue exitoso (exit 0)** |     |     |
| `      \| \|` | O lógico (OR)    | Ejecuta el **segundo comando solo si el primero falla (exit ≠ 0)**     |
| `&`           | En segundo plano | Ejecuta el comando **en segundo plano** (paralelamente)                |     |     |

---

### 🧪 Ejemplos explicados

---

#### 🟩 1. Usando `;` — Ejecutar todos los comandos

```bash
echo "Hola"; echo "Mundo"
```

🟢 Resultado:

```
Hola
Mundo
```

✅ Ambos comandos se ejecutan **siempre**, sin importar si uno falla.

---

#### 🟨 2. Usando `&&` — Solo si el primero fue exitoso

```bash
mkdir nueva_carpeta && cd nueva_carpeta
```

🟢 Solo entra a la carpeta **si `mkdir` fue exitoso** (por ejemplo, si no existía antes).

---

#### 🟥 3. Usando `||` — Solo si el primero falla

```bash
cat archivo_inexistente.txt || echo "El archivo no existe"
```

🟢 Si `cat` **falla**, se ejecuta el `echo`.

---

#### 🟦 4. Usando `&` — Ejecutar en segundo plano

```bash
firefox &
```

🟢 Abre Firefox en segundo plano y te **devuelve el control de la terminal inmediatamente**.

> 🔥 Útil para abrir apps o procesos pesados sin bloquear la terminal.

---

#### 🟪 5. Combinación de operadores

```bash
cd /home/gustavo/proyecto && ls || echo "No se pudo acceder al directorio"
```

🟢 Si se accede correctamente, se hace `ls`.
❌ Si **falla**, imprime el mensaje de error.

---

### ✅ Ejemplo completo paso a paso

#### 🎯 Objetivo:

Crear una carpeta, entrar en ella, y crear un archivo **solo si todo sale bien**.

---

#### 👣 Paso 1: Crear una carpeta y entrar si se creó

```bash
mkdir logs && cd logs
```

📌 Si `mkdir logs` fue exitoso (la carpeta no existía), entra en ella.

---

#### 👣 Paso 2: Crear un archivo de log si entramos bien

```bash
mkdir logs && cd logs && touch registro.txt
```

📌 Si se creó la carpeta **y entramos** a ella, se crea el archivo `registro.txt`.

---

#### 👣 Paso 3: Mostrar error si no se pudo

```bash
mkdir logs && cd logs && touch registro.txt || echo "Hubo un error en el proceso"
```

🔴 Si **algo falla en toda la cadena**, aparece el mensaje.

---

#### 👣 Paso 4: Ejecutar comandos secuenciales sin importar errores

```bash
echo "Inicio del proceso"; ls archivos_inexistentes; echo "Fin del proceso"
```

📌 Se ejecutan **todos**, incluso si `ls` falla.

---

#### 👣 Paso 5: Ejecutar algo en segundo plano

```bash
gedit & echo "Editor abierto en segundo plano"
```

📌 Se abre `gedit` (editor de texto) y el mensaje aparece **sin esperar que cierres el programa**.

---

### 🧠 Resumen visual

```bash
comando1 ; comando2             # Ejecuta ambos comandos, sin importar si fallan
comando1 && comando2           # Ejecuta el segundo solo si el primero tiene éxito
comando1 || comando2           # Ejecuta el segundo solo si el primero falla
comando &                      # Ejecuta en segundo plano
```

---

[🔼](#índice)

---

## **600. Cómo se manejan los permisos**

### 🛡️ ¿Qué son los permisos en Linux?

En Linux, **cada archivo y carpeta tiene permisos de acceso** que determinan **quién puede leerlo, escribirlo o ejecutarlo**. Esto es clave para la seguridad y el orden del sistema.

---

### 🧍 Tipos de usuarios

Cada archivo tiene permisos definidos para tres **tipos de usuarios**:

| Usuario         | Significado                                |
| --------------- | ------------------------------------------ |
| **Propietario** | El usuario que creó el archivo             |
| **Grupo**       | Un grupo de usuarios con acceso compartido |
| **Otros**       | Todos los demás usuarios del sistema       |

---

### 🧷 Tipos de permisos

| Permiso     | Letra | Significado                                              |
| ----------- | ----- | -------------------------------------------------------- |
| **Read**    | `r`   | Leer (ver el contenido)                                  |
| **Write**   | `w`   | Escribir (modificar o eliminar)                          |
| **Execute** | `x`   | Ejecutar (para archivos ejecutables o entrar a carpetas) |

---

### 🔍 ¿Cómo veo los permisos?

Usa el comando `ls -l` para ver permisos:

```bash
ls -l
```

📌 Salida ejemplo:

```bash
-rwxr-xr-- 1 gustavo staff 1234 jul 23 12:00 script.sh
```

Interpretación del bloque de permisos `-rwxr-xr--`:

```
| Tipo | Propietario | Grupo | Otros |
|------|-------------|-------|-------|
|  -   | rwx         | r-x   | r--   |
```

- `-`: archivo normal (`d` sería directorio)
- `rwx`: el dueño **puede leer, escribir y ejecutar**
- `r-x`: el grupo **puede leer y ejecutar**
- `r--`: otros usuarios **solo pueden leer**

---

### 🔧 Cambiar permisos con `chmod`

#### 🛠️ Forma simbólica:

```bash
chmod [quién][operador][permiso] archivo
```

- Quién:

  - `u` = usuario (propietario)
  - `g` = grupo
  - `o` = otros
  - `a` = todos

- Operador:

  - `+` = agregar permiso
  - `-` = quitar permiso
  - `=` = asignar exactamente

#### ✅ Ejemplos simbólicos:

```bash
chmod u+x script.sh     # Agrega permiso de ejecución al dueño
chmod g-w archivo.txt   # Quita permiso de escritura al grupo
chmod o=r archivo.txt   # Otros solo pueden leer
```

---

#### 🔢 Forma numérica (octal)

```bash
chmod NNN archivo
```

- Donde cada `N` es una suma de permisos:

  - `r = 4`
  - `w = 2`
  - `x = 1`

| Permisos | Número |
| -------- | ------ |
| `rwx`    | 7      |
| `rw-`    | 6      |
| `r--`    | 4      |
| `---`    | 0      |

#### ✅ Ejemplos numéricos:

```bash
chmod 755 script.sh     # rwx r-x r-x
chmod 644 archivo.txt   # rw- r-- r--
chmod 700 archivo.sh    # rwx --- ---
```

---

### 👤 Cambiar el propietario o grupo

```bash
chown nuevo_usuario archivo.txt
chgrp nuevo_grupo archivo.txt
```

Puedes combinarlos:

```bash
chown nuevo_usuario:nuevo_grupo archivo.txt
```

---

### 📁 Permisos en directorios

- `r` (read): ver el contenido (con `ls`)
- `w` (write): crear o eliminar archivos dentro
- `x` (execute): entrar al directorio (`cd`)

---

### ✅ Ejemplo completo paso a paso

#### 🎯 Objetivo:

1. Crear un archivo
2. Revisar sus permisos
3. Cambiarlos
4. Probar qué puede hacer otro usuario

---

#### 👣 Paso 1: Crear carpeta y archivo

```bash
mkdir permisos_demo
cd permisos_demo
echo "contenido secreto" > secreto.txt
```

---

#### 👣 Paso 2: Ver los permisos

```bash
ls -l
```

📌 Verás algo como:

```
-rw-r--r-- 1 gustavo gustavo 20 jul 23 15:00 secreto.txt
```

---

#### 👣 Paso 3: Quitar permisos a otros

```bash
chmod o-r secreto.txt
```

🔍 Ahora solo el dueño y el grupo pueden leer el archivo.

---

#### 👣 Paso 4: Hacer que solo el dueño tenga acceso total

```bash
chmod 700 secreto.txt
```

📌 Permisos ahora: `-rwx------`

---

#### 👣 Paso 5: Comprobación con otro usuario (opcional si tienes uno)

Puedes usar `sudo su - otro_usuario` para intentar acceder y ver que no tiene permisos.

---

#### 👣 Paso 6: Restaurar permisos legibles

```bash
chmod 644 secreto.txt
```

📌 Ahora todos pueden leerlo, pero **solo el dueño puede modificarlo**.

---

### 🧠 Resumen visual

| Comando               | Qué hace                             |
| --------------------- | ------------------------------------ |
| `ls -l`               | Muestra permisos                     |
| `chmod 755 archivo`   | Cambia permisos con modo numérico    |
| `chmod u+x archivo`   | Agrega permiso de ejecución al dueño |
| `chown user archivo`  | Cambia el dueño del archivo          |
| `chgrp grupo archivo` | Cambia el grupo del archivo          |

---

[🔼](#índice)

---

## **601. Modificando permisos en la terminal**

### 🛠️ ¿Qué significa “modificar permisos” en la terminal?

En Linux, **cada archivo y carpeta tiene permisos** que determinan **quién puede leer, escribir o ejecutar** ese archivo o directorio.

Modificar permisos significa **cambiar esas reglas de acceso**, ya sea para ti, tu grupo o para otros usuarios.

---

### 🧩 ¿Para qué sirve esto?

- Proteger archivos importantes de ser borrados o editados por accidente.
- Dar permisos de lectura a alguien sin permitirle modificar el archivo.
- Hacer que un script sea ejecutable.
- Controlar el acceso a carpetas compartidas.

---

### ✅ ¿Hay que instalar algo?

No necesitas instalar nada. Todos los comandos que veremos (`chmod`, `chown`, `chgrp`) ya están disponibles por defecto en cualquier distribución de Linux, incluyendo WSL (Windows Subsystem for Linux), Ubuntu, Debian, etc.

Si usas **WSL en Windows** y aún no lo tienes:

#### 👉 Instalar WSL (por si no lo hiciste)

Abre PowerShell (como administrador) y ejecuta:

```powershell
wsl --install
```

Esto instala Ubuntu automáticamente. Reinicia tu PC, y ya podrás usar la terminal de Linux.

---

### 🔒 Tipos de permisos

Cada archivo o carpeta puede tener 3 tipos de permisos para 3 tipos de usuarios:

#### Tipos de usuarios:

- **u** (user): el propietario
- **g** (group): grupo al que pertenece
- **o** (others): los demás usuarios
- **a** (all): todos los anteriores

#### Tipos de permisos:

- `r`: lectura
- `w`: escritura
- `x`: ejecución

---

### 🔧 Comando para modificar permisos: `chmod`

#### 🔹 Sintaxis simbólica:

```bash
chmod [quién][operador][permiso] archivo
```

- Operadores:

  - `+`: agrega permiso
  - `-`: quita permiso
  - `=`: asigna solo esos permisos (elimina los anteriores)

#### 🔹 Sintaxis numérica:

```bash
chmod [modo numérico] archivo
```

Permisos en número:

| Permisos | Binario | Decimal |
| -------- | ------- | ------- |
| `r--`    | 100     | 4       |
| `-w-`    | 010     | 2       |
| `--x`    | 001     | 1       |

Combinaciones:

\| `rwx` = 7 | `rw-` = 6 | `r--` = 4 | `---` = 0 |

---

### 🧪 Ejemplos claros

#### 🔸 Ver permisos actuales

```bash
ls -l archivo.txt
```

Ejemplo:

```
-rw-r--r-- 1 gustavo gustavo  45 jul 23 20:00 archivo.txt
```

Eso significa:

- `rw-` (usuario): puede leer y escribir
- `r--` (grupo): solo puede leer
- `r--` (otros): solo pueden leer

---

#### 🔸 Agregar permiso de ejecución

```bash
chmod +x script.sh
```

Ahora puedes ejecutarlo con `./script.sh`.

---

#### 🔸 Quitar permisos de escritura para otros

```bash
chmod o-w archivo.txt
```

---

#### 🔸 Dar permisos totales al usuario, lectura y ejecución al grupo y nada al resto

```bash
chmod 750 archivo.txt
```

Equivale a:

- Usuario: `rwx` = 7
- Grupo: `r-x` = 5
- Otros: `---` = 0

---

#### 🔸 Asignar permisos exactos con `=`

```bash
chmod u=rw,g=r,o= archivo.txt
```

Eso deja:

- Usuario: `rw`
- Grupo: `r`
- Otros: sin permisos

---

#### 👤 Cambiar el propietario o grupo

A veces, quieres que **otro usuario o grupo tenga control**:

```bash
chown otro_usuario archivo.txt
chgrp otro_grupo archivo.txt
```

O ambos:

```bash
chown otro_usuario:otro_grupo archivo.txt
```

---

### ✅ Ejemplo completo paso a paso

#### 🎯 Objetivo:

Crear un archivo, cambiarle los permisos, y comprobar su acceso.

---

#### 🪜 Paso 1: Crear carpeta y archivo

```bash
mkdir permisos_demo
cd permisos_demo
echo "Hola Gustavo" > saludo.txt
```

---

#### 🪜 Paso 2: Ver permisos actuales

```bash
ls -l saludo.txt
```

Ejemplo de salida:

```
-rw-r--r-- 1 gustavo gustavo 14 jul 23 20:10 saludo.txt
```

---

#### 🪜 Paso 3: Quitar permisos de lectura a otros

```bash
chmod o-r saludo.txt
```

---

#### 🪜 Paso 4: Dar permiso de ejecución al propietario

```bash
chmod u+x saludo.txt
```

---

#### 🪜 Paso 5: Asignar permisos con número (solo lectura para todos)

```bash
chmod 444 saludo.txt
```

Ahora:

- Nadie puede escribir ni ejecutar el archivo.

---

#### 🪜 Paso 6: Restaurar permisos solo para el propietario

```bash
chmod 600 saludo.txt
```

Solo tú (el dueño) puedes leer y escribir.

---

### 🧠 Resumen rápido

| Comando                     | Acción                      |
| --------------------------- | --------------------------- |
| `chmod +x archivo`          | Agrega ejecución            |
| `chmod o-w archivo`         | Quita escritura a otros     |
| `chmod 755 archivo`         | rwx r-x r-x                 |
| `chmod u=rw,g=r,o= archivo` | Asigna permisos específicos |
| `chown usuario archivo`     | Cambia el propietario       |
| `chgrp grupo archivo`       | Cambia el grupo             |

---

[🔼](#índice)

---

## **602. Cómo configurar variables de entorno**

### 🧠 ¿Qué es una variable de entorno?

Una **variable de entorno** es como una **cajita que guarda información temporal** que el sistema o tus programas pueden usar.

🔹 Por ejemplo:

- El nombre de usuario (`$USER`)
- El directorio principal (`$HOME`)
- El camino para ejecutar comandos (`$PATH`)
- Claves API, tokens, configuraciones de apps, etc.

---

### 📦 ¿Qué se puede guardar en una variable de entorno?

Ejemplos típicos:

| Variable       | ¿Qué almacena?                          |
| -------------- | --------------------------------------- |
| `PATH`         | Rutas donde buscar comandos ejecutables |
| `USER`         | Nombre del usuario                      |
| `HOME`         | Carpeta personal del usuario            |
| `EDITOR`       | Editor de texto predeterminado          |
| `NODE_ENV`     | Modo de trabajo de Node.js (dev/prod)   |
| `DATABASE_URL` | Dirección de una base de datos          |

---

### ✅ ¿Necesito instalar algo?

**No necesitas instalar nada.**
Las variables de entorno vienen **incluidas por defecto** en cualquier sistema Linux, WSL o macOS.

Si estás en Windows puro (sin WSL), se puede hacer también, pero es diferente. Aquí nos enfocamos en Linux/WSL (bash).

---

### 🧪 Cómo ver variables de entorno

```bash
printenv
```

O para una sola variable:

```bash
echo $HOME
echo $USER
```

---

### 🔧 Cómo crear una variable de entorno (temporal)

```bash
NOMBRE=Gustavo
```

O usarla:

```bash
echo $NOMBRE
# Resultado: Gustavo
```

✅ Pero esta variable **desaparece cuando cierras la terminal.**

---

### 🧱 Cómo hacerla **permanente**

Debes agregarla a uno de los archivos de configuración del **shell (Bash)**:

- `~/.bashrc` – se ejecuta al abrir una terminal interactiva
- `~/.profile` o `~/.bash_profile` – se ejecuta al iniciar sesión (login shell)

👉 El más común es `~/.bashrc`.

---

#### 🪜 Paso para hacerla permanente

1. Abre el archivo `.bashrc` con un editor:

```bash
nano ~/.bashrc
```

2. Agrega al final algo como esto:

```bash
export NOMBRE=Gustavo
export PROYECTO_ACTUAL=api-ecommerce
```

3. Guarda con `CTRL+O`, luego `Enter`, y sal con `CTRL+X`.

4. Aplica los cambios sin cerrar la terminal:

```bash
source ~/.bashrc
```

---

### 🎯 ¿Qué significa `export`?

👉 `export` hace que la variable esté **disponible para procesos hijos**, como cuando ejecutas un programa desde la terminal.

Sin `export`, la variable solo vive dentro del shell actual.

---

### 🧪 Usos reales con variables

#### 🔹 Uso para programadores

```bash
export NODE_ENV=production
export DATABASE_URL="mongodb+srv://gustavo:clave@cluster.mongodb.net"
```

---

#### 🔹 Agregar al PATH para usar programas propios

```bash
export PATH=$PATH:/home/gustavo/scripts
```

👉 Así puedes ejecutar cualquier script dentro de esa carpeta desde cualquier lugar.

---

### ✅ Ejemplo completo paso a paso

#### 🎯 Objetivo:

Crear una variable `MI_NOMBRE`, hacerla permanente, y usarla para un script o impresión.

---

#### 👣 Paso 1: Crear una variable temporal

```bash
MI_NOMBRE="Gustavo"
echo $MI_NOMBRE
```

---

#### 👣 Paso 2: Hacerla permanente

```bash
nano ~/.bashrc
```

Agregar al final:

```bash
export MI_NOMBRE="Gustavo"
```

Guardar con `CTRL+O`, salir con `CTRL+X`.

---

#### 👣 Paso 3: Aplicar los cambios

```bash
source ~/.bashrc
```

---

#### 👣 Paso 4: Verificar que existe

```bash
echo $MI_NOMBRE
# Resultado: Gustavo
```

---

#### 👣 Paso 5: Usarla en un script

```bash
nano saludo.sh
```

Contenido del archivo:

```bash
#!/bin/bash
echo "Hola, $MI_NOMBRE. ¡Bienvenido!"
```

Guardar y darle permiso:

```bash
chmod +x saludo.sh
./saludo.sh
```

Resultado:

```
Hola, Gustavo. ¡Bienvenido!
```

---

### 🧠 Resumen

| Acción                  | Comando                              |
| ----------------------- | ------------------------------------ |
| Ver variables           | `printenv` o `echo $NOMBRE`          |
| Crear variable temporal | `MI_VAR=valor`                       |
| Hacerla permanente      | `export MI_VAR=valor` en `~/.bashrc` |
| Aplicar cambios         | `source ~/.bashrc`                   |
| Agregar carpeta al PATH | `export PATH=$PATH:/ruta/adicional`  |

---

[🔼](#índice)

---

## **603. Comandos de búsqueda**

### 🧠 ¿Qué son los comandos de búsqueda?

En Linux, los **comandos de búsqueda** te permiten encontrar:

- Archivos por nombre, tipo, tamaño, fecha, etc.
- Texto dentro de archivos
- Rutas específicas en el sistema

Son fundamentales cuando trabajas con muchos archivos o necesitas ubicar información rápidamente desde la terminal.

---

### 🔍 Principales comandos de búsqueda

| Comando  | ¿Para qué sirve?                                    |
| -------- | --------------------------------------------------- |
| `find`   | Buscar archivos y carpetas por muchos criterios     |
| `grep`   | Buscar texto dentro de archivos                     |
| `locate` | Buscar archivos por nombre usando una base de datos |
| `which`  | Ubicar el ejecutable de un comando                  |

---

### 🔧 ¿Necesitan instalación?

En WSL o distribuciones como Ubuntu:

- `find`, `grep` y `which` **vienen preinstalados** ✅
- `locate` puede requerir instalación:

```bash
sudo apt update
sudo apt install mlocate
sudo updatedb  # construye la base de datos de archivos
```

---

### 📘 Comando `find`

#### 🧾 Sintaxis básica:

```bash
find [ruta] [condición] [acción]
```

#### 📌 Ejemplos:

##### Buscar archivos por nombre

```bash
find . -name "archivo.txt"
```

Busca "archivo.txt" en la carpeta actual y subcarpetas.

##### Buscar por extensión

```bash
find /home/gustavo -name "*.sh"
```

Busca todos los archivos `.sh` en tu carpeta personal.

##### Buscar por tipo de archivo

```bash
find . -type d -name "config"
```

Busca directorios (`-type d`) con nombre "config".

##### Buscar archivos más grandes de 5 MB

```bash
find . -size +5M
```

---

### 📘 Comando `grep`

#### 🧾 Sintaxis básica:

```bash
grep [opciones] "texto" archivo
```

#### 📌 Ejemplos:

##### Buscar palabra en un archivo

```bash
grep "error" log.txt
```

Muestra todas las líneas del archivo `log.txt` que contengan la palabra **error**.

##### Buscar de forma recursiva en una carpeta

```bash
grep -r "token" .
```

Busca "token" en todos los archivos y subcarpetas del directorio actual.

##### Ignorar mayúsculas/minúsculas

```bash
grep -i "usuario" base_datos.txt
```

---

### 📘 Comando `locate`

#### 🧾 Sintaxis básica:

```bash
locate nombre_del_archivo
```

#### 📌 Ejemplo:

```bash
locate bashrc
```

Te muestra rápidamente **todas las ubicaciones** del archivo `.bashrc`.

🛠️ Nota: si acabas de crear un archivo, necesitas actualizar la base de datos:

```bash
sudo updatedb
```

---

### 📘 Comando `which`

Muestra la **ruta exacta del ejecutable** de un comando:

```bash
which node
which python3
```

---

### ✅ Ejemplo completo paso a paso

#### 🎯 Objetivo: Buscar un archivo `.sh` y una línea de texto dentro de él.

---

#### 👣 Paso 1: Crear estructura de prueba

```bash
mkdir proyecto
cd proyecto
echo 'echo "Hola mundo"' > hola.sh
echo 'echo "Token secreto: 12345"' > config.sh
```

---

#### 👣 Paso 2: Buscar archivo `.sh` con `find`

```bash
find . -name "*.sh"
```

Resultado:

```
./hola.sh
./config.sh
```

---

#### 👣 Paso 3: Buscar la palabra "Token" con `grep`

```bash
grep "Token" config.sh
```

Resultado:

```
echo "Token secreto: 12345"
```

---

#### 👣 Paso 4: Buscar la palabra en todos los archivos con `grep -r`

```bash
grep -r "Token" .
```

---

#### 👣 Paso 5: Buscar archivo por nombre con `locate` (si instalado)

```bash
locate config.sh
```

Si no aparece, ejecuta:

```bash
sudo updatedb
```

y luego repite el comando.

---

### 🧠 Resumen rápido

| Comando                      | Qué hace                                                 |
| ---------------------------- | -------------------------------------------------------- |
| `find . -name "*.txt"`       | Busca archivos `.txt` en la carpeta actual               |
| `grep "palabra" archivo.txt` | Busca texto dentro de un archivo                         |
| `grep -r "texto" .`          | Busca texto dentro de todos los archivos recursivamente  |
| `locate nombre_archivo`      | Encuentra archivos por nombre rápido (requiere updatedb) |
| `which comando`              | Muestra la ruta del comando ejecutable                   |

---

### 🧪 ¿Qué más podrías hacer?

- Usar `find` junto con `grep`:

  ```bash
  find . -name "*.log" -exec grep "error" {} \;
  ```

- Buscar archivos modificados en las últimas 24 horas:

  ```bash
  find . -type f -mtime -1
  ```

---

[🔼](#índice)

---

## **604. Usando el comando grep**

### 🧠 ¿Qué es `grep`?

`grep` es uno de los comandos más poderosos y usados en Linux.
Sirve para **buscar texto dentro de archivos**. Es como un “buscar” (Ctrl+F) pero desde la terminal.

🔍 Su nombre viene de:

> **g/re/p** = global / regular expression / print

---

### 📦 ¿Cómo se instala `grep`?

#### ✅ Ya viene instalado en:

- Ubuntu
- Debian
- WSL
- Kali Linux
- Casi cualquier sistema Linux

Pero si por alguna razón no lo tienes:

```bash
sudo apt update
sudo apt install grep
```

Para verificar si ya está instalado:

```bash
grep --version
```

---

### 📘 Sintaxis básica

```bash
grep [opciones] "texto_a_buscar" archivo
```

Ejemplo básico:

```bash
grep "hola" saludo.txt
```

Buscará todas las líneas que contengan la palabra "hola" en el archivo `saludo.txt`.

---

### 🧪 Ejemplos fáciles

#### 📂 1. Buscar una palabra específica

```bash
grep "error" registro.log
```

Resultado:

```
[2025-07-23 10:33] error: conexión fallida
```

---

#### 🔁 2. Buscar en varios archivos

```bash
grep "usuario" *.txt
```

Buscará la palabra "usuario" en **todos los archivos `.txt`** del directorio.

---

#### 🔎 3. Buscar sin importar mayúsculas o minúsculas

```bash
grep -i "gustavo" usuarios.txt
```

Buscará "gustavo", "Gustavo", "GUSTAVO", etc.

---

#### 📄 4. Ver solo los nombres de archivos que contienen el texto

```bash
grep -l "token" *.txt
```

`-l` = muestra **solo el nombre de los archivos** donde aparece el texto.

---

#### 🌳 5. Buscar dentro de carpetas y subcarpetas

```bash
grep -r "clave" .
```

`-r` = recursivo, busca en todos los archivos dentro del directorio actual y subdirectorios.

---

#### 🔢 6. Mostrar números de línea donde aparece el texto

```bash
grep -n "admin" usuarios.txt
```

`-n` = muestra el **número de línea** junto al contenido.

---

#### ❌ 7. Mostrar las líneas que **NO** contienen el texto

```bash
grep -v "error" registro.log
```

`-v` = muestra solo las líneas que **no** tienen el texto.

---

#### 🎯 8. Buscar una palabra exacta (no partes de palabras)

```bash
grep -w "root" usuarios.txt
```

Sin `-w`, también encontraría "rootuser", "superroot", etc.

---

#### 🧬 9. Buscar usando expresiones regulares

```bash
grep -E "usuario[0-9]+" usuarios.txt
```

Buscará palabras como `usuario1`, `usuario202`, etc.

---

### ✅ Ejemplo completo paso a paso

#### 🎯 Objetivo: Buscar errores en un archivo de logs

---

#### 👣 Paso 1: Crear archivo de prueba

```bash
echo -e "Info: todo ok\nError: conexión fallida\nWarning: posible error\nError: acceso denegado" > logs.txt
```

---

#### 👣 Paso 2: Buscar la palabra "Error"

```bash
grep "Error" logs.txt
```

Resultado:

```
Error: conexión fallida
Error: acceso denegado
```

---

#### 👣 Paso 3: Buscar sin importar mayúsculas

```bash
grep -i "error" logs.txt
```

Resultado:

```
Error: conexión fallida
Warning: posible error
Error: acceso denegado
```

---

#### 👣 Paso 4: Mostrar con número de línea

```bash
grep -in "error" logs.txt
```

Resultado:

```
2:Error: conexión fallida
3:Warning: posible error
4:Error: acceso denegado
```

---

#### 👣 Paso 5: Mostrar solo las líneas que **NO** contienen "error"

```bash
grep -iv "error" logs.txt
```

Resultado:

```
Info: todo ok
```

---

### 🧠 Resumen de opciones útiles

| Opción | ¿Qué hace?                                   |
| ------ | -------------------------------------------- |
| `-i`   | Ignora mayúsculas/minúsculas                 |
| `-r`   | Búsqueda recursiva en carpetas               |
| `-n`   | Muestra el número de línea                   |
| `-l`   | Muestra solo los nombres de archivos         |
| `-v`   | Muestra líneas que **no** contienen el texto |
| `-w`   | Coincidencia exacta de palabras              |
| `-E`   | Permite expresiones regulares extendidas     |

---

### 🧪 ¿Qué más puedo hacer con `grep`?

- Combinarlo con `find`:

```bash
find . -name "*.txt" -exec grep "Gustavo" {} \;
```

- Usarlo con pipes (`|`):

```bash
cat usuarios.txt | grep "admin"
```

---

[🔼](#índice)

---

## **605. Utilidades de red**

### 🧠 ¿Qué son las utilidades de red?

Las **utilidades de red** son herramientas que vienen en Linux (y también puedes usarlas en WSL) para:

- Saber si hay conexión a internet
- Ver si un sitio web o servidor responde
- Obtener direcciones IP
- Ver el estado de la red
- Diagnosticar problemas de red

Estas utilidades son **indispensables en ciberseguridad, administración de sistemas, servidores y desarrollo web**.

---

### 🛠️ Instalación (en caso no las tengas)

La mayoría ya viene instalada en distribuciones como Ubuntu o Kali, pero si no:

```bash
sudo apt update
sudo apt install net-tools iputils-ping dnsutils
```

Algunos comandos adicionales útiles están en paquetes como:

```bash
sudo apt install nmap traceroute curl wget
```

---

### 📚 Las utilidades más comunes

| Comando           | ¿Para qué sirve?                                             |
| ----------------- | ------------------------------------------------------------ |
| `ping`            | Verifica si un host está activo/respondiendo                 |
| `ifconfig` / `ip` | Muestra la configuración de red local                        |
| `traceroute`      | Muestra el camino que siguen los paquetes hasta un host      |
| `nslookup`        | Consulta servidores DNS para resolver nombres de dominio     |
| `dig`             | Información detallada sobre consultas DNS                    |
| `netstat`         | Muestra conexiones de red y puertos abiertos                 |
| `nmap`            | Escanea puertos y detecta servicios activos en hosts remotos |
| `curl`            | Solicita recursos web (ver HTML, JSON, etc.)                 |
| `wget`            | Descarga archivos desde internet por HTTP/FTP                |
| `hostname`        | Muestra o cambia el nombre del equipo                        |

---

### ✅ Explicaciones y ejemplos simples

---

#### 🔁 1. `ping`

Envía paquetes ICMP para saber si un host responde.

```bash
ping google.com
```

Resultado:

```
64 bytes from 142.250.78.238: icmp_seq=1 ttl=115 time=21.8 ms
```

Detén con `Ctrl + C`.

Puedes usarlo para saber si tienes internet o si una IP está activa.

---

#### 🖧 2. `ifconfig` o `ip`

##### Ver interfaces de red:

```bash
ifconfig
```

O con el nuevo comando:

```bash
ip addr
```

Te muestra tu dirección IP local, interfaces como `eth0`, `lo`, etc.

---

#### 🌐 3. `traceroute`

Muestra el recorrido de tu conexión hasta un servidor.

```bash
traceroute google.com
```

Te dice por qué nodos (routers) pasan tus paquetes.

Si no está instalado:

```bash
sudo apt install traceroute
```

---

#### 📛 4. `nslookup`

Consulta DNS: traduce dominio a IP.

```bash
nslookup google.com
```

Resultado:

```
Name: google.com
Address: 142.250.190.206
```

---

#### 🔎 5. `dig`

Consulta avanzada de DNS:

```bash
dig openai.com
```

Resultado más detallado que `nslookup`, útil para investigar problemas de DNS.

---

#### 📊 6. `netstat`

Ver conexiones y puertos abiertos:

```bash
netstat -tuln
```

- `-t`: TCP
- `-u`: UDP
- `-l`: Listening (escuchando)
- `-n`: direcciones numéricas

> Nota: Si no tienes `netstat`, instala `net-tools`.

---

#### 🚨 7. `nmap`

Escanea un host o red para detectar puertos abiertos.

```bash
nmap 192.168.1.1
```

Muestra qué puertos están abiertos y qué servicios están activos.

Instala con:

```bash
sudo apt install nmap
```

---

#### 🌐 8. `curl`

Consulta una URL y ve la respuesta HTML o JSON:

```bash
curl https://jsonplaceholder.typicode.com/posts/1
```

---

#### 💾 9. `wget`

Descarga archivos desde internet:

```bash
wget https://www.example.com/archivo.zip
```

---

#### 🏷️ 10. `hostname`

Muestra o cambia el nombre de tu equipo:

```bash
hostname
sudo hostname nuevo-nombre
```

---

### ✅ Ejemplo completo paso a paso

#### 🎯 Objetivo: Diagnosticar la conexión a un sitio web

---

#### 👣 Paso 1: Verificar si hay conexión

```bash
ping google.com
```

Si responde, tienes internet.

---

#### 👣 Paso 2: Ver tu IP local

```bash
ip addr
```

Busca una línea como:

```
inet 192.168.1.100/24
```

---

#### 👣 Paso 3: Resolver el dominio (DNS)

```bash
nslookup github.com
```

Te da su dirección IP.

---

#### 👣 Paso 4: Hacer un `traceroute` hasta el sitio

```bash
traceroute github.com
```

Verás los routers por los que pasa tu conexión.

---

#### 👣 Paso 5: Ver si el sitio responde en la web

```bash
curl https://github.com
```

Si ves HTML, es que responde.

---

#### 👣 Paso 6: Ver puertos abiertos con `nmap`

```bash
nmap github.com
```

Te dirá si tiene abierto el puerto 80 (HTTP) o 443 (HTTPS).

---

### 🧠 Resumen general

| Utilidad          | ¿Qué hace?                              | Instalación si no está |
| ----------------- | --------------------------------------- | ---------------------- |
| `ping`            | Ver si un host responde                 | Ya instalado           |
| `ip` / `ifconfig` | Ver IPs e interfaces de red             | `net-tools`            |
| `traceroute`      | Ver el camino de conexión               | `traceroute`           |
| `nslookup`        | Resolver nombres de dominio a IP        | `dnsutils`             |
| `dig`             | Consulta DNS avanzada                   | `dnsutils`             |
| `netstat`         | Ver puertos abiertos                    | `net-tools`            |
| `nmap`            | Escaneo de red                          | `nmap`                 |
| `curl`            | Consultar páginas web desde la terminal | `curl`                 |
| `wget`            | Descargar archivos                      | `wget`                 |

---

[🔼](#índice)

---

## **606. Comprimiendo archivos tar y zip**

### 🧠 ¿Qué significa comprimir archivos?

Comprimir archivos significa:

- Agrupar uno o más archivos/directorios en **uno solo**.
- Reducir el tamaño total (en algunos casos).
- Facilitar el transporte o copia.

**Ejemplo de la vida real**: como cuando metes muchas cosas en una maleta (archivo `.tar` o `.zip`) para llevarlas juntas y ocupando menos espacio.

---

### 🧰 Herramientas comunes en Linux

| Herramienta | ¿Qué hace?                                    | Extensión usual   |
| ----------- | --------------------------------------------- | ----------------- |
| `tar`       | Agrupa varios archivos (puede o no comprimir) | `.tar`, `.tar.gz` |
| `zip`       | Comprime y agrupa archivos                    | `.zip`            |
| `gzip`      | Comprime archivos (no agrupa)                 | `.gz`             |
| `unzip`     | Descomprime archivos `.zip`                   | `.zip`            |

---

### 🛠️ Instalación (si no están)

En la mayoría de sistemas Linux y WSL ya vienen preinstalados. Si no:

```bash
sudo apt update
sudo apt install zip unzip tar gzip
```

---

### 🐚 COMANDOS BÁSICOS

---

### 📦 Comprimir con `tar`

#### 1. Comprimir una carpeta o archivo

```bash
tar -cvf archivo.tar carpeta/
```

**Significado**:

- `c`: crear archivo
- `v`: mostrar lo que hace (verbose)
- `f`: nombre del archivo resultante
- `archivo.tar`: el nombre del archivo tar que crearás
- `carpeta/`: la carpeta o archivos a comprimir

**Ejemplo**:

```bash
tar -cvf respaldo.tar documentos/
```

---

#### 2. Comprimir y **comprimir con gzip**

```bash
tar -czvf archivo.tar.gz carpeta/
```

**Significado adicional**:

- `z`: usar `gzip` para comprimir

**Ejemplo**:

```bash
tar -czvf respaldo.tar.gz documentos/
```

---

#### 3. Descomprimir un archivo `.tar.gz`

```bash
tar -xzvf archivo.tar.gz
```

**Ejemplo**:

```bash
tar -xzvf respaldo.tar.gz
```

---

### 📦 Comprimir con `zip`

#### 1. Comprimir archivos

```bash
zip archivo.zip archivo1.txt archivo2.txt
```

**Ejemplo**:

```bash
zip mis_datos.zip datos1.txt datos2.txt
```

---

#### 2. Comprimir una carpeta (recursivamente)

```bash
zip -r archivo.zip carpeta/
```

**Ejemplo**:

```bash
zip -r backup.zip proyecto/
```

---

#### 3. Descomprimir `.zip`

```bash
unzip archivo.zip
```

**Ejemplo**:

```bash
unzip backup.zip
```

---

### ✅ EJEMPLO COMPLETO

#### 🎯 Objetivo: Comprimir una carpeta de proyecto y luego descomprimirla

---

#### 📁 Supón que tienes esta estructura:

```
/home/gustavo/mi_proyecto/
├── index.html
├── style.css
└── script.js
```

---

#### 1. Comprimir usando `tar.gz`

```bash
cd /home/gustavo
tar -czvf mi_proyecto.tar.gz mi_proyecto/
```

Resultado: se crea `mi_proyecto.tar.gz`.

---

#### 2. Descomprimir

```bash
tar -xzvf mi_proyecto.tar.gz
```

Esto recreará la carpeta `mi_proyecto/` con sus archivos.

---

#### 3. Comprimir con `zip`

```bash
zip -r mi_proyecto.zip mi_proyecto/
```

Resultado: `mi_proyecto.zip`.

---

#### 4. Descomprimir con `unzip`

```bash
unzip mi_proyecto.zip
```

---

### 🧠 ¿Cuál usar?

| Necesidad                           | Usa                                 |
| ----------------------------------- | ----------------------------------- |
| Compatibilidad con Windows          | `.zip`                              |
| Trabajo en servidores Linux         | `.tar.gz`                           |
| Máxima compresión                   | `.tar.gz` o `.7z` (si usas `p7zip`) |
| Quieres solo agrupar, sin comprimir | `.tar`                              |

---

[🔼](#índice)

---

## **607. Manejo de procesos**

### 🧠 ¿Qué es un proceso en Linux?

Un **proceso** es una instancia de un programa que se está ejecutando.
Por ejemplo, cuando abres Firefox o ejecutas un script en la terminal, se crea un proceso.

Cada proceso tiene un **PID (Process ID)** único, y el sistema lo administra para saber qué está haciendo y cuánta memoria, CPU y recursos usa.

---

### 🧰 ¿Qué herramientas se usan para manejar procesos?

| Comando           | ¿Qué hace?                        |
| ----------------- | --------------------------------- |
| `ps`              | Lista procesos actuales           |
| `top` / `htop`    | Muestra procesos en tiempo real   |
| `kill`            | Finaliza un proceso               |
| `killall`         | Finaliza procesos por nombre      |
| `nice` / `renice` | Cambia prioridad de procesos      |
| `&`               | Ejecuta en segundo plano          |
| `jobs`            | Lista procesos en segundo plano   |
| `fg` / `bg`       | Trae procesos al frente o fondo   |
| `xkill`           | Mata una ventana gráfica con clic |

---

### 📦 Instalación (opcional)

La mayoría de estas herramientas ya están instaladas por defecto. Pero puedes instalar herramientas adicionales como `htop`:

```bash
sudo apt update
sudo apt install htop
```

---

### 📘 Ejemplos fáciles por comando

---

#### 1. `ps`: ver los procesos

```bash
ps
```

Muestra solo tus procesos activos en esta sesión.

```bash
ps aux
```

- `a`: todos los usuarios
- `u`: formato detallado
- `x`: incluye procesos sin terminal asociada

🔎 Ejemplo:

```bash
ps aux | grep firefox
```

---

#### 2. `top`: ver procesos en tiempo real

```bash
top
```

Presiona `q` para salir.

Más bonito con `htop`:

```bash
htop
```

(usa flechas para navegar, `F9` para matar procesos, etc.)

---

#### 3. Ejecutar procesos en segundo plano

```bash
firefox &
```

El símbolo `&` lo envía al **segundo plano** y te devuelve la terminal.

---

#### 4. Ver procesos en segundo plano

```bash
jobs
```

Muestra algo como:

```
[1]+  Running  firefox &
```

---

#### 5. Traer al frente o mandar al fondo

```bash
fg %1   # Trae el trabajo número 1 al frente
bg %1   # Lo envía al fondo
```

---

#### 6. `kill`: matar un proceso por PID

Primero, busca su PID:

```bash
ps aux | grep firefox
```

Luego:

```bash
kill 12345
```

Si no muere, puedes forzar:

```bash
kill -9 12345
```

---

#### 7. `killall`: matar por nombre

```bash
killall firefox
```

Mata todos los procesos llamados "firefox".

---

#### 8. `nice` y `renice`: prioridad

Valores de nice van de -20 (más prioridad) a 19 (menos prioridad).

```bash
nice -n 10 mi_script.sh
```

Cambiar prioridad de un proceso que ya existe:

```bash
renice -n 5 -p 12345
```

---

#### 9. `xkill`: matar ventana con el mouse (solo entornos gráficos)

```bash
xkill
```

Haz clic en la ventana que quieras cerrar.
Si no lo tienes:

```bash
sudo apt install x11-utils
```

---

### ✅ EJEMPLO COMPLETO PASO A PASO

#### 🎯 Objetivo: Ejecutar un proceso, verlo en la lista, mandarlo al fondo y luego matarlo.

---

#### 👣 Paso 1: Ejecuta un script o comando en segundo plano

```bash
sleep 100 &
```

Esto simula un proceso que estará 100 segundos en ejecución.

---

#### 👣 Paso 2: Verifica los procesos

```bash
jobs
```

Muestra algo como:

```
[1]+  Running  sleep 100 &
```

---

#### 👣 Paso 3: Verifica con `ps` o `top`

```bash
ps aux | grep sleep
```

---

#### 👣 Paso 4: Matar el proceso

Primero, obtén el PID:

```bash
ps aux | grep sleep
```

Digamos que el PID es `2345`, entonces:

```bash
kill 2345
```

O, si no responde:

```bash
kill -9 2345
```

---

#### 👣 Paso 5: Confirmar que murió

```bash
ps aux | grep sleep
```

Si ya no aparece, fue eliminado correctamente.

---

### 🧠 Resumen de comandos clave

| Comando           | Acción                        |
| ----------------- | ----------------------------- |
| `ps aux`          | Ver todos los procesos        |
| `top` / `htop`    | Monitor en tiempo real        |
| `kill PID`        | Matar proceso por ID          |
| `killall nombre`  | Matar proceso por nombre      |
| `&`               | Ejecutar en segundo plano     |
| `jobs`            | Ver procesos en segundo plano |
| `fg` / `bg`       | Controlar esos procesos       |
| `nice` / `renice` | Modificar prioridad           |

---

[🔼](#índice)

---

## **608. Procesos en foreground y background**

### 🧠 ¿Qué son los procesos en foreground y background?

#### 🔸 Foreground (primer plano)

Es cuando ejecutas un comando y **la terminal se bloquea** esperando a que termine.
No puedes hacer nada más en la terminal hasta que ese proceso acabe o lo detengas.

🔍 **Ejemplo típico**:

```bash
ping google.com
```

Esto sigue enviando paquetes a Google indefinidamente. No puedes escribir otro comando hasta que presiones `Ctrl + C` para detenerlo.

---

#### 🔸 Background (segundo plano)

Es cuando ejecutas un proceso y **la terminal queda libre para otros comandos**, porque el proceso corre "al fondo".

Para esto se usa el símbolo `&` al final:

```bash
ping google.com &
```

Ahora puedes seguir usando la terminal mientras ese proceso sigue ejecutándose.

---

### 📦 Instalación de herramientas (opcional)

No necesitas instalar nada para usar estos conceptos, porque los comandos base (`jobs`, `fg`, `bg`, etc.) ya vienen en cualquier shell como `bash`, `zsh`, etc.

Sin embargo, puedes instalar `htop` si quieres una visualización más gráfica de los procesos en ejecución:

```bash
sudo apt update
sudo apt install htop
```

---

### 🧰 Comandos clave para controlar procesos

| Comando    | Función                                                   |
| ---------- | --------------------------------------------------------- |
| `&`        | Ejecuta un proceso en segundo plano                       |
| `jobs`     | Lista los procesos en segundo plano                       |
| `fg %n`    | Trae un proceso al primer plano                           |
| `bg %n`    | Envía un proceso detenido al fondo                        |
| `Ctrl + Z` | Pausa un proceso (lo suspende)                            |
| `kill %n`  | Mata un proceso en segundo plano por su número de trabajo |
| `kill PID` | Mata un proceso por su ID                                 |

---

### 👣 Ejemplos paso a paso

---

#### ✅ 1. Ejecutar un proceso en primer plano

```bash
sleep 30
```

Esto espera 30 segundos y **bloquea la terminal** mientras corre.

---

#### ✅ 2. Ejecutar en segundo plano

```bash
sleep 30 &
```

Te devolverá algo como:

```
[1] 12345
```

Eso significa:

- `[1]`: número del trabajo
- `12345`: ID del proceso (PID)

Ahora puedes seguir usando la terminal mientras ese proceso "duerme".

---

#### ✅ 3. Ver procesos en segundo plano

```bash
jobs
```

Resultado:

```
[1]+  Running  sleep 30 &
```

---

#### ✅ 4. Detener un proceso en ejecución con `Ctrl + Z`

Ejecuta algo largo:

```bash
ping google.com
```

Luego presiona:

```text
Ctrl + Z
```

Resultado:

```
[1]+  Stopped  ping google.com
```

El proceso fue **pausado**.

---

#### ✅ 5. Reanudarlo en segundo plano

```bash
bg %1
```

O si fuera el trabajo `[2]`:

```bash
bg %2
```

---

#### ✅ 6. Reanudarlo en primer plano

```bash
fg %1
```

---

#### ✅ 7. Matar un proceso en segundo plano

```bash
kill %1
```

O si conoces su PID:

```bash
kill 12345
```

Para forzarlo:

```bash
kill -9 12345
```

---

### 🎯 EJEMPLO COMPLETO

Vamos a simular un proceso de "largo tiempo" con `sleep`.

#### 👣 Paso 1: Ejecutar en segundo plano

```bash
sleep 100 &
```

Salida:

```
[1] 34567
```

---

#### 👣 Paso 2: Ver los procesos activos en segundo plano

```bash
jobs
```

---

#### 👣 Paso 3: Detener el proceso

```bash
kill %1
```

Verifica con:

```bash
jobs
```

o

```bash
ps aux | grep sleep
```

---

#### 👣 Paso 4: Ejecutar un proceso, pausarlo y reanudarlo

```bash
ping google.com
```

Ahora presiona `Ctrl + Z` para pausarlo.

Luego:

```bash
bg
```

Para enviarlo al segundo plano.

O:

```bash
fg
```

Para volver al frente.

---

### 🧠 Consejos útiles

- Siempre que veas el símbolo `&`, es un proceso en segundo plano.
- Si presionas `Ctrl + Z`, no mata el proceso, solo lo **suspende**.
- Usa `jobs`, `fg` y `bg` para moverte entre procesos sin cerrarlos.

---

### ¿Para qué sirve esto?

- Ejecutar múltiples tareas sin abrir nuevas terminales.
- Dejar procesos largos corriendo mientras haces otras cosas.
- Controlar scripts, descargas, servidores o programas desde una sola terminal.

---

[🔼](#índice)

---

## **609. Editores de texto en la terminal**

### 🧠 ¿Qué es un editor de texto en la terminal?

Un **editor de texto** es una herramienta que permite **crear y modificar archivos de texto plano**. En la terminal de Linux, esto es clave para editar:

- Archivos de configuración del sistema (`.bashrc`, `nginx.conf`, etc.)
- Scripts (`.sh`, `.py`, `.js`)
- Notas o documentación

Todo esto **sin abrir ventanas gráficas**, ideal para servidores o desarrollo remoto.

---

### 🧰 Editores de texto comunes en la terminal

| Editor  | Fácil de usar   | ¿Viene instalado? | Comando para abrir  |
| ------- | --------------- | ----------------- | ------------------- |
| `nano`  | ✅ Muy fácil    | 🔁 A veces sí     | `nano archivo.txt`  |
| `vim`   | ❌ Más complejo | ✅ Casi siempre   | `vim archivo.txt`   |
| `vi`    | ❌ Básico       | ✅ Siempre        | `vi archivo.txt`    |
| `emacs` | 🔁 Avanzado     | ❌ No             | `emacs archivo.txt` |

---

### 🛠️ Instalación

Instala cualquiera de ellos con:

```bash
sudo apt update
sudo apt install nano vim emacs
```

> En WSL o Ubuntu ya suele venir `vim` y `vi`, pero te recomiendo usar `nano` al inicio porque es más intuitivo.

---

### ✏️ Usando `nano` (el más amigable)

#### 📄 Crear o editar un archivo

```bash
nano hola.txt
```

- Si el archivo no existe, lo creará.
- Si existe, lo abrirá para editarlo.

#### 🖱️ Cómo usarlo

- Escribes directamente como en un bloc de notas.
- Las combinaciones como `^X` significan: **Ctrl + X**
- Abajo tienes accesos rápidos para guardar, salir, buscar, etc.

#### 🧪 Comandos útiles en `nano`:

| Acción           | Comando    |
| ---------------- | ---------- |
| Guardar cambios  | `Ctrl + O` |
| Salir del editor | `Ctrl + X` |
| Buscar texto     | `Ctrl + W` |
| Cortar línea     | `Ctrl + K` |
| Pegar línea      | `Ctrl + U` |

---

#### 🧪 Usando `vim` (más avanzado)

```bash
vim hola.txt
```

#### Modo de operación:

- **Modo normal**: Navegas, copias, borras
- **Modo inserción**: Escribes (`i` para entrar)
- **Modo comando**: Ejecutas acciones (`:` para entrar)

##### Acciones básicas:

| Acción                  | Comando |
| ----------------------- | ------- |
| Insertar texto          | `i`     |
| Salir del modo insertar | `Esc`   |
| Guardar                 | `:w`    |
| Salir                   | `:q`    |
| Guardar y salir         | `:wq`   |
| Salir sin guardar       | `:q!`   |

---

### ✅ EJEMPLO COMPLETO (usando `nano`)

#### 🎯 Objetivo: Crear un archivo de texto con un mensaje personalizado

---

#### 1. Abre la terminal y ejecuta:

```bash
nano saludo.txt
```

---

#### 2. Escribe lo siguiente dentro:

```txt
Hola Gustavo,
¡Bienvenido a tu primer archivo creado desde la terminal!
```

---

#### 3. Guarda el archivo:

- Presiona `Ctrl + O` (escribir cambios)
- Presiona `Enter` para confirmar el nombre

---

#### 4. Sal del editor:

- Presiona `Ctrl + X`

---

#### 5. Verifica el contenido:

```bash
cat saludo.txt
```

Deberías ver:

```txt
Hola Gustavo,
¡Bienvenido a tu primer archivo creado desde la terminal!
```

---

### 🧠 ¿Cuándo se usan estos editores?

- En servidores Linux (sin entorno gráfico)
- En WSL para modificar scripts
- Al configurar archivos de sistema (`.bashrc`, `crontab`, etc.)
- En automatización DevOps, ciberseguridad y scripting

---

[🔼](#índice)

---

## **610. Personalizar la terminal de comandos**

### 🧠 ¿Qué significa personalizar la terminal?

Personalizar la terminal significa **cambiar su apariencia y comportamiento** para que sea:

- Más útil (muestra información como la ruta, el usuario, el estado del Git, etc.)
- Más atractiva visualmente (colores, fuentes, temas)
- Más productiva (autocompletado, historial mejorado, alias)

Esto es especialmente útil si usas la terminal frecuentemente (como en desarrollo, scripting o administración de sistemas).

---

### 🛠️ ¿Qué podemos personalizar?

| Elemento              | Ejemplo de personalización              |
| --------------------- | --------------------------------------- |
| **Prompt (PS1)**      | Cambiar cómo se ve la línea de comandos |
| **Colores del texto** | Verde para éxito, rojo para errores     |
| **Alias de comandos** | `ll` en lugar de `ls -la`               |
| **Autocompletado**    | Activar sugerencias inteligentes        |
| **Temas y fuentes**   | Cambiar fuente, tamaño y fondo          |
| **Shell mejorada**    | Usar `zsh` con `oh-my-zsh` para mejoras |

---

### 🔧 Herramientas necesarias

#### ✅ `bash` o `zsh`

- `bash` es el shell predeterminado.
- `zsh` es una alternativa más potente y personalizable.

#### ✅ Archivos de configuración

- `~/.bashrc` (para bash)
- `~/.zshrc` (para zsh)

---

### 📦 Instalación de herramientas opcionales

#### 🔹 Instalar Zsh y Oh My Zsh (opcional pero recomendado)

```bash
sudo apt update
sudo apt install zsh git -y
```

Instala [Oh My Zsh](https://ohmyz.sh) con:

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Esto cambiará tu shell por `zsh` y te dará una terminal mucho más personalizable con colores, plugins, y temas.

---

### 🎨 ¿Cómo se personaliza la terminal?

#### 1. Personaliza el **prompt (PS1)** en `.bashrc` o `.zshrc`

##### 📁 Abre tu archivo:

```bash
nano ~/.bashrc     # o nano ~/.zshrc si usas Zsh
```

Busca o añade esta línea:

```bash
export PS1="\u@\h:\w\$ "
```

Esto significa:

- `\u` = nombre del usuario
- `\h` = nombre del host (computadora)
- `\w` = ruta del directorio
- `\$` = símbolo \$ o #

Resultado:

```
gussdev@laptop:~/Documentos$
```

Puedes agregar colores, por ejemplo:

```bash
export PS1="\[\e[1;32m\]\u@\h:\w\$ \[\e[0m\]"
```

---

#### 2. Añade **alias** para comandos rápidos

En el mismo archivo `.bashrc` o `.zshrc`, agrega:

```bash
alias ll='ls -la --color=auto'
alias gs='git status'
alias cls='clear'
```

Guarda (`Ctrl + O`) y cierra (`Ctrl + X`).

Luego aplica los cambios:

```bash
source ~/.bashrc
# o
source ~/.zshrc
```

---

#### 3. Usa temas en `oh-my-zsh`

Si estás usando `zsh`, edita el archivo `.zshrc`:

```bash
nano ~/.zshrc
```

Busca esta línea:

```bash
ZSH_THEME="robbyrussell"
```

Y cámbiala por, por ejemplo:

```bash
ZSH_THEME="agnoster"
```

Otros temas bonitos: `agnoster`, `powerlevel10k`, `bureau`, `clean`

> Para `powerlevel10k`:

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k
```

En `.zshrc`:

```bash
ZSH_THEME="powerlevel10k/powerlevel10k"
```

---

### ✅ EJEMPLO COMPLETO

#### 🎯 Objetivo: Personalizar tu terminal para que se vea así:

```bash
🌟 Gustavo@mi-pc: ~/Proyectos →
```

---

#### 👣 Paso 1: Edita tu `.bashrc` o `.zshrc`

```bash
nano ~/.bashrc
```

Agrega o edita estas líneas:

```bash
export PS1="\[\e[1;36m\]🌟 \u@\h: \w → \[\e[0m\]"
alias ll='ls -la --color=auto'
alias cls='clear'
```

---

#### 👣 Paso 2: Guarda y aplica los cambios

```bash
source ~/.bashrc
```

---

#### 👣 Paso 3: Probarlo

- Escribe `ll` para listar archivos con color.
- Mira tu nuevo prompt con tu nombre y una flechita.
- Usa `cls` para limpiar.

---

#### 👣 Paso 4 (opcional): Usa `zsh` con `oh-my-zsh`

```bash
sudo apt install zsh git -y
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Edita `.zshrc` para aplicar alias y elegir tema.

---

### 🧠 ¿Por qué personalizar la terminal?

- Trabajas más rápido con alias y autocompletado.
- Puedes ver info útil (nombre del repo git, rama, etc.)
- Se ve más profesional y organizada.
- Aumenta tu productividad y enfoque.

---

[🔼](#índice)

---

| **Inicio**         | **Siguiente 2**                                                     |
| ------------------ | ------------------------------------------------------------------- |
| [🏠](../README.md) | [⏩](./7_2_Introduccion_a_la_Administracion_de_Servidores_Linux.md) |
