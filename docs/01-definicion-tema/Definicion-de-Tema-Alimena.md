# Definición de Tema — Trabajo de Grado

**Universidad Austral · Facultad de Ingeniería**
**Ingeniería en Informática — Orientación Gestión · Plan 2023**
**Profesora a cargo:** Gabriela Robiolo
**Ciclo lectivo:** 2026–2027

> Entregable formal correspondiente a la consigna de definición de tema: (1) nombre del
> proyecto, (2) nombre y nota del Director que acepta la dirección, (3) participantes.
> La entrega es individual, aunque el trabajo pueda realizarse en grupo.

---

## 1. Nombre del Proyecto

**ARGOS — *Autonomous Risk & Governance Oversight for Software***

**Título académico completo:**
*Gobernanza de agentes de IA en el desarrollo de software: autonomía graduada y evidencia proporcional.*

**Síntesis del tema (una página):**

Los marcos vigentes de gobernanza de inteligencia artificial —ISO/IEC 42001:2023, el *AI Risk
Management Framework* del NIST y el Reglamento (UE) 2024/1689— fueron diseñados para gobernar la
IA **como producto**. Cuando la IA agéntica se incorpora al **proceso de desarrollo de software**,
el objeto gobernado se desplaza: la IA deja de ser lo que la organización entrega y pasa a
integrar el proceso que produce *todo* su software, incluidos los sistemas que no contienen IA
alguna. El riesgo, en consecuencia, deja de estar confinado al sistema con IA y se propaga a la
totalidad de lo entregado.

El mecanismo por el cual ese desplazamiento degrada el control es aritmético. Un agente produce
en minutos el volumen de cambio que una persona producía en días, mientras que quien aprueba
conserva la misma jornada laboral. La revisión sustantiva deja de entrar en el tiempo disponible
y la supervisión humana (*Human-in-the-Loop*) se degrada en silencio, hasta que el registro de
aprobación conserva su prolijidad formal pero detrás de la firma ya no hay lectura efectiva
(*rubber stamping*).

**Claim del trabajo:**

> La supervisión humana solo es real si es verificable. Todo nivel de autonomía delegado a un
> agente de software debe contar con un nivel de evidencia proporcional que permita reconstruir
> *ex post* quién decidió qué. Sin evidencia proporcional, el HITL opera como una ficción de
> cumplimiento.

**Artefactos a producir:**

| # | Artefacto | Propósito |
|---|---|---|
| **A0** | Criterios de gobernabilidad de topologías agénticas | Estructurar enjambres de agentes de modo que existan costuras naturales de inspección humana. |
| **A1** | Taxonomía de riesgos del desarrollo agentizado | Clasificar amenazas específicas (*slopsquatting*, fuga de contexto, degradación de revisión). |
| **A2** | Matriz Autonomía × Control (niveles A0–A4) | Parametrizar compuertas y controles obligatorios según la libertad delegada al agente. |
| **A3** | Telemetría + motor evaluador de conformidad + tablero | Recolectar trazas en CI/CD, evaluar conformidad automáticamente y exponer KRIs a la dirección. |
| **V** | Validación empírica pre/post + panel Delphi | Medir sobre un caso de estudio real en PyME (*reconstruction tests* de PRs) y validar externamente. |

**Marco metodológico:** *Design Science Research* (Peffers et al.; Hevner et al.) combinado con
investigación-acción en caso único (Yin; Runeson & Höst) y validación cualitativa por panel
Delphi. Ver `kb/adrs/ADR-001-metodologia-dsr-y-caso-unico.md`.

**Marco ético:** encíclica *Magnifica Humanitas* (León XIV, 2026), sobre la custodia de la
persona humana frente al paradigma tecnocrático y la distinción entre elección algorítmica y
decisión moral. Desarrollo completo en el Informe Ético y Social (`docs/02-informe-etico/`).

---

## 2. Director del Proyecto

**Director:** Marcos Giagnorio
**Rol:** Director / Tutor académico del Trabajo de Grado
**Aceptación de la dirección:** correo electrónico transcripto a continuación.

> ⚠️ **PENDIENTE DE COMPLETAR ANTES DE LA ENTREGA.**
> Pegar aquí, textualmente y sin editar, el correo donde consta la aceptación de la dirección
> (encabezados incluidos: remitente, destinatario, fecha, asunto). Este bloque no se redacta:
> se transcribe el correo real.

```text
De:      Marcos Giagnorio <...>
Para:    Macarena Alimena <...>
Fecha:   ...
Asunto:  ...

[ Transcripción textual del correo de aceptación ]
```

*(En la versión Word que se entrega, conviene además insertar la captura de pantalla del correo
debajo de la transcripción.)*

---

## 3. Participantes del Proyecto

| Participante | Rol | Carrera / Orientación | Legajo |
|---|---|---|---|
| Macarena Alimena | Autora — trabajo individual | Ingeniería en Informática, Orientación Gestión | *(completar)* |

El proyecto se desarrolla de forma individual: una única participante. La consigna admite grupos
de hasta dos personas, pero el alcance definido —cuatro artefactos más validación empírica
pre/post sobre un caso único— está dimensionado y presupuestado en horas para una sola autora
(320 h de ejecución, ver `ROADMAP.md` §0).

**Caso de estudio:** organización PyME de desarrollo de software donde la autora participa del
proceso de desarrollo, lo que habilita el acceso al historial de *pull requests* y el control
sobre el despliegue de la intervención. El tratamiento de datos históricos y su anonimización
están definidos en `kb/adrs/ADR-006-carga-horaria-y-gestion-de-datos-historicos.md`.

---

## Anexo — Trazabilidad de la entrega

| Hito | Fecha | Estado |
|---|---|---|
| **H0** · Definición de tema (este documento) | Agosto 2026 | En preparación |
| **H1** · Plan de Trabajo de Grado | 01/09/2026 | En curso — `docs/03-plan-de-trabajo/` |
| **H2** · Informe Ético y Social | 15/09/2026 | Pendiente — `docs/02-informe-etico/` |
| **H3** · Pitch de Tesis | 23/02/2027 | Pendiente — `docs/04-pitch-tesis/` |
| **H4** · Defensa final | Jun–Jul 2027 | Pendiente — `docs/05-tesis-final/` |

Cronograma completo, ventanas de medición y criterios pre-registrados: `ROADMAP.md`.
