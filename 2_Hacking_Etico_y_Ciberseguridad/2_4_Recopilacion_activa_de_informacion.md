| **Inicio**         | **atrás 3**                                            | **Siguiente 5**                             |
| ------------------ | ------------------------------------------------------ | ------------------------------------------- |
| [🏠](../README.md) | [⏪](./2_3_Recopilacion_semi_pasiva_de_informacion.md) | [⏩](./2_5_Analisis_de_Vulnerabilidades.md) |

---

## **Índice**

| Temario                                                                                                           |
| ----------------------------------------------------------------------------------------------------------------- |
| [25. Recopilacion activa de informacion](#25-recopilacion-activa-de-informacion)                                  |
| [26. Instalación del entorno vulnerable: Metasploitable3](#26-instalación-del-entorno-vulnerable-metasploitable3) |
| [27. DNSrecon y transferencia de zona](#27-dnsrecon-y-transferencia-de-zona)                                      |
| [28. Nmap: Descubrimiento de Hosts](#28-nmap-descubrimiento-de-hosts)                                             |
| [29. Nmap: Escaneo de puertos](#29-nmap-escaneo-de-puertos)                                                       |
| [30. Nmap: Estados de los puertos](#30-nmap-estados-de-los-puertos)                                               |
| [31. Nmap: Descubrimiento de servicios](#31-nmap-descubrimiento-de-servicios)                                     |
| [32. Amap: Descubrimiento de servicios](#32-amap-descubrimiento-de-servicios)                                     |
| [33. Nmap: Identificación del sistema operativo](#33-nmap-identificación-del-sistema-operativo)                   |
| [34. Nmap: SMB Enumeration](#34-nmap-smb-enumeration)                                                             |
| [35. Nmap: SNMP Enumeration](#35-nmap-snmp-enumeration)                                                           |

---

# **Recopilacion activa de informacion**

## **25. Recopilacion activa de informacion**

### ¿Qué es la recopilación de información?

En **ciberseguridad**, la **recopilación de información** (o **information gathering / reconnaissance**) es el **primer paso de un ataque o auditoría**.

✔️ Es **entender el objetivo**: su red, servidores, servicios, usuarios, etc.

---

Hay **dos grandes tipos**:

✅ **Recopilación pasiva**

➡️ Observar sin interactuar directamente (ejemplo: buscar en Google, bases de datos WHOIS).

✅ **Recopilación activa**

➡️ Interactuar directamente con el objetivo para obtener información.

---

### ¿Qué es la **recopilación activa**?

➡️ Es el **proceso de obtener información enviando tráfico o haciendo consultas directamente al sistema objetivo**.

✅ Implica **contacto directo**, por ejemplo:

✔️ Escanear puertos

✔️ Hacer peticiones a servidores

✔️ Analizar respuestas

---

✅ 📌 Diferencia con la pasiva:

- **Pasiva** ➜ sin tocar al objetivo directamente.
- **Activa** ➜ contacto directo ➜ **puede ser detectada**.

---

### ¿Para qué se usa la recopilación activa?

✔️ Saber **qué puertos y servicios están abiertos**.

✔️ Identificar **versiones de software** (para buscar vulnerabilidades).

✔️ Mapear la **estructura de red**.

✔️ Ver **usuarios válidos** en un sistema.

✔️ Planificar **ataques posteriores**.

---

✅ 📌 Analogía sencilla:

✅ Pasiva ➜ Mirar una casa con binoculares desde lejos.

✅ Activa ➜ Tocar la puerta y ver quién responde.

---

### **Ejemplos de técnicas activas**

✔️ Escaneo de puertos

✔️ Enumeración de servicios

✔️ Fingerprinting de SO

✔️ Ataques de fuerza bruta de login

✔️ Banner grabbing

✔️ Peticiones DNS directas

---

### Herramientas más comunes

✅ **Nmap** ➜ escaneo de puertos y servicios

✅ **Netcat** ➜ conexión manual a puertos

✅ **Nikto** ➜ escaneo de vulnerabilidades en webs

✅ **Hydra** ➜ fuerza bruta de credenciales

✅ **dirb / gobuster** ➜ enumeración de directorios web

✅ **DNSenum / DNSrecon** ➜ enumeración DNS

---

### 📌 Ejemplo detallado: Escaneo de puertos con Nmap

✅ Objetivo: ver **qué puertos están abiertos** en un servidor.

---

#### 🧪 Comando básico:

```bash
nmap ejemplo.com
```

✅ Resultado ejemplo:

```
PORT     STATE  SERVICE
22/tcp   open   ssh
80/tcp   open   http
443/tcp  open   https
```

✔️ Te dice **qué servicios** están abiertos.

---

#### 🧪 Escaneo detallado de versiones

```bash
nmap -sV ejemplo.com
```

✅ Resultado:

```
22/tcp open  ssh  OpenSSH 8.2
80/tcp open  http Apache 2.4.41
```

✔️ Ahora sabes **las versiones exactas** ➜ puedes buscar vulnerabilidades conocidas.

---

#### 🧪 Escaneo de sistema operativo

```bash
nmap -O ejemplo.com
```

✅ Resultado:

```
OS details: Ubuntu 20.04 LTS
```

✔️ Te dice el **SO del servidor**.

---

✅ Usos reales:

✔️ Saber **cómo atacar o defender**.

✔️ Verificar que solo estén expuestos puertos necesarios.

---

### 📌 Ejemplo: Enumeración de directorios con gobuster

✅ Objetivo: encontrar **rutas ocultas en un sitio web**.

---

#### 🧪 Comando ejemplo:

```bash
gobuster dir -u http://ejemplo.com -w /usr/share/wordlists/dirb/common.txt
```

✅ Resultado:

```
/admin
/login
/uploads
```

✔️ Descubriste **rutas sensibles** para atacar o auditar.

---

### 📌 Ejemplo: Banner grabbing con Netcat

✅ Objetivo: ver **qué servicio corre** en un puerto.

---

#### 🧪 Comando ejemplo:

```bash
nc ejemplo.com 80
```

✅ Escribes:

```
HEAD / HTTP/1.0
```

✅ Respuesta:

```
HTTP/1.1 200 OK
Server: Apache/2.4.41 (Ubuntu)
```

✔️ ¡Tienes la versión del servidor!

---

✅ Otro ejemplo:

```bash
nc ejemplo.com 22
```

✅ Respuesta:

```
SSH-2.0-OpenSSH_8.2p1 Ubuntu
```

✔️ Ya sabes la versión de SSH.

---

### 📌 Ejemplo: Enumeración DNS con dnsenum

✅ Objetivo: descubrir **subdominios o registros DNS**.

---

#### 🧪 Comando ejemplo:

```bash
dnsenum ejemplo.com
```

✅ Resultado:

```
Found host: www.ejemplo.com
Found host: mail.ejemplo.com
Found host: admin.ejemplo.com
```

✔️ Ahora conoces subdominios potencialmente vulnerables.

---

### 📌 Ejemplo: Fuerza bruta de login con Hydra

✅ Objetivo: intentar **adivinar contraseñas**.

---

#### 🧪 Comando ejemplo:

```bash
hydra -l admin -P rockyou.txt ssh://ejemplo.com
```

✅ Intenta loguear como admin usando contraseñas del diccionario.

---

✅ Uso defensivo:

✔️ Verificar **cuán fácil es romper contraseñas**.

✔️ Aplicar **bloqueo de cuentas** tras intentos fallidos.

---

### ¿Es legal la recopilación activa?

⚠️ Muy importante:

✅ Legal ➜ en **tu propia infraestructura** o con **permiso del propietario**.

❌ Ilegal ➜ contra sistemas sin autorización ➜ **delito en casi todos los países**.

---

✅ En **pentesting ético**, se hace **con permiso escrito**.

✅ Sirve para **detectar vulnerabilidades antes que un atacante real**.

---

### Resumen sencillo

✔️ **Recopilación activa = interactuar con el objetivo para descubrir información**.

✔️ Más intrusiva ➜ más fácil de detectar.

✔️ Herramientas comunes ➜ Nmap, Netcat, Hydra, Gobuster, DNSenum.

✔️ Propósito ➜ mapear la superficie de ataque.

---

### 📌 Tabla de técnicas y herramientas

| Técnica                     | Herramienta común |
| --------------------------- | ----------------- |
| Escaneo de puertos          | nmap              |
| Banner grabbing             | netcat            |
| Enumeración de directorios  | gobuster          |
| Enumeración DNS             | dnsenum           |
| Fuerza bruta de contraseñas | hydra             |

---

### Ejercicio práctico (laboratorio seguro)

1️⃣ Instala Nmap en Linux:

```bash
sudo apt install nmap
```

2️⃣ Escanea tu propio router:

```bash
nmap 192.168.1.1
```

✅ Observa puertos abiertos.

3️⃣ Escaneo de versión:

```bash
nmap -sV 192.168.1.1
```

✅ Aprende **qué servicios** corre.

---

### Buenas prácticas

✔️ Usa siempre con **permiso**.

✔️ Documenta resultados.

✔️ Combina con **recopilación pasiva**.

✔️ Prioriza **seguridad y ética**.

---

### Conclusión

> **Recopilación activa = técnicas para interactuar directamente con un sistema objetivo y descubrir información que ayude a mapear y entender su superficie de ataque.**

✅ Herramientas ➜ Nmap, Netcat, Hydra, Gobuster.

✅ Clave para pentesting y auditorías.

✅ Siempre requiere **permiso legal**.

---

[🔼](#índice)

---

## **26. Instalación del entorno vulnerable: Metasploitable3**

### ¿Qué es Metasploitable3?

✔️ **Metasploitable3** es una **máquina virtual vulnerable** diseñada para **aprender hacking ético y pentesting**.

✔️ Incluye **vulnerabilidades reales** en servicios y aplicaciones.

✔️ Es como un “campo de pruebas” seguro para practicar ataques y explotación.

✔️ A diferencia de **Metasploitable2**, esta versión está basada en **Windows Server 2008** o **Ubuntu 14.04** y es **más realista y compleja**.

---

✅ **Usos principales:**

- Aprender Metasploit Framework.
- Practicar enumeración, explotación y post-explotación.
- Simular ataques reales en un entorno seguro.

---

📌 **¡Importante!**

⚠️ ¡Nunca ataques máquinas que no tengas permiso para auditar!

✔️ Metasploitable3 es para **uso personal y educativo en un laboratorio controlado.**

---

### Requisitos previos

Metasploitable3 **no es una ISO ni un OVA ya listo** como Metasploitable2.

✅ Se construye **usando scripts de automatización**.

---

✔️ Necesitarás:

✅ Sistema operativo (recomendado): **Linux (Ubuntu / Kali / Debian) o macOS**, pero también se puede en Windows.

✅ **Vagrant** ➜ Administra VMs.

✅ **VirtualBox** ➜ Hipervisor para correr las VMs.

✅ **Packer** ➜ Construye imágenes de VM automáticamente.

✅ Git ➜ Para clonar el repositorio oficial.

---

✅ **Hardware recomendado:**

✔️ CPU: mínimo 2 núcleos (4 mejor).

✔️ RAM: 4 GB libres mínimo (8+ mejor).

✔️ Espacio en disco: 30–40 GB libres (las VMs son pesadas).

---

### Paso a paso para instalar **Metasploitable3** (Linux)

> A continuación te enseño **la forma más común y sencilla en Linux / Kali / Ubuntu**.

_(Si usas Windows, también puedes hacerlo, pero los comandos cambian un poco)._

---

#### ✅ Paso 1: Instalar **VirtualBox**

✔️ VirtualBox permite crear y ejecutar máquinas virtuales.

🧪 En Ubuntu / Debian:

```bash
sudo apt update
sudo apt install virtualbox
```

🧪 O descarga la última versión desde:

👉 [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

---

#### ✅ Paso 2: Instalar **Vagrant**

✔️ Vagrant gestiona la creación y configuración de las VMs.

🧪 En Ubuntu:

```bash
sudo apt install vagrant
```

🧪 O descarga el .deb desde:

👉 [https://developer.hashicorp.com/vagrant/downloads](https://developer.hashicorp.com/vagrant/downloads)

✅ Verifica la instalación:

```bash
vagrant --version
```

---

#### ✅ Paso 3: Instalar **Packer**

✔️ Packer construye las imágenes base de VirtualBox.

🧪 En Ubuntu:

✅ Descarga Packer desde:

👉 [https://developer.hashicorp.com/packer/downloads](https://developer.hashicorp.com/packer/downloads)

✅ Descomprime y copia el binario en `/usr/local/bin`:

```bash
unzip packer_*.zip
sudo mv packer /usr/local/bin/
```

✅ Verifica:

```bash
packer --version
```

---

✅ 📌 En Kali Linux reciente puedes instalarlo con:

```bash
sudo apt install packer
```

---

#### ✅ Paso 4: Instalar **Git**

✅ Para clonar el repositorio de Metasploitable3.

```bash
sudo apt install git
```

---

#### ✅ Paso 5: Clonar el repositorio oficial

✅ Clona el repositorio de Metasploitable3:

```bash
git clone https://github.com/rapid7/metasploitable3
```

✅ Entra a la carpeta:

```bash
cd metasploitable3
```

---

✅ Dentro verás:

```
build.sh
packer/
vagrant/
scripts/
...
```

---

#### ✅ Paso 6: Construir la VM

✅ Para **Ubuntu 14.04** (Linux vulnerable):

```bash
./build.sh ubuntu1404
```

✅ Para **Windows Server 2008**:

```bash
./build.sh windows2008
```

---

✅ El script va a:

✔️ Descargar el ISO de Ubuntu o Windows Server (tarda un poco).

✔️ Usar **Packer** para crear la VM base.

✔️ Configurar servicios vulnerables.

✔️ Crear un archivo Vagrant para VirtualBox.

---

📌 **Tiempo estimado:**

⚠️ 20–90 minutos, dependiendo de tu PC e Internet.

✅ El resultado ➜ Una VM lista para usarse con Vagrant + VirtualBox.

---

#### ✅ Paso 7: Iniciar la VM

✅ Cuando termine la construcción:

```bash
vagrant up ubuntu1404
```

o

```bash
vagrant up windows2008
```

✔️ Esto iniciará la VM en VirtualBox.

---

✅ Ver estado de la VM:

```bash
vagrant status
```

✅ Apagar la VM:

```bash
vagrant halt
```

✅ Destruir la VM:

```bash
vagrant destroy
```

---

✅ Usar VirtualBox para verla gráficamente:

✔️ Abre VirtualBox ➜ verás “metasploitable3-ubuntu1404” o “windows2008”.

✔️ Puedes abrir la consola para interactuar.

---

#### Acceso y uso

✅ Por defecto, las VMs tienen varios **servicios vulnerables** expuestos.

---

✅ Ejemplo con **nmap**:

```bash
nmap 192.168.56.101
```

✅ Resultado:

```
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
80/tcp   open  http
3306/tcp open  mysql
...
```

✔️ Te servirá para **escaneo, explotación con Metasploit, pruebas manuales, etc.**

---

✅ Puedes conectarte por **SSH** (si habilitado):

```bash
ssh vagrant@192.168.56.101
password: vagrant
```

---

#### Ejemplo de uso con Metasploit

✅ En tu Kali o Linux:

```bash
msfconsole
```

✅ Buscar exploits:

```bash
search vsftpd
```

✅ Usar exploit:

```bash
use exploit/unix/ftp/vsftpd_234_backdoor
```

✅ Configurar:

```bash
set RHOST 192.168.56.101
```

✅ Lanzar:

```bash
exploit
```

✔️ Resultado ➜ ¡Shell en la VM vulnerable!

---

✅ O prueba exploits para Windows con **windows2008**:

```bash
use exploit/windows/smb/ms17_010_eternalblue
```

---

✅ 📌 ¡Metasploitable3 tiene múltiples servicios y vulnerabilidades reales para practicar!

---

### Alternativa más fácil (OVA ya listo)

✔️ Hay personas que han compartido ya la VM **.ova** exportada (no oficial).

✔️ Puedes importarla directamente en VirtualBox.

⚠️ Pero cuidado:

✅ Puede que no tenga todos los servicios configurados idénticos.

✅ Siempre verifica fuentes confiables.

---

### Resumen paso a paso (Linux)

1️⃣ Instala VirtualBox:

```bash
sudo apt install virtualbox
```

2️⃣ Instala Vagrant:

```bash
sudo apt install vagrant
```

3️⃣ Instala Packer:

✅ Desde la web oficial.

4️⃣ Instala Git:

```bash
sudo apt install git
```

5️⃣ Clona el repositorio:

```bash
git clone https://github.com/rapid7/metasploitable3
```

6️⃣ Entra al directorio:

```bash
cd metasploitable3
```

7️⃣ Construye la VM:

```bash
./build.sh ubuntu1404
```

o

```bash
./build.sh windows2008
```

8️⃣ Inicia con Vagrant:

```bash
vagrant up ubuntu1404
```

9️⃣ Haz pentesting desde Kali o desde tu máquina anfitriona.

---

### Tabla de comandos clave

| Comando                      | Qué hace                              |
| ---------------------------- | ------------------------------------- |
| `git clone URL`              | Clona el repositorio                  |
| `cd metasploitable3`         | Entra a la carpeta                    |
| `./build.sh ubuntu1404`      | Construye la VM de Ubuntu vulnerable  |
| `./build.sh windows2008`     | Construye la VM de Windows vulnerable |
| `vagrant up ubuntu1404`      | Arranca la VM de Ubuntu               |
| `vagrant halt ubuntu1404`    | Apaga la VM                           |
| `vagrant destroy ubuntu1404` | Borra la VM completamente             |
| `vagrant status`             | Verifica el estado de las VMs         |

---

### Consejos útiles

✔️ Hazlo en **entornos de laboratorio** (no en producción).

✔️ Usa **red interna o host-only** en VirtualBox para aislar la VM.

✔️ Ten **suficiente espacio en disco**.

✔️ Usa **Snapshots** en VirtualBox para guardar estados.

✔️ Puedes construir ambas versiones (Ubuntu y Windows) para practicar todo tipo de ataques.

---

### Conclusión

> **Metasploitable3** es un entorno perfecto para aprender hacking ético.

✅ Más realista que Metasploitable2.

✅ Incluye vulnerabilidades modernas.

✅ Te obliga a practicar **escaneo, enumeración, explotación y post-explotación**.

---

[🔼](#índice)

---

## **27. DNSrecon y transferencia de zona**

### ¿Qué es DNSrecon?

✔️ **DNSrecon** es una herramienta en Python que se utiliza para **recolectar información de registros DNS de un dominio**.

---

✅ **¿Qué puedes hacer con DNSrecon?**

🔹 Enumerar registros DNS (A, AAAA, MX, NS, TXT, etc.)

🔹 Hacer brute force de subdominios

🔹 Intentar una **transferencia de zona**

🔹 Verificar configuraciones inseguras

---

📌 **Está incluida en Kali Linux y Parrot Security**, o la puedes instalar en cualquier Linux/macOS.

---

✅ **¿Por qué es importante?**

Porque el DNS (Domain Name System) es como **la guía telefónica de Internet**, y si logras sacar mucha información DNS, puedes:

✔️ Descubrir subdominios internos o servidores expuestos

✔️ Mapear infraestructura de red

✔️ Encontrar posibles puntos débiles

---

---

### ¿Qué es una Transferencia de Zona (Zone Transfer)?

🚨 **Transferencia de zona = La joya de la corona de la enumeración DNS.**

---

✅ Una **zona DNS** es la **base de datos completa de nombres y registros** de un dominio, que está guardada en los **servidores DNS autoritativos**.

✅ Una **transferencia de zona** (AXFR) es un proceso que permite a un servidor DNS secundario copiar todos los registros de un servidor primario para sincronizar la información.

---

🔍 **¿Por qué es un problema de seguridad?**

Porque si el servidor DNS autoritativo está mal configurado, cualquiera podría pedir esa transferencia y conseguir:

✔️ Todos los registros DNS del dominio

✔️ Subdominios internos (intranet, dev, staging)

✔️ Correo y servidores críticos

---

✅ **Ejemplo sencillo:**

Imagínate que preguntas al servidor DNS:

```
Hola, ¿puedes darme TODO tu directorio telefónico, por favor?
```

... y te responde:

```
Claro, toma todo mi libro de contactos.
```

😮 Eso es un problema.

---

✅ En un entorno bien configurado, los servidores DNS **no deberían permitir transferencias de zona a cualquier IP**, solo a sus servidores secundarios autorizados.

---

### Instalación de DNSrecon

En **Kali Linux** ya viene instalado.

Si usas otro sistema, puedes instalarlo así:

✅ Requisitos:

- Python3
- Git

---

🧪 **Instalar en Linux o macOS:**

```bash
git clone https://github.com/darkoperator/dnsrecon.git
cd dnsrecon
sudo pip3 install -r requirements.txt
```

✅ Para ejecutarlo:

```bash
python3 dnsrecon.py
```

o si ya está instalado como ejecutable:

```bash
dnsrecon
```

---

✅ Para comprobar que funciona:

```bash
dnsrecon -h
```

Verás las opciones de uso.

---

### Ejemplo de uso básico: Enumerar registros DNS

✅ Comando sencillo:

```bash
dnsrecon -d ejemplo.com
```

✅ ¿Qué hace?

✔️ Consulta registros:

- A (direcciones IP)
- AAAA (IPv6)
- MX (correo)
- NS (servidores DNS)
- TXT (verificaciones, SPF, etc.)

---

✅ Ejemplo de salida:

```
[*] NS Records
ns1.ejemplo.com.
ns2.ejemplo.com.

[*] A Records
www.ejemplo.com. 192.168.1.10

[*] MX Records
mail.ejemplo.com.

[*] TXT Records
"v=spf1 include:_spf.google.com ~all"
```

✔️ Ahora tienes un buen mapa inicial.

---

### Transferencia de Zona con DNSrecon

🎯 **Aquí viene lo interesante: probar si algún servidor permite AXFR.**

✅ Comando:

```bash
dnsrecon -d ejemplo.com -t axfr
```

---

✅ ¿Qué significa?

- `-d ejemplo.com` ➜ dominio objetivo
- `-t axfr` ➜ intento de transferencia de zona

---

✅ **¿Qué pasa si está vulnerable?**

🎉 Te entregará **TODOS los registros DNS**:

```
[*] Attempting AXFR
[+] Zone Transfer successful: ns1.ejemplo.com.

[+] Records obtained:
www.ejemplo.com.   A   192.168.1.10
mail.ejemplo.com.  A   192.168.1.20
dev.ejemplo.com.   A   192.168.1.30
ftp.ejemplo.com.   A   192.168.1.40
...
```

---

✅ Esto significa:

✔️ Descubriste subdominios internos.

✔️ Ahora sabes servidores internos (dev, staging, etc).

✔️ Podrías planificar más ataques.

---

✅ **¿Qué pasa si no es vulnerable?**

Te mostrará algo como:

```
[-] Failed AXFR on ns1.ejemplo.com.
```

✔️ Eso significa que el servidor no permite transferencias no autorizadas (bien configurado).

---

### Otras opciones útiles de DNSrecon

🔹 **Enumerar subdominios por diccionario**

```bash
dnsrecon -d ejemplo.com -D wordlist.txt -t brt
```

- `-D` ➜ diccionario de subdominios (por ejemplo, `/usr/share/wordlists/dnsmap.txt`)
- `-t brt` ➜ brute force de subdominios

---

🔹 **Guardar resultados en un archivo**

```bash
dnsrecon -d ejemplo.com -a -t axfr -j salida.json
```

- `-j` ➜ guarda resultados en formato JSON

---

### Ejemplo completo paso a paso

🎯 Imagina que quieres auditar `midominio.com`.

---

✅ 1️⃣ Enumerar registros:

```bash
dnsrecon -d midominio.com
```

---

✅ 2️⃣ Ver qué servidores DNS tiene:

```
[*] NS Records
ns1.midominio.com.
ns2.midominio.com.
```

---

✅ 3️⃣ Probar transferencia de zona:

```bash
dnsrecon -d midominio.com -t axfr
```

✔️ Si es vulnerable, aparecerán todos los registros.

✔️ Si no, verás error de AXFR.

---

✅ 4️⃣ Enumerar subdominios con brute force:

```bash
dnsrecon -d midominio.com -D /usr/share/wordlists/dnsmap.txt -t brt
```

✔️ Así descubres subdominios adicionales.

---

✅ 5️⃣ Guardar todo en JSON:

```bash
dnsrecon -d midominio.com -a -j resultado.json
```

---

### Resumen rápido de comandos clave

| Comando                                      | Qué hace                      |
| -------------------------------------------- | ----------------------------- |
| `dnsrecon -d dominio`                        | Enumera registros básicos     |
| `dnsrecon -d dominio -t axfr`                | Prueba transferencia de zona  |
| `dnsrecon -d dominio -D wordlist.txt -t brt` | Brute force de subdominios    |
| `dnsrecon -d dominio -a`                     | Todas las pruebas disponibles |
| `dnsrecon -d dominio -j archivo.json`        | Guarda en JSON                |

---

### Buenas prácticas y legalidad

🚨 **IMPORTANTE:**

✅ La transferencia de zona **NO debe hacerse sin permiso**.

✅ Aunque parezca un “error de configuración”, explotar información sin autorización puede ser **ilegal**.

---

✅ Uso permitido:

- Auditorías de tu propia infraestructura.
- Pentesting con permiso escrito del cliente.
- Laboratorios de práctica.

---

### Conclusión

> **DNSrecon** es una herramienta poderosa para:

> ✅ Enumerar registros DNS.

> ✅ Descubrir subdominios.

> ✅ Probar transferencias de zona.

> ✅ Mapear superficies de ataque.

✅ La **transferencia de zona** es un hallazgo crítico que puede exponer toda la estructura DNS de un dominio si está mal configurada.

---

[🔼](#índice)

---

## **28. Nmap: Descubrimiento de Hosts**

### ¿Qué es Nmap?

✅ **Nmap** (Network Mapper) es una herramienta de código abierto para **explorar redes y auditorías de seguridad**.

✔️ Muy usada en pentesting y administración de redes.

✔️ Permite descubrir **qué dispositivos (hosts) están activos**, **qué puertos están abiertos**, **qué servicios corren**, etc.

---

✅ Uno de sus usos más básicos y esenciales es:

👉 **Descubrimiento de hosts**

➡️ Es decir: saber **qué equipos están encendidos/respondiendo** en una red.

---

✅ Ejemplo sencillo:

> "En mi red hay 50 direcciones IP posibles, pero ¿cuáles están encendidas?"

---

### ¿Qué es el Descubrimiento de Hosts?

✔️ También llamado **Host Discovery** o **Ping Scan**.

✔️ Es el **primer paso en un escaneo Nmap**.

✔️ Sirve para **identificar máquinas vivas** antes de escanear puertos.

---

✅ 📌 Analogía simple:

> "Antes de preguntar por puertas abiertas (puertos), primero averigua si alguien vive en la casa."

---

✅ En redes grandes (empresas, oficinas), reduce **mucho tiempo**:

✔️ No escaneas direcciones IP que no existen o están apagadas.

---

### Cómo funciona el Descubrimiento de Hosts

Nmap usa varias técnicas para saber si un host está activo:

✅ **ICMP Echo Request** ➜ como `ping` clásico.

✅ **TCP SYN Ping** ➜ envía paquetes SYN a puertos comunes (80, 443).

✅ **TCP ACK Ping** ➜ para saltar ciertos firewalls.

✅ **UDP Ping** ➜ menos usado, pero a veces útil.

✅ **ARP Scan** ➜ en redes locales (LAN).

---

✅ 🔥 Muy importante:

> Muchos hosts/firewalls **bloquean ICMP (ping)**, por lo que Nmap ofrece **alternativas** para detectar hosts.

---

### Ejemplo básico: Ping Scan

✅ **Comando:**

```bash
nmap -sn 192.168.1.0/24
```

✅ Significado:

- `-sn` ➜ "ping scan", solo descubre hosts, no escanea puertos.

✅ Ejemplo de salida:

```
Nmap scan report for 192.168.1.1
Host is up (0.0030s latency).
Nmap scan report for 192.168.1.10
Host is up (0.0020s latency).
Nmap done: 256 IP addresses (2 hosts up) scanned in 3.45 seconds
```

✅ Resultado ➜ sabes **qué hosts están activos**.

---

✅ ¿Para qué sirve?

✔️ Saber cuántos dispositivos hay.

✔️ Planificar escaneos de puertos **solo en hosts vivos**.

---

### Ejemplo con rango de IPs

✅ Para un rango específico:

```bash
nmap -sn 192.168.1.10-20
```

✔️ Solo escanea las IPs del 10 al 20.

---

✅ O lista de hosts en un archivo:

```
cat hosts.txt
192.168.1.10
192.168.1.11
192.168.1.12
```

```bash
nmap -sn -iL hosts.txt
```

---

### ICMP Echo Request (Ping clásico)

✅ Por defecto, `-sn` usa ICMP (si no bloqueado):

✔️ Equivalente a:

```bash
ping 192.168.1.10
```

✔️ Ventaja ➜ rápido y simple.

✔️ Desventaja ➜ puede ser bloqueado por firewalls.

---

✅ 🔎 Para solo ICMP:

```bash
nmap -PE -sn 192.168.1.0/24
```

- `-PE` ➜ ICMP Echo.

---

### TCP SYN Ping

✅ Útil si ICMP está bloqueado.

✔️ Envía paquetes SYN a puertos (como 80 o 443).

✔️ Respuesta indica que el host está activo.

✅ Comando:

```bash
nmap -PS80,443 192.168.1.0/24
```

✅ Explicación:

- `-PS` ➜ SYN Ping.
- `80,443` ➜ puertos destino.

---

✅ Ejemplo de salida:

```
Nmap scan report for 192.168.1.15
Host is up.
```

✔️ Descubre hosts que responden en esos puertos.

---

### TCP ACK Ping

✅ Para evadir ciertos firewalls que bloquean SYN pero permiten ACK.

✅ Comando:

```bash
nmap -PA80,443 192.168.1.0/24
```

- `-PA` ➜ ACK Ping.

---

✅ Uso:

✔️ Firewalls stateful suelen dejar pasar ACK.

✔️ Útil en redes corporativas.

---

### UDP Ping

✅ A veces firewalls filtran TCP pero no UDP.

✅ Comando:

```bash
nmap -PU53 192.168.1.0/24
```

- `-PU` ➜ UDP Ping.
- `53` ➜ puerto DNS.

---

✅ Descubre hosts que responden a paquetes UDP.

---

### ARP Scan (redes locales)

✅ En redes locales (LAN), **la mejor técnica**.

✔️ Envía ARP Requests.

✔️ No se puede bloquear con firewalls.

✔️ Muy confiable.

✅ Comando:

```bash
sudo nmap -sn 192.168.1.0/24
```

✅ Nmap detecta que es LAN ➜ usa ARP automáticamente.

---

✅ Resultado típico:

```
Nmap scan report for 192.168.1.2
MAC Address: 00:11:22:33:44:55 (Vendor)
Host is up.
```

✔️ Además te da la dirección MAC.

---

### Combinando técnicas

✔️ Puedes combinar técnicas para mayor efectividad.

✅ Ejemplo:

```bash
nmap -PE -PS80,443 -PA8080 -sn 192.168.1.0/24
```

✅ Significa:

- ICMP Echo
- TCP SYN a 80,443
- TCP ACK a 8080

✅ Aumenta la probabilidad de detectar hosts detrás de firewalls.

---

### Guardar resultados

✅ Para guardar en archivo:

```bash
nmap -sn 192.168.1.0/24 -oN resultado.txt
```

✅ Formato XML:

```bash
nmap -sn 192.168.1.0/24 -oX resultado.xml
```

✔️ Para análisis posterior.

---

### Resumen de opciones clave

| Opción        | Qué hace                             |
| ------------- | ------------------------------------ |
| `-sn`         | Ping Scan (solo descubrir hosts)     |
| `-PE`         | ICMP Echo Request                    |
| `-PS`         | TCP SYN Ping                         |
| `-PA`         | TCP ACK Ping                         |
| `-PU`         | UDP Ping                             |
| `-PR`         | ARP Ping (en LAN)                    |
| `-iL archivo` | Leer lista de hosts desde un archivo |
| `-oN`         | Salida en texto normal               |
| `-oX`         | Salida en XML                        |

---

### Ejemplo práctico paso a paso

✔️ Imagina que estás en tu red local (192.168.1.0/24).

---

✅ 1️⃣ Descubre hosts vivos con ARP:

```bash
sudo nmap -sn 192.168.1.0/24
```

✅ Resultado:

```
Host is up: 192.168.1.1
Host is up: 192.168.1.10
Host is up: 192.168.1.20
```

---

✅ 2️⃣ Intento con ICMP:

```bash
nmap -PE -sn 192.168.1.0/24
```

---

✅ 3️⃣ Alternativa si ICMP está bloqueado:

```bash
nmap -PS80,443 -sn 192.168.1.0/24
```

---

✅ 4️⃣ Combinar técnicas:

```bash
nmap -PE -PS22,80,443 -PA8080 -sn 192.168.1.0/24
```

---

✅ 5️⃣ Guardar resultados:

```bash
nmap -sn 192.168.1.0/24 -oN hosts_activos.txt
```

---

### Buenas prácticas

✔️ Siempre usa **rangos limitados** (no escanees Internet sin permiso).

✔️ En pentesting profesional ➜ siempre con **permiso del cliente**.

✔️ En redes corporativas ➜ coordina con admins para evitar alarmas.

---

### Conclusión

✅ **Descubrimiento de hosts = primer paso esencial** en reconocimiento y escaneo.

✅ Nmap ofrece **múltiples técnicas** para adaptarse a firewalls y topologías de red.

✅ Herramienta poderosa, pero **úsala éticamente y con permiso.**

---

[🔼](#índice)

---

## **29. Nmap: Escaneo de puertos**

### ¿Qué es el escaneo de puertos?

✔️ Es **el proceso de enviar paquetes a un puerto de red para ver si está abierto o cerrado**.

✔️ Cada puerto representa un **servicio o aplicación** que escucha conexiones.

---

✅ 📌 Analogía sencilla:

> Imagina un edificio con muchas puertas numeradas (puertos).

> Tocar cada puerta para ver si alguien responde ➜ eso es un **escaneo de puertos**.

---

✅ ¿Para qué sirve?

✔️ Descubrir **qué servicios ofrece un sistema**.

✔️ Identificar **versiones vulnerables**.

✔️ Planificar ataques o auditorías.

✔️ Detectar **puertos expuestos innecesariamente**.

---

✅ Es uno de los **primeros pasos en pentesting** y **auditoría de redes**.

---

### Conceptos básicos

✔️ **Puertos**: Numerados del 0 al 65535.

- **0-1023** ➜ Puertos conocidos (HTTP=80, SSH=22, FTP=21).
- **1024-49151** ➜ Puertos registrados.
- **49152-65535** ➜ Puertos dinámicos o privados.

---

✔️ **Estados de un puerto**:

- **open (abierto)** ➜ acepta conexiones.
- **closed (cerrado)** ➜ responde, pero no hay servicio.
- **filtered (filtrado)** ➜ firewall o filtro lo bloquea.
- **unfiltered** ➜ no se sabe si está abierto o cerrado.
- **open|filtered** ➜ no se pudo determinar.

---

### Instalación de Nmap

✔️ En **Linux**:

```bash
sudo apt update
sudo apt install nmap
```

✔️ En **Windows**:

👉 Descargar desde: [nmap.org](https://nmap.org/download.html)

✔️ Verifica:

```bash
nmap --version
```

---

### Escaneo de puertos más básico

✅ Comando:

```bash
nmap <IP>
```

✅ Ejemplo:

```bash
nmap 192.168.1.10
```

✅ Resultado típico:

```
PORT     STATE  SERVICE
22/tcp   open   ssh
80/tcp   open   http
443/tcp  closed https
```

---

✅ Explicación:

✔️ 22 abierto ➜ SSH está activo.

✔️ 80 abierto ➜ HTTP activo.

✔️ 443 cerrado ➜ HTTPS no disponible.

---

### Escanear un rango de IPs

✅ Comando:

```bash
nmap 192.168.1.10-20
```

✔️ Nmap escanea todos los hosts en ese rango y reporta puertos abiertos.

---

### Especificar puertos concretos

✅ Escanear solo ciertos puertos:

```bash
nmap -p 22,80,443 192.168.1.10
```

✔️ Solo verifica esos puertos.

---

✅ Rango de puertos:

```bash
nmap -p 20-100 192.168.1.10
```

---

### Escaneo de todos los 65535 puertos

✅ Comando:

```bash
nmap -p- 192.168.1.10
```

✔️ Muy completo, pero más lento.

---

### ✅ 8️⃣ Modo "Verbose" (detallado)

✅ Para ver más información en consola:

```bash
nmap -v 192.168.1.10
```

✔️ Usa `-vv` para todavía más detalle.

---

### Modo rápido (Fast Scan)

✅ Para escanear solo los **1000 puertos más comunes**:

```bash
nmap -F 192.168.1.10
```

✔️ Mucho más rápido.

---

### Escaneo de versión de servicios

✅ Uno de los más usados:

```bash
nmap -sV 192.168.1.10
```

✔️ Intenta identificar **la versión exacta del servicio**.

✅ Resultado:

```
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 8.2p1 Ubuntu
80/tcp   open  http    Apache httpd 2.4.41
```

✔️ ¡Ideal para encontrar vulnerabilidades específicas!

---

### Escaneo de sistema operativo

✅ Comando:

```bash
sudo nmap -O 192.168.1.10
```

✔️ Intenta adivinar el **sistema operativo** remoto.

✅ Resultado ejemplo:

```
OS details: Linux 3.2 - 4.9
```

---

✅ Combinar:

```bash
sudo nmap -sV -O 192.168.1.10
```

✔️ Versiones de servicios + sistema operativo.

---

### Escaneo agresivo

✅ Súper útil en auditorías:

```bash
sudo nmap -A 192.168.1.10
```

✅ ¿Qué hace `-A`?

✔️ Detección de SO (`-O`)

✔️ Detección de versiones (`-sV`)

✔️ Script scan (NSE básico)

✔️ Trace route

✅ Resultado muy detallado.

---

✅ Ejemplo:

```
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 8.2p1
80/tcp   open  http    Apache 2.4.41
|_http-title: Welcome to my website!
```

---

### Guardar resultados en archivos

✅ Salida en texto:

```bash
nmap -oN resultado.txt 192.168.1.10
```

✅ Salida en XML:

```bash
nmap -oX resultado.xml 192.168.1.10
```

✅ Salida en formato grepable:

```bash
nmap -oG resultado.gnmap 192.168.1.10
```

---

✅ Muy útil para informes o procesamiento posterior.

---

### Ejemplo práctico paso a paso

🎯 Imagina que quieres auditar la IP `192.168.1.50`.

---

✅ 1️⃣ Escaneo rápido (puertos comunes):

```bash
nmap -F 192.168.1.50
```

---

✅ 2️⃣ Escaneo completo de todos los puertos:

```bash
nmap -p- 192.168.1.50
```

---

✅ 3️⃣ Detección de versiones:

```bash
nmap -sV 192.168.1.50
```

---

✅ 4️⃣ Detección de SO:

```bash
sudo nmap -O 192.168.1.50
```

---

✅ 5️⃣ Escaneo agresivo:

```bash
sudo nmap -A 192.168.1.50
```

---

✅ 6️⃣ Guardar en archivo:

```bash
nmap -A -oN auditoria.txt 192.168.1.50
```

---

### Escaneo sigiloso (SYN Scan)

✅ Muy usado en pentesting:

```bash
sudo nmap -sS 192.168.1.50
```

✔️ Envía paquetes SYN ➜ más difícil de detectar.

✔️ Muy rápido y efectivo.

---

### Scripts NSE básicos

✅ Nmap tiene **scripts** para buscar vulnerabilidades conocidas.

---

✅ Ejemplo:

```bash
nmap --script vuln 192.168.1.50
```

✔️ Lanza scripts de **vulnerabilidad**.

---

✅ Resultado:

```
PORT   STATE SERVICE
80/tcp open  http
| http-dombased-xss:
|   Spidering limited to: maxdepth=3; maxpagecount=20
|   Possible XSS: ...
```

---

### Resumen de opciones útiles

| Opción       | Qué hace                                    |
| ------------ | ------------------------------------------- |
| `-p`         | Especificar puertos                         |
| `-p-`        | Todos los puertos (0-65535)                 |
| `-F`         | Escaneo rápido (puertos comunes)            |
| `-sV`        | Detección de versiones                      |
| `-O`         | Detección de sistema operativo              |
| `-A`         | Escaneo agresivo (OS + versiones + scripts) |
| `-sS`        | SYN scan (sigiloso)                         |
| `--script`   | Usar scripts NSE                            |
| `-oN`, `-oX` | Guardar resultados                          |

---

### Buenas prácticas

✔️ Usa siempre **con permiso**.

✔️ Evita escanear redes ajenas sin autorización.

✔️ Documenta resultados.

✔️ Filtra puertos abiertos innecesarios ➜ mejora seguridad.

---

### Conclusión

✅ El **escaneo de puertos con Nmap** es **fundamental** en ciberseguridad.

✅ Permite:

✔️ Descubrir servicios expuestos.

✔️ Detectar versiones vulnerables.

✔️ Planificar defensas.

✅ Es **rápido**, **flexible** y **muy poderoso**.

---

[🔼](#índice)

---

## **30. Nmap: Estados de los puertos**

### ¿Qué son los estados de los puertos?

Cuando haces un escaneo con **Nmap**, para cada puerto escaneado él te dirá su **estado**.

📌 **El estado indica si un puerto está abierto, cerrado, filtrado, etc.**

✅ En otras palabras:

> **¿El puerto está escuchando? ¿Responde? ¿Está bloqueado?**

---

✅ 🔎 **Por qué es importante:**

✔️ Saber si puedes conectarte al servicio.

✔️ Identificar puertos expuestos.

✔️ Planificar ataques o defensas.

✔️ Detectar firewalls o filtros.

---

### Estados principales que muestra Nmap

Nmap define varios **estados** para los puertos.

✔️ Los más comunes son:

| Estado                 | Qué significa                                           |     |
| ---------------------- | ------------------------------------------------------- | --- |
| **open**               | Hay un servicio escuchando activamente                  |     |
| **closed**             | No hay servicio, pero el host respondió                 |     |
| **filtered**           | No hay respuesta clara; un firewall bloquea la conexión |     |
| **unfiltered**         | Accesible pero Nmap no sabe si está abierto o cerrado   |     |
| **open \| filtered**   | Nmap no puede distinguir si está abierto o filtrado     |
| **closed \| filtered** | No sabe si está cerrado o filtrado (más raro)           |

---

✅ Vamos uno por uno, **con ejemplos fáciles**.

---

### Estado: **open**

✅ Significa ➜ el puerto **está abierto** y **acepta conexiones**.

✔️ Hay un **servicio escuchando** (como SSH, HTTP, etc.).

✅ **Ejemplo real:**

```
PORT   STATE SERVICE
22/tcp open  ssh
```

✔️ SSH está escuchando en el puerto 22.

✔️ Puedes intentar conectarte con:

```bash
ssh usuario@IP
```

---

✅ Usos en pentesting:

✔️ Buscar versiones del servicio ➜ vulnerabilidades.

✔️ Intentar explotación.

✔️ Enumeración.

---

### Estado: **closed**

✅ Significa ➜ **el puerto está cerrado**.

✔️ No hay servicio escuchando.

✔️ El host respondió con un **RST (reset)**.

✅ **Ejemplo:**

```
PORT     STATE  SERVICE
443/tcp  closed https
```

✔️ No hay servidor HTTPS en ese puerto.

---

✅ Usos:

✔️ El sistema está **vivo** (responde).

✔️ Puede abrirse en el futuro ➜ monitorear.

✔️ Firewalls menos restrictivos suelen mostrar puertos "closed" en lugar de "filtered".

---

### Estado: **filtered**

✅ Significa ➜ **Nmap no puede determinar si está abierto o cerrado.**

✔️ **No hubo respuesta** al escaneo.

✔️ Un **firewall o filtro** está bloqueando los paquetes.

✅ **Ejemplo:**

```
PORT     STATE     SERVICE
23/tcp   filtered  telnet
```

✔️ El puerto 23 está protegido ➜ no puedes saber si Telnet corre allí.

---

✅ Usos:

✔️ Indica **protección activa**.

✔️ Analizar reglas de firewall.

✔️ Intentar otras técnicas (UDP, ACK, etc.) para evadir filtros.

---

### Estado: **unfiltered**

✅ Menos común.

✔️ El puerto es **accesible**, pero Nmap **no puede determinar** si está abierto o cerrado con ese tipo de escaneo.

✅ Típico con ciertos **ACK Scans**:

```
PORT    STATE       SERVICE
80/tcp  unfiltered  http
```

---

✅ Usos:

✔️ Saber que no hay firewall bloqueando.

✔️ Cambiar de técnica ➜ escaneo SYN o Connect.

---

### Estado: **open|filtered**

✅ Nmap **no puede distinguir** entre **abierto** o **filtrado**.

✔️ Típico en **UDP Scans** o cuando el puerto no responde en absoluto.

✅ Ejemplo:

```
PORT     STATE          SERVICE
53/udp   open|filtered  domain
```

✔️ Podría estar abierto (DNS activo) o filtrado (firewall bloquea).

---

✅ Usos:

✔️ Intentar técnicas alternativas ➜ enviar consultas DNS reales.

✔️ Usar scripts NSE para prueba más profunda.

---

### Estado: **closed|filtered**

✅ Más raro.

✔️ Aparece en ciertos escaneos de puertos cuando **Nmap no puede decidir si está cerrado o filtrado**.

---

✅ Ejemplo:

```
PORT     STATE            SERVICE
9999/tcp closed|filtered  unknown
```

✔️ Respuesta insuficiente ➜ el resultado es ambiguo.

---

### Ejemplo práctico con Nmap

✅ Vamos a hacer un escaneo sencillo y ver estados:

---

✅ Comando:

```bash
nmap 192.168.1.10
```

✅ Resultado típico:

```
PORT     STATE  SERVICE
22/tcp   open   ssh
80/tcp   open   http
443/tcp  closed https
23/tcp   filtered telnet
```

✔️ Interpretación:

- 22/tcp ➜ SSH activo.
- 80/tcp ➜ HTTP activo.
- 443/tcp ➜ no hay HTTPS.
- 23/tcp ➜ firewall bloquea Telnet.

---

### Escaneo de puertos específicos

✅ Comando:

```bash
nmap -p 21,22,23,80,443 192.168.1.10
```

✅ Resultado:

```
PORT     STATE     SERVICE
21/tcp   closed    ftp
22/tcp   open      ssh
23/tcp   filtered  telnet
80/tcp   open      http
443/tcp  closed    https
```

✔️ ¡Puedes leer cada línea como una frase!

> "El puerto 21 está cerrado. El 22 está abierto. El 23 está filtrado."

---

### Ver estados con escaneo completo

✅ Para escanear **todos los puertos**:

```bash
nmap -p- 192.168.1.10
```

✔️ Revisará del 1 al 65535.

✅ Muy útil para:

✔️ Encontrar servicios en puertos no estándar.

✔️ Ver estados en puertos poco comunes.

---

### Escaneo con resultados detallados

✅ Agregar **verbose**:

```bash
nmap -v 192.168.1.10
```

✔️ Muestra más información durante el escaneo.

✅ Ejemplo:

```
Initiating Ping Scan
Discovered open port 22/tcp
Discovered closed port 443/tcp
Discovered filtered port 23/tcp
```

---

### Estados y firewalls

✅ **Cómo afectan los firewalls a los estados:**

✔️ **Sin firewall** ➜ abiertos o cerrados claramente.

✔️ **Con firewall permisivo** ➜ estados "closed" claros.

✔️ **Con firewall restrictivo** ➜ estados "filtered" o "open | filtered".

---

✅ 📌 Consejo práctico:

> Muchos administradores **prefieren mostrar puertos "filtered"** para esconder información.

---

### Cómo usar los estados en un pentest

✔️ open ➜ objetivo claro para pruebas de versión, exploits.

✔️ closed ➜ puede monitorearse ➜ puede abrirse en el futuro.

✔️ filtered ➜ necesitas evadir firewalls o usar técnicas diferentes.

✔️ open|filtered ➜ pruebas adicionales para confirmar.

---

### Resumen práctico de estados

✅ **open**

✔️ El servicio está escuchando.

✔️ Puedes interactuar con él.

✅ **closed**

✔️ No hay servicio escuchando.

✔️ El host respondió ➜ está activo.

✅ **filtered**

✔️ Un firewall o filtro impide saber el estado.

✔️ No hay respuesta o paquetes descartados.

✅ **unfiltered**

✔️ Accesible ➜ pero estado indeterminado con esa técnica.

✅ **open | filtered**

✔️ Podría estar abierto o filtrado ➜ no se sabe con certeza.

✅ **closed | filtered**

✔️ Muy raro ➜ ambiguo ➜ se necesita otro método.

---

### Ejemplo de comando recomendado

✅ Escaneo con detección de versión (para open ports):

```bash
nmap -sV 192.168.1.10
```

✅ Escaneo completo y guardado:

```bash
nmap -p- -oN resultado.txt 192.168.1.10
```

✅ Escaneo agresivo (OS, servicios, scripts):

```bash
sudo nmap -A 192.168.1.10
```

---

### Buenas prácticas

✔️ Usa Nmap **solo en redes con permiso**.

✔️ No escanees Internet al azar ➜ puedes generar alertas o problemas legales.

✔️ Documenta bien los resultados.

✔️ Úsalo para **mejorar la seguridad**, no para atacarla sin permiso.

---

### Conclusión

✅ Los **estados de puertos** en Nmap son clave para entender:

✔️ Qué servicios están disponibles.

✔️ Qué está cerrado o bloqueado.

✔️ Dónde puedes enfocar tus pruebas.

✅ Son **la base** del reconocimiento en ciberseguridad.

---

[🔼](#índice)

---

## **31. Nmap: Descubrimiento de servicios**

### ¿Qué es el descubrimiento de servicios en Nmap?

✔️ Cuando escaneas puertos con Nmap, por defecto solo te dice si el puerto está **open**, **closed** o **filtered**.

✅ Pero **no te dice exactamente qué programa está escuchando en ese puerto**.

✅ **Descubrimiento de servicios** = identificar **qué servicio exacto** y **su versión** está corriendo en cada puerto abierto.

---

✅ 📌 Ejemplo simple:

✔️ Escaneo básico:

```
PORT   STATE SERVICE
22/tcp open  ssh
```

➡️ Solo sabes que es "ssh".

✔️ Descubrimiento de servicios:

```
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu
```

➡️ ¡Ahora sabes qué software, con versión!

---

✅ **¿Por qué es útil?**

✔️ Saber exactamente **qué versión** ➜ buscar vulnerabilidades específicas.

✔️ Evitar falsos positivos (no es suficiente saber que está “abierto”, ¡hay que saber qué hay ahí!).

✔️ Planificar exploits o auditorías.

---

### ¿Cómo funciona técnicamente?

✔️ Nmap envía **peticiones específicas** al puerto.

✔️ Analiza las respuestas.

✔️ Compara contra una base de datos interna de **firmas** de servicios.

✔️ Muestra el resultado.

✅ Esto se llama **Service Detection** o **Service Fingerprinting**.

---

✅ Nmap tiene un enorme **archivo de firmas** para reconocer:

- Servidores web (Apache, nginx)
- Servidores SSH (OpenSSH, Dropbear)
- Servidores FTP (vsftpd, ProFTPD)
- Bases de datos (MySQL, PostgreSQL)
- y muchos más.

---

### Opción para descubrimiento de servicios en Nmap

✅ La opción principal es:

```
-sV
```

✔️ Significa ➜ **Service Version Detection**.

✔️ Nmap intentará descubrir **nombre** y **versión** del servicio.

---

✅ Es uno de los modos más populares y más usados de Nmap.

---

### Ejemplo súper básico

✅ Escaneo normal:

```bash
nmap 192.168.1.10
```

✔️ Resultado:

```
PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http
```

➡️ Solo sabes que hay "ssh" y "http".

---

✅ Con descubrimiento de servicios:

```bash
nmap -sV 192.168.1.10
```

✔️ Resultado:

```
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 20.04
80/tcp open  http    Apache httpd 2.4.41
```

✅ Ahora sabes:

✔️ El software ➜ OpenSSH, Apache httpd.

✔️ La versión ➜ 8.2p1, 2.4.41.

✔️ A veces incluso ➜ el sistema operativo base (Ubuntu 20.04).

---

✅ ✅ Súper útil:

- Buscar CVEs (vulnerabilidades) específicas.
- Ver si está desactualizado.
- Saber qué exploit usar.

---

### Otro ejemplo fácil de entender

✅ Imagina un servidor con varios servicios:

✅ Comando:

```bash
nmap -sV 192.168.1.20
```

✅ Resultado:

```
PORT     STATE SERVICE VERSION
21/tcp   open  ftp     vsftpd 3.0.3
22/tcp   open  ssh     OpenSSH 7.6p1 Ubuntu
80/tcp   open  http    Apache httpd 2.4.29 ((Ubuntu))
3306/tcp open  mysql   MySQL 5.7.33-0ubuntu0.18.04.1
```

✅ Interpretación:

✔️ FTP ➜ vsftpd 3.0.3

✔️ SSH ➜ OpenSSH 7.6p1

✔️ HTTP ➜ Apache 2.4.29

✔️ MySQL ➜ 5.7.33

✅ ➜ Puedes buscar vulnerabilidades en esas versiones.

---

### Escanear un rango de IPs

✅ Descubrimiento de servicios en múltiples hosts:

```bash
nmap -sV 192.168.1.10-20
```

✔️ Nmap te dirá **qué servicios corren y sus versiones** en cada máquina.

---

✅ Resultado típico:

```
Nmap scan report for 192.168.1.12
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.4
80/tcp open  http    nginx 1.18.0

Nmap scan report for 192.168.1.15
PORT   STATE SERVICE VERSION
22/tcp open  ssh     Dropbear sshd 2019.78
```

---

### Escaneo de puertos específicos con -sV

✅ Para ahorrar tiempo ➜ enfócate en puertos específicos:

```bash
nmap -sV -p 22,80,443 192.168.1.10
```

✔️ Solo escanea esos puertos.

✔️ Más rápido que escanear todos.

---

### Combinar con rangos de puertos

✅ Escaneo más amplio pero controlado:

```bash
nmap -sV -p 1-1000 192.168.1.10
```

✔️ Revisa los 1000 primeros puertos ➜ mucho más que solo 22 y 80.

---

### Guardar resultados en un archivo

✅ Muy útil en auditorías:

```bash
nmap -sV -oN resultado.txt 192.168.1.10
```

✔️ Guarda la salida legible en `resultado.txt`.

✅ En XML para parseo:

```bash
nmap -sV -oX resultado.xml 192.168.1.10
```

---

### Escaneo agresivo (incluye -sV)

✅ La opción `-A` incluye **detección de servicios** automáticamente:

```bash
sudo nmap -A 192.168.1.10
```

✔️ Incluye:

- Service Detection (-sV)
- OS Detection (-O)
- Scripts NSE
- Trace route

✅ Resultado:

```
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
```

✔️ Además ➜ sistema operativo, scripts de seguridad.

---

### Personalizar nivel de detección de servicios

✔️ Para afinar la detección ➜ usa `--version-intensity`.

✅ Valores:

- 0 ➜ muy rápido, menos preciso.
- 9 ➜ muy exhaustivo, más lento.

✅ Ejemplo:

```bash
nmap -sV --version-intensity 5 192.168.1.10
```

✔️ Nivel medio de intensidad.

---

### Ejemplo práctico paso a paso

✅ 1️⃣ Escaneo básico:

```bash
nmap 192.168.1.10
```

✔️ Resultado:

```
22/tcp open ssh
80/tcp open http
```

---

✅ 2️⃣ Descubrimiento de servicios:

```bash
nmap -sV 192.168.1.10
```

✔️ Resultado:

```
22/tcp open ssh OpenSSH 8.2p1
80/tcp open http Apache 2.4.41
```

---

✅ 3️⃣ Escaneo con más puertos:

```bash
nmap -sV -p 1-1000 192.168.1.10
```

✔️ Revisa más servicios.

---

✅ 4️⃣ Escaneo agresivo:

```bash
sudo nmap -A 192.168.1.10
```

✔️ Resultado ➜ servicios + versiones + OS + scripts.

---

✅ 5️⃣ Guardar resultado:

```bash
nmap -sV -oN servicios.txt 192.168.1.10
```

✔️ Para análisis posterior.

---

### Resumen práctico

| Opción                | Qué hace                                        |
| --------------------- | ----------------------------------------------- |
| `-sV`                 | Detecta servicios y sus versiones               |
| `-A`                  | Escaneo agresivo (incluye -sV, -O, scripts)     |
| `-p`                  | Especifica puertos                              |
| `--version-intensity` | Controla el nivel de detalle del fingerprinting |
| `-oN`, `-oX`, `-oG`   | Guardar resultados en archivos                  |

---

### Buenas prácticas

✔️ **Siempre pide permiso** antes de escanear redes ajenas.

✔️ No abuses de -A en redes sensibles ➜ genera mucho tráfico.

✔️ Ajusta `--version-intensity` si necesitas velocidad o sigilo.

✔️ Documenta resultados ➜ muy útil para auditorías y reportes.

---

### Conclusión

✅ El **descubrimiento de servicios** con Nmap te dice:

✔️ **Qué servicios corren.**

✔️ **Qué versiones usan.**

✔️ **Qué sistema operativo podría estar en uso.**

✅ Es **fundamental** para:

✔️ Enumeración en pentesting.

✔️ Encontrar vulnerabilidades.

✔️ Proteger tu propia infraestructura.

---

[🔼](#índice)

---

## **32. Amap: Descubrimiento de servicios**

### ¿Qué es Amap?

**Amap** es una herramienta antigua pero todavía útil que sirve para **identificar qué servicio se está ejecutando en un puerto abierto**.

📌 Mientras que Nmap también hace esto con `-sV`, **Amap es más especializado** en el _fingerprinting_ de aplicaciones.

---

✅ **¿Por qué usar Amap?**

✔️ Porque:

- Detecta protocolos y servicios aunque estén en puertos _no estándar_.
- Es rápido y sencillo.
- A veces identifica servicios que Nmap no reconoce bien.
- Se complementa con otras herramientas.

---

✅ **Diferencia principal con Nmap:**

- **Nmap** primero hace descubrimiento de hosts y escaneo de puertos.
- **Amap** se centra solo en **identificar qué corre en puertos abiertos** que tú ya conoces.

👉 Por eso, normalmente usas primero Nmap (para encontrar puertos abiertos), y luego Amap (para saber qué servicio hay).

---

### ¿Cómo se instala Amap?

**En Kali Linux** y muchas distribuciones ya viene instalado.

Si no lo tienes:

**Debian/Ubuntu/Kali:**

```bash
sudo apt update
sudo apt install amap
```

Verifica la versión:

```bash
amap -h
```

Te mostrará la ayuda.

---

### ¿Cómo funciona Amap?

✔️ Le dices **IP y puerto** y él:

- Envía peticiones conocidas a ese puerto.
- Observa la respuesta.
- La compara con su base de datos de firmas (`amap.dat`).
- Te dice qué protocolo/servicio ha detectado.

---

✅ Ejemplo sencillo:

Si un servicio SSH corre en el puerto 2222 (no estándar), Nmap puede no reconocerlo bien, pero Amap sí.

---

### Ejemplo básico de uso

**Sintaxis:**

```
amap <IP> <PUERTO>
```

✅ Ejemplo:

```bash
amap 192.168.1.10 22
```

Si el puerto 22 es SSH, verás algo como:

```
22/tcp open  ssh
```

---

### Escaneo de múltiples puertos

Puedes poner varios puertos separados por espacios:

✅ Ejemplo:

```bash
amap 192.168.1.10 21 22 23 80 443
```

Resultado típico:

```
21/tcp open  ftp
22/tcp open  ssh
23/tcp open  telnet
80/tcp open  http
443/tcp open  ssl/http
```

---

### Leer puertos desde un archivo

Si tienes un archivo con IPs y puertos (por ejemplo, sacado de Nmap), puedes usarlo directamente.

✅ Ejemplo:

1️⃣ Crear un archivo `puertos.txt`:

```
192.168.1.10 22
192.168.1.10 80
192.168.1.20 8080
```

2️⃣ Ejecutar:

```bash
amap -i puertos.txt
```

---

### Descubrimiento UDP

Amap también soporta UDP, usando la opción `-U`.

✅ Ejemplo:

```bash
amap -U 192.168.1.10 161
```

Detectará si hay SNMP u otro servicio UDP.

---

### Modo “verbose” para ver más detalles

Para ver más información de cómo hace la detección, añade `-v`:

✅ Ejemplo:

```bash
amap -v 192.168.1.10 22
```

---

### Guardar resultados en un archivo

Usa `-o` para guardar la salida:

✅ Ejemplo:

```bash
amap -o resultado_amap.txt 192.168.1.10 21 22 80
```

Así tendrás un informe en texto plano.

---

### Ejemplo práctico paso a paso

Imagina que con Nmap descubriste esto:

```
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
2222/tcp open  unknown
8080/tcp open  unknown
```

Ves puertos **"unknown"** (no identificados).

✅ Usar Amap para identificarlos:

```bash
amap 192.168.1.10 2222 8080
```

✅ Resultado:

```
2222/tcp open ssh
8080/tcp open http-proxy
```

✔️ Ahora sabes:

- 2222 es un SSH en puerto no estándar.
- 8080 es un proxy HTTP.

---

✅ Esto es muy útil porque muchos servicios corren en puertos _raros_.

---

### Opciones comunes de Amap

| Opción         | Qué hace                         |
| -------------- | -------------------------------- |
| `-b`           | Modo batch (no interactivo)      |
| `-i <archivo>` | Leer IPs y puertos desde archivo |
| `-o <archivo>` | Guardar resultados en archivo    |
| `-v`           | Modo verbose (más detalle)       |
| `-U`           | Escaneo UDP                      |
| `-q`           | Modo silencioso (menos salida)   |

---

### Comparativa con Nmap

| Característica             | Nmap          | Amap                                   |
| -------------------------- | ------------- | -------------------------------------- |
| Descubrimiento de hosts    | ✅ Sí         | ❌ No                                  |
| Escaneo de puertos         | ✅ Sí         | ❌ No                                  |
| Identificación de servicio | ✅ Sí (`-sV`) | ✅ Sí (principal función)              |
| Detección de versión       | ✅ Sí         | ✅ Limitada                            |
| Soporte activo             | ✅ Muy activo | ❌ Ya no recibe muchas actualizaciones |

👉 **Conclusión**: Nmap es más completo, pero Amap puede encontrar algunos servicios en puertos raros que Nmap no detecta bien.

---

### Buenas prácticas de uso

✔️ Primero usa **Nmap** para descubrir puertos abiertos.

✔️ Luego usa **Amap** para identificar qué hay en esos puertos si Nmap no lo detecta.

✔️ No escanees redes sin permiso (puede generar alertas).

✔️ Guarda siempre los resultados para tu informe.

---

### Ejemplo completo de flujo

1️⃣ Escanear todos los puertos con Nmap:

```bash
nmap -p- 192.168.1.10
```

2️⃣ Detectar servicios con Nmap:

```bash
nmap -sV 192.168.1.10
```

3️⃣ Si quedan puertos "unknown", usar Amap:

```bash
amap 192.168.1.10 2222 8080
```

4️⃣ Guardar el resultado:

```bash
amap -o servicios.txt 192.168.1.10 2222 8080
```

Así tendrás:

- Qué puertos están abiertos.
- Qué servicios corren.
- Qué versiones usan.

---

### Resumen rápido

**Amap**:

✅ Herramienta específica para identificar servicios en puertos abiertos.

✅ Muy útil en puertos no estándar.

✅ Complemento de Nmap.

✅ Fácil de usar con comandos simples.

---

[🔼](#índice)

---

## **33. Nmap: Identificación del sistema operativo**

### ¿Qué es la detección de sistema operativo con Nmap?

✔️ Es una técnica para **adivinar el sistema operativo (OS)** que corre en un dispositivo remoto.

✔️ Nmap analiza **cómo responde la máquina a distintos paquetes** de red.

✔️ Intenta determinar **familia del sistema operativo**, versión aproximada e incluso detalles de red.

✅ 📌 **Ejemplo:**

> Saber si es Linux, Windows, FreeBSD, etc.

> Saber si es Ubuntu 20.04, Windows 10, etc.

---

✅ **¿Para qué sirve?**

✔️ Planificar un ataque (elegir exploits compatibles).

✔️ Ajustar scripts NSE.

✔️ Mejorar la auditoría.

✔️ Saber qué sistemas hay en tu red ➜ inventario.

---

✅ Es **uno de los pasos más importantes en reconocimiento (recon)** en pentesting y ciberseguridad defensiva.

---

### ¿Cómo funciona? (Explicación sencilla)

✔️ Nmap envía **paquetes especialmente diseñados** al objetivo.

✔️ Analiza cosas como:

- Respuesta a paquetes TCP con flags raros.
- Ventana de tamaño TCP.
- TTL (Time To Live).
- Opciones de TCP.
- ICMP replies.

✔️ Cada sistema operativo tiene **patrones únicos**.

✔️ Nmap compara las respuestas con su **base de datos de firmas OS** (`nmap-os-db`).

✅ Resultado ➜ predicción del sistema operativo.

---

✅ 📌 **Analogía sencilla:**

> Imagínate que llamas a una puerta y escuchas la voz del dueño ➜ puedes adivinar quién es.

---

### ¿Qué comando se usa?

✔️ La opción principal es:

```
-O
```

✅ Significa ➜ **OS detection**.

---

### Ejemplo básico

✅ Comando:

```bash
sudo nmap -O 192.168.1.10
```

✅ Resultado típico:

```
OS details: Linux 3.2 - 4.9
Network Distance: 1 hop
```

✔️ Te dice:

- **Sistema operativo:** Linux.
- **Versión aproximada del kernel:** 3.2 - 4.9.
- **Distancia de red (saltos):** 1 ➜ en la misma red local.

---

### Ejemplo con más detalle

✅ Comando:

```bash
sudo nmap -O 192.168.1.20
```

✅ Resultado:

```
OS details: Microsoft Windows 10 1703 (Build 15063)
Network Distance: 1 hop
```

✔️ Aquí Nmap identificó:

- **Sistema operativo:** Windows 10.
- **Versión:** 1703.

✅ Súper útil ➜ puedes buscar exploits específicos.

---

### Detección de OS + Servicios

✅ Puedes combinarlo con `-sV` para descubrir servicios y versiones:

```bash
sudo nmap -O -sV 192.168.1.10
```

✅ Resultado:

```
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
OS details: Linux 5.4 (Ubuntu 20.04)
```

✔️ Ahora tienes:

- Servicios + versiones.
- Sistema operativo + versión.

---

### Escaneo agresivo (incluye OS detection)

✅ La opción `-A` combina varias cosas, incluyendo OS detection:

```bash
sudo nmap -A 192.168.1.10
```

✔️ Incluye:

- `-O` ➜ OS detection.
- `-sV` ➜ Service/version detection.
- NSE scripts básicos.
- Trace route.

✅ Resultado súper detallado ➜ muy usado en auditorías.

---

### Nivel de precisión y confiabilidad

✔️ Nmap da un **OS guess (suposición)** con un puntaje de confianza (accuracy).

✅ Ejemplo de salida con puntaje:

```
OS guesses: Linux 3.2 - 4.9 (96%)
```

✔️ 96% de certeza ➜ bastante confiable.

---

✅ A veces no puede adivinar:

```
No OS matches for host
```

✔️ Puede pasar si:

- Firewall bloquea paquetes.
- Sistema no responde "normalmente".
- Muy lejos en la red.

---

### Forzar detección con más pruebas

✔️ Usa `--osscan-guess` para forzar un guess cuando la confianza es baja:

✅ Ejemplo:

```bash
sudo nmap -O --osscan-guess 192.168.1.10
```

✔️ A veces te da _mejor pista_ aunque menos confiable.

---

### Identificar hosts en un rango

✅ Puedes detectar SO de varios hosts a la vez:

```bash
sudo nmap -O 192.168.1.10-20
```

✔️ Muy útil en redes internas.

✅ Resultado ejemplo:

```
Nmap scan report for 192.168.1.11
OS details: Linux 5.4 (Ubuntu 20.04)

Nmap scan report for 192.168.1.15
OS details: Microsoft Windows 7 Professional
```

---

### Ver más detalle (verbose)

✅ Usa `-v` o `-vv` para más información:

```bash
sudo nmap -O -v 192.168.1.10
```

✔️ Verás qué pruebas manda Nmap y cómo decide.

---

### Guardar resultados en archivo

✅ Salida legible:

```bash
sudo nmap -O -oN os_detection.txt 192.168.1.10
```

✅ En XML:

```bash
sudo nmap -O -oX os_detection.xml 192.168.1.10
```

✔️ Ideal para informes o parseo.

---

### Ejemplo práctico paso a paso

✅ 1️⃣ Escaneo básico de puertos:

```bash
nmap 192.168.1.10
```

✔️ Ver puertos abiertos.

---

✅ 2️⃣ Detección de servicios:

```bash
nmap -sV 192.168.1.10
```

✔️ Ver qué servicios y versiones hay.

---

✅ 3️⃣ Detección de sistema operativo:

```bash
sudo nmap -O 192.168.1.10
```

✔️ Ver sistema operativo probable.

---

✅ 4️⃣ Todo junto:

```bash
sudo nmap -A 192.168.1.10
```

✔️ Escaneo agresivo ➜ servicios + OS + scripts.

---

✅ 5️⃣ Guardar en archivo:

```bash
sudo nmap -A -oN auditoria.txt 192.168.1.10
```

✔️ Para el reporte.

---

### Limitaciones

⚠️ La detección de OS:

✔️ Depende de que el host responda bien.

✔️ Firewalls y filtros pueden bloquear las señales.

✔️ NAT puede falsear resultados.

✔️ VPN puede alterar TTL.

✅ A veces tendrás **"No OS matches"** ➜ prueba otras técnicas o herramientas.

---

### Buenas prácticas

✔️ Usa siempre **con permiso** ➜ escaneo activo ➜ puede generar alertas.

✔️ Combina con otras técnicas ➜ fingerprinting de banners, servicios.

✔️ Documenta bien resultados.

✔️ Usa `-A` solo cuando sea necesario ➜ es ruidoso.

---

### Resumen rápido de comandos

| Comando                            | Qué hace                                      |
| ---------------------------------- | --------------------------------------------- |
| `sudo nmap -O <IP>`                | Detección básica de sistema operativo         |
| `sudo nmap -O --osscan-guess <IP>` | Forzar predicción cuando la confianza es baja |
| `sudo nmap -O -v <IP>`             | Más detalle de la detección                   |
| `sudo nmap -A <IP>`                | Escaneo agresivo (OS + servicios + scripts)   |
| `-oN`, `-oX`                       | Guardar resultados en archivo                 |

---

### Conclusión

✅ La **detección de sistema operativo** con Nmap es:

✔️ Fundamental para pentesters y auditores.

✔️ Útil para planificar ataques o mejorar defensas.

✔️ Basada en fingerprinting avanzado.

✅ Nmap ➜ herramienta esencial para este trabajo.

---

[🔼](#índice)

---

## **34. Nmap: SMB Enumeration**

### ¿Qué es SMB?

✔️ **SMB (Server Message Block)** es un protocolo de red usado principalmente en **Windows** para:

✅ Compartir archivos y carpetas.

✅ Compartir impresoras.

✅ Acceso remoto a recursos.

✅ Autenticación y comunicación entre máquinas en una red.

---

✅ **Ejemplo simple:**

- Tu PC con Windows accede a `\\Servidor\CarpetaCompartida` usando SMB.
- Empresas usan SMB para compartir recursos entre empleados.

---

📌 SMB típicamente usa los puertos:

- **TCP 445** (moderno)
- **TCP 139** (NetBIOS/SMB antiguo)

---

### ¿Qué es "SMB Enumeration"?

**Enumerar SMB** = **Obtener información** del servicio SMB expuesto en un host.

✅ Puedes descubrir:

✔️ Nombre del sistema.

✔️ Dominio/Grupo de trabajo.

✔️ Usuarios.

✔️ Shares/carpetas compartidas.

✔️ Versiones del protocolo SMB.

✔️ Vulnerabilidades (como EternalBlue).

---

✅ ¿Para qué sirve?

✔️ Planificar ataques (explotar vulnerabilidades SMB).

✔️ Obtener información de la red.

✔️ Verificar seguridad y configuraciones.

✔️ Auditar qué recursos están expuestos.

---

✅ Es un **paso clave en pentesting interno o de red**.

---

### ¿Cómo ayuda Nmap?

Nmap tiene **scripts NSE** (Nmap Scripting Engine) especializados para **enumerar SMB**.

✅ Usas el argumento:

```
--script
```

✅ Hay docenas de scripts SMB pre-hechos, como:

- `smb-os-discovery`
- `smb-enum-shares`
- `smb-enum-users`
- `smb-vuln-*` (chequeo de vulnerabilidades)

---

### Antes de empezar ➜ Identificar puertos SMB

✔️ Normalmente quieres confirmar que SMB está abierto.

✅ Comando básico:

```bash
nmap -p 445,139 <IP>
```

✅ Resultado:

```
PORT    STATE SERVICE
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
```

✔️ Perfecto ➜ puedes intentar enumerar SMB.

---

### Ejemplo 1: Descubrir sistema operativo y dominio

✅ Script NSE ➜ `smb-os-discovery`

✔️ Comando:

```bash
nmap --script smb-os-discovery -p 445 <IP>
```

✅ Resultado típico:

```
Host script results:
| smb-os-discovery:
|   OS: Windows 10 Pro 1909 (Build 18363)
|   Computer name: VICTIMA-PC
|   NetBIOS computer name: VICTIMA-PC
|   Workgroup: WORKGROUP
```

✅ ¿Qué aprendiste?

✔️ Sistema operativo exacto.

✔️ Nombre de la máquina.

✔️ Workgroup.

✅ Usos:

✔️ Planificar exploits.

✔️ Enumerar más objetivos en la red.

---

### Ejemplo 2: Enumerar carpetas compartidas (shares)

✅ Script NSE ➜ `smb-enum-shares`

✔️ Comando:

```bash
nmap --script smb-enum-shares -p 445 <IP>
```

✅ Resultado típico:

```
| smb-enum-shares:
|   ADMIN$      Disk   Remote Admin
|   C$          Disk   Default share
|   IPC$        IPC    Remote IPC
|   Public      Disk   Public Files
```

✅ Interpretación:

✔️ Viste las **shares** disponibles.

✔️ Algunas pueden ser públicas o mal configuradas.

✔️ Admin\$ y C\$ son administrativas (requieren credenciales).

---

### Ejemplo 3: Enumerar usuarios

✅ Script NSE ➜ `smb-enum-users`

✔️ Comando:

```bash
nmap --script smb-enum-users -p 445 <IP>
```

✅ Resultado típico:

```
| smb-enum-users:
|   Guest
|   Admin
|   Juan
|   Maria
```

✅ Usos:

✔️ Enumerar posibles cuentas para ataques de fuerza bruta o password spraying.

✔️ Confirmar exposición de información.

---

### Ejemplo 4: Combinación de scripts

✅ Puedes ejecutar varios scripts NSE a la vez:

✔️ Comando:

```bash
nmap --script smb-os-discovery,smb-enum-shares,smb-enum-users -p 445 <IP>
```

✅ Resultado ➜ un informe completo:

✔️ OS.

✔️ Nombre de máquina.

✔️ Shares.

✔️ Usuarios.

---

### Ejemplo 5: Detectar vulnerabilidades SMB

✅ Nmap incluye scripts para detectar vulnerabilidades conocidas.

✅ Muy popular ➜ Checar EternalBlue (MS17-010)

✔️ Comando:

```bash
nmap --script smb-vuln-ms17-010 -p 445 <IP>
```

✅ Resultado:

```
| smb-vuln-ms17-010:
|   VULNERABLE:
|   Remote Code Execution vulnerability in Microsoft SMBv1 servers (ms17-010)
|   State: VULNERABLE
|   IDs: CVE:CVE-2017-0143
```

✅ ¡Advertencia!

✔️ Ahora sabes si el host es vulnerable al exploit **EternalBlue**.

✔️ Muy importante para evaluar seguridad.

---

✅ Hay otros scripts de vulnerabilidades, por ejemplo:

- `smb-vuln-cve2009-3103`
- `smb-vuln-ms10-054`
- `smb-vuln-ms10-061`

✅ Puedes usarlos todos así:

```bash
nmap --script smb-vuln-* -p 445 <IP>
```

---

### Uso con rangos de IP

✅ Puedes escanear una red completa:

```bash
nmap --script smb-os-discovery -p 445 192.168.1.0/24
```

✔️ Descubre SO de todas las máquinas con SMB activo.

---

### Verbose y detalle

✅ Agrega `-v` o `-vv` para más información:

```bash
nmap -v --script smb-enum-shares -p 445 <IP>
```

✔️ Muestra más pasos y resultados.

---

✅ Agrega salida a archivo:

```bash
nmap --script smb-os-discovery -p 445 <IP> -oN resultado_smb.txt
```

✔️ Guarda tu auditoría.

---

### Ejemplo práctico completo (paso a paso)

✅ 1️⃣ Confirmar puertos SMB:

```bash
nmap -p 139,445 <IP>
```

✅ 2️⃣ Detección de sistema operativo:

```bash
nmap --script smb-os-discovery -p 445 <IP>
```

✅ 3️⃣ Enumerar shares:

```bash
nmap --script smb-enum-shares -p 445 <IP>
```

✅ 4️⃣ Enumerar usuarios:

```bash
nmap --script smb-enum-users -p 445 <IP>
```

✅ 5️⃣ Buscar vulnerabilidades:

```bash
nmap --script smb-vuln-* -p 445 <IP>
```

✅ 6️⃣ Todo junto:

```bash
nmap --script smb-os-discovery,smb-enum-shares,smb-enum-users,smb-vuln-* -p 445 <IP>
```

✅ 7️⃣ Guardar resultados:

```bash
nmap --script smb-os-discovery,smb-enum-shares -p 445 <IP> -oN informe_smb.txt
```

---

### Resumen rápido de scripts útiles

| Script              | Qué hace                                      |
| ------------------- | --------------------------------------------- |
| `smb-os-discovery`  | Descubre sistema operativo y nombre de equipo |
| `smb-enum-shares`   | Lista carpetas compartidas                    |
| `smb-enum-users`    | Lista usuarios SMB                            |
| `smb-vuln-ms17-010` | Chequea EternalBlue                           |
| `smb-vuln-*`        | Ejecuta todos los scripts de vulnerabilidad   |

---

### Buenas prácticas

✔️ **Siempre con permiso** ➜ estos son escaneos activos.

✔️ Usa en auditorías y pentests controlados.

✔️ Guarda resultados ➜ importante para el reporte.

✔️ Revisa exposición innecesaria ➜ cierra o limita shares.

✔️ Actualiza y parchea ➜ evita vulnerabilidades SMB conocidas.

---

### Conclusión

✅ **SMB Enumeration con Nmap** es una técnica esencial para:

✔️ Descubrir información valiosa.

✔️ Evaluar la seguridad de sistemas Windows (y Samba en Linux).

✔️ Encontrar shares expuestos.

✔️ Detectar usuarios válidos.

✔️ Verificar vulnerabilidades graves.

✅ Usar Nmap + NSE ➜ rápido, potente y muy flexible.

---

[🔼](#índice)

---

## **35. Nmap: SNMP Enumeration**

### ¿Qué es SNMP?

**SNMP** (Simple Network Management Protocol) es un protocolo usado para **monitorear y administrar dispositivos de red** como routers, switches, impresoras, servidores, etc.

✅ Con SNMP puedes:

- Ver estadísticas del sistema (CPU, RAM, disco).
- Consultar nombre del host.
- Ver interfaces de red y su estado.
- Obtener listas de usuarios.
- Cambiar configuraciones (si tienes permisos de escritura).

---

✅ SNMP usa principalmente:

- **UDP puerto 161** para consultas.
- **UDP puerto 162** para traps (notificaciones de eventos).

---

📌 **Importante**: SNMP puede filtrar **mucha información sensible** si no está bien configurado, especialmente si usa la **comunidad pública “public”** (sin contraseña real).

---

### ¿Qué es SNMP Enumeration?

**SNMP Enumeration** = Extraer información de un dispositivo a través de SNMP.

Puedes obtener:

- Nombre del host.
- Descripción del sistema.
- Uptime.
- Interfaces de red.
- Rutas.
- Tablas ARP.
- Procesos.
- Usuarios.
- Información de hardware/software.

🔍 **Ideal para pentesting, auditoría de red o ciberseguridad ofensiva.**

---

### ¿Qué papel cumple Nmap?

Nmap tiene **scripts NSE especializados para SNMP**, que permiten:

✅ Enumerar:

- Información del sistema.
- Interfaces de red.
- Usuarios y procesos.
- Servidores SNMP mal configurados.

✅ Y todo esto de forma **rápida y automática**, sin herramientas externas.

---

### Paso 1: Identificar si SNMP está activo

Antes de enumerar, veamos si el puerto UDP 161 está abierto.

✅ Comando:

```bash
nmap -sU -p 161 <IP>
```

✅ Resultado típico:

```
PORT    STATE SERVICE
161/udp open  snmp
```

✔️ Si ves que está “**open**”, puedes hacer SNMP enumeration.

---

### Paso 2: Usar scripts NSE de Nmap para SNMP

#### 📌 Script 1: `snmp-info`

🔍 **Extrae información básica del sistema.**

✅ Comando:

```bash
nmap -sU -p 161 --script=snmp-info <IP>
```

✅ Resultado:

```
| snmp-info:
|  enterprise: Cisco
|  contact: admin@empresa.com
|  name: Router-Central
|  location: Sala servidores
|  description: Cisco IOS Software Version 12.4
|_ uptime: 12 days, 4 hours, 33 minutes
```

✔️ Obtuviste:

- Fabricante.
- Nombre del dispositivo.
- Uptime.
- Localización física.
- Versión de software.

📌 Todo eso puede ayudarte a:

- Planificar un ataque.
- Detectar equipos vulnerables.
- Hacer inventario en una red.

---

#### 📌 Script 2: `snmp-interfaces`

🔍 **Lista las interfaces de red y su estado.**

✅ Comando:

```bash
nmap -sU -p 161 --script=snmp-interfaces <IP>
```

✅ Resultado:

```
| snmp-interfaces:
|  eth0: up, 1000Mbps, MAC: 00:1A:2B:3C:4D:5E
|  eth1: down
|_ wlan0: up, 300Mbps, MAC: 00:1A:2B:3C:4D:5F
```

✔️ Esto te da:

- Interfaces activas.
- Dirección MAC.
- Velocidad.
- Estado (up/down).

✅ Puedes identificar hosts por su MAC o interfaz activa.

---

#### 📌 Script 3: `snmp-processes`

🔍 **Muestra los procesos corriendo en el dispositivo.**

✅ Comando:

```bash
nmap -sU -p 161 --script=snmp-processes <IP>
```

✅ Resultado:

```
| snmp-processes:
|   PID  Name           Path
|   123  httpd          /usr/sbin/httpd
|   456  sshd           /usr/sbin/sshd
|_  789  mysqld         /usr/bin/mysqld
```

✔️ Con esto sabes:

- Qué servicios están corriendo.
- Puedes buscar vulnerabilidades específicas.

---

#### 📌 Script 4: `snmp-win32-users` (si el host es Windows)

✅ Comando:

```bash
nmap -sU -p 161 --script=snmp-win32-users <IP>
```

✅ Resultado:

```
| snmp-win32-users:
|  Administrador
|  Juan
|  Maria
|_ Invitado
```

✔️ Puedes usar esos nombres en ataques de fuerza bruta o en informes de auditoría.

---

### Paso 3: Combinación de scripts útiles

✅ Ejecuta varios scripts juntos:

```bash
nmap -sU -p 161 --script=snmp-info,snmp-interfaces,snmp-processes <IP>
```

✔️ Te dará un informe completo de:

- Info del sistema.
- Interfaces.
- Procesos.

---

✅ O usa todos los scripts SNMP disponibles:

```bash
nmap -sU -p 161 --script "snmp-*" <IP>
```

🔎 Esto ejecutará todos los scripts NSE relacionados con SNMP.

---

### Paso 4: Guardar resultados en un archivo

✅ Comando:

```bash
nmap -sU -p 161 --script=snmp-info <IP> -oN snmp_enumeration.txt
```

✔️ Muy útil para auditorías o reportes.

---

### Prueba en red local

Puedes probar en tu red local con un router, switch o VM con SNMP activado (como Metasploitable2/3).

✅ En Metasploitable2:

```bash
nmap -sU -p 161 --script=snmp-* 192.168.1.100
```

✔️ Verás mucha información sin autenticación si usa la comunidad "public".

---

### ¿Qué pasa si el host no permite SNMP?

✅ Puede que SNMP:

- Esté deshabilitado.
- Use comunidades personalizadas (no “public”).
- Filtre por IPs (solo ciertas máquinas pueden consultarlo).

✅ Resultado de Nmap:

```
161/udp closed
```

➡️ En ese caso no se puede enumerar SNMP desde fuera.

---

### Buenas prácticas

🔐 Para administradores:

- Cambiar comunidad “public” por una personalizada.
- Usar SNMPv3 (más seguro).
- Restringir acceso SNMP por IP.
- Desactivar si no se usa.

🚫 Para pentesters:

- No ejecutar sin permiso.
- Guardar evidencia.
- Incluir hallazgos SNMP en tu informe final.

---

### Resumen de comandos útiles

| Tarea                       | Comando                                          |
| --------------------------- | ------------------------------------------------ |
| Detectar puerto UDP 161     | `nmap -sU -p 161 <IP>`                           |
| Info del sistema            | `nmap -sU -p 161 --script=snmp-info <IP>`        |
| Interfaces de red           | `nmap -sU -p 161 --script=snmp-interfaces <IP>`  |
| Procesos activos            | `nmap -sU -p 161 --script=snmp-processes <IP>`   |
| Enumerar usuarios (Windows) | `nmap -sU -p 161 --script=snmp-win32-users <IP>` |
| Todos los scripts SNMP      | `nmap -sU -p 161 --script="snmp-*" <IP>`         |
| Guardar resultado           | `-oN salida.txt`                                 |

---

### Conclusión

🎯 Con **SNMP Enumeration** usando **Nmap** puedes:

- Obtener info muy valiosa de sistemas sin autenticación.
- Enumerar procesos, usuarios, interfaces y datos del host.
- Detectar configuraciones inseguras.
- Planificar ataques o recomendaciones de seguridad.

✅ Es una técnica clave en auditorías y pentesting de redes.

---

[🔼](#índice)

---

| **Inicio**         | **atrás 3**                                            | **Siguiente 5**                             |
| ------------------ | ------------------------------------------------------ | ------------------------------------------- |
| [🏠](../README.md) | [⏪](./2_3_Recopilacion_semi_pasiva_de_informacion.md) | [⏩](./2_5_Analisis_de_Vulnerabilidades.md) |
