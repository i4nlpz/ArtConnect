# Visión del producto

---

**Autor: Ian Adolfo López Maldonado**

**Fecha de la última versión: 18/08/26**

**Repositorio: ArtConnect**

---

## 1. Descripción del sistema

**Nombre del sistema: ArtConnect**

**Descripción: 
ArtConnect es un sistema que facilita la contratación y gestión de trabajos artísticos personalizados entre clientes y artistas. permite que los clientes soliciten obras, ya sea ilustraciones, pinturas, retratos o diseños, que puedan saber las condiciones del trabajo y den seguimiento a su encargo, mientras que los artistas puedan organizar sus solicitudes, fechas de entrega y tengan comunicación con sus clientes.**

---

## 2. Problema y usuarios

### El Problema

**Actualmente los encargos artísticos suelen gestionarse mediante redes sociales, mensajes y conversaciones informales. Esto puede provocar que la información sobre el precio, las características de la obra, las fechas de entrega y los cambios solicitados queden dispersos.**

### Cómo se resuelve hoy sin el sistema
**El cliente normalmente contacta el artista mediante redes sociales (ya sea twitter, instagram facebook, etc.) o servicios de mensajería, explica lo que quiere y recibe una cotización. Luego, ambos acuerdan el precio, detalles y la fecha de entrega mediante mensajes. Durante el proceso, el artista puede enviar avances para recibir comentarios y el cliente solicita modificaciones. Los pagos y anticipos también pueden coordinarse por separado. Si surge algún cambio o desacuerdo, esto se debe revisar manualmente para determinar qué se había acordado**

**Usuarios del sistema:**

| Tipo de usuario | Qué necesita del sistema | Qué le preocupa |
|---|---|---|
|Cliente|Solicitar una obra, consultar precios y condiciones, revisar avances, solicitar cambios y conocer el estado de su encargo.|Que el resultado corresponda a lo acordado, conocer el costo y recibir la obra dentro del tiempo establecido.|
|Artista|Administrar encargos, fechas de entrega, solicitudes de clientes, avances y condiciones de cada trabajo.|Que los cambios no excedan lo acordado, recibir los pagos correspondientes y cumplir con sus fechas de entrega.|
|Administrador|Supervisar los encargos y resolver problemas entre clientes y artistas.|Que los acuerdos se respeten y que el servicio funcione correctamente.|


**Un conflicto entre usuarios**

**El cliente puede querer realizar varias modificaciones a una obra hasta quedar satisfecho, mientras que el artista necesita limitar los cambios para evitar que un trabajo termine requiriendo mucho más tiempo del acordado.**


---

## 3. Alcance

### Dentro del alcance - Cinco cosas que el sistema SÍ hace

1. Permite a los clientes solicitar trabajos artísticos personalizados indicando el tipo de obra, característica y fecha deseada
2. Permite a los artistas enviar cotizaciones con el precio, condiciones, tiempo estimado y características del trabajo
3. Permite a los clientes revisar y aprobar una cotización antes de que el artista comience el trabajo
4. Permite a los artistas publicar avances de una obra para que el cliente pueda revisarlos y slicitar modificaciones
5. Permite a clientes y artistas consultar el estado de un encargo, incluyendo sus fechas, acuerdos, avances y solicitudes de cambio

### Explícitamente fuera del alcance - Tres cosas que el sistema NO hace

1. No crea ni edita las obras artísticas; Solo permite solicitar, acordar y dar seguimiento al trabajo, la creación de la obra el artista la realiza fuera de los parámetros del sistema
2. No determina automáticamente el precio de una obra; El artista es quien establece el precio de acuerdo con las características y condiciones del encargo
3. No funciona como una red social para artistas: No busca permitir publicaciones generales, seguidores, comentarios o contenido que no esté relacionado con un encargo

### Por qué queda fuera: No crea ni edita las obras artísticas -
**El sistema no crea ni edita las obras artísticas porque su objetivo es facilitar la contratación y seguimiento de los encargos, no proporcionar herramientas profesionales de edición o creación. Incluir herramientas de dibujo o edición digial aumentaría considerablemente el alcance del proyecto y lo convertiría en un producto diferente**

### Funcionalidad futura - Sistema de pagos integrado
**Me gustaría que este sistema permitiera realizar anticipos y pagos directamente dentro de la plataforma, así como llevar un registro automático de los pagos realizados y pendientes. Solo que esta funcionalidad queda fuera del alcance del proyecto debido al tiempo disponible y a la complejidad de integrar un sistema de pagos seguros.**

---

## 4. Tipo de sistema y restricciones

**Tipo de sistema: Sistema de Información**

**Por qué es de ese tipo: Porque este sistema permite recopilar, organizzar, consultar y actualizar información relacionada con los encargos artísticos. El sistema almacena datos e clientes, artistas, solicitudes, cotizaciones, fechas de entrega, avances y modificaciones, y permite que cada usuario consulte la información que necesita para llevar a cabo su parte del proceso.**

**Atributos de calidad que impone:**

| Atributo | Por qué importa en mi caso | Qué pasa si no se cumple |
|---|---|---|
|Seguridad|Porque manejará info. personal de clientes y artistas, además de información sobre encargos y acuerdos|Usuarios no autorizados podrían acceder o modificar información de otros usuarios|
|Usabilidad|Porque el cliente y artista deben poder solicitar, consultar y actualizar info. sin necesitar conocimientos técnicos|Los usuarios podrían confundirse, cometer errores o preferir continuar utilizando mensajes y redes sociales|
|Disponibilidad|Porque los usuarios necesitan consultar sus encargos, fechas y avances cuando lo necesiten, especialmente durante un trabajo en proceso|El cliente o artista podría no tener acceso a información importante sobre el encargo|

**Reglas de negocio que ya identifiqué:**

1. Un artista debe establecer las condiciones de un encargo antes de que el cliente pueda aprobarlo - esto incuye aspectos como el precio, características del trabajo y fecha estimada de entrega.
2. Las modificaciones solicitadas por el cliente pueden afectar la condiciones originales del encargo - por lo que debe definirse cuándo una modificación forma parte del trabajo acordado y cuándo forma parte de un trabajo adicional.
3. Un encargo no debe considerarse terminado hasta que el artista entregue la obra y el cliente confirme que recibió el trabajo acordado.

---

## 5. Ciclo de vida elegido

*Instrucción: este apartado se trabaja en la semana 3, después de ver los modelos de desarrollo. La justificación pesa más que la elección: no hay un modelo correcto, hay uno defendible para tu caso.*

**Modelo elegido:**

**Por qué le conviene a este proyecto:**

*Instrucción: argumenta con las características reales de tu caso. Estabilidad de los requisitos, disponibilidad del cliente, nivel de riesgo, tamaño del equipo, frecuencia de entregas esperada.*

### Alternativas descartadas

**Alternativa 1:**

*Por qué la descarté:*

**Alternativa 2:**

*Por qué la descarté:*

---

## Antes de entregar

Reviso que el documento cumpla lo siguiente:

- [ ] La descripción del apartado 1 se entiende sin ser del área
- [ ] Hay al menos dos tipos de usuario con necesidades distintas
- [ ] Identifiqué un conflicto real entre usuarios
- [ ] El alcance dice qué queda fuera, no solo qué queda dentro
- [ ] Las exclusiones son específicas, no genéricas
- [ ] Identifiqué el tipo de sistema y al menos dos atributos de calidad
- [ ] Anoté al menos tres reglas de negocio no obvias
- [ ] Justifiqué el ciclo de vida contra dos alternativas descartadas
- [ ] El documento está en mi repositorio y se puede leer desde el navegador
- [ ] Borré todas las instrucciones en cursiva de la plantilla
