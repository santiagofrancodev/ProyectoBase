# Registro de Decisiones de Arquitectura y Producto (ADR)

Este documento registra las decisiones clave tomadas por el equipo a lo largo del diseño del proyecto **Ayuda con Destino**.

Cada decisión cuenta con un estado formal:
- **`Propuesta`**: En formulación o evaluación preliminar por parte del equipo.
- **`Aceptada`**: Consensuada y adoptada como directriz vinculante para el proyecto.
- **`Pendiente`**: Identificada pero postergada deliberadamente hasta contar con mayor evidencia técnica o empírica.

---

## Índice de Decisiones

| ID | Título | Estado | Fecha |
| :--- | :--- | :--- | :--- |
| **ADR-001** | MVP limitado estrictamente a donaciones en especie | `Aceptada` | 2026-09-27 |
| **ADR-002** | Máquina de estados finita de cuatro etapas (`Recibido → Custodiado → Asignado → Entregado`) | `Aceptada` | 2026-09-27 |
| **ADR-003** | Exclusión absoluta de datos personales en registros distribuidos públicos (Off-chain data) | `Aceptada` | 2026-09-27 |
| **ADR-004** | Postergación del desarrollo de código y contratos hasta la fase técnica del bootcamp (Semana 3) | `Aceptada` | 2026-09-27 |
| **ADR-005** | Evaluación comparativa de Stellar Classic vs. Soroban diferida a la fase de prototipado | `Pendiente` | 2026-09-27 |
| **ADR-006** | Captura local con sincronización posterior diferida para mitigar baja conectividad | `Propuesta` | 2026-09-27 |

---

## Detalle de Decisiones

### ADR-001: MVP limitado estrictamente a donaciones en especie
- **Estado:** `Aceptada`
- **Contexto:** En situaciones de desastre, existen múltiples vectores de ayuda (donaciones monetarias, voluntariado, logística de maquinaria pesada, bienes en especie). Pretender abarcar flujos financieros introduce complejidades regulatorias, cambiarias, tributarias y de seguridad financiera que desviarían el objetivo central del MVP.
- **Decisión:** El Producto Mínimo Viable se limita exclusivamente a **bienes físicos en especie** (mercados de víveres, kits de higiene, abrigo, insumos básicos). Quedan fuera de alcance: dinero fiat, criptoactivos, vales y esquemas de trueque.
- **Consecuencias:**
  - *Positivas:* Simplifica radicalmente el modelo de datos y la validación en centros de acopio reales; evita fricciones regulatorias de intermediación financiera.
  - *Negativas:* No resuelve la trazabilidad de ayudas donadas en dinero en efectivo o transferencias bancarias directas.

---

### ADR-002: Máquina de estados finita de cuatro etapas
- **Estado:** `Aceptada`
- **Contexto:** El proceso logístico de un centro de acopio puede dividirse en decenas de subetapas (pesaje, desinfección, empaque, apilado, estiba, transporte). Modelar un ciclo con excesivos estados en el primer prototipo aumentaría la fricción para los voluntarios en turnos de emergencia.
- **Decisión:** Adoptar una secuencia lineal simple y estricta de cuatro estados:
  $$\text{Recibido} \longrightarrow \text{Custodiado} \longrightarrow \text{Asignado} \longrightarrow \text{Entregado}$$
- **Consecuencias:**
  - *Positivas:* Reduce la carga operativa sobre los voluntarios de acopio al registrar transiciones; permite una visualización clara e intuitiva para donantes y familias afectadas.
  - *Negativas:* Agrupa subprocesos internos que podrían ser relevantes en almacenes de gran escala (como mermas o redistribución intercentros).

---

### ADR-003: Exclusión de datos personales en registros distribuidos (Off-chain)
- **Estado:** `Aceptada`
- **Contexto:** Las cadenas de bloques públicas proporcionan inmutabilidad y transparencia global, lo que entra en conflicto directo con los derechos de privacidad, el derecho al olvido y la protección a personas en situación de vulnerabilidad extrema tras una emergencia.
- **Decisión:** Queda terminantemente prohibido almacenar nombres reales, cédulas, números telefónicos, coordenadas GPS exactas o fotografías identificables en cualquier ledger o contrato público. La cadena solo contendrá hashes criptográficos, identificadores sintéticos de lote, marcas de tiempo y tipos genéricos de bien.
- **Consecuencias:**
  - *Positivas:* Cumplimiento estricto de privacidad por diseño; protege la dignidad física y jurídica de los damnificados.
  - *Negativas:* Requiere diseñar una capa de almacenamiento local/privado complementaria para que los centros de acopio consulten internamente las órdenes físicas asociadas a cada hash.

---

### ADR-004: Postergación de código y contratos hasta la Semana 3
- **Estado:** `Aceptada`
- **Contexto:** Es común en proyectos tecnológicos apresurarse a programar contratos inteligentes antes de tener claridad sobre el problema, las necesidades del usuario y la pertinencia técnica del caso.
- **Decisión:** Mantener el repositorio estrictamente documental y de formulación durante las Semanas 1 y 2. No se crearán contratos inteligentes, scripts ejecutables, SDKs ni dependencias de software hasta que el cronograma académico del bootcamp lo establezca en la Semana 3.
- **Consecuencias:**
  - *Positivas:* Fuerza al equipo a consolidar los cimientos conceptuales, la arquitectura de información y la validación de hipótesis sin distraerse en detalles de implementación temprana.
  - *Negativas:* Ninguna; se alinea estrictamente con los criterios de evaluación del programa.

---

### ADR-005: Evaluación comparativa de Stellar Classic vs. Soroban
- **Estado:** `Pendiente`
- **Contexto:** Stellar permite emitir activos y registrar memos en transacciones estándar de bajo costo, pero también cuenta con el entorno de contratos inteligentes Soroban (WASM/Rust) para ejecutar lógica determinista en cadena.
- **Decisión:** Diferir la elección tecnológica entre Stellar Classic y Soroban a la Semana 3. Se evaluará si una máquina de estados con transacciones multifirma y memos nativos es suficiente o si la lógica de autorización por roles de acopio justifica el despliegue de un contrato inteligente en Soroban.
- **Consecuencias:**
  - *Positivas:* Evita sobreingeniería prematura; permite tomar la decisión con base en el aprendizaje técnico de las sesiones 5 y 6 del bootcamp.
  - *Negativas:* Mantiene abierta la arquitectura de software hasta el inicio de la fase de implementación.

---

### ADR-006: Captura local y sincronización diferida para baja conectividad
- **Estado:** `Propuesta`
- **Contexto:** En catástrofes naturales, la infraestructura eléctrica y las antenas de telecomunicaciones suelen presentar caídas severas o congestión total. Una solución que requiera conexión a internet permanente para operar el centro de acopio quedaría inutilizada en el peor momento.
- **Decisión:** Proponer como hipótesis de diseño un esquema de captura de datos local (almacenamiento en caché del dispositivo o base de datos local ligera) con capacidad de firma criptográfica local y sincronización encolada hacia la red Stellar una vez que se restablezca la conectividad.
- **Consecuencias:**
  - *Positivas:* Hace la herramienta viable en condiciones de infraestructura degradada; no detiene la operación física de entrega de ayuda.
  - *Negativas:* Introduce desafíos de resolución de concurrencia y desfase temporal entre la entrega física y la confirmación final visible en la red.
