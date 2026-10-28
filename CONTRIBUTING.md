# Guía de trabajo colaborativo

Estas reglas aseguran que el repositorio tenga un historial ordenado, revisado y fácil de auditar (trazabilidad: quién hizo qué, cuándo y por qué).

## 1. Ramas (branches)

| Rama | Uso | Ejemplo |
|---|---|---|
| `main` | Versión revisada y aprobada. **No se trabaja directamente sobre ella.** | — |
| `docs/…` | Documentación nueva o actualizada | `docs/hu1-descuento-stock` |
| `feature/…` | Nueva funcionalidad del sistema | `feature/alerta-reposicion` |
| `fix/…` | Corrección de errores | `fix/calculo-subtotal` |

- Una rama por tarea o historia de usuario.
- Nombres en minúscula, sin acentos y con guiones.
- Después del merge, la rama se elimina.

## 2. Mensajes de commit

Formato: `tipo: descripción breve en infinitivo` (máximo ~70 caracteres).

| Tipo | Cuándo se usa |
|---|---|
| `docs` | Documentación |
| `feat` | Funcionalidad nueva |
| `fix` | Corrección |
| `chore` | Configuración o mantenimiento del repositorio |

✔️ `docs: agregar diagrama BPMN del proceso de venta (TO-BE)`
✔️ `docs: definir criterios de aceptación de la HU2`
❌ `cambios` · ❌ `arreglos varios` · ❌ `prueba`

Commits **chicos y frecuentes**: cada commit es un cambio con sentido propio.

## 3. Pull Requests (PR)

1. Abrir el PR desde la rama de trabajo hacia `main`.
2. Título claro y descripción completa: **qué** se cambió, **por qué** y **cómo revisarlo**.
3. Si resuelve una historia de usuario, escribir `Closes #N` (así el issue se cierra y pasa a **Listo** en el tablero).
4. Pedir la revisión de **al menos un par** (*Reviewers*).
5. Quien revisa deja comentarios y elige **Approve** o **Request changes**.
6. Solo con la aprobación se hace **Merge** y se elimina la rama.

## 4. Tablero de gestión

Cada historia de usuario es un *issue* vinculado al tablero de GitHub Projects:

**Por hacer** → (se crea la rama y se empieza a trabajar) → **En progreso** → (se aprueba y se fusiona el PR) → **Listo**
