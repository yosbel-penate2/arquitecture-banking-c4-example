# Configuración del Proyecto

## Documentos ISO clave

### 1. Documento de Ámbitos (ISO 1.1)

# Documento de Ámbitos - Sistema de Gestión de Calidad - BankingCo

## 1. Objetivo

1.1 Definir el ámbito del Sistema de Gestión de Calidad (QMS)

1.2 Incluye:
   - Plataformas de banca digital (WEB/Mobile/PWA)
   - Servicios bancarios principales (cuentas, transacciones, notificaciones)
   - Infraestructura en la nube (AWS con RDS, S3, SQS)
   - APIs REST y servicios microservicios

1.3 Excluye:
   - Documentación personal de empleados
   - Procesos financieros externos fuera del sistema
   - Implementaciones de terceros no relacionadas con la banca

## 2. Procesos principales identificados para la mejora continua

2.1 Planificación
   - Planificación de riesgos e imprevistos
   - Planificación de mejora continua

2.2 Diseño e implementación
   - Arquitectura de microservicios
   - Desarrollo guiado por pruebas TDD
   - Implementación DevOps con CI/CD

2.3 Monitoreo y medición
   - Seguimiento KPI Operativos
   - Detección de fraudes
   - Balance de riesgos

2.4 Mejora continua
   - Revisiones de procesos
   - Auditoría del sistema de calidad
   - Controles de cambios (ISO 8.5)

## 3. Criterios de éxito ISO

3.1 Requisitos regulatorios
   - Cumplimiento de KYC
   - Normas AML
   - Pronunciamientos del Banco Central

3.2 Objetivos de calidad
   - Tiempo de actividad 99.99%
   - Tasa de error error < 0.01%
   - Velocidad de respuesta < 200ms

3.3 Objetivos del sistema de calidad
   - Clientes satisfechos > 90%
   - Sin incidentes críticos
   - Aprobación de auditoría

## 4. Referencias

- ISO 9001:2015 - Sistemas de gestión de calidad — Requisitos
- ISO 27001 - Seguridad de la información
- Acuerdos de nivel de servicio (SLA)
- Reglas de cumplimiento normativo


## 2. Gestión de planificación de riesgos ISO (ISO 6.1)

# Planificación de la gestión de riesgos e imprevistos

## 1. Tipos de riesgos identificados

| ID | Riesgo | Probabilidad | Impacto | Nivel | Responsable | Tratamiento |
|----|--------|--------------|--------|-------|-------------|-------------|
| R001 | Vulnerabilidades de seguridad | Media | Alto | Alto | Ciberseguridad | Mitigar | 
| R002 | Fallos en el RTO de la base de datos | Baja | Alto | Medio | DBAs | Aceptar |
| R003 | Desacuerdos regulatorios | Baja | Medio | Bajo | Conformidad | Mitigar |
| R004 | Fallos en la tasa de error del backend | Media | Medio | Medio | Ingenieros backend | Mitigar |
| R005 | Incidentes de tiempo de inactividad por DDoS | Baja | Alto | Alto | Infraestructura | Evitar |
| R006 | Codificación mediocre | Media | Medio | Medio | Ingenieros de software | Mitigar |
| R007 | Baja participación del equipo | Baja | Bajo | Bajo | Recursos humanos | Aceptar |
| R008 | Falta de integración de API | Alta | Alto | Alto | Arquitecto | Mitigar |

## 2. Tratamiento de riesgos

### Aceptar (R002, R007)
- Documentar el riesgo y las condiciones de aceptación
- Establecer un monitoreo continuo sin acciones correctivas adicionales

### Mitigar (R001, R004, R005, R006, R008)
- Aplicar controles de seguridad adecuados
- Implementar mecanismos de detección de errores
- Implementar defensas contra DDoS
- Implementar pruebas unitarias estrictas

### Evitar (R005)
- Subcontratar servicios de CDN/DDoS
- Implementar restricciones de limitación de velocidad

## 3. Monitoreo y medición ISO (8.1)

### 3.1 Indicadores clave de rendimiento (KPI)

- **Tiempo de actividad del servicio**: Tiempo de respuesta anual (medido en minutos)
- **Tasa de error**: Porcentaje de solicitudes fallidas (%)
- **Tiempo de respuesta**: Latencia promedio (ms)
- **Tasa de aprobación de auditoría**: % de auditorías exitosas
- **Latencia de API**: Latencia máxima (ms)

### 3.2 Estándares de calidad ISO

- **ISO 25000**: Calidad de software (usabilidad, eficiencia, seguridad, mantenibilidad)
- **ISO 15289**: Contenido y formato del informe de pruebas de software
- **ISO 12119**: Control de calidad y conformidad

### 3.3 Planes de medición

**Verifica (8.2):
- Seguimiento de calidad del producto: Garantía de calidad de cada lanzamiento
- Evaluación de la efectividad del plan de riesgo y acción correctiva de control de calidad
- Medición del nivel de madurez de la calidad del software

**Monitoriza (8.1):
- KPI metricos de rendimiento
- Monitoreo de fraudes y actividades sospechosas
- Estado de las actividades del plan de mejora continua

## 4. Mejora continua (ISO 10.3)

### 4.1 Plan de mejora continua

**Evaluación del rendimiento**
- Auditoría de calidad y productividad del software
- Auditoría de riesgos, seguridad y cumplimiento normativo
- Auditoría del sistema de gestión de calidad

**Acción correctiva**
- Identificar y corregir problemas
- Auditar la causa raíz en profundidad
- Efectuar actividad repetitiva y continua

### 4.2 Seguimiento y medición (ISO 8.5)

**Producto**: Garantía de calidad de cada versión
- Pruebas unitarias / de integración
- Pruebas de penetración de seguridad
- Pruebas de carga y rendimiento
- Pruebas de solo lectura

**Proceso**:
- Auditorías internas y externas del sistema de gestión de calidad
- Plano de madurez de calidad de software basado en ISO 25010

**Recurso**: El sistema de gestión de calidad
- Mejorar el sistema de calidad y las competencias
