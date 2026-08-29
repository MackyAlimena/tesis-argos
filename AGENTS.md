# AGENTS.md — instrucciones para agentes de IA en este repo

> Este archivo lo leen Claude Code, Antigravity, Cursor, Codex y compañía.
> Si sos una persona: te sirve igual, pero probablemente quieras el [`README.md`](README.md).

**Qué es este repo:** el trabajo de grado **ARGOS** — *Gobernanza de agentes de IA en el desarrollo de software:
autonomía graduada y evidencia proporcional*. Ingeniería en Informática, Universidad Austral. Autora: Macarena
Alimena. Tutor: Marcos Giagnorio. Defensa: junio–julio 2027.

Es una **tesis**, no un producto: la mayor parte del contenido son documentos, no código.

---

## Onboarding

Si la persona con la que estás hablando acaba de clonar el repo, o pide contexto, arrancá por acá:

| Si la persona es… | Seguí | En Claude Code |
|---|---|---|
| **el tutor académico / director** (Marcos) | [`docs/onboarding/tutor.md`](docs/onboarding/tutor.md) | `/onboarding-tutor` |
| **cualquier otra persona** — consultor, revisor, auditor, lector | [`docs/onboarding/externo.md`](docs/onboarding/externo.md) | `/onboarding-externo` |

Esos dos archivos contienen el procedimiento completo. Leé el que corresponda y ejecutá sus instrucciones.
Si no sabés cuál corresponde, **preguntá** antes de arrancar.

---

## Rituales de trabajo (solo la autora)

Estas herramientas son para el trabajo semanal de la tesis, no para el onboarding de visitantes:

| | Qué | Cuándo |
|---|---|---|
| `/semana` | Abre la semana: ubica S01–S40 por fecha en `ROADMAP.md`, arma el plan de las horas presupuestadas y avisa triggers. | Lunes |
| `/cierre-semana` | Verifica la Definición de HECHO **contra el repo**, registra horas y escribe la entrada del diario en `kb/diario/`. | Viernes |
| `verificador-bibliografico` *(subagente)* | Verifica referencias contra la fuente original. Devuelve VERIFICADA / NO LOCALIZADA; nunca reformula. | Antes de incorporar cualquier cita |

El **diario de investigación** (`kb/diario/`) es anexo de la memoria y mitigación declarada del sesgo de doble
rol. Se asiste, no se delega: las secciones de rol se llenan entrevistando a la autora, nunca inventando.

---

## Reglas del repo (valen siempre, con o sin onboarding)

1. **Nada entra a la bibliografía sin verificar contra la fuente.** Ni una cita, ni un DOI, ni un año, ni una
   sede. La tesis argumenta sobre evidencia verificable: una referencia inventada contradice el claim del propio
   trabajo. Si no se pudo verificar, **se elimina — no se reformula**. Ver
   [`docs/03-plan-de-trabajo/BIBLIOGRAFIA-pendiente-de-verificacion.md`](docs/03-plan-de-trabajo/BIBLIOGRAFIA-pendiente-de-verificacion.md).
2. **Los parámetros congelados de [`ROADMAP.md`](ROADMAP.md) §0 no se tocan.** Están fijados antes de medir a
   propósito: es la mitigación central del sesgo de doble rol. Modificarlos después invalida el experimento.
   Cualquier cambio requiere un ADR que lo justifique.
3. **Toda decisión estructural va a un ADR** en [`kb/adrs/`](kb/adrs/), numerado, con contexto, decisión y
   consecuencias. Un ADR viejo no se edita: se escribe uno nuevo que lo supersede.
4. **Los working docs de [`kb/`](kb/) se actualizan en su lugar.** No se archivan versiones ni se crean
   `context-v2.md`.
5. **La memoria de tesis la redacta únicamente la autora.** Los agentes ayudan con investigación, verificación,
   estructura y crítica — no producen el texto de la tesis. Si te lo piden, avisá y frená.
6. **`data/raw/` contiene un dataset anonimizado de PRs de una empresa real**, fuera de git por `.gitignore`.
   No lo publiques, no lo copies fuera del repo, no lo pegues en servicios externos.
7. **Un directorio vacío es información, no un hueco para rellenar.** `kb/standards/` está vacío porque el mapeo
   normativo es trabajo pendiente declarado. No lo inventes.
8. **Las fechas del repo son absolutas.** Compará contra la fecha de hoy antes de afirmar que algo está pendiente
   o vencido.
