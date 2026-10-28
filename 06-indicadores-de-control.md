# 6. Mecanismos de control: estándares e indicadores

El control sigue las cuatro etapas vistas en la Unidad 4: **1) establecer estándares** (las metas M1-M7), **2) medir** el desempeño real, **3) comparar** con el estándar (semáforo) y **4) corregir** los desvíos y retroalimentar la planificación.

Semáforo: 🟢 cumple el estándar · 🟡 desvío tolerable, se analiza · 🔴 desvío crítico, se aplica la acción correctiva.

## A. Desempeño técnico del sistema (auditoría técnica)

| ID | Indicador | Fórmula | Estándar 🟢 | 🟡 | 🔴 | Frecuencia y fuente | Responsable | Acción correctiva |
|---|---|---|---|---|---|---|---|---|
| IC1 | Velocidad de registro (M1) | ventas registradas en ≤ 2 s / total de ventas × 100 | ≥ 95 % | 90–94,9 % | < 90 % | Diaria · log de tiempos del módulo | Soporte de Sistemas | Revisar consultas lentas e índices de la base de datos; ampliar el servidor en la nube |
| IC2 | Sincronización web (M2) | actualizaciones en ≤ 60 s / ventas del local × 100 | ≥ 99 % | 97–98,9 % | < 97 % | Diaria · log de sincronización | Soporte de Sistemas | Revisar la conexión con la tienda online; reprocesar la cola de actualizaciones |
| IC3 | Facturación automática (M3) | facturas Autorizadas / ventas Pagadas × 100 | 100 % | 98–99,9 % | < 98 % | Diaria · VENTA y FACTURA | Facturación y Cobranzas | Emitir las faltantes; revisar la integración con ARCA |
| IC4 | Facturas Pendientes > 24 h | cantidad de FACTURA en estado Pendiente con más de 24 h | 0 | 1–3 | > 3 | Diaria · FACTURA.estado | Facturación y Cobranzas | Contactar a ARCA o al soporte; plan de contingencia |
| IC5 | Rendimiento con volumen (M4) | tiempo de respuesta con 5.000 productos y 300.000 ventas | ≤ 2 s | 2–3 s | > 3 s | Antes de la puesta en marcha y trimestral · prueba de carga | Responsable de Pruebas / Soporte | Optimizar la base de datos antes de habilitar el sistema |
| IC6 | Disponibilidad | horas operativas / horas de atención × 100 | ≥ 99 % | 97–98,9 % | < 97 % | Mensual · monitoreo del servidor | Soporte de Sistemas | Analizar caídas; activar la contingencia de ventas sin conexión |

## B. Procesos de negocio (gestión por procesos)

| ID | Indicador | Fórmula | Estándar 🟢 | 🟡 | 🔴 | Frecuencia y fuente | Responsable | Acción correctiva |
|---|---|---|---|---|---|---|---|---|
| IC7 | Exactitud del stock (M5) | \|stock físico − stock del sistema\| / stock del sistema × 100 | < 2 % | 2–4 % | > 4 % | Mensual · inventario por muestreo vs LOTE | Gerencia de Operaciones | Recontar, ajustar y buscar la causa (robo, error de carga, merma) |
| IC8 | Quiebres de stock | productos activos con stock 0 / productos activos × 100 | ≤ 2 % | 2–5 % | > 5 % | Semanal · PRODUCTO y LOTE | Compras y Abastecimiento | Revisar los stocks mínimos y los plazos de los proveedores |
| IC9 | Mercadería vencida | unidades vencidas descartadas / unidades ingresadas × 100 | ≤ 1 % | 1–2 % | > 2 % | Mensual · LOTE | Depósito y Logística | Controlar la regla de vender primero lo que vence antes; promociones de vencimiento próximo |
| IC10 | Preparación de pedidos online | pedidos despachados en ≤ 24 h hábiles / pedidos pagados × 100 | ≥ 95 % | 90–94,9 % | < 90 % | Semanal · VENTA (canal Online, estado) | Depósito y Logística | Reasignar personal en horarios pico |

## C. Control del proyecto (Gantt y equipo)

| ID | Indicador | Estándar | Fuente | Responsable | Acción correctiva |
|---|---|---|---|---|---|
| IC11 | Cumplimiento de hitos H1-H5 | 100 % en fecha (tolerancia: la holgura de cada tarea) | Gantt y tablero | Líder de Proyecto | Replanificar dentro de la holgura; si afecta el camino crítico, informar a la Dirección |
| IC12 | Avance real vs planificado | ≥ 95 % de lo previsto a la fecha | Tablero (tareas en Listo) | Líder de Proyecto | Reasignar tareas o recursos |
| IC13 | Defectos críticos abiertos | 0 antes de la puesta en marcha (condición del hito H4) | Issues con etiqueta `bug` | Responsable de Pruebas | No se habilita el sistema hasta corregirlos |
| IC14 | Personal capacitado (M7) | 100 % de los 18 empleados | Registro de asistencia | Líder de Proyecto | Capacitación adicional antes del 01/03/2027 |

## D. Trabajo colaborativo (GitHub)

| ID | Indicador | Estándar | Cómo se verifica |
|---|---|---|---|
| IC15 | PR aprobados por un par antes del merge | 100 % | Pestaña *Pull requests* (cerrados) → cada uno con *Approved* |
| IC16 | Commits según la convención `tipo: descripción` | 100 % | Historial de commits |
| IC17 | Historias de usuario terminadas con criterios cumplidos | 3 de 3 al cierre | Tablero en **Listo** e issues cerrados |
| IC18 | Trabajo directo sobre `main` | 0 commits (salvo el inicial) | Gráfico *Insights → Network* |

## E. Auditoría técnica del sistema (lista de verificación)

- [ ] **Permisos por área:** cada usuario modifica solo los datos de su sector (tabla de unidades y entidades de la Entrega 3).
- [ ] **Registro de auditoría (log):** quedan registrados los cambios de precios, las anulaciones de ventas y los ajustes de stock, con usuario, fecha y hora.
- [ ] **Copias de seguridad:** backup diario de la base de datos y prueba mensual de restauración.
- [ ] **Conciliación diaria:** ventas pagadas = facturas Autorizadas + Pendientes.
- [ ] **Protección de datos personales:** cumplimiento de la Ley N.º 25.326 (consentimiento en `acepta_comunicaciones` y acceso restringido a los datos de los clientes).
- [ ] **Seguridad del repositorio:** sin tokens ni contraseñas subidos (`.gitignore`) y revisión de pares en cada Pull Request.
