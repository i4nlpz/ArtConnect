# Visión del producto

---

**Autor: Ian Adolfo López Maldonado**

**Fecha de la última versión: 01/09/26**

**Repositorio: ArtConnect**

---

## 1. Descripción del sistema

**Nombre del sistema: ArtConnect**

**Descripción: 
ArtConnect es un sistema que facilita la contratación y gestión de trabajos artísticos personalizados entre clientes y artistas. Permite que los clientes soliciten obras, reciban y aprueben cotizaciones, consulten el estado de sus encargos y revisen avances, mientras que los artistas pueden recibir solicitudes, establecer las condiciones de cada trabajo, organizar sus encargos y comunicarse con sus clientes.**

---

## 2. Problema y usuarios

### El Problema

**Actualmente los encargos artísticos suelen gestionarse mediante redes sociales, apps de mensajes y conversaciones informales. Esto puede provocar que la información sobre el precio, las características de la obra, las fechas de entrega y otros acuerdos queden dispersos. Como resultado de esto, tanto el cliente como el artista pueden tener dificultades para consultar qué se acordó originalmente o conocer el estado de un encargo.**

### Cómo se resuelve hoy sin el sistema
**El cliente normalmente contacta el artista mediante redes sociales (ya sea twitter, instagram facebook, etc.) o servicios de mensajería, explica lo que quiere y recibe una cotización. Luego, ambos acuerdan el precio, detalles y la fecha de entrega mediante mensajes. Durante el proceso, el artista puede enviar avances para recibir comentarios y el cliente solicita modificaciones. Los pagos y anticipos también pueden coordinarse por separado. Si surge algún cambio o desacuerdo, esto se debe revisar manualmente para determinar qué se había acordado**

**Usuarios del sistema:**

| Tipo de usuario | Qué necesita del sistema | Qué le preocupa |
|---|---|---|
|Cliente|Solicitar una obra, consultar precios y condiciones, revisar avances, solicitar cambios y conocer el estado de su encargo.|Que el resultado corresponda a lo acordado, conocer el costo y recibir la obra dentro del tiempo establecido.|
|Artista|Administrar encargos, fechas de entrega, solicitudes de clientes, avances y condiciones de cada trabajo.|Que las solicitudes sean claras, que los cambios no excedan lo acordado y poder cumplir con sus fechas de entrega.|
|Administrador|Consultar encargos, usuarios y reportes de problemas relacionados con el servicio.|Que los acuerdos registrados sean claros y que los conflictos puedan identificarse y atenderse.|


**Un conflicto entre usuarios**

**El cliente puede querer realizar varias modificaciones a una obra hasta quedar satisfecho, mientras que el artista necesita limitar los cambios para evitar que un trabajo termine requiriendo mucho más tiempo del acordado.**


---

## 3. Alcance

### Dentro del alcance - Cinco cosas que el sistema SÍ hace

1. Permite a los clientes crear solicitudes de trabajos artísticos personalizados.
2. Permite a los artistas enviar cotizaciones con precio, condiciones y fecha estimada de entrega.
3. Permite a los clientes aceptar o rechazar las cotizaciones recibidas.
4. Permite a los artistas publicar avances de una obra y a los clientes revisarlos y solicitar modificaciones.
5. Permite registrar y consultar modificaciones y acuerdos realizados durante.

### Explícitamente fuera del alcance - Tres cosas que el sistema NO hace

1. No procesa pagos ni anticipos entre clientes y artistas.
2. No crea ni edita las obras artísticas
3. No garantiza que un artista o cliente cumpla económiamente con sus obligaciones fuera de la plataforma

### Por qué queda fuera: Exclusión de pagos
**El procesamiento de pagos queda fuera del alcance porque requeriría implementar mecanísmos adicionales de seguridad, protección contra fraude, reembolsos y resolución de disputas. Además, implicaría una complejidad técnica y legal que no es necesaria para resolver el problema principal que aborda este sistema.**

### Funcionalidad futura: Sistema de pagos con proteción para clientes y artistas
**Me gustaría que este sistema pudiera recibir el pago del cliente, retenerlo durante el proceso y liberarlo al artista cuando se cumplan las condiciones acordadas. También permitiría solicitar reembolsos o iniciar disputas en caso de incumplimiento. Esta funcionalidad queda fuera del alcance actual debido a la complejidad técnica, de seguridad y de gestión de disputas que implicaría**

---

## 4. Tipo de sistema y restricciones

**Tipo de sistema: Web y SaaS a la medida**

**Por qué es de ese tipo: Porque este sistema permite será una plataforma accesible mediante Intenrnet que permitirá a clientes y artistas utilizar sus funciones sin necesidad de instalar el sistema en sus dispositivos. El sistema almacenará y procesará información relacionada con solicitudes, cotizaciones, acuerdos, avances y encargos. Y esta diseñado específicamente para gestionar las necesidades de usuarios que realizan trabajos por encargo.**

**Atributos de calidad que impone:**

| Atributo | Por qué importa en mi caso | Qué pasa si no se cumple |
|---|---|---|
|Seguridad|Porque almacenará info. personal, conversaciones, archivos y acuerdos entre clietes y artistas|Usuarios no autorizados podrían acceder o modificar información de otros usuarios|
|Usabilidad|Porque el cliente y artista deben poder utilizar el sistema sin conocimientos técnicos|Los usuarios podrían confundirse, cometer errores o preferir continuar utilizando mensajes y redes sociales|
|Integridad|Los precios, fechas, condiciones y modificaciones deben conservarse correctamente para que exista un registro confiable de los acuerdos|Podrían surgir conflictos porque el cliente y artista tendrían información diferente sobre lo acordado|

**Reglas de negocio que ya identifiqué:**

1. Una cotización debe especificar las condiciones principales del encargo antes de que el cliente pueda aceptarla.
2. Una modificación que cambie el precio, alcance o fecha de entrega debe ser aprobada por ambas partes antes de considerarse parte del encargo.
3. Una vez aceptada una cotización, sus condiciones originales deben conservarse aunque posteriormente se realicen modificaciones.

---

## 5. Ciclo de vida elegido

**Modelo elegido: Ágil**

**Por qué le conviene a este proyecto: Porque puede ir cambiando conforme reciba retroalimentación de los artistas y clientes, permitiendo adaptar las funciones y requisitos durante el desarrollo en lugar de tener que definir todo desde el principio.**

### Alternativas descartadas

**Alternativa 1: Proceso Unificado**

- Porque, aunque este modelo permmite trabajar de forma iterativa y adaptarse a cambios, está más orientado a mantener una mayor planificación del proyecto. Para mi sistema preferí un modelo más flexible que permita cambiar prioridades y requisitos rápidamente conforme reciba retroalimentación.

**Alternativa 2: Prototipado**

- Aunque sería útil para diseñar y validar la interfaz del sistema, el principal reto del proyeto no es solo el UX, sino definir y adaptar las reglas del proceso de las comisiones. Por eso el modelo Ágil resulta más conveniente para modificar y priorizar funcionalidades durante todo el desarrollo.

---
