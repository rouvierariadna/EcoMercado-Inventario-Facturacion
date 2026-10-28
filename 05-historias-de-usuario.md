# 5. Backlog ágil: historias de usuario

Las historias de usuario están escritas en formato formal y se gestionan como *issues* vinculados al tablero de **GitHub Projects** con tres columnas: **Por hacer → En progreso → Listo**.

| ID | Historia | Prioridad | Metas | Gantt | Especificación |
|---|---|---|---|---|---|
| HU1 | Como **vendedor/a del local**, quiero que **al registrar una venta el stock se descuente automáticamente del lote que vence primero**, para **no vender productos sin stock y que la tienda online muestre siempre el stock real**. | Alta | M1, M2, M5 | 3.1, 3.3, 3.4 | [HU1](historias/HU1-descuento-de-stock.md) |
| HU2 | Como **responsable de Facturación y Cobranzas**, quiero que **cada venta pagada genere automáticamente su factura electrónica con CAE de ARCA**, para **no cargar comprobantes a mano y cumplir con la normativa fiscal**. | Alta | M3 | 3.2 | [HU2](historias/HU2-facturacion-automatica.md) |
| HU3 | Como **encargado/a de Compras y Abastecimiento**, quiero **recibir una alerta cuando un producto baje de su stock mínimo**, para **reponer a tiempo y no perder ventas por falta de mercadería**. | Media | M5 | 3.5 | [HU3](historias/HU3-alerta-de-reposicion.md) |

## Flujo de estados en el tablero

| Estado | Cuándo pasa a ese estado | Evidencia en el repositorio |
|---|---|---|
| **Por hacer** | Se crea el issue y se agrega al tablero | Issue abierto |
| **En progreso** | Se crea la rama de la historia y se empieza a trabajar | Rama `docs/huN-…` con commits |
| **Listo** | Se aprueba y se fusiona el Pull Request que dice `Closes #N` | Issue cerrado automáticamente y PR fusionado |
