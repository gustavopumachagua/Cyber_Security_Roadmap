| **Inicio**         | **atrás 4**           | **Siguiente 6**      |
| ------------------ | --------------------- | -------------------- |
| [🏠](../README.md) | [⏪](./3_4_Whonix.md) | [⏩](./3_6_TAILS.md) |

---

## **Índice**

| Temario                                                                                      |
| -------------------------------------------------------------------------------------------- |
| [129. ¿Qué es Qubes OS?](#129-qué-es-qubes-os)                                               |
| [130. Instalación de Qubes OS](#130-instalación-de-qubes-os)                                 |
| [131. Navegación segura en Qubes OS](#131-navegación-segura-en-qubes-os)                     |
| [132. Gestión segura de ficheros en Qubes OS](#132-gestión-segura-de-ficheros-en-qubes-os)   |
| [133. Disposable Qube](#133-disposable-qube)                                                 |
| [134. Qubes Manager y gestión de aplicaciones](#134-qubes-manager-y-gestión-de-aplicaciones) |
| [135. Creación de nuevos Qubes](#135-creación-de-nuevos-qubes)                               |
| [136. Whonix con Qubes OS](#136-whonix-con-qubes-os)                                         |

---

# **Qubes OS**

## **129. ¿Qué es Qubes OS?**

### ✅ ¿QUÉ ES QUBES OS? (Explicación sencilla)

**Qubes OS** es un **sistema operativo** orientado a la **seguridad y privacidad extrema**.

🌟 Su lema es:

> _“Security through compartmentalization”_ (Seguridad mediante compartimentación).

✅ Significa que **divide tu computadora en compartimentos aislados** llamados **qubes**.

---

### ⭐ Idea clave (ultra simple):

✔️ En Windows o Linux normales → TODAS tus apps están juntas.

❌ Si un virus infecta una app → Podría infectarlas todas.

✔️ En Qubes OS → Cada tarea corre en su propio **qube** aislado.

✅ Si una se infecta → No puede saltar a las demás.

---

#### ⭐ Ejemplo fácil:

✅ Tienes:

- Un qube para correo.
- Un qube para navegar.
- Un qube para banca en línea.
- Un qube para trabajo.

✔️ Si tu navegador se infecta → NO puede espiar tu banca.

---

✅ Resultado:

✅ **Aislamiento completo**.

✅ **Mínimo daño si algo se compromete.**

---

### ✅ ¿CÓMO FUNCIONA QUBES OS? (Con ejemplos fáciles)

**Qubes OS** se basa en la idea de **virtualización ligera**.

✔️ Usa un **hipervisor** (Xen) para crear “mini máquinas virtuales” (qubes).

✔️ Cada qube → Su propio mini-sistema aislado.

✔️ Tienen permisos limitados.

---

✅ Ejemplo muy sencillo:

➡️ Imagina tu PC como un **edificio de oficinas**.

✔️ Cada qube es una **habitación cerrada con llave**.

✔️ Para pasar de una habitación a otra → Debes usar puertas controladas.

✔️ El sistema vigila quién puede entrar o salir.

---

#### ✅ Tipos de Qubes

1️⃣ **App Qubes**

- Donde abres apps: navegador, correo, LibreOffice.
- Totalmente aislados.

2️⃣ **Template Qubes**

- Plantillas con el sistema base (Fedora, Debian).
- No guardan tus datos, solo el sistema.

3️⃣ **Service Qubes**

- Manejan red, almacenamiento, actualizaciones.

4️⃣ **Disposable Qubes**

- Sesión de un solo uso → Cuando cierras, se destruye.

---

#### ⭐ Ejemplo práctico

✅ App Qube: **work-qube**

- Abres tu cliente de correo.

✅ App Qube: **bank-qube**

- Abres tu banca en línea.

✅ Si malware infecta **work-qube** → NO puede ver **bank-qube**.

---

### ✅ ¿POR QUÉ ES TAN SEGURO?

✅ Compartimentación = Seguridad.

✔️ Si algo se rompe → Solo afecta ese qube.

✔️ No se propaga a todo el sistema.

---

#### ⭐ Analogía fácil

✔️ PC normal = Todo en un solo cuarto.

❗ Se incendia → Todo se quema.

✔️ Qubes OS = Varios cuartos sellados.

🔥 Si un cuarto se incendia → Los demás siguen seguros.

---

✅ También:

✔️ **Red aislada**: qubes de red manejan la conexión.

✔️ **Almacenamiento cifrado**.

✔️ **Desechables**: qubes temporales que desaparecen al cerrar.

✔️ **Control total de permisos**.

---

#### ✅ EJEMPLOS DE USO

✅ Juan es periodista:

- Un qube para investigar en la web.
- Un qube para escribir artículos.
- Un qube para comunicarse con fuentes.
- Un qube desechable para abrir documentos sospechosos.

✅ Si alguien envía malware → Juan lo abre en un qube desechable → Al cerrarlo se destruye.

---

✅ Ana es desarrolladora:

- Un qube para código personal.
- Un qube para proyectos del cliente.
- Un qube para Internet normal.
- Un qube para pentesting con herramientas ofensivas.

✅ Así evita mezclar datos o comprometer su máquina.

---

### ✅ VENTAJAS CLAVE

✔️ Aislamiento → Seguridad real.

✔️ Control de permisos → Decides qué puede comunicarse con qué.

✔️ Integración → Ventanas de diferentes qubes aparecen en el mismo escritorio pero siguen aisladas.

✔️ Descartables → Para abrir cosas peligrosas.

✔️ Compatible con Whonix → Para navegación anónima en TOR.

---

### ✅ INSTALACIÓN DE QUBES OS (EXPLICADA FÁCIL)

✔️ Qubes OS es un sistema operativo completo.

✔️ Debes instalarlo como harías con Linux, pero con algunas particularidades.

---

#### ⭐ Requisitos mínimos

✅ Procesador compatible con virtualización (Intel VT-x / AMD-V).

✅ 8 GB de RAM (recomendado 16 GB).

✅ 40 GB de espacio libre (mejor más).

✅ Compatible con UEFI.

---

#### ⭐ PASO 1️⃣: Descargar Qubes OS

✅ Ve al sitio oficial:

```
https://www.qubes-os.org/downloads/
```

✔️ Descarga el archivo ISO.

✔️ Verifica la firma (opcional pero recomendado para seguridad).

---

#### ⭐ PASO 2️⃣: Crear USB booteable

✅ Usa herramientas como:

- **balenaEtcher** (fácil y gratis)
- **Rufus** (Windows)
- **dd** (Linux)

✅ Ejemplo con Etcher:

- Abrir Etcher.
- Seleccionar ISO.
- Seleccionar USB.
- Hacer clic en Flash.

---

#### ⭐ PASO 3️⃣: Bootear desde el USB

✔️ Reinicia tu computadora.

✔️ Entra al menú de arranque (usualmente F12, F2 o ESC según la marca).

✔️ Selecciona el USB.

---

#### ⭐ PASO 4️⃣: Instalador de Qubes

✔️ Pantalla de bienvenida → **Install Qubes OS**.

✔️ Elegir idioma.

✔️ Configurar disco:

- Puedes borrar el disco y usarlo todo para Qubes.
- O hacer partición personalizada.

✔️ Define contraseña de administrador.

---

#### ⭐ PASO 5️⃣: Esperar la instalación

✔️ Suele tardar entre 20 y 60 minutos, según el equipo.

✔️ Cuando termine → Reinicia.

✔️ Retira el USB.

---

#### ⭐ PASO 6️⃣: Configuración inicial

✅ Primer arranque:

✔️ Crea qubes por defecto → Recomendado.

✔️ Configura red.

✔️ Activa qubes de Whonix (opcional → para TOR).

✔️ Actualiza el sistema.

---

### ✅ USO BÁSICO (MUY FÁCIL DE ENTENDER)

✔️ Escritorio de Qubes OS → Ventanas de apps de distintos qubes.

✔️ Color de borde → Indica de qué qube es.

✅ Ejemplo práctico:

- Azul → work-qube (correo).
- Verde → personal-qube (navegador).
- Rojo → untrusted-qube (descargas sospechosas).

✔️ No pueden hablar entre sí sin permiso.

---

#### ⭐ Disposable Qubes

✅ Abres un documento sospechoso:

✔️ Botón derecho → **Abrir en Disposable Qube**.

✔️ Se destruye al cerrar → Nada persiste.

---

### ✅ USO DE WHONIX EN QUBES

✔️ Qubes OS incluye plantillas para **Whonix-Gateway** y **Whonix-Workstation**.

✔️ Así puedes navegar por TOR con aislamiento.

✅ Flujo:

```
Whonix-Workstation → Whonix-Gateway → TOR → Internet
```

✔️ Workstation no ve tu IP → Gateway maneja TOR.

✔️ Gateway no tiene tus datos → Solo enruta tráfico.

---

### ✅ RESUMEN SÚPER CORTO

🌟 **Qubes OS = Sistema operativo ultra seguro.**

✔️ Divide todo en qubes aislados.

✔️ Cada tarea → su propio entorno.

✔️ Incluso si te hackean → Solo afecta un qube.

✔️ Incluye soporte para Whonix (TOR).

---

✅ **VENTAJAS:**

- Compartimentación.
- Aislamiento de malware.
- Control total de permisos.
- Compatible con TOR / Whonix.
- Qubes desechables para contenido peligroso.

---

✅ **INSTALACIÓN RESUMIDA:**

✔️ Descargar ISO desde el sitio oficial.

✔️ Crear USB booteable con Etcher o Rufus.

✔️ Bootear desde USB.

✔️ Instalar en disco duro.

✔️ Configurar qubes iniciales.

✔️ ¡Listo para usar!

---

[🔼](#índice)

---

## **130. Instalación de Qubes OS**

### ✅ **¿Qué es Qubes OS? (breve recordatorio)**

- Es un sistema operativo **muy seguro**.
- Divide tu computadora en “qubes” (pequeñas máquinas virtuales) aisladas.
- Si algo se infecta, **no puede dañar el resto del sistema**.

✅ Ejemplo:

> Un qube para navegar por internet sospechoso.
> Otro qube para tu banca.
> No pueden hablar entre sí.

---

### ✅ **Requisitos antes de instalar**

✔️ Procesador compatible con virtualización (Intel VT-x / AMD-V).

✔️ 8 GB de RAM mínimo (16 GB recomendado).

✔️ Al menos 40 GB de espacio libre en disco.

✔️ UEFI (casi todas las PCs modernas tienen).

✔️ Un USB de **mínimo 16 GB**.

✅ ❗ Qubes OS reemplaza tu sistema actual si eliges todo el disco → **haz backup de tus datos**.

---

### ✅ **PASO A PASO**

---

#### ⭐ PASO 1️⃣: Descargar Qubes OS

✅ Ve al sitio oficial:

```
https://www.qubes-os.org/downloads/
```

✔️ Descarga la **ISO estable más reciente**.

✔️ Verifica la firma (opcional, pero recomendado para seguridad avanzada).

✅ Tamaño aproximado: \~5 GB.

---

#### ✅ Ejemplo fácil

✔️ Botón "Download".

✔️ Archivo → `Qubes-R4.2-x86_64.iso` (el nombre puede variar según la versión).

---

#### ⭐ PASO 2️⃣: Crear un USB booteable

El objetivo es **grabar la ISO en un USB** para arrancar la instalación.

✅ Herramientas recomendadas:

- **balenaEtcher** (Windows / Linux / macOS).
- **Rufus** (Windows).

---

##### 📌 Opción A: balenaEtcher (la más fácil)

✅ Descarga:

```
https://www.balena.io/etcher/
```

✅ Pasos:

1️⃣ Abre Etcher.

2️⃣ Clic en **Flash from file** → selecciona tu archivo `.iso` de Qubes.

3️⃣ Inserta el USB → Etcher lo detecta.

4️⃣ Clic en **Flash!**.

✅ Etcher se encarga de todo → fácil y seguro.

---

##### 📌 Opción B: Rufus (Windows)

✅ Descarga:

```
https://rufus.ie/
```

✅ Pasos:

1️⃣ Abre Rufus.

2️⃣ Selecciona tu USB.

3️⃣ En **Boot selection** → elige la ISO de Qubes.

4️⃣ Esquema de partición → GPT (para UEFI).

5️⃣ Sistema de destino → UEFI.

6️⃣ Clic en **Start**.

✅ Rufus crea el USB booteable.

---

#### ⭐ PASO 3️⃣: Arrancar desde el USB

✔️ Inserta el USB en la computadora.

✔️ Apágala y enciéndela.

✔️ Entra al **menú de arranque** (Boot Menu).

✅ Clave típica según marca:

- Dell → F12
- HP → ESC o F9
- Lenovo → F12
- Asus → ESC o F8

---

✅ En el menú → elige **USB**.

---

✅ Resultado:
Verás la **pantalla de arranque de Qubes OS**.

---

#### ⭐ PASO 4️⃣: Comenzar la instalación

✔️ En el menú → elige:

```
Install Qubes OS
```

✅ Se carga el **instalador gráfico** (muy parecido a Fedora/Red Hat).

---

✅ Pasos:

✔️ 1️⃣ Selecciona idioma (Español o Inglés).

✔️ 2️⃣ Zona horaria.

✔️ 3️⃣ Teclado.

✔️ 4️⃣ Contraseña de administrador (root).

✅ Anótala → la necesitarás para todo.

---

#### ⭐ PASO 5️⃣: Configurar el disco

Aquí tienes 2 opciones:

✅ **A. Usar todo el disco (más fácil)**

- Borra TODO en el disco duro.
- Qubes se instala solo.

✅ **B. Personalizado (para avanzados)**

- Puedes elegir particiones manualmente.
- Útil si quieres dual-boot (no recomendado para novatos).

---

✅ Consejo para principiantes:

✔️ Elige **Usar todo el disco**.

✔️ Marca **Encriptar mi disco** → escribe una **contraseña fuerte**.

✅ Ejemplo fácil de contraseña:

```
FuerteYUnica2025!
```

---

#### ⭐ PASO 6️⃣: Confirmar e instalar

✔️ Revisa todo.

✔️ Haz clic en **Comenzar instalación**.

✔️ Espera (15–60 min).

✅ Al finalizar → haz clic en **Reiniciar**.

✅ Quita el USB antes de arrancar de nuevo.

---

#### ⭐ PASO 7️⃣: Primer arranque

✅ Verás la pantalla de **Qubes OS**.

✅ Ingresa la **contraseña de cifrado del disco**.

✅ Ingresa la **contraseña de usuario (root)**.

---

✅ Aparecerá el **asistente de configuración inicial**.

---

✔️ Selecciona:

✅ Crear qubes recomendados → **SÍ** (opción fácil).

✅ Configurar qubes de red y actualizaciones.

✅ (Opcional) Activar Whonix → para navegar por TOR.

✅ Haz clic en **Finalizar**.

---

✅ ¡Qubes OS estará listo para usar!

---

---

### ✅ **Cómo se usa Qubes OS (explicado fácil)**

✅ Escritorio = similar a Linux.

✅ Verás **menús con colores**:

- Azul, Verde, Amarillo, Rojo → Cada color = un qube.

---

✅ Ejemplo de uso:

✔️ Navegar en internet → Abre **personal qube** (azul).

✔️ Leer email → Abre **work qube** (verde).

✔️ Abrir archivo sospechoso → Botón derecho → **Abrir en qube desechable**.

✔️ Usar TOR → Abre **Whonix qube**.

---

✅ Cada qube = mini máquina virtual → completamente aislada.

---

---

### ✅ **Ventajas prácticas**

✅ Si malware entra en **internet-qube**:

```
NO puede infectar work-qube.
```

✅ Si abres un PDF sospechoso:

```
Se destruye al cerrar qube desechable.
```

✅ Si usas TOR:

```
Whonix qubes → todo el tráfico va por TOR automáticamente.
```

---

### ✅ **Resumen ultra corto**

✔️ Qubes OS = Sistema operativo centrado en seguridad.

✔️ Divide tu PC en compartimentos (qubes).

✔️ Cada qube → aislado → protege tus datos.

✔️ Compatible con TOR vía Whonix.

---

✅ **Pasos de instalación (en breve):**

1️⃣ Descargar ISO de Qubes.

2️⃣ Crear USB booteable (Etcher / Rufus).

3️⃣ Arrancar desde USB.

4️⃣ Seguir el instalador gráfico.

5️⃣ Configurar disco y contraseña.

6️⃣ Esperar instalación → reiniciar.

7️⃣ Configurar qubes iniciales.

8️⃣ ¡Listo!

---

### ✅ **Consejos finales para principiantes**

✔️ Usa **“crear qubes por defecto”** → más fácil.

✔️ No mezcles tareas en el mismo qube → más seguro.

✔️ Actualiza frecuentemente tus templates.

✔️ Aprende a usar **qubes desechables** → muy útiles.

✔️ Activa Whonix si quieres TOR → fácil y seguro.

---

✅ **IMPORTANTE:**

Qubes OS reemplaza el sistema actual si eliges "usar todo el disco". **Haz backup antes**.

---

[🔼](#índice)

---

## **131. Navegación segura en Qubes OS**

### ✅ ¿QUÉ ES “NAVEGACIÓN SEGURA” EN QUBES OS?

Qubes OS está diseñado para **compartimentar** todas tus tareas.

✅ Cada actividad se hace en un “qube” separado.

✅ Si algo se infecta, **no puede afectar otros qubes**.

✔️ Navegar seguro = usar el navegador **en un qube aislado**, para evitar que malware o rastreadores te comprometan.

---

#### ⭐ Analogía MUY sencilla

Imagina tu PC como un edificio de oficinas:

✅ Cada **qube** es una **habitación cerrada**.

✅ Un ladrón (malware) en una habitación **no puede entrar a otras**.

➡️ Así, aunque tu navegador se infecte → tus datos sensibles en otro qube están **seguros**.

---

### ✅ EJEMPLO PRÁCTICO DE USO

✅ Organiza tus qubes así:

- **personal** → para redes sociales y cuentas personales.
- **work** → para trabajo.
- **shopping** → para banca/compras.
- **untrusted** → para navegar en sitios peligrosos o desconocidos.
- **whonix** → para TOR / .onion / navegación anónima.

---

✅ Ejemplo de flujo:

✔️ Necesitas revisar Facebook → usas **personal qube**.

✔️ Comprar en tu banco → usas **shopping qube**.

✔️ Buscar cosas raras → usas **untrusted qube**.

✔️ Acceder a sitios .onion → usas **whonix qube**.

✅ Resultado:

❌ Si el malware infecta **untrusted**, **NO** puede acceder a tu banco.

---

### ✅ CONFIGURACIÓN BÁSICA EN QUBES

Cuando instalas Qubes OS, puedes:

✅ Crear qubes por defecto:

- **personal**
- **work**
- **untrusted**
- **vault** (sin red para contraseñas)
- **whonix-ws** (para TOR)

✅ ¡Recomendado para principiantes!

---

✅ Puedes crear **más qubes personalizados**:

✔️ Menú → Qubes Manager → Create Qube.

✔️ Dale un nombre → ejemplo: **shopping**.

✔️ Asigna color.

✔️ Elige su plantilla (Fedora, Debian, Whonix, etc.).

✔️ Configura si tiene red → por ejemplo, solo a través de **sys-whonix** para TOR.

---

### ✅ ¿CÓMO SE “INSTALA” LA NAVEGACIÓN SEGURA?

En realidad, **Qubes OS ya incluye** todo para navegación segura.
✅ Solo hay que organizarlo y usarlo bien.

---

✔️ **A. Navegador normal (no TOR):**

✅ Usa qubes diferentes según el propósito.

Ejemplo:

- Navegar en bancos → shopping qube.
- Redes sociales → personal qube.
- Web peligrosa → untrusted qube.

---

✔️ **B. Navegador con TOR:**

✅ Usa los qubes de Whonix.

✔️ Qubes ya trae:

- **sys-whonix** → el Gateway que conecta a TOR.
- **whonix-ws** → tu workstation anónima.

✅ Allí se abre **Tor Browser** automáticamente.

---

### ✅ USAR TOR / WHONIX PASO A PASO

✅ Viene preconfigurado en Qubes OS (si marcaste “Activar Whonix” en la instalación).

---

✔️ **PASO 1:** Abre Qube Manager.

✔️ Verifica que existan:

- **sys-whonix** (gateway a TOR).
- **whonix-ws** (workstation).

---

✔️ **PASO 2:** Abre **whonix-ws**.

✅ Menú → Whonix → **Tor Browser**.

---

✅ Resultado:

✔️ Todo el tráfico pasa por:

```
whonix-ws → sys-whonix → TOR → Internet
```

✔️ Tu IP real **nunca sale** → la red TOR la oculta.

---

✅ **EJEMPLO REAL:**

✅ Necesitas entrar a un sitio .onion:

1️⃣ Abre **whonix-ws**.

2️⃣ Abre **Tor Browser**.

3️⃣ Escribe el .onion:

```
protonirockerxow.onion
```

✅ Tu IP real está protegida.

---

### ✅ USAR QUBES DESECHABLES PARA MÁS SEGURIDAD

✅ Qubes OS permite abrir **Disposable Qubes**.

---

✔️ Idea sencilla:

✅ Se crea → usas → se destruye.

---

✅ Ejemplo:

📌 Descargar un PDF sospechoso:

1️⃣ Botón derecho → **Open in Disposable Qube**.

2️⃣ El PDF se abre en un qube temporal.

3️⃣ Al cerrarlo → todos los cambios desaparecen.

---

✅ Resultado:

✔️ Si el PDF tenía malware → NO infecta tu sistema real.

---

### ✅ CÓMO SE “INSTALA” TOR EN QUBES

✅ No necesitas instalarlo manualmente → Qubes OS ya trae Whonix configurado.

✔️ Al instalar Qubes OS y elegir “Activar Whonix”, se crean:

✅ **sys-whonix**

✅ **whonix-ws**

---

✔️ Si no lo hiciste al principio:

✅ Ve a Qubes Manager → **Create Qube** → elige plantilla Whonix → ¡listo!

✅ También puedes actualizar las plantillas Whonix:

```bash
sudo apt update
sudo apt upgrade
```

en **whonix-ws** o **whonix-gw**.

---

### ✅ EJEMPLO DE USO DIARIO SÚPER CLARO

✅ Tu día en Qubes OS podría ser así:

⭐ Banco:

✔️ Abres **shopping qube**.

✔️ Navegador → web del banco.

⭐ Email trabajo:

✔️ Abres **work qube**.

✔️ Thunderbird o navegador → correo del trabajo.

⭐ Navegar en sitios desconocidos:

✔️ Abres **untrusted qube**.

✔️ Firefox → sitios raros.

⭐ Navegación anónima:

✔️ Abres **whonix-ws**.

✔️ Tor Browser → .onion o web normal anónima.

⭐ Archivo sospechoso:

✔️ Botón derecho → **Open in Disposable Qube**.

✅ Resultado:

✅ TODO separado → más seguro.

---

### ✅ CONSEJOS AVANZADOS PERO FÁCILES

✅ Usa colores para identificar qubes (azul, verde, rojo).

✅ Limita la red:

- Qubes de contraseñas → **sin red**.
- Qubes de navegación → solo la red necesaria.
- TOR → siempre via **sys-whonix**.

✅ Usa Disposable Qubes para contenido peligroso.

✅ Actualiza plantillas con frecuencia.

✅ No mezcles tareas → mantén datos sensibles en qubes separados.

---

### ✅ RESUMEN ULTRA CORTO

✔️ Qubes OS = compartimentación.

✔️ Cada qube → su propio mundo.

✔️ Si algo se infecta → no puede dañar otros qubes.

✔️ Navegación segura = usar qubes separados.

✔️ TOR = usar qubes Whonix (preinstalados en Qubes OS).

✔️ Archivos sospechosos → abrir en Disposable Qubes.

---

### ✅ PASO A PASO FINAL (BREVE)

✔️ 1️⃣ Instalar Qubes OS → incluye Whonix.

✔️ 2️⃣ Abrir **Qubes Manager**.

✔️ 3️⃣ Verificar/crear qubes:

- personal
- work
- shopping
- untrusted
- whonix-ws
- Disposable Qubes

✔️ 4️⃣ Usar cada qube para su propósito.

✔️ 5️⃣ Navegar con Tor → abrir **Tor Browser** en **whonix-ws**.

✔️ 6️⃣ Usar **Disposable Qubes** para abrir archivos o webs sospechosas.

---

✅ Resultado:

🌟 Tu navegación y tu sistema están súper protegidos.

---

[🔼](#índice)

---

## **132. Gestión segura de ficheros en Qubes OS**

### ✅ ¿QUÉ ES “GESTIÓN SEGURA DE FICHEROS” EN QUBES OS?

**Idea clave súper sencilla:**

✅ Qubes OS divide tu sistema en compartimentos (qubes).

✅ Cada qube es **aislado**, como una caja cerrada.

✅ Los archivos **no pueden moverse libremente** entre qubes.

✔️ Esto evita que malware o datos sensibles se filtren entre entornos.

---

✅ **Gestión segura de ficheros** =

✔️ Elegir **qué mover, de dónde y hacia dónde**.

✔️ Revisar **qué qube confías**.

✔️ Usar **herramientas de Qubes** para copiar de forma controlada.

---

### ✅ ANALOGÍA MUY FÁCIL

Imagina que tienes **varios cuartos cerrados con llave**:

🟦 Cuarto azul → trabajo

🟩 Cuarto verde → personal

🟥 Cuarto rojo → navegación peligrosa

🟧 Cuarto naranja → correo

✅ Para pasar un paquete (archivo) de un cuarto a otro:

✔️ Necesitas abrir la puerta **tú mismo**.

✔️ Decidir si vale la pena **arriesgar**.

---

✅ Qubes OS te obliga a **pensar cada movimiento**.

❌ No hay “copiar y pegar” directo como en Windows.

---

### ✅ CÓMO FUNCIONA EN QUBES (EXPLICADO FÁCIL)

✅ En Qubes OS:

✔️ Cada qube tiene su propio **almacenamiento aislado**.

✔️ Para mover un archivo → usas herramientas especiales:

✅ _qvm-copy_

✅ _qvm-move_

✅ _qvm-open-in-dvm_

✅ Así evitas **errores o fugas accidentales**.

---

#### ⭐ Ejemplo práctico sencillo:

✅ Descargas un archivo en **untrusted qube** (para navegación peligrosa).

✅ Antes de abrirlo en tu qube personal:

✔️ Lo revisas.

✔️ Quizá lo abres primero en **Disposable Qube** para chequear si tiene malware.

✔️ Si está limpio, lo copias a **personal qube**.

✅ Resultado:

❌ Malware no se propaga a tu qube personal.

---

### ✅ HERRAMIENTAS PROPIAS DE QUBES

✔️ **qvm-copy** → Copiar un archivo de un qube a otro.

✔️ **qvm-move** → Mover (elimina del origen).

✔️ **qvm-open-in-dvm** → Abrir en qube desechable (DisposableVM).

---

✅ Estas herramientas:

✔️ Aparecen en el **menú contextual** (botón derecho).

✔️ Son fáciles de usar, sin terminal.

✔️ Garantizan que **NO haya conexión directa** entre qubes.

---

### ✅ PASO A PASO – COPIAR ARCHIVOS ENTRE QUBES

✅ **Ejemplo real:**

Quieres copiar un archivo desde **untrusted** → a **work**.

---

✔️ **PASO 1:** Abre el administrador de archivos en **untrusted qube**.

✔️ **PASO 2:** Botón derecho sobre el archivo.

✔️ Verás opciones:

```
Copy to Another Qube
Move to Another Qube
```

✔️ **PASO 3:** Elige **Copy to Another Qube**.

✔️ **PASO 4:** Aparece una lista de tus qubes.

✔️ **PASO 5:** Selecciona **work**.

✔️ **PASO 6:** Haz clic en **OK**.

---

✅ Resultado:

✔️ El archivo se copia **aisladamente**.

✔️ Untrusted → NO ve directamente el sistema de archivos de **work**.

✔️ Qubes OS gestiona la transferencia **de forma controlada**.

---

✅ **Diferencia entre Copy y Move:**

- **Copy to Another Qube** → Copia el archivo y lo deja también en el origen.
- **Move to Another Qube** → Copia y elimina del origen.

---

### ✅ USAR DISPOSABLE QUBES PARA ARCHIVOS SOSPECHOSOS

✅ Qubes OS permite abrir archivos **en qubes desechables**.

✔️ Disposable Qube = Sesión temporal → se destruye al cerrar.

✔️ Ideal para abrir **PDFs, imágenes o documentos sospechosos**.

---

✅ **PASO A PASO:**

✔️ Botón derecho en el archivo →

```
Open in DisposableVM
```

✔️ Qubes lanza una Disposable Qube.

✔️ Abre el archivo ahí.

✔️ Cuando cierras → TODO se borra.

---

✅ Resultado:

✔️ Si tenía malware → NO infecta tu qube principal.

✔️ Nada persiste → máxima seguridad.

---

#### ⭐ Ejemplo práctico:

✅ Descargas un archivo en **untrusted**.

✅ Antes de abrirlo →

✔️ Lo abres en DisposableVM.

✔️ Si se ve bien y seguro → Puedes copiarlo a otro qube confiable.

---

### ✅ CÓMO COPIAR DESDE UN DISPOSABLE QUBE

✔️ Generalmente, DisposableVMs no guardan datos.

✔️ Pero puedes **guardar archivos** antes de cerrar:

✅ Abre terminal en el DisposableVM:

```
qvm-copy-to-vm work /home/user/Documents/archivo.txt
```

✅ El archivo se copiará al qube “work” antes de que el DisposableVM se destruya.

---

### ✅ COPIAR DESDE UN QUBE SIN INTERFAZ GRÁFICA (opcional avanzado)

✔️ En terminal:

✅ Para copiar:

```
qvm-copy-to-vm destino /ruta/del/archivo
```

✅ Para mover:

```
qvm-move-to-vm destino /ruta/del/archivo
```

✅ Ejemplo:

```
qvm-copy-to-vm personal /home/user/descargas/archivo.pdf
```

---

### ✅ TIPOS DE FLUJO SEGURO (EJEMPLO COMPLETO)

✅ Descargar algo:

✔️ Siempre usa **untrusted qube** para navegar.

✔️ Descargas allí.

✅ Revisar:

✔️ Lo abres en **DisposableVM** para chequear si es peligroso.

✅ Limpiar y copiar:

✔️ Si está limpio → usa **Copy to Another Qube** → **personal** o **work**.

✅ Resultado:

✔️ **Malware no puede saltar** entre qubes.

---

### ✅ BUENAS PRÁCTICAS

✅ Usa nombres claros para tus qubes:

- personal
- work
- shopping
- untrusted
- vault (sin red)

✅ Usa colores para diferenciarlos.

✅ Nunca abras archivos directamente en qubes sensibles.

✅ Usa Disposable Qubes para archivos de orígenes desconocidos.

✅ Usa qvm-copy/qvm-move → nunca “drag and drop”.

---

### ✅ RESUMEN ULTRA CORTO

⭐ Qubes OS **aísla** qubes.

⭐ Para mover archivos → herramientas seguras:

✔️ qvm-copy

✔️ qvm-move

✔️ qvm-open-in-dvm

⭐ Nada se comparte automáticamente.

⭐ Tú decides **qué, a dónde, y por qué**.

⭐ Usa Disposable Qubes para máxima seguridad.

---

### ✅ MINI GUÍA DE INSTALACIÓN Y CONFIGURACIÓN (RESUMIDA)

✅ Si ya instalaste Qubes OS:

✔️ Ya tienes **qvm-copy**, **qvm-move** y **DisposableVM** listos.

✔️ Solo necesitas:

✅ Abrir Qubes Manager.

✅ Ver tus qubes → Personal, Work, Untrusted, Disposable.

✅ Usarlos para separar actividades.

✅ Copiar/mover archivos de forma **deliberada y segura**.

---

### ✅ EJEMPLO DE TRABAJO DIARIO

✅ 1️⃣ Navegar en **untrusted** → descargar PDF.

✅ 2️⃣ Botón derecho → **Open in DisposableVM**.

✅ 3️⃣ Si es seguro → botón derecho → **Copy to Another Qube** → **work**.

✅ 4️⃣ Trabajar en **work** → abrir el PDF ya revisado.

---

✅ Resultado:

✔️ Aislamiento total.

✔️ Reducción de riesgo.

✔️ Malware contenido.

---

[🔼](#índice)

---

## **133. Disposable Qube**

### ✅ ¿QUÉ ES UN DISPOSABLE QUBE? (Explicación sencilla)

Un **Disposable Qube** (también llamado **DVM**) es un **qube temporal que se destruye automáticamente** cuando lo cierras.

> 🧼 Ideal para abrir archivos sospechosos, visitar sitios web poco confiables o hacer tareas rápidas sin dejar rastro.

---

#### 🎯 Ventajas principales:

- **Seguridad:** todo lo que abras en él desaparece al cerrarlo.
- **Aislamiento:** no afecta tu sistema principal ni tus otros qubes.
- **Práctico:** puedes lanzar uno en segundos, listo para usar.

---

#### 🧠 Analogía fácil:

🔐 Imagina que quieres abrir un paquete sospechoso.
En lugar de abrirlo en tu casa (qube principal),

👉 lo llevas a una **habitación desechable** de un solo uso.

Si explota 💣... no pasa nada, porque se destruye cuando sales de ahí.

---

### ✅ ¿CUÁNDO USAR UN DISPOSABLE QUBE?

| Tarea                                        | ¿Usar Disposable Qube?              |
| -------------------------------------------- | ----------------------------------- |
| Abrir archivos adjuntos desconocidos         | ✅ Sí                               |
| Navegar en sitios dudosos                    | ✅ Sí                               |
| Acceder a tu correo electrónico              | ❌ No (mejor usar un qube dedicado) |
| Leer documentos PDF de fuentes no confiables | ✅ Sí                               |
| Instalar programas                           | ❌ No (se borra al cerrar)          |
| Revisar archivos comprimidos (zip/rar)       | ✅ Sí                               |

---

### ✅ CÓMO FUNCIONA UN DISPOSABLE QUBE

Un Disposable Qube **se crea a partir de una plantilla** (como Fedora o Debian),
pero **no guarda cambios**.

> 🗂️ Puedes usar archivos desde otros qubes dentro de él, pero si modificas algo, **se pierde al cerrarlo**.

---

### ✅ EJEMPLO REAL Y FÁCIL

#### 🔹 Situación:

Te llega un archivo PDF por correo en tu qube de trabajo (**work-qube**)
y no confías mucho en él.

---

#### 🔹 Solución con Disposable Qube:

1. Botón derecho sobre el archivo.
2. Elige:

   ```
   Open in DisposableVM
   ```

3. Se abre un entorno limpio con el archivo.
4. Lo lees. Si no pasa nada raro, bien.
5. Al cerrar la ventana → **todo se borra** automáticamente.

✔️ No queda ni rastro del archivo.

✔️ Si era malware, no infectó tu sistema.

---

### ✅ ¿VIENEN INSTALADOS POR DEFECTO?

**¡Sí!**

Al instalar Qubes OS y activar las configuraciones recomendadas, ya tienes:

- `disp1234` → el Disposable Qube por defecto.
- Basado en plantillas como **fedora-XX-dvm** o **debian-XX-dvm**.

---

### ✅ ¿CÓMO VERLOS O USARLOS?

#### 🔹 Opción 1: Desde el menú

🖱️ Haz clic en el menú de Qubes (arriba a la izquierda).

📁 Busca:

```
Disposable: fedora-XX-dvm: Files
Disposable: fedora-XX-dvm: Firefox
```

---

#### 🔹 Opción 2: Desde otro qube

✅ Botón derecho sobre un archivo →

```
Open in DisposableVM
```

✅ O abrir terminal y escribir:

```bash
qvm-open-in-dvm archivo.pdf
```

---

### ✅ ¿CÓMO SE CREA UNO PERSONALIZADO?

Puedes **crear tu propio Disposable Qube personalizado** si lo deseas.

---

#### 🔹 PASO A PASO:

1. Ve al **Qube Manager**.

2. Haz clic en **Create Qube**.

3. Rellena los datos:

   - **Name:** por ejemplo, `my-dispo-fedora`.
   - **Color:** el que gustes.
   - **Use as template for Disposable VMs:** ✅ actívalo.
   - **Template:** `fedora-XX` o `debian-XX`.

4. Espera unos segundos.

---

#### 🔹 Resultado:

Has creado una plantilla especial para tus propios DisposableVMs.

---

### ✅ USAR TU PROPIO DISPOSABLE QUBE

1. En el menú de Qubes, selecciona:

   ```
   Disposable: my-dispo-fedora: Firefox
   ```

2. Puedes configurar qué apps aparecen en ese menú editando la plantilla.

---

### ✅ ¿CÓMO CAMBIAR LA PLANTILLA POR DEFECTO DE LOS DISPOSABLE?

#### 🔹 Por terminal:

```bash
qvm-prefs --set default_dispvm <nombre-del-qube>
```

✅ Ejemplo:

```bash
qvm-prefs --set default_dispvm my-dispo-fedora
```

Ahora, cuando hagas "Open in DisposableVM", usará esa plantilla.

---

### ✅ ¿PUEDO GUARDAR UN ARCHIVO DESDE UN DISPOSABLE QUBE?

Sí, pero debes **copiarlo a otro qube antes de cerrarlo**.
Porque cuando lo cierras, **todo desaparece**.

---

#### 🔹 Paso a paso:

1. Terminal en DisposableVM:

```bash
qvm-copy-to-vm work archivo.txt
```

✅ Así lo envías al qube **work** antes de cerrar.

---

### ✅ RESUMEN ULTRA RÁPIDO

| Característica      | ¿Cómo funciona?                        |
| ------------------- | -------------------------------------- |
| Temporal            | Se borra todo al cerrarse              |
| Basado en plantilla | Usa Fedora o Debian como base          |
| Aislamiento total   | No accede a tus otros qubes            |
| Archivos peligrosos | Ábrelos aquí para máxima seguridad     |
| Personalizable      | Puedes crear tus propios DisposableVMs |

---

### ✅ TIPS DE USO

✅ Usa siempre qubes desechables para:

- Archivos adjuntos de correos.
- Sitios web desconocidos.
- Documentos de pendrives.
- PDFs, DOCs, etc. de origen incierto.

✅ No guardes datos importantes aquí.

✅ Si quieres conservar algo → **cópialo antes de cerrar**.

---

[🔼](#índice)

---

## **134. Qubes Manager y gestión de aplicaciones**

### ✅ ¿QUÉ ES QUBES MANAGER?

**Qubes Manager** es la **herramienta gráfica principal de Qubes OS** para **ver y controlar todos tus qubes**.

✅ Piensa en él como un **panel de control central**.

✅ Muestra todos tus qubes activos e inactivos en una sola ventana.

✅ Te permite arrancar, detener, pausar, copiar, borrar, crear y gestionar qubes.

---

✅ **Analogía fácil:**

> Es como el “Administrador de tareas” o “Control Center” de Qubes, pero específico para tus qubes aislados.

---

### ✅ PARA QUÉ SIRVE (IDEA SENCILLA)

Con Qubes Manager puedes:

✔️ Ver todos tus qubes en un solo lugar.

✔️ Saber cuáles están corriendo.

✔️ Ver consumo de RAM y CPU.

✔️ Abrir terminal o aplicaciones en un qube específico.

✔️ Copiar o mover archivos entre qubes.

✔️ Parar o reiniciar qubes.

✔️ Editar su configuración (RAM, plantillas, redes).

✔️ Crear qubes nuevos.

✔️ Eliminar qubes que no necesitas.

✅ Es la **manera más fácil y gráfica de gestionar Qubes OS**.

---

### ✅ ¿CÓMO SE INSTALA?

✅ **¡Muy fácil!**

**Qubes Manager ya viene instalado por defecto en Qubes OS**.

✅ No necesitas instalar nada extra.

---

✅ Si por alguna razón se desinstaló o quieres reinstalarlo:

#### En terminal (con privilegios):

✅ Para Fedora template:

```bash
sudo dnf install qubes-manager
```

✅ Para Debian template:

```bash
sudo apt install qubes-manager
```

---

✅ Después de instalarlo, estará en tu menú:

```
Q → Qubes Tools → Qubes Manager
```

---

### ✅ ¿CÓMO SE ABRE QUBES MANAGER?

✅ Desde el menú de aplicaciones:

🖱️ Ve a la esquina superior izquierda → **Q** → **Qubes Tools** → **Qubes Manager**.

✅ También puedes buscarlo escribiendo “Qubes Manager” en el buscador de aplicaciones.

---

### ✅ VISTA PRINCIPAL DE QUBES MANAGER

Cuando abres Qubes Manager verás **una lista de todos tus qubes**.

✅ Cada fila = un qube.

✅ Columnas típicas:

| Qube Name    | State   | Template  | NetVM        | RAM usage | Label  |
| ------------ | ------- | --------- | ------------ | --------- | ------ |
| sys-net      | Running | fedora-XX | none         | 200 MB    | Red    |
| sys-firewall | Running | fedora-XX | sys-net      | 150 MB    | Orange |
| personal     | Halted  | fedora-XX | sys-firewall | 0 MB      | Blue   |
| vault        | Halted  | fedora-XX | none         | 0 MB      | Gray   |

✅ Puedes ver:

- Estado: Running / Halted.
- Plantilla: Fedora, Debian, Whonix.
- NetVM: cómo se conecta a Internet.
- RAM en uso.
- Color (label).

---

### ✅ ACCIONES BÁSICAS EN QUBES MANAGER

🖱️ **Clic derecho** sobre cualquier qube → aparece un menú con opciones:

✔️ Start

✔️ Shutdown

✔️ Pause

✔️ Resume

✔️ Restart

✔️ Open Terminal

✔️ Create Shortcut

✔️ Copy to Another Qube

✔️ Move to Another Qube

✔️ Settings

✅ Súper fácil y accesible.

---

### ✅ EJEMPLO PRÁCTICO: ARRANCAR UN QUBE

✅ Imagina que quieres iniciar **personal**:

✔️ Abre Qubes Manager.

✔️ Busca “personal”.

✔️ Estado = Halted.

✔️ Botón derecho → **Start**.

✅ Resultado:

```
El qube arranca.
```

Ahora puedes abrir apps dentro de “personal”.

---

### ✅ EJEMPLO PRÁCTICO: ABRIR UNA TERMINAL

✅ Para abrir terminal en “work”:

✔️ Abre Qubes Manager.

✔️ Botón derecho en “work” → **Open Terminal**.

✅ Resultado:

```
Se abre una terminal aislada en el qube work.
```

---

### ✅ EJEMPLO PRÁCTICO: COPIAR ARCHIVO ENTRE QUBES

✅ Desde Qubes Manager:

✔️ Botón derecho en qube origen (ejemplo: untrusted).

✔️ Elegir **Copy to Another Qube**.

✔️ Selecciona qube destino (ejemplo: work).

✔️ Confirmar.

✅ Qubes OS copia el archivo de forma segura y aislada.

---

### ✅ EDITAR CONFIGURACIÓN DE UN QUBE

✅ Desde Qubes Manager:

✔️ Botón derecho sobre el qube → **Settings**.

---

#### En la ventana de configuración puedes:

✔️ Cambiar el nombre.

✔️ Cambiar color/label.

✔️ Cambiar la plantilla (Debian, Fedora, Whonix).

✔️ Cambiar la red (NetVM: sys-firewall, sys-whonix, etc.).

✔️ Ajustar memoria RAM.

✔️ Definir si es Disposable Template.

✔️ Configurar almacenamiento adicional.

✅ Resultado:

```
Tu qube queda personalizado como tú quieras.
```

---

### ✅ CREAR UN NUEVO QUBE (PASO A PASO)

✅ Desde Qubes Manager:

✔️ Menú → **Qube** → **Create New Qube**.

---

#### Pasos:

1️⃣ Nombre: por ejemplo, **shopping**.

2️⃣ Color: por ejemplo, Verde.

3️⃣ Template: Fedora / Debian / Whonix.

4️⃣ NetVM: sys-firewall, sys-whonix, etc.

5️⃣ Marcar si quieres que sea Disposable Template.

✅ Haz clic en **OK**.

✅ Resultado:

```
Se crea tu nuevo qube.
```

---

### ✅ GESTIÓN DE APLICACIONES EN QUBES OS

✅ Cada qube tiene su propio **menú de aplicaciones**.

---

#### 🔹 Añadir o quitar aplicaciones de un qube:

✔️ Abre **Qubes Manager**.

✔️ Botón derecho → **Settings** en el qube.

✔️ Pestaña **Applications**.

✅ Verás:

| Available                      | Selected                             |
| ------------------------------ | ------------------------------------ |
| Todas las apps en la plantilla | Las que aparecen en el menú del qube |

✅ Puedes:

✔️ Seleccionar apps para añadir.

✔️ Quitar apps que no quieres que aparezcan.

---

✅ Ejemplo:

✔️ Qube “personal” → quieres añadir Firefox.

✔️ Lo seleccionas en Available → clic en **>** → aparece en Selected.

✔️ Aplicas cambios.

✅ Resultado:

```
Firefox aparece en el menú de apps del qube personal.
```

---

---

### ✅ CONSEJOS Y BUENAS PRÁCTICAS

✅ Usa colores para identificar qubes fácilmente.

✅ Nombra qubes según su función (work, personal, banking).

✅ Limita las conexiones de red (NetVM) a lo mínimo necesario.

✅ Usa DisposableVMs para abrir archivos peligrosos.

✅ Actualiza plantillas regularmente.

✅ Desactiva qubes que no uses para ahorrar RAM.

---

### ✅ RESUMEN MUY CORTO

✔️ **Qubes Manager** = panel central para controlar todos tus qubes.

✔️ Ya viene instalado por defecto.

✔️ Puedes: arrancar, detener, pausar, borrar, crear, copiar, mover qubes.

✔️ También sirve para **gestionar aplicaciones** y sus accesos directos.

✔️ Muy fácil de usar con clic derecho.

---

### ✅ MINI GUÍA PASO A PASO FINAL

✅ **Abrir Qubes Manager:**

Menú Q → Qubes Tools → Qubes Manager.

✅ **Ver qubes:**

Revisa estado, RAM, NetVM.

✅ **Acciones rápidas:**

Botón derecho → Start, Shutdown, Terminal.

✅ **Configurar apps:**

Botón derecho → Settings → Applications.

✅ **Crear nuevo qube:**

Menú → Qube → Create New Qube.

✅ **Copiar archivos entre qubes:**

Botón derecho → Copy to Another Qube.

---

[🔼](#índice)

---

## **135. Creación de nuevos Qubes**

### ✅ ¿QUÉ ES UN “QUBE”? (Explicación sencilla)

En Qubes OS, **un qube es como una máquina virtual aislada**.

✅ Es tu “cajita” privada para una tarea o propósito.

✅ Todo lo que pasa en ese qube **no afecta a los demás**.

✅ Cada qube tiene su propio sistema de archivos, aplicaciones, configuraciones.

---

✅ **Analogía fácil:**

> Es como tener **varios escritorios separados y cerrados con llave** en tu computadora.

---

### ✅ ¿PARA QUÉ SIRVE CREAR NUEVOS QUBES?

✅ Te ayuda a **aislar tareas** y **organizar tu trabajo**.

✔️ Navegar en sitios peligrosos → qube “untrusted”.

✔️ Banca online → qube “banking”.

✔️ Correo del trabajo → qube “work”.

✔️ Navegar anónimo con Tor → qube “whonix-ws”.

✔️ Guardar contraseñas → qube “vault” (sin red).

✅ Así, si un qube se infecta o se rompe → **no afecta a los demás**.

---

### ✅ TIPOS DE QUBES QUE PUEDES CREAR

✔️ App Qube → normal, para tareas diarias.

✔️ Disposable Template → plantilla para qubes desechables.

✔️ Standalone Qube → copia independiente (no hereda actualizaciones de la plantilla).

✅ La más común → **App Qube**.

---

### ✅ EJEMPLOS TÍPICOS DE QUBES

✅ untrusted → para descargas y navegación peligrosa.

✅ personal → para redes sociales y correo personal.

✅ work → para trabajo.

✅ banking → solo para banca online.

✅ vault → para contraseñas (sin red).

✅ shopping → compras online.

✅ whonix-ws → navegación Tor.

---

### ✅ ¿CÓMO SE CREAN NUEVOS QUBES? (PASO A PASO)

✅ Lo puedes hacer **con interfaz gráfica (Qubes Manager)** o **con terminal**.

---

#### ⭐ A. MÉTODO FÁCIL: QUBES MANAGER (gráfico)

✅ Paso 1️⃣: Abre Qubes Manager.

🖱️ Menú superior → Q → Qubes Tools → **Qubes Manager**.

---

✅ Paso 2️⃣: Clic en el menú superior → **Qube** → **Create New Qube**.

---

✅ Paso 3️⃣: Completar formulario.

✔️ **Name:** Nombre de tu qube (ejemplo: `shopping`).

✔️ **Color Label:** El color (verde, azul, rojo…).

✔️ **Type:** normalmente **AppVM** (qube normal).

✔️ **Template:** Fedora, Debian, Whonix, etc.

- Fedora / Debian → para uso general.
- whonix-ws → para navegación Tor.

  ✔️ **Networking:**

- sys-firewall → para acceso normal a Internet.
- sys-whonix → para TOR.
- none → sin red (seguridad máxima, como vault).

✅ Paso 4️⃣: Haz clic en **OK**.

---

✅ Resultado:

```
¡Tu nuevo qube está listo!
```

Aparecerá en el Qubes Manager con el nombre y color que elegiste.

---

#### ⭐ B. EJEMPLO PRÁCTICO REAL

✅ Quiero crear un qube llamado **banking**:

🖱️ Abro Qubes Manager.

🖱️ Qube → Create New Qube.

✅ Completo así:

✔️ Name → `banking`

✔️ Color → Azul

✔️ Type → AppVM

✔️ Template → fedora-XX

✔️ Networking → sys-firewall (acceso a Internet normal)

✅ Clic en OK.

---

✅ Resultado:

```
banking aparece en Qubes Manager listo para usarse.
```

---

#### ⭐ C. CREAR UN QUBE SIN RED (ejemplo “vault”)

✅ Qube Manager → Create New Qube.

✔️ Name → `vault`

✔️ Color → Gris

✔️ Type → AppVM

✔️ Template → fedora-XX

✔️ Networking → **none**

✅ Resultado:

```
vault no tendrá acceso a ninguna red → súper seguro.
```

---

### ✅ 6️⃣ OPCIONES AVANZADAS AL CREAR

✅ **Networking:**

- sys-firewall → para navegar normalmente.
- sys-whonix → todo el tráfico por TOR.
- none → sin Internet (para datos sensibles).

✅ **Template:**

- Fedora o Debian → uso general.
- Whonix → navegación anónima.

✅ **Disposable Template:**

- Para crear qubes desechables basados en él.

✅ **Storage Pool:**

- Para elegir en qué disco o partición guardar los datos (opcional, para usuarios avanzados).

---

### ✅ MÉTODO ALTERNATIVO: TERMINAL (OPCIONAL)

✅ También puedes crear qubes con comandos.

✔️ Comando básico:

```bash
qvm-create --class AppVM --label green shopping
```

✔️ Cambiar plantilla:

```bash
qvm-prefs shopping template fedora-XX
```

✔️ Configurar red:

```bash
qvm-prefs shopping netvm sys-firewall
```

---

✅ Resultado:

```
Se crea un qube “shopping” con Fedora, color verde y acceso a Internet.
```

---

### ✅ GESTIONAR EL NUEVO QUBE

✅ Una vez creado → puedes:

✔️ Arrancarlo desde Qubes Manager.

✔️ Abrir terminal.

✔️ Abrir aplicaciones.

✔️ Copiar o mover archivos hacia/desde él.

✔️ Editar su configuración (RAM, red, plantilla).

---

### ✅ BUENAS PRÁCTICAS PARA NOMBRAR Y ORGANIZAR

✅ Usa nombres claros y descriptivos:

✔️ work

✔️ personal

✔️ banking

✔️ shopping

✔️ untrusted

✔️ vault

✅ Usa colores para identificar rápidamente:

🟥 Rojo → peligroso (untrusted)

🟦 Azul → personal / banca

🟩 Verde → compras / correo

⬛ Gris → vault (sin red)

✅ Limita la red según el propósito.

---

### ✅ RESUMEN CORTO Y CLARO

⭐ Un qube = un espacio aislado.

⭐ Puedes crear qubes para diferentes tareas → más seguridad.

⭐ Crearlos es fácil desde Qubes Manager.

⭐ Define nombre, color, plantilla, red.

⭐ Puedes hacerlo también por terminal.

⭐ Mantén qubes organizados para mayor seguridad.

---

### ✅ MINI GUÍA ULTRARÁPIDA

✔️ Abre **Qubes Manager**.

✔️ Menú → Qube → **Create New Qube**.

✔️ Ponle un **nombre**.

✔️ Elige un **color**.

✔️ Define **plantilla** (Fedora, Debian, Whonix).

✔️ Define **red** (sys-firewall, sys-whonix, none).

✔️ Haz clic en **OK**.

✔️ ¡Listo! 🎉

---

### ✅ EJEMPLOS LISTOS PARA COPIAR

✔️ Crear “untrusted”:

✅ Qubes Manager → Create New Qube:

- Name → untrusted
- Color → Rojo
- Template → fedora-XX
- Networking → sys-firewall

---

✔️ Crear “vault”:

✅ Qubes Manager → Create New Qube:

- Name → vault
- Color → Gris
- Template → fedora-XX
- Networking → none

---

✔️ Crear “tor-browser” para TOR:

✅ Qubes Manager → Create New Qube:

- Name → tor-browser
- Color → Púrpura
- Template → whonix-ws-XX
- Networking → sys-whonix

---

[🔼](#índice)

---

## **136. Whonix con Qubes OS**

### ✅ ¿QUÉ ES WHONIX?

**Whonix** es un sistema operativo orientado a la privacidad y el anonimato.

✔️ Se basa en Debian.

✔️ Todo el tráfico sale exclusivamente a través de **Tor**.

✔️ Está dividido en dos partes:

- **Whonix-Gateway**: se conecta a la red Tor.
- **Whonix-Workstation**: donde trabajas o navegas, pero solo puede comunicarse con Internet a través del Gateway.

---

✅ **Idea sencilla:**

> Whonix separa la parte que conecta a Tor de la parte donde haces tus actividades.

---

#### 🎯 Ventaja

✅ Aunque un atacante controle la Workstation, **solo ve tráfico Tor**, y no tu IP real.

✅ Todo está diseñado para minimizar fugas de IP.

---

### ✅ ¿QUÉ ES WHONIX EN QUBES OS?

Qubes OS integra **Whonix** de forma especial:

✔️ Usa **plantillas** (templates) para crear qubes basados en Whonix.

✔️ Gestiona aislamiento extremo con el modelo de seguridad de Qubes.

---

En Qubes OS:

✅ **Whonix-Gateway (sys-whonix):**

- Es el qube que conecta a Tor.
- Todos los qubes que uses para Tor se conectan a Internet a través de él.

✅ **Whonix-Workstation (anon-whonix):**

- Es donde navegas o haces tareas anónimas.
- Solo se comunica con Internet pasando por sys-whonix.

---

✅ **Esquema súper fácil:**

```
anon-whonix  →  sys-whonix  →  Tor  →  Internet
```

---

### ✅ ¿PARA QUÉ SIRVE?

✅ Navegar de forma anónima.

✅ Evitar filtraciones de IP real.

✅ Compartimentar tu actividad.

✅ Usar Tor de forma segura y aislada.

---

✅ Ejemplos:

✔️ Usar Tor Browser.

✔️ Leer correos sensibles.

✔️ Acceder a onion services.

✔️ Enviar reportes anónimos.

---

### ✅ EJEMPLO REAL Y FÁCIL DE ENTENDER

✅ Imagínate que quieres entrar a la Dark Web o a un sitio onion:

✔️ Abres **anon-whonix**.

✔️ Todo el tráfico pasa **solo por Tor**.

✔️ Aunque un malware intente salir → no puede evitar sys-whonix → no ve tu IP real.

---

✅ Resultado:

> Tu actividad se oculta tras Tor, con aislamiento fuerte entre componentes.

---

### ✅ ¿VIENE INSTALADO POR DEFECTO EN QUBES OS?

✅ Normalmente **sí**, si marcaste la opción durante la instalación inicial de Qubes.

✅ Aparecen qubes como:

- **sys-whonix** (gateway)
- **anon-whonix** (workstation)
- Plantillas: whonix-gw-XX, whonix-ws-XX

---

### ✅ CÓMO SABER SI YA LO TIENES INSTALADO

✔️ Abre **Qubes Manager**.

✔️ Busca en la lista:

✅ sys-whonix

✅ anon-whonix

✅ whonix-gw-XX (template)

✅ whonix-ws-XX (template)

---

Si los ves → ¡ya lo tienes!

---

### ✅ ¿CÓMO INSTALARLO SI NO LO TIENES?

Si no lo seleccionaste al instalar Qubes, puedes **añadir Whonix después**.

---

✅ PASOS DETALLADOS:

#### ✅ A. Abre una Terminal en tu qube de plantillas (por ejemplo **dom0**):

```bash
sudo qubes-dom0-update qubes-template-whonix-gw qubes-template-whonix-ws
```

✅ Esto instala las plantillas necesarias:

- whonix-gw (gateway)
- whonix-ws (workstation)

---

#### ✅ B. Reinicia Qubes OS (opcional pero recomendado):

```
systemctl reboot
```

✅ O simplemente cierra y reinicia Qubes Manager.

---

#### ✅ C. Crear el Gateway

Después de instalar las plantillas:

✔️ Abre **Qubes Manager**.

✔️ Menú → **Qube** → **Create New Qube**.

✅ Completa:

- **Name:** sys-whonix
- **Type:** AppVM
- **Template:** whonix-gw-XX
- **Networking:** normalmente → sys-net o sys-firewall.

✅ Marca **Provides Network** (esto le permite ser gateway para otros qubes).

✅ Haz clic en **OK**.

---

✅ Resultado:

```
Creaste el Gateway que conecta a Tor.
```

---

#### ✅ D. Crear la Workstation

✅ Qubes Manager → **Create New Qube**.

✔️ Completa:

- **Name:** anon-whonix
- **Type:** AppVM
- **Template:** whonix-ws-XX
- **Networking:** sys-whonix

✅ Haz clic en **OK**.

---

✅ Resultado:

```
anon-whonix usará sys-whonix como red → todo el tráfico saldrá por Tor.
```

---

### ✅ CÓMO USAR WHONIX EN QUBES PASO A PASO

✅ Para navegar anónimo:

✔️ Abre **anon-whonix** desde el menú.

✔️ Inicia **Tor Browser**.

✔️ Navega → todo pasa por sys-whonix → Tor.

---

✅ Para actualizar Whonix:

✔️ Abre **whonix-ws-XX** → Terminal:

```
sudo apt update && sudo apt upgrade
```

✔️ Abre **whonix-gw-XX** → Terminal:

```
sudo apt update && sudo apt upgrade
```

---

✅ Para crear más qubes que usen Tor:

✔️ Qubes Manager → **Create New Qube**.

✔️ Networking: **sys-whonix**.

✅ Resultado:

```
Ese nuevo qube siempre saldrá por Tor.
```

---

### ✅ EJEMPLO MUY FÁCIL DE ENTENDER

✅ Quiero crear un qube llamado **tor-mail** para leer correo anónimo:

✔️ Qubes Manager → Create New Qube:

- Name: tor-mail
- Color: Púrpura
- Template: whonix-ws-XX
- Networking: sys-whonix

✅ Listo:

```
tor-mail solo se conecta a Internet vía Tor.
```

---

### ✅ TIPOS DE QUBES QUE PUEDES HACER CON WHONIX

✅ sys-whonix (Gateway):

- Obligatorio → maneja Tor.

✅ anon-whonix (Workstation por defecto):

- Navegar con Tor Browser.

✅ Otros:

- tor-chat → para mensajería.
- tor-mail → para email.
- tor-research → para investigación anónima.

---

### ✅ OPCIÓN AVANZADA: CAMBIAR PLANTILLA

✔️ Si quieres actualizar Whonix:

✅ Instala nueva versión de la plantilla:

```bash
sudo qubes-dom0-update qubes-template-whonix-gw qubes-template-whonix-ws
```

✅ Luego en Qubes Manager:

✔️ Botón derecho → Settings → cambia la plantilla a la nueva.

---

### ✅ RESUMEN CLARITO

⭐ Whonix en Qubes = máxima privacidad y Tor integrado.

⭐ sys-whonix = Gateway a Tor.

⭐ anon-whonix = Navegación anónima.

⭐ Todo tráfico pasa por Tor.

⭐ Separación y aislamiento para evitar filtraciones.

---

### ✅ MINI GUÍA PASO A PASO FINAL

✔️ 1️⃣ Abre **Qubes Manager**.

✔️ 2️⃣ Create New Qube → sys-whonix:

- Template: whonix-gw
- Networking: sys-net/sys-firewall
- Provides Network ✅

✔️ 3️⃣ Create New Qube → anon-whonix:

- Template: whonix-ws
- Networking: sys-whonix

✔️ 4️⃣ Abre anon-whonix → Tor Browser.

✔️ 5️⃣ Navega de forma anónima. 🎯

---

### ✅ BUENAS PRÁCTICAS

✅ Usa sys-whonix solo como Gateway → no abras apps ahí.

✅ Usa anon-whonix o clones para tareas separadas.

✅ No instales software innecesario en whonix-ws.

✅ Actualiza regularmente.

✅ Mantén Whonix separado de qubes sin Tor.

---

[🔼](#índice)

---

| **Inicio**         | **atrás 4**           | **Siguiente 6**      |
| ------------------ | --------------------- | -------------------- |
| [🏠](../README.md) | [⏪](./3_4_Whonix.md) | [⏩](./3_6_TAILS.md) |
