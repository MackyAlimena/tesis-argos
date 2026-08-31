# Onboarding — Colaborador externo

> **Para quién:** cualquiera que llegue al repo por fuera del trabajo de grado — consultor externo, revisor,
> auditor, lector técnico, o alguien evaluando si puede aportar.
> **Cómo se usa:** pegale este archivo a tu agente (Claude Code, Antigravity, Cursor, el que uses) y pedile
> *"seguí este onboarding"*. En Claude Code alcanza con `/onboarding-externo`. Sin agente: leelo de arriba a abajo.
> **Cuánto tarda:** ~10 min de lectura dirigida, más lo que dure el frente que elijas.
>
> Si sos el **tutor académico**, usá [`tutor.md`](tutor.md) en su lugar.

---

## 0. Instrucciones para el agente

Este onboarding es **conversacional y ramificado**. No vuelques todo de una: el objetivo es entender qué vino a
hacer la persona y llevarla al frente de trabajo correcto con el contexto mínimo suficiente.

Reglas:
- **No edites nada** hasta que la persona elija un frente y confirme que quiere trabajar en él.
- Si un archivo referenciado no existe o está vacío, **decilo**. No lo rellenes ni lo inventes.
- Las fechas del repo son absolutas: comparalas contra hoy antes de afirmar que algo está pendiente.
- Nada de este repo se comparte fuera sin que lo pida quien te está hablando. Hay datos de una empresa real
  involucrados (ver §4).

---

## 1. Qué es esto, en 60 segundos

Contale a la persona, con tus palabras, después de leer `README.md` y `kb/context.md` §§1–3:

- Es un **trabajo de grado** de Ingeniería en Informática (Universidad Austral), no un producto ni una startup.
  Defensa: junio–julio 2027.
- **El gap:** ISO/IEC 42001, NIST AI RMF y el EU AI Act gobiernan la IA *como producto*. Cuando la IA agéntica
  entra al *proceso* de desarrollo, el riesgo se propaga a todo el software de la organización, incluso al que no
  tiene nada de IA. La analogía está en `kb/context.md` §2.2: **todos regulan el auto; el problema está en la fábrica.**
- **El claim:** la supervisión humana solo es real si es verificable. A cada nivel de autonomía delegado a un
  agente le corresponde un nivel de evidencia proporcional que permita reconstruir *ex post* quién decidió qué.
  Sin eso, el human-in-the-loop es una ficción de cumplimiento.
- **Lo que produce:** cuatro artefactos (A0 topologías gobernables · A1 taxonomía de riesgos · A2 matriz
  autonomía × control · A3 telemetría + motor de conformidad + tablero) más una validación empírica pre/post en
  una PyME real, más validación externa por auditoría de certificación ISO/IEC 27001 y entrevistas a especialistas.

---

## 2. Cómo está armado el repo

Leelo de `README.md` (sección *Estructura del Repositorio*) y verificá contra el filesystem real. Lo mínimo que
hay que saber:

| Carpeta | Qué es | Cómo se trata |
|---|---|---|
| `kb/` | Base de conocimiento. `context.md` es **el documento maestro**. | **Working docs:** se editan en su lugar, no se archivan versiones. |
| `kb/adrs/` | Las seis decisiones estructurales ya tomadas, con su porqué. | Inmutables. Una decisión nueva es un **ADR nuevo** que supersede, nunca una edición del viejo. |
| `ROADMAP.md` | Cronograma S01–S40, parámetros congelados, criterios C1–C5. | §0 está **congelado**. No se toca sin ADR. |
| `docs/` | Entregables formales de la facultad. | Tienen fecha de entrega. No son borradores libres. |
| `src/` | Implementación del artefacto A3. | Techo duro de 44 h (ADR-004): es investigación, no una plataforma. |
| `data/`, `evaluation/` | Dataset del experimento y validación del método. | Ver §4 antes de tocar. |

**Antes de opinar sobre cualquier decisión de diseño, revisá `kb/adrs/`.** Es muy probable que ya esté explicada
ahí — y si tu objeción no está contemplada, eso sí es aporte.

---

## 3. Los cuatro frentes abiertos — elegí uno

Presentale esta tabla a la persona y **preguntale cuál quiere tomar**. Está ordenada por urgencia real.
La versión viva está en `README.md` (sección *Research abierto*): verificá contra ella antes de mostrarla.

| Prioridad | Frente | Qué hace falta concretamente |
|---|---|---|
| 🔴 **Bloqueante** | **Verificación bibliográfica** | 10 referencias (B1–B10) entraron sin verificar contra la fuente. Confirmar autoría, año, sede y DOI — o **eliminarlas**. No reformularlas. B3, B6 y B7 son las más frágiles. → [`BIBLIOGRAFIA-pendiente-de-verificacion.md`](../03-plan-de-trabajo/BIBLIOGRAFIA-pendiente-de-verificacion.md) |
| 🟠 **Alta** | **Estado del arte / vigilancia** | Barrer ICSE, FSE, ASE, MSR, CHI, FAccT, USENIX buscando trabajo previo que ya resuelva el claim — **o que lo contradiga**. Toda ficha usa la plantilla. → [`estrategia-bibliografica-y-vigilancia.md`](../../kb/literature/estrategia-bibliografica-y-vigilancia.md) · [`TEMPLATE-ficha-lectura.md`](../../kb/literature/TEMPLATE-ficha-lectura.md) |
| 🟠 **Alta** | **Mapeo normativo** | `kb/standards/` está vacío. Falta mapear la taxonomía A1 y la matriz A2 contra ISO/IEC 42001 Anexo A, ISO/IEC 27002 y NIST SP 800-218A. Es lo que convierte a ARGOS en un perfil de implementación y no en un marco inventado. → [`kb/standards/`](../../kb/standards/) |
| 🟡 **Media** | **Cobertura del Catálogo Giagnorio (2026)** | Cruzar las 14 categorías del catálogo contra lo que ARGOS gobierna: qué está cubierto, qué no, qué se implementó sin decisión explícita. → [`catalogo-agentes-ia-giagnorio-2026.md`](../../kb/literature/catalogo-agentes-ia-giagnorio-2026.md) |

**Si la persona vino a romper el diseño** (revisor, auditor, segunda opinión metodológica), llevala directo acá —
son los flancos que la propia autora declara:

1. **Sesgo de doble rol** — diseña el marco, lo implementa en su empresa y mide el resultado. Mitigaciones
   declaradas: parámetros congelados antes de medir, auditor externo y ciego, auditoría externa de certificación, diario
   de investigación. *¿Alcanzan?*
2. **Caso único (n=1)** — una PyME. Límites en [`ADR-001`](../../kb/adrs/ADR-001-metodologia-dsr-y-caso-unico.md).
3. **C1 como apuesta binaria** — Δ ≥ 40 puntos de TRD, un solo umbral sostiene el claim entero.
4. **C2 con tolerancia cero** — 0 % de discrepancia entre `trace.json` y Git/CI puede ser inalcanzable en la práctica.

---

## 4. Reglas no negociables

Estas valen para cualquiera que toque el repo, con o sin agente:

- **Nada entra a la bibliografía sin verificar contra la fuente.** Ni una cita, ni un DOI, ni un año. La tesis
  argumenta sobre evidencia verificable: una referencia inventada acá no es un error de estilo, es una
  contradicción con el propio claim. **Si no pudiste verificarla, se elimina — no se reformula.**
- **No se tocan los parámetros congelados** de `ROADMAP.md` §0. Están congelados antes de medir a propósito: es
  la mitigación central del sesgo de doble rol. Cambiarlos después invalida el experimento.
- **Toda decisión estructural va a un ADR.** Si tu aporte cambia método, alcance o criterios, el entregable es un
  ADR nuevo, no una edición silenciosa.
- **La tesis la redacta Macarena, sola.** El aporte externo es investigación, verificación y crítica — no
  redacción de la memoria. Si te piden producir texto de tesis, frená y decilo.
- **Datos sensibles:** `data/raw/` contiene un dataset histórico anonimizado de PRs de una empresa real y está
  fuera de git por `.gitignore`. No lo publiques, no lo copies fuera del repo, no lo pegues en servicios externos.

---

## 5. Cómo entregar

- **Trabajo de contenido** (fichas, mapeos, verificaciones) → archivo nuevo en la carpeta que corresponde,
  siguiendo la plantilla si existe.
- **Cambios estructurales** → ADR en `kb/adrs/`, numerado correlativo, con *contexto · decisión · consecuencias*.
- **Crítica al diseño** → no hace falta archivo: llevásela directo a Macarena. Si la crítica prospera, se
  convierte en ADR.
- Trabajá en una rama y proponé el cambio; no pushees a `main`.

---

## 6. Cierre

Cerrá preguntando explícitamente: **¿qué frente tomás, y con qué fecha?** Y si la persona todavía no sabe si
puede aportar, ofrecele leer `ROADMAP.md` §5 (dependencias críticas) — ahí se ve qué está bloqueado y por quién.
