# HU2 · Factura electrónica automática

**Como** responsable de Facturación y Cobranzas, **quiero** que cada venta pagada genere automáticamente su factura electrónica con CAE de ARCA, **para** no cargar comprobantes a mano y cumplir con la normativa fiscal.

**Prioridad:** Alta · **Meta:** M3 · **Gantt:** 3.2 · **Lanes BPMN:** Módulo, Facturación y Cobranzas · **Pool externo:** ARCA

## Criterios de aceptación
- [ ] Cuando la VENTA pasa a estado "Pagada", el sistema solicita el CAE a ARCA.
- [ ] El tipo de comprobante (A o B) se define según la `condicion_iva` del CLIENTE.
- [ ] Con CAE, la FACTURA queda "Autorizada" en **≤ 10 s** y se entrega con el ticket (local) o por e-mail (online).
- [ ] Si ARCA no responde, la FACTURA queda "Pendiente", se reintenta cada 15 minutos y **la venta no se bloquea**.
- [ ] Facturación y Cobranzas ve la lista de facturas pendientes; ninguna debe superar las 24 h.
- [ ] El 100 % de las ventas pagadas tiene factura sin carga manual (M3).

## Datos involucrados
VENTA, CLIENTE, FACTURA (campos `cae`, `estado`, `tipo_comprobante`).
