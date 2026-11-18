# Análisis de impacto de SC-001

> Análisis de impacto · Ingeniería de Software I · SIS3407
> Repositorio: `docs/cambios/ai-001-proponer-nueva-fecha-de-entrega.md`
> Lo escribe el dueño del sistema (Ian Adolfo López Maldonado), sobre la solicitud que le entregó su dupla.

---

## Solicitud que se analiza

`sc-001-proponer-nueva-fecha-de-entrega.md`, pedida por Jorge Eduardo García Hernández (dupla de revisión) el 15/11/2026.

## Traducción a términos del sistema

**Lo pedido:** "Quiero poder proponerle al cliente, desde ArtConnect, una nueva fecha de entrega cuando no me alcance el tiempo, explicar el motivo, y que el cliente la acepte o la rechace."

**Traducido:** una `Modificacion` de una comisión activa que tiene su origen en el Artista (hoy solo la origina el Cliente) y que afecta únicamente la fecha de entrega (`afectaFechaEntrega` verdadero).

Se atiende con el mecanismo que ya existe en CU-06, sin crear uno paralelo:
- El Artista propone nuevas `CondicionesTrabajo` con una fecha distinta, por la variante `ProponerNuevasCondiciones` de la estrategia de modificación.
- El Cliente decide con `registrarDecision`. Si acepta, la nueva versión de `CondicionesTrabajo` pasa a ser la vigente y la anterior se conserva. Si rechaza, la versión vigente no cambia.

Lo realmente nuevo es solo esto: (1) que una modificación pueda iniciarla el Artista y no solo el Cliente, y (2) que la modificación registre quién la originó y el motivo. Todo ocurre dentro del módulo Comisiones y Seguimiento.

## Impacto directo

| Artefacto | Unidad | Qué hay que cambiar |
|---|---|---|
| Requisito RF-008 | 2 | Hoy describe "una solicitud de modificación del cliente". Debe permitir que también el artista inicie una modificación cuando se trata de la fecha de entrega, indicando el motivo. |
| Requisito RF-009 | 2 | Su criterio parte de "al responder una solicitud de modificación". Debe cubrir también el caso en que el artista propone las condiciones por iniciativa propia, sin solicitud previa del cliente. |
| Caso de uso CU-06 | 2 | Hoy su actor principal es el Cliente y su objetivo habla de una modificación "solicitada por el cliente". Agregar el flujo alterno D, "El Artista propone una nueva fecha de entrega", que reutiliza los pasos 8 a 11 del escenario principal y el flujo C (comisión no activa). Ajustar objetivo y precondición. |
| Diagrama de clases | 4 | `Modificacion` debe registrar quién la originó y el motivo. Esto implica una relación nueva entre `Usuario` y `Modificacion` (con su multiplicidad) y ajustar `registrarSolicitud` para recibir ese origen y motivo. |
| Diagrama de secuencia | 4 | El único diagrama de secuencia, el de CU-01, no cambia. Si se implementa el cambio se recomienda dibujar uno nuevo para el flujo D, pero no es obligatorio para aceptar la solicitud. |
| Prototipo | 2 | Detalle de comisión, vista del artista: nueva opción para proponer una fecha con su motivo. Revisión de modificación, vista del cliente: debe mostrar fecha vigente, fecha propuesta y motivo, además de los botones Aceptar y Rechazar que ya existen. |
| Trazabilidad (sección 6 de la especificación) | 2 | Actualizar las filas de RF-008 y RF-009 con el nuevo flujo y los elementos del prototipo, subir la versión de la especificación y agregar la línea correspondiente al registro de cambios. |

## Impacto indirecto

| Artefacto | Unidad | Por qué se ve afectado |
|---|---|---|
| Requisito RF-010 (historial) | 2 | Su criterio lista "modificaciones y acuerdos" sin decir quién los originó. Debe mostrar el origen y el motivo para que el historial refleje el cambio de fecha (criterios 5 de la solicitud). |
| Requisito RF-011 | 2 | Sin impacto: ya registra aceptación o rechazo del cliente sobre condiciones propuestas. Revisado. |
| RNF-CON-001 | 2 | Se aplica sin cambiarlo: al aceptarse la nueva fecha, la anterior debe conservarse (regla de negocio 3). Hay que verificarlo al probar. |
| RNF-SEG-001 | 2 | Se aplica sin cambiarlo: solo el artista y el cliente de la comisión pueden ver y responder la propuesta (criterio 7 de la solicitud). |
| Diagrama de casos de uso | 2 | Sin impacto: el Artista ya está asociado a CU-06, y los «extend» "Proponer condiciones" y "Registrar decisión" se reutilizan tal cual. |
| Patrón Strategy | 4 | Se absorbe sin clases nuevas: una nueva fecha siempre afecta las condiciones, así que usa la variante `ProponerNuevasCondiciones`. |
| Demás clases (Solicitud, Cotizacion, Comision, Avance, Mensaje) | 4 | Sin impacto. |
| Máquina de estados de `Cotizacion` | 4 | Sin impacto: la cotización ya está Aceptada cuando existe la comisión, y el diagrama no cubre la modificación. |
| Diagrama de objetos | 4 | Sin impacto: representa un caso sin reprogramación. |
| Diagrama de paquetes | 4 | Sin impacto: no hay módulos ni dependencias nuevas. |
| Registro de decisión ADR-001 | 3 | Sin impacto: la decisión de monolito modular se sostiene porque el cambio cabe dentro de un solo módulo, sin tocar fronteras ni dependencias. Revisado. |
| Diagrama de contexto C4 | 3 | Sin impacto: no hay actores ni sistemas externos nuevos. |
| Diagrama de contenedores C4 | 3 | Sin impacto: mismas piezas y mismas flechas. |
| Diagrama de componentes C4 | 3 | Sin impacto en módulos ni flechas. Solo cambia el contenido interno de Comisiones y Seguimiento. |
| Módulo Comunicación | 3 | Sin impacto: no hay avisos automáticos (el patrón Observer se descartó en la Actividad 2), así que el cliente ve la propuesta al consultar la comisión. Ver riesgo 1. |

## Lo que queda sin tocar

- El flujo de solicitud y cotización (CU-01 a CU-03), sus clases y la máquina de estados de `Cotizacion`.
- Los cuatro módulos, sus dependencias y el ADR-001.
- Seguimiento, avances y mensajes (CU-04, CU-05 y CU-07), salvo cómo se muestra el historial.
- La base de datos y el almacenamiento externo.
- Los pagos, que siguen fuera del alcance: cambiar la fecha no implica ningún cobro.
- Las reglas de negocio 1, 2 y 3, que se cumplen tal cual: la nueva fecha se aprueba entre ambas partes y las condiciones anteriores se conservan.

## Riesgos

| # | Riesgo | Probabilidad | Cómo se atiende |
|---|---|---|---|
| 1 | El cliente no se entera a tiempo de la propuesta, porque no hay avisos automáticos. | Media | La propuesta queda destacada al consultar la comisión y en el historial. Los avisos quedan fuera de esta solicitud. |
| 2 | Dos modificaciones pendientes a la vez sobre la misma comisión (una del cliente y una del artista) y versiones de condiciones que se pisan. | Baja | Definir en CU-06 que solo puede haber una propuesta pendiente por comisión. |
| 3 | El cliente rechaza la fecha y el artista de todos modos no puede cumplir. | Media | Es el flujo B: la fecha original sigue vigente y el conflicto se resuelve fuera del sistema, como hoy. Se documenta como postcondición. |
| 4 | Uso repetido para posponer una entrega una y otra vez. | Baja | El cliente decide cada vez y el historial deja constancia de cuántas veces ocurrió. |
| 5 | **No hacerlo:** el cambio de fecha por retraso sigue acordándose por chat y el registro de ArtConnect deja de ser confiable justo en los casos con posible desacuerdo. | Media | Es el riesgo que motiva la solicitud. |

## Alternativas consideradas

1. **Opción A, tratarlo como una modificación iniciada por el artista (me inclino por esta).** Reutiliza CU-06, la estrategia `ProponerNuevasCondiciones` y el versionado de `CondicionesTrabajo`. Cuesta: editar dos requisitos y el historial, agregar un flujo alterno, dos datos nuevos en `Modificacion` y ajustar dos pantallas, sin tocar la arquitectura. Deja pendiente: los avisos al cliente.
2. **Opción B, un caso de uso nuevo e independiente, "Reprogramar entrega".** Con su propio requisito (RF-014), su propia clase de reprogramación y su propia máquina de estados. Permite reglas propias, como límite de reprogramaciones, pero duplica la lógica de aprobación entre ambas partes que ya existe y obliga a mantener dos mecanismos. Cuesta aproximadamente el doble. Deja pendiente: unificar ambos mecanismos.
3. **Descartada: solo permitir que el artista avise por mensaje.** No cambia la fecha vigente ni deja un acuerdo registrado, así que no resuelve el problema.

## Estimación de esfuerzo

| Concepto | Esfuerzo |
|---|---|
| Cambios de diseño y documentación | 3.5 h |
| Implementación | 16 h |
| Pruebas | 6 h |
| **Total** | **25.5 h** |

**De dónde sale este número.**
- **Diseño y documentación (3.5 h):** editar RF-008, RF-009 y RF-010 (1 h), agregar el flujo D y ajustar CU-06 (0,5 h), actualizar el diagrama de clases (0,5 h) y las dos pantallas del prototipo más la trazabilidad (1.5 h).
- **Implementación (16 h):** supuse que construir todo CU-06 costaría unas 24 h para una sola persona. Este cambio reutiliza la propuesta de condiciones, la decisión del cliente y el versionado de condiciones, así que solo agrega el inicio desde el artista, dos datos nuevos y el ajuste de pantallas, aproximadamente un tercio de ese trabajo.
- **Pruebas (6 h):** cerca de media hora por cada uno de los 7 criterios de aceptación de la solicitud, más una hora de regresión sobre CU-06.
- **Supuestos:** una sola persona, horas efectivas de trabajo. Como el sistema todavía no está implementado, no tengo datos históricos y la estimación es por analogía, no medida.
- **No incluye:** avisos automáticos, despliegue ni la revisión de la dupla.
- **Margen:** el rango de 20 a 30 horas refleja que la fricción en la integración, las pruebas y la corrección manual de detalles para un perfil junior amplía el esfuerzo más allá de la simple generación de código.

## Recomendación

**Aceptar, con la opción A.** Aporta lo que la solicitud pide con un cambio razonable: encaja en el diseño actual, no toca la arquitectura ni los otros módulos y reutiliza el patrón que ya definimos. Tiene riesgos bajos.

Condiciones: definir que solo puede haber una propuesta pendiente por comisión (riesgo 2) y documentar qué pasa si el cliente rechaza la fecha (riesgo 3). Los avisos automáticos quedan fuera de esta solicitud.

Siguiendo el ciclo Ágil elegido, la documentación (3.5 h) se incorpora al diseño ahora y la implementación entra en la siguiente iteración.

---

*El objetivo de este documento no es dar un número exacto. Es que cualquiera pueda seguir tu razonamiento y señalarte dónde te equivocaste.*
