# Problem Brief

> **Borrador preliminar — pendiente de confirmar tras el commit individual de Gustavo Arcila. No afirmar consenso todavía.**

## Decisión del problema

### Problema elegido

Donantes, centros de acopio y comunidades no pueden verificar de forma independiente qué recursos en especie fueron recibidos, asignados y entregados. Propuesta base provisional de Santiago Franco, pendiente de confirmar con Gustavo Arcila.

### Por qué elegimos este

De forma provisional se toma la propuesta de Santiago Franco como base porque describe un flujo observable en centros de acopio, delimita el MVP a donaciones en especie y plantea una hipótesis de registro compartido compatible con el criterio de la Sesión 1. Esta elección es preliminar y queda pendiente de confirmar tras el commit individual de Gustavo Arcila. No se afirma consenso todavía.

### Propuestas descartadas

Ninguna propuesta se descarta en este borrador. Como contexto, sin copiar su contenido, se deja constancia de que la propuesta de Gustavo Arcila aborda centros de acopio comunitarios en Pereira, con flujo donante → administrador o voluntario → persona damnificada, y evidencia desde observación directa de distribución de mercados. Dicha propuesta será registrada por su autor y luego se contrastará con la base provisional para decidir.

### Cómo tomamos la decisión

Aún no hay decisión final. El procedimiento previsto es: publicar ambas propuestas individuales, comparar problema, actores y flujo, y luego registrar el acuerdo o la votación en este documento. Hasta que se complete el commit individual de Gustavo Arcila, todo lo que sigue es un borrador preliminar no final.

---

## Problem Brief

### Encabezado

Ayuda con Destino: donantes, centros de acopio y comunidades no pueden verificar de forma independiente qué recursos en especie fueron recibidos, asignados y entregados.

### Equipo y roles

- Santiago Franco — usuario de GitHub: santiagofrancodev — responsable de propuesta individual y de este borrador preliminar.
- Gustavo Adolfo Arcila — integrante del equipo — responsable de su propuesta individual, que será registrada mediante commit realizado por él.
- Responsable de entregas y coordinación: por definir tras el commit individual de Gustavo Arcila.
- Canal de coordinación interna: por definir en el acuerdo posterior al borrador.

### Problema y evidencia

El problema es que donantes, centros de acopio y comunidades afectadas no pueden verificar de forma independiente qué recursos en especie fueron recibidos, asignados y entregados durante la atención de una emergencia. El contexto de referencia es el terremoto del 10 de agosto de 2026, vivido desde Armenia con residencia y trabajo en Pereira, donde la urgencia multiplica las donaciones en especie y al mismo tiempo dispersa la información entre cuadernos, mensajes y memoria de los voluntarios. La frecuencia del problema aparece cada vez que un centro de acopio concentra aportes de múltiples donantes y debe repartirlos entre varias familias en pocos días, con turnos rotativos y presión por entregar rápido. El alcance de este borrador se limita a trazabilidad de donaciones en especie dentro de un centro de acopio, con estados recibido, custodiado, asignado y entregado, sin incluir dinero, vales, trueque, comercio, logística internacional ni tratamientos tributarios. La evidencia mínima es la experiencia propia del autor de la base provisional y la observación directa del registro manual en centros de acopio, donde resulta difícil reconstruir después qué lote llegó, quién lo custodió, a quién se asignó y si efectivamente se entregó. No se presentan cifras, entrevistas ni alianzas porque no se cuenta con fuentes verificables en esta etapa. La consecuencia es desconfianza entre partes que en principio colaboran, pues ante demoras o pérdidas no existe un historial compartido que permita comprobar los movimientos sin depender de una sola persona o cuaderno.

### Usuario y actores

Quienes sufren el problema son, en primer lugar, los donantes de bienes en especie, que entregan alimentos, ropa o insumos y necesitan saber si su aporte fue recibido, custodiado, asignado y entregado, pero hoy solo pueden preguntar por mensajes o visitas y rara vez obtienen una respuesta trazable. En segundo lugar, las comunidades afectadas, que esperan ayudas y necesitan información clara sobre qué recursos llegaron al centro, qué les fue asignado y qué fue entregado, sin tener que confiar únicamente en la palabra del turno de turno. En tercer lugar, los equipos de los centros de acopio, entre ellos quien recibe, quien custodia en bodega, quien asigna y quien entrega, que necesitan registrar rápido con pocos recursos y responder reclamos sin un historial común. Hoy lo resuelven con anotaciones manuales, listas en papel, fotos sueltas y chats, lo que les cuesta tiempo duplicado en registrar y buscar, esfuerzo de coordinación entre turnos que heredan información incompleta, y costo de confianza cuando no pueden demostrar un movimiento. Intervienen además voluntarios de apoyo y líderes comunitarios que median entre el centro y las familias, sin un papel formal de auditoría. Todos comparten la necesidad de un registro simple, consultable y común sobre cada lote en especie.

### Flujo actual de valor

El flujo actual describe cómo se mueve hoy un bien en especie, junto con su información, desde el origen hasta el destino, sin que ningún paso responda a una obligación normativa identificada en este borrador. La secuencia observada es la siguiente. Primero, el donante entrega alimentos, ropa o insumos en el centro de acopio y alguien anota de forma manual qué se recibió, con fecha aproximada y sin identificador único del lote. Segundo, el equipo del centro clasifica lo recibido y lo ubica en bodega bajo custodia, registrando en cuaderno o memoria quién queda a cargo, sin un estado formal de custodiado que otros puedan consultar. Tercero, quien coordina decide la asignación según criterios variables como orden de llegada, urgencia percibida o solicitudes de líderes comunitarios, y comunica la decisión de palabra o por chat, sin un registro de asignación verificable. Cuarto, se prepara el lote y se entrega a la familia o persona destinataria, con una firma en papel o un mensaje como única constancia. Quinto, cuando alguien pregunta después qué pasó con un aporte, un voluntario busca en cuadernos y chats e intenta reconstruir la historia. Este recorrido muestra que el bien se mueve razonablemente, pero la información no lo acompaña con la misma fidelidad, por lo que la verificación independiente resulta imposible y cada consulta consume tiempo operativo del centro.

### Fricciones identificadas

Las fricciones se ubican en pasos concretos del flujo y muestran dónde falla, se encarece o se demora la trazabilidad. En el paso de recepción, la fricción es la ausencia de identificador único por lote, cuya causa es el registro manual apurado en momentos de alto volumen, y afecta al donante y al centro porque después no se puede distinguir un aporte de otro. En el paso de custodia, la fricción es que no queda claro quién responde por cada lote en bodega, cuya causa es el cambio de turnos sin entrega formal del inventario, y afecta al equipo del centro porque nadie puede demostrar qué tenía a cargo. En el paso de asignación, la fricción es la opacidad de los criterios de reparto, cuya causa es que la decisión se comunica de palabra o por chat sin registro consultable, y afecta a las comunidades que perciben trato desigual sin poder verificarlo. En el paso de entrega, la fricción es la constancia débil, cuya causa es depender de firmas en papel o mensajes dispersos que se pierden, y afecta a donantes y familias porque no hay prueba compartida de la entrega. En el paso de consulta posterior, la fricción es la reconstrucción costosa del historial, cuya causa es la información fragmentada entre cuadernos y personas, y afecta a todos porque cada verificación exige tiempo presencial y depende de la memoria disponible.

### Oportunidad e hipótesis

La oportunidad priorizada es la trazabilidad consultable del lote en especie a lo largo de los estados recibido, custodiado, asignado y entregado, porque concentra las fricciones de identificación, custodia, asignación y entrega en un solo punto de mejora y porque responde directamente a la necesidad de verificación independiente de donantes, centros y comunidades. Se elige esta oportunidad frente a otras posibles, como optimizar rutas o predecir demanda, porque sin un historial compartido cualquier otra mejora seguiría apoyada en registros fragmentados y no resolvería la desconfianza. La hipótesis inicial es que si cada lote cuenta con un identificador o código QR, responsable visible, marca de tiempo, estado actual y una evidencia mínima del movimiento, entonces un donante podrá comprobar qué pasó con su aporte, una familia podrá verificar qué le fue asignado y entregado, y el centro podrá responder consultas sin reconstruir cuadernos. Los datos personales y las ubicaciones exactas quedarían fuera del registro compartido para proteger la privacidad. Para contextos con conectividad intermitente se contempla captura local con sincronización posterior, sin prometer confirmación inmediata en un registro distribuido cuando no hay conexión. Esta hipótesis se validará con pruebas guiadas y datos sintéticos.

### Criterio de pertinencia

El caso requiere evaluar un registro distribuido en lugar de una base de datos tradicional o una integración entre sistemas existentes, apoyándose en el criterio de la Sesión 1 según el cual varias partes que no confían plenamente entre sí necesitan compartir un mismo registro cuyo historial no pueda alterarse. En este borrador, donantes, equipos de centros de acopio, voluntarios y comunidades afectadas colaboran alrededor de los mismos bienes, pero ninguna parte quiere depender por completo de la versión que guarda otra, y los registros manuales actuales permiten pérdidas, ediciones o versiones contradictorias sin dejar rastro. Una base de datos administrada por una sola parte mantendría el problema de fondo, porque obligaría a todos a confiar en ese administrador para la lectura y la escritura del historial, justo cuando la rotación de turnos y la presión de la emergencia debilitan esa confianza. La hipótesis es que un historial compartido e inalterable de movimientos por lote, con identificador, responsable, marca de tiempo y estado, permitiría que cada parte verifique sin pedir permiso ni intermediarios adicionales. No se afirma que blockchain sea la única opción ni que ya esté validada, solo que el patrón de desconfianza parcial y necesidad de auditoría común justifica explorar un registro compartido frente a una solución centralizada.

### Supuestos y riesgos

El primer supuesto es que los centros de acopio pueden sostener el registro de cada lote con un esfuerzo mínimo, es decir, escanear o anotar un identificador, cambiar el estado y guardar una evidencia simple en el momento del movimiento. Si en la práctica el volumen o la rotación impiden ese registro, la hipótesis se invalida porque el historial quedaría incompleto y la verificación perdería valor. El segundo supuesto es que donantes y comunidades valoran y usan la verificación independiente, consultando el estado de un lote cuando lo necesitan y aceptando identificadores sin datos personales. Si prefieren seguir preguntando por chat o presencialmente, o si desconfían de la herramienta, la mejora no se adoptaría aunque técnicamente funcione. El tercer supuesto es que existe conectividad suficiente para sincronizar con una frecuencia útil, complementada con captura local ordenada cuando la conexión falla, sin prometer registros definitivos sin conexión. Si los cortes son prolongados o los dispositivos son escasos, la sincronización tardía generaría dudas sobre la actualidad del historial. Los riesgos asociados son sobrecarga operativa en picos de entrega, errores de captura que contaminen el registro, y expectativas excesivas sobre inmutabilidad sin comprender sus límites, por lo que el MVP deberá probar usabilidad, privacidad y contingencia con datos sintéticos.
