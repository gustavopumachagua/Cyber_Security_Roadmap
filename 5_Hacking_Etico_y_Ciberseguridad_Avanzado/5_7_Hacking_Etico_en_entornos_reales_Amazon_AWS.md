| **Inicio**         | **atrás 6**                                              |
| ------------------ | -------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./5_6_Hacking_etico_y_post_explotacion_avanzada.md) |

---

## **Índice**

| Temario                                                                                                    |
| ---------------------------------------------------------------------------------------------------------- |
| [359. Arquitectura y registro en la nube (AWS)](#359-arquitectura-y-registro-en-la-nube-aws)               |
| [360. Registro y configuración de una cuenta en AWS](#360-registro-y-configuración-de-una-cuenta-en-aws)   |
| [361. Infraestructura de red en la nube (AWS)](#361-infraestructura-de-red-en-la-nube-aws)                 |
| [362. Seguridad y computación en la nube (AWS)](#362-seguridad-y-computación-en-la-nube-aws)               |
| [363. Balanceadores y almacenamiento en la nube (AWS)](#363-balanceadores-y-almacenamiento-en-la-nube-aws) |
| [364. Recopilación de información en un entorno real](#364-recopilación-de-información-en-un-entorno-real) |
| [365. Controles de seguridad en un entorno real](#365-controles-de-seguridad-en-un-entorno-real)           |
| [366. Auditando la infraestructura interna](#366-auditando-la-infraestructura-interna)                     |
| [367. Tipos de auditorías de seguridad](#368-eliminando-el-entorno-en-la-nube-aws)                         |
| [368. Eliminando el entorno en la nube (AWS)](#368-eliminando-el-entorno-en-la-nube-aws)                   |

---

# **Hacking Etico en entornos reales (Amazon AWS)**

## **359. Arquitectura y registro en la nube (AWS)**

![AWS](../img/5_Hacking_Etico_y_Ciberseguridad_Avanzado/AWS.png "AWS")

### 🧠 ¿Qué es AWS?

**Amazon Web Services (AWS)** es una **plataforma de servicios en la nube** de Amazon. Te permite alquilar infraestructura como:

- Servidores (EC2)
- Bases de datos (RDS)
- Almacenamiento de archivos (S3)
- Redes virtuales (VPC)
- Y muchos otros servicios

Con AWS puedes lanzar proyectos sin comprar hardware físico, y pagar **solo por lo que usas**.

---

### 🧱 ¿Qué es la arquitectura en la nube?

La **arquitectura en la nube** se refiere a cómo diseñamos y organizamos los **componentes tecnológicos** en una nube como AWS para construir soluciones como:

- Sitios web
- Aplicaciones móviles
- Plataformas de análisis de datos
- Infraestructuras empresariales

#### 🔧 Componentes comunes en una arquitectura en AWS

| Componente     | Servicio AWS              | ¿Para qué sirve?            |
| -------------- | ------------------------- | --------------------------- |
| Computación    | EC2, Lambda               | Ejecutar aplicaciones       |
| Almacenamiento | S3, EBS                   | Guardar archivos y discos   |
| Base de datos  | RDS, DynamoDB             | Datos estructurados o NoSQL |
| Redes          | VPC, Load Balancer        | Aislar y enrutar tráfico    |
| Seguridad      | IAM, Security Groups, KMS | Control de acceso y cifrado |
| Supervisión    | CloudWatch, CloudTrail    | Logs, métricas, auditorías  |

---

### 📝 ¿Cómo me registro en AWS?

#### Paso 1: Ir al sitio oficial

Accede a: [https://aws.amazon.com](https://aws.amazon.com)

Haz clic en **"Create an AWS Account"**.

---

### #Paso 2: Completa el formulario de registro

1. Ingresa tu **correo electrónico**, **nombre de cuenta**, y **contraseña**.
2. Elige si eres **cuenta personal** o **empresa**.
3. Proporciona un **número de teléfono y dirección real**.
4. Ingresa los **datos de tu tarjeta de crédito/débito**. _(No te cobrarán si usas el nivel gratuito)_.
5. Verifica tu identidad con un código enviado a tu teléfono.
6. Elige un plan: elige **Free Tier (nivel gratuito)**.

---

#### Paso 3: Accede al **AWS Management Console**

Una vez registrado, puedes acceder desde:

🔗 [https://console.aws.amazon.com/](https://console.aws.amazon.com/)

Usa tu usuario y contraseña para acceder.

---

### 🧪 Ejemplo completo: Lanzar un servidor en la nube con AWS

#### 🎯 Objetivo:

Crear un servidor virtual (EC2) en AWS, con acceso remoto, y probarlo desde tu PC.

---

#### 1. Acceder al servicio EC2

1. Entra a la consola: [https://console.aws.amazon.com](https://console.aws.amazon.com)
2. En el buscador escribe “EC2” y haz clic.
3. Clic en “Launch instance”.

---

#### 2. Configurar la instancia

| Paso               | Opción sugerida                                   |
| ------------------ | ------------------------------------------------- |
| Nombre             | MiServidorLinux                                   |
| Imagen             | Amazon Linux 2023 o Ubuntu 22.04 (Free Tier)      |
| Tipo de instancia  | t2.micro (1 vCPU, 1GB RAM)                        |
| Par de claves      | Crear nueva: “mi_clave.pem”                       |
| Firewall (puertos) | Abrir SSH (puerto 22), HTTP (puerto 80) si deseas |

---

#### 3. Descargar clave privada `.pem`

Guarda tu archivo `mi_clave.pem` en un lugar seguro. Luego cambia los permisos:

```bash
chmod 400 mi_clave.pem
```

---

#### 4. Conectarte a tu servidor por SSH

Desde tu terminal (Linux/Mac/WSL):

```bash
ssh -i mi_clave.pem ec2-user@<IP-PÚBLICA>
```

(Si elegiste Ubuntu, el usuario puede ser `ubuntu`)

---

#### 5. Probar el servidor

En la terminal del servidor puedes hacer:

```bash
sudo yum update  # (si es Amazon Linux)
sudo apt update  # (si es Ubuntu)
```

Crear un archivo:

```bash
echo "Hola desde AWS" > hola.txt
cat hola.txt
```

---

### 📦 Resultado

¡Ya tienes un servidor funcionando en la nube! Puedes instalar NGINX, desplegar una app, correr un backend o conectarte a una base de datos.

---

### 🧠 Buenas prácticas básicas

- 🔐 Nunca compartas tu archivo `.pem`.
- 🔒 Usa **Security Groups** para limitar acceso solo desde tu IP.
- 💰 Monitorea el uso para no exceder el **Free Tier**.
- 📤 Detén o termina instancias si no las estás usando.

---

### 🚀 ¿Qué sigue?

Con tu cuenta de AWS puedes ahora:

- Crear una bucket S3 para alojar archivos
- Lanzar una base de datos RDS para tu app
- Crear funciones Lambda sin servidores
- Automatizar todo con CloudFormation o Terraform

---

[🔼](#índice)

---

## **360. Registro y configuración de una cuenta en AWS**

### 🧠 ¿Qué es AWS?

**Amazon Web Services (AWS)** es una plataforma de servicios en la nube que te permite:

- Crear servidores virtuales (EC2)
- Guardar archivos (S3)
- Usar bases de datos (RDS)
- Analizar datos, crear sitios web, apps móviles, etc.

Y lo mejor: puedes comenzar gratis con el plan **Free Tier**.

---

### ✅ ¿Qué necesitas para registrarte en AWS?

1. Correo electrónico válido (mejor si es uno profesional o que uses para proyectos serios)
2. Número de teléfono celular
3. Tarjeta de crédito o débito (se requiere para verificar, pero no te cobran si usas el nivel gratuito)
4. Conexión a Internet estable

---

### 📝 Paso a Paso: Registro de una cuenta en AWS

#### 🔹 Paso 1: Ingresar al sitio oficial

Abre tu navegador y ve a:

👉 [https://aws.amazon.com](https://aws.amazon.com)

Haz clic en el botón **"Crear una cuenta de AWS"**.

---

#### 🔹 Paso 2: Crear una cuenta

Completa el formulario:

| Campo                | Ejemplo                                             |
| -------------------- | --------------------------------------------------- |
| Correo electrónico   | [guss.dev@example.com](mailto:guss.dev@example.com) |
| Nombre de cuenta     | GussDev Cloud                                       |
| Contraseña           | \[Tu contraseña segura]                             |
| Confirmar contraseña | \[La misma]                                         |

Haz clic en **Continuar (Next)**.

---

#### 🔹 Paso 3: Datos de contacto

Selecciona si es:

- Personal (para ti)
- Empresa (si es una organización)

Completa con tu nombre, dirección, país y número de teléfono. Asegúrate que sea **correcto**, porque recibirás un código de verificación.

---

#### 🔹 Paso 4: Método de pago

Aquí debes ingresar los datos de **una tarjeta de crédito o débito** válida.

💡 **TIP:** AWS hará un cobro de **\$1 o menos**, solo para verificar. Se devuelve después.

---

#### 🔹 Paso 5: Verificación por teléfono

AWS te llamará o te enviará un SMS con un **código de 4 dígitos**.

📞 Ingresa el código para verificar que el número es tuyo.

---

#### 🔹 Paso 6: Elige un plan

Verás tres opciones:

- Free Tier (Gratis)
- Developer (pago)
- Business (pago)

🔹 **Elige "Free Tier"**.

---

#### 🔹 Paso 7: ¡Listo!

Tu cuenta está activa. Puedes entrar a la consola en:

👉 [https://console.aws.amazon.com](https://console.aws.amazon.com)

Usa tu correo y contraseña para iniciar sesión.

---

### 🛠️ ¿Qué es la Consola de Administración de AWS?

Es el panel de control donde puedes ver y administrar **todos los servicios** de AWS.

Desde aquí puedes:

- Crear servidores
- Subir archivos
- Gestionar bases de datos
- Configurar seguridad
- Usar servicios de inteligencia artificial, etc.

---

### 🔐 Recomendaciones de configuración inicial

Después de registrarte, sigue estos pasos importantes:

#### 🔸 1. Activar la verificación en dos pasos (MFA)

1. En la esquina superior derecha haz clic en tu nombre > **"Security credentials"**.
2. Ve a la sección "Multi-Factor Authentication (MFA)".
3. Configura con una app como **Google Authenticator**.

🔒 Esto protege tu cuenta si alguien roba tu contraseña.

---

#### 🔸 2. Crear un usuario administrador (no usar root)

1. En la consola, busca **IAM** (Identity and Access Management).
2. Crea un nuevo usuario:

   - Tipo: **IAM user**
   - Permisos: **Administrador**

3. Usa este nuevo usuario para trabajar en AWS. Evita usar la cuenta **root** (principal) todo el tiempo.

---

#### 🔸 3. Crear una clave SSH (si usarás EC2)

Desde tu terminal (Linux/Mac):

```bash
ssh-keygen -t rsa -b 4096 -f gussdev-key
```

Esto crea dos archivos:

- `gussdev-key` → clave privada (¡guárdala bien!)
- `gussdev-key.pub` → clave pública (la subirás a AWS para conectarte a servidores)

---

### 🚀 Ejemplo completo: Crear y conectarte a tu primer servidor (EC2)

#### 🎯 Objetivo:

Crear un servidor en la nube (Amazon Linux) y conectarte por SSH.

---

#### 1. Desde la consola, busca **EC2**

Haz clic en **"Launch Instance"** (Iniciar instancia).

---

#### 2. Configura la instancia

| Opción            | Valor recomendado                      |
| ----------------- | -------------------------------------- |
| Nombre            | MiPrimerServidor                       |
| AMI (sistema)     | Amazon Linux 2023 (Free tier)          |
| Tipo de instancia | t2.micro (gratis)                      |
| Par de claves     | Sube tu clave pública o crea una nueva |
| Config. red       | Habilita puerto 22 (SSH)               |

Haz clic en **Launch Instance**.

---

#### 3. Conectarte por SSH desde tu terminal

```bash
ssh -i gussdev-key ec2-user@<IP-PÚBLICA>
```

Cambiar permisos si es necesario:

```bash
chmod 400 gussdev-key
```

---

#### 4. Probar que funciona

Una vez dentro:

```bash
echo "¡Hola desde AWS!" > hola.txt
cat hola.txt
```

¡Tu servidor en la nube está funcionando!

---

### 📌 Resumen rápido

| Paso | Acción                                                     |
| ---- | ---------------------------------------------------------- |
| 1    | Crea tu cuenta en [aws.amazon.com](https://aws.amazon.com) |
| 2    | Verifica tu número y tarjeta                               |
| 3    | Elige el plan gratuito (Free Tier)                         |
| 4    | Activa MFA y crea usuarios IAM seguros                     |
| 5    | Lanza una instancia EC2                                    |
| 6    | Conéctate con SSH usando tu clave privada                  |

---

[🔼](#índice)

---

## **361. Infraestructura de red en la nube (AWS)**

### 🌐 ¿Qué es la Infraestructura de Red en la Nube (AWS)?

En AWS, la **infraestructura de red** es el conjunto de **recursos virtuales de red** que permiten que tus servidores, bases de datos, aplicaciones web, etc., se conecten de forma segura y controlada.

---

#### 🔧 Componentes principales de una red en AWS

| Componente                      | ¿Qué hace?                                                                  | Ejemplo                                         |
| ------------------------------- | --------------------------------------------------------------------------- | ----------------------------------------------- |
| **VPC (Virtual Private Cloud)** | Red privada virtual donde trabajas                                          | Como una "casa" para tus servidores             |
| **Subnets**                     | Divisiones de tu red (pueden ser públicas o privadas)                       | Un cuarto público o privado                     |
| **Route Tables**                | Tabla de rutas para saber a dónde va el tráfico                             | Como decir "si vas a Internet, usa esta puerta" |
| **Internet Gateway**            | Permite conexión a Internet desde la VPC                                    | La puerta principal de salida                   |
| **NAT Gateway**                 | Permite a subredes privadas salir a Internet sin ser accesibles desde fuera | Una salida con espejo unidireccional            |
| **Security Groups**             | Firewalls virtuales que controlan puertos                                   | "Abre solo el puerto 22 (SSH)"                  |
| **Network ACLs**                | Otro tipo de firewall pero por subred                                       | Seguridad a nivel de subnet                     |

---

### 🎓 Metáfora para entenderlo fácilmente

Imagina que construyes una casa:

- 🏠 La casa completa = VPC
- 🛏️ Cuartos privados/públicos = Subnets
- 🚪 Puerta principal (a la calle) = Internet Gateway
- 🔑 Llaves que solo abren ciertas puertas = Security Groups
- 📦 Paquetes con direcciones = Route Tables

---

### ✅ ¿Por qué crear tu propia red en AWS?

- Aislar servicios por seguridad (por ejemplo, un servidor backend en una subred privada)
- Conectar solo lo necesario a Internet (mayor control)
- Escalar de forma profesional (como lo hacen las grandes empresas)
- Prepararte para arquitecturas en producción

---

### 🛠️ Cómo instalar y configurar una infraestructura de red en AWS

---

#### 📦 PASO 1: Crear una VPC personalizada

1. Entra a la consola de AWS:
   👉 [https://console.aws.amazon.com](https://console.aws.amazon.com)

2. Busca "VPC" en la barra superior.

3. Ve a **Your VPCs** > clic en **Create VPC**.

4. Completa:

| Campo           | Valor recomendado |
| --------------- | ----------------- |
| Name tag        | `guss-vpc`        |
| IPv4 CIDR block | `10.0.0.0/16`     |
| Tenancy         | default           |

Haz clic en **Create VPC**.

---

#### 📦 PASO 2: Crear subredes

##### 🔹 Subred pública

1. Ve a **Subnets** > Create subnet.
2. Elige la VPC `guss-vpc`.
3. Asigna:

| Campo             | Valor                    |
| ----------------- | ------------------------ |
| Name tag          | `guss-public-subnet`     |
| Availability Zone | us-east-1a (por ejemplo) |
| IPv4 CIDR         | `10.0.1.0/24`            |

Haz clic en **Create subnet**.

##### 🔹 Subred privada (para base de datos o backend)

Mismo proceso, pero usa:

- Name: `guss-private-subnet`
- CIDR: `10.0.2.0/24`

---

#### 📦 PASO 3: Crear una Internet Gateway (IGW)

1. Ve a **Internet Gateways** > Create.
2. Name tag: `guss-igw`
3. Crea y luego haz clic en "Attach to VPC" → elige `guss-vpc`.

---

#### 📦 PASO 4: Asociar tabla de rutas a la subred pública

1. Ve a **Route Tables**.

2. Crea una nueva:

   - Name tag: `guss-public-rt`
   - VPC: `guss-vpc`

3. Luego edita las rutas:

- Destino: `0.0.0.0/0`
- Target: Internet Gateway (`guss-igw`)

4. Asocia esta tabla a la subred pública (`guss-public-subnet`).

---

#### 📦 PASO 5: Crear un Security Group

1. Ve a **Security Groups** > Create.

| Campo       | Valor                 |
| ----------- | --------------------- |
| Name        | `guss-sg`             |
| Description | `Permitir SSH y HTTP` |
| VPC         | `guss-vpc`            |

2. En reglas de entrada (Inbound):

- Tipo: SSH, puerto 22, origen: `0.0.0.0/0`
- Tipo: HTTP, puerto 80, origen: `0.0.0.0/0`

3. Guarda el grupo.

---

### ✅ Ejemplo completo: crear una infraestructura para un servidor web

#### Objetivo

✅ Lanzar una instancia EC2 en la subred pública

✅ Conectarte vía SSH

✅ Acceder a un sitio web en Apache

---

#### PASO 1: Lanzar una instancia EC2

1. EC2 > Launch Instance
2. Nombre: `ServidorWeb`
3. AMI: Amazon Linux 2023
4. Tipo: `t2.micro`
5. Key pair: selecciona o crea una
6. Red: `guss-vpc`
   Subred: `guss-public-subnet`
   Auto-assign public IP: Enabled
7. Security Group: `guss-sg`
8. Lanzar

---

#### PASO 2: Instalar Apache

Conéctate por SSH:

```bash
ssh -i guss-key.pem ec2-user@<IP_PUBLICA>
```

Instala Apache:

```bash
sudo yum update -y
sudo yum install -y httpd
sudo systemctl start httpd
sudo systemctl enable httpd
```

Crea una página de prueba:

```bash
echo "<h1>¡Hola desde AWS!</h1>" | sudo tee /var/www/html/index.html
```

---

#### PASO 3: Visita el sitio en el navegador

Abre tu navegador y visita:

```
http://<IP_PUBLICA>
```

👀 Verás el mensaje: **¡Hola desde AWS!**

---

### ✅ Resumen Visual (Arquitectura Final)

```
       Internet
          │
          ▼
    ┌──────────────┐
    │ Internet GW  │
    └─────┬────────┘
          │
    ┌─────▼────────────────────────────────┐
    │           guss-vpc (10.0.0.0/16)     │
    │                                      │
    │ ┌────────────┐     ┌──────────────┐  │
    │ │ Public Sub │     │ Private Sub  │  │
    │ │ 10.0.1.0/24│     │ 10.0.2.0/24  │  │
    │ │ ┌────────┐ │     │ DB/Backend   │  │
    │ │ │ EC2 🖥️ │ │     └──────────────┘  │
    │ └────────────┘                       │
    └────────────────────────────────────┘
```

---

### 🎁 ¿Qué sigue?

Ahora que ya sabes cómo crear tu red, puedes:

- Agregar una base de datos en la subred privada (RDS)
- Usar balanceadores de carga
- Desplegar contenedores en ECS o EKS
- Montar un backend en Node, Flask o Django

---

[🔼](#índice)

---

## **362. Seguridad y computación en la nube (AWS)**

### ☁️ ¿Qué es la seguridad en la computación en la nube?

La **seguridad en la nube** se refiere a todos los mecanismos, servicios y buenas prácticas que se aplican para **proteger tus datos, servicios y recursos alojados en AWS**.

---

#### 🧱 ¿Qué debes proteger en la nube?

| Elemento              | ¿Por qué se protege?                         |
| --------------------- | -------------------------------------------- |
| ✅ Datos              | Evitar accesos no autorizados (ej. clientes) |
| ✅ Máquinas virtuales | Proteger tus servidores (EC2)                |
| ✅ Red virtual        | Bloquear accesos no deseados (firewalls)     |
| ✅ Cuentas y usuarios | Controlar quién accede y qué hace            |
| ✅ Archivos en S3     | Evitar filtraciones de información           |

---

### 🔐 Principios clave de seguridad en AWS

1. **Mínimos privilegios**: solo lo necesario para cada usuario o recurso.
2. **Autenticación y autorización**: cada acción debe estar validada.
3. **Encriptación**: cifrar datos en tránsito y en reposo.
4. **Monitoreo constante**: alertas y registros de actividad.
5. **Segmentación de red**: dividir recursos para aislar riesgos.

---

### 🔧 Herramientas de seguridad que ofrece AWS

| Servicio                                 | ¿Qué hace?                                   | Ejemplo fácil                                  |
| ---------------------------------------- | -------------------------------------------- | ---------------------------------------------- |
| **IAM** (Identity and Access Management) | Gestiona usuarios, permisos y roles          | Crear un usuario que solo puede leer un bucket |
| **Security Groups**                      | Firewall por instancia                       | Solo permitir tráfico por puerto 22 (SSH)      |
| **Network ACLs**                         | Firewall a nivel de subred                   | Bloquear tráfico desde ciertos IPs             |
| **CloudTrail**                           | Guarda logs de todo lo que pasa en tu cuenta | Saber quién borró una base de datos            |
| **KMS** (Key Management Service)         | Maneja claves para cifrado                   | Cifrar archivos de S3 automáticamente          |
| **S3 Bucket Policies**                   | Controla acceso a buckets de forma precisa   | Permitir solo a cierto usuario descargar       |
| **GuardDuty**                            | Detecta amenazas automáticamente             | Alertas por comportamiento sospechoso          |

---

### 🛠️ ¿Cómo se instala o configura?

En la nube, **"instalar" significa activar o usar servicios desde la consola de AWS o mediante código**. Te muestro los más importantes y cómo configurarlos:

---

#### 🔑 1. Crear una política de acceso (IAM)

**Objetivo**: permitir acceso solo de lectura a un bucket S3.

1. Ve a la consola de AWS → **IAM** → Policies → **Create policy**.
2. Elige JSON y pega esto:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": ["s3:GetObject"],
      "Resource": ["arn:aws:s3:::mi-bucket-ejemplo/*"]
    }
  ]
}
```

3. Guárdalo como `SoloLecturaS3`.

---

#### 👤 2. Crear un usuario seguro con MFA (doble factor)

1. En IAM → **Users** → Add user.
2. Nombre: `lector-s3`
3. Tipo de acceso: **Programmatic access**
4. Adjunta la política `SoloLecturaS3`
5. En la configuración avanzada, activa **MFA** y sigue las instrucciones para usar Google Authenticator o Authy.

---

#### 🔐 3. Proteger una instancia EC2 con Security Groups

1. Al crear una EC2, elige:

   - Solo permitir tráfico por el puerto 22 (SSH)
   - Elimina reglas que permitan acceso general (0.0.0.0/0) si no es necesario

---

#### 🔍 4. Habilitar AWS CloudTrail

1. Ve a **CloudTrail** → Create trail
2. Nombre: `miTrail`
3. Apunta los logs a un bucket S3
4. ¡Listo! Ahora se registrará toda la actividad de la cuenta.

---

#### 🔒 5. Encriptar un bucket de S3

1. Ve a S3 → Elige tu bucket → Properties.
2. Busca “Default encryption”.
3. Activa la opción y elige **AWS-KMS** o **SSE-S3**.

---

### ✅ Ejemplo completo: sitio web seguro en EC2 + bucket S3 con políticas

#### Objetivo:

Crear un sitio web en EC2 que:

- Está protegido por un Security Group.
- Sube y descarga archivos de un bucket S3.
- Solo ciertos usuarios pueden acceder al bucket.

---

#### PASO 1: Crear instancia EC2 segura

- Tipo: Amazon Linux 2023
- Security Group: Solo puerto 22 (SSH) y 80 (HTTP)
- Script de instalación (User Data):

```bash
#!/bin/bash
sudo yum update -y
sudo yum install -y httpd
echo "<h1>Sitio web seguro con AWS</h1>" > /var/www/html/index.html
sudo systemctl start httpd
sudo systemctl enable httpd
```

---

#### PASO 2: Crear bucket S3 con política

1. Nombre: `sitio-web-guss`
2. En “Permissions” → Bucket Policy:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "LecturaUsuario",
      "Effect": "Allow",
      "Principal": {
        "AWS": "arn:aws:iam::tu-ID-de-cuenta:user/lector-s3"
      },
      "Action": ["s3:GetObject"],
      "Resource": ["arn:aws:s3:::sitio-web-guss/*"]
    }
  ]
}
```

---

#### PASO 3: Proteger acceso con CloudTrail y MFA

- Activa CloudTrail como se explicó arriba.
- Activa MFA para el usuario `lector-s3`.

---

#### PASO 4: Prueba final

- El usuario `lector-s3` puede acceder al bucket solo si se autentica correctamente.
- Tu instancia EC2 es accesible por navegador web en el puerto 80.
- Todo acceso queda registrado en CloudTrail.

---

### ✅ Conclusión

La seguridad en la nube con AWS **no es opcional**. Te ayuda a:

- Cumplir normas (ISO, GDPR, etc.)
- Prevenir ataques
- Tener control total de tus recursos
- Automatizar auditorías

---

[🔼](#índice)

---

## **363. Balanceadores y almacenamiento en la nube (AWS)**

### 🧭 1. ¿Qué es un Balanceador de Carga (Load Balancer)?

Un **balanceador de carga** distribuye automáticamente el tráfico entrante (por ejemplo, de usuarios que entran a tu sitio web) entre varios servidores (EC2), para:

- **Evitar que un solo servidor se sobrecargue**
- **Mejorar la alta disponibilidad** (si un servidor cae, el otro sigue funcionando)
- **Hacer el sistema más escalable y seguro**

🔁 Ejemplo simple:

Si tienes 3 servidores que muestran tu sitio, el balanceador reparte el tráfico entre ellos:

```text
Usuario 1 ─┬─> EC2-1
Usuario 2 ─┤
Usuario 3 ─┼─> EC2-2
Usuario 4 ─┤
Usuario 5 ─┴─> EC2-3
```

---

#### 📦 Tipos de Load Balancer en AWS (ELB)

| Tipo                                | Uso principal                         |
| ----------------------------------- | ------------------------------------- |
| **Application Load Balancer (ALB)** | Para sitios web, apps HTTP/S (capa 7) |
| **Network Load Balancer (NLB)**     | Para tráfico TCP/UDP masivo (capa 4)  |
| **Gateway Load Balancer (GWLB)**    | Para appliances de seguridad virtual  |

✅ Para la mayoría de aplicaciones web, usamos **ALB**.

---

### 🗄️ 2. ¿Qué es el Almacenamiento en la nube (AWS)?

AWS tiene varios tipos de almacenamiento. Los principales son:

| Servicio    | ¿Qué guarda?                      | Ejemplo fácil                          |
| ----------- | --------------------------------- | -------------------------------------- |
| **S3**      | Archivos, imágenes, backups, etc. | Subes un PDF o una imagen              |
| **EBS**     | Disco para máquinas EC2           | Como el disco C: de tu laptop          |
| **EFS**     | Sistema de archivos compartido    | Varios servidores pueden leer/escribir |
| **Glacier** | Archivos viejos (archivado)       | Backups antiguos que rara vez usas     |

✅ El más usado es **Amazon S3** por su simplicidad y escalabilidad.

---

### 🛠️ 3. ¿Cómo se configuran? (Instalación)

En AWS, “instalar” significa **habilitar y conectar servicios desde la consola o CLI**. Veamos paso a paso:

---

#### 🔧 Paso 1: Crear una VPC con 2 subredes públicas

1. VPC > Launch VPC Wizard
2. Nombre: `mi-vpc`
3. Crea 2 subredes públicas: `subred-1`, `subred-2`
4. Asegúrate de tener una **gateway de internet**

---

#### 🔧 Paso 2: Lanzar 2 instancias EC2 en diferentes subredes

- Tipo: Amazon Linux 2 o Ubuntu
- Agrega el siguiente script en **User Data** para instalar servidor web:

```bash
#!/bin/bash
sudo yum update -y
sudo yum install -y httpd
echo "<h1>Servidor $(hostname)</h1>" > /var/www/html/index.html
sudo systemctl start httpd
sudo systemctl enable httpd
```

Esto mostrará el nombre del servidor en el navegador para saber cuál responde.

---

#### 🔧 Paso 3: Crear un Application Load Balancer

1. Ve a **EC2 → Load Balancers → Create Load Balancer**
2. Elige **Application Load Balancer**
3. Nombre: `mi-alb`
4. Escoge las 2 subredes públicas creadas antes
5. Crea un nuevo **Security Group** que permita tráfico por el puerto 80
6. Crea un **Target Group** con tipo `instance`, nombre: `grupo-web`
7. Añade las 2 EC2 al target group
8. Termina la configuración

✅ Resultado: tu ALB repartirá tráfico entre los dos servidores EC2.

---

#### 🔧 Paso 4: Crear bucket S3 para almacenamiento

1. Ve a **S3 → Create bucket**
2. Nombre: `mi-almacenamiento-guss`
3. Desactiva acceso público si no lo necesitas (por seguridad)
4. Ve a “Permissions” y crea una política si lo quieres público temporalmente:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::mi-almacenamiento-guss/*"
    }
  ]
}
```

---

#### 🧪 Paso 5: Prueba el sistema

1. Sube una imagen o archivo PDF al bucket S3.
2. Abre el link generado y verifica que funciona.
3. Copia la **DNS del Load Balancer**, pégala en el navegador:

   - Verás que cada vez que actualizas, responde un servidor diferente (`Servidor ip-...`)

---

### ✅ EJEMPLO COMPLETO (Resumen Visual)

```text
        Internet
           |
    ┌──── Load Balancer (ALB) ─────┐
    |                              |
┌──▼───┐                     ┌─────▼───┐
| EC2-1|                     | EC2-2   |
| Web  |                     | Web     |
└──────┘                     └─────────┘
        ↘                     ↙
           Bucket S3: mi-almacenamiento-guss
                 (imagenes, backups, etc)
```

---

### 🧠 ¿Por qué usar Balanceador + S3?

| Ventaja balanceador            | Ventaja S3                               |
| ------------------------------ | ---------------------------------------- |
| Alta disponibilidad            | Almacenamiento barato y escalable        |
| Escalabilidad automática       | Puedes servir archivos públicos/privados |
| Tolerancia a fallos (failover) | Integración con Lambda, CloudFront, etc. |
| SSL fácilmente habilitable     | Seguridad granular con IAM y políticas   |

---

[🔼](#índice)

---

## **364. Recopilación de información en un entorno real**

### 🧠 ¿Qué es la recopilación de información?

La **recopilación de información (o "Information Gathering")** es la **primera fase del hacking ético** o pentesting. Consiste en **recolectar la mayor cantidad de datos posibles sobre el objetivo**, sin alertarlo (fase pasiva) o interactuando directamente (fase activa).

---

### 🎯 ¿Para qué sirve?

- Entender la infraestructura de red y servidores del objetivo
- Identificar posibles puntos débiles o vulnerabilidades
- Planificar futuras fases como escaneo o explotación

---

### 🧱 Tipos de recopilación de información

| Tipo       | Descripción                                | Ejemplo fácil                  |
| ---------- | ------------------------------------------ | ------------------------------ |
| **Pasiva** | No interactúas directamente con el sistema | Googlear el nombre del dominio |
| **Activa** | Interactúas con el sistema objetivo        | Escanear con Nmap o ping       |

---

### 🛠️ Herramientas utilizadas (Instalables)

A continuación, una tabla con herramientas populares y cómo instalarlas:

| Herramienta    | Función principal             | Instalación en Kali/Linux         |
| -------------- | ----------------------------- | --------------------------------- |
| `whois`        | Info sobre dominio            | `sudo apt install whois`          |
| `dig`          | Info DNS del dominio          | `sudo apt install dnsutils`       |
| `nslookup`     | Resolver dominios             | Viene preinstalado                |
| `theHarvester` | Emails, subdominios, IPs      | `sudo apt install theharvester`   |
| `recon-ng`     | Framework OSINT               | `sudo apt install recon-ng`       |
| `Nmap`         | Escaneo de puertos            | `sudo apt install nmap`           |
| `WhatWeb`      | Identificar tecnologías web   | `sudo apt install whatweb`        |
| `Shodan CLI`   | Busqueda en base de datos IoT | `pip install -U shodan` + API Key |

---

### 📥 Ejemplo completo paso a paso

Vamos a suponer que tienes que auditar el dominio: `midominioempresa.com`

#### 🪪 1. Whois – Información del dominio

```bash
whois midominioempresa.com
```

💡 Qué obtienes:

- Nombre del registrante
- Empresa
- Emails administrativos
- Fechas de creación y expiración

---

#### 🌐 2. DNS y subdominios – dig / nslookup / theHarvester

```bash
dig midominioempresa.com
```

```bash
nslookup midominioempresa.com
```

```bash
theHarvester -d midominioempresa.com -b google
```

💡 Qué obtienes:

- Dirección IP pública del dominio
- Servidores de nombres (DNS)
- Subdominios como `mail.midominioempresa.com`, `vpn.`, etc.
- Correos electrónicos expuestos

---

#### 🔎 3. Tecnologías Web – WhatWeb

```bash
whatweb http://midominioempresa.com
```

💡 Qué obtienes:

- Framework usado (WordPress, Laravel, etc)
- Lenguaje backend (PHP, ASP.NET)
- Servidor web (Apache, Nginx)

---

#### 🌍 4. Información pública – Google Dorks + LinkedIn

```bash
site:midominioempresa.com filetype:pdf
```

Busca PDF internos de la empresa, info técnica, versiones.

En LinkedIn:

- Buscas empleados
- Nombres de dominio de correo (`juan.perez@midominioempresa.com`)
- Estructura organizacional

---

#### 🛰️ 5. Shodan – Infraestructura expuesta en Internet

Instala el CLI y usa tu API:

```bash
pip install shodan
shodan init TU_API_KEY
shodan search midominioempresa.com
```

💡 Qué puedes encontrar:

- Dispositivos abiertos al mundo (cámaras, firewalls)
- Puertos abiertos
- Tecnologías antiguas o sin parches

---

### 🎯 Resultado Final: Resumen práctico

```yaml
Dominio: midominioempresa.com

IP pública: 142.250.183.238
Servidor web: Apache/2.4.7 (Ubuntu)
Framework: WordPress 5.4.2
Subdominios:
  - mail.midominioempresa.com
  - vpn.midominioempresa.com
  - intranet.midominioempresa.com

Correos encontrados:
  - soporte@midominioempresa.com
  - admin@midominioempresa.com

Empleados (de LinkedIn):
  - Juan Pérez, CTO
  - María Rojas, Infraestructura

Shodan:
  - IP 142.250.183.238 expone puerto 22 (SSH)
  - Certificado SSL autofirmado caducado
```

---

#### ✅ Conclusiones

Has realizado una **recopilación de información completa** sin interactuar agresivamente con el objetivo. Esto te permite:

- Descubrir **superficies de ataque**
- Evaluar vulnerabilidades sin alertar
- Prepararte para fases como **escaneo de puertos y explotación**

---

[🔼](#índice)

---

## **365. Controles de seguridad en un entorno real**

### 🛡️ ¿Qué son los controles de seguridad?

Son **medidas que se implementan para proteger sistemas, redes, datos y usuarios** frente a amenazas y ataques. Pueden ser físicos, técnicos o administrativos.

#### 📚 Tipos de controles de seguridad

| Tipo                 | Qué hacen                                     | Ejemplo fácil                             |
| -------------------- | --------------------------------------------- | ----------------------------------------- |
| **Preventivos**      | Evitan que ocurra un incidente                | Contraseña fuerte, antivirus              |
| **Detectivos**       | Detectan actividades sospechosas o ataques    | IDS, monitoreo de logs                    |
| **Correctivos**      | Ayudan a recuperarse tras un ataque           | Backups, restauración de sistemas         |
| **Disuasivos**       | Desalientan a los atacantes                   | Mensajes legales, cámaras de seguridad    |
| **Físicos**          | Protegen el acceso físico                     | Puertas con llave, tarjetas RFID          |
| **Lógicos/Técnicos** | Protegen sistemas y redes mediante tecnología | Firewall, autenticación multifactor (MFA) |

---

### 🧠 ¿Por qué son importantes?

Porque una organización sin controles:

- Puede sufrir robos de información
- Es vulnerable a ransomware
- Pierde reputación y puede tener sanciones legales

---

### 🧰 Instalación y ejemplos por categoría

Te muestro ejemplos **reales y aplicables** que puedes instalar tú mismo:

---

#### 🔐 1. Control preventivo: Autenticación multifactor (MFA)

**Instalación en Linux con Google PAM Module:**

```bash
sudo apt install libpam-google-authenticator
google-authenticator
```

👉 Esto activa el uso de una app móvil tipo Google Authenticator para iniciar sesión en el sistema.

---

#### 🔥 2. Control técnico: Firewall con UFW (Ubuntu)

```bash
sudo apt install ufw
sudo ufw enable
sudo ufw allow 22     # Permite SSH
sudo ufw deny 23      # Bloquea Telnet
```

👉 Protege el servidor filtrando qué puertos están accesibles.

---

#### 🕵️ 3. Control detectivo: Monitoreo con `auditd`

```bash
sudo apt install auditd
sudo auditctl -w /etc/passwd -p wa -k passwd_changes
```

👉 Esto registra cualquier escritura o acceso al archivo de contraseñas.

---

#### 💾 4. Control correctivo: Copias de seguridad automáticas

```bash
crontab -e
```

Y agregas esta línea:

```bash
0 1 * * * tar -czf /backup/$(date +\%F).tar.gz /home/usuario
```

👉 Se genera un respaldo diario a la 1:00 AM.

---

#### 🧑‍🏫 5. Control administrativo: Políticas de seguridad

Redacta un archivo `politicas_seguridad.txt` con puntos como:

```text
- Cambiar la contraseña cada 90 días
- No compartir credenciales
- Reportar incidentes en menos de 24 horas
```

👉 Aunque no es técnico, es clave para que los usuarios sepan cómo comportarse.

---

### ✅ Ejemplo completo: "Segurizando una pequeña empresa"

Imagina que estás protegiendo un servidor web de una startup.

#### 🔧 Configuras lo siguiente:

1. **Preventivo:**

   - Contraseñas fuertes obligatorias (`/etc/login.defs`)
   - MFA para el acceso SSH con Google Authenticator

2. **Detectivo:**

   - `auditd` monitoreando cambios en `/etc/passwd` y `/var/www`
   - `fail2ban` detectando intentos de fuerza bruta en SSH

3. **Correctivo:**

   - Script diario de backup automático con `cron` y `tar`
   - Snapshot semanal de la instancia si usas AWS o Azure

4. **Disuasivo:**

   - Mensaje legal en el banner de SSH:

```bash
echo "ACCESO NO AUTORIZADO PROHIBIDO. TODO ESTÁ MONITOREADO." | sudo tee /etc/issue.net
sudo sed -i 's/#Banner none/Banner \/etc\/issue.net/' /etc/ssh/sshd_config
sudo systemctl restart sshd
```

5. **Técnico:**

   - `ufw` para restringir puertos (solo 22 y 80 abiertos)
   - `clamav` como antivirus básico

---

### 📋 Resultado esperado

Con todos estos controles implementados:

- Un atacante no podrá acceder fácilmente
- Si lo intenta, será detectado
- Si logra algo, podrás restaurar con backups
- Legalmente estás cubierto (banner + políticas)
- Técnicamente el sistema está mucho más seguro

---

[🔼](#índice)

---

## **366. Auditando la infraestructura interna**

### 🧠 ¿Qué significa auditar la infraestructura interna?

**Auditar la infraestructura interna** es evaluar los sistemas, redes, dispositivos y políticas internas de una organización para detectar vulnerabilidades, configuraciones incorrectas y riesgos de seguridad.

> 👉 Es como hacer una revisión médica completa, pero a los servidores, computadoras, routers, etc.

---

### 🎯 ¿Qué incluye una auditoría interna?

1. **Descubrimiento de red (qué hay conectado)**
2. **Enumeración de servicios (qué corre en cada equipo)**
3. **Detección de vulnerabilidades**
4. **Revisión de configuraciones (firewall, puertos, usuarios)**
5. **Pruebas de acceso (con o sin credenciales)**
6. **Análisis de registros (logs del sistema)**

---

### 🧰 Herramientas que usaremos

| Herramienta   | ¿Para qué sirve?                      |
| ------------- | ------------------------------------- |
| `nmap`        | Escaneo de red y puertos              |
| `netdiscover` | Descubrir dispositivos en la red      |
| `OpenVAS`     | Análisis de vulnerabilidades          |
| `Lynis`       | Auditoría de seguridad local en Linux |
| `Nikto`       | Evaluación de servidores web          |
| `logwatch`    | Analiza logs del sistema              |

---

### 🔧 Paso a paso: Cómo instalar las herramientas (Ubuntu/Debian)

#### 1. Instalar Nmap y Netdiscover

```bash
sudo apt update
sudo apt install nmap netdiscover -y
```

#### 2. Instalar OpenVAS (ahora llamado `gvm`)

```bash
sudo apt install gvm -y
sudo gvm-setup
sudo gvm-check-setup
```

#### 3. Instalar Lynis

```bash
sudo apt install lynis -y
```

#### 4. Instalar Nikto

```bash
sudo apt install nikto -y
```

#### 5. Instalar Logwatch

```bash
sudo apt install logwatch -y
```

---

### 🧪 Ejemplo completo: Auditoría de una red interna pequeña

Imaginemos que estás auditando una oficina pequeña con:

- 1 servidor web
- 3 PCs de usuarios
- 1 router

---

#### 🕵️ Paso 1: Descubrir la red

```bash
sudo netdiscover -r 192.168.1.0/24
```

> 🔎 Esto te muestra todos los dispositivos conectados a esa red local, sus IPs y MAC.

---

#### 🔍 Paso 2: Escanear servicios con Nmap

```bash
nmap -sS -sV -O 192.168.1.10
```

> Escanea puertos, versiones de servicios y sistema operativo del host `192.168.1.10`.

---

#### 🛡️ Paso 3: Buscar vulnerabilidades con OpenVAS

1. Abre el panel web:

```bash
sudo gvm-start
```

2. Ingresa a `https://localhost:9392` con tu usuario
3. Realiza un "Full and fast scan" contra los IPs descubiertos

---

#### 🔍 Paso 4: Auditoría local con Lynis (en cada equipo Linux)

```bash
sudo lynis audit system
```

> Esto revisa configuraciones de seguridad, permisos, servicios activos, logs, etc.

---

#### 🌐 Paso 5: Revisar seguridad del servidor web con Nikto

```bash
nikto -h http://192.168.1.10
```

> Detecta directorios inseguros, archivos ocultos, headers débiles, etc.

---

#### 📜 Paso 6: Revisar logs con Logwatch

```bash
sudo logwatch --detail high --service all --range today --format text
```

> Muestra un resumen de actividad sospechosa del día: intentos de login, fallos, etc.

---

### 📊 ¿Qué obtienes con todo esto?

🔐 Un panorama claro de la **seguridad de la red interna**:

- Sabes **qué hay conectado**
- Sabes **qué puertos y servicios están activos**
- Puedes ver **vulnerabilidades conocidas**
- Detectas **configuraciones incorrectas**
- Monitoreas actividad sospechosa en los logs

---

### ✅ Recomendaciones tras la auditoría

- **Cerrar puertos innecesarios**
- **Actualizar software vulnerable**
- **Cambiar contraseñas débiles**
- **Aplicar reglas de firewall**
- **Hacer auditorías periódicas**

---

[🔼](#índice)

---

## **367. Tipos de auditorías de seguridad**

### 🛡️ ¿Qué es una Auditoría de Seguridad?

Una **auditoría de seguridad** es un proceso sistemático para **evaluar la seguridad** de sistemas, redes, software y procedimientos. Se busca identificar **vulnerabilidades, errores de configuración, amenazas** o incumplimientos de normas de seguridad.

---

### ✅ ¿Por qué se hace una auditoría de seguridad?

- Para **proteger información sensible**
- Para **cumplir normas o regulaciones** (ISO 27001, GDPR, PCI-DSS, etc.)
- Para **detectar vulnerabilidades** antes que un atacante
- Para **fortalecer la seguridad interna**

---

### 🧩 TIPOS DE AUDITORÍA DE SEGURIDAD

Existen diferentes tipos, según **lo que se evalúa** o **cómo se realiza**. Aquí te los explico con ejemplos sencillos.

---

#### 🔍 1. **Auditoría interna**

> La realiza personal de la propia organización.

**Ejemplo:**

El área de IT revisa los accesos de los empleados y configura alertas por intentos de acceso fallido.

**Objetivo:**

Verificar que se cumplen políticas internas de seguridad.

---

#### 🕵️ 2. **Auditoría externa**

> La hace una empresa externa o consultor independiente.

**Ejemplo:**

Contratas una empresa para que revise tu red, intente vulnerarla y te entregue un informe con recomendaciones.

**Objetivo:**

Obtener una visión objetiva e imparcial de tu seguridad.

---

#### 💻 3. **Auditoría de sistemas**

> Evalúa servidores, equipos, SO, configuración, permisos, etc.

**Ejemplo:**

Verificar que no hay servicios obsoletos corriendo en un servidor Linux y que los permisos de archivos son seguros.

---

#### 🌐 4. **Auditoría de red**

> Evalúa la infraestructura de red: routers, switches, firewall, puertos, tráfico, etc.

**Ejemplo:**

Escaneo con Nmap y análisis de firewall para detectar puertos abiertos o protocolos inseguros (como Telnet).

---

#### 🧪 5. **Auditoría de aplicaciones web**

> Se evalúan apps web en busca de XSS, SQLi, CSRF, etc.

**Ejemplo:**

Escanear un sitio web con **OWASP ZAP** o **Nikto** para detectar vulnerabilidades como inyecciones o scripts maliciosos.

---

#### 👤 6. **Auditoría de usuarios y accesos**

> Revisa cómo están configuradas las cuentas de usuario, grupos, permisos y políticas de contraseñas.

**Ejemplo:**

Revisar en Active Directory que ningún usuario tenga contraseña que nunca expire.

---

#### 🔒 7. **Auditoría de cumplimiento**

> Evalúa si una empresa cumple con normas o estándares como:

- ISO 27001
- PCI-DSS
- GDPR
- HIPAA

**Ejemplo:**

Verificar si se aplican controles de cifrado, registros de logs y respaldo de información en una clínica médica.

---

#### 💣 8. **Auditoría de vulnerabilidades (Pentest)**

> Simula un ataque real para detectar debilidades.

**Ejemplo:**

Utilizar Metasploit o Burp Suite para intentar tomar control de un servidor vulnerable.

---

### 🔧 ¿Cómo se hace una auditoría de seguridad? (Proceso general)

1. **Definir el alcance**: ¿qué se va a auditar?
2. **Recopilar información**: Infraestructura, usuarios, sistemas.
3. **Evaluar configuración**: Revisar SO, red, contraseñas, firewalls, etc.
4. **Detectar vulnerabilidades**: Escaneo, pruebas de penetración.
5. **Analizar resultados**: Clasificar por riesgo.
6. **Redactar informe**: Con hallazgos, impacto y recomendaciones.

---

### 🧪 EJEMPLO COMPLETO: Auditoría interna + de red + de sistema

#### 🖥 Escenario: Tienes una red de 4 PCs, un servidor Ubuntu y un router.

---

##### 🔹 PASO 1: Descubrir la red

```bash
sudo netdiscover -r 192.168.1.0/24
```

> Muestra qué equipos están conectados en la red.

---

##### 🔹 PASO 2: Escanear servicios con Nmap

```bash
sudo nmap -sS -sV -O 192.168.1.1-254
```

> Detecta qué puertos y servicios están abiertos en los dispositivos.

---

##### 🔹 PASO 3: Revisar configuración del servidor

```bash
sudo lynis audit system
```

> Auditoría de seguridad local del sistema Linux (permisos, configuraciones, servicios).

---

##### 🔹 PASO 4: Probar aplicación web interna

```bash
nikto -h http://192.168.1.10
```

> Detecta configuraciones inseguras o rutas expuestas en servidores web.

---

##### 🔹 PASO 5: Revisar logs

```bash
sudo logwatch --detail high --range today --service all
```

> Muestra alertas, accesos sospechosos, errores, etc.

---

### 📄 RESULTADO FINAL

Tienes un **informe técnico** con:

- Equipos conectados
- Puertos inseguros abiertos
- Servicios mal configurados
- Logs con actividad sospechosa
- Recomendaciones de mitigación

---

### ✅ Buenas prácticas tras la auditoría

- Cierra puertos innecesarios
- Actualiza software vulnerable
- Aplica políticas de contraseñas fuertes
- Configura firewalls correctamente
- Monitorea logs y alertas

---

[🔼](#índice)

---

## **368. Eliminando el entorno en la nube (AWS)**

### 🧠 ¿Qué significa “eliminar el entorno en la nube”?

Significa **borrar todos los recursos** creados en tu cuenta de AWS para un proyecto: servidores, bases de datos, redes, balanceadores, buckets de S3, etc. Se hace normalmente cuando:

- Finalizaste un proyecto o prueba
- Ya no necesitas los recursos
- Quieres evitar gastos
- Vas a crear un nuevo entorno desde cero

---

### ✅ ¿Qué se debe eliminar?

Un entorno típico puede incluir muchos servicios. Aquí te muestro los más comunes que debes revisar y eliminar:

| Categoría         | Servicios comunes a eliminar                                    |
| ----------------- | --------------------------------------------------------------- |
| 🖥️ Cómputo        | EC2 (instancias), Auto Scaling Groups, AMIs, Snapshots          |
| 💾 Almacenamiento | EBS Volumes, S3 Buckets, Snapshots                              |
| 🌐 Red            | VPCs, Subnets, Security Groups, Internet Gateways, Route Tables |
| 🔧 Balanceo       | ELB (Elastic Load Balancer)                                     |
| 📊 Monitoreo      | CloudWatch Logs, Alarms, Metrics                                |
| 🔐 IAM            | Roles, Policies, Users, Access Keys                             |
| 🛠️ Otros          | RDS, Lambda, API Gateway, etc.                                  |

---

### 🧰 ¿Qué herramientas puedes usar para eliminar tu entorno?

1. **Consola de AWS** (modo gráfico)
2. **AWS CLI** (modo terminal)
3. **AWS CloudFormation** (si todo fue creado como infraestructura como código)

---

### 🧭 Requisitos previos (si usas AWS CLI)

1. Instala AWS CLI:
   En Linux/macOS:

   ```bash
   curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
   unzip awscliv2.zip
   sudo ./aws/install
   ```

   En Windows: descarga desde [https://aws.amazon.com/cli/](https://aws.amazon.com/cli/)

2. Configura tu perfil:

   ```bash
   aws configure
   ```

   Se te pedirá:

   - Access Key ID
   - Secret Access Key
   - Región (por ejemplo: `us-east-1`)
   - Formato de salida (puedes poner `json`)

---

### 🧪 EJEMPLO PRÁCTICO: Eliminando un entorno sencillo en AWS

#### 🎯 Escenario:

Has creado un entorno que incluye:

- 1 instancia EC2
- 1 volumen EBS
- 1 bucket S3
- 1 VPC personalizada
- 1 rol de IAM

Vamos a eliminarlo paso a paso.

---

#### 🔹 PASO 1: Ver las instancias EC2 activas

```bash
aws ec2 describe-instances --query "Reservations[*].Instances[*].InstanceId"
```

#### 🔹 PASO 2: Terminar la instancia EC2

```bash
aws ec2 terminate-instances --instance-ids i-1234567890abcdef0
```

---

#### 🔹 PASO 3: Eliminar volúmenes EBS sin usar

```bash
aws ec2 describe-volumes --filters Name=status,Values=available
```

```bash
aws ec2 delete-volume --volume-id vol-0abcd1234ef567890
```

---

#### 🔹 PASO 4: Eliminar un bucket S3

Primero, vacíalo:

```bash
aws s3 rm s3://mi-bucket-prueba --recursive
```

Luego elimínalo:

```bash
aws s3api delete-bucket --bucket mi-bucket-prueba
```

---

#### 🔹 PASO 5: Eliminar VPC personalizada (¡con cuidado!)

Primero obtén el ID de la VPC:

```bash
aws ec2 describe-vpcs --query "Vpcs[*].VpcId"
```

Elimina los elementos asociados antes de eliminar la VPC (como subredes, gateways, tablas de rutas):

```bash
aws ec2 delete-subnet --subnet-id subnet-0abcd1234
aws ec2 detach-internet-gateway --internet-gateway-id igw-0abcd1234 --vpc-id vpc-0abcd1234
aws ec2 delete-internet-gateway --internet-gateway-id igw-0abcd1234
aws ec2 delete-route-table --route-table-id rtb-0abcd1234
aws ec2 delete-vpc --vpc-id vpc-0abcd1234
```

---

#### 🔹 PASO 6: Eliminar un rol de IAM

```bash
aws iam delete-role-policy --role-name MiRol --policy-name MiPolitica
aws iam delete-role --role-name MiRol
```

---

### ✅ Verificación final

Puedes revisar si ya no hay recursos:

```bash
aws ec2 describe-instances --filters Name=instance-state-name,Values=running
aws s3 ls
aws ec2 describe-vpcs
```

---

### 🧽 ¿Y si usaste CloudFormation?

Si usaste una plantilla, basta con eliminar el _stack_:

```bash
aws cloudformation delete-stack --stack-name MiEntornoDePrueba
```

Esto **automáticamente borra todos los recursos asociados**.

---

### 🔐 Recomendaciones finales

- Verifica que **no quedan recursos activos** (especialmente bases de datos, buckets S3 o instancias EC2)
- **Borra claves de acceso IAM** si ya no usarás esa cuenta
- Puedes habilitar **Billing Alerts** para evitar gastos si algo quedó activo

---

[🔼](#índice)

---

| **Inicio**         | **atrás 6**                                              |
| ------------------ | -------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./5_6_Hacking_etico_y_post_explotacion_avanzada.md) |
