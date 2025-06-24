| **Inicio**         | **Siguiente 2**                  |
| ------------------ | -------------------------------- |
| [🏠](../README.md) | [⏩](./1_2_La_shell_de_Linux.md) |

---

## **Índice**

| Temario                                                                          |
| -------------------------------------------------------------------------------- |
| [1. ¿Qué es Linux?](#1-qué-es-linux)                                             |
| [2. ¿Qué distribución de Linux utilizar?](#2-qué-distribución-de-linux-utilizar) |

---

# **Linux: Manejo de comandos y Shell Script**

## **1. ¿Qué es Linux?**

### ✅ ¿Qué es Linux?

**Linux** es un **sistema operativo**, como lo son Windows o macOS. Es el software que se encarga de que todos los programas y el hardware (como el teclado, la pantalla o la impresora) puedan trabajar juntos.

🔧 **Lo especial de Linux:**

- Es **libre y de código abierto**: cualquiera puede ver, modificar o distribuir su código.
- Es **muy estable y seguro**, por eso lo usan en servidores, celulares (como Android) y hasta en supercomputadoras.

#### 🎯 Ejemplo sencillo:

Imagina que tu computadora es una cocina:

- El **hardware** (los utensilios, la estufa, etc.) está ahí.
- Los programas (como un navegador) son los cocineros.
- **Linux** sería el **jefe de cocina** que coordina todo, da acceso a los ingredientes, organiza las tareas, y evita que dos cocineros usen la misma sartén al mismo tiempo.

---

### 🕰️ Antes de Linux

Antes de Linux, los sistemas operativos eran:

- **Propietarios** (cerrados, como MS-DOS o UNIX original).
- **Costosos y con licencias estrictas** (especialmente UNIX, usado en universidades y grandes empresas).
- Limitados: muchos funcionaban sólo en ciertas computadoras específicas.

---

### 🧾 Historia de Linux

1. **1969 – Nace UNIX:**

   - Desarrollado por AT\&T Bell Labs.
   - Era potente, multitarea y usado en universidades.
   - Pero: **no era gratis ni abierto**.

2. **1984 – Proyecto GNU (Richard Stallman):**

   - Quiso crear un sistema operativo libre, llamado GNU.
   - Hizo muchas herramientas (compiladores, editores, etc.), pero **le faltaba el kernel**.

3. **1991 – Linus Torvalds crea Linux:**

   - Estudiante finlandés.
   - Quería hacer un kernel libre para usar en su PC.
   - Publicó el código en internet, y muchos programadores lo ayudaron a mejorarlo.

4. **GNU + Linux = Sistema operativo libre completo**

   - Aunque la gente lo llama “Linux”, el nombre más correcto es “GNU/Linux”.

---

### 🔍 Conceptos básicos

#### 🧠 Kernel

El **kernel** es el **núcleo del sistema operativo**. Se encarga de:

- Comunicar el hardware con el software.
- Administrar la memoria, los procesos, los archivos, etc.

💡 **Ejemplo:**
Si abres una imagen:

- El programa le pide al kernel: “¡Oye, ábreme este archivo!”.
- El kernel se encarga de ir al disco, leer el archivo y pasárselo al programa.

📌 En Linux, el kernel es el archivo principal que se carga al iniciar el sistema.

---

#### 👤 Espacio de usuario (User space)

Es donde corren los programas del usuario: navegadores, editores de texto, juegos, etc.

- **El usuario no accede directamente al hardware**, sino a través del kernel.
- **Separación de espacios:** esto mejora la seguridad y estabilidad. Si una app falla, el kernel sigue funcionando.

💡 **Ejemplo:**
Cuando tú escribes un texto en un editor:

- El editor corre en el espacio de usuario.
- Pero cuando guarda el archivo en el disco, **usa funciones del kernel** para hacerlo.

---

### 📈 Evolución de Linux

Desde que nació en 1991, Linux ha evolucionado muchísimo:

| Época     | Evolución                                      |
| --------- | ---------------------------------------------- |
| 1991      | Primera versión del kernel (0.01), muy básica. |
| 1992–1996 | Se suman miles de desarrolladores.             |
| 1998–2000 | Grandes empresas (IBM, Oracle) lo apoyan.      |
| 2001–2010 | Aparece Android (basado en Linux).             |
| 2010–hoy  | Se usa en la nube, servidores, IoT, etc.       |

📱 **Ejemplos actuales:**

- Android: el sistema más usado en celulares, usa el kernel de Linux.
- Google, Facebook, Amazon: sus servidores funcionan con Linux.
- Raspberry Pi: mini computadora que usa Linux para proyectos caseros.

---

### 🧠 Resumen visual

| Concepto           | Explicación sencilla                                                |
| ------------------ | ------------------------------------------------------------------- |
| Linux              | Sistema operativo libre y de código abierto.                        |
| Antes de Linux     | Sistemas cerrados como UNIX y MS-DOS.                               |
| Historia           | Nace UNIX → Proyecto GNU → Linus crea Linux en 1991.                |
| Kernel             | Parte central que comunica hardware y software.                     |
| Espacio de usuario | Donde se ejecutan las aplicaciones del usuario.                     |
| Evolución          | Desde un hobby en 1991 hasta dominar servidores, móviles y la nube. |

---

[🔼](#índice)

---

## **2. ¿Qué distribución de Linux utilizar?**

### ✅ Distribuciones de Linux

Una **distribución de Linux** es una **versión personalizada del sistema operativo Linux**, que incluye:

- El **kernel de Linux** (el núcleo).
- Programas básicos (como editores, navegadores).
- Gestor de paquetes (para instalar programas).
- Entorno gráfico (escritorio, íconos, ventanas).

💡 **Piensa en el kernel como el motor** y las distribuciones como **el auto completo con el motor incluido**, cada una con una carrocería distinta.

---

### 🧠 ¿Cómo elegir una distribución?

#### Preguntas clave:

1. ¿Eres principiante o tienes experiencia?
2. ¿Lo usarás en una PC antigua o moderna?
3. ¿Lo quieres para aprender, trabajar, programar, administrar servidores o como reemplazo de Windows?

---

### 🔥 Distribuciones de Linux más populares (con ejemplos y detalles)

#### 1. **Ubuntu**

- 📌 Ideal para: **Principiantes**
- ✅ Fácil de instalar y usar
- 🧰 Tiene todo lo necesario (ofimática, navegador, gestor de software)
- 🖼️ Entorno de escritorio: GNOME
- 🌐 Comunidad enorme, muchos tutoriales

**Ejemplo de uso:**
Si eres nuevo en Linux y quieres un sistema amigable, rápido y con una tienda de software, Ubuntu es perfecto.

---

#### 2. **Linux Mint**

- 📌 Ideal para: **Exusuarios de Windows**
- 🎨 Escritorio similar a Windows (Cinnamon)
- 🧰 Incluye códecs de video, software preinstalado (LibreOffice, Firefox)
- 💻 Muy ligero, ideal para PCs antiguas o modestas

**Ejemplo de uso:**
Si vienes de Windows y no quieres complicarte, Mint es fácil y familiar.

---

#### 3. **Debian**

- 📌 Ideal para: **Usuarios con más experiencia**
- 🛡️ Muy estable y confiable (se usa en servidores)
- 🧱 Base de Ubuntu (Ubuntu se deriva de Debian)
- 📦 Menos actualizaciones, pero muy sólido

**Ejemplo de uso:**
Para quienes quieren estabilidad a largo plazo (por ejemplo, montar un servidor o una estación de trabajo confiable).

---

#### 4. **Fedora**

- 📌 Ideal para: **Usuarios intermedios o desarrolladores**
- 🔁 Siempre con software más actualizado
- 🧪 Es el "laboratorio de pruebas" de Red Hat
- 👨‍💻 Muy usado para desarrollo de software

**Ejemplo de uso:**
Un programador que quiere probar las últimas versiones de lenguajes y herramientas puede preferir Fedora.

---

#### 5. **Arch Linux**

- 📌 Ideal para: **Expertos o quienes quieren aprender a fondo**
- 🛠️ Se instala desde cero, muy personalizable
- 📦 Rolling release (siempre actualizado)
- 📘 Excelente documentación (Arch Wiki)

**Ejemplo de uso:**
Un usuario que quiere aprender cómo funciona Linux desde las bases y controlar cada detalle de su sistema.

🔁 **Versión más amigable**: 👉 **Manjaro** (basado en Arch, pero más fácil de instalar)

---

#### 6. **Kali Linux**

- 📌 Ideal para: **Ciberseguridad y hacking ético**
- 🧰 Viene con herramientas como Wireshark, Nmap, Metasploit
- ⚠️ No es para uso diario, sino para pruebas y auditorías

**Ejemplo de uso:**
Un estudiante o profesional de seguridad que quiere practicar pentesting.

---

#### 7. **Zorin OS**

- 📌 Ideal para: **Usuarios que quieren reemplazar Windows**
- 💻 Muy visual, rápido y con apariencia de Windows o macOS
- 🧰 Incluye muchas apps útiles preinstaladas

**Ejemplo de uso:**
Una persona que quiere abandonar Windows sin perder una experiencia similar y sin complicaciones.

---

### 🖥️ Tabla resumen

| Distribución | Nivel       | Ideal para              | Características principales                  |
| ------------ | ----------- | ----------------------- | -------------------------------------------- |
| Ubuntu       | 🟢 Básico   | Usuarios nuevos         | Muy fácil, estable, gran comunidad           |
| Mint         | 🟢 Básico   | Exusuarios de Windows   | Ligero, familiar, todo preinstalado          |
| Debian       | 🟡 Medio    | Servidores, estabilidad | Muy estable, menos actualizaciones           |
| Fedora       | 🟡 Medio    | Desarrolladores         | Moderno, actualizaciones frecuentes          |
| Arch         | 🔴 Avanzado | Aprender Linux a fondo  | Personalizable desde cero, documentación top |
| Manjaro      | 🟡 Medio    | Usuarios intermedios    | Arch más fácil, rolling release              |
| Kali Linux   | 🔴 Avanzado | Ciberseguridad          | Pentesting, no para uso diario               |
| Zorin OS     | 🟢 Básico   | Reemplazar Windows      | Muy visual, todo incluido, aspecto moderno   |

---

### 🧪 ¿Qué puedes hacer con una distribución de Linux?

| Utilidad                           | Distribuciones recomendadas         |
| ---------------------------------- | ----------------------------------- |
| Navegar, ver videos, escribir      | Ubuntu, Mint, Zorin OS              |
| Recuperar una PC vieja             | Linux Lite, Xubuntu, Mint XFCE      |
| Aprender ciberseguridad            | Kali Linux, Parrot OS               |
| Programar                          | Fedora, Ubuntu, Arch, Manjaro       |
| Servidores web / correo            | Debian, CentOS, Ubuntu Server       |
| Hacer pruebas / máquinas virtuales | Cualquiera (en VirtualBox o VMware) |

---

### 🚀 ¿Cuál te recomiendo si estás empezando?

✅ **Linux Mint Cinnamon**

- Muy fácil, liviano, y se parece a Windows.

✅ **Ubuntu Desktop**

- Muy popular, mucha ayuda en internet, estable y completo.

✅ **Zorin OS Lite** (si tienes una PC antigua)

- Rápido, moderno y simple.

---

[🔼](#índice)

---

| **Inicio**         | **Siguiente 2**                  |
| ------------------ | -------------------------------- |
| [🏠](../README.md) | [⏩](./1_2_La_shell_de_Linux.md) |
