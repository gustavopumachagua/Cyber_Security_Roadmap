| **Inicio**         | **atrás 1**                                                        | **Siguiente 3**                                        |
| ------------------ | ------------------------------------------------------------------ | ------------------------------------------------------ |
| [🏠](../README.md) | [⏪](./2_1_introduccion_al_hacking_etico_y_penetration_testing.md) | [⏩](./2_3_Recopilacion_semi_pasiva_de_informacion.md) |

---

## **Índice**

| Temario                                                                                                              |
| -------------------------------------------------------------------------------------------------------------------- |
| [3. Introducción a la fase de Recopilación de Información](#3-introducción-a-la-fase-de-recopilación-de-información) |
| [4. Recopilación pasiva de información](#4-recopilación-pasiva-de-información)                                       |
| [5. Hacking con buscadores: Google Hacking](#5-hacking-con-buscadores-google-hacking)                                |
| [6. Google Hacking Database](#6-google-hacking-database)                                                             |
| [7. Google Hacking: Comandos y Operadores Booleanos](#7-google-hacking-comandos-y-operadores-booleanos)              |
| [8. Shodan](#8-shodan)                                                                                               |
| [9. Shodan: Comandos principales](#9-shodan-comandos-principales)                                                    |
| [10. Censys](#10-censys)                                                                                             |
| [11. Whois](#11-whois)                                                                                               |
| [12. Archive: Análisis de información histórica](#12-archive-análisis-de-información-histórica)                      |
| [13. TheHarvester](#13-theharvester)                                                                                 |
| [14. Bloqueo temporal de dirección IP pública](#14-bloqueo-temporal-de-dirección-ip-pública)                         |
| [15. Maltego](#15-maltego)                                                                                           |
| [16. Recon-ng](#16-recon-ng)                                                                                         |

---

# **Recopilacion pasiva de informacion**

## **3. Introducción a la fase de Recopilación de Información**

### ¿Qué es la fase de recopilación de información?

Es **la primera etapa de un test de penetración o hacking ético**.

👉 Su objetivo es **conseguir la mayor cantidad de información posible sobre el objetivo**, para planificar los siguientes pasos del ataque o evaluación.

Es como **ser un detective**: buscas pistas que te ayuden a entender cómo atacar o proteger mejor un sistema.

---

### ¿Por qué es importante?

📌 Porque **entre más sepas de tu objetivo**, más fácil será:

- Encontrar vulnerabilidades.
- Elegir herramientas adecuadas.
- Simular ataques realistas.

Piensa que es **la base del ataque o la auditoría**: si falla, el resto también será débil.

---

### Tipos de recopilación de información

**A. Pasiva**
✅ Obtenemos información **sin interactuar directamente con el objetivo**.
✅ Ejemplo: Buscar en Google, redes sociales.

**B. Activa**
✅ Interactuamos directamente con el objetivo.
✅ Ejemplo: Hacer ping, escanear puertos.

Ambas son importantes en hacking ético.

---

### Ejemplo fácil de entender

**Imagina** que eres un pentester contratado para evaluar `empresa.com`.

#### ➜ 📌 Recopilación PASIVA

✅ Buscas en Google:

```
"empresa.com confidential"
"site:empresa.com filetype:pdf"
```

✅ Resultado:

- Encuentras un PDF con organigrama interno.
  ✅ Impacto:
- Nombres reales de empleados para phishing.

---

✅ Buscas en LinkedIn:

- Empleados de la empresa.
- Sus roles (como "Administrador de TI").

✅ Impacto:

- Preparas un ataque de ingeniería social (correos falsos muy creíbles).

---

✅ Whois:

```
whois empresa.com
```

✅ Resultado:

- Contacto del administrador del dominio.
- Servidores de nombres.

✅ Impacto:

- Datos para ataques dirigidos.

---

✅ Buscas subdominios con crt.sh:

```
crt.sh/?q=%25.empresa.com
```

✅ Resultado:

- api.empresa.com
- dev.empresa.com

✅ Impacto:

- Dev suele tener menos seguridad.

---

#### ➜ 📌 Recopilación ACTIVA

✅ Escaneo simple con **ping**:

```
ping empresa.com
```

✅ Resultado:

- Responde → servidor activo.

✅ Escaneo de puertos con Nmap:

```
nmap empresa.com
```

✅ Resultado:

- Puerto 80 (HTTP) abierto.
- Puerto 443 (HTTPS) abierto.
- Puerto 22 (SSH) abierto.

✅ Impacto:

- Se puede investigar la versión del servidor web o intentar fuerza bruta en SSH.

---

✅ Banner Grabbing:

```
nc empresa.com 80
GET / HTTP/1.1
```

✅ Resultado:

- “Server: Apache/2.4.29 (Ubuntu)”

✅ Impacto:

- Sabes la versión → puedes buscar vulnerabilidades conocidas.

---

### Herramientas típicas

📌 Para PASIVA:

- Google Dorks
- Whois
- Maltego
- crt.sh
- Shodan

📌 Para ACTIVA:

- Nmap
- Netcat
- Recon-ng
- Dig / nslookup
- Dirbuster / Gobuster

---

### Resultados típicos que buscas

✅ Subdominios ocultos
✅ Direcciones IP
✅ Correos electrónicos del personal
✅ Tecnologías usadas (Apache, Nginx, etc.)
✅ Sistemas operativos
✅ Empleados y sus roles
✅ Documentos públicos mal configurados
✅ Vulnerabilidades conocidas del software usado

---

### Ejemplo práctico resumido paso a paso

🎯 Objetivo: `tiendaonline.com`

✅ PASIVA:

- Google: `site:tiendaonline.com filetype:pdf`
  ➜ Encuentras un manual interno.

- Whois:
  ➜ Admin: [admin@tiendaonline.com](mailto:admin@tiendaonline.com)

- crt.sh:
  ➜ Descubres subdominio: dev.tiendaonline.com

✅ ACTIVA:

- Nmap `tiendaonline.com`
  ➜ Puertos abiertos: 80, 443, 22

- Banner Grabbing:
  ➜ Server: Apache/2.2

✅ Resultado:

- Plan para siguiente fase:

  - Revisar Apache 2.2 (muy viejo).
  - Intentar fuerza bruta en SSH (si se autoriza).
  - Atacar subdominio dev.

---

### Reglas éticas

**⚠️ Muy importante:**

- La recopilación de información activa **solo con permiso**.
- Lo pasivo (como búsquedas en Google) suele ser legal, pero el análisis debe respetar acuerdos de confidencialidad.

---

### Resumen fácil

✅ Es la **fase de “espionaje” ético**.
✅ Buscas **toda la info posible**.
✅ Sirve para planificar **ataques más efectivos** (o defender mejor).
✅ Incluye técnicas **pasivas y activas**.
✅ Herramientas: Nmap, Whois, Google, Maltego, Shodan.

---

### Frase clave para recordar

> 🎯 **“No puedes atacar bien lo que no conoces bien.”**
> La recopilación de información es la clave para un test de penetración exitoso.

---

[🔼](#índice)

---

## **4. Recopilación pasiva de información**

### ¿Qué es la recopilación pasiva de información?

Es una técnica de **recolección de datos sin interactuar directamente con el sistema objetivo**.
🔍 No generas tráfico hacia el servidor, red o aplicación.
🎯 **Todo lo haces desde fuentes públicas y abiertas**, como buscadores, redes sociales, bases de datos públicas, etc.

#### 🔐 Es completamente legal (si no accedes a sistemas privados).

---

### ¿Para qué sirve?

- Para **entender cómo está expuesta la organización** en internet.
- Para **planificar ataques futuros** (en hacking ético).
- Para **reducir la superficie de ataque** (en defensa).

---

### ¿Qué tipo de información puedes obtener?

| Tipo de info   | Ejemplo                               |
| -------------- | ------------------------------------- |
| Subdominios    | `dev.empresa.com`                     |
| Correos        | `juan.perez@empresa.com`              |
| Tecnologías    | Apache, WordPress, PHP                |
| Empleados      | LinkedIn, Facebook                    |
| Documentos     | PDFs, Word, Excel públicos            |
| Direcciones IP | Desde registros DNS o históricos      |
| Teléfonos      | Página de contacto, anuncios          |
| Servidores     | info de servicios expuestos en Shodan |

---

### Ejemplo práctico paso a paso

🎯 Objetivo: `www.ejemplo.com`

---

#### 🔍 Paso 1: Búsqueda con Google (Google Dorking)

```plaintext
site:ejemplo.com filetype:pdf
```

➡ Encuentras manuales y reportes públicos en PDF.

```plaintext
inurl:admin site:ejemplo.com
```

➡ Te muestra rutas como `www.ejemplo.com/admin/login`.

✅ **Aprendes posibles rutas de panel de administración.**

---

#### 🧑‍💼 Paso 2: Buscar empleados en LinkedIn

🔎 Buscas “Ejemplo S.A.C.” en LinkedIn.

✅ Encuentras:

- José Ríos – SysAdmin
- Ana Ledesma – RRHH

✅ **Esto sirve para ataques de ingeniería social o phishing** (con permiso del cliente, claro).

---

#### 🌐 Paso 3: Whois (información del dominio)

```bash
whois ejemplo.com
```

➡ Resultado:

- Registrante: Carlos Gomez
- Email técnico: [admin@ejemplo.com](mailto:admin@ejemplo.com)
- Servidor DNS: ns1.ejemplo.com

✅ **Sabes quién administra el sitio y puedes buscar más sobre ese correo.**

---

#### 📜 Paso 4: crt.sh – Certificados SSL públicos

🔎 Entras a: [https://crt.sh](https://crt.sh) y buscas:

```plaintext
%ejemplo.com
```

➡ Encuentras:

- dev.ejemplo.com
- api.ejemplo.com
- test.ejemplo.com

✅ **Estos subdominios no aparecen en Google, pero sí en los certificados.**

---

#### 🌍 Paso 5: Netcraft – Tecnologías y servidores

🔎 Entras a: [https://sitereport.netcraft.com/](https://sitereport.netcraft.com)

Buscas `www.ejemplo.com`.

➡ Resultado:

- Servidor: Apache/2.4.41
- Ubicación: Lima, Perú
- IP del servidor: 190.xxx.xxx.12

✅ **Ya sabes qué versión del servidor usan (para buscar vulnerabilidades después).**

---

#### 📡 Paso 6: Shodan (motor de búsqueda de dispositivos conectados)

🔎 Entras a: [https://www.shodan.io](https://www.shodan.io)

Buscas:

```plaintext
hostname:"ejemplo.com"
```

➡ Encuentras:

- Un servidor expone puerto 21 (FTP) sin cifrado.
- Hay servicios que responden a peticiones en el puerto 80 desde fuera.

✅ **Esto te muestra posibles fallos sin escanear tú mismo el sistema.**

---

### Herramientas comunes para recopilación pasiva

| Herramienta        | Función principal                        |
| ------------------ | ---------------------------------------- |
| 🔎 Google Dorks    | Buscar archivos, rutas ocultas           |
| 🌐 Whois           | Información de registro de dominios      |
| 🧑‍💼 LinkedIn        | Identificar empleados y roles            |
| 📜 crt.sh          | Descubrir subdominios vía SSL            |
| 🧠 Maltego         | Relaciones entre personas, dominios      |
| 📡 Shodan          | Información sobre dispositivos expuestos |
| 🌐 Netcraft        | Tecnologías, IP, geolocalización         |
| 📂 Wayback Machine | Ver versiones antiguas del sitio         |
| 🔧 Hunter.io       | Descubrir correos públicos               |

---

### Ventajas de la recopilación pasiva

✅ No generas alertas ni tráfico sospechoso.
✅ Es totalmente legal si accedes a fuentes abiertas.
✅ Muy útil para **ingeniería social**, **OSINT** y **red teaming**.

---

### Buenas prácticas

✅ Guarda toda la evidencia encontrada (pantallazos, links, datos).
✅ Organiza en un informe: subdominios, emails, empleados, archivos encontrados.
✅ Mantén el objetivo dentro del alcance autorizado.
✅ Si haces esto como parte de una auditoría, **documenta la fuente exacta** (URL, fecha, etc.).

---

### Ejemplo de resumen de información pasiva recolectada

| Categoría        | Dato encontrado                                                                                  |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| Subdominios      | `dev.ejemplo.com`, `api.ejemplo.com`                                                             |
| Empleados        | José Ríos (TI), Ana Ledesma (RRHH)                                                               |
| Tecnologías      | Apache/2.4.41, WordPress                                                                         |
| Correos públicos | [soporte@ejemplo.com](mailto:soporte@ejemplo.com), [admin@ejemplo.com](mailto:admin@ejemplo.com) |
| Archivos         | Manual técnico (manual_red.pdf)                                                                  |
| IP Pública       | 190.200.50.12                                                                                    |

---

### Conclusión

La **recopilación pasiva de información** es:

- 🔍 Una forma segura y silenciosa de obtener datos clave.
- 🧠 Basada en inteligencia abierta (OSINT).
- 🧱 El primer paso crítico para un análisis profundo.

> 🎯 **Recuerda:** “Quien domina la información, domina el juego.”

---

[🔼](#índice)

---

## **5. Hacking con buscadores: Google Hacking**

### ¿Qué es Google Hacking?

Google Hacking (también llamado Google Dorking) es **el uso avanzado del motor de búsqueda de Google para encontrar información sensible o interesante**.

👉 Se basa en usar **comandos especiales (dorks)** para filtrar resultados de forma precisa.

✅ Con Google puedes:

- Encontrar archivos confidenciales expuestos.
- Descubrir paneles de administración.
- Ver cámaras o dispositivos mal configurados.
- Obtener versiones de software.
- Enumerar usuarios o correos públicos.

**⚠️ Nota:**

✅ Google Hacking no explota vulnerabilidades directamente.

✅ Solo descubre **lo que ya está público**.

✅ Es 100% legal si solo navegas y NO hackeas nada.

---

### ¿Por qué es útil en hacking ético?

- Es **recopilación pasiva**: el objetivo no sabrá que buscas.
- Muy usado en OSINT (Open Source Intelligence).
- Ayuda a mapear la superficie de ataque.
- Ahorra tiempo y descubre errores de exposición.

> 🎯 _Ejemplo real: empresas que suben sus backups o contraseñas a internet sin querer._

---

### ¿Cómo funciona?

Usas operadores avanzados de Google llamados **dorks**.
Son comandos especiales para refinar la búsqueda.

✅ Algunos dorks básicos:

| Operador     | Uso                                     | Ejemplo                    |
| ------------ | --------------------------------------- | -------------------------- |
| `site:`      | Limita a un dominio específico          | `site:empresa.com`         |
| `inurl:`     | Busca en la URL                         | `inurl:admin`              |
| `intitle:`   | Busca en el título de la página         | `intitle:"index of"`       |
| `filetype:`  | Busca archivos con extensión específica | `filetype:pdf`             |
| `allintext:` | Palabras exactas en el texto            | `allintext:"confidential"` |
| `cache:`     | Muestra la versión en caché de Google   | `cache:empresa.com`        |

✅ Puedes combinarlos:

```
site:empresa.com filetype:pdf intext:password
```

---

### Ejemplo súper fácil paso a paso

**🎯 Caso:** Hacer una auditoría ética para `empresa.com`.

---

#### ✅ A. Buscar documentos públicos

```plaintext
site:empresa.com filetype:pdf
```

✅ Resultado:

- Manuales técnicos.
- Informes internos subidos por error.

---

#### ✅ B. Buscar contraseñas en documentos públicos

```plaintext
site:empresa.com intext:password
```

✅ Resultado:

- Un documento con:
  `MySQL password: 123456`

---

#### ✅ C. Encontrar paneles de administración

```plaintext
inurl:admin
```

o

```plaintext
site:empresa.com inurl:login
```

✅ Resultado:

- `www.empresa.com/admin/login.php`

✅ Usos:

- Mapear rutas sensibles.
- Recomendar al cliente ocultar o proteger mejor.

---

#### ✅ D. Descubrir backups expuestos

```plaintext
site:empresa.com filetype:sql
```

✅ Resultado:

- `backup_cliente.sql` descargable.

---

#### ✅ E. Listado de directorios (indexación expuesta)

```plaintext
intitle:"index of" site:empresa.com
```

✅ Resultado:

- Carpeta pública navegable con fotos, documentos.

---

#### ✅ F. Combinar dorks para más precisión

```plaintext
site:empresa.com inurl:backup filetype:zip
```

✅ Resultado:

- `backup2024.zip` disponible para descargar.

---

#### ✅ G. Encontrar cámaras o dispositivos

```plaintext
inurl:/view/index.shtml
```

✅ Resultado:

- Páginas con video en vivo de cámaras IP mal configuradas.

---

### Tabla con ejemplos reales de dorks

| Búsqueda                        | Qué busca                                    |
| ------------------------------- | -------------------------------------------- |
| `filetype:xls site:empresa.com` | Planillas Excel expuestas                    |
| `filetype:pdf confidential`     | Documentos PDF con la palabra "confidential" |
| `inurl:wp-admin`                | Paneles de administración de WordPress       |
| `intitle:"index of" passwords`  | Listados de carpetas con contraseñas         |
| `site:*.empresa.com`            | Subdominios del dominio                      |
| `inurl:signup`                  | Formularios de registro expuestos            |

---

### Herramientas para facilitar Google Hacking

✅ Manual:

- Tu navegador y Google.

✅ Semiautomáticas:

- **Google Hacking Database (GHDB):**
  👉 [https://www.exploit-db.com/google-hacking-database](https://www.exploit-db.com/google-hacking-database)

✅ Automáticas:

- **theHarvester** (OSINT)
- **Recon-ng** (framework OSINT)
- **FOCA** (extrae metadatos y archivos)

---

### Resultado típico en un informe de pentest

En la **sección de recopilación pasiva**, el informe puede decir:

> ✔️ Durante las búsquedas avanzadas en Google se encontraron archivos públicos sensibles:
>
> - `manual_interno.pdf` con información técnica.
> - `backup2024.zip` accesible sin contraseña.
> - Panel de administración en `/admin/login.php`.
>
> ✔️ Recomendación:
>
> - Eliminar documentos sensibles de la web pública.
> - Implementar restricciones de acceso.
> - Desactivar indexación de carpetas.

---

### Ventajas y desventajas

✅ Ventajas:

- 100% pasivo y silencioso.
- Muy fácil de hacer.
- Acceso a toneladas de info pública.

⚠️ Desventajas:

- Solo encuentras lo que ya está expuesto.
- Puede dar **falsos positivos** (datos antiguos o irrelevantes).

---

### Buenas prácticas

✅ Usa combinaciones lógicas (AND, OR) para refinar.
✅ Guarda resultados con fecha y hora.
✅ Documenta fuentes exactas para el cliente.
✅ No abuses: no descargues datos confidenciales sin permiso explícito.

---

### Frase clave para recordar

> 🎯 **“Google sabe más sobre tu empresa de lo que imaginas.”**

---

### Resumen rápido

📌 **Google Hacking** es:

✅ Usar dorks (operadores avanzados) en Google.

✅ Descubrir información pública sensible.

✅ Fundamental en la **fase de recopilación pasiva** de un pentest.

✅ 100% OSINT (Open Source Intelligence).

---

### Ejercicio fácil para practicar

**Objetivo:** El sitio ficticio `example.com`.

✅ Encuentra:

- Documentos PDF públicos:

```
site:example.com filetype:pdf
```

- Paneles de administración:

```
inurl:admin site:example.com
```

- Archivos de backup:

```
site:example.com filetype:zip OR filetype:tar
```

- Directorios indexados:

```
intitle:"index of" site:example.com
```

---

[🔼](#índice)

---

## **6. Google Hacking Database**

### ¿Qué es la Google Hacking Database (GHDB)?

La **Google Hacking Database** es **un repositorio público** de _dorks_ o búsquedas avanzadas que permiten encontrar **información sensible o vulnerable** usando Google.

Fue creada y mantenida por **Offensive Security (exploit-db.com)**.

✅ Es como un **catálogo de “búsquedas inteligentes”** ya probadas por otros hackers éticos.
✅ Ayuda a **encontrar problemas de seguridad expuestos en Internet** sin escanear ni atacar directamente.

---

### ¿Por qué existe?

Porque **mucha gente publica cosas en Internet sin saber que están expuestas**.

✅ Bases de datos de backups.

✅ Contraseñas en archivos públicos.

✅ Paneles de administración sin protección.

✅ Directorios abiertos.

✅ Cámaras IP mal configuradas.

✅ Logs de errores con datos internos.

El GHDB **documenta y clasifica estas búsquedas para que pentesters puedan encontrarlas fácilmente**.

---

### ¿Dónde se encuentra?

👉 Está online y gratuita en:
🔗 [https://www.exploit-db.com/google-hacking-database](https://www.exploit-db.com/google-hacking-database)

---

### ¿Cómo está organizada?

El GHDB está organizado en **categorías**.
Aquí tienes las más comunes con **explicación sencilla y ejemplo real**:

---

#### ✅ A. **Files containing passwords**

> Archivos que exponen contraseñas.

📌 Ejemplo de dork:

```
filetype:txt intext:password
```

✅ Resultado típico:

- Archivos `.txt` con contenido como:

  ```
  username: admin
  password: 123456
  ```

---

#### ✅ B. **Sensitive Directories**

> Directorios abiertos que no deberían estar indexados.

📌 Ejemplo:

```
intitle:"index of" admin
```

✅ Resultado típico:

- Listados de carpetas `/admin/` con archivos descargables.

---

#### ✅ C. **Login Pages**

> Páginas de login expuestas o mal protegidas.

📌 Ejemplo:

```
inurl:admin/login
```

✅ Resultado típico:

- Panel de administración de un CMS.

---

#### ✅ D. **Error Messages**

> Páginas que muestran errores con info sensible.

📌 Ejemplo:

```
intext:"Warning: mysql_fetch"
```

✅ Resultado típico:

- Código de error PHP que revela estructura de la base de datos.

---

#### ✅ E. **Vulnerable Files**

> Archivos con exploits conocidos.

📌 Ejemplo:

```
inurl:wp-config.php.bak
```

✅ Resultado típico:

- Archivo de configuración de WordPress con claves de la DB.

---

#### ✅ F. **Pages containing juicy info**

> Páginas con info sensible, aunque no sea un error obvio.

📌 Ejemplo:

```
intext:"ssn" filetype:xls
```

✅ Resultado típico:

- Planillas Excel con números de seguro social o IDs.

---

#### ✅ G. **Exploit Files**

> Archivos subidos que incluyen exploits.

📌 Ejemplo:

```
filetype:py intext:exploit
```

✅ Resultado típico:

- Scripts de prueba o PoC olvidados en servidores públicos.

---

### ¿Cómo se usa en hacking ético?

✅ En la fase de **recopilación pasiva de información**.
✅ Para descubrir **exposición involuntaria de información**.
✅ Sin generar tráfico sospechoso hacia el objetivo (el tráfico va a Google).

---

### Ejemplo práctico paso a paso

🎯 Objetivo: Auditoría para `empresa.com`

✅ 1️⃣ Buscar backups expuestos:

```
site:empresa.com filetype:sql
```

➡ Resultado:

- `clientes_backup.sql` → contiene datos de clientes.

---

✅ 2️⃣ Buscar contraseñas en archivos de texto:

```
site:empresa.com filetype:txt intext:password
```

➡ Resultado:

- `configuracion.txt` → incluye:

  ```
  db_password=admin123
  ```

---

✅ 3️⃣ Directorios abiertos:

```
intitle:"index of" site:empresa.com
```

➡ Resultado:

- Carpeta `/uploads/` con fotos y documentos internos.

---

✅ 4️⃣ Login pages:

```
site:empresa.com inurl:login
```

➡ Resultado:

- `https://empresa.com/admin/login.php`

---

✅ 5️⃣ Error messages:

```
site:empresa.com intext:"Warning: mysql_fetch"
```

➡ Resultado:

- Muestra código y tablas SQL → posible SQLi.

---

### Cómo se ve un resultado en GHDB

En el sitio web verás algo así:

| Title                      | Category                   | Dork                           | Author    |
| -------------------------- | -------------------------- | ------------------------------ | --------- |
| Files containing passwords | Files containing passwords | `filetype:txt intext:password` | Johnny    |
| Exposed Backups            | Vulnerable Files           | `filetype:sql inurl:backup`    | admin     |
| Admin Login Pages          | Login Pages                | `inurl:admin/login`            | pentester |

✅ Copias el **Dork** y lo pegas en Google.

✅ Personalizas con el sitio objetivo (opcional).

---

### Usar dorks de GHDB de forma ética

✅ Úsalos **solo en objetivos donde tengas permiso**.

✅ Documenta los hallazgos en tu informe.

✅ No descargues datos confidenciales sin autorización.

✅ Informa al cliente para que elimine o restrinja el acceso.

---

### Resultado típico en un informe de pentest

En la sección de **Recopilación Pasiva**:

> ✔️ Se usaron búsquedas avanzadas (GHDB) para identificar exposición pública.
>
> - Archivo `clientes_backup.sql` disponible públicamente (contiene emails y teléfonos).
> - Contraseña en `configuracion.txt` expuesta en Google.
> - Directorio `/uploads/` indexado y navegable.
>
> ✔️ Recomendaciones:
>
> - Retirar archivos innecesarios de la web pública.
> - Desactivar el listado de directorios.
> - Implementar políticas de control de versiones y limpieza.

---

### Resumen en pocas palabras

✅ **Google Hacking Database** = colección de dorks probados para encontrar info sensible en Google.

✅ Muy útil en **OSINT y pentesting**.

✅ Facilita la **fase de recopilación pasiva**.

✅ Ayuda a descubrir **errores de configuración** en sitios web.

✅ Es **legal** si solo navegas y **no hackeas**.

---

### Frase clave para recordar

> 🎯 **“No necesitas ser un hacker para encontrar secretos; solo necesitas saber buscar.”**

---

### Ejercicio fácil para ti

✔️ Abre Google y prueba estas búsquedas (¡en sitios públicos o de prueba!):

✅ Buscar PDFs:

```
site:example.com filetype:pdf
```

✅ Backups expuestos:

```
filetype:sql inurl:backup
```

✅ Login pages:

```
inurl:admin/login
```

✅ Directorios abiertos:

```
intitle:"index of" confidential
```

---

[🔼](#índice)

---

## **7. Google Hacking: Comandos y Operadores Booleanos**

### ¿Qué es Google Hacking?

Es el uso de **operadores avanzados (dorks)** en Google para encontrar **información específica y muchas veces sensible o mal protegida** en la web.

✅ Es una forma de **recopilación de información pasiva** (OSINT).

✅ Aprovecha **la potencia del buscador** para descubrir cosas que el propio dueño del sitio no sabía que estaban accesibles.

> 🎯 **Ejemplo:**
> Buscar archivos PDF con contraseñas expuestas.

---

### ¿Qué son los comandos o “operadores” en Google?

Son **palabras clave especiales** que le dicen a Google **cómo debe buscar**.

✅ Sirven para:

- Filtrar resultados.
- Especificar el formato del archivo.
- Limitar la búsqueda a un sitio.
- Buscar en el título, en la URL, etc.

---

### ¿Qué son los operadores booleanos?

Son **conectores lógicos** para combinar o excluir términos.

✅ Los principales son:

- `AND`
- `OR`
- `-` (NOT)
- `""` (comillas exactas)

✅ Sirven para **refinar aún más** las búsquedas.

---

### Los comandos más comunes de Google Hacking

Vamos a ver **cada comando con su explicación sencilla y un ejemplo real**.

---

#### ✅ **site:**

Limita la búsqueda a un dominio específico.

📌 Ejemplo:

```
site:empresa.com
```

➡ Solo muestra resultados de `empresa.com`.

✅ Muy usado en pentesting para **restringir el objetivo.**

---

#### ✅ **inurl:**

Busca palabras clave en la URL.

📌 Ejemplo:

```
inurl:admin
```

➡ Encuentra URLs que contengan “admin” → como `/admin/login.php`.

✅ Muy útil para:

- Encontrar paneles de administración.
- Rutas interesantes.

---

#### ✅ **intitle:**

Busca palabras en el **título de la página**.

📌 Ejemplo:

```
intitle:"index of"
```

➡ Encuentra **directorios listados** en servidores web.

✅ Muy útil para:

- Ver carpetas expuestas con navegación habilitada.

---

#### ✅ **intext:**

Busca palabras específicas en el **contenido** de la página.

📌 Ejemplo:

```
intext:"password"
```

➡ Encuentra páginas o documentos donde aparece “password”.

✅ Muy útil para:

- Encontrar configuraciones mal expuestas.

---

#### ✅ **filetype:**

Filtra resultados por **extensión de archivo**.

📌 Ejemplo:

```
filetype:pdf
```

➡ Solo PDF.

✅ Combinar con site:

```
site:empresa.com filetype:pdf
```

➡ Todos los PDFs públicos de `empresa.com`.

---

#### ✅ **allinurl:**

Requiere que **todos los términos aparezcan en la URL**.

📌 Ejemplo:

```
allinurl:admin login
```

➡ URLs que contengan **ambas** palabras.

---

#### ✅ **allintitle:**

Todos los términos deben aparecer en el **título**.

📌 Ejemplo:

```
allintitle:admin login
```

➡ Títulos de páginas con “admin” y “login”.

---

#### ✅ **cache:**

Muestra la versión **en caché** de una página guardada por Google.

📌 Ejemplo:

```
cache:empresa.com
```

➡ Ver contenido aunque esté eliminado o modificado.

---

#### ✅ **related:**

Encuentra sitios **similares**.

📌 Ejemplo:

```
related:empresa.com
```

➡ Empresas del mismo rubro.

✅ Menos usado en pentest, pero útil en OSINT.

---

### Operadores Booleanos

Ahora vamos a los **operadores lógicos** que combinan o filtran resultados:

---

#### ✅ **AND** (implícito)

Google **ya asume AND** si pones palabras separadas.

📌 Ejemplo:

```
admin login
```

➡ Resultados que incluyan **ambos** términos.

✅ No necesitas escribir AND, está implícito.

---

#### ✅ **OR** (mayúsculas)

Permite **una u otra palabra**.

📌 Ejemplo:

```
admin OR login
```

➡ Páginas que contengan **admin o login**.

✅ Usado para ampliar resultados.

---

#### ✅ **- (NOT)**

Excluye resultados.

📌 Ejemplo:

```
admin -login
```

➡ Resultados con **admin**, pero **sin** login.

✅ Muy útil para eliminar ruido.

---

#### ✅ **"" (comillas exactas)**

Búsqueda **exacta**.

📌 Ejemplo:

```
"admin login"
```

➡ Solo resultados con esa frase exacta.

✅ Evita resultados irrelevantes.

---

### Combinando operadores para búsquedas potentes

👉 La verdadera fuerza de Google Hacking está en **combinarlos**.

---

✅ 📌 Ejemplo 1 – Buscar backups SQL en un dominio

```
site:empresa.com filetype:sql
```

➡ Encuentra bases de datos exportadas.

---

✅ 📌 Ejemplo 2 – Contraseñas en archivos de texto o config

```
filetype:txt OR filetype:conf intext:password
```

➡ Archivos `.txt` o `.conf` con la palabra **password**.

---

✅ 📌 Ejemplo 3 – Directorios expuestos

```
intitle:"index of" admin
```

➡ Directorios públicos con “admin” en el nombre.

---

✅ 📌 Ejemplo 4 – Login pages en un dominio

```
site:empresa.com inurl:login OR inurl:admin
```

➡ Todas las páginas de login o admin en el sitio.

---

✅ 📌 Ejemplo 5 – Excluir resultados molestos

```
site:empresa.com inurl:admin -support
```

➡ Todas las páginas admin, pero **sin** las de soporte.

---

### Ejemplo real paso a paso

🎯 Objetivo ficticio: `acme.com`

✅ Paso 1 – Limitar al dominio

```
site:acme.com
```

✅ Todos los resultados del sitio.

---

✅ Paso 2 – Buscar paneles de admin

```
site:acme.com inurl:admin
```

✅ Encuentras:

```
acme.com/admin/login.php
acme.com/admin/dashboard
```

---

✅ Paso 3 – Ver PDFs públicos

```
site:acme.com filetype:pdf
```

✅ Resultado:

- `manual_tecnico.pdf`
- `contratos2024.pdf`

---

✅ Paso 4 – Buscar contraseñas en archivos públicos

```
site:acme.com intext:password
```

✅ Resultado:

- `configuracion.txt`:

  ```
  db_password=123456
  ```

---

✅ Paso 5 – Buscar backups expuestos

```
site:acme.com filetype:sql OR filetype:zip
```

✅ Resultado:

- `backup_clientes2023.sql`
- `respaldo.zip`

---

### Tabla resumen de comandos

| Comando       | Qué hace                        | Ejemplo                  |
| ------------- | ------------------------------- | ------------------------ |
| `site:`       | Limita a un dominio             | `site:empresa.com`       |
| `inurl:`      | Busca en la URL                 | `inurl:admin`            |
| `intitle:`    | Busca en el título de la página | `intitle:"index of"`     |
| `intext:`     | Busca en el texto de la página  | `intext:password`        |
| `filetype:`   | Filtra por tipo de archivo      | `filetype:pdf`           |
| `allinurl:`   | Todos los términos en la URL    | `allinurl:admin login`   |
| `allintitle:` | Todos los términos en el título | `allintitle:admin login` |
| `cache:`      | Ver versión en caché            | `cache:empresa.com`      |
| `OR`          | Uno u otro término              | `login OR admin`         |
| `-`           | Excluye términos                | `admin -login`           |
| `""`          | Búsqueda exacta                 | `"admin login"`          |

---

### Buenas prácticas

✅ Usa comillas para frases exactas.

✅ Combina operadores para reducir resultados irrelevantes.

✅ Documenta tus dorks más útiles.

✅ Respeta la ética: no uses para hackear sitios sin permiso.

---

### Frase clave para recordar

> 🎯 **“Saber buscar es más importante que saber romper.”**

---

### Ejercicio sencillo para ti

✔️ Prueba estas búsquedas en Google (con un dominio de prueba):

✅ PDFs públicos:

```
site:example.com filetype:pdf
```

✅ Paneles de admin:

```
inurl:admin OR inurl:login
```

✅ Directorios abiertos:

```
intitle:"index of"
```

✅ Backups expuestos:

```
filetype:sql OR filetype:zip inurl:backup
```

✅ Contraseñas en texto:

```
intext:password filetype:txt
```

---

[🔼](#índice)

---

## **8. Shodan**

### ¿Qué es Shodan?

**Shodan** es un **motor de búsqueda especializado** que, en lugar de indexar páginas web como Google, **indexa dispositivos conectados a Internet**.

✅ Ejemplos de dispositivos que Shodan encuentra:

- Cámaras IP.
- Servidores web.
- Routers.
- Bases de datos expuestas.
- Sistemas de control industrial (SCADA).
- IoT (Internet de las Cosas).

> 🎯 **Frase fácil:**

> 🧭 **“Shodan es como Google, pero para cosas conectadas.”**

---

### ¿Para qué sirve?

✅ **Para ciberseguridad:**

- Detectar dispositivos expuestos sin protección.
- Ver servicios abiertos y versiones vulnerables.
- Auditar redes (con permiso).

✅ **Para investigación:**

- Ver cuántos dispositivos de un tipo hay en un país.
- Analizar exposición global de un protocolo.

✅ **Para OSINT (Inteligencia de Fuentes Abiertas):**

- Obtener información sobre objetivos.
- Mapear infraestructura.

---

### ¿Cómo funciona Shodan?

🧭 Mientras Google usa **bots web** para descargar páginas HTML...

✅ **Shodan escanea puertos** de direcciones IP.

✅ Obtiene **banners** → texto que describe el servicio.

✅ Banner típico:

```
220 ProFTPD 1.3.5 Server (Debian) [::ffff:192.168.1.1]
```

➡ Indica:

- Software (ProFTPD 1.3.5)
- Sistema operativo (Debian)

✅ Shodan **almacena estos datos** para que los busques.

---

### ¿Qué es un _banner_?

📌 Es la **respuesta de un servicio al conectarse**.

✅ Contiene información del sistema.

✅ Ejemplo real:

```
HTTP/1.1 200 OK
Server: Apache/2.4.29 (Ubuntu)
```

➡ Sabes:

- Que es Apache.
- Su versión.
- El sistema operativo.

✅ Shodan recoge millones de estos banners.

---

### Acceso a Shodan

✅ Sitio web oficial:
🔗 [https://www.shodan.io](https://www.shodan.io)

✅ Tiene:

- Versión gratuita (limitada).
- Planes pagos (más resultados y funciones).

✅ También tiene:

- API para desarrolladores.
- CLI (interfaz de línea de comandos).

---

### Usos típicos de Shodan

🎯 ✅ Auditorías y pentesting:

- Encontrar dispositivos sin contraseña.
- Ver puertos abiertos innecesarios.
- Identificar servicios vulnerables.

✅ Investigación de ciberamenazas:

- Ver dispositivos infectados.
- Mapear botnets.

✅ Inventario de activos:

- Saber qué está expuesto en tu organización.

---

### Ejemplo súper fácil de búsqueda en Shodan

Imagina que quieres **buscar cámaras web abiertas**.

✅ Escribes:

```
webcamXP
```

➡ Resultado:

- Listado de cámaras usando ese software.
- Muchas veces sin contraseña.

✅ Puedes filtrar por país:

```
webcamXP country:"PE"
```

➡ Cámaras en Perú.

---

### Ejemplo con servidores

✅ Buscar servidores Apache:

```
Apache
```

➡ Resultado:

- IPs con Apache expuesto.
- Puertos abiertos (80, 443).
- Versión del servidor.

✅ Buscar solo en un país:

```
Apache country:"BR"
```

➡ Solo en Brasil.

✅ Buscar versión vulnerable:

```
Apache/2.2.3
```

➡ Esa versión es vieja → posiblemente vulnerable.

---

### Ejemplo con protocolos industriales (SCADA)

✅ Buscar sistemas ICS (peligrosos si están expuestos):

```
port:502
```

➡ Modbus (protocolo industrial).

✅ Buscar sistemas HMI:

```
"Human Machine Interface"
```

➡ Interfaces industriales mal configuradas.

---

### Operadores avanzados en Shodan

✅ **country:** filtra por país.

```
country:"US"
```

✅ **port:** busca en un puerto específico.

```
port:22
```

✅ **org:** filtra por organización (ISP).

```
org:"Telefonica"
```

✅ **hostname:** filtra por nombre de host.

```
hostname:"example.com"
```

✅ **os:** sistema operativo.

```
os:"Windows 2012"
```

✅ **after/before:** fechas.

```
after:"2023-01-01"
```

---

### Ejemplo práctico paso a paso

🎯 Imagina que eres un auditor de seguridad contratado para revisar la exposición de tu cliente en Perú.

✅ Paso 1 – Buscar SSH expuesto en Perú:

```
port:22 country:"PE"
```

➡ Resultado:

- IPs con SSH abierto en Perú.
- Versiones del servidor SSH.

✅ Paso 2 – Encontrar cámaras abiertas:

```
webcam country:"PE"
```

➡ Resultado:

- Cámaras sin autenticación.

✅ Paso 3 – Ver servidores Apache en Perú:

```
Apache country:"PE"
```

➡ Resultado:

- IPs con Apache.
- Versiones → verificar si son obsoletas.

---

### Resultados típicos que obtienes

✅ IP pública.

✅ Puerto abierto.

✅ Banner con versión del servicio.

✅ Geolocalización aproximada.

✅ ISP (proveedor de internet).

---

✅ **Ejemplo de resultado real de un servidor web en Shodan:**

```
IP: 200.48.120.55
Port: 80
Banner:
HTTP/1.1 200 OK
Server: Apache/2.2.22 (Debian)
```

➡ Sabes:

- IP pública.
- Puerto 80 abierto.
- Apache versión 2.2.22 (¡vieja y vulnerable!).

---

### Ventajas de Shodan

✅ Fácil de usar → solo escribes palabras clave.

✅ Enorme base de datos de dispositivos.

✅ Resultados actualizados.

✅ Permite filtrar por país, organización, puerto, etc.

✅ Herramienta OSINT **legal y pasiva**.

---

### Limitaciones

⚠️ Resultados a veces pueden estar desactualizados.

⚠️ Acceso completo requiere suscripción.

⚠️ Solo te dice que **está expuesto**, pero no explota vulnerabilidades.

---

### Uso ético

✅ Usar Shodan **no es ilegal**: la información es pública.

✅ Pero **explotar o vulnerar** dispositivos sin permiso SÍ es ilegal.

✅ Usar para:

- Pentesting autorizado.
- Auditorías de seguridad.
- Investigación académica.

---

### Frase clave para recordar

> 🎯 **“Shodan no rompe nada. Solo te muestra lo que ya está roto y expuesto.”**

---

### Ejercicio fácil para ti

✅ Entra en [https://www.shodan.io](https://www.shodan.io)

✅ Prueba estas búsquedas:

1️⃣ Buscar cámaras:

```
webcamXP
```

2️⃣ Servidores SSH en un país:

```
port:22 country:"PE"
```

3️⃣ Servidores Apache:

```
Apache
```

4️⃣ Filtrar por organización:

```
org:"Telefonica"
```

---

### Tabla resumen de operadores en Shodan

| Operador    | Qué hace                        | Ejemplo                  |
| ----------- | ------------------------------- | ------------------------ |
| `port:`     | Busca por puerto específico     | `port:22`                |
| `country:`  | Limita a un país                | `country:"PE"`           |
| `org:`      | Filtra por organización o ISP   | `org:"Telefonica"`       |
| `hostname:` | Busca en nombres de dominio     | `hostname:"empresa.com"` |
| `os:`       | Filtra por sistema operativo    | `os:"Windows"`           |
| `after:`    | Resultados después de una fecha | `after:"2023-01-01"`     |
| `before:`   | Resultados antes de una fecha   | `before:"2023-06-01"`    |

---

### Resumen corto

✅ **Shodan** = buscador para dispositivos conectados.

✅ Encuentra **cámaras, servidores, routers, IoT**.

✅ Usa **banners** para mostrar versiones y configuraciones.

✅ Ideal para **pentesters y auditores**.

✅ Permite **filtrar** por país, puerto, organización y más.

---

[🔼](#índice)

---

## **9. Shodan: Comandos principales**

### ¿Para qué sirven los comandos en Shodan?

**Shodan** es un motor de búsqueda para dispositivos conectados.

✅ Los **comandos** o **filtros** te permiten **afinar** la búsqueda.

✅ Te ayudan a **encontrar exactamente** el tipo de dispositivo, servicio, país o puerto que quieres analizar.

> 🎯 **Frase sencilla:** > **"Los comandos en Shodan son como filtros en Google, pero para Internet de las Cosas."**

---

### ¿Dónde se usan?

✅ En la barra de búsqueda de [shodan.io](https://www.shodan.io).

✅ En la **CLI** (línea de comandos) o **API** (para programadores).

✅ Aquí nos centraremos en la **interfaz web** (la más fácil de entender).

---

### ¿Cómo se usan los comandos?

✅ Simplemente **los escribes en la barra de búsqueda** junto con tus términos.

✅ **Formato:**

```
<palabra clave> <comando>:<valor>
```

✅ Puedes combinarlos:

```
Apache port:80 country:"PE"
```

➡ Busca servidores **Apache** en el **puerto 80** en **Perú**.

---

### Comando clave #1: `port:`

✅ Limita los resultados a **un puerto específico**.

✅ Ejemplo básico:

```
port:22
```

➡ Encuentra todos los servicios SSH (normalmente en el puerto 22).

✅ Ejemplo práctico:

```
OpenSSH port:22 country:"PE"
```

➡ Busca servidores **SSH** en **Perú**.

✅ Útil para:

- Auditar puertos abiertos.
- Identificar servicios expuestos.

---

### Comando clave #2: `country:`

✅ Filtra resultados por **país**.

✅ Usa el **código ISO de dos letras**.

✅ Ejemplo:

```
country:"US"
```

➡ Solo resultados en Estados Unidos.

✅ Combinado:

```
webcamXP country:"PE"
```

➡ Encuentra cámaras en Perú.

---

### Comando clave #3: `city:`

✅ Filtra por **ciudad** (cuando Shodan tiene ese dato).

✅ Ejemplo:

```
port:80 city:"Lima"
```

➡ Servidores web en Lima.

✅ ⚠️ A veces la geolocalización no es 100% precisa.

---

### Comando clave #4: `org:`

✅ Filtra por **organización** o proveedor (ISP).

✅ Ejemplo:

```
org:"Telefonica"
```

➡ Solo dispositivos con direcciones IP asignadas a Telefónica.

✅ Combinado:

```
Apache org:"Movistar"
```

➡ Servidores Apache en Movistar.

---

### Comando clave #5: `hostname:`

✅ Busca coincidencias en el **nombre de host** (DNS).

✅ Ejemplo:

```
hostname:"empresa.com"
```

➡ Encuentra cualquier IP o dispositivo que tenga ese dominio o subdominio.

✅ Muy útil para:

- Descubrir subdominios.
- Mapear infraestructura.

---

### Comando clave #6: `os:`

✅ Filtra por **sistema operativo** detectado en el banner.

✅ Ejemplo:

```
os:"Windows 2012"
```

➡ Servidores con Windows Server 2012.

✅ Otro ejemplo:

```
os:"Linux"
```

➡ Todo lo que identifique como Linux.

---

### Comando clave #7: `product:`

✅ Filtra por **producto o servicio** detectado.

✅ Ejemplo:

```
product:"Apache"
```

➡ Servidores web Apache.

✅ Otro ejemplo:

```
product:"MySQL"
```

➡ Bases de datos MySQL expuestas.

---

### Comando clave #8: `version:`

✅ Filtra por **versión específica** de un servicio.

✅ Ejemplo:

```
product:"Apache" version:"2.2.3"
```

➡ Encuentra servidores Apache versión 2.2.3 (¡potencialmente vulnerable!).

✅ Muy usado para:

- Detectar versiones obsoletas.
- Identificar objetivos vulnerables en un pentest.

---

### Comando clave #9: `after:` y `before:`

✅ Filtran resultados por **fecha de detección**.

✅ Ejemplo:

```
after:"2024-01-01"
```

➡ Resultados encontrados después de esa fecha.

✅ Combinado:

```
product:"Apache" country:"PE" after:"2024-01-01"
```

➡ Servidores Apache en Perú **encontrados en 2024**.

✅ Muy útil para:

- Ver cambios recientes en la exposición.

---

### Comando clave #10: `ssl:`

✅ Filtra por **atributos del certificado SSL**.

✅ Ejemplo:

```
ssl.cert.subject.CN:"empresa.com"
```

➡ Encuentra servidores con certificados para `empresa.com`.

✅ Muy usado para:

- Mapear infraestructura.
- Ver certificados válidos/caducados.

---

### Combinando comandos

✅ La **potencia real de Shodan** está en combinarlos.

✅ 🎯 Ejemplo 1 – Buscar SSH en Perú de Telefónica:

```
port:22 country:"PE" org:"Telefonica"
```

✅ 🎯 Ejemplo 2 – Cámaras web en Perú:

```
webcamXP country:"PE"
```

✅ 🎯 Ejemplo 3 – Servidores Apache vulnerables en Perú:

```
product:"Apache" version:"2.2.3" country:"PE"
```

✅ 🎯 Ejemplo 4 – Servidores MySQL en Perú descubiertos en 2024:

```
product:"MySQL" country:"PE" after:"2024-01-01"
```

---

### Tabla de resumen con los principales comandos

| Comando     | Qué hace                                 | Ejemplo                             |
| ----------- | ---------------------------------------- | ----------------------------------- |
| `port:`     | Filtra por puerto                        | `port:22`                           |
| `country:`  | Filtra por país                          | `country:"PE"`                      |
| `city:`     | Filtra por ciudad                        | `city:"Lima"`                       |
| `org:`      | Filtra por organización o ISP            | `org:"Movistar"`                    |
| `hostname:` | Filtra por nombre de dominio             | `hostname:"empresa.com"`            |
| `os:`       | Filtra por sistema operativo             | `os:"Windows 2012"`                 |
| `product:`  | Filtra por producto/servicio             | `product:"Apache"`                  |
| `version:`  | Filtra por versión específica            | `version:"2.2.3"`                   |
| `after:`    | Resultados posteriores a una fecha       | `after:"2024-01-01"`                |
| `before:`   | Resultados previos a una fecha           | `before:"2024-06-01"`               |
| `ssl:`      | Filtra por atributos del certificado SSL | `ssl.cert.subject.CN:"empresa.com"` |

---

### Resultado típico en Shodan

✅ Cuando haces una búsqueda con comandos, Shodan te muestra:

- IP pública.
- País y ciudad.
- ISP (organización).
- Puerto y protocolo.
- Banner del servicio (incluye versión, sistema operativo, etc.).

✅ Ejemplo real:

```
IP: 200.48.120.55
Port: 80
Country: Peru
ISP: Telefonica
Banner:
HTTP/1.1 200 OK
Server: Apache/2.2.22 (Debian)
```

➡ Sabes:

- Puerto abierto (80).
- Software y versión (Apache/2.2.22).
- SO (Debian).

---

### Ejercicio súper fácil para practicar

✔️ Entra en [https://www.shodan.io](https://www.shodan.io).

✔️ Prueba estas búsquedas:

✅ SSH en Perú:

```
port:22 country:"PE"
```

✅ Cámaras en Perú:

```
webcamXP country:"PE"
```

✅ Servidores Apache en Perú:

```
product:"Apache" country:"PE"
```

✅ MySQL en Perú con fecha:

```
product:"MySQL" country:"PE" after:"2024-01-01"
```

---

### Frase clave para recordar

> 🎯 **“Shodan no inventa vulnerabilidades, solo te muestra lo que está expuesto.”**

---

### Resumen corto

✅ **Shodan** es un buscador para dispositivos conectados.

✅ **Comandos** = filtros para afinar resultados.

✅ Los más usados son:

- `port:`
- `country:`
- `org:`
- `product:`
- `version:`
- `hostname:`
- `os:`
- `after:` / `before:`
  ✅ Permiten encontrar **servicios vulnerables** o **mal configurados**.

---

[🔼](#índice)

---

## **10. Censys**

### ¿Qué es Censys?

**Censys** es un **motor de búsqueda especializado** que permite explorar **todos los dispositivos y servicios conectados a Internet**, así como **certificados digitales**.

> 🎯 **Frase fácil:**

> ✅ **“Censys es como Google, pero para Internet de las Cosas y certificados SSL.”**

---

### ¿En qué se parece y se diferencia de Shodan?

✅ Tanto **Censys** como **Shodan** son herramientas OSINT (Open Source Intelligence) para descubrir servicios expuestos en Internet.

✅ Pero:

| Característica    | Shodan                             | Censys                                         |
| ----------------- | ---------------------------------- | ---------------------------------------------- |
| Enfoque principal | Dispositivos y servicios expuestos | Dispositivos y certificados SSL                |
| Datos             | Banners, puertos abiertos          | Banners + información profunda de certificados |
| Uso común         | Auditorías rápidas, descubrimiento | Investigación más estructurada y detallada     |
| Base de datos     | Grande, menos estructurada         | Muy estructurada, fácil de analizar            |

✅ Ambos se usan **para evaluar la exposición y seguridad en Internet**.

---

### ¿Qué información encuentra Censys?

✅ Dispositivos conectados (IP, puertos abiertos, banners).

✅ Certificados digitales (SSL/TLS).

✅ Dominios y subdominios.

✅ Versiones de software expuesto.

---

### ¿Para qué sirve Censys?

✅ Auditorías de seguridad:

- Encontrar servicios expuestos.
- Detectar versiones vulnerables.
- Ver certificados caducados o mal configurados.

✅ Investigación OSINT:

- Mapear la infraestructura de un dominio.
- Analizar certificados y ver qué dominios están asociados.
- Descubrir relaciones entre organizaciones.

✅ Inventario de activos:

- Ver qué tiene tu empresa expuesto en Internet.

---

### ¿Cómo funciona Censys?

✅ Censys **escanea continuamente Internet**.

✅ Recoge **banners** (información sobre servicios en puertos abiertos).

✅ Extrae **certificados digitales**.

✅ Organiza todo en **bases de datos públicas** consultables.

✅ 📌 A diferencia de Google, que indexa páginas web, **Censys indexa dispositivos y certificados**.

---

### Acceso a Censys

✅ Página web:
🔗 [https://search.censys.io](https://search.censys.io)

✅ Tiene:

- Versión gratuita (con límite de búsquedas).
- Planes pagos (para más consultas y datos completos).

✅ También tiene:

- API para automatizar búsquedas.
- CLI para uso en terminal.

---

### Tipos de búsqueda en Censys

✅ **Hosts**: Búsqueda de dispositivos por IP.

✅ **Certificates**: Búsqueda de certificados SSL/TLS.

✅ **Domains**: Búsqueda de dominios.

✅ 📌 ¡Esto es lo que la hace poderosa para investigadores!

---

### Ejemplo 1: Búsqueda de host (IP/dispositivo)

✅ Supongamos que quieres ver qué servicios tiene abierta la IP **200.48.120.55**.

✅ En Censys:

```
ip:200.48.120.55
```

✅ Resultado típico:

- Puertos abiertos (80, 443, 22).
- Servicios corriendo (Apache, SSH).
- Versiones detectadas.
- Certificado SSL (si es HTTPS).

✅ Ejemplo de **banner** en Censys:

```
"service_name": "HTTP",
"port": 80,
"software": "Apache/2.4.29 (Ubuntu)"
```

✅ ¡Muy útil para identificar versiones obsoletas o vulnerables!

---

### Ejemplo 2: Búsqueda de certificados

✅ Supongamos que quieres encontrar **todos los certificados emitidos para empresa.com**.

✅ Búsqueda en Censys:

```
parsed.names: "empresa.com"
```

✅ Resultado típico:

- Certificados válidos o caducados.
- Emisor del certificado (CA).
- Fechas de validez.
- Subdominios incluidos en el SAN.

✅ Ejemplo de resultado:

```
"parsed.subject_dn": "CN=empresa.com",
"parsed.validity.start": "2024-01-01",
"parsed.validity.end": "2025-01-01"
```

✅ ⚡ ¡Genial para mapear la infraestructura de un dominio!

---

### Ejemplo 3: Búsqueda de dominios

✅ Censys también permite buscar **dominios registrados** y detalles sobre sus certificados.

✅ Ejemplo de búsqueda:

```
domain:empresa.com
```

✅ Resultado típico:

- Historial de certificados.
- Subdominios descubiertos.
- Información sobre hosting y DNS.

---

### Comandos principales en Censys (con ejemplos)

Vamos a ver **comandos comunes**, súper sencillos:

---

#### ✅ A. `ip:`

🔎 Busca por dirección IP.

```
ip:200.48.120.55
```

➡ Muestra todos los puertos abiertos y servicios.

---

#### ✅ B. `services.service_name:`

🔎 Filtra por nombre del servicio.

```
services.service_name: "HTTP"
```

➡ Solo resultados con servicio HTTP.

---

#### ✅ C. `services.port:`

🔎 Filtra por puerto.

```
services.port: 22
```

➡ Solo resultados con SSH.

---

#### ✅ D. `location.country:`

🔎 Filtra por país.

```
location.country: "Peru"
```

➡ Dispositivos en Perú.

---

#### ✅ E. `parsed.names:`

🔎 Busca nombres en certificados.

```
parsed.names: "empresa.com"
```

➡ Todos los certificados con ese dominio.

---

#### ✅ F. `parsed.subject_dn:`

🔎 Busca por Subject DN (Nombre Distinguido del Certificado).

```
parsed.subject_dn: "CN=empresa.com"
```

➡ Encuentra certificados con ese Common Name.

---

#### ✅ G. `parsed.validity.start:` y `parsed.validity.end:`

🔎 Filtran por fechas de validez.

```
parsed.validity.start: [2024-01-01 TO 2025-01-01]
```

➡ Certificados emitidos en ese rango.

---

#### ✅ H. Combinación de filtros

✅ Censys es súper potente al combinar:

```
services.port: 443 AND location.country: "Peru" AND services.software: "Apache"
```

➡ Servidores Apache con HTTPS en Perú.

---

### Ejemplo real paso a paso

🎯 Objetivo ficticio: Auditar **empresa.com**.

✅ Paso 1 – Ver servicios en su IP:

```
ip:200.48.120.55
```

➡ Descubre:

- Puertos abiertos (80, 443, 22).
- Apache/2.2.22 (¡viejo!).

---

✅ Paso 2 – Ver sus certificados:

```
parsed.names: "empresa.com"
```

➡ Descubre:

- CN: empresa.com
- SAN: sub1.empresa.com, sub2.empresa.com

---

✅ Paso 3 – Ver subdominios asociados:

```
domain:empresa.com
```

➡ Resultado:

- sub1.empresa.com
- admin.empresa.com

---

✅ Paso 4 – Buscar dispositivos en Perú con HTTPS:

```
services.port: 443 AND location.country: "Peru"
```

➡ Encuentra:

- IPs con HTTPS.
- Información del certificado.
- Versiones del servidor.

---

### Ventajas de Censys

✅ Datos muy estructurados y fáciles de analizar.

✅ Gran foco en certificados → muy útil para OSINT.

✅ Ideal para mapear infraestructura.

✅ API poderosa para análisis masivo.

---

### Limitaciones

⚠️ Límite de búsquedas en la versión gratuita.

⚠️ Puede no cubrir **todos** los dispositivos (depende de los escaneos).

⚠️ No muestra dispositivos que no respondan a los escaneos.

---

### Resumen súper corto

✅ **Censys** = buscador de Internet para **dispositivos** y **certificados**.

✅ Ayuda a encontrar:

- Servicios abiertos y versiones.
- Puertos expuestos.
- Certificados SSL y dominios asociados.

✅ Ideal para:

- Auditorías de seguridad.
- Investigación OSINT.
- Inventario de activos expuestos.

---

### Frase clave para recordar

> 🎯 **“Censys no te dice solo qué está expuesto, te muestra cómo está configurado.”**

---

### Ejercicio súper fácil para ti

✅ Entra en [https://search.censys.io](https://search.censys.io).

✅ Prueba estas búsquedas:

✅ Ver dispositivos en Perú:

```
location.country: "Peru"
```

✅ Buscar Apache en Perú:

```
services.software: "Apache" AND location.country: "Peru"
```

✅ Ver certificados de un dominio:

```
parsed.names: "empresa.com"
```

✅ Buscar SSH en Perú:

```
services.port: 22 AND location.country: "Peru"
```

---

[🔼](#índice)

---

## **11. Whois**

### ¿Qué es WHOIS?

**WHOIS** es un **protocolo y servicio** que permite **consultar información sobre el registro de un dominio o dirección IP** en Internet.

> 🎯 **Frase sencilla:**
>
> ✅ **“WHOIS es como la tarjeta de identidad de un dominio o dirección IP.”**

---

### ¿Para qué sirve WHOIS?

✅ Saber **quién es el propietario** de un dominio.

✅ Ver **cuándo se registró** y **cuándo expira**.

✅ Identificar **datos de contacto** (a veces públicos, a veces privados).

✅ Conocer **el registrador** (empresa donde se compró el dominio).

✅ Investigar **IP** → ver qué organización la posee.

✅ 🎯 Usos comunes:

- Contactar al dueño de un dominio.
- Verificar legitimidad (¿quién está detrás?).
- Investigar en ciberseguridad (OSINT).
- Comprobar fechas de expiración.

---

### ¿Cómo funciona WHOIS?

✅ Existe una **base de datos distribuida** mantenida por **registradores** y **registros** (como Verisign para .com).

✅ Cuando haces una consulta **WHOIS**, el sistema busca en esas bases de datos **la información registrada**.

---

### ¿Qué tipo de datos muestra WHOIS?

✅ Los datos más comunes son:

- **Dominio**: el nombre consultado.
- **Registrar**: empresa donde se registró.
- **Registrant**: nombre del propietario (si no está privado).
- **Fechas**: creación, expiración, última actualización.
- **Servidores DNS**: a dónde apunta el dominio.
- **Estado**: activo, en redención, etc.
- **Contactos**: email, teléfono (a veces ocultos).

✅ ⚠️ IMPORTANTE:

- Muchos datos ahora están **ocultos** por privacidad (GDPR y servicios como Whois Privacy).
- Pero **siempre verás el registrador, fechas, estado y DNS**.

---

### ¿Cómo se hace una consulta WHOIS?

✅ Hay muchas formas:

✅ 🌐 Web:

- [https://whois.domaintools.com](https://whois.domaintools.com)
- [https://www.whois.com/whois/](https://www.whois.com/whois/)
- [https://whois.icann.org](https://whois.icann.org)

✅ 💻 Terminal (Linux o Mac):

```
whois ejemplo.com
```

✅ 💻 En Windows (PowerShell con módulos):

```
whois ejemplo.com
```

✅ 🧩 Herramientas OSINT y frameworks de hacking ético suelen tener módulos WHOIS.

---

### Ejemplo muy fácil de entender

✅ Dominio: **ejemplo.com**

✅ Resultado WHOIS simplificado:

```
Domain Name: EJEMPLO.COM
Registrar: EXAMPLE REGISTRAR INC.
Creation Date: 2000-01-01
Expiration Date: 2030-01-01
Updated Date: 2024-01-01
Name Servers: NS1.EXAMPLE.COM, NS2.EXAMPLE.COM
Status: ACTIVE
Registrant Name: John Doe
Registrant Organization: Example Corp.
Registrant Email: john@example.com
```

✅ Significado:

- **Domain Name:** Nombre del dominio.
- **Registrar:** Empresa donde se compró.
- **Creation Date:** Fecha de registro.
- **Expiration Date:** Hasta cuándo está pagado.
- **Updated Date:** Última vez que se actualizó algo.
- **Name Servers:** A dónde apunta (quién maneja el DNS).
- **Status:** Estado (activo, en redención, etc.).
- **Registrant:** Propietario.

---

### Ejemplo real con privacidad activada

✅ Dominio: **openai.com**

✅ Resultado típico:

```
Domain Name: OPENAI.COM
Registrar: MarkMonitor Inc.
Creation Date: 2015-04-14
Expiration Date: 2032-04-14
Updated Date: 2023-03-12
Name Servers: NS1.P13.DYNECT.NET, NS2.P13.DYNECT.NET
Registrant Organization: Domains By Proxy, LLC
Registrant State/Province: Arizona
Registrant Country: US
```

✅ Observa:

- **La información personal (nombre, email) está oculta** → aparece Domains By Proxy.
- Es un servicio de privacidad que oculta datos reales.
- Pero aún puedes ver **quién es el registrador**, **las fechas**, **DNS**, **estado**.

---

### Ejemplo investigando una IP

✅ WHOIS no es solo para dominios → también sirve para IPs.

✅ Ejemplo: IP **8.8.8.8** (Google DNS)

✅ Resultado simplificado:

```
NetRange: 8.8.8.0 - 8.8.8.255
Organization: Google LLC
Country: US
CIDR: 8.8.8.0/24
```

✅ Significado:

- **NetRange:** Bloque de IPs.
- **Organization:** A quién pertenece (Google).
- **Country:** País.
- **CIDR:** Notación de red.

✅ Muy usado para:

- Identificar dueños de IPs sospechosas.
- Ver a qué proveedor o empresa pertenece un rango.

---

### Ejemplo súper sencillo y práctico

🎯 Imagina que haces un pentest y encuentras:

```
http://inseguro.ejemplo.com
```

✅ Quieres saber quién lo registró:

✅ Buscas en:

```
https://www.whois.com/whois/inseguro.ejemplo.com
```

✅ Resultado:

```
Domain Name: INSEGURO.EJEMPLO.COM
Registrar: Example Registrar
Registrant Organization: EmpresaInsegura SA
Creation Date: 2012-05-20
Expiration Date: 2026-05-20
```

✅ Aprendes:

- Quién es la empresa.
- Cuándo registraron el dominio.
- Hasta cuándo está activo.
- Posible contacto → enviar reporte de vulnerabilidad.

---

### ¿Qué NO muestra WHOIS?

✅ No te dice:

- Dónde está alojada la página físicamente.
- Quién la administra actualmente (si usa privacidad).
- Qué contenido tiene.
- Contraseñas ni datos sensibles.

✅ Es solo **metadatos del registro**.

---

### Usos en Ciberseguridad y OSINT

✅ ✔️ Pentesting:

- Ver quién controla un dominio objetivo.
- Contactar al dueño para responsible disclosure.

✅ ✔️ Investigación:

- Encontrar todos los dominios de una organización.
- Relacionar dominios sospechosos por mismo registrante.

✅ ✔️ Inteligencia de amenazas:

- Atribuir campañas de phishing.
- Ver cuándo se registraron dominios fraudulentos.

✅ ✔️ Red Team:

- Mapear infraestructura de una empresa objetivo.

---

### Servicios que ofrecen WHOIS

✅ Sitios web:

- [whois.com](https://www.whois.com)
- [ICANN WHOIS](https://lookup.icann.org)
- [domaintools.com](https://whois.domaintools.com)

✅ CLI (Linux):

```
whois dominio.com
```

✅ APIs:

- JSON para integrarlo en apps o herramientas.

✅ Herramientas OSINT:

- Maltego.
- Recon-ng.
- Spiderfoot.

---

### Tabla resumen de campos comunes en WHOIS

| Campo            | Descripción                              | Ejemplo                                     |
| ---------------- | ---------------------------------------- | ------------------------------------------- |
| Domain Name      | Nombre del dominio                       | ejemplo.com                                 |
| Registrar        | Empresa donde se compró                  | NameCheap, GoDaddy                          |
| Creation Date    | Fecha de registro                        | 2000-01-01                                  |
| Expiration Date  | Fecha de expiración                      | 2030-01-01                                  |
| Updated Date     | Última actualización                     | 2024-01-01                                  |
| Status           | Estado del dominio                       | active, clientHold, redemptionPeriod        |
| Name Servers     | Servidores DNS asociados                 | ns1.ejemplo.com, ns2.ejemplo.com            |
| Registrant       | Nombre del dueño (si no usa privacidad)  | John Doe, Empresa SA                        |
| Registrant Email | Email de contacto (si no usa privacidad) | [john@ejemplo.com](mailto:john@ejemplo.com) |
| Organization     | Organización dueña del dominio           | Example Corp.                               |

---

### Frase clave para recordar

> 🎯 **“WHOIS no te dice qué hay en la web, te dice quién la registró y cómo contactarlo.”**

---

### Ejercicio fácil para ti

✅ Ve a [https://www.whois.com/whois/](https://www.whois.com/whois/)

✅ Prueba estas consultas:

✅ Dominio famoso:

```
openai.com
```

✅ Dominio local o tuyo:

```
tunombre.com
```

✅ IP famosa:

```
8.8.8.8
```

✅ Observa:

- Quién es el registrador.
- Cuándo se creó.
- Cuándo expira.
- Quién es el dueño (si no está privado).

---

### Resumen súper corto

✅ **WHOIS** es un servicio para consultar **datos de registro** de dominios o IPs.

✅ Te muestra **quién**, **cuándo**, **dónde** y **cómo contactarlos**.

✅ Es clave para **OSINT** y **ciberseguridad**.

✅ Es **gratuito** y **legal** → solo muestra datos públicos.

---

[🔼](#índice)

---

## **12. Archive: Análisis de información histórica**

### ¿Qué es "Archive" en este contexto?

En el contexto de **OSINT (Inteligencia de fuentes abiertas)** y **ciberseguridad**, "Archive" se refiere al uso de **servicios que guardan versiones antiguas o pasadas de sitios web** o información digital, para analizarlas con fines de investigación, auditoría o pruebas.

> 🎯 **Frase clave:**

> **“Archive te permite ver cómo era un sitio web o dominio en el pasado.”**

---

### ¿Para qué sirve el análisis histórico de información?

✅ Muy útil en investigaciones de:

- **Phishing** o estafas (ver versiones pasadas maliciosas de un sitio).
- **Pérdida de datos** (recuperar contenido eliminado).
- **Evolución de una empresa o atacante** (cambios en su web).
- **Pruebas forenses**.
- **Red team/pentesting** (descubrir subdominios, correos, paths antiguos).

---

### Herramienta principal: **Wayback Machine (archive.org)**

✅ Es una **biblioteca digital gratuita** que **guarda capturas de páginas web** a lo largo del tiempo.

🔗 [https://archive.org/web](https://archive.org/web)

---

### ¿Qué es la Wayback Machine?

✅ Es un servicio de la organización **Internet Archive** que permite:

- Ver **versiones antiguas** de páginas web.
- Descargar contenido eliminado.
- Comparar cambios a lo largo del tiempo.

> 📅 Se han archivado miles de millones de páginas desde 1996.

---

### ¿Cómo funciona?

✅ La Wayback Machine hace **capturas automáticas** de sitios web periódicamente.

✅ También puedes **forzar un guardado manual** usando la opción “Save Page Now”.

---

### ¿Qué información puedes obtener?

✅ Ejemplos:

- ¿Qué había en la página principal de una empresa en 2015?
- ¿Qué URL tenía el login de empleados antes?
- ¿Qué correos de contacto usaban antes?
- ¿Qué scripts o archivos JS usaban?

---

### Ejemplo real paso a paso

🎯 Objetivo: Investigar un dominio sospechoso → `sitiowebfraudulento.com`

#### 🔎 Paso 1: Ir a

👉 [https://archive.org/web](https://archive.org/web)

#### 🔎 Paso 2: Escribir el dominio

```
sitiowebfraudulento.com
```

#### 🔎 Paso 3: Ver el **timeline de capturas**

Verás un calendario con años y días resaltados (días donde se hizo captura).

###3 🔎 Paso 4: Elegir una fecha (por ejemplo, 2020)

✅ Resultado:

- En 2020, ese sitio mostraba una tienda falsa con pago por criptomonedas.
- En 2024, ya no existe.

✅ Conclusión: ¡Era usado para estafa en el pasado!

---

### ¿Qué puedes encontrar útil para pentesting o OSINT?

| Elemento             | ¿Por qué es útil?                                         |
| -------------------- | --------------------------------------------------------- |
| URLs antiguas        | Te ayudan a encontrar rutas escondidas (ej: `/admin-old`) |
| Formularios          | Puedes ver campos expuestos antes (email, password)       |
| Correos de contacto  | Para rastrear empleados antiguos                          |
| Scripts o recursos   | Ver JS externos → posible tracking o vulnerabilidades     |
| Cambios de contenido | Identificar actividad sospechosa o encubrimientos         |
| Subdominios          | Puede revelar `blog.ejemplo.com`, `dev.ejemplo.com`       |
| Tecnología utilizada | Ver qué CMS, librerías, plugins usaban antes              |

---

### Casos prácticos fáciles de entender

#### 🕵️‍♂️ Caso 1: Red team

✅ El dominio actual no tiene login visible.

✅ Pero en la Wayback Machine ves que en 2021 existía `/login.php`.

➡ Puedes probar si sigue funcionando aunque no esté enlazado.

---

#### 🕵️‍♂️ Caso 2: Phishing

✅ Sitio fraudulento eliminado, pero alguien guardó una copia en 2023.

✅ Ves:

- Logotipo clonado.
- Botón de "Iniciar sesión".
- URL falsa parecida a un banco.

➡ Pruebas perfectas para un informe de fraude.

---

#### 🕵️‍♂️ Caso 3: Buscar emails

✅ En la versión 2018 de una página de contacto, ves:

```
soporte@empresaantigua.com
```

➡ Útil para rastrear relaciones o para spear phishing en pentests.

---

#### 🕵️‍♂️ Caso 4: Cazando vulnerabilidades antiguas

✅ En 2019, una página tenía:

```html
<script src="http://inseguro.servidor.com/hack.js"></script>
```

➡ ¡Malware o recurso comprometido!

---

### ¿Qué otras herramientas similares a Archive.org existen?

| Herramienta             | Función principal                                    | Enlace                                         |
| ----------------------- | ---------------------------------------------------- | ---------------------------------------------- |
| **Archive.today**       | Guarda copias exactas de páginas (incluye JS render) | [https://archive.today](https://archive.today) |
| **Google Cache**        | Versión en caché de páginas indexadas                | Usar operador `cache:dominio.com`              |
| **Wayback Machine CLI** | Ver capturas desde línea de comandos                 | [GitHub - wayback](https://github.com)         |

---

### ¿Cómo guardar una página manualmente?

✅ Ir a:
🔗 [https://archive.org/web](https://archive.org/web)

✅ En el campo de abajo, poner URL y darle clic a “**Save Page Now**”.

✅ Útil para:

- Documentar incidentes.
- Probar que algo estaba publicado antes.

---

### Ventajas del análisis histórico

✅ Ver contenido eliminado.

✅ Rastrear actividad maliciosa o sospechosa.

✅ Mapear rutas y cambios en sitios web.

✅ Recopilar evidencia en informes forenses o legales.

✅ Rastrear actividad de atacantes o campañas antiguas.

---

### Limitaciones

⚠️ No todos los sitios están archivados (especialmente si usan `robots.txt` para bloquear crawlers).

⚠️ No siempre carga bien CSS o JS.

⚠️ No se pueden usar formularios antiguos (son solo capturas).

⚠️ No incluye contenido de login o secciones privadas.

---

### Frase clave para recordar

> 🧠 **"Lo que fue público en Internet... puede seguir vivo en Archive.org."**

---

### Ejercicio práctico para ti

🎯 Entra a 👉 [https://archive.org/web](https://archive.org/web)

1. Busca tu dominio favorito (ej: `elcomercio.pe`).
2. Elige un año (ej: 2010).
3. Observa:

   - ¿Cómo era el diseño?
   - ¿Qué información aparecía que hoy ya no?
   - ¿Había rutas o correos visibles?

¡Es divertido y educativo!

---

### Resumen corto

✅ **Archive.org (Wayback Machine)** es una herramienta que **almacena capturas históricas de sitios web**.

✅ Sirve para:

- Análisis forense.
- OSINT y ciberseguridad.
- Rastrear cambios o estafas.

✅ Útil para pentesters, periodistas, investigadores, abogados y usuarios curiosos.

---

[🔼](#índice)

---

## **13. TheHarvester**

### ¿Qué es TheHarvester?

**TheHarvester** es una **herramienta de OSINT** (Open Source Intelligence) usada para **recopilar información pública** sobre:

✅ Correos electrónicos.

✅ Nombres de empleados.

✅ Subdominios.

✅ Direcciones IP.

✅ Hosts (servidores).

> 🎯 **Frase fácil de recordar:**

> **“TheHarvester busca en Internet lo que está públicamente disponible sobre un objetivo.”**

---

### ¿Para qué sirve?

✅ Etapa de **reconocimiento** en hacking ético.

✅ Recopilar información **antes** de un pentest.

✅ Mapear la **superficie de ataque**.

✅ Preparar **ataques dirigidos** (Red Team).

✅ Generar **listas de objetivos** para phishing o ingeniería social (con fines éticos).

---

### ¿Cómo funciona TheHarvester?

✅ Usa **fuentes públicas**: motores de búsqueda, redes sociales, bases de datos de certificados, etc.

✅ Hace **consultas automatizadas** para recolectar datos.

✅ No explota vulnerabilidades → solo busca **lo que ya es público**.

> ✅ Es **LEGAL** si se usa para auditorías autorizadas o investigaciones OSINT.

---

### Principales fuentes que usa

✅ Google.

✅ Bing.

✅ DuckDuckGo.

✅ Yahoo.

✅ Baidu.

✅ LinkedIn (limitado).

✅ Hunter.io (con API).

✅ Shodan.

✅ crt.sh (certificados SSL).

✅ DNS Dumpster.

✅ ¡Y más! → Puedes elegir la fuente con un parámetro.

---

### ¿Qué puedes encontrar?

✅ Ejemplo de **resultados**:

| Tipo de dato        | Ejemplo                                                 |
| ------------------- | ------------------------------------------------------- |
| Email               | [juan.perez@empresa.com](mailto:juan.perez@empresa.com) |
| Subdominio          | vpn.empresa.com                                         |
| IP                  | 192.0.2.15                                              |
| Nombre de host      | mail.empresa.com                                        |
| Dominio relacionado | partners.empresa.com                                    |

✅ Muy útil para **mapear objetivos**.

---

### Instalación sencilla (Linux)

✅ La mayoría de distros lo tienen en repositorios o se instala desde GitHub:

```bash
git clone https://github.com/laramies/theHarvester.git
cd theHarvester
pip install -r requirements.txt
```

✅ Para Kali Linux:

```bash
sudo apt install theharvester
```

✅ Ya viene preinstalado en muchas distros de pentesting.

---

### Comando básico

✅ Forma general:

```
theHarvester -d <dominio> -b <fuente>
```

✅ Parámetros:

- `-d`: Dominio objetivo.
- `-b`: Fuente (motor de búsqueda o API).

✅ Ejemplo muy sencillo:

```
theHarvester -d empresa.com -b google
```

➡ Busca información sobre `empresa.com` usando Google.

---

### Ejemplo súper práctico

🎯 **Objetivo:** Encontrar emails y subdominios públicos de `empresa.com`

✅ Comando:

```
theHarvester -d empresa.com -b bing
```

✅ Resultado ficticio:

```
[*] Emails found:
- juan.perez@empresa.com
- soporte@empresa.com

[*] Hosts found:
- vpn.empresa.com
- mail.empresa.com
- intranet.empresa.com
```

✅ Significado:

- Ahora sabes **emails de empleados** → posible vector de phishing.
- Conoces **subdominios** → nuevos objetivos para escaneo.

---

### Uso con múltiples fuentes

✅ Puedes combinar varias fuentes para resultados más completos.

✅ Ejemplo:

```
theHarvester -d empresa.com -b google,bing,duckduckgo
```

✅ Resultado:

- Más emails.
- Más subdominios.
- Información más rica.

---

### Buscar en bases de datos de certificados (crt.sh)

✅ crt.sh guarda **certificados SSL/TLS públicos**.

✅ Muchos certificados incluyen **subdominios**.

✅ Ejemplo:

```
theHarvester -d empresa.com -b crtsh
```

✅ Resultado:

```
vpn.empresa.com
admin.empresa.com
secure.empresa.com
```

✅ Muy útil para **descubrir infraestructura oculta**.

---

### Guardar resultados en archivo

✅ Puedes exportar en texto plano o HTML.

✅ Ejemplo para HTML:

```
theHarvester -d empresa.com -b google -f resultado
```

✅ Genera:

```
resultado.html
```

✅ Puedes abrirlo en tu navegador.

---

### Parámetros comunes y fáciles de usar

| Parámetro | Significado                                  | Ejemplo          |
| --------- | -------------------------------------------- | ---------------- |
| `-d`      | Dominio objetivo                             | `-d empresa.com` |
| `-b`      | Fuente o motor de búsqueda                   | `-b google`      |
| `-l`      | Límite de resultados                         | `-l 100`         |
| `-f`      | Nombre de archivo de salida                  | `-f reporte`     |
| `-v`      | Verbose / Salida detallada                   | `-v`             |
| `-h`      | Ayuda / ver todos los parámetros disponibles | `-h`             |

---

### Caso de uso real paso a paso

✅ **Escenario:** Eres pentester contratado por `empresa.com`.

✅ **Objetivo:** Recopilar emails y subdominios públicos.

✅ **Comando:**

```
theHarvester -d empresa.com -b google,bing,crtsh -l 200 -f informe_empresa
```

✅ Resultado:

```
[*] Emails found:
- juan.perez@empresa.com
- maria.gomez@empresa.com

[*] Hosts found:
- vpn.empresa.com
- admin.empresa.com
- webmail.empresa.com
```

✅ Ahora puedes:

- Usar emails para simular phishing (con permiso).
- Escanear subdominios con nmap o nikto.
- Incluir resultados en tu **reporte de hallazgos**.

---

### Limitaciones de TheHarvester

⚠️ No hace explotación → **solo recolecta**.

⚠️ Depende de **fuentes públicas** → si algo está bien oculto, no lo encontrará.

⚠️ Puede tener **falsos positivos**.

⚠️ Motores de búsqueda pueden **bloquear IPs** por exceso de consultas.

---

### Frase clave para recordar

> 🎯 **"TheHarvester no hackea. Solo recolecta lo que ya es público."**

---

### Ejercicio súper fácil para ti

✅ Si tienes Linux o Kali, prueba:

```
theHarvester -d openai.com -b google
```

✅ Mira:

- Emails públicos.
- Subdominios.

✅ Observa los resultados → ¿qué tan expuesta está la organización?

---

### Resumen corto

✅ **TheHarvester** = herramienta OSINT para **reconocimiento pasivo**.

✅ Encuentra:

- Emails.
- Subdominios.
- IPs.

  ✅ Usa fuentes públicas como Google, Bing, crt.sh.

  ✅ Muy útil para:

- Pentesting.
- Red Team.
- Investigación OSINT.

---

[🔼](#índice)

---

## **14. Bloqueo temporal de dirección IP pública**

### ¿Qué es una dirección IP pública?

✅ Una **dirección IP pública** es el número único que identifica a tu dispositivo o red en Internet.

> 🎯 **Ejemplo fácil:**

> Tu dirección IP pública es como la **dirección de tu casa** en Internet.

> Así los servidores saben **a dónde enviar la información** que pides.

✅ Ejemplo real de IP pública:

```
181.65.120.34
```

---

### ¿Qué significa "bloqueo de IP"?

✅ Significa **impedir el acceso** de esa dirección IP a un servidor o servicio.

✅ Cuando tu IP está **bloqueada**, ya **no puedes conectarte** (o se limita tu acceso).

> 📌 Es como **poner un candado en la puerta** para que un visitante no pueda entrar.

---

### ¿Qué es un **bloqueo temporal** de IP?

✅ Es un bloqueo **solo por un tiempo definido**.

✅ Pasado ese tiempo, **se levanta el bloqueo automáticamente** y puedes volver a acceder.

> 🎯 **Ejemplo fácil:**

> ✅ “Te castigo por 10 minutos y después puedes volver.”

---

### ¿Por qué se usa el bloqueo temporal de IP?

✅ Para proteger servicios de:

- Ataques de fuerza bruta.
- Accesos sospechosos o repetidos.
- Bots o scrapers agresivos.
- Usuarios que violan reglas.

✅ En lugar de **bloquear permanentemente**, se **limita por un período**.

✅ Es más **flexible** y **justo** (permite volver a intentarlo después).

---

### Ejemplo fácil de la vida real

✅ Imagina un sistema de **login en un sitio web**:

- Intentas entrar 5 veces con contraseña incorrecta.
- El servidor **bloquea tu IP por 15 minutos**.

➡ Resultado:

- Evita ataques de fuerza bruta.
- Pero no te bloquea para siempre → puedes volver a intentarlo más tarde.

---

### ¿Cómo funciona técnicamente?

✅ El servidor o firewall tiene reglas para detectar:

- Número de intentos fallidos.
- Tasa de peticiones por segundo/minuto.
- Firmas de comportamiento malicioso.

✅ Cuando se supera el límite:

➡ La IP se agrega a una “lista de bloqueo” (ban list).

➡ Esa lista tiene **una expiración** (por ejemplo, 10 minutos).

✅ Después de ese tiempo:

➡ La IP se **elimina de la lista** automáticamente.

➡ El acceso se restablece.

---

### Ejemplo técnico sencillo (pseudocódigo)

✅ Un sistema de login:

```
if intentos_fallidos > 5:
    bloquear_IP(usuario_IP, tiempo=15 minutos)
```

✅ Resultado:

- Bloquea la IP durante 15 minutos.
- Evita más intentos durante ese tiempo.

---

### ¿Dónde se implementa el bloqueo temporal?

✅ En muchos niveles:

✅ 🔒 **Aplicaciones web**

- Bloquean IPs tras muchos intentos de login fallidos.

✅ 🔒 **Firewalls**

- Detectan muchas peticiones y bloquean temporalmente.

✅ 🔒 **Servidores SSH**

- Herramientas como Fail2ban bloquean IPs con intentos fallidos de acceso.

✅ 🔒 **APIs**

- Limitan llamadas excesivas de una misma IP.

---

### Ejemplo real con **Fail2ban** (Linux)

✅ **Fail2ban** es una herramienta que lee logs en busca de actividad maliciosa.

✅ Ejemplo de configuración:

```
[sshd]
enabled = true
port = ssh
filter = sshd
logpath = /var/log/auth.log
maxretry = 5
bantime = 600
```

✅ Explicación:

- **maxretry = 5** → 5 intentos fallidos.
- **bantime = 600** → bloqueo por 600 segundos (10 minutos).

✅ Resultado:
➡ Después de 5 intentos fallidos → **IP bloqueada 10 minutos**.

---

### Otro ejemplo práctico (Cloudflare)

✅ Cloudflare → protege webs de ataques.

✅ Puedes configurar reglas:

- Si una IP hace 1000 solicitudes en 1 minuto → bloquearla 10 minutos.

✅ Resultado:

➡ Mitiga ataques DDoS.

➡ Los usuarios legítimos pueden volver luego.

---

### Ejemplo de mensaje típico para usuario bloqueado

✅ Si intentas acceder mientras estás bloqueado, podrías ver:

```
403 Forbidden
Your IP has been temporarily blocked due to suspicious activity.
Please try again in 15 minutes.
```

✅ Es una forma clara de avisar al usuario.

---

### Ventajas del bloqueo temporal de IP

✅ 🔹 Evita ataques automatizados.

✅ 🔹 No castiga para siempre a usuarios legítimos.

✅ 🔹 Ayuda a gestionar picos de tráfico.

✅ 🔹 Fácil de implementar.

---

### Desventajas o limitaciones

⚠️ Usuarios con IP dinámica pueden cambiarla para saltar el bloqueo.

⚠️ En redes compartidas (cafés, empresas), puedes afectar a varios usuarios legítimos.

⚠️ Atacantes avanzados pueden usar proxies o VPN para evadirlo.

---

### Tabla resumen sencilla

| Característica     | Bloqueo permanente                | Bloqueo temporal                      |
| ------------------ | --------------------------------- | ------------------------------------- |
| Duración           | Indefinida                        | Limitada (ej: 10-60 minutos)          |
| Flexibilidad       | Baja                              | Alta                                  |
| Impacto a usuarios | Puede castigar usuarios legítimos | Menor riesgo de falsos positivos      |
| Usos comunes       | IPs maliciosas confirmadas        | Prevención de fuerza bruta / scrapers |

---

### Frase clave para recordar

> 🎯 **“El bloqueo temporal de IP es como un time-out para comportamientos sospechosos.”**

---

### Ejercicio fácil para ti

✅ Piensa en tu aplicación o página favorita:

➡ ¿Qué pasaría si alguien intenta 1000 inicios de sesión por minuto?

➡ ¿Cómo podría ayudar un bloqueo temporal?

✅ Reflexiona:

- ¿Qué tiempo de bloqueo sería adecuado?
- ¿Cómo evitarías castigar a usuarios legítimos?

---

### ✅ 17️⃣ Resumen súper corto

✅ Bloqueo temporal de IP = impedir acceso **por un tiempo limitado**.

✅ Sirve para **proteger contra ataques** como fuerza bruta o scraping excesivo.

✅ Es **flexible** y **reduce el impacto** en usuarios legítimos.

✅ Se usa en:

- Aplicaciones web.
- Firewalls.
- APIs.
- Servidores SSH.

---

[🔼](#índice)

---

## **15. Maltego**

### ¿Qué es Maltego?

**Maltego** es una **herramienta de OSINT (Open Source Intelligence)** y **análisis de enlaces**.

> 🎯 **Frase sencilla:**

> ✅ **“Maltego es como un mapa visual para investigar relaciones en Internet.”**

✅ Permite **encontrar, recopilar y visualizar conexiones** entre:

- Personas
- Direcciones de correo electrónico
- Números de teléfono
- Direcciones IP
- Dominios
- Redes sociales
- Organizaciones
- Infraestructura técnica

---

### ¿Para qué sirve?

✅ Investigar **amenazas cibernéticas**

✅ Hacer **perfilamiento** de objetivos (personas o empresas)

✅ Mapear **infraestructura de redes**

✅ Detectar **relaciones ocultas**

✅ Preparar **informes de inteligencia**

✅ Usado por:

- Pentesters
- Investigadores OSINT
- Periodistas
- Policías y agencias de seguridad

---

### Idea básica: "Entidades y relaciones"

✅ Maltego trabaja con **entidades** (nodos) conectadas por **relaciones** (líneas).

> 📌 **Ejemplo fácil:**

> ✅ Entidad: un correo electrónico

> ✅ Entidad: un dominio

> ✅ Relación: “este correo está registrado en este dominio”

✅ Visualmente → un grafo:

```
[correo] ———> [dominio]
```

---

### ¿Cómo funciona Maltego?

✅ Tú comienzas con **un dato inicial** (semilla):

- Un nombre
- Un dominio
- Una IP
- Un correo
- Un hashtag

✅ Luego aplicas **transforms**:

➡ Son **búsquedas automáticas** en fuentes públicas o APIs.

➡ Cada transform encuentra **datos relacionados**.

✅ Resultado:

- Un mapa visual **con nodos y enlaces**.
- Puedes explorar las conexiones **en profundidad**.

---

### Ejemplo súper fácil

✅ Imagínate que investigas:

```
ejemplo.com
```

✅ Maltego hace transforms:

- Descubre subdominios (vpn.ejemplo.com, mail.ejemplo.com)
- Encuentra direcciones IP de esos subdominios
- Relaciona IPs con ubicaciones geográficas
- Busca correos públicos asociados
- Encuentra certificados SSL con subdominios

✅ Resultado:

✅ Un grafo donde ves **toda la infraestructura** de ejemplo.com.

---

### ¿Qué son los **Transforms**?

✅ Son scripts o funciones que **extraen datos públicos**.

✅ Maltego tiene cientos de transforms integrados.

✅ Ejemplos de transforms:

- Obtener subdominios de un dominio
- Resolver IPs de dominios
- Buscar en bases de datos de filtrado de spam
- Consultar Shodan para servicios abiertos
- Obtener datos de Whois
- Buscar correos en filtraciones de datos
- Ver perfiles de redes sociales

✅ Muchos transforms son **gratuitos**. Otros requieren **APIs** o licencias.

---

### Fuentes de datos

✅ Maltego busca en:

- Motores de búsqueda (Google, Bing)
- WHOIS
- Shodan
- Censys
- HaveIBeenPwned
- Redes sociales (Twitter, Facebook)
- DNS
- Certificados SSL (crt.sh)
- Bases de datos de filtraciones

---

### ¿Qué se puede investigar con Maltego?

✅ 🕵️‍♂️ Investigación personal

- Emails asociados
- Redes sociales
- Dominios comprados
- Números de teléfono

✅ 🏢 Investigación de empresas

- Subdominios
- IPs de servidores
- Empleados públicos en LinkedIn
- Brechas de seguridad conocidas

✅ 🌐 Infraestructura técnica

- Servicios abiertos (SSH, HTTP)
- Certificados SSL
- Bloques de IP

✅ 📌 Redes criminales

- Correlacionar direcciones Bitcoin
- Ver redes de phishing

---

### Ejemplo práctico paso a paso

🎯 **Escenario:** Quieres investigar `acme-corp.com`

✅ Paso 1️⃣

- Abres Maltego
- Creas un nuevo grafo
- Agregas la entidad “Domain” con valor `acme-corp.com`

✅ Paso 2️⃣

- Aplicas transforms:

  - To DNS Name → obtiene subdominios
  - To IP Address → resuelve IPs
  - To WHOIS Record → obtiene registrador, fechas

✅ Resultado:

```
[acme-corp.com]
  |
  |-- vpn.acme-corp.com (IP: 192.0.2.10)
  |
  |-- mail.acme-corp.com (IP: 192.0.2.11)
  |
  |-- WHOIS → Registrado por John Doe
```

✅ Paso 3️⃣

- Aplicas transforms para:

  - Buscar emails en filtraciones
  - Ver puertos abiertos en Shodan

✅ Resultado:

```
vpn.acme-corp.com → puerto 22 abierto (SSH)
mail.acme-corp.com → puerto 25 (SMTP)
Emails filtrados:
- admin@acme-corp.com
- soporte@acme-corp.com
```

✅ Paso 4️⃣

- Exportas el grafo como PDF o imagen
- Lo usas en tu informe

---

### Ejemplo real para personas

✅ Empiezas con:

```
Juan Perez (entidad Person)
```

✅ Transforms:

- Search for Email Address
- Search for Social Profiles

✅ Resultado:

```
Juan Perez
  |
  |-- juan.perez@gmail.com
  |-- Twitter: @juanperez
  |-- LinkedIn: /in/juanperez
```

✅ Muy útil para:

- Ingeniería social
- Verificar identidades

---

### Interfaz visual (Grafo)

✅ El resultado en Maltego **no es solo texto**.

✅ Es **un grafo interactivo**:

✅ Ejemplo:

```
[juan.perez@gmail.com]
  |
  |-- [LinkedIn Profile]
  |
  |-- [Facebook Profile]
  |
  |-- [Dominio registrado]
```

✅ Puedes:

- Arrastrar nodos
- Agrupar
- Filtrar
- Exportar imágenes o PDFs

---

### Versiones de Maltego

✅ **Maltego CE (Community Edition)**

- Gratuita
- Limitada (ej. menos resultados por transform)

✅ **Maltego Classic/Pro/Enterprise**

- Licencia de pago
- Más resultados
- Colaboración en equipo

✅ **Maltego CaseFile**

- Gratuita
- Solo para grafo manual (sin transforms automáticos)

---

### Ventajas

✅ 🎯 Muy visual → fácil de entender relaciones.

✅ 🎯 Muchas fuentes de datos.

✅ 🎯 Automatiza consultas que tomarían horas.

✅ 🎯 Útil en OSINT, pentesting, forense, periodismo.

---

### Desventajas

⚠️ Puede generar **mucho ruido** (datos irrelevantes).

⚠️ Algunas fuentes requieren **API keys o pago**.

⚠️ Limitaciones en la edición gratuita (menos resultados).

⚠️ Necesita **conexión a Internet** para la mayoría de transforms.

---

### Frase clave para recordar

> 🎯 **"Maltego no adivina: solo conecta datos públicos para mostrar relaciones."**

---

### Ejercicio fácil para ti

✅ Descarga Maltego CE (gratis):
🔗 [https://www.maltego.com/downloads/](https://www.maltego.com/downloads/)

✅ Prueba con:

```
- Un dominio que te interese (ejemplo.com)
- Un correo (si tienes permiso)
- Tu nombre
```

✅ Aplica transforms:

- To Email Address
- To DNS Name
- To IP Address
- To Social Profiles

✅ Observa el grafo:

- ¿Qué conexiones aparecen?
- ¿Qué descubriste que no sabías?

---

### Resumen súper corto

✅ **Maltego** = herramienta OSINT para **mapear conexiones** entre datos.

✅ Usa **transforms** → consultas automáticas a fuentes públicas.

✅ Resultados = **grafos visuales** fáciles de analizar.

✅ Sirve para:

- Pentesting
- Red Team
- OSINT
- Periodismo de investigación
- Forense digital

---

[🔼](#índice)

---

## **16. Recon-ng**

### ¿Qué es Recon-ng?

**Recon-ng** es una herramienta de **OSINT** (Open Source Intelligence) que ayuda a **automatizar la recolección de información** sobre un objetivo.

> 🎯 **Frase sencilla:**

> ✅ **“Recon-ng es como un laboratorio de OSINT en la terminal.”**

✅ Es similar a **Metasploit**, pero para **reconocimiento**:

- Tiene **módulos** que puedes cargar.
- Cada módulo hace tareas específicas de recolección.
- Guarda resultados en una **base de datos interna**.

---

### ¿Para qué sirve Recon-ng?

✅ Etapa de **reconocimiento** en hacking ético.

✅ Descubrir **información pública** sobre:

- Dominios
- Subdominios
- Emails
- Hosts
- Direcciones IP
- Usuarios de redes sociales

✅ Automatiza búsquedas **manuales** que tomarían mucho tiempo.

---

### ¿Cómo funciona?

✅ Tiene **módulos** para tareas específicas:

- WHOIS
- Google dorking
- DNS bruteforce
- Buscadores de subdominios
- Brechas de datos (HaveIBeenPwned)
- APIs (Shodan, Censys, Bing)

✅ **Base de datos interna**: guarda los hallazgos para usarlos en otros módulos.

✅ Puedes **encadenar módulos** → hacer workflows completos.

---

### Idea básica (muy fácil de entender)

✅ Tú le das **un dato inicial** (semilla):

```
example.com
```

✅ Luego cargas módulos:

- Buscar WHOIS → obtiene datos de registro.
- Buscar subdominios → descubre \*.example.com.
- Resolver IPs → obtiene direcciones IP.
- Buscar correos en filtraciones → obtiene emails filtrados.

✅ Resultado:

➡ Una **base de datos organizada** con toda la info recolectada.

---

### ¿Cómo se instala?

✅ En Kali Linux suele venir preinstalado.

✅ O puedes instalarlo en cualquier Linux:

```bash
git clone https://github.com/lanmaster53/recon-ng.git
cd recon-ng
pip install -r REQUIREMENTS
python3 recon-ng
```

✅ Al ejecutarlo verás su **consola interactiva** parecida a Metasploit:

```
[recon-ng][default] >
```

---

### Flujo de trabajo típico

✅ Paso 1️⃣ Crear workspace

```
workspaces create test
```

✅ Es como un **proyecto separado**.

✅ Paso 2️⃣ Insertar dominio

```
add domains example.com
```

✅ Añades tu objetivo.

✅ Paso 3️⃣ Listar módulos

```
modules search
```

✅ Verás todos los módulos disponibles.

✅ Paso 4️⃣ Usar un módulo

```
modules load recon/domains-hosts/bing_domain_web
```

✅ Paso 5️⃣ Configurar opciones

```
options set SOURCE example.com
```

✅ Paso 6️⃣ Ejecutar módulo

```
run
```

✅ ¡Listo! Los resultados quedan guardados en la base de datos.

---

### ¿Qué tipo de módulos existen?

✅ Recon-ng tiene **muchos módulos**.

Ejemplos:

| Tipo                | Ejemplo de módulo                         | Qué hace                            |
| ------------------- | ----------------------------------------- | ----------------------------------- |
| WHOIS               | recon/domains-contacts/whois_pocs         | Información de registro             |
| Motores de búsqueda | recon/domains-hosts/bing_domain_web       | Encuentra subdominios con Bing      |
| DNS                 | recon/domains-hosts/brute_hosts           | Fuerza subdominios                  |
| Certificados SSL    | recon/domains-hosts/crtsh                 | Busca subdominios en certificados   |
| Brechas de datos    | recon/contacts-credentials/haveibeenpwned | Verifica si emails fueron filtrados |
| IP geolocalización  | recon/hosts-locations/ipinfodb            | Ubicación aproximada de IPs         |
| Shodan              | recon/hosts-hosts/shodan_hostname         | Servicios abiertos en host          |

---

### Ejemplo súper fácil de entender

🎯 **Objetivo:** `acme-corp.com`

✅ 1️⃣ Abrir Recon-ng

```
python3 recon-ng
```

✅ 2️⃣ Crear workspace

```
workspaces create acme
```

✅ 3️⃣ Añadir dominio

```
add domains acme-corp.com
```

✅ 4️⃣ Buscar módulos para subdominios

```
modules search hosts
```

✅ Resultado:

```
recon/domains-hosts/bing_domain_web
recon/domains-hosts/crtsh
recon/domains-hosts/brute_hosts
```

✅ 5️⃣ Usar crt.sh para subdominios en certificados

```
modules load recon/domains-hosts/crtsh
options set SOURCE acme-corp.com
run
```

✅ Resultado:

```
Found subdomains:
- vpn.acme-corp.com
- mail.acme-corp.com
- admin.acme-corp.com
```

✅ 6️⃣ Resolver IPs

```
modules load recon/hosts-hosts/resolve
options set SOURCE default
run
```

✅ Resultado:

```
vpn.acme-corp.com → 192.0.2.12
mail.acme-corp.com → 192.0.2.13
```

✅ 7️⃣ Buscar correos filtrados

```
modules load recon/contacts-credentials/haveibeenpwned
options set SOURCE acme-corp.com
run
```

✅ Resultado:

```
- juan.perez@acme-corp.com was found in 3 breaches
```

---

### Resultado final (muy claro)

Después de unos comandos tienes:

✅ Subdominios:

- vpn.acme-corp.com
- mail.acme-corp.com
- admin.acme-corp.com

✅ IPs:

- 192.0.2.12
- 192.0.2.13

✅ Emails filtrados:

- [juan.perez@acme-corp.com](mailto:juan.perez@acme-corp.com) (comprometido)

✅ Puedes **exportar** los datos para tu informe.

---

### Ventajas

✅ Muy organizado → usa base de datos.

✅ Modular → muchos tipos de búsquedas.

✅ Automatiza tareas repetitivas.

✅ Gratuito y open source.

✅ Ideal para pentesting profesional.

---

### Desventajas

⚠️ Requiere aprendizaje → consola no gráfica.

⚠️ Algunas APIs requieren clave (Shodan, Bing).

⚠️ Puede generar datos ruidosos → hay que filtrar.

⚠️ No explota vulnerabilidades → solo recolecta.

---

### Frase clave para recordar

> 🎯 **“Recon-ng es un cuchillo suizo para recolectar información pública de forma ordenada.”**

---

### Resumen súper corto

✅ **Recon-ng** = Framework OSINT en terminal.

✅ Usa **módulos** para:

- WHOIS
- Subdominios
- DNS
- Brechas de datos
- APIs como Shodan

✅ Organiza resultados en base de datos.

✅ Es **automatizable** y muy útil en pentesting.

---

### Ejercicio fácil para ti

Si quieres probar:

✅ En Kali o Linux:

```
recon-ng
```

✅ Luego:

```
workspaces create demo
add domains example.com
modules load recon/domains-hosts/crtsh
options set SOURCE example.com
run
```

✅ Observa los subdominios descubiertos.

---

### Extra: Uso en informes

✅ Puedes exportar resultados:

- CSV
- JSON
- Tablas para reportes

✅ Perfecto para **documentar hallazgos** en auditorías.

---

[🔼](#índice)

---

| **Inicio**         | **atrás 1**                                                        | **Siguiente 3**                                        |
| ------------------ | ------------------------------------------------------------------ | ------------------------------------------------------ |
| [🏠](../README.md) | [⏪](./2_1_introduccion_al_hacking_etico_y_penetration_testing.md) | [⏩](./2_3_Recopilacion_semi_pasiva_de_informacion.md) |
