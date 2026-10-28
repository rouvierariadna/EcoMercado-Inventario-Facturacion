# HU1 · Descuento automático de stock por lote

**Como** vendedor/a del local, **quiero** que al registrar una venta el stock se descuente automáticamente del lote que vence primero, **para** no vender productos sin stock y que la tienda online muestre siempre el stock real.

**Prioridad:** Alta · **Metas:** M1, M2, M5 · **Gantt:** 3.1, 3.3, 3.4 · **Lanes BPMN:** Ventas, Módulo

## Criterios de aceptación
- [ ] Antes de cobrar, el sistema verifica que la suma de `cantidad_disponible` de los LOTE del producto alcance; si no alcanza, la venta no se confirma y se avisa al vendedor.
- [ ] Al confirmar la venta, la cantidad se descuenta del LOTE con la `fecha_vencimiento` más próxima; si ese lote no alcanza, se completa con el siguiente.
- [ ] Cada DETALLE_VENTA guarda el `id_lote` del que salió la mercadería (trazabilidad).
- [ ] El registro de la venta y el descuento tardan **≤ 2 s** en el 95 % de los casos (M1).
- [ ] El stock publicado en la tienda online se actualiza en **≤ 60 s** (M2).

## Datos involucrados
PRODUCTO, LOTE, VENTA, DETALLE_VENTA (diccionario de datos, Entrega 3).
