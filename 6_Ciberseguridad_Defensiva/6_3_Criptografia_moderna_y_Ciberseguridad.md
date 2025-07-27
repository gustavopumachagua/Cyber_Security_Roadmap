| **Inicio**         | **atrás 2**                                               | **Siguiente 4**                                         |
| ------------------ | --------------------------------------------------------- | ------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./6_2_Criptografia_y_Ciberseguridad_Introduccion.md) | [⏩](./6_4_CiberSeguridad_de_los_datos_Data_Scurity.md) |

---

## **Índice**

| Temario                                                                                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [398. Criptosistemas simétricos modernos](#398-criptosistemas-simétricos-modernos)                                                                      |
| [399. Stream Ciphers](#399-stream-ciphers)                                                                                                              |
| [400. El tamaño del Keystream](#400-el-tamaño-del-keystream)                                                                                            |
| [401. Propiedades de los Stream Ciphers](#401-propiedades-de-los-stream-ciphers)                                                                        |
| [402. Stream Ciphers populares](#402-stream-ciphers-populares)                                                                                          |
| [403. RC4](#403-rc4)                                                                                                                                    |
| [404. RC4 en la práctica](#404-rc4-en-la-práctica)                                                                                                      |
| [405. Implementa RC4 en Python](#405-implementa-rc4-en-python)                                                                                          |
| [406. Ataques a RC4](#406-ataques-a-rc4)                                                                                                                |
| [407. ChaCha20](#407-chacha20)                                                                                                                          |
| [408. Funcionamiento de ChaCha20](#408-funcionamiento-de-chacha20)                                                                                      |
| [409. Caso Práctico: ChaCha20](#409-caso-práctico-chacha20)                                                                                             |
| [410. Block Ciphers](#410-block-ciphers)                                                                                                                |
| [411. Propiedades de los Block Ciphers](#411-propiedades-de-los-block-ciphers)                                                                          |
| [412. Block Ciphers populares](#412-block-ciphers-populares)                                                                                            |
| [413. DES (Data Encryption Standard)](#413-des-data-encryption-standard)                                                                                |
| [414. Detalles del funcionamiento de DES](#414-detalles-del-funcionamiento-de-des)                                                                      |
| [415. Ataques a DES](#415-ataques-a-des)                                                                                                                |
| [416. Triple DES](#416-triple-des)                                                                                                                      |
| [417. AES (Advanced Encryption Standard)](#417-aes-advanced-encryption-standard)                                                                        |
| [418. Detalles de las funciones de AES](#418-detalles-de-las-funciones-de-aes)                                                                          |
| [419. Caso práctico: AES](#419-caso-práctico-aes)                                                                                                       |
| [420. Initialization Vector (IV)](#420-initialization-vector-iv)                                                                                        |
| [421. Modos de operación: ECB](#421-modos-de-operación-ecb)                                                                                             |
| [422. Modos de operación: CBC](#422-modos-de-operación-cbc)                                                                                             |
| [423. Modos de operación: CFB](#423-modos-de-operación-cfb)                                                                                             |
| [424. Modos de operación: OFB](#424-modos-de-operación-ofb)                                                                                             |
| [425. Modos de operación: CTR](#425-modos-de-operación-ctr)                                                                                             |
| [426. Cuándo usar criptosistemas simétricos](#426-cuándo-usar-criptosistemas-simétricos)                                                                |
| [427. Criptosistemas asimétricos o de clave pública](#427-criptosistemas-asimétricos-o-de-clave-pública)                                                |
| [428. Diffie Hellman: Intercambio de claves](#428-diffie-hellman-intercambio-de-claves)                                                                 |
| [429. RSA](#429-rsa)                                                                                                                                    |
| [430. Generando un par de claves RSA con OpenSSL](#430-generando-un-par-de-claves-rsa-con-openssl)                                                      |
| [431. Curvas elípticas](#431-curvas-elípticas)                                                                                                          |
| [432. Computación cuántica: Un viaje hacia una nueva era en la criptografía](#432-computación-cuántica-un-viaje-hacia-una-nueva-era-en-la-criptografía) |

---

# **Criptografia moderna y Ciberseguridad**

## **398. Criptosistemas simétricos modernos**

### 🧠 ¿Qué es un Criptosistema Simétrico?

Un **criptosistema simétrico** es un sistema de cifrado donde **la misma clave se usa para cifrar y descifrar** la información.

#### 🔐 Características clave:

| Característica         | Descripción                                                    |
| ---------------------- | -------------------------------------------------------------- |
| Clave única compartida | El emisor y el receptor usan la **misma clave secreta**.       |
| Rápido                 | Son **muy eficientes** para cifrar grandes volúmenes de datos. |
| Seguro (si bien usado) | Ofrece buena seguridad si se protege la clave.                 |

---

### 🏛️ Ejemplos de criptosistemas simétricos modernos:

| Algoritmo      | Descripción breve                                      |
| -------------- | ------------------------------------------------------ |
| **AES**        | Estándar de cifrado avanzado. El más usado hoy en día. |
| **DES**        | Algoritmo más antiguo, ahora considerado inseguro.     |
| **Triple DES** | Variación de DES más segura.                           |
| **ChaCha20**   | Alternativa moderna a AES, muy usada en móviles y VPN. |
| **Blowfish**   | Algoritmo rápido, útil para contraseñas.               |

El más usado hoy en día es **AES (Advanced Encryption Standard)**, y es el que veremos en el ejemplo.

---

### 🧪 ¿Cómo funciona AES (por ejemplo)?

Imagina que quieres enviar el mensaje `"HOLA MUNDO"` y ambos tú y tu amigo tienen esta **clave secreta compartida**:

```
Clave: "clave_super_secreta123"
```

El algoritmo AES toma el mensaje, lo convierte en bloques binarios, los mezcla, los revuelve y los transforma en un texto ilegible (cifrado). Solo con la misma clave podrás devolverlo a su forma original (descifrado).

---

### 🔧 ¿Cómo se “instala” o se usa?

Usaremos **Python** con la librería `cryptography`, que es moderna, segura y fácil de usar.

#### 🔹 Paso 1: Instalar la librería

Abre la terminal o consola de comandos y escribe:

```bash
pip install cryptography
```

---

### 💻 Ejemplo completo de cifrado y descifrado con AES

Vamos a cifrar y descifrar el mensaje `"HOLA MUNDO"` usando AES con clave simétrica.

#### 📄 Código en Python:

```python
from cryptography.fernet import Fernet

# 1. Generamos una clave simétrica
clave = Fernet.generate_key()
cipher = Fernet(clave)

# 2. Mensaje original
mensaje = "HOLA MUNDO".encode()

# 3. Cifrado del mensaje
mensaje_cifrado = cipher.encrypt(mensaje)

# 4. Descifrado del mensaje
mensaje_descifrado = cipher.decrypt(mensaje_cifrado)

# 5. Mostrar resultados
print("Clave secreta:", clave.decode())
print("Mensaje original:", mensaje.decode())
print("Mensaje cifrado:", mensaje_cifrado.decode())
print("Mensaje descifrado:", mensaje_descifrado.decode())
```

#### 🧾 Posible salida:

```
Clave secreta: pJrfkUSuol6hxTIGfDnONrkwK9ArX4HeYTbNRITywh4=
Mensaje original: HOLA MUNDO
Mensaje cifrado: gAAAAABkgn7e9tUdcZK...
Mensaje descifrado: HOLA MUNDO
```

---

### 🛡️ Ventajas de los Criptosistemas Simétricos Modernos

- ✅ Muy rápidos
- ✅ Buenos para cifrar archivos, bases de datos, discos duros
- ✅ Usados en HTTPS, VPNs, Wi-Fi (WPA2/WPA3), backups, etc.

---

### ⚠️ Desventajas

- ❌ **Debes proteger muy bien la clave** (si alguien la obtiene, todo se puede descifrar).
- ❌ No sirven bien para sistemas de comunicación abiertos como correo sin una segunda capa (como criptografía asimétrica).

---

### 🧭 ¿Cuándo usar criptografía simétrica?

| Uso                                   | Recomendado                           |
| ------------------------------------- | ------------------------------------- |
| Cifrar archivos en tu disco duro      | ✅ Sí                                 |
| Cifrar base de datos o backups        | ✅ Sí                                 |
| Comunicación entre servidores seguros | ✅ Sí                                 |
| Enviar correos cifrados a extraños    | ❌ No (mejor usar cifrado asimétrico) |

---

### ✅ Conclusión rápida

| Pregunta               | Resumen breve                               |
| ---------------------- | ------------------------------------------- |
| ¿Qué es?               | Cifrado con una única clave compartida      |
| ¿Es seguro?            | Sí, si proteges la clave                    |
| ¿Qué algoritmo se usa? | AES, ChaCha20, Triple DES, Blowfish, etc.   |
| ¿Cómo lo uso?          | Con librerías como `cryptography` en Python |

---

[🔼](#índice)

---

## **399. Stream Ciphers**

### 🔐 ¿Qué es un Stream Cipher?

Un **stream cipher** o **cifrador de flujo** es un tipo de algoritmo criptográfico **simétrico** que **cifra los datos bit por bit o byte por byte**, usando una clave y un generador de flujo.

🔁 A diferencia de los **block ciphers** (como AES), que cifran los datos en bloques (por ejemplo, de 128 bits), los **stream ciphers** trabajan con datos que van llegando poco a poco, como si fuese una transmisión en tiempo real.

---

#### 🧠 ¿Cómo funciona?

1. Se tiene una **clave secreta** (key).
2. Se genera un flujo de bits pseudoaleatorio (keystream).
3. El flujo de bits se combina con el mensaje original (texto claro) usando una operación como **XOR** (exclusiva o).
4. Se obtiene un texto cifrado.
5. Para descifrar, se aplica el mismo keystream al texto cifrado con XOR y se recupera el mensaje original.

---

### 📦 Ejemplo fácil

#### Supón este mensaje:

```
Mensaje: 10110001
Keystream: 11001100
```

Aplicamos XOR (⊕):

```
Texto cifrado: 01111101
```

Para descifrarlo:

```
01111101 ⊕ 11001100 = 10110001  → ¡recuperamos el mensaje original!
```

---

### 🧰 Ejemplos conocidos de stream ciphers

| Algoritmo    | Uso común                                             |
| ------------ | ----------------------------------------------------- |
| **RC4**      | Usado antiguamente en SSL/TLS y Wi-Fi (ya no seguro). |
| **ChaCha20** | Reemplazo moderno, rápido y seguro.                   |
| **Salsa20**  | Similar a ChaCha20, también muy seguro.               |

---

### 📌 ¿Cuándo usar un Stream Cipher?

- Cuando se necesita **cifrar en tiempo real** (como llamadas, video, o streaming).
- Cuando los datos **no tienen tamaño fijo**.
- En aplicaciones con pocos recursos (IoT, móviles).

---

### ⚙️ ¿Cómo se instala?

Usaremos **Python** con la librería `cryptography`, que soporta **ChaCha20**, un stream cipher moderno y seguro.

#### 🧪 Instalación

Abre la terminal y escribe:

```bash
pip install cryptography
```

---

### 💻 Ejemplo completo: ChaCha20 en Python

Vamos a cifrar y descifrar un mensaje con un stream cipher moderno.

#### 📄 Código:

```python
from cryptography.hazmat.primitives.ciphers import Cipher, algorithms
from cryptography.hazmat.backends import default_backend
import os

# 1. Crear clave de 32 bytes y un nonce (único por mensaje)
clave = os.urandom(32)
nonce = os.urandom(16)

# 2. Crear el cifrador ChaCha20
algorithm = algorithms.ChaCha20(clave, nonce)
cipher = Cipher(algorithm, mode=None, backend=default_backend())
encryptor = cipher.encryptor()

# 3. Mensaje original
mensaje = b"Hola mundo desde stream cipher!"

# 4. Cifrar
cifrado = encryptor.update(mensaje)

# 5. Descifrar (usar misma clave y nonce)
decryptor = cipher.decryptor()
descifrado = decryptor.update(cifrado)

# 6. Mostrar resultados
print("Clave:", clave.hex())
print("Nonce:", nonce.hex())
print("Mensaje original:", mensaje.decode())
print("Mensaje cifrado:", cifrado.hex())
print("Mensaje descifrado:", descifrado.decode())
```

---

#### 📌 Resultado esperado (ejemplo):

```
Clave: d09f...7b
Nonce: 918f...1d
Mensaje original: Hola mundo desde stream cipher!
Mensaje cifrado: 69a12f...
Mensaje descifrado: Hola mundo desde stream cipher!
```

---

### ✅ Ventajas de los stream ciphers

- 🔄 Buen rendimiento para flujos continuos de datos.
- ⚡ Más rápidos que muchos block ciphers en algunos contextos.
- 🔐 Bien diseñados (como ChaCha20) son muy seguros.

---

### ⚠️ Desventajas

- ❌ Si se reutiliza la clave y el nonce → el sistema se rompe.
- ❌ RC4 ya **no es seguro** (no usar).

---

### 🧭 Cuadro comparativo: Stream vs Block Cipher

| Característica                      | Stream Cipher | Block Cipher        |
| ----------------------------------- | ------------- | ------------------- |
| Cifra bit/byte a bit                | ✅ Sí         | ❌ No (usa bloques) |
| Cifra en tiempo real                | ✅ Ideal      | ❌ Menos eficiente  |
| Vulnerable a reutilización de clave | ✅ Sí         | ✅ También          |
| Ejemplo moderno                     | ChaCha20      | AES                 |

---

### 🎯 Conclusión

- Los stream ciphers son ideales para comunicaciones en **tiempo real** o **datos de tamaño variable**.
- El uso de algoritmos modernos como **ChaCha20** es recomendable.
- No reutilices la clave y nonce: eso rompe la seguridad.
- Puedes usarlos fácilmente en Python con `cryptography`.

---

[🔼](#índice)

---

## **400. El tamaño del Keystream**

### 🔐 ¿Qué es el Keystream?

El **keystream** es un flujo de bits (o bytes) pseudoaleatorio que se **genera a partir de una clave secreta**, y que se **combina con el texto original** (plaintext) para obtener un texto cifrado (ciphertext) en un cifrado de flujo (stream cipher).

Se suele usar una operación XOR (`⊕`) entre el texto original y el keystream:

```
Texto cifrado = Texto original ⊕ Keystream
```

---

### 📏 ¿Qué significa "tamaño del Keystream"?

El **tamaño del keystream** es la **longitud** (en bits o bytes) del flujo generado por el algoritmo criptográfico para cifrar un mensaje.

🔑 **Regla importante:**

> 📌 **El tamaño del keystream debe ser igual o mayor al tamaño del mensaje.**

Porque si el keystream es más corto, **no puedes cifrar todo el mensaje**.

---

### 🎓 Ejemplo simple paso a paso

Supón este mensaje (en binario):

```
Mensaje:   10101100 (8 bits)
Keystream: 11010110 (8 bits)
```

Aplicamos XOR bit a bit:

```
Cifrado:   01111010
```

🔁 Para descifrar, hacemos lo mismo:

```
Cifrado:   01111010
Keystream: 11010110
Original:  10101100
```

✅ ¡Recuperamos el mensaje original!

---

### ⚠️ ¿Qué pasa si el keystream es **más corto**?

Ejemplo:

```
Mensaje:   10101100 01010101 (16 bits)
Keystream: 11010110          (8 bits solamente) ❌
```

⛔ Solo puedes cifrar la **primera mitad** del mensaje. El resto no se puede cifrar, o deberías repetir la clave (lo cual **no es seguro**).

---

### 🎯 ¿Por qué es importante?

Un cifrado de flujo seguro (como el **One-Time Pad**) **nunca debe reutilizar la clave ni el keystream**.

**El tamaño del keystream afecta la seguridad:**

- Si es más corto → no puedes cifrar todo.
- Si lo repites → pierdes seguridad (puede romperse por ataques estadísticos).

---

### ✅ Buenas prácticas:

1. 🔑 Asegúrate de que el tamaño del keystream sea **al menos igual** al tamaño del mensaje.
2. 🔄 No reutilices el mismo keystream (especialmente con one-time pad).
3. 📏 Si el mensaje cambia de longitud, genera un nuevo keystream.

---

### 🧰 ¿Cómo se genera un keystream?

El keystream se genera a partir de:

- Una **clave secreta** (`key`)
- Un **nonce** o número único para cada mensaje

El algoritmo genera un flujo pseudoaleatorio usando esos valores.

---

### 💻 Ejemplo completo en Python usando `ChaCha20` (stream cipher moderno)

#### ✅ Requisitos

```bash
pip install cryptography
```

---

#### 🧑‍💻 Código paso a paso:

```python
from cryptography.hazmat.primitives.ciphers import Cipher, algorithms
from cryptography.hazmat.backends import default_backend
import os

# 1. Generar una clave de 32 bytes y un nonce de 16 bytes
key = os.urandom(32)
nonce = os.urandom(16)

# 2. Crear algoritmo ChaCha20 (stream cipher)
algorithm = algorithms.ChaCha20(key, nonce)
cipher = Cipher(algorithm, mode=None, backend=default_backend())

# 3. Crear cifrador y descifrador
encryptor = cipher.encryptor()
decryptor = cipher.decryptor()

# 4. Mensaje original
mensaje = b"Hola desde el keystream!"

# 5. Cifrar (esto genera un keystream del mismo tamaño que el mensaje)
cifrado = encryptor.update(mensaje)

# 6. Descifrar (mismo keystream se usa para recuperar el mensaje)
descifrado = decryptor.update(cifrado)

# 7. Mostrar resultados
print("Mensaje original:", mensaje.decode())
print("Texto cifrado (hex):", cifrado.hex())
print("Mensaje descifrado:", descifrado.decode())
```

---

#### 🧪 Resultado esperado:

```
Mensaje original: Hola desde el keystream!
Texto cifrado (hex): a75f79f...
Mensaje descifrado: Hola desde el keystream!
```

---

### 📌 Conclusión

- El **tamaño del keystream** debe **igualar o superar** al tamaño del mensaje.
- Si el keystream es **muy corto**, **no se puede cifrar todo el mensaje**.
- En cifradores como **ChaCha20**, el keystream se genera automáticamente y del tamaño correcto según el mensaje.
- **Nunca reutilices el keystream** con diferentes mensajes (es un gran error de seguridad).

---

[🔼](#índice)

---

## **401. Propiedades de los Stream Ciphers**

### 🔐 ¿Qué es un Stream Cipher?

Un **Stream Cipher** (cifrador de flujo) es un tipo de algoritmo de cifrado **simétrico** que **cifra los datos bit a bit o byte a byte**, utilizando un flujo de claves pseudoaleatorias llamadas **keystream**.

Se diferencia de un **Block Cipher** (cifrador por bloques), que cifra los datos por bloques completos (por ejemplo, de 128 bits).

---

### ✅ Propiedades clave de los Stream Ciphers

#### 🔄 **Cifrado en tiempo real (bit a bit o byte a byte)**

- Cifran y descifran los datos **uno por uno**.
- Ideal para transmisión de datos en tiempo real: voz, video, streaming.

📌 **Ejemplo:** mientras alguien te está enviando un mensaje por voz cifrada, cada byte se cifra al momento que se envía.

---

#### 🔑 **Uso de un Keystream (flujo de claves)**

- Se genera un **flujo de bits pseudoaleatorio** usando una clave secreta.
- El keystream se **combina con el mensaje original** usando una operación XOR.

📌 **Ejemplo:**

```
Mensaje original:  11001010
Keystream:         10101010
Cifrado:           01100000  ← Resultado de XOR
```

---

#### 🔁 **Determinismo**

- Dado el mismo mensaje, clave y nonce, el resultado **siempre será el mismo**.
- Pero si cambias solo el nonce o la clave, el resultado cambia totalmente.

---

#### 🧠 **Alta eficiencia**

- Rápidos y requieren **menos recursos computacionales** que block ciphers.
- Muy usados en dispositivos con recursos limitados (como IoT, radios, tarjetas SIM).

---

#### 🧷 **Sensibles al orden y sincronización**

- Si se pierde un bit durante la transmisión, todo el mensaje posterior puede quedar corrupto.
- Ambos extremos deben estar sincronizados en el flujo de claves.

---

#### 🔐 **No deben reutilizar el mismo keystream**

- Si se usa el mismo keystream para dos mensajes, un atacante puede recuperar información.

📌 Ejemplo de mal uso (muy importante):

```plaintext
Mensaje1 ⊕ Keystream = Cifrado1
Mensaje2 ⊕ Keystream = Cifrado2

→ Cifrado1 ⊕ Cifrado2 = Mensaje1 ⊕ Mensaje2
```

Esto da **información directa sobre ambos mensajes**.

---

#### 📏 **No necesitan padding**

- Como no cifran por bloques, **no es necesario rellenar** el mensaje para que encaje.
- Esto simplifica el diseño.

---

#### 🧩 **Puede usarse con modos de operación como CTR o OFB**

Aunque hay stream ciphers dedicados (como RC4, ChaCha20), también puedes simular un flujo de claves usando un bloque cifrado en modo **CTR** o **OFB**, que lo convierten en una especie de stream cipher.

---

### 🔧 ¿Cómo se “instala” o implementa un stream cipher?

Como no se instala como un programa, lo que realmente haces es **usar una biblioteca de cifrado** (como `cryptography` en Python o `Crypto` en Node.js).

---

### 🧑‍💻 Ejemplo completo: Usando ChaCha20 (Stream Cipher moderno) en Python

#### ✅ Requisitos:

```bash
pip install cryptography
```

---

#### 📦 Código paso a paso:

```python
from cryptography.hazmat.primitives.ciphers import Cipher, algorithms
from cryptography.hazmat.backends import default_backend
import os

# 1. Crear clave (32 bytes para ChaCha20)
clave = os.urandom(32)

# 2. Crear nonce (número de uso único, 16 bytes)
nonce = os.urandom(16)

# 3. Crear cifrador de flujo ChaCha20
algoritmo = algorithms.ChaCha20(clave, nonce)
cifrador = Cipher(algoritmo, mode=None, backend=default_backend())

# 4. Crear objeto para cifrar y descifrar
encryptor = cifrador.encryptor()
decryptor = cifrador.decryptor()

# 5. Mensaje original
mensaje = b"Hola mundo desde stream cipher!"

# 6. Cifrar el mensaje
cifrado = encryptor.update(mensaje)

# 7. Descifrar el mensaje
descifrado = decryptor.update(cifrado)

# 8. Mostrar resultados
print("Mensaje original:", mensaje.decode())
print("Cifrado (hex):", cifrado.hex())
print("Mensaje descifrado:", descifrado.decode())
```

---

#### 🧪 Resultado esperado:

```
Mensaje original: Hola mundo desde stream cipher!
Cifrado (hex): 45bfa2...
Mensaje descifrado: Hola mundo desde stream cipher!
```

---

### 🧠 Conclusión

**Propiedades importantes de los Stream Ciphers**:

| Propiedad               | Descripción breve                                 |
| ----------------------- | ------------------------------------------------- |
| Bit a bit / byte a byte | Ideal para tiempo real                            |
| Keystream               | Generado desde una clave, no debe repetirse       |
| Rápidos                 | Eficientes, ideal para dispositivos pequeños      |
| Sin padding             | No necesitas rellenar bloques                     |
| Sensibles al orden      | Un bit perdido arruina el resto                   |
| No reutilizar keystream | Rompe la seguridad                                |
| Simples de implementar  | Muy directos en librerías criptográficas modernas |

---

[🔼](#índice)

---

## **402. Stream Ciphers populares**

### 🧠 ¿Qué son los Stream Ciphers?

Un **Stream Cipher** es un tipo de cifrado simétrico que **cifra los datos bit a bit o byte a byte**, usando una secuencia pseudoaleatoria llamada **keystream**.

Cada bit del texto original se combina con un bit del keystream, normalmente mediante la operación XOR.

---

### ⭐ Stream Ciphers más populares

Aquí tienes algunos de los stream ciphers más conocidos y utilizados en la práctica:

---

#### 🔒 **RC4 (Rivest Cipher 4)**

- Fue ampliamente usado en SSL/TLS, WEP y WPA.
- Es rápido y fácil de implementar.
- **Actualmente está obsoleto** por vulnerabilidades críticas (filtraciones de bytes del keystream).
- Ejemplo de ataque: si se reutiliza la clave, es muy fácil romperlo.

📌 **Uso típico (histórico):** navegación web segura, Wi-Fi (WEP).

---

#### 🔒 **ChaCha20**

- Diseñado por Daniel J. Bernstein.
- Mucho más seguro que RC4.
- **Muy rápido**, resistente a ataques y confiable.
- Usado por **Google, WhatsApp, WireGuard, OpenSSH, TLS 1.3**.
- No usa tablas S-box como RC4 → más seguro contra ataques de canal lateral (como timing attacks).

📌 **Clave:** 256 bits (32 bytes)

📌 **Nonce:** 96 bits o 128 bits (según implementación)

---

#### 🔒 **Salsa20**

- Antecesor de ChaCha20, también creado por Bernstein.
- Más simple, eficiente y también seguro.
- Ya no se usa tanto como ChaCha20, pero sigue siendo confiable.

---

#### 🔒 **Grain y Trivium**

- Son **stream ciphers diseñados para hardware** y dispositivos de baja potencia (como IoT).
- Son parte del proyecto **eSTREAM**.
- No se usan tanto en software general, pero sí en criptografía embebida.

---

#### 🔄 **AES en modo CTR (Counter Mode)**

Aunque AES es un **block cipher**, si lo usas en **modo CTR (Counter)** se comporta como un stream cipher:

- Genera un keystream cifrando un contador que va aumentando.
- Muy seguro y ampliamente adoptado.

📌 Se usa en muchas aplicaciones modernas para obtener los beneficios de los stream ciphers sin dejar de usar AES.

---

### 🛠️ ¿Cómo se "instalan" los stream ciphers?

No se instalan como programas normales. Para usarlos, necesitas una biblioteca criptográfica en tu lenguaje favorito. Aquí tienes algunos ejemplos:

| Lenguaje | Biblioteca popular             |
| -------- | ------------------------------ |
| Python   | `cryptography`                 |
| Node.js  | `crypto`                       |
| Java     | `javax.crypto`                 |
| C        | OpenSSL                        |
| C#       | `System.Security.Cryptography` |

---

### 🧪 Ejemplo completo: Usando **ChaCha20** en Python

#### 🔧 Requisitos

Asegúrate de instalar la librería:

```bash
pip install cryptography
```

---

#### ✅ Código completo

```python
from cryptography.hazmat.primitives.ciphers import Cipher, algorithms
from cryptography.hazmat.backends import default_backend
import os

# 1. Crear clave y nonce
clave = os.urandom(32)     # 256 bits para ChaCha20
nonce = os.urandom(16)     # 128 bits

# 2. Crear el objeto de cifrado
algoritmo = algorithms.ChaCha20(clave, nonce)
cifrador = Cipher(algoritmo, mode=None, backend=default_backend())

# 3. Crear el encryptor y decryptor
encryptor = cifrador.encryptor()
decryptor = cifrador.decryptor()

# 4. Mensaje original
mensaje = b"Hola, este es un mensaje cifrado con ChaCha20!"

# 5. Cifrar el mensaje
cifrado = encryptor.update(mensaje)

# 6. Descifrar el mensaje
descifrado = decryptor.update(cifrado)

# 7. Mostrar resultados
print("Mensaje original:", mensaje.decode())
print("Mensaje cifrado (hex):", cifrado.hex())
print("Mensaje descifrado:", descifrado.decode())
```

---

#### 🧾 Resultado esperado (salida):

```plaintext
Mensaje original: Hola, este es un mensaje cifrado con ChaCha20!
Mensaje cifrado (hex): 7f43c3e21d... (una secuencia hexadecimal)
Mensaje descifrado: Hola, este es un mensaje cifrado con ChaCha20!
```

---

### 🧠 Conclusión

| Cifrador      | Estado      | Uso común                    | Seguridad |
| ------------- | ----------- | ---------------------------- | --------- |
| RC4           | Obsoleto ❌ | WEP, TLS                     | Inseguro  |
| ChaCha20      | Actual ✅   | TLS 1.3, WhatsApp, WireGuard | Muy alta  |
| Salsa20       | Vigente ✅  | Alternativa simple a ChaCha  | Alta      |
| AES-CTR       | Actual ✅   | Cifrado moderno              | Muy alta  |
| Grain/Trivium | Niche ✅    | IoT, hardware embebido       | Alta      |

---

[🔼](#índice)

---

## **403. RC4**

### 🔐 ¿Qué es RC4?

**RC4** (Rivest Cipher 4) es un algoritmo de cifrado simétrico de flujo, diseñado por **Ron Rivest** en 1987. Es famoso por su **simplicidad, velocidad y facilidad de implementación**. Por muchos años fue usado en protocolos como **SSL/TLS** y en **WEP/WPA** (seguridad Wi-Fi).

> 📛 **Importante:** Hoy en día **RC4 está considerado inseguro** y **obsoleto**, debido a varias vulnerabilidades descubiertas, especialmente si se reutiliza la clave.

---

### 📌 Características de RC4

- Es un **stream cipher**, cifra los datos **byte por byte**.
- Usa una **clave variable** entre 40 y 2048 bits (generalmente 128 bits).
- Usa una estructura interna llamada **S-box** (una permutación de 256 bytes).
- La operación principal es el XOR entre el texto plano y el keystream.

---

### ⚙️ ¿Cómo funciona RC4?

RC4 tiene **dos fases** principales:

1. **Key Scheduling Algorithm (KSA)**

   Inicializa y mezcla la tabla S (permuta los valores del 0 al 255 en base a la clave).

2. **Pseudo-Random Generation Algorithm (PRGA)**

   Genera un keystream pseudoaleatorio que se combina con el texto plano usando XOR.

---

### 👨‍🏫 Ejemplo simple paso a paso

Supón que tienes el mensaje:

```
Texto plano:  HOLA
Clave:         KEY
```

El keystream generado será una secuencia de bytes pseudoaleatorios, por ejemplo: `0x5A, 0x1F, 0x33, 0x9C`.

El texto cifrado se obtiene así:

```
'H' (0x48) XOR 0x5A → 0x12
'O' (0x4F) XOR 0x1F → 0x50
'L' (0x4C) XOR 0x33 → 0x7F
'A' (0x41) XOR 0x9C → 0xDD
```

Texto cifrado en hexadecimal: `12 50 7F DD`

Para **descifrar**, simplemente vuelves a aplicar XOR con el mismo keystream.

---

### 📦 Instalación y uso de RC4 en Python

Aunque RC4 está en desuso, puedes usarlo para **fines educativos** con bibliotecas como `PyCryptodome`.

#### 🔧 Paso 1: Instalar PyCryptodome

```bash
pip install pycryptodome
```

---

### ✅ Ejemplo completo en Python

```python
from Crypto.Cipher import ARC4
from Crypto.Random import get_random_bytes

# 1. Crear clave (16 bytes)
clave = get_random_bytes(16)

# 2. Crear el cifrador RC4
cipher = ARC4.new(clave)

# 3. Texto original
mensaje = b"Hola, este es un mensaje usando RC4."

# 4. Cifrar
cifrado = cipher.encrypt(mensaje)

# 5. Para descifrar, crear un nuevo cifrador con la misma clave
cipher2 = ARC4.new(clave)
descifrado = cipher2.decrypt(cifrado)

# 6. Resultados
print("Mensaje original:", mensaje.decode())
print("Mensaje cifrado (hex):", cifrado.hex())
print("Mensaje descifrado:", descifrado.decode())
```

---

### 🔍 Salida esperada

```plaintext
Mensaje original: Hola, este es un mensaje usando RC4.
Mensaje cifrado (hex): b4a7d2f09f...
Mensaje descifrado: Hola, este es un mensaje usando RC4.
```

---

### 🚫 Vulnerabilidades conocidas de RC4

1. **Sesgo en los primeros bytes** del keystream.
2. **Ataques al primer byte** (usado en WEP para romper claves).
3. **Predecibilidad** del keystream si la clave se reutiliza.

🔐 Hoy en día, **ChaCha20 o AES-CTR** son usados como reemplazo seguro de RC4.

---

### 🧠 Conclusión

| Ventajas de RC4               | Desventajas de RC4                               |
| ----------------------------- | ------------------------------------------------ |
| Rápido y fácil de implementar | Inseguro, especialmente si se reutiliza la clave |
| Usado históricamente en TLS   | Sesgos en el keystream                           |
| No necesita relleno (padding) | No cumple con estándares modernos                |

---

[🔼](#índice)

---

## **404. RC4 en la práctica**

### 🔐 ¿Qué es RC4 en la práctica?

**RC4** (Rivest Cipher 4) es un algoritmo de cifrado por flujo **simétrico**, lo que significa que **usa la misma clave para cifrar y descifrar**. A pesar de estar **obsoleto** para usos reales (por inseguro), **es útil para aprender** cómo funcionan los cifrados de flujo y para practicar criptografía básica.

En la práctica, RC4:

- Se implementa fácilmente con unas pocas líneas de código.
- Se usa para cifrar texto o archivos pequeños.
- Su clave puede ser corta (por ejemplo, 16 bytes).
- Es vulnerable si reutilizas la clave o no descartas los primeros bytes del keystream.

---

### 🧠 ¿Cómo funciona RC4?

1. **Generación de estado interno (S-box)** con 256 valores (0-255).
2. **Mezcla (Key Scheduling Algorithm – KSA)** usando la clave.
3. **Generación de keystream (PRGA)**: RC4 genera un flujo de bytes pseudoaleatorios.
4. **Cifrado/Descifrado**: El texto plano se combina con el keystream usando XOR.

> 🔁 En la práctica, cifrar y descifrar son la **misma operación XOR**.

---

### 💻 ¿Cómo se instala RC4 para probarlo?

La forma más sencilla es usando **Python** con la biblioteca `PyCryptodome`.

#### 🔧 Instalación paso a paso

1. Abre tu terminal o CMD
2. Escribe este comando:

```bash
pip install pycryptodome
```

> Esta librería contiene muchas herramientas criptográficas, incluyendo RC4 (llamado `ARC4` aquí por temas de derechos de autor).

---

### ✅ Ejemplo práctico completo: cifrado y descifrado RC4

#### ✏️ Código en Python

```python
from Crypto.Cipher import ARC4
from Crypto.Random import get_random_bytes

# Paso 1: Crear una clave aleatoria (de 16 bytes)
clave = get_random_bytes(16)

# Paso 2: Crear el cifrador con la clave
cifrador = ARC4.new(clave)

# Paso 3: Texto a cifrar
mensaje = b"Este es un mensaje secreto con RC4."

# Paso 4: Cifrar el mensaje
mensaje_cifrado = cifrador.encrypt(mensaje)

# Paso 5: Para descifrar, se debe reiniciar el cifrador con la misma clave
descifrador = ARC4.new(clave)
mensaje_descifrado = descifrador.decrypt(mensaje_cifrado)

# Paso 6: Mostrar resultados
print("Texto original:", mensaje.decode())
print("Texto cifrado (hex):", mensaje_cifrado.hex())
print("Texto descifrado:", mensaje_descifrado.decode())
```

---

#### 📥 Salida esperada

```plaintext
Texto original: Este es un mensaje secreto con RC4.
Texto cifrado (hex): 9a4f88aaffb3...
Texto descifrado: Este es un mensaje secreto con RC4.
```

---

### 🎯 Explicación línea por línea

| Línea de código            | Explicación                                                 |
| -------------------------- | ----------------------------------------------------------- |
| `get_random_bytes(16)`     | Genera una clave de 16 bytes aleatorios                     |
| `ARC4.new(clave)`          | Crea una instancia del cifrador RC4 con la clave            |
| `encrypt(mensaje)`         | Cifra el mensaje con el keystream generado                  |
| `decrypt(mensaje_cifrado)` | Descifra el mensaje aplicando XOR otra vez con el keystream |
| `.hex()`                   | Convierte bytes cifrados a hexadecimal para visualizar      |

---

### 🚫 ¿Por qué no se recomienda RC4 en sistemas modernos?

RC4 es fácil de implementar, pero:

- Tiene **sesgos estadísticos** en el keystream.
- Se puede **romper fácilmente** si no descartas los primeros bytes.
- Fue explotado en **ataques a WEP** y **TLS con RC4**.

Por eso hoy se prefieren algoritmos como:

- **AES en modo CTR**
- **ChaCha20**

---

### 📚 Resumen

| Concepto              | Detalle                                 |
| --------------------- | --------------------------------------- |
| Tipo de cifrado       | Simétrico, por flujo                    |
| Seguridad actual      | Débil, no recomendado para producción   |
| Usos educativos       | Excelente para aprender XOR y keystream |
| Clave                 | Secreta, entre 40 y 2048 bits           |
| Instalación en Python | `pip install pycryptodome`              |
| Biblioteca usada      | `Crypto.Cipher.ARC4`                    |

---

### 🧪 ¿Qué puedes hacer ahora?

Aquí tienes algunas ideas para practicar con RC4:

1. Cifrar y descifrar archivos de texto.
2. Implementar RC4 desde cero en Python (sin librerías).
3. Comparar RC4 con AES o ChaCha20.
4. Simular un ataque por reutilización de clave.

---

[🔼](#índice)

---

## **405. Implementa RC4 en Python**

### 🔐 ¿Qué es RC4?

**RC4** es un algoritmo de cifrado **simétrico por flujo** que genera un **keystream** (flujo de claves pseudoaleatorias) que luego se **combina mediante XOR con el texto original** para cifrarlo o descifrarlo.

---

### 📌 Conceptos clave de RC4

#### **Key Scheduling Algorithm (KSA):**

- Inicializa una lista `S` con valores del 0 al 255.
- Mezcla `S` usando la clave.

#### **Pseudo-Random Generation Algorithm (PRGA):**

- Usa `S` para generar una secuencia pseudoaleatoria de bytes (keystream).
- El keystream se usa para cifrar o descifrar usando **XOR**.

---

### 🧠 ¿Cómo funciona?

1. **Prepara una clave** (por ejemplo, `"clave123"`).
2. Inicializa un array `S` con los números del 0 al 255.
3. Aplica el **KSA** con esa clave para mezclar `S`.
4. Ejecuta el **PRGA** para generar el keystream.
5. Aplica **XOR** entre cada byte del texto y el keystream para cifrar/descifrar.

---

### 💻 Instalación

👉 No necesitas instalar nada. Solo necesitas **Python instalado en tu sistema** (puede ser Python 3.7 o superior).

Para verificar si lo tienes:

```bash
python --version
```

---

### ✅ Implementación completa en Python (desde cero)

```python
def KSA(key):
    """Key Scheduling Algorithm: mezcla la lista S con la clave."""
    key_length = len(key)
    S = list(range(256))
    j = 0
    for i in range(256):
        j = (j + S[i] + key[i % key_length]) % 256
        S[i], S[j] = S[j], S[i]  # intercambio
    return S

def PRGA(S):
    """Pseudo-Random Generation Algorithm: genera el keystream."""
    i = 0
    j = 0
    while True:
        i = (i + 1) % 256
        j = (j + S[i]) % 256
        S[i], S[j] = S[j], S[i]  # intercambio
        K = S[(S[i] + S[j]) % 256]
        yield K

def RC4(key, data):
    """Cifra o descifra el texto usando RC4."""
    key = [ord(c) for c in key]  # convierte la clave en lista de enteros
    S = KSA(key)
    keystream = PRGA(S)
    result = bytes([c ^ next(keystream) for c in data])
    return result
```

---

### 🧪 Ejemplo completo de uso

```python
# Texto original y clave
clave = "clave123"
texto = "Hola, mundo secreto"

# Cifrado
texto_bytes = texto.encode()
cifrado = RC4(clave, texto_bytes)
print("Texto cifrado (hex):", cifrado.hex())

# Descifrado
descifrado = RC4(clave, cifrado)
print("Texto descifrado:", descifrado.decode())
```

#### 🧾 Salida esperada:

```bash
Texto cifrado (hex): 2d7be90b9a4d5f...
Texto descifrado: Hola, mundo secreto
```

---

### 🧠 ¿Qué debes recordar?

| Concepto         | Explicación breve                                     |
| ---------------- | ----------------------------------------------------- |
| XOR              | Es reversible: `C = M ⊕ K`, luego `M = C ⊕ K`         |
| Simetría         | Se usa la misma clave para cifrar y descifrar         |
| Keystream        | Flujo pseudoaleatorio generado desde `S`              |
| Clave            | Puede ser cualquier texto (ideal: >= 8 caracteres)    |
| Seguridad actual | RC4 ya **no es seguro para uso real**, solo educativo |

---

[🔼](#índice)

---

## **406. Ataques a RC4**

### 🔐 ¿Qué es RC4?

RC4 es un **algoritmo de cifrado de flujo simétrico** muy rápido, creado en 1987 por Ron Rivest. Durante años fue ampliamente usado en protocolos como:

- SSL/TLS (para cifrado web)
- WEP y WPA (en redes Wi-Fi)
- Microsoft Office y PDF antiguos

Pero con el tiempo se descubrieron **varias debilidades**, lo que lo hace **inseguro hoy en día**.

---

### ⚠️ ¿Por qué RC4 es vulnerable?

#### Vulnerabilidades clave:

| Tipo de ataque                       | Explicación breve                                                                                             |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------- |
| **Sesgo del keystream**              | Algunos bytes al inicio del keystream no son completamente aleatorios.                                        |
| **Bias en pares de bytes**           | Algunos pares de bytes se repiten más que otros, lo cual puede usarse para deducir la clave o el texto plano. |
| **Ataques sobre WEP/WPA**            | Se reutilizan claves o IVs (vectores de inicialización), lo cual facilita ataques.                            |
| **Ataques de recuperación de clave** | En protocolos mal implementados, como WEP, es posible recuperar la clave compartida.                          |

---

### 🔎 Ejemplos de ataques a RC4

#### 1. 🔁 **Reutilización de keystreams (clave+IV repetido)**

- **Regla de oro del cifrado por flujo**: Nunca reutilices el keystream.
- Si cifras dos mensajes con el mismo keystream:

```text
Mensaje 1: M1 = "hola mundo"
Mensaje 2: M2 = "clave secreta"
Cifrado1 = M1 ⊕ K
Cifrado2 = M2 ⊕ K

Entonces:
Cifrado1 ⊕ Cifrado2 = M1 ⊕ K ⊕ M2 ⊕ K = M1 ⊕ M2
```

Y si se conoce M1, se puede recuperar M2 (y viceversa).

---

#### 2. 📊 **Ataques de análisis estadístico**

RC4 tiene **sesgos**: ciertos valores del keystream ocurren **con más frecuencia** de lo que deberían.

Ejemplo:

- El segundo byte del keystream tiende a ser `0x00` más seguido que cualquier otro valor.
- Los atacantes pueden analizar muchos mensajes cifrados con RC4 y deducir partes del texto o de la clave.

---

#### 3. 🧰 Ataques reales: BEAST, Lucky13, RC4 NOMORE

RC4 fue **deshabilitado oficialmente en TLS** (seguridad web) porque:

- Ataques como **RC4 NOMORE** (2015) demostraron que RC4 es vulnerable incluso si se usa correctamente.
- Analizando millones de mensajes cifrados, se podía recuperar texto plano (como cookies o contraseñas).

---

### 🛠️ ¿Cómo “instalar” un entorno para probar ataques?

Puedes simular un entorno vulnerable para pruebas educativas con:

#### 🔧 Requisitos:

- Python instalado
- Un editor como VSCode o Jupyter Notebook

#### 🐍 Instala `pycryptodome` (opcional, para comparar con cifrados modernos):

```bash
pip install pycryptodome
```

---

### 🧪 Ejemplo completo: Mostrar debilidad al reutilizar keystream

```python
def xor_bytes(a, b):
    return bytes([x ^ y for x, y in zip(a, b)])

def ejemplo_ataque_rc4():
    # Keystream fijo (mismo para ambos mensajes)
    keystream = b'\x1f\x2a\x3b\x4c\x5d\x6e\x7f\x80\x91\xa2'

    # Mensaje original
    mensaje1 = b'Hola Mundo'
    mensaje2 = b'Secreto123'

    # Cifrado (simulación)
    cifrado1 = xor_bytes(mensaje1, keystream)
    cifrado2 = xor_bytes(mensaje2, keystream)

    # Ataque: si el atacante tiene ambos cifrados:
    xor_cifrados = xor_bytes(cifrado1, cifrado2)

    print("Cifrado1:", cifrado1.hex())
    print("Cifrado2:", cifrado2.hex())
    print("XOR de ambos:", xor_cifrados)

    # Si el atacante conoce uno de los textos:
    mensaje2_reconstruido = xor_bytes(xor_cifrados, mensaje1)
    print("Mensaje2 recuperado:", mensaje2_reconstruido.decode())

ejemplo_ataque_rc4()
```

#### 🧾 Salida esperada:

```
Cifrado1: 5f460d280e...
Cifrado2: 4c64092a1e...
XOR de ambos: 13020c0210...
Mensaje2 recuperado: Secreto123
```

---

### 🔐 Conclusión

| ✅ Ventajas de RC4 (históricas) | ❌ Debilidades que lo hacen inseguro hoy |
| ------------------------------- | ---------------------------------------- |
| Simple y rápido                 | Sesgo estadístico en el keystream        |
| Fácil de implementar            | Sensible a reutilización de claves/IV    |
| Usado en protocolos populares   | Ataques prácticos en WEP, TLS, SSL       |

#### ❗Estado actual:

> **RC4 ya no debe usarse** en ningún sistema moderno. Está **prohibido en TLS desde 2015**. Solo se usa con fines educativos.

---

[🔼](#índice)

---

## **407. ChaCha20**

### 🔐 ¿Qué es ChaCha20?

**ChaCha20** es un **cifrado de flujo simétrico moderno** desarrollado por Daniel J. Bernstein en 2008, basado en el cifrado anterior llamado **Salsa20**. Es rápido, seguro y está diseñado para funcionar bien en hardware y software.

#### ✨ ¿Por qué es tan popular?

- ✅ **Muy rápido** (incluso más que AES en muchos dispositivos móviles)

- ✅ **Seguro** (no tiene los sesgos de RC4)

- ✅ **Resistente a ataques de canal lateral**

- ✅ Usado por **Google, WhatsApp, WireGuard, OpenSSH**, etc.

---

### 🧠 ¿Cómo funciona ChaCha20?

ChaCha20 no cifra directamente como AES. En lugar de eso:

1. **Toma una clave secreta de 256 bits (32 bytes)**.
2. Toma un **contador de bloque** y un **nonce** (un número aleatorio único por mensaje).
3. Genera un **keystream (flujo de claves pseudoaleatorias)**.
4. Luego, **XOR** el keystream con el mensaje para cifrarlo.

#### Fórmula:

```
ciphertext = plaintext ⊕ keystream
```

Y para descifrar:

```
plaintext = ciphertext ⊕ keystream
```

💡 **Nota**:

El mismo keystream **jamás debe reutilizarse** con la misma clave + nonce, igual que otros stream ciphers.

---

### 📦 ¿Cómo instalar ChaCha20?

Usaremos `pycryptodome`, una librería de Python que implementa ChaCha20 de forma segura.

#### 🔧 Paso 1: Instalar la librería

Abre tu terminal o consola y escribe:

```bash
pip install pycryptodome
```

---

### ✅ Ejemplo completo en Python

```python
from Crypto.Cipher import ChaCha20
from Crypto.Random import get_random_bytes

def ejemplo_chacha20():
    # Paso 1: Crear clave y nonce
    clave = get_random_bytes(32)   # 256 bits
    nonce = get_random_bytes(12)   # 96 bits, recomendado para ChaCha20

    # Paso 2: Crear el mensaje
    mensaje = b"Este es un mensaje secreto usando ChaCha20"

    # Paso 3: Cifrar
    cifrador = ChaCha20.new(key=clave, nonce=nonce)
    ciphertext = cifrador.encrypt(mensaje)

    print("Mensaje original:", mensaje)
    print("Cifrado (hex):", ciphertext.hex())

    # Paso 4: Descifrar
    descifrador = ChaCha20.new(key=clave, nonce=nonce)
    mensaje_recuperado = descifrador.decrypt(ciphertext)

    print("Mensaje descifrado:", mensaje_recuperado)

ejemplo_chacha20()
```

#### 🧾 Salida esperada:

```
Mensaje original: b'Este es un mensaje secreto usando ChaCha20'
Cifrado (hex): 83a2f1c78ef8b1e3f5...
Mensaje descifrado: b'Este es un mensaje secreto usando ChaCha20'
```

---

### 📌 Resumen de ChaCha20

| Característica       | Detalles                                  |
| -------------------- | ----------------------------------------- |
| Tipo                 | Cifrado de flujo (stream cipher)          |
| Longitud de clave    | 256 bits (32 bytes)                       |
| Longitud del nonce   | 96 bits (12 bytes) recomendado            |
| Seguridad            | Muy alta, sin ataques prácticos conocidos |
| Velocidad            | Excelente, mejor que AES en móviles       |
| Implementación común | TLS 1.3, WireGuard, WhatsApp, OpenSSH     |

---

### 🛡️ ¿ChaCha20 es mejor que AES?

Depende del caso:

| Criterio                         | AES          | ChaCha20         |
| -------------------------------- | ------------ | ---------------- |
| Velocidad en CPU sin aceleración | Más lento    | Mucho más rápido |
| Seguridad moderna                | Alta         | Alta             |
| Hardware necesario               | Aceleradores | No necesita      |
| Resistente a timing attacks      | No mucho     | Sí ✅            |

---

[🔼](#índice)

---

## **408. Funcionamiento de ChaCha20**

### 🔐 ¿Qué es ChaCha20?

**ChaCha20** es un **cifrado de flujo moderno** creado por **Daniel J. Bernstein**. Está diseñado para ser:

- Más **rápido** que AES en algunos dispositivos.
- Más **seguro** que antiguos cifrados como RC4.
- Más **resistente** a ataques de temporización (side-channel attacks).

💡 Es ampliamente usado en:

- **TLS 1.3 (HTTPS)**
- **WireGuard VPN**
- **OpenSSH**
- **WhatsApp**

---

### ⚙️ ¿Cómo funciona internamente ChaCha20?

ChaCha20 **no cifra directamente el mensaje**, sino que:

#### 📌 En lugar de eso:

1. **Genera una secuencia pseudoaleatoria de bytes** (keystream).
2. Luego realiza un **XOR** entre el mensaje original y ese keystream.

Esto convierte el mensaje en algo incomprensible (cifrado).

---

#### 🔧 ¿Qué necesita ChaCha20 para funcionar?

- Una **clave secreta** de 256 bits (32 bytes)
- Un **nonce** (número aleatorio único de 96 bits = 12 bytes)
- Un **contador de bloques** (32 bits)
- El **mensaje en texto claro**

---

#### 🧮 ¿Qué pasa dentro de ChaCha20?

ChaCha20 usa una función llamada **"ChaCha core function"**, que transforma un estado inicial de 512 bits (64 bytes) con una serie de operaciones matemáticas:

1. Sumas módulo $2^{32}$
2. Rotaciones a la izquierda
3. XORs

Estos pasos se repiten 20 veces para asegurar la mezcla total de datos.

> 🎯 Resultado: se genera un bloque de 64 bytes de keystream.

Este **keystream** se usa para cifrar (o descifrar) el texto mediante una operación XOR:

```
ciphertext = plaintext ⊕ keystream
plaintext = ciphertext ⊕ keystream
```

---

### 🧠 Ejemplo simplificado (con analogía)

Imagina que quieres enviar un mensaje a tu amigo. Ambos tienen un **libro secreto** (la clave) y cada día usan una **página distinta** (el nonce).

- El libro (clave) genera una lista de números aleatorios (keystream).
- Tú sumas tu mensaje con esa lista (XOR).
- Tu amigo usa el mismo libro y página para **restar** (XOR de nuevo) y recuperar el mensaje.

---

### 📦 Instalación para probar ChaCha20

Usaremos Python y la biblioteca `pycryptodome`, que incluye una implementación segura de ChaCha20.

#### ✅ Instala con pip:

```bash
pip install pycryptodome
```

---

### 🧪 Ejemplo completo en Python

```python
from Crypto.Cipher import ChaCha20
from Crypto.Random import get_random_bytes

def cifrar_con_chacha20(mensaje):
    # Generar clave de 32 bytes (256 bits)
    clave = get_random_bytes(32)

    # Generar nonce de 12 bytes (96 bits)
    nonce = get_random_bytes(12)

    # Crear objeto cifrador con clave y nonce
    cifrador = ChaCha20.new(key=clave, nonce=nonce)

    # Cifrar el mensaje
    ciphertext = cifrador.encrypt(mensaje)

    print("Mensaje original:", mensaje)
    print("Texto cifrado:", ciphertext.hex())

    # Descifrado (necesita misma clave y nonce)
    descifrador = ChaCha20.new(key=clave, nonce=nonce)
    texto_descifrado = descifrador.decrypt(ciphertext)

    print("Texto descifrado:", texto_descifrado)

# Ejecutar
mensaje = b"Hola, esto es un ejemplo de ChaCha20"
cifrar_con_chacha20(mensaje)
```

---

#### 🧾 Salida esperada:

```
Mensaje original: b'Hola, esto es un ejemplo de ChaCha20'
Texto cifrado: e1a3f9c4a8f927...
Texto descifrado: b'Hola, esto es un ejemplo de ChaCha20'
```

---

### ✅ Resumen

| Elemento            | Valor                                  |
| ------------------- | -------------------------------------- |
| Cifrado             | ChaCha20                               |
| Tipo                | Stream Cipher (flujo)                  |
| Clave               | 256 bits (32 bytes)                    |
| Nonce               | 96 bits (12 bytes)                     |
| Operación principal | XOR con keystream                      |
| Seguridad           | Alta, sin ataques prácticos conocidos  |
| Ventaja             | Rápido, seguro y simple de implementar |

---

[🔼](#índice)

---

## **409. Caso Práctico: ChaCha20**

### 🔐 ¿Qué es ChaCha20 (resumen corto)?

ChaCha20 es un **cifrado por flujo moderno**:

- Muy rápido y seguro
- Usado en WhatsApp, TLS 1.3, WireGuard, etc.
- Funciona generando un **keystream pseudoaleatorio** que se combina con el mensaje usando XOR

---

### 🧠 ¿Cuándo lo usarías en la vida real?

ChaCha20 es ideal cuando necesitas:

- 🔐 Cifrar mensajes o archivos en dispositivos móviles (es rápido en hardware débil)
- 🛡️ Evitar ataques de temporización (seguro en entornos no protegidos)
- 🧳 Cifrado rápido sin depender de AES (alternativa moderna)

---

### 🧪 Caso práctico: cifrar un archivo de texto confidencial

Imagina que trabajas en una empresa y tienes que guardar información confidencial en un archivo de texto (por ejemplo, nombres de clientes, contraseñas temporales, notas internas).

#### 🎯 Objetivo:

1. **Cifrar** el archivo usando ChaCha20
2. **Guardar** la clave y el nonce (necesarios para descifrar)
3. **Descifrar** el archivo cuando se necesite

---

### 📦 Instalación (en tu PC)

Instala la librería `pycryptodome`:

```bash
pip install pycryptodome
```

---

### 📁 Archivos que usaremos

- `datos.txt`: contiene el texto a cifrar
- `clave_nonce.bin`: contiene la clave y el nonce (guardados en binario)
- `datos_cifrados.bin`: resultado cifrado
- `datos_descifrados.txt`: resultado descifrado

---

### 🧩 Código completo

#### 🔒 Paso 1: Cifrar el archivo

```python
from Crypto.Cipher import ChaCha20
from Crypto.Random import get_random_bytes

# Leer el archivo original
with open("datos.txt", "rb") as f:
    datos = f.read()

# Generar clave de 32 bytes y nonce de 12 bytes
clave = get_random_bytes(32)
nonce = get_random_bytes(12)

# Cifrar con ChaCha20
cipher = ChaCha20.new(key=clave, nonce=nonce)
datos_cifrados = cipher.encrypt(datos)

# Guardar datos cifrados
with open("datos_cifrados.bin", "wb") as f:
    f.write(datos_cifrados)

# Guardar clave y nonce (necesarios para descifrar)
with open("clave_nonce.bin", "wb") as f:
    f.write(clave + nonce)

print("✅ Archivo cifrado correctamente.")
```

---

#### 🔓 Paso 2: Descifrar el archivo

```python
from Crypto.Cipher import ChaCha20

# Leer los datos cifrados
with open("datos_cifrados.bin", "rb") as f:
    datos_cifrados = f.read()

# Leer clave y nonce
with open("clave_nonce.bin", "rb") as f:
    contenido = f.read()
    clave = contenido[:32]
    nonce = contenido[32:]

# Descifrar con ChaCha20
cipher = ChaCha20.new(key=clave, nonce=nonce)
datos_descifrados = cipher.decrypt(datos_cifrados)

# Guardar los datos descifrados
with open("datos_descifrados.txt", "wb") as f:
    f.write(datos_descifrados)

print("✅ Archivo descifrado correctamente.")
```

---

### 📂 Estructura del proyecto

```
📁 proyecto_chacha20
├── datos.txt               # Texto original
├── datos_cifrados.bin      # Texto cifrado
├── datos_descifrados.txt   # Texto recuperado
├── clave_nonce.bin         # Clave y nonce guardados
├── cifrar.py               # Script de cifrado
└── descifrar.py            # Script de descifrado
```

---

### 🧪 Ejemplo en ejecución

**Contenido de `datos.txt`:**

```
Usuario: Ana
Contraseña: Secreta123
Notas: Enviar informe antes del viernes.
```

**Después de cifrar y descifrar**, el archivo `datos_descifrados.txt` debe contener exactamente el mismo texto.

---

### 🧷 Buenas prácticas

- Nunca reutilices la misma combinación de **clave y nonce** en otro mensaje.
- Almacena la clave y el nonce en un lugar **seguro**, por ejemplo, un archivo cifrado o un gestor de claves.
- Puedes combinar ChaCha20 con **Poly1305** si necesitas **autenticación de integridad** (ChaCha20-Poly1305).

---

### ✅ Resumen final

| Paso               | Detalle                                 |
| ------------------ | --------------------------------------- |
| 🔐 Cifrado usado   | ChaCha20                                |
| 📦 Instalación     | `pip install pycryptodome`              |
| 🔑 Requiere        | Clave de 256 bits + Nonce de 96 bits    |
| 🧪 Caso práctico   | Cifrado y descifrado de archivos        |
| 📁 Archivos usados | texto, clave+nonce, cifrado, descifrado |

---

[🔼](#índice)

---

## **410. Block Ciphers**

### 🔐 ¿Qué es un Block Cipher (cifrador por bloques)?

Un **Block Cipher** es un algoritmo criptográfico que **cifra datos en bloques fijos de bits**, por ejemplo de 64 o 128 bits. A diferencia de los cifradores por flujo (que cifran bit a bit o byte a byte), un cifrador por bloques toma **un bloque completo de datos de entrada** y lo transforma con una clave secreta.

---

#### 🧱 Ejemplo básico:

Supongamos que tenemos un cifrador que cifra **bloques de 4 letras** a la vez, y nuestro mensaje es:

```
Mensaje: HOLAAMIGOS
Bloques: [HOLA] [AMIG] [OSXX]  ← (rellenamos con X para completar el último bloque)
```

Cada bloque es procesado **independientemente** (o con alguna relación, según el modo de operación) usando la clave.

---

### 🧰 ¿Dónde se usan los block ciphers?

- En **TLS/SSL** (cuando visitas páginas web HTTPS)
- En **archivos cifrados** (como ZIP, PDF, discos duros cifrados)
- En **sistemas bancarios y bases de datos cifradas**
- En **VPNs y conexiones seguras**

---

### 🔑 Características importantes

| Característica      | Explicación                                                                                                        |
| ------------------- | ------------------------------------------------------------------------------------------------------------------ |
| **Bloques fijos**   | Trabajan con bloques de tamaño definido (ej. 128 bits)                                                             |
| **Determinísticos** | El mismo bloque de entrada y clave siempre da la misma salida (a menos que se use un modo como CBC, ver más abajo) |
| **Simétricos**      | Usan la misma clave para cifrar y descifrar                                                                        |

---

### 🔄 Modos de operación

Un block cipher **por sí solo solo cifra un bloque**. Para cifrar mensajes largos, usamos **modos de operación**:

| Modo    | Descripción simplificada                                     |
| ------- | ------------------------------------------------------------ |
| ECB     | Cada bloque se cifra por separado (no recomendado, inseguro) |
| CBC     | Cada bloque depende del anterior (más seguro)                |
| CFB/CTR | Cifran como si fueran un stream cipher                       |
| GCM     | Agrega autenticación (AEAD, moderno y seguro)                |

---

### 🔒 Ejemplos de cifradores por bloques populares

| Nombre   | Tamaño de bloque | Tamaño de clave    | Seguro hoy           |
| -------- | ---------------- | ------------------ | -------------------- |
| **AES**  | 128 bits         | 128, 192, 256 bits | ✅ Sí                |
| DES      | 64 bits          | 56 bits            | ❌ No (obsoleto)     |
| 3DES     | 64 bits          | 112 o 168 bits     | ⚠️ No recomendado    |
| Blowfish | 64 bits          | Hasta 448 bits     | ⚠️ No tan usado      |
| Twofish  | 128 bits         | Hasta 256 bits     | ✅ Alternativa a AES |

---

### 🛠️ Instalación (librería en Python)

Usaremos **PyCryptodome**, que ofrece soporte para AES y otros cifradores por bloques.

```bash
pip install pycryptodome
```

---

### ✅ Ejemplo completo: Cifrado con AES en modo CBC

#### ✏️ Paso 1: Cifrar un mensaje

```python
from Crypto.Cipher import AES
from Crypto.Util.Padding import pad
from Crypto.Random import get_random_bytes

# Mensaje a cifrar
mensaje = b"Hola, este es un mensaje secreto que debe protegerse."

# Clave de 16 bytes (128 bits)
clave = get_random_bytes(16)

# IV: vector de inicialización (16 bytes también)
iv = get_random_bytes(16)

# Crear objeto de cifrado AES en modo CBC
cipher = AES.new(clave, AES.MODE_CBC, iv)

# Rellenar el mensaje al múltiplo de 16 bytes
mensaje_padded = pad(mensaje, AES.block_size)

# Cifrar
cifrado = cipher.encrypt(mensaje_padded)

print("🔐 Mensaje cifrado:", cifrado.hex())
```

---

#### ✏️ Paso 2: Descifrar el mensaje

```python
from Crypto.Cipher import AES
from Crypto.Util.Padding import unpad

# Crear objeto de descifrado con misma clave e IV
cipher = AES.new(clave, AES.MODE_CBC, iv)

# Descifrar
descifrado_padded = cipher.decrypt(cifrado)

# Quitar relleno
mensaje_original = unpad(descifrado_padded, AES.block_size)

print("📨 Mensaje descifrado:", mensaje_original.decode())
```

---

### 📂 Resumen del código

- Usamos AES con bloques de 128 bits (16 bytes)
- Modo CBC (Cipher Block Chaining) para seguridad real
- Usamos `pad()` y `unpad()` para asegurar el tamaño de los bloques
- Guardamos `clave` e `iv`, ya que son necesarios para descifrar

---

### 🧠 Conclusión

| Concepto                | Valor                                |
| ----------------------- | ------------------------------------ |
| Tipo                    | Cifrador por bloques (Block Cipher)  |
| Algoritmo usado         | AES (moderno y seguro)               |
| Tamaño de bloque        | 128 bits                             |
| Modo de operación usado | CBC                                  |
| Uso real                | HTTPS, archivos cifrados, VPNs, etc. |

---

[🔼](#índice)

---

## **411. Propiedades de los Block Ciphers**

### 🔐 ¿Qué es un Block Cipher?

Un **Block Cipher** es un algoritmo de cifrado **simétrico** que transforma datos de entrada (plaintext) en bloques de un tamaño fijo, típicamente 64 o 128 bits, usando una clave secreta.

Por ejemplo:

```
Entrada (64 bits): 01001011 10101001 ...
Clave (64 bits):   01100011 11100011 ...
↓
Salida (64 bits):  11100101 00011010 ...
```

---

### 🧠 Propiedades clave de los Block Ciphers

Estas propiedades son esenciales para garantizar que un Block Cipher sea seguro y útil en la práctica.

| Propiedad                           | ¿Qué significa?                                                                    | Ejemplo fácil                                                        |
| ----------------------------------- | ---------------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| **Determinismo (sin modo CBC)**     | Con la misma clave y el mismo texto plano, **siempre** se obtiene el mismo cifrado | AES en modo ECB siempre da el mismo resultado para la misma entrada  |
| **Difusión**                        | Un cambio pequeño en el texto plano afecta muchos bits en el cifrado               | Cambiar 1 letra del mensaje cambia todo el bloque cifrado            |
| **Confusión**                       | La relación entre la clave y el texto cifrado debe ser lo más compleja posible     | No se puede adivinar la clave viendo el texto cifrado                |
| **Avalancha**                       | Cambiar un solo bit en la entrada **cambia la mitad o más de los bits de salida**  | Cambiar una letra hace que el resultado cifrado cambie completamente |
| **Inversibilidad**                  | Se puede **descifrar** correctamente con la misma clave                            | Con la clave correcta puedes recuperar el mensaje original           |
| **Resistencia a ataques conocidos** | No debe ser vulnerable a ataques como texto claro conocido o elegido               | AES y Twofish han sido diseñados para resistir estos ataques         |
| **Longitud fija del bloque**        | El cifrador opera con bloques de un tamaño determinado (ej. 128 bits)              | AES siempre trabaja con bloques de 128 bits                          |

---

#### 🎯 Ejemplo visual de **difusión** y **avalancha**

Imagina dos mensajes que difieren por una sola letra:

```
Mensaje A: "HOLA MUNDO"
Mensaje B: "HOLA NUNDO" ← cambiamos la M por una N

→ El resultado cifrado (en AES modo CBC) será **completamente distinto**
```

Este comportamiento es deseado: **difusión y avalancha protegen contra ataques que intentan deducir patrones**.

---

### 🧰 Instalación de herramientas (Python)

Vamos a usar la librería `pycryptodome`, que incluye implementaciones modernas de cifradores por bloques como AES.

```bash
pip install pycryptodome
```

---

### ✅ Ejemplo completo en Python: Comparando propiedades

Vamos a ver cómo un pequeño cambio en el texto claro cambia completamente el texto cifrado (difusión y avalancha) usando **AES en modo ECB (no recomendado en producción, pero útil para estudiar)**.

```python
from Crypto.Cipher import AES
from Crypto.Util.Padding import pad
from Crypto.Random import get_random_bytes

# Clave de 16 bytes (128 bits)
clave = get_random_bytes(16)

# Mensajes similares
mensaje1 = b"HOLA MUNDO   "  # 12 bytes
mensaje2 = b"HOLA NUNDO   "  # solo cambia una letra: M -> N

# Rellenar mensajes a 16 bytes (bloque de AES)
mensaje1_padded = pad(mensaje1, 16)
mensaje2_padded = pad(mensaje2, 16)

# Crear cifrador AES en modo ECB (determinístico)
cipher = AES.new(clave, AES.MODE_ECB)

# Cifrar ambos mensajes
cifrado1 = cipher.encrypt(mensaje1_padded)
cifrado2 = cipher.encrypt(mensaje2_padded)

# Mostrar resultados
print("🔐 Cifrado de mensaje1:", cifrado1.hex())
print("🔐 Cifrado de mensaje2:", cifrado2.hex())
print("\n¿Son iguales?:", cifrado1 == cifrado2)
```

#### Salida esperada (ejemplo):

```
🔐 Cifrado de mensaje1: 6c31...9aef
🔐 Cifrado de mensaje2: 7b12...fd23
¿Son iguales?: False
```

Esto demuestra:

- **Avalancha**: cambiar una letra cambia todo el cifrado.
- **Determinismo**: si se cifra dos veces el mismo mensaje con misma clave y modo ECB, da el mismo resultado.

---

### 📌 Nota importante

- El **modo ECB** (Electronic Code Book) **no es seguro** para datos reales, porque **no oculta patrones**. Se usa aquí solo con fines educativos.
- En práctica se usan modos como **CBC**, **CTR**, **GCM** que sí protegen contra ataques de análisis.

---

### 🧠 Conclusión

| Propiedad      | Ejemplo práctico                                  |
| -------------- | ------------------------------------------------- |
| Difusión       | Cambio en una letra → cifrado totalmente distinto |
| Avalancha      | 1 bit cambia → mitad del resultado cambia         |
| Inversibilidad | El mensaje se puede recuperar con la clave        |
| Determinismo   | (en ECB) mismo mensaje = mismo resultado          |

---

[🔼](#índice)

---

## **412. Block Ciphers populares**

### 🔐 ¿Qué es un Block Cipher?

Un **Block Cipher** es un algoritmo de cifrado **simétrico** que toma bloques de texto plano (por ejemplo, de 64 o 128 bits) y los convierte en texto cifrado usando una **clave secreta**.

🔁 La misma clave se usa tanto para cifrar como para descifrar.

---

### ⭐ Block Ciphers populares

Aquí te muestro los más conocidos y usados, con explicaciones fáciles:

| Algoritmo    | Año  | Tamaño de bloque | Tamaño de clave  | ¿Dónde se usa?                      |
| ------------ | ---- | ---------------- | ---------------- | ----------------------------------- |
| **DES**      | 1977 | 64 bits          | 56 bits          | Obsoleto, usado históricamente      |
| **3DES**     | 1998 | 64 bits          | 112 o 168 bits   | Obsoleto, fue usado en banca y VPN  |
| **AES**      | 2001 | 128 bits         | 128/192/256 bits | Estándar actual (WiFi, SSL, discos) |
| **Blowfish** | 1993 | 64 bits          | 32 a 448 bits    | VPN, software antiguo               |
| **Twofish**  | 1998 | 128 bits         | 128/192/256 bits | Alternativa a AES                   |
| **Camellia** | 2000 | 128 bits         | 128/192/256 bits | Recomendado en Japón y Europa       |
| **IDEA**     | 1991 | 64 bits          | 128 bits         | Fue usado en PGP                    |

---

### 🧠 Explicación sencilla de los más importantes

#### 🔹 1. **AES (Advanced Encryption Standard)**

- Reemplazó al DES por ser más seguro y rápido.
- Usa bloques de **128 bits**.
- Claves de **128, 192 o 256 bits**.
- Altamente eficiente y resistente a ataques conocidos.

🧪 **Ejemplo real:**

Usado en HTTPS, WhatsApp, Zoom, discos duros encriptados (BitLocker, VeraCrypt), WiFi WPA2/WPA3.

---

#### 🔹 2. **3DES (Triple DES)**

- Aplica DES tres veces para mejorar la seguridad.
- Lento comparado con AES.
- Considerado **inseguro hoy en día** (desde 2018, NIST lo desaprueba).

🧪 **Ejemplo real:**

Se usó en cajeros automáticos, bancos y tarjetas inteligentes.

---

#### 🔹 3. **Blowfish**

- Libre y rápido.
- Bloques de 64 bits → no recomendado para archivos grandes.
- Reemplazado por su sucesor: **Twofish**.

---

#### 🔹 4. **Twofish**

- Candidato finalista para reemplazar a DES (junto con AES).
- Muy seguro, y clave de hasta 256 bits.
- Ideal en sistemas embebidos o alternativos a AES.

---

#### 🔹 5. **Camellia**

- Seguridad similar a AES.
- Recomendado por la ISO y la Unión Europea.
- Rápido en hardware y software.

---

### 🧰 Instalación de herramientas para probarlos (Python)

Vamos a usar **`pycryptodome`**, una librería de Python que implementa muchos cifradores modernos:

```bash
pip install pycryptodome
```

---

### ✅ Ejemplo completo: Cifrado y descifrado con AES

```python
from Crypto.Cipher import AES
from Crypto.Random import get_random_bytes
from Crypto.Util.Padding import pad, unpad

# Generar clave y datos
clave = get_random_bytes(16)  # 128 bits
datos = b"Hola, mundo secreto"

# Rellenar el mensaje para que sea múltiplo de 16
datos_padded = pad(datos, 16)

# Crear cifrador AES en modo ECB (para ejemplo sencillo)
cipher = AES.new(clave, AES.MODE_ECB)

# Cifrar
cifrado = cipher.encrypt(datos_padded)
print("🔐 Cifrado:", cifrado.hex())

# Descifrar
cipher2 = AES.new(clave, AES.MODE_ECB)
descifrado = unpad(cipher2.decrypt(cifrado), 16)
print("🔓 Descifrado:", descifrado.decode('utf-8'))
```

#### Salida esperada:

```
🔐 Cifrado: 77a3efca9a6f1c38c5f0c4fcd71e2e...
🔓 Descifrado: Hola, mundo secreto
```

---

### ⚠️ Nota sobre el modo ECB

- El modo ECB es **inseguro** porque no oculta patrones.
- En la práctica se usan modos como:

  - **CBC** (Cipher Block Chaining)
  - **CTR** (Counter Mode)
  - **GCM** (Galois Counter Mode)

---

### 🧠 Conclusión

| Algoritmo | ¿Se usa hoy?   | Seguridad | Comentario              |
| --------- | -------------- | --------- | ----------------------- |
| AES       | ✅ Sí          | 🔒 Alta   | Estándar global         |
| 3DES      | ❌ No          | ⚠️ Débil  | Obsoleto desde 2018     |
| Blowfish  | ⚠️ Menos       | Buena     | Reemplazado por Twofish |
| Twofish   | ✅ Alternativa | 🔒 Alta   | Libre, rápido, flexible |
| Camellia  | ✅ En uso      | 🔒 Alta   | Apoyo fuerte en Asia/UE |

---

[🔼](#índice)

---

## **413. DES (Data Encryption Standard)**

### 🔐 ¿Qué es DES?

**DES (Data Encryption Standard)** es un algoritmo de **cifrado simétrico por bloques**, publicado en 1977 por el **NIST**. Usa una **clave de 56 bits** (aunque originalmente son 64, 8 se usan para verificación de paridad) y trabaja con **bloques de 64 bits** de datos.

#### 📦 Características principales:

| Propiedad        | Valor                    |
| ---------------- | ------------------------ |
| Tipo             | Cifrado simétrico        |
| Tamaño de bloque | 64 bits                  |
| Tamaño de clave  | 56 bits efectivos        |
| Rondas           | 16 rondas                |
| Velocidad        | Razonable, pero obsoleto |

---

### 🧠 ¿Cómo funciona DES (explicación simple)?

1. **Entrada**: Un bloque de 64 bits (8 bytes de texto plano).
2. **Clave**: Una clave de 64 bits (de los cuales solo 56 se usan).
3. **División**: El bloque se divide en dos mitades de 32 bits: izquierda (L) y derecha (R).
4. **16 rondas** de transformación:

   - En cada ronda, se usa una subclave derivada de la clave original.
   - Se aplica una función (F) a la mitad derecha y se combina con la mitad izquierda.

5. **Reunión final**: Se combinan ambas mitades, se aplica una permutación final, y se obtiene el texto cifrado.

---

### 📛 ¿Por qué ya no se usa DES?

Aunque fue un estándar por décadas, **DES fue roto en 1998** mediante fuerza bruta, debido a su **clave muy corta (56 bits)**. Hoy en día, no se considera seguro.

👉 Por eso se desarrollaron alternativas como **3DES** y luego **AES**.

---

### 🔧 Instalación para probar DES

Vamos a usar `pycryptodome`, una librería de Python para cifrado.

#### Paso 1: Instala la librería

```bash
pip install pycryptodome
```

---

### ✅ Ejemplo completo: Cifrado y descifrado con DES

```python
from Crypto.Cipher import DES
from Crypto.Random import get_random_bytes
from Crypto.Util.Padding import pad, unpad

# DES necesita una clave de 8 bytes (64 bits)
clave = get_random_bytes(8)

# Mensaje a cifrar (debe ser múltiplo de 8 al final)
mensaje = b"Hola, mundo!"

# Rellenar (padding) a múltiplos de 8 bytes
mensaje_padded = pad(mensaje, 8)

# Crear el cifrador en modo ECB
cipher = DES.new(clave, DES.MODE_ECB)

# Cifrar el mensaje
cifrado = cipher.encrypt(mensaje_padded)
print("🔐 Cifrado (hex):", cifrado.hex())

# Descifrar
cipher_dec = DES.new(clave, DES.MODE_ECB)
descifrado = unpad(cipher_dec.decrypt(cifrado), 8)
print("🔓 Descifrado:", descifrado.decode('utf-8'))
```

---

### 🧪 Salida esperada (varía porque la clave es aleatoria)

```
🔐 Cifrado (hex): 8e53a1f67c9e541c275149dfd183b703
🔓 Descifrado: Hola, mundo!
```

---

### ⚠️ Seguridad de DES

- **Clave corta**: solo 56 bits → vulnerable a fuerza bruta.
- **Reemplazado por 3DES** y luego **AES**.
- Solo se usa hoy en sistemas antiguos o para propósitos educativos.

---

### 🧠 Conclusión fácil

| Ventaja                     | Desventaja                    |
| --------------------------- | ----------------------------- |
| Rápido y simple de entender | Clave muy corta (inseguro)    |
| Buena base para aprender    | Vulnerable a ataques modernos |
| Usado durante 20 años       | Reemplazado por AES           |

---

[🔼](#índice)

---

## **414. Detalles del funcionamiento de DES**

### 🔐 ¿Qué es DES?

DES (**Data Encryption Standard**) es un algoritmo de cifrado **simétrico por bloques**. Eso significa que:

- Usa **la misma clave para cifrar y descifrar**.
- Cifra datos **en bloques de 64 bits (8 bytes)**.
- Utiliza una **clave de 64 bits**, aunque solo 56 son usados realmente (los otros 8 son bits de paridad).

---

### 🧠 ¿Cómo funciona DES paso a paso?

Vamos a explicarlo **paso a paso**, con analogías y ejemplos:

---

#### **Entrada: Texto claro de 64 bits**

Supón que queremos cifrar este texto:

```plaintext
Texto: "ABCDEFGH"
```

Cada carácter tiene 1 byte (8 bits), entonces en total son 8 bytes = 64 bits.

---

#### **Clave de 64 bits (8 bytes)**

Ejemplo:

```plaintext
Clave: "mi_clave" + un byte adicional
```

Pero solo se usan **56 bits** (7 bytes) realmente, el resto se usa para verificación de paridad.

---

#### **Permutación inicial (IP)**

Antes de comenzar, DES hace una **permutación inicial** (reordena los bits del bloque de entrada). No cambia el contenido, solo el orden.

---

#### **División en mitades: L0 y R0**

El bloque de 64 bits se divide en dos mitades de 32 bits:

- **L0** = izquierda (los primeros 32 bits)
- **R0** = derecha (los últimos 32 bits)

---

#### **16 rondas de Feistel**

DES hace **16 rondas**, y en cada una:

- Se genera una **subclave de 48 bits** desde la clave principal.
- Se aplica una **función F** a la mitad derecha y se combina con la mitad izquierda.

##### Cada ronda:

```
Li = Ri-1
Ri = Li-1 XOR F(Ri-1, subclave_i)
```

La función F hace esto:

1. **Expansión** de R: de 32 bits a 48 bits.
2. **XOR con subclave** (48 bits).
3. **Sustitución** con S-boxes (reduce de 48 a 32 bits).
4. **Permutación**.

---

#### **Intercambio final y permutación inversa**

Después de 16 rondas:

- Se intercambian las mitades una vez más.
- Se aplica una permutación inversa (IP⁻¹) para obtener el bloque final cifrado.

---

### 🧮 Ejemplo visual simplificado

**Texto plano**: `"ABCDEFGH"` → 64 bits

**Clave**: `"12345678"` (64 bits)

Después del proceso, podrías obtener algo como:

**Texto cifrado (hexadecimal)**:

```
E.g.: 6AC5F149D1FE4379
```

---

### 🔧 Instalación

Para experimentar con DES en Python:

```bash
pip install pycryptodome
```

---

### ✅ Ejemplo completo en Python

```python
from Crypto.Cipher import DES
from Crypto.Random import get_random_bytes
from Crypto.Util.Padding import pad, unpad

# Paso 1: Generar una clave de 8 bytes (64 bits)
clave = get_random_bytes(8)
print("Clave:", clave.hex())

# Paso 2: Mensaje de prueba
mensaje = b"HolaMundo123"  # 11 bytes

# Paso 3: Padding (DES necesita múltiplos de 8 bytes)
mensaje_padded = pad(mensaje, 8)

# Paso 4: Crear el cifrador
cipher = DES.new(clave, DES.MODE_ECB)

# Paso 5: Cifrar
texto_cifrado = cipher.encrypt(mensaje_padded)
print("Texto cifrado (hex):", texto_cifrado.hex())

# Paso 6: Descifrar
cipher_dec = DES.new(clave, DES.MODE_ECB)
descifrado = unpad(cipher_dec.decrypt(texto_cifrado), 8)
print("Texto descifrado:", descifrado.decode())
```

---

#### 🧪 Resultado esperado

```
Clave: b7e2f3a6c5d4e1f0
Texto cifrado (hex): 8a7b6f21ed34c5...
Texto descifrado: HolaMundo123
```

---

### ⚠️ Seguridad de DES hoy

- **DES es obsoleto**: Su clave de 56 bits es muy corta.
- En 1998, se construyó una máquina que rompía DES en menos de un día.
- Hoy usamos **AES** o **ChaCha20**.

---

### 🧠 Resumen

| Paso            | Explicación                              |
| --------------- | ---------------------------------------- |
| Entrada         | Bloque de 64 bits (8 bytes)              |
| Clave           | 64 bits (solo 56 útiles)                 |
| Rondas          | 16 rondas Feistel                        |
| Función F       | Expansión → XOR → Sustitución → Permutar |
| Resultado final | Bloque cifrado de 64 bits                |
| Implementación  | Usando `pycryptodome` en Python          |

---

[🔼](#índice)

---

## **415. Ataques a DES**

### 🧠 ¿Qué es DES?

DES es un algoritmo de **cifrado simétrico por bloques** desarrollado en los años 70. Utiliza:

- Bloques de **64 bits** de datos.
- Una clave de **64 bits**, de los cuales **56 bits son útiles** (8 son de paridad).
- **16 rondas** de operaciones en estructura Feistel.

Aunque fue muy popular, **hoy está considerado inseguro**.

---

### 🛠️ ¿Por qué DES es vulnerable?

Principalmente por su **tamaño de clave corto**. Solo tiene 2⁵⁶ combinaciones posibles, lo que permite ataques **por fuerza bruta**.

2⁵⁶ ≈ 72 cuatrillones de claves

Hoy, eso puede romperse en **horas o minutos** con computadoras modernas.

---

### 🔓 Principales ataques a DES

#### 🔨 **Ataque por Fuerza Bruta**

**Qué es**: Probar todas las claves posibles hasta encontrar la correcta.

**Ejemplo**:

Supón que el mensaje cifrado es `8A1B3C4D...`, y sabes que el texto plano original comienza con `"Hola"`. Puedes probar todas las combinaciones posibles de claves hasta que la desencriptación coincida con `"Hola..."`.

🔧 En 1998, la **EFF (Electronic Frontier Foundation)** construyó una máquina que rompía DES en menos de 24 horas.

---

#### 🧠 **Ataques de Texto Plano Conocido**

**Qué es**:

El atacante **sabe parte del mensaje original** (texto plano) y también el mensaje cifrado correspondiente. Así puede intentar recuperar la clave.

**Ejemplo fácil**:

- Texto plano: `"Inicio sesión: admin"`
- Texto cifrado: `F3C1B2...`

Si se tienen suficientes pares de texto plano y cifrado, se puede reconstruir la clave o reducir el espacio de búsqueda.

---

#### 🔁 **Ataque de Texto Cifrado Elegido**

**Qué es**:

El atacante **elige textos a cifrar** y obtiene los resultados cifrados, como en un sistema vulnerable tipo "encripta tu contraseña aquí".

Esto permite estudiar cómo se comporta el algoritmo y reconstruir la clave.

---

#### 🧱 **Criptoanálisis Diferencial**

**Qué es**:

Técnica que analiza **cómo pequeñas diferencias en el texto plano afectan al texto cifrado**.

Se necesitan **muchos pares de datos cifrados** con diferencias controladas.

Esto fue una técnica avanzada **diseñada por investigadores de IBM** y luego usada por la NSA.

---

### 🛑 ¿Por qué NO se debe usar DES hoy?

| Motivo                        | Detalle                                |
| ----------------------------- | -------------------------------------- |
| Clave muy corta               | 56 bits son fáciles de romper hoy.     |
| Criptoanálisis efectivo       | Diferencial y lineal funcionan.        |
| Fuerza bruta acelerada        | Hardware moderno lo rompe rápidamente. |
| Sustituido por AES y ChaCha20 | Más rápidos, seguros y modernos.       |

---

### 🔧 ¿Cómo simular un ataque a DES? (didáctico)

Para fines educativos, puedes hacer una **mini fuerza bruta** usando claves pequeñas, aunque no es realista para 2⁵⁶ claves.

#### 📦 Instalación

Usamos `pycryptodome`:

```bash
pip install pycryptodome
```

---

### ✅ Ejemplo en Python: Mini fuerza bruta a DES

Vamos a usar claves de 8 bytes pero solo probar las primeras 1000 posibles (por simplicidad):

```python
from Crypto.Cipher import DES
from Crypto.Util.Padding import pad, unpad
from itertools import product
import string

# Mensaje original y clave real
clave_real = b'12345678'  # 8 bytes
mensaje = b"HolaDES123"

# Cifrado original
cipher = DES.new(clave_real, DES.MODE_ECB)
mensaje_padded = pad(mensaje, 8)
cifrado = cipher.encrypt(mensaje_padded)
print("Texto cifrado (hex):", cifrado.hex())

# Simulamos ataque por fuerza bruta (solo 3 caracteres para el demo)
alfabeto = string.digits
for k in product(alfabeto, repeat=3):
    intento = ''.join(k).ljust(8, '0')  # Rellenar con ceros hasta 8 bytes
    try:
        cipher_try = DES.new(intento.encode(), DES.MODE_ECB)
        descifrado = unpad(cipher_try.decrypt(cifrado), 8)
        if b"Hola" in descifrado:
            print(f"¡Clave encontrada!: {intento}")
            print("Mensaje descifrado:", descifrado.decode())
            break
    except:
        continue
```

#### 🧪 Resultado esperado (versión reducida):

```
Texto cifrado (hex): 8f4b1c...
¡Clave encontrada!: 12300000
Mensaje descifrado: HolaDES123
```

---

### 🛡️ ¿Cómo protegerse?

#### ✅ Soluciones modernas:

| Solución                | Descripción                                       |
| ----------------------- | ------------------------------------------------- |
| **AES (128, 192, 256)** | Algoritmo de cifrado moderno y seguro.            |
| **ChaCha20**            | Rápido y seguro, ideal para dispositivos móviles. |
| **Evitar modo ECB**     | Usa CBC, GCM o modos con IV aleatorio.            |
| **Contraseñas fuertes** | Usa generadores seguros, no patrones simples.     |

---

### 📌 Resumen Final

- **DES ya no es seguro**. Romperlo es factible hoy en día.
- **Fuerza bruta**, criptoanálisis y ataques con texto conocido son efectivos.
- Puedes simular ataques reducidos con Python para aprender.
- **Usa AES o ChaCha20** en sistemas modernos.

---

[🔼](#índice)

---

## **416. Triple DES**

### 🔐 ¿Qué es Triple DES?

**Triple DES (3DES)** es una versión más segura del algoritmo original **DES** (Data Encryption Standard), que **cifra los datos tres veces** en lugar de una.

> 🔎 Se creó porque DES (con claves de 56 bits) se volvió inseguro ante ataques por fuerza bruta.

---

#### 🧠 ¿Cómo funciona?

En lugar de cifrar una vez con una clave, 3DES **cifra, descifra y vuelve a cifrar** el mensaje, usando **tres claves diferentes** (o una clave dividida en partes).

**Esquema básico (modo EDE):**

```
C = E(K3, D(K2, E(K1, P)))
```

Donde:

- `E = Encrypt`, `D = Decrypt`, `P = Plaintext`, `C = Ciphertext`
- `K1`, `K2`, `K3` son las claves (pueden ser iguales o distintas)
- Se cifra con `K1`, luego se descifra con `K2`, y se cifra otra vez con `K3`

---

### 🔑 Tipos de claves en Triple DES

| Tipo                            | Descripción                         |
| ------------------------------- | ----------------------------------- |
| **1 clave (K1 = K2 = K3)**      | Igual a DES, inseguro hoy           |
| **2 claves (K1 ≠ K2, K3 = K1)** | Seguridad media                     |
| **3 claves distintas**          | Seguridad alta (168 bits efectivos) |

---

### ✅ Ventajas y ❌ Desventajas

| ✅ Ventajas                 | ❌ Desventajas                           |
| --------------------------- | ---------------------------------------- |
| Más seguro que DES          | Más lento que AES                        |
| Fácil de implementar        | Usa bloques de 64 bits (menos eficiente) |
| Compatible con sistemas DES | Vulnerable a ataques de cumpleaños       |

---

### 🧪 Ejemplo práctico fácil de entender

Supón que quieres cifrar el mensaje:

```
Mensaje: "Hola mundo"
Clave1: "12345678"
Clave2: "abcdefgh"
Clave3: "ABCDEFGH"
```

Se cifra 3 veces con esas claves.

---

### 🧰 ¿Cómo se “instala” o usa?

Usaremos **Python** y la librería `pycryptodome`, que permite trabajar con 3DES fácilmente.

#### 📦 Instalación

Primero, instala la librería:

```bash
pip install pycryptodome
```

---

### 🧑‍💻 Ejemplo completo en Python con Triple DES

```python
from Crypto.Cipher import DES3
from Crypto.Util.Padding import pad, unpad

# Mensaje a cifrar
mensaje = b"Hola mundo"

# Claves deben tener 16 o 24 bytes para 3DES
clave = b'12345678abcdefghABCDEFGH'  # 24 bytes = 3 claves de 8 bytes

# Crear objeto Triple DES
cipher = DES3.new(clave, DES3.MODE_ECB)

# Cifrado
mensaje_padded = pad(mensaje, 8)  # DES usa bloques de 8 bytes
cifrado = cipher.encrypt(mensaje_padded)
print("Cifrado (hex):", cifrado.hex())

# Descifrado
cipher2 = DES3.new(clave, DES3.MODE_ECB)
descifrado = unpad(cipher2.decrypt(cifrado), 8)
print("Descifrado:", descifrado.decode())
```

#### ✅ Salida esperada:

```
Cifrado (hex): 2fa3d4...
Descifrado: Hola mundo
```

---

### 📌 Consideraciones importantes

1. **Modo ECB** es el más básico pero **no recomendado** para producción. Usar CBC o GCM con un **IV aleatorio** es mejor.
2. **3DES está obsoleto**, aunque aún es usado en sistemas antiguos.
3. Para nuevos proyectos se recomienda **AES** o **ChaCha20**.

---

### 🛡️ Alternativas modernas

| Algoritmo    | Longitud de clave  | Seguridad                       |
| ------------ | ------------------ | ------------------------------- |
| **AES**      | 128, 192, 256 bits | Muy alta                        |
| **ChaCha20** | 256 bits           | Alta y rápida                   |
| **3DES**     | 112 o 168 bits     | Aceptable pero lenta y obsoleta |

---

### 🧠 Resumen final

| Punto clave                          | Detalle                             |
| ------------------------------------ | ----------------------------------- |
| Triple DES = cifrar 3 veces          | E(K3, D(K2, E(K1, P)))              |
| Claves: 1, 2 o 3 distintas           | 3 claves = más seguridad (168 bits) |
| Python lo soporta con `pycryptodome` | Usa `DES3.new()` y `pad/unpad`      |
| Mejor usar AES en nuevos sistemas    | Más rápido y seguro                 |

---

[🔼](#índice)

---

## **417. AES (Advanced Encryption Standard)**

### 🔐 ¿Qué es AES?

**AES** (Advanced Encryption Standard) es uno de los algoritmos de cifrado **más usados y seguros del mundo**. Se utiliza para **proteger datos** en comunicaciones, discos, correos electrónicos, aplicaciones bancarias, etc.

Fue adoptado por el **gobierno de EE.UU.** en 2001 como reemplazo del antiguo **DES**, que era vulnerable.

---

#### 📌 Características principales de AES

| Característica      | Valor                                               |
| ------------------- | --------------------------------------------------- |
| Tipo de cifrado     | Simétrico (misma clave para cifrar y descifrar)     |
| Longitudes de clave | 128, 192 o 256 bits                                 |
| Tamaño de bloque    | 128 bits (16 bytes)                                 |
| Velocidad           | Rápido y eficiente                                  |
| Seguridad           | Muy alta (incluso contra ataques cuánticos básicos) |

---

### 🧠 ¿Cómo funciona AES?

AES **trabaja en bloques de 16 bytes** (128 bits). Usa una serie de transformaciones llamadas **rondas**, y cada tamaño de clave tiene un número diferente de rondas:

| Tamaño de clave | Rondas |
| --------------- | ------ |
| 128 bits        | 10     |
| 192 bits        | 12     |
| 256 bits        | 14     |

Cada ronda hace:

1. **SubBytes**: Sustituye cada byte con otro usando una tabla fija.
2. **ShiftRows**: Mueve (rota) las filas de la matriz de bytes.
3. **MixColumns**: Mezcla los datos de cada columna.
4. **AddRoundKey**: Mezcla con una parte de la clave.

---

### 🔑 ¿Por qué AES es seguro?

- Las transformaciones son no lineales y complejas.
- Soporta claves de 256 bits (inmune a ataques de fuerza bruta).
- Ha resistido análisis cripto durante más de 20 años.

---

### 🧪 Ejemplo simple de uso

Supongamos que quieres cifrar este texto:

```
Texto: "Hola mundo AES"
Clave: "EstaEsUnaClaveSegura123456" (32 bytes → AES-256)
```

---

### 🧰 ¿Cómo se instala y usa en Python?

Usaremos la biblioteca `pycryptodome`.

#### 📦 Instalación

Abre tu terminal y ejecuta:

```bash
pip install pycryptodome
```

---

### 🧑‍💻 Ejemplo completo en Python

Aquí ciframos y desciframos un mensaje con **AES en modo CBC**, que es más seguro que ECB porque usa un IV (vector de inicialización) aleatorio.

```python
from Crypto.Cipher import AES
from Crypto.Random import get_random_bytes
from Crypto.Util.Padding import pad, unpad

# Mensaje original
mensaje = b"Hola mundo AES"

# Clave de 32 bytes = AES-256
clave = b'EstaEsUnaClaveSegura1234567890!!'

# IV (vector de inicialización) aleatorio de 16 bytes
iv = get_random_bytes(16)

# Crear objeto AES en modo CBC
cipher = AES.new(clave, AES.MODE_CBC, iv)

# Cifrar mensaje con padding
mensaje_padded = pad(mensaje, AES.block_size)
cifrado = cipher.encrypt(mensaje_padded)

print("Cifrado (hex):", cifrado.hex())

# Para descifrar
cipher2 = AES.new(clave, AES.MODE_CBC, iv)
descifrado = unpad(cipher2.decrypt(cifrado), AES.block_size)

print("Descifrado:", descifrado.decode())
```

---

#### ✅ Salida esperada

```text
Cifrado (hex): 3a9b58ac53e9e7a4...
Descifrado: Hola mundo AES
```

---

### 🔐 Modos de operación comunes

AES no se usa solo: necesita un **modo de operación**:

| Modo | Descripción                           | Seguro para producción |
| ---- | ------------------------------------- | ---------------------- |
| ECB  | Cifra bloques por separado (inseguro) | ❌                     |
| CBC  | Cifra cada bloque con el anterior     | ✅ (con IV aleatorio)  |
| CTR  | Convierte AES en un stream cipher     | ✅                     |
| GCM  | Autenticado y rápido (usa IV + tag)   | ✅✅✅ (preferido)     |

---

### 🛡️ Buenas prácticas

- Usa **AES-256** si quieres máxima seguridad.
- Usa siempre un **IV aleatorio** (excepto en ECB).
- Nunca reutilices la misma clave + IV.
- Para producción: usa **modo GCM** porque da **autenticación (integridad)** además del cifrado.

---

### 📌 Resumen final

| Concepto                 | Explicación breve                      |
| ------------------------ | -------------------------------------- |
| AES                      | Algoritmo de cifrado simétrico moderno |
| Bloques                  | 128 bits (16 bytes)                    |
| Claves                   | 128, 192, 256 bits                     |
| Modo recomendado         | GCM o CBC (con IV aleatorio)           |
| Implementación en Python | Usando `pycryptodome`                  |

---

[🔼](#índice)

---

## **418. Detalles de las funciones de AES**

### 🧠 ¿Qué hace internamente AES?

AES **transforma bloques de texto plano en bloques cifrados** de 128 bits usando una clave de 128, 192 o 256 bits. Este proceso se realiza en **rondas** (entre 10 y 14, dependiendo del tamaño de la clave), y cada ronda aplica una **serie de funciones internas**:

---

### 🔄 Funciones internas de AES

Cada ronda de AES aplica las siguientes 4 operaciones (excepto la última, que omite una):

#### **SubBytes** (Sustitución no lineal)

🔹 **¿Qué hace?**

Sustituye cada byte de la matriz con otro según una tabla (llamada **S-box**), fija y conocida.

🔹 **¿Por qué?**

Introduce **no linealidad**, haciendo más difícil para un atacante predecir los cambios.

🔹 **Ejemplo:**

Supón que un byte en la matriz vale `0x53`. En la S-box, eso se sustituye por `0xED`.

```txt
Entrada: 0x53
Salida:  0xED  ← según la S-box
```

---

#### **ShiftRows** (Rotación de filas)

🔹 **¿Qué hace?**

Rota los bytes en cada fila de la matriz hacia la izquierda:

- Fila 0: no se mueve.
- Fila 1: se rota 1 byte.
- Fila 2: se rota 2 bytes.
- Fila 3: se rota 3 bytes.

🔹 **¿Por qué?**

Rompe la alineación vertical y dispersa los datos.

🔹 **Ejemplo:**

Antes:

```
[ a  b  c  d ]
[ e  f  g  h ]
[ i  j  k  l ]
[ m  n  o  p ]
```

Después de ShiftRows:

```
[ a  b  c  d ]
[ f  g  h  e ]
[ k  l  i  j ]
[ p  m  n  o ]
```

---

#### **MixColumns** (Mezcla por columnas)

🔹 **¿Qué hace?**

Aplica una transformación matemática (multiplicación en Galois Field) a cada **columna** de la matriz.

🔹 **¿Por qué?**

Introduce **difusión**: un solo byte del texto afecta a varios bytes del bloque cifrado.

🔹 **Ejemplo simplificado:**

```txt
Entrada: columna [a, b, c, d]
Salida: columna [a', b', c', d'] ← mezcla calculada por fórmula GF(2⁸)
```

No es intuitivo ver el resultado sin cálculos complejos, pero la idea es que mezcla los 4 valores para dispersar la información.

---

#### **AddRoundKey** (XOR con parte de la clave)

🔹 **¿Qué hace?**

Cada byte del estado (matriz de 4x4 bytes) se mezcla con una parte de la clave mediante **XOR**.

🔹 **¿Por qué?**

Introduce la clave al proceso de cifrado.

🔹 **Ejemplo:**

```txt
Estado:    0x3C
Clave:     0xA6
Resultado: 0x3C ^ 0xA6 = 0x9A
```

---

#### 🔁 ¿Cuántas veces se repite esto?

| Tamaño de clave | Rondas totales |
| --------------- | -------------- |
| 128 bits        | 10             |
| 192 bits        | 12             |
| 256 bits        | 14             |

- La **primera ronda** solo hace `AddRoundKey`.
- Las **intermedias** hacen las 4 funciones.
- La **última ronda** omite `MixColumns`.

---

### 📊 Estructura general de AES-128

```
Entrada: Texto plano (16 bytes)
↓
AddRoundKey (clave inicial)
↓
9 Rondas de:
    SubBytes
    ShiftRows
    MixColumns
    AddRoundKey
↓
Última ronda (solo 3 pasos):
    SubBytes
    ShiftRows
    AddRoundKey
↓
Salida: Texto cifrado
```

---

### 📦 Instalación para usar AES

Usaremos la biblioteca `pycryptodome`.

Instálala con:

```bash
pip install pycryptodome
```

---

### 🧪 Ejemplo completo en Python

Este código muestra el cifrado AES-128 con clave de 16 bytes y modo ECB (educativo, **no seguro en producción**).

```python
from Crypto.Cipher import AES
from Crypto.Util.Padding import pad, unpad

# Clave de 16 bytes = 128 bits
clave = b'ClaveDe16Bytes!!'

# Mensaje de prueba (menos de 16 bytes → necesita padding)
mensaje = b"Hola AES"

# Rellenar mensaje a múltiplos de 16 bytes
mensaje_padded = pad(mensaje, AES.block_size)

# Crear objeto AES en modo ECB (solo para demostración)
cipher = AES.new(clave, AES.MODE_ECB)

# Cifrar
cifrado = cipher.encrypt(mensaje_padded)
print("Texto cifrado (hex):", cifrado.hex())

# Descifrar
cipher2 = AES.new(clave, AES.MODE_ECB)
descifrado = unpad(cipher2.decrypt(cifrado), AES.block_size)
print("Texto descifrado:", descifrado.decode())
```

---

#### 🛑 Nota importante

ECB **no** es seguro en producción porque no usa IV y patrones se repiten. Usa CBC o GCM en la práctica.

---

### ✅ Resumen

| Función     | Qué hace                  | Por qué importa           |
| ----------- | ------------------------- | ------------------------- |
| SubBytes    | Sustituye bytes por otros | No linealidad (confusión) |
| ShiftRows   | Rota filas                | Dispersión (difusión)     |
| MixColumns  | Mezcla columnas           | Más difusión              |
| AddRoundKey | XOR con parte de la clave | Introduce secreto         |

---

[🔼](#índice)

---

## **419. Caso práctico: AES**

### 🔐 ¿Qué es AES?

**AES (Advanced Encryption Standard)** es un algoritmo de cifrado **simétrico** que transforma información legible (texto plano) en algo ilegible (texto cifrado) usando una **clave secreta compartida**.

🔑 **Simétrico** = la misma clave sirve para **cifrar y descifrar**.

---

### 🧠 Caso práctico: “Encriptar contraseñas de usuarios antes de guardarlas”

#### 🎯 Objetivo:

Simular un sistema donde un usuario crea una cuenta, su contraseña se **cifra con AES**, y luego se puede **descifrar** solo con la clave.

> 🚨 _Nota:_ En el mundo real, **las contraseñas se almacenan con funciones hash (como bcrypt)**, no cifradas. Este caso es educativo, también aplicable a cifrado de mensajes, archivos, etc.

---

### ⚙️ Instalación

Primero, necesitas instalar la biblioteca **`pycryptodome`**, que contiene la implementación de AES:

```bash
pip install pycryptodome
```

---

### 🧩 Elementos que usaremos

- **Clave secreta**: de 16, 24 o 32 bytes (AES-128, 192 o 256)
- **IV (vector de inicialización)**: requerido en modos como CBC
- **Modo de cifrado**: usaremos **AES en modo CBC**, más seguro que ECB
- **Relleno (padding)**: los datos deben ser múltiplos de 16 bytes

---

### ✅ Ejemplo completo en Python

```python
from Crypto.Cipher import AES
from Crypto.Util.Padding import pad, unpad
from Crypto.Random import get_random_bytes

# 1. Supongamos que el usuario escribe una contraseña
password = "MiS3cret0!"  # texto plano

# 2. Convertimos a bytes
datos = password.encode()

# 3. Generamos una clave secreta de 16 bytes (AES-128)
clave = get_random_bytes(16)  # se debe guardar para descifrar después

# 4. Generamos un IV aleatorio (vector de inicialización) de 16 bytes
iv = get_random_bytes(16)

# 5. Crear el objeto AES en modo CBC
cipher = AES.new(clave, AES.MODE_CBC, iv)

# 6. Cifrar el mensaje (con padding para completar a múltiplos de 16)
cifrado = cipher.encrypt(pad(datos, AES.block_size))

print("🔒 Contraseña cifrada (hex):", cifrado.hex())

# 7. Para descifrar...
# Crear un nuevo objeto AES con la misma clave e IV
cipher_descifrado = AES.new(clave, AES.MODE_CBC, iv)

# 8. Descifrar y quitar el padding
descifrado = unpad(cipher_descifrado.decrypt(cifrado), AES.block_size)

print("🔓 Contraseña descifrada:", descifrado.decode())
```

---

#### 🧪 Salida esperada (varía por el IV aleatorio):

```
🔒 Contraseña cifrada (hex): 01ae9f89b7ef276cabf0c35dc419ab2b
🔓 Contraseña descifrada: MiS3cret0!
```

---

### 🛡️ ¿Dónde se usa AES en la vida real?

- Cifrado de archivos ZIP, PDF, y bases de datos
- Seguridad de comunicaciones (TLS/SSL)
- Mensajería cifrada (como WhatsApp)
- Tarjetas inteligentes (smart cards)
- Seguridad en discos duros (BitLocker, FileVault)

---

### 📌 Recomendaciones

| Buenas prácticas AES         | Descripción                                         |
| ---------------------------- | --------------------------------------------------- |
| Nunca uses ECB               | Usa CBC, GCM, o CTR — ECB repite patrones           |
| Usa IV aleatorio y único     | Pero no necesitas mantenerlo en secreto             |
| Guarda la clave con cuidado  | Es la llave para recuperar la información           |
| Aplica padding               | Usa `pad` y `unpad` para asegurar bloques correctos |
| No uses AES para contraseñas | Usa hashing como `bcrypt` o `argon2` en esos casos  |

---

### 🧠 ¿Qué aprendiste?

Has aplicado AES en un caso **realista y práctico**, entendiendo:

- Qué funciones necesita AES para funcionar
- Qué datos debes generar (clave, IV)
- Cómo cifrar y descifrar correctamente

---

[🔼](#índice)

---

## **420. Initialization Vector (IV)**

### 🔐 ¿Qué es un Initialization Vector (IV)?

El **IV (Initialization Vector)** o **Vector de Inicialización** es un **valor aleatorio o pseudorrandom** que se utiliza **junto con una clave** para **cifrar datos** en muchos algoritmos de cifrado simétrico, como **AES en modo CBC, CFB, OFB y CTR**.

> 📌 **Importante:** El IV no necesita ser secreto, pero **debe ser único y aleatorio para cada cifrado**.
>
> Si usas el mismo IV y la misma clave para cifrar dos mensajes diferentes, podrías facilitar un ataque criptográfico.

---

### 🧠 ¿Por qué se necesita el IV?

Si ciframos dos mensajes iguales con la **misma clave**, **sin IV**, el resultado cifrado sería el mismo. Eso **filtra información**. El IV **asegura que los textos cifrados sean distintos**, incluso si el texto plano es igual.

---

### 🏗️ ¿Dónde se usa el IV?

El IV se usa en **modos de operación de cifrado por bloques** como:

| Modo | ¿Usa IV? | ¿Para qué sirve el IV?                  |
| ---- | -------- | --------------------------------------- |
| ECB  | ❌       | No usa IV (inseguro)                    |
| CBC  | ✅       | Cifra el primer bloque                  |
| CFB  | ✅       | Inicializa el primer bloque de feedback |
| OFB  | ✅       | Semilla para generar keystream          |
| CTR  | ✅       | Contador inicial                        |

---

### ⚙️ Instalación (si usas Python)

Usaremos la librería `pycryptodome` para el cifrado:

```bash
pip install pycryptodome
```

---

### ✅ Ejemplo completo en Python

Cifraremos una contraseña usando AES en modo CBC con un IV aleatorio.

```python
from Crypto.Cipher import AES
from Crypto.Util.Padding import pad, unpad
from Crypto.Random import get_random_bytes

# Texto plano (ej. una contraseña)
texto_plano = "contrasena123"
datos = texto_plano.encode()

# Generamos una clave AES de 16 bytes (AES-128)
clave = get_random_bytes(16)

# Generamos un IV aleatorio de 16 bytes (para CBC)
iv = get_random_bytes(16)

# Creamos el objeto de cifrado AES en modo CBC
cifrador = AES.new(clave, AES.MODE_CBC, iv)

# Aplicamos padding al texto plano y lo ciframos
cifrado = cifrador.encrypt(pad(datos, AES.block_size))

# Mostramos resultados
print("Texto cifrado (hex):", cifrado.hex())
print("IV usado (hex):", iv.hex())

# 🔓 Desciframos
# Necesitamos usar el mismo IV y clave
descifrador = AES.new(clave, AES.MODE_CBC, iv)
descifrado = unpad(descifrador.decrypt(cifrado), AES.block_size)

print("Texto descifrado:", descifrado.decode())
```

---

#### 🧪 Salida esperada (variable en cada ejecución):

```
Texto cifrado (hex): 7c508fa8e7a7e27d15a82e2ad8bd6c50
IV usado (hex): 23fe3a8fbb3a7c0d7c52493303f2f312
Texto descifrado: contrasena123
```

---

### 📌 Buenas prácticas sobre el IV

| Práctica                                                                | ¿Por qué?                           |
| ----------------------------------------------------------------------- | ----------------------------------- |
| Generar IV aleatorio para cada cifrado                                  | Asegura la unicidad y seguridad     |
| Usar un IV del tamaño correcto (igual al tamaño del bloque del cifrado) | AES = 16 bytes                      |
| Guardar o enviar el IV junto al mensaje cifrado                         | Es necesario para descifrar         |
| No reutilizar el IV con la misma clave                                  | Puede provocar ataques por patrones |

---

### 📦 ¿Cómo guardar o enviar el IV?

Como el IV no es secreto, puedes hacer cosas como:

```python
mensaje_final = iv + cifrado
```

Y al descifrar:

```python
iv_recibido = mensaje_final[:16]
cifrado_recibido = mensaje_final[16:]
```

---

### 🧠 ¿Qué aprendiste?

- El IV **agrega aleatoriedad y seguridad** al cifrado.
- Debe ser único por mensaje y tener el tamaño adecuado.
- No es secreto, pero sí esencial para descifrar.

---

[🔼](#índice)

---

## **421. Modos de operación: ECB**

### 🧠 ¿Qué es ECB (Electronic Codebook Mode)?

**ECB (Electronic Codebook)** es uno de los modos de operación de los **algoritmos de cifrado por bloques**, como AES o DES.

#### 🔐 ¿Cómo funciona?

- Divide el mensaje en **bloques del mismo tamaño** (por ejemplo, 16 bytes para AES).
- **Cada bloque** se cifra **de forma independiente** usando la **misma clave**.

> 🧊 Es como poner cada bloque en una caja fuerte separada, **todas con la misma llave**.

---

### 📦 Ejemplo visual

Supongamos que queremos cifrar el mensaje:

```
"ATAQUEALAMANANA"
```

(AES trabaja con bloques de 16 bytes, este texto tiene 15, así que le aplicamos **padding** para que encaje).

Ahora lo dividimos en bloques:

```
[ATAQUEALAMANANA]
```

Como es un solo bloque (16 bytes), ECB lo cifra con la **misma clave**.

Pero si tuviéramos:

```
ATAQUE A LA MAÑANA EN EL PUENTE
```

Se dividiría en bloques así (imaginando que cada bloque es de 8 letras):

```
[ATAQUE A] [ LA MAÑA] [NA EN EL ] [PUENTE..]
```

Y **si se repite un bloque**, **el texto cifrado será igual**, lo cual es **un gran problema** de seguridad.

---

### ⚠️ Problema de seguridad del ECB

**ECB no oculta patrones** en los datos. Esto puede ser **peligroso**.

#### Ejemplo famoso: imagen cifrada con ECB

Cuando una imagen (como el logo de Linux) se cifra en modo ECB, los **patrones visuales se mantienen**, aunque los colores cambien. No se ve igual, pero **la forma de Tux sigue allí**.

¡Malo para la seguridad! 😬

---

### ✅ ¿Cuándo usar ECB?

**NUNCA** en la práctica moderna, salvo en casos muy específicos (como cifrado de claves o datos muy pequeños y únicos).

---

### ⚙️ Instalación del entorno (Python)

Usaremos `pycryptodome`, una librería para cifrado:

```bash
pip install pycryptodome
```

---

### 🧪 Ejemplo completo en Python: AES en modo ECB

```python
from Crypto.Cipher import AES
from Crypto.Util.Padding import pad, unpad
from Crypto.Random import get_random_bytes

# Texto plano
texto = "ATAQUEALAMANANA"
datos = texto.encode()  # Convertimos a bytes

# Clave AES de 16 bytes (AES-128)
clave = get_random_bytes(16)

# Ciframos usando ECB
cifrador = AES.new(clave, AES.MODE_ECB)
cifrado = cifrador.encrypt(pad(datos, AES.block_size))

print("Texto cifrado (hex):", cifrado.hex())

# Desciframos
descifrador = AES.new(clave, AES.MODE_ECB)
descifrado = unpad(descifrador.decrypt(cifrado), AES.block_size)

print("Texto descifrado:", descifrado.decode())
```

---

#### 🧾 Salida esperada:

```
Texto cifrado (hex): 8f763f542bf64a70c8f172c13886f96e
Texto descifrado: ATAQUEALAMANANA
```

---

### 📌 Resumen rápido:

| Característica                           | ECB          |
| ---------------------------------------- | ------------ |
| ¿Divide en bloques?                      | ✅           |
| ¿Cada bloque se cifra igual si es igual? | ❌ inseguro  |
| ¿Usa IV?                                 | ❌           |
| ¿Se recomienda en la práctica?           | ❌ No        |
| ¿Es simple de usar?                      | ✅ Muy fácil |

---

### ✅ Conclusión

- ECB es **el modo más básico**, pero también **el más inseguro**.
- Es útil **para entender** cómo funciona el cifrado por bloques.
- **Nunca lo uses para cifrar archivos, mensajes o imágenes reales.**

---

[🔼](#índice)

---

## **422. Modos de operación: CBC**

### 🔐 ¿Qué es CBC?

**CBC (Cipher Block Chaining)** es un **modo de operación** para algoritmos de cifrado por bloques como AES. Es mucho más seguro que ECB porque **agrega dependencia entre los bloques cifrados**.

#### 🧠 Idea básica:

Cada bloque de texto plano se **XORea con el bloque cifrado anterior** antes de cifrarlo. Así, **aunque dos bloques de texto plano sean iguales, los bloques cifrados serán diferentes**, si el anterior fue distinto.

---

### 🧊 Flujo del cifrado CBC

Supón que tienes estos bloques de texto plano (en letras para simplificar):

```
Bloque 1: ATAQUEEN
Bloque 2: LAMAÑANA
```

Y un **IV (vector de inicialización)** de 16 bytes aleatorios:

1. Se hace:

   `Bloque1 XOR IV → resultado → cifrar con clave → C1 (primer bloque cifrado)`

2. Luego:

   `Bloque2 XOR C1 → resultado → cifrar con clave → C2`

🔁 Y así con todos los bloques siguientes.

---

### 📦 ¿Qué es el IV?

**IV (Vector de Inicialización)** es como una "semilla aleatoria" que se aplica **solo al primer bloque** para garantizar que incluso si cifras el mismo mensaje otra vez, **el resultado sea diferente**.

> 🔐 Muy importante: **El IV no es secreto**, pero **debe ser aleatorio y único** para cada mensaje.

---

### ✅ Ventajas de CBC

- Evita que bloques iguales produzcan bloques cifrados iguales.
- Mucho más seguro que ECB.
- Ideal para cifrar archivos, contraseñas o textos largos.

### ⚠️ Desventajas

- No se puede paralelizar fácilmente el cifrado.
- Requiere IV.
- Un error en un bloque afecta el siguiente.

---

### 🛠 Instalación del entorno (Python)

Instalamos la librería `pycryptodome`:

```bash
pip install pycryptodome
```

---

### 🧪 Ejemplo completo en Python: AES en modo CBC

```python
from Crypto.Cipher import AES
from Crypto.Util.Padding import pad, unpad
from Crypto.Random import get_random_bytes

# Texto plano
texto = "ATAQUE A LA MAÑANA"
datos = texto.encode()

# Clave AES de 16 bytes (AES-128)
clave = get_random_bytes(16)

# IV de 16 bytes aleatorios
iv = get_random_bytes(16)

# Cifrado
cifrador = AES.new(clave, AES.MODE_CBC, iv)
cifrado = cifrador.encrypt(pad(datos, AES.block_size))

print("Texto cifrado (hex):", cifrado.hex())

# Descifrado
descifrador = AES.new(clave, AES.MODE_CBC, iv)
descifrado = unpad(descifrador.decrypt(cifrado), AES.block_size)

print("Texto descifrado:", descifrado.decode())
```

---

#### 🧾 Salida esperada:

```
Texto cifrado (hex): 3fa21b7c... ← cambia cada vez por el IV
Texto descifrado: ATAQUE A LA MAÑANA
```

---

### 🧠 ¿Qué pasaría si cambiamos una letra?

Supongamos que cambiamos solo una letra del texto original. El resultado cifrado será **completamente diferente**, debido al **encadenamiento de bloques (CBC)**.

---

### 📌 Resumen:

| Concepto                                                 | CBC Mode                           |
| -------------------------------------------------------- | ---------------------------------- |
| Usa IV                                                   | ✅ Sí, obligatorio                 |
| Bloques cifrados iguales si bloques de texto son iguales | ❌ No (más seguro)                 |
| Necesita padding                                         | ✅ Sí                              |
| Se puede paralelizar                                     | ❌ Solo en descifrado              |
| ¿Se recomienda en práctica?                              | ✅ Sí (aunque hoy se prefiere GCM) |

---

### 🎯 Conclusión:

- CBC es mucho más seguro que ECB.
- Muy usado para cifrar archivos, bases de datos o transmisiones.
- Es importante usar un **IV diferente cada vez**.
- El mismo mensaje cifrado dos veces con CBC generará **dos salidas distintas**.

---

[🔼](#índice)

---

## **423. Modos de operación: CFB**

### 🔐 ¿Qué es el modo CFB?

**CFB (Cipher Feedback Mode)** es un **modo de operación** que permite usar un **cifrado por bloques (como AES o DES) para trabajar como si fuera un cifrado por flujo**. Es decir, **procesa los datos en trozos más pequeños (bits o bytes)** en lugar de por bloques enteros, aunque internamente sigue usando bloques.

---

### 📦 ¿Por qué usar CFB?

- Permite cifrar **datos en tiempo real**, como en comunicaciones por red o mensajes de texto.
- No requiere padding, ya que se puede cifrar en segmentos menores al tamaño del bloque (por ejemplo, byte a byte).
- Se puede usar para cifrar **textos de longitud variable**, incluso sin saber el tamaño del mensaje.

---

### 🔁 ¿Cómo funciona el CFB?

#### Supongamos que estamos usando AES de 128 bits (16 bytes) y queremos cifrar un mensaje de 3 bloques:

1. **Inicio**:

   - Usamos un **IV (Vector de Inicialización)** de 16 bytes.
   - El primer paso es cifrar el IV con AES.
   - Luego se toma el resultado y se hace un XOR con el primer bloque del texto plano → se obtiene el primer bloque cifrado.

2. **Después**:

   - El resultado del XOR (el bloque cifrado) **se vuelve a cifrar**, y el resultado se hace XOR con el siguiente bloque de texto plano, y así sucesivamente.

---

#### ✏️ Ejemplo visual (simplificado):

Supongamos:

- Texto plano: `"HOLA"`
- Clave AES: `"clave1234567890"`
- IV: `"IV12345678901234"`

##### Paso 1:

```
Cifrar(IV) → resultado1
resultado1 XOR 'H' → C1
```

##### Paso 2:

```
Cifrar(C1) → resultado2
resultado2 XOR 'O' → C2
```

Y así sucesivamente...

---

### ⚖️ Ventajas y desventajas

| Ventajas                           | Desventajas                            |
| ---------------------------------- | -------------------------------------- |
| No requiere padding                | Los errores de transmisión se propagan |
| Funciona como un cifrado por flujo | Cifrado y descifrado no son simétricos |
| Adecuado para transmisión de datos | Un solo bit alterado daña varios bits  |

---

### 📥 Instalación (en Python)

Usaremos la librería `pycryptodome`, que contiene funciones para AES y CFB.

```bash
pip install pycryptodome
```

---

### ✅ Ejemplo completo: Cifrado y descifrado en modo CFB con AES

```python
from Crypto.Cipher import AES
from Crypto.Random import get_random_bytes

# Texto plano a cifrar
mensaje = b"HOLA MUNDO DESDE CFB"

# Clave de 16 bytes para AES-128
clave = get_random_bytes(16)

# IV (vector de inicialización)
iv = get_random_bytes(16)

# Crear cifrador en modo CFB
cifrador = AES.new(clave, AES.MODE_CFB, iv)

# Cifrado
cifrado = cifrador.encrypt(mensaje)

print("Texto cifrado (hex):", cifrado.hex())

# Crear descifrador con la misma clave e IV
descifrador = AES.new(clave, AES.MODE_CFB, iv)

# Descifrado
descifrado = descifrador.decrypt(cifrado)

print("Texto descifrado:", descifrado.decode())
```

---

#### 💡 Resultado típico:

```
Texto cifrado (hex): 8f2c4a02f7ae19dca9...
Texto descifrado: HOLA MUNDO DESDE CFB
```

> 🔐 **IMPORTANTE:** El mismo texto cifrado con la misma clave, pero con un IV diferente, **genera resultados distintos**, lo cual ayuda a la seguridad.

---

### 🧠 Resumen de CFB

| Característica        | Valor                          |
| --------------------- | ------------------------------ |
| Usa IV                | ✅ Sí                          |
| Requiere padding      | ❌ No                          |
| Puede cifrar flujos   | ✅ Sí (byte a byte)            |
| Propaga errores       | ⚠️ Sí, en los siguientes bytes |
| Se usa en la práctica | ✅ Comunicaciones seguras      |

---

### 📌 Cuándo usar CFB

- Cuando se quiere cifrar texto o datos en tiempo real (mensajería, transmisión de voz).
- Cuando no se conoce de antemano el tamaño total del mensaje.
- En aplicaciones donde no se quiere usar padding (relleno) como en ECB o CBC.

---

[🔼](#índice)

---

## **424. Modos de operación: OFB**

### 🔐 ¿Qué es el modo OFB?

**OFB (Output Feedback)** es un **modo de operación** que convierte un **cifrado por bloques** (como AES) en un **cifrado por flujo**. Es decir, permite cifrar datos poco a poco (byte a byte o bit a bit), sin necesidad de procesar bloques enteros de una sola vez.

---

### ⚙️ ¿Cómo funciona el modo OFB?

A diferencia de otros modos como CBC o CFB, **en OFB el texto cifrado anterior NO se usa como entrada para el siguiente paso**. En cambio, el resultado del **cifrado del bloque anterior** se usa como entrada para el siguiente.

#### Pasos:

1. Se elige un **IV (vector de inicialización)**.
2. El IV se cifra con la clave secreta usando AES (u otro algoritmo).
3. El resultado se llama "salida intermedia" (output feedback).
4. Esa salida se **hace XOR con el texto plano** para obtener el texto cifrado.
5. Luego, se **vuelve a cifrar la salida anterior** (no el texto cifrado) y se repite.

---

### 🧠 Diferencia clave

- En **CFB**, se cifra el texto cifrado anterior.
- En **OFB**, se cifra la **salida cifrada anterior**.

---

### 🔁 Ejemplo conceptual paso a paso:

Supón que queremos cifrar `"HOLA"` con una clave y un IV.

- Texto plano: `H O L A`
- IV: `IV0`
- Clave: `K`

#### Proceso:

1. `S1 = Cifrar(IV0, K)`
2. `C1 = H XOR S1`
3. `S2 = Cifrar(S1, K)`
4. `C2 = O XOR S2`
5. `S3 = Cifrar(S2, K)`
6. `C3 = L XOR S3`
7. ...

---

### ✅ Ventajas de OFB

| Ventaja                       | Descripción                                             |
| ----------------------------- | ------------------------------------------------------- |
| 🔄 Cifrado por flujo          | Puedes cifrar poco a poco, útil para streaming.         |
| ❌ Sin padding                | No necesita rellenar el mensaje para completar bloques. |
| ✅ Sin propagación de errores | Si un bit se daña, solo afecta a ese bit.               |

---

### ⚠️ Desventajas de OFB

| Desventaja                         | Descripción                                                    |
| ---------------------------------- | -------------------------------------------------------------- |
| ❗ Si el IV se repite, es inseguro | Usar el mismo IV con la misma clave puede romper la seguridad. |
| ↩️ No permite cifrado paralelo     | Como cada paso depende del anterior, es más lento en hardware. |

---

### 📥 Instalación (Python)

Usaremos la librería `pycryptodome`.

```bash
pip install pycryptodome
```

---

### 🧪 Ejemplo completo en Python

Cifrar y descifrar un mensaje con **AES en modo OFB**:

```python
from Crypto.Cipher import AES
from Crypto.Random import get_random_bytes

# Texto plano
mensaje = b"Hola desde modo OFB"

# Clave de 16 bytes para AES-128
clave = get_random_bytes(16)

# IV (vector de inicialización) de 16 bytes
iv = get_random_bytes(16)

# Cifrado
cifrador = AES.new(clave, AES.MODE_OFB, iv)
cifrado = cifrador.encrypt(mensaje)
print("Texto cifrado (hex):", cifrado.hex())

# Descifrado (necesita la misma clave e IV)
descifrador = AES.new(clave, AES.MODE_OFB, iv)
descifrado = descifrador.decrypt(cifrado)
print("Texto descifrado:", descifrado.decode())
```

---

#### 🔎 Resultado típico

```
Texto cifrado (hex): 1a4c7e...
Texto descifrado: Hola desde modo OFB
```

---

### 📌 ¿Cuándo usar OFB?

Usa OFB cuando:

- Necesitas cifrar datos **en tiempo real** (como voz o video en streaming).
- Quieres **evitar padding** (relleno).
- Quieres evitar propagación de errores (por ejemplo, en redes inestables).

---

### 🧠 Resumen

| Propiedad                       | Valor |
| ------------------------------- | ----- |
| Usa IV                          | ✅ Sí |
| Padding necesario               | ❌ No |
| Cifrado por flujo               | ✅ Sí |
| Errores se propagan             | ❌ No |
| Cifrado y descifrado simétricos | ✅ Sí |

---

[🔼](#índice)

---

## **425. Modos de operación: CTR**

### 🔐 ¿Qué es el modo CTR?

**CTR (Counter Mode)** es un **modo de operación para cifrados por bloques** (como AES) que transforma el cifrado en **uno de flujo**. A diferencia de modos como ECB o CBC, **CTR es rápido, permite paralelismo y no necesita padding**.

---

### 🧠 ¿Cómo funciona el CTR?

En lugar de cifrar directamente el bloque de texto plano, en **CTR se cifra un contador (counter)**. El resultado se **XORea** con el texto plano para obtener el texto cifrado.

#### 📋 Pasos:

1. Se genera un **Nonce** (valor aleatorio único) y un **contador** que empieza desde 0.
2. Se **cifra el Nonce + contador** con la clave.
3. El resultado se **XORea** con el bloque del texto plano.
4. El contador se incrementa y se repite el proceso.

> 📌 _Nonce = “Number used once” → Nunca debe repetirse con la misma clave._

---

### ✅ Ventajas del modo CTR

| Ventaja                                  | Explicación                                   |
| ---------------------------------------- | --------------------------------------------- |
| 🔁 Cifrado por flujo                     | Puedes cifrar bloques de longitud arbitraria. |
| ⚡ Rápido y paralelizable                | No depende de bloques anteriores.             |
| ❌ No necesita padding                   | Se adapta a cualquier longitud.               |
| 🔄 Mismo proceso para cifrar y descifrar | Solo se hace XOR.                             |

---

### ⚠️ Desventajas

| Desventaja                                  | Explicación                                              |
| ------------------------------------------- | -------------------------------------------------------- |
| ❗ Si se repite el Nonce + clave → inseguro | Dos mensajes con el mismo nonce y clave pueden romperse. |
| 📦 Requiere sincronización                  | Ambos extremos deben conocer el mismo contador y nonce.  |

---

### 🔁 Ejemplo paso a paso (conceptual)

Supón que queremos cifrar `"HOLA"` con una clave `K` y un Nonce `N`.

- Paso 1: Contador = 0 → Entrada = N + 0
- Paso 2: Salida = AES(K, Entrada)
- Paso 3: `C1 = H XOR AES(K, N+0)`

Repetimos para cada bloque:

- `C2 = O XOR AES(K, N+1)`
- `C3 = L XOR AES(K, N+2)`
- `C4 = A XOR AES(K, N+3)`

---

### 🧰 Instalación (en Python)

Usaremos la librería `pycryptodome` para usar AES en modo CTR:

```bash
pip install pycryptodome
```

---

### 🧪 Ejemplo completo en Python (cifrado y descifrado)

```python
from Crypto.Cipher import AES
from Crypto.Random import get_random_bytes
from Crypto.Util import Counter

# Texto plano
mensaje = b"Hola desde modo CTR en AES"

# Clave de 16 bytes para AES-128
clave = get_random_bytes(16)

# Nonce de 8 bytes (importante: debe ser único por clave)
nonce = get_random_bytes(8)

# Creamos el contador con el nonce
contador = Counter.new(64, prefix=nonce)

# Cifrado
cifrador = AES.new(clave, AES.MODE_CTR, counter=contador)
cifrado = cifrador.encrypt(mensaje)
print("Texto cifrado (hex):", cifrado.hex())

# Para descifrar, reiniciamos el contador con el mismo nonce
contador_dec = Counter.new(64, prefix=nonce)
descifrador = AES.new(clave, AES.MODE_CTR, counter=contador_dec)
descifrado = descifrador.decrypt(cifrado)
print("Texto descifrado:", descifrado.decode())
```

---

### 🔎 Resultado esperado:

```
Texto cifrado (hex): 4f1e9a2a...
Texto descifrado: Hola desde modo CTR en AES
```

---

### 📌 ¿Cuándo usar CTR?

Usa CTR cuando:

- Necesitas **altísimo rendimiento** (cifrado en paralelo).
- No quieres lidiar con **padding**.
- Quieres cifrar **grandes volúmenes de datos** rápidamente (por ejemplo, en discos o VPNs).

---

### 🧠 Resumen final

| Propiedad           | CTR                                |
| ------------------- | ---------------------------------- |
| Padding necesario   | ❌ No                              |
| Cifrado por bloques | ✅ Sí, pero se comporta como flujo |
| Paralelismo         | ✅ Sí                              |
| Errores se propagan | ❌ No                              |
| Uso común           | VPNs, discos, protocolos modernos  |

---

[🔼](#índice)

---

## **426. Cuándo usar criptosistemas simétricos**

### 🔐 ¿Qué es un criptosistema simétrico?

Un **criptosistema simétrico** es un sistema de cifrado donde **la misma clave se usa tanto para cifrar como para descifrar**.

#### 📌 Ejemplos populares:

- **AES** (Advanced Encryption Standard)
- **DES** y **Triple DES**
- **ChaCha20**
- **RC4** (ya no recomendado)

---

### ✅ ¿Cuándo usar criptosistemas simétricos?

#### 🔒 **Cuando ambos extremos confían y pueden compartir una clave secreta**

- Ideal en sistemas **cerrados** o **controlados** (como una empresa o un servidor con sus clientes autorizados).

📦 **Ejemplo**: un banco que transmite datos entre su base de datos y su sistema interno.

---

#### ⚡ **Cuando se necesita velocidad y eficiencia**

- Los criptosistemas simétricos son **mucho más rápidos** que los asimétricos (como RSA).

📦 **Ejemplo**: cifrado de discos duros o transmisión de video en tiempo real.

---

#### 📁 **Cuando se manejan grandes volúmenes de datos**

- Son más eficientes para cifrar **archivos grandes**, como backups, archivos multimedia, logs, etc.

📦 **Ejemplo**: servicios de almacenamiento como Google Drive o Dropbox cifran archivos en sus servidores usando AES.

---

#### 🧩 **Cuando se combina con criptografía asimétrica**

- En muchas aplicaciones, se usa un **sistema híbrido**:

  - El canal se asegura con criptografía asimétrica (como TLS/SSL),
  - Luego, se establece una clave simétrica para el resto de la sesión.

📦 **Ejemplo**: HTTPS en navegadores.

---

### ❌ ¿Cuándo NO usar criptosistemas simétricos?

| Situación                                       | ¿Por qué no es ideal?                                                                   |
| ----------------------------------------------- | --------------------------------------------------------------------------------------- |
| 🔑 No puedes compartir la clave de forma segura | No hay forma de que ambos extremos obtengan la clave sin que un atacante la intercepte. |
| 👥 Comunicación abierta entre desconocidos      | No se puede confiar en que todos manejen la misma clave secreta.                        |
| 🔐 Necesitas autenticación del emisor           | No puedes saber _quién_ cifró el mensaje (a diferencia de firmas digitales).            |

---

### 📦 Instalación y uso en Python (con `pycryptodome`)

#### Instalación:

```bash
pip install pycryptodome
```

---

### 🧪 Ejemplo completo: cifrado y descifrado con AES

Vamos a cifrar un mensaje con **AES en modo CBC**, un modo simétrico muy utilizado.

```python
from Crypto.Cipher import AES
from Crypto.Random import get_random_bytes
from Crypto.Util.Padding import pad, unpad

# Mensaje a cifrar
mensaje = b"Mensaje secreto que vamos a cifrar"

# Clave de 16 bytes (128 bits)
clave = get_random_bytes(16)

# IV (vector de inicialización) de 16 bytes
iv = get_random_bytes(16)

# Crear objeto AES en modo CBC
cifrador = AES.new(clave, AES.MODE_CBC, iv)

# Cifrar el mensaje (lo rellenamos para que sea múltiplo de 16)
cifrado = cifrador.encrypt(pad(mensaje, AES.block_size))

print("Texto cifrado (hex):", cifrado.hex())

# Para descifrar, usamos la misma clave e IV
descifrador = AES.new(clave, AES.MODE_CBC, iv)
descifrado = unpad(descifrador.decrypt(cifrado), AES.block_size)

print("Texto descifrado:", descifrado.decode())
```

#### 🔎 Resultado esperado:

```
Texto cifrado (hex): 2e1ab7f3...
Texto descifrado: Mensaje secreto que vamos a cifrar
```

---

### 📌 Resumen Final

| Situación ideal para usar criptosimetría | Ejemplo                    |
| ---------------------------------------- | -------------------------- |
| Comunicación interna en redes confiables | Intranet de una empresa    |
| Grandes volúmenes de datos               | Cifrado de discos, backups |
| Velocidad necesaria                      | Streaming, VPN             |
| Sesión segura tras autenticación pública | HTTPS con AES              |

---

[🔼](#índice)

---

## **427. Criptosistemas asimétricos o de clave pública**

### 🔐 ¿Qué es un criptosistema asimétrico?

Un **criptosistema asimétrico** usa **dos claves diferentes**:

- 🔑 **Clave pública**: se comparte con cualquiera.
- 🔐 **Clave privada**: se guarda en secreto.

Estas claves están **matemáticamente relacionadas**, pero **no puedes obtener la privada a partir de la pública** (al menos no fácilmente).

---

### 📤 ¿Cómo funciona?

1. **Cifrado:**

   - El emisor **usa la clave pública del receptor** para cifrar el mensaje.
   - Solo el receptor, con su **clave privada**, puede descifrarlo.

2. **Firmas digitales:**

   - El emisor **firma** con su **clave privada**.
   - Cualquiera puede verificar la firma usando la **clave pública** del emisor.

---

### 🎯 ¿Cuándo se usa?

- Cuando **dos personas no se conocen**, pero quieren comunicarse de forma segura.
- Cuando se necesita **autenticidad y no repudio** (firmas digitales).
- Para **intercambiar claves simétricas** de forma segura (ej. HTTPS).

---

### 🧠 Ejemplo fácil

Imagina que María quiere enviarle un mensaje a Juan:

- Juan genera un **par de claves**:

  🔐 clave privada → guarda en secreto

  🔑 clave pública → se la da a María

- María **cifra el mensaje** con la **clave pública de Juan**.

- Solo **Juan** puede **descifrarlo** con su **clave privada**.

---

### 🛠️ Instalación en Python

Vamos a usar la librería `cryptography`.

#### 📦 Instalación:

```bash
pip install cryptography
```

---

### 🧪 Ejemplo completo paso a paso

#### 🔧 1. Generar claves pública y privada

```python
from cryptography.hazmat.primitives.asymmetric import rsa
from cryptography.hazmat.primitives import serialization

# Generar clave privada
clave_privada = rsa.generate_private_key(
    public_exponent=65537,
    key_size=2048
)

# Extraer clave pública
clave_publica = clave_privada.public_key()

# Mostrar en formato PEM
clave_privada_pem = clave_privada.private_bytes(
    encoding=serialization.Encoding.PEM,
    format=serialization.PrivateFormat.TraditionalOpenSSL,
    encryption_algorithm=serialization.NoEncryption()
)

clave_publica_pem = clave_publica.public_bytes(
    encoding=serialization.Encoding.PEM,
    format=serialization.PublicFormat.SubjectPublicKeyInfo
)

print("Clave privada:\n", clave_privada_pem.decode())
print("Clave pública:\n", clave_publica_pem.decode())
```

---

#### 🔐 2. Cifrar un mensaje con la clave pública

```python
from cryptography.hazmat.primitives.asymmetric import padding
from cryptography.hazmat.primitives import hashes

mensaje = b"Hola Juan, este es un mensaje secreto."

# Cifrado
mensaje_cifrado = clave_publica.encrypt(
    mensaje,
    padding.OAEP(
        mgf=padding.MGF1(algorithm=hashes.SHA256()),
        algorithm=hashes.SHA256(),
        label=None
    )
)

print("Mensaje cifrado:", mensaje_cifrado.hex())
```

---

#### 🔓 3. Descifrar el mensaje con la clave privada

```python
mensaje_descifrado = clave_privada.decrypt(
    mensaje_cifrado,
    padding.OAEP(
        mgf=padding.MGF1(algorithm=hashes.SHA256()),
        algorithm=hashes.SHA256(),
        label=None
    )
)

print("Mensaje descifrado:", mensaje_descifrado.decode())
```

---

### 📌 Resumen de ventajas

| Ventaja                                       | Explicación                                  |
| --------------------------------------------- | -------------------------------------------- |
| 🔑 No es necesario compartir la clave privada | Solo se comparte la clave pública            |
| 🔒 Seguridad para iniciar comunicaciones      | Aunque no haya confianza previa              |
| 🧾 Firmas digitales                           | Permite verificar identidad y evitar repudio |
| 🔁 Combinación con criptografía simétrica     | Ej. HTTPS, SSH, VPN, etc.                    |

---

### ⚠️ Desventajas

- Más **lento** que los sistemas simétricos.
- Requiere gestión de **pares de claves**.
- No es práctico para **cifrar archivos grandes directamente**.

---

### 📚 Ejemplo en la vida real

- **Correo seguro**: GPG o PGP usa claves públicas para que cualquiera pueda enviarte un mensaje cifrado.
- **HTTPS (SSL/TLS)**: tu navegador cifra la conexión usando la clave pública del servidor.
- **Firmas digitales de software**: aseguran que un programa no fue modificado.

---

[🔼](#índice)

---

## **428. Diffie Hellman: Intercambio de claves**

### 🔐 ¿Qué es Diffie-Hellman?

El **intercambio de claves Diffie-Hellman** es un **protocolo criptográfico** que permite a **dos partes** (por ejemplo, Alicia y Bob) acordar **una clave secreta compartida**, **sin necesidad de enviarla directamente** por el canal inseguro.

> 📌 Importante: **Diffie-Hellman no cifra mensajes directamente.** Solo sirve para **acordar una clave secreta** que luego se puede usar para cifrar comunicaciones con algoritmos simétricos como AES.

---

### 🧠 ¿Por qué es útil?

Imagina que Alicia y Bob quieren hablar de forma segura por internet. No tienen una clave previa. Usando Diffie-Hellman, pueden generar **cada uno una parte del secreto**, intercambiar valores **públicos**, y aún así **terminar con la misma clave secreta**.

---

### 🧮 Ejemplo fácil con colores (metáfora visual)

1. Ambos eligen un **color público base** (como el número primo `p`) y una **técnica de mezcla** (como la base `g`).
2. Alicia elige un **color secreto privado** (clave privada `a`) y mezcla.
3. Bob también elige uno.
4. Ambos **intercambian sus mezclas** (valores públicos).
5. Cada uno mezcla lo recibido con su secreto privado.
6. ¡Ambos obtienen el mismo color final (clave secreta)!

---

### 📐 Parte matemática real

Se basa en la **aritmética modular**.

#### Parámetros públicos:

- `p`: número primo grande
- `g`: generador (número menor que `p`)

#### Cada parte:

- Elige un número secreto:

  - Alicia: `a`
  - Bob: `b`

- Calcula:

  - Alicia envía `A = g^a mod p`
  - Bob envía `B = g^b mod p`

- Ambos calculan la clave compartida:

  - Alicia: `s = B^a mod p`
  - Bob: `s = A^b mod p`

- Ambos obtienen el **mismo resultado `s`**.

---

### 🛠️ ¿Cómo se instala?

Usaremos Python con la biblioteca `cryptography`, que ya viene con soporte para **Diffie-Hellman**.

#### ✅ Instalación

```bash
pip install cryptography
```

---

### 🧪 Ejemplo completo en Python (paso a paso)

```python
from cryptography.hazmat.primitives.asymmetric import dh
from cryptography.hazmat.primitives import serialization, hashes
from cryptography.hazmat.primitives.kdf.hkdf import HKDF

# 1. Generar parámetros (esto sería público: p y g)
parametros = dh.generate_parameters(generator=2, key_size=2048)

# 2. Cada parte genera su clave privada y pública
# ALICE
clave_privada_alice = parametros.generate_private_key()
clave_publica_alice = clave_privada_alice.public_key()

# BOB
clave_privada_bob = parametros.generate_private_key()
clave_publica_bob = clave_privada_bob.public_key()

# 3. Cada parte genera la clave compartida
clave_compartida_alice = clave_privada_alice.exchange(clave_publica_bob)
clave_compartida_bob = clave_privada_bob.exchange(clave_publica_alice)

# 4. Usamos HKDF para derivar una clave simétrica segura a partir de la compartida
def derivar_clave(clave_compartida):
    return HKDF(
        algorithm=hashes.SHA256(),
        length=32,
        salt=None,
        info=b'intercambio de claves DH',
    ).derive(clave_compartida)

clave_simetrica_alice = derivar_clave(clave_compartida_alice)
clave_simetrica_bob = derivar_clave(clave_compartida_bob)

# 5. Verificamos que ambas claves coincidan
print("¿Claves coinciden?:", clave_simetrica_alice == clave_simetrica_bob)
print("Clave secreta compartida (hex):", clave_simetrica_alice.hex())
```

---

### 📌 ¿Qué logramos?

Ambas partes (Alicia y Bob):

✅ Generaron una clave secreta compartida sin necesidad de enviarla directamente

✅ Esa clave ahora puede usarse para cifrar información (ej. con AES)

✅ Si un atacante observa todo el intercambio, **no puede calcular la clave secreta** (esto se basa en el problema del logaritmo discreto)

---

### 🧱 Resumen Visual

```text
   Paso            Alicia                  Bob
   ----           -------                -------
    1        Clave privada: a         Clave privada: b
    2        Calcula A = g^a mod p    Calcula B = g^b mod p
    3        Envia A a Bob            Envia B a Alicia
    4        Calcula s = B^a mod p    Calcula s = A^b mod p
           => Clave compartida secreta s (misma para ambos)
```

---

### 🛑 Limitaciones

- No tiene autenticación por sí solo (puede ser vulnerable a "man-in-the-middle").
- Se combina normalmente con **firmas digitales** para autenticar a las partes (como en TLS).

---

[🔼](#índice)

---

## **429. RSA**

### 🔐 ¿Qué es RSA?

**RSA** es un algoritmo de **criptografía asimétrica**. Se usa para:

- **Cifrado**: Proteger mensajes con una clave pública.
- **Firmas digitales**: Validar la identidad del remitente con una clave privada.

#### 📌 ¿Qué significa asimétrica?

Significa que usa **dos claves diferentes**:

- 🔓 **Clave pública**: Se comparte con todos. Sirve para cifrar.
- 🔒 **Clave privada**: Se guarda en secreto. Sirve para descifrar.

> Si alguien cifra con tu clave pública, **solo tú** puedes descifrarlo con tu clave privada.
>
> Si tú firmas algo con tu clave privada, **todos pueden verificarlo** con tu clave pública.

---

### 🧠 ¿Cómo funciona RSA (en sencillo)?

RSA se basa en **matemáticas con números primos muy grandes**. Aquí están los pasos principales:

#### 1. Generar claves

- Se eligen dos números primos grandes `p` y `q`.
- Se calcula `n = p * q`.
- Se calcula `φ(n) = (p - 1) * (q - 1)`.
- Se elige un número `e` (clave pública) que no tenga factores comunes con `φ(n)`.
- Se calcula `d` (clave privada), tal que:
  `d * e ≡ 1 (mod φ(n))`

#### 2. Claves

- Clave **pública**: `(e, n)`
- Clave **privada**: `(d, n)`

#### 3. Cifrado

Para cifrar un número `m`:

```text
c = m^e mod n
```

#### 4. Descifrado

Para descifrar `c`:

```text
m = c^d mod n
```

---

### 🧮 Ejemplo numérico miniatura (muy pequeño)

#### 1. Elegimos primos:

```text
p = 3, q = 11 → n = 33
φ(n) = (3-1)(11-1) = 20
```

#### 2. Elegimos `e = 3` (debe ser primo con 20)

#### 3. Calculamos `d` tal que:

```text
d * 3 ≡ 1 mod 20 → d = 7
```

#### 4. Claves:

- Pública: `(e=3, n=33)`
- Privada: `(d=7, n=33)`

#### 5. Cifrado de `m=4`:

```text
c = 4^3 mod 33 = 64 mod 33 = 31
```

#### 6. Descifrado:

```text
m = 31^7 mod 33 = 4
```

✅ ¡Se recupera el mensaje original!

---

### ⚙️ Instalación en Python

Vamos a usar `cryptography` o `PyCryptodome`.

#### Opción 1: `cryptography`

```bash
pip install cryptography
```

#### Opción 2: `pycryptodome` (alternativa potente)

```bash
pip install pycryptodome
```

---

### 🧪 Ejemplo completo con `cryptography` (moderno y seguro)

```python
from cryptography.hazmat.primitives.asymmetric import rsa, padding
from cryptography.hazmat.primitives import hashes

# 1. Generar par de claves
clave_privada = rsa.generate_private_key(public_exponent=65537, key_size=2048)
clave_publica = clave_privada.public_key()

# 2. Mensaje a cifrar
mensaje = b"Hola mundo secreto"

# 3. Cifrar con la clave pública
mensaje_cifrado = clave_publica.encrypt(
    mensaje,
    padding.OAEP(
        mgf=padding.MGF1(algorithm=hashes.SHA256()),
        algorithm=hashes.SHA256(),
        label=None
    )
)

# 4. Descifrar con la clave privada
mensaje_descifrado = clave_privada.decrypt(
    mensaje_cifrado,
    padding.OAEP(
        mgf=padding.MGF1(algorithm=hashes.SHA256()),
        algorithm=hashes.SHA256(),
        label=None
    )
)

# 5. Mostrar resultados
print("Mensaje original:", mensaje)
print("Cifrado (hex):", mensaje_cifrado.hex())
print("Descifrado:", mensaje_descifrado)
```

---

### 📌 Resumen Visual

```text
              CLAVE PÚBLICA (e, n)               CLAVE PRIVADA (d, n)
                      ↓                                   ↓
Emisor cifra:    c = m^e mod n         Receptor descifra: m = c^d mod n
```

---

### 🔐 ¿Para qué se usa RSA?

✅ Intercambio seguro de claves (ej: en HTTPS/TLS)

✅ Firmas digitales (validar identidad)

✅ Autenticación en tokens (como JWT en web)

✅ Encriptación de mensajes pequeños o claves

---

### 🛑 Limitaciones

- Lento para mensajes grandes (por eso se usa solo para **intercambiar claves**, no para cifrar archivos completos)
- Vulnerable si se usan claves pequeñas o sin padding
- Siempre debe usarse con padding seguro como **OAEP** o **PSS**

---

[🔼](#índice)

---

## **430. Generando un par de claves RSA con OpenSSL**

### 🔐 ¿Qué es un par de claves RSA?

En criptografía **RSA**, usamos dos claves:

- 🔓 **Clave pública**: Para cifrar o verificar firmas.
- 🔒 **Clave privada**: Para descifrar o firmar datos.

El par de claves se genera al mismo tiempo, y están matemáticamente relacionadas, pero es imposible (prácticamente) obtener la clave privada solo con la pública.

---

### 🧰 ¿Qué es OpenSSL?

**OpenSSL** es una herramienta de línea de comandos de código abierto que permite hacer operaciones de criptografía como:

- Generar claves (RSA, ECC, etc.)
- Cifrar y descifrar mensajes
- Crear certificados digitales
- Firmar archivos
- Verificar firmas

---

### ⚙️ Cómo instalar OpenSSL

#### En Windows

1. Ve a: [https://slproweb.com/products/Win32OpenSSL.html](https://slproweb.com/products/Win32OpenSSL.html)
2. Descarga e instala **Win64 OpenSSL** o **Win32 OpenSSL** (según tu sistema).
3. Durante la instalación, selecciona la opción que agregue OpenSSL al PATH.

Luego, abre la terminal `cmd` o PowerShell y escribe:

```bash
openssl version
```

Debe salir algo como:

```
OpenSSL 3.x.x ...
```

---

#### En Linux (Ubuntu/Debian)

```bash
sudo apt update
sudo apt install openssl
```

#### En macOS

```bash
brew install openssl
```

---

### 🛠️ Generando un par de claves RSA

Vamos a usar la terminal paso a paso.

---

#### ✅ Paso 1: Generar clave privada

```bash
openssl genpkey -algorithm RSA -out clave_privada.pem -pkeyopt rsa_keygen_bits:2048
```

Esto genera una clave privada de 2048 bits y la guarda en `clave_privada.pem`.

📌 **Nota:** Puedes usar 4096 bits para más seguridad (pero es más lento).

---

#### ✅ Paso 2: Extraer clave pública desde la privada

```bash
openssl rsa -pubout -in clave_privada.pem -out clave_publica.pem
```

Esto lee la clave privada y genera la clave pública correspondiente en `clave_publica.pem`.

---

#### ✅ Paso 3 (opcional): Ver el contenido de las claves

**Clave privada:**

```bash
openssl pkey -in clave_privada.pem -text -noout
```

**Clave pública:**

```bash
openssl pkey -pubin -in clave_publica.pem -text -noout
```

---

### 📦 Archivos generados

- `clave_privada.pem` → contiene la clave **privada**
- `clave_publica.pem` → contiene la clave **pública**

Estos archivos están codificados en formato **PEM** (texto Base64), que es compatible con muchos sistemas.

---

### 🧪 Ejemplo completo: Cifrar y descifrar un mensaje

#### Paso 1: Crear un mensaje de prueba

```bash
echo "Este es un mensaje secreto" > mensaje.txt
```

---

#### Paso 2: Cifrar el mensaje con la **clave pública**

```bash
openssl pkeyutl -encrypt -in mensaje.txt -pubin -inkey clave_publica.pem -out mensaje_cifrado.bin
```

Esto crea un archivo binario cifrado `mensaje_cifrado.bin`.

---

#### Paso 3: Descifrar con la **clave privada**

```bash
openssl pkeyutl -decrypt -in mensaje_cifrado.bin -inkey clave_privada.pem -out mensaje_descifrado.txt
```

---

#### Paso 4: Leer el mensaje descifrado

```bash
cat mensaje_descifrado.txt
```

Deberías ver:

```
Este es un mensaje secreto
```

✅ ¡Mensaje cifrado y descifrado correctamente con RSA y OpenSSL!

---

### 📌 Resumen

| Acción                | Comando                                                                |
| --------------------- | ---------------------------------------------------------------------- |
| Generar clave privada | `openssl genpkey -algorithm RSA -out clave_privada.pem`                |
| Extraer clave pública | `openssl rsa -pubout -in clave_privada.pem -out clave_publica.pem`     |
| Cifrar mensaje        | `openssl pkeyutl -encrypt -pubin -inkey clave_publica.pem -in msg.txt` |
| Descifrar mensaje     | `openssl pkeyutl -decrypt -inkey clave_privada.pem -in msg_cifrado`    |

---

[🔼](#índice)

---

## **431. Curvas elípticas**

### 🔍 ¿Qué son las curvas elípticas?

En criptografía, las **curvas elípticas** no son "curvas elípticas" como elipses comunes, sino **curvas definidas por una ecuación algebraica específica** que tiene una forma como esta:

$$
y^2 = x^3 + ax + b
$$

📌 Estas curvas están definidas sobre un conjunto finito (un campo), como los números módulo un primo (por ejemplo, $\mathbb{F}_p$).

---

#### 🎯 ¿Por qué se usan en criptografía?

Las curvas elípticas se usan porque permiten crear sistemas criptográficos:

- Muy seguros
- Con **claves mucho más pequeñas** que RSA
- Rápidos en dispositivos con poca potencia (teléfonos, tarjetas inteligentes)

> 📊 Por ejemplo: ECC con 256 bits ≈ seguridad de RSA con 3072 bits.

---

### 🧠 ¿Cómo se usa una curva elíptica para criptografía?

Se basa en un problema difícil: el **Problema del Logaritmo Discreto en Curvas Elípticas (ECDLP)**.

#### En palabras simples:

1. Se escoge un **punto base G** en la curva.
2. El usuario elige un número secreto **k**.
3. Luego, se multiplica:

   $$
   P = k \cdot G
   $$

   Donde $P$ es **público**, y $k$ es la **clave privada**.

🔐 Calcular $P$ es fácil, pero dado $P$ y $G$, encontrar $k$ es prácticamente imposible.

---

### 🧰 Herramientas para trabajar con ECC

La mayoría de herramientas modernas ya soportan criptografía de curvas elípticas.

Usaremos:

#### 🟦 OpenSSL

Para generar claves, firmar y verificar con ECC.

---

### ⚙️ Instalación de OpenSSL (si aún no lo tienes)

#### En Ubuntu/Debian

```bash
sudo apt update
sudo apt install openssl
```

#### En Windows

- Ve a [https://slproweb.com/products/Win32OpenSSL.html](https://slproweb.com/products/Win32OpenSSL.html)
- Descarga e instala la versión recomendada.
- Agrega OpenSSL al **PATH** para usarlo desde la terminal (`cmd` o PowerShell).

---

### 🛠️ Ejemplo completo: ECC en OpenSSL

#### ✅ Paso 1: Generar una clave privada ECC

Usaremos la curva `prime256v1` (muy común).

```bash
openssl ecparam -name prime256v1 -genkey -noout -out ecc_priv.pem
```

Esto crea una clave privada ECC en el archivo `ecc_priv.pem`.

---

#### ✅ Paso 2: Generar la clave pública

```bash
openssl ec -in ecc_priv.pem -pubout -out ecc_pub.pem
```

Esto genera la clave pública a partir de la clave privada.

---

#### ✅ Paso 3: Crear un mensaje a firmar

```bash
echo "Este es un mensaje firmado con ECC" > mensaje.txt
```

---

#### ✅ Paso 4: Firmar el mensaje con la clave privada

```bash
openssl dgst -sha256 -sign ecc_priv.pem -out firma.bin mensaje.txt
```

Esto genera una **firma binaria** del archivo `mensaje.txt`.

---

#### ✅ Paso 5: Verificar la firma con la clave pública

```bash
openssl dgst -sha256 -verify ecc_pub.pem -signature firma.bin mensaje.txt
```

Resultado esperado:

```
Verified OK
```

---

### 📦 Archivos generados

- `ecc_priv.pem`: Clave privada ECC
- `ecc_pub.pem`: Clave pública ECC
- `mensaje.txt`: Mensaje a firmar
- `firma.bin`: Firma digital del mensaje

---

### 📌 Comparación rápida: ECC vs RSA

| Característica        | RSA (2048 bits) | ECC (256 bits)                        |
| --------------------- | --------------- | ------------------------------------- |
| Seguridad equivalente | 112 bits        | 112 bits                              |
| Tamaño de clave       | Grande          | Mucho más pequeña                     |
| Rendimiento           | Lento           | Rápido                                |
| Uso recomendado       | General         | Ideal para dispositivos móviles o IoT |

---

### 🧠 En resumen

- ECC usa operaciones matemáticas sobre curvas para crear claves.
- Es tan seguro como RSA, pero con **menos consumo de recursos**.
- Herramientas como **OpenSSL** permiten generar claves, firmar y verificar fácilmente.

---

[🔼](#índice)

---

## **432. Computación cuántica: Un viaje hacia una nueva era en la criptografía**

![Computación cuántica](../img/6_Ciberseguridad_Defensiva/Computacion_cuantica.avif "Computación cuántica")

### 🌐 1. Introducción sencilla: ¿Qué es la computación cuántica?

La **computación cuántica** es una nueva forma de procesar información **usando las leyes de la física cuántica**. A diferencia de las computadoras tradicionales (clásicas) que usan bits (0 o 1), las computadoras cuánticas usan **qubits**, que pueden estar en **0, 1 o ambos a la vez** gracias a algo llamado **superposición**.

---

#### 🧠 Conceptos clave:

- **Qubit**: Unidad básica de la computación cuántica (como el bit clásico, pero más poderoso).
- **Superposición**: Un qubit puede representar 0 y 1 al mismo tiempo.
- **Entrelazamiento (entanglement)**: Qubits que están conectados de manera que lo que le pase a uno afecta al otro.
- **Interferencia**: Los resultados no deseados pueden "cancelarse" y reforzar los que sí queremos.

---

### 🔐 2. ¿Qué tiene que ver esto con la criptografía?

¡Mucho!

La criptografía moderna (como RSA, ECC, Diffie-Hellman) **depende de que ciertos cálculos sean difíciles para una computadora clásica**. Por ejemplo:

- **RSA**: Difícil factorizar números muy grandes.
- **ECC**: Difícil resolver logaritmos discretos en curvas elípticas.

Sin embargo, **una computadora cuántica suficientemente potente puede romper estos sistemas** con algoritmos cuánticos especiales.

---

#### 📉 Criptografía vulnerable con computación cuántica

| Algoritmo clásico | Algoritmo cuántico que lo rompe        | ¿Seguridad en peligro? |
| ----------------- | -------------------------------------- | ---------------------- |
| RSA               | **Shor** (factorización)               | ❌ Sí                  |
| Diffie-Hellman    | **Shor**                               | ❌ Sí                  |
| ECC               | **Shor**                               | ❌ Sí                  |
| AES / Symétricos  | **Grover** (reducción de fuerza bruta) | ⚠️ Parcialmente        |

🔐 **AES**, aunque es afectado, **no está roto**, solo hay que **doblar el tamaño de la clave** para mantener la seguridad.

---

### 🧪 3. ¿Qué es la criptografía post-cuántica?

Es una rama de la criptografía que **diseña algoritmos resistentes a ataques cuánticos**. Se basa en problemas matemáticos que no pueden resolverse eficientemente, ni siquiera con una computadora cuántica.

📌 Algunos candidatos:

- **Lattice-based** (basado en retículos): como Kyber, NTRU
- **Code-based**: como McEliece
- **Hash-based**: como SPHINCS+
- **Multivariable**: basados en polinomios

💡 **NIST (EE.UU.)** ya está estandarizando criptografía post-cuántica (PQCrypto).

---

### ⚙️ 4. ¿Cómo experimentar con criptografía cuántica o post-cuántica?

#### 🔧 Instalación y uso (con ejemplo)

Usaremos la biblioteca **`pqcrypto`** en Python para probar algoritmos post-cuánticos.

#### ✅ Requisitos:

- Python 3.8+
- pip

---

#### 🛠️ Instalación:

```bash
pip install pqcrypto
```

---

#### 👨‍💻 Ejemplo completo: Cifrado con Kyber512 (post-cuántico)

```python
from pqcrypto.kem.kyber512 import generate_keypair, encrypt, decrypt

# Generar par de claves
public_key, secret_key = generate_keypair()

# Simular envío de clave secreta
ciphertext, shared_secret_enc = encrypt(public_key)

# Receptor descifra el mensaje
shared_secret_dec = decrypt(ciphertext, secret_key)

# Mostrar resultados
print("Clave secreta cifrada:", shared_secret_enc.hex())
print("Clave secreta descifrada:", shared_secret_dec.hex())
print("¿Coinciden?:", shared_secret_enc == shared_secret_dec)
```

---

🔍 Este ejemplo demuestra **cómo un emisor y receptor** pueden compartir una clave secreta de forma segura usando un algoritmo resistente a ataques cuánticos.

---

### 🚀 5. ¿En qué estado está la computación cuántica hoy?

🔹 Las computadoras cuánticas **ya existen**, pero con pocos qubits y muy **ruidosas**.
🔹 Empresas como IBM, Google, Microsoft y startups cuánticas están desarrollándolas.
🔹 Todavía no pueden romper RSA, pero **en 10–20 años**, podrían hacerlo.

---

### 🧭 6. ¿Qué debemos hacer ahora?

- **Adoptar criptografía post-cuántica** poco a poco (por ejemplo, en nuevas aplicaciones).
- **Hacer auditorías de sistemas actuales** que dependen de RSA o ECC.
- Estar informados sobre los estándares del NIST.

---

### 🧠 En resumen:

| Término              | Explicación fácil                                |
| -------------------- | ------------------------------------------------ |
| Computadora cuántica | Usa física cuántica para cálculos increíbles     |
| Qubit                | Bit cuántico que puede ser 0 y 1 al mismo tiempo |
| Shor                 | Algoritmo que rompe RSA, ECC                     |
| Grover               | Acelera fuerza bruta, afecta AES                 |
| Criptografía PQ      | Diseñada para resistir ataques cuánticos         |

---

[🔼](#índice)

---

| **Inicio**         | **atrás 2**                                               | **Siguiente 4**                                         |
| ------------------ | --------------------------------------------------------- | ------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./6_2_Criptografia_y_Ciberseguridad_Introduccion.md) | [⏩](./6_4_CiberSeguridad_de_los_datos_Data_Scurity.md) |
