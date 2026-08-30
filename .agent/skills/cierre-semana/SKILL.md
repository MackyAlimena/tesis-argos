---
name: cierre-semana
description: Cierra la semana de trabajo de la tesis ARGOS. Usar cuando la autora termina la semana, dice "cerremos la semana", "registrá las horas", quiere escribir la entrada del diario de investigación o verificar si cumplió la Definición de HECHO. Verifica el HECHO contra el repo real, registra horas planificadas vs reales y redacta la entrada semanal separando rol ingeniera de rol investigadora.
---

# Cerrar la semana

Ritual de cierre. Produce **la entrada del diario de investigación**, que va como anexo de la memoria y es la
cuarta mitigación del sesgo de doble rol (`kb/context.md` §8.1).

> **Lo más importante de esta skill:** verificás la Definición de HECHO **contra el filesystem**, no contra lo que
> la autora te cuenta. Si dice que IS-01 está listo, abrís el archivo y contás las columnas. Un cierre complaciente
> no sirve para nada; el valor está en que el veredicto sea verificable.

## 1. Ubicá la semana y su Definición de HECHO

Igual que `/semana`: fila de `ROADMAP.md` §4 por rango de fechas. Copiá la Definición de HECHO **textual, sin
editar** — va citada en la entrada.

## 2. Verificá el HECHO contra el repo

Para cada cosa que la Definición de HECHO exige, buscá la evidencia real:

- ¿El archivo existe? ¿En la ruta que corresponde?
- ¿Tiene la estructura pedida? (ej. S05: "≥1 fila por agente y las 6 columnas completas, sin celdas vacías" →
  contá filas y columnas de verdad)
- ¿El script es re-ejecutable, o solo existe?
- ¿Lo que había que enviar, se envió? Eso no lo podés verificar en el repo: **preguntalo explícitamente** y
  registrá la respuesta como declarada por la autora, no como verificada.
- Mirá también `git log` de la semana: qué se tocó realmente.

**Veredicto en tres estados:** ✅ cumplida · ⚠️ parcial · ❌ no cumplida. Sé estricto. Un ⚠️ honesto en S05 vale
más que un ✅ generoso que explota en S09 delante del tutor.

## 3. Registrá las horas

Preguntá las horas reales trabajadas. Compará contra las presupuestadas de la fila.

- Si hubo **consumo de reserva**, preguntá cuál es el trigger declarado que lo justifica (`ROADMAP.md` §6). Si no
  hay trigger, no es reserva: es sobre-ejecución, y se registra como Δ positivo.
- Un Δ positivo sostenido (3+ semanas) es señal de que el presupuesto de la fase está mal estimado. Decilo.

## 4. Escribí la entrada

Creá `kb/diario/SXX.md` desde `kb/diario/TEMPLATE-entrada.md`. Para las secciones 2–4 **entrevistá a la autora**,
no inventes:

- **Rol ingeniera:** qué decidiste sobre el pipeline o la empresa, que hubieras hecho igual sin tesis.
- **Rol investigadora:** qué decidiste sobre método, artefactos o medición.
- **Dónde se cruzaron:** el bloque que importa. Preguntá directo: *"¿alguna decisión técnica de esta semana afecta
  lo que vas a medir? ¿algo del interés de la investigación empujó una decisión del pipeline?"*. Si la respuesta
  es "ninguno", aceptalo — pero preguntá una vez.

Escribí con la voz de la autora, en primera persona, en español rioplatense. Sobrio y concreto. **Esto es un
registro, no una narración de logros.**

## 5. Actualizá la tabla de horas

Agregá la fila de la semana en `kb/diario/README.md` y recalculá acumulado, reserva disponible y fecha de última
actualización.

## 6. Cerrá con el hand-off

Devolvé en pantalla:

```
S07 CERRADO · 6 h plan / 7 h reales (Δ +1)
HECHO: ⚠️ parcial — <qué falta y a qué semana se reprograma>
Acumulado: 45 h / 320 · Reserva: 30 h intactas

📌 ABIERTO PARA S08
- …

🔴 <alerta de trigger, capítulo sin borrador, o Δ sostenido — solo si aplica>
```

## 7. Reglas

- **Nunca reescribas una entrada vieja para que quede mejor.** Se corrige un error de hecho, nada más. Una semana
  incumplida se queda registrada como incumplida: ese es el valor probatorio del diario.
- **No redactes contenido de tesis acá.** La entrada registra lo que pasó; no adelanta capítulos.
- Si la semana cierra una fase (S09, S13, S17, S22, S29, S34, S37, S40), avisá que corresponde **checkpoint con
  tutor** y que §3 del ROADMAP pide el borrador del capítulo de esa fase. Preguntá si existe.
- Si en la conversación aparece una decisión estructural, marcala en la sección 5 como candidata a ADR. No la
  escribas vos.
