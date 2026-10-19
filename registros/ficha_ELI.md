# Ficha de ELI — Express Logistics International (catálogo n.º 22, IG3)

Texto extraído de forma automática (pdftotext -layout) de `Docs/02_Catalogo/Catalogo_Empresas_Proyecto_Final_ESEN_2026.pdf`, sección 4.22, páginas 95–98. **Fuente única de datos de la organización.** Si algo se ve cortado o una tabla se ve desalineada, se verifica contra el PDF original. Este archivo no se edita a mano.

```text
4.22 Express Logistics International (ELI)

  Grupo de Implementación asignado: IG3. Trazabilidad de carga internacional y datos de clientes corporativos,
  con operación distribuida y fraude dirigido en la cadena logística.

Datos básicos de la empresa
  • Sector: Logística y Transporte de Carga.
  • Tamaño: Grande (850 empleados).
  • Ubicación: Centro de distribución principal cerca del aeropuerto, oficinas aduaneras y bodegas en puntos
    estratégicos.
  • Misión: Ofrecer soluciones logísticas integrales y confiables para el comercio internacional, manejando la carga
    de nuestros clientes con la máxima seguridad y eficiencia.
  • Visión: Ser el operador logístico 3PL/4PL líder en la región, impulsado por la visibilidad y la automatización de la
    cadena de suministro.
  • Estructura Organizacional Básica: Dirección General, Gerencia de Carga Aérea, Gerencia de Carga Marítima,
    Gerencia de Aduanas, Almacenamiento, TI.
Modelo de negocio y procesos críticos
  • Servicios Principales: Agenciamiento de carga internacional, trámites aduanales, almacenamiento y
    distribución.
  • Clientes: Importadores y exportadores de diversos sectores (retail, manufactura, farmacéutica).
Procesos Críticos (4):
        – 1. Sistema de Gestión de Transporte (TMS): Planificación y seguimiento de todos los embarques.
        – 2. Sistema de Gestión de Almacenes (WMS): Control de inventario de los clientes en las bodegas.
        – 3. Plataforma de Gestión Aduanal: Creación y transmisión de declaraciones de importación/exportación a
          la autoridad aduanera.
        – 4. Plataforma de Visibilidad para Clientes: Portal web que permite a los clientes rastrear su carga en
          tiempo real.

  • Dependencia Tecnológica: Crítica. La integridad de los datos de los manifiestos de carga es vital. Un error o
    manipulación puede resultar en multas, retrasos o pérdida de mercancía.
Infraestructura tecnológica inicial
  • Sistemas: TMS y WMS de Manhattan Associates, sistema aduanal de desarrollo propio, portal de clientes en
    Azure.
  • Red y Comunicaciones: Extensa integración con sistemas de aerolíneas, navieras y la Dirección General de
    Aduanas.
  • Madurez y Controles Actuales: Nivel bajo. El desarrollo del sistema aduanal se hizo sin considerar la seguridad,
    haciéndolo vulnerable a inyección de datos. La autenticación en el portal de clientes es débil, y los datos de
    rastreo podrían ser interceptados o manipulados. No tienen un plan de respuesta a incidentes.
Ficha de datos del cliente (entregada en la reunión de arranque)
Datos que el cliente entrega al equipo, con el valor probable y el rango mínimo–máximo que considera posible. Con
ellos el equipo calcula el BIA y los análisis siguientes; ningún dato de esta ficha se reemplaza por un supuesto.
Economía
 Dato                           Valor probable                  Rango                Detalle

                                                                                     Carga aérea 40 %, carga marítima 35 %,
 Ingresos anuales               USD 95 M                        85–105 M             almacenaje y distribución 15 %, trámites
                                                                                     aduanales 10 %

 Margen operativo               7%                              5–9 %                Sobre ingresos

                                Septiembre a noviembre,
                                                                                     Embarques frente al mes promedio: 1,5 (1,3–
 Temporada alta                 importaciones para fin          —
                                                                                     1,7)
                                de año

                                650 declaraciones                                    2 400 embarques activos; USD 180 M de
 Volumen de transacciones                                       550–750
                                aduaneras por día                                    inventario de clientes en bodegas (150–210 M)

                                60 000 destinatarios de
                                                                                     4 800 clientes empresariales con datos fiscales
 Datos personales               paquetería con dirección        50 000–70 000
                                                                                     y de contacto
                                y teléfono

 Costo de notificar a un
                                USD 0,30                        0,20–0,45            Correo y SMS
 titular

 Costo de reposición de                                         750 000–1 100        Servidores del sistema aduanal, del TMS y del
                                USD 900 000
 equipos clave                                                  000                  WMS

 Contenedor retenido en         USD 150 por día por                                  Almacenaje y demora que cobran el puerto y la
                                                                100–220
 puerto                         contenedor                                           naviera

Operación por proceso
 Proceso                             Sistema de gestión de transporte (TMS)

 Horario                             24 horas, todos los días

 Personal en turno y costo           110 coordinadores de carga por turno; costo cargado USD 8 por hora (±15 %)

 Procedimiento alterno               Seguimiento por correo y hojas de cálculo con navieras y aerolíneas

 Penalizaciones                      Almacenaje y demora de contenedores en puerto: USD 150 por día por contenedor

 Proceso                             Sistema de gestión de transporte (TMS)

 Consecuencias que describe el       4 h: embarques sin seguimiento; clientes llaman · 24 h: reservas de espacio perdidas · 72 h:
 dueño (4 h · 24 h · 72 h · 1        contenedores retenidos en puerto con cargos · 1 semana: clientes trasladan cuentas · 1
 semana · 1 mes)                     mes: pérdida de clientes grandes

 Proceso                             Sistema de gestión de almacenes (WMS)

 Horario                             Bodegas de lunes a sábado de 6:00 a 22:00

 Personal en turno y costo           260 bodegueros por turno; costo cargado USD 4,50 por hora (±15 %)

 Procedimiento alterno               Preparación de pedidos con listas impresas y conteo manual; capacidad al 40 %

                                     SLA con clientes farmacéuticos: despacho en 24 horas; crédito del 5 % de la factura mensual
 Penalizaciones
                                     si se incumple

 Consecuencias que describe el       4 h: despachos atrasados · 24 h: incumplimiento del SLA farmacéutico · 72 h: inventario sin
 dueño (4 h · 24 h · 72 h · 1        control; riesgo de robo · 1 semana: diferencias de inventario reclamadas · 1 mes: pérdida de
 semana · 1 mes)                     clientes farmacéuticos

 Proceso                             Plataforma de gestión aduanal

 Horario                             Lunes a sábado de 7:00 a 20:00; aduana aérea 24 horas

 Personal en turno y costo           45 tramitadores; costo cargado USD 9 por hora (±15 %)

 Procedimiento alterno               Digitación directa en el sistema de la Dirección General de Aduanas; capacidad al 30 %

                                     Multas aduaneras por declaraciones tardías o erróneas; una manipulación de declaraciones
 Penalizaciones                      pone en riesgo la licencia de agente aduanero y la certificación de Operador Económico
                                     Autorizado

 Consecuencias que describe el       4 h: declaraciones en cola · 24 h: carga retenida en aduana · 72 h: cargos de almacenaje y
 dueño (4 h · 24 h · 72 h · 1        multas · 1 semana: reclamos de clientes · 1 mes: si hubo manipulación de datos, suspensión
 semana · 1 mes)                     de la licencia

 Proceso                             Plataforma de visibilidad para clientes (portal de rastreo)

 Horario                             24 horas, todos los días

 Personal en turno y costo           8 personas de soporte digital; costo cargado USD 10 por hora (±15 %)

 Procedimiento alterno               Estado de la carga por correo a solicitud

 Penalizaciones                      Ninguna contractual; los clientes grandes exigen el portal en su contrato

 Consecuencias que describe el       4 h: consultas por teléfono y correo · 24 h: centro de atención saturado · 72 h: quejas de
 dueño (4 h · 24 h · 72 h · 1        clientes grandes · 1 semana: renegociación de contratos · 1 mes: si se filtró el rastreo, robo
 semana · 1 mes)                     de carga de alto valor

Tecnología

 Elemento                              Situación actual

                                       Manhattan TMS y WMS en sus instalaciones, sobre Windows Server 2019 con Microsoft SQL
 Transporte y almacenes
                                       Server 2019

 Sistema aduanal                       Desarrollo propio en PHP 7.4 con MySQL 5.7

 Portal de clientes                    Azure App Service con .NET 6 y Azure SQL Database; usuario y contraseña propios

 Integraciones                         EDI con aerolíneas y navieras por SFTP; transmisión a la aduana por internet

                                       Active Directory en Windows Server 2016; Microsoft 365; estaciones con Windows 10 y
 Oficina e identidad
                                       Windows 11

 Red                                   Centro de distribución y dos bodegas unidas por MPLS

Respaldos y continuidad
 Sistema                               Situación actual

 TMS y WMS                             Respaldo nocturno a disco y copia semanal a cinta guardada en el centro de distribución

 Sistema aduanal                       Respaldo diario en el mismo servidor

 Portal                                Respaldo automático de Azure SQL Database con retención de 7 días

 Sitio alterno                         No existe

Incidentes de los últimos años
 Año          Incidente                                                             Duración                      Costo

              Robo de un contenedor de electrónicos tras consultas de                                             USD 240 000 cubiertos
 2023                                                                               —
              rastreo con credenciales de un cliente reutilizadas                                                 en parte por el seguro

              Errores del sistema aduanal ante entradas manipuladas en                                            Sin declaraciones
 2024                                                                               Semanas
              un formulario; se detectó al revisar bitácoras                                                      alteradas confirmadas

                                                                                                                  USD 50 000 en multas y
 2025         Ransomware en estaciones de tramitadores                              3 días
                                                                                                                  almacenaje

 2026         Caída del enlace de internet con la aduana                            7 horas                       Carga retenida un día

Organización y presupuesto
 Dato                                  Valor

                                       Dirección General; Gerencias de Carga Aérea, Carga Marítima, Aduanas y Almacenamiento;
 Organigrama                           TI (22 personas); Finanzas, que incluye RR. HH.; Legal y Cumplimiento Aduanero; auditoría
                                       interna de una persona. No existe una unidad de seguridad de la información

 Presupuesto aprobado para             2027: USD 700 000 (450 000 de inversión y 250 000 de operación). 2028 y 2029: USD 500
 seguridad                             000 por año, sujeto a aprobación

 Arranque del programa de
                                       Aprobado por la Dirección General para el lunes 4 de enero de 2027
 seguridad

 Dato                                  Valor

                                       Código Aduanero Uniforme Centroamericano y su reglamento; normativa de la Dirección
 Cumplimiento que el cliente           General de Aduanas; certificación de Operador Económico Autorizado; Ley para la
 reconoce                              Protección de Datos Personales; buenas prácticas de almacenamiento exigidas por clientes
                                       farmacéuticos

Controles que ya existen
 Familia                               Estado actual

 Desarrollo                            El sistema aduanal se construyó sin validación de entradas ni revisión de seguridad

 Portal                                Autenticación solo con usuario y contraseña; sin bloqueo por intentos fallidos

 Respuesta a incidentes                No existe un plan

 Antimalware                           Antivirus en estaciones y servidores Windows

 Seguridad física                      Videovigilancia y guardias en bodegas, exigidos por la certificación aduanera

```
