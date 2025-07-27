| **Inicio**         | **Siguiente 2**                                   |
| ------------------ | ------------------------------------------------- |
| [🏠](../README.md) | [⏩](./2_2_Recopilacion_pasiva_de_informacion.md) |

---

## **Índice**

| Temario                                                                                                                                |
| -------------------------------------------------------------------------------------------------------------------------------------- |
| [1. Metodologías para la realización de Hacking Ético](#1-metodologías-para-la-realización-de-hacking-ético)                           |
| [2. Ejemplos de informes de Hacking Ético y auditoría de seguridad](#2-ejemplos-de-informes-de-hacking-ético-y-auditoría-de-seguridad) |

---

# **Introduccion al hacking etico y penetration testing**

## **1. Metodologías para la realización de Hacking Ético**

### ¿Qué es una metodología de hacking ético?

Es **un conjunto de pasos ordenados y estructurados** que los profesionales de seguridad siguen para evaluar la seguridad de un sistema **de forma legal y autorizada**.

Piensa en esto como una **receta de cocina**, donde sigues pasos para obtener un resultado confiable (en este caso, un informe de vulnerabilidades y recomendaciones).

---

### ¿Por qué usar una metodología?

- Para no saltarte pasos críticos.
- Para mantener el proceso **ético y legal**.
- Para asegurar **resultados replicables y documentados**.
- Para dar confianza al cliente.

---

### Metodologías conocidas

Hay varias, pero las más populares son:

- **OSSTMM** (Open Source Security Testing Methodology Manual)
- **OWASP Testing Guide** (para aplicaciones web)
- **PTES** (Penetration Testing Execution Standard)
- **NIST SP 800-115** (Technical Guide to Information Security Testing)
- **ISSAF** (Information Systems Security Assessment Framework)

---

### Fases comunes en la mayoría de metodologías

Aunque cada metodología tiene su estilo, casi todas siguen **estas fases generales**:

---

#### ⭐ 1. Reconocimiento o “Information Gathering”

**Objetivo:** Recolectar información sobre el objetivo sin interactuar directamente (pasivo) o interactuando (activo).

✅ Ejemplo fácil:

- Buscas el sitio web de la empresa.
- Revisas redes sociales de empleados.
- Usas herramientas como **whois** para saber quién registró un dominio.

✅ Herramientas comunes:

- Google (Google Hacking)
- Whois
- Maltego
- Recon-ng

---

#### ⭐ 2. Enumeración y escaneo

**Objetivo:** Descubrir servicios, puertos abiertos, usuarios, etc.

✅ Ejemplo fácil:

- Ejecutas **nmap** para ver qué puertos están abiertos en la IP de la empresa.

✅ Herramientas:

- Nmap
- Netcat
- Nessus

---

#### ⭐ 3. Análisis de vulnerabilidades

**Objetivo:** Encontrar debilidades conocidas.

✅ Ejemplo:

- Escaneas la IP con **Nessus** o **OpenVAS** para ver si usan versiones vulnerables de software.

✅ Herramientas:

- Nessus
- OpenVAS
- Nikto (para sitios web)

---

#### ⭐ 4. Explotación

**Objetivo:** Intentar aprovechar vulnerabilidades para acceder al sistema.

✅ Ejemplo:

- Usas **Metasploit** para explotar un servicio vulnerable y obtener una shell.

✅ Herramientas:

- Metasploit
- SQLmap (para SQLi)
- Burp Suite (para web)

---

#### ⭐ 5. Post-explotación

**Objetivo:** Qué hacer una vez dentro (pivoting, escalada de privilegios, etc.).

✅ Ejemplo:

- Ya tienes acceso limitado. Buscas escalar a administrador.
- Extraes contraseñas del sistema.

✅ Herramientas:

- Mimikatz
- Meterpreter

---

#### ⭐ 6. Reporte

**Objetivo:** Documentar hallazgos y dar recomendaciones.

✅ Ejemplo:

- Creas un documento explicando:

  - Vulnerabilidad hallada.
  - Evidencia (capturas).
  - Riesgo.
  - Cómo arreglarla.

✅ Herramientas:

- Microsoft Word
- Markdown
- Dradis (colaborativo)

---

### Ejemplo práctico simplificado

Imagina que una empresa te contrata para probar su sitio web:

🎯 Objetivo: **[www.ejemplo.com](http://www.ejemplo.com)**

✅ Fase 1 (Reconocimiento):

- Google: encuentras un subdominio **dev.ejemplo.com**.
- Whois: datos de contacto.

✅ Fase 2 (Escaneo):

- Nmap: puerto 80 abierto.
- Descubres servidor Apache 2.2 (muy viejo).

✅ Fase 3 (Análisis):

- Apache 2.2 tiene vulnerabilidades conocidas.

✅ Fase 4 (Explotación):

- Usas Metasploit con módulo para Apache 2.2 → obtienes acceso.

✅ Fase 5 (Post-explotación):

- Encuentras archivos con contraseñas en el servidor.

✅ Fase 6 (Reporte):

- Entregas un informe con:

  - Evidencia del acceso.
  - Recomendación: actualizar Apache.

---

### Resumen gráfico

✅ Fases típicas:

1️⃣ Reconocimiento 🕵️

2️⃣ Escaneo/Enumeración 🔍

3️⃣ Análisis de vulnerabilidades ⚠️

4️⃣ Explotación 💥

5️⃣ Post-explotación 🏴‍☠️

6️⃣ Reporte 📑

---

### ¿Qué metodología elegir?

✅ **OSSTMM**: Muy estructurada, cubre redes, humanos, físicos.
✅ **OWASP**: Enfocada en aplicaciones web.
✅ **PTES**: Muy usada, bien detallada, práctica.

---

### En pocas palabras

> **Hacking ético no es “hackear por hackear”. Es un proceso sistemático, ético y documentado.**

---

[🔼](#índice)

---

## **2. Ejemplos de informes de Hacking Ético y auditoría de seguridad**

### ¿Qué es un informe de Hacking Ético o auditoría de seguridad?

Es un **documento profesional** que presenta de forma clara:

- Qué vulnerabilidades se encontraron.
- Cómo se explotaron.
- Qué impacto tienen.
- Y **cómo mitigarlas**.

📌 **Importancia:**
Este informe será leído por:

- Técnicos (que necesitan los detalles).
- Gerentes (que necesitan un resumen de riesgos).
- Auditores o terceros (en evaluaciones de cumplimiento).

---

### Estructura típica de un informe de hacking ético

> 🎯 Vamos a verlo con ejemplos simulados para que sea fácil de entender.

---

#### 1️⃣ Portada

Contiene:

- Nombre del informe: “Informe de Pruebas de Penetración”
- Cliente: Empresa X
- Fecha: 01/07/2025
- Consultor: Gustavo PenTester

---

#### 2️⃣ Resumen ejecutivo (para gerentes)

**👉 Explica en lenguaje no técnico** qué se hizo y qué se encontró.

##### 📌 Ejemplo:

> Durante la auditoría realizada del 24 al 28 de junio, se identificaron 6 vulnerabilidades, de las cuales 2 fueron críticas.
> La más grave permitió el acceso no autorizado al sistema administrativo mediante un fallo de SQL Injection.
> Se recomienda aplicar parches, implementar controles de acceso y revisar la seguridad de la aplicación web.

---

#### 3️⃣ Alcance

Se define **qué se evaluó y qué no** (esto es clave para delimitar responsabilidades).

##### 📌 Ejemplo:

**Sistemas evaluados:**

- Sitio web: `https://tienda.ejemplo.com`
- Servidor: `192.168.0.10`
- Aplicación interna: `http://intranet.ejemplo.local`

**Sistemas excluidos:**

- Correo electrónico corporativo
- Red WiFi de invitados

---

#### 4️⃣ Metodología utilizada

Describe **cómo se hizo la evaluación**.

##### 📌 Ejemplo:

> Se siguió la metodología PTES (Penetration Testing Execution Standard), cubriendo:

- Reconocimiento
- Escaneo y enumeración
- Análisis de vulnerabilidades
- Explotación controlada
- Post-explotación
- Reporte

Herramientas empleadas: Nmap, Burp Suite, Metasploit, Nikto.

---

#### 5️⃣ Resultados (por vulnerabilidad)

Aquí está **el corazón del informe**. Por cada hallazgo se presenta:

- Nombre de la vulnerabilidad
- Descripción
- Evidencia técnica (con capturas o comandos usados)
- Impacto (qué puede causar)
- Riesgo (bajo, medio, alto, crítico)
- Recomendación de remediación

---

##### 🎯 Ejemplo 1: Vulnerabilidad Crítica

**ID:** VULN-001
**Nombre:** SQL Injection
**Ubicación:** `https://tienda.ejemplo.com/producto?id=5`
**Descripción:** El parámetro `id` permite inyección de código SQL.
**Impacto:** Un atacante puede extraer toda la base de datos de productos y clientes.
**Evidencia:**

```
Payload usado: ' OR '1'='1
Respuesta del servidor: muestra todos los productos
```

**Riesgo:** Crítico
**Recomendación:** Usar consultas preparadas (prepared statements) y validación de entradas.

---

##### 🎯 Ejemplo 2: Vulnerabilidad Media

**ID:** VULN-004
**Nombre:** Directorio listado sin protección
**Ubicación:** `https://tienda.ejemplo.com/uploads/`
**Descripción:** El servidor permite navegar libremente por los archivos subidos.
**Impacto:** Se puede acceder a documentos confidenciales.
**Riesgo:** Medio
**Recomendación:** Desactivar el listado de directorios en Apache/Nginx.

---

#### 6️⃣ Resumen de riesgos

Una **tabla** para visualizar rápidamente los riesgos por severidad:

| Riesgo  | Cantidad |
| ------- | -------- |
| Crítico | 1        |
| Alto    | 1        |
| Medio   | 3        |
| Bajo    | 1        |

---

#### 7️⃣ Recomendaciones generales

Incluye mejoras no técnicas o estratégicas:

📌 Ejemplos:

- Implementar política de actualizaciones regulares.
- Capacitación en seguridad para desarrolladores.
- Implementar escaneos automáticos mensuales.
- Realizar una nueva auditoría en 6 meses.

---

#### 8️⃣ Anexos (opcional)

- Logs de escaneo (Nmap, Nessus, Burp)
- Capturas de pantalla
- Scripts o payloads usados (si aplica)
- Resultados completos

---

### ✅ Ejemplo completo resumido en Markdown

```markdown
# Informe de Hacking Ético – Empresa X

## Resumen Ejecutivo

Se identificaron 6 vulnerabilidades. La más grave permite extracción de base de datos por SQLi.

## Alcance

Evaluado: tienda web, servidor interno.
Excluido: correo y red WiFi.

## Metodología

Metodología PTES – herramientas: Nmap, Burp, Metasploit.

## Resultados

### VULN-001 – SQL Injection (Crítico)

- Afecta: https://tienda.ejemplo.com/producto?id=5
- Impacto: acceso a base de datos de clientes
- Evidencia: payload `' OR '1'='1` muestra todos los productos
- Recomendación: usar consultas preparadas

### VULN-004 – Directory Listing (Medio)

- Afecta: /uploads/
- Riesgo: permite ver archivos confidenciales
- Recomendación: desactivar listado en Apache

## Tabla de Riesgos

| Severidad | Total |
| --------- | ----- |
| Crítico   | 1     |
| Alto      | 1     |
| Medio     | 3     |
| Bajo      | 1     |

## Recomendaciones

- Parchear software desactualizado
- Aplicar WAF (Firewall de aplicaciones web)
- Capacitar al equipo de desarrollo
```

---

### Recursos para practicar la elaboración de informes

- [TryHackMe](https://tryhackme.com) (laboratorios con retos + informes)
- [Hack The Box](https://www.hackthebox.com/)
- OWASP Juice Shop (web vulnerable para practicar)
- Plantillas en GitHub: busca `penetration test report template`

---

### Conclusión

Un **buen informe de hacking ético**:

- Es claro y estructurado.
- Detalla lo técnico, pero también explica para no técnicos.
- Propone **soluciones prácticas**, no solo el problema.
- Sirve como base para **mejorar la seguridad** real del sistema.

---

[🔼](#índice)

---

| **Inicio**         | **Siguiente 2**                                   |
| ------------------ | ------------------------------------------------- |
| [🏠](../README.md) | [⏩](./2_2_Recopilacion_pasiva_de_informacion.md) |
