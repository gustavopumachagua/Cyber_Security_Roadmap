| **Inicio**         | **atrás 14**                                        | **Siguiente 16**                                  |
| ------------------ | --------------------------------------------------- | ------------------------------------------------- |
| [🏠](../README.md) | [⏪](./7_14_Inteligencia_para_la_Ciberseguridad.md) | [⏩](./7_16_Hacking_Pentesting_con_Metasploit.md) |

---

## **Índice**

| Temario                                                                                              |
| ---------------------------------------------------------------------------------------------------- |
| [913. IP Logger](#913-ip-logger)                                                                     |
| [914. Banner Grabbing](#914-banner-grabbing)                                                         |
| [915. Enumeración de subdominios](#915-enumeración-de-subdominios)                                   |
| [916. Fingerprinting de aplicaciones web](#916-fingerprinting-de-aplicaciones-web)                   |
| [917. Identificación de WAF](#917-identificación-de-waf)                                             |
| [918. Ping y Traceroute](#918-ping-y-traceroute)                                                     |
| [919. Nslookup](#919-nslookup)                                                                       |
| [920. Netdiscover](#920-netdiscover)                                                                 |
| [921. SSLscan](#921-sslscan)                                                                         |
| [922. Enum4Linux](#922-enum4linux)                                                                   |
| [923. Análisis de dispositivos y puertos con Nmap](#923-análisis-de-dispositivos-y-puertos-con-nmap) |
| [924. Parámetros y opciones de escaneo](#924-parámetros-y-opciones-de-escaneo)                       |
| [925. Full TCP scan vs Stealth scan](#925-full-tcp-scan-vs-stealth-scan)                             |
| [926. Fingerprinting con Nmap](#926-fingerprinting-con-nmap)                                         |
| [927. Escaneo Agresivo con Zenmap](#927-escaneo-agresivo-con-zenmap)                                 |
| [928. Análisis de Traceroute](#928-análisis-de-traceroute)                                           |
| [929. Creación de perfiles de escaneo en Zenmap](#929-creación-de-perfiles-de-escaneo-en-zenmap)     |
| [930. Nmap Scripting Engine](#930-nmap-scripting-engine)                                             |
| [931. Gobuster](#931-gobuster)                                                                       |
| [932. Dumpster Diving](#932-dumpster-diving)                                                         |
| [933. Ingeniería Social](#933-ingeniería-social)                                                     |
| [934. Nmap](#934-nmap)                                                                               |
| [935. Joomscan](#935-joomscan)                                                                       |
| [936. Wpscan](#936-wpscan)                                                                           |
| [937. Nessus Essentials](#937-nessus-essentials)                                                     |
| [938. Vega](#938-vega)                                                                               |

# **Escaneo Activo y Análisis de Vulnerabilidades**

## **913. IP Logger**

### 🧠 ¿Qué es un IP Logger?

Un **IP Logger** es una herramienta o servicio web que te permite **capturar la dirección IP** de una persona cuando visita un enlace especial que tú generas.

#### 📌 ¿Para qué sirve?

- Saber desde dónde accede alguien a un enlace.
- Conocer si alguien ha abierto tu mensaje (verificación).
- Analizar patrones geográficos de usuarios (con consentimiento).
- En pruebas de **ingeniería social o Red Teaming** para empresas.

---

### ⚠️ Advertencia importante

El mal uso de IP loggers **puede ser ilegal o violar la privacidad**. Solo deben usarse:

✅ Con consentimiento

✅ En entornos de prueba o simulación

✅ Con fines educativos, éticos o investigativos

---

### 🧰 Formas de usar un IP Logger

Hay dos métodos:

1. **Servicios web ya creados (fáciles)**
2. **Crear tu propio IP Logger en un servidor (más técnico)**

---

### 🔹 Opción 1: Usar un IP Logger ya creado (sencillo)

#### 🧭 Sitios comunes:

- [https://iplogger.org/](https://iplogger.org/)
- [https://grabify.link/](https://grabify.link/)
- [https://2no.co/](https://2no.co/)

#### 🚀 Pasos con Grabify:

1. Ve a: [https://grabify.link/](https://grabify.link/)

2. En el campo "Enter a valid URL", pon cualquier enlace (ej: `https://google.com`)

3. Haz clic en **Create URL**

4. Obtendrás:

   - Un **Tracking Link** (acortado)
   - Un **Tracking Code** para ver las IPs

5. Envía ese enlace a tu “objetivo” (por ejemplo, en una simulación de phishing controlada)

6. Cuando esa persona haga clic, **Grabify registrará su IP**

#### 🧪 Ver resultados:

- En la misma página, escribe el código de tracking.
- Verás:

  - Dirección IP
  - Ciudad / país
  - Sistema operativo
  - Navegador
  - Referente (de dónde vino)

---

### 🔸 Opción 2: Crear tu propio IP Logger (usando PHP)

Esto es más avanzado, pero más **seguro, privado y controlado**.

#### 📦 Requisitos

- Tener **un servidor web** (puede ser local con XAMPP, o remoto)
- Tener **PHP** y **acceso a archivos**

---

#### 🛠 Código básico de IP Logger en PHP

**Archivo:** `iplogger.php`

```php
<?php
$ip = $_SERVER['REMOTE_ADDR'];
$agent = $_SERVER['HTTP_USER_AGENT'];
$log = "IP: $ip | Agente: $agent | Fecha: " . date("Y-m-d H:i:s") . "\n";

// Guardar en archivo de texto
file_put_contents("ips.txt", $log, FILE_APPEND);

// Redireccionar a otro sitio
header("Location: https://google.com");
exit;
?>
```

#### 🧪 ¿Cómo funciona?

1. Alguien entra al archivo `iplogger.php`
2. Su IP y datos del navegador se registran en `ips.txt`
3. Se redirige automáticamente a Google (o cualquier página)

---

#### 🔧 Instalación paso a paso en local (XAMPP)

1. Instala XAMPP: [https://www.apachefriends.org/es/index.html](https://www.apachefriends.org/es/index.html)
2. Abre `htdocs` y crea una carpeta: `mi_ip_logger`
3. Guarda el código `iplogger.php` en esa carpeta
4. Ejecuta Apache desde el panel de control de XAMPP
5. Accede desde navegador a:
   `http://localhost/mi_ip_logger/iplogger.php`

Cuando alguien lo visite, su IP se guardará en `ips.txt`.

---

### 💡 Ejemplo práctico completo

#### 🎯 Escenario: Simulación de phishing (controlado en laboratorio)

1. Usas **Grabify** para acortar el enlace a un documento falso (ej. `https://fakeform.com`)

2. Obtienes el link: `https://grabify.link/ABCD12`

3. Envías el enlace en un mensaje tipo:

   > "Hola, por favor revisa el documento antes de la reunión: \[[https://grabify.link/ABCD12](https://grabify.link/ABCD12)]"

4. La persona da clic → su IP y datos se registran

5. Tú accedes al dashboard de Grabify y ves:

   - IP: `181.65.22.10`
   - País: Perú
   - Navegador: Chrome
   - Sistema: Windows

✅ ¡Simulación exitosa para propósitos de entrenamiento de awareness!

---

### 🛡️ Recomendaciones de seguridad

- Nunca uses IP loggers para fines ilegales (como rastrear sin permiso)
- No publiques enlaces en redes públicas para recolectar IPs al azar
- Si haces pruebas internas en una empresa, documenta y pide permiso

---

### ✅ Conclusión

Un **IP Logger** es una herramienta poderosa para obtener información técnica de una conexión. Usado correctamente, ayuda en investigaciones, pruebas de ciberseguridad o análisis de campañas maliciosas.

Puedes:

- Usar servicios como Grabify para hacerlo fácil
- Crear tu propio logger en PHP para mayor control

---

[🔼](#índice)

---

## **914. Banner Grabbing**

### 🧠 ¿Qué es Banner Grabbing?

**Banner Grabbing** (en español: "captura de banner") es una técnica que se utiliza para **obtener información de un servicio remoto** al conectarse a un puerto abierto. Esta técnica permite identificar:

- El tipo de servicio (por ejemplo, HTTP, SSH, FTP)
- La versión del software del servicio
- Información del sistema operativo (a veces)
- Encabezados de seguridad mal configurados

---

#### 📌 ¿Para qué sirve el Banner Grabbing?

Banner Grabbing es útil en:

✅ **Reconocimiento** durante un test de penetración

✅ **Detección de vulnerabilidades** (por versiones obsoletas)

✅ **Inventario de sistemas y servicios**

✅ **Auditorías de seguridad**

---

### 🔍 Ejemplo de Banner Grabbing

Imagina que hay un servidor con la IP `192.168.1.10` y el puerto 22 abierto (SSH). Si haces una conexión básica, podrías recibir una respuesta así:

```
SSH-2.0-OpenSSH_7.4
```

Esa es información valiosa, porque sabes que corre **OpenSSH versión 7.4**, que puede tener vulnerabilidades conocidas.

---

### 🛠 Herramientas para Banner Grabbing

#### ✅ 1. **Telnet**

Comando clásico para conectarse a puertos manualmente.

#### ✅ 2. **Netcat (nc)**

Herramienta más versátil que Telnet.

#### ✅ 3. **Nmap**

Escáner de red con scripts para banner grabbing automáticos.

---

### 💻 Instalación

#### 🔸 En Linux (Kali o Ubuntu):

```bash
sudo apt update
sudo apt install netcat nmap telnet
```

#### 🔸 En Windows:

1. Puedes usar **CMD** o **PowerShell** para Telnet:
   Primero actívalo:

   - Ir a "Activar o desactivar características de Windows"
   - Habilita **Telnet Client**

2. Instala Nmap desde:
   [https://nmap.org/download.html](https://nmap.org/download.html)

---

### 🧪 Ejemplo completo paso a paso

Supongamos que tienes la IP de un servidor: `192.168.1.100`

---

#### 🧰 Método 1: Banner Grabbing con **Telnet**

```bash
telnet 192.168.1.100 80
```

Luego, escribes manualmente una solicitud HTTP para ver la respuesta:

```
GET / HTTP/1.1
Host: 192.168.1.100
```

Presiona **Enter dos veces**.

📥 Salida esperada:

```
HTTP/1.1 200 OK
Server: Apache/2.4.29 (Ubuntu)
...
```

---

#### 🧰 Método 2: Banner Grabbing con **Netcat**

```bash
nc 192.168.1.100 80
```

Y luego igual que antes:

```
GET / HTTP/1.1
Host: 192.168.1.100
```

📥 Resultado:

```
HTTP/1.1 200 OK
Server: nginx/1.18.0 (Ubuntu)
...
```

---

#### 🧰 Método 3: Banner Grabbing con **Nmap**

Usa el siguiente comando:

```bash
nmap -sV 192.168.1.100
```

📥 Salida ejemplo:

```
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 7.4 (protocol 2.0)
80/tcp   open  http    Apache httpd 2.4.29 ((Ubuntu))
```

Puedes obtener aún más detalles con un script:

```bash
nmap -sV --script=banner 192.168.1.100
```

---

### 🚨 Importancia en ciberseguridad

Con Banner Grabbing puedes:

- Detectar software obsoleto o sin parches
- Encontrar servicios no autorizados (por ejemplo, FTP público)
- Preparar una lista de objetivos para escaneo de vulnerabilidades
- Saber si un servidor revela demasiada información (mala práctica)

---

### 🔐 ¿Cómo protegerte del Banner Grabbing?

- **Oculta banners** innecesarios en Apache, SSH, FTP, etc.
- **Actualiza tus servicios** para evitar que las versiones vulnerables sean detectadas.
- Usa **firewalls** para limitar el acceso a servicios.
- **Escanea tus propios sistemas** para ver lo que otros pueden ver.

---

### ✅ Conclusión

El **Banner Grabbing** es una técnica simple pero poderosa que te ayuda a descubrir qué servicios corren en un servidor y con qué versiones, lo que puede revelar vulnerabilidades.

---

[🔼](#índice)

---

## **915. Enumeración de subdominios**

### 📌 ¿Qué es la enumeración de subdominios?

La **enumeración de subdominios** es el proceso de **descubrir subdominios** pertenecientes a un dominio principal. Esto es una parte fundamental de la **fase de reconocimiento en ciberseguridad** (o pentesting).

Por ejemplo, si el dominio principal es:

```
ejemplo.com
```

Los subdominios pueden ser:

- `mail.ejemplo.com`
- `admin.ejemplo.com`
- `blog.ejemplo.com`

---

### 🤔 ¿Por qué es importante enumerar subdominios?

Porque:

✅ Puede revelar **servicios expuestos innecesariamente**

✅ A veces hay subdominios olvidados con **software obsoleto o sin mantenimiento**

✅ Permite identificar **superficies de ataque más amplias**

✅ Ayuda a detectar entornos de pruebas como: `dev.`, `test.`, `staging.`

---

### 🧰 Herramientas populares para enumeración de subdominios

| Herramienta     | Descripción                                           |
| --------------- | ----------------------------------------------------- |
| **Sublist3r**   | Usa motores de búsqueda y OSINT                       |
| **Amass**       | Potente herramienta para descubrimiento masivo        |
| **Assetfinder** | Muy simple, rápida y útil para OSINT                  |
| **crt.sh**      | Certificados públicos donde aparecen subdominios      |
| **DNSdumpster** | Servicio web gratuito con visualización de registros  |
| **Gobuster**    | Fuerza bruta sobre DNS si tienes una lista de nombres |

---

### 🛠 Instalación de herramientas

#### 📍 En Kali Linux o Ubuntu

##### 1. Instalar **Sublist3r**

```bash
sudo apt install sublist3r
```

O desde GitHub:

```bash
git clone https://github.com/aboul3la/Sublist3r.git
cd Sublist3r
pip install -r requirements.txt
```

##### 2. Instalar **Amass**

```bash
sudo apt install amass
```

---

### 💡 Ejemplo completo

#### 🔎 Vamos a enumerar subdominios del dominio: `example.com`

---

#### ✅ Con Sublist3r

```bash
sublist3r -d example.com
```

📥 Salida esperada:

```
[-] Enumerating subdomains now for example.com
[+] Found 5 subdomains:
 - www.example.com
 - mail.example.com
 - admin.example.com
 - shop.example.com
 - ftp.example.com
```

---

#### ✅ Con Amass

```bash
amass enum -d example.com
```

📥 Salida:

```
www.example.com
api.example.com
dev.example.com
```

_Amass usa fuentes públicas, certificados, registros DNS, OSINT._

---

#### ✅ Usando crt.sh manualmente (web)

1. Ir a: [https://crt.sh](https://crt.sh)
2. Buscar: `%.example.com`
3. Verás certificados SSL donde aparecen subdominios del dominio.

---

### 🧪 Bonus: Enumerar subdominios por fuerza bruta (con Gobuster)

Primero necesitas una lista de palabras (wordlist), como la de SecLists.

```bash
sudo apt install gobuster
```

```bash
gobuster dns -d example.com -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt
```

📥 Resultado:

```
Found: admin.example.com
Found: blog.example.com
Found: support.example.com
```

---

### 🧱 Cómo defenderse

Las empresas deben:

✅ Monitorear continuamente sus subdominios

✅ Eliminar subdominios no utilizados

✅ Aplicar certificados SSL correctamente

✅ Configurar correctamente los registros DNS

---

### 🧠 Conclusión

- La **enumeración de subdominios** es una técnica esencial en ciberseguridad ofensiva.
- Revela **activos ocultos** que pueden tener fallas de seguridad.
- Herramientas como **Sublist3r** y **Amass** hacen este trabajo más fácil y automático.

---

[🔼](#índice)

---

## **916. Fingerprinting de aplicaciones web**

### 📌 ¿Qué es el Fingerprinting de Aplicaciones Web?

El **fingerprinting** (huella digital) de una aplicación web es el proceso de **identificar la tecnología que usa una página web**, como:

- El servidor web (Apache, Nginx, etc.)
- El sistema de gestión de contenidos (WordPress, Joomla…)
- Los frameworks (React, Laravel, Django…)
- El lenguaje backend (PHP, Node.js, etc.)
- Versiones de software
- Sistemas operativos (Linux, Windows Server)

👉 Es una parte esencial de la **fase de reconocimiento pasivo y activo en pentesting.**

---

### 🤔 ¿Por qué es importante?

Porque si sabes **qué tecnologías usa un sitio web**, puedes:

- Buscar **vulnerabilidades conocidas** (CVE) para esa versión.
- Saber cómo está estructurado el sistema.
- Atacar **puntos débiles específicos** de cada tecnología.

---

### 🧰 Herramientas para Fingerprinting

| Herramienta            | ¿Qué hace?                                                 |
| ---------------------- | ---------------------------------------------------------- |
| **WhatWeb**            | Detecta tecnologías web, frameworks, CMS, etc.             |
| **Wappalyzer**         | Extensión del navegador que muestra tecnologías de sitios. |
| **BuiltWith**          | Sitio web que escanea tecnologías utilizadas.              |
| **Nmap + scripts NSE** | Detecta servicios y versiones.                             |
| **Nikto**              | Escáner de vulnerabilidades y servidores web.              |

---

### 🛠 ¿Cómo se instalan?

#### ✅ 1. WhatWeb

**En Kali Linux o Ubuntu:**

```bash
sudo apt install whatweb
```

**O desde GitHub:**

```bash
git clone https://github.com/urbanadventurer/WhatWeb.git
cd WhatWeb
sudo ruby whatweb --help
```

---

#### ✅ 2. Wappalyzer

- Ir a la Chrome Web Store: [https://chrome.google.com/webstore/](https://chrome.google.com/webstore/)
- Buscar **Wappalyzer**
- Clic en "Añadir a Chrome"
- Luego visita cualquier sitio web y verás las tecnologías detectadas automáticamente.

---

#### ✅ 3. BuiltWith

Solo necesitas el navegador:

- Ir a [https://builtwith.com](https://builtwith.com)
- Escribir la URL del sitio web que deseas investigar

---

### 🧪 Ejemplo completo de Fingerprinting

Vamos a analizar el sitio: `https://testphp.vulnweb.com` (un sitio vulnerable de práctica legal de Acunetix)

---

#### 🔍 Paso 1: Usar WhatWeb

```bash
whatweb https://testphp.vulnweb.com
```

📥 Resultado típico:

```
https://testphp.vulnweb.com [200 OK] Country[UNITED STATES][US], HTML5, Apache[2.4.7], IP[192.124.249.3], PHP[5.4.6], Script, Title[Welcome to testphp.vulnweb.com]
```

👉 Este fingerprinting detectó:

- **Servidor web**: Apache 2.4.7
- **Lenguaje backend**: PHP 5.4.6
- **HTML5** como estándar
- El **título** de la página web

---

#### 🔍 Paso 2: Usar Wappalyzer

1. Visita `https://testphp.vulnweb.com` en tu navegador.
2. Haz clic en el icono de Wappalyzer.
3. Detectarás algo como:

```
Technologies:
- Apache
- PHP
- Google Fonts
- HTML5
```

---

#### 🔍 Paso 3: Complementar con Nmap

```bash
nmap -sV testphp.vulnweb.com
```

📥 Resultado:

```
PORT    STATE SERVICE  VERSION
80/tcp  open  http     Apache httpd 2.4.7 ((Ubuntu))
```

---

### 🛡 ¿Cómo protegerse?

Para dificultar el fingerprinting:

✅ Eliminar banners con versiones del servidor (Apache/Nginx)

✅ Usar un WAF (Firewall de Aplicaciones Web)

✅ Ofuscar tecnologías (por ejemplo, cambiar rutas estándar de WordPress)

✅ Actualizar todas las versiones a las más seguras

✅ Configurar correctamente el encabezado HTTP `Server`, `X-Powered-By`, etc.

---

### 🧠 Conclusión

- El **fingerprinting** es clave para **reconocer la superficie de ataque** de una web.
- Herramientas como **WhatWeb**, **Wappalyzer** y **Nmap** te dan una visión técnica muy útil.
- Es una técnica pasiva (si usas solo navegador) o activa (si usas herramientas como Nmap o WhatWeb).

---

[🔼](#índice)

---

## **917. Identificación de WAF**

### 🧱 ¿Qué es un WAF?

Un **WAF (Web Application Firewall)** es un tipo de firewall que **protege aplicaciones web** filtrando, monitoreando y bloqueando tráfico HTTP malicioso.

#### 🚫 ¿Qué bloquea un WAF?

- Inyecciones SQL
- Cross-Site Scripting (XSS)
- Peticiones sospechosas o automatizadas
- Ataques de fuerza bruta

---

### 🤔 ¿Por qué es importante identificar un WAF?

Antes de realizar pruebas de penetración (pentesting), es esencial saber si un sitio está protegido por un WAF porque:

- Podría **bloquear tu IP**.
- Puede **modificar la respuesta del servidor**.
- Puede **detectar firmas de herramientas automáticas**.
- Necesitas **adaptar tus técnicas de ataque** para evadirlo (de forma ética y con permiso).

---

### 🛠 Herramientas para identificar WAF

| Herramienta              | ¿Qué hace?                                              |
| ------------------------ | ------------------------------------------------------- |
| **WafW00f**              | Detecta automáticamente WAFs en sitios web.             |
| **Nmap con scripts NSE** | Puede detectar WAFs en algunos casos.                   |
| **WhatWeb**              | También puede mostrar encabezados o firmas WAF.         |
| **Burp Suite**           | Detecta comportamientos sospechosos en el tráfico HTTP. |

---

### 🧰 Instalación de WafW00f (Recomendado)

#### ✅ En Kali Linux o Ubuntu

```bash
sudo apt update
sudo apt install wafw00f
```

#### ✅ Desde GitHub (si no tienes Kali)

```bash
git clone https://github.com/EnableSecurity/wafw00f.git
cd wafw00f
sudo pip install -r requirements.txt
python3 wafw00f.py -h
```

---

### 💡 ¿Cómo funciona WafW00f?

WafW00f analiza la respuesta del sitio web cuando le hace peticiones HTTP con ciertos patrones. Si un WAF está presente, puede detectar:

- Encabezados HTTP como `Server`, `X-WAF-Blocked`, `X-Sucuri-ID`, etc.
- Códigos de estado HTTP inusuales (403, 406, etc.)
- Comportamientos frente a ataques simulados (como inyecciones)

---

### 🧪 Ejemplo completo de identificación de WAF

Vamos a usar `wafw00f` para analizar un sitio de prueba:

```bash
wafw00f https://www.cloudflare.com
```

📥 Resultado esperado:

```
[*] Checking https://www.cloudflare.com
[+] The site https://www.cloudflare.com is behind Cloudflare (Cloudflare Inc.)
```

👉 Esto te indica que el sitio usa **Cloudflare como WAF**, una de las soluciones más comunes.

---

### 🔍 Otro ejemplo con una web vulnerable

```bash
wafw00f https://testphp.vulnweb.com
```

📥 Resultado típico:

```
[*] Checking https://testphp.vulnweb.com
[-] No WAF detected
```

Esto indica que no hay un WAF activo, y es más fácil hacer pruebas.

---

### 🧪 Complemento con Nmap

Puedes intentar con Nmap y sus scripts NSE:

```bash
nmap -p80,443 --script http-waf-detect testphp.vulnweb.com
```

🔎 Este script intenta detectar la presencia de un WAF enviando peticiones con ataques conocidos y analizando las respuestas.

---

### 🛡 ¿Cómo se protegen los sitios con WAF?

Ejemplos de proveedores de WAF:

- **Cloudflare** (gratuito y de pago)
- **AWS WAF**
- **Imperva**
- **Sucuri**
- **ModSecurity** (open-source para Apache/Nginx)

---

### ⚠️ Consideraciones éticas

❗️**NUNCA escanees un sitio web sin autorización.**
Usa sitios de pruebas como:

- `https://testphp.vulnweb.com`
- `http://dvwa.local` (local)
- Laboratorios de TryHackMe, Hack The Box o PortSwigger

---

### ✅ Conclusión

- Identificar un WAF te permite planear mejor tus pruebas de seguridad.
- La herramienta **wafw00f** es rápida, simple y efectiva.
- Puedes combinarla con otras herramientas como **WhatWeb** y **Nmap**.
- Es un paso importante dentro de la **fase de reconocimiento activo** en un pentest.

---

[🔼](#índice)

---

## **918. Ping y Traceroute**

### 📌 ¿Qué es Ping?

#### 🧠 Definición:

`ping` es una herramienta de red que se usa para comprobar si un **host (computadora, servidor o dispositivo)** está **activo y accesible** a través de una red (como internet).

🔄 Usa el protocolo **ICMP (Internet Control Message Protocol)** para enviar un paquete **Echo Request** al host destino, que si está disponible, responde con un **Echo Reply**.

---

#### ✅ ¿Para qué sirve Ping?

- Saber si un host está “vivo”.
- Medir el **tiempo de ida y vuelta** (latencia).
- Detectar **problemas de conectividad**.
- Verificar la **calidad de la red** (tiempo de respuesta y pérdida de paquetes).

---

#### 📦 ¿Cómo se instala Ping?

En la mayoría de sistemas operativos modernos **ya viene instalado**.

- **Windows:** ya está incluido, solo abre `cmd`.
- **Linux/macOS:** viene por defecto. Si no lo tienes:

  ```bash
  sudo apt install iputils-ping  # En Debian/Ubuntu
  ```

---

#### 🧪 Ejemplo de uso (Linux, macOS o Windows):

```bash
ping google.com
```

📥 Salida típica:

```
64 bytes from 142.250.64.110: icmp_seq=1 ttl=118 time=25.4 ms
64 bytes from 142.250.64.110: icmp_seq=2 ttl=118 time=23.7 ms
...
```

Significa que `google.com` está activo y responde con una latencia de 25.4 ms.

---

### 📌 ¿Qué es Traceroute?

#### 🧠 Definición:

`traceroute` (o `tracert` en Windows) es una herramienta que **muestra la ruta que siguen los paquetes** hasta llegar al host destino.

📍 Cada paso en el camino es un **router (nodo intermedio)**. Traceroute te muestra **todos esos saltos**.

---

#### ✅ ¿Para qué sirve Traceroute?

- Ver el **camino exacto** que siguen los datos por la red.
- Identificar en qué punto **hay lentitud o pérdida** de conexión.
- Detectar **problemas de red entre tu equipo y un servidor**.

---

#### 📦 ¿Cómo se instala Traceroute?

- **Linux:**

  ```bash
  sudo apt install traceroute
  ```

- **macOS:** viene instalado.

- **Windows:** usa el comando `tracert` desde la terminal (`cmd`).

---

#### 🧪 Ejemplo de uso (Linux/macOS):

```bash
traceroute google.com
```

📥 Salida típica:

```
1  192.168.0.1 (192.168.0.1)  1.234 ms  1.112 ms  1.205 ms
2  10.0.0.1 (10.0.0.1)        10.567 ms  10.654 ms  10.712 ms
3  172.217.0.0 (google)       25.456 ms  25.476 ms  25.492 ms
```

Cada línea representa un **salto** (router intermedio).

---

#### Ejemplo en **Windows (cmd)**:

```cmd
tracert google.com
```

📥 Salida:

```
1     1 ms     1 ms     1 ms  192.168.1.1
2    14 ms    12 ms    13 ms  10.0.0.1
3    23 ms    24 ms    25 ms  google.com
```

---

### 🧠 Diferencias clave entre Ping y Traceroute

| Característica     | Ping                    | Traceroute                                |
| ------------------ | ----------------------- | ----------------------------------------- |
| Uso principal      | Ver si un host responde | Ver los nodos por los que pasa un paquete |
| Protocolo usado    | ICMP Echo Request/Reply | ICMP (o UDP en Linux/macOS)               |
| Diagnóstico de red | Simple                  | Más detallado                             |

---

### 💻 Ejemplo completo de análisis con Ping + Traceroute

Supón que no puedes entrar a `example.com`, quieres saber si es tu internet o el servidor. Entonces:

1. **Paso 1 – Ver si el servidor está vivo:**

```bash
ping example.com
```

👉 Si responde, el servidor está **vivo**.

2. **Paso 2 – Ver por dónde fallan los paquetes:**

```bash
traceroute example.com
```

👉 Si se queda detenido en un punto (por ejemplo, en el salto 5), ahí está el cuello de botella o corte.

---

### ✅ Conclusión

- `ping` te dice **si un host responde y qué tan rápido**.
- `traceroute` te dice **por qué camino llegan los datos** y dónde se atascan.
- Son herramientas esenciales para **diagnóstico de redes**, **reconocimiento en hacking ético** y **resolución de problemas**.

---

[🔼](#índice)

---

## **919. Nslookup**

### 🧠 ¿Qué es `nslookup`?

`nslookup` significa **Name Server Lookup**.

Es una **herramienta de red** que te permite consultar información del **DNS (Domain Name System)**, como:

- A qué dirección IP está asociado un dominio (`A` record).
- Qué servidor maneja el correo de un dominio (`MX` record).
- Obtener los servidores de nombre de un dominio (`NS` record).
- Comprobar si el DNS está funcionando correctamente.

---

#### 🧩 ¿Para qué sirve?

- Verificar si un dominio apunta a la IP correcta.
- Identificar posibles errores de DNS.
- Investigar información técnica de sitios web.
- Usado tanto por **administradores de red** como por **hackers éticos** y **auditores**.

---

### 🖥️ ¿Cómo se instala?

La herramienta viene preinstalada en la mayoría de los sistemas:

- **Windows:** viene incluida, solo abre `cmd`.
- **Linux (Debian/Ubuntu):**

```bash
sudo apt install dnsutils
```

- **macOS:** viene preinstalada en Terminal.

---

### 🧪 Sintaxis básica

```bash
nslookup [opciones] [dominio o IP]
```

---

### 🔍 Ejemplos fáciles de entender

---

#### 1. 📌 Consultar la IP de un dominio

```bash
nslookup google.com
```

📥 Salida:

```
Servidor:  router.local
Address:   192.168.0.1

Respuesta no autoritativa:
Nombre:    google.com
Address:   142.250.64.110
```

Significa que `google.com` apunta a esa IP pública.

---

#### 2. 📬 Obtener los servidores de correo (MX records)

```bash
nslookup -query=mx gmail.com
```

📥 Salida:

```
gmail.com MX preference = 5, mail exchanger = gmail-smtp-in.l.google.com
...
```

Esto te dice qué servidores reciben correo para ese dominio.

---

#### 3. 🌐 Obtener los servidores de nombres (NS)

```bash
nslookup -query=ns microsoft.com
```

📥 Salida:

```
microsoft.com nameserver = ns1-204.azure-dns.com
...
```

Muestra quién gestiona el DNS de ese dominio.

---

#### 4. 🧠 Consultar desde otro servidor DNS

Por defecto, usas el DNS de tu red, pero puedes usar otro:

```bash
nslookup google.com 8.8.8.8
```

👉 Esto consulta a **Google DNS** directamente (8.8.8.8).

---

#### 5. 🔁 Inverso: IP a dominio (PTR)

```bash
nslookup 142.250.64.110
```

📥 Salida:

```
Name:  lhr25s31-in-f14.1e100.net
Address: 142.250.64.110
```

Esto se llama **reverse DNS lookup**.

---

### 💻 Ejemplo completo paso a paso

#### Supongamos que quieres investigar `openai.com`.

##### Paso 1 – Obtener su IP:

```bash
nslookup openai.com
```

📥 Resultado:

```
Name:    openai.com
Address: 104.18.12.123
```

##### Paso 2 – Ver quién gestiona su correo:

```bash
nslookup -query=mx openai.com
```

📥 Resultado:

```
openai.com MX preference = 10, mail exchanger = aspmx.l.google.com
```

👉 Usa Gmail para correos.

##### Paso 3 – Saber qué servidores de nombres tiene:

```bash
nslookup -query=ns openai.com
```

📥 Resultado:

```
openai.com nameserver = ns-1123.awsdns-12.org
```

---

### 📦 Bonus: Uso interactivo (modo consola)

Puedes entrar al modo interactivo:

```bash
nslookup
```

Desde ahí puedes escribir comandos como:

```
> set type=mx
> openai.com
> set type=ns
> openai.com
> exit
```

---

### ✅ Conclusión

- `nslookup` es una herramienta **sencilla pero poderosa** para investigar DNS.
- No requiere instalación en Windows o macOS.
- Útil para diagnosticar problemas o investigar objetivos en análisis OSINT o auditorías.
- Se puede usar en modo directo o interactivo.

---

[🔼](#índice)

---

## **920. Netdiscover**

### 🧠 ¿Qué es Netdiscover?

**Netdiscover** es una herramienta de red que sirve para **descubrir dispositivos activos** en una red local (LAN). Se basa en el protocolo **ARP (Address Resolution Protocol)**.

> 🔍 ARP se utiliza para descubrir qué direcciones MAC están asociadas a qué direcciones IP dentro de la misma red.

---

### 🎯 ¿Para qué sirve Netdiscover?

- Ver **qué dispositivos están conectados** a tu red (PCs, celulares, impresoras, cámaras, etc.).
- Detectar **equipos no autorizados** en una red.
- Ayudar en tareas de **reconocimiento pasivo** durante pruebas de penetración.
- Conocer la IP y MAC de cada dispositivo.

---

### 💾 ¿Cómo se instala?

#### 🔧 En Kali Linux (ya viene instalado normalmente):

Si no lo tienes, puedes instalarlo con:

```bash
sudo apt update
sudo apt install netdiscover
```

#### 🐧 En Ubuntu/Debian:

```bash
sudo apt update
sudo apt install netdiscover
```

#### 🏁 En Windows:

Netdiscover **no está disponible para Windows directamente**. Necesitas usarlo dentro de un entorno Linux (como Kali Linux en una máquina virtual o WSL2 con entorno gráfico).

---

### 📗 Sintaxis básica

```bash
sudo netdiscover [opciones]
```

La opción más común:

```bash
sudo netdiscover -r [rango de red]
```

---

### 📌 ¿Cómo saber tu rango de red?

Usa el siguiente comando:

```bash
ip a
```

Ejemplo de salida:

```
inet 192.168.1.25/24
```

Esto significa que tu red está en el rango `192.168.1.0/24`.

---

### 🧪 Ejemplo fácil de entender

#### 🔍 Objetivo:

Saber qué dispositivos están conectados a tu red local.

#### ✅ Paso a paso:

##### Paso 1: Ver tu IP local y rango

```bash
ip a
```

Supón que ves:

```
inet 192.168.0.15/24
```

Tu rango es: `192.168.0.0/24`

---

##### Paso 2: Ejecutar netdiscover

```bash
sudo netdiscover -r 192.168.0.0/24
```

📥 Resultado:

```
Currently scanning: 192.168.0.0/24   |   Screen View: Unique Hosts

IP                MAC Address       Vendor                 Hostname
------------------------------------------------------------------------------
192.168.0.1       00:11:22:33:44:55  TP-Link Technologies   router.local
192.168.0.10      60:57:18:9b:72:c1  Apple Inc              iphone-de-mama
192.168.0.15      48:2a:e3:7c:11:bc  Hewlett Packard        laptop-tuyo
```

✅ ¡Listo! Ya sabes qué dispositivos están conectados a tu red.

---

### 🎓 Otros modos útiles

#### 🔄 Escaneo continuo (no para hasta que tú lo detengas con Ctrl + C):

```bash
sudo netdiscover -s
```

#### 📡 Descubrimiento en redes con DHCP sin especificar rango (modo pasivo):

```bash
sudo netdiscover
```

---

### 🔐 ¿Qué tan útil es esto en ciberseguridad?

Muy útil en la **fase de reconocimiento interno** de una auditoría o pentesting. Por ejemplo:

- Estás conectado a una red Wi-Fi empresarial.
- Ejecutas Netdiscover.
- Descubres todos los dispositivos conectados: servidores, cámaras IP, estaciones de trabajo.
- Puedes tomar nota de IPs para usarlas en escaneos con `nmap`.

---

### 🧪 Ejemplo completo paso a paso

1. Abre tu terminal de Linux.

2. Encuentra tu rango de red:

   ```bash
   ip a
   ```

   ➤ Resultado: `inet 192.168.1.15/24`

3. Ejecuta Netdiscover:

   ```bash
   sudo netdiscover -r 192.168.1.0/24
   ```

4. Analiza la salida:

```
IP              MAC Address         Vendor
---------------------------------------------------------
192.168.1.1     c4:6e:1f:00:aa:11   Cisco Systems
192.168.1.5     9c:b6:d0:1a:11:1f   Samsung Electronics
192.168.1.15    58:55:ca:10:ae:fe   Dell Inc.
```

👉 Ahora sabes qué dispositivos están conectados a tu red.

---

### ✅ Conclusión

| Característica       | Detalle                                          |
| -------------------- | ------------------------------------------------ |
| 💡 Herramienta       | Netdiscover                                      |
| 🛠️ Función principal | Descubrir dispositivos en una red LAN            |
| 🔐 Útil para         | Reconocimiento, seguridad, detección de intrusos |
| 💻 Instalación       | `sudo apt install netdiscover`                   |
| ⚙️ Uso básico        | `sudo netdiscover -r [tu_rango]`                 |

---

[🔼](#índice)

---

## **921. SSLscan**

### 🔐 ¿Qué es SSLScan?

**SSLScan** es una herramienta de código abierto que se utiliza para **auditar la configuración SSL/TLS** de un servidor web. Su objetivo es descubrir:

- Protocolos SSL/TLS soportados (por ejemplo TLS 1.0, 1.1, 1.2, 1.3).
- Cifrados disponibles.
- Certificados válidos y detalles del certificado.
- Versiones inseguras de SSL o TLS.
- Algoritmos débiles (como RC4, DES, etc).

---

### 🛡️ ¿Para qué sirve?

SSLScan se usa en auditorías de ciberseguridad para:

✅ Comprobar si un servidor es vulnerable a fallos conocidos (como POODLE, BEAST, etc).

✅ Ver si un sitio todavía usa **protocolos antiguos inseguros**.

✅ Verificar la **fuerza del cifrado** usado en el tráfico HTTPS.

✅ Saber si el **certificado digital** es válido o tiene errores.

---

### 💻 ¿Cómo se instala SSLScan?

#### ✅ En Kali Linux:

SSLScan ya viene instalado por defecto.

Si no lo está, puedes instalarlo con:

```bash
sudo apt update
sudo apt install sslscan
```

### 🐧 En Ubuntu/Debian:

```bash
sudo apt update
sudo apt install sslscan
```

### 🧪 Verifica instalación:

```bash
sslscan --version
```

---

### ⚙️ Uso básico de SSLScan

```bash
sslscan dominio_o_ip
```

Por ejemplo:

```bash
sslscan google.com
```

Este comando analiza todas las configuraciones SSL/TLS del servidor `google.com`.

---

### 📌 Opciones útiles

| Comando                | Descripción                        |
| ---------------------- | ---------------------------------- |
| `--no-failed`          | Oculta los cifrados que fallaron.  |
| `--tls1_2`             | Fuerza el uso de TLS 1.2.          |
| `--show-certificate`   | Muestra detalles del certificado.  |
| `--output=archivo.txt` | Guarda el resultado en un archivo. |

---

### 🧪 Ejemplo fácil paso a paso

#### Escenario: quieres analizar el SSL/TLS de `example.com`.

##### Paso 1: Abrir terminal

##### Paso 2: Ejecutar el análisis

```bash
sslscan example.com
```

##### Resultado (resumido):

```
SSLv2      not offered
SSLv3      not offered
TLSv1.0    not offered
TLSv1.1    not offered
TLSv1.2    offered
TLSv1.3    offered

Accepted  TLSv1.2  256 bits  ECDHE-RSA-AES256-GCM-SHA384
Accepted  TLSv1.3  256 bits  TLS_AES_256_GCM_SHA384
...
Subject: CN=example.com
Issuer:  CN=Let's Encrypt Authority X3
Not valid before: Jul 15 10:00:00 2025 GMT
Not valid after : Oct 13 10:00:00 2025 GMT
```

✅ Esto te indica que:

- El servidor **no usa versiones antiguas** (SSLv2, SSLv3, TLS1.0).
- Usa **TLS 1.2 y 1.3**, que son seguras.
- El certificado es válido y emitido por Let's Encrypt.

---

### 📁 Guardar resultados

Si quieres guardar el análisis en un archivo:

```bash
sslscan example.com --output=sslscan_result.txt
```

---

### ❗ Análisis de un servidor vulnerable (opcional)

Puedes probar contra servidores vulnerables de prueba como:

```bash
sslscan testssl.sh
```

O páginas tipo **"badssl.com"**:

```bash
sslscan rc4.badssl.com
```

Esto te mostrará qué cifrados débiles siguen aceptando.

---

### 🧠 ¿Por qué es importante?

Muchas organizaciones no saben que sus sitios aún aceptan:

- Protocolos obsoletos como **TLS 1.0**
- Cifrados inseguros como **RC4**
- Certificados caducados

Usar `sslscan` permite **detectar estas debilidades fácilmente**, lo que es clave para proteger la información transmitida (como contraseñas, tarjetas, etc).

---

### ✅ Ejemplo completo: escaneo de una web real

```bash
sslscan --show-certificate --no-failed wikipedia.org
```

📋 Resultado parcial:

```
TLSv1.2  256 bits  ECDHE-RSA-AES256-GCM-SHA384
TLSv1.3  256 bits  TLS_AES_256_GCM_SHA384

Subject: CN=*.wikipedia.org
Issuer:  CN=GlobalSign RSA OV SSL CA 2018
Valid from: Jun 01 00:00:00 2025 GMT
Valid to  : Sep 01 12:00:00 2025 GMT
```

✅ Wikipedia usa TLS 1.2 y 1.3, con buenos cifrados y un certificado válido.

---

### 📌 Conclusión rápida

| Elemento         | Descripción                                        |
| ---------------- | -------------------------------------------------- |
| 🔧 Herramienta   | `sslscan`                                          |
| 🎯 Objetivo      | Auditar configuraciones SSL/TLS                    |
| 🛡️ Uso           | Seguridad web, análisis de cifrados y certificados |
| 💻 Instalación   | `sudo apt install sslscan`                         |
| 📗 Comando clave | `sslscan dominio.com`                              |

---

[🔼](#índice)

---

## **922. Enum4Linux**

### 🛠️ ¿Qué es Enum4linux?

**Enum4linux** es una herramienta escrita en Perl que permite **enumerar información desde sistemas Windows a través del protocolo SMB (Server Message Block)**.

👉 Es muy útil para recopilar información sin necesidad de credenciales válidas.

---

### 🔍 ¿Para qué sirve?

Enum4linux puede recuperar:

| Información              | Descripción                                           |
| ------------------------ | ----------------------------------------------------- |
| Usuarios                 | Lista de usuarios locales en el sistema Windows       |
| Grupos                   | Grupos locales definidos                              |
| Comparticiones (shares)  | Carpetas compartidas vía SMB                          |
| Políticas de seguridad   | Configuraciones como la longitud mínima de contraseña |
| Sistemas operativos      | Nombre del SO, versión, etc.                          |
| Controladores de dominio | Información sobre el dominio si es parte de uno       |

---

### ✅ ¿Cuándo usarla?

Durante la **fase de enumeración** en una auditoría de red (Red Team o pruebas de penetración), cuando hay máquinas Windows activas y el puerto **139 o 445** está abierto.

---

### 💻 Instalación paso a paso

#### 🔸 En Kali Linux

Enum4linux viene instalado por defecto. Si no está, puedes instalarlo así:

```bash
sudo apt update
sudo apt install enum4linux
```

#### 🔸 En Ubuntu/Debian

```bash
sudo apt update
sudo apt install enum4linux
```

> También puedes clonar el repositorio:

```bash
git clone https://github.com/CiscoCXSecurity/enum4linux
cd enum4linux
chmod +x enum4linux.pl
```

Y ejecutarlo con:

```bash
./enum4linux.pl [IP]
```

---

### ⚙️ Uso básico

```bash
enum4linux [opciones] [IP_del_objetivo]
```

#### Ejemplo mínimo:

```bash
enum4linux 192.168.1.10
```

Esto intentará extraer toda la información posible del host.

---

### 🔧 Opciones comunes

| Opción                     | Descripción                                        |
| -------------------------- | -------------------------------------------------- |
| `-a`                       | Ejecuta **todas** las pruebas (opción recomendada) |
| `-u usuario -p contraseña` | Usar credenciales si las tienes                    |
| `-U`                       | Enumera usuarios                                   |
| `-S`                       | Enumera comparticiones SMB (shares)                |
| `-G`                       | Enumera grupos                                     |
| `-P`                       | Enumera políticas de contraseña                    |

---

### 🧪 Ejemplo práctico: Escaneo completo

#### Paso 1: Descubres una máquina Windows en tu red (por ejemplo, `192.168.1.15`) con `nmap`:

```bash
nmap -sS -p 139,445 192.168.1.15
```

Resultado:

```
PORT    STATE SERVICE
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
```

⚠️ Estos puertos son usados por SMB → perfecto para `enum4linux`.

---

#### Paso 2: Ejecutar Enum4linux

```bash
enum4linux -a 192.168.1.15
```

Resultado parcial:

```
[*] Enumerating users using SID S-1-5-21...
Found user: Administrator
Found user: Guest
Found user: juan
Found user: carlos

[*] Enumerating share drives...
Found share: C$
Found share: IPC$
Found share: Public

[*] Password policy...
Min password length: 8
Password history length: 24
```

✅ ¡Has conseguido usuarios, políticas y comparticiones sin necesidad de contraseña!

---

### 🛡️ ¿Por qué es útil para ciberseguridad?

Con `enum4linux` puedes:

- Enumerar **usuarios y grupos** para ataques de fuerza bruta.
- Ver políticas débiles (como contraseñas cortas).
- Acceder a carpetas compartidas sin autenticación.
- Saber si la máquina es parte de un dominio.

---

### 🧠 Recomendaciones

- Enum4linux es ruidosa, puede **generar alertas** en un sistema bien protegido.
- Si no funciona, prueba con `smbclient`, `rpcclient` o herramientas como `crackmapexec`.
- No es solo para pentesters, también lo usan defensores para auditar sistemas internos.

---

### ✅ Resumen

| Elemento              | Detalle                                             |
| --------------------- | --------------------------------------------------- |
| 🎯 Herramienta        | Enum4linux                                          |
| 🧰 Función            | Enumeración SMB de sistemas Windows                 |
| 📌 Instalación        | `sudo apt install enum4linux` o clonar de GitHub    |
| 💻 Uso                | `enum4linux -a 192.168.X.X`                         |
| 📊 Información que da | Usuarios, shares, SO, políticas de contraseña, etc. |

---

[🔼](#índice)

---

## **923. Análisis de dispositivos y puertos con Nmap**

### 🔍 ¿Qué es Nmap?

**Nmap (Network Mapper)** es una herramienta de **código abierto** muy utilizada en ciberseguridad para:

- Detectar dispositivos activos en una red.
- Analizar puertos abiertos.
- Detectar servicios y versiones que corren en los puertos.
- Identificar el sistema operativo del objetivo (fingerprinting).

> Es ideal para la **fase de reconocimiento y escaneo** en un análisis de vulnerabilidades o pruebas de penetración (pentesting).

---

### 🛠️ ¿Cómo se instala Nmap?

#### 🔸 En Linux (Kali, Ubuntu, Debian)

Nmap ya viene preinstalado en Kali. Si no lo tienes:

```bash
sudo apt update
sudo apt install nmap
```

#### 🔸 En Windows

1. Ve a la página oficial: [https://nmap.org/download.html](https://nmap.org/download.html)
2. Descarga el **instalador de Nmap** para Windows.
3. Sigue el asistente de instalación. Se instalará con **Zenmap** (la versión gráfica).

#### 🔸 En macOS

Si tienes Homebrew:

```bash
brew install nmap
```

---

### ✅ Comandos básicos de Nmap (explicados)

#### 1. 🔎 Escaneo rápido de una IP

```bash
nmap 192.168.1.1
```

- Verifica si la IP está activa.
- Enumera los puertos abiertos más comunes (los 1000 primeros por defecto).

---

#### 2. 🌐 Escaneo de red (todos los dispositivos)

```bash
nmap -sn 192.168.1.0/24
```

- Descubre qué **dispositivos están activos** en una red (escaneo ping).
- Ideal para saber **cuántos equipos hay conectados**.

> Resultado típico:

```
Nmap scan report for 192.168.1.1
Host is up (0.0050s latency).
MAC Address: XX:XX:XX:XX:XX:XX (Tp-Link)

Nmap scan report for 192.168.1.10
Host is up (0.0020s latency).
MAC Address: XX:XX:XX:XX:XX:XY (Dell)
```

---

#### 3. 🔓 Escaneo de puertos abiertos

```bash
nmap -p- 192.168.1.10
```

- Escanea **todos los 65535 puertos**.
- Útil para descubrir servicios no comunes.

---

#### 4. 🧠 Detección de servicios y versiones

```bash
nmap -sV 192.168.1.10
```

- Analiza los servicios activos en los puertos abiertos y muestra su **versión**.

Ejemplo de salida:

```
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 7.9
80/tcp   open  http    Apache httpd 2.4.29
```

---

#### 5. 🧠 Identificación del sistema operativo

```bash
nmap -O 192.168.1.10
```

- Intenta identificar el **sistema operativo** del dispositivo objetivo.

> Requiere permisos de superusuario (`sudo`) y que el equipo no esté filtrando.

---

#### 6. 🧪 Escaneo completo combinado

```bash
sudo nmap -A 192.168.1.10
```

- Realiza detección de sistema operativo, versión de servicios, traceroute, y más.
- Es muy ruidoso (alerta a firewalls y sistemas IDS).

---

### 🧪 Ejemplo completo paso a paso

#### 🔧 Escenario:

Estás en una red local (Wi-Fi de tu casa) y quieres descubrir todos los dispositivos conectados y qué servicios ofrecen.

#### Paso 1: Descubrir dispositivos conectados

```bash
nmap -sn 192.168.1.0/24
```

Supongamos que encuentras:

- Tu router: `192.168.1.1`
- Tu laptop: `192.168.1.5`
- Un servidor sospechoso: `192.168.1.20`

#### Paso 2: Escanear puertos y servicios en el servidor

```bash
nmap -sV -p- 192.168.1.20
```

Resultado:

```
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 8.2
80/tcp   open  http    Apache httpd 2.4.41
139/tcp  open  netbios-ssn Samba smbd 3.X
445/tcp  open  microsoft-ds Samba smbd 3.X
```

Significa que:

- Hay un servidor SSH (podría intentarse login por fuerza bruta).
- Está sirviendo una página web en Apache.
- Usa **Samba** (acceso remoto a archivos estilo Windows).

#### Paso 3: Intentar identificar el sistema operativo

```bash
sudo nmap -O 192.168.1.20
```

Resultado:

```
OS details: Linux 5.4 - 5.8
```

---

### 🚨 ¡Advertencia!

- Nmap puede ser detectado por **firewalls o IDS** (como Snort).
- Solo debes escanear redes donde **tienes permiso**.
- No escanees sitios públicos sin autorización (puede considerarse ilegal).

---

### 🧠 Consejos de uso

| Consejo           | Detalle                                              |
| ----------------- | ---------------------------------------------------- |
| Usa `-v` o `-vv`  | Para ver más detalle del escaneo en tiempo real      |
| Usa `-T4` o `-T5` | Para hacer el escaneo más rápido (pero más ruidoso)  |
| Usa `-Pn`         | Si el objetivo no responde a ping, fuerza el escaneo |

---

### 📋 Resumen rápido

| Tarea                  | Comando Nmap              |
| ---------------------- | ------------------------- |
| Escaneo simple         | `nmap IP`                 |
| Escanear red           | `nmap -sn 192.168.X.0/24` |
| Todos los puertos      | `nmap -p- IP`             |
| Detección de servicios | `nmap -sV IP`             |
| Detección de SO        | `nmap -O IP`              |
| Escaneo agresivo       | `nmap -A IP`              |

---

[🔼](#índice)

---

## **924. Parámetros y opciones de escaneo**

### 🧠 ¿Qué son los parámetros y opciones de escaneo en Nmap?

Los **parámetros de escaneo** son **opciones y banderas** que le indicas a Nmap para realizar escaneos de red más precisos, eficientes o enfocados según tu objetivo:

- Buscar **puertos abiertos**.
- Determinar **sistemas operativos**.
- Detectar **servicios en ejecución**.
- Hacer el escaneo **más rápido o sigiloso**, etc.

---

### 🛠️ ¿Cómo se instala Nmap?

#### En Kali Linux / Ubuntu / Debian:

```bash
sudo apt update
sudo apt install nmap
```

#### En Windows:

1. Ve a [https://nmap.org/download.html](https://nmap.org/download.html).
2. Descarga el instalador.
3. Sigue el asistente de instalación.

#### En macOS (con Homebrew):

```bash
brew install nmap
```

---

### 🧪 Parámetros y opciones más comunes (con ejemplos)

#### 🔹 `-sS` → Escaneo TCP SYN (rápido y discreto)

```bash
nmap -sS 192.168.1.10
```

Este escaneo se llama **"half-open scan"** y es difícil de detectar por firewalls o IDS.

---

#### 🔹 `-sT` → Escaneo TCP completo (conexión total)

```bash
nmap -sT 192.168.1.10
```

Es más fácil de detectar. Se usa si no tienes privilegios de root/sudo.

---

#### 🔹 `-p` → Escanear puertos específicos

```bash
nmap -p 22,80,443 192.168.1.10
```

Escanea **solo los puertos 22 (SSH), 80 (HTTP) y 443 (HTTPS)**.

---

#### 🔹 `-p-` → Escanear **todos los puertos**

```bash
nmap -p- 192.168.1.10
```

Escanea del **1 al 65535**. Útil cuando buscas servicios no convencionales.

---

#### 🔹 `-sV` → Detectar **servicios y versiones**

```bash
nmap -sV 192.168.1.10
```

Detecta el **tipo de servicio** en cada puerto y su **versión**.

---

#### 🔹 `-O` → Detección de sistema operativo

```bash
sudo nmap -O 192.168.1.10
```

Intenta identificar el sistema operativo del equipo.

---

#### 🔹 `-A` → Escaneo agresivo

```bash
sudo nmap -A 192.168.1.10
```

Incluye:

- Detección de OS
- Versión de servicios
- Script scanning (NSE)
- Traceroute

**¡Cuidado!** Puede ser muy visible para IDS/firewalls.

---

#### 🔹 `-T` → Velocidad del escaneo (de 0 a 5)

```bash
nmap -T4 192.168.1.10
```

- `-T0`: muy lento, sigiloso.
- `-T4`: rápido, usado comúnmente.
- `-T5`: muy rápido, pero ruidoso.

---

#### 🔹 `-Pn` → Omitir ping (si el host no responde al ping)

```bash
nmap -Pn 192.168.1.10
```

Fuerza el escaneo incluso si el host no responde a ping.

---

#### 🔹 `-v` o `-vv` → Modo verbose

```bash
nmap -v 192.168.1.10
```

Muestra más información en tiempo real.

---

#### 🔹 `-oN`, `-oX`, `-oG` → Guardar resultados

```bash
nmap -oN resultado.txt 192.168.1.10
```

- `-oN`: salida normal (texto plano).
- `-oX`: salida XML.
- `-oG`: salida para grep (útil para automatización).

---

#### 🔹 `-iL` → Leer una lista de IPs desde archivo

```bash
nmap -iL lista_ips.txt
```

Si tienes varias IPs o rangos que quieres escanear.

---

#### 🔹 `--open` → Mostrar solo puertos abiertos

```bash
nmap --open 192.168.1.10
```

Ignora puertos cerrados o filtrados.

---

### 🧪 Ejemplo completo con múltiples parámetros

Supongamos que quieres escanear la red local `192.168.1.0/24`, obtener los servicios, guardar el resultado y hacerlo rápido pero efectivo:

```bash
sudo nmap -sS -sV -p 1-1000 -T4 --open -oN reporte.txt 192.168.1.0/24
```

#### ¿Qué hace?

- `-sS`: escaneo SYN (más discreto)
- `-sV`: detecta versiones de servicios
- `-p 1-1000`: escanea los primeros 1000 puertos
- `-T4`: escaneo rápido
- `--open`: muestra solo puertos abiertos
- `-oN reporte.txt`: guarda el resultado en un archivo de texto
- `192.168.1.0/24`: escanea toda la red local

---

### ✅ Conclusión

Los **parámetros de escaneo de Nmap** te permiten personalizar al máximo el tipo de información que deseas obtener de una red o dispositivo. Aprenderlos y combinarlos es clave para un buen análisis en ciberseguridad.

---

[🔼](#índice)

---

## **925. Full TCP scan vs Stealth scan**

### 🔍 ¿Qué es un escaneo de puertos TCP?

Antes de entrar en las diferencias, es importante entender que cuando se realiza un escaneo de puertos, el objetivo es **identificar qué servicios están corriendo en una máquina**, es decir, **qué puertos están abiertos** y qué aplicaciones están escuchando en ellos.

---

### 💣 Full TCP Scan (`-sT`) – Escaneo de Conexión Completa

#### ✅ ¿Qué es?

El **Full TCP Scan** o **TCP Connect Scan** realiza una **conexión completa (three-way handshake)** con el puerto de destino.

Pasos:

1. Envía un paquete **SYN**.
2. Si el puerto está abierto, el host responde con un **SYN-ACK**.
3. El escáner responde con un **ACK**, completando la conexión.
4. Luego **cierra la conexión** con un FIN o RST.

#### 🔧 Ventajas

- No necesita privilegios de root.
- Utiliza la pila TCP del sistema operativo.
- Muy confiable.

#### 🚫 Desventajas

- Muy **fácil de detectar** por firewalls e IDS (Intrusion Detection Systems).
- Más **lento** que el escaneo SYN.

#### 🔍 Ejemplo:

```bash
nmap -sT 192.168.1.100
```

Escanea usando conexión completa. Ideal si no puedes usar `sudo`.

---

### 🕵️ Stealth Scan (`-sS`) – Escaneo Sigiloso o Half-Open

#### ✅ ¿Qué es?

El **SYN Scan** o **escaneo sigiloso** realiza solo la **primera parte del handshake TCP**:

1. Envía un paquete **SYN**.
2. Si recibe un **SYN-ACK**, detecta que el puerto está abierto.
3. Luego envía un **RST** para evitar completar la conexión.

> Como **no se completa la conexión**, muchos sistemas no lo registran como actividad sospechosa.

#### 🔧 Ventajas

- **Mucho más rápido** que el Full TCP scan.
- **Menos detectable**, ideal para auditorías de seguridad.
- Ofrece información precisa sobre puertos abiertos.

#### 🚫 Desventajas

- Requiere **privilegios de root o sudo** (en Linux/macOS).
- Algunos firewalls avanzados pueden detectarlo.

#### 🔍 Ejemplo:

```bash
sudo nmap -sS 192.168.1.100
```

Este es el **escaneo por defecto** de Nmap cuando usas `sudo`.

---

### ⚙️ Cómo instalar Nmap

#### 🔹 Kali Linux / Ubuntu / Debian:

```bash
sudo apt update
sudo apt install nmap
```

#### 🔹 Windows:

1. Ve a [https://nmap.org/download.html](https://nmap.org/download.html).
2. Descarga el instalador (incluye Zenmap).
3. Sigue los pasos del asistente.

#### 🔹 macOS:

```bash
brew install nmap
```

---

### 🧪 Comparación rápida

| Característica          | Full TCP Scan (`-sT`)      | Stealth Scan (`-sS`)   |
| ----------------------- | -------------------------- | ---------------------- |
| Tipo de conexión        | Completa (3-way handshake) | Incompleta (half-open) |
| Necesita root/sudo      | ❌ No                      | ✅ Sí                  |
| Detección por firewalls | Fácil de detectar          | Difícil de detectar    |
| Velocidad               | Más lento                  | Más rápido             |
| Precisión               | Alta                       | Muy alta               |

---

### ✅ Ejemplo completo

Escenario: quieres escanear una red entera para encontrar puertos abiertos de forma sigilosa y también hacer un escaneo completo por si uno falla.

#### Paso 1: Stealth Scan (más discreto)

```bash
sudo nmap -sS -p 22,80,443 -T4 192.168.1.0/24 -oN sigiloso.txt
```

- `-sS`: SYN scan.
- `-p`: escanea puertos comunes (SSH, HTTP, HTTPS).
- `-T4`: velocidad alta pero razonable.
- `-oN`: guarda el resultado.

#### Paso 2: Full TCP Scan (por si no tienes privilegios)

```bash
nmap -sT -p 22,80,443 -T4 192.168.1.0/24 -oN completo.txt
```

#### Resultado

Tendrás dos archivos (`sigiloso.txt` y `completo.txt`) con los resultados, y puedes comparar si hubo diferencias entre métodos.

---

### 🧠 Conclusión

- **Full TCP Scan**: más fácil de usar, pero más evidente.
- **Stealth Scan**: mejor opción para auditorías, más rápido y sigiloso.
- Ambos son útiles dependiendo del contexto y permisos del sistema.

---

[🔼](#índice)

---

## **926. Fingerprinting con Nmap**

### 🔍 ¿Qué es el Fingerprinting con Nmap?

El **fingerprinting** (o huella digital) en ciberseguridad es el proceso de **identificar información específica de un sistema remoto** como:

- Sistema operativo (OS).
- Servicios y versiones en ejecución.
- Tipo de dispositivo.
- Arquitectura de red.

Nmap incluye técnicas para hacer **OS Fingerprinting** (detectar el sistema operativo) y **Service Fingerprinting** (detectar la versión de los servicios).

---

### 🧠 ¿Por qué es importante?

El fingerprinting es una **fase de reconocimiento** en una auditoría o prueba de penetración. Saber qué sistema operativo o versión de un servicio corre en una máquina te puede ayudar a:

- Encontrar vulnerabilidades específicas.
- Planificar ataques más precisos.
- Verificar configuraciones de seguridad.

---

### 🔧 ¿Cómo se instala Nmap?

#### En Linux (Debian, Ubuntu, Kali):

```bash
sudo apt update
sudo apt install nmap
```

#### En macOS:

```bash
brew install nmap
```

(Requiere Homebrew)

#### En Windows:

1. Ve a [https://nmap.org/download.html](https://nmap.org/download.html).
2. Descarga el instalador para Windows.
3. Instálalo como cualquier otro programa.

---

### 📘 Tipos de Fingerprinting con Nmap

#### 1. **Service Fingerprinting** (detectar versiones de servicios)

Usa el parámetro `-sV` para detectar qué versiones de software están corriendo.

```bash
nmap -sV 192.168.1.10
```

Esto puede detectar cosas como:

- Apache 2.4.29
- OpenSSH 7.6
- Microsoft IIS 10.0

---

#### 2. **OS Fingerprinting** (detectar el sistema operativo)

Usa el parámetro `-O`. Nmap analiza detalles de la respuesta TCP/IP para adivinar el sistema operativo.

```bash
sudo nmap -O 192.168.1.10
```

Resultado esperado:

> Running: Linux 5.X, Windows 10, FreeBSD, etc.

> ⚠️ Requiere privilegios de superusuario (`sudo`) para enviar ciertos paquetes.

---

#### 3. **Fingerprinting agresivo**

Usa `-A` para combinar varios tipos de fingerprinting:

```bash
sudo nmap -A 192.168.1.10
```

Esto hace:

- OS detection (`-O`)
- Version detection (`-sV`)
- Script scanning (`-sC`)
- Traceroute

---

#### 4. **Script-based Fingerprinting**

Nmap viene con muchos scripts NSE (Nmap Scripting Engine) para escanear cosas específicas como:

```bash
nmap --script http-title 192.168.1.10
```

Este script extrae el título de una página web, útil para fingerprinting web.

---

### 📦 Otras opciones útiles

| Opción              | Significado                          |
| ------------------- | ------------------------------------ |
| `-sS`               | Escaneo SYN (stealth scan)           |
| `-sT`               | Escaneo TCP completo                 |
| `-T4`               | Velocidad media/rápida del escaneo   |
| `-p-`               | Escanear todos los puertos (0-65535) |
| `-v`                | Modo verbose (más detalles)          |
| `-oN`, `-oX`, `-oG` | Salida en diferentes formatos        |

---

### ✅ Ejemplo completo

Escenario: quieres identificar qué sistema operativo y qué servicios están corriendo en la IP `192.168.1.10`.

#### Paso 1: Escaneo básico de puertos

```bash
nmap -p 1-1000 192.168.1.10
```

#### Paso 2: Detección de servicios (versiones)

```bash
nmap -sV 192.168.1.10
```

#### Paso 3: Fingerprinting del sistema operativo

```bash
sudo nmap -O 192.168.1.10
```

#### Paso 4: Escaneo agresivo todo en uno

```bash
sudo nmap -A 192.168.1.10 -T4 -v -oN informe_fingerprint.txt
```

- `-A`: fingerprinting completo.
- `-T4`: velocidad alta.
- `-v`: modo detallado.
- `-oN`: guarda el informe en un archivo de texto.

---

### 🧪 Resultado esperado (ejemplo)

```bash
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 8.2 (protocol 2.0)
80/tcp   open  http    Apache httpd 2.4.41 ((Ubuntu))
MAC Address: 00:0C:29:9A:77:BA (VMware)
Device type: general purpose
Running: Linux 5.X
OS details: Linux 5.0 - 5.8
Network Distance: 1 hop
```

---

### 🧠 Conclusión

- El **fingerprinting** permite conocer el sistema y servicios remotos.
- Es vital en **ciberseguridad ofensiva y defensiva**.
- Nmap es una herramienta potente y versátil para este propósito.
- Puedes usar `-sV`, `-O` y `-A` para obtener la información más útil.

---

[🔼](#índice)

---

## **927. Escaneo Agresivo con Zenmap**

### 🧠 ¿Qué es Zenmap?

**Zenmap** es la interfaz gráfica oficial de **Nmap**, diseñada para facilitar el uso de esta poderosa herramienta de escaneo de redes a usuarios principiantes y avanzados.

Con Zenmap puedes:

- Realizar escaneos rápidos o avanzados sin usar la terminal.
- Guardar resultados y compararlos visualmente.
- Crear perfiles personalizados de escaneo.
- Ver gráficamente la topología de la red escaneada.

---

### 🔍 ¿Qué es un Escaneo Agresivo?

Un **escaneo agresivo** busca recopilar la **máxima cantidad de información posible** sobre un host o red, incluyendo:

- **Sistema operativo** (OS).
- **Versiones** de servicios.
- **Puertos abiertos**.
- **Scripts NSE comunes**.
- **Ruta de red (Traceroute)**.

Este tipo de escaneo usa el comando de Nmap:

```bash
nmap -A <IP>
```

En Zenmap, esta opción está disponible como perfil predefinido.

---

### 🛠️ ¿Cómo se instala Zenmap?

#### 🔸 En Linux (Debian, Ubuntu, Kali)

Zenmap ya no está en los repositorios recientes, pero puedes instalarlo con paquetes `.deb`.

1. Descarga el `.deb` desde [https://nmap.org/dist/old/](https://nmap.org/dist/old/)
2. Instálalo manualmente:

```bash
sudo apt install ./zenmap-7.91-1.noarch.deb
```

⚠️ También necesitas tener **Python 2** instalado, ya que Zenmap depende de él.

#### 🔸 En Windows

1. Ve a [https://nmap.org/download.html](https://nmap.org/download.html)
2. Descarga el **"Self-installer"** que incluye Zenmap.
3. Instálalo como cualquier programa.
4. Abre **Zenmap GUI** desde el menú inicio.

---

### 💡 Interfaz de Zenmap

Cuando abres Zenmap, verás:

- **Target**: IP o dominio a escanear.
- **Profile**: Escaneo a ejecutar (por ejemplo: "Intense scan").
- **Command**: La línea de comandos equivalente.
- **Output**: Resultado en texto.
- **Ports/Hosts**: Puertos y dispositivos encontrados.
- **Topology**: Vista gráfica de la red.
- **Host Details**: Información detallada.
- **Scans**: Historial de escaneos.

---

### ✅ Ejemplo completo: Escaneo agresivo con Zenmap

#### 🎯 Escenario

Queremos escanear el host: `192.168.1.10` para obtener información completa sobre puertos, servicios, sistema operativo y traceroute.

---

#### 📝 Paso 1: Abrir Zenmap

Abre Zenmap como **administrador** (recomendado para escaneos agresivos).

---

#### 📝 Paso 2: Completar los campos

- **Target**: `192.168.1.10`
- **Profile**: Selecciona `"Intense scan"`
  (equivale a `nmap -T4 -A -v`)
- Haz clic en el botón **Scan**

---

#### 🕵️‍♂️ ¿Qué hace ese perfil?

- `-T4`: Aumenta la velocidad del escaneo.
- `-A`: Habilita detección de SO, versiones, scripts NSE, traceroute.
- `-v`: Salida detallada (verbose).

---

#### 🧪 Resultado esperado

En la pestaña **"Nmap Output"**, verás algo como esto:

```
Starting Nmap...
Nmap scan report for 192.168.1.10
Host is up (0.0010s latency).
Not shown: 996 closed ports
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 7.6p1 Ubuntu
80/tcp   open  http    Apache httpd 2.4.29 ((Ubuntu))
Device type: general purpose
Running: Linux 5.X
OS details: Linux 5.0 - 5.8
Network Distance: 1 hop
```

---

#### 🖼️ Paso 3: Explorar pestañas útiles

- **Ports/Hosts**: Lista los puertos y servicios activos.
- **Topology**: Dibuja la red y los "saltos" hasta el host.
- **Host Details**: Muestra todo lo que Nmap descubrió sobre el host.

---

### 📦 Exportar resultados

Puedes guardar el informe como:

- Texto (`.txt`)
- XML (`.xml`)
- Script Kiddie (resumen técnico para informes)
- Comparar escaneos anteriores

Archivo → Save Scan...

---

### 🧠 Conclusión

- **Zenmap** es ideal si prefieres una interfaz gráfica.
- El **escaneo agresivo** entrega mucha información, ideal para auditorías de red.
- Úsalo con precaución y siempre con permiso — puede generar alertas en sistemas monitoreados.

---

[🔼](#índice)

---

## **928. Análisis de Traceroute**

### 🔎 ¿Qué es Traceroute?

**Traceroute** es una herramienta de red que permite rastrear el **camino que toma un paquete de datos** desde tu computadora hasta un servidor o dirección IP en Internet.

Sirve para:

- Identificar **dónde hay lentitud o problemas en la red**.
- Conocer la **ruta física y lógica** que sigue tu conexión.
- Detectar **saltos intermedios (routers)** entre tu dispositivo y el destino.
- Analizar **la latencia (tiempo de respuesta)** en cada salto.

---

### 🧠 ¿Cómo funciona Traceroute?

1. Traceroute envía paquetes con un valor llamado **TTL (Time To Live)**.
2. El TTL empieza en 1 y aumenta en cada intento.
3. Cada **router** por el que pasa el paquete reduce el TTL en 1.
4. Cuando el TTL llega a 0, el router **responde con un mensaje ICMP "Time Exceeded"**.
5. Así, Traceroute identifica uno por uno los routers intermedios hasta llegar al destino final.

---

### 📦 ¿Cómo se instala Traceroute?

#### 🔸 En Linux (Ubuntu, Debian, Kali)

```bash
sudo apt update
sudo apt install traceroute -y
```

#### 🔸 En Windows

Ya viene preinstalado como `tracert`.

Para usarlo, solo abre **Símbolo del sistema (CMD)** y escribe:

```cmd
tracert google.com
```

#### 🔸 En macOS

También viene preinstalado.

Usa la terminal:

```bash
traceroute google.com
```

---

### ✅ Comandos básicos de Traceroute

| Sistema | Comando                     |
| ------- | --------------------------- |
| Linux   | `traceroute <IP o dominio>` |
| Windows | `tracert <IP o dominio>`    |
| macOS   | `traceroute <IP o dominio>` |

---

### 🧪 Ejemplo completo paso a paso

#### 🧰 Objetivo: Analizar la ruta hacia `google.com`

##### 🔸 En Linux o macOS

```bash
traceroute google.com
```

##### 🔸 En Windows (CMD)

```cmd
tracert google.com
```

---

#### 📋 Resultado esperado (resumen simplificado):

```bash
 1  192.168.1.1      1 ms    (tu router)
 2  10.125.0.1       5 ms    (proveedor local)
 3  200.48.225.1     8 ms    (ISP nacional)
 4  216.239.58.217  32 ms    (Google router)
 5  172.253.65.131  35 ms    (Servidor final en Google)
```

---

#### 🔍 ¿Cómo interpretar?

| Salto | IP             | Tiempo de respuesta | Significado               |
| ----- | -------------- | ------------------- | ------------------------- |
| 1     | 192.168.1.1    | 1 ms                | Tu router                 |
| 2     | 10.125.0.1     | 5 ms                | Salida de tu red local    |
| 3     | 200.48.x.x     | 8 ms                | ISP regional o nacional   |
| 4-5   | 216.x.x / 172. | 30-35 ms            | Infraestructura de Google |

Si algún salto aparece con `* * *`, puede significar:

- El router no responde a ICMP.
- Hay filtrado por firewall.
- Hay una caída o congestión en ese salto.

---

### 📈 Casos de uso reales

| Escenario                      | Cómo ayuda Traceroute                                                        |
| ------------------------------ | ---------------------------------------------------------------------------- |
| Tienes internet lento          | Identifica si el problema es en tu red o en tu ISP.                          |
| Problemas de acceso a un sitio | Muestra en qué salto se pierde la conexión.                                  |
| Diagnóstico de red             | Mide la latencia entre tú y varios destinos.                                 |
| Seguridad / OSINT              | Puedes ver rutas, proveedores, e incluso geolocalización de IPs intermedias. |

---

### 🧠 Consejos prácticos

- Si haces pruebas a distintos sitios (Google, Cloudflare, Amazon), puedes comparar las **rutas** y **tiempos**.
- Puedes exportar los resultados para analizarlos.
- En Linux, puedes añadir más opciones como:

  ```bash
  traceroute -n -w 2 google.com
  ```

  - `-n`: no resuelve nombres DNS (más rápido)
  - `-w`: tiempo de espera por salto en segundos

---

### 🛡️ Nota de seguridad

Traceroute **no es una herramienta maliciosa**, pero puede usarse en **reconocimiento de red (footprinting)** por atacantes para:

- Identificar la topología de la red objetivo.
- Ver dispositivos intermedios que podrían ser vulnerables.

Por eso, muchos firewalls corporativos bloquean o limitan respuestas ICMP de traceroute.

---

### ✅ Conclusión

- Traceroute es útil para **analizar problemas de red** y entender cómo viajan los datos.
- Es fácil de instalar y usar en cualquier sistema operativo.
- Con un análisis detallado, puedes detectar cuellos de botella o caídas.

---

[🔼](#índice)

---

## **929. Creación de perfiles de escaneo en Zenmap**

### 🧠 ¿Qué es Zenmap?

**Zenmap** es la interfaz gráfica oficial de **Nmap**, una de las herramientas más potentes para escaneo de redes. Zenmap facilita el uso de Nmap para usuarios que no están familiarizados con la terminal, permitiéndote:

- Ejecutar escaneos complejos con solo unos clics.
- Guardar perfiles personalizados de escaneo.
- Visualizar resultados de forma gráfica (puertos, hosts, servicios, etc.).
- Comparar escaneos anteriores.

---

### 🧰 ¿Qué es un perfil de escaneo?

Un **perfil de escaneo** en Zenmap es una **configuración predefinida** que puedes usar para realizar un tipo específico de escaneo sin tener que recordar los parámetros manualmente.

Por ejemplo:

- Escaneo completo TCP.
- Detección de sistema operativo.
- Detección de servicios.
- Escaneo de puertos específicos.

---

### 🧪 ¿Cómo se instala Zenmap?

#### 🔸 En Kali Linux

Ya viene preinstalado normalmente.

Si no está:

```bash
sudo apt update
sudo apt install zenmap -y
```

> ⚠️ Nota: En distribuciones nuevas, Zenmap fue descontinuado del repositorio oficial. Puedes instalarlo con `.deb` desde sitios alternativos o usar herramientas equivalentes como **Nmap + Nmap-GUI alternativas**.

#### 🔸 En Windows

1. Descarga desde:
   [https://nmap.org/download.html](https://nmap.org/download.html)

2. Instala el paquete completo (incluye Zenmap).

3. Ejecuta **Zenmap** desde el menú de inicio.

---

### ✅ Interfaz de Zenmap

Cuando abres Zenmap verás:

- **Target**: la IP o dominio a escanear.
- **Profile**: un menú desplegable con perfiles como:

  - Intense scan
  - Quick scan
  - OS detection

- **Command**: muestra el comando real que se ejecutará.
- **Output**: muestra los resultados del escaneo.
- **Topology / Ports / Host Details**: vistas gráficas del análisis.

---

### ✨ Cómo crear un perfil de escaneo personalizado

#### 🧾 Paso a paso:

1. **Abre Zenmap**.
2. En la parte superior, en el menú, haz clic en:
   `Profile > New Profile`
3. Aparecerá una ventana llamada **"Edit Scan Profile"**.

---

#### 🛠 Campos importantes:

- **Profile Name**: Dale un nombre como "Escaneo personalizado TCP".
- **Command**: Aquí colocas los parámetros Nmap, por ejemplo:

```bash
-sS -p 1-1000 -T4 -A
```

> Esto hace un escaneo SYN (rápido), de los puertos 1 al 1000, con velocidad alta (`-T4`) y detección avanzada de servicios/SO (`-A`).

- **Scan Technique**: Puedes seleccionar tipos como:

  - TCP Connect
  - SYN Stealth
  - UDP Scan

- **Target**: Puedes dejarlo vacío, ya que lo defines al lanzar el escaneo.
- **Timing Options**: Controla la velocidad del escaneo.

4. Cuando termines, haz clic en **Save Profile**.

---

### 🔁 Cómo usar tu nuevo perfil

1. En la ventana principal de Zenmap:

   - En **Target**, escribe una IP o dominio (ej: `scanme.nmap.org`).
   - En **Profile**, selecciona el perfil que creaste.

2. Haz clic en **Scan**.
3. Verás el resultado en tiempo real, incluyendo:

   - Puertos abiertos
   - Servicios detectados
   - Sistema operativo estimado
   - Hosts intermedios (si es el caso)

---

### 📋 Ejemplo completo

#### Objetivo: Escanear un servidor para conocer sus puertos, sistema operativo y servicios usando un perfil personalizado.

#### 1. Crear el perfil

Nombre: `Escaneo TCP completo`

Parámetros:

```bash
-sS -T4 -A -p 1-65535
```

#### 2. Escanear objetivo

Target:

```
scanme.nmap.org
```

Seleccionar el perfil `Escaneo TCP completo` y presionar **Scan**.

---

#### Resultado esperado:

En la pestaña **Ports/Hosts**, verás:

- Puerto 22/tcp abierto (servicio: SSH)
- Puerto 80/tcp abierto (servicio: HTTP)
- Información del sistema operativo (Linux estimado)
- Hostname: scanme.nmap.org

---

### 🔐 Advertencia ética

> Solo escanea dispositivos **que tú controlas o que te han dado permiso**. Escanear equipos sin autorización puede ser ilegal en muchos países.

---

### ✅ Conclusión

- Zenmap hace que el escaneo con Nmap sea accesible visualmente.
- Puedes crear perfiles para distintos tipos de análisis.
- Guardar perfiles te ahorra tiempo y reduce errores.
- Es ideal tanto para pentesters como para administradores de red.

---

[🔼](#índice)

---

## **930. Nmap Scripting Engine**

### 🧠 ¿Qué es el Nmap Scripting Engine (NSE)?

El **Nmap Scripting Engine (NSE)** permite usar **scripts escritos en Lua** para realizar tareas avanzadas durante un escaneo, como:

- Detección de vulnerabilidades.
- Enumeración de servicios.
- Extracción de información.
- Ataques básicos (fuerza bruta, explotación).

🔍 **Ejemplo de lo que puedes hacer:**

- Verificar si un sitio tiene login SSH vulnerable.
- Buscar servidores con Heartbleed.
- Detectar versiones desactualizadas de software.

---

### 🧰 ¿Cómo funciona?

Los scripts están ubicados en el directorio:

```
/usr/share/nmap/scripts/
```

Hay más de 600 scripts listos para usarse. Se agrupan por categorías como:

| Categoría NSE | Función                            |
| ------------- | ---------------------------------- |
| `auth`        | Autenticación (SSH, FTP, SMB)      |
| `vuln`        | Detecta vulnerabilidades conocidas |
| `discovery`   | Encuentra hosts y servicios        |
| `safe`        | Scripts seguros, no invasivos      |
| `intrusive`   | Pueden ser agresivos o detectables |

---

### 🛠️ ¿Cómo se instala Nmap y NSE?

#### 🔸 En Kali Linux o Ubuntu:

```bash
sudo apt update
sudo apt install nmap -y
```

NSE viene **incluido con Nmap**, no necesitas instalarlo por separado.

#### 🔸 Verifica los scripts disponibles:

```bash
ls /usr/share/nmap/scripts
```

---

### ✅ Comandos básicos para usar NSE

```bash
nmap --script <nombre_del_script> <objetivo>
```

#### 🔹 Ejemplo: Detectar vulnerabilidades HTTP

```bash
nmap --script=http-vuln-cve2014-3704 -p 80 192.168.1.10
```

---

### 🔎 Cómo buscar scripts específicos

```bash
locate *.nse | grep smb
```

o usa el siguiente comando para buscar por nombre:

```bash
nmap --script-help=http-enum
```

---

### 📋 Ejemplo completo paso a paso

#### Objetivo: Usar NSE para descubrir archivos y directorios en un servidor web

---

#### 🔶 Paso 1: Seleccionar el script

Usaremos el script `http-enum`, que enumera rutas comunes como `/admin`, `/login`, `/config`, etc.

---

#### 🔶 Paso 2: Elegir el objetivo

Usaremos un objetivo de prueba:

```
http://testphp.vulnweb.com
```

---

#### 🔶 Paso 3: Ejecutar el escaneo con NSE

```bash
nmap -p 80 --script=http-enum testphp.vulnweb.com
```

📌 Detalles del comando:

- `-p 80`: escanear solo el puerto 80 (HTTP)
- `--script=http-enum`: ejecutar el script de enumeración web

---

#### 🔶 Paso 4: Resultado esperado (resumen)

```bash
PORT   STATE SERVICE
80/tcp open  http
| http-enum:
|   /admin/: Admin login page
|   /includes/: Contains server files
|   /images/: Public image directory
|_  /login/: User login page
```

✅ Esto te muestra **rutas y recursos accesibles** que podrían ser interesantes en un análisis de seguridad o pentest.

---

### 💡 Otros scripts útiles con ejemplos

| Script NSE        | Comando                                | Función                              |
| ----------------- | -------------------------------------- | ------------------------------------ |
| `vulners`         | `--script vulners`                     | Detección de CVEs                    |
| `smb-enum-shares` | `--script smb-enum-shares -p 445 <ip>` | Enumerar recursos compartidos en SMB |
| `ftp-anon`        | `--script ftp-anon -p 21 <ip>`         | Detectar acceso anónimo a FTP        |
| `ssh-brute`       | `--script ssh-brute -p 22 <ip>`        | Fuerza bruta sobre SSH               |
| `dns-brute`       | `--script dns-brute <ip o dominio>`    | Enumeración de subdominios           |

---

### ⚙️ Cómo actualizar los scripts de Nmap

```bash
sudo nmap --script-updatedb
```

Esto actualiza la base de datos de scripts si agregas nuevos o actualizas Nmap.

---

### 🚨 Recomendaciones éticas

✅ **SIEMPRE**:

- Usa NSE con fines educativos, en entornos controlados o con permiso.
- Documenta cada acción durante pruebas de seguridad profesional.

🚫 **NUNCA**:

- Escanees sistemas que no te pertenecen sin autorización.

---

### 🧠 Conclusión

- **NSE** es una extensión poderosa de Nmap que convierte el escáner en una herramienta de auditoría completa.
- Puedes realizar tareas automatizadas de recolección, descubrimiento, análisis y explotación.
- Aprender a usar NSE amplía mucho tus capacidades en ciberseguridad ofensiva y defensiva.

---

[🔼](#índice)

---

## **931. Gobuster**

### 🔍 ¿Qué es Gobuster?

**Gobuster** es una herramienta de línea de comandos escrita en Go que sirve para **fuerza bruta de directorios, archivos y subdominios** en aplicaciones web.

Se usa mucho en **pentesting** y **reconocimiento web** para descubrir:

- Directorios ocultos (como `/admin`, `/login`, `/uploads`)
- Archivos sensibles (como `config.php`, `backup.zip`)
- Subdominios (como `admin.ejemplo.com`)

---

### 💡 ¿Por qué usar Gobuster?

- Es **rápido y eficiente**.
- Te permite **usar diccionarios personalizados**.
- Soporta **HTTP/HTTPS**, autenticación, proxy, cabeceras personalizadas, etc.
- Mucho más rápido que herramientas como **DirBuster** porque no usa interfaz gráfica.

---

### 🛠️ ¿Cómo instalar Gobuster?

#### 🔸 En Kali Linux o Debian/Ubuntu:

```bash
sudo apt update
sudo apt install gobuster -y
```

Verifica que se instaló correctamente:

```bash
gobuster -h
```

#### 🔸 En otras distribuciones (compilando desde Go):

Si tienes Go instalado:

```bash
go install github.com/OJ/gobuster/v3@latest
```

Luego añade el ejecutable a tu PATH:

```bash
export PATH=$PATH:$(go env GOPATH)/bin
```

---

### 🚀 Cómo usar Gobuster

La estructura básica del comando es:

```
gobuster dir -u URL -w lista.txt
```

Donde:

- `dir`: indica que vas a hacer **fuerza bruta de directorios/archivos**
- `-u`: es la URL del objetivo
- `-w`: es la ruta al **diccionario (wordlist)**

---

### 📘 Diccionarios recomendados

Puedes usar wordlists de **SecLists**:

```bash
sudo apt install seclists
```

Ruta común:

```
/usr/share/seclists/Discovery/Web-Content/common.txt
```

---

### ✅ Ejemplo completo paso a paso

#### 🎯 Objetivo: Descubrir rutas ocultas en un sitio web

---

#### 🔹 Paso 1: Escoger el sitio

Usaremos un sitio vulnerable de prueba:

```
http://testphp.vulnweb.com
```

---

#### 🔹 Paso 2: Elegir diccionario

Usaremos uno común:

```
/usr/share/seclists/Discovery/Web-Content/common.txt
```

---

#### 🔹 Paso 3: Ejecutar el escaneo

```bash
gobuster dir -u http://testphp.vulnweb.com -w /usr/share/seclists/Discovery/Web-Content/common.txt
```

---

#### 🔹 Resultado esperado:

```bash
===============================================================
Gobuster v3.6
===============================================================
[+] Url:                     http://testphp.vulnweb.com
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/seclists/Discovery/Web-Content/common.txt
===============================================================
/admin                (Status: 301)
/images               (Status: 301)
/includes             (Status: 301)
/login                (Status: 301)
/phpmyadmin           (Status: 403)
===============================================================
```

📌 Esto significa que encontró varias rutas interesantes como `/admin`, `/login`, etc.

---

### 🔧 Otros modos útiles

| Modo    | Uso                           |
| ------- | ----------------------------- |
| `dns`   | Enumerar subdominios          |
| `vhost` | Enumerar host virtuales       |
| `s3`    | Enumerar buckets de Amazon S3 |

---

#### 🎯 Ejemplo: Enumeración de subdominios

```bash
gobuster dns -d ejemplo.com -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt
```

Resultado:

```
Found: mail.ejemplo.com
Found: dev.ejemplo.com
Found: test.ejemplo.com
```

---

### 🧠 Consejos para usar Gobuster

- Usa el parámetro `-x` para buscar extensiones específicas:

```bash
gobuster dir -u http://example.com -w lista.txt -x php,html,txt
```

- Usa `-t` para ajustar la cantidad de hilos (más rápido):

```bash
gobuster dir -u http://example.com -w lista.txt -t 50
```

- Guarda el resultado en un archivo:

```bash
gobuster dir -u http://example.com -w lista.txt -o resultado.txt
```

---

### ⚠️ Ética y Legalidad

🔐 **Solo debes usar Gobuster con fines legales y educativos**, o con permiso del dueño del sistema.

---

### ✅ Conclusión

| Característica     | Detalle                                                    |
| ------------------ | ---------------------------------------------------------- |
| ¿Qué es?           | Herramienta de fuerza bruta para directorios y subdominios |
| ¿Cómo se instala?  | `sudo apt install gobuster`                                |
| ¿Para qué sirve?   | Descubrir rutas ocultas, archivos, subdominios             |
| ¿Ejemplo completo? | `gobuster dir -u http://testphp.vulnweb.com -w lista.txt`  |

---

[🔼](#índice)

---

## **932. Dumpster Diving**

### 🗑️ ¿Qué es Dumpster Diving?

**Dumpster Diving** en ciberseguridad es una técnica utilizada por **atacantes o pentesters** que consiste en **buscar información confidencial en la basura**, ya sea **física o digital**, para utilizarla en un ataque o reconocimiento.

En español se traduce como **"buzoneo"** o **"recolección de basura"**. El nombre proviene del hecho de que los atacantes **rebuscan en la basura de empresas o personas para encontrar datos útiles**.

---

### 🎯 ¿Qué tipo de información se busca?

Algunos ejemplos:

- Contraseñas escritas en papel
- Documentos impresos con datos bancarios o de clientes
- USBs o discos duros tirados
- Recibos de compras con datos personales
- Listados de empleados
- Post-its con contraseñas pegados a escritorios o monitores
- Equipos viejos sin formatear
- Routers, impresoras u otros dispositivos con configuraciones activas

---

### 🧠 ¿Por qué es importante?

Porque muchas veces **no protegemos bien la información física**, y eso puede ser una fuente muy valiosa para un atacante:

- **Fase de reconocimiento** en un ataque
- Para realizar **ingeniería social** más efectiva
- Robar **identidad o información sensible**

---

### 📦 ¿Cómo se puede prevenir?

Las organizaciones deben aplicar políticas de **seguridad física y manejo de la información**:

| Medida preventiva                   | Descripción                                                    |
| ----------------------------------- | -------------------------------------------------------------- |
| Trituradoras de papel               | Para destruir documentos sensibles antes de tirarlos           |
| Política de limpieza de escritorios | No dejar información escrita o dispositivos expuestos          |
| Etiquetado y destrucción de discos  | Borrar y destruir discos duros, USBs, CDs antes de desecharlos |
| Concientización                     | Entrenar a los empleados sobre los riesgos                     |
| Borrado seguro                      | Usar software de _wiping_ para eliminar datos de forma segura  |

---

### 🧪 ¿Cómo se "instala" o se hace?

No es una herramienta de software, pero si lo aplicas en **pruebas de penetración legales**, puedes simularlo así:

#### 🛠️ Herramientas comunes en pruebas:

- **Cámara o bloc de notas**: Para documentar hallazgos
- **Guantes**: Por higiene
- **Lámpara o linterna**: Si se inspecciona de noche o en contenedores
- **Bolsa o caja**: Para recolectar evidencias
- **Herramientas OSINT**: Para complementar datos encontrados

> ⚠️ **IMPORTANTE**: Solo se debe realizar con **permiso explícito**, ya que buscar en la basura de una empresa sin autorización puede ser ilegal.

---

### ✅ Ejemplo completo paso a paso (simulado y legal)

#### 🎯 Escenario: Red Team simula un ataque a una empresa con permiso

---

#### Paso 1: Reconocimiento físico

El equipo identifica los puntos de basura cerca del edificio de oficinas (contenedores traseros, reciclaje de papel, cajas de archivo).

---

#### Paso 2: Inspección

Encuentran:

- Varias hojas rotas a mano, pero completas

- Una hoja con el título: “Acceso remoto – VPN”

- Anotaciones con usuario y contraseña:
  `user123` / `Summer2024!`

- Un calendario de reuniones

- Un CD sin etiqueta

---

#### Paso 3: Análisis posterior

1. La contraseña encontrada es válida para el portal VPN.
2. El CD contiene archivos con nombres como `PlanContable_2023.xls`.
3. Las reuniones del calendario indican qué día estará fuera el jefe de seguridad.

---

#### Paso 4: Informe

Se documenta que la empresa:

- No destruye adecuadamente la información.
- Usa contraseñas impresas físicamente.
- Deja dispositivos sin formatear.

Se recomienda:

- Implementar trituradoras industriales.
- Capacitar al personal sobre eliminación segura.
- Crear un procedimiento de destrucción de medios digitales.

---

### 💬 Frases clave para recordar

| Concepto        | Significado                                                        |
| --------------- | ------------------------------------------------------------------ |
| Dumpster Diving | Técnica de buscar información útil en la basura (física o digital) |
| Fase del ataque | Reconocimiento                                                     |
| Prevención      | Concientización, destrucción segura de documentos y dispositivos   |
| Legalidad       | Solo debe realizarse con permiso (red team, pentesting autorizado) |

---

[🔼](#índice)

---

## **933. Ingeniería Social**

### 🧠 ¿Qué es la Ingeniería Social?

La **Ingeniería Social** es el arte de **engañar a personas** para que revelen información confidencial, realicen acciones peligrosas (como hacer clic en un enlace o abrir un archivo), o permitan acceso a sistemas protegidos.

En lugar de **atacar sistemas**, el atacante **manipula psicológicamente a los humanos**, que suelen ser el **eslabón más débil** en la seguridad.

---

### 🧩 ¿Qué se busca obtener?

- Contraseñas o credenciales
- Información personal o empresarial
- Acceso físico a instalaciones
- Control remoto de dispositivos
- Transferencias de dinero (caso de phishing a bancos)

---

### 📚 Tipos comunes de Ingeniería Social

| Técnica          | Explicación breve                                                             |
| ---------------- | ----------------------------------------------------------------------------- |
| **Phishing**     | Correos o mensajes falsos que simulan ser legítimos para robar información    |
| **Vishing**      | Llamadas telefónicas para engañar (ej: fingir ser soporte técnico o policía)  |
| **Smishing**     | Similar al phishing, pero por SMS o WhatsApp                                  |
| **Pretexting**   | Inventar una historia creíble para justificar una solicitud de información    |
| **Baiting**      | Dejar algo tentador (como un USB infectado) para que alguien lo use           |
| **Tailgating**   | Seguir físicamente a alguien autorizado para entrar en una instalación segura |
| **Quid pro quo** | Ofrecer algo a cambio de información (“te doy soporte si me das acceso”)      |

---

### 🔧 ¿Cómo se "instala"? (En sentido ético y práctico)

La Ingeniería Social **no requiere instalación de software**. Es una **habilidad**, y para aplicarla legalmente en **ciberseguridad** (por ejemplo, en pruebas de penetración éticas), se requiere:

1. **Permiso previo del objetivo** (como parte de un test de seguridad)
2. **Diseñar un escenario (pretexto)**: inventar una historia o identidad
3. **Usar canales reales**: email, teléfono, redes sociales, o presencial
4. **Obtener información clave**
5. **Reportar los hallazgos** con sugerencias de mitigación

---

### 🧠 Técnicas psicológicas comunes

| Técnica                | Ejemplo                                                                 |
| ---------------------- | ----------------------------------------------------------------------- |
| **Autoridad**          | Fingir ser un jefe o policía ("Soy del área de TI, dame tu clave")      |
| **Urgencia**           | Presionar con poco tiempo ("Necesito esto ahora o se caerá el sistema") |
| **Empatía / Simpatía** | Generar confianza ("Hola, yo también trabajo contigo en RRHH")          |
| **Recompensa**         | Prometer algo a cambio ("Participas en una encuesta y ganas un iPhone") |

---

### ✅ Ejemplo completo paso a paso (simulado)

#### 🎯 Escenario: Simulación de phishing a empleados de una empresa

---

#### 1. Recolección de información (OSINT)

- En LinkedIn, se identifica al jefe de sistemas: `Carlos Delgado – CTO en EmpresaXYZ`
- Se observa que usan correos `@empresaxyz.com` y Microsoft 365

---

#### 2. Creación del pretexto

El atacante crea un correo falso que simula ser de Microsoft:

> **Asunto**: "Actualización urgente de seguridad - Cuenta bloqueada"
>
> **Contenido**: “Su cuenta `carlos.delgado@empresaxyz.com` ha sido comprometida.
>
> Ingrese inmediatamente a \[login-seguro365.com] para verificar su identidad.”

---

#### 3. Lanzamiento del ataque

El correo se envía masivamente a 10 empleados con correos similares.

---

#### 4. Resultado (simulado)

- 3 empleados hacen clic en el enlace.
- 1 de ellos ingresa su usuario y contraseña en el sitio falso.

---

#### 5. Reporte

En el informe de la prueba se concluye:

- El sistema no tiene filtro de correo malicioso (phishing).
- Los empleados no están capacitados en ciberseguridad básica.
- No se usa autenticación multifactor (MFA).

---

### 🛡️ ¿Cómo se previene?

| Medida de defensa                  | Ejemplo práctico                                                    |
| ---------------------------------- | ------------------------------------------------------------------- |
| Capacitación constante al personal | Simulacros de phishing, talleres de concienciación                  |
| Verificación en dos pasos (MFA)    | Aunque roben la contraseña, no podrán acceder sin el segundo factor |
| Filtros antispam y antiphishing    | Bloquean correos sospechosos antes de llegar al usuario             |
| Políticas de seguridad internas    | "Nunca dar tu clave por correo o llamada"                           |
| Simulación de ataques éticos       | Pentesting con escenarios de Ingeniería Social autorizados          |

---

### 🧠 Frase clave para recordar

> “La seguridad no solo depende de firewalls o antivirus… también depende de las personas.”

---

[🔼](#índice)

---

## **934. Nmap**

### 🛠️ ¿Qué es Nmap?

**Nmap** (Network Mapper) es una herramienta **de código abierto** usada para:

- Descubrir dispositivos en una red
- Detectar puertos abiertos
- Identificar servicios y versiones
- Detectar sistemas operativos
- Hacer pruebas de seguridad (auditorías)

👉 Nmap es una herramienta esencial para **pentesters, administradores de red** y profesionales de **ciberseguridad**.

---

### 🎯 ¿Para qué sirve? (Con ejemplos simples)

| Uso de Nmap                       | Ejemplo práctico                                   |
| --------------------------------- | -------------------------------------------------- |
| Descubrir dispositivos en una red | Ver qué equipos están conectados a una red local   |
| Escanear puertos abiertos         | Detectar si un servidor tiene abierto el puerto 22 |
| Ver qué servicios están corriendo | Identificar si hay un servidor web en el puerto 80 |
| Detectar sistema operativo        | Saber si una máquina usa Windows o Linux           |
| Automatizar escaneos              | Hacer scripts para escaneos masivos o periódicos   |

---

### 💻 ¿Cómo se instala?

#### 🔹 En **Kali Linux** o sistemas basados en Debian/Ubuntu:

Ya viene preinstalado. Si no, puedes instalarlo así:

```bash
sudo apt update
sudo apt install nmap
```

#### 🔹 En **Windows**:

1. Ve al sitio oficial: [https://nmap.org/download.html](https://nmap.org/download.html)
2. Descarga el instalador de Nmap para Windows
3. Ejecuta el instalador (incluye **Zenmap**, la interfaz gráfica opcional)
4. Asegúrate de marcar la casilla para añadir Nmap al `PATH`

---

### 🧪 Comandos básicos (fáciles de entender)

| Comando Nmap                    | ¿Qué hace?                                            |
| ------------------------------- | ----------------------------------------------------- |
| `nmap 192.168.1.1`              | Escaneo básico de un host                             |
| `nmap -sS 192.168.1.1`          | Escaneo stealth (SYN scan)                            |
| `nmap -p 22,80,443 192.168.1.1` | Escanea puertos específicos                           |
| `nmap -p- 192.168.1.1`          | Escanea todos los 65535 puertos                       |
| `nmap -O 192.168.1.1`           | Intenta detectar el sistema operativo                 |
| `nmap -sV 192.168.1.1`          | Detecta versiones de servicios                        |
| `nmap -A 192.168.1.1`           | Escaneo agresivo (SO, servicios, traceroute, scripts) |
| `nmap -iL lista.txt`            | Escanea múltiples IPs desde un archivo                |

---

### 📦 Ejemplo completo paso a paso

#### 🎯 Escenario:

Quiero analizar un equipo en mi red local (`192.168.1.10`) para:

- Saber si está encendido
- Qué puertos tiene abiertos
- Qué sistema operativo usa

---

#### ✅ Paso 1: Verificar si responde

```bash
nmap -sn 192.168.1.10
```

**Salida esperada:**

```txt
Nmap scan report for 192.168.1.10
Host is up (0.0010s latency).
```

---

#### ✅ Paso 2: Ver puertos abiertos y servicios

```bash
nmap -sV 192.168.1.10
```

**Salida esperada (ejemplo):**

```txt
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 8.2
80/tcp   open  http    Apache httpd 2.4.41
```

---

#### ✅ Paso 3: Detectar sistema operativo

```bash
sudo nmap -O 192.168.1.10
```

**Salida esperada (ejemplo):**

```txt
Running: Linux 5.X
OS details: Linux 5.4 - 5.10
```

---

#### ✅ Paso 4: Escaneo agresivo completo

```bash
sudo nmap -A 192.168.1.10
```

Esto hará un escaneo profundo con servicios, sistema operativo, scripts y traceroute.

---

### 🧠 Consejos importantes

- Usa `sudo` para mejores resultados (necesario para OS detection)
- No escanees redes que **no te pertenecen** sin permiso — puede ser ilegal
- Usa `-T4` para que el escaneo sea más rápido (aunque más ruidoso)
- Guarda resultados con `-oN` (normal), `-oX` (XML), `-oG` (grepable)

```bash
nmap -sV -oN resultado.txt 192.168.1.10
```

---

### 🔐 Nmap en ciberseguridad

Nmap es vital para:

- Reconocimiento en pentesting (fase de enumeración)
- Evaluar vulnerabilidades (junto a scripts NSE)
- Comprobar exposición de puertos y servicios
- Validar configuraciones de red

---

[🔼](#índice)

---

## **935. Joomscan**

### 🧠 ¿Qué es JoomScan?

**JoomScan** es una herramienta de **auditoría de seguridad para sitios web que usan Joomla**. Está escrita en Perl y es desarrollada por **OWASP**. Permite detectar:

- Versiones vulnerables de Joomla
- Vulnerabilidades comunes (LFI, SQLi, RFI, XSS, etc.)
- Componentes y módulos vulnerables
- Archivos de respaldo o instalación expuestos
- Configuraciones inseguras

🔐 Es muy útil para pentesters y profesionales de ciberseguridad que realizan **pruebas de seguridad web**.

---

### 📌 ¿Qué necesitas para usar JoomScan?

- Sistema basado en Linux (aunque también se puede correr en Windows con Perl)
- Tener instalado **Perl**
- Tener **git** (para clonar el repositorio)
- Conexión a Internet para escanear sitios

---

### 💻 ¿Cómo se instala JoomScan?

#### 🔸 En Kali Linux (¡ya viene instalado!)

Solo escribe:

```bash
joomscan
```

Si no está instalado:

#### 🔸 En cualquier sistema Linux (Debian, Ubuntu, Kali, Parrot, etc.)

##### 1. Instalar dependencias (si no las tienes):

```bash
sudo apt update
sudo apt install git perl libwww-perl
```

##### 2. Clonar el repositorio oficial:

```bash
git clone https://github.com/OWASP/joomscan.git
cd joomscan
```

##### 3. Ejecutar JoomScan:

```bash
perl joomscan.pl
```

¡Listo! Ya puedes empezar a escanear.

---

### 🧪 Comandos básicos de JoomScan

| Comando                                 | ¿Qué hace?                                     |
| --------------------------------------- | ---------------------------------------------- |
| `perl joomscan.pl`                      | Muestra menú interactivo                       |
| `perl joomscan.pl -u https://sitio.com` | Escanea directamente ese sitio Joomla          |
| `perl joomscan.pl --help`               | Muestra ayuda de comandos                      |
| `perl joomscan.pl -update`              | Actualiza la base de datos de vulnerabilidades |

---

### 🧪 Ejemplo completo paso a paso

#### 🎯 Escenario: Escanear un sitio web Joomla

Supongamos que queremos auditar:

```
https://demo.testjoomlasite.com
```

#### ✅ Paso 1: Entramos a la carpeta de JoomScan

```bash
cd joomscan
```

#### ✅ Paso 2: Ejecutamos el escaneo

```bash
perl joomscan.pl -u https://demo.testjoomlasite.com
```

#### ✅ Paso 3: Análisis de la salida

La salida incluirá:

- **Versión de Joomla detectada** (ej. Joomla 3.9.0)
- **Componentes encontrados** (ej. com_content, com_users)
- **Vulnerabilidades conocidas** si existen para esa versión
- **Recomendaciones** de seguridad
- Archivos como `/administrator/` o `/installation/` si están expuestos

---

### 📄 Ejemplo de salida simplificada

```txt
Target : https://demo.testjoomlasite.com

[+] Detecting Joomla version...
    Joomla 3.9.0 detected

[+] Checking for common vulnerabilities...
    [+] com_users - Found
    [+] com_content - Found
    [+] Vulnerable version of Joomla detected! [CVE-2019-11847]

[+] Checking for exposed admin panel...
    /administrator/ - Found!

[+] Recommendations:
    - Update to latest Joomla version
    - Restrict access to /administrator/
```

---

### 🧠 ¿Cuándo usar JoomScan?

- Durante una auditoría web donde sabes o sospechas que el sitio usa Joomla.
- Para ver qué componentes Joomla están expuestos.
- Para encontrar vulnerabilidades específicas de Joomla.
- Como parte del **reconocimiento pasivo y activo** en un test de penetración.

---

### ⚠️ Advertencia ética

> 🔒 **Nunca escanees un sitio web sin autorización**. El escaneo sin permiso es ilegal en muchos países y puede tener consecuencias legales. Úsalo solo con sitios de prueba o con autorización explícita.

---

### ✅ Resumen rápido

| Elemento             | Detalle                            |
| -------------------- | ---------------------------------- |
| 🧩 Herramienta       | JoomScan                           |
| 🔧 Instalación       | `git clone`, ejecutar con Perl     |
| 🛠️ Función principal | Auditar sitios web Joomla          |
| 📊 Detecta           | Versión, módulos, vulnerabilidades |
| 🔐 Usado en          | Pentesting web, análisis de CMS    |

---

[🔼](#índice)

---

## **936. Wpscan**

### 🧠 ¿Qué es WPScan?

**WPScan** es una herramienta de código abierto diseñada para **detectar vulnerabilidades en sitios web que usan WordPress**. Fue creada por la comunidad de seguridad y hoy la mantiene **Automattic** (los creadores de WordPress.com).

WPScan **no solo detecta vulnerabilidades**, también te muestra:

- Versión de WordPress
- Plugins instalados (y si son vulnerables)
- Temas (themes) usados
- Usuarios (usernames) públicos
- Archivos sensibles expuestos

---

### 💡 ¿Por qué usar WPScan?

Porque más del 40% de los sitios web del mundo usan WordPress. Muchos de ellos están mal configurados, desactualizados o tienen plugins inseguros. WPScan te permite **detectar esas fallas antes de que un atacante lo haga**.

---

### 🧰 ¿Qué necesitas para usar WPScan?

- Tener instalado **Linux o WSL** (aunque también funciona en macOS o Windows usando Docker)
- Tener **Ruby** (lenguaje en que está hecho WPScan)
- Tener **una clave API de WPScan** (gratuita para escaneos simples)

---

### 📥 Instalación de WPScan (paso a paso)

#### ✅ Opción 1: En Kali Linux (recomendado)

WPScan **ya viene preinstalado** en Kali. Solo verifica:

```bash
wpscan --help
```

Si no lo tienes, instálalo con:

```bash
sudo apt update
sudo apt install wpscan
```

#### ✅ Opción 2: En Ubuntu u otra distro

1. Instala Ruby y dependencias:

```bash
sudo apt update
sudo apt install ruby ruby-dev libcurl4-openssl-dev make
```

2. Instala WPScan:

```bash
sudo gem install wpscan
```

3. Verifica que funciona:

```bash
wpscan --version
```

---

### 🔑 Obtener una API KEY de WPScan

WPScan usa una **clave API gratuita** para acceder a su base de datos de vulnerabilidades.

1. Ve a: [https://wpscan.com](https://wpscan.com)
2. Regístrate y entra a tu cuenta
3. Copia tu API Key desde tu perfil

Luego puedes usarla así:

```bash
wpscan --api-token TU_API_KEY
```

---

### 🔍 Comandos más usados de WPScan

| Comando                            | ¿Qué hace?                               |
| ---------------------------------- | ---------------------------------------- |
| `wpscan --url https://ejemplo.com` | Escanea el sitio completo                |
| `--enumerate u`                    | Enumera usuarios                         |
| `--enumerate p`                    | Enumera plugins                          |
| `--enumerate t`                    | Enumera temas                            |
| `--api-token`                      | Añade tu token de acceso                 |
| `--disable-tls-checks`             | Evita errores por certificados inválidos |
| `--output salida.txt`              | Guarda los resultados en un archivo      |

---

### 🧪 Ejemplo completo paso a paso

#### 🎯 Escenario:

Supongamos que tienes este sitio WordPress para pruebas:

```
https://www.testwordpress.local
```

#### ✅ Paso 1: Escaneo básico

```bash
wpscan --url https://www.testwordpress.local --api-token TU_API_KEY
```

Esto detectará:

- Versión de WordPress
- Plugins activos y si son vulnerables
- Temas instalados
- Archivos como `readme.html`, `wp-config.php~`, etc.

#### ✅ Paso 2: Enumerar usuarios

```bash
wpscan --url https://www.testwordpress.local -e u --api-token TU_API_KEY
```

Esto intenta adivinar usuarios públicos como `admin`, `editor`, `juan`, etc.

#### ✅ Paso 3: Escaneo completo

```bash
wpscan --url https://www.testwordpress.local -e at --api-token TU_API_KEY
```

Esto enumera:

- `a` = plugins, temas, usuarios, etc.
- `t` = temas
- `u` = usuarios

Puedes usar `-e ap` para solo plugins, o `-e at` para temas.

#### ✅ Paso 4: Guardar resultados

```bash
wpscan --url https://www.testwordpress.local --api-token TU_API_KEY --output reporte.txt
```

---

### 📄 Ejemplo de salida (resumen)

```txt
Target URL: https://www.testwordpress.local

WordPress version: 5.7.2 (outdated)
  - Found by: Meta Generator Tag
  - [!] Vulnerability: CVE-2021-29447

Enumerating plugins:
  - contact-form-7 v5.1.6
    - [!] Vulnerability: Unauthenticated file upload (CVE-2020-35489)

Enumerating users:
  - admin (ID: 1)
  - juan (ID: 2)

[+] Recommendations:
  - Update WordPress to the latest version
  - Update vulnerable plugins
  - Restrict access to wp-admin
```

---

### 🔐 Consejos de seguridad

- Nunca hagas escaneos sin autorización.
- WPScan no realiza explotación, solo reconocimiento.
- Combina WPScan con herramientas como Burp Suite o Nmap para auditorías más completas.

---

### ✅ RESUMEN RÁPIDO

| Elemento        | Detalle                                       |
| --------------- | --------------------------------------------- |
| 🧩 Herramienta  | WPScan                                        |
| 🔧 Instalación  | `sudo gem install wpscan`                     |
| 🔍 Función      | Auditar WordPress: versión, plugins, usuarios |
| 🔑 API Key      | Requiere registrarte en wpscan.com            |
| 🧪 Uso práctico | `wpscan --url https://web.com --api-token`    |

---

[🔼](#índice)

---

## **937. Nessus Essentials**

### 🧠 ¿Qué es Nessus Essentials?

**Nessus Essentials** es una versión gratuita del escáner de vulnerabilidades **Nessus**, desarrollado por **Tenable**. Está diseñado para ayudar a **analistas de seguridad, estudiantes y profesionales** a escanear redes y sistemas en busca de vulnerabilidades conocidas, configuraciones incorrectas, parches faltantes, puertos abiertos, etc.

Es ideal para:

- Pentesters en fase de reconocimiento
- Administradores de redes
- Prácticas en ciberseguridad
- Preparación para certificaciones como CompTIA Security+, OSCP, CEH

---

### 🛠️ ¿Qué puede detectar Nessus Essentials?

- Puertos abiertos
- Software desactualizado
- Malware conocido
- Fallos de configuración
- Contraseñas débiles
- Vulnerabilidades con CVE
- Fallas en SSL/TLS, FTP, SSH, DNS, etc.

---

### 💡 ¿Qué lo diferencia de otras herramientas?

A diferencia de herramientas como **Nmap** o **OpenVAS**, Nessus ofrece:

✅ Reportes visuales

✅ Recomendaciones de corrección

✅ Detecta miles de CVEs actualizados

✅ Interfaz web sencilla

✅ Escaneos automáticos

---

### 📥 ¿Cómo instalar Nessus Essentials?

#### 📌 Requisitos

- Windows 10/11, macOS, o Linux (Kali, Ubuntu, Debian, etc.)
- 2 GB de RAM mínimo
- Conexión a Internet (para registrar la licencia gratuita)

---

#### 🔽 Paso 1: Descargar Nessus

1. Ve a: [https://www.tenable.com/products/nessus/nessus-essentials](https://www.tenable.com/products/nessus/nessus-essentials)
2. Haz clic en **“Download”**
3. Selecciona **Nessus Essentials**
4. Elige tu sistema operativo (Windows, Linux o Mac)
5. Introduce tu correo electrónico
6. Te llegará una **clave de activación** (API key gratuita)

---

#### 🖥️ Paso 2: Instalar en Linux (ejemplo: Kali)

```bash
wget https://www.tenable.com/downloads/api/v1/public/pages/nessus/downloads/XXXXXXXX/download?i_agree_to_tenable_license_agreement=true -O nessus.deb
sudo dpkg -i nessus.deb
sudo systemctl start nessusd
```

En Windows o Mac basta con ejecutar el instalador `.exe` o `.dmg`.

---

#### 🌐 Paso 3: Acceder a la interfaz web

Luego de instalar y arrancar el servicio:

1. Abre tu navegador y visita:

```
https://localhost:8834
```

2. Aparecerá la pantalla de configuración:

   - Crea una cuenta local (usuario y contraseña)
   - Introduce la clave de activación
   - Espera que descargue y configure los plugins (tarda unos minutos)

---

### 🧪 ¿Cómo se usa Nessus Essentials?

Una vez dentro de la interfaz web:

#### ✅ Paso 1: Crear un nuevo escaneo

1. Haz clic en **"New Scan"**
2. Elige un tipo de escaneo, por ejemplo:

   - **Basic Network Scan** (el más común)

3. Nombra tu escaneo y pon la IP o dominio objetivo
4. Guarda y luego haz clic en **"Launch"**

---

#### ✅ Paso 2: Espera los resultados

Dependiendo del tamaño de la red o sistema, puede demorar entre 2 y 15 minutos.

Te mostrará:

| Elemento             | Ejemplo                            |
| -------------------- | ---------------------------------- |
| Vulnerabilidad alta  | OpenSSH 7.2 con CVE-2018-15473     |
| Vulnerabilidad media | Apache desactualizado              |
| Configuración débil  | FTP sin autenticación segura       |
| Recomendaciones      | Actualiza OpenSSH a la versión 8.0 |

---

#### ✅ Paso 3: Ver resultados

Puedes hacer clic en cada hallazgo para ver:

- Descripción del problema
- CVE asociado
- Nivel de riesgo (bajo, medio, alto, crítico)
- Solución sugerida
- A qué puerto y servicio afecta

---

#### ✅ Paso 4: Exportar reportes

Puedes exportar en PDF, CSV, HTML para compartirlo o documentarlo:

1. Entra al escaneo → clic en “Export”
2. Elige formato
3. Guarda el archivo

---

### 📄 Ejemplo completo (escaneo de una IP local)

#### 🎯 Objetivo: Escanear el sistema con IP `192.168.1.10`

1. Inicia Nessus en el navegador: `https://localhost:8834`
2. Crea un escaneo:

   - Nombre: `Escaneo Red Local`
   - IP objetivo: `192.168.1.10`
   - Tipo: `Basic Network Scan`

3. Haz clic en **Launch**
4. Espera el análisis
5. Resultado:

| Vulnerabilidad | Riesgo | Servicio | Solución                        |
| -------------- | ------ | -------- | ------------------------------- |
| CVE-2021-3156  | Alta   | sudo     | Actualiza sudo a 1.9.5p2+       |
| SSH sin banner | Media  | SSH      | Configura banner en sshd_config |
| Puertos SMB    | Baja   | SMB      | Restringe acceso por firewall   |

6. Exporta el reporte en PDF

---

### 🧩 Resumen

| Elemento          | Detalles                                                                   |
| ----------------- | -------------------------------------------------------------------------- |
| 🛠️ Herramienta    | Nessus Essentials (de Tenable)                                             |
| 🎯 Objetivo       | Detectar vulnerabilidades, puertos abiertos y software inseguro            |
| 💾 Instalación    | Descarga desde el sitio oficial según tu sistema operativo                 |
| 🌐 Interfaz       | Web en `https://localhost:8834`                                            |
| 🧪 Ejemplo de uso | Escaneo de IP o dominio, reporte detallado, recomendación de solución      |
| 💡 Ideal para     | Pentesting, auditoría de redes, prácticas de estudiantes de ciberseguridad |

---

[🔼](#índice)

---

## **938. Vega**

### 🧠 ¿Qué es Vega?

**Vega** es una herramienta **gratuita y de código abierto** para realizar pruebas de seguridad en **aplicaciones web**. Fue desarrollada en Java por la empresa **Subgraph**.

Te permite escanear sitios web en busca de vulnerabilidades comunes como:

- **XSS (Cross Site Scripting)**
- **SQL Injection**
- **Inyecciones en encabezados**
- **Exposición de archivos**
- **Fuga de información en cookies**
- **Links y recursos inseguros**
- ¡Y más!

> 🧪 Ideal para quienes se están iniciando en **pentesting web**, **bug bounty** o **auditorías de seguridad**.

---

### 💡 ¿Qué puedes hacer con Vega?

- Escanear automáticamente un sitio web en busca de vulnerabilidades
- Interceptar peticiones con su **proxy**
- Repetir y modificar peticiones
- Ver cabeceras, cookies y respuestas del servidor
- Ver vulnerabilidades con explicación y sugerencias

---

### 🖥️ Requisitos para usar Vega

- Sistema operativo: **Windows, Linux o macOS**
- Tener **Java** instalado (Java Runtime Environment 1.8 o superior)
- Se recomienda al menos 2 GB de RAM

---

### 🔽 ¿Cómo instalar Vega?

#### 🔸 Paso 1: Descargar Vega

1. Visita: [https://subgraph.com/vega/](https://subgraph.com/vega/)
2. Ve a la sección de **descargas**
3. Elige tu sistema operativo:

   - Windows → `vega-win32.win32.x86_64.zip`
   - Linux → `vega-linux.gtk.x86_64.tar.gz`

---

#### 🔸 Paso 2: Instalar Java

Si no tienes Java:

##### En Windows:

1. Ve a: [https://www.java.com/es/download/](https://www.java.com/es/download/)
2. Descarga e instala el **JRE (Java Runtime Environment)**

##### En Kali Linux:

```bash
sudo apt update
sudo apt install default-jre -y
```

---

#### 🔸 Paso 3: Ejecutar Vega

##### En Windows:

1. Extrae el `.zip` descargado
2. Entra a la carpeta y haz doble clic en `Vega.exe`

##### En Linux:

1. Extrae el `.tar.gz`

```bash
tar -xvf vega-linux.gtk.x86_64.tar.gz
cd vega
./vega
```

---

### 🌐 Interfaz de Vega

Cuando abras Vega verás tres zonas principales:

| Zona               | Función principal                                       |
| ------------------ | ------------------------------------------------------- |
| Escaneo automático | Para buscar vulnerabilidades                            |
| Proxy              | Interceptar tráfico web                                 |
| Request/Response   | Ver peticiones/respuestas HTTP de cada escaneo o ataque |

---

### 🧪 ¿Cómo usar Vega? (Paso a paso con ejemplo completo)

#### 🎯 Escenario: Escanear un sitio de pruebas

Vamos a usar el sitio **demo.testfire.net**, una web vulnerable para practicar.

---

#### ✅ Paso 1: Crear un nuevo escaneo

1. Abre Vega
2. Ve a: **Scan → New Scan**
3. En el campo "Target", pon:

   ```
   http://demo.testfire.net
   ```

4. Marca “Use a crawler” y “Use modules”
5. En la siguiente pantalla deja todos los módulos seleccionados (XSS, SQLi, etc.)
6. Clic en **Finish**

---

#### ✅ Paso 2: Esperar resultados

Vega comenzará a rastrear el sitio, enviando peticiones y buscando vulnerabilidades.

Verás que aparecen en tiempo real en la pestaña izquierda bajo la lista de escaneos activos.

---

#### ✅ Paso 3: Analizar resultados

Ejemplo de resultados:

| Vulnerabilidad detectada      | Descripción                                          | Sugerencia                    |
| ----------------------------- | ---------------------------------------------------- | ----------------------------- |
| Reflected XSS                 | Parámetro `search` refleja entrada sin sanitizar     | Escapar caracteres peligrosos |
| SQL Injection                 | Parámetro `user` responde con error de base de datos | Usar consultas preparadas     |
| Información sensible expuesta | Cookie contiene `JSESSIONID` sin atributo `HttpOnly` | Marcar cookie como HttpOnly   |

Puedes hacer clic en cada hallazgo y ver:

- Descripción técnica
- Severidad
- Reproducción manual
- Cabeceras HTTP involucradas

---

#### ✅ Paso 4: Exportar resultados (opcional)

Vega no tiene opción directa de exportar a PDF, pero puedes:

- Copiar los resultados manualmente
- Tomar capturas de pantalla
- Exportar logs desde la pestaña de tráfico

---

### 📄 Ejemplo completo

#### 🔍 Objetivo:

Detectar vulnerabilidades en `http://demo.testfire.net`

#### 👣 Pasos:

1. Instalar Java y descargar Vega
2. Ejecutar Vega
3. Crear nuevo escaneo a `http://demo.testfire.net`
4. Seleccionar todos los módulos de vulnerabilidad
5. Correr escaneo
6. Revisar resultados:

```
- Reflected XSS in search
- SQLi in login
- Cookie HttpOnly missing
```

7. Analizar qué parámetro está vulnerable y cómo explotarlo (Vega te muestra cómo)
8. Anotar los hallazgos o probarlos en navegador con Burp Suite o manualmente

---

### 🧩 Conclusión

| Elemento           | Descripción                                                  |
| ------------------ | ------------------------------------------------------------ |
| 🛠️ Herramienta     | Vega                                                         |
| 🎯 Propósito       | Escanear vulnerabilidades web como XSS, SQLi, cookies, etc.  |
| 💾 Instalación     | Descargar + Java Runtime + Ejecutar (sin instalación formal) |
| 🧪 Funciones clave | Crawler, escaneo, análisis de tráfico, proxy interceptador   |
| 📊 Reportes        | Listado interno en pestañas, exportación manual              |
| 👤 Ideal para      | Estudiantes, pentesters junior, bug bounty hunters           |

---

[🔼](#índice)

---

| **Inicio**         | **atrás 14**                                        | **Siguiente 16**                                  |
| ------------------ | --------------------------------------------------- | ------------------------------------------------- |
| [🏠](../README.md) | [⏪](./7_14_Inteligencia_para_la_Ciberseguridad.md) | [⏩](./7_16_Hacking_Pentesting_con_Metasploit.md) |
