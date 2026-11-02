# context.md — Verdad del proyecto (ELI, Equipo 8)

Última actualización: 2026-10-29. Fuente: lectura de `Entregables/E01`, `Entregables/E02` y `registros/ficha_ELI.md`.
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

## 5. Estado de los entregables (al 2026-10-29)
- E.01 y E.02: llenos por el equipo, sin commit todavía. E.01 tiene abierto el archivo en Word (lock `~$1_...`).
- BIA_P01 a P04 en `Entregables/anexos/`: plantillas **vacías**.
- BIA_P05 a P07, E.03 a E.12: sin empezar.
- Las fechas oficiales de E.01 a E.06 ya pasaron; la forma de entregar lo atrasado la confirma el docente.
- Supuestos: **ninguno numerado aún**. El siguiente es **S-01**.

## 6. Pendientes de corrección en E.01 y E.02 (los hace el equipo)
1. E.02 dice «carga por mar y por tierra». La ficha dice carga aérea y marítima.
2. E.02 dice «ISO/IEC 2700:2022». Debe ser 27001:2022.
3. Tablas de supuestos de E.01 y E.02 vacías. Deben numerarse: Unidad de Seguridad, firmantes simulados, y que el presupuesto 2028–2029 está sujeto a aprobación.
4. E.01, bloque «Organización asignada»: campos vacíos.
5. E.01 dice «desvío de cargos de más de USD 200 000». La ficha dice robo de un contenedor, USD 240 000, cubierto en parte por el seguro. Ajustar la redacción.
6. E.02 trata los USD 500 000 de 2028–2029 como firmes. La ficha dice «sujeto a aprobación».

## 7. BIA_P01, propuesta de trabajo (pendiente de confirmar por el equipo)
- Inventario de 6 procesos: P-01 planificar y dar seguimiento a embarques (TMS), P-02 controlar inventario de clientes en bodega (WMS), P-03 crear y transmitir declaraciones aduaneras, P-04 dar visibilidad de la carga a clientes, P-05 gestionar usuarios y equipos de trabajo, P-06 gestionar conexiones con terceros.
- Áreas: Carga Aérea o Marítima (TMS, a decidir un solo dueño), Almacenamiento, Aduanas, TI.
- Ventanas P-01 a P-04 de la ficha. Ventanas de P-05 y P-06 no están en la ficha: supuesto S-nn.
- Dueños: roles del organigrama; si se pone nombre, es supuesto S-nn, igual en los 7 anexos y en E.03.
- Sección 4 de P01: copiar las 3 exclusiones de E.02.
- No incluir facturación ni nómina como procesos: Finanzas es apoyo en E.02.
