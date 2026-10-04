# Contexto del Proyecto — Ayuda con Destino

---

## 1. Relato del problema y punto de partida

Tras una emergencia o desastre socio-natural, la movilización de ayuda solidaria ciudadana e institucional suele ser masiva y espontánea. No obstante, la logística de recepción, acopio y distribución en el terreno suele colapsar bajo esquemas de gestión informal y fragmentada.

Este proyecto toma como punto de referencia el contexto regional del sismo del 10 de agosto de 2026, experimentado en las ciudades de Pereira y Armenia (Eje Cafetero, Colombia). Durante situaciones de esta naturaleza, los centros de acopio improvisados o comunitarios reciben alimentos, ropa, frazadas e insumos de aseo de parte de cientos de donantes individuales y empresas locales.

En el fragor de la emergencia, los registros de entrada y salida se realizan frecuentemente en cuadernos de papel, planillas manuales o chats de mensajería instantánea. Esta precariedad provoca que la información se fracture conforme los voluntarios cambian de turno o se desplazan a zonas de entrega. En consecuencia, se genera un manto de incertidumbre: los donantes desconocen si sus aportes llegaron a quienes realmente los necesitaban, los coordinadores no pueden auditar inventarios con facilidad y las familias damnificadas quedan sometidas a decisiones discrecionales sin posibilidad de corroborar la equidad del reparto.

### Enunciado central del problema

> *Las familias afectadas por una emergencia no pueden verificar cómo se asignan los suministros de ayuda porque los registros de acopio se manejan de forma fragmentada e informal entre distintos administradores locales.*

El objetivo de esta investigación de producto no es sostener que la tecnología blockchain sea una solución mágica para la ayuda humanitaria, sino evaluar con criterio de ingeniería si un registro de auditoría compartido, verificable y con garantías de inalterabilidad puede reducir la dependencia de la confianza ciega en un administrador central, mitigando sospechas y mejorando la rendición de cuentas operativa.

---

## 2. Personas y actores iniciales

| Actor / Rol | Papel en el flujo | Necesidad principal | Punto de fricción actual |
| :--- | :--- | :--- | :--- |
| **Persona damnificada / Cabeza de hogar afectada** | Usuario principal y destinatario final del lote de ayuda. | Conocer qué suministros están disponibles, si le fueron asignados y verificar la entrega efectiva. | Falta de visibilidad; incertidumbre ante asignaciones percibidas como discrecionales o preferenciales. |
| **Donante (individual o colectivo)** | Entrega insumos en especie en el centro de acopio o punto de recolección. | Obtener certeza verificable de que sus recursos ingresaron al circuito y llegaron a destino. | Dependencia de mensajes informales o ausencia total de constancia tras dejar los bienes. |
| **Voluntario / Administrador de acopio** | Recibe, clasifica, custodia en bodega y entrega los lotes de ayuda. | Disponer de una herramienta ágil para registrar entradas/salidas sin duplicar trabajo en turnos rotativos. | Cuadernos dispersos, pérdida de notas, sospechas injustificadas de desvío por falta de pruebas formales. |
| **Veeduría comunitaria / Organización local** | Audita y hace seguimiento cívico del reparto de recursos en el territorio. | Consultar el historial completo de movimientos para verificar equidad y consistencia en el acopio. | Dificultad para auditar registros en papel o chats privados; imposibilidad de reconstruir la trazabilidad. |

---

## 3. Flujo operativo acotado del MVP

El alcance inicial se focaliza estrictamente en **donaciones en especie** (por ejemplo: mercados básicos de alimentos no perecederos, kits de higiene personal, cobijas o ropa clasificada). Quedan expresamente descartadas las transacciones monetarias.

El ciclo de trazabilidad se modela en un flujo finito de cuatro estados:

```text
[ Recibido ] ──> [ Custodiado ] ──> [ Asignado ] ──> [ Entregado ]
```

1. **Recibido:**
   - **Disparador:** Donante entrega bienes en el centro de acopio.
   - **Registro:** Se conforma un lote físico, se le asigna un identificador único (ID de lote / QR preliminar), se clasifica la categoría (p. ej., "Alimentos - 10 kg") y se asocia la marca de tiempo de recepción.
2. **Custodiado:**
   - **Disparador:** El lote se almacena formalmente en la bodega o carpa del centro de acopio.
   - **Registro:** Se asocia el lote al custodio o responsable del inventario en ese turno operativo.
3. **Asignado:**
   - **Disparador:** La coordinación del centro determina el destino o núcleo familiar beneficiario según el censo de necesidades.
   - **Registro:** El estado del lote pasa a "Asignado" vinculándose a un identificador sintético u orden de entrega comunitaria, resguardando en todo momento la identidad y ubicación real de la familia.
4. **Entregado:**
   - **Disparador:** El lote es recibido físicamente por la persona o familia destinataria.
   - **Registro:** Se marca como completado con una evidencia criptográfica o atestación mínima (firma de entrega o código de confirmación), cerrando el ciclo del lote.

---

## 4. Alcance y límites del proyecto

### Dentro del alcance del descubrimiento y MVP

- Modelado formal de la máquina de estados del lote de ayuda.
- Definición de identificadores únicos por lote con soporte de código visual (QR o equivalente).
- Registro auditable de marcas de tiempo y transiciones de estado.
- Mecanismo de consulta pública o semipública del historial del lote sin revelar datos protegidos.
- Pruebas conceptuales y de usabilidad basadas en datos sintéticos.

### Fuera de alcance (Exclusiones estrictas del MVP inicial)

- **Dinero real y activos financieros:** Ni moneda de curso legal (fiat), ni criptoactivos, ni vales, ni trueque digital.
- **Incentivos económicos tokenizados:** Sin esquemas de recompensa o *gamificación* para voluntarios o donantes.
- **Beneficios tributarios o fiscales:** Sin integración con entidades recaudadoras ni certificados tributarios.
- **Donaciones internacionales y logística mayor:** No abarca aduanas, contenedores de importación ni fletes intercontinentales.
- **Aplicación móvil nativa completa:** Se prioriza diseño web responsivo o interfaz ligera orientada a condiciones de campo.
- **Automatización de verificación física:** No se pretende reemplazar la inspección humana de los bienes mediante sensores IoT complejos; la atestación física recae en los actores responsables.
- **Implementación blockchain prematura:** Sin contratos inteligentes ni scripts funcionales en el repositorio durante las semanas 1 y 2.

---

## 5. Visión técnica futura y decisiones preliminares

Para cuando el programa académico habilite la etapa de implementación técnica (Semana 3 en adelante), se mantendrán las siguientes premisas arquitectónicas:

1. **Privacidad por diseño (Off-chain data):** Ningún dato personal (nombres reales, documentos de identidad, teléfonos, direcciones exactas de damnificados) residirá en un registro distribuido o cadena de bloques pública. Los registros públicos futuros solo contendrán metadatos mínimos: ID del lote, tipo genérico de bien, timestamp, hash criptográfico de constancias y estado actual.
2. **Resiliencia ante conectividad intermitente:** En zonas de catástrofe las redes móviles suelen colapsar. La arquitectura contempla el principio de **captura local u offline con sincronización posterior diferida**. Bajo ninguna circunstancia se prometerá operación distribuida en tiempo real sin conexión física de red.
3. **Evaluación de arquitectura sobre Stellar:** La elección entre transacciones estándar de Stellar (cuentas, memos, transacciones multifirma) frente a contratos inteligentes en Soroban es una decisión técnica que se contrastará en función del costo, simplicidad y mantenibilidad, sin adoptar tecnologías innecesariamente complejas de manera anticipada.

---

## 6. Criterios éticos y tratamiento de información

- **Rigor en las observaciones:** Las observaciones directas aportadas por los integrantes (Gustavo en distribución de mercados en Pereira y Santiago en el contexto del sismo de 2026) son puntos de partida de campo que deben contrastarse empíricamente.
- **Prevención de estigmatización y acusaciones infundadas:** No se emitirán juicios ni afirmaciones sobre corrupción, delitos específicos ni convenios institucionales sin una fuente oficial y verificable. Las fallas observadas se analizan como problemas sistémicos de diseño de procesos y herramientas.
- **Protección estricta a la vulnerabilidad:** Las poblaciones afectadas por emergencias se encuentran en estado de extrema vulnerabilidad. La tecnología debe proteger su dignidad y privacidad, evitando cualquier riesgo de revictimización o exposición pública indebida.
