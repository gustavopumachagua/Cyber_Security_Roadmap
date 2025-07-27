| **Inicio**         | **atrás 2**                                                         | **Siguiente 4**                               |
| ------------------ | ------------------------------------------------------------------- | --------------------------------------------- |
| [🏠](../README.md) | [⏪](./7_2_Introduccion_a_la_Administracion_de_Servidores_Linux.md) | [⏩](./7_4_Redes_Informaticas_de_Internet.md) |

---

## **Índice**

| Temario                                                                                                          |
| ---------------------------------------------------------------------------------------------------------------- |
| [643. Tus siguientes pasos en Linux](#643-tus-siguientes-pasos-en-linux)                                         |
| [644. ¿Cómo es el arranque del sistema?](#644-cómo-es-el-arranque-del-sistema)                                   |
| [645. Modo recovery](#645-modo-recovery)                                                                         |
| [646. ¿Qué son los grupos y usuarios en Linux?](#646-qué-son-los-grupos-y-usuarios-en-linux)                     |
| [647. Manejo de usuarios](#647-manejo-de-usuarios)                                                               |
| [648. Manejo de grupos](#648-manejo-de-grupos)                                                                   |
| [649. El control de accesos en Linux](#649-el-control-de-accesos-en-linux)                                       |
| [650. Creación de un usuario administrador](#650-creación-de-un-usuario-administrador)                           |
| [651. Particionando y montando una unidad](#651-particionando-y-montando-una-unidad)                             |
| [652. ¿Qué es RAID y LVM?](#652-qué-es-raid-y-lvm)                                                               |
| [653. Creacion de sistema RAID 1](#653-creacion-de-sistema-raid-1)                                               |
| [654. Creación de LVM sobre RAID 1](#654-creación-de-lvm-sobre-raid-1)                                           |
| [655. Agregando el sistema a fstab](#655-agregando-el-sistema-a-fstab)                                           |
| [656. Preparando el sistema](#656-preparando-el-sistema)                                                         |
| [657. Escalando el sistema con chroot e instalando Grub](#657-escalando-el-sistema-con-chroot-e-instalando-grub) |

---

# **Administración de Servidores Linux: Manejo de Recursos**

## **643. Tus siguientes pasos en Linux**

### 🧭 1. **Fortalece tus habilidades en la terminal**

La terminal es tu superpoder en Linux.

#### 📌 Practica comandos avanzados:

| Comando | ¿Para qué sirve?                                    |
| ------- | --------------------------------------------------- |
| `find`  | Buscar archivos con filtros por nombre, fecha, etc. |
| `grep`  | Buscar texto dentro de archivos                     |
| `awk`   | Procesamiento de textos basado en columnas          |
| `cut`   | Extraer partes de una línea o archivo               |
| `sed`   | Sustituciones y ediciones automáticas de texto      |
| `xargs` | Ejecuta comandos sobre resultados anteriores        |

📍 **Ejemplo**:

```bash
find /var/log -name "*.log" | xargs grep "error"
```

> Busca archivos `.log` que contengan la palabra "error".

---

### 🧱 2. **Aprende a manejar servicios con `systemctl`**

Linux moderno usa **systemd** para manejar servicios (como Apache, MySQL, SSH).

| Acción                         | Comando                       |
| ------------------------------ | ----------------------------- |
| Ver si un servicio está activo | `systemctl status ssh`        |
| Iniciar un servicio            | `sudo systemctl start nginx`  |
| Detener un servicio            | `sudo systemctl stop nginx`   |
| Habilitar al iniciar           | `sudo systemctl enable nginx` |

---

### 🧠 3. **Maneja usuarios y permisos**

Aprender a controlar quién puede hacer qué es esencial.

| Acción                      | Comando                       |
| --------------------------- | ----------------------------- |
| Crear usuario               | `sudo adduser juan`           |
| Asignar grupo sudo          | `sudo usermod -aG sudo juan`  |
| Cambiar permisos de archivo | `chmod 755 archivo.sh`        |
| Cambiar propietario         | `chown juan:juan archivo.txt` |

📍 **Ejemplo**:

```bash
sudo adduser pruebas
sudo usermod -aG sudo pruebas
```

---

### 🌐 4. **Administra tu red**

| Comando          | ¿Qué hace?                       |
| ---------------- | -------------------------------- |
| `ip a`           | Muestra interfaces de red        |
| `ping`           | Verifica conectividad            |
| `curl` o `wget`  | Descarga archivos por HTTP       |
| `netstat -tulnp` | Ver puertos abiertos y servicios |

📍 **Ejemplo**:

```bash
curl https://api.github.com
```

---

### 🛡️ 5. **Empieza con seguridad básica**

- Instala **firewalls** como `ufw` o `firewalld`.
- Aprende sobre SSH: cambia el puerto por defecto, usa llaves.
- Usa `fail2ban` para proteger tu servidor de intentos de acceso.

📍 **Ejemplo con UFW**:

```bash
sudo apt install ufw
sudo ufw enable
sudo ufw allow ssh
sudo ufw status
```

---

### 🧪 6. **Aprende scripting Bash**

Automatiza tareas con scripts. Es lo más útil para administración de sistemas.

📍 **Ejemplo básico**:

```bash
#!/bin/bash
echo "¡Hola $USER!"
echo "La fecha de hoy es: $(date)"
```

Guarda como `saludo.sh` y hazlo ejecutable:

```bash
chmod +x saludo.sh
./saludo.sh
```

---

### 🧰 7. **Administra paquetes (apt/yum/dnf)**

Ya sabes instalar con `apt`, `yum` o `dnf`, ahora aprende:

- A listar paquetes: `apt list --installed`
- A buscar: `apt search apache`
- A actualizar: `sudo apt update && sudo apt upgrade`

---

### 🔐 8. **Practica con servidores**

Instala servicios reales como:

| Servicio      | Comando de instalación (Ubuntu)   |
| ------------- | --------------------------------- |
| Apache        | `sudo apt install apache2`        |
| Nginx         | `sudo apt install nginx`          |
| MySQL/MariaDB | `sudo apt install mariadb-server` |
| SSH           | `sudo apt install openssh-server` |

---

### 🎯 EJEMPLO COMPLETO: **Configura un servidor básico NGINX + HTML + cron**

#### 🔧 Paso 1: Instala NGINX

```bash
sudo apt update
sudo apt install nginx
```

#### 📁 Paso 2: Crea una página web

```bash
echo "<h1>Servidor activo: $(date)</h1>" | sudo tee /var/www/html/index.html
```

#### 🔁 Paso 3: Crea un script que actualice la hora cada minuto

```bash
sudo nano /usr/local/bin/actualizar_html.sh
```

Contenido:

```bash
#!/bin/bash
echo "<h1>Servidor activo: $(date)</h1>" > /var/www/html/index.html
```

Guarda y hazlo ejecutable:

```bash
sudo chmod +x /usr/local/bin/actualizar_html.sh
```

#### ⏱️ Paso 4: Agrega un cron job

```bash
crontab -e
```

Agrega:

```bash
* * * * * /usr/local/bin/actualizar_html.sh
```

#### 🌐 Paso 5: Visita tu servidor

Abre un navegador y entra a `http://localhost` o la IP de tu máquina virtual.

---

### ✅ ¿Qué aprendiste con este ejemplo?

- Instalar servicios
- Crear scripts automatizados
- Programar tareas con `cron`
- Administrar archivos y permisos
- Publicar contenido dinámico en un servidor real

---

### 🔚 Conclusión: ¿Qué sigue?

Una vez domines lo anterior, te recomiendo:

🔸 Aprender sobre:

- Contenedores (Docker)
- Monitoreo (htop, journalctl, logs)
- Respaldos (`rsync`, `tar`, `scp`)
- Configuración de servicios como FTP, Samba, DNS, Mail
- Crear usuarios y usar llaves SSH

🔸 Plataformas donde practicar:

- [https://www.overthewire.org](https://www.overthewire.org)
- [https://linuxjourney.com](https://linuxjourney.com)
- [https://tryhackme.com](https://tryhackme.com) (modo seguridad)

---

[🔼](#índice)

---

## **644. ¿Cómo es el arranque del sistema?**

### 🧠 ¿Qué es el arranque del sistema (boot process) en Linux?

El **arranque del sistema** es el proceso que ocurre desde que enciendes tu computadora hasta que el sistema operativo (como Linux) está completamente cargado y listo para usarse.

---

### 🧱 Etapas del arranque en Linux

#### 1. **BIOS / UEFI**

- Cuando enciendes el equipo, lo primero que se ejecuta es el **BIOS** (o UEFI en sistemas modernos).
- Verifica que el hardware funcione bien (RAM, disco, teclado, etc.).
- Luego, busca un dispositivo **de arranque** (disco, USB, CD) con un **cargador de arranque (bootloader)**.

📌 _Ejemplo visual_: Cuando ves la pantalla negra con el logo del fabricante y presionas F2/F10/DEL para entrar a configuración, eso es el BIOS.

---

#### 2. **MBR / GPT y el Bootloader**

El BIOS/UEFI carga el **MBR** (Master Boot Record) o **GPT** del disco, que contiene el **bootloader**.

**Bootloaders comunes**:

- **GRUB** (el más usado en Linux)
- LILO (más antiguo)

📌 GRUB = GRand Unified Bootloader.

GRUB muestra un menú si tienes varios sistemas instalados (por ejemplo, Windows y Linux) o simplemente carga Linux.

🔎 **Puedes ver GRUB al encender el equipo si presionas Shift o Esc antes que arranque Linux.**

---

#### 3. **Kernel de Linux**

GRUB carga el **kernel de Linux** (archivo llamado algo como `vmlinuz-6.5.0-generic`), el núcleo del sistema operativo.

El kernel:

- Detecta hardware
- Monta el sistema de archivos raíz `/`
- Comienza a ejecutar procesos esenciales

---

#### 4. **init o systemd**

Una vez el kernel arranca, ejecuta el **primer proceso de usuario**: `init` o `systemd`.

Hoy en día la mayoría de distribuciones usan `systemd`.

📌 Este proceso tiene siempre el **PID 1**, y se encarga de:

- Iniciar servicios (red, interfaz gráfica, SSH, etc.)
- Montar discos
- Activar logs
- Ejecutar lo necesario para que el sistema funcione

🔍 Puedes ver esto con:

```bash
ps -p 1 -o comm=
```

Resultado esperado: `systemd`

---

#### 5. **Target o Runlevel**

`systemd` usa **targets**, que son como "modos" del sistema:

| Target              | Función                                  |
| ------------------- | ---------------------------------------- |
| `rescue.target`     | Modo de recuperación                     |
| `multi-user.target` | Modo consola sin interfaz gráfica        |
| `graphical.target`  | Modo completo con GUI (interfaz gráfica) |

---

#### 6. **Login / Interfaz gráfica**

Finalmente, se ejecuta:

- Un **login manager** (en sistemas con GUI, como GDM o LightDM)
- O el **prompt de terminal** (si no hay entorno gráfico)

Aquí ingresas tu usuario y contraseña.

---

### 🛠 ¿Cómo verificar o explorar este proceso?

#### 📌 Ver GRUB:

```bash
cat /boot/grub/grub.cfg
```

#### 📌 Ver qué kernel estás usando:

```bash
uname -r
```

#### 📌 Ver el PID 1:

```bash
ps -p 1 -o comm=
```

#### 📌 Ver los servicios que se arrancan:

```bash
systemctl list-units --type=service --state=running
```

#### 📌 Ver logs del arranque:

```bash
journalctl -b
```

---

### 🔧 ¿Cómo se instala GRUB o se repara?

#### ✅ En Ubuntu/Debian:

```bash
sudo grub-install /dev/sda
sudo update-grub
```

(Usa `/dev/sda` o el disco donde va el MBR)

#### ✅ En RHEL/CentOS:

```bash
sudo grub2-install /dev/sda
sudo grub2-mkconfig -o /boot/grub2/grub.cfg
```

---

### 🧪 EJEMPLO COMPLETO: Analizar paso a paso el arranque en una máquina virtual Ubuntu Server

#### Paso 1: Ver el GRUB al iniciar

1. Crea una máquina virtual con Ubuntu Server en VirtualBox.
2. Al iniciarla, presiona **Shift** para mostrar GRUB.
3. Verás algo como:

   ```
   Ubuntu
   Advanced options for Ubuntu
   ```

---

#### Paso 2: Ver el kernel y el init

Entra a la VM y ejecuta:

```bash
uname -r
```

> Resultado: Muestra la versión del kernel (ej. `6.5.0-25-generic`)

```bash
ps -p 1 -o comm=
```

> Resultado: `systemd`

---

#### Paso 3: Ver los servicios activos tras el arranque

```bash
systemctl list-units --type=service --state=running
```

Te mostrará todos los servicios levantados automáticamente.

---

#### Paso 4: Ver cuánto demoró el arranque

```bash
systemd-analyze
```

> Resultado: `Startup finished in 2.1s (kernel) + 3.8s (userspace) = 5.9s`

---

#### Paso 5: Ver el árbol de dependencias del arranque

```bash
systemd-analyze blame
```

> Muestra qué servicios tardan más en iniciarse.

---

### ✅ Conclusión

El proceso de arranque en Linux es un flujo estructurado:

1. **BIOS/UEFI** → 2. **Bootloader (GRUB)** → 3. **Kernel** → 4. **systemd/init** → 5. **Servicios/Target** → 6. **Login**

Entender cada fase te permite:

- Diagnosticar errores de arranque
- Reparar sistemas corruptos
- Personalizar cómo arranca tu servidor o equipo

---

[🔼](#índice)

---

## **645. Modo recovery**

### 🛠 ¿Qué es el Modo Recovery en Linux?

El **modo recovery** (modo de recuperación) es una opción especial del sistema Linux que te permite **solucionar errores** cuando no puedes arrancar normalmente.

Es una especie de **"modo seguro"**, donde puedes:

- Reparar el sistema de archivos.
- Cambiar contraseñas (incluido root).
- Reinstalar paquetes dañados.
- Deshabilitar servicios que impiden el arranque.
- Recuperar datos.
- Montar el sistema como solo lectura.

---

### 🧠 ¿Cómo funciona?

Cuando enciendes el sistema y aparece **GRUB**, una de las opciones es **"Advanced options for Ubuntu"** (o similar). Dentro de esa sección está el **kernel en modo recovery**.

Este modo carga:

- El kernel de Linux.
- El sistema en modo **mínimo** (runlevel 1 o `rescue.target` con `systemd`).
- Un menú tipo texto con varias opciones de reparación.

---

### ⚙️ ¿Cómo entrar al Modo Recovery?

#### 🔹 En distribuciones como **Ubuntu/Debian**:

1. Reinicia el equipo.
2. Cuando veas la pantalla de GRUB, presiona `Shift` (si no aparece sola).
3. Selecciona:
   `Advanced options for Ubuntu`
4. Luego elige:
   `Ubuntu, with Linux x.x.x (recovery mode)`
5. Verás un menú con opciones como:

   - `resume` (volver a arrancar normalmente)
   - `clean` (intenta liberar espacio)
   - `dpkg` (reparar paquetes)
   - `fsck` (verificar sistema de archivos)
   - `root` (entrar a la consola root)

🔒 Nota: muchas veces el sistema de archivos está montado en modo **solo lectura**. Para poder hacer cambios, deberás montar como lectura-escritura:

```bash
mount -o remount,rw /
```

---

#### 🔹 En distribuciones con **Systemd** (RHEL, Fedora, Arch, etc.):

Puedes forzar el arranque en modo de recuperación editando GRUB así:

1. En GRUB, selecciona tu entrada normal.
2. Presiona `e` para editar.
3. Busca la línea que empieza con `linux` y añade al final:

   ```
   systemd.unit=rescue.target
   ```

4. Presiona `Ctrl + X` o `F10` para arrancar con esa configuración.

Esto iniciará en modo **rescate** (similar al recovery).

---

### 🔧 ¿Se puede instalar o configurar el modo recovery?

En la mayoría de distribuciones **ya viene incluido** cuando instalas Linux.

#### ✅ Verifica si está instalado:

```bash
ls /boot
```

Busca entradas como:

```
vmlinuz-x.x.x
initrd.img-x.x.x
```

También verifica en el archivo de configuración del GRUB:

```bash
cat /boot/grub/grub.cfg | grep recovery
```

Si no aparece, puedes **actualizar GRUB** para regenerar las entradas:

- Ubuntu/Debian:

  ```bash
  sudo update-grub
  ```

- RHEL/CentOS:

  ```bash
  sudo grub2-mkconfig -o /boot/grub2/grub.cfg
  ```

---

### 🧪 EJEMPLO COMPLETO: Recuperar acceso root desde modo recovery

Imagina que **olvidaste la contraseña de tu usuario root/admin**. Vamos a recuperarla usando el modo recovery en Ubuntu Server.

---

#### ✅ PASOS:

##### 1. Reinicia la máquina

En VirtualBox o tu PC real, reinicia y **entra al menú de GRUB** con `Shift`.

---

##### 2. Entra a `Advanced options for Ubuntu`

Selecciona la opción:

```
Ubuntu, with Linux x.x.x-generic (recovery mode)
```

---

##### 3. Selecciona `root` (Drop to root shell prompt)

Esto te dará una consola limitada **como root** pero en modo solo lectura.

---

##### 4. Montar el sistema con permisos de escritura

```bash
mount -o remount,rw /
```

---

##### 5. Cambiar la contraseña de root

```bash
passwd root
```

Te pedirá nueva contraseña. Escríbela 2 veces.

---

##### 6. Reinicia

```bash
reboot
```

O usa el menú `resume` para seguir cargando el sistema.

---

✅ ¡Listo! Has cambiado la contraseña de root y recuperado el acceso gracias al modo recovery.

---

### 🧯 Consejos de seguridad

- **Desactiva GRUB sin contraseña** si tu servidor es accesible físicamente.
- Agrega protección con contraseña al GRUB editando `/etc/grub.d/40_custom`.
- Usa `passwd -l root` si no deseas que se pueda loguear por root.

---

### ✅ RESUMEN

| Paso                         | Qué hace                                   |
| ---------------------------- | ------------------------------------------ |
| GRUB → Recovery              | Carga kernel en modo recuperación          |
| `mount -o remount,rw /`      | Habilita escritura en disco                |
| `passwd root`                | Te permite recuperar el acceso root        |
| `fsck`                       | Verifica y repara errores en disco         |
| `dpkg`                       | Reinstala o repara paquetes dañados        |
| `systemd.unit=rescue.target` | Fuerza arranque en modo rescate desde GRUB |

---

[🔼](#índice)

---

## **646. ¿Qué son los grupos y usuarios en Linux?**

### 🧑‍💻 ¿Qué son los Usuarios en Linux?

Un **usuario en Linux** es cualquier cuenta que puede iniciar sesión en el sistema, ya sea una persona (como tú) o un servicio (como MySQL, Apache, etc.).

Cada usuario tiene:

- Un **nombre de usuario** (ej: `gustavo`).
- Un **UID** (identificador único).
- Un **grupo principal** (por defecto con el mismo nombre del usuario).
- Un **directorio personal** (`/home/gustavo`).
- Una **shell** por defecto (`/bin/bash` u otra).

El usuario más importante es **root**, que tiene acceso total al sistema (UID 0).

---

### 👥 ¿Qué son los Grupos en Linux?

Un **grupo** es una colección de usuarios. Sirve para asignar **permisos compartidos** a varios usuarios al mismo tiempo.

Ejemplos comunes:

- Grupo `sudo` → usuarios que pueden usar `sudo`.
- Grupo `www-data` → usado por servicios web como Apache/Nginx.

Un usuario puede:

- Tener un **grupo principal** (uno solo).
- Pertenecer a **grupos secundarios** (muchos).

---

### 📂 ¿Dónde se guardan usuarios y grupos?

Linux guarda la información en archivos de texto:

| Archivo       | Contiene                                               |
| ------------- | ------------------------------------------------------ |
| `/etc/passwd` | Información de los usuarios (nombre, UID, home, shell) |
| `/etc/shadow` | Contraseñas cifradas de los usuarios                   |
| `/etc/group`  | Lista de grupos y sus miembros                         |

Puedes leerlos con:

```bash
cat /etc/passwd
cat /etc/group
```

---

### 🛠 Comandos para gestionar usuarios y grupos

#### 🔹 Crear un usuario

```bash
sudo adduser juan
```

Esto también:

- Crea su carpeta `/home/juan`.
- Le pide una contraseña.
- Le asigna un grupo propio `juan`.

#### 🔹 Crear un grupo

```bash
sudo groupadd desarrolladores
```

#### 🔹 Añadir un usuario a un grupo

```bash
sudo usermod -aG desarrolladores juan
```

(El `-aG` es para añadir sin quitarle otros grupos.)

#### 🔹 Ver a qué grupos pertenece un usuario

```bash
groups juan
```

#### 🔹 Eliminar un usuario

```bash
sudo deluser juan
```

(O con su carpeta: `sudo deluser --remove-home juan`)

#### 🔹 Eliminar un grupo

```bash
sudo groupdel desarrolladores
```

---

### 🔒 ¿Y los permisos?

Usuarios y grupos son esenciales para la **gestión de permisos** en archivos:

```bash
ls -l archivo.txt
```

Ejemplo de salida:

```
-rw-r--r-- 1 juan desarrolladores  0 jul 23 10:00 archivo.txt
```

- El archivo pertenece al **usuario `juan`**.
- El grupo propietario es **`desarrolladores`**.
- Los permisos indican:

  - `rw-`: el usuario puede leer y escribir.
  - `r--`: el grupo puede leer.
  - `r--`: los demás pueden leer.

---

### ✅ EJEMPLO COMPLETO PASO A PASO

#### Objetivo:

Crear un usuario llamado `gustavo`, asignarlo a un grupo llamado `proyectos`, y probar los permisos en un archivo.

---

#### 1️⃣ Crear el usuario:

```bash
sudo adduser gustavo
```

Sigue los pasos del sistema (te pedirá contraseña, etc.).

---

#### 2️⃣ Crear el grupo:

```bash
sudo groupadd proyectos
```

---

#### 3️⃣ Añadir a `gustavo` al grupo `proyectos`:

```bash
sudo usermod -aG proyectos gustavo
```

Puedes confirmar con:

```bash
groups gustavo
```

---

#### 4️⃣ Crear un archivo y cambiarle el grupo:

```bash
sudo touch /home/gustavo/informe.txt
sudo chown gustavo:proyectos /home/gustavo/informe.txt
```

---

#### 5️⃣ Asignar permisos para el grupo:

```bash
sudo chmod 640 /home/gustavo/informe.txt
```

Esto significa:

- `6` (rw-) para el dueño (`gustavo`)
- `4` (r--) para el grupo (`proyectos`)
- `0` (---) para los demás

---

#### 6️⃣ Probar acceso con otro usuario:

Supón que tienes un usuario `ana`. Añádelo al grupo:

```bash
sudo usermod -aG proyectos ana
```

Inicia sesión como `ana` y trata de leer el archivo:

```bash
cat /home/gustavo/informe.txt
```

✔️ Si pertenece al grupo `proyectos`, podrá leer el archivo.

---

### 🧠 RESUMEN RÁPIDO

| Acción         | Comando                          |
| -------------- | -------------------------------- |
| Crear usuario  | `sudo adduser nombre`            |
| Crear grupo    | `sudo groupadd nombre`           |
| Añadir a grupo | `sudo usermod -aG grupo usuario` |
| Ver grupos     | `groups usuario`                 |
| Ver usuarios   | `cat /etc/passwd`                |
| Ver grupos     | `cat /etc/group`                 |

---

[🔼](#índice)

---

## **647. Manejo de usuarios**

### 🧑‍💻 ¿Qué significa “manejo de usuarios” en Linux?

El **manejo de usuarios** en Linux es una de las tareas fundamentales del administrador del sistema. Involucra:

- Crear, modificar y eliminar cuentas de usuario.
- Asignar grupos a los usuarios.
- Configurar contraseñas y permisos.
- Controlar quién puede hacer qué en el sistema.

---

### 📌 ¿Por qué es importante?

Porque Linux es un sistema multiusuario. Esto significa que **varias personas pueden usar el mismo sistema** al mismo tiempo, y cada una debe tener **acceso solo a lo que le corresponde**.

---

### 📂 Archivos importantes del sistema para usuarios

Linux guarda la información de usuarios y contraseñas en estos archivos:

| Archivo       | Descripción                                          |
| ------------- | ---------------------------------------------------- |
| `/etc/passwd` | Lista de usuarios con info básica (UID, shell, etc.) |
| `/etc/shadow` | Contraseñas cifradas                                 |
| `/etc/group`  | Información de los grupos                            |

Puedes verlos con `cat`:

```bash
cat /etc/passwd
cat /etc/shadow
cat /etc/group
```

---

### 🔧 ¿Cómo se maneja?

Vamos por partes con ejemplos.

---

### 🔹 1. **Crear un usuario**

```bash
sudo adduser juan
```

Este comando:

- Crea al usuario `juan`.
- Le asigna una carpeta personal en `/home/juan`.
- Le pide una contraseña.
- Le crea un grupo con su nombre.

También puedes usar:

```bash
sudo useradd -m juan
sudo passwd juan
```

> `-m` crea el directorio home si no existe.

---

### 🔹 2. **Ver información de un usuario**

```bash
id juan
```

Salida posible:

```
uid=1001(juan) gid=1001(juan) groups=1001(juan)
```

También puedes usar:

```bash
getent passwd juan
```

---

### 🔹 3. **Cambiar contraseña a un usuario**

```bash
sudo passwd juan
```

---

### 🔹 4. **Modificar un usuario**

Cambiar nombre:

```bash
sudo usermod -l nuevo_nombre juan
```

Cambiar directorio home:

```bash
sudo usermod -d /nuevo/home juan
```

Cambiar shell predeterminada:

```bash
sudo usermod -s /bin/zsh juan
```

---

### 🔹 5. **Eliminar un usuario**

```bash
sudo deluser juan
```

Eliminar también su carpeta:

```bash
sudo deluser --remove-home juan
```

---

### 🔹 6. **Bloquear y desbloquear cuentas**

🔒 Bloquear:

```bash
sudo usermod -L juan
```

🔓 Desbloquear:

```bash
sudo usermod -U juan
```

---

### 🔹 7. **Listar todos los usuarios**

```bash
cut -d: -f1 /etc/passwd
```

O también:

```bash
getent passwd
```

---

### 📦 ¿Cómo se instala?

Los comandos como `adduser`, `useradd`, `passwd`, etc., **ya vienen preinstalados** en todas las distribuciones Linux. No necesitas instalar nada extra.

Si por alguna razón no tienes `adduser`, puedes instalarlo en Ubuntu/Debian con:

```bash
sudo apt install adduser
```

En RHEL/CentOS/Fedora:

```bash
sudo dnf install util-linux-user
```

---

### ✅ EJEMPLO COMPLETO: Crear, modificar y eliminar usuarios

#### 🎯 Objetivo:

Crear un usuario `gustavo`, cambiarle la contraseña, asignarle un nuevo shell, añadirlo a un grupo y eliminarlo al final.

---

#### Paso 1: Crear usuario

```bash
sudo adduser gustavo
```

Sigue las instrucciones (nombre completo, contraseña, etc.).

---

#### Paso 2: Ver información

```bash
id gustavo
```

Verifica su UID, GID y grupos.

---

#### Paso 3: Cambiar su shell

```bash
sudo usermod -s /bin/bash gustavo
```

Puedes verificar con:

```bash
grep gustavo /etc/passwd
```

---

#### Paso 4: Crear grupo y asignar

```bash
sudo groupadd desarrolladores
sudo usermod -aG desarrolladores gustavo
```

Verifica con:

```bash
groups gustavo
```

---

#### Paso 5: Bloquear y desbloquear

```bash
sudo usermod -L gustavo   # Bloquear
sudo usermod -U gustavo   # Desbloquear
```

---

#### Paso 6: Eliminar usuario

```bash
sudo deluser --remove-home gustavo
```

---

### 🧠 RESUMEN RÁPIDO

| Tarea              | Comando                              |
| ------------------ | ------------------------------------ |
| Crear usuario      | `sudo adduser nombre`                |
| Ver usuario        | `id nombre`                          |
| Cambiar contraseña | `sudo passwd nombre`                 |
| Cambiar shell      | `sudo usermod -s /ruta/shell nombre` |
| Añadir a grupo     | `sudo usermod -aG grupo nombre`      |
| Eliminar usuario   | `sudo deluser --remove-home nombre`  |

---

[🔼](#índice)

---

## **648. Manejo de grupos**

### 🧑‍🤝‍🧑 ¿Qué es el manejo de grupos en Linux?

En Linux, un **grupo** es una forma de reunir a varios usuarios bajo una misma categoría para **compartir permisos**, **archivos**, y **acceso a recursos**. Esto simplifica la administración: en lugar de dar permisos usuario por usuario, puedes asignarlos a todo un grupo.

---

### 🧠 ¿Por qué es útil?

Por ejemplo:

- Tienes un grupo llamado `desarrolladores`.
- Todos los usuarios dentro de ese grupo pueden leer y escribir en el directorio `/proyectos`.
- Si entra un nuevo desarrollador, solo lo añades al grupo, ¡y listo! Tiene acceso como los demás.

---

### 📁 Archivos relacionados con grupos

- `/etc/group`: Lista los grupos del sistema.
- `/etc/gshadow`: Almacena contraseñas de grupos (si se usan).

Puedes ver el contenido así:

```bash
cat /etc/group
```

---

### 📦 ¿Cómo se instala?

**No necesitas instalar nada.** Las herramientas para manejar grupos vienen integradas en Linux:

- `groupadd`, `groupdel`, `groupmod`
- `usermod`, `gpasswd`

Si por alguna razón no están, puedes instalar el paquete `passwd` o `util-linux`:

```bash
# En Debian/Ubuntu
sudo apt install passwd

# En RedHat/Fedora
sudo dnf install util-linux-user
```

---

### 🛠️ Comandos para manejo de grupos

#### 🔸 1. **Crear un grupo**

```bash
sudo groupadd desarrolladores
```

Esto crea un nuevo grupo llamado `desarrolladores`.

---

#### 🔸 2. **Ver todos los grupos**

```bash
getent group
```

o

```bash
cut -d: -f1 /etc/group
```

---

#### 🔸 3. **Ver grupos de un usuario**

```bash
groups gustavo
```

o

```bash
id gustavo
```

---

#### 🔸 4. **Agregar un usuario a un grupo (secundario)**

```bash
sudo usermod -aG desarrolladores gustavo
```

> ⚠️ Usa `-aG` para _añadir_ sin eliminar grupos existentes.

---

#### 🔸 5. **Cambiar grupo principal de un usuario**

```bash
sudo usermod -g desarrolladores gustavo
```

> El grupo principal es el que se usa por defecto para nuevos archivos.

---

#### 🔸 6. **Eliminar un usuario de un grupo (manualmente)**

Edita el archivo `/etc/group` o usa `gpasswd`:

```bash
sudo gpasswd -d gustavo desarrolladores
```

---

#### 🔸 7. **Eliminar un grupo**

```bash
sudo groupdel desarrolladores
```

---

#### 🔸 8. **Cambiar nombre de un grupo**

```bash
sudo groupmod -n nuevo_nombre desarrolladores
```

---

### ✅ EJEMPLO COMPLETO: Crear, asignar y gestionar grupos

#### 🎯 Objetivo:

Crear un grupo de trabajo llamado `proyectoX`, añadir usuarios, dar permisos a un directorio, y luego eliminar todo.

---

#### Paso 1: Crear grupo

```bash
sudo groupadd proyectoX
```

---

#### Paso 2: Crear usuarios

```bash
sudo adduser ana
sudo adduser luis
```

---

#### Paso 3: Añadir usuarios al grupo

```bash
sudo usermod -aG proyectoX ana
sudo usermod -aG proyectoX luis
```

Verifica:

```bash
groups ana
groups luis
```

---

#### Paso 4: Crear un directorio compartido

```bash
sudo mkdir /home/proyectoX
```

Asignar grupo propietario:

```bash
sudo chown :proyectoX /home/proyectoX
```

Dar permisos al grupo:

```bash
sudo chmod 770 /home/proyectoX
```

Ahora, solo miembros del grupo `proyectoX` pueden entrar y modificar archivos ahí.

---

#### Paso 5: Verificar permisos

```bash
ls -ld /home/proyectoX
```

Debe mostrar:

```
drwxrwx--- 2 root proyectoX 4096 jul 23 17:00 /home/proyectoX
```

---

#### Paso 6: Eliminar grupo y limpiar

```bash
sudo deluser ana proyectoX
sudo deluser luis proyectoX
sudo groupdel proyectoX
```

---

### 🧠 RESUMEN DE COMANDOS

| Tarea                     | Comando                          |
| ------------------------- | -------------------------------- |
| Crear grupo               | `sudo groupadd nombre`           |
| Ver grupos de un usuario  | `groups usuario`                 |
| Añadir usuario a grupo    | `sudo usermod -aG grupo usuario` |
| Cambiar grupo principal   | `sudo usermod -g grupo usuario`  |
| Eliminar usuario de grupo | `sudo gpasswd -d usuario grupo`  |
| Eliminar grupo            | `sudo groupdel grupo`            |
| Ver grupos del sistema    | `getent group`                   |

---

[🔼](#índice)

---

## **649. El control de accesos en Linux**

### 🧠 ¿Qué es el control de accesos?

El **control de accesos** en Linux es el **sistema que define quién puede hacer qué con cada archivo, carpeta, proceso o recurso**. Se basa en **usuarios, grupos y permisos**. Es esencial para la **seguridad y privacidad** en un sistema multiusuario.

---

### 📦 ¿Se instala?

No es necesario instalar nada. Linux **ya incluye todo lo necesario** para gestionar el control de accesos, usando:

- El sistema de permisos tradicionales (`rwx`)
- Comandos como `chmod`, `chown`, `chgrp`
- Herramientas para ACL (Listas de control de acceso avanzadas)
- El archivo `/etc/sudoers` para privilegios administrativos

---

### 🧱 Conceptos base

#### 🧍 Usuario (owner)

Es el **propietario** del archivo. Generalmente, quien lo crea.

#### 👥 Grupo

Conjunto de usuarios que pueden compartir ciertos permisos.

#### 🌐 Otros

El **resto de usuarios** del sistema.

---

### 🔐 Permisos básicos

Los permisos en Linux se expresan con tres letras:

| Letra | Significado        | Aplica a                                                |
| ----- | ------------------ | ------------------------------------------------------- |
| `r`   | read (leer)        | Archivos: ver contenido. Carpetas: listar contenido.    |
| `w`   | write (escribir)   | Archivos: modificar. Carpetas: crear/eliminar archivos. |
| `x`   | execute (ejecutar) | Archivos: ejecutarlos. Carpetas: entrar a ellas.        |

Se agrupan en tres bloques:

```
-rwxr-xr--
  ||| |||
  ||| ||└─→ Permisos para "otros"
  ||| └──→ Permisos para "grupo"
  └──→ Permisos para "usuario"
```

---

### 🛠️ Comandos para manejar permisos y accesos

#### 🔸 1. Ver permisos

```bash
ls -l archivo.txt
```

Ejemplo de salida:

```
-rw-r--r-- 1 gustavo gustavo 123 jul 23 15:00 archivo.txt
```

→ `gustavo` es el usuario y grupo dueño.

---

#### 🔸 2. Cambiar permisos (`chmod`)

```bash
chmod [opciones] archivo
```

##### Ejemplos:

```bash
chmod u+x script.sh    # Añadir permiso de ejecución al usuario
chmod g-w archivo.txt  # Quitar permiso de escritura al grupo
chmod o=r archivo.txt  # Otros solo podrán leer
```

Forma numérica (`r=4, w=2, x=1`):

```bash
chmod 755 archivo.sh
```

\| 7 (u) = rwx | 5 (g) = r-x | 5 (o) = r-x |

---

#### 🔸 3. Cambiar propietario (`chown`)

```bash
sudo chown nuevo_usuario archivo
```

Ejemplo:

```bash
sudo chown gustavo documento.txt
```

---

#### 🔸 4. Cambiar grupo (`chgrp`)

```bash
sudo chgrp desarrolladores proyecto/
```

---

#### 🔸 5. Permisos avanzados: ACL (opcional)

Para asignar permisos más finos:

1. Habilita ACL en el sistema de archivos (ya viene en ext4).
2. Usa `setfacl` y `getfacl`.

Ejemplo:

```bash
setfacl -m u:ana:rw archivo.txt
getfacl archivo.txt
```

---

#### 🔸 6. Privilegios de superusuario (sudo)

Los usuarios definidos en `/etc/sudoers` pueden usar `sudo` para ejecutar comandos como administrador.

```bash
sudo visudo
```

Agrega una línea como:

```bash
gustavo ALL=(ALL) NOPASSWD: ALL
```

---

### ✅ EJEMPLO COMPLETO: Control de accesos para un proyecto compartido

🎯 Objetivo: Crear un directorio llamado `/proyecto`, accesible solo por miembros del grupo `equipo`.

---

#### 🔹 Paso 1: Crear grupo y usuarios

```bash
sudo groupadd equipo
sudo useradd ana
sudo useradd luis
sudo usermod -aG equipo ana
sudo usermod -aG equipo luis
```

---

#### 🔹 Paso 2: Crear directorio

```bash
sudo mkdir /proyecto
```

---

#### 🔹 Paso 3: Asignar grupo y permisos

```bash
sudo chown :equipo /proyecto
sudo chmod 770 /proyecto
```

✅ Esto permite acceso **completo** a los usuarios del grupo `equipo` y **ningún acceso** al resto.

---

#### 🔹 Paso 4: Verificar

```bash
ls -ld /proyecto
```

Salida esperada:

```
drwxrwx--- 2 root equipo 4096 jul 23 16:00 /proyecto
```

---

#### 🔹 Paso 5 (opcional): Forzar archivos nuevos con grupo heredado

```bash
sudo chmod g+s /proyecto
```

---

### 🧠 Resumen de comandos

| Acción              | Comando                             |
| ------------------- | ----------------------------------- |
| Ver permisos        | `ls -l archivo`                     |
| Cambiar permisos    | `chmod 755 archivo`                 |
| Cambiar propietario | `chown usuario archivo`             |
| Cambiar grupo       | `chgrp grupo archivo`               |
| Ver ACL             | `getfacl archivo`                   |
| Asignar ACL         | `setfacl -m u:usuario:perm archivo` |

---

### 📌 Conclusión

El control de accesos en Linux es la base de la seguridad del sistema. Dominar `chmod`, `chown`, `chgrp`, `sudo` y ACL te permite controlar quién puede hacer qué. Es fundamental para proteger archivos, gestionar proyectos y mantener el sistema ordenado.

---

[🔼](#índice)

---

## **650. Creación de un usuario administrador**

### 👤 ¿Qué es un usuario administrador en Linux?

En Linux, **el usuario administrador** es aquel que puede realizar tareas privilegiadas en el sistema (instalar software, crear usuarios, cambiar configuraciones, etc.). Por defecto, ese usuario es **root**, pero **se puede crear otro usuario y darle privilegios de administrador** usando `sudo`.

---

### 🛠️ ¿Se necesita instalar algo?

En la mayoría de distribuciones (como Ubuntu, Debian, RHEL, Fedora), **el comando `sudo` ya viene instalado**.

Si por alguna razón no está instalado (como en algunas versiones mínimas), puedes instalarlo:

#### 🔸 En sistemas basados en Debian/Ubuntu:

```bash
sudo apt update
sudo apt install sudo
```

#### 🔸 En sistemas basados en RHEL/CentOS/Fedora:

```bash
sudo dnf install sudo  # Fedora/RHEL 8+
```

---

### ✅ Pasos para crear un usuario administrador

#### 🔹 Paso 1: Crear un nuevo usuario

```bash
sudo adduser gussadmin
```

> Esto crea al usuario y te pedirá establecer una contraseña.

---

#### 🔹 Paso 2: Añadirlo al grupo `sudo` (o `wheel` en RHEL)

- En **Ubuntu/Debian**, los usuarios que están en el grupo `sudo` tienen privilegios de administrador:

```bash
sudo usermod -aG sudo gussadmin
```

- En **RedHat, CentOS y Fedora**, se usa el grupo `wheel`:

```bash
sudo usermod -aG wheel gussadmin
```

---

#### 🔹 Paso 3: Verificar que el usuario tiene permisos

Puedes iniciar sesión como ese usuario:

```bash
su - gussadmin
```

Y luego probar un comando con privilegios:

```bash
sudo whoami
```

Si todo está bien, debe decir:

```
root
```

---

### 🧠 Explicación rápida de los comandos usados

| Comando        | Qué hace                                     |
| -------------- | -------------------------------------------- |
| `adduser`      | Crea un nuevo usuario                        |
| `usermod -aG`  | Añade el usuario a un grupo                  |
| `sudo`         | Permite ejecutar comandos como administrador |
| `su - usuario` | Cambia al usuario indicado                   |
| `whoami`       | Muestra el nombre del usuario actual         |

---

### 🧪 EJEMPLO COMPLETO

🎯 **Objetivo**: Crear un usuario llamado `adminprueba` con privilegios administrativos en Ubuntu.

---

#### 🔸 1. Crear el usuario

```bash
sudo adduser adminprueba
```

👀 Te pedirá la contraseña y algunos datos (puedes dejarlos en blanco si gustas).

---

#### 🔸 2. Añadir al grupo sudo

```bash
sudo usermod -aG sudo adminprueba
```

---

#### 🔸 3. Probar el acceso

```bash
su - adminprueba
sudo apt update
```

✅ Si te pide contraseña y el comando se ejecuta, ¡ya es administrador!

---

### 🔐 (Opcional) Revisión del archivo sudoers

Si deseas revisar cómo el grupo `sudo` tiene permisos, puedes ver el archivo `/etc/sudoers` de forma segura con:

```bash
sudo visudo
```

Allí verás una línea como:

```bash
%sudo   ALL=(ALL:ALL) ALL
```

Esto significa: todos los miembros del grupo `sudo` pueden usar `sudo`.

---

### 📌 Conclusión

Crear un usuario administrador en Linux es fácil, pero **muy importante para la seguridad**. Te permite no depender del usuario `root` directamente, lo cual es una **buena práctica recomendada**.

---

[🔼](#índice)

---

## **651. Particionando y montando una unidad**

### 🧠 ¿Qué significa "particionar y montar una unidad"?

#### 🔹 Particionar:

Dividir un disco (por ejemplo `/dev/sdb`) en secciones llamadas **particiones**, como si dividiras un cuaderno en capítulos. Esto permite que el sistema las trate como unidades independientes: `/dev/sdb1`, `/dev/sdb2`, etc.

#### 🔹 Montar:

Es el proceso de **hacer accesible una partición** en el sistema de archivos. Cuando montas una unidad, puedes acceder a su contenido desde una carpeta (como `/mnt/disco1` o `/home`).

---

### 🛠️ ¿Qué se necesita?

- Un disco duro o unidad externa **sin usar** (por ejemplo, `/dev/sdb`).
- Privilegios de **administrador** (`sudo`).
- Herramientas como `fdisk`, `mkfs` y `mount` (vienen por defecto en la mayoría de distros).

---

### 🪜 PASOS para particionar y montar una unidad

---

#### 🔸 Paso 1: Identificar el disco

Usa el siguiente comando:

```bash
lsblk
```

Salida de ejemplo:

```
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda      8:0    0   50G  0 disk
├─sda1   8:1    0   48G  0 part /
└─sda2   8:2    0    2G  0 part [SWAP]
sdb      8:16   0   10G  0 disk
```

👉 En este caso, `sdb` es un disco sin particionar.

---

#### 🔸 Paso 2: Crear una partición con `fdisk`

```bash
sudo fdisk /dev/sdb
```

Dentro de `fdisk`, haz lo siguiente:

- Presiona `n` → para nueva partición
- Presiona `p` → para partición primaria
- Presiona `1` → número de partición
- Presiona `Enter` dos veces para aceptar valores por defecto
- Presiona `w` → para escribir los cambios

✅ Esto crea `/dev/sdb1`.

---

#### 🔸 Paso 3: Formatear la partición

Una vez creada la partición, hay que darle un **sistema de archivos**, por ejemplo `ext4`:

```bash
sudo mkfs.ext4 /dev/sdb1
```

---

#### 🔸 Paso 4: Crear un punto de montaje

```bash
sudo mkdir /mnt/disco1
```

---

#### 🔸 Paso 5: Montar la partición

```bash
sudo mount /dev/sdb1 /mnt/disco1
```

Ahora puedes acceder al contenido del disco en `/mnt/disco1`.

---

#### 🔸 Paso 6: (Opcional) Montaje automático al iniciar el sistema

Edita el archivo `/etc/fstab`:

```bash
sudo nano /etc/fstab
```

Agrega al final:

```
/dev/sdb1   /mnt/disco1   ext4   defaults   0   2
```

💡 Recomendación: usa UUID en vez de `/dev/sdb1` para mayor seguridad:

```bash
sudo blkid /dev/sdb1
```

Agrega la línea usando el UUID:

```
UUID=xxxxx-xxxx-xxxx-xxxx   /mnt/disco1   ext4   defaults   0   2
```

---

### 🔧 COMANDOS RESUMIDOS

| Comando          | Propósito                         |
| ---------------- | --------------------------------- |
| `lsblk`          | Ver discos disponibles            |
| `fdisk /dev/sdX` | Particionar el disco              |
| `mkfs.ext4`      | Formatear la partición            |
| `mkdir`          | Crear directorio de montaje       |
| `mount`          | Montar la partición               |
| `blkid`          | Ver UUID de las particiones       |
| `/etc/fstab`     | Archivo para montajes automáticos |

---

### 🧪 EJEMPLO COMPLETO

🎯 Quiero particionar y montar el disco `/dev/sdb` en `/mnt/usbdata`.

---

#### 1. Ver discos:

```bash
lsblk
```

Veo que `/dev/sdb` está libre.

---

#### 2. Particionar:

```bash
sudo fdisk /dev/sdb
```

Dentro de `fdisk`:

- `n` → nueva partición
- `p` → primaria
- `1` → número
- Enter → por defecto
- Enter
- `w` → guardar

---

#### 3. Formatear:

```bash
sudo mkfs.ext4 /dev/sdb1
```

---

#### 4. Crear carpeta de montaje:

```bash
sudo mkdir /mnt/usbdata
```

---

#### 5. Montar la partición:

```bash
sudo mount /dev/sdb1 /mnt/usbdata
```

---

#### 6. Verificar:

```bash
df -h
```

Verás que `/dev/sdb1` está montado en `/mnt/usbdata`.

---

### ✅ Conclusión

Has aprendido:

- Qué es particionar y montar.
- Cómo hacerlo paso a paso.
- Cómo asegurarte que se monte automáticamente.
- Qué comandos necesitas.

---

[🔼](#índice)

---

## **652. ¿Qué es RAID y LVM?**

### 📌 ¿Qué es RAID?

#### ✅ RAID = _Redundant Array of Independent Disks_

RAID es una **tecnología de almacenamiento** que combina múltiples discos duros físicos en una **unidad lógica** para mejorar el **rendimiento**, la **redundancia** o ambos.

#### 🎯 ¿Para qué sirve RAID?

- 💾 **Redundancia:** Si un disco falla, los datos no se pierden (según el nivel de RAID).
- ⚡ **Rendimiento:** Varios discos pueden trabajar al mismo tiempo.
- 📊 **Espacio combinado:** Puedes unir varios discos para que se comporten como uno solo.

---

#### 🔢 Tipos comunes de RAID

| Nivel RAID | Descripción                                  | Ventaja               | Desventaja                         |
| ---------- | -------------------------------------------- | --------------------- | ---------------------------------- |
| RAID 0     | Divide los datos entre los discos (striping) | Velocidad ⚡          | No hay copia de seguridad ❌       |
| RAID 1     | Copia exacta en 2 discos (mirroring)         | Seguridad 🛡️          | Solo usas el 50% del total         |
| RAID 5     | Distribuye datos y paridad (mínimo 3 discos) | Equilibrio 🧠         | Si fallan 2 discos, se pierde todo |
| RAID 10    | Combinación de RAID 1 + RAID 0               | Seguridad + Velocidad | Se necesitan mínimo 4 discos       |

> RAID puede ser por **hardware** (controladora RAID física) o **software** (configurado por el sistema operativo, por ejemplo con `mdadm` en Linux).

---

### 📌 ¿Qué es LVM?

#### ✅ LVM = _Logical Volume Manager_

LVM es un sistema de administración de volúmenes que permite gestionar **espacio de disco flexible**.

#### 🎯 ¿Para qué sirve LVM?

- 📏 **Redimensionar particiones fácilmente** (aumentar o reducir).
- 📦 **Combinar varios discos** en uno solo (volúmenes lógicos).
- 🧩 **Snapshots:** crear copias rápidas de volúmenes para respaldos.

---

#### 🧱 Jerarquía de LVM

1. **PV (Physical Volume):** Disco o partición real.
2. **VG (Volume Group):** Grupo de volúmenes físicos.
3. **LV (Logical Volume):** Partición lógica donde se guarda la info.

---

### 🔧 ¿Cómo se instala y configura RAID y LVM?

#### 🧰 Herramientas necesarias

- `mdadm` para RAID (RAID por software)
- `lvm2` para LVM

---

### ✅ Instalación de herramientas

```bash
sudo apt update
sudo apt install mdadm lvm2 -y
```

---

### 🧪 EJEMPLO COMPLETO (RAID 1 + LVM)

🎯 Objetivo: Crear un RAID 1 con dos discos `/dev/sdb` y `/dev/sdc`, y usar ese RAID como volumen físico para LVM.

---

#### 🔹 Paso 1: Identificar discos

```bash
lsblk
```

Verifica que `/dev/sdb` y `/dev/sdc` estén vacíos.

---

#### 🔹 Paso 2: Crear RAID 1

```bash
sudo mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sdb /dev/sdc
```

💡 `/dev/md0` será el nuevo RAID.

Verifica estado:

```bash
cat /proc/mdstat
```

---

#### 🔹 Paso 3: Crear volumen físico (PV) en RAID

```bash
sudo pvcreate /dev/md0
```

---

#### 🔹 Paso 4: Crear grupo de volumen (VG)

```bash
sudo vgcreate vgdatos /dev/md0
```

---

#### 🔹 Paso 5: Crear volumen lógico (LV)

```bash
sudo lvcreate -L 5G -n lvbackup vgdatos
```

---

#### 🔹 Paso 6: Formatear el volumen lógico

```bash
sudo mkfs.ext4 /dev/vgdatos/lvbackup
```

---

#### 🔹 Paso 7: Montar el volumen

```bash
sudo mkdir /mnt/lvbackup
sudo mount /dev/vgdatos/lvbackup /mnt/lvbackup
```

Verificar:

```bash
df -h
```

---

### 🎉 ¡Listo!

Ahora tienes:

- Un **RAID 1** configurado para proteger tus datos.
- Un **volumen lógico LVM** encima del RAID.
- Flexibilidad de crecer el espacio o hacer copias sin interrupciones.

---

### 📌 ¿Cuándo usar RAID o LVM?

| Escenario                                     | Solución recomendada  |
| --------------------------------------------- | --------------------- |
| Quieres proteger datos frente a fallos        | RAID 1 o RAID 5       |
| Quieres agrupar varios discos en uno solo     | LVM                   |
| Quieres redimensionar particiones en caliente | LVM                   |
| Quieres respaldo + flexibilidad               | RAID + LVM combinados |

---

[🔼](#índice)

---

## **653. Creacion de sistema RAID 1**

### 🧠 ¿Qué es RAID 1?

**RAID 1** es un tipo de RAID llamado **"mirroring"** (espejo).

> 🚨 Lo que se escribe en un disco se copia automáticamente en el otro disco.

#### ✅ Ventajas:

- Si uno de los discos falla, el otro tiene **una copia exacta** de todos los datos.
- Muy útil para servidores donde la **integridad de los datos** es crítica.

#### ❌ Desventajas:

- Se pierde el 50% del espacio total. Si usas 2 discos de 500 GB, solo tendrás 500 GB útiles.

---

### 🧰 Requisitos previos

- 2 discos duros (reales o virtuales), vacíos y del **mismo tamaño**, por ejemplo: `/dev/sdb` y `/dev/sdc`.
- Linux instalado (por ejemplo, Ubuntu Server).
- Acceso como superusuario (`sudo`).

---

### 🔧 Instalación de herramienta RAID por software: `mdadm`

```bash
sudo apt update
sudo apt install mdadm -y
```

> `mdadm` es la herramienta que permite crear y administrar RAID por software en Linux.

---

### ✅ PASOS para crear RAID 1

#### 🔹 1. Verifica los discos disponibles

```bash
lsblk
```

Debes ver algo como:

```
sda     20G
├─sda1  512M
└─sda2  19.5G
sdb     10G
sdc     10G
```

🧠 Asegúrate de que `sdb` y `sdc` estén vacíos.

---

#### 🔹 2. Limpia los discos (opcional, pero recomendado)

```bash
sudo wipefs -a /dev/sdb
sudo wipefs -a /dev/sdc
```

---

#### 🔹 3. Crear el RAID 1

```bash
sudo mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sdb /dev/sdc
```

📌 Explicación:

- `--create` → Crea un nuevo RAID.
- `/dev/md0` → Nombre del RAID.
- `--level=1` → RAID 1 (espejo).
- `--raid-devices=2` → Dos discos.

---

#### 🔹 4. Confirmar el estado del RAID

```bash
cat /proc/mdstat
```

🔍 Deberías ver algo como:

```
md0 : active raid1 sdb[0] sdc[1]
      10465280 blocks super 1.2 [2/2] [UU]
```

✅ Si ves `[UU]`, ¡el RAID está activo y ambos discos están sincronizados!

---

#### 🔹 5. Crear archivo de configuración (opcional, pero recomendado)

Esto ayuda a que el RAID se monte automáticamente al reiniciar.

```bash
sudo mdadm --detail --scan | sudo tee -a /etc/mdadm/mdadm.conf
sudo update-initramfs -u
```

---

#### 🔹 6. Crear sistema de archivos

Formateamos el RAID con `ext4` para poder usarlo:

```bash
sudo mkfs.ext4 /dev/md0
```

---

#### 🔹 7. Montar el RAID en un directorio

```bash
sudo mkdir /mnt/raid1
sudo mount /dev/md0 /mnt/raid1
```

---

#### 🔹 8. Verificar que está montado

```bash
df -h
```

Deberías ver una línea como:

```
/dev/md0       9.8G  ...  /mnt/raid1
```

---

#### 🔹 9. Montar automáticamente al iniciar (fstab)

Editamos el archivo `/etc/fstab`:

```bash
sudo nano /etc/fstab
```

Agrega al final:

```bash
/dev/md0   /mnt/raid1   ext4   defaults   0   0
```

---

### 🎉 EJEMPLO COMPLETO RESUMIDO

```bash
# Instalar mdadm
sudo apt install mdadm -y

# Limpieza de discos
sudo wipefs -a /dev/sdb
sudo wipefs -a /dev/sdc

# Crear RAID 1
sudo mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sdb /dev/sdc

# Verificar estado
cat /proc/mdstat

# Configuración permanente
sudo mdadm --detail --scan | sudo tee -a /etc/mdadm/mdadm.conf
sudo update-initramfs -u

# Crear sistema de archivos
sudo mkfs.ext4 /dev/md0

# Montar el RAID
sudo mkdir /mnt/raid1
sudo mount /dev/md0 /mnt/raid1

# Agregar al fstab
echo '/dev/md0 /mnt/raid1 ext4 defaults 0 0' | sudo tee -a /etc/fstab
```

---

### 📌 ¿Cómo probar que funciona?

Puedes crear un archivo en `/mnt/raid1`:

```bash
sudo touch /mnt/raid1/test.txt
```

Luego apaga la máquina, desconecta un disco (por ejemplo, `/dev/sdc`), y vuelve a iniciar. El RAID seguirá funcionando con solo un disco. Esa es la **magia de RAID 1**.

---

[🔼](#índice)

---

## **654. Creación de LVM sobre RAID 1**

### 🧠 ¿Qué es LVM sobre RAID 1?

#### 🔸 RAID 1:

Es un sistema que **duplica los datos** en 2 discos (mirroring), lo que permite **tolerancia a fallos**: si un disco se rompe, el otro tiene todos los datos.

#### 🔸 LVM (Logical Volume Manager):

Es un sistema que permite **administrar el almacenamiento de forma flexible**, con cosas como:

- Redimensionar particiones "al vuelo".
- Crear snapshots.
- Agregar más discos fácilmente.

#### 🔸 ¿Por qué combinarlos?

Porque RAID 1 te da **redundancia** (protección contra fallos), y LVM te da **flexibilidad de manejo de espacio**.

---

### 🛠️ Estructura que vamos a crear:

```
/dev/sdb   \
            > RAID 1 --> /dev/md0 --> PV --> VG --> LV --> Sistema de archivos --> Punto de montaje
/dev/sdc   /
```

---

### ✅ Requisitos

- Dos discos vacíos (ej. `/dev/sdb` y `/dev/sdc`)
- Sistema Linux con privilegios root
- Herramientas:

  - `mdadm` (para RAID)
  - `lvm2` (para LVM)

---

### 🔧 Instalación de herramientas

```bash
sudo apt update
sudo apt install mdadm lvm2 -y
```

---

### 🪜 PASOS: Crear LVM sobre RAID 1

#### 1️⃣ Limpiar los discos (opcional pero recomendable)

```bash
sudo wipefs -a /dev/sdb
sudo wipefs -a /dev/sdc
```

---

#### 2️⃣ Crear RAID 1

```bash
sudo mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sdb /dev/sdc
```

🔍 Verifica el estado:

```bash
cat /proc/mdstat
```

✅ Si ves `[UU]`, ¡está bien sincronizado!

---

#### 3️⃣ Crear volumen físico LVM sobre RAID

```bash
sudo pvcreate /dev/md0
```

---

#### 4️⃣ Crear un grupo de volúmenes (VG)

```bash
sudo vgcreate vg_raid1 /dev/md0
```

Puedes nombrarlo como desees, aquí usamos `vg_raid1`.

---

#### 5️⃣ Crear volumen lógico (LV)

```bash
sudo lvcreate -L 5G -n lv_datos vg_raid1
```

- `-L 5G`: tamaño
- `-n lv_datos`: nombre del volumen lógico
- `vg_raid1`: grupo al que pertenece

---

#### 6️⃣ Formatear el volumen lógico

```bash
sudo mkfs.ext4 /dev/vg_raid1/lv_datos
```

---

#### 7️⃣ Montar el sistema de archivos

```bash
sudo mkdir /mnt/datos
sudo mount /dev/vg_raid1/lv_datos /mnt/datos
```

---

#### 8️⃣ Montaje permanente en fstab

Primero obtenemos el UUID:

```bash
sudo blkid /dev/vg_raid1/lv_datos
```

Copia el UUID y edita el fstab:

```bash
sudo nano /etc/fstab
```

Agrega una línea como esta:

```
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /mnt/datos ext4 defaults 0 2
```

---

### 📦 EJEMPLO COMPLETO RESUMIDO

```bash
# 1. Instalar herramientas
sudo apt install mdadm lvm2 -y

# 2. Limpiar discos
sudo wipefs -a /dev/sdb
sudo wipefs -a /dev/sdc

# 3. Crear RAID 1
sudo mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sdb /dev/sdc

# 4. Confirmar RAID
cat /proc/mdstat

# 5. Crear PV sobre /dev/md0
sudo pvcreate /dev/md0

# 6. Crear VG
sudo vgcreate vg_raid1 /dev/md0

# 7. Crear LV
sudo lvcreate -L 5G -n lv_datos vg_raid1

# 8. Formatear y montar
sudo mkfs.ext4 /dev/vg_raid1/lv_datos
sudo mkdir /mnt/datos
sudo mount /dev/vg_raid1/lv_datos /mnt/datos

# 9. Agregar a fstab
sudo blkid /dev/vg_raid1/lv_datos  # Copiar UUID
sudo nano /etc/fstab
# Agregar línea: UUID=... /mnt/datos ext4 defaults 0 2
```

---

### 🧪 ¿Cómo lo pruebas?

1. Copia un archivo grande a `/mnt/datos`:

```bash
sudo dd if=/dev/zero of=/mnt/datos/test.img bs=1M count=100
```

2. Verifica que está allí:

```bash
ls -lh /mnt/datos/
```

3. Puedes simular un fallo desconectando un disco, y RAID 1 seguirá funcionando. Luego puedes añadir un disco nuevo al RAID (si quieres te puedo enseñar cómo hacer eso también).

---

[🔼](#índice)

---

## **655. Agregando el sistema a fstab**

### 🧠 ¿Qué es el archivo `fstab`?

`fstab` (File System Table) es un archivo del sistema que se encuentra en:

```
/etc/fstab
```

Y su función es **indicarle al sistema qué sistemas de archivos montar automáticamente al iniciar**.

#### 🧩 En resumen:

- Es como una "agenda" para decirle a Linux:

  > “Monta esta partición/disco en esta carpeta cada vez que inicie.”

---

### 📝 Formato de una línea en `fstab`

Cada línea del archivo tiene esta forma:

```bash
<dispositivo>   <punto_de_montaje>   <tipo_fs>   <opciones>   <dump>   <pass>
```

#### 🔍 Ejemplo:

```
UUID=5c327a02-5ed7-4e00-bbe1-e9e21a445f6e   /mnt/datos   ext4   defaults   0   2
```

#### 📕 Desglose:

| Campo        | Descripción                                                                |
| ------------ | -------------------------------------------------------------------------- |
| `UUID`       | Identificador único del disco o partición (más seguro que usar `/dev/sdX`) |
| `/mnt/datos` | Carpeta donde se montará                                                   |
| `ext4`       | Tipo de sistema de archivos                                                |
| `defaults`   | Opciones comunes: lectura/escritura, auto-montado, etc.                    |
| `0`          | Dump (para respaldo, suele ser 0)                                          |
| `2`          | fsck: orden de chequeo. `1` para root, `2` para otros sistemas             |

---

### 🔧 ¿Cómo saber el UUID de un disco o volumen?

Usa este comando:

```bash
sudo blkid
```

🔁 Ejemplo de salida:

```
/dev/vg_raid1/lv_datos: UUID="5c327a02-5ed7-4e00-bbe1-e9e21a445f6e" TYPE="ext4"
```

---

### ✅ ¿Cómo agregar un disco al `fstab`?

#### Ejemplo práctico: tienes un volumen lógico LVM montado en `/mnt/datos`.

---

#### 🪜 PASO A PASO

##### 1️⃣ Verifica que el disco o volumen esté montado y funcionando:

```bash
df -h
```

Busca la línea con `/mnt/datos` (o el punto de montaje que uses).

---

##### 2️⃣ Encuentra el UUID

```bash
sudo blkid /dev/vg_raid1/lv_datos
```

Salida esperada:

```
/dev/vg_raid1/lv_datos: UUID="5c327a02-5ed7-4e00-bbe1-e9e21a445f6e" TYPE="ext4"
```

---

##### 3️⃣ Edita el archivo `fstab`

```bash
sudo nano /etc/fstab
```

Agrega al final esta línea:

```
UUID=5c327a02-5ed7-4e00-bbe1-e9e21a445f6e   /mnt/datos   ext4   defaults   0   2
```

---

##### 4️⃣ Guarda y prueba sin reiniciar:

```bash
sudo mount -a
```

🔎 Si **no sale ningún error**, todo está bien configurado.

Puedes verificar con:

```bash
df -h | grep datos
```

---

### ❗ Tips importantes

- Siempre haz **una copia de seguridad de `fstab`** antes de editarlo:

```bash
sudo cp /etc/fstab /etc/fstab.bak
```

- Si escribes mal una línea, podrías hacer que el sistema **no arranque** correctamente. Por eso es útil probar con `mount -a`.

---

### 📦 EJEMPLO COMPLETO DE AGREGAR UN DISCO

Supongamos que tienes un volumen lógico montado en `/mnt/backup`, y quieres montarlo siempre al iniciar.

#### 🧩 Paso a paso:

1. Verifica el volumen:

```bash
sudo mount /dev/vg_data/lv_backup /mnt/backup
```

2. Encuentra el UUID:

```bash
sudo blkid /dev/vg_data/lv_backup
```

Supón que el UUID es:

```
UUID=abcd1234-ef56-7890-abcd-1234567890ef
```

3. Edita el archivo:

```bash
sudo nano /etc/fstab
```

Agrega al final:

```
UUID=abcd1234-ef56-7890-abcd-1234567890ef   /mnt/backup   ext4   defaults   0   2
```

4. Monta sin reiniciar para validar:

```bash
sudo mount -a
```

---

### 📌 ¿Qué pasa si reinicias?

Linux leerá `/etc/fstab` y montará automáticamente el volumen en `/mnt/backup` sin que tú hagas nada más.

---

### ✅ Resultado final

Tu disco, volumen o partición se montará automáticamente cada vez que inicies el sistema, evitando que tengas que hacerlo manualmente.

---

[🔼](#índice)

---

## **656. Preparando el sistema**

### 🧠 ¿Qué significa "preparar el sistema"?

**Preparar el sistema** es realizar una serie de configuraciones básicas e importantes **después de instalar el sistema operativo**, para que esté listo para trabajar como servidor, ya sea web, base de datos, o cualquier otro uso.

---

### ⚙️ ¿Qué incluye la preparación del sistema?

Aquí te detallo las acciones más comunes (y necesarias):

1. 🔄 **Actualizar el sistema operativo**
2. 👤 **Crear un nuevo usuario con privilegios de administrador (sudo)**
3. 🔒 **Configurar firewall y seguridad básica (como SSH)**
4. 📦 **Instalar paquetes básicos y utilidades**
5. 🧭 **Establecer zona horaria y nombre del host**
6. 💽 **Configurar almacenamiento si hay discos extra**
7. 🧹 **Eliminar software innecesario**

---

### 🪜 PASO A PASO: Preparando un sistema Linux

Imaginemos que instalaste **Ubuntu Server 22.04** o **RHEL 9**, y ahora vas a preparar tu sistema.

---

#### 1️⃣ Actualiza el sistema

> Esto garantiza que tienes los últimos parches de seguridad.

**Ubuntu/Debian:**

```bash
sudo apt update && sudo apt upgrade -y
```

**Red Hat/CentOS/RHEL:**

```bash
sudo dnf update -y
```

---

#### 2️⃣ Crear un nuevo usuario administrador

No es buena idea usar siempre el usuario `root`.

```bash
sudo adduser gustavo
sudo usermod -aG sudo gustavo
```

🔐 Esto te crea un usuario "gustavo" con privilegios de administrador (`sudo`).

---

#### 3️⃣ Configurar SSH seguro (opcional pero recomendado)

Abre el archivo de configuración:

```bash
sudo nano /etc/ssh/sshd_config
```

Cambia o asegura estas líneas:

```bash
PermitRootLogin no
PasswordAuthentication yes
```

Guarda con `Ctrl + O`, `Enter` y sal con `Ctrl + X`.

Reinicia SSH:

```bash
sudo systemctl restart ssh
```

---

#### 4️⃣ Instalar herramientas básicas

Estas te facilitan mucho el trabajo:

```bash
sudo apt install curl wget git net-tools htop unzip zip tree -y
```

(Usa `dnf` en RHEL)

---

#### 5️⃣ Configurar zona horaria

```bash
sudo timedatectl set-timezone America/Lima
```

Verifica con:

```bash
timedatectl
```

---

#### 6️⃣ Cambiar el nombre del host (hostname)

```bash
sudo hostnamectl set-hostname servidor-web
```

Verifica con:

```bash
hostnamectl
```

---

#### 7️⃣ Configurar firewall básico con UFW (Ubuntu)

```bash
sudo apt install ufw -y
sudo ufw allow OpenSSH
sudo ufw enable
sudo ufw status
```

En RHEL puedes usar:

```bash
sudo firewall-cmd --add-service=ssh --permanent
sudo firewall-cmd --reload
```

---

### 🧪 EJEMPLO COMPLETO

Supón que acabas de instalar **Ubuntu Server 22.04**. Ahora vamos a prepararlo con los pasos anteriores.

#### Paso 1: Iniciar sesión como root o con el usuario creado en la instalación.

```bash
ssh root@192.168.1.10
```

#### Paso 2: Actualizar el sistema

```bash
apt update && apt upgrade -y
```

#### Paso 3: Crear usuario "gustavo" y darle permisos de sudo

```bash
adduser gustavo
usermod -aG sudo gustavo
```

#### Paso 4: Instalar herramientas esenciales

```bash
apt install curl wget git net-tools htop unzip tree -y
```

#### Paso 5: Configurar zona horaria

```bash
timedatectl set-timezone America/Lima
```

#### Paso 6: Cambiar hostname

```bash
hostnamectl set-hostname servidor-web
```

#### Paso 7: Configurar y activar firewall

```bash
ufw allow OpenSSH
ufw enable
ufw status
```

---

### 📌 Resultado final

Tendrás un sistema:

✅ Actualizado

✅ Con usuario administrador distinto de root

✅ Herramientas básicas instaladas

✅ Nombre del sistema correcto

✅ Firewall activo

✅ Zona horaria correcta

¡Todo listo para instalar servicios como Apache, Nginx, MySQL, etc!

---

[🔼](#índice)

---

## **657. Escalando el sistema con chroot e instalando Grub**

### 🧠 ¿Qué es `chroot`?

`chroot` significa **"change root"**, o "cambiar raíz". Es un comando que permite crear un entorno Linux dentro del sistema, donde la raíz (`/`) es **otra carpeta** (normalmente una instalación montada en otro disco o partición).

> Esto es útil cuando tu sistema **no arranca**, pero puedes acceder al disco desde un **Live CD/USB**, para montarlo y “entrar” a él usando `chroot` como si hubieras arrancado normalmente.

---

### 🧱 ¿Qué es GRUB?

**GRUB (GRand Unified Bootloader)** es el programa que carga el sistema operativo cuando prendes tu computadora.
Si GRUB está dañado o mal configurado, **el sistema no arranca**.

---

### 🛠️ ¿Cuándo se usa esto?

- El sistema no arranca porque **se perdió GRUB**.
- Instalaste Linux, pero GRUB no detecta otros sistemas (como Windows).
- Cambiaste de disco o partición y necesitas **reinstalar el gestor de arranque**.
- Vas a **recuperar o modificar configuraciones** desde un entorno Live.

---

### ✅ Requisitos previos

- Una **USB booteable con Ubuntu Server o Desktop** (puede ser otra distro, como Debian).
- Tu **partición raíz Linux (por ejemplo `/dev/sda2`)** debe estar sana.

---

### 🪜 PASO A PASO: Escalando con `chroot` e instalando GRUB

---

#### 🔁 1. Inicia desde un Live CD/USB

1. Bootea desde un **Live USB de Ubuntu** (elige "Probar Ubuntu" o "Try Ubuntu").
2. Abre una terminal (`Ctrl + Alt + T`).

---

#### 🧩 2. Identifica tus particiones

Usa:

```bash
lsblk
```

Ejemplo de salida:

```
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
sda      8:0    0  100G  0 disk
├─sda1   8:1    0  512M  0 part /boot/efi
├─sda2   8:2    0   20G  0 part /
├─sda3   8:3    0   4G   0 part [SWAP]
```

Tu **sistema raíz** suele estar en `/dev/sda2`.

---

#### 📦 3. Monta la partición raíz

```bash
sudo mount /dev/sda2 /mnt
```

Si tienes `/boot` o `/boot/efi` separados:

```bash
sudo mount /dev/sda1 /mnt/boot/efi
```

Si tienes `/boot` separado también:

```bash
sudo mount /dev/sdaX /mnt/boot
```

---

#### 🔧 4. Monta los sistemas necesarios para `chroot`

```bash
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
```

---

#### 🌀 5. Entra al entorno `chroot`

```bash
sudo chroot /mnt
```

Ahora estás “dentro” del sistema como si lo hubieras arrancado.

---

#### 🧱 6. Instalar GRUB

Primero asegúrate de que `grub` esté instalado:

```bash
grub-install /dev/sda
```

> ⚠️ Asegúrate de **instalar GRUB en el disco (ej. `/dev/sda`) y no en la partición (ej. `/dev/sda2`)**.

Después, actualiza la configuración de GRUB:

```bash
update-grub
```

En RHEL o derivados:

```bash
grub2-install /dev/sda
grub2-mkconfig -o /boot/grub2/grub.cfg
```

---

#### 🚪 7. Salir y desmontar todo

```bash
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt/sys
sudo umount /mnt/boot/efi
sudo umount /mnt
```

---

#### 🔁 8. Reinicia el sistema

```bash
sudo reboot
```

Retira el USB y tu sistema debería arrancar normalmente con GRUB.

---

### 🧪 EJEMPLO COMPLETO

#### Situación:

Tienes una instalación de Ubuntu en `/dev/sda2`, con `/boot/efi` en `/dev/sda1`, pero GRUB se perdió.

#### Solución paso a paso:

```bash
# Desde el Live USB
sudo mount /dev/sda2 /mnt
sudo mount /dev/sda1 /mnt/boot/efi
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

# Entrar al sistema
sudo chroot /mnt

# Instalar y actualizar GRUB
grub-install /dev/sda
update-grub

# Salir y desmontar
exit
sudo umount /mnt/dev /mnt/proc /mnt/sys /mnt/boot/efi /mnt
sudo reboot
```

---

### 📌 Resultado Final

✔️ Tu sistema vuelve a arrancar

✔️ GRUB está instalado correctamente

✔️ Puedes modificar tu sistema incluso si no inicia

---

[🔼](#índice)

---

| **Inicio**         | **atrás 2**                                                         | **Siguiente 4**                               |
| ------------------ | ------------------------------------------------------------------- | --------------------------------------------- |
| [🏠](../README.md) | [⏪](./7_2_Introduccion_a_la_Administracion_de_Servidores_Linux.md) | [⏩](./7_4_Redes_Informaticas_de_Internet.md) |
