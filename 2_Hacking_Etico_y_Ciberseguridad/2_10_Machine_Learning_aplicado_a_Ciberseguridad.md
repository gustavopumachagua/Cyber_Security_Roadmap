| **Inicio**         | **atrás 9**                                 |
| ------------------ | ------------------------------------------- |
| [🏠](../README.md) | [⏪](./2_9_Tecnicas_de_Post_Explotacion.md) |

---

## **Índice**

| Temario                                                                                   |
| ----------------------------------------------------------------------------------------- |
| [95. BATEA: Reconocimiento de hosts con ML](#95-batea-reconocimiento-de-hosts-con-ml)     |
| [96. Pesidious: Mutaciones con Deep Learning](#96-pesidious-mutaciones-con-deep-learning) |
| [97. Ingeniería Social - Deep fake](#97-ingeniería-social---deep-fake)                    |

---

# **Machine Learning aplicado a Ciberseguridad**

## **95. BATEA: Reconocimiento de hosts con ML**

### 📌 ¿Qué es BATEA?

**BATEA** (Behavioral Analysis Tools for Enterprise Assessments) es una herramienta de **reconocimiento de hosts basada en machine learning**, diseñada para identificar **los activos más interesantes en una red corporativa**, por ejemplo:

- Controladores de dominio.
- Servidores críticos.
- Equipos de administración.

Utiliza modelos de **aprendizaje automático** para **priorizar objetivos** durante un reconocimiento pasivo, analizando datos de red como:

- Nombre del host.
- TTL.
- Intervalos de respuesta.
- Campos NetBIOS/SMB.
- Tipos de servicios detectados.

---

### 🧠 ¿Por qué es útil?

En lugar de simplemente listar IPs y puertos abiertos (como haría Nmap), BATEA aplica **ML para adivinar qué host es el más importante**, facilitando ataques dirigidos.

---

### 🧪 EJEMPLO PRÁCTICO EN MÁQUINAS VIRTUALES

#### 🖥️ Requisitos:

| Máquina              | Rol        | Sistema Operativo |
| -------------------- | ---------- | ----------------- |
| Kali Linux           | Atacante   | Kali              |
| Windows 10           | Víctima    | Windows 10 Pro    |
| (Opcional) WinServer | DC víctima | Windows Server    |

Todas las máquinas deben estar en **la misma red (modo puente o red interna)** para que el reconocimiento funcione correctamente.

---

#### ⚙️ INSTALACIÓN DE BATEA EN KALI LINUX

1. **Actualizar e instalar dependencias**:

```bash
sudo apt update && sudo apt install -y python3-pip nmap git
```

2. **Clonar el repositorio oficial**:

```bash
git clone https://github.com/josephkingstone/batea.git
cd batea
```

3. **Instalar los requerimientos de Python**:

```bash
pip3 install -r requirements.txt
```

¡Listo! Ya tienes BATEA instalado.

---

### 🚀 CÓMO FUNCIONA BATEA

#### 1. Realiza un escaneo Nmap (o usa uno existente):

```bash
nmap -sS -sU -A -T4 192.168.100.0/24 -oX red_scan.xml
```

Esto escaneará toda la red y guardará el resultado en formato XML.

#### 2. Ejecutar BATEA sobre ese escaneo:

```bash
python3 batea.py red_scan.xml
```

#### 3. Resultado:

Obtendrás una **lista ordenada** de hosts, indicando:

- Hostname.
- Probabilidad de ser un servidor importante.
- Puertos detectados.
- Probabilidades generadas por ML.

---

### 📊 ¿Qué hace BATEA diferente?

| Herramienta | Salida básica                     | Prioriza objetivos importantes |
| ----------- | --------------------------------- | ------------------------------ |
| Nmap        | Puertos y servicios               | ❌                             |
| BATEA       | Usa datos + ML para clasificación | ✅                             |

BATEA aplica modelos estadísticos (ML sin supervisión como PCA y clustering) para identificar **anomalías que suelen ser señales de equipos críticos**.

---

### 🧠 Ejemplo interpretado (simulado)

Supón que tienes:

- 15 máquinas en red.
- BATEA identifica que una tiene puertos 445, 389, 135, 88, y hostname `DC-01`.

Resultado:

```bash
Rank Hostname       Score  IP             Services
1    DC-01.local     0.98   192.168.100.2  SMB, LDAP, Kerberos
2    SRV-BD01        0.75   192.168.100.5  MSSQL, RDP
3    USR-PC1         0.12   192.168.100.12  SMB
```

➡️ Esto te dice que `DC-01.local` es probablemente un **controlador de dominio**, tu objetivo más interesante.

---

### 🛠️ OPCIONES ÚTILES DE BATEA

```bash
python3 batea.py -h
```

Algunos flags útiles:

| Opción                 | Función                         |
| ---------------------- | ------------------------------- |
| `--input-file red.xml` | Usa escaneo Nmap XML            |
| `--log batea.log`      | Guarda la salida en log         |
| `--verbose`            | Muestra más detalle             |
| `--model`              | Define el tipo de modelo a usar |

---

### 🧩 BONUS: Integrar con recon-ng o BloodHound

Aunque BATEA no exporta directamente a BloodHound, puedes usar su salida para:

- Identificar objetivos.
- Preparar ataques específicos (Kerberoasting, LLMNR, etc.).
- Marcar equipos en un mapa de red.

---

### ✅ RESUMEN

| Característica     | BATEA                            |
| ------------------ | -------------------------------- |
| ¿Qué hace?         | Reconocimiento con ML            |
| ¿Qué identifica?   | Hosts críticos (DC, servidores)  |
| ¿Dónde se ejecuta? | Kali, desde archivo XML de Nmap  |
| ¿Qué analiza?      | Nombre, puertos, TTL, protocolos |
| ¿Cómo se instala?  | `git clone`, `pip install`       |

---

[🔼](#índice)

---

## **96. Pesidious: Mutaciones con Deep Learning**

### 📌 ¿Qué es Pesidious?

**Pesidious** es una herramienta ofensiva que usa **Deep Learning (aprendizaje profundo)** para generar **mutaciones de malware** que pueden evadir sistemas antivirus (AV) o EDRs (Endpoint Detection & Response).

Su objetivo es ayudar a investigadores de seguridad y profesionales de pentesting a:

- Entender cómo los antivirus detectan amenazas.
- Evaluar si un archivo malicioso es detectable.
- Crear **variantes del mismo archivo ejecutable** que puedan evitar detección.

> ⚠️ **Uso legal y ético**: Esta herramienta está diseñada para **pruebas de laboratorio y entornos controlados**. Usarla fuera de estos contextos es ilegal.

---

### 🎯 ¿Por qué es importante?

Los antivirus modernos usan inteligencia artificial para detectar malware. Pesidious responde generando variantes **entrenadas para parecer benignas**, mientras siguen siendo maliciosas.

Usa técnicas como:

- **Mutación de código binario**.
- Evaluación automática en VirusTotal (opcional).
- Redes neuronales entrenadas en muestras maliciosas y benignas.

---

### 🖥️ ENTORNO DE PRUEBA (Máquinas Virtuales)

| Máquina    | Rol      | Sistema        |
| ---------- | -------- | -------------- |
| Kali Linux | Atacante | Kali (última)  |
| Windows 10 | Víctima  | Windows 10 Pro |
| Ubuntu VM  | Sandbox  | Ubuntu         |

> Ideal para usar con una **sandbox aislada** (como Cuckoo o FLARE VM) donde probar los ejecutables mutados.

---

### ⚙️ INSTALACIÓN DE PESIDIOUS EN KALI LINUX

#### Paso 1: Actualiza e instala dependencias

```bash
sudo apt update && sudo apt install -y python3-pip git
```

#### Paso 2: Clona el repositorio oficial

```bash
git clone https://github.com/peaas/pesidious.git
cd pesidious
```

#### Paso 3: Instala los requerimientos de Python

```bash
pip3 install -r requirements.txt
```

---

#### ⚙️ OPCIONAL: Configurar VirusTotal (si quieres automatizar pruebas)

Crea una cuenta gratuita en [https://www.virustotal.com/](https://www.virustotal.com/)
Ve a tu perfil > API Key.

Luego, edita el archivo `.env` o usa tu clave al ejecutar:

```bash
export VT_API_KEY='tu_api_key_aquí'
```

---

### 🧪 USO BÁSICO: MUTAR UN BINARIO

Supón que tienes un ejecutable llamado `malware.exe`.

1. Copia `malware.exe` al directorio de Pesidious.

2. Ejecuta:

```bash
python3 pesidious.py --file malware.exe --mutate --epochs 5
```

Donde:

- `--file`: es tu binario de entrada.
- `--mutate`: indica que quieres generar mutaciones.
- `--epochs`: cuántas generaciones de mutación quieres probar (más = más tiempo).

📁 Esto genera varios archivos mutados:

```
output/
├── malware_mutation_1.exe
├── malware_mutation_2.exe
└── ...
```

---

### 🧠 ¿Qué hace internamente?

Pesidious aplica cambios a nivel de:

- **Secciones del PE (Portable Executable)**.
- **Bytes redundantes**.
- **Padding entre instrucciones**.
- **Encriptado o encoding de strings**.
- Cambia hashes sin romper funcionalidad.

Luego, usa una red neuronal para **verificar si sigue siendo ejecutable** y **menos detectable**.

---

### 🧪 PRUEBA EN MÁQUINA VIRTUAL WINDOWS

1. Pasa `malware_mutation_1.exe` a tu VM de Windows.

2. Usa un antivirus real (como Defender, Kaspersky o Avast Free) para escanearlo.

3. Comprueba si alguno de los archivos mutados **no es detectado**, mientras que el original sí.

4. Opcional: ejecuta el archivo en una **sandbox (Cuckoo, Any.Run, FLARE VM)** para ver comportamiento.

---

### 💡 RESULTADOS ESPERADOS

| Archivo                  | Detección AV | Funciona    |
| ------------------------ | ------------ | ----------- |
| `malware.exe`            | ❌ Detectado | ✅ Ejecuta  |
| `malware_mutation_1.exe` | ✅ Evadido   | ✅ Ejecuta  |
| `malware_mutation_3.exe` | ❌ Detectado | ❌ Se rompe |

> Los mejores resultados se logran afinando los `--epochs`, entrenando el modelo con más muestras o integrando módulos personalizados.

---

### ⚙️ OTRAS FUNCIONES DE PESIDIOUS

| Comando                         | Función                                 |
| ------------------------------- | --------------------------------------- |
| `--analyze`                     | Analiza y clasifica binarios            |
| `--train`                       | Entrena tu propio modelo de detección   |
| `--check-virustotal`            | Compara detección AV (requiere API Key) |
| `--save-model` / `--load-model` | Guarda o carga modelo entrenado         |

---

### 🧠 BONUS: ENTRENAMIENTO PERSONALIZADO

Puedes alimentar tu propio conjunto de datos de malware y goodware (benignos) y hacer:

```bash
python3 pesidious.py --train --dataset ./samples/
```

Así, el modelo se adapta mejor a tu contexto (entorno industrial, IoT, etc.).

---

### ✅ RESUMEN

| Elemento             | Detalle                                       |
| -------------------- | --------------------------------------------- |
| ¿Qué es?             | Generador de malware mutado con Deep Learning |
| ¿Para qué sirve?     | Evadir AV, probar EDR, análisis defensivo     |
| ¿Qué necesitas?      | Python, binarios PE, entorno controlado       |
| ¿Resultado esperado? | Malware funcional, pero con baja detección    |
| ¿Es legal usarlo?    | Solo en laboratorios o con permiso explícito  |

---

[🔼](#índice)

---

## **97. Ingeniería Social - Deep fake**

### 📌 ¿Qué es la Ingeniería Social con Deepfake?

La **ingeniería social** busca manipular a personas para obtener información, acceso o control de sistemas. Cuando se combina con **Deepfake**, se vuelve aún más peligrosa, porque se usan **videos o audios falsos generados por inteligencia artificial** que imitan a personas reales.

> 💡 **Deepfake** = _Deep learning + Fake_. Son medios audiovisuales generados por IA que suplantan rostros, voces o movimientos de personas reales.

---

### 🧠 ¿Para qué se usa en Ciberseguridad?

- Suplantar a un jefe para pedir contraseñas o transferencias (ej: video de “el jefe” pidiendo acceso).
- Generar audios que imitan voces reales (vía WhatsApp, llamadas, etc.).
- Manipular reuniones virtuales.
- Extorsionar o engañar en campañas de phishing.

---

### 🎯 Objetivo del laboratorio

Usar **herramientas de deepfake (de voz o video)** para crear una suplantación y simular un ataque de ingeniería social, **en un entorno virtual cerrado**.

---

### 🖥️ MÁQUINAS VIRTUALES SUGERIDAS

| Máquina    | Rol            | Sistema        |
| ---------- | -------------- | -------------- |
| Kali Linux | Atacante       | Kali Linux     |
| Windows 10 | Víctima        | Windows 10 Pro |
| Ubuntu     | Laboratorio IA | Ubuntu 22.04   |

> 🧪 Opcional: Puedes usar la Ubuntu o Kali como laboratorio para las herramientas de Deep Learning si tu Kali no tiene suficiente RAM/GPU.

---

### 💻 HERRAMIENTAS QUE USAREMOS

#### Para voz (Deepfake de voz):

- `Real-Time Voice Cloning`
- `Descript` (web, opcional)
- `ElevenLabs` o `Play.ht` (online, demo gratis)

#### Para video (rostros animados):

- `DeepFaceLab` (Windows)
- `Avatarify` o `First Order Motion Model` (Linux)

---

### 🔧 INSTALACIÓN DE UNA HERRAMIENTA: Real-Time Voice Cloning

Vamos a usar **Real-Time Voice Cloning** para clonar una voz y generar audio falso.

#### Paso 1: Instalar dependencias (en Ubuntu o Kali)

```bash
sudo apt update && sudo apt install git python3-pip build-essential espeak ffmpeg libsndfile1-dev
```

#### Paso 2: Clonar el repositorio

```bash
git clone https://github.com/CorentinJ/Real-Time-Voice-Cloning.git
cd Real-Time-Voice-Cloning
```

#### Paso 3: Instalar los requerimientos

```bash
pip3 install -r requirements.txt
```

> ⚠️ Es posible que necesites una GPU para buenos resultados (puedes usar Google Colab si no tienes).

---

#### Paso 4: Descargar los modelos preentrenados

```bash
# Dentro del repo:
wget https://github.com/CorentinJ/Real-Time-Voice-Cloning/releases/download/2020.05.14/pretrained.zip
unzip pretrained.zip
```

---

### 🚀 USO BÁSICO

1. **Inicia la demo**:

```bash
python3 demo_cli.py
```

2. Elige un archivo de audio de referencia (por ejemplo, la voz de tu jefe o compañero).

3. Escribe un texto:

```text
"Hola, necesito que me envíes el informe de contraseñas ahora mismo."
```

4. La IA generará un audio **falso pero similar** a la voz de la persona.

Puedes guardar el archivo `.wav` y usarlo en correos, WhatsApp Web o llamadas simuladas.

---

### 🧪 ESCENARIO DE LABORATORIO

#### Simulación:

Tu máquina Kali/Ubuntu genera un audio con la voz falsa de “El Director de TI” diciendo:

> "Aprueba este archivo, ya hablé con Seguridad."

Luego, envías ese audio junto con un archivo `malicioso.docx` por email simulado (con `SET` o `Gophish`), para simular cómo el engaño aumenta si la voz es familiar.

---

### 👀 DEMO VISUAL (OPCIONAL): Avatarify o FOMM

#### Avatarify: Clona rostro + voz en videollamadas (Zoom, Teams)

#### Requiere:

- GPU NVIDIA.
- Python.
- Zoom/Teams en VM.

Más info: [https://github.com/alievk/avatarify](https://github.com/alievk/avatarify)

---

### ⚠️ ÉTICA Y LEGALIDAD

Usar deepfakes para ataques reales es **ilegal y antiético**. Estos laboratorios son para:

- Pruebas de conciencia de seguridad.
- Simulacros de phishing.
- Detección de suplantación.
- Entrenamiento en Ciberdefensa.

---

### ✅ RESUMEN

| Elemento          | Detalles                                                           |
| ----------------- | ------------------------------------------------------------------ |
| ¿Qué es?          | Técnica de suplantación con IA (voz/video)                         |
| ¿Objetivo?        | Engañar usando identidad de otra persona                           |
| ¿Herramientas?    | Real-Time Voice Cloning, DeepFaceLab, Avatarify                    |
| ¿En qué entornos? | Kali, Ubuntu, Windows (en VMs)                                     |
| ¿Cómo se usa?     | Generas audio/video falso y lo usas en un ataque simulado          |
| ¿Legal?           | Solo con fines educativos, laboratorios y simulaciones autorizadas |

---

[🔼](#índice)

---

| **Inicio**         | **atrás 9**                                 |
| ------------------ | ------------------------------------------- |
| [🏠](../README.md) | [⏪](./2_9_Tecnicas_de_Post_Explotacion.md) |
