## Diagrama de arquitectura

```mermaid
flowchart TB
    CLI([Cliente])
    SEL([Seller])
    ADM([Administrador])
    WEB["<b>Cliente Web</b><br/>Navegador · HTML / CSS / JavaScript"]

    CLI --> WEB
    SEL --> WEB
    ADM --> WEB

    subgraph MONO["«monolito» Marketplace Backend · Node.js 20 LTS · Express<br/>Una sola aplicación · un solo proceso · un solo despliegue"]
        MW["<b>Middlewares Express (transversales)</b><br/>cors · express.json() · auth (JWT) · validación de entrada · manejo de errores · logger"]

        subgraph PRES["1. CAPA DE PRESENTACIÓN<br/>Recibe peticiones HTTP, autentica, valida la entrada y responde JSON"]
            UR["usuarios.routes.js"]
            UC["usuarios.controller.js"]
            SR["sellers.routes.js"]
            SC["sellers.controller.js"]
            CR["catalogo.routes.js"]
            CC["catalogo.controller.js"]
            KR["carrito.routes.js"]
            KC["carrito.controller.js"]
            PR["pedidos.routes.js"]
            PC["pedidos.controller.js"]
        end

        subgraph NEG["2. CAPA DE LÓGICA DE NEGOCIO<br/>Reglas de negocio y coordinación entre módulos"]
            US["<b>usuarios.service.js</b><br/>registro, login, roles"]
            SS["<b>sellers.service.js</b><br/>alta de tiendas, validación"]
            CS["<b>catalogo.service.js</b><br/>productos, categorías, stock"]
            KS["<b>carrito.service.js</b><br/>ítems, totales"]
            PS["<b>pedidos.service.js</b><br/>checkout, estados, pago/envío"]
        end

        subgraph DAT["3. CAPA DE DATOS<br/>Persistencia y consultas a la base de datos"]
            URE["usuarios.repository.js"]
            SRE["sellers.repository.js"]
            CRE["catalogo.repository.js"]
            KRE["carrito.repository.js"]
            PRE["pedidos.repository.js"]
            ORM["<b>Acceso a datos compartido</b><br/>Sequelize (ORM) · modelos · pool de conexiones (src/shared/db)"]
        end
    end

    DB[("<b>PostgreSQL</b><br/>marketplace_db")]
    PAG["«sistema externo»<br/><b>Pasarela de pagos</b><br/>(p. ej. Culqi / Niubiz)"]
    ENV["«sistema externo»<br/><b>Servicio de envíos</b><br/>(API del courier)"]

    WEB -->|"HTTPS · JSON · /api/v1/*"| MW

    MW --> UR
    MW --> SR
    MW --> CR
    MW --> KR
    MW --> PR

    UR --> UC --> US --> URE
    SR --> SC --> SS --> SRE
    CR --> CC --> CS --> CRE
    KR --> KC --> KS --> KRE
    PR --> PC --> PS --> PRE

    URE --> ORM
    SRE --> ORM
    CRE --> ORM
    KRE --> ORM
    PRE --> ORM

    PS -.-> KS
    KS -.-> CS
    CS -.-> SS
    SS -.-> US
    PS -.-> US

    PS -->|"HTTPS / REST"| PAG
    PS -->|"HTTPS / REST"| ENV
    ORM -->|"SQL · TCP 5432"| DB

    linkStyle 29,30,31,32,33 stroke:#38761d,stroke-width:1.5px,stroke-dasharray:4 3

    style MONO fill:#ffffff,stroke:#333,stroke-dasharray:6 4
    style PRES fill:#e4ebf8,stroke:#aebfe0
    style NEG fill:#e3f0dc,stroke:#b5d3a6
    style DAT fill:#fdf0d9,stroke:#e6cf9f

    classDef externo fill:#eeeeee,stroke:#666,color:#000
    classDef presentacion fill:#ffffff,stroke:#3b5b9d,color:#000
    classDef negocio fill:#d3e5c8,stroke:#38761d,color:#000
    classDef datos fill:#ffffff,stroke:#bf9000,color:#000
    classDef orm fill:#fde4bb,stroke:#bf9000,color:#000
    classDef transversal fill:#dbe5f8,stroke:#3b5b9d,color:#000

    class PAG,ENV externo
    class UR,UC,SR,SC,CR,CC,KR,KC,PR,PC presentacion
    class US,SS,CS,KS,PS negocio
    class URE,SRE,CRE,KRE,PRE datos
    class ORM orm
    class MW transversal
```


# Estilo arquitectónico

**Estilo seleccionado:** Monolito modular con arquitectura en capas.

Todo el backend se ejecuta como una sola aplicación (un solo proceso y un solo despliegue), organizada en módulos independientes y en tres capas: presentación, lógica de negocio y datos. Esta decisión responde a los drivers DA01 (Escalabilidad) y DA06 (Mantenibilidad), y está registrada en ADR-001.





## Reglas de la arquitectura

1. Cada capa solo invoca a la capa inmediatamente inferior.
2. Un módulo no accede al repository ni a las tablas de otro módulo.
3. La comunicación entre módulos se hace llamando a su service.
4. Todo se ejecuta en un único proceso Node.js con una única base de datos.