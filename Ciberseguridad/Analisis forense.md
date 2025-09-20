# <p align="center">Informática forense</p>

¡Buenas! Antes de empezar con este apartado, recomiendo ver primero el apartado de **ciberseguridad: conceptos y cosas**, ya que es una introducción que te ayudará a entender mejor los conceptos de cada sección. Toda la información de estos repositorios procede del curso de especialización que he realizado en ciberseguridad; su objetivo es plasmar conocimientos y asegurarme de que permanezcan aquí por si en algún momento necesito regresar a esta información.

Dicho esto, en este apartado explico qué es la informática forense, cómo funciona y cómo se realiza un análisis forense completo. También especifico qué herramientas se usan y cómo deben emplearse.

Comenzaremos con la parte teórica (proceso y objetivos), y continuaremos con casos prácticos: veremos cómo se realizan, qué resultados aportan y cómo deben ser tratados.

> [!NOTE]
> <h3>Al final del documento se especifican 3 casos distintos con los que se realizan 3 análisis forenses distintos.</h3>

## 📑 Índice

1. [¿Qué es la informática forense?](#que-es-la-informatica-forense)  
   - [Objetivos de la informática forense](#objetivos-de-la-informatica-forense)  
   - [Identificación de evidencias digitales](#identificacion-de-evidencias-digitales)  
   - [Recopilación de evidencias](#recopilacion-de-evidencias)  
   - [Preservar la integridad de las evidencias](#preservar-la-integridad-de-las-evidencias)  
   - [Presentar un informe de conclusiones y recomendaciones](#presentar-un-informe-de-conclusiones-y-recomendaciones)

2. [Análisis de la línea de tiempo (timestamp)](#analisis-de-la-linea-de-tiempo-timestamp)

3. [Análisis de la memoria volátil](#analisis-de-la-memoria-volatil)

4. [Análisis de logs](#analisis-de-logs)  
   - [Tipos de logs y fuentes](#tipos-de-logs-y-fuentes)

5. [Herramientas y software forense](#herramientas-y-software-forense)

6. [Proceso para realizar un análisis forense](#proceso-para-realizar-un-analisis-forense)

7. [Casos prácticos](#casos-practicos)  
   - Caso 1 — Filtración de credenciales y exfiltración de base de datos  
   - Caso 2 — Ransomware en servidor de archivos  
   - Caso 3 — Compromiso por phishing y lateral movement

8. [Detalles a tener en cuenta](#detalles-a-tener-en-cuenta)

---

## ¿Qué es la informática forense?
La **informática forense** (análisis forense digital) es la disciplina enfocada en la **identificación, preservación, análisis y presentación** de evidencias digitales. Se aplica en contextos legales y en la respuesta a incidentes de seguridad de la información.

El propósito es investigar incidentes (ciberdelitos, intrusiones, fugas de datos) y obtener evidencias válidas que permitan entender qué pasó, quién pudo hacerlo y cómo mitigar o remediar la situación.

### Objetivos de la informática forense
Basándonos en la definición anterior, los objetivos principales son:

#### 1. Identificación de evidencias digitales
Determinar qué artefactos (archivos, registros, conexiones, metadatos) son relevantes para el caso y dónde se localizan.

#### 2. Recopilación de evidencias
Recolectar las evidencias de forma controlada (imágenes forenses, dumps de memoria, logs exportados) para que no se modifiquen los datos originales.

#### 3. Preservar la integridad de las evidencias
Garantizar la cadena de custodia y la integridad (hashes, bitstream copy, registro de timestamps) para que las pruebas sean admisibles en un proceso legal.

#### 4. Presentar un informe de conclusiones y recomendaciones
Elaborar un informe claro y profesional que incluya hallazgos, metodología, evidencia, conclusiones y recomendaciones técnicas y operativas.

### Partes de un informe de conclusiones (ejemplo)
1. Resumen ejecutivo.  
2. Alcance y objetivos del análisis.  
3. Metodología aplicada.  
4. Evidencias recopiladas (hashes, paths, dumps).  
5. Análisis y timeline de eventos.  
6. Conclusiones y recomendaciones.  
7. Anexos (comandos, outputs, capturas, scripts).

---

## Análisis de la línea de tiempo (timestamp)
La línea de tiempo (timeline) es fundamental: permite ordenar eventos (creación, modificación, acceso) y correlacionarlos con acciones de usuarios o procesos.  
Tareas clave:
- Extraer timestamps de archivos, registros y metadatos.  
- Normalizar zonas horarias.  
- Correlacionar con logs de red, autenticaciones y backups.  
- Detectar lagunas temporales o manipulaciones (timestamps futuros/pasados).

**Herramientas típicas:** `log2timeline/plaso`, `mactime`, `Timesketch` (para visualización).

---

## Análisis de la memoria volátil
La memoria RAM contiene procesos en ejecución, conexiones de red activas, credenciales en memoria y artefactos efímeros que no están en disco.  
Tareas:
- Hacer un volcado de memoria (dump) con herramientas forenses.  
- Analizar procesos, DLL/so libraries cargadas, sockets abiertos y credenciales en memoria.  
- Buscar rootkits o procesos inyectados.

**Herramientas típicas:** `Volatility`, `Rekall`, utilidades `winpmem`/`linux`/`mac` para adquisición.

---

## Análisis de logs
Los logs documentan eventos de sistema, aplicaciones, firewalls y dispositivos de red. Son esenciales para reconstruir la intrusión.

### Tipos de logs y fuentes
- Logs de sistema (Windows Event Logs, syslog).  
- Logs de aplicaciones (bases de datos, servidores web).  
- Logs de red (firewall, IDS/IPS, routers).  
- Logs de autenticación (Active Directory, SSH).  
- Registros de servicios en la nube (AWS CloudTrail, Azure Activity Logs).

**Buenas prácticas:** centralizar logs, retención adecuada, timestamps sincronizados y alertas configuradas.

---

## Herramientas y software forense
Listado no exhaustivo de herramientas útiles según cada fase:

- **Adquisición / imagen forense:** `FTK Imager`, `dd`, `Guymager`.  
- **Análisis de disco:** `Autopsy/Sleuth Kit`, `EnCase (propietario)`.  
- **Timeline / logs:** `log2timeline/plaso`, `Timesketch`.  
- **Memoria:** `Volatility`, `Rekall`.  
- **Network:** `Wireshark`, `Zeek`.  
- **Análisis de malware:** `Cuckoo Sandbox`, `Ghidra` (para ingeniería inversa).  
- **Integridad y hashes:** `sha256sum`, `md5sum`.  

> Nota: la elección depende del entorno (Windows/Linux/macOS), presupuesto y requisitos legales.

---

## Proceso para realizar un análisis forense
> [!IMPORTANT]  
> A partir de este punto necesitaremos conocimientos específicos y cierto control sobre las herramientas implementadas.

Pasos clave (resumen):
1. **Preparación y alcance:** definir objetivos y límites del análisis.  
2. **Adquisición:** captura de evidencias (imágenes de disco, dumps de RAM, exportación de logs) siguiendo procedimientos que preserven integridad.  
3. **Análisis:** reconstrucción de la timeline, correlación de logs, análisis de memoria y búsqueda de artefactos maliciosos.  
4. **Documentación:** registrar cada paso (quién, cuándo, cómo) y mantener hashes/metadata.  
5. **Informe:** presentar resultados, impacto, indicadores de compromiso (IOCs) y recomendaciones de mitigación.  
6. **Remediación y seguimiento:** aplicar contención, parches, restauración y monitorización continua.

### Estudiar el caso y determinar la afección
Antes de usar cualquier herramienta, clarifica:
- ¿Qué sistemas están afectados?  
- ¿Cuál es la magnitud del incidente? (uno, varios servidores, usuarios).  
- ¿Hay riesgo legal o de fuga de datos sensibles?

### Recopilar, preservar y esclarecer evidencias
- Prioriza volcado de RAM si el sistema está activo.  
- Realiza imagen forense del almacenamiento (bit-for-bit).  
- Exporta logs y guarda metadatos.  
- Genera y registra hashes antes y después del transporte de evidencias.

---

## Casos prácticos

### Caso 1 — Filtración de credenciales y exfiltración de base de datos
**Resumen:** Credenciales de un empleado se filtran por phishing; atacante accede al servidor, copia la base de datos y la borra; posteriormente exige rescate.

**Acciones forenses:**
- Revisar logs de autenticación (Windows Event Logs, syslog, proxy).  
- Extraer archivos de auditoría y backups.  
- Analizar timeline: inicio de sesión, transferencia de archivos (SFTP/FTP/DB dump), operaciones de eliminación.  
- Recuperar artefactos de red para identificar IPs y posibles C2.  
- Documentar IOCs y recomendar rotación de credenciales, restauración desde backup limpio y auditoría de accesos.

### Caso 2 — Ransomware en servidor de archivos
**Resumen:** Servidor compartido cifrado, sobrescritura de archivos y notas de rescate.

**Acciones forenses:**
- Identificar vector inicial (phishing, RDP, vulnerabilidad).  
- Aislar el host y hacer imagen forense.  
- Analizar procesos y servicios para detectar la muestra de ransomware.  
- Buscar artefactos de lateral movement y pivoteo.  
- Restaurar desde backups comprobados y fortalecer accesos/patching.

### Caso 3 — Compromiso por phishing y movimiento lateral
**Resumen:** Usuario comprometido por correo malicioso; atacante obtiene persistencia y explora la red.

**Acciones forenses:**
- Analizar correo y attachments (sandbox).  
- Buscar conexiones salientes inusuales y comunicaciones con C2.  
- Revisar logs de detección y AD para escalada de privilegios.  
- Saneamiento de cuentas comprometidas, auditoría de permisos y segmentación de red.

---

## Detalles a tener en cuenta
- Mantén siempre la **cadena de custodia** documentada.  
- No trabajes directamente sobre las evidencias originales: usa copias forenses.  
- Normaliza horas y zonas horarias al cruzar datos.  
- Prioriza adquisición de RAM en sistemas activos.  
- Coordina con el equipo legal si hay implicaciones judiciales o regulatorias.  
- Ten un plan de backups y pruebas de restauración antes de cualquier incidente.

---

## Enlaces de interés
- Guías y documentación general sobre análisis forense (PLASO / Timesketch).  
- Repositorios y cheatsheets de IOCs.  
- Foros y comunidades (DFIR Slack / Reddit / Stack Exchange).
