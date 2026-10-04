# Matriz de Riesgos y Preguntas Abiertas

Este documento centraliza el análisis prospectivo de riesgos y las incógnitas críticas que deben ser abordadas y resueltas durante las cinco semanas del bootcamp para garantizar la viabilidad del proyecto **Ayuda con Destino**.

---

## 1. Matriz de Riesgos

| Categoría | Descripción del riesgo | Impacto | Probabilidad | Estrategia de mitigación |
| :--- | :--- | :---: | :---: | :--- |
| **Alcance (Scope Creep)** | Intentar abarcar donaciones monetarias, logística de transporte intermunicipal, pagos en criptoactivos o certificación tributaria en el MVP inicial. | `Alto` | `Media` | Mantener como principio inamovible el ADR-001: donaciones en especie únicamente con máquina de cuatro estados. Todo lo demás se relega a *Won't have* en el backlog. |
| **Privacidad y Datos Sensibles** | Filtración o registro accidental de nombres, cédulas, teléfonos o direcciones exactas de damnificados en la red pública de Stellar. | `Crítico` | `Baja` | Aplicar ADR-003: arquitectura de estricta separación *off-chain*. En cadena solo se registran identificadores sintéticos de lote, hashes criptográficos y marcas de tiempo. |
| **Conectividad Intermitente** | Caída o colapso de las redes móviles de telecomunicaciones en zonas afectadas por emergencias, impidiendo la emisión de transacciones en tiempo real. | `Alto` | `Alta` | Diseñar el sistema con enfoque *offline-first*: almacenamiento temporal en dispositivo con cola de sincronización diferida hacia Stellar cuando se recupere la red (ADR-006). |
| **Adopción por Voluntarios** | Resistencia de los voluntarios en centros de acopio a utilizar una interfaz digital si perciben que retrasa la descarga y empaque de víveres bajo lluvia o estrés. | `Alto` | `Alta` | Diseñar flujos ultraligeros que permitan registrar un lote en menos de 30 segundos, reduciendo clics al mínimo y admitiendo lectura rápida de códigos QR preimpresos. |
| **Verificación Física (Oráculos Humanos)** | El "problema del oráculo físico": un registro digital inalterable no garantiza por sí solo que la caja contenía realmente 20 kg de arroz o que no fue alterada físicamente antes de ser entregada. | `Medio` | `Alta` | Asumir explícitamente en el relato que blockchain provee auditoría del proceso y responsabilidad visible por turno, pero no sustituye la inspección física humana. |
| **Sesgos de Distribución / Favoritismo** | Que la herramienta registre asignaciones pero que los coordinadores sigan distribuyendo ayudas de forma discrecional o preferencial a allegados. | `Alto` | `Media` | Transparencia pública del volumen total de lotes recibidos vs. asignados. Las veedurías y comunidades pueden contrastar si un barrio recibió desproporcionadamente más que otro. |

---

## 2. Preguntas Abiertas Críticas

### Preguntas de Producto y Negocio
1. **¿Quién custodia los identificadores preimpresos?** ¿Es más viable que los centros de acopio tengan rollos de calcomanías QR prediseñadas o que la interfaz genere el código en pantalla al momento de la recepción?
2. **¿Cómo interactúa el damnificado que carece de teléfono inteligente?** Si la persona no tiene conectividad ni smartphone para verificar un QR, ¿qué comprobante físico de baja tecnología le garantiza certeza de su asignación?
3. **¿Cuál es el incentivo para que un centro de acopio adopte esta herramienta?** Más allá de la transparencia moral, ¿la herramienta les ahorra tiempo real en la elaboración de balances diarios y rendición de cuentas?

### Preguntas Técnicas y de Arquitectura
4. **¿Stellar Classic vs. Soroban?** ¿Es suficiente utilizar transacciones nativas de Stellar con campos `memo` que almacenen los hashes de transición de estado, o se requiere la lógica programable de un contrato inteligente en Soroban para gobernar las reglas de transición de la máquina de estados?
5. **¿Cómo gestionar la resolución de conflictos en sincronizaciones diferidas?** Si dos dispositivos registran estados discordantes sobre un mismo lote mientras operan sin conexión, ¿qué regla de consenso local prevalece al momento de la reconexión?
6. **¿Quién asume el costo de red (fees) de las transacciones?** En la red Testnet el costo es gratuito; pero en un modelo productivo futuro, ¿debe el centro de acopio fondear una cuenta pagadora (Fee Bump Transactions / Sponsorship) para que los voluntarios no requieran saldo propio en XLM?
