---
name: tutor-sync
description: Procesa y documenta las conversaciones, notas de reuniones y feedback del Director Académico (Marcos Giagnorio), generando minutas estructuradas en kb/tutorias/, analizando impactos en cascada en borradores (docs/), ADRs (kb/adrs/), ROADMAP.md, kb/context.md y el diario de investigación (kb/diario/).
---

# Protocolo de Procesamiento de Feedback de Tutoría (`tutor-sync`)

Cuando la usuaria mencione que tuvo una reunión con Marcos, o pegue notas en crudo, audios transcriptos o resúmenes de una sesión de tutoría, seguí este procedimiento estricto:

## 1. Entrevista y recepción de notas
* Si las notas son muy escuetas o ambiguas, hacé hasta 2 o 3 preguntas de clarificación breves para capturar el fondo del feedback de Marcos.
* Identificá:
  - Fecha y horario de la reunión.
  - Temas tratados.
  - Observaciones y críticas específicas de Marcos.
  - Acuerdos alcanzados.
  - Próximos compromisos y plazos.

## 2. Generación de la minuta estructurada
* Creá un nuevo archivo en `kb/tutorias/AAAA-MM-DD-tutoria-marcos.md` basado en [`kb/tutorias/TEMPLATE-tutoria.md`](file:///home/macky/Projects/tesis/kb/tutorias/TEMPLATE-tutoria.md).
* Redactá con precisión técnica y tono formal todo lo tratado, clasificando el feedback en:
  - Sobre entregables y documentos formales (`docs/`).
  - Sobre metodología, gobernanza y artefactos (A0–A3).
  - Sobre la relación con la cátedra y el tribunal.

## 3. Análisis de Impacto en Cascada y Actualización Automática

El agente debe proponer y ejecutar los cambios correspondientes:

1. **Borradores de entrega (`docs/`):**
   - Si Marcos pidió cambios de redacción, alcance o énfasis en el Plan de Trabajo (`docs/03-plan-de-trabajo/Plan-de-Trabajo-Alimena.md`), Informe Ético (`docs/02-informe-etico/`) o Pitch (`docs/04-pitch-tesis/`), aplicar las ediciones de inmediato.
2. **Registro de Acuerdos (`kb/context.md` §20):**
   - Añadir el acuerdo numerado en la sección "KB de Acuerdos y Decisiones con la Directora de Tesis / Cátedra".
3. **Decisiones de Arquitectura / Metodología (`kb/adrs/`):**
   - Si el feedback implica un cambio estructural en el marco o el diseño experimental, crear un nuevo ADR o actualizar el correspondiente.
4. **Cronograma y Entregas (`ROADMAP.md`):**
   - Ajustar fechas, tareas o hitos si se acordó una modificación en el calendario.
5. **Diario de investigación (`kb/diario/`):**
   - Preparar los puntos de insumo para la sección "Rol investigadora" y "Donde los dos roles se cruzaron" de la semana en curso.

## 4. Reporte de Cierre a la Usuaria
Presentá un resumen conciso con:
- Enlace a la minuta generada en `kb/tutorias/`.
- Lista de archivos modificados con el diff resumido de lo que cambió.
- Tareas pendientes con su responsable y fecha límite.
