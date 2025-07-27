| **Inicio**         | **atrás 4**                                       | **Siguiente 6**                                                   |
| ------------------ | ------------------------------------------------- | ----------------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./2_4_Recopilacion_activa_de_informacion.md) | [⏩](./2_6_Explotacion_y_hacking_de_vulnerabilidades_en_hosts.md) |

---

## **Índice**

| Temario                                                                                                                  |
| ------------------------------------------------------------------------------------------------------------------------ |
| [36. Introducción a la fase de Análisis de Vulnerabilidades](#36-introducción-a-la-fase-de-análisis-de-vulnerabilidades) |
| [37. Análisis de vulnerabilidades](#37-análisis-de-vulnerabilidades)                                                     |
| [38. CVE, CVSS, CPE - Common Vulnerabilities and Exposures](#38-cve-cvss-cpe---common-vulnerabilities-and-exposures)     |
| [39. Análisis de vulnerabilidades con Nmap](#39-análisis-de-vulnerabilidades-con-nmap)                                   |
| [40. Nessus: Introducción e instalación](#40-nessus-introducción-e-instalación)                                          |
| [41. Nessus: Análisis básico de vulnerabilidades](#41-nessus-análisis-básico-de-vulnerabilidades)                        |
| [42. Nessus: Análisis avanzado de vulnerabilidades](#42-nessus-análisis-avanzado-de-vulnerabilidades)                    |
| [43. Otras herramientas de análisis de vulnerabilidades](#43-otras-herramientas-de-análisis-de-vulnerabilidades)         |

---

# **Análisis de Vulnerabilidades**

## **36. Introducción a la fase de Análisis de Vulnerabilidades**

### ¿Qué es la fase de Análisis de Vulnerabilidades?

**Definición sencilla:**

> Es el proceso de identificar, analizar y priorizar las vulnerabilidades (fallas de seguridad) en sistemas, redes o aplicaciones.

En otras palabras: **buscar huecos de seguridad que un atacante podría explotar**.

---

### ¿Dónde ocurre esta fase?

Es parte de un **proceso más grande** de gestión de vulnerabilidades, que suele tener estas etapas:

1️⃣ **Identificación**: Escanear para encontrar vulnerabilidades.

2️⃣ **Análisis**: Entender y priorizar qué tan graves son. 👉 _Aquí nos centramos hoy_.

3️⃣ **Remediación**: Arreglarlas o mitigarlas.

4️⃣ **Verificación**: Comprobar que ya no existan.

El **análisis** es como el **diagnóstico del médico** tras los exámenes: te dice qué problemas hay y cuáles son más urgentes.

---

### Objetivo de la fase de análisis

- Entender **qué tan crítica es** cada vulnerabilidad.
- Determinar **impacto** y **probabilidad** de explotación.
- Ayudar a decidir **qué arreglar primero**.

---

### ¿Cómo se hace? (Proceso típico)

Aquí tienes los pasos **bien explicados**:

#### 🔎 A. Recolectar resultados del escaneo

- Usas un **escáner de vulnerabilidades** (como Nessus, OpenVAS, Qualys, etc.) que te da un **listado de hallazgos**.
- Ejemplo de salida de escaneo:

  ```
  - Puerto 22 abierto (SSH) sin autenticación de clave
  - Apache 2.2 con vulnerabilidad CVE-2017-3169
  - Contraseña débil: admin/admin
  ```

---

#### 🔎 B. Validar resultados

- **Quitar falsos positivos**.
- Confirmar si la vulnerabilidad **realmente existe**.

✅ Ejemplo:

- El escáner dice: «Apache 2.2 vulnerable».
- Tú revisas y ves que el servidor tiene Apache 2.4 (ya actualizado).
  ✅ Entonces es un **falso positivo** y lo descartas.

---

#### 🔎 C. Clasificar las vulnerabilidades

- Usas un **sistema de puntuación**, como **CVSS (Common Vulnerability Scoring System)**.
- CVSS te da una calificación de 0 a 10:

  - Baja: 0.1–3.9
  - Media: 4.0–6.9
  - Alta: 7.0–8.9
  - Crítica: 9.0–10.0

✅ Ejemplo:

```
- CVE-2017-3169: CVSS 7.5 → Alta
- Contraseña débil → Crítica (acceso fácil para atacante)
```

---

#### 🔎 D. Determinar impacto y riesgo

- Impacto: ¿Qué pasa si se explota?
- Probabilidad: ¿Qué tan fácil es explotarla?
- Riesgo = Impacto × Probabilidad.

✅ Ejemplo práctico:

- **Contraseña débil en admin/admin:**

  - Impacto: Total (pueden controlar el sistema)
  - Probabilidad: Muy alta
  - Resultado: Riesgo Crítico

- **Apache desactualizado con vulnerabilidad de inyección menos grave:**

  - Impacto: Medio
  - Probabilidad: Media
  - Resultado: Riesgo Alto o Medio

---

#### 🔎 E. Priorizar vulnerabilidades

- Se ordenan para remediar primero las más peligrosas.

  ✅ Ejemplo de priorización:

```
1. Contraseña débil (Crítico)
2. Apache vulnerable (Alto)
3. SSH sin clave (Medio)
```

---

### Ejemplo completo fácil de entender

**Escenario:** Un sitio web de comercio electrónico

✅ Hallazgos del escáner:

- SQL Injection en la página de login.
- Servidor usa TLS 1.0.
- Puerto 22 abierto sin restricción.

✅ Análisis:

- SQL Injection:

  - Impacto: Alto (puede extraer datos de clientes)
  - Probabilidad: Alta (explotable con scripts comunes)
  - CVSS \~ 9.8 → Crítico

- TLS 1.0:

  - Impacto: Medio (datos podrían ser descifrados)
  - Probabilidad: Media
  - CVSS \~ 5.6 → Medio

- SSH abierto:

  - Impacto: Medio
  - Probabilidad: Baja (autenticación fuerte)
  - CVSS \~ 4.3 → Bajo

✅ Prioridad:

1. SQL Injection (Crítico)
2. TLS 1.0 (Medio)
3. SSH abierto (Bajo)

✅ Plan:

- Corregir la inyección SQL de inmediato.
- Planificar actualización de TLS.
- Considerar restricción en SSH.

---

### Herramientas comunes para el análisis

- **Nessus, OpenVAS, Qualys** (para escaneo inicial)
- **CVSS Calculator** (para puntuación)
- **OWASP Vulnerability Management Guide** (buenas prácticas)

---

### Uso en la vida real

En empresas:

- Equipos de ciberseguridad hacen análisis semanal o mensual.
- Informan a los equipos de TI qué vulnerabilidades arreglar primero.
- Documentan el análisis en **reportes**.

✅ Ejemplo de reporte sencillo:

| Vulnerabilidad      | CVSS | Impacto | Probabilidad | Prioridad | Recomendación                     |
| ------------------- | ---- | ------- | ------------ | --------- | --------------------------------- |
| SQL Injection       | 9.8  | Alto    | Alta         | 1         | Validar entradas, usar ORM seguro |
| TLS 1.0 obsoleto    | 5.6  | Medio   | Media        | 2         | Desactivar TLS 1.0, usar TLS 1.2+ |
| SSH sin restricción | 4.3  | Medio   | Baja         | 3         | Limitar IPs permitidas            |

---

### Resumen

⭐ El **Análisis de Vulnerabilidades** consiste en:

- Confirmar hallazgos.
- Medir su gravedad.
- Determinar impacto y probabilidad.
- Priorizar para arreglar primero lo más crítico.

⭐ Sirve para **usar recursos limitados de forma efectiva**, evitando ataques costosos.

---

[🔼](#índice)

---

## **37. Análisis de vulnerabilidades**

### ¿Qué es el Análisis de Vulnerabilidades?

Es el proceso de **buscar, identificar, analizar y priorizar** fallas de seguridad (vulnerabilidades) en sistemas, redes o aplicaciones.

**Objetivo:**

👉 Encontrar los "huecos" que un atacante podría usar, antes de que él lo haga.

---

### Fases (explicadas fácil)

El proceso suele dividirse así:

1️⃣ **Descubrimiento / Identificación:**

- Buscar puertos abiertos, servicios, versiones.
- Escanear para encontrar vulnerabilidades conocidas.

2️⃣ **Análisis:**

- Confirmar si son reales.
- Evaluar su impacto y riesgo.

3️⃣ **Remediación:**

- Arreglarlas o mitigarlas.

4️⃣ **Verificación:**

- Volver a escanear para confirmar que se solucionaron.

---

### Ejemplo simple (vida real)

**Escenario:**

Tu servidor web está en Internet.

**Pasos:**

1. Escaneas con una herramienta.

2. Encuentras:

   - Apache versión vieja → vulnerable a CVE-XXXX.
   - Puerto 22 abierto a todo el mundo.
   - Contraseña por defecto en la base de datos.

3. Analizas:

   - Apache viejo → Ataque remoto → ALTO riesgo.
   - Puerto 22 abierto → Riesgo MEDIO.
   - Contraseña débil → Riesgo CRÍTICO.

4. Priorizas:

   - Cambiar la contraseña YA.
   - Actualizar Apache.
   - Restringir SSH.

---

### ¿Cómo se hace en la práctica?

👉 Se usa un **escáner de vulnerabilidades**.

Estos programas revisan el sistema y generan un **reporte de hallazgos**.

---

### Herramientas populares (gratuitas y fáciles de usar)

✅ **Nmap** – Para descubrir puertos/servicios.

✅ **OpenVAS** – Escáner completo y gratuito.

✅ **Nessus Essentials** – Versión gratis de uso limitado.

✅ **Nikto** – Escáner para sitios web.

---

### Instalación y uso paso a paso

Aquí te explico cómo instalar **dos herramientas muy usadas y gratis**:

---

#### 🚀 A. Nmap

✅ **¿Para qué sirve?**

- Descubre puertos abiertos y servicios.
- Te dice qué corre en tu servidor.

✅ **Instalación (Linux, Ubuntu/Debian):**

```bash
sudo apt update
sudo apt install nmap
```

✅ **Instalación (Windows):**

- Descarga de:

[https://nmap.org/download.html](https://nmap.org/download.html)

- Instalador fácil (siguiente, siguiente).

✅ **Ejemplo de uso:**

```bash
nmap 192.168.1.10
```

👉 Resultado:

```
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
```

✅ Interpreta:

- El servidor tiene SSH y HTTP abiertos.

✅ **Escaneo más detallado:**

```bash
nmap -sV 192.168.1.10
```

- Incluye versiones:

```
22/tcp open  ssh    OpenSSH 7.6
80/tcp open  http   Apache 2.4.29
```

👉 Ya sabes si está desactualizado.

---

#### 🚀 B. OpenVAS (Greenbone Vulnerability Manager)

✅ **¿Para qué sirve?**

- Escanea el sistema en busca de vulnerabilidades conocidas.
- Analiza y da un reporte con CVSS.

✅ **Requisitos:**

- Linux (más fácil).
- En Windows: usar máquina virtual o WSL2.

✅ **Instalación (Ubuntu / Debian):**

```bash
sudo apt update
sudo apt install openvas
```

✅ Configuración inicial:

```bash
sudo gvm-setup
```

✅ Iniciar el servicio:

```bash
sudo gvm-start
```

✅ Verás algo como:

```
Web UI available at: https://127.0.0.1:9392
```

✅ **Acceso:**

- Abre tu navegador en esa dirección.
- Ingresa con el usuario/contraseña creado en el setup.

✅ **Uso (ejemplo):**

1️⃣ Crear un "Target" (el servidor que quieres escanear).

2️⃣ Configurar un "Task" (el escaneo).

3️⃣ Lanzar el escaneo.

4️⃣ Ver el **Reporte**:

- Lista de vulnerabilidades encontradas.
- CVSS Score.
- Descripción.
- Solución sugerida.

✅ **Ejemplo de hallazgo:**

```
Apache 2.2 Detected
CVE-2017-3169
CVSS Score: 7.5 (High)
Remediation: Update to 2.4.29 or higher
```

✅ **Interpretación:**

- Te indica qué hacer → actualizar Apache.

---

#### 🚀 C. Nikto (web scanner)

✅ **¿Para qué sirve?**

- Escanea sitios web en busca de vulnerabilidades conocidas.

✅ **Instalación (Linux):**

```bash
sudo apt install nikto
```

✅ **Uso básico:**

```bash
nikto -h http://example.com
```

✅ Resultado:

```
+ Server: Apache/2.2.29
+ The anti-clickjacking X-Frame-Options header is not present.
+ Allowed HTTP Methods: GET, HEAD, POST, OPTIONS
+ OSVDB-877: Apache 2.2.29 is vulnerable.
```

✅ Interpretación:

- Falta cabecera de seguridad.
- Versión vulnerable → hay que actualizar.

---

### Cómo usarlo en un flujo real (paso a paso)

Aquí te dejo **un ejemplo práctico completo**:

✅ 1. Usas Nmap:

```bash
nmap -sV 192.168.1.10
```

👉 Descubres puertos abiertos y versiones.

✅ 2. Usas OpenVAS:

- Configuras target = 192.168.1.10.
- Corres un escaneo completo.
- Obtienes un reporte con vulnerabilidades, CVSS y recomendaciones.

✅ 3. Usas Nikto (si es un servidor web):

```bash
nikto -h http://192.168.1.10
```

- Encuentras problemas en cabeceras, configuraciones y versiones.

✅ 4. Analizas:

- Revisión de CVSS.
- Impacto y probabilidad.
- Priorizas (Crítico > Alto > Medio > Bajo).

✅ 5. Remedias:

- Cambiar contraseñas débiles.
- Actualizar software.
- Restringir puertos.

✅ 6. Verificas:

- Vuelves a escanear para confirmar.

---

### Resumen súper fácil

⭐ **Análisis de Vulnerabilidades** = Buscar, entender y priorizar huecos de seguridad.

⭐ **Herramientas gratis y fáciles**:

- Nmap → descubrimiento.
- OpenVAS → escaneo de vulnerabilidades.
- Nikto → escaneo web.

⭐ **Proceso típico**:

1️⃣ Descubrir → Nmap.

2️⃣ Escanear → OpenVAS / Nikto.

3️⃣ Analizar → CVSS.

4️⃣ Remediar → Solucionar vulnerabilidades.

5️⃣ Verificar → Volver a escanear.

---

[🔼](#índice)

---

## **38. CVE, CVSS, CPE - Common Vulnerabilities and Exposures**

### ¿Qué es CVE?

**CVE = Common Vulnerabilities and Exposures**

👉 Es **un identificador único** para cada vulnerabilidad conocida en software o hardware.

✅ Piensa en CVE como el **DNI de las vulnerabilidades**.

---

#### 📌 Formato

```
CVE-AÑO-NÚMERO
```

✅ Ejemplo real:

```
CVE-2017-0144
```

- Año: 2017
- Número: 0144

---

#### 📌 ¿Para qué sirve?

- Es un **estándar mundial** para nombrar vulnerabilidades.
- Permite que todos hablen el **mismo idioma**.

✅ Por ejemplo:

- Microsoft, Apple, Nessus y OpenVAS pueden decir "esta vulnerabilidad es CVE-2017-0144" y sabrás que es la misma.

---

#### 📌 Ejemplo concreto

✅ CVE-2017-0144

- Apodo: EternalBlue
- Descripción: Vulnerabilidad en SMBv1 en Windows.
- Impacto: Permite ejecución remota de código.
- Usado en el ransomware WannaCry.

✅ Resultado:

- Parche crítico de seguridad por Microsoft.
- CVE único para identificarlo.

---

#### 📌 ¿Dónde buscarlo?

✅ [NVD (National Vulnerability Database)](https://nvd.nist.gov/vuln/search)

✅ [MITRE CVE List](https://cve.mitre.org/)

✅ Puedes escribir en Google:

```
CVE-2017-0144
```

Y encuentras toda la información.

---

#### ✅ ¿Cómo se usa en análisis?

Cuando escaneas un servidor con OpenVAS, Nessus o Qualys, te dicen:

```
Found vulnerability: CVE-2017-0144
Severity: Critical
```

✅ Así sabes **exactamente cuál es** y puedes buscar **cómo arreglarla**.

---

### ¿Qué es CVSS?

**CVSS = Common Vulnerability Scoring System**

👉 Es **un sistema para medir la gravedad** de una vulnerabilidad.

✅ Da **un puntaje** de 0.0 a 10.0:

- 0.0 – 3.9 → Bajo
- 4.0 – 6.9 → Medio
- 7.0 – 8.9 → Alto
- 9.0 – 10.0 → Crítico

---

#### 📌 Ejemplo fácil:

✅ CVE-2017-0144 (EternalBlue):

```
CVSS v3 Score: 8.1 (High)
```

Significa:

- Impacto: alto (puede ejecutar código remotamente).
- Complejidad: baja (fácil de explotar).

---

✅ CVE-2020-0601 (CurveBall):

```
CVSS v3 Score: 8.1
```

✅ CVE-2021-34527 (PrintNightmare):

```
CVSS v3 Score: 8.8
```

---

#### 📌 ¿Cómo se calcula?

El CVSS considera varios factores:

- Attack Vector (Red local o Internet)
- Attack Complexity
- Privileges Required
- User Interaction
- Scope
- Impacto en confidencialidad, integridad y disponibilidad

✅ Hay calculadoras en línea:

✅ [Calculadora oficial de FIRST](https://www.first.org/cvss/calculator/3.1)

---

#### 📌 ¿Para qué sirve?

- **Priorizar arreglos.**
- Decidir: ¿Parchear ya o planificar?

✅ Ejemplo práctico:

```
Encontraste 5 CVEs en tu servidor:
- CVSS 9.8 → Prioridad máxima
- CVSS 5.4 → Puede esperar
```

---

#### 📌 ¿Dónde consultar?

✅ [NVD](https://nvd.nist.gov/)

✅ [MITRE](https://cve.mitre.org/)

✅ También en reportes de:

- Nessus
- OpenVAS
- Qualys

---

### ¿Qué es CPE?

**CPE = Common Platform Enumeration**

👉 Es un **sistema estandarizado para nombrar software y hardware**.

✅ Piensa en CPE como el **catálogo oficial de software**.

---

#### 📌 Formato típico

```
cpe:2.3:a:microsoft:windows_10:1909:*:*:*:*:*:*:*
```

✅ Desglosado:

- cpe:2.3 – Versión del formato.
- a – Tipo (a = aplicación, o = OS, h = hardware).
- microsoft – Fabricante.
- windows_10 – Producto.
- 1909 – Versión.

---

#### 📌 ¿Para qué sirve?

✅ Asociar vulnerabilidades a productos **de forma precisa**.

✅ Cuando dices:

```
CVE-2017-0144 afecta a
cpe:2.3:o:microsoft:windows_7:*:*:*:*:*:*:*
```

- Herramientas automáticas pueden detectar si tu sistema coincide.

---

#### 📌 Ejemplo en la vida real:

✅ OpenVAS detecta:

```
CPE: cpe:/a:apache:http_server:2.2.22
```

- Significa que encontró **Apache 2.2.22**.
- Busca vulnerabilidades para ese CPE.
- Te devuelve:

```
CVE-2017-3169 (CVSS 7.5)
```

---

✅ Resumen:

- **CVE** = Identificador único de la vulnerabilidad.
- **CVSS** = Cuánto de grave es.
- **CPE** = A qué producto específico afecta.

---

### Ejemplo práctico completo

✅ Escenario:

Tu servidor corre:

```
Apache/2.2.22 (Ubuntu)
```

✅ Tu escáner OpenVAS te dice:

- **CPE detectado:**

  ```
  cpe:/a:apache:http_server:2.2.22
  ```

- **CVE encontrado:**

  ```
  CVE-2017-3169
  ```

- **CVSS:**

  ```
  7.5 (High)
  ```

- **Descripción:**

  ```
  Apache HTTPD privilege escalation.
  ```

- **Solución:**

  ```
  Update to Apache 2.4.x
  ```

✅ Resultado:

- Sabes **qué vulnerabilidad tienes** (CVE).
- Qué tan peligrosa es (CVSS).
- En qué producto exacto está (CPE).
- Cómo arreglarla.

---

### ¿Cómo “instalar” o “usar” CVE, CVSS y CPE?

👉 No se "instalan" como programas, **se consultan** y se **usan en herramientas**.

✅ Formas de usarlos:

1️⃣ **Sitios web**:

- [NVD](https://nvd.nist.gov/) → Busca CVEs, ve CVSS y CPE.
- [MITRE CVE](https://cve.mitre.org/).

2️⃣ **Escáneres de vulnerabilidades**:

- OpenVAS
- Nessus
- Qualys

Estos **ya incluyen** las bases de datos de CVE, CVSS y CPE.

✅ Uso real:

```
OpenVAS → Detecta software → Mapea con CPE → Busca CVE → Muestra CVSS → Da solución.
```

---

✅ 3️⃣ **APIs y descargas**

- NVD permite descargar toda la base de datos en JSON.
- Usado en desarrollos o integraciones.

✅ Ejemplo de uso en script (avanzado):

- Parsear JSON con CVEs para hacer dashboards internos.

---

### Ejemplo sencillo para usar hoy

✅ Quieres revisar CVE en tu software:

⭐ Buscas en NVD:

1️⃣ Ve a:

```
https://nvd.nist.gov/vuln/search
```

2️⃣ Escribe:

```
Apache 2.2.22
```

3️⃣ Resultado:

- CVE listados.
- CVSS Score.
- CPE asociado.
- Descripción.
- Solución sugerida.

✅ ¡Así de fácil!

---

### Resumen

**CVE**

> Identificador único de vulnerabilidad.
>
> Ejemplo: CVE-2017-0144

**CVSS**

> Puntaje de gravedad (0–10).
>
> Ejemplo: 9.8 → Crítico.

**CPE**

> Identificador estándar del producto.
>
> Ejemplo: cpe:/a\:apache\:http_server:2.2.22

✅ Usados juntos para:

- Detectar
- Priorizar
- Remediar vulnerabilidades.

---

✅ En herramientas:

- OpenVAS, Nessus y Qualys ya integran CVE, CVSS y CPE automáticamente.

---

✅ **No necesitas instalar CVE/CVSS/CPE** como programas.

✅ Necesitas **consultarlos** en bases de datos o usar herramientas que los integren.

---

[🔼](#índice)

---

## **39. Análisis de vulnerabilidades con Nmap**

### ¿Qué es Nmap? (Explicación sencilla)

**Nmap (Network Mapper)** es una herramienta de código abierto que sirve para:

✅ Descubrir hosts en una red.

✅ Ver puertos abiertos.

✅ Identificar servicios y sus versiones.

✅ Detectar el sistema operativo.

✅ Hacer scripts para detectar vulnerabilidades conocidas.

> Es como **una linterna de hacker/analista** para ver lo que está expuesto en la red.

---

### ¿Para qué sirve en análisis de vulnerabilidades?

🔎 Nmap NO es un escáner de vulnerabilidades completo (como OpenVAS o Nessus).

👉 Pero **te ayuda mucho en estas fases**:

✅ Recolección de información (reconocimiento).

✅ Identificación de puertos/servicios abiertos.

✅ Detección de versiones vulnerables.

✅ Ejecución de scripts NSE para pruebas de vulnerabilidades conocidas.

✅ ¡Se usa mucho en pentesting y auditorías!

---

### ¿Cómo instalar Nmap?

#### En Linux (Debian/Ubuntu)

```bash
sudo apt update
sudo apt install nmap
```

#### En Fedora/CentOS/RHEL

```bash
sudo dnf install nmap
```

o

```bash
sudo yum install nmap
```

#### En macOS

Usa Homebrew:

```bash
brew install nmap
```

#### En Windows

1️⃣ Ve a la web oficial:

👉 [https://nmap.org/download.html](https://nmap.org/download.html)

2️⃣ Descarga el instalador.

3️⃣ Sigue el asistente (siguiente, siguiente…).

✅ Incluye Zenmap (interfaz gráfica opcional).

---

### Primeros comandos básicos

✅ Escanear un host:

```bash
nmap 192.168.1.10
```

✅ Resultado típico:

```
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
```

✅ Escaneo de red:

```bash
nmap 192.168.1.0/24
```

✅ Encuentra todos los dispositivos activos.

---

### Identificar servicios y versiones

Muy útil para **encontrar versiones vulnerables**.

✅ Comando:

```bash
nmap -sV 192.168.1.10
```

✅ Resultado ejemplo:

```
22/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.8
80/tcp open  http    Apache httpd 2.4.18
```

✅ Interpretación:

- Sabes qué software está corriendo.
- Puedes buscar CVE en NVD:

  - Apache 2.4.18 tiene CVEs conocidos.
  - OpenSSH 7.2p2 también.

✅ Esto es **análisis de vulnerabilidades básico**: saber qué versiones tienes expuestas.

---

### Detección de sistema operativo

✅ Comando:

```bash
nmap -O 192.168.1.10
```

✅ Resultado ejemplo:

```
OS details: Linux 3.2 - 4.9
```

✅ Usas esta info para saber:

- ¿Es Windows? ¿Linux? ¿Qué versión?
- ¿Tiene vulnerabilidades conocidas para su kernel?

---

### Scripts NSE (Nmap Scripting Engine)

✅ ¡Aquí está la magia para vulnerabilidades!

Nmap incluye **scripts NSE** para:

✅ Detectar CVEs conocidos.

✅ Revisar configuraciones inseguras.

✅ Hacer ataques ligeros (autenticación por fuerza bruta, etc.).

---

#### Ejemplo: Usar scripts de vulnerabilidad

✅ Escanear con NSE:

```bash
nmap --script vuln 192.168.1.10
```

✅ Resultado:

```
PORT   STATE SERVICE
80/tcp open  http
| http-vuln-cve2017-5638:
|   VULNERABLE:
|   Apache Struts CVE-2017-5638 Remote Code Execution
|     State: VULNERABLE
|     IDs:  CVE:CVE-2017-5638
```

✅ Interpretación:

- Nmap detecta que Apache Struts está vulnerable a **CVE-2017-5638**.
- Ya tienes el CVE para buscar parches o soluciones.

---

#### Explicación fácil:

- `--script vuln` → Usa todos los scripts NSE de categoría "vuln".
- Te hace un **mini-escaneo de vulnerabilidades conocidas**.

---

### Otros scripts útiles

✅ Enumerar usuarios en SMB:

```bash
nmap --script smb-enum-users -p445 192.168.1.10
```

✅ Ver contraseñas débiles en FTP:

```bash
nmap --script ftp-brute -p21 192.168.1.10
```

✅ Buscar Heartbleed en HTTPS:

```bash
nmap --script ssl-heartbleed -p443 192.168.1.10
```

✅ Resultado:

```
| ssl-heartbleed:
|   VULNERABLE:
|   The Heartbleed Bug is a serious vulnerability in the popular OpenSSL cryptographic software library
|     State: VULNERABLE
|     IDs:  CVE:CVE-2014-0160
```

✅ ¡Así detectas CVEs concretos!

---

### Ejemplo completo, súper fácil de entender

✅ Escenario:

- Tienes un servidor en 192.168.1.10.

✅ Flujo:

1️⃣ Escaneo básico:

```bash
nmap 192.168.1.10
```

→ Descubres puertos abiertos (22, 80).

2️⃣ Identificar versiones:

```bash
nmap -sV 192.168.1.10
```

→ Apache 2.2.22 (viejo).

3️⃣ Buscar vulnerabilidades conocidas:

```bash
nmap --script vuln 192.168.1.10
```

→ Resultado:

```
| http-vuln-cve2017-3169:
|   VULNERABLE:
|   Apache HTTPD privilege escalation
|     IDs:  CVE:CVE-2017-3169
```

✅ Resultado final:

- Sabes que el Apache tiene **CVE-2017-3169**.
- Puedes buscar su **CVSS Score** (7.5 → Alto).
- Tienes solución: actualizar Apache.

---

### Reporte simple que podrías crear

```
Host: 192.168.1.10
Puertos abiertos: 22, 80
Servicios detectados:
 - SSH: OpenSSH 7.2p2
 - HTTP: Apache 2.2.22

Vulnerabilidades encontradas:
 - CVE-2017-3169 (Apache)
   - CVSS: 7.5
   - Descripción: Apache privilege escalation
   - Solución: actualizar a Apache 2.4.x
```

---

### Resumen súper claro

**Nmap sirve para**:

✅ Saber qué puertos están abiertos.

✅ Ver qué servicios y versiones corren.

✅ Descubrir el sistema operativo.

✅ Usar scripts para detectar vulnerabilidades conocidas (¡con CVE!).

---

**Comandos clave**:

✅ Básico:

```bash
nmap 192.168.1.10
```

✅ Con versiones:

```bash
nmap -sV 192.168.1.10
```

✅ Detección de OS:

```bash
nmap -O 192.168.1.10
```

✅ Scripts de vulnerabilidad:

```bash
nmap --script vuln 192.168.1.10
```

✅ Buscar Heartbleed:

```bash
nmap --script ssl-heartbleed -p443 192.168.1.10
```

---

**Cómo instalarlo**:

✅ Linux:

```bash
sudo apt install nmap
```

✅ macOS:

```bash
brew install nmap
```

✅ Windows:

- Descarga desde:

[nmap.org](https://nmap.org/download.html)

---

**Cómo usarlo en un flujo real de análisis de vulnerabilidades**:

1️⃣ Reconocimiento con Nmap → Ver puertos/servicios.

2️⃣ Identificar versiones → Buscar si son viejas o con CVE.

3️⃣ Usar NSE → Scripts de vulnerabilidades conocidas.

4️⃣ Anotar hallazgos → Buscar en NVD.

5️⃣ Priorizar → Basado en CVSS.

6️⃣ Remediar → Actualizar/cerrar puertos/asegurar servicios.

---

### Conclusión

✅ Nmap es **gratis, fácil de instalar y muy poderoso**.

✅ Es la herramienta básica de cualquier análisis de vulnerabilidades.

✅ Aunque no es un escáner completo como OpenVAS o Nessus, **te da la base para descubrir puntos débiles**.

---

[🔼](#índice)

---

## **40. Nessus: Introducción e instalación**

### Introducción: ¿Qué es Nessus?

**Nessus** es uno de los **escáneres de vulnerabilidades más populares del mundo**.

✅ Es un programa que:

- Escanea sistemas y redes.
- Detecta vulnerabilidades conocidas (con sus CVE).
- Evalúa configuraciones inseguras.
- Genera reportes con soluciones.

> ¡Piensa en Nessus como un "doctor de seguridad" para tus sistemas!

---

#### ✅ 📌 Características principales:

Base de datos enorme de vulnerabilidades (más de 70,000 plugins).

Detecta:

- Versiones de software vulnerables.
- Contraseñas débiles.
- Servicios mal configurados.
- Puertos abiertos.

  Asigna **CVSS** a cada hallazgo.

  Genera **reportes profesionales**.

---

#### ✅ 📌 Versiones de Nessus

✅ **Nessus Essentials (Gratis)**

- Para uso personal y educativo.
- Hasta 16 IPs.
- ¡Perfecta para aprender!

✅ Nessus Professional (de pago)

- Sin límite de IPs.
- Uso comercial.

---

### ¿Para qué sirve? (Ejemplo fácil)

✅ Imagina que administras un servidor:

- Corre Apache en Linux.
- Tiene SSH abierto.
- Hay MySQL expuesto.

✅ Usas Nessus y obtienes resultados:

```
1. Apache desactualizado → CVE-2017-3169 → CVSS 7.5 (Alto)
2. Contraseña root sin cambio → Crítico
3. MySQL con puerto abierto → Medio
```

✅ Gracias a Nessus:

- Sabes **qué vulnerabilidades tienes**.
- Su gravedad (CVSS).
- Qué hacer para arreglarlas (remediación sugerida).

---

✅ 🧩 Resumen fácil:

> Nessus **te ayuda a encontrar y priorizar vulnerabilidades antes de que un atacante las explote.**

---

### Cómo funciona (en palabras simples)

✅ 1️⃣ Escaneo

- Tú defines el **target** (IP o rango).
- Nessus escanea:

  - Puertos abiertos.
  - Servicios y versiones.
  - Vulnerabilidades conocidas (CVE).

✅ 2️⃣ Análisis

- Usa su base de datos para asociar vulnerabilidades.
- Asigna **CVSS** (riesgo).

✅ 3️⃣ Reporte

- Lista hallazgos.
- Incluye descripción, CVE, CVSS, solución.

---

✅ 📌 Ejemplo real de salida:

```
Vulnerability: Apache HTTPD privilege escalation
CVE: CVE-2017-3169
CVSS: 7.5
Solution: Upgrade to Apache 2.4.29 or higher
```

---

✅ 4️⃣ Prioridad

- Tú decides:

  - Arreglar primero lo crítico.
  - Planificar lo medio.
  - Aceptar riesgos bajos.

---

### Instalación de Nessus (detallada, con ejemplos)

> Te explico **cómo instalar Nessus Essentials GRATIS** en **Windows**, **Linux** y **macOS**.

---

#### A) Cómo instalar Nessus en Windows

✅ 1️⃣ Ve al sitio oficial:

👉 [https://www.tenable.com/products/nessus/nessus-essentials](https://www.tenable.com/products/nessus/nessus-essentials)

✅ 2️⃣ Regístrate para obtener **el código de activación gratis** (Essentials).

- Te lo envían al correo.

✅ 3️⃣ Descarga el instalador para **Windows**.

- Archivo .exe

✅ 4️⃣ Ejecuta el instalador:

- Siguiente → Siguiente → Instalar.

✅ 5️⃣ Al finalizar:

- Nessus corre como servicio.
- Abre el navegador en:

```
https://localhost:8834
```

✅ 6️⃣ Configuración inicial:

- Elige **Nessus Essentials**.
- Ingresa el **código de activación**.
- Crea usuario y contraseña.

✅ 7️⃣ Espera a que descargue los plugins (¡esto puede tardar varios minutos!).

✅ 8️⃣ Listo ✅

- Ya puedes hacer escaneos.

---

#### B) Cómo instalar Nessus en Linux (ejemplo en Ubuntu)

✅ 1️⃣ Descarga el paquete .deb desde:

👉 [https://www.tenable.com/products/nessus/nessus-essentials](https://www.tenable.com/downloads/nessus)

✅ 2️⃣ Instala el paquete:

```bash
sudo dpkg -i Nessus-*.deb
```

✅ 3️⃣ Inicia el servicio:

```bash
sudo systemctl start nessusd
```

✅ 4️⃣ Verifica estado:

```bash
sudo systemctl status nessusd
```

✅ 5️⃣ Accede desde navegador:

```
https://localhost:8834
```

✅ 6️⃣ Activación y setup:

- Selecciona Nessus Essentials.
- Pon el código de activación.
- Crea usuario/contraseña.
- Descarga de plugins.

✅ 7️⃣ ¡Listo para usar!

---

#### C) Cómo instalar en macOS

✅ 1️⃣ Descarga el .dmg oficial:

👉 [https://www.tenable.com/products/nessus/nessus-essentials](https://www.tenable.com/downloads/nessus)

✅ 2️⃣ Instala como cualquier app.

✅ 3️⃣ Abre Nessus.

✅ 4️⃣ Accede en el navegador:

```
https://localhost:8834
```

✅ 5️⃣ Activa con tu código de Essentials.

✅ 6️⃣ Espera que cargue plugins.

✅ ¡Ya puedes escanear!

---

✅ 📌 Nota:

Para usar Nessus Essentials necesitas **Internet** para:

- Activar la licencia.
- Descargar los plugins.

---

### Primer escaneo con Nessus (bien explicado)

✅ Ya tienes Nessus en:

```
https://localhost:8834
```

✅ Pasos:

✅ 1️⃣ Inicia sesión.

✅ 2️⃣ Ve a **My Scans**.

✅ 3️⃣ Click en **New Scan**.

✅ 4️⃣ Selecciona **Basic Network Scan**.

✅ 5️⃣ Pon un nombre:

```
"Mi primer escaneo"
```

✅ 6️⃣ En **Targets**:

```
IP o rango (ejemplo: 192.168.1.10)
```

✅ 7️⃣ Guarda.

✅ 8️⃣ Click en **Launch**.

✅ 9️⃣ Espera resultados.

---

✅ Resultado:

- Verás lista de vulnerabilidades detectadas.
- Incluye:

  - Nombre.
  - Descripción.
  - CVE asociado.
  - CVSS.
  - Solución recomendada.

✅ Ejemplo de resultado:

```
- Vulnerability: Apache HTTPD privilege escalation
- CVE: CVE-2017-3169
- CVSS: 7.5
- Solution: Upgrade Apache to 2.4.29
```

---

### Ejemplo práctico completo

**Escenario**: Escaneas un servidor Ubuntu con Apache.

✅ Resultado Nessus:

```
1) Apache outdated
   - CVE-2017-3169
   - CVSS 7.5
   - Solution: Update to Apache 2.4.29

2) OpenSSH outdated
   - CVE-2018-15473
   - CVSS 5.3
   - Solution: Update OpenSSH to latest version
```

✅ Tú decides:

- Prioridad Alta → Apache (CVSS 7.5)
- Prioridad Media → OpenSSH

✅ Plan:

- Actualizar Apache hoy.
- Planificar OpenSSH esta semana.

---

✅ Resultado:

> Ahora sabes **qué arreglar primero** para reducir el riesgo.

---

### Resumen súper fácil

✅ Nessus = Escáner de vulnerabilidades profesional.

✅ Encuentra vulnerabilidades (con CVE y CVSS).

✅ Te dice cómo arreglarlas.

✅ Gratis hasta 16 IPs (Essentials).

---

✅ ⭐ Instalación:

🟢 Windows: .exe oficial → [https://localhost:8834](https://localhost:8834)

🟢 Linux: .deb o .rpm → systemctl start nessusd

🟢 macOS: .dmg → [https://localhost:8834](https://localhost:8834)

---

✅ Uso básico:

1️⃣ Crear escaneo.

2️⃣ Definir objetivos.

3️⃣ Lanzar.

4️⃣ Ver reporte.

5️⃣ Aplicar soluciones.

---

✅ Resultado:

> Reduces riesgo, cumples normativas, proteges sistemas.

---

### Links útiles

✅ Descargar Nessus Essentials:

👉 [https://www.tenable.com/products/nessus/nessus-essentials](https://www.tenable.com/products/nessus/nessus-essentials)

✅ Documentación oficial:

👉 [https://docs.tenable.com/nessus/](https://docs.tenable.com/nessus/)

---

[🔼](#índice)

---

## **41. Nessus: Análisis básico de vulnerabilidades**

### Introducción fácil: ¿Qué es un análisis de vulnerabilidades con Nessus?

**Un análisis de vulnerabilidades** es el proceso de **buscar fallas de seguridad en sistemas o redes**.

✅ Nessus hace esto de forma **automática y muy detallada**:

✔ Escanea puertos.

✔ Descubre servicios y versiones.

✔ Compara con su base de datos de vulnerabilidades.

✔ Muestra las fallas encontradas.

✔ Asigna un riesgo (CVSS).

✔ Recomienda cómo arreglarlo.

---

✅ **Ejemplo sencillo (vida real):**

- Tienes un servidor Linux con Apache.
- Apache está desactualizado.
- Tiene un CVE conocido.

✅ Nessus te dirá:

```
✔ Vulnerabilidad encontrada: CVE-2017-3169

✔ CVSS Score: 7.5 (High)

✔ Solución: Actualiza Apache a 2.4.29 o mayor.
```

---

✅ Resultado:

👉 Sabes **qué falla tienes**.

👉 Qué tan grave es.

👉 Cómo arreglarla.

---

### Breve repaso: Cómo instalar Nessus (Essentials, GRATIS)

⭐ **Nessus Essentials** es GRATIS (hasta 16 direcciones IP).

⭐ Ideal para aprender, uso personal o pruebas.

✅ **En Windows / Linux / macOS**:

✅ 1️⃣ Ve a:

👉 [https://www.tenable.com/products/nessus/nessus-essentials](https://www.tenable.com/products/nessus/nessus-essentials)

✅ 2️⃣ Regístrate para obtener **código de activación GRATIS**.

- Te llega al correo.

✅ 3️⃣ Descarga tu instalador (Windows, macOS o Linux .deb/.rpm).

✅ 4️⃣ Instala:

- **Windows:** doble clic en .exe, sigue el asistente.
- **macOS:** abre el .dmg, arrástralo a Aplicaciones.
- **Linux (ejemplo .deb):**

```bash
sudo dpkg -i Nessus-*.deb
```

✅ 5️⃣ Inicia el servicio (Linux):

```bash
sudo systemctl start nessusd
```

✅ 6️⃣ Accede en navegador:

```
https://localhost:8834
```

> ⚠ Es HTTPS, así que tu navegador puede advertir "conexión insegura" (certificado autofirmado). Acepta continuar.

✅ 7️⃣ Configuración inicial:

- Elige **Nessus Essentials**.
- Ingresa tu código de activación.
- Crea usuario y contraseña.
- Espera que descargue los **plugins** (puede tardar).

✅ ¡Listo! Nessus está funcionando.

---

### Cómo hacer un análisis básico paso a paso

✅ Te explico **como si estuvieras haciéndolo ahora mismo**:

---

#### ✅ Paso 1️⃣ Accede a Nessus

👉 Abre tu navegador:

```
https://localhost:8834
```

✅ Ingresa con tu usuario y contraseña que configuraste.

---

#### ✅ Paso 2️⃣ Crea un nuevo escaneo

✅ En el menú lateral izquierdo:

Haz clic en **My Scans**.

✅ Haz clic en **New Scan** (botón verde).

✅ Verás plantillas:

Elige **Basic Network Scan** (es la opción más sencilla para empezar).

---

#### ✅ Paso 3️⃣ Configura tu escaneo

✅ Nessus te pide llenar un formulario:

- **Name:** Escribe un nombre amigable.

```
Mi primer escaneo
```

- **Targets:** La IP o rango de IPs a analizar.

```
192.168.1.10
```

o

```
192.168.1.0/24
```

✅ Puedes dejar otras opciones por defecto.

✅ Haz clic en **Save**.

---

✅ Resultado:

Ahora tienes tu escaneo guardado en **My Scans**.

---

#### ✅ Paso 4️⃣ Ejecuta el escaneo

✅ Ve a **My Scans**.

✅ Busca el escaneo que creaste.

✅ Haz clic en el botón **Launch** (icono ▶).

✅ Nessus comenzará a escanear:

- Descubre puertos.
- Identifica servicios y versiones.
- Compara con su base de datos de vulnerabilidades.

✅ Tarda unos minutos, según el tamaño del objetivo.

---

### ✅ 4️⃣ Leer el resultado del escaneo

✅ Cuando termine, haz clic en tu escaneo para ver **el reporte**.

✅ Verás algo como:

✅ Panel con resultados por severidad:

```
✔ Critical: 2
✔ High: 4
✔ Medium: 10
✔ Low: 15
✔ Info: 20
```

✅ Lista de vulnerabilidades encontradas.
Cada una muestra:

Nombre.

Descripción.

CVE (identificador de la vulnerabilidad).

CVSS Score (gravedad).

Plugin ID (identificador interno de Nessus).

Solución sugerida.

---

✅ **Ejemplo de vulnerabilidad encontrada**:

```
Title: Apache HTTPD privilege escalation
CVE: CVE-2017-3169
Severity: High
CVSS v2 Base Score: 7.5
Description: Apache HTTPD is vulnerable to privilege escalation...
Solution: Upgrade to Apache 2.4.29 or later.
```

✅ Muy claro:

- Qué problema hay.
- Qué tan grave es.
- Cómo solucionarlo.

---

✅ **Puedes hacer clic en cada hallazgo** para leer más:

- Detalles técnicos.
- Links de referencia (NVD, CVE).
- Soluciones paso a paso.

---

### ✅ 5️⃣ ¿Qué hago después?

✅ Nessus **no arregla por ti**, pero te dice exactamente qué hacer.

✅ Pasos típicos después del análisis:

1️⃣ **Revisar hallazgos críticos y altos primero.**

2️⃣ Confirmar con el equipo de sistemas / TI.

3️⃣ Aplicar parches y actualizaciones.

4️⃣ Revisar configuraciones inseguras.

5️⃣ Cerrar puertos innecesarios.

6️⃣ Cambiar contraseñas débiles.

7️⃣ Volver a escanear para verificar.

---

✅ Ejemplo de plan real:

```
✔ Día 1: Arreglar vulnerabilidades críticas.
✔ Semana 1: Corregir todas las altas.
✔ Mes 1: Planificar solución de medias.
```

✅ Así reduces el **riesgo real**.

---

### ✅ 6️⃣ Ejemplo práctico completo (escenario real)

✅ **Escenario:**

Escaneas un servidor web en 192.168.1.10.

✅ **Resultado Nessus:**

```
1) Apache desactualizado
   - CVE: CVE-2017-3169
   - Severity: High
   - CVSS: 7.5
   - Solution: Update to Apache 2.4.29

2) SSH vulnerable
   - CVE: CVE-2018-15473
   - Severity: Medium
   - CVSS: 5.3
   - Solution: Update OpenSSH

3) Weak password policy detected
   - Severity: Critical
   - Solution: Enforce strong passwords.
```

✅ **Plan de acción:**

Prioridad 1: Arreglar contraseñas débiles (Crítico).

Prioridad 2: Actualizar Apache (High).

Prioridad 3: Planificar actualización de OpenSSH (Medium).

✅ Resultado esperado:

✔ Reduces exposición a ataques.

✔ Mejoras la postura de seguridad.

---

### ✅ 7️⃣ Exportar el reporte

✅ En la interfaz web de Nessus:

1️⃣ Abre tu escaneo terminado.

2️⃣ Haz clic en **Export**.

3️⃣ Elige formato:

- PDF
- CSV
- Nessus (para importar en otro sistema).

✅ Así puedes compartirlo con el equipo o guardarlo como evidencia.

---

### ✅ 8️⃣ Resumen MUY fácil

**Nessus = Herramienta para encontrar vulnerabilidades.**

Escanea redes/sistemas y muestra:

✔ Qué fallas hay.

✔ Su gravedad (CVSS).

✔ Cómo arreglarlas.

---

✅ Flujo básico:

1️⃣ Instalar Nessus.

2️⃣ Activar (Essentials, gratis).

3️⃣ Crear un escaneo → definir target.

4️⃣ Lanzar el escaneo.

5️⃣ Leer el reporte.

6️⃣ Arreglar vulnerabilidades.

7️⃣ Volver a escanear.

---

✅ Beneficio real:

> Evitar que un atacante explote tus fallas.
>
> Cumplir normativas de seguridad.
>
> Mantener tus sistemas seguros.

---

### ✅ 9️⃣ Links súper útiles

✅ Descargar Nessus Essentials:

👉 [https://www.tenable.com/products/nessus/nessus-essentials](https://www.tenable.com/products/nessus/nessus-essentials)

✅ Documentación oficial:

👉 [https://docs.tenable.com/nessus/](https://docs.tenable.com/nessus/)

---

[🔼](#índice)

---

## **42. Nessus: Análisis avanzado de vulnerabilidades**

### ¿Qué es un “análisis avanzado” en Nessus?

**Escaneo básico** = le das una IP y usas la plantilla "Basic Network Scan" → Nessus hace todo automático.

✅ Muy bueno para empezar.

✅ Pero en **escaneo avanzado**, tú decides:

⭐ Qué puertos escanear.

⭐ Qué plugins usar (familias de vulnerabilidades).

⭐ Qué credenciales dar (para análisis interno).

⭐ Qué políticas (policies) definir.

⭐ Cómo programarlo (para que se ejecute solo).

⭐ Qué exclusiones poner.

⭐ Qué niveles de rendimiento usar.

✅ Resultado:

> Mucho más control, más hallazgos, menos falsos positivos.

---

#### Ejemplo real (fácil de entender)

✅ Escenario:

Tu empresa tiene 100 servidores Linux y Windows.

✅ Necesitas:

- Revisar software desactualizado.
- Revisar configuraciones débiles (SSH, RDP).
- Ver si cumplen políticas internas.
- Generar reportes separados por equipo.

✅ En escaneo avanzado, puedes:

✔ Crear diferentes policies para Linux y Windows.

✔ Usar credenciales para escaneo **autenticado** (más profundo).

✔ Filtrar plugins (solo CVE críticos o solo config-checks).

✔ Agendar escaneos semanales.

✔ Excluir rangos (por ejemplo, servidores de pruebas).

✔ Exportar reportes personalizados.

✅ Resultado:

> Seguridad mucho más profesional y alineada a tus necesidades.

---

### Repaso rápido: ¿Cómo instalar Nessus?

✅ **Nessus Essentials (Gratis)** → hasta 16 IPs.

✅ Descarga oficial:

👉 [https://www.tenable.com/products/nessus/nessus-essentials](https://www.tenable.com/products/nessus/nessus-essentials)

✅ Windows:

- Descargar .exe → doble clic → instalar.
- Acceder en navegador:

```
https://localhost:8834
```

✅ Linux (ejemplo Ubuntu):

```bash
sudo dpkg -i Nessus-*.deb
sudo systemctl start nessusd
```

- Acceso:

```
https://localhost:8834
```

✅ macOS:

- Descargar .dmg → arrastrar a Aplicaciones.
- Acceder en:

```
https://localhost:8834
```

✅ Configurar Essentials:

- Poner el **Activation Code** (gratis).
- Crear usuario y contraseña.
- Esperar descarga de **plugins**.

---

### Antes de empezar: Conceptos clave

**Policy (Política)**

→ Define cómo va a ser tu escaneo.

- Puertos.
- Plugins.
- Credenciales.
- Exclusiones.
- Performance.

  **Plugins**

→ Son “chequeos” individuales de vulnerabilidades.

- Nessus tiene más de 70,000.
- Organizados por familias:

  - Windows.
  - Databases.
  - CIS compliance.
  - Web servers.
  - SCADA.

  **Credenciales**

→ Usuario/contraseña o claves SSH para entrar al sistema.

✅ Permite escaneo **autenticado** → mucho más completo.

**Schedule**

→ Define cuándo se ejecuta (una vez, cada semana, cada mes).

---

### Cómo crear un **escaneo avanzado** paso a paso

✅ Te explico **como si tú mismo lo hicieras**.

---

#### ✅ A) Ingresa a Nessus

👉 Abre navegador:

```
https://localhost:8834
```

✅ Log in con tu usuario.

---

#### ✅ B) Ve a "Policies" (Políticas)

✅ Menú lateral → **Policies**.

✅ Haz clic en **New Policy**.
Verás opciones:

✔ Basic Network Scan

✔ Advanced Network Scan

✔ Web App Tests

✔ Compliance Audit

✔ Malware Scan

✔ Credentialed Patch Audit
...

✅ Elige **Advanced Network Scan**.

---

#### ✅ C) Define la política (opciones avanzadas)

✅ Nessus te pedirá:

**Name**

```
Escaneo Avanzado Servidores Linux
```

**Targets**

✔ Puedes dejarlo en blanco (se define al lanzar el escaneo) o poner un rango.

---

✅ **1️⃣ Discovery (Descubrimiento)**

- Puertos:

  - Default → top 1000 puertos.
  - Custom → puedes poner:

```
22,80,443,3306
```

- All → TODOS los 65,535 puertos.

✔ Ejemplo: solo puertos comunes

```
22,80,443
```

---

✅ **2️⃣ Port Scanning**

- TCP Scan → habilitado.
- UDP Scan → opcional (más lento).
- SYN Scan → recomendado.
- Service Detection → ON (identifica versiones).
- OS Detection → ON.
- Traceroute → ON/OFF.

✔ Ejemplo avanzado:

✔ Activar UDP Scan para puertos críticos (53, 161).

---

✅ **3️⃣ Assessment (Evaluación)**

✔ Vulnerability Scanning → ON.

✔ Exploit Available → solo mostrar si hay exploit → opcional.

✔ Unsafe Checks → activar para tests más agresivos.

✔ Ejemplo:

✅ Activar "Show potential vulnerabilities".

---

✅ **4️⃣ Credentials (MUY IMPORTANTE)**

✅ Aquí das credenciales para **escaneo autenticado**:

⭐ Linux/Unix:

- SSH Username.
- Password o Private Key.

⭐ Windows:

- Domain.
- User.
- Password.

✅ ¿Por qué?

→ Nessus entra al sistema y revisa versiones instaladas, configuraciones internas → mucho más preciso.

---

✅ **5️⃣ Plugins**

✅ Por default, todos están activos.

✅ Tú puedes **filtrar**:

- Solo "Windows".
- Solo "Web Servers".
- Solo "Database".
- Solo CVSS >= 7.0.

✅ Ejemplo avanzado:

✔ Solo "Web Servers" + "SQL".

---

✅ **6️⃣ Preferences**

- Puedes poner rate limits.
- Throttle (para no saturar la red).
- SSH options (port, timeouts).

---

✅ **7️⃣ Advanced Settings**

✔ Performance → Max concurrent checks.

✔ Network → Custom route.

✔ Logging.

✅ Ejemplo:

✔ Bajar intensidad si la red es sensible:

```
Max checks per host: 4
```

---

✅ Cuando terminas → **Save**.

---

##### ✅ D) Lanzar escaneo con esta policy

✅ Ve a **My Scans**.

✅ New Scan → elige tu Policy personalizada.

✅ Nombre:

```
Escaneo Avanzado Linux Junio
```

✅ Targets:

```
192.168.1.0/24
```

✅ Schedule:

✔ Now → ejecuta ya.

✔ Schedule → define días/horas.

✅ Haz clic en **Save**.

✅ Haz clic en **Launch**.

---

✅ Nessus ahora escaneará **usando tus opciones avanzadas**:

✔ Solo puertos definidos.

✔ Plugins filtrados.

✔ Credenciales para escaneo interno.

✔ Configuración de performance.

---

### Resultado de un escaneo avanzado

✅ Cuando termina:

✔ Verás la distribución por severidad:

```
Critical: 3
High: 5
Medium: 12
Low: 18
Info: 30
```

✅ Cada hallazgo incluye:

✔ Nombre.

✔ CVE.

✔ CVSS.

✔ Descripción.

✔ Solución sugerida.

✔ Evidencia técnica.

---

✅ **Ejemplo de resultado avanzado (real):**

```
✔ Weak SSH Ciphers Enabled
   - Severity: High
   - Solution: Disable weak ciphers in sshd_config.

✔ Apache HTTPD outdated
   - CVE: CVE-2017-3169
   - CVSS: 7.5
   - Solution: Upgrade to Apache 2.4.29 or higher.

✔ MySQL root user no password
   - Severity: Critical
   - Solution: Set a strong root password.
```

✅ Además:

✔ Verás SI se usaron credenciales.

✔ Qué puertos se escanearon.

✔ Qué servicios se identificaron.

---

✅ Puedes **exportar el reporte**:

⭐ PDF → para gerencia.

⭐ CSV → para análisis en Excel.

⭐ Nessus → para reimportar.

---

### Buenas prácticas para escaneo avanzado

✅ Define **policies diferentes** para cada tipo de activo:

✔ Servidores Linux.

✔ Servidores Windows.

✔ Bases de datos.

✔ Web apps.

✅ Usa **credenciales** siempre que puedas:

✔ Mucho más preciso.

✔ Menos falsos positivos.

✅ Programa escaneos:

✔ Semanal o mensual.

✔ Cumplimiento de políticas.

✅ Excluye IPs críticas (como firewalls de producción).

✔ Evita alertas o bloqueos.

✅ Ajusta performance:

✔ Evita saturar redes.

✔ Usa throttling.

---

### Resumen muy fácil

✅ Nessus avanzado te permite:

⭐ Definir políticas personalizadas.

⭐ Elegir puertos y servicios.

⭐ Seleccionar plugins específicos.

⭐ Usar credenciales (escaneo autenticado).

⭐ Configurar performance y schedule.

⭐ Generar reportes profesionales.

✅ Resultado:

✔ Análisis más profundo y dirigido.

✔ Menos falsos positivos.

✔ Mejores decisiones de seguridad.

---

✅ ⭐ Flujo típico:

1️⃣ Crear Policy avanzada.

2️⃣ Configurar puertos, plugins, credenciales.

3️⃣ Guardar.

4️⃣ Crear escaneo usando la policy.

5️⃣ Lanzar o agendar.

6️⃣ Analizar resultados.

7️⃣ Exportar reporte.

8️⃣ Remediar vulnerabilidades.

9️⃣ Volver a escanear.

---

### Links súper útiles

✅ Descargar Nessus Essentials:

👉 [https://www.tenable.com/products/nessus/nessus-essentials](https://www.tenable.com/products/nessus/nessus-essentials)

✅ Documentación oficial:

👉 [https://docs.tenable.com/nessus/](https://docs.tenable.com/nessus/)

---

[🔼](#índice)

---

## **43. Otras herramientas de análisis de vulnerabilidades**

### Introducción: ¿Qué son las herramientas de análisis de vulnerabilidades?

Son programas que **buscan fallas de seguridad en sistemas, redes, aplicaciones o sitios web**.

✅ Funcionan así:

- Analizan equipos o servicios.
- Buscan versiones desactualizadas.
- Revisan configuraciones inseguras.
- Comparan con bases de datos de vulnerabilidades (CVE).
- Generan reportes con recomendaciones.

✅ Sirven para:

✔ Prevenir ataques.

✔ Cumplir normas de seguridad.

✔ Identificar riesgos antes que los atacantes.

---

✅ Ejemplo fácil:

> Es como un "doctor" que revisa tu computadora o red y te dice:
>
> - "Tu Apache está enfermo con una vulnerabilidad crítica."
> - "Tu contraseña es débil."
> - "Tu puerto 22 está expuesto sin protección."

---

### Herramientas populares (explicadas fácil)

Te dejo **4 herramientas muy conocidas y usadas**, con ejemplos fáciles y cómo instalarlas:

✅ 1️⃣ OpenVAS / Greenbone

✅ 2️⃣ Nikto

✅ 3️⃣ Nmap (con scripts NSE)

✅ 4️⃣ Lynis

---

#### ✅ 1️⃣ OpenVAS / Greenbone

⭐ **Qué es**

- OpenVAS = "Open Vulnerability Assessment System".
- Parte del Greenbone Vulnerability Management (GVM).
- Muy parecido a Nessus → escanea redes, puertos, servicios, vulnerabilidades.
- Base de datos grande de CVEs.
- Gratis y de código abierto.

---

⭐ **Ejemplo fácil**

> "Escaneo tu red y te dice:
>
> ✔ Apache vulnerable (CVE-XXXX-YYYY).
>
> ✔ MySQL expuesto.
>
> ✔ SSH permite contraseñas débiles."

---

⭐ **Cómo instalarlo en Linux (ejemplo Ubuntu):**

1️⃣ Actualiza sistema:

```bash
sudo apt update && sudo apt upgrade
```

2️⃣ Instala GVM (incluye OpenVAS):

```bash
sudo apt install -y greenbone-vulnerability-manager
```

3️⃣ Configura la base de datos:

```bash
sudo gvm-setup
```

4️⃣ Inicia el servicio:

```bash
sudo gvm-start
```

5️⃣ Abre navegador:

```
https://localhost:9392
```

✅ Usuario inicial → te lo da `gvm-setup`.

---

⭐ **Cómo usarlo (básico):**

✅ Ingresa a la web.

✅ Crea un nuevo escaneo:

- Define nombre.
- Define IP o rango.

  ✅ Lanzar.

  ✅ Ver reporte con vulnerabilidades, CVE, soluciones.

---

⭐ **Ventajas:**

✔ Gratis y libre.

✔ Base de datos CVE grande.

✔ Interfaz web.

✔ Reportes detallados.

---

#### ✅ 2️⃣ Nikto

⭐ **Qué es**

- Escáner de vulnerabilidades para servidores web.
- Analiza HTTP/HTTPS.
- Busca configuraciones inseguras, archivos peligrosos, versiones vulnerables.
- Muy fácil y rápido.

---

⭐ **Ejemplo fácil:**

> "Revisa tu web y te dice:
>
> ✔ Directorio /admin expuesto.
>
> ✔ Apache versión vieja.
>
> ✔ Archivos de backup públicos."

---

⭐ **Cómo instalarlo (Linux):**

✅ Muy fácil en Kali o Debian/Ubuntu:

```bash
sudo apt install nikto
```

✅ O clonarlo:

```bash
git clone https://github.com/sullo/nikto.git
cd nikto
```

---

⭐ **Uso básico:**

✅ Escaneo simple:

```bash
nikto -h http://example.com
```

✅ Escaneo HTTPS:

```bash
nikto -h https://example.com
```

✅ Escaneo con opciones:

```bash
nikto -h https://example.com -output resultado.txt
```

---

⭐ **Resultados ejemplo:**

```
+ Server: Apache/2.2.14
+ The X-Frame-Options header is not present.
+ Allowed HTTP Methods: GET, HEAD, POST, OPTIONS
+ /admin/ - Directory indexing found.
```

✅ Muy claro y directo.

---

⭐ **Ventajas:**

✔ Gratis.

✔ Fácil de usar.

✔ Enfocado en servidores web.

✔ Ideal para tests rápidos.

---

#### ✅ 3️⃣ Nmap con NSE (Nmap Scripting Engine)

⭐ **Qué es**

- Nmap es el escáner de puertos más famoso.
- Con NSE, puedes hacer escaneo de vulnerabilidades.
- Usa scripts para detectar fallas conocidas.

---

⭐ **Ejemplo fácil:**

> "No solo te dice qué puertos están abiertos, sino:
>
> ✔ Detecta versión vieja de OpenSSH.
>
> ✔ Busca vulnerabilidades con CVE.
>
> ✔ Hace brute-force contra contraseñas débiles."

---

⭐ **Cómo instalarlo:**

✅ En Linux (Debian/Ubuntu):

```bash
sudo apt install nmap
```

✅ En Windows/macOS:

- Descargar desde:

  👉 [https://nmap.org/download.html](https://nmap.org/download.html)

---

⭐ **Uso básico para puertos abiertos:**

```bash
nmap 192.168.1.10
```

---

⭐ **Uso avanzado con scripts NSE:**

✅ Vulnerability scan simple:

```bash
nmap --script vuln 192.168.1.10
```

✅ Ejemplo resultado:

```
PORT   STATE SERVICE
22/tcp open  ssh
| sshv1:
|   SSH Protocol version 1 detected
|   Vulnerability: CVE-2001-0554
|_  Severity: High
```

✅ Otro ejemplo con versión:

```bash
nmap -sV --script vuln 192.168.1.10
```

---

⭐ **Ventajas:**

✔ Gratis y open-source.

✔ Muy personalizable.

✔ Escaneo de red y vulnerabilidades al mismo tiempo.

✔ Scripts para cientos de CVEs.

---

#### ✅ 4️⃣ Lynis

⭐ **Qué es**

- Herramienta para auditoría y hardening de sistemas Linux/Unix.
- Revisa configuraciones inseguras.
- Da consejos para mejorar seguridad.
- NO es un escáner de red → analiza el sistema desde adentro.

---

⭐ **Ejemplo fácil:**

> "Te dice:
>
> ✔ Permisos incorrectos en /etc/shadow.
>
> ✔ SSH permite root login.
>
> ✔ Kernel no tiene hardening activado."

---

⭐ **Cómo instalarlo (Linux):**

✅ Clonarlo desde GitHub:

```bash
git clone https://github.com/CISOfy/lynis
cd lynis
```

✅ O instalar en Debian/Ubuntu:

```bash
sudo apt install lynis
```

---

⭐ **Uso básico:**

✅ Auditar sistema:

```bash
sudo lynis audit system
```

✅ Ejemplo de salida:

```
[+] SSH
 - Root login enabled [WARNING]
 - Weak ciphers allowed [WARNING]
[+] Filesystem
 - /tmp not mounted with noexec [SUGGESTION]
```

✅ Al final → Score y recomendaciones.

---

⭐ **Ventajas:**

✔ Gratis y open-source.

✔ Muy detallado para sistemas Linux.

✔ Excelente para hardening.

✔ Sin escaneo de red, solo auditoría interna.

---

### Resumen muy fácil

✅ 🔍 **OpenVAS / Greenbone**

✔ Escáner de red completo, como Nessus.

✔ Ideal para encontrar CVEs en servicios.

✔ Web interface, reportes.

✔ Gratis.

---

✅ 🔍 **Nikto**

✔ Escáner web.

✔ Busca problemas en servidores HTTP/HTTPS.

✔ Muy fácil y rápido.

✔ Gratis.

---

✅ 🔍 **Nmap + NSE**

✔ Escáner de red y puertos.

✔ Usa scripts para buscar vulnerabilidades.

✔ Muy flexible.

✔ Gratis.

---

✅ 🔍 **Lynis**

✔ Auditoría de sistemas Linux.

✔ Hardening y configuraciones.

✔ Sin escaneo de red.

✔ Gratis.

---

### Tabla resumen

| Herramienta | Tipo de análisis        | Instalar en         | Uso principal                          |
| ----------- | ----------------------- | ------------------- | -------------------------------------- |
| OpenVAS     | Escaneo de red/vulns    | Linux               | Encontrar CVEs en servicios            |
| Nikto       | Escaneo web             | Linux/Windows/macOS | Chequear servidores HTTP/HTTPS         |
| Nmap + NSE  | Puertos + vulns scripts | Linux/Windows/macOS | Descubrir servicios y vulnerabilidades |
| Lynis       | Auditoría sistema       | Linux               | Revisar configuraciones inseguras      |

---

### Consejos para usarlas juntas

✅ Escanea puertos → Nmap.

✅ Busca vulnerabilidades en servicios → Nmap NSE o OpenVAS.

✅ Revisa servidores web → Nikto.

✅ Audita servidores Linux → Lynis.

---

✅ ⭐ Ejemplo de flujo real:

1️⃣ Nmap para descubrir hosts y puertos:

```
nmap -sV 192.168.1.0/24
```

2️⃣ OpenVAS para escaneo profundo de vulnerabilidades.

3️⃣ Nikto para analizar tu sitio web.

4️⃣ Lynis en servidores Linux para hardening.

---

### Enlaces útiles

✅ OpenVAS / Greenbone:

👉 [https://www.greenbone.net](https://www.greenbone.net)

✅ Nikto:

👉 [https://github.com/sullo/nikto](https://github.com/sullo/nikto)

✅ Nmap:

👉 [https://nmap.org](https://nmap.org)

✅ Lynis:

👉 [https://cisofy.com/lynis/](https://cisofy.com/lynis/)

---

[🔼](#índice)

---

| **Inicio**         | **atrás 4**                                       | **Siguiente 6**                                                   |
| ------------------ | ------------------------------------------------- | ----------------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./2_4_Recopilacion_activa_de_informacion.md) | [⏩](./2_6_Explotacion_y_hacking_de_vulnerabilidades_en_hosts.md) |
