| **Inicio**         | **atrás 25**                                       | **Siguiente 27**                                                   |
| ------------------ | -------------------------------------------------- | ------------------------------------------------------------------ |
| [🏠](../README.md) | [⏪](./7_25_Introduccion_a_Informatica_Forense.md) | [⏩](./7_27_Preparacion_para_la_Certificacion_CompTIA_Security.md) |

---

## **Índice**

| Temario                                                                                                           |
| ----------------------------------------------------------------------------------------------------------------- |
| [1141. Por qué Ciberseguridad para Desarrollo Web](#1141-por-qué-ciberseguridad-para-desarrollo-web)              |
| [1142. No estamos seguros](#1142-no-estamos-seguros)                                                              |
| [1143. Autorización Autenticación y Accountability : AAA](#1143-autorización-autenticación-y-accountability--aaa) |
| [1144. Empecemos por la lógica](#1144-empecemos-por-la-lógica)                                                    |
| [1145. SQL Injection](#1145-sql-injection)                                                                        |
| [1146. De local a producción](#1146-de-local-a-producción)                                                        |
| [1147. DevSecOps como cultura](#1147-devsecops-como-cultura)                                                      |
| [1148. Creando pipelines](#1148-creando-pipelines)                                                                |
| [1149. Corriendo nuestras pruebas](#1149-corriendo-nuestras-pruebas)                                              |
| [1150. Listas de control de privilegios](#1150-listas-de-control-de-privilegios)                                  |
| [1151. Diseñando la arquitectura](#1151-diseñando-la-arquitectura)                                                |
| [1152. Infraestructura como código](#1152-infraestructura-como-código)                                            |
| [1153. Creando la infraestructura](#1153-creando-la-infraestructura)                                              |
| [1154. Creando roles y policies](#1154-creando-roles-y-policies)                                                  |
| [1155. Desplegando funciones lambda](#1155-desplegando-funciones-lambda)                                          |
| [1156. El mundo de la Base de Datos](#1156-el-mundo-de-la-base-de-datos)                                          |
| [1157. Conectando lambdas a una VPC](#1157-conectando-lambdas-a-una-vpc)                                          |
| [1158. Single point of failure](#1158-single-point-of-failure)                                                    |
| [1159. Configurando Auth](#1159-configurando-auth)                                                                |
| [1160. Creando un lambda Authorizer](#1160-creando-un-lambda-authorizer)                                          |
| [1161. Secretos y API Keys](#1161-secretos-y-api-keys)                                                            |
| [1162. Creando Endpoints](#1162-creando-endpoints)                                                                |
| [1163. Evitando Cross Site Scripting o XSS](#1163-evitando-cross-site-scripting-o-xss)                            |
| [1164. Validando la integridad de los datos con tokens](#1164-validando-la-integridad-de-los-datos-con-tokens)    |
| [1165. Conociendo la naturaleza de los datos](#1165-conociendo-la-naturaleza-de-los-datos)                        |
| [1166. Protege tus datos con Key Management Services](#1166-protege-tus-datos-con-key-management-services)        |
| [1167. Sistema de logs](#1167-sistema-de-logs)                                                                    |
| [1168. Observabilidad](#1168-observabilidad)                                                                      |
| [1169. Alertas y Postmortems](#1169-alertas-y-postmortems)                                                        |
| [1170. Errores de CORS](#1170-errores-de-cors)                                                                    |

# **Ciberseguridad para Desarrollo Web**

## **1141. Por qué Ciberseguridad para Desarrollo Web**

### 🔐 ¿Por qué la **Ciberseguridad** es importante para el **Desarrollo Web**?

La **ciberseguridad en desarrollo web** es **esencial** porque protege a:

- Los usuarios (sus datos personales, contraseñas, etc.)
- Las empresas (contra pérdidas económicas, legales o de reputación)
- Los sistemas (infraestructura web, APIs, bases de datos)

Un sitio web sin medidas de seguridad puede ser hackeado fácilmente, lo que podría llevar a robo de datos, fraude, infección con malware, secuestro del sitio, o incluso a consecuencias legales graves si se expone información sensible.

---

### 📌 ¿Qué se debe proteger en un sitio web?

1. **Datos de los usuarios** (ej. contraseñas, direcciones, tarjetas de crédito)
2. **Base de datos**
3. **Sesiones de usuario**
4. **Código fuente y lógica del backend**
5. **Acceso administrativo**
6. **APIs expuestas**
7. **Dominio y certificados SSL**

---

### 🔍 Ejemplos fáciles de entender

#### ✅ 1. Sin seguridad:

Un formulario de login simple:

```html
<form method="POST" action="/login">
  <input name="user" />
  <input name="password" />
</form>
```

Si no validas la entrada ni proteges la sesión, alguien puede hacer **inyección SQL** así:

```
usuario: admin
contraseña: ' OR 1=1 --
```

Eso puede **saltarse el login** y obtener acceso de administrador.

---

#### ✅ 2. Con seguridad aplicada:

En el backend (ej. Node.js), proteges así:

```js
// Protección contra inyección SQL usando parámetros
const user = req.body.user;
const pass = req.body.password;
const result = await db.query(
  "SELECT * FROM users WHERE username = ? AND password = ?",
  [user, pass]
);
```

Además:

- Encriptas las contraseñas con bcrypt
- Usas HTTPS (SSL)
- Validación de formularios
- Token CSRF para proteger formularios

---

### ⚙️ ¿Cómo se "instala" o aplica la seguridad en el desarrollo web?

Aquí “instalar” no se refiere a instalar un software como tal, sino a **integrar prácticas, herramientas y librerías de seguridad** durante el desarrollo.

#### 🔧 Herramientas y prácticas comunes:

| Seguridad Web             | Cómo se aplica o "instala"                                                               |
| ------------------------- | ---------------------------------------------------------------------------------------- |
| 🔒 HTTPS                  | Instalando un certificado SSL (ej. con Let's Encrypt)                                    |
| 🔐 Autenticación segura   | Usar librerías como JWT o Auth0. Encriptar contraseñas con bcrypt.                       |
| 🛡️ Protección contra XSS  | Escapar variables en HTML, usar frameworks como React o Vue que lo hacen por defecto     |
| 🧱 Firewalls              | WAF (Web Application Firewall) como Cloudflare o AWS WAF                                 |
| 🧪 Pruebas de seguridad   | Herramientas como OWASP ZAP, Burp Suite o pruebas automatizadas de seguridad (SAST/DAST) |
| 🧾 Políticas de acceso    | Aplicar roles (admin, user, guest), validar tokens en endpoints sensibles                |
| 📁 Gestión de errores     | No mostrar trazas internas al usuario ("error 500" genérico, logs internos en privado)   |
| 🚫 Bloqueo de inyecciones | Usar ORM (Mongoose, Prisma, Sequelize), validación de entradas (Joi, Zod)                |

---

### 💡 Buenas prácticas para desarrollo web seguro

1. **Principio de privilegio mínimo**: que un usuario solo pueda hacer lo que necesita
2. **Validación del lado cliente y servidor**
3. **No confiar en el frontend**
4. **Registro de logs de acceso y errores**
5. **Actualizaciones periódicas de librerías**
6. **Revisar las dependencias por vulnerabilidades (`npm audit`)**

---

### 📄 Ejemplo completo: Aplicación web segura de inicio de sesión

Supongamos una app en **Node.js + Express + MongoDB**.

---

#### 📁 Estructura simple:

```
- app.js
- routes/login.js
- models/User.js
- middlewares/auth.js
```

---

#### 1. Registro de usuario seguro

```js
// POST /register
const bcrypt = require("bcrypt");

app.post("/register", async (req, res) => {
  const { user, password } = req.body;

  const hashed = await bcrypt.hash(password, 12);
  await User.create({ user, password: hashed });

  res.send("Usuario registrado");
});
```

---

#### 2. Login con validación

```js
// POST /login
app.post("/login", async (req, res) => {
  const { user, password } = req.body;
  const found = await User.findOne({ user });

  if (!found) return res.status(404).send("No existe");

  const match = await bcrypt.compare(password, found.password);
  if (!match) return res.status(401).send("Contraseña incorrecta");

  // Autenticación segura con token (JWT)
  const token = jwt.sign({ id: found._id }, "secreto", { expiresIn: "1h" });
  res.json({ token });
});
```

---

#### 3. Middleware para proteger rutas

```js
// auth.js
const jwt = require("jsonwebtoken");

function auth(req, res, next) {
  const token = req.headers.authorization?.split(" ")[1];
  if (!token) return res.status(403).send("Token requerido");

  try {
    const payload = jwt.verify(token, "secreto");
    req.user = payload;
    next();
  } catch (err) {
    res.status(401).send("Token inválido");
  }
}
```

---

#### 4. Ruta protegida

```js
// GET /dashboard
app.get("/dashboard", auth, (req, res) => {
  res.send(`Hola usuario con ID: ${req.user.id}`);
});
```

---

### 🧠 Resumen final

| Aspecto                      | Por qué importa                                 |
| ---------------------------- | ----------------------------------------------- |
| Autenticación segura         | Evita acceso no autorizado                      |
| Validación de entradas       | Previene XSS, inyección SQL y ataques similares |
| HTTPS y certificados         | Protege la comunicación con el servidor         |
| Protección de sesiones       | Evita secuestros de sesión                      |
| Actualizaciones de librerías | Cierra vulnerabilidades conocidas               |

---

### ✅ Conclusión

La **ciberseguridad en desarrollo web no es opcional**: es una responsabilidad. Asegurar tu aplicación desde el diseño hasta la implementación evita brechas, ataques, multas y pérdida de confianza del usuario.

---

[🔼](#índice)

---

## **1142. No estamos seguros**

### 🔍 “¿Cómo saber si un sistema **no está seguro**?”

Aquí tienes una explicación clara y paso a paso:

---

### 🔐 ¿Qué significa que un sistema **no está seguro**?

Un sistema no seguro es aquel que:

- Tiene **vulnerabilidades conocidas**
- No tiene **parches o actualizaciones**
- Carece de **controles de acceso**
- No tiene **cifrado de datos**
- No tiene un **firewall** o protección contra amenazas
- No está monitoreado ni auditado

---

### 🛠️ ¿Cómo se identifica?

#### ✅ Herramientas para saber si tu sistema no está seguro:

| Herramienta                  | Qué revisa                                                            |
| ---------------------------- | --------------------------------------------------------------------- |
| 🔍 Nmap                      | Detecta puertos abiertos                                              |
| 🧪 Nessus                    | Escanea vulnerabilidades                                              |
| 📦 OWASP ZAP                 | Escanea aplicaciones web                                              |
| 🐍 Lynis (Linux)             | Revisa seguridad en sistemas Linux                                    |
| 🖥️ Windows Defender          | Revisa amenazas en Windows                                            |
| ⚙️ `npm audit` / `pip audit` | Revisa vulnerabilidades en dependencias de software (Node.js, Python) |

---

#### 🔴 Ejemplos de señales de que “no estamos seguros”:

1. **No se usa HTTPS**

   → Los datos se transmiten en texto plano y pueden ser interceptados.

2. **Contraseñas sin cifrar en la base de datos**

   → Si un atacante accede, obtiene todas las credenciales.

3. **El servidor permite conexiones SSH con usuario root**

   → Cualquier persona con la contraseña puede tener control total.

4. **Los logs muestran accesos desde países extraños**

   → Puede indicar una brecha de seguridad o acceso no autorizado.

---

### ⚙️ ¿Cómo "se instala" la seguridad o se empieza a proteger?

1. 🔄 **Actualizar el sistema operativo y software**

   - Linux: `sudo apt update && sudo apt upgrade`
   - Windows: Verifica en “Windows Update”

2. 🔐 **Instalar firewall**

   - Linux: `sudo ufw enable`
   - Windows: Activa desde el Panel de Control

3. 🔍 **Instalar un escáner de seguridad**

   - Nessus: [https://www.tenable.com/products/nessus](https://www.tenable.com/products/nessus)
   - ClamAV: antivirus de línea de comandos

4. 👨‍💻 **Crear usuarios sin privilegios innecesarios**

5. 📊 **Monitorear accesos y errores** con herramientas como Fail2ban o logs en `/var/log/auth.log`

6. 🔑 **Implementar autenticación fuerte** (contraseñas seguras, 2FA)

7. 🧯 **Tener respaldos** en caso de ataques como ransomware

---

### ✅ Ejemplo completo: Detectar que tu servidor **no está seguro** y empezar a protegerlo (Linux)

#### Paso 1: Verificar puertos abiertos

```bash
sudo apt install nmap
nmap localhost
```

Si ves muchos puertos abiertos (ej. 22, 80, 3306), es un riesgo si no los usas.

---

#### Paso 2: Activar firewall UFW

```bash
sudo apt install ufw
sudo ufw enable
sudo ufw default deny incoming
sudo ufw allow ssh
```

---

#### Paso 3: Revisar usuarios con privilegios

```bash
cat /etc/passwd
```

Busca usuarios sospechosos o innecesarios.

---

#### Paso 4: Instalar escáner de seguridad

```bash
sudo apt install lynis
sudo lynis audit system
```

Esto genera un informe con debilidades.

---

#### Paso 5: Asegurar contraseñas

Edita `/etc/login.defs` para exigir contraseñas más fuertes.

---

#### Resultado

Después de aplicar estas medidas, puedes verificar que:

- Solo los servicios necesarios están activos
- Tienes logs, firewall y escaneo activo
- Las contraseñas son seguras
- El sistema tiene las últimas actualizaciones

---

### 🧠 Conclusión

> Si **"no estamos seguros"**, significa que hay brechas que un atacante podría aprovechar.
>
> La seguridad no se instala como un programa, se **implementa** con prácticas, configuraciones, actualizaciones y monitoreo constante.

---

[🔼](#índice)

---

## **1143. Autorización Autenticación y Accountability : AAA**

### 🔐 ¿Qué es AAA en ciberseguridad?

El modelo **AAA** es un enfoque fundamental en seguridad que garantiza que las personas solo accedan a lo que tienen permitido y que sus acciones puedan ser rastreadas.

AAA significa:

| Letra              | Significado            | ¿Qué hace?                                                          |
| ------------------ | ---------------------- | ------------------------------------------------------------------- |
| **Autenticación**  | _Authentication_       | Verifica **quién eres**                                             |
| **Autorización**   | _Authorization_        | Verifica **qué puedes hacer**                                       |
| **Accountability** | _Auditoría / Registro_ | Registra **lo que hiciste** (también conocido como **"auditoría"**) |

---

### 🧠 Explicación con ejemplos simples

#### 1. 🔑 Autenticación (Authentication)

**¿Quién eres tú?**

Verifica tu identidad usando:

- Usuario y contraseña
- Biometría (huella, rostro)
- Tarjeta inteligente
- 2FA (Autenticación de dos factores)

🧸 **Ejemplo sencillo:**

Cuando abres tu Facebook e ingresas tu **usuario y contraseña**, estás **autenticándote**. El sistema comprueba que tú eres tú.

---

#### 2. 🛂 Autorización (Authorization)

**¿Qué puedes hacer?**

Una vez que el sistema sabe quién eres, **controla tu acceso** a recursos:

- Un administrador puede **crear usuarios**
- Un empleado solo puede **ver su hoja de pago**
- Un visitante no puede **modificar datos**

🧸 **Ejemplo sencillo:**

En una empresa, el jefe puede acceder a todos los reportes, pero tú solo puedes ver los que te pertenecen.

---

#### 3. 📋 Accountability (Auditoría o responsabilidad)

**¿Qué hiciste?**

Registra las acciones del usuario:

- Cuándo inició sesión
- Qué archivos editó
- Si intentó acceder a un área prohibida

🧸 **Ejemplo sencillo:**

Si borras un archivo del sistema, tu acción queda registrada con tu nombre, fecha y hora.

---

### 🧰 ¿Cómo se **instala** o implementa AAA?

AAA no se instala como una aplicación, sino que se **configura** en sistemas, redes o aplicaciones. Aquí te muestro cómo en diferentes entornos:

---

#### 🔧 En un servidor Linux:

##### 1. 🔐 Autenticación: solo usuarios válidos

```bash
sudo adduser gustavo
sudo passwd gustavo
```

##### 2. 🛂 Autorización: definir permisos

```bash
sudo usermod -aG sudo gustavo  # Permite a Gustavo ser admin
```

O limitar permisos con archivos:

```bash
chmod 640 archivo.txt
chown gustavo archivo.txt
```

##### 3. 📋 Accountability: logs de actividad

```bash
cat /var/log/auth.log  # Muestra quién inició sesión y cuándo
```

Puedes instalar **auditd** para monitoreo más avanzado:

```bash
sudo apt install auditd
sudo auditctl -w /etc/passwd -p wa
```

---

#### 🧰 En aplicaciones web (por ejemplo, en Node.js)

##### 1. Autenticación (Login con JWT)

```js
const jwt = require("jsonwebtoken");
const token = jwt.sign({ userId: user.id }, "secreto");
```

##### 2. Autorización (Roles)

```js
if (user.role !== "admin") return res.status(403).send("No autorizado");
```

##### 3. Accountability (logs)

```js
console.log(`${user.email} eliminó el archivo X a las ${new Date()}`);
```

---

### ✅ Ejemplo completo: AAA en una aplicación web

Supongamos que tienes una app de administración para una empresa.

#### 🔐 Autenticación:

- Los usuarios inician sesión con usuario/contraseña.
- Se implementa 2FA con Google Authenticator.

```js
// Login
POST /api/login
{
  "email": "gustavo@gmail.com",
  "password": "12345678"
}
```

Sistema verifica en la base de datos si es correcto y crea un **token JWT**.

---

#### 🛂 Autorización:

- El rol de usuario determina qué puede ver/hacer.

```js
if (user.role !== "admin") {
  return res.status(403).json({ message: "No autorizado" });
}
```

- "Gustavo" es "admin", puede ver todos los reportes.

---

#### 📋 Accountability:

- Cada acción se registra con fecha y usuario:

```js
logger.info(`${user.email} creó nuevo reporte el ${new Date()}`);
```

Estos logs se almacenan y sirven para auditar comportamientos sospechosos.

---

### 🧠 Conclusión

> El modelo **AAA** (Autenticación, Autorización y Accountability) garantiza seguridad completa:

- Solo entra quien debe (autenticación)
- Solo hace lo que puede (autorización)
- Todo queda registrado (accountability)

---

[🔼](#índice)

---

## **1144. Empecemos por la lógica**

### 🧠 ¿Qué es la lógica?

La **lógica** es la **ciencia del razonamiento válido**. En tecnología, especialmente en programación y ciberseguridad, se usa para **tomar decisiones basadas en condiciones**. Es como enseñarle a una máquina a **pensar paso a paso** y tomar decisiones según ciertas reglas.

> En palabras simples: **la lógica es pensar con claridad y sin contradicciones**.

---

### 🔎 Tipos de lógica más usados en informática

| Tipo de lógica         | Descripción breve                                | Ejemplo fácil                      |
| ---------------------- | ------------------------------------------------ | ---------------------------------- |
| **Lógica booleana**    | Usa valores: verdadero (1) o falso (0)           | ¿Está encendida la luz? Sí/No      |
| **Lógica condicional** | Toma decisiones: _si pasa esto, haz esto otro_   | Si llueve, entonces llevo paraguas |
| **Lógica matemática**  | Opera con números y comparaciones                | ¿5 > 3? Sí                         |
| **Lógica binaria**     | Representa información en 1s y 0s                | Computadoras procesan en binario   |
| **Lógica de control**  | Organiza flujos: secuencia, repetición, decisión | Repetir 5 veces: imprime "Hola"    |

---

### 🧸 Ejemplos fáciles de entender

#### Ejemplo 1: Lógica condicional (IF)

```text
Si tengo hambre, como. Si no, sigo trabajando.
```

**Traducción a código:**

```python
if tengo_hambre:
    comer()
else:
    trabajar()
```

---

#### Ejemplo 2: Lógica booleana

```text
¿Tienes permiso? Sí (True) o No (False)
```

```python
permiso = True

if permiso:
    print("Puedes entrar")
else:
    print("No puedes entrar")
```

---

#### Ejemplo 3: Lógica con ciclos (bucles)

```text
Repite 3 veces: "Bienvenido"
```

```python
for i in range(3):
    print("Bienvenido")
```

---

### 🧰 ¿Cómo se "instala" la lógica?

⚠️ No se instala como un software, **se desarrolla en tu mente**. Aprender lógica es como entrenar un músculo. Pero aquí te dejo cómo **"aplicarla"** con pasos prácticos:

#### 🔧 1. Practicar con situaciones diarias

- Si hace calor, uso polo.
- Si me llaman, contesto si tengo saldo.

#### 💡 2. Resolver acertijos o juegos de lógica

- Juegos tipo Sudoku, ajedrez, rompecabezas.

#### 🧮 3. Usar lenguaje de programación (Python recomendado)

Instálalo así:

##### En Windows:

1. Descarga Python desde [https://www.python.org/](https://www.python.org/)
2. Instálalo marcando **“Add to PATH”**
3. Abre CMD y escribe:

   ```bash
   python
   ```

##### Escribe código simple:

```python
edad = 18

if edad >= 18:
    print("Eres mayor de edad")
else:
    print("Eres menor de edad")
```

---

### ✅ Ejemplo completo: "Lógica para abrir una puerta"

**Problema:**

Una puerta solo se abre si:

- El usuario tiene permiso
- Y la clave es correcta

#### 🧠 Pensamiento lógico:

```text
Si tiene permiso Y la clave es correcta, abre la puerta.
Sino, no abrir.
```

#### 💻 Código en Python:

```python
permiso = True
clave = "1234"
clave_ingresada = input("Ingresa la clave: ")

if permiso and clave_ingresada == clave:
    print("✅ Puerta abierta")
else:
    print("❌ Acceso denegado")
```

---

### 🧠 Conclusión

> La **lógica** es la base de toda la programación, ciberseguridad y tecnología. Si sabes **analizar situaciones, comparar condiciones y tomar decisiones**, ya estás usando lógica.

---

[🔼](#índice)

---

## **1145. SQL Injection**

### 🔍 ¿Qué es SQL Injection?

**SQL Injection** (Inyección de SQL) es una técnica de ataque donde un atacante **inyecta código SQL malicioso** en una consulta a la base de datos a través de entradas vulnerables (como formularios, URLs, campos de búsqueda, etc.).

> En palabras simples: el atacante **engaña al sistema** para que ejecute comandos no autorizados en la base de datos.

---

### 📦 ¿Cómo sucede?

Esto ocurre cuando una aplicación:

- **No valida correctamente los datos del usuario**.
- **Concatena directamente** las entradas del usuario con consultas SQL.

#### 🧱 Estructura básica de una consulta SQL segura:

```sql
SELECT * FROM usuarios WHERE usuario = 'gustavo' AND clave = '1234';
```

#### 💥 Con SQL Injection malicioso:

```sql
SELECT * FROM usuarios WHERE usuario = 'gustavo' AND clave = '' OR '1'='1';
```

> `'1'='1'` siempre es **verdadero**, por lo que **se salta la contraseña**.

---

### 🧠 Ejemplo fácil de entender

Imagina un **formulario de login** con dos campos:

- Usuario: `admin`
- Contraseña: `' OR '1'='1`

El código inseguro que maneja el formulario es:

```python
consulta = "SELECT * FROM usuarios WHERE usuario = '" + usuario + "' AND clave = '" + clave + "';"
```

Con la inyección:

```sql
SELECT * FROM usuarios WHERE usuario = 'admin' AND clave = '' OR '1'='1';
```

Resultado: el atacante **entra sin la clave real**.

---

### ⚙️ ¿Cómo se "instala" una SQL Injection?

No se instala como un software, sino que se **explota** desde el navegador o herramientas como:

- Navegador normal (usando formularios)
- Herramientas como:

  - **sqlmap** (automatiza SQL Injection)
  - **Burp Suite** (para interceptar peticiones)
  - **Postman** (para probar APIs)

#### 🛠️ Instalación básica de sqlmap (en Linux):

```bash
sudo apt install sqlmap
```

#### Ejemplo de uso:

```bash
sqlmap -u "http://victima.com/login.php?usuario=admin&clave=" --dbs
```

---

### 🔐 ¿Cómo prevenir SQL Injection?

| Medida                                  | Explicación                                                      |
| --------------------------------------- | ---------------------------------------------------------------- |
| **Usar sentencias preparadas**          | No concatena strings, sino que separa el código SQL de los datos |
| **Validar entradas**                    | Nunca confiar en los datos del usuario                           |
| **Usar ORM (Object Relational Mapper)** | Como Sequelize, Hibernate, Django ORM, etc.                      |
| **Desactivar errores visibles**         | No mostrar detalles de errores SQL al usuario                    |
| **Control de acceso**                   | Limitar permisos de la cuenta de la base de datos                |

---

### ✅ Ejemplo completo

#### 1. Supongamos un login **vulnerable** en PHP:

```php
<?php
$usuario = $_POST['usuario'];
$clave = $_POST['clave'];

$conn = new mysqli("localhost", "root", "", "mi_bd");
$sql = "SELECT * FROM usuarios WHERE usuario = '$usuario' AND clave = '$clave'";
$resultado = $conn->query($sql);

if ($resultado->num_rows > 0) {
    echo "🎉 Acceso concedido";
} else {
    echo "❌ Acceso denegado";
}
?>
```

#### 2. Ataque usando SQL Injection:

- Usuario: `admin`
- Contraseña: `' OR '1'='1`

Consulta final que se ejecuta:

```sql
SELECT * FROM usuarios WHERE usuario = 'admin' AND clave = '' OR '1'='1';
```

👉 Siempre devuelve verdadero, ¡el atacante entra!

---

#### 🛡️ Solución segura usando sentencias preparadas (PHP + MySQLi):

```php
<?php
$usuario = $_POST['usuario'];
$clave = $_POST['clave'];

$conn = new mysqli("localhost", "root", "", "mi_bd");
$stmt = $conn->prepare("SELECT * FROM usuarios WHERE usuario = ? AND clave = ?");
$stmt->bind_param("ss", $usuario, $clave);
$stmt->execute();
$resultado = $stmt->get_result();

if ($resultado->num_rows > 0) {
    echo "🎉 Acceso concedido";
} else {
    echo "❌ Acceso denegado";
}
?>
```

> ✅ En este caso, el código **no ejecuta directamente lo que el usuario escribe**, por lo que se **bloquea la inyección**.

---

### 🧠 Conclusión

- **SQL Injection** es uno de los ataques más comunes y peligrosos.
- Es fácil de ejecutar si la aplicación está mal diseñada.
- Se puede prevenir con buenas prácticas como **sentencias preparadas** y **validación de entradas**.

---

[🔼](#índice)

---

## **1146. De local a producción**

### 🔍 ¿Qué significa "De local a producción"?

Trabajar **"en local"** significa desarrollar en tu propia computadora (localhost).
Pasar a **"producción"** significa desplegar (publicar) ese proyecto en internet para que **otros lo puedan usar** (clientes, usuarios, etc.).

> Es como cocinar en casa (local) y luego servir el plato en un restaurante (producción).

---

### 🛠️ ¿Qué se necesita para pasar a producción?

Depende del stack que uses. Pero normalmente vas a necesitar:

| Recurso                       | ¿Para qué sirve?                                |
| ----------------------------- | ----------------------------------------------- |
| **Hosting/servidor**          | Lugar donde estará tu app (Vercel, Render, VPS) |
| **Base de datos en la nube**  | MongoDB Atlas, PostgreSQL en Supabase, etc.     |
| **Dominio (opcional)**        | Para tener algo como `midominio.com`            |
| **Variables de entorno**      | Guardar secretos como contraseñas y APIs        |
| **Herramienta de despliegue** | Git, CI/CD, Docker, etc.                        |

---

### 🧪 Ejemplo fácil de entender

#### Proyecto: Aplicación de tareas en React (frontend) y Node.js + MongoDB (backend)

- En local:

  - Frontend en React (`http://localhost:5173`)
  - Backend en Express (`http://localhost:3000`)
  - MongoDB en local (`mongodb://localhost:27017/tareasdb`)

Queremos que esto esté en producción, por ejemplo:

- Frontend: `https://mis-tareas.vercel.app`
- Backend: `https://api-mis-tareas.onrender.com`
- MongoDB: alojado en MongoDB Atlas

---

### ⚙️ ¿Cómo se "instala" en producción?

Veámoslo en **3 etapas simples**:

---

#### 🧱 1. Subir el código a GitHub

Sube tu proyecto a GitHub (o GitLab/Bitbucket) para facilitar el despliegue.

```bash
git init
git add .
git commit -m "Proyecto de tareas"
git remote add origin https://github.com/tuusuario/tareas.git
git push -u origin main
```

---

#### 🚀 2. Desplegar el frontend

> Usaremos **Vercel** para React

1. Ve a [https://vercel.com](https://vercel.com)
2. Conéctalo con tu cuenta de GitHub
3. Elige el repositorio del frontend
4. Configura si es necesario (por ejemplo, `vite` como framework)
5. Agrega variables de entorno si se conectará con el backend:

   - `VITE_API_URL=https://api-mis-tareas.onrender.com`

6. Haz clic en **Deploy**

✅ Tu frontend ya está publicado.

---

#### 🛠️ 3. Desplegar el backend

> Usaremos **Render** para Express

1. Ve a [https://render.com](https://render.com)
2. Conéctate con GitHub
3. Elige el repositorio del backend
4. Configura:

   - Build Command: `npm install`
   - Start Command: `node index.js` o `npm start`

5. Variables de entorno:

   - `MONGO_URI=mongodb+srv://...`
   - `PORT=10000` _(Render lo asigna automáticamente)_

6. Haz clic en **Deploy**

✅ Tu backend ya está en la nube.

---

#### 🧮 4. Subir tu base de datos a la nube

> Usaremos **MongoDB Atlas**

1. Ir a [https://www.mongodb.com/cloud/atlas](https://www.mongodb.com/cloud/atlas)
2. Crear un clúster gratis
3. Crear una base de datos: `tareasdb`
4. Crear un usuario con contraseña
5. Agregar tu IP (o permitir acceso desde todas: `0.0.0.0/0`)
6. Obtendrás una URL como:

   ```
   mongodb+srv://usuario:clave@cluster.mongodb.net/tareasdb?retryWrites=true&w=majority
   ```

7. Esa URL se usa como variable `MONGO_URI` en tu backend

---

### ✅ Ejemplo completo

#### Estructura del proyecto:

```
📁 tareas/
 ├── frontend/  --> React + Vite
 └── backend/   --> Node.js + Express + Mongoose
```

#### 1. En local:

- React corre en `localhost:5173`
- Express corre en `localhost:3000`
- MongoDB corre en `localhost:27017`

#### 2. En producción:

- Frontend: Vercel → `https://tareas.vercel.app`
- Backend: Render → `https://tareas-api.onrender.com`
- MongoDB: Atlas

#### 3. Variables de entorno:

##### En frontend (Vercel):

```
VITE_API_URL=https://tareas-api.onrender.com
```

##### En backend (Render):

```
PORT=10000
MONGO_URI=mongodb+srv://usuario:clave@cluster.mongodb.net/tareasdb
```

---

### 🧠 Recomendaciones finales

- Usa **variables de entorno** (nunca publiques contraseñas)
- Usa **HTTPS** en producción
- Habilita **CORS** en el backend si frontend y backend están separados
- Usa servicios como **Vercel, Render, Railway** si no quieres administrar servidores
- Para producción seria, usa **Docker + VPS** (más avanzado)

---

[🔼](#índice)

---

## **1147. DevSecOps como cultura**

### 🧠 ¿Qué es DevSecOps?

**DevSecOps** es una **cultura de desarrollo de software** que **integra la seguridad (Sec)** desde el principio dentro del proceso de desarrollo y operaciones (Dev + Ops).

#### ¿De dónde viene el nombre?

- **Dev**: Desarrollo
- **Sec**: Seguridad
- **Ops**: Operaciones

> 💡 Es la evolución de DevOps, agregando la seguridad como parte **activa y automática** del ciclo de vida del software.

---

### 🎯 ¿Cuál es el objetivo de DevSecOps?

- Hacer que **la seguridad no sea una etapa al final**, sino que esté **presente desde el diseño hasta el despliegue**.
- Detectar y corregir vulnerabilidades **rápido y automáticamente**.
- Fomentar la **colaboración entre desarrolladores, equipos de seguridad y operaciones**.
- Automatizar pruebas de seguridad en cada cambio del código.

---

### 🧱 Características principales

| Elemento                  | Significado                                                                 |
| ------------------------- | --------------------------------------------------------------------------- |
| **Shift-left**            | Detectar problemas de seguridad desde el inicio del desarrollo              |
| **Automatización**        | Usar herramientas que detecten errores de seguridad sin intervención humana |
| **Integración continua**  | Las pruebas de seguridad ocurren cada vez que hay un cambio en el código    |
| **Colaboración cultural** | Todos (devs, ops, seguridad) son responsables de la ciberseguridad          |
| **Educación constante**   | Capacitar al equipo en buenas prácticas de ciberseguridad                   |

---

### 🧪 Ejemplos fáciles de entender

#### 🔧 Caso 1: Sin DevSecOps

Un desarrollador crea una app, la entrega al final al equipo de seguridad. Ahí recién encuentran fallas (por ejemplo, SQL Injection), y toca rehacer partes del código.

Resultado: **Retrasos, costos altos y software vulnerable.**

---

#### 🔐 Caso 2: Con DevSecOps

El desarrollador al guardar código, ejecuta automáticamente:

- Análisis de dependencias inseguras (con herramientas como **Snyk**)
- Escaneo de código estático (con **SonarQube** o **Semgrep**)
- Tests automáticos de seguridad (con **OWASP ZAP** en CI/CD)

Si hay un error, no se aprueba el código hasta corregirlo.

Resultado: **Aplicación más segura, menos trabajo manual y más eficiencia.**

---

### ⚙️ ¿Cómo se "instala" o implementa DevSecOps?

Aunque no es una app que se instala, DevSecOps se **implementa como un conjunto de herramientas + prácticas + mentalidad**. Se puede aplicar así:

---

#### 🔄 Pasos para aplicar DevSecOps como cultura

##### 1. **Capacitar al equipo**

- Todos deben entender los principios básicos de ciberseguridad.
- Realizar talleres o cursos sobre seguridad en desarrollo.

##### 2. **Integrar seguridad en el pipeline de CI/CD**

- Usar herramientas automáticas en el flujo de integración continua, como:

  - **Snyk, Trivy, SonarQube, Bandit, ESLint, OWASP ZAP, etc.**

##### 3. **Automatizar escaneos**

- Agregar análisis de vulnerabilidades a cada "push" o "pull request".

##### 4. **Revisiones seguras de código**

- Añadir reglas para que el código no se apruebe si hay errores de seguridad.

##### 5. **Aplicar políticas de infraestructura segura**

- Usar Terraform o Kubernetes con validaciones de seguridad (policy as code).

##### 6. **Monitoreo y alertas**

- Instalar herramientas de monitoreo como **Prometheus + Grafana**, alertas en **Slack/Teams** ante fallos.

##### 7. **Mejora continua**

- Medir métricas: tiempo de detección de vulnerabilidades, tiempo de respuesta, etc.
- Retroalimentación constante entre equipos.

---

### 🧰 Herramientas comunes en DevSecOps

| Tipo                         | Herramienta común                  |
| ---------------------------- | ---------------------------------- |
| Análisis de dependencias     | Snyk, OWASP Dependency-Check       |
| Análisis de código           | SonarQube, Semgrep, Bandit         |
| Escaneo de contenedores      | Trivy, Clair                       |
| Pruebas dinámicas            | OWASP ZAP, Burp Suite              |
| CI/CD                        | GitHub Actions, GitLab CI, Jenkins |
| Seguridad de infraestructura | Checkov, KICS, Terraform Sentinel  |

---

### ✅ Ejemplo completo de DevSecOps en acción

#### 🎯 Caso: Proyecto con React (frontend) + Node.js (backend) + MongoDB, usando GitHub + Vercel + Render

#### 1. Desarrollo en local

- El equipo trabaja normalmente con Git y Visual Studio Code.
- Se usa ESLint y Prettier para estilo de código.

#### 2. CI/CD configurado en GitHub Actions

Cada vez que alguien hace un `push`, se ejecutan estas acciones:

##### 📌 `.github/workflows/security.yml`

```yaml
name: Seguridad DevSecOps

on: [push]

jobs:
  security:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2

      - name: Escaneo de dependencias con Snyk
        uses: snyk/actions/node@master
        env:
          SNYK_TOKEN: ${{ secrets.SNYK_TOKEN }}

      - name: Análisis estático con Semgrep
        uses: returntocorp/semgrep-action@v1

      - name: Linter y pruebas
        run: |
          npm install
          npm run lint
          npm test
```

> Si alguno de estos pasos falla, **el código no se despliega**.

---

#### 3. Seguridad en la infraestructura

- El backend en Render no se despliega si no pasan los tests de seguridad.
- La base de datos en MongoDB Atlas está con IP restringida y contraseña segura.

---

#### 4. Monitoreo

- Se agregan logs en producción con **LogRocket** (frontend) y **Winston** (backend).
- Alertas si se detecta actividad inusual.

---

### 🧠 Conclusión

DevSecOps no es una herramienta, es una **cultura completa** donde:

- Todos en el equipo se preocupan por la seguridad.
- Se automatizan las pruebas de seguridad en el flujo de desarrollo.
- Se evita el "parcheo al final", asegurando desde el inicio.
- Se mejora la calidad del software y se reducen riesgos y costos.

---

[🔼](#índice)

---

## **1148. Creando pipelines**

### 1) 🧠 ¿Qué es un _pipeline_?

Un **pipeline** es una **secuencia automatizada de pasos** (jobs) que se ejecutan cada vez que ocurre un evento (por ejemplo, un _push_ o _merge request_) para **construir, probar, analizar, empaquetar y desplegar** tu software (o datos) **sin intervención manual**.

> Piensa en una **fábrica automática**: cada commit entra por un extremo y del otro sale (idealmente) software probado, seguro y desplegado.

---

### 2) 🚦 Tipos de pipelines más comunes

| Tipo                                    | Objetivo                           | Ejemplos de pasos                               |
| --------------------------------------- | ---------------------------------- | ----------------------------------------------- |
| **CI (Continuous Integration)**         | Validar cada cambio de código      | build, tests, linters, SAST                     |
| **CD (Continuous Delivery/Deployment)** | Entregar/desplegar automáticamente | build de imagen, push a registry, deploy a prod |
| **Pipelines de seguridad (DevSecOps)**  | “Shift-left” de seguridad          | SCA (dependencias), SAST, DAST, IaC scanning    |
| **Pipelines de datos (DataOps/ETL)**    | Mover/transformar datos            | extracción, limpieza, carga, validaciones       |

_(Por el contexto de tus últimas preguntas, me enfoco en **CI/CD + seguridad**.)_

---

### 3) 🧱 Bloques típicos de un pipeline CI/CD

1. **Checkout del código**
2. **Configuración del entorno** (lenguaje, versión)
3. **Instalación de dependencias**
4. **Análisis estático (linter, SAST)**
5. **Ejecución de pruebas** (unitarias, integración)
6. **Build** (artefactos binarios, bundles, contenedores)
7. **Escaneo de seguridad** (dependencias, imágenes Docker)
8. **Publicación de artefactos** (registry, S3, releases)
9. **Despliegue** (staging → producción)
10. **Notificaciones** (Slack, Teams, email)

---

### 4) 🛠️ Herramientas populares para crear pipelines

| Plataforma               | Archivo de pipeline                    | Comentario                                      |
| ------------------------ | -------------------------------------- | ----------------------------------------------- |
| **GitHub Actions**       | `.github/workflows/*.yml`              | Muy fácil de empezar, gratis hasta cierto uso   |
| **GitLab CI/CD**         | `.gitlab-ci.yml`                       | Integrado con runners propios o compartidos     |
| **Jenkins**              | `Jenkinsfile`                          | On-premise, súper flexible, requiere mantenerlo |
| **Azure DevOps**         | `azure-pipelines.yml`                  | Integrado con el ecosistema Microsoft           |
| **CircleCI / Travis CI** | `.circleci/config.yml` / `.travis.yml` | SaaS, fáciles para proyectos open source        |

---

### 5) “Cómo se instala” (mejor dicho, **cómo se configura**) un pipeline

#### A) **GitHub Actions (el más directo para empezar)**

1. Sube tu repo a GitHub.
2. Crea la carpeta `.github/workflows/`.
3. Dentro, crea un archivo YAML (por ejemplo `ci-cd.yml`).
4. (Opcional) Configura **Secrets** (Settings → Secrets and variables → Actions) para claves, tokens, etc.
5. Cada _push_ o _pull request_ disparará el pipeline.

#### B) **GitLab CI**

1. Sube el repo a GitLab.
2. Crea el archivo `.gitlab-ci.yml` en la raíz.
3. Configura _runners_ (pueden ser los compartidos de GitLab o propios).
4. Usa **CI/CD Variables** para secretos.

#### C) **Jenkins (auto-hosted)**

1. Instala Jenkins (Docker o paquete del SO).
2. Instala plugins necesarios (Git, Pipeline, Blue Ocean, etc.).
3. Crea un `Jenkinsfile` en el repo (pipeline declarativo).
4. Configura un job multibranch o pipeline desde Jenkins.

---

### 6) 🧩 Buenas prácticas

- **Shift-left**: corre seguridad y pruebas **temprano**.
- **Fail fast**: que falle rápido si algo está mal.
- **Cache de dependencias** para acelerar builds.
- **Ambientes separados**: _dev → staging → prod_.
- **Infra as Code (IaC)** + **Policy as Code**.
- **Secretos en el gestor de la plataforma**, nunca en el repo.
- **Versiona artefactos e imágenes Docker** con el número de commit/tag.

---

### 7) ✅ Ejemplo completo (Node.js + tests + SAST + Docker + deploy)

Te dejo **dos versiones**: **GitHub Actions** (principal) y luego **GitLab CI** equivalente.

#### 7.1. Estructura mínima del proyecto

```
.
├── src/
│   └── index.js
├── test/
│   └── app.test.js
├── package.json
├── Dockerfile
└── .github/
    └── workflows/
        └── ci-cd.yml
```

#### 7.2. `Dockerfile` (simple)

```dockerfile
FROM node:20-alpine

WORKDIR /app
COPY package*.json ./
RUN npm ci --omit=dev

COPY . .
EXPOSE 3000
CMD ["npm", "start"]
```

#### 7.3. `package.json` (scripts típicos)

```json
{
  "name": "api-ejemplo",
  "version": "1.0.0",
  "scripts": {
    "lint": "eslint .",
    "test": "jest --coverage",
    "start": "node src/index.js",
    "build": "echo 'Build step (si compilas TS o transpilas)'"
  },
  "devDependencies": {
    "eslint": "^8.0.0",
    "jest": "^29.0.0"
  }
}
```

#### 7.4. **Pipeline en GitHub Actions** (`.github/workflows/ci-cd.yml`)

Este pipeline:

- Se ejecuta en cada **push** y **pull request**.
- Corre **lint + tests**.
- Hace **SAST** con **Semgrep** (puedes comentarlo si no tienes cuenta).
- Construye una **imagen Docker**, la sube a **GitHub Container Registry (GHCR)**.
- (Opcional) Despliega a **Render/Heroku/Kubernetes** (te muestro ejemplo con _kubectl_ comentado).

```yaml
name: CI-CD

on:
  push:
    branches: ["main"]
  pull_request:

jobs:
  ci:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: 20
          cache: "npm"

      - name: Install
        run: npm ci

      - name: Lint
        run: npm run lint

      - name: Test
        run: npm test

      # --- SAST con Semgrep (opcional, requiere token si usas reglas privadas)
      - name: Semgrep SAST
        uses: returntocorp/semgrep-action@v1
        with:
          config: "p/ci" # reglas públicas de semgrep
        env:
          SEMGREP_APP_TOKEN: ${{ secrets.SEMGREP_APP_TOKEN }} # opcional

  build_and_push:
    needs: ci
    runs-on: ubuntu-latest
    permissions:
      contents: read
      packages: write # para subir a GHCR
      id-token: write

    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Login to GHCR
        uses: docker/login-action@v3
        with:
          registry: ghcr.io
          username: ${{ github.actor }}
          password: ${{ secrets.GITHUB_TOKEN }}

      - name: Build image
        run: |
          IMAGE=ghcr.io/${{ github.repository }}/api-ejemplo:${{ github.sha }}
          echo "IMAGE=$IMAGE" >> $GITHUB_ENV
          docker build -t $IMAGE .

      - name: Push image
        run: docker push $IMAGE

  deploy:
    needs: build_and_push
    runs-on: ubuntu-latest
    if: github.ref == 'refs/heads/main' # solo desde main

    steps:
      - name: Checkout
        uses: actions/checkout@v4

      # --- Ejemplo despliegue a Kubernetes (comentalo si no usas K8s) ---
      # - name: Setup kubectl
      #   uses: azure/setup-kubectl@v4
      #
      # - name: Authenticate to cluster
      #   run: |
      #     # Ejemplo con OIDC o usando un secreto KUBECONFIG
      #
      # - name: Deploy
      #   run: |
      #     kubectl set image deployment/api api=$IMAGE
      #     kubectl rollout status deployment/api

      # --- Ejemplo simple: llamar a un webhook de Render/Heroku/your server ---
      - name: Call deploy webhook
        run: curl -X POST ${{ secrets.DEPLOY_WEBHOOK_URL }}
```

**Secrets que deberías definir en GitHub:**

- `SEMGREP_APP_TOKEN` (opcional).
- `DEPLOY_WEBHOOK_URL` (si usas webhook para desplegar).
- O credenciales de Kubernetes / cloud.

---

#### 7.5. **Versión equivalente en GitLab CI** (`.gitlab-ci.yml`)

```yaml
stages:
  - test
  - build
  - deploy

variables:
  DOCKER_IMAGE: $CI_REGISTRY_IMAGE/api-ejemplo:$CI_COMMIT_SHA

cache:
  key: ${CI_COMMIT_REF_SLUG}
  paths:
    - node_modules/

test:
  stage: test
  image: node:20-alpine
  script:
    - npm ci
    - npm run lint
    - npm test
  artifacts:
    reports:
      junit: report.xml

build:
  stage: build
  image: docker:24
  services:
    - docker:24-dind
  script:
    - docker login -u $CI_REGISTRY_USER -p $CI_REGISTRY_PASSWORD $CI_REGISTRY
    - docker build -t $DOCKER_IMAGE .
    - docker push $DOCKER_IMAGE
  only:
    - main

deploy:
  stage: deploy
  image: alpine:latest
  script:
    # Ejemplo: curl al webhook de tu plataforma de despliegue
    - apk add curl
    - curl -X POST $DEPLOY_WEBHOOK_URL
  only:
    - main
```

**Variables a configurar en GitLab → Settings → CI/CD → Variables:**

- `CI_REGISTRY_USER`, `CI_REGISTRY_PASSWORD` (automáticas si usas el registry de GitLab).
- `DEPLOY_WEBHOOK_URL`, tokens, etc.

---

### 8) 🧠 Conclusión

- Un **pipeline** automatiza la calidad y la seguridad del software **desde el primer commit**.
- **No se “instala”**, **se configura** en tu plataforma (GitHub/GitLab/Jenkins) como **código**.
- El pipeline ideal incluye: **lint + tests + seguridad + build + deploy + monitoreo**.
- **Empieza simple** (lint + tests + deploy) y **evoluciona** (SAST, DAST, IaC, contenedores, K8s).

---

[🔼](#índice)

---

## **1149. Corriendo nuestras pruebas**

### 🧠 1. ¿Qué significa "correr nuestras pruebas"?

**Correr pruebas** significa ejecutar scripts que validan si el código

**funciona como debe**, en distintos niveles:

| Tipo de prueba           | ¿Qué prueba?                        | Ejemplo fácil                        |
| ------------------------ | ----------------------------------- | ------------------------------------ |
| **Unitarias**            | Funciones específicas               | `suma(2, 3) debe ser 5`              |
| **Integración**          | Módulos que interactúan             | `registro de usuario guarda en DB`   |
| **End-to-End (E2E)**     | El flujo completo del usuario       | `usuario se loguea y ve su perfil`   |
| **Pruebas de seguridad** | Inyecciones, permisos, validaciones | `SQL Injection no debería funcionar` |

---

### 🛠 2. ¿Cómo se "instala" un sistema de pruebas?

#### ⚙️ Depende del lenguaje y framework:

##### Si usas **JavaScript (Node.js + Jest)**:

```bash
npm install --save-dev jest
```

Y en tu `package.json`:

```json
"scripts": {
  "test": "jest"
}
```

##### Si usas **Python (pytest)**:

```bash
pip install pytest
```

Y puedes correr con:

```bash
pytest
```

##### Si usas **PHP (Laravel)**:

```bash
php artisan test
```

##### Si usas **Java (JUnit + Maven)**:

Incluyes en tu `pom.xml`:

```xml
<dependency>
  <groupId>junit</groupId>
  <artifactId>junit</artifactId>
  <version>4.13.2</version>
  <scope>test</scope>
</dependency>
```

Y ejecutas:

```bash
mvn test
```

---

### 📦 3. ¿Dónde se corren las pruebas?

- ✅ En tu **máquina local** con `npm test`, `pytest`, etc.
- ✅ En la **integración continua (CI)** automáticamente cuando haces un push (ej. con GitHub Actions).
- 🚫 **Nunca directamente en producción**, solo si son pruebas de monitoreo tipo health check o E2E bien controladas.

---

### ✅ 4. Ejemplo completo: Pruebas en Node.js con Jest

#### A) Estructura del proyecto

```
/mi-app/
├── src/
│   └── operaciones.js
├── test/
│   └── operaciones.test.js
├── package.json
```

#### B) `src/operaciones.js`

```js
function suma(a, b) {
  return a + b;
}

function divide(a, b) {
  if (b === 0) throw new Error("No se puede dividir por cero");
  return a / b;
}

module.exports = { suma, divide };
```

#### C) `test/operaciones.test.js`

```js
const { suma, divide } = require("../src/operaciones");

test("suma de 2 + 3 debe ser 5", () => {
  expect(suma(2, 3)).toBe(5);
});

test("no se puede dividir por cero", () => {
  expect(() => divide(5, 0)).toThrow("No se puede dividir por cero");
});
```

#### D) `package.json`

```json
{
  "name": "mi-app",
  "version": "1.0.0",
  "scripts": {
    "test": "jest"
  },
  "devDependencies": {
    "jest": "^29.0.0"
  }
}
```

#### E) Comandos para correr las pruebas

```bash
npm install
npm test
```

---

### 🤖 5. Automatizar pruebas en GitHub Actions (CI)

Crea el archivo `.github/workflows/tests.yml`:

```yaml
name: Run Tests

on:
  push:
    branches: [main]
  pull_request:

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repo
        uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: 20

      - name: Install dependencies
        run: npm ci

      - name: Run tests
        run: npm test
```

Cada vez que hagas un **push a main** o un **pull request**, GitHub ejecutará las pruebas automáticamente.

---

### 🎓 6. Buenas prácticas al correr pruebas

| Práctica                                              | ¿Por qué?                                 |
| ----------------------------------------------------- | ----------------------------------------- |
| 🧪 Escribe pruebas antes o junto al código            | Así piensas en errores desde el inicio    |
| 🧹 Limpia los datos después de las pruebas            | Para evitar efectos colaterales           |
| 🚥 Corre pruebas en CI/CD                             | Para detectar errores antes de producción |
| 🔒 Agrega pruebas de seguridad (inyecciones, accesos) | Para proteger tu aplicación               |

---

### 🧩 7. ¿Y si quieres pruebas E2E?

Puedes usar herramientas como:

- **Playwright** (moderno, potente): `npx playwright test`
- **Cypress** (popular en frontend): `npx cypress open`
- **Selenium** (más usado en entornos enterprise)

¿Quieres un ejemplo con Playwright o Cypress? Te lo armo también, listo para usar.

---

### ✅ Resumen Final

| Paso | Acción                                                |
| ---- | ----------------------------------------------------- |
| 1️⃣   | Elige una herramienta de pruebas (Jest, Pytest, etc.) |
| 2️⃣   | Escribe pruebas que validen lo más crítico            |
| 3️⃣   | Corre localmente (`npm test`, `pytest`, etc.)         |
| 4️⃣   | Automatiza en CI (GitHub Actions, GitLab, etc.)       |
| 5️⃣   | Agrega pruebas de seguridad y cobertura               |

---

[🔼](#índice)

---

## **1150. Listas de control de privilegios**

### 🧠 ¿Qué son las Listas de Control de Privilegios (ACLs)?

Una **Lista de Control de Acceso (ACL)** es una lista que define **quién puede hacer qué** con un recurso.

- Se aplica a archivos, carpetas, bases de datos, servicios, firewalls, etc.
- ACLs permiten **controlar de forma granular los permisos** por usuario o grupo.
- A diferencia de los permisos clásicos (como rwx en Linux), ACL permite especificar **permisos distintos para muchos usuarios y grupos a la vez**.

---

### 📦 Ejemplo fácil de entender

Imagina que tienes un documento llamado `informe.txt` y:

- Tú eres el dueño (usuario `gustavo`) y puedes **leer y escribir**.
- El grupo `contabilidad` solo puede **leer**.
- El usuario `juan` tiene permiso especial para **escribir**, pero **no leer**.

Una ACL para eso sería:

```
Owner: gustavo         → rw
Group: contabilidad    → r-
User: juan             → -w
```

Este nivel de detalle **no es posible con permisos clásicos**, pero sí con ACLs.

---

### ⚙️ ¿Cómo se instalan o configuran?

ACLs ya están integradas en sistemas operativos modernos (Linux, Windows, redes, etc.), pero a veces hay que activarlas.

#### 🔹 En Linux

1. **Verificar que el sistema soporte ACL**:

```bash
mount | grep acl
```

2. **Habilitar ACL en una partición** (si no está):
   Edita `/etc/fstab`:

```
UUID=... / ext4 defaults,acl 0 1
```

Y vuelve a montar:

```bash
sudo mount -o remount,acl /
```

3. **Usar `setfacl` y `getfacl`**:

- Dar permiso de escritura solo a `juan` sobre un archivo:

```bash
setfacl -m u:juan:w informe.txt
```

- Dar permiso de lectura al grupo `contabilidad`:

```bash
setfacl -m g:contabilidad:r informe.txt
```

- Ver las ACLs de un archivo:

```bash
getfacl informe.txt
```

---

#### 🔹 En redes (firewall o routers)

ACLs en redes controlan **qué tráfico entra o sale** según reglas:

- Por IP
- Por protocolo
- Por puerto

Ejemplo (en un router Cisco):

```plaintext
access-list 101 permit tcp 192.168.1.0 0.0.0.255 any eq 80
access-list 101 deny ip any any
```

Significa:

- Permite tráfico HTTP desde la red 192.168.1.0
- Bloquea todo lo demás

---

#### 🔹 En bases de datos

ACLs en bases de datos permiten dar permisos finos:

##### En PostgreSQL:

```sql
GRANT SELECT ON empleados TO contabilidad;
GRANT UPDATE ON empleados TO juan;
```

##### En MongoDB:

```json
{
  "user": "juan",
  "roles": [{ "role": "readWrite", "db": "empresa" }]
}
```

---

### ✅ Ejemplo completo en Linux

Supongamos este escenario:

- Archivo: `reporte.txt`
- Propietario: `gustavo` (rw)
- El grupo `analistas` debe poder leerlo (r)
- El usuario `jose` debe poder leer y escribir (rw)
- Todos los demás: sin acceso

#### A) Crear archivo

```bash
touch reporte.txt
```

#### B) Aplicar permisos ACL

```bash
setfacl -m u:gustavo:rw reporte.txt          # Dueño
setfacl -m g:analistas:r reporte.txt         # Grupo
setfacl -m u:jose:rw reporte.txt             # Usuario especial
setfacl -m o::--- reporte.txt                # Otros sin acceso
```

#### C) Ver ACL aplicada

```bash
getfacl reporte.txt
```

Salida esperada:

```
# file: reporte.txt
# owner: gustavo
# group: gustavo
user::rw-
user:jose:rw-
group:analistas:r--
mask::rw-
other::---
```

---

### 🔐 Ventajas de usar ACLs

| Ventaja                                     | ¿Por qué es útil?                     |
| ------------------------------------------- | ------------------------------------- |
| Permite permisos detallados                 | Varios usuarios con distintos accesos |
| Más flexible que permisos clásicos          | rwx solo permite 1 usuario y 1 grupo  |
| Se usa en servidores, redes, bases de datos | Es un estándar de control moderno     |

---

### 🧪 Buenas prácticas

- **Usa ACLs solo donde se justifiquen**. Si los permisos tradicionales funcionan, son más simples.
- **Documenta las reglas ACL** que aplicas (en servidores, routers o bases de datos).
- **Combina ACL con autenticación fuerte**: saber "quién es quién" es clave.
- **Revísalas periódicamente**: para evitar accesos innecesarios.

---

### 🧩 ¿Quieres aplicarlo en una app web?

En una API o app web (Node.js, Python, Laravel...), ACL puede implementarse con middleware:

```js
if (req.user.role === "admin") {
  next(); // acceso permitido
} else {
  res.status(403).send("No tienes permiso");
}
```

---

[🔼](#índice)

---

## **1151. Diseñando la arquitectura**

### 🧠 ¿Qué significa “Diseñar la arquitectura”?

Diseñar la arquitectura es **definir cómo se van a organizar todos los componentes** de un sistema o aplicación:

- ¿Qué tecnologías se usarán?
- ¿Cómo se comunican entre sí?
- ¿Dónde se alojan los datos?
- ¿Dónde se ejecuta el frontend, backend, base de datos, etc.?

Es como **crear los planos de una casa antes de construirla**.

---

### 📦 Ejemplo fácil de entender

Supongamos que vas a hacer una app como **Netflix**:

- Usuarios ven películas online.
- Hay perfiles, pagos, recomendaciones.
- Se guarda todo en la nube.

**Diseñar la arquitectura de Netflix** implicaría:

| Parte del sistema       | Decisión de arquitectura                |
| ----------------------- | --------------------------------------- |
| Frontend                | React.js, desplegado en Vercel          |
| Backend                 | Node.js + Express, desplegado en Render |
| Base de datos           | PostgreSQL en Supabase o Railway        |
| Almacenamiento de video | AWS S3 o Cloudflare R2                  |
| Autenticación           | Auth0 o Firebase Auth                   |
| Comunicación interna    | API REST o GraphQL                      |
| Escalabilidad           | Usar contenedores con Docker            |

---

### 🏗️ Tipos comunes de arquitectura de software

1. **Monolítica**

   Todo el código (frontend, lógica, datos) está junto en un solo programa.

   - ✅ Fácil al inicio
   - ❌ Difícil de escalar

2. **Cliente-servidor**

   Hay una parte cliente (frontend) y una parte servidor (backend).

   - React + Node, por ejemplo.

3. **3 capas (o n capas)**

   Separado en:

   - Presentación (UI)
   - Lógica de negocio
   - Acceso a datos

4. **Microservicios**

   Cada parte del sistema es un servicio independiente.

   - Escalable, pero complejo de manejar.

5. **Serverless**

   Ejecutas funciones en la nube cuando se necesitan.

   - Ejemplo: Firebase Functions

---

### ⚙️ ¿Cómo se diseña (o “se instala”) la arquitectura?

1. **Recoger requisitos**

   - ¿Qué debe hacer la aplicación?
   - ¿Cuántos usuarios tendrá?

2. **Elegir estilo de arquitectura**

   - ¿Monolítica, cliente-servidor, microservicios?

3. **Elegir tecnologías**

   - ¿React o Angular? ¿MongoDB o PostgreSQL?

4. **Definir estructura**

   - ¿Cómo se divide el código? ¿Cómo se comunican los módulos?

5. **Dibujar diagramas**

   - Usa herramientas como Lucidchart, Draw\.io o a mano.

6. **Configurar entornos**

   - Dev (local), Staging (pruebas), Prod (producción)

---

### 🖼️ Ejemplo completo: arquitectura de una app de recetas

#### 🎯 Objetivo

Desarrollar una app web de recetas donde:

- Usuarios se registran
- Publican recetas
- Comentan recetas
- Buscan recetas por ingrediente

---

#### 🧱 Diseño arquitectónico

| Componente                 | Tecnología Elegida                  |
| -------------------------- | ----------------------------------- |
| Frontend                   | React + Tailwind (en Vercel)        |
| Backend (API)              | Node.js + Express (en Render)       |
| Base de datos              | MongoDB Atlas (en la nube)          |
| Autenticación              | JSON Web Token (JWT)                |
| Almacenamiento de imágenes | Cloudinary                          |
| Seguridad                  | Helmet, cors, rate-limit en Express |

---

#### 🔧 Estructura general

```plaintext
Frontend (React)
    ⬍
API REST (Node.js + Express)
    ⬍
Base de datos (MongoDB)
```

---

#### 📋 Diagrama de alto nivel (simplificado)

```
[ Navegador del usuario ]
         |
       React
         |
    [ API Express ]
     |     |     |
   Auth  Recetas  Comentarios
         |
     MongoDB
```

---

#### 🧪 Código ejemplo de arquitectura (backend básico)

```bash
mkdir recetas-api
cd recetas-api
npm init -y
npm install express mongoose dotenv cors
```

**index.js**

```js
require("dotenv").config();
const express = require("express");
const app = express();
const cors = require("cors");
const mongoose = require("mongoose");

app.use(cors());
app.use(express.json());

mongoose.connect(process.env.MONGO_URI, () => {
  console.log("✅ Conectado a MongoDB");
});

// Rutas
app.use("/api/recetas", require("./routes/recetas"));

app.listen(4000, () => console.log("Servidor en puerto 4000"));
```

**routes/recetas.js**

```js
const express = require("express");
const router = express.Router();
const Receta = require("../models/Receta");

router.get("/", async (req, res) => {
  const recetas = await Receta.find();
  res.json(recetas);
});

module.exports = router;
```

**models/Receta.js**

```js
const mongoose = require("mongoose");

const recetaSchema = new mongoose.Schema({
  titulo: String,
  ingredientes: [String],
  pasos: String,
  autor: String,
});

module.exports = mongoose.model("Receta", recetaSchema);
```

---

#### 🌍 Frontend básico

Desplegado con Vercel:

```bash
npx create-react-app recetas-frontend
cd recetas-frontend
npm install axios
```

**App.jsx**

```jsx
import { useEffect, useState } from "react";
import axios from "axios";

function App() {
  const [recetas, setRecetas] = useState([]);

  useEffect(() => {
    axios
      .get("https://tu-api/render.com/api/recetas")
      .then((res) => setRecetas(res.data));
  }, []);

  return (
    <div className="p-4">
      <h1>Recetas</h1>
      {recetas.map((r) => (
        <div key={r._id}>
          <h2>{r.titulo}</h2>
          <p>{r.pasos}</p>
        </div>
      ))}
    </div>
  );
}
export default App;
```

---

### ✅ Conclusión

Diseñar la arquitectura es **planear antes de construir**:

| Fase                | ¿Qué haces?                                |
| ------------------- | ------------------------------------------ |
| Recoges requisitos  | ¿Qué debe hacer la app?                    |
| Eliges arquitectura | Monolito, cliente-servidor, microservicios |
| Definir tecnologías | React, Node, Mongo, Firebase, etc.         |
| Diagrama            | Representas la conexión de los componentes |
| Implementación      | Empiezas a desarrollar en base a ese plano |

---

[🔼](#índice)

---

## **1152. Infraestructura como código**

### 🧠 ¿Qué es Infraestructura como Código (IaC)?

**Infraestructura como Código (IaC)** es el proceso de **provisionar y gestionar la infraestructura (servidores, redes, bases de datos, etc.) mediante archivos de código**, en lugar de hacerlo manualmente desde un panel web o consola.

#### 🎯 Objetivo:

Automatizar y estandarizar la creación de entornos (desarrollo, pruebas, producción) con código.

---

### 💡 Ejemplo fácil de entender

#### ✅ Sin IaC:

Supón que quieres levantar una máquina virtual en AWS para tu backend. Tienes que:

1. Entrar a la consola de AWS.
2. Crear manualmente una instancia EC2.
3. Configurar el firewall (grupo de seguridad).
4. Asignar IP, configurar almacenamiento, etc.

¡Eso toma tiempo y puede haber errores humanos!

---

#### ✅ Con IaC:

Solo escribes un archivo `.tf` (si usas Terraform) como este:

```hcl
resource "aws_instance" "web" {
  ami           = "ami-12345678"
  instance_type = "t2.micro"
}
```

Y ejecutas:

```bash
terraform apply
```

¡Y listo! Terraform crea todo automáticamente.

---

### 🧱 Beneficios de IaC

| Beneficio       | Explicación                                                      |
| --------------- | ---------------------------------------------------------------- |
| ✅ Repetible    | Puedes levantar entornos iguales con un solo comando.            |
| 🔁 Versionable  | Todo está en Git, como el resto del código.                      |
| 👥 Colaborativo | El equipo puede revisar la infraestructura como si fuera código. |
| 🛡️ Seguro       | Puedes integrar escaneo de seguridad en pipelines DevSecOps.     |
| 💨 Rápido       | Automatiza despliegues en minutos.                               |

---

### 🛠️ Herramientas populares de IaC

| Herramienta        | Descripción                                        |
| ------------------ | -------------------------------------------------- |
| Terraform          | La más usada, compatible con AWS, Azure, GCP, etc. |
| AWS CloudFormation | Solo para infraestructura en AWS.                  |
| Ansible            | Automatización de configuración.                   |
| Pulumi             | IaC usando JavaScript, TypeScript, Python, etc.    |
| Azure Bicep        | Para infraestructura en Azure.                     |

---

### 🔧 ¿Cómo se instala?

#### 📍 Usaremos Terraform como ejemplo (porque es muy usado y fácil de comenzar).

#### 🔹 Requisitos:

- Tener una cuenta en AWS.
- Instalar Terraform.
- Configurar las credenciales de AWS.

---

#### 1. ✅ Instalar Terraform

**En Windows:**

Descarga desde: [https://developer.hashicorp.com/terraform/downloads](https://developer.hashicorp.com/terraform/downloads)

1. Descarga y descomprime.
2. Agrega el ejecutable al PATH.

**En Linux:**

```bash
sudo apt update
sudo apt install -y gnupg software-properties-common curl
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update
sudo apt install terraform
```

Verifica con:

```bash
terraform -v
```

---

#### 2. ✅ Configurar credenciales de AWS

Crea un usuario IAM en la consola de AWS con permisos de EC2.

Luego en tu terminal:

```bash
aws configure
```

Coloca:

- Access Key ID
- Secret Access Key
- Región: `us-east-1` (por ejemplo)

---

### 📦 Ejemplo completo: Crear una instancia EC2 en AWS con Terraform

#### 1. Crear carpeta de proyecto:

```bash
mkdir terraform-ec2
cd terraform-ec2
```

#### 2. Crear archivo `main.tf` con este contenido:

```hcl
provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "mi-servidor" {
  ami           = "ami-0c55b159cbfafe1f0" # Amazon Linux 2
  instance_type = "t2.micro"

  tags = {
    Name = "ServidorDesdeTerraform"
  }
}
```

> ⚠️ Puedes buscar una `ami` actual en [https://cloud-images.ubuntu.com/locator/](https://cloud-images.ubuntu.com/locator/) o en la consola de AWS.

---

#### 3. Inicializar el proyecto

```bash
terraform init
```

Esto descarga los plugins necesarios.

---

#### 4. Verificar qué se va a crear

```bash
terraform plan
```

---

#### 5. Aplicar los cambios

```bash
terraform apply
```

Escribe `yes` cuando te lo pida.

Esto crea la instancia EC2 en AWS.

---

#### 6. Ver en AWS

Ve a tu consola de AWS → EC2 → Instancias
¡Y verás que se ha creado!

---

#### 7. Destruir la infraestructura (para no pagar)

```bash
terraform destroy
```

---

### 🔐 Relación con Ciberseguridad

La IaC permite:

- Automatizar **configuraciones seguras por defecto**.
- Evitar **errores humanos en firewalls, redes y accesos**.
- **Versionar configuraciones seguras**.
- Integrar pruebas de seguridad (como linters, escaneos, validación de puertos).

---

### 📌 Resumen

| Concepto          | Explicación                                                 |
| ----------------- | ----------------------------------------------------------- |
| ¿Qué es?          | Escribir código para desplegar y gestionar infraestructura. |
| ¿Cómo se instala? | Instalas herramientas como Terraform, Ansible o Pulumi.     |
| ¿Qué gana?        | Velocidad, seguridad, repetibilidad y colaboración.         |
| ¿Ejemplo?         | Crear una instancia EC2 con Terraform.                      |

---

[🔼](#índice)

---

## **1153. Creando la infraestructura**

### 🧠 ¿Qué significa "crear la infraestructura"?

Crear la infraestructura es **provisionar los recursos tecnológicos necesarios** para que una aplicación web funcione: servidores, base de datos, red, almacenamiento, balanceadores, seguridad, etc.

#### 🔧 Incluye cosas como:

- Instancias (servidores virtuales)
- Base de datos (MySQL, PostgreSQL, MongoDB…)
- Buckets (almacenamiento de archivos)
- Firewall o grupos de seguridad
- Dominios, certificados SSL
- Redes privadas (VPC)
- Balanceadores de carga

---

### 🏗️ ¿Por qué es importante automatizar la creación?

**Antes:** Los equipos creaban servidores manualmente desde el panel de AWS o DigitalOcean.

**Ahora:** Lo hacemos con herramientas como:

| Herramienta             | Función principal                        |
| ----------------------- | ---------------------------------------- |
| Terraform               | Define infraestructura como código (IaC) |
| Ansible                 | Configura servidores automáticamente     |
| Docker + Docker Compose | Contenedores ligeros para apps           |
| Kubernetes              | Orquestación de contenedores             |
| CloudFormation          | IaC solo para AWS                        |

---

### 🛠️ Cómo se instala: usando **Terraform** (ejemplo real)

Vamos a construir una infraestructura sencilla:

**Un servidor EC2 en AWS + un bucket de S3 + una base de datos PostgreSQL**

---

### 🔍 Paso a paso: creando la infraestructura

#### 📌 Requisitos:

- Tener una cuenta en **AWS**
- Instalar **Terraform**
- Configurar tu **usuario IAM**

---

### 🧪 PASO 1: Instalar Terraform

#### En Windows:

1. Descarga desde: [https://developer.hashicorp.com/terraform/downloads](https://developer.hashicorp.com/terraform/downloads)
2. Extrae el `.zip`
3. Agrega la carpeta al PATH

#### En Linux (Ubuntu):

```bash
sudo apt update
sudo apt install -y gnupg software-properties-common curl
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update
sudo apt install terraform
```

Verifica:

```bash
terraform -v
```

---

### 🧪 PASO 2: Configura AWS CLI

```bash
aws configure
```

Proporciona:

- AWS Access Key ID
- AWS Secret Access Key
- Región: `us-east-1` (por ejemplo)

---

### 🧪 PASO 3: Escribe la Infraestructura (IaC)

Crea un nuevo proyecto:

```bash
mkdir infraestructura-web
cd infraestructura-web
```

Crea un archivo `main.tf` con este contenido:

```hcl
# Proveedor
provider "aws" {
  region = "us-east-1"
}

# Crear instancia EC2
resource "aws_instance" "mi_servidor" {
  ami           = "ami-0c55b159cbfafe1f0" # Amazon Linux 2
  instance_type = "t2.micro"

  tags = {
    Name = "ServidorWeb"
  }
}

# Crear bucket S3
resource "aws_s3_bucket" "mi_bucket" {
  bucket = "mi-bucket-gustavo-ciberseguridad"
  acl    = "private"
}

# Crear base de datos PostgreSQL
resource "aws_db_instance" "postgresql" {
  allocated_storage    = 20
  engine               = "postgres"
  engine_version       = "14.1"
  instance_class       = "db.t3.micro"
  name                 = "basedatosweb"
  username             = "admin"
  password             = "Password1234"
  skip_final_snapshot  = true
}
```

---

### 🧪 PASO 4: Inicializa Terraform

```bash
terraform init
```

Esto descarga los plugins necesarios.

---

### 🧪 PASO 5: Verifica el plan

```bash
terraform plan
```

Verás qué recursos se van a crear.

---

### 🧪 PASO 6: Aplica el plan

```bash
terraform apply
```

Confirma con `yes`.

Terraform creará la infraestructura en tu cuenta de AWS.

---

### 🧪 PASO 7: Comprobar en AWS

- Ve a la consola de AWS EC2 → verás la instancia.
- Ve a S3 → el bucket creado.
- Ve a RDS → la base de datos PostgreSQL.

---

### 🧪 PASO 8: Destruir (opcional)

```bash
terraform destroy
```

Esto elimina toda la infraestructura si no la necesitas.

---

### 🛡️ Buenas prácticas de ciberseguridad al crear infraestructura

| Práctica                                      | Ejemplo                                       |
| --------------------------------------------- | --------------------------------------------- |
| 🔐 Usar IAM con permisos mínimos              | Usuario con permisos solo para EC2 y S3       |
| 📄 No hardcodear contraseñas                  | Usa `terraform.tfvars` o variables de entorno |
| 🔒 Crear reglas de firewall estrictas         | Solo permitir puerto 22 (SSH) desde tu IP     |
| 🧪 Validar configuración antes del despliegue | Usar `terraform plan`                         |
| 📦 Versionar el código de infraestructura     | Usa Git                                       |

---

[🔼](#índice)

---

## **1154. Creando roles y policies**

### ✅ ¿Qué son los **roles** y las **policies**?

En ciberseguridad y administración de sistemas (especialmente en la nube como AWS, Azure, GCP), los **roles y policies** son herramientas para **gestionar permisos de acceso**.

- **Un rol** define **quién** puede hacer algo.
- **Una policy** define **qué acciones** están permitidas o denegadas.

---

### 📦 Ejemplo cotidiano para entenderlo

> 🏢 Supón que estás en una oficina.
>
> - **Rol**: "Contador"
> - **Policy**: Puede ver reportes financieros, pero no puede modificar contratos legales.

---

### 🎯 ¿Dónde se usan?

- En la nube (como **AWS IAM**, **Azure RBAC** o **Google IAM**)
- En sistemas Linux (usando `sudoers`, `chown`, ACLs…)
- En aplicaciones web (roles como admin, usuario, invitado)

---

### 🔑 En la nube: AWS como ejemplo principal

En **AWS IAM** puedes:

- Crear un **rol IAM** (ej. "Desarrollador de backend")
- Asignarle una **policy** (ej. "Solo acceso a DynamoDB y Lambda")
- Asociar el rol a usuarios, servicios o incluso contenedores (EC2, Lambda…)

---

### 🧰 ¿Cómo se instala y configura? (con Terraform o manualmente en consola AWS)

Te muestro ambas:

---

#### ✅ Opción 1: Crear Rol y Policy desde **Consola de AWS** (GUI)

**1.** Ir a [https://console.aws.amazon.com/iam](https://console.aws.amazon.com/iam)
**2.** Clic en “Roles” → “Crear rol”
**3.** Selecciona el tipo de entidad (ejemplo: EC2 o IAM user)
**4.** Adjunta una política (ej. `AmazonS3ReadOnlyAccess`)
**5.** Asigna un nombre al rol: `LeerSoloS3`

Ya tienes un rol que permite solo lectura de S3.

---

#### ✅ Opción 2: Crear Rol y Policy usando **Terraform** (infraestructura como código)

#### 📁 Estructura del proyecto:

```bash
roles-y-policies/
│
├── main.tf
├── variables.tf
├── outputs.tf
```

#### 📄 `main.tf`:

```hcl
provider "aws" {
  region = "us-east-1"
}

# Crear policy personalizada
resource "aws_iam_policy" "lectura_s3" {
  name        = "LecturaSoloS3"
  description = "Permite solo lectura de objetos S3"
  policy = jsonencode({
    Version = "2012-10-17"
    Statement = [
      {
        Action   = ["s3:GetObject", "s3:ListBucket"]
        Effect   = "Allow"
        Resource = "*"
      }
    ]
  })
}

# Crear rol
resource "aws_iam_role" "rol_lectura_s3" {
  name = "RolLecturaS3"
  assume_role_policy = jsonencode({
    Version = "2012-10-17"
    Statement = [
      {
        Effect = "Allow"
        Principal = {
          Service = "ec2.amazonaws.com"
        }
        Action = "sts:AssumeRole"
      }
    ]
  })
}

# Asociar policy al rol
resource "aws_iam_role_policy_attachment" "adjuntar_policy" {
  role       = aws_iam_role.rol_lectura_s3.name
  policy_arn = aws_iam_policy.lectura_s3.arn
}
```

---

### ⚙️ ¿Cómo se instala y ejecuta?

#### 1. Instala Terraform (si no lo tienes)

- En Linux:

  ```bash
  sudo apt install terraform
  ```

- En Windows: [https://developer.hashicorp.com/terraform/downloads](https://developer.hashicorp.com/terraform/downloads)

#### 2. Configura AWS CLI

```bash
aws configure
```

#### 3. Ejecuta en la terminal:

```bash
terraform init
terraform plan
terraform apply
```

Verás cómo se crea un rol llamado `RolLecturaS3` y una policy `LecturaSoloS3`, la cual se adjunta al rol.

---

### 🧠 ¿Y después?

Este **rol** puede asignarse a:

- Un **usuario IAM** para limitar su acceso.
- Un **servidor EC2** para que solo lea archivos de un bucket S3.
- Una **función Lambda** con acceso limitado a ciertos servicios.

---

### 🛡️ Buenas prácticas

| Práctica                           | Ejemplo                                   |
| ---------------------------------- | ----------------------------------------- |
| ✅ Principio de menor privilegio   | Da solo permisos que se necesitan         |
| ✅ Usa nombres descriptivos        | `LecturaS3ParaEC2Producción`              |
| ✅ Revisa logs (CloudTrail)        | Audita qué hizo cada rol                  |
| ✅ Versiona tus policies con Git   | Así puedes saber quién cambió qué         |
| ✅ No uses `Resource: "*"` en prod | Especifica recursos exactos si es posible |

---

### ✅ Ejemplo completo en acción

**Caso real:**

> Tienes una app web en producción. Necesita que su backend EC2 pueda:
>
> - Leer imágenes desde un bucket S3.
> - Pero **no debe subir, borrar ni modificar nada**.

✅ Solución:

- Crear un **rol IAM** con una policy de solo lectura.
- Asociar ese rol a la instancia EC2 del backend.
- ¡Ya está protegido y limitado por diseño!

---

[🔼](#índice)

---

## **1155. Desplegando funciones lambda**

### 🔹 ¿Qué es una función Lambda?

AWS **Lambda** es un servicio de computación sin servidor (serverless) que **ejecuta tu código automáticamente** cuando ocurre un evento, **sin necesidad de administrar servidores**.

Piensa en Lambda como:

🧠 “Quiero que este código se ejecute **solo cuando alguien haga algo** (suba un archivo, llame una API, etc.)... y **yo no me encargo de servidores**.”

---

### 🔹 ¿Para qué sirve?

- Procesar imágenes al subirlas a S3.
- Crear una API sin servidor.
- Automatizar tareas en la nube.
- Reaccionar a eventos (de DynamoDB, SQS, etc.)
- Validar formularios o correr scripts ligeros.

---

### 🔹 ¿Cómo funciona Lambda?

1. Subes una función (tu código).
2. AWS la ejecuta cuando ocurre un evento.
3. AWS escala y gestiona los recursos automáticamente.

---

### 🔹 Lenguajes soportados

- Node.js
- Python
- Go
- Java
- .NET
- Ruby
- y más…

---

### 🧱 Componentes principales

- **Código**: tu función
- **Handler**: punto de entrada
- **Trigger**: evento que dispara la función
- **Role IAM**: permisos de lo que puede hacer la función (por seguridad)
- **Timeout y memoria**: ajustes de rendimiento

---

### 📦 Ejemplo simple

> 🧪 “Quiero una función que diga ‘Hola Gustavo’ cada vez que la llamo desde una URL”.

---

### 🔨 ¿Cómo se instala y despliega?

#### 🔸 Opción 1: Desde la consola de AWS (GUI)

1. Entra a [https://console.aws.amazon.com/lambda](https://console.aws.amazon.com/lambda)
2. Haz clic en **"Crear función"**
3. Elige “Autor desde cero”
4. Nombre: `saludarGustavo`
5. Tiempo de ejecución: **Node.js 18.x** (u otro)
6. Crear función

En la sección de código, pega esto:

```javascript
exports.handler = async (event) => {
  return {
    statusCode: 200,
    body: JSON.stringify("Hola Gustavo desde Lambda!"),
  };
};
```

7. Haz clic en “Implementar”
8. En “Prueba”, crea una prueba vacía y ejecútala

✅ Resultado: **Hola Gustavo desde Lambda!**

---

#### 🔸 Opción 2: Con AWS CLI (más técnico)

1. Instala AWS CLI y configura con:

```bash
aws configure
```

2. Crea tu código `index.js`:

```javascript
exports.handler = async (event) => {
  return {
    statusCode: 200,
    body: JSON.stringify("¡Hola desde Lambda CLI!"),
  };
};
```

3. Comprime el archivo:

```bash
zip function.zip index.js
```

4. Crea el rol IAM (una sola vez):

```bash
aws iam create-role --role-name lambda-basic-execution \
  --assume-role-policy-document file://trust-policy.json
```

(trust-policy.json debe contener el trust para Lambda, puedo dártelo si lo necesitas)

5. Despliega:

```bash
aws lambda create-function \
  --function-name saludarGus \
  --zip-file fileb://function.zip \
  --handler index.handler \
  --runtime nodejs18.x \
  --role arn:aws:iam::<tu_cuenta>:role/lambda-basic-execution
```

✅ ¡Tu función está lista!

---

#### 🔸 Opción 3: Con **Terraform** (infraestructura como código)

Estructura:

```
lambda-proyecto/
├── main.tf
├── lambda/
│   └── index.js
```

#### 📄 `lambda/index.js`:

```js
exports.handler = async (event) => {
  return {
    statusCode: 200,
    body: JSON.stringify("¡Hola Gustavo desde Terraform!"),
  };
};
```

#### 📄 `main.tf`:

```hcl
provider "aws" {
  region = "us-east-1"
}

resource "aws_iam_role" "lambda_exec" {
  name = "lambda_exec_role"

  assume_role_policy = jsonencode({
    Version = "2012-10-17",
    Statement = [{
      Action = "sts:AssumeRole",
      Principal = {
        Service = "lambda.amazonaws.com"
      },
      Effect = "Allow",
      Sid = ""
    }]
  })
}

resource "aws_iam_role_policy_attachment" "attach_basic" {
  role       = aws_iam_role.lambda_exec.name
  policy_arn = "arn:aws:iam::aws:policy/service-role/AWSLambdaBasicExecutionRole"
}

data "archive_file" "lambda_zip" {
  type        = "zip"
  source_file = "${path.module}/lambda/index.js"
  output_path = "${path.module}/lambda/index.zip"
}

resource "aws_lambda_function" "saludo" {
  function_name = "saludarGustavo"
  role          = aws_iam_role.lambda_exec.arn
  handler       = "index.handler"
  runtime       = "nodejs18.x"
  filename      = data.archive_file.lambda_zip.output_path
  source_code_hash = data.archive_file.lambda_zip.output_base64sha256
}
```

#### ▶️ Ejecutar:

```bash
terraform init
terraform apply
```

---

### ✅ Resultado

Tendrás una función Lambda desplegada que puedes invocar por:

- Consola
- API Gateway (para exponerla como una API REST)
- Evento (por ejemplo, cuando se sube un archivo a S3)
- Cron job (programada)

---

### 🧠 Buenas prácticas

| Práctica                         | Descripción                                               |
| -------------------------------- | --------------------------------------------------------- |
| ✅ Principio de menor privilegio | El rol IAM solo debe tener permisos necesarios            |
| ✅ Versiona tu código            | Usa Git y CI/CD para mantener tu función bajo control     |
| ✅ Observabilidad                | Usa logs (CloudWatch) para ver errores y trazas           |
| ✅ Divide en pequeñas funciones  | No pongas todo en una sola Lambda                         |
| ✅ Usa variables de entorno      | Para no poner credenciales o secretos en el código fuente |

---

[🔼](#índice)

---

## **1156. El mundo de la Base de Datos**

### 🔹 ¿Qué es una Base de Datos?

Una **base de datos** es un lugar donde se **almacena información organizada** para que pueda **buscarse, actualizarse y gestionarse fácilmente**.

#### 🧠 Ejemplo fácil:

Imagina que tienes una **agenda telefónica**. Cada página es una persona, con:

- Nombre
- Teléfono
- Dirección

Una **base de datos** sería una versión digital de esa agenda, ¡pero mucho más poderosa! 📱💻

---

### 🔹 Tipos de Bases de Datos

| Tipo                      | Ejemplo                       | Para qué sirve                                            |
| ------------------------- | ----------------------------- | --------------------------------------------------------- |
| **Relacional**            | MySQL, PostgreSQL, SQL Server | Tablas conectadas entre sí (clientes, pedidos, productos) |
| **No Relacional (NoSQL)** | MongoDB, Redis                | Datos flexibles como JSON, documentos, claves/valores     |
| **Tiempo Real**           | Firebase Realtime DB          | Apps móviles/chat en vivo                                 |
| **Orientada a Grafos**    | Neo4j                         | Redes sociales, relaciones complejas entre nodos          |

---

### 🔹 ¿Dónde se usan las Bases de Datos?

- Aplicaciones web (login de usuarios, e-commerce)
- Redes sociales (publicaciones, likes)
- Empresas (facturación, inventario)
- Salud (historial médico)
- Ciencia (análisis de datos)

---

### 🔹 ¿Qué lenguaje usan?

En las bases **relacionales**, usamos SQL:

```sql
SELECT nombre FROM clientes WHERE ciudad = 'Lima';
```

Las bases **NoSQL** como MongoDB usan comandos tipo JSON:

```javascript
db.clientes.find({ ciudad: "Lima" });
```

---

### 🔧 ¿Cómo se instala una base de datos?

Vamos a instalar dos: una relacional (MySQL) y una NoSQL (MongoDB).

---

#### ✅ Instalando **MySQL** (base de datos relacional)

**Opción 1: Local (Windows/Linux/Mac)**

1. Ve a [https://dev.mysql.com/downloads/installer/](https://dev.mysql.com/downloads/installer/)
2. Descarga **MySQL Installer**
3. Instala seleccionando: `MySQL Server`, `Workbench`
4. Crea una contraseña para el usuario `root`

**Opción 2: Usando Docker**

```bash
docker run --name mysql-prueba -e MYSQL_ROOT_PASSWORD=1234 -p 3306:3306 -d mysql
```

---

#### ✅ Instalando **MongoDB** (NoSQL)

**Opción 1: Local**

1. Ve a [https://www.mongodb.com/try/download/community](https://www.mongodb.com/try/download/community)
2. Descarga e instala MongoDB Community
3. Abre MongoDB Compass para ver tus colecciones visualmente

**Opción 2: Docker**

```bash
docker run --name mongo-prueba -p 27017:27017 -d mongo
```

---

### 🧪 Ejemplo completo: Base de datos de una tienda online

#### ✅ Usaremos MySQL para una base de datos relacional

---

#### 🎯 Escenario

Queremos guardar:

- Clientes
- Productos
- Pedidos

---

#### 📦 Estructura

```sql
-- Crear base de datos
CREATE DATABASE tienda;

-- Usar base
USE tienda;

-- Crear tabla clientes
CREATE TABLE clientes (
  id INT AUTO_INCREMENT PRIMARY KEY,
  nombre VARCHAR(100),
  ciudad VARCHAR(100)
);

-- Crear tabla productos
CREATE TABLE productos (
  id INT AUTO_INCREMENT PRIMARY KEY,
  nombre VARCHAR(100),
  precio DECIMAL(10,2)
);

-- Crear tabla pedidos
CREATE TABLE pedidos (
  id INT AUTO_INCREMENT PRIMARY KEY,
  cliente_id INT,
  producto_id INT,
  cantidad INT,
  FOREIGN KEY (cliente_id) REFERENCES clientes(id),
  FOREIGN KEY (producto_id) REFERENCES productos(id)
);
```

---

#### ➕ Insertamos datos

```sql
INSERT INTO clientes (nombre, ciudad) VALUES ('Gustavo', 'Lima');
INSERT INTO productos (nombre, precio) VALUES ('Laptop', 3000.00);
INSERT INTO pedidos (cliente_id, producto_id, cantidad) VALUES (1, 1, 2);
```

---

#### 🔍 Consultamos

```sql
-- Mostrar pedidos con nombre del cliente y producto
SELECT
  c.nombre AS cliente,
  p.nombre AS producto,
  pd.cantidad
FROM pedidos pd
JOIN clientes c ON pd.cliente_id = c.id
JOIN productos p ON pd.producto_id = p.id;
```

✅ Resultado:

```
cliente  | producto | cantidad
-------- | -------- | --------
Gustavo  | Laptop   | 2
```

---

### 🧠 Conclusión

- Las bases de datos organizan información.
- Pueden ser **relacionales** (tablas y SQL) o **NoSQL** (documentos y JSON).
- Se usan en **casi toda aplicación moderna**.
- Puedes instalarlas localmente o en la nube.
- ¡Saber diseñar y consultar una base de datos es esencial para desarrollo y ciberseguridad!

---

[🔼](#índice)

---

## **1157. Conectando lambdas a una VPC**

### 🧠 ¿Qué es una VPC?

Una **VPC (Virtual Private Cloud)** es una red privada dentro de AWS. Es como tu **propio centro de datos aislado**, donde puedes lanzar servicios como:

- EC2 (servidores)
- RDS (bases de datos)
- Lambdas conectadas a recursos privados

---

### 🐑 ¿Qué es una Lambda?

Una **Lambda** es una función que corre código sin que tengas que administrar servidores. Es parte de la computación sin servidor (**serverless**).

Ejemplo de función Lambda:

```javascript
exports.handler = async (event) => {
  return {
    statusCode: 200,
    body: "Hola mundo desde Lambda",
  };
};
```

---

### 🔗 ¿Por qué conectar una Lambda a una VPC?

Por defecto, una Lambda **no está dentro de tu VPC**. Pero a veces necesitas conectarla a:

- Una base de datos RDS (que solo es accesible desde dentro de la VPC)
- Una instancia EC2
- Un sistema de archivos EFS

👉 **Por eso la conectas a una VPC**.

---

### 📌 Requisitos para conectar Lambda a una VPC

1. Tener una **VPC existente**
2. Tener **subredes privadas** (con una NAT Gateway si quieres acceso a internet)
3. Tener una **Security Group** que permita el tráfico necesario
4. Asignar la **VPC, subredes y security group** a la Lambda

---

### 🧱 Arquitectura básica

```
         Internet
            |
         NAT Gateway
            |
  ---------------------
  | Subred Privada    |
  |  (con Lambda)     |
  |     + RDS         |
  ---------------------
            |
          VPC
```

---

### 🧰 ¿Cómo se instala y configura?

Vamos paso por paso con un ejemplo.

---

### 🛠️ **Ejemplo completo: Lambda accediendo a una base de datos RDS en una VPC**

---

#### Paso 1: Crear una VPC (usando consola o VPC Wizard)

1. Ve a **VPC > Launch VPC Wizard**
2. Elige "VPC with Public and Private Subnets"
3. Crea una VPC llamada `mi-vpc`
4. Verás:

   - Subred pública (con NAT Gateway)
   - Subred privada (donde irá Lambda y RDS)

---

#### Paso 2: Crear una base de datos RDS

1. Ve a **RDS > Create database**
2. Tipo: MySQL o PostgreSQL
3. Red: Selecciona `mi-vpc`
4. Subred: Selecciona grupo de subredes privadas
5. Seguridad:

   - Usa un **Security Group** que permita conexión en el puerto 3306 desde la Lambda

---

#### Paso 3: Crear una Lambda

1. Ve a **Lambda > Create function**
2. Nombre: `lambda-acceso-rds`
3. Tiempo de ejecución: Node.js o Python

---

#### Paso 4: Conectar Lambda a la VPC

1. En tu función Lambda:

   - Ve a la sección **Configuration > VPC**
   - Haz clic en **Edit**
   - Selecciona:

     - **VPC**: `mi-vpc`
     - **Subredes**: las privadas
     - **Security Group**: el que tenga permisos para acceder a RDS

2. Guarda los cambios

---

#### Paso 5: Código de la Lambda para conectarse a RDS

Ejemplo en Node.js (MySQL):

```javascript
const mysql = require("mysql2/promise");

exports.handler = async () => {
  const connection = await mysql.createConnection({
    host: "tu-endpoint-rds",
    user: "admin",
    password: "tu_password",
    database: "mi_base_datos",
  });

  const [rows] = await connection.execute("SELECT NOW() AS hora_actual");
  await connection.end();

  return {
    statusCode: 200,
    body: JSON.stringify(rows[0]),
  };
};
```

---

#### Paso 6: Probar la Lambda

- Ejecuta la función desde AWS Lambda > Test
- Si todo está bien configurado, te devolverá:

```json
{
  "hora_actual": "2025-07-27T00:00:00.000Z"
}
```

---

### 🧠 Consejos clave

- **Lambdas en VPC tardan más en arrancar (cold start)**. Puedes reducirlo usando subredes con NAT Gateway bien configuradas.
- Asegúrate que el **Security Group de la Lambda pueda hablar con el de RDS**.
- Para conectarse a internet desde una Lambda en subred privada, necesitas **NAT Gateway**.

---

### ✅ Conclusión

| Concepto              | Descripción                                                        |
| --------------------- | ------------------------------------------------------------------ |
| VPC                   | Red privada virtual en AWS                                         |
| Lambda                | Función sin servidor                                               |
| ¿Por qué conectarlas? | Acceder a recursos internos como RDS o EC2                         |
| Requisitos            | Subred privada, NAT Gateway (si necesitas internet), SGs correctos |
| Resultado             | Seguridad + conectividad interna                                   |

---

[🔼](#índice)

---

## **1158. Single point of failure**

### 🧠 ¿Qué es un "Single Point of Failure"?

Un **Single Point of Failure (SPOF)** es **un componente único** en un sistema (red, software, hardware, etc.) que, si falla, **hace que todo el sistema deje de funcionar**.

> ⚠️ Si ese único punto falla, **todo se cae**.

---

#### 🔍 Ejemplo simple en la vida real

Imagina una casa con **una sola puerta de entrada**.
Si esa puerta se bloquea o se rompe, **nadie puede entrar ni salir**.

👉 Esa puerta es un **SPOF**.

---

#### 🔧 Ejemplo en tecnología

1. Tienes una aplicación web.
2. Tu base de datos está en **un solo servidor** (sin respaldo).
3. Si ese servidor se cae, **toda tu aplicación deja de funcionar**.

👉 Ese servidor es el **Single Point of Failure**.

---

### 📉 ¿Por qué es malo?

Porque **reduce la disponibilidad y confiabilidad** de tus sistemas. Si dependes de un solo componente, ese es un **riesgo crítico**.

---

### ✅ ¿Cómo evitar un SPOF?

**Diseñando con redundancia y alta disponibilidad**:

| SPOF Común             | Solución para evitarlo                                                   |
| ---------------------- | ------------------------------------------------------------------------ |
| 1 solo servidor web    | Usar varios servidores detrás de un balanceador de carga                 |
| 1 base de datos        | Crear una réplica secundaria (failover)                                  |
| 1 cable de red         | Usar múltiples interfaces y conexiones                                   |
| 1 proveedor en la nube | Tener plan de contingencia multi-cloud o backups fuera de AWS, GCP, etc. |

---

### 🛠️ ¿Cómo se “instala” o configura una solución ante SPOF?

Aunque no es algo que se instale literalmente como un programa, **se previene** implementando arquitectura con **redundancia y distribución**.

---

#### 🎯 Ejemplo completo (con solución)

##### Escenario:

Tienes una aplicación web con este esquema básico:

```
[Cliente] --> [Servidor Web] --> [Base de Datos]
```

Ambos servicios están en **una sola máquina EC2**.

👉 Si EC2 falla, todo se cae = SPOF.

---

#### ✅ Solución: Alta disponibilidad (HA)

Reestructuramos así:

```
              [Cliente]
                  |
          ------------------
         |                  |
  [Servidor Web 1]     [Servidor Web 2]
         |                  |
          ------------------
                  |
      [Load Balancer (ELB)]
                  |
          [Base de Datos principal]
                  |
          [Base de Datos réplica]
```

---

#### 🛠️ Pasos prácticos (con AWS como ejemplo):

1. **EC2 Duplicado**: Tener **2 instancias EC2** con tu aplicación.
2. **Balanceador de carga (ELB)**:
   Configura un ELB que distribuya tráfico entre las 2 EC2.
3. **Base de datos con réplica (RDS)**:
   Configura tu base de datos RDS con una **instancia de réplica en otra zona de disponibilidad (AZ)**.
4. **Auto Scaling**:
   Configura Auto Scaling para lanzar más EC2 si una falla.

---

#### 📋 Código de infraestructura (resumen con Terraform)

```hcl
resource "aws_lb" "app_lb" {
  name               = "app-lb"
  internal           = false
  load_balancer_type = "application"
  subnets            = ["subnet-1", "subnet-2"]
}

resource "aws_autoscaling_group" "web_asg" {
  launch_configuration = aws_launch_configuration.web_config.name
  min_size              = 2
  max_size              = 4
  vpc_zone_identifier   = ["subnet-1", "subnet-2"]
}
```

Este código crea un balanceador y un grupo de instancias escalables: si una EC2 cae, otra toma su lugar.

---

### 🧠 Conclusión

| Concepto  | Explicación                                          |
| --------- | ---------------------------------------------------- |
| SPOF      | Componente único cuya falla detiene todo el sistema  |
| Problema  | Riesgo de caída completa y pérdida de disponibilidad |
| Solución  | Redundancia, failover, balanceadores, backups        |
| Resultado | Sistema más resiliente, disponible y profesional     |

---

[🔼](#índice)

---

## **1159. Configurando Auth**

### 🧠 ¿Qué es "Auth"?

**Auth** (abreviatura de _Authentication_) es el **proceso de verificar la identidad de un usuario**.

👉 En otras palabras, es cómo un sistema confirma que tú eres quien dices ser.

> Ejemplos comunes:

- Iniciar sesión con usuario y contraseña
- Iniciar sesión con Google, GitHub, etc.
- Usar tokens o llaves API

---

### 🧱 Tipos de Autenticación

| Tipo de Auth         | Ejemplo fácil                                  |
| -------------------- | ---------------------------------------------- |
| Usuario y contraseña | Login tradicional (como en Facebook)           |
| Token JWT            | Apps modernas con frontend y backend separados |
| OAuth2               | Login con Google, GitHub, etc.                 |
| MFA / 2FA            | Segundo paso como código SMS o app             |

---

### 🔒 ¿Qué es lo que NO es Auth?

**Auth ≠ Authorization**

- **Authentication**: ¿Quién eres?
- **Authorization**: ¿Qué puedes hacer?

---

### 🛠️ ¿Cómo se instala o configura Auth?

Vamos a ver cómo hacerlo en un proyecto típico de **Node.js + Express + MongoDB**, usando **JWT (JSON Web Tokens)** para autenticación.

---

### ✅ PASOS para configurar Auth con JWT

#### 1. 🔧 Instala los paquetes necesarios

```bash
npm install express bcryptjs jsonwebtoken mongoose dotenv
```

---

#### 2. 📁 Estructura del proyecto recomendada

```
/auth-api
│
├── .env
├── server.js
├── config/
│   └── db.js
├── models/
│   └── User.js
├── routes/
│   └── auth.js
├── middleware/
│   └── authMiddleware.js
```

---

#### 3. 🌱 Código de ejemplo

##### `config/db.js` – Conexión a MongoDB

```js
const mongoose = require("mongoose");

const connectDB = async () => {
  await mongoose.connect(process.env.MONGO_URI);
  console.log("MongoDB conectado");
};

module.exports = connectDB;
```

---

##### `models/User.js` – Esquema de usuario

```js
const mongoose = require("mongoose");

const userSchema = new mongoose.Schema({
  email: { type: String, required: true, unique: true },
  password: { type: String, required: true },
});

module.exports = mongoose.model("User", userSchema);
```

---

##### `routes/auth.js` – Rutas de login y registro

```js
const express = require("express");
const bcrypt = require("bcryptjs");
const jwt = require("jsonwebtoken");
const User = require("../models/User");
const router = express.Router();

// Registro
router.post("/register", async (req, res) => {
  const { email, password } = req.body;
  const hashed = await bcrypt.hash(password, 10);
  const user = await User.create({ email, password: hashed });
  res.json({ message: "Usuario creado", userId: user._id });
});

// Login
router.post("/login", async (req, res) => {
  const { email, password } = req.body;
  const user = await User.findOne({ email });
  if (!user) return res.status(400).json({ error: "Usuario no encontrado" });

  const isMatch = await bcrypt.compare(password, user.password);
  if (!isMatch) return res.status(401).json({ error: "Contraseña incorrecta" });

  const token = jwt.sign({ userId: user._id }, process.env.JWT_SECRET, {
    expiresIn: "1h",
  });

  res.json({ token });
});

module.exports = router;
```

---

##### `middleware/authMiddleware.js` – Protege rutas

```js
const jwt = require("jsonwebtoken");

const auth = (req, res, next) => {
  const token = req.header("Authorization")?.split(" ")[1];
  if (!token) return res.status(401).json({ error: "No autorizado" });

  try {
    const decoded = jwt.verify(token, process.env.JWT_SECRET);
    req.user = decoded;
    next();
  } catch (err) {
    res.status(400).json({ error: "Token inválido" });
  }
};

module.exports = auth;
```

---

##### `server.js` – Código principal

```js
require("dotenv").config();
const express = require("express");
const connectDB = require("./config/db");
const authRoutes = require("./routes/auth");

const app = express();
app.use(express.json());

connectDB();

app.use("/api/auth", authRoutes);

app.listen(3000, () => console.log("Servidor en puerto 3000"));
```

---

##### `.env` – Variables de entorno

```
MONGO_URI=mongodb://localhost:27017/auth_example
JWT_SECRET=miclavesecreta123
```

---

### 🚀 Prueba completa (ejemplo)

#### 📝 1. Registrar usuario

```bash
curl -X POST http://localhost:3000/api/auth/register \
-H "Content-Type: application/json" \
-d '{"email": "guss@dev.com", "password": "123456"}'
```

📦 Respuesta:

```json
{ "message": "Usuario creado", "userId": "64ee..." }
```

---

#### 🔐 2. Iniciar sesión

```bash
curl -X POST http://localhost:3000/api/auth/login \
-H "Content-Type: application/json" \
-d '{"email": "guss@dev.com", "password": "123456"}'
```

📦 Respuesta:

```json
{ "token": "eyJhbGciOiJI..." }
```

---

#### 🛡️ 3. Acceder a una ruta protegida

```js
// en alguna ruta protegida:
router.get("/perfil", auth, (req, res) => {
  res.json({ user: req.user });
});
```

```bash
curl -H "Authorization: Bearer eyJhbGciOi..." http://localhost:3000/api/auth/perfil
```

📦 Respuesta:

```json
{ "user": { "userId": "64ee..." } }
```

---

### 🎓 Conclusión

| Parte               | Descripción                                                  |
| ------------------- | ------------------------------------------------------------ |
| ¿Qué es Auth?       | Verificar quién es el usuario                                |
| ¿Cómo se configura? | Usando bcrypt (para passwords) + JWT (para tokens)           |
| ¿Para qué sirve?    | Para asegurar que solo usuarios legítimos accedan            |
| ¿Dónde se usa?      | En toda app moderna: e-commerce, banca, redes sociales, etc. |
| Ejemplo final       | App Node.js con registro, login y ruta protegida con token   |

---

[🔼](#índice)

---

## **1160. Creando un lambda Authorizer**

### 🧠 ¿Qué es un Lambda Authorizer?

Es una función **AWS Lambda** que se **usa para autorizar** peticiones a una **API en API Gateway**, **antes de que lleguen a tu backend** (otra Lambda, ECS, etc.).

👉 Sirve como una **puerta de entrada** para decidir si una solicitud **puede o no** acceder a un endpoint.

---

#### 📘 Ejemplo simple para entender:

- Usuario quiere acceder a `GET /api/usuarios`
- Envía un **token en el header**
- Antes de ejecutar la API, se invoca la **Lambda Authorizer**
- Esta Lambda **verifica el token**
- Si el token es válido, la petición continúa
- Si es inválido, API Gateway **bloquea la solicitud**

---

### 🧱 ¿Cuándo usar Lambda Authorizer?

| Caso de uso                          | ¿Usar Authorizer Lambda?                        |
| ------------------------------------ | ----------------------------------------------- |
| Validar tokens JWT personalizados    | ✅                                              |
| Conectarte a bases de datos o cache  | ✅                                              |
| Controlar roles y permisos complejos | ✅                                              |
| Usar Cognito                         | ❌ (mejor usar Cognito Authorizer directamente) |

---

### 🛠️ ¿Cómo se configura un Lambda Authorizer?

#### Requisitos:

- Cuenta de AWS
- API Gateway REST API
- Lambda creada (la que quieres proteger)
- Crear la Lambda Authorizer

---

### ✅ PASOS

---

#### 1. Crear función Lambda (Authorizer)

##### Código de ejemplo (valida JWT):

```js
// Authorizer Lambda
const jwt = require("jsonwebtoken");

exports.handler = async (event) => {
  const token = event.authorizationToken;

  if (!token || !token.startsWith("Bearer ")) {
    throw "Unauthorized";
  }

  try {
    const tokenValue = token.split(" ")[1];
    const decoded = jwt.verify(tokenValue, "clave_secreta_123"); // cambia tu clave

    const policy = generatePolicy(decoded.sub, "Allow", event.methodArn);
    return policy;
  } catch (err) {
    console.log("Token inválido:", err);
    throw "Unauthorized";
  }
};

// Generar política de acceso
const generatePolicy = (principalId, effect, resource) => {
  return {
    principalId,
    policyDocument: {
      Version: "2012-10-17",
      Statement: [
        {
          Action: "execute-api:Invoke",
          Effect: effect,
          Resource: resource,
        },
      ],
    },
  };
};
```

> ✅ Este Lambda espera un header: `Authorization: Bearer TOKEN`

---

#### 2. Crear la API en API Gateway

1. Ve a **API Gateway**
2. Crea una **REST API**
3. Agrega un **endpoint** (ej. `/usuarios`, método `GET`)
4. Selecciona como backend tu **Lambda protegida**

---

#### 3. Crear el Lambda Authorizer

1. En API Gateway, ve a tu API
2. En la sección izquierda, haz clic en **Authorizers**
3. Clic en **Create New Authorizer**
4. Configura:

   - **Name**: `MiJWTAuth`
   - **Type**: Lambda
   - **Lambda Function**: elige la Lambda Authorizer creada
   - **Token Source**: `method.request.header.Authorization`

✅ Guarda los cambios

---

#### 4. Asociar el Authorizer al endpoint

1. Ve al endpoint (ej. `GET /usuarios`)
2. En la pestaña **Method Request**, en `Authorization`, selecciona `MiJWTAuth`
3. Guarda y vuelve a desplegar tu API (`Actions > Deploy API`)

---

### 🧪 Prueba con Postman o curl

#### ✅ Solicitud con token válido

```bash
curl -H "Authorization: Bearer <TOKEN_VALIDO>" https://mi-api-id.execute-api.us-east-1.amazonaws.com/dev/usuarios
```

👉 Devuelve la respuesta del backend.

---

#### ❌ Solicitud sin token o token inválido

```bash
curl https://mi-api-id.execute-api.us-east-1.amazonaws.com/dev/usuarios
```

📦 Respuesta:

```json
{
  "message": "Unauthorized"
}
```

---

### 🧑‍💻 Ejemplo completo

#### Situación:

- Estás construyendo una API con `/usuarios`
- Quieres protegerla con tokens JWT
- Usas Node.js para la función backend y el authorizer

#### Flujo:

1. El cliente hace login (desde otra app o backend) y recibe un token JWT.
2. Para acceder a `/usuarios`, debe enviar ese token en el header.
3. API Gateway invoca la **Lambda Authorizer**.
4. Si el token es válido:

   - API Gateway deja pasar la solicitud a la Lambda backend.

5. Si no es válido:

   - API Gateway corta la ejecución y responde con `401 Unauthorized`.

---

### 📚 Conclusión

| Parte            | Descripción                                                            |
| ---------------- | ---------------------------------------------------------------------- |
| ¿Qué es?         | Lambda personalizada que decide si una solicitud puede ejecutarse o no |
| ¿Para qué sirve? | Validar tokens, roles o permisos complejos                             |
| ¿Cómo funciona?  | Se ejecuta ANTES del backend en API Gateway                            |
| ¿Dónde se usa?   | En APIs protegidas con JWT o sistemas propios de autenticación         |
| Ejemplo práctico | Lambda que valida JWT y devuelve una policy                            |

---

[🔼](#índice)

---

## **1161. Secretos y API Keys**

### 🧠 ¿Qué son?

- **Secretos**: Son datos confidenciales como **contraseñas**, **tokens**, **certificados**, claves privadas, etc., que se usan para conectarse a otros servicios.
- **API Keys**: Son un tipo de secreto: claves únicas que se usan para **autenticar y autorizar** a un cliente (por ejemplo, tu frontend o backend) para usar una **API**.

#### 📦 Ejemplos de secretos:

- `DB_PASSWORD=MiSuperClave123`
- `JWT_SECRET=abc123xyz`
- `MAIL_SERVICE_API_KEY=SG.skfnd823...`

---

### 🕵️‍♂️ ¿Por qué son importantes?

Porque si los secretos quedan **expuestos** (por ejemplo, subidos a GitHub o mostrados en consola), alguien puede:

- Acceder a tu base de datos
- Enviar correos falsos desde tu app
- Usar tus servicios de pago o almacenamiento (¡y gastar tu dinero!)

---

### 📛 ¿Dónde **NO** se deben poner?

❌ Nunca debes colocar secretos:

- Directamente en tu código (`const password = "123456"`)
- En archivos públicos (`.js`, `.html`, etc.)
- En el frontend (¡incluso si es React o Angular!)
- En repositorios sin control

---

### ✅ ¿Cómo se deben manejar?

| Forma Segura                       | Ejemplo                                               |
| ---------------------------------- | ----------------------------------------------------- |
| Variables de entorno               | `.env`, `process.env.JWT_SECRET`                      |
| Secret Managers (como AWS Secrets) | AWS Secrets Manager, HashiCorp Vault, Azure Key Vault |
| Almacenamiento cifrado             | Guardar y leer secretos de un archivo cifrado         |
| Contextos en CI/CD                 | GitHub Actions secrets, GitLab CI/CD variables, etc.  |

---

### 🔧 ¿Cómo se "instalan" o configuran?

#### 💻 Opción 1: Variables de entorno (local)

1. Crea un archivo `.env`:

```env
DB_HOST=localhost
DB_USER=admin
DB_PASS=SuperClaveSecreta123
```

2. En tu backend Node.js:

```js
require("dotenv").config();

console.log(process.env.DB_USER); // admin
```

> 🧪 Asegúrate de agregar `.env` a tu `.gitignore`

---

#### ☁️ Opción 2: Gestores de secretos en la nube (ej: AWS Secrets Manager)

##### Ventajas:

- Cifrado automático
- Control de acceso (IAM)
- Rotación de claves automática

##### Pasos:

1. Ve a [AWS Secrets Manager](https://console.aws.amazon.com/secretsmanager/)
2. Crea un nuevo secreto:

   - Tipo: `Other type of secret`
   - Claves: `DB_USER`, `DB_PASS`

3. Dale un nombre, por ejemplo: `miapp/credenciales-db`
4. En tu código (Node.js + SDK AWS):

```js
const AWS = require("aws-sdk");
const client = new AWS.SecretsManager({ region: "us-east-1" });

async function getSecrets() {
  const secret = await client
    .getSecretValue({ SecretId: "miapp/credenciales-db" })
    .promise();
  const parsed = JSON.parse(secret.SecretString);
  console.log(parsed.DB_USER, parsed.DB_PASS);
}
getSecrets();
```

---

### 🔐 ¿Cómo proteger una API Key?

1. **Nunca la pongas en el frontend**
2. Usa un **proxy o backend** que la consuma
3. Restringe el uso por IP, dominio o cuota (si el proveedor lo permite)
4. Rota las claves regularmente

---

### ✅ Ejemplo completo

#### 🧩 Escenario:

Tienes un sitio web que permite enviar correos usando SendGrid y necesitas guardar la **API Key** sin exponerla.

#### Paso 1: Crea `.env`

```env
SENDGRID_API_KEY=SG.Djskfnd8293ldjasdf...
```

#### Paso 2: Backend en Node.js

```js
require("dotenv").config();
const sgMail = require("@sendgrid/mail");

sgMail.setApiKey(process.env.SENDGRID_API_KEY);

const enviarCorreo = async () => {
  const msg = {
    to: "destinatario@correo.com",
    from: "miapp@correo.com",
    subject: "¡Hola desde mi app!",
    text: "Este correo fue enviado de forma segura.",
  };

  try {
    await sgMail.send(msg);
    console.log("Correo enviado ✅");
  } catch (error) {
    console.error("Error al enviar:", error.response.body);
  }
};

enviarCorreo();
```

#### Resultado:

- La clave **nunca se expone**
- Se accede de forma segura con `process.env`
- Puedes cambiar la clave sin tocar el código

---

### 🚨 Bonus: Cómo detectar secretos expuestos

- Usa herramientas como:

  - [`git-secrets`](https://github.com/awslabs/git-secrets)
  - [`truffleHog`](https://github.com/trufflesecurity/trufflehog)
  - [`gitleaks`](https://github.com/gitleaks/gitleaks)

---

### 📚 Resumen

| Concepto            | Descripción                                            |
| ------------------- | ------------------------------------------------------ |
| Secretos            | Información confidencial (claves, tokens, contraseñas) |
| API Keys            | Claves que autentican clientes frente a APIs           |
| Manejo correcto     | Variables de entorno, Secret Managers, cifrado         |
| Nunca exponer       | No colocarlas en código, frontend o repositorios       |
| Herramientas útiles | dotenv, AWS Secrets Manager, GitHub Actions Secrets    |

---

[🔼](#índice)

---

## **1162. Creando Endpoints**

### 🧠 ¿Qué es un Endpoint?

Un **endpoint** es una **URL específica** en tu servidor o API donde un cliente (como un navegador o una app móvil) puede enviar o recibir datos.

#### 🗂️ Ejemplo de endpoints:

| Verbo HTTP | Endpoint        | Acción                     |
| ---------- | --------------- | -------------------------- |
| `GET`      | `/productos`    | Obtener lista de productos |
| `GET`      | `/producto/:id` | Obtener producto por ID    |
| `POST`     | `/producto`     | Crear un nuevo producto    |
| `PUT`      | `/producto/:id` | Actualizar un producto     |
| `DELETE`   | `/producto/:id` | Eliminar un producto       |

---

### 🛠️ ¿Cómo se crean?

Se crean en el backend (servidor) usando un **framework web** como:

- Node.js → Express.js
- Python → Flask o FastAPI
- PHP → Laravel
- Java → Spring Boot
- Ruby → Rails

---

### ✅ Ejemplo fácil con **Node.js + Express**

#### 🧪 Instalación:

1. Crea un proyecto Node.js:

```bash
mkdir mi-api
cd mi-api
npm init -y
npm install express
```

2. Crea un archivo llamado `index.js`:

```js
const express = require("express");
const app = express();
const PORT = 3000;

app.use(express.json()); // Permite recibir JSON

// Endpoint GET para productos
app.get("/productos", (req, res) => {
  res.json([
    { id: 1, nombre: "Laptop" },
    { id: 2, nombre: "Mouse" },
  ]);
});

// Endpoint GET con parámetro
app.get("/producto/:id", (req, res) => {
  const { id } = req.params;
  res.json({ id, nombre: `Producto con ID ${id}` });
});

// Endpoint POST para agregar un producto
app.post("/producto", (req, res) => {
  const nuevoProducto = req.body;
  res.status(201).json({ mensaje: "Producto creado", producto: nuevoProducto });
});

// Endpoint PUT para actualizar producto
app.put("/producto/:id", (req, res) => {
  const { id } = req.params;
  const actualizado = req.body;
  res.json({ mensaje: `Producto ${id} actualizado`, datos: actualizado });
});

// Endpoint DELETE para eliminar producto
app.delete("/producto/:id", (req, res) => {
  const { id } = req.params;
  res.json({ mensaje: `Producto ${id} eliminado` });
});

// Servidor escuchando
app.listen(PORT, () => {
  console.log(`Servidor en http://localhost:${PORT}`);
});
```

3. Ejecuta tu servidor:

```bash
node index.js
```

---

### 🧪 Prueba con Postman o navegador:

- `GET http://localhost:3000/productos` → ver productos
- `GET http://localhost:3000/producto/2` → ver producto 2
- `POST http://localhost:3000/producto`
  con cuerpo JSON:

  ```json
  {
    "id": 3,
    "nombre": "Teclado"
  }
  ```

---

### 📚 Resumen

| Concepto     | Descripción                                         |
| ------------ | --------------------------------------------------- |
| Endpoint     | Punto de acceso a un recurso en una API o servidor  |
| Verbo HTTP   | Indica la acción (GET, POST, PUT, DELETE, etc.)     |
| Ejemplo      | `/productos`, `/producto/:id`                       |
| Uso          | Backend para recibir o enviar datos a clientes      |
| Herramientas | Express (Node), Flask (Python), Laravel (PHP), etc. |

---

### 🧩 Ejemplo completo: API simple para usuarios

```js
// archivo: usuarios.js
const express = require("express");
const app = express();
app.use(express.json());

let usuarios = [
  { id: 1, nombre: "Ana" },
  { id: 2, nombre: "Luis" },
];

// GET todos los usuarios
app.get("/usuarios", (req, res) => {
  res.json(usuarios);
});

// POST nuevo usuario
app.post("/usuarios", (req, res) => {
  const nuevo = req.body;
  usuarios.push(nuevo);
  res.status(201).json({ mensaje: "Usuario agregado", nuevo });
});

// DELETE un usuario
app.delete("/usuarios/:id", (req, res) => {
  const { id } = req.params;
  usuarios = usuarios.filter((u) => u.id != id);
  res.json({ mensaje: `Usuario ${id} eliminado` });
});

app.listen(3000, () => console.log("API corriendo en http://localhost:3000"));
```

---

[🔼](#índice)

---

## **1163. Evitando Cross Site Scripting o XSS**

### 📌 ¿Qué es XSS?

**XSS (Cross-Site Scripting)** es una vulnerabilidad de seguridad web que permite a un atacante **inyectar código JavaScript malicioso** en páginas vistas por otros usuarios.

> ⚠️ Este ataque puede robar cookies, secuestrar sesiones, redirigir a sitios maliciosos o manipular el DOM de una página.

---

### 🧠 Tipos de XSS

1. **XSS Reflejado:** el script malicioso se envía como parte de la URL o formulario.

   - Se ejecuta solo si el usuario hace clic en un enlace con ese script.

2. **XSS Almacenado:** el código se guarda en la base de datos o backend y se ejecuta cada vez que alguien visita la página afectada.

   - Muy peligroso.

3. **XSS DOM-based:** el ataque se inyecta y ejecuta en el navegador directamente a través de la manipulación del DOM.

---

### 💥 Ejemplo sencillo de ataque XSS

Supongamos que tienes una página que muestra el nombre del usuario:

```html
<!-- página: saludo.html -->
<p>Hola, <span id="nombreUsuario"></span></p>

<script>
  const params = new URLSearchParams(window.location.search);
  const nombre = params.get("nombre");
  document.getElementById("nombreUsuario").innerHTML = nombre;
</script>
```

Si accedes a esta URL:

```
http://misitio.com/saludo.html?nombre=<script>alert('Hackeado')</script>
```

👉 ¡El código malicioso se ejecutará! (`alert('Hackeado')`).

---

### 🔐 ¿Cómo evitar XSS?

#### ✅ 1. Escapar la salida

Nunca insertes datos sin sanear directamente en el HTML. Usa funciones para **escapar caracteres peligrosos**.

Ejemplo en JavaScript:

```js
function escaparHTML(texto) {
  return texto
    .replace(/&/g, "&amp;")
    .replace(/</g, "&lt;")
    .replace(/>/g, "&gt;")
    .replace(/"/g, "&quot;")
    .replace(/'/g, "&#039;");
}

const nombreSeguro = escaparHTML(nombre);
document.getElementById("nombreUsuario").innerHTML = nombreSeguro;
```

---

#### ✅ 2. Usar frameworks modernos

Frameworks como React, Angular, Vue **protegen automáticamente** contra XSS porque escapan el HTML por defecto.

```jsx
function Saludo({ nombre }) {
  return <p>Hola, {nombre}</p>; // React escapa automáticamente
}
```

---

#### ✅ 3. Validar y sanitizar datos en el backend

**En Node.js con Express**, puedes usar la librería `express-validator` o `DOMPurify`.

```bash
npm install dompurify jsdom
```

```js
const createDOMPurify = require("dompurify");
const { JSDOM } = require("jsdom");

const window = new JSDOM("").window;
const DOMPurify = createDOMPurify(window);

const entradaSegura = DOMPurify.sanitize(usuarioInput);
```

---

#### ✅ 4. Usar encabezados de seguridad (HTTP Headers)

Usa el middleware `helmet` para prevenir ataques XSS.

```bash
npm install helmet
```

```js
const helmet = require("helmet");
app.use(helmet()); // Configura cabeceras HTTP seguras
```

---

#### ✅ 5. Content Security Policy (CSP)

Es una cabecera HTTP que **bloquea scripts no autorizados**.

```js
app.use(
  helmet.contentSecurityPolicy({
    directives: {
      defaultSrc: ["'self'"],
      scriptSrc: ["'self'"],
    },
  })
);
```

---

### 🧩 Ejemplo completo en Node.js + Express

```bash
npm init -y
npm install express helmet
```

```js
// archivo: app.js
const express = require("express");
const helmet = require("helmet");
const app = express();

app.use(helmet());
app.use(express.urlencoded({ extended: true }));
app.use(express.json());

function escaparHTML(texto) {
  return texto
    .replace(/&/g, "&amp;")
    .replace(/</g, "&lt;")
    .replace(/>/g, "&gt;")
    .replace(/"/g, "&quot;")
    .replace(/'/g, "&#039;");
}

app.get("/saludo", (req, res) => {
  const nombre = req.query.nombre || "Invitado";
  const nombreSeguro = escaparHTML(nombre);

  res.send(`<h1>Hola, ${nombreSeguro}</h1>`);
});

app.listen(3000, () => {
  console.log("Servidor corriendo en http://localhost:3000");
});
```

---

#### ✅ Prueba:

- Abre en el navegador:

```
http://localhost:3000/saludo?nombre=Gustavo
```

- Ahora prueba con:

```
http://localhost:3000/saludo?nombre=<script>alert('Hackeado')</script>
```

👉 Verás que el script no se ejecuta. ¡Está escapado y neutralizado!

---

### 🎓 Resumen

| Medida                   | ¿Para qué sirve?                                        |
| ------------------------ | ------------------------------------------------------- |
| Escapar HTML             | Evita ejecución de scripts al mostrar datos del usuario |
| Validar datos de entrada | Evita entrada maliciosa desde formularios o URLs        |
| Usar frameworks seguros  | React, Angular, etc. protegen automáticamente           |
| Helmet + CSP             | Configura cabeceras HTTP seguras contra XSS             |
| Sanitizar contenido      | Limpia entradas potencialmente maliciosas               |

---

[🔼](#índice)

---

## **1164. Validando la integridad de los datos con tokens**

### 🧠 ¿Qué significa "integridad de los datos"?

La **integridad** asegura que los datos **no han sido modificados, dañados ni manipulados** entre el momento en que se crearon y el momento en que se usan/verifican.

> Por ejemplo, si alguien modifica tu correo en un enlace de verificación, y el sistema lo acepta, tu seguridad está en riesgo.

---

### 🧩 ¿Qué es un token?

Un **token** es un trozo de información **firmado digitalmente** (a veces también cifrado), que contiene datos que queremos proteger o verificar.

- 🔑 Normalmente incluye una **firma digital (hash)** que garantiza que **nadie lo ha modificado**.
- 🎟️ Si alguien cambia un solo byte, la firma ya no coincidirá y el sistema lo rechazará.

---

### 💡 ¿Qué tipos de tokens existen?

| Tipo                 | Uso común                                         |
| -------------------- | ------------------------------------------------- |
| JWT (JSON Web Token) | Autenticación y transmisión segura de datos       |
| CSRF Tokens          | Evitar ataques de tipo Cross-Site Request Forgery |
| HMAC tokens          | Validación de integridad en APIs o URL firmadas   |
| Tokens antifraude    | Confirmar acciones como pagos o accesos sensibles |

---

### 🔐 ¿Cómo protege un token la integridad?

Veamos un ejemplo con un token tipo JWT:

```json
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.
eyJ1c3VhcmlvIjoiZ3VzdGF2byIsInJvbCI6ImFkbWluIn0.
9k9f1WVrD6Rn3a9g1dzMoFZz23IOAH2aHRKlq7T35C0
```

Este token tiene 3 partes:

1. **Header** (algoritmo y tipo)
2. **Payload** (datos: usuario, rol, etc.)
3. **Firma** (firmado con una clave secreta)

🔐 Si alguien intenta cambiar el payload para decir `"rol": "admin"`, la firma dejará de coincidir → el servidor lo rechazará.

---

### 🛠️ ¿Cómo se "instala" esto?

#### Necesitas:

- Un backend (por ejemplo: Node.js + Express)
- Una librería para crear/verificar tokens (`jsonwebtoken`)

---

### 🧪 Ejemplo completo: Node.js + JWT

#### 1. Instalar dependencias

```bash
npm init -y
npm install express jsonwebtoken
```

#### 2. Crear archivo `server.js`

```js
const express = require("express");
const jwt = require("jsonwebtoken");
const app = express();

const CLAVE_SECRETA = "clave-ultra-secreta";

app.use(express.json());

// Ruta para generar un token
app.post("/login", (req, res) => {
  const usuario = req.body.usuario;

  // ⚠️ Aquí debería haber autenticación real (omitida por simplicidad)
  const token = jwt.sign({ usuario: usuario }, CLAVE_SECRETA, {
    expiresIn: "1h",
  });

  res.json({ token });
});

// Ruta protegida
app.get("/datos-protegidos", (req, res) => {
  const token = req.headers.authorization?.split(" ")[1];

  if (!token) return res.status(401).json({ error: "Token requerido" });

  try {
    const data = jwt.verify(token, CLAVE_SECRETA);
    res.json({ mensaje: `Hola ${data.usuario}, tus datos están protegidos.` });
  } catch (err) {
    res.status(403).json({ error: "Token inválido o modificado" });
  }
});

app.listen(3000, () => {
  console.log("Servidor corriendo en http://localhost:3000");
});
```

---

#### 3. Probar el flujo

1. Haz un **POST a `/login`** con JSON:

```json
{ "usuario": "gustavo" }
```

2. El servidor devuelve:

```json
{ "token": "eyJhbGci..." }
```

3. Haz un **GET a `/datos-protegidos`** con ese token en la cabecera:

```
Authorization: Bearer eyJhbGci...
```

👉 Si todo está correcto, verás:

```
Hola gustavo, tus datos están protegidos.
```

❌ Si alguien modifica el token, verás:

```
Token inválido o modificado
```

---

### 🔐 ¿Dónde más se usa esto?

- 🔗 **Enlaces de recuperación de contraseña** firmados con tokens
- ✅ **Confirmación de correo electrónico**
- 💳 **Pagos online temporales**
- 🌐 **Verificación de identidad en APIs**

---

### ✅ Resumen visual

| Elemento                       | Función                                            |
| ------------------------------ | -------------------------------------------------- |
| Token (ej. JWT)                | Lleva datos firmados que no pueden ser modificados |
| Firma digital (hash)           | Garantiza la integridad                            |
| Clave secreta                  | Protege la firma; solo el servidor puede validarla |
| Librerías (jsonwebtoken, etc.) | Ayudan a crear y validar tokens fácilmente         |

---

[🔼](#índice)

---

## **1165. Conociendo la naturaleza de los datos**

### 🧠 ¿Qué significa esto?

Significa **entender el tipo de información** que manejas para poder **clasificarla, protegerla y procesarla** de forma correcta. No todos los datos son iguales ni requieren el mismo nivel de protección.

---

### 🎯 ¿Por qué es importante?

Antes de proteger datos, debes saber:

- ¿Qué tipo de datos estás manejando?
- ¿Son sensibles? ¿Públicos? ¿Confidenciales?
- ¿Qué impacto tendría si se pierden o son robados?

Esto es clave en áreas como:

- Ciberseguridad 🔐
- Protección de datos personales (como GDPR, Ley de Datos Personales en Perú) 📜
- Seguridad informática y forense 🧪
- Desarrollo seguro de software 💻

---

### 🗂️ Tipos comunes de datos (con ejemplos)

| Tipo de dato         | Ejemplos                                              | Sensibilidad |
| -------------------- | ----------------------------------------------------- | ------------ |
| 📄 Datos personales  | Nombre, DNI, dirección, teléfono                      | Alta         |
| 🏥 Datos sensibles   | Salud, religión, orientación sexual                   | Muy alta     |
| 💳 Datos financieros | Tarjeta de crédito, cuentas bancarias                 | Muy alta     |
| 📧 Datos internos    | Correos internos, planes empresariales                | Media a alta |
| 🌐 Datos públicos    | Información del sitio web, blogs, documentos públicos | Baja         |
| 📁 Datos técnicos    | Logs, direcciones IP, configuración de red            | Variable     |

---

### 🔍 ¿Qué hacemos con esta clasificación?

- **Asignamos niveles de seguridad**: por ejemplo, encriptar datos sensibles.
- **Aplicamos controles de acceso**: solo ciertas personas pueden ver ciertos datos.
- **Definimos políticas de retención**: cuánto tiempo se guardan y cuándo se eliminan.

---

### 🛠️ ¿Cómo se "instala" o aplica este concepto?

Esto no se instala como un software, pero sí se **implementa como parte de una política y arquitectura de seguridad**. Por ejemplo:

#### 1. Clasificación de datos

Puedes etiquetar archivos y bases de datos:

- `público`, `confidencial`, `sensible`
- Esto puede hacerse manualmente o con software de DLP (Data Loss Prevention)

#### 2. Cifrado de datos

- Cifrar los datos sensibles antes de almacenarlos o enviarlos.
- En bases de datos, puedes usar campos encriptados (como en MongoDB o SQL Server).

#### 3. Accesos diferenciados

- En una app, usuarios normales no pueden ver datos financieros, pero un rol “admin sí”.

---

### ✅ Ejemplo completo (Desarrollo Web + Seguridad)

#### Supón que estás desarrollando una app de salud con 3 tipos de datos:

1. Nombre del paciente
2. Diagnóstico médico
3. Blog de consejos de salud

#### Paso 1: Clasificarlos

| Dato                | Naturaleza | Acción de seguridad                 |
| ------------------- | ---------- | ----------------------------------- |
| Nombre del paciente | Personal   | Cifrado + Autenticación             |
| Diagnóstico médico  | Sensible   | Cifrado fuerte + Acceso restringido |
| Blog de consejos    | Público    | No requiere protección extra        |

---

#### Paso 2: Código en Node.js que aplica cifrado a datos sensibles

```bash
npm install express mongoose dotenv crypto-js
```

#### `server.js`

```js
require("dotenv").config();
const express = require("express");
const mongoose = require("mongoose");
const CryptoJS = require("crypto-js");

const app = express();
app.use(express.json());

mongoose.connect("mongodb://localhost:27017/clinica");

const pacienteSchema = new mongoose.Schema({
  nombre: String,
  diagnostico: String, // Este lo vamos a cifrar
});

const Paciente = mongoose.model("Paciente", pacienteSchema);

// Registrar nuevo paciente (cifrando el diagnóstico)
app.post("/paciente", async (req, res) => {
  const { nombre, diagnostico } = req.body;

  // Cifrado de dato sensible
  const diagnosticoCifrado = CryptoJS.AES.encrypt(
    diagnostico,
    process.env.CLAVE_SECRETA
  ).toString();

  const paciente = new Paciente({ nombre, diagnostico: diagnosticoCifrado });
  await paciente.save();

  res.send("Paciente registrado con datos protegidos");
});

// Obtener paciente y descifrar diagnóstico
app.get("/paciente/:id", async (req, res) => {
  const paciente = await Paciente.findById(req.params.id);
  if (!paciente) return res.status(404).send("No encontrado");

  const diagnosticoDescifrado = CryptoJS.AES.decrypt(
    paciente.diagnostico,
    process.env.CLAVE_SECRETA
  ).toString(CryptoJS.enc.Utf8);

  res.json({
    nombre: paciente.nombre,
    diagnostico: diagnosticoDescifrado,
  });
});

app.listen(3000, () => console.log("Servidor en http://localhost:3000"));
```

#### `.env`

```
CLAVE_SECRETA=clave-super-secreta
```

---

### 🔐 Resultado:

- Se **identificó la naturaleza** de los datos (diagnóstico = sensible).
- Se aplicó **cifrado** solo a los datos que lo necesitan.
- Se mantuvo accesible la parte pública sin protección innecesaria.

---

### 🧠 Conclusión

> “Conocer la naturaleza de los datos” es el **primer paso para aplicar seguridad inteligente.**

No todos los datos se tratan igual. Al identificar qué tipo de dato tienes, puedes:

✅ Protegerlos adecuadamente

✅ Cumplir con regulaciones (como GDPR o la Ley 29733 en Perú)

✅ Evitar sobreproteger (gastar recursos innecesarios)

---

[🔼](#índice)

---

## **1166. Protege tus datos con Key Management Services**

### 🔐 ¿Qué es Key Management Services (KMS)?

**Key Management Services** es un servicio que **genera, almacena y gestiona claves de cifrado** usadas para proteger tus datos. Lo ofrece, por ejemplo:

- **AWS KMS**
- **Azure Key Vault**
- **Google Cloud KMS**

---

### 🧠 ¿Por qué usar un servicio de gestión de claves?

Cuando cifras datos, necesitas una **clave secreta**. Guardar esa clave en tu código o base de datos es **inseguro**.

Por eso, KMS:

✅ Crea claves seguras

✅ Las almacena en un entorno protegido

✅ Te permite usarlas para cifrar y descifrar datos

✅ Controla quién puede usarlas (control de acceso con IAM)

---

### 🔐 ¿Qué tipo de datos puedes proteger?

- Contraseñas
- Números de tarjeta
- Archivos confidenciales
- Tokens JWT
- Datos personales o de salud
- Claves API

---

### 🎯 ¿Cómo funciona KMS (en simple)?

1. Tienes un dato → “123456”
2. Lo envías a KMS con la orden: “Cifra esto”
3. KMS lo cifra y te devuelve: “AGSB12@@a89s...”
4. Luego puedes enviar eso a KMS para descifrarlo
5. ¡Y listo! Nunca ves ni controlas la clave directamente

---

### ⚙️ ¿Cómo se configura (“instala”)?

Usaremos **AWS KMS** como ejemplo.

#### 🔧 Paso 1: Crear una clave en AWS KMS

1. Entra a tu consola de AWS: [https://console.aws.amazon.com/kms](https://console.aws.amazon.com/kms)
2. Ir a **Key Management Service (KMS)**
3. Haz clic en “Crear clave”
4. Tipo: **clave simétrica**
5. Nómbrala (ej. `claveDeCifradoApp`)
6. Asigna permisos (IAM roles o usuarios que pueden usarla)
7. Finaliza y copia el **Key ID**

---

#### 📦 Paso 2: Instalar SDK de AWS

En tu proyecto Node.js:

```bash
npm install @aws-sdk/client-kms dotenv
```

---

#### 🧪 Paso 3: Usar KMS para cifrar/descifrar datos

Creamos un pequeño ejemplo para cifrar el número de una tarjeta de crédito.

---

### ✅ Ejemplo completo: cifrar y descifrar usando AWS KMS en Node.js

#### 📁 `.env`

```env
AWS_REGION=us-east-1
KEY_ID=tu-key-id-aquí
```

#### 📁 `kms-demo.js`

```js
require("dotenv").config();
const {
  KMSClient,
  EncryptCommand,
  DecryptCommand,
} = require("@aws-sdk/client-kms");

const kms = new KMSClient({ region: process.env.AWS_REGION });

async function cifrar(texto) {
  const params = {
    KeyId: process.env.KEY_ID,
    Plaintext: Buffer.from(texto),
  };
  const comando = new EncryptCommand(params);
  const respuesta = await kms.send(comando);
  return respuesta.CiphertextBlob.toString("base64");
}

async function descifrar(cifrado) {
  const params = {
    CiphertextBlob: Buffer.from(cifrado, "base64"),
  };
  const comando = new DecryptCommand(params);
  const respuesta = await kms.send(comando);
  return respuesta.Plaintext.toString();
}

(async () => {
  const textoOriginal = "4111-1111-1111-1111";
  const cifrado = await cifrar(textoOriginal);
  console.log("Cifrado:", cifrado);

  const descifrado = await descifrar(cifrado);
  console.log("Descifrado:", descifrado);
})();
```

---

#### 🔐 Resultado esperado:

```
Cifrado: AQICAHiWTxK5... (una cadena larga)
Descifrado: 4111-1111-1111-1111
```

---

### 🛡️ Beneficios de usar KMS

| Ventaja                 | Explicación                                                                |
| ----------------------- | -------------------------------------------------------------------------- |
| 🔐 Seguridad            | Las claves están en hardware seguro (HSM) y no las puedes ver directamente |
| 👤 Control de acceso    | Solo ciertos roles/usuarios pueden cifrar/descifrar                        |
| 📜 Cumplimiento legal   | Cumples con regulaciones como GDPR o HIPAA                                 |
| 🔄 Rotación automática  | Puedes rotar claves sin afectar datos cifrados                             |
| 🛠️ Integración sencilla | Se conecta fácilmente con otros servicios como S3, RDS, Lambda, etc.       |

---

### 🧠 Conclusión

**Key Management Services** te ayuda a:

- Proteger los datos más delicados 🔐
- Centralizar la gestión de claves 🗝️
- Dar acceso seguro a apps o servicios ⚙️

---

### 📌 ¿Y si no uso la nube?

También puedes usar **Vault de HashiCorp** o **GnuPG** para cifrado local. Pero con la nube, todo es más fácil, escalable y seguro.

---

[🔼](#índice)

---

## **1167. Sistema de logs**

### 📓 ¿Qué es un sistema de logs?

Un **sistema de logs** es un mecanismo que permite **registrar eventos, acciones, errores o cualquier actividad** que ocurre en una aplicación, servidor, red o sistema operativo.

---

### 🧠 ¿Por qué es importante?

1. 🔍 **Monitoreo:** Saber qué ocurre en tu sistema.
2. 🛡️ **Seguridad:** Detectar accesos sospechosos.
3. 🐞 **Depuración:** Identificar errores en el código.
4. 📝 **Auditoría:** Tener trazabilidad para análisis forense o cumplimiento de normas (GDPR, HIPAA, etc).

---

### 📦 Tipos comunes de logs

| Tipo de Log           | ¿Dónde aparece?                                    | ¿Qué registra?                             |
| --------------------- | -------------------------------------------------- | ------------------------------------------ |
| **Sistema operativo** | Linux (`/var/log/syslog`) / Windows (Event Viewer) | Fallos, procesos, hardware, usuarios       |
| **Aplicación web**    | Backend Node.js, Python, etc.                      | Errores, solicitudes HTTP, autenticaciones |
| **Servidor web**      | Apache, Nginx                                      | Peticiones HTTP, IPs, errores              |
| **Seguridad**         | Firewall, antivirus, IDS/IPS                       | Intrusiones, reglas activadas, bloqueos    |
| **Base de datos**     | MySQL, PostgreSQL                                  | Consultas, errores de conexión, bloqueos   |

---

### 🔧 ¿Cómo se implementa un sistema de logs?

#### Ejemplo 1: Logs básicos en una app de Node.js

```js
console.log("Usuario inició sesión");
console.error("Error: no se pudo conectar a la base de datos");
```

Pero esto **no es suficiente**. Necesitamos:

✅ Nivel de severidad (info, error, warn)

✅ Tiempos (timestamps)

✅ Archivos persistentes

✅ Posibilidad de analizarlos

---

### 🛠️ Herramientas populares para gestión de logs

| Herramienta             | Descripción                         |
| ----------------------- | ----------------------------------- |
| **Winston**             | Librería de logging para Node.js    |
| **Log4j**               | Java                                |
| **Fluentd / Logstash**  | Recolección y procesamiento de logs |
| **Graylog / ELK Stack** | Análisis y visualización de logs    |
| **AWS CloudWatch Logs** | Logs de servicios en AWS            |
| **Syslog**              | Estándar en Linux para logging      |

---

### ⚙️ Instalación de un sistema de logs con Winston (Node.js)

#### Paso 1: Instalar Winston

```bash
npm install winston
```

#### Paso 2: Crear el archivo de logging

📁 `logger.js`

```js
const { createLogger, transports, format } = require("winston");

const logger = createLogger({
  level: "info",
  format: format.combine(
    format.timestamp(),
    format.printf(({ level, message, timestamp }) => {
      return `[${timestamp}] ${level.toUpperCase()}: ${message}`;
    })
  ),
  transports: [
    new transports.Console(),
    new transports.File({ filename: "logs/app.log" }),
  ],
});

module.exports = logger;
```

---

### ✅ Ejemplo completo: App que registra eventos y errores

#### 📁 `app.js`

```js
const express = require("express");
const logger = require("./logger");

const app = express();
const PORT = 3000;

app.get("/", (req, res) => {
  logger.info("Ruta principal accedida por el usuario");
  res.send("Bienvenido");
});

app.get("/error", (req, res) => {
  logger.error("Error simulado para pruebas");
  res.status(500).send("Algo falló");
});

app.listen(PORT, () => {
  logger.info(`Servidor corriendo en puerto ${PORT}`);
});
```

---

### 📂 Archivos generados

Cuando accedes a `http://localhost:3000/`, se registrará:

```
[2025-07-27T20:50:30.123Z] INFO: Servidor corriendo en puerto 3000
[2025-07-27T20:50:32.456Z] INFO: Ruta principal accedida por el usuario
```

Y si accedes a `/error`, verás:

```
[2025-07-27T20:51:10.789Z] ERROR: Error simulado para pruebas
```

También puedes ver todo esto en el archivo `logs/app.log`.

---

### 📊 ¿Cómo analizarlos?

Puedes analizar logs con:

- 📈 **ELK Stack (Elasticsearch + Logstash + Kibana)**
- ☁️ **CloudWatch (en AWS)**
- 🧩 **Graylog o Splunk**

Esto permite **buscar eventos, crear dashboards, alertas y más**.

---

### 🧠 Conclusión

Un buen sistema de logs te permite:

✔️ Detectar problemas antes de que escalen

✔️ Identificar brechas de seguridad

✔️ Auditar el comportamiento de usuarios y apps

✔️ Mejorar la calidad del software

---

[🔼](#índice)

---

## **1168. Observabilidad**

### 📌 ¿Qué es Observabilidad?

**Observabilidad** es la **capacidad de entender lo que está ocurriendo dentro de un sistema** solo mirando su salida externa (logs, métricas y trazas).

👉 Es como ser médico y diagnosticar el estado de un paciente midiendo temperatura, presión y escuchando el corazón. En sistemas, usamos:

1. 📄 **Logs** – qué pasó (mensajes de eventos)
2. 📊 **Métricas** – cuántas veces pasó y cuánto demoró
3. 🧵 **Trazas** – cómo viajó una solicitud a través del sistema

---

### 🧠 ¿Para qué sirve?

- 🐞 Detectar errores en producción
- 🔎 Diagnosticar problemas de rendimiento
- 📈 Entender el comportamiento del sistema
- ⚙️ Mejorar la arquitectura basada en datos reales
- 🔐 Prevenir incidentes de seguridad

---

### 🔄 Diferencia con monitoreo

| Monitoreo                  | Observabilidad                   |
| -------------------------- | -------------------------------- |
| Reacciona a fallos         | Permite entender _por qué_ falló |
| Tiene alertas predefinidas | Descubre problemas inesperados   |
| Más superficial            | Más profunda y contextual        |

---

### 🧰 Componentes clave

#### 1. **Logs**

Mensajes que indican qué ocurrió.

```js
console.log("Usuario X inició sesión");
```

#### 2. **Métricas**

Valores numéricos en el tiempo.

```js
requests_per_minute = 100
memory_usage = 512MB
```

#### 3. **Trazas (Traces)**

Viaje completo de una solicitud a través de microservicios.

```plaintext
Usuario → API Gateway → Servicio Auth → Base de datos
```

---

### 🔧 ¿Cómo se instala o implementa la observabilidad?

Depende de si estás en desarrollo local o nube (AWS, GCP, etc.). Aquí va un ejemplo usando **Node.js con Prometheus + Grafana** (local).

---

### ✅ Ejemplo: Observabilidad en Node.js con Prometheus y Grafana

#### Paso 1: Crear un proyecto

```bash
mkdir observabilidad-demo
cd observabilidad-demo
npm init -y
npm install express prom-client
```

#### Paso 2: Código base con métricas

📁 `server.js`

```js
const express = require("express");
const client = require("prom-client");

const app = express();
const collectDefaultMetrics = client.collectDefaultMetrics;
collectDefaultMetrics(); // Métricas como uso de memoria, CPU, etc.

const httpRequestCounter = new client.Counter({
  name: "http_requests_total",
  help: "Número total de solicitudes HTTP",
  labelNames: ["method", "route", "status_code"],
});

app.get("/", (req, res) => {
  httpRequestCounter.inc({ method: "GET", route: "/", status_code: 200 });
  res.send("Hola mundo 🌍");
});

app.get("/metrics", async (req, res) => {
  res.set("Content-Type", client.register.contentType);
  res.end(await client.register.metrics());
});

app.listen(3000, () => {
  console.log("Servidor en http://localhost:3000");
});
```

#### Paso 3: Instalar Prometheus

Crea el archivo de configuración `prometheus.yml`

```yaml
global:
  scrape_interval: 5s

scrape_configs:
  - job_name: "node_app"
    static_configs:
      - targets: ["localhost:3000"]
```

Ejecuta Prometheus:

```bash
./prometheus --config.file=prometheus.yml
```

(Descarga Prometheus desde: [https://prometheus.io/download/](https://prometheus.io/download/))

---

#### Paso 4: Visualizar con Grafana

1. Instala Grafana: [https://grafana.com/grafana/download/](https://grafana.com/grafana/download/)
2. Accede a `http://localhost:3000` (Grafana por defecto)
3. Añade Prometheus como fuente de datos
4. Crea dashboards con las métricas recolectadas

---

### 📊 ¿Qué observarás?

- 🔄 Cantidad de solicitudes por ruta
- ⏱️ Tiempo de respuesta promedio
- 📈 Uso de memoria / CPU
- ⚠️ Alertas por errores 500, latencias altas, etc.

---

### 🧪 ¿Y las trazas?

Para trazas puedes usar herramientas como:

| Herramienta       | Lenguaje     | Descripción                           |
| ----------------- | ------------ | ------------------------------------- |
| **Jaeger**        | Multi        | Visualización de trazas               |
| **OpenTelemetry** | Multi        | Estándar para trazas, métricas y logs |
| **AWS X-Ray**     | AWS (Lambda) | Trazabilidad en servicios AWS         |

---

### ✅ Ejemplo completo: Proyecto Express + Logs + Métricas + Trazas

| Elemento | Herramienta                |
| -------- | -------------------------- |
| Logs     | `winston`                  |
| Métricas | `prom-client` + Prometheus |
| Trazas   | `OpenTelemetry + Jaeger`   |

---

### 🧠 Conclusión

#### 🌟 Observabilidad te permite:

- Ver qué pasa en tiempo real
- Detectar problemas invisibles con solo monitoreo
- Trazar la causa raíz de errores en microservicios
- Hacer ingeniería basada en datos, no suposiciones

---

[🔼](#índice)

---

## **1169. Alertas y Postmortems**

### 🔔 **Alertas**

Son **notificaciones automáticas** que te avisan cuando **algo anormal sucede** en un sistema, como:

- Se cae una web
- Se llena el disco duro
- Aumenta el tiempo de respuesta
- Hay muchos errores 500 en un servicio

👉 Te ayudan a **reaccionar rápido antes que el usuario lo note**.

---

### 📄 **Postmortems**

Después de un incidente o caída, un **postmortem es un informe detallado** donde se analiza:

- Qué pasó
- Por qué pasó
- Cómo se solucionó
- Qué hacer para que no pase de nuevo

👉 Sirve para **aprender del error sin culpas** y **mejorar el sistema**.

---

### 🔧 ¿Cómo se configuran las alertas?

Depende del entorno. Aquí algunos ejemplos:

| Herramienta                             | Uso                              |
| --------------------------------------- | -------------------------------- |
| **Prometheus + Alertmanager**           | Métricas + notificaciones        |
| **Datadog / New Relic / Grafana Cloud** | Observabilidad avanzada          |
| **AWS CloudWatch**                      | En la nube de AWS                |
| **UptimeRobot**                         | Para saber si una web está caída |

---

### 🎯 Ejemplo de una alerta (con Prometheus y Alertmanager)

Supón que quieres recibir una alerta si tu API tarda más de 3 segundos:

**Prometheus Rule (alert.rules.yml):**

```yaml
groups:
  - name: example
    rules:
      - alert: AltaLatencia
        expr: http_request_duration_seconds_average > 3
        for: 1m
        labels:
          severity: warning
        annotations:
          summary: "Alta latencia detectada"
          description: "La API tarda más de 3s en responder"
```

---

### 📥 ¿Dónde llegan las alertas?

Las alertas pueden llegar por:

- 📧 Correo
- 📱 SMS
- 🟢 Slack
- 💬 Telegram
- 👩‍💻 Microsoft Teams
- 📟 PagerDuty u Opsgenie

---

### 🧪 ¿Qué lleva un **Postmortem**?

Un buen postmortem incluye:

| Sección               | Descripción                                                  |
| --------------------- | ------------------------------------------------------------ |
| 🕐 Fecha y hora       | Cuándo empezó y terminó el incidente                         |
| 📌 Descripción        | Qué ocurrió                                                  |
| 🔍 Causa raíz         | Por qué ocurrió                                              |
| 🛠️ Solución inmediata | Qué se hizo para arreglarlo                                  |
| 📈 Impacto            | Cuánto afectó a usuarios o sistemas                          |
| 🧱 Prevención futura  | Qué cambios se implementarán para que no vuelva a pasar      |
| 👥 Responsables       | Quiénes participaron en la resolución (sin buscar culpables) |

---

### 🧾 Ejemplo de **Postmortem sencillo**

```markdown
### Postmortem: Caída del sitio web - 26 de julio 2025

#### 🕐 Tiempo del incidente

- Inicio: 14:05
- Fin: 14:28
- Duración: 23 minutos

#### 📌 Qué pasó

Los usuarios no podían acceder al sitio web principal. Se mostraba error 500.

#### 🔍 Causa raíz

Una actualización de código mal testeada rompió la conexión con la base de datos.

#### 🛠️ Solución inmediata

Se revirtió el despliegue al commit anterior.

#### 📈 Impacto

- 100% de usuarios afectados por 23 minutos
- 40 tickets de soporte generados

#### 🧱 Acciones correctivas

- Añadir pruebas automáticas a esa ruta
- Crear revisión por pares obligatoria antes de hacer deploy

#### 👥 Responsables del análisis

- Gustavo (DevSecOps)
- Carla (Backend)
```

---

### 🚀 ¿Cómo implementar todo esto desde cero?

#### 🔔 Alertas

1. Usa Prometheus para recolectar métricas.
2. Instala Alertmanager para enviar notificaciones.
3. Configura reglas como `expr: error_rate > 0.05`.
4. Prueba con una falla forzada (como parar un servicio).

#### 📄 Postmortems

1. Usa una plantilla fija para todos los incidentes.
2. Almacénalos en Notion, Confluence, Google Docs o Git.
3. Revísalos en retrospectivas mensuales con el equipo.

---

### 💡 Consejos

- Nunca culpes a una persona en un postmortem. Culpa al proceso.
- Automatiza todo lo que puedas (pruebas, alertas, monitoreo).
- Documenta todo para aprender más rápido.

---

### ✅ Ejemplo completo

🎯 **Escenario: API con alta latencia**

- Se detecta que `/login` tarda 6 segundos.
- Prometheus lanza alerta a Slack.
- El equipo revisa y encuentra una consulta SQL sin índice.
- Se soluciona agregando el índice.
- Se documenta el incidente con un postmortem.
- Se agrega una alerta preventiva de latencia > 2s.

---

[🔼](#índice)

---

## **1170. Errores de CORS**

### 🧠 ¿Qué es CORS?

**CORS (Cross-Origin Resource Sharing)** es un **mecanismo de seguridad** que usa el navegador para **controlar qué recursos web pueden ser solicitados desde un dominio distinto al del servidor**.

---

#### ⚠️ En otras palabras:

Si tienes un frontend en `http://tupagina.com` y haces una petición a un backend que está en `http://api.otroservidor.com`, **el navegador podría bloquear esa solicitud si no está permitido explícitamente** por el servidor.

Esto se hace para proteger a los usuarios de ataques como el **Cross-Site Request Forgery (CSRF)**.

---

### ❌ ¿Qué es un error de CORS?

Un **error de CORS ocurre cuando intentas hacer una petición a otro dominio (cross-origin)** y el servidor **no autoriza esa conexión**.

#### 🔥 Mensajes comunes:

- `Access to fetch at 'http://api.ejemplo.com/data' from origin 'http://localhost:3000' has been blocked by CORS policy.`
- `No 'Access-Control-Allow-Origin' header is present on the requested resource.`

---

### 🧾 Ejemplo del error:

Tienes este frontend en React (localhost:3000):

```js
fetch("https://api.ejemplo.com/users")
  .then((res) => res.json())
  .then((data) => console.log(data));
```

Si `https://api.ejemplo.com` **no permite peticiones desde `localhost:3000`**, el navegador **bloqueará la solicitud y mostrará un error de CORS.**

---

### 🎯 ¿Cuándo ocurre un error de CORS?

Cuando ocurre una combinación como esta:

| Cliente          | Servidor                             | Resultado     |
| ---------------- | ------------------------------------ | ------------- |
| `localhost:3000` | `api.misitio.com`                    | ❌ CORS error |
| `tudominio.com`  | `api.tudominio.com`                  | ✅ Permitido  |
| `localhost:3000` | `localhost:5000` (con CORS activado) | ✅ Permitido  |

---

### 🛠️ ¿Cómo solucionarlo?

#### ✅ Solución 1: **Permitir el origen desde el servidor**

Debes agregar un **header** en el servidor llamado:

```
Access-Control-Allow-Origin
```

Y puedes configurarlo para que permita peticiones desde ciertos orígenes.

---

#### 💡 Ejemplo en distintos lenguajes

##### 🔵 Node.js con Express:

```js
const express = require("express");
const cors = require("cors");
const app = express();

// Permitir todos los orígenes (no recomendable en producción)
app.use(cors());

// O permitir uno específico:
app.use(cors({ origin: "http://localhost:3000" }));

app.get("/datos", (req, res) => {
  res.json({ mensaje: "Hola desde el backend" });
});

app.listen(4000, () => console.log("Servidor en puerto 4000"));
```

---

##### 🟠 Python con Flask:

```python
from flask import Flask
from flask_cors import CORS

app = Flask(__name__)
CORS(app)  # Permite todos los orígenes

@app.route('/datos')
def datos():
    return {"mensaje": "Hola desde Flask"}

app.run(port=5000)
```

---

##### 🔶 PHP:

```php
header("Access-Control-Allow-Origin: *");
```

---

### 🛡️ ¿Es seguro permitir todos los orígenes (`*`)?

**No.** Solo debes permitir todos los orígenes en:

- Desarrollo local
- APIs públicas sin autenticación sensible

Para APIs con datos privados, **debes restringir el origen.**

---

### 🧪 ¿Cómo probar si es error de CORS?

1. Abre la consola del navegador (F12).
2. Haz una petición fetch o XMLHttpRequest.
3. Si ves un error de tipo _"blocked by CORS policy"_, el servidor no lo está permitiendo.

---

### 📦 Instalación del middleware de CORS

#### Node.js:

```bash
npm install cors
```

Y luego:

```js
const cors = require("cors");
app.use(cors());
```

---

### ✅ Ejemplo completo

#### 🧱 Backend (Express en Node.js)

```js
// backend.js
const express = require("express");
const cors = require("cors");
const app = express();

// Permitir desde React local
app.use(cors({ origin: "http://localhost:3000" }));

app.get("/saludo", (req, res) => {
  res.json({ mensaje: "Hola Gustavo desde el servidor" });
});

app.listen(4000, () => console.log("Servidor en puerto 4000"));
```

#### 🖥️ Frontend (React)

```js
// App.jsx
import { useEffect, useState } from "react";

function App() {
  const [mensaje, setMensaje] = useState("");

  useEffect(() => {
    fetch("http://localhost:4000/saludo")
      .then((res) => res.json())
      .then((data) => setMensaje(data.mensaje))
      .catch((err) => console.error("Error de CORS:", err));
  }, []);

  return <h1>{mensaje}</h1>;
}

export default App;
```

---

### 🧩 Consejos finales

- En producción, **usa una lista blanca de orígenes permitidos**.
- No uses `*` si tu API requiere autenticación.
- Usa herramientas como [Postman](https://www.postman.com/) para probar si el servidor está respondiendo correctamente sin depender del navegador.

---

[🔼](#índice)

---

| **Inicio**         | **atrás 25**                                       | **Siguiente 27**                                                   |
| ------------------ | -------------------------------------------------- | ------------------------------------------------------------------ |
| [🏠](../README.md) | [⏪](./7_25_Introduccion_a_Informatica_Forense.md) | [⏩](./7_27_Preparacion_para_la_Certificacion_CompTIA_Security.md) |
