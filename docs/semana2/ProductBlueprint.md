# Product Blueprint — Entregable 2

> [!WARNING]  
> **ESTADO DEL DOCUMENTO: Borrador estructural — Pendiente de historias individuales y consenso.**  
> Este artefacto consolida la arquitectura de producto preliminar para el MVP de **Ayuda con Destino**. Se actualizará y completará una vez que Gustavo Arcila y Santiago Franco integren sus historias de usuario individuales y acuerden formalmente la priorización del backlog.

---

## 1. Lean Canvas Preliminar

| Bloque | Definición preliminar para Ayuda con Destino |
| :--- | :--- |
| **Problema** | Registros manuales e informales en centros de acopio provocan fragmentación de datos, desconfianza comunitaria, sospechas de favoritismo y sobrecarga en la rendición de cuentas tras desastres. |
| **Segmento de Clientes / Usuarios** | 1. Damnificados y familias afectadas (usuario final prioritario).<br>2. Donantes particulares e institucionales.<br>3. Administradores y voluntarios de centros de acopio.<br>4. Veedurías y líderes comunitarios locales. |
| **Propuesta Única de Valor (UVP)** | *"Trazabilidad auditable e inalterable del recorrido de donaciones en especie, permitiendo verificación independiente sin depender de la discrecionalidad de intermediarios."* |
| **Solución** | Registro inalterable basado en lotes físicos etiquetados con QR, gobernados por una máquina de estados determinista de cuatro etapas (`Recibido → Custodiado → Asignado → Entregado`), con soporte de captura offline y separación de datos sensibles. |
| **Canales** | Interfaz web ligera para consulta ciudadana; interfaz web responsiva de uso rápido para estaciones de acopio y brigadistas. |
| **Fuentes de Sostenibilidad** | Proyecto sin fines de lucro en etapa formativa. Hipótesis futura: adopción por comités de socorro cívico, municipios u ONG humanitarias como bien público digital. |
| **Estructura de Costos** | Tarifas mínimas de red en Stellar (fracciones de centavo de dólar por transacción), almacenamiento ligero off-chain e impresión básica de etiquetas QR. |
| **Métricas Clave (KPIs)** | - Tiempo promedio de registro de lote en recepción (< 30 s).<br>- Porcentaje de lotes con trazabilidad completa de cuatro estados.<br>- Número de consultas ciudadanas exitosas sin asistencia de intermediarios.<br>- Tasa de sincronización diferida exitosa tras desconexión. |
| **Ventaja Injusta** | Flujo acotado basado en la vivencia directa de campo en el Eje Cafetero, priorizando usabilidad de bajo estrés y privacidad absoluta antes que complejidad financiera. |

---

## 2. Alcance Definido del MVP

### Lo que SÍ hace el MVP
- Identifica cada donación en especie mediante un identificador sintético único de lote (código alfanumérico / QR).
- Administra el ciclo de vida del lote a través de 4 estados sucesivos e irrevocables:
  $$\text{Recibido} \longrightarrow \text{Custodiado} \longrightarrow \text{Asignado} \longrightarrow \text{Entregado}$$
- Asocia a cada transición: marca de tiempo (timestamp), alias del operador/rol y hash de la constancia.
- Ofrece una vista de consulta pública que permite a cualquier ciudadano o donante auditar el recorrido del lote ingresando el ID.
- Mantiene todos los datos de identidad y ubicación sensible fuera de la cadena (*off-chain*).
- Simula y valida el flujo completo utilizando datos sintéticos generados en pruebas controladas.

### Lo que NO hace el MVP (Fronteras y exclusiones)
- No procesa dinero en efectivo, transferencias bancarias, monedas estables ni criptomonedas.
- No ofrece esquemas de fidelización, puntos, recompensas ni beneficios fiscales/tributarios.
- No incluye trazabilidad de fletes internacionales ni aduanas.
- No utiliza hardware IoT ni automatizaciones físicas que sustituyan la verificación humana.
- No requiere hardware especializado (funciona sobre navegadores móviles estándar).

---

## 3. Matriz de Actores y Puntos de Contacto

```text
  [ Donante ]             [ Voluntario Acopio ]       [ Familia Damnificada ]
       │                            │                            │
  (Entrega bien)             (Genera Lote ID)                    │
       ▼                            ▼                            │
  [ Estado: RECIBIDO ]  ──────> [ QR Físico ]                    │
                                    │                            │
                             (Ingreso Bodega)                    │
                                    ▼                            │
                         [ Estado: CUSTODIADO ]                  │
                                    │                            │
                             (Orden Reparto)                     │
                                    ▼                            │
                          [ Estado: ASIGNADO ]                   │
                                    │                            │
                             (Entrega Física) ─────────────────> │
                                    ▼                      (Recibe ayuda)
                          [ Estado: ENTREGADO ]
                                    ▲
                                    │
                         [ Veeduría Comunitaria ]
                            (Audita historial)
```

---

## 4. Arquitectura de Datos: Estrategia On-chain vs. Off-chain

| Atributo | Ubicación | Justificación técnica y de privacidad |
| :--- | :--- | :--- |
| **ID de Lote** (ej. `LOTE-2026-001`) | On-chain | Clave pública de indexación y búsqueda inalterable. |
| **Estado actual** (`0..3`) | On-chain | Control determinista de la máquina de estados. |
| **Timestamp de transición** | On-chain | Garantía de orden temporal y no repudio del movimiento. |
| **Categoría genérica** (ej. `Alimentos`) | On-chain | Metadata no sensible para agregación estadística pública. |
| **Hash de constancia** (SHA-256) | On-chain | Anclaje criptográfico de integridad de la evidencia documental. |
| **Alias del operador / Llave pública** | On-chain | Responsabilidad del turno que ejecuta la transición. |
| **Nombres y cédulas de beneficiarios** | **ESTRICTAMENTE OFF-CHAIN** | Protección absoluta de la intimidad y seguridad física de familias damnificadas. |
| **Direcciones domiciliarias exactas** | **ESTRICTAMENTE OFF-CHAIN** | Evitar riesgos de focalización indebida o estigmatización barrial. |
| **Notas o actas físicas de entrega** | **OFF-CHAIN (Local / Privado)** | El documento permanece en el centro; solo su hash viaja a la red. |

---

## 5. Backlog Consolidado Preliminar (Pendiente de Consenso)

*Este backlog se armonizará formalmente una vez incorporadas las historias individuales de Gustavo Arcila:*

- **US-01 [Must]:** Registro inicial del lote y asignación de identificador único / QR (`Recibido`).
- **US-02 [Must]:** Relevo y aceptación de custodia en bodega por turno de guardia (`Custodiado`).
- **US-03 [Must]:** Asignación de lote a orden de entrega comunitaria anonimizada (`Asignado`).
- **US-04 [Must]:** Registro de entrega física y cierre definitivo del ciclo del lote (`Entregado`).
- **US-05 [Should]:** Portal web responsivo de consulta pública de trazabilidad por ID/QR.
- **US-06 [Should]:** Módulo de contingencia para captura local y sincronización diferida (*offline-first*).

---

## 6. Plan de Validación con Usuarios y Datos Sintéticos

1. **Simulación de Centro de Acopio (Semana 4):**
   - Ejecución de un ejercicio de rol simulado con datos sintéticos (10 a 20 lotes de víveres ficticios).
   - Medición de fricción y tiempos de captura entre voluntarios no técnicos.
2. **Prueba de Consulta Ciudadana:**
   - Presentación de la vista pública a observadores externos para evaluar si la información presentada genera comprensión y certidumbre sin violar la privacidad.
3. **Prueba de Resiliencia ante Desconexión:**
   - Registro de transiciones en condiciones de corte deliberado de conectividad local y posterior sincronización.
