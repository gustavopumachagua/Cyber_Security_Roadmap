| **Inicio**         | **atrás 3**                                                  | **Siguiente 5**                                |
| ------------------ | ------------------------------------------------------------ | ---------------------------------------------- |
| [🏠](../README.md) | [⏪](./5_3_Acceso_a_credenciales_y_movimientos_laterales.md) | [⏩](./5_5_Deteccion_y_Evasion_de_defensas.md) |

---

## **Índice**

| Temario                                                                                                                                  |
| ---------------------------------------------------------------------------------------------------------------------------------------- |
| [327. Unas palabras sobre Bug Bounty](#327-unas-palabras-sobre-bug-bounty)                                                               |
| [328. Preparación del entorno vulnerable](#328-preparación-del-entorno-vulnerable)                                                       |
| [329. Identificación de subdominios: Subfinder, Sublist3r y Subbrute](#329-identificación-de-subdominios-subfinder-sublist3r-y-subbrute) |
| [330. Identificación de tecnologías web: WhatWeb y WebAnalyze](#330-identificación-de-tecnologías-web-whatweb-y-webanalyze)              |
| [331. Identificación de contenido: Dirbuster](#331-identificación-de-contenido-dirbuster)                                                |
| [332. Gobuster y Seclists](#332-gobuster-y-seclists)                                                                                     |
| [333. Análisis de vulnerabilidades: OWASP ZAP Proxy](#333-análisis-de-vulnerabilidades-owasp-zap-proxy)                                  |
| [334. Nikto y Skipfish](#334-nikto-y-skipfish)                                                                                           |
| [335. Nuclei y Nuclei Templates](#335-nuclei-y-nuclei-templates)                                                                         |
| [336. Fuzzing básico con ffuf](#336-fuzzing-básico-con-ffuf)                                                                             |
| [337. Fuzzing avanzado con ffuf](#337-fuzzing-avanzado-con-ffuf)                                                                         |
| [338. Explotación: Commix](#338-explotación-commix)                                                                                      |
| [339. Unas palabras sobre la fase de explotación](#339-unas-palabras-sobre-la-fase-de-explotación)                                       |
| [340. Changeme, Gitleaks y CyberChef](#340-changeme-gitleaks-y-cyberchef)                                                                |

---

# **Hacking avanzado de aplicaciones web y bug bounty**

## **327. Unas palabras sobre Bug Bounty**

### 🐞 ¿Qué es el Bug Bounty?

**Bug Bounty** (en español, "recompensa por errores") es un programa donde las empresas **ofrecen dinero o premios a los hackers éticos** (conocidos como bug bounty hunters) por encontrar **vulnerabilidades** o **errores de seguridad** en sus sistemas, apps, páginas web, APIs, etc.

---

### 🎯 ¿Qué se busca en un programa de Bug Bounty?

- Vulnerabilidades **web** como:

  - XSS (Cross-Site Scripting)
  - SQL Injection
  - CSRF
  - Broken Authentication

- Fallas móviles (Android/iOS)
- Fallas en APIs
- Problemas en configuración de servidores, etc.

---

### 🤝 ¿Quién ofrece Bug Bounties?

Plataformas famosas:

| Plataforma | Sitio Web                                              |
| ---------- | ------------------------------------------------------ |
| HackerOne  | [https://hackerone.com](https://hackerone.com)         |
| Bugcrowd   | [https://bugcrowd.com](https://bugcrowd.com)           |
| Synack     | [https://www.synack.com](https://www.synack.com)       |
| Integrity  | [https://www.intigriti.com](https://www.intigriti.com) |
| YesWeHack  | [https://www.yeswehack.com](https://www.yeswehack.com) |

También hay empresas que **tienen su propio programa**, como:

- Google (Google VRP)
- Meta/Facebook
- Microsoft
- TikTok
- Apple (aunque más cerrado)

---

### 🛠️ ¿Cómo "instalarse" en el mundo de Bug Bounty?

No necesitas instalar un software específico, pero sí necesitas estas **herramientas y pasos** para empezar:

---

#### 1. Crear cuenta en una plataforma (como HackerOne)

👉 Ve a [https://hackerone.com](https://hackerone.com), haz clic en **Join HackerOne** y crea tu cuenta como **researcher**.

---

#### 2. Aprende las bases de hacking ético

##### Conocimientos recomendados:

- **HTML, JS, HTTP, APIs**
- OWASP Top 10
- Burp Suite
- Reconocimiento con herramientas como `amass`, `nmap`, `subfinder`
- Scripting básico en **Python**, **Bash**

---

#### 3. Instalar herramientas básicas

##### ✅ Burp Suite (analizador de tráfico web)

```bash
sudo apt install burpsuite
```

O descargar desde: [https://portswigger.net/burp](https://portswigger.net/burp)

---

##### ✅ Subfinder (recolección de subdominios)

```bash
go install -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest
```

---

##### ✅ Nuclei (busca vulnerabilidades automáticamente)

```bash
go install -v github.com/projectdiscovery/nuclei/v2/cmd/nuclei@latest
```

---

##### ✅ Dirsearch (descubre rutas ocultas)

```bash
git clone https://github.com/maurosoria/dirsearch.git
cd dirsearch
python3 dirsearch.py -u https://target.com
```

---

### 🧪 Ejemplo realista de Bug Bounty

#### 🎯 Target: Sitio web de ejemplo en un programa de HackerOne

**Paso 1:** Entras al programa y encuentras que aceptan el dominio:

```
https://testsite.h1-example.com
```

---

**Paso 2:** Usas Burp Suite para interceptar el tráfico y pruebas un campo de búsqueda con:

```html
<script>
  alert(1);
</script>
```

Si ves un `alert(1)` ejecutarse, ¡descubriste un **XSS**!

---

**Paso 3:** Confirmas que el bug es **explotable** y no es un duplicado (lo reportas con pruebas).

---

**Paso 4:** Lo reportas en HackerOne con:

- Descripción clara
- Reproducción paso a paso
- Capturas de pantalla o video
- Impacto de seguridad

---

**Resultado:** Si es válido, la empresa te recompensa con:

💸 Recompensa típica: **\$100 a \$5,000+ USD**
🏅 También ganas puntos de reputación y visibilidad

---

### 🎓 ¿Dónde practicar?

Plataformas seguras y legales para practicar:

| Nombre               | Sitio web                                                                    |
| -------------------- | ---------------------------------------------------------------------------- |
| Hack The Box         | [https://hackthebox.com](https://hackthebox.com)                             |
| PortSwigger Labs     | [https://portswigger.net/web-security](https://portswigger.net/web-security) |
| TryHackMe            | [https://tryhackme.com](https://tryhackme.com)                               |
| Web Security Academy | [https://portswigger.net/web-security](https://portswigger.net/web-security) |
| PentesterLab         | [https://pentesterlab.com](https://pentesterlab.com)                         |

---

### ✅ Resumen

| Concepto           | Descripción                                             |
| ------------------ | ------------------------------------------------------- |
| ¿Qué es?           | Programa de recompensas por encontrar vulnerabilidades. |
| ¿Quién puede?      | Cualquiera con conocimientos en ciberseguridad.         |
| ¿Qué necesitas?    | Burp Suite, terminal, conocimientos en web y OWASP.     |
| ¿Dónde practicar?  | HTB, PortSwigger, TryHackMe.                            |
| ¿Dónde participar? | HackerOne, Bugcrowd, Intigriti, etc.                    |

---

[🔼](#índice)

---

## **328. Preparación del entorno vulnerable**

### 🔐 ¿Qué es un entorno vulnerable?

Un entorno vulnerable es un laboratorio controlado que simula computadoras, servidores, servicios y aplicaciones **con vulnerabilidades reales**, pero en un entorno seguro. Es ideal para aprender:

- Hacking ético
- Red Team / Blue Team
- Active Directory
- Explotación web
- Privilege escalation
- Post-explotación

---

### 🎯 Objetivo

Crear un laboratorio local con máquinas virtuales vulnerables en tu PC, usando:

- VirtualBox o VMware
- Kali Linux (atacante)
- Windows Server + Windows 10 (víctimas)
- Active Directory mal configurado
- Máquinas de práctica (como Metasploitable, DVWA, etc.)

---

### 🧰 Requisitos

| Requisito                                                         | Descripción                          |
| ----------------------------------------------------------------- | ------------------------------------ |
| RAM                                                               | 8GB mínimo (ideal 16GB)              |
| Disco duro                                                        | 80 GB libres mínimo                  |
| VirtualBox / VMware                                               | Para ejecutar las máquinas virtuales |
| ISO o VM de Kali Linux                                            | Para atacar                          |
| Máquinas vulnerables (Metasploitable, DVWA, Windows Server, etc.) | Para practicar                       |

---

### 🧱 PASO 1: Instalar VirtualBox y Extensiones

#### 🔧 Instalar VirtualBox

1. Ir a: [https://www.virtualbox.org/](https://www.virtualbox.org/)
2. Descargar e instalar según tu sistema operativo (Windows/Linux/Mac).
3. Instala el **Extension Pack** para red, USB y carpetas compartidas.

---

### 🐍 PASO 2: Descargar Kali Linux (máquina atacante)

1. Ir a [https://www.kali.org/get-kali/#kali-virtual-machines](https://www.kali.org/get-kali/#kali-virtual-machines)
2. Descargar la versión **Kali Linux VirtualBox** (ya viene lista).
3. Importar el archivo `.ova` en VirtualBox:
   Menú → Archivo → **Importar servicio virtualizado** → Selecciona el `.ova`.

> 🛠️ Usuario: `kali` | Contraseña: `kali`

---

### 💣 PASO 3: Descargar máquinas vulnerables

#### 📦 Opción A: Metasploitable 2 (Linux vulnerable)

- Descargar:
  [https://sourceforge.net/projects/metasploitable/files/Metasploitable2/](https://sourceforge.net/projects/metasploitable/files/Metasploitable2/)

- Importar en VirtualBox como una nueva VM.

> Usuario: `msfadmin` | Contraseña: `msfadmin`

---

#### 📦 Opción B: DVWA (Damn Vulnerable Web App)

Puedes instalarla dentro de una máquina Linux como Ubuntu o usarla en Docker:

```bash
git clone https://github.com/digininja/DVWA.git
cd DVWA
docker-compose up -d
```

---

#### 📦 Opción C: Windows Server + Windows 10 (para Active Directory)

Puedes conseguir imágenes gratuitas de evaluación:

- Windows Server 2019 (ISO o VHD):
  [https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2019](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2019)

- Windows 10 Enterprise:
  [https://developer.microsoft.com/en-us/windows/downloads/virtual-machines/](https://developer.microsoft.com/en-us/windows/downloads/virtual-machines/)

> Puedes simular un **entorno de dominio** con AD, usuarios, GPOs y vulnerabilidades como LLMNR, SMBv1, etc.

---

### 🌐 PASO 4: Configurar red interna o en puente

Para que Kali pueda "ver" a las demás máquinas, usa uno de estos modos en VirtualBox:

- **Red interna** (`intnet`): todas las VMs se comunican entre sí pero no tienen acceso a internet.
- **Adaptador en puente**: las VMs se comportan como si estuvieran en tu red local.

Ejemplo:

1. En cada VM, ve a configuración → red → selecciona "Adaptador en puente"
2. Asegúrate de que todas las máquinas tengan IPs en el mismo rango (ej. `192.168.1.X`)

---

### 🔍 PASO 5: Probar conectividad

Desde Kali (terminal):

```bash
ping 192.168.1.100  # IP de Metasploitable
```

Si responde, ¡todo está listo!

---

### ✅ PASO 6: Ejemplo completo – Ataque a Metasploitable

#### 🎯 Objetivo: Encontrar y explotar una vulnerabilidad en Metasploitable 2 desde Kali

---

##### 1. Descubrir la máquina:

```bash
nmap -sS -sV 192.168.1.100
```

Salida esperada:

```
21/tcp open  ftp
22/tcp open  ssh
23/tcp open  telnet
...
```

---

##### 2. Encontrar una vulnerabilidad (ej: VSFTPD 2.3.4 backdoor)

```bash
searchsploit vsftpd 2.3.4
```

Resultado:

```
Exploit Title: vsftpd 2.3.4 - Backdoor Command Execution
```

---

##### 3. Explotar con Metasploit:

```bash
msfconsole
```

```bash
use exploit/unix/ftp/vsftpd_234_backdoor
set RHOST 192.168.1.100
run
```

Si todo va bien, obtendrás una shell en la máquina remota:

```bash
id
uname -a
```

---

### 🧪 BONUS: Herramientas útiles para el laboratorio

| Herramienta      | Función                      |
| ---------------- | ---------------------------- |
| **Burp Suite**   | Interceptar tráfico web      |
| **Wireshark**    | Análisis de red              |
| **Nmap**         | Escaneo de puertos           |
| **Metasploit**   | Framework de explotación     |
| **BloodHound**   | Análisis de AD               |
| **Responder**    | Envenenamiento LLMNR/NBT-NS  |
| **CrackMapExec** | Enumeración de redes Windows |

---

### ✅ Resumen final

| Paso | Acción                                                              |
| ---- | ------------------------------------------------------------------- |
| 1    | Instalar VirtualBox y extensiones                                   |
| 2    | Descargar Kali Linux como atacante                                  |
| 3    | Descargar máquinas vulnerables (Metasploitable, DVWA, Windows)      |
| 4    | Configurar red interna o en puente                                  |
| 5    | Probar conectividad                                                 |
| 6    | Hacer pruebas reales (reconocimiento, explotación, postexplotación) |

---

[🔼](#índice)

---

## **329. Identificación de subdominios: Subfinder, Sublist3r y Subbrute**

### 🧠 ¿Qué es la identificación de subdominios?

Los **subdominios** son partes de un dominio principal, como:

- `www.ejemplo.com`
- `admin.ejemplo.com`
- `mail.ejemplo.com`

Algunos subdominios pueden contener aplicaciones vulnerables, paneles de administración, entornos de desarrollo olvidados, etc. Por eso, **enumerarlos es crucial en la fase de reconocimiento**.

---

### 🔧 Herramientas a usar

| Herramienta | Lenguaje | Tipo de escaneo           |
| ----------- | -------- | ------------------------- |
| Subfinder   | Go       | Pasivo                    |
| Sublist3r   | Python   | Pasivo                    |
| Subbrute    | Python   | Activo (fuerza bruta DNS) |

---

### 📦 1. Subfinder (rápido y moderno)

#### 🔧 Instalación (Linux / WSL / Mac)

1. Necesitas tener instalado `Go`:

   ```bash
   sudo apt install golang -y
   ```

2. Instala Subfinder:

   ```bash
   go install -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest
   ```

3. Agrega `GOPATH` al PATH si no lo has hecho:

   ```bash
   export PATH=$PATH:$(go env GOPATH)/bin
   ```

4. Verifica:

   ```bash
   subfinder -h
   ```

---

#### ✅ Ejemplo de uso

```bash
subfinder -d ejemplo.com
```

Salida esperada:

```
mail.ejemplo.com
admin.ejemplo.com
api.ejemplo.com
```

> Puedes exportar la salida:

```bash
subfinder -d ejemplo.com -o subdominios.txt
```

---

### 🐍 2. Sublist3r (ligero y popular)

#### 🔧 Instalación

```bash
sudo apt install python3-pip
git clone https://github.com/aboul3la/Sublist3r.git
cd Sublist3r
pip3 install -r requirements.txt
```

---

#### ✅ Ejemplo de uso

```bash
python3 sublist3r.py -d ejemplo.com
```

Opciones útiles:

- `-o archivo.txt`: guarda salida
- `-v`: modo verbose

---

### 🔎 3. Subbrute (fuerza bruta DNS)

#### 🔧 Instalación

```bash
git clone https://github.com/TheRook/subbrute.git
cd subbrute
```

> Requiere tener `dnspython`, que se instala así:

```bash
pip3 install dnspython
```

---

#### ✅ Ejemplo de uso

```bash
python3 subbrute.py ejemplo.com
```

> Esta herramienta usa una wordlist (por defecto `names.txt`) para intentar subdominios por fuerza bruta.

Puedes cambiar la wordlist:

```bash
python3 subbrute.py -s custom_list.txt ejemplo.com
```

---

### 🧪 Ejemplo completo de flujo

#### Escenario: Quieres investigar subdominios del dominio `testfire.net` (de práctica).

---

##### 1. Subfinder (pasivo rápido)

```bash
subfinder -d testfire.net -o subfinder.txt
```

---

##### 2. Sublist3r (busca en motores de búsqueda)

```bash
python3 sublist3r.py -d testfire.net -o sublist3r.txt
```

---

##### 3. Subbrute (fuerza bruta DNS)

```bash
python3 subbrute.py testfire.net > subbrute.txt
```

---

##### 4. Unir resultados

```bash
cat subfinder.txt sublist3r.txt subbrute.txt | sort -u > subdominios_final.txt
```

---

### 💡 Consejos prácticos

- Usa herramientas pasivas primero (Subfinder, Sublist3r) para evitar ser detectado.
- Luego, aplica fuerza bruta (Subbrute) solo si es necesario.
- Apóyate con DNS resolvers públicos como Google (8.8.8.8) o Cloudflare (1.1.1.1).
- Puedes usar otras herramientas complementarias como **Amass**, **Assetfinder** o **crt.sh**.

---

### 🧰 Extras (si quieres automatizar)

Puedes usar todas estas herramientas juntas con herramientas como:

- **Recon-ng**
- **Assetnote Subdomain Wordlists**
- **OneForAll**
- **Sudomy**
- **Project Discovery tools** (con subfinder, httpx, etc.)

---

### ✅ Conclusión

| Herramienta | Método | Uso recomendado                   |
| ----------- | ------ | --------------------------------- |
| Subfinder   | Pasivo | Rápido y moderno                  |
| Sublist3r   | Pasivo | Básico y popular                  |
| Subbrute    | Activo | Cuando necesitas fuerza bruta DNS |

La identificación de subdominios es una de las **mejores formas de encontrar superficies de ataque ocultas**, y puede conducirte a APIs olvidadas, entornos de staging, paneles de admin abiertos y más.

---

[🔼](#índice)

---

## **330. Identificación de tecnologías web: WhatWeb y WebAnalyze**

### 🧠 ¿Qué es la identificación de tecnologías web?

Cuando visitas un sitio web, en segundo plano este usa tecnologías como:

- Lenguaje: PHP, ASP.NET, Java
- CMS: WordPress, Joomla, Drupal
- Servidor web: Apache, Nginx, IIS
- Frameworks: React, Angular, Vue
- Librerías JS, bases de datos, analytics, etc.

Identificar estas tecnologías es fundamental para:

🔹 Reconocimiento en **pentesting**
🔹 **Bug bounty** (saber qué exploits aplicar)
🔹 Análisis de competencia o footprinting

---

### 🛠️ Herramientas que usaremos

| Herramienta    | Lenguaje | Tipo de escaneo   | Método                 |
| -------------- | -------- | ----------------- | ---------------------- |
| **WhatWeb**    | Ruby     | Rápido y versátil | HTTP headers, HTML, JS |
| **Webanalyze** | Go       | Preciso y rápido  | Basado en Wappalyzer   |

---

### ✅ 1. WhatWeb

#### 🔧 Instalación en Linux / WSL / Kali / Parrot

```bash
sudo apt update
sudo apt install whatweb -y
```

> También puedes clonar manualmente si no estás en Debian/Kali:

```bash
git clone https://github.com/urbanadventurer/WhatWeb.git
cd WhatWeb
sudo ruby whatweb -h
```

---

#### 🧪 Ejemplo básico

```bash
whatweb https://www.peru.gob.pe
```

**Salida esperada (resumida):**

```
https://www.peru.gob.pe [200 OK] Country[PERU][PA] IP[200.37.63.100] JQuery[1.11.1] Google-Analytics[UA-xxxxxx] Apache[2.4.6]
```

> Esto te dice que usa Apache, jQuery, Google Analytics, etc.

---

#### 🔧 Opciones útiles

- `-v` → modo verbose
- `-a 3` → agresividad (1 a 3)
- `--color=never` → sin color
- `-o salida.txt` → guardar resultados

```bash
whatweb -a 3 -v -o resultado.txt https://ejemplo.com
```

---

### ✅ 2. Webanalyze

Es una alternativa ligera y rápida basada en Wappalyzer.

#### 🔧 Requisitos

Necesitas tener **Go** instalado:

```bash
sudo apt install golang -y
```

---

#### 🔧 Instalación

```bash
git clone https://github.com/rverton/webanalyze
cd webanalyze
go build
```

> Esto creará un binario llamado `webanalyze`

---

#### 🔃 Descarga del archivo de tecnologías

```bash
./webanalyze -update
```

Este paso descarga la base de datos de tecnologías desde [Wappalyzer](https://www.wappalyzer.com/).

---

#### 🧪 Ejemplo de uso

```bash
./webanalyze -host https://www.peru.gob.pe
```

**Salida esperada:**

```
peru.gob.pe
Technologies:
 - Google Analytics
 - jQuery 1.11.1
 - Apache
```

---

#### 📂 Escaneo masivo con lista de dominios

Si tienes varios sitios en un archivo `dominios.txt`:

```bash
./webanalyze -hosts dominios.txt -crawl
```

---

### 🧪 Ejemplo completo de identificación de tecnologías

#### Escenario:

Quieres analizar el sitio **[https://testphp.vulnweb.com](https://testphp.vulnweb.com)**, que es un sitio vulnerable de pruebas de Acunetix.

---

#### 🔎 Paso 1: Con WhatWeb

```bash
whatweb -a 3 https://testphp.vulnweb.com
```

**Salida esperada:**

```
https://testphp.vulnweb.com [200 OK] Country[US][US] IP[xxx.xxx.xxx.xxx] Apache PHP[5.2.17] Cookies[PHPSESSID]
```

---

#### 🔎 Paso 2: Con Webanalyze

```bash
./webanalyze -host https://testphp.vulnweb.com
```

**Salida esperada:**

```
testphp.vulnweb.com
Technologies:
 - Apache
 - PHP 5.2.17
 - Cookie-based session
```

---

### 🔐 ¿Por qué es útil esto?

Detectar tecnologías vulnerables te permite:

✅ Saber si hay versiones antiguas de WordPress, Joomla, etc.

✅ Identificar servidores mal configurados (Apache/Nginx viejos)

✅ Explorar posibles **CVE** para explotar

✅ Ayuda a elegir herramientas de ataque más precisas

---

### ✅ Conclusión

| Herramienta    | Ideal para...                          |
| -------------- | -------------------------------------- |
| **WhatWeb**    | Escaneo rápido y personalizable        |
| **Webanalyze** | Detección precisa basada en Wappalyzer |

Usar ambas te da una **visión completa de la superficie de ataque** de cualquier dominio.

---

[🔼](#índice)

---

## **331. Identificación de contenido: Dirbuster**

### 🧠 ¿Qué es DirBuster?

**DirBuster** es una herramienta gráfica desarrollada por OWASP que permite realizar ataques de **fuerza bruta** sobre aplicaciones web para descubrir:

✅ Directorios ocultos

✅ Archivos sensibles (ej: `.bak`, `.php`, `.zip`, etc.)

✅ Rutas no publicadas por el desarrollador

Esto se usa mucho en **pentesting** y **bug bounty** para descubrir:

- `/admin/`, `/backup/`, `/test/`, `/config.php`, etc.

---

### 🧰 ¿Cómo funciona?

DirBuster lanza peticiones HTTP automáticas a un dominio, probando **miles de rutas posibles** desde una **lista de palabras (wordlist)**.

Por ejemplo:

```
GET /admin/
GET /login/
GET /wp-admin/
GET /backup.zip
```

Y observa si recibe respuestas **200 OK** (¡existe!) o **403 Forbidden** (también útil), o **404 Not Found**.

---

### 🛠️ Instalación de DirBuster

#### ✅ En Kali Linux / Parrot OS

Ya viene preinstalado:

```bash
dirbuster
```

Si no lo tienes:

```bash
sudo apt update
sudo apt install dirbuster -y
```

---

#### ✅ En otras distros (Ubuntu/Debian)

```bash
sudo apt install dirbuster -y
```

---

#### ✅ En Windows

1. Necesitas tener **Java instalado**.

2. Descarga desde:
   🔗 [https://sourceforge.net/projects/dirbuster/](https://sourceforge.net/projects/dirbuster/)

3. Descomprime el `.zip`

4. Ejecuta: `DirBuster-0.12.jar` con doble clic o por terminal:

```bash
java -jar DirBuster-0.12.jar
```

---

### 🖥️ Interfaz de DirBuster (explicación paso a paso)

1. **Target URL**: escribe la dirección, por ejemplo:

   ```
   http://testphp.vulnweb.com/
   ```

2. **List-based brute force**: deja activado.

3. **File with list of dirs/files**:
   Usa una lista de palabras. Puedes usar:

   ```
   /usr/share/wordlists/dirb/common.txt
   ```

4. **Number of Threads**: cantidad de hilos simultáneos.

   - 10 a 30 es seguro
   - Si subes más, es más rápido pero más agresivo

5. Clic en **"Start"**

---

### 📈 ¿Qué buscar en los resultados?

- Estado **200 OK** → Existe
- Estado **403 Forbidden** → Existe, pero no se permite acceder
- Estado **500** → Posible error interno al acceder (interesante)
- Estado **301/302** → Redirección

---

### 📂 Wordlists recomendadas

- `/usr/share/wordlists/dirb/common.txt`
- `/usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt`
- Puedes usar las de SecLists:
  🔗 [https://github.com/danielmiessler/SecLists](https://github.com/danielmiessler/SecLists)

---

### 🧪 Ejemplo completo con DirBuster

#### 🔍 Escenario:

Vamos a probar en el sitio vulnerable de Acunetix:

🔗 `http://testphp.vulnweb.com`

#### 🛠️ Configuración:

| Campo                 | Valor                                                   |
| --------------------- | ------------------------------------------------------- |
| Target URL            | `http://testphp.vulnweb.com`                            |
| Threads               | `20`                                                    |
| Wordlist              | `/usr/share/wordlists/dirb/common.txt`                  |
| Scan Type             | List-based brute force                                  |
| File extension to add | (en blanco o agrega `.php,.html,.bak` si deseas probar) |

#### ▶️ Iniciar escaneo

Clic en `Start`.

#### 📊 Resultados esperados:

```
[+] /admin/
[+] /images/
[+] /cart.php
[+] /password.txt (← ¡esto sería crítico!)
[403] /logs/ (existe pero no se puede acceder)
```

---

### 🧠 ¿Por qué es importante DirBuster?

- Te ayuda a **descubrir partes no públicas** del sitio.
- Permite encontrar **archivos mal protegidos** (ej: contraseñas, backups).
- Puede revelar **paneles de administración** ocultos.
- Es útil en **fases de reconocimiento** antes de un ataque.

---

### ✅ Recomendaciones

| Consejo                     | Explicación                                    |
| --------------------------- | ---------------------------------------------- |
| Usa múltiples wordlists     | Algunas son comunes, otras más avanzadas       |
| Revisa respuestas 403 y 401 | A veces son rutas reales protegidas            |
| No uses demasiados hilos    | Puede ser detectado como DoS o bloqueo por WAF |
| Guarda los resultados       | Puedes exportarlos en un `.csv` desde la GUI   |

---

### 🔚 Conclusión

DirBuster es una herramienta imprescindible en pentesting web:

- Fácil de usar (GUI)
- Muy configurable
- Compatible con grandes wordlists
- Detecta rutas y archivos ocultos de forma eficiente

---

[🔼](#índice)

---

## **332. Gobuster y Seclists**

### 🛠️ **Gobuster y SecLists: Enumeración de directorios web desde terminal**

---

#### 🧠 ¿Qué es **Gobuster**?

**Gobuster** es una herramienta de fuerza bruta muy rápida escrita en Go. Sirve para encontrar:

- Directorios o archivos ocultos en un sitio web
- Subdominios
- Recursos en buckets S3, DNS, etc.

Usa una **wordlist** para probar rutas como:

```
http://example.com/admin
http://example.com/login
http://example.com/backup.zip
```

Y nos dice cuáles existen.

---

#### 📚 ¿Qué son **SecLists**?

**SecLists** es una colección enorme de wordlists (listas de palabras) para pruebas de seguridad, que incluye listas para:

- Fuerza bruta
- Directorios y archivos comunes
- Usuarios, contraseñas
- Subdominios
- Fuzzing, payloads, etc.

Gobuster las usa para lanzar ataques efectivos.

---

### 🧪 Ejemplo real:

**Objetivo:** encontrar rutas ocultas en una página vulnerable:
`http://testphp.vulnweb.com`

---

### 🔧 Instalación paso a paso

#### ✅ 1. Instalar Gobuster

##### En Kali Linux / Parrot OS:

Ya viene instalado. Si no:

```bash
sudo apt update
sudo apt install gobuster -y
```

##### En Ubuntu/Debian:

```bash
sudo apt install gobuster -y
```

##### En Arch:

```bash
sudo pacman -S gobuster
```

##### O compilar desde el código:

```bash
go install github.com/OJ/gobuster/v3@latest
```

> Ejecutable quedará en: `$HOME/go/bin/gobuster`

---

#### ✅ 2. Instalar SecLists

Clona el repositorio:

```bash
git clone https://github.com/danielmiessler/SecLists.git
```

Esto te dará muchas listas, por ejemplo:

```
SecLists/Discovery/Web-Content/common.txt
SecLists/Discovery/Web-Content/directory-list-2.3-medium.txt
SecLists/Passwords/Common-Credentials/
```

---

### ⚙️ Sintaxis básica de Gobuster

```bash
gobuster dir -u <URL> -w <WORDLIST>
```

Opciones comunes:

| Opción | Explicación                                 |
| ------ | ------------------------------------------- |
| `-u`   | URL objetivo (ej. `http://example.com`)     |
| `-w`   | Wordlist (ruta al archivo `.txt`)           |
| `-x`   | Extensiones a buscar (`php,html,txt`)       |
| `-t`   | Número de hilos                             |
| `-o`   | Archivo de salida                           |
| `-q`   | Modo silencioso (solo respuestas positivas) |

---

### ✅ Ejemplo completo

```bash
gobuster dir -u http://testphp.vulnweb.com -w SecLists/Discovery/Web-Content/common.txt -t 30 -x php,txt,html -o resultado.txt
```

🔍 Esto hará:

- Probar rutas del wordlist `common.txt`
- Usar 30 hilos (más rápido)
- Buscar rutas como `/admin.php`, `/login.txt`, etc.
- Guardar resultados en `resultado.txt`

---

#### 💡 Resultado esperado:

```bash
/htdocs (Status: 403)
/admin (Status: 200)
/login.php (Status: 200)
/backup.zip (Status: 200)
/robots.txt (Status: 200)
```

Esto indica qué rutas existen, lo cual es útil para explotación.

---

### 🧠 Consejos útiles

| Consejo                  | Descripción                                                                |
| ------------------------ | -------------------------------------------------------------------------- |
| Usa varias wordlists     | Prueba `directory-list-2.3-medium.txt` o `big.txt` para mejores resultados |
| Filtra respuestas 403    | A veces son rutas protegidas que también son interesantes                  |
| Guarda los resultados    | Usa `-o` para mantener un registro                                         |
| Usa en conjunto con Burp | Puedes validar rutas sospechosas con Burp Suite                            |

---

### 🚨 Precaución

- **No escanees sitios que no tengas permiso de auditar.**
- Esto puede causar **bloqueos**, especialmente si usas muchos hilos o atacas servidores reales sin autorización.

---

### ✅ Resumen final

| Herramienta  | Propósito                                                             |
| ------------ | --------------------------------------------------------------------- |
| **Gobuster** | Escanear directorios ocultos en aplicaciones web                      |
| **SecLists** | Wordlists listas para usar (archivos, contraseñas, subdominios, etc.) |

Juntos, son una combinación poderosa para **reconocimiento web y pruebas de seguridad**.

---

[🔼](#índice)

---

## **333. Análisis de vulnerabilidades: OWASP ZAP Proxy**

### 🧠 ¿Qué es OWASP ZAP?

**OWASP ZAP (Zed Attack Proxy)** es una herramienta gratuita y de código abierto desarrollada por OWASP para detectar vulnerabilidades en aplicaciones web. Actúa como un **proxy entre el navegador y el sitio web**, interceptando y analizando las peticiones y respuestas.

### 🔒 ¿Qué puede hacer ZAP?

- Escaneo automático de vulnerabilidades web
- Intercepción y modificación de peticiones HTTP/S
- Análisis de contenido web
- Descubrimiento de endpoints ocultos
- Fuerza bruta de autenticación
- Pruebas manuales de seguridad

---

### ✅ Características principales

| Característica          | Descripción                                    |
| ----------------------- | ---------------------------------------------- |
| **Interceptar tráfico** | Puedes ver y modificar peticiones/respuestas   |
| **Scan activo/pasivo**  | Encuentra vulnerabilidades automáticamente     |
| **Spider**              | Descubre rutas de una aplicación               |
| **Fuzzer**              | Prueba entradas con múltiples datos maliciosos |
| **Scripting**           | Automatiza tareas personalizadas               |
| **Integración**         | Compatible con CI/CD y otras herramientas      |

---

### 💻 Instalación de OWASP ZAP

#### ✅ 1. Requisitos

- Java 8 o superior
- Sistema: Windows, Linux o macOS

#### ✅ 2. Métodos de instalación

##### 🔹 Opción 1: Instalador oficial (GUI)

1. Ve a la web oficial:
   👉 [https://www.zaproxy.org/download/](https://www.zaproxy.org/download/)

2. Descarga la versión para tu sistema (Windows/Linux/macOS).

3. Instálalo como cualquier otro programa.

##### 🔹 Opción 2: Snap (Linux)

```bash
sudo snap install zaproxy --classic
```

##### 🔹 Opción 3: Docker

```bash
docker run -u zap -p 8080:8080 -i owasp/zap2docker-stable zap.sh
```

---

### 🔧 Primeros pasos: configurando el proxy

#### Paso 1: Ejecuta OWASP ZAP

- Si estás en Linux, ejecuta:

```bash
zaproxy
```

- En Windows/macOS, abre el programa como cualquier aplicación.

#### Paso 2: Configura tu navegador (Firefox recomendado)

1. Abre Firefox.
2. Ve a **Preferencias > Red > Configuración**.
3. Cambia a:

   - **Servidor proxy HTTP**: `127.0.0.1`
   - **Puerto**: `8080`
   - Marca la opción “Usar este proxy para todos los protocolos”.

Esto hace que todo el tráfico pase por ZAP.

#### Paso 3: Visita cualquier web (por ejemplo `http://testphp.vulnweb.com`)

ZAP capturará y mostrará todas las peticiones HTTP.

---

### 🚀 Ejemplo completo: Análisis de vulnerabilidades

#### 🎯 Objetivo: Escanear `http://testphp.vulnweb.com`

#### Paso 1: Spider (exploración de rutas)

1. En ZAP, haz clic derecho sobre `http://testphp.vulnweb.com` en la columna izquierda.
2. Elige **Attack > Spider Site**.
3. Espera a que termine. Esto identifica todas las URLs de la página.

#### Paso 2: Escaneo pasivo (automático)

- Mientras navegas por la página con Firefox, ZAP detectará posibles vulnerabilidades automáticamente (XSS, cookies inseguras, etc.).

#### Paso 3: Escaneo activo

1. Haz clic derecho en el sitio.
2. Selecciona **Attack > Active Scan**.
3. Inicia el escaneo. Esto realiza pruebas automáticas activas (inyección SQL, XSS, etc.).

#### Paso 4: Resultados

Ve a la pestaña **Alerts** y revisa los hallazgos. Por ejemplo:

| Tipo de vulnerabilidad | Descripción                                  |
| ---------------------- | -------------------------------------------- |
| Reflected XSS          | Entrada de usuario sin validación            |
| SQL Injection          | Parámetros vulnerables a inyecciones         |
| Insecure Cookies       | Cookies sin la bandera `HttpOnly` o `Secure` |
| Server Info Disclosure | Fugas de versión del servidor                |

---

### 🧠 Consejos de uso

| Consejo                      | Detalle                                               |
| ---------------------------- | ----------------------------------------------------- |
| No uses ZAP sin autorización | Puede ser detectado como ataque real                  |
| Usa Firefox o Chromium       | Son los más compatibles                               |
| Automatiza con scripts       | Puedes usar Python o Groovy para escaneos programados |
| Puedes integrarlo a CI/CD    | Ideal para DevSecOps                                  |

---

### 🧪 ¿Cómo usar ZAP desde la terminal (modo headless)?

```bash
zap.sh -daemon -port 8080 -host 127.0.0.1 -config api.disablekey=true
```

Y luego escanear un sitio:

```bash
zap-cli --zap-url http://127.0.0.1 -p 8080 quick-scan --self-contained http://testphp.vulnweb.com
```

---

### ✅ Resumen

| Elemento             | Descripción                                                               |
| -------------------- | ------------------------------------------------------------------------- |
| **Herramienta**      | OWASP ZAP Proxy                                                           |
| **Propósito**        | Detectar vulnerabilidades web                                             |
| **Instalación**      | GUI, Snap, Docker                                                         |
| **Modo de uso**      | Proxy, Spider, Escaneo pasivo y activo                                    |
| **Recomendado para** | Pentesters, developers, bug bounty hunters, estudiantes de ciberseguridad |

---

[🔼](#índice)

---

## **334. Nikto y Skipfish**

### 🔍 ¿Qué son Nikto y Skipfish?

#### 🛠️ Nikto

- **Nikto** es un escáner de servidores web de código abierto.
- Busca **archivos peligrosos**, **configuraciones erróneas**, **versiones antiguas de software**, etc.
- Es **rápido, simple** y se usa desde la terminal.
- Desarrollado en **Perl**.

#### 🛠️ Skipfish

- **Skipfish** es un escáner de seguridad web creado por Google.
- Usa técnicas de **fuzzing inteligente** y mapea sitios web mientras analiza.
- Su salida es un **reporte HTML interactivo** muy completo.
- Está hecho en **C**, lo que lo hace rápido y eficiente.

---

### 🧩 Diferencias clave

| Herramienta  | Lenguaje | Salida        | Mejor para...            |
| ------------ | -------- | ------------- | ------------------------ |
| **Nikto**    | Perl     | Texto plano   | Detectar errores comunes |
| **Skipfish** | C        | Reportes HTML | Mapeo profundo y fuzzing |

---

### 🧪 ¿Qué buscan Nikto y Skipfish?

- Directorios sensibles (`/admin`, `/phpmyadmin`)
- Archivos de backup (`index.php~`, `config.old`)
- Errores de seguridad (XSS, CSRF, SQLi en formularios)
- Versiones inseguras de software (Apache, PHP, WordPress)
- Cookies inseguras, cabeceras mal configuradas, etc.

---

### 🖥️ Instalación paso a paso

#### 🔧 Nikto

##### ✅ En Kali Linux / Debian

```bash
sudo apt update
sudo apt install nikto
```

##### ✅ En cualquier Linux (desde GitHub)

```bash
git clone https://github.com/sullo/nikto.git
cd nikto/program
chmod +x nikto.pl
```

Puedes ejecutarlo con:

```bash
perl nikto.pl -h http://localhost
```

---

#### 🔧 Skipfish

##### ✅ En Kali Linux

```bash
sudo apt update
sudo apt install skipfish
```

##### ✅ En Ubuntu/Debian (manual)

```bash
sudo apt install git build-essential libidn11-dev libssl-dev
git clone https://github.com/spinkham/skipfish.git
cd skipfish
make
```

Para ejecutarlo:

```bash
./skipfish -o reporte http://localhost
```

---

### 🚀 Ejemplos prácticos y fáciles

#### 🧪 Ejemplo completo con **Nikto**

Escanear un servidor web (por ejemplo `http://testphp.vulnweb.com`):

```bash
nikto -h http://testphp.vulnweb.com
```

🔍 **¿Qué verás en los resultados?**

- Software detectado: Apache/2.2.8
- Directorios inseguros: `/admin`, `/uploads`
- Archivos públicos: `/test.php`, `/config.php.bak`
- Cabeceras mal configuradas: Falta de `X-Frame-Options`, `Strict-Transport-Security`, etc.

---

#### 🧪 Ejemplo completo con **Skipfish**

Escanear el mismo sitio con Skipfish y generar reporte HTML:

```bash
skipfish -o resultado-skipfish http://testphp.vulnweb.com
```

📁 Se creará una carpeta `resultado-skipfish` con un archivo `index.html`. Ábrelo en tu navegador.

🔍 **¿Qué verás en el reporte?**

- Mapa del sitio escaneado
- Posibles vulnerabilidades
- Entradas de formularios analizadas
- Seguridad de cookies
- Errores HTTP (403, 500, etc.)
- Sugerencias de mitigación

---

### ✅ Consejos de uso

| Consejo                       | Nikto | Skipfish         |
| ----------------------------- | ----- | ---------------- |
| Rápido para checklist básica  | ✅    | ❌               |
| Requiere poco conocimiento    | ✅    | ❌ (más técnico) |
| Reporte gráfico y detallado   | ❌    | ✅               |
| Ideal para bug bounty         | ✅    | ✅               |
| Analiza profundidad del sitio | ❌    | ✅               |

---

### ⚠️ Precauciones

- Ambas herramientas pueden generar mucho tráfico: **NO las uses sin permiso.**
- Pueden ser detectadas por firewalls como comportamiento sospechoso.
- Usa un entorno de pruebas o laboratorios como:

  - `http://testphp.vulnweb.com`
  - `https://www.hackthebox.com/`
  - `https://www.tryhackme.com/`

---

### 📌 Resumen

| Herramienta | Función Principal   | Comando                             |
| ----------- | ------------------- | ----------------------------------- |
| Nikto       | Escaneo básico web  | `nikto -h http://target`            |
| Skipfish    | Fuzzing + mapeo web | `skipfish -o carpeta http://target` |

---

[🔼](#índice)

---

## **335. Nuclei y Nuclei Templates**

### 🧠 ¿Qué es **Nuclei**?

**Nuclei** es una **herramienta de escaneo de vulnerabilidades** súper rápida desarrollada por **ProjectDiscovery**. Escanea objetivos web (URLs, IPs, etc.) en busca de **vulnerabilidades conocidas**, **archivos sensibles**, **cabeceras mal configuradas**, etc.

📌 Lo más poderoso de Nuclei es que usa **templates** (plantillas YAML) para definir **qué tipo de vulnerabilidades buscar**. Tú puedes usar miles ya creadas o escribir las tuyas.

---

### 📦 ¿Qué son los **Nuclei Templates**?

- Son **archivos en YAML** que definen un patrón de ataque o verificación.
- Pueden detectar:

  - CVEs conocidas (como CVE-2023-XXXXX)
  - Exposición de archivos (`.env`, `.git`, `wp-config.php`)
  - Headers mal configurados (CORS, CSP, etc.)
  - Paneles admin, login, subdominios, etc.

👉 Hay miles disponibles en el repositorio oficial:

[https://github.com/projectdiscovery/nuclei-templates](https://github.com/projectdiscovery/nuclei-templates)

---

### 🛠️ ¿Cómo se instala **Nuclei**?

#### ✅ En Kali Linux, Ubuntu, Debian o WSL (recomendado)

```bash
sudo apt update
sudo apt install git curl
```

#### 📥 Instalar Nuclei (binario oficial)

```bash
curl -s https://api.github.com/repos/projectdiscovery/nuclei/releases/latest \
| grep "browser_download_url.*linux_amd64.zip" \
| cut -d '"' -f 4 \
| wget -i -

unzip nuclei_*_linux_amd64.zip
chmod +x nuclei
sudo mv nuclei /usr/local/bin/
```

✅ Verifica instalación:

```bash
nuclei -version
```

---

### 📦 ¿Cómo se instalan los **templates**?

Ejecuta el siguiente comando (solo la primera vez o cuando quieras actualizar):

```bash
nuclei -update-templates
```

Esto crea una carpeta en `~/.local/nuclei-templates/` con más de **3000 plantillas** actualizadas desde GitHub.

---

### 🚀 Ejemplo completo y fácil de entender

#### 🎯 Objetivo: Analizar un sitio web en busca de vulnerabilidades

Usaremos un sitio de pruebas: `http://testphp.vulnweb.com`

```bash
nuclei -u http://testphp.vulnweb.com
```

🔍 Este comando:

- Escanea esa URL con las plantillas predeterminadas.
- Analiza vulnerabilidades básicas: headers, archivos expuestos, etc.
- Muestra resultados directamente en la terminal.

---

#### 📁 Resultado típico:

```bash
[info] [http] [exposure] .git folder found http://testphp.vulnweb.com/.git/
[low] [cve] Apache version outdated http://testphp.vulnweb.com/ [CVE-2017-3167]
[medium] [misconfiguration] X-Frame-Options header not set
```

---

### 🧠 ¿Y si quiero escanear con un tipo de plantilla específico?

#### Escanear solo en busca de CVEs:

```bash
nuclei -u http://testphp.vulnweb.com -t cves/
```

#### Escanear con múltiples URLs desde archivo:

```bash
cat sitios.txt
```

```txt
https://midominio.com
https://empresa.com/login
```

```bash
nuclei -l sitios.txt
```

---

### 🛠️ Crear tu propia plantilla personalizada (opcional)

Ejemplo: verificar si una URL devuelve el header `X-Powered-By: PHP`

```yaml
id: custom-x-powered-check

info:
  name: Check X-Powered-By Header
  author: gussdev
  severity: info

requests:
  - method: GET
    path:
      - "{{BaseURL}}"
    matchers:
      - type: word
        part: header
        words:
          - "X-Powered-By: PHP"
```

Guárdalo como `myheader.yaml` y ejecuta:

```bash
nuclei -u http://example.com -t myheader.yaml
```

---

### 💡 Consejos útiles

| Comando                    | Descripción                                |
| -------------------------- | ------------------------------------------ |
| `nuclei -update-templates` | Descarga las plantillas más recientes      |
| `nuclei -t exposures/`     | Escanea solo por exposiciones              |
| `nuclei -l urls.txt`       | Escanea múltiples URLs desde archivo       |
| `nuclei -json`             | Salida en formato JSON (útil para scripts) |
| `nuclei -silent`           | Muestra solo hallazgos, sin logs           |

---

### 🔐 ⚠️ ¿Es legal usar Nuclei?

✅ **Sí**, si:

- Lo usas con **permiso** (tu propia web o entorno de pruebas).
- No haces DoS o algo destructivo.

  ❌ **No**, si:

- Atacas objetivos sin autorización (es ilegal y antiético).

---

### 🧪 ¿Dónde practicar legalmente?

- [https://testphp.vulnweb.com/](https://testphp.vulnweb.com/)
- [https://demo.testfire.net/](https://demo.testfire.net/)
- [https://tryhackme.com/](https://tryhackme.com/)
- [https://www.hackthebox.com/](https://www.hackthebox.com/)

---

### 🧾 Resumen

| Herramienta | Función                                                       | Tipo de salida |
| ----------- | ------------------------------------------------------------- | -------------- |
| Nuclei      | Escáner web de vulnerabilidades basado en plantillas YAML     | Consola, JSON  |
| Templates   | Plantillas que definen qué buscar (CVE, leaks, headers, etc.) | Actualizables  |

---

[🔼](#índice)

---

## **336. Fuzzing básico con ffuf**

### 🧠 ¿Qué es FFUF?

**FFUF (Fuzz Faster U Fool)** es una herramienta de línea de comandos para hacer **fuzzing** de contenido web. Su propósito principal es:

- Descubrir **archivos y directorios ocultos** en un sitio web.
- Buscar **parámetros** o **subdominios** válidos.
- Hacer pruebas de fuerza bruta sobre APIs, rutas REST, etc.

---

### 🛠️ Instalación de FFUF

#### ✅ En Kali Linux (ya viene instalado en versiones nuevas)

Verifica con:

```bash
ffuf -h
```

#### 🐧 En Ubuntu/Debian o WSL

1. Instala `Go` (lenguaje en el que está escrito ffuf):

```bash
sudo apt update
sudo apt install golang -y
```

2. Instala `ffuf` desde GitHub:

```bash
go install github.com/ffuf/ffuf/v2@latest
```

3. Agrega `ffuf` al PATH:

```bash
echo 'export PATH=$PATH:$(go env GOPATH)/bin' >> ~/.bashrc
source ~/.bashrc
```

✅ Ahora puedes usarlo con:

```bash
ffuf -h
```

---

### 📁 ¿Qué necesitas para hacer fuzzing?

1. Un sitio web objetivo.
2. Una **wordlist** (lista de palabras) para probar.
   Ejemplo: `/usr/share/seclists/Discovery/Web-Content/common.txt`

   Instala seclists (si no lo tienes):

   ```bash
   sudo apt install seclists
   ```

---

### 🚀 Ejemplo básico de Fuzzing con FFUF

#### 🎯 Objetivo: Encontrar rutas ocultas en un sitio de pruebas

Usaremos: `http://testphp.vulnweb.com`

```bash
ffuf -u http://testphp.vulnweb.com/FUZZ -w /usr/share/seclists/Discovery/Web-Content/common.txt
```

📌 Qué significa:

| Opción | Significado                                                                      |
| ------ | -------------------------------------------------------------------------------- |
| `-u`   | URL objetivo. La palabra **FUZZ** será reemplazada por cada palabra de la lista. |
| `-w`   | Wordlist usada.                                                                  |

#### 🖥️ Resultado esperado:

```bash
/backup              [Status: 403, Size: 279]
/admin               [Status: 200, Size: 4112]
/uploads             [Status: 200, Size: 1992]
```

💡 Esto significa que `/admin` y `/uploads` son rutas válidas que **no estaban enlazadas directamente** en la web.

---

### 📄 Otros ejemplos útiles

#### 🔹 Buscar archivos `.php` ocultos:

```bash
ffuf -u http://target.com/FUZZ.php -w /usr/share/seclists/Discovery/Web-Content/common.txt
```

#### 🔹 Fuzzing en parámetros GET (por ejemplo: `?id=FUZZ`):

```bash
ffuf -u "http://target.com/page.php?id=FUZZ" -w /usr/share/seclists/Fuzzing/1000-common-words.txt
```

#### 🔹 Filtrar por código de respuesta

```bash
ffuf -u http://target.com/FUZZ -w wordlist.txt -fc 404
```

Esto oculta todas las respuestas con código 404.

---

### 💬 Personaliza la salida

- `-t`: cantidad de hilos (más rápido): `-t 100`
- `-mc`: filtrar por código de respuesta (match code): `-mc 200`
- `-of json`: salida en formato JSON para usar en scripts

---

### 🧪 Sitios para practicar legalmente

- [http://testphp.vulnweb.com/](http://testphp.vulnweb.com/)
- [http://dvwa.local](http://dvwa.local) (si instalas DVWA en local)
- [https://portswigger.net/web-security/](https://portswigger.net/web-security/) (laboratorios gratuitos)
- [https://tryhackme.com/](https://tryhackme.com/) y [https://hackthebox.com/](https://hackthebox.com/)

---

### 🧾 Resumen

| Herramienta    | FFUF                                                                         |
| -------------- | ---------------------------------------------------------------------------- |
| Propósito      | Fuzzing de rutas, archivos, parámetros web                                   |
| Instalación    | `go install github.com/ffuf/ffuf/v2@latest`                                  |
| Wordlists      | Usa Seclists (común: `/usr/share/seclists/Discovery/Web-Content/common.txt`) |
| Comando básico | `ffuf -u http://site.com/FUZZ -w wordlist.txt`                               |

---

[🔼](#índice)

---

## **337. Fuzzing avanzado con ffuf**

### 🧠 ¿Qué es el fuzzing avanzado?

El **fuzzing avanzado** con `ffuf` no solo implica buscar directorios o archivos, sino también:

- 🔍 Encontrar **parámetros ocultos**.
- 🌐 Descubrir **subdominios**.
- 📂 Buscar archivos con extensiones específicas.
- 💬 Atacar **puntos múltiples** en una sola URL (`-input-cmd`, `-request`, `-request-proto`).
- 🔐 Bypass de métodos HTTP, cabeceras, y más.

---

### 🛠️ Instalación de FFUF

#### En Kali Linux (ya viene preinstalado):

```bash
ffuf -h
```

#### En Ubuntu/Debian:

1. Instala Go:

```bash
sudo apt install golang -y
```

2. Instala ffuf:

```bash
go install github.com/ffuf/ffuf/v2@latest
```

3. Agrega ffuf al PATH:

```bash
echo 'export PATH=$PATH:$(go env GOPATH)/bin' >> ~/.bashrc
source ~/.bashrc
```

✅ Ahora puedes usar `ffuf`.

---

### 📁 Wordlists recomendadas

Instala Seclists si no lo tienes:

```bash
sudo apt install seclists
```

Ubicación: `/usr/share/seclists/`

---

### 🧪 1. Fuzzing avanzado de **parámetros GET**

#### Objetivo: descubrir parámetros ocultos como `?page=`, `?id=`, `?file=`, etc.

```bash
ffuf -u "http://target.com/index.php?FUZZ=test" -w /usr/share/seclists/Discovery/Web-Content/burp-parameter-names.txt -fs 0
```

| Opción  | Significado                                                                          |
| ------- | ------------------------------------------------------------------------------------ |
| `FUZZ`  | Lugar a reemplazar con cada palabra                                                  |
| `-fs 0` | Filtra respuestas del mismo tamaño que 0 bytes (útil para ignorar respuestas vacías) |

---

### 🧪 2. Fuzzing de archivos con extensión

Buscar archivos `.php`, `.bak`, `.zip`, `.old`, etc.:

```bash
ffuf -u "http://target.com/FUZZ" -w /usr/share/seclists/Discovery/Web-Content/raft-small-files.txt -e .php,.bak,.zip,.old -fc 404
```

| Bandera   | Explicación                                      |
| --------- | ------------------------------------------------ |
| `-e`      | Añade extensiones a cada palabra del diccionario |
| `-fc 404` | Oculta respuestas con código 404                 |

---

### 🧪 3. Fuzzing de subdominios

Buscar subdominios válidos con ffuf:

```bash
ffuf -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt -u http://FUZZ.target.com -fs 0
```

⚠️ Necesitas que el dominio tenga wildcard DNS desactivado o usar una herramienta combinada con `dnsx`.

---

### 🧪 4. Fuzzing doble: múltiples puntos `-w` (parámetro y valor)

#### Objetivo: probar combinaciones de parámetro y valor

```bash
ffuf -u "http://target.com/index.php?PARAM=VALUE" -w paramlist.txt:PARAM -w valuelist.txt:VALUE -fs 0
```

📁 `paramlist.txt`:

```
id
page
file
```

📁 `valuelist.txt`:

```
1
admin
index.html
```

Esto generará peticiones como:

- `index.php?id=1`
- `index.php?page=admin`
- `index.php=file=index.html`

---

### 🧪 5. Fuzzing de métodos HTTP

Buscar métodos habilitados como `PUT`, `DELETE`, `OPTIONS`, etc.

```bash
ffuf -X FUZZ -u http://target.com/index.php -w /usr/share/seclists/Discovery/Web-Content/web-methods.txt -mc 200,403
```

📁 `web-methods.txt` puede contener:

```
GET
POST
PUT
DELETE
OPTIONS
HEAD
```

---

### 🧪 6. Fuzzing con cabeceras personalizadas (bypass)

#### Ejemplo: intentar bypass con cabecera `X-Original-URL`

```bash
ffuf -w /usr/share/seclists/Discovery/Web-Content/common.txt -u http://target.com/ -H "X-Original-URL: /FUZZ" -fs 0
```

Esto intenta acceder a `/admin` por medio de la cabecera en lugar de la URL directa.

---

### 🧪 7. Fuzzing con un archivo de petición raw

Si capturas una petición con Burp Suite, puedes guardarla como `.txt` y hacer fuzzing sobre ella.

1. Guarda la petición como `request.txt`, reemplaza valores con `FUZZ`.

2. Ejecuta:

```bash
ffuf -request request.txt -w wordlist.txt -input-cmd FUZZ
```

---

### 📌 Ejemplo completo final

#### Objetivo: buscar archivos `.php`, `.bak`, `.zip` ocultos en un sitio vulnerable

```bash
ffuf -u http://testphp.vulnweb.com/FUZZ -w /usr/share/seclists/Discovery/Web-Content/raft-small-files.txt -e .php,.bak,.zip -fc 404 -t 50
```

- Descubre archivos como:

  - `login.php`
  - `config.bak`
  - `backup.zip`

---

### 🎓 Resumen

| Característica                | Uso                                   |
| ----------------------------- | ------------------------------------- |
| Fuzzing de parámetros         | `http://site.com/index.php?FUZZ=test` |
| Subdominios                   | `http://FUZZ.site.com`                |
| Archivos con extensión        | `FUZZ.php`, `FUZZ.bak`, etc.          |
| Fuzzing doble (param y valor) | `?PARAM=VALUE`                        |
| Métodos HTTP                  | `-X FUZZ`                             |
| Cabeceras personalizadas      | `-H "Header: FUZZ"`                   |
| Petición raw                  | `-request request.txt`                |

---

[🔼](#índice)

---

## **338. Explotación: Commix**

### 🧨 Explotación: **Commix (Command Injection Exploiter)**

---

### 🧠 ¿Qué es Commix?

**Commix (Command Injection Exploiter)** es una herramienta automatizada escrita en Python que permite detectar y explotar **vulnerabilidades de inyección de comandos del sistema operativo** (OS Command Injection) en aplicaciones web.

Una inyección de comandos ocurre cuando una aplicación web **pasa datos del usuario a un comando del sistema operativo**, sin validarlos adecuadamente. Esto puede permitirle a un atacante ejecutar comandos arbitrarios en el sistema.

---

### 📥 Instalación de Commix

#### 🔧 Requisitos previos

- Python 3.x
- Git

#### 📌 Instalación en Kali Linux (ya viene instalado normalmente):

```bash
commix --help
```

Si no está instalado, haz esto:

#### 💻 En Ubuntu / Debian

```bash
sudo apt update
sudo apt install git python3 -y
git clone https://github.com/commixproject/commix.git
cd commix
sudo python3 commix.py --help
```

Puedes dejarlo accesible globalmente con un alias:

```bash
echo "alias commix='python3 ~/commix/commix.py'" >> ~/.bashrc
source ~/.bashrc
```

---

### 🔍 ¿Cómo funciona?

Commix **automatiza el proceso de inyección de comandos**. Tiene varios modos de ataque y opciones, incluyendo:

- Inyección directa (`GET`, `POST`, `Cookie`, etc.)
- Auto detección de parámetros vulnerables
- Shell interactiva si logra explotar
- Soporte para cookies y autenticación
- Comandos personalizados

---

### 🎯 Escenario básico de ejemplo

Supongamos que tenemos una URL vulnerable como:

```
http://vulnerable.com/page.php?user=juan
```

Y el parámetro `user` no está filtrado y permite ejecutar comandos, como:

```
http://vulnerable.com/page.php?user=juan;ls
```

Commix puede detectar esto y automatizar el ataque.

---

### 🚀 Uso básico de Commix

```bash
python3 commix.py -u "http://vulnerable.com/page.php?user=juan"
```

Si hay vulnerabilidad, obtendrás una shell tipo:

```
commix(os-shell) >
```

Ejecuta comandos como:

```
whoami
ls -la
```

---

### ⚙️ Opciones útiles

| Opción        | Significado                                |
| ------------- | ------------------------------------------ |
| `--cookie`    | Pasar cookies si necesitas sesión          |
| `--data`      | Para inyección en formularios POST         |
| `--os-cmd`    | Ejecutar un comando directamente           |
| `--os-shell`  | Acceder a una shell remota                 |
| `--force-ssl` | Si el sitio está en HTTPS                  |
| `--auth-type` | Autenticación básica, NTLM, etc.           |
| `--technique` | Limitar tipo de inyección (`T`, `R`, etc.) |

---

#### 🧪 Ejemplo 1: Inyección en parámetro GET

```bash
python3 commix.py -u "http://testphp.vulnweb.com/artists.php?artist=1"
```

Este sitio es vulnerable a inyecciones.

---

#### 🧪 Ejemplo 2: Inyección en formulario POST

Si estás atacando un formulario con `user` y `pass`, puedes usar:

```bash
python3 commix.py --url "http://target.com/login.php" --data "user=admin&pass=test"
```

Si `user` o `pass` es vulnerable, Commix lo detectará.

---

#### 🧪 Ejemplo 3: Uso con cookies

```bash
python3 commix.py -u "http://target.com/panel.php?id=1" --cookie="PHPSESSID=abcd1234"
```

---

#### 🧪 Ejemplo 4: Ejecutar un comando directamente

```bash
python3 commix.py -u "http://target.com/item.php?id=5" --os-cmd whoami
```

---

### 🛡️ ¿Cómo evitar estas vulnerabilidades?

- Nunca ejecutar comandos con entradas del usuario.
- Usar funciones seguras (`subprocess.run()` con `shell=False` en Python).
- Validar, filtrar y sanitizar todos los inputs del usuario.
- Aplicar políticas de mínimo privilegio al servidor web.

---

### 🧩 Ejemplo completo final: DVWA

1. Instala DVWA (Damn Vulnerable Web Application) con Docker:

```bash
git clone https://github.com/digininja/DVWA
cd DVWA
sudo docker build -t dvwa .
sudo docker run -it -p 80:80 dvwa
```

2. Accede a: `http://localhost/setup.php`, configura y crea la DB.

3. En el panel, ve a “Command Injection”.

4. Prueba con Commix:

```bash
python3 commix.py -u "http://localhost/vulnerabilities/exec/?ip=127.0.0.1&Submit=Submit"
```

5. Si todo va bien, tendrás una shell del servidor web.

---

### 🧠 Conclusión

✅ **Commix** es ideal para detectar y explotar **inyecciones de comandos**, pero úsalo únicamente en entornos autorizados o de laboratorio.

---

[🔼](#índice)

---

## **339. Unas palabras sobre la fase de explotación**

### 🧠 ¿Qué es la Fase de Explotación?

La **fase de explotación** es una de las etapas más críticas durante una auditoría de seguridad o un pentest (test de penetración). Consiste en **aprovechar una vulnerabilidad detectada** para **obtener acceso** no autorizado o control sobre un sistema, servicio o aplicación.

En resumen:

> 🎯 **Objetivo**: Lograr acceso (inicial o extendido) explotando una debilidad real en el objetivo.

---

### 🛠️ ¿Qué tipo de vulnerabilidades se explotan?

Algunos ejemplos comunes incluyen:

| Tipo de vulnerabilidad                        | ¿Qué permite hacer?                          |
| --------------------------------------------- | -------------------------------------------- |
| **Inyección SQL**                             | Acceder o modificar una base de datos.       |
| **Inyección de comandos (Command Injection)** | Ejecutar comandos en el sistema operativo.   |
| **Fallas en autenticación**                   | Saltarse logins o acceder como otro usuario. |
| **RCE (Remote Code Execution)**               | Ejecutar código remoto en el servidor.       |
| **Desbordamiento de búfer**                   | Tomar control del flujo de un programa.      |
| **Cross-Site Scripting (XSS)**                | Inyectar scripts en navegadores.             |
| **Inyecciones en LDAP, XML, etc.**            | Manipular funciones internas.                |

---

### 🧪 Herramientas comunes en la explotación

- **Metasploit Framework**
- **Commix** (para command injection)
- **SQLMap** (para SQL injection)
- **Rubeus / Mimikatz** (en entornos Windows/AD)
- **Burp Suite** (para explotar vulnerabilidades web)
- **Exploit-DB** (para buscar exploits públicos)

---

### ⚠️ Consideraciones Éticas

Antes de explotar una vulnerabilidad:

- 📜 Debes tener **permiso legal** (auditoría contratada, CTF, laboratorio propio).
- 💾 Debes **documentar** cuidadosamente lo que explotas.
- 🧼 Intenta minimizar el impacto (no borres archivos ni afectes usuarios reales).
- ⏱️ Planea qué hacer tras la explotación: ¿elevar privilegios?, ¿movimiento lateral?, ¿persistencia?

---

### 🔧 Instalación de una herramienta de explotación: **Metasploit**

Metasploit es el marco más conocido para explotación.

#### ✅ En Kali Linux ya viene instalado

Solo corre:

```bash
msfconsole
```

#### 🐧 En Ubuntu / Debian

```bash
sudo apt update
sudo apt install metasploit-framework -y
msfconsole
```

#### 🐳 Con Docker

```bash
docker pull metasploitframework/metasploit-framework
docker run -it metasploitframework/metasploit-framework
```

---

### 🎯 Ejemplo completo: Explotar una vulnerabilidad real en DVWA (Damn Vulnerable Web App)

#### 1. Instala DVWA en local (con Docker)

```bash
git clone https://github.com/digininja/DVWA.git
cd DVWA
docker-compose up -d
```

Accede en tu navegador a `http://localhost` y configura la base de datos desde `http://localhost/setup.php`.

#### 2. Activa el nivel de seguridad en **"Low"**.

#### 3. Inyección de comandos en la sección **"Command Injection"**

En el input, pon:

```
127.0.0.1; whoami
```

Verás el resultado del comando inyectado.

#### 4. Explotación con Commix (opcional)

```bash
python3 commix.py -u "http://localhost/vulnerabilities/exec/?ip=127.0.0.1&Submit=Submit"
```

Y si es vulnerable, podrás ejecutar comandos como:

```bash
ls
cat /etc/passwd
```

---

### 🧠 ¿Qué pasa después?

Una vez explotada la vulnerabilidad, las fases siguientes podrían ser:

- **Post-explotación**: Obtener más información del sistema, usuarios, contraseñas.
- **Elevación de privilegios**: Convertirte en administrador/root.
- **Persistencia**: Dejar puertas traseras o crear usuarios ocultos.
- **Movimiento lateral**: Saltar a otros sistemas de la red.
- **Extracción de datos (exfiltración)**: Descargar información sensible.

---

### 🧾 Resumen

| Paso                                   | Descripción               |
| -------------------------------------- | ------------------------- |
| 1️⃣ Identificar vulnerabilidad          | Inyección, RCE, etc.      |
| 2️⃣ Verificar que se pueda explotar     | Manual o con herramientas |
| 3️⃣ Ejecutar código o comando malicioso | Gana acceso               |
| 4️⃣ Obtener control o más información   | Shell, datos, privilegios |
| 5️⃣ Documentar todo                     | Para el reporte final     |

---

### ✅ Conclusión

- La fase de explotación es **clave para demostrar el impacto real** de una vulnerabilidad.
- Debe hacerse de forma **controlada y ética**.
- Herramientas como **Metasploit**, **Commix**, **SQLMap** o **Burp Suite** son tus mejores aliadas.
- El objetivo no es destruir, sino aprender y fortalecer la seguridad.

---

[🔼](#índice)

---

## **340. Changeme, Gitleaks y CyberChef**

### 1. 🔐 **Changeme**

#### ¿Qué es?

Changeme es una herramienta diseñada para **detectar credenciales por defecto** en dispositivos y servicios (como routers, servidores web, bases de datos, etc.). Sirve para pentesters que quieren saber si alguien dejó una contraseña como `admin:admin` o `root:toor`.

---

#### 🔧 Instalación

**Requisitos**: Python 3 y Git.

```bash
git clone https://github.com/ztgrace/changeme.git
cd changeme
pip3 install -r requirements.txt
```

Luego puedes ejecutar:

```bash
python3 changeme/changeme.py -h
```

---

#### 🎯 Ejemplo fácil

```bash
python3 changeme/changeme.py -t http://192.168.1.1
```

> Esto intenta acceder al panel web del router con contraseñas por defecto. Si entra, ¡lo detectará!

---

#### 2. 🔍 **Gitleaks**

#### ¿Qué es?

Gitleaks es una herramienta que **busca secretos filtrados** en repositorios Git, como:

- Claves API
- Tokens
- Contraseñas
- Claves privadas SSH
- AWS secrets, etc.

Ideal para Bug Bounty y revisiones de código.

---

#### 🔧 Instalación

##### ✅ En Linux o Mac (vía curl):

```bash
curl -sSL https://github.com/gitleaks/gitleaks/releases/latest/download/gitleaks-linux-amd64 -o gitleaks
chmod +x gitleaks
sudo mv gitleaks /usr/local/bin/
```

##### ✅ En Windows

1. Descarga el binario desde: [https://github.com/gitleaks/gitleaks/releases](https://github.com/gitleaks/gitleaks/releases)
2. Agrega el binario a tu `PATH`.

---

#### 🎯 Ejemplo fácil

Analizar un repo local:

```bash
gitleaks detect --source .
```

Analizar un repo remoto:

```bash
gitleaks detect --source https://github.com/usuario/repositorio.git
```

> Si hay secretos filtrados, te los mostrará con el tipo, línea y archivo.

---

### 3. 🧙‍♂️ **CyberChef**

#### ¿Qué es?

CyberChef es una herramienta web de análisis y transformación de datos. Permite:

- Decodificar base64, JWT, hashes, etc.
- Desencriptar AES/RC4
- Buscar patrones
- Convertir entre formatos

> ¡Como un "cuchillo suizo" de datos para forense y CTF!

---

#### 🔧 ¿Cómo se instala?

CyberChef es una **webapp estática**, así que puedes usarla online o instalarla localmente.

##### ✅ Opción 1: Usar online

👉 [https://gchq.github.io/CyberChef/](https://gchq.github.io/CyberChef/)

##### ✅ Opción 2: Instalar local

```bash
git clone https://github.com/gchq/CyberChef.git
cd CyberChef
npm install
npm run build
```

Luego abre `CyberChef/dist/index.html` en tu navegador.

---

#### 🎯 Ejemplo fácil

Supón que tienes esta cadena:

```
U29tZSBzZWNyZXQgdGV4dA==
```

Esto es **Base64**.

1. Ve a CyberChef.
2. Arrastra "From Base64" al panel de recetas.
3. Pega la cadena en el input.

✔️ Resultado: `Some secret text`

---

### 🧪 Ejemplo completo integrando las 3 herramientas

#### Escenario:

Eres un pentester y:

1. Accediste a un router en `192.168.1.1`.
2. Encontraste un repositorio Git en `/var/www/html/.git`.
3. Extrajiste los datos y encontraste cadenas sospechosas.

#### Paso a paso:

##### 1. **Detectar credenciales por defecto**

```bash
python3 changeme/changeme.py -t http://192.168.1.1
```

Resultado: `✓ Default credentials found: admin:admin`

##### 2. **Escanear el repo con Gitleaks**

```bash
gitleaks detect --source ./repositorio-extraido/
```

Resultado: Encontró una clave AWS y un token JWT.

##### 3. **Analizar el token en CyberChef**

- Usa “JWT Decode” o “From Base64”.
- Verifica si hay credenciales embebidas o datos de usuario.

---

### ✅ Conclusión

| Herramienta | Para qué sirve                          | Ideal para                        |
| ----------- | --------------------------------------- | --------------------------------- |
| Changeme    | Detectar credenciales por defecto       | Pentest de redes, IoT, servidores |
| Gitleaks    | Buscar secretos en código Git           | Bug Bounty, devsecops             |
| CyberChef   | Analizar, decodificar y convertir datos | Forense digital, CTF, reversing   |

---

[🔼](#índice)

---

| **Inicio**         | **atrás 3**                                                  | **Siguiente 5**                                |
| ------------------ | ------------------------------------------------------------ | ---------------------------------------------- |
| [🏠](../README.md) | [⏪](./5_3_Acceso_a_credenciales_y_movimientos_laterales.md) | [⏩](./5_5_Deteccion_y_Evasion_de_defensas.md) |
