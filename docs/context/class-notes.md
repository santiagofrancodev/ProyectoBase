# Notas de Clase y Fundamentos de Aprendizaje â€” BB101

> [!NOTE]
> **AclaraciÃ³n metodolÃ³gica:** Este documento es una sÃ­ntesis interna de notas de clase estructurada para el proyecto **Ayuda con Destino**. Refleja los conceptos clave de las primeras cuatro sesiones del programa **Blockchain Builders 101** (dictado por BAF, Ruta N y Stellar). En caso de cualquier duda o discrepancia, prevalecerÃ¡ siempre el material y las grabaciones oficiales del bootcamp.

---

## SesiÃ³n 1: Fundamentos de Blockchain y Criterios de Pertinencia

### 1. Â¿QuÃ© es y cÃ³mo opera un registro distribuido?
Una cadena de bloques es un libro contable digital, descentralizado y distribuido entre mÃºltiples nodos independientes que mantienen una copia sincronizada del estado sin depender de una Ãºnica entidad rectora. La integridad de la informaciÃ³n no reposa en la honorabilidad de un administrador, sino en la criptografÃ­a y el consenso de la red.

### 2. Criterios para evaluar si Blockchain aporta valor real
No todo problema de informaciÃ³n requiere una cadena de bloques. Una base de datos relacional tradicional (p. ej., PostgreSQL) es mÃ¡s rÃ¡pida, econÃ³mica y sencilla de operar en la gran mayorÃ­a de los casos centralizados. Blockchain aporta valor real **Ãºnicamente** cuando se cumplen de manera concurrente tres condiciones estructurales:

1. **MÃºltiples partes que no confÃ­an plenamente entre sÃ­:** Actores independientes (p. ej., donantes, comitÃ©s de acopio, voluntarios y veedurÃ­as ciudadanas) necesitan colaborar e intercambiar informaciÃ³n sensible sobre el mismo activo o flujo, pero ninguno desea delegar el control exclusivo de la base de datos en otra parte.
2. **Necesidad estricta de un histÃ³rico inalterable (Append-only audit trail):** Los registros del pasado no pueden ser editados, recalculados ni borrados retrospectivamente por ningÃºn actor, garantizando que cualquier anomalÃ­a, alteraciÃ³n o intento de desvÃ­o quede expuesto en el tiempo.
3. **EliminaciÃ³n o reducciÃ³n de un intermediario que concentra la confianza:** En esquemas tradicionales, un operador centralizado actÃºa como punto Ãºnico de falla (y de susceptibilidad a corrupciÃ³n o presiones). El registro descentralizado transfiere la confianza a un protocolo auditable y verificable por todas las partes interesadas.

---

## SesiÃ³n 2: Problemas, Modelado de Fricciones y Fundamentos CriptogrÃ¡ficos

### 1. Mapeo de flujos y detecciÃ³n de fricciones
- Para resolver un problema tÃ©cnico primero hay que entender el flujo actual de valor y de informaciÃ³n en el mundo real.
- Las fricciones no son genÃ©ricas: deben ubicarse en un paso concreto del recorrido, asociarse a una causa raÃ­z operativa y delimitar claramente a quÃ© rol o usuario impactan negativamente.
- La tecnologÃ­a se introduce Ãºnicamente en la fricciÃ³n priorizada donde la hipÃ³tesis de descentralizaciÃ³n genera un diferencial concreto frente a las soluciones existentes.

### 2. CriptografÃ­a aplicada: Hashes y Firmas Digitales
- **Funciones Hash CriptogrÃ¡ficas (SHA-256):** Algoritmos deterministas unidireccionales que transforman cualquier volumen de datos en una huella digital de longitud fija. Son la base de la inmutabilidad y la verificaciÃ³n de integridad. Un cambio infinitesimal en el archivo o registro genera un hash completamente diferente (*efecto avalancha*).
- **CriptografÃ­a AsimÃ©trica (Par de llaves pÃºblica / privada):**
  - La *llave privada* firma transacciones de forma intransferible, garantizando autenticidad y no repudio.
  - La *llave pÃºblica* permite a cualquier tercero verificar matemÃ¡ticamente que la firma fue generada por el titular legÃ­timo, sin exponer la llave secreta.

### 3. SeparaciÃ³n estricta entre datos pÃºblicos y privados (Off-chain vs. On-chain)
- **Principio cardinal:** En una cadena de bloques pÃºblica, toda informaciÃ³n registrada es permanente y accesible para cualquier observador.
- **Privacidad y cumplimiento:** Los datos personales identificables (nombres, documentos de identidad, historiales mÃ©dicos, domicilios familiares) jamÃ¡s deben residir en la cadena de bloques.
- **PatrÃ³n de evidencia (Commitment scheme):** La informaciÃ³n sensible se almacena de forma privada (fuera de cadena u *off-chain*); en la cadena Ãºnicamente se ancla la marca de tiempo, el identificador sintÃ©tico y el **hash** de la constancia. De este modo se puede probar que un documento existÃ­a y no ha sido alterado, sin exponer su contenido a miradas no autorizadas.

---

## SesiÃ³n 3: DiseÃ±o de Producto, Alcance de MVP y GestiÃ³n Ãgil

### 1. Lean Canvas y DefiniciÃ³n del MVP
- El Lean Canvas actÃºa como un mapa vivo de supuestos crÃ­ticos de negocio: problema, segmento de clientes, propuesta Ãºnica de valor, soluciÃ³n, canales, fuentes de ingreso/sostenibilidad, estructura de costos, mÃ©tricas clave y ventaja injusta.
- **DefiniciÃ³n de MVP (Producto MÃ­nimo Viable):** No es un producto incompleto o defectuoso, sino la versiÃ³n mÃ¡s pequeÃ±a y controlada de la soluciÃ³n que permite recorrer el ciclo completo de valor y validar las hipÃ³tesis centrales con usuarios reales, minimizando el desperdicio de desarrollo.

### 2. Historias de Usuario con Criterios de AceptaciÃ³n
- Formato estÃ¡ndar de historia de usuario:
  $$\text{Como } [\text{rol}], \text{ quiero } [\text{acciÃ³n / capacidad}], \text{ para } [\text{beneficio o impacto esperado}].$$
- Cada historia debe ser comprobable mediante **Criterios de AceptaciÃ³n** claros (condiciones objetivas bajo las cuales la historia se considera terminada y aceptada por el equipo).

### 3. PriorizaciÃ³n MoSCoW
Para proteger el alcance del MVP frente a la tentaciÃ³n de agregar caracterÃ­sticas superfluas:
- **Must have (Debe tener):** Elementos no negociables sin los cuales el flujo central no funciona.
- **Should have (DeberÃ­a tener):** Importantes pero no vitales para el primer ciclo de prueba.
- **Could have (PodrÃ­a tener):** Deseables si sobra tiempo o capacidad operativa.
- **Won't have (No tendrÃ¡ por ahora):** ExplÃ­citamente descartados para este ciclo para evitar dispersiÃ³n.

### 4. GestiÃ³n con GitHub Projects (Kanban)
- Visibilidad compartida del trabajo mediante un tablero Kanban con flujo transparente: `Backlog` $\rightarrow$ `Por hacer (To Do)` $\rightarrow$ `En curso (In Progress)` $\rightarrow$ `RevisiÃ³n (Review)` $\rightarrow$ `Hecho (Done)`.
- Cada tarea debe trazarse contra un issue o una historia de usuario comprobable.

---

## SesiÃ³n 4: Fundamentos de la Red Stellar y Arquitectura TÃ©cnica

### 1. Arquitectura de Stellar y Ciclo de Transacciones
- Stellar es una red descentralizada de capa 1 optimizada para la emisiÃ³n, custodia y transferencia eficiente de activos y pagos transfronterizos a bajo costo y con liquidaciÃ³n en segundos (3â€“5 segundos por libro mayor / ledger).
- **Consenso federado (Stellar Consensus Protocol - SCP):** A diferencia de *Proof of Work* (PoW) o *Proof of Stake* (PoS), Stellar utiliza acuerdos bizantinos federados basados en quÃ³rums de confianza (Slices), lo que permite alta velocidad, bajo consumo energÃ©tico y finalidad determinista casi inmediata.

### 2. Conceptos nucleares de Stellar
- **Cuentas (Accounts):** Identificadas por una llave pÃºblica (formato `G...`). Requieren una reserva base mÃ­nima de lumens (XLM) para existir en el ledger y mitigar el spam de cuentas vacÃ­as.
- **Activos (Assets):** Representaciones digitales de valor emitidas por cuentas ancla (Anchor accounts), definidas por un cÃ³digo de activo y la llave pÃºblica del emisor.
- **Transacciones y Operaciones:** Una transacciÃ³n agrupa una o mÃ¡s operaciones atÃ³micas (pago, gestiÃ³n de confianza, etc.), cuenta de origen, secuencia de cuenta, tarifa de red (base fee en stroops) y firmas requeridas.
- **Memos:** Campos de metadatos integrados dentro de las transacciones de Stellar que permiten asociar identificadores o hashes externos a una operaciÃ³n.

### 3. Soroban frente a Stellar Classic
- **Stellar Classic:** Operaciones nativas de pagos, transacciones multifirma y lÃ­neas de confianza altamente optimizadas sin necesidad de lÃ³gica programable pesada.
- **Soroban:** Plataforma de contratos inteligentes de nueva generaciÃ³n de Stellar basada en WebAssembly (WASM) y Rust. Permite lÃ³gica de negocio determinista compleja, almacenamiento con vencimiento administrado (State Archival) y pruebas reproducibles en red local y Testnet.
- **Criterio de decisiÃ³n:** No incorporar contratos Soroban a menos que la lÃ³gica de negocio exija validaciones de estado programables complejas que no puedan resolverse de forma mÃ¡s limpia y econÃ³mica mediante transacciones nativas de Stellar.
