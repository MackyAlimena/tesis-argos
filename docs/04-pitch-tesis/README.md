# HITO 3 — Pitch de Tesis · 23/02/2027

Carpeta de trabajo del pitch. Se abre ahora para que el material se vaya depositando a medida
que se produce, no la semana previa.

| Dato | Valor |
|---|---|
| **Fecha** | 23/02/2027 (S26 del roadmap) |
| **Preparación** | S25 · 15–21/02/2027 · 6 h — deck + demo ensayada y cronometrada |
| **Ejecución** | S26 · 22–28/02/2027 · 4 h |
| **Formato** | Deck de 12 slides + demo en vivo |
| **Peso en el plan** | 1,3 % de las 320 h |

## Estructura acordada del deck

1. **Problema** — la fábrica, no el producto: la IA se corrió al proceso de desarrollo y el
   riesgo se propagó a todo el software entregado.
2. **Claim** — autonomía graduada exige evidencia proporcional; sin ella el HITL es una ficción
   de cumplimiento.
3. **BL-01 en gráficos** — la línea de base medida sobre el caso real. Es el corazón del pitch:
   el número concreto ("diffs de N líneas de origen agéntico aprobados en T segundos, sin
   comentarios, en el X % de los casos"). Fuente: nota BL-01 de S09 (26/10–01/11/2026).
4. **Los cuatro artefactos** — A0 topologías · A1 taxonomía · A2 matriz autonomía × control ·
   A3 telemetría, motor y tablero.
5. **Calibración del orquestador** — ADR-005: por qué el instrumento de medición es confiable.
6. **Plan de validación y cronograma a defensa** — T0 (15/02/2027, instrumentación silenciosa),
   T1 (15/03/2027, intervención plena), ventana POST de 9 semanas, panel Delphi, N ≥ 60 PRs.

## Demo

A la fecha del pitch, T0 ya está corriendo (15/02/2027): telemetría pasiva, sin gates y sin
cambio de política. La demo muestra el recolector y el tablero con datos reales de la ventana
PRE, no un *mock*. Debe estar ensayada y cronometrada antes del 21/02.

## Contenido de la carpeta

| Subcarpeta | Qué va acá |
|---|---|
| `deck/` | Fuente y export del deck de 12 slides. |
| `demo/` | Guion de la demo, dataset congelado para la corrida, plan B si falla el vivo. |
| `feedback-tribunal/` | Devoluciones del tribunal, transcriptas el mismo día. |

## Regla de cierre

El feedback del tribunal no queda acá: se registra en `kb/` como insumo directo de las fases
F6 (panel Delphi + *reconstruction test* PRE) y F7 (*reconstruction test* POST + análisis
pre/post). Esta carpeta guarda el original; `kb/` guarda la decisión que se tomó a partir de él.

## Dependencias aguas arriba

- **BL-01** (S09, 26/10–01/11/2026) — sin el número de la línea de base no hay slide 3.
- **A2 · Matriz Autonomía × Control** (F4, enero 2027) — debe estar cerrada.
- **T0 activo** (15/02/2027) — condición para que la demo tenga datos reales.
