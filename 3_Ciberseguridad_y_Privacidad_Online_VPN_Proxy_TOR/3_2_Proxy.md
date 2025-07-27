| **Inicio**         | **atrás 1**                                | **Siguiente 3**        |
| ------------------ | ------------------------------------------ | ---------------------- |
| [🏠](../README.md) | [⏪](./3_1_VPN_Virtual_Private_Network.md) | [⏩](./3_3_Red_TOR.md) |

---

## **Índice**

| Temario                                                                                            |
| -------------------------------------------------------------------------------------------------- |
| [109. ¿Qué es un Proxy?](#109-qué-es-un-proxy)                                                     |
| [110. Funcionamiento y configuración de un Proxy](#110-funcionamiento-y-configuración-de-un-proxy) |
| [111. Análisis del tráfico Proxy](#111-análisis-del-tráfico-proxy)                                 |
| [112. ¿Qué es Socksv4 y Socksv5?](#112-qué-es-socksv4-y-socksv5)                                   |
| [113. Privoxy](#113-privoxy)                                                                       |
| [114. Proxy Web - ProxySite](#114-proxy-web---proxysite)                                           |
| [115. ProxyChains](#115-proxychains)                                                               |

---

# **Proxy**

## **109. ¿Qué es un Proxy?**

![proxy](../img/3_Ciberseguridad_y_Privacidad_Online_VPN_Proxy_TOR/proxy.png "proxy")

Un **proxy** es un **servidor intermedio** que se coloca entre **tu dispositivo** e **Internet**.

✅ Tú → Proxy → Internet

En lugar de conectarte directamente a un sitio web, **te conectas al proxy**, y **el proxy hace la petición por ti**.

---

✅ **Metáfora sencilla:**

> Imagínate que en vez de hablar directo con alguien, le pasas un mensaje a un amigo, y él lo entrega por ti. Nadie sabe que tú eres el que pidió el mensaje.

---

### ✅ ¿Para qué sirve un proxy?

✅ Cambiar tu dirección IP.

✅ Acceder a contenido bloqueado por región.

✅ Filtrar o monitorear tráfico (en empresas).

✅ Mejorar velocidad con caché (almacenando páginas visitadas).

✅ Control parental o filtrado de contenido.

✅ Proteger privacidad (ocultar IP real del destino).

---

✅ **Ejemplo práctico:**

- Quieres entrar a un sitio bloqueado en tu país.
- Configuras un proxy en otro país.
- El sitio web cree que estás en ese otro país.

---

### ✅ ¿Cómo funciona? (explicación fácil)

✅ Sin proxy:

```
Tú → Internet
```

- Tu dirección IP real llega al sitio web.
- El sitio web te responde directamente.

---

✅ Con proxy:

```
Tú → Proxy → Internet
```

- Tú le mandas la solicitud al proxy.
- El proxy la envía al sitio web usando SU dirección IP.
- El sitio web responde al proxy.
- El proxy te devuelve la respuesta.

---

✅ **Resultado:**

- El sitio web nunca ve tu IP real.
- Ve la IP del proxy.

---

✅ **Ejemplo sencillo:**

- Estás en Perú.
- Usas un proxy en EE. UU.
- Quieres ver un video solo disponible en EE. UU.
- El sitio web ve la IP del proxy (en EE. UU.) y te deja verlo.

---

### ✅ Tipos de proxies

✅ ⭐ HTTP Proxy:

- Solo para tráfico web (HTTP/HTTPS).
- Fácil de usar en navegadores.

✅ ⭐ SOCKS Proxy:

- Más versátil.
- Soporta más tipos de tráfico (correo, torrents, etc.).
- Ejemplo popular: SOCKS5.

✅ ⭐ Transparente Proxy:

- El usuario no se da cuenta.
- Usado por empresas o escuelas para filtrar contenido.

✅ ⭐ Reverse Proxy:

- Usado por servidores → para balancear carga o proteger backends.
- Ejemplo: NGINX como reverse proxy.

---

### ✅ Ventajas y limitaciones

✅ ⭐ Ventajas:

✅ Cambia tu IP.

✅ Puede saltar bloqueos geográficos.

✅ Puede mejorar velocidad (caché).

✅ Útil para filtrado o control.

✅ ⚠️ Limitaciones:

❌ No cifra tráfico por defecto (¡no es VPN!).

❌ El operador del proxy puede ver tu tráfico.

❌ No protege todo tu sistema (solo apps configuradas).

❌ Puede ser lento si está saturado.

---

### ✅ Ejemplo súper sencillo

✅ Imagínate:

**Sin proxy:**

- Tu PC (IP: 190.12.34.56) → google.com
- Google ve IP: 190.12.34.56

**Con proxy en Francia:**

- Tu PC → Proxy (IP: 89.45.23.1 en Francia) → google.com
- Google ve IP: 89.45.23.1
- Cree que estás en Francia.

---

### ✅ Cómo se instala y usa un proxy (paso a paso sencillo)

#### ⭐ Opción A: En el navegador (más fácil)

✅ Ejemplo en Google Chrome:

1️⃣ Abre Chrome.

2️⃣ Ve a **Configuración** → Avanzada → Sistema → Abrir configuración de proxy de tu sistema.

3️⃣ En Windows → se abre "Opciones de Internet".

4️⃣ En la pestaña **Conexiones**, haz clic en **Configuración de LAN**.

5️⃣ Marca **Usar servidor proxy para la LAN**.

6️⃣ Escribe la IP y el puerto del proxy (ejemplo: 123.45.67.89:8080).

7️⃣ Guarda los cambios.

✅ Resultado:

- Todo el tráfico web en ese navegador pasa por el proxy.

---

✅ Ejemplo práctico de IP de proxy:

```
IP: 192.168.1.100
Puerto: 8080
```

---

✅ **En Firefox (aún más fácil):**

1️⃣ Abre Firefox.

2️⃣ Ve a **Preferencias / Opciones**.

3️⃣ Busca **Configuración de red**.

4️⃣ Haz clic en **Configurar conexión**.

5️⃣ Marca **Configuración manual del proxy**.

6️⃣ Escribe la IP y puerto.

7️⃣ Acepta.

---

#### ⭐ Opción B: En Windows para todo el sistema

✅ Windows 10/11:

1️⃣ Ve a **Configuración** → **Red e Internet** → **Proxy**.

2️⃣ Activa **Usar un servidor proxy**.

3️⃣ Escribe la dirección y el puerto.

4️⃣ Guarda.

✅ Resultado:

- Todo el tráfico del sistema (que respete la configuración de proxy) pasa por ahí.

---

#### ⭐ Opción C: En Linux

✅ Método sencillo usando variables de entorno (terminal):

```
export http_proxy="http://IP:PUERTO"
export https_proxy="http://IP:PUERTO"
```

✅ Ejemplo:

```
export http_proxy="http://192.168.1.100:8080"
```

✅ Aplica a herramientas en la terminal que usen estas variables.

---

✅ O en navegadores (igual que en Windows → editas la configuración de red).

---

### ✅ Resumen súper claro

⭐ **Proxy = intermediario entre tú e Internet**.

✅ Oculta tu IP real.

✅ Puede desbloquear contenido geográfico.

✅ Puede filtrar o almacenar en caché contenido.

✅ No cifra por defecto → menos seguro que una VPN.

✅ Fácil de configurar en navegadores o sistema.

---

✅ **Metáfora para recordar:**

> Un proxy es como **un mensajero** que entrega tus cartas. La gente ve su dirección, no la tuya.

---

[🔼](#índice)

---

## **110. Funcionamiento y configuración de un Proxy**

### ✅ ¿Qué es un proxy? (breve recordatorio)

Un **proxy** es un **servidor intermedio** entre tu dispositivo e Internet.

✅ Tú → Proxy → Internet

⭐ En lugar de conectarte directamente a un sitio web, **le pides al proxy que lo haga por ti**.
⭐ El sitio web ve la IP del proxy, no la tuya.

---

✅ **Metáfora sencilla:**

> Es como pedirle a un amigo que compre algo por ti en la tienda. La tienda ve a tu amigo, no a ti.

---

### ✅ ¿Cómo funciona un proxy? (explicación clara)

✅ Flujo básico:

1️⃣ Tu computadora se conecta al **servidor proxy**.

2️⃣ Le dice: “Por favor, tráeme la página web X”.

3️⃣ El proxy se conecta a la página web.

4️⃣ La descarga.

5️⃣ Te la devuelve.

✅ Resultado:

- El sitio web ve la IP del proxy.
- Tu IP real está oculta.
- A veces, el proxy almacena la página (caché) para hacerla más rápida la próxima vez.

---

✅ **Ejemplo fácil:**

- Estás en Perú.
- Configuras un proxy en EE. UU.
- Accedes a Hulu, que solo está disponible en EE. UU.
- Hulu ve la IP del proxy (en EE. UU.) y te deja entrar.

---

✅ **Diagrama súper sencillo:**

```
[Tu PC] -> [Proxy] -> [Internet]
```

---

### ✅ Tipos de Proxy

✅ ⭐ HTTP Proxy

- Solo para tráfico web (HTTP/HTTPS).
- Ideal para navegadores.

✅ ⭐ SOCKS Proxy

- Más versátil.
- Maneja más protocolos (correo, torrents, etc.).
- Muy usado en Tor (SOCKS5).

✅ ⭐ Transparente Proxy

- El usuario no se entera.
- Usado por escuelas o empresas para filtrar contenido.

✅ ⭐ Reverse Proxy

- Usado por servidores para balanceo de carga o seguridad (ejemplo: NGINX).

---

### ✅ Ventajas del proxy

✅ Oculta tu IP.

✅ Puede desbloquear contenido restringido por región.

✅ Puede filtrar contenido (control parental).

✅ A veces acelera carga de páginas (caché).

✅ En empresas → permite monitorear tráfico.

---

✅ **Pero ojo:**

❌ No cifra el tráfico (a diferencia de una VPN).

❌ El dueño del proxy puede ver lo que haces si no es HTTPS.

---

### ✅ Ejemplo súper fácil

✅ Sin Proxy:

```
Tú (IP: 190.20.30.40) -> YouTube
```

→ YouTube ve IP: 190.20.30.40

✅ Con Proxy en EE. UU.:

```
Tú -> Proxy (IP: 34.56.78.90 en EE. UU.) -> YouTube
```

→ YouTube ve IP: 34.56.78.90

✅ Resultado:

- YouTube cree que estás en EE. UU.

---

### ✅ Configuración de un Proxy paso a paso

Aquí viene la parte **práctica y detallada**, según tu sistema:

---

#### ⭐ A) En Windows 10/11

✅ Paso 1: Abre **Configuración**

→ Inicio → Configuración (ícono de engranaje).

✅ Paso 2: Ve a **Red e Internet**

→ En el menú izquierdo, elige **Proxy**.

✅ Paso 3: Activa **Usar un servidor proxy**.

✅ Paso 4: Ingresa:

- Dirección IP del proxy.
- Puerto.

✅ Ejemplo:

```
Dirección: 123.45.67.89
Puerto: 8080
```

✅ Paso 5: Guarda y cierra.

✅ Resultado:

- Todo el tráfico del sistema que respete la configuración usará ese proxy.

---

#### ⭐ B) En macOS

✅ Paso 1: Preferencias del Sistema → Red.

✅ Paso 2: Selecciona tu conexión activa (Wi-Fi o Ethernet).

✅ Paso 3: Haz clic en **Avanzado** → pestaña **Proxies**.

✅ Paso 4: Marca **Web Proxy (HTTP)** o **Secure Web Proxy (HTTPS)**.

✅ Paso 5: Ingresa IP y puerto.

✅ Paso 6: Aceptar → Aplicar.

---

#### ⭐ C) En Linux (Ubuntu/GNOME)

✅ Paso 1: Configuración → Red.

✅ Paso 2: Proxy de red.

✅ Paso 3: Elige **Manual**.

✅ Paso 4: Ingresa IP y puerto para HTTP, HTTPS, SOCKS según lo necesites.

✅ Paso 5: Guarda.

✅ Resultado:

- Aplicaciones que respeten la configuración del sistema usarán el proxy.

---

✅ También puedes configurarlo en la terminal:

```
export http_proxy="http://IP:PUERTO"
export https_proxy="http://IP:PUERTO"
```

✅ Ejemplo:

```
export http_proxy="http://123.45.67.89:8080"
```

---

#### ⭐ D) En navegador (Chrome/Firefox)

✅ Muy útil si solo quieres el proxy para navegar.

---

✅ **Google Chrome (usa la configuración del sistema):**

- Chrome → Configuración → Avanzada → Sistema → Abrir configuración de proxy.
- Te lleva a la configuración de Windows/Mac descrita arriba.

---

✅ **Mozilla Firefox (más flexible):**

✅ Paso 1: Abrir Firefox.

✅ Paso 2: Menú → Opciones/Preferencias.

✅ Paso 3: Buscar **Configuración de red** → **Configurar conexión**.

✅ Paso 4: Seleccionar **Configuración manual del proxy**.

✅ Paso 5: Ingresar IP y puerto.

✅ Paso 6: Guardar.

✅ Resultado:

- Solo Firefox usará ese proxy.

---

✅ **Ejemplo práctico:**

```
IP del proxy: 123.45.67.89
Puerto: 8080
```

→ Lo escribes y listo.

---

### ✅ Nota sobre autenticación

✅ Algunos proxies requieren usuario y contraseña.

✅ Al configurar, verás campos para ingresar esas credenciales.

✅ Ejemplo:

```
IP: 123.45.67.89
Puerto: 8080
Usuario: miusuario
Contraseña: miclave
```

---

### ✅ Resumen súper claro

⭐ **Proxy = servidor intermedio.**

✅ Oculta tu IP real.

✅ Ayuda a saltar bloqueos geográficos.

✅ Filtra o controla tráfico.

✅ A veces acelera la navegación (caché).

⚠️ **No cifra por defecto.**

⚠️ El proxy puede ver tu tráfico si no usas HTTPS.

✅ **Configuración fácil:**

⭐ En Windows/Mac/Linux → Ajustes de Red → Proxy → IP y Puerto.

⭐ En navegadores → Preferencias → Red → Configurar Proxy.

---

✅ **Metáfora para recordar:**

> Un proxy es **como un mensajero**: lleva y trae tus mensajes. La gente ve al mensajero, no a ti.

---

[🔼](#índice)

---

## **111. Análisis del tráfico Proxy**

### ✅ ¿Qué significa “análisis del tráfico Proxy”?

⭐ Es **inspeccionar** y **entender** los datos que pasan **entre tu dispositivo y el proxy** o **entre el proxy y el destino final en Internet**.

✅ En otras palabras:

- Ver qué se envía y recibe a través del proxy.
- Ver URLs, encabezados HTTP, contenido, etc.

✅ El análisis de tráfico proxy es **útil para**:

- Seguridad → detectar ataques.
- Depuración → ver si el proxy funciona bien.
- Control → bloquear contenido no deseado.
- Aprendizaje → entender cómo viajan los datos en la red.

---

✅ **Metáfora sencilla:**

> Imagínate que el proxy es un **cartero**. Analizar el tráfico es **abrir y leer las cartas** para ver qué contienen.

---

### ✅ ¿Para qué sirve analizar tráfico de proxy?

✅ Usos comunes:

⭐ Seguridad:

- Ver si alguien filtra información confidencial.
- Detectar malware usando el proxy para comunicarse.

⭐ Depuración:

- Ver por qué un servicio falla.
- Ver si el proxy altera solicitudes.

⭐ Monitoreo:

- Control parental.
- Políticas de empresa.

⭐ Aprendizaje:

- Estudiar cabeceras HTTP.
- Ver cómo funcionan cookies y sesiones.

---

✅ **Ejemplo fácil:**

- Una app envía datos a través de un proxy.
- Inspeccionas el tráfico → descubres que manda la contraseña en texto plano.

---

### ✅ ¿Cómo funciona el análisis del tráfico proxy?

✅ Es interceptar y **capturar** los paquetes de red.

✅ Decodificar su contenido → ver qué dicen.

✅ Requiere que tu herramienta esté:

- Entre el cliente y el proxy.
- O en el mismo dispositivo, capturando salidas.
- O en el servidor proxy mismo.

✅ Proxies HTTP permiten **leer** y hasta **modificar** tráfico HTTP.

✅ Proxies HTTPS (con TLS) requieren técnicas de _interceptación SSL_ (como mitmproxy).

---

✅ **Flujo sencillo:**

```
[Cliente] --> [Proxy] --> [Internet]
```

✅ Analizas:

- Cliente <-> Proxy
- Proxy <-> Servidor final

---

✅ **Diagrama con análisis:**

```
Cliente -> Proxy -> Sitio
 \         |         /
  \__Sniffer o Proxy Interceptador__/
```

---

### ✅ Ejemplo súper sencillo de la vida real

✅ Imagínate:

⭐ Usas un proxy en el trabajo.

⭐ Quieres ver si está espiando tus datos.

⭐ Capturas tráfico → ves:

```
GET /login
Host: example.com
username=juan&password=12345
```

✅ ¡Está en claro!
→ Descubres que deberías usar HTTPS o VPN.

---

### ✅ Herramientas para analizar tráfico de proxy

✅ ⭐ Wireshark

- Captura TODO el tráfico en la red.
- Decodifica protocolos.
- Gráfica, amigable.

✅ ⭐ mitmproxy

- Actúa como proxy interceptador.
- Ve solicitudes/respuestas HTTP y HTTPS.
- Puede modificar tráfico.

✅ ⭐ Fiddler

- Proxy para Windows/Mac.
- Muy usado para depuración web.
- Soporta HTTPS.

✅ ⭐ Burp Suite

- Usado en ciberseguridad.
- Intercepta y modifica tráfico web.
- Muy completo.

✅ ⭐ tcpdump

- Terminal.
- Más técnico.
- Para capturas rápidas.

---

### ✅ Instalación y uso paso a paso

Vamos con **dos herramientas populares y gratuitas**:

---

#### ⭐ A) Análisis de tráfico Proxy con Wireshark

✅ Objetivo:

Ver TODO el tráfico, incluyendo tráfico hacia el proxy.

---

✅ **PASO 1: Instalar Wireshark**

🔹 Windows:

- Descarga desde [wireshark.org](https://www.wireshark.org/download.html).
- Instala siguiendo el asistente.

🔹 Linux:

```bash
sudo apt update
sudo apt install wireshark
```

---

✅ **PASO 2: Elegir la interfaz**

- Abre Wireshark.
- Elige la interfaz de red (Wi-Fi o Ethernet).

✅ Ejemplo:

```
eth0
wlan0
```

---

✅ **PASO 3: Capturar tráfico**

- Haz clic en **Start Capture**.
- Navega en el navegador configurado con el proxy.

✅ Resultado:

- Wireshark capturará paquetes hacia/desde el proxy.

---

✅ **PASO 4: Filtrar tráfico**

Usa filtros para ver solo el proxy:

✅ Por IP del proxy:

```
ip.addr == 123.45.67.89
```

✅ Por puerto (ejemplo: 8080):

```
tcp.port == 8080
```

---

✅ **PASO 5: Analizar contenido**

- Haz clic en un paquete.
- Ve **Detalles**:

  - Método HTTP.
  - Headers.
  - Datos enviados.

✅ Ejemplo:

```
POST /login HTTP/1.1
Host: proxyserver.com
Content-Type: application/x-www-form-urlencoded

username=juan&password=12345
```

---

✅ **Conclusión con Wireshark:**

- Viste todo lo que viaja hacia el proxy.
- Útil para ver si datos sensibles viajan en claro.

---

#### ⭐ B) Análisis de tráfico Proxy con mitmproxy

✅ Objetivo:

Ser **el proxy** y ver (¡o modificar!) tráfico.

---

✅ **PASO 1: Instalar mitmproxy**

🔹 Windows/Mac/Linux (con Python):

```
pip install mitmproxy
```

✅ En Linux (Ubuntu):

```
sudo apt install mitmproxy
```

---

✅ **PASO 2: Ejecutar mitmproxy**

Para interceptar HTTP:

```
mitmproxy
```

✅ Por defecto escucha en el puerto 8080.

---

✅ **PASO 3: Configurar navegador o app**

- Ajustes → Proxy Manual.
- Dirección: `localhost`
- Puerto: `8080`

✅ Resultado:

- Todo tu tráfico web pasará por mitmproxy.

---

✅ **PASO 4: Ver tráfico en mitmproxy**

- Abre el navegador.
- Accede a sitios web.
- En la terminal de mitmproxy verás:

  - Métodos HTTP (GET, POST).
  - URLs.
  - Headers.
  - Body (contenido enviado).

---

✅ **PASO 5: HTTPS (opcional avanzado)**

✅ mitmproxy puede interceptar HTTPS **con su certificado**:

1️⃣ Ejecuta:

```
mitmproxy --mode regular
```

2️⃣ Visita:

```
http://mitm.it
```

3️⃣ Descarga e instala el certificado en el navegador.

4️⃣ Ahora también ves tráfico HTTPS.

✅ Resultado:

- Puedes analizar TODO → incluso tráfico cifrado (si el cliente acepta el certificado).

---

✅ **Ejemplo práctico con mitmproxy:**

```
→ Cliente solicita: GET /search?q=proxy
→ Proxy mitmproxy muestra:
Host: google.com
Path: /search?q=proxy
Headers: User-Agent, Cookies
```

---

✅ **Ventaja de mitmproxy:**

⭐ No solo ves → puedes modificar tráfico en tiempo real.

⭐ Perfecto para aprender seguridad web.

---

### ✅ Resumen súper claro

✅ **Análisis de tráfico proxy = ver qué datos pasan entre tú y el proxy, o entre proxy y destino.**

✅ Sirve para:

⭐ Seguridad.

⭐ Monitoreo.

⭐ Aprendizaje.

⭐ Depuración.

✅ Herramientas:

⭐ Wireshark → captura general de red.

⭐ mitmproxy → intercepta como proxy, muestra y modifica tráfico.

✅ **Instalación súper sencilla:**

✅ Wireshark:

```
sudo apt install wireshark
```

✅ mitmproxy:

```
pip install mitmproxy
```

✅ **Configuración súper sencilla:**

- En navegador → configura proxy en localhost:8080 para mitmproxy.
- En Wireshark → selecciona interfaz y aplica filtro por puerto o IP.

---

✅ **Metáfora para recordar:**

> Analizar tráfico proxy es como **leer la conversación entre el mensajero y la tienda**, para saber exactamente qué están diciendo.

---

[🔼](#índice)

---

## **112. ¿Qué es Socksv4 y Socksv5?**

### ✅ ¿Qué es SOCKS?

⭐ SOCKS es un **protocolo de proxy**.

✅ Su nombre viene de “**SOCKet Secure**”.

✅ Permite enviar tu tráfico de Internet **a través de un servidor proxy**.

✅ Es más versátil que un proxy HTTP → funciona con **cualquier protocolo** (no solo HTTP/HTTPS).

---

✅ **Metáfora sencilla:**

> Es como **un túnel universal** que lleva _cualquier cosa_ que quieras mandar o recibir.

---

✅ **Flujo básico:**

```
Tu PC → Proxy SOCKS → Internet
```

- Tu computadora se conecta al servidor SOCKS.
- El servidor SOCKS reenvía tus datos al destino.
- El destino solo ve la IP del servidor SOCKS.

✅ Resultado:

- Tu IP real queda oculta.
- Puedes “aparecer” en otro país.

---

### ✅ SOCKSv4 y SOCKSv5: ¿Cuál es la diferencia?

SOCKS tiene dos versiones principales:

---

#### ⭐ A) SOCKS v4

✅ Versión más antigua.

✅ Muy simple.

✅ Solo soporta tráfico TCP.

✅ No tiene autenticación avanzada.

✅ No soporta IPv6.

✅ No soporta UDP.

✅ **Ejemplo de uso:**

- Reenviar conexiones web simples.
- Descargas por HTTP.

---

✅ **Metáfora:**

> SOCKSv4 es como un túnel recto y básico, sin puertas ni candados.

---

#### ⭐ B) SOCKS v5

✅ Es la versión mejorada y más usada hoy.

✅ Soporta:

⭐ Autenticación (usuario/contraseña).

⭐ Resolución de DNS en el servidor.

⭐ Tráfico TCP **y** UDP.

⭐ IPv6.

✅ **Ventajas importantes:**

⭐ Evitar filtrado DNS local.

⭐ Soportar apps como torrents o videojuegos (que usan UDP).

⭐ Acceso más seguro con contraseña.

---

✅ **Metáfora:**

> SOCKSv5 es como un túnel moderno con **puertas con llave**, **señalización para distintos caminos (TCP/UDP)** y **direcciones precisas (DNS)**.

---

### ✅ ¿Para qué sirve SOCKS en la práctica?

✅ Ocultar tu IP real.

✅ Saltar bloqueos geográficos.

✅ Evitar censura.

✅ Proteger privacidad al redireccionar tráfico.

✅ Usar apps que no funcionan con proxies HTTP.

---

✅ **Ejemplos fáciles:**

⭐ Configurar un navegador para navegar como si estuvieras en otro país.

⭐ Configurar un cliente de torrent para que use el proxy y oculte tu IP real.

⭐ Usar SSH con SOCKS para crear un túnel seguro.

---

### ✅ Ejemplo súper sencillo

✅ Tú estás en Perú.

✅ Usas un servidor SOCKSv5 en Alemania.

✅ Configuras tu navegador o app para usarlo.

✅ Todo el tráfico pasa por el servidor SOCKS.

✅ Resultado:

- Los sitios web creen que estás en Alemania.
- Tu IP peruana queda oculta.

---

✅ Diagrama fácil:

```
Tu PC → Servidor SOCKS (Alemania) → Internet
```

---

✅ **Con DNS remoto (SOCKSv5):**

- Incluso las búsquedas de dominio (como "google.com") las hace el servidor SOCKS.
- Tu ISP no ve ni siquiera los dominios que visitas.

---

### ✅ Resumen de diferencias SOCKSv4 vs SOCKSv5

| Característica | SOCKSv4 | SOCKSv5 |
| -------------- | ------- | ------- |
| TCP            | ✅      | ✅      |
| UDP            | ❌      | ✅      |
| Autenticación  | ❌      | ✅      |
| DNS remoto     | ❌      | ✅      |
| IPv6           | ❌      | ✅      |

---

✅ En pocas palabras:

⭐ **SOCKSv5 = SOCKSv4 + muchas mejoras**.

---

### ✅ ¿Cómo se instala y configura SOCKS? (Guía paso a paso)

¡Ahora la parte práctica!

✅ Hay **dos formas principales** de usar un proxy SOCKS:

---

#### ⭐ A) Usar un servidor SOCKS externo (comprado o gratuito)

✅ Paso 1: Consigue datos del servidor SOCKS

- IP o dominio
- Puerto
- (opcional) Usuario/contraseña

✅ Ejemplo:

```
IP: 123.45.67.89
Puerto: 1080
Usuario: juan
Contraseña: 1234
```

---

✅ Paso 2: Configura tu navegador

⭐ En Firefox (muy fácil):

1️⃣ Abre Firefox.

2️⃣ Menú → Ajustes → Configuración de red → Configurar conexión.

3️⃣ Marca **Configuración manual del proxy**.

4️⃣ En **SOCKS Host** → pon la IP y el puerto.

5️⃣ Elige SOCKSv5.

6️⃣ (Si tu servidor pide usuario/contraseña, Firefox te pedirá al conectar).

7️⃣ Aceptar.

✅ Resultado:

- Todo el tráfico de Firefox pasa por el servidor SOCKS.
- Tu IP pública será la del servidor SOCKS.

---

✅ En Google Chrome:

- Chrome no tiene opción SOCKS en su GUI.
- Debes iniciarlo con parámetros:

```
chrome.exe --proxy-server="socks5://123.45.67.89:1080"
```

✅ O usar extensiones de proxy.

---

✅ En el sistema Windows:

1️⃣ Configuración → Red e Internet → Proxy.

2️⃣ Manual → SOCKS proxy → IP y puerto.

⚠️ Windows no siempre soporta SOCKS nativamente → a menudo se usa en apps específicas.

---

✅ En Linux:

✅ En terminal:

```
export ALL_PROXY="socks5://usuario:contraseña@123.45.67.89:1080"
```

✅ En apps como curl:

```
curl --socks5 123.45.67.89:1080 http://example.com
```

---

#### ⭐ B) Crear tu propio servidor SOCKS

✅ Usar SSH es la forma más fácil y segura.

✅ **Con SSH:**

```
ssh -D 1080 usuario@mi-servidor
```

- -D 1080 → abre un proxy SOCKS en tu máquina en el puerto 1080.
- Tu tráfico se cifra hasta el servidor SSH.

✅ Resultado:

- SOCKSv5 local → tráfico cifrado → servidor → Internet.

✅ Ejemplo práctico:

```
ssh -D 1080 juan@mi-servidor.com
```

✅ Luego en Firefox:

```
SOCKS Host: localhost
Puerto: 1080
SOCKSv5
```

✅ Todo pasa por tu servidor → seguro y privado.

---

### ✅ Resumen súper claro

✅ **SOCKS = proxy universal para cualquier protocolo.**

✅ **SOCKSv4** → básico, solo TCP, sin autenticación.

✅ **SOCKSv5** → avanzado:

⭐ TCP y UDP

⭐ Autenticación

⭐ DNS remoto

⭐ IPv6

✅ **Usos comunes:**

⭐ Navegadores

⭐ Torrents

⭐ Juegos en línea

⭐ Saltar bloqueos

✅ **Instalación súper sencilla:**

⭐ Usar servidor externo → configuras navegador o sistema.

⭐ Crear tu propio → SSH con -D (proxy local SOCKSv5).

---

✅ **Metáfora para recordar:**

> SOCKS es como un **túnel** para cualquier tráfico de Internet. SOCKSv4 es un túnel sencillo; SOCKSv5 es un túnel moderno con más funciones y seguridad.

---

[🔼](#índice)

---

## **113. Privoxy**

### ✅ ¿Qué es Privoxy?

⭐ **Privoxy** es un **proxy web avanzado** (HTTP/HTTPS) diseñado para **filtrar y modificar el tráfico web**.

✅ Es un **proxy de filtrado**:

- Puede bloquear anuncios.
- Filtrar cookies.
- Quitar rastreadores.
- Reescribir páginas.

✅ Es software libre y gratuito.

---

✅ **Metáfora sencilla:**

> Es como un **filtro purificador** en el grifo del agua → limpia el contenido antes de que llegue a ti.

---

### ✅ ¿Para qué sirve Privoxy?

✅ Bloquear anuncios molestos.

✅ Quitar rastreadores web.

✅ Filtrar contenido para control parental.

✅ Ocultar cabeceras de identificación del navegador.

✅ Redirigir tráfico a otros proxies (como Tor o un proxy SOCKS).

---

✅ **Usos comunes:**

⭐ Navegar sin anuncios.

⭐ Más privacidad.

⭐ Redireccionar todo tu tráfico a Tor para anonimato.

⭐ Hacer de "puente" a otro proxy SOCKS.

---

### ✅ ¿Cómo funciona? (Explicación fácil)

✅ Sin Privoxy:

```
[Tu Navegador] → [Internet]
```

→ El navegador recibe TODO: anuncios, rastreadores, scripts.

✅ Con Privoxy:

```
[Tu Navegador] → [Privoxy] → [Internet]
```

→ Privoxy filtra:

⭐ Elimina anuncios.

⭐ Bloquea rastreadores.

⭐ Cambia cabeceras.

⭐ Aplica reglas.

---

✅ **Ejemplo fácil:**

- Tu navegador pide **example.com**.
- Privoxy intercepta la página.
- Borra los scripts de anuncios.
- La entrega limpia al navegador.

---

✅ **Otra forma de usarlo:**

```
[Tu Navegador] → [Privoxy] → [Tor] → [Internet]
```

→ Privoxy puede enviar tu tráfico a Tor → anonimato extra.

---

### ✅ Características clave de Privoxy

✅ Bloqueo de anuncios (como AdBlock pero a nivel proxy).

✅ Filtrado de URLs (bloquea dominios malos).

✅ Eliminación o reescritura de cookies.

✅ Eliminación de banners e imágenes publicitarias.

✅ Personalización de cabeceras HTTP.

✅ Compatible con HTTP y HTTPS (hasta cierto punto → no descifra HTTPS, pero puede controlar las cabeceras).

---

### ✅ Ejemplo súper sencillo de uso

⭐ Sin Privoxy:

- Accedes a un sitio → te salen 10 banners, rastreadores, scripts maliciosos.

⭐ Con Privoxy:

- Accedes al mismo sitio → los banners son bloqueados, scripts de rastreo eliminados.

✅ Resultado:

- Página más ligera, más rápida.
- Más privacidad.

---

✅ **Otro ejemplo (con Tor):**

- Configuras Privoxy para reenviar tráfico a Tor.
- Navegas → tu IP pública es la de un nodo Tor.

---

### ✅ Cómo se instala paso a paso

¡Vamos a la parte práctica!

---

#### ⭐ A) En Windows

✅ Paso 1: Descarga

- Ve a [https://www.privoxy.org](https://www.privoxy.org).
- Descarga el instalador para Windows.

✅ Paso 2: Instalación

- Ejecuta el instalador.
- Acepta los términos.
- Elige la carpeta de instalación.
- Finaliza.

✅ Paso 3: Arrancar Privoxy

- Normalmente se instala como **servicio de Windows**.
- Se inicia automáticamente.
- También puedes abrir el acceso directo:

  - "Privoxy Start" → abre la ventana de comandos con Privoxy corriendo.

✅ Resultado:

- Privoxy escuchando en `127.0.0.1:8118` (puerto por defecto).

---

#### ⭐ B) En Linux (Ubuntu/Debian)

✅ Paso 1: Abrir terminal

```
sudo apt update
```

✅ Paso 2: Instalar Privoxy

```
sudo apt install privoxy
```

✅ Paso 3: Verificar estado

```
sudo systemctl status privoxy
```

✅ Resultado:

- Servicio activo escuchando en `127.0.0.1:8118`.

✅ Paso 4: Iniciar/Detener/Recargar

```
sudo systemctl start privoxy
sudo systemctl stop privoxy
sudo systemctl restart privoxy
```

---

### ✅ Cómo se configura

✅ Archivo principal de configuración:

⭐ En Linux:

```
/etc/privoxy/config
```

⭐ En Windows:

```
C:\Program Files (x86)\Privoxy\config.txt
```

---

✅ Puerto y dirección:

```
listen-address  127.0.0.1:8118
```

→ Puedes cambiar el puerto o abrirlo a otras IPs (¡cuidado con seguridad!).

---

✅ Redirigir a otro proxy (por ejemplo Tor):

```
forward-socks5   /   127.0.0.1:9050 .
```

→ Esto manda todo tu tráfico a un proxy SOCKSv5 en localhost:9050 (el puerto típico de Tor).

---

✅ Bloqueo de anuncios y filtros

- Privoxy tiene **archivos de acciones** (`default.action`, etc.).
- Contienen reglas para bloquear banners, rastreadores, etc.
- Puedes editarlos para personalizar el filtrado.

✅ Bloqueo de dominios

- Archivo `default.filter`.
- Puedes agregar patrones de URLs a bloquear.

---

✅ Acceso a la interfaz web local

- Por defecto en:

```
http://127.0.0.1:8118
```

- Muestra el estado de Privoxy y acceso a la documentación local.

---

✅ **Ejemplo de regla para redirigir a Tor en el archivo de config:**

```
forward-socks5 / 127.0.0.1:9050 .
```

→ Navegas en Firefox con proxy HTTP configurado en 127.0.0.1:8118 → tráfico pasa a Tor.

---

### ✅ Cómo usar Privoxy en el navegador

✅ Firefox (más fácil):

1️⃣ Menú → Configuración → Red → Configurar conexión.

2️⃣ Proxy Manual:

```
HTTP Proxy: 127.0.0.1
Puerto: 8118
```

3️⃣ Aceptar.

✅ Resultado:

- Todo el tráfico del navegador pasa por Privoxy.
- Privoxy filtra anuncios, redirige a Tor o a otro proxy si configuraste eso.

---

✅ Chrome:

- Usa la configuración del sistema en Windows.
- O arranca con:

```
chrome.exe --proxy-server="http://127.0.0.1:8118"
```

---

### ✅ Resumen súper claro

⭐ **Privoxy = Proxy filtrador para HTTP.**

✅ Bloquea anuncios.

✅ Filtra rastreadores.

✅ Reescribe páginas.

✅ Puede redirigir tráfico a otro proxy (como Tor o SOCKS).

✅ **Puerto por defecto:** 8118.

✅ **Instalación fácil:**

⭐ Windows → Instalador oficial.

⭐ Linux → `sudo apt install privoxy`.

✅ **Configuración fácil:**

⭐ Edita `config` → cambia puerto, reglas de filtrado, reenvío a otros proxies.

⭐ Usa con navegador → configura proxy HTTP en 127.0.0.1:8118.

---

✅ **Metáfora para recordar:**

> Privoxy es **como un filtro de agua** para Internet → limpia la suciedad (anuncios, rastreadores) antes de que llegue a ti.

---

[🔼](#índice)

---

## **114. Proxy Web - ProxySite**

### ✅ ¿Qué es un Proxy Web?

⭐ Un **proxy web** es un **servicio en línea** (una página web) que actúa como **intermediario** entre tú e Internet.

✅ En vez de conectarte **directamente** a un sitio bloqueado o filtrado:

- **Te conectas al proxy web**.
- El proxy web **pide la página por ti**.
- Te la muestra en su propia interfaz.

---

✅ **Metáfora súper fácil:**

> Es como si **le pidieras a un amigo**: “Entra a la página por mí y muéstramela en su pantalla”.

---

✅ **Sin Proxy Web:**

```
Tú → Sitio bloqueado ❌
```

✅ **Con Proxy Web:**

```
Tú → Proxy Web → Sitio ✔️
```

→ El sitio solo ve la IP del proxy web, no la tuya.

---

✅ **¿Para qué sirve?**

⭐ Saltar bloqueos de red (escuela, oficina, país).

⭐ Navegar anónimamente (tu IP queda oculta).

⭐ Acceder a contenido restringido.

---

### ✅ ¿Qué es ProxySite?

✅ **ProxySite.com** es un **proxy web gratuito** y popular.

✅ Es un sitio web que te permite:

- Escribir la dirección que quieres visitar.
- Cargarla a través de sus servidores proxy.
- Ver la página bloqueada desde su interfaz.

✅ No necesitas instalar nada. Solo un navegador.

---

✅ **Características clave:**

⭐ Gratuito.

⭐ Fácil de usar.

⭐ Varios servidores en diferentes ubicaciones (EE.UU., Europa, etc.).

⭐ HTTPS (cifrado entre tú y ProxySite).

⭐ Sin registro obligatorio.

---

✅ **Sitio oficial:**

[https://www.proxysite.com](https://www.proxysite.com)

---

### ✅ ¿Cómo funciona? (Explicación fácil con ejemplo)

✅ **Flujo básico:**

1️⃣ Tú visitas **ProxySite.com** en tu navegador.

2️⃣ Escribes la dirección que quieres visitar (ejemplo: **facebook.com**).

3️⃣ ProxySite hace la solicitud en tu lugar.

4️⃣ ProxySite te muestra la página **dentro de su propia ventana**.

---

✅ **Ejemplo súper sencillo:**

✔️ Estás en la oficina, donde Facebook está bloqueado.

✔️ Abres [proxysite.com](https://www.proxysite.com).

✔️ En el cuadro de búsqueda, escribes:

```
https://www.facebook.com
```

✔️ Haces clic en “Go” o “Ir”.

✔️ ProxySite carga Facebook en su página.

✔️ Puedes usar Facebook a través de ProxySite.

---

✅ **Resultado:**

- El firewall de tu oficina ve tráfico hacia proxysite.com (no hacia Facebook).
- Facebook ve la IP de ProxySite (no la tuya).
- Tú accedes al contenido bloqueado.

---

✅ **Diagrama sencillo:**

```
Tú → ProxySite → Facebook
```

---

✅ **Metáfora:**

> Es como pedirle a un amigo que lea la carta prohibida por ti y te la copie en otra hoja.

---

### ✅ Ventajas y limitaciones

✅ **Ventajas:**

⭐ Gratis.

⭐ Sin instalar nada.

⭐ Fácil de usar.

⭐ Oculta tu IP del sitio de destino.

⭐ Evita algunos bloqueos escolares o de trabajo.

✅ **Limitaciones:**

⚠️ No cifra hasta el destino (el sitio destino puede ser HTTP).

⚠️ El proxy web ve tu tráfico → Confía en el servicio.

⚠️ Puede ser más lento.

⚠️ No sirve para todo el tráfico → solo para navegación web a través del sitio.

⚠️ Algunos sitios pueden romperse o no funcionar igual.

---

✅ **En resumen:**

→ Es ideal para acceso rápido, puntual, desde el navegador.

→ No reemplaza una VPN.

---

### ✅ Cómo se usa ProxySite paso a paso

✅ Super sencillo – solo necesitas un navegador:

---

✅ **PASO 1:**

- Abre tu navegador (Chrome, Firefox, Edge, Safari, etc.).
- Ve a:

```
https://www.proxysite.com
```

---

✅ **PASO 2:**

- Verás un cuadro que dice:

```
Enter URL
```

---

✅ **PASO 3:**

- Escribe la dirección del sitio bloqueado o al que quieras acceder.
  ✅ Ejemplo:

```
https://www.youtube.com
```

---

✅ **PASO 4:**

- Elige un servidor (opcional):

  - EE.UU. #1, #2, etc.
  - Europa #1, #2, etc.
    → Puedes cambiar si uno es más rápido o desbloquea mejor.

---

✅ **PASO 5:**

- Haz clic en **Go** o **Ir**.

---

✅ **PASO 6:**

- ¡Listo! El sitio web se carga dentro de la ventana de ProxySite.
- Navega desde ahí como si estuvieras en otra ubicación.

---

✅ **✅ Resultado:**

- Tu red local solo ve que visitas ProxySite.com.
- El sitio de destino ve la IP de ProxySite, no la tuya.

---

### ✅ ¿Hay que instalar algo?

⭐ ¡No!

✅ ProxySite es un **servicio web**.

✅ No se instala.

✅ Funciona en:

- Windows
- macOS
- Linux
- Android
- iPhone

✅ Solo necesitas un navegador y conexión a Internet.

---

✅ **Opcional:**

Si quieres algo más “integrado” (para todo tu tráfico), puedes usar:

⭐ VPN (cifra todo el tráfico).

⭐ Proxy en sistema (para apps).

⭐ Extensiones de navegador (algunos ofrecen proxys dedicados).

Pero **ProxySite.com** en sí no requiere instalación.

---

### ✅ Resumen súper claro

✅ **¿Qué es ProxySite?**

- Un **proxy web gratuito**.
- Se usa desde el navegador.
- Oculta tu IP del sitio destino.
- Permite saltar bloqueos de red.

✅ **¿Cómo funciona?**

- Tú → ProxySite → Sitio web.
- El sitio ve la IP de ProxySite.
- Tu red local solo ve ProxySite.

✅ **Ventajas:**

⭐ Gratis y fácil.

⭐ Sin instalación.

⭐ Varios servidores.

✅ **Limitaciones:**

⚠️ Solo funciona en el navegador.

⚠️ Puede ser más lento.

⚠️ No cifra todo tu tráfico como una VPN.

✅ **Uso súper fácil:**

✔️ Entra a [proxysite.com](https://www.proxysite.com).

✔️ Escribe la URL.

✔️ Haz clic en “Go”.

✔️ Navega.

---

✅ **Metáfora para recordar:**

> ProxySite es como un **amigo en Internet** que abre la página bloqueada por ti y te la muestra en su pantalla.

---

[🔼](#índice)

---

## **115. ProxyChains**

### ✅ ¿Qué es ProxyChains?

**ProxyChains** es una herramienta de línea de comandos en Linux que te permite **redirigir el tráfico de cualquier programa a través de uno o más proxies**.

✅ En otras palabras:

- Hace que **cualquier app o comando** use un proxy.
- Incluso apps que **no tienen opción de proxy propia**.

---

✅ Es como **forzar** el tráfico de un programa para que pase por un proxy.

✅ Tipos de proxy que soporta:

⭐ SOCKS4

⭐ SOCKS5

⭐ HTTP

---

✅ **Metáfora sencilla:**

> Es como construir un túnel para obligar a tus datos a ir por un camino indirecto.

---

### ✅ ¿Para qué sirve ProxyChains?

✅ Casos de uso típicos:

⭐ Ocultar tu IP real → redirigir tráfico por proxies.

⭐ Saltar bloqueos geográficos o censura.

⭐ Encadenar varios proxies (más anonimato).

⭐ Redirigir tráfico a través de Tor para anonimato fuerte.

⭐ Pruebas de seguridad → ver cómo se comporta un servicio detrás de proxys.

---

✅ **Usos comunes:**

- Navegar desde terminal con `curl` o `wget` a través de proxies.
- Usar herramientas como `nmap` o `ssh` detrás de Tor.
- Encadenar proxies → proxy → proxy → Tor.

---

### ✅ ¿Cómo funciona? (Explicación sencilla)

✅ Sin ProxyChains:

```
[Tu App] → [Internet]
```

✅ Con ProxyChains:

```
[Tu App] → [Proxy 1] → [Proxy 2] → [...] → [Internet]
```

✅ Resultado:

⭐ Tu IP pública es la del último proxy.

⭐ Es más difícil rastrearte.

⭐ Puedes “aparecer” en otros países.

---

✅ **Diagrama fácil:**

```
curl --> ProxyChains --> SOCKS5 Proxy --> Internet
```

✅ **Con múltiples proxies:**

```
curl --> ProxyChains --> Proxy1 --> Proxy2 --> Proxy3 --> Internet
```

---

✅ **Metáfora:**

> Es como enviar tu carta a través de varios amigos antes de llegar al destinatario → cada uno tapa tus huellas un poco más.

---

### ✅ Características principales

✅ Encadenamiento de múltiples proxies.

✅ Soporte de SOCKS4, SOCKS5, HTTP.

✅ Compatible con Tor.

✅ Fácil de usar en la terminal.

✅ No necesita que la app tenga soporte de proxy → ProxyChains lo intercepta.

---

✅ **Ventaja clave:**

⭐ Puedes usar cualquier app de línea de comandos con proxy, incluso si la app no tiene opción de proxy.

---

### ✅ Ejemplo de uso real súper fácil

✅ Problema:

Tu país bloquea `example.com`.

✅ Solución con ProxyChains:

1️⃣ Configuras un proxy SOCKS en ProxyChains.

2️⃣ Lanzas `curl` a través de ProxyChains.

3️⃣ El tráfico va por el proxy → tu IP real queda oculta → el bloqueo se evita.

---

✅ **Comando ejemplo:**

```
proxychains curl http://example.com
```

→ `curl` usa el proxy aunque no sepa hacerlo por sí mismo.

---

✅ Otro ejemplo:

```
proxychains nmap -sT -Pn target.com
```

→ Hacer un escaneo por proxy.

---

✅ Con Tor:

```
proxychains firefox
```

→ Firefox lanza todo el tráfico por la red Tor.

---

### ✅ Cómo se instala ProxyChains (Linux)

✅ ProxyChains es muy popular en Linux.

---

⭐ **En Debian / Ubuntu / Kali / Linux Mint**:

```bash
sudo apt update
sudo apt install proxychains
```

✅ En muchas distros viene ya instalado (especialmente en Kali).

---

⭐ **En Arch / Manjaro**:

```bash
sudo pacman -S proxychains
```

---

✅ Hay dos variantes:

- proxychains (el clásico)
- proxychains-ng (mejorado)

✅ Ambos funcionan casi igual. proxychains-ng tiene más opciones.

---

✅ **Verificar instalación**:

```bash
proxychains -h
```

→ Verás la ayuda.

---

### ✅ Cómo se configura ProxyChains

✅ El archivo principal de configuración suele estar en:

⭐ Ubuntu/Debian/Kali:

```
/etc/proxychains.conf
```

⭐ En proxychains-ng:

```
/etc/proxychains.conf o /etc/proxychains4.conf
```

---

✅ **Contenido típico del archivo**:

```
# dynamic_chain
# strict_chain
# random_chain

# proxies list
[ProxyList]
socks5 127.0.0.1 9050
```

---

✅ **Explicación sencilla:**

⭐ **dynamic_chain**

- Intenta usar proxies en orden, pero salta uno si falla.

⭐ **strict_chain**

- Usa exactamente en orden → si falla uno, falla todo.

⭐ **random_chain**

- Usa proxies en orden aleatorio.

---

✅ **Sección \[ProxyList]:**

Ahí pones tus proxies.

✅ Ejemplo de SOCKS5 local (como Tor):

```
socks5 127.0.0.1 9050
```

✅ Ejemplo con varios proxies:

```
socks5 127.0.0.1 9050
socks5 192.168.1.100 1080
http 203.0.113.5 8080
```

---

✅ **Opciones más comunes:**

```
socks4  IP PUERTO
socks5  IP PUERTO
http    IP PUERTO
```

✅ Con autenticación (SOCKS5 con usuario/contraseña):

```
socks5 usuario:contraseña@IP PUERTO
```

---

✅ **Ejemplo completo de ProxyList:**

```
strict_chain
[ProxyList]
socks5 127.0.0.1 9050
socks5 192.168.1.100 1080
```

→ El tráfico saldrá por Tor y luego por el segundo proxy.

---

### ✅ Cómo se usa ProxyChains

✅ Muy fácil:

```
proxychains [comando]
```

---

✅ ⭐ Ejemplos reales:

⭐ Usar curl:

```
proxychains curl http://example.com
```

⭐ Usar wget:

```
proxychains wget http://example.com/file.zip
```

⭐ Usar nmap:

```
proxychains nmap -sT target.com
```

⭐ Usar SSH:

```
proxychains ssh usuario@servidor
```

⭐ Usar Firefox:

```
proxychains firefox
```

---

✅ ⭐ Con Tor (caso clásico):

- Instalas Tor:

```bash
sudo apt install tor
```

- Arrancas el servicio:

```bash
sudo systemctl start tor
```

- ProxyChains ya configurado con:

```
socks5 127.0.0.1 9050
```

- Ejecutas:

```
proxychains firefox
```

→ Todo el tráfico de Firefox sale por la red Tor.

---

✅ Resultado:

⭐ Tu IP real queda oculta.

⭐ Apareces como una IP de la red Tor.

⭐ Puedes acceder a contenido bloqueado o censurado.

---

### ✅ Resumen súper claro

✅ **ProxyChains = herramienta para Linux** que redirige el tráfico de cualquier app por uno o más proxies.

✅ Soporta SOCKS4, SOCKS5 y HTTP.

✅ Permite encadenar proxies.

✅ Muy usado con Tor para anonimato.

---

✅ **Ventajas:**

⭐ Fácil de instalar.

⭐ Forza apps que no soportan proxy.

⭐ Muy flexible.

✅ **Limitaciones:**

⚠️ Solo para Linux (oficialmente).

⚠️ Puede ser más lento con muchas cadenas.

⚠️ No cifra contenido (eso depende del proxy usado).

---

✅ **Comandos clave:**

⭐ Instalar:

```
sudo apt install proxychains
```

⭐ Editar configuración:

```
sudo nano /etc/proxychains.conf
```

⭐ Usar:

```
proxychains [comando]
```

---

✅ **Metáfora para recordar:**

> ProxyChains es **como obligar a tus datos a tomar un camino secreto lleno de túneles y desvíos para ocultar su origen**.

---

[🔼](#índice)

---

| **Inicio**         | **atrás 1**                                | **Siguiente 3**        |
| ------------------ | ------------------------------------------ | ---------------------- |
| [🏠](../README.md) | [⏪](./3_1_VPN_Virtual_Private_Network.md) | [⏩](./3_3_Red_TOR.md) |
