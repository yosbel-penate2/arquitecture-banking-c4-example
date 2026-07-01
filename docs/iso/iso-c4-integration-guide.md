# Integración ISO-C4: Guía de Implementación

## Conceptos Clave

### 1. Enfoque basado en procesos de ISO con Documentación C4

ISO 9001 enfatiza la importancia de los procesos documentados, medibles y controlados. La notación C4 complementa esto visualizando los procesos y sus interrelaciones.

**Enfoque Basado en Procesos (ISO 4.1)**

| Elemento ISO | Representación C4 | Descripción |
|---------------|-------------------|-------------|
| Proceso definido | Contenedor / Componente | Visualiza procesos principales como contenedores o componentes estructurados |
| Entradas y salidas | Flechas de relaciones | Muestra el flujo de materias primas a productos terminados |
| Personas responsables | Pedidos de acceso | Indica quién interactúa con cada proceso |
| Métricas de proceso | Etiquetas/Atributos | Mide el rendimiento de cada proceso |

**Ejemplo: Mejora Continua (ISO 8.5)**

```dot
// Diagrama C4 para Mejora Continua - ISO 8.5
// ******************************************

digraph G {
    rankdir=TB;
    node [shape=ellipse, style=filled, fontname="Arial"];
    edge [fontname="Arial"];

    // Planificación y diseño (ISO 5.1)
    subgraph cluster_planificacion {
        label = "Planificación";
        style = rounded;
        color = #FFD700;
        PlanificacionDeCalidad [fillcolor=lightyellow];
        DefinicionDelAlcance [fillcolor=lightyellow];
        PlanificacionDeRiesgos [fillcolor=lightyellow];
    }

    // Implementación (ISO 7.1)
    subgraph cluster_implementacion {
        label = "Implementación";
        style = rounded;
        color = #90EE90;
        EstablecimientoDeProcesos [fillcolor=lightgreen];
        EntrenamientoDelPersonal [fillcolor=lightgreen];
        EstablecimientoDeInfraestructura [fillcolor=lightgreen];
    }

    // Monitoreo y medición (ISO 8.1)
    subgraph cluster_monitoreo {
        label = "Monitoreo";
        style = rounded;
        color = #ADD8E6;
        SeguimientoDeProcesos [fillcolor=lightblue];
        MedicionDeIndicadores [fillcolor=lightblue];
        AuditoriasDelSistema [fillcolor=lightblue];
    }

    // Revisión por parte de la dirección (ISO 9.1)
    subgraph cluster_revision {
        label = "Revisión por parte de la dirección";
        style = rounded;
        color = #FFB6C1;
        RevisionPeriodica [fillcolor=lightpink];
        EvaluacionDeLaEficacia [fillcolor=lightpink];
        RequisitosLegales [fillcolor=lightpink];
    }

    // Acción correctiva (ISO 8.5)
    subgraph cluster_accion {
        label = "Acción Correctiva";
        style = rounded;
        color = #FFA07A;
        IdentificacionDeNoConformidades [fillcolor=salmon];
        AnalisisDeLaInformacion [fillcolor=salmon];
        RealizacionDeAcciones [fillcolor=salmon];
        VerificacionDeLaEficacia [fillcolor=salmon];
    }

    // Flujo de mejora continua
    PlanificacionDeCalidad -> EstablecimientoDeProcesos;
    EstablecimientoDeProcesos -> SeguimientoDeProcesos;
    SeguimientoDeProcesos -> MedicionDeIndicadores;
    MedicionDeIndicadores -> AuditoriasDelSistema;
    AuditoriasDelSistema -> RevisionPeriodica;
    RevisionPeriodica -> EvaluacionDeLaEficacia;
    EvaluacionDeLaEficacia -> IdentificacionDeNoConformidades;
    IdentificacionDeNoConformidades -> AnalisisDeLaInformacion;
    AnalisisDeLaInformacion -> RealizacionDeAcciones;
    RealizacionDeAcciones -> VerificacionDeLaEficacia;
    VerificacionDeLaEficacia -> EstablecimientoDeProcesos;

    // ISO 9001:2015 Cláusulas integradas
    subgraph cluster_iso {
        label = "ISO 9001:2015";
        style = dashed;
        color = gray;
        footer = "Cláusulas: 5.1, 6.1, 8.1, 8.2, 8.5, 9.1, 10.3";
    }
}
```

### 2. Gestión de Riesgos e Imprevistos - ISO 6.1 con C4

ISO 6.1 requiere la planificación de riesgos e imprevistos. Los diagramas C4 pueden visualizar los diferentes tipos de riesgos y su tratamiento.

```dot
// Diagrama C4 de Gestión de Riesgos - ISO 6.1
// ****************************************

digraph G {
    rankdir=LR;
    node [shape=box, style=filled, fontname="Arial"];
    edge [fontname="Arial"];

    // Riesgos identificados
    subgraph cluster_riesgos {
        label = "Riesgos Identificados";
        style = rounded;
        color = darkred;

        Risk_Business [fillcolor=crimson, label="Riesgos de negocio\n(ISO 5.1)"];
        Risk_Operational [fillcolor=firebrick, label="Riesgos operativos\n(ISO 8.1)"];
        Risk_Technical [fillcolor=darkred, label="Riesgos técnicos\n(ISO 7.1)"];
        Risk_Regulatory [fillcolor=maroon, label="Riesgos regulatorios\n(ISO 5.3)"];
        Risk_Security [fillcolor=indianred, label="Riesgos de seguridad\n(ISO 8.2)"];
    }

    // Evaluación de riesgos
    subgraph cluster_evaluation {
        label = "Evaluación de Riesgos";
        style = rounded;
        color = blue;

        Risk_Identification [fillcolor=lightcoral];
        Risk_Analysis [fillcolor=lightblue];
        Risk_Evaluation [fillcolor=lightskyblue];
        Risk_Prioritization [fillcolor=powderblue];
    }

    // Tratamiento de riesgos
    subgraph cluster_treatment {
        label = "Tratamiento de Riesgos (ISO 6.1.2)";
        style = rounded;
        color = orange;

        Risk_Acceptance [fillcolor=lightyellow, label="Aceptar (6.1.2.3)"];
        Risk_Avoidance [fillcolor=lightgoldenrodyellow, label="Evitar (6.1.2.1)"];
        Risk_Mitigation [fillcolor=lightgreen, label="Mitigar (6.1.2.2)"];
        Risk_Sharing [fillcolor=pink, label="Compartir (6.1.2.4)"];
    }

    // Riesgos monitoreados
    subgraph cluster_monitoring {
        label = "Supervisión";
        style = rounded;
        color = purple;

        Risk_Monitoring [fillcolor=lavender];
        Risk_Review [fillcolor=thistle];
        Risk_Update [fillcolor=plum];
    }

    // Conexiones
    Risk_Identification -> Risk_Analysis;
    Risk_Analysis -> Risk_Evaluation;
    Risk_Evaluation -> Risk_Prioritization;
    Risk_Prioritization -> Risk_Acceptance;
    Risk_Prioritization -> Risk_Avoidance;
    Risk_Prioritization -> Risk_Mitigation;
    Risk_Prioritization -> Risk_Sharing;

    Risk_Acceptance -> Risk_Monitoring;
    Risk_Avoidance -> Risk_Monitoring;
    Risk_Mitigation -> Risk_Monitoring;
    Risk_Sharing -> Risk_Monitoring;

    Risk_Monitoring -> Risk_Review;
    Risk_Review -> Risk_Update;
    Risk_Update -> Risk_Identification;

    // Riesgos emergentes
    subgraph cluster_emerging {
        label = "Riesgos Emergentes";
        style = rounded;
        color = black;
        fillcolor = #F0F0F0;
        label = "Riesgos emergentes";
        Risk_New [fillcolor=gainsboro];
    }

    Risk_Update -> Risk_New;

    // Referencias ISO
    subgraph cluster_iso {
        label = "ISO 9001:2015";
        style = dashed;
        color = gray;
        footer = "Cláusula principal: 6.1 Planificación de riesgos e imprevistos";
    }
}
```

### 3. Enfoque de Documentación C4 para ISO 9.1 (Liderazgo)

ISO 9.1 enfatiza el compromiso de la dirección y una orientación basada en procesos. Los diagramas C4 pueden visualiza estos elementos clave.

```dot
// Diagrama C4 C4 de Compromiso de la Dirección - ISO 9.1
// ************************************************

digraph G {
    rankdir=TB;
    node [shape=box, style=filled, fontname="Arial"];
    edge [fontname="Arial"];

    // Liderazgo y compromiso
    subgraph cluster_liderazgo {
        label = "Liderazgo y Compromiso";
        style = rounded;
        color = #FFD700;
        Commitment_of_top_management [fillcolor=gold];
        Leadership_engagement [fillcolor=goldenrod];
        Policy_documentation [fillcolor=orange];
    }

    // Orientación basada en procesos
    subgraph cluster_procesos {
        label = "Enfoque Basado en Procesos";
        style = rounded;
        color = #90EE90;
        Process_approach [fillcolor=lightgreen];
        Knowledge_of_the_organization [fillcolor=lemonchiffon];
        Process_management [fillcolor=green];
    }

    // Interacción con partes interesadas
    subgraph cluster_partes_interesadas {
        label = "Partes Interesadas";
        style = rounded;
        color = #ADD8E6;
        Customer_focus [fillcolor=lightblue];
        Supplier_relationships [fillcolor=powderblue];
        Employee_involvement [fillcolor=lightskyblue];
        Community_involvement [fillcolor=aliceblue];
    }

    // Resultados organizacionales
    subgraph cluster_resultados {
        label = "Resultados Organizacionales";
        style = rounded;
        color = #FFB6C1;
        Improvement [fillcolor=lightpink];
        Effectiveness [fillcolor=palevioletred];
        Quality_performance [fillcolor=lightcoral];
        Environomic_performance [fillcolor=indianred];
    }

    // Conexiones
    Commitment_of_top_management -> Process_approach;
    Leadership_engagement -> Process_management;
    Policy_documentation -> Knowledge_of_the_organization;

    Process_approach -> Customer_focus;
    Process_approach -> Employee_involvement;
    Process_approach -> Supplier_relationships;
    Process_approach -> Community_involvement;

    Customer_focus -> Improvement;
    Employee_involvement -> Effectiveness;
    Supplier_relationships -> Quality_performance;
    Community_involvement -> Environomic_performance;

    Improvement -> Process_management;
    Improvement -> Process_approach;

    // Referencias ISO
    subgraph cluster_iso {
        label = "ISO 9001:2015";
        style = dashed;
        color = gray;
        footer = "Cláusulas: 5.1, 5.2, 5.3, 9.1, 9.2, 10.2";
    }
}
```

### 4. Control de Documentos y Datos ISO con C4

ISO 8.3 enfatiza el control de documentos y datos. Los diagramas C4 pueden visualizar los flujos de documentos y su control de versiones.

```dot
// Diagrama C4 para Control de Documentos - ISO 8.3
// ******************************************

digraph G {
    rankdir=LR;
    node [shape=box, style=filled, fontname="Arial"];
    edge [fontname="Arial"];

    // Creación de documentos
    subgraph cluster_creation {
        label = "Creación"; 
        style = rounded;
        color = #87CEEB;
        Document_creation [fillcolor=skyblue];
        Version_control [fillcolor=lightskyblue];
        Content_approval [fillcolor=lightsteelblue];
    }

    // Distribución de documentos
    subgraph cluster_distribution {
        label = "Distribución"; 
        style = rounded;
        color = #98FB98;
        Document_distribution [fillcolor=lightgreen];
        Access_controls [fillcolor=palegreen];
        User_authentication [fillcolor=chartreuse];
    }

    // Uso de documentos
    subgraph cluster_usage {
        label = "Uso"; 
        style = rounded;
        color = #FFB6C1;
        Document_usage [fillcolor=lightpink];
        Usage_tracking [fillcolor=palevioletred];
        Compliance_checking [fillcolor=mediumvioletred];
    }

    // Control y mantenimiento
    subgraph cluster_control {
        label = "Control y Mantenimiento"; 
        style = rounded;
        color = #FFA07A;
        Document_revision [fillcolor=salmon];
        Archive_management [fillcolor=lightsalmon];
        Retention_schedule [fillcolor=orange];
    }

    // Eliminación de documentos
    subgraph cluster_disposition {
        label = "Disposición"; 
        style = rounded;
        color = #D3D3D3;
        Document_deletion [fillcolor=lightgray];
        Disposal_audit [fillcolor= Gainsboro];
        Compliance_deletion [fillcolor= #C0C0C0];
    }

    // Conexiones
    Document_creation -> Version_control;
    Document_creation -> Content_approval;
    Document_creation -> Document_distribution;
    Version_control -> Access_controls;
    Version_control -> Document_usage;

    Document_distribution -> Document_usage;
    Access_controls -> Document_usage;
    User_authentication -> Document_usage;

    Document_usage -> Document_revision;
    Document_usage -> Compliance_checking;
    Usage_tracking -> Document_revision;

    Document_revision -> Archive_management;
    Document_revision -> Retention_schedule;

    Compliance_checking -> Document_deletion;
    Disposal_audit -> Document_deletion;
    Compliance_deletion -> Document_deletion;

    Archive_management -> Document_deletion;

    // Referencias ISO
    subgraph cluster_iso {
        label = "ISO 9001:2015";
        style = dashed;
        color = gray;
        footer = "Cláusula principal: 8.3 Control de documentos y datos";
    }
}
```

### 5. Uso Práctico para Ejemplo de Sistema Bancario

El siguiente ejemplo muestra cómo integrar los principios de ISO 9001 con la documentación C4 para un sistema bancario.

```dot
// Diagrama C4 Integrado ISO-C4 para Sistema Bancario
// **************************************************

digraph G {
    rankdir=TB;
    node [shape=box, style=filled, fontname="Arial"];
    edge [fontname="Arial"];

    // Liderazgo y compromiso (ISO 5.1)
    subgraph cluster_leadership {
        label = "Compromiso de Liderazgo";
        style = rounded;
        color = #FFD700;
        Managing_director [fillcolor=gold];
        Chief_risk_officer [fillcolor=goldenrod];
        Compliance_officer [fillcolor=orange];
    }

    // Planificación de riesgos e imprevistos (ISO 6.1)
    subgraph cluster_risk {
        label = "Riesgo e Imprevistos (ISO 6.1)";
        style = rounded;
        color = #FF6B6B;
        Risk_assessment [fillcolor=firebrick];
        Risk_mitigation [fillcolor=darkred];
        Business_continuity [fillcolor=indianred];
    }

    // Enfoque basado en procesos (ISO 4.1)
    subgraph cluster_process {
        label = "Enfoque Basado en Procesos (ISO 4.1)";
        style = rounded;
        color = #4ECDC4;
        Customer_onboarding [fillcolor=lightseagreen];
        Account_management [fillcolor=mediumturquoise];
        Transaction_processing [fillcolor=lightblue];
        Compliance_monitoring [fillcolor=skyblue];
    }

    // Servicio al cliente (ISO 8.2)
    subgraph cluster_customer {
        label = "Servicio al Cliente (ISO 8.2)";
        style = rounded;
        color = #45B7D1;
        Customer_service [fillcolor=lightcyan];
        Complaint_handling [fillcolor=lightblue];
        Feedback_collection [fillcolor=azure];
    }

    // Mejora continua (ISO 10.3)
    subgraph cluster_improvement {
        label = "Mejora Continua (ISO 10.3)";
        style = rounded;
        color = #96CEB4;
        Performance_review [fillcolor=lightgreen];
        Process_optimization [fillcolor=darkgreen];
        Continuous_improvement [fillcolor=olive];
    }

    // Auditoría del sistema de calidad (ISO 9.2)
    subgraph cluster_audit {
        label = "Auditoría del Sistema (ISO 9.2)";
        style = rounded;
        color = #FFEAA7;
        Internal_audit [fillcolor=lemonchiffon];
        External_audit [fillcolor=lightgoldenrodyellow];
        Management_review [fillcolor= wheat];
    }

    // Flujos
    Managing_director -> Risk_assessment;
    Managing_director -> Risk_mitigation;
    Managing_director -> Business_continuity;

    Chief_risk_officer -> Compliance_officer;

    Compliance_officer -> Customer_onboarding;
    Compliance_officer -> Compliance_monitoring;

    Customer_onboarding -> Account_management;
    Account_management -> Transaction_processing;

    Customer_service -> Complaint_handling;
    Customer_service -> Feedback_collection;

    Feedback_collection -> Performance_review;
    Performance_review -> Process_optimization;

    Internal_audit -> Compliance_monitoring;
    Internal_audit -> Customer_service;
    Internal_audit -> Continuous_improvement;

    External_audit -> Management_review;
    Management_review -> Risk_assessment;
    Management_review -> Performance_review;

    // Patrones ISO-C4
    subgraph cluster_iso_patterns {
        label = "Patrones ISO-C4";
        style = dashed;
        color = #A8E6CF;
        footer = "Cláusulas cubiertas: 4.1, 5.1, 5.2, 6.1, 8.2, 9.1, 9.2, 10.3";
    }
}
```

### 6. Guía de Implementación ISO-C4

#### Fases de Implementación

1. **Fase 1: Planeación e Identificación (ISO 4.1, 6.1)**
   - Documentar el alcance organizacional
   - Identificar procesos y partes interesadas clave
   - Realizar planeación de riesgos e imprevistos

2. **Fase 2: Diseño y Documentación (ISO 4.1, 8.3)**
   - Crear diagramas C4 de Contexto
   - Diseñar diagramas C4 de Contenedores
   - Detallar componentes C4

3. **Fase 3: Implementación y Ejecución (ISO 8.1, 8.2)**
   - Establecer procesos de control
   - Implementar métricas de seguimiento
   - Documentar controles de datos

4. **Fase 4: Revisión y Mejora (ISO 9.1, 9.2, 10.3)**
   - Realizar auditorías internas y externas
   - Revisar el desempeño del sistema
   - Planificar acciones correctivas

#### Caminos de Auditoría ISO con C4

```dot
// Camino de Auditoría ISO con C4
// ****************************

digraph G {
    rankdir=LR;
    node [shape=box, style=filled, fontname="Arial"];
    edge [fontname="Arial"];

    // Inicio de la auditoría
    subgraph cluster_auditoria {
        label = "Planificación de la Auditoría";
        style = rounded;
        color = #FFB6C1;
        Audit_scope [fillcolor=lightpink];
        Audit_objectives [fillcolor=palevioletred];
        Auditor_assignment [fillcolor=mediumvioletred];
    }

    // Recolección de evidencia (ISO 9.2)
    subgraph cluster_evidencia {
        label = "Recolección de Evidencia (ISO 9.2)";
        style = rounded;
        color = #87CEEB;
        Document_review [fillcolor=skyblue];
        Process_observation [fillcolor=lightblue];
        Interview_records [fillcolor=lightskyblue];
        Test_results [fillcolor=azure];
    }

    // Revisión de cumplimiento (ISO 8.2)
    subgraph cluster_revision {
        label = "Revisión de Cumplimiento (ISO 8.2)";
        style = rounded;
        color = #98FB98;
        Requirement_matching [fillcolor=lightgreen];
        Nonconformity_identification [fillcolor=darkgreen];
        Performance_evaluation [fillcolor=olive];
    }

    // Reporte de hallazgos (ISO 8.5)
    subgraph cluster_report {
        label = "Reportar Hallazgos (ISO 8.5)";
        style = rounded;
        color = #FFD700;
        Audit_findings [fillcolor=gold];
        Nonconformity_report [fillcolor=goldenrod];
        Audit_conclusion [fillcolor=orange];
    }

    // Acciones correctivas (ISO 8.5)
    subgraph cluster_corrective {
        label = "Acciones Correctivas (ISO 8.5)";
        style = rounded;
        color = #FFA07A;
        Corrective_action [fillcolor=salmon];
        Effectiveness_verification [fillcolor=lightsalmon];
        Management_review [fillcolor=orange];
    }

    // Enriquecimiento del sistema (ISO 10.3)
    subgraph cluster_enrichment {
        label = "Enriquecimiento del Sistema (ISO 10.3)";
        style = rounded;
        color = #A8E6CF;
        Process_update [fillcolor=lightgreen];
        Documentation_update [fillcolor=darkgreen];
        Competence_enhancement [fillcolor=olive];
    }

    // Conexiones
    Audit_scope -> Document_review;
    Document_review -> Requirement_matching;
    Requirement_matching -> Nonconformity_identification;
    Nonconformity_identification -> Nonconformity_report;
    Requirement_matching -> Test_results;
    Requirement_matching -> Interview_records;
    Nonconformity_identification -> Corrective_action;
    Process_observation -> Performance_evaluation;
    Process_observation -> Nonconformity_identification;

    Corrective_action -> Effectiveness_verification;
    Effectiveness_verification -> Audit_findings;
    Effectiveness_verification -> Management_review;

    Nonconformity_report -> Management_review;
    Management_review -> Audit_conclusion;
    Management_review -> Process_update;
    Audit_conclusion -> Audit_findings;

    Management_review -> Documentation_update;
    Management_review -> Competence_enhancement;

    Effectiveness_verification -> Process_update;
    Process_update -> Requirement_matching;
    Process_update -> Effectiveness_verification;

    Documentation_update -> Document_review;
    Competence_enhancement -> Process_optimization;
    Competence_enhancement -> Process_observation;

    // Patrones ISO
    subgraph cluster_iso {
        label = "ISO 9001:2015";
        style = dashed;
        color = gray;
        footer = "Cláusulas: 9.1, 9.2, 8.2, 8.5, 10.3";
    }
}
```

### 7. Diseño de Repositorio para Plantillas ISO-C4

La siguiente estructura de repositorio demuestra cómo organizar las plantillas y documentación para un programa de arquitectura ISO-C4 efectivo.

```
D:/Projects/arquitecture-banking-c4-example/
├── README.md                          # Descripción general
├── docs/                              # Documentación ISO
│   ├── iso/                          # Documentación ISO
│   │   ├── compliance-templates.md    # Plantillas ISO 9001
│   │   └── compliance-planification.md # Planificación y control de riesgos
│   └── diagrams/                     # Diagramas C4
│       ├── context-diagrams/         # Diagramas C4 de Contexto
│       ├── container-diagrams/       # Diagramas C4 de Contenedores
│       └── component-diagrams/       # Diagramas C4 de Componentes
│           ├── auth-system/          # Ejemplos de diagramas C4 de autenticación
│           ├── user-system/          # Ejemplos de diagramas C4 de usuario
│           └── transaction-system/   # Ejemplos de diagramas C4 de transacciones
├── software/                         # Plantillas C4
│   ├── c4-templates/                # Plantillas de C4
│   │   ├── introduction.md           # Introducción al Modelo C4
│   │   ├── diagrams.md               # Plantillas completas de C4 (4 niveles)
│   │   └── iso-integration.md       # Guía de integración ISO-C4
│   └── examples/                    # Ejemplos prácticos
│       └── banking-c4/              # Ejemplo bancario con C4 completo
└── tests/                           # Pruebas de calidad ISO
    └── integration-tests/           # Pruebas de integración ISO-C4
```

### 8. Agregar Archivos de Diagramas Listos para Graphviz

El siguiente archivo `.dot` puede ser convertido directamente por Graphviz para generar imágenes.

```markdown
# Diagrama C4 Integrado ISO-C4 para Sistema Empresarial

```dot
// Diagrama Integrado ISO-C4: Sistema Empresarial Completo
// *****************************************************

digraph G {
    rankdir=TB;
    node [shape=box, style=filled, fontname="Arial"];
    edge [fontname="Arial"];

    // ISO 9001:2015 Clausura 5.1 - Liderazgo y compromiso
    subgraph cluster_iso_leadership {
        label = "ISO 5.1: Liderazgo y Compromiso";
        style = rounded;
        color = #FFD700;

        CEO [fillcolor=gold, label="Gerente General\n5.1.1 Compromiso"];
        Quality_manager [fillcolor=goldenrod, label="Gerente de Calidad\n5.1.2 Enfoque basado en procesos"];
    }

    // ISO 9001:2015 Clausura 6.1 - Planificación de riesgos e imprevistos
    subgraph cluster_iso_risk {
        label = "ISO 6.1: Riesgo e Imprevistos";
        style = rounded;
        color = #FF6B6B;

        Risk_manager [fillcolor=firebrick, label="Gerente de Riesgos\n6.1.1 Enfoque basado en riesgos"];
        Risk_assessment_tool [fillcolor=darkred, label="Herramientas de Evaluación"];
        Risk_treatment_plan [fillcolor=indianred, label="Plan de Tratamiento"];
    }

    // ISO 9001:2015 Clausura 8.1 - Monitoreo y medición
    subgraph cluster_iso_monitoring {
        label = "ISO 8.1: Monitoreo y Medición";
        style = rounded;
        color = #4ECDC4;

        KPI_dashboard [fillcolor=lightseagreen, label="KPI Dashboard\n8.1.1 Indicadores"];
        Process_monitoring [fillcolor=mediumturquoise, label="Monitoreo de Procesos\n8.1.2 Monitoreo"];
        Performance_metrics [fillcolor=lightblue, label="Métricas de Desempeño\n8.1.4 Evaluación"];
    }

    // ISO 9001:2015 Clausura 8.2 - Requisitos del producto
    subgraph cluster_iso_requirements {
        label = "ISO 8.2: Requisitos del Producto";
        style = rounded;
        color = #45B7D1;

        Product_specifications [fillcolor=lightcyan, label="Especificaciones del Producto\n8.2.1 Planeación"];
        Design_review [fillcolor=lightblue, label="Revisión de Diseño\n8.2.3 Diseño y desarrollo"];
        Validation_activities [fillcolor=azure, label="Actividades de Validación\n8.2.4 Validación"];
    }

    // ISO 9001:2015 Clausura 8.5 - Acción correctiva
    subgraph cluster_iso_corrective {
        label = "ISO 8.5: Acción Correctiva";
        style = rounded;
        color = #96CEB4;

        Nonconformity_identification [fillcolor=lightgreen, label="Identificación\n8.5.2 Identificación"];
        Cause_analysis [fillcolor=darkgreen, label="Análisis de Causa Raíz\n8.5.2 Análisis"];
        Corrective_action [fillcolor=olive, label="Acción Correctiva\n8.5.3 Acción correctiva"];
        Effectiveness_verification [fillcolor=lightyellow, label="Verificación de Eficacia\n8.5.3 Verificación"];
    }

    // ISO 9001:2015 Clausura 9.1 - Revisión por parte de la dirección
    subgraph cluster_iso_review {
        label = "ISO 9.1: Revisión por parte de la dirección";
        style = rounded;
        color = #FFEAA7;

        Management_review [fillcolor=lemonchiffon, label="Revisión de Gestión\n9.1.1 Planeación"];
        Organization_performance [fillcolor=lightgoldenrodyellow, label="Desempeño de la Organización\n9.1.2 Requisitos legales"];
        Continual_improvement [fillcolor= wheat, label="Mejora Continua\n9.1.3 Requisitos de la organización"];
    }

    // ISO 9001:2015 Clausura 10.2 - No conformidades y correcciones correctivas
    subgraph cluster_iso_incidents {
        label = "ISO 10.2: No conformidades y correcciones";
        style = rounded;
        color = #FFA07A;

        Incident_reporting [fillcolor=salmon, label="Reportar Incidentes\n10.2.1 Reportar"];
        Incident_investigation [fillcolor=lightsalmon, label="Investigar Incidentes\n10.2.2 Investigar"];
        Corrective_and_preventive [fillcolor=orange, label="Corrección y Prevención\n10.2.3 Corregir y Prevenir"];
        Post_implementation_review [fillcolor= #FF8C00, label="Revisión Post-Implementación\n10.2.4 Revisar"];
    }

    // ISO 9001:2015 Clausura 10.3 - mejora continua del sistema
    subgraph cluster_iso_improvement {
        label = "ISO 10.3: Mejora Continua del Sistema";
        style = rounded;
        color = #A8E6CF;

        Continual_improvement_cycle [fillcolor=lightgreen, label="Ciclo de Mejora Continua\n10.3.1 Mejorar"];
        Quality_policy_review [fillcolor=darkgreen, label="Revisar Política de Calidad\n10.3.2 Revisar"];
        System_enhancement [fillcolor=olive, label="Mejorar Sistema\n10.3.1 Mejorar"];
    }

    // Conexiones
    CEO -> Risk_manager;
    CEO -> Quality_manager;

    Quality_manager -> KPI_dashboard;
    Quality_manager -> Process_monitoring;

    Quality_manager -> Product_specifications;
    Quality_manager -> Design_review;
    Quality_manager -> Validation_activities;

    Quality_manager -> Nonconformity_identification;
    Quality_manager -> Cause_analysis;
    Quality_manager -> Corrective_action;

    Nonconformity_identification -> Corrective_action;
    Cause_analysis -> Corrective_action;
    Corrective_action -> Effectiveness_verification;

    Quality_manager -> Management_review;
    Management_review -> Management_review;
    Management_review -> Continual_improvement;

    Quality_manager -> Incident_reporting;
    Incident_reporting -> Incident_investigation;
    Incident_investigation -> Corrective_and_preventive;
    Corrective_and_preventive -> Post_implementation_review;

    Post_implementation_review -> Continual_improvement_cycle;
    Continual_improvement_cycle -> Quality_policy_review;
    Quality_policy_review -> System_enhancement;

    // Diagrama C4 complementario para arquitectura de la información
    subgraph cluster_architecture {
        label = "Diagrama C4 - Arquitectura Informativa";
        style = rounded;
        color = #E2E2E2;

        subgraph cluster_context {
            label = "Nivel 1: Contexto";
            style = dashed;
            color = #E8E8E8;
            Banks_and_customers [fillcolor=white];
            Online_banking [fillcolor=white];
        }

        subgraph cluster_containers {
            label = "Nivel 2: Contenedores";
            style = dashed;
            color = #E8E8E8;
            Frontend [fillcolor=white];
            API_Gateway [fillcolor=white];
            Auth_Service [fillcolor=white];
            Transaction_Service [fillcolor=white];
        }

        subgraph cluster_components {
            label = "Nivel 3: Componentes";
            style = dashed;
            color = #E8E8E8;
            User_Authentication [fillcolor=white];
            Transaction_Validation [fillcolor=white];
            Notification_Service [fillcolor=white];
        }

        subgraph cluster_code {
            label = "Nivel 4: Código";
            style = dashed;
            color = #E8E8E8;
            Auth_Controller [fillcolor=white];
            Auth_Service_Impl [fillcolor=white];
            Database_Access [fillcolor=white];
        }

        // Conexiones arquitectónicas
        Banks_and_customers -> Online_banking;
        Online_banking -> Frontend;
        Frontend -> API_Gateway;
        API_Gateway -> Auth_Service;
        API_Gateway -> Transaction_Service;
        Auth_Service -> User_Authentication;
        Auth_Service -> Notification_Service;
        Transaction_Service -> Transaction_Validation;
        Transaction_Service -> Notification_Service;
        Auth_Service -> Auth_Controller;
        Auth_Service -> Auth_Service_Impl;
        Auth_Service_Impl -> Database_Access;
        Transaction_Service -> Database_Access;
    }
}
```

## Conclusión

La integración de los estándares ISO 9001 con el modelo C4 crea un sistema de documentación de arquitectura robusto y procesado. Este enfoque:

1. **Visualiza los requisitos organizacionales** ISO en diagramas claros y comprensibles
2. **Documenta procesos y controles** en múltiples niveles de abstracción
3. **Identifica alineación de riesgos y mejoras** entre filosofía basada en procesos e implementación técnica
4. **Facilita auditorías y revisiones** con seguimiento claro de cláusulas y controles
5. **Promueve mejora continua** con ciclos iterativos documentados explícitamente

La combinación ISO-C4 proporciona tanto el riguroso marco de calidad basado en procesos de ISO como la notación visual clara y centrada en la arquitectura de C4, resultando en una estrategia de documentación de arquitectura integral y práctica.
