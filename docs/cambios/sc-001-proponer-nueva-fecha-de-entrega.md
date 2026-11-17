# SC-001: El artista puede proponer una nueva fecha de entrega

> Solicitud de cambio · Ingeniería de Software I · SIS3407
> Repositorio: `docs/cambios/sc-001-proponer-nueva-fecha-de-entrega.md`
---

## Estado

Propuesta · 15/11/2026

## Quién la pide

Jorge Eduardo García Hernández, como dupla de revisión (entrevistado del proyecto).

## Qué se pide

"A veces junto varios encargos y no me alcanza el tiempo para entregar uno en la fecha que acordé. Hoy le escribo al cliente para pedirle más días y lo que quedamos solo queda en el chat. Quiero poder proponerle desde ArtConnect una nueva fecha de entrega, explicar el motivo, y que el cliente pueda aceptarla o rechazarla, como pasa cuando es él quien pide un cambio."

## Por qué

En la entrevista expliqué que, cuando un trabajo no se puede entregar en la fecha prevista, lo único que hago es avisarle al cliente por mensaje y acordar una fecha nueva; no existe un procedimiento definido.

ArtConnect busca que los acuerdos (precio, condiciones y fechas) queden en un solo lugar, pero hoy solo contempla los cambios que pide el cliente. Los retrasos nacen del lado del artista, así que justo ese cambio de fecha seguiría acordándose fuera del sistema, y la fecha registrada podría dejar de ser la real.

## Qué pasa si no se hace

Los cambios de fecha por retraso seguirían acordándose por chat. En esos casos ArtConnect mostraría una fecha de entrega distinta a la realmente acordada, y el historial de la comisión quedaría incompleto justamente cuando más podría hacer falta para aclarar un desacuerdo.

No impide usar el sistema para todo lo demás, así que no es grave en el día a día. El costo es de confianza en el registro.

## Tipo de mantenimiento

- [ ] **Correctivo** · algo está mal y hay que repararlo
- [ ] **Adaptativo** · el entorno cambió y hay que ajustarse
- [x] **Perfectivo** · funciona, pero puede ser mejor
- [ ] **Preventivo** · todavía no falla, pero va a fallar

**Justificación:** ArtConnect ya maneja bien los cambios que pide el cliente; este cambio lo mejora cubriendo el que nace del artista.

## Criterio de aceptación

1. Un artista puede proponer una nueva fecha de entrega en una comisión que está en curso, y no puede enviar la propuesta sin explicar el motivo.
2. El cliente de esa comisión ve la fecha vigente, la fecha propuesta y el motivo, y puede aceptarla o rechazarla.
3. Si el cliente la acepta, la fecha de entrega de la comisión pasa a ser la propuesta y la fecha anterior sigue consultable.
4. Si el cliente la rechaza, la fecha de entrega no cambia.
5. En el historial de la comisión aparecen la propuesta, el motivo y la decisión del cliente, en orden cronológico y con la fecha en que ocurrió cada uno.
6. No se puede proponer una nueva fecha en una comisión que ya no está en curso.
7. Una persona que no participa en esa comisión no puede ver ni responder la propuesta.

## Prioridad que sugiere el solicitante

**Media.** Según mi experiencia esta situación ocurre a veces y no con todos los encargos, y el sistema sigue sirviendo sin ella. Pero afecta directamente la promesa de ArtConnect de tener los acuerdos en un solo lugar, por eso no la dejaría en baja.

---

*La solicitud describe qué se quiere, nunca cómo hacerlo. El cómo se decide en el análisis de impacto, y lo decide quien conoce el diseño.*
