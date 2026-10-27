# Proyecto Final Ciberseguridad ESEN 2026 — Equipo 8 «Cuartel General»

**Organización:** Express Logistics International (**ELI**), n.º 22 del catálogo · **IG3** (153 salvaguardas CIS v8.1)
**Equipo:** Guillermo Molina · Erick Pineda · Javier Chavez · Sebastian Dimas · Joseph Lyon · Ali Cheves

Este README define **quién hace qué, cuándo y cómo se trabaja en el repo**, para personas y para sus agentes de IA. El detalle de cada entregable, campo por campo, está en [`CHECKLIST_Proyecto_Final.md`](CHECKLIST_Proyecto_Final.md). Si algo de aquí choca con la Guía del Estudiante, manda la guía.

---

## 0. Situación al 18-oct-2026 — leer primero

- **No hemos entregado nada.** Según el calendario oficial, ya vencieron:
  - E.01 (25-sep)
  - E.02 (2-oct)
  - E.03 + BIA_P01–P07 y E.04 (16-oct)
- El **próximo hito oficial es H3, el viernes 23-oct**: E.05, E.06 y las versiones 1.1 de E.03, E.04 y BIA_P07.
- **Plan:** esta semana hacemos un **sprint de recuperación** y entregamos de E.01 a E.06 el viernes 23-oct.
- **Lunes 19-oct, primera hora (Guillermo):**
  1. Registrar ELI en el aula virtual. **La primera solicitud válida bloquea la organización** y otro equipo podría tomarla.
  2. Escribir al docente para confirmar la asignación de ELI y si acepta la entrega tardía de E.01–E.04 (y con qué penalización).
  3. Avisar al grupo apenas haya respuesta. Si el docente indica otra cosa, este plan se ajusta.

---

## 1. Roles oficiales (Guía, sección 3)

Esta es una propuesta y el equipo puede cambiarla. Si cambia, hay que actualizarla también en E.01.

| Integrante | Rol oficial | De qué responde |
|---|---|---|
| **Guillermo Molina** | **Consultor líder** | Plan y cronograma, relación con el docente y asesorías, decisiones finales, numeración final de IDs y supuestos, conclusiones de E.11 |
| **Erick Pineda** | **Analista de riesgos (responsable del rol)** | Método BIA (P01, P05, P06), matriz de riesgos E.05 y cuantificación D.6/D.7 |
| **Javier Chavez** | **Analista de riesgos (comparte; responsable: Erick)** | Fichas BIA de procesos, registro de riesgos y mapa de calor |
| **Sebastian Dimas** | **Arquitecto de controles** | E.04 activos, selección de los 6 controles, consolidación de E.08 (conteo 56/153), roadmap E.10 |
| **Joseph Lyon** | **Oficial de documentación** | E.02 alcance, E.06 RACI, formato de las plantillas, ensamblaje de E.11, bibliografía |
| **Ali Cheves** | **Oficial de calidad** | Checklist de cierre de **cada** entregable antes de subirlo, revisión de PRs, trazabilidad riesgo → control → indicador, E.09 auditoría |

> El rol dice **de qué responde** cada persona, no **qué es lo único que hace**. El trabajo se reparte parejo (unas 30–35 h por persona), y **en la defensa le preguntan a cualquiera sobre cualquier parte**.

---

## 2. Orden de trabajo

El orden de los documentos, por fases, está en [`ROADMAP.md`](ROADMAP.md). El equipo avanza fase por fase, sin saltarse ninguna.

---

## 3. Datos clave de ELI (la fuente completa está en `registros/ficha_ELI.md`)

- **4 procesos críticos según el perfil:**
  1. TMS (Manhattan): 24/7, 110 coordinadores/turno a USD 8/h
  2. WMS (Manhattan): lun–sáb 6:00–22:00, 260 bodegueros/turno a USD 4,50/h, SLA farmacéutico de 24 h con crédito del 5 %
  3. Plataforma aduanal (desarrollo propio): lun–sáb 7:00–20:00 con aduana aérea 24 h, 45 tramitadores a USD 9/h, en riesgo la licencia y la certificación OEA
  4. Portal de visibilidad (Azure): 24/7, 8 personas a USD 10/h
- **Economía:**
  - ingresos de USD 95 M y margen operativo del 7 %
  - temporada alta de septiembre a noviembre, con factor 1,5
  - 650 declaraciones al día y 2 400 embarques activos
  - USD 180 M de inventario de clientes
  - **60 000 titulares** (destinatarios) y 4 800 clientes empresariales
  - **USD 0,30** por notificar a cada titular
  - USD 150 por día por contenedor retenido
  - USD 900 000 de reposición de servidores
- **Organigrama:** Dirección General; Gerencias de Carga Aérea, Carga Marítima, Aduanas y Almacenamiento; TI (22 personas); Finanzas (incluye RR. HH.); Legal y Cumplimiento Aduanero; auditoría interna de 1 persona. **No hay unidad de seguridad**, así que se crea como supuesto en E.02.
- **Presupuesto de seguridad:** 2027 = USD 700 000 (450 000 de inversión + 250 000 de operación); 2028 y 2029 = USD 500 000 por año, sujeto a aprobación. Arranque del programa: **lunes 4-ene-2027**.
- **Cumplimiento que el cliente reconoce:** CAUCA y su reglamento, normativa de la DGA, certificación **OEA**, **LPDP**, buenas prácticas de almacenamiento farmacéutico. **No hay pagos con tarjeta declarados**, así que **no aplica PCI DSS**.
- **Controles que ya existen** (son los únicos que pueden marcarse «existente» o «existente parcial» en E.08):
  - desarrollo sin validación de entradas
  - portal solo con usuario y contraseña
  - sin plan de incidentes
  - **antivirus en Windows**
  - **videovigilancia y guardias en bodegas**
- **Tecnología** (versiones para los CIS Benchmarks y posibles hallazgos de fin de soporte en E.07 F.4, que **cada uno debe verificar con la página oficial del fabricante**):
  - Windows Server 2019 + SQL Server 2019 (TMS/WMS)
  - **PHP 7.4 + MySQL 5.7** (aduanal)
  - **.NET 6** + Azure SQL (portal)
  - AD sobre **Windows Server 2016**
  - **Windows 10** y 11
  - EDI por SFTP
  - MPLS entre el centro de distribución y 2 bodegas
- **Pistas para SPOF y riesgos** (hay que validarlas en el BIA; no son conclusiones):
  - enlace único con la aduana (caída de 7 h en 2026)
  - **no hay sitio alterno**
  - el respaldo del aduanal está **en el mismo servidor**
  - las cintas de TMS/WMS se guardan **en el mismo centro de distribución**
  - incidentes: robo de contenedor por credenciales reutilizadas (2023), inyección en el aduanal (2024), ransomware en tramitadores (2025)
- **Ejes de amenaza:** **identidad** y **terceros** aplican siempre; **nube** se activa por Azure; **IA** y **OT** hay que evaluarlos y justificar en una línea si no aplican.

---

## 4. Cómo trabajamos en el repo (GitHub)

### Estructura

```
/                                  ← raíz del repo (carpeta Cyber)
├── README.md                      ← este archivo
├── CHECKLIST_Proyecto_Final.md    ← checklist detallado de cada entregable
├── Docs/                          ← paquete oficial PF_V2.2 · SOLO LECTURA, no se edita
├── registros/
│   ├── ficha_ELI.md               ← perfil + ficha de ELI extraídos del catálogo · fuente única de datos
│   ├── supuestos.md               ← registro global S-nn (ver regla de IDs)
│   ├── ids.md                     ← P-nn procesos · A-nn activos · R-nn riesgos · SLE-nn escenarios
│   └── decisiones.md              ← decisiones del equipo con fecha (pesos BIA, apetito, 6 controles…)
├── entregables/
│   ├── E01_Acta/
│   ├── E02_Compromiso_Alcance/
│   ├── E03_BIA/                   ← BIA_P01…P07 + consolidación E03
│   ├── E04_Activos/
│   ├── E05_Riesgos/
│   ├── E06_RACI/
│   ├── E07_Controles/Control_XX/  ← una carpeta por control
│   ├── E08_Baseline/
│   ├── E09_Indicadores/
│   ├── E10_Roadmap/
│   ├── E11_Documento_Final/
│   └── E12_Presentacion/
└── entregas/H1 … H6/              ← copia exacta de lo que se subió a Moodle, con nombre normalizado
```

### Flujo de trabajo

1. **El borrador se escribe en Markdown** (`entregables/EXX/borrador.md` o `BIA_P0X_borrador.md`). Markdown se puede revisar y fusionar en Git; los `.docx` no.
2. **Cuando el borrador está aprobado**, el R del entregable copia la plantilla de `Docs/03_Plantillas_Entregables/` (o `Docs/04_Anexos_BIA/`) a su carpeta y la llena. **No se cambia la estructura ni los encabezados.**
3. **Un `.docx` tiene un solo dueño a la vez.** Nadie edita un `.docx` ajeno; los comentarios se dejan en el PR.
4. **Ramas:** `<iniciales>/<entregable>-<tema>`. Por ejemplo `ep/e05-riesgos`, `jc/bia-tms`, `sd/e07-control-12`. Las iniciales son: gm, ep, jc, sd, jl, ac.
5. **Nada va directo a `main`.** Todo entra por PR, con revisión de **Ali** y de una persona más. Durante el sprint, si Ali no alcanza, revisa el A del entregable.
6. **Commits en español** y descriptivos, por ejemplo `E05: agrega R-07 a R-12 (ejes nube y terceros)`.
7. `.gitignore` mínimo:
   ```
   ._*
   .DS_Store
   ~$*
   *.tmp
   ```

### Regla de IDs (evita choques con 6 personas en paralelo)

- La guía exige supuestos **S-nn globales y correlativos en orden de entregable**. Mientras se trabaja en paralelo, cada quien usa **IDs temporales**: `S-tmp-<iniciales>-<n>`, `R-tmp-jc-3`, `A-tmp-sd-2`.
- **Guillermo asigna los IDs finales** al fusionar cada entregable, en el orden E.01 → E.10, y actualiza `registros/supuestos.md` e `ids.md`.
- Una vez asignado, **un ID no cambia nunca**. Los A-nn de E.04 son los mismos en E.05, y los R-nn de E.05 son los mismos en E.07, E.10 y E.11.

---

## 5. Instrucciones para agentes de IA

> Si eres un agente de IA (Claude, ChatGPT, Copilot, etc.) ayudando a un integrante de este equipo, sigue esta sección al pie de la letra.

**Antes de escribir cualquier cosa, lee en este orden:**
1. Este `README.md` y después `ROADMAP.md`, para ubicar en qué fase y documento va el equipo.
2. `CHECKLIST_Proyecto_Final.md`: la sección del entregable en curso.
3. `registros/ficha_ELI.md`: los datos de la organización.
4. `Docs/01_Guias/Guia_Estudiante_Proyecto_Final_ESEN_2026.pdf`, **sección 9**, la ficha del entregable (pasos, campos, errores frecuentes y checklist de cierre). Para el BIA, además, `Docs/01_Guias/Guia_Estudiante_BIA.pdf`.
5. La plantilla del entregable en `Docs/03_Plantillas_Entregables/` o `Docs/04_Anexos_BIA/`.
6. El entregable equivalente en `Docs/06_Proyecto_Ejemplo_ENSA/`, **solo para ver formato y extensión**.
7. `registros/supuestos.md`, `registros/ids.md` y `registros/decisiones.md`, para no contradecir lo ya decidido.

**Reglas obligatorias:**
- **Nunca inventes datos.** Todo número sale de la ficha de ELI, de un entregable anterior del repo o de un **supuesto declarado**.
- **Nunca reemplaces un dato de la ficha por un supuesto.** Antes de declarar un supuesto, busca el dato en `ficha_ELI.md`.
- Cada supuesto lleva un ID temporal (`S-tmp-<iniciales>-n`), el supuesto y su fundamento. Agrégalo también a `registros/supuestos.md`.
- **No copies cifras ni texto de RHM ni de ENSA.** Son otras empresas.
- **No edites archivos de tareas que no son de tu usuario**, ni nada dentro de `Docs/`. Si detectas un error en el trabajo de otro, déjalo escrito como comentario para el PR.
- **Respeta la estructura de la plantilla.** Reemplaza las filas «(p. ej.)» y conserva los encabezados.
- **Haz los cálculos con código o con una hoja de cálculo**, no de cabeza. Esto incluye:
  - costo por hora y por día
  - límites de la escala de P03 (porcentajes de USD 95 M)
  - puntajes de P05 (redondeo a 2 decimales, la mitad hacia arriba)
  - SLE = AV × EF
  - ALE = SLE × ARO
  - ACC con la adquisición anualizada a 5 años
  - ROSI = (Beneficio − ACC) ÷ ACC
  - conteo 56/153
- **Comprobaciones duras:** RTO + WRT ≤ MTPD · 1 sola A y ≥1 R por fila de la RACI · ≥12 riesgos · cada SPOF es la vulnerabilidad de algún riesgo · cada Crítico o Alto está cubierto por un control.
- **Fin de soporte y CIS Benchmarks:** verifica en la fuente oficial (fabricante o https://www.cisecurity.org/cis-benchmarks) y **pon el enlace**. Si no puedes verificarlo, dilo; no lo afirmes.
- **Normas:** cita siempre con edición y año (CIS v8.1 2024, ISO/IEC 27001:2022, NIST SP 800-30 r1, CSF 2.0, ISO 22301:2019, LPDP D.L. 144/2024 art. 25, Ley de Ciberseguridad D.L. 143/2024).
- **Al terminar, corre el checklist de cierre** de la ficha del entregable (Guía, sección 9) y reporta qué casillas no se cumplen.
- Escribe en **español**, con tono profesional de firma consultora, específico para ELI. **El texto genérico se califica como ausente.**
- **No subas nada a Moodle ni fusiones a `main`.** Eso lo hacen las personas.

**Prompt sugerido para iniciar tu agente:**
> «Soy <nombre> del equipo 8. Lee el README.md y el CHECKLIST_Proyecto_Final.md del repo. Estamos trabajando en <documento del ROADMAP.md>. Lee la ficha de ELI y la sección 9 de la Guía para ese entregable, y ayúdame a hacer el borrador en `entregables/<carpeta>/borrador.md` siguiendo las reglas de la sección 5 del README.»

---

## 6. Ritmo del equipo

- **Reunión semanal:** día y hora por definir (va en el acta E.01). **Asesoría con el docente:** 30 minutos semanales. Guillermo lleva los avances y las preguntas concretas.
- **Durante el sprint de esta semana:** check-in diario de 15 minutos por chat, respondiendo: qué terminé, qué hago hoy y qué me bloquea.
- **Semáforo semanal** en `Docs/05_Control_Entregables/` (copia en `registros/`). Se marca **rojo apenas** un entregable esté en duda.
- **Retroalimentación del docente:** cada vez que llegue, se anota en `registros/decisiones.md`. Joseph la vuelca al Anexo B de E.11.

## 7. Calendario de entregas

| Fecha | Entregamos | Responsable de subirlo |
|---|---|---|
| **vie 23-oct** | E.01 (v1.1) · E.02 (v1.1) · E.03 + BIA_P01–P07 (v1.1) · E.04 (v1.1) · E.05 · E.06 | Guillermo (tras el visto bueno de Ali) |
| **vie 30-oct** | E.07 (6 archivos) | Sebastian |
| **vie 6-nov** | E.08 · E.09 | Sebastian (E.08) · Ali (E.09) |
| **mié 11-nov** | E.10 · E.11 (PDF + DOCX) | Sebastian (E.10) · Joseph (E.11) |
| **12–14-nov** | E.12 + defensa oral | Guillermo |

Las fechas de recuperación de E.01–E.04 dependen de la respuesta del docente (sección 0).
