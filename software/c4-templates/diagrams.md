# Plantillas de Documentación C4

## 1. C4 Diagrama de Contexto

```dot
// Diagrama C4 de Contexto - Sistema bancario completo
// ***********************************************

 digraph G {
    rankdir=LR;
    node [shape=box, style=filled, fontname="Arial"];

    // Actores externos
    subgraph cluster_exterior {
        label = "Entornos externos";
        style = dashed;
        color = gray;

        Customer [fillcolor=lightblue];
        Bank [fillcolor=lightblue];
        CentralBank [fillcolor=lightblue];
    }

    // Sistema actual
    subgraph cluster_sistema {
        label = "Banca en línea actual";
        style = rounded;
        color = darkgreen;
        fillcolor = lightgreen;

        WebApp [fillcolor=lightgreen];
        ApiGateway [fillcolor=lightgreen];
        AuthService [fillcolor=lightgreen];
        TransactionService [fillcolor=lightgreen];
        AccountService [fillcolor=lightgreen];
        NotificationService [fillcolor=lightgreen];
        Database [fillcolor=lightgreen];
    }

    // Flechas de relación
    Customer -> WebApp [label="Inicia sesión / Transacciona"];
    WebApp -> ApiGateway [label="API REST"];
    Customer -> CentralBank [label="Regulación"];
    Bank -> CentralBank [label="Supervisión"];

    // Conexiones de servicios
    ApiGateway -> AuthService [label="Autenticación"];
    ApiGateway -> TransactionService [label="Transacciones"];
    ApiGateway -> AccountService [label="Cuentas"];
    ApiGateway -> NotificationService [label="Notificaciones"];
    TransactionService -> Database [label="Lectura/Escritura"];
    AccountService -> Database [label="Lectura/Escritura"];
}
```

## 2. Plantilla de Contenedores C4

```dot
// Diagrama de Contenedores C4 - Descomposición del software bancario
// *************************************************************

 digraph G {
    rankdir=LR;
    node [shape=box, style=filled, fontname="Arial"];
    edge [fontname="Arial"];

    // Servicios del lado del cliente
    subgraph cluster_client {
        label = "Cliente WEB/Mobile";
        style = rounded;
        color = blue;

        Frontend [fillcolor=lightyellow];
        MobileApp [fillcolor=lightyellow];
        PWA [fillcolor=lightyellow];
    }

    // API Gateway
    subgraph cluster_infra {
        label = "Infraestructura";
        style = rounded;
        color = orange;

        LoadBalancer [fillcolor=lightcoral];
        ReverseProxy [fillcolor=lightcoral];
        APIProxy [fillcolor=lightcoral];
    }

    // Microservicios backend
    subgraph cluster_backend {
        label = "Servicios backend";
        style = rounded;
        color = purple;
        fillcolor = lavender;

        AuthService [fillcolor=lavender];
        UserService [fillcolor=lavender];
        AccountService [fillcolor=lavender];
        TransactionService [fillcolor=lavender];
        NotificationService [fillcolor=lavender];
        ReportService [fillcolor=lavender];
        RateLimitService [fillcolor=lavender];
    }

    // Almacenamiento de datos
    subgraph cluster_data {
        label = "Datos";
        style = rounded;
        color = teal;

        UserDB [fillcolor=lightpink];
        TransactionDB [fillcolor=lightpink];
        Cache [fillcolor=lightpink];
        S3 [fillcolor=lightpink];
        Redis [fillcolor=lightpink];
        MessageQueue [fillcolor=lightpink];
    }

    // Conexiones de clientes
    Frontend -> LoadBalancer;
    MobileApp -> LoadBalancer;
    PWA -> LoadBalancer;

    // Conexiones de infraestructura
    LoadBalancer -> APIProxy;
    APIProxy -> AuthService;
    APIProxy -> UserService;
    APIProxy -> AccountService;
    APIProxy -> TransactionService;
    APIProxy -> NotificationService;
    APIProxy -> ReportService;
    APIProxy -> RateLimitService;

    // Conexiones de base de datos
    AuthService -> UserDB;
    UserService -> UserDB;
    AccountService -> UserDB;
    TransactionService -> TransactionDB;
    TransactionService -> Cache;
    TransactionService -> MessageQueue;
    NotificationService -> Redis;
    ReportService -> S3;
    ReportService -> Redis;
    RateLimitService -> Redis;
}
```

## 3. Plantilla de Componentes C4

```dot
// Diagrama C4 de Componentes - Descomposición del detalle de servicios
// ******************************************************************

 digraph G {
    rankdir=LR;
    node [shape=box, style=filled, fontname="Arial"];
    edge [fontname="Arial"];

    // Servicio de autenticación detallado
    subgraph cluster_auth {
        label = "AuthService";
        style = rounded;
        color = darkblue;
        fillcolor = lightblue;

        OAuth2Proxy [fillcolor=lightblue];
        TokenValidator [fillcolor=lightblue];
        SessionManager [fillcolor=lightblue];
        PasswordHasher [fillcolor=lightblue];
        JWTGenerator [fillcolor=lightblue];
        RefreshTokenManager [fillcolor=lightblue];
    }

    // Servicio de usuario detallado
    subgraph cluster_user {
        label = "UserService";
        style = rounded;
        color = darkgreen;
        fillcolor = lightgreen;

        UserRepository [fillcolor=lightgreen];
        ProfileService [fillcolor=lightgreen];
        EmailVerifier [fillcolor=lightgreen];
        TwoFAService [fillcolor=lightgreen];
        AuditLogger [fillcolor=lightgreen];
    }

    // Servicio de cuentas detallado
    subgraph cluster_account {
        label = "AccountService";
        style = rounded;
        color = darkred;
        fillcolor = lightcoral;

        AccountRepository [fillcolor=lightcoral];
        BalanceService [fillcolor=lightcoral];
        CustomerVerification [fillcolor=lightcoral];
        AccountLockoutService [fillcolor=lightcoral];
    }

    // Servicio de transacciones detallado
    subgraph cluster_transaction {
        label = "TransactionService";
        style = rounded;
        color = darkorange;
        fillcolor = lightsalmon;

        TransactionRepository [fillcolor=lightsalmon];
        TransactionValidator [fillcolor=lightsalmon];
        FraudDetector [fillcolor=lightsalmon];
        TransactionProcessor [fillcolor=lightsalmon];
        ReconciliationService [fillcolor=lightsalmon];
    }

    // Conexiones entre servicios
    AuthService -> TokenValidator [label="Verificar"];
    AuthService -> JWTGenerator [label="Generar"];
    AuthService -> RefreshTokenManager [label="Gestionar"];

    UserService -> UserRepository [label="CRUD"];
    UserService -> AuditLogger [label="Registrar"];
    UserService -> ProfileService [label="Actualizar"];

    AccountService -> AccountRepository [label="CRUD"];
    AccountService -> BalanceService [label="Consultar"];

    TransactionService -> TransactionRepository [label="CRUD"];
    TransactionService -> FraudDetector [label="Validar"];
    TransactionService -> TransactionProcessor [label="Procesar"];
    TransactionService -> ReconciliationService [label="Reconciliar"];
}
```

## 4. Plantilla de Diagrama de Código C4

```dot
// Diagrama de Dependencias de Código C4 - Implementación técnica
// *************************************************************

 digraph G {
    rankdir=LR;
    node [shape=box, style=filled, fontname="Courier", fontsize=10];
    edge [fontname="Arial"];

    // Java / Spring Boot Services
    subgraph cluster_java {
        label = "Servicios Java";
        style = rounded;
        color = darkblue;
        fillcolor = aliceblue;

        domain [fillcolor=aliceblue];
        service [fillcolor=aliceblue];
        repository [fillcolor=aliceblue];
        config [fillcolor=aliceblue];
        security [fillcolor=aliceblue];
    }

    // Frameworks y dependencias
    subgraph cluster_framework {
        label = "Spring Boot / Frameworks";
        style = rounded;
        color = blue;
        fillcolor = lightcyan;

        spring_boot [fillcolor=lightcyan];
        spring_data_jpa [fillcolor=lightcyan];
        spring_security [fillcolor=lightcyan];
        lombok [fillcolor=lightcyan];
        jackson [fillcolor=lightcyan];
        validation [fillcolor=lightcyan];
    }

    // Tecnologías de base de datos
    subgraph cluster_db {
        label = "Base de datos relacional";
        style = rounded;
        color = green;
        fillcolor = lightyellow;

        h2 [fillcolor=lightyellow];
        postgresql [fillcolor=lightyellow];
        flyway [fillcolor=lightyellow];
        hibernate [fillcolor=lightyellow];
    }

    // Infraestructura cloud
    subgraph cluster_cloud {
        label = "Cloud/AWS";
        style = rounded;
        color = orange;
        fillcolor = moccasin;

        aws_sdk [fillcolor=moccasin];
        aws_s3 [fillcolor=moccasin];
        aws_sqs [fillcolor=moccasin];
        aws_secrets_manager [fillcolor=moccasin];
    }

    // Conexiones entre capas

    // Spring Boot con framework
    spring_boot -> spring_data_jpa [label="Usa"];
    spring_boot -> spring_security [label="Usa"];
    spring_boot -> lombok [label="Usa"];
    spring_boot -> jackson [label="Usa"];
    spring_boot -> validation [label="Usa"];

    // Framework con código
    spring_data_jpa -> repository [label="Interfaz"];
    spring_security -> security [label="Módulo"];

    // Framework con BD
    spring_data_jpa -> hibernate [label="Usa"];
    spring_data_jpa -> postgresql [label="Almacena"];
    hibernate -> h2 [label="Almacena"];
    hibernate -> postgresql [label="Almacena"];
    flyway -> postgresql [label="Migraciones"];

    // Base de datos con AWS
    postgresql -> aws_secrets_manager [label="Credenciales"];
    h2 -> aws_secrets_manager [label="Credenciales"];
    aws_s3 -> h2 [label="Backup"], postgresql [label="Archivar"];
    aws_sqs -> h2 [label="Colas"], postgresql [label="Colas"];

    // Servicios con AWS
    service -> aws_sdk [label="Usa"];
    service -> aws_s3 [label="Archivar"];
    service -> aws_sqs [label="Colas de mensajes"];

    // Repositorio con base de datos
    repository -> hibernate [label="Usa"];
    repository -> postgresql [label="Conecta a"];

    // Config con múltiples
    config -> postgresql [label="Conecta a"];
    config -> h2 [label="Conecta a"];
    config -> aws_secrets_manager [label="Credenciales"];
}
```

## 5. Ejemplo de Patrones de Arquitectura ISO

Las siguientes plantillas demuestran cómo documentar los principios clave de ISO 9001 en formato C4:

### a) Mejora Continua

```dot
// Diagrama C4 de Mejora Continua (ISO 8.5)
// ****************************

digraph G {
    rankdir=TB;
    node [shape=ellipse, style=filled, fontname="Arial"];
    edge [fontname="Arial"];

    Learning [fillcolor=lightyellow];
    Analysis [fillcolor=lightgreen];
    Improvement [fillcolor=lightblue];
    Implementation [fillcolor=lightpink];

    Learning -> Analysis [label="Feedback"];
    Analysis -> Improvement [label="Insighths"];
    Improvement -> Implementation [label="Acciones"];
    Implementation -> Learning [label="Results"];

    // ISO 9001:2015 Clause 8.5
    subgraph cluster_iso {
        label = "ISO 9001:2015";
        style = dashed;
        color = gray;
        footnote = "Cláusula 8.5: Acción correctiva";
    }
}
```

### b) Enfoque basado en procesos

```dot
// Diagrama C4 de Gestión de Procesos (ISO 4.1)
// *******************************

digraph G {
    rankdir=LR;
    node [shape=box, style=filled, fontname="Arial"];
    edge [fontname="Arial"];

    // Gestión de riesgos e oportunidades
    subgraph cluster_risk {
        label = "Planificación de riesgos y oportunidades";
        style = rounded;
        color = red;

        RiskAssessment [fillcolor=lightcoral];
        RiskTreatment [fillcolor=lightcoral];
        RiskMonitoring [fillcolor=lightcoral];
    }

    // Liderazgo y enfoque
    subgraph cluster_leadership {
        label = "Liderazgo y enfoque";
        style = rounded;
        color = blue;

        LeadershipCommitment [fillcolor=lightblue];
        CustomerFocus [fillcolor=lightblue];
        ProcessApproach [fillcolor=lightblue];
    }

    // Mejora del producto
    subgraph cluster_product {
        label = "Mejora del producto";
        style = rounded;
        color = green;

        ProductRequirements [fillcolor=lightgreen];
        QualityObjectives [fillcolor=lightgreen];
        ProductPerformance [fillcolor=lightgreen];
    }

    // ISO 9001:2015 cláusulas relacionadas
    subgraph cluster_iso_clauses {
        label = "ISO 9001:2015";
        style = dashed;
        color = gray;
        footer = "Cláusulas: 5.1, 6.1, 8.5.2, 10.3";
    }
}
```
