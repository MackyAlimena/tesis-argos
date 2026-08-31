# Onboarding — Tutor / Director de Trabajo de Grado

> **Para quién:** Marcos Giagnorio, tutor académico de este trabajo de grado.
> **Cómo se usa:** pegale este archivo a tu agente (Claude Code, Antigravity, Cursor, el que uses) y pedile
> *"seguí este onboarding"*. En Claude Code alcanza con `/onboarding-tutor`. Sin agente: leelo de arriba a abajo,
> los links son los mismos.
> **Cuánto tarda:** ~15 min de lectura dirigida.

---

## 0. Instrucciones para el agente

Ejecutá este onboarding **en orden**, y no lo hagas en silencio: después de cada bloque, contale a la persona
qué leíste y qué encontraste. El objetivo no es resumir el repo, es dejar al tutor en condiciones de **discutir y
firmar**.

Reglas:
- **No edites nada** durante el onboarding. Es lectura. Si al final el tutor quiere dejar feedback, ver §5.
- Si un archivo referenciado no existe o está vacío, **decilo explícitamente** en vez de rellenarlo. Un
  directorio vacío acá es información (ej: `kb/standards/` vacío = trabajo pendiente declarado).
- Las fechas del repo son absolutas. Comparalas contra la fecha de hoy y avisá qué está vencido o por vencer.

---

## 1. El argumento en una página

Leé, en este orden:

1. `README.md` — el gap, el claim y los cuatro artefactos.
2. `kb/context.md` §§1–3 — título, problema (en criollo, por analogía y en académico) y el claim.

**Devolvé al tutor:** el claim en una frase, y cuál es la diferencia entre "gobernar la IA como producto" y
"gobernar la IA como parte del proceso que produce el software". Si no podés explicar esa diferencia sin jerga,
volvé a leer §2.2.

---

## 2. Contra qué se mide (lo que hay que aprobar antes de medir)

Leé `ROADMAP.md` §0 completo — parámetros congelados y criterios C1–C5.

Esto es lo más importante de todo el onboarding. Los parámetros están **congelados a propósito**: fijarlos antes
de medir es la mitigación #1 del sesgo de doble rol. Una vez que se mide, ya no se tocan.

**Devolvé al tutor, en tabla:**

| Qué | Para revisar |
|---|---|
| **C1** | Δ ≥ 40 puntos de TRD. El claim entero se sostiene o se cae acá. ¿El umbral es defendible ante tribunal, o es alto/bajo? |
| **C2** | 0 % de discrepancia entre `trace.json` y Git/CI. Tolerancia cero. ¿Es alcanzable en un pipeline real? |
| **C3** | Reducción ≥ 30 % del rubber stamping. ¿La operacionalización (< 60 s por cada 100 líneas) mide lo que dice medir? |
| **C4** | Guardrail DORA, deterioro ≤ 15 %. Declarado como guardrail, no como objetivo. |
| **C5** | Validación externa (ADR-007): auditoría ISO/IEC 27001 sin no conformidades sobre el proceso intervenido **+** acuerdo de ≥ 3 de cada 4 especialistas entrevistados. Sustituye al panel Delphi. **Es el criterio a revisar con más atención: cambió después del borrador inicial.** |

Y marcá las **fechas duras**: T0 = 15/02/2027, T1 = 15/03/2027, piso absoluto de T1 = 29/03/2027.

---

## 3. Las decisiones ya tomadas (y por qué)

Listá `kb/adrs/` y leé el título y la sección *Decisión* de los seis ADR. No hace falta leerlos enteros ahora.

Los seis, en una línea cada uno, para que el tutor sepa dónde meter mano:

- **ADR-001** — DSR + investigación-acción en caso único (n=1). Acá están declarados los límites de generalización.
- **ADR-002** — nombre y alcance de ARGOS.
- **ADR-003** — quality gates gobernados vs. tradicionales.
- **ADR-004** — desactivación del agente auditor generalista (techo duro contra la deriva a producto).
- **ADR-005** — calibración y verificación del orquestador.
- **ADR-006** — carga horaria (320 h) y gestión de datos históricos.

**Devolvé al tutor:** cuál de los seis es el más discutible desde su rol de director, y por qué.

---

## 4. Qué está esperando de vos (el bloque accionable)

Esto es lo que el trabajo **no puede avanzar sin el tutor**. Revisalo contra la fecha de hoy.

| # | Qué | Estado | Fecha |
|---|---|---|---|
| T1 | Mail de aceptación como Director de Trabajo de Grado | Pendiente | — |
| T2 | Lectura y **firma** del Plan de Trabajo formal — [`docs/03-plan-de-trabajo/Plan-de-Trabajo-Alimena.md`](../03-plan-de-trabajo/Plan-de-Trabajo-Alimena.md) | Borrador listo, requiere firma | **Entrega 01/09/2026** |
| T3 | Informe Ético y Social — `docs/02-informe-etico/` | Vacío | **15/09/2026** |
| T4 | Checkpoints de fase (artefacto vN + una página de estado) | Recurrentes | S09, S13, S17, S22, S29, S34, S37, S40 |

Además, hay un frente donde el tutor es **fuente primaria**, no revisor: la
[cobertura del Catálogo Giagnorio (2026)](../../kb/literature/catalogo-agentes-ia-giagnorio-2026.md) — cruzar las
14 categorías contra lo que ARGOS efectivamente gobierna. Es insumo directo del capítulo 4.

**Devolvé al tutor:** esta tabla, con el estado real verificado en el repo (no el que dice esta guía) y marcando
qué está vencido.

---

## 5. Dónde el diseño es más atacable

El aporte más útil del tutor es acá. Presentale los cuatro flancos declarados por la propia autora
(están en `README.md` y en `kb/context.md` §8.1):

1. **Sesgo de doble rol** — diseña el marco, lo implementa en su empresa y mide el resultado. Mitigaciones:
   parámetros congelados antes de medir, auditor externo y ciego, auditoría externa de certificación, diario de investigación.
   *La pregunta abierta: ¿alcanzan?*
2. **Caso único (n=1)** — una PyME. Límites en ADR-001.
3. **C1 como apuesta binaria** — un solo umbral sostiene el claim.
4. **C2 con tolerancia cero** — puede ser inalcanzable en la práctica.

Y sumá los riesgos con trigger fechado de `ROADMAP.md` §6, en particular el **Plan B si no llegan los datos
históricos de PRs** (trigger: 09/10/2026).

---

## 6. Cómo dejar feedback en el repo

Reglas del repo, respetalas:

- **Feedback estructural** (cambia método, alcance o criterios) → **ADR nuevo** en `kb/adrs/`, numerado, con
  contexto, decisión y consecuencias. No se edita un ADR viejo: se escribe uno que lo supersede.
- **Feedback de contenido** → se edita el working doc **en su lugar** (`kb/context.md`, `ROADMAP.md`). No se
  archivan versiones.
- **Referencias bibliográficas** → nada entra sin verificar contra la fuente. Ver
  [`docs/03-plan-de-trabajo/BIBLIOGRAFIA-pendiente-de-verificacion.md`](../03-plan-de-trabajo/BIBLIOGRAFIA-pendiente-de-verificacion.md).
  Una cita falsa acá no es un error de estilo: contradice el claim de la tesis.
- **Nunca modifiques los parámetros congelados de `ROADMAP.md` §0** sin un ADR que lo justifique. Ese es
  justamente el punto de congelarlos.

> **La tesis la escribe Macarena, sola.** El rol del tutor es dirigir, cuestionar y firmar — no redactar. Si el
> agente detecta que se le está pidiendo producir contenido de tesis, avisá y frená.

---

## 7. Cierre

Terminado el recorrido, ofrecé al tutor tres caminos concretos:

- **"Quiero revisar el Plan de Trabajo para firmarlo"** → abrir `docs/03-plan-de-trabajo/Plan-de-Trabajo-Alimena.md`
  y contrastarlo contra `docs/templates/` y `ROADMAP.md`.
- **"Quiero atacar el diseño"** → §5, empezando por C1 y el doble rol.
- **"Quiero ver el cruce con mi catálogo"** → `kb/literature/catalogo-agentes-ia-giagnorio-2026.md`.
