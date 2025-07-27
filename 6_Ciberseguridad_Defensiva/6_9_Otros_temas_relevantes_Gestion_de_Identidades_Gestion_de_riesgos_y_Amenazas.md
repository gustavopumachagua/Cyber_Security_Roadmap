| **Inicio**         | **atrás 8**                                                                             |
| ------------------ | --------------------------------------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./6_8_Firma_digital_Certificado_digital_y_PKI_Infraestructura_de_clave_publica.md) |

---

## **Índice**

| Temario                                                                                                                                            |
| -------------------------------------------------------------------------------------------------------------------------------------------------- |
| [582. Gestión de Identidades y control de acceso (IAM)](#582-gestión-de-identidades-y-control-de-acceso-iam)                                       |
| [583. IAM vs Active Directory](#583-iam-vs-active-directory)                                                                                       |
| [584. Gestión de Identidades y acceso (IAM) en AWS](#584-gestión-de-identidades-y-acceso-iam-en-aws)                                               |
| [585. Autenticación y Autorización: SAML, OAUTH, 2FA](#585-autenticación-y-autorización-saml-oauth-2fa)                                            |
| [586. Gestión y análisis de riesgos de Ciberseguridad](#586-gestión-y-análisis-de-riesgos-de-ciberseguridad)                                       |
| [587. Modelos de gestión y análisis de riesgos de Ciberseguridad](#587-modelos-de-gestión-y-análisis-de-riesgos-de-ciberseguridad)                 |
| [588. Modelado de amenazas de Ciberseguridad: MITRE ATT&CK, STRIDE](#588-modelado-de-amenazas-de-ciberseguridad-mitre-attck-stride)                |
| [589. Gestión de riesgos de ciberseguridad mediante modelado de amenazas](#589-gestión-de-riesgos-de-ciberseguridad-mediante-modelado-de-amenazas) |

---

# **Otros temas relevantes: Gestion de Identidades, Gestion de riesgos y Amenazas**

## **582. Gestión de Identidades y control de acceso (IAM)**

### 🧠 ¿Qué es IAM (Identity and Access Management)?

La **Gestión de Identidades y Acceso (IAM)** es un **conjunto de políticas, procesos y tecnologías** que permiten:

| Objetivo                       | Ejemplo real                                                |
| ------------------------------ | ----------------------------------------------------------- |
| 🔐 Identificar usuarios        | ¿Quién eres tú? (correo, nombre de usuario, etc.)           |
| ✅ Autenticar usuarios         | ¿Cómo demuestras quién eres? (contraseña, MFA, certificado) |
| 🛂 Autorizar accesos           | ¿Qué puedes hacer? (leer, escribir, administrar)            |
| 🧾 Auditar y registrar accesos | ¿Cuándo y cómo accediste?                                   |

---

### 🏢 Ejemplo en la vida real

Piensa en el sistema de una empresa:

- Un empleado **nuevo** ingresa
- RRHH lo registra en el sistema
- El sistema IAM crea una **identidad digital** (ej: [juan@empresa.com](mailto:juan@empresa.com))
- Le asigna permisos según su **rol** (ej: solo acceso a ventas)
- Si cambia de rol, se **ajustan los permisos**
- Si renuncia, se **revoca el acceso**

---

### 📚 Componentes principales de IAM

| Componente            | ¿Qué hace?                                                   |
| --------------------- | ------------------------------------------------------------ |
| **Identidades**       | Son los usuarios, servicios o dispositivos                   |
| **Autenticación**     | Verifica la identidad (usuario + contraseña, MFA, SSO, etc.) |
| **Autorización**      | Define qué recursos puede acceder un usuario                 |
| **Roles y políticas** | Permiten agrupar permisos fácilmente                         |
| **Auditoría**         | Registra quién hizo qué y cuándo                             |

---

### 🔧 ¿Cómo se implementa un sistema IAM?

Hay varias formas. Las más comunes son:

#### 🔹 1. IAM Local (On-Premise)

Ej: **Active Directory (AD)** o **FreeIPA**

- Usuarios guardados en tu red local
- Autenticación centralizada (LDAP/Kerberos)

#### 🔹 2. IAM en la nube

Ej: **AWS IAM**, **Azure Active Directory**, **Google Workspace**

- Controlas accesos a servicios cloud
- Ideal para empresas distribuidas

#### 🔹 3. Soluciones de IAM de código abierto

Ej: **Keycloak**, **Auth0 (gratuito hasta cierto punto)**

---

### ✅ Instalación práctica con **Keycloak** (IAM de código abierto)

Keycloak es una herramienta de IAM **gratuita y robusta** para gestionar:

- Usuarios
- Roles
- Aplicaciones
- Single Sign-On (SSO)
- MFA

---

### 🚀 Instalación de Keycloak en Docker (Rápido)

#### Paso 1: Requisitos

- Docker
- Docker Compose (opcional)

#### Paso 2: Crear archivo `docker-compose.yml`

```yaml
version: "3"

services:
  keycloak:
    image: quay.io/keycloak/keycloak:24.0.2
    command: start-dev
    environment:
      KEYCLOAK_ADMIN: admin
      KEYCLOAK_ADMIN_PASSWORD: admin123
    ports:
      - "8080:8080"
```

#### Paso 3: Ejecutar

```bash
docker-compose up -d
```

#### Paso 4: Acceder

Ir a [http://localhost:8080](http://localhost:8080)
Login: `admin` / `admin123`

🎉 ¡Ya tienes un servidor IAM funcionando!

---

### 👤 Crear usuarios, roles y controlar accesos

#### Paso 1: Crear un **realm**

Un _realm_ es como una "empresa" o "entorno". Puedes tener varios.

1. En el panel, click en "Add realm"
2. Nombre: `empresa-acme`

---

#### Paso 2: Crear un usuario

1. En el realm `empresa-acme`, ir a “Users” → “Add user”
2. Username: `gustavo`
3. Guardar
4. Ir a la pestaña “Credentials”
5. Establecer una contraseña

---

#### Paso 3: Crear un rol y asignarlo

1. Ir a “Roles” → “Add Role” → Nombre: `admin`
2. Ir al usuario `gustavo` → “Role Mappings” → Asignar el rol `admin`

---

#### Paso 4: Conectar una app (simulada)

Puedes proteger una app como un dashboard, API o servicio web integrando:

- Keycloak Adapter (para Java, Node.js, React, etc.)
- Usando OAuth2, OIDC o SAML

---

### 🧪 Ejemplo completo de control de acceso

#### Escenario:

1. Gustavo entra a un sistema con su usuario
2. Tiene el rol `admin`
3. Accede a `/admin-panel`
4. Otro usuario con rol `viewer` no puede entrar a esa ruta

#### Backend Express.js protegido con JWT de Keycloak:

```js
const express = require("express");
const jwt = require("express-jwt");
const jwksRsa = require("jwks-rsa");

const app = express();

const checkJwt = jwt({
  secret: jwksRsa.expressJwtSecret({
    jwksUri:
      "http://localhost:8080/realms/empresa-acme/protocol/openid-connect/certs",
    cache: true,
    rateLimit: true,
  }),
  audience: "my-app",
  issuer: "http://localhost:8080/realms/empresa-acme",
  algorithms: ["RS256"],
});

app.use(checkJwt);

app.get("/admin-panel", (req, res) => {
  const roles = req.user.realm_access.roles;
  if (roles.includes("admin")) {
    res.send("Bienvenido al panel de administración.");
  } else {
    res.status(403).send("Acceso denegado.");
  }
});

app.listen(3000, () => console.log("App corriendo en http://localhost:3000"));
```

---

### 🔍 Beneficios de usar IAM

| Beneficio                 | Ejemplo                                                  |
| ------------------------- | -------------------------------------------------------- |
| Seguridad centralizada    | Usuarios y accesos en un solo lugar                      |
| Escalabilidad             | Fácil de manejar para 10 o 10,000 usuarios               |
| Cumplimiento (compliance) | Registros y auditorías para normativas (ISO, NIST, etc.) |
| Reducción de errores      | Automatiza asignación de permisos con roles              |
| SSO (Single Sign-On)      | Un login para todas tus apps                             |

---

### 🧠 Resumen general

| Concepto            | Detalle                                                        |
| ------------------- | -------------------------------------------------------------- |
| ¿Qué es IAM?        | Sistema para gestionar usuarios, accesos y permisos            |
| ¿Cómo se autentica? | Contraseña, MFA, certificados, SSO                             |
| ¿Cómo se autoriza?  | Roles, políticas y reglas                                      |
| Herramienta usada   | Keycloak (open-source), alternativa a AzureAD o AWS IAM        |
| Ejemplo práctico    | Gustavo accede como admin a un panel solo si su rol lo permite |

---

[🔼](#índice)

---

## **583. IAM vs Active Directory**

### 📌 ¿Qué es IAM?

**IAM** (_Identity and Access Management_) es un **conjunto de políticas, procesos y tecnologías** que permiten gestionar **quién tiene acceso a qué recursos** en una organización.

✅ Se enfoca en:

- Usuarios (humanos o máquinas)
- Acceso a recursos digitales (apps, APIs, servicios)
- Autenticación (¿quién eres?)
- Autorización (¿qué puedes hacer?)

---

### 📌 ¿Qué es Active Directory (AD)?

**Active Directory** es un **servicio de directorio** desarrollado por **Microsoft** para gestionar identidades y accesos **en redes Windows**.

✅ Se enfoca en:

- Computadoras, impresoras, usuarios dentro de una red
- Inicios de sesión centralizados (SSO)
- Control de acceso basado en dominios, grupos y políticas de seguridad

---

### 🧠 Comparación general

| Característica                | IAM (ej: AWS IAM, Keycloak)         | Active Directory (AD)                             |
| ----------------------------- | ----------------------------------- | ------------------------------------------------- |
| **Origen**                    | Diseñado para la nube o apps web    | Diseñado para redes Windows locales               |
| **Usuarios**                  | Humanos, apps, servicios, APIs      | Humanos, PCs, impresoras                          |
| **Protocolo base**            | OAuth2, OpenID Connect, SAML        | LDAP, Kerberos, NTLM                              |
| **Autenticación**             | Tokens, MFA, login social, federado | Usuario/contraseña + Kerberos                     |
| **Autorización**              | Basado en roles/políticas           | Grupos de seguridad y GPOs                        |
| **Interfaz web para gestión** | Sí (ej: Keycloak, AWS IAM)          | Sí, pero requiere consola AD                      |
| **Soporte multiplataforma**   | Sí (Linux, Windows, Cloud, Web)     | Principalmente Windows                            |
| **SSO**                       | Sí, muy flexible con SAML y OIDC    | Sí, limitado a dominios y redes Windows           |
| **Ideal para...**             | Apps web, APIs, servicios cloud     | Empresas con infraestructura Microsoft            |
| **Ejemplo real**              | Login de usuarios en una app web    | Login de empleados en computadoras de una oficina |

---

### 🎯 ¿Entonces cuál elegir?

| Necesidad                            | Recomendación                       |
| ------------------------------------ | ----------------------------------- |
| Intranet empresarial Windows         | ✅ Active Directory                 |
| Aplicación web o sistema distribuido | ✅ IAM moderno (Keycloak, Auth0...) |
| Infraestructura en AWS               | ✅ AWS IAM                          |
| Gestión de usuarios + SSO web        | ✅ IAM (Keycloak, Azure AD B2C)     |

---

### 🛠️ ¿Cómo se instala?

#### 🔸 1. **Instalar Keycloak (IAM moderno)**

```bash
docker run -d --name keycloak \
  -e KEYCLOAK_ADMIN=admin \
  -e KEYCLOAK_ADMIN_PASSWORD=admin123 \
  -p 8080:8080 \
  quay.io/keycloak/keycloak:24.0.2 start-dev
```

- Accede: [http://localhost:8080](http://localhost:8080)
- Login: `admin` / `admin123`
- Crea usuarios, roles, apps web, etc.

---

#### 🔸 2. **Instalar Active Directory (en Windows Server)**

##### Requisitos:

- Windows Server (2016, 2019 o 2022)
- IP fija
- DNS configurado

##### Pasos rápidos:

1. Abre el "Server Manager"
2. Agrega roles y características → selecciona "Active Directory Domain Services (AD DS)"
3. Instala y promueve el servidor como controlador de dominio
4. Crea el dominio (ej: `empresa.local`)
5. Administra con “Active Directory Users and Computers”

---

### 🧪 Ejemplo práctico completo

#### Escenario:

Una empresa quiere gestionar:

- Accesos a su red de oficinas (equipos, archivos compartidos)
- Accesos a su app web de gestión de clientes

---

#### 🔐 Con Active Directory (red local):

1. Se crea un usuario `gustavo` en AD
2. Gustavo inicia sesión en su PC de oficina usando `gustavo@empresa.local`
3. Tiene acceso a carpetas compartidas según su grupo (`Ventas`)
4. Si renuncia, se desactiva su cuenta en AD

---

#### ☁️ Con IAM (Keycloak):

1. Se crea un usuario `gustavo` en Keycloak
2. Se le asigna el rol `admin` en la app web
3. Al iniciar sesión en la web (ej: `clientes.acme.com`), se autentica con Keycloak
4. Puede ver todos los clientes, crear, editar, borrar
5. Otro usuario con rol `viewer` solo puede ver

---

#### Diagrama resumen:

```
+--------------------+         +------------------+
| Gustavo (usuario)  |  -->    | Active Directory | --> PC oficina / Archivos
+--------------------+         +------------------+

+--------------------+         +---------------+         +------------+
| Gustavo (navegador)| --> OIDC|  Keycloak IAM | --> JWT | Web app API|
+--------------------+         +---------------+         +------------+
```

---

### 🎓 Conclusión

| Punto Clave                           | Explicación clara                                   |
| ------------------------------------- | --------------------------------------------------- |
| AD = gestión de identidad en redes    | PCs, usuarios, políticas dentro de una red Windows  |
| IAM = gestión en apps y servicios web | Usuarios web, APIs, cloud, apps con roles dinámicos |
| IAM es más flexible y multiplataforma | Ideal para ambientes modernos o híbridos            |

---

[🔼](#índice)

---

## **584. Gestión de Identidades y acceso (IAM) en AWS**

### 🔐 ¿Qué es IAM en AWS?

**IAM (Identity and Access Management)** es el **sistema de control de identidades y permisos** que usa **Amazon Web Services (AWS)** para decidir **quién puede hacer qué dentro de tu cuenta**.

#### 📌 ¿Para qué sirve?

- **Gestionar usuarios y grupos**
- **Dar o quitar permisos** a servicios de AWS (como EC2, S3, Lambda, etc.)
- **Autenticación y autorización** segura
- **Control de acceso mínimo necesario**

---

### 🎯 Ejemplo fácil de entender

**Ejemplo:**

Tienes una cuenta de AWS. Quieres que:

- Tú tengas acceso total (Administrador)
- Tu amigo Juan pueda **ver** archivos de S3 pero **no borrarlos**
- Tu app web suba imágenes a S3 pero no cree buckets nuevos

💡 Con IAM puedes **crear usuarios y políticas** para lograr eso.

---

### 🛠️ ¿Cómo funciona internamente?

- **Usuarios IAM** → Personas o apps que necesitan acceso.
- **Grupos IAM** → Conjuntos de usuarios con los mismos permisos.
- **Roles IAM** → Identidades temporales usadas por servicios o apps.
- **Políticas IAM** → Reglas (en JSON) que dicen qué puede hacer quién y dónde.

---

### 🔐 Ejemplo de política IAM en JSON

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": ["s3:GetObject"],
      "Resource": "arn:aws:s3:::mi-bucket/*"
    }
  ]
}
```

👆 Permite **ver (GetObject)** archivos dentro del bucket `mi-bucket`.

---

### 🧱 Estructura visual de IAM

```
CUENTA AWS
│
├── Usuario: Gustavo (admin)
│     └── Política: Acceso total
│
├── Usuario: Juan
│     └── Política: Solo lectura en S3
│
├── Rol: uploader-app
│     └── Política: Subir archivos a S3
```

---

### ⚙️ ¿Cómo se configura IAM en AWS?

> Puedes usar la consola web de AWS, la CLI (línea de comandos) o Terraform.

---

### ✅ Paso a paso para configurarlo desde la consola de AWS

#### 1. Ingresa a IAM

- Ve a [https://console.aws.amazon.com/iam/](https://console.aws.amazon.com/iam/)
- Menú izquierdo → **"Usuarios"** → **"Agregar usuario"**

#### 2. Crea un usuario llamado `juan`

- Tipo de acceso: **Acceso mediante consola**
- Contraseña temporal
- Asigna permisos:

  - Elige "Adjuntar políticas existentes directamente"
  - Selecciona: `AmazonS3ReadOnlyAccess`

#### 3. (Opcional) Agrúpalo

- Puedes crear un grupo llamado `LectoresS3` y asignar la política ahí.

#### 4. Verifica acceso

- Juan podrá ingresar a la consola con su cuenta, pero solo podrá **ver archivos de S3**.

---

### ☁️ ¿Y para una aplicación? (ej: app web que sube fotos)

#### 1. Crea un rol IAM para el servicio que usará la app (como Lambda o EC2)

- IAM → Roles → Crear rol
- Tipo de entidad: EC2 o Lambda
- Asocia política: por ejemplo:

```json
{
  "Effect": "Allow",
  "Action": ["s3:PutObject"],
  "Resource": "arn:aws:s3:::mi-bucket/subidas/*"
}
```

#### 2. Tu app usará ese rol automáticamente al ejecutarse

---

### 🧪 Ejemplo práctico completo

#### 🎯 Escenario:

Eres dueño de una cuenta AWS y quieres:

1. Tener un **usuario administrador** (tú)
2. Crear un **usuario Juan** que **solo pueda ver objetos de S3**
3. Crear un **rol para tu app** que pueda **subir imágenes al bucket `imagenes-app`**

---

#### 🛠️ Pasos resumidos:

| Elemento        | Acción                                                                 |
| --------------- | ---------------------------------------------------------------------- |
| Usuario Gustavo | Ya está (raíz o admin)                                                 |
| Usuario Juan    | Crear usuario → Política `AmazonS3ReadOnlyAccess`                      |
| App Web         | Crear **rol IAM** para EC2/Lambda → Política personalizada `PutObject` |

---

#### 🌐 Visual en consola de AWS:

```
IAM
├── Usuarios
│   ├── gustavo (Admin)
│   └── juan (Lectura S3)
│
└── Roles
    └── subir-imagenes-app
         └── Acción: s3:PutObject sobre arn:aws:s3:::imagenes-app/*
```

---

### 🔐 ¿IAM es seguro?

✅ Sí, si sigues buenas prácticas como:

- Aplicar **principio de menor privilegio**
- Usar **MFA (autenticación de dos factores)**
- Rotar claves
- Monitorear con **CloudTrail**

---

### 📦 Extras útiles:

- CLI: `aws iam create-user`, `aws iam attach-user-policy`
- Terraform: puedes crear políticas IAM como código
- CloudTrail: para auditar acciones en IAM
- IAM Access Analyzer: para revisar si estás dando más acceso del necesario

---

### 🎓 Conclusión rápida

| IAM en AWS te permite...                      | Beneficio                                         |
| --------------------------------------------- | ------------------------------------------------- |
| Controlar quién accede a qué recurso          | Seguridad granular                                |
| Crear roles para apps o servicios             | Accesos automáticos sin claves                    |
| Usar políticas JSON                           | Definición exacta de permisos                     |
| Auditar todo con CloudTrail                   | Detectar accesos no autorizados                   |
| Integrarse con servicios como EC2, S3, Lambda | Automatización segura de tu infraestructura cloud |

---

[🔼](#índice)

---

## **585. Autenticación y Autorización: SAML, OAUTH, 2FA**

### 🧠 ¿Qué es la **Autenticación**?

Es el proceso de **verificar la identidad de un usuario**.

> Ejemplo: cuando ingresas a una web con tu usuario y contraseña, estás autenticándote.

---

### 🧠 ¿Qué es la **Autorización**?

Es el proceso de **verificar qué acciones puede realizar ese usuario** después de autenticarse.

> Ejemplo: un usuario puede entrar al sistema (autenticación), pero solo puede ver su perfil, no editar usuarios (autorización).

---

### 🛠️ Tecnologías de autenticación/autorización que veremos:

| Tecnología | Tipo                | ¿Para qué sirve?                                               |
| ---------- | ------------------- | -------------------------------------------------------------- |
| **SAML**   | Autenticación (SSO) | Permite a empresas usar un solo login para múltiples servicios |
| **OAuth**  | Autorización        | Permite a apps acceder a tus datos sin compartir contraseña    |
| **2FA**    | Autenticación extra | Añade una segunda capa de seguridad (como un código SMS o app) |

---

### 🧩 1. SAML (Security Assertion Markup Language)

**¿Qué es?**

- Es un protocolo usado para **SSO (Single Sign-On)**: iniciar sesión una sola vez para usar múltiples servicios.

**¿Cómo funciona?**

1. Vas a una app (como Gmail corporativo).
2. Esta app redirige al **proveedor de identidad** (ej: Okta, Azure AD).
3. Te autenticas allí (una sola vez).
4. Recibes un **"assertion SAML"** (como un pase digital).
5. La app confía en ese pase y te deja entrar.

#### ✨ Ejemplo:

- Universidad: usa Google Workspace + Moodle + Zoom
- Un alumno se autentica una vez con su cuenta institucional
- Ya no necesita volver a loguearse en Zoom ni Moodle

---

#### 🧰 Instalación / Implementación de SAML:

1. Tener un **Identity Provider (IdP)** (como Okta, Azure AD o Google).
2. Tener una **aplicación web** compatible con SAML (como Moodle, GitLab, etc.).
3. Configurar el intercambio de metadatos:

   - La app debe conocer el IdP
   - El IdP debe reconocer la app

4. Usar certificados y URLs para firmar/verificar las sesiones

---

### 🧩 2. OAuth 2.0 (Open Authorization)

**¿Qué es?**

- Es un protocolo de **autorización delegada**.
- Permite que **una app pueda acceder a tus datos de otra app sin conocer tu contraseña**.

#### ✨ Ejemplo:

- Una app web de edición de imágenes te permite **subir fotos desde Google Drive**.
- Al presionar "Conectar con Google":

  - Google te muestra un mensaje: “¿Quieres darle acceso a esta app?”
  - Tú aceptas y se emite un **token** que permite a la app acceder a tus archivos sin tu contraseña.

---

#### 🧰 Instalación / Implementación de OAuth 2.0:

1. Registra tu app en el proveedor (ej: Google Developer Console).
2. Obtienes:

   - `client_id`
   - `client_secret`

3. En tu app web:

   - Redirige al usuario a `https://accounts.google.com/o/oauth2/auth?...`
   - Google redirige de vuelta con un **authorization code**
   - Tu backend intercambia el código por un **access token**

4. Usas el **access token** para acceder a la API de Google Drive, Gmail, etc.

---

### 🧩 3. 2FA (Autenticación de dos factores)

**¿Qué es?**

- Es una medida extra de seguridad que exige **dos pruebas** para autenticarte:

| Factor          | Ejemplo                     |
| --------------- | --------------------------- |
| Algo que sabes  | Contraseña                  |
| Algo que tienes | Código de app o SMS         |
| Algo que eres   | Huella, rostro (biométrico) |

---

#### ✨ Ejemplo:

- Inicias sesión con tu contraseña
- Luego te pide un código de **Google Authenticator**
- Solo si tienes ambos, puedes entrar

---

#### 🧰 Instalación / Implementación de 2FA (con apps como Google Authenticator)

1. En tu app o backend, genera un **secreto compartido (TOTP)**.
2. Muestra al usuario un **QR Code** (puede usar `speakeasy` y `qrcode` en Node.js).
3. El usuario escanea el código con una app como Google Authenticator.
4. Cada vez que el usuario inicia sesión, debe escribir el código de la app.
5. Tu sistema verifica si el código es correcto (válido en ese momento).

---

### ✅ Ejemplo completo: Login en una web con SSO + OAuth + 2FA

#### 🎯 Escenario:

Tu empresa usa:

- Microsoft Azure AD para login único (SAML)
- Una app externa que quiere ver tu calendario de Outlook (OAuth)
- Y fuerza a todos los usuarios a usar 2FA

#### 🧪 Paso a paso:

1. Gustavo accede a \[tuempresa.zoom.com]
2. Es redirigido a Azure AD (SSO SAML)
3. Ingresa su usuario + contraseña
4. Azure le pide un código 2FA de Microsoft Authenticator
5. Una vez autenticado, entra a Zoom sin poner más credenciales
6. En Zoom, una app de terceros pide acceso a su calendario
7. Gustavo acepta → se usa OAuth 2.0 → se genera un token temporal
8. La app puede ver (pero no modificar) su calendario

---

### 🧱 Comparación rápida

| Tecnología | ¿Autenticación o Autorización? | ¿Para quién?                     | Método                          |
| ---------- | ------------------------------ | -------------------------------- | ------------------------------- |
| SAML       | Autenticación (SSO)            | Empresas y usuarios corporativos | Redirección a IdP + XML firmado |
| OAuth 2.0  | Autorización delegada          | Apps de terceros                 | Access token                    |
| 2FA        | Autenticación extra            | Cualquier usuario                | Contraseña + código adicional   |

---

### 🎓 Conclusión

✅ **SAML**: perfecto para que empleados usen múltiples apps con un solo login

✅ **OAuth**: ideal para que apps accedan a tus recursos sin tu contraseña

✅ **2FA**: obligatorio hoy en día para proteger cualquier cuenta

---

[🔼](#índice)

---

## **586. Gestión y análisis de riesgos de Ciberseguridad**

### 🧠 ¿Qué es la gestión de riesgos en ciberseguridad?

Es un **proceso estructurado para identificar, evaluar y tratar los riesgos** relacionados con los activos digitales de una organización (datos, sistemas, redes, personas).

---

#### 🎯 Objetivo principal:

Reducir las probabilidades de que ocurran incidentes (como ataques, fugas de datos, ransomware) y minimizar su impacto.

---

### 🧩 ¿Qué es un riesgo?

Un riesgo es la **posibilidad de que una amenaza explote una vulnerabilidad** y cause un impacto.

🔄 Fórmula general:

```text
Riesgo = Amenaza × Vulnerabilidad × Impacto
```

---

### 📌 Términos clave

| Término            | Definición breve                          | Ejemplo                                                  |
| ------------------ | ----------------------------------------- | -------------------------------------------------------- |
| **Activo**         | Cualquier recurso valioso para la empresa | Base de datos de clientes, sistema ERP, archivos del CEO |
| **Amenaza**        | Algo que puede causar daño                | Ransomware, hacker, error humano                         |
| **Vulnerabilidad** | Debilidad explotable por amenazas         | Software sin actualizar, contraseñas débiles             |
| **Impacto**        | Consecuencia si se materializa la amenaza | Pérdida de datos, daño reputacional, sanción legal       |
| **Probabilidad**   | Posibilidad de que ocurra el evento       | Alta, media, baja                                        |

---

### 🧭 Etapas de la Gestión de Riesgos (según ISO 27005 / NIST)

1. **Identificación de activos**
2. **Identificación de amenazas y vulnerabilidades**
3. **Evaluación del riesgo**
4. **Tratamiento del riesgo**
5. **Monitoreo y revisión**

---

### 🧰 ¿Cómo se instala o aplica en la práctica?

Aunque no se "instala" como software único, puedes implementar este proceso **con herramientas y marcos**. Aquí te explico **cómo lo haces paso a paso**.

---

### 🧪 PASO A PASO DETALLADO

#### 1. 🔍 Identificar activos

Haz una lista de los activos críticos:

- Servidores de bases de datos
- Sistemas de correo
- Aplicaciones web
- Documentos financieros
- Personal clave

👉 Herramientas: Excel, CMDBs (AssetTiger, GLPI), scripts de inventario

---

#### 2. ⚠️ Identificar amenazas y vulnerabilidades

Ejemplos de amenazas:

- Ataques DDoS
- Phishing
- Malware
- Insider threat (empleado malicioso)

Ejemplos de vulnerabilidades:

- Contraseñas débiles
- Software sin parches
- Servicios expuestos en internet

👉 Herramientas: Nessus, OpenVAS, CVE Search, Shodan

---

#### 3. 📊 Evaluar los riesgos

Evalúa **probabilidad e impacto**, por ejemplo con una **matriz de riesgo**:

|             | Impacto Bajo | Impacto Medio | Impacto Alto |
| ----------- | ------------ | ------------- | ------------ |
| Prob. Alta  | Medio        | Alto          | Crítico      |
| Prob. Media | Bajo         | Medio         | Alto         |
| Prob. Baja  | Bajo         | Bajo          | Medio        |

🔢 Puedes asignar valores numéricos y calcular el nivel de riesgo.

---

#### 4. 🛡️ Tratar los riesgos

Decides qué hacer con cada riesgo:

- **Mitigar** (reducir): aplicar firewall, parches, 2FA
- **Aceptar**: si el costo de mitigarlo es mayor que el impacto
- **Transferir**: usar seguros o servicios externos
- **Eliminar**: dejar de usar el activo vulnerable

---

#### 5. 📈 Monitorear y revisar

Esto no es una tarea de una sola vez. Hay que revisar regularmente los riesgos y activos.

👉 Herramientas: SIEM (como Splunk), informes de escaneo, dashboards, auditorías.

---

### 🛠️ Herramientas para gestión y análisis de riesgos

| Herramienta                              | Para qué sirve                                  |
| ---------------------------------------- | ----------------------------------------------- |
| **OCTAVE**                               | Metodología de evaluación de riesgos            |
| **FAIR**                                 | Modelo cuantitativo de riesgo                   |
| **ISO/IEC 27005**                        | Guía para análisis y gestión de riesgos         |
| **NIST 800-30**                          | Metodología paso a paso del gobierno de EE. UU. |
| **Excel/Sheets**                         | Para matrices de riesgos simples                |
| **GRC Tools (ex: RiskWatch, LogicGate)** | Gestión profesional de riesgos                  |

---

### ✅ Ejemplo completo práctico

Supón que trabajas en una empresa que almacena información de clientes en una base de datos MySQL.

#### 🧱 Escenario:

- Activo: Servidor MySQL de clientes
- Amenaza: Ataque SQL Injection
- Vulnerabilidad: No hay validación de entradas
- Impacto: Alto (pérdida de datos, multa legal)
- Probabilidad: Alta (aplicación antigua sin protección)

---

#### 📊 Evaluación:

| Elemento        | Valor asignado |
| --------------- | -------------- |
| Probabilidad    | Alta           |
| Impacto         | Alto           |
| Nivel de riesgo | Crítico        |

---

#### 🛡️ Tratamiento:

- Implementar validaciones de entrada (mitigación)
- Instalar WAF (firewall de aplicaciones web)
- Hacer pruebas de pentesting cada trimestre
- Capacitar a desarrolladores

---

#### 📈 Seguimiento:

- Revisar logs de ataques
- Verificar parches aplicados
- Actualizar la matriz cada 3 meses

---

### 🎓 Conclusión

La gestión de riesgos en ciberseguridad es **clave para proteger los activos más valiosos** de una organización. Se puede empezar **con herramientas simples como Excel**, y luego escalar a **métodos más robustos (FAIR, ISO, GRCs)**.

---

[🔼](#índice)

---

## **587. Modelos de gestión y análisis de riesgos de Ciberseguridad**

### 🧠 ¿Qué es un modelo de gestión y análisis de riesgos en ciberseguridad?

Un **modelo de gestión y análisis de riesgos** es una **estructura organizada o metodología** que guía a las organizaciones a:

1. Identificar sus activos digitales.
2. Detectar amenazas y vulnerabilidades.
3. Evaluar la probabilidad de ocurrencia e impacto.
4. Tomar decisiones para minimizar los riesgos.

---

### 🧩 ¿Por qué son importantes?

Porque te permiten tomar **decisiones informadas** en seguridad, protegiendo activos críticos como:

- Bases de datos de clientes,
- Aplicaciones web,
- Infraestructura en la nube,
- Información financiera o confidencial.

---

### 🛠️ Modelos más usados en el análisis y gestión de riesgos

Aquí te explico **los 4 modelos más conocidos**, con lenguaje sencillo y ejemplos reales:

---

#### 1. 🔐 **Modelo NIST SP 800-30 (EE. UU.)**

**Instituto Nacional de Estándares y Tecnología**. Es uno de los más utilizados mundialmente.

**Etapas**:

1. Identificar amenazas, activos y vulnerabilidades.
2. Evaluar la probabilidad e impacto.
3. Determinar el nivel de riesgo.
4. Aplicar controles.
5. Documentar y revisar.

✅ **Ejemplo**:

- Activo: Web de clientes.
- Amenaza: Ataque SQL Injection.
- Vulnerabilidad: No hay validación.
- Impacto: Alto.
- Control: WAF, sanitizar inputs.

---

#### 2. 📈 **FAIR (Factor Analysis of Information Risk)**

Modelo **cuantitativo** que da un valor en **dólares o impacto numérico** al riesgo. Muy útil para que la gerencia entienda los riesgos en su lenguaje.

**Componentes**:

- Probabilidad de evento de pérdida.
- Magnitud de la pérdida.
- Tipo de amenazas (internas/externas).

✅ **Ejemplo**:

- Costo estimado por filtración: \$100,000.
- Probabilidad: 10% anual.
- Riesgo anualizado: \$10,000.

---

#### 3. 🛡️ **ISO/IEC 27005**

Parte del estándar ISO 27000, específicamente diseñado para la **gestión de riesgos en seguridad de la información**.

**Fases**:

1. Contexto organizacional.
2. Identificación de riesgos.
3. Análisis y evaluación.
4. Tratamiento.
5. Aceptación y comunicación.

✅ Muy usado por empresas que buscan **certificaciones ISO 27001**.

---

#### 4. 🧪 **OCTAVE (Operationally Critical Threat, Asset, and Vulnerability Evaluation)**

Diseñado para organizaciones pequeñas o medianas.

**Enfocado en los procesos y personas**. No solo analiza tecnología.

**Fases**:

- Identificar activos críticos.
- Valorar amenazas organizacionales.
- Evaluar vulnerabilidades tecnológicas.
- Crear planes de mitigación.

✅ Ejemplo: Si un empleado puede copiar datos a un USB sin supervisión → riesgo interno alto.

---

### 🧰 ¿Cómo se "instalan" o aplican estos modelos?

No se instalan como software, pero **puedes aplicarlos así**:

| Acción                      | Herramienta o recurso                    |
| --------------------------- | ---------------------------------------- |
| Inventario de activos       | Excel, AssetTiger, GLPI                  |
| Escaneo de vulnerabilidades | Nessus, OpenVAS, Qualys                  |
| Matriz de riesgos           | Google Sheets, ISO templates             |
| Evaluación cuantitativa     | FAIR tools, calculadora de riesgos       |
| Reportes y monitoreo        | Power BI, Kibana, Splunk, dashboards GRC |

---

### ✅ Ejemplo práctico paso a paso (Modelo NIST SP 800-30)

#### 🧱 Escenario:

Empresa mediana con una web para clientes donde gestionan reclamos y pagos. Usan una base de datos PostgreSQL sin cifrado.

---

#### **1. Identificación de activos**

- Web: `clientes.miservicio.com`
- Base de datos: PostgreSQL local
- Usuario: cliente final

---

#### **2. Amenazas y vulnerabilidades**

| Amenaza               | Vulnerabilidad                |
| --------------------- | ----------------------------- |
| Inyección SQL         | No hay validación de entradas |
| Exfiltración de datos | BD sin cifrado                |
| Ransomware            | Backups no automatizados      |

---

#### **3. Evaluación de riesgos**

Creamos una **matriz simple**:

| Riesgo        | Probabilidad | Impacto | Nivel   |
| ------------- | ------------ | ------- | ------- |
| SQL Injection | Alta         | Alto    | Crítico |
| Fuga de datos | Media        | Alto    | Alto    |
| Ransomware    | Media        | Medio   | Medio   |

---

#### **4. Tratamiento del riesgo**

| Riesgo        | Acción                                        |
| ------------- | --------------------------------------------- |
| SQL Injection | Implementar validación + WAF                  |
| Fuga de datos | Cifrar base de datos con pgcrypto             |
| Ransomware    | Automatizar backups en S3 + pruebas mensuales |

---

#### **5. Monitoreo y revisión**

- Revisar logs con Wazuh o Splunk.
- Verificar alertas de seguridad.
- Actualizar matriz cada 3 meses.

---

### 📊 Resultado final en Excel (sugerido):

Puedes crear un archivo con estas columnas:

| Activo       | Amenaza       | Vulnerabilidad      | Impacto | Probabilidad | Riesgo  | Control aplicado    |
| ------------ | ------------- | ------------------- | ------- | ------------ | ------- | ------------------- |
| Web clientes | SQL Injection | Entrada sin validar | Alto    | Alta         | Crítico | WAF + validación JS |

¿Te gustaría que te prepare esa matriz de Excel ya hecha? Puedo exportarla y darte un modelo editable.

---

### 🧠 Conclusión

Un modelo de gestión y análisis de riesgos **no es un software**, sino una **metodología organizada**. Puedes usar herramientas como Excel, SIEM, escáneres de vulnerabilidades o plataformas GRC para ayudarte a aplicar cualquiera de estos modelos.

---

[🔼](#índice)

---

## **588. Modelado de amenazas de Ciberseguridad: MITRE ATT&CK, STRIDE**

### 🧠 ¿Qué es el Modelado de Amenazas?

El **modelado de amenazas** es una **técnica proactiva de ciberseguridad** que permite identificar:

- Qué puede salir mal (amenazas).
- Qué tan probable es.
- Qué impacto tendría.
- Qué controles se necesitan para prevenirlo o detectarlo.

Es como hacerle una “radiografía” a un sistema para entender cómo lo podrían atacar, antes de que lo ataquen.

---

### 🚨 ¿Por qué es importante?

Porque te ayuda a:

✅ Identificar vectores de ataque antes que un atacante.

✅ Priorizar esfuerzos de defensa (no todo tiene el mismo riesgo).

✅ Diseñar controles específicos.

✅ Conectar con otros procesos como el análisis de riesgos o pentesting.

---

### 📚 1. STRIDE – Modelo de Amenazas de Microsoft

**STRIDE** es un acrónimo de 6 tipos de amenazas comunes:

| Letra | Tipo de amenaza         | ¿Qué significa?                          | Ejemplo fácil                                      |
| ----- | ----------------------- | ---------------------------------------- | -------------------------------------------------- |
| **S** | Spoofing                | Suplantación de identidad                | Usuario A se hace pasar por B                      |
| **T** | Tampering               | Manipulación de datos                    | Alguien altera un archivo de logs                  |
| **R** | Repudiation             | Negación de acciones sin poder rastrear  | Usuario borra registros sin dejar rastro           |
| **I** | Information Disclosure  | Divulgación no autorizada de información | Filtración de datos personales                     |
| **D** | Denial of Service (DoS) | Negación de servicio                     | Sobrecarga del sistema para dejarlo fuera de línea |
| **E** | Elevation of Privilege  | Escalada de privilegios                  | Usuario básico obtiene acceso root                 |

#### 🛠️ ¿Cómo se usa STRIDE?

1. Se analiza el sistema (app web, API, red, etc.)
2. Se dibuja un **Data Flow Diagram (DFD)** con componentes (usuarios, procesos, bases de datos).
3. A cada elemento se le aplican los 6 tipos de amenazas.

---

### 🧰 2. MITRE ATT\&CK – Marco basado en ataques reales

**MITRE ATT\&CK** (Adversarial Tactics, Techniques & Common Knowledge) es una base de datos de:

- Tácticas (lo que el atacante quiere hacer).
- Técnicas (cómo lo hace).
- Subtécnicas (detalles específicos).
- Grupos APT (atacantes conocidos que usan estas técnicas).
- Herramientas (Malware, scripts, etc).

Está basado en **observaciones reales** de ataques y **ayuda a entender cómo piensan los atacantes**.

#### 📦 Estructura básica:

| Táctica              | Ejemplo de Técnica           |
| -------------------- | ---------------------------- |
| Initial Access       | Phishing, explotación de RDP |
| Execution            | Scripts, PowerShell          |
| Persistence          | Registro de Windows          |
| Privilege Escalation | Exploits de kernel           |
| Defense Evasion      | Deshabilitar antivirus       |
| Credential Access    | Keylogging, Dump de LSASS    |

> 👉 Puedes verlo en [https://attack.mitre.org](https://attack.mitre.org)

---

### 🛠️ ¿Cómo “se instala” MITRE ATT\&CK?

No es software para instalar, **es una base de conocimiento** que se puede:

✅ Usar desde la web oficial.

✅ Integrar con SIEMs como Splunk, ELK, Wazuh.

✅ Usar con herramientas como MITRE CALDERA (automatización de emulación de ataques).

✅ Usar en hojas Excel, Power BI o gráficos para mapeo.

---

### ✅ Ejemplo completo paso a paso

#### 🧱 Escenario ficticio:

Empresa que tiene una aplicación web donde los clientes hacen pagos y reclamos.

#### 🔍 Paso 1: Dibujo de componentes (simplificado)

- Usuario
- Aplicación web (frontend/backend)
- Base de datos (MySQL)
- API REST
- Admin dashboard

---

#### 🧪 Paso 2: Aplicamos STRIDE

| Componente     | Amenaza STRIDE         | Descripción del riesgo                         | Mitigación                    |
| -------------- | ---------------------- | ---------------------------------------------- | ----------------------------- |
| Login web      | Spoofing               | Un atacante intenta adivinar la contraseña     | MFA, política de contraseñas  |
| API            | Tampering              | Se modifican parámetros para manipular datos   | Validación estricta, logs     |
| Base de datos  | Information Disclosure | Acceso no autorizado a datos sensibles         | Cifrado, roles estrictos      |
| Logs           | Repudiation            | Un usuario borra su historial sin dejar huella | Logs firmados y centralizados |
| Backend        | DoS                    | Lluvia de peticiones satura el servicio        | WAF, rate limiting            |
| Usuario básico | Elevation of Privilege | Intenta acceder al panel de administrador      | RBAC, autenticación por rol   |

---

#### 🧩 Paso 3: Aplicamos MITRE ATT\&CK

Usamos las tácticas y técnicas observadas:

| Táctica           | Técnica usada                       | Ejemplo en nuestro caso                    | Defensa recomendada                  |
| ----------------- | ----------------------------------- | ------------------------------------------ | ------------------------------------ |
| Initial Access    | T1566.001: Spearphishing Attachment | Correo con archivo falso al admin          | Filtrado de correo, concientización  |
| Execution         | T1059.001: PowerShell               | Script ejecutado tras abrir archivo        | Restringir PowerShell, EDR           |
| Credential Access | T1003.001: LSASS Memory Dumping     | Robo de credenciales del servidor          | Protecciones a procesos críticos     |
| Persistence       | T1547.001: Registry Run Keys        | Malware se reinicia al encender el sistema | Monitorización de registros          |
| Command & Control | T1071.001: Web Protocols            | Comunicación a un C2 por HTTP              | IDS, bloqueo de dominios sospechosos |

---

#### 📈 Representación visual (opcional)

Puedes usar herramientas como:

- [Threat Dragon](https://owasp.org/www-project-threat-dragon/) para STRIDE.
- Excel + MITRE ATT\&CK Matrix.
- Splunk Enterprise Security (que integra ATT\&CK).
- MITRE Navigator ([https://mitre-attack.github.io/attack-navigator/](https://mitre-attack.github.io/attack-navigator/)) para hacer matrices visuales.

---

### 📌 Conclusión

| Marco         | Ideal para...                         | Nivel de uso  |
| ------------- | ------------------------------------- | ------------- |
| STRIDE        | Aplicaciones web, APIs, apps internas | Fácil de usar |
| MITRE ATT\&CK | Analizar tácticas de atacantes reales | Más avanzado  |

Ambos modelos se **complementan**. STRIDE es más estructurado y técnico para análisis estático; ATT\&CK es dinámico y se basa en inteligencia real de amenazas.

---

[🔼](#índice)

---

## **589. Gestión de riesgos de ciberseguridad mediante modelado de amenazas**

### 📌 ¿Qué es la gestión de riesgos de ciberseguridad?

Es un **proceso sistemático** para:

1. **Identificar** los activos críticos de una organización.
2. **Detectar amenazas y vulnerabilidades** que puedan afectar a esos activos.
3. **Evaluar el impacto y la probabilidad** de que ocurran incidentes.
4. **Mitigar o controlar** los riesgos.
5. **Monitorear y revisar continuamente**.

> 🎯 _Objetivo:_ reducir al mínimo el daño que puede causar un ataque, enfocándose en lo más importante y probable.

---

### 🎯 ¿Qué es el modelado de amenazas?

Es una **herramienta dentro de la gestión de riesgos**, que ayuda a entender **cómo un atacante podría comprometer un sistema o proceso**, antes de que ocurra.

> Es como anticiparse a los movimientos del enemigo antes de una guerra.

---

### 🧠 ¿Cómo se relacionan?

El **modelado de amenazas** se integra en la fase de **identificación y análisis de riesgos**:

- Ayuda a detectar **vectores de ataque posibles**.
- Permite visualizar el **impacto sobre activos críticos**.
- Facilita la **toma de decisiones sobre controles de seguridad**.

---

### 📚 Modelos comunes de modelado de amenazas

Hay muchos, pero los más conocidos (y fáciles de aplicar) son:

#### 1. **STRIDE** (de Microsoft)

Modelo para clasificar amenazas:

| Letra | Tipo de amenaza         | Ejemplo práctico                      |
| ----- | ----------------------- | ------------------------------------- |
| S     | Spoofing                | Suplantar identidad con contraseña    |
| T     | Tampering               | Alterar datos en tránsito             |
| R     | Repudiation             | Negar haber hecho algo sin evidencia  |
| I     | Information Disclosure  | Robo de información confidencial      |
| D     | Denial of Service (DoS) | Caída del sistema por sobrecarga      |
| E     | Elevation of Privilege  | Escalada de permisos sin autorización |

#### 2. **MITRE ATT\&CK**

Base de datos pública con técnicas reales que los atacantes usan, organizada por tácticas.

| Táctica              | Técnica (ejemplo)         |
| -------------------- | ------------------------- |
| Initial Access       | Phishing                  |
| Privilege Escalation | Exploits del sistema      |
| Persistence          | Malware con autoejecución |

---

### 🧰 ¿Cómo se “instala” o implementa?

No se instala como un programa, pero sí puedes usar herramientas para modelar amenazas:

#### ✔️ Herramientas útiles

| Herramienta                    | ¿Para qué sirve?              | Enlace                                                                             |
| ------------------------------ | ----------------------------- | ---------------------------------------------------------------------------------- |
| Threat Dragon (OWASP)          | Modelado STRIDE gráfico       | [Enlace](https://owasp.org/www-project-threat-dragon/)                             |
| MITRE ATT\&CK Navigator        | Crear matrices personalizadas | [Enlace](https://mitre-attack.github.io/attack-navigator/)                         |
| Microsoft Threat Modeling Tool | Herramienta visual de STRIDE  | [Descarga](https://www.microsoft.com/en-us/securityengineering/sdl/threatmodeling) |
| Lucidchart / Draw\.io          | Crear DFDs manuales           | -                                                                                  |

---

### 🧪 Ejemplo completo paso a paso

#### 🧱 Escenario:

Una **empresa financiera** tiene una aplicación web donde los clientes:

- Inician sesión.
- Consultan saldo.
- Hacen transferencias.

#### 🎯 Objetivo:

Aplicar **gestión de riesgos con modelado de amenazas** para reducir la posibilidad de un ataque grave.

---

#### ✅ Paso 1: Identificación de activos

| Activo                    | Valor para el negocio |
| ------------------------- | --------------------- |
| Aplicación web de banca   | Muy alto              |
| Base de datos de clientes | Crítico               |
| Servidor backend/API      | Muy alto              |
| Red interna               | Alto                  |

---

#### ✅ Paso 2: Modelado de amenazas con STRIDE

Dibujamos un **diagrama de flujo de datos (DFD)** con:

- Usuario
- Frontend Web
- API REST
- Base de datos

Y analizamos amenazas:

| Componente           | Tipo STRIDE            | Ejemplo fácil                          | Riesgo                         | Control recomendado               |
| -------------------- | ---------------------- | -------------------------------------- | ------------------------------ | --------------------------------- |
| Login Web            | Spoofing               | Atacante adivina contraseña            | Robo de cuentas                | Habilitar MFA, limitar intentos   |
| API de transferencia | Tampering              | Cambiar el monto enviado por URL       | Transferencias manipuladas     | Validación backend, cifrado HTTPS |
| Servidor             | Elevation of Privilege | Usuario explota bug para hacerse admin | Acceso total al sistema        | Parches, RBAC                     |
| BD                   | Information Disclosure | Ataque SQLi extrae datos clientes      | Filtración de datos personales | Prepared statements, WAF, logging |
| Red Interna          | DoS                    | Botnet satura servicios                | Interrupción de operaciones    | Firewalls, mitigación de tráfico  |

---

#### ✅ Paso 3: Evaluación de riesgos

Se estima:

- **Probabilidad** (Alta, Media, Baja).
- **Impacto** (Crítico, Alto, Medio, Bajo).

| Riesgo                  | Probabilidad | Impacto | Nivel de Riesgo |
| ----------------------- | ------------ | ------- | --------------- |
| Robo de cuentas         | Media        | Alto    | Alto            |
| SQL Injection           | Alta         | Crítico | Muy Alto        |
| Escalada de privilegios | Baja         | Crítico | Alto            |
| DoS por red             | Media        | Medio   | Medio           |

---

#### ✅ Paso 4: Plan de mitigación

| Riesgo                  | Control                                         |
| ----------------------- | ----------------------------------------------- |
| SQL Injection           | Sanitizar entradas, usar ORM, WAF               |
| Robo de cuentas         | MFA, alertas de inicio de sesión sospechoso     |
| Escalada de privilegios | Segmentación de roles, auditorías               |
| DoS                     | Limitar solicitudes por IP, servicios anti-DDoS |

---

#### ✅ Paso 5: Documentación y monitoreo

- Se documenta en formato de **plan de tratamiento de riesgos**.
- Se define un **plan de revisión** mensual o trimestral.
- Se enlaza con herramientas SIEM para detección proactiva (Splunk, Wazuh, etc.).

---

### ✅ Conclusión

| Elemento               | ¿Qué aprendimos?                                                          |
| ---------------------- | ------------------------------------------------------------------------- |
| Modelado de amenazas   | Te ayuda a pensar como un atacante                                        |
| Gestión de riesgos     | Te obliga a priorizar y tomar decisiones informadas                       |
| STRIDE y MITRE ATT\&CK | Se complementan: uno es estructurado, el otro basado en inteligencia real |
| Valor real             | Mejora la seguridad sin gastar de más; dirige esfuerzos donde más importa |

---

[🔼](#índice)

---

| **Inicio**         | **atrás 8**                                                                             |
| ------------------ | --------------------------------------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./6_8_Firma_digital_Certificado_digital_y_PKI_Infraestructura_de_clave_publica.md) |
