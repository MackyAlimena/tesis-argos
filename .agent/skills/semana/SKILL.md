---
name: semana
description: Abre la semana de trabajo de la tesis ARGOS. Usar cuando la autora arranca la semana, pregunta "qué toca esta semana", "por dónde sigo", "en qué semana estoy" o quiere el plan de las 8 h. Ubica la semana S01-S40 en ROADMAP.md por fecha, muestra foco, horas, Definición de HECHO, triggers que vencen y lo que quedó abierto en el diario.
---

# Abrir la semana

Ritual de apertura. **Es lectura y planificación: no ejecutes el trabajo de la semana acá.** La salida es un plan
de 8 h que la autora pueda mirar el lunes y ejecutar el resto de la semana.

## 1. Ubicá la semana

Buscá en `ROADMAP.md` §4 la fila cuyo rango de fechas contiene la fecha de hoy. **No calcules el número de semana
por aritmética** — las fechas están escritas y mandan ellas (S01 arranca el 28/08/2026).

Casos borde, tratalos explícitamente:
- **Receso declarado S18–S19** (28/12/2026–10/01/2027, 0 h): decilo y no armes plan. Ofrecé la entrada de diario con 0 h.
- **Fecha fuera de S01–S40:** decí en qué semana cae la fecha más cercana y preguntá contra cuál quiere trabajar.
- **S26** es el Pitch de Tesis (H3, 4 h), no una semana de fase normal.

## 2. Leé, en este orden

1. La fila de la semana en `ROADMAP.md` §4 — foco, horas, tareas y Definición de HECHO.
2. El encabezado de la FASE a la que pertenece (arriba de la tabla): suele traer una advertencia que cambia cómo
   se lee la semana.
3. `ROADMAP.md` §5 (dependencias críticas) y §6 (riesgos) — filtrá por triggers que vencen **dentro de las
   próximas 3 semanas**.
4. La última entrada de `kb/diario/` — sección *Abierto para la semana que viene* y cualquier HECHO ⚠️ o ❌ que
   se haya reprogramado. Si no hay entradas todavía, decilo.
5. `kb/diario/README.md` — tabla de horas: acumulado y reserva disponible.

## 3. Devolvé esto y nada más

```
S07 · 12–18/10/2026 · Fase F1 · 6 h presupuestadas
Acumulado: 38 h / 320 · Reserva: 30 h intactas

FOCO
<el foco de la fila, en una línea>

DEFINICIÓN DE HECHO (así se te va a medir el viernes)
<textual del ROADMAP>

ARRASTRE DE LA SEMANA PASADA
<de la última entrada del diario, o "nada abierto">

⏰ TRIGGERS EN EL HORIZONTE
<solo los que vencen en ≤3 semanas, con fecha y consecuencia si fallan>

PLAN DE LAS 6 H
1. …  (Xh)
2. …  (Xh)
<bloques concretos que suman las horas presupuestadas, no una lista de deseos>

⚠️ <alerta, solo si hay algo realmente fuera de eje>
```

## 4. Reglas

- **El plan suma exactamente las horas presupuestadas.** Si la Definición de HECHO no entra en esas horas,
  decilo como problema en vez de comprimir la estimación — es información para el checkpoint.
- **No propongas alcance que no esté en el ROADMAP.** La reserva se consume ante un trigger declarado, nunca para
  agregar trabajo. Si creés que falta algo, decilo aparte, marcado como fuera de plan.
- **Verificá el arrastre contra el repo**, no contra lo que dice el diario. Si la entrada anterior declaró algo
  hecho y el archivo no está, esa es la primera línea de tu respuesta.
- Si la semana toca un checkpoint con tutor (S09, S13, S17, S22, S29, S34, S37, S40), avisalo arriba de todo:
  la semana tiene una entrega, no solo trabajo.
- Sé breve. Esto se lee en dos minutos o no se lee.
