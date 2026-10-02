# Especificación de requisitos

**Plantilla del curso · Ingeniería de Software I · SIS3407**

**Sistema:** ArtConnect  
**Autor:** Ian A. López Maldonado  
**Versión:** 1.4  
**Fecha de la última actualización:** 30 de septiembre de 2026

---

## 1. Propósito y alcance

**Propósito del documento:**
Definir los requisitos funcionales y no funcionales de ArtConnect a partir de la Visión del producto y de los resultados obtenidos durante la entrevista de elicitación. Estos requisitos servirán como base para el diseño de los casos de uso, el prototipo y la posterior validación del sistema.

**Alcance del sistema:**
ArtConnect es un sistema web orientado a la gestión de trabajos artísticos personalizados por encargo entre clientes y artistas.

**El sistema contempla:**
- El registro de solicitudes de trabajos artísticos.
- La elaboración de cotizaciones asociadas a una solicitud.
- La aceptación, rechazo o solicitud de ajustes sobre una cotización.
- El seguimiento del estado y avance de una comisión.
- La solicitud y resolución de modificaciones durante la realización del trabajo.
- La consulta de los acuerdos, modificaciones y avances registrados durante una comisión.
- La comunicación entre cliente y artista mediante mensajes asociados a una comisión.

**Fuera del alcance:**
- El sistema no procesa pagos, anticipos ni transferencias entre clientes y artistas.

- El sistema no crea, modifica ni edita las obras artísticas.
- El sistema no garantiza el cumplimiento de obligaciones económicas o acuerdos realizados fuera de la plataforma.

---

## 2. Usuarios y su contexto

| **Usuario** | **Qué hace hoy sin el sistema** | **Qué espera del sistema** |
| :--- | :--- | :--- |
| **Cliente** | Contacta al artista mediante redes sociales o aplicaciones de mensajería, explica el trabajo que necesita y revisa conversaciones anteriores para recordar precios, condiciones, avances o cambios acordados. Para conocer el progreso depende de que el artista le envíe información o responda sus mensajes. | Registrar claramente lo que solicita, consultar las condiciones del encargo, conocer su progreso y solicitar modificaciones sin perder los acuerdos realizados durante el proceso y comunicarse con el artista dentro del sistema. |
| **Artista** | Recibe solicitudes mediante redes sociales, revisa referencias, calcula precios y organiza sus encargos mediante conversaciones, notas y archivos. Cuando tiene varios trabajos puede necesitar revisar mensajes anteriores para recordar cambios, precios o fechas. | Organizar las solicitudes y comisiones en un mismo lugar, establecer las condiciones de cada trabajo, registrar avances y mantener la comunicación relacionada con cada encargo dentro del mismo sistema. |

**Conflictos identificados entre usuarios:**
El cliente puede querer realizar modificaciones durante el desarrollo de la obra para obtener el resultado esperado, mientras que el artista necesita evitar que los cambios excedan el trabajo originalmente acordado.

La entrevista mostró que la etapa de la comisión es importante para resolver este conflicto. Un cambio durante el boceto puede ser sencillo, mientras que un cambio solicitado cuando el trabajo está avanzado puede afectar el precio, la fecha de entrega o incluso quedar fuera de las condiciones originales.

Este conflicto se resuelve estableciendo que, cuando una modificación afecte el precio, alcance o fecha de entrega, el artista propone las nuevas condiciones y el cliente debe aceptarlas antes de que el cambio se incorpore a la comisión.

---

## 3. Requisitos funcionales

### 3.1 Resumen

| **ID** | **Nombre del Requisito (Infinitivo)** | **Prioridad**  | **Origen** |
| :--- | :--- | :--- | :--- |
| **RF-001** | Registrar solicitud de comisión | Imprescindible | Visión del producto + Entrevista (P10: información necesaria para solicitar un trabajo) |
| **RF-002** | Registrar cotización | Imprescindible | Visión del producto + Entrevista (P11: acuerdo de precio y condiciones) |
| **RF-003** | Solicitar ajuste de cotización | Importante | Entrevista (P12: negociación antes de aceptar o rechazar) |
| **RF-004** | Registrar decisión sobre cotización | Imprescindible | Visión del producto + Entrevista (P12: respuesta del cliente ante una cotización) |
| **RF-005** | Actualizar estado de comisión | Imprescindible | Derivado del seguimiento de la Visión + Entrevista (P14: identificación de la etapa del encargo) |
| **RF-006** | Registrar avance de comisión | Imprescindible | Visión del producto + Entrevista (P1 y P14: envío de avances al cliente) |
| **RF-007** | Consultar progreso de comisión | Imprescindible | Visión del producto + Entrevista (P14: consulta actual del progreso) |
| **RF-008** | Solicitar modificación | Imprescindible | Visión del producto + Entrevista (P4, P8 y P13: cambios durante el trabajo) |
| **RF-009** | Proponer condiciones de modificación | Imprescindible | Regla de negocio de la Visión + Entrevista (P4, P8 y P13: impacto de los cambios) |
| **RF-010** | Consultar historial de comisión | Importante | Problema definido en la Visión + Entrevista (P5: revisión de acuerdos anteriores) |
| **RF-011** | Registrar decisión sobre modificación | Imprescindible | Regla de negocio de la Visión + Entrevista (P13: cambios que afectan las condiciones) |
| **RF-012** | Enviar mensaje en una comisión | Importante | Derivado del problema de la Visión + reforzado por Entrevista (P5 y P7: información dispersa en mensajes) |
| **RF-013** | Consultar conversación de una comisión | Importante | Derivado del problema de la Visión + reforzado por Entrevista (P5: búsqueda de acuerdos en conversaciones) |

### 3.2 Fichas

**RF-001 - Registrar solicitud de comisión**

| **Campo** | **Contenido** |
| :--- | :--- |
| **Descripción** | El sistema registra una solicitud de comisión con la descripción del trabajo, estilo solicitado, cantidad de elementos, nivel de detalle y referencias proporcionadas por el cliente. |
| **Origen** | Visión del producto y entrevista (Pregunta 10). La Visión ya contemplaba la creación de solicitudes y la entrevista confirmó que el artista necesita conocer características como estilo, cantidad de elementos, nivel de detalle, referencias y, cuando existe, una fecha límite antes de evaluar el trabajo. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al enviar una solicitud con la descripción del trabajo, estilo, cantidad de elementos, nivel de detalle y referencias, el sistema la registra asociada al cliente y la muestra al artista correspondiente. Si falta alguno de los datos obligatorios, el sistema no registra la solicitud e indica cuál falta. |
| **Relacionado con** | RF-002 |

**RF-002 - Registrar cotización**

| **Campo** | **Contenido** |
| :--- | :--- |
| **Descripción** | El sistema registra una cotización del artista asociada a una solicitud de comisión. |
| **Origen** | Visión del producto y entrevista (Pregunta 11). La Visión contemplaba el envío de cotizaciones y la entrevista confirmó que el artista establece el precio y las condiciones antes de comenzar el trabajo. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al registrar una cotización con precio, condiciones y fecha estimada de entrega, el sistema la asocia a la solicitud correspondiente y la deja disponible para que el cliente la revise. |
| **Relacionado con** | RF-001, RF-003, RF-004 |

**RF-003 - Solicitar ajuste de cotización**

| **Campo** | **Contenido** |
| :--- | :--- |
| **Descripción** | El sistema registra una solicitud del cliente para ajustar una cotización recibida. |
| **Origen** | Se deriva de la entrevista (Pregunta 12). Se tomó en cuenta que una cotización no siempre se acepta o rechaza directamente, ya que el cliente puede solicitar cambios en las características del trabajo para ajustar el precio. |
| **Prioridad** | Importante |
| **Criterio de aceptación** | Al solicitar un ajuste sobre una cotización, el sistema registra la solicitud de cambio asociada a esa cotización y la mantiene pendiente de revisión por el artista. |
| **Relacionado con** | RF-002, RF-004 |

**RF-004 - Registrar decisión sobre cotización**

| **Campo** | **Contenido** |
| :--- | :--- |
| **Descripción** | El sistema registra la aceptación o rechazo de una cotización por parte del cliente. |
| **Origen** | Visión del producto y entrevista (Pregunta 12). La Visión ya contemplaba aceptar o rechazar cotizaciones y la entrevista confirmó ambas respuestas, además de revelar que pueden estar precedidas por una negociación. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al aceptar una cotización, el sistema registra la decisión como aceptada. Al rechazarla, registra la decisión como rechazada. La decisión queda asociada a la cotización correspondiente. |
| **Relacionado con** | RF-002, RF-003, RF-005 |

**RF-005 - Actualizar estado de comisión**

| **Campo** | **Contenido** |
| :--- | :--- |
| **Descripción** | El sistema actualiza la etapa registrada de una comisión durante su realización. |
| **Origen** | Derivado de la necesidad de seguimiento establecida en la Visión del producto y reforzado por la entrevista (Pregunta 14). En esta se mostró que el artista distingue en qué etapa se encuentra cada encargo, aunque actualmente lo hace mediante archivos, listas y conocimiento personal. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al seleccionar una etapa disponible para una comisión activa, el sistema registra el cambio y muestra la nueva etapa en la información de la comisión. |
| **Relacionado con** | RF-006, RF-007, RF-008 |

**RF-006 - Registrar avance de comisión**

| **Campo** | **Contenido** |
| :--- | :--- |
| **Descripción** | El sistema registra un avance asociado a una comisión activa. |
| **Origen** | Visión del producto y entrevista (Preguntas 1 y 14). La Visión contemplaba la publicación de avances y la entrevista confirmó que el artista actualmente envía avances al cliente durante el desarrollo del trabajo. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al registrar un avance en una comisión activa, el sistema lo guarda asociado a esa comisión y lo incorpora a su seguimiento. |
| **Relacionado con** | RF-005, RF-007, RF-010 |

**RF-007 - Consultar progreso de comisión**

| **Campo** | **Contenido** |
| :--- | :--- |
| **Descripción** | El sistema muestra al cliente el progreso registrado de su comisión. |
| **Origen** | Visión del producto y entrevista (Pregunta 14). La Visión ya contemplaba que el cliente revisara avances y la entrevista reforzó esta necesidad al revelar que actualmente el cliente solo conoce el progreso cuando el artista le envía información o cuando pregunta directamente. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al consultar una comisión, el cliente puede visualizar su estado actual y los avances registrados correspondientes a esa comisión. |
| **Relacionado con** | RF-005, RF-006 |

**RF-008 - Solicitar modificación**

| **Campo** | **Contenido** |
| :--- | :--- |
| **Descripción** | El sistema registra una solicitud de modificación del cliente asociada a una comisión activa. |
| **Origen** | Visión del producto y entrevista (Preguntas 4, 8 y 13). La Visión contemplaba la solicitud de modificaciones y la entrevista confirmó que estas ocurren durante el trabajo y que su manejo depende del tipo de cambio y de la etapa en la que se encuentre la comisión. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al enviar una modificación sobre una comisión activa, el sistema registra la solicitud y la mantiene asociada a la comisión correspondiente para su revisión. |
| **Relacionado con** | RF-009, RF-010, RF-011 |

**RF-009 - Proponer condiciones de modificación**

| **Campo** | **Contenido** |
| :--- | :--- |
| **Descripción** | El sistema registra las condiciones propuestas por el artista para atender una solicitud de modificación. |
| **Origen** | Regla de negocio definida en la Visión del producto y reforzada por la entrevista (Preguntas 4, 8 y 13). La Visión establece que una modificación que afecte precio, alcance o fecha debe ser aprobada por ambas partes, mientras que la entrevista mostró que el artista evalúa el impacto del cambio según su magnitud y la etapa del trabajo. |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Al responder una solicitud de modificación, el artista puede registrar las condiciones bajo las que realizará el cambio. El sistema conserva la propuesta asociada a la modificación y la mantiene pendiente de decisión por parte del cliente. |
| **Relacionado con** | RF-008, RF-010, RF-011 |

**RF-010 - Consultar historial de comisión**

| **Campo** | **Contenido** |
| :--- | :--- |
| **Descripción** | El sistema muestra el historial de eventos registrados de una comisión. |
| **Origen** | Derivado del problema identificado en la Visión del producto y reforzado por la entrevista (Pregunta 5). La entrevista confirmó que actualmente el artista debe buscar manualmente conversaciones anteriores para comprobar qué se había acordado con el cliente. |
| **Prioridad** | Importante |
| **Criterio de aceptación** | Al consultar el historial de una comisión, el sistema muestra en orden cronológico los cambios de estado, avances, modificaciones y acuerdos registrados para esa comisión. |
| **Relacionado con** | RF-005, RF-006, RF-008, RF-009, RF-011 |

**RF-011 - Registrar decisión sobre modificación**

| **Campo** | **Contenido** |
| :--- | :--- |
| **Descripción** | El sistema registra la aceptación o rechazo del cliente sobre las condiciones propuestas para una modificación. |
| **Origen** | Regla de negocio definida en la Visión del producto y reforzada por la entrevista (Pregunta 13). La Visión establece que una modificación que cambie precio, alcance o fecha debe ser aprobada por ambas partes, y la entrevista confirmó que los cambios grandes pueden modificar las condiciones originales del encargo |
| **Prioridad** | Imprescindible |
| **Criterio de aceptación** | Si el cliente acepta las condiciones propuestas, el sistema registra la modificación como aprobada y conserva las nuevas condiciones asociadas a la comisión. Si las rechaza, el sistema conserva las condiciones anteriores del encargo. |
| **Relacionado con** | RF-008, RF-009, RF-010 |

**RF-012 - Enviar mensaje en una comisión**

| **Campo** | **Contenido** |
| :--- | :--- |
| **Descripción** | El sistema registra un mensaje enviado por un cliente o artista dentro de una comisión en la que participa. |
| **Origen** | Derivado del problema definido en la Visión del producto y reforzado por la entrevista (Preguntas 5 y 7). La entrevista mostró que actualmente la información de un encargo se consulta mediante conversaciones, listas y archivos separados, por lo que se incorporó la comunicación asociada directamente a cada comisión. |
| **Prioridad** | Importante |
| **Criterio de aceptación** | Al enviar un mensaje desde una comisión, el sistema lo registra asociado a esa comisión y al usuario que lo envió. |
| **Relacionado con** | RF-013, RNF-SEG-001 |

**RF-013 - Consultar conversación de una comisión**

| **Campo** | **Contenido** |
| :--- | :--- |
| **Descripción** | El sistema muestra los mensajes registrados entre el cliente y el artista de una comisión. |
| **Origen** | Derivado del problema definido en la Visión del producto y reforzado por la entrevista (Pregunta 5). La entrevista mostró que revisar acuerdos anteriores requiere buscar manualmente dentro de conversaciones extensas, por lo que se incorporó la consulta de mensajes asociados a cada comisión. |
| **Prioridad** | Importante |
| **Criterio de aceptación** | Al consultar la conversación de una comisión, el sistema muestra en orden cronológico los mensajes registrados para esa comisión. |
| **Relacionado con** | RF-012, RNF-SEG-001 |

---

## 4. Requisitos no funcionales

### 4.1 Resumen

| **ID** | **Atributo** | **Nombre** | **Prioridad** | **Origen** |
| :--- | :--- | :--- | :--- | :--- |
| **RNF-SEG-001** | Seguridad | Acceso restringido a comisiones | Imprescindible | Visión del producto |
| **RNF-USA-001** | Usabilidad | Ejecución de operaciones principales | Importante | Visión del producto |
| **RNF-CON-001** | Confiabilidad/Integridad | Conservación de información de la comisión | Imprescindible | Visión del producto |

### 4.2 Fichas

**Seguridad**

**RNF-SEG-001 - Acceso restringido a comisiones**

| **Campo** | **Contenido** |
| :--- | :--- |
| **Atributo de calidad** | Seguridad |
| **Descripción** | El sistema restringe la consulta y modificación de una comisión a los usuarios relacionados con ella. |
| **Métrica** | El 100 % de los intentos de consulta o modificación realizados por usuarios que no participan en una comisión deben ser rechazados. |
| **Origen** | Visión del producto. La seguridad fue identificada como atributo necesario porque ArtConnect almacena información y acuerdos relacionados con clientes y artistas. |
| **Prioridad** | Imprescindible |
| **Por qué importa** | Las comisiones contienen información sobre clientes, precios, condiciones y modificaciones. El acceso de usuarios ajenos podría exponer o alterar información privada. |
| **Afecta a** | RF-001, RF-002, RF-004, RF-005, RF-006, RF-007, RF-008, RF-009, RF-010, RF-011, RF-012, RF-013 |

**Usabilidad**

**RNF-USA-001 - Ejecución de operaciones principales**

| **Campo** | **Contenido** |
| :--- | :--- |
| **Atributo de calidad** | Usabilidad |
| **Descripción** | Los usuarios nuevos completan las operaciones principales de ArtConnect sin requerir asistencia especializada. |
| **Métrica** | Al menos el 80 % de los usuarios de una prueba de usabilidad deben completar sin ayuda las tareas de registrar una solicitud, revisar una cotización y consultar el progreso de una comisión. |
| **Origen** | Visión del producto. La usabilidad fue identificada como atributo necesario porque clientes y artistas deben poder utilizar ArtConnect sin requerir conocimientos técnicos especializados. |
| **Prioridad** | Importante |
| **Por qué importa** | Si las operaciones principales son difíciles de entender, los usuarios pueden volver a gestionar sus encargos mediante redes sociales y aplicaciones de mensajería. |
| **Afecta a** | RF-001, RF-002, RF-004, RF-007, RF-008 |

**Confiabilidad/Integridad**

**RNF-CON-001 - Conservación de información de la comisión**

| **Campo** | **Contenido** |
| :--- | :--- |
| **Atributo de calidad** | Confiabilidad/Integridad |
| **Descripción** | El sistema conserva los estados, avances, modificaciones, acuerdos y mensajes registrados en una comisión sin perder la información anterior. |
| **Métrica** | El 100 % de los estados, avances, modificaciones, acuerdos y mensajes registrados debe conservar su contenido y relación con la comisión después de actualizaciones posteriores. |
| **Origen** | Visión del producto. La integridad fue identificada como atributo necesario porque precios, fechas, condiciones y modificaciones deben conservarse correctamente para mantener un registro confiable de los acuerdos. |
| **Prioridad** | Imprescindible |
| **Por qué importa** | Si la información registrada se pierde o modifica incorrectamente, cliente y artista podrían disponer de versiones diferentes de lo acordado, reproduciendo uno de los problemas que ArtConnect busca resolver. |
| **Afecta a** | RF-005, RF-006, RF-008, RF-009, RF-010, RF-011, RF-012, RF-013 |

---

## 5. Casos de uso

### 5.1 Relación de Casos de Uso del Sistema

| **ID** | **Caso de uso** | **Actor(es)** | **Requisitos relacionados** |
| :--- | :--- | :--- | :--- |
| **CU-01** | Solicitar comisión artística | Cliente | RF-001 |
| **CU-02** | Emitir cotización | Artista | RF-002 |
| **CU-03** | Responder cotización | Cliente | RF-003, RF-004 |
| **CU-04** | Actualizar seguimiento de comisión | Artista | RF-005, RF-006 |
| **CU-05** | Consultar seguimiento de comisión | Cliente | RF-007, RF-010 |
| **CU-06** | Gestionar modificación de comisión | Cliente, Artista | RF-008, RF-009, RF-011 |
| **CU-07** | Comunicarse en una comisión | Cliente, Artista | RF-012, RF-013 |

### 5.2 Detalle de los Casos de Uso del Sistema

**CU-06 Gestionar modificación de comisión**

*   **Actor principal:** Cliente
*   **Actor participante:** Artista

*   **Objetivo:** Gestionar una modificación solicitada por el cliente durante una comisión activa, permitiendo que el artista determine las condiciones para realizarla y que el cliente decida si acepta dichas condiciones.

*   **Precondición:** Existe una comisión activa entre el cliente y el artista derivada de una cotización previamente aceptada.

**Escenario principal**

1.  El Cliente consulta una comisión activa.
2.  El sistema muestra la información y el seguimiento actual de la comisión.
3.  El Cliente solicita una modificación y describe el cambio que desea realizar.
4.  El sistema registra la solicitud de modificación asociada a la comisión (RF-008).
5.  El Artista consulta la modificación solicitada.
6.  El Artista evalúa el impacto que tendría el cambio sobre el trabajo.
7.  El Artista registra las condiciones necesarias para realizar la modificación (RF-009).
8.  El sistema muestra al Cliente las condiciones propuestas.
9.  El Cliente acepta las nuevas condiciones.
10. El sistema registra la modificación como aprobada y conserva las nuevas condiciones asociadas a la comisión (RF-011).
11. El sistema conserva el registro de la modificación y de las condiciones anteriores dentro del historial de la comisión (RNF-CON-001).

**Flujos alternos**

* **Flujo alterno A - El cambio no requiere modificar las condiciones originales**

1.  En el paso 6, el Artista determina que el cambio solicitado puede realizarse sin modificar el precio, alcance o fecha de entrega.
2.  El Artista registra que la modificación puede realizarse manteniendo las condiciones actuales.
3.  El sistema registra la modificación como aprobada.
4.  La comisión continúa manteniendo las condiciones previamente acordadas.
5.  El sistema conserva la modificación dentro del historial de la comisión.

* **Flujo alterno B - El Cliente rechaza las nuevas condiciones**

1.  En el paso 9, el Cliente no está de acuerdo con las condiciones propuestas por el Artista.
2.  El Cliente rechaza la propuesta de modificación.
3.  El sistema registra que la modificación no fue aprobada (RF-011).
4.  El sistema conserva las condiciones que estaban vigentes antes de solicitar el cambio.
5.  La comisión continúa sin incorporar la modificación solicitada.

* **Flujo alterno C - La comisión ya no admite nuevas modificaciones**

1.  Al intentar solicitar una modificación, el sistema verifica la situación actual de la comisión.
2.  Si la comisión ya no se encuentra activa, el sistema impide registrar la nueva solicitud.
3.  El sistema conserva la información de la comisión sin cambios.
4.  El flujo termina sin crear una modificación.

**Postcondición**

La solicitud de modificación queda registrada con su resultado.

Si fue aprobada, la comisión conserva las condiciones correspondientes a la modificación junto con el registro de las condiciones anteriores. Si fue rechazada, las condiciones anteriores continúan vigentes.

**Requisitos que realiza**

- **RF-008:** Solicitar modificación.
- **RF-009:** Proponer condiciones de modificación.
- **RF-011:** Registrar decisión sobre modificación.
- **RNF-CON-001:** Conservación de información de la comisión.

---

## 6. Trazabilidad

| **Requisito** | **Origen** | **Caso de uso** | **Elemento del prototipo** |
| :--- | :--- | :--- | :--- |
| **RF-001** | Visión del producto + Entrevista (P10) | CU-01 Solicitar comisión artística | Nueva solicitud |
| **RF-002** | Visión del producto + Entrevista (P11) | CU-02 Emitir cotización | Crear cotización |
| **RF-003** | Entrevista (P12) | CU-03 Responder cotización | Cotización recibida, opción “Solicitar ajuste” |
| **RF-004** | Visión del producto + Entrevista (P12) | CU-03 Responder cotización | Cotización recibida, botones “Aceptar” y “Rechazar” |
| **RF-005** | Derivado del seguimiento de la Visión + Entrevista (P14) | CU-04 Actualizar seguimiento de comisión | Detalle de comisión, control de etapa actual |
| **RF-006** | Visión del producto + Entrevista (P1 y P14) | CU-04 Actualizar seguimiento de comisión | Detalle de comisión, sección “Publicar avance” |
| **RF-007** | Visión del producto + Entrevista (P14) | CU-05 Consultar seguimiento de comisión | Seguimiento de comisión, estado y avances |
| **RF-008** | Visión del producto + Entrevista (P4, P8 y P13) | CU-06 Gestionar modificación de comisión | Detalle de comisión, opción “Solicitar modificación” |
| **RF-009** | Regla de negocio de la Visión + Entrevista (P4, P8 y P13) | CU-06 Gestionar modificación de comisión | Solicitud de modificación (para el artista), formulario de nuevas condiciones |
| **RF-010** | Problema definido en la Visión + Entrevista (P5) | CU-05 Consultar seguimiento de comisión | Historial de comisión |
| **RF-011** | Regla de negocio de la Visión + Entrevista (P13) | CU-06 Gestionar modificación de comisión | Revisión de modificación, botones “Aceptar” y “Rechazar” |
| **RF-012** | Derivado del problema de la Visión + Entrevista (P5 y P7) | CU-07 Comunicarse en una comisión | Conversación, campo de mensaje y botón “Enviar” |
| **RF-013** | Derivado del problema de la Visión + Entrevista (P5) | CU-07 Comunicarse en una comisión | Conversación, historial cronológico de mensajes |
| **RNF-SEG-001** | Visión del producto | Transversal a CU-01–CU-07 | Acceso a comisiones |
| **RNF-USA-001** | Visión del producto | Transversal a los flujos principales | Flujo general del prototipo |
| **RNF-CON-001** | Visión del producto | CU-04, CU-05, CU-06 y CU-07 | Detalle/Historial de comisión |

---

## 7. Registro de cambios

| **Fecha** | **Requisito** | **Qué cambió** | **Por qué** |
| :--- | :--- | :--- | :--- |
| 27/09/2026 | General | Se eliminó el usuario Administrador del alcance actual del sistema. | Durante la elicitación no se identificaron necesidades o funciones suficientes que justificaran su participación como usuario del sistema actual. |
| 27/09/2026 | Alcance, RF-012 y RF-013 | Se incorporó la mensajería entre Cliente y Artista dentro de cada comisión. | Se determinó que mantener la comunicación exclusivamente en plataformas externas conservaría parte del problema de dispersión de información identificado en la Visión del producto. |
| 27/09/2026 | RF-009 y RF-011 | Se separó la propuesta de condiciones de una modificación de la decisión del cliente sobre dichas condiciones. | La Visión del producto establece que los cambios que afecten precio, alcance o fecha deben ser aprobados por ambas partes. |
| 27/09/2026 | RNF-CON-001 | Se amplió la conservación de información para incluir los mensajes asociados a una comisión. | La incorporación de mensajería requiere que la conversación relacionada con el encargo también forme parte de la información que debe conservarse. |
| 28/09/2026 | RF-001 a RF-013 | Se refinó el origen de los requisitos funcionales, identificando las preguntas específicas de la entrevista, reglas de negocio y problemas de la Visión del producto que sustentan cada requisito. | Mejorar la trazabilidad entre la Visión del producto, los hallazgos de la entrevista y los requisitos definidos. |
| 28/09/2026 | Casos de uso | Se definieron los siete casos de uso del sistema y se documentó en detalle CU-06 Gestionar modificación de comisión, incluyendo escenario principal, flujos alternos, precondición y postcondición. | Relacionar los requisitos funcionales con los objetivos completos de Cliente y Artista y establecer la base para el diagrama UML y el prototipo. |
| 28/09/2026 | RF-001 | Se especificaron los datos obligatorios de una solicitud de comisión: descripción del trabajo, estilo solicitado, cantidad de elementos, nivel de detalle y referencias. | Mejorar la verificabilidad del requisito y evitar ambigüedad sobre qué información debe contener una solicitud. |
| 28/09/2026 | Conflicto entre usuarios / RF-008, RF-009 y RF-011 | Se documentó cómo se resuelve el conflicto entre Cliente y Artista cuando una modificación afecta el precio, alcance o fecha de entrega. | Cumplir con la revisión de consistencia, dejando claro que el artista propone nuevas condiciones y el cliente debe aceptarlas antes de incorporar el cambio a la comisión. |
| 29/09/2026 | Trazabilidad | Se completó la tabla de trazabilidad relacionando los requisitos funcionales y no funcionales con su origen, casos de uso y elementos correspondientes del prototipo. | Garantizar la conexión entre los requisitos definidos, los objetivos representados en los casos de uso y su representación en el prototipo. |
| 30/10/2026 | Revisión de dupla | Se realizó una revisión general del documento verificando redacción, consistencia, requisitos, casos de uso y trazabilidad. | Registrar la revisión realizada por la dupla antes de la entrega final. |

---

## 8. Revisión de la dupla

**Revisado por:** Jorge Eduardo García Hernández  
**Rol:** Dupla  
**Fecha de revisión:** 30 de septiembre de 2026
