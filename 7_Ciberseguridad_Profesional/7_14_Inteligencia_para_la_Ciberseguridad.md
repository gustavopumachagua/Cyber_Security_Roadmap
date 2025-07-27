| **Inicio**         | **atrás 13**                  | **Siguiente 15**                                              |
| ------------------ | ----------------------------- | ------------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./7_13_Hacking_Etico.md) | [⏩](./7_15_Escaneo_Activo_y_Analisis_de_Vulnerabilidades.md) |

---

## **Índice**

| Temario                                                                                                                              |
| ------------------------------------------------------------------------------------------------------------------------------------ |
| [893. ¿Qué es la inteligencia?](#893-qué-es-la-inteligencia)                                                                         |
| [894. El ciclo de la inteligencia](#894-el-ciclo-de-la-inteligencia)                                                                 |
| [895. Inteligencia para la ciberseguridad](#895-inteligencia-para-la-ciberseguridad)                                                 |
| [896. Mapeo de aplicaciones web y análisis de archivos de interés](#896-mapeo-de-aplicaciones-web-y-análisis-de-archivos-de-interés) |
| [897. Base de datos WHO IS](#897-base-de-datos-who-is)                                                                               |
| [898. Way Back Machine](#898-way-back-machine)                                                                                       |
| [899. Reverse IP lookup](#899-reverse-ip-lookup)                                                                                     |
| [900. Google Hacking](#900-google-hacking)                                                                                           |
| [901. Análisis de fuga de información](#901-análisis-de-fuga-de-información)                                                         |
| [902. Enumeración de subdominios](#902-enumeración-de-subdominios)                                                                   |
| [903. Análisis de metadatos con Foca](#903-análisis-de-metadatos-con-foca)                                                           |
| [904. Análisis de servidores con Shodan](#904-análisis-de-servidores-con-shodan)                                                     |
| [905. Enumeración de correos electrónicos](#905-enumeración-de-correos-electrónicos)                                                 |
| [906. Análisis de números telefónicos](#906-análisis-de-números-telefónicos)                                                         |
| [907. Investigación de individuos por su nombre](#907-investigación-de-individuos-por-su-nombre)                                     |
| [908. Investigación de redes sociales por nickname](#908-investigación-de-redes-sociales-por-nickname)                               |
| [909. Análisis reverso de imágenes](#909-análisis-reverso-de-imágenes)                                                               |
| [910. Análisis de datos en Twitter y Whatsapp](#910-análisis-de-datos-en-twitter-y-whatsapp)                                         |
| [911. Investigaciones en Facebook](#911-investigaciones-en-facebook)                                                                 |
| [912. Maltego](#912-maltego)                                                                                                         |

# **Inteligencia para la Ciberseguridad**

## **893. ¿Qué es la inteligencia?**

### 🧠 1. ¿Qué es la inteligencia? (En sentido general)

#### ✅ **Definición básica:**

La **inteligencia** es la capacidad que tiene una persona o sistema para **adquirir conocimientos, comprender, razonar, resolver problemas y adaptarse al entorno**.

#### 📌 Características clave:

- **Aprender de la experiencia**
- **Resolver problemas**
- **Adaptarse a nuevas situaciones**
- **Comprender conceptos complejos**
- **Tomar decisiones informadas**

---

#### 🎓 Ejemplo fácil de entender (vida diaria):

Imagina que estás en un país donde no hablan tu idioma. Al principio no entiendes nada. Pero poco a poco:

- Observas cómo saludan.
- Aprendes algunas palabras.
- Usas gestos para comunicarte.
- Y finalmente puedes comprar comida o pedir ayuda.

👉 Eso es **inteligencia en acción**: **adaptación + aprendizaje**.

---

#### 📘 Tipos de inteligencia (según Howard Gardner)

Howard Gardner propuso que no hay una sola inteligencia, sino varias. Aquí algunos ejemplos:

| Tipo de inteligencia | Ejemplo común                                                |
| -------------------- | ------------------------------------------------------------ |
| Lógico-matemática    | Resolver acertijos, cálculos mentales                        |
| Lingüística          | Expresar ideas con claridad, escribir, hablar varios idiomas |
| Musical              | Tocar instrumentos, identificar tonos                        |
| Espacial             | Leer mapas, imaginar objetos en 3D                           |
| Corporal-cinestésica | Habilidad para deportes, baile, usar herramientas            |
| Interpersonal        | Entender a otros, trabajar en equipo                         |
| Intrapersonal        | Conocerse a sí mismo, autocontrol                            |
| Naturalista          | Entender la naturaleza, clasificar plantas/animales          |

---

### 🛡️ 2. ¿Qué es la inteligencia? (En ciberseguridad o contexto militar)

En este contexto, **la inteligencia** se refiere a la **recolección y análisis de información** para anticiparse a amenazas o tomar decisiones estratégicas.

#### ✅ Definición:

> Conjunto de actividades y procesos para obtener información crítica sobre personas, sistemas, amenazas, vulnerabilidades o comportamientos.

---

### 🔍 Ejemplo en ciberseguridad:

Supón que una empresa recibe muchos ataques cibernéticos. El equipo de seguridad:

1. Analiza los correos sospechosos (phishing).
2. Investiga direcciones IP que intentan acceder al sistema.
3. Identifica patrones (por ejemplo, que todos vienen desde la misma región).
4. Crea reglas de firewall o alerta a los usuarios.

👉 Todo eso es parte de la **inteligencia de amenazas (Threat Intelligence)**.

---

### 🛠️ ¿Cómo se instala o aplica la inteligencia?

**No se instala como un software**, pero sí se puede **implementar como procesos, herramientas y hábitos** según el contexto.

#### 🧠 En personas:

- **Estudia, practica, reflexiona, aprende** de errores.
- Usa técnicas como mapas mentales, juegos de lógica, etc.

#### 💻 En ciberseguridad:

- Usa herramientas como:

  - **OSINT Framework** (inteligencia de fuentes abiertas)
  - **Threat Intelligence Platforms** (como MISP)
  - **SIEMs** (como Splunk o AlienVault)

---

### ✅ Ejemplo completo y sencillo

#### 🎯 Ejemplo práctico en la vida real:

**Situación:** Tienes que cocinar una receta que nunca has hecho.

1. Buscas información (YouTube, recetas escritas).
2. Compras los ingredientes.
3. Sigues instrucciones, pero adaptas si falta algo.
4. Aprendes qué funcionó o no para la próxima vez.

👉 Esa es una muestra clara de **inteligencia general**: observas, analizas, decides y aprendes.

---

### 💻 Ejemplo práctico en ciberseguridad:

**Situación:** Un atacante usa una dirección IP sospechosa para hacer fuerza bruta a un sistema.

1. Recolectas logs del servidor.
2. Identificas la IP y el patrón de ataque.
3. Buscas información de esa IP en OSINT (por ejemplo, AbuseIPDB).
4. Determinas que es parte de una botnet.
5. Bloqueas la IP y creas una regla para bloquear IPs similares.

👉 Esto es un ejemplo real de **uso de inteligencia en ciberseguridad**.

---

### 🧠 Resumen Final

| Contexto       | ¿Qué es inteligencia?                          | Ejemplo fácil                  |
| -------------- | ---------------------------------------------- | ------------------------------ |
| General        | Capacidad de aprender y resolver problemas     | Aprender a cocinar o adaptarse |
| Educativo      | Conjunto de habilidades múltiples              | Musical, lógica, social, etc.  |
| Ciberseguridad | Procesos para anticipar y responder a amenazas | Analizar IPs sospechosas       |
| Militar        | Información clave para decisiones estratégicas | Vigilar movimientos enemigos   |

---

[🔼](#índice)

---

## **894. El ciclo de la inteligencia**

### 🧠 ¿Qué es el ciclo de la inteligencia?

Es el **proceso estructurado** que siguen las organizaciones (militares, policiales, de ciberseguridad, etc.) para **convertir información cruda en inteligencia útil** para la toma de decisiones.

Este ciclo **no es solo para espías o hackers éticos**; también se usa en empresas, gobiernos y seguridad informática para **anticipar amenazas, prevenir ataques o tomar decisiones estratégicas.**

---

### 🔄 Fases del ciclo de la inteligencia

El ciclo tiene **5 etapas principales**. Aquí te explico cada una de forma simple y con ejemplos:

---

#### 🔹 1. **Planificación y dirección**

Es decidir **qué información se necesita**, **para qué** y **cómo se va a recolectar**.

📌 **Ejemplo fácil**: Eres el jefe de seguridad de una empresa. Quieres saber si algún grupo de hackers está apuntando a tu organización.

Entonces planificas:

- ¿Qué vas a investigar? → amenazas dirigidas a tu empresa.
- ¿Cómo? → OSINT, foros, redes sociales, logs, etc.

---

#### 🔹 2. **Recolección**

Es la etapa donde **obtienes la información** desde diversas fuentes.

📌 **Fuentes comunes:**

- Logs de servidores
- Análisis de red
- Redes sociales (OSINT)
- Deep/Dark web
- Herramientas como Shodan, Maltego, Spiderfoot

📌 **Ejemplo fácil**:

- Usas Google Hacking para encontrar datos públicos de tu dominio.
- Usas `whois` para saber quién registró un dominio sospechoso.

---

#### 🔹 3. **Procesamiento**

Conviertes la **información cruda en datos útiles**.

📌 Aquí puedes:

- Traducir documentos en otro idioma.
- Organizar los datos.
- Filtrar información duplicada o irrelevante.

📌 **Ejemplo fácil**:

- Tienes 100 archivos de logs.
- Filtras solo los errores 403 y 500 que ocurrieron con una IP específica.

---

#### 🔹 4. **Análisis y producción**

Aquí **interpretas los datos procesados** para encontrar patrones, relaciones y conclusiones.

📌 **Ejemplo fácil**:

- Encuentras que los ataques se hacen cada día a la misma hora, desde una IP en Rusia.
- Descubres que están usando un exploit conocido (CVE).

Con esa información puedes concluir que están automatizando ataques hacia una vulnerabilidad específica.

---

#### 🔹 5. **Difusión y retroalimentación**

Compartes los resultados con quienes deben actuar (equipo técnico, directivos, otras organizaciones).

📌 **Ejemplo fácil**:

- Generas un informe con:

  - IP maliciosa
  - Herramientas usadas
  - Horario de ataque
  - Recomendaciones para proteger el sistema

También recibes **feedback**: ¿Qué tan útil fue tu análisis? ¿Hay que mejorar la recolección o análisis?

---

### 🛠️ ¿Cómo se “instala” el ciclo de inteligencia?

No se instala como un software único, pero puedes **crear un entorno o stack de inteligencia** usando herramientas especializadas en cada fase:

| Fase                         | Herramientas recomendadas                 |
| ---------------------------- | ----------------------------------------- |
| Planificación                | MISP, TheHive (organizar investigaciones) |
| Recolección                  | Spiderfoot, Maltego, OSINT Framework      |
| Procesamiento                | Excel, Python scripts, Logstash           |
| Análisis y producción        | Kibana, Splunk, herramientas SIEM         |
| Difusión y retroalimentación | Informes PDF, dashboards, reportes a SOC  |

También puedes instalar un entorno de análisis usando **máquinas virtuales** con Kali Linux, herramientas OSINT y un sistema SIEM (como Wazuh o Security Onion).

---

### ✅ Ejemplo completo sencillo (modo historia)

#### 🎯 Caso realista:

Eres analista de seguridad en una universidad. Sospechan que están siendo espiados por un grupo externo.

1. **Planificación**: Definen que quieren investigar intentos de acceso externo al portal de estudiantes.

2. **Recolección**:

   - Usas `Nmap` para ver los puertos abiertos.
   - Recolectas logs del servidor web.
   - Revisas redes sociales por posibles filtraciones.

3. **Procesamiento**:

   - Filtras logs por IPs externas con más de 10 intentos fallidos.
   - Encuentras una IP con comportamiento extraño.

4. **Análisis**:

   - Detectas que la IP está asociada a un servidor conocido en foros de hackers.
   - Encuentras que usaron un exploit CVE reciente.

5. **Difusión**:

   - Escribes un informe con los hallazgos.
   - El equipo de TI bloquea la IP y actualiza el software vulnerable.
   - El rectorado agradece la rápida acción.

---

### 🧠 Resumen gráfico:

```txt
PLANIFICACIÓN → ¿Qué buscar?
       ↓
RECOLECCIÓN → Obtener datos
       ↓
PROCESAMIENTO → Organizar datos
       ↓
ANÁLISIS → Encontrar patrones
       ↓
DIFUSIÓN → Informar y actuar
```

---

### 🎁 Bonus: ¿Dónde practicar esto?

- Usa **Kali Linux** + **Spiderfoot** + **MISP**.
- Crea una red con **VirtualBox**: una máquina atacante, una víctima (Metasploitable), y un SIEM.
- Simula ataques y sigue el ciclo.

---

[🔼](#índice)

---

## **895. Inteligencia para la ciberseguridad**

### 🧠 ¿Qué es la inteligencia para la ciberseguridad?

Es el **proceso de recolectar, analizar y usar información sobre amenazas digitales** (como malware, ataques, actores maliciosos o vulnerabilidades) para **prevenir, detectar y responder a incidentes de seguridad**.

---

### 🎯 Objetivo

La inteligencia en ciberseguridad **no solo reacciona a los ataques**, sino que **se anticipa** a ellos. Sirve para responder a preguntas como:

- ¿Quién está intentando atacarme?
- ¿Qué métodos están usando?
- ¿Qué tan vulnerable soy?
- ¿Qué debería hacer antes de que ocurra un ataque?

---

### 🔍 Tipos de inteligencia en ciberseguridad

#### 1. **Inteligencia estratégica**

- **Enfocada a la alta dirección.**
- Contiene análisis de largo plazo: tendencias, amenazas geopolíticas, campañas APT (Advanced Persistent Threats).

📌 _Ejemplo fácil:_ Un informe sobre cómo grupos rusos están atacando universidades en América Latina.

---

#### 2. **Inteligencia táctica**

- **Para equipos técnicos.**
- Muestra **tácticas, técnicas y procedimientos (TTPs)** usados por atacantes.

📌 _Ejemplo fácil:_ Un análisis de cómo un malware usa PowerShell para persistencia.

---

#### 3. **Inteligencia operativa**

- **Información en tiempo real o reciente.**
- Relacionada con campañas específicas o ataques actuales.

📌 _Ejemplo fácil:_ Detectar que una botnet está activa hoy y atacando redes en Perú.

---

#### 4. **Inteligencia técnica**

- Datos detallados como IPs maliciosas, hashes de archivos, dominios sospechosos, etc.

📌 _Ejemplo fácil:_ Un IOC (indicador de compromiso) que muestra la IP `45.10.1.44` usada por un C2 (servidor de comando y control).

---

### 🛠️ ¿Cómo se “instala” o aplica la inteligencia para la ciberseguridad?

No es una instalación como un programa, pero puedes **montar un entorno con herramientas reales** para usarla. Aquí te muestro algunas:

| Nivel          | Herramientas recomendadas                        |
| -------------- | ------------------------------------------------ |
| Recolección    | 🐍 Spiderfoot, Maltego, Shodan, TheHarvester     |
| Análisis       | 📊 MISP, TheHive, Kibana, ElasticSearch          |
| Visualización  | 📉 Grafana, dashboards de SIEM como Wazuh        |
| Automatización | ⚙️ MISP + Cortex, YARA, Sigma, scripts en Python |

---

### 🧪 ¿Dónde se puede practicar?

Puedes crear tu laboratorio usando:

- 🐧 **Kali Linux** (como entorno de análisis)
- 🐳 **Docker** para correr herramientas como Spiderfoot o MISP
- 💻 **VirtualBox o VMware** para montar redes simuladas (con Metasploitable o DVWA)
- 🌐 Conexión a fuentes de OSINT y threat intelligence (como abuse.ch, VirusTotal, AlienVault OTX)

---

### ✅ Ejemplo completo paso a paso

#### 🧪 Caso realista: Sospechas de un ataque dirigido a una pequeña empresa

---

##### 🔹 1. Recolección

Tu firewall detectó tráfico inusual desde la IP `185.123.99.7`.

💡 Usas:

- `whois 185.123.99.7`: descubres que pertenece a un hosting ruso.
- `urlscan.io` y `Shodan`: muestran que la IP aloja varios paneles de malware.
- Spiderfoot: indica que está en listas negras.

---

##### 🔹 2. Análisis

- Correlacionas la IP con una **firma YARA** de un malware reciente llamado “AgentTesla”.
- Buscas en MISP (Threat Intelligence Platform): ves reportes de campañas recientes de phishing con ese malware en América Latina.

---

##### 🔹 3. Acción

- Bloqueas la IP en el firewall.
- Escaneas tus equipos internos con un antivirus y una regla YARA.
- Informas al equipo de TI y generas un reporte de amenaza para la dirección.

---

##### 🔹 4. Prevención

- Implementas detección de correo con ficheros `.exe` sospechosos.
- Actualizas el software del servidor web.
- Agregas reglas Sigma para que tu SIEM alerte si aparece la IP o hashes similares.

---

### 🔐 Resultado

Has usado inteligencia para:

- Identificar una amenaza real antes de que se convierta en un ataque grave.
- Compartir datos con tu equipo.
- Fortalecer tus defensas para futuras amenazas.

---

### 🎁 Recurso útil para practicar

- [https://www.circl.lu/services/misp/](https://www.circl.lu/services/misp/) → para usar MISP.
- [https://osintframework.com/](https://osintframework.com/) → recolección de info pública.
- [https://threatfox.abuse.ch](https://threatfox.abuse.ch) → indicadores de compromiso actualizados.

---

### 🧠 Resumen gráfico:

```txt
📌 INTELIGENCIA = Saber antes de que pase
    ↓
Recolección → Análisis → Acciones → Prevención
    ↓
Protección proactiva
```

---

[🔼](#índice)

---

## **896. Mapeo de aplicaciones web y análisis de archivos de interés**

### 🔎 ¿Qué es el mapeo de aplicaciones web?

Es el **proceso de descubrir cómo está construida una aplicación web**: qué tecnologías usa, qué rutas existen, qué funcionalidades tiene, qué entradas permite, y si existen archivos o rutas que el atacante puede aprovechar.

---

#### 📍 ¿Por qué es importante?

Un atacante no puede explotar lo que no conoce. El mapeo es la **primera etapa del reconocimiento** en un pentest (prueba de penetración). Sirve para:

- Conocer rutas ocultas.
- Detectar formularios de entrada.
- Ver tecnologías usadas (PHP, JavaScript, CMS como WordPress).
- Buscar archivos de configuración o respaldo mal protegidos (como `.env`, `backup.zip`, `config.old`).
- Identificar puntos de posible inyección o abuso.

---

### 🛠️ ¿Qué herramientas se usan?

| Herramienta          | Uso principal                              |
| -------------------- | ------------------------------------------ |
| 🔍 **WhatWeb**       | Detecta tecnologías usadas en el sitio     |
| 🕸️ **Gobuster/Dirb** | Descubre directorios y archivos ocultos    |
| 🐙 **Burp Suite**    | Intercepta tráfico y mapea rutas dinámicas |
| 🕷️ **OWASP ZAP**     | Mapea rutas y analiza vulnerabilidades     |
| 📄 **Wget/Curl**     | Descarga archivos y analiza cabeceras      |

---

### 🧰 Instalación de herramientas

#### 🔹 En Kali Linux ya vienen preinstaladas:

- Burp Suite
- WhatWeb
- Dirb
- Wget, Curl

Pero si no tienes Kali, puedes instalar en Ubuntu (o WSL):

```bash
sudo apt update
sudo apt install gobuster whatweb dirb wget curl
```

---

### 📂 Archivos de interés comunes en aplicaciones web

| Archivo          | Riesgo principal                         |
| ---------------- | ---------------------------------------- |
| `.git/config`    | Expone repositorio, historial de cambios |
| `.env`           | Variables de entorno → contraseñas       |
| `backup.zip`     | Respaldos con código fuente completo     |
| `config.php.bak` | Configuración con credenciales           |
| `admin/`         | Panel de administración                  |
| `phpinfo.php`    | Expone configuración interna de PHP      |

---

### 🧪 Ejemplo completo: práctica real

#### 🔸 Objetivo:

Mapear el sitio web `http://testphp.vulnweb.com/` para encontrar rutas ocultas y archivos interesantes.

---

#### 🔹 Paso 1: Identificar tecnologías usadas

```bash
whatweb http://testphp.vulnweb.com/
```

🔍 _Resultado_: Detecta Apache, PHP, posibles CMS.

---

#### 🔹 Paso 2: Descubrir directorios y archivos ocultos

```bash
gobuster dir -u http://testphp.vulnweb.com/ -w /usr/share/wordlists/dirb/common.txt
```

📁 _Resultado posible_: Encuentra `/admin`, `/uploads`, `/phpinfo.php`

---

#### 🔹 Paso 3: Explorar manualmente

Abres `http://testphp.vulnweb.com/phpinfo.php` y ves que muestra información de PHP.

👉 Un atacante podría usar esto para saber la versión exacta de PHP e investigar vulnerabilidades asociadas.

---

#### 🔹 Paso 4: Interceptar tráfico dinámico con Burp Suite

1. Abres Burp Suite.
2. Configuras el navegador para usar el proxy (por ejemplo, `127.0.0.1:8080`).
3. Navegas por el sitio mientras Burp registra el tráfico.
4. Vas a la pestaña **"Target" → "Site map"** y ves todas las rutas descubiertas dinámicamente.

---

#### 🔹 Paso 5: Analizar archivos de interés

Usas `wget` para descargar posibles archivos de configuración.

```bash
wget http://testphp.vulnweb.com/.env
```

👀 Si el servidor no lo protege correctamente, puedes ver variables como:

```
DB_PASSWORD=supersecret
MAIL_HOST=smtp.mailtrap.io
```

---

#### 🔹 Paso 6: Reporte

Como pentester, reportarías:

- Tecnologías usadas: Apache, PHP 5.4.x
- Archivos peligrosos: `/phpinfo.php`, `/admin`
- Rutas accesibles no autenticadas.
- Recomendaciones: eliminar archivos de prueba y proteger rutas sensibles.

---

### ✅ Resumen

```txt
🎯 Mapeo web = Reconocer la estructura y puntos débiles del sitio
    ↓
1. Detectar tecnologías (WhatWeb)
2. Descubrir rutas/archivos (Gobuster/Dirb)
3. Ver tráfico dinámico (Burp Suite)
4. Analizar archivos sensibles (.env, .git)
    ↓
🔐 ¡Esto permite al pentester saber por dónde empezar a atacar!
```

---

### 🎁 Recursos para practicar

- 🔗 [http://testphp.vulnweb.com/](http://testphp.vulnweb.com/) – Sitio vulnerable de práctica
- 🔗 [https://portswigger.net/web-security](https://portswigger.net/web-security) – Laboratorio gratuito de Burp Suite

---

[🔼](#índice)

---

## **897. Base de datos WHO IS**

### 🧠 ¿Qué es la base de datos WHOIS?

**WHOIS** es un protocolo y una base de datos que permite consultar información **registrada públicamente** sobre **nombres de dominio (como google.com) o direcciones IP**.

Cuando alguien registra un dominio, como `midominio.com`, la información sobre:

- El **dueño del dominio**
- Su **correo electrónico**
- El **registrador** (GoDaddy, Namecheap, etc.)
- Las **fechas de registro y expiración**
- Los **servidores DNS** asociados

queda guardada en una **base de datos WHOIS** y está disponible públicamente (con algunas excepciones por privacidad).

---

### 🧑‍💻 ¿Para qué sirve en ciberseguridad y hacking ético?

- 🔎 **Reconocimiento en pentesting (OSINT)**: Saber quién está detrás de un dominio.
- 🕵️‍♂️ **Rastreo de amenazas**: Analizar dominios maliciosos.
- ⛔ **Detección de phishing**: Revisar si un dominio es nuevo o sospechoso.
- 📅 **Fechas de expiración**: Algunos atacantes compran dominios que expiran para suplantación (domain squatting).

---

### 🛠️ Herramientas WHOIS más comunes

| Herramienta             | Descripción                           |
| ----------------------- | ------------------------------------- |
| `whois` (CLI)           | Consulta rápida desde terminal        |
| `whois.domaintools.com` | Consulta web avanzada con historial   |
| `https://who.is`        | Interfaz simple y visual              |
| `python-whois`          | Librería para programar scripts OSINT |

---

### 🧰 Cómo instalar WHOIS

#### En Kali Linux / Ubuntu / Debian:

Ya viene instalado en Kali, pero si no lo tienes:

```bash
sudo apt update
sudo apt install whois
```

#### En Windows (via PowerShell con WSL):

Puedes usar WSL e instalarlo igual que en Ubuntu. O también usar herramientas web como [https://who.is](https://who.is)

---

### 🧪 Ejemplo completo práctico

#### 🎯 Objetivo:

Descubrir información sobre el dominio `example.com` usando WHOIS.

##### 🔹 Paso 1: Comando básico

```bash
whois example.com
```

🔍 Resultado (parte del resultado real):

```
Domain Name: EXAMPLE.COM
Registry Domain ID: 2336799_DOMAIN_COM-VRSN
Registrar WHOIS Server: whois.iana.org
Registrar URL: http://res-dom.iana.org
Updated Date: 2023-08-14T07:01:20Z
Creation Date: 1995-08-14T04:00:00Z
Registrar Registration Expiration Date: 2024-08-13T04:00:00Z
Name Server: A.IANA-SERVERS.NET
Name Server: B.IANA-SERVERS.NET
```

---

##### 🔹 Paso 2: Analizar los datos

- `Creation Date`: Cuándo se registró (muy viejo = confiable).
- `Registrar`: Empresa que lo gestiona.
- `Name Server`: Infraestructura usada.
- ¿Hay datos ocultos por privacidad? Algunos dominios ocultan el correo o nombre del registrante.

---

##### 🔹 Paso 3: Usar WHOIS para detectar algo sospechoso

Supón que llega un correo con un link a:

`http://paypal-seguridad-verificacion.com`

Lo analizas:

```bash
whois paypal-seguridad-verificacion.com
```

Y te aparece:

```
Creation Date: 2024-07-01T10:00:00Z
Registrar: NAMECHEAP INC.
Name Server: ns1.fakehost.com
```

👀 El dominio fue creado hace pocos días. Eso **es típico de páginas de phishing**.

---

### 🛡️ ¿Qué hacer con esta información?

- Añadirlo a un **reporte OSINT**.
- Ver si está relacionado con otros dominios por IP o registrador.
- Reportarlo a Google Safe Browsing, antivirus o CERT local.

---

##3 ✅ Resumen final

```txt
📂 WHOIS = Registro público de dominios e IPs
🔍 Se usa para reconocimiento, OSINT y caza de amenazas
🛠️ Herramientas: whois (CLI), páginas web o scripts en Python
🧪 Ejemplo: saber cuándo y quién registró example.com o detectar phishing
```

---

### 🎁 Recursos útiles

- 🌐 [https://who.is](https://who.is) – interfaz gráfica
- 🐍 [https://pypi.org/project/python-whois/](https://pypi.org/project/python-whois/) – librería en Python
- 📖 [https://osintframework.com](https://osintframework.com) – herramientas de investigación

---

[🔼](#índice)

---

## **898. Way Back Machine**

### 🧠 ¿Qué es la Wayback Machine?

La **Wayback Machine** es una herramienta gratuita ofrecida por [Internet Archive](https://archive.org/web/), que **guarda copias históricas de sitios web**. Funciona como una "máquina del tiempo": puedes ver cómo lucía una web en el pasado.

---

### 🎯 ¿Para qué se usa en ciberseguridad?

En el **hacking ético y el pentesting**, se usa principalmente en la **fase de reconocimiento (OSINT)** para:

- 📜 Ver versiones antiguas de un sitio web.
- 🔍 Encontrar páginas eliminadas o desindexadas (por ejemplo, `/admin`, `/test`, `/dev`, etc.).
- 🕵️ Analizar tecnologías antiguas usadas por el sitio.
- 🛑 Detectar vulnerabilidades expuestas en el pasado.

---

### 🛠️ ¿Cómo se usa? ¿Requiere instalación?

No necesitas instalar nada para usarla manualmente. Solo visita:

🔗 [https://web.archive.org](https://web.archive.org)

Pero si deseas hacer consultas automáticas (por ejemplo, como parte de un script de pentesting), puedes usar:

- `waybackurls` (herramienta en terminal)
- `urlscan.io` o `gau` (GetAllURLs)
- Scripts en Python que consultan la API

---

### 🔧 Instalación (opcional) – herramienta `waybackurls`

#### 1. **Requisitos**: Tener Go instalado

Si no lo tienes:

```bash
sudo apt install golang-go
```

#### 2. **Instalar waybackurls**

```bash
go install github.com/tomnomnom/waybackurls@latest
```

Esto instala la herramienta en `~/go/bin/waybackurls`

Agrega esa carpeta al PATH si no la tienes:

```bash
export PATH=$PATH:$(go env GOPATH)/bin
```

---

### 🧪 Ejemplo completo (manual y automatizado)

#### 🎯 Objetivo:

Ver si un sitio web tenía archivos sensibles que ya no existen hoy.

---

#### 🔹 Método 1: Manual

1. Ir a [https://web.archive.org](https://web.archive.org)
2. Buscar por ejemplo: `http://example.com`
3. Elegir un año del historial (por ejemplo, 2010)
4. Explorar las páginas archivadas

👀 Puedes encontrar rutas como:

```
http://example.com/backup.zip
http://example.com/admin/login.php
http://example.com/test/index.html
```

---

#### 🔹 Método 2: Automatizado con `waybackurls`

Supón que quieres extraer todas las URLs antiguas de `midominio.com`:

```bash
echo "midominio.com" | waybackurls
```

🔍 Resultado:

```
http://midominio.com/index.html
http://midominio.com/test.php
http://midominio.com/.git/config
http://midominio.com/admin/login.php
```

🎯 Ahora puedes tomar esas URLs y verificar si algunas todavía están activas con herramientas como:

```bash
cat urls.txt | httpx
```

O puedes analizarlas con Burp Suite, curl, etc.

---

### 🛡️ Aplicación real en OSINT / Pentesting

Imagine esto:

1. Estás auditando `victima.com`

2. En la Wayback Machine ves que en 2017 tenía:

   - `/admin/backup.sql`
   - `/test/login_bkp.php`

3. Visitas esas URLs hoy, y…

   - ¡`backup.sql` sigue online! Puedes descargarlo y ver datos internos.

Este tipo de hallazgos pueden dar **acceso a contraseñas, usuarios, configuraciones sensibles**, etc.

---

### ✅ Resumen general

```txt
📂 Wayback Machine = Archivo público de versiones antiguas de sitios web
🔎 Se usa en OSINT y pentesting para buscar rutas ocultas o archivos antiguos
🛠️ Uso manual en web o automático con herramientas como `waybackurls`
🧪 Ejemplo: buscar URLs antiguas de un dominio y ver si siguen expuestas
```

---

### 🎁 Recursos útiles

- 🌐 [https://web.archive.org](https://web.archive.org)
- 📦 `waybackurls`: [https://github.com/tomnomnom/waybackurls](https://github.com/tomnomnom/waybackurls)
- 🛠️ Alternativa: `gau` – [https://github.com/lc/gau](https://github.com/lc/gau)
- 📘 Cheat Sheet de OSINT: [https://osintframework.com](https://osintframework.com)

---

[🔼](#índice)

---

## **899. Reverse IP lookup**

### 🧠 ¿Qué es el Reverse IP Lookup?

**Reverse IP Lookup** (búsqueda inversa de IP) es el proceso de encontrar todos los **nombres de dominio** (sitios web) que están **alojados en una misma dirección IP**.

> 🌐 Por ejemplo, si la IP `198.51.100.34` pertenece a un servidor compartido, podrías encontrar que en esa IP están alojados:
>
> - `tiendaejemplo.com`
> - `portalnoticias.com`
> - `foro-debate.net`

---

### 🎯 ¿Para qué se usa en ciberseguridad?

El **reverse IP lookup** se utiliza en la fase de **reconocimiento** (OSINT) del pentesting para:

- 🕵️‍♂️ Descubrir dominios "hermanos" de un objetivo.
- 🧩 Encontrar subdominios olvidados o desprotegidos.
- 🛠️ Ver si un servidor compartido tiene sitios con vulnerabilidades.
- 🎯 Enfocar un ataque en dominios menos protegidos para llegar al principal.

---

### 🔧 ¿Cómo se hace un Reverse IP Lookup?

#### 1. Métodos manuales (sin instalación)

Hay sitios web gratuitos donde puedes hacer esto:

- [https://viewdns.info/reverseip/](https://viewdns.info/reverseip/)
- [https://securitytrails.com](https://securitytrails.com)
- [https://dnsdumpster.com](https://dnsdumpster.com)

👉 Solo ingresas la IP y te muestra los dominios alojados allí.

---

#### 2. Métodos con herramientas (requieren instalación)

Puedes usar herramientas en Linux como:

- `nmap`
- `dig` y `host` (para obtener la IP)
- `recon-ng`
- `theHarvester`
- Scripts en Python (te mostraré uno)

---

### 🖥️ Instalación de herramientas útiles

#### 🔹 Requisitos básicos en Linux (Kali o Ubuntu):

```bash
sudo apt update
sudo apt install nmap dnsutils whois python3-pip -y
```

---

#### 🔹 Instalar una herramienta OSINT: `recon-ng`

```bash
sudo apt install recon-ng
```

---

#### 🔹 Instalar `SecurityTrails` vía API (opcional)

Puedes usar su API con Python si te registras gratis en: [https://securitytrails.com](https://securitytrails.com)

---

### ✅ Ejemplo completo paso a paso

---

#### 🧪 Supongamos que tienes el dominio: `midominio.com`

##### 1. Obtener la IP del dominio

```bash
host midominio.com
```

🔎 Resultado:

```
midominio.com has address 198.51.100.34
```

---

##### 2. Usar viewdns.info para obtener dominios en esa IP

👉 Ir a:
[https://viewdns.info/reverseip/?host=198.51.100.34](https://viewdns.info/reverseip/?host=198.51.100.34)

🔍 Resultado posible:

```
tiendaejemplo.com
portalnoticias.com
foro-debate.net
```

---

##### 3. Verificar si alguno de esos dominios tiene vulnerabilidades

Puedes analizarlos con herramientas como:

```bash
nmap -sV -Pn tiendaejemplo.com
```

o

```bash
whatweb portalnoticias.com
```

---

#### 🔧 Ejemplo con Python (usando API pública gratuita)

```python
import requests

ip = "198.51.100.34"
url = f"https://api.hackertarget.com/reverseiplookup/?q={ip}"

response = requests.get(url)

if response.status_code == 200:
    print("Dominios encontrados:")
    print(response.text)
else:
    print("Error al hacer la consulta")
```

👆 Este script usa la API pública de [hackertarget.com](https://hackertarget.com) (sin necesidad de cuenta).

---

### 🧩 Aplicación real en pentesting

🔐 Supón que estás auditando `empresa.com` y descubres que:

- La IP del sitio también aloja `intranet.empresa.com` (descubierto con reverse IP).
- Esa intranet tiene login sin HTTPS y usuarios antiguos.
- Puedes enfocar tu análisis allí para intentar ingresar.

---

### 🧾 Resumen general

| Concepto               | Detalle                                                         |
| ---------------------- | --------------------------------------------------------------- |
| 🔍 ¿Qué es?            | Buscar qué dominios comparten una misma IP                      |
| 🧠 ¿Para qué sirve?    | Reconocimiento, descubrimiento de objetivos, OSINT              |
| 💻 ¿Cómo se usa?       | Sitios web como viewdns.info o con herramientas (nmap, scripts) |
| 🧪 Ejemplo completo    | Obtener IP → buscar dominios → analizar con Nmap, WhatWeb, etc. |
| 🧰 Herramientas útiles | host, dig, recon-ng, Python, SecurityTrails API, viewdns.info   |

---

[🔼](#índice)

---

## **900. Google Hacking**

### 🧠 ¿Qué es Google Hacking?

**Google Hacking** (también llamado “Google Dorking”) es una técnica que consiste en usar **operadores avanzados de búsqueda en Google** para encontrar información sensible o vulnerable publicada en internet, ya sea **por error, descuido o mala configuración**.

🔍 En lugar de buscar “restaurantes en Lima”, podrías buscar cosas como:

```
filetype:pdf "confidencial" site:empresa.com
```

Eso te daría **archivos PDF etiquetados como “confidencial” en el sitio web de empresa.com**.

---

### 🎯 ¿Para qué se usa en ciberseguridad?

En el contexto del **hacking ético** y el **OSINT (inteligencia de fuentes abiertas)**, se utiliza para:

- Encontrar archivos sensibles expuestos (PDF, DOC, XLS, backups).
- Encontrar cámaras de seguridad accesibles públicamente.
- Identificar directorios de administración o login olvidados.
- Ver versiones de software expuestas.
- Detectar vulnerabilidades conocidas en sitios web.

---

### 🔐 ¿Es ilegal?

👉 **Usar Google con fines informativos y educativos NO es ilegal.**
Pero **usar esta información para dañar, ingresar sin permiso o explotar vulnerabilidades SÍ es ilegal.** Por eso se llama **hacking ético** cuando se hace con autorización.

---

### 🔧 ¿Cómo se instala?

No se instala **nada**. Solo necesitas:

- Un navegador web.
- Acceso a Google (¡eso es todo!).
- (Opcional) Un navegador seguro como **Firefox** o **Tor** para navegación anónima.

👉 Pero puedes organizar tus búsquedas usando herramientas como:

- [Google Hacking Database (GHDB)](https://www.exploit-db.com/google-hacking-database) — Repositorio de dorks clasificados.
- Extensiones como **Hacking tools** para Chrome/Firefox (opcional).

---

### 🧪 Ejemplos de Google Dorks útiles y fáciles

#### 1. Buscar archivos PDF expuestos:

```bash
filetype:pdf site:empresa.com
```

#### 2. Buscar archivos de backup:

```bash
filetype:sql OR filetype:bak site:empresa.com
```

#### 3. Buscar cámaras web abiertas:

```bash
inurl:/view.shtml
```

#### 4. Buscar páginas de login:

```bash
inurl:login site:empresa.com
```

#### 5. Buscar configuraciones expuestas:

```bash
filetype:env OR filetype:xml site:empresa.com
```

---

### 🧪 Ejemplo completo paso a paso

#### 🔎 Objetivo ficticio: `midominio.com`

##### 1. Buscar archivos de Word con información interna:

```bash
filetype:docx site:midominio.com
```

> Esto mostrará documentos Word públicos del dominio.

---

##### 2. Buscar cámaras públicas:

```bash
inurl:"/view.shtml"
```

> Abre una lista de cámaras de seguridad que transmiten en vivo sin contraseña.

---

##### 3. Buscar bases de datos expuestas:

```bash
intitle:"index of" "backup" site:midominio.com
```

> Verás directorios abiertos llamados “backup” si existen.

---

##### 4. Buscar formularios de login olvidados:

```bash
inurl:admin OR inurl:login site:midominio.com
```

> Podrías encontrar páginas como `/admin/login.php`.

---

#### ⚠️ Precauciones

- No intentes ingresar ni explotar vulnerabilidades sin autorización.
- Usa estas técnicas para **aprender**, practicar en laboratorios o **auditar tu propia empresa o sitio**.
- Documenta todo si haces un **pentest autorizado**.

---

### 🧰 Tip rápido para organizar tus dorks

Puedes usar un bloc de notas con tus dorks favoritos como:

```bash
# Buscar PDF
filetype:pdf site:ejemplo.com

# Buscar bases de datos
filetype:sql OR filetype:bak site:ejemplo.com

# Buscar paneles de login
inurl:admin OR inurl:login site:ejemplo.com
```

---

### 📚 Recurso útil

- [https://www.exploit-db.com/google-hacking-database](https://www.exploit-db.com/google-hacking-database)
  Aquí puedes encontrar miles de ejemplos reales de dorks listos para usar.

---

### 🧾 Resumen final

| Concepto               | Detalle                                             |
| ---------------------- | --------------------------------------------------- |
| ¿Qué es?               | Técnica para buscar información sensible con Google |
| ¿Para qué sirve?       | OSINT, reconocimiento, encontrar archivos o login   |
| ¿Necesita instalación? | No. Solo navegador y conexión a internet            |
| ¿Legal?                | Sí, mientras no accedas sin permiso ni causes daño  |
| Recurso recomendado    | Google Hacking Database (GHDB)                      |

---

[🔼](#índice)

---

## **901. Análisis de fuga de información**

### 🧠 ¿Qué es el análisis de fuga de información?

El **análisis de fuga de información** (también conocido como _Data Leak Analysis_ o _Data Leak Detection_) es el proceso de **detectar y analizar información sensible que ha sido expuesta sin autorización**.

Esto puede incluir:

- Contraseñas en repositorios públicos (como GitHub).
- Archivos confidenciales mal configurados en la nube.
- Datos personales (DNI, correos, tarjetas).
- Información técnica (configuraciones, tokens, claves API).

---

### 🔍 ¿Por qué ocurre una fuga de información?

Algunas causas comunes:

| Causa                          | Ejemplo                                            |
| ------------------------------ | -------------------------------------------------- |
| Repositorios mal configurados  | Subir claves o `.env` a GitHub.                    |
| Buckets públicos en la nube    | AWS S3 sin autenticación.                          |
| Archivos de respaldo olvidados | `backup.sql` disponible en la web.                 |
| Configuraciones expuestas      | Archivos `.env`, `config.yaml` en producción.      |
| Ingeniería social              | Un empleado publica sin saber que es confidencial. |

---

### 🧰 ¿Qué herramientas se usan?

Algunas herramientas útiles para buscar fugas de información:

- **Google Hacking** (ya lo viste): `filetype:env site:ejemplo.com`
- **GitLeaks**: Busca secretos en repos de Git.
- **TruffleHog**: Detecta claves en commits.
- **SpiderFoot**: Escaneo automatizado de OSINT.
- **Shodan**: Busca dispositivos y servicios mal configurados.
- **HaveIBeenPwned**: Para ver si tus correos o contraseñas han sido filtrados.

---

### 🛠️ ¿Cómo instalar el entorno para análisis?

Puedes usar Kali Linux o cualquier sistema Linux para hacerlo.

#### ✅ Requisitos:

- Git instalado
- Python (3.x)
- Docker (opcional)

---

#### 🧪 Ejemplo de instalación: TruffleHog

```bash
# Paso 1: Clonar el repositorio
git clone https://github.com/trufflesecurity/trufflehog.git

# Paso 2: Entrar al proyecto
cd trufflehog

# Paso 3: Ejecutar escaneo en un repositorio
python3 trufflehog/trufflehog.py https://github.com/ejemplo/repositorio
```

Este comando buscará **tokens, contraseñas y claves** en el historial del repo.

---

### 🧪 Ejemplo completo: Análisis de fuga en repositorio público de GitHub

#### 🎯 Escenario:

Queremos ver si hay información sensible en un repositorio de GitHub:
`https://github.com/empresa-seguridad/backend-api`

#### 🔍 Paso 1: Escaneo con TruffleHog

```bash
python3 trufflehog/trufflehog.py https://github.com/empresa-seguridad/backend-api
```

#### 🔎 Resultado:

```bash
Reason: High Entropy String
Path: .env
Strings found:
  SECRET_KEY=sk_test_51Hk...oEYf
```

> ¡Encontramos una clave de API expuesta en el archivo `.env`!

---

#### 🛡️ Paso 2: Validar el hallazgo

Verificamos si esa clave sigue activa o si ya fue revocada.

Si está activa:

- Contactamos al equipo responsable.
- Recomendamos revocarla y rotarla.
- Sugerimos usar variables de entorno en producción (no subir `.env` a repos).

---

#### 🔒 Paso 3: Recomendaciones

- Agregar `.env` a `.gitignore`
- Usar herramientas de escaneo como GitLeaks antes de hacer `push`
- Usar alertas automáticas de GitHub o GitGuardian

---

### 📋 Resumen

| Elemento                  | Detalle                                                           |
| ------------------------- | ----------------------------------------------------------------- |
| ¿Qué es?                  | Análisis para detectar datos sensibles expuestos                  |
| ¿Por qué ocurre?          | Errores humanos, mal configuración, desconocimiento               |
| Herramientas recomendadas | TruffleHog, GitLeaks, SpiderFoot, Shodan, Google Dorking          |
| Instalación ejemplo       | `git clone` + `python3 trufflehog.py`                             |
| Resultado posible         | Claves, tokens, archivos `.env`, credenciales, respaldos, correos |

---

[🔼](#índice)

---

## **902. Enumeración de subdominios**

### 🔍 ¿Qué es la Enumeración de Subdominios?

La **enumeración de subdominios** es una técnica que consiste en **descubrir subdominios de un dominio principal**. Esto forma parte del **reconocimiento o fase de información** en el hacking ético o pentesting.

Por ejemplo, si el dominio principal es:

```
empresa.com
```

Los subdominios podrían ser:

- `mail.empresa.com`
- `admin.empresa.com`
- `dev.empresa.com`
- `intranet.empresa.com`

Cada subdominio puede **apuntar a un servidor diferente**, con diferentes servicios, tecnologías o incluso **vulnerabilidades**.

---

### 🧠 ¿Por qué es importante?

- Algunos subdominios pueden tener configuraciones débiles o no actualizadas.
- Se pueden encontrar entornos de desarrollo o administración.
- Son puertas de entrada para ataques como XSS, inyecciones o acceso no autorizado.

---

### 🔧 Herramientas para Enumerar Subdominios

| Herramienta     | Descripción breve                                      |
| --------------- | ------------------------------------------------------ |
| **Amass**       | Recolector de subdominios por OSINT + DNS              |
| **Sublist3r**   | Escanea motores de búsqueda (Google, Bing, Yahoo, etc) |
| **Assetfinder** | Rápido y sencillo, ideal para bug bounty               |
| **Findomain**   | Muy veloz, ideal para automatización                   |
| **crt.sh**      | Búsqueda manual de certificados SSL                    |

---

### ⚙️ ¿Cómo instalar las herramientas?

#### 🐍 Opción 1: Instalar Sublist3r

Sublist3r está hecho en Python, ideal para empezar:

```bash
# Paso 1: Clonar repositorio
git clone https://github.com/aboul3la/Sublist3r.git

# Paso 2: Entrar al directorio
cd Sublist3r

# Paso 3: Instalar dependencias
pip install -r requirements.txt

# Paso 4: Ejecutar
python3 sublist3r.py -d empresa.com
```

---

#### 🏎️ Opción 2: Instalar Amass (más potente)

```bash
sudo apt install amass -y
```

Verifica que se instaló bien:

```bash
amass -h
```

---

### 🧪 Ejemplo práctico completo

Vamos a hacer una enumeración para el dominio `uber.com` usando **Amass**.

#### 🔎 Paso 1: Ejecutar Amass

```bash
amass enum -d uber.com
```

Esto buscará subdominios por motores, bases de datos de certificados, DNS, etc.

---

#### 📋 Resultado esperado

```bash
login.uber.com
api.uber.com
m.uber.com
driver.uber.com
riders.uber.com
admin.uber.com
```

> 💡 Cada uno de estos puede llevar a una aplicación diferente con posibles puntos de entrada para un pentest.

---

#### 🧰 Paso 2: Opcional – guardar en un archivo

```bash
amass enum -d uber.com -o subdominios.txt
```

Esto guarda todos los subdominios encontrados en el archivo `subdominios.txt`.

---

### 🔐 ¿Y luego qué?

Con los subdominios identificados puedes:

- Hacer escaneo de puertos (Nmap).
- Ver tecnologías usadas (con WhatWeb, Wappalyzer).
- Analizar archivos visibles (`robots.txt`, `sitemap.xml`, etc).
- Buscar subdominios inactivos (para ataques como **takeover**).

---

### 🧾 Resumen general

| Elemento                  | Detalle                                            |
| ------------------------- | -------------------------------------------------- |
| ¿Qué es?                  | Buscar subdominios de un dominio                   |
| ¿Para qué sirve?          | Reconocimiento, hallar posibles puertas de entrada |
| Herramientas recomendadas | Sublist3r, Amass, Assetfinder, Findomain           |
| Instalación ejemplo       | `git clone`, `pip install`, `apt install`          |
| Ejemplo práctico          | `amass enum -d uber.com`                           |

---

[🔼](#índice)

---

## **903. Análisis de metadatos con Foca**

### 🧠 ¿Qué es el análisis de metadatos?

Los **metadatos** son **datos sobre otros datos**. En documentos como PDF, Word, imágenes o presentaciones, los metadatos pueden contener:

- Nombre del autor
- Fecha de creación y modificación
- Versión del software usado
- Nombre de usuario del equipo
- Ruta del archivo
- Información sobre la impresora o red

---

### 🎯 ¿Por qué es importante en ciberseguridad?

Un atacante ético puede usar los metadatos para:

- Descubrir nombres reales de empleados
- Identificar estructuras internas (nombres de carpetas, servidores)
- Detectar versiones de software vulnerable
- Observar patrones de uso

---

### 🛠️ ¿Qué es FOCA?

**FOCA** (Fingerprinting Organizations with Collected Archives) es una herramienta desarrollada por **ElevenPaths (Telefónica)** que permite:

- Descargar documentos públicos (PDF, DOCX, XLS, etc.)
- Extraer sus metadatos automáticamente
- Analizar posibles vulnerabilidades

Es una herramienta potente para hacer **reconocimiento pasivo** en el pentesting.

---

### 💻 ¿Cómo se instala FOCA?

> ⚠️ FOCA solo está disponible para **Windows** y requiere **.NET Framework**.

#### Paso 1: Descargar FOCA

1. Ir al sitio oficial:
   👉 [https://www.elevenpaths.com/labstools/foca/index.html](https://www.elevenpaths.com/labstools/foca/index.html)

2. Descargar el instalador de FOCA.

3. Instalar como cualquier programa típico de Windows (siguiente → siguiente → instalar).

---

#### Paso 2: Requisitos

- Windows 10 o superior.
- Microsoft .NET Framework 4.5 o superior.
- Conexión a internet para búsquedas públicas.

---

### ✅ Ejemplo completo paso a paso

Vamos a analizar los metadatos de documentos públicos del sitio `example.com`.

#### Paso 1: Abrir FOCA

- Ejecuta FOCA desde el menú de inicio.
- Crea un nuevo proyecto:
  `Archivo → Nuevo proyecto → Nombre: "análisis-example"`

#### Paso 2: Agregar dominio objetivo

- Agrega `example.com` como dominio a analizar.
- FOCA buscará archivos públicos asociados a este dominio (como en Google, Bing, DuckDuckGo).

#### Paso 3: Buscar documentos

- FOCA buscará archivos como:

  ```
  filetype:pdf site:example.com
  filetype:docx site:example.com
  filetype:xls site:example.com
  ```

- Descargará automáticamente los archivos encontrados en los resultados de búsqueda.

#### Paso 4: Extraer metadatos

- Haz clic derecho en los archivos descargados → **"Extraer metadatos"**.
- FOCA mostrará una tabla con los metadatos como:

| Archivo     | Autor  | Software usado    | Ruta interna                          |
| ----------- | ------ | ----------------- | ------------------------------------- |
| informe.pdf | JLopez | Microsoft Word 16 | C:\Users\JLopez\Documents\informe.pdf |
| ventas.xls  | admin  | Excel 2013        | D:\Compartido\ventas\2024.xls         |

---

#### Paso 5: Interpretar resultados

- Si ves `JLopez`, `admin`, etc., puedes investigar en redes sociales si trabajan en la empresa.
- Si ves rutas internas, puedes suponer estructura de carpetas, por ejemplo:

  - Red compartida: `\\servidor\documentos\clientes\`

- Si ves software antiguo, podría estar sin parches.

---

### 🔐 Buenas prácticas

- **Nunca publiques documentos sensibles sin limpiarlos**.
- Usa herramientas como `mat2`, `exiftool`, o incluso Word → Exportar → Quitar propiedades personales.
- En pentesting real, **siempre obtén permiso** para hacer análisis de dominio.

---

### 🧾 Resumen general

| Elemento         | Descripción                                      |
| ---------------- | ------------------------------------------------ |
| ¿Qué es FOCA?    | Herramienta OSINT para metadatos en documentos   |
| ¿Qué analiza?    | Autor, software, rutas internas, fechas          |
| Instalación      | Solo en Windows – descargable desde ElevenPaths  |
| Ejemplo          | Buscar `site:empresa.com filetype:pdf` y extraer |
| Resultado típico | Información interna útil para ataques dirigidos  |

---

[🔼](#índice)

---

## **904. Análisis de servidores con Shodan**

### 🧠 ¿Qué es Shodan?

**Shodan** es un **motor de búsqueda** como Google, pero en lugar de buscar sitios web, busca **dispositivos conectados a internet**, como:

- Servidores web
- Ruteadores
- Cámaras IP
- Bases de datos
- Dispositivos IoT
- Firewalls, PLCs, impresoras, etc.

👉 Shodan no escanea la web entera, pero **almacena los datos del banner de puertos abiertos** de muchos dispositivos conectados.

---

### 🔎 ¿Qué puedes encontrar con Shodan?

- Servicios activos (puertos abiertos)
- Versión de software o sistema operativo
- Ubicación geográfica del servidor
- ISP (proveedor de internet)
- Vulnerabilidades conocidas (CVEs)
- Si usa HTTP, HTTPS, FTP, SSH, RDP, etc.

---

### 🎯 ¿Para qué sirve en ciberseguridad?

Shodan es muy útil en:

| Área                   | Uso                                                            |
| ---------------------- | -------------------------------------------------------------- |
| Hacking ético / OSINT  | Ver qué expone una empresa a internet                          |
| Pentesting             | Buscar versiones vulnerables de servicios                      |
| Defensa (Blue Team)    | Detectar servicios inseguros que se deberían cerrar            |
| Auditoría de seguridad | Buscar dispositivos mal configurados o que filtran información |

---

### 🧰 ¿Cómo usar Shodan?

Tienes **3 formas de usar Shodan**:

#### 1. 🌐 Usando el navegador (la forma más simple)

- Ve a: [https://www.shodan.io](https://www.shodan.io)
- Crea una cuenta gratuita
- Escribe en la barra de búsqueda como si fuera Google

Ejemplo:

```
apache port:80 country:"PE"
```

Busca servidores Apache en el puerto 80 en Perú.

---

#### 2. 💻 Usando Shodan desde la terminal (CLI)

##### ✅ Requisitos:

- Tener Python 3 instalado
- Tener pip

##### 🧪 Instalación paso a paso:

1. Abre tu terminal y escribe:

```bash
pip install shodan
```

2. Ve a [https://account.shodan.io](https://account.shodan.io) y copia tu API Key

3. Guarda tu API Key con este comando:

```bash
shodan init TU_API_KEY
```

4. Ya puedes usar comandos como:

```bash
shodan search apache
```

---

#### 3. 📦 Usando la API de Shodan en tus programas

Si haces scripts en Python, puedes usar:

```python
import shodan

api = shodan.Shodan('TU_API_KEY')

results = api.search('nginx country:PE')

for result in results['matches']:
    print(f"IP: {result['ip_str']}")
    print(result['data'])
    print("="*30)
```

---

### ✅ Ejemplo completo: buscar servidores vulnerables en Perú

#### Paso 1: Entrar a Shodan.io y registrarte

- Crea una cuenta gratuita
- Verifica tu correo

#### Paso 2: Escribe una búsqueda

```sh
nginx country:"PE" port:80
```

> Esto muestra servidores con Nginx en Perú usando el puerto 80 (HTTP). Puedes ver la IP, ciudad, banner de servicio y más.

---

#### Paso 3: Analiza los resultados

Verás algo como:

```
IP: 190.XX.XX.12
Puerto: 80
Banner:
Server: nginx/1.18.0
Location: Lima, Peru
ISP: Claro
```

Con esa información puedes:

- Ver si la versión es antigua
- Buscar CVEs asociadas a esa versión
- Hacer escaneo posterior (si tienes permiso)

---

#### Paso 4 (opcional): Buscar dispositivos abiertos con Telnet o FTP

```sh
port:23 country:"PE"
```

O:

```sh
ftp anonymous country:"PE"
```

Esto puede revelar **sistemas inseguros con acceso FTP abierto** al mundo.

---

### 🔐 ¿Es legal usar Shodan?

✅ **Sí**, si solo usas la **información pública** que Shodan te ofrece.

❌ **No es legal** realizar ataques o explotación sin autorización.

Shodan solo recopila lo que **está público** en internet, igual que si hicieras un escaneo tú mismo con Nmap.

---

### 🧾 Resumen general

| Elemento             | Descripción                                    |
| -------------------- | ---------------------------------------------- |
| ¿Qué es Shodan?      | Buscador de dispositivos conectados a internet |
| ¿Qué busca?          | Servidores, IoT, puertos, software, versiones  |
| ¿Cómo usarlo?        | Desde la web, terminal o API Python            |
| ¿Qué se puede hacer? | OSINT, pentesting, auditorías, caza de CVEs    |
| ¿Legal?              | Sí, si no haces acciones intrusivas            |

---

[🔼](#índice)

---

## **905. Enumeración de correos electrónicos**

### 🧠 ¿Qué es la Enumeración de Correos Electrónicos?

Es el proceso de **recolectar direcciones de correo electrónico** asociadas a una persona, empresa, dominio o entidad.
Forma parte del reconocimiento pasivo y se utiliza para:

- Ingeniería social (ej. phishing)
- Caza de cuentas vulnerables
- Ataques de diccionario
- Recolección de información para pentesting
- Análisis de filtraciones o fugas

---

### 🛠️ ¿Cómo se puede hacer la enumeración?

#### ✅ Métodos más usados:

1. **Google Dorking**
2. **Herramientas OSINT automáticas**
3. **Redes sociales y buscadores de personas**
4. **Filtraciones públicas (HaveIBeenPwned, LeakCheck, etc.)**
5. **WHOIS, LinkedIn, Pastebin**
6. **Revisar archivos PDF, DOC o metadatos públicos**

---

### 🔍 Ejemplo de Google Dorks para correos

```
site:example.com intext:"@example.com"
```

Busca páginas del dominio que contengan emails.

```
filetype:pdf "@example.com"
```

Busca PDFs con correos del dominio objetivo.

---

### 🧰 Herramientas útiles

- **theHarvester** (enumeración de correos, subdominios, IPs)
- **Hunter.io** (requiere cuenta, online)
- **EmailHarvester.py** (script de Python)
- **Email2phonenumber** (relaciona emails con números)
- **Maltego CE** (gráfico visual de OSINT)
- **Recon-ng** (framework completo de reconocimiento)

---

### 🐍 Instalación de `theHarvester` (herramienta recomendada)

Es una herramienta de línea de comandos que obtiene emails desde Google, Bing, LinkedIn, etc.

#### Requisitos:

- Python 3
- Linux, macOS o Windows con WSL

#### 🔧 Instalación paso a paso:

```bash
git clone https://github.com/laramies/theHarvester.git
cd theHarvester
pip install -r requirements.txt
```

#### Ejecución básica:

```bash
python3 theHarvester.py -d example.com -b google
```

Esto buscará correos electrónicos, subdominios y hosts relacionados con `example.com` usando Google.

---

### ✅ Ejemplo completo: Enumeración de correos con theHarvester

#### Escenario:

Quieres encontrar correos públicos asociados al dominio **"empresa.com"** para un informe OSINT o test de phishing controlado.

---

#### 🔴 Paso 1: Instalar theHarvester (si no lo tienes)

```bash
git clone https://github.com/laramies/theHarvester.git
cd theHarvester
pip install -r requirements.txt
```

---

#### 🟠 Paso 2: Ejecutar búsqueda

```bash
python3 theHarvester.py -d empresa.com -b bing
```

Puedes cambiar `-b` por otros motores:

- `google`
- `bing`
- `yahoo`
- `duckduckgo`
- `linkedin` (requiere credenciales)
- `crtsh` (certificados SSL)

---

#### 🟡 Paso 3: Analizar los resultados

Ejemplo de salida:

```
[-] Emails found:
juan.perez@empresa.com
rrhh@empresa.com
maria.garcia@empresa.com
```

---

#### 🟢 Paso 4: Complementar con Google Dorks

```bash
site:empresa.com intext:"@empresa.com"
```

También puedes probar:

```bash
"juan.perez@empresa.com" filetype:pdf
```

---

#### 🔵 Paso 5: Verificar correos con herramientas online

Puedes usar:

- [https://haveibeenpwned.com](https://haveibeenpwned.com)
- [https://hunter.io](https://hunter.io)
- [https://emailrep.io](https://emailrep.io)

---

### 🔐 Consideraciones legales

✅ Recolectar correos que están públicamente disponibles **es legal** si no los usas para fines maliciosos.

❌ Usar esta información para **phishing o spam no autorizado es ilegal**.

🛡️ Esto se utiliza en **hacking ético, OSINT, investigaciones forenses y pruebas de seguridad** bajo autorización.

---

### 📚 Resumen general

| Elemento             | Detalle                                                  |
| -------------------- | -------------------------------------------------------- |
| ¿Qué es?             | Proceso de buscar emails relacionados a una organización |
| Herramientas comunes | theHarvester, Google Dorks, Hunter, Maltego              |
| Métodos              | Motores de búsqueda, metadatos, filtraciones             |
| Sistema necesario    | Python, Linux/WSL                                        |
| Casos de uso         | OSINT, phishing ético, análisis de filtraciones          |

---

[🔼](#índice)

---

## **906. Análisis de números telefónicos**

### 🧠 ¿Qué es el análisis de números telefónicos?

Es una técnica de **OSINT** que permite recopilar información sobre un número de teléfono, como:

- Ubicación geográfica
- Operador telefónico
- Si está vinculado a redes sociales (WhatsApp, Facebook, etc.)
- Posible nombre o identidad del dueño
- Actividad en apps o filtraciones de datos

Es útil en **investigaciones digitales, pentesting, ciberinteligencia e incluso recuperación de cuentas.**

---

### 📌 ¿Para qué se usa?

- Verificar si un número está en uso
- Identificar posibles víctimas o amenazas
- Correlacionar identidad digital (email, IP, usuario, teléfono)
- Investigar fraudes o suplantaciones
- Recopilar pruebas de ciberacoso o doxing

---

### 🔍 Herramientas OSINT para analizar teléfonos

| Herramienta            | ¿Qué hace?                                                               |
| ---------------------- | ------------------------------------------------------------------------ |
| **PhoneInfoga**        | Busca metadatos del número (país, carrier, filtraciones, redes sociales) |
| **OSINT-Phone-Number** | Conecta varias fuentes públicas de datos                                 |
| **Truecaller (web)**   | Puede mostrar el nombre de la persona si está registrado                 |
| **Sync.me**            | Similar a Truecaller (en la web)                                         |
| **Google** / Dorking   | Puede revelar resultados públicos, como anuncios, foros, etc.            |

---

### 🛠️ Instalación de PhoneInfoga (la herramienta más popular y potente)

#### 📦 Requisitos:

- Tener Python instalado (recomendado)
- Tener Linux, Windows o WSL
- Tener Git (opcional pero útil)

---

#### 🔧 Instalación paso a paso:

##### 🟢 Opción 1: Usar Docker (recomendado para evitar errores de dependencias)

```bash
docker pull sundowndev/phoneinfoga
```

Para ejecutar:

```bash
docker run -it sundowndev/phoneinfoga scan -n "+51987654321"
```

##### 🟠 Opción 2: Clonar el repositorio y usar Python

```bash
git clone https://github.com/sundowndev/phoneinfoga.git
cd phoneinfoga
python3 -m pip install -r requirements.txt
```

Para lanzar el escaneo:

```bash
python3 phoneinfoga.py -n "+51987654321"
```

> Reemplaza el número con el que quieras analizar.

---

### 🧪 Ejemplo completo: Análisis de número peruano con PhoneInfoga

#### Escenario:

Supón que encuentras el número **+51987654321** en un mensaje sospechoso y quieres saber si está en uso, si aparece en alguna filtración, y qué proveedor lo maneja.

---

#### 🔴 Paso 1: Instalar PhoneInfoga con Docker

```bash
docker pull sundowndev/phoneinfoga
```

---

#### 🟠 Paso 2: Ejecutar el escaneo

```bash
docker run -it sundowndev/phoneinfoga scan -n "+51987654321"
```

---

#### 🟡 Paso 3: Analizar el resultado

Posible salida:

```bash
🕵️‍♂️ Number: +51987654321
📍 Country: Peru (PE)
📱 Carrier: Movistar
📡 Line type: Mobile
🔍 Has been leaked in 2 data breaches!
🔗 Related profiles: whatsapp, facebook (found with pattern match)
```

---

#### 🟢 Paso 4: Complementar con Google Dorks

```bash
"987654321" site:pe
"987654321" intext:"contacto" OR "teléfono"
```

---

#### 🔵 Paso 5: Comprobar si tiene WhatsApp

Guarda el número en tu teléfono y abre WhatsApp. Si aparece una foto, estado o nombre, está en uso.

---

### ⚠️ Consideraciones legales

| Acción                        | Legal con autorización | Ilegal sin consentimiento |
| ----------------------------- | ---------------------- | ------------------------- |
| Analizar datos públicos       | ✅ Sí                  | -                         |
| Usar para suplantar identidad | ❌ No                  | Sí                        |
| Recolectar para OSINT ético   | ✅ Sí                  | -                         |
| Hackear WhatsApp/Facebook     | ❌ No                  | Sí                        |

---

### 📚 Resumen

| Elemento                  | Detalle                                                       |
| ------------------------- | ------------------------------------------------------------- |
| ¿Qué es?                  | Recolección de información pública sobre un número telefónico |
| Herramientas recomendadas | PhoneInfoga, Truecaller, Google, Sync.me                      |
| Requisitos                | Docker o Python                                               |
| Casos de uso              | OSINT, ciberseguridad, investigaciones                        |

---

[🔼](#índice)

---

## **907. Investigación de individuos por su nombre**

### ✅ ¿Qué es?

La **investigación de individuos por nombre** forma parte de las técnicas de **OSINT (Open Source Intelligence)**, y se refiere a **buscar información pública sobre una persona usando solo su nombre completo.**

Esto se puede hacer **sin hackear**, ya que toda la información se obtiene de **fuentes abiertas** como redes sociales, registros públicos, foros, noticias, y herramientas OSINT especializadas.

---

### 🎯 ¿Para qué se utiliza?

- Verificar identidades en procesos de selección o auditorías
- Recolectar información para investigaciones legales o periodísticas
- Ciberinteligencia para análisis de amenazas o fraudes
- Perfiles psicológicos o de comportamiento en redes
- Análisis de reputación

---

### 🔍 ¿Qué tipo de información se puede obtener?

| Tipo de dato                   | Ejemplo práctico                       |
| ------------------------------ | -------------------------------------- |
| Nombre completo                | "Carlos Andrés Rivas Torres"           |
| Alias o nicknames              | “carlosdev123” en foros o GitHub       |
| Redes sociales                 | Facebook, LinkedIn, Twitter, Instagram |
| Profesión o lugar de trabajo   | Ingeniero de sistemas en Google        |
| Ubicación (si es pública)      | Lima, Perú                             |
| Correos y teléfonos filtrados  | En bases de datos o leaks              |
| Participación en foros         | StackOverflow, Reddit, etc.            |
| Archivos con metadatos         | PDFs, DOCs, imágenes                   |
| Registros legales o académicos | Universidades, artículos, licencias    |

---

### 🧰 Herramientas para investigar por nombre

| Herramienta               | ¿Qué hace?                                                 |
| ------------------------- | ---------------------------------------------------------- |
| **Google / Google Dorks** | Busca todo tipo de información indexada                    |
| **Namechk / KnowEm**      | Revisa si el nombre está registrado como usuario en sitios |
| **PeekYou**               | Agrega resultados sociales y de foros                      |
| **Spiderfoot**            | Automatiza búsquedas OSINT, incluido por nombre            |
| **Social Searcher**       | Busca actividad en redes sociales                          |
| **LinkedIn y Facebook**   | Para búsquedas directas con filtros                        |

---

### 💻 Cómo instalar y usar Spiderfoot para este propósito

#### Requisitos:

- Tener Python 3 instalado
- Tener Git
- Tener una máquina con Linux o WSL (Windows Subsystem for Linux)

---

#### 🔧 Instalación paso a paso (Spiderfoot)

1. **Clonar el repositorio:**

```bash
git clone https://github.com/smicallef/spiderfoot.git
cd spiderfoot
```

2. **Instalar dependencias:**

```bash
pip3 install -r requirements.txt
```

3. **Iniciar la herramienta:**

```bash
python3 sf.py
```

4. **Abrir en el navegador:**

Abre [http://127.0.0.1:5001](http://127.0.0.1:5001)

---

### 🧪 Ejemplo completo de práctica: investigar a una persona con nombre público

#### Escenario:

Supón que quieres investigar a una persona llamada **"Daniela Méndez Silva"**, para un análisis OSINT en un curso de ciberseguridad.

---

#### 🔴 Paso 1: Búsqueda inicial con Google

```text
"Daniela Méndez Silva" site:linkedin.com
"Daniela Méndez Silva" site:facebook.com
"Daniela Méndez Silva" Perú OR Lima
```

✅ Esto puede revelar redes sociales, lugar de trabajo o fotos públicas.

---

#### 🟠 Paso 2: Revisar si usa el nombre como nickname

Entra a:

🔗 [https://namechk.com/](https://namechk.com/)

🔗 [https://knowem.com/](https://knowem.com/)

Escribe: `danielamendez`, `dani.mendez.silva`, etc.

👉 Esto muestra si está registrado en Instagram, Twitter, GitHub, Reddit, etc.

---

#### 🟡 Paso 3: Iniciar Spiderfoot

1. Inicia Spiderfoot (`python3 sf.py`) y abre el navegador.
2. En el panel web, crea un nuevo escaneo.
3. En “Target”, escribe: `Daniela Méndez Silva`
4. Marca módulos relacionados a redes sociales, leaks, foros.
5. Ejecuta el escaneo.

🔍 Te arrojará resultados de:

- Posibles emails asociados
- Cuentas en sitios como LinkedIn
- Fotos de perfil públicas
- Información filtrada en breaches
- Participación en sitios como Github o foros técnicos

---

#### 🟢 Paso 4: Complementar con redes sociales

Usa **LinkedIn, Facebook, Instagram** y busca:

```text
"Daniela Méndez Silva" Lima
"Daniela Méndez Silva" universidad OR trabajo
```

Revisa:

- Lugares que etiqueta
- Universidad o empresa
- Amigos en común
- Comentarios públicos

---

### ⚠️ Aspectos éticos y legales

| Acción                                 | ¿Legal sin permiso? |
| -------------------------------------- | ------------------- |
| Buscar en fuentes públicas             | ✅ Sí               |
| Descargar y almacenar sin compartir    | ✅ Sí               |
| Usar para campañas de acoso o chantaje | ❌ No               |
| Suplantación o doxing                  | ❌ No               |

---

### 📚 Resumen final

| Elemento                  | Detalle                                                   |
| ------------------------- | --------------------------------------------------------- |
| ¿Qué es?                  | Investigación pública de una persona por su nombre        |
| Herramientas recomendadas | Spiderfoot, Google Dorks, Namechk, redes sociales         |
| Instalación destacada     | Spiderfoot (manual o Docker)                              |
| Casos de uso              | Ciberinvestigación, inteligencia, recursos humanos, OSINT |

---

[🔼](#índice)

---

## **908. Investigación de redes sociales por nickname**

### ✅ ¿Qué es?

La **investigación por nickname** (alias, usuario, handle o username) consiste en rastrear la presencia de una persona en **redes sociales, foros, blogs, plataformas de juegos u otros sitios**, usando como única pista su **nombre de usuario**.

Ejemplo: Si alguien usa el nickname **"ciber_ninja21"**, podemos buscar en qué plataformas aparece, qué publica y qué información personal ha dejado expuesta.

---

### 🎯 ¿Para qué sirve?

- Rastrear la huella digital de una persona
- Encontrar redes sociales ocultas o cuentas secundarias
- Verificar si un alias está vinculado con actividades sospechosas
- Investigar en ciberseguridad, recursos humanos, ciberacoso, OSINT, etc.

---

### 🔍 ¿Qué puedes descubrir con un nickname?

| Lo que puedes encontrar     | Ejemplo                            |
| --------------------------- | ---------------------------------- |
| Perfiles en redes sociales  | Instagram, TikTok, Twitter, Reddit |
| Nombre real vinculado       | En bio o publicaciones             |
| Localización o idioma       | Por fotos, horarios o lenguaje     |
| Fotos, correos, páginas web | En la bio o publicaciones          |
| Información sensible        | Opiniones, leaks, filtraciones     |
| Conductas o patrones online | En comunidades o foros             |

---

### 🧰 Herramientas para investigar por nickname

| Herramienta               | Función principal                                           |
| ------------------------- | ----------------------------------------------------------- |
| **Sherlock**              | Busca el nickname en más de 300 redes sociales              |
| **Maigret**               | Parecido a Sherlock, pero más detallado                     |
| **WhatsMyName**           | Sitio web con una gran base de datos de sitios OSINT        |
| **Namechk / KnowEm**      | Webs para verificar nombre de usuario en muchas plataformas |
| **Social Analyzer**       | Análisis más visual de perfiles por alias                   |
| **Spiderfoot / Recon-ng** | Frameworks OSINT que incluyen módulos por nicknames         |

---

### 💻 Cómo instalar **Sherlock** paso a paso

#### 🔧 Requisitos

- Tener Python 3
- Tener Git instalado
- Sistema operativo Linux o WSL en Windows

---

#### 🛠 Instalación de Sherlock

1. Abre la terminal y ejecuta:

```bash
git clone https://github.com/sherlock-project/sherlock.git
cd sherlock
```

2. Instala dependencias:

```bash
pip3 install -r requirements.txt
```

3. Ejecuta Sherlock con un nickname:

```bash
python3 sherlock ciber_ninja21
```

Esto te mostrará todas las plataformas donde ese nickname existe o no.

---

### 🧪 Ejemplo completo de práctica

---

#### 🎯 Objetivo:

Investigar el alias: **"ciber_hunter2024"** y descubrir:

- En qué redes sociales aparece
- Qué tipo de contenido comparte
- Si está relacionado con alguna actividad sospechosa o filtración

---

#### 🔴 Paso 1: Ejecutar Sherlock

```bash
python3 sherlock ciber_hunter2024
```

🔍 Resultado:

```
[+] Found username ciber_hunter2024 on:
    - https://twitter.com/ciber_hunter2024
    - https://github.com/ciber_hunter2024
    - https://www.reddit.com/user/ciber_hunter2024
    - https://www.tiktok.com/@ciber_hunter2024
```

---

#### 🟠 Paso 2: Visitar perfiles manualmente

1. **Twitter**: observa si tiene nombre real, ubicación o enlaces
2. **GitHub**: puede tener proyectos con metadatos o archivos con emails
3. **Reddit**: revisar comentarios y subreddits en los que participa
4. **TikTok**: videos públicos, hashtags, información de la bio

---

#### 🟡 Paso 3: Comprobar si está en leaks

Usar páginas como:

- 🔗 [https://haveibeenpwned.com](https://haveibeenpwned.com)
- 🔗 [https://dehashed.com](https://dehashed.com) (requiere cuenta)

Busca: `ciber_hunter2024` o posibles correos asociados.

---

#### 🟢 Paso 4: Verificar actividad cruzada

Busca en Google con dorks:

```
"ciber_hunter2024" site:github.com
"ciber_hunter2024" email
"ciber_hunter2024" Lima OR Perú
```

También puedes usar `Namechk` o `WhatsMyName`:

🔗 [https://whatsmyname.app/](https://whatsmyname.app/)

🔗 [https://namechk.com/](https://namechk.com/)

---

### ⚠️ Consideraciones éticas

| Acción                               | ¿Es legal sin permiso? |
| ------------------------------------ | ---------------------- |
| Buscar alias en fuentes públicas     | ✅ Sí                  |
| Descargar información pública        | ✅ Sí                  |
| Suplantar identidad o acosar         | ❌ No                  |
| Reutilizar info con fines maliciosos | ❌ No                  |

---

### 📌 Resumen final

| Elemento              | Detalle                                               |
| --------------------- | ----------------------------------------------------- |
| ¿Qué es?              | Búsqueda en internet basada en alias o nickname       |
| Herramienta principal | Sherlock (rápido y simple)                            |
| Complementos útiles   | WhatsMyName, Namechk, Google Dorks                    |
| Casos de uso          | Ciberseguridad, OSINT, selección de personal, forense |

---

[🔼](#índice)

---

## **909. Análisis reverso de imágenes**

### ✅ ¿Qué es el análisis reverso de imágenes?

El **análisis reverso de imágenes** es el proceso de investigar **el origen, contenido y metadatos** de una imagen para obtener información oculta o contexto sobre:

- Dónde se publicó primero
- Si ha sido manipulada
- Quién la tomó (cámara, ubicación GPS, etc.)
- Dónde más ha aparecido en internet
- Con qué otras imágenes se relaciona

---

### 🧠 ¿Para qué sirve?

- 🔎 **Verificar fake news o imágenes manipuladas**
- 👮 **Investigar delitos cibernéticos o rastrear publicaciones**
- 🕵️‍♂️ **Hacer OSINT (inteligencia de fuentes abiertas)**
- 👤 **Identificar personas o lugares por fotos**
- 🔐 **Analizar evidencia digital forense**

---

### 🧰 Herramientas principales para análisis reverso

| Herramienta               | Función principal                                    | Tipo      |
| ------------------------- | ---------------------------------------------------- | --------- |
| **Google Imágenes**       | Búsqueda por imagen inversa                          | Web       |
| **TinEye**                | Búsqueda de dónde más aparece una imagen             | Web       |
| **ExifTool**              | Extraer metadatos ocultos de la imagen (GPS, cámara) | CLI       |
| **FotoForensics**         | Verifica si una imagen fue manipulada                | Web       |
| **Yandex Images**         | Excelente para reconocimiento facial e imágenes      | Web       |
| **Maltego (con plugins)** | OSINT profesional con imagen conectada a redes       | App OSINT |

---

### 🔧 ¿Cómo se instala una herramienta potente como ExifTool?

#### 📦 Instalación en Linux (Ubuntu/Kali/WSL)

```bash
sudo apt update
sudo apt install exiftool
```

#### 📦 En Windows

1. Descargar de: [https://exiftool.org/](https://exiftool.org/)
2. Extraer y ejecutar `exiftool(-k).exe`
3. Puedes renombrarlo como `exiftool.exe` para ejecutarlo fácilmente desde CMD o PowerShell

---

### 📦 Alternativa: Instalar ExifTool vía Python (si usas Python habitualmente)

```bash
pip install pyexiftool
```

---

### ✍️ Ejemplo de uso con ExifTool

Imagina que tienes una imagen llamada `foto1.jpg`.

Ejecuta:

```bash
exiftool foto1.jpg
```

Salida típica:

```
Make                            : Apple
Camera Model Name               : iPhone 11
Date/Time Original              : 2022:08:15 12:34:56
GPS Latitude                    : 12.0432 N
GPS Longitude                   : 77.0282 W
File Modification Date/Time     : 2022:08:15 12:34:57
```

#### 📍 ¿Qué puedes saber con esto?

- 📆 Cuándo se tomó la foto
- 📱 Con qué dispositivo
- 📍 Dónde (coordenadas GPS)
- 👁️ Si fue editada

---

### 🧪 Ejemplo completo y paso a paso

#### 🎯 Objetivo: Analizar una imagen descargada de redes sociales

##### Supongamos que tienes esta imagen: `playa_lima.jpg`

---

#### 🔴 Paso 1: Extraer metadatos con ExifTool

```bash
exiftool playa_lima.jpg
```

##### 🔍 Resultado:

```
File Name                       : playa_lima.jpg
Camera Model Name               : Canon EOS 90D
Date/Time Original              : 2023:03:15 14:22:10
GPS Latitude                    : 12.1211 S
GPS Longitude                   : 77.0321 W
Software                        : Adobe Photoshop CC 2023
```

➡️ Sabemos:

- Es una **foto real**, tomada con cámara profesional.
- Ha sido **editada con Photoshop**.
- Tiene **coordenadas GPS**: podemos pegarlas en Google Maps.

---

#### 🟡 Paso 2: Buscar la imagen en internet con Google Imágenes

1. Ir a: [https://images.google.com](https://images.google.com)
2. Hacer clic en el ícono de cámara 📷
3. Subir `playa_lima.jpg` o pegar su URL

🔍 Resultado: vemos si esa imagen ya circula en internet o es única.

---

#### 🟢 Paso 3: Verificar autenticidad con FotoForensics

1. Ir a: [https://fotoforensics.com](https://fotoforensics.com)
2. Subir la imagen
3. Analizar si fue **modificada**, clonada, editada o alterada

🔍 Verás un análisis de errores, compresión y manipulación por zonas.

---

### ⚠️ Consideraciones Éticas

| Acciones                                   | ¿Permitidas? |
| ------------------------------------------ | ------------ |
| Analizar imágenes propias o públicas       | ✅ Sí        |
| Extraer GPS y ubicación sin consentimiento | ⚠️ Depende   |
| Usar fotos privadas para seguimiento       | ❌ No        |
| Compartir análisis sin permiso             | ⚠️ Riesgoso  |

---

### 📌 Resumen Final

| Punto                 | Detalles                                                    |
| --------------------- | ----------------------------------------------------------- |
| ¿Qué es?              | Analizar metadatos y presencia en red de una imagen         |
| Herramientas clave    | ExifTool, Google Images, TinEye, FotoForensics              |
| Qué puedes saber      | Lugar, fecha, cámara, si ha sido editada, si circula online |
| Uso en ciberseguridad | OSINT, fake news, análisis forense, seguimiento de fuentes  |

---

[🔼](#índice)

---

## **910. Análisis de datos en Twitter y Whatsapp**

### ✅ ¿Qué es el análisis de datos en Twitter y WhatsApp?

El **análisis de datos** en plataformas como **Twitter y WhatsApp** consiste en examinar mensajes, imágenes, horarios, relaciones entre usuarios, palabras clave, etc., para entender patrones, detectar anomalías o realizar investigaciones de seguridad (como OSINT, amenazas o campañas de desinformación).

---

### 🧠 ¿Para qué sirve?

| Aplicación real                          | Plataforma | Ejemplo                                               |
| ---------------------------------------- | ---------- | ----------------------------------------------------- |
| Detección de campañas de desinformación  | Twitter    | Bots que difunden spam político                       |
| Investigación forense                    | WhatsApp   | Rastrear con quién se comunicó un sospechoso y cuándo |
| OSINT (Inteligencia de fuentes abiertas) | Ambas      | Identificar ubicación por imágenes o publicaciones    |
| Análisis de sentimiento                  | Twitter    | Ver si un tema genera emociones positivas o negativas |
| Seguimiento de amenazas                  | Ambas      | Analizar mensajes de odio, terrorismo o ciberdelitos  |

---

### 🔧 Herramientas necesarias

#### Para Twitter:

| Herramienta              | Función                       | Instalación                 |
| ------------------------ | ----------------------------- | --------------------------- |
| Tweepy (Python)          | Acceder a la API de Twitter   | `pip install tweepy`        |
| Twint (scraping sin API) | Scrapea datos sin usar la API | `pip install twint` (extra) |
| Pandas                   | Análisis de datos             | `pip install pandas`        |

#### Para WhatsApp:

| Herramienta          | Función                       | Instalación             |
| -------------------- | ----------------------------- | ----------------------- |
| WhatsApp Exporter    | Exportar chats a texto (.txt) | Función de WhatsApp     |
| Python + Pandas      | Leer y analizar chats         | `pip install pandas`    |
| WordCloud (opcional) | Generar nube de palabras      | `pip install wordcloud` |

---

### 🟢 Cómo se instala

#### En tu máquina con Python:

```bash
pip install pandas wordcloud tweepy
```

#### Para Twint (si no tienes acceso a la API de Twitter):

```bash
git clone https://github.com/twintproject/twint.git
cd twint
pip install -r requirements.txt
python setup.py install
```

---

### 🧪 EJEMPLO COMPLETO

---

#### 1️⃣ Análisis de datos en Twitter con `Tweepy`

##### 🎯 Objetivo: Buscar tuits con la palabra "phishing", analizar cuántos son positivos o negativos.

```python
import tweepy
import pandas as pd
from textblob import TextBlob

# Crea tu cuenta en https://developer.twitter.com y consigue tus claves
api_key = 'TU_API_KEY'
api_key_secret = 'TU_API_SECRET'
access_token = 'TU_ACCESS_TOKEN'
access_token_secret = 'TU_ACCESS_SECRET'

# Autenticación
auth = tweepy.OAuth1UserHandler(api_key, api_key_secret, access_token, access_token_secret)
api = tweepy.API(auth)

# Buscar tuits
tweets = api.search_tweets(q='phishing', lang='en', count=100)

# Analizar
data = []
for tweet in tweets:
    texto = tweet.text
    sentimiento = TextBlob(texto).sentiment.polarity
    data.append({'texto': texto, 'sentimiento': sentimiento})

df = pd.DataFrame(data)
print(df.head())
print("Promedio de sentimiento:", df['sentimiento'].mean())
```

➡️ Esto analiza si los tuits son negativos (valor cercano a -1) o positivos (cercano a +1).

---

#### 2️⃣ Análisis de datos de WhatsApp

##### 🎯 Objetivo: Ver quién habla más y a qué hora.

##### 📤 Paso 1: Exportar el chat

En tu WhatsApp:

> Chat → ... → Más → Exportar chat → _Sin archivos multimedia_ → se guarda como `.txt`

Ejemplo de línea del archivo:

```
[12/06/2024, 9:43:21 p. m.] Juan: Hola, ¿todo bien?
```

---

##### 📊 Código para analizar:

```python
import pandas as pd
import re
from collections import Counter
import matplotlib.pyplot as plt

# Cargar archivo exportado
with open('chat.txt', encoding='utf-8') as f:
    lines = f.readlines()

# Limpiar y extraer datos
data = []
for line in lines:
    match = re.match(r'\[(\d{2}/\d{2}/\d{4}), (\d{1,2}:\d{2}.*?)\] (.*?): (.*)', line)
    if match:
        fecha, hora, autor, mensaje = match.groups()
        data.append({'fecha': fecha, 'hora': hora, 'autor': autor, 'mensaje': mensaje})

df = pd.DataFrame(data)

# Quién escribió más
conteo = df['autor'].value_counts()
print("Mensajes por persona:\n", conteo)

# Horas más activas
df['hora_num'] = pd.to_datetime(df['hora'], errors='coerce').dt.hour
df['hora_num'].dropna().astype(int).plot.hist(bins=24, title='Actividad por hora')
plt.xlabel("Hora del día")
plt.show()
```

🔍 Salida:

- Gráfico de mensajes por hora
- Usuario más activo del chat

---

### 🛡️ Seguridad y Ética

| Acción                               | ¿Es válida?            |
| ------------------------------------ | ---------------------- |
| Analizar tus propios datos           | ✅                     |
| Exportar chats sin permiso           | ❌                     |
| Usar herramientas de Twitter pública | ✅ (respetando TOS)    |
| Compartir análisis sin anonimizar    | ⚠️ Debes tener cuidado |

---

### 📌 Resumen final

| Tema         | Detalles clave                                            |
| ------------ | --------------------------------------------------------- |
| Twitter      | Se puede analizar texto, hashtags, redes, emociones       |
| WhatsApp     | Se puede analizar chats, actividad, frecuencia, contenido |
| Herramientas | Tweepy, Twint, Pandas, WordCloud, ExifTool (imágenes)     |
| Requisitos   | Python, API (en caso de Twitter), exportar chats          |
| Casos reales | OSINT, forense digital, detección de amenazas             |

---

[🔼](#índice)

---

## **911. Investigaciones en Facebook**

### ✅ ¿Qué es la investigación en Facebook?

La **investigación en Facebook** forma parte de lo que se conoce como **OSINT** (Inteligencia de Fuentes Abiertas). Consiste en recopilar información pública disponible en perfiles, publicaciones, grupos, imágenes y más, sin necesidad de violar ninguna ley ni hackear cuentas.

#### 📌 ¿Para qué sirve?

- Ver actividad pública de un perfil
- Analizar redes de amigos
- Rastrear ubicaciones geográficas en publicaciones
- Investigar interacciones en grupos o páginas
- Ver cambios en el nombre del perfil, fotos anteriores, etc.

---

### 🚨 Importante: Legalidad y ética

✔️ Sí puedes:

- Usar datos públicos accesibles sin login.
- Analizar contenido visible para todos.

❌ No puedes:

- Hackear cuentas, eludir bloqueos, ni usar métodos ilegales.
- Usar cuentas falsas para infiltrarte sin consentimiento.

---

### 🔧 Herramientas necesarias para investigar

| Herramienta                         | Función                                         | Instalación o acceso                                          |
| ----------------------------------- | ----------------------------------------------- | ------------------------------------------------------------- |
| **Facebook Graph Search (manual)**  | Buscar publicaciones/personas por palabra clave | No requiere instalación                                       |
| **Facebook ID Finder**              | Obtener el ID numérico de una cuenta            | Sitio web: [https://findmyfbid.com/](https://findmyfbid.com/) |
| **OSINT Tools - Sherlock, Maigret** | Buscar usuarios con mismo nombre de usuario     | `pip install sherlock` / `pip install maigret`                |
| **ExifTool**                        | Ver metadatos de fotos descargadas              | `sudo apt install exiftool` (Linux)                           |
| **Social Analyzer**                 | Recolectar datos públicos de redes sociales     | `git clone` desde GitHub                                      |

---

### 🔍 ¿Cómo se instala?

#### Opción 1: Usar herramientas OSINT

```bash
# Sherlock (buscar perfiles por username)
git clone https://github.com/sherlock-project/sherlock.git
cd sherlock
pip install -r requirements.txt
python3 sherlock.py nombredeusuario
```

#### Opción 2: Social Analyzer

```bash
git clone https://github.com/qeeqbox/social-analyzer.git
cd social-analyzer
npm install
node src/index.js -u nombredeusuario
```

---

### 🧪 Ejemplo completo de investigación en Facebook

---

#### 🔎 Escenario:

Un usuario dejó un comentario sospechoso en una publicación pública. Queremos:

1. Ver su perfil
2. Ver si ha cambiado su nombre
3. Ver publicaciones públicas anteriores
4. Ver en qué páginas o grupos participa

---

#### 🪪 Paso 1: Obtener su ID de Facebook

1. Copia la **URL del perfil** (por ejemplo: `https://www.facebook.com/jose.fernandez.123`)
2. Entra a [https://findmyfbid.com](https://findmyfbid.com)
3. Pega el link → Te mostrará algo como `100012345678901`

---

#### 🧠 Paso 2: Buscar publicaciones públicas

Visita este link reemplazando el ID:

```
https://www.facebook.com/search/100012345678901/stories
```

📌 Esto te muestra todas las **publicaciones públicas** del usuario.

---

#### 🖼️ Paso 3: Descargar imágenes y analizar metadatos

1. Descarga manualmente la foto pública del perfil
2. Usa `exiftool`:

```bash
exiftool nombreimagen.jpg
```

➡️ Si la imagen conserva metadatos, podrías encontrar **fecha, ubicación, modelo de cámara, GPS, etc.**

---

#### 👥 Paso 4: Ver amigos y redes

Muchos perfiles restringen su lista de amigos, pero puedes intentar:

```
https://www.facebook.com/search/100012345678901/friends
```

También puedes observar interacciones en publicaciones públicas (quién comenta, reacciona, etc.) para inferir relaciones.

---

#### 🛠️ Alternativa con Sherlock

```bash
python3 sherlock.py josefernandez123
```

Esto buscará si el nombre de usuario está registrado en otras redes (Instagram, Twitter, YouTube), lo que ayuda a armar un perfil completo de la persona.

---

### 🧩 Resumen final

| Elemento investigado   | Herramienta / Link                               |
| ---------------------- | ------------------------------------------------ |
| ID de perfil           | [https://findmyfbid.com](https://findmyfbid.com) |
| Publicaciones públicas | `facebook.com/search/[ID]/stories`               |
| Fotos y metadatos      | `exiftool`                                       |
| Amigos y relaciones    | `facebook.com/search/[ID]/friends`               |
| Más redes sociales     | Sherlock, Maigret                                |

---

### 📌 Consejo profesional

Aunque las herramientas automáticas ayudan, **el análisis humano es clave**: observar qué publica, cómo se comunica, patrones de comportamiento, y cruces con otras redes.

---

[🔼](#índice)

---

## **912. Maltego**

### 🧠 ¿Qué es Maltego?

**Maltego** es una herramienta de recolección y visualización de datos para realizar análisis de relaciones en redes, personas, dominios, correos, organizaciones, redes sociales, infraestructuras, y más.

🔍 Se basa en el concepto de **transformaciones**: cada dato (como un dominio, IP o correo) se representa como un nodo, y puedes realizar transformaciones para descubrir datos relacionados.

---

### ✅ ¿Para qué sirve?

- Buscar información sobre una **persona** (nombre, correos, redes, teléfono)
- Investigar **dominios** y sus subdominios
- Descubrir **infraestructura de red** (IP, DNS, MX, etc.)
- Rastrear **entidades criminales o grupos** en redes sociales
- Investigar **fugas de información** o conexiones entre perfiles

---

### 🧰 Versiones de Maltego

| Versión                    | Características principales               | Gratuita |
| -------------------------- | ----------------------------------------- | -------- |
| **CE (Community Edition)** | Para uso personal o académico             | ✅ Sí    |
| **Classic**                | Más nodos por transformación              | ❌ No    |
| **XL**                     | Para grandes volúmenes de datos           | ❌ No    |
| **Enterprise**             | Integración con herramientas privadas/CTI | ❌ No    |

---

### 💻 ¿Cómo instalar Maltego?

#### 🔸 Requisitos previos

- Tener **Java** instalado (versión 11 o superior)
- Un equipo con al menos **4 GB de RAM**
- Registro en [https://www.maltego.com/](https://www.maltego.com/) para una cuenta gratuita

---

#### 🔹 Instalación en Windows / Linux / macOS

1. **Ir al sitio oficial**:
   👉 [https://www.maltego.com/downloads/](https://www.maltego.com/downloads/)

2. Descargar la versión correspondiente a tu sistema operativo:

   - `.exe` para Windows
   - `.dmg` para macOS
   - `.deb` o `.tar.gz` para Linux

3. Instala el archivo como cualquier otro programa.

4. Al iniciar por primera vez:

   - Crea una cuenta o inicia sesión.
   - Selecciona la **Community Edition (CE)**.
   - Instala transformaciones gratuitas como:

     - Shodan
     - WhoisXML
     - VirusTotal
     - HaveIBeenPwned
     - DomainTools (limitado)

---

### 🔄 ¿Cómo funciona Maltego?

#### Conceptos clave:

- **Entity (Entidad)**: es un nodo (correo, IP, dominio, nombre, etc.)
- **Transformation (Transformación)**: es una consulta sobre esa entidad para obtener más información.
- **Graph**: es el mapa visual donde se conectan las entidades descubiertas.

---

### 🧪 Ejemplo completo de uso de Maltego (fácil de entender)

#### 🔎 Escenario:

Queremos investigar el dominio **openai.com** para descubrir:

- Subdominios
- IP
- Servicios (como mail, web, etc.)
- Dónde está alojado

---

#### 🧭 Paso a paso:

##### 1. Abre Maltego

Selecciona "New Graph".

##### 2. Añade una entidad de tipo **Domain**

- Haz clic en la barra izquierda.
- Arrastra el icono **Domain** al centro.
- Haz doble clic en él y cambia el nombre a `openai.com`.

##### 3. Ejecuta una transformación: **To IP Address \[DNS]**

- Clic derecho sobre el dominio.
- Ve a "All Transforms" → "DNS from Domain" → "To IP Address \[DNS]"

📍 Resultado: Aparecen una o más direcciones IP.

##### 4. Busca subdominios

- Clic derecho sobre el dominio.
- Ejecuta la transformación: **To DNS Name – A record (subdomain)**

📍 Resultado: Se listarán subdominios como `api.openai.com`, `chat.openai.com`, etc.

##### 5. Analiza puertos o servicios

- Clic derecho sobre una IP descubierta.
- Ejecuta: **To Ports and Services \[Shodan]** (requiere API Key de Shodan)

##### 6. Verifica si el dominio o correo está comprometido

- Arrastra la entidad **Email Address**
- Escribe `info@openai.com` o uno genérico
- Ejecuta transformación: **To Breach Data \[HaveIBeenPwned]**

---

### 🧩 Ejemplo visual resumido:

```
[openai.com]
   ↓
[IP Address]
   ↓
[Subdomains]
   ↓
[Puertos / Servicios]
   ↓
[Ubicación del servidor]
   ↓
[Correos filtrados]
```

---

### 📌 Consejos útiles

- Puedes guardar tu **graph** y exportarlo como imagen o PDF.
- Usa la **función de timeline** para ver en qué momento se ejecutó cada transformación.
- Puedes instalar más **transformaciones externas** desde el Maltego Transform Hub.
- No hagas abuso de transformaciones gratuitas, tienen límite diario.

---

### 🛡️ Ética y uso responsable

Maltego debe utilizarse únicamente con fines legales y éticos, como:

- Auditorías de ciberseguridad
- Investigaciones académicas o forenses
- Recolección de inteligencia en fuentes abiertas

❌ No usar para acoso, espionaje privado, o propósitos ilegales.

---

### ✅ Conclusión

**Maltego** es una herramienta visual y poderosa para OSINT. Permite conectar datos aparentemente sueltos y ver relaciones ocultas entre entidades digitales. No requiere saber programación y te da resultados en segundos.

---

[🔼](#índice)

---

| **Inicio**         | **atrás 13**                  | **Siguiente 15**                                              |
| ------------------ | ----------------------------- | ------------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./7_13_Hacking_Etico.md) | [⏩](./7_15_Escaneo_Activo_y_Analisis_de_Vulnerabilidades.md) |
