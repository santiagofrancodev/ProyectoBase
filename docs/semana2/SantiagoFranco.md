# Historias de Usuario — Semana 2

> **Estado: Borrador preliminar propuesto por Santiago Franco para revisión y priorización del equipo.**

**Integrante:** Santiago Franco  
**Usuario de GitHub:** [`@santiagofrancodev`](https://github.com/santiagofrancodev)  
**Rol provisional:** Producto, documentación, modelo de datos y UX  

---

## Metodología y Formato

Cada historia sigue el estándar:
$$\text{Como } [\text{rol}], \text{ quiero } [\text{acción / capacidad}], \text{ para } [\text{beneficio o impacto esperado}].$$

Se acompaña de **Criterios de Aceptación** objetivos y una categorización de prioridad mediante el marco **MoSCoW**:
- **Must have:** Crítica para el recorrido mínimo del lote.
- **Should have:** Importante pero no bloquea la prueba inicial.
- **Could have:** Deseable si la capacidad lo permite.
- **Won't have (por ahora):** Descartada del MVP inicial.

---

## Historias de Usuario Propuestas

### US-01: Registro y generación de identificador de lote en recepción
- **Enunciado:** Como **voluntario de recepción en el centro de acopio**, quiero **registrar el ingreso de una donación en especie y generar un identificador único (ID/QR)**, para **iniciar formalmente la trazabilidad del lote y asignarle su estado inicial "Recibido"**.
- **Criterios de aceptación:**
  1. El sistema permite seleccionar la categoría general del bien (Alimentos no perecederos, Higiene/Aseo, Ropa/Abrigo, Insumos médicos básicos).
  2. Se genera un identificador sintético alfanumérico único para el lote (ej. `LOTE-2026-001`).
  3. Se asocia automáticamente la marca de tiempo (timestamp) de recepción y el identificador de la estación de acopio.
  4. No se solicita ningún dato personal ni cédula del donante para completar el registro.
- **Prioridad MoSCoW:** **Must have**

---

### US-02: Registro de custodia formal en bodega
- **Enunciado:** Como **encargado de bodega del centro de acopio**, quiero **escanear el lote recibido y asociarlo a mi turno de guardia cambiando el estado a "Custodiado"**, para **delimitar con claridad la responsabilidad del inventario físico y evitar inconsistencias en los relevos de turno**.
- **Criterios de aceptación:**
  1. El estado del lote solo puede cambiar a "Custodiado" si su estado previo es "Recibido".
  2. Se asocia al lote el identificador o alias del custodio de turno y la marca de tiempo de ingreso al almacén.
  3. El sistema valida que el lote no haya sido registrado simultáneamente en otra ubicación física.
- **Prioridad MoSCoW:** **Must have**

---

### US-03: Asignación de lote a necesidad comunitaria sin datos sensibles
- **Enunciado:** Como **coordinador del centro de acopio**, quiero **cambiar el estado del lote a "Asignado" vinculándolo a un código de solicitud u orden de reparto barrial**, para **evidenciar que el recurso ya tiene un destino programado sin exponer la identidad de la familia damnificada**.
- **Criterios de aceptación:**
  1. El lote pasa a estado "Asignado" únicamente desde el estado previo "Custodiado".
  2. La vinculación se realiza mediante un código sintético de orden o sector (ej. `ORDEN-BARRIO-CENTRO-04`), sin guardar nombres ni direcciones exactas en el registro público.
  3. El cambio de estado registra la marca de tiempo y el identificador del coordinador que autoriza el despacho.
- **Prioridad MoSCoW:** **Must have**

---

### US-04: Atestación de entrega física efectiva
- **Enunciado:** Como **voluntario brigadista de entrega**, quiero **registrar la entrega física del lote en terreno cambiando su estado a "Entregado" mediante una constancia de cierre**, para **dar por completado el ciclo del recurso y generar evidencia inalterable del reparto**.
- **Criterios de aceptación:**
  1. El estado cambia a "Entregado" únicamente desde el estado "Asignado".
  2. Se captura una atestación mínima (código de confirmación alfanumérico entregado al beneficiario o firma digital simple fuera de cadena).
  3. La máquina de estados marca el lote como cerrado (estado final), impidiendo transiciones posteriores.
- **Prioridad MoSCoW:** **Must have**

---

### US-05: Consulta pública y transparente de la historia del lote
- **Enunciado:** Como **donante o ciudadano veedor**, quiero **escanear o ingresar el identificador del lote en un portal de consulta pública**, para **comprobar en qué estado se encuentra (`Recibido`, `Custodiado`, `Asignado`, `Entregado`) y verificar sus marcas de tiempo y constancias sin depender de un intermediario**.
- **Criterios de aceptación:**
  1. La consulta devuelve la cronología completa de transiciones de estado del lote consultado.
  2. Se visualizan las marcas de tiempo y el identificador de cada fase.
  3. No se revela bajo ninguna circunstancia el nombre, documento o ubicación exacta de la familia beneficiaria.
  4. La consulta se ejecuta de forma libre, sin requerir registro ni inicio de sesión para el observador.
- **Prioridad MoSCoW:** **Should have**

---

### US-06: Captura local de movimientos ante desconexión de red
- **Enunciado:** Como **voluntario operativo en campo**, quiero **registrar cambios de estado de lotes en mi dispositivo aún sin cobertura de red**, para **evitar que la caída de antenas interrumpa la entrega física y asegurar que los datos se sincronicen cuando vuelva la conectividad**.
- **Criterios de aceptación:**
  1. La interfaz permite registrar las transiciones en almacenamiento local cuando el dispositivo detecta modo *offline*.
  2. Cada movimiento encolado retiene la marca de tiempo local de ocurrencia física.
  3. Al recuperar la red, el sistema ofrece una acción explícita para sincronizar en lote las transiciones pendientes.
  4. En caso de discrepancia o conflicto, el sistema alerta visualmente para revisión del administrador.
- **Prioridad MoSCoW:** **Should have**
