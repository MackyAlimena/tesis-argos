# Registro de Tutorías y Acuerdos con el Director

> **Propósito:** Documentar de manera sistemática cada reunión, llamada o intercambio de trabajo con el Director Académico (**Prof. Marcos Giagnorio**).
> **Por qué es crítico:** 
> 1. Asegura que ningún feedback, corrección u observación del director quede en el aire.
> 2. Traduce de inmediato los acuerdos a cambios en los documentos (`docs/`), decisiones de arquitectura (`kb/adrs/`), acuerdos de contexto (`kb/context.md` §20) y entradas del diario (`kb/diario/`).
> 3. Constituye evidencia auditable del proceso continuo de dirección y seguimiento del Trabajo de Grado.

---

## Convención de archivos

* Cada reunión se documenta con el formato: `AAAA-MM-DD-tutoria-marcos.md` (ej. `2026-08-31-tutoria-marcos.md`).
* Se utiliza la plantilla oficial: [`TEMPLATE-tutoria.md`](TEMPLATE-tutoria.md).

---

## Flujo de procesamiento post-reunión

1. **Captura de notas en crudo:** La autora anota durante o inmediatamente después de la reunión.
2. **Procesamiento y estructuración:** Se activa la skill o agente de tutoría pasando las notas en bruto.
3. **Generación de la minuta:** Se crea el archivo en `kb/tutorias/` completando todas las secciones.
4. **Ejecución del plan de impacto:**
   - Aplicación de correcciones en los borradores de entrega (`docs/`).
   - Redacción o actualización de ADRs si hubo cambios conceptuales o metodológicos.
   - Sincronización en `kb/context.md` y `ROADMAP.md`.
   - Alimentación de la sección "Rol investigadora" en `kb/diario/`.
