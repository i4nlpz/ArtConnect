
# ADR-001 — Arquitectura de monolito modular para ArtConnect

## Estado

Aceptada, 29 de octubre de 2026

## Contexto

ArtConnect es una plataforma web que permite gestionar comisiones artísticas entre clientes y artistas. Los clientes pueden solicitar trabajos, revisar cotizaciones, consultar avances y solicitar modificaciones, mientras que los artistas pueden emitir cotizaciones, actualizar el seguimiento y responder a los cambios solicitados. Actualmente, el sistema lo desarrolla una sola persona, por lo que mantener varios servicios independientes complicaría el desarrollo y mantenimiento.

Las fronteras entre módulos están definidas: **Usuarios, Solicitudes y Cotizaciones, Comisiones y Seguimiento, y Comunicación**. Usuarios administra la información de clientes y artistas. Solicitudes y Cotizaciones gestiona los encargos iniciales y sus condiciones. Comisiones y Seguimiento administra las etapas, avances, modificaciones e historial, mientras que Comunicación permite intercambiar mensajes asociados a las comisiones.

Se consideró utilizar microservicios, pero se descartó porque el proyecto todavía tiene un alcance relativamente pequeño y los requisitos pueden cambiar después de validar el prototipo con los usuarios. Separar los módulos en servicios independientes agregaría complejidad sin resolver una necesidad actual.

## Decisión

Construimos ArtConnect como un **monolito modular**, con una sola aplicación y una base de datos compartida. Los cuatro módulos estarán separados internamente por sus responsabilidades e interfaces, evitando que un módulo acceda directamente a las tablas de otro.

Cuando un módulo necesite información de otro, deberá solicitarla mediante su interfaz. Por ejemplo, Comunicación consultará a Comisiones y Seguimiento para verificar que un usuario participa en la comisión antes de permitir el acceso a sus mensajes.

## Consecuencias

Tendremos un solo despliegue, una sola aplicación que mantener y una base de datos compartida. Esto facilita el desarrollo por una sola persona y permite realizar modificaciones sin coordinar distintos servicios. También ayuda a mantener organizadas las responsabilidades de cada módulo.

Como desventaja, los módulos no podrán escalarse de manera independiente. Si la aplicación presenta una falla general, todas sus funcionalidades podrían verse afectadas, incluyendo las solicitudes, el seguimiento y las conversaciones.

Si en el futuro fuera necesario separar algún módulo, el primer candidato sería **Comunicación**, porque administra los mensajes entre clientes y artistas y tiene una responsabilidad relativamente independiente. La señal para separarlo sería que aumentara considerablemente el volumen de mensajes, que las conversaciones comenzaran a afectar el rendimiento de otras operaciones o que Comunicación necesitara actualizarse y desplegarse con mucha mayor frecuencia que los demás módulos.

El principal riesgo es que se pierda la separación interna cuando un módulo acceda directamente a la información de otro. Por ejemplo, que Comunicación consulte las tablas de Comisiones y Seguimiento en lugar de utilizar su interfaz. Para evitarlo, se revisarán las dependencias entre módulos durante el desarrollo y se mantendrán sus responsabilidades claramente delimitadas.
