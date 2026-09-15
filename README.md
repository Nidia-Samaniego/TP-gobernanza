# Trabajo Práctico Semana 1: Gobernanza y Calidad de Software



## 1. Definition of Done (DoD)

La siguiente **Definition of Done (DoD)** establece los criterios de calidad mínimos y obligatorios que debe cumplir cada incremento de código o *User Story* antes de ser considerada oficialmente "Terminada" e integrada en la rama principal (`main`).

* **Integridad de compilación:** El código debe compilar de forma exitosa en el entorno local y en el servidor de Integración Continua (CI). No se permiten advertencias (*warnings*) críticas que comprometan la estabilidad del sistema.
* **Validación de pruebas automatizadas:** Todas las pruebas unitarias, de integración y de extremo a extremo (E2E) existentes deben ejecutarse y pasar con éxito (0% de fallos). Se prohíbe deshabilitar o saltar (*skip*) pruebas para forzar el éxito del pipeline.
* **Umbrales mínimos de cobertura de código:** El código nuevo o modificado debe alcanzar un **mínimo del 80% de cobertura (Code Coverage)** en pruebas unitarias. Este umbral será auditado automáticamente mediante herramientas de análisis estático.
* **Revisión por pares obligatoria (Peer Review):** Todo cambio requiere la aprobación de al menos **dos (2) ingenieros de software** del equipo a través de un *Pull Request* (PR). Ningún desarrollador puede auto-aprobarse un cambio.
* **Gobernanza de estilo:** El código debe cumplir estrictamente con los estándares y guías de estilo del lenguaje (por ejemplo, PEP 8, ESLint). El formateador automático y el *linter* no deben arrojar errores antes del despliegue.
* **Sustento de la documentación técnica:** Se deben actualizar los diagramas de arquitectura afectados, el archivo `README.md` (si aplica) y la documentación de la API (Swagger/OpenAPI). Además, el código debe incluir comentarios claros en algoritmos complejos.

---

## 2. Matriz de Categorización (Sistema de Etiquetas)

Para auditar la trazabilidad y garantizar que el estado de cumplimiento de la DoD se mantenga transparente, se propone el siguiente sistema de etiquetas (*Labels*):

| Etiqueta (Label) | Color Sugerido | Descripción Técnica | Justificación Técnica ante la DoD |
| :--- | :--- | :--- | :--- |
| `bug` | `#d73a4a` | Fallo o comportamiento inesperado que rompe la funcionalidad actual del sistema. | **Bloqueante de DoD:** Ninguna historia puede cerrarse si introduce un bug. Permite priorizar parches y verificar que las pruebas automatizadas incluyan el caso de fallo. |
| `technical-debt` | `#7057ff` | Código que requiere refactorización, optimización o actualización de librerías obsoletas. | **Control de Umbrales:** Identifica código que no cumple con la gobernanza de estilo o la cobertura mínima del 80%, mapeando qué partes del sistema necesitan remediación. |
| `documentation` | `#0075ca` | Cambios, mejoras o adiciones exclusivas a los archivos de documentación técnica (Wiki, OpenAPI, README). | **Sustento Técnico:** Garantiza la auditoría del criterio de documentación en la DoD. Permite validar que el conocimiento del sistema esté actualizado antes del despliegue. |
| `feature` | `#a2eeef` | Desarrollo de una nueva funcionalidad, módulo o requerimiento del negocio. | **Disparador de Ciclo:** Activa de forma estricta los 6 criterios de la DoD. Obliga a que el nuevo incremento pase por revisión de pares y análisis de cobertura. |
