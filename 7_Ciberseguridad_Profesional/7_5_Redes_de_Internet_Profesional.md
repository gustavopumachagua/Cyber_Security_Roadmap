| **Inicio**         | **atrás 4**                                   | **Siguiente 6**                                         |
| ------------------ | --------------------------------------------- | ------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./7_4_Redes_Informaticas_de_Internet.md) | [⏩](./7_6_Guia_para_Aprender_Seguridad_Informatica.md) |

---

## **Índice**

| Temario                                                                                                                                                             |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [682. Números binarios fáciles](#682-números-binarios-fáciles)                                                                                                      |
| [683. Máscaras, todas las tallas para todos los tamaños](#683-máscaras-todas-las-tallas-para-todos-los-tamaños)                                                     |
| [684. Clases de direcciones](#684-clases-de-direcciones)                                                                                                            |
| [685. Configuración de redes empresariales y clases IP](#685-configuración-de-redes-empresariales-y-clases-ip)                                                      |
| [686. ¿Por qué tenemos direcciones públicas y privadas?](#686-por-qué-tenemos-direcciones-públicas-y-privadas)                                                      |
| [687. Instalación de Packet Tracer](#687-instalación-de-packet-tracer)                                                                                              |
| [688. Traducción de direcciones públicas a privadas](#688-traducción-de-direcciones-públicas-a-privadas)                                                            |
| [689. Capa de red, las direcciones públicas se han acabado ¿Qué haremos?](#689-capa-de-red-las-direcciones-públicas-se-han-acabado-qué-haremos)                     |
| [690. Nombres para humanos vs nombres para máquinas](#690-nombres-para-humanos-vs-nombres-para-máquinas)                                                            |
| [691. ¿Cómo sabe una máquina quién es? Servicio de asignación de direcciones](#691-cómo-sabe-una-máquina-quién-es-servicio-de-asignación-de-direcciones)            |
| [692. Rutas ¿Cuál es la ubicación de las máquinas?](#692-rutas-cuál-es-la-ubicación-de-las-máquinas)                                                                |
| [693. Uso de rutas estáticas](#693-uso-de-rutas-estáticas)                                                                                                          |
| [694. Configuración de rutas estáticas](#694-configuración-de-rutas-estáticas)                                                                                      |
| [695. Rutas dinámicas: cuando los enrutadores aprenden por sí mismos](#695-rutas-dinámicas-cuando-los-enrutadores-aprenden-por-sí-mismos)                           |
| [696. Configuración de rutas dinámicas](#696-configuración-de-rutas-dinámicas)                                                                                      |
| [697. Apuntes: rutas estáticas y dinámicas](#697-apuntes-rutas-estáticas-y-dinámicas)                                                                               |
| [698. Convergencia de enrutamiento, cuando todos los enrutadores están de acuerdo](#698-convergencia-de-enrutamiento-cuando-todos-los-enrutadores-están-de-acuerdo) |
| [699. Necesidad del diseño de la topología de LAN](#699-necesidad-del-diseño-de-la-topología-de-lan)                                                                |
| [700. Ejecución del diseño de la topología de LAN](#700-ejecución-del-diseño-de-la-topología-de-lan)                                                                |
| [701. Redes inalámbricas, los usuarios se mueven por todos lados](#701-redes-inalámbricas-los-usuarios-se-mueven-por-todos-lados)                                   |
| [702. Diseño de redes inalámbricas](#702-diseño-de-redes-inalámbricas)                                                                                              |
| [703. Configuración de redes inalámbricas](#703-configuración-de-redes-inalámbricas)                                                                                |
| [704. Equipos activos de LAN: el cableado sigue siendo importante](#704-equipos-activos-de-lan-el-cableado-sigue-siendo-importante)                                 |
| [705. Separación de grupos, el uso de las VLAN](#705-separación-de-grupos-el-uso-de-las-vlan)                                                                       |
| [706. Enlaces troncales, cuando las conexiones se unen](#706-enlaces-troncales-cuando-las-conexiones-se-unen)                                                       |
| [707. Lista de control de acceso: elementos](#707-lista-de-control-de-acceso-elementos)                                                                             |
| [708. Lista de control de acceso: filosofía](#708-lista-de-control-de-acceso-filosofía)                                                                             |
| [709. Listas de control de acceso, un firewall en reglas](#709-listas-de-control-de-acceso-un-firewall-en-reglas)                                                   |
| [710. Ataques al servicio DNS ¿Qué pasa cuando me engañan con el nombre?](#710-ataques-al-servicio-dns-qué-pasa-cuando-me-engañan-con-el-nombre)                    |

# **Redes de Internet - Profesional**

## **682. Números binarios fáciles**

### ✅ Explicación fácil

Un **número binario** es un número que **solo usa dos cifras**:

- **0** y
- **1**

Este sistema se llama **sistema binario** y lo usan las **computadoras** para procesar información, porque trabajan con impulsos eléctricos:

- **0 = apagado (sin corriente)**
- **1 = encendido (con corriente)**

---

### ¿En qué se diferencia del sistema decimal?

| Sistema decimal (el que usamos) | Sistema binario (el que usan las computadoras) |
| ------------------------------- | ---------------------------------------------- |
| Usa 10 números: 0 al 9          | Usa solo 2 números: 0 y 1                      |
| Base 10                         | Base 2                                         |

---

### 🎓 Ejemplo comparativo

| Decimal | Binario |
| ------- | ------- |
| 0       | 0       |
| 1       | 1       |
| 2       | 10      |
| 3       | 11      |
| 4       | 100     |
| 5       | 101     |
| 6       | 110     |
| 7       | 111     |
| 8       | 1000    |
| 9       | 1001    |
| 10      | 1010    |

---

### 🧠 ¿Cómo convertir decimal a binario?

#### Paso a paso:

Vamos a convertir el número **13** a binario:

1. Dividimos por 2 y anotamos el residuo.
2. Repetimos con el cociente hasta llegar a 0.
3. Leemos los residuos de abajo hacia arriba.

```
13 ÷ 2 = 6 y sobra 1
6 ÷ 2 = 3 y sobra 0
3 ÷ 2 = 1 y sobra 1
1 ÷ 2 = 0 y sobra 1

Entonces: 13 en binario es 1101
```

---

### 🧮 ¿Cómo convertir binario a decimal?

Toma cada número binario, **multiplícalo por una potencia de 2** (de derecha a izquierda).

Ejemplo:
Convertir **1011** a decimal.

```
1 × 2³ = 8
0 × 2² = 0
1 × 2¹ = 2
1 × 2⁰ = 1

8 + 0 + 2 + 1 = 11
Entonces: 1011 en binario es 11 en decimal
```

---

### 💻 ¿Cómo "instalar" o trabajar con binarios?

#### 🧰 En Windows

1. Abre la **Calculadora** de Windows.
2. Cambia al modo **Programador** (presiona `Alt + 3`).
3. Selecciona “Bin” (binario), “Dec” (decimal), etc.
4. Escribe un número en decimal y cambia a binario automáticamente.

---

#### 🧰 En línea

Puedes usar estas páginas para convertir binarios fácilmente:

- [https://www.rapidtables.com/convert/number/decimal-to-binary.html](https://www.rapidtables.com/convert/number/decimal-to-binary.html)
- [https://www.binaryhexconverter.com/](https://www.binaryhexconverter.com/)

---

#### 🧰 En programación (ejemplo en Python):

```python
# Decimal a binario
numero = 10
binario = bin(numero)  # Resultado: '0b1010'
print(binario[2:])     # Imprime: 1010

# Binario a decimal
binario = "1101"
decimal = int(binario, 2)
print(decimal)         # Imprime: 13
```

---

### 🧪 Ejemplo completo explicado

Convertir el número decimal **25** a binario y luego volver a decimal:

#### 1. Decimal → Binario

```
25 ÷ 2 = 12 resto 1
12 ÷ 2 = 6  resto 0
6 ÷ 2 = 3   resto 0
3 ÷ 2 = 1   resto 1
1 ÷ 2 = 0   resto 1

Binario: 11001
```

#### 2. Binario → Decimal

```
1 × 2⁴ = 16
1 × 2³ = 8
0 × 2² = 0
0 × 2¹ = 0
1 × 2⁰ = 1
Total: 16 + 8 + 0 + 0 + 1 = 25
```

✔ ¡Funciona perfecto!

---

### 🧠 Resumen

| Concepto        | Explicación corta                |
| --------------- | -------------------------------- |
| Sistema binario | Solo usa 0 y 1                   |
| Usado por       | Computadoras                     |
| Conversión      | Decimal ↔ Binario                |
| Herramientas    | Calculadora, Python, páginas web |

---

[🔼](#índice)

---

## **683. Máscaras, todas las tallas para todos los tamaños**

### 🧠 ¿Qué es una Máscara de Subred?

Una **máscara de subred** (o **subnet mask**) es un conjunto de números que sirve para **dividir** una red en **subredes más pequeñas**. Ayuda a determinar:

- Cuál parte de una IP pertenece a la **red**.
- Cuál parte pertenece a los **hosts** (dispositivos).

---

#### 🔧 ¿Por qué se usan?

Las máscaras permiten:

✅ Usar eficientemente el espacio de direcciones IP

✅ Aumentar la seguridad

✅ Organizar redes grandes en secciones más pequeñas

---

### 🎯 Ejemplo fácil de entender

Supongamos que tienes la IP:

`192.168.1.15` y la máscara: `255.255.255.0`

Esto significa:

- **192.168.1.** → parte de red
- **15** → parte del host (dispositivo)

La máscara `255.255.255.0` está diciendo:
“los primeros 3 números (octetos) son de red y el último es para los dispositivos”.

---

### 📦 Analizando la máscara

| Máscara Decimal | Máscara Binaria                     | Hosts disponibles |
| --------------- | ----------------------------------- | ----------------- |
| 255.0.0.0       | 11111111.00000000.00000000.00000000 | 16,777,214        |
| 255.255.0.0     | 11111111.11111111.00000000.00000000 | 65,534            |
| 255.255.255.0   | 11111111.11111111.11111111.00000000 | 254               |
| 255.255.255.192 | 11111111.11111111.11111111.11000000 | 62                |
| 255.255.255.252 | 11111111.11111111.11111111.11111100 | 2                 |

🔎 _Nota:_ Siempre se pierden 2 direcciones:

- 1 para la red (todos ceros)
- 1 para el broadcast (todos unos)

---

### 🎨 Analizando “tallas para todos los tamaños”

Cada máscara permite una “talla” diferente. Ejemplos:

| ¿Cuántos hosts necesito? | Máscara que puedo usar | # IPs disponibles |
| ------------------------ | ---------------------- | ----------------- |
| 2 impresoras             | /30 o 255.255.255.252  | 2                 |
| 10 computadoras          | /28 o 255.255.255.240  | 14                |
| 50 dispositivos          | /26 o 255.255.255.192  | 62                |
| 200 dispositivos         | /24 o 255.255.255.0    | 254               |
| 1000 dispositivos        | /22 o 255.255.252.0    | 1022              |

---

### 📘 Cómo se representa una máscara

Existen 2 formas:

#### 1. Decimal:

```
255.255.255.0
```

#### 2. Notación CIDR (compacta):

```
/24  →  significa que los primeros 24 bits son para red
```

Por ejemplo:
`192.168.0.0/24` → red con 254 hosts disponibles.

---

### 🛠️ ¿Cómo se "instala" o configura una máscara?

#### En Windows:

1. Ir a **Panel de Control** → Redes → Cambiar adaptador
2. Clic derecho en tu red → Propiedades
3. Seleccionas “Protocolo de Internet versión 4 (TCP/IPv4)”
4. Allí puedes poner:

   - Dirección IP: `192.168.1.10`
   - Máscara: `255.255.255.0`
   - Puerta de enlace: `192.168.1.1`

#### En Linux (terminal):

```bash
sudo ifconfig eth0 192.168.1.10 netmask 255.255.255.0 up
```

---

### ✅ Ejemplo completo paso a paso

#### ✅ Quiero una red para 50 dispositivos

#### Paso 1: Elegir el tamaño adecuado

Sabemos que con 50 dispositivos, necesitamos al menos 50 IPs.

La máscara ideal es:
`255.255.255.192` (o /26) → nos da **62 IPs útiles**

---

#### Paso 2: Elegir un bloque de IPs

Usamos por ejemplo:
`192.168.1.0/26`

Este bloque va de:

- **192.168.1.1** (primer host)
- a **192.168.1.62** (último host)
- y **192.168.1.63** es la dirección de broadcast

---

#### Paso 3: Asignar IPs

| Dispositivo | Dirección IP |
| ----------- | ------------ |
| Router      | 192.168.1.1  |
| PC1         | 192.168.1.2  |
| Impresora   | 192.168.1.3  |
| ...         | ...          |
| PC50        | 192.168.1.51 |

---

### 🧠 Resumen final

| Concepto                  | Significado                                  |
| ------------------------- | -------------------------------------------- |
| Máscara de subred         | Define cuántas IPs se pueden usar en una red |
| Notación CIDR (/24, /26…) | Forma abreviada de expresar la máscara       |
| Tamaños                   | Se eligen según cuántos hosts necesito       |
| Configuración             | Se hace en el sistema operativo              |

---

[🔼](#índice)

---

## **684. Clases de direcciones**

### ✅ ¿Qué son las direcciones IP?

Una **dirección IP** (Internet Protocol) es como una **placa de identificación** para cada dispositivo conectado a una red. Permite que los dispositivos **se comuniquen entre sí**.

Ejemplo de dirección IP:
**192.168.1.10**

---

### 🧠 ¿Por qué existen clases de direcciones IP?

Las **clases de IP** fueron creadas para **organizar el espacio de direcciones** de IPv4 y permitir diferentes tamaños de redes. Así, empresas grandes, medianas o pequeñas pueden tener el espacio justo de direcciones.

---

### 🔤 Las 5 clases de direcciones IPv4

IPv4 tiene 5 clases principales:

| Clase | Rango de IPs                | N° Máx. de Redes | N° Máx. de Hosts por Red | Uso común                  |
| ----- | --------------------------- | ---------------- | ------------------------ | -------------------------- |
| **A** | 1.0.0.0 – 126.255.255.255   | 128 (2⁷)         | 16,777,214               | Redes MUY grandes (ISPs)   |
| **B** | 128.0.0.0 – 191.255.255.255 | 16,384 (2¹⁴)     | 65,534                   | Empresas medianas-grandes  |
| **C** | 192.0.0.0 – 223.255.255.255 | 2,097,152 (2²¹)  | 254                      | Oficinas o redes locales   |
| **D** | 224.0.0.0 – 239.255.255.255 | No aplica        | No aplica                | Multicast (envío a varios) |
| **E** | 240.0.0.0 – 255.255.255.255 | Reservado        | Reservado                | Investigación              |

---

#### 📌 Notas importantes:

- **127.x.x.x** está reservada para **loopback** (autoprueba, como `127.0.0.1`)
- Las IPs como `192.168.x.x`, `10.x.x.x`, y `172.16.x.x – 172.31.x.x` son **privadas** (uso en redes internas)

---

### 🔍 Detalle de cada clase con ejemplo

#### 🅰️ **Clase A**

- Rango: `1.0.0.0` a `126.255.255.255`
- Máscara por defecto: `255.0.0.0` o `/8`
- Primer octeto: `1–126`

**Ejemplo:**

IP: `10.20.30.40`
→ Es clase A porque empieza con 10.

**Red:** 10.0.0.0
**Host válido:** 10.20.30.40
**Broadcast:** 10.255.255.255

---

#### 🅱️ **Clase B**

- Rango: `128.0.0.0` a `191.255.255.255`
- Máscara: `255.255.0.0` o `/16`
- Primer octeto: `128–191`

**Ejemplo:**

IP: `172.16.5.1`
→ Es clase B porque empieza con 172.

**Red:** 172.16.0.0
**Host válido:** 172.16.5.1
**Broadcast:** 172.16.255.255

---

#### 🅲️ **Clase C**

- Rango: `192.0.0.0` a `223.255.255.255`
- Máscara: `255.255.255.0` o `/24`
- Primer octeto: `192–223`

**Ejemplo:**

IP: `192.168.1.100`
→ Es clase C.

**Red:** 192.168.1.0
**Host válido:** 192.168.1.100
**Broadcast:** 192.168.1.255

---

#### 🅳️ **Clase D** (Multicast)

- Rango: `224.0.0.0` a `239.255.255.255`
- No se usa para hosts normales.
- Se usa para transmitir a varios receptores a la vez.

**Ejemplo:**

IP: `224.0.0.5` → Protocolo OSPF (routing dinámico)

---

#### 🅴️ **Clase E** (Experimental)

- Rango: `240.0.0.0` a `255.255.255.255`
- Reservado para investigación.
- No se usa en redes comunes.

---

### 🛠️ ¿Cómo se identifica la clase?

Mira el **primer número (octeto)** de la IP:

| Primer octeto | Clase |
| ------------- | ----- |
| 1 – 126       | A     |
| 128 – 191     | B     |
| 192 – 223     | C     |
| 224 – 239     | D     |
| 240 – 255     | E     |

---

### ⚙️ ¿Cómo se configura en una PC?

#### En Windows

1. Abre "Centro de redes y recursos compartidos"
2. Haz clic en "Cambiar configuración del adaptador"
3. Clic derecho en tu red → Propiedades
4. Selecciona: "Protocolo de Internet versión 4 (TCP/IPv4)"
5. Aquí puedes asignar manualmente:

   - IP (ej. 192.168.1.10)
   - Máscara (ej. 255.255.255.0)
   - Puerta de enlace (ej. 192.168.1.1)

#### En Linux (terminal):

```bash
sudo ifconfig eth0 192.168.1.10 netmask 255.255.255.0 up
```

---

### ✅ Ejemplo completo: Red doméstica

#### 🎯 Objetivo:

Configurar una red doméstica con 3 computadoras, 1 impresora y 1 router.

---

#### Paso 1: Elegir clase

Usamos **clase C**, con IPs privadas:
`192.168.0.0/24`

---

#### Paso 2: Asignar IPs

| Dispositivo | Dirección IP  | Clase |
| ----------- | ------------- | ----- |
| Router      | 192.168.0.1   | C     |
| PC 1        | 192.168.0.10  | C     |
| PC 2        | 192.168.0.11  | C     |
| PC 3        | 192.168.0.12  | C     |
| Impresora   | 192.168.0.100 | C     |

---

#### Paso 3: Configurar en cada dispositivo

En Windows o Linux se asigna IP, máscara (`255.255.255.0`), y puerta de enlace (`192.168.0.1`).

¡Red funcionando! 🎉

---

### 🧠 Resumen final

| Clase | Uso común         | Ejemplo IP  | Máscara por defecto |
| ----- | ----------------- | ----------- | ------------------- |
| A     | Redes enormes     | 10.0.0.1    | 255.0.0.0 (/8)      |
| B     | Empresas medianas | 172.16.0.1  | 255.255.0.0 (/16)   |
| C     | Hogares/oficinas  | 192.168.1.1 | 255.255.255.0 (/24) |
| D     | Multicast         | 224.0.0.5   | -                   |
| E     | Reservado         | 240.0.0.1   | -                   |

---

[🔼](#índice)

---

## **685. Configuración de redes empresariales y clases IP**

### 🧠 ¿Qué es una Red Empresarial?

Una **red empresarial** conecta computadoras, servidores, impresoras, dispositivos móviles, cámaras, etc., dentro de una empresa, para que **compartan recursos, archivos, internet y aplicaciones**.

📌 **Objetivos de una red empresarial**:

- Compartir datos entre empleados.
- Acceder a sistemas de gestión (ERP, CRM, etc.).
- Compartir impresoras y escáneres.
- Tener seguridad (cámaras IP, firewalls).
- Acceder a internet de manera centralizada.

---

### 🧱 Tipos de redes empresariales

1. **LAN (Local Area Network)**: Dentro de una oficina o edificio.
2. **WAN (Wide Area Network)**: Conecta sedes en diferentes ciudades o países.
3. **WLAN (Wireless LAN)**: Red LAN pero por Wi-Fi.
4. **VLAN (Virtual LAN)**: Segmenta la red por áreas (Ej. contabilidad, ventas, etc.)

---

### 🏷️ ¿Qué son las clases IP?

Las **clases IP** determinan cuántos dispositivos puedes conectar en una red:

| Clase | Rango IP                    | Hosts posibles | Uso típico                 |
| ----- | --------------------------- | -------------- | -------------------------- |
| A     | 1.0.0.0 - 126.255.255.255   | 16 millones    | ISP, grandes corporaciones |
| B     | 128.0.0.0 - 191.255.255.255 | 65 mil         | Empresas medianas          |
| C     | 192.0.0.0 - 223.255.255.255 | 254            | Oficinas pequeñas          |

---

### ⚙️ ¿Cómo se configura una red empresarial?

#### 🔧 Paso 1: Elegir la clase IP correcta

- Si es una **oficina pequeña**, usa clase **C**:
  `192.168.1.0/24`

- Si es una **empresa con más de 254 dispositivos**, usa clase **B**:
  `172.16.0.0/16`

- Si es una **empresa gigante**, usa clase **A**:
  `10.0.0.0/8`

---

#### 🔧 Paso 2: Planificar la red

Divide la red en segmentos (subredes o VLANs) por departamento:

| Departamento   | Subred IP      | Rango de dispositivos       |
| -------------- | -------------- | --------------------------- |
| Administración | 192.168.1.0/24 | 192.168.1.1 - 192.168.1.254 |
| Ventas         | 192.168.2.0/24 | 192.168.2.1 - 192.168.2.254 |
| Producción     | 192.168.3.0/24 | 192.168.3.1 - 192.168.3.254 |

---

#### 🔧 Paso 3: Asignar IPs estáticas o dinámicas

- **Estáticas**: Para impresoras, servidores, cámaras (IPs fijas).
- **Dinámicas (DHCP)**: Para computadoras y móviles.

---

#### 🔧 Paso 4: Conectar los dispositivos

1. Un **router principal** se conecta al proveedor de internet.
2. El router se conecta a un **switch principal**.
3. El switch se conecta a las computadoras, servidores, etc.
4. Se pueden usar **puntos de acceso Wi-Fi** para zonas inalámbricas.

---

### 🛠️ Instalación práctica (ejemplo completo)

**Situación**: Empresa "DigitalSoft" con 3 departamentos: Administración, Ventas y Producción.

- Usaremos clase **C** (red privada): `192.168.x.0/24`
- Cada área tendrá su propia subred.

#### 🧩 Diseño de red

```plaintext
Internet
   │
[Router Principal] → IP: 192.168.0.1
   │
[Switch Principal]
 ├── Administración: 192.168.1.x
 ├── Ventas:         192.168.2.x
 └── Producción:     192.168.3.x
```

#### 📋 Asignación de IPs

| Dispositivo         | Departamento   | IP asignada   |
| ------------------- | -------------- | ------------- |
| PC Jefe Adm         | Administración | 192.168.1.10  |
| Impresora Adm       | Administración | 192.168.1.100 |
| PC Vendedor 1       | Ventas         | 192.168.2.10  |
| Laptop Vendedor 2   | Ventas         | DHCP          |
| Servidor Producción | Producción     | 192.168.3.200 |
| Cámara de seguridad | Producción     | 192.168.3.150 |

#### ⚙️ Configuración en una PC (Windows)

1. Panel de control → Redes → Cambiar adaptador
2. Propiedades → Protocolo IPv4
3. Usar IP manual:

   - IP: `192.168.1.10`
   - Máscara: `255.255.255.0`
   - Puerta de enlace: `192.168.1.1` (router)
   - DNS: `8.8.8.8`

---

### 📘 Resumen visual

| Clase | Máscara       | IP Ejemplo  | Red para         | Tamaño red |
| ----- | ------------- | ----------- | ---------------- | ---------- |
| A     | 255.0.0.0     | 10.0.0.1    | ISP, corporativo | Grande     |
| B     | 255.255.0.0   | 172.16.0.1  | Empresa mediana  | Mediana    |
| C     | 255.255.255.0 | 192.168.1.1 | Oficina, PyME    | Pequeña    |

---

## 🛡️ Buenas prácticas

- Usa IPs privadas (Clase A, B o C según tamaño).
- Usa DHCP para equipos móviles y estática para infraestructura.
- Separa la red en subredes o VLANs si tienes muchos departamentos.
- Coloca seguridad en el router: firewall, NAT y reglas de acceso.

---

[🔼](#índice)

---

## **686. ¿Por qué tenemos direcciones públicas y privadas?**

Las direcciones **IP públicas** y **privadas** existen por una razón muy importante:

👉 **La cantidad de direcciones IPv4 es limitada.**

Solo hay alrededor de **4 mil millones** de direcciones IPv4 posibles. En un mundo donde **cada teléfono, laptop, smart TV o consola** se conecta a internet… **¡no hay suficientes IPs para todos si fueran públicas!**

### ✳️ Entonces se decidió lo siguiente:

- Las **IP públicas** las usan los **dispositivos que se conectan directamente a internet** (como servidores, routers de casas, páginas web).
- Las **IP privadas** se usan **dentro de redes internas** (como tu casa o una oficina), y **no pueden salir directamente a internet sin traducirse**.

---

### 📖 ¿Qué es una IP pública?

Una **IP pública** es una dirección única en internet, visible por el mundo.

Ejemplo real:

🖥️ Servidor web de Google: `142.250.191.174`

📞 Dirección visible en internet: _Sí_

📶 Asignada por: Proveedor de internet (ISP)

> ✅ Una IP pública es como **la dirección de tu casa**: cualquier persona del mundo puede enviarte algo (por ejemplo, una carta).

---

### 📖 ¿Qué es una IP privada?

Una **IP privada** es **una dirección interna**, solo visible dentro de tu red (casa, oficina, universidad).

#### 🔐 Rango de IPs privadas según su clase:

| Clase | Rango de IPs privadas         | Ejemplo      |
| ----- | ----------------------------- | ------------ |
| A     | 10.0.0.0 – 10.255.255.255     | 10.0.1.1     |
| B     | 172.16.0.0 – 172.31.255.255   | 172.16.5.4   |
| C     | 192.168.0.0 – 192.168.255.255 | 192.168.1.15 |

> ❌ Las IP privadas **no pueden salir directamente a internet**. Primero deben pasar por un router que las convierte (NAT).

---

#### 🎯 ¿Y cómo accede una computadora con IP privada a internet?

Gracias al **NAT (Network Address Translation)**:

- Tu computadora tiene una IP privada: `192.168.1.10`
- El router tiene una IP pública: `181.64.23.5`
- Cuando accedes a Google, tu router **traduce** tu IP privada a su IP pública, y luego te pasa la respuesta.

---

### 🛠️ ¿Cómo se instalan?

#### ✅ IP privada: instalación manual (Windows)

1. Ir a **Configuración de red** → Propiedades del adaptador.
2. Seleccionar **Protocolo de Internet versión 4 (TCP/IPv4)**.
3. Marcar: “Usar la siguiente dirección IP”.
4. Ejemplo de configuración:

```
Dirección IP:       192.168.1.10
Máscara de subred:  255.255.255.0
Puerta de enlace:   192.168.1.1 (IP del router)
DNS:                8.8.8.8
```

---

#### ✅ IP pública: no la instalas tú

Tu IP pública es asignada **automáticamente** por tu proveedor de internet (Movistar, Claro, Entel, etc.).
Es la **cara visible de tu red ante el mundo**.

Puedes conocerla aquí: [https://www.whatismyip.com/](https://www.whatismyip.com/)

---

### ✅ Ejemplo completo

#### 🎯 Situación: Red en una pequeña oficina

- La oficina tiene 5 computadoras, un router y una impresora.
- Todos comparten internet a través del router.
- Usarán IPs privadas para trabajar internamente.
- El router tiene la IP pública.

#### 🌐 Red local (IP privadas – clase C)

| Dispositivo | Dirección IP privada |
| ----------- | -------------------- |
| Router      | 192.168.1.1          |
| PC 1        | 192.168.1.10         |
| PC 2        | 192.168.1.11         |
| PC 3        | 192.168.1.12         |
| Impresora   | 192.168.1.100        |

📶 Todos los dispositivos pueden acceder a internet porque el router **traduce (NAT)** las IPs privadas a la IP pública del proveedor.

🔐 **IP pública del router (automática):**

Ejemplo: `181.64.23.5` (asignada por Claro o Movistar)

---

### 🧠 ¿Por qué esto es importante?

- Usar IPs privadas **ahorra espacio** en el mundo.
- Proporciona **seguridad** (los dispositivos no están directamente expuestos).
- Permite que una empresa u hogar tenga **miles de dispositivos conectados** con solo 1 IP pública.

---

[🔼](#índice)

---

## **687. Instalación de Packet Tracer**

### 📌 ¿Qué es Packet Tracer?

**Cisco Packet Tracer** es un **simulador de redes**. Fue creado por **Cisco Systems** y se utiliza para:

- Diseñar redes de computadoras.
- Simular cómo se comunican los dispositivos.
- Aprender sobre el modelo OSI, TCP/IP, IPs, routers, switches, etc.
- Practicar sin necesidad de tener hardware real.

> ✅ Es ideal para estudiantes y principiantes en redes, e incluso es usado en la certificación **CCNA**.

---

### 🔧 ¿Cómo se instala Packet Tracer? (Windows)

#### ✅ Paso 1: Crear una cuenta gratuita en Cisco Networking Academy

1. Ve a: [https://www.netacad.com/](https://www.netacad.com/)
2. Haz clic en **"Registrarse"** o "Sign Up".
3. Crea una cuenta gratuita (elige la opción de **"Aprendiz independiente"** o "Self-Enroll").
4. Una vez creado el usuario, **inicia sesión**.

---

#### ✅ Paso 2: Descargar Cisco Packet Tracer

1. Después de iniciar sesión, entra a:
   [https://www.netacad.com/portal/resources/packet-tracer](https://www.netacad.com/portal/resources/packet-tracer)
2. Haz clic en el botón **"Download Packet Tracer"**.
3. Elige tu sistema operativo (Windows, macOS o Linux).
4. Descarga el archivo `.exe` (para Windows).

---

#### ✅ Paso 3: Instalar Packet Tracer

1. Abre el archivo descargado: `PacketTracerSetup.exe`.
2. Acepta los términos y condiciones.
3. Elige la ubicación donde quieres instalarlo (deja la predeterminada si no sabes).
4. Haz clic en **“Install”**.
5. Espera a que termine y luego haz clic en **“Finish”**.

---

#### ✅ Paso 4: Iniciar sesión

1. Al abrir el programa por primera vez, te pedirá que **inicies sesión con tu cuenta de Cisco**.
2. Escribe tu usuario y contraseña de NetAcad.
3. ¡Listo! Ya puedes comenzar a usar Packet Tracer.

---

### 🧪 ¿Cómo se usa? Interfaz básica

Cuando abras Packet Tracer verás:

- 📦 Una **barra con dispositivos** (routers, switches, PCs, cables).
- 🧩 Un **área de trabajo** donde arrastras los dispositivos.
- ⚙️ Herramientas para configurar: interfaces, IPs, conexiones.
- 📡 Iconos para **simular la red** y ver cómo circulan los paquetes.

---

### ✅ Ejemplo completo y fácil de entender

#### 🎯 Objetivo: Conectar 2 computadoras con cable y verificar si se comunican.

#### 🧱 Paso a paso:

##### 1. Agregar dispositivos

- Haz clic en el ícono de **PC** (parte inferior izquierda).
- Arrastra **2 computadoras** al área de trabajo (PC0 y PC1).

##### 2. Agregar cable

- Haz clic en el **icono de rayo (cables)**.
- Elige **cable cruzado (Cross-over)**: el color es **naranja**.
- Haz clic en PC0 → FastEthernet0.
- Luego en PC1 → FastEthernet0.

🔌 ¡Ahora están conectadas por cable!

##### 3. Asignar IPs

Haz doble clic en **PC0** → pestaña “Desktop” → “IP Configuration”:

- IP: `192.168.1.1`
- Máscara: `255.255.255.0`

Haz lo mismo en **PC1**:

- IP: `192.168.1.2`
- Máscara: `255.255.255.0`

##### 4. Verificar conectividad (ping)

- En **PC0** → pestaña “Command Prompt”.
- Escribe: `ping 192.168.1.2`

📶 Si todo está bien, verás:

```
Reply from 192.168.1.2: bytes=32 time<1ms TTL=128
```

¡Felicitaciones! Acabas de simular una red de dos computadoras que **se comunican entre sí** 🎉

---

### 🎓 ¿Por qué es útil Packet Tracer?

- Aprendes a montar redes sin hardware físico.
- Puedes experimentar con IPs, subredes, routers, switches.
- Es ideal para practicar **exámenes de redes y ciberseguridad**.
- No necesitas conexión a internet para usarlo una vez instalado.

---

[🔼](#índice)

---

## **688. Traducción de direcciones públicas a privadas**

### ✅ ¿Qué es la Traducción de Direcciones? (NAT)

**NAT** significa **Network Address Translation** (Traducción de Direcciones de Red). Es una técnica que **convierte direcciones IP privadas en públicas y viceversa**, permitiendo que **dispositivos dentro de una red local accedan a Internet usando una sola IP pública**.

---

#### 🧠 ¿Por qué se usa NAT?

- Las **direcciones IP públicas son limitadas**.
- Las redes locales (casas, empresas) usan **IP privadas** que **no son válidas en Internet**.
- NAT permite que **muchas computadoras privadas compartan una sola IP pública** para conectarse a Internet.

---

### 📥 Direcciones privadas vs públicas

| Tipo de dirección | Rango                                  | Ejemplo             |
| ----------------- | -------------------------------------- | ------------------- |
| **Privadas**      | Clase A: 10.0.0.0 – 10.255.255.255     | 10.0.0.5            |
|                   | Clase B: 172.16.0.0 – 172.31.255.255   | 172.16.5.10         |
|                   | Clase C: 192.168.0.0 – 192.168.255.255 | 192.168.1.100       |
| **Públicas**      | Todas las demás                        | 181.65.10.15 (Perú) |

---

### 🧩 Tipos de NAT

| Tipo                   | Descripción                                         | Ejemplo                                   |
| ---------------------- | --------------------------------------------------- | ----------------------------------------- |
| **Static NAT**         | 1 IP privada ↔ 1 IP pública (asignación fija)       | Servidor web local                        |
| **Dynamic NAT**        | 1 IP privada ↔ 1 IP pública (dinámica, de un grupo) | Usuarios saliendo a internet              |
| **PAT (NAT Overload)** | Muchas IP privadas ↔ 1 IP pública (usa puertos)     | Red doméstica compartiendo una IP pública |

> ✅ **PAT es el más común**: todos los dispositivos de una casa usan **una sola IP pública** asignada por el proveedor de Internet (ISP).

---

### 🧪 Ejemplo para entenderlo (PAT):

Supón que en tu casa tienes 3 dispositivos conectados:

| Dispositivo | IP privada  |
| ----------- | ----------- |
| Laptop      | 192.168.0.2 |
| Celular     | 192.168.0.3 |
| Smart TV    | 192.168.0.4 |

Todos se conectan a Internet a través del router, que tiene una IP pública: `181.64.15.10`.

Cuando navegas a Google:

1. Tu laptop envía una solicitud desde `192.168.0.2:1035` a Google.
2. El router cambia esa IP privada por su IP pública, y añade un número de puerto.
3. Google responde a la IP pública del router (`181.64.15.10:1035`).
4. El router recibe la respuesta y **sabe que debe enviársela a tu laptop (192.168.0.2)**.

Esto lo hace con una tabla de traducción de direcciones NAT.

---

### 🔧 ¿Cómo se configura NAT en Packet Tracer?

Vamos a hacer un ejemplo **PASO A PASO** usando **Cisco Packet Tracer**.

---

#### 🧱 Escenario:

- 1 PC con IP privada: `192.168.1.2`
- Router con 2 interfaces:

  - `Gig0/0`: hacia la red privada (IP: `192.168.1.1`)
  - `Gig0/1`: hacia Internet (IP pública: `181.64.10.1`)

- Usamos NAT para que la PC pueda acceder a una "red pública"

---

#### 🛠 Paso a paso:

##### 1. Asignar IPs en la PC

Ve a la PC > Desktop > IP Configuration:

- IP: `192.168.1.2`
- Máscara: `255.255.255.0`
- Puerta de enlace: `192.168.1.1`

##### 2. Configurar el Router

Entra a CLI y escribe:

```bash
enable
configure terminal

interface gig0/0
ip address 192.168.1.1 255.255.255.0
ip nat inside
no shutdown

interface gig0/1
ip address 181.64.10.1 255.255.255.0
ip nat outside
no shutdown

exit
```

##### 3. Crear una lista de acceso para IPs privadas permitidas

```bash
access-list 1 permit 192.168.1.0 0.0.0.255
```

##### 4. Activar NAT

```bash
ip nat inside source list 1 interface gig0/1 overload
```

> Esto es lo que hace el router NAT tipo PAT (varios dispositivos → 1 IP pública).

---

#### 🧪 Verificar NAT

Puedes hacer “ping” a una PC pública o a una nube configurada en Packet Tracer. También puedes usar:

```bash
show ip nat translations
```

Esto te mostrará cómo el router convierte direcciones privadas en públicas.

---

### 🧠 ¿Qué pasa si no existiera NAT?

- Cada dispositivo necesitaría una IP pública.
- Las direcciones IP públicas **se acabarían muy rápido**.
- Las redes privadas **no podrían acceder a Internet**.

---

### 🎓 Resumen simple

| Pregunta               | Respuesta                                      |
| ---------------------- | ---------------------------------------------- |
| ¿Qué es NAT?           | Traduce IPs privadas en públicas               |
| ¿Para qué sirve?       | Para que redes locales accedan a Internet      |
| ¿Dónde se usa?         | En routers domésticos, empresas, universidades |
| ¿Cuál es el más común? | PAT (NAT con sobrecarga)                       |
| ¿Se puede simular?     | Sí, con Cisco Packet Tracer                    |

---

[🔼](#índice)

---

## **689. Capa de red, las direcciones públicas se han acabado ¿Qué haremos?**

### 🧱 ¿Qué es la Capa de Red?

La **Capa de Red** es la **tercera capa** del modelo OSI. Su función principal es:

- **Encaminar** (rutar) los paquetes desde el origen hasta el destino, incluso si están en redes diferentes.
- Utiliza direcciones **IP** (Internet Protocol).
- Ejemplo de protocolo de esta capa: **IP (v4 y v6)**.

---

#### 🧠 ¿Qué son las direcciones IP?

Una dirección IP identifica a un dispositivo en una red. Por ejemplo:

```
192.168.1.10  (privada)
8.8.8.8       (pública - Google DNS)
```

---

### ⚠️ ¿Por qué se han acabado las direcciones IP públicas?

Porque el protocolo **IPv4** usa **direcciones de 32 bits**, lo que da un máximo de:

```bash
2^32 = 4,294,967,296 direcciones únicas
```

Al comienzo parecía suficiente, pero con:

- Millones de computadoras personales
- Smartphones
- Cámaras IP
- Dispositivos IoT (Internet de las cosas)

➡️ **Ya no alcanza para todos**.

---

### 🛠️ ¿Qué soluciones tenemos?

Cuando se acabaron las IP públicas en IPv4, se implementaron **tres soluciones principales**:

---

#### ✅ 1. NAT (Traducción de Direcciones de Red)

Ya lo viste antes: permite que **muchas IP privadas compartan una IP pública**.

- 🌐 Red interna (192.168.1.0/24) → Router (con 1 IP pública)
- Cada dispositivo usa **la misma IP pública**, pero diferente puerto.

🔧 Ya está instalado en la mayoría de **routers domésticos** o empresariales.

---

#### ✅ 2. Subredes y uso eficiente

Permite dividir una red grande en **pequeñas redes más organizadas** (subredes) usando **máscaras de subred**.

- Ayuda a **no desperdiciar IPs**.
- Ejemplo: en lugar de usar una red completa para 50 PCs, puedes crear una subred específica para ellas con `/26`.

---

#### ✅ 3. IPv6: el futuro (¡y ya presente!)

IPv6 es el reemplazo de IPv4. Usa **direcciones de 128 bits**:

```
2^128 ≈ 340 sextillones de direcciones
```

Suficientes para **cubrir todo el planeta... muchas veces**.

🟢 Ejemplo de dirección IPv6:

```
2001:0db8:85a3:0000:0000:8a2e:0370:7334
```

---

### 💡 Instalación o uso en la vida real

#### 🏠 En una red doméstica:

- Tu proveedor de Internet (ISP) te da **una IP pública**.
- Tu router la usa y, gracias a **NAT**, tus dispositivos internos (con IP privadas) pueden conectarse a Internet.

➡️ Ya estás **usando NAT automáticamente**.

---

#### 🏢 En una empresa:

- Se puede usar:

  - NAT para navegación a Internet.
  - IPv6 si tienen compatibilidad.
  - Subredes para organizar departamentos (por ejemplo: Finanzas, Recursos Humanos).

---

### 🎓 Ejemplo completo y fácil de entender

#### 🎯 Objetivo:

Tienes 3 dispositivos con IP privadas, y quieres que todos puedan navegar por Internet usando **una sola IP pública**.

---

#### 🧱 Elementos:

| Dispositivo | IP privada           |
| ----------- | -------------------- |
| PC1         | 192.168.1.2          |
| PC2         | 192.168.1.3          |
| PC3         | 192.168.1.4          |
| Router      | pública: 181.64.1.10 |
|             | interna: 192.168.1.1 |

---

#### 🛠 ¿Qué hacemos?

1. Cada PC tiene su IP privada.
2. En el router:

   - Configuramos **NAT/PAT**.
   - Configuramos **rutas de salida**.

3. Cuando PC1 visita `google.com`:

   - Su IP privada es reemplazada temporalmente por la IP pública del router.
   - Google responde al router, que reenvía la respuesta a PC1.

✅ ¡Así, todas pueden navegar sin tener una IP pública para cada una!

---

#### 🧰 Comandos básicos de configuración en un router Cisco (Packet Tracer)

```bash
access-list 1 permit 192.168.1.0 0.0.0.255
interface gig0/0
 ip address 192.168.1.1 255.255.255.0
 ip nat inside
interface gig0/1
 ip address 181.64.1.10 255.255.255.0
 ip nat outside

ip nat inside source list 1 interface gig0/1 overload
```

---

### 📌 Resumen final

| Concepto    | Explicación                                              |
| ----------- | -------------------------------------------------------- |
| Capa de red | Ruta paquetes entre redes distintas, usa IPs             |
| Problema    | Se acabaron las IP públicas en IPv4                      |
| Soluciones  | NAT, subredes, e IPv6                                    |
| Ejemplo     | Router compartiendo IP pública con varias PCs usando NAT |

---

[🔼](#índice)

---

## **690. Nombres para humanos vs nombres para máquinas**

### 🧠 ¿Qué significa "Nombres para humanos vs nombres para máquinas"?

En redes computacionales, los **humanos** y las **máquinas** se comunican de forma distinta.

| Humanos                          | Máquinas                        |
| -------------------------------- | ------------------------------- |
| Usan nombres fáciles de recordar | Usan direcciones numéricas      |
| Ej: `google.com`, `youtube.com`  | Ej: `142.250.190.78`, `8.8.8.8` |

---

### 📍 ¿Por qué hay una diferencia?

Porque:

- A nosotros nos resulta fácil recordar palabras (como `chat.openai.com`).
- A las computadoras y routers les resulta más fácil **trabajar con números**, como **direcciones IP**.

Por eso, se creó un sistema que **traduce nombres legibles para humanos en direcciones comprensibles para las máquinas**.

---

### 🌐 ¿Qué hace esa traducción?

El sistema que hace eso se llama:

#### 👉 **DNS** — _Domain Name System_ (Sistema de Nombres de Dominio)

---

### 🔄 ¿Cómo funciona DNS?

Imagina que quieres entrar a `www.google.com`:

1. Escribes el nombre en tu navegador.
2. Tu computadora pregunta a un servidor DNS:
   _"¿Cuál es la IP de `www.google.com`?"_
3. El DNS responde con algo como:
   _"La IP es 142.250.190.78"_
4. Tu computadora se conecta a esa IP (la máquina) pero tú solo viste el nombre (el que entiendes).

---

### 🧱 Ejemplo visual

| Lo que tú haces             | Lo que hace la máquina             |
| --------------------------- | ---------------------------------- |
| Escribes `www.openai.com`   | La PC busca la IP: `104.18.12.123` |
| Entras a `www.facebook.com` | Tu PC encuentra: `31.13.92.36`     |

---

### 🛠️ ¿Cómo se "instala" o configura esto?

#### En una PC o red:

Generalmente, **ya está configurado** automáticamente. Pero tú puedes:

1. **Ver** tu servidor DNS actual:

   - En Windows:
     Abre la terminal (CMD) y escribe:

     ```bash
     ipconfig /all
     ```

     Verás algo como:

     ```
     Servidores DNS . . . . . . : 8.8.8.8
                                8.8.4.4
     ```

     Eso significa que estás usando **DNS de Google**.

2. **Cambiar el DNS manualmente**:

   - En Windows:

     - Ve a Configuración > Red e Internet > Cambiar opciones de adaptador.
     - Haz clic derecho en tu conexión > Propiedades.
     - Selecciona "Protocolo de Internet versión 4 (TCP/IPv4)" > Propiedades.
     - Marca "Usar las siguientes direcciones de servidor DNS":

       - Preferido: `8.8.8.8`
       - Alternativo: `1.1.1.1` (Cloudflare)

---

### 📦 ¿Cómo se aplica en redes más grandes?

En una empresa o centro de datos, puedes tener tu **propio servidor DNS interno**, que:

- Traduce nombres como `intranet.empresa.com` → IP privada.
- Controla a qué recursos puede acceder cada equipo.

---

### 📚 Ejemplo completo

#### 🎯 Objetivo:

Configurar una red en Cisco Packet Tracer donde una PC se conecte a un sitio web usando **nombre de dominio** y no solo la IP.

---

#### 🧰 Elementos:

| Dispositivo | IP           | Rol       |
| ----------- | ------------ | --------- |
| PC0         | 192.168.1.10 | Cliente   |
| ServidorDNS | 192.168.1.2  | DNS + Web |
| Router      | 192.168.1.1  | Gateway   |

---

#### 🛠 Pasos en Packet Tracer:

1. Conecta los dispositivos con cable.

2. Asigna IPs manuales a cada dispositivo.

3. En el **Servidor**, habilita DNS y Web Server:

   - DNS:

     - Host Name: `web.local`
     - IP Address: `192.168.1.2`

   - Web Server:

     - Crea una página web simple.

4. En la **PC0**:

   - IP: `192.168.1.10`
   - Gateway: `192.168.1.1`
   - DNS: `192.168.1.2`

5. En el navegador de PC0, escribe `web.local`.

✅ Si todo está bien configurado, se mostrará la página del servidor web, gracias a la **traducción de nombre a IP** que hace el DNS.

---

### 🎓 Resumen final

| Concepto                   | Explicación                                      |
| -------------------------- | ------------------------------------------------ |
| Nombres para humanos       | Ej: `google.com` — fácil de recordar             |
| Nombres para máquinas      | Ej: `142.250.190.78` — dirección IP              |
| DNS                        | Traduce de nombre a IP automáticamente           |
| Configuración              | Ya viene configurado, pero puedes cambiar el DNS |
| Aplicación en redes reales | Uso de servidores DNS internos o externos        |

---

[🔼](#índice)

---

## **691. ¿Cómo sabe una máquina quién es? Servicio de asignación de direcciones**

### 🌐 ¿Qué significa "quién es" una máquina?

Cuando una computadora o dispositivo se conecta a una red (como el WiFi de tu casa o la red de una empresa), **necesita tener una dirección IP única** para poder comunicarse.

Esa dirección IP es como su **número de identificación** dentro de la red. Sin ella, no puede hablar con nadie.

---

### ❓ Entonces… ¿cómo consigue esa IP?

Hay dos formas:

| Tipo de asignación    | ¿Qué significa?                       |
| --------------------- | ------------------------------------- |
| Manual (estática)     | Tú escribes la IP a mano              |
| Automática (dinámica) | La IP se asigna sola mediante DHCP 🔑 |

---

### 💡 ¿Qué es DHCP?

#### **DHCP** significa:

**D**ynamic **H**ost **C**onfiguration **P**rotocol

Es un **servicio** que automáticamente le **asigna a cada máquina**:

- Dirección IP
- Máscara de subred
- Gateway predeterminado
- Servidor DNS

Todo esto **sin que tú tengas que escribir nada**.

---

### 📦 Ejemplo fácil:

Supongamos que tienes 3 laptops que se conectan a un router WiFi. Ninguna tiene IP configurada.

1. Las laptops envían un mensaje de:
   **"¡Hola! ¿Alguien me da una IP?"** (broadcast)

2. El router (que tiene servicio DHCP activado) responde:
   **"Sí, laptop, usa la IP 192.168.0.10 por ahora"**

3. ¡Listo! Ya puede navegar por internet.

---

### 🔁 ¿Qué más hace DHCP?

- Guarda un **registro** de qué IP tiene cada dispositivo (para no repetirlas).
- Asigna IPs por un **tiempo limitado** (llamado _lease_).
- Puede **renovar o cambiar** IPs automáticamente.

---

### 🛠️ ¿Cómo se instala o activa DHCP?

#### ✅ En casa (router doméstico):

Casi todos los routers **ya vienen con DHCP activado**.

- Puedes acceder al router desde tu navegador:

  - Escribe `192.168.1.1` o `192.168.0.1`
  - Ingresa con usuario y contraseña (ej: `admin` / `admin`)
  - Busca una sección llamada **DHCP Settings**
  - Ahí puedes:

    - Activar o desactivar el servicio
    - Establecer el **rango de IPs** que va a repartir (por ejemplo: de 192.168.0.10 a 192.168.0.100)

---

#### 🖥 En Windows (para recibir IP por DHCP):

1. Ir a:

   - Panel de Control > Redes e Internet > Centro de redes > Cambiar configuración del adaptador

2. Haz clic derecho sobre tu conexión > Propiedades.
3. Selecciona `Protocolo de Internet versión 4 (TCP/IPv4)` > Propiedades.
4. Marca:

   - ✅ Obtener una dirección IP automáticamente
   - ✅ Obtener la dirección del servidor DNS automáticamente

---

#### 🧪 En Packet Tracer (ejemplo simulado):

1. Crea una red con:

   - Un **Router o Switch**
   - Un **Servidor DHCP**
   - Una o más **PCs**

2. Configura el servidor:

   - Activa el servicio DHCP
   - Define el nombre del pool, el gateway, el rango de IPs

3. En las PCs:

   - Configura la red en modo **DHCP** (no le pongas IP manual)

4. Al iniciar, la PC enviará un broadcast y el servidor le asignará una IP.

---

### 📚 Ejemplo completo explicado

#### 🖥 Escenario:

| Dispositivo | IP asignada por DHCP | Función       |
| ----------- | -------------------- | ------------- |
| PC1         | 192.168.1.10         | Cliente DHCP  |
| PC2         | 192.168.1.11         | Cliente DHCP  |
| Router      | 192.168.1.1          | Gateway       |
| Servidor    | 192.168.1.2          | Servidor DHCP |

#### 🔁 Proceso paso a paso:

1. PC1 se conecta → Envia un **DHCP Discover**.
2. El servidor responde con un **DHCP Offer** → le propone una IP.
3. PC1 dice “¡La quiero!” con un **DHCP Request**.
4. El servidor le confirma con **DHCP Acknowledgment** (ACK).

🧠 Este ciclo se llama: **DORA**

- **D**iscover
- **O**ffer
- **R**equest
- **A**ck

---

### 🎓 Resumen

| Concepto                 | Explicación sencilla                            |
| ------------------------ | ----------------------------------------------- |
| ¿Quién da la IP?         | El servidor DHCP                                |
| ¿Qué hace?               | Asigna IP, gateway, DNS automáticamente         |
| ¿Qué evita?              | Que pongas direcciones a mano                   |
| ¿Dónde se encuentra?     | En routers, servidores o switches administrados |
| ¿Cómo se llama el ciclo? | DORA (Discover, Offer, Request, Ack)            |

---

[🔼](#índice)

---

## **692. Rutas ¿Cuál es la ubicación de las máquinas?**

### 🔍 ¿Qué significa “ubicación” en redes?

En una red, **"ubicación"** no se refiere a una dirección física (como una calle), sino a **dónde está una máquina en la red** y **cómo llegar a ella**.

Eso se hace con las **rutas de red (routing)**, que indican el **camino que deben seguir los datos** desde un dispositivo origen hasta el destino.

---

### 🛣️ ¿Qué es una ruta?

Una **ruta** es un conjunto de instrucciones que le dice a los datos:

- Cómo salir de tu red.
- Qué camino tomar para llegar a otra red.
- A través de qué dispositivos deben pasar (routers).

> Es como un GPS digital que guía los paquetes de datos por la red.

---

### 🗺️ Ejemplo muy simple:

Imagina que tienes esta red:

```
[PC1] --- [Router1] --- [Router2] --- [PC2]
```

- PC1 está en la red 192.168.1.0/24
- PC2 está en la red 10.0.0.0/24

Para que **PC1 pueda hablar con PC2**, necesita saber:

- Que debe **enviar los datos a su puerta de enlace (Router1)**.
- Que Router1 **sabe que para llegar a la red 10.0.0.0/24, debe pasar por Router2**.

---

### 🔁 ¿Cómo se establecen las rutas?

Hay **dos tipos principales de rutas**:

| Tipo de ruta  | ¿Quién la configura?       | ¿Cuándo se usa?                         |
| ------------- | -------------------------- | --------------------------------------- |
| Ruta estática | El administrador de red    | Redes pequeñas o controladas            |
| Ruta dinámica | Protocolos de enrutamiento | Redes grandes (usa RIP, OSPF, EIGRP...) |

---

### 🛠️ ¿Cómo se instala o se ve una ruta?

#### ✅ En Windows:

Abre la terminal (CMD) y escribe:

```bash
route print
```

Verás algo como:

```
IPv4 Route Table
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
0.0.0.0                    0.0.0.0          192.168.1.1    192.168.1.100   25
```

🧠 **¿Qué significa esto?**

- `0.0.0.0` significa “todo lo que no conozco”.
- `192.168.1.1` es el **router (puerta de enlace)** por donde deben salir los paquetes.

---

#### ✅ En Linux o Mac:

```bash
ip route show
```

---

#### ✅ Para agregar una ruta manual:

**En Windows (como admin):**

```bash
route add 10.0.0.0 mask 255.255.255.0 192.168.1.1
```

Esto le dice:

> Para llegar a la red 10.0.0.0/24, **usa como puerta de enlace la IP 192.168.1.1**

---

### 🧪 Ejemplo completo (Packet Tracer)

#### 🎯 Objetivo:

Conectar 2 PCs en redes diferentes a través de 2 routers.

#### 🔧 Topología:

```
[PC1]---(R1)---(R2)---[PC2]
```

#### 🧮 Direcciones:

| Dispositivo | IP          | Red            |
| ----------- | ----------- | -------------- |
| PC1         | 192.168.1.2 | 192.168.1.0/24 |
| R1 (G0/0)   | 192.168.1.1 | 192.168.1.0/24 |
| R1 (G0/1)   | 172.16.0.1  | 172.16.0.0/30  |
| R2 (G0/0)   | 172.16.0.2  | 172.16.0.0/30  |
| R2 (G0/1)   | 10.0.0.1    | 10.0.0.0/24    |
| PC2         | 10.0.0.2    | 10.0.0.0/24    |

---

#### 🛠️ Paso a paso:

##### 1. Configura IPs en las interfaces de cada router y PC

(Puedes usar Packet Tracer o hacer la lógica en papel).

##### 2. Establece rutas estáticas:

**En Router 1:**

```bash
ip route 10.0.0.0 255.255.255.0 172.16.0.2
```

**En Router 2:**

```bash
ip route 192.168.1.0 255.255.255.0 172.16.0.1
```

Con esto, ambos routers sabrán cómo llegar a las redes opuestas.

##### 3. Asegúrate de que:

- Las PC tengan su **gateway correcto**:

  - PC1 → 192.168.1.1
  - PC2 → 10.0.0.1

##### 4. Prueba conectividad con `ping`:

Desde PC1:

```bash
ping 10.0.0.2
```

🎉 Si responde, ¡la ruta funciona!

---

### 🧠 ¿Por qué es importante saber esto?

Porque si las máquinas no saben “dónde están” las demás en la red:

- No se pueden comunicar.
- No puedes acceder a servidores ni servicios externos.
- La red puede funcionar solo en partes locales (LAN), pero no más allá.

---

### 📌 Resumen rápido

| Concepto clave        | Explicación                         |
| --------------------- | ----------------------------------- |
| Ruta                  | Camino para llegar a una red        |
| Tabla de enrutamiento | Lista de todos los caminos posibles |
| Gateway               | Salida hacia otras redes            |
| Rutas estáticas       | Manuales, simples                   |
| Rutas dinámicas       | Automáticas, más inteligentes       |

---

[🔼](#índice)

---

## **693. Uso de rutas estáticas**

### 🧠 ¿Qué es una ruta estática?

Una **ruta estática** es una instrucción **manual** que le dice a un router o a un sistema **cómo llegar a una red específica**.

> Es como poner una ruta fija en tu GPS, sin importar si hay tráfico o mejores caminos.

---

### 📌 ¿Por qué usar rutas estáticas?

- Son **simples** de configurar.
- Útiles en redes **pequeñas o controladas**.
- No consumen recursos como los protocolos de enrutamiento dinámico.
- Garantizan que el tráfico siempre tome una ruta específica.

---

### 🧭 Ejemplo simple de la vida real:

Imagina esto:

```
[PC1]---(Router1)---(Router2)---[PC2]
```

- PC1 está en la red **192.168.1.0/24**
- PC2 está en la red **10.0.0.0/24**
- Entre los routers hay una red intermedia: **172.16.0.0/30**

Para que Router1 sepa **cómo llegar a la red 10.0.0.0/24**, necesita que alguien **le diga la ruta**, y eso es lo que hacemos con una **ruta estática**.

---

### 🔧 Sintaxis básica (en Cisco IOS):

```bash
ip route <RED_DESTINO> <MÁSCARA> <PRÓXIMO_SALTO>
```

Por ejemplo:

```bash
ip route 10.0.0.0 255.255.255.0 172.16.0.2
```

Esto le dice a Router1:

> Si quieres llegar a la red 10.0.0.0/24, **envía los datos a 172.16.0.2**, que es el otro router (Router2).

---

### 💻 ¿Cómo se instala una ruta estática?

#### 🖥️ En routers Cisco (como en Packet Tracer):

1. Entra al router:

```bash
Router> enable
Router# configure terminal
```

2. Agrega la ruta:

```bash
Router(config)# ip route 10.0.0.0 255.255.255.0 172.16.0.2
```

3. Sal y guarda:

```bash
Router(config)# exit
Router# write memory
```

---

#### 🖥️ En Windows (como administrador):

```bash
route add 10.0.0.0 mask 255.255.255.0 192.168.1.1
```

Esto indica que para llegar a **10.0.0.0/24**, debes ir a través del router **192.168.1.1**

---

### 🔁 ¿Cómo verificar las rutas?

#### 🧪 En Windows:

```bash
route print
```

#### 🧪 En Cisco IOS:

```bash
show ip route
```

---

### 🧪 Ejemplo completo (Packet Tracer)

#### 🎯 Objetivo:

Conectar dos redes diferentes usando dos routers y rutas estáticas.

---

#### 🔧 Topología:

```
[PC1]---(R1)---(R2)---[PC2]
```

#### 📋 Configuración de IPs:

| Dispositivo | Interfaz | IP          | Red            |
| ----------- | -------- | ----------- | -------------- |
| PC1         | -        | 192.168.1.2 | 192.168.1.0/24 |
| R1          | G0/0     | 192.168.1.1 | 192.168.1.0/24 |
| R1          | G0/1     | 172.16.0.1  | 172.16.0.0/30  |
| R2          | G0/0     | 172.16.0.2  | 172.16.0.0/30  |
| R2          | G0/1     | 10.0.0.1    | 10.0.0.0/24    |
| PC2         | -        | 10.0.0.2    | 10.0.0.0/24    |

---

#### 🛠️ Configura los dispositivos:

##### 1. Asigna IPs en cada router (modo CLI):

**En Router1:**

```bash
interface g0/0
ip address 192.168.1.1 255.255.255.0
no shutdown

interface g0/1
ip address 172.16.0.1 255.255.255.252
no shutdown
```

**En Router2:**

```bash
interface g0/0
ip address 172.16.0.2 255.255.255.252
no shutdown

interface g0/1
ip address 10.0.0.1 255.255.255.0
no shutdown
```

---

#### 2. Agrega las rutas estáticas:

**En R1 (para llegar a la red 10.0.0.0):**

```bash
ip route 10.0.0.0 255.255.255.0 172.16.0.2
```

**En R2 (para llegar a la red 192.168.1.0):**

```bash
ip route 192.168.1.0 255.255.255.0 172.16.0.1
```

---

#### 3. Configura gateway en las PCs:

- En **PC1**, gateway = **192.168.1.1**
- En **PC2**, gateway = **10.0.0.1**

---

#### ✅ Prueba:

Desde PC1, abre la terminal y escribe:

```bash
ping 10.0.0.2
```

Desde PC2, haz:

```bash
ping 192.168.1.2
```

👉 Si todo está bien configurado, verás que las respuestas llegan correctamente.

---

### 🎓 Conclusión

| Concepto       | Detalle                                                             |
| -------------- | ------------------------------------------------------------------- |
| ¿Qué es?       | Una ruta manual que indica cómo llegar a otra red.                  |
| ¿Dónde se usa? | En routers, servidores o computadoras con múltiples redes.          |
| ¿Ventajas?     | Control total, simple en redes pequeñas.                            |
| ¿Desventajas?  | No escala bien en redes grandes. Cambios deben hacerse manualmente. |

---

[🔼](#índice)

---

## **694. Configuración de rutas estáticas**

### 🧠 ¿Qué es una ruta estática?

Una **ruta estática** es una **instrucción manual** que le damos a un router para indicarle **por dónde enviar los datos** cuando quiera llegar a una red específica.

> Es como poner una dirección en tu GPS de forma manual, sin que el GPS busque la mejor ruta automáticamente.

---

### 📌 ¿Para qué sirve?

Las rutas estáticas son útiles cuando:

- La red es **pequeña** o **no cambia mucho**.
- No queremos que los routers gasten recursos calculando rutas.
- Necesitamos **control total** sobre las rutas.
- Queremos tener rutas de **respaldo** (backup).

---

### 🏗️ ¿Cómo funciona?

Imagina esta red:

```
PC1 ── Router1 ── Router2 ── PC2
```

- **PC1:** red 192.168.1.0/24
- **PC2:** red 10.0.0.0/24
- **Red entre routers:** 172.16.0.0/30

Para que **Router1 sepa cómo llegar a PC2**, necesita una **ruta estática** que le diga:

> "Si quieres llegar a la red 10.0.0.0/24, **envía los datos a Router2 (IP 172.16.0.2)**".

---

### 🛠️ Comando básico (en routers Cisco):

```bash
ip route <red_destino> <máscara> <ip_del_próximo_salto>
```

Ejemplo:

```bash
ip route 10.0.0.0 255.255.255.0 172.16.0.2
```

---

### 🧪 Ejemplo completo en Packet Tracer

#### 🎯 Objetivo:

Conectar dos PCs a través de dos routers usando rutas estáticas.

#### 🧱 Topología:

```
PC1 ── R1 ── R2 ── PC2
```

#### 📋 Direcciones IP:

| Dispositivo | Interfaz      | IP          | Red            |
| ----------- | ------------- | ----------- | -------------- |
| PC1         | FastEthernet0 | 192.168.1.2 | 192.168.1.0/24 |
| R1          | G0/0          | 192.168.1.1 | 192.168.1.0/24 |
| R1          | G0/1          | 172.16.0.1  | 172.16.0.0/30  |
| R2          | G0/0          | 172.16.0.2  | 172.16.0.0/30  |
| R2          | G0/1          | 10.0.0.1    | 10.0.0.0/24    |
| PC2         | FastEthernet0 | 10.0.0.2    | 10.0.0.0/24    |

---

#### 🧰 Paso 1: Configurar IPs en los routers

##### En **Router1**:

```bash
enable
configure terminal

interface g0/0
ip address 192.168.1.1 255.255.255.0
no shutdown

interface g0/1
ip address 172.16.0.1 255.255.255.252
no shutdown
```

##### En **Router2**:

```bash
enable
configure terminal

interface g0/0
ip address 172.16.0.2 255.255.255.252
no shutdown

interface g0/1
ip address 10.0.0.1 255.255.255.0
no shutdown
```

---

#### ⚙️ Paso 2: Configurar IPs y gateway en las PCs

##### En **PC1**:

- IP: 192.168.1.2
- Máscara: 255.255.255.0
- Gateway: 192.168.1.1

##### En **PC2**:

- IP: 10.0.0.2
- Máscara: 255.255.255.0
- Gateway: 10.0.0.1

---

#### 🛣️ Paso 3: Configurar rutas estáticas

##### En **Router1** (para llegar a la red de PC2):

```bash
ip route 10.0.0.0 255.255.255.0 172.16.0.2
```

##### En **Router2** (para llegar a la red de PC1):

```bash
ip route 192.168.1.0 255.255.255.0 172.16.0.1
```

---

#### ✅ Paso 4: Probar conectividad

Desde **PC1**:

```bash
ping 10.0.0.2
```

Desde **PC2**:

```bash
ping 192.168.1.2
```

---

### 🧠 ¿Cómo lo verifico?

#### En los routers:

```bash
show ip route
```

Verás las rutas manuales con una letra **S** (de Static).

---

### 📝 Ventajas y desventajas

| Ventajas                 | Desventajas                                    |
| ------------------------ | ---------------------------------------------- |
| Fácil de configurar      | No se adapta a cambios automáticos             |
| Menor uso de CPU/memoria | Poco escalable en redes grandes                |
| Más seguridad/control    | Puede provocar errores si se omite alguna ruta |

---

### 🎓 Conclusión

Las **rutas estáticas** son ideales para redes pequeñas o cuando quieres tener **control total del tráfico**. Son fáciles de configurar, entender y depurar. Este tipo de rutas se usa mucho en **laboratorios**, **empresas pequeñas**, y para **respaldo** de rutas dinámicas.

---

[🔼](#índice)

---

## **695. Rutas dinámicas: cuando los enrutadores aprenden por sí mismos**

### 🧠 ¿Qué son las rutas dinámicas?

Las **rutas dinámicas** son aquellas que **aprenden los routers automáticamente** usando **protocolos de enrutamiento dinámico** como:

- **RIP (Routing Information Protocol)**
- **OSPF (Open Shortest Path First)**
- **EIGRP (Enhanced Interior Gateway Routing Protocol)**

👉 En lugar de configurarlas manualmente como las rutas estáticas, los routers se **comunican entre ellos** para compartir qué redes conocen y cuál es el mejor camino para llegar.

---

### 🧩 Ejemplo fácil de la vida real

Imagina tres ciudades conectadas con carreteras: Lima, Cusco y Arequipa. Si cada ciudad le dice a las otras **qué caminos tiene abiertos** y cuánto demora llegar, pueden encontrar la mejor ruta automáticamente. ¡Eso hacen los routers con las rutas dinámicas!

---

### 🛠️ ¿Cómo se instala o activa?

Debes **habilitar un protocolo de enrutamiento** en los routers.

Por ejemplo, si usas **RIP**, se configura así:

```bash
router rip
version 2
network [red conectada al router]
```

Esto le dice al router:

> "Usa RIP y avísales a tus vecinos sobre tus rutas disponibles".

---

### 🚦 ¿Qué protocolo de enrutamiento escojo?

| Protocolo | Fácil de usar | Rápido | Escalable | Ideal para…                   |
| --------- | ------------- | ------ | --------- | ----------------------------- |
| **RIP**   | ✅ Sí         | 🚫 No  | 🚫 No     | Redes pequeñas (laboratorios) |
| **OSPF**  | ☑️ Medio      | ✅ Sí  | ✅ Sí     | Redes grandes y complejas     |
| **EIGRP** | ☑️ Medio      | ✅ Sí  | ✅ Sí     | Solo Cisco, redes medianas    |

Para este ejemplo, **usaremos RIP** por su facilidad.

---

### 🧪 EJEMPLO COMPLETO: Rutas dinámicas con RIP en Packet Tracer

#### 🎯 Objetivo

Conectar tres routers entre sí para que compartan rutas automáticamente y los **PCs puedan comunicarse** entre redes.

#### 🧱 Topología

```
PC1 ── R1 ── R2 ── R3 ── PC2
```

#### 📋 Direccionamiento IP

| Dispositivo | Interfaz      | IP          | Red            |
| ----------- | ------------- | ----------- | -------------- |
| PC1         | FastEthernet0 | 192.168.1.2 | 192.168.1.0/24 |
| R1          | G0/0          | 192.168.1.1 | 192.168.1.0/24 |
| R1          | G0/1          | 10.0.0.1    | 10.0.0.0/30    |
| R2          | G0/0          | 10.0.0.2    | 10.0.0.0/30    |
| R2          | G0/1          | 10.0.0.5    | 10.0.0.4/30    |
| R3          | G0/0          | 10.0.0.6    | 10.0.0.4/30    |
| R3          | G0/1          | 192.168.2.1 | 192.168.2.0/24 |
| PC2         | FastEthernet0 | 192.168.2.2 | 192.168.2.0/24 |

---

#### 🧰 Paso 1: Configurar IPs en los routers

##### En R1

```bash
enable
configure terminal

interface g0/0
ip address 192.168.1.1 255.255.255.0
no shutdown

interface g0/1
ip address 10.0.0.1 255.255.255.252
no shutdown
```

##### En R2

```bash
enable
configure terminal

interface g0/0
ip address 10.0.0.2 255.255.255.252
no shutdown

interface g0/1
ip address 10.0.0.5 255.255.255.252
no shutdown
```

##### En R3

```bash
enable
configure terminal

interface g0/0
ip address 10.0.0.6 255.255.255.252
no shutdown

interface g0/1
ip address 192.168.2.1 255.255.255.0
no shutdown
```

---

#### 🧰 Paso 2: Configurar IPs en PCs

##### PC1

- IP: 192.168.1.2
- Máscara: 255.255.255.0
- Gateway: 192.168.1.1

##### PC2

- IP: 192.168.2.2
- Máscara: 255.255.255.0
- Gateway: 192.168.2.1

---

#### 🔁 Paso 3: Activar RIP en cada router

##### En R1

```bash
router rip
version 2
no auto-summary
network 192.168.1.0
network 10.0.0.0
```

##### En R2

```bash
router rip
version 2
no auto-summary
network 10.0.0.0
```

##### En R3

```bash
router rip
version 2
no auto-summary
network 10.0.0.0
network 192.168.2.0
```

> 📌 Nota: `no auto-summary` evita que RIP resuma mal las redes. Es buena práctica.

---

#### ✅ Paso 4: Verifica conectividad

En **PC1**:

```bash
ping 192.168.2.2
```

En **PC2**:

```bash
ping 192.168.1.2
```

---

#### 👀 Paso 5: Verifica las rutas aprendidas

En cada router:

```bash
show ip route
```

Verás rutas con la letra **R** indicando que fueron aprendidas por **RIP**.

---

### 📌 Ventajas de rutas dinámicas

✅ No necesitas configurarlas todas a mano.

✅ Se ajustan solas si un enlace cae.

✅ Son ideales para redes medianas y grandes.

✅ Ahorra tiempo en la administración.

---

### ⚠️ Desventajas

🚫 Consumen más recursos.

🚫 Pueden ser vulnerables si no se aseguran bien.

🚫 RIP no es ideal para redes grandes (mejor OSPF o EIGRP).

---

### 🎓 Conclusión

Las **rutas dinámicas** permiten que los routers **aprendan solos** cómo llegar a otras redes, **mejorando la eficiencia** y reduciendo errores humanos. Son muy usadas en redes reales, y en este ejemplo aprendiste a configurarlas fácilmente usando **RIP**.

---

[🔼](#índice)

---

## **696. Configuración de rutas dinámicas**

### 🧠 ¿Qué es la configuración de rutas dinámicas?

En redes, las **rutas dinámicas** son aquellas que los routers **aprenden automáticamente** usando **protocolos de enrutamiento dinámico**, en lugar de que un administrador las configure manualmente.

Los protocolos más usados son:

- **RIP** (Routing Information Protocol): ideal para comenzar, fácil.
- **OSPF** (Open Shortest Path First): más eficiente, para redes medianas o grandes.
- **EIGRP** (Enhanced Interior Gateway Routing Protocol): exclusivo de Cisco, rápido.

---

### 🧩 ¿Por qué usar rutas dinámicas?

Imagina que administras una empresa con **10 routers**. Si una ruta cae (por ejemplo, un cable cortado), con rutas estáticas tendrías que reconfigurarlas todas manualmente. Con rutas dinámicas, los routers **se comunican entre ellos** y **aprenden automáticamente nuevas rutas disponibles**.

---

### 🚦 Ejemplo de la vida real (fácil de entender)

📍 Supón que tienes tres ciudades conectadas (como routers):

- **Lima**, **Cusco**, y **Arequipa**.

Si cada ciudad (router) **comparte con sus vecinos las rutas que conoce**, todos pueden aprender cómo llegar a las otras ciudades sin que tú les digas exactamente cómo. Eso hacen las rutas dinámicas.

---

### 🛠️ ¿Cómo se instala y configura una ruta dinámica?

Usaremos **Packet Tracer** y configuraremos el protocolo **RIP**, que es muy fácil y perfecto para empezar.

---

### 🔧 EJEMPLO COMPLETO – Rutas dinámicas con RIP

#### 🎯 Objetivo

Conectar tres routers con redes diferentes y permitir que los PCs puedan comunicarse automáticamente, **sin usar rutas estáticas**.

---

#### 🧱 Topología

```
PC1 ── R1 ── R2 ── R3 ── PC2
```

---

#### 📋 Direccionamiento IP

| Dispositivo | Interfaz      | Dirección IP | Red            |
| ----------- | ------------- | ------------ | -------------- |
| PC1         | FastEthernet0 | 192.168.1.2  | 192.168.1.0/24 |
| R1 G0/0     |               | 192.168.1.1  | 192.168.1.0/24 |
| R1 G0/1     |               | 10.0.0.1     | 10.0.0.0/30    |
| R2 G0/0     |               | 10.0.0.2     | 10.0.0.0/30    |
| R2 G0/1     |               | 10.0.0.5     | 10.0.0.4/30    |
| R3 G0/0     |               | 10.0.0.6     | 10.0.0.4/30    |
| R3 G0/1     |               | 192.168.2.1  | 192.168.2.0/24 |
| PC2         | FastEthernet0 | 192.168.2.2  | 192.168.2.0/24 |

---

### 🧰 Paso 1: Configura las IPs en los routers

#### ▶ R1

```bash
enable
configure terminal

interface g0/0
ip address 192.168.1.1 255.255.255.0
no shutdown

interface g0/1
ip address 10.0.0.1 255.255.255.252
no shutdown
```

---

#### ▶ R2

```bash
enable
configure terminal

interface g0/0
ip address 10.0.0.2 255.255.255.252
no shutdown

interface g0/1
ip address 10.0.0.5 255.255.255.252
no shutdown
```

---

#### ▶ R3

```bash
enable
configure terminal

interface g0/0
ip address 10.0.0.6 255.255.255.252
no shutdown

interface g0/1
ip address 192.168.2.1 255.255.255.0
no shutdown
```

---

### 💻 Paso 2: Configura las IPs de los PCs

#### ▶ PC1

- Dirección IP: `192.168.1.2`
- Máscara: `255.255.255.0`
- Gateway: `192.168.1.1`

#### ▶ PC2

- Dirección IP: `192.168.2.2`
- Máscara: `255.255.255.0`
- Gateway: `192.168.2.1`

---

### 🔁 Paso 3: Activar el protocolo RIP en los routers

#### ▶ En R1

```bash
router rip
version 2
no auto-summary
network 192.168.1.0
network 10.0.0.0
```

#### ▶ En R2

```bash
router rip
version 2
no auto-summary
network 10.0.0.0
```

#### ▶ En R3

```bash
router rip
version 2
no auto-summary
network 10.0.0.0
network 192.168.2.0
```

> 📌 RIP versión 2 permite usar subredes (RIPv1 no las soporta).
>
> 📌 `network` indica qué redes anunciará el router a sus vecinos.
>
> 📌 `no auto-summary` evita que resuma automáticamente (mejor práctica).

---

### ✅ Paso 4: Verificar conectividad

Desde **PC1**:

```bash
ping 192.168.2.2
```

Desde **PC2**:

```bash
ping 192.168.1.2
```

¡Si todo está bien configurado, los pings deben responder correctamente!

---

### 🔍 Paso 5: Comprobar que los routers aprendieron rutas

En cada router escribe:

```bash
show ip route
```

Verás algo como:

```
R    192.168.2.0/24 [120/1] via 10.0.0.5, 00:00:12, GigabitEthernet0/1
```

La letra **R** significa que la ruta fue aprendida por **RIP**.

---

### 🧠 ¿Qué aprendiste aquí?

- Las rutas dinámicas permiten que los routers **aprendan automáticamente** cómo comunicarse.
- Usamos el protocolo **RIP v2**, que es sencillo y útil para redes pequeñas.
- No necesitas escribir una ruta para cada red: RIP se encarga de ello.
- Los routers **intercambian información** y se adaptan si una red cambia o se cae.

---

### 💡 ¿Y si quiero usar OSPF o EIGRP?

También se puede. Aquí un ejemplo rápido con **OSPF** en R1:

```bash
router ospf 1
network 192.168.1.0 0.0.0.255 area 0
network 10.0.0.0 0.0.0.3 area 0
```

OSPF necesita saber qué redes usar (con máscara wildcard) y a qué **área** pertenecen (normalmente `area 0`).

---

### 🎁 ¿Deseas el archivo `.pkt` de este laboratorio?

Si quieres que te lo cree para abrirlo directamente en **Packet Tracer**, solo dímelo y te lo entrego.

---

[🔼](#índice)

---

## **697. Apuntes: rutas estáticas y dinámicas**

### 📌 ¿Qué es una ruta?

Una **ruta** es el **camino que sigue un paquete de datos** desde un origen hasta un destino a través de una red. Los **routers** se encargan de decidir por qué camino enviarán los datos.

---

### 🧭 Tipos de rutas

Existen **dos formas principales** de decirle a un router cómo llegar a otra red:

| Tipo de Ruta      | ¿Cómo se configura?             | ¿Cuándo se usa?                     |
| ----------------- | ------------------------------- | ----------------------------------- |
| **Ruta Estática** | Manualmente, por un admin       | Redes pequeñas o controladas        |
| **Ruta Dinámica** | Automáticamente, con protocolos | Redes medianas o grandes, flexibles |

---

### 🚦 1. RUTAS ESTÁTICAS

#### 🧠 ¿Qué es?

Una **ruta estática** es una instrucción fija que le dice al router:

“**Para llegar a esta red, usa esta puerta de salida (interfaz) o este vecino (next-hop).**”

#### ✅ Ventajas

- Simples de entender y configurar.
- Usan pocos recursos.
- Predecibles.

#### ❌ Desventajas

- No se adaptan solas a cambios (cortes, nuevas rutas).
- Mantenimiento manual si crece la red.

---

#### 🛠️ Ejemplo fácil

🧱 Topología:

```
PC1 ── R1 ── R2 ── PC2
```

#### Direccionamiento:

- PC1: `192.168.1.2/24`, Gateway: `192.168.1.1`
- PC2: `192.168.2.2/24`, Gateway: `192.168.2.1`
- R1 a R2: `10.0.0.1/30` (R1), `10.0.0.2/30` (R2)

---

#### ▶ En R1:

```bash
ip route 192.168.2.0 255.255.255.0 10.0.0.2
```

👉 Le estás diciendo a R1:

> “Para llegar a la red 192.168.2.0, envía los paquetes al router 10.0.0.2”

---

#### ▶ En R2:

```bash
ip route 192.168.1.0 255.255.255.0 10.0.0.1
```

---

### 🔁 2. RUTAS DINÁMICAS

#### 🧠 ¿Qué es?

Las **rutas dinámicas** se configuran usando **protocolos de enrutamiento** como:

- **RIP** (Routing Information Protocol)
- **OSPF** (Open Shortest Path First)
- **EIGRP** (Cisco)

Estos protocolos permiten que los routers:

- **Detecten automáticamente otras redes**
- **Se comuniquen entre ellos**
- **Cambien de ruta si una se cae**

---

#### ✅ Ventajas

- Se adaptan solas.
- Buenas para redes con muchos routers.
- Se actualizan automáticamente.

#### ❌ Desventajas

- Consumen más CPU y ancho de banda.
- Configuración un poco más técnica.

---

#### 🛠️ Ejemplo fácil con RIP

##### ▶ En R1:

```bash
router rip
version 2
no auto-summary
network 192.168.1.0
network 10.0.0.0
```

##### ▶ En R2:

```bash
router rip
version 2
no auto-summary
network 10.0.0.0
network 192.168.2.0
```

Los routers intercambiarán rutas automáticamente.

---

### 🧠 ¿Cuándo usar cuál?

| Situación                                      | Mejor opción     |
| ---------------------------------------------- | ---------------- |
| Red pequeña, estable, sin muchos cambios       | Ruta Estática    |
| Red grande, muchos routers, cambios frecuentes | Ruta Dinámica    |
| Red híbrida (core estable, borde flexible)     | Ambas combinadas |

---

### 💻 ¿Cómo se instalan en la práctica?

Usaremos **Cisco Packet Tracer** (si no lo tienes, puedo ayudarte a instalarlo).

---

### ✅ EJEMPLO COMPLETO

#### Topología:

```
PC1 ── R1 ── R2 ── PC2
```

#### Direccionamiento:

| Dispositivo | IP          | Interfaz |
| ----------- | ----------- | -------- |
| PC1         | 192.168.1.2 | Fa0      |
| R1 G0/0     | 192.168.1.1 | G0/0     |
| R1 G0/1     | 10.0.0.1    | G0/1     |
| R2 G0/0     | 10.0.0.2    | G0/0     |
| R2 G0/1     | 192.168.2.1 | G0/1     |
| PC2         | 192.168.2.2 | Fa0      |

---

#### 📍 Parte A: Con rutas **estáticas**

##### En R1:

```bash
ip route 192.168.2.0 255.255.255.0 10.0.0.2
```

##### En R2:

```bash
ip route 192.168.1.0 255.255.255.0 10.0.0.1
```

📌 Luego haces ping desde PC1 a PC2 (`ping 192.168.2.2`) → ¡Éxito!

---

#### 📍 Parte B: Con rutas **dinámicas** (RIP)

##### En R1:

```bash
router rip
version 2
no auto-summary
network 192.168.1.0
network 10.0.0.0
```

##### En R2:

```bash
router rip
version 2
no auto-summary
network 192.168.2.0
network 10.0.0.0
```

❗ Elimina las rutas estáticas antes de probar rutas dinámicas. Luego haz ping → funciona.

---

### 🧾 RESUMEN

| Aspecto              | Ruta Estática    | Ruta Dinámica             |
| -------------------- | ---------------- | ------------------------- |
| ¿Quién la configura? | El administrador | El router (con protocolo) |
| ¿Reacciona a fallas? | ❌ No            | ✅ Sí                     |
| ¿Es flexible?        | ❌ No            | ✅ Sí                     |
| ¿Consume recursos?   | ✅ Bajo          | ⚠️ Medio a Alto           |
| ¿Escalable?          | ❌ Poco          | ✅ Mucho                  |

---

[🔼](#índice)

---

## **698. Convergencia de enrutamiento, cuando todos los enrutadores están de acuerdo**

### 🧠 ¿Qué es la convergencia de enrutamiento?

**Convergencia** es el proceso mediante el cual **todos los routers en una red dinámica aprenden y se ponen de acuerdo sobre las mejores rutas hacia todas las redes disponibles**.

> Es como cuando varios GPS en autos se actualizan al mismo tiempo y muestran la misma mejor ruta hacia un lugar después de un accidente.

---

#### 🕓 ¿Cuándo ocurre?

- Cuando se **encienden todos los routers**.
- Cuando **cambia una ruta** (por ejemplo, si un enlace se cae).
- Cuando se **agrega una nueva red**.

---

### 🚦 ¿Por qué es importante?

Porque **hasta que todos los routers tengan la misma información de enrutamiento**, puede haber pérdida de paquetes o decisiones incorrectas de ruta.

> Una red **no está estable** hasta que **todos los routers tienen las rutas correctas**.

---

### 🧩 ¿Qué factores influyen en la convergencia?

| Factor                    | Efecto sobre la convergencia               |
| ------------------------- | ------------------------------------------ |
| Protocolo de enrutamiento | Algunos convergen más rápido (OSPF, EIGRP) |
| Velocidad del enlace      | Influye en qué tan rápido se comunican     |
| Cantidad de routers/redes | Más dispositivos = más tiempo              |
| Cambios en la red         | Cuantos más cambios, más demora            |

---

### 🔄 Ejemplo fácil de entender

Imagina tres routers conectados:

```
R1 ─── R2 ─── R3
```

Cada uno conectado a su propia red:

- R1: 192.168.1.0/24
- R2: 192.168.2.0/24
- R3: 192.168.3.0/24

Todos usan el **protocolo RIP**.

#### Escenario:

1. R1 enciende y conoce solo su red.
2. R2 se conecta a R1 y aprenden uno del otro.
3. R3 se conecta a R2.
4. RIP intercambia información cada 30 segundos.
5. **Después de un tiempo**, todos los routers conocen TODAS las redes.

✅ En ese momento, la red ha **convergido**.

---

### ⌛ ¿Qué pasa si una ruta cae?

1. Supongamos que el enlace entre R2 y R3 se rompe.
2. R2 y R3 notan la desconexión.
3. Usando RIP (que tiene un **temporizador de 180 segundos para "inaccesible"**), eventualmente eliminan la ruta.
4. Vuelven a converger con la nueva topología.

---

### 🔁 ¿Qué protocolos convergen más rápido?

| Protocolo | Tiempo aproximado de convergencia | Tipo                |
| --------- | --------------------------------- | ------------------- |
| RIP       | 3 a 6 minutos                     | Distancia vectorial |
| OSPF      | Segundos a 1 minuto               | Estado de enlace    |
| EIGRP     | Casi en tiempo real               | Híbrido             |
| BGP       | Minutos a horas (global)          | Path Vector         |

---

### 💻 ¿Cómo se instala en la práctica?

Usaremos **Cisco Packet Tracer** para probar esto.

---

### ✅ EJEMPLO COMPLETO EN PACKET TRACER

#### Topología:

```
PC1 ─ R1 ─ R2 ─ R3 ─ PC2
```

---

#### Direccionamiento:

| Dispositivo | IP          | Interfaz |
| ----------- | ----------- | -------- |
| PC1         | 192.168.1.2 | Fa0      |
| R1 Fa0/0    | 192.168.1.1 | Fa0/0    |
| R1 Fa0/1    | 10.0.0.1    | Fa0/1    |
| R2 Fa0/0    | 10.0.0.2    | Fa0/0    |
| R2 Fa0/1    | 10.0.1.1    | Fa0/1    |
| R3 Fa0/0    | 10.0.1.2    | Fa0/0    |
| R3 Fa0/1    | 192.168.3.1 | Fa0/1    |
| PC2         | 192.168.3.2 | Fa0      |

---

#### Paso 1: Configurar RIP en cada router

##### ▶ R1:

```bash
router rip
version 2
no auto-summary
network 192.168.1.0
network 10.0.0.0
```

##### ▶ R2:

```bash
router rip
version 2
no auto-summary
network 10.0.0.0
network 10.0.1.0
```

##### ▶ R3:

```bash
router rip
version 2
no auto-summary
network 10.0.1.0
network 192.168.3.0
```

---

#### Paso 2: Ver la convergencia

1. Usa el comando `show ip route` en cada router.
2. Espera \~1 minuto.
3. Verás todas las redes conocidas.

---

#### Paso 3: Prueba la red

Desde **PC1**, haz ping a **PC2**:

```bash
ping 192.168.3.2
```

✅ Si hay respuesta, ¡la red ha convergido!

---

### 🧠 Conclusión

- **Convergencia** es cuando todos los routers conocen todas las rutas posibles.
- Es **clave para la estabilidad** de una red dinámica.
- Se logra con **protocolos de enrutamiento** como RIP, OSPF o EIGRP.
- El **tiempo de convergencia** depende del protocolo y la red.

---

[🔼](#índice)

---

## **699. Necesidad del diseño de la topología de LAN**

### ✅ ¿Qué es una LAN?

**LAN** significa **Local Area Network** o **Red de Área Local**.
Es una red que conecta dispositivos **dentro de una zona pequeña**, como:

- Una casa
- Una oficina
- Un colegio
- Un laboratorio

---

### 🧠 ¿Qué es una _topología de red_?

Es la forma en la que se **organizan y conectan** los dispositivos (PCs, routers, switches, etc.) dentro de la red.

> Imagina que estás haciendo un plano de una casa. La topología es como decides **distribuir los muebles y pasillos** para que todo funcione bien.

---

### 🎯 ¿Por qué es NECESARIO diseñar una topología LAN?

Diseñar una topología LAN antes de implementar la red tiene muchas **ventajas**:

| Razón                           | ¿Por qué es importante?                                 |
| ------------------------------- | ------------------------------------------------------- |
| 1. ✅ Mejora el rendimiento     | Optimiza el tráfico y evita cuellos de botella          |
| 2. ✅ Facilita la escalabilidad | Puedes agregar más dispositivos sin caos                |
| 3. ✅ Reduce costos             | Evitas gastar en cables o dispositivos innecesarios     |
| 4. ✅ Mayor confiabilidad       | Si algo falla, sabes dónde y por qué                    |
| 5. ✅ Ayuda en el mantenimiento | Un diseño claro facilita detectar y reparar fallos      |
| 6. ✅ Mejora la seguridad       | Puedes controlar mejor qué parte de la red es accesible |

---

### 🔁 Tipos comunes de topología LAN

| Tipo de topología | Descripción fácil                                           | Ventajas                     | Desventajas                        |
| ----------------- | ----------------------------------------------------------- | ---------------------------- | ---------------------------------- |
| **Bus**           | Todos los dispositivos conectados a un solo cable           | Simple, barata               | Si el cable falla, toda la red cae |
| **Estrella**      | Todos los dispositivos se conectan a un switch              | Fácil de mantener, muy usada | Si el switch falla, se cae la red  |
| **Anillo**        | Cada dispositivo se conecta al siguiente formando un anillo | Ordenado                     | Lento y difícil de escalar         |
| **Malla**         | Todos conectados con todos                                  | Alta redundancia             | Muy costoso y complejo             |
| **Híbrida**       | Combinación de dos o más topologías                         | Flexible                     | Requiere buen diseño               |

---

### 📦 ¿Cómo se "instala" una topología LAN?

La instalación real implica:

#### 🔧 Paso 1: Planificación

- ¿Cuántas PCs tendrás?
- ¿Necesitas acceso a Internet?
- ¿Dónde estarán los equipos?
- ¿Qué tipo de topología usarás? (por lo general **estrella**)

#### 💡 Paso 2: Elección de equipos

- **Switches o routers**
- **Cables Ethernet (UTP Cat5e, Cat6)**
- **Patch panel (opcional)**
- **Tarjetas de red**

#### 🔌 Paso 3: Cableado físico

- Tiras cables desde cada PC al **switch**
- Se etiquetan y organizan para futuras reparaciones

#### 🖥️ Paso 4: Configuración lógica

- Asignas direcciones IP
- Configuras servicios como DHCP o DNS
- Segmentas por VLAN si es necesario

---

### 👨‍🏫 Ejemplo fácil de entender: Oficina de 4 computadoras

#### 🎯 Objetivo:

Conectar 4 computadoras en red para que compartan archivos e impresoras.

#### 🗺️ Diseño:

Usaremos topología **estrella**.

```
PC1       PC2       PC3       PC4
 |         |         |         |
 +---------+---------+---------+
           SWITCH
             |
         Internet (opcional)
```

---

#### 📋 Equipos necesarios:

- 1 switch de 8 puertos
- 4 cables Ethernet (Cat6)
- 4 computadoras
- Opcional: router con acceso a Internet

---

#### ⚙️ Instalación:

1. **Conecta cada PC al switch** usando cables de red.
2. **Configura las IPs** manualmente o usa un router con DHCP.

   - Ejemplo:

     - PC1: 192.168.1.2
     - PC2: 192.168.1.3
     - etc.

3. **Verifica conectividad** con `ping`.
4. **Comparte carpetas o impresoras** desde una PC para el resto.
5. (Opcional) Conecta el switch a un router para tener Internet.

---

#### 🧪 Prueba:

En **PC1** abre la terminal (o CMD):

```bash
ping 192.168.1.3
```

✅ Si responde, ¡la red LAN está funcionando!

---

### 📌 Resumen

- La **topología LAN** define cómo se conectan los dispositivos.
- Su diseño **mejora el rendimiento, organización y crecimiento** de la red.
- La **topología estrella** es la más usada en oficinas y hogares.
- Antes de instalar, siempre planifica: número de dispositivos, tipo de tráfico, y seguridad.

---

[🔼](#índice)

---

## **700. Ejecución del diseño de la topología de LAN**

### 🧠 ¿Qué significa “ejecutar” el diseño?

Ya tienes el diseño de tu red (el plano), ahora toca **hacerlo realidad**:

- Comprar los equipos correctos
- Conectar los dispositivos físicamente
- Configurar direcciones IP
- Verificar que todo funcione

Piensa en esto como cuando **haces un plano para tu casa (diseño)** y luego **construyes las paredes, conectas la electricidad y luces (ejecución)**.

---

### ✅ Etapas para ejecutar la topología de LAN

---

#### 🔍 1. Revisión del diseño lógico

Antes de comenzar a armar la red físicamente, asegúrate de tener claro:

- Qué tipo de topología usarás (estrella, bus, malla, etc.)
- Qué dispositivos participarán (PCs, switches, routers, impresoras, etc.)
- Cuántos puertos de red necesitas
- Qué direcciones IP se asignarán
- Si usarás direcciones IP estáticas o DHCP

---

#### 🧰 2. Reúne los materiales

##### Por ejemplo:

- Switch de 8 puertos
- Cables de red (UTP Cat6, de al menos 1 metro por equipo)
- Computadoras o laptops
- Router (si habrá conexión a Internet)
- Herramientas: pelacables, probador de red (opcional)

---

#### 🔌 3. Cableado físico

Conecta todo en base a tu topología. La más común: **estrella**

```plaintext
PC1   PC2   PC3   PC4
 |     |     |     |
 +-----+-----+-----+
        SWITCH
           |
        (opcional)
         ROUTER
```

Pasos:

1. Conecta cada PC al **switch** usando cables UTP.
2. Si usarás Internet, conecta el switch al router/modem.
3. Organiza y etiqueta los cables (buena práctica).

---

#### 🖥️ 4. Configuración de red

##### Opción A: IP estática (manual)

En cada PC:

- Ir a:
  `Configuración > Red e Internet > Cambiar opciones del adaptador > Propiedades del protocolo IPv4`

- Asigna:

| PC  | IP          | Máscara       | Puerta de enlace |
| --- | ----------- | ------------- | ---------------- |
| 1   | 192.168.1.2 | 255.255.255.0 | 192.168.1.1      |
| 2   | 192.168.1.3 | 255.255.255.0 | 192.168.1.1      |
| 3   | 192.168.1.4 | 255.255.255.0 | 192.168.1.1      |
| 4   | 192.168.1.5 | 255.255.255.0 | 192.168.1.1      |

##### Opción B: DHCP (automático)

- Conecta el switch al router
- Configura el **router** para que asigne direcciones IP automáticamente (DHCP activado)

---

#### 🧪 5. Verificación de conectividad

Desde una PC, abre la terminal (o CMD en Windows) y ejecuta:

```bash
ping 192.168.1.3
```

Si responde, significa que la red funciona correctamente.

---

### 🧰 Herramientas para simular antes de instalar (opcional)

Puedes usar software como **Cisco Packet Tracer** para simular todo antes de hacerlo físico.

---

### 🧪 Ejemplo completo: Red LAN de una pequeña oficina

#### 🎯 Requisitos

- 1 router
- 1 switch
- 4 PCs
- 1 impresora compartida
- Acceso a Internet

#### 💡 Topología: Estrella

```
            INTERNET
                |
             [ROUTER]
                |
             [SWITCH]
     +----+----+----+----+
     |    |    |    |    |
   PC1  PC2  PC3  PC4  IMPRESORA
```

---

#### 📦 Equipos:

- Router TP-Link
- Switch de 8 puertos
- Cables UTP Cat6
- 4 PCs
- Impresora con red Ethernet

---

#### ⚙️ Configuración:

1. Conecta todos los cables: PCs, impresora y router al switch.
2. Activa DHCP en el router para que asigne IPs automáticamente.
3. Verifica con `ping` desde cualquier PC a otra o a la impresora.
4. En una PC, comparte archivos o configura la impresora de red.

---

#### ✅ Prueba:

En PC1:

```bash
ping 192.168.1.4   # (IP de la impresora)
```

Si responde, ¡todo está funcionando!

---

### 🧠 Resumen final

| Paso | Descripción                                                    |
| ---- | -------------------------------------------------------------- |
| 🧠 1 | Revisa el diseño lógico (tipo de topología, dispositivos, IPs) |
| 🧰 2 | Reúne el hardware (switch, cables, PCs, router)                |
| 🔌 3 | Realiza el cableado físico                                     |
| ⚙️ 4 | Configura las direcciones IP                                   |
| 🧪 5 | Verifica la conectividad                                       |

---

[🔼](#índice)

---

## **701. Redes inalámbricas, los usuarios se mueven por todos lados**

### 🧠 ¿Qué es una red inalámbrica?

Una **red inalámbrica (wireless network)** es una red de computadoras donde **no se utilizan cables** para conectar los dispositivos. En lugar de eso, se usa el **aire** como medio de transmisión a través de señales de radio, infrarrojas o microondas.

Los dispositivos pueden moverse libremente dentro del área de cobertura sin perder conexión.

---

### 🔑 Características principales

| Característica     | Descripción breve                                       |
| ------------------ | ------------------------------------------------------- |
| 🚫 Sin cables      | Usa señales de radio, no necesita cables UTP            |
| 📱 Movilidad       | Puedes moverte con laptops, tablets, celulares          |
| 📡 Acceso flexible | Permite conexión desde cualquier punto dentro del rango |
| 🔒 Seguridad       | Usa cifrados como WPA2 o WPA3 para proteger los datos   |

---

### 📶 Ejemplos fáciles

#### 🏠 En casa:

Tienes un **router Wi-Fi** en la sala. Conectas tu laptop desde tu habitación sin necesidad de cables.

#### 🏢 En una empresa:

Los empleados se conectan con sus laptops o smartphones mientras se mueven entre oficinas y salas de reuniones, sin perder conexión a la red corporativa.

---

### 🧩 Tipos de redes inalámbricas

| Tipo | Significado                    | Ejemplo fácil                       |
| ---- | ------------------------------ | ----------------------------------- |
| WLAN | Wireless Local Area Network    | Red Wi-Fi en una casa u oficina     |
| WPAN | Wireless Personal Area Network | Bluetooth entre celular y audífonos |
| WMAN | Wireless Metropolitan Area     | WiMAX para grandes ciudades         |
| WWAN | Wireless Wide Area Network     | Redes móviles 4G/5G                 |

---

### ⚙️ ¿Cómo se instala una red inalámbrica?

#### 🧰 Requisitos básicos

- Un **router inalámbrico (Wi-Fi)**
- Conexión a Internet (opcional si solo es red local)
- Dispositivos que tengan Wi-Fi (laptops, celulares, tablets)
- Acceso al **panel de configuración del router**

---

#### 🪛 Pasos para instalar una red inalámbrica

##### 🧱 1. Conectar el router

- Conecta el **cable de red del proveedor de Internet (ISP)** al **puerto WAN** del router.
- Conecta el router a la corriente eléctrica y enciéndelo.

##### 🖥️ 2. Configurar el router

1. Abre un navegador web en tu PC/laptop conectada al router (por cable o Wi-Fi).
2. Entra a la dirección: `192.168.1.1` o `192.168.0.1` (depende del modelo).
3. Inicia sesión (usuario/contraseña suele ser `admin`/`admin` o viene en una etiqueta).
4. Cambia el **nombre de la red (SSID)**, por ejemplo: `Red-Gustavo`.
5. Establece una contraseña fuerte con **cifrado WPA2 o WPA3**.

##### 📡 3. Conectar tus dispositivos

- Desde tu celular o laptop, abre la lista de redes Wi-Fi disponibles.
- Elige tu red (`Red-Gustavo`) y escribe la contraseña.
- ¡Listo! Ya estás conectado.

---

### 🧪 Verificación

Desde tu dispositivo conectado:

```bash
ping google.com
```

Si recibes respuestas, estás conectado a Internet.

---

### 📘 Ejemplo completo

#### 🎯 Objetivo:

Instalar una red Wi-Fi en una pequeña oficina para 6 empleados que usan laptops y celulares.

---

#### 🧰 Equipos necesarios:

- 1 router Wi-Fi (ej. TP-Link Archer)
- 1 módem de Internet (del proveedor)
- 6 laptops
- 6 celulares

---

#### 🪛 Instalación paso a paso:

1. Conectar el router al módem (puerto WAN).
2. Encender el router y conectar una laptop por cable.
3. Acceder al panel en `192.168.1.1`
4. Cambiar:

   - Nombre de red: `OficinaGusNet`
   - Contraseña Wi-Fi: `Trabajo2025`
   - Seguridad: WPA2

5. Guardar y reiniciar.
6. Conectar todos los dispositivos a la red `OficinaGusNet`.

---

#### 🧪 Prueba final:

En cada laptop:

```bash
ping 192.168.1.1
```

Para comprobar que están conectadas al router.

---

### 📚 Resumen

| Paso                     | Acción                                            |
| ------------------------ | ------------------------------------------------- |
| 🔌 Conectar el router    | Al módem de Internet y a la corriente eléctrica   |
| ⚙️ Configurar el router  | Cambiar nombre de red, contraseña y seguridad     |
| 📱 Conectar dispositivos | A través del Wi-Fi, con la contraseña establecida |
| 🧪 Verificar conexión    | Haciendo ping o probando acceso a Internet        |

---

[🔼](#índice)

---

## **702. Diseño de redes inalámbricas**

### 🧠 ¿Qué es el diseño de una red inalámbrica?

Diseñar una red inalámbrica es **planificar cómo se conectarán los dispositivos sin usar cables**, asegurando que:

- Todos tengan buena señal
- La red sea **segura**
- La red soporte el **tráfico de datos** esperado
- Se usen los **equipos adecuados**

---

### 🏗️ ¿Dónde se necesita diseñar una red inalámbrica?

| Lugar                  | Necesidades comunes                                 |
| ---------------------- | --------------------------------------------------- |
| 🏠 Casa                | Wi-Fi para familia, TV, celulares y laptops         |
| 🏢 Oficina pequeña     | 5 a 10 empleados, correo, videollamadas             |
| 🏫 Escuela/Universidad | Cobertura total, múltiples dispositivos simultáneos |
| 🏨 Hotel o café        | Acceso público, seguridad separada del personal     |
| 🏟️ Grandes eventos     | Redes temporales, gran cantidad de conexiones       |

---

### ✅ Objetivos del diseño de red Wi-Fi

1. 📶 **Buena cobertura**: señal fuerte en todas las áreas.
2. 🚀 **Velocidad adecuada**: navegación y descargas rápidas.
3. 🔒 **Seguridad**: proteger el acceso a la red.
4. 👥 **Capacidad de usuarios**: soportar muchos dispositivos.
5. ⚡ **Redundancia**: evitar cortes si falla un equipo.

---

### 🧰 Equipos necesarios para una red inalámbrica

| Dispositivo             | Función                                                       |
| ----------------------- | ------------------------------------------------------------- |
| 📡 Router inalámbrico   | Centraliza la conexión a Internet y genera señal Wi-Fi        |
| 📶 Punto de acceso (AP) | Amplía la señal en zonas grandes (salones, almacenes, patios) |
| 🔁 Switch (opcional)    | Conecta múltiples dispositivos por cable si es necesario      |
| 🔌 Módem del proveedor  | Brinda acceso a Internet                                      |

---

### 📐 Pasos del diseño de red inalámbrica

#### 1. 📋 Levantamiento de información

- ¿Cuántos dispositivos se conectarán?
- ¿Qué tipo de aplicaciones usarán? (navegación, video, juegos, etc.)
- ¿Qué área debe tener cobertura? (metros cuadrados, pisos, etc.)
- ¿Cuáles son los posibles obstáculos? (muros, puertas, muebles)

#### 2. 📍 Mapa del lugar

- Usa un plano del lugar (puede ser dibujado)
- Marca zonas clave donde se necesita señal
- Identifica zonas difíciles (paredes gruesas, sótanos)

#### 3. 📡 Ubicación de equipos

- Coloca el router o puntos de acceso en lugares **centrales y elevados**
- Evita esquinas, objetos metálicos o cerca de microondas
- Usa varios AP si el lugar es grande

#### 4. ⚙️ Elección del canal y frecuencia

- Usa **2.4 GHz** para mayor alcance
- Usa **5 GHz** para mayor velocidad y menos interferencia
- Configura canales diferentes si hay varios AP (para evitar choques)

#### 5. 🔒 Seguridad

- Nombre de red (SSID) claro pero sin información sensible
- Contraseña WPA2 o WPA3
- Si es red pública, separa red de invitados (con VLAN o routers separados)

---

### 🧱 ¿Cómo se instala físicamente?

#### 🛠️ Instalación básica:

1. Conectar el **módem del proveedor** al **router inalámbrico**
2. Configurar el router (SSID, clave, canal, cifrado)
3. Instalar **puntos de acceso adicionales**, si es necesario
4. Conectar dispositivos y hacer pruebas

---

### 📘 Ejemplo completo: diseño de red inalámbrica para una oficina de 2 pisos

#### 🎯 Objetivo

Crear una red Wi-Fi para una oficina con:

- 2 pisos
- 15 empleados
- Videollamadas frecuentes
- Impresoras Wi-Fi
- Visitas ocasionales de clientes

---

#### 📐 Plano simplificado

- Piso 1: recepción, sala de reuniones, área de impresión
- Piso 2: estaciones de trabajo, oficina de gerencia

---

#### 🧰 Equipamiento seleccionado

- 1 Router Wi-Fi principal en piso 1
- 2 Puntos de acceso adicionales (uno por piso)
- Switch para conectar PCs fijas en piso 2
- SSID: `Oficina-Gustavo`
- Contraseña: `RedEmpresarial2025`
- Seguridad: WPA2-PSK
- Rango IP: 192.168.10.0/24

---

#### ⚙️ Instalación

1. Conectar módem al router (en Piso 1)
2. Configurar el router desde una laptop:

   - IP del router: `192.168.10.1`
   - SSID: `Oficina-Gustavo`
   - WPA2 + contraseña

3. Conectar puntos de acceso por cable al router/switch
4. Verificar la señal con la app **WiFi Analyzer**
5. Hacer pruebas de conexión, velocidad y ping

---

### 🧪 Verificación

Desde una laptop en Piso 2, conectada por Wi-Fi:

```bash
ping 192.168.10.1
```

Desde un celular:

- Conectarse a `Oficina-Gustavo`
- Probar navegar, hacer videollamada y usar impresora

---

### 🎓 Conclusión

Diseñar redes inalámbricas es **más que solo poner un router**. Es planear para que todos los dispositivos tengan:

✅ Buena señal

✅ Seguridad

✅ Velocidad

✅ Estabilidad

Con las herramientas adecuadas y una buena planificación, puedes cubrir casas, oficinas, cafés, escuelas o hasta almacenes grandes.

---

[🔼](#índice)

---

## **703. Configuración de redes inalámbricas**

### 🧠 ¿Qué es configurar una red inalámbrica?

Es el proceso de **ajustar todos los parámetros de una red Wi-Fi** para que los dispositivos puedan conectarse de forma **segura, rápida y estable**.

Esto incluye:

- Definir el **nombre de la red (SSID)**
- Asignar una **contraseña segura**
- Configurar el **canal, frecuencia y cifrado**
- Establecer si la IP será **estática o automática (DHCP)**
- (Opcional) Dividir la red en **principal e invitados**

---

### 🛠️ ¿Qué necesitas?

| Recurso                            | Descripción                                   |
| ---------------------------------- | --------------------------------------------- |
| 📶 Router Wi-Fi                    | Dispositivo que genera la señal inalámbrica   |
| 🌐 Acceso a Internet               | Desde el proveedor (opcional si es red local) |
| 💻 Laptop/PC o celular             | Para ingresar al panel de configuración       |
| 🧠 Usuario y contraseña del router | Están debajo del equipo o en el manual        |

---

### ⚙️ PASOS PARA CONFIGURAR UNA RED INALÁMBRICA

---

#### 🔌 1. Conecta el router Wi-Fi

- **Puerto WAN** del router → al **módem del proveedor**
- Enchufa el router a la corriente
- Espera a que los LEDs de encendido y Wi-Fi se estabilicen

---

#### 🌐 2. Accede al panel de configuración

##### Opción 1: Conecta una PC por cable (recomendado)

##### Opción 2: Conecta por la red Wi-Fi predeterminada (nombre y clave están debajo del router)

- Abre un navegador y escribe la IP del router (ejemplo):

  ```
  http://192.168.0.1
  http://192.168.1.1
  ```

- Inicia sesión:

  - Usuario: `admin`
  - Contraseña: `admin` o la que indique el fabricante

---

#### 🖥️ 3. Cambia la configuración básica

##### 🔤 Nombre de la red (SSID)

- Cambia el nombre por uno personalizado, por ejemplo:
  `Casa-Gustavo`, `OficinaGusNet`, `Red-Inalambrica-2025`

##### 🔒 Contraseña y cifrado

- Tipo de seguridad: **WPA2-PSK** o **WPA3** (si está disponible)
- Contraseña: usa una combinación de letras, números y símbolos.
  Ejemplo: `MiWifiSegura2025!`

---

#### 📶 4. Configura el canal y frecuencia (opcional pero recomendado)

- Banda: elige entre:

  - **2.4 GHz** → mayor alcance, más interferencia
  - **5 GHz** → más velocidad, menos alcance

- Canal: elige un canal libre (puedes usar apps como _WiFi Analyzer_ para saber cuál)

---

#### 📬 5. Configura el servidor DHCP (opcional)

> DHCP asigna IPs automáticas a los dispositivos conectados.

- Actívalo (la mayoría de routers ya lo traen por defecto)
- Rango sugerido: `192.168.1.100` a `192.168.1.200`

---

#### 👥 6. (Opcional) Habilita la red para invitados

- Crea una red Wi-Fi separada sin acceso a tus archivos
- Ejemplo:

  - SSID: `Invitados-Gus`
  - Contraseña: `SoloInternet2025`

---

#### 💾 7. Guarda los cambios y reinicia

- Presiona "Guardar" o "Apply"
- El router se reiniciará y aplicará la nueva configuración

---

### ✅ EJEMPLO COMPLETO: Configuración de una red inalámbrica en casa

---

#### Escenario:

Tienes un router Wi-Fi TP-Link y quieres configurarlo para conectar:

- 3 laptops
- 2 celulares
- 1 Smart TV

---

#### Paso a paso:

1. Conecta el router al módem del proveedor
2. Enciende el router
3. Conecta una laptop al router por cable
4. Abre el navegador y entra a `http://192.168.0.1`
5. Inicia sesión con `admin/admin`
6. Cambia:

   - SSID: `Casa-Gustavo`
   - Contraseña: `RedCasa2025!`
   - Seguridad: WPA2-PSK

7. Activa DHCP con rango de IPs: `192.168.0.100` – `192.168.0.200`
8. Guarda y reinicia el router

---

#### Pruebas de funcionamiento:

- Desde tu celular, conéctate a la red `Casa-Gustavo`
- Ingresa la contraseña
- Abre un navegador y visita `www.google.com`
- En tu laptop, abre CMD y haz ping:

```bash
ping 8.8.8.8
```

✅ Si hay respuesta, ¡todo está funcionando correctamente!

---

### 🛡️ Consejos de seguridad adicionales

- Cambia la contraseña de acceso al panel del router (no uses `admin`)
- Desactiva WPS (puede ser una brecha de seguridad)
- Actualiza el firmware del router desde el mismo panel

---

### 📚 Resumen general

| Elemento             | Configuración recomendada                       |
| -------------------- | ----------------------------------------------- |
| Nombre de red (SSID) | Personalizado, sin información personal         |
| Contraseña Wi-Fi     | Fuerte, con letras, números y símbolos          |
| Seguridad            | WPA2-PSK o WPA3                                 |
| DHCP                 | Activado, rango claro                           |
| Banda                | 2.4 GHz o 5 GHz según tus necesidades           |
| Canal                | Automático o manual según interferencias        |
| Red de invitados     | Separada, sin acceso a dispositivos principales |

---

[🔼](#índice)

---

## **704. Equipos activos de LAN: el cableado sigue siendo importante**

### 📌 ¿Qué es una red LAN?

**LAN (Local Area Network)** es una red local que conecta computadoras, impresoras, servidores y otros dispositivos dentro de un área limitada como:

- Una casa
- Una oficina
- Un edificio

---

### 📟 ¿Qué son los Equipos Activos?

Son los **dispositivos electrónicos que gestionan, amplifican, y encaminan los datos en una red**. Se llaman "activos" porque **requieren energía eléctrica** para funcionar y **procesan activamente la información**.

---

### 🔌 ¿Y los equipos pasivos?

- No necesitan energía
- Solo transportan la señal (ej: **cables, conectores, canaletas**)
- No procesan ni interpretan datos

---

### 📋 Lista de Equipos Activos en una LAN

| Equipo activo     | Función principal                                          |
| ----------------- | ---------------------------------------------------------- |
| 🔄 Switch         | Conecta múltiples dispositivos y los comunica internamente |
| 📶 Router         | Conecta redes distintas, como la LAN con Internet          |
| 🌐 Access Point   | Crea una red inalámbrica (Wi-Fi)                           |
| 💻 Tarjeta de red | Permite que una computadora se conecte a la red            |
| 🖥️ Servidor       | Provee servicios (archivos, correo, impresión, etc.)       |
| 🔐 Firewall       | Controla qué entra y sale de la red (seguridad)            |

---

### 🧰 ¿Cómo se instalan los equipos activos?

---

#### 1. **Planificación y topología**

Define cuántos dispositivos vas a conectar y dónde están ubicados. Decide si usarás:

- 🕸️ **Topología estrella** (la más común): todo se conecta a un switch
- 🔁 **Topología en bus o híbrida** (en redes pequeñas o mixtas)

---

#### 2. **Cableado estructurado**

- Usa **cables de red (UTP categoría 5e o 6)** para conectar los equipos
- Cada dispositivo tiene un **puerto RJ45**
- Cablea desde cada dispositivo al **switch o router**
- Si hay muchos pisos, considera un **rack con switches por piso**

---

#### 3. **Conectar el switch**

- Conecta el **switch a la corriente**
- Une cada dispositivo al switch con cables Ethernet
- Conecta el switch al router (si necesitas acceso a Internet)

---

#### 4. **Instalar el router (si hay Internet)**

- El **router** se conecta al módem (de la empresa de Internet)
- Luego del router, conecta al switch (o directamente a algunos dispositivos si tiene más puertos)

---

#### 5. **Agregar un punto de acceso inalámbrico (si deseas Wi-Fi)**

- El **Access Point (AP)** se conecta al switch o router
- Se configura el SSID (nombre de red), contraseña y tipo de seguridad (WPA2/WPA3)

---

#### 6. **Encender todo y probar**

- Enciende el router, luego el switch, luego los dispositivos
- Verifica que todos tengan conexión (IP válida, acceso entre ellos o a Internet)
- Prueba haciendo ping, abriendo carpetas compartidas o accediendo al servidor

---

### 📦 Ejemplo completo: Instalación de una LAN con equipos activos

---

#### 🎯 Objetivo

Conectar 4 computadoras y 2 laptops en una oficina pequeña para compartir archivos e impresora y tener acceso a Internet.

---

#### 🛠️ Equipos

- 1 Router Wi-Fi (con 4 puertos LAN)
- 1 Switch de 8 puertos
- 1 Access Point (para las laptops)
- 6 cables Ethernet UTP Cat6
- 4 PCs de escritorio
- 2 laptops con Wi-Fi
- 1 impresora en red

---

#### 🧱 Instalación

1. **Conecta el módem al router** (puerto WAN)
2. **Conecta el router al switch** (puerto LAN del router a un puerto del switch)
3. **Conecta las 4 PCs al switch** con cables UTP
4. **Conecta la impresora al switch** también
5. **Conecta el Access Point al switch**
6. **Configura el AP** con SSID "OficinaGus", clave segura WPA2
7. **Conecta las 2 laptops vía Wi-Fi** al AP
8. **Verifica** que todas las máquinas tienen IP, pueden hacer ping entre sí y acceder a la impresora

---

#### 🔄 Resultado

- Todas las PCs tienen acceso a la red e Internet
- Laptops se conectan por Wi-Fi
- Impresora es compartida en red
- El switch permite ampliar si se necesita agregar más PCs

---

### ✅ Conclusiones clave

- **Los equipos activos son el corazón de la red**: sin ellos, no hay comunicación ni procesamiento.
- **El cableado sigue siendo esencial**, especialmente para estabilidad y velocidad.
- Un buen diseño de red LAN incluye **planificación de puertos, cableado limpio y configuración segura**.

---

[🔼](#índice)

---

## **705. Separación de grupos, el uso de las VLAN**

### ✅ ¿Qué es una VLAN?

**VLAN** significa **Red de Área Local Virtual** (del inglés _Virtual Local Area Network_).

> Es una técnica para **dividir lógicamente** una red física en **varios grupos independientes**, aunque todos estén conectados al mismo switch físico.

---

#### 🎯 ¿Por qué usar VLANs?

Imagina una empresa con varias áreas:

- 🧑‍💼 Recursos Humanos
- 💻 Área de Tecnología
- 📊 Contabilidad

Aunque todos los equipos están conectados al **mismo switch**, no queremos que **todos puedan comunicarse libremente** por motivos de **seguridad, organización y rendimiento**. Ahí es donde **las VLANs ayudan**.

---

### 📦 ¿Qué hacen las VLANs?

- Agrupan equipos **por función**, **no por ubicación física**
- Aumentan la **seguridad**
- Disminuyen el **tráfico innecesario**
- Permiten tener **varias redes en un mismo switch**

---

### 💡 Ejemplo básico:

En un **switch físico**, puedes tener:

| Puerto | Dispositivo            | VLAN asignada |
| ------ | ---------------------- | ------------- |
| 1      | PC de Recursos Humanos | VLAN 10       |
| 2      | PC de Recursos Humanos | VLAN 10       |
| 3      | PC de Contabilidad     | VLAN 20       |
| 4      | PC de Tecnología       | VLAN 30       |

Aunque todos están conectados al **mismo switch**, los que están en VLAN 10 **no pueden comunicarse** con los de VLAN 20 o 30, a menos que haya un **router o switch capa 3 que lo permita**.

---

### 🧰 ¿Qué se necesita para usar VLANs?

- Un **switch administrable** (gestionable)
- Conectarte al switch vía consola, Telnet o navegador
- Asignar **VLANs a cada puerto**
- (Opcional) Un **router o switch de capa 3** para que las VLANs se comuniquen entre sí

---

### ⚙️ ¿Cómo se instala y configura una VLAN?

#### 📍 En Packet Tracer o en un switch real (Cisco)

---

#### 🛠️ PASO A PASO

##### 1. **Accede al switch**

Puedes entrar por consola en Packet Tracer o vía CLI:

```plaintext
Switch> enable
Switch# configure terminal
```

---

##### 2. **Crear las VLANs**

```bash
Switch(config)# vlan 10
Switch(config-vlan)# name RecursosHumanos
Switch(config-vlan)# exit

Switch(config)# vlan 20
Switch(config-vlan)# name Contabilidad
Switch(config-vlan)# exit
```

---

##### 3. **Asignar puertos a las VLANs**

```bash
Switch(config)# interface fastEthernet 0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10
Switch(config-if)# exit

Switch(config)# interface fastEthernet 0/2
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10
Switch(config-if)# exit

Switch(config)# interface fastEthernet 0/3
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 20
Switch(config-if)# exit
```

---

##### 4. **Guardar la configuración**

```bash
Switch(config)# exit
Switch# write memory
```

---

### 🧪 ¿Cómo lo pruebas?

- Conecta PCs a los puertos configurados

- Asigna IPs como:

  - VLAN 10: 192.168.10.x
  - VLAN 20: 192.168.20.x

- Haz ping entre PCs:

  - Los de la **misma VLAN se comunican**
  - Los de **diferentes VLANs no**

---

### 🧾 Ejemplo completo: Empresa con 3 departamentos

#### 🏢 Escenario

Una empresa tiene:

- 2 PCs en **Recursos Humanos** (VLAN 10)
- 2 PCs en **Contabilidad** (VLAN 20)
- 1 servidor en **VLAN 99 (Servidor común)**

---

#### 💻 Direcciones IP

| Dispositivo        | VLAN | IP           | Puerto |
| ------------------ | ---- | ------------ | ------ |
| PC1 (RRHH)         | 10   | 192.168.10.2 | Fa0/1  |
| PC2 (RRHH)         | 10   | 192.168.10.3 | Fa0/2  |
| PC3 (Contabilidad) | 20   | 192.168.20.2 | Fa0/3  |
| PC4 (Contabilidad) | 20   | 192.168.20.3 | Fa0/4  |
| Servidor           | 99   | 192.168.99.2 | Fa0/5  |

---

#### 🧠 Resultado esperado

- PC1 puede hacer ping a PC2 ✅
- PC1 NO puede hacer ping a PC3 ❌
- Ningún PC puede hacer ping al servidor si no hay un router (❌)
- Si añades un router o switch capa 3, puedes permitir comunicación entre VLANs (✅)

---

### 🎯 Ventajas clave de usar VLAN

- Separación lógica de grupos de trabajo
- Mejor control de tráfico
- Seguridad entre departamentos
- Escalabilidad y administración más simple

---

[🔼](#índice)

---

## **706. Enlaces troncales, cuando las conexiones se unen**

### ✅ ¿Qué es un enlace troncal?

Un **enlace troncal** (o _trunk link_) es un **tipo especial de conexión entre switches (o entre switch y router)** que permite el **tráfico de múltiples VLANs al mismo tiempo** sobre un solo cable.

> 🌐 Imagina una autopista que transporta carros de diferentes colores (VLANs) entre ciudades (switches). Esa autopista es el **enlace troncal**.

---

### 🎯 ¿Para qué sirve un enlace troncal?

Sin trunks, tendrías que usar **un cable por cada VLAN** entre switches. Con un trunk, puedes:

- Transportar **múltiples VLANs en una sola interfaz física**
- **Conectar switches y mantener separadas las VLANs**
- Permitir que las VLANs funcionen entre **varios switches o entre switch y router**

---

### 🧱 ¿Cómo se logra?

Los switches usan protocolos como:

- **IEEE 802.1Q** (más usado)
- ISL (antiguo, Cisco propietario)

Estos protocolos **etiquetan (tag)** cada trama con su número de VLAN para que el switch receptor sepa a qué VLAN pertenece.

---

### 🧠 Ejemplo visual simple:

Imagina dos switches conectados así:

```
[PC1 - VLAN 10]         [PC3 - VLAN 10]
      |                        |
   Switch A  <--trunk-->   Switch B
      |                        |
[PC2 - VLAN 20]         [PC4 - VLAN 20]
```

🔹 Switch A y Switch B están unidos por **un cable configurado como trunk**

🔹 Permite que PC1 y PC3 (misma VLAN) se comuniquen, y PC2 con PC4 también.

---

### ⚙️ ¿Cómo se configura un enlace troncal?

Usaremos **Cisco CLI** en Packet Tracer o un switch real.

---

#### 🛠️ PASO A PASO – Enlace Trunk entre dos switches

##### 🔌 Paso 1: Conecta los switches

Conecta el **puerto Fa0/24 de Switch A** al **puerto Fa0/24 de Switch B** con un cable cruzado (en Packet Tracer, usa el cable automático).

---

##### 🖥️ Paso 2: Entra al modo configuración en ambos switches

```bash
Switch> enable
Switch# configure terminal
```

---

##### 🧩 Paso 3: Configura la interfaz como trunk

Haz esto en **ambos switches**:

```bash
Switch(config)# interface fastEthernet 0/24
Switch(config-if)# switchport mode trunk
Switch(config-if)# exit
```

---

##### 🛡️ Paso 4: (Opcional pero recomendado) Permitir solo las VLANs necesarias

Ejemplo, permitir solo VLAN 10 y 20:

```bash
Switch(config)# interface fastEthernet 0/24
Switch(config-if)# switchport trunk allowed vlan 10,20
Switch(config-if)# exit
```

---

##### 💾 Paso 5: Guarda cambios

```bash
Switch# write memory
```

---

### ✅ Verificación

Usa este comando para verificar el modo de trunk en el switch:

```bash
Switch# show interfaces trunk
```

---

### 🧾 Ejemplo completo – Tráfico VLAN entre dos switches usando trunk

#### 📦 Escenario

- **Switch A** tiene PC1 (VLAN 10) y PC2 (VLAN 20)
- **Switch B** tiene PC3 (VLAN 10) y PC4 (VLAN 20)
- Ambos switches están conectados por **un cable troncal en Fa0/24**

---

#### 🧑‍💻 Configuración de PCs

| Dispositivo | VLAN | IP           | Conectado a    |
| ----------- | ---- | ------------ | -------------- |
| PC1         | 10   | 192.168.10.2 | Switch A Fa0/1 |
| PC2         | 20   | 192.168.20.2 | Switch A Fa0/2 |
| PC3         | 10   | 192.168.10.3 | Switch B Fa0/1 |
| PC4         | 20   | 192.168.20.3 | Switch B Fa0/2 |

---

#### 🛠️ Configura VLANs y puertos de acceso

**En ambos switches:**

```bash
vlan 10
 name Red_RRHH
vlan 20
 name Red_TECNO

interface fastEthernet 0/1
 switchport mode access
 switchport access vlan 10

interface fastEthernet 0/2
 switchport mode access
 switchport access vlan 20
```

---

#### 🔗 Configura el trunk entre switches

```bash
interface fastEthernet 0/24
 switchport mode trunk
 switchport trunk allowed vlan 10,20
```

---

#### ✅ Resultado esperado

- PC1 puede hacer ping a PC3 (ambos en VLAN 10)
- PC2 puede hacer ping a PC4 (ambos en VLAN 20)
- No hay comunicación entre VLANs (sin router de inter-VLAN)

---

### 📌 Beneficios clave de usar enlaces troncales

| Ventaja           | Explicación                                           |
| ----------------- | ----------------------------------------------------- |
| Ahorro de puertos | No necesitas un cable por cada VLAN                   |
| Escalabilidad     | Facilita agregar más switches sin complicar el diseño |
| Separación lógica | Mantiene la seguridad entre departamentos             |
| Menor costo       | Menos cables y equipos necesarios                     |

---

[🔼](#índice)

---

## **707. Lista de control de acceso: elementos**

### 🛡️ ¿Qué es una Lista de Control de Acceso (ACL)?

Una **ACL (Access Control List)** es una **regla o conjunto de reglas** que se aplica en un router o firewall para **permitir o denegar** el tráfico de red basado en **criterios como dirección IP, protocolo, puerto, etc.**

> 🧠 Es como un **portero de discoteca** que revisa una lista: si estás en la lista, puedes entrar; si no, te quedas fuera.

---

### 🎯 ¿Para qué sirve una ACL?

- Restringir acceso a partes de la red (por ejemplo: bloquear redes invitadas a servidores)
- Controlar tráfico hacia/desde Internet
- Mejorar la seguridad
- Filtrar paquetes de datos según origen, destino, protocolo, etc.

---

### 🧩 Elementos principales de una ACL

Aquí están los **componentes clave** que forman una ACL:

| Elemento                 | Explicación                                                                  |
| ------------------------ | ---------------------------------------------------------------------------- |
| **Número o nombre**      | Identificador de la ACL (ej. 1 para ACL estándar, 100 para extendida)        |
| **Permitir / Denegar**   | Acción: `permit` o `deny`                                                    |
| **Dirección IP origen**  | Desde qué IP se origina el paquete                                           |
| **Wildcard mask**        | Máscara que indica qué bits comparar (similar a máscara de subred invertida) |
| **Dirección IP destino** | Hacia qué IP va el paquete (solo en ACL extendidas)                          |
| **Protocolo**            | TCP, UDP, ICMP, IP (solo en ACL extendidas)                                  |
| **Puerto**               | Opcional, para filtrar por número de puerto (ej. puerto 80 para HTTP)        |

---

### 🔍 Tipos de ACL

| Tipo          | Características principales                                    |
| ------------- | -------------------------------------------------------------- |
| ACL estándar  | Filtra **solo por IP de origen**                               |
| ACL extendida | Filtra por IP origen, destino, protocolo, puerto, etc.         |
| ACL nombradas | Usan nombres en vez de números; permiten editar más fácilmente |

---

### 🧰 ¿Cómo se instala o configura una ACL?

Generalmente en un **router**, pero también en switches multicapa.

---

#### 🔧 Comandos básicos (ACL estándar)

```bash
Router(config)# access-list 1 permit 192.168.1.0 0.0.0.255
Router(config)# interface fastEthernet 0/0
Router(config-if)# ip access-group 1 in
```

---

#### 🔧 Comandos básicos (ACL extendida)

```bash
Router(config)# access-list 100 deny tcp 192.168.1.0 0.0.0.255 any eq 80
Router(config)# access-list 100 permit ip any any
Router(config)# interface fastEthernet 0/0
Router(config-if)# ip access-group 100 in
```

---

### 🧪 Ejemplo completo paso a paso – ACL extendida para bloquear navegación web

#### 🎯 Objetivo

Bloquear que los usuarios de la red 192.168.1.0/24 accedan a **sitios web (puerto 80)**, pero permitir todo lo demás.

---

#### 🔌 Topología

- PC1 (192.168.1.10) conectado al Router en `Fa0/0`
- El Router conectado a Internet (puede ser un switch simulando el exterior)

---

#### 🧱 Paso 1: Acceso al router

```bash
Router> enable
Router# configure terminal
```

---

#### 🧾 Paso 2: Crear la ACL

```bash
Router(config)# access-list 100 deny tcp 192.168.1.0 0.0.0.255 any eq 80
Router(config)# access-list 100 permit ip any any
```

📌 La primera línea bloquea HTTP desde la red 192.168.1.0
📌 La segunda línea permite todo lo demás

---

#### 🔗 Paso 3: Aplicar la ACL en la interfaz de entrada

```bash
Router(config)# interface fastEthernet 0/0
Router(config-if)# ip access-group 100 in
```

---

#### 💾 Paso 4: Guardar la configuración

```bash
Router# write memory
```

---

#### 🧪 Resultado esperado

- PC1 **no podrá acceder a páginas web (HTTP)** como [www.google.com](http://www.google.com)
- Pero sí podrá **hacer ping, usar FTP, SSH, etc.**

---

### 🧠 ¿Qué es una wildcard mask?

La **wildcard mask** es una máscara inversa que **indica qué bits se ignoran** al hacer la comparación. Por ejemplo:

- Subred: `192.168.1.0/24`
- Máscara normal: `255.255.255.0`
- Wildcard: `0.0.0.255`

👉 El `0` significa: "compara este octeto exactamente"

👉 El `255` significa: "ignora este octeto"

---

### 💡 Recomendaciones al usar ACLs

- Siempre termina con `permit ip any any` si no quieres que todo lo demás se bloquee.
- Aplica ACLs **lo más cerca posible del origen** (extendidas) o del destino (estándar).
- Verifica con `show access-lists` y `show ip interface`

---

### 🧾 Resumen visual

```
access-list 100 deny tcp 192.168.1.0 0.0.0.255 any eq 80
access-list 100 permit ip any any
interface FastEthernet 0/0
 ip access-group 100 in
```

---

[🔼](#índice)

---

## **708. Lista de control de acceso: filosofía**

### 🧠 ¿Qué es la “filosofía” de una Lista de Control de Acceso (ACL)?

Cuando hablamos de “**filosofía**” en el contexto de ACLs, nos referimos a **la forma de pensar y diseñar** las reglas de control de acceso en una red. Es la **estrategia mental** que se debe tener al crear reglas para **permitir o negar tráfico de red**.

Es como tener una **puerta con filtro**: no dejas pasar a cualquiera, y decides exactamente **quién entra, por dónde y con qué propósito**.

---

### 🎯 Filosofía básica de las ACLs

| Principio                      | Explicación                                                                               |
| ------------------------------ | ----------------------------------------------------------------------------------------- |
| **Negar por defecto**          | Todo está **denegado al final**, si no lo permites explícitamente, se bloquea.            |
| **Permitir lo necesario**      | Solo permites **el tráfico que sabes que necesitas** (por seguridad).                     |
| **Menos es más (restricción)** | Cuantas menos cosas permitas, **más segura es tu red**.                                   |
| **Orden importa**              | Las ACL se **evalúan de arriba hacia abajo**, **línea por línea**.                        |
| **Cerca del origen o destino** | ACL estándar: aplicar cerca del **destino**. ACL extendida: aplicar cerca del **origen**. |
| **Documentar y probar**        | Siempre documenta lo que haces y **prueba antes de aplicar en producción**.               |

---

### 👀 Analogía sencilla: club con lista de entrada

Imagina que eres el portero de un club:

- **ACL estándar**: solo te fijas en el nombre de la persona (IP origen).
- **ACL extendida**: ves el nombre, a dónde quiere ir, con quién, y a qué fiesta (IP destino, puerto, protocolo).

Si alguien **no está en la lista, no entra**. Si está, debe cumplir exactamente los requisitos. Si nadie dijo nada sobre él, tampoco entra (regla implícita de “deny all”).

---

### 🧱 Filosofía práctica: cómo pensar una ACL paso a paso

1. **¿Qué debo proteger?**

   Ejemplo: un servidor web interno.

2. **¿Quién debe acceder y cómo?**

   Solo usuarios de la red 192.168.10.0 usando HTTP (puerto 80).

3. **¿Qué debo bloquear?**

   El resto del tráfico, especialmente conexiones no autorizadas.

4. **¿Dónde aplicar la ACL?**

   En la **interfaz de entrada o salida** del router, según el tipo.

5. **¿Cuál es el orden correcto?**

   Primero se colocan las reglas más específicas, luego las más generales.

---

### 🔧 ¿Cómo se “instala” o configura una ACL?

La instalación de una ACL significa **escribir las reglas** y luego **aplicarlas a una interfaz de red** (como una puerta de entrada/salida).

---

#### 📍 Comandos base (Router Cisco)

```bash
Router(config)# access-list 101 permit tcp 192.168.10.0 0.0.0.255 any eq 80
Router(config)# access-list 101 deny ip any any
Router(config)# interface fa0/0
Router(config-if)# ip access-group 101 in
```

---

### 📦 Ejemplo completo – Filosofía aplicada a un caso real

#### 🎯 Objetivo

Permitir solo acceso web (HTTP) desde la red **192.168.10.0/24** al **servidor web** (IP 10.0.0.5). Bloquear todo lo demás.

---

#### 🖥️ Escenario

- PC: 192.168.10.10
- Router con dos interfaces:

  - Fa0/0: red LAN (192.168.10.1)
  - Fa0/1: red DMZ (10.0.0.1)

- Servidor web: 10.0.0.5

---

#### 🔧 Paso a paso

##### 1. Crear la ACL en el router

```bash
Router(config)# access-list 110 permit tcp 192.168.10.0 0.0.0.255 host 10.0.0.5 eq 80
Router(config)# access-list 110 deny ip any any
```

📌 Línea 1: permite tráfico HTTP solo al servidor

📌 Línea 2: bloquea todo lo que no está explícitamente permitido

---

##### 2. Aplicar la ACL en la interfaz de entrada (desde la LAN)

```bash
Router(config)# interface fa0/0
Router(config-if)# ip access-group 110 in
```

---

##### 3. Verificar con `show`

```bash
Router# show access-lists 110
```

---

### 🧪 Resultado

- PC puede entrar al servidor web (10.0.0.5:80)
- No puede hacer ping a otros equipos
- No puede usar FTP, SSH, ni navegar hacia otros sitios

---

### ✅ Recomendaciones al aplicar la filosofía de ACLs

1. **Haz un plan antes de escribir comandos.**
2. **Aplica reglas específicas primero.**
3. **Nunca olvides la regla final implícita de deny.**
4. **Prueba en entornos controlados antes de implementar en producción.**
5. **Documenta cada regla que escribes.**

---

### 🧾 Resumen de filosofía

- ACLs deben **pensarse como filtros inteligentes**, no como simples listas.
- La **seguridad es prioridad**: más vale bloquear de más que permitir de más.
- Su poder está en su **precisión y orden**.
- Evalúan **de arriba a abajo, línea por línea**, y **se detienen cuando encuentran una coincidencia**.

---

[🔼](#índice)

---

## **709. Listas de control de acceso, un firewall en reglas**

![firewall](../img/7_Ciberseguridad_Profesional/firewall.jpg "firewall")

### 🧠 ¿Qué es una Lista de Control de Acceso (ACL)?

Una **ACL (Access Control List)** es un conjunto de **reglas que controlan el tráfico de red**. Funcionan como un **firewall simple**, que dice **qué paquetes están permitidos** o **denegados** al entrar o salir de una red.

> ⚠️ Son una de las formas más básicas de implementar **seguridad en redes**.

---

### 🎯 ¿Para qué se usan?

- Controlar qué equipos pueden **acceder a otros**.
- Proteger servidores o segmentos de red.
- **Filtrar tráfico por IP, protocolo, puerto**, etc.
- Evitar accesos no deseados (como un firewall).
- Dividir redes por funciones o seguridad.

---

### 🏗️ Tipos de ACL

| Tipo          | ¿Qué filtra?                             | Ideal para:                          |
| ------------- | ---------------------------------------- | ------------------------------------ |
| **Estándar**  | Solo **IP de origen**                    | Permitir o negar acceso por IP       |
| **Extendida** | IP de origen, destino, protocolo, puerto | Control más preciso (web, SSH, etc.) |

---

### 🔒 ACL como un "Firewall de reglas"

Un firewall puede tener miles de reglas. Una ACL es **la base** de eso: **una lista ordenada de condiciones** que dice quién puede o no puede hacer algo.

📌 El tráfico entra a un router o switch y se **evalúa contra la lista**.

- Si **coincide con una regla**, se **permite o se niega**.
- Si **no hay coincidencia**, se aplica la regla final implícita:
  `deny all` (bloquea todo lo demás).

---

### 🧱 ¿Cómo funciona? – Analogía

Imagina una entrada a un edificio:

1. Hay una **lista** de personas autorizadas (IP origen, destino, protocolo, puerto).
2. El guardia ve la lista y dice:

   - "Tú sí puedes pasar."
   - "Tú no estás en la lista, lo siento."

3. Nadie entra sin estar en esa lista.

---

### 🔧 ¿Cómo se “instala” una ACL?

Se **crea** una lista de reglas y se **aplica a una interfaz** de un router o switch, en modo:

- **Entrada (inbound):** cuando el paquete entra al dispositivo.
- **Salida (outbound):** cuando el paquete sale del dispositivo.

---

### 🖥️ Ejemplo real de configuración: ACL extendida como firewall

#### 🎯 Objetivo

- Permitir solo tráfico HTTP (puerto 80) y HTTPS (puerto 443) desde la red 192.168.10.0/24 al servidor 10.0.0.5.
- Bloquear todo lo demás.

---

#### 1. Crear la ACL

```bash
Router(config)# access-list 110 permit tcp 192.168.10.0 0.0.0.255 host 10.0.0.5 eq 80
Router(config)# access-list 110 permit tcp 192.168.10.0 0.0.0.255 host 10.0.0.5 eq 443
Router(config)# access-list 110 deny ip any any
```

📌 ¿Qué significan?

- `permit tcp`: solo permite protocolo TCP.
- `192.168.10.0 0.0.0.255`: cualquier equipo de esa red.
- `host 10.0.0.5`: solo al servidor web.
- `eq 80`: solo si se va al puerto HTTP (80).
- `deny ip any any`: bloquea todo lo demás.

---

#### 2. Aplicar la ACL en la interfaz de entrada

```bash
Router(config)# interface FastEthernet0/0
Router(config-if)# ip access-group 110 in
```

🧠 Significa: al entrar por esta interfaz, los paquetes deben **pasar la ACL 110**.

---

#### 3. Verificar que está funcionando

```bash
Router# show access-lists 110
```

Verás los contadores de cuántos paquetes han coincidido con cada línea.

---

### ✅ Resultado esperado

| Acción                  | ¿Está permitida? |
| ----------------------- | ---------------- |
| Acceso web (HTTP/HTTPS) | ✅ Sí            |
| Ping al servidor        | ❌ No            |
| FTP al servidor         | ❌ No            |
| SSH al servidor         | ❌ No            |

---

### 📘 Reglas clave al diseñar una ACL tipo firewall

| Regla                       | Descripción                                            |
| --------------------------- | ------------------------------------------------------ |
| **Menor a mayor**           | Primero lo específico, luego lo general.               |
| **Menor acceso posible**    | Solo permitir lo que es necesario.                     |
| **Deny implícito**          | Todo lo que no coincida con ninguna regla se bloquea.  |
| **Documentar siempre**      | Usa comentarios si es posible para recordar la lógica. |
| **Probar antes de aplicar** | Hazlo en simuladores como Packet Tracer o GNS3.        |

---

### 🔄 ¿Y cómo se revierte o edita una ACL?

Puedes eliminar toda una ACL con:

```bash
Router(config)# no access-list 110
```

O eliminar una sola línea si usas **ACLs nombradas**, por ejemplo:

```bash
Router(config)# ip access-list extended FIREWALL_WEB
Router(config-ext-nacl)# no permit tcp 192.168.10.0 0.0.0.255 host 10.0.0.5 eq 443
```

---

### 🧪 Ejemplo completo en Packet Tracer (resumen visual)

```
[PC1] ----------------- [Switch] --- [Router] --- [Servidor Web]
192.168.10.10            Fa0/0         Fa0/1         10.0.0.5
192.168.10.1                                         10.0.0.1
```

ACL en Fa0/0:

```bash
access-list 110 permit tcp 192.168.10.0 0.0.0.255 host 10.0.0.5 eq 80
access-list 110 permit tcp 192.168.10.0 0.0.0.255 host 10.0.0.5 eq 443
access-list 110 deny ip any any
interface fa0/0
ip access-group 110 in
```

🎯 Solo se permite tráfico web hacia el servidor desde la LAN. Nada más.

---

### 🧾 Resumen final

- Las ACL son como **firewalls con reglas manuales**.
- Evalúan paquetes en orden hasta que una condición se cumple.
- Son vitales para **filtrar tráfico**, **aumentar seguridad** y **controlar acceso**.
- Pueden usarse tanto en routers como switches de capa 3.

---

[🔼](#índice)

---

## **710. Ataques al servicio DNS ¿Qué pasa cuando me engañan con el nombre?**

### ¿Qué pasa cuando me engañan con el nombre?

---

### 🔍 ¿Qué es el DNS?

DNS (Domain Name System) es como la **guía telefónica de Internet**. Traduce nombres fáciles para humanos (como `www.google.com`) en direcciones IP que entienden las máquinas (como `142.250.64.100`).

> 🎯 Ejemplo:
>
> Cuando escribes `www.facebook.com`, tu computadora pregunta al DNS:
>
> _"¿Cuál es la IP de facebook.com?"_
>
> El DNS responde: `157.240.229.35`
>
> Luego tu navegador accede a esa IP.

---

### 💣 ¿Qué es un ataque al DNS?

Es cuando **un atacante manipula o intercepta el proceso de resolución de nombres** para redirigirte a un sitio falso, malicioso o interceptar tu tráfico.

---

### 🎭 ¿Qué pasa cuando me engañan con el nombre?

> Se llama **suplantación de DNS** o **DNS Spoofing / DNS Poisoning**.

Tú crees que estás visitando un sitio legítimo (`www.tubanco.com`), pero el DNS ha sido manipulado y te lleva a un sitio falso idéntico, donde el atacante puede robar tu contraseña.

---

### 🛠️ ¿Cómo me pueden engañar?

#### 🔸 1. **DNS Spoofing (suplantación DNS)**

Un atacante **responde falsamente a una consulta DNS** antes que el servidor real, haciendo que tu equipo guarde (cachee) esa respuesta falsa.

📌 Ejemplo:

- Tú visitas `banco.com`
- El atacante responde que la IP de `banco.com` es `123.123.123.123` (un sitio falso)
- Tu equipo guarda esa IP y la usará hasta que expire (por minutos o días)

---

#### 🔸 2. **DNS Cache Poisoning (envenenamiento de caché)**

El atacante **modifica la caché del servidor DNS**, no solo la tuya.

📌 Resultado:

- Todos los que usen ese servidor también serán redirigidos al sitio falso.

---

#### 🔸 3. **Man-in-the-Middle (MitM) con DNS**

El atacante se sitúa entre tú y el servidor DNS y **intercepta o modifica la respuesta**.

📌 Muy común en redes WiFi públicas mal configuradas.

---

### 🧪 ¿Qué puede pasar si caes en el engaño?

- Te redirigen a **sitios falsos** para robar tus credenciales (phishing).
- Instalan **malware** desde páginas que parecen legítimas.
- Te bloquean el acceso a sitios reales (DoS).
- Te hacen participar en ataques (como botnets).

---

### 🔐 ¿Cómo protegerse?

#### ✅ Para usuarios:

| Medida                                                                       | ¿Qué hace?                                  |
| ---------------------------------------------------------------------------- | ------------------------------------------- |
| Usar **HTTPS** siempre                                                       | Evita que páginas falsas parezcan legítimas |
| Verificar el **candado 🔒** en la URL                                        | Asegura que estás en el sitio real          |
| Usar **DNS seguros** como Cloudflare (`1.1.1.1`), Google (`8.8.8.8`) o Quad9 | Evita usar servidores DNS vulnerables       |
| Instalar **antivirus** o extensiones de seguridad                            | Detecta sitios falsos                       |
| Desactivar DNS en caché (si es posible)                                      | Previene respuestas falsas persistentes     |

---

#### ✅ Para administradores/redes:

| Medida                                                 | Descripción                                            |
| ------------------------------------------------------ | ------------------------------------------------------ |
| **DNSSEC (DNS Security Extensions)**                   | Firma digital que garantiza autenticidad de respuestas |
| Configurar **firewalls** y reglas de DNS               | Solo permitir DNS legítimos                            |
| Usar **DoH (DNS over HTTPS)** o **DoT (DNS over TLS)** | Encripta las consultas DNS                             |
| Monitorear cambios en DNS y logs                       | Detectar respuestas anómalas o IPs sospechosas         |
| Limpiar cachés DNS frecuentemente                      | Evita usar datos envenenados por largo tiempo          |

---

### 🧱 ¿Cómo se simula o “instala” un ataque en laboratorio?

(Para prácticas seguras con fines educativos en red local)

#### Herramientas:

- **Kali Linux** (para ataque)
- **Windows/Linux cliente**
- Red local (o VirtualBox con red interna)

#### Ejemplo de herramienta: `ettercap` o `dnschef`

```bash
sudo dnschef --fakeip 192.168.1.50
```

Este comando redirige todas las consultas DNS al falso `192.168.1.50`.

---

### 🧪 Ejemplo completo (simulado en red local o Packet Tracer)

#### 🔧 Escenario

| Dispositivo | IP           | Función                  |
| ----------- | ------------ | ------------------------ |
| PC Víctima  | 192.168.1.10 | Navega a banco.com       |
| DNS Server  | 192.168.1.1  | Resuelve nombres         |
| Atacante    | 192.168.1.99 | Responde con IP falsa    |
| Sitio falso | 192.168.1.50 | Copia de banco.com falsa |

#### 🧬 Resultado

- El atacante responde más rápido con `banco.com → 192.168.1.50`
- El navegador de la víctima carga el sitio falso
- El usuario escribe usuario/clave
- Atacante captura los datos

---

### 🛡️ Solución implementada con Cloudflare DNS

Configura tu equipo para usar `1.1.1.1` como DNS seguro:

#### En Windows:

1. Ve a **Configuración > Red e Internet > Cambiar opciones de adaptador**.
2. Haz clic derecho en tu red → Propiedades.
3. Selecciona **Protocolo de Internet versión 4 (TCP/IPv4)**.
4. Marca "Usar las siguientes direcciones de servidor DNS":

   - Preferido: `1.1.1.1`
   - Alternativo: `1.0.0.1`

5. Acepta.

✔️ Eso reduce mucho el riesgo de usar un servidor DNS envenenado o malicioso.

---

### 🧾 Resumen final

| Punto clave                                                                | Explicación                                   |
| -------------------------------------------------------------------------- | --------------------------------------------- |
| DNS convierte nombres en IPs                                               | Sin DNS, no podrías navegar por nombre        |
| Ataques al DNS modifican esa conversión                                    | Redirigen al usuario a sitios falsos          |
| Existen técnicas como spoofing y envenenamiento                            | Afectan tanto al cliente como al servidor DNS |
| La protección incluye DNSSEC, DNS sobre HTTPS y usar servidores confiables | Mejora la seguridad                           |

---

[🔼](#índice)

---

| **Inicio**         | **atrás 4**                                   | **Siguiente 6**                                         |
| ------------------ | --------------------------------------------- | ------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./7_4_Redes_Informaticas_de_Internet.md) | [⏩](./7_6_Guia_para_Aprender_Seguridad_Informatica.md) |
