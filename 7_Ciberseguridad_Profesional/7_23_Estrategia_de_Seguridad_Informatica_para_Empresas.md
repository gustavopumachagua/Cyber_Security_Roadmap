| **Inicio**         | **atrás 22**                                              | **Siguiente 24**                                            |
| ------------------ | --------------------------------------------------------- | ----------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./7_22_Ciberseguridad_y_Privacidad_para_Empresas.md) | [⏩](./7_24_Seguridad_Informatica_para_Equipos_Tecnicos.md) |

---

## **Índice**

| Temario                                                                                                                                        |
| ---------------------------------------------------------------------------------------------------------------------------------------------- |
| [1079. ¿Por qué crear un programa de seguridad de la información?](#1079-por-qué-crear-un-programa-de-seguridad-de-la-información)             |
| [1080. Objetivos del programa de seguridad de la información](#1080-objetivos-del-programa-de-seguridad-de-la-información)                     |
| [1081. Componentes clave de un programa de seguridad de la información](#1081-componentes-clave-de-un-programa-de-seguridad-de-la-información) |
| [1082. Políticas de seguridad](#1082-políticas-de-seguridad)                                                                                   |
| [1083. Respuesta a incidentes](#1083-respuesta-a-incidentes)                                                                                   |
| [1084. Gestión de vulnerabilidades](#1084-gestión-de-vulnerabilidades)                                                                         |
| [1085. ¿Qué se entiende por Riesgo?](#1085-qué-se-entiende-por-riesgo)                                                                         |
| [1086. Gestión del Riesgo](#1086-gestión-del-riesgo)                                                                                           |
| [1087. Evaluación del Riesgo](#1087-evaluación-del-riesgo)                                                                                     |
| [1088. Gestión de Controles](#1088-gestión-de-controles)                                                                                       |
| [1089. Definiciones y términos](#1089-definiciones-y-términos)                                                                                 |
| [1090. Análisis de impacto de negocio](#1090-análisis-de-impacto-de-negocio)                                                                   |
| [1091. Desarrollo o adquisición de software seguro](#1091-desarrollo-o-adquisición-de-software-seguro)                                         |
| [1092. Introducción a OWASP](#1092-introducción-a-owasp)                                                                                       |
| [1093. OWASP Top 10](#1093-owasp-top-10)                                                                                                       |
| [1094. Modelo de Madurez para el Aseguramiento del Software](#1094-modelo-de-madurez-para-el-aseguramiento-del-software)                       |
| [1095. Roles, equipos y modelos de seguridad](#1095-roles-equipos-y-modelos-de-seguridad)                                                      |
| [1096. Pirámide de crecimiento o criterio de contratación](#1096-pirámide-de-crecimiento-o-criterio-de-contratación)                           |
| [1097. La experiencia de Platzi con ISO27001](#1097-la-experiencia-de-platzi-con-iso27001)                                                     |

# **Estrategia de Seguridad Informática para Empresas**

## **1079. ¿Por qué crear un programa de seguridad de la información?**

### 🔐 ¿Por qué crear un Programa de Seguridad de la Información?

Un **programa de seguridad de la información** es un conjunto de **políticas, procedimientos, herramientas y prácticas** que una organización implementa para **proteger su información confidencial, datos de clientes, sistemas tecnológicos y operaciones**.

#### 📌 ¿Para qué sirve?

- **Evitar filtraciones** de datos sensibles
- **Cumplir leyes** como la Ley de Protección de Datos Personales
- **Prevenir ataques** (phishing, ransomware, robo interno, etc.)
- **Proteger la reputación** de la empresa
- **Garantizar continuidad del negocio**

---

### ✅ Ejemplos fáciles de entender

#### 🔧 Caso 1: Negocio sin programa de seguridad

Una veterinaria tiene su base de datos de clientes en Excel sin contraseña. Un trabajador que renuncia copia los datos y los vende.

→ Resultado: Se filtra información personal y pierden la confianza del cliente.

#### 🛡️ Caso 2: Negocio con programa de seguridad

Una clínica dental implementa:

- Contraseñas seguras
- Accesos controlados
- Backups diarios
- Entrenamiento de personal en phishing

→ Resultado: Evita ataques, cumple con regulaciones y protege a sus pacientes.

---

### 🧩 ¿Qué incluye un Programa de Seguridad de la Información?

1. **Política de seguridad**

   Documento que explica qué se protege, por qué y cómo.

2. **Clasificación de información**

   No toda la información es igual. Se clasifica en:

   - Pública
   - Interna
   - Confidencial
   - Crítica

3. **Control de acceso**

   Quien accede a qué y bajo qué condiciones (roles, permisos, contraseñas, MFA).

4. **Gestión de incidentes**

   ¿Qué hacer si hay un ataque? Tener un plan de respuesta.

5. **Capacitación del personal**

   Entrenar al equipo en riesgos cibernéticos, uso de correo, redes Wi-Fi, etc.

6. **Backups y recuperación**

   Cómo se realizan las copias de seguridad y cómo restaurarlas en caso de pérdida.

7. **Auditoría y monitoreo**

   Revisar constantemente si hay anomalías, fallos o mejoras.

---

### 🛠️ ¿Cómo se instala o implementa?

No se instala como un software, sino que se **diseña, documenta e integra** en la organización paso a paso:

#### 🔟 Pasos para implementarlo (fácil)

| Paso | Acción                             | Ejemplo                                                        |
| ---- | ---------------------------------- | -------------------------------------------------------------- |
| 1    | Hacer un inventario de los activos | PCs, correos, bases de datos, CRM                              |
| 2    | Clasificar la información          | Datos internos, confidenciales, financieros                    |
| 3    | Crear una política simple          | Quién accede, cómo se protegen datos, qué pasa ante incidentes |
| 4    | Definir roles y accesos            | El contador accede a facturación, no a marketing               |
| 5    | Usar contraseñas fuertes y MFA     | Todas las cuentas usan autenticación en dos pasos              |
| 6    | Realizar backups automáticos       | Se programa copia diaria a Google Drive/OneDrive               |
| 7    | Entrenar al personal               | Cursos básicos de phishing, redes seguras, uso de dispositivos |
| 8    | Establecer un plan de incidentes   | Si hay ataque, saber a quién llamar y qué hacer                |
| 9    | Monitorizar actividades            | Revisar accesos, conexiones externas, etc.                     |
| 10   | Revisar cada 6 meses               | Auditar y mejorar continuamente                                |

---

### 🧪 Ejemplo completo: PYME que crea su programa de seguridad

#### Empresa: **EcoMarket Perú**, tienda online de productos ecológicos

---

#### 🔍 Problema:

- Cliente denunció que recibió phishing desde una cuenta parecida a EcoMarket.
- Al revisar, usan contraseñas simples, sin backups y no hay control de accesos.

---

#### ✅ Solución: Implementar un programa de seguridad

**1. Política de seguridad básica:**

Se redacta un documento de 2 páginas con normas de seguridad, firmado por todos.

**2. Clasificación de datos:**

- Pedidos: Interno
- Datos de tarjeta: Confidencial
- Productos: Público

**3. Accesos definidos:**

- Solo administradores acceden a datos de tarjeta.
- Vendedores acceden solo a catálogo y pedidos.

**4. Contraseñas y MFA:**

Se implementa **Bitwarden** y **autenticación en dos pasos**.

**5. Backups automáticos:**

- Se configuran con **Dropbox Business**.
- Copias diarias de base de datos y sistema.

**6. Capacitación del equipo:**

Un taller de 2 horas sobre buenas prácticas digitales.

**7. Plan de respuesta a incidentes:**

- Se define una persona responsable.
- Pasos claros en caso de hackeo o filtración.

**8. Monitoreo y revisiones:**

Cada 3 meses se evalúan mejoras y se hace un simulacro de phishing.

---

#### 🎯 Resultado:

- Se reducen los riesgos de ataques
- Los clientes confían más en el sitio
- Se cumple con la ley de protección de datos personales en Perú

---

### 📌 Conclusión

Crear un programa de seguridad **es esencial en cualquier organización, sin importar su tamaño**.

No es algo técnico exclusivo de expertos, sino una **combinación de orden, cultura, herramientas simples y sentido común**.

---

[🔼](#índice)

---

## **1080. Objetivos del programa de seguridad de la información**

### 🎯 ¿Qué son los Objetivos de un Programa de Seguridad de la Información?

Los **objetivos de un programa de seguridad de la información** son **las metas concretas que se quieren lograr** para **proteger los datos**, mantener las operaciones seguras y **reducir los riesgos digitales**.

No se trata solo de evitar ataques, sino de garantizar que **la información sea segura, confiable, privada y disponible** cuando se necesite.

---

### ✅ Principales objetivos (con explicación sencilla y ejemplos)

#### 1. **Confidencialidad**

🔒 Proteger la información para que **solo personas autorizadas** puedan acceder.

**Ejemplo fácil:**

Solo Recursos Humanos debe tener acceso a los sueldos del personal. Nadie más.

**Cómo se implementa:**

- Estableciendo roles y permisos en sistemas
- Cifrando archivos y correos
- Usando contraseñas seguras y doble autenticación (MFA)

---

#### 2. **Integridad**

🧱 Asegurar que la información **no sea alterada sin autorización**, ni por error ni por ataque.

**Ejemplo fácil:**

Si un cliente hace un pedido de S/. 80, que no cambie misteriosamente a S/. 800.

**Cómo se implementa:**

- Usando registros de cambios (logs)
- Validando los datos
- Copias de seguridad para verificar versiones originales

---

#### 3. **Disponibilidad**

📆 Garantizar que los sistemas y la información estén **accesibles cuando se necesiten**.

**Ejemplo fácil:**

Un médico necesita ver el historial clínico de un paciente durante una emergencia.

**Cómo se implementa:**

- Servidores con respaldo eléctrico (UPS)
- Backups frecuentes
- Hosting en la nube con alta disponibilidad (como AWS, Azure, etc.)

---

#### 4. **Cumplimiento legal y normativo**

📜 Cumplir con leyes como la **Ley de Protección de Datos Personales** (Perú) o el **RGPD** (UE).

**Ejemplo fácil:**

Una tienda online debe pedir permiso antes de usar los datos del cliente para enviarle promociones.

**Cómo se implementa:**

- Políticas de privacidad visibles
- Consentimiento explícito para el tratamiento de datos
- Retención segura de la información

---

#### 5. **Reducción de riesgos**

🚨 Identificar, prevenir y mitigar amenazas digitales como phishing, malware, errores humanos, etc.

**Ejemplo fácil:**

Evitar que un empleado caiga en un correo falso que robe credenciales.

**Cómo se implementa:**

- Simulacros de ciberataques
- Capacitación continua
- Evaluación periódica de vulnerabilidades

---

#### 6. **Concientización y cultura de seguridad**

👥 Hacer que todos los colaboradores comprendan su **rol en proteger la información**.

**Ejemplo fácil:**

Enseñar al personal a **no compartir contraseñas** o **dejar computadoras desbloqueadas**.

**Cómo se implementa:**

- Talleres y cursos internos
- Campañas de buenas prácticas
- Carteles visuales y recordatorios en la oficina

---

#### 7. **Respuesta y recuperación ante incidentes**

🧯 Estar preparados para responder rápido ante un ataque, caída de sistema o pérdida de datos.

**Ejemplo fácil:**

Un ransomware ataca los sistemas, pero se restauran en 2 horas gracias a backups y un plan claro.

**Cómo se implementa:**

- Crear un “Plan de Respuesta a Incidentes”
- Designar responsables (Equipo de Ciberseguridad o TI)
- Simular ataques para medir tiempos de respuesta

---

### 🛠️ ¿Cómo se instalan o implementan los objetivos?

Aunque no se "instalan" como un software, se **integran como parte del funcionamiento diario de la empresa** a través de políticas, tecnologías, y comportamiento del personal.

#### Pasos prácticos para implementar estos objetivos:

| Paso | Acción práctica                   | Resultado esperado                                      |
| ---- | --------------------------------- | ------------------------------------------------------- |
| 1    | Crear una política de seguridad   | Define qué proteger y cómo                              |
| 2    | Clasificar la información         | Saber qué datos son confidenciales, críticos o públicos |
| 3    | Configurar accesos                | Solo usuarios autorizados entran a ciertos datos        |
| 4    | Establecer backups y recuperación | Se garantiza disponibilidad e integridad                |
| 5    | Hacer simulacros de ataques       | Se entrena al personal para responder bien              |
| 6    | Capacitar al personal             | Todos cuidan la seguridad desde su rol                  |
| 7    | Revisar y auditar cada 6 meses    | Mejora continua de la seguridad                         |

---

### 🧪 Ejemplo completo: PYME peruana implementando los objetivos

#### Empresa: **"ComidaNatural.pe"** – Delivery de productos orgánicos

#### Problema:

- Perdieron datos de clientes por no hacer copias de seguridad
- Un empleado compartió información por error
- Se enfrentaron a un intento de phishing vía WhatsApp

---

#### Implementación de objetivos del programa de seguridad:

| Objetivo               | Acción tomada                                                                    |
| ---------------------- | -------------------------------------------------------------------------------- |
| Confidencialidad       | Se limitó el acceso a la base de datos a solo 2 personas con doble autenticación |
| Integridad             | Se activaron logs de edición en su sistema web                                   |
| Disponibilidad         | Backup diario en la nube con Google Drive Business                               |
| Cumplimiento           | Se agregó checkbox de consentimiento en el formulario de registro                |
| Reducción de riesgos   | Se instaló antivirus, firewall, y se configuró filtro de spam                    |
| Concientización        | Se hizo una capacitación sobre “cómo detectar phishing”                          |
| Respuesta a incidentes | Se redactó un protocolo: “Qué hacer si detectas un ciberataque”                  |

---

#### Resultado:

- Ya no pierden información importante
- Ningún ataque ha tenido éxito desde que implementaron estas medidas
- Los clientes sienten mayor confianza y la empresa está alineada a las normativas peruanas

---

### 📌 Conclusión

Los objetivos de un programa de seguridad de la información permiten que una organización funcione **confiablemente, con privacidad, estabilidad y cumplimiento legal**. No son difíciles de implementar si se hace paso a paso y se adapta a cada realidad.

---

[🔼](#índice)

---

## **1081. Componentes clave de un programa de seguridad de la información**

### 🧩 ¿Qué es un programa de seguridad de la información?

Un **programa de seguridad de la información** es un **conjunto organizado de políticas, procedimientos, herramientas y prácticas** que busca **proteger la confidencialidad, integridad y disponibilidad de los datos** de una empresa u organización.

Para que funcione, este programa debe tener ciertos **componentes clave**, como si fuera un carro: sin motor, llantas o frenos, no va a avanzar ni estar seguro.

---

### 🔑 Componentes clave de un programa de seguridad de la información

#### 1. **Políticas y Normativas**

📜 Las **reglas escritas** que indican qué se puede hacer y qué no con la información.

**Ejemplo fácil:**

"Está prohibido compartir contraseñas entre compañeros de trabajo."

**Cómo se implementa (instala):**

- Redacta una política de seguridad clara.
- Difúndela en un manual o curso de inducción.
- Haz que todos la firmen.

---

#### 2. **Gestión de Riesgos**

🚨 Identificar qué amenazas podrían afectar la empresa, cómo de graves son y cómo mitigarlas.

**Ejemplo fácil:**

Detectar que los correos de phishing son un riesgo frecuente, y que si alguien cae, se podrían robar datos sensibles.

**Cómo se implementa:**

- Haz una matriz de riesgos: riesgo, impacto, probabilidad.
- Diseña controles para los más críticos.
- Revisa al menos cada 6-12 meses.

---

#### 3. **Control de Acceso**

🔐 Establecer quién puede ver, editar o borrar ciertos datos o sistemas.

**Ejemplo fácil:**

Solo el contador puede modificar los libros contables, pero los jefes pueden verlos.

**Cómo se implementa:**

- Usa roles y permisos en sistemas y aplicaciones.
- Aplica autenticación multifactor (MFA).
- Registra los accesos (logs).

---

#### 4. **Gestión de Activos**

📦 Saber qué dispositivos, software, documentos o bases de datos se tienen, dónde están y cómo se protegen.

**Ejemplo fácil:**

Inventariar laptops, servidores, discos duros, USBs y licencias de software.

**Cómo se implementa:**

- Lleva una hoja o sistema con todos los activos.
- Clasifica los datos según su nivel de sensibilidad (público, confidencial, etc.).
- Define quién es responsable de cada activo.

---

#### 5. **Educación y Concientización del Personal**

🎓 Capacitar a todos en buenas prácticas de seguridad.

**Ejemplo fácil:**

Enseñar al personal a no hacer clic en enlaces sospechosos.

**Cómo se implementa:**

- Cursos trimestrales o semestrales.
- Simulacros de phishing.
- Manuales o carteles visibles en la oficina.

---

#### 6. **Respuesta a Incidentes**

🧯 Tener un plan claro de qué hacer si ocurre un ataque o problema de seguridad.

**Ejemplo fácil:**

Si detectan un ransomware, saber cómo desconectar los equipos, a quién avisar y cómo recuperar la información.

**Cómo se implementa:**

- Crear un plan paso a paso con roles definidos.
- Hacer simulacros una vez al año.
- Registrar y analizar todos los incidentes.

---

#### 7. **Backups y Recuperación**

💾 Hacer copias de seguridad de la información y tener un plan para recuperarla.

**Ejemplo fácil:**

Una tienda hace backup diario de su base de datos para restaurarla en caso de fallo.

**Cómo se implementa:**

- Automatiza backups diarios o semanales.
- Guarda una copia fuera del lugar de trabajo o en la nube.
- Prueba la recuperación de datos periódicamente.

---

#### 8. **Auditoría y Mejora Continua**

🔍 Revisar el programa regularmente para corregir fallos y adaptarlo.

**Ejemplo fácil:**

Cada seis meses se revisa si los controles siguen siendo eficaces y actualizados.

**Cómo se implementa:**

- Auditoría interna o externa.
- Revisar logs, reportes, controles.
- Aplicar mejoras según hallazgos.

---

### 🛠️ ¿Cómo se “instalan” estos componentes?

Aunque no es una instalación como un programa, se implementa **paso a paso** en la organización mediante las siguientes acciones:

| Paso | Acción                                                                                     |
| ---- | ------------------------------------------------------------------------------------------ |
| 1️⃣   | Designar un responsable de seguridad de la información (o equipo)                          |
| 2️⃣   | Crear políticas y procedimientos claros                                                    |
| 3️⃣   | Clasificar la información y activos                                                        |
| 4️⃣   | Configurar accesos y controles                                                             |
| 5️⃣   | Capacitar al personal regularmente                                                         |
| 6️⃣   | Realizar simulacros e instalar herramientas de protección (antivirus, firewall, MFA, etc.) |
| 7️⃣   | Hacer auditorías y mejoras periódicas                                                      |

---

### 🧪 Ejemplo completo: Empresa ficticia "EcoSalud.pe"

**Empresa:** Tienda online de productos saludables en Perú.

**Problema:** Sufrieron un intento de ataque vía phishing, no sabían cómo reaccionar y no tenían backup.

#### Aplicación de los componentes clave:

| Componente             | Acción aplicada en EcoSalud.pe                                                       |
| ---------------------- | ------------------------------------------------------------------------------------ |
| Políticas              | Redactaron y difundieron una política de seguridad que prohíbe compartir contraseñas |
| Gestión de riesgos     | Identificaron phishing y pérdida de datos como riesgos más probables                 |
| Control de acceso      | Solo los jefes y contabilidad acceden a datos financieros                            |
| Gestión de activos     | Hicieron inventario de laptops, celulares y software                                 |
| Concientización        | Capacitaron al equipo sobre cómo detectar correos falsos                             |
| Respuesta a incidentes | Crearon un protocolo: "Qué hacer ante un ataque cibernético"                         |
| Backups                | Activaron copia diaria automática en Google Drive empresarial                        |
| Auditoría              | Revisan políticas y riesgos cada 6 meses                                             |

#### Resultado:

- Ya no han caído en intentos de phishing.
- Recuperaron datos tras un problema con la base de productos.
- Mejoraron su reputación y confianza de clientes.

---

### 📌 Conclusión

Un buen programa de seguridad de la información debe tener estos **componentes clave bien definidos e integrados**. Cada uno cumple una función esencial para **proteger los datos, las personas y la operación de una empresa u organización**.

> 🔐 Implementarlo es una inversión en confianza, continuidad y protección frente a amenazas.

---

[🔼](#índice)

---

## **1082. Políticas de seguridad**

### 🛡️ ¿Qué son las Políticas de Seguridad?

Las **políticas de seguridad de la información** son **documentos formales** que definen **cómo una organización protege su información, sus sistemas y sus usuarios**. Funcionan como las **reglas del juego** en ciberseguridad: todos deben conocerlas, cumplirlas y aplicarlas.

> **Ejemplo fácil:**
>
> Así como en casa tienes reglas como “no abrir la puerta a desconocidos” o “cerrar con llave al salir”, en una empresa hay reglas como “no compartir contraseñas” o “bloquear la computadora al ausentarse”.

---

### 🎯 Objetivos de las políticas de seguridad

- Proteger la **confidencialidad, integridad y disponibilidad** de la información.
- Establecer responsabilidades claras.
- Prevenir incidentes de seguridad (phishing, malware, robo de datos, etc.).
- Garantizar el cumplimiento de leyes y normativas (como la Ley de Protección de Datos en Perú).

---

### 🧱 Tipos comunes de políticas de seguridad

Aquí te muestro algunos ejemplos típicos con explicaciones sencillas:

| Política                         | ¿Qué regula?                                      | Ejemplo sencillo                                 |
| -------------------------------- | ------------------------------------------------- | ------------------------------------------------ |
| Política de contraseñas          | Longitud, complejidad, vencimiento de contraseñas | Mínimo 12 caracteres, cambia cada 3 meses        |
| Política de uso aceptable        | Qué se puede hacer o no con los recursos de TI    | No instalar programas sin permiso                |
| Política de acceso a la red      | Controla quién entra a la red y cómo              | Solo dispositivos autorizados                    |
| Política de backup               | Copias de seguridad y recuperación                | Backup diario automático a la nube               |
| Política de manejo de incidentes | Qué hacer ante un ataque o problema               | Reportar al área TI en menos de 30 minutos       |
| Política de uso de correo        | Cómo usar el correo corporativo                   | No reenviar cadenas ni abrir enlaces sospechosos |
| Política de dispositivos móviles | Uso seguro de smartphones, USBs, tablets          | Encriptar USBs y tener bloqueo de pantalla       |

---

### ⚙️ ¿Cómo se “instalan” o implementan las políticas de seguridad?

Aunque no se instalan como un software, sí se **implementan paso a paso** en una organización. Aquí te dejo cómo hacerlo de forma práctica:

#### 🪜 Paso a paso:

1. **Identificar los activos y riesgos**

   - ¿Qué información necesita protección?
   - ¿Cuáles son las amenazas más comunes? (Ej: phishing, robo de laptops, etc.)

2. **Redactar las políticas**

   - Usa lenguaje claro y directo.
   - Define qué está permitido, qué no, y cuáles son las consecuencias.
   - Ejemplo de título: "Política de Contraseñas Seguras"

3. **Validarlas con dirección o legal**

   - Es importante que los jefes y el área legal las aprueben.

4. **Difundirlas**

   - A través del correo, el onboarding, la intranet o carteles visibles.
   - Idealmente, hacer sesiones de capacitación.

5. **Hacerlas cumplir**

   - A través de supervisión, auditorías, y consecuencias claras en caso de incumplimiento.

6. **Actualizar cada 6 o 12 meses**

   - La tecnología cambia, así que también deben hacerlo las políticas.

---

### 🧪 Ejemplo completo: Política de Contraseñas para una empresa ficticia

---

#### 📄 Documento: Política de Contraseñas Seguras

**Empresa:** EcoSalud.pe

**Aprobada por:** Gerencia de Tecnología

**Versión:** 1.0 – Julio 2025

---

#### 📌 Objetivo

Proteger el acceso a los sistemas informáticos de EcoSalud.pe mediante el uso de contraseñas robustas y seguras.

---

#### 🎯 Alcance

Aplica a todos los empleados, contratistas y proveedores que accedan a sistemas informáticos de la empresa.

---

#### 🔒 Política

1. Las contraseñas deben tener al menos:

   - 12 caracteres
   - 1 mayúscula, 1 minúscula, 1 número y 1 símbolo

2. Está prohibido:

   - Compartir contraseñas con otras personas
   - Usar la misma contraseña en otros servicios (ej: Facebook, Gmail)

3. Las contraseñas deben cambiarse cada 90 días.

4. Se recomienda el uso de un gestor de contraseñas como **Bitwarden** o **1Password**.

5. En caso de sospecha de que tu contraseña fue comprometida, debes:

   - Cambiarla inmediatamente
   - Informar al área de TI

---

#### 👮 Sanciones

El incumplimiento de esta política puede llevar a sanciones disciplinarias y/o suspensión de acceso a los sistemas.

---

#### 🔁 Revisión

Esta política será revisada cada 6 meses por el equipo de seguridad informática.

---

### 🧰 Herramientas para ayudarte a implementar políticas

- **Bitwarden / 1Password / KeePass** → Para políticas de contraseñas.
- **Google Workspace o Microsoft 365** → Para restringir acceso, enviar políticas y notificaciones.
- **Canva / Word / Google Docs** → Para diseñar documentos visuales y claros.
- **Notion / Confluence / Intranet** → Para publicar las políticas en línea.
- **Formularios de Google o Microsoft Forms** → Para hacer que los usuarios firmen digitalmente que han leído la política.

---

### ✅ Conclusión

Las **políticas de seguridad** son la **base de cualquier programa de ciberseguridad**. Ayudan a **prevenir errores humanos**, definir comportamientos aceptables y estar **preparados ante amenazas**.

> 🧠 Recuerda: una política que **nadie conoce ni entiende, es como si no existiera**.

---

[🔼](#índice)

---

## **1083. Respuesta a incidentes**

### 🛡️ ¿Qué es la Respuesta a Incidentes?

La **respuesta a incidentes** es el proceso mediante el cual una organización **detecta, analiza, contiene y recupera** de un ataque cibernético o fallo de seguridad.

> 🎯 **Objetivo**: Minimizar el daño, recuperar operaciones lo antes posible y prevenir que el ataque se repita.

---

### 🧠 Ejemplo fácil de entender

Imagina que alguien entra a tu casa y se roba tu laptop.
Una buena **respuesta a incidentes en tu hogar** sería:

1. **Detectarlo**: Notas que la laptop ya no está.
2. **Contenerlo**: Aseguras la puerta para que no vuelvan a entrar.
3. **Erradicarlo**: Cambias la cerradura.
4. **Recuperarte**: Compras otra laptop y recuperas la información desde tu backup.
5. **Lección aprendida**: Instalas una alarma y refuerzas la seguridad.

En ciberseguridad funciona igual, pero con computadoras, servidores, usuarios y redes.

---

### 🧱 Fases del Ciclo de Respuesta a Incidentes

| Fase                        | ¿Qué se hace?                                                         | Ejemplo claro                                             |
| --------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------- |
| 1. **Preparación**          | Crear políticas, entrenar al personal, instalar software de monitoreo | Simulacros de phishing o firewalls activos                |
| 2. **Identificación**       | Detectar que algo está mal (alertas, antivirus, usuarios reportan)    | Se detecta actividad inusual en una cuenta                |
| 3. **Contención**           | Aislar la amenaza para que no se propague                             | Se desconecta la red del equipo comprometido              |
| 4. **Erradicación**         | Eliminar el malware o acceso no autorizado                            | Se elimina el archivo malicioso y se cambia la contraseña |
| 5. **Recuperación**         | Restaurar sistemas y servicios a su funcionamiento normal             | Se restaura el backup y se vuelve a habilitar el equipo   |
| 6. **Lecciones aprendidas** | Analizar el incidente y actualizar políticas y controles              | Se mejora la política de contraseñas o se instala MFA     |

---

### ⚙️ ¿Cómo se “instala” o implementa un proceso de Respuesta a Incidentes?

No se instala como un programa, pero **sí se implementa como un conjunto de prácticas, roles, herramientas y documentación**.

#### 🪜 Pasos para implementar un Plan de Respuesta a Incidentes (PRI)

1. **Designa un equipo CSIRT (Computer Security Incident Response Team)**

   - Al menos un encargado de seguridad o TI, y enlaces de cada área.

2. **Define roles y responsabilidades**

   - ¿Quién detecta? ¿Quién decide si apagar un servidor? ¿Quién comunica a la gerencia?

3. **Crea un procedimiento documentado**

   - Un documento PDF o físico con qué hacer en cada etapa (puede ser una checklist).

4. **Implementa herramientas de monitoreo**

   - Ej: antivirus con alertas, firewall, SIEM (como Wazuh, Graylog, Splunk).

5. **Capacita al personal**

   - Que todos sepan cómo reportar incidentes.

6. **Haz simulacros**

   - Ataques ficticios de phishing, ransomware, etc.

7. **Revisa y mejora continuamente**

   - Después de un incidente real o simulado.

---

### 🧪 Ejemplo completo paso a paso: Respuesta a incidente de **Phishing**

#### 🔎 Escenario

Un empleado hace clic en un correo falso y entrega sus credenciales en una página que imita Office 365.

---

#### 🛠️ Fase 1: Identificación

- El equipo de TI recibe una alerta de inicio de sesión desde Nigeria.
- Verifican que el usuario **Juan** está en Lima y no viajó.

✅ _Incidente detectado: posible phishing con robo de credenciales._

---

#### 🧯 Fase 2: Contención

- Se **bloquea la cuenta** del usuario temporalmente.
- Se **revoca el token de sesión** en Microsoft 365.
- Se **avisa al equipo de ciberseguridad**.

---

#### 🧹 Fase 3: Erradicación

- Se elimina el acceso del atacante.
- Se analiza si el atacante movió datos.
- Se hace un escaneo de malware por si instaló algo.

---

#### 🔁 Fase 4: Recuperación

- Se restablece la cuenta de Juan con una nueva contraseña.
- Se activa MFA (autenticación de dos factores).
- Se notifica al usuario y a su jefe.

---

#### 🧠 Fase 5: Lecciones aprendidas

- Se revisa por qué Juan no identificó el correo como falso.
- Se hace un taller corto con su área sobre **cómo detectar phishing**.
- Se mejora el filtro de spam y el sistema de alertas.

---

### 🧰 Herramientas útiles para Respuesta a Incidentes

| Herramienta                          | ¿Para qué sirve?                      |
| ------------------------------------ | ------------------------------------- |
| **Wazuh**                            | SIEM libre para detección y respuesta |
| **TheHive**                          | Plataforma de gestión de incidentes   |
| **Graylog**                          | Recolección y análisis de logs        |
| **Cortex**                           | Automatiza acciones de contención     |
| **Google Workspace / Microsoft 365** | Alertas, bloqueo de cuentas           |

---

### 📄 Plantilla básica para documento de Respuesta a Incidentes

```markdown
#### Plan de Respuesta a Incidentes – Empresa XYZ

##### 1. Objetivo

Establecer el proceso para detectar, contener, erradicar y recuperar de incidentes de seguridad informática.

##### 2. Alcance

Todos los sistemas, usuarios y dispositivos de Empresa XYZ.

##### 3. Fases

- Identificación
- Contención
- Erradicación
- Recuperación
- Lecciones aprendidas

##### 4. Equipo CSIRT

- Coordinador: Jefe de TI
- Analista: Especialista de seguridad
- Comunicación: RR.HH. o Legal

##### 5. Procedimiento de Activación

1. Detectar el incidente
2. Escalar a CSIRT
3. Ejecutar contención
4. Notificar a dirección

##### 6. Contacto de Emergencia

- seguridad@empresa.xyz
- Tel. 999-999-999
```

---

### ✅ Conclusión

Un buen plan de **respuesta a incidentes** no solo evita pérdidas económicas o legales, sino que **protege la reputación** y permite que la organización se recupere **rápidamente** ante cualquier amenaza.

> 💡 Una empresa sin plan de respuesta es como un barco sin salvavidas.

---

[🔼](#índice)

---

## **1084. Gestión de vulnerabilidades**

### 🛡️ ¿Qué es la Gestión de Vulnerabilidades?

La **gestión de vulnerabilidades** es un proceso continuo que busca:

- **Identificar**
- **Evaluar**
- **Priorizar**
- **Corregir o mitigar**
  las **vulnerabilidades** (errores de seguridad) presentes en sistemas, redes, aplicaciones y dispositivos.

> ⚠️ Una **vulnerabilidad** es una falla de seguridad que un atacante puede explotar.

---

### 🎯 ¿Por qué es importante?

Porque **ningún sistema es perfecto**. Todos los días aparecen nuevas vulnerabilidades. Si no las gestionas, dejas **puertas abiertas** que pueden ser aprovechadas por **cibercriminales, ransomware o insiders**.

---

### 🔍 Ejemplo fácil de entender

Imagina que tu casa tiene ventanas sin seguro y puertas con la cerradura floja.

- **Gestión de vulnerabilidades** sería hacer una revisión mensual de puertas y ventanas:

  - Ver si alguna se puede abrir fácilmente.
  - Evaluar cuál es más crítica (una da a la calle, otra al patio).
  - Repararlas según el nivel de riesgo.

En el mundo digital:

- Las **ventanas** son puertos abiertos o software sin actualizar.
- Las **cerraduras flojas** son contraseñas débiles o servicios sin parches.

---

### 🔁 Ciclo de Gestión de Vulnerabilidades

| Etapa                           | ¿Qué se hace?                                                             |
| ------------------------------- | ------------------------------------------------------------------------- |
| 1. **Descubrimiento**           | Se escanean los sistemas en busca de vulnerabilidades                     |
| 2. **Análisis y evaluación**    | Se determina la gravedad (CVSS) y el riesgo real para el negocio          |
| 3. **Priorización**             | Se decide qué corregir primero (según criticidad o exposición)            |
| 4. **Remediación o mitigación** | Se aplican parches, configuraciones o se deshabilitan servicios inseguros |
| 5. **Verificación**             | Se vuelve a escanear para comprobar que la vulnerabilidad ya no existe    |
| 6. **Repetir**                  | Es un proceso continuo, no algo que se hace una sola vez                  |

---

### 🛠️ ¿Cómo se instala o implementa la Gestión de Vulnerabilidades?

No se trata de instalar un solo programa, sino de **configurar un proceso completo**, con herramientas y personas involucradas.

#### 📋 Requisitos previos

✅ Tener un inventario de activos: computadoras, servidores, routers, sistemas, aplicaciones.

✅ Contar con permisos de administrador para escanear dispositivos.

✅ Herramientas de escaneo y un equipo responsable (puede ser una sola persona en empresas pequeñas).

---

#### 🧰 Herramientas populares

| Herramienta                   | Tipo                        | ¿Gratis? | Descripción rápida                     |
| ----------------------------- | --------------------------- | -------- | -------------------------------------- |
| **OpenVAS / Greenbone**       | Escaneo de vulnerabilidades | Sí       | Escanea redes y servidores             |
| **Nessus Essentials**         | Escaneo (limitado)          | Sí       | Muy usado en empresas                  |
| **Nmap + scripts NSE**        | Detección manual            | Sí       | Descubre puertos y servicios inseguros |
| **Qualys / Rapid7 / Tenable** | Escaneo corporativo         | No       | Profesionales, con dashboard           |

---

#### 🪜 Pasos para instalar OpenVAS (en Linux)

```bash
# Paso 1: Instala Greenbone Vulnerability Manager (OpenVAS)
sudo apt update && sudo apt install openvas -y

# Paso 2: Configura los feeds (bases de datos de vulnerabilidades)
sudo gvm-setup

# Paso 3: Inicia el servicio
sudo gvm-start

# Paso 4: Accede al dashboard web
# Usualmente http://localhost:9392 o la IP del servidor
```

> En Windows podrías usar herramientas como **Nessus** o una VM con Kali Linux que ya tiene OpenVAS.

---

### 🧪 Ejemplo completo paso a paso: Gestión de vulnerabilidades en una pequeña oficina

#### 📍 Escenario

Tienes una oficina con:

- 5 computadoras con Windows 10
- 1 servidor local
- 1 router

---

#### 🔎 Paso 1: Escaneo de vulnerabilidades

- Usas **Nessus Essentials** en tu laptop conectada a la red.
- Escaneas el rango 192.168.0.1 - 192.168.0.255

**Resultado del escaneo**:

- PC1: Windows sin parchear (vulnerabilidad crítica CVE-2023-21768)
- PC2: Puerto RDP abierto sin protección
- Servidor: Apache 2.4.49 vulnerable a path traversal (CVE-2021-41773)

---

#### ⚖️ Paso 2: Evaluación y priorización

Analizas el riesgo:

| Activo   | Vulnerabilidad                    | Riesgo  | Prioridad |
| -------- | --------------------------------- | ------- | --------- |
| PC1      | Windows sin parches críticos      | Alto    | Alta      |
| PC2      | RDP sin protección ni MFA         | Alto    | Media     |
| Servidor | Apache vulnerable a ataque remoto | Crítico | Muy Alta  |

---

#### 🔧 Paso 3: Remediación

- PC1: Ejecutas `Windows Update` y aplicas parches críticos.
- PC2: Cierras el puerto RDP en el firewall y se activa VPN.
- Servidor: Actualizas Apache a versión segura y desactivas módulos innecesarios.

---

#### ✔️ Paso 4: Verificación

- Vuelves a escanear y verificas que ya no aparecen las vulnerabilidades reportadas.

---

#### 🔄 Paso 5: Documentación y repetición

- Documentas las acciones tomadas.
- Programas el próximo escaneo mensual.

---

### ✅ Buenas prácticas

- 🗓️ Escanea **mensualmente** (mínimo).
- 🧠 Capacita al personal de TI sobre **parcheo y hardening**.
- 🛑 Prioriza **vulnerabilidades críticas** expuestas a internet.
- 🔐 Asegúrate de que tus herramientas estén **actualizadas**.
- 📄 Lleva un **registro histórico** de vulnerabilidades tratadas.

---

##3 🧠 Conclusión

> La **gestión de vulnerabilidades** no se trata de eliminar el 100% de los riesgos, sino de **saber qué arreglar primero** y **reducir al mínimo las puertas abiertas** que un atacante podría usar.

Una empresa o profesional que **ignora sus vulnerabilidades** se vuelve **un blanco fácil**.

---

[🔼](#índice)

---

## **1085. ¿Qué se entiende por Riesgo?**

### 📘 Definición clara

**Riesgo** en ciberseguridad es la **posibilidad de que ocurra un evento que afecte negativamente** a tus sistemas, datos o procesos por una **vulnerabilidad explotada por una amenaza**.

Se resume como:

> 🔥 **Riesgo = Amenaza × Vulnerabilidad × Impacto**

---

#### 🧩 ¿Qué significan esos componentes?

| Concepto           | Definición clara                                                | Ejemplo fácil                        |
| ------------------ | --------------------------------------------------------------- | ------------------------------------ |
| **Amenaza**        | Algo que **puede causar daño** (hackers, malware, error humano) | Hacker intentando entrar a tu red    |
| **Vulnerabilidad** | Una **debilidad** que puede ser aprovechada                     | Contraseña débil                     |
| **Impacto**        | El **daño** si la amenaza tiene éxito                           | Pérdida de datos, dinero, reputación |

---

### 💡 Ejemplo fácil: casa

Imagina tu **casa**.

- **Amenaza**: Ladrón que camina por tu barrio.
- **Vulnerabilidad**: Dejas la puerta abierta.
- **Impacto**: Te roban la TV y la laptop.

👉 **Riesgo** = posibilidad real de que te roben, porque **existe un ladrón, tu puerta está abierta y hay cosas valiosas**.

---

### 🖥️ Ejemplo en ciberseguridad

- **Amenaza**: Un atacante quiere robar credenciales.
- **Vulnerabilidad**: Tu aplicación web no tiene cifrado (usa HTTP).
- **Impacto**: Robo de contraseñas, acceso a datos, daño reputacional.

👉 Hay un **riesgo alto** si no corriges la vulnerabilidad.

---

### ⚖️ ¿Cómo se mide un riesgo?

Muchas organizaciones usan escalas cualitativas o cuantitativas.

Una forma muy usada es:

| Riesgo  | Probabilidad | Impacto      |
| ------- | ------------ | ------------ |
| Bajo    | Baja         | Bajo         |
| Medio   | Alta         | Bajo         |
| Alto    | Alta         | Alto         |
| Crítico | Muy Alta     | Catastrófico |

O mediante **fórmulas** como:

> Riesgo = (Probabilidad de explotación) × (Impacto financiero, legal, operativo)

---

### 🧰 ¿Cómo se "instala" o gestiona el concepto de riesgo?

No se **instala como software**, pero se **implementa** un proceso llamado **gestión de riesgos**. Es parte esencial de la **seguridad de la información**.

---

### 🪜 Pasos para gestionar el riesgo

1. **Identificar activos**: ¿Qué quieres proteger? (servidores, datos, aplicaciones).
2. **Identificar amenazas**: ¿Qué puede atacar esos activos? (malware, phishing, insiders).
3. **Identificar vulnerabilidades**: ¿Qué debilidades existen? (software sin parches, mala configuración).
4. **Evaluar el riesgo**: ¿Qué tan probable es que ocurra y qué tan grave sería?
5. **Tratar el riesgo**:

   - Mitigar (reducir)
   - Aceptar (vivir con él)
   - Transferir (ej. seguros)
   - Eliminar (eliminar el activo o dejar de usar el sistema)

6. **Monitorear y revisar** continuamente.

---

### 🧪 Ejemplo completo y realista

#### 📍 Escenario

Gustavo tiene un sitio web que recopila correos para enviar boletines y está en producción.

---

#### 🔎 Análisis de Riesgo

| Activo        | Amenaza       | Vulnerabilidad             | Impacto                         | Riesgo  |
| ------------- | ------------- | -------------------------- | ------------------------------- | ------- |
| Base de datos | Cibercriminal | Contraseña débil           | Robo de correos → multas (GDPR) | Alto    |
| Sitio web     | Ataques DDoS  | Sin protección de firewall | Sitio caído                     | Medio   |
| Formularios   | Inyección SQL | No validación de entrada   | Robo de datos                   | Crítico |

---

#### ✅ Gestión del riesgo

| Riesgo           | Acción tomada                                   |
| ---------------- | ----------------------------------------------- |
| Contraseña débil | Usar contraseña robusta y gestor de contraseñas |
| Sin firewall     | Implementar Cloudflare y reglas de WAF          |
| Inyección SQL    | Validar entradas, usar ORM                      |

---

#### 📈 Resultado

Después de aplicar medidas, los riesgos se **reducen significativamente**.

---

### ✅ Conclusiones

- **Riesgo no significa que algo malo ya pasó**, sino que **podría pasar**.
- Se gestiona, no se elimina del todo.
- Cada organización tiene diferentes niveles de **tolerancia al riesgo**.
- Entender el riesgo es **clave para priorizar recursos en seguridad**.

---

[🔼](#índice)

---

## **1086. Gestión del Riesgo**

### ✅ ¿Qué es la gestión del riesgo?

La **gestión del riesgo** es el **proceso sistemático para identificar, evaluar y controlar riesgos** que podrían afectar la seguridad de los sistemas, datos o servicios de una organización.

En otras palabras:

> Es cómo las organizaciones **detectan lo que podría salir mal**, **evalúan cuánto daño causaría** y **deciden qué hacer al respecto**.

---

### 📌 ¿Por qué es importante?

- Ayuda a **prevenir pérdidas económicas**.
- Protege datos personales o sensibles.
- Cumple con regulaciones (como la Ley de Protección de Datos, ISO 27001, etc.).
- Prioriza esfuerzos de seguridad donde más se necesitan.

---

### ⚙️ ¿Cómo se “instala” o implementa?

Aunque no se instala como un software, se **aplica un proceso estructurado** en la organización. Esto se puede hacer manualmente (Excel, Word, entrevistas) o con herramientas especializadas.

#### 🔧 Herramientas comunes para gestionar riesgos

| Herramienta               | Tipo            | ¿Para qué sirve?                                 |
| ------------------------- | --------------- | ------------------------------------------------ |
| **Excel / Google Sheets** | Manual          | Registrar, clasificar y evaluar riesgos          |
| **OCTAVE**                | Framework       | Evaluación de riesgos organizacionales           |
| **NIST SP 800-30**        | Estándar/guía   | Evaluación cualitativa y cuantitativa de riesgos |
| **RiskLens**              | Plataforma SaaS | Gestión de riesgos basada en análisis financiero |
| **FAIR Model**            | Metodología     | Cuantificación del riesgo en dinero              |

---

### 🧭 Etapas de la gestión del riesgo (paso a paso)

---

#### 1. 🕵️ Identificación de riesgos

Se detectan los activos importantes, las amenazas, y las vulnerabilidades.

**Ejemplo:**

- Activo: Servidor web
- Amenaza: Hacker
- Vulnerabilidad: Software sin parches

---

#### 2. 📊 Análisis del riesgo

Se evalúa la **probabilidad** de que ocurra y el **impacto** si sucede.

**Escala simple:**

| Riesgo | Probabilidad  | Impacto |
| ------ | ------------- | ------- |
| Bajo   | Poco probable | Bajo    |
| Alto   | Muy probable  | Crítico |

También puedes usar fórmulas:

> **Riesgo = Amenaza × Vulnerabilidad × Impacto**

---

#### 3. 🎯 Evaluación y priorización

Se ordenan los riesgos desde los más graves hasta los menos importantes. Así sabes en qué enfocarte primero.

---

#### 4. 🛡️ Tratamiento del riesgo

Hay 4 formas principales de tratar un riesgo:

| Estrategia | ¿Qué hace?                            | Ejemplo                            |
| ---------- | ------------------------------------- | ---------------------------------- |
| Mitigar    | Reducir el riesgo                     | Usar firewall, actualizar software |
| Aceptar    | Aceptar que el riesgo existe          | Riesgo bajo que no vale mitigar    |
| Transferir | Pasar el riesgo a otro (como seguros) | Contratar seguro cibernético       |
| Eliminar   | Dejar de hacer la actividad de riesgo | Eliminar una app antigua           |

---

#### 5. 🔁 Monitoreo y revisión

Los riesgos cambian. Hay que revisarlos periódicamente para adaptarse.

---

### ✏️ Ejemplo completo y fácil de entender

---

#### 🎯 Escenario: Empresa de comercio electrónico (tienda en línea)

---

#### 1. Identificación

| Activo          | Amenaza                  | Vulnerabilidad                    |
| --------------- | ------------------------ | --------------------------------- |
| Página de pagos | Ataque Man-in-the-Middle | No usa HTTPS                      |
| Base de datos   | Acceso no autorizado     | Contraseña débil                  |
| Red interna     | Ransomware               | Usuarios abren correos maliciosos |

---

#### 2. Análisis

| Riesgo                           | Probabilidad | Impacto | Nivel de riesgo |
| -------------------------------- | ------------ | ------- | --------------- |
| Robo de tarjetas por HTTP        | Alta         | Crítico | Muy Alto        |
| Acceso a BD por contraseña débil | Media        | Alto    | Alto            |
| Ransomware                       | Alta         | Crítico | Muy Alto        |

---

#### 3. Tratamiento

| Riesgo           | Acción tomada                                 |
| ---------------- | --------------------------------------------- |
| HTTP en pagos    | Instalar certificado SSL (usar HTTPS)         |
| Contraseña débil | Aplicar política de contraseñas fuertes + MFA |
| Ransomware       | Capacitación + instalar antivirus actualizado |

---

#### 4. Seguimiento

- Revisión mensual del firewall.
- Análisis de vulnerabilidades cada trimestre.
- Actualización constante del inventario de activos.

---

### 🧠 Conclusión

- La gestión de riesgos **no es algo que se instale como un programa**, sino un proceso continuo.
- Ayuda a las organizaciones a **evitar daños serios antes de que ocurran**.
- Se puede hacer **con herramientas simples** (Excel) o **plataformas especializadas**.

---

[🔼](#índice)

---

## **1087. Evaluación del Riesgo**

### ✅ ¿Qué es la Evaluación del Riesgo?

Es el **proceso de identificar, analizar y entender los riesgos** a los que están expuestos los sistemas informáticos, los datos o la organización en general.

> En otras palabras: es **detectar qué puede salir mal, qué tan probable es que pase, qué consecuencias tendría y cómo podrías prepararte.**

---

### 🧩 ¿Por qué es importante?

- **Anticipas problemas** antes de que ocurran.
- Te permite **priorizar recursos** en lo más importante.
- Ayuda a cumplir con estándares como **ISO 27001**, **NIST**, **GDPR**, etc.
- Evita pérdidas económicas, reputacionales y legales.

---

### 📌 Diferencia entre Evaluación del Riesgo y Gestión del Riesgo

| Término                   | ¿Qué hace?                                                 |
| ------------------------- | ---------------------------------------------------------- |
| **Evaluación del riesgo** | Identifica y analiza los riesgos                           |
| **Gestión del riesgo**    | Decide qué hacer con esos riesgos (aceptar, mitigar, etc.) |

---

### 🔧 ¿Cómo se instala o implementa?

No se “instala” como un software, pero se **aplica como una metodología de trabajo**. Se puede hacer:

- Manualmente (en papel, Excel).
- Con plantillas o formularios estándar.
- Con software especializado.

**Herramientas útiles:**

- Hojas de cálculo
- NIST SP 800-30 (guía de evaluación de riesgos)
- ISO/IEC 27005
- RiskLens (software de análisis FAIR)
- Microsoft Threat Modeling Tool

---

### 🧭 Etapas de la Evaluación del Riesgo

---

#### 1. 🔍 Identificación del riesgo

Se identifican:

- **Activos** (lo que vale proteger): servidores, bases de datos, aplicaciones, etc.
- **Amenazas** (lo que puede dañarlo): hackers, errores humanos, fallas técnicas.
- **Vulnerabilidades** (lo que lo hace débil): software desactualizado, mala configuración.

🧠 Ejemplo fácil:

- Activo: Laptop del jefe de contabilidad
- Amenaza: Robo físico
- Vulnerabilidad: No tiene contraseña, ni cifrado de disco

---

#### 2. 📊 Análisis del riesgo

Se evalúa:

- La **probabilidad** de que ocurra (Alta, Media, Baja)
- El **impacto** que tendría si ocurre (Crítico, Alto, Medio, Bajo)

También puedes calcularlo así:

> **Riesgo = Probabilidad × Impacto**

🧠 Ejemplo:

- Probabilidad: Alta
- Impacto: Crítico
- Riesgo: Muy alto

---

#### 3. 🧮 Valoración del riesgo

Se asignan niveles (por colores o puntuación):

| Riesgo  | Nivel    |
| ------- | -------- |
| Bajo    | Verde    |
| Medio   | Amarillo |
| Alto    | Naranja  |
| Crítico | Rojo     |

Esto te dice **a qué darle prioridad**.

---

#### 4. 📄 Documentación del riesgo

Toda la información se coloca en una **tabla** o **registro de riesgos**:

| ID  | Activo       | Riesgo               | Prob. | Impacto | Nivel    | Responsable |
| --- | ------------ | -------------------- | ----- | ------- | -------- | ----------- |
| 1   | Servidor web | Acceso no autorizado | Alta  | Crítico | Muy alto | Equipo IT   |

---

### ✅ Resultado: ¿Qué obtienes?

- Una lista priorizada de riesgos.
- Datos para tomar decisiones.
- Información para pasar a la **gestión del riesgo** (plan de acción).

---

### 📘 Ejemplo completo y fácil de entender

---

#### 🎯 Escenario: Colegio que usa una plataforma virtual para clases

---

#### 1. Identificación

| Activo                  | Amenaza              | Vulnerabilidad                    |
| ----------------------- | -------------------- | --------------------------------- |
| Plataforma web          | Ataques DDoS         | No usa servicios de protección    |
| Servidor de notas       | Robo de credenciales | Contraseñas simples de profesores |
| Red WiFi administrativa | Acceso no autorizado | Red sin cifrado WPA2              |

---

#### 2. Análisis

| Riesgo                                 | Probabilidad | Impacto | Nivel de riesgo |
| -------------------------------------- | ------------ | ------- | --------------- |
| Ataque DDoS deja la web sin acceso     | Media        | Alto    | Alto            |
| Robo de contraseñas de profesores      | Alta         | Crítico | Muy alto        |
| Acceso a red interna por WiFi insegura | Media        | Medio   | Medio           |

---

#### 3. Documentación

| ID  | Activo                  | Riesgo               | Prob. | Impacto | Nivel    | Responsable    |
| --- | ----------------------- | -------------------- | ----- | ------- | -------- | -------------- |
| 1   | Plataforma web          | DDoS                 | Media | Alto    | Alto     | Proveedor TI   |
| 2   | Servidor de notas       | Robo de credenciales | Alta  | Crítico | Muy alto | Coordinador IT |
| 3   | Red WiFi administrativa | Acceso no autorizado | Media | Medio   | Medio    | Técnico redes  |

---

#### 4. Resultado

- **Prioridad alta:** Cambiar política de contraseñas, implementar doble factor.
- **Acciones sugeridas:**

  - Activar protección DDoS (Cloudflare, por ejemplo).
  - Fortalecer WiFi con WPA3 o VPN para acceso remoto.
  - Educar a los docentes sobre seguridad.

---

### 🧠 Conclusión

- La evaluación del riesgo te dice **qué está en peligro, cómo y cuánto puede doler si pasa algo malo**.
- Es **clave para la ciberseguridad organizacional**.
- Se puede hacer con **herramientas simples (Excel)** o **plataformas avanzadas**.

---

[🔼](#índice)

---

## **1088. Gestión de Controles**

### ✅ ¿Qué es?

La **Gestión de Controles** en ciberseguridad es el proceso de **seleccionar, aplicar, monitorear y revisar los controles de seguridad** que ayudan a proteger los sistemas, redes, personas y datos frente a amenazas o vulnerabilidades.

> **En otras palabras**: son las "reglas, mecanismos o herramientas" que una organización aplica para **evitar, detectar o corregir problemas de seguridad**.

---

### 🎯 ¿Qué son los “controles”?

Son **medidas técnicas, físicas o administrativas** que se implementan para reducir riesgos.

#### Tipos de controles:

| Tipo de Control      | Ejemplo                                                    |
| -------------------- | ---------------------------------------------------------- |
| **Preventivo**       | Contraseñas fuertes, antivirus, firewalls                  |
| **Detectivo**        | Sistemas de detección de intrusos (IDS), alertas           |
| **Correctivo**       | Restauración de backup, reinstalar sistema limpio          |
| **Físico**           | Puertas con cerradura, cámaras de seguridad                |
| **Administrativo**   | Políticas de seguridad, capacitaciones, auditorías         |
| **Técnico (lógico)** | Encriptación, autenticación multifactor, control de acceso |

---

### 🧩 ¿Por qué es importante la Gestión de Controles?

- Asegura que **los controles estén actualizados y funcionando**.
- Ayuda a **reducir el impacto de ciberataques**.
- Mejora el cumplimiento con normas como **ISO 27001, NIST, PCI-DSS, GDPR**.
- Reduce costos de respuesta a incidentes y daños legales.

---

### 🧰 ¿Cómo se “instala” o implementa?

No es un programa como un software, sino un **conjunto de prácticas y herramientas** que se aplican de forma organizada.

---

#### 🔧 Pasos para implementar una Gestión de Controles

---

#### 1. 📋 Identificar riesgos y activos a proteger

Ejemplo: base de datos de clientes, servidores web, laptops de empleados.

---

#### 2. 🧠 Seleccionar controles apropiados

Con base en los riesgos identificados, seleccionas los controles más adecuados.

Ejemplo:

- Para proteger la base de datos → encriptación, autenticación multifactor
- Para proteger laptops → software antivirus, políticas de bloqueo de sesión

---

#### 3. 🔐 Implementar los controles

Instalar software, aplicar políticas, educar usuarios.

---

#### 4. 📊 Monitorear y auditar

Verificar que los controles funcionen correctamente. Puedes usar herramientas como:

- SIEM (Security Information and Event Management)
- Software de monitoreo de red

---

#### 5. 🔄 Evaluar y mejorar

Revisar continuamente si los controles son efectivos y actualizarlos.

---

### 🧠 Ejemplos fáciles de entender

---

#### 👨‍🏫 Caso 1: Escuela

- Riesgo: alumnos acceden a información privada de otros
- Control: se configuran cuentas separadas por estudiante con contraseñas
- Gestión: el encargado de informática revisa semanalmente los accesos

---

#### 💼 Caso 2: Empresa pequeña

- Riesgo: phishing por correos maliciosos
- Control: instalar filtros de spam y dar capacitación a empleados
- Gestión: revisar estadísticas de correos bloqueados y realizar simulaciones

---

### 📘 Ejemplo completo

---

#### 🎯 Escenario: Empresa de ventas online (E-commerce)

---

#### 🧾 Paso 1: Identificar riesgos

| Activo             | Riesgo                      |
| ------------------ | --------------------------- |
| Plataforma web     | Inyección SQL, ataques DDoS |
| Base de datos      | Robo de datos               |
| Correo corporativo | Phishing                    |

---

#### 🧠 Paso 2: Seleccionar controles

| Riesgo        | Control seleccionado                                   |
| ------------- | ------------------------------------------------------ |
| Inyección SQL | Validación de entradas, firewall de aplicaciones (WAF) |
| Ataques DDoS  | Cloudflare o AWS Shield                                |
| Robo de datos | Encriptación, control de acceso basado en roles        |
| Phishing      | Filtro de spam, formación del personal                 |

---

#### 🛠️ Paso 3: Implementar controles

- Se configura el WAF con reglas OWASP
- Se activa Cloudflare contra DDoS
- Se establece política de contraseñas y doble factor
- Se capacita al personal cada 3 meses

---

#### 📈 Paso 4: Monitorear y auditar

- Se revisan los logs del SIEM semanalmente
- Se hacen pruebas de phishing una vez al mes
- Se hace backup automático diario

---

#### 🔁 Paso 5: Evaluar

- Los indicadores muestran baja tasa de clics en phishing (mejora)
- El tiempo de respuesta ante alertas ha bajado un 30%
- Se actualiza el software del firewall por nuevas amenazas detectadas

---

### ✅ Resultado

- Controles bien definidos y adaptados al negocio
- Menos vulnerabilidades expuestas
- Cultura de seguridad más fuerte

---

### 🎓 Conclusión

- La **gestión de controles** es como tener un **sistema de defensa organizado**.
- No basta con instalar antivirus: hay que **planificar, aplicar y mantener controles según el contexto.**
- Bien ejecutada, reduce riesgos y prepara a la organización ante cualquier amenaza.

---

[🔼](#índice)

---

## **1089. Definiciones y términos**

### ✅ ¿Por qué es importante conocer las definiciones?

La **ciberseguridad** es un campo técnico y complejo. Conocer los términos más usados te ayudará a:

- Entender lo que ocurre cuando hay amenazas digitales.
- Comunicarte con profesionales del área.
- Protegerte mejor tanto en lo personal como en tu trabajo.

---

### 🧠 Términos fundamentales y sus definiciones

---

| Término                             | Definición clara                                                   | Ejemplo fácil                                                         |
| ----------------------------------- | ------------------------------------------------------------------ | --------------------------------------------------------------------- |
| **Amenaza**                         | Cualquier cosa que pueda causar daño a tus sistemas o información. | Un virus que puede robar tus fotos o contraseñas.                     |
| **Vulnerabilidad**                  | Debilidad o fallo que puede ser explotado.                         | Una computadora sin actualizar puede ser atacada fácilmente.          |
| **Riesgo**                          | Probabilidad de que una amenaza explote una vulnerabilidad.        | Si no cambias tu contraseña débil, es probable que alguien acceda.    |
| **Ataque**                          | Acción de un atacante para comprometer un sistema.                 | Enviar un correo falso para que hagas clic en un enlace.              |
| **Phishing**                        | Técnica para engañar y obtener tus datos personales.               | Un correo que parece de tu banco pidiendo tu clave.                   |
| **Malware**                         | Software malicioso que causa daño.                                 | Virus, troyanos, spyware, ransomware.                                 |
| **Firewall**                        | Herramienta que filtra el tráfico de red.                          | Bloquea conexiones no autorizadas.                                    |
| **Antivirus**                       | Programa que detecta y elimina malware.                            | Windows Defender, Avast, Kaspersky.                                   |
| **Cifrado (Encriptación)**          | Proceso de convertir datos en ilegibles sin clave.                 | WhatsApp cifra tus mensajes para que solo tú y el otro los lean.      |
| **Autenticación**                   | Verificación de identidad.                                         | Iniciar sesión con usuario y contraseña.                              |
| **Autenticación multifactor (MFA)** | Verificación adicional a la contraseña.                            | Te pide un código que llega por SMS o app.                            |
| **Ingeniería Social**               | Manipulación psicológica para obtener información.                 | Un “técnico” te llama diciendo que necesita tu clave para “ayudarte”. |
| **Backdoor**                        | Puerta trasera para entrar a un sistema sin permiso.               | Un hacker deja una vía secreta para volver a entrar después.          |
| **Zero Trust**                      | Modelo que no confía en nadie, ni dentro ni fuera.                 | Cada acceso debe ser verificado, siempre.                             |
| **SIEM**                            | Herramienta para centralizar alertas de seguridad.                 | Recoge logs y detecta ataques en tiempo real.                         |

---

### 🔧 ¿Cómo se “instalan” estas definiciones?

Obviamente no se “instalan” como un software, pero **se aplican y se aprenden** en:

#### 1. 🧑‍🏫 Capacitaciones de ciberseguridad

Cursos, charlas o talleres donde se explican estos términos.

#### 2. 📃 Políticas internas en empresas

Se incluye un glosario para que todos sepan qué significan los términos.

#### 3. 📘 Material educativo en sitios web o manuales

Guías, ebooks, normas (como la ISO/IEC 27001) que definen conceptos clave.

#### 4. 🧪 Prácticas reales y simulaciones

Cuando haces simulacros de incidentes, aprendes los términos en contexto.

---

### 🎯 Ejemplo completo y aplicable

---

#### 📌 Escenario: Oficina administrativa en una pequeña empresa

---

1. **Amenaza:** un hacker quiere robar los correos de la empresa.
2. **Vulnerabilidad:** empleados usan contraseñas débiles.
3. **Riesgo:** alta posibilidad de acceso no autorizado.
4. **Control:** se implementa autenticación multifactor (MFA).
5. **Término aplicado:**

   - Se explica a los empleados qué es **phishing** y cómo detectarlo.
   - Se les enseña qué es una **contraseña segura** y por qué es necesaria.
   - Se les informa que cualquier incidente debe reportarse (concepto de **respuesta a incidentes**).

---

#### 📈 Resultado:

- Los empleados **entienden mejor los riesgos** y actúan de forma más segura.
- Se reduce el riesgo de accesos indebidos y de pérdida de datos.
- La empresa fortalece su postura de seguridad con **educación y buenas prácticas**.

---

### 🎓 Conclusión

Conocer las **definiciones y términos clave** en ciberseguridad es como tener un buen diccionario cuando hablas un nuevo idioma: **te ayuda a entender lo que pasa, comunicarte mejor y actuar correctamente**.

---

[🔼](#índice)

---

## **1090. Análisis de impacto de negocio**

### ✅ ¿Qué es el Análisis de Impacto de Negocio?

Es una herramienta o proceso que **identifica y evalúa cómo ciertos incidentes afectan al negocio**, en términos de:

- Interrupción de servicios.
- Pérdidas económicas.
- Reputación dañada.
- Riesgos legales o de cumplimiento.

> 💡 En otras palabras, el BIA nos ayuda a **entender qué procesos del negocio son más críticos** y cuánto **tiempo puede estar un sistema fuera de servicio** antes de causar daños graves.

---

### 🎯 ¿Para qué sirve?

- Para **priorizar** qué sistemas, áreas o procesos recuperar primero en una emergencia.
- Para preparar un **Plan de Continuidad de Negocio** o un **Plan de Recuperación ante Desastres (DRP)**.
- Para **minimizar el impacto de interrupciones** en la operación.

---

### 🧠 Conceptos clave que se analizan en un BIA

| Concepto                           | ¿Qué significa?                                              | Ejemplo fácil                                  |
| ---------------------------------- | ------------------------------------------------------------ | ---------------------------------------------- |
| **Proceso crítico**                | Actividad clave para el negocio.                             | Facturación, atención al cliente, envíos.      |
| **RTO (Recovery Time Objective)**  | Tiempo máximo aceptable que puede estar caído un proceso.    | 4 horas sin acceso al sistema de pedidos.      |
| **RPO (Recovery Point Objective)** | Cantidad de datos que se puede perder sin causar daño grave. | Aceptamos perder máximo 1 hora de datos.       |
| **Impacto**                        | Consecuencias si el proceso se interrumpe.                   | Pérdidas de ventas, clientes molestos, multas. |

---

### 🛠️ ¿Cómo se “instala” o aplica un BIA?

No se instala como un software, pero sí se **aplica en 5 pasos** prácticos:

---

#### 1. 🧩 Identificar procesos críticos

Haz una lista de las actividades claves para la operación del negocio.

Ejemplo: ventas, pagos a proveedores, atención al cliente.

---

#### 2. ⏱️ Estimar el impacto de su interrupción

¿Qué pasa si este proceso no funciona por 1, 4, 12 o 24 horas?

Ejemplo: Si ventas está caído 12 horas, se pierden \$5,000.

---

#### 3. 📏 Determinar RTO y RPO

- ¿En cuánto tiempo debe recuperarse?
- ¿Cuántos datos se pueden perder?

Ejemplo:

- RTO: 6 horas
- RPO: 30 minutos

---

#### 4. 📋 Clasificar el nivel de impacto

Impacto puede ser:

- Bajo: no afecta mucho.
- Medio: interfiere.
- Alto: para el negocio.

---

#### 5. 🧭 Documentar y tomar decisiones

Con la info reunida, decides:

- Qué proteger con más urgencia.
- Dónde invertir en seguridad y backups.

---

### 🧪 Ejemplo completo (Caso realista)

---

#### 🏢 Escenario: Empresa de ventas en línea

---

**Proceso 1: Sistema de pedidos en línea**

- Si se cae:

  - Se pierden ventas por hora.
  - Los clientes se quejan en redes.

- RTO: 4 horas
- RPO: 15 minutos
- Impacto: Alto
- Acción: tener servidores en la nube con failover automático.

---

**Proceso 2: Sistema de recursos humanos**

- Si se cae:

  - No se procesan pagos ni vacaciones.

- RTO: 24 horas
- RPO: 1 día
- Impacto: Medio
- Acción: backups diarios, acceso por VPN.

---

**Proceso 3: Correo corporativo**

- Si se cae:

  - El equipo no puede comunicarse.

- RTO: 6 horas
- RPO: 30 minutos
- Impacto: Alto
- Acción: solución en la nube tipo Microsoft 365 o Google Workspace con respaldo.

---

#### 📘 Resultado

Con este análisis:

✅ La empresa **prioriza los recursos más críticos**.

✅ Establece planes de recuperación **basados en RTO y RPO reales**.

✅ Mejora su **continuidad del negocio** y toma mejores decisiones en seguridad.

---

### 🎓 Conclusión

El **Análisis de Impacto en el Negocio (BIA)** es **clave en ciberseguridad y continuidad del negocio**. Permite responder a estas preguntas:

- ¿Qué procesos no pueden fallar?
- ¿Cuánto tiempo podemos tolerar una caída?
- ¿Cuánto podemos perder sin afectar al negocio?

---

[🔼](#índice)

---

## **1091. Desarrollo o adquisición de software seguro**

### ✅ ¿Qué significa "software seguro"?

Un **software seguro** es una aplicación (web, móvil o de escritorio) que **ha sido diseñada, desarrollada, probada o seleccionada teniendo en cuenta medidas de ciberseguridad**. Su objetivo es **proteger los datos, los usuarios y la infraestructura** donde se ejecuta.

---

### 🎯 ¿Por qué es importante?

Porque si el software **tiene fallos de seguridad**:

- Un atacante puede robar datos personales o bancarios.
- Puede secuestrar sistemas (ransomware).
- Puede dañar la reputación del negocio.
- Puede provocar pérdidas económicas graves.

---

### 🧠 ¿Qué se debe tener en cuenta?

Ya sea que **desarrolles** o **compres** software, debes seguir buenas prácticas de ciberseguridad desde el inicio.

---

#### 📌 Etapas del Desarrollo Seguro (conocido como **SDLC seguro**)

| Etapa         | Qué se hace en seguridad          | Ejemplo sencillo                          |
| ------------- | --------------------------------- | ----------------------------------------- |
| Requisitos    | Definir necesidades de seguridad. | “El usuario debe iniciar sesión con MFA.” |
| Diseño        | Diseñar estructuras seguras.      | Usar roles de usuario, limitar acceso.    |
| Desarrollo    | Aplicar buenas prácticas.         | No guardar contraseñas en texto plano.    |
| Pruebas       | Buscar vulnerabilidades.          | Test de SQL Injection, XSS, etc.          |
| Despliegue    | Implementar seguro.               | HTTPS, logs, control de cambios.          |
| Mantenimiento | Parches y monitoreo.              | Actualizar librerías inseguras.           |

---

### 🛠️ ¿Cómo se “instala” o aplica en la práctica?

Hay dos escenarios: cuando **desarrollas** software, o cuando lo **adquieres**.

---

#### 🧑‍💻 Si desarrollas software:

1. ✅ Usa marcos de desarrollo seguros (Django, Spring, etc.).
2. ✅ Valida toda la entrada de datos del usuario.
3. ✅ Usa autenticación fuerte (MFA, tokens, roles).
4. ✅ Guarda contraseñas con hash (ej. bcrypt, Argon2).
5. ✅ Usa librerías actualizadas y confiables.
6. ✅ Realiza pruebas de seguridad (DAST/SAST).
7. ✅ Aplica OWASP Top 10 como guía.

---

#### 🛒 Si compras o adquieres software:

1. 🕵️‍♂️ Evalúa al proveedor:

   - ¿Tiene certificaciones? (ISO 27001, SOC 2)
   - ¿Actualiza el software con regularidad?

2. 🔐 Verifica que tenga:

   - Autenticación segura
   - Registro de auditoría (logs)
   - Control de accesos por roles

3. 🧪 Solicita pruebas:

   - PenTesting, informes de vulnerabilidades

4. 🤝 Firma un acuerdo de seguridad:

   - NDA + SLA + compromiso de seguridad

---

### 🔍 Ejemplo práctico completo

---

#### 🎯 Escenario: Empresa que necesita un software para gestionar ventas y clientes (CRM)

---

##### Opción A: Lo desarrollan internamente

1. **Definen requisitos seguros**

   - Solo personal autorizado accede al CRM
   - Autenticación con 2FA

2. **Diseñan arquitectura segura**

   - Separan backend, frontend y base de datos
   - Implementan roles de usuarios

3. **Desarrollan con buenas prácticas**

   - Validan formularios y entradas
   - Protegen contra inyecciones SQL
   - Usan bcrypt para contraseñas

4. **Realizan pruebas**

   - Prueban con OWASP ZAP para detectar vulnerabilidades
   - Simulan inyecciones y ataques XSS

5. **Despliegan con HTTPS y logs de actividad**

6. **Monitorean errores y parchan vulnerabilidades** regularmente

---

##### Opción B: Compran un software CRM de un proveedor externo

1. **Investigan** y seleccionan un proveedor que:

   - Tiene encriptación de datos en tránsito y reposo
   - Cumple con el RGPD / Ley de protección de datos
   - Tiene historial de buenas prácticas

2. **Solicitan una demo técnica + informe de seguridad**

3. **Firman acuerdo SLA con cláusulas de seguridad**

4. **Instalan el software en un servidor interno y configuran**:

   - Roles de usuario
   - Logs de acceso
   - Backups automáticos diarios

5. **Capacitan al personal** para usarlo de forma segura

---

### 🧠 Buenas prácticas clave para software seguro

✅ Aplicar la norma **OWASP Top 10**

✅ Tener un ambiente de desarrollo seguro

✅ Realizar auditorías de código

✅ Establecer control de versiones y repositorios privados

✅ Capacitar a los desarrolladores en ciberseguridad

✅ Monitorear en tiempo real el comportamiento del software

✅ Usar herramientas como:

- **SonarQube** (análisis de código)
- **OWASP ZAP / Burp Suite** (pruebas)
- **Dependabot / Snyk** (vulnerabilidades en librerías)

---

### 🧩 Conclusión

- Desarrollar o adquirir software seguro no es solo una tarea del área técnica, sino una **decisión estratégica** de la empresa.
- Invertir tiempo en seguridad **previene brechas, sanciones y pérdidas**.
- La seguridad debe aplicarse **desde el inicio del ciclo de vida del software** (SDLC seguro).

---

[🔼](#índice)

---

## **1092. Introducción a OWASP**

### ✅ ¿Qué es OWASP?

OWASP significa **Open Worldwide Application Security Project** (Proyecto Abierto de Seguridad en Aplicaciones Web).
Es una **organización sin fines de lucro** que ayuda a desarrolladores, empresas y profesionales a **construir software más seguro**.

Su contenido es **gratuito y abierto**, y es muy respetado en el mundo de la ciberseguridad.

---

### 🎯 ¿Para qué sirve OWASP?

Sirve para:

- Detectar y prevenir **vulnerabilidades** en aplicaciones web.
- Mejorar la **seguridad del desarrollo de software**.
- Capacitar a equipos en **prácticas de ciberseguridad**.
- Establecer **estándares globales** de seguridad web.

---

### ¿Qué es el OWASP Top 10?

Es el recurso más famoso de OWASP.
Consiste en una **lista actualizada de las 10 principales vulnerabilidades** que afectan a las aplicaciones web.

| 🧨 Código | Vulnerabilidad                     | Ejemplo fácil de entender                     |
| --------- | ---------------------------------- | --------------------------------------------- |
| A01       | Broken Access Control              | Un usuario común puede ver archivos de admins |
| A02       | Cryptographic Failures             | Se transmite contraseña sin cifrar            |
| A03       | Injection                          | El atacante pone código SQL en un formulario  |
| A04       | Insecure Design                    | La lógica del sistema permite omitir reglas   |
| A05       | Security Misconfiguration          | Dejan puerto abierto o error en producción    |
| A06       | Vulnerable Components              | Usar librerías desactualizadas con bugs       |
| A07       | Identification & Auth Failures     | Login sin límite de intentos fallidos         |
| A08       | Software & Data Integrity Failures | Actualizaciones sin verificación              |
| A09       | Logging & Monitoring Failures      | No hay alertas ni registros de errores        |
| A10       | SSRF                               | Servidor accede recursos internos sin control |

---

### 👨‍🏫 Ejemplo simple de A03: Inyección SQL

```sql
-- Código inseguro:
SELECT * FROM usuarios WHERE usuario = '$input' AND clave = '$clave';
```

Un atacante puede poner en el formulario:

```
' OR '1'='1
```

Y obtener acceso a toda la base de datos sin saber la clave.

---

### 🛠️ ¿Cómo se “instala” o aplica OWASP?

No se instala como un programa, sino que se aplica como **una metodología o guía de seguridad**.

---

#### ✅ Así se aplica en un proyecto real:

1. **Educación del equipo**: Explicar qué es OWASP y sus riesgos.
2. **Checklist de OWASP Top 10**: Evaluar el software con esa lista.
3. **Herramientas automatizadas**:

   - 🔍 [OWASP ZAP](https://www.zaproxy.org/): escanea vulnerabilidades.
   - 🛠️ SonarQube: analiza código inseguro.
   - 📦 Snyk: detecta librerías con fallos.

4. **Corrección de vulnerabilidades**:

   - Reescribir código inseguro.
   - Configurar servidores adecuadamente.

5. **Documentación y buenas prácticas**:

   - Validar inputs.
   - Usar HTTPS.
   - Cifrar contraseñas con bcrypt.
   - Control de acceso con roles.

---

### 👨‍💻 Ejemplo completo en la vida real

---

#### 🎯 Escenario: Estás desarrollando una app web para registrar usuarios.

---

##### 🔒 Problema: Tu formulario tiene esta línea en el backend

```js
// Inseguro
const usuario = req.body.usuario;
const clave = req.body.clave;

const query = `SELECT * FROM usuarios WHERE usuario = '${usuario}' AND clave = '${clave}'`;
```

Un atacante pone:

```
usuario: admin
clave: ' OR '1'='1
```

El resultado: puede entrar sin la contraseña real. 🚨 (OWASP A03)

---

##### ✅ Solución: aplicar OWASP

```js
// Seguro: usando parámetros
const query = "SELECT * FROM usuarios WHERE usuario = ? AND clave = ?";
db.query(query, [usuario, claveHash], ...);
```

Y además:

- Limitar intentos de login (previene A07)
- Cifrar la clave con bcrypt (previene A02)
- Validar los inputs con regex o librerías (previene A03)
- Hacer logs de accesos y errores (previene A09)

---

#### 📘 Recursos OWASP recomendados

| Recurso      | ¿Para qué sirve?                      | Link                                                                                                                                                   |
| ------------ | ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| OWASP Top 10 | Lista de vulnerabilidades             | [https://owasp.org/www-project-top-ten/](https://owasp.org/www-project-top-ten/)                                                                       |
| OWASP ZAP    | Escáner de vulnerabilidades web       | [https://www.zaproxy.org/](https://www.zaproxy.org/)                                                                                                   |
| Cheat Sheets | Guías para prácticas seguras          | [https://cheatsheetseries.owasp.org/](https://cheatsheetseries.owasp.org/)                                                                             |
| OWASP ASVS   | Estándar de verificación de seguridad | [https://owasp.org/www-project-application-security-verification-standard/](https://owasp.org/www-project-application-security-verification-standard/) |

---

### ✅ Conclusión

- OWASP **no es un software que se instala**, es una guía de referencia **esencial** para desarrollar, probar y mantener software seguro.
- Si estás en ciberseguridad o desarrollo web, **debes conocer y aplicar OWASP**.
- Apoyarte en herramientas como **OWASP ZAP, SonarQube, Snyk o Burp Suite** te ayudará a encontrar errores antes de que lo hagan los atacantes.

---

[🔼](#índice)

---

## **1093. OWASP Top 10**

### ✅ ¿Qué es OWASP Top 10?

El **OWASP Top 10** es una lista de las **10 vulnerabilidades más críticas de seguridad** en aplicaciones web, publicada por la organización **OWASP** (Open Worldwide Application Security Project).

Se actualiza cada pocos años (la última versión es **2021**) y **sirve como guía práctica** para que desarrolladores, empresas y expertos en seguridad aprendan a **identificar y prevenir errores comunes de seguridad.**

---

### 🧠 ¿Por qué es importante?

Porque **más del 90% de los ataques a sitios web** ocurren por vulnerabilidades conocidas en esta lista.

Si tú desarrollas una app y **previenes estas 10 fallas**, estás evitando los errores más graves y frecuentes.

---

### Las 10 vulnerabilidades del OWASP Top 10 (versión 2021)

| Código | Vulnerabilidad                               | Explicación fácil                             | Ejemplo corto                             |
| ------ | -------------------------------------------- | --------------------------------------------- | ----------------------------------------- |
| A01    | **Broken Access Control**                    | No se controlan bien los permisos             | Un usuario común accede a datos de admins |
| A02    | **Cryptographic Failures**                   | Mal uso de cifrado                            | Contraseñas guardadas sin cifrar          |
| A03    | **Injection**                                | El sistema ejecuta código no deseado          | Inyección SQL o de comandos               |
| A04    | **Insecure Design**                          | El diseño mismo es inseguro                   | No hay validación de lógica de negocio    |
| A05    | **Security Misconfiguration**                | Mala configuración del servidor/app           | Dejar error 500 con detalles del sistema  |
| A06    | **Vulnerable and Outdated Components**       | Usar librerías viejas con fallos              | jQuery o Log4j vulnerables                |
| A07    | **Identification & Authentication Failures** | Fallos en login/autenticación                 | No hay límite de intentos o 2FA           |
| A08    | **Software & Data Integrity Failures**       | Sin verificación de integridad                | Código actualizado desde fuente no segura |
| A09    | **Security Logging & Monitoring Failures**   | No hay registros ni alertas                   | No se detectan ataques en tiempo real     |
| A10    | **Server Side Request Forgery (SSRF)**       | Servidor accede a sitios internos sin control | Se abusa del servidor como proxy          |

---

### 🧰 ¿Cómo **se instala** o se usa OWASP Top 10?

OWASP Top 10 **no se instala como software**, se **aplica como una guía de buenas prácticas**.

#### 📋 Pasos para aplicar OWASP Top 10:

1. **Leer la documentación oficial** en [owasp.org](https://owasp.org).
2. **Capacitar al equipo de desarrollo** sobre estas 10 vulnerabilidades.
3. **Aplicar controles en el código** y revisar que se cumplan buenas prácticas.
4. **Usar herramientas de análisis de seguridad** para escanear errores, como:

   - OWASP ZAP (escaneo automático de vulnerabilidades).
   - SonarQube (análisis de código estático).
   - Snyk o Dependabot (para detectar librerías inseguras).

5. **Hacer pruebas de penetración** para validar la seguridad antes de publicar.

---

### 💡 Ejemplos simples por categoría

#### 🔓 A01 - Broken Access Control

> Un usuario normal accede al panel de administrador:

URL:

```
https://miweb.com/admin
```

Solución:

```js
if (!usuario.rol.includes("admin")) {
  return res.status(403).send("Acceso denegado");
}
```

---

#### 💾 A02 - Cryptographic Failures

> Guardas la contraseña como texto plano:

```json
{
  "usuario": "juan",
  "clave": "123456"
}
```

Solución:

```js
// Hasheado con bcrypt
const bcrypt = require("bcrypt");
const hash = await bcrypt.hash("123456", 10);
```

---

#### 💉 A03 - SQL Injection

```js
// Inseguro
db.query(`SELECT * FROM users WHERE email = '${email}'`);
```

Solución:

```js
db.query(`SELECT * FROM users WHERE email = ?`, [email]);
```

---

### ✅ Ejemplo completo paso a paso (Aplicación insegura vs. segura)

#### 🎯 Escenario:

Estás desarrollando una API de login en Node.js para tu aplicación web.

---

#### ❌ Código Inseguro

```js
app.post("/login", (req, res) => {
  const email = req.body.email;
  const clave = req.body.clave;

  // ¡Vulnerable a SQL Injection!
  const query = `SELECT * FROM usuarios WHERE email = '${email}' AND clave = '${clave}'`;
  db.query(query, (err, result) => {
    if (result.length > 0) {
      res.send("Acceso permitido");
    } else {
      res.send("Acceso denegado");
    }
  });
});
```

##### Problemas:

- A03: Inyección SQL.
- A02: Claves sin cifrar.
- A07: No hay control de intentos ni 2FA.
- A09: No hay registro de intentos fallidos.

---

#### ✅ Código Seguro siguiendo OWASP

```js
const bcrypt = require("bcrypt");

app.post("/login", async (req, res) => {
  const { email, clave } = req.body;

  const query = `SELECT * FROM usuarios WHERE email = ?`;
  db.query(query, [email], async (err, result) => {
    if (err || result.length === 0) {
      // A09: Logging de fallos
      console.log(`Intento fallido de login para ${email}`);
      return res.status(401).send("Usuario o clave incorrectos");
    }

    const user = result[0];
    const claveOk = await bcrypt.compare(clave, user.clave_hash);

    if (!claveOk) {
      console.log(`Intento fallido de login para ${email}`);
      return res.status(401).send("Usuario o clave incorrectos");
    }

    res.send("Bienvenido, acceso concedido");
  });
});
```

##### Seguridad aplicada:

✅ Evita inyección (A03)

✅ Usa bcrypt (A02)

✅ Logging básico (A09)

✅ Preparado para agregar MFA (A07)

---

### 📘 Recursos oficiales

| Recurso                               | Enlace                                                                                                                                                 |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| OWASP Top 10 2021                     | [https://owasp.org/Top10](https://owasp.org/Top10)                                                                                                     |
| OWASP ZAP                             | [https://www.zaproxy.org](https://www.zaproxy.org)                                                                                                     |
| OWASP Cheat Sheets                    | [https://cheatsheetseries.owasp.org](https://cheatsheetseries.owasp.org)                                                                               |
| Guía ASVS (verificación de seguridad) | [https://owasp.org/www-project-application-security-verification-standard/](https://owasp.org/www-project-application-security-verification-standard/) |

---

### 🎓 Conclusión

- El **OWASP Top 10 es una brújula esencial** para el desarrollo seguro de aplicaciones web.
- No se instala, **se estudia y se aplica como marco de referencia**.
- Aplicar estas prácticas ayuda a **proteger tu app contra los ataques más comunes.**

---

[🔼](#índice)

---

## **1094. Modelo de Madurez para el Aseguramiento del Software**

### 🧠 ¿Qué es un Modelo de Madurez?

Un **modelo de madurez** te ayuda a **medir qué tan bien estás asegurando el software que desarrollas**. No se trata solo de escribir buen código, sino de hacerlo **de forma segura, repetible y profesional**.

---

### 🔐 ¿Qué es el Modelo de Madurez para el Aseguramiento del Software?

Es una guía creada por **OWASP** llamada **OpenSAMM (Software Assurance Maturity Model)**.
Ayuda a organizaciones (grandes o pequeñas) a **evaluar, mejorar y formalizar sus prácticas de seguridad** en el desarrollo de software.

---

### 📊 ¿Por qué es útil?

Porque te permite:

- Saber **qué tan madura es tu empresa** en seguridad.
- Establecer **objetivos claros** de mejora.
- Adoptar buenas prácticas según tu **nivel de madurez**.
- Incluir seguridad desde el diseño hasta el mantenimiento del software.

---

### 🧱 ¿Cómo está estructurado OpenSAMM?

Se divide en **4 funciones de seguridad clave**, cada una con **3 prácticas de seguridad**.
Cada práctica tiene **3 niveles de madurez** (de básico a avanzado).

#### 🔹 1. Gobernanza

- Estrategia y métricas
- Educación y concientización
- Política y cumplimiento

#### 🔹 2. Construcción

- Requisitos de seguridad
- Arquitectura de seguridad
- Diseño de amenazas

#### 🔹 3. Verificación

- Revisión de código
- Pruebas de seguridad
- Auditorías de dependencias

#### 🔹 4. Implementación

- Gestión del entorno
- Implementación segura
- Gestión de vulnerabilidades

---

### 📶 Niveles de Madurez

| Nivel         | Qué significa                                         |
| ------------- | ----------------------------------------------------- |
| 1️⃣ Básico     | Seguridad aplicada de forma ocasional o informal      |
| 2️⃣ Intermedio | Seguridad integrada en procesos estables              |
| 3️⃣ Avanzado   | Seguridad automatizada, repetible, medible y continua |

---

### 📌 ¿Cómo **se aplica** OpenSAMM? (No se instala)

No es un software que se instala, pero puedes **implementar su metodología** siguiendo estos pasos:

#### 📋 PASOS PARA IMPLEMENTAR OpenSAMM

1. **Evaluación inicial**

   - Evalúa en qué nivel está tu organización.
   - Puedes usar la herramienta gratuita de OWASP:
     👉 [https://owaspsamm.org](https://owaspsamm.org)

2. **Identificación de brechas**

   - ¿Estás en nivel 1, pero quieres llegar al 2?
   - ¿Te falta revisar el código o hacer pruebas automatizadas?

3. **Plan de mejora**

   - Define un roadmap con fechas y responsables.

4. **Implementación de prácticas**

   - Añade revisiones de código, capacitaciones, gestión de dependencias, etc.

5. **Medición y ajuste**

   - Usa métricas y evaluaciones periódicas para ver el progreso.

---

### 🎓 Ejemplos fáciles de entender

#### ✅ Ejemplo 1: Revisión de código (Verificación)

| Nivel | Práctica                | Ejemplo                                                            |
| ----- | ----------------------- | ------------------------------------------------------------------ |
| 1️⃣    | Revisión informal       | Juan revisa el código de Pedro "por encima" antes de subirlo       |
| 2️⃣    | Revisión sistemática    | Todo PR debe ser revisado por otro desarrollador y pasar SonarQube |
| 3️⃣    | Automatización + reglas | Se usa IA o reglas estáticas para detectar fallas automáticamente  |

---

#### ✅ Ejemplo 2: Política y cumplimiento (Gobernanza)

| Nivel | Práctica                      | Ejemplo                                                    |
| ----- | ----------------------------- | ---------------------------------------------------------- |
| 1️⃣    | Política verbal               | El jefe dice “No uses contraseñas simples”                 |
| 2️⃣    | Documentado y con seguimiento | Hay una política escrita que se revisa trimestralmente     |
| 3️⃣    | Integrado + auditado          | Las políticas se revisan, actualizan y auditan formalmente |

---

### 💡 Ejemplo completo de aplicación en una startup

**Situación:** Tienes una pequeña empresa de desarrollo web y quieres mejorar la seguridad de tus aplicaciones.

---

#### 🔍 Paso 1: Diagnóstico rápido

- **Gobernanza:** No hay políticas formales.
- **Construcción:** A veces se piensa en seguridad, pero no hay un proceso.
- **Verificación:** No se hace revisión de código.
- **Implementación:** El servidor se actualiza manualmente cuando hay tiempo.

→ Resultado: **Nivel de madurez: 1**

---

#### 🛠️ Paso 2: Roadmap hacia Nivel 2

1. Redactar y aplicar una **política de contraseñas y cifrado**.
2. Hacer una **checklist de revisión de código** en cada PR.
3. Agregar **OWASP ZAP** a las pruebas del frontend.
4. Usar **Snyk** para detectar vulnerabilidades en librerías.
5. Hacer al menos **una capacitación de seguridad** cada 3 meses.

---

#### ✅ Resultado después de 3 meses:

| Área                 | Mejora lograda                                                 |
| -------------------- | -------------------------------------------------------------- |
| Revisión de código   | 100% de PR revisados por otro dev + análisis estático          |
| Gestión de librerías | Uso de herramienta para vulnerabilidades                       |
| Capacitación         | Sesión mensual de concientización                              |
| Políticas            | Documento oficial publicado en Notion con control de versiones |

→ Resultado: **Nivel de madurez: 2 (casi 3)**

---

### 📘 Recursos oficiales

| Recurso                               | Enlace                                                                                                                                 |
| ------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| Página oficial de OpenSAMM            | [https://owaspsamm.org](https://owaspsamm.org)                                                                                         |
| Documentación técnica                 | [https://owaspsamm.org/model/](https://owaspsamm.org/model/)                                                                           |
| Herramienta de autoevaluación (Excel) | [https://owaspsamm.org/resources/SAMM-2.0-Assessment-Workbook.xlsx](https://owaspsamm.org/resources/SAMM-2.0-Assessment-Workbook.xlsx) |
| OWASP SAMM GitHub                     | [https://github.com/OWASP/samm](https://github.com/OWASP/samm)                                                                         |

---

### 🎯 Conclusión

- El **Modelo de Madurez para Aseguramiento del Software (OpenSAMM)** es **una herramienta estratégica**, no un software.
- Te ayuda a **medir y mejorar** la seguridad de tu software en toda la organización.
- Puedes comenzar desde lo básico e ir madurando paso a paso hasta tener una empresa **con prácticas seguras, documentadas y auditables**.

---

[🔼](#índice)

---

## **1095. Roles, equipos y modelos de seguridad**

### 🧠 ¿Qué significa esto?

En ciberseguridad, **roles** y **equipos** definen **las responsabilidades de cada persona o área** dentro de una organización.

Un **modelo de seguridad** describe **cómo se organizan y aplican** esas responsabilidades para proteger la información.

---

### 🧱 1. **Roles en Seguridad de la Información**

Estos roles aseguran que todas las tareas relacionadas con la protección de la información estén bien cubiertas. Los más comunes son:

| Rol                                          | Función                                        |
| -------------------------------------------- | ---------------------------------------------- |
| 🔒 CISO (Chief Information Security Officer) | Lidera la estrategia de ciberseguridad         |
| 👨‍💻 Analista de Seguridad                     | Monitorea, detecta y responde a amenazas       |
| 👷‍♂️ Ingeniero de Seguridad                    | Implementa soluciones técnicas de seguridad    |
| 📊 Auditor de Seguridad                      | Verifica que se cumplan políticas y normativas |
| 📚 Oficial de Cumplimiento                   | Asegura el cumplimiento de leyes como GDPR     |
| 🧪 Tester de Penetración (Pentester)         | Evalúa vulnerabilidades explotables            |
| 👨‍🏫 Usuario final                             | Sigue las políticas, contraseñas y alertas     |

---

#### 🔹 Ejemplo Fácil:

Imagina una empresa como un banco:

- El **CISO** diseña las reglas del juego.
- El **Ingeniero** instala las alarmas y cámaras (firewalls, antivirus).
- El **Analista** está en la sala de control mirando las cámaras.
- El **Pentester** actúa como ladrón para ver si puede entrar.
- El **Auditor** revisa si todos cumplen las reglas.
- El **usuario final** (cajero) no debe compartir su contraseña.

---

### 🧑‍🤝‍🧑 2. Equipos de Seguridad

Según el tamaño de la organización, estos pueden ser:

#### 🟦 a. Equipo interno

- Tienen su propio SOC (Centro de Operaciones de Seguridad).
- Ej: Grandes empresas, bancos, entidades gubernamentales.

#### 🟧 b. Equipo mixto o tercerizado (outsourcing)

- Usan servicios de empresas externas para monitoreo o pentesting.
- Ej: Startups, medianas empresas.

---

#### Equipos especializados:

| Equipo                                           | Función                                               |
| ------------------------------------------------ | ----------------------------------------------------- |
| SOC (Security Operations Center)                 | Detecta y responde a incidentes 24/7                  |
| CSIRT (Computer Security Incident Response Team) | Actúa en incidentes graves y recupera sistemas        |
| Red Team                                         | Simula ataques reales                                 |
| Blue Team                                        | Defiende los sistemas frente a ataques                |
| Purple Team                                      | Une a los Red y Blue para mejorar defensa y detección |

---

#### 🔹 Ejemplo fácil:

- El **Red Team** es como un ladrón profesional que intenta entrar al sistema.
- El **Blue Team** son los guardias que lo evitan.
- El **Purple Team** analiza qué funcionó y qué no, para mejorar a ambos.

---

### 🧭 3. Modelos de Seguridad

Un modelo define **cómo se protege la información**. Existen varios tipos. Aquí te muestro los más conocidos:

#### 🔐 a. Modelo Bell-LaPadula (Confidencialidad)

- Se centra en **evitar la lectura no autorizada**.
- Usado en defensa o gobiernos.
- Principio: "No leas hacia arriba, no escribas hacia abajo".

#### 🛡️ b. Modelo Biba (Integridad)

- Se enfoca en **evitar la corrupción de datos**.
- Principio: "No leas hacia abajo, no escribas hacia arriba".

#### 🔄 c. Modelo Clark-Wilson (Transacciones seguras)

- Aplica controles sobre quién puede hacer qué.
- Usado en bancos, hospitales.

#### 🧩 d. Zero Trust

- No se confía en nada ni nadie por defecto.
- Verifica identidad y contexto cada vez.
- “Nunca confíes, siempre verifica”.

---

### 🛠 ¿Cómo se "instala" o aplica esto?

No se instala como un programa. Se **implementa en políticas, equipos y tecnología**:

#### Pasos básicos para aplicar roles, equipos y modelos:

1. **Definir roles** de seguridad según tu organización.
2. **Asignar personas** o contratar expertos para esos roles.
3. **Establecer un equipo** (interno o tercerizado) para ciberseguridad.
4. **Aplicar un modelo de seguridad** según tus necesidades (Zero Trust, Biba, Bell-LaPadula…).
5. **Capacitar** a todo el personal para que cumpla su rol.

---

### ✅ Ejemplo completo de aplicación en una PYME

#### 🏢 Empresa: SoftwarePYME SAC

Tiene 20 empleados y desarrolla software para contabilidad.

---

#### 👨‍🔧 Paso 1: Roles definidos

- CISO: Dueño del negocio.
- Analista: Técnico IT con formación básica en ciberseguridad.
- Usuario final: Todo el personal.

---

#### 🧑‍🤝‍🧑 Paso 2: Equipo mixto

- No tiene SOC interno.
- Contrata a una empresa externa para pentesting anual y respuesta ante incidentes (CSIRT tercerizado).

---

#### 🔐 Paso 3: Modelo de Seguridad

- Aplica el modelo **Zero Trust**.

  - Nadie accede sin autenticación multifactor.
  - Se segmentan redes por áreas.
  - Cada acción crítica se registra y valida.

---

#### 📄 Paso 4: Políticas internas

- Prohibido compartir contraseñas.
- Uso obligatorio de gestor de contraseñas.
- Backups semanales obligatorios.
- Se aplican parches de seguridad cada 2 semanas.

---

#### 🧠 Paso 5: Capacitación

- Todos los empleados toman una capacitación cada 3 meses sobre:

  - Phishing
  - Contraseñas seguras
  - Uso correcto de correo y dispositivos

---

#### 🔎 Resultado:

✅ Roles definidos

✅ Equipo funcional de respuesta

✅ Modelo aplicado (Zero Trust)

✅ Políticas internas activas

✅ Personal capacitado

---

### 📘 Recursos Recomendados

| Recurso                       | Enlace                                                                                                                 |
| ----------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| OpenSAMM Roles                | [https://owaspsamm.org/model/](https://owaspsamm.org/model/)                                                           |
| NIST CSF (marco de seguridad) | [https://www.nist.gov/cyberframework](https://www.nist.gov/cyberframework)                                             |
| Modelo Zero Trust (NIST)      | [https://www.nist.gov/publications/zero-trust-architecture](https://www.nist.gov/publications/zero-trust-architecture) |

---

### 🎯 Conclusión

- **Roles bien definidos** garantizan que la seguridad no se deje al azar.
- **Equipos especializados** responden eficazmente ante amenazas.
- **Modelos de seguridad** te dan una base sólida para proteger información.
- No se instala como un software, **se implementa mediante políticas, personas y herramientas.**

---

[🔼](#índice)

---

## **1096. Pirámide de crecimiento o criterio de contratación**

### 🧱 ¿Qué es la Pirámide de Crecimiento o Criterio de Contratación?

La **Pirámide de Crecimiento** (también llamada a veces **Pirámide de Talento**) es un modelo que ayuda a las empresas a estructurar **cómo contratar personal técnico o de ciberseguridad**, desde los roles más básicos hasta los más avanzados.

Este modelo organiza a los profesionales en **niveles**, de acuerdo a su:

- **Conocimiento**
- **Experiencia**
- **Responsabilidades**
- **Impacto en la organización**

---

### 🔺 Estructura de la pirámide

Imagina una pirámide dividida en 4 o 5 niveles. De abajo hacia arriba:

| Nivel                                   | Rol típico                    | Características                                   |
| --------------------------------------- | ----------------------------- | ------------------------------------------------- |
| 🟩 Nivel 1: Junior                      | Soporte, técnico, pasante     | Aprende y ejecuta tareas básicas                  |
| 🟨 Nivel 2: Semi Senior                 | Analista, desarrollador       | Ya tiene experiencia, resuelve tareas medianas    |
| 🟧 Nivel 3: Senior                      | Especialista, líder técnico   | Alta experiencia, toma decisiones técnicas        |
| 🟥 Nivel 4: Arquitecto / Lead / Manager | CISO, arquitecto de seguridad | Lidera estrategia, toma decisiones clave          |
| ⭐ Nivel 5: Experto / Consultor         | Consultor, investigador       | Define estándares, entrena equipos, visión global |

---

#### 🔹 Ejemplo fácil de entender:

Imagina que eres dueño de una panadería digital (una empresa que vende pan online 🍞):

- Contratas a un **junior** para responder correos y revisar alertas simples.
- Luego a un **semi senior** para gestionar el sitio web y los pedidos.
- Un **senior** se encarga de proteger los datos de los clientes con firewalls y cifrado.
- Un **arquitecto** diseña toda la infraestructura de seguridad.
- Un **consultor externo** revisa todo y te propone mejoras anuales.

---

### 🛠 ¿Cómo se "instala" esto en una empresa?

No se instala como software. Se **aplica como una estrategia organizacional** y de recursos humanos (RRHH). Estos son los pasos:

---

### ✅ Paso a paso para aplicar la pirámide de contratación

#### 1. **Define tu estrategia de ciberseguridad**

- ¿Qué quieres proteger?
- ¿Qué herramientas ya usas?
- ¿Qué tipo de amenazas enfrentas?

#### 2. **Haz un mapeo de roles**

- ¿Qué tareas necesitas cubrir?
- ¿Tienes monitoreo de alertas? ¿Parches de sistemas? ¿Respaldo? ¿Firewall?

#### 3. **Ubica cada rol en la pirámide**

Ejemplo:

- Nivel 1 → Técnico en soporte TI
- Nivel 2 → Analista SOC
- Nivel 3 → Especialista en ciberseguridad
- Nivel 4 → Arquitecto de seguridad
- Nivel 5 → Consultor externo / mentor

#### 4. **Diseña un plan de carrera**

Permite que tus empleados suban en la pirámide:

- Cursos
- Proyectos asignados
- Mentorías
- Certificaciones

#### 5. **Contrata según el nivel necesario**

No contrates solo expertos. Mezcla todos los niveles:

- Juniors: hacen tareas repetitivas y aprenden.
- Seniors: lideran, toman decisiones.
- Leads: gestionan proyectos y arquitectura.
- Consultores: validan y optimizan la estrategia.

---

### 📄 Ejemplo completo aplicado en una empresa

#### Empresa: **"SafeCorp SAC"** (empresa mediana de software financiero)

#### 🔐 Necesidades de seguridad:

- Mantener seguros los datos de los clientes.
- Responder a incidentes rápidamente.
- Cumplir con normas de protección de datos (como GDPR).

---

#### 🔺 Aplicación de la pirámide:

| Nivel   | Rol                                | Tareas asignadas                                                      |
| ------- | ---------------------------------- | --------------------------------------------------------------------- |
| Nivel 1 | Soporte técnico (Junior)           | Monitorea alertas básicas en la consola del antivirus                 |
| Nivel 2 | Analista SOC (Semi Senior)         | Responde a alertas de malware, configura reglas de firewall           |
| Nivel 3 | Especialista en seguridad (Senior) | Diseña políticas, lidera simulacros de phishing                       |
| Nivel 4 | Arquitecto de Seguridad            | Diseña toda la infraestructura segura (VPN, segmentación, backups)    |
| Nivel 5 | Consultor externo                  | Audita la empresa, entrena al equipo, verifica cumplimiento normativo |

---

#### 📈 Resultado:

- Se logra una **estructura balanceada**: juniors aprenden, seniors lideran, expertos validan.
- Reducción de costos: no se contratan solo expertos.
- Alto crecimiento interno: técnicos ascienden en la pirámide.
- Mejora continua: cada nivel aporta valor y evolución.

---

### 🧩 Relación con modelos como NIST o CMMI

La pirámide se puede aplicar dentro de marcos como:

| Modelo    | Relación                                               |
| --------- | ------------------------------------------------------ |
| NIST CSF  | Apoya el dominio "Develop and Maintain Workforce"      |
| CMMI-SVC  | Mejora continua de servicios con niveles de madurez    |
| ISO 27001 | Ayuda en la gestión de roles, competencias y controles |

---

### 🧠 Conclusión

- La **pirámide de contratación** ayuda a formar equipos sostenibles y escalables.
- Puedes **mezclar niveles de experiencia** para ahorrar costos y mejorar resultados.
- Apoya tanto la contratación como el crecimiento interno del personal técnico.
- No es una herramienta de software, **se aplica como una estrategia organizativa**.

---

[🔼](#índice)

---

## **1097. La experiencia de Platzi con ISO27001**

### 🏆 1. ¿Quién es Platzi y qué certificación obtuvo?

- **Platzi**, la plataforma líder de educación online en español, fue la primera **edtech certificada con ISO 27001:2022 en Colombia** ([Blu Radio][1]).
- Este logro representa su compromiso con la **seguridad, privacidad y excelencia operativa** ([Blu Radio][1]).

---

### 🔍 2. ¿Cómo inició el camino hacia ISO 27001?

#### a) Buenas prácticas desde el inicio

- Implementaron firewall, cifrado de bases de datos, controles de acceso desde etapas tempranas ([Cloudflare][2]).
- Gradualmente formalizaron procesos bajo estándares globales como OWASP, NIST SP 800‑53 y el modelo OWASP SAMM ([Platzi][3]).

#### b) Cultura de seguridad institucional

- Introdujeron cápsulas de seguridad en reuniones semanales y cursos obligatorios desde el proceso de contratación.
- Formaron “Security Champions” para fomentar la concientización en todos los niveles ([Platzi][3], [AmericaMalls & Retail][4]).

#### c) Formalización del SGSI

- Documentaron rigurosamente procesos y políticas.
- Contrataron auditor interno/externo y seleccionaron un organismo certificador (ICONTECH) para auditoría ISO 27001 ([Platzi][3]).

---

### ⚙️ 3. ¿Cómo se aplicó ISO 27001 en Platzi?

#### Paso a paso práctico:

| Etapa             | Qué hicieron                                            |
| ----------------- | ------------------------------------------------------- |
| Planificar (Plan) | Analizar contexto, partes interesadas y definir alcance |
| Hacer (Do)        | Implementar controles: cifrado, firewall, accesos       |
| Verificar (Check) | Auditorías internas, revisión por la dirección          |
| Actuar (Act)      | Gestión de no conformidades y mejora continua           |

- Adoptaron el ciclo **PDCA** como base de su SGSI ([es.wikipedia.org][5], [Cloudflare][2]).
- Integraron estándares y frameworks como **OWASP Top 10, NIST SP 800‑30 y SP 800‑53**, y OpenSAMM para madurez del software ([La Nota Económica][6]).

---

### 🧪 4. Ejemplo ilustrativo inspirado en la experiencia de Platzi

#### 📍 Empresa ficticia: “EducaLearn S.A.”

**Objetivo:** certificarse bajo ISO 27001 para proteger datos estudiantiles y procesos internos:

1. **Implementación de controles técnicos:**

   - Firewalls, acceso segmentado, cifrado de datos.

2. **Evaluación de riesgos:**

   - Clasificación de información y aplicación de controles según tipo de dato.

3. **Capacitación interna:**

   - Cápsulas de seguridad, cursos obligatorios, designación de Security Champions.

4. **Formalización documental:**

   - Políticas, procedimientos, auditorías internas y revisión por dirección.

5. **Auditoría externa:**

   - Con un organismo acreditado para obtener certificado.

6. **Mejora continua:**

   - Actualización periódica, gestión de vulnerabilidades y métricas de desempeño.

✅ Resultado: certificación ISO 27001 lograda, reducción de riesgos, mayor confianza institucional y cadena de mejora constante.

---

### 📄 Conclusión

- Platzi se convirtió en la **primera edtech certificada ISO 27001:2022 en Colombia**, reflejando un firme compromiso organizacional y cultural con la seguridad ([Blu Radio][1], [Platzi][3], [es.wikipedia.org][5]).
- Su enfoque fue integral: tecnología, cultura organizacional, documentación, auditoría y mejora continua.
- La certificación no fue un fin, sino un **hito dentro de un proceso de evolución continua** en seguridad ([AmericaMalls & Retail][4]).

[1]: https://www.bluradio.com/tecnologia/primera-edtech-en-obtener-certificado-iso-27001-so35?utm_source=chatgpt.com "Primera Edtech en obtener certificado ISO 27001 - BluRadio"
[2]: https://www.cloudflare.com/es-la/case-studies/platzi/?utm_source=chatgpt.com "Platzi | Caso práctico | Cloudflare"
[3]: https://platzi.com/cursos/ciberseguridad-en-empresas/la-experiencia-de-platzi-con-iso27001/?utm_source=chatgpt.com "Certificación ISO 27001: Implementación y Mejora Continua en Platzi"
[4]: https://america-retail.com/secciones/omnicanalidad/primera-edtech-certificada-con-iso-27001-en-colombia/?utm_source=chatgpt.com "Primera edtech certificada con ISO 27001 en Colombia - AmericaMalls & Retail"
[5]: https://es.wikipedia.org/wiki/ISO/IEC_27001?utm_source=chatgpt.com "ISO/IEC 27001"
[6]: https://lanotaeconomica.com.co/movidas-empresarial/primera-edtech-en-obtener-certificado-iso-27001-en-colombia/?utm_source=chatgpt.com "Primera Edtech en obtener certificado ISO 27001 en Colombia - La Nota Económica"

---

[🔼](#índice)

---

| **Inicio**         | **atrás 22**                                              | **Siguiente 24**                                            |
| ------------------ | --------------------------------------------------------- | ----------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./7_22_Ciberseguridad_y_Privacidad_para_Empresas.md) | [⏩](./7_24_Seguridad_Informatica_para_Equipos_Tecnicos.md) |
