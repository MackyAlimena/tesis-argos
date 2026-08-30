---
name: entrega
description: Revisa y pule una entrega formal de la tesis ARGOS antes de mandarla - Plan de Trabajo, Informe Ético, pitch, capítulo, artefacto vN o página de estado de checkpoint. Usar cuando la autora dice "revisá esta entrega", "está lista para mandar", "pulí esto", "qué me falta" o menciona una fecha de entrega. Chequea completitud contra la plantilla oficial, consistencia cruzada de números y fechas, y simula las preguntas del tribunal.
---

# Pulir una entrega

Revisión adversarial de un documento que está por salir del repo. **No es una corrección de estilo: es un
control previo a que lo lea la cátedra, el tutor o el tribunal.**

## La línea que no cruzás

> **Podés reescribir lo que ya existe. No podés escribir lo que falta.**

Pulir una oración que la autora escribió, sugerir un corte, señalar una ambigüedad, proponer una redacción
alternativa concreta: sí. Redactar una sección vacía, inventar un argumento que no está, completar un hueco con
prosa plausible: **no**. Un hueco se marca como hueco y lo llena ella.

Es la misma distinción que sostiene la tesis: autonomía graduada. Y es lo que hace que la declaración de uso de
IA del Informe Ético sea verdad.

## 1. Identificá la entrega y su rúbrica

| Entrega | Rúbrica contra la que se mide | Fecha |
|---|---|---|
| **Plan de Trabajo** — `docs/03-plan-de-trabajo/Plan-de-Trabajo-Alimena.md` | `docs/templates/Plan-de-trabajo-template.md`, sección por sección | **01/09/2026** |
| **Informe Ético y Social** — `docs/02-informe-etico/` | `docs/templates/Lineamientos-Informe-Etico.md` + las 5 preguntas mapeadas en `kb/context.md` §10.1 + matriz E1–E10 | **15/09/2026** |
| **Pitch de Tesis** — `docs/04-pitch-tesis/` | `kb/context.md` §17 (el pitch en tres tamaños) | 23/02/2027 |
| **Capítulo** — `docs/05-tesis-final/` | Mapeo artefacto→capítulo de `ROADMAP.md` §3 | Fin de su fase |
| **Artefacto vN + página de estado** | Definición de HECHO de la semana del checkpoint (`ROADMAP.md` §4) | S09, S13, S17, S22, S29, S34, S37, S40 |

Si no está claro cuál es, preguntá. No revises a ciegas.

## 2. Primera pasada — completitud

Recorré la plantilla oficial **sección por sección** y marcá: presente / incompleta / ausente. Sé literal: si la
plantilla pide "Arquitectura (1 diagrama)", un párrafo describiendo la arquitectura **no** es un diagrama.

Para el Plan de Trabajo, verificá además lo que `ROADMAP.md` S01 exige explícitamente:
- §0 del ROADMAP embebido (320 h, ventanas, criterios).
- **Los cinco criterios pre-registrados figuran con número** (C1…C5). Esto no es opcional: pre-registrarlos es la
  mitigación #1 del doble rol, y si no están numerados en el documento entregado, no están pre-registrados.
- Bibliografía en APA, **solo con referencias verificadas**.

## 3. Segunda pasada — consistencia cruzada (la más importante)

Un documento escrito a lo largo de semanas se desincroniza solo. Extraé **todo número y toda fecha** del
documento y contrastalos contra la fuente canónica. Cualquier discrepancia es un hallazgo, no un detalle.

**Números canónicos** (fuente: `ROADMAP.md` §0 — si el documento dice otra cosa, el documento está mal):

| | Valor |
|---|---|
| Carga horaria | 320 h = 8 h/sem × 40 sem · reserva 30 h |
| Ventana de ejecución | S01 31/08/2026 → S40 06/06/2027 · receso S18–S19 |
| C1 | Δ ≥ 40 puntos porcentuales de TRD (pre < 25 %, post ≥ 80 %) |
| C2 | 0 % de discrepancia (tolerancia cero) |
| C3 | Reducción ≥ 30 % · umbral < 60 s por cada 100 líneas |
| C4 | Deterioro ≤ 15 % (guardrail DORA) |
| C5 | IQR ≤ 1 en escala 1–5 · ≥ 75 % de ítems en ronda 2 |
| T0 / T1 | 15/02/2027 · 15/03/2027 (piso absoluto T1: 29/03) |
| Ventanas | PRE 01/03/2026→14/03/2027 · POST 15/03/2027→16/05/2027 |
| Muestras | N ≥ 60 PRs post · 40 PRs reconstruction (20 pre / 20 post) · 8 expertos Delphi (se invitan 12) |
| Entregas | 01/09/2026 · 15/09/2026 · 23/02/2027 · defensa jun–jul 2027 |

Verificá también:
- **El claim** dice lo mismo que en `kb/context.md` §3. No una variante parecida.
- **Los cuatro artefactos** se llaman igual que en el README (A0, A1, A2, A3) y describen lo mismo.
- **Toda referencia citada está verificada.** Cruzá contra
  `docs/03-plan-de-trabajo/BIBLIOGRAFIA-pendiente-de-verificacion.md`: si una B1–B10 aparece citada en el
  documento y sigue sin verificar, **es un bloqueante, no una observación**. Delegá al subagente
  `verificador-bibliografico` si hace falta resolverlo en el momento.
- **Nada contradice un ADR** de `kb/adrs/`.

## 4. Tercera pasada — defensa

Leé el documento como lo va a leer alguien que quiere encontrarle el punto flojo. Para cada afirmación fuerte,
preguntá: *¿esto está sostenido acá adentro, o depende de algo que el lector no tiene?*

Priorizá los cuatro flancos declarados (doble rol, n=1, C1 binario, C2 con tolerancia cero) y devolvé **las
preguntas que te haría el tribunal**, no tu opinión sobre el texto.

## 5. Devolvé esto

```
PLAN DE TRABAJO · entrega 01/09/2026 · faltan 2 días

🔴 BLOQUEANTE  (no se entrega así)
- <hallazgo> → <qué hacer, en una línea>

🟠 IMPORTANTE  (debería resolverse antes de mandar)
- …

🟡 MENOR  (mejora, no bloquea)
- …

❓ LO QUE TE VAN A PREGUNTAR
- …

✂️ PULIDO CONCRETO
- §Motivación, párr. 3: "<texto actual>" → "<propuesta>"  (razón: …)
```

Ordenado por severidad, con la fecha de entrega y los días restantes arriba de todo. Si no hay bloqueantes,
decilo en la primera línea — no inventes hallazgos para justificar la revisión.

## 6. Reglas

- **Los huecos se marcan, no se rellenan.** Ver la línea de arriba.
- **No toques los parámetros congelados** de `ROADMAP.md` §0 para que "cierren" con el documento. Si hay
  discrepancia, el que está mal es el documento.
- **No propongas alcance nuevo.** Estás revisando lo que hay contra lo que se pidió.
- Si el documento requiere firma del tutor (Plan de Trabajo), avisá cuántos días de margen quedan para que Marcos
  lo lea. Un documento perfecto entregado sin tiempo de lectura no está listo.
- Aplicá los cambios de la sección ✂️ solo si la autora lo pide explícitamente, uno por uno.
