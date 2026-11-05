# Análisis de sustantivos: ArtConnect

## Paso 1. Sustantivos subrayados (sin filtrar)

acceso, aceptación, acuerdo, ajuste, alcance, aplicación de mensajería, artista, archivo, asistencia especializada, atributo de calidad, avance, boceto, cambio, cantidad de elementos, cliente, comisión, comunicación, condición, confiabilidad, conocimiento técnico, consulta, contenido, conversación, cotización, decisión, descripción, desarrollo, detalle, entrega, estado, etapa, evento, fecha, fecha estimada de entrega, fecha límite, historial, información, integridad, intento, mensaje, modificación, nivel de detalle, nota, obra artística, obligación económica, operación, pago, plataforma, precio, proceso, progreso, propuesta, referencia, rechazo, registro, red social, requisito, resultado, solicitud, solicitud de ajuste, solicitud de comisión, solicitud de modificación, sistema, estilo, tarea, transferencia, usuario, usabilidad, usuario participante, usuario ajeno, prueba de usabilidad, trabajo artístico, encargo, actualización.

## Paso 2. Clases candidatas (4)

Se aplicó el filtro de las cuatro razones: es atributo, es sinónimo de otra, está fuera del sistema o es demasiado vago.

| Clase | Sustantivos de los que sale | Por qué pasó el filtro |
| :--- | :--- | :--- |
| Usuario | usuario, cliente, artista, usuario participante | Tiene identidad y un rol dentro del sistema. Puede ser cliente o artista, y sus permisos y operaciones dependen de ese rol. Participa en las solicitudes, cotizaciones, modificaciones y conversaciones (RNF-SEG-001). |
| Solicitud | solicitud, solicitud de comisión, descripción, estilo, cantidad de elementos, nivel de detalle, referencias | Representa el pedido inicial de un trabajo artístico. Tiene información propia, pertenece a un cliente y se envía al artista para que pueda evaluarla y elaborar una cotización (RF-001). |
| Cotización | cotización, precio, condiciones, fecha estimada de entrega, ajuste, aceptación, rechazo | Contiene la propuesta económica y las condiciones que establece el artista para realizar un encargo. Tiene un estado y permite registrar ajustes, aceptación o rechazo por parte del cliente (RF-002, RF-003 y RF-004). |
| Comisión | comisión, encargo, trabajo por encargo, estado, etapa, seguimiento | Representa el trabajo que se realiza después de aceptar una cotización. Tiene un estado, condiciones acordadas y relaciones con el cliente y el artista. Permite organizar el seguimiento, los avances y las modificaciones (RF-005, RF-006, RF-007 y RF-008). |
| Condiciones de trabajo | condición, precio, alcance, fecha de entrega, condiciones originales, nuevas condiciones | Contiene los términos acordados para realizar una comisión. Es importante porque el sistema debe conservar las condiciones anteriores y registrar las nuevas cuando una modificación es aprobada por ambas partes (RF-002, RF-009, RF-011 y RNF-CON-001). |
| Modificación | modificación, solicitud de modificación, cambio, propuesta, decisión | Representa un cambio solicitado por el cliente durante una comisión. Tiene una descripción y un resultado, y puede requerir nuevas condiciones propuestas por el artista y aceptadas o rechazadas por el cliente (RF-008, RF-009 y RF-011). |
| Avance | avance, progreso, etapa, información del trabajo | Representa la información que el artista registra para mostrar cómo se desarrolla una comisión. Está asociado a una comisión y permite mantener actualizado su seguimiento (RF-006 y RF-007). |
| Mensaje | mensaje, comunicación, contenido, conversación | Representa una comunicación entre el cliente y el artista dentro de una comisión. Tiene un emisor y pertenece a una comisión, permitiendo conservar y consultar los mensajes en orden cronológico (RF-012, RF-013 y RNF-CON-001). |

## Paso 3. Qué sabe y qué hace cada clase

| Clase | Sabe | Hace |
| :--- | :--- | :--- |
| Usuario | Identidad, rol (Cliente o Artista) y comisiones en las que participa. | Registra solicitudes, elabora o revisa cotizaciones, actualiza o consulta comisiones y se comunica con el otro participante según su rol. |
| Solicitud | Descripción del trabajo, estilo solicitado, cantidad de elementos, nivel de detalle, referencias y cliente que la realizó. | Registra el pedido inicial y lo presenta al artista para que pueda evaluarlo y elaborar una cotización. |
| Cotización | Precio, condiciones del trabajo, fecha estimada de entrega y estado de la propuesta. | Registra la propuesta del artista y permite guardar los ajustes, la aceptación o el rechazo del cliente. |
| Comisión | Cliente, artista, estado actual, etapa de realización y condiciones acordadas. | Actualiza su estado, organiza los avances, relaciona las modificaciones y mantiene la información del trabajo. |
| Condiciones de trabajo | Precio, alcance y fecha de entrega acordados, así como las condiciones anteriores y las nuevas propuestas. | Conserva las condiciones originales y registra las nuevas cuando una modificación es aprobada. |
| Modificación | Descripción del cambio solicitado, comisión relacionada, condiciones propuestas y resultado de la decisión. | Registra la solicitud, permite que el artista proponga condiciones y conserva la aceptación o el rechazo del cliente. |
| Avance | Información sobre el progreso de una comisión y la comisión a la que pertenece. | Registra un avance y lo incorpora al seguimiento para que el cliente pueda consultarlo. |
| Mensaje | Contenido, usuario que lo envió y comisión a la que pertenece. | Registra y muestra los mensajes de la conversación en orden cronológico. |

## Paso 4. Sustantivos descartados y por qué

| Razón | Descartados | Qué son realmente |
| :--- | :--- | :--- |
| Es un atributo | Descripción, estilo, cantidad de elementos, nivel de detalle, referencias, fecha límite. | Son datos que describen una Solicitud. |
| | Precio, alcance, fecha estimada de entrega, condiciones originales, nuevas condiciones. | Son datos que forman parte de las Condiciones de trabajo y de las cotizaciones. |
| | Estado, etapa, fecha de entrega, progreso. | Son datos o características de una Comisión. |
| | Decisión, aceptación, rechazo, resultado. | Son estados o resultados de una Cotización o Modificación. |
| | Contenido. | Es un dato propio de un Mensaje. |
| Es sinónimo de otra o representa un rol | Cliente, Artista, usuario participante, usuario ajeno. | Son roles o contextos de participación de la clase Usuario. No necesitan ser clases independientes en este primer análisis. |
| | Encargo, trabajo por encargo. | Son formas de referirse a la Comisión que administra el sistema. |
| | Solicitud de ajuste. | Es una acción relacionada con la Cotización, no una entidad independiente. |
| Está fuera del sistema | Redes sociales, aplicaciones de mensajería, notas, archivos. | Son herramientas externas que actualmente utilizan los clientes y artistas para organizar sus encargos y comunicarse. |
| | Pagos, anticipos, transferencias y obligaciones económicas. | Son operaciones y responsabilidades económicas que ArtConnect no procesa ni garantiza dentro de su alcance actual. |
| | Obra artística. | Es el resultado del trabajo del artista. El sistema gestiona el encargo, pero no crea, modifica ni edita la obra. |
| Es demasiado vago | Sistema, proceso, requisito, información, operación, plataforma, actualización. | Son términos generales del software o del funcionamiento del sistema, sin identidad propia como entidades del negocio. |
| | Seguimiento, progreso, historial, conversación. | Son conceptos que representan consultas o conjuntos de información. El seguimiento se obtiene de la Comisión y sus Avances; el historial reúne los eventos registrados y la conversación agrupa los Mensajes. |
| | Evento, registro, cambio, acuerdo, propuesta, comunicación. | Son conceptos generales que se representan mediante las clases Cotización, Comisión, Condiciones de trabajo, Modificación y Mensaje. |
| | Acceso, consulta, asistencia especializada, conocimiento técnico, prueba de usabilidad, tarea, atributo de calidad, confiabilidad, integridad, usabilidad, intento. | Son acciones, criterios o atributos relacionados con los requisitos no funcionales, no entidades principales del negocio. |
