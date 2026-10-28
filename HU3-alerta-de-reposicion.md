# HU3 · Alerta de reposición por stock mínimo

**Como** encargado/a de Compras y Abastecimiento, **quiero** recibir una alerta cuando un producto baje de su stock mínimo, **para** reponer a tiempo y no perder ventas por falta de mercadería.

**Prioridad:** Media · **Meta:** M5 · **Gantt:** 3.5 · **Lanes BPMN:** Módulo, Compras y Abastecimiento · **Pool externo:** Proveedor

## Criterios de aceptación
- [ ] Después de cada descuento de stock, si el stock total del PRODUCTO (suma de sus LOTE) queda por debajo de `stock_minimo`, se genera una alerta.
- [ ] La alerta muestra el producto, el stock actual y el stock mínimo.
- [ ] La alerta **no detiene** la venta (en BPMN es un evento intermedio de señal).
- [ ] No se repite la alerta del mismo producto hasta que se registre su reposición.
- [ ] Desde la alerta, Compras puede generar la orden de compra al proveedor.

## Datos involucrados
PRODUCTO (`stock_minimo`), LOTE (`cantidad_disponible`).
