## BSGI-CAI-LLM-SA_TrabajoFinal
Repositorio del Curso Certified AI/LLM Solution Architect de BSG Institute
## 📋 Información General del Proyecto

| Campo | Valor |
|-------|-------|
| **Nombre del Proyecto** | Gestión de los servicios de mantemiento (correctivos, preventivos y predictivos), de la flota vehicular asistida por agentes de Inteligencia Artificial/LLM  |
| **Participante(s)** | Mtro. David Alejandro Pacanins Chávez |
| **Instructor** | Dr. Andrés Felipe Rojas Parra |
| **Cohorte / Edición** | *Ej. Cohorte 2025-A* |
| **Fecha de Inicio** | 04 mayo 2026 |
| **Fecha de Entrega Final** | 04 enero 2027 |
| **Versión del Documento** | *v1.0* |
| **Estado del Proyecto** | En Planificación / En Desarrollo  |
| **Repositorio GitHub/GitLab** | https://github.com/pakan2AI/BSGI-CAI-LLM-SA_TrabajoFinal.git |
| **Entorno Cloud** | Hibrido |
| **Stack Tecnológico Principal** | *Ej. Python, LangChain, GPT-4o, FastAPI, Docker, Kubernetes* 

## Tabla de Contenidos

- [1. Resumen Ejecutivo](#1-resumen-ejecutivo)
- [2. Análisis y Especificación de Requerimientos](#2-análisis-y-especificación-de-requerimientos)
- [3. Diseño de Arquitectura AI/LLM](#3-diseño-de-arquitectura-aillm)
- [4. Diseño de APIs y Conectores](#4-diseño-de-apis-y-conectores)
- [5. Seguridad, Cumplimiento y Ética](#5-seguridad-cumplimiento-y-ética)
- [6. Implementación y Configuración de Infraestructura](#6-implementación-y-configuración-de-infraestructura)
- [7. Estrategia de Pruebas y Resultados](#7-estrategia-de-pruebas-y-resultados)
- [8. Despliegue, Escalabilidad y Costos](#8-despliegue-escalabilidad-y-costos)
- [9. Observabilidad y Monitoreo](#9-observabilidad-y-monitoreo)
- [10. Resultados, Conclusiones y Trabajo Futuro](#10-resultados-conclusiones-y-trabajo-futuro)
- [11. Rúbrica de Evaluación](#11-rúbrica-de-evaluación)
- [12. Referencias y Bibliografía](#12-referencias-y-bibliografía)
- [Anexos](#anexos)

---

## 1. Resumen Ejecutivo

*Este trabajo esta basado en un grupo de empresas especializadas en movilidad de personas, como son: transporte de personal, escolar, servicios especiales configurados por los clientes a eventos públicos o privados, y paquetes de transporte a centros turísticos, con/o sin entradas, de entretenimiento o cualquier otro destino que desee el cliente. Tiene operación en más de 15 ciudades del país. No todas las marcas tienen presencia en las ciudades mencionadas. Las marcas que tienen operación están representadas por unidades administrativas, la estructura organizacional de estas unidades es: dirección general, área comercial, capital humano, operaciones, logística, facturación-cobranza y un parque vehicular asignado según el tamaño de la operación que se tenga contratada. **La flota vehicular del grupo es de aproximadamente de 9000 unidades**, integradas por: camiones y camionetas de diferentes años de fabricación, asignadas según la operación en las unidades de negocio.

Un contrato de movilidad, está representada por la relación de un cliente (Nombre, Razón Social,rfc), un servicio o contrato (datos generales, datos fiscales, datos bancarios), las especificaciones del servicio( numero de personas a movilizar,n rutas,  m viajes y las especificaciondes de los dias y las horas de las rutas a realizar. Las **rutas** están definidas por un punto inicial (número de personal, coordenadas y la hora), puntos de colecta- en algunos casos (coordenadas, personas y horas) y un punto final (coordenadas y hora de llegada), en el caso de rutas de entrada, para el caso de rutas de salida es: un punto inicial (coordenadas, número de personas y hora). y un punto final (coordenadas y hora), para servicios fijos no cambian estas especificaciones en el ciclo de vida del contrato, para servicios especiales, solo son válidos para el día y fecha especificados en el contrato. Un **viaje** es la ejecución de la ruta en los días/horarios especificados en el contrato. 

La operación diaria que reflejan los contratos establecidos, son de aproximadamente 15000 viajes en más de mil rutas, más los servicios especiales, esta operación se monitorea mediante el seguimiento de las unidades con dispositivos GPS en tiempo real. Dependiendo de la ciudad son los horarios de servicio, hay lugares en donde la mayoría de los clientes son empresas con líneas de producción que están las 24 horas operando los 7 días de la semana, ello implica tener servicios de entrada y salida por los tres turnos para movilizar a los empleados desde los puntos de recolección a la empresa y viceversa. Otras empresas requieren movilizar a sus empleados dentro de las instalaciones, entre diferentes edificios o complejos, en estos casos las unidades se encuentran realizando servicios de ruleta, durante todo el día. En lugares en donde el servicio es para oficinas o centros educativos, como es en la CDMX, las unidades tienen programados los servicios de entrada y salida a determinadas horas de lunes a viernes.

El parque vehicular, los operadores y los clientes, son los factores de mayor importancia para el grupo, contar con una flota de 9000 unidades y una operación de 15000 viajes diarios, requiere que la gestión de los servicios de mantenimiento del parque vehicular funcione de manera eficiente, eficaz y de calidad, para que la movilidad de las personas se realice en tiempo, forma y de manera segura para seguir siendo lideres en el ramo.*

### 1.1 Propuesta de Valor y Problema que Resuelve

Para tener una operación eficiente, optima y eficaz, el grupo cuenta con un área de excelencia operativa que cuenta con los departamentos de logística, operaciones, mantenimiento y combustibles. EL departamento de logística se encarga de optimizar las rutas que se solicitan en las cotizaciones de servicios fijos, como también el número de vehículos, el tipo y año para solventar la operación solicitada. Cuando ya se concretan los contratos y se tienen la operación diaria, existe un periodo de optimización de rutas en ejecución por la combinación vehículo/operador asignado a cada ruta, cuando se da de baja un operador se asigna uno nuevo que quizás viva en un diferente lugar al anterior y esto hace que se re asignen ciertos operadores según la optimización de la ruta/operador para reducir los tiempos en vacío. desplazamientos que se realizan antes de comenzar una ruta, por lo regular de la casa del operador al punto de colecta del inicio de la ruta, o del punto de llegada-destino-al encierro o lugar de espera, hasta que se realice el siguiente viaje a realizar.

Cada unidad de negocio cuenta con una cabina de control, qué pertenece al departamento de logística, con tres turnos, para dar seguimiento a los viajes programados por día, registrar las incidencias y verificar que el ETA, corresponda a los establecidos para calificar los viajes como realizados correctamente, según las especificaciones de servicio registradas en el contrato. El departamento de operaciones, gestiona al personal operativo: operadores, coordinadores, jefes de operación y gerentes de operación. 

La rentabilidad de la empresa descansa en el mayor tiempo de operación de las unidades por servicios fijos o especiales, según el contrato realizado. Esto requiere que las unidades estén en óptimas condiciones mecánicas con los servicios preventivos en tiempo y forma según las políticas establecidas por la dirección de mantenimiento.

Cumplir con la operación de 15000 viajes diarios, no es solo un trabajo de planeación y ejecución sino también cumplir con las especificaciones de servicio descritas en los contratos de cada cliente, requiere que los vehículos estén en correcto funcionamiento y disponibles el mayor tiempo posible, para lograr esto, el grupo cuenta con 17 talleres generales, 2 regionales, distribuidos en toda la república, para dar el soporte de servicio de mantenimiento a las 9000 unidades y mantenerlas operativamente funcionales, como lo requiere la operación.  Cada taller cuenta con 5 bahías de atención, especializadas en un tipo de servicio específico: pintura y hojalatería, eléctrico, mecánico, llantas y generales, se cuenta con un área de servicio llamada express o pits- que atienden cuestione como llenado de aceites, calibración de llantas, cambios de focos, actividades que no llevarían más de 10 minutos de atención. Los horarios y turnos de atención, dependen del tamaño de la operación de la unidad de negocio, teniendo talleres que cuentan con un turno, otros con dos y unos pocos de 24 hrs. Hay talleres que dan servicio a vehículos de hasta tres marcas, según su capacidad y programación diaria.

**Los servicios se clasifican en: Correctivos, preventivos y predictivos.**

**Los servicios correctivos**, a su vez se dividen en dos, aquellos que requieren una atención inmediata, menos de 10 minutos, por lo pequeño del fallo pero que pueden interrumpir la operación sino son atendidos inmediatamente, como son luces, líquidos especiales como son líquido de frenos, aceite de motor, anticongelante, liquido de limpia para brizas, llantas ponchadas, falta de aire. Los servicios correctivos que requieren una atención de más tiempo en el taller, como son pintura, cambio de piezas por accidentes, fallo o falta de piezas.

**Los servicios preventivos** están debidamente identificados por el kilometraje recorrido y los años de vida de las unidades, por las alertas que registra el motor, que se registran mediante el servicio de GPS, en tiempo real.
**Los servicios preventivos para llantas**, dependen del desgaste progresivo por el uso o por la pérdida total de la llanta por accidente, en estos casos se entra a servicio para realizar el cambio, en el caso del desgaste, se lleva el registro de la asignación de las llantas por vehículo, la posición que se coloca cada una, el registro de la medición del desgaste por la operación, como también el intercambio de la posición para que se realice un desgaste parejo, en una plataforma especializada. Con esta información se programa la entrada a taller para atender temas de llantas. 
**Los servicios preventivos por kilómetros o desgaste de llantas**, se encuentran clasificados, cada clasificación tiene identificados los recursos materiales, técnicos (llamados kid´s de servicios) y de tiempo que requieren para ser ejecutados.  Esto permite tener una estimación de costos asociados a cada servicio y permitir una mejor planeación de atención y presupuestos.

Cada taller tiene catalogados los servicios preventivos, según el tiempo de atención, servicios menores de 15 minutos, servicios mayores de 15 minutos y menores a 48 hrs, servicios de mas de 48 hrs hasta 40 hrs, y servicios de mas de una semana y menores a cuatro semanas. Entre más tarde un vehículo en el taller, mas afecta la operación y se requiere tener un pull de vehículos que den el servicio temporalmente. 

**Los servicios predictivos** se clasifican en dos tipos, los que se determinan por el ciclo de vida de ciertas piezas mecánicas claves en el funcionamiento correcto del vehículo y el segundo enfocado en las alertas, en tiempo real, que envían ciertas áreas del motor mediante el canban, estas mediciones se envían cada 15 o 20 segundos por vehículo, se tienen que recolectar, clasificar y evaluar en tiempo real para evitar problemas mayores con el motor.
La estructura de personal con el que cuenta cada taller es: técnicos en electricidad, pintura y hojalatería, llantas, mecánica general, jefes de taller, gerentes de taller, gerentes regionales de taller y el personal administrativo de corporativo del área de taller.

El proceso de gestión de las unidades para entrada a taller por servicios preventivos y predictivos, (recolección, clasificación y evaluación de la información, la programación y notificación a los actores interesados), se realiza manualmente, esto conlleva un alto riesgo de errores, tiempos muertos de atención, sobrecarga del taller, incumplimiento de la ejecución de servicios, mala toma de decisiones, estadísticas mal realizadas o a destiempo.
La información que requiere este proceso no solo pertenece a mantenimiento, sino proviene de otras áreas como: comercial (características del servicio), logística operación (programación de viajes por vehículo), almacén (disponibilidad, especificaciones de garantías y periodos de vida de las piezas, compras ),  finanzas (presupuesto), sistema de llantas (asignación de llantas y la posición de cada una de ellas por vehículo, desgaste individual, fechas de asignación y de las medidas realizadas), proveedor del GPS (geolocalización del vehículo, kilómetros recorridos, alertas de motor), combustibles (consumos y rendimientos por vehículo), excelencia operativa (score de manejo, score de seguridad), la integración con estas áreas y los sistemas que gestionan la información, requieren de un conjunto de API´s de ambas vías, para garantizar calidad de la información en los tiempos y forma requeridos.

Se propone como solución una plataforma de gestión del proceso de servicios de mantenimiento asistida por agentes de IA, que este enfocada para satisfacer las necesidades de la gestión operativa de mantenimiento, reducir los tiempos de (recolección, clasificación y evaluación de la información, la programación y notificación a los actores interesados), en la espera y atención en taller por servicios preventivos y predictivos. Reducción de costos en atención, en servicio y fallos de las unidades, para lograr estos objetivos se requiere que la plataforma identifique las unidades que requieren servicio correctivo, preventivo y predictivos, la programación, asignación del taller, bahías de servicio, la gestión de los recursos requeridos para la atención de la unidad y de las notificaciones requeridas en cada etapa del proceso a cada actor en la forma y canal identificado.

La implementación de la solución debe de estar adecuada a las características de la operación de los talleres del área de mantenimiento, de las necesidades operativas y de servicio por parte de la empresa para con los clientes. La propuesta está enfocada en una plataforma web, que puede ser accedida mediante dispositivos móviles y de escritorio para facilitar el acceso y operación en cada uno de los niveles de operación que se identificaron en el proceso. La solución está enfocada para los usuarios internos que son parte del proceso de gestión de servicios de mantenimiento y de las áreas involucradas, dentro o fuera de las instalaciones, según el nivel de acceso asignado. Se contempla el acceso restringido mediante niveles de acceso gestionados por roles y responsabilidades de los usuarios. No se permitirá tener más de una sesión abierta. 

La solución será un desarrollo hecho a la medida y de tipo web que permita a los clientes acceder a las funcionalidades desde diferentes tipos de dispositivos. Para cumplir con esta característica se utilizará infraestructura de servicios de cloud computing, como son base de datos para la persistencia de la información y instancias para el servidor de aplicaciones. Para garantizar la seguridad en las transacciones de la plataforma se implementará un certificado SSL y la encriptación de contraseñas. También se implementarán y respetaran las leyes y normas en materia de acceso a la información que son vigentes en México.


### 1.2 Objetivo general y objetivos particulares
**Objetivo General**
Implementar una plataforma informática asistido por agentes de IA, en 10 meses, que gestione de manera eficiente, las actividades de mantenimiento para reducir los tiempos de atención en un 40%, costos en un 20% y perdidas asociadas en la falta de identificación de los servicios preventivos por kilómetros recorridos, sustitución o cambio de piezas, o por la identificación de alertas severas que motor registre en canban.

**Objetivos particulares**
1.	Identificar en tiempo y forma los vehículos que requieren servicio preventivo por kilometrajes para realizar la óptima programación de servicio en los talleres asociados a la unidad de negocio que pertenecen, en los tiempos que no cuente con programación de servicios.

2.	Identificar los vehículos que requieren servicio de forma inmediata por el tipo y frecuencia de notificaciones de alarmas que el motor registra y envía en la plataforma de canban. Programarlos en los talleres asociados a la unidad de negocio que pertenecen.

3.	Optimizar la gestión de la programación de las bahías de atención de servicio según el tipo de servicio, prioridad de atención, recursos técnicos y de personal. 

4.	Optimizar los recursos materiales de taller por la correcta identificación de los servicios, programación y asignación de personal 

5.	Reducir los tiempos de atención por la correcta programación y asignación de recursos en cada servicio.
6.	Reducir el riesgo y costos en la identificación de vehículos que requieren atención inmediata por alertas de motor no identificadas y evaluadas a tiempo.


### 1.3 Alcance y Delimitación

*Defina con precisión qué está IN SCOPE y qué está OUT OF SCOPE para la versión entregada.*

| ✅ EN SCOPE | ❌ OUT OF SCOPE |
|------------|----------------|
| Ej. Integración con fuentes de datos internas de la empresa | Ej. Entrenamiento de modelos desde cero (fine-tuning de base) |
| Ej. Despliegue en entorno cloud (AWS/Azure/GCP) | Ej. Soporte en idiomas distintos al español e inglés |
| *[Agregue más filas según necesidad]* | *[Agregue más filas según necesidad]* |

### 1.3 Indicadores Clave de Éxito (KPIs del Proyecto)

| KPI / Métrica | Línea Base | Meta Objetivo | Resultado Obtenido |
|---------------|-----------|---------------|-------------------|
| Latencia promedio (p95) | N/A | < 2 segundos | *[Completar al final]* |
| Tasa de éxito de respuestas | *[Baseline]* | > 92% | *[Completar al final]* |
| Costo por 1,000 consultas (USD) | *[Baseline]* | *[Definir]* | *[Completar al final]* |
| Cobertura de pruebas (%) | 0% | > 80% | *[Completar al final]* |
| *[KPI adicional]* | | | |

---
