# Trabajo de Grado — Contexto y definición del tema

**Alumna:** Macarena Alimena · Ingeniería en Informática (Univ. Austral), orientación Gestión
**Tutor académico propuesto:** Marcos Giagnorio (en proceso de confirmación administrativa; sinergia con su investigación doctoral)
**Entrega de definición de tema:** viernes 14/08/2026 · **Entrega final:** junio–julio 2027
**Estado de este documento:** working doc. Consolida las decisiones tomadas y feedback de cátedra/tutor. Se actualiza, no se archiva.

---

## 1. Título

> ### Gobernanza de agentes de IA en el desarrollo de software: autonomía graduada y evidencia proporcional

**En inglés:** *Governing AI Agents in Software Development: Graduated Autonomy and Proportional Evidence*

**Palabras clave:** gobernanza de IA; agentes de IA; desarrollo de software; supervisión humana; auditabilidad; ISO/IEC 42001; ISO/IEC 27001.

**Decisiones de título y alcance (alineadas con feedback de cátedra):**
- **"ISO 42001" queda fuera del título:** La tesis no inventa una norma de cero (lo cual sería inverosímil para un trabajo de grado), sino que desarrolla una **extensión/perfil de implementación operacional** para integrar agentes al ciclo de software sobre ISO 42001 e ISO 27001.
- **"SDLC" queda fuera del título:** Sigla en inglés + jerga. "Desarrollo de software" dice lo mismo.

**Alternativas descartadas pero disponibles:**
- *Supervisión humana verificable en el desarrollo de software con agentes de IA* (la más corta; no dice "gobernanza").
- *Gobernanza de la autonomía: control y evidencia en el desarrollo de software con agentes de IA*.
- *Marco de gobernanza para la delegación de tareas de ingeniería a agentes de IA* (la más segura, la más gris).

---

## 2. El problema

### 2.1. En criollo

Hasta hace poco el software lo escribían personas: una escribía, otra leía y aprobaba. Ahora un agente escribe en cinco minutos lo que una persona escribía en tres días — **pero el que aprueba sigue teniendo el mismo día de ocho horas.**

Antes llegaban 5 cambios de 50 líneas por día. Ahora llegan 40 cambios de 500 líneas. La revisión, físicamente, ya no entra. Nadie decide dejar de revisar: la revisión se va degradando sola hasta que el "aprobado por: Juan" sigue igual de prolijo pero atrás ya no hay nadie leyendo.

> **La supervisión humana no se rompe por mala fe. Se rompe por aritmética. Y se rompe sin hacer ruido.**

### 2.2. La analogía que lo explica (autos)

Casi toda la regulación de IA está escrita para **un auto con piloto automático**: la IA está adentro del producto.

Lo que pasa acá es otra cosa: **cambiamos los robots de la línea de montaje.**

- Si falla el piloto automático, falla *ese modelo* de auto. Si el robot de la fábrica se manda una macana, **salen mal todos los autos** — incluidos los modelos que no tienen nada de tecnología.
- Y nadie mira, porque el manual se escribió para el piloto automático.

**Todo el mundo está regulando el auto. El problema está en la fábrica.**

### 2.3. En académico (el gap)

Los marcos de gobernanza de IA vigentes —ISO/IEC 42001, NIST AI RMF, EU AI Act— fueron concebidos para gobernar la IA **en tanto producto** entregado a usuarios. La incorporación de agentes de IA al ciclo de vida del desarrollo de software desplaza el objeto gobernado: la IA deja de ser el producto y pasa a integrar **el proceso que produce todo el software de la organización**, propagando riesgo incluso hacia sistemas que no contienen IA. Para ese escenario no existe hoy ni un modelo de control ni un modelo de evidencia.

---

## 3. El claim (la apuesta de la tesis)

> **La supervisión humana de agentes de IA solo es real si es verificable. Por lo tanto, todo nivel de autonomía delegado a un agente debe tener asociado un nivel de evidencia obligatoria que permita reconstruir *ex post* quién decidió qué. Sin evidencia proporcional, el human-in-the-loop opera como una ficción de cumplimiento.**

**Principio unificador:** *autonomía graduada, evidencia proporcional.*

**Es falsable:** si al medir resulta que las revisiones humanas son profundas incluso sin evidencia obligatoria, el claim se cae. Que se pueda caer es lo que lo hace una tesis.

### 3.1. El razonamiento encadenado (para poder reconstruirlo sin memorizar)

1. La supervisión humana se rompe en silencio, por volumen.
2. Si se rompe en silencio, preguntar "¿supervisaste?" no sirve — todos responden que sí, de buena fe.
3. Lo único que distingue supervisión real de supervisión de cartón es que **quede rastro**.
4. Por lo tanto: sin rastro exigido, no hay supervisión — hay una promesa.
5. Pero exigir rastro máximo siempre mata la productividad que motivó usar agentes. Por eso: **proporcional**. (Analogía: nadie pide factura por un café; sí por transferir $50 millones.)

### 3.2. Qué se sabe y qué no

**Ya está definido (la apuesta):** el problema no se resuelve con más revisores ni prohibiendo agentes, sino **convirtiendo la autonomía en una decisión explícita en lugar de un accidente**. Hoy nadie decidió cuánta libertad tienen los agentes: quedó así por cómo se fue armando el pipeline.

Mecanismo, en cuatro movimientos:
1. **Hacer explícito lo implícito** — nombrar qué nivel de autonomía tiene hoy cada agente.
2. **Acoplar exigencia a autonomía** — más libertad ⇒ más control y más registro.
3. **Automatizar la evidencia** — que salga del pipeline sola. *Si depende de que alguien la cargue a mano, se muere en dos semanas.*
4. **Medir la brecha** entre lo declarado y lo real.

**Lo que se averigua en la tesis (y está bien no saberlo hoy):** dónde van exactamente los cortes entre niveles, qué evidencia alcanza en cada uno, y cuánto mejora efectivamente la trazabilidad al aplicar el marco.

> ⚠️ Una tesis **no** es "no sé la respuesta y la voy a averiguar". Es "tengo una apuesta y voy a probar si aguanta". Nunca decir lo primero en una reunión.

---

## 4. Pregunta de investigación

> **¿Cómo debe extenderse un sistema de gestión de IA conforme a ISO/IEC 42001 para gobernar de forma auditable la delegación de tareas de ingeniería a agentes de IA a lo largo del ciclo de vida del software, preservando la responsabilidad humana y la trazabilidad de la evidencia?**

- **SP1** — ¿Qué riesgos introduce la agentización del desarrollo que las taxonomías actuales de riesgo de IA no cubren?
- **SP2** — ¿Qué controles y qué evidencia mínima requiere cada nivel de autonomía?
- **SP3** — ¿Qué debe registrar un pipeline agentizado para ser auditable *ex post*?
- **SP4** — ¿Qué criterios permiten diseñar una topología de agentes que sea gobernable?
- **SP5** — ¿Qué indicadores permiten a la dirección decidir qué delegar, cuánto y cuándo revertir?

---

## 5. El aporte: cuatro artefactos

| # | Artefacto | En criollo |
|---|---|---|
| **A0** | Criterios de gobernabilidad de topologías agénticas | **Cómo armar el enjambre** para que después se pueda supervisar |
| **A1** | Taxonomía de riesgos del desarrollo agentizado | **La lista ordenada** de formas en que esto puede morder |
| **A2** | Matriz Autonomía × Control (A0–A4) | **La perilla**: a este nivel de libertad, estos controles y este registro |
| **A3** | Modelo de evidencia (telemetría) + Motor evaluador de conformidad + Tablero | **Qué queda anotado**, un **gatekeeper/auditor automatizado** en CI/CD que evalúa la evidencia contra la política, y una pantalla que lo muestra |
| **V** | Medición pre/post + Calibración | **La prueba de que sirve** — sin esto es una opinión bien escrita |

### 5.1. A2 — Matriz Autonomía × Control (borrador)

| Nivel | Qué hace el agente | Control humano | Evidencia obligatoria |
|---|---|---|---|
| **A0** | Sugiere (autocompletado) | Aceptación implícita | Registro de uso |
| **A1** | Redacta el cambio; el humano revisa y firma | Revisión sustantiva obligatoria | Diff + revisor identificado + tiempo de revisión |
| **A2** | Ejecuta dentro de guardrails (tests, refactors acotados) | Aprobación por excepción | Traza completa + política aplicada + resultado de gates |
| **A3** | Autónomo end-to-end en dominio acotado | Supervisión por muestreo + KRIs | Traza + reconstrucción de la decisión + plan de reversión probado |
| **A4** | Autónomo hasta producción | Kill-switch + auditoría continua | Todo lo anterior + evidencia de contención |

Cada celda se mapea a controles del Anexo A de ISO/IEC 42001 y de ISO/IEC 27002.

### 5.2. A0 — La capa de topología (el hallazgo propio)

> **La forma del enjambre decide si el sistema se puede gobernar o no. La arquitectura no es previa a la gobernanza: es la primera decisión de gobernanza.**

Dos configuraciones que funcionan igual de bien pero no son igual de gobernables:

- **A — un agente grande** que agarra el ticket y devuelve el cambio listo (diseña, escribe, testea, documenta). **No hay dónde meter a un humano**: no hay costura. Y no hay dónde capturar evidencia, porque lo que pasó adentro no dejó frontera.
- **B — cinco agentes chicos** que se pasan el trabajo. **Cada pase de mano es un punto de control natural y una frontera de evidencia natural.**

Se eligió la capacidad de supervisar cuando se eligió la topología, meses antes de que apareciera la palabra "gobernanza". **La gobernanza no se le puede atornillar después a una arquitectura que no la admite.**

**Corolario aplicable de inmediato en la empresa:**

> **Un agente que revisa el trabajo de otro agente no es un control.** Si corren sobre modelos parecidos comparten puntos ciegos y fallan en las mismas cosas. Parece segregación de funciones; es duplicación. El concepto de independencia del revisor existe hace décadas en control interno y nadie lo tradujo todavía a agentes.

**Orden de las capas:**

```
Cómo armo el enjambre        → ¿este diseño admite supervisión?   (A0)
        ↓
Cuánta autonomía le doy      → matriz A0–A4                       (A2)
        ↓
Qué controles y qué registro → evidencia proporcional             (A3)
        ↓
Cómo lo mido                 → tablero                            (A3)
```

**Dos advertencias sobre A0:**
1. **No prometer encontrar la combinación ideal de agentes.** Probablemente no exista: depende del producto, del equipo y del riesgo. Prometer eso es prometer lo imposible. Lo que sí se promete es **el criterio para decidir** — dar el criterio en vez de la receta es, textualmente, la diferencia entre gestión e implementación.
2. **No comparar herramientas.** Un benchmark de frameworks de agentes vence en seis meses y la defensa es en 2027. Los criterios de gobernabilidad no vencen; los rankings sí.

### 5.3. El mecanismo técnico vs. el aporte de tesis: Quality Gates tradicionales vs. Quality Gates Gobernados

Cuando un ingeniero de software u orientador técnico escucha hablar de compuertas en CI/CD, dice: *"eso se llama Quality Gates"*. La afirmación es **técnicamente correcta en el mecanismo de ejecución, pero insuficiente en el nivel de gobernanza**:

| Dimensión | Quality Gate Tradicional (DevOps / SonarQube) | Quality Gate Gobernado por Autonomía (Esta Tesis) |
|---|---|---|
| **Criterio de evaluación** | Estático y binario (ej. Cobertura > 80%, 0 bugs críticos). | **Dinámico y contextual:** parametriza la exigencia según el nivel de autonomía delegado al agente (A0–A4). |
| **Sujeto generador** | Ciego a la procedencia: evalúa el artefacto final sin distinguir si lo escribió un senior, un junior o un agente. | **Sensible a la procedencia:** exige cadena de custodia, modelo/prompt utilizado y trazabilidad de decisiones intermedias. |
| **Emisión de evidencia** | Pasa/Falla local en CI/CD (se pierde tras el build). | **Evidencia auditable ex post:** emite telemetría estructurada alineada a controles de ISO 42001 e ISO 27001. |
| **Diseño del pipeline** | Se asume un pipeline lineal estándar. | **Condicionado por la topología agéntica (A0):** define dónde cortar los pases de mano entre agentes para inyectar inspección humana real. |

> **En síntesis:** El *Quality Gate* es el punto de inyección de software. La **tesis** es el modelo de gobernanza, la taxonomía de riesgos, la matriz de proporcionalidad y el sistema de evidencia que le dice al gate qué exigir, qué registrar y cuándo bloquear según la autonomía del agente.

---

## 6. El experimento estrella

Con datos de pull requests que **ya existen** (no hay que instrumentar nada nuevo):

| Métrica | Qué revela |
|---|---|
| Tiempo entre apertura y aprobación vs. tamaño del diff | ¿Hubo lectura o hubo click? |
| Tasa de aprobación sin comentarios, humano vs. agente | ¿El revisor discrimina el origen? |
| Defectos que escapan a producción por origen del cambio | Consecuencia real |
| % de cambios cuya decisión es reconstruible hoy | Línea de base de auditabilidad |

Si la línea de base muestra que diffs de 600 líneas generados por agente se aprueban en 45 segundos, **queda demostrada empíricamente la ficción de cumplimiento**. Ese solo hallazgo es publicable y no depende de que la empresa haga nada.

---

## 7. Alcance y delimitación

**El trabajo cubre:** el ciclo de desarrollo completo a nivel de marco conceptual (mapa de riesgos, niveles y evidencia para todas las fases).

**La validación empírica profunda va sobre un solo punto de control:** **revisión, aprobación y merge hacia producción.** Es donde autonomía y evidencia chocan de frente y donde los datos ya existen.
*Regla: amplitud en el marco, profundidad en un punto. Un capítulo con medición sólida vale más que ocho con anécdotas.*

**El trabajo NO:**
- certifica la empresa en ninguna norma;
- construye agentes nuevos;
- evalúa la calidad de modelos de lenguaje;
- hace benchmark de herramientas comerciales;
- abarca IA embebida en el producto (solo IA en el **proceso**).

### 7.1. El diferenciador: contexto PyME

Casi toda la literatura de gobernanza de IA asume una corporación con función de cumplimiento, segunda línea de defensa y auditoría interna. Acá la misma persona es AI engineer, referente de seguridad e implementadora.

Eso **no es una limitación del caso: es una pregunta de investigación adicional.**

> ¿Cómo se implementa gobernanza de IA verificable en una organización que no tiene segregación de funciones ni una función de cumplimiento dedicada?

Llamarlo **gobernanza proporcional**. Convierte el contexto en aporte a un segmento desatendido por la norma, y blinda contra la crítica de generalización.

---

## 8. Metodología

**Design Science Research** (Hevner; Peffers) + **investigación-acción** sobre **caso único** (Yin; Runeson & Höst) + **panel de expertos tipo Delphi**.

DSR es el escudo metodológico: es el paradigma aceptado en ingeniería para "construí un artefacto y lo evalué". Convierte "hice un framework" en investigación rigurosa. **Citarlo explícitamente desarma la objeción "esto no tiene ingeniería".**

### 8.1. El doble rol: activo y riesgo

Ser quien construye el objeto de estudio habilita algo raro: **intervenir por diseño** — instrumentar la telemetría *mientras* se construye el pipeline, en vez de reconstruirla después. Eso es investigación-acción, y es un método reconocido, no una excusa.

Pero el tribunal va a decir: *"vos diseñaste el marco, vos lo implementaste y vos evaluaste si funciona"*. **Cuatro mitigaciones, escritas desde el día uno** (tenerlas previstas antes de que las señalen vale el doble):

1. **Criterios de éxito pre-registrados** — umbrales definidos y congelados en el Plan de Trabajo, antes de medir. No se mueve el arco después.
2. **Evaluación externa** — el panel evalúa el artefacto; la autora no es jueza de su propio diseño.
3. **Triangulación** — datos del pipeline + entrevistas a devs + revisión documental.
4. **Diario de investigación** — bitácora fechada separando cuándo se actuó como ingeniera y cuándo como investigadora. Va como anexo. Es el equivalente metodológico de la propia trazabilidad que propone la tesis.

*Bonus de integridad: el propio comportamiento como revisora es un dato. Reconocerlo explícitamente suma.*

### 8.2. Validación y Calibración (tres patas + aseguramiento de calidad)

En el marco de Design Science Research (DSR), la evaluación debe probar que los artefactos no solo son conceptualmente válidos, sino operativamente eficaces y calibrados:

1. **Auditoría simulada / evidence reconstruction test:** tomar $N$ PRs reales ya mergeados e intentar reconstruir la cadena de evidencia. Medir **% de decisiones reconstruibles** antes y después de aplicar el marco.
2. **Panel de expertos (Delphi ligero):** 6–10 profesionales (auditores ISO 27001/42001, tech leads, investigadores académicos). Agendarlo **en enero**, no en marzo.
3. **Métricas pre/post:** DORA (lead time, change failure rate) + defect escape rate + tasa de intervención humana vs. aprobación automática + tasa de reversión.
4. **Calibración y aseguramiento de calidad (enfoque ISO 9001 / PDCA):**
   - *Calibración de Quality Gates:* asegurar que los guardrails (linters, SCA, chequeo de alucinaciones) no generen falsos positivos excesivos que induzcan a los desarrolladores a saltarse los controles.
   - *Verificación de la telemetría:* contrastar que los registros emitidos por el recolector de evidencia coincidan fielmente con las acciones reales ejecutadas en el repositorio y en el orquestador.

---

## 9. Pilares del proyecto

Cada pilar se ancla en una materia cursada. Ese es el argumento de que es indiscutiblemente orientación **Gestión** con sustento técnico.

| # | Pilar | Contenido | Ancla |
|---|---|---|---|
| **P1** | Normativo / GRC | Mapeo e integración de normas; integración SGSI↔SGIA (no dos sistemas paralelos) | GRC |
| **P2** | Ingeniería del desarrollo agentizado | Modelo de referencia: taxonomía de agentes, artefactos que tocan, quality gates, guardrails, puntos de inyección de control | Trabajo real |
| **P3** | Riesgo y control | Taxonomía + matriz autonomía×control + evaluación de impacto adaptada | GRC |
| **P4** | Datos, medición y decisión | Telemetría de gobernanza, KPIs/KRIs, tablero directivo, DORA extendido | Decisiones Estratégicas Basadas en Datos |
| **P5** | Factor humano, ética y cambio | Roles y RACI, competencias, HITL efectivo, gestión del cambio | Habilidades Blandas + Informe Ético |
| **T** | *(transversal)* Método | DSR + caso único + Delphi | — |

---

## 10. Matriz ética

Construida contra las **5 preguntas literales** del documento de la Facultad. La columna "Tensión residual" es la que distingue: un informe ético que no reconoce tensiones no convence.

| # | Dilema | Cómo se manifiesta | Afectados | Anclaje | Control propuesto | Tensión residual |
|---|---|---|---|---|---|---|
| E1 | **Brecha de responsabilidad** | Nadie "escribió" el commit que causó el incidente. *Moral crumple zone*: el revisor absorbe la culpa de una falla sistémica | Devs, revisores, clientes | 42001 (roles); 27001 A.5 | Firma humana nominada e indelegable por nivel; RACI explícito; el agente nunca es sujeto de responsabilidad | Firmar sin capacidad real de verificar = responsabilidad ficticia |
| E2 | **Sesgo de automatización / HITL de sello de goma** | El revisor aprueba sin leer. *Ironies of Automation*: a mayor automatización, menor capacidad de supervisar | Devs, usuarios finales | 42001 (supervisión humana); AI Act art. 14 | Métrica de profundidad de revisión; muestreo obligatorio; rotación | Medir la revisión es vigilar al revisor (→ E9) |
| E3 | **Alucinaciones en código productivo** | Dependencias inexistentes (*slopsquatting*), APIs inventadas, lógica plausible que pasa los tests | Usuarios finales, negocio | NIST SP 800-218A; OWASP LLM | Allowlist de dependencias, SCA, tests de propiedad, cobertura mínima por nivel | Ningún gate detecta el error semántico correcto-pero-inadecuado |
| E4 | **Fuga de IP (saliente)** | Código propietario, secretos y datos de cliente enviados a proveedores de modelos como contexto | Empresa, clientes | 27001 A.5.14/A.8; Ley 25.326; 42001 (proveedores) | Clasificación de repos, redacción de secretos, cláusulas de no-entrenamiento, inventario de terceros | La utilidad del agente crece con el contexto que se le da |
| E5 | **Contaminación de licencias (entrante)** | El agente reproduce código copyleft sin atribución | Empresa, comunidad OSS | Propiedad intelectual | Escaneo de licencias, política de atribución, registro de procedencia | Trazabilidad imposible hacia los datos de entrenamiento |
| E6 | **Sesgos** | No es "código sesgado": es *qué* se construye. Defaults excluyentes, accesibilidad omitida; revisión automática que penaliza estilos no idiomáticos o inglés no nativo | Usuarios finales, devs no anglófonos | AI Act; principios de equidad | Checklist de accesibilidad/inclusión en el gate de diseño; auditoría de sugerencias por perfil | El sesgo del modelo es opaco y no auditable desde afuera |
| E7 | **Desprofesionalización / "problema del pipeline"** | Si los agentes hacen el trabajo junior, ¿de dónde salen los seniors que supervisan en cinco años? | Devs junior, profesión | Impacto de mediano/largo plazo | Plan de competencias, tareas de aprendizaje protegidas, "modo entrenamiento" sin agente | Tensión directa con la productividad de corto plazo |
| E8 | **Privacidad de datos** | PII en fixtures, logs, prompts y trazas | Titulares de datos | Ley 25.326; ISO/IEC 27701 | Minimización, datos sintéticos, retención acotada de trazas | Auditabilidad exige retener; privacidad exige borrar |
| E9 | **Vigilancia laboral** ⚠️ | **El propio marco crea la superficie de vigilancia**: la telemetría mide personas, no solo agentes | Empleados | Ley 25.326; derechos laborales | Agregación, propósito declarado, prohibición de uso para evaluación de desempeño individual, consulta a los equipos | Genuina: el mismo dato sirve para auditar y para controlar |
| E10 | **Sostenibilidad** | Costo energético de la inferencia agéntica a escala | Ambiente | Impacto de largo plazo | Métrica de costo/energía por tarea; "el agente correcto para la tarea" | — |

> **E9 es la mejor carta.** Una tesis que identifica que su propia solución genera un riesgo ético muestra una madurez que casi ningún trabajo de grado tiene.

### 10.1. Mapeo a las 5 preguntas de la Facultad

1. **¿Objeto y fin éticos? ¿Qué circunstancias lo modificarían?** → El fin es **aumentar** la responsabilidad humana sobre sistemas automatizados, no reducirla. Circunstancias que lo modifican: que el marco se use para *justificar* delegación sin supervisión real (E2) o como herramienta de vigilancia (E9).
2. **Impacto positivo para stakeholders** → Trazabilidad, menos defectos que escapan, protección de IP, decisiones informadas, adopción deliberada y no por inercia. Stakeholders: devs, empresa, clientes, usuarios finales, auditores, reguladores.
3. **Medidas de mitigación** → toda la columna "Control propuesto", con horizontes: puesta en marcha (E4, E8), mediano (E2, E3), largo (E7, E10).
4. **DDHH, justicia y equidad** → E6, E7, E9. Explicitar que el marco **no** habilita despidos automatizados ni evaluación individual por telemetría.
5. **Integridad** → APA + **declaración de uso de IA en la propia tesis**, con criterios de trazabilidad. Sería incoherente escribir sobre gobernanza de IA sin gobernar el propio uso.

### 10.2. El argumento humano (por qué esto no es burocracia)

Algo va a salir mal. Un cambio que escribió un agente va a romper algo caro. Cuando pase, van a buscar al responsable y van a encontrar un registro que dice **"aprobado por"** y un nombre. Probablemente el más junior del equipo: alguien que recibió 40 cambios ese día y no tenía forma humana de leerlos todos.

**Eso es lo que la tesis trata de evitar.** No son papeles para pasar una auditoría: es que la responsabilidad caiga donde corresponde, y que cuando se dice "hay un humano supervisando" sea verdad y no un sello.

### 10.3. Fundamentación humanista y Magisterio Pontificio: Encíclica *Magnifica Humanitas* (León XIV, 2026)

Para el Informe Ético y Social de la Universidad Austral, el marco ancla formalmente en el Magisterio de la Iglesia sobre inteligencia artificial, con eje central en la **Carta Encíclica *Magnifica Humanitas*** del Papa León XIV (*"Sobre la custodia de la persona humana en el tiempo de la inteligencia artificial"*, mayo de 2026), publicada en el 135.º aniversario de la *Rerum Novarum*:

1. **Custodia de la persona frente al paradigma tecnocrático:**
   - La encíclica advierte contra la reducción de la persona a mero "dato", "operador" o "prestación funcional". En el desarrollo de software, esto se traduce en evitar que el revisor humano sea degradado a una zona de choque moral (*moral crumple zone*) o a un sello de goma de procesos automatizados.
2. **La IA no es neutral y exige gobernanza:**
   - *Magnifica Humanitas* explicita que los sistemas algorítmicos no son éticamente neutros y concentran poder de decisión. La respuesta ética no es la tecnofobia ni el rechazo, sino el **desarme de la opacidad** mediante la transparencia, la rendición de cuentas (*accountability*) y marcos de custodia proporcionados.
3. **Distinción entre elección algorítmica y decisión moral:**
   - La máquina procesa probabilidades y realiza selecciones operativas; la persona humana asume la responsabilidad ética de la decisión. La delegación de tareas de ingeniería a agentes solo es legítima si el ser humano retiene la soberanía y la capacidad efectiva de supervisión.

> **Síntesis:** El claim de la tesis (*"la supervisión humana solo es real si es verificable; sin evidencia proporcional, el human-in-the-loop es una ficción"*) es la operacionalización ingenieril directa de *Magnifica Humanitas*: custodiar la primacía de la persona humana en los procesos productivos mediados por IA a través de evidencia y control real.

---

## 11. Marco normativo de referencia

> ⚠️ Verificar numeración de cláusulas, controles de Anexo A y años de publicación contra las normas originales antes de citar.

- **ISO/IEC 42001:2023** — Sistema de gestión de IA (SGIA) + Anexo A de controles.
- **ISO/IEC 23894:2023** — Gestión del riesgo en IA.
- **ISO/IEC 42005** — Evaluación de impacto de sistemas de IA *(verificar estado de publicación)*.
- **ISO/IEC 5338:2023** — Procesos del ciclo de vida de sistemas de IA.
- **ISO/IEC/IEEE 12207** — Procesos del ciclo de vida del software.
- **ISO/IEC 27001:2022 / 27002:2022** — SGSI y controles. **Punto clave: integración SGSI↔SGIA, no dos sistemas paralelos.**
- **ISO/IEC 27701** — Gestión de privacidad.
- **NIST AI RMF 1.0 (2023)** + **NIST AI 600-1 (2024)** — perfil de IA generativa.
- **NIST SP 800-218 (SSDF)** y **SP 800-218A (2024)** — prácticas de desarrollo seguro con IA generativa.
- **Reglamento (UE) 2024/1689 (AI Act)** — relevancia indirecta (clientes/mercado); art. 14 sobre supervisión humana.
- **OWASP Top 10 for LLM Applications** y guías de amenazas agénticas.
- **Ley 25.326 (Argentina)** — protección de datos personales; aplica a monitoreo de empleados.

---

## 12. Preguntas para el Director de Carrera

**1. Criterio de suficiencia del aporte.**
> "El template del Plan de Trabajo pide *Funcionalidades*, *Tecnologías propuestas* y *Arquitectura* — está pensado para una tesis de producto de software. Mi propuesta es un marco de gobernanza validado empíricamente, bajo Design Science Research. **¿Cómo espera que instancie esas tres secciones?** ¿Un artefacto documental + tablero + instrumentación de trazabilidad califica, o el tribunal espera un sistema funcionando?"

*(Si la respuesta es "necesitás software", el componente construible es el **recolector de telemetría de gobernanza + tablero**: se implementa, se demuestra y se mide.)*

**2. Evidencia de validación aceptable.**
> "¿Qué considera validación suficiente: panel de expertos tipo Delphi, auditoría simulada con métricas pre/post sobre un caso único, o exigen medición sobre múltiples proyectos? ¿Cuál es el N mínimo defendible?"

**3. Confidencialidad y doble rol.**
> "(a) ¿Cuál es el procedimiento de la Facultad para datos confidenciales de empresa — anonimización, anexo reservado, acuerdo con la universidad? (b) ¿Qué mecanismo formal esperan para mitigar el sesgo de practitioner-researcher, dado que soy investigadora y parte del objeto de estudio?"

**4. Reglas del trabajo individual.**
> "¿El alcance esperado se ajusta respecto de un trabajo grupal, o solo cambia la carga? ¿Cuántas horas semanales debo declarar en el Plan y qué total se considera razonable?"

**5. Plan de contingencia y gobernanza del proyecto.**
> "Mi tesis toma insumos de un proyecto corporativo cuyo cronograma no controlo. **Quiero dejar aprobado de antemano un plan B**: si la empresa despriorizara, la tesis continúa como marco validado por panel de expertos + datos históricos ya capturados. ¿Le parece formalizarlo en el Plan de Trabajo? ¿Y cómo se reparten roles entre tutor corporativo y tutor académico?"

**Bonus (para el tutor, no para el Director):**
> "¿Qué política adopta la cátedra sobre uso de IA generativa en la redacción de la tesis? Lo pregunto porque quiero declararlo explícitamente en el Informe Ético, como coherencia con el tema."

---

## 13. Cómo llenar el template del Plan de Trabajo

| Sección | Qué poner |
|---|---|
| **Motivación** | El gap: la IA agéntica entró al proceso de producción de software más rápido que los marcos que deberían gobernarla. Anclado en experiencia real. |
| **Objetivo** | Pregunta de investigación + los cuatro artefactos + criterio de éxito **medible** (ej.: elevar la reconstrucción de decisiones del X% al Y%). |
| **Palabras clave** | Las de la sección 1. |
| **Funcionalidades** | Reinterpretar como **capacidades del marco**: clasificar autonomía, seleccionar controles, emitir evidencia, calcular indicadores, disparar escalamiento. |
| **Tecnologías propuestas** | El componente instrumental: recolector de telemetría sobre el pipeline real (CI/CD, control de versiones, orquestador de agentes), almacenamiento de trazas, tablero. Más el corpus normativo. |
| **Arquitectura** | **Arquitectura de gobernanza en capas** superpuesta al ciclo de desarrollo: política → control (guardrails y gates) → evidencia (telemetría) → decisión (indicadores). Un solo diagrama y la sección está ganada. |
| **Metodología** | DSR (Peffers, 6 etapas) + caso único (Yin) + Delphi. |
| **Carga horaria** | Cerrar con la respuesta a la pregunta 4. Referencia: ~12 h/semana × ~40 semanas ≈ 480 h. |

---

## 14. Cronograma

| Período | Hito | Entregable |
|---|---|---|
| **Ago 2026** | 14/08 — Definición de tema | Título + pregunta + gap + delimitación + plan B |
| **Ago–Sep** | ⚡ **Captura de línea de base (empezar YA)** | Dataset histórico de cambios agente/humano |
| **Sep–Oct** | Estado del arte + marco teórico | **Informe Ético** (usar la matriz §10) |
| **Oct** | Arranca ISO 42001 en la empresa → lograr que el uso agéntico quede escrito en el alcance del SGIA | **Plan de Trabajo** formal |
| **Nov–Dic** | Diagnóstico + taxonomía de riesgos v1 (A1) + criterios de topología (A0) | Informe de diagnóstico |
| **Ene–Mar 2027** | Diseño del artefacto: matriz autonomía×control (A2), modelo de evidencia y tablero (A3) | Framework v1 |
| **Mar–Abr** | Panel de expertos → framework v2 | Informe de validación cualitativa |
| **Abr–May** | Instanciación piloto + auditoría simulada + métricas pre/post | Resultados cuantitativos |
| **May–Jun** | Análisis, discusión, redacción final | Borrador completo |
| **Jun–Jul** | Revisión con tutores + defensa | **Tesis** |

**Dependencias críticas:** (a) panel agendado en enero, no en marzo; (b) línea de base existente antes de diciembre; (c) alcance del SGIA incluye el caso de uso.

---

## 15. Riesgos del proyecto y plan B

| Riesgo | Mitigación |
|---|---|
| La empresa despriorizara ISO 42001 | **La tesis no depende de la certificación.** La empresa es caso de estudio, no dependencia. Plan B aprobado por escrito: validación por panel + datos históricos. |
| No conseguir acceso a datos del pipeline | Pedir el export histórico **ahora**, mientras el tema está caliente. Fallback: validación cualitativa como eje. |
| Perder la línea de base | **Riesgo más urgente.** Capturar ago–sep 2026. Si se espera a 2027, el "antes" se pierde para siempre. |
| Deriva hacia benchmark de herramientas | Regla escrita en la delimitación: criterios, no rankings. |
| Cuestionamiento por doble rol | Las cuatro mitigaciones de §8.1, escritas desde el Plan de Trabajo. |
| El template empuja hacia tesis de producto | Pregunta 1 al Director, resuelta antes del Plan. |

---

## 16. Acciones inmediatas

- [ ] **Hablar con el jefe** y pedir tres cosas concretas:
  - export histórico de PRs de los últimos 6–12 meses (autor, revisor, timestamps de apertura/aprobación/merge, líneas cambiadas, comentarios, origen humano/agente);
  - permiso escrito breve para usar datos **anonimizados** en la tesis;
  - que el **uso agéntico en el desarrollo quede escrito en el alcance del SGIA** cuando arranque la implementación.
- [ ] Mandar el mail al Director de Carrera y a la Directora de Tesis pidiendo reunión antes del viernes 14.
- [ ] Reunión con las 5 preguntas de §12.
- [ ] Congelar título y pitch.
- [ ] Entregar definición de tema el 14/08.

---

## 17. El pitch, en tres tamaños

**Una frase (ascensor):**
> Construyo y valido un marco para decidir **cómo armar y cuánta autonomía darle a un conjunto de agentes de IA en el desarrollo de software**, de modo que la supervisión humana sea verificable y no una ficción.

**Tres frases (Director de Carrera):**
> Los marcos de gobernanza de IA gobiernan la IA como producto; nadie gobierna la IA cuando está adentro del proceso que produce el software. Mi tesis sostiene que la supervisión humana solo es real si es verificable, y que por lo tanto cada nivel de autonomía delegado a un agente exige un nivel de evidencia proporcional. Construyo ese marco —taxonomía de riesgos, matriz autonomía×control, modelo de evidencia— y lo valido midiendo, sobre un caso real, cuánto sube la trazabilidad de las decisiones al aplicarlo.

**Un párrafo (formal, para el documento):**
> Los marcos de gobernanza de inteligencia artificial vigentes —ISO/IEC 42001, NIST AI RMF, EU AI Act— fueron concebidos para gobernar la IA en tanto producto entregado a usuarios. Sin embargo, la incorporación de agentes de IA al ciclo de vida del desarrollo de software desplaza el objeto gobernado: la IA deja de ser el producto y pasa a integrar el proceso que produce todo el software de la organización, propagando riesgo incluso hacia sistemas que no contienen IA. Para ese escenario no existe hoy ni un modelo de control ni un modelo de evidencia. Este trabajo sostiene que la supervisión humana solo es real cuando es verificable, y que por lo tanto cada nivel de autonomía delegado a un agente debe tener asociado un nivel de evidencia obligatoria que permita reconstruir ex post la cadena de decisión; en ausencia de esa evidencia proporcional, el human-in-the-loop opera como una ficción de cumplimiento. Se propone construir y validar un marco compuesto por criterios de gobernabilidad de topologías agénticas, una taxonomía de riesgos, una matriz de niveles de autonomía y controles asociados, y un modelo de telemetría de gobernanza con su tablero de decisión. La validación se realizará mediante investigación-acción sobre un caso único —una PyME tecnológica que atraviesa simultáneamente la agentización de su desarrollo y la implementación de un sistema de gestión de IA— combinando medición cuantitativa pre/post sobre el punto de control de revisión y despliegue con evaluación externa por panel de expertos.

**El test del "¿y qué?":** si alguien pregunta *"¿y qué?"*, la respuesta no es "es un framework". Es:
> **"Que hoy tu empresa firma que un humano supervisó, y no lo puede probar."**

---

## 18. Las cuatro ideas que hay que poder reconstruir sin memorizar

1. **La IA se metió en la fábrica, no en el producto.** Todas las reglas están escritas para el producto.
2. **La supervisión humana se rompe sola, por volumen, y sin avisar.**
3. **Lo único que distingue supervisión real de supervisión de cartón es que quede rastro.**
4. **Cuanta más autonomía, más rastro. Ni más ni menos: proporcional.**

Todo lo demás son detalles de implementación.

---

## 19. Bibliografía inicial (APA)

> ⚠️ Verificar cada referencia contra la fuente original antes de citarla en un entregable.

**Método**
- Hevner, A. R., March, S. T., Park, J., & Ram, S. (2004). Design science in information systems research. *MIS Quarterly, 28*(1), 75–105.
- Peffers, K., Tuunanen, T., Rothenberger, M. A., & Chatterjee, S. (2007). A design science research methodology for information systems research. *Journal of Management Information Systems, 24*(3), 45–77.
- Yin, R. K. (2018). *Case study research and applications: Design and methods* (6th ed.). Sage.
- Runeson, P., & Höst, M. (2009). Guidelines for conducting and reporting case study research in software engineering. *Empirical Software Engineering, 14*(2), 131–164.
- Susman, G. I., & Evered, R. D. (1978). An assessment of the scientific merits of action research. *Administrative Science Quarterly, 23*(4), 582–603.

**Factor humano y automatización**
- Bainbridge, L. (1983). Ironies of automation. *Automatica, 19*(6), 775–779.
- Parasuraman, R., & Riley, V. (1997). Humans and automation: Use, misuse, disuse, abuse. *Human Factors, 39*(2), 230–253.
- Elish, M. C. (2019). Moral crumple zones: Cautionary tales in human-robot interaction. *Engaging Science, Technology, and Society, 5*, 40–60.

**IA en ingeniería de software y agentes (2023–2026)**
- Jiménez, C. E., Yang, J., Wettig, A., Yao, S., Pei, K., Press, O., & Narasimhan, K. (2024). SWE-bench: Can language models resolve real-world GitHub issues? *ICLR 2024*.
- Hong, S., Zheng, X., Chen, J., Cheng, Y., Zhang, C., Wang, Z., ... & Zhou, M. (2024). MetaGPT: Meta programming for a multi-agent collaborative framework. *ICLR 2024*.
- Qian, C., Cong, X., Yang, C., Chen, W., Su, Y., Xu, J., ... & Liu, Z. (2024). Communicative agents for software development. *ACL 2024*.
- Perry, N., Srivastava, M., Kumar, D., & Boneh, D. (2023). Do users write more insecure code with AI assistants? *ACM CCS 2023*.
- Sandoval, G., Pearce, H., Nisi, T., Karmakar, S., Dolan-Gavitt, B., & Garg, S. (2023). Lost at C: A user study on the security implications of large language model code assistants. *USENIX Security 2023*.
- Vaithilingam, P., Zhang, T., & Glassman, E. L. (2022). Expectation vs. experience: Evaluating the usability of code generation tools powered by large language models. *CHI EA*.
- Forsgren, N., Humble, J., & Kim, G. (2018). *Accelerate: The science of lean software and DevOps*. IT Revolution Press.

**Ética, Magisterio Pontificio y Algor-ética**
- León XIV. (2026, 15 de mayo). *Carta Encíclica Magnifica Humanitas: Sobre la custodia de la persona humana en el tiempo de la inteligencia artificial*. Ciudad del Vaticano.
- Papa Francisco. (2024, 14 de junio). *Discurso del Santo Padre en la sesión del G7 sobre Inteligencia Artificial*. Borgo Egnazia.
- Papa Francisco. (2024, 1 de enero). *Mensaje para la 57ª Jornada Mundial de la Paz: Inteligencia Artificial y Paz*.
- Pontificia Academia para la Vida. (2020/2024). *Rome Call for AI Ethics*. Ciudad del Vaticano.

**Normas y regulación** — ver §11.

---

## 20. KB de Acuerdos y Decisiones con la Directora de Tesis / Cátedra

*Registrado tras la reunión de definición y aprobación inicial de tema:*

1. **Aprobación de encuadre individual:** Aprobada la modalidad individual y el enfoque como **Trabajo de Investigación**. Cronograma formal con horizonte junio–julio 2027.
2. **Tutor Académico:** Marcos Giagnorio (enlace con su línea de doctorado afín; asegura feedback de alto nivel y foco en publicabilidad).
3. **Profundidad bibliográfica:** Exigencia explícita de literatura científica actualizada (foco 2023–2026 en papers de SE agéntica, LLM security, DSR y gobernanza).
4. **No inventar una norma; extender las vigentes:** El tribunal valora el aterrizaje operacional. La tesis formaliza una **extensión/perfil de implementación para SDLC agentizado** sobre ISO/IEC 42001 e ISO/IEC 27001, sin pretender crear un estándar desde cero.
5. **Validación, Calibración y Pre/Post:** Exigencia de apartado riguroso de validación (DSR + ISO 9001/PDCA). Se ratifica la recolección de métricas pre/post sobre PRs reales y la calibración de gates/recolectores de evidencia.
6. **Manejo de limitaciones de IA (alucinaciones y datos):** Se resuelven como controles específicos en la matriz A2 y gates determinísticos en CI/CD (SCA, allowlist de paquetes, filtros de sanitización).
7. **Límites de HITL:** Definición explícita de puntos de costura indelegables donde la persona física retiene la firma y la responsabilidad.
8. **Anclaje del Informe Ético en el Magisterio Papal:** Incorporación central de la Encíclica *Magnifica Humanitas* (León XIV, 2026) sobre la custodia de la persona humana, complementada con el concepto de *Algor-ética* y la distinción ontológica entre elección algorítmica y decisión moral humana.
9. **Desactivación de la trampa del "Agente Auditor":** Se descarta crear un bot generalista que audite políticas empresariales (desvío a producto). Se integra en **A3** como un **Motor Evaluador de Conformidad en CI/CD**, que audita automáticamente si las trazas del agente de desarrollo cumplen con la matriz A2.
10. **Quality Gates vs. Gobernanza de Autonomía:** Aclaración de que el *Quality Gate* es el punto de inyección técnico en CI/CD, mientras que la tesis aporta el marco de gobernanza que parametriza dinámicamente dichos gates según la autonomía del agente (A0–A4) y emite evidencia auditable ex post.
