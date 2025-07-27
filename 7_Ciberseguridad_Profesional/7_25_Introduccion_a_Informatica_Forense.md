| **Inicio**         | **atrás 24**                                                | **Siguiente 26**                                   |
| ------------------ | ----------------------------------------------------------- | -------------------------------------------------- |
| [🏠](../README.md) | [⏪](./7_24_Seguridad_Informatica_para_Equipos_Tecnicos.md) | [⏩](./7_26_Ciberseguridad_para_Desarrollo_Web.md) |

---

## **Índice**

| Temario                                                                                                                          |
| -------------------------------------------------------------------------------------------------------------------------------- |
| [1133. Qué es Informática Forense](#1133-qué-es-informática-forense)                                                             |
| [1134. dentificación de equipos](#1134-dentificación-de-equipos)                                                                 |
| [1135. Preservando la integridad de los datos](#1135-preservando-la-integridad-de-los-datos)                                     |
| [1136. Asignando identificadores hash](#1136-asignando-identificadores-hash)                                                     |
| [1137. Hardware para informática forense](#1137-hardware-para-informática-forense)                                               |
| [1138. Analizando la información obtenida](#1138-analizando-la-información-obtenida)                                             |
| [1139. Realizando una copia forense y un volcado de memoria RAM](#1139-realizando-una-copia-forense-y-un-volcado-de-memoria-ram) |
| [1140. Cómo presentar un informe forense](#1140-cómo-presentar-un-informe-forense)                                               |

# **Introducción a Informática Forense**

## **1133. Qué es Informática Forense**

### 🧠 ¿Qué es la Informática Forense?

La **informática forense**, también conocida como **forense digital**, es una **rama de la ciberseguridad** que se encarga de **investigar, identificar, recuperar y preservar evidencias digitales** cuando ocurre un delito o incidente relacionado con computadoras, redes o dispositivos electrónicos.

> 📌 Su objetivo es encontrar **la verdad digital** que pueda ser usada legalmente en una investigación o juicio.

---

### 🔍 ¿Qué hace exactamente la informática forense?

1. **Recupera información** eliminada o dañada (archivos, correos, logs).
2. **Analiza sistemas comprometidos** (virus, malware, accesos no autorizados).
3. **Identifica culpables** mediante rastreo de huellas digitales.
4. **Preserva la evidencia digital** sin alterarla, para que pueda ser usada legalmente.
5. **Genera informes técnicos** para abogados, jueces o empresas.

---

### 📦 Ejemplos fáciles de entender

#### 🔓 Ejemplo 1: Robo de archivos internos

Un empleado roba información confidencial y la elimina del servidor.

- La informática forense:

  - Recupera los archivos borrados.
  - Detecta la cuenta que accedió a ellos.
  - Extrae los registros del sistema (logs).
  - Presenta evidencia del delito.

---

#### 💻 Ejemplo 2: Ciberataque a una empresa

Una empresa fue atacada por un hacker que dejó un ransomware.

- El forense digital:

  - Analiza cómo entró el atacante (phishing, puerto abierto, etc.).
  - Revisa si hay puertas traseras.
  - Estudia qué archivos fueron cifrados.
  - Identifica dirección IP del atacante o herramientas usadas.

---

### 🧰 ¿Cómo se “instala” o se aplica la informática forense?

En este contexto, **"instalar"** significa cómo se **implementa** o cómo se **prepara** un entorno de informática forense.

#### 🧱 Requisitos básicos:

1. **Herramientas de software especializadas**:

   - 💽 FTK (Forensic Toolkit)
   - 🐧 Autopsy / Sleuth Kit (Linux/Windows)
   - 🐘 Volatility (análisis de memoria RAM)
   - 📁 EnCase (comercial)
   - 🐍 Wireshark (análisis de red)

2. **Equipos dedicados**:

   - PC con alto rendimiento y discos duros grandes.
   - Discos para clonar evidencias (copias forenses).

3. **Protocolos legales y técnicos**:

   - Cadena de custodia.
   - Documentación detallada.
   - Evitar alterar los datos originales.

---

#### 📥 Cómo se aplica paso a paso:

| Paso                      | Descripción                                                             |
| ------------------------- | ----------------------------------------------------------------------- |
| 1. **Asegurar la escena** | Desconectar el equipo afectado sin apagarlo si es necesario (para RAM). |
| 2. **Clonar el disco**    | Hacer una copia exacta del disco afectado (bit a bit).                  |
| 3. **Análisis forense**   | Usar software para examinar logs, archivos, procesos, redes, RAM, etc.  |
| 4. **Documentar**         | Registrar todo el proceso sin alterar el original.                      |
| 5. **Informe final**      | Redactar hallazgos con lenguaje técnico y legal.                        |

---

### 📘 Ejemplo completo paso a paso

#### 🎯 Caso: Un trabajador filtró datos confidenciales a la competencia

##### 🖥️ Escenario:

La empresa "TecnoData" descubre que su software interno fue filtrado a una empresa rival. Sospechan de un exempleado.

---

#### 🔍 Paso 1: Asegurar la evidencia

- El disco duro del exempleado es incautado.
- Se evita encender el equipo para no alterar evidencia.

---

#### 💽 Paso 2: Clonación

- Se usa la herramienta **FTK Imager** para clonar el disco duro.
- Se trabaja sobre la copia, no sobre el disco original.

---

#### 🧪 Paso 3: Análisis

- Con **Autopsy**, el perito detecta:

  - Archivos comprimidos recientemente.
  - Acceso a un servicio de transferencia de archivos (WeTransfer).
  - Archivos borrados que fueron recuperados.
  - Un log de conexión USB a las 3:00 a. m. (unidad externa).

---

#### 🧾 Paso 4: Documentación

- Se registra:

  - Qué herramientas se usaron.
  - Hash MD5/SHA1 del disco original y la copia.
  - Hora y fecha de cada paso.

---

#### 📑 Paso 5: Informe técnico

> El informe indica:

- El exempleado usó una USB a escondidas.
- Copió carpetas confidenciales.
- Usó una red privada para enviar los archivos.

---

### 📌 Conclusión

| Elemento                   | Explicación resumida                                               |
| -------------------------- | ------------------------------------------------------------------ |
| ¿Qué es?                   | Investigación de evidencia digital ante incidentes o delitos       |
| ¿Para qué sirve?           | Recuperar datos, identificar atacantes, presentar evidencia        |
| ¿Cómo se aplica?           | Mediante herramientas, protocolos y análisis forense técnico-legal |
| ¿Qué herramientas se usan? | FTK, Autopsy, EnCase, Volatility, Wireshark, etc.                  |
| ¿Dónde se aplica?          | Empresas, gobierno, justicia, defensa, bancos, hospitales, etc.    |

---

[🔼](#índice)

---

## **1134. dentificación de equipos**

### 🧠 ¿Qué es la Identificación de Equipos?

La **identificación de equipos** es el proceso de **reconocer, registrar y gestionar todos los dispositivos** (computadoras, servidores, routers, celulares, etc.) que están conectados a una red o que pertenecen a una organización.

> 📌 Esto es esencial en ciberseguridad porque **no puedes proteger lo que no sabes que existe**.

---

### 🛠️ ¿Por qué es importante?

1. 🕵️‍♂️ Detectar dispositivos desconocidos (que podrían ser maliciosos).
2. 📋 Controlar y gestionar activos tecnológicos.
3. 🔐 Aplicar políticas de seguridad (por ejemplo, limitar dispositivos personales).
4. ⚠️ Prevenir accesos no autorizados o intrusos en la red.
5. 📊 Tener un inventario actualizado para auditorías, control de licencias y análisis de riesgos.

---

### 📱 Ejemplos fáciles de entender

#### ✅ Ejemplo 1: Oficina pequeña

En una oficina hay:

- 5 laptops,
- 2 impresoras en red,
- 1 router,
- 1 servidor,
- y un celular personal conectado al Wi-Fi.

> El área de sistemas realiza una **identificación de equipos** para saber qué está conectado, quién lo usa, y si es un equipo autorizado.

---

#### 🚫 Ejemplo 2: Dispositivo desconocido

En una red empresarial aparece un **dispositivo nuevo no registrado** con actividad inusual. Al identificarlo, descubren que es una **Raspberry Pi conectada por un visitante**, lo cual viola las normas de seguridad.

---

### 🧰 ¿Cómo se realiza o se "instala"?

Aquí “instalar” se refiere a aplicar procesos y herramientas para identificar equipos dentro de una red o sistema.

---

#### 🧾 Formas comunes de identificar equipos:

| Método                    | ¿Qué hace?                                                                     |
| ------------------------- | ------------------------------------------------------------------------------ |
| 📡 Escaneo de red         | Detecta dispositivos activos conectados a la red (ping, ARP, SNMP).            |
| 🧠 Inventario manual      | Registro físico o en Excel con número de serie, nombre, usuario, etc.          |
| 💻 Software de inventario | Automatiza el proceso: detecta, registra, clasifica y actualiza dispositivos.  |
| 🎛️ Control de accesos NAC | Solo permite conexión de dispositivos autorizados mediante MAC o certificados. |

---

#### 🔧 Herramientas útiles

1. **Angry IP Scanner** (Windows/Linux/Mac) – Escanea redes rápidamente.
2. **Nmap** – Escaneo profundo de red (puertos, sistemas operativos, etc.).
3. **GLPI o OCS Inventory** – Gestión de activos de TI (gratis).
4. **Advanced IP Scanner** – Escaneo rápido en entornos Windows.
5. **Netdiscover** – En Linux, para escanear IPs y MACs.

---

### 🖥️ Ejemplo completo paso a paso

#### 🎯 Objetivo: Identificar los equipos conectados a la red Wi-Fi de tu casa

##### 🧪 Paso 1: Usar "Advanced IP Scanner" (Windows)

1. **Descargar**: Ve a [https://www.advanced-ip-scanner.com/es/](https://www.advanced-ip-scanner.com/es/) y descarga el programa.
2. **Instalar** y ejecutar.
3. **Escanear**: Dale clic en "Explorar" para que escanee tu red local.
4. **Resultado**:

   - Verás una lista de dispositivos: IP, nombre del equipo, MAC address, fabricante.
   - Puedes saber si es tu PC, tu celular, tu impresora o algo desconocido.

##### 📌 Paso 2: Registrar los equipos

- Anota en una tabla o Excel:

  - Nombre del equipo
  - Dirección IP
  - Dirección MAC
  - Usuario propietario
  - Sistema operativo

##### 🔐 Paso 3: Revisar anomalías

- Si hay un equipo que **no reconoces**, puedes:

  - Ver su fabricante (por la MAC).
  - Buscar la IP desde el router.
  - Bloquearlo desde la configuración del router.

---

#### 📊 Resultado

| IP          | Nombre del equipo | MAC Address         | Usuario     | Tipo de equipo              |
| ----------- | ----------------- | ------------------- | ----------- | --------------------------- |
| 192.168.0.2 | LAPTOP-GUS        | 44:1C\:A8:32\:DE:11 | Gustavo     | Laptop personal             |
| 192.168.0.5 | N/A               | 80:35\:C1\:FF:23:90 | Desconocido | ¿Dispositivo no autorizado? |

---

### ✅ Conclusión

| Punto               | Explicación                                                              |
| ------------------- | ------------------------------------------------------------------------ |
| ¿Qué es?            | Registro y monitoreo de todos los equipos conectados a la red            |
| ¿Para qué sirve?    | Proteger la red, evitar accesos no autorizados, tener control de activos |
| ¿Cómo se aplica?    | Con escaneos, software, control de acceso y listas de inventario         |
| Herramientas útiles | Nmap, Advanced IP Scanner, OCS Inventory, GLPI, Netdiscover              |

---

[🔼](#índice)

---

## **1135. Preservando la integridad de los datos**

### ✅ ¿Qué es la integridad de los datos?

La **integridad de los datos** significa que la información **se mantiene exacta, coherente y sin alteraciones no autorizadas** durante todo su ciclo de vida (desde que se crea hasta que se elimina).

---

### 🔎 ¿Por qué es importante?

Preservar la integridad garantiza que:

- Los datos **no han sido modificados accidental o maliciosamente**.
- Se puede **confiar en la información** almacenada.
- Las decisiones basadas en esos datos son correctas y seguras.

---

### 🧠 Ejemplo fácil de entender

Imagina que eres contador y tienes una hoja de cálculo con los sueldos del personal. Si alguien (por error o a propósito) cambia el sueldo de un trabajador sin que te des cuenta, entonces la **integridad del archivo fue comprometida**. Eso puede generar **errores financieros, sanciones o pérdida de confianza**.

---

### 🧰 ¿Cómo se preserva la integridad de los datos?

Existen **varias técnicas y herramientas**. Aquí te explico las más comunes:

---

#### 🔐 1. **Hashing (funciones hash)**

- Se genera una **huella digital única** de un archivo o mensaje (por ejemplo, con SHA-256).
- Si el archivo cambia aunque sea una letra, el hash cambia completamente.
- Se usa para **verificar que los datos no fueron alterados**.

🔧 Herramientas:

- `certutil` en Windows.
- `sha256sum` en Linux.

---

#### 🔐 2. **Control de acceso**

- Solo personas autorizadas pueden **ver o modificar** ciertos datos.
- Se aplican **permisos de lectura, escritura o ejecución**.

📍 Ejemplo:

- Un empleado puede ver su nómina, pero no modificarla.

---

#### 💾 3. **Registros de auditoría (logs)**

- Se guarda un historial de **quién accedió a qué datos, cuándo y qué hizo**.
- Si se detecta una modificación no autorizada, se puede rastrear.

---

#### 🧯 4. **Copias de seguridad (backups)**

- Se hacen regularmente para **restaurar datos originales** si hubo una alteración.
- Idealmente, se combinan con herramientas que **detectan cambios inesperados**.

---

#### 🧪 5. **Firmas digitales**

- Certifican que el documento **no ha sido modificado desde que fue firmado**.
- Se usa mucho en contratos, correos y facturas electrónicas.

---

### 📥 ¿Cómo se implementa en la práctica?

Aquí te doy un ejemplo técnico **sencillo de implementar** tanto en Windows como en Linux:

---

#### 🔧 **Windows – Verificar integridad de un archivo con `certutil`**

##### Paso 1: Generar el hash del archivo original

```cmd
certutil -hashfile documento.txt SHA256
```

Ejemplo de salida:

```
1F2A4E5C9A6F5E7F8E3A9C765FC123F0987765BB9C1D3B92F4E66709F5F12345
```

##### Paso 2: Guardar ese hash en un lugar seguro

##### Paso 3: Más adelante, volver a generar el hash

```cmd
certutil -hashfile documento.txt SHA256
```

✅ Si el hash **es el mismo**, **los datos no han cambiado**.

❌ Si el hash **es diferente**, alguien **modificó el archivo**.

---

#### 🐧 Linux – Usando `sha256sum`

```bash
sha256sum archivo.txt
```

Te devuelve una cadena hash. La puedes guardar en un archivo `.sha` y verificarla luego con:

```bash
sha256sum -c archivo.sha
```

---

### 📌 Ejemplo completo paso a paso: Preservando integridad con hashing + backup

#### Escenario:

Tienes un archivo importante `contrato.pdf` que **no debe ser modificado**.

---

##### 1️⃣ Paso 1: Genera el hash del archivo

**En Linux:**

```bash
sha256sum contrato.pdf > contrato.hash
```

**En Windows:**

```cmd
certutil -hashfile contrato.pdf SHA256
```

(Copia el resultado en un archivo de texto aparte)

---

##### 2️⃣ Paso 2: Crea una copia de seguridad del archivo original

- Guarda `contrato.pdf` en una carpeta segura (o en la nube cifrada).
- También guarda el `.hash`.

---

##### 3️⃣ Paso 3: Verifica en el futuro

Después de un mes, quieres asegurarte de que `contrato.pdf` **no fue modificado**:

```bash
sha256sum -c contrato.hash
```

Si dice:

```
contrato.pdf: OK
```

✅ Todo bien.

Si dice:

```
contrato.pdf: FAILED
```

❌ El archivo fue alterado. Deberías restaurar desde el backup.

---

### ✅ Conclusión

| Concepto                    | ¿Para qué sirve?                                                |
| --------------------------- | --------------------------------------------------------------- |
| **Integridad de los datos** | Garantizar que los datos no se han modificado sin autorización. |
| **Hashing**                 | Detectar cambios en archivos o datos.                           |
| **Control de acceso**       | Evitar que personas no autorizadas editen datos.                |
| **Logs**                    | Saber quién hizo qué y cuándo.                                  |
| **Backups**                 | Recuperar los datos originales si hubo una alteración.          |

---

[🔼](#índice)

---

## **1136. Asignando identificadores hash**

### ✅ ¿Qué es un identificador hash?

Un **identificador hash** es una cadena de texto alfanumérica generada por una **función hash** (como SHA-256) a partir de un dato (archivo, texto, contraseña, etc). Esta cadena **representa de forma única** el contenido original.

- Si los datos cambian, **el hash cambia completamente**.
- Dos archivos distintos **no deberían tener el mismo hash** (colisiones son muy raras si se usa una buena función hash).
- Se usa para **verificar integridad**, **almacenar contraseñas**, **identificar archivos** y **firmar digitalmente documentos**.

---

### 🔎 Ejemplo fácil de entender

Imagina que tienes una caja fuerte. Tú creas una contraseña secreta (por ejemplo, "gato123"). En lugar de guardar esa contraseña tal cual, generas su **hash**:

```
SHA-256("gato123") = a5f6c25d1d...
```

Esto significa que si alguien intenta entrar con "gato124", el hash será diferente y no funcionará.

✅ Así es como las páginas web **guardan contraseñas sin almacenar el texto original**, por seguridad.

---

### 🔐 ¿Para qué se usan los identificadores hash?

| Uso común                   | Ejemplo                                     |
| --------------------------- | ------------------------------------------- |
| Verificar integridad        | Confirmar que un archivo no fue modificado  |
| Almacenar contraseñas       | Guardar hash en vez de la contraseña real   |
| Identificar archivos únicos | Detectar duplicados, o reconocer versiones  |
| Firmas digitales            | Certificar que un documento no fue alterado |
| Blockchain y criptografía   | Validar bloques y transacciones             |

---

### 🛠️ ¿Cómo se instala un generador hash?

#### 📦 En **Windows** (ya viene incluido):

Puedes usar `certutil` desde la línea de comandos para calcular el hash de un archivo:

```cmd
certutil -hashfile archivo.txt SHA256
```

---

#### 🐧 En **Linux o WSL**:

Usa `sha256sum` (normalmente ya viene instalado). Si no lo tienes:

```bash
sudo apt update
sudo apt install coreutils
```

Luego ejecuta:

```bash
sha256sum archivo.txt
```

---

#### 💻 En **Python** (multiplataforma):

Puedes generar hashes de cualquier cadena o archivo usando el módulo `hashlib`.

```python
import hashlib

texto = "gato123"
hash = hashlib.sha256(texto.encode()).hexdigest()
print(hash)
```

---

### 📥 ¿Cómo se asigna un hash a un archivo?

Asignar un hash significa **generarlo y almacenarlo** para referencia futura. Puedes hacerlo manualmente o mediante un script automatizado.

---

#### ✅ Ejemplo completo paso a paso

#### 🎯 Objetivo: Verificar que un archivo PDF no fue modificado

##### 1️⃣ Tienes un archivo: `contrato.pdf`

##### 2️⃣ Genera su hash y guárdalo

**En Linux:**

```bash
sha256sum contrato.pdf > contrato.hash
```

**En Windows:**

```cmd
certutil -hashfile contrato.pdf SHA256 > contrato_hash.txt
```

Esto guarda el hash en un archivo. Ejemplo del contenido:

```
1a79a4d60de6718e8e5b326e338ae533 contrato.pdf
```

---

##### 3️⃣ Más adelante: Verifica que el archivo no fue modificado

**Linux:**

```bash
sha256sum -c contrato.hash
```

Si el archivo es idéntico, obtendrás:

```
contrato.pdf: OK
```

Si fue alterado:

```
contrato.pdf: FAILED
```

---

#### 🔄 Automatización (opcional)

Puedes crear un script que genere los hashes de todos los archivos de una carpeta:

**Linux - Bash Script:**

```bash
#!/bin/bash
for f in *.pdf; do
  sha256sum "$f" >> verificacion.hash
done
```

**Windows - Batch:**

```bat
@echo off
for %%f in (*.pdf) do (
  certutil -hashfile "%%f" SHA256 >> verificacion_hash.txt
)
```

---

### ✅ Resumen

| Concepto     | Explicación rápida                                         |
| ------------ | ---------------------------------------------------------- |
| Hash         | Huella digital única de un archivo o texto                 |
| Función hash | Algoritmo que transforma datos en una cadena (ej. SHA-256) |
| Asignar hash | Generar y guardar el hash de un archivo para verificarlo   |
| Verificación | Comparar hash guardado con uno nuevo para ver si cambió    |

---

[🔼](#índice)

---

## **1137. Hardware para informática forense**

### ✅ ¿Qué es el hardware en informática forense?

El **hardware para informática forense** son **equipos físicos especializados** usados para **adquirir, preservar, analizar y presentar evidencias digitales** de forma **segura y sin alterar los datos originales**.

No es cualquier computadora común. Este hardware debe garantizar que:

- No se modifiquen los datos (por ejemplo, bloqueando escritura).
- Se puedan extraer copias fieles de discos o memorias.
- Se trabaje rápidamente con grandes volúmenes de información.

---

### 🧰 Tipos de hardware usados en informática forense

| Tipo de hardware forense                  | ¿Qué hace?                                                          | Ejemplo fácil                                      |
| ----------------------------------------- | ------------------------------------------------------------------- | -------------------------------------------------- |
| 🔒 **Write Blockers**                     | Dispositivos que impiden que se escriba en el disco original        | Como un vidrio que permite mirar, pero no tocar    |
| 💽 **Duplicadores forenses**              | Copian sectores exactos de un disco a otro sin alterar nada         | Clonar un disco duro sector por sector             |
| 🧠 **Estaciones forenses (workstations)** | Computadoras con mucho poder y herramientas forenses instaladas     | Un laboratorio digital                             |
| 🔍 **Lectores de dispositivos**           | Lectoras de tarjetas SIM, memorias SD, USB, discos SATA, NVMe, etc. | Permiten examinar evidencias en distintos formatos |
| 📱 **Kits móviles forenses**              | Dispositivos para extraer datos de celulares sin desbloquearlos     | Extraer chats de WhatsApp sin abrir el teléfono    |
| 🧯 **Kits de emergencia**                 | Maletines con todos los dispositivos para hacer análisis en campo   | Como una caja de herramientas portátiles           |
| 🧲 **Imán/desmagnetizador**               | Destruye discos duros al desmagnetizarlos                           | Para eliminar pruebas de forma definitiva          |
| 🧪 **Dongles y llaves físicas**           | Llaves para acceder a software forense licenciado                   | Como un USB que activa el software forense         |

---

### 🔧 ¿Cómo se instala el hardware forense?

#### 1. **Write Blocker (bloqueador de escritura)**

🔹 **¿Cómo se conecta?**
Entre el disco original y la computadora forense:

```
[Disco original] ←→ [Write Blocker] ←→ [PC Forense]
```

🔹 **Instalación típica:**

- Conecta el write blocker por USB o SATA a tu estación de trabajo.
- Conecta el disco de evidencia al write blocker.
- El disco aparecerá en modo de solo lectura.

🔹 **Importante:** Antes de usar, debes verificar con software que el disco está realmente bloqueado contra escritura.

---

#### 2. **Duplicador forense**

🔹 Dispositivo físico con dos entradas:

```
[Fuente] → [Duplicador] → [Destino]
```

🔹 Se enciende, seleccionas el modo "bit a bit" o "clon forense", y empieza a copiar.

🔹 Muchos duplicadores modernos generan automáticamente:

- Un reporte con hash SHA-256 o MD5.
- Log de tiempo, errores y validación.

---

#### 3. **Estación forense (PC)**

Una estación forense es una PC de alto rendimiento con:

- CPU potente (i7/i9, Ryzen 9)
- Mínimo 32-64 GB de RAM
- Varios puertos USB 3.0, SATA, NVMe
- Software como Autopsy, FTK, EnCase, X-Ways
- UPS (respaldo eléctrico)

🔧 **Instalación:**

- Se conecta como cualquier PC.
- Debe mantenerse aislada de Internet para no contaminar las pruebas.
- Puede tener entornos virtuales o de arranque desde USB para distintos análisis.

---

### 📦 Ejemplo de marcas y dispositivos reales

| Categoría          | Ejemplo de producto                         | Marca                 |
| ------------------ | ------------------------------------------- | --------------------- |
| Write Blocker      | Tableau T356789iu Universal                 | Tableau (de OpenText) |
| Duplicador forense | Logicube Falcon Neo                         | Logicube              |
| Estación forense   | FRED (Forensic Recovery of Evidence Device) | Digital Intelligence  |
| Kit móvil forense  | UFED Touch 2                                | Cellebrite            |
| Software asociado  | FTK, EnCase, X-Ways                         | AccessData, OpenText  |

---

### 📄 Ejemplo completo paso a paso

#### 🎯 Escenario: Recuperar evidencia de un disco duro de una laptop

##### 1️⃣ Extraes el disco de la laptop sospechosa

##### 2️⃣ Lo conectas al **Write Blocker Tableau T356789iu**

- Se enciende un LED que indica "Modo solo lectura activo"

##### 3️⃣ Lo conectas a tu estación forense (por ejemplo, una FRED)

##### 4️⃣ Abres FTK Imager y haces lo siguiente:

- Crea una imagen forense del disco (`.E01`)
- Genera y guarda los hashes MD5 y SHA-1
- Verifica que la imagen coincida con el hash original

##### 5️⃣ Almacenas la imagen en un almacenamiento seguro (NAS, servidor forense, etc.)

##### 6️⃣ Trabajas con la **copia**, nunca con el disco original

---

### ✅ Resumen

| Punto clave        | Explicación sencilla                                |
| ------------------ | --------------------------------------------------- |
| Hardware forense   | Equipos físicos usados en análisis digital legal    |
| Write blocker      | Bloquea la escritura para preservar evidencia       |
| Duplicador forense | Copia exacta de discos sin modificar los datos      |
| Estación forense   | Computadora potente con herramientas especializadas |
| Instalación        | Fácil, pero requiere procedimientos cuidadosos      |

---

[🔼](#índice)

---

## **1138. Analizando la información obtenida**

### ✅ ¿Qué significa analizar la información obtenida?

En informática forense, **analizar la información obtenida** es el proceso en el cual el investigador revisa cuidadosamente todos los datos recuperados o extraídos de dispositivos digitales (computadoras, teléfonos, USB, etc.) para:

- **Buscar evidencia de un delito** (como acceso no autorizado, fraude, robo de datos, etc.)
- **Reconstruir lo que pasó** (quién, cuándo, cómo y desde dónde)
- **Detectar actividades sospechosas** (archivos eliminados, correos enviados, accesos remotos)

Este análisis **no debe modificar la evidencia original** y se hace siempre sobre una **copia forense** (imagen del disco, memoria RAM, etc.).

---

### 🧠 ¿Qué tipos de información se analizan?

| Tipo de información          | ¿Qué se busca?                                | Ejemplo fácil                              |
| ---------------------------- | --------------------------------------------- | ------------------------------------------ |
| Archivos                     | Archivos eliminados, ocultos, modificados     | Un informe borrado antes de una auditoría  |
| Registros del sistema (logs) | Actividad del usuario o del sistema operativo | A qué hora se encendió el equipo           |
| Navegador web                | Historial, cookies, contraseñas guardadas     | Acceso a páginas sospechosas               |
| Correos electrónicos         | Mensajes enviados/recibidos                   | Correos con amenazas o filtración de datos |
| Chats y redes                | WhatsApp, Telegram, Facebook, etc.            | Conversaciones con cómplices               |
| Actividad de red             | Conexiones a direcciones IP externas          | Acceso a servidores externos maliciosos    |
| Metadatos                    | Propiedades ocultas en documentos             | Quién creó un archivo y cuándo             |

---

### 🧰 Herramientas para analizar la información

Aquí algunos programas utilizados:

| Herramienta             | Función principal                        | Gratuita/Paga |
| ----------------------- | ---------------------------------------- | ------------- |
| 🔍 **Autopsy**          | Plataforma para análisis forense general | Gratuita      |
| 💻 **FTK Imager**       | Visualizar imágenes de disco             | Gratuita      |
| 🔎 **X-Ways Forensics** | Análisis forense detallado de sistemas   | Paga          |
| 📄 **PDFStreamDumper**  | Examinar PDFs maliciosos                 | Gratuita      |
| 📂 **Bulk Extractor**   | Extraer correos, URLs, contraseñas       | Gratuita      |
| 📶 **Wireshark**        | Analizar tráfico de red                  | Gratuita      |
| 💬 **Mobilyze**         | Analizar datos móviles                   | Paga          |

---

### 🛠️ ¿Cómo se “instala” o prepara el análisis?

No es instalar como un programa común. Implica preparar tu **entorno de análisis** con estos pasos:

---

#### 🔧 Pasos previos al análisis:

1. **Instala las herramientas en tu estación forense (offline):**

   - Ej. Autopsy, FTK Imager, Wireshark.

2. **Copia la imagen forense a tu estación:**

   - Desde un disco externo o red interna segura.

3. **Verifica la integridad con hash:**

   - Asegúrate de que el archivo no se haya modificado.

4. **Carga la imagen en la herramienta:**

   - Por ejemplo, en Autopsy puedes cargar un archivo `.E01` o `.dd`.

5. **Comienza el análisis sin modificar la fuente.**

---

### 🔎 ¿Qué se hace durante el análisis?

Una vez cargada la evidencia:

| Acción                   | ¿Qué se busca?                            |
| ------------------------ | ----------------------------------------- |
| Buscar palabras clave    | Ej. "contraseña", "hack", "banco", etc.   |
| Revisar cronología       | Ordenar eventos por fecha/hora            |
| Buscar archivos borrados | Herramientas los recuperan temporalmente  |
| Analizar navegación web  | Historial de Chrome, Firefox, etc.        |
| Revisar logs del sistema | Inicios de sesión, errores, acceso remoto |
| Detectar malware         | Archivos o procesos sospechosos           |
| Crear un informe         | Lo que se encontró, cómo y cuándo         |

---

### 📄 Ejemplo completo y sencillo

#### 🎯 Escenario:

Se sospecha que un empleado filtró documentos confidenciales desde su laptop.

##### 🔁 Paso a paso:

1. **Se obtiene la imagen forense del disco** con FTK Imager.
2. **Se abre en Autopsy** y se inicia un nuevo caso.
3. **Se busca la palabra clave:** `confidencial` o `reporte2025`.
4. **Autopsy muestra que:**

   - El archivo `reporte2025.pdf` fue enviado a través de una cuenta personal de Gmail.
   - El navegador tenía sesiones activas en servicios en la nube como Dropbox.

5. **Se revisa el historial de acceso:**

   - Se usó una USB justo antes de cerrar el documento.

6. **Se crea el informe del caso** en PDF con toda la evidencia recolectada.
7. **La imagen forense se almacena con su hash** para futuras revisiones legales.

---

### ✅ Recomendaciones clave

- Siempre trabajar sobre copias forenses.
- Verificar integridad antes y después del análisis.
- Documentar cada paso con fechas y herramientas usadas.
- Mantener el sistema forense **aislado de Internet** para evitar contaminación.

---

[🔼](#índice)

---

## **1139. Realizando una copia forense y un volcado de memoria RAM**

### ✅ ¿Qué es una copia forense?

Una **copia forense** es una **replica exacta (bit a bit)** de un medio digital (como un disco duro o una USB), hecha de manera que se **preserve la integridad** de los datos. Se usa en informática forense para analizar la evidencia sin alterar el original.

🔒 **Importancia:** Evita contaminar la evidencia y garantiza que se pueda presentar legalmente.

---

### ✅ ¿Qué es un volcado de memoria RAM?

La **RAM (memoria volátil)** almacena procesos activos, contraseñas, sesiones abiertas, datos temporales, etc. Un **volcado de RAM** (RAM dump) guarda su contenido en un archivo, permitiendo analizar:

- Programas en ejecución
- Contraseñas temporales
- Malware en memoria
- Conexiones abiertas

📌 **Nota:** La RAM se borra al apagar el equipo, así que se debe capturar **en caliente**, antes de apagarlo.

---

### 🛠️ Herramientas necesarias

| Herramienta                | Uso principal                    | Gratuita |
| -------------------------- | -------------------------------- | -------- |
| **FTK Imager**             | Hacer imágenes forenses          | ✅ Sí    |
| **Magnet RAM Capture**     | Capturar RAM de Windows          | ✅ Sí    |
| **Belkasoft RAM Capturer** | Capturar RAM con interfaz simple | ✅ Sí    |
| **Volatility**             | Analizar volcados de RAM         | ✅ Sí    |
| **dd (Linux)**             | Clonar discos                    | ✅ Sí    |

---

### 💻 Instalación de las herramientas (Windows)

#### 🔧 1. FTK Imager

1. Descárgalo desde el sitio oficial:

   [https://accessdata.com/product-download/ftk-imager](https://accessdata.com/product-download/ftk-imager)

2. Ejecuta el instalador (`FTK_Imager.exe`) y sigue los pasos.

3. Ábrelo como **administrador** para acceso total al disco.

---

#### 🔧 2. Magnet RAM Capture

1. Descárgalo desde:

   [https://www.magnetforensics.com/resources/magnet-ram-capture/](https://www.magnetforensics.com/resources/magnet-ram-capture/)

2. No requiere instalación. Es un `.exe` portable.

3. Ejecuta como administrador, elige la ruta de guardado del volcado (`.raw`) y haz clic en **"Start"**.

---

### 📄 Ejemplo completo paso a paso

---

#### 🎯 Escenario:

Eres parte de un equipo de respuesta a incidentes. Sospechas que hay un malware ejecutándose en la RAM de una laptop con Windows.

---

#### 👣 Paso 1: Capturar el volcado de RAM

**Herramienta:** Magnet RAM Capture

1. Inserta un USB con la herramienta Magnet RAM Capture.
2. Ábrelo como **Administrador** desde el USB.
3. Selecciona como destino el mismo USB (o un disco externo).
4. Haz clic en **"Start"**.
5. Se generará un archivo: `memory.raw`.

---

#### 👣 Paso 2: Hacer imagen forense del disco

**Herramienta:** FTK Imager

1. Abre FTK Imager.
2. Haz clic en **File > Create Disk Image**.
3. Selecciona **Physical Drive** y elige el disco de la laptop.
4. Elige el tipo de imagen: `E01` (formato forense estándar).
5. Indica la ruta para guardar la imagen (otro disco externo).
6. Opcional: Marca la casilla para calcular **hash MD5/SHA1**.
7. Haz clic en **Start** y espera a que termine.

Resultado:

- Una imagen forense: `evidencia.E01`
- Un volcado de memoria: `memory.raw`
- Un archivo de hashes: `hash.txt`

---

#### 👣 Paso 3: Analizar el volcado de RAM

**Herramienta:** Volatility (requiere Python)

1. Descarga Volatility:

   [https://github.com/volatilityfoundation/volatility](https://github.com/volatilityfoundation/volatility)

2. Instala Python y Volatility:

   ```bash
   pip install volatility
   ```

3. Analiza el volcado:

   ```bash
   volatility -f memory.raw --profile=Win10x64_18362 pslist
   ```

   Esto mostrará una lista de procesos activos en la memoria. Puedes buscar malware, procesos extraños o conexiones activas con:

   ```bash
   volatility -f memory.raw --profile=Win10x64_18362 netscan
   ```

---

### ✅ Buenas prácticas

- Siempre trabajar sobre copias, no sobre el disco original.
- Usar herramientas desde USB o CD (modo portable).
- Guardar los **hashes MD5/SHA1** para verificar que no se alteró nada.
- Documentar fecha, hora, quién hizo la captura, en qué equipo, etc.

---

### 📌 Resumen del flujo

```
[1] Detectar incidente sospechoso
      ↓
[2] Capturar la RAM (Magnet RAM Capture)
      ↓
[3] Crear imagen del disco (FTK Imager)
      ↓
[4] Analizar RAM (Volatility)
      ↓
[5] Analizar imagen del disco (Autopsy/FTK)
```

---

[🔼](#índice)

---

## **1140. Cómo presentar un informe forense**

### 🔍 ¿Qué es un informe forense?

Un **informe forense digital** es un **documento técnico y legal** donde se detallan todas las actividades realizadas durante una investigación forense, incluyendo:

- Evidencias recolectadas
- Herramientas utilizadas
- Metodología aplicada
- Resultados obtenidos
- Conclusiones y recomendaciones

Este informe puede ser presentado ante autoridades, abogados, empresas o peritos, así que debe ser **claro, objetivo, bien organizado y verificable**.

---

### 📌 ¿Por qué es importante?

- **Respalda legalmente el análisis realizado**
- **Documenta cada paso para auditorías**
- **Evita manipulación o dudas sobre las pruebas**
- Sirve como **evidencia en juicios** o despidos laborales

---

### 🧱 Estructura típica del informe forense

| Sección                  | Contenido breve                                                      |
| ------------------------ | -------------------------------------------------------------------- |
| 1. Portada               | Título, fecha, autor, organización                                   |
| 2. Tabla de contenido    | Ítems con números de página                                          |
| 3. Introducción          | Qué pasó, quién pidió el informe, qué se buscaba                     |
| 4. Alcance               | Qué sistemas se analizaron, qué quedó fuera                          |
| 5. Metodología           | Pasos seguidos, herramientas usadas                                  |
| 6. Evidencia recolectada | Hashes, discos, logs, volcados de memoria                            |
| 7. Análisis              | Lo encontrado: malware, usuarios, IPs, puertos, archivos sospechosos |
| 8. Conclusión            | Qué se determinó, resumen del incidente                              |
| 9. Recomendaciones       | Cómo evitar que vuelva a ocurrir                                     |
| 10. Anexos               | Logs, capturas de pantalla, hash, archivos .E01 o .RAW               |

---

### 🛠️ Herramientas para redactarlo

Puedes usar:

- 📝 **Microsoft Word o Google Docs**
- 📄 **Markdown + Pandoc (para PDF profesional)**
- 🖼️ Capturas con Snipping Tool, Flameshot o ShareX
- 📁 Evidencias en carpetas con hashes generados (usando `md5sum` o `sha256sum`)

---

### ✅ Buenas prácticas

- Escribir en **lenguaje claro y técnico**
- Incluir **fechas, horas y firmas digitales**
- Documentar **paso por paso lo hecho**
- Agregar **hashes** de las evidencias (MD5, SHA1)
- Evitar opiniones personales: solo hechos y conclusiones objetivas

---

### 📄 Ejemplo completo: Informe Forense de un ataque por USB infectado

---

#### 🧾 1. Portada

```
INFORME FORENSE DIGITAL
Investigación sobre posible infección por dispositivo USB
Fecha: 27/07/2025
Autor: Gustavo Puma
Organización: CyberDefensa SAC
```

---

#### 📚 2. Tabla de contenido

```
1. Introducción........................... 1
2. Alcance............................... 2
3. Metodología........................... 2
4. Evidencia recolectada................ 3
5. Análisis.............................. 4
6. Conclusión............................ 6
7. Recomendaciones....................... 7
8. Anexos................................ 8
```

---

#### 🧩 3. Introducción

> Se solicitó un análisis forense del equipo **PC-LAB003** de un laboratorio educativo, ya que el antivirus reportó una posible amenaza después de insertar un USB desconocido el día 25/07/2025.

---

#### 🧭 4. Alcance

> Se analizó únicamente el equipo PC-LAB003, específicamente su disco duro y memoria RAM. No se consideraron otros dispositivos de red ni USBs relacionados.

---

#### 🧰 5. Metodología

- Captura de imagen forense del disco con **FTK Imager**
- Captura de volcado de RAM con **Magnet RAM Capture**
- Verificación de integridad mediante **hashes SHA-256**
- Análisis de RAM usando **Volatility Framework**
- Escaneo del disco con **Autopsy**

---

#### 💽 6. Evidencia recolectada

| Nombre del archivo | Tipo           | Hash SHA-256          |
| ------------------ | -------------- | --------------------- |
| memoria.raw        | Volcado de RAM | `e3b0c44298fc1c14...` |
| disco.E01          | Imagen forense | `3a0d12aa7f41dfbc...` |

Se almacenaron en una carpeta segura en disco externo cifrado.

---

#### 🔎 7. Análisis

- El proceso `usbscan.exe` se ejecutó a las **15:03 h**, 1 minuto después de conectar el USB.
- El malware copió archivos `*.docx` al USB y lo ocultó con atributos `system/hidden`.
- El malware usó `powershell.exe` para descargar scripts desde IPs rusas: `185.XX.XX.23`.
- Se hallaron 2 conexiones abiertas a puertos 443 y 8080 desde procesos desconocidos.
- Se halló persistencia en `HKLM\Software\Microsoft\Windows\Run\usb_loader`.

---

#### ✅ 8. Conclusión

> El equipo fue infectado por un malware contenido en un USB que, al conectarse, se ejecutó automáticamente y comenzó a exfiltrar documentos de Word del usuario. Se confirma el incidente.

---

#### 🛡️ 9. Recomendaciones

- Implementar políticas de **bloqueo de puertos USB**
- Activar **protección contra ejecución automática (autorun.inf)**
- Capacitar al personal sobre el **riesgo de conectar dispositivos no autorizados**
- Aislar y formatear el equipo afectado

---

#### 📎 10. Anexos

- Captura de Volatility con `pslist` y `netscan`
- Logs exportados de Autopsy
- Archivo comprimido con `memory.raw` y `disco.E01`
- Hashes SHA256 generados con `sha256sum`

---

### 🎁 Resultado final

Un archivo PDF o DOCX bien estructurado, con texto técnico pero claro, evidencia bien organizada, y todo lo necesario para **proteger legalmente** tu análisis.

---

[🔼](#índice)

---

| **Inicio**         | **atrás 24**                                                | **Siguiente 26**                                   |
| ------------------ | ----------------------------------------------------------- | -------------------------------------------------- |
| [🏠](../README.md) | [⏪](./7_24_Seguridad_Informatica_para_Equipos_Tecnicos.md) | [⏩](./7_26_Ciberseguridad_para_Desarrollo_Web.md) |
