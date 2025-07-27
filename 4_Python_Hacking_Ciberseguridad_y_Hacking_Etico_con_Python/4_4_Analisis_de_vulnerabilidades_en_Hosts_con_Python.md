| **Inicio**         | **atrás 3**                                                                    | **Siguiente 5**                                                                     |
| ------------------ | ------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./4_3_Escaneos_y_analisis_de_redes_con_Python_Hosts_Puertos_Servicios.md) | [⏩](./4_5_Python_Hacking_y_Explotacion_de_Vulnerabilidades_en_Hosts_con_Python.md) |

---

## **Índice**

| Temario                                                                                                                                           |
| ------------------------------------------------------------------------------------------------------------------------------------------------- |
| [204. BeautifulSoup: Procesamiento de páginas web con Python](#204-beautifulsoup-procesamiento-de-páginas-web-con-python)                         |
| [205. CVE, CVSS, CVE Details con Python](#205-cve-cvss-cve-details-con-python)                                                                    |
| [206. Escáner de vulnerabilidades con Python: Obtención de CVEs](#206-escáner-de-vulnerabilidades-con-python-obtención-de-cves)                   |
| [207. Escáner de vulnerabilidades con Python: Obtención de CVSS](#207-escáner-de-vulnerabilidades-con-python-obtención-de-cvss)                   |
| [208. Escáner de vulnerabilidades con Python: Presentación de resultados](#208-escáner-de-vulnerabilidades-con-python-presentación-de-resultados) |
| [209. Integración de análisis de red y detección de vulnerabilidades](#209-integración-de-análisis-de-red-y-detección-de-vulnerabilidades)        |
| [210. Instalación y configuración de Nessus](#210-instalación-y-configuración-de-nessus)                                                          |
| [211. Introducción a Nessus con Python](#211-introducción-a-nessus-con-python)                                                                    |
| [212. Nessus con Python: Creación de una sesión y consulta de políticas](#212-nessus-con-python-creación-de-una-sesión-y-consulta-de-políticas)   |
| [213. Nessus con Python: Creación de escaneos](#213-nessus-con-python-creación-de-escaneos)                                                       |
| [214. Nessus con Python: Descarga y procesamiento de resultados](#214-nessus-con-python-descarga-y-procesamiento-de-resultados)                   |
| [215. Procesa los resultados de Nessus con Python](#215-procesa-los-resultados-de-nessus-con-python)                                              |

---

# **Analisis de vulnerabilidades en Hosts con Python**

## **204. BeautifulSoup: Procesamiento de páginas web con Python**

### 🟣 ¿Qué es BeautifulSoup?

**BeautifulSoup** es una librería de Python para **parsear (analizar) HTML y XML**.

✅ En lenguaje sencillo:

✔️ Te ayuda a leer páginas web.

✔️ Te permite **extraer datos** de su contenido.

✔️ Puedes navegar entre etiquetas como si fueran objetos.

✅ Muy usado para:

✔️ Web scraping.

✔️ Automatizar descargas de datos.

✔️ Analizar estructuras HTML.

---

### 🟣 ¿Para qué sirve?

✅ Imagínate que tienes este HTML:

```html
<html>
  <head>
    <title>Mi Página</title>
  </head>
  <body>
    <h1>Hola Mundo</h1>
    <p>Bienvenido a mi página</p>
    <a href="https://example.com">Visítanos</a>
  </body>
</html>
```

✅ BeautifulSoup te permite hacer:

✔️ Sacar el **título**.

✔️ Leer el **texto**.

✔️ Obtener **enlaces**.

✔️ Modificar el contenido (si quieres).

---

### 🟣 Instalación de Python

✅ Ve a: [https://www.python.org/downloads/](https://www.python.org/downloads/)

✔️ Descárgalo.

✔️ Marca ✅ _Add Python to PATH_.

✅ Verifica:

```bash
python --version
```

✅ Resultado esperado:

```
Python 3.x.x
```

---

### 🟣 Instalación de BeautifulSoup

✅ BeautifulSoup está en PyPI.

✔️ Abre tu CMD o Terminal:

```bash
pip install beautifulsoup4
```

✅ Verifica instalación:

```bash
pip show beautifulsoup4
```

✅ Resultado esperado:

```
Name: beautifulsoup4
Version: ...
```

---

### 🟣 Instalación de un **parser**

BeautifulSoup necesita un **parser** para leer HTML.

✅ Opciones:

✅ 1. html.parser (viene con Python).

✅ 2. lxml (más rápido y potente).

---

✅ Instalar lxml:

```bash
pip install lxml
```

✅ Verificar:

```bash
pip show lxml
```

---

### 🟣 Primer ejemplo: Extraer el título de una página

✅ Paso 1: Código mínimo

```python
from bs4 import BeautifulSoup

html_doc = """
<html>
  <head><title>Mi Página</title></head>
  <body>
    <h1>Hola Mundo</h1>
  </body>
</html>
"""

soup = BeautifulSoup(html_doc, 'html.parser')
print(soup.title.text)
```

✅ Resultado:

```
Mi Página
```

---

✅ Explicación:

| Línea                                    | Qué hace                         |
| ---------------------------------------- | -------------------------------- |
| `BeautifulSoup(html_doc, 'html.parser')` | Crea el objeto Soup.             |
| `soup.title`                             | Encuentra la etiqueta `<title>`. |
| `.text`                                  | Extrae su texto.                 |

---

### 🟣 Ejemplo: Extraer todos los enlaces de una página

✅ HTML ficticio:

```python
html_doc = """
<html>
  <body>
    <a href="https://example.com">Example</a>
    <a href="https://test.com">Test</a>
  </body>
</html>
"""
```

✅ Código:

```python
from bs4 import BeautifulSoup

soup = BeautifulSoup(html_doc, 'html.parser')

for link in soup.find_all('a'):
    print(link['href'], '-', link.text)
```

✅ Resultado:

```
https://example.com - Example
https://test.com - Test
```

✅ Explicación:

| Línea           | Qué hace                             |
| --------------- | ------------------------------------ |
| `find_all('a')` | Encuentra todas las etiquetas `<a>`. |
| `link['href']`  | Obtiene el atributo href.            |
| `link.text`     | El texto entre las etiquetas.        |

---

### 🟣 Ejemplo con **requests**: descargar y procesar página real

✅ BeautifulSoup se usa junto a **requests** para descargar páginas.

---

✅ Instalación:

```bash
pip install requests
```

✅ Verificar:

```bash
pip show requests
```

---

✅ Código:

```python
import requests
from bs4 import BeautifulSoup

# Descargar página
url = 'https://example.com'
response = requests.get(url)

# Parsear HTML
soup = BeautifulSoup(response.text, 'html.parser')

# Obtener título
print("[+] Título:", soup.title.text)

# Obtener todos los enlaces
for link in soup.find_all('a'):
    print("[+] Enlace:", link.get('href'))
```

✅ Resultado esperado (depende del sitio):

```
[+] Título: Example Domain
[+] Enlace: https://www.iana.org/domains/example
```

---

✅ Explicación:

| Línea                | Qué hace                     |
| -------------------- | ---------------------------- |
| `requests.get(url)`  | Descarga el HTML.            |
| `response.text`      | Contenido de la página.      |
| `BeautifulSoup(...)` | Crea el objeto para parsear. |
| `soup.title.text`    | Título de la página.         |
| `soup.find_all('a')` | Encuentra todos los enlaces. |

---

### 🟣 Ejemplo más completo: Scrapear tabla HTML

✅ HTML de ejemplo:

```python
html_doc = """
<html>
  <body>
    <table>
      <tr><th>Nombre</th><th>Edad</th></tr>
      <tr><td>Ana</td><td>25</td></tr>
      <tr><td>Juan</td><td>30</td></tr>
    </table>
  </body>
</html>
"""
```

✅ Código:

```python
from bs4 import BeautifulSoup

soup = BeautifulSoup(html_doc, 'html.parser')

# Encontrar la tabla
tabla = soup.find('table')

# Filas
filas = tabla.find_all('tr')

for fila in filas:
    columnas = fila.find_all(['th', 'td'])
    datos = [col.text for col in columnas]
    print(datos)
```

✅ Resultado:

```
['Nombre', 'Edad']
['Ana', '25']
['Juan', '30']
```

✅ Explicación:

| Línea                            | Qué hace                    |
| -------------------------------- | --------------------------- |
| `find('table')`                  | Encuentra la primera tabla. |
| `find_all('tr')`                 | Todas las filas.            |
| `find_all(['th', 'td'])`         | Celdas en la fila.          |
| `[col.text for col in columnas]` | Extrae texto de celdas.     |

---

### 🟣 Resumen súper corto

✅ 1️⃣ Instalar Python.

✅ 2️⃣ Instalar librerías:

```
pip install beautifulsoup4 lxml requests
```

✅ 3️⃣ Código básico:

```python
from bs4 import BeautifulSoup
import requests

url = "https://example.com"
html = requests.get(url).text
soup = BeautifulSoup(html, 'html.parser')

print(soup.title.text)
```

✅ 4️⃣ Extraer lo que quieras:

- Títulos.
- Enlaces.
- Tablas.
- Imágenes.

---

### 🟣 Tips extra

✅ Usa lxml para parsear más rápido:

```python
soup = BeautifulSoup(html, 'lxml')
```

✅ Imprimir bonito:

```python
print(soup.prettify())
```

✅ Extraer texto limpio:

```python
print(soup.get_text())
```

✅ Buscar por clase:

```python
soup.find_all(class_='mi-clase')
```

---

### ✅ Resultado final

✅ Con BeautifulSoup puedes:

✔️ Descargar HTML (con requests).

✔️ Parsear el contenido.

✔️ Extraer datos estructurados.

✔️ Automatizar la recolección de información web.

---

### ✅ Instalación final resumida

✔️ Python:

```
python --version
```

✔️ BeautifulSoup:

```
pip install beautifulsoup4
```

✔️ Parser recomendado:

```
pip install lxml
```

✔️ requests para descargar páginas:

```
pip install requests
```

---

[🔼](#índice)

---

## **205. CVE, CVSS, CVE Details con Python**

### ✅ ¿Qué es un CVE?

**CVE** ➜ _Common Vulnerabilities and Exposures_

✔️ Es un identificador único para una vulnerabilidad conocida.

✔️ Ejemplo: `CVE-2023-12345`.

✔️ Gestionado por MITRE.

✅ Cada CVE describe **un fallo de seguridad**.

✅ Usado por investigadores, fabricantes y equipos de seguridad.

---

✅ Ejemplo:

```
CVE-2023-12345
Descripción: Buffer overflow en X versión Y permite ejecución remota de código.
```

---

### ✅ ¿Qué es **CVSS**?

**CVSS** ➜ _Common Vulnerability Scoring System_

✔️ Es un sistema para **calificar la gravedad** de una vulnerabilidad.

✔️ Puntaje de **0.0 a 10.0**.

✅ Ejemplo:

| Score    | Nivel de severidad |
| -------- | ------------------ |
| 0.0      | Ninguna            |
| 0.1-3.9  | Baja               |
| 4.0-6.9  | Media              |
| 7.0-8.9  | Alta               |
| 9.0-10.0 | Crítica            |

✔️ Permite priorizar parches y mitigaciones.

---

✅ Ejemplo práctico:

```
CVE-2023-12345 ➜ CVSS 9.8 (Crítica)
```

---

### ✅ ¿Qué es **CVE Details**?

**CVE Details** ➜ un sitio web que **recolecta y organiza datos de CVE**.

✅ Puedes buscar:

✔️ CVEs por producto.

✔️ CVEs por año.

✔️ Detalles y métricas CVSS.

✅ Es una fuente **muy usada** para investigar vulnerabilidades.

✅ Web ➜ [https://www.cvedetails.com](https://www.cvedetails.com)

---

### ✅ ¿Por qué usarlos en seguridad?

✔️ Inventario de vulnerabilidades conocidas.

✔️ Saber **qué parchar primero**.

✔️ Evaluar el riesgo real.

✔️ Cumplimiento normativo (ISO, NIST).

✅ **En pentesting o blue team**:

➜ Escaneas sistemas, ves sus versiones, y buscas CVEs asociados.

➜ Priorizas con CVSS.

---

### ✅ Instalación de Python y librerías

---

✅ **Paso 1: Verificar Python**

```bash
python --version
```

✔️ Resultado esperado:

```
Python 3.x.x
```

✅ Si no lo tienes:

- Descarga en ➜ [https://www.python.org/downloads/](https://www.python.org/downloads/)
- Marca ✅ _Add Python to PATH_.

---

✅ **Paso 2: Instalar librerías necesarias**

Abrir terminal / CMD:

```bash
pip install requests pandas
```

✅ ¿Qué son?

| Librería | Para qué sirve                     |
| -------- | ---------------------------------- |
| requests | Descargar datos de Internet (API). |
| pandas   | Manejar datos en forma de tabla.   |

---

### ✅ Cómo obtener datos de CVE en Python

✅ Muchas fuentes:

✔️ NVD (National Vulnerability Database).

✔️ CVE Details (no tiene API oficial).

✔️ Apis públicas de seguridad.

✅ Ejemplo ➜ **NVD API gratuita**.

Documentación oficial:

- [https://nvd.nist.gov/developers/vulnerabilities](https://nvd.nist.gov/developers/vulnerabilities)

---

✅ Endpoint (para usar en requests):

```
https://services.nvd.nist.gov/rest/json/cves/2.0
```

✅ Puedes filtrar por:

- palabras clave.
- rango de fechas.
- CVE específico.

---

### ✅ Ejemplo mínimo: obtener datos de CVE

✅ Código paso a paso:

```python
import requests

# Endpoint básico de NVD (puedes añadir parámetros)
url = 'https://services.nvd.nist.gov/rest/json/cves/2.0'
params = {'keywordSearch': 'Apache'}

# Hacer la petición
response = requests.get(url, params=params)

# Verificar resultado
print(response.status_code)
print(response.json())
```

✅ Resultado esperado:

```
200
{...JSON con lista de CVEs...}
```

---

✅ Explicación:

| Línea             | Qué hace                            |
| ----------------- | ----------------------------------- |
| `params`          | Filtro de búsqueda (palabra clave). |
| `requests.get`    | Hace la petición HTTP.              |
| `response.json()` | Devuelve los datos en formato JSON. |

---

### ✅ Procesar los resultados (JSON ➜ tabla)

✅ Extraer datos útiles:

- CVE ID.
- Descripción.
- Puntaje CVSS.

✅ Código:

```python
import pandas as pd

# Obtener JSON
data = response.json()

# Acceder a la lista de vulnerabilidades
vulns = data.get('vulnerabilities', [])

# Procesar
cves_list = []
for v in vulns:
    cve_data = v['cve']
    cve_id = cve_data.get('id')
    desc = cve_data['descriptions'][0]['value']
    cvss = None

    # Intentar sacar el score CVSS v3
    metrics = cve_data.get('metrics', {})
    if 'cvssMetricV31' in metrics:
        cvss = metrics['cvssMetricV31'][0]['cvssData']['baseScore']
    elif 'cvssMetricV30' in metrics:
        cvss = metrics['cvssMetricV30'][0]['cvssData']['baseScore']

    cves_list.append({
        'CVE_ID': cve_id,
        'Descripción': desc,
        'CVSS': cvss
    })

# Convertir en DataFrame
df = pd.DataFrame(cves_list)
print(df.head())
```

✅ Resultado esperado:

```
    CVE_ID                     Descripción                      CVSS
0  CVE-2023-XXXXX  Buffer overflow in Apache module allows...   9.8
1  CVE-2022-YYYYY  Apache vulnerable to directory traversal...  5.3
...
```

---

✅ Explicación:

| Línea                         | Qué hace                |
| ----------------------------- | ----------------------- |
| `data.get('vulnerabilities')` | Lista de resultados.    |
| `for v in vulns`              | Recorre cada CVE.       |
| `cve_data.get('id')`          | Obtiene el CVE ID.      |
| `desc`                        | Obtiene la descripción. |
| `cvss`                        | Puntaje de gravedad.    |
| `pd.DataFrame`                | Lo convierte en tabla.  |

---

### ✅ Guardar resultados en CSV

✅ Muy útil para reportes:

```python
df.to_csv('cves_apache.csv', index=False)
print("Archivo CSV guardado correctamente.")
```

✅ Resultado:

✔️ Un archivo **cves_apache.csv** con columnas:

```
CVE_ID,Descripción,CVSS
```

---

### ✅ Ejemplo de uso real: priorización de parches

✅ Puedes filtrar solo vulnerabilidades críticas:

```python
criticas = df[df['CVSS'] >= 9]
print(criticas)
```

✅ Resultado:

```
       CVE_ID                      Descripción                   CVSS
0  CVE-2023-XXXXX          Buffer overflow en Apache...           9.8
```

✅ Explicación:

✔️ Usas el score CVSS para priorizar **qué parchar primero**.

---

### ✅ Resumen ultra corto

✅ CVE ➜ ID único de vulnerabilidad.

✅ CVSS ➜ Puntaje de gravedad (0.0 a 10.0).

✅ CVE Details ➜ sitio para explorar CVEs.

✅ NVD ➜ fuente oficial con API gratuita.

✅ Python:

1️⃣ Instalar:

```
pip install requests pandas
```

2️⃣ Obtener datos:

```python
response = requests.get(url, params)
```

3️⃣ Procesar JSON:

```python
data = response.json()
```

4️⃣ Analizar y filtrar:

```python
df[df['CVSS'] >= 9]
```

5️⃣ Guardar:

```python
df.to_csv('resultados.csv')
```

---

### ✅ Variaciones más avanzadas

✅ Filtrar por año:

```python
params = {
    'pubStartDate': '2023-01-01T00:00:00:000 UTC-00:00',
    'pubEndDate': '2023-12-31T23:59:59:999 UTC-00:00'
}
```

✅ Buscar por producto:

```python
params = {'keywordSearch': 'Apache Struts'}
```

✅ Analizar CVSS v2 y v3:

```python
metrics.get('cvssMetricV2', [{}])[0].get('cvssData', {}).get('baseScore')
```

---

✅ ¡Y puedes combinar con Machine Learning para predecir riesgos personalizados!

---

### ✅ Resultado final

✔️ En Python puedes:

✅ Buscar CVEs en NVD.

✅ Extraer ID, descripción, CVSS.

✅ Filtrar y priorizar por gravedad.

✅ Exportar resultados.

---

[🔼](#índice)

---

## **206. Escáner de vulnerabilidades con Python: Obtención de CVEs**

### ✅ ¿Qué es un “escáner de vulnerabilidades” (concepto sencillo)?

- Es un **programa o script** que analiza sistemas o software, y **detecta vulnerabilidades conocidas**.
- Por ejemplo, si tienes un servidor con **Apache 2.4.49**, el escáner busca si existen **CVE** publicados para esa versión.

✅ En ciberseguridad se usa para:

✔️ Saber qué parches aplicar.

✔️ Reducir el riesgo.

✔️ Hacer auditorías.

---

### ✅ ¿Qué es un CVE?

- **CVE = Common Vulnerabilities and Exposures.**
- Es un **ID único** para una vulnerabilidad conocida.
- Ejemplo: `CVE-2021-41773`

✅ Cada CVE tiene:

✔️ ID.

✔️ Descripción.

✔️ Score de gravedad (**CVSS**).

---

✅ Ejemplo real:

```
CVE-2021-41773
Apache 2.4.49 tiene un path traversal que permite acceso no autorizado a archivos del sistema.
CVSS: 7.5
```

---

### ✅ Idea general de nuestro **escáner en Python**

✔️ **Entrada**: Software/servicio/versión (ej: "Apache 2.4.49").

✔️ **Búsqueda**: Consultar base de datos o API de vulnerabilidades.

✔️ **Salida**: Listar CVEs relacionados, con sus descripciones y CVSS.

✅ Resultado esperado:

```
Servicio: Apache 2.4.49
- CVE-2021-41773 (CVSS 7.5): Path traversal vulnerability...
- CVE-2021-42013 (CVSS 9.8): Remote code execution...
```

---

✅ Nosotros vamos a hacerlo usando **la API de NVD** (National Vulnerability Database), que es _gratuita y oficial_.

---

### ✅ Preparación del entorno

---

#### 🟣 Instalar Python

✔️ Ve a ➜ [https://www.python.org/downloads/](https://www.python.org/downloads/)

✔️ Descarga y marca ✅ _Add Python to PATH_.

✔️ Verifica en terminal/cmd:

```
python --version
```

✅ Resultado esperado:

```
Python 3.x.x
```

---

#### 🟣 Instalar librerías necesarias

✔️ Abrir CMD o Terminal:

```
pip install requests pandas
```

✅ ¿Para qué sirven?

| Librería   | Uso                                   |
| ---------- | ------------------------------------- |
| `requests` | Descargar datos de internet.          |
| `pandas`   | Manejar resultados en forma de tabla. |

---

✅ Verificar:

```
pip show requests
pip show pandas
```

✅ Resultado esperado:

```
Name: requests
Version: ...
```

---

### ✅ Entendiendo la **fuente de datos**

✅ Usaremos la **API REST de NVD (nist.gov)**.

- Documentación oficial ➜ [https://nvd.nist.gov/developers/vulnerabilities](https://nvd.nist.gov/developers/vulnerabilities)
- Endpoint ➜

```
https://services.nvd.nist.gov/rest/json/cves/2.0
```

✅ Puedes filtrar por:

✔️ palabra clave (ej: "Apache 2.4.49").

✔️ fechas.

✔️ severidad.

---

✅ Resultado ➜ JSON con:

✔️ Lista de vulnerabilidades.

✔️ CVE ID.

✔️ Descripción.

✔️ CVSS.

---

### ✅ Esqueleto del escáner en Python

✅ Vamos a construirlo paso a paso:

---

#### ✅ Paso 1: Importar librerías

```python
import requests
import pandas as pd
```

---

#### ✅ Paso 2: Definir función de búsqueda de CVEs

✅ Vamos a usar _keywordSearch_ para buscar CVEs por nombre de producto/versión.

```python
def buscar_cves(software):
    url = 'https://services.nvd.nist.gov/rest/json/cves/2.0'
    params = {
        'keywordSearch': software,
        'resultsPerPage': 20  # Puedes ajustar
    }

    print(f"[*] Buscando CVEs para: {software}")
    response = requests.get(url, params=params)

    if response.status_code != 200:
        print("[!] Error al consultar la API:", response.status_code)
        return []

    data = response.json()
    resultados = data.get('vulnerabilities', [])
    return resultados
```

✅ Explicación:

| Línea             | Qué hace                                     |
| ----------------- | -------------------------------------------- |
| `keywordSearch`   | Filtra por el término (ej: "Apache 2.4.49"). |
| `resultsPerPage`  | Número de resultados por página.             |
| `requests.get`    | Hace la petición HTTP.                       |
| `response.json()` | Devuelve datos en JSON.                      |

---

#### ✅ Paso 3: Procesar resultados

✔️ Extraemos ID, descripción y CVSS.

```python
def procesar_cves(lista_cves):
    cves_data = []

    for item in lista_cves:
        cve_info = item['cve']
        cve_id = cve_info.get('id')
        desc = cve_info['descriptions'][0]['value']
        cvss = None

        # Intentar obtener CVSS v3
        metrics = cve_info.get('metrics', {})
        if 'cvssMetricV31' in metrics:
            cvss = metrics['cvssMetricV31'][0]['cvssData']['baseScore']
        elif 'cvssMetricV30' in metrics:
            cvss = metrics['cvssMetricV30'][0]['cvssData']['baseScore']

        cves_data.append({
            'CVE_ID': cve_id,
            'Descripción': desc,
            'CVSS': cvss
        })

    return pd.DataFrame(cves_data)
```

✅ Explicación:

✔️ Itera cada resultado.

✔️ Extrae ID y descripción.

✔️ Lee CVSS si existe.

✔️ Devuelve un DataFrame de pandas.

---

#### ✅ Paso 4: Integrar todo en un flujo

✅ Código para usar las funciones:

```python
if __name__ == "__main__":
    software = input("Ingresa el software/versión a buscar: ")

    resultados_brutos = buscar_cves(software)
    df_cves = procesar_cves(resultados_brutos)

    if df_cves.empty:
        print("[!] No se encontraron CVEs.")
    else:
        print("\n[+] Resultados encontrados:")
        print(df_cves)

        # Opcional: Guardar en CSV
        df_cves.to_csv(f'cves_{software.replace(" ", "_")}.csv', index=False)
        print(f"[+] Resultados guardados en cves_{software.replace(' ', '_')}.csv")
```

✅ Explicación:

| Línea           | Qué hace                               |
| --------------- | -------------------------------------- |
| `input()`       | Pide al usuario el software o versión. |
| `buscar_cves`   | Descarga CVEs desde NVD.               |
| `procesar_cves` | Limpia y organiza resultados.          |
| `to_csv`        | Guarda en archivo CSV.                 |

---

### ✅ Resultado esperado

✅ Al ejecutar:

```
python escaner_cves.py
```

✅ Ejemplo:

```
Ingresa el software/versión a buscar: Apache 2.4.49

[*] Buscando CVEs para: Apache 2.4.49

[+] Resultados encontrados:
     CVE_ID                       Descripción                             CVSS
0  CVE-2021-41773    Path traversal en Apache 2.4.49 permite acceso...    7.5
1  CVE-2021-42013    Remote Code Execution en Apache 2.4.49 y 2.4.50      9.8

[+] Resultados guardados en cves_Apache_2.4.49.csv
```

---

### ✅ Archivos CSV generados

✔️ Contienen:

```
CVE_ID,Descripción,CVSS
CVE-2021-41773,"Path traversal...",7.5
CVE-2021-42013,"Remote Code Execution...",9.8
```

✔️ Útil para reportes o auditorías.

---

### ✅ Extra: Filtrar por criticidad

✅ Puedes filtrar el DataFrame:

```python
criticos = df_cves[df_cves['CVSS'] >= 9]
print("[+] Vulnerabilidades críticas encontradas:")
print(criticos)
```

✅ Resultado:

```
[+] Vulnerabilidades críticas encontradas:
    CVE_ID                 Descripción           CVSS
1  CVE-2021-42013     Remote Code Execution...   9.8
```

---

### ✅ Resumen ultra corto

✅ 1️⃣ Instalar:

```
pip install requests pandas
```

✅ 2️⃣ Descargar datos de NVD con:

```python
requests.get(url, params)
```

✅ 3️⃣ Procesar JSON ➜ extraer ID, descripción, CVSS.

✅ 4️⃣ Mostrar en tabla (pandas).

✅ 5️⃣ Guardar en CSV.

✅ 6️⃣ Filtrar por severidad.

---

### ✅ Resultado final

Con este script:

✔️ El usuario escribe: “Apache 2.4.49”.

✔️ El script consulta NVD.

✔️ Descarga CVEs relacionados.

✔️ Extrae su descripción y CVSS.

✔️ Imprime resultados.

✔️ Guarda CSV para reportes.

---

### ✅ ¿Cómo instalar todo junto?

✅ **Instalación completa en Windows/Linux/macOS:**

```
pip install requests pandas
```

✅ Código completo ➜ solo guarda el script como `escaner_cves.py`.

✅ Ejecuta:

```
python escaner_cves.py
```

✅ ¡Listo!

---

### ✅ Variaciones avanzadas (opcional)

✅ Filtrar por fechas:

```python
params['pubStartDate'] = '2023-01-01T00:00:00:000 UTC-00:00'
```

✅ Analizar CVSS v2 además de v3.

✅ Leer lista de softwares desde archivo.

✅ Crear un dashboard con Streamlit.

---

[🔼](#índice)

---

## **207. Escáner de vulnerabilidades con Python: Obtención de CVSS**

### ✅ ¿Qué es CVSS?

**CVSS = Common Vulnerability Scoring System**

✔️ Es un sistema estándar para **calificar la severidad** de una vulnerabilidad.

✔️ Puntaje de **0.0 a 10.0**.

✅ Tabla de severidad:

| Score    | Nivel   |
| -------- | ------- |
| 0.0      | Ninguna |
| 0.1–3.9  | Baja    |
| 4.0–6.9  | Media   |
| 7.0–8.9  | Alta    |
| 9.0–10.0 | Crítica |

✅ Ejemplo:

```
CVE-2021-34527
CVSS: 9.8 (Crítica)
```

✔️ Sirve para **priorizar parches**.

---

### ✅ ¿De dónde se obtiene el CVSS?

✅ Fuentes públicas:

⭐ [NVD (National Vulnerability Database)](https://nvd.nist.gov)

⭐ [CVE Details](https://www.cvedetails.com)

✅ NVD tiene **API oficial gratuita** que devuelve:

✔️ CVE ID

✔️ Descripción

✔️ CVSS v2 / v3

✅ Ejemplo de respuesta JSON:

```json
{
  "cve": {
    "id": "CVE-2021-41773",
    "descriptions": [
      { "lang": "en", "value": "A path traversal vulnerability in Apache..." }
    ],
    "metrics": {
      "cvssMetricV31": [{ "cvssData": { "baseScore": 7.5 } }]
    }
  }
}
```

---

✅ En resumen:

✔️ Tu script buscará **CVE** relacionados con un software.

✔️ Extraerá su **CVSS** del JSON.

✔️ Lo mostrará o guardará.

---

### ✅ Instalación de Python

✅ Ve a ➜ [https://www.python.org/downloads/](https://www.python.org/downloads/)

✔️ Descarga y **marca ✅ Add Python to PATH**.

✔️ Verifica:

```bash
python --version
```

✅ Resultado esperado:

```
Python 3.x.x
```

---

### ✅ Instalación de librerías en Python

✔️ Abre CMD o Terminal:

```bash
pip install requests pandas
```

✅ ¿Para qué sirven?

| Librería | Uso                                      |
| -------- | ---------------------------------------- |
| requests | Descargar datos desde la web (API).      |
| pandas   | Organizar datos como tablas (DataFrame). |

---

✅ Verificar:

```bash
pip show requests
pip show pandas
```

---

### ✅ ¿Cómo funciona la **API de NVD**?

✔️ URL base:

```
https://services.nvd.nist.gov/rest/json/cves/2.0
```

✔️ Puedes usar filtros:

- **keywordSearch** ➜ texto libre (ej: "Apache 2.4.49")
- **pubStartDate**, **pubEndDate** ➜ rango de fechas

✅ Ejemplo de request:

```
GET https://services.nvd.nist.gov/rest/json/cves/2.0?keywordSearch=Apache
```

---

### ✅ Idea del script en Python

✅ Entrada ➜ Nombre del software (o versión)

✅ Paso 1 ➜ Consultar API de NVD

✅ Paso 2 ➜ Extraer CVEs

✅ Paso 3 ➜ Obtener su CVSS

✅ Salida ➜ Imprimir o guardar tabla

---

### ✅ Vamos paso por paso en el código

---

#### ✅ Paso 1: Importar librerías

```python
import requests
import pandas as pd
```

✅ Explicación:

| Línea           | Qué hace                      |
| --------------- | ----------------------------- |
| import requests | Permite hacer peticiones HTTP |
| import pandas   | Manejar datos tabulares       |

---

#### ✅ Paso 2: Función para consultar la API

```python
def buscar_cves(software):
    url = 'https://services.nvd.nist.gov/rest/json/cves/2.0'
    params = {
        'keywordSearch': software,
        'resultsPerPage': 20
    }

    print(f"[*] Buscando CVEs para: {software}")
    response = requests.get(url, params=params)

    if response.status_code != 200:
        print("[!] Error al consultar la API:", response.status_code)
        return []

    data = response.json()
    resultados = data.get('vulnerabilities', [])
    return resultados
```

✅ Explicación línea por línea:

- **url** ➜ endpoint de la NVD API.
- **params** ➜ filtros de búsqueda.
- **requests.get** ➜ hace la petición HTTP.
- **response.json()** ➜ convierte la respuesta a JSON.
- **data.get('vulnerabilities')** ➜ extrae la lista de CVEs.

---

✅ Resultado ➜ lista de CVEs en JSON.

---

#### ✅ Paso 3: Extraer datos útiles (incluye CVSS)

```python
def procesar_cves(lista_cves):
    cves_data = []

    for item in lista_cves:
        cve_info = item['cve']
        cve_id = cve_info.get('id')
        desc = cve_info['descriptions'][0]['value']
        cvss = None

        metrics = cve_info.get('metrics', {})
        if 'cvssMetricV31' in metrics:
            cvss = metrics['cvssMetricV31'][0]['cvssData']['baseScore']
        elif 'cvssMetricV30' in metrics:
            cvss = metrics['cvssMetricV30'][0]['cvssData']['baseScore']
        elif 'cvssMetricV2' in metrics:
            cvss = metrics['cvssMetricV2'][0]['cvssData']['baseScore']

        cves_data.append({
            'CVE_ID': cve_id,
            'Descripción': desc,
            'CVSS': cvss
        })

    return pd.DataFrame(cves_data)
```

✅ Explicación línea por línea:

| Línea                  | Qué hace                     |
| ---------------------- | ---------------------------- |
| for item in lista_cves | Recorre cada vulnerabilidad. |
| cve_info\['id']        | Obtiene el ID (CVE-XXXX).    |
| desc                   | Extrae descripción.          |
| metrics                | Contiene datos de CVSS.      |
| cvssMetricV31/V30/V2   | Intenta obtener baseScore.   |
| cves_data.append       | Guarda en lista.             |
| pd.DataFrame           | Convierte a tabla.           |

✅ Resultado ➜ **DataFrame** con columnas:

- CVE_ID
- Descripción
- CVSS

---

#### ✅ Paso 4: Programa principal

```python
if __name__ == "__main__":
    software = input("Ingresa el software/versión a buscar: ")

    resultados_brutos = buscar_cves(software)
    df_cves = procesar_cves(resultados_brutos)

    if df_cves.empty:
        print("[!] No se encontraron CVEs.")
    else:
        print("\n[+] Resultados encontrados:")
        print(df_cves)

        # Guardar en CSV
        df_cves.to_csv(f'cves_{software.replace(" ", "_")}.csv', index=False)
        print(f"[+] Resultados guardados en cves_{software.replace(' ', '_')}.csv")
```

✅ Explicación:

✔️ **input()** ➜ pide el software al usuario.

✔️ **buscar_cves()** ➜ consulta la API.

✔️ **procesar_cves()** ➜ procesa JSON.

✔️ **print()** ➜ muestra resultados.

✔️ **to_csv()** ➜ guarda tabla en archivo CSV.

---

### ✅ Resultado esperado

✅ Al ejecutar:

```
python escaner_cvss.py
```

✅ Ejemplo:

```
Ingresa el software/versión a buscar: Apache 2.4.49

[*] Buscando CVEs para: Apache 2.4.49

[+] Resultados encontrados:
     CVE_ID                          Descripción                          CVSS
0  CVE-2021-41773    Path traversal en Apache 2.4.49 permite acceso...    7.5
1  CVE-2021-42013    Remote Code Execution en Apache 2.4.49 y 2.4.50      9.8

[+] Resultados guardados en cves_Apache_2.4.49.csv
```

---

✅ Archivo CSV generado:

```
CVE_ID,Descripción,CVSS
CVE-2021-41773,"Path traversal...",7.5
CVE-2021-42013,"Remote Code Execution...",9.8
```

---

### ✅ Filtrar por criticidad (opcional)

✅ Si quieres **solo críticos**:

```python
criticos = df_cves[df_cves['CVSS'] >= 9]
print("\n[+] Vulnerabilidades críticas encontradas:")
print(criticos)
```

✅ Resultado:

```
[+] Vulnerabilidades críticas encontradas:
      CVE_ID               Descripción              CVSS
1  CVE-2021-42013        Remote Code Execution...   9.8
```

---

### ✅ Guardar resultados en Excel (opcional)

✅ En vez de CSV:

```python
df_cves.to_excel(f'cves_{software.replace(" ", "_")}.xlsx', index=False)
```

---

### ✅ Resumen ultra corto

✅ 1️⃣ Instalar dependencias:

```
pip install requests pandas
```

✅ 2️⃣ Buscar CVEs con:

```python
requests.get(url, params)
```

✅ 3️⃣ Extraer:

- ID
- Descripción
- CVSS

✅ 4️⃣ Mostrar en tabla (pandas) y guardar CSV o Excel.

---

### ✅ Resultado final: Un escáner básico de CVEs y CVSS en Python

✔️ Entrada ➜ Nombre de software.

✔️ Salida ➜ Lista de CVEs con su puntaje de severidad (CVSS).

✔️ Útil para:

- Auditorías.
- Pentesting.
- Gestión de parches.

---

[🔼](#índice)

---

## **208. Escáner de vulnerabilidades con Python: Presentación de resultados**

### ✅ Introducción: ¿Qué queremos lograr?

Un **escáner de vulnerabilidades** suele:

✅ Buscar vulnerabilidades (CVEs) para un software o servicio.

✅ Obtener datos como:

- CVE ID
- Descripción
- CVSS (puntuación de severidad)

✅ Presentar resultados de forma:

- Legible en consola.
- Guardable en CSV o Excel.
- Filtrable (por criticidad).

---

✔️ El problema más común ➜ "Tengo un montón de resultados en JSON poco legible".

✅ Solución ➜ convertir eso en tablas limpias, archivos CSV o Excel, o gráficos.

---

### ✅ Requisitos previos

#### 🟣 Tener Python instalado

```bash
python --version
```

✅ Si no, descargar en ➜ [https://www.python.org/downloads/](https://www.python.org/downloads/)

---

#### 🟣 Instalar librerías

Abrir CMD / Terminal:

```bash
pip install requests pandas tabulate openpyxl
```

✅ ¿Para qué sirven?

| Librería | Uso                                 |
| -------- | ----------------------------------- |
| requests | Obtener datos de la web (API).      |
| pandas   | Manejar datos en tablas.            |
| tabulate | Imprimir tablas bonitas en consola. |
| openpyxl | Escribir en archivos Excel.         |

---

### ✅ Flujo de trabajo del escáner

✅ Entrada ➜ Software o versión a analizar.

✅ Paso 1 ➜ Descargar vulnerabilidades (CVE) desde API (NVD).

✅ Paso 2 ➜ Extraer campos clave.

✅ Paso 3 ➜ Mostrar en consola como tabla.

✅ Paso 4 ➜ Guardar en CSV o Excel.

---

### ✅ Ejemplo paso a paso

---

#### ✅ Importar librerías

```python
import requests
import pandas as pd
from tabulate import tabulate
```

✅ Explicación:

- `requests` ➜ para pedir datos a la API.
- `pandas` ➜ manejar los resultados en forma de tabla.
- `tabulate` ➜ imprimir resultados bonitos.

---

#### ✅ Función para obtener datos

```python
def obtener_cves(software):
    url = 'https://services.nvd.nist.gov/rest/json/cves/2.0'
    params = {
        'keywordSearch': software,
        'resultsPerPage': 20
    }

    print(f"\n[*] Buscando CVEs para: {software}\n")
    response = requests.get(url, params=params)
    if response.status_code != 200:
        print("[!] Error al consultar la API:", response.status_code)
        return []

    data = response.json()
    return data.get('vulnerabilities', [])
```

✅ Explicación:

- Usa **keywordSearch** para filtrar CVEs por nombre.
- Devuelve **lista de vulnerabilidades**.

---

#### ✅ Procesar resultados y extraer campos clave

```python
def procesar_cves(lista_cves):
    resultados = []

    for item in lista_cves:
        cve_info = item['cve']
        cve_id = cve_info.get('id')
        descripcion = cve_info['descriptions'][0]['value']
        cvss = None

        metrics = cve_info.get('metrics', {})
        if 'cvssMetricV31' in metrics:
            cvss = metrics['cvssMetricV31'][0]['cvssData']['baseScore']
        elif 'cvssMetricV30' in metrics:
            cvss = metrics['cvssMetricV30'][0]['cvssData']['baseScore']
        elif 'cvssMetricV2' in metrics:
            cvss = metrics['cvssMetricV2'][0]['cvssData']['baseScore']

        resultados.append({
            'CVE_ID': cve_id,
            'Descripción': descripcion,
            'CVSS': cvss
        })

    return pd.DataFrame(resultados)
```

✅ Explicación:

- Extrae ➜ CVE_ID, Descripción y CVSS.
- Devuelve ➜ DataFrame de pandas.

---

#### ✅ Mostrar resultados en consola en forma de tabla

```python
def mostrar_tabla(df):
    if df.empty:
        print("[!] No se encontraron resultados.")
        return

    print("\n[+] Resultados encontrados:\n")
    print(tabulate(df, headers='keys', tablefmt='psql', showindex=False))
```

✅ Explicación:

- Usa `tabulate` para imprimir **bonito**.
- Formato ➜ estilo SQL, columnas alineadas.

---

#### ✅ Guardar resultados en CSV o Excel

```python
def guardar_resultados(df, software):
    csv_file = f"cves_{software.replace(' ', '_')}.csv"
    excel_file = f"cves_{software.replace(' ', '_')}.xlsx"

    df.to_csv(csv_file, index=False)
    df.to_excel(excel_file, index=False)

    print(f"\n[+] Resultados guardados en:\n - {csv_file}\n - {excel_file}")
```

✅ Explicación:

- Guarda resultados en **CSV** y **Excel**.
- Usa **openpyxl** para el Excel.

---

#### ✅ Programa principal

```python
if __name__ == "__main__":
    software = input("\n>> Ingresa el software/versión a buscar: ")

    cves_json = obtener_cves(software)
    df_cves = procesar_cves(cves_json)

    mostrar_tabla(df_cves)
    if not df_cves.empty:
        guardar_resultados(df_cves, software)
```

✅ Explicación:

- Pide al usuario el software.
- Descarga resultados.
- Muestra tabla en consola.
- Guarda en archivo.

---

### ✅ Ejecución completa

✅ Guarda el script como ➜ `escanner_presentacion.py`

---

✅ Ejecuta en terminal:

```bash
python escanner_presentacion.py
```

✅ Ejemplo de uso:

```
>> Ingresa el software/versión a buscar: Apache 2.4.49
```

✅ Resultado en consola:

```
[+] Resultados encontrados:

+-----------------+---------------------------------------------------------------+--------+
| CVE_ID          | Descripción                                                   |  CVSS  |
|------------------+---------------------------------------------------------------+--------+
| CVE-2021-41773  | Path traversal en Apache 2.4.49 permite acceso no autorizado. |   7.5  |
| CVE-2021-42013  | Remote Code Execution en Apache 2.4.49 y 2.4.50.              |   9.8  |
+-----------------+---------------------------------------------------------------+--------+

[+] Resultados guardados en:
 - cves_Apache_2.4.49.csv
 - cves_Apache_2.4.49.xlsx
```

---

✅ También genera archivos:

✔️ `cves_Apache_2.4.49.csv`:

```
CVE_ID,Descripción,CVSS
CVE-2021-41773,"Path traversal en Apache 2.4.49 permite acceso no autorizado.",7.5
CVE-2021-42013,"Remote Code Execution en Apache 2.4.49 y 2.4.50.",9.8
```

✔️ `cves_Apache_2.4.49.xlsx`:

| CVE_ID         | Descripción                                                   | CVSS |
| -------------- | ------------------------------------------------------------- | ---- |
| CVE-2021-41773 | Path traversal en Apache 2.4.49 permite acceso no autorizado. | 7.5  |
| CVE-2021-42013 | Remote Code Execution en Apache 2.4.49 y 2.4.50.              | 9.8  |

---

### ✅ Variaciones avanzadas (opcional)

✔️ Filtrar solo CVSS ≥ 9 (críticos):

```python
def filtrar_criticos(df):
    criticos = df[df['CVSS'] >= 9]
    print("\n[+] Vulnerabilidades críticas encontradas:\n")
    print(tabulate(criticos, headers='keys', tablefmt='psql', showindex=False))
```

✅ Usar:

```python
filtrar_criticos(df_cves)
```

---

✔️ Graficar con matplotlib:

```python
import matplotlib.pyplot as plt

def graficar_cvss(df):
    df['CVSS'].hist(bins=10)
    plt.title('Distribución de CVSS')
    plt.xlabel('CVSS Score')
    plt.ylabel('Cantidad')
    plt.show()
```

✅ Usar:

```python
graficar_cvss(df_cves)
```

---

### ✅ Resumen

1️⃣ Instalar:

```
pip install requests pandas tabulate openpyxl
```

2️⃣ Descargar vulnerabilidades desde NVD.

3️⃣ Procesar datos ➜ ID, Descripción, CVSS.

4️⃣ Mostrar en consola ➜ tabla limpia con `tabulate`.

5️⃣ Guardar ➜ CSV y Excel.

6️⃣ Filtrar ➜ por criticidad.

7️⃣ (Opcional) ➜ Graficar.

---

### ✅ Resultado final

✔️ Tu escáner ya no solo "baja datos", sino que:

✅ ➜ Presenta resultados ordenados.

✅ ➜ Los guarda en formatos legibles.

✅ ➜ Ayuda a priorizar parches.

---

[🔼](#índice)

---

## **209. Integración de análisis de red y detección de vulnerabilidades**

### ✅ ¿Qué significa “Integración de análisis de red y detección de vulnerabilidades”?

Es **combinar dos etapas**:

1️⃣ **Análisis de red**

✔️ Descubrir hosts activos.

✔️ Detectar puertos abiertos y servicios.

✔️ Saber qué versiones de software corren.

2️⃣ **Detección de vulnerabilidades**

✔️ Usar la info anterior para buscar vulnerabilidades conocidas (CVEs).

✔️ Evaluar el riesgo (CVSS).

✅ En ciberseguridad, se usa para:

✔️ Auditorías.

✔️ Pentesting.

✔️ Gestión de parches.

---

### ✅ Flujo general (fácil de entender)

✅ Entrada ➜ red o IP objetivo.

✅ Paso 1 ➜ descubrir hosts activos (ping sweep, ARP).

✅ Paso 2 ➜ escanear puertos y servicios.

✅ Paso 3 ➜ identificar versión de software.

✅ Paso 4 ➜ buscar vulnerabilidades conocidas (CVE).

✅ Salida ➜ informe con hosts, puertos, servicios, CVEs y CVSS.

---

**Ejemplo esperado de resultado:**

```
Host: 192.168.1.10
 - Servicio: Apache 2.4.49
   - CVE-2021-41773 (CVSS 7.5): Path Traversal.
   - CVE-2021-42013 (CVSS 9.8): RCE.
 - Servicio: OpenSSH 8.2
   - CVE-2020-14145 (CVSS 5.3): Info disclosure.
```

---

### ✅ Herramientas comunes para esto

✔️ **nmap** ➜ descubrimiento de hosts, puertos, servicios, versiones.

✔️ **scapy** ➜ análisis de paquetes, ARP, sniffing personalizado.

✔️ **Python** ➜ para orquestar, analizar resultados y buscar CVEs.

✔️ **API de NVD** ➜ para buscar CVEs y obtener su CVSS.

---

### ✅ Instalación del entorno

#### ✅ Instalar Python

✅ Descargar ➜ [https://www.python.org/downloads/](https://www.python.org/downloads/)

✔️ Marcar “Add Python to PATH”.

✔️ Verificar:

```bash
python --version
```

---

#### ✅ Instalar nmap

✅ Linux:

```bash
sudo apt update
sudo apt install nmap
```

✅ Windows:

✔️ Descargar ➜ [https://nmap.org/download.html](https://nmap.org/download.html)

---

#### ✅ Instalar módulos de Python

✔️ Abre terminal o CMD:

```bash
pip install python-nmap requests pandas tabulate
```

✅ Librerías:

| Librería    | Uso                                |
| ----------- | ---------------------------------- |
| python-nmap | Controlar nmap desde Python.       |
| requests    | Llamar a APIs (NVD).               |
| pandas      | Manejar tablas de resultados.      |
| tabulate    | Mostrar tablas bonitas en consola. |

---

### ✅ Flujo de ejemplo práctico

Vamos a hacer un **mini escáner integrado**:

✅ Paso 1 ➜ Descubrir hosts vivos.

✅ Paso 2 ➜ Escanear puertos/servicios.

✅ Paso 3 ➜ Buscar CVEs en NVD usando el nombre/versión del servicio.

✅ Paso 4 ➜ Mostrar tabla final.

---

### ✅ Ejemplo sencillo en Python

Te dejo **paso por paso** con código comentado.

---

#### ✅ Importar librerías

```python
import nmap
import requests
import pandas as pd
from tabulate import tabulate
```

---

#### ✅ Definir escaneo de red con nmap

```python
def escanear_red(rango_ip):
    print(f"[*] Escaneando red: {rango_ip}")
    scanner = nmap.PortScanner()
    scanner.scan(hosts=rango_ip, arguments='-sn')
    hosts_activos = [host for host in scanner.all_hosts() if scanner[host].state() == 'up']
    return hosts_activos
```

✅ Explicación:

✔️ `-sn` ➜ Ping sweep (solo descubre hosts activos).

✔️ Devuelve lista de IPs.

---

#### ✅ Escanear puertos y servicios

```python
def escanear_puertos_servicios(ip):
    print(f"[*] Escaneando puertos en: {ip}")
    scanner = nmap.PortScanner()
    scanner.scan(ip, arguments='-sV --top-ports 10')

    servicios = []
    for proto in scanner[ip].all_protocols():
        ports = scanner[ip][proto].keys()
        for port in ports:
            service = scanner[ip][proto][port]
            name = service.get('name')
            product = service.get('product')
            version = service.get('version')
            if product:
                servicios.append({
                    'Port': port,
                    'Service': name,
                    'Product': product,
                    'Version': version
                })
    return servicios
```

✅ Explicación:

✔️ `-sV` ➜ detectar versión.

✔️ `--top-ports 10` ➜ solo los 10 puertos más comunes (rápido).

✔️ Devuelve lista de diccionarios con servicio, producto y versión.

---

#### ✅ Buscar CVEs en NVD

```python
def buscar_cves(software):
    print(f"[*] Buscando CVEs para: {software}")
    url = 'https://services.nvd.nist.gov/rest/json/cves/2.0'
    params = {'keywordSearch': software, 'resultsPerPage': 5}
    response = requests.get(url, params=params)

    if response.status_code != 200:
        print("[!] Error al consultar NVD")
        return []

    data = response.json().get('vulnerabilities', [])
    resultados = []

    for item in data:
        cve_id = item['cve']['id']
        desc = item['cve']['descriptions'][0]['value']
        cvss = None
        metrics = item['cve'].get('metrics', {})
        if 'cvssMetricV31' in metrics:
            cvss = metrics['cvssMetricV31'][0]['cvssData']['baseScore']
        elif 'cvssMetricV30' in metrics:
            cvss = metrics['cvssMetricV30'][0]['cvssData']['baseScore']
        elif 'cvssMetricV2' in metrics:
            cvss = metrics['cvssMetricV2'][0]['cvssData']['baseScore']

        resultados.append({
            'CVE_ID': cve_id,
            'Descripción': desc,
            'CVSS': cvss
        })
    return resultados
```

✅ Explicación:

✔️ Usa la API de NVD.

✔️ Filtra por palabra clave (producto y versión).

✔️ Extrae ID, descripción, CVSS.

---

#### ✅ Integrar todo

```python
def main():
    rango = input("\n>> Ingresa el rango de IP (ej: 192.168.1.0/24): ")
    hosts = escanear_red(rango)

    if not hosts:
        print("[!] No se encontraron hosts activos.")
        return

    resultados_finales = []

    for ip in hosts:
        servicios = escanear_puertos_servicios(ip)
        for servicio in servicios:
            producto_version = f"{servicio['Product']} {servicio['Version']}".strip()
            cves = buscar_cves(producto_version)

            for cve in cves:
                resultados_finales.append({
                    'IP': ip,
                    'Puerto': servicio['Port'],
                    'Servicio': servicio['Service'],
                    'Producto': producto_version,
                    'CVE_ID': cve['CVE_ID'],
                    'CVSS': cve['CVSS'],
                    'Descripción': cve['Descripción']
                })

    if resultados_finales:
        df = pd.DataFrame(resultados_finales)
        print("\n[+] Resultados encontrados:")
        print(tabulate(df, headers='keys', tablefmt='psql', showindex=False))
        df.to_csv('reporte_vulnerabilidades.csv', index=False)
        print("\n[+] Resultados guardados en reporte_vulnerabilidades.csv")
    else:
        print("[!] No se encontraron vulnerabilidades.")
```

✅ Explicación:

✔️ Escanea red ➜ hosts vivos.

✔️ Para cada host ➜ escanea servicios.

✔️ Para cada servicio ➜ busca CVEs.

✔️ Guarda todo en CSV.

✔️ Muestra tabla bonita.

---

#### ✅ Ejecutar

```python
if __name__ == "__main__":
    main()
```

---

✅ Guarda el archivo como:

```
analizador_red_vuln.py
```

✅ Ejecuta:

```
python analizador_red_vuln.py
```

---

### ✅ Resultado esperado

```
>> Ingresa el rango de IP (ej: 192.168.1.0/24): 192.168.1.0/24

[*] Escaneando red: 192.168.1.0/24
[*] Escaneando puertos en: 192.168.1.10
[*] Buscando CVEs para: Apache 2.4.49

[+] Resultados encontrados:

+---------------+---------+----------+-------------------+------------------+--------+--------------------------------------------------+
| IP            | Puerto  | Servicio | Producto          | CVE_ID           |  CVSS  | Descripción                                      |
|---------------+---------+----------+-------------------+------------------+--------+--------------------------------------------------|
| 192.168.1.10  | 80      | http     | Apache 2.4.49     | CVE-2021-41773   |  7.5   | Path Traversal en Apache...                      |
| 192.168.1.10  | 80      | http     | Apache 2.4.49     | CVE-2021-42013   |  9.8   | Remote Code Execution en Apache...               |
+---------------+---------+----------+-------------------+------------------+--------+--------------------------------------------------+

[+] Resultados guardados en reporte_vulnerabilidades.csv
```

---

✅ También tendrás:

✔️ Archivo CSV con todas las columnas:

```
IP,Puerto,Servicio,Producto,CVE_ID,CVSS,Descripción
```

✔️ Muy útil para informes de auditoría.

---

### ✅ Resumen súper corto

✅ 1️⃣ Instalar dependencias:

```
pip install python-nmap requests pandas tabulate
```

✅ 2️⃣ Escanear red ➜ nmap.

✅ 3️⃣ Extraer servicios/productos.

✅ 4️⃣ Consultar CVEs ➜ NVD API.

✅ 5️⃣ Extraer CVSS.

✅ 6️⃣ Presentar resultados en tabla y CSV.

---

[🔼](#índice)

---

## **210. Instalación y configuración de Nessus**

### 🔐 ¿Qué es Nessus?

**Nessus** es uno de los escáneres de vulnerabilidades más populares y potentes del mundo. Fue desarrollado por **Tenable** y te permite:

✅ Escanear equipos (PC, servidores, routers, etc.).

✅ Detectar vulnerabilidades (CVE), configuraciones débiles y puertos abiertos.

✅ Exportar informes con riesgos clasificados (bajo, medio, alto, crítico).

✅ Automatizar pruebas de seguridad.

> 💡 Hay una versión **gratuita** llamada **Nessus Essentials** (ideal para aprender y probar).

---

### 🧰 Requisitos

✔️ Sistema operativo compatible:

- **Windows 10/11**, **Windows Server**
- **Linux (Ubuntu, Debian, CentOS, Kali, etc.)**
- **macOS**

✔️ Conexión a internet (para la activación).

✔️ Registro gratuito en Tenable para obtener tu código de activación.

---

### 🖥️ 1. Registro y descarga de Nessus

#### 🔗 Paso 1: Ir a la página oficial

👉 [https://www.tenable.com/products/nessus/nessus-essentials](https://www.tenable.com/products/nessus/nessus-essentials)

#### ✅ Paso 2: Completa el formulario

- Nombre, correo, organización (puede ser personal).
- Te enviarán un **código de activación** (licencia gratuita de Nessus Essentials).

Ejemplo:

```
Código: 8C-1234-5678-90AB-CDEF
```

#### 📦 Paso 3: Descarga el instalador

Elige tu sistema operativo:

- Windows (.exe)
- Linux (.deb o .rpm)
- macOS (.dmg)

---

### 💻 2. Instalación en Windows (explicación sencilla)

#### 🔧 Paso 1: Ejecuta el instalador

Haz doble clic en el archivo `.exe` descargado.

#### ✅ Paso 2: Acepta los términos y sigue los pasos

✔️ Instalará como servicio de Windows.

✔️ Al finalizar, se abrirá el navegador con:

```
https://localhost:8834
```

> ✅ Si no se abre solo, escribe eso en tu navegador: `https://localhost:8834` (¡no olvides el `https`!).

---

### 🌐 3. Configuración inicial

#### 👤 Paso 1: Crear usuario y contraseña

Ejemplo:

- Usuario: `admin`
- Contraseña: `Segura123!`

#### 🧾 Paso 2: Ingresar tu código de activación

✔️ Ingresa el código que llegó a tu correo.

✔️ El sistema descargará plugins de vulnerabilidades (esto puede tardar unos minutos).

#### 🗂️ Paso 3: Ya puedes usar Nessus

Verás el panel principal:

```
[+] Dashboard
[+] My Scans
[+] Policies
```

---

### 🔍 4. Primer escaneo básico

#### 🧪 Paso 1: Crear un escaneo

1. Clic en “**New Scan**”.
2. Selecciona “**Basic Network Scan**”.

#### 📋 Paso 2: Configura el escaneo

- **Name**: Escaneo red local
- **Targets**: IP o rango (ej: `192.168.1.1-254`)
- Puedes dejar las opciones por defecto.

#### ▶️ Paso 3: Ejecutar escaneo

- Haz clic en “**Save**” y luego “**Launch**”.

✅ Verás el progreso y luego un resumen con:

- Puertos abiertos
- Servicios detectados
- Vulnerabilidades clasificadas (CVSS)
- CVEs relacionadas

---

### 🧾 5. Ver resultados

Haz clic en el nombre del escaneo ➜ verás:

- **Host(s) encontrados**
- **Vulnerabilidades por nivel (bajo, medio, alto, crítico)**
- **Detalles por CVE**
- **Recomendaciones para mitigar cada problema**

Puedes exportar en:

- PDF
- CSV
- HTML

---

### 🛠️ 6. Configuración extra (opcional)

#### 🔧 Cambiar el puerto (por defecto es 8834)

En Linux/Windows, se puede modificar el archivo de configuración:
`nessusd.conf`

---

### 📦 7. Instalación en Linux (ejemplo con Kali o Ubuntu)

#### Paso 1: Descargar paquete .deb

```bash
wget https://www.tenable.com/downloads/api/v1/public/pages/nessus/downloads/17344/download?i_agree_to_tenable_license_agreement=true -O nessus.deb
```

> (Link puede cambiar — siempre revisa la web oficial)

#### Paso 2: Instalar

```bash
sudo dpkg -i nessus.deb
sudo systemctl start nessusd
```

#### Paso 3: Accede vía navegador

```
https://localhost:8834
```

---

### 🤖 ¿Y si quiero usar Nessus con Python?

Nessus tiene una **API REST** para que tú puedas:

- Lanzar escaneos desde código
- Obtener reportes
- Analizar CVEs con tus scripts

> Si te interesa eso, dime y te explico cómo usar **la API de Nessus con Python paso a paso**.

---

### 📚 Resumen final

| Paso                 | Detalles                                                                           |
| -------------------- | ---------------------------------------------------------------------------------- |
| Registro             | En [Tenable Essentials](https://www.tenable.com/products/nessus/nessus-essentials) |
| Código de activación | Llega por correo (gratis)                                                          |
| Instalación          | Ejecutar el instalador (.exe o .deb)                                               |
| Acceso               | `https://localhost:8834` (desde el navegador)                                      |
| Primer escaneo       | Crear escaneo ➜ elegir IP ➜ lanzar ➜ revisar resultados                            |
| Exportar             | PDF / CSV con CVEs, niveles de riesgo, soluciones                                  |

---

[🔼](#índice)

---

## **211. Introducción a Nessus con Python**

### ✅ ¿Qué es Nessus y para qué sirve?

**Nessus** es un escáner de vulnerabilidades profesional.
✔️ Analiza hosts o redes.

✔️ Detecta puertos abiertos y servicios.

✔️ Encuentra vulnerabilidades (CVEs, con su CVSS).

✔️ Genera reportes.

**Nessus Essentials** ➜ versión gratuita para aprendizaje (hasta 16 IPs).

---

### ✅ ¿Qué es la API de Nessus?

✅ Nessus tiene una **API REST** oficial:

- Usas peticiones HTTP (GET, POST, DELETE, etc.).
- Puedes **controlar Nessus desde scripts en Python**.

✅ Cosas que puedes hacer con la API:

- Crear escaneos.
- Lanzarlos.
- Consultar el progreso.
- Descargar resultados.

> **Muy útil** para automatización en pentesting o auditorías.

---

### ✅ Instalación de Nessus (Resumen rápido)

Ya vimos cómo hacerlo, pero repasemos brevemente:

✔️ **Descargar** desde:

[https://www.tenable.com/products/nessus/nessus-essentials](https://www.tenable.com/products/nessus/nessus-essentials)

✔️ **Instalar**:

- Windows ➜ ejecutable `.exe`.
- Linux ➜ `.deb` o `.rpm`.

✔️ **Acceder**:

```
https://localhost:8834
```

✔️ **Activar con tu código gratuito**.

---

### ✅ Cómo obtener las credenciales para la API

Para usar la API necesitas **loguearte**.

✅ La forma más sencilla:

**Usuario y contraseña** ➜ los mismos que creaste al instalar Nessus.

> Ejemplo:

```
Usuario: admin
Contraseña: MiClaveSegura123!
```

---

### ✅ Cómo se instala el entorno de Python

Necesitamos librerías para:

✔️ hacer peticiones HTTP.

✔️ manejar datos (opcional).

✅ Instalarlas:

```
pip install requests pandas
```

✔️ `requests` ➜ para hablar con la API de Nessus.

✔️ `pandas` ➜ opcional para manejar tablas.

---

### ✅ Arquitectura general

✅ Tu script en Python ➜ se conecta a Nessus (que corre en tu máquina o servidor).

✅ Usa la **API REST** para:

- Autenticarse
- Obtener un token de sesión
- Enviar comandos (crear escaneo, lanzarlo, etc.)
- Descargar resultados

---

### ✅ Flujo de trabajo con la API

✅ 1. Autenticarse ➜ obtener **token de sesión**.

✅ 2. Listar escaneos existentes.

✅ 3. Crear un nuevo escaneo.

✅ 4. Lanzarlo.

✅ 5. Obtener resultados.

---

### ✅ Ejemplo práctico en Python

#### 🔹 Importar librerías

```python
import requests
import json
import pandas as pd
```

---

#### 🔹 Definir conexión a Nessus

Por defecto, Nessus corre en:

```
https://localhost:8834
```

Pero puede ser un servidor remoto.

---

#### 🔹 Ignorar advertencia SSL (opcional)

Nessus usa un certificado autofirmado ➜ suele dar advertencia.

```python
import urllib3
urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)
```

---

#### ✅ Autenticación

Necesitas **usuario** y **contraseña**.

```python
NESSUS_URL = "https://localhost:8834"
USERNAME = "admin"
PASSWORD = "TuContraseñaSegura"

def obtener_token():
    url = f"{NESSUS_URL}/session"
    data = {"username": USERNAME, "password": PASSWORD}
    r = requests.post(url, json=data, verify=False)
    if r.status_code == 200:
        token = r.json()['token']
        print("[+] Token obtenido:", token)
        return token
    else:
        print("[!] Error de autenticación")
        print(r.text)
        return None
```

✅ Resultado esperado:

```
[+] Token obtenido: abcdef123456...
```

---

#### ✅ Listar escaneos existentes

```python
def listar_escaneos(token):
    headers = {"X-Cookie": f"token={token}"}
    url = f"{NESSUS_URL}/scans"
    r = requests.get(url, headers=headers, verify=False)
    data = r.json()
    scans = data.get('scans', [])

    if scans:
        print("\n[+] Escaneos encontrados:")
        for s in scans:
            print(f"- ID: {s['id']} | Nombre: {s['name']} | Estado: {s['status']}")
    else:
        print("[!] No hay escaneos.")
```

✅ Resultado esperado:

```
[+] Escaneos encontrados:
- ID: 1 | Nombre: Red local | Estado: completed
- ID: 2 | Nombre: Servidor Web | Estado: running
```

---

#### ✅ Crear un nuevo escaneo (básico)

✅ Necesitas conocer el **template UUID**.

- Nessus tiene plantillas (ej: advanced, basic).

✅ Para obtener plantillas:

```python
def obtener_templates(token):
    headers = {"X-Cookie": f"token={token}"}
    url = f"{NESSUS_URL}/editor/scan/templates"
    r = requests.get(url, headers=headers, verify=False)
    data = r.json()
    templates = data.get('templates', [])

    print("\n[+] Templates disponibles:")
    for t in templates:
        print(f"- {t['name']} | UUID: {t['uuid']}")
```

✅ Resultado:

```
[+] Templates disponibles:
- advanced | UUID: abcd1234...
- basic | UUID: efgh5678...
```

---

✅ Crear el escaneo:

```python
def crear_escaneo(token, nombre, targets, template_uuid):
    headers = {"X-Cookie": f"token={token}"}
    url = f"{NESSUS_URL}/scans"
    data = {
        "uuid": template_uuid,
        "settings": {
            "name": nombre,
            "text_targets": targets
        }
    }
    r = requests.post(url, headers=headers, json=data, verify=False)
    if r.status_code == 200:
        scan_id = r.json()['scan']['id']
        print(f"[+] Escaneo creado con ID: {scan_id}")
        return scan_id
    else:
        print("[!] Error al crear escaneo")
        print(r.text)
        return None
```

✅ Uso:

```
scan_id = crear_escaneo(token, "Escaneo Python", "192.168.1.1", "UUID_DEL_TEMPLATE")
```

---

#### ✅ Lanzar el escaneo

```python
def lanzar_escaneo(token, scan_id):
    headers = {"X-Cookie": f"token={token}"}
    url = f"{NESSUS_URL}/scans/{scan_id}/launch"
    r = requests.post(url, headers=headers, verify=False)
    if r.status_code == 200:
        print("[+] Escaneo lanzado!")
    else:
        print("[!] Error al lanzar escaneo")
        print(r.text)
```

---

#### ✅ Descargar resultados (CSV o JSON)

Una vez termine el escaneo:

```python
def exportar_resultados(token, scan_id, formato="csv"):
    headers = {"X-Cookie": f"token={token}"}
    url = f"{NESSUS_URL}/scans/{scan_id}/export"
    data = {"format": formato}
    r = requests.post(url, headers=headers, json=data, verify=False)

    if r.status_code == 200:
        file_id = r.json()['file']
        print(f"[+] Exportando... file ID: {file_id}")
        return file_id
    else:
        print("[!] Error al exportar")
        print(r.text)
        return None

def descargar_archivo(token, scan_id, file_id, filename):
    headers = {"X-Cookie": f"token={token}"}
    status_url = f"{NESSUS_URL}/scans/{scan_id}/export/{file_id}/status"

    while True:
        r = requests.get(status_url, headers=headers, verify=False)
        if r.json()['status'] == 'ready':
            break

    download_url = f"{NESSUS_URL}/scans/{scan_id}/export/{file_id}/download"
    r = requests.get(download_url, headers=headers, verify=False)

    with open(filename, 'wb') as f:
        f.write(r.content)

    print(f"[+] Resultado guardado en: {filename}")
```

✅ Uso:

```
file_id = exportar_resultados(token, scan_id)
descargar_archivo(token, scan_id, file_id, "reporte.csv")
```

---

#### ✅ Programa principal

```python
if __name__ == "__main__":
    token = obtener_token()
    if not token:
        exit()

    listar_escaneos(token)
    obtener_templates(token)

    # Crear nuevo escaneo (rellena con tu UUID de template)
    # scan_id = crear_escaneo(token, "MiEscaneoPython", "192.168.1.1", "UUID_DEL_TEMPLATE")
    # lanzar_escaneo(token, scan_id)
```

---

### ✅ Resultado esperado

✔️ Listar tus escaneos en consola.

✔️ Crear nuevos escaneos automáticamente.

✔️ Lanzarlos.

✔️ Exportar resultados a CSV o JSON.

✔️ Usar pandas para analizarlos.

---

### ✅ Resumen

✅ Instalar Nessus y activarlo.

✅ Obtener tu usuario/contraseña.

✅ Instalar dependencias:

```
pip install requests pandas
```

✅ Usar la API REST de Nessus con Python para:

✔️ Autenticarse.

✔️ Crear escaneos.

✔️ Lanzarlos.

✔️ Descargar resultados.

---

[🔼](#índice)

---

## **212. Nessus con Python: Creación de una sesión y consulta de políticas**

### 🌟 ¿Qué es Nessus?

✅ Nessus = Escáner de vulnerabilidades muy usado en ciberseguridad.

✔️ Detecta puertos abiertos y servicios.

✔️ Encuentra vulnerabilidades (CVE).

✔️ Genera reportes.

✅ Hay versión **gratuita** (Nessus Essentials) ➜ excelente para aprender.

---

### 🌐 ¿Qué es la API de Nessus?

✅ Nessus tiene **API REST** ➜ te permite controlarlo desde código.

✅ Puedes:

✔️ Crear sesión (login)

✔️ Crear escaneos

✔️ Lanzar escaneos

✔️ Descargar resultados

✔️ Consultar políticas (policies)

✅ Perfecto para **automatización y scripting en Python**.

---

### 🔑 ¿Qué es “crear una sesión”?

✅ Significa **loguearte** en Nessus desde Python.

✔️ En la interfaz web tú escribes tu usuario/contraseña.

✔️ Con la **API** haces lo mismo pero desde tu código.

✔️ Nessus devuelve un **token de sesión** (como un "pase de acceso").

✔️ Ese token se usa en los siguientes requests.

> 💡 Sin ese token, la API no te dejará hacer nada.

---

### 📋 ¿Qué son las “policies” (políticas)?

✅ Son **configuraciones de escaneo** predefinidas en Nessus.

✔️ Definen **qué** y **cómo** se escanea.

✔️ Ejemplo:

- Escaneo básico de red
- Detección de vulnerabilidades web
- Escaneo de cumplimiento de normas

✅ La API te permite **listar todas las policies** disponibles.

✅ Así puedes elegir la que necesitas al crear un nuevo escaneo.

---

### 💻 Resumen rápido: instalación de Nessus

✅ Descargar ➜ [https://www.tenable.com/products/nessus/nessus-essentials](https://www.tenable.com/products/nessus/nessus-essentials)

✅ Instalar ➜ Windows / Linux.

✅ Acceder en navegador:

```
https://localhost:8834
```

✅ Crear usuario y contraseña.

✅ Activar con código gratuito.

---

### 🐍 Instalar el entorno Python

✅ Necesitas `requests` para hablar con la API:

```
pip install requests
```

✅ Opcional: ignorar advertencias SSL si usas certificado autofirmado:

```
pip install urllib3
```

---

### ⚙️ Arquitectura de la conexión

✅ Tu script en Python ➜ se conecta a Nessus (localhost:8834).

✅ Envío de requests HTTPS ➜ recibe JSON de respuesta.

✔️ Primero ➜ login ➜ obtener token.

✔️ Después ➜ usar token para otras llamadas (listar policies, crear escaneos, etc.).

---

### ✅ Empezamos el ejemplo en Python

Vamos paso por paso con **código comentado**.

---

#### 📌 Importar librerías

```python
import requests
import urllib3
```

✅ `requests` ➜ para hacer llamadas HTTP.

✅ `urllib3` ➜ para desactivar advertencias SSL.

---

#### 📌 Ignorar advertencias de SSL

> Nessus usa un certificado autofirmado por defecto.

```python
urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)
```

✅ Así evitas los avisos de "InsecureRequestWarning".

---

#### 📌 Configurar la URL y credenciales

```python
NESSUS_URL = "https://localhost:8834"
USERNAME = "admin"
PASSWORD = "TuContraseñaSegura"
```

✅ Cambia `"TuContraseñaSegura"` por la tuya.

---

#### ✅ Crear sesión (login)

Aquí se autentica tu script.

```python
def crear_sesion():
    url = f"{NESSUS_URL}/session"
    datos = {
        "username": USERNAME,
        "password": PASSWORD
    }
    respuesta = requests.post(url, json=datos, verify=False)

    if respuesta.status_code == 200:
        token = respuesta.json()["token"]
        print("[+] Sesión creada correctamente. Token:", token)
        return token
    else:
        print("[!] Error al crear sesión")
        print(respuesta.text)
        return None
```

✅ Explicación:

✔️ POST a `/session` con usuario y contraseña.

✔️ Devuelve `token` si es correcto.

---

✅ Resultado esperado:

```
[+] Sesión creada correctamente. Token: abcdef123456...
```

---

#### ✅ Consultar las policies (políticas)

✔️ Ahora usamos el **token** para acceder a `/policies`.

```python
def listar_policies(token):
    url = f"{NESSUS_URL}/policies"
    headers = {"X-Cookie": f"token={token}"}
    respuesta = requests.get(url, headers=headers, verify=False)

    if respuesta.status_code == 200:
        data = respuesta.json()
        policies = data.get("policies", [])

        if not policies:
            print("[!] No hay políticas encontradas.")
            return

        print("\n[+] Policies disponibles:")
        for p in policies:
            print(f"- ID: {p['id']} | Nombre: {p['name']}")
    else:
        print("[!] Error al consultar policies")
        print(respuesta.text)
```

✅ Explicación:

✔️ GET a `/policies` con encabezado `token`.

✔️ Devuelve lista de políticas.

---

✅ Resultado esperado:

```
[+] Policies disponibles:
- ID: 1 | Nombre: Escaneo Básico de Red
- ID: 2 | Nombre: Detección Web Avanzada
```

---

### ✅ Programa principal

✅ Para juntar todo:

```python
if __name__ == "__main__":
    token = crear_sesion()
    if token:
        listar_policies(token)
```

---

#### ✅ Código completo de ejemplo

##### Copiar y pegar

```python
import requests
import urllib3

# Ignorar advertencias SSL
urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)

# Configuración
NESSUS_URL = "https://localhost:8834"
USERNAME = "admin"
PASSWORD = "TuContraseñaSegura"

def crear_sesion():
    url = f"{NESSUS_URL}/session"
    datos = {
        "username": USERNAME,
        "password": PASSWORD
    }
    respuesta = requests.post(url, json=datos, verify=False)

    if respuesta.status_code == 200:
        token = respuesta.json()["token"]
        print("[+] Sesión creada correctamente. Token:", token)
        return token
    else:
        print("[!] Error al crear sesión")
        print(respuesta.text)
        return None

def listar_policies(token):
    url = f"{NESSUS_URL}/policies"
    headers = {"X-Cookie": f"token={token}"}
    respuesta = requests.get(url, headers=headers, verify=False)

    if respuesta.status_code == 200:
        data = respuesta.json()
        policies = data.get("policies", [])

        if not policies:
            print("[!] No hay políticas encontradas.")
            return

        print("\n[+] Policies disponibles:")
        for p in policies:
            print(f"- ID: {p['id']} | Nombre: {p['name']}")
    else:
        print("[!] Error al consultar policies")
        print(respuesta.text)

if __name__ == "__main__":
    token = crear_sesion()
    if token:
        listar_policies(token)
```

---

✅ Resultado esperado en consola:

```
[+] Sesión creada correctamente. Token: abcdef123456...

[+] Policies disponibles:
- ID: 1 | Nombre: Escaneo Básico de Red
- ID: 2 | Nombre: Detección Web Avanzada
```

---

### ✅ Requisitos previos (resumen rápido)

✔️ Tener Nessus **ya instalado y corriendo**.

✔️ Saber usuario y contraseña de Nessus.

✔️ Tener Python 3 instalado.

✔️ Instalar requests:

```
pip install requests
```

---

[🔼](#índice)

---

## **213. Nessus con Python: Creación de escaneos**

### 🌟 Qué es Nessus y su API (resumen rápido)

✅ **Nessus** = escáner de vulnerabilidades muy usado.

✔️ Detecta puertos abiertos.

✔️ Encuentra vulnerabilidades (CVE).

✔️ Clasifica riesgos (CVSS).

✔️ Genera informes.

✅ **API REST de Nessus** ➜ para controlarlo desde código.

✔️ Autenticarse.

✔️ Crear y lanzar escaneos.

✔️ Consultar resultados.

✔️ Descargar reportes.

---

### 🌐 ¿Qué es "crear un escaneo"?

✅ En Nessus, un "escaneo" es una definición de:

✔️ Nombre del análisis.

✔️ Objetivos (IPs o rangos).

✔️ Política o plantilla de escaneo (qué tipo de pruebas se harán).

✔️ Configuraciones avanzadas (credenciales, puertos, etc.).

✅ Con la **API de Nessus**, puedes:

✔️ Crear estos escaneos automáticamente.

✔️ Guardarlos en el servidor de Nessus.

✔️ Lanzarlos en cualquier momento.

---

### ⚙️ Instalación y preparación necesarias

✅ Tener Nessus **ya instalado** y corriendo en tu máquina o servidor.

✔️ Acceso en navegador:

```
https://localhost:8834
```

✔️ Usuario y contraseña definidos.

✅ Python 3 instalado.

✅ Paquete requests:

```
pip install requests
```

✅ Opcional (para evitar advertencias SSL):

```
pip install urllib3
```

---

### 💡 Arquitectura del flujo

✅ 1️⃣ Tu script en Python se conecta a Nessus por HTTPS.

✅ 2️⃣ Hace login ➜ obtiene un **token**.

✅ 3️⃣ Usa el token para **crear escaneos**.

✅ 4️⃣ Puede **lanzarlos** y ver resultados.

---

### 💻 Explicación paso a paso con código

Vamos a construir un **script en Python** que:

✅ Hace login (crea sesión).

✅ Obtiene la lista de plantillas (policies/templates) para elegir.

✅ Crea un nuevo escaneo con nombre y objetivo.

✅ Lanza el escaneo.

---

#### 📌 Importar librerías

```python
import requests
import urllib3
```

✅ `requests` ➜ para hablar con la API.

✅ `urllib3` ➜ para ignorar advertencias SSL.

---

#### 📌 Ignorar advertencias SSL

Nessus suele usar certificados autofirmados.

```python
urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)
```

---

#### 📌 Configurar variables básicas

✅ Cambia los valores por los de tu Nessus:

```python
NESSUS_URL = "https://localhost:8834"
USERNAME = "admin"
PASSWORD = "TuContraseñaSegura"
```

---

#### ✅ Crear sesión (login) y obtener token

Este paso es **obligatorio**.

> La API requiere un token para autenticar todas las llamadas.

```python
def crear_sesion():
    url = f"{NESSUS_URL}/session"
    datos = {
        "username": USERNAME,
        "password": PASSWORD
    }
    respuesta = requests.post(url, json=datos, verify=False)

    if respuesta.status_code == 200:
        token = respuesta.json()["token"]
        print("[+] Sesión creada correctamente. Token:", token)
        return token
    else:
        print("[!] Error al crear sesión")
        print(respuesta.text)
        return None
```

✅ Resultado esperado en consola:

```
[+] Sesión creada correctamente. Token: abcdef123456
```

---

#### ✅ Ver plantillas de escaneo disponibles

> Para crear un escaneo, necesitas el **UUID de la plantilla** (template).

✔️ Ejemplo:

- **Basic Network Scan** ➜ UUID específico.
- **Advanced Scan** ➜ otro UUID.

✅ Este paso te permite elegir el tipo de escaneo:

```python
def obtener_templates(token):
    url = f"{NESSUS_URL}/editor/scan/templates"
    headers = {"X-Cookie": f"token={token}"}
    respuesta = requests.get(url, headers=headers, verify=False)

    if respuesta.status_code == 200:
        data = respuesta.json()
        templates = data.get("templates", [])

        print("\n[+] Templates disponibles:")
        for t in templates:
            print(f"- Name: {t['name']} | UUID: {t['uuid']}")
    else:
        print("[!] Error al obtener templates")
        print(respuesta.text)
```

✅ Resultado esperado:

```
[+] Templates disponibles:
- Name: advanced | UUID: abcd1234-...
- Name: basic | UUID: efgh5678-...
```

✅ **💡 Apunta el UUID que quieres usar.**

---

#### ✅ Crear un nuevo escaneo

Ahora vamos a **crear** el escaneo con:

✔️ Nombre elegido.

✔️ Objetivos (IP o rango).

✔️ UUID de la plantilla.

```python
def crear_escaneo(token, nombre, targets, uuid_template):
    url = f"{NESSUS_URL}/scans"
    headers = {"X-Cookie": f"token={token}"}
    datos = {
        "uuid": uuid_template,
        "settings": {
            "name": nombre,
            "text_targets": targets
        }
    }

    respuesta = requests.post(url, headers=headers, json=datos, verify=False)

    if respuesta.status_code == 200:
        scan_id = respuesta.json()["scan"]["id"]
        print(f"[+] Escaneo creado correctamente. ID: {scan_id}")
        return scan_id
    else:
        print("[!] Error al crear escaneo")
        print(respuesta.text)
        return None
```

✅ Resultado esperado:

```
[+] Escaneo creado correctamente. ID: 5
```

✅ **Explicación sencilla:**

- `uuid`: indica la plantilla de escaneo.
- `text_targets`: las IPs o rangos.
- Nessus guarda este escaneo en su interfaz.

---

#### ✅ Lanzar el escaneo

> ¡Ahora podemos lanzarlo para que empiece a escanear!

```python
def lanzar_escaneo(token, scan_id):
    url = f"{NESSUS_URL}/scans/{scan_id}/launch"
    headers = {"X-Cookie": f"token={token}"}
    respuesta = requests.post(url, headers=headers, verify=False)

    if respuesta.status_code == 200:
        print("[+] Escaneo lanzado exitosamente!")
    else:
        print("[!] Error al lanzar escaneo")
        print(respuesta.text)
```

✅ Resultado esperado:

```
[+] Escaneo lanzado exitosamente!
```

---

#### ✅ Programa completo de ejemplo

Aquí te dejo **todo junto para copiar/pegar**:

```python
import requests
import urllib3

# Ignorar advertencias SSL
urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)

# Configuración
NESSUS_URL = "https://localhost:8834"
USERNAME = "admin"
PASSWORD = "TuContraseñaSegura"

def crear_sesion():
    url = f"{NESSUS_URL}/session"
    datos = {
        "username": USERNAME,
        "password": PASSWORD
    }
    respuesta = requests.post(url, json=datos, verify=False)

    if respuesta.status_code == 200:
        token = respuesta.json()["token"]
        print("[+] Sesión creada correctamente. Token:", token)
        return token
    else:
        print("[!] Error al crear sesión")
        print(respuesta.text)
        return None

def obtener_templates(token):
    url = f"{NESSUS_URL}/editor/scan/templates"
    headers = {"X-Cookie": f"token={token}"}
    respuesta = requests.get(url, headers=headers, verify=False)

    if respuesta.status_code == 200:
        data = respuesta.json()
        templates = data.get("templates", [])

        print("\n[+] Templates disponibles:")
        for t in templates:
            print(f"- Name: {t['name']} | UUID: {t['uuid']}")
    else:
        print("[!] Error al obtener templates")
        print(respuesta.text)

def crear_escaneo(token, nombre, targets, uuid_template):
    url = f"{NESSUS_URL}/scans"
    headers = {"X-Cookie": f"token={token}"}
    datos = {
        "uuid": uuid_template,
        "settings": {
            "name": nombre,
            "text_targets": targets
        }
    }

    respuesta = requests.post(url, headers=headers, json=datos, verify=False)

    if respuesta.status_code == 200:
        scan_id = respuesta.json()["scan"]["id"]
        print(f"[+] Escaneo creado correctamente. ID: {scan_id}")
        return scan_id
    else:
        print("[!] Error al crear escaneo")
        print(respuesta.text)
        return None

def lanzar_escaneo(token, scan_id):
    url = f"{NESSUS_URL}/scans/{scan_id}/launch"
    headers = {"X-Cookie": f"token={token}"}
    respuesta = requests.post(url, headers=headers, verify=False)

    if respuesta.status_code == 200:
        print("[+] Escaneo lanzado exitosamente!")
    else:
        print("[!] Error al lanzar escaneo")
        print(respuesta.text)

if __name__ == "__main__":
    token = crear_sesion()
    if token:
        obtener_templates(token)

        # REEMPLAZA ESTO CON TU UUID Y OBJETIVOS
        uuid_template = "TU_UUID_DE_TEMPLATE"
        objetivos = "192.168.1.1,192.168.1.2"
        nombre_escaneo = "Escaneo desde Python"

        scan_id = crear_escaneo(token, nombre_escaneo, objetivos, uuid_template)
        if scan_id:
            lanzar_escaneo(token, scan_id)
```

---

### ✅ Resultado esperado en consola

```
[+] Sesión creada correctamente. Token: abcdef123456

[+] Templates disponibles:
- Name: advanced | UUID: abcd-efgh...
- Name: basic | UUID: ijkl-mnop...

[+] Escaneo creado correctamente. ID: 5
[+] Escaneo lanzado exitosamente!
```

---

### ✅ Resumen de pasos

| Paso                 | Explicación                                  |
| -------------------- | -------------------------------------------- |
| 1️⃣ Crear sesión      | Login con usuario/contraseña ➜ obtener token |
| 2️⃣ Obtener templates | Ver UUIDs disponibles para escaneos          |
| 3️⃣ Crear escaneo     | Definir nombre, objetivo y template          |
| 4️⃣ Lanzar escaneo    | Iniciar el análisis en Nessus                |

---

[🔼](#índice)

---

## **214. Nessus con Python: Descarga y procesamiento de resultados**

### 🌟 ¿Qué son los resultados de un escaneo en Nessus?

✅ Cuando ejecutas un escaneo en Nessus, obtienes **informes de vulnerabilidades** con información como:

✔️ IP del host escaneado

✔️ Puertos abiertos

✔️ Servicios detectados

✔️ Vulnerabilidades encontradas (con CVE y CVSS)

✔️ Recomendaciones de mitigación

✅ Los resultados se pueden **exportar** en:

- JSON
- CSV
- PDF
- Nessus (archivo propietario)

✅ Usaremos **JSON** y **CSV** porque son fáciles de procesar con Python.

---

### 🌐 ¿Qué es la API REST de Nessus?

✅ Es una **interfaz web** para controlar Nessus desde código.

✔️ Haces peticiones HTTP (GET, POST)

✔️ Responde con JSON

✔️ Necesitas **autenticación** (token)

✅ Cosas que puedes hacer:

✔️ Crear escaneos

✔️ Lanzarlos

✔️ Monitorearlos

✔️ Descargar resultados

---

### ⚙️ Instalación necesaria

✅ Tener **Nessus** instalado y corriendo:

✔️ [https://www.tenable.com/products/nessus/nessus-essentials](https://www.tenable.com/products/nessus/nessus-essentials)

✔️ Acceder en navegador:

```
https://localhost:8834
```

✔️ Tener usuario y contraseña creados.

✅ Tener **Python 3** instalado.

✅ Instalar librerías necesarias:

```bash
pip install requests pandas
```

---

### 🧭 Flujo completo del proceso

✅ 1️⃣ Autenticarse ➜ obtener token

✅ 2️⃣ Listar escaneos ➜ elegir uno por ID

✅ 3️⃣ Solicitar exportación ➜ elegir formato

✅ 4️⃣ Descargar archivo exportado

✅ 5️⃣ Procesar contenido (CSV o JSON) en Python

---

### 💻 Código detallado, paso por paso

---

#### 📌 Importar librerías

```python
import requests
import urllib3
import time
import pandas as pd
```

✅ requests ➜ para API REST

✅ urllib3 ➜ para ignorar advertencias SSL

✅ pandas ➜ para procesar CSV o JSON

---

#### 📌 Ignorar advertencias SSL

Nessus usa certificados autofirmados:

```python
urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)
```

---

#### 📌 Configuración de conexión

```python
NESSUS_URL = "https://localhost:8834"
USERNAME = "admin"
PASSWORD = "TuContraseñaSegura"
```

✅ Cambia `USERNAME` y `PASSWORD` por los tuyos.

---

#### ✅ Autenticarse y obtener un token

> Todas las llamadas a la API requieren este token.

```python
def obtener_token():
    url = f"{NESSUS_URL}/session"
    data = {"username": USERNAME, "password": PASSWORD}
    r = requests.post(url, json=data, verify=False)

    if r.status_code == 200:
        token = r.json()['token']
        print("[+] Sesión creada. Token:", token)
        return token
    else:
        print("[!] Error al autenticar:", r.text)
        return None
```

✅ Resultado esperado:

```
[+] Sesión creada. Token: abcdef123456
```

---

#### ✅ Listar escaneos existentes

> Para saber qué ID usar al exportar.

```python
def listar_escaneos(token):
    headers = {"X-Cookie": f"token={token}"}
    url = f"{NESSUS_URL}/scans"
    r = requests.get(url, headers=headers, verify=False)

    if r.status_code == 200:
        scans = r.json().get('scans', [])
        print("\n[+] Escaneos disponibles:")
        for s in scans:
            print(f"ID: {s['id']} | Nombre: {s['name']} | Estado: {s['status']}")
    else:
        print("[!] Error al listar escaneos:", r.text)
```

✅ Resultado esperado:

```
[+] Escaneos disponibles:
ID: 3 | Nombre: Red interna | Estado: completed
ID: 5 | Nombre: Servidor Web | Estado: completed
```

✅ Apunta el **ID** del escaneo que quieras descargar.

---

#### ✅ Solicitar exportación de resultados

✔️ Necesitas especificar el formato.

✔️ La exportación es **asíncrona** ➜ hay que esperar que esté lista.

```python
def solicitar_exportacion(token, scan_id, formato="csv"):
    headers = {"X-Cookie": f"token={token}"}
    url = f"{NESSUS_URL}/scans/{scan_id}/export"
    data = {"format": formato}
    r = requests.post(url, headers=headers, json=data, verify=False)

    if r.status_code == 200:
        file_id = r.json()['file']
        print(f"[+] Export solicitado. File ID: {file_id}")
        return file_id
    else:
        print("[!] Error al solicitar export:", r.text)
        return None
```

✅ Resultado esperado:

```
[+] Export solicitado. File ID: 12
```

---

#### ✅ Verificar si el archivo está listo

> Exportaciones pueden tardar unos segundos.

```python
def esperar_exportacion(token, scan_id, file_id):
    headers = {"X-Cookie": f"token={token}"}
    status_url = f"{NESSUS_URL}/scans/{scan_id}/export/{file_id}/status"

    while True:
        r = requests.get(status_url, headers=headers, verify=False)
        status = r.json()['status']
        print(f"[*] Estado del export: {status}")

        if status == "ready":
            print("[+] Export listo para descargar!")
            break
        time.sleep(2)
```

✅ Resultado esperado:

```
[*] Estado del export: loading
[*] Estado del export: ready
[+] Export listo para descargar!
```

---

#### ✅ Descargar el archivo exportado

```python
def descargar_exportacion(token, scan_id, file_id, nombre_archivo):
    headers = {"X-Cookie": f"token={token}"}
    url = f"{NESSUS_URL}/scans/{scan_id}/export/{file_id}/download"
    r = requests.get(url, headers=headers, verify=False)

    if r.status_code == 200:
        with open(nombre_archivo, 'wb') as f:
            f.write(r.content)
        print(f"[+] Archivo descargado: {nombre_archivo}")
    else:
        print("[!] Error al descargar archivo:", r.text)
```

✅ Resultado esperado:

```
[+] Archivo descargado: resultados.csv
```

---

#### ✅ Procesar resultados en Python

✅ Si es CSV:

```python
def procesar_csv(nombre_archivo):
    df = pd.read_csv(nombre_archivo)
    print("\n[+] Vista previa del CSV:")
    print(df.head())
```

✅ Resultado esperado:

```
[+] Vista previa del CSV:
       Host        Port      Protocol      Vulnerability
0  192.168.1.5      22         tcp        SSH Weak Cipher
1  192.168.1.5      80         tcp        HTTP Directory Listing
```

✅ Si es JSON:

```python
def procesar_json(nombre_archivo):
    df = pd.read_json(nombre_archivo)
    print("\n[+] Vista previa del JSON:")
    print(df.head())
```

---

### ✅ Programa completo de ejemplo

Aquí tienes todo **juntito para copiar/pegar**:

```python
import requests
import urllib3
import time
import pandas as pd

urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)

NESSUS_URL = "https://localhost:8834"
USERNAME = "admin"
PASSWORD = "TuContraseñaSegura"

def obtener_token():
    url = f"{NESSUS_URL}/session"
    data = {"username": USERNAME, "password": PASSWORD}
    r = requests.post(url, json=data, verify=False)
    if r.status_code == 200:
        token = r.json()['token']
        print("[+] Sesión creada. Token:", token)
        return token
    else:
        print("[!] Error al autenticar:", r.text)
        return None

def listar_escaneos(token):
    headers = {"X-Cookie": f"token={token}"}
    url = f"{NESSUS_URL}/scans"
    r = requests.get(url, headers=headers, verify=False)
    if r.status_code == 200:
        scans = r.json().get('scans', [])
        print("\n[+] Escaneos disponibles:")
        for s in scans:
            print(f"ID: {s['id']} | Nombre: {s['name']} | Estado: {s['status']}")
    else:
        print("[!] Error al listar escaneos:", r.text)

def solicitar_exportacion(token, scan_id, formato="csv"):
    headers = {"X-Cookie": f"token={token}"}
    url = f"{NESSUS_URL}/scans/{scan_id}/export"
    data = {"format": formato}
    r = requests.post(url, headers=headers, json=data, verify=False)
    if r.status_code == 200:
        file_id = r.json()['file']
        print(f"[+] Export solicitado. File ID: {file_id}")
        return file_id
    else:
        print("[!] Error al solicitar export:", r.text)
        return None

def esperar_exportacion(token, scan_id, file_id):
    headers = {"X-Cookie": f"token={token}"}
    status_url = f"{NESSUS_URL}/scans/{scan_id}/export/{file_id}/status"
    while True:
        r = requests.get(status_url, headers=headers, verify=False)
        status = r.json()['status']
        print(f"[*] Estado del export: {status}")
        if status == "ready":
            print("[+] Export listo para descargar!")
            break
        time.sleep(2)

def descargar_exportacion(token, scan_id, file_id, nombre_archivo):
    headers = {"X-Cookie": f"token={token}"}
    url = f"{NESSUS_URL}/scans/{scan_id}/export/{file_id}/download"
    r = requests.get(url, headers=headers, verify=False)
    if r.status_code == 200:
        with open(nombre_archivo, 'wb') as f:
            f.write(r.content)
        print(f"[+] Archivo descargado: {nombre_archivo}")
    else:
        print("[!] Error al descargar archivo:", r.text)

def procesar_csv(nombre_archivo):
    df = pd.read_csv(nombre_archivo)
    print("\n[+] Vista previa del CSV:")
    print(df.head())

if __name__ == "__main__":
    token = obtener_token()
    if not token:
        exit()

    listar_escaneos(token)

    # Cambia esto por tu ID de escaneo
    scan_id = int(input("\nIngresa el ID del escaneo que deseas descargar: "))

    file_id = solicitar_exportacion(token, scan_id, formato="csv")
    if file_id:
        esperar_exportacion(token, scan_id, file_id)
        nombre_archivo = "resultado.csv"
        descargar_exportacion(token, scan_id, file_id, nombre_archivo)
        procesar_csv(nombre_archivo)
```

---

### ✅ Resultado esperado en consola

```
[+] Sesión creada. Token: abcdef123456
[+] Escaneos disponibles:
ID: 5 | Nombre: Servidor Web | Estado: completed
ID: 6 | Nombre: Red Interna | Estado: completed

Ingresa el ID del escaneo que deseas descargar: 5
[+] Export solicitado. File ID: 12
[*] Estado del export: loading
[*] Estado del export: ready
[+] Export listo para descargar!
[+] Archivo descargado: resultado.csv

[+] Vista previa del CSV:
       Host        Port    Protocol      Vulnerability
0  192.168.1.5      22      tcp         SSH Weak Cipher
1  192.168.1.5      80      tcp         HTTP Directory Listing
```

---

### ✅ Resumen práctico

✔️ 1. **Instalar Nessus** y obtener usuario/contraseña.

✔️ 2. **Instalar Python** con `pip install requests pandas`.

✔️ 3. **Usar la API** para:

✅ Autenticarse

✅ Listar escaneos

✅ Exportarlos en CSV

✅ Descargar resultados

✅ Procesarlos con pandas

---

[🔼](#índice)

---

## **215. Procesa los resultados de Nessus con Python**

### 🌟 ¿Qué son los resultados de Nessus?

✅ Nessus genera reportes de escaneos de vulnerabilidades.
✔️ Contienen información como:

- Host (IP, nombre)
- Puerto y protocolo
- Servicio detectado
- Vulnerabilidad encontrada (CVE, CVSS)
- Severidad (Critical, High, Medium, Low, Info)
- Recomendaciones

✅ Puedes **exportar** resultados en varios formatos:

✔️ CSV

✔️ JSON

✔️ PDF

✔️ Archivo .nessus (XML propietario)

✅ **CSV y JSON** son ideales para procesamiento con Python.

---

### 📦 Cómo se exportan los resultados

✅ Dos formas principales:

**A) Interfaz Web de Nessus**

✔️ Abre Nessus en tu navegador.

✔️ Ve a tu escaneo.

✔️ Haz clic en "Exportar".

✔️ Elige CSV o JSON.

✔️ Descarga el archivo.

**B) API REST de Nessus (opcional avanzado)**

✔️ Puedes hacer login desde Python.

✔️ Pedir exportación.

✔️ Descargar el archivo.

✔️ Ya te enseñé eso en el tema anterior 😊

✅ Aquí vamos a asumir que **ya tienes** un archivo CSV o JSON exportado.

---

### 💻 Instalación previa de Python y librerías

✅ Necesitas tener **Python 3**.

✅ Vamos a usar **pandas** para leer y analizar los resultados.

✅ Instala pandas (si aún no lo tienes):

```bash
pip install pandas
```

✅ Si quieres graficar también (opcional):

```bash
pip install matplotlib
```

---

### ⚙️ Estructura típica de un resultado CSV de Nessus

Un archivo CSV exportado desde Nessus suele verse así:

| Host         | Port | Protocol | Severity | Plugin Name            | CVE           |
| ------------ | ---- | -------- | -------- | ---------------------- | ------------- |
| 192.168.1.5  | 22   | tcp      | Medium   | SSH Weak Cipher        | CVE-2016-0777 |
| 192.168.1.5  | 80   | tcp      | High     | HTTP Directory Listing | CVE-2020-1234 |
| 192.168.1.10 | 443  | tcp      | Critical | TLS Vulnerability      | CVE-2014-3566 |

✅ Cada fila = hallazgo en un host/puerto.

✅ Columnas típicas:

- Host
- Port
- Protocol
- Severity
- Plugin Name
- CVE

---

### ✅ Leer un archivo CSV de Nessus en Python

Vamos a ver el ejemplo más sencillo:

✅ Suponemos que descargaste tu escaneo como **resultados.csv**.

---

#### 📌 Código básico

```python
import pandas as pd

# Cargar el CSV exportado desde Nessus
df = pd.read_csv('resultados.csv')

# Mostrar las primeras filas
print(df.head())
```

✅ Resultado esperado:

```
     Host        Port    Protocol    Severity            Plugin Name              CVE
0  192.168.1.5    22      tcp        Medium          SSH Weak Cipher           CVE-2016-0777
1  192.168.1.5    80      tcp        High            HTTP Directory Listing    CVE-2020-1234
...
```

---

#### ✅ Filtrar vulnerabilidades críticas

✔️ Ver solo lo más urgente:

```python
criticas = df[df['Severity'] == 'Critical']
print("\n[+] Vulnerabilidades críticas:")
print(criticas)
```

✅ Resultado:

```
[+] Vulnerabilidades críticas:
     Host           Port     Protocol    Severity       Plugin Name           CVE
2  192.168.1.10     443       tcp        Critical     TLS Vulnerability     CVE-2014-3566
```

---

#### ✅ Contar por severidad

✔️ Ver resumen rápido:

```python
conteo = df['Severity'].value_counts()
print("\n[+] Conteo de vulnerabilidades por severidad:")
print(conteo)
```

✅ Resultado esperado:

```
[+] Conteo de vulnerabilidades por severidad:
Medium      12
High         7
Critical     3
Low          1
```

---

#### ✅ Ver hosts únicos afectados

```python
hosts = df['Host'].unique()
print("\n[+] Hosts afectados:")
for h in hosts:
    print("-", h)
```

✅ Resultado esperado:

```
[+] Hosts afectados:
- 192.168.1.5
- 192.168.1.10
```

---

#### ✅ Exportar filtrado a Excel

✔️ Por ejemplo, solo críticas y altas:

```python
filtro = df[df['Severity'].isin(['Critical', 'High'])]
filtro.to_excel('resultados_filtrados.xlsx', index=False)
print("[+] Archivo resultados_filtrados.xlsx creado.")
```

✅ Resultado ➜ archivo Excel más fácil de compartir o reportar.

---

#### ✅ Analizar vulnerabilidades por puerto

✔️ Ver cuántas vulnerabilidades hay por puerto:

```python
puertos = df['Port'].value_counts()
print("\n[+] Conteo de vulnerabilidades por puerto:")
print(puertos)
```

✅ Resultado:

```
[+] Conteo de vulnerabilidades por puerto:
80     8
22     6
443    5
```

---

### 📌 Leer un archivo JSON exportado de Nessus

✅ Si exportaste en JSON, es igual de fácil:

```python
df_json = pd.read_json('resultados.json')
print(df_json.head())
```

✔️ El formato exacto depende del export de Nessus, pero pandas puede cargarlo directo si es tabla plana.

✔️ Si es anidado ➜ usa `json_normalize()` de pandas.

---

### ✅ Instalación resumida paso por paso

✔️ 1️⃣ Tener Python 3 instalado.

✔️ 2️⃣ Instalar pandas:

```
pip install pandas
```

✔️ 3️⃣ Opcional para Excel:

```
pip install openpyxl
```

✔️ 4️⃣ Opcional para gráficos:

```
pip install matplotlib
```

---

### ✅ Código completo de ejemplo

Aquí te dejo **todo listo para copiar y pegar**:

```python
import pandas as pd

# Cargar el CSV
archivo = 'resultados.csv'
df = pd.read_csv(archivo)

# Vista previa
print("\n[+] Vista previa:")
print(df.head())

# Vulnerabilidades críticas
criticas = df[df['Severity'] == 'Critical']
print("\n[+] Vulnerabilidades críticas:")
print(criticas)

# Conteo por severidad
conteo = df['Severity'].value_counts()
print("\n[+] Conteo por severidad:")
print(conteo)

# Hosts afectados
hosts = df['Host'].unique()
print("\n[+] Hosts afectados:")
for h in hosts:
    print("-", h)

# Vulnerabilidades por puerto
puertos = df['Port'].value_counts()
print("\n[+] Conteo por puerto:")
print(puertos)

# Exportar filtrado
filtro = df[df['Severity'].isin(['Critical', 'High'])]
filtro.to_excel('resultados_filtrados.xlsx', index=False)
print("\n[+] Archivo resultados_filtrados.xlsx creado.")
```

---

### ✅ Resultado esperado en consola

```
[+] Vista previa:
    Host         Port   Protocol    Severity           Plugin Name              CVE
0  192.168.1.5    22      tcp        Medium        SSH Weak Cipher          CVE-2016-0777
1  192.168.1.5    80      tcp         High        HTTP Directory Listing    CVE-2020-1234
...

[+] Vulnerabilidades críticas:
     Host         Port    Protocol    Severity       Plugin Name         CVE
2  192.168.1.10   443      tcp       Critical      TLS Vulnerability   CVE-2014-3566

[+] Conteo por severidad:
Medium      12
High         7
Critical     3
Low          1

[+] Hosts afectados:
- 192.168.1.5
- 192.168.1.10

[+] Conteo por puerto:
80     8
22     6
443    5

[+] Archivo resultados_filtrados.xlsx creado.
```

---

[🔼](#índice)

---

| **Inicio**         | **atrás 3**                                                                    | **Siguiente 5**                                                                     |
| ------------------ | ------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------- |
| [🏠](../README.md) | [⏪](./4_3_Escaneos_y_analisis_de_redes_con_Python_Hosts_Puertos_Servicios.md) | [⏩](./4_5_Python_Hacking_y_Explotacion_de_Vulnerabilidades_en_Hosts_con_Python.md) |
