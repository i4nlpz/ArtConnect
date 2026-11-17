# Diagramas de mi sistema - ArtConnect

## 1. Diagrama de Contexto

```mermaid
flowchart TB
    cliente([Cliente])
    artista([Artista])
    archivos[["Servicio de almacenamiento<br/>de archivos<br/>[sistema externo]"]]

    sistema["ArtConnect<br/>Sistema de gestión de<br/>comisiones artísticas"]

    cliente -->|"solicita comisiones, revisa cotizaciones,<br/>consulta avances, solicita modificaciones y se<br/>comunica con el artista"| sistema
    artista -->|"recibe solicitudes, emite cotizaciones,<br/>publica avances, responde modificaciones y<br/>se comunica con el cliente"| sistema

    sistema -->|"guarda referencias y avances"| archivos
    archivos -->|"entrega los archivos cuando<br/>se consultan"| sistema

    style archivos stroke-dasharray: 5 5
```

---

## 2. Diagrama de Contenedores

```mermaid
flowchart TB
    cliente([Cliente])
    artista([Artista])
    storage[["Servicio de almacenamiento<br/>de archivos<br/>[sistema externo]"]]

    subgraph artconnect["ArtConnect"]
        web["App web<br/>[React · navegador en<br/>celular o computadora]"]
        server["Servidor ArtConnect<br/>[Node.js · monolito<br/>modular]"]
        db[("Base de datos<br/>[PostgreSQL]")]

        web -->|"HTTPS / JSON"| server
        server -->|"lee y escribe (SQL)"| db
    end

    cliente -->|"usa"| web
    artista -->|"usa"| web
    server -->|"guarda y recupera archivos<br/>(HTTPS / API del servicio)"| storage

    style storage stroke-dasharray: 5 5
```

---

## 3. Diagrama de Componentes

```mermaid
flowchart TB
    web[App web]

    subgraph servidor["Servidor ArtConnect · monolito modular"]
        comunicacion["Comunicación<br/>mensajes de cada comisión"]
        comisiones["Comisiones y Seguimiento<br/>etapas, avances,<br/>modificaciones e historial"]
        solicitudes["Solicitudes y Cotizaciones<br/>solicitudes, cotizaciones y<br/>su decisión"]
        usuarios["Usuarios<br/>identidad y roles de clientes<br/>y artistas"]

        comunicacion -->|"verifica que participa en la<br/>comisión"| comisiones
        comisiones -->|"consulta la cotización<br/>aceptada"| solicitudes
        comisiones -->|"consulta a los participantes"| usuarios
        solicitudes -->|"consulta al cliente y al<br/>artista"| usuarios
    end

    db[(Base de datos)]

    web -->|"busca artistas por nombre"| usuarios
    web -->|"registra solicitudes y<br/>cotizaciones"| solicitudes
    web -->|"consulta y actualiza el<br/>seguimiento"| comisiones
    web -->|"envía y lee mensajes"| comunicacion

    servidor -->|"cada módulo usa solo sus<br/>propias tablas"| db
```

---

## 4. Diagrama de Clases

```mermaid
classDiagram
direction LR

class Usuario {
    -id: int
    -nombre: String
    -correo: String
    -roles: List~String~
    +crearSolicitud(solicitud: Solicitud) Solicitud
    +emitirCotizacion(solicitud: Solicitud, cotizacion: Cotizacion) void
    +enviarMensaje(comision: Comision, contenido: String) Mensaje
}

class Solicitud {
    -id: int
    -descripcion: String
    -estilo: String
    -cantidadElementos: int
    -nivelDetalle: String
    -referencias: String
    -fechaDeseada: Date
    -estado: String
    +registrar(descripcion: String, estilo: String, cantidad: int, nivelDetalle: String, referencias: String, artista: Usuario) void
    +actualizarEstado(nuevoEstado: String) void
    +validarDatosObligatorios() List~String~
}

class Cotizacion {
    -id: int
    -precio: Decimal
    -condiciones: String
    -fechaEntregaEstimada: Date
    -estado: String
    -comentarioAjuste: String
    +registrar(precio: Decimal, condiciones: String, fechaEntrega: Date) void
    +solicitarAjuste(comentario: String) void
    +registrarDecision(decision: String) void
}

class Comision {
    -id: int
    -fechaInicio: Date
    -estado: String
    -etapaActual: String
    +actualizarEtapa(nuevaEtapa: String) void
    +registrarAvance(avance: Avance) void
    +consultarHistorial() List~String~
}

class CondicionesTrabajo {
    -id: int
    -version: int
    -precio: Decimal
    -alcance: String
    -fechaEntrega: Date
    -fechaAcuerdo: Date
    -vigente: Boolean
    +crearVersion(precio: Decimal, alcance: String, fechaEntrega: Date) CondicionesTrabajo
    +marcarVigencia(vigente: Boolean) void
}

class Modificacion {
    -id: int
    -descripcion: String
    -fechaSolicitud: Date
    -estado: String
    -afectaPrecio: Boolean
    -afectaAlcance: Boolean
    -afectaFechaEntrega: Boolean
    +registrarSolicitud(descripcion: String) void
    +proponerCondiciones(condiciones: CondicionesTrabajo) void
    +registrarDecision(aceptada: Boolean) void
}

class Avance {
    -id: int
    -descripcion: String
    -etapa: String
    -fechaRegistro: Date
    +registrar(descripcion: String, etapa: String) void
}

class Mensaje {
    -id: int
    -contenido: String
    -fechaEnvio: Date
    -leido: Boolean
    +enviar(contenido: String) void
    +marcarComoLeido() void
}

Usuario "1" -- "0..*" Solicitud : registra como cliente
Usuario "1" -- "0..*" Cotizacion : emite como artista
Usuario "1" -- "0..*" Solicitud : recibe como artista
Solicitud "1" -- "0..1" Cotizacion : recibe
Cotizacion "1" -- "0..1" Comision : origina al aceptarse
Usuario "2" -- "0..*" Comision : participa como cliente y artista
Comision "1" *-- "0..*" Modificacion : contiene
Comision "1" *-- "0..*" Avance : contiene
Comision "1" *-- "0..*" Mensaje : contiene
Comision "1" *-- "1..*" CondicionesTrabajo : conserva versiones
Modificacion "0..1" -- "0..1" CondicionesTrabajo : puede proponer
```

---

## 5. Diagrama de Secuencia

```mermaid
sequenceDiagram
    actor Cliente
    participant web as App web
    participant sol as solicitud: Solicitud

    Cliente->>web: envía la solicitud
    activate web
    web->>sol: registrar(descripcion, estilo, cantidad,<br/>nivelDetalle, referencias, artista)
    activate sol

    sol->>sol: validarDatosObligatorios()

    alt datos completos
        sol-->>web: ok
        web-->>Cliente: solicitud registrada
    else faltan datos obligatorios
        sol-->>web: faltantes (datos sin llenar)
        web-->>Cliente: indica los datos que faltan
    end

    deactivate sol
    deactivate web
```

---

## 6. Diagrama de Estados

```mermaid
stateDiagram-v2
    direction LR
    [*] --> Emitida : registrar / asocia la cotización a la solicitud
    Emitida --> AjusteSolicitado : solicitarAjuste / guarda el comentario de ajuste
    AjusteSolicitado --> Emitida : registrar / actualiza precio, condiciones y fecha
    Emitida --> Aceptada : registrarDecision [decisión = aceptada y tiene condiciones] / origina la Comisión
    Emitida --> Rechazada : registrarDecision [decisión = rechazada]
    Aceptada --> [*]
    Rechazada --> [*]
```
