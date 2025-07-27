| **Inicio**         | **Siguiente 2**                                                           |
| ------------------ | ------------------------------------------------------------------------- |
| [🏠](../README.md) | [⏩](./4_2_Investigacion_de_fuentes_abiertas_OSINT_con_Python_Hacking.md) |

---

## **Índice**

| Temario                                                                                                                                          |
| ------------------------------------------------------------------------------------------------------------------------------------------------ |
| [152. Entornos virtuales en Python](#152-entornos-virtuales-en-python)                                                                           |
| [153. Hacking con buscadores con Python](#153-hacking-con-buscadores-con-python)                                                                 |
| [154. Operadores y keywords Google Hacking](#154-operadores-y-keywords-google-hacking)                                                           |
| [155. DuckDuckGo Hacking](#155-duckduckgo-hacking)                                                                                               |
| [156. Ejecución de scripts en Python](#156-ejecución-de-scripts-en-python)                                                                       |
| [157. Argumentos en línea de comandos: Argparse](#157-argumentos-en-línea-de-comandos-argparse)                                                  |
| [158. Generación de resultados: JSON, HTML, Consola](#158-generación-de-resultados-json-html-consola)                                            |
| [159. Manejo de ficheros: Descarga, Lectura y Escritura](#159-manejo-de-ficheros-descarga-lectura-y-escritura)                                   |
| [160. Inteligencia Artificial aplicada a Hacking Ético y Ciberseguridad](#160-inteligencia-artificial-aplicada-a-hacking-ético-y-ciberseguridad) |
| [161. Potenciando los Dorks con Inteligencia Artificial](#161-potenciando-los-dorks-con-inteligencia-artificial)                                 |
| [162. OpenAI, GPT-4 y ChatGPT-4](#162-openai-gpt-4-y-chatgpt-4)                                                                                  |
| [163. Potenciando los Dorks con GPT-4](#163-potenciando-los-dorks-con-gpt-4)                                                                     |
| [164. Google Hacking con Inteligencia Artificial](#164-google-hacking-con-inteligencia-artificial)                                               |
| [165. Filtrado de información con Expresiones Regulares](#165-filtrado-de-información-con-expresiones-regulares)                                 |
| [166. Filtrado de información con Inteligencia Artificial](#166-filtrado-de-información-con-inteligencia-artificial)                             |
| [167. Integra SmartSearch con NinjaDork](#167-integra-smartsearch-con-ninjadork)                                                                 |
| [168. Emulando el comportamiento humano con Selenium](#168-emulando-el-comportamiento-humano-con-selenium)                                       |
| [169. Hacking con buscadores automático con Selenium](#169-hacking-con-buscadores-automático-con-selenium)                                       |

---

# **Primer Proyecto de Python Hacking: Google Hacking, IA y Automatizacion**

## **152. Entornos virtuales en Python**

### ¿Qué es un entorno virtual en Python?

Un **entorno virtual (virtual environment)** es un espacio aislado en tu computadora donde puedes instalar **versiones específicas de Python y paquetes** (librerías) sin afectar el resto del sistema.

En otras palabras, puedes tener muchos proyectos en tu PC y **cada uno con sus propias dependencias** sin que se mezclen o entren en conflicto.

✅ **Ejemplo de problema sin entornos virtuales:**

- Proyecto A necesita **Django 3.2**
- Proyecto B necesita **Django 4.2**

Si solo tienes un Python global, no puedes tener **dos versiones de Django** instaladas al mismo tiempo sin romper algo.

✅ **Solución con entornos virtuales:**

- Proyecto A ➜ entorno virtual con Django 3.2
- Proyecto B ➜ entorno virtual con Django 4.2

Cada entorno virtual es como una "burbuja" separada.

---

### Ventajas de usar entornos virtuales

⭐ Evitar conflictos de dependencias.

⭐ Organizar proyectos de forma más limpia.

⭐ Reproducir fácilmente el entorno en otra máquina (usando requirements.txt).

---

### Herramientas para entornos virtuales en Python

Hay varias formas, pero la más común y sencilla es **venv**, que viene con Python 3.3+.

Otras opciones más avanzadas:

- virtualenv
- conda (para ciencia de datos)
- pipenv
- poetry

Pero aquí nos centraremos en **venv**, porque es oficial y no necesitas instalar nada extra.

---

### ¿Cómo instalar y usar entornos virtuales con `venv`?

#### ✅ Prerequisito

- Tener Python 3.3 o superior instalado.

Verifica con:

```bash
python --version
```

o

```bash
python3 --version
```

---

#### ✅ Paso 1: Crear el entorno virtual

Supongamos que estás en la carpeta de tu proyecto.

**Comando:**

```bash
python -m venv nombre_del_entorno
```

✅ Ejemplo práctico:

```bash
python -m venv venv
```

Aquí `venv` es el nombre del entorno (puedes llamarlo como quieras: env, .venv, myenv, etc.).

---

✅ Resultado:

Se crea una carpeta llamada `venv/` con:

```
venv/
  bin/ (Linux/Mac) o Scripts/ (Windows)
  lib/
  pyvenv.cfg
```

Todo lo necesario para aislar las dependencias.

---

#### ✅ Paso 2: Activar el entorno virtual

Dependiendo del sistema operativo:

⭐ En **Windows** (PowerShell):

```powershell
.\venv\Scripts\Activate
```

⭐ En **Windows** (CMD):

```cmd
venv\Scripts\activate.bat
```

⭐ En **Linux/Mac**:

```bash
source venv/bin/activate
```

✅ Resultado:

El prompt de tu terminal cambia:

```
(venv) $
```

Eso indica que **el entorno está activado**. Todas las instalaciones con `pip` irán solo a ese entorno.

---

#### ✅ Paso 3: Instalar paquetes en el entorno

Cuando el entorno está activado:

```bash
pip install requests
```

✅ Verificación:

```bash
pip list
```

Solo verás los paquetes instalados **en el entorno**.

---

#### ✅ Paso 4: Desactivar el entorno

Para volver al Python global:

```bash
deactivate
```

El prompt vuelve a normal.

---

### Ejemplo práctico completo

Te dejo un ejemplo paso a paso como si lo escribieras en la terminal:

```bash
# 1. Crear carpeta del proyecto
mkdir mi_proyecto
cd mi_proyecto

# 2. Crear entorno virtual
python -m venv venv

# 3. Activar el entorno (Linux/Mac)
source venv/bin/activate

# o en Windows PowerShell
.\venv\Scripts\Activate

# 4. Instalar paquetes
pip install flask

# 5. Ver paquetes instalados
pip list

# 6. Desactivar el entorno
deactivate
```

---

### Compartir dependencias (opcional)

Para guardar las dependencias en un archivo:

```bash
pip freeze > requirements.txt
```

Contenido de ejemplo de **requirements.txt**:

```
Flask==2.2.5
requests==2.31.0
```

En otra máquina o entorno, puedes recrearlo con:

```bash
pip install -r requirements.txt
```

---

### Resumen

✅ `python -m venv nombre` ➜ crea un entorno virtual

✅ Activar ➜ usar source (Linux/Mac) o .\ (Windows)

✅ Instalar ➜ pip install

✅ Desactivar ➜ deactivate

✅ Compartir ➜ pip freeze > requirements.txt

---

### BONUS: Buenas prácticas

⭐ Nómbralo `.venv` para que editores como VSCode lo detecten.

⭐ Añade `venv/` o `.venv/` al archivo `.gitignore` para no subirlo a Git.

---

[🔼](#índice)

---

## **153. Hacking con buscadores con Python**

### ✅ ¿Qué es el "hacking con buscadores"?

Es el **uso avanzado de buscadores** (Google, Bing, DuckDuckGo, etc.) para encontrar información sensible o interesante que está _públicamente indexada_, pero que normalmente no debería ser tan fácil de descubrir.

✅ Ejemplos de lo que se puede encontrar:

- Páginas de login de administradores.
- Archivos de configuración expuestos (.env, .git).
- Cámaras web sin seguridad.
- Documentos confidenciales indexados.

---

### ✅ ¿Cómo funciona? (explicación sencilla)

Los buscadores indexan TODO lo que encuentran si no está protegido. Usando operadores especiales de búsqueda (llamados **Google Dorks**) puedes filtrar resultados para cosas muy específicas.

✅ Operadores básicos:

- **site:** → Limita a un dominio

  - `site:example.com`

- **filetype:** → Busca tipo de archivo

  - `filetype:pdf`

- **inurl:** → Cadena en la URL

  - `inurl:admin`

- **intitle:** → Cadena en el título de la página

  - `intitle:"login"`

✅ Ejemplo manual:

```
site:example.com inurl:admin
```

→ Busca páginas en _example.com_ que tengan _admin_ en la URL.

---

### ✅ Aplicaciones (legales y éticas)

⚠️ MUY IMPORTANTE: El "hacking con buscadores" **no es ilegal en sí mismo** porque se basa en información pública, pero usarlo para vulnerar sistemas o extraer datos sensibles sin permiso **sí puede ser ilegal**.

✅ Usos legales:

- Auditorías de seguridad (pentesting con permiso).
- Reconocimiento en bug bounties.
- Investigación OSINT.
- Verificar si tu propia web expone datos sensibles.

---

### ✅ ¿Cómo se hace a mano?

Supongamos que queremos encontrar documentos PDF sobre finanzas en un sitio:

```
site:example.com filetype:pdf finanzas
```

O páginas de login expuestas:

```
intitle:"login" inurl:admin
```

---

### ✅ ¿Cómo se hace con Python? (Automatización)

Ahora, vamos a lo interesante: **automatizarlo con Python.**

Los buscadores no quieren que los "scrapees" masivamente. Google, por ejemplo, te bloqueará o te pondrá CAPTCHAs. Pero puedes hacerlo de forma sencilla, respetuosa y limitada para experimentación o auditoría.

Hay varias formas:

✅ Usar **Google Search API oficial (limitada, de pago)**

✅ Usar **librerías de scraping (con precaución)**

✅ Usar **librerías para búsqueda "no oficial"** (como `googlesearch-python`)

Te voy a explicar **la forma más sencilla** para aprender:

---

### ✅ Instalación de la herramienta en Python

Vamos a usar [`googlesearch-python`](https://pypi.org/project/googlesearch-python/), una librería fácil de instalar y usar.

#### ✅ Instalación

Abre la terminal y escribe:

```
pip install googlesearch-python
```

Eso descargará e instalará la librería.

---

### ✅ Ejemplo práctico paso a paso

### **Escenario:**

Queremos automatizar la búsqueda de paneles de administración en un dominio específico.

✅ Manualmente haríamos:

```
site:example.com inurl:admin
```

✅ Con Python:

```python
from googlesearch import search

query = 'site:example.com inurl:admin'

for result in search(query, num_results=10):
    print(result)
```

**Explicación del código:**

- Importamos `search` de la librería.
- Definimos la consulta (puede ser cualquier dork).
- Iteramos sobre los primeros 10 resultados.
- Imprimimos las URLs.

---

### ✅ Otro ejemplo práctico

✅ Buscar archivos PDF públicos en todo internet sobre "contratos":

```python
from googlesearch import search

query = 'filetype:pdf contratos'

for url in search(query, num_results=5):
    print(url)
```

✅ Resultado esperado (ejemplo):

```
https://example.com/contratos2023.pdf
https://otherdomain.com/documentos/contrato.pdf
...
```

---

### ✅ Mejoras y variaciones

✅ Cambiar la cantidad de resultados:

```python
for url in search(query, num_results=20):
    print(url)
```

✅ Probar otros operadores:

- `intitle:"index of"`
- `inurl:login`
- `filetype:env`
- `site:*.gov confidential`

✅ Uso avanzado (concatenar múltiples dorks):

```python
query = 'site:example.com inurl:admin intitle:"login"'
```

---

### ✅ Limitaciones importantes

⚠️ Google bloquea el scraping excesivo.

⚠️ Respeta el "robots.txt" y las políticas de uso.

⚠️ Solo úsalo con fines educativos o de auditoría autorizada.

✅ Alternativas:

- Bing Search API
- DuckDuckGo API (no oficial)
- Scraping con Selenium (más complejo)

---

### ✅ Resumen ultra corto

✅ Hacking con buscadores = usar operadores de búsqueda avanzados.

✅ Sirve para encontrar info sensible indexada.

✅ Manual: usar Google con dorks.

✅ Con Python:

1. `pip install googlesearch-python`
2. Importar `search`
3. Definir tu consulta
4. Iterar resultados.

---

### ✅ BONUS: Plantilla de script genérico

Te dejo un **script más completo**:

```python
from googlesearch import search

def google_dork_scan(query, limit=10):
    print(f"Realizando búsqueda: {query}")
    results = search(query, num_results=limit)
    for i, url in enumerate(results, start=1):
        print(f"{i}. {url}")

if __name__ == "__main__":
    dork = input("Ingresa tu Google Dork: ")
    google_dork_scan(dork, limit=10)
```

✅ Ejecución ejemplo:

```
Ingresa tu Google Dork: site:example.com inurl:admin
```

✅ Salida:

```
1. https://example.com/admin/login
2. https://example.com/admin/dashboard
...
```

---

### ✅ Conclusión

**Hacking con buscadores** es una técnica OSINT poderosa.

- Manual: usa operadores de Google.
- Python: automatiza tus búsquedas.
- Siempre usa con responsabilidad.

---

[🔼](#índice)

---

## **154. Operadores y keywords Google Hacking**

### ✅ ¿Qué es Google Hacking?

**Google Hacking** (también llamado **Google Dorking**) es el uso avanzado del buscador de Google (o de otros buscadores) para **encontrar información sensible o específica** usando ciertos comandos especiales llamados **operadores**.

Google indexa millones de páginas, y con búsquedas comunes sólo ves lo más relevante.
Pero con **operadores** puedes filtrar resultados y encontrar cosas muy específicas.

---

### ✅ ¿Qué son operadores y keywords en Google Hacking?

✅ **Operadores:** son comandos especiales que le dices a Google para filtrar tu búsqueda.

✅ **Keywords:** son las palabras clave que acompañan los operadores para afinar la búsqueda.

👉 Son como trucos o atajos para hacer **búsquedas más potentes**.

---

### ✅ ¿Para qué sirven?

✅ Encontrar información pública pero "olvidada":

- Formularios de login
- Archivos confidenciales
- Backups
- Bases de datos expuestas
- Cámaras web
- Documentos sensibles

✅ Usos éticos:

- Auditorías de seguridad (pentesting)
- OSINT (inteligencia de fuentes abiertas)
- Bug bounty

✅ Usos maliciosos (¡prohibidos!):

- Acceder a datos sin permiso

---

### ✅ ¿Se instalan?

❌ ¡NO! No necesitas instalar nada.

✔️ Solo necesitas **un navegador y Google**.

✔️ Opcionalmente puedes automatizar con Python (te lo puedo enseñar si quieres).

---

### ✅ Principales operadores con ejemplos fáciles

Te dejo **los más usados**, súper claros y con ejemplos reales (cámbialos por el sitio que quieras):

---

#### ⭐ 1. `site:`

✅ Restringe los resultados a un sitio o dominio específico.

**Ejemplo:**

```
site:example.com
```

🔎 → Muestra solo resultados de _example.com_.

✅ Otro ejemplo:

```
site:*.gov
```

🔎 → Resultados de cualquier sitio .gov.

---

#### ⭐ 2. `inurl:`

✅ Busca palabras en la URL.

**Ejemplo:**

```
inurl:admin
```

🔎 → Encuentra URLs con "admin".

✅ Combinado:

```
site:example.com inurl:login
```

🔎 → Encuentra páginas de login en _example.com_.

---

#### ⭐ 3. `intitle:`

✅ Busca palabras en el **título** de la página.

**Ejemplo:**

```
intitle:"index of"
```

🔎 → Encuentra directorios abiertos.

✅ Otro ejemplo:

```
intitle:"login"
```

🔎 → Encuentra páginas de inicio de sesión.

---

#### ⭐ 4. `filetype:`

✅ Busca archivos de un tipo específico.

**Ejemplo:**

```
filetype:pdf
```

🔎 → Solo PDFs.

✅ Combinado:

```
filetype:pdf site:example.com
```

🔎 → Solo PDFs en _example.com_.

✅ Otro:

```
filetype:xls password
```

🔎 → Hojas de Excel que pueden contener la palabra "password".

---

#### ⭐ 5. `intext:`

✅ Busca palabras en el contenido de la página.

**Ejemplo:**

```
intext:"confidential"
```

🔎 → Encuentra páginas con "confidential" en el texto.

---

#### ⭐ 6. `cache:`

✅ Muestra la versión en caché de una página.

**Ejemplo:**

```
cache:example.com
```

🔎 → La versión guardada en Google.

---

#### ⭐ 7. `-`

✅ Excluye palabras.

**Ejemplo:**

```
login -facebook
```

🔎 → Resultados con "login" pero que NO tengan "facebook".

---

#### ⭐ 8. `OR`

✅ Busca una cosa u otra.

**Ejemplo:**

```
admin OR login
```

🔎 → Resultados que tengan "admin" o "login".

---

#### ⭐ 9. `" "`

✅ Busca frase exacta.

**Ejemplo:**

```
"index of /backup"
```

🔎 → Exactamente esa frase.

---

#### ⭐ 10. `*`

✅ Comodín (cualquier palabra).

**Ejemplo:**

```
"index of * backup"
```

🔎 → Coincide con cualquier palabra entre "index of" y "backup".

---

#### ✅ Ejemplos reales de Google Dorks

Aquí tienes ejemplos completos (¡para practicar!):

✅ Buscar páginas de login:

```
inurl:admin intitle:login
```

✅ Buscar directorios abiertos:

```
intitle:"index of" "backup"
```

✅ Buscar archivos de contraseñas:

```
filetype:txt intext:password
```

✅ Buscar cámaras web públicas:

```
inurl:view/view.shtml
```

✅ Buscar documentos confidenciales:

```
site:*.gov filetype:pdf confidential
```

✅ Buscar bases de datos expuestas:

```
intitle:"index of" "db.sql"
```

---

### ✅ No necesitas instalar nada, pero puedes usar Python (opcional)

Para usar estos operadores en Python puedes instalar una librería:

```
pip install googlesearch-python
```

✅ Código súper fácil:

```python
from googlesearch import search

query = 'site:example.com inurl:admin'
for url in search(query, num_results=5):
    print(url)
```

✅ Resultado:

```
https://example.com/admin/login
https://example.com/admin/dashboard
...
```

---

### ✅ ¿Es ilegal?

❌ Usar Google con operadores no es ilegal (la información es pública).

⚠️ Lo ilegal es acceder sin permiso a datos sensibles o vulnerar sistemas.

✅ Úsalo solo para auditoría autorizada, investigación o aprendizaje.

---

### ✅ Resumen rápido

✅ **Operadores** = comandos especiales para filtrar búsquedas.

✅ **Keywords** = palabras clave que usas con los operadores.

✅ No necesitas instalar nada, solo Google.

✅ Ejemplos útiles:

- `site:`
- `inurl:`
- `intitle:`
- `filetype:`
- `intext:`

  ✅ Puedes combinarlos para búsquedas más potentes.

---

### ✅ Tabla de operadores (para tu chuleta)

| Operador  | Qué hace                        | Ejemplo              |
| --------- | ------------------------------- | -------------------- |
| site:     | Limita a un dominio             | site\:example.com    |
| inurl:    | Busca en la URL                 | inurl\:admin         |
| intitle:  | Busca en el título de la página | intitle:"index of"   |
| filetype: | Tipo de archivo                 | filetype\:pdf        |
| intext:   | Palabra en el contenido         | intext\:password     |
| cache:    | Muestra versión en caché        | cache\:example.com   |
| -         | Excluye palabras                | login -facebook      |
| OR        | Una cosa u otra                 | admin OR login       |
| " "       | Frase exacta                    | "index of /backup"   |
| \*        | Comodín                         | "index of \* backup" |

---

### ✅ Práctica sugerida

✅ Prueba en Google:

```
site:edu filetype:pdf cybersecurity
```

→ PDFs sobre ciberseguridad en sitios .edu.

✅ Otro:

```
intitle:"index of" "admin"
```

→ Directorios abiertos que contengan "admin".

---

### ✅ Conclusión

⭐ Google Hacking = usar operadores para búsquedas avanzadas.

⭐ Útil en auditorías, OSINT, bug bounty.

⭐ 100% legal si lo usas responsablemente.

⭐ No necesitas instalar nada.

⭐ Puedes automatizar con Python si quieres.

---

[🔼](#índice)

---

## **155. DuckDuckGo Hacking**

### ✅ ¿Qué es “DuckDuckGo Hacking”?

**DuckDuckGo Hacking** (o “DuckDuckGo Dorking”) es el uso avanzado del buscador **DuckDuckGo** para encontrar información pública pero “oculta a simple vista”, usando operadores especiales.

Es muy parecido al **Google Hacking / Google Dorking**, pero en **DuckDuckGo**.

✅ DuckDuckGo **no guarda historial**, **no personaliza resultados**, **no tiene captchas agresivos**.

✅ A menudo muestra **resultados distintos** de Google.

---

### ✅ ¿Para qué sirve?

✅ Encontrar información pública o mal configurada:

- Páginas de login.
- Backups abiertos.
- Archivos de configuración.
- Bases de datos expuestas.
- Directorios listados.
- Documentos confidenciales indexados.

✅ Usos éticos:

- Auditorías de seguridad (pentesting con permiso).
- OSINT (Open Source Intelligence).
- Bug bounty.

✅ ⚠️ **ATENCIÓN:**

Usar estos métodos para acceder o explotar sistemas sin permiso **es ilegal**.

---

### ✅ ¿Cuál es la diferencia con Google?

✔️ DuckDuckGo **soporta la mayoría de los mismos operadores** que Google.

✔️ Pero DuckDuckGo **no siempre bloquea ni limita tanto**.

✔️ Muestra **resultados diferentes** porque usa otras fuentes (no solo Google).

✔️ **No necesitas cuenta** ni historial.

---

### ✅ ¿Qué se “instala”?

❌ No se instala nada para usarlo en el navegador:

✅ Solo necesitas **abrir [DuckDuckGo](https://duckduckgo.com/)**.

✔️ Si quieres **automatizar con Python**, te explico más abajo cómo **instalar** una librería.

---

### ✅ Principales operadores de DuckDuckGo

DuckDuckGo soporta **operadores de búsqueda avanzados**, igual que Google.

Aquí te dejo **explicados uno por uno con ejemplos MUY claros.**

---

#### ⭐ 1. `site:`

✅ Limita la búsqueda a un dominio.

**Ejemplo:**

```
site:example.com
```

🔎 Solo resultados de _example.com_.

---

#### ⭐ 2. `inurl:`

✅ Busca una palabra en la URL.

**Ejemplo:**

```
inurl:admin
```

🔎 Encuentra URLs que contengan "admin".

✅ Combinado:

```
site:example.com inurl:login
```

→ Login pages en _example.com_.

---

#### ⭐ 3. `intitle:`

✅ Busca en el título de la página.

**Ejemplo:**

```
intitle:"index of"
```

🔎 Directorios abiertos.

---

#### ⭐ 4. `filetype:`

✅ Restringe por tipo de archivo.

**Ejemplo:**

```
filetype:pdf
```

→ Solo PDFs.

✅ Combinado:

```
site:example.com filetype:pdf
```

→ PDFs en _example.com_.

---

#### ⭐ 5. `-`

✅ Excluye términos.

**Ejemplo:**

```
login -facebook
```

→ Login pero excluyendo Facebook.

---

#### ⭐ 6. `" "`

✅ Búsqueda exacta.

**Ejemplo:**

```
"index of /backup"
```

→ Solo resultados exactos.

---

#### ⭐ 7. `OR`

✅ Busca una cosa o la otra.

**Ejemplo:**

```
admin OR login
```

→ Resultados con "admin" o "login".

---

#### ⭐ 8. `*`

✅ Comodín (palabra cualquiera).

**Ejemplo:**

```
"index of * backup"
```

→ Coincide con cualquier palabra entre "index of" y "backup".

---

### ✅ Ejemplos prácticos paso a paso

Aquí te dejo **busquedas reales** que puedes copiar y pegar en DuckDuckGo:

---

✅ 1. Encontrar paneles de administración en un sitio

```
site:example.com inurl:admin
```

🔎 Encuentra páginas con "admin" en la URL en _example.com_.

---

✅ 2. Buscar directorios abiertos

```
intitle:"index of" "backup"
```

🔎 Encuentra directorios con backups expuestos.

---

✅ 3. Encontrar documentos confidenciales

```
filetype:pdf confidential
```

🔎 PDFs que contengan "confidential".

---

✅ 4. Buscar contraseñas en archivos de texto

```
filetype:txt password
```

🔎 Archivos .txt con la palabra "password".

---

✅ 5. Encontrar cámaras web públicas

```
inurl:view/view.shtml
```

🔎 Páginas con cámaras IP sin contraseña.

---

✅ 6. Buscar archivos SQL expuestos

```
intitle:"index of" "db.sql"
```

🔎 Directorios con bases de datos SQL expuestas.

---

### ✅ BONUS: Combinaciones potentes

✅ Directorios con backups

```
intitle:"index of" (backup OR .bak OR .zip)
```

✅ Archivos de configuración

```
filetype:env DB_PASSWORD
```

✅ Datos de empleados en PDF

```
site:*.gov filetype:pdf employees
```

✅ Contraseñas en Excel

```
filetype:xls password
```

✅ Backups en S3

```
site:s3.amazonaws.com backup
```

---

### ✅ Limitaciones y diferencias con Google

✔️ DuckDuckGo NO te pide CAPTCHA tan seguido.

✔️ No guarda tu historial.

✔️ No tiene tantas restricciones de país.

❗️ Algunas búsquedas avanzadas no son idénticas a Google (no soporta todos los operadores complejos).

---

### ✅ ¿Cómo "instalar" DuckDuckGo Hacking en Python?

Ahora, si quieres **automatizar** tus búsquedas con Python, necesitas **instalar una librería** para hacer búsquedas web.

DuckDuckGo **no tiene una API oficial gratuita para búsquedas web genéricas**, pero hay librerías no oficiales como [`duckduckgo-search`](https://pypi.org/project/duckduckgo-search/).

---

#### ✅ Instalación en tu terminal

```
pip install duckduckgo-search
```

---

#### ✅ Ejemplo súper fácil en Python

```python
from duckduckgo_search import DDGS

query = 'site:example.com inurl:admin'

with DDGS() as ddgs:
    for r in ddgs.text(query, max_results=5):
        print(r['href'])
```

✅ Resultado esperado:

```
https://example.com/admin/login
https://example.com/admin/dashboard
...
```

---

#### ✅ Otro ejemplo: buscar backups públicos

```python
from duckduckgo_search import DDGS

query = 'intitle:"index of" "backup"'

with DDGS() as ddgs:
    for r in ddgs.text(query, max_results=5):
        print(r['href'])
```

✅ Resultado esperado:

```
http://somesite.com/backup/
http://othersite.com/files/backup.zip
...
```

---

### ✅ Tabla de operadores para DuckDuckGo

| Operador  | Qué hace                  | Ejemplo              |
| --------- | ------------------------- | -------------------- |
| site:     | Limita a un dominio       | site\:example.com    |
| inurl:    | Busca en la URL           | inurl\:admin         |
| intitle:  | Busca en el título        | intitle:"index of"   |
| filetype: | Busca por tipo de archivo | filetype\:pdf        |
| -         | Excluye términos          | login -facebook      |
| " "       | Búsqueda exacta           | "index of /backup"   |
| OR        | Una cosa u otra           | admin OR login       |
| \*        | Comodín                   | "index of \* backup" |

---

### ✅ Resumen rápido

✅ DuckDuckGo Hacking = usar operadores de búsqueda avanzados en DuckDuckGo.

✅ No necesitas instalar nada para usarlo en el navegador.

✅ Puedes automatizarlo con Python instalando:

```
pip install duckduckgo-search
```

✅ Usa operadores como:

- `site:`
- `inurl:`
- `intitle:`
- `filetype:`
- `-`, `OR`, `" "`, `*`

✅ ⚠️ Úsalo solo con fines éticos.

---

### ✅ ¿Para qué sirve realmente?

⭐ Pentesters y equipos de seguridad: verificar información expuesta.

⭐ Periodistas o investigadores OSINT: encontrar datos públicos.

⭐ Bug bounty hunters: hallar vulnerabilidades no intencionadas.

⭐ Dueños de sitios: verificar su propia exposición.

---

[🔼](#índice)

---

## **156. Ejecución de scripts en Python**

### ✅ ¿Qué es un "script" en Python?

**Un script en Python** es simplemente un **archivo de texto** que contiene **código Python**.

Se guarda con la extensión `.py`.

✅ Puedes pensar en él como una receta de instrucciones que Python lee y ejecuta línea por línea.

---

✅ **Ejemplo súper sencillo de un script:**

Supongamos que escribes esto en un archivo de texto:

```python
print("Hola mundo")
```

Si guardas eso como `hola.py`, ¡ese ya es un script en Python!

Cuando lo ejecutes, imprimirá:

```
Hola mundo
```

---

### ✅ ¿Para qué sirve un script?

⭐ Automatizar tareas.

⭐ Procesar datos.

⭐ Crear aplicaciones web.

⭐ Hacer scraping.

⭐ Hacer cálculos científicos.

⭐ Casi cualquier cosa que puedas imaginar en programación.

---

### ✅ ¿Cómo escribir un script en Python?

#### ✅ Paso 1: Instalar Python

Antes de ejecutar scripts, **debes tener Python instalado**.

---

##### 🔹 Verificar si ya tienes Python

✅ Abre la terminal o CMD:

```
python --version
```

o

```
python3 --version
```

✅ Ejemplo de salida:

```
Python 3.10.12
```

Si aparece algo así, **ya lo tienes instalado**.

---

##### 🔹 Si NO tienes Python

✅ Ve a [https://www.python.org/downloads/](https://www.python.org/downloads/)

✅ Descarga el instalador para tu sistema (Windows, Mac, Linux).

✅ En Windows, asegúrate de marcar **"Add Python to PATH"** al instalar.

---

#### ✅ Paso 2: Crear el archivo de script

✅ Abre un editor de texto:

- Bloc de notas (Windows)
- VSCode
- Sublime
- Nano (Linux)
- Cualquiera

✅ Escribe el código:

```python
print("Hola mundo desde mi script")
```

✅ Guárdalo como:

```
hola.py
```

✅ Ahora tienes tu primer **script**.

---

### ✅ ¿Cómo se ejecuta un script en Python?

#### ✅ A. En Windows

✅ Abre CMD o PowerShell.

✅ Navega a la carpeta donde está tu archivo.

Por ejemplo:

```cmd
cd C:\Users\TuUsuario\MisProyectos
```

✅ Ejecuta:

```
python hola.py
```

o (a veces necesario):

```
python3 hola.py
```

✅ Resultado esperado:

```
Hola mundo desde mi script
```

---

#### ✅ B. En Linux o Mac

✅ Abre la terminal.

✅ Navega a la carpeta del script:

```bash
cd /home/tuusuario/MisProyectos
```

o

```bash
cd ~/MisProyectos
```

✅ Ejecuta:

```bash
python hola.py
```

o

```bash
python3 hola.py
```

✅ Resultado:

```
Hola mundo desde mi script
```

---

### ✅ Ejemplo de script más completo

✅ Vamos a crear un script llamado **saludo.py**:

```python
nombre = input("¿Cómo te llamas? ")
print(f"¡Hola, {nombre}!")
```

✅ Guardar como:

```
saludo.py
```

✅ Ejecutar:

```
python saludo.py
```

✅ Ejemplo de salida en terminal:

```
¿Cómo te llamas? Juan
¡Hola, Juan!
```

---

### ✅ Opción avanzada (hacerlo ejecutable en Linux/Mac)

✅ Agregar _shebang_ al inicio del archivo:

```python
#!/usr/bin/env python3
print("¡Hola mundo ejecutable!")
```

✅ Dar permisos de ejecución:

```bash
chmod +x mi_script.py
```

✅ Ejecutar directamente:

```bash
./mi_script.py
```

✅ Resultado:

```
¡Hola mundo ejecutable!
```

---

### ✅ Ejecutar scripts en VSCode

✅ Abre VSCode.

✅ Abre la carpeta o el archivo `.py`.

✅ Haz clic en el botón ▶️ (Run Python File).

✅ Salida aparecerá en el terminal integrado.

✅ Ejemplo:

```python
print("Probando desde VSCode")
```

---

### ✅ Ejecutar scripts en IDLE (el editor de Python)

✅ Python incluye **IDLE** al instalarlo.

✅ Abre IDLE.

✅ File > New File.

✅ Escribe tu código.

✅ File > Save As...

✅ File > Run Module (o presiona F5).

✅ Resultado:

```
>>> ===================
>>> Hola desde IDLE
```

---

### ✅ Ejecutar scripts con argumentos

✅ Crea **argumentos** en tu script:

```python
import sys

print("Argumentos recibidos:", sys.argv)
```

✅ Guarda como:

```
args.py
```

✅ Ejecutar:

```
python args.py uno dos tres
```

✅ Resultado:

```
Argumentos recibidos: ['args.py', 'uno', 'dos', 'tres']
```

---

### ✅ ¿Cómo instalar y usar entornos virtuales (opcional recomendado)?

✅ Para aislar dependencias por proyecto.

✅ Crear:

```
python -m venv venv
```

✅ Activar:

⭐ Windows:

```
venv\Scripts\activate
```

⭐ Linux/Mac:

```
source venv/bin/activate
```

✅ Instalar paquetes:

```
pip install requests
```

✅ Ejecutar script:

```
python mi_script.py
```

✅ Desactivar entorno:

```
deactivate
```

---

### ✅ Ejemplo final súper completo

✅ Código (en archivo **mi_programa.py**):

```python
#!/usr/bin/env python3

import sys

def main():
    print("Hola desde mi_programa.py")
    print("Argumentos:", sys.argv)

if __name__ == "__main__":
    main()
```

✅ Guardar.

✅ Dar permisos (Linux/Mac):

```
chmod +x mi_programa.py
```

✅ Ejecutar:

```
./mi_programa.py hola mundo
```

✅ Resultado:

```
Hola desde mi_programa.py
Argumentos: ['./mi_programa.py', 'hola', 'mundo']
```

---

### ✅ Resumen breve

✅ Un script = archivo .py con código.

✅ Escribir con cualquier editor.

✅ Guardar como .py.

✅ Ejecutar con:

```
python archivo.py
```

✅ Se puede usar CMD, terminal, VSCode, IDLE.

✅ En Linux/Mac puedes hacerlo ejecutable.

✅ Puedes usar entornos virtuales para gestionar dependencias.

---

### ✅ Consejos finales

⭐ Usa nombres claros: `mi_script.py`, `analisis.py`.

⭐ Comenta tu código.

⭐ Usa entornos virtuales.

⭐ Prueba en VSCode o PyCharm para más comodidad.

⭐ Aprende a usar `argparse` para argumentos más pro.

---

[🔼](#índice)

---

## **157. Argumentos en línea de comandos: Argparse**

### ✅ ¿Qué es `argparse`?

`argparse` es **un módulo de Python** para crear programas que acepten **argumentos desde la línea de comandos**.

✅ Permite leer argumentos que escribes cuando llamas a tu script.

✅ Genera ayuda automática (`-h`).

✅ Es muy usado en scripts, herramientas de automatización, CLI.

---

### ✅ ¿Para qué sirve?

✔️ Para que tus scripts sean interactivos y configurables **sin editar el código**.

✅ Por ejemplo:

En lugar de hardcodear:

```python
nombre = "Juan"
```

Puedes ejecutarlo así:

```
python saludo.py --nombre Juan
```

---

✅ Usos comunes:

⭐ Scripts de automatización.

⭐ Herramientas de línea de comandos.

⭐ Procesamiento de archivos.

⭐ Web scraping configurable.

⭐ Machine learning (ajustar parámetros desde CLI).

---

### ✅ ¿Cómo se instala?

✅ ¡No necesitas instalar nada!
`argparse` **viene incluido con Python** (desde la versión 2.7 y 3.2+).

✅ Solo necesitas **importarlo**:

```python
import argparse
```

---

### ✅ ¿Cómo funciona? Explicación simple

✅ Tu script define **qué argumentos espera**.

✅ El usuario llama al script con esos argumentos.

✅ Tu código **lee y usa** esos valores.

---

### ✅ Ejemplo súper sencillo (argumento obligatorio)

Vamos a crear un script llamado **saludo.py**:

---

**saludo.py:**

```python
import argparse

parser = argparse.ArgumentParser(description="Script de saludo")
parser.add_argument("nombre", help="Tu nombre")
args = parser.parse_args()

print(f"¡Hola, {args.nombre}!")
```

---

✅ Explicación paso a paso:

1️⃣ `ArgumentParser` ➜ Crea el "parser" que entiende argumentos.

2️⃣ `add_argument("nombre", ...)` ➜ Define argumento obligatorio.

3️⃣ `parse_args()` ➜ Lee los argumentos pasados.

4️⃣ `args.nombre` ➜ Valor que el usuario pasó.

---

✅ ¿Cómo se ejecuta?

```bash
python saludo.py Juan
```

✅ Salida:

```
¡Hola, Juan!
```

---

✅ Si lo llamas sin argumento:

```bash
python saludo.py
```

Te dará error + ayuda automática:

```
usage: saludo.py [-h] nombre
saludo.py: error: the following arguments are required: nombre
```

---

### ✅ Ejemplo con argumentos opcionales

Ahora veremos **argumentos con flags**:

✅ Creamos **saludo_opcional.py**:

```python
import argparse

parser = argparse.ArgumentParser(description="Saludo personalizado")
parser.add_argument("--nombre", help="Tu nombre", default="amigo")
args = parser.parse_args()

print(f"¡Hola, {args.nombre}!")
```

---

✅ Explicación:

- `--nombre` ➜ argumento opcional (con doble guion).
- `default="amigo"` ➜ valor por defecto si no se pasa.

---

✅ Ejecutar con argumento:

```bash
python saludo_opcional.py --nombre Juan
```

✅ Salida:

```
¡Hola, Juan!
```

---

✅ Ejecutar sin argumento:

```bash
python saludo_opcional.py
```

✅ Salida:

```
¡Hola, amigo!
```

---

### ✅ Argumentos múltiples

✅ Script: **operaciones.py**

```python
import argparse

parser = argparse.ArgumentParser(description="Sumar dos números")
parser.add_argument("a", type=int, help="Primer número")
parser.add_argument("b", type=int, help="Segundo número")
args = parser.parse_args()

resultado = args.a + args.b
print(f"La suma de {args.a} y {args.b} es {resultado}")
```

---

✅ Ejecutar:

```bash
python operaciones.py 5 7
```

✅ Salida:

```
La suma de 5 y 7 es 12
```

---

### ✅ Argumentos opcionales con flags

✅ Script: **saludo_formal.py**

```python
import argparse

parser = argparse.ArgumentParser(description="Saludo formal o informal")
parser.add_argument("--nombre", help="Tu nombre", default="amigo")
parser.add_argument("--formal", action="store_true", help="Usar saludo formal")
args = parser.parse_args()

if args.formal:
    print(f"Estimado/a {args.nombre}, un placer saludarle.")
else:
    print(f"¡Hola, {args.nombre}!")
```

---

✅ Ejecutar informal:

```bash
python saludo_formal.py --nombre Juan
```

✅ Salida:

```
¡Hola, Juan!
```

---

✅ Ejecutar formal:

```bash
python saludo_formal.py --nombre Juan --formal
```

✅ Salida:

```
Estimado/a Juan, un placer saludarle.
```

---

✅ Explicación del flag:

- `action="store_true"` ➜ Guarda `True` si está presente, `False` si no.
- Es un **interruptor**.

---

### ✅ Mostrar ayuda automática

✅ Todos los scripts con argparse soportan:

```
-h
```

o

```
--help
```

✅ Ejemplo:

```bash
python saludo_formal.py --help
```

✅ Salida:

```
usage: saludo_formal.py [-h] [--nombre NOMBRE] [--formal]

Saludo formal o informal

optional arguments:
  -h, --help       show this help message and exit
  --nombre NOMBRE  Tu nombre
  --formal         Usar saludo formal
```

---

### ✅ Ejemplo completo y profesional

✅ Script: **procesador_archivos.py**

```python
import argparse

def main():
    parser = argparse.ArgumentParser(
        description="Procesador de archivos con opciones"
    )

    parser.add_argument(
        "archivo", help="Ruta del archivo a procesar"
    )
    parser.add_argument(
        "--verbose", "-v", action="store_true", help="Modo detallado"
    )
    parser.add_argument(
        "--output", "-o", help="Archivo de salida"
    )

    args = parser.parse_args()

    if args.verbose:
        print(f"Procesando archivo: {args.archivo}")

    # Simulación de procesamiento
    contenido = f"Contenido procesado de {args.archivo}"

    if args.output:
        with open(args.output, "w") as f:
            f.write(contenido)
        if args.verbose:
            print(f"Guardado en {args.output}")
    else:
        print(contenido)

if __name__ == "__main__":
    main()
```

---

✅ Usos:

⭐ Solo mostrar resultado:

```bash
python procesador_archivos.py entrada.txt
```

✅ Resultado:

```
Contenido procesado de entrada.txt
```

---

⭐ Modo verbose:

```bash
python procesador_archivos.py entrada.txt --verbose
```

✅ Resultado:

```
Procesando archivo: entrada.txt
Contenido procesado de entrada.txt
```

---

⭐ Guardar en archivo:

```bash
python procesador_archivos.py entrada.txt --output resultado.txt
```

✅ Resultado:

- Archivo **resultado.txt** creado con el contenido procesado.

---

### ✅ Resumen rápido

✅ `argparse` viene con Python.

✅ Permite definir argumentos:

- Posicionales (obligatorios).
- Opcionales (con flags).

  ✅ Genera ayuda automática.

  ✅ Soporta tipos de datos.

  ✅ Muy usado para scripts profesionales.

---

### ✅ Guía ultra-corta de uso

✔️ Importar:

```python
import argparse
```

✔️ Crear parser:

```python
parser = argparse.ArgumentParser(description="Descripción")
```

✔️ Agregar argumentos:

```python
parser.add_argument("posicional")
parser.add_argument("--opcional", default="valor")
parser.add_argument("--flag", action="store_true")
```

✔️ Parsear:

```python
args = parser.parse_args()
```

✔️ Usar:

```python
print(args.posicional)
print(args.opcional)
print(args.flag)
```

---

✅ Resultado:

Ejecutar con:

```
python mi_script.py valor --opcional otro --flag
```

✅ Salida:

```
valor
otro
True
```

---

### ✅ Consejos y buenas prácticas

⭐ Usa nombres claros para tus argumentos.

⭐ Usa `--help` para verificar la descripción.

⭐ Incluye `type=int`, `default`, `choices` para validar.

⭐ Usa `action="store_true"` para banderas.

⭐ Encapsula en funciones para scripts grandes.

---

### ✅ NO NECESITAS INSTALAR NADA

✅ `argparse` ya viene en Python.

✔️ Solo importa:

```python
import argparse
```

---

[🔼](#índice)

---

## **158. Generación de resultados: JSON, HTML, Consola**

### ✅ ¿Qué significa "generación de resultados"?

Es **producir o "imprimir" datos** de tu script en algún formato para que **otros programas o usuarios puedan usarlos**.

Por ejemplo:

✔️ Generar **JSON** para APIs o para guardar datos.

✔️ Generar **HTML** para páginas web o reportes.

✔️ Mostrar resultados en **consola** para usuarios humanos.

---

### ✅ Resultado en **CONSOLA**

**Consola** significa simplemente **mostrar texto al usuario** con `print()`.

✅ **NO necesita instalar nada.**

✅ Es la forma más simple y directa.

---

#### ⭐ Ejemplo 1: Hola mundo

```python
print("¡Hola mundo!")
```

✅ Resultado al ejecutar:

```
¡Hola mundo!
```

---

#### ⭐ Ejemplo 2: Mostrar datos calculados

```python
nombre = "Juan"
edad = 30

print("Nombre:", nombre)
print("Edad:", edad)
```

✅ Resultado:

```
Nombre: Juan
Edad: 30
```

---

#### ⭐ Ejemplo 3: Formatear salida

```python
nombre = "Ana"
saldo = 1234.56

print(f"Cliente: {nombre}, Saldo: ${saldo:.2f}")
```

✅ Resultado:

```
Cliente: Ana, Saldo: $1234.56
```

---

✅ **Resumen CONSOLA:**

- Solo necesitas `print()`.
- Súper directo.
- Perfecto para scripts simples.

---

### ✅ Resultado en **JSON**

✅ **JSON** (JavaScript Object Notation) es un formato de texto **muy usado** para intercambiar datos entre programas.

✅ Python trae un módulo **integrado**: `json`.

✅ ¡No necesitas instalar nada!

---

#### ⭐ Ejemplo sencillo: guardar datos en JSON

✅ Código: **guardar_json.py**

```python
import json

# Datos en Python (diccionario)
datos = {
    "nombre": "Carlos",
    "edad": 25,
    "ciudad": "Lima"
}

# Guardar en archivo JSON
with open("salida.json", "w") as f:
    json.dump(datos, f, indent=4)

print("Archivo JSON generado con éxito.")
```

---

✅ Resultado:

- Archivo **salida.json** generado con contenido:

```json
{
  "nombre": "Carlos",
  "edad": 25,
  "ciudad": "Lima"
}
```

---

#### ⭐ Ejemplo: convertir a texto JSON

✅ Código:

```python
import json

persona = {"nombre": "Lucía", "edad": 28}

# Convertir a string JSON
texto_json = json.dumps(persona, indent=4)

print("JSON generado:")
print(texto_json)
```

✅ Resultado en consola:

```
JSON generado:
{
    "nombre": "Lucía",
    "edad": 28
}
```

---

#### ⭐ Ejemplo: leer JSON

✅ Código:

```python
import json

with open("salida.json") as f:
    datos = json.load(f)

print("Datos leídos:", datos)
```

✅ Resultado:

```
Datos leídos: {'nombre': 'Carlos', 'edad': 25, 'ciudad': 'Lima'}
```

---

✅ **Resumen JSON:**

- Usa `import json` (viene con Python).
- `json.dump()` ➜ guardar en archivo.
- `json.dumps()` ➜ convertir a texto.
- `json.load()` ➜ leer desde archivo.
- `json.loads()` ➜ leer desde string.

---

### ✅ Resultado en **HTML**

✅ HTML (HyperText Markup Language) se usa para **crear páginas web** o **reportes en formato web**.

✅ En Python puedes **generar archivos .html fácilmente**.

✅ **No necesitas instalar nada** para lo básico.

---

#### ⭐ Ejemplo simple: generar archivo HTML

✅ Código: **generar_html.py**

```python
contenido_html = """
<!DOCTYPE html>
<html>
<head>
    <title>Reporte</title>
</head>
<body>
    <h1>Reporte de Cliente</h1>
    <p>Nombre: Juan Pérez</p>
    <p>Edad: 32</p>
</body>
</html>
"""

with open("reporte.html", "w") as f:
    f.write(contenido_html)

print("Archivo HTML generado con éxito.")
```

---

✅ Resultado:

- Archivo **reporte.html** con contenido web.
- Puedes abrirlo en tu navegador.

---

#### ⭐ Ejemplo dinámico: usando variables

✅ Código: **reporte_dinamico.py**

```python
nombre = "Ana"
edad = 29

html = f"""
<!DOCTYPE html>
<html>
<head>
    <title>Reporte Personalizado</title>
</head>
<body>
    <h1>Reporte de Cliente</h1>
    <p>Nombre: {nombre}</p>
    <p>Edad: {edad}</p>
</body>
</html>
"""

with open("reporte_ana.html", "w") as f:
    f.write(html)

print("Reporte generado para", nombre)
```

✅ Resultado:

- Archivo **reporte_ana.html** generado con los datos dinámicos.

---

#### ⭐ Resultado al abrir en navegador:

```
Reporte de Cliente

Nombre: Ana
Edad: 29
```

---

✅ **Extra (opcional):** Usar plantillas avanzadas

Si quieres algo más pro ➜ puedes instalar Jinja2:

```
pip install Jinja2
```

✅ Pero para lo **básico** ➜ `f-strings` o `.format()` ya funcionan.

---

✅ **Resumen HTML:**

- Solo necesitas abrir un archivo `.html` en modo escritura.
- Puedes mezclar texto con variables de Python.
- Ideal para reportes bonitos.

---

### ✅ INSTALACIÓN (resumen de requisitos)

✅ **Consola**:

✔️ No necesita nada extra.

✔️ Solo Python.

✅ **JSON**:

✔️ No necesita nada extra.

✔️ El módulo `json` viene con Python.

✅ **HTML**:

✔️ Para generación básica ➜ nada extra.

✔️ Para plantillas pro ➜ `pip install Jinja2` (opcional).

---

✅ En Windows, Linux, Mac:

✔️ Solo necesitas tener **Python instalado**.

✔️ Verificar con:

```
python --version
```

✔️ Si no tienes ➜ descargar desde [https://www.python.org/](https://www.python.org/).

---

### ✅ Comparación rápida

| Formato | Uso principal                         | Complejidad |
| ------- | ------------------------------------- | ----------- |
| Consola | Mostrar resultados al usuario         | Muy fácil   |
| JSON    | Guardar datos estructurados / APIs    | Fácil       |
| HTML    | Crear páginas web / reportes legibles | Fácil       |

---

### ✅ Mini-proyecto completo (todo junto)

✅ **Script:** `generador.py`

```python
import json

# Datos de ejemplo
cliente = {
    "nombre": "Luis",
    "edad": 40,
    "ciudad": "Cusco"
}

# 1️⃣ Resultado en Consola
print("\n--- CONSOLA ---")
print(f"Cliente: {cliente['nombre']}, Edad: {cliente['edad']}, Ciudad: {cliente['ciudad']}")

# 2️⃣ Resultado en JSON
with open("cliente.json", "w") as f:
    json.dump(cliente, f, indent=4)
print("\nArchivo JSON generado: cliente.json")

# 3️⃣ Resultado en HTML
html = f"""
<!DOCTYPE html>
<html>
<head>
    <title>Reporte de Cliente</title>
</head>
<body>
    <h1>Datos del Cliente</h1>
    <p>Nombre: {cliente['nombre']}</p>
    <p>Edad: {cliente['edad']}</p>
    <p>Ciudad: {cliente['ciudad']}</p>
</body>
</html>
"""

with open("cliente.html", "w") as f:
    f.write(html)
print("Archivo HTML generado: cliente.html")
```

---

✅ Al ejecutar:

```
python generador.py
```

✅ Resultado:

⭐ Consola:

```
--- CONSOLA ---
Cliente: Luis, Edad: 40, Ciudad: Cusco

Archivo JSON generado: cliente.json
Archivo HTML generado: cliente.html
```

⭐ Archivos generados:

- **cliente.json** con datos estructurados.
- **cliente.html** para abrir en navegador.

---

### ✅ Resumen final

✅ Mostrar en consola ➜ `print()`.

✅ Guardar JSON ➜ `import json`.

✅ Crear HTML ➜ escribir archivo `.html` con contenido dinámico.

✅ Nada extra que instalar para lo básico.

---

[🔼](#índice)

---

## **159. Manejo de ficheros: Descarga, Lectura y Escritura**

### ✅ Concepto básico: ¿Qué es el manejo de ficheros en Python?

Es trabajar con **archivos en tu disco o en la red**:

✔️ **Descargarlos** desde Internet.

✔️ **Leerlos** (abrirlos y extraer su contenido).

✔️ **Escribirlos** (crear o modificar archivos).

---

✅ Python trae **herramientas incorporadas** para trabajar con archivos locales:

✔️ No necesitas instalar nada extra para leer o escribir.

✅ Para **descargar** desde la web, puedes usar:

✔️ `urllib` (viene con Python).

✔️ O la librería externa `requests` (más fácil).

---

### ✅ Requisitos previos: ¿Qué se instala?

✅ Para lectura/escritura de archivos locales:

✔️ Nada. Python lo trae listo.

✅ Para descargas simples:

✔️ `urllib` ➜ viene con Python.

✔️ `requests` ➜ mejor, más fácil, pero debes instalarlo:

```bash
pip install requests
```

---

### ✅ **Lectura de archivos**

✅ Es abrir un archivo y **leer su contenido**.

---

#### ⭐ Ejemplo 1: Leer texto completo

Supongamos que tienes un archivo **saludo.txt**:

```
Hola mundo
Bienvenido a Python
```

✅ Código:

```python
with open("saludo.txt", "r") as f:
    contenido = f.read()

print(contenido)
```

✅ Salida en consola:

```
Hola mundo
Bienvenido a Python
```

---

✅ Explicación:

- `"r"` ➜ modo lectura (read).
- `with` ➜ asegura que se cierra el archivo.
- `f.read()` ➜ lee todo el contenido.

---

#### ⭐ Ejemplo 2: Leer línea por línea

```python
with open("saludo.txt", "r") as f:
    for linea in f:
        print("Línea:", linea.strip())
```

✅ Salida:

```
Línea: Hola mundo
Línea: Bienvenido a Python
```

✅ `.strip()` ➜ quita saltos de línea.

---

### ✅ **Escritura de archivos**

✅ Crear o sobrescribir un archivo con contenido.

---

#### ⭐ Ejemplo 1: Escribir texto

✅ Código:

```python
with open("nuevo.txt", "w") as f:
    f.write("Hola desde Python\n")
    f.write("Segunda línea\n")

print("Archivo escrito con éxito.")
```

✅ Resultado:

- Archivo **nuevo.txt** con:

```
Hola desde Python
Segunda línea
```

---

✅ Explicación:

- `"w"` ➜ modo escritura (write).
- Si el archivo existe ➜ **se sobrescribe**.
- `\n` ➜ salto de línea.

---

#### ⭐ Ejemplo 2: Agregar contenido

✅ Código:

```python
with open("nuevo.txt", "a") as f:
    f.write("Línea adicional\n")

print("Línea añadida.")
```

✅ Resultado:

- **nuevo.txt** ahora tiene:

```
Hola desde Python
Segunda línea
Línea adicional
```

✅ `"a"` ➜ modo append (agregar al final).

---

### ✅ **Descarga de archivos desde Internet**

✅ Vamos a ver **dos formas**:

✔️ (A) Usando `urllib` (viene con Python).

✔️ (B) Usando `requests` (más fácil).

---

#### ✅ (A) Descarga con urllib

✅ Sin instalar nada.

```python
import urllib.request

url = "https://www.example.com/somefile.txt"
archivo_destino = "descargado.txt"

urllib.request.urlretrieve(url, archivo_destino)

print("Archivo descargado como", archivo_destino)
```

✅ Explicación:

- `urllib.request.urlretrieve()` ➜ descarga el archivo.
- Guarda en **descargado.txt**.

---

✅ Nota:

- urllib ➜ básico.
- No maneja muy bien errores o sesiones.

---

#### ✅ (B) Descarga con `requests` (recomendado)

✅ Primero debes instalar `requests` (si no lo tienes):

```
pip install requests
```

---

✅ Código:

```python
import requests

url = "https://www.example.com/somefile.txt"

respuesta = requests.get(url)

with open("descarga_requests.txt", "wb") as f:
    f.write(respuesta.content)

print("Archivo descargado con requests")
```

✅ Explicación:

- `requests.get(url)` ➜ hace la petición HTTP.
- `.content` ➜ datos binarios.
- `"wb"` ➜ escribir en modo binario (para texto o imágenes).

---

#### ⭐ Descargar imagen (ejemplo real)

```python
import requests

url = "https://www.python.org/static/img/python-logo.png"

r = requests.get(url)

with open("logo_python.png", "wb") as f:
    f.write(r.content)

print("Imagen descargada como logo_python.png")
```

✅ Resultado: imagen guardada localmente.

---

### ✅ **Lectura y escritura combinadas (copia de archivos)**

✅ Ejemplo ➜ leer un archivo y crear una copia.

```python
with open("original.txt", "r") as f_origen:
    contenido = f_origen.read()

with open("copia.txt", "w") as f_destino:
    f_destino.write(contenido)

print("Archivo copiado con éxito.")
```

✅ Explicación:

- Abres original en lectura.
- Lees contenido.
- Escribes en otro archivo.

---

### ✅ Modos de apertura resumidos

| Modo   | Significado                   |
| ------ | ----------------------------- |
| `"r"`  | Leer (falla si no existe)     |
| `"w"`  | Escribir (crea o sobrescribe) |
| `"a"`  | Agregar al final              |
| `"rb"` | Leer en binario               |
| `"wb"` | Escribir en binario           |

✅ Binario ➜ para imágenes, PDF, etc.

---

### ✅ Ejemplo completo (mini-proyecto)

✅ **descargar_guardar.py**:

```python
import requests

# 1. Descargar archivo de texto
url = "https://www.w3.org/TR/PNG/iso_8859-1.txt"
r = requests.get(url)

# 2. Guardar archivo descargado
with open("descargado.txt", "wb") as f:
    f.write(r.content)

print("Archivo descargado.")

# 3. Leer el contenido
with open("descargado.txt", "r", encoding="latin1") as f:
    contenido = f.read()

print("\n--- Contenido del archivo ---")
print(contenido[:200])  # solo las primeras 200 letras

# 4. Escribir un resumen en otro archivo
with open("resumen.txt", "w") as f:
    f.write("Primeras 200 letras del archivo descargado:\n")
    f.write(contenido[:200])

print("\nResumen guardado en resumen.txt")
```

---

✅ Resultado al ejecutar:

```
Archivo descargado.

--- Contenido del archivo ---
The following are the graphical (non-control) characters defined by
ISO 8859-1 (1987).  Descriptions in words
...

Resumen guardado en resumen.txt
```

✅ Genera:

- `descargado.txt` ➜ contenido completo.
- `resumen.txt` ➜ las primeras 200 letras.

---

#### ✅ Instalación resumida

✅ Para **lectura/escritura locales** ➜ nada que instalar.

✅ Para descargas:

- `urllib` ➜ ya incluido.
- `requests` ➜ instalar con:

```
pip install requests
```

---

✅ Verifica Python con:

```
python --version
```

✅ Si no tienes Python ➜ descárgalo de:

- [https://www.python.org/downloads/](https://www.python.org/downloads/)

---

### ✅ Resumen Final

✔️ **Lectura** ➜ `open("archivo", "r")`.

✔️ **Escritura** ➜ `open("archivo", "w")`.

✔️ **Agregar** ➜ `open("archivo", "a")`.

✔️ **Descarga urllib** ➜ incluido en Python.

✔️ **Descarga requests** ➜ instalar con `pip`.

✅ Puedes hacer:

- Procesamiento de texto.
- Copias de archivos.
- Descargar y guardar imágenes o datos.
- Generar reportes.

---

[🔼](#índice)

---

## **160. Inteligencia Artificial aplicada a Hacking Ético y Ciberseguridad**

### ✅ ¿Qué significa "IA aplicada a Hacking Ético y Ciberseguridad"?

**IA (Inteligencia Artificial)** es un conjunto de técnicas que permiten a los sistemas **analizar datos, aprender patrones y tomar decisiones** automáticamente.

**En Ciberseguridad y Hacking Ético**, IA se usa para:

✔️ Detectar ataques y anomalías.

✔️ Analizar logs en busca de intrusiones.

✔️ Automatizar pentesting.

✔️ Generar reportes inteligentes.

✔️ Clasificar malware.

✔️ Predecir amenazas.

✔️ Generar payloads o fuzzing inteligentes.

---

✅ En hacking ético ➜ el especialista usa IA como **herramienta** para:

⭐ Encontrar vulnerabilidades más rápido.

⭐ Revisar enormes volúmenes de datos (logs, tráfico).

⭐ Simular ataques inteligentes.

⭐ Automatizar tareas repetitivas.

---

### ✅ ¿Para qué sirve concretamente? (Ejemplos reales)

✅ _Detección de intrusos (IDS/IPS):_

Usar IA para reconocer patrones anómalos en tráfico de red.

✅ _Análisis de logs:_

IA puede analizar gigabytes de logs y encontrar patrones sospechosos.

✅ _Clasificación de malware:_

Entrenar modelos para diferenciar archivos maliciosos o benignos.

✅ _Fuzzing inteligente:_

Generar entradas maliciosas de forma más efectiva para probar seguridad.

✅ _Reconocimiento de patrones en escaneos:_

Identificar hosts vulnerables basándose en fingerprinting.

✅ _Chatbots defensivos:_

Asistir en respuesta a incidentes (como copilotos de SOC).

✅ _Automatización de OSINT:_

Analizar datos públicos para encontrar datos expuestos.

---

### ✅ Tecnologías típicas usadas en IA para Ciberseguridad

✅ Python (lenguaje más usado)

✅ Bibliotecas de IA:

- scikit-learn
- TensorFlow
- PyTorch

✅ Bibliotecas para datos:

- pandas
- numpy
- matplotlib

✅ Herramientas de ciberseguridad:

- Nmap
- Wireshark/tshark
- Metasploit

✅ Plataformas de SIEM:

- Splunk
- ELK (Elasticsearch, Logstash, Kibana)

---

### ✅ Instalación del entorno en Python

⭐ Para usar IA en ciberseguridad, necesitas:

✅ Python (recomendado 3.8+)

✅ Paquetes para IA y análisis:

```
pip install scikit-learn pandas numpy matplotlib
```

✅ Para redes / hacking ético puedes añadir:

```
pip install python-nmap requests
```

✅ Para redes avanzadas:

```
pip install scapy
```

✅ Para redes neuronales:

```
pip install tensorflow
```

o

```
pip install torch
```

---

✅ Verificar instalación:

```
python --version
```

✅ Ejemplo de importación en un script:

```python
import pandas as pd
import numpy as np
from sklearn.ensemble import RandomForestClassifier
```

---

### ✅ Ejemplo 1: Detección de tráfico sospechoso (simplificado)

**Escenario:** quieres clasificar conexiones como normales o sospechosas.

---

#### 📌 Dataset ficticio:

| bytes_sent | duration | flag_syn | label  |
| ---------- | -------- | -------- | ------ |
| 500        | 10       | 1        | normal |
| 2000       | 60       | 1        | ataque |
| 100        | 5        | 0        | normal |

---

#### 📌 Código paso a paso

✅ 1️⃣ Crear datos:

```python
import pandas as pd

data = {
    'bytes_sent': [500, 2000, 100],
    'duration': [10, 60, 5],
    'flag_syn': [1, 1, 0],
    'label': ['normal', 'ataque', 'normal']
}

df = pd.DataFrame(data)
print(df)
```

✅ 2️⃣ Entrenar modelo:

```python
from sklearn.ensemble import RandomForestClassifier

# Variables (X) y etiquetas (y)
X = df[['bytes_sent', 'duration', 'flag_syn']]
y = df['label']

modelo = RandomForestClassifier()
modelo.fit(X, y)
```

✅ 3️⃣ Predecir tráfico nuevo:

```python
nuevo = [[1500, 45, 1]]
prediccion = modelo.predict(nuevo)
print("Resultado:", prediccion[0])
```

✅ Resultado esperado:

```
Resultado: ataque
```

---

✅ **Explicación:**

- El modelo aprende diferencias entre tráfico normal y malicioso.
- Puedes aplicar esto a logs de firewall o de red reales.

---

### ✅ Ejemplo 2: Análisis de logs para patrones

**Escenario:** detectar anomalías en logs de acceso.

✅ Código:

```python
import pandas as pd

# Simular logs
logs = {
    'ip': ['192.168.1.10', '192.168.1.10', '10.0.0.5', '10.0.0.5', '10.0.0.5'],
    'peticiones': [5, 6, 50, 55, 60]
}

df = pd.DataFrame(logs)

# Regla simple: más de 40 peticiones = sospechoso
df['sospechoso'] = df['peticiones'] > 40

print(df)
```

✅ Resultado:

```
           ip  peticiones  sospechoso
0  192.168.1.10           5       False
1  192.168.1.10           6       False
2      10.0.0.5          50        True
3      10.0.0.5          55        True
4      10.0.0.5          60        True
```

---

✅ **Explicación:**

- Analiza logs con pandas.
- Aplica regla para marcar IPs sospechosas.
- Fácil de adaptar para SIEM o alertas.

---

### ✅ Ejemplo 3: Descarga y análisis de inteligencia de amenazas (OSINT)

**Escenario:** descargar feeds de IPs maliciosas y compararlas.

✅ Código:

```python
import requests

# Descargar lista (ejemplo ficticio)
url = "https://example.com/malicious_ips.txt"
# En la práctica usarías un feed real de abuseipdb o similar
ips_maliciosas = ["10.0.0.5", "203.0.113.1"]

# Logs locales
logs_locales = ["192.168.1.10", "10.0.0.5", "8.8.8.8"]

for ip in logs_locales:
    if ip in ips_maliciosas:
        print(f"ALERTA: IP maliciosa detectada {ip}")
```

✅ Resultado:

```
ALERTA: IP maliciosa detectada 10.0.0.5
```

---

✅ **Explicación:**

- Descarga (o simula) feed de amenazas.
- Compara contra tus logs.
- Automatiza detección de amenazas.

---

### ✅ Uso más avanzado: Redes Neuronales (opcional)

✅ Puedes usar TensorFlow o PyTorch para:

✔️ Clasificación de malware en archivos.

✔️ Detección avanzada de intrusos.

✔️ Modelos de lenguaje para análisis de logs.

✅ Instalación:

```
pip install tensorflow
```

o

```
pip install torch
```

✅ Ejemplo simple con TensorFlow:

```python
import tensorflow as tf

print("TensorFlow version:", tf.__version__)
```

✅ Resultado:

```
TensorFlow version: 2.x
```

✅ Desde ahí puedes construir modelos para clasificación de datos de seguridad.

---

### ✅ ¿Cómo se integra con herramientas de seguridad reales?

✅ Nmap ➜ parsear resultados y buscar vulnerabilidades.

✅ Wireshark ➜ analizar capturas (con scapy).

✅ Metasploit ➜ automatizar ataques (con scripting).

✅ ELK ➜ enviar/recibir datos para dashboards.

✅ SIEM ➜ procesar logs y alertar con IA.

---

✅ Ejemplo simple: ejecutar Nmap y analizar resultados

```python
import nmap

scanner = nmap.PortScanner()
scanner.scan('127.0.0.1', '22-80')

for host in scanner.all_hosts():
    print("Host:", host)
    print("Estado:", scanner[host].state())
    for proto in scanner[host].all_protocols():
        ports = scanner[host][proto].keys()
        for port in ports:
            print(f"Puerto {port} abierto")
```

✅ Salida:

```
Host: 127.0.0.1
Estado: up
Puerto 22 abierto
...
```

---

✅ Puedes aplicar IA para:

- Clasificar hosts vulnerables.
- Priorizar objetivos.
- Detectar patrones de ataque.

---

### ✅ Resumen

✔️ **IA en ciberseguridad** ➜ Analizar datos, detectar ataques, automatizar tareas.

✔️ **Uso en Hacking Ético** ➜ Pentesting inteligente, OSINT automatizado, fuzzing.

✔️ **Instalación básica en Python**:

```
pip install pandas numpy scikit-learn matplotlib requests scapy
```

✔️ **Librerías para IA avanzada**:

```
pip install tensorflow torch
```

---

✅ Con Python puedes:

⭐ Descargar datos ➜ requests

⭐ Analizar ➜ pandas, numpy

⭐ Modelar ➜ scikit-learn, tensorflow

⭐ Hacer hacking ético ➜ nmap, scapy

---

[🔼](#índice)

---

## **161. Potenciando los Dorks con Inteligencia Artificial**

### ✅ ¿Qué es un Dork?

✔️ Un **Google Dork** es una consulta avanzada en motores de búsqueda (Google, Bing, DuckDuckGo) que usa operadores especiales para **encontrar información sensible o vulnerable** expuesta en Internet.

✅ Ejemplos clásicos:

- `site:example.com inurl:admin`
- `intitle:index.of passwd`
- `filetype:sql password`

---

✅ **Uso en hacking ético:**

⭐ Descubrir paneles de administración.

⭐ Encontrar archivos de respaldo públicos.

⭐ Detectar errores de configuración.

⭐ Realizar OSINT.

---

### ✅ ¿Qué significa “potenciar dorks con IA”?

✅ Es **usar Inteligencia Artificial (IA) para mejorar la creación o el uso de dorks**.

✔️ En lugar de escribirlos manualmente, entrenas o usas modelos para:

✅ Generar dorks más efectivos.

✅ Adaptarlos a un objetivo específico.

✅ Clasificar o filtrar dorks útiles.

✅ Encontrar patrones exitosos.

---

✅ **Ejemplo de idea práctica:**

⭐ Darle a un modelo datos de muchos dorks conocidos.

⭐ Pedirle que genere variaciones nuevas.

⭐ Filtrar los que sean más relevantes para cierto dominio o tecnología.

---

✅ Es como tener un **asistente inteligente** que te ayuda a encontrar mejores dorks para pentesting.

---

### ✅ ¿Para qué sirve en hacking ético?

✔️ Aumenta productividad ➜ menos tiempo probando dorks inútiles.

✔️ Encuentra resultados menos obvios ➜ dorks creativos.

✔️ Personaliza ataques ➜ por dominio, por tecnología.

✔️ Ayuda a principiantes ➜ sugiere buenas consultas.

---

✅ Muy útil para:

⭐ OSINT (Open Source Intelligence).

⭐ Bug bounty.

⭐ Red teaming.

⭐ Auditorías web.

---

### ✅ ¿Cómo se puede hacer técnicamente?

✅ **En esencia:**

- Tienes **datos** ➜ una lista grande de dorks conocidos.
- Usas **modelos de lenguaje** ➜ para generar o completar dorks.
- Usas **filtros** ➜ para quedarte con los mejores.

---

✅ Herramientas posibles:

✔️ Modelos de lenguaje ➜ GPT, T5, Bloom, LLaMA.

✔️ Algoritmos de NLP ➜ RNN, transformers.

✔️ Librerías ➜ Hugging Face Transformers, scikit-learn, NLTK.

✅ También se puede hacer con **modelos pequeños entrenados localmente**.

---

✅ Para empezar fácil en Python:

⭐ Usar **transformers** ➜ `pip install transformers`

⭐ Usar **textgen** ➜ `pip install textgenrnn`

⭐ Usar **scikit-learn** ➜ para clustering o filtrado.

---

### ✅ Instalación del entorno (Python)

Para hacer algo sencillo (generación + filtrado):

✅ 1️⃣ Tener Python 3.8+

✅ 2️⃣ Instalar librerías necesarias:

```
pip install transformers torch
pip install pandas scikit-learn
```

✅ Explicación:

- `transformers` ➜ usar modelos de lenguaje.
- `torch` ➜ backend de deep learning.
- `pandas`, `scikit-learn` ➜ analizar y filtrar resultados.

---

### ✅ Ejemplo MUY simple paso a paso

#### 🎯 Objetivo:

✅ Generar nuevos dorks a partir de ejemplos.

✅ Filtrar los más largos o con ciertas palabras clave.

---

✅ PASO 1️⃣: Lista de dorks de entrenamiento

```python
ejemplos_dorks = [
    "site:gov filetype:xls password",
    "intitle:index.of admin",
    "inurl:login site:.edu",
    "filetype:sql intext:password",
    "site:.com inurl:wp-admin"
]
```

---

✅ PASO 2️⃣: Generar variantes con IA

Aquí usamos **Hugging Face transformers** con un modelo de lenguaje de texto simple.

```python
from transformers import pipeline

generator = pipeline("text-generation", model="distilgpt2")

for dork in ejemplos_dorks:
    resultado = generator(dork, max_length=30, num_return_sequences=1)
    print("Entrada:", dork)
    print("Generado:", resultado[0]['generated_text'])
    print()
```

✅ Salida ejemplo (varía):

```
Entrada: site:gov filetype:xls password
Generado: site:gov filetype:xls password admin inurl:login site:gov...

Entrada: intitle:index.of admin
Generado: intitle:index.of admin login user password...
```

---

✅ **Explicación:**

- El modelo aprende el "estilo" del dork.
- Genera variantes que combinan operadores.
- Puedes usar modelos más grandes para mejor calidad.

---

✅ PASO 3️⃣: Filtrar resultados

✅ Supongamos queremos quedarnos **solo con dorks que contengan "login"**:

```python
resultados = [
    "site:gov filetype:xls password admin inurl:login site:gov",
    "intitle:index.of admin login user password",
    "filetype:sql intext:password dump database"
]

filtrados = [d for d in resultados if "login" in d]
print("Dorks filtrados:")
for d in filtrados:
    print("-", d)
```

✅ Salida:

```
Dorks filtrados:
- site:gov filetype:xls password admin inurl:login site:gov
- intitle:index.of admin login user password
```

---

✅ **Resultado:**

- Generaste y filtraste automáticamente.
- Esto se puede aplicar a miles de dorks.
- Es la base para un asistente de OSINT o pentest.

---

### ✅ Ejemplo más pro: guardarlos en un CSV

✅ Código:

```python
import pandas as pd

# Resultado filtrado
data = {
    'dork': filtrados,
    'comentario': ['posible login gov', 'index con admin login']
}

df = pd.DataFrame(data)
df.to_csv("dorks_generados.csv", index=False)

print("Archivo CSV generado con dorks.")
```

✅ Resultado:

- Archivo **dorks_generados.csv**:

| dork                                                          | comentario            |
| ------------------------------------------------------------- | --------------------- |
| site\:gov filetype\:xls password admin inurl\:login site\:gov | posible login gov     |
| intitle\:index.of admin login user password                   | index con admin login |

---

✅ **Explicación:**

- Puedes entregar un reporte a tu equipo.
- O importarlo en Burp Suite o recon tools.

---

### ✅ Idea de proyectos más avanzados

✔️ Entrenar tu propio modelo (finetuning) en un corpus de dorks reales.

✔️ Usar embeddings para agrupar y deduplicar dorks.

✔️ Generar payloads específicos para fuzzing.

✔️ Integrar con un bot de Telegram para OSINT.

✔️ Crear un script que lanza búsquedas automáticas en Google/DuckDuckGo y guarda resultados.

---

### ✅ Resumen paso a paso

✔️ 1️⃣ Colecciona datos (dorks reales).

✔️ 2️⃣ Usa IA ➜ Genera variantes creativas.

✔️ 3️⃣ Filtra ➜ Quita los irrelevantes.

✔️ 4️⃣ Guarda ➜ CSV, base de datos.

✔️ 5️⃣ Usa ➜ en recon, pentesting, OSINT.

---

### ✅ Instalación resumida

Para hacer estos ejemplos en tu máquina:

```
pip install transformers torch pandas scikit-learn
```

✅ Verifica:

```
python --version
```

✅ Si no tienes Python ➜ descargar en [https://www.python.org/downloads/](https://www.python.org/downloads/)

---

### ✅ ¿Qué más se puede hacer?

✔️ Usar modelos grandes (GPT-3.5, GPT-4 via API).

✔️ Entrenar un modelo con tus propios dorks.

✔️ Usar técnicas de NLP para entender el contexto.

✔️ Construir un "Dork Generator" con UI en Flask.

✔️ Integrar en pipelines de OSINT automáticos.

---

✅ ¡Eso es potenciar dorks con IA!

✅ Mezclar hacking ético + NLP + automatización.

✅ Ahorrar tiempo y descubrir más.

---

[🔼](#índice)

---

## **162. OpenAI, GPT-4 y ChatGPT-4**

### ✅ ¿Qué es OpenAI?

**OpenAI** es la empresa que creó los modelos GPT (Generative Pre-trained Transformer).

✅ Es una empresa de investigación en IA.

✅ Desarrolla modelos de lenguaje que generan texto, imágenes, código, etc.

✅ Productos más conocidos:

- GPT-3, GPT-4
- ChatGPT
- DALL·E (imágenes)
- Whisper (audio/transcripción)
- Codex (código)

---

✅ **Idea clave:**

OpenAI = la empresa y la plataforma que te da acceso a sus modelos de IA.

---

### ✅ ¿Qué es GPT-4?

✅ GPT = Generative Pre-trained Transformer.

✅ GPT-4 es **la cuarta generación** de este modelo.

✔️ Es un **modelo de lenguaje grande** (LLM).

✔️ Puede **generar texto, responder preguntas, escribir código, resumir, traducir, etc.**

✔️ Es **más avanzado** que GPT-3.5:

- Mejor comprensión de instrucciones.
- Respuestas más coherentes.
- Mejor manejo de contextos largos.

---

✅ **Ejemplo de uso de GPT-4:**

⭐ Pregunta: “Explícame la teoría de la relatividad como si tuviera 5 años.”

⭐ Respuesta de GPT-4 ➜ texto claro y sencillo.

---

✅ **Importante:** GPT-4 es un **modelo**.

No se “instala” localmente (en tu PC) por defecto.

✅ Se accede **vía la nube (API de OpenAI o apps como ChatGPT)**.

---

### ✅ ¿Qué es ChatGPT (y ChatGPT-4)?

✅ ChatGPT = la **aplicación** (web/app) que usa GPT-3.5 o GPT-4.

✔️ Es una **interfaz conversacional**.

✔️ Puedes chatear como con un humano.

✔️ ChatGPT-4 = ChatGPT usando el modelo GPT-4.

---

✅ **Plan gratuito:**

- Usa GPT-3.5.

✅ **Plan Plus (pago):**

- Puedes elegir GPT-4.

---

✅ **Acceso:**

✔️ Web ➜ [https://chat.openai.com](https://chat.openai.com)

✔️ App ➜ iOS y Android.

---

✅ **Resumen sencillo:**

- **GPT-4** = el modelo.
- **ChatGPT** = la app para usarlo.
- **ChatGPT-4** = usar GPT-4 en ChatGPT (con suscripción Plus).

---

---

### ✅ ¿Para qué sirve GPT-4?

✔️ Redacción de textos.

✔️ Ayuda para escribir o corregir código.

✔️ Resumir documentos.

✔️ Traducir entre idiomas.

✔️ Generar ideas creativas.

✔️ Responder preguntas técnicas.

✔️ Automatizar tareas de atención al cliente.

✔️ Análisis de datos o logs.

✅ **En ciberseguridad:**

✔️ Generar payloads para pruebas.

✔️ Escribir scripts para pentesting.

✔️ Analizar logs.

✔️ Generar reportes.

---

### ✅ ¿Cómo se accede o se “instala” ChatGPT?

⭐ No se instala en tu PC como un programa clásico.

⭐ Se usa como **servicio en la nube**:

✅ Paso 1️⃣ ➜ Crear cuenta en [https://chat.openai.com](https://chat.openai.com)

✅ Paso 2️⃣ ➜ Confirmar tu correo y teléfono.

✅ Paso 3️⃣ ➜ Usar gratis (GPT-3.5) o pagar ChatGPT Plus para GPT-4.

✅ También puedes:

✔️ Descargar la app en Android/iOS.

✔️ Iniciar sesión con tu cuenta.

---

✅ **No necesitas instalar nada en tu PC** si solo quieres chatear.

---

### ✅ ¿Cómo se usa GPT-4 con código Python (API)?

Si quieres usar GPT-4 **en tus propios programas**, necesitas:

✔️ Una **API Key de OpenAI**.

✔️ Instalar la librería **openai**.

---

✅ **Paso 1:** Crea cuenta en OpenAI

✅ Paso 2:\*\* Ve a [platform.openai.com](https://platform.openai.com)

✅ Paso 3:\*\* Consigue tu **API Key**.

---

✅ **Paso 4: Instalar la librería**

```
pip install openai
```

✅ Para la nueva librería (2024):

```
pip install --upgrade openai
```

---

✅ **Paso 5: Usar en Python**

#### ⭐ Ejemplo muy simple:

```python
from openai import OpenAI

client = OpenAI(api_key="TU_API_KEY")

response = client.chat.completions.create(
    model="gpt-4o",
    messages=[
        {"role": "system", "content": "Eres un asistente útil."},
        {"role": "user", "content": "Explícame la teoría de la relatividad de forma sencilla."}
    ]
)

print(response.choices[0].message.content)
```

✅ Salida típica:

```
La teoría de la relatividad dice que el espacio y el tiempo están conectados...
```

---

✅ **Explicación paso a paso:**

✔️ `OpenAI` ➜ cliente oficial.

✔️ `"model": "gpt-4o"` ➜ usa GPT-4o (o "gpt-4" en su plan).

✔️ `messages` ➜ la conversación.

✔️ Devuelve la respuesta generada.

---

### ✅ ¿Qué modelos hay disponibles?

✅ GPT-3.5 ➜ gratis.

✅ GPT-4 ➜ en el plan pago (ChatGPT Plus).

✅ GPT-4o ➜ versión más rápida/multimodal (imágenes + texto).

✅ GPT-4 Turbo ➜ más barato, mayor contexto.

---

✅ En la API, puedes elegir:

```
model="gpt-3.5-turbo"
model="gpt-4"
model="gpt-4o"
```

---

### ✅ Ejemplo un poco más avanzado (resumen de texto)

✅ Supongamos que tienes un texto largo:

```python
from openai import OpenAI

client = OpenAI(api_key="TU_API_KEY")

texto_largo = """
La inteligencia artificial es una rama de la informática que estudia cómo lograr que las máquinas realicen tareas que requieren inteligencia humana...
"""

respuesta = client.chat.completions.create(
    model="gpt-4o",
    messages=[
        {"role": "system", "content": "Eres un asistente experto en resúmenes."},
        {"role": "user", "content": f"Resume este texto en una oración: {texto_largo}"}
    ]
)

print(respuesta.choices[0].message.content)
```

✅ Salida típica:

```
La inteligencia artificial busca que las máquinas realicen tareas inteligentes como los humanos.
```

---

### ✅ ¿Cómo usar GPT-4 en terminal (sin programar)?

✅ Usar ChatGPT en la web:

✔️ [chat.openai.com](https://chat.openai.com)

✔️ Escribes preguntas en el navegador.

✅ Usar el Playground:

✔️ [platform.openai.com/playground](https://platform.openai.com/playground)

✔️ Ajustas parámetros y pruebas.

✅ Usar la app oficial:

✔️ Android / iOS.

---

### ✅ Resumen rápido

⭐ **OpenAI:** empresa que desarrolla GPT.

⭐ **GPT-4:** modelo avanzado de lenguaje.

⭐ **ChatGPT:** app para usar GPT conversacional.

⭐ **ChatGPT-4:** ChatGPT usando GPT-4 (con plan pago).

⭐ **Acceso:** web, app, API.

⭐ **Instalación para API:** `pip install openai`.

⭐ **Uso en código:** generar texto, resúmenes, ideas, código, etc.

---

✅ GPT-4 no es como un programa que te descargas a tu PC y corres localmente (pesa cientos de gigas).

✅ Se usa **a través de la nube** ➜ pagas o usas el plan gratuito limitado.

---

[🔼](#índice)

---

## **163. Potenciando los Dorks con GPT-4**

### ✅ ¿Qué es un “Dork”?

✔️ Un **dork** (o Google Dork) es una consulta avanzada para motores de búsqueda (Google, Bing, DuckDuckGo) que aprovecha operadores especiales para encontrar información sensible o vulnerable.

✅ Ejemplo clásico:

```
site:gov filetype:xls password
```

✔️ Busca hojas de cálculo en sitios .gov que puedan contener “password”.

---

✅ Otros operadores de dorks:

- **site:** restringe a un dominio
- **inurl:** busca en la URL
- **intitle:** busca en el título de la página
- **filetype:** busca tipos de archivos
- **intext:** busca en el contenido

✅ Objetivo de un dork:

- Encontrar archivos sensibles
- Encontrar paneles de administración
- Descubrir directorios expuestos
- Realizar OSINT

---

### ✅ ¿Qué significa “Potenciar los Dorks con GPT-4”?

✅ Normalmente, un hacker ético crea dorks manualmente combinando operadores.

⭐ GPT-4 puede ayudarte a:

✔️ Generar **variantes nuevas** automáticamente

✔️ **Personalizar** dorks para un objetivo (dominio, país, tecnología)

✔️ **Filtrar o mejorar** consultas para ser más efectivas

✔️ Ahorrar **tiempo** en OSINT

✅ Es como tener un asistente que:

🧠 Entiende patrones de dorks

🧠 Sugiere combinaciones creativas

🧠 Adapta las consultas a tu objetivo

---

✅ Ejemplo de **uso humano**:

> "GPT, dame 10 dorks para buscar archivos .pdf con contraseñas en sitios .edu"

✅ Respuesta generada:

```
site:.edu filetype:pdf intext:password
site:.edu filetype:pdf "confidential"
site:.edu inurl:admin filetype:pdf
...
```

✅ ➜ Más rápido, más creativo, más adaptado.

---

### ✅ ¿Para qué sirve en Hacking Ético?

✔️ OSINT más efectivo.

✔️ Recon más automatizado.

✔️ Bug bounty más rápido.

✔️ Red Teaming con menos trabajo manual.

✔️ Reportes más profesionales (con mejores búsquedas).

---

✅ Ejemplo de usos prácticos:

⭐ Encontrar endpoints ocultos

⭐ Buscar configuraciones expuestas

⭐ Encontrar backups

⭐ Descubrir leaks en sites específicos

---

### ✅ ¿Cómo funciona técnicamente?

✅ GPT-4 = un **modelo de lenguaje** capaz de completar o generar texto.

✅ Tú defines **el prompt** ➜ GPT genera **la lista de dorks**.

---

✅ En términos técnicos:

🧭 **Entrada (prompt):**

```
"Dame 10 dorks para buscar archivos .sql con contraseñas en sitios .gov"
```

🧭 **Salida (respuesta GPT):**

```
site:.gov filetype:sql intext:password
site:.gov inurl:backup filetype:sql
...
```

---

✅ Así puedes **automatizar**:

- Generación masiva de dorks
- Personalización por objetivo
- Variación creativa para evadir filtros

---

### ✅ ¿Cómo se instala para usar en Python?

Para acceder a GPT-4 necesitas:

✅ Una cuenta en [OpenAI](https://platform.openai.com)

✅ Obtener **API Key**

---

✅ Librería oficial en Python:

```
pip install --upgrade openai
```

✅ Verificar:

```
python --version
```

✅ Compatible con Python 3.8+

---

### ✅ Preparar el entorno en Python

✅ Crear archivo `.env` (opcional, para guardar tu clave):

```
OPENAI_API_KEY="tu_api_key_aqui"
```

✅ Instalar dotenv si quieres:

```
pip install python-dotenv
```

✅ Librerías a usar:

```bash
pip install openai python-dotenv
```

---

### ✅ Código en Python súper simple

✅ **Ejemplo: Generar 5 dorks con GPT-4**

---

#### 🟢 Paso 1️⃣ Importar librerías

```python
from openai import OpenAI
import os
```

---

#### 🟢 Paso 2️⃣ Configurar la API Key

✅ Manera directa:

```python
client = OpenAI(api_key="TU_API_KEY_AQUI")
```

✅ O si usas `.env`:

```python
from dotenv import load_dotenv
load_dotenv()
client = OpenAI(api_key=os.getenv("OPENAI_API_KEY"))
```

---

#### 🟢 Paso 3️⃣ Definir el prompt

✅ Ejemplo:

```python
prompt_usuario = """
Dame 5 Google Dorks para buscar archivos .sql con contraseñas en sitios .gov.
Hazlos variados y creativos.
"""
```

---

#### 🟢 Paso 4️⃣ Llamar a GPT-4

```python
respuesta = client.chat.completions.create(
    model="gpt-4o",  # o "gpt-4"
    messages=[
        {"role": "system", "content": "Eres un experto en hacking ético y OSINT."},
        {"role": "user", "content": prompt_usuario}
    ]
)
```

---

#### 🟢 Paso 5️⃣ Imprimir resultado

```python
print("Dorks generados por GPT-4:\n")
print(respuesta.choices[0].message.content)
```

---

✅ 🔵 **Posible salida:**

```
1. site:.gov filetype:sql intext:password
2. site:.gov inurl:backup filetype:sql
3. site:.gov "database dump" filetype:sql
4. site:.gov filetype:sql "confidential"
5. site:.gov intext:"admin password" filetype:sql
```

---

✅ **Explicación del resultado:**

- GPT-4 combinó operadores para generar dorks.
- Variaciones creativas adaptadas al objetivo.
- Evita repetir lo mismo.

---

### ✅ Personalizar el prompt

✅ Puedes cambiar fácilmente:

⭐ Por país:

```
"Dame 10 dorks para buscar archivos .pdf confidenciales en sitios .pe"
```

⭐ Por tecnología:

```
"Dame 5 dorks para encontrar paneles de admin en WordPress"
```

⭐ Por archivo:

```
"Dame 5 dorks para archivos .xlsx con datos bancarios"
```

✅ GPT-4 se adapta.

---

### ✅ Ejemplo más avanzado: generar y guardar en CSV

✅ Instalar pandas:

```
pip install pandas
```

✅ Código:

```python
import pandas as pd

dorks_generados = respuesta.choices[0].message.content.split("\n")

df = pd.DataFrame({'dork': dorks_generados})
df.to_csv("dorks_gpt4.csv", index=False)

print("Dorks guardados en dorks_gpt4.csv")
```

---

✅ Resultado:

✔️ Archivo **dorks_gpt4.csv** con tu lista.

✔️ Puedes cargarlo en Burp Suite, recon tools, etc.

---

### ✅ Idea aún más PRO

✅ Loop en Python:

✔️ Generar 50 dorks en lotes de 10.

✔️ Filtrar por longitud o palabras clave.

✔️ Guardar todo en un repositorio.

---

✅ Concepto:

⭐ Usar GPT-4 como **asistente de OSINT**

⭐ Automatizar la generación de payloads para Google, Bing, DuckDuckGo

---

### ✅ Resumen para principiantes

✅ OpenAI ➜ empresa y API.

✅ GPT-4 ➜ modelo de lenguaje avanzado.

✅ Potenciar dorks ➜ usar GPT-4 para:

- Generarlos automáticamente
- Variarlos
- Adaptarlos al objetivo

✅ Instalación fácil:

```
pip install --upgrade openai python-dotenv
```

✅ Código muy simple:

```python
from openai import OpenAI
client = OpenAI(api_key="TU_API_KEY")
...
```

✅ Resultado ➜ cientos de dorks nuevos para OSINT o pentesting.

---

### ✅ ¿Para qué sirve en hacking ético?

✔️ Reconocimiento más eficaz.

✔️ Ahorra tiempo creando queries.

✔️ Resultados personalizados.

✔️ Automatización para bug bounty o auditorías.

---

[🔼](#índice)

---

## **164. Google Hacking con Inteligencia Artificial**

### ✅ ¿Qué es Google Hacking?

⭐ **Google Hacking** es el arte de usar operadores de búsqueda avanzados en Google para encontrar información sensible, mal configurada o expuesta de forma involuntaria.

✅ Ejemplos básicos:

- `site:.gov filetype:xls password`

  > Archivos de Excel con "password" en sitios .gov

- `intitle:index.of "backup"`

  > Directorios expuestos con backups

- `inurl:admin`

  > URLs con "admin" para posibles paneles de administración

---

✅ **Usos éticos:**

✔️ OSINT (inteligencia de fuentes abiertas)

✔️ Pentesting (reconocimiento)

✔️ Bug Bounty (hallar vulnerabilidades)

✔️ Auditorías de exposición en Internet

---

✅ Los **dorks** = las “queries” avanzadas que usas en Google.

---

### ✅ ¿Qué significa “Google Hacking con IA”?

**Idea clave:**

✅ Usar **Inteligencia Artificial (IA)** para **ayudarte a generar, personalizar o mejorar** tus Google Dorks.

✅ En vez de hacerlos todos tú manualmente, la IA te puede:

⭐ Generar dorks creativos y variados

⭐ Personalizarlos para dominios o países específicos

⭐ Filtrarlos por utilidad

⭐ Crear grandes listas para automatizar OSINT

---

**Ejemplo de uso:**

> Tú dices:
>
> “Dame 10 dorks para buscar archivos SQL con passwords en sitios .edu”

✔️ IA genera:

```
site:.edu filetype:sql intext:password
site:.edu inurl:backup filetype:sql
site:.edu "database dump" filetype:sql
...
```

✅ Resultado: _ahorro de tiempo y mejores resultados_.

---

### ✅ ¿Para qué sirve en Hacking Ético?

✔️ Reconocer más rápido objetivos o vulnerabilidades.

✔️ Encontrar información expuesta.

✔️ Automatizar la parte aburrida del OSINT.

✔️ Personalizar dorks para un cliente o dominio.

✔️ Ser más creativo y efectivo.

---

✅ Escenarios reales:

⭐ Auditoría de un sitio gubernamental.

⭐ Red Teaming (sin alertar al target).

⭐ Preparar un bug bounty.

⭐ Crear un reporte profesional.

---

### ✅ ¿Cómo se “instala” o se prepara?

¡Ojo! La IA (como GPT-4) no se instala en tu PC como un programa local.

✅ GPT-4 se usa **en la nube (API)**.

✅ Para hacerlo en **Python** necesitas:

✔️ Una **API Key** de OpenAI (desde [https://platform.openai.com/](https://platform.openai.com/))

✔️ Instalar la librería oficial:

```
pip install --upgrade openai
```

✅ Para guardar la clave de forma segura (opcional):

```
pip install python-dotenv
```

---

✅ Resumen de instalación:

```bash
pip install --upgrade openai python-dotenv
```

✅ Verificar:

```bash
python --version
```

---

### ✅ ¿Cómo funciona con GPT-4?

⭐ GPT-4 es un modelo de lenguaje **muy grande**.

⭐ Le das **prompts** ➜ genera texto con lógica.

⭐ Puedes pedirle que actúe como un **generador de dorks**.

---

✅ Ejemplo simple:

**Prompt:**

```
Dame 5 Google Dorks para buscar documentos PDF con contraseñas en sitios .gov
```

**GPT-4 genera:**

```
site:.gov filetype:pdf intext:password
site:.gov filetype:pdf "confidential"
site:.gov "login credentials" filetype:pdf
...
```

✅ IA = _tu asistente de OSINT_.

---

### ✅ Ejemplo completo en Python (fácil)

✅ Paso 1️⃣ Importar librerías:

```python
from openai import OpenAI
import os
```

---

✅ Paso 2️⃣ Configurar la API Key

✔️ Opción directa (no recomendado en producción):

```python
client = OpenAI(api_key="TU_API_KEY_AQUI")
```

✔️ Opción segura (usando .env):

1️⃣ Crear archivo `.env`:

```
OPENAI_API_KEY="TU_API_KEY_AQUI"
```

2️⃣ Código:

```python
from dotenv import load_dotenv
load_dotenv()
client = OpenAI(api_key=os.getenv("OPENAI_API_KEY"))
```

---

✅ Paso 3️⃣ Definir el prompt

```python
prompt_usuario = """
Eres un experto en hacking ético.
Genera 5 Google Dorks variados para buscar archivos SQL con contraseñas en sitios .edu.
"""
```

---

✅ Paso 4️⃣ Llamar a GPT-4

```python
respuesta = client.chat.completions.create(
    model="gpt-4o",
    messages=[
        {"role": "system", "content": "Eres un generador de Google Dorks para OSINT."},
        {"role": "user", "content": prompt_usuario}
    ]
)
```

---

✅ Paso 5️⃣ Imprimir resultado

```python
print("\nDorks sugeridos por GPT-4:\n")
print(respuesta.choices[0].message.content)
```

---

✅ Resultado típico:

```
1. site:.edu filetype:sql intext:password
2. site:.edu inurl:backup filetype:sql
3. site:.edu "database dump" filetype:sql
4. site:.edu filetype:sql "confidential"
5. site:.edu intext:"admin password" filetype:sql
```

---

### ✅ Personalizando el Prompt

⭐ Puedes pedir:

✅ Por país:

```
Dame 10 dorks para buscar archivos PDF confidenciales en sitios .pe
```

✅ Por tecnología:

```
Dame 5 dorks para encontrar paneles de admin en WordPress
```

✅ Por archivo:

```
Dame 5 dorks para archivos .xlsx con datos bancarios
```

✅ GPT-4 ➜ adapta su respuesta.

---

### ✅ Generar y Guardar en CSV

✅ Instalar pandas:

```
pip install pandas
```

✅ Código:

```python
import pandas as pd

# Dividir la respuesta en líneas
dorks = respuesta.choices[0].message.content.split("\n")

# Guardar en CSV
df = pd.DataFrame({'dork': dorks})
df.to_csv("dorks_generados.csv", index=False)

print("✅ Archivo dorks_generados.csv creado.")
```

✅ Resultado:

✔️ Archivo con todos los dorks generados.

✔️ Fácil de usar en Burp, recon tools, reportes.

---

### ✅ Usos avanzados

✅ GPT-4 puede ayudarte a:

⭐ Generar dorks por industria (bancos, gobiernos, universidades).

⭐ Crear listas para Google, Bing, DuckDuckGo.

⭐ Filtrar resultados automáticamente.

⭐ Integrarlo en pipelines de OSINT.

⭐ Hacer un bot para Telegram que genere dorks on-demand.

---

✅ Ejemplo de prompt más avanzado:

```
Crea 10 Google Dorks para encontrar páginas de login de aplicaciones bancarias en Perú. Incluye variaciones creativas.
```

✅ GPT-4 devuelve:

```
site:.pe inurl:login bank
site:.pe intitle:"banking login"
...
```

---

### ✅ Resumen rápido

⭐ **Google Hacking:** usar operadores de búsqueda avanzados.

⭐ **IA (GPT-4):** genera dorks más creativos, personalizados y variados.

⭐ **Ventajas:** ahorra tiempo, mejora resultados, automatiza OSINT.

✅ **Instalación en Python:**

```
pip install --upgrade openai python-dotenv
```

✅ **Código básico:**

```python
from openai import OpenAI
client = OpenAI(api_key="TU_API_KEY")
respuesta = client.chat.completions.create(
    model="gpt-4o",
    messages=[
        {"role": "system", "content": "Eres un generador de Google Dorks."},
        {"role": "user", "content": "Dame 5 dorks para buscar archivos PDF confidenciales en sitios .gov"}
    ]
)
print(respuesta.choices[0].message.content)
```

---

✅ **Resultado:**

✔️ Listas de dorks personalizadas.

✔️ Automáticas.

✔️ Profesionales.

---

[🔼](#índice)

---

## **165. Filtrado de información con Expresiones Regulares**

### ✅ ¿Qué son las Expresiones Regulares (Regex)?

Las **expresiones regulares** son patrones de búsqueda usados para **encontrar, validar, reemplazar o extraer texto**.

Son como “filtros inteligentes” para cadenas de texto.

---

#### 📌 Ejemplos:

| Tarea                 | Expresión Regular (Ejemplo)                           |     |     |
| --------------------- | ----------------------------------------------------- | --- | --- |
| Detectar email        | `\b[\w.-]+@[\w.-]+\.\w{2,4}\b`                        |     |     |
| Detectar IP           | `\b(?:\d{1,3}\.){3}\d{1,3}\b`                         |     |     |
| Buscar URL            | `https?://[^\s]+`                                     |     |     |
| Detectar números      | `\d+`                                                 |     |     |
| Buscar palabras clave | `(?i)password                 \| clave \| contraseña` |

---

### ✅ ¿Para qué sirven en Ciberseguridad y Hacking Ético?

✅ Analizar archivos de logs

✅ Extraer emails, IPs o contraseñas filtradas

✅ Buscar tokens, claves API

✅ Detectar patrones en texto (como comandos sospechosos)

✅ Filtrar resultados de scrapers o dorks

---

#### 📌 Escenario real:

Tienes un archivo de texto con 10,000 líneas y necesitas extraer **solo los correos electrónicos** o las **URLs con login** → **Regex lo hace en segundos.**

---

### ✅ ¿Cómo se instalan y usan en Python?

¡No necesitas instalar nada extra!

✅ Python ya incluye el módulo `re` para expresiones regulares.

Solo importa:

```python
import re
```

---

### ✅ Ejemplos muy fáciles

---

#### 📌 Ejemplo 1: Buscar un email en un texto

```python
import re

texto = "Hola, puedes contactarme en contacto@ejemplo.com para más detalles."

patron_email = r"\b[\w.-]+@[\w.-]+\.\w{2,4}\b"

resultado = re.findall(patron_email, texto)

print("Correo encontrado:", resultado)
```

🟢 Salida:

```
Correo encontrado: ['contacto@ejemplo.com']
```

---

#### 📌 Ejemplo 2: Detectar todas las direcciones IP en un archivo

```python
texto = """
Intento desde 192.168.0.1 fallido.
Nuevo acceso desde 10.0.0.55 autorizado.
"""

patron_ip = r"\b(?:\d{1,3}\.){3}\d{1,3}\b"

ips = re.findall(patron_ip, texto)

print("IPs encontradas:", ips)
```

🟢 Salida:

```
IPs encontradas: ['192.168.0.1', '10.0.0.55']
```

---

#### 📌 Ejemplo 3: Buscar líneas que contengan “password” o “clave”

```python
texto = """
password=123456
usuario=admin
clave: qwerty
"""

patron = r"(?i)(password|clave).+"

resultados = re.findall(patron, texto)

print("Coincidencias:", resultados)
```

---

#### 📌 Ejemplo 4: Extraer URLs de texto

```python
texto = """
Visita nuestra web en https://www.misitio.com o http://login.site.org para más info.
"""

patron_url = r"https?://[^\s]+"

urls = re.findall(patron_url, texto)

print("URLs encontradas:", urls)
```

🟢 Salida:

```
['https://www.misitio.com', 'http://login.site.org']
```

---

### ✅ ¿Cómo integrarlo con archivos?

#### 📌 Leer un archivo `.txt` y extraer correos

```python
with open("data.txt", "r", encoding="utf-8") as archivo:
    contenido = archivo.read()

patron_email = r"\b[\w.-]+@[\w.-]+\.\w{2,4}\b"
correos = re.findall(patron_email, contenido)

print("Correos encontrados:", correos)
```

---

### ✅ ¿Cómo integrar con scraping?

Supón que obtienes código HTML o texto desde una web, puedes usar regex para buscar datos sensibles:

```python
html = """
<form>
  <input type="text" name="user">
  <input type="password" name="pass">
</form>
"""

# Detectar campos de contraseñas en formularios
patron = r'<input.*?type="password".*?>'

resultados = re.findall(patron, html)

print("Campos de contraseña encontrados:", resultados)
```

---

### ✅ Tabla de patrones útiles en Regex

| Tarea          | Regex                                                                           | Descripción                        |     |     |
| -------------- | ------------------------------------------------------------------------------- | ---------------------------------- | --- | --- |
| Número         | `\d+`                                                                           | Uno o más dígitos                  |     |     |
| Palabra        | `\w+`                                                                           | Letras, números y guiones bajos    |     |     |
| Espacios       | `\s+`                                                                           | Espacios, tabs, saltos de línea    |     |     |
| Email          | `[\w.-]+@[\w.-]+\.\w{2,4}`                                                      | Emails simples                     |     |     |
| URL            | `https?://[^\s]+`                                                               | URLs que empiezan con http o https |     |     |
| IP             | `(?:\d{1,3}\.){3}\d{1,3}`                                                       | Dirección IP                       |     |     |
| Palabras clave | `(?i)(clave               \| password                           \| contraseña)` | Busca sin distinguir mayúsculas    |

---

### ✅ ¿Cómo se prueba Regex fácilmente?

Puedes practicar en línea en estas webs:

- [regex101.com](https://regex101.com/)
- [pythex.org](https://pythex.org/)
- [regexr.com](https://regexr.com/)

✅ Allí puedes ver qué coincide con tu patrón, línea por línea.

---

### ✅ ¿Cómo detectar vulnerabilidades con regex?

Supón que haces scraping o buscas archivos filtrados (ej: leaks de contraseñas), puedes buscar con regex:

✅ API keys:

```python
r"AIza[0-9A-Za-z-_]{35}"   # Google API Key
```

✅ Tokens JWT:

```python
r"eyJ[A-Za-z0-9-_]+\.[A-Za-z0-9-_]+\.[A-Za-z0-9-_]+"
```

✅ Contraseñas en texto:

```python
r"(password|clave|contraseña)\s*[=:]\s*\S+"
```

---

### ✅ Resumen paso a paso

| Paso | Acción                                                      |
| ---- | ----------------------------------------------------------- |
| 1️⃣   | Asegúrate de tener Python instalado                         |
| 2️⃣   | Usa `import re` (sin instalar nada)                         |
| 3️⃣   | Define el patrón que quieres buscar                         |
| 4️⃣   | Usa `re.findall(patron, texto)` para obtener los resultados |
| 5️⃣   | Filtra datos en logs, webs, correos, IPs, etc.              |

---

[🔼](#índice)

---

## **166. Filtrado de información con Inteligencia Artificial**

### ✅ ¿Qué es “Filtrado de Información con Inteligencia Artificial”?

**Filtrar información** = Separar lo que te interesa del “ruido”.

✅ En ciberseguridad, scraping, análisis de datos ➜ recibes _muchísima_ información (logs, resultados de dorks, texto web).

✅ Necesitas **quedarte solo con lo útil**.

✅ Filtrar = buscar, extraer, clasificar, resumir, descartar.

---

✅ **Con IA** (como GPT-4):

✔️ No usas reglas fijas duras (regex sola, if/else).

✔️ Puedes pedirle cosas más complejas en lenguaje natural.

✔️ Puede entender contexto y lenguaje humano.

✔️ Genera resúmenes, clasifica, organiza, etiqueta.

---

**💡 Ejemplo comparativo:**

| Método | Qué hace                                                                                     |
| ------ | -------------------------------------------------------------------------------------------- |
| Regex  | “Dame todas las líneas con la palabra ‘password’.”                                           |
| IA     | “Léete este archivo y dime qué líneas parecen contener credenciales o información sensible.” |

---

### ✅ ¿Para qué sirve en Ciberseguridad / OSINT?

✅ Clasificar resultados de scraping (dorks) ➜ separar útiles de basura.

✅ Extraer indicadores de compromiso (IPs, URLs maliciosas).

✅ Resumir logs o datos largos.

✅ Detectar leaks (contraseñas, tokens, claves API).

✅ Generar reportes resumidos para clientes.

---

✅ Usos típicos:

- Filtrar cientos de resultados de Google Dorks
- Revisar dumps de bases de datos expuestas
- Analizar logs enormes
- Separar datos válidos en OSINT

---

### ✅ ¿Cómo se hace con GPT-4? (Idea sencilla)

✔️ Tú le envías texto.

✔️ Le das un **prompt** claro.

✔️ GPT-4 responde con lo que filtra o resume.

---

✅ 💡 Ejemplo de prompt:

> “Analiza este texto y extrae solo las líneas que contengan contraseñas o claves API.”

---

✅ GPT-4 es **multitarea**:

✔️ Filtrar contenido

✔️ Resumir

✔️ Clasificar

✔️ Etiquetar

✔️ Reescribir en formato JSON

---

### ✅ Instalación en Python

✅ GPT-4 se usa **en la nube**, no se instala en tu PC como un modelo gigante.

✅ Necesitas:

✔️ Una **API Key** de OpenAI ➜ [platform.openai.com](https://platform.openai.com)

✔️ Instalar la librería oficial:

```bash
pip install --upgrade openai
```

✅ Opcional para guardar la clave en un archivo `.env`:

```bash
pip install python-dotenv
```

---

✅ Estructura de tu proyecto:

```
mi-proyecto/
  |-- filtrar.py
  |-- .env
```

---

✅ Ejemplo de archivo `.env`:

```
OPENAI_API_KEY="tu_api_key_aqui"
```

---

### ✅ Código Python muy fácil

✅ **Importar librerías:**

```python
from openai import OpenAI
import os
from dotenv import load_dotenv
```

✅ **Cargar la API Key:**

```python
load_dotenv()
client = OpenAI(api_key=os.getenv("OPENAI_API_KEY"))
```

---

✅ **Definir texto con datos mixtos:**

```python
texto = """
usuario: admin
password: 123456
clave API: sk-abcdef12345
correo: ejemplo@correo.com
nota: no compartir esta info
"""
```

---

✅ **Definir el prompt para filtrar:**

```python
prompt = f"""
Analiza el siguiente texto y extrae solo las líneas que contienen contraseñas o claves API.

Texto:
{texto}
"""
```

---

✅ **Llamar a GPT-4 para filtrar:**

```python
respuesta = client.chat.completions.create(
    model="gpt-4o",
    messages=[
        {"role": "system", "content": "Eres un asistente experto en ciberseguridad."},
        {"role": "user", "content": prompt}
    ]
)
```

---

✅ **Imprimir resultado:**

```python
print("\nRESULTADO FILTRADO:")
print(respuesta.choices[0].message.content)
```

---

✅ **Posible salida:**

```
password: 123456
clave API: sk-abcdef12345
```

---

**💡 Fíjate:**

✔️ GPT-4 entendió el texto.

✔️ Extrajo solo lo que pediste.

✔️ Ignoró correos o notas irrelevantes.

---

### ✅ Otro ejemplo: Clasificación

✅ Texto mixto:

```python
texto = """
192.168.1.1 - Acceso permitido
10.0.0.5 - Intento fallido
usuario: admin
password=letmein
clave API: sk-abcde
"""
```

✅ Prompt más avanzado:

```python
prompt = f"""
Analiza el siguiente texto. Clasifica las líneas en dos categorías: 'Credenciales' y 'Logs de Acceso'.

Texto:
{texto}

Devuelve la respuesta en formato JSON.
"""
```

✅ GPT-4 genera:

```
{
  "Credenciales": [
    "usuario: admin",
    "password=letmein",
    "clave API: sk-abcde"
  ],
  "Logs de Acceso": [
    "192.168.1.1 - Acceso permitido",
    "10.0.0.5 - Intento fallido"
  ]
}
```

---

✅ Así puedes:

✔️ Procesar resultados de dorks.

✔️ Clasificar logs.

✔️ Generar datos estructurados automáticamente.

---

### ✅ Resumen: Cómo se instala

✅ Solo necesitas:

```
pip install --upgrade openai python-dotenv
```

✅ Configurar tu `.env`:

```
OPENAI_API_KEY="tu_api_key_aqui"
```

✅ Escribir tu script en Python:

✔️ Importar librerías

✔️ Cargar tu API Key

✔️ Preparar tu texto

✔️ Escribir tu prompt

✔️ Obtener y procesar la respuesta

---

### ✅ Ideas prácticas para ciberseguridad

✅ Filtrar dumps de contraseñas:

```
"Filtra solo las líneas que parezcan credenciales con usuario y contraseña."
```

✅ Analizar resultados de scraping:

```
"Revisa este texto y extrae solo las URLs de login."
```

✅ Resumir logs enormes:

```
"Resume los incidentes críticos de este log en 5 líneas."
```

✅ Formato estructurado:

```
"Extrae emails e IPs de este texto y devuélvelos como JSON."
```

---

### ✅ Ventajas frente a Regex puro

| Característica            | Regex          | IA (GPT-4)            |
| ------------------------- | -------------- | --------------------- |
| Patrón fijo               | ✅ Muy bueno   | ⚠️ No necesario       |
| Entender lenguaje natural | ❌ No puede    | ✅ Sí                 |
| Contexto y variaciones    | ❌ Limitado    | ✅ Excelente          |
| Clasificación compleja    | ❌ Muy difícil | ✅ Muy fácil          |
| Salida estructurada       | ❌ Manual      | ✅ Puede generar JSON |

---

✅ **Mejor juntos:**

Usa regex para cosas muy simples y GPT-4 para filtrados más complejos o contexto.

---

### ✅ Bonus: Script básico completo

```python
from openai import OpenAI
from dotenv import load_dotenv
import os

# Cargar API Key
load_dotenv()
client = OpenAI(api_key=os.getenv("OPENAI_API_KEY"))

# Texto de ejemplo
texto = """
usuario: admin
password=123456
API KEY: sk-test-abcde123
email: test@example.com
"""

# Prompt para filtrar credenciales
prompt = f"""
Eres un asistente de ciberseguridad. Filtra el siguiente texto y devuelve solo las líneas que contengan contraseñas o claves API.

Texto:
{texto}
"""

# Llamada a GPT
response = client.chat.completions.create(
    model="gpt-4o",
    messages=[
        {"role": "system", "content": "Eres un experto en filtrado de información sensible."},
        {"role": "user", "content": prompt}
    ]
)

# Mostrar resultado
print("\nRESULTADO FILTRADO:\n")
print(response.choices[0].message.content)
```

---

✅ Salida típica:

```
password=123456
API KEY: sk-test-abcde123
```

---

### ✅ Resumen para ti:

✅ IA ➜ entiende texto como un humano.

✅ Puedes darle instrucciones naturales.

✅ GPT-4 ➜ filtra, clasifica, resume, estructura.

✅ Instalación ➜ solo `openai` y `python-dotenv`.

✅ Código ➜ súper simple, solo defines tu prompt.

---

**Conclusión:**

✅ Filtrar con IA = ahorrar horas de trabajo, hacer OSINT más fácil, resultados más útiles.

---

[🔼](#índice)

---

## **167. Integra SmartSearch con NinjaDork**

### ✅ ¿Qué es NinjaDork?

⭐ NinjaDork es una **herramienta para hacking ético / OSINT** diseñada para:

✔️ Generar automáticamente **Google Dorks**.

✔️ Organizar dorks por categorías (admin panels, backups, passwords, etc.).

✔️ Facilitar búsquedas avanzadas para **encontrar información sensible en la web**.

✅ Objetivo principal:

> Ahorrar tiempo creando queries de Google Hacking.

✅ Ejemplo de dork generado por NinjaDork:

```
site:.gov filetype:xls intext:password
```

---

✅ ✔️ Funciona típicamente como **script en Python** o como **herramienta CLI** (según la versión).

✅ ✔️ Muchos repositorios en GitHub (código abierto).

---

### ✅ ¿Qué es SmartSearch?

✅ SmartSearch NO es _una herramienta_ oficial única: es más un **concepto** o patrón que se usa en OSINT / recon:

✔️ “Smart Search” = usar búsquedas **más inteligentes**, personalizadas y filtradas.

✔️ Incluye:

- Variantes creativas de dorks
- Uso de operadores avanzados (inurl, intitle, site, filetype)
- Filtrado semántico (temas, países, tipos de archivos)
- Combinación con inteligencia artificial para sugerencias

---

✅ Algunas herramientas o scripts usan “SmartSearch” como nombre o módulo:

⭐ Idea:

> Genera búsquedas adaptadas a tu objetivo en lugar de dorks genéricos.

✅ Ejemplo de SmartSearch:

```
site:.pe filetype:pdf "confidencial"
```

✔️ Es más dirigido y adaptado.

---

✅ **Resumen:**

✔️ NinjaDork = Generador automático de Dorks.

✔️ SmartSearch = Búsquedas personalizadas e inteligentes (operadores + IA).

---

### ✅ ¿Para qué sirve combinarlos?

⭐ Juntos → **workflow más potente para OSINT y Hacking Ético**:

✅ NinjaDork ➜ genera decenas o cientos de dorks base.

✅ SmartSearch ➜ filtra, adapta, personaliza, mejora.

---

✅ Uso real:

1️⃣ NinjaDork genera 100 dorks.

2️⃣ SmartSearch filtra:

- País específico
- Archivo específico
- Tema o industria

  3️⃣ Resultado ➜ lista de 10-20 dorks ultra relevantes para tu objetivo.

---

✅ Otra forma:

- NinjaDork ➜ salida inicial.
- GPT-4 (o SmartSearch con IA) ➜ “hazlos más creativos” o “ajústalos a .edu”.

---

### ✅ ¿Cómo se “instala” o prepara el entorno?

✅ **Paso 1:** Tener Python instalado (3.8+ recomendado):

```bash
python --version
```

✅ **Paso 2:** Crear un entorno virtual (opcional pero recomendado):

```bash
python -m venv venv
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate     # Windows
```

✅ **Paso 3:** Instalar dependencias típicas:

```bash
pip install requests openai python-dotenv
```

✅ **Paso 4:** Descargar o clonar NinjaDork

Ejemplo con Git:

```bash
git clone https://github.com/someuser/NinjaDork.git
cd NinjaDork
```

✅ Muchas versiones son scripts `.py`, a veces `.sh`.

---

✅ **Uso típico:**

```bash
python ninja_dork.py -o output.txt
```

✔️ Genera archivo `output.txt` con docenas o cientos de dorks.

---

### ✅ Ejemplo de flujo manual

✔️ NinjaDork genera:

```
site:.com inurl:admin
site:.edu filetype:pdf intext:password
site:.gov intitle:"index of"
...
```

---

✔️ Ahora quieres **SmartSearch**:

> Filtra los que:
>
> - Sean para Perú (.pe)
>
> - Busquen PDFs

✅ Filtrados manualmente:

```
site:.pe filetype:pdf intext:password
site:.pe intitle:"index of"
```

---

### ✅ Integrarlo con IA (SmartSearch con GPT)

✅ ✔️ Vamos a hacerlo en **Python**:

✅ Supongamos que **NinjaDork** generó este archivo:

```
dorks.txt:
site:.com inurl:admin
site:.edu filetype:pdf intext:password
site:.gov intitle:"index of"
```

---

✅ Código para filtrar con GPT-4:

#### 🟢 1️⃣ Instalar:

```bash
pip install openai python-dotenv
```

---

#### 🟢 2️⃣ Crear `.env`:

```
OPENAI_API_KEY="tu_api_key_aqui"
```

---

#### 🟢 3️⃣ Código ejemplo en `smartsearch_filter.py`:

```python
import os
from openai import OpenAI
from dotenv import load_dotenv

# Cargar clave
load_dotenv()
client = OpenAI(api_key=os.getenv("OPENAI_API_KEY"))

# Leer archivo de dorks
with open("dorks.txt", "r", encoding="utf-8") as f:
    dorks = f.read()

# Prompt para IA
prompt = f"""
Eres un experto en OSINT y Google Hacking. A continuación tienes una lista de dorks.

Filtra solo los que sean útiles para buscar archivos PDF confidenciales en sitios .pe. Si no hay ninguno, crea variantes adaptadas.

Lista:
{dorks}
"""

# Llamada a GPT
respuesta = client.chat.completions.create(
    model="gpt-4o",
    messages=[
        {"role": "system", "content": "Eres un asistente experto en filtrado de Google Dorks."},
        {"role": "user", "content": prompt}
    ]
)

# Resultado
print("\nDorks filtrados o generados:\n")
print(respuesta.choices[0].message.content)
```

---

✅ ¿Qué hace esto?

✔️ Lee el output de NinjaDork.

✔️ Envía el contenido a GPT.

✔️ GPT filtra o adapta a tu criterio (“PDF en .pe”).

✔️ Devuelve una lista más relevante.

---

### ✅ Resultado típico:

```
site:.pe filetype:pdf intext:password
site:.pe filetype:pdf "confidencial"
site:.pe inurl:documents filetype:pdf
```

---

✅ Ahora tienes:

✔️ Generación masiva (NinjaDork) ➜ cientos de dorks.

✔️ Filtrado inteligente (SmartSearch con GPT) ➜ 5-10 dorks útiles.

---

### ✅ ¿Cómo guardar los resultados?

✅ Puedes guardar la salida en un archivo:

```python
with open("filtered_dorks.txt", "w", encoding="utf-8") as f:
    f.write(respuesta.choices[0].message.content)
```

---

✅ Resultado:

✔️ Archivo `filtered_dorks.txt` con tu lista final.

---

### ✅ Resumen paso a paso

| Paso | Qué haces                                           |
| ---- | --------------------------------------------------- |
| 1️⃣   | Instalas Python y pip                               |
| 2️⃣   | Clonas/descargas NinjaDork                          |
| 3️⃣   | Generas lista grande de dorks                       |
| 4️⃣   | Instalas openai y dotenv                            |
| 5️⃣   | Creas tu `.env` con API Key                         |
| 6️⃣   | Escribes un script para filtrado con GPT            |
| 7️⃣   | Ejecutas ➜ consigues lista filtrada y personalizada |

---

✅ Así integras:

⭐ **NinjaDork** = generación masiva.

⭐ **SmartSearch con IA** = filtrado y personalización avanzada.

---

### ✅ Variaciones más avanzadas

✔️ Filtrar por país, archivo, tema:

```
"Filtra solo los dorks para .gov en México que busquen archivos Excel."
```

✔️ Generar JSON estructurado:

```
"Devuelve la lista en formato JSON con campos: dork, objetivo, categoría."
```

✔️ Clasificar en categorías:

```
"Clasifica estos dorks en: backups, passwords, admin panels."
```

---

✅ ➜ Puedes convertirlo en:

⭐ CLI con argparse

⭐ Webapp en Flask / Django

⭐ Bot para Telegram

---

### ✅ Conclusión

✅ NinjaDork ➜ genera **cantidad**.

✅ SmartSearch (con IA) ➜ filtra y personaliza **calidad**.

✅ Juntos ➜ OSINT más rápido, profesional y efectivo.

---

[🔼](#índice)

---

## **168. Emulando el comportamiento humano con Selenium**

### ✅ ¿Qué es Selenium?

**Selenium** es un **framework** que te permite **automatizar navegadores web**.

✔️ Abre un navegador real (Chrome, Firefox, Edge...).

✔️ Hace clics, escribe, navega, igual que un humano.

✔️ Captura contenido dinámico (JavaScript, AJAX).

✅ Es usado para:

- Pruebas automáticas de sitios web.
- Scraping de sitios que requieren login o interacciones.
- Emular usuarios para OSINT (registro, búsqueda, etc.).
- Verificar si bots son detectados (Red Team).

---

✅ 🟢 Ejemplo básico de lo que hace:

- Abre Chrome.
- Va a `https://google.com`.
- Escribe “OpenAI” en el cuadro de búsqueda.
- Hace clic en "Buscar".
- Extrae resultados.

---

### ✅ ¿Qué significa “emular comportamiento humano”?

Los **bots** tradicionales son _rápidos, predecibles y fáciles de detectar_.

**Emular humano** significa:

✔️ Movimientos de mouse.

✔️ Pausas aleatorias.

✔️ Scroll en la página.

✔️ Escritura "lenta" como una persona.

✔️ Interacción real con botones o formularios.

✅ Beneficio ➜ Evitar bloqueos / CAPTCHAs / detección.

---

✅ 🟢 Ejemplo de comparación:

| Bot normal                  | Bot "humano" con Selenium   |
| --------------------------- | --------------------------- |
| Envia solicitud en 0.1s     | Espera 1-3s antes de buscar |
| Lee HTML sin renderizar JS  | Renderiza la página real    |
| No mueve mouse              | Mueve mouse o scroll        |
| No llena formularios reales | Usa campos del formulario   |

---

### ✅ ¿Para qué sirve en hacking ético y OSINT?

✅ Automate reconnaissance:

- Buscar con Google, Bing, DuckDuckGo.
- Extraer datos de páginas que bloquean scrapers simples.

✅ Simular login:

- Probar contraseñas débiles (con permisos, ethical testing).
- Extraer información interna (bug bounty / OSINT).

✅ Analizar aplicaciones web:

- Ver rutas ocultas.
- Revisar contenido dinámico.

✅ Evitar detección anti-bot:

- Selenium puede comportarse como un usuario humano.

---

### ✅ ¿Cómo se instala Selenium?

**✅ Paso 1: Tener Python instalado**

Verificar:

```bash
python --version
```

---

**✅ Paso 2: Instalar Selenium**

```bash
pip install selenium
```

---

**✅ Paso 3: Descargar WebDriver**

⭐ Selenium necesita un **driver** que controle tu navegador.

✔️ Chrome ➜ [ChromeDriver](https://sites.google.com/chromium.org/driver/)

✔️ Firefox ➜ [GeckoDriver](https://github.com/mozilla/geckodriver/releases)

✔️ Edge ➜ [EdgeDriver](https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/)

✅ Debes:

- Descargar el driver correcto para tu navegador y versión.
- Colocar el ejecutable en una carpeta conocida (opcionalmente en PATH).

---

✅ **Para Chrome en Windows:**

- Baja `chromedriver.exe` ➜ guárdalo en `C:\webdriver\chromedriver.exe`.
- En Linux/Mac ➜ solo coloca el binario y dale permisos.

---

### ✅ Código básico en Python

**✔️ Abrir Google y buscar algo**

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time

# Ruta a tu ChromeDriver
PATH = "/ruta/a/chromedriver"  # Ejemplo: "C:/webdriver/chromedriver.exe"

driver = webdriver.Chrome(PATH)

driver.get("https://www.google.com")
time.sleep(2)  # Pausa para parecer humano

# Buscar la caja de texto
search_box = driver.find_element(By.NAME, "q")
search_box.send_keys("OpenAI")
time.sleep(1)  # Simula escribir pausado

search_box.send_keys(Keys.RETURN)  # Presiona Enter
time.sleep(3)

# Extraer resultados
results = driver.find_elements(By.CSS_SELECTOR, "h3")
for result in results:
    print(result.text)

driver.quit()
```

---

✅ ¿Qué hace?

✔️ Abre Chrome.

✔️ Va a Google.

✔️ Escribe "OpenAI".

✔️ Espera, carga resultados.

✔️ Imprime títulos de resultados.

---

### ✅ Emulando comportamiento humano

✅ Selenium es muy rápido por defecto.

➡️ Debes **hacerlo más humano**:

⭐ **a. Pausas aleatorias**

```python
import random

time.sleep(random.uniform(2, 5))
```

---

⭐ **b. Scroll en la página**

```python
driver.execute_script("window.scrollTo(0, document.body.scrollHeight);")
time.sleep(2)
```

---

⭐ **c. Mouse over / hover**

```python
from selenium.webdriver import ActionChains

element = driver.find_element(By.CSS_SELECTOR, "h3")
actions = ActionChains(driver)
actions.move_to_element(element).perform()
time.sleep(1)
```

---

⭐ **d. Escritura lenta**

```python
for char in "OpenAI":
    search_box.send_keys(char)
    time.sleep(random.uniform(0.1, 0.3))
```

---

✅ Resultado ➜ Parece más humano:

- No es instantáneo.
- Movimientos y pausas.
- Interacciones reales.

---

### ✅ Extra: Evitar detección anti-bot

Muchos sitios detectan **headless** o bots.
✔️ Solución:

✅ Usar perfil real de Chrome:

```python
from selenium.webdriver.chrome.options import Options

options = Options()
options.add_argument("user-data-dir=/ruta/a/tu/perfil")
driver = webdriver.Chrome(PATH, options=options)
```

---

✅ Desactivar automation flags:

```python
options.add_experimental_option("excludeSwitches", ["enable-automation"])
options.add_experimental_option('useAutomationExtension', False)
```

---

✅ Emular user-agent real:

```python
options.add_argument(
    "user-agent=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 ..."
)
```

---

✅ Usar undetected_chromedriver:

✔️ Librería que modifica Selenium para evitar detección:

```bash
pip install undetected-chromedriver
```

---

**Código ejemplo:**

```python
import undetected_chromedriver as uc

driver = uc.Chrome()
driver.get("https://www.google.com")
```

---

### ✅ Ejemplo más realista: Google Dork con pausa

✅ Buscar "site:.gov filetype\:pdf password"

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time, random

PATH = "/ruta/a/chromedriver"
driver = webdriver.Chrome(PATH)

driver.get("https://www.google.com")
time.sleep(random.uniform(2, 4))

search_box = driver.find_element(By.NAME, "q")

dork = 'site:.gov filetype:pdf password'
for char in dork:
    search_box.send_keys(char)
    time.sleep(random.uniform(0.1, 0.3))

search_box.send_keys(Keys.RETURN)
time.sleep(random.uniform(3, 6))

results = driver.find_elements(By.CSS_SELECTOR, "h3")
for result in results:
    print(result.text)

driver.quit()
```

---

✅ **Emula:**

✔️ Esperar cargue.

✔️ Escribir letra por letra.

✔️ Scroll / pausa.

✔️ Click real.

✅ ➜ Mucho más humano.

---

### ✅ Resumen de instalación

| Paso                               | Comando                                                       |
| ---------------------------------- | ------------------------------------------------------------- |
| Instalar selenium                  | `pip install selenium`                                        |
| (Opcional) undetected_chromedriver | `pip install undetected-chromedriver`                         |
| Descargar driver                   | [ChromeDriver](https://sites.google.com/chromium.org/driver/) |

---

✅ Archivo típico:

```
tu_script.py
chromedriver.exe (en ruta conocida)
```

---

✅ Estructura proyecto:

```
mi-bot/
  ├── bot.py
  ├── chromedriver.exe
  └── requirements.txt
```

---

✅ requirements.txt:

```
selenium
undetected-chromedriver
```

---

### ✅ Resumen práctico

⭐ Selenium ➜ automatiza navegador real.

⭐ Emular humano ➜ pausas, scroll, escritura lenta, hover.

⭐ Usos:

✔️ Scraping avanzado.

✔️ Login automation.

✔️ Evitar bloqueos anti-bot.

✔️ OSINT y recon.

---

✅ **Instalación mínima:**

```bash
pip install selenium
```

✅ **Driver:**

- Chrome ➜ [ChromeDriver](https://sites.google.com/chromium.org/driver/).

✅ **Código ejemplo mínimo:**

```python
from selenium import webdriver
driver = webdriver.Chrome("/ruta/a/chromedriver")
driver.get("https://www.google.com")
```

---

[🔼](#índice)

---

## **169. Hacking con buscadores automático con Selenium**

### ✅ ¿Qué es "Hacking con buscadores"?

✔️ También conocido como **Google Hacking / Dorking**.

✅ Consiste en usar operadores avanzados de búsqueda para encontrar información sensible o no intencionada públicamente expuesta.

✅ Ejemplos de **Google Dorks**:

- `inurl:admin`
- `filetype:pdf confidential`
- `site:.gov intext:password`
- `"index of /" +backup`

✅ Usos en hacking ético / OSINT:

- Encontrar paneles de administración.
- Localizar documentos sensibles.
- Ver bases de datos expuestas.

---

### ✅ ¿Por qué hacerlo **automático**?

✅ Hacer búsquedas manuales ➜ lento y limitado.

✅ Automatizar con Selenium ➜ ventajas:

✔️ Ejecutar docenas o cientos de dorks.

✔️ Simular navegador humano.

✔️ Evitar algunos bloqueos básicos anti-bot.

✔️ Extraer resultados en masa.

✔️ Filtrar y guardar resultados.

---

### ✅ ¿Qué es **Selenium**?

⭐ Selenium es una librería de Python (y otros lenguajes) para **automatizar navegadores reales** (Chrome, Firefox, Edge...).

✔️ Abre el navegador.

✔️ Escribe en formularios.

✔️ Hace clics.

✔️ Lee contenido dinámico (JavaScript).

✅ Simula un **usuario real**.

---

✅ Muy útil para **hacking ético / scraping avanzado**:

✔️ Evitar bloqueos por user-agent.

✔️ Renderizar contenido generado por JS.

✔️ Emular interacciones humanas.

---

### ✅ Instalación paso a paso

#### ✅ A. Tener Python instalado

Verifica con:

```bash
python --version
```

---

#### ✅ B. Crear entorno virtual (opcional, recomendado)

```bash
python -m venv venv
```

Activar:

- Windows:

```bash
venv\Scripts\activate
```

- macOS/Linux:

```bash
source venv/bin/activate
```

---

#### ✅ C. Instalar Selenium

```bash
pip install selenium
```

---

#### ✅ D. Descargar WebDriver

✔️ Para **Chrome**: [ChromeDriver](https://sites.google.com/chromium.org/driver/)

✔️ Para **Firefox**: [GeckoDriver](https://github.com/mozilla/geckodriver/releases)

✅ Debe ser **compatible con tu versión de navegador**.

---

✅ Ejemplo:

- Windows ➜ `chromedriver.exe` en `C:\webdriver\chromedriver.exe`
- Linux/Mac ➜ en `/usr/local/bin/chromedriver`

---

### ✅ Código mínimo: abrir Google

**Archivo:** `bot_basico.py`

```python
from selenium import webdriver

driver = webdriver.Chrome("/ruta/a/chromedriver")
driver.get("https://www.google.com")
```

✔️ Se abre Google en Chrome.

---

### ✅ Automatizando búsqueda (hacking con buscadores)

✅ Objetivo:

✔️ Abrir Google.

✔️ Escribir un **dork**.

✔️ Obtener resultados.

✔️ Imprimir títulos.

---

**✔️ Ejemplo sencillo**

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time

PATH = "/ruta/a/chromedriver"
driver = webdriver.Chrome(PATH)

# Abrir Google
driver.get("https://www.google.com")
time.sleep(2)

# Buscar con dork
search_box = driver.find_element(By.NAME, "q")
dork = 'site:.gov filetype:pdf password'
search_box.send_keys(dork)
search_box.send_keys(Keys.RETURN)
time.sleep(3)

# Extraer resultados
results = driver.find_elements(By.CSS_SELECTOR, "h3")
for result in results:
    print(result.text)

driver.quit()
```

✅ Salida (ejemplo):

```
Confidential PDF Document - gov
Password Policy.pdf - .gov site
...
```

---

### ✅ Ejecutar múltiples dorks automáticamente

✅ Normalmente quieres **probar varios dorks**:

```
dorks.txt:
site:.gov filetype:pdf password
inurl:admin
intitle:"index of" backup
```

---

✅ Código ejemplo: **leer archivo y buscar todos**

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time, random

# Config
PATH = "/ruta/a/chromedriver"
driver = webdriver.Chrome(PATH)

with open("dorks.txt", "r", encoding="utf-8") as file:
    dorks = [line.strip() for line in file if line.strip()]

for dork in dorks:
    print(f"\n🔎 Buscando: {dork}\n")
    driver.get("https://www.google.com")
    time.sleep(random.uniform(2, 4))

    search_box = driver.find_element(By.NAME, "q")
    for char in dork:
        search_box.send_keys(char)
        time.sleep(random.uniform(0.1, 0.3))  # Emula tipeo humano
    search_box.send_keys(Keys.RETURN)
    time.sleep(random.uniform(3, 6))

    results = driver.find_elements(By.CSS_SELECTOR, "h3")
    for result in results:
        print(result.text)

driver.quit()
```

---

✅ Explicación paso a paso:

✔️ Abre Google.

✔️ Toma **dork 1** del archivo.

✔️ Escribe letra por letra (emula humano).

✔️ Espera.

✔️ Obtiene resultados.

✔️ Repite con **dork 2**, **dork 3**...

---

### ✅ Emulando **comportamiento humano**

✅ Muy importante para evitar detección anti-bot.

✅ Técnicas:

✔️ Pausas aleatorias:

```python
time.sleep(random.uniform(2, 5))
```

✔️ Escritura lenta:

```python
for char in dork:
    search_box.send_keys(char)
    time.sleep(random.uniform(0.1, 0.3))
```

✔️ Scroll:

```python
driver.execute_script("window.scrollTo(0, document.body.scrollHeight);")
```

✔️ Hover sobre elementos:

```python
from selenium.webdriver import ActionChains
actions = ActionChains(driver)
actions.move_to_element(result).perform()
```

---

✅ Resultado:

✔️ Más lento, pero más "humano".

✔️ Menos probable ser bloqueado por Google.

---

### ✅ Guardar resultados en archivo

✅ Agregar al script:

```python
with open("resultados.txt", "a", encoding="utf-8") as f:
    for result in results:
        f.write(f"{dork} => {result.text}\n")
```

✔️ Cada búsqueda se guarda en un archivo.

---

### ✅ Evitar bloqueos (opcional avanzado)

✅ Google puede detectar Selenium:

✔️ Usar **undetected_chromedriver**:

```bash
pip install undetected-chromedriver
```

✅ Código:

```python
import undetected_chromedriver as uc

driver = uc.Chrome()
```

✅ Funciona casi igual, pero evita detección **automation flags**.

---

✅ User-Agent personalizado:

```python
from selenium.webdriver.chrome.options import Options

options = Options()
options.add_argument(
    "user-agent=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36..."
)
driver = webdriver.Chrome(PATH, options=options)
```

---

✅ Usar perfiles reales:

```python
options.add_argument("user-data-dir=/ruta/a/tu/perfil")
```

---

### ✅ Resumen súper corto

✅ **Instalación**:

```bash
pip install selenium
```

✅ Descargar **ChromeDriver**.

✅ **Script básico**:

✔️ Abre Google.

✔️ Escribe dork.

✔️ Extrae resultados.

✅ **Script avanzado**:

✔️ Lee lista de dorks.

✔️ Emula escritura humana.

✔️ Pausas aleatorias.

✔️ Guarda resultados.

---

### ✅ Flujo típico para OSINT

1️⃣ Preparar archivo `dorks.txt` con tus queries.

2️⃣ Ejecutar script Selenium.

3️⃣ Emular pausas humanas.

4️⃣ Guardar resultados en archivo.

5️⃣ Filtrar con Regex o IA después.

---

### ✅ Estructura recomendada de proyecto

```
hacking-buscadores/
  ├── bot.py
  ├── dorks.txt
  ├── resultados.txt
  └── requirements.txt
```

✅ `requirements.txt`:

```
selenium
undetected-chromedriver
```

---

### ✅ ¿Quieres más avanzado?

⭐ Podemos agregar:

✔️ Scroll infinito (Google paginación).

✔️ Login automatizado.

✔️ Headless (navegador oculto).

✔️ Integración con GPT-4 para filtrar resultados.

✔️ Guardar en JSON o CSV.

✅ ¡Solo dime y te armo la guía paso a paso!

---

### 🚀 **Conclusión**

✅ Hacking con buscadores **automático con Selenium** =

✔️ Buscar cientos de dorks.

✔️ Extraer resultados como humano.

✔️ Evitar bloqueos básicos.

✔️ Guardar resultados para análisis.

✅ Selenium = herramienta clave para hacking ético, OSINT, scraping avanzado.

---

[🔼](#índice)

---

| **Inicio**         | **Siguiente 2**                                                           |
| ------------------ | ------------------------------------------------------------------------- |
| [🏠](../README.md) | [⏩](./4_2_Investigacion_de_fuentes_abiertas_OSINT_con_Python_Hacking.md) |
