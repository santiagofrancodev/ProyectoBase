# Matriz de Evidencia, Hipótesis y Validación

Este documento articula de forma rigurosa la frontera entre lo que el equipo ha observado directamente en la realidad, las hipótesis de solución formuladas, las preguntas que deben validarse empíricamente y los riesgos éticos asociados.

---

## 1. Clasificación Metodológica

- **Observación directa:** Hechos concretos presenciados o vividos por los integrantes del equipo en terreno o durante emergencias reales. No son especulaciones, pero su representatividad estadística requiere corroboración.
- **Hipótesis:** Supuesto fundamentado de que un cambio de diseño o tecnología producirá un resultado positivo observable para los usuarios.
- **Pregunta de validación:** Interrogante concreto que debe responderse mediante pruebas guiadas, entrevistas o prototipos para confirmar o refutar una hipótesis.
- **Evidencia requerida:** Tipo de dato, testimonio o métrica empírica necesaria para dar por válida una hipótesis.
- **Riesgo ético o de privacidad:** Posibles efectos secundarios no deseados que podrían perjudicar a los damnificados, voluntarios o la integridad de la ayuda.

---

## 2. Matriz de Validación

| # | Observación directa | Hipótesis de solución | Pregunta de validación | Evidencia requerida | Riesgo ético o de privacidad |
| :-: | :--- | :--- | :--- | :--- | :--- |
| **1** | En los centros de acopio comunitarios, los registros de entrada se hacen en cuadernos o chats, sin un identificador único por lote donado. | Si se genera un identificador único con código QR al recibir el lote, se podrá rastrear su historial sin sobrecargar el tiempo de recepción. | ¿Cuánto tiempo adicional toma etiquetar y escanear un lote en el momento pico de recepción frente a anotar en papel? | Medición de tiempos de registro en una prueba simulada de acopio con datos sintéticos (tiempo objetivo: < 30 seg por lote). | Riesgo de que la exigencia tecnológica demore la descarga física de insumos perecederos en plena lluvia o emergencia. |
| **2** | El cambio de turno entre voluntarios de acopio genera pérdida de información sobre qué insumos quedaron efectivamente en bodega (custodia). | Al registrar la transición al estado "Custodiado" asociada a un responsable visible por turno, se delimita la custodia física y se reduce el inventario fantasma. | ¿Están los voluntarios dispuestos a asumir y firmar digitalmente la custodia de un lote al inicio y cierre de su guardia? | Entrevistas estructuradas con 3 a 5 personas con experiencia previa en voluntariado de acopio. | Señalamiento indebido o estigmatización de voluntarios honestos en caso de pérdidas físicas por daño o deterioro de empaques. |
| **3** | La asignación de mercados y kits a destinatarios genera susceptibilidad y rumores de reparto preferencial o discrecional entre líderes comunitarios. | Un registro inalterable y auditable de asignaciones con criterios transparentes permite a la comunidad verificar que los recursos se asignaron equitativamente. | ¿La consulta pública del estado "Asignado" reduce la percepción de favoritismo en un grupo de prueba comunitario? | Encuesta de percepción de confianza y transparencia tras simular la consulta del flujo con líderes comunitarios. | Riesgo de revictimización o exposición de la condición de vulnerabilidad de las familias beneficiarias si se filtran identificadores. |
| **4** | Las constancias de entrega física en papel o firmas en planillas sueltas suelen extraviarse o mojarse, impidiendo la verificación posterior. | Una atestación mínima digital de entrega en el estado "Entregado" proporciona una prueba compartida e incorruptible para el donante y la veeduría. | ¿Es viable obtener una confirmación criptográfica o código de entrega de un damnificado sin exigirle un teléfono inteligente avanzado? | Pruebas de usabilidad con esquemas de validación de baja fricción (p. ej., código numérico impreso o tarjeta de lote). | Exclusión digital de adultos mayores, analfabetas digitales o personas sin acceso a dispositivos móviles durante la crisis. |
| **5** | En emergencias como el sismo del 10 de agosto de 2026, las redes de datos móviles sufren caídas intermitentes o congestión crítica en la zona cero. | Un mecanismo de captura local con sincronización asíncrona diferida hacia Stellar permitirá operar el centro de acopio sin detenerse por falta de señal. | ¿Qué tasa de conflicto o desincronización ocurre al registrar múltiples entregas offline y sincronizarlas por lotes al recuperar la red? | Simulación de desconexión forzada de red durante 2 horas con emisión de 20 transacciones locales y posterior sync. | Confusión entre usuarios si un lote entregado físicamente no aparece como "Entregado" en la red pública hasta varias horas después. |

---

## 3. Principios de Validación con Datos Sintéticos

Para dar cumplimiento a los estándares éticos del programa:

1. **Entorno controlado:** Toda prueba de concepto se ejecutará en entornos de simulación utilizando nombres y direcciones ficticias (datos sintéticos generados específicamente para pruebas).
2. **Cero contacto con información sensible:** No se recolectarán bases de datos de censos reales ni padrones de damnificados de entidades oficiales sin un marco de investigación formalmente aprobado.
3. **Validación de usabilidad antes que volumen:** Se priorizará validar si un voluntario bajo estrés comprende la interfaz antes de medir capacidades de transacciones por segundo (TPS).
