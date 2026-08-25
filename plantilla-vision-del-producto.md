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

**Los usuarios que podrían beneficiarse de este sistema serían los alumnos, que usarían el sistema para agendar sus citas, consutar los horarios disponibles, conocer quién será su psicólogo, etc.
EL psicólogo o terapeuta para administrar su disponibilidad, consultar sus citas, conocer los estudiantes que atenderá y recibir notificaciones sobre nuevas citas, cancelaciones o cambios.
Y el personal encargado para gestionar las solicitudes de atención, horarios y profesionales, además de apoyar en la organización general del servicio.**

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

### Cinco cosas que el sistema SÍ hace

**1.- Permite a los clientes solicitar trabajos artísticos personalizados indicando el tipo de obra, característica y fecha deseada**

**2.- Permite a los artistas enviar cotizaciones con el precio, condiciones, tiempo estimado y características del trabajo**

**3.- Permite a los clientes revisar y aprobar una cotización antes de que el artista comience el trabajo**

**4.- Permite a los artistas publicar avances de una obra para que el cliente pueda revisarlos y slicitar modificaciones**

**5.- Permite a clientes y artistas consultar el estado de un encargo, incluyendo sus fechas, acuerdos, avances y solicitudes de cambio**

### Tres cosas que el sistema explícitamente NO hace

**1.- No crea ni edita las obras artísticas; Solo permite solicitar, acordar y dar seguimiento al trabajo, la creación de la obra el artista la realiza fuera de los parámetros del sistema**

**2.- No determina automáticamente el precio de una obra; El artista es quien establece el precio de acuerdo con las características y condiciones del encargo**

**3.- No funciona como una red social para artistas: No busca permitir publicaciones generales, seguidores, comentarios o contenido que no esté relacionado con un encargo**

### Razón para la exlusion - No crea ni edita las obras artísticas -
**El sistema no crea ni edita las obras artísticas porque su objetivo es facilitar la contratación y seguimiento de los encargos, no proporcionar herramientas profesionales de edición o creación. Incluir herramientas de dibujo o edición digial aumentaría considerablemente el alcance del proyecto y lo convertiría en un producto diferente**

### Funcionalidad futura - Sistema de pagos integrado
**Me gustaría que este sistema permitiera realizar anticipos y pagos directamente dentro de la plataforma, así como llevar un registro automático de los pagos realizados y pendientes. Solo que esta funcionalidad queda fuera del alcance del proyecto debido al tiempo disponible y a la complejidad de integrar un sistema de pagos seguros.**

### Dentro del alcance

-
-
-
-

### Explícitamente fuera del alcance

-
-
-

**Por qué queda fuera:**

*Instrucción: para al menos una de las exclusiones, explica la razón. Puede ser tiempo, complejidad, o que no aporta al problema central.*

---

## 4. Tipo de sistema y restricciones

*Instrucción: identifica de qué tipo es tu sistema y qué te obliga a garantizar ese tipo. Un sistema de información y un sistema crítico no se diseñan igual.*

**Tipo de sistema:**

*(De información · Embebido · Crítico · Web y SaaS · De datos y análisis)*

**Por qué es de ese tipo:**

**Atributos de calidad que impone:**

| Atributo | Por qué importa en mi caso | Qué pasa si no se cumple |
|---|---|---|
| | | |
| | | |
| | | |

**Reglas de negocio que ya identifiqué:**

*Instrucción: reglas que no son obvias desde fuera y que alguien que conoce el dominio tendría que explicarte. Si no encuentras ninguna, tu caso puede ser demasiado simple.*

1.
2.
3.

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
