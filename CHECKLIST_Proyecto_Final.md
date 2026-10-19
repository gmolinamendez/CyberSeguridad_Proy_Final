# Checklist del Proyecto Final — Ciberseguridad ESEN 2026

Este checklist se construyó leyendo el paquete **PF_V2.2** completo: las guías, el catálogo, las 12 plantillas E01–E12, los 7 anexos BIA, la hoja de control y el ejemplo de ENSA. El documento rector es la **Guía del Estudiante del Proyecto Final** (`Docs/01_Guias/`). Si algo de este checklist choca con la guía, manda la guía.

> ⚠️ **Fechas — revisar YA.** Según el calendario oficial, **H1 (25-sep / 2-oct) y H2 (16-oct) ya vencieron**. El próximo hito es **H3, el viernes 23 de octubre**: E.05, E.06 y las versiones 1.1 de E.03, E.04 y BIA_P07. Si el equipo todavía no tiene empresa asignada, confirmen con el docente qué calendario les aplica antes de planificar.

---

## 0. Lo esencial en una página

- **Qué se construye:** la línea base de seguridad de una organización del catálogo, trabajando como firma consultora. Incluye BIA, activos, riesgos, RACI, 6 controles CIS a profundidad, baseline de las 153 salvaguardas IG3, indicadores, roadmap, documento final y defensa oral.
- **Peso:** 45 % de la nota del curso.
  - J.1, entregables E.01–E.09: 20 %
  - J.2, informe final E.10 + E.11: 15 %
  - J.3, defensa E.12: 10 %
- **Esfuerzo medido por la cátedra:** 179 horas de equipo, unas 30 por persona. El pico cae en S6–S7 (E.07 + E.08).
- **Marcos:**
  - CIS Controls v8.1 (2024), con 18 controles y 153 salvaguardas
  - ISO/IEC 27001:2022 y 27002:2022
  - NIST SP 800-30 r1 (riesgo)
  - NIST CSF 2.0 (2024)
  - ISO 22301:2019 + ISO/TS 22317:2021 (BIA)
  - NIST SP 800-34 r1
  - Ciclo PDCA
  - LPDP, D.L. 144/2024, art. 25: notificar en 72 h
  - Ley de Ciberseguridad, D.L. 143/2024, según el ámbito de su art. 2
  - PCI DSS v4.0.1, solo si la ficha declara pagos con tarjeta
- **Las 27 organizaciones son IG3**, así que el baseline siempre son las **153 salvaguardas** (56 IG1 + 74 IG2 + 23 IG3).
- **Cadena obligatoria:** BIA (E.03) → activos (E.04) → riesgos (E.05) → RACI (E.06) → 6 controles (E.07) → baseline (E.08) → indicadores (E.09) → roadmap (E.10) → documento final (E.11) → defensa (E.12).

### Reglas de oro (se evalúan en TODOS los entregables)

- [ ] **El perfil y la ficha de datos del cliente se usan tal como están escritos.** Un dato que trae la ficha **nunca** se reemplaza por un supuesto.
- [ ] Solo lo que ni el perfil ni la ficha traen se declara como **supuesto**, con ID **global y correlativo** (S-01, S-02…) y su fundamento. Cada entregable continúa la numeración del anterior, y E.11 los consolida en el Anexo A.
- [ ] Toda plantilla E01–E10 cierra con la sección **«Supuestos declarados en este entregable»**. Si no hay supuestos, la primera fila lo dice.
- [ ] **Las plantillas no se rediseñan, se llenan:** se conservan los encabezados y se reemplazan las filas «(p. ej.)».
- [ ] **Toda cifra lleva fuente o supuesto.**
- [ ] **Adaptación real a la organización.** El material genérico sin adaptar se califica como **ausente**.
- [ ] **No copiar cifras de RHM ni de ENSA.** Son solo ejemplos de formato.
- [ ] **Política ≠ SOP.** La política dice el qué y el porqué; el SOP dice el cómo, quién y con qué frecuencia.
- [ ] Se puede usar IA, pero **cada integrante debe poder defender todo**. En la defensa preguntan a cualquiera sobre cualquier parte.
- [ ] Antes de subir cada entregable, el oficial de calidad **corre el checklist de cierre**. Con una casilla sin marcar, no se sube.
- [ ] Se sube a Moodle con el **nombre normalizado** de cada ficha.
- [ ] La **retroalimentación de cada hito** se incorpora antes de pasar el contenido a E.11 y se registra en el Anexo B.

---

## 1. Elección de empresa (si aún no está asignada)

Las organizaciones **libres** según el registro de asignaciones son las n.º 2, 4, 6, 7, 8, 9, 11, 15, 16, 17, 18, 20, 21, 22, 25 y 27. El grupo 8 (Cuartel General) aparece sin empresa.

La comparación sale de los datos del catálogo. Los factores que más trabajo agregan son:

- **OT/IoT/SCADA:** exige separar TI y OT en E.08 y activa el eje OT en E.05.
- **Pagos con tarjeta:** trae PCI DSS como requisito adicional.
- **Número de procesos críticos:** cada proceso crítico lleva BIA_P02 + P03 + P04 completos.

| N.º | Organización | Proc. críticos (perfil) | OT/IoT en el perfil | Tarjeta/PCI | Comentario |
|---|---|---|---|---|---|
| **22** | **Express Logistics International (ELI)** | 4 | No | No | Stack claro (TMS/WMS Manhattan, aduanal propio, portal en Azure). Brechas evidentes: inyección en el sistema aduanal, auth débil del portal, sin plan de incidentes. **Ninguna de las tres complicaciones** |
| **16** | **Capitalia Gestores de Patrimonio** | 4 | No | No | La más pequeña (280 empleados). Madurez intermedia-baja, con varios controles que ya existen (MFA en M365, Aladdin) que facilitan los estados de E.08. Agrega regulación SSF y lavado de dinero |
| **20** | **Constructora Horizonte** | 4 | IoT ligero (telemetría de maquinaria vía portales del fabricante) | No | Ficha muy concreta, con incidentes reales (BEC 2023, ransomware 2025) que sirven para justificar P e I. Versiones viejas de software (Win Server 2016, Project Server 2016) obligan a registrar hallazgos de fin de soporte en E.07 |
| 25 | CrediRápido | 4 | No | Sí (vía procesador) | 100 % GCP/Kubernetes: muy técnico. APIs y modelo de scoring |
| 8 | Aseguradora Confianza Total | **5** | No | Sí | Un proceso crítico más que las otras, y PCI |
| 9 | MerdiCA | 4 | No | Sí | Perfil largo y complejo (e-commerce + fintech) |
| 2 | RHM | 4 | IoMT | No | Es el ejemplo de la Guía. Cuidado con parecer copia |
| 4 | ENSA | 4 | **SCADA/OT** | Sí | Es el **proyecto ejemplo completo**. Las guías no lo prohíben explícitamente, pero el riesgo de "copia" es alto. Si les interesa, **consultar al docente** |
| 6, 11, 18, 21, 27 | LogiPort, AESA, GeoExplora, CENAZU, Genómica | 3–4 | OT/PLC/SCADA/DCS | Varía | Más trabajo, porque mezclan TI y OT |
| 7, 15, 17 | Innovatec, ALACA, CJDES | 4 | Varía | Varía | Regulación sectorial pesada (BPM, aviación, justicia) |

**Recomendación:** en orden, **ELI (22) → Capitalia (16) → Constructora Horizonte (20)**. Esto es juicio sobre la carga de trabajo, no una regla de la cátedra. Antes de decidir, lean completos sus tres perfiles y fichas en el catálogo (secciones 4.22, 4.16 y 4.20).

- [ ] Leer el perfil **y la ficha completa** de las 3 candidatas. La ficha incluye Economía, Operación por proceso, Tecnología, Respaldos, Incidentes, Organización y presupuesto, y Controles que ya existen.
- [ ] Registrar las 3 preferencias en el aula virtual. La primera solicitud válida bloquea la organización para los demás.
- [ ] Confirmar la asignación con el docente.

---

## 2. Arranque del equipo

- [ ] Leer la **Guía rápida** y la **Guía del Estudiante del Proyecto Final**, como mínimo las secciones 1–8 y el **Anexo J** (rúbrica).
- [ ] Equipo de **6 integrantes** con los **5 roles**:
  - [ ] **Consultor líder:** plan, cronograma, relación con el docente, consolida decisiones.
  - [ ] **Analista de riesgos:** BIA (E.03), activos (E.04), riesgos (E.05).
  - [ ] **Arquitecto de controles:** E.07, E.08, E.09 y roadmap.
  - [ ] **Oficial de documentación:** redacción, consistencia, ensamblaje de E.11, versiones.
  - [ ] **Oficial de calidad:** corre los checklists de cierre y audita la trazabilidad riesgo → control → indicador.
  - [ ] Dos integrantes **comparten** el rol de analista de riesgos o el de arquitecto de controles, con un **responsable declarado** en el acta.
- [ ] Imprimir o llenar la **hoja de control** (`Docs/05_Control_Entregables/`): equipo, organización, IG, integrantes, responsable por entregable y V.º B.º.
- [ ] Definir el día y la hora de la **reunión semanal** del equipo y de la **asesoría semanal** (30 min) con el docente.
- [ ] Definir el **repositorio de trabajo** y el control de versiones.
- [ ] Llevar un **registro maestro de supuestos** (hoja compartida S-01, S-02…) desde el día 1, para no romper la numeración global.
- [ ] Llevar un **registro de IDs**: procesos P-nn, activos A-nn, riesgos R-nn, escenarios SLE-nn, supuestos S-nn.
- [ ] Hojear el **proyecto ejemplo ENSA** (`Docs/06_Proyecto_Ejemplo_ENSA/`) para calibrar el formato y la extensión. Como referencia, ENSA tuvo:
  - un censo de 10 procesos, de los cuales 2 salieron críticos
  - unos 24 activos, 14 riesgos, 6 escenarios SLE y 17 supuestos
  - un documento final de 66 páginas

---

## 3. Checklist por entregable

### E.01 — Acta de equipo y selección de empresa · H1 · J.1.1 (1 %) · ~2 h
Plantilla: `E01_Acta_Equipo_Seleccion_Empresa.docx` · Moodle: `E01_Acta_Equipo_Seleccion_Empresa_<Equipo>.docx/.pdf`
Fechas: v1.0 el **viernes 25-sep**; v1.1 (con la organización asignada) el **viernes 2-oct**, junto con E.02.

- [ ] Llenar la tabla de identificación del equipo: equipo, organización, IG, integrantes, fecha y versión.
- [ ] Llenar la tabla de integrantes: nombre, **carné**, **correo institucional** y rol. Los 5 roles deben estar cubiertos.
- [ ] Registrar las 3 preferencias con **n.º de catálogo, nombre e IG**, en orden.
- [ ] Declarar **3–4 criterios** de orden y cómo se aplicaron a cada opción. Por ejemplo: afinidad con el sector, lo que la ficha anticipa (procesos, sistemas, datos personales, tarjeta), madurez actual e interés profesional.
- [ ] Escribir un **párrafo de justificación** del orden.
- [ ] **v1.1:** organización asignada, n.º, IG, fecha de asignación (registro del lunes 28-sep) y, si aplica, autorización para compartir organización.
- [ ] Llenar el plan de trabajo: responsable de cada entregable E.01–E.12 y fecha de revisión del oficial de calidad.
- [ ] Marcar las **4 casillas de compromiso**: perfil y ficha fijos, baseline hacia el IG asignado, dominio completo de cada integrante y conocimiento del calendario y la rúbrica.
- [ ] Firmas y fecha de todos.
- [ ] Sección de supuestos (aunque sea «sin supuestos»).
- [ ] **Checklist de cierre de la guía:** acta completa con carné, correo y rol · 3 preferencias con n.º e IG correctos + criterios + párrafo · v1.1 con la organización asignada entregada con E.02 · compromisos marcados y firmas · v1.0 entregada el 25-sep.

### E.02 — Compromiso de la dirección y alcance del SGSI · H1 · J.1.2 (2 %) · ~6 h
Plantilla: `E02_Compromiso_Direccion_Alcance_SGSI.docx` · Moodle: `E02_Compromiso_Direccion_Alcance_SGSI_<Equipo>.docx/.pdf` · **2–3 páginas**
Fechas: v1.0 el **viernes 2-oct**; **v1.1 (sección A.3)** junto con E.03 el **viernes 16-oct**.
Fundamento: ISO/IEC 27001:2022, cláusulas 4 y 5; función Gobernar de CSF 2.0.

**A.1 Declaración de compromiso.** Se redacta en prosa completa en la 2.ª columna, reemplazando la descripción de la plantilla.
- [ ] **Encabezado:** organización, fecha y firmantes simulados (dirección general y responsable de seguridad).
- [ ] **Contexto del negocio** en 3–5 líneas: misión, procesos que generan ingresos y dependencia tecnológica, sacados del perfil y la ficha.
- [ ] **Organigrama** tomado de la fila «Organigrama» del bloque «Organización y presupuesto» de la ficha, con Legal, Auditoría y RR. HH. donde la ficha los ubica.
  - [ ] Si no existe una función de seguridad, **crearla como supuesto** (unidad y cargo). Se usa como firmante aquí y como rol en E.06.
- [ ] **Declaración de compromiso** en primera persona institucional: seguridad como prioridad, recursos y autoridad asignados, adopción de **CIS Controls v8.1 (2024) e ISO/IEC 27001:2022**.
- [ ] **3–5 objetivos de seguridad medibles**, cada uno con verbo, meta, proceso del perfil y **fecha absoluta** contada desde el arranque del **lunes 4-ene-2027**. Ejemplo: «al 30 de junio de 2027». Nada de «en seis meses».
- [ ] **Compromisos concretos:** presupuesto por año (inversión y operación) y personal **copiados tal cual** de la ficha, más la frecuencia de revisión por la dirección y el apoyo al PDCA.

**A.2 Alcance del SGSI**
- [ ] **Procesos cubiertos**, con el nombre exacto del catálogo. Los procesos críticos del perfil son el mínimo.
- [ ] Unidades y sedes.
- [ ] Sistemas e infraestructura, del perfil.
- [ ] **Exclusiones justificadas**, una línea por exclusión. Un alcance sin exclusiones se considera error.
- [ ] **Partes interesadas y requisitos:**
  - [ ] Clientes, reguladores y terceros.
  - [ ] Normas de la fila «Cumplimiento que el cliente reconoce» de la ficha.
  - [ ] **LPDP (D.L. 144/2024), art. 25:** notificación en **72 h** a la **Agencia de Ciberseguridad del Estado**, la **Fiscalía General de la República** y los **titulares afectados**.
  - [ ] **Ley de Ciberseguridad (D.L. 143/2024)** con su nota de ámbito (art. 2). Si la organización es privada y presta un servicio esencial, se registra «sujeto a calificación como operador de infraestructura crítica» (art. 8 f).
  - [ ] Si es una entidad pública, aplica el Título III de la LPDP (art. 2). Si opera un registro público o el DUI, aplica la exclusión del art. 3 d).
  - [ ] Una norma sectorial que no esté en el perfil ni en la ficha se declara como supuesto.

**A.3 Revisión del alcance tras el BIA (v1.1)**
- [ ] Una fila por cada diferencia entre los procesos cubiertos y la clase que asigna BIA_P05, con la decisión (mantener o ajustar) y su justificación.

- [ ] **Checklist de cierre:** marcos + autoridad + recursos de la ficha + frecuencia de revisión · 3–5 objetivos medibles con fecha absoluta · alcance con los nombres del catálogo · exclusiones justificadas · LPDP art. 25 + Ley de Ciberseguridad · v1.1 con A.3.

### E.03 — BIA: procesos críticos y consolidación (+ BIA_P01–P07) · H2 · J.1.3 (3 %) · ~38 h
Plantilla: `E03_BIA_Consolidacion_Procesos_Criticos.docx` + los 7 anexos de `Docs/04_Anexos_BIA/` · Moodle: `E03_BIA_Consolidacion_Procesos_Criticos_<Equipo>.docx/.pdf` (**un solo envío con los 7 anexos**)
Fechas: **viernes 16-oct**. La **v1.1** (B.4 con los IDs de riesgo y BIA_P07, secciones 8–11) va con E.05 el **viernes 23-oct**.
Método: **Guía del Estudiante del BIA**, 13 pasos. **ARO/ALE/ROSI NO van aquí**; van en E.05.

> El tiempo se va sobre todo en BIA_P02 (~10 h) y BIA_P03 (~6 h). Las entrevistas son **simuladas**: las respuestas del dueño del proceso se toman del bloque «Operación por proceso» de la ficha (horario, personal, alterno, penalizaciones y consecuencias en los 5 cortes).

**BIA_P01 — Inventario de procesos (pasos 1–2)**
- [ ] Identificación: empresa, sector y tamaño, equipo, analista y fecha.
- [ ] Censo de procesos, **nombrados con verbo + objeto** (procesos, no sistemas). Los críticos del perfil son el mínimo, más los procesos de **soporte** que los alimentan.
- [ ] Por proceso: área, dueño (nombre y cargo), servicio que entrega, destinatario, sistemas de soporte y ventana de operación.
- [ ] Sección 4: alcance y **exclusiones declaradas**.

**BIA_P05 — Precalificación y priorización (paso 7). Se hace temprano porque decide qué procesos llevan ficha completa.**
- [ ] **Pesos** de las 5 categorías (financiero, operativo, legal/regulatorio, reputacional, seguridad de las personas). Deben **sumar 100 %**, con su fundamento y la aprobación de la dirección simulada.
- [ ] Línea «Corte de tiempo»: **24 h** por convención, o una regla alternativa (cada proceso en su propio MTPD) con justificación.
- [ ] Precalificar **todo el censo** en el corte de 24 h con las consecuencias que trae la ficha.
- [ ] Puntaje = suma ponderada × (1 + 0,10 × n.º de procesos dependientes), redondeado a 2 decimales con la mitad hacia arriba. Va en la línea «Ajuste por dependientes».
- [ ] Sección 5: **rangos de clase** declarados (crítico / importante / diferible) y qué implican.
- [ ] Sección 6: **lista única ordenada**, con MTPD, RTO, WRT y RPO.
- [ ] Sección 7: enganche con CSF 2.0 y CIS v8.1.
- [ ] Todo proceso que cambie de clase después de BIA_P03 se declara.
- [ ] Un proceso crítico por **confidencialidad** que puntúe bajo **conserva su clase**. La criticidad por confidencialidad va como **brecha** en BIA_P06 y E.05 la trata como riesgo.

**BIA_P02 — Ficha por proceso (pasos 3–5, 8, 11). Una por cada proceso CRÍTICO.**
- [ ] Sección 2: método de levantamiento (entrevista, cuestionario, taller, revisión documental, validación del dueño, aprobación de la dirección).
- [ ] Sección 3: identificación del proceso.
- [ ] Sección 4: **MTPD (lo fija el negocio), RTO, WRT, RPO y MBCO.**
  - [ ] Comprobar **RTO + WRT ≤ MTPD**. Si no se cumple, la ficha no avanza y se corrige.
- [ ] Sección 5: MBCO en términos verificables (qué se atiende, con qué volumen y con qué personal).
- [ ] Sección 6: **períodos pico** y factor de agravamiento. Se valora el peor escenario temporal.
- [ ] Sección 7: **procedimiento alterno**, quién lo ejecuta, recursos, **duración máxima sostenible**, cómo se verificó y esfuerzo de reconstrucción (alimenta el WRT).
- [ ] Sección 8: **costo por hora y por día**: ingresos no percibidos, personal improductivo u horas extra, penalizaciones, costo del alterno y otros. Usar el costo cargado por hora y el personal de la ficha.
- [ ] Sección 9: **AV, EF y SLE = AV × EF**, con un **SLE-nn por escenario** (cifrado o indisponibilidad, exposición de datos, fraude, sabotaje).
  - [ ] SLE de **exposición de datos**: AV = titulares de la ficha × (costo de notificar + otros costos por titular), y EF = proporción de titulares expuestos.
- [ ] Sección 10: **método de valoración** (cuantitativo, cualitativo o semicuantitativo) con su justificación.
- [ ] Sección 11: validación con firmas simuladas.
- [ ] Un proceso **importante** que trata los datos personales que cuantifica la ficha lleva **además** las secciones 3, 8 y 9.

**BIA_P03 — Matriz de impacto × tiempo (paso 4). Una por proceso crítico.**
- [ ] Anotar las **ventas o ingresos anuales de la ficha** y calcular los límites en USD de la escala (porcentajes fijos de la plantilla):
  - nivel 1: <0,01 %
  - nivel 2: 0,01–0,05 %
  - nivel 3: 0,05–0,25 %
  - nivel 4: 0,25–1 %
  - nivel 5: >1 %
- [ ] Escribir el criterio verbal de cada nivel para las otras 4 categorías. Si los dos criterios difieren, gana el mayor.
- [ ] Llenar la matriz de **5 categorías × 5 cortes** (4 h, 24 h, 72 h, 1 semana, 1 mes) y el impacto consolidado de cada corte (el máximo).
- [ ] Declarar el **umbral de tolerancia** antes de ver la matriz, con quién lo aprueba y la fecha.
- [ ] Registrar el primer corte que cruza el umbral, la categoría que lo cruza, el **MTPD derivado** frente al **declarado** y la explicación de la diferencia.
- [ ] Describir el **punto de inflexión** de la curva y el mecanismo que lo explica.

**BIA_P04 — Dependencias y recursos (paso 6). Una por proceso crítico.**
- [ ] Las **6 clases**, con al menos una fila por clase:
  - personas y competencias
  - aplicaciones y sistemas
  - datos y registros vitales
  - proveedores y terceros
  - instalaciones
  - equipamiento y servicios básicos
- [ ] Por dependencia: recurso mínimo en el MBCO, **SPOF sí/no**, alternativa y observaciones.
- [ ] Recursos mínimos consolidados, operación normal frente a MBCO: personas, estaciones, red, instalación, aplicaciones y datos, insumos.
- [ ] Interdependencias entre procesos (quién alimenta a quién).
- [ ] Secuencia de recuperación propuesta.

**BIA_P06 — Supuestos, SPOF y brechas (pasos 6, 11, 12)**
- [ ] Registro de supuestos con ID **S-nn global**, valor, origen y fecha, y escenarios **mínimo / esperado / máximo** para **AV y EF**. El ARO se varía en E.05.
- [ ] Identificar las variables que gobiernan la conclusión.
- [ ] **Al menos 2 puntos únicos de falla**, con proceso, consecuencia, alternativa y prioridad.
- [ ] Brechas, con su evidencia, el control propuesto y la referencia CIS v8.1 o CSF 2.0.
- [ ] (Opcional) Sección FAIR con rangos.

**BIA_P07 — Informe ejecutivo (pasos 8, 13)**
- [ ] 2 Resumen ejecutivo (máximo 1 página): exposición en $ por tiempo, tolerancia, hallazgos y recomendación.
- [ ] 3 Alcance y método.
- [ ] 4 Procesos priorizados con sus métricas y la comprobación RTO+WRT≤MTPD («fichas que la superan: x de y»).
- [ ] 5 Costo de indisponibilidad: por hora, por día y **al alcanzar el MTPD**.
- [ ] 6 SPOF y brechas que exigen decisión.
- [ ] 7 Frontera con el análisis de riesgos (ARO y ALE van en E.05).
- [ ] 8–11 **Marcar «se completa en E.05»** en H2. Se llenan en la v1.1:
  - 8: 5 pasos
  - 9: ACC en 3 familias
  - 10: ROSI
  - 11: sensibilidad
- [ ] 12 Recomendaciones y decisión solicitada.
- [ ] 13 Aprobación.

**E03 — Hoja de consolidación**
- [ ] **B.1** Proceso, dueño, puntaje, clase, MTPD, RTO, WRT, RPO y MBCO, **ordenado por puntaje**, con RTO+WRT≤MTPD en cada fila.
- [ ] **B.2** Una fila por proceso y escenario (SLE-nn): costo por hora y por día con sus componentes, AV, EF, SLE y método. Va para cada crítico y para cada importante con datos personales de la ficha.
- [ ] **B.3** Períodos pico, alterno, duración máxima sostenible y recurso mínimo.
- [ ] **B.4** Cada SPOF de BIA_P06 con su clase de dependencia. El **ID de riesgo** se completa en la v1.1.
- [ ] **B.5** Supuestos de AV/EF/costo en 3 escenarios, con la variable que gobierna.
- [ ] Supuestos del entregable, con el mismo S-nn que BIA_P06.
- [ ] **Checklist de cierre:** P01–P07 completos y adjuntos · 5 categorías × 5 cortes · todo el censo en P05 · cada crítico con P02+P03+P04 · B.1 ordenada · B.2 con SLE por escenario · B.4 con todos los SPOF · B.5 en 3 escenarios · P07 con las secciones 8–11 marcadas · v1.1 con E.05.

### E.04 — Inventario y clasificación de activos críticos · H2 · J.1.4 (2 %) · ~6 h
Plantilla: `E04_Inventario_Clasificacion_Activos.docx` · Moodle: `E04_Inventario_Clasificacion_Activos_<Equipo>.docx/.pdf`
Fechas: **viernes 16-oct**. **v1.1** (columna 8 con los riesgos) con E.05 el **viernes 23-oct**.
Fundamento: CIS v8.1, controles 1, 2 y 3.

- [ ] Tomar cada proceso **crítico** de E.03, más cada **importante con datos personales o con un SPOF**, y listar sus activos desde BIA_P04. La orientación es **12–20 activos**.
- [ ] **ID A-nn** correlativo. No se cambia después.
- [ ] Nombre **concreto**: sistema, equipo, contrato, rol o sede. Nada genérico.
- [ ] Categoría, una de 7: información, software, hardware, servicios, personas clave, instalaciones, identidades y cuentas.
- [ ] Proceso que sostiene, con el nombre exacto de E.03.
- [ ] **Dueño:** un rol del organigrama de la ficha. **No poner «TI» como dueño de todo.**
- [ ] Clasificación: pública / interna / confidencial / restringida.
- [ ] Datos personales sí/no. Un **«Sí» obliga a confidencial o restringida** y a marcarlo bajo la LPDP.
- [ ] **Regla de calidad:** cada proceso tiene ≥1 activo de **información**, ≥1 de **plataforma** (software o hardware) y ≥1 de **personas o terceros**.
- [ ] **Columna 8** (en la v1.1): los IDs de riesgo de E.05 de cada activo, o una justificación de su ausencia.
- [ ] **Checklist de cierre:** regla de las 3 categorías por proceso · todos con ID, categoría, proceso, dueño y clasificación · datos personales ≥ confidencial · cada activo aparece en E.05 o trae su justificación (v1.1).

### E.05 — Matriz de riesgos · H3 · J.1.5 (4 %, el entregable parcial que más pesa) · ~20 h
Plantilla: `E05_Matriz_Riesgos.docx` · Moodle: `E05_Matriz_Riesgos_<Equipo>.docx/.pdf` · **viernes 23-oct**
Fundamento: NIST SP 800-30 r1.

- [ ] **D.4-bis Apetito de riesgo**, escrito y **firmado** por la dirección simulada. Ejemplo: «ningún Crítico o Alto sin tratamiento; residual máximo Medio».
- [ ] Por cada activo de E.04, listar amenazas plausibles del sector y del perfil.
- [ ] **Ejes de amenaza del curso**: al menos **1 riesgo por eje activo**, y una línea con los que **no aplican**.
  - IA
  - identidad (aplica a todos)
  - nube
  - terceros y cadena de suministro (aplica a todos)
  - OT
- [ ] **Cada SPOF de E.03** aparece como vulnerabilidad de al menos un riesgo.
- [ ] **D.5 Registro**, **mínimo 12 riesgos** y no todos en el mismo nivel. Cada fila lleva:
  - ID R-nn
  - activo (ID y nombre)
  - amenaza concreta
  - vulnerabilidad concreta del perfil
  - P e I del 1 al 5, con escalas D.1 y D.2 y una línea de justificación
- [ ] El impacto se sustenta con el **MTPD y el costo por hora** del BIA.
- [ ] Inherente = P × I, clasificado como Crítico 17–25 · Alto 10–16 · Medio 5–9 · Bajo 1–4.
- [ ] Tratamiento: mitigar / transferir / evitar / aceptar. **«Aceptar» requiere la firma de la dirección.**
- [ ] **Control CIS asociado** cuando el tratamiento es mitigar. Si no hay salvaguarda CIS aplicable (personas o proveedores), se cita **ISO/IEC 27002:2022** y se declara.
- [ ] Residual: P×I esperado **dentro del apetito**. **No puede ser igual al inherente si el tratamiento es mitigar.**
- [ ] **D.5-bis Mapa de calor 5×5**, con **cada ID en su celda**.
- [ ] **D.6 Cuantificación** de los **Críticos**. Si hay menos de 3 Críticos, también los **Altos de 15–16**:
  - [ ] SLE de E.03 (B.2), citado con su **SLE-nn**.
  - [ ] **ARO** con la convención 5≈1 · 4≈0,5 · 3≈0,2 · 2≈0,1 · 1≈0,05, o con una fuente citada.
  - [ ] ALE actual = SLE × ARO.
  - [ ] Efectividad: reducción de **al menos un nivel** de P o del EF, justificada.
  - [ ] ALE con control, y **beneficio** = ALE actual − ALE con control.
  - [ ] **ACC** en 3 familias: adquisición anualizada a **5 años**, operación y mantenimiento.
  - [ ] **ROSI = (Beneficio − ACC) ÷ ACC**. El control se justifica si ACC < la reducción del ALE.
  - [ ] Los ALE **no se suman** entre riesgos del mismo proceso; se toma el mayor.
  - [ ] Si el ROSI sale de cientos de %, revisar el SLE, el ARO y el ACC antes de aceptarlo.
- [ ] **D.7 Sensibilidad del ARO** (mínimo / esperado / máximo): ALE, beneficio y si el control **se justifica en los 3 escenarios**.
- [ ] **Volver a E.03 y E.04:** IDs de riesgo en B.4 y en la columna 8 de E.04.
- [ ] **Entregar junto con E.05 (23-oct):**
  - [ ] **E.03 v1.1**
  - [ ] **E.04 v1.1**
  - [ ] **BIA_P07 v1.1** (secciones 8–11 completas con los números de D.6 y D.7)
- [ ] **Checklist de cierre:** ≥12 riesgos con P e I justificados · todos los SPOF como vulnerabilidad · ejes de amenaza + nota de los que no aplican · inherente, tratamiento, control y residual dentro del apetito · D.6 completa · mapa de calor, apetito firmado y D.7.

### E.06 — Matriz RACI · H3 · J.1.6 (1 %) · ~5 h
Plantilla: `E06_Matriz_RACI.docx` · Moodle: `E06_Matriz_RACI_<Equipo>.docx/.pdf` · **viernes 23-oct**

- [ ] Reemplazar las columnas genéricas por **roles reales del organigrama** de la ficha, más las funciones creadas como supuesto en E.02 (por ejemplo, el responsable de seguridad).
- [ ] Ubicar RR. HH., Legal y Auditoría bajo la unidad que declare el equipo. Si una función no existe, decir quién la asume o que se contrata fuera, con una línea de justificación.
- [ ] Conservar y adaptar las **8 actividades base**:
  - aprobar la política
  - vulnerabilidades y parches
  - cuentas y accesos
  - respaldos
  - incidentes
  - notificar brechas en 72 h (LPDP)
  - concientización
  - auditoría interna
- [ ] **Agregar las actividades propias del sector** y las que exigen los **tratamientos de E.05**.
- [ ] **Exactamente una A por fila** y **al menos una R**. C e I según corresponda.
- [ ] La dirección y el responsable de seguridad deben ser coherentes con E.02.
- [ ] **Checklist de cierre:** 1 A y ≥1 R por fila · columnas = organigrama o supuestos de E.02 · actividades del sector y de E.05 agregadas.

### E.07 — Seis controles a profundidad (política + SOP + controles) · H4 · J.1.7 (3 %) · ~42 h (~7 por control)
Plantilla: `E07_Desarrollo_Control_CIS.docx` (**6 archivos**, uno por control) · Moodle: `E07_Desarrollo_Control_CIS_<Control>_<Equipo>.docx/.pdf` · **viernes 30-oct** · **3–5 páginas de desarrollo por control** (F.1–F.4)

**Selección (paso previo)**
- [ ] Listar los controles CIS de la columna «Control CIS asociado» de los riesgos **Críticos y Altos**, y contar cuántos riesgos cubre cada uno.
- [ ] Elegir los 6 que más riesgo reducen. Si hay empate, desempatar en este orden:
  1. cubre un Crítico
  2. mayor suma de inherentes
  3. mayor SLE
  4. cubre un riesgo que ningún otro trata
  5. implementa el tratamiento de D.6
- [ ] **F.0**: tabla de los 6 controles con los riesgos (IDs) que cubre cada uno y el criterio que decidió su lugar. **Va idéntica en los 6 archivos.**
- [ ] Verificar que **cada Crítico y cada Alto** quede cubierto por uno de los 6, o por una salvaguarda de E.08, o por un control ISO 27002 de E.05 con su iniciativa en la tabla I.3 de E.10.

**Por cada uno de los 6 controles**
- [ ] **F.1 Identificación:**
  - [ ] Número y nombre oficial del control (v8.1).
  - [ ] **TODAS las salvaguardas IG3** del control (tomadas de la tabla G.2 de E08), cada una marcada «diseñada ahora» o «al roadmap».
  - [ ] Riesgos que mitiga (IDs R-nn).
  - [ ] Controles ISO/IEC 27002:2022 relacionados (por ejemplo 8.20, 8.22).
  - [ ] **Una** función CSF 2.0.
- [ ] **F.2 Política:**
  - [ ] Propósito anclado a los riesgos.
  - [ ] Alcance.
  - [ ] **Declaraciones numeradas y verificables**, sin «se procurará».
  - [ ] Roles coherentes con **E.06**.
  - [ ] Cumplimiento y excepciones.
  - [ ] Revisión (frecuencia y dueño).
- [ ] **F.3 SOP:**
  - [ ] Objetivo y disparador.
  - [ ] Responsable y frecuencia.
  - [ ] **Pasos numerados con herramienta y criterio de decisión.**
  - [ ] **Evidencia generada**: es la fuente del indicador de E.09.
  - [ ] Escalamiento.
- [ ] **F.4 Controles por tipo**, de **2 a 4** técnicos, 2 a 4 administrativos y 2 a 4 físicos (donde aplique):
  - [ ] Los técnicos usan la pila del bloque **«Tecnología»** de la ficha y citan el **CIS Benchmark** del producto **en la versión declarada**. Si esa versión no existe, se usa la más cercana y se declara. Si no hay Benchmark, se usa la guía de hardening del fabricante y se declara.
  - [ ] Una versión **sin soporte del fabricante** se registra como **hallazgo** (producto, versión, fecha de fin de soporte y fuente del fabricante) y pasa a E.10 como iniciativa.
- [ ] Supuestos del entregable.
- [ ] **Checklist de cierre:** 6 controles justificados con IDs de Críticos/Altos · F.1 completo · políticas verificables con roles de E.06 · SOP con pasos, responsable, frecuencia, evidencia y escalamiento · 2–4 controles por tipo, con Benchmarks y hallazgos de fin de soporte.

> 💡 Arrancar el **ensamblaje parcial de E.11 (secciones 1–7) en la S6**, en paralelo a E.07 (~9 h). Lo recomienda la cátedra para descargar la S8.

### E.08 — Baseline IG3 (153 salvaguardas) · H4 · J.1.8 (3 %)
Plantilla: `E08_Checklist_Baseline_IG.docx` (la tabla G.2 viene **pre-poblada con las 153**) · Moodle: `E08_Checklist_Baseline_IG_<Equipo>.docx/.pdf` (también se acepta XLSX con la misma estructura) · **viernes 6-nov**

- [ ] **Repartir** los 12 controles restantes entre los integrantes (5–7 h de equipo). El oficial de calidad revisa el conjunto.
- [ ] **Eliminar las filas de los 6 controles de E.07**, que quedan documentadas en su F.1.
- [ ] **Comprobar el conteo:** IG1 de E.08 + IG1 de las 6 F.1 = **56**, y el total de E.08 + F.1 = **153**.
  - Referencia por control: 1(5) · 2(7) · 3(14) · 4(12) · 5(6) · 6(8) · 7(7) · 8(12) · 9(7) · 10(7) · 11(5) · 12(8) · 13(11) · 14(9) · 15(7) · 16(14) · 17(9) · 18(5).
- [ ] Por cada salvaguarda restante:
  - [ ] **Medida concreta** para el perfil, en una línea. Si varias salvaguardas usan la misma medida, se escribe una vez y las demás la referencian.
  - [ ] **Estado**, un solo valor de cinco:
    - **existente** o **existente parcial**: **SOLO** si la medida está en el bloque «Controles que ya existen» de la ficha. En el parcial se declara la brecha, que pasa a E.10.
    - **cubierta por tercero**: solo con contrato vigente, nombrando al **proveedor**, la **cláusula contractual** y la **evidencia** que entrega. Si la cláusula no está firmada, el estado es «por implementar» y la medida es la cláusula propuesta.
    - **por implementar**.
    - **al roadmap**: solo lo que las dependencias impiden implantar en el corto plazo.
  - [ ] **Evidencia esperada**: el registro, reporte o configuración que probará la salvaguarda.
  - [ ] En perfiles con OT, la medida distingue **TI y OT**.
- [ ] Que haya **cero «existentes»** es válido si la ficha no trae controles.
- [ ] **No mandar todo «al roadmap»** para evitar diseñar medidas.
- [ ] **Resumen por estado**: conteo de existentes, parciales, de tercero, por implementar y al roadmap.
- [ ] **Checklist de cierre:** todas las salvaguardas fuera de los 6 controles, con número y nombre oficial · conteo 56/153 comprobado · cada fila con medida, estado y evidencia · estados «existente» respaldados por la ficha · resumen por estado.

### E.09 — Indicadores y auditoría interna · H4 · J.1.9 (1 %) · ~8 h
Plantilla: `E09_Indicadores_Auditoria_Interna.docx` · Moodle: `E09_Indicadores_Auditoria_Interna_<Equipo>.docx/.pdf` · **viernes 6-nov**

- [ ] **H.1 Al menos 1 indicador por cada uno de los 6 controles.** Cada ficha lleva:
  - [ ] Nombre: debe medir **el control**, no la actividad. «% de dispositivos inventariados» sí; «n.º de reuniones» no.
  - [ ] Fórmula (numerador / denominador × 100, o conteo).
  - [ ] **Meta** y **umbral de alerta**.
  - [ ] Frecuencia.
  - [ ] **Fuente** = la **evidencia del SOP (F.3)** del control.
  - [ ] Responsable: la **R** de E.06 mide y la **A** recibe.
- [ ] **H.2 Auditoría interna** (ISO/IEC 27001:2022, §9.2), con 6 elementos:
  - [ ] Alcance y objetivo (como mínimo los 6 controles).
  - [ ] Criterios: políticas y SOP propios, CIS v8.1 e ISO 27001.
  - [ ] Método y muestra: revisión documental, evidencias del SOP, entrevistas y tamaño de muestra por control.
  - [ ] Programa: fechas en el año simulado, **auditor independiente** del área auditada y duración. Si no hay auditoría interna en el organigrama, declarar quién ejerce la independencia (un tercero o una unidad ajena).
  - [ ] Informe y hallazgos: **formato de hallazgo** (conformidad / no conformidad / oportunidad de mejora) y a quién se reporta.
  - [ ] Seguimiento: las no conformidades generan acciones correctivas, **enlazadas con E.10**.
- [ ] **Checklist de cierre:** ≥1 indicador completo por control · fuente = evidencia del SOP y responsable en E.06 · auditoría con los 6 elementos, auditor independiente y formato de hallazgo.

### E.10 — Roadmap de madurez hacia IG3 · H5 · J.2.4 (2 %) · ~10 h
Plantilla: `E10_Roadmap_Madurez_IG.docx` · Moodle: `E10_Roadmap_Madurez_IG_<Equipo>.docx/.pdf` · **miércoles 11-nov**

- [ ] Agrupar en **iniciativas** las filas «por implementar» y «al roadmap» de E.08, más las salvaguardas «al roadmap» de la F.1 de E.07, más las acciones correctivas de E.09.
- [ ] **I.1**: cada iniciativa con salvaguardas, IG, **horizonte**, responsable (de E.06), **dependencias** y **resultado esperado verificable**. Horizontes:
  - **corto:** 4-ene a 30-jun-2027
  - **mediano:** 1-jul-2027 a 30-jun-2028
  - **largo:** 1-jul-2028 a 31-dic-2029
- [ ] Ordenar IG1 en el corto plazo, IG2 en el mediano e IG3 en el largo.
  - [ ] Se **adelanta** si trata un riesgo Crítico o Alto, sirve a un objetivo de E.02 con fecha anterior, o cumple una obligación legal o contractual.
  - [ ] Se **pospone** si una dependencia lo exige.
  - [ ] El motivo va en la columna «Dependencias».
- [ ] Ninguna iniciativa entra a un horizonte antes de que sus dependencias estén cubiertas.
- [ ] Hallazgos de software sin soporte (E.07, F.4) y brechas de los «existente parcial» (E.08) incluidos como iniciativas.
- [ ] **I.2 Estado por horizonte:** salvaguardas IG1/IG2/IG3 operando hoy, al 30-jun-2027, al 30-jun-2028 y al 31-dic-2029. **Al final operan 56 + 74 + 23 = 153.**
- [ ] **I.3**: tratamientos de E.05 **sin salvaguarda CIS** (control ISO 27002), con iniciativa, responsable, horizonte y resultado. Van **fuera** del conteo de 153.
- [ ] **Checklist de cierre:** cada iniciativa completa · todas las filas pendientes de E.08 y F.1 cubiertas · dependencias respetadas y IG3 alcanzado en 36 meses · I.2 e I.3 completas.

### E.11 — Documento final integrado · H5 · J.2 completo (15 %) · ~5 h de cierre + 9 h de ensamblaje parcial en S6
Plantilla: `E11_Documento_Final_LineaBase.docx` · Moodle: `E11_Documento_Final_LineaBase_<Organizacion>_<Equipo>.docx/.pdf` (**PDF + DOCX fuente**) · **miércoles 11-nov**

- [ ] **Portada** con la organización, el equipo y la ESEN. **Sin logotipos de terceros.**
- [ ] **Registro formal**: versión, fecha, elaboró (oficial de documentación), revisó (oficial de calidad) y aprobó (consultor líder).
- [ ] Tabla de contenidos y **numeración de páginas**.
- [ ] Las **13 secciones, en orden fijo**:
  - [ ] 1 Portada y datos generales (organización, IG3, equipo con roles, fecha, versión).
  - [ ] 2 Introducción y compromiso, de E.02 A.1, **con firmas** de la dirección y del responsable de seguridad.
  - [ ] 3 Alcance del SGSI, de E.02 A.2 + A.3 (v1.1).
  - [ ] 4 BIA, de E.03 **v1.1**.
  - [ ] 5 Activos, de E.04.
  - [ ] 6 Riesgos y mapa de calor, de E.05, con el apetito y la cuantificación de los Críticos.
  - [ ] 7 RACI, de E.06.
  - [ ] 8 Controles seleccionados, de E.07, **con subsecciones 8.1–8.6**.
  - [ ] 9 Baseline IG3, de E.08, con el resumen por estado.
  - [ ] 10 Indicadores y auditoría, de E.09.
  - [ ] 11 Roadmap, de E.10.
  - [ ] 12 **Conclusiones y recomendaciones** (redacción **nueva**): estado de riesgo, las 6 medidas prioritarias y la ruta a IG3. No se repite el resumen; se recomienda.
  - [ ] 13 **Bibliografía con ediciones y años**:
    - CIS v8.1 (2024)
    - ISO/IEC 27001 y 27002:2022
    - NIST SP 800-30 r1 (2012)
    - CSF 2.0 (2024)
    - ISO 22301:2019
    - ISO/TS 22317:2021
    - LPDP D.L. 144/2024
    - Ley de Ciberseguridad D.L. 143/2024 y PCI DSS v4.0.1, si aplican
    - los CIS Benchmarks citados, con producto y versión
    - los reportes citados
- [ ] **Anexo A:** todos los supuestos S-01…S-nn, en orden, con fundamento y entregable de origen.
- [ ] **Anexo B:** retroalimentación aplicada, una fila por hito H1–H4. Si un hito no tuvo retroalimentación, se escribe «sin retroalimentación recibida».
- [ ] **Anexo C:** lista de BIA_P01–P07, con **los 7 archivos adjuntos al final del PDF**.
- [ ] Aplicar la retroalimentación de cada hito **antes** de pegar cada sección.
- [ ] **Trazabilidad de extremo a extremo:** cada control de la sección 8 nombra riesgos de la 6, cada Crítico o Alto tiene control o salvaguarda, y cada indicador de la 10 mide un control de la 8. También BIA → activos → riesgos.
- [ ] Toda cifra del cuerpo tiene fuente.
- [ ] Exportar a PDF.
- [ ] **Checklist de cierre:** 13 secciones en orden y corregidas · bibliografía con ediciones · cadena verificable · políticas, SOP y controles específicos · roadmap que alcanza IG3 · portada, índice, numeración, registro, firmas y anexos A, B y C · nombre normalizado.

### E.12 — Presentación ejecutiva y defensa oral · H6 · J.3 (10 %) · ~10 h
Plantilla: `E12_Presentacion_Ejecutiva.pptx` · Moodle: `E12_Presentacion_Ejecutiva_<Organizacion>_<Equipo>.pptx/.pdf` · **12–14 de noviembre** (fecha y hora las asigna el docente)

- [ ] **9 diapositivas que suman 10:00 exactos.** Ensayar para 9 minutos. El docente **corta en el minuto 10**.
  - [ ] 1 Portada (0:30): organización, IG3 y equipo.
  - [ ] 2 Organización y alcance (1:00): procesos críticos, sedes, sistemas y exclusiones.
  - [ ] 3 Panorama del BIA (1:30): MTPD, RTO, costo por hora y SPOF.
  - [ ] 4 Mapa de calor (1:30): Críticos y Altos, y el apetito.
  - [ ] 5 Los 6 controles (2:00): control, riesgo, salvaguardas y evidencia, más el **argumento económico (ROSI) de uno**.
  - [ ] 6 Baseline (0:45): resumen por estado.
  - [ ] 7 Indicadores y auditoría (0:45): 2 indicadores y el programa.
  - [ ] 8 Roadmap (1:30): 3 horizontes, dependencias y estado final.
  - [ ] 9 Recomendaciones (0:30): las **3 decisiones** que la dirección toma primero.
- [ ] Texto mínimo, **cada cifra con su «Fuente»** al pie, máximo 1 tabla o 1 gráfico o 3 ideas por diapositiva.
- [ ] **Notas del orador** en cada diapositiva: quién presenta, qué dice y la pregunta probable con su respuesta.
- [ ] Cada bloque tiene un **presentador y un suplente**.
- [ ] **Diapositiva 10, «Preparación de la defensa»** (se entrega y no se proyecta):
  - [ ] Tabla de reparto de bloques.
  - [ ] **Registro de ≥3 ensayos cronometrados** (fecha y duración).
  - [ ] Preguntas preparadas con su respuesta, que citen IDs de riesgo, cifras del BIA, salvaguardas y marcos con edición:
    - [ ] ¿Por qué esos 6 controles?
    - [ ] ¿Por qué ese orden del roadmap?
    - [ ] ¿Por qué IG3?
    - [ ] Al menos una pregunta propia del equipo.
- [ ] Llevar el documento final impreso o en pantalla para consulta.
- [ ] **Todos ensayan todos los bloques.** Preguntan a cualquier integrante.
- [ ] **Checklist de cierre:** 9 bloques en 10 minutos · reparto con suplentes y ensayos registrados · respuestas preparadas con evidencia · apoyo visual sobrio y trabajo de equipo visible.

---

## 4. Versiones 1.1 (fáciles de olvidar)

| Versión 1.1 | Qué cambia | Se entrega con | Fecha |
|---|---|---|---|
| E.01 v1.1 | Organización asignada, n.º, IG y fecha de asignación | E.02 | vie 2-oct |
| E.02 v1.1 | Sección A.3: revisión del alcance tras BIA_P05 | E.03 | vie 16-oct |
| E.03 v1.1 | B.4 con el ID de riesgo de cada SPOF | E.05 | vie 23-oct |
| BIA_P07 v1.1 | Secciones 8–11 (5 pasos, ACC, ROSI, sensibilidad) | E.05 | vie 23-oct |
| E.04 v1.1 | Columna 8: riesgos de cada activo o la justificación de su ausencia | E.05 | vie 23-oct |

---

## 5. Calendario y carga

| Semana | Fechas | Trabajo | Horas de equipo |
|---|---|---|---|
| S1 | 21–27 sep | E.01 | 2 |
| S2 | 28 sep – 4 oct | E.02 · arranque del BIA | 6 |
| S3 | 5–11 oct | E.03 · E.04 | ↓ |
| S4 | 12–18 oct | E.03 · E.04 · arranque de E.05 | 44 (H2) |
| S5 | 19–25 oct | **E.05 · E.06 + v1.1 → vie 23-oct** | 25 (H3) |
| S6 | 26 oct – 1 nov | **E.07 → vie 30-oct** · ensamblaje de E.11, secciones 1–7 | 42 + 9 |
| S7 | 2–8 nov | **E.08 · E.09 → vie 6-nov** | ~26 |
| S8 | 9–15 nov | **E.10 · E.11 → mié 11-nov** · **E.12 defensa 12–14 nov** | 15 + 10 |

Pesos por hito: H1 3 % · H2 5 % · H3 5 % · H4 7 % · H5 15 % · H6 10 %.

---

## 6. Control final antes de cada entrega (oficial de calidad)

- [ ] El checklist de cierre de la ficha (Guía, sección 9) está todo marcado.
- [ ] El nombre del archivo es el normalizado, con `<Equipo>` (y `<Organizacion>` en E.11 y E.12).
- [ ] La tabla de identificación está llena: equipo, organización, IG3, integrantes, fecha y versión.
- [ ] No quedan filas «(p. ej.)» sin reemplazar.
- [ ] Los supuestos continúan la numeración S-nn global y ningún dato de la ficha fue reemplazado por un supuesto.
- [ ] Los IDs (P-nn, A-nn, R-nn, SLE-nn) son consistentes con los entregables anteriores.
- [ ] Las cifras tienen fuente y los cálculos están verificados:
  - [ ] RTO+WRT≤MTPD
  - [ ] SLE=AV×EF
  - [ ] ALE=SLE×ARO
  - [ ] ROSI
  - [ ] conteo 56/153
- [ ] La hoja de control está actualizada (fecha de entrega y V.º B.º).
- [ ] La retroalimentación del hito anterior está registrada para el Anexo B.

---

## 7. Fuentes oficiales (del paquete, verificadas por la cátedra el 23-sep-2026)

- CIS Controls v8.1: https://www.cisecurity.org/controls/v8-1 (descarga con registro) · Navigator sin registro: https://www.cisecurity.org/controls/cis-controls-navigator
- CIS Benchmarks: https://www.cisecurity.org/cis-benchmarks · PDF: https://learn.cisecurity.org/benchmarks
- PCI DSS v4.0.1: https://www.pcisecuritystandards.org/document_library/
- LPDP, D.L. 144/2024: https://www.asamblea.gob.sv/sites/default/files/documents/decretos/7A4FBD85-7E1B-46BE-9408-6FC549E53E00.pdf
- Ley de Ciberseguridad, D.L. 143/2024: https://www.asamblea.gob.sv/sites/default/files/documents/decretos/D056D9A1-299D-4188-941A-9C3B5898D3F3.pdf

## 8. Dónde está cada cosa en `Docs/`

| Necesito… | Archivo |
|---|---|
| Reglas, pasos, ejemplos y checklists de cierre | `01_Guias/Guia_Estudiante_Proyecto_Final_ESEN_2026.pdf`, sección 9 |
| Rúbrica | Misma guía, Anexo J |
| Método BIA | `01_Guias/Guia_Estudiante_BIA.pdf` + `04_Anexos_BIA/ESEN2026_BIA_Presentacion…pdf` |
| Perfil y ficha de la empresa | `02_Catalogo/Catalogo_Empresas_Proyecto_Final_ESEN_2026.pdf`, sección 4.n |
| Plantillas a llenar | `03_Plantillas_Entregables/` (E01–E12) y `04_Anexos_BIA/` (BIA_P01–P07) |
| Seguimiento semanal | `05_Control_Entregables/Control_Entregables_Proyecto_Final_ESEN_2026.docx` |
| Cómo se ve terminado | `06_Proyecto_Ejemplo_ENSA/` (mismo nombre de archivo por entregable) |
