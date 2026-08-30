**Gobernanza de agentes de IA en el desarrollo de software: autonomía graduada y evidencia proporcional**

# Plan de Trabajo de Grado

Ingeniería en Informática — Orientación Gestión

## Plan 2023 - Año 2026

## *Profesora: Gabriela Robiolo*

## *Director: Marcos Giagnorio*

## *Alumna: Macarena Alimena*

---

# Índice

[**Introducción**](#introducción)

[Motivación](#motivación)

[Objetivo](#objetivo)

[**Descripción y caracterización**](#descripción-y-caracterización)

[Funcionalidades](#funcionalidades)

[Tecnologías propuestas](#tecnologías-propuestas)

[Arquitectura](#arquitectura)

[**Metodología y cronograma**](#metodología-y-cronograma)

[**Bibliografía**](#bibliografía)

---

# Introducción

La incorporación de agentes de inteligencia artificial al ciclo de vida del desarrollo de software constituye un cambio de naturaleza y no solo de escala. Un agente de IA no es un asistente que sugiere texto: es un componente que recibe un requerimiento, planifica, escribe código, ejecuta pruebas, abre una solicitud de integración y, en configuraciones más avanzadas, la despliega. La organización deja de operar con herramientas que asisten a personas y pasa a operar con actores que producen artefactos.

Los marcos de gobernanza de IA vigentes no fueron escritos para ese escenario. ISO/IEC 42001:2023 establece los requisitos de un sistema de gestión de inteligencia artificial; el *AI Risk Management Framework* del NIST propone un ciclo de identificación y tratamiento de riesgos; el Reglamento (UE) 2024/1689 clasifica sistemas según su nivel de riesgo e impone obligaciones de supervisión humana. Los tres comparten un supuesto implícito: que el sistema de IA es el objeto que la organización entrega al mercado, y que gobernarlo consiste en controlar ese objeto.

Cuando la IA se incorpora al proceso de desarrollo, ese supuesto se rompe. La inteligencia artificial deja de ser el producto y pasa a integrar **el proceso que produce todo el software de la organización**. El desplazamiento tiene una consecuencia directa: el riesgo deja de estar confinado al sistema que contiene IA y se propaga hacia la totalidad de los sistemas entregados, incluidos aquellos que no incorporan inteligencia artificial alguna.

Una analogía permite fijar la distinción. Casi toda la regulación vigente está escrita para un automóvil con piloto automático: la IA está dentro del producto, y si el piloto automático falla, falla ese modelo de automóvil. Lo que ocurre en el desarrollo agentizado es de otra naturaleza: se cambiaron los robots de la línea de montaje. Si el robot de la fábrica introduce un defecto sistemático, salen defectuosos todos los automóviles, incluidos los modelos que no incorporan tecnología alguna. La atención regulatoria está puesta sobre el automóvil; el desplazamiento ocurrió en la fábrica.

El mecanismo concreto por el cual este desplazamiento degrada el control es aritmético. Hasta hace poco, una persona escribía el código y otra lo revisaba y aprobaba. Un agente produce hoy en minutos el volumen de cambio que una persona producía en días, pero quien aprueba conserva la misma jornada laboral. Donde antes llegaban cinco cambios de cincuenta líneas por día, llegan ahora decenas de cambios de varios cientos de líneas. La revisión sustantiva, físicamente, deja de entrar en el tiempo disponible.

Lo relevante es que nadie decide dejar de revisar. La supervisión se degrada de manera gradual hasta que el registro de aprobación conserva su prolijidad formal pero detrás de la firma ya no hay lectura efectiva. El fenómeno está documentado en la literatura de factores humanos: Bainbridge (1983) describió cómo la automatización erosiona precisamente la competencia de supervisión que ella misma requiere; Parasuraman y Riley (1997) caracterizaron el sesgo que lleva a aceptar la salida del sistema sin verificación independiente; y Elish (2019) aportó el concepto de *moral crumple zone*, según el cual el operador humano situado al final de una cadena automatizada absorbe la responsabilidad de una falla sistémica que no estaba en condiciones de prevenir.

## Motivación

La motivación de este trabajo no reside en limitar el uso de agentes de IA en el desarrollo de software ni en proponer más instancias de revisión humana, sino en aportar, desde el dominio de la gestión y la gobernanza de sistemas, un modelo que permita distinguir empíricamente una supervisión efectiva de su simulacro administrativo.

La preocupación central es que la supervisión humana no se rompe por mala fe: se rompe por aritmética, y se rompe sin producir señal. Una organización puede exhibir hoy un registro completo de aprobaciones nominadas y no estar en condiciones de demostrar que alguna de ellas correspondió a una lectura real. Cuando algo salga mal —y un cambio escrito por un agente eventualmente romperá algo costoso— la investigación encontrará un registro que dice "aprobado por" y un nombre, con frecuencia el de la persona con menos antigüedad del equipo, que recibió cuarenta cambios ese día y no tenía forma humana de leerlos todos.

Ese es el problema que este trabajo aborda. No se trata de producir documentación para superar una auditoría, sino de que la responsabilidad recaiga donde corresponde y de que la afirmación "hay una persona supervisando" sea verificable y no una declaración de intenciones.

El interés académico recae en que hoy no existe, para este escenario, ni un modelo de control ni un modelo de evidencia. La literatura de gobernanza de IA asume además una organización de gran porte, con función de cumplimiento y auditoría interna independiente. El caso de estudio es una PyME tecnológica donde una misma persona concentra los roles de ingeniera de IA, referente de seguridad e implementadora. Esa condición no se trata como limitación sino como pregunta adicional: cómo se implementa gobernanza verificable en una organización que carece de segregación de funciones.

## Objetivo

El objetivo general es **construir y validar empíricamente un marco de gobernanza —denominado ARGOS, *Autonomous Risk & Governance Oversight for Software*— que permita a una organización decidir de manera explícita cuánta autonomía delega en agentes de IA dentro de su proceso de desarrollo de software, qué controles exige en cada nivel y qué evidencia debe emitir el pipeline para que la supervisión humana sea auditable *ex post*.**

El marco se define como una **extensión de dominio y perfil de implementación operacional** sobre ISO/IEC 42001:2023 e ISO/IEC 27001:2022. No pretende constituir una norma nueva: aporta el aterrizaje operacional que las normas vigentes no proveen para el escenario de la agentización del desarrollo.

La pregunta de investigación que ordena el trabajo es: *¿cómo debe extenderse un sistema de gestión de IA conforme a ISO/IEC 42001 para gobernar de forma auditable la delegación de tareas de ingeniería a agentes de IA a lo largo del ciclo de vida del software, preservando la responsabilidad humana y la trazabilidad de la evidencia?*

La tesis que se sostiene es que **la supervisión humana solo es real si es verificable**, y que por lo tanto todo nivel de autonomía delegado a un agente debe tener asociado un nivel de evidencia obligatoria que permita reconstruir *ex post* quién decidió qué. El principio unificador es **autonomía graduada, evidencia proporcional**. La afirmación es falsable: si al medir resultara que las revisiones conservan profundidad sustantiva aun sin evidencia obligatoria, la tesis se cae.

Para alcanzar el objetivo general se definen los siguientes objetivos específicos:

* Identificar y clasificar los riesgos que introduce la agentización del desarrollo y que las taxonomías vigentes de riesgo de IA no cubren.
* Establecer los criterios arquitectónicos que determinan si una topología de agentes admite supervisión humana efectiva y captura de evidencia.
* Definir los controles y la evidencia mínima obligatoria correspondientes a cada nivel de autonomía delegada.
* Especificar qué debe registrar un pipeline agentizado para ser auditable *ex post*, e implementar el componente instrumental que emite y evalúa esa evidencia.
* Definir los indicadores que permiten a la dirección decidir qué delegar, en qué medida y bajo qué condiciones revertir.
* Validar el marco mediante medición previa y posterior a la intervención sobre un caso real, complementada con evaluación externa por panel de expertos.

**Palabras clave**: Gobernanza de Inteligencia Artificial, Agentes de IA, Desarrollo de Software, Supervisión Humana, Auditabilidad, Evidencia Proporcional, ISO/IEC 42001, Design Science Research.

# Descripción y caracterización

La propuesta consiste en el diseño y la validación empírica de un marco de gobernanza compuesto por cuatro artefactos articulados, evaluado sobre la combinación de agentes de IA que cubren distintas etapas del ciclo de desarrollo seguro de software (diseño, codificación, pruebas y análisis de seguridad) en el entorno de una PyME tecnológica.

| Artefacto | Contenido |
|---|---|
| **A0** | Criterios de gobernabilidad de topologías agénticas: qué configuraciones y combinaciones de agentes admiten inspección humana y captura de evidencia a lo largo del ciclo de vida. |
| **A1** | Taxonomía de riesgos del desarrollo agentizado, mapeada a controles normativos. |
| **A2** | Matriz Autonomía × Control: cinco niveles (A0–A4) con sus controles obligatorios y su evidencia mínima por fase. |
| **A3** | Modelo de evidencia (telemetría de gobernanza), motor evaluador de conformidad en el pipeline y tablero de indicadores de decisión. |

El trabajo cubre el ciclo de desarrollo completo **a nivel de marco conceptual**. La **validación empírica profunda** se concentra sobre el punto de control crítico de integración: revisión, aprobación y despliegue de cambios hacia producción, evaluando el comportamiento del pipeline con la combinación de agentes antes y después de la intervención gobernada mediante una batería de indicadores cuantitativos y cualitativos. La regla que ordena el alcance es: amplitud en el marco, profundidad en un punto.

Para acotar el trabajo a los recursos disponibles, se establece explícitamente qué queda **fuera del alcance**:

* **Certificación normativa:** no se certifica a la organización en ninguna norma. Las normas operan como marco de referencia y destino de mapeo, no como objetivo de cumplimiento.
* **Construcción de agentes:** no se desarrollan agentes de IA nuevos ni se evalúa la calidad de modelos de lenguaje. Los agentes son el objeto gobernado, no el objeto construido.
* **Comparación de herramientas:** no se realizan *benchmarks* ni rankings de plataformas agénticas comerciales. La exclusión es metodológica: una comparación de herramientas pierde vigencia en pocos meses, mientras que los criterios de gobernabilidad no caducan. Se aporta el criterio de decisión, no la recomendación de producto.
* **IA embebida en el producto:** el trabajo aborda exclusivamente la IA incorporada al proceso que produce el software, no la que se entrega dentro de él.
* **Desarrollo de producto comercial:** el componente de software es instrumental. Quedan excluidas la gestión de usuarios, la comercialización y las interfaces orientadas a un consumidor externo.

## Funcionalidades

La plantilla solicita esta sección en términos de funcionalidades de producto. Dado que el resultado es un marco de gobernanza validado empíricamente, se instancia como **capacidades**: aquello que una organización queda habilitada a hacer una vez implantado ARGOS. Las tres últimas se materializan en software efectivamente construido.

* **Diagnosticar la gobernabilidad de una topología agéntica (A0):** evaluar, antes de delegar, si la configuración de agentes adoptada admite puntos de inspección humana y fronteras de captura de evidencia. Responde a si el diseño es supervisable, no a si funciona.
* **Identificar y clasificar riesgos del desarrollo agentizado (A1):** reconocer amenazas propias del escenario —alucinación de dependencias inexistentes, pérdida de restricciones de seguridad en los pases de mano entre agentes, degradación silenciosa de la revisión, contaminación de licencias— y ubicarlas en una estructura que permita asignarles control.
* **Clasificar el nivel de autonomía y seleccionar controles proporcionales (A2):** determinar en cuál de los cinco niveles opera efectivamente cada agente, derivar de allí los controles obligatorios, la evidencia mínima y el punto de firma humana indelegable, y hacer explícita la brecha entre el nivel declarado y el real.
* **Emitir y evaluar evidencia de forma automatizada (A3):** capturar del pipeline la traza de procedencia de cada cambio, evaluarla contra la política vigente y bloquear, marcar o escalar según corresponda. La evidencia se emite desde la ejecución: si depende de carga manual, deja de producirse en pocas semanas.
* **Calcular indicadores de decisión directiva (A3):** producir indicadores de riesgo —tasa de intervención humana, retención de contexto entre agentes, discrepancia de traza, tasa de falsos positivos de las compuertas— que permitan decidir qué delegar y cuándo revertir.
* **Contener y escalar (A3):** disparar el corte determinístico y la derivación a supervisión humana ante bucles de razonamiento, exceso de consumo de recursos o intento de acceso a artefactos restringidos.

Una objeción previsible sostiene que este mecanismo equivale a las *quality gates* ya existentes en integración continua. La observación es correcta respecto del punto de inyección técnico e insuficiente respecto del nivel de gobernanza: una compuerta tradicional evalúa con criterio estático y binario, es ciega a la procedencia del artefacto y su resultado se pierde tras la ejecución. Una compuerta gobernada parametriza su exigencia según el nivel de autonomía delegado, exige cadena de custodia del cambio y emite evidencia estructurada auditable *ex post*. La compuerta es el punto de inyección; el aporte del trabajo es el modelo que le indica qué exigir, qué registrar y cuándo bloquear.

## Tecnologías propuestas

*   **Recolector de telemetría de gobernanza (Python):** captura eventos del orquestador de agentes y del pipeline de integración continua mediante las API del sistema de control de versiones y de la plataforma de CI/CD, los normaliza al esquema de evidencia y reconcilia de manera determinística lo declarado por el orquestador contra lo efectivamente registrado en el repositorio.
*   **Motor evaluador de conformidad (Python):** evalúa cada traza contra la política derivada de la matriz de autonomía mediante un motor de reglas declarativo, y se integra como etapa del pipeline resolviendo permitir, marcar, bloquear o escalar.
*   **Tablero de gobernanza:** aplicación web ligera que presenta los indicadores de riesgo, la salud de las compuertas y la brecha entre autonomía declarada y real.
*   **Banco de pruebas de calibración y re-evaluación periódica:** conjunto de casos de referencia (*golden dataset* con código vulnerable, alucinaciones de dependencias y violaciones de política) y arnés de pruebas automatizado para verificar la efectividad de detección de los agentes, adherencia a fronteras de rol, deriva de contexto (*context drift*) y comportamiento ante inyección de fallos. Este banco se establece como una compuerta de recalibración periódica (trimestral o ante cambio de modelo/prompt) para certificar que los agentes mantienen su precisión de detección y no degradan los guardarraíles.
*   **Herramientas de análisis:** scripts de procesamiento del conjunto de datos históricos de solicitudes de integración y cálculo de las métricas comparativas antes y después de la intervención.
*   **Corpus normativo de referencia:** ISO/IEC 42001:2023 y su Anexo A; ISO/IEC 27001:2022 y 27002:2022; ISO/IEC 23894:2023; ISO/IEC 5338:2023; NIST AI RMF 1.0 y NIST AI 600-1; NIST SP 800-218A; Reglamento (UE) 2024/1689, con atención a su artículo 14; OWASP *Top 10 for LLM Applications*; y Ley 25.326.

Se deja constancia del alcance del componente instrumental: **no se construye una plataforma de producto**. El esfuerzo de investigación cubre el diseño del esquema de evidencia, la calibración, el banco de pruebas y su documentación; la operación del instrumento sobre el pipeline real se realiza en el marco de la actividad profesional de la autora, lo cual constituye la modalidad de investigación-acción adoptada.

Un punto de diseño central es que ARGOS **integra** el sistema de gestión de seguridad de la información con el de gestión de IA en lugar de proponer dos sistemas paralelos, dado que en una organización de porte pequeño la duplicación de sistemas de gestión es la causa más frecuente de que ninguno de los dos se mantenga vigente.

## Arquitectura

ARGOS se estructura como una arquitectura de gobernanza en capas superpuesta al ciclo de desarrollo. Cada capa produce la entrada de la siguiente, y el orden entre ellas no es arbitrario: constituye el hallazgo principal del artefacto A0.

```text
   CAPA 1 · TOPOLOGÍA (A0)          ¿cómo se estructura el enjambre de agentes?
   ───────────────────────          Determina dónde existen costuras de inspección
              │                     humana y fronteras de captura de evidencia.
              ▼  ¿este diseño admite supervisión?
   CAPA 2 · POLÍTICA (A1+A2)        ¿cuánta libertad se delega, contra qué riesgos?
   ─────────────────────────        Taxonomía de riesgos → niveles A0–A4.
              │
              ▼  a este nivel, estos controles
   CAPA 3 · CONTROL (A2→A3)         Compuertas gobernadas, guardarraíles y punto
   ────────────────────────         de firma humana indelegable.
              │
              ▼  y este registro obligatorio
   CAPA 4 · EVIDENCIA (A3)          Telemetría emitida desde la ejecución y
   ───────────────────────          reconciliada contra el control de versiones.
              │                     Motor evaluador: permite, marca, bloquea, escala.
              ▼  que se agrega y se mide
   CAPA 5 · DECISIÓN (A3)           Indicadores de riesgo para la dirección:
   ──────────────────────           delegar, ampliar o revertir autonomía.
```

**La forma del enjambre determina si el sistema puede ser gobernado.** Dos configuraciones funcionalmente equivalentes no son igualmente gobernables. Un agente único que recibe el requerimiento y devuelve el cambio terminado —diseña, implementa, prueba y documenta— no ofrece punto alguno donde insertar supervisión humana, porque no hay costura; ni dónde capturar evidencia, porque lo ocurrido internamente no dejó frontera observable. Un conjunto de agentes acotados que se transfieren el trabajo produce un punto de control natural y una frontera de evidencia natural en cada pase de mano. La capacidad de supervisar quedó decidida al elegir la topología, meses antes de que la palabra gobernanza apareciera en la conversación: la gobernanza no puede atornillarse a una arquitectura que no la admite.

De allí se desprende un corolario aplicable: **un agente que revisa el trabajo de otro agente no constituye un control**. Si ambos operan sobre modelos de arquitectura semejante comparten puntos ciegos y fallan de manera correlacionada. La configuración aparenta segregación de funciones pero produce duplicación. El principio de independencia del revisor es patrimonio del control interno desde hace décadas; su traducción al escenario agéntico es una de las contribuciones que este trabajo propone.

La matriz Autonomía × Control, en su formulación preliminar, ordena los niveles del siguiente modo:

| Nivel | Qué hace el agente | Control humano | Evidencia obligatoria |
|---|---|---|---|
| **A0** | Sugiere (autocompletado) | Aceptación implícita | Registro de uso |
| **A1** | Redacta el cambio; la persona revisa y firma | Revisión sustantiva obligatoria | Diferencia + revisor identificado + tiempo de revisión |
| **A2** | Ejecuta dentro de guardarraíles | Aprobación por excepción | Traza completa + política aplicada + resultado de compuertas |
| **A3** | Autónomo de extremo a extremo en dominio acotado | Supervisión por muestreo + indicadores | Traza + reconstrucción de la decisión + plan de reversión probado |
| **A4** | Autónomo hasta producción | Interruptor de corte + auditoría continua | Todo lo anterior + evidencia de contención |

La formulación definitiva de los cortes entre niveles y de la evidencia suficiente en cada uno constituye parte del resultado del trabajo, no un supuesto de partida.

# Metodología y cronograma

Se adopta **Design Science Research** (Hevner et al., 2004; Peffers et al., 2007) como paradigma principal, por ser el marco aceptado en ingeniería y sistemas de información para investigación cuyo resultado es la construcción y evaluación rigurosa de un artefacto. Se complementa con **investigación-acción sobre caso único** (Yin, 2018; Runeson y Höst, 2009), lo que habilita una condición poco frecuente: intervenir por diseño, instrumentando la telemetría mientras el pipeline se construye, en lugar de reconstruirla retrospectivamente. La validación externa incorpora un **panel de expertos tipo Delphi**.

**Criterios de éxito pre-registrados.** Los umbrales siguientes se fijan en este Plan, antes de cualquier medición, y no se modifican con posterioridad a ella:

| # | Criterio | Umbral de éxito |
|---|---|---|
| **C1** | Reconstrucción de decisiones: porcentaje de cambios en los que un auditor externo y ciego reconstruye origen, nivel de autonomía, controles ejecutados y firma con su evidencia | Δ ≥ 40 puntos porcentuales entre las mediciones posterior y anterior |
| **C2** | Fidelidad de la traza: discrepancia entre lo declarado por el orquestador y lo registrado en el repositorio y el pipeline | 0 % (tolerancia cero) |
| **C3** | Profundidad de revisión: proporción de cambios de origen agéntico aprobados sin comentario y con menos de 60 segundos por cada 100 líneas | Reducción ≥ 30 % |
| **C4** | No degradación de la entrega *(restricción)*: indicadores DORA de *lead time* y frecuencia de despliegue | Deterioro ≤ 15 % |
| **C5** | Validación externa: consenso del panel (rango intercuartílico ≤ 1 en escala de 1 a 5) sobre cada artefacto | ≥ 75 % de los ítems en la segunda ronda |

C4 se declara como restricción y no como objetivo: un marco que mejorara la trazabilidad destruyendo el tiempo de entrega no resolvería el problema planteado, lo trasladaría.

**Diseño de la validación.** Se emplean cuatro instrumentos complementarios:
1. Una prueba de reconstrucción de evidencia sobre 40 cambios ya integrados (20 anteriores y 20 posteriores a la intervención), auditados por una persona externa y ciega a la condición según rúbrica fijada de antemano.
2. La medición cuantitativa y comparativa previa y posterior sobre el conjunto histórico y productivo de solicitudes de integración, contrastando los indicadores del ciclo de desarrollo antes y después de aplicar la combinación gobernada de agentes.
3. Un panel Delphi de ocho expertos en dos rondas, para el cual se cursan doce invitaciones a especialistas en auditoría ISO 27001/42001, líderes técnicos e investigadores.
4. El banco de pruebas de calibración y verificación del orquestador, que evalúa la fidelidad de la traza, adherencia a fronteras de rol, deriva de contexto (*context drift*) e inyección de fallos, instaurando una compuerta periódica (evaluación trimestral sobre *golden dataset*) para auditar que los agentes mantengan su capacidad de detección de riesgos y no degraden los controles con el tiempo.

La intervención se despliega en dos momentos deliberadamente separados: **T0 (15/02/2027)**, instrumentación silenciosa con telemetría pasiva, sin compuertas ni cambio de política, que no contamina la ventana previa; y **T1 (15/03/2027)**, intervención plena con la combinación gobernada de agentes activa. La ventana previa comprende del 01/03/2026 al 14/03/2027 y la posterior del 15/03/2027 al 16/05/2027, con un mínimo declarado de 60 casos.

**Mitigación del sesgo por doble rol.** La autora construye el marco, lo implementa y participa de su evaluación. Esa condición es a la vez el activo que hace posible el trabajo y su principal amenaza de validez. Se adoptan cuatro mitigaciones, todas con fecha comprometida: el pre-registro de los criterios de éxito en este Plan; la evaluación externa mediante auditor ciego y panel independiente; la triangulación de fuentes entre datos del pipeline, inventario documental y entrevistas al equipo; y un diario de investigación fechado que distingue las intervenciones realizadas en calidad de ingeniera de las realizadas en calidad de investigadora, que se incorpora como anexo de la memoria.

**Carga horaria.** La carga horaria será de 8 horas semanales, durante 40 semanas —del 31 de agosto de 2026 al 6 de junio de 2027—, alcanzando un total de 320 horas. La distribución no es uniforme: se declara un receso de dos semanas entre el 28 de diciembre y el 10 de enero, se concentra mayor dedicación en las semanas previas a cada entrega, y se reserva un 9,4 % del presupuesto sin asignar, destinado exclusivamente a absorber desvíos declarados y no a incorporar alcance adicional.

Las fases de trabajo se estructuran en torno a los hitos académicos definidos:

* **Fase 1: Entregas formales y diagnóstico (septiembre – octubre 2026) — 56 h**
  * Redacción y entrega del Plan de Trabajo y del Informe Ético y Social.
  * Inventario del estado de facto de la superficie agéntica: qué agentes y verificaciones operan hoy en el pipeline, con qué autonomía efectiva y qué evidencia dejan.
  * Solicitud, anonimización y análisis exploratorio del conjunto de datos históricos de solicitudes de integración, que constituye la línea de base previa a la intervención.
  * *Hitos académicos: entrega del Plan de Trabajo (1 de septiembre) y del Informe Ético y Social (15 de septiembre).*

* **Fase 2: Construcción de los artefactos conceptuales (noviembre 2026 – enero 2027) — 80 h**
  * Taxonomía de riesgos del desarrollo agentizado (A1), mapeada a controles del Anexo A de ISO/IEC 42001 y de ISO/IEC 27002.
  * Criterios de gobernabilidad de topologías agénticas (A0) y su aplicación diagnóstica sobre el pipeline real.
  * Matriz Autonomía × Control (A2) y clasificación de los agentes relevados, con cálculo de la brecha entre autonomía declarada y real.
  * Convocatoria del panel de expertos, cursada en enero para sesionar en marzo.

* **Fase 3: Instrumentación, calibración y pitch (febrero – marzo 2027) — 48 h**
  * Definición del esquema de evidencia e implementación del recolector de telemetría.
  * Implementación del motor evaluador de conformidad y del tablero de indicadores.
  * Calibración de las compuertas sobre conjunto de referencia y ejecución del banco de pruebas del orquestador.
  * *Hito académico: pitch de tesis, defensa intermedia de avance (23 de febrero).*

* **Fase 4: Validación empírica (marzo – mayo 2027) — 60 h**
  * Ejecución de las dos rondas del panel de expertos y análisis de consenso.
  * Pruebas de reconstrucción de evidencia sobre las ventanas previa y posterior.
  * Análisis comparativo contra los umbrales pre-registrados y cálculo del tamaño del efecto.

* **Fase 5: Consolidación y cierre (mayo – junio 2027) — 46 h**
  * Integración de los capítulos redactados de manera incremental al cierre de cada fase, discusión, limitaciones y anexos metodológicos.
  * *Hito académico: entrega del borrador completo de la memoria (6 de junio) y defensa final ante el tribunal (junio–julio 2027).*

Las 30 horas restantes corresponden a la reserva sin asignar para contingencias y absorción de desvíos declarados.

**Riesgos y contingencia.** El riesgo principal es la eventual indisponibilidad del conjunto de datos históricos, cuya recepción se compromete para el 9 de octubre de 2026. En ese supuesto se activa un plan alternativo previamente acordado: el eje empírico se traslada al inventario del estado de facto y a la prueba de reconstrucción sobre la ventana posterior, con mayor peso relativo del panel de expertos. El segundo riesgo es la demora de la intervención, mitigado por una configuración mínima viable que prescinde del tablero, dado que este no condiciona la medición. El tercero es un tamaño de muestra posterior insuficiente, con extensión de la ventana con cargo a la reserva horaria. Finalmente, el trabajo no depende de que la organización se certifique en norma alguna: la empresa es caso de estudio, no dependencia del diseño.

# Bibliografía

Bainbridge, L. (1983). Ironies of automation. *Automatica, 19*(6), 775–779.

DORA. (2025). *State of AI-assisted software development report*. DORA / Google Cloud.

Elish, M. C. (2019). Moral crumple zones: Cautionary tales in human-robot interaction. *Engaging Science, Technology, and Society, 5*, 40–60.

Forsgren, N., Humble, J., & Kim, G. (2018). *Accelerate: The science of lean software and DevOps*. IT Revolution Press.

Hevner, A. R., March, S. T., Park, J., & Ram, S. (2004). Design science in information systems research. *MIS Quarterly, 28*(1), 75–105.

Hong, S., Zheng, X., Chen, J., Cheng, Y., Zhang, C., Wang, Z., … Zhou, M. (2024). MetaGPT: Meta programming for a multi-agent collaborative framework. *International Conference on Learning Representations (ICLR 2024)*.

Hou, X., Zhao, Y., Liu, Y., Yang, Z., Wang, K., Li, L., … Lo, D. (2024). Large language models for software engineering: A systematic literature review. *ACM Transactions on Software Engineering and Methodology*.

International Organization for Standardization. (2022). *ISO/IEC 27001:2022 — Information security, cybersecurity and privacy protection: Information security management systems — Requirements*.

International Organization for Standardization. (2022). *ISO/IEC 27002:2022 — Information security, cybersecurity and privacy protection: Information security controls*.

International Organization for Standardization. (2023). *ISO/IEC 5338:2023 — Information technology: Artificial intelligence — AI system life cycle processes*.

International Organization for Standardization. (2023). *ISO/IEC 23894:2023 — Information technology: Artificial intelligence — Guidance on risk management*.

International Organization for Standardization. (2023). *ISO/IEC 42001:2023 — Information technology: Artificial intelligence — Management system*.

Jiménez, C. E., Yang, J., Wettig, A., Yao, S., Pei, K., Press, O., & Narasimhan, K. (2024). SWE-bench: Can language models resolve real-world GitHub issues? *International Conference on Learning Representations (ICLR 2024)*.

León XIV. (2026, 15 de mayo). *Carta encíclica Magnifica Humanitas: Sobre la custodia de la persona humana en el tiempo de la inteligencia artificial*. Ciudad del Vaticano.

National Institute of Standards and Technology. (2023). *Artificial Intelligence Risk Management Framework (AI RMF 1.0)* (NIST AI 100-1). U.S. Department of Commerce.

National Institute of Standards and Technology. (2024). *Artificial Intelligence Risk Management Framework: Generative Artificial Intelligence Profile* (NIST AI 600-1). U.S. Department of Commerce.

National Institute of Standards and Technology. (2024). *Secure Software Development Practices for Generative AI and Dual-Use Foundation Models* (NIST SP 800-218A). U.S. Department of Commerce.

OWASP Foundation. (2025). *OWASP Top 10 for Large Language Model Applications*.

Parasuraman, R., & Riley, V. (1997). Humans and automation: Use, misuse, disuse, abuse. *Human Factors, 39*(2), 230–253.

Parlamento Europeo y Consejo de la Unión Europea. (2024). *Reglamento (UE) 2024/1689 por el que se establecen normas armonizadas en materia de inteligencia artificial*. Diario Oficial de la Unión Europea.

Peffers, K., Tuunanen, T., Rothenberger, M. A., & Chatterjee, S. (2007). A design science research methodology for information systems research. *Journal of Management Information Systems, 24*(3), 45–77.

Perry, N., Srivastava, M., Kumar, D., & Boneh, D. (2023). Do users write more insecure code with AI assistants? *ACM SIGSAC Conference on Computer and Communications Security (CCS 2023)*.

República Argentina. (2000). *Ley 25.326 de Protección de los Datos Personales*. Boletín Oficial.

Runeson, P., & Höst, M. (2009). Guidelines for conducting and reporting case study research in software engineering. *Empirical Software Engineering, 14*(2), 131–164.

Sandoval, G., Pearce, H., Nisi, T., Karmakar, S., Dolan-Gavitt, B., & Garg, S. (2023). Lost at C: A user study on the security implications of large language model code assistants. *USENIX Security Symposium 2023*.

Yin, R. K. (2018). *Case study research and applications: Design and methods* (6.ª ed.). Sage.

---

### Conformidad de Dirección

**Aprobación del Plan de Trabajo de parte del Director:**

<br>
<br>

__________________________________  
**Prof. Marcos Giagnorio**  
Director Académico de Tesis  
Universidad Austral
