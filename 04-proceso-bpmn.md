# 4. Modelado del proceso de negocio (BPMN 2.0)

**Proceso modelado:** venta con control de stock y facturación automática, tal como funcionará **con el módulo** (modelo *TO-BE*).

![BPMN](img/bpmn-proceso-venta-facturacion.png)

## Participantes

| Tipo | Elemento | Rol en el proceso |
|---|---|---|
| Pool externo | **Cliente** | Envía el pedido y el pago; recibe los productos y la factura |
| Pool interno | **EcoMercado S.R.L.** | Contiene el proceso |
| Lane | Ventas (Local y E-commerce) | Registra y cobra la venta; entrega en el local |
| Lane | Depósito y Logística | Arma y despacha los pedidos online |
| Lane | **Módulo de Inventario y Facturación** | Comportamiento automatizado: verifica y descuenta stock, solicita el CAE y emite alertas |
| Lane | Compras y Abastecimiento | Atiende las alertas y genera la orden de compra |
| Lane | Facturación y Cobranzas | Supervisa las facturas que quedaron Pendientes |
| Pool externo | **ARCA** | Autoriza la factura (devuelve el CAE) |
| Pool externo | **Proveedor** | Recibe la orden de compra |

## Flujo estándar (camino feliz)

1. Llega el pedido del cliente (**evento de inicio de mensaje**) y Ventas **registra la venta**.
2. El sistema **verifica el stock disponible por lote** → hay stock.
3. Ventas **cobra la venta** → pago aprobado.
4. **Compuerta paralela**: a la vez, el sistema **descuenta el stock del lote que vence primero** y **solicita el CAE y emite la factura electrónica**.
5. **Compuerta paralela de unión**: se espera a que terminen las dos ramas.
6. **¿Canal de venta?** Local → se entregan los productos con ticket y factura. Online → Depósito arma y despacha el pedido y se envía la factura por e-mail.

## Excepciones contempladas (compuertas exclusivas)

| Compuerta | Excepción | Tratamiento |
|---|---|---|
| ¿Hay stock suficiente? | No | Se informa al cliente → fin *Venta no concretada* |
| ¿Pago aprobado? | No | Fin *Venta anulada* |
| ¿Stock bajo el mínimo? | Sí | **Evento intermedio de señal** "Alerta de reposición": la venta **no se detiene**; Compras inicia su propio flujo (inicio por señal) y envía la orden al Proveedor |
| ¿ARCA devolvió el CAE? | No | La factura queda *Pendiente*; Facturación y Cobranzas la supervisa y un **evento de tiempo** reintenta cada 15 minutos (estrategia DA del FODA) |

## Reglas de la notación aplicadas

- Un pool por participante; los **flujos de secuencia no cruzan pools**.
- Los **flujos de mensaje** (línea discontinua) se usan **solo entre pools**.
- Actividades nombradas con **verbo en infinitivo** y con su tipo: usuario, servicio, script, envío o manual.
- Todas las compuertas exclusivas tienen una **pregunta** y **salidas etiquetadas**; las paralelas abren y cierran en pareja y no llevan nombre.
- Varios **eventos de fin** que aclaran cómo terminó cada camino.
- Un **data store** (base de datos) asociado a las actividades que leen y escriben PRODUCTO, LOTE, VENTA, DETALLE_VENTA y FACTURA.

## Del proceso actual (AS-IS) al proceso con el módulo (TO-BE)

| Paso | Hoy (AS-IS) | Con el módulo (TO-BE) |
|---|---|---|
| Control de stock | Planillas separadas para local y web | Stock único por lote, en tiempo real |
| Venta sin stock | Se descubre después (sobre todo online) | Se detecta antes de cobrar |
| Factura | Carga manual, con errores de tipeo | Automática con CAE; contingencia si ARCA no responde |
| Reposición | Se nota cuando el producto se agota | Alerta automática al bajar del stock mínimo |
| Información para la Dirección | Reportes manuales y atrasados | Tablero en tiempo real |
