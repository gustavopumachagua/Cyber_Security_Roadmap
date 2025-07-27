| **Inicio**         | **atrás 19**                                         | **Siguiente 21**                                                                  |
| ------------------ | ---------------------------------------------------- | --------------------------------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./7_19_Hacking_Aplicaciones_Web_Server_Side.md) | [⏩](./7_21_Introduccion_a_la_Ingenieria_Social_Tecnicas_Ataques_y_Pretexting.md) |

---

## **Índice**

| Temario                                                                                                                                                   |
| --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [1007. Tus datos estan en peligro ¿Como Protegerte?](#1007-tus-datos-estan-en-peligro-como-protegerte)                                                    |
| [1008. Autenticación 2FA: crucial para proteger tus cuentas](#1008-autenticación-2fa-crucial-para-proteger-tus-cuentas)                                   |
| [1009. Construye y administra contraseñas robustas](#1009-construye-y-administra-contraseñas-robustas)                                                    |
| [1010. Navegar seguro en redes publicas ¿Como?](#1010-navegar-seguro-en-redes-publicas-como)                                                              |
| [1011. Configura un antivirus para tus dispositivos](#1011-configura-un-antivirus-para-tus-dispositivos)                                                  |
| [1012. Cómo aumentar el nivel de seguridad contra ransomware](#1012-cómo-aumentar-el-nivel-de-seguridad-contra-ransomware)                                |
| [1013. Riesgos del uso de software pirata](#1013-riesgos-del-uso-de-software-pirata)                                                                      |
| [1014. Los riesgos de mantener un sistema empresarial desactualizado](#1014-los-riesgos-de-mantener-un-sistema-empresarial-desactualizado)                |
| [1015. Configura el control parental en los dispositivos de tu familia](#1015-configura-el-control-parental-en-los-dispositivos-de-tu-familia)            |
| [1016. ¿Por qué mantener los sistemas siempre actualizados?](#1016-por-qué-mantener-los-sistemas-siempre-actualizados)                                    |
| [1017. Restringir los permisos del sistema para limitar daños](#1017-restringir-los-permisos-del-sistema-para-limitar-daños)                              |
| [1018. Cómo identificar mensajes potencialmente inseguros](#1018-cómo-identificar-mensajes-potencialmente-inseguros)                                      |
| [1019. Phishing: identifica los elementos que indican que un correo es falso](#1019-phishing-identifica-los-elementos-que-indican-que-un-correo-es-falso) |
| [1020. Uso seguro de ChatGPT](#1020-uso-seguro-de-chatgpt)                                                                                                |
| [1021. La ciberseguridad es grupal](#1021-la-ciberseguridad-es-grupal)                                                                                    |

# **Introducción a Ciberseguridad: Prevención de Ataques Informáticos**

## **1007. Tus datos estan en peligro ¿Como Protegerte?**

### 🔐 **¿Tus datos están en peligro? ¿Cómo protegerte?**

Vivimos en un mundo donde gran parte de nuestra vida está digitalizada: fotos, contraseñas, números de tarjetas, historial médico, redes sociales... **¡todo!**
Y sí: **tus datos personales están en peligro** si no tomas medidas.

Veamos **por qué**, **cómo protegerte**, y al final **un ejemplo completo de prácticas seguras** que tú mismo puedes aplicar.

---

### 🧠 ¿Por qué están en peligro tus datos?

Tus datos pueden ser robados o expuestos por:

| Amenaza                      | Ejemplo sencillo                                                |
| ---------------------------- | --------------------------------------------------------------- |
| Phishing                     | Te llega un correo de "tu banco" pidiendo tu clave              |
| Malware/Spyware              | Descargas una app falsa y roba tus archivos o contraseñas       |
| Redes Wi-Fi inseguras        | Te conectas al Wi-Fi del café y alguien te espía                |
| Contraseñas débiles          | Usas "123456" como contraseña                                   |
| Reutilización de contraseñas | Usas la misma clave en muchas páginas: si una se filtra, todas  |
| Ingeniería social            | Alguien se hace pasar por soporte y te convence de dar tu clave |
| Aplicaciones maliciosas      | Instalas apps que espían o roban datos en segundo plano         |

---

### 🛡️ ¿Cómo proteger tus datos? (Paso a paso)

Aquí tienes una **guía práctica** dividida por áreas:

---

#### ✅ 1. **Contraseñas fuertes y únicas**

- Usa contraseñas como: `S!6$k&uT9z@2025`
- No repitas contraseñas entre servicios
- Usa un **gestor de contraseñas** como:

  - **Bitwarden** (gratis y de código abierto)
  - **1Password** / **LastPass**

📦 **Instalación de Bitwarden (ejemplo en PC):**

```bash
sudo snap install bitwarden
```

---

#### ✅ 2. **Autenticación de dos factores (2FA)**

Habilita 2FA en:

- Google, Facebook, Instagram
- Correo (Gmail, Outlook)
- Billeteras de criptomonedas
- Servicios bancarios

🔐 Usa apps como:

- **Google Authenticator**
- **Authy** (puedes hacer copia de seguridad en la nube)

---

#### ✅ 3. **Navegación segura**

- Usa **HTTPS** siempre
- Instala extensiones como:

  - **uBlock Origin** (bloquea rastreadores y anuncios maliciosos)
  - **Privacy Badger** (protege tu privacidad)

🧪 Ejemplo con Chrome o Brave:

1. Ve a la Chrome Web Store
2. Busca "uBlock Origin"
3. Haz clic en "Agregar a Chrome"

---

#### ✅ 4. **Wi-Fi y conexiones seguras**

- No uses Wi-Fi públicas sin VPN
- Cambia la contraseña por defecto de tu router
- Usa cifrado **WPA2 o WPA3** en casa

🔐 Recomendado: **VPN segura** como:

- ProtonVPN (tiene plan gratis)
- Mullvad (sin cuenta, paga con criptomonedas)

---

#### ✅ 5. **Actualizaciones**

- Actualiza siempre:

  - Windows, Linux, macOS
  - Navegador
  - Antivirus
  - Apps móviles

🛠️ ¿Por qué? → Muchas brechas ocurren por **fallos antiguos no parcheados**

---

#### ✅ 6. **Evita el phishing**

- No hagas clic en enlaces sospechosos
- Revisa el dominio antes de escribir tus credenciales (¿es `micr0soft.com`?)
- Si una web pide tus datos personales y no la esperabas: **sospecha**

---

#### ✅ 7. **Copia de seguridad (Backup)**

- Haz copia de tus fotos, documentos y claves
- Usa:

  - Disco externo
  - Google Drive / Dropbox / MEGA
  - Syncthing (alternativa libre, descentralizada)

📁 Organiza backups **encriptados** si es posible.

---

#### ✅ 8. **Antivirus y Antimalware**

- En Windows, activa **Defender** (es bueno)
- Usa también:

  - **Malwarebytes** (gratis para escanear)
  - **ClamAV** (en Linux)

🧪 En Linux (Ubuntu):

```bash
sudo apt install clamav
sudo freshclam
sudo clamscan -r /home/tuusuario
```

---

### 💻 Ejemplo completo: Cómo protegerte día a día

Imaginemos tu rutina diaria con prácticas seguras:

| Acción                    | Práctica segura que aplicas                                 |
| ------------------------- | ----------------------------------------------------------- |
| Inicias sesión en Gmail   | Usas contraseña única + 2FA con Google Authenticator        |
| Navegas sitios web        | Tienes uBlock Origin y Privacy Badger activados             |
| Usas redes sociales       | Evitas enlaces sospechosos en mensajes                      |
| Guardas tus contraseñas   | Usas Bitwarden para generarlas y almacenarlas               |
| Trabajas desde una laptop | VPN activada al usar Wi-Fi público                          |
| Usas apps móviles         | Solo instalas desde fuentes oficiales (Play Store/AppStore) |
| Haces backup              | Semanalmente haces copia en disco externo y nube            |

---

### 🧩 Bonus: Prueba si tu correo ha sido filtrado

Visita:

🔍 [https://haveibeenpwned.com/](https://haveibeenpwned.com/)
📧 Escribe tu correo y revisa si ha sido filtrado en alguna brecha de seguridad.

---

### 🔚 Conclusión

Tus datos sí están en peligro **si no te proteges**. Pero con estas herramientas, hábitos y medidas simples puedes reducir **enormemente** los riesgos.

---

[🔼](#índice)

---

## **1008. Autenticación 2FA: crucial para proteger tus cuentas**

### ✅ ¿Qué es la autenticación 2FA?

**2FA** (Two-Factor Authentication o Autenticación de Dos Factores) es una capa extra de seguridad al iniciar sesión en una cuenta. En lugar de solo usar tu contraseña, también debes **verificar tu identidad** con un segundo método.

> 🔓 Así, **aunque alguien tenga tu contraseña**, **no podrá entrar sin el segundo factor**.

---

### 🔑 Ejemplo sencillo

Sin 2FA:

1. Vas a Gmail
2. Escribes tu correo y contraseña
3. ¡Listo! Acceso concedido

Con 2FA:

1. Escribes tu correo y contraseña
2. Te llega un código a tu celular (o app)
3. Debes escribirlo para entrar

---

### 🛠️ Tipos comunes de segundo factor

| Tipo                        | Ejemplo                                     |
| --------------------------- | ------------------------------------------- |
| App de autenticación (TOTP) | Google Authenticator, Authy, Microsoft Auth |
| SMS o llamada               | Código que te llega por mensaje             |
| Correo electrónico          | Código temporal enviado a tu email          |
| Dispositivo físico          | YubiKey, tarjeta de seguridad               |
| Huella digital / biometría  | Reconocimiento facial, dactilar             |

---

### 🔒 ¿Por qué es crucial?

| Amenaza                      | Cómo te protege 2FA                            |
| ---------------------------- | ---------------------------------------------- |
| Phishing (te roban la clave) | No pueden entrar sin el segundo código         |
| Filtraciones de contraseñas  | Aunque tu clave esté expuesta, estás protegido |
| Keyloggers                   | Capturan tu clave, pero no tu app de 2FA       |

---

### 📲 ¿Cómo se instala?

#### 🔹 Opción A: Usar **Google Authenticator**

1. Instala desde Play Store o App Store
   📱 **Google Authenticator**
2. Activa 2FA en un sitio (ej. Gmail, Facebook)
3. Escanea el **QR** que te muestra la página
4. La app te dará códigos cada 30 segundos
5. Cuando inicies sesión, ¡usa ese código!

#### 🔹 Opción B: Usar **Authy** (recomendado porque guarda backups)

1. Descarga Authy:

   - Android: [https://play.google.com/store/apps/details?id=com.authy.authy](https://play.google.com/store/apps/details?id=com.authy.authy)
   - iOS: [https://apps.apple.com/us/app/authy/id494168017](https://apps.apple.com/us/app/authy/id494168017)

2. Regístrate con tu número y correo
3. Cuando una web te diga "Escanea este código QR", abre Authy
4. Escanea y listo: obtendrás códigos temporales

---

### 🧪 Activar 2FA en tus cuentas principales

| Plataforma | ¿Dónde activar 2FA?                                        |
| ---------- | ---------------------------------------------------------- |
| Gmail      | myaccount.google.com → Seguridad → Verificación en 2 pasos |
| Instagram  | Configuración → Seguridad → Autenticación en dos pasos     |
| Facebook   | Configuración → Seguridad e inicio de sesión               |
| GitHub     | Settings → Security → Two-factor authentication            |
| Amazon     | Cuenta → Login y Seguridad → 2FA                           |

---

### 💡 Recomendación: Guarda tus códigos de respaldo

Cada vez que actives 2FA, las plataformas te darán **códigos de respaldo**. Guárdalos en:

- Un cuaderno físico
- Un archivo cifrado (por ejemplo, con Bitwarden)
- Nunca en un documento sin protección

---

### 📦 Ejemplo completo: Activando 2FA en tu cuenta de Google con Authy

#### Paso 1: Instalar Authy

- Ve a la Play Store / App Store
- Busca “**Authy**”
- Instálalo y registra tu número y correo

#### Paso 2: Activar 2FA en Google

1. Entra a [https://myaccount.google.com/security](https://myaccount.google.com/security)
2. Ve a “**Verificación en dos pasos**”
3. Elige “**App de autenticación**”
4. Google te mostrará un **código QR**
5. Abre Authy → toca el botón “+” → escanea el código
6. Authy comenzará a generar códigos de 6 dígitos
7. Google te pedirá que ingreses uno → hazlo

¡Listo! Tu cuenta está protegida con 2FA.

---

### 🛡️ ¿Y si pierdo el celular?

Por eso es clave:

- Guardar tus **códigos de respaldo**
- Usar Authy, que permite hacer **backup** seguro en la nube
- Registrar más de un método (correo, SMS)

---

### 🔚 Conclusión

La autenticación 2FA es una de las formas **más simples y efectivas** de proteger tus cuentas. No cuesta nada y puede evitar:

- Robos de cuentas
- Suplantación de identidad
- Pérdida de archivos importantes

---

[🔼](#índice)

---

## **1009. Construye y administra contraseñas robustas**

### 🔐 ¿Qué es una contraseña robusta?

Una **contraseña robusta** es una clave difícil de adivinar por humanos o sistemas automatizados (como los que usan ataques de fuerza bruta o diccionario). Debe ser:

✅ Larga (mínimo 12 caracteres)

✅ Compleja (mezcla de mayúsculas, minúsculas, números y símbolos)

✅ Única (una contraseña distinta para cada cuenta)

✅ No basada en datos personales (fechas, nombres, etc.)

---

### ❌ Ejemplos de contraseñas débiles (¡no usar!):

- `123456`
- `contraseña`
- `pepito2023`
- `admin`
- `lima123`

Estas son muy comunes y pueden ser **adivinadas en segundos**.

---

### ✅ Ejemplos de contraseñas robustas:

- `gD7!#zQrN!vF28sL`
- `v3rD3_P1z@!*20xx`
- `rG!e29qU-tX#cL7m`

¿Difíciles de recordar? ¡Por eso existen los gestores de contraseñas!

---

### 🔐 ¿Qué es un gestor de contraseñas?

Es una herramienta que:

- Genera contraseñas seguras
- Las guarda cifradas
- Te permite autocompletar en sitios web
- Solo debes recordar una **contraseña maestra**

#### Los más conocidos:

| Gestor        | Tipo     | Características                               |
| ------------- | -------- | --------------------------------------------- |
| **Bitwarden** | Gratuito | Código abierto, nube o local, extensiones web |
| **1Password** | De pago  | Muy seguro, multiplataforma                   |
| **KeepassXC** | Gratuito | Almacenamiento local, sin nube                |
| **LastPass**  | Freemium | Sincroniza, pero ha tenido filtraciones       |

---

### 🛠️ Instalación de Bitwarden (recomendado)

#### 🔹 Opción 1: Versión Web (no requiere instalación)

1. Ve a: [https://vault.bitwarden.com](https://vault.bitwarden.com)
2. Crea una cuenta
3. Crea una contraseña maestra (la única que debes memorizar)
4. ¡Listo! Puedes empezar a guardar contraseñas

---

#### 🔹 Opción 2: Extensión para navegador

1. Chrome/Firefox: busca “Bitwarden” en la tienda de extensiones
2. Instálala
3. Inicia sesión
4. Cuando vayas a un formulario, Bitwarden puede sugerir o guardar contraseñas automáticamente

---

#### 🔹 Opción 3: App para escritorio o móvil

- [https://bitwarden.com/download/](https://bitwarden.com/download/)
- Compatible con Windows, Linux, macOS, Android, iOS

---

### 🧪 Ejemplo completo: Cómo crear y guardar una contraseña robusta para Gmail

#### Paso 1: Instalar extensión Bitwarden

- En Google Chrome:

  - Ir a: [https://chrome.google.com/webstore](https://chrome.google.com/webstore)
  - Buscar: `Bitwarden`
  - Instalar la extensión

#### Paso 2: Crear cuenta en Bitwarden

- Crea una cuenta en [https://vault.bitwarden.com](https://vault.bitwarden.com)
- Elige una contraseña **maestra fuerte** (ej: `B1tw4rD3n!20xx#`)

#### Paso 3: Generar una contraseña segura

1. Haz clic en la extensión de Bitwarden
2. Ve a "Generador de contraseñas"
3. Configura:

   - Longitud: 16 caracteres
   - Incluir: mayúsculas, números, símbolos

4. Copia la contraseña generada

Ejemplo: `t$L9q#Wm4z!3BNv8`

#### Paso 4: Crear cuenta en Gmail y usar la contraseña

1. Ve a [https://accounts.google.com/signup](https://accounts.google.com/signup)
2. Pega la contraseña generada
3. Bitwarden detectará el formulario y te preguntará si quieres guardar esta contraseña
4. Acepta → ya está guardada

#### Paso 5: Autocompletar y administrar

- La próxima vez que entres a Gmail, Bitwarden completará tu usuario y contraseña.
- Puedes revisar y editar contraseñas en el **“Vault”**.

---

### 🎯 Tips extra para una buena administración

- Usa **una contraseña distinta** por cada cuenta
- No repitas contraseñas entre redes sociales, bancos, correos
- Activa **2FA** (verificación en dos pasos) en cuentas críticas
- Cambia tus contraseñas si un sitio web sufrió una **filtración**

---

### 📦 Bonus: Cómo crear una contraseña robusta fácil de recordar

Usa una frase aleatoria y reemplaza letras:

Ejemplo:

- Frase: `Mi perro come ceviche los domingos`
- Transformada: `M1p3rr0C0m3C3v!ch3L0sD0m1ng0s`

Es fácil de recordar para ti, pero difícil para una máquina.

---

### 🛡️ Conclusión

🔐 **Construir y administrar contraseñas robustas es esencial para tu seguridad digital.**
Herramientas como Bitwarden lo hacen fácil, seguro y accesible para todos.

---

[🔼](#índice)

---

## **1010. Navegar seguro en redes publicas ¿Como?**

### 🌐 ¿Qué es una red pública?

Una **red pública** es una conexión a Internet abierta y gratuita, sin contraseña o con acceso libre, como por ejemplo:

- WiFi del aeropuerto
- Red gratuita en cafés o restaurantes
- WiFi en buses o estaciones
- Redes compartidas en hoteles

🔴 **Problema**: Estas redes **no son seguras**, y cualquier persona conectada puede interceptar lo que haces si no tomas precauciones.

---

### 🎯 ¿Por qué son peligrosas?

Cuando te conectas a una red pública sin protección:

1. **Tus datos viajan sin cifrar**
2. **Cualquiera en la misma red** podría espiar tu tráfico
3. Es posible que estés conectado a un **"Evil Twin"**: una red falsa que imita la original para robar información
4. Puedes caer en ataques tipo **Man-in-the-Middle (MitM)**

---

### 🛡️ ¿Cómo navegar seguro en redes públicas?

Aquí tienes **las mejores prácticas** y herramientas con ejemplos fáciles:

---

#### ✅ 1. Usa una VPN (Red Privada Virtual)

**¿Qué hace?**

Cifra toda tu conexión. Nadie, ni siquiera el administrador del WiFi, podrá ver lo que haces.

**Ejemplos de VPN confiables:**

| VPN                 | Gratis | Notas                              |
| ------------------- | ------ | ---------------------------------- |
| ProtonVPN           | ✅     | Gratuito con servidores limitados  |
| Windscribe          | ✅     | Hasta 10GB/mes en plan gratuito    |
| Mullvad VPN         | ❌     | Muy privado, sin registros, barato |
| NordVPN / Surfshark | ❌     | De pago, fáciles de usar           |

---

#### 🔧 Instalación de **ProtonVPN** (ejemplo gratuito):

1. Ve a: [https://protonvpn.com](https://protonvpn.com)
2. Regístrate (puedes usar un correo temporal si deseas más privacidad)
3. Descarga el cliente para:

   - Windows/macOS
   - Android/iOS
   - Linux (mediante terminal)

4. Inicia sesión, elige un país gratuito
5. ¡Conéctate! Todo tu tráfico estará cifrado.

---

#### ✅ 2. Usa sitios con HTTPS

🔒 Solo navega por sitios que usan **HTTPS** (mira el candado en la barra del navegador)

Ejemplo seguro:

✔️ `https://banco.pe`

Ejemplo no seguro (¡evítalo!):

❌ `http://banco.pe`

---

#### ✅ 3. Evita acceder a servicios sensibles

En redes públicas:

- ❌ No hagas transferencias bancarias
- ❌ No ingreses a tu correo principal si puedes evitarlo
- ❌ No uses tus contraseñas sin protección (usa VPN o espera a estar en casa)

---

#### ✅ 4. Usa autenticación de dos factores (2FA)

Incluso si alguien roba tu contraseña, no podrá ingresar sin el código del 2FA.

- Gmail → Usa Google Authenticator o similar
- Instagram, Facebook, etc. → Activa en configuración de seguridad

---

#### ✅ 5. Desactiva la compartición de archivos

En Windows:

1. Ve a **Panel de Control → Red e Internet → Centro de redes y recursos compartidos**
2. Haz clic en tu red actual
3. Marca como “Red pública”
4. Desactiva la opción de compartir archivos e impresoras

---

#### ✅ 6. Usa navegador seguro + extensiones

- 🦊 Usa **Firefox** o **Brave** (ambos respetan tu privacidad)
- Instala extensiones como:

  - **HTTPS Everywhere** (fuerza HTTPS)
  - **uBlock Origin** (bloquea anuncios maliciosos)
  - **Privacy Badger** (bloquea rastreadores)

---

### 🧪 Ejemplo completo paso a paso: Navegar seguro en la WiFi del aeropuerto

#### Escenario:

Vas a esperar 2 horas en el aeropuerto y quieres revisar tu correo y redes.

---

#### 🔹 Paso 1: Conéctate a la red del aeropuerto

- Elige la red con más señal, por ejemplo `Aeropuerto_Libre`

---

#### 🔹 Paso 2: Abre ProtonVPN

1. Abres la app de ProtonVPN
2. Te conectas al servidor más cercano (por ejemplo: `United States Free #1`)
3. Esperas a que diga "Connected"

---

#### 🔹 Paso 3: Asegúrate de que el candado HTTPS esté visible

- Entra a tu correo Gmail: `https://mail.google.com`
- Verifica que haya 🔒 en la barra del navegador

---

#### 🔹 Paso 4: Evita abrir apps bancarias o sitios sin HTTPS

- Si vas a ver tus redes, hazlo desde el navegador con VPN activada

---

#### 🔹 Paso 5: Desconéctate y borra la red al terminar

1. Haz clic en “Olvidar esta red” después de salir del aeropuerto
2. Cierra sesión de tu correo y VPN si ya no la usarás

---

### 💡 Otros consejos útiles:

- 🔌 Usa tus datos móviles si vas a ingresar a sitios críticos (banco, SUNAT, etc.)
- 📶 No te conectes a redes WiFi con nombres raros o que imiten marcas (ej: `FreeStarbucksOpen`)
- 🔋 Apaga el WiFi cuando no lo uses

---

### 🛡️ Conclusión

**Navegar seguro en redes públicas no es difícil**, pero requiere **hábitos y herramientas**:

| Hábito                   | ¿Protege? |
| ------------------------ | --------- |
| Usar VPN                 | ✅ Sí     |
| Verificar HTTPS          | ✅ Sí     |
| No hacer cosas sensibles | ✅ Sí     |
| Compartir sin control    | ❌ No     |

---

[🔼](#índice)

---

## **1011. Configura un antivirus para tus dispositivos**

¡Claro, Gustavo! Aquí tienes una **explicación completa, fácil de entender**, sobre **cómo configurar un antivirus en tus dispositivos** (Windows, Android y Mac), incluyendo **cómo se instala** y un **ejemplo completo paso a paso** al final.

---

## 🛡️ ¿Qué es un antivirus?

Un **antivirus** es un software diseñado para **detectar, bloquear y eliminar** virus, malware, ransomware, spyware y otras amenazas digitales que pueden afectar tu computadora o teléfono.

### 🧠 ¿Por qué es importante tener uno?

- Protege tu información personal
- Detecta amenazas en tiempo real
- Bloquea sitios web maliciosos
- Analiza archivos antes de que los abras
- Evita que un ciberataque te afecte

---

## 🔍 ¿Qué características debe tener un buen antivirus?

| Característica              | ¿Por qué importa?                        |
| --------------------------- | ---------------------------------------- |
| Protección en tiempo real   | Detecta amenazas mientras usas el equipo |
| Análisis bajo demanda       | Puedes escanear archivos manualmente     |
| Bajo consumo de recursos    | No ralentiza tu equipo                   |
| Actualizaciones automáticas | Mantiene su base de datos al día         |
| Cortafuegos (Firewall)      | Controla el tráfico de red               |
| Protección web              | Bloquea sitios inseguros                 |

---

## ✅ Antivirus recomendados (gratuitos y de pago)

| Antivirus             | Gratis | Plataformas           | Notas                               |
| --------------------- | ------ | --------------------- | ----------------------------------- |
| **Windows Defender**  | ✅     | Windows               | Viene preinstalado en Windows 10/11 |
| **Avast Free**        | ✅     | Windows, Mac, Android | Fácil de usar, incluye escudo web   |
| **Bitdefender Free**  | ✅     | Windows, Android      | Ligero, silencioso y eficaz         |
| **Kaspersky Free**    | ✅     | Windows, Android      | Muy buena detección de malware      |
| **Malwarebytes Free** | ✅     | Windows, Mac          | Bueno para análisis puntual         |
| **Sophos Home Free**  | ✅     | Windows, Mac          | Ideal para familias                 |

---

## 💻 Instalación y configuración en Windows (Ejemplo con Avast Free)

### 🔧 Instalación:

1. Ve a [https://www.avast.com/es-pe/free-antivirus-download](https://www.avast.com/es-pe/free-antivirus-download)
2. Haz clic en **"Descargar gratis"**
3. Abre el archivo `.exe` descargado
4. Haz clic en **"Instalar"**
5. Espera a que finalice el proceso
6. Haz clic en **"Continuar"** y luego en **"Usar versión gratuita"**

---

### ⚙️ Configuración básica (Avast Free):

1. **Escaneo rápido inicial**
   Se ejecuta automáticamente después de instalar. Deja que termine.

2. **Programar escaneos automáticos**

   - Ve a **Protección → Antivirus → Escaneos programados**
   - Configura un escaneo semanal cada lunes a las 9:00 a.m.

3. **Activar escudo web y de correo**

   - Ve a **Protección activa** y asegúrate de que:

     - “Escudo web” esté activado
     - “Escudo de correo electrónico” esté activado

4. **Actualizar la base de datos de virus**

   - Ve a **Menú → Configuración → Actualizaciones**
   - Asegúrate de que esté en “Automático”

---

## 📱 Instalación en Android (Ejemplo con Bitdefender Free)

1. Abre **Google Play Store**
2. Busca **"Bitdefender Antivirus Free"**
3. Instala la app
4. Ábrela y permite los permisos necesarios
5. Toca **"Scan"** para escanear tu teléfono

---

## 🍏 Instalación en Mac (Ejemplo con Avast)

1. Ve a [https://www.avast.com/en-us/free-mac-security](https://www.avast.com/en-us/free-mac-security)
2. Descarga el instalador
3. Ábrelo y sigue las instrucciones
4. Una vez instalado, ejecuta un análisis completo

---

## ✅ Ejemplo completo paso a paso: Proteger tu laptop con Avast Free

### Escenario:

Tienes una laptop con Windows 10 y quieres protegerla gratis con un antivirus confiable.

---

### 🔹 Paso 1: Descargar

- Vas a [https://www.avast.com](https://www.avast.com)
- Haces clic en “Descargar antivirus gratis”

---

### 🔹 Paso 2: Instalar

- Abres el archivo `.exe` descargado
- Le das a “Instalar” y esperas
- Al terminar, eliges “Usar versión gratuita”

---

### 🔹 Paso 3: Configurar

- Se abre el panel de Avast
- Haz un **escaneo rápido inicial**
- Activa los **escudos en tiempo real**
- Programa un **escaneo semanal**
- Verifica que las **actualizaciones automáticas** estén activadas

---

### 🔹 Paso 4: Recomendación final

Activa el **modo No Molestar** para que no te interrumpa con ventanas emergentes mientras juegas o trabajas.

---

### 🎁 Bonus: Consejos de seguridad con antivirus

- **No instales dos antivirus al mismo tiempo** (pueden interferir entre sí)
- **Mantén el antivirus actualizado**
- **Haz escaneos regulares**
- Si te pide eliminar algo sospechoso, deja que lo haga
- Usa también **Malwarebytes Free** para escaneos puntuales

---

[🔼](#índice)

---

## **1012. Cómo aumentar el nivel de seguridad contra ransomware**

### 🧨 ¿Qué es el ransomware?

El **ransomware** es un tipo de malware que **bloquea tus archivos o sistema** y exige un **rescate (ransom)** para liberarlos. Es como si alguien entrara a tu casa, cerrara con llave tus cosas y te pidiera dinero para devolvértelas.

---

### ⚠️ ¿Qué puede hacerte el ransomware?

- Encripta tus fotos, documentos, videos, trabajos.
- Puede bloquear todo tu sistema operativo.
- Te pide pagar en criptomonedas (Bitcoin, Monero, etc.).
- Aunque pagues, a veces **no recuperas tus datos**.

---

### 🛡️ ¿Cómo protegerte del ransomware?

Aquí tienes **7 estrategias clave** con ejemplos y cómo implementarlas.

---

#### 1. 🔄 **Mantén el sistema y programas actualizados**

Los ransomware explotan vulnerabilidades. Si tu sistema está desactualizado, es un blanco fácil.

✅ _Ejemplo:_

- Instala actualizaciones de Windows, Linux o Android tan pronto salgan.

🛠️ _Cómo hacerlo en Windows:_

- Ir a: **Configuración → Actualización y seguridad → Buscar actualizaciones**

---

#### 2. 🧪 **Instala un antivirus y antimalware con protección contra ransomware**

Algunos antivirus tienen **módulos especiales** contra ransomware.

✅ _Ejemplo:_

- Bitdefender, Kaspersky, Avast, Sophos y Malwarebytes tienen protección dedicada contra ransomware.

🛠️ _Instalación con Malwarebytes (Gratis):_

1. Ve a: [https://www.malwarebytes.com](https://www.malwarebytes.com)
2. Descarga el instalador y ejecútalo.
3. Haz clic en **"Activar protección gratuita"**
4. Programa escaneos semanales.

---

#### 3. 📦 **Haz backups regulares de tus archivos**

Esto te protege si el ransomware cifra tus archivos: puedes restaurarlos sin pagar nada.

✅ _Ejemplo:_

- Usa un disco externo o un servicio en la nube (Google Drive, OneDrive, Mega, Dropbox).

🛠️ _Cómo hacerlo en Windows:_

1. Conecta un disco externo.
2. Ir a: **Configuración → Copia de seguridad → Agregar unidad**
3. Elige el disco externo → activa **"Hacer copia de seguridad automática"**

---

#### 4. 🔒 **Usa control de acceso y privilegios mínimos**

Muchos ransomware se instalan desde cuentas con permisos de administrador.

✅ _Ejemplo:_

- Crea una cuenta limitada para usar todos los días.

🛠️ _Cómo crear un usuario limitado en Windows:_

1. **Configuración → Cuentas → Familia y otros usuarios**
2. Clic en **"Agregar otra persona"**
3. Elige “usuario sin cuenta Microsoft”
4. Asígnale un nombre y selecciona “usuario estándar”

---

#### 5. 💻 **Desactiva macros en Office y ejecutables desconocidos**

Muchos ataques llegan por **documentos maliciosos** (Word, Excel) que usan **macros** para ejecutar ransomware.

🛠️ _Desactivar macros en Word/Excel:_

1. Abre Word → **Archivo → Opciones**
2. Ir a **Centro de confianza → Configuración del centro de confianza**
3. Ir a **Configuración de macros → Marcar "Deshabilitar todas las macros"**

---

#### 6. 🧱 **Activa el control de carpetas en Windows Defender (anti-ransomware)**

Esto impide que aplicaciones no autorizadas modifiquen tus archivos personales.

🛠️ _Pasos:_

1. Ve a **Seguridad de Windows**
2. Clic en **Protección contra virus y amenazas**
3. Clic en **Administrar protección contra ransomware**
4. Activa **"Acceso controlado a carpetas"**
5. Agrega carpetas como: `Documentos`, `Imágenes`, `Escritorio`

---

#### 7. 🌐 **Evita redes Wi-Fi públicas y correos sospechosos**

✅ _Ejemplo:_

No abras archivos adjuntos ni enlaces en correos que no esperas, aunque parezcan del banco o tu jefe.

🛠️ _Consejos rápidos:_

- Si el archivo se llama `Factura_23-07.exe`, **¡nunca lo abras!**
- Si el correo viene con faltas de ortografía, ¡desconfía!

---

### ✅ Ejemplo completo paso a paso: Cómo proteger tu laptop con Windows 10 de ransomware

**Escenario:**

Tienes una laptop con Windows 10 y quieres protegerte del ransomware sin pagar nada.

---

#### 🔹 Paso 1: Actualiza tu sistema

- **Configuración → Actualización y seguridad → Buscar actualizaciones**
- Instala todo lo disponible.

---

#### 🔹 Paso 2: Instala Malwarebytes

1. Ve a: [https://www.malwarebytes.com](https://www.malwarebytes.com)
2. Descarga el instalador
3. Instala y activa la versión gratuita
4. Programa un análisis semanal

---

#### 🔹 Paso 3: Habilita protección anti-ransomware de Windows

1. Abre **Seguridad de Windows**
2. Ir a **Protección contra virus y amenazas**
3. Activar **"Acceso controlado a carpetas"**
4. Añadir `Documentos`, `Imágenes`, etc.

---

#### 🔹 Paso 4: Crea un respaldo en disco externo

1. Conecta un USB o disco externo
2. **Configuración → Copia de seguridad**
3. Activar copia de seguridad con historial de archivos

---

#### 🔹 Paso 5: Desactiva macros

1. Abre Word → Archivo → Opciones → Centro de confianza → Configuración de macros → Deshabilitar todas

---

#### 🔹 Paso 6: Usa un usuario limitado

1. Crea un nuevo usuario estándar desde **Configuración → Cuentas**
2. No uses la cuenta de administrador para tareas diarias

---

### 🧠 Consejos adicionales

- No uses cracks ni instaladores de programas piratas.
- Usa doble autenticación donde puedas (2FA).
- Revisa si tienes archivos con respaldo automático en la nube.

---

[🔼](#índice)

---

## **1013. Riesgos del uso de software pirata**

### 📌 ¿Qué es el software pirata?

El **software pirata** es un programa que ha sido **copiado, modificado o distribuido ilegalmente**, generalmente para evitar pagar por él. Ejemplos comunes: Windows activado con crack, Photoshop descargado de sitios ilegales, videojuegos en torrent, etc.

---

### 💥 Riesgos principales del software pirata

---

#### 1. **Malware y virus ocultos** 🦠

✅ _Ejemplo:_

Descargas un "Photoshop crackeado", pero al instalarlo también se ejecuta un troyano que roba tus contraseñas de Facebook, banco y Gmail.

🔎 _¿Por qué?_

Alguien alteró el instalador y le añadió un **keylogger** o un **ransomware**.

---

#### 2. **No hay actualizaciones de seguridad** 🔒

✅ _Ejemplo:_

Tienes un Office pirata 2019 y se descubre una vulnerabilidad grave en Excel. Microsoft lanza el parche, pero como es pirata, **no puedes actualizar**. Quedas expuesto a ciberataques.

---

#### 3. **Problemas legales** ⚖️

✅ _Ejemplo real:_

En algunos países (como Perú), las empresas pueden ser multadas por usar software pirata, incluso si lo usan “solo para diseño”.

⚠️ _Las leyes de derechos de autor pueden llevar a sanciones penales y civiles._

---

#### 4. **Fallo del sistema o pérdida de archivos** 💻

✅ _Ejemplo:_

Instalas un programa pirata de edición de video. El crack sobrescribe archivos del sistema y tu computadora se vuelve inestable: se reinicia sola, da pantallazos azules o borra archivos.

---

#### 5. **No hay soporte ni ayuda técnica** 📞🚫

✅ _Ejemplo:_

Tu software de contabilidad crackeado deja de funcionar. Contactas al soporte, pero al ver que es pirata, no pueden ayudarte.

---

#### 6. **Mal rendimiento y puertas traseras** 🧠🔓

✅ _Ejemplo:_

Un juego pirata en tu laptop se conecta a servidores desconocidos sin que te des cuenta. Consume tu internet, reduce la velocidad de tu PC y hasta puede usarte como **bot** en ataques DDoS.

---

### 🛠️ Cómo instalar software de forma legal (seguro y sin crack)

---

#### ✅ Paso 1: Usa software gratuito (open source o con licencia libre)

Alternativas legales:

| Software pirata  | Alternativa gratuita y legal                                             |
| ---------------- | ------------------------------------------------------------------------ |
| Photoshop        | GIMP ([https://www.gimp.org](https://www.gimp.org))                      |
| Microsoft Office | LibreOffice ([https://www.libreoffice.org](https://www.libreoffice.org)) |
| WinRAR           | 7-Zip ([https://www.7-zip.org](https://www.7-zip.org))                   |
| Windows 10       | Ubuntu Linux ([https://ubuntu.com](https://ubuntu.com))                  |
| FL Studio        | LMMS ([https://lmms.io](https://lmms.io))                                |

---

#### ✅ Paso 2: Compra versiones originales (con descuento si eres estudiante)

Algunas tiendas ofrecen descuentos especiales, por ejemplo:

- **Microsoft Office 365 para estudiantes:** Gratis con correo universitario.
- **Adobe Creative Cloud para estudiantes:** Hasta 65% de descuento.
- **Steam:** Juegos legales con descuentos frecuentes.

---

#### ✅ Paso 3: Usa licencias gratuitas de prueba y luego desinstala

Ejemplo:

- Malwarebytes tiene versión gratuita por 14 días con funciones premium.
- Puedes probar Windows 10 sin activar: tendrás marcas de agua, pero el sistema funciona legalmente.

---

### ✅ Ejemplo completo paso a paso: Dejar de usar software pirata

---

**Escenario:** Usabas Microsoft Office y WinRAR piratas. Quieres reemplazarlos de forma segura y sin pagar.

#### 🔹 Paso 1: Desinstala lo pirata

1. **Panel de control → Programas → Desinstalar un programa**
2. Elimina “Office 2016” y “WinRAR”
3. Borra carpetas residuales (normalmente en `C:\Program Files`)

---

#### 🔹 Paso 2: Instala alternativas legales

##### Para Office:

1. Visita [https://www.libreoffice.org](https://www.libreoffice.org)
2. Descarga la versión estable
3. Instálalo → Ahora puedes abrir y editar documentos `.docx`, `.xlsx`, `.pptx`

##### Para WinRAR:

1. Ve a [https://www.7-zip.org](https://www.7-zip.org)
2. Descarga la versión de 64 bits
3. Instálalo → Reemplaza WinRAR sin costo

---

#### 🔹 Paso 3: Verifica que no haya malware

1. Descarga Malwarebytes: [https://www.malwarebytes.com](https://www.malwarebytes.com)
2. Escanea tu sistema completo
3. Elimina cualquier amenaza que encuentre

---

#### 🔹 Paso 4: Crea el hábito de buscar software seguro

- Antes de descargar algo, busca en: `alternativeto.net`
- Revisa sitios como GitHub, SourceForge o páginas oficiales.

---

### 🧠 Consejos finales para protegerte

- No uses cracks, keygens ni parches de activación.
- Si no puedes pagar software, **hay muchas alternativas gratuitas**.
- Los piratas no te regalan software: **te venden malware** disfrazado.
- Una buena práctica es usar máquinas virtuales para probar software primero.

---

[🔼](#índice)

---

## **1014. Los riesgos de mantener un sistema empresarial desactualizado**

### 🧨 ¿Qué significa tener un sistema empresarial desactualizado?

Un **sistema desactualizado** es aquel que:

- No tiene los **últimos parches de seguridad**.
- Usa software, sistemas operativos o herramientas sin soporte.
- No aplica actualizaciones de firmware, antivirus o controladores.
- Mantiene plataformas web o servidores sin mantenimiento.

Esto ocurre por **falta de tiempo**, **desconocimiento**, **temor a que algo se rompa**, o por **descuido**.

---

### ⚠️ Principales riesgos de tener sistemas empresariales desactualizados

---

#### 1. **Vulnerabilidades conocidas sin parchar**

Los atacantes pueden aprovechar errores públicos (CVE) para explotar el sistema.

✅ _Ejemplo:_

Tu servidor Windows Server 2012 tiene una vulnerabilidad RDP conocida. Un atacante puede conectarse remotamente sin contraseña y tomar control total.

---

#### 2. **Ransomware y malware**

Los sistemas sin actualizar son el blanco favorito de malware que se propaga automáticamente.

✅ _Ejemplo real:_

El ransomware **WannaCry** afectó a más de 200,000 empresas en 2017 por una vulnerabilidad en sistemas no parchados (EternalBlue – MS17-010).

---

#### 3. **Pérdida de datos o corrupción de información**

Software obsoleto puede generar errores, perder archivos o volverse incompatible con nuevos sistemas.

✅ _Ejemplo:_

Usas una base de datos antigua que ya no es compatible con versiones modernas de Windows. Tras una actualización forzada, deja de funcionar y pierdes registros de clientes.

---

#### 4. **Fuga de datos o robo de información sensible**

Las aplicaciones viejas suelen tener fallos en autenticación o cifrado.

✅ _Ejemplo:_

Un sistema web hecho en PHP 5.6 sigue usando cifrado débil (MD5) y expone contraseñas de clientes si hay una brecha.

---

#### 5. **Impacto económico y reputacional**

Una brecha de seguridad puede causar multas por no cumplir con normativas (como GDPR o Ley de Protección de Datos).

✅ _Ejemplo:_

Una empresa pierde la información de tarjetas de crédito de sus clientes. Se expone a denuncias, multas y pérdida de confianza.

---

### 🔧 ¿Cómo mantener un sistema empresarial actualizado? (Proceso de instalación de actualizaciones)

---

#### 🔹 Paso 1: **Identifica todo lo que debe actualizarse**

- Sistema operativo (Windows, Linux, macOS, etc.)
- Software de gestión (ERP, CRM, etc.)
- Base de datos (MySQL, PostgreSQL, SQL Server, Oracle)
- Antivirus y firewalls
- Aplicaciones web (WordPress, plugins, CMS, frameworks)
- Hardware y firmware (BIOS, impresoras, routers)

---

#### 🔹 Paso 2: **Consulta versiones y parches oficiales**

- Visita los sitios oficiales de cada software.
- Revisa si el sistema aún tiene **soporte activo** (EOL: End Of Life).
- Suscríbete a boletines de seguridad o feeds de CVE.

---

#### 🔹 Paso 3: **Aplica las actualizaciones en entorno de prueba**

Antes de actualizar en producción:

- Prueba primero en un entorno aislado (VM o copia del sistema).
- Verifica compatibilidades y funcionamiento.

---

#### 🔹 Paso 4: **Aplica parches en horarios de mantenimiento**

- Programa actualizaciones en horarios de baja actividad.
- Avisa al personal técnico y usuarios.

---

#### 🔹 Paso 5: **Documenta todo**

- Fecha, versión actualizada, responsable y resultados.
- Si usas herramientas como **WSUS**, **Ansible**, **PDQ Deploy**, automatiza el proceso.

---

### ✅ Ejemplo completo paso a paso: Peligro de no actualizar un sistema empresarial

---

#### 🏢 Escenario real:

Empresa "Contabilidad Lima SAC" usa Windows Server 2012 R2 para su sistema ERP.

---

#### 🔴 Problema:

No han aplicado actualizaciones desde 2021. En 2023, un atacante explota una vulnerabilidad RDP y cifra todos los archivos del servidor con **ransomware**.

---

#### ⚙️ Solución correcta:

##### Paso 1: Identificar el problema

- El antivirus detecta "ransomware.exe".
- El puerto RDP está expuesto (3389).
- No está instalado el parche **MS17-010** (EternalBlue).

##### Paso 2: Recuperación

- Afortunadamente, tienen una copia de seguridad externa.
- Formatean el servidor.
- Instalan **Windows Server 2022**.
- Migran el sistema ERP.

##### Paso 3: Prevención futura

- Activan actualizaciones automáticas.
- Instalan firewall y VPN para acceso remoto.
- Crean una política de mantenimiento mensual.

---

#### 🔐 Resultado:

El sistema ahora está actualizado, protegido y monitoreado.

---

### ✅ Recomendaciones finales

- Crea un **calendario mensual de mantenimiento**.
- Usa herramientas de auditoría como:

  - `Lansweeper`, `OpenVAS`, `Nessus` para ver software desactualizado.

- Automatiza actualizaciones con **WSUS** (Windows) o **Unattended Upgrades** (Linux).
- Mantén siempre **copias de seguridad offline**.

---

[🔼](#índice)

---

## **1015. Configura el control parental en los dispositivos de tu familia**

### 🧒 ¿Qué es el Control Parental?

El **control parental** es una funcionalidad que permite a los padres o tutores:

- Restringir el acceso a **contenidos inapropiados** (violencia, pornografía, apuestas).
- Establecer **horarios de uso** del dispositivo o internet.
- **Bloquear apps**, juegos o compras no autorizadas.
- **Monitorear** el uso del dispositivo.

Ideal para familias con niños o adolescentes que usan smartphones, tablets, computadoras o consolas.

---

### 🎯 ¿Por qué es importante el control parental?

- **Protección emocional**: Evita que menores accedan a contenido dañino.
- **Prevención del ciberacoso**: Puedes monitorear interacciones.
- **Evita adicción a pantallas**: Puedes limitar horas de uso.
- **Control de gastos**: Bloquea compras en apps o juegos.
- **Supervisión educativa**: Solo pueden usar apps aprobadas para tareas escolares.

---

### 🛠️ ¿Cómo se configura el control parental?

Vamos a ver **cómo se instala y configura** en los dispositivos más comunes:

---

#### ✅ 1. En Windows 10/11

##### 🔹 Paso 1: Crear cuentas para tus hijos

1. Ve a **Configuración > Cuentas > Familia y otros usuarios**.
2. Agrega una cuenta infantil (requiere un correo Microsoft).
3. Asegúrate de que esté marcada como **menor de edad**.

##### 🔹 Paso 2: Configurar control parental online

1. Ve a 👉 [https://account.microsoft.com/family](https://account.microsoft.com/family)
2. Inicia sesión con tu cuenta.
3. Desde aquí podrás:

   - Ver historial de actividad.
   - Restringir apps/juegos.
   - Establecer horarios por dispositivo.
   - Bloquear sitios web específicos.

##### 🔹 Paso 3: Activar filtros web y de tiempo

- En la opción **Exploración web**, activa:

  - "Filtrar sitios web inapropiados"
  - Agrega sitios permitidos/bloqueados.

- En **Tiempo frente a la pantalla**, define límites diarios.

---

#### ✅ 2. En Android (con Family Link)

##### 🔹 Paso 1: Instalar Family Link

1. Descarga **Google Family Link** desde Play Store en tu teléfono.
2. Crea o conecta una cuenta de Google infantil.
3. Vincula el dispositivo del niño con el tuyo.

##### 🔹 Paso 2: Configurar reglas

Desde tu celular (padre):

- Establece límites diarios de uso (ej. 2h al día).
- Bloquea apps no apropiadas.
- Controla contenido de YouTube.
- Ubica el dispositivo en tiempo real.
- Bloquea el dispositivo a distancia.

📌 _Requiere Android 7.0 o superior en el dispositivo del niño._

---

#### ✅ 3. En iPhone/iPad (iOS)

##### 🔹 Paso 1: Crear cuenta infantil

1. Ve a **Configuración > Tiempo en pantalla**.
2. Toca **Configurar “Tiempo en pantalla” para familia**.
3. Agrega a tu hijo con su Apple ID.

##### 🔹 Paso 2: Establecer restricciones

- Establece un código de acceso parental.
- En **Límites de uso**, bloquea apps después de ciertas horas.
- En **Restricciones de contenido y privacidad**, bloquea:

  - Webs para adultos.
  - Descargas de apps.
  - Contenido explícito de música o películas.

##### 🔹 Paso 3: Activar ubicación

Ve a **Compartir en familia > Compartir ubicación** para ver en tiempo real dónde está el dispositivo.

---

### ✅ Ejemplo completo: Familia con dos hijos

**Familia Torres** tiene dos hijos: Ana (10 años, usa Android) y Marcos (14 años, usa laptop con Windows 10).

---

#### 👨‍👩‍👧‍👦 Objetivo:

- Ana solo puede usar YouTube Kids 1h diaria.
- Marcos no debe jugar más de 2h en PC y no puede entrar a redes sociales.
- Ambos dispositivos deben apagarse a las 9:00 p.m.

---

#### 👣 Paso a paso:

##### 👧 En el Android de Ana:

1. Instalan **Family Link** en el teléfono del papá.
2. Crean una cuenta de Google infantil para Ana.
3. Vinculan su tablet al Family Link.
4. Activan límites:

   - 1 hora diaria.
   - Solo apps aprobadas (YouTube Kids, juegos educativos).
   - Apagado automático a las 9:00 p.m.
   - Bloquean YouTube normal y TikTok.

##### 👦 En la laptop con Windows de Marcos:

1. Desde Windows, crean cuenta infantil y la asocian al padre.
2. En [account.microsoft.com/family](https://account.microsoft.com/family), configuran:

   - 2h máximo en apps de videojuegos (Minecraft, Steam).
   - Bloquean redes sociales (Facebook, Instagram).
   - Filtro de sitios web inapropiados activado.
   - Horario de apagado: no se puede usar después de las 9:00 p.m.

##### 👨‍💻 Monitoreo:

- Los padres pueden ver desde su celular:

  - Cuánto tiempo usaron los dispositivos.
  - Qué apps abrieron.
  - Qué sitios web visitaron.
  - Y si intentaron violar alguna restricción.

---

### 🔒 Consejos adicionales

- Usa un **código PIN seguro** para evitar que los niños desactiven el control.
- Explica a tus hijos **por qué** se aplican estas restricciones.
- Revísalo **cada semana o mes**, ajusta límites según edad y comportamiento.
- Activa **verificación de compras** para evitar cargos no autorizados.

---

[🔼](#índice)

---

## **1016. ¿Por qué mantener los sistemas siempre actualizados?**

### 🔐 ¿Por qué es importante mantener los sistemas actualizados?

Actualizar un sistema (como Windows, Android, macOS, aplicaciones, navegadores, etc.) **no es solo para tener funciones nuevas**. Las actualizaciones son **fundamentales para la seguridad**.

#### ✅ Beneficios de mantener todo actualizado:

| Beneficio                                     | Explicación fácil                                                                                            |
| --------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| 🛡️ **Corrige fallos de seguridad**            | Los hackers descubren errores en los sistemas. Las actualizaciones los corrigen antes de que los aprovechen. |
| 🚀 **Mejora el rendimiento**                  | Muchas actualizaciones hacen que tu equipo funcione más rápido o consuma menos batería.                      |
| 🔧 **Arregla errores o “bugs”**               | Algunas fallas o cuelgues se deben a errores corregidos en versiones nuevas.                                 |
| 🧩 **Compatibilidad con nuevas apps**         | Las apps modernas a veces requieren el sistema actualizado para poder instalarse.                            |
| 🔒 **Protección contra malware y ransomware** | Muchos virus explotan sistemas antiguos para ingresar, como WannaCry en 2017.                                |

---

### ⚠️ ¿Qué pasa si no actualizas?

- Tu equipo queda vulnerable a **exploits** conocidos.
- Puedes ser víctima de **ransomware** (virus que secuestran tu información).
- Algunas apps dejarán de funcionar o no se instalarán.
- Tu sistema puede volverse lento o inestable.
- Podrías sufrir **filtraciones de datos personales o bancarios**.

---

### 🛠️ ¿Cómo mantener actualizado un sistema?

Veamos cómo se hace en los sistemas más comunes:

---

#### 💻 En Windows 10/11

1. **Ir a Configuración** → "Actualización y seguridad"
2. Clic en **Buscar actualizaciones**
3. Instala las actualizaciones disponibles y **reinicia** si es necesario
4. Activa las **actualizaciones automáticas** (recomendado)

> ✅ Consejo: Puedes programar las actualizaciones en horarios en los que no uses tu PC.

---

#### 📱 En Android

1. Ve a **Ajustes > Sistema > Actualización de software**
2. Pulsa **Buscar actualizaciones**
3. Si hay una disponible, toca **Descargar e instalar**
4. Algunos fabricantes (como Samsung o Xiaomi) tienen su propia opción de actualización

> ✅ Consejo: Conéctate a Wi-Fi y carga la batería antes de actualizar.

---

#### 🍎 En iPhone/iPad (iOS)

1. **Ajustes > General > Actualización de software**
2. Si hay una disponible, toca **Descargar e instalar**
3. Puedes activar las **actualizaciones automáticas**

---

#### 🌐 En navegadores (Chrome, Edge, Firefox)

- **Google Chrome**:

  - Haz clic en los tres puntos arriba a la derecha > Ayuda > Acerca de Google Chrome
  - Chrome se actualizará automáticamente si hay una versión nueva

- **Firefox**:

  - Menú > Ayuda > Acerca de Firefox
  - Se actualizará y pedirá reiniciar

- **Microsoft Edge**:

  - Igual que Chrome: configuración > Acerca de Microsoft Edge

---

### 🧪 Ejemplo completo

Imagina que **Carlos**, un contador, tiene su laptop con Windows 10 y no actualiza desde hace 1 año. Un día descarga un archivo PDF con un virus que **explota una vulnerabilidad que ya había sido parcheada por Microsoft**, pero él nunca instaló esa actualización.

Como resultado:

- El ransomware **cifra todos sus archivos** contables.
- Le piden \$500 en Bitcoin para recuperar la información.
- Pierde tiempo, dinero y reputación.

---

#### ✅ ¿Qué debió hacer Carlos?

1. Tener las actualizaciones automáticas activadas.
2. Verificar cada semana si había algo pendiente.
3. Instalar un antivirus actualizado.
4. Hacer **copias de seguridad** regularmente.

---

### 📌 Recomendaciones generales

| Acción                                      | Frecuencia                        |
| ------------------------------------------- | --------------------------------- |
| Verifica actualizaciones del sistema        | Cada semana o dejar en automático |
| Actualiza el navegador y antivirus          | Cada vez que se te notifique      |
| Revisa tus apps móviles                     | 1 vez por semana                  |
| Haz backup antes de una actualización mayor | Siempre                           |

---

### 🧰 Herramientas útiles

- 🪟 **Windows Update**
- 🔄 **WSUS Offline Update** (para entornos corporativos)
- 🔐 **Patch My PC** (actualiza programas de terceros)
- 📲 **Play Store / App Store** (para mantener apps móviles actualizadas)

---

[🔼](#índice)

---

## **1017. Restringir los permisos del sistema para limitar daños**

### 🔐 ¿Qué significa “restringir permisos del sistema”?

**Restringir permisos del sistema** significa **limitar lo que pueden hacer los usuarios y programas** en un sistema operativo. Así, si alguien hackea tu equipo o si un programa se comporta mal, **el daño será mínimo**, porque no podrá hacer cosas que no debería (como borrar todo tu disco o robar contraseñas).

---

### 🧠 ¿Por qué es importante?

| Riesgo común                                    | Solución con permisos restringidos                                                              |
| ----------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| Un virus borra archivos importantes             | Si el virus se ejecuta como usuario sin permisos elevados, no puede borrar archivos del sistema |
| Un usuario sin experiencia borra carpetas clave | Si ese usuario no tiene permisos administrativos, no puede hacerlo                              |
| Una app espía intenta acceder a tus documentos  | Si no tiene permisos de lectura sobre tu carpeta personal, no puede ver nada                    |

---

### 🎯 Objetivo

> **Tener control sobre quién puede hacer qué en el sistema.**

Esto aplica a:

- Usuarios (personas con cuentas)
- Programas (apps que corren en segundo plano)
- Archivos y carpetas (quién puede leer, escribir o ejecutar)

---

### 🛠️ ¿Cómo se hace? (Por sistema operativo)

---

#### 🔵 En **Windows**

##### Paso 1: Crea cuentas de usuario estándar

1. Ir a **Inicio > Configuración > Cuentas > Familia y otros usuarios**
2. Haz clic en **Agregar otra persona a este equipo**
3. Elige “No tengo la información de inicio de sesión”
4. Crear cuenta local > define un nombre y contraseña
5. En tipo de cuenta selecciona: **Estándar**

✅ Con esto, ese usuario **no podrá instalar programas ni cambiar configuraciones del sistema**.

---

##### Paso 2: Configura permisos en carpetas

1. Haz clic derecho en una carpeta > **Propiedades**
2. Ve a la pestaña **Seguridad**
3. Elige el usuario o grupo, y haz clic en **Editar**
4. Marca las opciones que deseas **negar** o permitir:

   - Leer
   - Escribir
   - Ejecutar

✅ Así puedes, por ejemplo, permitir que un usuario vea archivos pero **no pueda borrarlos ni editarlos**.

---

#### 🐧 En **Linux**

##### Paso 1: Crear un usuario sin privilegios

```bash
sudo adduser juan
```

Esto crea un usuario básico llamado `juan`.

##### Paso 2: No darle permisos sudo (administrador)

Asegúrate de que **NO esté en el grupo `sudo`**:

```bash
sudo deluser juan sudo
```

✅ Ahora, `juan` no puede instalar programas ni ejecutar comandos peligrosos con `sudo`.

---

##### Paso 3: Establecer permisos en archivos

Supón que tienes un archivo importante:

```bash
sudo chown root:root archivo.txt
sudo chmod 600 archivo.txt
```

- `chown root:root`: solo el administrador puede acceder
- `chmod 600`: solo el propietario (root) puede leer y escribir

✅ Si el usuario `juan` intenta acceder, recibirá un **"Permiso denegado"**.

---

### 🧪 Ejemplo práctico completo

Imagina que en una empresa pequeña, **Luz** es diseñadora y usa la PC solo para usar Photoshop. Tú eres el encargado de TI y quieres que:

1. **No pueda instalar programas**
2. **No borre archivos del sistema**
3. **Solo trabaje en su carpeta de trabajo**

---

#### 🔹 En Windows:

1. Le creas una cuenta estándar llamada `Luz`.
2. Configuras permisos para que solo pueda editar la carpeta `C:\DiseñosLuz`.
3. Aseguras las carpetas del sistema (`C:\Windows`, `C:\Archivos de programa`) para que estén en **solo lectura para ella**.

---

#### 🔹 En Linux:

1. Creas un usuario sin acceso a `sudo`:

   ```bash
   sudo adduser luz
   sudo deluser luz sudo
   ```

2. Solo le das acceso a `/home/luz/proyectos`:

   ```bash
   sudo chown luz:luz /home/luz/proyectos
   ```

3. Le quitas permisos de lectura a carpetas críticas:

   ```bash
   sudo chmod o-rx /etc /var /root
   ```

---

### 🔐 Herramientas útiles (Opcionales)

- 🔧 **AppArmor / SELinux** (Linux): Controlan qué puede hacer cada proceso
- 🔍 **Process Monitor** (Windows): Para ver permisos en tiempo real
- 🧱 **Política de grupo (GPO)**: Para administradores en entornos Windows Enterprise

---

### 📌 Consejos finales

| Recomendación                                               | Por qué                                        |
| ----------------------------------------------------------- | ---------------------------------------------- |
| No uses cuentas de administrador para uso diario            | Evitas errores graves o instalación de malware |
| No le des más permisos a los programas de los que necesitan | Menos superficie de ataque                     |
| Usa herramientas como antivirus y firewall                  | Complementan las restricciones de permisos     |
| Educa a los usuarios sobre su rol                           | Así no intentan hacer cosas que no deben       |

---

[🔼](#índice)

---

## **1018. Cómo identificar mensajes potencialmente inseguros**

### 🔍 ¿Qué es un mensaje potencialmente inseguro?

Un **mensaje potencialmente inseguro** es cualquier mensaje que pueda tener **una intención maliciosa**: robarte información, infectar tu dispositivo, engañarte para que hagas clic en un enlace peligroso o descargues algo dañino.

Estos mensajes pueden venir por:

- **Correo electrónico (phishing)**
- **SMS (smishing)**
- **WhatsApp, Telegram, Facebook Messenger, etc.**
- **Mensajes en páginas web**
- **Pop-ups o ventanas emergentes falsas**

---

### 🚨 Características típicas de mensajes peligrosos

| Característica                   | Ejemplo                                                                            |
| -------------------------------- | ---------------------------------------------------------------------------------- |
| ✅ Urgencia o amenaza            | “¡Tu cuenta será bloqueada en 24h!”                                                |
| 🧨 Ofertas demasiado buenas      | “¡Ganaste un iPhone gratis!”                                                       |
| 🕵️ Remitente falso               | “[Soporte@paypal.com](mailto:Soporte@paypal.com)” pero el verdadero correo es otro |
| 🔗 Enlaces sospechosos           | `http://paypal.seguro-cuenta.com` (no es oficial)                                  |
| 📎 Archivos adjuntos raros       | `factura.zip`, `reporte.exe`, `documento.scr`                                      |
| 👀 Errores ortográficos          | “Valla ahora mismmo a acivar su cuuenta”                                           |
| 🧱 Solicitud de datos personales | Piden usuario, clave, número de tarjeta, etc.                                      |

---

### 🛠️ ¿Cómo instalar una protección básica para detectar estos mensajes?

Aunque no se trata de una app específica, hay **herramientas y configuraciones que te ayudan** a protegerte y entrenarte para detectarlos:

#### En PC (Windows o Linux)

1. **Instala un antivirus confiable**
   Ejemplo: Avast, Bitdefender, Kaspersky, Windows Defender
   👉 Detecta enlaces maliciosos y archivos peligrosos

2. **Extensión para navegador como “Netcraft” o “Avira Browser Safety”**
   👉 Bloquea sitios falsos o phishing

3. **Configura Gmail/Outlook para filtrar correos sospechosos**

   - Activa filtros de spam
   - No marques correos legítimos como “No spam” si dudas

---

#### En Android o iOS

1. **Activa la detección de spam de SMS y llamadas**

   - Android: `Mensajes > Configuración > Protección contra spam`
   - iPhone: `Configuración > Mensajes > Filtro de mensajes desconocidos`

2. **Instala antivirus móvil**
   Ejemplo: Kaspersky Mobile, Norton Mobile, Avast Mobile

3. **No instales apps fuera de Google Play / App Store**

---

### ✅ Cómo analizar un mensaje (paso a paso)

Supongamos que recibes este mensaje por email:

> 🔔 “Hola, tu cuenta de Netflix ha sido suspendida. Para recuperarla, ingresa en el siguiente enlace e inicia sesión:
>
> [http://netflix.seguridad-clientes.com](http://netflix.seguridad-clientes.com)”

#### ¿Cómo detectas que es falso?

1. **Analiza el remitente:**
   ¿Es un correo como `soporte@netflix.com` o algo raro como `servicios@netflix-clientes.ru`?

2. **Revisa el enlace (sin hacer clic):**
   Pasa el mouse y verás que **no apunta al sitio real** (`netflix.com`) sino a otro dominio.

3. **Fíjate en el mensaje:**
   ¿Te presiona con urgencia? ¿Te amenaza con suspender la cuenta?

4. **Errores de redacción:**
   Mensajes oficiales casi nunca tienen errores ortográficos.

---

### 🧪 Ejemplo práctico completo

**Caso real simulado: Mensaje por WhatsApp**

> ✉️ “Hola, soy de soporte técnico de tu banco. Hemos detectado un ingreso no autorizado. Por favor, confirma tu identidad aquí:
>
> `http://bancoseguro-validacion.ga/login.php`”

**Análisis paso a paso:**

| Paso                | Verificación                                         |
| ------------------- | ---------------------------------------------------- |
| 1. ¿Quién lo envía? | Un número desconocido, no oficial                    |
| 2. ¿Qué pide?       | Que ingreses a un enlace y pongas tus datos          |
| 3. ¿Enlace raro?    | Termina en `.ga`, un dominio barato común en estafas |
| 4. ¿Sentido común?  | El banco nunca contacta por WhatsApp sin cita previa |

✅ **Conclusión:** es un intento de phishing. **NO debes ingresar a ese enlace.**

---

### 🔐 ¿Qué hacer si ya hiciste clic o diste datos?

1. **Cambia tus contraseñas de inmediato**
   especialmente de correo, banca y redes sociales.

2. **Activa la autenticación en dos pasos (2FA)**
   para proteger tus cuentas.

3. **Ejecuta un análisis con tu antivirus**
   para detectar si descargaste algo dañino.

4. **Llama a tu banco o entidad afectada**
   y **avísales que podrías haber sido víctima de fraude**.

---

### 🧠 Consejos finales para no caer en trampas

| Consejo                                               | Detalle                                           |
| ----------------------------------------------------- | ------------------------------------------------- |
| Siempre duda de mensajes con URGENCIA                 | “¡Actúa ahora!” suele ser trampa                  |
| No compartas tus claves por correo o chat             | Ninguna empresa seria lo pide                     |
| Verifica siempre el sitio web antes de ingresar datos | Comprueba que sea **https** y el dominio correcto |
| Usa gestores de contraseñas                           | Detectan sitios falsos                            |
| Activa 2FA en todas tus cuentas importantes           | Es tu última línea de defensa                     |

---

[🔼](#índice)

---

## **1019. Phishing: identifica los elementos que indican que un correo es falso**

### 🕵️‍♂️ ¿Qué es el Phishing?

**Phishing** es un tipo de ataque en el que un atacante **se hace pasar por una entidad confiable** (como un banco, red social, empresa, etc.) para engañarte y así obtener **información confidencial** como:

- Contraseñas
- Datos bancarios o de tarjetas
- Acceso a cuentas personales (Gmail, Facebook, etc.)

Generalmente llega en forma de:

- Correo electrónico
- SMS (→ Smishing)
- Llamadas telefónicas (→ Vishing)
- Redes sociales o sitios falsificados

---

### 📬 ¿Cómo reconocer un correo de phishing?

Aquí tienes los **elementos clave** que delatan que un correo puede ser falso:

| Elemento                           | Qué debes buscar                                   | Ejemplo sospechoso                   |
| ---------------------------------- | -------------------------------------------------- | ------------------------------------ |
| **Remitente**                      | Dirección extraña o mal escrita                    | `atencion@seguridad-bbva.cliente.ru` |
| **Saludo genérico**                | “Estimado usuario”, sin tu nombre                  | “Hola cliente”                       |
| **Mensaje urgente o de miedo**     | Amenazas: “tu cuenta será cerrada”                 | “¡Actúa ahora o perderás acceso!”    |
| **Errores ortográficos o raros**   | Mala gramática o traducción                        | “su cuenta a sideo suspndida”        |
| **Enlaces sospechosos**            | No apuntan al dominio oficial                      | `http://banco-cliente-validacion.ga` |
| **Archivos adjuntos no esperados** | `.zip`, `.exe`, `.scr` o documentos que no pediste | `Factura_Impuestos.scr`              |

---

### 🛠️ ¿Cómo protegerte desde tu dispositivo?

Aunque el phishing no “se instala” como un programa, sí puedes **instalar protecciones que te ayudan a detectarlo y evitar caer en la trampa**.

#### 🔒 En tu computadora

1. **Usa un buen navegador actualizado**

   - Google Chrome, Firefox, Brave o Edge detectan sitios falsos

2. **Activa la protección contra phishing**:

   - En Chrome:
     `Configuración > Privacidad y seguridad > Seguridad > Navegación segura (Protección mejorada)`

3. **Instala una extensión de seguridad**:

   - `Avira Browser Safety`, `Netcraft`, o `Bitdefender TrafficLight`

4. **Ten un antivirus actualizado**

   - Windows Defender, Avast, Kaspersky, Bitdefender

---

#### 📱 En tu móvil

1. **No abras enlaces raros en SMS o WhatsApp**

2. **Usa apps de seguridad como**:

   - `Norton 360`, `Avast Mobile`, `Bitdefender Mobile Security`

3. **Activa filtro de spam en correos y mensajes**

   - Gmail y Outlook lo tienen por defecto

---

### 🧪 Ejemplo completo de phishing analizado

Supón que recibes el siguiente correo:

---

#### ✉️ Asunto del correo:

**"⚠️ Tu cuenta de PayPal será suspendida si no verificas tu identidad"**

---

#### Cuerpo del mensaje:

> Estimado usuario,
>
> Hemos detectado actividad inusual en tu cuenta.
> Por favor verifica tu identidad para evitar el bloqueo de la cuenta.
>
> **Haz clic aquí para verificar**:
> [https://paypal.seguridad-cliente.com/confirmar](https://paypal.seguridad-cliente.com/confirmar)
>
> Atentamente,
> Equipo de Soporte de PayPal

---

#### 🕵️‍♂️ Análisis del phishing

| Elemento       | Análisis                                                                              |
| -------------- | ------------------------------------------------------------------------------------- |
| **Remitente**  | `seguridad@paypal-alerta.com` → No es el dominio oficial de PayPal (`paypal.com`)     |
| **Enlace**     | El dominio es falso: `paypal.seguridad-cliente.com`                                   |
| **Tono**       | Amenaza: “tu cuenta será suspendida”                                                  |
| **Saludo**     | Genérico: “Estimado usuario”                                                          |
| **Ortografía** | Aunque parece profesional, es una técnica para engañar                                |
| **Sitio web**  | Si abres el enlace (¡no lo hagas en la vida real!), es una copia de PayPal pero falsa |

---

#### ✅ ¿Qué hacer en este caso?

1. **No hacer clic** en el enlace
2. **Marcar como phishing** en tu correo (Gmail/Outlook lo permite)
3. **Eliminar el mensaje**
4. **Revisar tu cuenta directamente** desde el sitio oficial (`https://www.paypal.com`)
5. **Activar 2FA** (verificación en dos pasos) si aún no lo has hecho

---

### 🧠 Consejo final: Cómo comprobar si un enlace es seguro

Antes de hacer clic, **pasa el mouse encima del enlace** (hover) y observa en la esquina inferior izquierda del navegador **a dónde realmente apunta**.

Si no termina en el dominio **oficial** (por ejemplo, `paypal.com`, `bbva.pe`, `bcp.com.pe`, `facebook.com`), ¡**no ingreses tus datos** ahí!

---

[🔼](#índice)

---

## **1020. Uso seguro de ChatGPT**

### 🤖 ¿Qué es ChatGPT y por qué hablar de "uso seguro"?

ChatGPT es una inteligencia artificial que **procesa lenguaje natural**. Puedes pedirle que:

- Resuma textos
- Cree código
- Explique conceptos complejos
- Genere ideas o redacte contenido

🔐 Pero como cualquier herramienta digital, **debes usarla de forma responsable y segura**, sobre todo porque tú eres el que controla **qué compartes**.

---

### 🧠 ¿Por qué es importante el uso seguro?

ChatGPT **no accede a Internet ni recuerda lo que haces entre sesiones**, pero:

- Lo que escribes **puede ser revisado** por humanos para mejorar el modelo (si no desactivas esa opción).
- Si compartes **datos personales o confidenciales**, los estás exponiendo innecesariamente.
- Puedes recibir respuestas que **no siempre son 100% precisas** o actualizadas.

---

### 🔒 Buenas prácticas de uso seguro

Aquí tienes un resumen de cómo usar ChatGPT de forma **segura e inteligente**:

| Buenas prácticas ✅                                                                 | Malas prácticas ❌                                          |
| ----------------------------------------------------------------------------------- | ----------------------------------------------------------- |
| Evita poner tu DNI, número de tarjeta, contraseñas                                  | Escribir: “Mi contraseña es...”, “Mi cuenta bancaria es...” |
| Usa nombres ficticios si haces ejemplos sensibles                                   | Usar nombres reales de tus clientes o empresa sin permiso   |
| Revisa las respuestas antes de usarlas como verdad                                  | Copiar y pegar todo sin leer                                |
| Usa la función de borrar historial si es necesario                                  | Dejar historial activo en una computadora pública           |
| Verifica con fuentes oficiales si el tema es delicado (como salud, leyes, finanzas) | Tomar decisiones legales o médicas solo con ChatGPT         |

---

### 🧰 ¿Hay algo que instalar?

**No es necesario instalar nada** para usar ChatGPT. Solo necesitas:

1. Acceder desde tu navegador a:
   👉 [https://chat.openai.com](https://chat.openai.com)

2. Iniciar sesión con tu cuenta de Google, Microsoft o correo.

📱 También puedes **instalar la app oficial** en:

- [iOS (App Store)](https://apps.apple.com/app/chatgpt/id6448311069)
- [Android (Google Play)](https://play.google.com/store/apps/details?id=com.openai.chatgpt)

Solo asegúrate de que la app esté **publicada por OpenAI**. Nunca instales apps de terceros no verificadas.

---

### ✅ Ejemplo completo: Uso seguro de ChatGPT

#### 🎯 Supongamos este escenario:

Estás desarrollando un software de facturación para una empresa. Necesitas ayuda para crear una función en Python que calcule IGV y descuentos.

---

#### 🧾 Uso inseguro ❌

```plaintext
Hola, ChatGPT. Necesito ayuda. Estoy haciendo un software para la empresa Distribuidora Perú SAC. El RUC es 12345678910 y el correo del gerente es ricardo@empresa.com. ¿Me puedes ayudar a calcular el IGV de una factura?
```

**Problemas:**

- Mencionas el nombre real de la empresa
- Incluyes el RUC y correo personal
- Innecesario para que la IA te ayude

---

#### ✅ Uso seguro y profesional

```plaintext
Hola, ChatGPT. Estoy desarrollando un sistema de facturación en Python para una empresa ficticia. ¿Puedes ayudarme con una función que calcule el total con IGV del 18% y un posible descuento del 10% si el total supera 500 soles?
```

**Ventajas:**

- No revelas información real o confidencial
- El prompt es claro, técnico y específico
- Obtienes el mismo resultado sin exponer a nadie

---

#### 🔐 Cómo desactivar el historial de entrenamiento

Si no quieres que tus conversaciones sean revisadas por OpenAI para mejorar el modelo:

1. Ve a [https://chat.openai.com](https://chat.openai.com)
2. Clic en tu nombre (abajo a la izquierda) → `Configuración (Settings)`
3. En la pestaña `Datos (Data Controls)` → Desactiva **"Chat History & Training"**

Esto evitará que tus chats se usen para entrenar futuros modelos.

---

### 🧠 Consejos finales para uso seguro

1. **No confíes ciegamente**: Verifica datos importantes con otras fuentes.
2. **No compartas datos personales**: Ni tuyos ni de otros.
3. **Aprende y experimenta con conciencia**: ChatGPT es un gran apoyo, pero **tú tienes el control**.

---

[🔼](#índice)

---

## **1021. La ciberseguridad es grupal**

### 🛡️ ¿Qué significa que _la ciberseguridad es grupal_?

Cuando hablamos de ciberseguridad, muchas personas creen que es **solo responsabilidad del área de TI** o de una persona “experta”. **Pero no es así**. En realidad:

> **La ciberseguridad es tarea de todos.**

Desde el **usuario común** que abre un correo, hasta el **director de una empresa** que guarda documentos sensibles. Todos deben asumir prácticas responsables para evitar ataques como:

- Ransomware
- Phishing
- Fugas de datos
- Robo de identidad

---

### 🧠 ¿Por qué debe ser grupal y no individual?

| Individualmente 🧍‍♂️                         | Grupales 👥                                |
| ------------------------------------------ | ------------------------------------------ |
| Solo una persona se cuida                  | Todos colaboran activamente                |
| Riesgo alto si alguien comete un error     | Riesgo menor porque se vigilan entre todos |
| Nadie se da cuenta de un problema a tiempo | El equipo puede detectar anomalías rápido  |
| No hay cultura de seguridad                | Se refuerzan buenas prácticas en el grupo  |

> **Ejemplo real**: Si un empleado hace clic en un archivo malicioso, todo el sistema de la empresa puede quedar comprometido, aunque los técnicos sean expertos.

---

### 🔧 ¿Cómo se “instala” esta mentalidad de seguridad grupal?

No se instala como un programa, pero sí se puede **integrar en la cultura** de un grupo o familia con **buenas prácticas como estas**:

#### 🏢 En una empresa:

1. **Capacitación continua**: Todos deben saber identificar correos sospechosos.
2. **Simulacros de phishing**: Se lanzan pruebas para ver si los empleados caen.
3. **Políticas claras**: Qué hacer si ocurre una brecha, cómo crear contraseñas, etc.
4. **MFA obligatorio**: Autenticación en dos pasos para todos.
5. **Seguridad por defecto**: Computadoras bloqueadas automáticamente, permisos limitados.

#### 🏡 En la familia:

1. **Control parental activo**
2. **Hablar con los hijos** sobre los riesgos de dar su información
3. **Configurar antivirus y contraseñas seguras**
4. **Enseñar a reconocer sitios web falsos**
5. **No compartir dispositivos sin protección**

---

### ✅ Ejemplo completo y práctico

#### 🏠 Escenario: Familia segura en casa

**Personajes:**

- _Ana_ (mamá, trabaja desde casa)
- _Carlos_ (papá, revisa su banca online)
- _Lucas_ (hijo de 13 años, juega y usa redes)
- _Mía_ (hija de 8 años, mira videos en YouTube)

#### 🛡️ Buenas prácticas que implementan:

1. **Ana** activa el **firewall de Windows** y usa una VPN para trabajar.
2. **Carlos** activa **doble factor de autenticación** en su banco y no guarda contraseñas en el navegador.
3. **Lucas** recibe una charla mensual de sus padres sobre **ciberacoso y grooming**. Tiene una app de control como Qustodio.
4. **Mía** solo accede a YouTube Kids con supervisión y con restricciones de tiempo.
5. Todos usan **un antivirus actualizado** y no descargan software de sitios desconocidos.

#### 💡 Resultado:

Si Lucas recibe un mensaje extraño en un juego online, **ya sabe que debe avisar**. Si Ana recibe un correo raro, **lo reporta antes de hacer clic**. Si Carlos se conecta desde una red pública, **usa la VPN**. Cada uno **protege al grupo entero con su acción**.

---

### 🧠 Conclusión

> La ciberseguridad grupal no se trata solo de tecnología, sino de **educación, comunicación y compromiso compartido**.

Todos debemos ser responsables y conscientes. No importa si somos usuarios básicos, desarrolladores o padres de familia. **Un error de uno puede afectar a todos**.

---

[🔼](#índice)

---

| **Inicio**         | **atrás 19**                                         | **Siguiente 21**                                                                  |
| ------------------ | ---------------------------------------------------- | --------------------------------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./7_19_Hacking_Aplicaciones_Web_Server_Side.md) | [⏩](./7_21_Introduccion_a_la_Ingenieria_Social_Tecnicas_Ataques_y_Pretexting.md) |
