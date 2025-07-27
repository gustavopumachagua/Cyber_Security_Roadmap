| **Inicio**         | **atrás 5**                                  | **Siguiente 7**                                            |
| ------------------ | -------------------------------------------- | ---------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./7_5_Redes_de_Internet_Profesional.md) | [⏩](./7_7_Seguridad_Informatica_para_Equipos_Tecnicos.md) |

---

## **Índice**

| Temario                                                                                                                |
| ---------------------------------------------------------------------------------------------------------------------- |
| [711. Retos: define tu rol en seguridad informática](#711-retos-define-tu-rol-en-seguridad-informática)                |
| [712. ¿Qué es seguridad informática?](#712-qué-es-seguridad-informática)                                               |
| [713. Roles y oportunidades laborales de la ciberseguridad](#713-roles-y-oportunidades-laborales-de-la-ciberseguridad) |
| [714. Glosario de seguridad informática](#714-glosario-de-seguridad-informática)                                       |
| [715. InfoSec o seguridad de la información](#715-infosec-o-seguridad-de-la-información)                               |
| [716. Ciberinteligencia](#716-ciberinteligencia)                                                                       |
| [717. Malware](#717-malware)                                                                                           |
| [718. Criptografía y esteganografía](#718-criptografía-y-esteganografía)                                               |
| [719. Código seguro](#719-código-seguro)                                                                               |
| [720. Pentesting](#720-pentesting)                                                                                     |
| [721. Seguridad forense](#721-seguridad-forense)                                                                       |
| [722. Seguridad en redes](#722-seguridad-en-redes)                                                                     |
| [723. Certificaciones internacionales de ciberseguridad](#723-certificaciones-internacionales-de-ciberseguridad)       |
| [724. Cómo hacer una carrera en seguridad informática](#724-cómo-hacer-una-carrera-en-seguridad-informática)           |

# **Guía para Aprender Seguridad Informática**

## **711. Retos: define tu rol en seguridad informática**

### 🧠 ¿Qué es la seguridad informática?

Es el conjunto de **prácticas, herramientas y conocimientos** destinados a **proteger los sistemas, redes y datos** contra accesos no autorizados, ataques, robos, daño o interrupciones.

---

### 🎯 ¿Por qué es importante definir tu rol?

Porque la **ciberseguridad** es muy amplia. Si no defines un rol, es fácil sentirse perdido o intentar aprender todo a la vez (lo cual no es práctico).

> Es como en medicina: no todos son cirujanos. Algunos son radiólogos, otros pediatras o psicólogos. En ciberseguridad pasa lo mismo.

---

### 🧩 Principales roles en ciberseguridad (con ejemplos)

#### 🔎 1. **Analista SOC (Centro de Operaciones de Seguridad)**

**Qué hace:**

Monitorea alertas de seguridad en tiempo real.
Detecta, analiza y responde a incidentes.

**Ejemplo diario:**

Detecta un intento de acceso no autorizado y bloquea la IP desde un firewall.

**Herramientas comunes:**

- SIEM (como Splunk, AlienVault)
- Wireshark
- Antivirus/EDR

---

#### 🔐 2. **Especialista en Pentesting (Hacker ético)**

**Qué hace:**

Ataca sistemas con permiso para encontrar vulnerabilidades antes que los criminales.

**Ejemplo diario:**

Encuentra una falla en una página web que permite robar contraseñas (XSS, SQLi).

**Herramientas comunes:**

- Kali Linux
- Burp Suite
- Metasploit

---

#### 🔧 3. **Administrador de Seguridad o Infraestructura Segura**

**Qué hace:**

Configura firewalls, VPN, reglas de red, usuarios, sistemas operativos seguros.

**Ejemplo diario:**

Instala y configura un firewall para una empresa, bloqueando puertos inseguros.

**Herramientas comunes:**

- PfSense, Fortinet
- Cisco ASA
- Windows Server, Linux Hardened

---

#### 🧪 4. **Analista Forense Digital**

**Qué hace:**

Investiga incidentes de seguridad **después** de que ocurrieron. Busca evidencia.

**Ejemplo diario:**

Recupera archivos borrados de un disco duro después de un ataque de ransomware.

**Herramientas comunes:**

- Autopsy
- FTK Imager
- EnCase

---

#### 🧱 5. **Especialista en Gestión de Riesgos / GRC**

**Qué hace:**

Evalúa riesgos, define políticas, asegura cumplimiento con leyes (ISO 27001, NIST, etc.)

**Ejemplo diario:**

Crea una política para que los empleados cambien contraseñas cada 90 días.

**Herramientas comunes:**

- Excel + Marcos: ISO, NIST, COBIT
- Herramientas GRC: Archer, Varonis

---

#### 🌐 6. **Ingeniero de Seguridad en la Nube**

**Qué hace:**

Protege entornos en AWS, Azure, Google Cloud.

**Ejemplo diario:**

Configura reglas de acceso en AWS para que nadie acceda públicamente a una base de datos.

**Herramientas comunes:**

- AWS IAM, Azure Security Center
- Terraform
- CloudTrail, GuardDuty

---

### 🚀 ¿Cómo “instalar” tu rol? (Pasos para elegir)

#### ✅ 1. **Evalúate**

- ¿Te gusta investigar y resolver misterios? → Forense o analista SOC
- ¿Te encanta romper cosas (de forma legal)? → Pentester
- ¿Te interesan las normas, políticas, cumplimiento? → GRC
- ¿Te gustan los cables, redes, firewalls? → Admin de seguridad
- ¿Prefieres la nube y automatización? → Ingeniero cloud security

---

#### ✅ 2. **Aprende lo básico común**

Antes de especializarte, debes entender:

| Área                                | ¿Por qué es clave?                     |
| ----------------------------------- | -------------------------------------- |
| Redes (TCP/IP, subredes, puertos)   | Todo ataque viaja por red              |
| Sistemas Operativos (Windows/Linux) | Son el blanco de la mayoría de ataques |
| Ciberseguridad general              | Te da contexto y lenguaje común        |
| Comandos de terminal                | Todo es más eficiente en consola       |
| Herramientas básicas                | Wireshark, Nmap, VirtualBox, etc.      |

---

#### ✅ 3. **Haz laboratorios prácticos**

Usa **máquinas virtuales** para simular roles. Por ejemplo:

- Instala **Kali Linux** y ataca una máquina vulnerable (`Metasploitable`, `DVWA`)
- Usa **Packet Tracer** para simular redes y firewalls
- Usa **Wireshark** para capturar tráfico en una red casera

---

#### ✅ 4. **Certificaciones recomendadas según el rol**

| Rol             | Certificación inicial sugerida       |
| --------------- | ------------------------------------ |
| Pentester       | CEH, eJPT, OSCP (avanzado)           |
| SOC             | CompTIA Security+, Blue Team Level 1 |
| Forense         | CHFI, eCDFP                          |
| GRC             | ISO 27001 Foundation, CISM           |
| Infraestructura | Cisco CCNA Security, Fortinet NSE    |
| Cloud           | AWS Security Specialty, Azure SC-100 |

---

### ✅ Ejemplo completo: “Instalarse” como Pentester Junior

#### 🔹 Perfil deseado:

- Le gusta investigar
- Aprende rápido herramientas técnicas
- Le apasiona “romper y entender cómo funcionan las cosas”

#### 🔹 Ruta paso a paso:

1. **Estudiar redes y protocolos** (TCP/IP, puertos, ARP, DNS, etc.)
2. **Aprender Linux básico** (navegar carpetas, permisos, comandos)
3. **Instalar Kali Linux o Parrot OS**
4. **Practicar con herramientas**: Nmap, Burp Suite, Hydra, etc.
5. **Usar plataformas de práctica**:

   - Hack The Box
   - TryHackMe
   - VulnHub

6. **Estudiar y rendir eJPT o CEH**
7. **Crear un portafolio con capturas y reportes**
8. **Buscar puestos junior o internships en seguridad ofensiva**

---

### 🧾 Resumen general

| Paso                        | Acción                                            |
| --------------------------- | ------------------------------------------------- |
| 1. Conoce los roles         | Aprende qué áreas existen y qué hacen             |
| 2. Identifica tus intereses | Con base en tu estilo, define a cuál apuntar      |
| 3. Aprende lo común         | Redes, sistemas, fundamentos de ciberseguridad    |
| 4. Practica en labs         | VirtualBox, Packet Tracer, Hack The Box, etc.     |
| 5. Enfócate                 | Estudia certificaciones según el rol que elegiste |

---

[🔼](#índice)

---

## **712. ¿Qué es seguridad informática?**

### 🧠 **Definición fácil de entender**

La **seguridad informática** (también llamada **ciberseguridad**) es el **conjunto de técnicas, herramientas y prácticas** que se usan para **proteger los sistemas informáticos, redes, dispositivos y datos** de:

- **Accesos no autorizados**
- **Robo o pérdida de información**
- **Ataques informáticos**
- **Errores humanos**
- **Malware (virus, troyanos, etc.)**

---

### 🎯 ¿Por qué es importante?

Porque hoy en día **casi todo** depende de computadoras y redes:

| Ejemplo    | Qué pasa si no hay seguridad                        |
| ---------- | --------------------------------------------------- |
| Bancos     | Pueden robarte dinero o datos                       |
| Hospitales | Pueden manipular historiales médicos                |
| Escuelas   | Pueden perder notas y documentos                    |
| Casas      | Hackers pueden acceder a tus cámaras o WiFi         |
| Empresas   | Pueden perder millones por ataques o fugas de datos |

---

### 🔑 **Principios fundamentales de la seguridad informática (la triada CIA)**

| Sigla | Significado      | ¿Qué protege?                                         | Ejemplo                                             |
| ----- | ---------------- | ----------------------------------------------------- | --------------------------------------------------- |
| **C** | Confidencialidad | Que nadie acceda sin permiso                          | Solo tú puedes leer tus correos                     |
| **I** | Integridad       | Que la información no sea modificada sin autorización | Tus notas en la universidad no deben alterarse      |
| **A** | Disponibilidad   | Que la información esté siempre accesible             | Puedes entrar a tu banco online cuando lo necesites |

---

### 🧩 Tipos de seguridad informática

| Tipo                        | Qué protege                       |
| --------------------------- | --------------------------------- |
| Seguridad de red            | Routers, switches, tráfico de red |
| Seguridad de sistemas       | Windows, Linux, Mac               |
| Seguridad de aplicaciones   | Webs, apps móviles                |
| Seguridad de la información | Datos personales, documentos      |
| Seguridad en la nube        | AWS, Azure, Google Cloud          |
| Seguridad física            | Servidores, dispositivos físicos  |
| Ciberseguridad ofensiva     | Pentesting, hacking ético         |
| Ciberseguridad defensiva    | Firewalls, detección de amenazas  |

---

### 🦠 Tipos de amenazas comunes

| Amenaza     | ¿Qué hace?                              | Ejemplo real                                                        |
| ----------- | --------------------------------------- | ------------------------------------------------------------------- |
| Virus       | Infecta archivos                        | Un .exe infectado que daña tu sistema                               |
| Phishing    | Suplantación para robar datos           | Correo falso de "tu banco" que pide tu contraseña                   |
| Ransomware  | Cifra archivos y pide rescate           | WannaCry atacó a empresas y hospitales                              |
| Keylogger   | Captura lo que escribes                 | Robo de contraseñas por programas invisibles                        |
| Ataque DDoS | Satura un servidor para que no funcione | Un sitio web se cae porque lo atacan con miles de peticiones falsas |

---

### ⚙️ ¿Cómo se "instala" la seguridad informática? (Aplicación práctica)

No se instala como un software único, pero **se implementa por capas**. Ejemplo en una oficina:

1. 🔐 **Contraseñas fuertes y políticas de acceso**
2. 🧱 **Firewall que filtra conexiones no deseadas**
3. 💾 **Antivirus y antimalware**
4. 🧠 **Capacitación de usuarios contra phishing**
5. 🧮 **Backups automáticos de datos importantes**
6. 🌐 **VPN para trabajo remoto**
7. 🛡️ **Actualizaciones automáticas de sistemas**

---

### ✅ Ejemplo completo y fácil de entender

#### 🏠 Escenario: Tu casa

Tienes una laptop, un smartphone, y una red WiFi. ¿Cómo aplicar seguridad informática?

| Elemento                | Riesgo                           | Medida de seguridad                        |
| ----------------------- | -------------------------------- | ------------------------------------------ |
| WiFi sin contraseña     | Vecinos o hackers pueden entrar  | Colocas una contraseña WPA2 fuerte         |
| Laptop sin antivirus    | Puede infectarse con malware     | Instalas antivirus gratuito como Avast     |
| Teléfono desactualizado | Vulnerabilidades abiertas        | Actualizas Android o iOS con parches       |
| Contraseñas débiles     | Te pueden hackear el Facebook    | Usas gestor de contraseñas (ej. Bitwarden) |
| Niños en internet       | Pueden entrar a sitios inseguros | Activas control parental o SafeSearch      |

➡️ Resultado: Aunque no seas experto, **ya estás aplicando seguridad informática** en tu vida diaria.

---

### 🎓 Resumen en 1 frase:

> **La seguridad informática es como una cerradura digital para todo lo que usas en internet: tus datos, tu identidad y tus dispositivos.**

---

### 📦 ¿Quieres probarla? (Mini-lab para ti)

👉 **Laboratorio rápido (sin peligro):**

1. **Instala VirtualBox**
2. Crea 2 máquinas virtuales: una con Windows y otra con Kali Linux
3. En Kali, abre una terminal y ejecuta:

   ```
   nmap -sS <IP de Windows>
   ```

4. Verás los puertos abiertos, simulando un escaneo de red

🎯 Con eso ya estás **probando** una herramienta de seguridad informática.

---

[🔼](#índice)

---

## **713. Roles y oportunidades laborales de la ciberseguridad**

### ✅ ¿Qué es la Ciberseguridad?

La **ciberseguridad** es el conjunto de prácticas, tecnologías y procesos diseñados para proteger redes, dispositivos, programas y datos de ataques, daños o accesos no autorizados.

---

### 🎯 Objetivo de la Ciberseguridad

Proteger:

- Datos personales y empresariales
- Infraestructuras tecnológicas (servidores, redes, dispositivos)
- Software y sistemas operativos
- Aplicaciones web y móviles

---

### 🔐 Principales Roles en Ciberseguridad (con ejemplos simples)

#### 1. **Analista de Ciberseguridad**

**Qué hace:** Monitorea redes y sistemas para detectar actividades sospechosas.

📌 **Ejemplo:** Como un guardia de seguridad en un edificio que mira las cámaras todo el tiempo.

**Herramientas comunes:** SIEM (como Splunk, QRadar)

---

#### 2. **Ingeniero de Seguridad**

**Qué hace:** Diseña e implementa soluciones de seguridad (firewalls, antivirus, etc.).

📌 **Ejemplo:** Es como un arquitecto que construye muros de protección alrededor de una casa.

**Conocimientos necesarios:** Redes, sistemas operativos, scripting (Python, Bash)

---

#### 3. **Hacker Ético (o Pentester)**

**Qué hace:** Simula ataques para encontrar vulnerabilidades antes que lo haga un hacker malicioso.

📌 **Ejemplo:** Como un ladrón contratado por el dueño de una casa para ver si puede entrar.

**Herramientas comunes:** Metasploit, Burp Suite, Kali Linux

---

#### 4. **Analista de Incidentes**

**Qué hace:** Responde cuando hay un ataque real. Investiga qué pasó, cómo entraron y cómo detenerlos.

📌 **Ejemplo:** Como los bomberos que llegan cuando hay un incendio.

---

#### 5. **Especialista en Cumplimiento y Riesgos**

**Qué hace:** Asegura que la empresa cumpla con leyes de protección de datos (como GDPR, ISO 27001).

📌 **Ejemplo:** Como un abogado que revisa que todo esté en regla.

---

#### 6. **Forense Digital**

**Qué hace:** Investiga crímenes cibernéticos recuperando datos borrados y rastreando al atacante.

📌 **Ejemplo:** Como un detective digital que busca huellas en las computadoras.

---

#### 7. **Arquitecto de Seguridad**

**Qué hace:** Diseña toda la estructura de seguridad de una empresa.

📌 **Ejemplo:** Como un ingeniero que diseña toda la defensa de un castillo.

---

### 🚀 ¿Cómo iniciarte en Ciberseguridad? (Instalación del conocimiento)

#### Paso 1: Aprende lo básico

- Redes (TCP/IP, DNS, protocolos)
- Sistemas Operativos (Linux y Windows)
- Fundamentos de seguridad (confidencialidad, integridad, disponibilidad)

📚 Cursos recomendados:

- Curso gratuito de ciberseguridad en **Coursera**, **EdX** o **Cisco NetAcad**
- Libro: “Cybersecurity for Beginners” de Raef Meeuwisse

---

#### Paso 2: Instala herramientas básicas

- **Kali Linux**: un sistema operativo con herramientas para pruebas de seguridad.
- **Wireshark**: para analizar tráfico de red.
- **VirtualBox** o **VMware**: para crear entornos seguros de práctica.
- **Metasploitable**: máquina virtual vulnerable para practicar.

---

#### Paso 3: Certifícate

Las certificaciones ayudan mucho para entrar al mercado laboral:

- **CompTIA Security+** (Nivel principiante)
- **CEH (Certified Ethical Hacker)**
- **CISSP (avanzado)**

---

#### Paso 4: Participa en retos y comunidades

- Hack The Box, TryHackMe, CTFs (Capture the Flag)
- Participa en foros como Reddit r/netsec, Discord de ciberseguridad, etc.

---

### 💼 Oportunidades Laborales

- **Empresas tecnológicas** (Google, Microsoft)
- **Bancos y aseguradoras**
- **Gobiernos y fuerzas armadas**
- **Consultoras de seguridad** (KPMG, Deloitte, PwC)
- **Startups de ciberseguridad**
- **Trabajo remoto para empresas extranjeras**

**Salarios promedio (Latinoamérica):**

- Junior: \$500 – \$1,200 USD/mes
- Semi-senior: \$1,500 – \$2,500 USD/mes
- Senior: \$3,000 – \$6,000 USD/mes

---

### 🧩 Ejemplo completo de carrera en ciberseguridad

#### Caso: María, de 0 a Pentester

1. **Inicio (2022)**: María estudió redes básicas y Linux.
2. **Primeros pasos (2023)**:

   - Tomó un curso en TryHackMe
   - Aprendió a usar Kali Linux
   - Hizo proyectos en GitHub (simuló ataques y defensas)

3. **Certificación (2023)**:

   - Obtuvo CompTIA Security+
   - Participó en Hack The Box

4. **Primer trabajo (2024)**:

   - Consiguió puesto como analista SOC (monitor de seguridad)

5. **Ascenso (2025)**:

   - Se convirtió en pentester junior
   - Sigue aprendiendo para obtener CEH

---

### 🧠 Resumen Final

| Rol                       | Tareas Principales                             | Nivel      |
| ------------------------- | ---------------------------------------------- | ---------- |
| Analista SOC              | Monitoreo, detección de amenazas               | Junior     |
| Ingeniero de Seguridad    | Diseñar e implementar medidas de protección    | Mid        |
| Pentester (Hacker ético)  | Simular ataques, encontrar fallas              | Mid/Senior |
| Analista de Incidentes    | Responder a ataques, investigar                | Mid        |
| Forense Digital           | Investigar cibercrímenes                       | Senior     |
| Consultor en Cumplimiento | Revisar políticas, asegurar cumplimiento legal | Mid        |

---

[🔼](#índice)

---

## **714. Glosario de seguridad informática**

### 📘 ¿Qué es un Glosario de Seguridad Informática?

Un **glosario** es una **lista de palabras técnicas** con sus definiciones, usado para entender el lenguaje especializado de un tema.

En **seguridad informática**, hay muchos términos técnicos (como firewall, phishing, malware) que es vital conocer para:

- Entender cómo proteger sistemas y redes
- Leer documentación técnica
- Estudiar ciberseguridad o trabajar en ese campo

---

### ✅ Términos Clave del Glosario de Seguridad Informática (con ejemplos fáciles)

Te los agrupo por categorías para que sea más claro.

---

#### 🔐 **Amenazas y ataques**

| Término               | Definición clara                                                  | Ejemplo sencillo                                                                          |
| --------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| **Malware**           | Programa dañino (virus, troyano, etc.)                            | Como una “garrapata” que se pega al sistema y lo daña.                                    |
| **Phishing**          | Engaño para robar información                                     | Un correo falso que dice “tu banco necesita tu clave”                                     |
| **Ransomware**        | Malware que secuestra tus archivos y pide rescate                 | Como un ladrón que encierra tus fotos y pide dinero para devolverlas                      |
| **Ataque DDoS**       | Muchos dispositivos atacan un servidor para que deje de funcionar | Como una multitud que bloquea la entrada a una tienda                                     |
| **Ingeniería social** | Manipular a personas para obtener acceso o datos                  | Hacer que alguien te diga su contraseña por teléfono haciéndote pasar por soporte técnico |

---

#### 🔒 **Defensas y herramientas**

| Término                             | Definición clara                                    | Ejemplo sencillo                                                               |
| ----------------------------------- | --------------------------------------------------- | ------------------------------------------------------------------------------ |
| **Firewall**                        | Filtro que bloquea conexiones peligrosas            | Como un portero que no deja pasar a desconocidos                               |
| **Antivirus**                       | Programa que detecta y elimina malware              | Como un médico que detecta y cura enfermedades del sistema                     |
| **Autenticación**                   | Verificación de identidad                           | Ingresar con usuario y contraseña                                              |
| **MFA (autenticación multifactor)** | Requiere más de un método de acceso                 | Como usar clave + código SMS + huella dactilar                                 |
| **SIEM**                            | Sistema que analiza y registra eventos de seguridad | Como una central de vigilancia 24/7 que guarda todo lo que pasa en el edificio |

---

#### 🧱 **Vulnerabilidades y riesgos**

| Término                  | Definición clara                              | Ejemplo sencillo                                          |
| ------------------------ | --------------------------------------------- | --------------------------------------------------------- |
| **Vulnerabilidad**       | Falla que puede ser explotada por un atacante | Una ventana abierta en una casa                           |
| **Exploit**              | Código que aprovecha una vulnerabilidad       | Una ganzúa que entra por esa ventana abierta              |
| **Zero-Day**             | Vulnerabilidad nueva que nadie conoce aún     | Una grieta secreta en una pared que solo el atacante sabe |
| **Parches de seguridad** | Actualización que corrige fallos              | Como reparar un candado roto para que no entren ladrones  |

---

#### 📊 **Cumplimiento y gestión**

| Término                    | Definición clara                    | Ejemplo sencillo                                                    |
| -------------------------- | ----------------------------------- | ------------------------------------------------------------------- |
| **Política de seguridad**  | Conjunto de reglas de protección    | Como las reglas de seguridad en una empresa                         |
| **Auditoría de seguridad** | Revisión para detectar problemas    | Como una inspección de seguridad en un aeropuerto                   |
| **GDPR / LOPI**            | Leyes que protegen datos personales | Como reglas que prohíben que tu información se comparta sin permiso |

---

#### 🧠 **Otros conceptos clave**

| Término                    | Definición clara                                     | Ejemplo sencillo                                                  |
| -------------------------- | ---------------------------------------------------- | ----------------------------------------------------------------- |
| **Cifrado (encriptación)** | Transformar datos para que no se entiendan sin clave | Como hablar en código secreto                                     |
| **Red privada (VPN)**      | Conexión segura que oculta tu tráfico                | Como usar un túnel para evitar ser visto                          |
| **Penetration Testing**    | Prueba para ver si se puede entrar en un sistema     | Como contratar a un ladrón para ver si puede abrir tu caja fuerte |

---

### 💻 ¿Cómo “instalar” este glosario en tu mente? (cómo aprenderlo)

1. **Haz tarjetas de memoria (flashcards)**

   Usa apps como Quizlet o Anki para practicar los términos.

2. **Relaciona cada palabra con una imagen o ejemplo real**

   Por ejemplo, phishing → imagen de un anzuelo pescando contraseñas.

3. **Aplica el vocabulario en ejercicios prácticos**

   Crea un caso ficticio donde alguien sufre un ataque y usa los términos del glosario para describirlo.

4. **Haz mapas mentales o esquemas**

   Agrupa palabras por temas como “ataques”, “defensas”, “leyes”.

---

### 🧩 Ejemplo completo de uso del glosario en una situación real

#### Caso: Sofía, técnica en soporte

Sofía trabaja en soporte técnico de una empresa. Un día, un empleado dice que no puede acceder a sus archivos.

Sofía investiga:

1. Nota que los archivos están **cifrados** y hay un mensaje pidiendo dinero.

   🔍 Palabra: **Ransomware**

2. Revisa el correo electrónico del empleado y ve que recibió un archivo sospechoso de “Recursos Humanos”.

   🔍 Palabra: **Phishing**

3. Ve que el antivirus estaba desactivado y que la empresa no aplicó las actualizaciones.

   🔍 Palabras: **Antivirus**, **Parches de seguridad**, **Vulnerabilidad**

4. Llama al equipo de seguridad para contener la amenaza y reportar el incidente.

   🔍 Palabras: **Incidente**, **Política de seguridad**

Gracias al conocimiento del glosario, Sofía pudo:

✅ Entender qué ocurrió

✅ Comunicarlo claramente

✅ Seguir los pasos correctos de respuesta

---

### 🧠 Conclusión Final

🔑 Aprender el glosario de seguridad informática **es como aprender un nuevo idioma**: el idioma de la ciberseguridad.

✔️ Con este conocimiento puedes:

- Estudiar ciberseguridad con más facilidad
- Entender documentación técnica
- Tener mejores oportunidades laborales
- Hablar con colegas y expertos con confianza

---

[🔼](#índice)

---

## **715. InfoSec o seguridad de la información**

### 🧩 ¿Qué es InfoSec o Seguridad de la Información?

**InfoSec** (abreviatura de _Information Security_) es el conjunto de **estrategias, políticas, procesos y herramientas** que se usan para proteger **la información** de una organización o persona frente a:

- Acceso no autorizado
- Uso indebido
- Divulgación
- Modificación
- Destrucción

🛡️ **No se trata solo de computadoras**: también puede aplicarse a archivos físicos, conversaciones, redes, y más.

---

### 🎯 Objetivos principales de InfoSec (la "tríada CIA")

Los **3 pilares de InfoSec** son:

| Pilar                                  | ¿Qué protege?                                           | Ejemplo simple                                      |
| -------------------------------------- | ------------------------------------------------------- | --------------------------------------------------- |
| **C**onfidentiality (Confidencialidad) | Solo las personas autorizadas pueden ver la información | Como un diario con candado                          |
| **I**ntegrity (Integridad)             | La información no ha sido alterada sin permiso          | Como sellar un sobre: si está roto, fue abierto     |
| **A**vailability (Disponibilidad)      | La información debe estar accesible cuando se necesite  | Como tener las llaves de casa cuando quieres entrar |

---

### ✅ ¿Qué protege InfoSec?

- Archivos digitales (documentos, bases de datos)
- Archivos físicos (papeles, contratos)
- Sistemas y aplicaciones
- Redes y servidores
- Identidad de los usuarios
- Comunicaciones (emails, chats)

---

### 🔒 Ejemplos de riesgos que InfoSec quiere evitar

| Riesgo                    | Ejemplo fácil                                          |
| ------------------------- | ------------------------------------------------------ |
| Robo de datos             | Un hacker roba información de clientes                 |
| Alteración de registros   | Alguien cambia tu historial bancario                   |
| Filtración de información | Se publica en internet un documento confidencial       |
| Interrupción del servicio | Un ataque deja fuera de línea la página de una empresa |

---

### 🛠️ ¿Cómo se "instala" la Seguridad de la Información?

Es decir, ¿cómo se implementa InfoSec en la vida real?

#### 🧱 1. **Definir políticas de seguridad**

- Son las reglas internas de la empresa para proteger la información.
- Ejemplo: “Nadie puede compartir contraseñas por correo.”

#### 🔐 2. **Usar controles de acceso**

- Solo las personas con permiso pueden ver cierta información.
- Ejemplo: Un cajero puede ver las cuentas, pero no los sueldos del personal.

#### 🔄 3. **Hacer copias de seguridad (backups)**

- Se guarda la información en otro lugar por si se pierde.
- Ejemplo: Guardar archivos importantes en la nube y en un disco externo.

#### 🧪 4. **Realizar auditorías y revisiones**

- Se revisa que todo funcione como debe.
- Ejemplo: Verificar quién accedió a los archivos confidenciales la semana pasada.

#### 🧠 5. **Educar al personal**

- Las personas deben conocer las buenas prácticas.
- Ejemplo: No abrir enlaces sospechosos en correos.

#### 🛡️ 6. **Implementar herramientas tecnológicas**

- Antivirus, cortafuegos (firewalls), cifrado, autenticación de múltiples factores, etc.

---

### 🧠 InfoSec vs Ciberseguridad – ¿Es lo mismo?

❌ **No exactamente**, aunque están relacionadas.

| Aspecto | InfoSec                              | Ciberseguridad                   |
| ------- | ------------------------------------ | -------------------------------- |
| Enfoque | Proteger **información** en general  | Proteger **información digital** |
| Incluye | Seguridad física, procesos, personas | Solo tecnología y sistemas       |
| Ejemplo | Proteger un contrato en papel        | Proteger un archivo en la nube   |

**Entonces, InfoSec = ciberseguridad + más cosas.**

---

### 🧩 Ejemplo completo y práctico de InfoSec en acción

#### 🎬 Caso: Empresa "DataPlus"

**Problema:** La empresa maneja información confidencial de clientes. Un día, un empleado recibe un correo falso (phishing), hace clic, y un atacante accede a documentos sensibles.

#### 🔍 ¿Qué hace el equipo de InfoSec?

1. **Confidencialidad**

   - Detectan que la información fue accedida sin permiso.
   - Activan un sistema de control de accesos para revocar permisos no autorizados.

2. **Integridad**

   - Revisan si los datos fueron alterados.
   - Usan registros (logs) para verificar cambios y restauran las copias de seguridad.

3. **Disponibilidad**

   - Garantizan que los sistemas sigan funcionando mientras investigan.
   - Usan respaldo para continuar operaciones.

#### 🛠️ Medidas que implementan después

- Capacitan al personal en **seguridad de la información**
- Configuran filtros de correo para bloquear phishing
- Agregan **MFA (autenticación multifactor)**
- Hacen auditorías mensuales

---

### 📚 ¿Cómo aprender InfoSec desde cero?

#### Paso 1: Entender los conceptos básicos

- Tríada CIA
- Qué es un riesgo, amenaza y vulnerabilidad

#### Paso 2: Hacer cursos introductorios

- **“Introduction to Information Security”** en Coursera, Udemy o YouTube
- Libros como “Information Security Basics” o “ISO/IEC 27001 Simplified”

#### Paso 3: Practicar

- Crea tus propias políticas de seguridad
- Usa cifrado en archivos personales
- Haz simulacros (cómo actuar ante un ataque)

---

### ✅ Resumen Final

| Término clave         | ¿Qué significa?                                |
| --------------------- | ---------------------------------------------- |
| InfoSec               | Protección de la información (no solo digital) |
| Tríada CIA            | Confidencialidad, Integridad, Disponibilidad   |
| Política de seguridad | Reglas que protegen los datos                  |
| Control de acceso     | Permitir/ver información según permisos        |
| Ciberseguridad        | Subconjunto de InfoSec centrado en lo digital  |

---

[🔼](#índice)

---

## **716. Ciberinteligencia**

### 🧠 ¿Qué es la **Ciberinteligencia**?

**Ciberinteligencia** (o _Cyber Threat Intelligence - CTI_) es el proceso de **recoger, analizar y usar información** sobre **amenazas digitales**, para **prevenir ataques**, entender cómo piensan los hackers y proteger mejor los sistemas.

📌 No se trata solo de recolectar datos, sino de **transformar información cruda en conocimiento útil** para tomar decisiones de seguridad.

---

### 🎯 ¿Para qué sirve la Ciberinteligencia?

Sirve para:

- Prevenir ataques informáticos antes de que ocurran.
- Detectar quién está detrás de un ataque y por qué lo hace.
- Descubrir vulnerabilidades que aún no han sido explotadas.
- Proteger datos, infraestructura y reputación.

🔍 En resumen: **ver antes que ataquen y saber cómo defenderse.**

---

### 🛠️ ¿Cómo se “instala” la Ciberinteligencia?

(Es decir, cómo se **aplica en la práctica** paso a paso)

#### 1. **Recolección de información**

Se busca información en muchas fuentes como:

| Fuente                    | Ejemplo                                |
| ------------------------- | -------------------------------------- |
| Web abierta (Open Source) | Foros, blogs, noticias, redes sociales |
| Dark web                  | Foros de hackers, mercados ilegales    |
| Sistemas internos         | Logs de red, correos sospechosos       |
| Inteligencia compartida   | Alertas de otros equipos de seguridad  |

#### 2. **Análisis**

Se clasifica y analiza la información para responder preguntas como:

- ¿Quién es el atacante?
- ¿Qué quiere lograr?
- ¿Qué herramientas usa?
- ¿Cómo lo hace?
- ¿Qué tan peligroso es?

#### 3. **Correlación**

Se conectan datos entre sí para identificar patrones.

📌 Ejemplo: Un archivo malicioso + una dirección IP + una campaña en redes puede ser parte de un ataque planeado.

#### 4. **Toma de decisiones**

Con esa información, se decide:

- Bloquear una IP sospechosa
- Parchear un sistema vulnerable
- Alertar al personal de un ataque dirigido
- Reforzar controles en ciertas áreas

---

### 🔍 Tipos de Ciberinteligencia

| Tipo            | ¿Qué hace?                                        | Ejemplo simple                                                |
| --------------- | ------------------------------------------------- | ------------------------------------------------------------- |
| **Táctica**     | Detecta herramientas o técnicas del atacante      | Saber que un malware usa macros de Word                       |
| **Operacional** | Muestra actividades específicas del atacante      | Detectar un ataque de phishing en curso                       |
| **Estratégica** | Informa a directivos sobre riesgos a largo plazo  | Informar que hay una campaña contra bancos de tu país         |
| **Técnica**     | Analiza indicadores concretos (IP, hash, dominio) | Detectar que cierto hash corresponde a un ransomware conocido |

---

### 🧰 Herramientas comunes de Ciberinteligencia

| Herramienta          | ¿Para qué sirve?                            |
| -------------------- | ------------------------------------------- |
| **Maltego**          | Analiza relaciones entre datos              |
| **Shodan**           | Escanea dispositivos conectados a Internet  |
| **VirusTotal**       | Analiza archivos y URLs sospechosas         |
| **TheHive + Cortex** | Gestión de incidentes y análisis automático |
| **MISP**             | Plataforma para compartir inteligencia      |

---

### 📦 Ejemplo fácil de entender (mini historia)

#### 🎬 Caso: Empresa “SegurTech”

🔍 La analista de ciberinteligencia, Laura, descubre en un foro de la dark web que se está vendiendo una base de datos con correos corporativos de empresas del sector salud.

- Laura ve que hay menciones de correos con dominio @segurtech.com.
- Usando herramientas, encuentra que esos correos están siendo usados para enviar **phishing** con archivos infectados.
- Analiza el malware y descubre que se conecta con una IP en Rusia.
- Informa al equipo de IT para bloquear esa IP y reforzar filtros de correos.

📌 Gracias a eso, **previenen un ataque dirigido** y evitan una posible filtración de datos médicos.

---

### 🧠 ¿Cómo aprender o prepararse en Ciberinteligencia?

#### 📘 Conocimientos básicos necesarios:

- Fundamentos de ciberseguridad (redes, malware, sistemas)
- OSINT (Open Source Intelligence)
- Análisis de indicadores (hashes, IPs, dominios)
- Técnicas de ataque comunes (MITRE ATT\&CK, TTPs)

#### 🧰 Herramientas que puedes instalar:

- Kali Linux (con herramientas como recon-ng, maltego)
- MISP (plataforma colaborativa)
- TheHarvester (recolección de correos e info pública)
- SpiderFoot (automatización de OSINT)

#### 📚 Cursos recomendados:

- "Cyber Threat Intelligence" en plataformas como:

  - TryHackMe
  - Udemy
  - Cybrary
  - Coursera

---

### 🧩 Ejemplo completo y práctico: “Pedro, analista de Ciberinteligencia”

#### 🔹 Contexto:

Pedro trabaja para una entidad bancaria. Un día, nota que hay un aumento en los intentos de acceso no autorizado a cuentas de clientes.

#### 🔹 Paso a paso:

1. **Recolección**

   - Usa OSINT para buscar si se está compartiendo información del banco en foros.
   - Encuentra que hay campañas de phishing dirigidas al banco.

2. **Análisis**

   - Identifica correos falsos que simulan ser del banco.
   - Analiza el malware adjunto: roba credenciales.

3. **Correlación**

   - Encuentra que varias IPs están enviando los correos y están en listas negras.

4. **Acción**

   - Envía alertas al equipo técnico.
   - Bloquean IPs y filtran palabras clave en los correos.
   - Notifican a los clientes y actualizan la campaña educativa de seguridad.

#### ✅ Resultado:

El banco **evita una filtración de datos** y refuerza su postura de seguridad proactiva gracias a la **ciberinteligencia**.

---

### ✅ Resumen rápido

| Concepto            | Explicación breve                                |
| ------------------- | ------------------------------------------------ |
| Ciberinteligencia   | Recoger y analizar info sobre amenazas           |
| Finalidad           | Prevenir, detectar, entender y responder ataques |
| Tipos               | Táctica, técnica, operacional, estratégica       |
| Herramientas        | Maltego, VirusTotal, MISP, TheHarvester          |
| Aplicación práctica | Recolectar → Analizar → Correlacionar → Actuar   |

---

[🔼](#índice)

---

## **717. Malware**

![Malware](../img/7_Ciberseguridad_Profesional/Malware.webp "Malware")

### 🦠 ¿Qué es el **Malware**?

**Malware** es la abreviatura de **"Malicious Software"**, es decir, **software malicioso**.

📌 Es cualquier programa o archivo diseñado para **dañar**, **espiar**, **robar información** o **controlar** un sistema sin el consentimiento del usuario.

> 🔐 En otras palabras, es como un "virus" digital que entra a tu computadora o celular sin permiso para hacer algo malo.

---

### 🔍 ¿Qué puede hacer el Malware?

- Robar contraseñas y datos bancarios
- Destruir archivos
- Tomar el control del equipo
- Espiar lo que haces (por la cámara o el teclado)
- Extorsionar a cambio de dinero (como con ransomware)

---

### 🧩 Tipos de Malware (con ejemplos sencillos)

| Tipo de malware   | ¿Qué hace?                                                        | Ejemplo fácil                                             |
| ----------------- | ----------------------------------------------------------------- | --------------------------------------------------------- |
| **Virus**         | Se copia y propaga a otros archivos. Se activa al ejecutarlo.     | Como una gripe: si abres el archivo, se contagia          |
| **Gusano (worm)** | Se propaga solo por la red sin intervención del usuario.          | Como un mosquito que vuela de una PC a otra               |
| **Troyano**       | Se esconde dentro de un programa aparentemente útil o inofensivo. | Como un caballo de Troya moderno                          |
| **Spyware**       | Espía lo que haces y lo envía a un atacante.                      | Como alguien mirando por encima de tu hombro              |
| **Adware**        | Muestra anuncios no deseados y puede rastrear tu actividad.       | Como ventanas emergentes constantes con publicidad falsa  |
| **Ransomware**    | Bloquea tus archivos y pide dinero para desbloquearlos.           | Como un secuestrador de tus fotos y documentos            |
| **Rootkit**       | Da acceso oculto a tu sistema al atacante.                        | Como si alguien se metiera en tu casa y tú no lo supieras |
| **Keylogger**     | Registra lo que escribes en el teclado.                           | Como un espía que anota todo lo que escribes              |

---

### 🛠️ ¿Cómo se **instala** el malware en un equipo? (métodos de infección)

Aunque no se "instala" como un programa normal, el malware se **infiltra** en el sistema usando estos métodos:

#### 1. 📩 **Correos electrónicos con archivos adjuntos**

- Ejemplo: Te llega un correo diciendo "Factura pendiente", abres el archivo, ¡bam! malware instalado.

#### 2. 🌐 **Descargas falsas de programas**

- Descargas un programa pirata o crackeado, pero viene con troyano.

#### 3. 🖱️ **Enlaces maliciosos (phishing)**

- Haces clic en un enlace que parece legítimo, pero te lleva a un sitio que te descarga malware.

#### 4. 💿 **Dispositivos infectados (USB, discos)**

- Conectas una memoria USB contaminada y el gusano se instala automáticamente.

#### 5. ⚠️ **Explotación de vulnerabilidades**

- El malware aprovecha fallos de seguridad en Windows, navegadores o software desactualizado.

---

### 🛡️ ¿Cómo detectar y eliminar malware?

#### ✅ Síntomas comunes:

- La PC va más lenta sin razón
- Se abren ventanas solas
- Se cambió tu página de inicio en el navegador
- Tus archivos están cifrados o desaparecieron
- El antivirus está desactivado

#### 🔧 Herramientas para detectar y eliminar malware:

| Herramienta                | Función                         |
| -------------------------- | ------------------------------- |
| **Windows Defender**       | Antimalware gratuito de Windows |
| **Malwarebytes**           | Escaneo profundo antimalware    |
| **Kaspersky, Bitdefender** | Antivirus profesionales         |
| **HijackThis, AdwCleaner** | Limpieza de adware y spyware    |

---

### 🧪 ¿Cómo prevenir malware?

| Acción preventiva                     | Ejemplo simple                                  |
| ------------------------------------- | ----------------------------------------------- |
| No abrir archivos sospechosos         | “Factura urgente.zip” de alguien que no conoces |
| Tener un antivirus actualizado        | Windows Defender o Malwarebytes                 |
| No descargar software pirata          | Nada de “Photoshop full crack” de sitios raros  |
| Mantener todo actualizado             | Windows, Chrome, Java, etc.                     |
| Usar autenticación en dos pasos (2FA) | Aunque te roben la contraseña, no podrán entrar |

---

### 🧩 Ejemplo completo práctico: "Luis y el ransomware"

#### 🎬 Historia realista

**Luis** es diseñador gráfico. Un día, recibe un correo que dice:

> “Tu cuenta de Dropbox será suspendida. Descarga este archivo para conservar tus datos”.

Luis lo descarga. El archivo es un PDF… pero no lo abre nada. Pasa una hora y de repente:

- Todas sus carpetas están cifradas.
- Aparece una nota: “Tus archivos han sido encriptados. Paga 400 USD en Bitcoin para recuperarlos”.

🔍 Luis fue víctima de **ransomware**, un tipo de malware.

#### 🔎 ¿Qué ocurrió exactamente?

1. **Tipo de malware**: Ransomware
2. **Método de instalación**: Phishing por correo con archivo malicioso
3. **Consecuencias**:

   - Archivos personales cifrados
   - Pérdida de trabajos del último mes
   - Posible filtración de datos

#### 🛠️ ¿Cómo lo resolvió?

- Desconectó el equipo de Internet inmediatamente
- Usó una copia de seguridad que tenía en disco externo
- Instaló Malwarebytes y eliminó los rastros del ransomware
- Aprendió a verificar la dirección de los correos y a no descargar nada dudoso

---

### ✅ Resumen Final

| Concepto             | Descripción corta                          |
| -------------------- | ------------------------------------------ |
| Malware              | Software malicioso                         |
| Tipos                | Virus, troyano, ransomware, spyware, etc.  |
| Métodos de infección | Correo, enlaces, descargas, USB            |
| Prevención           | Antivirus, no abrir correos raros, backups |
| Ejemplo              | Ransomware en correo falso de Dropbox      |

---

[🔼](#índice)

---

## **718. Criptografía y esteganografía**

### 📘 ¿Qué es la **Criptografía**?

La **criptografía** es la **ciencia de proteger la información** transformándola para que **solo las personas autorizadas puedan entenderla**.

> Es como escribir en código secreto: solo el que tenga la clave puede leer el mensaje.

#### 🎯 Objetivo principal:

- Proteger la **confidencialidad**, **integridad** y **autenticidad** de la información.

---

#### 🔑 Tipos de criptografía (fáciles de entender)

| Tipo           | ¿Cómo funciona?                                                     | Ejemplo simple                                                                     |
| -------------- | ------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| **Simétrica**  | Usa **una sola clave** para cifrar y descifrar                      | Como una caja fuerte con una única llave                                           |
| **Asimétrica** | Usa **dos claves**: una pública para cifrar y una privada para leer | Como un buzón: cualquiera puede meter cartas, solo tú tienes la llave para abrirlo |
| **Hashing**    | Convierte datos en una “huella digital” irreversible                | Como un resumen único que no se puede invertir                                     |

---

#### 🔐 Ejemplo real de criptografía:

- Envías un correo cifrado con la clave “123”.
- Solo la persona que tiene “123” puede descifrarlo.
- Si alguien lo intercepta, verá solo letras y símbolos sin sentido.

---

### 🧬 ¿Qué es la **Esteganografía**?

La **esteganografía** es el arte de **esconder información dentro de otros archivos** (imágenes, audios, videos), sin que nadie note que hay algo oculto.

> No cambia el mensaje, sino que **oculta su existencia**.

📌 Es como **esconder un mensaje dentro de una pintura o una canción**, sin que nadie sospeche.

---

#### 🎯 Objetivo principal:

- **Disimular que hay un mensaje oculto**, para que nadie lo detecte.

---

#### 🖼️ Ejemplo fácil de entender:

- Tomas una imagen normal (un gatito 🐱).
- Insertas un texto secreto dentro de los **pixeles invisibles** (cambias ligeramente los colores).
- La imagen sigue viéndose igual, pero si usas una herramienta especial, puedes revelar el mensaje oculto.

---

### 🛠️ ¿Cómo se “instala” o aplica en la vida real?

#### 🔧 CRIPTOGRAFÍA: ¿Cómo se usa en la práctica?

##### ✅ Ejemplo básico: Cifrar texto con una contraseña

1. Escribes un mensaje: "Te espero a las 10"
2. Usas un programa o script para cifrarlo con una clave: "gato123"
3. El mensaje se convierte en algo como: `9f3a#@!zX92w3`
4. Solo quien tenga la clave "gato123" puede descifrarlo

##### 🔧 Herramientas comunes:

- **OpenSSL** (línea de comandos)
- **VeraCrypt** (cifrado de discos)
- **GPG** (correo seguro)
- **Cryptomator** (cifrado de archivos en la nube)

---

#### 🔧 ESTEGANOGRAFÍA: ¿Cómo se usa en la práctica?

##### ✅ Ejemplo básico: Ocultar texto en una imagen

1. Tienes una imagen JPG de una flor 🌸
2. Escribes el mensaje secreto: "El código es 12345"
3. Usas un programa para ocultar el mensaje dentro de la imagen (como **Steghide** o **SilentEye**)
4. La imagen sigue igual, pero ahora **contiene el mensaje oculto**
5. La otra persona usa el mismo programa y una clave para extraer el texto

##### 🔧 Herramientas comunes:

- **Steghide** (oculta texto en imágenes/audio)
- **SilentEye** (interfaz gráfica para ocultar datos)
- **OpenStego** (fácil de usar)
- **zsteg** (para análisis en imágenes PNG)

---

### 🧠 Diferencias clave: Criptografía vs Esteganografía

| Característica                  | Criptografía                | Esteganografía                           |
| ------------------------------- | --------------------------- | ---------------------------------------- |
| Protege el contenido            | ✔️ Sí                       | ❌ No (oculta, pero no cifra)            |
| Oculta el mensaje               | ❌ No                       | ✔️ Sí                                    |
| Es visible que hay algo cifrado | ✔️ Sí                       | ❌ No (parece una imagen o audio normal) |
| Se usa para                     | Seguridad de la información | Ocultamiento de información              |

🔐 **Puedes combinarlas**: primero cifras el mensaje y luego lo ocultas.

---

### 🧩 Ejemplo completo práctico: "Carla, agente encubierta"

#### 🔹 Escenario:

Carla necesita enviar información secreta sobre una operación confidencial a su jefe, sin que nadie se entere.

#### 🔹 Paso 1: **Cifrado**

- Carla escribe el mensaje: "Entrega el paquete a las 9 PM"
- Usa GPG para cifrarlo con una clave pública
- Obtiene un texto cifrado como: `QW#@RWEZx8!!....`

#### 🔹 Paso 2: **Esteganografía**

- Toma una foto común (una pizza 🍕)
- Usa Steghide para **ocultar el mensaje cifrado** dentro de la imagen
- La imagen se ve normal, sin cambios

#### 🔹 Paso 3: **Envío**

- Carla sube la imagen a una red social o la envía por correo
- El jefe descarga la imagen y sabe que hay algo oculto
- Usa la clave privada + Steghide para revelar el mensaje cifrado
- Finalmente, lo descifra con GPG

✅ **Resultado:** Nadie sospecha nada. La imagen parece inocente, pero contiene una operación secreta cifrada y oculta.

---

### ✅ Resumen Final

| Término                | ¿Qué hace?                         | Ejemplo fácil                           |
| ---------------------- | ---------------------------------- | --------------------------------------- |
| **Criptografía**       | Protege la información con claves  | Como un candado digital                 |
| **Esteganografía**     | Oculta la existencia del mensaje   | Como un mensaje escondido en una foto   |
| **Cifrado simétrico**  | Usa una sola clave                 | Como una caja con una sola llave        |
| **Cifrado asimétrico** | Usa dos claves (pública y privada) | Como un buzón público con llave privada |
| **Herramientas**       | GPG, OpenSSL, Steghide, SilentEye  | Puedes usarlas en Windows, Linux o Mac  |

---

[🔼](#índice)

---

## **719. Código seguro**

### 🧠 ¿Qué es el **Código Seguro**?

**Código seguro** es escribir programas o aplicaciones de forma que sean **resistentes a ataques informáticos**.

Es una forma de **programar pensando en la seguridad desde el inicio**, para que el software no tenga **vulnerabilidades** que un atacante pueda aprovechar.

> 🔐 En resumen: **es escribir código que no solo funcione bien, sino que también sea difícil de hackear.**

---

### 🛠️ ¿Por qué es importante el código seguro?

- Protege **datos sensibles** (contraseñas, tarjetas, usuarios)
- Evita **ataques cibernéticos** (como inyecciones, robo de sesión)
- Reduce **costos y problemas legales**
- Mejora la **confianza** de los usuarios

---

### 🧱 Principios del código seguro (con ejemplos sencillos)

Aquí van los errores comunes que debemos evitar, y cómo hacer las cosas bien:

---

#### 1. **Validación de entradas**

> No confiar nunca en lo que el usuario escribe.

**❌ Inseguro:**

```python
username = input("Nombre de usuario: ")
print("Hola " + username)
```

Si el usuario escribe: `Robert'); DROP TABLE users;--`
👉 El sistema puede sufrir **inyección de SQL** si esa entrada se usa en una consulta.

**✅ Seguro:**

```python
import re

username = input("Nombre de usuario: ")
if re.match("^[a-zA-Z0-9_]+$", username):
    print("Hola " + username)
else:
    print("Nombre no válido")
```

---

#### 2. **No mostrar errores internos al usuario**

**❌ Inseguro:**

```python
try:
    do_something()
except Exception as e:
    print(e)  # Muestra todo el error
```

Esto le da al atacante **información del sistema**.

**✅ Seguro:**

```python
try:
    do_something()
except Exception:
    print("Ocurrió un error. Intenta más tarde.")
    log_error_interno()  # Lo registra sin mostrarlo
```

---

#### 3. **Cifrado de contraseñas**

Nunca guardes contraseñas en texto plano.

**❌ Inseguro:**

```python
# Guardar la contraseña directamente
contraseña = "miclave123"
guardar(contraseña)
```

**✅ Seguro:**

```python
import bcrypt

contraseña = b"miclave123"
hashed = bcrypt.hashpw(contraseña, bcrypt.gensalt())
guardar(hashed)
```

---

#### 4. **Uso correcto de permisos y autenticación**

Nunca confíes en datos enviados por el cliente (navegador).

**❌ Inseguro (JavaScript del lado del cliente):**

```js
if (user_is_admin) {
  // mostrar botón de eliminar
}
```

El usuario puede modificar `user_is_admin` y ver cosas que no debería.

**✅ Seguro (verificación en el servidor):**

```python
if usuario.rol == "admin":
    mostrar_boton_eliminar()
```

---

#### 5. **Actualizar librerías y dependencias**

No usar librerías viejas con vulnerabilidades conocidas.

**✅ Usa herramientas como:**

- **npm audit** (Node.js)
- **pip-audit** (Python)
- **OWASP Dependency-Check**

---

### 💻 ¿Cómo se “instala” el código seguro?

(Es decir, cómo se **aplica** paso a paso en el desarrollo real)

1. 🏗️ **Diseña pensando en seguridad**

   - Usa roles de usuario, control de acceso, manejo de errores.
   - Sigue principios de "mínimo privilegio".

2. ✍️ **Escribe código seguro desde el inicio**

   - Valida todo, evita accesos inseguros, y protege datos.

3. 🔍 **Revisa el código (Code Review)**

   - Pide que otro desarrollador revise tu código, o usa herramientas automáticas (SAST).

4. 🧪 **Haz pruebas de seguridad**

   - Escanea con herramientas como **SonarQube**, **Bandit**, **Checkmarx** o **OWASP ZAP**.

5. 📚 **Aprende de estándares y guías**

   - **OWASP Top 10**: lista de los errores más comunes en seguridad web.
   - **CERT Coding Standards**

---

### 🧩 Ejemplo completo y realista: Código inseguro vs código seguro

#### 🎬 Caso: Formulario de login en una página web (Python + SQLite)

---

#### ❌ Código inseguro:

```python
import sqlite3

usuario = input("Usuario: ")
clave = input("Contraseña: ")

conn = sqlite3.connect("usuarios.db")
cursor = conn.cursor()

query = "SELECT * FROM usuarios WHERE nombre = '%s' AND clave = '%s'" % (usuario, clave)
cursor.execute(query)
datos = cursor.fetchone()

if datos:
    print("Bienvenido")
else:
    print("Acceso denegado")
```

🔴 Problemas:

- **Inyección SQL** posible si el usuario escribe algo como:
  `' OR '1'='1` como contraseña.
- Contraseña sin cifrar.
- No hay validación ni sanitización.

---

#### ✅ Código seguro:

```python
import sqlite3
import bcrypt

usuario = input("Usuario: ")
clave = input("Contraseña: ")

conn = sqlite3.connect("usuarios.db")
cursor = conn.cursor()

# Consulta segura con parámetros
cursor.execute("SELECT clave FROM usuarios WHERE nombre = ?", (usuario,))
datos = cursor.fetchone()

if datos and bcrypt.checkpw(clave.encode(), datos[0]):
    print("Bienvenido")
else:
    print("Acceso denegado")
```

🟢 Mejoras:

- Consulta preparada evita **inyección SQL**.
- La contraseña está **cifrada** con bcrypt.
- Entrada del usuario es tratada con cuidado.

---

### ✅ Resumen final

| Concepto clave          | ¿Qué significa?                                        |
| ----------------------- | ------------------------------------------------------ |
| Código seguro           | Programar sin dejar puertas abiertas a atacantes       |
| Validación de entradas  | Nunca confiar en lo que el usuario envía               |
| Cifrado de contraseñas  | Usar algoritmos como bcrypt, nunca guardar texto plano |
| Inyecciones SQL         | Evitarlas con consultas preparadas                     |
| Revisiones de seguridad | Hacer pruebas automáticas y manuales                   |
| OWASP Top 10            | Lista de los errores más comunes que debes evitar      |

---

[🔼](#índice)

---

## **720. Pentesting**

### 🕵️‍♂️ ¿Qué es el Pentesting?

**Pentesting** (también llamado **penetration testing** o prueba de penetración) es un **ataque ético y controlado** contra un sistema informático, red o aplicación para **encontrar y corregir vulnerabilidades antes de que lo hagan los hackers maliciosos**.

> 🔐 Es como contratar a un ladrón experto para que intente entrar a tu casa y te diga por dónde lo logró, para que tú refuerces esas puertas o ventanas.

---

### 🎯 Objetivo del Pentesting

- **Identificar fallos de seguridad**
- **Comprobar qué tan vulnerables** son los sistemas
- **Dar soluciones** para corregir esas vulnerabilidades
- **Cumplir con normativas** (como PCI-DSS, ISO 27001)

---

### 🔍 Tipos de Pentesting (con ejemplos fáciles)

| Tipo de pentest        | ¿Qué se prueba?                                | Ejemplo fácil                                  |
| ---------------------- | ---------------------------------------------- | ---------------------------------------------- |
| **Externo**            | Sistemas expuestos a internet (web, firewalls) | Atacar una página web desde afuera             |
| **Interno**            | Red interna, como si un empleado atacara       | Simular que un trabajador hackea la red        |
| **Web**                | Aplicaciones web (formulario, login, APIs)     | Buscar fallos como inyección SQL, XSS          |
| **Móvil**              | Apps en Android/iOS                            | Analizar cómo guardan datos, conexiones        |
| **Social Engineering** | Engañar personas (phishing, suplantación)      | Enviar correos falsos para obtener contraseñas |

---

### ⚙️ ¿Cómo se “instala” o se prepara un Pentesting?

Cuando decimos "instalar", en este contexto, significa **preparar el entorno y herramientas** para realizar el test de penetración.

---

#### 🛠️ Herramientas comunes para Pentesting

| Herramienta    | ¿Para qué sirve?                              |
| -------------- | --------------------------------------------- |
| **Kali Linux** | Sistema operativo especializado en Pentesting |
| **Metasploit** | Framework para explotar vulnerabilidades      |
| **Nmap**       | Escaneo de puertos y servicios                |
| **Burp Suite** | Pruebas a aplicaciones web (muy potente)      |
| **Nikto**      | Escaneo de servidores web                     |
| **Hydra**      | Ataques de fuerza bruta (contraseñas)         |
| **Wireshark**  | Analizar tráfico de red                       |

---

#### 📦 ¿Cómo instalar un entorno de Pentesting?

##### Opción 1: Instalar **Kali Linux** (la forma más común)

1. ✅ Descargar Kali desde:
   [https://www.kali.org/get-kali/](https://www.kali.org/get-kali/)
2. Instalarlo como:

   - Máquina virtual (con VirtualBox o VMware)
   - Sistema principal
   - WSL en Windows (con algunas limitaciones)

3. Iniciar Kali y usar herramientas ya preinstaladas

##### Opción 2: Instalar herramientas individuales en tu sistema

Si usas Ubuntu o Debian:

```bash
sudo apt update
sudo apt install nmap burpsuite hydra wireshark nikto
```

---

### 🧪 Etapas de un Pentesting (paso a paso con explicación)

| Etapa                   | ¿Qué se hace?                                | Ejemplo fácil                        |
| ----------------------- | -------------------------------------------- | ------------------------------------ |
| **1. Reconocimiento**   | Buscar información del objetivo              | IP, tecnologías, puertos abiertos    |
| **2. Escaneo**          | Identificar servicios y versiones            | Saber si usan Apache, MySQL, etc.    |
| **3. Enumeración**      | Recolectar usuarios, rutas, vulnerabilidades | Rutas ocultas, formularios inseguros |
| **4. Explotación**      | Usar una vulnerabilidad para entrar          | Usar SQLi, XSS, fuerza bruta         |
| **5. Post-explotación** | Ver hasta dónde se puede llegar              | Extraer datos, escalar privilegios   |
| **6. Reporte**          | Documentar todo con pruebas y soluciones     | Entregar un informe profesional      |

---

### 📋 Ejemplo completo y fácil de entender: Pentest web básico

#### 🎬 Escenario:

Vas a hacer un pentest a un sitio web llamado `http://ejemplo.com`. Tienes permiso del dueño.

---

#### 🔹 1. Reconocimiento

Buscamos qué hay detrás del sitio:

```bash
whois ejemplo.com
```

Resultado: Dirección IP, servidor DNS, correo admin…

---

#### 🔹 2. Escaneo con Nmap

```bash
nmap -sV -T4 -p- ejemplo.com
```

Resultado:

```
80/tcp   open  http     Apache 2.4.41
443/tcp  open  https    OpenSSL 1.1.1
```

👉 El servidor web está en el puerto 80 y 443

---

#### 🔹 3. Enumeración con Nikto

```bash
nikto -h http://ejemplo.com
```

Resultado:

```
- X-Powered-By: PHP/5.6.40
- Cookie without HttpOnly flag
- Admin panel found: /admin
```

👉 ¡Panel de administración encontrado!

---

#### 🔹 4. Pruebas de login con Hydra

```bash
hydra -l admin -P /usr/share/wordlists/rockyou.txt http-post-form "/admin/login.php:user=^USER^&pass=^PASS^:F=Login failed"
```

Resultado:

```
[80][http-post-form] login: admin   password: admin123
```

⚠️ Acceso conseguido por **fuerza bruta**

---

#### 🔹 5. Explotación

Ingresas al panel `/admin` con `admin:admin123`
Encuentras un **subidor de archivos sin filtros**.
Subes un archivo `.php` con una shell (acceso remoto).

---

#### 🔹 6. Reporte

Creas un documento que incluya:

- Paso a paso de lo que hiciste
- Evidencia (capturas de pantalla)
- Soluciones:

  - Bloquear fuerza bruta
  - Cambiar credenciales
  - Filtrar extensiones de subida
  - Actualizar PHP

---

### ✅ Resumen final

| Concepto             | Explicación sencilla                                 |
| -------------------- | ---------------------------------------------------- |
| **Pentesting**       | Ataque ético para detectar fallos                    |
| **Herramientas**     | Nmap, Burp, Metasploit, Nikto, Hydra                 |
| **Etapas**           | Reconocimiento → Escaneo → Explotación → Reporte     |
| **Requiere permiso** | ⚠️ ¡Siempre! No hagas pruebas sin autorización legal |
| **Entorno común**    | Kali Linux, o tu propio entorno con herramientas     |

---

[🔼](#índice)

---

## **721. Seguridad forense**

### 🧠 ¿Qué es la Seguridad Forense?

La **seguridad forense**, también conocida como **informática forense o análisis forense digital**, es la **disciplina encargada de investigar delitos informáticos** o incidentes de seguridad.

Su objetivo es:

- **Recopilar**, **analizar** y **preservar** evidencias digitales.
- De forma **legal**, **precisa** y que pueda usarse en un juicio si es necesario.

> 🕵️‍♀️ Es como ser un detective digital: buscas pruebas en computadoras, celulares, redes o correos electrónicos para saber qué pasó y cómo ocurrió.

---

### 🎯 ¿Cuándo se usa la informática forense?

- Robo de información o datos
- Accesos no autorizados
- Malware en una empresa
- Suplantación de identidad
- Filtración de documentos confidenciales
- Investigaciones policiales, juicios legales, etc.

---

### 🧪 Objetivos principales

1. **Identificar** lo que pasó (quién, cómo y cuándo)
2. **Preservar** la evidencia sin alterarla
3. **Analizar** dispositivos o sistemas
4. **Documentar** todo el proceso
5. **Presentar** pruebas claras, comprensibles y legales

---

### 📂 Tipos de evidencias digitales (con ejemplos fáciles)

| Tipo de evidencia    | Ejemplo                                            |
| -------------------- | -------------------------------------------------- |
| Archivos             | Documentos borrados, archivos modificados          |
| Registros (logs)     | Accesos, fallos, movimientos en servidores o redes |
| Metadatos            | Fecha de creación/modificación de un archivo       |
| Tráfico de red       | Paquetes sospechosos capturados con Wireshark      |
| Correo electrónico   | E-mails falsificados, spam, phishing               |
| Dispositivos móviles | Chats, fotos, ubicación, historial de apps         |
| Redes sociales       | Comentarios, publicaciones o perfiles falsos       |

---

### 🛠️ Herramientas más usadas en informática forense

| Herramienta          | ¿Para qué sirve?                        |
| -------------------- | --------------------------------------- |
| **Autopsy**          | Análisis completo de discos duros       |
| **FTK Imager**       | Crear y visualizar imágenes forenses    |
| **The Sleuth Kit**   | Examinar sistemas de archivos (CLI)     |
| **Volatility**       | Analizar memoria RAM                    |
| **Wireshark**        | Analizar tráfico de red                 |
| **X-Ways Forensics** | Herramienta profesional de pago         |
| **Magnet AXIOM**     | Forense para celulares y redes sociales |

---

### 💻 ¿Cómo se “instala” o prepara un entorno forense?

Usaremos como ejemplo la herramienta **Autopsy**, que es gratuita, de código abierto y fácil de usar.

---

#### 🔧 Instalación de Autopsy (en Windows o Linux)

1. Ve a:
   👉 [https://www.sleuthkit.org/autopsy/](https://www.sleuthkit.org/autopsy/)
2. Descarga el instalador para tu sistema operativo.
3. Instálalo como cualquier programa.
4. Autopsy ya incluye The Sleuth Kit y otras herramientas.

También puedes usar una distribución forense como:

- **Kali Linux** (ya viene con herramientas forenses)
- **CAINE** (especializada en forense digital)
- **DEFT Linux**

---

### 🧱 Etapas de una investigación forense

| Fase                 | ¿Qué se hace?                                                          |
| -------------------- | ---------------------------------------------------------------------- |
| **1. Adquisición**   | Captura de la evidencia digital (clonar disco, memoria RAM)            |
| **2. Preservación**  | Guardar la evidencia sin modificarla (hash MD5/SHA1)                   |
| **3. Análisis**      | Examinar los datos (archivos ocultos, logs, metadatos, tráfico de red) |
| **4. Documentación** | Escribir cada paso realizado y hallazgos con capturas y tiempos        |
| **5. Presentación**  | Mostrar los resultados con claridad, a veces en tribunales             |

---

### 🔍 Ejemplo fácil de entender: Análisis forense con Autopsy

#### 🎬 Escenario:

Una empresa sospecha que un empleado robó información. Tienen el disco duro de su computadora.

---

#### 🔹 Paso 1: Crear una imagen forense

Con **FTK Imager** (u otra herramienta), creamos una copia exacta (imagen) del disco:

```bash
# Línea de comando o usar la GUI de FTK Imager
```

---

#### 🔹 Paso 2: Abrir la imagen en Autopsy

1. Abrir Autopsy > “New Case”
2. Ingresar nombre del caso: `CasoRoboDatos`
3. Añadir imagen de disco (`.E01`, `.img`, `.dd`)
4. Esperar que Autopsy la analice

---

#### 🔹 Paso 3: Análisis en Autopsy

En el menú:

- Ver archivos borrados ✅
- Revisar historial del navegador 🌐
- Buscar archivos con palabras clave: “contrato”, “oferta”, “USB”
- Ver dispositivos conectados (USBs recientes)
- Revisar correos enviados

👀 Descubrimos:

- Archivos confidenciales copiados al USB
- Envío de correos con adjuntos sospechosos
- Historial de navegación borrado (pero recuperado)

---

#### 🔹 Paso 4: Documentar todo

En el reporte:

- Fecha y hora de análisis
- Pasos realizados
- Evidencias encontradas (archivos, capturas)
- Hashes de integridad (para que no se altere)

---

#### 🔹 Paso 5: Presentar el informe

El informe forense puede ser:

- En PDF
- En tabla con capturas y descripción
- Con conclusiones para recursos humanos o autoridades

---

### ✅ Resumen final

| Concepto               | Explicación clara                                                      |
| ---------------------- | ---------------------------------------------------------------------- |
| **Seguridad Forense**  | Investigar delitos usando evidencias digitales                         |
| **Objetivo**           | Saber qué ocurrió, cómo y quién lo hizo                                |
| **Fases**              | Adquirir → Preservar → Analizar → Documentar → Presentar               |
| **Herramientas clave** | Autopsy, FTK Imager, Sleuth Kit, Volatility, Wireshark                 |
| **Legalidad**          | ⚠️ Debe hacerse respetando la cadena de custodia y leyes de privacidad |

---

[🔼](#índice)

---

## **722. Seguridad en redes**

### 🧠 ¿Qué es la Seguridad en Redes?

La **seguridad en redes** es el conjunto de políticas, herramientas y prácticas que protegen una red informática de accesos no autorizados, uso indebido, fallos o ataques.

> 🧱 Imagina una red como tu casa: la seguridad en redes sería como poner puertas, cerraduras, cámaras y alarmas para proteger todo lo que hay dentro.

---

### 🎯 ¿Qué protege la seguridad en redes?

- **Datos confidenciales** (clientes, contraseñas, documentos)
- **Disponibilidad de servicios** (servidores, internet, aplicaciones)
- **Integridad** de la información (que no sea modificada por intrusos)
- **Accesos no autorizados** (hackers, malware, usuarios internos malintencionados)

---

### 🔍 Principales amenazas en redes

| Amenaza                  | Ejemplo fácil de entender                     |
| ------------------------ | --------------------------------------------- |
| Acceso no autorizado     | Alguien entra al Wi-Fi sin permiso            |
| Ataque DDoS              | Colapsan tu red con tráfico falso             |
| Sniffing (espionaje)     | Alguien lee lo que escribes en redes públicas |
| Man-in-the-Middle (MITM) | Interceptan datos entre tú y una página web   |
| Phishing                 | Te engañan para que entregues tus contraseñas |
| Ransomware               | Virus que encripta la red y pide rescate      |

---

### 🛠️ Herramientas y técnicas comunes de seguridad en redes

| Herramienta/Técnica           | ¿Qué hace?                                          |
| ----------------------------- | --------------------------------------------------- |
| **Firewall**                  | Bloquea o permite tráfico según reglas              |
| **Antivirus/Antimalware**     | Detecta y elimina software malicioso                |
| **VPN**                       | Crea túneles seguros para conectarse a distancia    |
| **IDS/IPS**                   | Detectan y previenen intrusos (ej: Snort, Suricata) |
| **Wireshark**                 | Analiza tráfico de red                              |
| **Segmentación de red**       | Divide la red para que un ataque no afecte todo     |
| **Actualizaciones regulares** | Cierra fallos de seguridad mediante parches         |
| **WPA3 o WPA2**               | Seguridad para redes Wi-Fi (nunca usar WEP)         |

---

### 💻 ¿Cómo se “instala” la seguridad en una red?

Aquí “instalar” significa **configurar medidas y herramientas** para proteger una red. Vamos a ver un enfoque general para una red pequeña (como una oficina o casa).

---

#### 🔧 Requisitos básicos

1. **Router Wi-Fi seguro**
2. **Firewall (en el router o en el equipo)**
3. **Antivirus y actualizaciones activas**
4. **Red segmentada (opcional para empresas)**
5. **Herramientas de monitoreo como Wireshark o IDS**

---

#### 🔒 Configuración paso a paso básica

##### 1. **Cambiar el usuario y contraseña del router**

- Accede a tu router: abre navegador y escribe `192.168.0.1` o `192.168.1.1`
- Cambia la contraseña por una fuerte
- Desactiva el acceso remoto si no es necesario

##### 2. **Activar el firewall del router**

- Busca “Firewall” en la configuración del router y asegúrate de que esté activo

##### 3. **Activar WPA2/WPA3 en Wi-Fi**

- Desactiva WEP (inseguro)
- Usa una clave robusta (mínimo 12 caracteres, con símbolos y mayúsculas)

##### 4. **Instalar un antivirus confiable**

- En cada dispositivo de la red (como Windows Defender, BitDefender, Kaspersky)

##### 5. **Instalar herramientas como Wireshark o Snort**

- Para análisis más avanzados

---

### 🧪 Ejemplo completo y sencillo: Seguridad en red doméstica

#### 🎬 Escenario:

Tienes una red en tu casa con:

- Un router Wi-Fi
- Dos laptops
- Un celular
- Una impresora Wi-Fi

Quieres protegerla de intrusos y malware.

---

#### ✅ Solución paso a paso

1. **Accedes al router** desde tu navegador → `192.168.0.1`
2. **Cambias el nombre de la red (SSID)**: ya no será "TP-Link123", sino "CasaSegura5G"
3. **Activas seguridad WPA3** (o al menos WPA2) y una contraseña fuerte:

   ```
   Clave: MiCasa!2025$
   ```

4. **Desactivas WPS** (puede ser vulnerable)
5. **Creas una red de invitados separada** para visitas, sin acceso a tu red principal
6. **Instalas antivirus** en tus laptops (por ejemplo, Windows Defender actualizado)
7. **Actualizas el firmware del router** desde su panel de control
8. **Instalas Wireshark** en una de las laptops para monitorear tráfico:

   ```bash
   sudo apt install wireshark    # en Linux
   ```

   - Verificas que no haya tráfico sospechoso saliendo a servidores desconocidos

9. **Creas reglas en el firewall del router**:

   - Bloquear conexiones entrantes desde ciertos países o rangos IP
   - Permitir solo ciertos puertos (80, 443, etc.)

---

### 📋 Resultado

Ahora tu red está protegida contra:

- Vecinos que quieran robar Wi-Fi
- Virus o malware que entren desde internet
- Accesos no autorizados a tus dispositivos
- Usuarios invitados que quieran espiar tus archivos

---

### ✅ Resumen final

| Concepto                     | Explicación clara                                                   |
| ---------------------------- | ------------------------------------------------------------------- |
| **Seguridad en redes**       | Protege datos, dispositivos y comunicaciones dentro de una red      |
| **Principales herramientas** | Firewall, antivirus, Wireshark, IDS/IPS, actualizaciones            |
| **Configuración básica**     | Cambiar claves, activar WPA2/WPA3, bloquear puertos, usar antivirus |
| **Ejemplo práctico**         | Protegiste tu red doméstica en menos de 30 minutos                  |

---

[🔼](#índice)

---

## **723. Certificaciones internacionales de ciberseguridad**

### 🧠 ¿Qué son las certificaciones de ciberseguridad?

Son **títulos reconocidos a nivel mundial** que demuestran que una persona tiene conocimientos y habilidades en áreas específicas de **ciberseguridad**.

> 🧾 Es como un diploma oficial que certifica que **sabes proteger sistemas, redes o datos** y que puedes desempeñar ciertos roles en el área de seguridad informática.

---

### 🎯 ¿Para qué sirven?

- **Validan tus conocimientos** ante empleadores
- **Aumentan tus oportunidades laborales** (mejores sueldos, más empleos)
- **Te especializan** en áreas como: hacking ético, análisis forense, gestión de riesgos, protección de redes, etc.
- Te abren puertas en **empresas internacionales**, gobiernos, bancos, etc.

---

### 🌎 Certificaciones más reconocidas (con ejemplos simples)

| Certificación                                     | ¿De qué trata?                          | Nivel             | Ejemplo práctico                               |
| ------------------------------------------------- | --------------------------------------- | ----------------- | ---------------------------------------------- |
| **CompTIA Security+**                             | Fundamentos de ciberseguridad           | Básico/Intermedio | Saber configurar firewalls, entender ataques   |
| **CEH** (Certified Ethical Hacker)                | Hacking ético                           | Intermedio        | Usar herramientas como Nmap, Metasploit        |
| **CISSP**                                         | Gestión de seguridad                    | Avanzado          | Crear políticas de seguridad para empresas     |
| **CISM**                                          | Gestión de riesgos                      | Avanzado          | Manejo de incidentes en grandes organizaciones |
| **OSCP**                                          | Pentesting ofensivo                     | Experto           | Exploits reales, pruebas de penetración        |
| **CHFI** (Computer Hacking Forensic Investigator) | Análisis forense                        | Intermedio        | Investigar ataques y recuperar evidencia       |
| **ISO 27001 Lead Auditor**                        | Seguridad de la información en empresas | Intermedio        | Evaluar si una empresa cumple con normas ISO   |

---

### 🛠️ ¿Cómo se “instalan”? (cómo se obtienen paso a paso)

Estas certificaciones **no se instalan como un programa**, pero sí se **estudian y rinden** como un examen. El proceso general es:

---

#### 🔹 PASO 1: Elegir una certificación

Depende de tu objetivo:

- ¿Quieres empezar? 👉 **CompTIA Security+**
- ¿Te interesa el hacking? 👉 **CEH o OSCP**
- ¿Prefieres gestión? 👉 **CISSP o CISM**
- ¿Te atrae lo forense? 👉 **CHFI**

---

#### 🔹 PASO 2: Estudiar

Puedes estudiar:

- En cursos online (Udemy, Coursera, TryHackMe, Hack The Box)
- En academias certificadas (EC-Council, Offensive Security, ISACA)
- Con libros oficiales y laboratorios virtuales

---

#### 🔹 PASO 3: Registrar el examen

Cada certificación tiene su portal oficial:

- CompTIA: [https://www.comptia.org](https://www.comptia.org)
- CEH: [https://www.eccouncil.org](https://www.eccouncil.org)
- OSCP: [https://www.offensive-security.com](https://www.offensive-security.com)
- CISSP: [https://www.isc2.org](https://www.isc2.org)

💵 _Los exámenes suelen costar entre 200 y 800 USD_, dependiendo del nivel.

---

#### 🔹 PASO 4: Rendir el examen

- Puede ser presencial (en centros autorizados como Pearson VUE)
- O en línea (con vigilancia por webcam)
- Algunos exámenes son teóricos (multiple choice), otros prácticos (laboratorio real)

---

### 👨‍🏫 Ejemplo completo: Obtener la certificación **CompTIA Security+**

#### 🎯 Objetivo: Aprender ciberseguridad desde cero y certificarme con CompTIA Security+

---

#### 🔹 Paso 1: Investigar

Buscas en la web:

👉 “CompTIA Security+”

Descubres que trata temas como:

- Tipos de ataques (malware, phishing)
- Seguridad de redes
- Criptografía básica
- Control de accesos

---

#### 🔹 Paso 2: Prepararte

Usas los siguientes recursos:

- Curso en Udemy: "CompTIA Security+ Complete Guide" (unos 15 USD)
- Libro oficial: "CompTIA Security+ Study Guide"
- Prácticas online: [https://www.tryhackme.com](https://www.tryhackme.com)

Estudias durante 3 meses, 1 hora al día.

---

#### 🔹 Paso 3: Registrarte al examen

1. Vas a [https://www.comptia.org](https://www.comptia.org)
2. Te creas una cuenta
3. Compras el voucher del examen (≈ 370 USD)
4. Eliges si darlo en línea o en un centro Pearson VUE

---

#### 🔹 Paso 4: Dar el examen

- Modalidad online, desde tu casa
- Tienes 90 minutos para responder preguntas de opción múltiple y simulaciones prácticas
- Al terminar, ves tu resultado: **¡Aprobado!**

---

#### 🔹 Paso 5: Obtener tu certificación

- Recibes tu diploma digital
- Lo subes a tu perfil de LinkedIn y CV
- Ahora puedes aplicar a puestos como:

  - Analista SOC nivel 1
  - Técnico de soporte en ciberseguridad
  - Administrador de seguridad de red

---

### 🧾 Tabla comparativa de certificaciones (para elegir según tu perfil)

| Certificación | Nivel    | Ideal para...                      | Modalidad del examen      |
| ------------- | -------- | ---------------------------------- | ------------------------- |
| Security+     | Básico   | Iniciarse en ciberseguridad        | Teórico, multiple choice  |
| CEH           | Medio    | Hacking ético                      | Teórico + práctica (labs) |
| CISSP         | Avanzado | Gestión, arquitectura de seguridad | Teórico (250 preguntas)   |
| OSCP          | Avanzado | Pentester profesional              | 24 h laboratorio real     |
| CHFI          | Medio    | Forense digital                    | Teórico                   |

---

### ✅ Resumen final

| Punto              | Explicación clara                                                |
| ------------------ | ---------------------------------------------------------------- |
| ¿Qué son?          | Certificaciones que validan tus conocimientos en ciberseguridad  |
| ¿Para qué sirven?  | Para crecer profesionalmente y acceder a mejores empleos         |
| ¿Cómo se obtienen? | Estudiando y rindiendo un examen oficial                         |
| ¿Cuál elegir?      | Según tu nivel e intereses (técnico, ofensivo, gestión, forense) |
| Ejemplo práctico   | Estudio y examen paso a paso de **CompTIA Security+**            |

---

[🔼](#índice)

---

## **724. Cómo hacer una carrera en seguridad informática**

### 🧠 ¿Qué es la seguridad informática?

La **seguridad informática (o ciberseguridad)** es el área que se encarga de **proteger los sistemas, redes y datos** contra ataques, accesos no autorizados, fraudes, malware y más.

> 🛡️ Imagínalo como ser un guardia digital que protege la información importante de una empresa, un gobierno, o incluso de ti mismo.

---

### 🎯 ¿Por qué hacer carrera en seguridad informática?

- 🔥 Alta demanda de profesionales
- 💰 Sueldos competitivos
- 🌎 Oportunidades en todo el mundo
- 🧩 Diversas áreas de especialización (hacking ético, forense, defensa, análisis de malware, etc.)

---

### 🧭 Rutas posibles en la carrera de ciberseguridad

La seguridad informática **no es solo para hackers**. Hay muchos caminos que puedes seguir:

| Área                             | ¿Qué hace?                                                  |
| -------------------------------- | ----------------------------------------------------------- |
| 🕵️‍♂️ Hacking Ético (Pentesting)    | Encuentra fallas de seguridad para protegerlas (legalmente) |
| 🔐 Seguridad de redes            | Configura firewalls, VPNs, protege routers                  |
| 🧑‍💼 Gestión de seguridad          | Establece políticas, normas y controla riesgos              |
| 🔍 Análisis forense digital      | Investiga cibercrímenes y rastrea huellas                   |
| 🧠 Ciberinteligencia             | Analiza amenazas futuras y ataques a gran escala            |
| 💻 Desarrollo de software seguro | Programa sin vulnerabilidades                               |

---

### 🛣️ ¿Cómo empezar una carrera en seguridad informática?

Aquí tienes una **ruta clara paso a paso** para iniciar:

---

#### 1. **Aprende las bases de informática**

Antes de proteger sistemas, necesitas saber cómo funcionan.

> ✅ Recomendado:

- Saber usar sistemas operativos (Windows, Linux)
- Aprender redes básicas (IP, puertos, DNS, etc.)
- Conocer fundamentos de programación (Python es ideal)

---

#### 2. **Elige un camino inicial**

Decide si quieres empezar por:

- Red Team (ofensiva: hacking, pentesting)
- Blue Team (defensiva: proteger, monitorear)
- GRC (gestión de riesgos y cumplimiento)

> Ejemplo:
>
> Si te gusta detectar intrusos, elige Blue Team.
>
> Si te apasiona "romper cosas" y aprender cómo entran los atacantes, elige Red Team.

---

#### 3. **Aprende con plataformas prácticas**

| Plataforma       | ¿Para qué sirve?                      |
| ---------------- | ------------------------------------- |
| **TryHackMe**    | Labs de hacking y defensa desde 0     |
| **Hack The Box** | Desafíos avanzados de pentesting      |
| **BlueTeamLabs** | Defensa, análisis forense y monitoreo |
| **OverTheWire**  | Juegos de seguridad en Linux          |

---

#### 4. **Haz cursos y consigue certificaciones**

> 🎓 Comienza con estas:

- **Google Cybersecurity Certificate (Coursera)** – para empezar desde 0
- **CompTIA Security+** – base sólida en todo
- **CEH, OSCP, CISSP, CHFI** – según especialización

---

#### 5. **Crea tu portafolio de seguridad**

> Incluye:

- Informes de pruebas de laboratorio
- Capturas de pantallas de tus ejercicios
- Proyectos como análisis de malware o detección de tráfico sospechoso

🔗 Súbelos a:

- GitHub
- LinkedIn
- Blog personal (¡incluso usando Notion!)

---

#### 6. **Aplica a trabajos de nivel inicial**

> 🧑‍💼 Puestos de entrada:

- Analista SOC (Security Operations Center)
- Técnico de soporte en seguridad
- Junior Pentester
- Intern o becario en ciberseguridad

---

#### 7. **Sigue especializándote y subiendo de nivel**

A medida que ganes experiencia:

| Nivel       | Ejemplo de cargo                          |
| ----------- | ----------------------------------------- |
| Junior      | Analista SOC, Soporte, Técnico            |
| Semi-senior | Pentester, Forense, Analista de riesgos   |
| Senior      | Jefe de seguridad, Arquitecto de red      |
| Experto     | CISO (Chief Information Security Officer) |

---

### 🛠️ Herramientas importantes

| Herramienta    | ¿Para qué sirve?                          |
| -------------- | ----------------------------------------- |
| **Kali Linux** | Sistema para hacking ético                |
| **Wireshark**  | Analiza tráfico de red                    |
| **Nmap**       | Escanea puertos y redes                   |
| **Burp Suite** | Pruebas de seguridad en páginas web       |
| **Splunk**     | Analiza y monitorea eventos de seguridad  |
| **Metasploit** | Plataforma para explotar vulnerabilidades |
| **Autopsy**    | Herramienta de análisis forense           |

---

### 📘 Ejemplo completo: Cómo empezar desde cero (caso real)

#### 🎯 Perfil del usuario:

- Edad: 19 años
- Sin experiencia previa
- Ganas de aprender ciberseguridad y conseguir empleo en 1 año

---

#### 🔹 Paso a paso:

1. **Mes 1 a 2**

   Aprende fundamentos:

   - Curso gratuito: [CS50x de Harvard](https://cs50.harvard.edu/x/)
   - Aprende Linux básico: [OverTheWire](https://overthewire.org)
   - Red básica con \[Cisco Packet Tracer]

2. **Mes 3 a 5**

   Entra a TryHackMe y completa:

   - “Complete Beginner Path”
   - “Pre Security”
   - Toma curso de CompTIA Security+ en Udemy

3. **Mes 6 a 7**

   Crea un blog y portafolio:

   - Publica tus análisis de máquinas
   - Sube capturas, reportes, scripts en GitHub

4. **Mes 8 a 10**

   Toma la certificación CompTIA Security+
   Regístrate y aprueba el examen online

5. **Mes 11 a 12**

   Aplica a puestos como:

   - Analista SOC Jr.
   - Técnico de seguridad
   - Intern en ciberseguridad

---

### ✅ Resumen final

| Etapa                       | Acciones                                       |
| --------------------------- | ---------------------------------------------- |
| Aprender informática básica | Linux, redes, Python                           |
| Elegir un camino            | Red Team, Blue Team o GRC                      |
| Practicar en plataformas    | TryHackMe, Hack The Box, labs virtuales        |
| Obtener certificaciones     | Security+, CEH, OSCP, según tu nivel           |
| Crear un portafolio         | Subir tus reportes, prácticas, investigaciones |
| Aplicar a trabajos          | Empezar como analista o técnico y crecer       |

---

[🔼](#índice)

---

| **Inicio**         | **atrás 5**                                  | **Siguiente 7**                                            |
| ------------------ | -------------------------------------------- | ---------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./7_5_Redes_de_Internet_Profesional.md) | [⏩](./7_7_Seguridad_Informatica_para_Equipos_Tecnicos.md) |
