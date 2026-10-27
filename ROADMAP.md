# Roadmap de documentos — Proyecto Final ELI (Equipo 8)

En qué **orden** se hace cada documento y qué necesita para arrancar. Cada documento depende del anterior: **no se salta de fase**. El detalle campo por campo de cada uno está en `CHECKLIST_Proyecto_Final.md`.

> Todos los archivos citados están en `Docs/`. Plantillas: `03_Plantillas_Entregables/` (E01–E12) y `04_Anexos_BIA/` (BIA_P01–P07). Ejemplo resuelto del mismo documento: `06_Proyecto_Ejemplo_ENSA/`.

---

## Antes de empezar (una sola vez)

- [ ] Leer `registros/ficha_ELI.md` completo. Es la fuente de **todos** los datos.
- [ ] Leer la **sección 9** de `01_Guias/Guia_Estudiante_Proyecto_Final_ESEN_2026.pdf` (tiene una ficha por entregable).
- [ ] Abrir `registros/supuestos.md`. Ahí se anota cada supuesto como S-01, S-02… en orden.

---

## FASE 0 — Fundación · ⬅ EMPIEZAN AQUÍ

| Orden | Documento | Plantilla | Necesita | Produce |
|---|---|---|---|---|
| 1 | **E.01 Acta de equipo** (sale directo en v1.1, con ELI ya asignada) | `E01_Acta_Equipo_Seleccion_Empresa.docx` | Integrantes, roles, ELI n.º 22, IG3 | Equipo y organización oficiales |
| 2 | **E.02 Compromiso de la dirección y alcance** (A.1 y A.2; A.3 queda pendiente) | `E02_Compromiso_Direccion_Alcance_SGSI.docx` | E.01 + ficha (organigrama, presupuesto USD 700k, arranque 4-ene-2027, cumplimiento) | Procesos en alcance, objetivos con fecha y la función de seguridad creada como supuesto |

✅ La fase está cerrada cuando el alcance tiene los 4 procesos de ELI (TMS, WMS, aduanal y portal), las exclusiones justificadas, la LPDP art. 25 y la Ley de Ciberseguridad.

---

## FASE 1 — BIA (la base de todo) · la más pesada, ~38 h

En la Fase 1 el orden es estricto.

| Orden | Documento | Plantilla | Qué hace |
|---|---|---|---|
| 3 | **BIA_P01** Inventario de procesos | `BIA_P01_Inventario_Procesos.docx` | Lista de los 4 procesos críticos más los de soporte que los alimentan |
| 4 | **BIA_P05** Matriz de criticidad (primera pasada) | `BIA_P05_Matriz_Criticidad_Priorizacion.docx` | Pesos que suman 100 %, calificación de **todos** los procesos en el corte de 24 h y clase de cada uno → **define cuáles son críticos** |
| 5 | **BIA_P02** Ficha BIA, una por proceso crítico | `BIA_P02_Ficha_BIA_Proceso.docx` | MTPD, RTO, WRT, RPO y MBCO (con RTO+WRT ≤ MTPD), costo por hora y por día, AV, EF y SLE. El portal además lleva el SLE de exposición: 60 000 × USD 0,30 |
| 6 | **BIA_P03** Matriz de impacto, una por proceso crítico | `BIA_P03_Matriz_Impacto_Tiempo.docx` | 5 categorías × 5 cortes, con la escala calculada sobre los USD 95 M de ingresos y el MTPD derivado |
| 7 | **BIA_P04** Mapa de dependencias, uno por proceso crítico | `BIA_P04_Mapa_Dependencias_Recursos.docx` | 6 clases de dependencia, recursos mínimos y **puntos únicos de falla (SPOF)** |
| 8 | **BIA_P05** (cierre) | misma | Se reemplazan las notas provisionales por las de P03 y se arma la lista final ordenada |
| 9 | **BIA_P06** Supuestos, SPOF y brechas | `BIA_P06_Registro_Supuestos_SPOF_Brechas.docx` | Mínimo 2 SPOF, brechas y supuestos en 3 escenarios |
| 10 | **BIA_P07** Informe ejecutivo (secciones 1–7, 12 y 13) | `BIA_P07_Informe_Ejecutivo.docx` | Las secciones 8–11 se marcan **«se completa en E.05»** |
| 11 | **E.03 Consolidación** | `E03_BIA_Consolidacion_Procesos_Criticos.docx` | Tablas B.1–B.5, que resumen P01–P07. **Se entrega junto con los 7 anexos** |
| 12 | **E.02 v1.1** | misma de E.02 | Se llena la sección A.3: diferencias entre el alcance y las clases de BIA_P05 |

---

## FASE 2 — Activos

| Orden | Documento | Plantilla | Necesita |
|---|---|---|---|
| 13 | **E.04 Inventario de activos** (12–20 activos, A-01…) | `E04_Inventario_Clasificacion_Activos.docx` | BIA_P04: cada dependencia de un proceso crítico se vuelve activo. La columna 8 queda vacía hasta E.05 |

---

## FASE 3 — Riesgos y responsables

| Orden | Documento | Plantilla | Necesita |
|---|---|---|---|
| 14 | **E.05 Matriz de riesgos** (≥12 riesgos, R-01…) | `E05_Matriz_Riesgos.docx` | Activos de E.04 · SPOF de E.03 · SLE de E.03 para la tabla D.6 (ALE, ACC, ROSI) |
| 15 | **E.03 v1.1, E.04 v1.1 y BIA_P07 v1.1** | las mismas | E.05: los IDs de riesgo en B.4 y en la columna 8, y las secciones 8–11 de P07 con los números de D.6 y D.7 |
| 16 | **E.06 Matriz RACI** (se puede hacer en paralelo a E.05) | `E06_Matriz_RACI.docx` | Organigrama de ELI + la función de seguridad de E.02 + las actividades nuevas de E.05 |

📌 Al terminar esta fase **se puede empezar a armar E.11, secciones 1–7** (ver Fase 5).

---

## FASE 4 — Controles

| Orden | Documento | Plantilla | Necesita |
|---|---|---|---|
| 17 | **E.07 Seis controles CIS** (6 archivos: política, SOP y controles) | `E07_Desarrollo_Control_CIS.docx` × 6 | Riesgos Críticos y Altos de E.05 (de ahí se eligen los 6) + roles de E.06 |
| 18 | **E.08 Baseline de 153 salvaguardas** | `E08_Checklist_Baseline_IG.docx` | E.07: se borran las filas de esos 6 controles; el resto se mapea. Se comprueba IG1 = 56 y total = 153 |
| 19 | **E.09 Indicadores y auditoría** | `E09_Indicadores_Auditoria_Interna.docx` | La evidencia que deja cada SOP de E.07 (al menos un indicador por control) + roles de E.06 |

---

## FASE 5 — Cierre

| Orden | Documento | Plantilla | Necesita |
|---|---|---|---|
| 20 | **E.10 Roadmap de madurez** (horizontes 2027–2029) | `E10_Roadmap_Madurez_IG.docx` | Filas «por implementar» y «al roadmap» de E.08 + E.07 + acciones de E.09 + tratamientos sin CIS de E.05 |
| 21 | **E.11 Documento final** (13 secciones + anexos A, B y C) | `E11_Documento_Final_LineaBase.docx` | **Todo lo anterior, ya corregido.** Las secciones 1–7 se arman desde la Fase 3 |

---

## FASE 6 — Defensa

| Orden | Documento | Plantilla | Necesita |
|---|---|---|---|
| 22 | **E.12 Presentación** (9 diapositivas, 10 min, más el anexo de preparación) | `E12_Presentacion_Ejecutiva.pptx` | E.11 |
| 23 | **Ensayos** (mínimo 3, cronometrados) y **defensa oral** | — | Todos dominan todo |

---

## Vista rápida

```
FASE 0  E.01 → E.02
FASE 1  BIA_P01 → BIA_P05 → [P02 → P03 → P04 por proceso crítico] → P05 final → P06 → P07 → E.03 → E.02 v1.1
FASE 2  E.04
FASE 3  E.05 → v1.1 de E.03/E.04/P07   ‖   E.06        (+ arranque de E.11 §1–7)
FASE 4  E.07 (×6) → E.08 → E.09
FASE 5  E.10 → E.11
FASE 6  E.12 → defensa
```

## Fechas oficiales del docente (para medir el atraso)

| Documento | Fecha oficial |
|---|---|
| E.01 · E.02 | 25-sep · 2-oct |
| E.03 + BIA · E.04 | 16-oct |
| E.05 · E.06 · versiones 1.1 | 23-oct |
| E.07 | **vie 30-oct** |
| E.08 · E.09 | vie 6-nov |
| E.10 · E.11 | mié 11-nov |
| E.12 + defensa | 12–14-nov |
