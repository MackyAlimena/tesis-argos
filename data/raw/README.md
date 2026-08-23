# Dataset Histórico de Pull Requests (Línea de Base)

> ⚠️ **Riesgo crítico del proyecto:** Este dataset debe capturarse antes de septiembre 2026 para congelar la línea de base "pre-intervención" (el estado del desarrollo antes de aplicar el marco ARGOS).

## Especificación del Export Requerido

Campos mínimos requeridos por cada PR de los últimos 6–12 meses:

| Campo | Tipo | Descripción |
|---|---|---|
| `pr_id` | String / Int | Identificador único anonimizado del PR |
| `repo_id` | String | Identificador anonimizado del repositorio |
| `created_at` | Timestamp | Fecha y hora de apertura del PR |
| `closed_at` | Timestamp | Fecha y hora de cierre / merge |
| `author_type` | Categoría | `human` o `ai_agent` |
| `reviewer_id` | String | Identificador anonimizado del revisor principal |
| `review_time_seconds` | Int | Diferencia entre asignación/apertura y aprobación |
| `lines_added` | Int | Líneas de código agregadas |
| `lines_deleted` | Int | Líneas de código eliminadas |
| `files_changed` | Int | Cantidad de archivos modificados |
| `comments_count` | Int | Número de comentarios de revisión sustantivos |
| `approved_without_comments` | Boolean | `true` si fue aprobado en 1-click sin comentarios |
| `defect_escaped` | Boolean | Si el cambio causó un rollback / hotfix posterior |
