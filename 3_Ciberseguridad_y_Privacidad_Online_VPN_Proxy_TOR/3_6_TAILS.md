| **Inicio**         | **atrás 5**             | **Siguiente 7**                        |
| ------------------ | ----------------------- | -------------------------------------- |
| [🏠](../README.md) | [⏪](./3_5_Qubes_OS.md) | [⏩](./3_7_Zero_Knowledge_Services.md) |

---

## **Índice**

| Temario                                                                                |
| -------------------------------------------------------------------------------------- |
| [137. ¿Qué es Tails?](#137-qué-es-tails)                                               |
| [138. Instalación y configuración de Tails](#138-instalación-y-configuración-de-tails) |
| [139. Funcionamiento general de Tails](#139-funcionamiento-general-de-tails)           |
| [140. OnionShare con Tails](#140-onionshare-con-tails)                                 |
| [141. HiddenVM](#141-hiddenvm)                                                         |
| [142. Whonix vs QubesOS vs Tails](#142-whonix-vs-qubesos-vs-tails)                     |

---

# **TAILS**

## **137. ¿Qué es Tails?**

### ✅ ¿QUÉ ES TAILS? (explicación sencilla)

**Tails** es un sistema operativo **enfocado en la privacidad y el anonimato**.

✔️ Es un sistema operativo completo que arranca **desde un USB**.

✔️ No deja rastros en la computadora.

✔️ Todo el tráfico de Internet pasa **exclusivamente por Tor**.

✔️ Incluye herramientas para proteger tu identidad.

---

✅ **Su nombre completo:**

> **Tails = The Amnesic Incognito Live System.**

✅ Significado:

✔️ _Amnesic_ → "con amnesia", **olvida todo** al apagar.

✔️ _Incognito_ → modo anónimo.

✔️ _Live System_ → puedes arrancarlo en cualquier PC desde USB **sin instalar nada en el disco**.

---

✅ **Idea súper sencilla:**

> Tails es como **tu computadora privada y secreta en un USB**.
>
> Donde sea que la conectes, usas Tor y al apagar **no queda rastro**.

---

### ✅ ¿PARA QUÉ SIRVE TAILS?

✔️ Navegar por Internet de forma anónima (a través de Tor).

✔️ Acceder a la Dark Web (.onion).

✔️ Comunicarte en privado.

✔️ Evitar censura o vigilancia.

✔️ Usar herramientas de criptografía.

✔️ No dejar rastros en computadoras prestadas o públicas.

---

✅ **Ejemplos prácticos:**

- Investigar temas sensibles sin ser rastreado.
- Chatear de forma segura (con aplicaciones como Pidgin + OTR).
- Leer documentos sin dejar copias en el disco local.
- Enviar correos cifrados (con Thunderbird + Enigmail).
- Abrir archivos PDF sin temor a infectar tu máquina personal.

---

### ✅ ¿CÓMO FUNCIONA? (explicación fácil)

✅ Tails **no se instala en tu disco duro** → Arranca desde un **USB**.

✅ Usa Tor automáticamente → **todo tu tráfico sale por Tor**.

✅ No guarda nada en el PC → Al apagar se borra **todo**.

---

✅ **Diagrama fácil:**

```
[ Tails (USB) ] → [ Tor Network ] → [ Internet ]
```

✔️ Nadie ve tu IP real.

✔️ El PC anfitrión no guarda evidencia.

---

### ✅ ¿QUÉ TRAE INCLUIDO TAILS?

✅ Aplicaciones preconfiguradas para privacidad:

✔️ **Tor Browser** → Navegar anónimo.

✔️ **Thunderbird** → Email con cifrado.

✔️ **LibreOffice** → Documentos.

✔️ **GnuPG** → Firmar y cifrar archivos.

✔️ **VeraCrypt** → Cifrar discos/volúmenes.

✔️ **OnionShare** → Compartir archivos por Tor.

✔️ **KeePassXC** → Gestor de contraseñas.

✔️ **Electrum** → Billetera Bitcoin.

✔️ Herramientas forenses para abrir archivos de forma segura.

---

✅ Todo configurado para **no filtrar tu identidad**.

---

### ✅ EJEMPLO MUY FÁCIL

✔️ Imagina que viajas y usas un **cibercafé**:

✅ Insertas tu USB con Tails.

✅ Reinicias el computador desde USB.

✅ Usas Tor Browser para navegar.

✅ Escribes un correo con Thunderbird cifrado.

✅ Al apagar → **no queda nada en el disco duro** del cibercafé.

✔️ Nadie puede rastrear lo que hiciste.

---

### ✅ ¿DIFERENCIAS CON WHONIX?

| Característica | Tails                                  | Whonix en Qubes OS                |
| -------------- | -------------------------------------- | --------------------------------- |
| Medio          | USB en cualquier PC                    | Instalado en Qubes OS             |
| Persistencia   | Opcional (se configura)                | Guarda datos en qubes específicos |
| Diseño         | "Live" → no deja rastros por defecto   | Uso en VM aisladas                |
| Movilidad      | Súper portátil (llevar en el bolsillo) | Requiere tu máquina Qubes         |

---

### ✅ REQUISITOS PARA USARLO

✔️ Una memoria USB (mínimo 8 GB, mejor 16 GB o más).

✔️ Un PC que pueda arrancar desde USB.

✔️ Conexión a Internet para descargar la ISO e instalar.

---

### ✅ ¿CÓMO SE INSTALA TAILS? (PASO A PASO)

**¡Ojo!**: _Instalar_ Tails no significa ponerlo en el disco duro, sino **crear el USB booteable**.

---

#### ✅ PASO 1️⃣: DESCARGA TAILS

✅ Ve a la página oficial:

🔗 [https://tails.net](https://tails.net)

✔️ Descarga la imagen ISO.

✔️ Verifica la firma si quieres máxima seguridad (opcional pero recomendado).

---

#### ✅ PASO 2️⃣: PREPARA EL USB

✔️ Necesitas un USB vacío de al menos 8 GB.

✔️ Todos sus datos se borrarán.

---

✅ Hay varias formas de grabar Tails en el USB. Aquí te dejo 2 MUY FÁCILES:

---

##### ✅ OPCIÓN A: Uso de **Tails Installer**

Si ya tienes Tails en otro USB:

✅ Conéctalos ambos.

✅ Abre **Tails Installer**.

✅ Sigue las instrucciones para "clonar" Tails al nuevo USB.

---

##### ✅ OPCIÓN B: Uso de **balenaEtcher** (recomendado para Windows/Mac/Linux)

1️⃣ Descarga e instala **balenaEtcher**:

🔗 [https://www.balena.io/etcher/](https://www.balena.io/etcher/)

2️⃣ Abre Etcher.

3️⃣ Selecciona la ISO de Tails.

4️⃣ Elige tu USB.

5️⃣ Haz clic en **Flash**.

6️⃣ Espera a que termine.

✅ Resultado:

```
Tu USB ahora tiene Tails listo para arrancar.
```

---

#### ✅ PASO 3️⃣: ARRANCAR DESDE EL USB

1️⃣ Inserta el USB en el PC.

2️⃣ Reinicia el PC.

3️⃣ Entra al **boot menu** (usualmente F12, Esc o F2).

4️⃣ Selecciona el USB como dispositivo de arranque.

✅ Tails se carga en RAM.

✅ No toca el disco duro.

---

#### ✅ PASO 4️⃣: INICIO DE TAILS

Al arrancar:

✔️ Aparecerá la pantalla de bienvenida.

✔️ Puedes elegir opciones (teclado, idioma, persistencia).

✔️ Haz clic en **Start Tails**.

✅ En minutos estarás en el escritorio de Tails, **con Tor listo para usar**.

---

### ✅ 9️⃣ USAR TAILS (BÁSICO)

✅ Abre **Tor Browser** → Navega anónimo.

✅ Abre **Thunderbird** → Correos cifrados.

✅ Abre **KeePassXC** → Gestiona contraseñas.

✅ Abre **VeraCrypt** → Monta volúmenes cifrados.

✔️ Todo está configurado para evitar fugas de IP.

---

### ✅ ¿QUÉ ES LA PERSISTENCIA?

Por defecto, Tails **olvida todo al apagar**.

✅ Pero puedes **configurar Persistencia** (opcional):

- Encriptada con contraseña.
- Guarda ciertas cosas en el USB:

✔️ Archivos.

✔️ Marcadores de navegador.

✔️ Contraseñas.

✔️ Llaves GPG.

✔️ Configuraciones.

✅ Súper útil → sin sacrificar privacidad.

---

### ✅ EJEMPLO MUY REAL

✅ María es periodista.

✅ Usa Tails en un USB.

✅ Va a un cibercafé:

✔️ Arranca Tails.

✔️ Escribe un reportaje.

✔️ Usa Tor Browser para contactar fuentes.

✔️ Guarda su trabajo en la **partición persistente cifrada**.

✔️ Apaga el PC → **no queda rastro en el cibercafé**.

✔️ Solo ella puede abrir sus archivos con la contraseña de persistencia.

---

### ✅ BUENAS PRÁCTICAS

✔️ Descarga siempre desde [tails.net](https://tails.net).

✔️ Verifica la firma si puedes.

✔️ Usa un USB confiable.

✔️ No uses Tails para loguearte en cuentas reales (¡rompe el anonimato!).

✔️ Configura la persistencia solo si la necesitas.

✔️ Usa Tor Browser para todo.

✔️ Apaga siempre Tails antes de quitar el USB.

---

### ✅ RESUMEN SÚPER CORTO

⭐ **Tails = sistema operativo anónimo en USB.**

⭐ Todo tráfico → Tor.

⭐ No deja rastros en la PC.

⭐ Herramientas de privacidad incluidas.

⭐ Arranca en cualquier computadora.

⭐ Persistencia cifrada opcional.

---

### ✅ MINI GUÍA ULTRARÁPIDA

✅ 1️⃣ Descarga ISO de [tails.net](https://tails.net).

✅ 2️⃣ Grábala en un USB (con Etcher).

✅ 3️⃣ Arranca el PC desde USB.

✅ 4️⃣ Usa Tails → Tor Browser, Thunderbird, etc.

✅ 5️⃣ Apaga → se borra todo.

---

[🔼](#índice)

---

## **138. Instalación y configuración de Tails**

### ✅ ¿QUÉ ES TAILS (recordatorio súper corto)?

✔️ Tails = sistema operativo _en vivo_ (live), que se ejecuta **desde un USB**.

✔️ Todo tráfico pasa **por Tor** para anonimato.

✔️ No deja rastros en la computadora.

✔️ Puedes llevarlo en tu bolsillo y usarlo en cualquier PC.

✅ Idea fácil:

> Tu sistema operativo anónimo y portátil en un USB.

---

### ✅ REQUISITOS ANTES DE EMPEZAR

✔️ Una memoria USB (mínimo 8 GB, recomendado 16 GB o más).

✔️ Una PC o laptop donde puedas arrancar desde USB.

✔️ Una segunda USB opcional para hacer la instalación inicial más fácil.

✔️ Conexión a Internet para descargar la imagen de Tails.

✅ _IMPORTANTE:_

> **Se borrarán todos los datos del USB**. Haz respaldo si lo necesitas.

---

### ✅ DESCARGA DE TAILS (paso a paso)

#### ✅ Ve al sitio oficial

🔗 [https://tails.net](https://tails.net)

✅ Siempre descarga desde la página oficial → evita versiones falsas.

---

#### ✅ Elige tu sistema operativo para la guía

✔️ Tails.net te ofrece un **asistente de instalación** que te va guiando según tu sistema (Windows, macOS, Linux).

✔️ Sigue las instrucciones para descargar la ISO (archivo de imagen de Tails).

---

#### ✅ Verificación (opcional pero MUY recomendado)

✔️ Puedes verificar la firma o el checksum para asegurarte de que no fue modificado.

✔️ Tails.net tiene **un verificador en la web** para Windows y guías para Linux/macOS.

✅ Idea fácil:

> Es como verificar el “sello de seguridad” de la descarga.

---

### ✅ GRABAR TAILS EN UN USB (crear el USB booteable)

✅ Aquí te explico **la forma más sencilla para Windows, Mac y Linux**.

---

#### ✅ OPCIÓN MÁS FÁCIL: Usar **balenaEtcher** (recomendado)

✅ balenaEtcher es una herramienta gráfica súper fácil:

🔗 [https://www.balena.io/etcher/](https://www.balena.io/etcher/)

---

##### ✅ PASOS CON ETCHER

1️⃣ Descarga e instala balenaEtcher.

2️⃣ Conecta el USB vacío a tu computadora.

3️⃣ Abre balenaEtcher.

4️⃣ Haz clic en **Flash from file** y elige la ISO de Tails que descargaste.

5️⃣ Selecciona tu USB en **Select target**.

6️⃣ Haz clic en **Flash**.

✅ Etcher formateará el USB y pondrá Tails en él.

✅ Resultado:

> ¡Tu USB ahora tiene Tails listo para arrancar!

---

✅ _Nota para usuarios avanzados:_

También puedes usar **dd** o **Rufus**. Pero Etcher es el más fácil.

---

### ✅ ARRANCAR DESDE EL USB

✅ Una vez que tienes el USB listo:

✔️ Inserta el USB en la computadora en la que quieres usar Tails.

✔️ Apaga la computadora.

✔️ Enciéndela y **entra al menú de arranque (boot menu)**.

- Usualmente se hace presionando F12, F2, Esc o Del (varía según la marca).

  ✔️ Elige arrancar desde tu USB.

✅ Resultado:

> La computadora arrancará Tails desde el USB.

---

✅ _Truco fácil:_

> Busca en Google: _cómo entrar al boot menu en \[marca de tu laptop]_.

---

### ✅ INICIO DE TAILS (Pantalla de bienvenida)

Cuando arranca Tails, verás la **pantalla de bienvenida**:

✔️ Puedes elegir el idioma y la distribución de teclado.

✔️ Puedes activar opciones avanzadas (por ejemplo, Tor Bridges si estás en un país que bloquea Tor).

✔️ Puedes activar **Persistencia** (opcional, te explico abajo).

✅ Cuando termines → haz clic en **Start Tails**.

---

✅ Espera un momento y verás el **escritorio de Tails**.

✔️ ¡Ya estás listo para usarlo!

---

### ✅ PRIMER USO DE TAILS

En el escritorio:

✔️ Abre **Tor Browser** → Navega anónimo.

✔️ Usa **Thunderbird** → correo cifrado.

✔️ Abre **OnionShare** → compartir archivos por Tor.

✔️ **KeePassXC** → gestor de contraseñas.

✔️ **LibreOffice** → documentos.

✔️ **VeraCrypt** → cifrar discos/archivos.

✅ Todo está configurado para **no filtrar tu IP real**.

---

✅ Importante:

> Al apagar Tails → TODO se borra, no queda rastro.

---

### ✅ CONFIGURAR PERSISTENCIA (OPCIONAL)

✅ Por defecto, Tails no guarda nada.

✅ Puedes habilitar **Persistencia cifrada** para guardar algunos datos en el USB.

---

#### ✅ ¿Qué puedes guardar en Persistencia?

✔️ Archivos personales.

✔️ Configuración de red Wi-Fi.

✔️ Llaves GPG.

✔️ Contraseñas en KeePassXC.

✔️ Marcadores del navegador.

✔️ Servidores de correo en Thunderbird.

✔️ Aplicaciones adicionales.

✅ Todo en un **volumen cifrado con contraseña**.

---

#### ✅ CÓMO ACTIVAR PERSISTENCIA (paso a paso)

1️⃣ Arranca Tails desde el USB.

2️⃣ En la pantalla de bienvenida, haz clic en **+ Configure persistent storage**.

3️⃣ Elige una **contraseña fuerte** → se usará para cifrar tu espacio persistente.

4️⃣ Tails creará la partición cifrada en el mismo USB.

5️⃣ Reinicia Tails.

✅ Resultado:

> La próxima vez que arranques, podrás desbloquear tu volumen persistente poniendo tu contraseña.

---

✅ _Truco:_

> Solo se guarda lo que TÚ habilites → así mantienes el control de qué se conserva.

---

---

### ✅ EJEMPLO PRÁCTICO MUY FÁCIL

✅ Imagínate que eres Ana, periodista:

✔️ Descargas Tails en tu casa.

✔️ Creas un USB booteable con Etcher.

✔️ Vas a un cibercafé.

✔️ Arrancas desde el USB → Tor Browser listo.

✔️ Escribes un artículo en LibreOffice.

✔️ Lo guardas en la **Persistencia cifrada** del USB.

✔️ Apagas la PC → **no queda nada en el disco duro del cibercafé**.

✔️ Todo el trabajo está seguro en tu USB, protegido por contraseña.

---

### ✅ BUENAS PRÁCTICAS DE SEGURIDAD

✔️ Descarga siempre desde [https://tails.net](https://tails.net).

✔️ Verifica la firma de la ISO si puedes.

✔️ Usa una contraseña fuerte para la Persistencia.

✔️ Usa Tor Browser para todo → evita filtraciones de IP.

✔️ No inicies sesión en cuentas reales que puedan revelar tu identidad (rompería el anonimato).

✔️ Apaga Tails antes de quitar el USB → garantiza que se borre todo.

✔️ Lleva el USB contigo → evita robos.

---

### ✅ RESUMEN SÚPER CORTITO

⭐ Tails = sistema operativo anónimo en USB.

⭐ Todo tráfico → Tor.

⭐ No deja rastros en la PC.

⭐ Puedes configurarlo para guardar ciertos datos de forma cifrada.

⭐ Muy fácil: descargar → grabar en USB → arrancar → usar → apagar = todo borrado.

---

### ✅ MINI GUÍA ULTRARÁPIDA

✅ 1️⃣ Descarga la ISO desde [tails.net](https://tails.net).

✅ 2️⃣ Grábala en un USB con **balenaEtcher**.

✅ 3️⃣ Arranca la computadora desde el USB.

✅ 4️⃣ Elige idioma y configuración → Start Tails.

✅ 5️⃣ Usa Tor Browser y apps incluidas.

✅ 6️⃣ Opcional → configura Persistencia cifrada.

✅ 7️⃣ Apaga → no queda rastro en la máquina.

---

[🔼](#índice)

---

## **139. Funcionamiento general de Tails**

### ✅ ¿QUÉ ES TAILS? (recordatorio rápido)

**Tails** = _The Amnesic Incognito Live System_.

✅ Es un sistema operativo **en vivo** (live) → se usa desde un **USB**.

✅ Todo el tráfico de Internet pasa **exclusivamente por Tor**.

✅ Está diseñado para **no dejar rastros** en la computadora.

✅ Puedes usarlo en **cualquier PC** sin instalar nada en el disco.

✔️ **Idea sencilla:**

> Es como tu propio “sistema operativo secreto” que llevas en un USB.

---

### ✅ ¿CÓMO FUNCIONA? (explicación sencilla)

Vamos paso por paso:

---

#### ✅ A. **Arranque en vivo (Live boot)**

✔️ Tails se inicia desde un USB, no se instala en el disco duro.

✔️ Cuando apagas el PC, **todo se borra de la RAM**.

✔️ Así no deja rastros en la computadora.

---

✅ **Ejemplo súper fácil:**

> Piensa en Tails como un “CD en vivo” pero en USB. Cuando lo arrancas, tienes un sistema nuevo, limpio, privado.

---

#### ✅ B. **Todo el tráfico por Tor**

✔️ Tails **fuerza todo el tráfico de Internet a pasar por Tor**.

✔️ Ninguna app puede conectarse directo → todas van por Tor.

✔️ Así se oculta tu dirección IP real.

✅ **Esquema simple:**

```
Tails (USB) → Tor Network → Internet
```

---

✅ **Ejemplo fácil:**

> Usas Tor Browser en Tails → tu IP real nunca se expone. Todos ven solo la IP de salida de Tor.

---

#### ✅ C. **Sistema Amnésico**

✔️ Tails olvida **todo** cuando apagas el PC.

✔️ No guarda contraseñas, archivos, historial, nada.

✔️ Es como una hoja en blanco cada vez.

✅ _Excepto si activas la persistencia cifrada (opcional)_.

---

✅ **Ejemplo:**

> Si escribiste un documento, al reiniciar Tails, desaparece (a menos que tú lo guardes en la partición persistente cifrada).

---

#### ✅ D. **Sistema Portátil y Autónomo**

✔️ Puedes usar Tails en **cualquier computadora**.

✔️ No necesitas instalar nada en el disco duro.

✔️ Solo necesitas que la PC pueda arrancar desde USB.

✅ **Ejemplo real:**

> Estás de viaje → entras a un cibercafé → inicias tu propio sistema operativo desde USB → nadie sabe lo que hiciste → apagas y no queda rastro.

---

### ✅ ¿QUÉ TRAE INCLUIDO TAILS? (Apps y herramientas)

Tails no solo es el sistema → incluye apps ya configuradas para la privacidad.

---

✅ ✔️ **Tor Browser**

- Navegar anónimo en la web.
- Acceso a sitios .onion.
- Evita rastreo y censura.

---

✅ ✔️ **Thunderbird + Enigmail**

- Email cifrado con GPG.
- Puedes firmar y cifrar tus correos.

---

✅ ✔️ **OnionShare**

- Compartir archivos de forma anónima por Tor.

---

✅ ✔️ **KeePassXC**

- Guardar contraseñas cifradas.

---

✅ ✔️ **LibreOffice**

- Editar documentos sin depender de la máquina anfitriona.

---

✅ ✔️ **VeraCrypt**

- Abrir/crear volúmenes cifrados.

---

✅ ✔️ **Electrum**

- Cartera de Bitcoin ligera.

---

✅ ✔️ Herramientas de análisis seguro de archivos

- Evitar malware al abrir documentos.

---

✅ **Todo está preconfigurado** para:

✔️ Salir solo por Tor.

✔️ Evitar fugas de IP.

✔️ Proteger tu anonimato.

---

### ✅ FUNCIONAMIENTO GENERAL EN EJEMPLOS SÚPER CLAROS

✔️ 📌 **Ejemplo 1: Navegar anónimo**

- Inicias Tails.
- Abres Tor Browser.
- Accedes a un sitio sin revelar tu IP real.

---

✔️ 📌 **Ejemplo 2: Escribir un artículo**

- Abres LibreOffice.
- Escribes tu documento.
- Lo guardas en la partición persistente cifrada (opcional).
- Nadie en la PC anfitriona ve nada.

---

✔️ 📌 **Ejemplo 3: Compartir archivos de forma segura**

- Usas OnionShare.
- Creas un enlace .onion para compartir.
- Solo quien tenga el enlace puede descargarlo por Tor.

---

✔️ 📌 **Ejemplo 4: Leer correos cifrados**

- Abres Thunderbird.
- Usas tu clave GPG para descifrar.
- Todo pasa por Tor.

---

### ✅ ¿CÓMO SE INSTALA TAILS? (CREAR EL USB)

✅ Nota: _En Tails no hay “instalación en disco duro”._
Lo que haces es **crear un USB booteable**.

---

#### ✅ PASO 1: Descargar la ISO oficial

✔️ Ve a [https://tails.net](https://tails.net)

✔️ Descarga la imagen .img o .iso.
✔️ (Opcional) Verifica la firma para más seguridad.

---

#### ✅ PASO 2: Grabar la ISO en el USB

✅ Herramienta súper fácil: **balenaEtcher**

- 🔗 [https://balena.io/etcher](https://balena.io/etcher)
- Compatible con Windows, macOS y Linux.

---

##### ⚡ PASOS CON ETCHER

1️⃣ Abre Etcher.

2️⃣ Elige la ISO de Tails.

3️⃣ Selecciona tu USB.

4️⃣ Haz clic en **Flash**.

5️⃣ Espera → ¡listo!

✅ Resultado:

> Tu USB ahora arranca Tails.

---

### ✅ ¿CÓMO SE USA TAILS? (Arranque)

✔️ Inserta el USB en la PC.

✔️ Apaga y enciende la computadora.

✔️ Entra al **Boot Menu** (F12, Esc, F2… depende del modelo).

✔️ Elige arrancar desde USB.

---

✅ Pantalla de bienvenida de Tails:

- Elige idioma.
- Configura teclado.
- Opciones de red (Tor Bridges si hace falta).
- **Haz clic en Start Tails.**

---

✔️ Espera → escritorio de Tails cargado.

✔️ Abre Tor Browser → ¡listo para navegar anónimo!

---

### ✅ OPCIONAL: Configurar PERSISTENCIA

Por defecto → Tails **olvida todo**.
Si quieres → puedes habilitar **Persistencia cifrada**.

---

✅ **¿Qué es la Persistencia?**

Una parte cifrada del USB donde puedes guardar:

✔️ Documentos.

✔️ Contraseñas.

✔️ Claves GPG.

✔️ Configuración de red Wi-Fi.

✔️ Marcadores del navegador.

---

✅ **Cómo se configura (paso a paso):**

1️⃣ Arranca Tails desde el USB.

2️⃣ En la pantalla de bienvenida, haz clic en **+ Configure persistent storage**.

3️⃣ Elige y confirma una **contraseña fuerte**.

4️⃣ Tails crea el volumen cifrado.

5️⃣ Reinicia Tails.

6️⃣ Ahora podrás desbloquear la Persistencia al inicio poniendo tu contraseña.

---

✅ **Ejemplo fácil:**

> Guardas un artículo en la Persistencia. Solo tú, con tu contraseña, puedes abrirlo en el futuro.

---

### ✅ BUENAS PRÁCTICAS

✔️ Descargar siempre desde [tails.net](https://tails.net).

✔️ Verificar la firma si puedes.

✔️ Usar Tor Browser para todo → evitar fugas.

✔️ No iniciar sesión en cuentas que revelen tu identidad real.

✔️ Apagar Tails antes de quitar el USB.

✔️ Usar contraseña fuerte en la Persistencia.

✔️ Llevar el USB contigo → evitar robos.

---

### ✅ RESUMEN FINAL (ultra claro)

⭐ Tails = sistema operativo en USB → para privacidad y anonimato.

⭐ Todo tráfico pasa por Tor → tu IP real está oculta.

⭐ No deja rastros en el disco duro.

⭐ Incluye apps preparadas para privacidad (Tor Browser, Thunderbird, KeePassXC, VeraCrypt).

⭐ Persistencia cifrada opcional → solo si tú la activas.

---

### ✅ MINI GUÍA RÁPIDA PASO A PASO

✅ 1️⃣ Descarga la ISO desde [tails.net](https://tails.net).

✅ 2️⃣ Grábala en un USB (con balenaEtcher).

✅ 3️⃣ Arranca la computadora desde el USB.

✅ 4️⃣ Pantalla de bienvenida → Start Tails.

✅ 5️⃣ Usa Tor Browser y apps incluidas.

✅ 6️⃣ (Opcional) Configura Persistencia cifrada para guardar datos.

---

[🔼](#índice)

---

## **140. OnionShare con Tails**

### 🌱 ¿QUÉ ES ONIONSHARE?

**OnionShare** es una herramienta que sirve para:

✔️ **Compartir archivos de forma anónima y segura** a través de la red Tor.

✔️ Crear un enlace secreto .onion que puedes pasar a otra persona.

✔️ Nadie sabe quién eres ni desde dónde lo envías.

---

✅ **Idea fácil:**

Es como si crearas tu propio _servidor temporal_ que vive en Tor, para compartir documentos, imágenes, etc., **sin depender de ningún servicio externo**.

---

### 🔒 ¿CÓMO FUNCIONA? (explicación sencilla)

1️⃣ Tú eliges un archivo o carpeta que quieras compartir.

2️⃣ OnionShare crea un enlace Tor tipo:

```
http://asj23dh1...onion
```

3️⃣ Le das ese enlace a quien quieras.

4️⃣ La otra persona abre ese enlace **usando Tor Browser** y descarga el archivo directamente desde tu computadora.

5️⃣ Cuando cierras OnionShare, el enlace deja de funcionar.

---

✅ **Ejemplo súper claro:**

> Quieres enviar un documento importante a tu amigo.
>
> Arrancas Tails, abres OnionShare, seleccionas el archivo.
>
> Te da un enlace .onion que le mandas por Signal o Telegram.
>
> Tu amigo lo abre en Tor Browser y descarga el archivo.
>
> Nadie más puede verlo.

---

### ✨ ¿QUÉ VENTAJAS TIENE ONIONSHARE?

✔️ **No necesitas servicios de terceros** (ni Google Drive, ni Dropbox).

✔️ **Anonimato total**: se basa en Tor.

✔️ **Cifrado extremo a extremo**: la conexión es segura.

✔️ **Autodestrucción**: cuando cierras OnionShare, nadie más accede al enlace.

✔️ Puedes compartir archivos grandes (limitado solo por tu conexión).

---

### 🖥️ ¿CÓMO INSTALAR TAILS? (si aún no lo tienes)

Te recuerdo rápido cómo crear tu USB Tails:

✅ 1️⃣ Descarga Tails desde [https://tails.net](https://tails.net).

✅ 2️⃣ Usa **balenaEtcher** para grabar la ISO en un USB (mínimo 8 GB).

✅ 3️⃣ Reinicia tu PC y arranca desde el USB.

✅ 4️⃣ Pantalla de bienvenida: **Start Tails**.

Si quieres guía detallada, dime y te la paso completa.

---

### 🟢 ¿CÓMO USAR ONIONSHARE EN TAILS?

Aquí la parte importante:

OnionShare ya **viene instalado en Tails**.

¡No tienes que instalar nada adicional!

---

#### ✨ PASO A PASO

##### ✅ Paso 1: Arrancar Tails

1️⃣ Inserta tu USB Tails.

2️⃣ Arranca la computadora desde el USB.

3️⃣ En la pantalla de bienvenida, haz clic en **Start Tails**.

---

##### ✅ Paso 2: Conectarte a Tor

✔️ Tails automáticamente establece la conexión a la red Tor.

✔️ Espera a que el icono de la cebolla en la esquina superior derecha se ponga verde.

---

##### ✅ Paso 3: Abrir OnionShare

1️⃣ Haz clic en el botón **Applications** (arriba a la izquierda).

2️⃣ Busca **OnionShare**.

3️⃣ Haz clic para abrirlo.

Verás una ventana como esta (dependiendo de tu versión):

```
[📂] Select Files
[🌐] Start Sharing
[⚙️] Settings
```

---

##### ✅ Paso 4: Elegir qué compartir

1️⃣ Haz clic en **Add Files** (o **Select Files**).

2️⃣ Navega y selecciona tu archivo o carpeta.

3️⃣ Verás el archivo listado en la ventana.

---

##### ✅ Paso 5: Empezar a compartir

1️⃣ Haz clic en **Start Sharing**.

2️⃣ OnionShare generará un enlace .onion, por ejemplo:

```
http://as1d2f3g4h5.onion
```

3️⃣ Copia ese enlace.

---

✅ **Importante:**

Mientras OnionShare está abierto y activo, **tu computadora es el servidor**. Si la apagas o cierras OnionShare, el enlace deja de funcionar.

---

##### ✅ Paso 6: Enviar el enlace

✔️ Usa un canal seguro (Signal, Telegram, correo cifrado) para enviarle el enlace a la persona que descargará.

---

##### ✅ Paso 7: El receptor descarga el archivo

✔️ La otra persona abre **Tor Browser** en su computadora.

✔️ Pega el enlace .onion en la barra de direcciones.

✔️ Descarga el archivo.

---

##### ✅ Paso 8: Terminar

✔️ Cuando termines de compartir, haz clic en **Stop Sharing**.

✔️ El enlace queda inservible.

✅ ¡Todo listo! El archivo ha sido compartido de manera segura.

---

### 🌿 EJEMPLO COMPLETO PASO A PASO

Vamos con un ejemplo de la vida real:

---

**Ejemplo: Marta quiere enviar una foto privada a su colega Juan**

1️⃣ Marta inicia Tails en un cibercafé.

2️⃣ Conecta su USB con la foto.

3️⃣ Abre OnionShare en Tails.

4️⃣ Añade la foto a compartir.

5️⃣ Inicia el servicio y obtiene este enlace:

```
http://kfh39sf4...onion
```

6️⃣ Le manda el enlace a Juan por Signal.

7️⃣ Juan abre Tor Browser en su laptop.

8️⃣ Pega el enlace y descarga la foto.

9️⃣ Marta hace **Stop Sharing**.

✅ Nadie más puede acceder.

---

### ⚠️ BUENAS PRÁCTICAS DE SEGURIDAD

✅ Usa canales seguros para compartir el enlace.

✅ No abras OnionShare en sistemas sin Tor (pierdes anonimato).

✅ Cierra OnionShare cuando termines.

✅ Usa Tails o sistemas limpios para máxima seguridad.

✅ Mantén Tails actualizado (nuevas versiones corrigen fallos).

---

### 🏁 MINI GUÍA ULTRARRÁPIDA

1️⃣ Arranca Tails desde tu USB.

2️⃣ Conéctate a Tor.

3️⃣ Abre OnionShare.

4️⃣ Añade archivos.

5️⃣ Start Sharing → copia el enlace .onion.

6️⃣ Envía el enlace por un canal seguro.

7️⃣ El receptor descarga vía Tor Browser.

8️⃣ Stop Sharing cuando termines.

---

[🔼](#índice)

---

## **141. HiddenVM**

### ✅ ¿QUÉ ES HIDDENVM?

**HiddenVM** es un proyecto que te permite:

✔️ Correr máquinas virtuales (VMs) de forma **oculta y cifrada**.

✔️ Usar sistemas operativos completos (como Whonix o Tails) **dentro de un contenedor cifrado**.

✔️ Lanzar esas VMs **directamente desde Tails o Linux**, sin dejar rastros en tu disco duro.

✅ Su objetivo:

> Crear un “entorno virtual privado” donde puedas usar Tor, Whonix o cualquier otra VM sin revelar nada a quien use tu computadora.

---

✅ **Idea muy sencilla:**

> HiddenVM = Un USB cifrado con un sistema operativo dentro de VirtualBox, que solo tú puedes abrir.

---

### 🔎 ✅ ¿PARA QUÉ SIRVE?

✔️ Para tener **una máquina virtual oculta** (Whonix, Kali, Ubuntu, etc.).

✔️ Para **ocultar la existencia de tus archivos** en un volumen cifrado (usando VeraCrypt).

✔️ Para **llevarla en un USB** y usarla en cualquier PC.

✔️ Para **combinar con Tails** y maximizar el anonimato.

---

✅ **Ejemplo muy claro:**

> Imagina que tienes una máquina virtual con Whonix y tus configuraciones de Tor. La guardas en un volumen cifrado.
>
> Nadie sabe que existe.
>
> Cuando la montas con tu clave, la arrancas con VirtualBox y la usas.
>
> Al desmontarla → se borra todo rastro.

---

### 🗂️ ✅ ¿CÓMO FUNCIONA? (explicación fácil)

✅ HiddenVM combina 3 cosas:

1️⃣ **VeraCrypt**: crea un volumen cifrado en tu USB o disco.

2️⃣ **VirtualBox Portable**: ejecuta máquinas virtuales **sin instalar nada** en la PC anfitriona.

3️⃣ **Máquinas virtuales preparadas** (como Whonix).

---

✅ **Esquema sencillo:**

```
[USB con VeraCrypt] → [Desbloqueas con clave] → [Abres VirtualBox Portable] → [Arrancas Whonix VM]
```

✅ Sin tu contraseña → **nadie sabe que la VM está ahí**.

---

### ✅ VENTAJAS DE HIDDENVM

✔️ **Portátil** → en un USB.

✔️ **Cifrado fuerte** → VeraCrypt.

✔️ **No requiere instalación** → VirtualBox portable.

✔️ **Privacidad extra** → puedes usar Tor y Whonix.

✔️ **Compatibilidad** → Linux (sobre todo Tails) y Windows.

---

### 🏁 ✅ EJEMPLO REAL MUY SENCILLO

✅ Paso a paso simplificado:

1️⃣ Tú creas un contenedor VeraCrypt de 32 GB en un USB.

2️⃣ Lo desbloqueas en Tails o Linux.

3️⃣ Dentro está VirtualBox portable + tu VM Whonix.

4️⃣ Abres VirtualBox → Inicias Whonix → Navegas por Tor.

5️⃣ Cuando terminas → Apagas → Desmontas VeraCrypt → Cierra todo.

6️⃣ El contenedor cifrado parece un archivo basura → nadie puede abrirlo sin tu clave.

---

### 🧰 ✅ ¿QUÉ NECESITAS PARA USAR HIDDENVM?

✔️ Un USB de al menos 32 GB (más grande es mejor).

✔️ Una computadora que pueda arrancar Tails o Linux.

✔️ Conexión para descargar los archivos iniciales.

✔️ VeraCrypt.

✔️ VirtualBox (o la versión portable de VirtualBox).

✔️ Imágenes de VM (por ejemplo, Whonix).

---

### ✅ INSTALACIÓN Y CONFIGURACIÓN PASO A PASO

¡Ahora te explico cómo se instala y configura HiddenVM con un ejemplo fácil!

---

#### ✅ PASO 1️⃣: Prepara tu USB

✔️ Consigue un USB vacío de al menos 32 GB.

✔️ Conéctalo en tu computadora.

---

✅ _Idea fácil:_

> Tu USB será tu “disco duro secreto”.

---

#### ✅ PASO 2️⃣: Instala VeraCrypt

✔️ En Tails o en tu Linux:

```bash
sudo apt install veracrypt
```

✔️ En Windows o Mac → descárgalo desde [https://www.veracrypt.fr](https://www.veracrypt.fr).

---

✅ **¿Qué es VeraCrypt?**

> Un programa para crear “cajas fuertes” digitales cifradas.

---

#### ✅ PASO 3️⃣: Crea un volumen cifrado

1️⃣ Abre VeraCrypt.

2️⃣ Haz clic en **Create Volume**.

3️⃣ Elige **Create an encrypted file container**.

4️⃣ Elige ubicación → en tu USB.

- Ejemplo: `/media/usb/HiddenVMContainer.hc`

  5️⃣ Tamaño → por ejemplo, 32 GB.

  6️⃣ Elige cifrado (AES es suficiente para la mayoría).

  7️⃣ Elige una contraseña fuerte → **guárdala bien**.

  8️⃣ Formatea el volumen → espera a que termine.

---

✅ Resultado:

> Un **archivo .hc** cifrado que luce como basura, pero dentro podrás guardar tus VMs.

---

#### ✅ PASO 4️⃣: Montar el volumen

✔️ Abre VeraCrypt.

✔️ Selecciona tu archivo .hc.

✔️ Haz clic en **Mount**.

✔️ Ingresa tu contraseña.

✅ Resultado:

> Aparecerá como una carpeta normal → aquí copiarás tus cosas.

---

#### ✅ PASO 5️⃣: Instalar VirtualBox Portable (opcional)

✅ Para Linux o Tails:

✔️ En Tails ya tienes **VirtualBox Guest Additions** instaladas.

✔️ Puedes instalar VirtualBox en modo "portable" dentro del volumen montado.

✔️ O usar el VirtualBox del sistema si está disponible.

✅ En Windows:

✔️ Descarga VirtualBox portable o normal y cópialo en el volumen montado.

---

✅ _Idea:_

> VirtualBox en tu volumen cifrado → nadie lo ve si no montas VeraCrypt.

---

#### ✅ PASO 6️⃣: Copiar la VM (por ejemplo Whonix)

✔️ Descarga Whonix → [https://www.whonix.org](https://www.whonix.org).

✔️ Descomprime los archivos .ova o .vdi.

✔️ Copia la carpeta de la VM dentro de tu volumen VeraCrypt montado.

✅ Resultado:

> Todo queda cifrado en el contenedor.

---

#### ✅ PASO 7️⃣: Usar HiddenVM

✅ Cuando quieras usarlo:

1️⃣ Arranca Tails o Linux.

2️⃣ Monta tu volumen VeraCrypt.

3️⃣ Abre VirtualBox desde ahí o el del sistema.

4️⃣ Importa o abre la VM (Whonix).

5️⃣ Inicia la VM → Usa Tor, navegador, etc.

✅ Cuando termines:

- Apaga la VM.
- Cierra VirtualBox.
- Desmonta VeraCrypt.

✔️ ¡Se borra todo de la RAM!

✔️ El volumen cifrado se guarda como un archivo imposible de abrir sin la clave.

---

### ✅ BUENAS PRÁCTICAS

✔️ Usa contraseñas fuertes para VeraCrypt.

✔️ No dejes montado el volumen si no lo estás usando.

✔️ No copies la clave en texto plano.

✔️ Haz backups cifrados en otras ubicaciones.

✔️ Usa Tor dentro de Whonix para navegar.

✔️ Mantén actualizado Tails o Linux.

---

### ✅ MINI RESUMEN SÚPER CLARO

⭐ **HiddenVM = VeraCrypt + VirtualBox + Whonix.**

⭐ Creas un volumen cifrado → metes VirtualBox portable y tus VMs.

⭐ Nadie ve nada sin tu contraseña.

⭐ Puedes usarlo en cualquier PC arrancando Tails o Linux.

⭐ Ideal para anonimato y privacidad.

---

### ✅ MINI GUÍA ULTRARRÁPIDA

✅ 1️⃣ Consigue USB (mínimo 32 GB).

✅ 2️⃣ Instala VeraCrypt.

✅ 3️⃣ Crea volumen cifrado en el USB.

✅ 4️⃣ Monta volumen → copia VirtualBox portable.

✅ 5️⃣ Descarga e importa Whonix VM dentro del volumen.

✅ 6️⃣ Arranca desde Tails → monta → abre VM → usa Tor.

✅ 7️⃣ Al terminar → apaga → desmonta → desaparece.

---

### ✅ 🌟 EJEMPLO FINAL MUY FÁCIL

✔️ Ana es activista:

✅ Tiene un USB de 64 GB.

✅ Crea un volumen VeraCrypt → `Activismo.hc`.

✅ Dentro instala VirtualBox portable y Whonix VM.

✅ Al viajar → lleva solo el USB.

✅ En cibercafés → arranca Tails → monta VeraCrypt → abre Whonix → navega por Tor.

✅ Al apagar → no queda nada en la PC.

✅ Nadie puede abrir el contenedor sin su clave.

---

[🔼](#índice)

---

## **142. Whonix vs QubesOS vs Tails**

### 🌟 PRIMERO: VISIÓN GENERAL

✅ Los tres son sistemas diseñados para **anonimato, privacidad y seguridad**, pero funcionan de formas muy diferentes:

| Sistema  | Tipo                   | Enfoque Principal                       |
| -------- | ---------------------- | --------------------------------------- |
| Tails    | Live OS en USB         | Anonimato _temporal_, amnésico          |
| Whonix   | Sistema basado en Tor  | Anonimato _persistente_, en VM          |
| Qubes OS | Sistema operativo Host | Seguridad por aislamiento de VM (qubes) |

✅ Vamos a explicar cada uno por separado y compararlos.

---

### 🌱 ¿QUÉ ES TAILS?

✔️ Tails = **The Amnesic Incognito Live System**.

✔️ Es un **sistema operativo en vivo** que se arranca desde un USB.

✔️ Todo su tráfico pasa por **Tor**.

✔️ No deja rastros en la computadora al apagar.

✅ Idea fácil:

> Imagina un sistema desechable: usas, apagas, desaparece.

✅ Ventajas:

- Súper fácil de usar.
- No requiere instalación en disco.
- Ideal para uso temporal (cibercafé, viaje).
- Todo se olvida al apagar (amnésico).

✅ Limitaciones:

- No guarda nada por defecto (salvo si configuras _Persistencia cifrada_).
- No es práctico para trabajo diario con muchas apps.
- Dependes de que puedas arrancar desde USB.

✅ Ejemplo real:

> Una periodista en un hotel arranca Tails en la laptop del hotel → escribe un artículo → sube a la web .onion → apaga → la laptop del hotel queda limpia.

---

### 🌱 ¿QUÉ ES WHONIX?

✔️ Whonix = sistema operativo orientado al anonimato **usando Tor**.

✔️ Diseñado para funcionar dentro de máquinas virtuales (VM).

✔️ Se compone de dos partes:

- **Gateway** → todo el tráfico sale por Tor.
- **Workstation** → tu escritorio normal, sin acceso directo a Internet.

✅ Idea fácil:

> Tu computadora está _dividida en dos_ → uno que filtra por Tor y otro que usas normalmente.

✅ Ventajas:

- Fuerte separación entre Tor y aplicaciones.
- Persistencia: puedes guardar configuraciones, claves.
- Se actualiza como cualquier Linux (Debian).
- Puede usarse en Qubes OS para más aislamiento.

✅ Limitaciones:

- Necesita VirtualBox, KVM o Qubes para funcionar.
- Más pesado (mínimo \~4 GB RAM recomendado).
- No es “live” → deja rastros si no usas cifrado.

✅ Ejemplo real:

> Un investigador instala Whonix en VirtualBox → usa la Workstation para navegar por Tor → nada de su IP real se filtra, incluso si hay malware.

---

### 🌱 ¿QUÉ ES QUBES OS?

✔️ Qubes OS = un **sistema operativo completo** diseñado para seguridad máxima.

✔️ Basado en la idea de **aislar todo en máquinas virtuales (qubes)**.

✔️ “Seguridad por compartimentalización”.

✅ Idea fácil:

> Es como tener muchos escritorios virtuales separados entre sí → uno para trabajo, otro para navegación anónima, otro para abrir archivos dudosos.

✅ Ventajas:

- Separación fuerte entre actividades (qubes).
- Puedes tener un qube con Whonix para Tor.
- Dom0 muy limitado (reduce riesgo de ataques).
- Gestión centralizada de seguridad.
- Puede ejecutar Windows en qubes si quieres.

✅ Limitaciones:

- Necesita hardware más potente (\~16 GB RAM recomendado).
- Solo soporta hardware compatible (UEFI, VT-d).
- Curva de aprendizaje más empinada.

✅ Ejemplo real:

> Un periodista usa Qubes OS con estos qubes:

- Personal (correo no sensible)
- Work (investigación)
- Whonix (navegación Tor)
- Untrusted (descargar y abrir documentos sospechosos)

---

### 🗂️ TABLA COMPARATIVA (RESUMEN)

| Característica      | Tails                           | Whonix                     | Qubes OS                         |
| ------------------- | ------------------------------- | -------------------------- | -------------------------------- |
| Tipo                | Live OS en USB                  | VM (Debian + Tor)          | OS Host con múltiples VM (qubes) |
| Uso principal       | Anonimato temporal              | Anonimato persistente      | Aislamiento extremo              |
| Almacenamiento      | Volátil (opcional persistencia) | Persistente (si se quiere) | Persistente en qubes separados   |
| Requisitos hardware | Muy bajos                       | Medios (\~4GB RAM)         | Altos (\~16GB RAM recomendado)   |
| Fácil de usar       | Muy fácil                       | Medio                      | Avanzado                         |
| Ejemplo ideal       | Cibercafé, viaje                | PC personal con VM         | PC personal de alto riesgo       |

---

### 🌟 CUÁL ELEGIR SEGÚN TUS NECESIDADES

✅ Usa **Tails** si:

- Quieres anonimato rápido y fácil.
- Usarás computadoras públicas.
- No necesitas guardar mucho.

✅ Usa **Whonix** si:

- Quieres anonimato más persistente.
- Trabajas siempre en la misma laptop o PC.
- Necesitas guardar configuraciones, claves, documentos.

✅ Usa **Qubes OS** si:

- Quieres el máximo aislamiento.
- Tienes hardware potente.
- Necesitas separar trabajo, vida personal, navegación anónima.

---

### ⚙️ INSTALACIÓN (GUÍA BÁSICA DE CADA UNO)

---

#### ✅ A. **INSTALAR TAILS**

✅ Ultra fácil:

1️⃣ Descarga la ISO oficial desde [https://tails.net](https://tails.net).

2️⃣ Grábala en un USB con **balenaEtcher**.

3️⃣ Arranca la computadora desde el USB.

4️⃣ ¡Listo! No se instala en disco.

✅ Ejemplo:

> Ana descarga Tails en su casa, lo graba en un USB. Viaja, arranca Tails en la laptop del hotel → navega por Tor.

---

#### ✅ B. **INSTALAR WHONIX**

✅ Requiere VirtualBox, KVM o Qubes OS.

✅ Pasos típicos:

1️⃣ Instala VirtualBox en Linux o Windows.

2️⃣ Descarga la imagen oficial Whonix (OVA) desde [https://www.whonix.org](https://www.whonix.org).

3️⃣ Importa la OVA en VirtualBox.

4️⃣ Inicia → se crean dos VMs: Gateway y Workstation.

5️⃣ Usa la Workstation → todo pasa por Tor.

✅ Ejemplo:

> Juan tiene Linux Mint. Instala VirtualBox → importa Whonix → abre la Workstation → navega por Tor con seguridad.

---

#### ✅ C. **INSTALAR QUBES OS**

✅ Es un sistema operativo completo → sustituye tu OS.

✅ Pasos típicos:

1️⃣ Verifica compatibilidad → [https://www.qubes-os.org/doc/system-requirements/](https://www.qubes-os.org/doc/system-requirements/).

2️⃣ Descarga la ISO desde [https://www.qubes-os.org](https://www.qubes-os.org).

3️⃣ Graba la ISO en un USB booteable (balenaEtcher, dd).

4️⃣ Arranca la computadora desde el USB.

5️⃣ Sigue el instalador (parecido a Fedora/RedHat).

6️⃣ Al iniciar, configuras qubes (Personal, Work, Whonix, Untrusted).

✅ Ejemplo:

> Laura tiene una laptop potente. Instala Qubes OS → tiene qubes separados → uno con Whonix para navegar anónimo, otro para trabajo normal.

---

### ✅ EJEMPLO MUY CLARO DE USO

✔️ **Tails:**

> Viajas y quieres usar Tor en un cibercafé → usas Tails en un USB → nada se guarda.

---

✔️ **Whonix:**

> En tu laptop personal → usas VirtualBox → Whonix Workstation para navegar por Tor → guardas contraseñas, llaves GPG.

---

✔️ **Qubes OS:**

> En tu PC potente → separas todo en qubes:

- Personal: correo personal
- Work: investigación
- Whonix: Tor
- Untrusted: abrir archivos sospechosos

---

### ✅ BUENAS PRÁCTICAS

✔️ Descargar siempre desde sitios oficiales.

✔️ Verificar firmas o hashes.

✔️ Usar contraseñas fuertes.

✔️ Mantener el software actualizado.

✔️ Nunca mezclar actividades personales y anónimas.

✔️ Evitar cuentas reales en Tor.

---

### ✅ MINI RESUMEN FINAL

✅ **Tails**: live USB → anonimato temporal → no deja rastros.

✅ **Whonix**: VM → anonimato persistente → para uso diario.

✅ **Qubes OS**: sistema completo → máxima seguridad → aislamiento por qubes.

---

[🔼](#índice)

---

| **Inicio**         | **atrás 5**             | **Siguiente 7**                        |
| ------------------ | ----------------------- | -------------------------------------- |
| [🏠](../README.md) | [⏪](./3_5_Qubes_OS.md) | [⏩](./3_7_Zero_Knowledge_Services.md) |
