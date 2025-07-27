| **Inicio**         | **atrás 9**                                        | **Siguiente 11**                   |
| ------------------ | -------------------------------------------------- | ---------------------------------- |
| [🏠](../README.md) | [⏪](./7_9_Curso_de_Introduccion_al_Pentesting.md) | [⏩](./7_11_Pentesting_a_Redes.md) |

---

## **Índice**

| Temario                                                                                                                          |
| -------------------------------------------------------------------------------------------------------------------------------- |
| [793. Conceptos y consideraciones en el diseño de redes seguras](#793-conceptos-y-consideraciones-en-el-diseño-de-redes-seguras) |
| [794. Segmentación de redes](#794-segmentación-de-redes)                                                                         |
| [795. Configuración de VLAN](#795-configuración-de-vlan)                                                                         |
| [796. Conexiones site to site y acceso remoto - VPN](#796-conexiones-site-to-site-y-acceso-remoto---vpn)                         |
| [797. Seguridad en puertos de red](#797-seguridad-en-puertos-de-red)                                                             |
| [798. Spanning Tree Protocol](#798-spanning-tree-protocol)                                                                       |
| [799. Firewalls como software](#799-firewalls-como-software)                                                                     |
| [800. Firewall UTM y NGFW](#800-firewall-utm-y-ngfw)                                                                             |
| [801. Protocolos seguros en redes de datos](#801-protocolos-seguros-en-redes-de-datos)                                           |
| [802. Control de acceso a red - NAC](#802-control-de-acceso-a-red---nac)                                                         |

# **Seguridad de Redes On-Premise**

## **793. Conceptos y consideraciones en el diseño de redes seguras**

### 🧠 ¿Qué es el diseño de redes seguras?

El **diseño de redes seguras** consiste en planear cómo se construye, organiza y protege una red informática para que **solo las personas y sistemas autorizados puedan acceder a ella**, mientras se evita que **usuarios no deseados** roben o dañen datos.

> 🛡️ Su propósito es **prevenir ataques**, **minimizar riesgos** y **mantener la disponibilidad, integridad y confidencialidad de la información**.

---

### 🧩 Conceptos clave en una red segura

| Concepto                                 | Explicación simple                                               | Ejemplo fácil                              |
| ---------------------------------------- | ---------------------------------------------------------------- | ------------------------------------------ |
| 🔐 **Segmentación de red**               | Dividir la red en partes para limitar el movimiento de amenazas. | Red separada para invitados y empleados.   |
| 🔍 **Control de acceso**                 | Solo personas autorizadas pueden acceder a recursos.             | Usuario necesita contraseña para imprimir. |
| 🧱 **Firewalls**                         | Dispositivo que decide qué tráfico entra o sale de la red.       | Bloquea conexiones no autorizadas.         |
| 📡 **DMZ (zona desmilitarizada)**        | Área expuesta al exterior pero separada de la red interna.       | Servidor web en una zona aislada.          |
| 🕵️ **IDS/IPS**                           | Sistemas que detectan o previenen ataques en tiempo real.        | IDS avisa si alguien escanea puertos.      |
| 🔐 **Cifrado (en tránsito y en reposo)** | Proteger datos cuando viajan y cuando están almacenados.         | HTTPS en sitios web y discos cifrados.     |
| 🔒 **Principio de mínimo privilegio**    | Dar solo los permisos necesarios.                                | Usuario solo puede leer, no borrar.        |
| 📋 **Políticas de seguridad**            | Normas que definen lo que se puede o no hacer.                   | Prohibido conectar USB desconocidos.       |

---

### ⚙️ Consideraciones importantes al diseñar una red segura

1. **¿Quién accede a qué?**

   - Define roles y permisos (ej. administrador vs usuario normal).

2. **¿Dónde están los recursos sensibles?**

   - Servidores, bases de datos, cámaras, etc. deben estar en zonas protegidas.

3. **¿Qué dispositivos se conectan a la red?**

   - Solo permitir PCs y móviles autorizados (uso de MAC filtering o NAC).

4. **¿Qué servicios están expuestos a internet?**

   - Si hay una página web o servidor SSH, ubícalos en la **DMZ**.

5. **¿Hay políticas de respaldo y monitoreo?**

   - Backups automáticos + logs de actividad = más seguridad.

---

### 🧰 Herramientas y tecnologías comunes

| Herramienta / Tecnología   | Para qué sirve                                    |
| -------------------------- | ------------------------------------------------- |
| **pfSense / OPNsense**     | Firewalls avanzados gratuitos.                    |
| **Wireshark**              | Analiza el tráfico de red.                        |
| **Snort / Suricata**       | IDS/IPS para detectar ataques.                    |
| **VLANs**                  | Separar tráfico interno (usuarios, cámaras, etc.) |
| **VPN**                    | Acceso remoto seguro.                             |
| **Active Directory + GPO** | Gestión de usuarios y políticas en redes Windows. |

---

### 🛠️ ¿Cómo se instala o diseña?

Aunque no se “instala” como un software, el **diseño de una red segura** se puede implementar paso a paso.

---

### ✅ Paso a paso: Diseñar una red segura simple

#### 🏠 Escenario:

Eres administrador de una oficina pequeña con:

- 10 empleados
- Un servidor de archivos
- Un servidor web público
- Conexión a Internet
- Cámaras IP
- Red WiFi para invitados

---

#### 🔧 Paso 1: Dibujar la red (arquitectura)

**Separar zonas con VLAN o subredes:**

1. 🔒 **Red interna de empleados** (acceso a archivos)
2. 🌐 **DMZ para el servidor web**
3. 🎥 **Red de cámaras IP (solo tráfico local)**
4. 📱 **Red WiFi de invitados (sin acceso a recursos internos)**

---

#### 🔧 Paso 2: Establecer controles

- Configurar un **firewall** (como pfSense):

  - Solo la red de empleados puede acceder al servidor de archivos.
  - DMZ no puede acceder a la red interna.
  - Invitados solo pueden navegar por internet.

- Activar **cifrado WPA3 en WiFi**

- Activar **HTTPS y SSH seguros**

- Crear **copias de seguridad programadas**

---

#### 🔧 Paso 3: Implementar políticas

- Crear usuarios con permisos mínimos
- Desactivar puertos no usados en switches
- Deshabilitar auto ejecución de dispositivos USB
- Usar contraseñas fuertes y doble autenticación

---

### 🧪 Ejemplo completo: Diseño básico de red segura

#### 🔍 Plano conceptual (simplificado):

```
             INTERNET
                 |
              [Firewall]
                 |
     --------------------------
    |            |             |
 [DMZ]     [Red Interna]   [WiFi Invitados]
  |              |             |
[Web Server] [PCs + FileSrv] [Navegación solo]
```

#### 🔐 Reglas del Firewall (ejemplo pfSense):

| Fuente    | Destino    | Puerto | Acción   |
| --------- | ---------- | ------ | -------- |
| Invitados | Interna    | \*     | Denegar  |
| Interna   | Internet   | 80,443 | Permitir |
| DMZ       | Interna    | \*     | Denegar  |
| Internet  | Web Server | 80,443 | Permitir |

---

#### 🛠️ Herramientas utilizadas:

- pfSense (como firewall con VLANs)
- Wireshark para analizar tráfico
- Switch gestionable para separar VLANs
- Servidor Ubuntu con Samba para archivos internos
- Apache en la DMZ

---

### ✅ Beneficios de este diseño

- Si un hacker entra por el servidor web, no puede llegar a los archivos.
- Los invitados no pueden espiar a los empleados.
- Las cámaras no pueden ser secuestradas desde internet.
- Todos los accesos quedan registrados.

---

### 🧠 Conclusión

El diseño de redes seguras **no depende solo de software**, sino de:

- **Arquitectura lógica bien pensada**
- **Segmentación adecuada**
- **Restricciones mínimas necesarias**
- **Monitoreo constante**

---

[🔼](#índice)

---

## **794. Segmentación de redes**

### 🧠 ¿Qué es la segmentación de redes?

La **segmentación de redes** es el proceso de dividir una red grande en **subredes más pequeñas (segmentos)**. Esto se hace por razones de **seguridad, rendimiento y organización**.

> Piensa en una oficina grande: separar departamentos (Contabilidad, IT, Ventas) es más seguro que tenerlos todos mezclados. Igual ocurre con las redes.

---

### 🎯 ¿Para qué sirve?

1. **Seguridad**: si un atacante accede a una parte, no accede a todo.
2. **Rendimiento**: menos tráfico innecesario en cada segmento.
3. **Control**: reglas de firewall y monitoreo por segmento.
4. **Aislamiento**: usuarios invitados, cámaras IP, servidores, etc. no deberían hablar entre sí.

---

### 🧩 Tipos de segmentación

| Tipo                           | Explicación simple                                           | Ejemplo                                                  |
| ------------------------------ | ------------------------------------------------------------ | -------------------------------------------------------- |
| 🔹 **Subredes (Subnetting)**   | Divide la red en rangos de IP diferentes.                    | 192.168.1.0/24 para PCs, 192.168.2.0/24 para servidores. |
| 🔸 **VLANs (Redes Virtuales)** | Crea redes lógicas independientes en un mismo switch físico. | VLAN 10 para ventas, VLAN 20 para IT.                    |
| 🔻 **Zonas de seguridad**      | Segmentación basada en funciones: interna, DMZ, invitados.   | Web server en la zona DMZ.                               |

---

### 🛡️ Beneficios principales

- **Aumenta la seguridad**: impide movimientos laterales de malware.
- **Reduce el riesgo**: si un segmento se ve comprometido, el resto está aislado.
- **Permite políticas más claras**: por ejemplo, "la VLAN de cámaras no puede acceder a internet".

---

### ⚙️ ¿Cómo se implementa?

#### Opción 1: Segmentación con subredes

1. Asigna diferentes **rangos de IP** a distintos dispositivos.
2. Usa routers/firewalls para permitir o denegar tráfico entre subredes.

**Ejemplo:**

| Segmento       | Rango IP        |
| -------------- | --------------- |
| Empleados      | 192.168.10.0/24 |
| Servidores     | 192.168.20.0/24 |
| Cámaras IP     | 192.168.30.0/24 |
| Invitados WiFi | 192.168.40.0/24 |

---

#### Opción 2: Segmentación con VLANs (más común en empresas)

1. Configura **VLANs en tu switch gestionable**.
2. Asigna puertos a cada VLAN.
3. Usa un **router o firewall (como pfSense o Mikrotik)** para controlar tráfico entre VLANs.

**Ejemplo de VLANs:**

| VLAN | Nombre     | Dispositivos            |
| ---- | ---------- | ----------------------- |
| 10   | Empleados  | PCs y laptops           |
| 20   | Servidores | Servidores internos     |
| 30   | Cámaras    | Cámaras de seguridad    |
| 40   | Invitados  | Celulares de visitantes |

---

### 🛠️ Herramientas necesarias

| Herramienta                     | Función                                    |
| ------------------------------- | ------------------------------------------ |
| Switch gestionable              | Crear y asignar VLANs                      |
| Router o firewall (ej. pfSense) | Gestionar el tráfico entre VLANs           |
| DHCP por VLAN o por subred      | Dar IPs diferentes por segmento            |
| Wireshark                       | Comprobar que los segmentos están aislados |

---

### ✅ Paso a paso para implementar segmentación con VLANs (ejemplo real)

#### 🎯 Escenario: Red pequeña de oficina

Tienes:

- 1 switch gestionable (ej. TP-Link, Cisco)
- 1 router con pfSense
- PCs de empleados, cámaras IP y una red WiFi para invitados

---

#### 🔧 Paso 1: Configurar VLANs

En el **switch gestionable**, define:

| VLAN ID | Nombre    | Puertos asignados     |
| ------- | --------- | --------------------- |
| 10      | Empleados | Puertos 1–10          |
| 20      | Cámaras   | Puertos 11–14         |
| 30      | Invitados | Puerto 15 (AP WiFi)   |
| 99      | Trunk     | Puerto 24 (al router) |

---

#### 🔧 Paso 2: Configurar pfSense (router/firewall)

1. **Crear interfaces por VLAN**:

   - VLAN 10 → 192.168.10.1/24
   - VLAN 20 → 192.168.20.1/24
   - VLAN 30 → 192.168.30.1/24

2. **Asignar reglas de firewall**:

   - VLAN 10 puede salir a internet y acceder a servidores.
   - VLAN 20 (cámaras) solo puede hablar con NVR, no con internet.
   - VLAN 30 (invitados) solo internet, sin acceso interno.

---

#### 🔧 Paso 3: Verificar

- PCs de empleados no pueden ver cámaras.
- Cámaras no acceden a internet.
- Invitados no acceden a la red interna.
- Puedes comprobarlo con **ping** o **Wireshark**.

---

### 🧪 Ejemplo completo y funcional

#### 🎯 Objetivo: Red segura con 3 segmentos

1. **Empleados** – VLAN 10 – IPs: 192.168.10.0/24
2. **Cámaras IP** – VLAN 20 – IPs: 192.168.20.0/24
3. **WiFi invitados** – VLAN 30 – IPs: 192.168.30.0/24

#### 🔐 Reglas del firewall (en pfSense):

| Desde   | Hacia               | Puerto | Acción   |
| ------- | ------------------- | ------ | -------- |
| VLAN 10 | Internet            | \*     | Permitir |
| VLAN 20 | Internet            | \*     | Denegar  |
| VLAN 20 | NVR (192.168.10.50) | \*     | Permitir |
| VLAN 30 | Internet            | \*     | Permitir |
| VLAN 30 | VLAN 10/20          | \*     | Denegar  |

---

### 📌 Conclusión

La segmentación de redes:

- Es **clave para la seguridad y rendimiento** de una red.
- Se puede hacer con **subredes o VLANs**.
- Aísla dispositivos según su función o nivel de confianza.
- Permite aplicar reglas claras y efectivas para minimizar riesgos.

---

[🔼](#índice)

---

## **795. Configuración de VLAN**

### 🧠 ¿Qué es una VLAN?

**VLAN** significa **Virtual Local Area Network**.

Es una tecnología que permite **dividir una red física en varias redes lógicas**, sin necesidad de hardware adicional. Aunque todos los dispositivos estén conectados al mismo switch, se comportan como si estuvieran en redes diferentes.

> **Ejemplo real**: En una oficina, puedes tener:
>
> - VLAN 10 para empleados
> - VLAN 20 para cámaras de seguridad
> - VLAN 30 para visitantes
>
>   ¡Y todo usando el mismo switch físico!

---

### 🛡️ ¿Para qué sirven las VLANs?

- **Seguridad**: usuarios de una VLAN no pueden ver el tráfico de otra.
- **Control de tráfico**: evita que todo el tráfico pase por toda la red.
- **Organización**: separa departamentos o servicios (servidores, cámaras, invitados, etc.).

---

### 🧩 ¿Qué necesitas para configurarlas?

1. **Switch gestionable** (TP-Link, Cisco, D-Link, etc.)
2. **Router compatible con VLANs** (ej. pfSense, MikroTik, Cisco)
3. **Conocimiento de las VLAN IDs y rangos IP** a usar
4. Opcional: un servidor DHCP por VLAN o configuración manual de IPs

---

### 🧰 Ejemplo de diseño de VLAN

| VLAN ID | Nombre     | Rango IP        | Uso                  |
| ------- | ---------- | --------------- | -------------------- |
| 10      | Empleados  | 192.168.10.0/24 | PCs, laptops         |
| 20      | Cámaras IP | 192.168.20.0/24 | Cámaras de seguridad |
| 30      | Invitados  | 192.168.30.0/24 | WiFi de visitantes   |

---

### ⚙️ Cómo configurar VLAN en un switch TP-Link gestionable (ejemplo real)

#### 🎯 Objetivo: dividir 3 VLANs en un switch físico

##### Paso 1: Acceder al switch

1. Conéctate al switch por navegador (ej: [http://192.168.0.1](http://192.168.0.1))
2. Ingresa usuario y contraseña (por defecto es `admin`/`admin`)
3. Ve a la sección **VLAN > 802.1Q VLAN**

---

#### Paso 2: Crear VLANs

1. Activa **802.1Q VLAN**.
2. Agrega estas VLANs:

| VLAN ID | VLAN Name |
| ------- | --------- |
| 10      | Empleados |
| 20      | Cámaras   |
| 30      | Invitados |

---

#### Paso 3: Asignar puertos a cada VLAN

**Ejemplo de distribución física:**

| Puerto | Dispositivo conectado  | VLAN ID | Tipo         |
| ------ | ---------------------- | ------- | ------------ |
| 1–8    | PCs de empleados       | 10      | **Untagged** |
| 9–12   | Cámaras IP             | 20      | **Untagged** |
| 13     | Access Point invitados | 30      | **Untagged** |
| 24     | Va al router/pfSense   | Todas   | **Tagged**   |

💡 **Untagged** = dispositivo final
💡 **Tagged** = trunk (transporta varias VLANs a la vez)

---

#### Paso 4: Configurar el router o firewall

##### Con pfSense o MikroTik:

- Crear interfaces virtuales por cada VLAN:

  - VLAN 10 → IP: 192.168.10.1/24
  - VLAN 20 → IP: 192.168.20.1/24
  - VLAN 30 → IP: 192.168.30.1/24

- Activar **DHCP Server** para cada una.

- Establecer reglas de firewall:

  - VLAN 10 puede acceder a internet.
  - VLAN 20 puede comunicarse solo con su NVR.
  - VLAN 30 puede salir a internet, pero no ver la LAN.

---

### 🧪 Ejemplo completo funcional: red con 3 VLANs

#### 🖼️ Diagrama lógico

```
         [ Internet ]
              |
           [ pfSense ]
              | (Puerto trunk)
           [ Switch TP-Link ]
        /       |        \
   VLAN 10   VLAN 20   VLAN 30
(PCs)     (Cámaras)   (WiFi invitados)
```

#### Configuración en resumen:

| Puerto | VLAN ID           | Descripción                 |
| ------ | ----------------- | --------------------------- |
| 1–8    | 10                | PC de empleados             |
| 9–12   | 20                | Cámaras IP                  |
| 13     | 30                | Access Point para invitados |
| 24     | 10,20,30 (Tagged) | Trunk al pfSense/router     |

---

### ✅ Verificación

- 🔍 Desde un PC de empleados: accede a internet, no ve cámaras.
- 🔍 Desde una cámara: no tiene acceso a la red general.
- 🔍 Desde la WiFi de invitados: acceso solo a internet.
- 📦 Usa **Wireshark** para probar el aislamiento de tráfico.

---

### 🧠 ¿Cómo saber que lo hiciste bien?

- Haces `ping` desde un dispositivo de una VLAN a otra y no responde (bloqueado).
- Todos tienen IPs diferentes según su VLAN.
- Puedes ver el tráfico dividido y controlado.

---

### 🚀 Herramientas para probar y configurar

| Herramienta        | Uso                           |
| ------------------ | ----------------------------- |
| Wireshark          | Captura de paquetes           |
| nmap               | Escaneo de red                |
| pfSense / MikroTik | Firewall, routing entre VLANs |
| DHCP en pfSense    | Asignación de IPs por VLAN    |
| TP-Link/Cisco      | Switch gestionable            |

---

### 🎁 Conclusión

- Las **VLANs aíslan y organizan tu red** de forma virtual y segura.
- Se pueden aplicar fácilmente con switches gestionables + routers compatibles.
- Son ideales para **proteger redes empresariales**, separar usuarios y limitar accesos.
- Una buena configuración evita movimientos laterales de amenazas (como ransomware).

---

[🔼](#índice)

---

## **796. Conexiones site to site y acceso remoto - VPN**

### 🧠 ¿Qué es una VPN?

**VPN (Virtual Private Network)** es una red virtual segura que permite **interconectar equipos o redes a través de Internet de forma cifrada**, como si estuvieran en una red local.

Existen **dos tipos principales**:

| Tipo de VPN       | ¿Para qué sirve?                                                                  |
| ----------------- | --------------------------------------------------------------------------------- |
| **Site-to-Site**  | Conecta **dos redes LAN completas** entre oficinas, sedes, etc.                   |
| **Acceso remoto** | Permite que **usuarios individuales** accedan a la red de la empresa desde fuera. |

---

### 🧩 Diferencia entre Site-to-Site y Acceso Remoto

| Característica       | Site-to-Site                            | Acceso remoto                  |
| -------------------- | --------------------------------------- | ------------------------------ |
| Uso principal        | Conexión entre sedes (empresa–sucursal) | Teletrabajo, usuarios externos |
| Usuarios             | Redes completas                         | Dispositivos individuales      |
| Configuración típica | Routers/firewalls en ambos extremos     | Cliente VPN en PC o móvil      |
| Tecnología           | IPsec, OpenVPN, WireGuard               | OpenVPN, L2TP, PPTP, WireGuard |

---

### 🛠️ Tecnologías VPN comunes

| Protocolo  | Seguro | Uso actual      | Comentario                 |
| ---------- | ------ | --------------- | -------------------------- |
| PPTP       | ❌ No  | Obsoleto        | No recomendado             |
| L2TP/IPsec | ✅     | Medio           | Soporte en muchos sistemas |
| OpenVPN    | ✅✅   | Muy usado       | Open Source, robusto       |
| WireGuard  | ✅✅✅ | Nuevo y moderno | Rápido, fácil, muy seguro  |

---

### 📦 Requisitos para una VPN Site-to-Site

- 2 routers o firewalls que **soporten IPsec/OpenVPN**
- Direcciones IP públicas en ambos extremos (o DDNS)
- Buen ancho de banda
- Permitir puertos específicos en firewall

---

### ✅ Ejemplo: VPN Site-to-Site con pfSense

#### Escenario:

- Oficina A (Central): IP pública 45.90.100.10 – Red interna: `192.168.10.0/24`
- Oficina B (Sucursal): IP pública 200.55.30.20 – Red interna: `192.168.20.0/24`

Queremos que las dos redes **se comuniquen como si fueran una sola LAN.**

---

#### Paso 1: Instalar pfSense (en ambas oficinas)

Sigue el mismo proceso que cualquier instalación de pfSense en una máquina o máquina virtual. Puedes usar una PC antigua, VMware o Proxmox.

Más info: [https://www.pfsense.org/download/](https://www.pfsense.org/download/)

---

#### Paso 2: Configurar VPN IPsec (en ambas pfSense)

##### En pfSense de la Oficina A:

1. Ir a: **VPN > IPsec > Tunnels**
2. Agregar nueva entrada:

   - **Remote Gateway**: `200.55.30.20` (oficina B)
   - **Pre-shared key**: una contraseña compartida (ej: `claveSegura2025`)

3. Fase 1 (IKE):

   - **Authentication**: Pre-shared Key
   - **My identifier**: IP address
   - **Encryption**: AES-256, SHA256, DH Group 14

4. Fase 2 (ESP):

   - **Local subnet**: `192.168.10.0/24`
   - **Remote subnet**: `192.168.20.0/24`

##### Repetir los mismos pasos en pfSense de la Oficina B, **invirtiendo los valores**.

---

#### Paso 3: Reglas de firewall

En **Firewall > Rules > IPsec**, permitir:

```plaintext
Protocol: Any
Source: 192.168.10.0/24
Destination: 192.168.20.0/24
```

Y viceversa en la otra sede.

---

#### ✅ Verificación

Desde un PC en la red de la oficina A:

```bash
ping 192.168.20.5
```

Y desde un PC en oficina B:

```bash
ping 192.168.10.5
```

¡Si hay respuesta, la VPN funciona! 🎉

---

### 📱 Acceso remoto con VPN (OpenVPN)

Ideal para **empleados que trabajan desde casa**.

#### Paso 1: En pfSense

1. Ir a **VPN > OpenVPN > Wizards**
2. Crear un servidor con:

   - Puerto: 1194 UDP
   - Tunnel Network: `10.10.10.0/24`
   - Local Network: `192.168.10.0/24`
   - Exportar archivo `.ovpn` para los usuarios

---

#### Paso 2: En el cliente

1. Instalar **OpenVPN Connect** o **OpenVPN GUI**
2. Importar el archivo `.ovpn`
3. Conectar → ¡ya forma parte de la red interna!

Ahora el empleado puede acceder a:

- Servidores internos
- Sistemas de gestión (ERP, CRM)
- Impresoras de red

---

### 🌐 ¿Qué puertos debes abrir?

| VPN       | Puerto     | Protocolo |
| --------- | ---------- | --------- |
| OpenVPN   | 1194       | UDP       |
| IPsec     | 500 y 4500 | UDP       |
| WireGuard | 51820      | UDP       |

---

### 🔐 Buenas prácticas de seguridad

✅ Usa contraseñas fuertes o certificados

✅ Cambia claves precompartidas con frecuencia

✅ Limita qué redes pueden verse entre sí

✅ Activa logs y alertas

---

### 🎁 Resumen final

| Tipo de VPN   | Mejor para                         | Tecnología          | Dificultad |
| ------------- | ---------------------------------- | ------------------- | ---------- |
| Site-to-Site  | Conectar redes de distintas sedes  | IPsec / OpenVPN     | Media      |
| Acceso remoto | Teletrabajo, administración remota | OpenVPN / WireGuard | Baja       |

---

[🔼](#índice)

---

## **797. Seguridad en puertos de red**

### 🔐 ¿Qué es la Seguridad en Puertos de Red?

Un **puerto de red** es como una puerta virtual por donde entran y salen los datos en un dispositivo conectado a una red. Cada aplicación o servicio (como un servidor web o de correo) utiliza **puertos específicos** para comunicarse.

**La seguridad en puertos de red** consiste en:

- **Controlar qué puertos están abiertos**
- **Cerrar los innecesarios**
- **Proteger los que deben estar abiertos**
- **Monitorear y detectar accesos no autorizados**

---

### 🎯 ¿Por qué es importante?

- Los **ataques automáticos** suelen escanear puertos abiertos en busca de vulnerabilidades.
- Puertos mal configurados pueden exponer servicios críticos.
- Algunos malware utilizan puertos específicos para propagarse o comunicarse con atacantes.

---

### 🚪 Ejemplos comunes de puertos

| Servicio | Puerto | Protocolo | Descripción                 |
| -------- | ------ | --------- | --------------------------- |
| HTTP     | 80     | TCP       | Navegación web sin cifrado  |
| HTTPS    | 443    | TCP       | Navegación segura           |
| SSH      | 22     | TCP       | Acceso remoto seguro        |
| FTP      | 21     | TCP       | Transferencia de archivos   |
| RDP      | 3389   | TCP       | Escritorio remoto (Windows) |
| DNS      | 53     | UDP/TCP   | Resolución de nombres       |

---

### 🛠️ Herramientas para asegurar puertos

#### 🔎 1. **Nmap** – Escaneo de puertos

Permite descubrir qué puertos están abiertos en un host o red.

Instalación (Linux/Debian):

```bash
sudo apt update
sudo apt install nmap
```

Escanear un equipo:

```bash
nmap 192.168.1.10
```

---

#### 🔐 2. **Firewall (UFW, iptables, pf, Windows Defender Firewall)**

Sirve para **bloquear o permitir puertos**.

##### UFW en Linux (más amigable que iptables):

Instalación:

```bash
sudo apt install ufw
```

Activar UFW y permitir solo lo necesario:

```bash
sudo ufw enable
sudo ufw default deny incoming
sudo ufw allow 22   # SSH
sudo ufw allow 443  # HTTPS
```

Ver estado:

```bash
sudo ufw status
```

---

#### 👁️ 3. **Wireshark** – Inspección de tráfico

Puedes capturar y ver qué puertos se usan en tiempo real, útil para auditorías.

Instalación:

```bash
sudo apt install wireshark
```

> Puedes filtrar por puertos: `tcp.port == 22` o `udp.port == 53`

---

#### 📊 4. **Port Knocking** (avanzado)

Permite que un puerto esté **cerrado** por defecto y **solo se abra** si se recibe una secuencia específica de intentos en otros puertos. Así, un atacante no sabrá que ese puerto existe.

---

### ✅ Buenas prácticas de seguridad en puertos

| Recomendación                                  | Explicación                                           |
| ---------------------------------------------- | ----------------------------------------------------- |
| **Cierra puertos innecesarios**                | Reduce la superficie de ataque                        |
| **Cambia puertos por defecto (si es posible)** | SSH en 2222 en vez de 22, por ejemplo                 |
| **Aplica firewall en todos los niveles**       | Servidor, router y red interna                        |
| **Limita el acceso por IP o rango**            | Solo ciertas IP pueden usar ciertos puertos           |
| **Monitorea constantemente**                   | Con herramientas como `fail2ban`, `iptables`, `snort` |

---

### 💡 Ejemplo completo: Asegurar servidor Ubuntu

#### Objetivo:

- Permitir solo **SSH (puerto 22)** y **HTTPS (puerto 443)**
- Bloquear todo lo demás
- Detectar intentos de acceso no autorizados

#### Paso 1: Instalar y configurar UFW

```bash
sudo apt install ufw
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 22    # SSH
sudo ufw allow 443   # HTTPS
sudo ufw enable
```

#### Paso 2: Instalar `fail2ban` para bloquear IP maliciosas

```bash
sudo apt install fail2ban
```

Fail2ban escanea logs de puertos como SSH. Si ve múltiples intentos fallidos, **bloquea la IP automáticamente**.

#### Paso 3: Escanear desde otro equipo

Desde otra máquina (o Kali Linux):

```bash
nmap IP_DEL_SERVIDOR
```

Resultado esperado:

```
PORT    STATE SERVICE
22/tcp  open  ssh
443/tcp open  https
```

Todo lo demás debería estar cerrado o filtrado.

---

### 📌 Resumen

| Acción                    | Herramienta                                    |
| ------------------------- | ---------------------------------------------- |
| Escanear puertos          | `nmap`, `netstat`, `ss`                        |
| Configurar firewall       | `ufw`, `iptables`, `Windows Defender Firewall` |
| Monitorear tráfico        | `Wireshark`, `tcpdump`                         |
| Automatizar bloqueos      | `fail2ban`, `snort`                            |
| Ocultar puertos sensibles | Port Knocking, VPN                             |

---

[🔼](#índice)

---

## **798. Spanning Tree Protocol**

### 🧠 ¿Qué es el Spanning Tree Protocol (STP)?

**STP (Spanning Tree Protocol)** es un protocolo de red de nivel 2 (capa de enlace) usado en **redes LAN conmutadas (switches)** para **prevenir bucles de red**.

#### 🧩 ¿Por qué es importante?

En redes con **switches redundantes**, si hay múltiples caminos entre dispositivos, pueden ocurrir **bucles de red**, causando:

- Transmisiones infinitas
- Saturación de la red
- Fallos de comunicación

**STP** detecta estos caminos redundantes y **bloquea temporalmente algunos** para crear una **estructura libre de bucles (una "árbol sin bucles")**.

---

### 📦 Tipos de STP

| Tipo  | Descripción                                 |
| ----- | ------------------------------------------- |
| STP   | El original (IEEE 802.1D)                   |
| RSTP  | Rapid STP (IEEE 802.1w), más rápido         |
| MSTP  | Multiple STP (IEEE 802.1s), múltiples VLANs |
| PVST+ | Propietario de Cisco, STP por VLAN          |

---

### ⚙️ ¿Cómo funciona STP?

#### 🏗️ Conceptos clave:

| Término              | Definición                                                   |
| -------------------- | ------------------------------------------------------------ |
| **Root Bridge**      | El switch principal. Todos los caminos se calculan desde él. |
| **Bridge ID**        | Valor que identifica a cada switch (prioridad + MAC)         |
| **Coste del camino** | Métrica usada para elegir la mejor ruta al Root Bridge       |
| **Puerto Designado** | Puerto que reenvía tráfico en un segmento                    |
| **Puerto Bloqueado** | Puerto deshabilitado por STP para evitar bucles              |

#### 🧭 Ejemplo visual

Imagina 3 switches conectados en triángulo. Si todos reenvían paquetes, los datos podrían circular **infinitamente**. STP **bloquea uno de los enlaces**, dejando una única ruta libre de bucles.

---

### 🧰 Instalación o activación de STP

STP viene **activado por defecto en la mayoría de los switches gestionables** (Cisco, HP, MikroTik, etc). Pero puedes **verificarlo o configurarlo** manualmente.

#### En Cisco (CLI):

```bash
# Ver si STP está habilitado
show spanning-tree

# Habilitar STP globalmente
spanning-tree mode pvst

# Cambiar prioridad (para hacer root bridge)
conf t
spanning-tree vlan 1 priority 4096
```

#### En Linux (Bridge STP):

Puedes crear un **bridge** con STP activado:

```bash
sudo ip link add name br0 type bridge
sudo ip link set br0 type bridge stp_state 1
sudo ip link set dev br0 up
```

Verifica estado STP:

```bash
bridge link
```

---

### 🧪 Ejemplo completo: Laboratorio con STP en Cisco Packet Tracer

#### 🧱 Topología:

```
SW1 ---- SW2
 |         |
 |         |
 SW3-------
```

Una topología en triángulo: 3 switches conectados entre sí, formando un bucle.

#### ⚙️ Configuración:

##### Paso 1: Asigna prioridad para elegir Root Bridge

En **SW1**:

```bash
conf t
spanning-tree vlan 1 priority 4096
end
```

En **SW2 y SW3** (más alta para que **NO** sean root):

```bash
conf t
spanning-tree vlan 1 priority 32768
end
```

##### Paso 2: Verifica STP

En cualquier switch:

```bash
show spanning-tree
```

Verás:

- El **Root Bridge** (debería ser SW1)
- Qué puertos están en estado **Forwarding**
- Qué puertos están en **Blocking**

##### Resultado:

Uno de los enlaces (por ejemplo SW3 <-> SW2) estará en estado **blocking**, **previniendo bucles**.

---

### 🧠 Resumen

| Concepto            | Explicación rápida                                                 |
| ------------------- | ------------------------------------------------------------------ |
| ¿Qué hace STP?      | Previene bucles de red al bloquear enlaces                         |
| ¿Dónde se usa?      | En redes LAN con múltiples switches                                |
| ¿Cómo funciona?     | Elige un "Root Bridge", calcula rutas, bloquea enlaces redundantes |
| ¿Cómo lo configuro? | Switches Cisco o bridges en Linux                                  |
| ¿Qué tipo usar?     | RSTP (rápido), PVST (por VLAN), STP básico                         |

---

[🔼](#índice)

---

## **799. Firewalls como software**

### 🔥 ¿Qué es un Firewall como software?

Un **firewall (cortafuegos)** es una herramienta de seguridad que **controla el tráfico de red** que entra y sale de un equipo o red.
Cuando hablamos de **firewall como software**, nos referimos a programas que se instalan en un sistema operativo (como Windows o Linux) para **proteger el sistema** bloqueando o permitiendo conexiones según reglas definidas.

---

### 🧱 ¿Para qué sirve?

- **Evitar accesos no autorizados** a tu sistema.
- **Bloquear aplicaciones** que intentan conectarse a Internet sin permiso.
- **Proteger servicios vulnerables** que corren en puertos específicos.
- **Monitorear el tráfico** y detectar posibles amenazas.

---

### 🧑‍💻 Ejemplos de Firewalls como Software

| Sistema Operativo | Firewall Integrado        | Ejemplo de Terceros        |
| ----------------- | ------------------------- | -------------------------- |
| Windows           | Windows Defender Firewall | ZoneAlarm, Comodo Firewall |
| Linux             | iptables / nftables / ufw | firewalld                  |
| macOS             | pf (Packet Filter)        | Little Snitch              |

---

### 🛠️ ¿Cómo se instala y usa?

#### 🔹 En Windows (integrado)

Ya viene **instalado y activo por defecto**.

Ver estado:

1. Ve a **Panel de control > Sistema y seguridad > Firewall de Windows Defender**.
2. Puedes **permitir o bloquear aplicaciones**.
3. También puedes **crear reglas personalizadas** desde "Configuración avanzada".

Ejemplo: bloquear el puerto 21 (FTP):

1. Ve a "Configuración avanzada".
2. Crea una nueva regla de entrada.
3. Elige **Puerto > TCP > 21 > Bloquear conexión**.

---

#### 🔹 En Linux: usando **UFW** (interfaz simple para iptables)

##### 📦 Instalación

```bash
sudo apt update
sudo apt install ufw
```

##### 🚀 Activación

```bash
sudo ufw enable
```

##### ✅ Reglas comunes

```bash
# Permitir SSH
sudo ufw allow 22

# Bloquear puerto 21 (FTP)
sudo ufw deny 21

# Ver estado y reglas activas
sudo ufw status verbose
```

##### ❌ Desactivación temporal

```bash
sudo ufw disable
```

---

### 🔐 Buenas prácticas

- ✅ Permite **solo lo necesario** (principio de mínimo privilegio).
- 🔒 **Bloquea todo el tráfico entrante** y permite solo salientes si no sabes qué necesitas.
- 🔁 Revisa tus reglas periódicamente.
- ⚠️ Usa **logs** para ver intentos de acceso sospechosos (`/var/log/ufw.log` en Linux).

---

### 🧪 Ejemplo completo: Firewall como software en Ubuntu con UFW

#### 🎯 Objetivo:

Proteger un servidor Ubuntu de accesos no autorizados, permitiendo solo:

- Acceso por SSH (puerto 22)
- Acceso web por HTTPS (puerto 443)
- Bloquear todo lo demás

#### 🔧 Pasos

##### 1. Instalar y activar UFW

```bash
sudo apt install ufw
sudo ufw enable
```

##### 2. Definir reglas

```bash
# Reglas seguras
sudo ufw default deny incoming
sudo ufw default allow outgoing

# Permitir SSH y HTTPS
sudo ufw allow 22
sudo ufw allow 443
```

##### 3. Verificar configuración

```bash
sudo ufw status verbose
```

🔎 Resultado esperado:

```
Status: active
Default: deny (incoming), allow (outgoing)
To                         Action      From
--                         ------      ----
22                         ALLOW       Anywhere
443                        ALLOW       Anywhere
```

##### 4. Probar desde otra máquina

Usa `nmap` para escanear el servidor:

```bash
nmap IP_DEL_SERVIDOR
```

🔐 Solo deben aparecer **puertos 22 y 443** como "open".

---

### ✅ Conclusión

| Ventaja del Firewall como software       | Explicación                                     |
| ---------------------------------------- | ----------------------------------------------- |
| Protege el sistema desde adentro         | Controla aplicaciones y servicios localmente    |
| Muy configurable                         | Puedes crear reglas personalizadas muy precisas |
| Fácil de combinar con otras herramientas | Se integra con IDS, antivirus, logs, etc.       |

---

[🔼](#índice)

---

## **800. Firewall UTM y NGFW**

### 🔐 UTM (Unified Threat Management)

Un **firewall UTM** es una **solución todo en uno** que combina varias funciones de seguridad en un solo dispositivo o software.

#### 📦 Funciones típicas de un UTM:

- **Firewall tradicional** (filtrado de paquetes)
- **Antivirus**/antimalware
- **Sistema de detección/prevención de intrusiones (IDS/IPS)**
- **Filtrado web y de contenido**
- **VPN (red privada virtual)**
- **Control de aplicaciones**

#### ✅ Ventajas:

- Fácil de administrar (todo en un panel).
- Buena opción para **pymes y oficinas**.
- No necesitas configurar muchos dispositivos separados.

---

### 🔥 NGFW (Next-Generation Firewall)

Un **NGFW** (Firewall de nueva generación) va más allá de un UTM. Incluye todas sus funciones, **pero mejora el análisis de tráfico y control a nivel de aplicación**.

#### 🧠 Características clave de NGFW:

- **Inspección profunda de paquetes (DPI)**
- **Identificación y control de aplicaciones específicas** (por ejemplo, bloquear Facebook pero permitir WhatsApp)
- **Integración con inteligencia de amenazas en tiempo real**
- **Prevención avanzada de intrusos (IPS basado en firmas y comportamiento)**
- **Autenticación de usuarios**
- **Soporte para políticas basadas en identidad**

#### 🆚 Diferencia principal:

| 🔍                               | UTM                  | NGFW                                        |
| -------------------------------- | -------------------- | ------------------------------------------- |
| Inspección a nivel de aplicación | ❌ limitada          | ✅ profunda                                 |
| Enfoque                          | Solución todo en uno | Seguridad avanzada por capas                |
| Ideal para                       | PYMEs                | Empresas medianas y grandes, con más riesgo |

---

### 🔧 ¿Cómo se instala un UTM o NGFW?

#### ✅ Opción 1: Dispositivo físico (hardware)

Muchos fabricantes como **Fortinet (FortiGate), Sophos, WatchGuard, Cisco Meraki, Palo Alto** ofrecen equipos dedicados.

- **Se conecta entre el router y la red interna.**
- Viene con su propio sistema operativo.
- Se configura vía interfaz web o CLI.

#### ✅ Opción 2: Solución virtual (software/appliance)

Hay versiones de UTM y NGFW que puedes **instalar como software en una máquina virtual** o servidor.

Ejemplos:

- **pfSense** (con plugins UTM)
- **OPNsense**
- **Sophos XG Firewall Home Edition**
- **FortiGate VM**
- **Cisco Firepower (NGFW)**

---

### 🛠️ Ejemplo de instalación y configuración: **pfSense como UTM**

#### 🎯 Objetivo:

Instalar pfSense como UTM para proteger una red interna con funciones básicas de firewall, IDS/IPS, y VPN.

---

#### 🔧 Requisitos:

- Una máquina virtual (VMware, VirtualBox) o equipo físico
- ISO de pfSense (desde [https://www.pfsense.org/download/](https://www.pfsense.org/download/))

---

#### 📦 Instalación paso a paso:

##### 1. Descarga e instala pfSense

- Monta el ISO en la VM
- Sigue los pasos del instalador (tipo "Next → Next")
- Asigna 2 interfaces:

  - **WAN** (conectado a Internet)
  - **LAN** (conectado a tu red privada o adaptador puente)

##### 2. Accede vía navegador

Conéctate desde un navegador a:
`https://192.168.1.1`
Usuario: `admin`
Contraseña: `pfsense`

---

#### 🔒 Configura funciones básicas

##### ➤ Firewall

- Ve a **Firewall > Rules**
- Crea reglas para permitir o bloquear tráfico entre LAN y WAN

##### ➤ IDS/IPS (Snort o Suricata)

1. Instala desde **System > Package Manager**
2. Configura desde **Services > Snort**
3. Elige la interfaz (WAN o LAN)
4. Activa reglas de detección

##### ➤ VPN (opcional)

- Ve a **VPN > OpenVPN** para crear un servidor VPN
- Exporta el cliente con "client export utility"

---

### 🧪 Ejemplo final: Bloquear acceso a YouTube con NGFW

#### 🔧 Con Sophos XG Home Edition (NGFW gratuito)

1. Instálalo en una máquina virtual (descargado desde Sophos)
2. Accede al panel web
3. Crea una **regla de filtrado web**

   - Categoría: "Streaming Media"
   - Acción: "Block"

4. Aplica a los usuarios o IPs de la red

🔍 Resultado: Todos los usuarios que accedan a YouTube serán bloqueados por inspección de capa 7 (aplicación), **incluso si usan HTTPS**.

---

### 📌 Resumen

| Tema                            | UTM                             | NGFW                                  |
| ------------------------------- | ------------------------------- | ------------------------------------- |
| ¿Qué es?                        | Cortafuegos todo en uno         | Firewall avanzado con capa aplicación |
| ¿Qué incluye?                   | Firewall, VPN, IDS, antivirus   | + control de aplicaciones, DPI        |
| ¿Dónde se usa?                  | Empresas pequeñas y medianas    | Empresas medianas y grandes           |
| ¿Se puede instalar en software? | Sí (pfSense, Sophos, FortiGate) | Sí (Sophos XG, Cisco Firepower)       |

---

[🔼](#índice)

---

## **801. Protocolos seguros en redes de datos**

### 🔐 ¿Qué son los protocolos seguros en redes de datos?

Los **protocolos seguros** son **reglas y estándares** usados para **proteger la información** que se transmite por una red (como Internet o una red interna). Su objetivo es garantizar:

- **Confidencialidad** (la información no puede ser leída por terceros).
- **Integridad** (la información no fue alterada).
- **Autenticación** (verificar quién envía y recibe).
- **No repudio** (garantizar que una acción ocurrió y no puede negarse).

---

### 🔐 Protocolos seguros más comunes (con ejemplos fáciles):

| Protocolo                | ¿Para qué sirve?                               | Ejemplo de uso fácil                             |
| ------------------------ | ---------------------------------------------- | ------------------------------------------------ |
| **HTTPS**                | Navegación web segura                          | Acceder a [https://banco.com](https://banco.com) |
| **SSH**                  | Acceso remoto seguro a servidores              | Conectarte a una VPS por consola                 |
| **SFTP**                 | Transferencia segura de archivos               | Subir archivos a un servidor por FileZilla       |
| **IPSec**                | Capa de red segura (usado en VPNs)             | Conexión entre dos oficinas                      |
| **TLS/SSL**              | Cifrado de datos (usado por HTTPS, SMTP, etc.) | Enviar correos cifrados o chats seguros          |
| **WPA3**                 | Seguridad para redes WiFi modernas             | WiFi con contraseña fuerte y cifrado             |
| **DNS over HTTPS (DoH)** | Protege tus consultas de dominio               | Usado por navegadores modernos como Firefox      |

---

### ✅ ¿Por qué son importantes?

Imagina que envías tu contraseña por una red **sin cifrado** (por ejemplo, HTTP). Cualquiera que intercepte el tráfico puede verla.
Usar protocolos **seguros** asegura que esa contraseña esté **cifrada**, **verificada** y **protegida contra manipulación**.

---

### ⚙️ ¿Cómo se "instalan" o configuran?

No se instalan como una app cualquiera, pero sí se **configuran en sistemas, servidores o dispositivos** de red. Aquí van ejemplos clave.

---

#### 🔹 1. HTTPS en un sitio web (con Let's Encrypt)

- El servidor web (como Apache o Nginx) usa un **certificado SSL/TLS**.
- Puedes instalar uno **gratuito** con Let's Encrypt:

```bash
sudo apt install certbot python3-certbot-nginx
sudo certbot --nginx
```

Eso activa **HTTPS seguro** en tu sitio.

---

#### 🔹 2. SSH en un servidor Linux

```bash
sudo apt install openssh-server
sudo systemctl enable ssh
sudo systemctl start ssh
```

Con eso, puedes conectarte remotamente con:

```bash
ssh usuario@IP_SERVIDOR
```

Y toda la comunicación será **cifrada y autenticada**.

---

#### 🔹 3. SFTP (usando SSH)

SFTP viene incluido con SSH. Si tienes acceso por SSH, también puedes transferir archivos de forma segura:

```bash
sftp usuario@IP_SERVIDOR
```

O usa FileZilla seleccionando **SFTP** en el protocolo.

---

#### 🔹 4. VPN con IPsec

Puedes usar herramientas como **strongSwan** (Linux) para crear una VPN IPsec:

```bash
sudo apt install strongswan
```

Luego configuras los archivos `/etc/ipsec.conf` y `/etc/ipsec.secrets` para establecer la conexión segura.

---

### 🔒 Ejemplo completo: Configuración de HTTPS con Let's Encrypt en Nginx

#### 🎯 Objetivo:

Tener un sitio web que funcione con **HTTPS cifrado**, usando un certificado gratuito de Let's Encrypt.

#### 🧰 Requisitos:

- Un servidor Linux (por ejemplo, Ubuntu)
- Un dominio apuntando al servidor (ej: `midominio.com`)
- Tener Nginx instalado

---

#### 🛠️ Paso a paso:

##### 1. Instalar Nginx

```bash
sudo apt update
sudo apt install nginx
```

##### 2. Comprobar que funcione

Abre tu navegador y accede a `http://TU_DOMINIO.com`.

##### 3. Instalar Certbot (cliente Let's Encrypt)

```bash
sudo apt install certbot python3-certbot-nginx
```

##### 4. Ejecutar Certbot

```bash
sudo certbot --nginx
```

Te pedirá:

- El dominio que quieres asegurar
- Un correo electrónico
- Si redirigir tráfico HTTP a HTTPS (elige SÍ)

---

#### ✅ Resultado

Ahora tu sitio web funcionará en:

```
https://midominio.com
```

🔒 El navegador mostrará un candado indicando que la conexión es segura.

---

### 📌 Resumen final

| Protocolo seguro | Capa       | Protege contra...              | Ejemplo de uso             |
| ---------------- | ---------- | ------------------------------ | -------------------------- |
| HTTPS            | Aplicación | Espionaje web, MITM            | Webs seguras               |
| SSH              | Transporte | Robo de contraseñas remotas    | Admin remota de servidores |
| TLS              | Transporte | Interceptación de datos        | Email, chat, APIs          |
| SFTP             | Aplicación | Intercepción al subir archivos | FTP seguro                 |
| IPSec            | Red        | Interceptar/redirigir tráfico  | VPNs de sitio a sitio      |

---

[🔼](#índice)

---

## **802. Control de acceso a red - NAC**

### ✅ ¿Qué es NAC?

**NAC (Network Access Control)** es una tecnología de seguridad que **controla quién o qué puede conectarse a una red**, asegurándose de que cumplan con las políticas de seguridad antes de permitir el acceso.

> 🧠 Piensa en NAC como un **guardia de seguridad digital** en la entrada de tu red. Si un dispositivo no cumple con las normas (por ejemplo, sin antivirus o desactualizado), **no entra** o entra con restricciones.

---

### 🧭 ¿Para qué sirve NAC?

- ✅ Evitar que dispositivos no autorizados accedan a la red.
- 🧪 Verificar si un dispositivo cumple con requisitos (antivirus activo, sistema actualizado, etc.).
- 📡 Distinguir entre invitados, empleados y dispositivos de IoT.
- 🔒 Segmentar la red según el nivel de confianza del dispositivo.

---

### 🧑‍🏫 Ejemplo sencillo:

| Dispositivo                      | ¿Cumple requisitos? | Acceso que recibe     |
| -------------------------------- | ------------------- | --------------------- |
| Laptop con antivirus actualizado | ✅ Sí               | Acceso total          |
| Celular personal                 | ❓ No verificado    | Solo red de invitados |
| PC desactualizada sin parches    | ❌ No               | Bloqueado             |

---

### 🧱 ¿Cómo funciona NAC?

1. **Descubrimiento del dispositivo**: detecta quién intenta conectarse.
2. **Autenticación**: verifica identidad (usuario, certificado, etc.).
3. **Evaluación de cumplimiento**: revisa si el dispositivo tiene antivirus, parches, etc.
4. **Aplicación de políticas**: permite, limita o bloquea el acceso.
5. **Remediación** (opcional): da la opción de corregir el problema para obtener acceso.

---

### 🔧 ¿Cómo se implementa NAC?

Existen dos formas comunes:

#### 🔹 Basado en Switches / Infraestructura

- Usando protocolos como **802.1X** (autenticación a nivel de puerto de switch).
- Requiere switches gestionables, servidor RADIUS, y configuración compleja.
- Ejemplo: Cisco ISE, Aruba ClearPass.

#### 🔹 Basado en Agente / Software

- Usando software que se instala en los dispositivos.
- El software comunica al NAC si el dispositivo es seguro o no.
- Ejemplo: FortiNAC, PacketFence.

---

### 💡 Soluciones NAC populares

| Herramienta     | Tipo      | Plataforma      |
| --------------- | --------- | --------------- |
| Cisco ISE       | Comercial | Infraestructura |
| Aruba ClearPass | Comercial | Infraestructura |
| **PacketFence** | **Libre** | Software        |
| FortiNAC        | Comercial | Infraestructura |
| Sophos NAC      | Comercial | Software        |

---

### 💻 ¿Cómo se instala PacketFence (ejemplo libre y gratuito)?

Vamos a instalar **PacketFence**, una solución NAC de código abierto muy potente.

#### 🧰 Requisitos:

- Sistema: CentOS 7 o Rocky Linux 8
- 2 CPU, 4 GB de RAM mínimo
- Acceso root o sudo

---

#### 🛠️ Paso a paso (instalación en Rocky Linux 8)

##### 1. Instalar dependencias:

```bash
sudo dnf update -y
sudo dnf install epel-release -y
```

##### 2. Descargar e instalar PacketFence:

```bash
sudo dnf install https://packetfence.org/downloads/PacketFence-el8.repo -y
sudo dnf install packetfence -y
```

##### 3. Iniciar PacketFence:

```bash
sudo systemctl enable packetfence
sudo systemctl start packetfence
```

##### 4. Acceder a la interfaz web:

Abre tu navegador y ve a:

```
https://IP_DEL_SERVIDOR:1443
```

Usuario: `admin`
Contraseña: establecida durante la instalación

---

#### ⚙️ Configurar política básica

1. Crea una **regla de acceso**:

   - Si el dispositivo es confiable → acceso total
   - Si no → red de cuarentena

2. Crea una **red de cuarentena VLAN**.

3. Agrega **autenticación por certificado o contraseña**.

4. Prueba desde un cliente (ej: laptop) conectándose al switch.

---

### 🔚 Ejemplo completo: Control de acceso con PacketFence

🎯 **Objetivo:** Permitir solo laptops con antivirus activo y Windows actualizado.

#### ✅ Flujo:

1. Usuario conecta su laptop a la red.
2. PacketFence escanea el dispositivo:

   - Si tiene antivirus y parches → accede a VLAN 10 (red interna).
   - Si no → redirige a portal de remediación (VLAN 20).

3. Usuario corrige problemas y vuelve a conectar → acceso concedido.

---

### 🧠 Conclusión

| Ventaja del NAC                          | Ejemplo claro                        |
| ---------------------------------------- | ------------------------------------ |
| Control total de quién entra a la red    | Solo PCs con políticas de seguridad  |
| Reducción de riesgos                     | Dispositivos inseguros se aíslan     |
| Visibilidad sobre todos los dispositivos | Saber qué se conecta en todo momento |

---

[🔼](#índice)

---

| **Inicio**         | **atrás 9**                                        | **Siguiente 11**                   |
| ------------------ | -------------------------------------------------- | ---------------------------------- |
| [🏠](../README.md) | [⏪](./7_9_Curso_de_Introduccion_al_Pentesting.md) | [⏩](./7_11_Pentesting_a_Redes.md) |
