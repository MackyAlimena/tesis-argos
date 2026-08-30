---
name: estado
description: Panel de situación de la tesis ARGOS en 30 segundos. Usar cuando la autora pregunta "cómo voy", "dónde estoy parada", "estoy atrasada", "cuántas horas llevo", "qué tengo pendiente" o quiere una foto general antes de un checkpoint con el tutor. Compara semana real vs calendario, horas acumuladas vs 320, capítulos con y sin borrador, triggers vencidos y entregas próximas. Solo lectura.
---

# Estado

Foto de situación. **Solo lectura: no edita nada, nunca.** Se responde en menos de un minuto de lectura.

> **La regla que le da valor:** todo se verifica contra el repo. Un capítulo "en progreso" que no tiene archivo
> es un capítulo que no existe. Un HECHO declarado en el diario cuyo artefacto no está en disco es un hallazgo,
> y va arriba de todo.

## Qué leer

1. **`ROADMAP.md` §4** — ubicá la semana por rango de fechas (no por aritmética). Esa es la semana en la que el
   plan dice que estás.
2. **`kb/diario/`** — última entrada escrita. Esa es la semana en la que **realmente** estás.
   **La brecha entre 1 y 2 es el dato más importante del panel.** Semanas sin entrada = deriva silenciosa.
3. **`kb/diario/README.md`** — tabla de horas: acumulado, Δ por semana, reserva consumida.
4. **`ROADMAP.md` §3** — mapeo artefacto→capítulo. Para cada capítulo que ya debería tener borrador según la
   fase transcurrida, verificá si existe el archivo en `docs/05-tesis-final/`. §6 lo dice explícito:
   *un capítulo sin borrador en su fase es una alarma, no un atraso menor.*
5. **`ROADMAP.md` §5** — dependencias D1–D7 con sus fechas. Marcá vencidas y las que vencen en ≤ 30 días.
6. **Entregas formales** — `kb/context.md` §14: 01/09/2026, 15/09/2026, 23/02/2027, defensa jun–jul 2027.
   Verificá contra `docs/` si el entregable existe.
7. **`git log`** de las últimas 2–3 semanas: qué se tocó de verdad.

## Qué devolvés

```
📍 S07 · 12–18/10/2026 · Fase F1 (Diagnóstico)
   Última entrada de diario: S06 → 1 semana sin registrar

⏱️  HORAS
   38 h / 320 (11,9 %) · esperado a esta altura: 42 h → −4 h
   Reserva: 30 h de 30 intactas
   Δ últimas 3 semanas: +1, +2, +1 → el presupuesto de F1 puede estar corto

📄 CAPÍTULOS
   Cap. 4 (S09) · sin borrador · falta 1 semana ⚠️
   Cap. 5–10 · no corresponde todavía

📅 PRÓXIMA ENTREGA
   Checkpoint con tutor S09 (26/10) · en 2 semanas · requiere BL-01 + cap. 4 borrador

⏰ DEPENDENCIAS
   🔴 D1 · export de PRs · vencía 09/10 · SIN RECIBIR → trigger de Plan B activo
   🟠 D2 · IS-01 completo · vence 11/10 · en curso

🎯 LO QUE IMPORTA ESTA SEMANA
   <una a tres líneas, no más>
```

Adaptá las secciones a lo que aplique: si no hay diario todavía, decilo en vez de fingir una serie. Si algo no se
puede determinar, escribí "no determinable" y por qué — **nunca estimes un número que no leíste**.

## Cómo interpretás

- **Horas esperadas** = suma de las horas presupuestadas de todas las semanas transcurridas según `ROADMAP.md` §2
  y §4, no un promedio lineal (las semanas tienen 4, 6, 8 o 12 h).
- **Δ positivo sostenido** (3+ semanas) → el presupuesto de la fase está mal estimado. Es tema de checkpoint.
- **Δ negativo sostenido** → o vas adelantada, o hay trabajo que no se está registrando. Preguntá cuál de las dos.
- **Reserva consumida sin trigger declarado** (`ROADMAP.md` §6) → señal de alcance creciendo. Nombralo.
- **Más de 2 semanas sin entrada de diario** → 🔴. No es un olvido administrativo: el diario es anexo de la
  memoria y mitigación del doble rol. Ofrecé `/cierre-semana` para las semanas faltantes.

## Reglas

- **No edites, no propongas plan, no arregles nada.** Para planificar está `/semana`; para cerrar,
  `/cierre-semana`; para revisar una entrega, `/entrega`. Esta skill informa.
- **Sin optimismo.** Si está atrasada, se dice con el número. Un panel que tranquiliza no sirve para decidir.
- Sin narración ni preámbulo: el bloque, y una línea final de qué importa esta semana.
