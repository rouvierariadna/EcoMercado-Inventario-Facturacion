 # EcoMercado · Módulo Integrado de Control de Inventario y Facturación Automatizada

> **Trabajo Práctico Integrador (TPI) · Organización Empresarial**
> Tecnicatura Universitaria en Programación a Distancia (TUP AD) · Universidad Tecnológica Nacional (UTN)

| | |
|---|---|
| **Caso de estudio** | EcoMercado S.R.L. (PyME ficticia de alimentos saludables, con local, depósito y tienda online) |
| **Sistema propuesto** | Módulo Integrado de Control de Inventario y Facturación Automatizada |
| **Integrante** | Rouvier, Ariadna |
| **Docentes** | Prof. Gabriela Martínez (titular) · Prof. Carolina Bruno, Prof. Mario Raúl López, Prof. Andrea Ramos (adjuntos) |
| **Repositorio** | [https://github.com/rouvierariadna/EcoMercado-Inventario-Facturacion](https://github.com/rouvierariadna/EcoMercado-Inventario-Facturacion) |
| **Tablero de gestión** | [GitHub Projects · Backlog EcoMercado](https://github.com/users/rouvierariadna/projects/1) |
| **Estado** | Documentación técnica · Entrega 4 (cierre del TPI) |

---

## 1. Descripción del sistema

EcoMercado vende en su local y en su tienda online, pero hoy controla el stock y emite las facturas de forma semi-manual y separada en cada canal. Por eso aparecen diferencias entre el stock real y el publicado en la web, errores de tipeo en las facturas y falta de información actualizada para la Dirección.

El módulo propuesto resuelve esos problemas:

- **Stock único y en tiempo real** para el local y la web, calculado a partir de los lotes, que descuenta primero el lote que vence antes.
- **Factura electrónica automática**, conectada con el Web Service de ARCA (CAE). Si ARCA no responde, la factura queda *Pendiente* y se reintenta sin frenar la venta.
- **Alertas de reposición** cuando un producto baja de su stock mínimo.
- **Tablero de reportes** para la Dirección: ventas por canal, stock y vencimientos.

Objetivo general (Entrega 2): *desarrollar e implementar, entre noviembre de 2026 y marzo de 2027, el módulo que unifique en tiempo real el stock del local y de la tienda online y automatice la emisión de facturas electrónicas, para reducir los errores operativos y brindar a la Dirección información actualizada para decidir.*

## 2. Contenido del repositorio

```
EcoMercado-Inventario-Facturacion/
├── README.md                     ← portada del proyecto (este archivo)
├── CONTRIBUTING.md               ← reglas de trabajo: ramas, commits y Pull Requests
├── .gitignore
├── .github/
│   ├── pull_request_template.md  ← checklist de revisión de pares
│   └── ISSUE_TEMPLATE/
│       └── historia-de-usuario.md
└── docs/
    ├── 01-caso-de-estudio.md         ← Entrega 1: organización y enfoque sistémico
    ├── 02-planificacion.md           ← Entrega 2: FODA, objetivos, metas y Gantt
    ├── 03-organizacion-y-datos.md    ← Entrega 3: organigrama y diccionario de datos
    ├── 04-proceso-bpmn.md            ← Entrega 4: modelado del proceso (BPMN)
    ├── 05-historias-de-usuario.md    ← Entrega 4: backlog ágil
    ├── 06-indicadores-de-control.md  ← Entrega 4: estándares e indicadores de control
    ├── historias/                    ← una especificación por historia de usuario
    ├── img/                          ← diagramas (BPMN, FODA, Gantt, organigramas)
    └── entregas/                     ← PDF de cada entrega del TPI
```

## 3. Proceso que el sistema automatiza (BPMN)

![Diagrama BPMN del proceso de venta y facturación](docs/img/bpmn-proceso-venta-facturacion.png)

Explicación completa en [`docs/04-proceso-bpmn.md`](docs/04-proceso-bpmn.md).

## 4. Backlog: historias de usuario

| ID | Historia de usuario | Prioridad | Issue |
|---|---|---|---|
| HU1 | Como **vendedor/a del local**, quiero que **al registrar una venta el stock se descuente automáticamente del lote que vence primero**, para **no vender productos sin stock y que la tienda online muestre siempre el stock real**. | Alta | #1 |
| HU2 | Como **responsable de Facturación y Cobranzas**, quiero que **cada venta pagada genere automáticamente su factura electrónica con CAE de ARCA**, para **no cargar comprobantes a mano y cumplir con la normativa fiscal**. | Alta | #2 |
| HU3 | Como **encargado/a de Compras y Abastecimiento**, quiero **recibir una alerta cuando un producto baje de su stock mínimo**, para **reponer a tiempo y no perder ventas por falta de mercadería**. | Media | #3 |

Cada historia es un *issue* del repositorio, vinculado al tablero de [GitHub Projects](https://github.com/users/rouvierariadna/projects/1) con los estados **Por hacer → En progreso → Listo**. Detalle y criterios de aceptación en [`docs/05-historias-de-usuario.md`](docs/05-historias-de-usuario.md).

## 5. Cómo se trabaja en este repositorio

- `main` contiene siempre la versión revisada y aprobada. **No se trabaja directamente sobre `main`.**
- Cada tarea se hace en una **rama secundaria**: `docs/…` (documentación), `feature/…` (funcionalidad), `fix/…` (correcciones).
- Los cambios vuelven a main solo mediante un Pull Request revisado antes del merge (al ser un trabajo individual, la revisión queda documentada con un comentario en cada PR).
- Los mensajes de commit siguen la convención `tipo: descripción en infinitivo` (por ejemplo, `docs: agregar diagrama BPMN del proceso de venta`).

Reglas completas en [`CONTRIBUTING.md`](CONTRIBUTING.md).

## 6. Control del proyecto y del sistema

Los estándares de desempeño surgen de las metas M1 a M7 (Entrega 2) y se controlan con indicadores en semáforo (verde, amarillo, rojo), cada uno con su fuente de datos, frecuencia, responsable y acción correctiva. Detalle en [`docs/06-indicadores-de-control.md`](docs/06-indicadores-de-control.md).

| Indicador clave | Estándar |
|---|---|
| Ventas registradas en 2 s o menos | ≥ 95 % |
| Stock web actualizado en 60 s o menos | ≥ 99 % |
| Ventas facturadas automáticamente con CAE | 100 % |
| Diferencia entre stock físico y registrado | < 2 % |
| Facturas Pendientes con más de 24 h | 0 |
| Pull Requests revisados y comentados antes del merge | 100 % |

---

## 7. Declaración de Uso de IA

Sí, utilicé inteligencia artificial generativa (Gemini y NotebookLM) como herramienta de apoyo. Mi forma de trabajo fue enviarle la información del proyecto (los datos del caso EcoMercado) y pedirle:

- **Los gráficos** del proyecto (matriz FODA, diagrama de Gantt, organigramas, diagrama BPMN y gráfico de ramas), a partir de los datos que yo había definido.
- **Borradores de redacción** a partir de esa información, que después revisé y ajusté.
- **Algún que otro diseño para optimizar las mejoras planteadas**, por ejemplo la contingencia cuando ARCA no responde o la alerta de reposición que no frena la venta.
- **Orientación para seguir la ruta correcta en GitHub** (ramas, commits, Pull Requests y tablero).

Las decisiones sobre el caso EcoMercado son mías, y la responsabilidad sobre la veracidad y la coherencia de lo entregado también.

### 7.1 Pedidos realizados a la IA

| Uso | Pedido realizado (resumido) | Qué hice yo con el resultado |
|---|---|---|
| Gráficos | Le envié los factores del FODA y le pedí la matriz | Revisé que cada factor estuviera en el cuadrante correcto (interno o externo) |
| Gráficos | Le envié las tareas, duraciones, precedencias y responsables y le pedí el diagrama de Gantt con el camino crítico | Controlé las fechas, el feriado y el receso de fin de año |
| Gráficos | Le envié las áreas y la dotación y le pedí el organigrama piramidal vertical (línea continua para la autoridad y de trazos para el staff) | Verifiqué las reglas de la norma (Unidad 4) y la dotación de 18 personas |
| Gráficos | Le envié el proceso de venta y facturación y le pedí el diagrama BPMN con pools, lanes y compuertas para las excepciones | Revisé que cumpliera las reglas de la notación (Unidad 5) |
| GitHub | "¿Qué pasa si no tengo compañero para revisar el Pull Request?" · "¿Qué revisa la persona si no hay nada subido?" | Hice yo misma todas las operaciones en GitHub |

### 7.2 Revisión crítica y correcciones propias

- Revisé que cada gráfico mostrara exactamente los datos que yo había definido.
- Comprobé que el diagrama BPMN respetara las reglas de la notación: flujos de mensaje solo entre pools, compuertas con una pregunta y salidas etiquetadas, actividades con verbo en infinitivo, y eventos de inicio y de fin.
- Comparé las metas, los indicadores de control y las entidades con mis entregas anteriores, para que el proyecto fuera coherente de punta a punta.
- Como el trabajo es individual, en cada Pull Request dejé un comentario de revisión antes del merge, aclarando que reviso mi propio trabajo.


### 7.3 Límites y riesgos

La IA puede equivocarse o inventar datos ("alucinaciones"). Por eso no tomé ninguna cifra, norma ni fecha sin compararla con mis entregas y con el material de la cátedra. Cualquier error que haya quedado es responsabilidad mía.
