| **Inicio**         | **atrás 20**                                                                     | **Siguiente 22**                                          |
| ------------------ | -------------------------------------------------------------------------------- | --------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./7_20_Introduccion_a_Ciberseguridad_Prevencion_de_Ataques_Informaticos.md) | [⏩](./7_22_Ciberseguridad_y_Privacidad_para_Empresas.md) |

---

## **Índice**

| Temario                                                                                                                                                                                                    |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [1022. Lo que aprenderás sobre ingeniería social](#1022-lo-que-aprenderás-sobre-ingeniería-social)                                                                                                         |
| [1023. Antecedentes de la ingeniería social](#1023-antecedentes-de-la-ingeniería-social)                                                                                                                   |
| [1024. ¿Qué son la ingeniería social y las reglas de compromiso?](#1024-qué-son-la-ingeniería-social-y-las-reglas-de-compromiso)                                                                           |
| [1025. ¿Por qué funciona la ingeniería social?](#1025-por-qué-funciona-la-ingeniería-social)                                                                                                               |
| [1026. Datos de la ingeniería social](#1026-datos-de-la-ingeniería-social)                                                                                                                                 |
| [1027. Metas de la ingeniería social](#1027-metas-de-la-ingeniería-social)                                                                                                                                 |
| [1028. Principios de la ingeniería social según Kevin Mitnick y Robert Cialdini](#1028-principios-de-la-ingeniería-social-según-kevin-mitnick-y-robert-cialdini)                                           |
| [1029. Principios de la ingeniería social a detalle](#1029-principios-de-la-ingeniería-social-a-detalle)                                                                                                   |
| [1030. Perfil del ingeniero(a) social](#1030-perfil-del-ingenieroa-social)                                                                                                                                 |
| [1031. Tipos de ingeniería social: basada en humanos](#1031-tipos-de-ingeniería-social-basada-en-humanos)                                                                                                  |
| [1032. Tipos de ingeniería social: basada en computadoras](#1032-tipos-de-ingeniería-social-basada-en-computadoras)                                                                                        |
| [1033. Taxonomía de la ingeniería social: marco de ataque](#1033-taxonomía-de-la-ingeniería-social-marco-de-ataque)                                                                                        |
| [1034. Taxonomía de los ataques](#1034-taxonomía-de-los-ataques)                                                                                                                                           |
| [1035. Ejemplos de ataques de la ingeniería social: Baiting y Phishing](#1035-ejemplos-de-ataques-de-la-ingeniería-social-baiting-y-phishing)                                                              |
| [1036. Ejemplos de ataques de ingeniería social: Pretexting, Sextortion, Dumpster Diving, Quid Pro Quo](#1036-ejemplos-de-ataques-de-ingeniería-social-pretexting-sextortion-dumpster-diving-quid-pro-quo) |
| [1037. Ejemplos de ataques de ingeniería social: Vishing, Fake News, Tailgating, Piggybacking](#1037-ejemplos-de-ataques-de-ingeniería-social-vishing-fake-news-tailgating-piggybacking)                   |
| [1038. ¿Qué es la elicitación y por qué es tan exitosa?](#1038-qué-es-la-elicitación-y-por-qué-es-tan-exitosa)                                                                                             |
| [1039. Estrategias y respuestas a la elicitación](#1039-estrategias-y-respuestas-a-la-elicitación)                                                                                                         |
| [1040. Qué es el pretexting y cuál es su proceso](#1040-qué-es-el-pretexting-y-cuál-es-su-proceso)                                                                                                         |
| [1041. Qué son los Deepfake y sus tipos](#1041-qué-son-los-deepfake-y-sus-tipos)                                                                                                                           |
| [1042. Aplicaciones disponibles para crear Deepfake](#1042-aplicaciones-disponibles-para-crear-deepfake)                                                                                                   |
| [1043. Relación del Deepfake, la ingeniería social y cómo detectarlos](#1043-relación-del-deepfake-la-ingeniería-social-y-cómo-detectarlos)                                                                |
| [1044. Herramientas de detección de Deepfake](#1044-herramientas-de-detección-de-deepfake)                                                                                                                 |
| [1045. Retos de los procesos de investigación forense en Deepfake](#1045-retos-de-los-procesos-de-investigación-forense-en-deepfake)                                                                       |
| [1046. Medidas de prevención, protección y cómo crear una cultura de seguridad](#1046-medidas-de-prevención-protección-y-cómo-crear-una-cultura-de-seguridad)                                              |
| [1047. Cómo protegerse y recomendaciones](#1047-cómo-protegerse-y-recomendaciones)                                                                                                                         |
| [1048. Creando un escenario de pretexting](#1048-creando-un-escenario-de-pretexting)                                                                                                                       |

# **Introducción a la Ingeniería Social: Técnicas, Ataques y Pretexting**

## **1022. Lo que aprenderás sobre ingeniería social**

### 🎭 ¿Qué es la Ingeniería Social?

La **ingeniería social** es el arte de manipular a las personas para que revelen información confidencial o realicen acciones inseguras.

> No se ataca a una computadora, **se ataca al humano** que la usa.

Los atacantes **engañan, mienten o se hacen pasar por alguien confiable** para lograr que las víctimas:

- Hagan clic en un enlace malicioso
- Entreguen sus contraseñas
- Instalen software malicioso
- Depositen dinero
- Les den acceso físico o remoto

---

### 🧠 ¿Qué aprenderás sobre Ingeniería Social?

Al estudiar este tema, aprenderás a:

#### 1. **Reconocer tácticas comunes de ataque**

- Correos falsos (phishing)
- Mensajes de WhatsApp o SMS sospechosos (smishing)
- Llamadas engañosas (vishing)
- Engaños en redes sociales (pretexting)
- Manipulación emocional (urgencia, miedo, autoridad)

#### 2. **Conocer el perfil de las víctimas**

- Personas mayores, niños o empleados sin formación
- Personas con exceso de confianza o curiosidad
- Usuarios distraídos o bajo presión

#### 3. **Identificar los objetivos del atacante**

- Contraseñas
- Números de tarjeta
- Acceso físico o remoto
- Datos personales o empresariales

#### 4. **Implementar defensas prácticas**

- Educación constante
- Verificación de identidades
- Doble factor de autenticación (2FA)
- Uso de contraseñas seguras
- No hacer clic sin revisar la URL

---

### 🔧 ¿Cómo se "instala" la defensa contra ingeniería social?

No se instala como un programa, pero sí se **desarrolla como una mentalidad preventiva**. Aquí algunas formas:

| Acciones básicas                         | Explicación                                                   |
| ---------------------------------------- | ------------------------------------------------------------- |
| ✅ Educación constante                   | Aprender sobre estos ataques para no caer                     |
| 🔐 2FA                                   | Aun si te roban la contraseña, no pueden entrar sin tu código |
| 📧 Revisar bien los correos              | Dudar de remitentes extraños o urgentes                       |
| 📵 No confiar en llamadas inesperadas    | Verificar siempre antes de actuar                             |
| 🔍 Comprobar enlaces antes de hacer clic | ¿Es un dominio real o falso?                                  |

---

### 💡 Ejemplo completo y fácil de entender

#### Escenario: _"Hola, soy del banco, su cuenta está en riesgo"_

**Situación:**

Lucía, una mujer de 40 años, recibe una llamada en la mañana:

> "Hola, señora Lucía, soy del área de seguridad del Banco ABC. Detectamos una compra sospechosa de S/800 en su cuenta. ¿Podría confirmarnos su número de tarjeta para detenerla?"

Lucía, nerviosa, responde con su número y código de seguridad.

Horas después, ve compras que ella **nunca autorizó**. Ha sido víctima de ingeniería social por **vishing** (engaño por llamada telefónica).

---

#### Cómo debió actuar Lucía:

1. **Colgar la llamada** y llamar al número oficial del banco (el que aparece en su tarjeta).
2. **No entregar datos personales** a una persona que la contacta de forma inesperada.
3. Activar **notificaciones automáticas del banco** y **2FA**.

---

### 📚 Conclusión

**Aprender sobre ingeniería social te permite reconocer al atacante incluso cuando no parece uno.** No necesitas saber de programación, solo **estar alerta y aplicar el sentido común digital**.

#### En resumen, aprenderás a:

✅ Identificar señales de engaño

✅ Saber cómo protegerte tú y tu entorno

✅ Entender que el eslabón más débil **sigue siendo el humano**

---

[🔼](#índice)

---

## **1023. Antecedentes de la ingeniería social**

### 🧠 ¿Qué son los antecedentes de la ingeniería social?

La **ingeniería social** no nació con las computadoras ni con internet. Es una **técnica muy antigua** basada en la **manipulación psicológica**, donde una persona engaña a otra para lograr un beneficio propio.

#### 📜 Historia breve:

La ingeniería social tiene sus raíces en tácticas antiguas de engaño usadas en:

- La **guerra (espionaje)**: espías se hacían pasar por civiles o soldados enemigos.
- La **estafa (timos clásicos)**: como el famoso "cuento del tío".
- El **fraude financiero**: como las pirámides o esquemas Ponzi.

Con el avance de la tecnología, esas tácticas migraron al mundo **digital**, donde los atacantes ya no necesitan estar cara a cara para engañarte.

---

### 📌 Ejemplos históricos (fáciles de entender)

#### 1. 🎩 Frank Abagnale Jr. (años 60)

Un joven que se hizo pasar por piloto, médico y abogado, falsificando identidades para ganar dinero, hospedarse gratis, y acceder a lugares restringidos.

➡ **Técnica:** _Imitación de autoridad + confianza_

---

#### 2. 💻 Kevin Mitnick (años 80 y 90)

Uno de los hackers más famosos del mundo. No solo explotaba fallas técnicas, sino que también **llamaba a empleados** para pedir contraseñas haciéndose pasar por técnicos de soporte.

➡ **Técnica:** _Vishing (ingeniería social por llamada) + conocimiento técnico_

---

#### 3. 📧 Primeros ataques de phishing (años 2000)

Hackers comenzaron a enviar correos falsos como si fueran de bancos o servicios populares, pidiendo “verificar tu cuenta”.

➡ **Técnica:** _Phishing masivo por email_

---

### 🛠️ ¿Cómo se “instala” la ingeniería social?

> **No se instala como una app.** Se implementa como una estrategia o mentalidad, tanto para atacar como para defender.

#### 🔐 Desde el lado de la defensa:

- **Capacitación constante** (charlas, videos, ejemplos reales)
- **Simulacros de phishing** para enseñar a identificar engaños
- **Normas de verificación**: nunca dar contraseñas por correo o teléfono
- **Cultura de ciberseguridad**: todos deben estar atentos

---

### 🎓 ¿Qué aprendemos de los antecedentes?

Aprendemos que:

- **No siempre es necesario hackear un sistema.** Es más fácil _engañar al humano_.
- La **autoridad, la urgencia y la confianza** son herramientas poderosas.
- La **educación es la mejor defensa**.

---

### ✅ Ejemplo completo

#### Escenario realista: "El técnico de soporte"

**Situación:**

Juan, un empleado de una empresa, recibe una llamada:

> “Hola, soy Pedro del área de sistemas. Necesitamos hacer mantenimiento urgente al sistema de correo, ¿puedes darme tu usuario y contraseña para hacerlo desde aquí?”

Juan, sin sospechar, se lo da.

**Consecuencia:**

El atacante accede a su correo, encuentra documentos confidenciales, y se infiltra en otros servicios de la empresa.

---

#### ¿Qué aprendemos?

- **Engañaron al humano, no al sistema.**
- El atacante usó una **estrategia clásica** de los años 80, actualizada a tiempos modernos.
- Juan debió:

  - Confirmar con su jefe o el área de sistemas
  - Nunca dar contraseñas por teléfono

---

### 🧩 Conclusión

Los **antecedentes de la ingeniería social** nos muestran que:

- La manipulación psicológica es más antigua que los virus informáticos.
- Las personas **siguen siendo el eslabón más débil**.
- La **formación y conciencia de los usuarios** es fundamental para proteger sistemas y redes.

---

[🔼](#índice)

---

## **1024. ¿Qué son la ingeniería social y las reglas de compromiso?**

### 🧠 1. ¿Qué es la Ingeniería Social?

La **ingeniería social** es el arte de **manipular a las personas para que revelen información confidencial**, hagan algo que no deberían o entreguen acceso a sistemas protegidos.
No se necesita ser un hacker técnico, sino un buen manipulador psicológico.

#### 🎯 Objetivo:

Engañar a una persona para conseguir:

- Contraseñas
- Acceso a computadoras o servidores
- Archivos internos
- Instalación de malware
- Información empresarial

#### 🧰 Métodos comunes:

| Técnica        | Ejemplo sencillo                                            |
| -------------- | ----------------------------------------------------------- |
| **Phishing**   | Un correo que parece de tu banco, pidiendo tu contraseña.   |
| **Vishing**    | Llamada telefónica fingiendo ser del soporte técnico.       |
| **Smishing**   | Mensaje de texto con un enlace malicioso.                   |
| **Pretexting** | Fingir ser otra persona (ej. policía, técnico, jefe).       |
| **Baiting**    | Usar “carnadas” como USBs con malware o regalos falsos.     |
| **Tailgating** | Entrar detrás de alguien a un área restringida sin permiso. |

---

### 📜 2. ¿Qué son las Reglas de Compromiso? (RoE)

Las **Reglas de Compromiso** son un conjunto de normas **éticas, legales y técnicas** que indican **lo que está permitido o prohibido** hacer en un **pentest (prueba de penetración)** o **evaluación de seguridad**, especialmente cuando se usan técnicas como la ingeniería social.

#### 🛡️ ¿Por qué existen?

Porque en una auditoría **no todo vale**. Necesitamos saber:

- ¿Se puede hacer phishing real o solo simulado?
- ¿Se pueden grabar llamadas o correos?
- ¿A qué empleados se les puede contactar?
- ¿Cuáles sistemas están en prueba?
- ¿Quién es el contacto si se encuentra una brecha?

#### 🧾 Ejemplo de Reglas de Compromiso:

1. No se permiten ataques fuera del horario laboral.
2. Solo se permite enviar correos de phishing, no SMS ni llamadas.
3. Si se logra obtener acceso, no se deben alterar archivos reales.
4. Todo debe ser documentado y reportado.

---

### ⚙️ ¿Cómo se “instala” esto?

> **No se instala como software.**
>
> Se **aplica o configura** en un entorno de trabajo o laboratorio de ciberseguridad.

#### 🔒 En un entorno profesional:

1. **Se define el alcance**: qué se prueba y qué no.
2. **Se firman acuerdos de reglas de compromiso** entre el auditor y la empresa.
3. **Se capacita al equipo** de seguridad y se hace una simulación (como campañas de phishing simuladas).

---

### ✅ Ejemplo completo: simulacro de ingeniería social con RoE

#### 🏢 Escenario:

Empresa “Segurito S.A.” contrata a un equipo de ciberseguridad para evaluar su vulnerabilidad ante ataques de ingeniería social.

##### ✔️ Reglas de compromiso:

- Solo se pueden enviar correos de phishing.
- No se pueden usar llamadas ni entrar físicamente al local.
- No se puede dañar o modificar ningún sistema.

##### 🎣 Ataque simulado:

El auditor envía un correo a varios empleados diciendo:

> "Hola, hemos actualizado nuestro portal de RR.HH. Ingresa con tus credenciales aquí: \[enlace falso]"

Este enlace lleva a una **página falsa simulada** (no maliciosa) para ver cuántos caen.

##### 📊 Resultado:

- 5 de 20 empleados entregaron su usuario y contraseña.
- El equipo de seguridad fue notificado de inmediato.
- Se generó un informe con recomendaciones:

  - Capacitar a empleados
  - Mejorar filtros de correo
  - Agregar autenticación de dos factores (2FA)

---

### 🧩 Conclusión:

| Tema                     | Resumen                                                                |
| ------------------------ | ---------------------------------------------------------------------- |
| **Ingeniería Social**    | Manipular personas para obtener acceso o datos.                        |
| **Reglas de Compromiso** | Normas que delimitan qué puede y no puede hacerse en una auditoría.    |
| **Aplicación**           | Se definen antes de comenzar pruebas o entrenamientos.                 |
| **Objetivo conjunto**    | Medir la preparación de los usuarios sin causar daños ni romper leyes. |

---

[🔼](#índice)

---

## **1025. ¿Por qué funciona la ingeniería social?**

### ✅ **¿Por qué funciona la Ingeniería Social?**

La **ingeniería social funciona porque ataca al eslabón más débil de la ciberseguridad: las personas.**
En lugar de romper firewalls o sistemas cifrados, el atacante **engaña a los usuarios para que cometan errores humanos**: dar contraseñas, abrir archivos maliciosos o ejecutar comandos sin querer.

---

### 🧠 ¿Qué aprovecha exactamente?

La ingeniería social **se basa en principios psicológicos** que afectan a todos, incluso a personas preparadas. Aquí te explico los más importantes:

| Principio Psicológico | ¿Qué significa?                                                       | Ejemplo fácil de entender                                      |
| --------------------- | --------------------------------------------------------------------- | -------------------------------------------------------------- |
| **Confianza**         | Las personas tienden a confiar en figuras de autoridad o lo familiar. | Si alguien dice ser del soporte técnico, le das acceso remoto. |
| **Miedo o urgencia**  | Las personas reaccionan rápido cuando hay presión.                    | “Tu cuenta será bloqueada si no haces clic en este enlace.”    |
| **Curiosidad**        | Lo desconocido genera deseo de saber.                                 | “Mira este archivo: nómina_2025.pdf.exe”                       |
| **Obediencia**        | La mayoría obedece órdenes sin cuestionar.                            | Un mail que parece del jefe pidiendo una transferencia.        |
| **Gratificación**     | Promesas de recompensas engañan fácilmente.                           | “Has ganado un premio. Haz clic aquí para reclamarlo.”         |
| **Reciprocidad**      | Si alguien te da algo, sientes que debes devolver el favor.           | Alguien “ayuda” con algo, y luego pide acceso a información.   |

---

### 💡 Ejemplo real simplificado:

> Imagina que alguien te llama y dice:
>
> _“Hola, soy Pedro del área de sistemas. Estamos actualizando contraseñas y necesito verificar tu cuenta. ¿Me puedes dictar tu usuario y clave para ingresarlo manualmente?”_

Muchas personas **no se atreven a decir que no**, y terminan entregando sus credenciales.

---

### 🔧 ¿Cómo se "instala" la ingeniería social?

> ⚠️ **Ojo:** La ingeniería social **no se instala como software**, pero **sí se puede aplicar, entrenar o prevenir** con pasos muy claros. Veamos ambas caras:

#### 🛠️ Si eres atacante (para propósitos educativos):

1. Estudias a la empresa y a las personas (open source intelligence, OSINT).
2. Diseñas una estrategia: correo, llamada, sitio falso, etc.
3. Simulas un mensaje legítimo.
4. Esperas a que la víctima caiga.

#### 🔐 Si eres defensor:

1. Capacitas al personal en ciberseguridad.
2. Haces simulacros de phishing.
3. Usas autenticación multifactor (2FA).
4. Definas políticas claras sobre entrega de información.

---

### ✅ Ejemplo completo: ¿Por qué funciona?

#### 🎭 Escenario:

Un empleado nuevo de atención al cliente recibe este correo:

> **Asunto:** URGENTE - Problema con tu acceso
>
> _“Hola Ana, detectamos actividad sospechosa en tu cuenta de empresa. Ingresa ahora mismo al siguiente enlace para evitar la suspensión del sistema:_
>
> \[[http://intranet-segura.soporte.empresa.com\]”](http://intranet-segura.soporte.empresa.com]”)

- Ana reconoce el logo del correo (está copiado de la empresa).
- El lenguaje suena profesional, y hay una **sensación de urgencia**.
- Entra al enlace y **escribe su usuario y contraseña**.

#### ⚠️ ¿Qué pasó?

1. Ana **confió** en el remitente (ingeniería social).
2. Respondió rápido por **miedo a perder el acceso**.
3. **No validó** que el enlace era falso.

#### 🔓 Resultado:

El atacante ahora tiene acceso al sistema interno y puede comprometer toda la red.

---

### 📌 ¿Cómo prevenir que funcione?

1. **Desconfiar de lo inesperado.** Verifica todo, incluso si parece legítimo.
2. **Nunca compartas contraseñas**, por ningún medio.
3. **No hagas clic en enlaces de correos sospechosos.**
4. **Verifica URLs** cuidadosamente (no confíes solo en el diseño).
5. **Capacita al personal de forma continua.**

---

### 🧩 Conclusión:

| Elemento                                         | Descripción breve                                        |
| ------------------------------------------------ | -------------------------------------------------------- |
| **Funciona porque**                              | Apela a emociones humanas: miedo, confianza, urgencia.   |
| **No requiere técnicas avanzadas**               | Solo habilidad para manipular psicológicamente.          |
| **Se previene con educación**                    | Concientización + políticas + verificación de identidad. |
| **Un ataque puede empezar con un simple correo** | Y terminar con una brecha de seguridad crítica.          |

---

[🔼](#índice)

---

## **1026. Datos de la ingeniería social**

### 🧠 **Datos de la Ingeniería Social**

> La ingeniería social es una técnica de manipulación psicológica que **busca engañar a las personas para obtener acceso no autorizado** a información, sistemas o lugares.
>
> Más del **90% de los ciberataques exitosos involucran ingeniería social**.
>
> La mayoría **no explota fallos técnicos**, sino humanos.

---

### ✅ ¿Qué tipo de **datos** se usan en Ingeniería Social?

Un atacante **recopila información previa (OSINT)** antes de lanzar el ataque. Estos datos se utilizan para **parecer más creíbles** y convencer a la víctima de actuar.

| Tipo de dato       | ¿Qué incluye?                                      | ¿Por qué es útil para el atacante? | Ejemplo fácil                                                     |
| ------------------ | -------------------------------------------------- | ---------------------------------- | ----------------------------------------------------------------- |
| **Personales**     | Nombre, teléfono, dirección, cumpleaños            | Para hacer mensajes más creíbles   | “Hola, Gustavo. Hoy es tu cumpleaños, entra aquí para tu regalo.” |
| **Profesionales**  | Cargo, empresa, jefe, equipo, correo corporativo   | Para simular autoridad o urgencia  | “Soy de RR.HH. Necesito tu RUC para un cambio de planilla.”       |
| **Redes sociales** | Posts, likes, fotos, comentarios                   | Para personalizar ataques          | “Vi que viajaste a Cusco, mira estas fotos nuevas tuyas.”         |
| **Tecnológicos**   | Sistemas operativos, herramientas que usas, correo | Para crear exploits dirigidos      | “Hay una actualización crítica de Outlook. Instálala aquí.”       |

---

### 🔍 ¿De dónde sacan estos datos los atacantes?

1. **Redes sociales públicas (Facebook, LinkedIn, Instagram)**
2. **Páginas web oficiales de empresas (quiénes somos, personal, correos)**
3. **Filtraciones de datos previas (por ejemplo, HaveIBeenPwned)**
4. **Google (técnica: Google Dorking)**
5. **Llamadas, encuestas falsas o interacciones casuales**

> Todo esto es parte de lo que se conoce como **OSINT (Open Source Intelligence)**: inteligencia de fuentes abiertas.

---

### 🛠️ ¿Cómo se “instala” un ataque de Ingeniería Social con datos?

Aunque no se instala como un software, **sí se puede preparar paso a paso**. Aquí te muestro cómo lo haría un atacante:

---

#### 🚨 Paso a paso del ataque:

1. **Reconocimiento (recolección de datos)**

   - El atacante busca a la víctima en redes sociales y páginas públicas.
   - Descubre que trabaja en una empresa y usa Office 365.

2. **Diseño del ataque**

   - Crea un correo falso que imita el estilo corporativo.
   - Usa el nombre del jefe, que vio en LinkedIn.

3. **Envío del ataque (phishing)**

   - Asunto: “Actualización obligatoria del sistema”
   - Cuerpo: “Hola, Gustavo. Por orden del Sr. Luis Romero, debes ingresar antes del mediodía y actualizar tu Office. Usa este enlace: `empresa-office365-login.com`”

4. **Acción de la víctima**

   - Gustavo confía, entra al enlace y coloca usuario y contraseña.

5. **Exfiltración**

   - El atacante ahora tiene acceso real y puede infiltrarse en la red empresarial.

---

### 🎯 Ejemplo completo fácil:

#### ✉️ **Correo falso bien diseñado:**

> **De:** [seguridad@empresa.com](mailto:seguridad@empresa.com)
>
> **Asunto:** Actividad sospechosa detectada en tu cuenta
>
> Hola Gustavo,
>
> Detectamos un intento de acceso desde Lima, Perú, que no coincide con tu patrón habitual.
> Por seguridad, **verifica tu identidad aquí:**
> 👉 \[[https://secure-empresa.com/login](https://secure-empresa.com/login)]
>
> Gracias,
>
> Equipo de Seguridad TI

##### ✅ ¿Por qué funciona?

- Muestra datos **geográficos reales**
- Usa tu **nombre**
- Tiene un **tono urgente**
- El sitio falso es **casi idéntico al real**

##### 🔓 ¿Qué pasa si haces clic?

- Entregas tu contraseña real.
- El atacante puede entrar al sistema empresarial.
- Se podrían robar datos, instalar malware o comprometer a toda la red.

---

### 🧩 ¿Cómo prevenirlo?

1. **Concientización constante** (tú y tu familia o equipo deben saber que esto existe).
2. **Verifica siempre los enlaces y remitentes.**
3. **No hagas clic en enlaces sospechosos, aunque parezcan confiables.**
4. **Activa el 2FA (autenticación de dos factores).**
5. **Desconfía de la urgencia o tono de miedo.**
6. **Nunca brindes datos por teléfono o correo no verificado.**

---

### 📈 Datos reales sobre ingeniería social:

- 🔐 El 91% de los ciberataques exitosos comienzan con **phishing**.
- 🧑‍💼 LinkedIn es la red más usada para **recopilar datos previos** (OSINT).
- 💸 El fraude de “el jefe pide una transferencia urgente” genera millones en pérdidas.
- 🧪 Las empresas que **capacitan en ingeniería social reducen en 70% los clics maliciosos**.

---

### ✅ Conclusión

| Aspecto                                         | Detalle                                                                    |
| ----------------------------------------------- | -------------------------------------------------------------------------- |
| **¿Qué son los datos de la ingeniería social?** | Información recolectada para engañar a una persona.                        |
| **¿Cómo se obtienen?**                          | Redes sociales, sitios públicos, correos filtrados.                        |
| **¿Cómo se usan?**                              | Para hacer ataques más creíbles (phishing, vishing, smishing, etc).        |
| **¿Cómo protegerse?**                           | Educación, análisis crítico, verificación, 2FA, herramientas antiphishing. |

---

[🔼](#índice)

---

## **1027. Metas de la ingeniería social**

> La ingeniería social no es solo engañar: tiene **metas claras** que dependen del **atacante**, la **víctima**, y el **entorno**.

---

### 🔎 ¿Qué es la Ingeniería Social?

Es una **técnica de manipulación psicológica** que permite a un atacante **engañar a una persona para que entregue información, acceda a sistemas o realice acciones perjudiciales**, sin necesidad de usar fuerza o tecnología sofisticada.

---

### 🎯 Principales Metas de la Ingeniería Social

| Meta                                          | Explicación fácil                                             | Ejemplo                                                               |
| --------------------------------------------- | ------------------------------------------------------------- | --------------------------------------------------------------------- |
| **1. Obtener información confidencial**       | Quieren datos que normalmente están protegidos.               | Contraseñas, números de tarjeta, correos, direcciones IP.             |
| **2. Obtener acceso a sistemas o redes**      | Engañar para que entregues acceso a tu computadora o sistema. | Un correo falso que pide iniciar sesión en “Outlook”.                 |
| **3. Instalar malware**                       | Hacer que descargues o ejecutes un archivo malicioso.         | “Descarga este CV en PDF”, pero es un archivo `.exe`.                 |
| **4. Desprestigiar a la empresa o persona**   | Afectar la reputación filtrando correos, imágenes o errores.  | Hackear y publicar mensajes ofensivos desde la cuenta de una empresa. |
| **5. Robo de dinero o extorsión**             | Sacar provecho económico directo o mediante chantaje.         | “Tenemos tus fotos, si no pagas en 24h las publicamos”.               |
| **6. Acceso físico o social a instalaciones** | Hacerse pasar por personal para entrar a un lugar.            | Fingir ser técnico de internet y entrar a una oficina.                |
| **7. Manipulación emocional o ideológica**    | Convencerte de apoyar una causa falsa, grupo o persona.       | “Estamos ayudando a niños con cáncer, dona aquí”.                     |

---

### 🧠 ¿Por qué son efectivas estas metas?

Porque **usan la psicología humana**:

- **Curiosidad**: “Mira esta foto tuya filtrada”.
- **Urgencia**: “Tu cuenta será eliminada hoy”.
- **Autoridad**: “Soy del banco, necesito verificar tus datos”.
- **Miedo**: “Tu dispositivo ha sido hackeado”.

---

### 💡 Ejemplo real y fácil de entender:

#### 🎯 Meta: **Robo de información confidencial**

**Situación**:

Gustavo trabaja en una empresa de desarrollo web. Un día, recibe este correo:

---

**✉️ Correo recibido:**

> De: [soporte@googlecorporativo.com](mailto:soporte@googlecorporativo.com)
>
> Asunto: \[URGENTE] Verifica tu cuenta de Google Workspace
>
> Hola Gustavo,
>
> Detectamos actividad sospechosa en tu cuenta `gustavo@empresa.com`.
>
> Por seguridad, verifica tu identidad aquí:
> 👉 [Verificar ahora](http://google-seguridad-verificacion.com)
>
> Saludos,
>
> Equipo de Soporte TI

---

**¿Qué pasó?**

- La **meta** del atacante es **robar las credenciales de Gustavo**.
- El atacante ya sabía su **correo laboral** (lo encontró en LinkedIn o en la web de la empresa).
- Si Gustavo hace clic y pone su contraseña, el atacante entra al sistema.

---

### 🛠️ ¿Cómo se “instala” una campaña de ingeniería social?

Aunque no se instala como un software, **sí hay una preparación previa**:

#### Paso a paso de la ejecución:

1. **Investigación previa** (OSINT):

   Encuentran información sobre Gustavo y la empresa donde trabaja.

2. **Definir la meta**:

   Robar credenciales de acceso a Google Workspace.

3. **Diseño del ataque**:

   Crear una página falsa y un correo convincente.

4. **Envío del ataque**:

   Enviar el correo al objetivo.

5. **Exfiltración**:

   Cuando Gustavo ingresa sus datos, estos se almacenan en el servidor del atacante.

---

### 🧱 ¿Cómo protegerse?

| Medida                                                       | Explicación                                                            |
| ------------------------------------------------------------ | ---------------------------------------------------------------------- |
| **Desconfiar de correos urgentes o con enlaces sospechosos** | Aunque parezcan reales, verifica su origen.                            |
| **Activar 2FA (autenticación en dos pasos)**                 | Aunque roben tu contraseña, no podrán entrar sin tu código extra.      |
| **Verificar enlaces**                                        | Pasa el cursor sobre el enlace antes de hacer clic.                    |
| **Capacitación constante**                                   | Mientras más sepas cómo actúan los atacantes, mejor podrás defenderte. |

---

### ✅ Conclusión

| Elemento                       | Detalle                                                               |
| ------------------------------ | --------------------------------------------------------------------- |
| **¿Qué buscan los atacantes?** | Información, acceso, dinero, control o daño.                          |
| **¿Cómo lo logran?**           | Usando ingeniería social: engaño, manipulación y persuasión.          |
| **¿Cómo lo evitamos?**         | Educación, sentido crítico, verificación y herramientas de seguridad. |

---

### 🧪 Ejemplo final completo (todo junto):

**Escenario completo:**

- **Meta del atacante**: Instalar un malware para controlar remotamente tu equipo.

- **Paso 1 (OSINT)**: Sabe que eres desarrollador por tu LinkedIn.

- **Paso 2 (Engaño)**: Te escribe desde una cuenta falsa:

  > “Hola Gustavo, estoy buscando un desarrollador freelance para un sitio de e-commerce. Adjunto te envío los requerimientos técnicos. Espero tu pronta respuesta.”

- **Adjunto**: un archivo llamado `proyecto_requisitos.pdf.exe`.

- **Resultado si haces clic**: el archivo instala un troyano que da acceso remoto al atacante.

---

[🔼](#índice)

---

## **1028. Principios de la ingeniería social según Kevin Mitnick y Robert Cialdini**

### Según **Kevin Mitnick** (hacker) y **Robert Cialdini** (psicólogo experto en persuasión)

---

### 🧔🏻‍♂️ ¿Quiénes son ellos?

| Persona             | Rol                               | Aportación                                                                                                                   |
| ------------------- | --------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| **Kevin Mitnick**   | Ex hacker, consultor en seguridad | Mostró cómo manipular a las personas para obtener acceso sin usar exploits técnicos. Autor de _“El arte del engaño”_.        |
| **Robert Cialdini** | Psicólogo social                  | Describió 6 principios de persuasión que los atacantes usan para manipular el comportamiento humano. Autor de _“Influence”_. |

---

### 🎯 Objetivo de la Ingeniería Social

Manipular a las personas para que **entreguen información**, **accedan a sistemas** o **realicen acciones perjudiciales**, **sin darse cuenta**.

---

### 📜 6 Principios de Persuasión según **Robert Cialdini**

Estos son **técnicas psicológicas** muy usadas en ingeniería social:

| Principio                      | Explicación                                                           | Ejemplo usado por un atacante                                                               |
| ------------------------------ | --------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| ✅ **Reciprocidad**            | Si alguien te da algo, te sientes obligado a devolver el favor.       | El atacante te ofrece un recurso gratuito (ebook, herramienta), y luego pide tus datos.     |
| 📈 **Compromiso y coherencia** | Las personas quieren ser coherentes con lo que ya dijeron o hicieron. | Te hacen aceptar una pequeña tarea (responder una encuesta), luego piden algo más sensible. |
| 🌟 **Aprobación social**       | Las personas confían en lo que otros hacen.                           | “Miles de personas ya se registraron, ¿tú aún no?”                                          |
| 👮 **Autoridad**               | Seguimos a figuras de autoridad.                                      | El atacante finge ser del banco, policía o jefe de IT.                                      |
| ❤️ **Simpatía**                | Es más fácil decir que sí a alguien que te agrada.                    | Se hacen pasar por alguien amable, confiado o similar a ti.                                 |
| 🚨 **Escasez**                 | Valoramos más lo que es limitado.                                     | “Solo quedan 3 cuentas gratuitas, regístrate ahora.”                                        |

---

### 🔐 Principios de Ingeniería Social según **Kevin Mitnick**

Él se enfocó más en cómo se **obtiene la confianza de la víctima**:

| Principio                              | Explicación clara                                        | Ejemplo                                                              |
| -------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------------------- |
| 🎭 **Pretexting**                      | Crear una historia o identidad falsa para lograr acceso. | Fingir ser técnico de soporte de tu empresa.                         |
| 🧩 **Gathering (recolección de info)** | Investigar previamente a la víctima.                     | Ver tus redes sociales, email de trabajo, costumbres.                |
| 🪤 **Explotación de confianza**        | Una vez que confías, es fácil que obedezcas.             | “Gustavo, ¿me puedes reenviar esa clave de Wi-Fi otra vez?”          |
| 🧨 **Desarme psicológico**             | Hacer que la víctima baje la guardia.                    | Usar humor, urgencia o emociones para distraerte.                    |
| 🧠 **Técnicas no técnicas**            | No siempre se necesita tecnología, solo conversación.    | Llamar por teléfono y convencer al recepcionista para que dé acceso. |

---

### 🛠️ ¿Cómo se "instalan" o aplican estos principios en un ataque?

No se “instalan” como un software, sino que se **implementan estratégicamente** en la comunicación, paso a paso:

1. **Investigación previa (OSINT)**

   Buscar datos públicos de la víctima (LinkedIn, Twitter, etc.)

2. **Diseño del ataque**

   Se arma un correo, llamada o mensaje usando 2 o más principios de Cialdini.

3. **Ejecución del ataque**

   Se hace contacto con la víctima: por llamada, email, mensaje de WhatsApp, etc.

4. **Ganar confianza y explotar**

   Se obtiene lo que se busca: contraseñas, acceso físico, instalación de malware, etc.

---

### 🧪 Ejemplo completo y fácil de entender

#### 🎯 Escenario: Gustavo trabaja en una empresa de desarrollo web.

Un atacante quiere robar tus credenciales de GitHub.

#### 👣 Paso a paso con los principios:

1. **Investigación previa** (Kevin Mitnick):

   El atacante encuentra tu LinkedIn y sabe que usas GitHub.

2. **Diseña un mensaje (Pretexting + Cialdini):**

> **Correo falso recibido**
>
> De: [soporte@github-soporte.com](mailto:soporte@github-soporte.com)
>
> Asunto: \[URGENTE] Seguridad: actividad sospechosa en tu cuenta
>
> Hola Gustavo,
>
> Detectamos un intento de ingreso desde una IP en China.
>
> Por tu seguridad, debes cambiar tu contraseña antes de 24 horas o tu cuenta será suspendida.
>
> [🔒 Cambiar contraseña ahora](http://github-seguridad-reset.com)

🎯 Principios usados:

- **Autoridad**: fingen ser GitHub.
- **Urgencia (Escasez)**: “hazlo en 24h o perderás acceso”.
- **Reciprocidad**: “te estamos protegiendo, haz tu parte”.

3. **Gustavo entra al enlace falso y escribe su usuario y contraseña.**

4. **El atacante entra al GitHub real y compromete sus repositorios.**

---

### 🔐 ¿Cómo evitar caer en estos ataques?

| Acción defensiva                                   | Por qué sirve                                     |
| -------------------------------------------------- | ------------------------------------------------- |
| **No confiar en urgencias ni enlaces sospechosos** | Son técnicas de manipulación emocional.           |
| **Verifica la dirección del remitente**            | Revisa si es exactamente igual a la oficial.      |
| **Activa 2FA**                                     | Incluso si roban tu contraseña, no podrán entrar. |
| **Capacítate**                                     | Entender estos principios te ayuda a detectarlos. |

---

### ✅ Conclusión

| Concepto            | Resumen                                                                                     |
| ------------------- | ------------------------------------------------------------------------------------------- |
| **Kevin Mitnick**   | Muestra cómo se construyen ataques con manipulación social.                                 |
| **Robert Cialdini** | Explica los principios de persuasión que se usan en esos ataques.                           |
| **Juntos**          | Dan la fórmula completa: investigar, crear una historia creíble y manipular con psicología. |

---

[🔼](#índice)

---

## **1029. Principios de la ingeniería social a detalle**

La **ingeniería social** es una forma de manipulación psicológica que **engaña a las personas para que entreguen información confidencial** o realicen acciones que comprometen la seguridad.

---

### 🧠 ¿Qué son los principios de la ingeniería social?

Son **técnicas psicológicas** que aprovechan el comportamiento humano para manipularlo y lograr un objetivo. Los más conocidos vienen de:

- 🧔 **Kevin Mitnick** – Ex hacker y autor del libro _El arte del engaño_.
- 👨‍🏫 **Robert Cialdini** – Psicólogo social que estudió cómo persuadir a las personas.

---

### 📚 Principios de Ingeniería Social según Kevin Mitnick

| Principio                              | Explicación fácil                                       | Ejemplo claro                                                   |
| -------------------------------------- | ------------------------------------------------------- | --------------------------------------------------------------- |
| 🎭 **Pretexting (pretextos)**          | Crear una historia falsa para justificar una acción.    | Fingir ser del banco para pedir tu DNI por teléfono.            |
| 🧩 **Gathering (recolección de info)** | Reunir información antes del ataque.                    | Ver tus redes sociales para saber tu cargo, correos, gustos.    |
| 🤝 **Explotar la confianza**           | Ganarse tu confianza para que no sospeches.             | Hablar contigo por semanas antes de pedirte un favor.           |
| 🧠 **Desarme psicológico**             | Hacerte bajar la guardia con humor, presión o simpatía. | “No te preocupes, esto lo hace todo el mundo.”                  |
| 📞 **Ingeniería no técnica**           | No se necesita hackear computadoras, solo hablar.       | Llamar a la oficina y decir: “Soy el técnico, necesito acceso”. |

---

### 🎯 Principios de Persuasión según Robert Cialdini

| Principio                      | Cómo funciona                                                   | Ejemplo en ataque                                             |
| ------------------------------ | --------------------------------------------------------------- | ------------------------------------------------------------- |
| 🔄 **Reciprocidad**            | Si alguien te da algo, te sientes obligado a devolver el favor. | El atacante te envía un regalo digital, luego pide un favor.  |
| ✅ **Compromiso y coherencia** | La gente quiere actuar de forma coherente con lo que ya hizo.   | Aceptas una pequeña encuesta, luego te piden más información. |
| 👥 **Aprobación social**       | Las personas siguen a la mayoría.                               | “Todos tus colegas ya lo hicieron, solo faltas tú.”           |
| 👮 **Autoridad**               | Seguimos órdenes de figuras de poder.                           | El atacante se hace pasar por tu jefe o un policía.           |
| ❤️ **Simpatía**                | Hacemos cosas por personas que nos agradan.                     | Fingen tener tus mismos gustos o forma de hablar.             |
| ⏳ **Escasez**                 | Valoramos más lo que es limitado o urgente.                     | “Solo hoy puedes acceder a este link.”                        |

---

### 🛠️ ¿Cómo se "instalan" o aplican estos principios en un ataque?

Aunque no se **instalan como software**, sí se implementan de forma **estratégica en la comunicación** del atacante. Aquí te muestro cómo:

---

#### 🪜 Etapas de un ataque de ingeniería social (con principios aplicados)

| Etapa           | Acción del atacante                                  | Principios aplicados            |
| --------------- | ---------------------------------------------------- | ------------------------------- |
| 1. Recolección  | Investiga tu correo, cargo, redes sociales.          | (Gathering)                     |
| 2. Preparación  | Crea un correo o historia creíble.                   | Pretexting, Autoridad           |
| 3. Contacto     | Te envía mensaje convincente.                        | Urgencia, Escasez, Reciprocidad |
| 4. Manipulación | Te hace actuar: descargar, responder, instalar algo. | Confianza, Compromiso           |
| 5. Explotación  | Usa la info o el acceso que obtuvo.                  | Sin técnicas técnicas           |

---

### ✅ Ejemplo completo y simple

#### 🎯 Escenario:

Gustavo trabaja como desarrollador en una empresa de tecnología.

El atacante quiere que Gustavo **abra un archivo malicioso para obtener acceso a su computadora**.

---

#### 👣 Paso a paso:

##### 🧩 1. Recolección (Gathering)

El atacante busca en tu LinkedIn y ve que trabajas con **React y Node.js**. También encuentra tu correo profesional en tu portafolio.

##### 🎭 2. Pretexting

El atacante crea una identidad falsa: “Carlos García – Reclutador de empresa X”.

##### 📧 3. Primer contacto

Te envía este mensaje:

> **Asunto:** Oportunidad para Dev Senior – React + Node
>
> Hola Gustavo,
>
> Vi tu perfil y me pareció ideal para un proyecto freelance.
>
> Te adjunto los requerimientos en un archivo PDF para que los revises.
>
> \[🔗 Requisitos_Carlos.pdf.exe]
>
> ¡Espero que te interese!
>
> Saludos,
> Carlos García

##### 🎯 4. Principios aplicados

- **Simpatía**: te habla amablemente.
- **Reciprocidad**: te ofrece una “oportunidad laboral”.
- **Autoridad**: se presenta como reclutador.
- **Urgencia**: insinúa que es por tiempo limitado.
- **Pretexting**: finge que el archivo es inofensivo.

##### 💣 5. Resultado

El archivo no es un PDF: es un **.exe malicioso** que al ejecutarse, da control remoto de tu PC al atacante (ej. con un _reverse shell_).

---

### 🔐 ¿Cómo defenderse?

| Acción defensiva                           | Beneficio                           |
| ------------------------------------------ | ----------------------------------- |
| Verifica remitente y extensión de archivos | .pdf.exe es peligroso               |
| No confíes en oportunidades no solicitadas | Puede ser phishing                  |
| Usa antivirus y sandbox                    | Detecta malware antes de ejecutarlo |
| Capacitación continua                      | Reconocerás patrones de ataque      |

---

### 📌 Conclusión

| Principio       | Clave para recordar                                           |
| --------------- | ------------------------------------------------------------- |
| Kevin Mitnick   | Demuestra que no se necesita hackear máquinas, solo personas. |
| Robert Cialdini | Enseña cómo manipular con psicología simple.                  |
| Aplicación      | Combinar varios principios hace ataques más efectivos.        |
| Defensa         | Conocimiento, sospecha lógica y herramientas de protección.   |

---

[🔼](#índice)

---

## **1030. Perfil del ingeniero(a) social**

### 🧠 ¿Qué es el perfil del ingeniero(a) social?

Un **ingeniero social** es una persona que **engaña y manipula psicológicamente** a otras para obtener información, acceso o acciones que no deberían conceder.

🔑 A diferencia del hacker técnico (que rompe sistemas), el ingeniero social **rompe la confianza de las personas**.

---

### 🧬 Características del perfil de un ingeniero(a) social

| Característica                | Explicación fácil                                                     | Ejemplo                                                                  |
| ----------------------------- | --------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| 🕵️‍♂️ Observador                 | Analiza lenguaje corporal, emociones y comportamientos.               | Nota que dudas en una llamada y aprovecha para presionarte.              |
| 🧠 Inteligente emocionalmente | Sabe cuándo presionar o agradar según tu tono o actitud.              | Cambia de tono: amable o autoritario, según tu reacción.                 |
| 🗣️ Comunicador hábil          | Usa palabras precisas, lenguaje técnico o coloquial según la víctima. | Si eres técnico, habla como un desarrollador; si no, se vuelve informal. |
| 📚 Buen investigador          | Usa Google, redes sociales, y buscadores OSINT para recolectar datos. | Busca tu correo en LinkedIn, nombre de tu jefe, tecnologías que usas.    |
| 🎭 Actor o actriz             | Puede fingir ser alguien más de forma convincente.                    | Se hace pasar por personal de TI, policía o cliente.                     |
| 🧩 Creativo e improvisador    | Siempre tiene una salida cuando las cosas no salen como quiere.       | Si fallas en abrir el archivo, te envía otro con una excusa diferente.   |
| 🧪 Estratega                  | Planea su ataque en fases, con lógica y control.                      | Investiga hoy, contacta mañana, ejecuta en una semana.                   |
| 🧲 Persuasivo                 | Sabe cómo convencer sin que sospeches.                                | Usa principios de Cialdini como urgencia, simpatía o autoridad.          |

---

### 👶 ¿Cómo se "instala" o forma un ingeniero social?

Obviamente no se **instala como un software**, pero un atacante desarrolla estas habilidades con el tiempo:

| "Instalación"                            | Detalle                                                                |
| ---------------------------------------- | ---------------------------------------------------------------------- |
| 🧠 Conocimiento psicológico              | Aprende sobre comportamiento humano, sesgos cognitivos y manipulación. |
| 🧑‍💻 Formación técnica (opcional)          | Aunque no es obligatorio, muchos ingenieros sociales saben algo de TI. |
| 📖 Lectura de libros y casos reales      | Como _El arte del engaño_ (Kevin Mitnick) o _Influence_ (Cialdini).    |
| 👀 Práctica en OSINT y redes sociales    | Aprende a recolectar información sin que lo descubran.                 |
| 🎮 Entrenamiento en entornos controlados | Plataformas como Hack The Box, TryHackMe o simulaciones corporativas.  |

---

### 🪜 Etapas del ataque del ingeniero(a) social

1. **Investigación** (OSINT): Busca tu información pública.
2. **Preparación del pretexto**: Inventa una historia para contactarte.
3. **Primer contacto**: Te escribe, llama o aborda.
4. **Manipulación**: Usa principios de persuasión.
5. **Explotación**: Logra que hagas lo que quiere (clic, envío de datos, acceso).
6. **Salida limpia**: Borra huellas o sigue contactándote para más.

---

### 🛑 ¿Cómo reconocer un posible ingeniero(a) social?

| Comportamiento sospechoso                        | Qué significa                                          |
| ------------------------------------------------ | ------------------------------------------------------ |
| Pide información urgente sin justificación clara | Podría ser manipulación por urgencia.                  |
| Se presenta como autoridad sin medios oficiales  | Puede estar fingiendo.                                 |
| Usa tecnicismos para intimidar o impresionar     | Quiere hacerte sentir ignorante para que obedezcas.    |
| Cambia de tono fácilmente                        | Está adaptándose a tu actitud.                         |
| Ofrece regalos o premios inesperados             | Probablemente quiere que hagas clic en algo malicioso. |

---

### ✅ Ejemplo completo realista

#### 🧪 Escenario:

Gustavo trabaja en el área de TI de una universidad.

El atacante quiere acceso al sistema de correo institucional.

---

#### 🧩 Etapa 1: Recolección (OSINT)

- El atacante encuentra en LinkedIn que Gustavo trabaja en TI.
- En la web de la universidad ve correos de alumnos: `usuario@uni.edu.pe`
- Detecta que se usa **Outlook Web Access (OWA)**.

---

#### 🎭 Etapa 2: Pretexto

Crea un correo falso:

**De:** [soporte.ti@uni-edu.pe](mailto:soporte.ti@uni-edu.pe)
**Asunto:** Urgente – Verificación de bandeja por mantenimiento
**Cuerpo:**

> Estimado Gustavo,
>
> Detectamos fallos en tu acceso a la plataforma. Para evitar pérdida de correos, inicia sesión en el siguiente enlace:
>
> \[🔗 [https://outlook-uni-webapp.verifcloud.co/login](https://outlook-uni-webapp.verifcloud.co/login)]
>
> Soporte Técnico – TI UNIEP

---

#### 🎯 Etapa 3: Principios aplicados

| Principio         | Aplicación                                      |
| ----------------- | ----------------------------------------------- |
| Autoridad         | Se hace pasar por Soporte Técnico.              |
| Urgencia          | “Evitar pérdida de correos”.                    |
| Reciprocidad      | Te ayuda a “no perder correos”.                 |
| Aprobación social | “Esto se está haciendo con todos los usuarios”. |

---

#### ☠️ Etapa 4: Resultado

- La página falsa parece idéntica a la real.
- Gustavo introduce su usuario y contraseña institucional.
- El atacante recibe las credenciales en su panel.
- Luego las usa para enviar campañas de phishing internas o robar información académica.

---

### 🔐 ¿Cómo protegerte del ingeniero(a) social?

| Medida defensiva                              | Ejemplo                                               |
| --------------------------------------------- | ----------------------------------------------------- |
| 🧠 Desconfía de correos urgentes sin contexto | Revisa la dirección real del remitente.               |
| 🔒 Usa doble factor (2FA) en todo             | Aunque roben tu clave, no podrán entrar.              |
| 🧼 No publiques información laboral sensible  | Evita mostrar tu rol técnico en redes públicas.       |
| 🛡️ Capacitación frecuente                     | Saber reconocer señales de ingeniería social.         |
| 🕵️ Verifica con una llamada real              | Antes de seguir instrucciones de correos sospechosos. |

---

### 📌 Conclusión

| Elemento   | Resumen                                                         |
| ---------- | --------------------------------------------------------------- |
| Qué es     | El ingeniero social manipula a personas, no sistemas.           |
| Cómo actúa | Recolecta datos, crea un pretexto y persuade para obtener algo. |
| Perfil     | Observador, persuasivo, buen comunicador y estratega.           |
| Defensa    | Educación, sentido crítico y medidas de seguridad.              |

---

[🔼](#índice)

---

## **1031. Tipos de ingeniería social: basada en humanos**

### 🧠 ¿Qué es la ingeniería social basada en humanos?

Es el tipo de ataque donde el **vector principal no es el sistema informático, sino la persona**. El atacante se enfoca en **manipular emocional y cognitivamente al ser humano** para obtener acceso, información o ejecutar acciones perjudiciales.

---

### 🧩 Tipos de ingeniería social basada en humanos

Aquí tienes los **más comunes**, explicados con lenguaje claro y ejemplos fáciles:

| Tipo                                    | Explicación fácil                                                         | Ejemplo sencillo                                                                |
| --------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| **Pretexting (pretexto)**               | El atacante se inventa una historia para justificar su acceso o pregunta. | Se hace pasar por técnico de TI que necesita tu clave para “migrar tu correo”.  |
| **Phishing presencial**                 | Te aborda en persona con una excusa convincente.                          | Llega a tu oficina diciendo que viene del proveedor de internet a revisar algo. |
| **Vishing (phishing por voz)**          | Llamada telefónica fingiendo autoridad o urgencia.                        | Te llama “el banco” diciendo que tu tarjeta fue bloqueada y necesita tus datos. |
| **Tailgating (seguimiento físico)**     | Se cuela detrás de alguien para ingresar a una zona restringida.          | Entra contigo a la empresa justo cuando abres la puerta con tu tarjeta.         |
| **Quid pro quo**                        | Ofrece algo a cambio de tu ayuda o información.                           | “Te ayudo con tu computadora, solo necesito que instales este software”.        |
| **Shoulder surfing (mirar por encima)** | Observa lo que haces sin que te des cuenta.                               | Ve tu contraseña mientras la escribes en un cajero o PC.                        |
| **Dumpster diving**                     | Revisa la basura en busca de información útil.                            | Encuentra hojas impresas con contraseñas o contratos en papel.                  |
| **Impersonation (suplantación)**        | Finge ser alguien de confianza.                                           | Se hace pasar por tu jefe o compañero para pedirte acceso a algo.               |

---

### 🔄 ¿Cómo se "instala" o prepara este tipo de ataque?

Aunque no se “instala” como un software, el atacante sí necesita **preparación y estrategia** antes de ejecutar un ataque basado en humanos:

| Etapa                                 | Acción del atacante                                                               |
| ------------------------------------- | --------------------------------------------------------------------------------- |
| 🔍 Recolección de información (OSINT) | Busca nombres, cargos, correos, jerarquías, horarios, cultura organizacional.     |
| 🧠 Diseño del pretexto                | Crea una historia creíble que se ajuste a la víctima y su entorno.                |
| 🎭 Ensayo y actitud                   | Practica cómo hablar, vestirse, qué lenguaje usar.                                |
| 🎯 Ejecución                          | Se presenta con confianza, manipula emociones y explota vulnerabilidades humanas. |

---

### 🔐 ¿Por qué estos ataques funcionan tan bien?

Porque **aprovechan elementos humanos universales**:

| Elemento      | Cómo lo explotan                                      |
| ------------- | ----------------------------------------------------- |
| Confianza     | Usan logos, uniformes, o nombres conocidos.           |
| Autoridad     | Se hacen pasar por jefes, bancos, técnicos.           |
| Urgencia      | Amenazan con consecuencias si no respondes rápido.    |
| Miedo o culpa | “Tu cuenta ha sido bloqueada” o “puede ser tu culpa”. |
| Simpatía      | Parecen agradables, atentos y amigables.              |

---

### ✅ Ejemplo completo realista

#### 🎯 Objetivo:

Acceder a una red corporativa **sin hackear nada técnico**.

#### 🏢 Escenario:

Empresa de seguros. La víctima: recepcionista del área administrativa.

---

#### 🔍 Fase 1: Recolección (OSINT)

El atacante:

- Encuentra el nombre de la empresa y su ubicación.
- Ve en LinkedIn que hay un recepcionista llamado **Carlos**.
- Descubre que la empresa usa impresoras en red marca **Xerox**.

---

#### 🎭 Fase 2: Preparación del ataque

El atacante:

- Compra una camisa con logo falso de "Soporte Xerox".
- Llega con una carpeta de trabajo falsa y un pendrive.
- Se aprende este guión:

> "Hola, vengo de Xerox. Me dijeron que el área de administración tenía problemas con la impresora de red. Solo necesito conectarme 5 minutos desde alguna máquina local."

---

#### 👣 Fase 3: Ejecución (Tailgating + pretexto)

1. Se cuela con un grupo de empleados que entra con tarjetas.
2. Se dirige a Carlos (recepcionista).
3. Le habla con seguridad y lenguaje técnico amigable.
4. Carlos, confiando, lo lleva a un escritorio libre.
5. El atacante conecta su pendrive, ejecuta una **reverse shell** camuflada como “driver de impresora”.
6. Ahora tiene acceso a la red desde fuera.

---

#### 🧨 Resultado

En 15 minutos, sin usar fuerza ni exploits, el atacante logró:

- Una sesión activa en la red.
- Credenciales almacenadas en el navegador.
- Acceso a carpetas internas.

---

### 🛡️ ¿Cómo prevenir estos ataques?

| Medida                                | Descripción clara                                      |
| ------------------------------------- | ------------------------------------------------------ |
| 🧠 Capacitación continua              | Enseñar al personal sobre estos tipos de manipulación. |
| 🔐 Doble verificación                 | Nunca confiar solo por una historia convincente.       |
| 🚫 No usar PC pública sin supervisión | Ni dejar puertas abiertas a desconocidos.              |
| 🪪 Identificación obligatoria          | Todo visitante debe estar registrado y acompañado.     |
| 🧹 Shredder + limpieza digital        | No dejar papeles sensibles ni archivos descargados.    |

---

### 📌 Conclusión

| Punto clave      | Resumen                                                                       |
| ---------------- | ----------------------------------------------------------------------------- |
| Qué es           | Ingeniería social basada en humanos manipula personas, no máquinas.           |
| Tipos comunes    | Pretexting, vishing, tailgating, impersonation, shoulder surfing, etc.        |
| Cómo se prepara  | Observación, ensayo, lenguaje persuasivo, credibilidad.                       |
| Ejemplo realista | Falso técnico ingresa a la empresa sin hackear nada.                          |
| Defensa          | Capacitación, verificación de identidades, protocolos físicos y psicológicos. |

---

[🔼](#índice)

---

## **1032. Tipos de ingeniería social: basada en computadoras**

### 🧠 ¿Qué es la ingeniería social basada en computadoras?

Es un tipo de ataque donde el atacante **utiliza medios digitales o tecnológicos (como correos, sitios web, archivos, USBs, redes Wi-Fi)** para engañar a la víctima y lograr que ejecute acciones que comprometan su sistema, datos o seguridad.

🔎 **En resumen:** El atacante usa _software_ o _plataformas digitales_ como vehículo del engaño, en lugar de interactuar directamente con la persona.

---

### 🧩 Tipos de ingeniería social basada en computadoras

| Tipo                  | ¿Qué es?                                                       | Ejemplo claro                                                              |
| --------------------- | -------------------------------------------------------------- | -------------------------------------------------------------------------- |
| **Phishing**          | Correos falsos que simulan ser de bancos, redes sociales, etc. | Un correo del "BCR" que te pide actualizar tus datos bancarios.            |
| **Spear Phishing**    | Phishing personalizado con información específica.             | Un correo que te llama por tu nombre y menciona tu puesto.                 |
| **Smishing**          | Phishing por SMS o WhatsApp.                                   | Recibes un SMS: “Tu cuenta fue bloqueada. Entra aquí \[link]”.             |
| **Malware camuflado** | Archivos adjuntos o links que instalan malware.                | Descargas un archivo Word con una macro maliciosa.                         |
| **USB baiting**       | Te dejan un USB infectado para que lo conectes.                | Encuentras un USB en el baño que tiene malware y lo insertas en tu laptop. |
| **Fake Login Pages**  | Páginas falsas que imitan plataformas reales.                  | Entras a "faceb00k.com" (con doble cero), y entregas tu contraseña real.   |
| **Clickjacking**      | Engañan tu clic para hacer algo diferente.                     | Das clic en “Play video” pero estás aprobando permisos de administrador.   |
| **Scareware**         | Mensajes falsos de virus para hacerte descargar algo.          | “¡Tu PC está infectada! Descarga este antivirus gratis.”                   |

---

### 🧠 ¿Cómo se “instala” o prepara el ataque?

Aunque no se instala como una app, **el atacante sí configura** herramientas para montar el engaño. Aquí algunos pasos generales:

#### 🔧 Herramientas comunes del atacante

| Herramienta                             | Para qué sirve                                           |
| --------------------------------------- | -------------------------------------------------------- |
| 🛠️ **SET (Social Engineering Toolkit)** | Crear sitios falsos, correos engañosos, USBs infectados. |
| 🐍 **Beef XSS**                         | Para ejecutar ataques desde navegadores vulnerables.     |
| 🐙 **Evilginx**                         | Clonar sitios y robar sesiones incluso con 2FA.          |
| 💻 **Kali Linux**                       | Sistema usado para montar campañas de ingeniería social. |
| 🐬 **Maltego**                          | Investigar a la víctima para personalizar los ataques.   |

---

### ✅ Ejemplo completo realista

#### 🎯 Objetivo:

Robar credenciales de inicio de sesión de un usuario de correo corporativo usando un ataque de **spear phishing** con sitio falso.

---

#### 🔍 Paso 1: Recolección de información

El atacante:

- Encuentra el dominio de la empresa: `empresa.com.pe`.
- Descubre en LinkedIn que hay una persona llamada **Lucía Gómez**, asistente administrativa.
- Ve que usan **Outlook Web Access (OWA)** como correo online.

---

#### 🧰 Paso 2: Preparación del ataque

El atacante:

1. Usa **Evilginx** para clonar el sitio de Outlook:

   - Crea una copia exacta en `out1ook-login.com` (parecido al original).

2. Configura un servidor web con HTTPS falso.

3. Redacta un correo personalizado:

   ```
   De: IT Soporte <soporte@empresa.com.pe>
   Asunto: Actualización obligatoria de correo

   Estimada Lucía,

   Como parte del mantenimiento del sistema, por favor actualiza tu sesión ingresando nuevamente a tu correo desde el siguiente enlace:

   👉 https://out1ook-login.com/actualiza

   Saludos,
   Equipo de Soporte TI
   ```

---

#### 🖱️ Paso 3: Ejecución

- Lucía abre el correo, no sospecha porque:

  - El dominio se parece.
  - El mensaje está bien escrito.
  - Usa el mismo lenguaje que su empresa.

- Ingresa su usuario y contraseña.
- El atacante **captura sus credenciales en tiempo real** y redirige a Lucía al sitio real (para que no sospeche).

---

#### 🎯 Resultado

- El atacante ahora puede entrar al correo real de Lucía.
- Desde ahí, puede:

  - Leer correos internos.
  - Enviar ataques desde su cuenta.
  - Solicitar transferencias internas.
  - Robar archivos adjuntos.

---

### 🛡️ ¿Cómo protegerse de estos ataques?

| Medida                            | ¿Por qué funciona?                                               |
| --------------------------------- | ---------------------------------------------------------------- |
| 🧠 Educación y conciencia         | Entender estos ataques ayuda a detectarlos.                      |
| 🔍 Revisar la URL siempre         | Sitios falsos usan letras extrañas: `goog1e.com`.                |
| 🔐 Activar 2FA                    | Aunque roben tu clave, no podrán ingresar sin el segundo factor. |
| 📧 Desconfiar de correos urgentes | “Actualiza ya” o “estás en peligro” son señales típicas.         |
| 🛑 No abrir archivos desconocidos | Ni PDFs, ni Word, ni Excel si vienen sin contexto.               |
| 🧼 Escanear USBs antes de usarlos | Evita que te infecten con autorun o keyloggers.                  |

---

### 📌 Conclusión

| Punto clave        | Resumen                                                        |
| ------------------ | -------------------------------------------------------------- |
| ¿Qué es?           | Ataques digitales que manipulan al usuario desde la pantalla.  |
| ¿Qué usan?         | Correos, links, sitios falsos, archivos, dispositivos.         |
| ¿Qué herramientas? | SET, Evilginx, Maltego, BeEF, Kali, etc.                       |
| ¿Cómo prevenir?    | Educación, 2FA, análisis de enlaces, antivirus, sentido común. |

---

[🔼](#índice)

---

## **1033. Taxonomía de la ingeniería social: marco de ataque**

### 🧠 ¿Qué es la Taxonomía de la Ingeniería Social?

La **taxonomía** es una forma de **clasificar** o **organizar sistemáticamente** los diferentes elementos de la ingeniería social según su **naturaleza**, **fase de ataque**, y **canal de ataque**. En este caso, hablaremos de ella como **un marco estructurado para entender cómo los ataques de ingeniería social ocurren paso a paso**.

---

### 🧱 ¿Qué es un Marco de Ataque?

Un **marco de ataque** es una **estructura lógica** que permite identificar las **etapas** y **tipos de herramientas o técnicas** usadas por un atacante para engañar a una víctima.

Uno de los marcos más conocidos es el que divide los ataques en:

1. **Preparación**
2. **Interacción**
3. **Explotación**
4. **Retiro**

---

### 📊 Taxonomía de la Ingeniería Social (simplificada)

| Etapa del ataque                          | Subetapas / Técnicas                                      | Ejemplo                                           |
| ----------------------------------------- | --------------------------------------------------------- | ------------------------------------------------- |
| **1. Investigación (Reconocimiento)**     | - OSINT<br>- Google Dorking<br>- Redes Sociales           | Buscar en LinkedIn quién es el jefe de finanzas.  |
| **2. Preparación**                        | - Clon de sitio web<br>- Falsificación de correo          | Crear `micuenta-empresaa.com` para engañar.       |
| **3. Engaño**                             | - Phishing<br>- Vishing<br>- USB infectado                | Enviar un correo urgente con malware adjunto.     |
| **4. Manipulación emocional**             | - Autoridad<br>- Miedo<br>- Urgencia                      | “Tu cuenta será bloqueada si no haces clic aquí”. |
| **5. Explotación (acción de la víctima)** | - Clic en enlace<br>- Ingreso de datos<br>- Abrir archivo | Víctima entrega su contraseña en un sitio falso.  |
| **6. Recolección de información**         | - Robo de credenciales<br>- Keylogging                    | Atacante captura usuario y clave.                 |
| **7. Retirada / Eliminación de rastros**  | - Borrado de logs<br>- Uso de proxy o VPN                 | El atacante se desconecta sin dejar huella.       |

---

### 🛠️ ¿Cómo se "instala" o aplica este marco?

Este marco no se **instala como software**, sino que se **usa como guía mental o de planificación** por parte de los atacantes para estructurar sus ataques, o por parte de defensores para **prevenir y detectar** actividades maliciosas.

> 💡 También puede implementarse como parte de un entrenamiento o simulación de ataques en equipos de ciberseguridad.

---

### 📚 Ejemplo real completo: Ataque usando el marco

#### 🎯 Objetivo: Obtener las credenciales del jefe de recursos humanos de una empresa.

---

#### 🧩 1. Investigación (Reconocimiento)

- El atacante busca en la web el dominio `empresaRRHH.com`.
- Encuentra en LinkedIn que la jefa de RRHH se llama **Carla Ríos**.
- Ve que la empresa usa correo corporativo con Outlook.

---

#### 🛠️ 2. Preparación

- Clona el sitio de Outlook Web Access (OWA).
- Compra un dominio muy parecido: `out1ook-rrhh.com`.
- Configura un servidor con certificado SSL falso para simular seguridad.

---

#### 🎭 3. Engaño

- Envía un correo falso a Carla simulando al equipo de TI:

```text
De: soporte@empresaRRHH.com
Asunto: Cambio urgente de contraseña

Estimada Carla,

Se detectó una actividad sospechosa en tu cuenta. Por favor, verifica tu identidad accediendo al siguiente enlace:

👉 https://out1ook-rrhh.com/seguridad

Gracias,
Equipo de TI
```

---

#### 💣 4. Manipulación emocional

- El mensaje contiene elementos de:

  - **Urgencia** ("actividad sospechosa")
  - **Autoridad** (aparenta venir de TI)
  - **Miedo** (posible pérdida de acceso)

---

#### ⛔ 5. Explotación

- Carla hace clic.
- Ingresa su usuario y contraseña en el sitio falso.
- El atacante obtiene acceso inmediato.

---

#### 📥 6. Recolección de información

- El atacante ingresa al correo de Carla.
- Descarga planillas de nómina, currículums, contratos confidenciales.

---

#### 👣 7. Retirada

- Usa VPN para ocultar su IP.
- Borra registros de acceso.
- Redirige el sitio falso a una página de error para no levantar sospechas.

---

### 🛡️ ¿Cómo protegerse usando este marco?

Como defensor o usuario, puedes **detectar y bloquear los ataques en cada etapa**:

| Etapa         | Defensa                                                            |
| ------------- | ------------------------------------------------------------------ |
| Investigación | No publicar datos innecesarios en redes.                           |
| Preparación   | Usar filtros de DNS, firewalls, y detección de dominios similares. |
| Engaño        | Usar filtros antiphishing y formación en conciencia de seguridad.  |
| Manipulación  | Entrenamiento para identificar urgencias falsas.                   |
| Explotación   | Uso de 2FA, contraseñas fuertes y monitoreo de accesos.            |
| Recolección   | Monitoreo de accesos inusuales y control de datos sensibles.       |
| Retirada      | Mantener logs, alertas y SIEM para detectar anomalías.             |

---

### 📌 Conclusión

| Elemento            | Resumen                                                                           |
| ------------------- | --------------------------------------------------------------------------------- |
| 🎯 ¿Qué es?         | La **taxonomía** organiza los ataques en etapas para entender mejor cómo ocurren. |
| 🧠 ¿Para qué sirve? | Detectar, prevenir y enseñar sobre ataques de ingeniería social.                  |
| 🧰 ¿Cómo se usa?    | Como guía mental en simulaciones, auditorías o entrenamientos.                    |
| ✅ ¿Cómo prevenir?  | Educación, monitoreo, 2FA, políticas de seguridad, conciencia del personal.       |

---

[🔼](#índice)

---

## **1034. Taxonomía de los ataques**

### 🔍 ¿Qué es la Taxonomía de los Ataques?

La **taxonomía de los ataques** es una **clasificación ordenada y estructurada** de los distintos tipos de ataques informáticos. Esta organización ayuda a:

- Comprender mejor los ataques.
- Detectar y prevenir amenazas.
- Aplicar defensas específicas.
- Enseñar ciberseguridad de forma lógica y progresiva.

Piensa en ella como un **árbol genealógico de los ataques** donde cada rama representa un tipo diferente.

---

### 🧱 Clasificación de los ataques por categorías

Existen distintas formas de clasificar los ataques. Aquí una de las más comunes:

---

#### 🗂️ 1. **Según el objetivo**

| Tipo                 | Descripción                                     | Ejemplo fácil                            |
| -------------------- | ----------------------------------------------- | ---------------------------------------- |
| **Confidencialidad** | Robar o acceder a información sin autorización. | Leer correos ajenos o robar contraseñas. |
| **Integridad**       | Modificar información sin permiso.              | Alterar los datos de una factura.        |
| **Disponibilidad**   | Impedir el acceso a un sistema.                 | Ataques DDoS a una página web.           |

---

#### 🔐 2. **Según el método de ataque**

| Tipo                                    | Subtipos                                 | Ejemplo                                       |
| --------------------------------------- | ---------------------------------------- | --------------------------------------------- |
| **Ataques pasivos**                     | Escucha, espionaje.                      | Sniffing de contraseñas en Wi-Fi.             |
| **Ataques activos**                     | Modifican o interrumpen sistemas.        | Borrar registros, ataques de ransomware.      |
| **Ataques físicos**                     | Manipulación de hardware o dispositivos. | Robar una laptop o insertar un USB malicioso. |
| **Ataques humanos (ingeniería social)** | Engañar al usuario.                      | Phishing por correo electrónico.              |

---

#### 🧰 3. **Según el vector de ataque**

| Vector                   | Ejemplo                                 |
| ------------------------ | --------------------------------------- |
| **Red**                  | Ataques MITM, sniffing, DDoS.           |
| **Aplicaciones web**     | SQL Injection, XSS, LFI.                |
| **Correo electrónico**   | Phishing, spear phishing.               |
| **Dispositivos físicos** | Keyloggers, USB infectados.             |
| **Redes sociales**       | Mensajes falsos con enlaces maliciosos. |

---

#### 🕵️ 4. **Según el atacante (actor de amenaza)**

| Atacante                     | Objetivo                     | Ejemplo                            |
| ---------------------------- | ---------------------------- | ---------------------------------- |
| Hacker ético (white hat)     | Probar seguridad.            | Test de penetración.               |
| Ciberdelincuente (black hat) | Robar, dañar o extorsionar.  | Ataques ransomware.                |
| Hacktivista                  | Protesta política o social.  | Defacement de sitios web.          |
| Insider                      | Usuario con acceso legítimo. | Exfiltra datos antes de renunciar. |

---

### 🛠️ ¿Cómo se "instala" o aplica la taxonomía?

La taxonomía no es un programa, sino una **herramienta conceptual y metodológica**. Se aplica en:

| Contexto                 | ¿Cómo se usa?                                             |
| ------------------------ | --------------------------------------------------------- |
| 🎓 Educación             | Enseñar los tipos de ataques en cursos de ciberseguridad. |
| 🛡️ Seguridad informática | Clasificar incidentes y aplicar contramedidas.            |
| 🔬 Análisis forense      | Entender cómo se realizó un ataque y documentarlo.        |
| 🧪 Pentesting / Red Team | Simular ataques basados en cada categoría.                |
| 📝 Auditoría             | Evaluar vulnerabilidades según tipo de ataque.            |

---

### 🧩 Ejemplo completo: Análisis de un ataque con la taxonomía

---

#### 🎯 Escenario: Un empleado hace clic en un enlace falso y compromete su equipo.

---

#### 🔍 Clasificación paso a paso

| Categoría    | Clasificación              | Ejemplo en el caso                   |
| ------------ | -------------------------- | ------------------------------------ |
| **Objetivo** | Confidencialidad           | El atacante roba credenciales.       |
| **Método**   | Activo + Ingeniería social | Se envía un correo falso (phishing). |
| **Vector**   | Correo electrónico         | El ataque llegó por un email.        |
| **Actor**    | Ciberdelincuente           | Motivo económico: robar acceso.      |

---

#### 📬 Correo recibido por la víctima:

```text
De: soporte@empresa.com
Asunto: Verifica tu cuenta urgentemente

Estimado empleado,

Hemos detectado actividad sospechosa en tu cuenta. Por favor, verifica tu identidad en el siguiente enlace:

https://login-empresasegura.com/verificar

Gracias,
Equipo de Seguridad TI
```

---

#### 😵‍💫 Resultado:

- El empleado hizo clic.
- Ingresó su usuario y contraseña.
- El atacante accedió a archivos internos.
- Se robaron contratos y datos personales.

---

#### 🛡️ Medidas preventivas según la taxonomía:

| Clasificación              | Defensa recomendada                              |
| -------------------------- | ------------------------------------------------ |
| Vector: Correo             | Filtro antiphishing, spam y análisis de enlaces. |
| Método: Ing. social        | Capacitación en conciencia de seguridad.         |
| Objetivo: Confidencialidad | Uso de doble autenticación (2FA).                |
| Actor: Ciberdelincuente    | Vigilancia activa de accesos remotos.            |

---

### 📘 Conclusión

| Elemento            | Resumen                                                                       |
| ------------------- | ----------------------------------------------------------------------------- |
| 🎯 ¿Qué es?         | Una forma ordenada de clasificar los distintos tipos de ataques informáticos. |
| 🧠 ¿Para qué sirve? | Para entender cómo ocurren, prevenirlos y aplicar seguridad estratégica.      |
| 🧪 ¿Cómo se usa?    | En análisis, educación, auditorías, pentesting y monitoreo.                   |
| 📚 ¿Qué aporta?     | Claridad, estructura y mejores prácticas en ciberseguridad.                   |

---

[🔼](#índice)

---

## **1035. Ejemplos de ataques de la ingeniería social: Baiting y Phishing**

### 🧠 ¿Qué es la Ingeniería Social?

La **ingeniería social** es el arte de manipular a las personas para obtener acceso a información, sistemas o recursos, **sin usar tecnología directamente**, sino apelando a la **confianza, miedo, curiosidad o urgencia**.

---

### 🎯 ¿Qué es Baiting?

#### 📦 Baiting (cebo)

Es un tipo de ataque que usa un **“cebo” físico o digital** para que la víctima lo abra y así el atacante gane acceso o controle el sistema.

#### 💡 Ejemplo fácil:

> Alguien deja un USB rotulado como “Fotos personales” en una cafetería. Una persona curiosa lo encuentra y lo conecta en su laptop. El USB tiene un virus que da acceso remoto al atacante.

---

#### 📂 Tipos de cebos comunes:

| Tipo    | Ejemplo                                                                                 |
| ------- | --------------------------------------------------------------------------------------- |
| Físico  | USB con malware, CD, DVD, disco duro externo.                                           |
| Digital | Archivo descargable llamado “CV.docx” infectado, películas piratas, videojuegos gratis. |

---

### 📨 ¿Qué es Phishing?

#### 🐟 Phishing

Es un ataque en el que se **envía un mensaje falso** (por email, SMS, WhatsApp, redes sociales…) que **simula ser de una entidad confiable** para que la víctima:

- Haga clic en un enlace falso.
- Entregue su usuario y contraseña.
- Descargue un archivo malicioso.

#### 💡 Ejemplo fácil:

> Recibes un correo que parece de tu banco diciendo que “tu cuenta será bloqueada” y te da un enlace para verificar. Cuando haces clic, te lleva a una página falsa donde escribes tus datos. El atacante ya tiene acceso a tu cuenta.

---

### 🛠️ ¿Cómo se “instalan” o aplican?

Estos ataques **no se instalan como un programa**, sino que **ocurren en la vida real o digital**. Aquí te muestro cómo se aplican y cómo prevenirlos:

---

#### 🚧 Cómo ocurre un ataque Baiting (flujo)

1. El atacante crea un archivo o dispositivo (como un USB) con malware.
2. Lo deja en un lugar visible (cafetería, baño, oficina).
3. La víctima lo encuentra y lo conecta por curiosidad.
4. El malware se ejecuta: puede abrir puertas traseras, robar archivos, o registrar pulsaciones de teclado (keylogger).

---

#### ✅ Cómo prevenir Baiting

| Medida                                                 | Explicación                                                            |
| ------------------------------------------------------ | ---------------------------------------------------------------------- |
| Nunca conectar dispositivos desconocidos               | Un USB en la calle no es un regalo.                                    |
| Usar máquinas virtuales para analizar archivos dudosos | Reduce el impacto si algo se ejecuta.                                  |
| Deshabilitar ejecución automática de USB               | En Windows, puedes configurarlo desde “Política de grupo” o “Regedit”. |
| Usar antivirus y antimalware actualizado               | Detectan malware conocido.                                             |

---

#### 💌 Cómo ocurre un ataque Phishing (flujo)

1. El atacante recopila información sobre su objetivo (nombre, correo, empresa).
2. Crea un mensaje creíble (correo del banco, aviso de Amazon, etc).
3. Envía el correo masivamente o dirigido (spear phishing).
4. La víctima hace clic en el enlace falso.
5. Introduce sus credenciales o descarga malware.
6. El atacante accede a la cuenta o sistema.

---

#### ✅ Cómo prevenir Phishing

| Medida                                           | Explicación                                                     |
| ------------------------------------------------ | --------------------------------------------------------------- |
| No hacer clic en enlaces de correos sospechosos  | Verifica la dirección real del remitente.                       |
| Usa autenticación de dos factores (2FA)          | Evita que roben tu cuenta aunque tengan tu contraseña.          |
| Instala extensiones antiphishing en tu navegador | Alertan si visitas un sitio malicioso.                          |
| Verifica siempre la URL                          | A veces cambian una letra: “g00gle.com” en vez de “google.com”. |

---

### 🧪 Ejemplo completo y detallado: Ataque Baiting + Phishing

---

#### 🎭 Escenario realista

Una empresa sufre dos ataques de ingeniería social en la misma semana. Uno con un USB infectado (baiting) y otro por correo electrónico falso (phishing).

---

#### 1️⃣ Ataque Baiting

##### 📦 Paso a paso:

1. Un atacante deja un USB en la recepción rotulado como “Fotos de la fiesta”.
2. Un empleado curioso lo conecta en su PC.
3. El archivo “Fotos_evento.exe” era un malware que crea una conexión remota (reverse shell).
4. El atacante accede al sistema interno de la empresa.

---

#### 2️⃣ Ataque Phishing

##### 📩 Paso a paso:

1. Otro empleado recibe este correo:

```text
De: soporte@micloud-banco.com
Asunto: ¡Alerta de seguridad! Verifica tu cuenta

Estimado cliente,

Detectamos movimientos sospechosos. Ingrese al siguiente enlace para confirmar su identidad:

https://banco-seguro.net/login

Atentamente,
Equipo de Seguridad
```

2. La víctima hace clic, introduce su usuario y contraseña.
3. El sitio era falso, y el atacante accede a su banca online.

---

#### 💥 Consecuencias:

- El atacante usó el acceso del USB para instalar ransomware.
- Vendió las credenciales bancarias en la dark web.
- La empresa pierde \$10,000 y horas de recuperación.

---

#### 🛡️ Medidas de prevención implementadas después:

| Medida                      | Acción tomada                                 |
| --------------------------- | --------------------------------------------- |
| Campañas de concientización | Taller sobre no conectar USBs extraños.       |
| Simulaciones de phishing    | Correos falsos para entrenar a los empleados. |
| Antivirus y EDR corporativo | Detección de malware desde el USB.            |
| Uso de 2FA para banca       | No basta con la contraseña robada.            |

---

### 📘 Conclusión

| Elemento   | Resumen                                                                           |
| ---------- | --------------------------------------------------------------------------------- |
| Baiting    | Engaña usando “cebos” físicos o digitales. Curiosidad es la trampa.               |
| Phishing   | Se basa en correos falsos que imitan entidades reales. Apela al miedo o urgencia. |
| Prevención | Educación, filtros, análisis de comportamiento y herramientas de seguridad.       |

---

[🔼](#índice)

---

## **1036. Ejemplos de ataques de ingeniería social: Pretexting, Sextortion, Dumpster Diving, Quid Pro Quo**

### 🧠 ¿Qué es la Ingeniería Social?

La **ingeniería social** es el arte de **engañar o manipular a una persona para que entregue información sensible, realice una acción o comprometa la seguridad**, confiando en un engaño bien construido.

---

### 🎭 1. Pretexting (Falsas identidades)

#### 📌 ¿Qué es?

Es cuando un atacante se **hace pasar por otra persona o entidad** (como un policía, técnico de IT, cliente, proveedor, etc.) para obtener información confidencial o acceso a sistemas.

#### 💡 Ejemplo fácil:

> Un atacante llama a un empleado haciéndose pasar por el jefe de IT:
>
> “Hola, estoy haciendo mantenimiento del servidor, necesito que me confirmes tu usuario y contraseña para revisar tu cuenta”.

#### 🔐 ¿Cómo prevenirlo?

- Nunca compartas contraseñas por teléfono o correo.
- Verifica siempre la identidad antes de dar información.
- Ten procesos claros de verificación de identidad en tu empresa.

---

### 💣 2. Sextortion (Extorsión sexual)

#### 📌 ¿Qué es?

Es un ataque en el que el atacante **afirma tener fotos o videos íntimos** tuyos y te amenaza con publicarlos si no pagas dinero (generalmente en criptomonedas).

#### 💡 Ejemplo fácil:

> Recibes un correo que dice:
>
> “Te grabé mientras veías pornografía, tengo acceso a tu cámara y tus contactos. Si no me pagas 500 USD en Bitcoin en 24h, enviaré el video a tus amigos”.

⚠️ Muchas veces es **falso**. Usan datos públicos filtrados (tu email o una contraseña antigua) para asustarte.

#### 🔐 ¿Cómo prevenirlo?

- Usa tape o una tapa para cubrir tu webcam.
- Cambia tus contraseñas si has sido filtrado.
- No cedas ante amenazas. Guarda evidencias y reporta.

---

### 🗑️ 3. Dumpster Diving (Buceo en la basura)

#### 📌 ¿Qué es?

Los atacantes **revisan la basura física o digital** para obtener información útil: credenciales escritas, contratos, planos, listas de empleados, etc.

#### 💡 Ejemplo fácil:

> Un atacante revisa la basura detrás de una oficina y encuentra una hoja con usuarios y contraseñas anotados a mano.

#### 🔐 ¿Cómo prevenirlo?

- Tritura todos los documentos antes de desecharlos.
- No tires papel con información sensible sin destruirlo.
- Configura borrado seguro en discos duros o USBs antes de desecharlos.

---

### 🤝 4. Quid Pro Quo (Este por aquello)

#### 📌 ¿Qué es?

Un atacante ofrece algo a cambio de información o acceso. Puede ser soporte técnico, regalos, o incluso beneficios laborales.

#### 💡 Ejemplo fácil:

> Un atacante llama a varias personas diciendo:
>
> “Hola, soy del soporte técnico de Microsoft. Quiero darte una actualización gratuita. Solo necesito acceso remoto a tu computadora”.

La víctima, creyendo que recibe un beneficio, entrega acceso.

#### 🔐 ¿Cómo prevenirlo?

- No aceptes ayuda no solicitada.
- Verifica el número o identidad del soporte técnico.
- Nunca instales programas por recomendación de un extraño.

---

### 🧪 EJEMPLO COMPLETO: Ataque combinado de Ingeniería Social

#### 🎯 Escenario: Empresa pequeña de marketing digital.

#### 1️⃣ Día 1 – Dumpster Diving

El atacante revisa la basura detrás de la empresa y encuentra:

- Un papel con la red Wi-Fi y clave escrita.
- Una factura impresa con datos del dueño y empleados.

#### 2️⃣ Día 2 – Pretexting

Con la información obtenida, el atacante llama a una diseñadora:

> “Hola, soy Luis de soporte. Estoy actualizando tu Adobe, ¿puedes entrar a este link y darme tu usuario y contraseña?”

La víctima confía porque el atacante menciona el nombre del jefe y datos reales del equipo.

#### 3️⃣ Día 3 – Quid Pro Quo

Luego, otro empleado recibe un correo:

> “Gracias por participar. Por ser cliente de Canva, ganas 3 meses Premium gratis. Solo instala esta extensión.”

La extensión era malware.

#### 4️⃣ Día 4 – Sextortion

Otro empleado recibe un correo:

> “Te observé por tu cámara, tengo tu contraseña: **mark2022** (era una contraseña real de una filtración). Si no pagas, te expongo.”

---

#### 💥 Consecuencias:

- Pérdida de acceso a correos y diseño en la nube.
- Extorsión emocional a empleados.
- Robos de clientes y datos privados.

---

### 🛡️ Medidas de Prevención recomendadas

| Técnica de ataque | Prevención                                               |
| ----------------- | -------------------------------------------------------- |
| Pretexting        | Validación de identidad. Nunca compartir claves.         |
| Sextortion        | No caer en el miedo. Revisión de filtraciones. Usar 2FA. |
| Dumpster Diving   | Triturado de papel. Eliminación segura de discos.        |
| Quid Pro Quo      | Política clara de soporte. Verificación externa.         |

---

### ✅ Conclusión

| Ataque          | Clave del engaño                                   |
| --------------- | -------------------------------------------------- |
| Pretexting      | Se gana tu confianza con un personaje falso.       |
| Sextortion      | Te manipula usando miedo y vergüenza.              |
| Dumpster Diving | Usa tu descuido físico para obtener datos.         |
| Quid Pro Quo    | Te ofrece algo atractivo a cambio de tu seguridad. |

---

[🔼](#índice)

---

## **1037. Ejemplos de ataques de ingeniería social: Vishing, Fake News, Tailgating, Piggybacking**

### 📞 1. **Vishing (Voice Phishing)**

#### 📌 ¿Qué es?

Es una forma de phishing que ocurre **por llamada telefónica**. El atacante se hace pasar por una figura de autoridad (banco, policía, soporte técnico, etc.) para que la víctima **entregue información confidencial**.

#### 💬 Ejemplo fácil:

> “Hola, le llamamos del banco BCP porque hubo un intento de retiro sospechoso. Necesitamos verificar su identidad. ¿Puede darnos el número de su tarjeta y su clave?”

Muchas personas caen por el **miedo o la urgencia**.

#### 🛡️ ¿Cómo prevenirlo?

- Nunca compartas datos por teléfono.
- Cuelga y llama directamente al número oficial de la empresa.
- Activa alertas por app para evitar depender de llamadas.

---

### 📰 2. **Fake News (Noticias falsas con fines de manipulación)**

#### 📌 ¿Qué es?

El atacante difunde **información falsa, alarmista o emocional** para manipular a las personas. Puede tener como objetivo político, social o simplemente causar caos.

#### 💬 Ejemplo fácil:

> Una publicación viral en redes dice:
>
> “¡Nueva ley prohíbe guardar efectivo en casa! Si no lo entregas al banco antes del lunes, será ilegal.”

Esto genera miedo y puede ser usado para:

- Redirigirte a un sitio falso de “registro”
- Aprovecharte emocionalmente
- Generar pánico y desinformación

#### 🛡️ ¿Cómo prevenirlo?

- Verifica las fuentes. ¿Es un medio confiable?
- Usa servicios de verificación como Snopes, AFP Factual o Maldita.
- No compartas sin confirmar.

---

### 🚪 3. **Tailgating (Colarse físicamente sin autorización)**

#### 📌 ¿Qué es?

El atacante **entra a un edificio o área restringida** aprovechando que alguien con acceso le abre la puerta. No tiene autorización, pero entra junto al personal legítimo.

#### 💬 Ejemplo fácil:

> Tú entras al edificio de tu oficina y alguien con una caja en la mano dice:
>
> “¡Uy! Se me olvidó la tarjeta, ¿me dejas pasar?”

Por amabilidad, lo dejas pasar sin verificar.

#### 🛡️ ¿Cómo prevenirlo?

- Nunca dejes entrar a alguien que no tenga credenciales visibles.
- Reporta accesos no autorizados.
- Usa puertas con sensores o molinetes.

---

### 🧍‍♂️ 4. **Piggybacking (Colarse con consentimiento, pero engañoso)**

#### 📌 ¿Qué es?

Muy parecido a Tailgating, pero **aquí la víctima consciente abre la puerta**, pensando que la persona **sí está autorizada** (es un engaño más deliberado).

#### 💬 Ejemplo fácil:

> El atacante dice:
>
> “Soy nuevo en TI, el jefe dijo que trabajaría desde hoy. ¿Podrías dejarme entrar?”

La víctima cree que es legítimo y lo deja pasar.

#### 🛡️ ¿Cómo prevenirlo?

- Confirma con Recursos Humanos o Seguridad si hay nuevos empleados.
- No te fíes solo del uniforme o apariencia.
- Reporta accesos inusuales.

---

### 🧪 EJEMPLO COMPLETO — Ataque Combinado

#### 🎯 Escenario: Oficina corporativa

1. **Fake News**:

   El atacante crea una noticia falsa en redes sociales:

   > “Ministerio de Salud advierte que todos los empleados deben vacunar a su familia esta semana. Ya se han cerrado oficinas por incumplir.”

2. **Vishing**:

   Luego, llama a la oficina:

   > “Hola, soy de la Unidad de Salud Corporativa. Necesitamos que sus empleados completen un formulario web para estar autorizados a trabajar.”

   El enlace lleva a un sitio falso donde roban nombres, correos, DNI y teléfonos.

3. **Piggybacking**:

   El atacante llega a la oficina y dice:

   > “Tengo cita para revisar el aire acondicionado del piso 3. Ya completé el formulario COVID que ustedes pidieron”.

   Le abren la puerta pensando que fue verificado.

4. **Tailgating**:

   Otro atacante aprovecha a un grupo de empleados para colarse directamente sin que lo vean.

---

#### 💥 Resultado:

- Robo de datos personales
- Acceso físico no autorizado
- Posible instalación de pendrives maliciosos

---

### 🛡️ Recomendaciones generales

| Ataque       | Prevención clave                                                    |
| ------------ | ------------------------------------------------------------------- |
| Vishing      | Nunca compartas info por teléfono. Verifica con tu banco o empresa. |
| Fake News    | Verifica las fuentes. No compartas sin confirmar.                   |
| Tailgating   | Cierra puertas y no dejes pasar a desconocidos.                     |
| Piggybacking | Verifica identidades, incluso si parece legítimo.                   |

---

### ✅ Conclusión

Estos ataques de ingeniería social **no dependen de tecnología avanzada**, sino de **errores humanos y descuidos**. Son muy usados porque son **baratos, efectivos y difíciles de rastrear**.

Con capacitación, sentido común y procedimientos claros, puedes **reducir el riesgo significativamente**.

---

[🔼](#índice)

---

## **1038. ¿Qué es la elicitación y por qué es tan exitosa?**

### 🧠 ¿Qué es la **elicitación**?

**La elicitación** es una técnica de manipulación psicológica que busca **extraer información sensible** de una persona sin que se dé cuenta de que está revelándola.

No se trata de amenazas ni coacción. Es más bien una conversación casual donde el atacante **hace preguntas indirectas, lanza comentarios estratégicos o usa trucos verbales** para que la víctima entregue datos voluntariamente.

---

### 🤔 ¿Por qué es tan exitosa?

Porque:

- La mayoría de personas **quiere ser amable o parecer útil**.
- Muchas veces queremos **presumir de lo que sabemos**.
- Se disfraza de conversación inocente.
- No parece un interrogatorio, por eso **baja las defensas**.

---

### 🔧 ¿Cómo se “instala” o aplica?

La elicitación no requiere software ni dispositivos. Se **aplica como una técnica verbal o escrita**.

El atacante puede usar:

- Un chat informal
- Una llamada telefónica
- Una conversación presencial
- Un correo aparentemente inocente

---

### 🎯 Técnicas comunes de elicitación

| Técnica               | Descripción                                       | Ejemplo                                                                                      |
| --------------------- | ------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| **Halago**            | Hacer que la víctima quiera impresionar.          | “Tú que eres experto en servidores, ¿qué medidas usas contra ataques?”                       |
| **Fingir ignorancia** | Pedir ayuda para “entender” algo.                 | “¿Qué es eso de SQL? Siempre escucho que es peligroso…”                                      |
| **Repetición falsa**  | Decir algo incorrecto para que lo corrijan.       | “¿Tu sistema tiene backup solo una vez al mes, no?”                                          |
| **Causa común**       | Simular tener algo en común.                      | “¡Yo también trabajé en Sunat! ¿Tú en qué área estabas?”                                     |
| **Presión del grupo** | Usar lo que otros “ya dijeron” como excusa.       | “Tu compañero me dijo que ustedes usan Oracle. ¿Tú también estás con esa base?”              |
| **Sondeo progresivo** | Hacer preguntas pequeñas que parecen inofensivas. | “¿Qué software usan en el área? ¿Está conectado a internet? ¿Tienen clave por cada usuario?” |

---

### 💬 Ejemplos fáciles y cotidianos

#### 🧑‍💻 En el trabajo

> **Atacante**: “Siempre he querido trabajar donde tú estás. ¿Cómo es la infraestructura ahí?”
>
> **Víctima**: “Bueno, usamos servidores virtuales con Ubuntu, tenemos backups semanales…”
>
> → ¡Ya reveló datos clave!

---

#### 🧑‍🎓 En una charla casual

> **Atacante**: “¿Tú que trabajas en ciberseguridad, cuál es el firewall más difícil de vulnerar?”
>
> **Víctima**: “Nosotros usamos Fortinet, aunque tengo mis dudas con ciertas configuraciones…”
>
> → Dio el nombre de su herramienta.

---

### ⚠️ ¿Qué tipo de información buscan con la elicitación?

- Software o tecnologías usadas
- Nombres de empleados o jerarquías
- Rutinas diarias
- Datos personales o laborales
- Contraseñas disfrazadas (“¿cuántos caracteres tiene tu clave?”)
- Opiniones que podrían ser usadas en chantajes

---

### 🛡️ ¿Cómo protegerte?

- No compartas información laboral o personal con desconocidos.
- Sé escéptico ante preguntas “curiosas”.
- Pregunta siempre: “¿Para qué necesita esta información?”
- Evita responder detalles técnicos por cortesía o para impresionar.
- Capacita a tu equipo en técnicas de elicitación.

---

### 🧪 EJEMPLO COMPLETO: Ataque de elicitación exitoso

#### 🎯 Contexto:

Un atacante quiere descubrir qué antivirus usan en una empresa para preparar un malware que lo evite.

#### 🧑‍💼 Conversación casual:

> **Atacante (en LinkedIn):**
>
> “¡Hola! Vi que trabajas en ciberseguridad en Empresa X. Estoy empezando en esto y me interesa mucho el tema de antivirus empresariales. ¿Tú qué recomendarías?”

> **Víctima:**
>
> “Hola. Bueno, nosotros usamos Kaspersky en las estaciones y Bitdefender en servidores. A veces da problemas con ciertas actualizaciones.”

> **Atacante:**
>
> “Interesante. ¿Y tienen algún SIEM que monitoree los logs?”

> **Víctima:**
>
> “Sí, Splunk. Lo conecta todo.”

#### 💥 Resultado:

El atacante ahora sabe:

- Qué antivirus usa la empresa
- Que usa Splunk
- Que hay problemas con actualizaciones → posible punto débil

Con esto puede construir:

- Malware que evada Kaspersky y Bitdefender
- Ataques que aprovechen esos “problemas”

---

### ✅ Conclusión

**La elicitación es silenciosa, sutil y muy efectiva.**
No hace falta un hackeo técnico si la víctima **entrega la información sin darse cuenta**. Por eso es una herramienta poderosa en la ingeniería social.

---

[🔼](#índice)

---

## **1039. Estrategias y respuestas a la elicitación**

### 🧠 ¿Qué es la elicitación? (Breve repaso)

La **elicitación** es una técnica de **ingeniería social** que busca obtener información confidencial de alguien a través de una conversación aparentemente inocente. El atacante **no amenaza ni hackea**, solo **conversa estratégicamente** para que la víctima **le entregue la información voluntariamente**.

---

### 🛡️ ¿Qué son las estrategias y respuestas ante la elicitación?

Son formas **conscientes y entrenadas de responder o actuar** frente a intentos de manipulación conversacional. Estas estrategias te permiten **detectar, resistir y cortar** la conversación antes de revelar información importante.

---

### 🎯 Objetivo: Proteger información sin sonar grosero ni levantar sospechas

---

### 🔧 ¿Cómo se “instalan” estas estrategias?

No se instalan como un software, sino que se:

- **Aprenden**
- **Practican**
- **Incorporan como hábitos de comunicación**

Se pueden enseñar en:

- Capacitaciones de ciberseguridad
- Simulacros de ingeniería social
- Políticas internas de seguridad
- Videos o guías para empleados y usuarios

---

### 🧱 Estrategias de defensa ante la elicitación

| Estrategia                              | Explicación                                    | Ejemplo de uso                                          |
| --------------------------------------- | ---------------------------------------------- | ------------------------------------------------------- |
| **Responder con ambigüedad**            | No dar detalles específicos.                   | “Usamos varias herramientas para protección.”           |
| **Responder con una broma**             | Desvía la conversación con humor.              | “¡Si te lo digo tendría que eliminarte!” 😅             |
| **Responder con una pregunta**          | Cambias el foco al interlocutor.               | “¿Y tú cómo manejas ese tema en tu trabajo?”            |
| **Cortar la conversación educadamente** | Poner límites sin sonar grosero.               | “Eso no puedo compartirlo, gracias por entender.”       |
| **Simular ignorancia**                  | Fingir que no sabes del tema.                  | “No manejo esa parte técnica, lo ve otra área.”         |
| **Redirigir a canales oficiales**       | Sugieres un medio más seguro o autorizado.     | “Puedes consultar eso con el área de soporte.”          |
| **Alertar al equipo de seguridad**      | Si notas un intento de elicitación, repórtalo. | (Avisar a tu jefe o seguridad TI tras la conversación.) |

---

### 🚨 Señales de que estás siendo víctima de elicitación

- Te hacen muchas preguntas que parecen **inofensivas pero técnicas**.
- Alguien intenta **halagarte o impresionarte** para que hables más.
- Sientes que la conversación **fluye rápido hacia temas confidenciales**.
- Te presionan suavemente con frases como:

  > “Solo por curiosidad”, “No pasa nada”, “Es solo un comentario”, etc.

---

### ✅ Cómo entrenar estas respuestas

1. **Role-playing**: Simula escenarios con compañeros.
2. **Listas negras**: Define qué tipo de información nunca debes compartir.
3. **Ejercicios de respuesta**: Práctica ante distintas preguntas.
4. **Recordatorios visuales**: Pega frases tipo “¿Por qué me están preguntando esto?” cerca del lugar de trabajo.
5. **Uso de guías rápidas**: Tarjetas con ejemplos de respuestas evasivas.

---

### 💡 Ejemplos fáciles de entender

#### 🗣️ Ejemplo 1: Redirigir y simular ignorancia

> **Atacante**: “¿Qué firewall usan en tu empresa?”
>
> **Tú**: “No estoy seguro, eso lo ve infraestructura. Seguro usan algo avanzado.” ✅

---

#### 🗣️ Ejemplo 2: Cortar educadamente

> **Atacante**: “¿En qué servidor está la base de datos de clientes?”
>
> **Tú**: “Disculpa, esa información es interna y no puedo compartirla.” ✅

---

#### 🗣️ Ejemplo 3: Broma con evasiva

> **Atacante**: “¿Tu contraseña tiene letras o números?”
>
> **Tú**: “¡Claro! También tiene runas élficas y símbolos secretos.” 😄✅

---

### 🧪 EJEMPLO COMPLETO DE DEFENSA CONTRA EL ELICITADOR

#### 🎯 Contexto:

Eres parte del área TI de una empresa y en una conferencia, un desconocido empieza a conversar contigo casualmente.

---

#### 🧑‍💼 Conversación:

> **Desconocido**: “Qué interesante lo que contaste del soporte. ¿Con qué sistema monitorean los incidentes de red?”
>
> **Tú**: “Lo maneja otra área, la verdad no tengo ese detalle.” ✅
>
> **Desconocido**: “Ah, ya... pero imagino que es algo tipo Zabbix o Splunk, ¿cierto?”
>
> **Tú**: “Puede ser, usamos varias herramientas, no sabría decirte cuál es exactamente.” ✅
>
> **Desconocido**: “Oye, ¿y tienen backups diarios o semanales?”
>
> **Tú**: “Eso es parte de nuestras políticas internas. Preferiría no comentar.” ✅
>
> **Desconocido**: “Ah ok, perdón. Es que estoy pensando en postular a tu empresa.”
>
> **Tú**: “¡Claro! Puedes revisar las vacantes en la web. Suerte.” ✅

---

#### 🔍 Resultado:

- No diste información sensible.
- No sonaste grosero.
- Mantuviste el control de la conversación.

---

### 🧩 Conclusión

- La **elicitación funciona** porque muchos caen sin notarlo.
- Pero **saber detectarla y responder estratégicamente** te protege sin necesidad de confrontar.
- Practicar estas respuestas y fomentar una **cultura de seguridad verbal** es vital, especialmente en ambientes corporativos o donde manejas datos sensibles.

---

[🔼](#índice)

---

## **1040. Qué es el pretexting y cuál es su proceso**

### 🧠 ¿Qué es el **pretexting**?

**Pretexting** (en español, “**pretextar**”) es una técnica de **ingeniería social** que consiste en **crear una identidad falsa y un escenario creíble (pretexto)** para engañar a una persona y lograr que revele **información sensible** o realice una **acción específica**.

🔑 El objetivo es **ganarse la confianza** de la víctima usando una historia convincente.

---

### 🔍 Características del pretexting

| Característica                      | Descripción                                                                                                                |
| ----------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| 🎭 **Falsa identidad**              | El atacante finge ser alguien con autoridad, confianza o rol específico (policía, técnico de TI, empleado de banco, etc.). |
| 📖 **Escenario creíble (pretexto)** | Crea una situación que justifique la solicitud de información.                                                             |
| 🗣️ **Interacción personalizada**    | No es un mensaje masivo como en el phishing; el atacante interactúa directamente.                                          |
| 🧠 **Se basa en la psicología**     | Usa el respeto a la autoridad, la urgencia o el deseo de ayudar para manipular.                                            |

---

### ⚙️ ¿Cómo se “instala” un ataque de pretexting?

No se instala como un programa, pero el atacante **sigue un proceso paso a paso**, como si estuviera “configurando” el engaño.

---

### 🧩 Proceso de un ataque de **pretexting**

1. **Investigación (reconocimiento)**

   - El atacante investiga a la empresa o persona objetivo (LinkedIn, redes sociales, etc.).
   - Busca jerarquías, correos, nombres reales, lenguaje interno.

2. **Creación del pretexto (historia convincente)**

   - Ejemplo: se hace pasar por técnico del banco que necesita “verificar una transferencia sospechosa”.

3. **Contacto con la víctima**

   - Vía correo, llamada telefónica, chat o en persona.

4. **Generación de confianza**

   - Usa tecnicismos, nombres reales, datos básicos ya recolectados (“Sé que usted trabaja en el área de ventas…”).

5. **Solicitud de información o acción**

   - Pide credenciales, datos privados, ejecución de comandos, instalación de software, etc.

6. **Cierre limpio**

   - El atacante termina la interacción sin levantar sospechas o deja la puerta abierta a un nuevo contacto.

---

### 🎯 Ejemplos simples y claros

#### 🧑‍💼 Ejemplo 1:

> Un atacante llama haciéndose pasar por el **soporte técnico de la empresa**:
>
> — “Hola, hablo del área de TI. Estamos revisando un incidente de seguridad. Necesito que me confirme su usuario y cambie su contraseña temporalmente a ‘Admin123’, por favor.”

✅ Parece legítimo, pero **es falso**.

---

#### 🏦 Ejemplo 2:

> El atacante se hace pasar por un **empleado del banco**:
>
> — “Hola, hubo una transferencia sospechosa en su cuenta. Para bloquearla, necesito verificar su clave token.”

---

#### 🧑‍🎓 Ejemplo 3:

> El atacante dice ser del **área de admisión de una universidad**:
>
> — “Su matrícula ha sido seleccionada para una beca, pero necesitamos validar su DNI y número de cuenta para el depósito.”

---

### 🛡️ ¿Cómo protegerte del pretexting?

| Estrategia                                                             | Acción                                                                     |
| ---------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| **Verifica siempre la identidad**                                      | Corta la llamada y llama tú mismo a la institución oficial.                |
| **No compartas credenciales ni datos sensibles por teléfono o correo** | Ni siquiera con supuestos empleados.                                       |
| **Fíjate en señales de urgencia sospechosa**                           | “Tienes que hacerlo ahora”, “Es una emergencia” suelen ser banderas rojas. |
| **Sospecha si te piden instalar software remoto**                      | Como AnyDesk, TeamViewer, etc.                                             |
| **Reporta intentos sospechosos**                                       | A tu equipo de seguridad, jefe o canal oficial.                            |

---

### 🧪 EJEMPLO COMPLETO DE PRETEXTING (Escenario realista)

#### 🎯 Contexto:

Trabajas en el área administrativa de una empresa. Recibes una llamada de alguien que dice ser del área de soporte TI de tu empresa.

---

#### 📞 Llamada:

> **Atacante (voz amable y profesional)**:
>
> “Hola, hablo de soporte técnico. Estoy viendo un problema con las credenciales en el servidor contable. Necesito verificar si su cuenta está generando conflictos. ¿Me puede decir su usuario y contraseña actual para hacer la prueba desde aquí?”

---

#### ⚠️ ¿Por qué suena creíble?

- Usa un pretexto válido: problemas técnicos.
- Menciona una herramienta interna real.
- Habla como si trabajara en tu empresa.

---

#### ❌ Si caes:

Le das tus credenciales y ahora el atacante puede entrar al sistema con tu cuenta.

---

#### ✅ Si te proteges:

> “Gracias por avisar. Prefiero confirmar esto directamente con soporte. ¿Cuál es su extensión? Voy a llamar por la central.”

O simplemente cuelgas y reportas.

---

### ✅ Conclusión

- El **pretexting** es una de las técnicas **más efectivas** de ingeniería social.
- Se basa en la **confianza y el engaño**, no en malware.
- Detectarlo a tiempo y saber responder con prudencia puede **proteger toda una organización**.

---

[🔼](#índice)

---

## **1041. Qué son los Deepfake y sus tipos**

### 🧠 ¿Qué son los **Deepfake**?

Los **deepfakes** son **videos, audios o imágenes falsas creadas con inteligencia artificial** que imitan la voz, el rostro o los gestos de una persona real de forma tan realista que puede parecer verdadero.

🔎 La palabra viene de:

- **Deep** (por "deep learning", o aprendizaje profundo)
- **Fake** (falso)

---

### 🤖 ¿Cómo se “instalan” o crean?

No se “instalan” como un programa, pero **se crean usando herramientas y modelos de IA** entrenados para **reconocer, copiar y manipular rostros, voces y gestos**.

#### 🔧 Herramientas comunes para crear deepfakes:

- **Faceswap** (software de código abierto)
- **DeepFaceLab**
- **Zao** (app china de intercambio facial)
- **Synthesia** (para crear presentaciones con avatares que hablan)
- **ElevenLabs** (para clonar voces)
- **Descript Overdub** (para clonar voz con texto)
- **Reface / Wombo AI** (apps móviles)

#### 🧱 Pasos básicos para crear un deepfake:

1. **Recolección de datos**

   Se consiguen muchos videos o imágenes de una persona (de redes sociales, YouTube, etc.).

2. **Entrenamiento del modelo**

   Un software de IA analiza el rostro y gestos de esa persona desde distintos ángulos.

3. **Generación del contenido**

   Se intercambia el rostro o voz en otro video o audio, haciendo que parezca que la persona dice o hace cosas que nunca dijo o hizo.

4. **Ajustes finales**

   Se afina la sincronización de labios, tono, movimientos de cabeza, etc.

---

### 🧨 ¿Por qué son peligrosos?

- Se pueden usar para:

  - **Difamar o engañar**
  - **Estafas o fraudes**
  - **Extorsión o chantaje**
  - **Propaganda política o fake news**
  - **Suplantación de identidad**
  - **Pornografía falsa**

---

### 🧬 Tipos de Deepfakes

| Tipo                                       | Descripción                                                                        | Ejemplo                                                                |
| ------------------------------------------ | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| 🎭 **Intercambio de rostro (Face Swap)**   | Cambiar la cara de una persona en un video por otra.                               | Un video donde Elon Musk “baila” en TikTok, pero es falso.             |
| 🗣️ **Clonación de voz (Voice Cloning)**    | La IA imita tu voz con solo unos minutos de grabación.                             | Un audio donde “pareces” decir que autorizas una transacción bancaria. |
| 🖼️ **Imágenes falsas (Deepfake Images)**   | Fotos manipuladas para mostrar cosas que no sucedieron.                            | Una foto tuya con alguien que nunca viste.                             |
| 👥 **Avatares digitales (AI Avatars)**     | Crear personajes que parecen humanos reales y hablan.                              | Noticias falsas con presentadores que no existen.                      |
| 🕵️ **Lip sync (sincronización de labios)** | Cambiar el movimiento de la boca para hacer parecer que la persona dice otra cosa. | Un político diciendo algo comprometedor que nunca dijo.                |

---

### ✅ Ejemplos fáciles de entender

#### 🎬 Ejemplo 1: Intercambio de cara

Un atacante crea un video donde parece que tú estás insultando a tu jefe. El video se ve real, pero es completamente falso: usaron tu rostro y lo colocaron en otro cuerpo.

---

#### 📞 Ejemplo 2: Clonación de voz

Un estafador llama a tu mamá usando una voz clonada con IA y dice:

> “Hola mamá, tuve un accidente y necesito que me transfieras S/ 1000 ahora mismo. No puedo hablar mucho.”

Tu madre, al reconocer tu voz, podría caer.

---

### 🧪 EJEMPLO COMPLETO REALISTA

#### 🎯 Contexto:

Una persona conocida publica muchos videos en TikTok hablando de temas financieros. Un estafador descarga esos videos y entrena una IA para **clonar su rostro y voz**.

---

#### 🎥 El ataque:

El atacante usa **DeepFaceLab** y **ElevenLabs** para crear un video donde esa persona dice:

> “Hola chicos, tengo una nueva inversión garantizada. Deposita ahora a esta cuenta y triplica tu dinero.”

Sube ese video falso a TikTok o YouTube como si fuera real.

---

#### 🧨 Resultado:

Decenas de seguidores **caen en la trampa**, creyendo que el video es auténtico porque **la cara y voz son idénticas** al influencer.

---

### 🔐 ¿Cómo protegerte?

| Estrategia                                       | Acción                                                                                    |
| ------------------------------------------------ | ----------------------------------------------------------------------------------------- |
| **Verifica la fuente original**                  | ¿El video fue publicado en la cuenta oficial o en otra cuenta?                            |
| **Busca movimientos raros o parpadeos extraños** | Algunos deepfakes aún fallan en eso.                                                      |
| **No confíes solo por ver o escuchar**           | Llama directamente, valida por otros canales.                                             |
| **Evita subir demasiados videos tuyos a redes**  | Cuanto más material haya, más fácil es clonar tu imagen o voz.                            |
| **Usa herramientas de detección**                | Hay plataformas como [Deepware Scanner](https://www.deepware.ai/) que detectan deepfakes. |

---

### 📌 Conclusión

- Los **deepfakes** usan IA para **engañar visual o auditivamente**.
- Son peligrosos porque parecen reales y pueden usarse en **estafas, difamación o chantaje**.
- Aprender a **identificarlos** y **verificar fuentes** es clave para protegerse.

---

[🔼](#índice)

---

## **1042. Aplicaciones disponibles para crear Deepfake**

### 📌 ¿Qué es una aplicación de Deepfake?

Una **aplicación de deepfake** permite crear videos, imágenes o audios falsos **simulando el rostro, cuerpo o voz de otra persona** con ayuda de inteligencia artificial. Son herramientas que **reconocen y reemplazan patrones faciales o de voz**.

---

### 🛠️ ¿Qué necesitas para usar estas apps?

- Una computadora o celular (dependiendo del tipo de aplicación)
- Videos o imágenes de la persona que quieras imitar
- (A veces) conocimientos básicos de edición
- Conexión a internet (si es en la nube)

---

### 🧰 Aplicaciones más populares para crear deepfakes

#### 1. **Reface** _(móvil)_

- 📱 App móvil (Android y iOS)
- 🖼️ Intercambia tu rostro con famosos, GIFs, memes, etc.
- 🧠 Usa IA para animar tu cara sobre otro cuerpo
- ✅ Muy fácil de usar
- ❌ Limitado para uso profesional

**Ejemplo:** Tomas una selfie y apareces como el protagonista de una película de Marvel.

---

#### 2. **Wombo AI** _(móvil)_

- 📱 Crea videos donde tu cara “canta” canciones famosas
- 🎤 Sólo necesitas una selfie
- 🧠 Genera el video en pocos segundos

**Ejemplo:** Subes tu foto y Wombo te hace cantar "Bohemian Rhapsody".

---

#### 3. **DeepFaceLab** _(PC - Windows)_

- 💻 Software avanzado y gratuito (código abierto)
- 🧠 Permite hacer deepfakes de alta calidad
- ⚙️ Requiere conocimientos técnicos y buen hardware
- 🎬 Usado por investigadores y creadores avanzados

**Instalación resumida:**

1. Descarga desde GitHub: [https://github.com/iperov/DeepFaceLab](https://github.com/iperov/DeepFaceLab)
2. Extrae el archivo ZIP
3. Abre los scripts según tu GPU (NVIDIA recomendada)
4. Sigue el flujo: **extraer rostro → entrenar modelo → reemplazar rostro**

---

#### 4. **Zao** _(móvil)_

- App china que permite cambiar tu rostro por el de un actor
- Solo necesitas una foto y se genera el video automáticamente
- Muy popular en Asia

**Ejemplo:** Tomas una selfie y te ves actuando en una escena de “Titanic”.

---

#### 5. **Synthesia** _(web)_

- 🌐 Herramienta profesional de generación de video con avatares
- Crea videos donde un avatar con apariencia real dice lo que tú escribes
- Ideal para empresas o presentaciones
- Tiene opción de subir tu avatar personalizado

**Ejemplo:** Escribes un texto y aparece un presentador digital diciendo eso en video.

---

#### 6. **FaceMagic** _(móvil)_

- Intercambia tu rostro en clips populares
- Muy similar a Reface
- Facilidad de uso en redes sociales

---

#### 7. **Avatarify / First Order Motion Model** _(PC / código abierto)_

- Transforma tu rostro para imitar a otros **en tiempo real** (como en videollamadas)
- Muy popular en la comunidad open source
- Ideal para streaming, bromas o proyectos de IA

---

#### 8. **Descript con Overdub** _(web)_

- 🧠 Crea audios clonando tu voz
- Subes un texto y la IA habla con tu voz
- Útil para locuciones, pero se puede mal usar

---

### 🧪 Ejemplo completo: Crear un deepfake simple con Reface

#### 🎯 Objetivo:

Aparecer como Iron Man usando la app Reface.

---

#### ✅ Pasos:

1. **Instala la app Reface**

   - Android: Google Play
   - iPhone: App Store

2. **Abre la app y toma una selfie**

3. **Elige un video famoso en la galería (por ejemplo, Iron Man)**

4. **La IA reemplaza el rostro de Iron Man por el tuyo**

5. **Guarda el video o compártelo**

🎥 **Resultado:** Pareces tú actuando como Iron Man con expresiones y movimientos.

---

### ⚠️ Consideraciones éticas

Estas apps tienen fines **entretenidos o educativos**, pero también pueden usarse para:

- Suplantar identidad
- Crear contenido difamatorio o engañoso
- Engañar con noticias falsas
- Cometer fraudes

Por eso, **su uso debe ser responsable y ético**.

---

### 🛡️ ¿Cómo saber si un deepfake es falso?

- La voz suena robótica o no natural
- La piel se ve muy suave o extraña
- El parpadeo es raro o inexistente
- El video tiene errores en sombras o reflejos

---

### 🧠 Conclusión

Las **aplicaciones de deepfake** van desde juegos hasta software avanzado. Algunas son simples y otras requieren computadoras potentes. Aunque parecen inofensivas, también pueden ser peligrosas si se usan con malas intenciones.

> La clave está en **saber cómo funcionan, entender sus riesgos y usarlas éticamente**.

---

[🔼](#índice)

---

## **1043. Relación del Deepfake, la ingeniería social y cómo detectarlos**

### 🧠 ¿Qué es un _deepfake_?

**Deepfake** (deep = profundo, fake = falso) es una técnica que usa **inteligencia artificial (IA)** para **crear videos, imágenes o audios falsos** que parecen reales. Se puede hacer que una persona diga o haga cosas que **nunca hizo realmente**.

---

### 🎭 ¿Qué es la _ingeniería social_?

Es una técnica que usan los ciberdelincuentes para **engañar y manipular psicológicamente** a las personas y así obtener:

- Información confidencial
- Acceso a sistemas
- Dinero u otros beneficios

Por ejemplo, alguien se hace pasar por un técnico de soporte para pedirte tu contraseña.

---

### 🔗 ¿Cómo se relacionan _deepfake_ e _ingeniería social_?

La **ingeniería social se basa en la confianza**, y el deepfake **fabrica esa confianza falsamente**.

#### 🎯 Relación directa:

1. **Ingeniería social** → manipula tu mente
2. **Deepfake** → manipula lo que ves y escuchas
3. Combinados → crean un **engaño visual y emocional muy poderoso**

---

#### 🧨 Ejemplo real:

Un estafador usó un **audio deepfake** de un director general (CEO) para llamar a un empleado y pedirle que hiciera una **transferencia bancaria urgente**.

👉 El empleado **reconoció la voz** y obedeció.

Ese es un caso de ingeniería social **potenciado por deepfake**.

---

### ⚙️ ¿Cómo se hacen los deepfakes? (instalación y uso básico)

Depende de si lo haces desde un **móvil** o una **PC potente**:

#### Opción 1: **Desde el celular** con Reface o Wombo

1. Instalas la app desde Play Store o App Store
2. Tomas una selfie o subes una foto
3. Eliges un video o audio popular
4. La IA reemplaza la cara o voz
5. Exportas o compartes

➡️ No requiere conocimientos técnicos.

---

#### Opción 2: **Desde la PC** con DeepFaceLab

1. Descarga el software desde GitHub
   👉 [https://github.com/iperov/DeepFaceLab](https://github.com/iperov/DeepFaceLab)
2. Necesitas:

   - Tarjeta gráfica (GPU)
   - Buen procesador y memoria

3. Flujo básico:

   - Extraer rostros de un video original
   - Entrenar la IA con tus imágenes
   - Insertar los rostros generados en el video objetivo

➡️ Requiere conocimientos de Python, IA y edición.

---

### 🛑 ¿Por qué son peligrosos los deepfakes?

- Pueden usarse para **difamar** a alguien
- Pueden **robar identidades**
- Se usan para **fraudes financieros**
- Facilitan **extorsión o chantaje**

---

### 🕵️‍♂️ ¿Cómo detectar un deepfake o ingeniería social?

#### 🔍 Técnicas para detectar deepfakes:

1. **Parpadeo raro o ausente**
2. **Desincronización entre labios y voz**
3. **Sombras o iluminación anormal**
4. **Cambios sutiles en los bordes del rostro**
5. **Errores en las manos o fondo distorsionado**

💡 Tip: Si algo “no se siente natural” en un video, **desconfía**.

---

#### 👀 Cómo detectar ingeniería social:

1. **Mensajes que generan urgencia o miedo**

   Ej: “¡Tu cuenta será bloqueada en 1 hora si no actúas!”

2. **Solicitudes de información confidencial**

   Ej: “Confírmame tu clave para actualizar el sistema”

3. **Lenguaje demasiado amable o técnico**

   Ej: “Soy del área de TI, necesito acceso remoto para ayudarte”

---

### ✅ Ejemplo completo fácil de entender

#### 🧪 Escenario: Estafa combinando ingeniería social + deepfake

1. Recibes un mensaje de WhatsApp con un **video de tu jefe** diciendo:

   > “Hola Gustavo, necesito que hagas una transferencia urgente de S/ 3,000. Es muy importante. Confírmame si puedes.”

2. El video **luce real**: se ve su cara y su voz.

3. Luego, un número desconocido te llama diciendo:

   > “Hola, soy el contador de tu jefe. ¿Pudiste hacer la transferencia?”

4. ¿Qué está pasando?

   - El video fue hecho con **deepfake**
   - La llamada es parte de la **ingeniería social**
   - Te están presionando emocionalmente y usando la imagen de alguien que **confías**

---

#### 🤯 ¿Cómo evitar caer?

1. Verifica la fuente: llama a tu jefe directamente
2. Sospecha si algo suena “urgente y secreto”
3. Fíjate en la calidad del video
4. Si es un número nuevo o desconocido, **no respondas con confianza**
5. Usa herramientas para detectar manipulación de imágenes/videos

---

### 🎓 Conclusión

| Concepto          | Qué hace                                     | Ejemplo en acción                       |
| ----------------- | -------------------------------------------- | --------------------------------------- |
| Deepfake          | Manipula la vista o el oído                  | Video falso de una autoridad            |
| Ingeniería social | Manipula tus emociones y decisiones          | Mensaje urgente de “soporte técnico”    |
| Ambos combinados  | Te hacen ver + creer una mentira convincente | Video falso + llamada para robar dinero |

🔐 **Protegerse** implica **dudar**, **verificar**, y **aprender a detectar patrones**.

---

[🔼](#índice)

---

## **1044. Herramientas de detección de Deepfake**

### 🧠 ¿Qué son los deepfakes?

Los _deepfakes_ son **videos, audios o imágenes falsos generados con inteligencia artificial (IA)**. Su propósito puede ir desde el entretenimiento hasta el fraude o manipulación.

Por ejemplo:

- Un video donde aparece el presidente diciendo algo que **nunca dijo realmente**.
- Una videollamada falsa usando la cara de un jefe pidiendo dinero.

---

### 🎯 ¿Por qué debemos detectarlos?

Porque los deepfakes pueden ser peligrosos:

- Suplantación de identidad
- Extorsión con videos falsos
- Manipulación de información
- Fraudes financieros

Por eso nacen las **herramientas de detección de deepfakes**.

---

### 🧰 Herramientas para detectar deepfakes

A continuación te muestro algunas herramientas reales y sus formas de uso:

---

#### 1. **Deepware Scanner (para usuarios comunes)**

- **¿Qué hace?**: Escanea archivos de video para detectar si es deepfake.
- **Tipo**: Online y app móvil (iOS y Android)
- **Ideal para**: Usuarios sin conocimientos técnicos.

##### 🔧 ¿Cómo usarlo?

1. Entra a [https://www.deepware.ai/](https://www.deepware.ai/)
2. Sube el video o pega el enlace de YouTube.
3. Espera unos segundos.
4. Te dice si es **real, sospechoso o deepfake confirmado**.

✅ **Fácil de usar, sin instalación avanzada**.

---

#### 2. **Microsoft Video Authenticator**

- **¿Qué hace?**: Analiza videos y da un puntaje de “probabilidad de ser falso”.
- **Tipo**: Herramienta distribuida por Microsoft solo a organizaciones verificadas (no de uso público general).
- **Ideal para**: Gobiernos, ONGs y medios de comunicación.

---

#### 3. **Sensity AI (antes Deeptrace)**

- **¿Qué hace?**: Analiza imágenes y videos y genera reportes detallados.
- **Tipo**: Herramienta profesional para empresas.
- **Uso**: Requiere registrarse en [https://sensity.ai](https://sensity.ai)

---

#### 4. **FaceForensics++ (para investigadores)**

- **¿Qué hace?**: Dataset + modelos entrenados para detectar deepfakes con precisión.
- **Tipo**: Técnico, para investigadores.
- **Instalación**:

  - Requiere conocimientos de Python
  - Descargar el repositorio desde GitHub
  - Ejecutar modelos entrenados para análisis

---

#### 5. **DeepFaceLab (para creadores y detectores)**

- Aunque su uso principal es crear deepfakes, se puede analizar cómo están construidos para entender su falsedad.
- Ideal para **entrenar a profesionales en cómo detectar manipulaciones**.

---

### 👣 ¿Cómo se instalan o usan estas herramientas?

#### Opción A: Online (sin instalar nada)

- Herramientas como Deepware.ai solo requieren **subir un archivo** o **pegar un enlace**.
- Recomendadas para el usuario común.

#### Opción B: Apps móviles

- Apps como Deepware o Truepic se instalan desde Play Store / App Store.
- Uso: subes una foto o video, y la app lo analiza.

#### Opción C: Herramientas técnicas

1. Instala Python en tu PC
2. Descarga modelos de GitHub (como `FaceForensics++`)
3. Usa Jupyter Notebook o consola para analizar los videos

Estas opciones son más avanzadas y se usan en universidades, laboratorios de ciberseguridad, etc.

---

### 🧪 Ejemplo completo fácil de entender

#### 🎬 Escenario:

Te llega un **video por WhatsApp** donde aparece tu jefe pidiendo una transferencia urgente.

Sospechas que puede ser un **deepfake**.

#### 🔎 ¿Cómo lo detectas?

##### Paso 1: Verifica visualmente

- ¿Parpadea de forma rara?
- ¿Los labios no coinciden bien con la voz?
- ¿Hay bordes pixelados en la cara?
- ¿La iluminación es uniforme o "plana"?

##### Paso 2: Usa Deepware Scanner

1. Ve a [https://www.deepware.ai](https://www.deepware.ai)
2. Sube el archivo de video desde tu PC o celular
3. Espera a que lo analice (1–2 min)
4. Resultado:

   - 🔴 “High Probability of Deepfake” (Alta probabilidad de deepfake)

##### Paso 3: Confirmas tus sospechas

Llamas a tu jefe por otro medio seguro y él **no tenía idea del video**.

➡️ **¡Te salvaste de una estafa!**

---

### ✅ Recomendaciones finales

| Recomendación                        | ¿Por qué?                                     |
| ------------------------------------ | --------------------------------------------- |
| Usa herramientas como Deepware       | Son fáciles y rápidas                         |
| Verifica siempre con otra fuente     | Una llamada directa puede evitar estafas      |
| Aprende a observar detalles visuales | Parpadeo, sombras, labios, voz                |
| Comparte esta info con tu equipo     | La ciberseguridad es responsabilidad de todos |

---

[🔼](#índice)

---

## **1045. Retos de los procesos de investigación forense en Deepfake**

### 🔍 ¿Qué es la investigación forense en Deepfake?

La **investigación forense digital en casos de Deepfake** consiste en **detectar, analizar, documentar y preservar evidencia digital** (como videos falsos) que han sido creados o manipulados mediante inteligencia artificial.

---

### ⚠️ ¿Por qué es importante?

Porque los deepfakes pueden:

- Manipular declaraciones públicas
- Causar daños a la reputación
- Suplantar identidad para fraudes
- Falsificar evidencia judicial

---

### 🎯 Objetivo de la investigación forense

Identificar **si un contenido multimedia ha sido alterado digitalmente**, cómo fue creado, cuándo, y si es posible, **quién lo hizo**.

---

### 🧱 Principales retos en la investigación forense de Deepfakes

Aquí están los **retos más importantes** con ejemplos fáciles de entender:

---

#### 1. **Alta calidad de los deepfakes actuales**

##### 🔍 Problema:

Los deepfakes modernos imitan muy bien los movimientos faciales, la voz y el fondo.

##### 📌 Ejemplo:

Antes podías ver errores como ojos que no parpadean. Hoy, eso ya está corregido con IA más avanzada, dificultando su detección visual.

---

#### 2. **Falta de metadatos confiables**

##### 🔍 Problema:

Muchos deepfakes eliminan o falsifican los metadatos del archivo (fecha de creación, software usado, cámara original).

##### 📌 Ejemplo:

Un video editado puede “parecer” grabado con un iPhone, pero en realidad fue generado en una PC con software de IA.

---

#### 3. **Dificultad de preservar evidencia**

##### 🔍 Problema:

Un video enviado por WhatsApp puede comprimirse o cambiar de formato, y **ya no se considera original**, dificultando su análisis pericial.

##### 📌 Ejemplo:

La policía recibe un video reenviado por 10 personas. Ya no es confiable como evidencia judicial directa.

---

#### 4. **Evolución constante de la IA**

##### 🔍 Problema:

Cada mes surgen nuevas técnicas que burlan los detectores actuales, obligando a los forenses a actualizarse constantemente.

##### 📌 Ejemplo:

Hoy detectas ojos fijos, pero mañana ya entrenan deepfakes para parpadear correctamente.

---

#### 5. **Acceso limitado a herramientas forenses avanzadas**

##### 🔍 Problema:

Muchos software de detección profunda solo están disponibles para universidades o empresas.

##### 📌 Ejemplo:

Herramientas como Microsoft Video Authenticator no están abiertas al público general.

---

#### 6. **Dificultad en probar la autoría**

##### 🔍 Problema:

Aun si se demuestra que el video es falso, **probar quién lo creó** es extremadamente difícil.

##### 📌 Ejemplo:

Un atacante usa una VPN y una cuenta falsa para subir un deepfake a redes sociales. No se puede rastrear.

---

### 🛠️ Herramientas para la investigación forense en Deepfake

Aquí algunos recursos que se pueden instalar o utilizar:

---

#### 1. **Sensity AI ([https://sensity.ai](https://sensity.ai))**

- Analiza videos e imágenes para detectar manipulación.
- Requiere registro.
- Uso profesional.

---

#### 2. **Deepware Scanner**

- Gratis.
- Sube un video y detecta si es deepfake.
- Ideal para usuarios comunes.

---

#### 3. **FaceForensics++ (con instalación local)**

Para usuarios más técnicos.

##### 🔧 ¿Cómo instalar?

1. Tener **Python 3** y **Git** instalado.
2. Clonar el repositorio:

   ```bash
   git clone https://github.com/ondyari/FaceForensics.git
   cd FaceForensics
   ```

3. Instalar dependencias:

   ```bash
   pip install -r requirements.txt
   ```

4. Ejecutar los scripts de detección de videos falsos.

Este tipo de software usa **redes neuronales** entrenadas para distinguir patrones humanos reales vs. artificiales.

---

### 🧪 Ejemplo completo: Caso práctico

#### 🎬 Escenario:

Un influencer famoso es acusado de hacer una declaración ofensiva en un video viral. Él niega haber dicho eso.

Te contratan como **analista forense**.

---

#### 🔎 Paso 1: Recolección de evidencia

Pides el **video original**, sin reenvíos ni ediciones.

---

#### 🧼 Paso 2: Verificación de metadatos

Usas herramientas como **ExifTool**:

```bash
exiftool video.mp4
```

Resultado: metadatos **eliminados**. Posible edición.

---

#### 👁️ Paso 3: Análisis visual

Observas:

- Parpadeo irregular
- Transiciones suaves entre planos
- Movimientos de labios sutilmente desincronizados

Sospecha de deepfake.

---

#### 🧪 Paso 4: Análisis con Deepware

1. Subes el video a [https://deepware.ai](https://deepware.ai)
2. Resultado: “High Probability of Deepfake”

---

#### 🤖 Paso 5: Validación con IA local

Usas `FaceForensics++` para hacer una segunda evaluación.

Código ejecutado:

```python
from forensics import analyze_video
analyze_video('video.mp4')
```

Resultado: 87% de probabilidad de generación con IA.

---

#### 📁 Paso 6: Documentación del caso

Creas un informe:

- Video original
- Hash SHA256
- Metadatos ausentes
- Análisis visual
- Resultado de IA
- Herramientas usadas

Este informe es entregado a abogados o jueces.

---

### ✅ Recomendaciones finales

| Acción                                | Por qué hacerlo                                   |
| ------------------------------------- | ------------------------------------------------- |
| Preservar siempre el archivo original | La evidencia debe ser confiable y legal           |
| Analizar visualmente primero          | A veces lo obvio también ayuda                    |
| Complementar con IA forense           | Mejora la credibilidad del análisis               |
| Usar varias herramientas              | Evita falsos positivos o negativos                |
| Capacitarse constantemente            | La IA avanza rápido, y los forenses deben también |

---

[🔼](#índice)

---

## **1046. Medidas de prevención, protección y cómo crear una cultura de seguridad**

### 🔍 ¿Qué significa esto?

- **Prevención:** Son acciones que haces **antes** de que ocurra un ataque o accidente de ciberseguridad.
- **Protección:** Son herramientas o configuraciones que **bloquean o reducen** el daño si un ataque llega a ocurrir.
- **Cultura de seguridad:** Es el conjunto de **hábitos, valores y prácticas** que todos (usuarios, empleados o familias) deben aplicar para mantener la seguridad digital.

---

### 🧱 1. Medidas de **Prevención** (lo que haces para evitar incidentes)

---

#### 🔐 A) Contraseñas seguras y autenticación

- **Qué hacer:** Usar contraseñas largas, únicas, y autenticación en dos pasos (2FA).
- **Ejemplo fácil:** En vez de "juan123", usa "TuPerroRojo2024!" y activa 2FA con Google Authenticator.

##### 📦 Cómo se instala:

- Activa 2FA en cuentas como Gmail, Facebook o Dropbox.
- Instala en tu celular:

  👉 **Google Authenticator** (Android/iOS)

  👉 **Authy** (si quieres respaldos)

---

#### 🌐 B) Navegar con cuidado

- No hacer clic en enlaces desconocidos.
- Verificar el candado 🔒 en la URL del navegador.
- Evitar descargar cosas de páginas extrañas.

##### Ejemplo:

Si te llega un correo de “Banco BBVA” pidiéndote tu clave, primero entra tú manualmente a bbva.com.pe y verifica si es cierto.

---

### 🧰 2. Medidas de **Protección** (cuando ya ocurrió un intento o incidente)

---

#### 🧱 A) Uso de antivirus y firewall

- Protegen en tiempo real contra virus, troyanos y otros ataques.

##### Cómo se instala:

- **Windows Defender** ya viene activado en Windows 10/11.
- Si deseas más funciones, puedes instalar:

  👉 **Bitdefender Free**

  👉 **Avast** o **Kaspersky Security Cloud Free**

---

#### 🔒 B) Control de permisos

- No dar permisos innecesarios a aplicaciones o usuarios.

##### Ejemplo:

Una app linterna no debería pedir acceso a tus contactos o cámara. Eso puede ser malicioso.

##### Cómo configurarlo:

- En Android: Configuración > Aplicaciones > Permisos.
- En Windows: Panel de control > Cuentas > Cambiar tipo de cuenta.

---

### 👨‍🏫 3. Crear una **Cultura de Seguridad** (la parte humana)

---

#### 🧠 A) Educar constantemente

- Hacer capacitaciones breves cada cierto tiempo.
- Usar videos, charlas o juegos interactivos.

##### Ejemplo:

Una empresa hace un reto mensual: “¿Detectas el correo falso?” con premios para el que acierte.

---

#### 🤝 B) Fomentar la responsabilidad compartida

- Cada persona es parte del escudo. Si uno falla, todos están en peligro.
- Enseñar a reportar rápidamente un error sin miedo.

##### Ejemplo:

Un empleado hace clic por error en un link malicioso, **pero avisa al instante**, y así se logra contener el daño.

---

#### 🗣️ C) Comunicación abierta

- Tener un canal claro para reportar incidentes: correo, WhatsApp, intranet.
- Que todos sepan a quién acudir.

---

### 🧪 Ejemplo completo: Aplicación en una familia o empresa

---

#### Escenario:

Una familia quiere protegerse en internet y empezar una **cultura de seguridad digital** en casa.

---

#### 🧩 Paso 1: Prevención

✅ Activan 2FA en Gmail de todos

✅ Enseñan a sus hijos a no compartir contraseñas

✅ Revisan juntos un video de YouTube sobre phishing

---

#### 🛡️ Paso 2: Protección

✅ Instalan antivirus gratuito (Bitdefender Free)

✅ Configuran el firewall del router Wi-Fi

✅ Ajustan permisos de apps en los celulares de sus hijos

---

#### 🌱 Paso 3: Cultura de seguridad

✅ Cada domingo tienen una “noche digital” donde comparten tips de seguridad

✅ Enseñan a su hijo a reportar cualquier cosa extraña que vea en redes sociales

✅ Papá recibe un correo extraño y lo reenvía a la familia para que todos aprendan a detectarlo

---

### ✅ Resultado

Toda la familia ahora:

- Tiene contraseñas seguras y doble verificación
- No cae fácilmente en trampas
- Sabe qué hacer en caso de un intento de hackeo
- Se protege unos a otros

---

### 📌 Recomendaciones finales

| Acción                          | Herramienta sugerida                   |
| ------------------------------- | -------------------------------------- |
| 2FA                             | Google Authenticator / Authy           |
| Antivirus                       | Bitdefender / Avast / Windows Defender |
| Control parental                | Google Family Link / Qustodio          |
| Gestión de contraseñas          | Bitwarden / LastPass                   |
| Cursos breves de ciberseguridad | Google Actívate / Platzi / Udemy       |

---

[🔼](#índice)

---

## **1047. Cómo protegerse y recomendaciones**

### 🎯 ¿Qué significa protegerse en el entorno digital?

Protegerse es **reducir los riesgos de ser víctima de un ciberataque**, **pérdida de datos**, o **engaños** a través del uso de buenas prácticas, herramientas y educación continua. No se trata de tener miedo, sino de estar **preparado y consciente**.

---

### 🧱 Principales formas de protegerse

---

#### 1. 🔑 **Usar contraseñas seguras y únicas**

**¿Por qué?**

Las contraseñas débiles son fáciles de adivinar con programas automatizados.

**Ejemplo fácil:**

No uses “123456” o “admin”. Mejor usa: `GatoCeleste!92&` o una frase como: `MiHermanoComePizza2025!`

**Cómo se instala o aplica:**

- Usa un **gestor de contraseñas** como **Bitwarden** o **LastPass**.
- Estos se instalan en navegador y/o celular y guardan tus contraseñas cifradas.

---

#### 2. 📲 **Activa la Autenticación en Dos Factores (2FA)**

**¿Por qué?**

Aunque un atacante robe tu contraseña, no podrá entrar sin el segundo paso (código del celular).

**Ejemplo fácil:**

Cuando inicias sesión en Gmail, te llega un código a tu celular antes de ingresar.

**Cómo se instala:**

- Ve a “Seguridad” en tu cuenta (Google, Facebook, etc.).
- Activa “Verificación en dos pasos”.
- Instala en tu celular **Google Authenticator** o **Authy**.

---

#### 3. 🦠 **Instalar y mantener actualizado un antivirus**

**¿Por qué?**

El antivirus detecta y bloquea archivos o sitios maliciosos antes de que causen daño.

**Cómo se instala:**

- En Windows ya tienes **Windows Defender** activo.
- Puedes instalar antivirus gratuitos como:

  - **Bitdefender Free**
  - **Avast**
  - **Kaspersky Security Cloud Free**

---

#### 4. 📡 **Navegar con precaución (especialmente en Wi-Fi públicas)**

**¿Por qué?**

Redes Wi-Fi abiertas pueden permitir que un hacker espíe tu conexión.

**Ejemplo fácil:**

Evita entrar a tu banco desde el Wi-Fi de un café.

**Cómo protegerte:**

- Usa una **VPN** confiable como **ProtonVPN** (gratuita) o **NordVPN** (de pago).
- No ingreses contraseñas sensibles desde redes públicas.

---

#### 5. 🚨 **Reconocer correos y mensajes sospechosos (phishing)**

**¿Por qué?**

Muchos ataques inician con un correo que parece legítimo, pero es falso.

**Ejemplo fácil:**

Un correo de “tu banco” te pide que hagas clic en un enlace raro para verificar tu cuenta.

**Cómo protegerte:**

- Nunca hagas clic sin verificar la dirección del remitente.
- Marca los correos sospechosos como "phishing" en tu bandeja de entrada.
- Usa extensiones como **“Netcraft Anti-Phishing”** en tu navegador.

---

#### 6. 📦 **Actualizar siempre tus dispositivos**

**¿Por qué?**

Las actualizaciones corrigen vulnerabilidades que los hackers pueden usar.

**Cómo se aplica:**

- Activa actualizaciones automáticas en:

  - Windows: Configuración → Actualización y seguridad
  - Android/iOS: Configuración → Actualización del sistema
  - Aplicaciones: Desde la tienda oficial (Play Store, App Store)

---

#### 7. 🧠 **Crear una cultura de seguridad (personal o familiar)**

**¿Por qué?**

Todos los miembros de tu hogar o empresa deben estar informados para no ser el eslabón débil.

**Cómo se hace:**

- Habla regularmente sobre ciberseguridad.
- Crea reglas claras:
  Ejemplo: “Nadie instala apps sin revisar permisos”
  Ejemplo: “Si ves algo raro, lo cuentas de inmediato”

---

### ✅ Recomendaciones clave

| Acción              | Herramienta recomendada            |
| ------------------- | ---------------------------------- |
| Contraseñas seguras | Bitwarden, LastPass                |
| 2FA                 | Google Authenticator, Authy        |
| Antivirus           | Bitdefender, Windows Defender      |
| Navegar seguro      | VPN: ProtonVPN, NordVPN            |
| Anti-phishing       | Netcraft, extensiones de navegador |
| Actualizaciones     | Sistema operativo y apps al día    |
| Educación en casa   | Juegos, videos, y dinámicas        |

---

### 🧪 Ejemplo completo

#### 🎯 Escenario:

Ana tiene 3 hijos, una laptop personal y usa internet para pagar el banco, estudiar y redes sociales. Ella quiere proteger su hogar digital.

---

#### 🧩 Paso 1: Contraseñas

✅ Ana instala Bitwarden

✅ Cambia su contraseña del correo por: `M1Perro$Ladra_2025`

---

#### 🔐 Paso 2: 2FA

✅ Activa verificación en dos pasos en Gmail

✅ Instala Google Authenticator en su celular

---

#### 🛡️ Paso 3: Antivirus y actualizaciones

✅ Activa Windows Defender

✅ Configura Windows para que se actualice automáticamente

---

#### 🌐 Paso 4: Navegación segura

✅ Instala ProtonVPN

✅ Enseña a sus hijos a no ingresar al banco desde el Wi-Fi de la escuela

---

#### 👨‍👩‍👧‍👦 Paso 5: Cultura de seguridad

✅ Cada sábado en la tarde hacen un juego de “Detecta el correo falso”

✅ Enseña a los niños a no dar contraseñas a nadie

---

#### 🔚 Resultado:

Ana y su familia están protegidos, informados y saben cómo actuar ante cualquier intento de engaño.

---

[🔼](#índice)

---

## **1048. Creando un escenario de pretexting**

### 🧠 ¿Qué es el **Pretexting**?

El **pretexting** (o "pretextado") es una técnica de **ingeniería social** en la que el atacante se **hace pasar por otra persona o entidad** con el fin de ganarse la confianza de la víctima y obtener **información confidencial**, **acceso a sistemas** o **recursos físicos o digitales**.

**La clave está en el “pretexto”**: el atacante inventa una historia o identidad **creíble**.

---

### 🎯 Objetivo del pretexting

El pretexting busca:

- Obtener datos personales (DNI, cuentas, contraseñas).
- Acceder a sistemas (inicios de sesión, correo, bases de datos).
- Extraer dinero o favores.

---

### 🔧 ¿Cómo se "instala" o se construye un ataque de pretexting?

#### 1. 🕵️ Recolección de información previa (OSINT)

El atacante investiga sobre:

- La empresa o persona objetivo.
- Jerarquías (quién es jefe, quién es asistente).
- Correos, redes sociales, fotos, rutinas.

💡 **Ejemplo fácil:**

El atacante busca en LinkedIn: "Recursos Humanos - Empresa XYZ" y encuentra que Carla Ramírez trabaja allí.

---

#### 2. 🎭 Crear el pretexto (historia falsa)

El atacante decide qué rol asumir:

- Técnico de soporte.
- Compañero nuevo.
- Jefe de otra sede.
- Auditor externo.

💡 **Ejemplo fácil:**

“Hola, soy Pablo de Soporte TI. Estamos haciendo una actualización del sistema y necesito verificar tu acceso a la VPN.”

---

#### 3. 📞 Contacto con la víctima

El atacante se comunica con la víctima por:

- Teléfono (vishing).
- Correo (pretexting digital).
- Mensaje.
- Presencialmente.

---

#### 4. 🎯 Ganarse la confianza

Utiliza:

- Tono formal y confiado.
- Detalles reales que obtuvo (para parecer legítimo).
- Presión o urgencia ("¡esto es urgente!").

---

#### 5. 🧨 Recolectar la información

Una vez que la víctima confía, el atacante:

- Pide datos sensibles.
- Accede remotamente al equipo.
- Manipula a la víctima para que haga algo riesgoso.

---

### 🧪 Ejemplo completo de un escenario de pretexting

#### 📌 Escenario: Empresa mediana de Lima, Perú

#### 🎭 Pretexto: “Soporte técnico del proveedor de internet”

---

#### 1. Recolección de información

El atacante ve en la página web que la empresa se llama **"SoluTIon Perú SAC"** y usa **Claro Empresas** como proveedor de internet.

---

#### 2. Preparación del ataque

El atacante crea una historia:

> “Soy Javier Huamán, del área técnica de Claro Empresas. Detectamos que hay problemas con la IP de su router y necesito validar si tienen configurado correctamente el acceso remoto al equipo para evitar interrupciones.”

---

#### 3. Contacto con la víctima

Llama a **la secretaria o recepcionista**:

📞 “Hola, soy Javier de Claro Empresas. ¿Está disponible alguien del área técnica o de sistemas? Esto es urgente. Ayer hubo problemas con su sede y tenemos que verificar la conectividad ahora.”

---

#### 4. Reacción de la víctima

Si la persona no tiene formación en ciberseguridad, puede:

- Transferir la llamada al responsable real (y ahí también manipularlo).
- O brindar información básica, como:

  - IP interna o externa.
  - Modelo del router.
  - Usuario y contraseña del Wi-Fi o de administración.

---

#### 5. Resultado del ataque

El atacante obtiene acceso remoto al router o red y puede:

- Interceptar tráfico.
- Redirigir páginas (ataques man-in-the-middle).
- Espiar actividad.

---

### 🛡️ ¿Cómo defenderse del pretexting?

#### 1. **Verifica la identidad**

- Si alguien llama diciendo que es de un proveedor, cuelga y **devuelve la llamada a través de los canales oficiales**.

#### 2. **Capacita al personal**

- Haz simulacros.
- Enseña a todos (hasta al vigilante) a **no dar datos sin autorización**.

#### 3. **Procedimientos claros**

- “Nadie comparte información por teléfono sin validación interna”.
- Toda solicitud debe ir por canales formales (correo oficial, formulario, etc.).

---

### ✅ Conclusión

El pretexting **es peligroso porque apela a nuestra confianza, educación o presión del momento**. No necesitas ser técnico para caer en la trampa.

La **mejor defensa es la prevención, la educación y una cultura de verificación constante**.

---

[🔼](#índice)

---

| **Inicio**         | **atrás 20**                                                                     | **Siguiente 22**                                          |
| ------------------ | -------------------------------------------------------------------------------- | --------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./7_20_Introduccion_a_Ciberseguridad_Prevencion_de_Ataques_Informaticos.md) | [⏩](./7_22_Ciberseguridad_y_Privacidad_para_Empresas.md) |
