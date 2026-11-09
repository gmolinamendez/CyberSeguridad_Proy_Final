# context.md — Verdad del proyecto (ELI, Equipo 8)

Última actualización: 2026-11-09. Fuente: lectura de `Entregables/E01`, `E02`, `anexos/BIA_P01–P04` y `registros/ficha_ELI.md`.
La IA consulta este archivo antes de ayudar. Si el equipo cambia una decisión, se actualiza aquí.

## 1. Equipo
- Equipo 8 «Cuartel General». Docente: Ing. Héctor Cuchilla. Ciclo 03-2026.
- Luis Guillermo Molina Méndez, 20245562: consultor líder
- Joseph Andrew Lyon Sullivan Silva, 20245574: oficial de documentación
- Erick Daniel Pineda Baires, 20245510: analista de riesgos (responsable del rol)
- Javier Andrés Chávez Portal, 20245512: analista de riesgos (comparte)
- Ali Efrain Cheves Muñoz, 20245542: oficial de calidad
- Sebastián Alberto Dimas Rodríguez, 20245246: arquitecto de controles

## 2. Organización
- Express Logistics International (ELI), catálogo n.º 22, **IG3** (CIS v8.1: 153 salvaguardas).
- Logística y transporte de carga. Grande, 850 empleados. Ingresos USD 95 M, margen 7 %.
- Opciones descartadas del equipo: Capitalia (2.ª) y Constructora Horizonte (3.ª). No se usan.
- Organigrama (ficha): Dirección General; Gerencias de Carga Aérea, Carga Marítima, Aduanas y Almacenamiento; TI (22); Finanzas (incluye RR. HH.); Legal y Cumplimiento Aduanero; auditoría interna (1 persona). **Hoy no existe unidad de seguridad.**
- No se conocen nombres de personas de ELI. Cualquier nombre de dueño o cargo es supuesto.

## 3. Decisiones del equipo (de E.01 y E.02)
- Procesos en alcance (6): los 4 críticos de la ficha (TMS, WMS, Plataforma de Gestión Aduanal, Plataforma de Visibilidad para Clientes) más 2 de apoyo: **Gestión de usuarios y equipos de trabajo** y **Gestión de conexiones con terceros**.
- Unidades en alcance: Dirección General, Carga Aérea, Carga Marítima, Aduanas, Almacenamiento, TI, Legal y Cumplimiento Aduanero y la **nueva Unidad de Seguridad de la Información**. Finanzas y auditoría interna: apoyo y control.
- Lugares: centro de distribución cerca del aeropuerto, oficinas de aduanas, bodegas unidas por MPLS y nube Azure.
- Unidad de Seguridad (decisión del equipo, supuesto): 1 oficial de seguridad más 2 analistas, reporta a Dirección General. Firmantes simulados de la declaración: Luis Guillermo Molina (dirección general) y Erick Pineda (responsable de seguridad).
- Exclusiones declaradas: (1) sistemas de aerolíneas, navieras y aduanas, ELI solo controla la conexión; (2) wifi de invitados, separada de la red; (3) cámaras y guardias de bodega, ya tienen programa de seguridad física, solo entrarían si conectan a la red de ELI.
- Marcos: CIS Controls v8.1 (2024) IG3, ISO/IEC 27001:2022, NIST CSF 2.0 (2024), ciclo PDCA.
- Leyes: LPDP D.L. 144/2024 art. 25 (aviso en 72 h a la Agencia de Ciberseguridad del Estado, FGR y titulares); Ley de Ciberseguridad D.L. 143/2024 (si la Agencia califica a ELI como operador de infraestructura crítica); normativa de la DGA; CAUCA; certificación OEA.
- Metas de seguridad con fecha: plan de respuesta a incidentes aprobado al 31-mar-2027 y simulacro de fuga en 72 h antes del 31-dic-2027; 2FA y bloqueo por intentos fallidos en el portal al 30-sep-2027; validación contra inyección SQL en la plataforma aduanal al 30-sep-2027; backups fuera del centro de distribución y recuperación probada por sistema al 30-jun-2027.
- Presupuesto (ficha): 2027 USD 700 000 (450 000 inversión + 250 000 operación); 2028 y 2029 USD 500 000 por año, **sujeto a aprobación**. Arranque del programa: lunes 4-ene-2027.
- Revisión de la dirección cada 3 meses y revisión extra tras un incidente; el alcance se revisa 1 vez al año.

## 4. Datos de la ficha que se usan tal cual
- Detalle completo en `registros/ficha_ELI.md`. Nunca sustituir por supuesto.
- TMS: 24 h todos los días; 110 coordinadores por turno; Manhattan, Windows Server 2019 + SQL Server 2019.
- WMS: lun–sáb 6:00–22:00; 260 bodegueros por turno; SLA farmacéutico de despacho en 24 h, crédito del 5 % si falla.
- Plataforma aduanal: desarrollo propio PHP 7.4 + MySQL 5.7; lun–sáb 7:00–20:00, aduana aérea 24 h; 650 declaraciones por día; 45 tramitadores.
- Portal de clientes: Azure App Service .NET 6 + Azure SQL; 24 h todos los días; 8 personas de soporte digital; autenticación solo usuario y contraseña, sin bloqueo.
- 2 400 embarques activos; USD 180 M de inventario de clientes en bodegas; 4 800 clientes empresariales; 60 000 destinatarios; costo de notificar USD 0,30 por titular; contenedor retenido USD 150 por día.
- Incidentes: 2023 robo de contenedor, USD 240 000 (credenciales reutilizadas); 2024 entradas manipuladas en formulario aduanal; 2025 ransomware en estaciones de tramitadores, 3 días, USD 50 000; 2026 caída del enlace con la aduana, 7 h.
- Sin plan de respuesta a incidentes. Sin sitio alterno. Backup del sistema aduanal en el mismo servidor.

## 5. Estado de los entregables (al 2026-11-09)
- Detalle y casillas en `CHECKLIST_Proyecto_Final.md` (bloque «Estado del proyecto»).
- E.01 y E.02: v1.0 llenas (27-oct). Faltan los huecos de la sección 6.
- BIA_P01 a P04 (Guillermo): llenos, con pulido pendiente. P04 es el más atrasado (§3 con TMS duplicado, §5 con tablas repetidas, sin IDs SPOF).
- BIA_P05 a P07 y E.03: los hace Joseph; esperan los datos de P02 §4 y §9 y los S-nn.
- E.04 y E.05: plantillas copiadas el 9-nov, vacías. E.04 (Sebastian) arranca con BIA_P04; E.05 (Erick) espera E.03, E.04 y los SPOF.
- E.06 a E.12: sin empezar.
- Fechas oficiales de E.01 a E.07 ya pasaron; la forma de entregar lo atrasado la confirma el docente.
- Supuestos: E.01 y E.02 todavía no tienen S-nn numerados. Los del BIA arrancan en **S-03** si E.01/E.02 declaran 2 (Unidad de Seguridad, firmantes simulados), o en S-04 si declaran 3. Decisión del equipo (D2).
- `registros/` solo tiene `ficha_ELI.md`; `supuestos.md`, `ids.md` y `decisiones.md` no existen todavía.

## 6. Pendientes de corrección en E.01 y E.02 (los hace el equipo)
1. E.02 dice «carga por mar y por tierra». La ficha dice carga aérea y marítima.
2. E.02: verificar «ISO/IEC 27001:2022» (no 2700).
3. Tablas de supuestos de E.01 y E.02 vacías: Unidad de Seguridad, firmantes simulados, y presupuesto 2028–2029 sujeto a aprobación.
4. E.01, bloque «Organización asignada», plan de trabajo, acuerdos y casillas de compromiso: vacíos.
5. E.01 dice «desvío de cargos de más de 200.000$». La ficha dice robo de un contenedor, USD 240 000, cubierto en parte por el seguro.
6. E.02 trata los USD 500 000 de 2028–2029 como firmes. La ficha dice «sujeto a aprobación».
7. E.02 A.3: se llena en la v1.1, cuando BIA_P05 esté cerrado.

## 7. Decisiones de diseño del BIA (Guillermo + Joseph)
- **Procesos (nombres estándar, iguales en P01–P07):** P-01 Planificar y dar seguimiento a embarques (TMS) · P-02 Controlar inventario en bodegas (WMS) · P-03 Crear y transmitir declaraciones aduaneras · P-04 Dar visibilidad de la carga a clientes (Portal) · P-05 Gestionar usuarios y equipos · P-06 Gestionar conexiones con terceros. P05 de Joseph debe adoptar estos nombres (D1).
- **Áreas y dueños (por cargo, supuesto):** Gerencia de Carga Aérea · Gerencia de Almacenamiento · Gerencia de Aduanas · TI. Un solo dueño por proceso.
- **Ventanas:** P-01 a P-04 de la ficha. P-05 y P-06 = 24/7 como supuesto S-nn.
- **Firmantes simulados:** Guillermo Molina = Director General (aprueba umbral y valida); Erick Pineda = responsable de seguridad. Un mismo integrante cubre dos roles: declararlo en un supuesto.
- **Métricas declaradas (P02 §4):** P-01 MTPD 24 / RTO 8 / WRT 4 / RPO 4 · P-02 24 / 6 / 4 / 4 · P-03 24 / 8 / 6 / 4 · P-04 72 / 12 / 4 / 24 (horas). MTPD de P-05 y P-06: propuesta 10 h (D3).
- **Costo (P02 §8):** ingreso por hora = % del ingreso ÷ horas de operación al año × 1,5 (temporada alta): TMS 75 % ÷ 8 760 h, WMS 15 % ÷ 4 992 h, aduanal 10 % ÷ 4 056 h. Personal = personas × costo de la ficha; alterno = 50 % de recargo.
- **Valoración (P02 §9):** AV = 7 % de margen × ingreso atribuible + USD 300 000 de reposición (900 000 ÷ 3 sistemas); portal = 10 % del margen del TMS. EF = pérdida de 72 h ÷ AV. SLE-01 a SLE-04 (cifrado 72 h: TMS, WMS, aduanal, portal) y SLE-05 (exposición de 60 000 titulares, USD 18 000).
- **P03:** umbral nivel 4 (Grave), aprobado 29/10/2026 (antes de la matriz, D4). Costo del corte: 4 h = costo por hora × 4; 24 h, 72 h, 1 sem y 1 mes = costo por día × 1, 3, 7 y 30. Ingresos USD 95 000 000.
- **SPOF (P04):** SPOF-01 sin sitio alterno · 02 respaldos en el mismo lugar · 03 un solo enlace de internet · 04 Manhattan sin sustituto · 05 un solo MPLS · 06 Dirección General de Aduanas (externo). Energía y climatización del centro de cómputo: «No», sin dato.
- **Fin de soporte:** Windows Server 2016, .NET 6, PHP 7.4 y MySQL 5.7 llevan fecha y enlace oficial del fabricante, que cada quien debe verificar (no se pudo verificar desde la sesión de la IA). Mientras tanto, «fecha por verificar».
- No incluir facturación ni nómina como procesos: Finanzas es apoyo en E.02.
- Cadena de uso: P04 alimenta E.04 (activos); P02 §9 (SLE-nn), P02 §4 y §8 (MTPD, costo por hora) y los SPOF alimentan E.05.
