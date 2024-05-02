# Fundamentos de Data Warehousing - Segunda Parte

## Duración Total: 2 horas

### Objetivos de Aprendizaje
Al final de esta sesión, los estudiantes podrán:
- Comprender qué es un Data Warehouse y cuáles son sus componentes principales.
- Explicar el proceso ETL y su importancia en Data Warehousing.
- Diferenciar entre los esquemas Estrella y Copo de Nieve y sus aplicaciones prácticas.
- Identificar las tendencias actuales y herramientas en el ámbito de los Data Warehouses.
- Reconocer la importancia de la gobernanza de datos en la estrategia de datos de una organización.

## Contenido

### Introducción a Data Warehousing (30 minutos)
- **Definición y Componentes:** Explorar la definición de Data Warehousing y sus componentes fundamentales.
- **Proceso ETL:** Describir el proceso de Extracción, Transformación y Carga, y su papel en Data Warehousing.

### Esquemas de Data Warehouse (1 hora)
- **Esquema Estrella vs. Esquema Copo de Nieve:** Analizar las diferencias, ventajas y desventajas de cada esquema.
- **Ejemplos y Casos Prácticos:** Proporcionar casos de estudio y ejemplos donde se apliquen estos esquemas.

### Tendencias y Herramientas Actuales (30 minutos)
- **Data Lakes y Plataformas en la Nube:** Examinar cómo los Data Lakes y las soluciones en la nube están cambiando el panorama de los Data Warehouses.
- **Herramientas de BI:** Revisar las herramientas de Business Intelligence más populares y su integración con los Data Warehouses.
- **Data Governance:** Entender la gobernanza de datos y su relevancia en la protección y gestión eficaz de los datos.

### Conclusión y Preguntas (15 minutos)
- **Resumen:** Recapitular los puntos clave de la sesión.
- **Preguntas y Respuestas:** Espacio para que los estudiantes resuelvan sus dudas y profundicen en los temas discutidos.

### Recursos Adicionales (15 minutos)
- **Documentación y Tutoriales:** Listar recursos en línea para aprender más sobre Data Warehousing y ETL.
- **Libros y Cursos Recomendados:** Sugerir material de lectura y cursos para una inmersión más profunda en el tema.
- **Comunidades y Foros:** Compartir foros y comunidades en línea donde los estudiantes puedan interactuar con profesionales y expertos en la materia.

## Introducción a Data Warehousing (30 minutos)

### Definición y Componentes

Un *Data Warehouse* es una sistema centralizado diseñado para integrar datos de múltiples fuentes, transformarlos según las necesidades del negocio y proporcionar una fuente de verdad única para el análisis y la toma de decisiones. Los componentes clave de un Data Warehouse incluyen:

- **Sistemas de Origen**: Donde se generan y recopilan los datos.
- **Almacenamiento de Datos**: La tecnología y la infraestructura para almacenar datos masivos.
- **Herramientas de Business Intelligence**: Aplicaciones que permiten el análisis y la generación de informes.
- **Herramientas de ETL**: Necesarias para transformar y cargar datos en el Data Warehouse.

Para una comprensión más profunda, consulta:
- [What is a data warehouse?](https://www.ibm.com/topics/data-warehouse).

### Proceso ETL

ETL, que significa *Extracción, Transformación y Carga*, es el proceso utilizado para mover y transformar datos desde sistemas de origen hacia el Data Warehouse. Este proceso incluye:

1. **Extracción**: Obtener datos de uno o más sistemas de origen.
2. **Transformación**: Limpiar, enriquecer y reformatear los datos según las reglas de negocio.
3. **Carga**: Insertar los datos transformados en el Data Warehouse para análisis.

Artículos recomendados para un estudio en profundidad:
- [What’s ETL? | Data Collection & Integration - Towards Data Science](https://towardsdatascience.com/whats-etl-b4903a57f8ce)
- [What is ETL? - Towards Data Science](https://towardsdatascience.com/what-is-etl-88154bdcde58)

Además, la discusión sobre ETL en el contexto de Python puede ser muy relevante para aquellos interesados en la ciencia de datos:
- [SQLAlchemy makes ETL magically easy - FreeCodeCamp](https://www.freecodecamp.org/news/sqlalchemy-makes-etl-magically-easy-ab2bd0df928/)

### Esquemas de Data Warehouse (1 hora)

#### Diferentes Esquemas: Star Schema vs Snowflake Schema

En el diseño de un Data Warehouse, el esquema utilizado para organizar las tablas y las relaciones entre ellas es crucial. Existen varios esquemas, pero principalmente se usan dos tipos de esquemas: Star Schema y Snowflake Schema.

##### Star Schema (Esquema Estrella)
- **Definición**: Un modelo de diseño de base de datos que consta de una tabla de hechos central (fact table) rodeada por tablas de dimensiones (dimension tables). La tabla de hechos contiene métricas cuantitativas y claves que apuntan a las tablas de dimensiones relacionadas.
- **Ventajas**: 
  - Alta eficiencia en el procesamiento de consultas.
  - Estructura sencilla y fácil de entender.
  - Rendimiento optimizado en herramientas de BI debido a menos joins.
- **Desventajas**:
  - No es tan normalizado, puede tener redundancia de datos.

##### Snowflake Schema (Esquema Copo de Nieve)
- **Definición**: Una extensión más compleja del esquema estrella donde las tablas de dimensiones están normalizadas, dividiéndose en tablas adicionales.
- **Ventajas**:
  - Mayor normalización y reducción de la redundancia de datos.
  - Mejor para datos complejos y cambiantes.
- **Desventajas**:
  - Puede requerir más joins, lo que puede afectar el rendimiento de las consultas.
  - Más complejo para comprender y administrar.

Para comprender en detalle estos esquemas y ver ejemplos visuales, estos artículos son de gran ayuda:
- [Star schema](https://www.geeksforgeeks.org/star-schema-in-data-warehouse-modeling/)
- [Snowflake schema](https://www.geeksforgeeks.org/snowflake-schema-in-data-warehouse-model/)
- [Star schema vs Snowflake](https://www.geeksforgeeks.org/difference-between-star-schema-and-snowflake-schema/)

### Tendencias y Herramientas Actuales (30 minutos)

La tecnología de datos está en constante evolución, y con ella, las estrategias y herramientas utilizadas para la recopilación, almacenamiento y análisis de datos. En esta sección, discutiremos las últimas tendencias en Data Lakes, plataformas en la nube, herramientas de BI y prácticas de Data Governance, proporcionando a los estudiantes una comprensión integral de cómo estos elementos están definiendo el futuro del Data Warehousing.

#### Data Lakes y Plataformas en la Nube

**Data Lakes** han surgido como una solución para el manejo de grandes cantidades de datos, permitiendo a las organizaciones almacenar información en su forma cruda, sin la necesidad de estructurarla previamente. Esto es especialmente útil en la era del Big Data, donde la velocidad y la variedad de datos generados requieren una flexibilidad que los sistemas tradicionales no pueden ofrecer.

Las **plataformas en la nube**, como AWS, Azure y Google Cloud, están facilitando la implementación de Data Lakes con su capacidad para escalar recursos según sea necesario, pagando solo por lo que se usa y beneficiándose de una gestión de datos más simplificada a través de servicios gestionados.

Los estudiantes deben comprender cómo estas tecnologías permiten un almacenamiento de datos más eficiente y cómo se integran con herramientas analíticas para procesar y extraer valor de grandes conjuntos de datos.

#### Herramientas de BI (Business Intelligence)

Las **herramientas de BI** son esenciales para las organizaciones que buscan tomar decisiones informadas basadas en datos. Herramientas como Power BI, Tableau y QlikSense transforman datos brutos en visualizaciones y dashboards interactivos, proporcionando insights accionables.

Al elegir una herramienta de BI, es crucial considerar la compatibilidad con los datos existentes, la facilidad de uso y las capacidades analíticas avanzadas. La herramienta ideal debe permitir a los usuarios finales crear informes personalizados sin depender demasiado del departamento de IT.

#### Data Governance

La **Data Governance** o gobernanza de datos, es un enfoque estratégico para gestionar los datos de una organización, asegurando su calidad, consistencia y seguridad. Involucra políticas, procedimientos y una clara definición de responsabilidades y procesos para manejar la información. Es fundamental en la era del GDPR y otras regulaciones de privacidad de datos, donde el manejo ético y legal de los datos es tan importante como su análisis.

Los estudiantes deben aprender no solo la importancia de una buena gobernanza de datos para el cumplimiento normativo, sino también cómo puede mejorar la eficiencia operativa y la confianza en las decisiones basadas en datos.

Con estos conceptos, los estudiantes estarán mejor equipados para entender las decisiones detrás de la arquitectura de sistemas de datos y la selección de herramientas, así como la importancia de las políticas y prácticas que aseguran el uso ético y efectivo de los datos.

### Conclusión y Preguntas (15 minutos)

Esta parte de la sesión está dedicada a solidificar el conocimiento adquirido y proporcionar un espacio para la interacción y la resolución de dudas.

- **Resumen**: Realizaremos un repaso conciso de los conceptos clave abordados, consolidando la comprensión de Data Warehousing, Data Lakes, BI y Data Governance.
- **Preguntas y Respuestas**: Momento para que los estudiantes realicen preguntas específicas, compartan inquietudes y profundicemos en aspectos particulares de la sesión.

### Recursos Adicionales (15 minutos)

Proporcionar a los estudiantes recursos adicionales es esencial para un aprendizaje continuo y autodirigido. A continuación, se presenta una lista de materiales y comunidades seleccionadas:

- **Documentación y Tutoriales**:
  - [Documentación Oficial de SQL de Microsoft](https://docs.microsoft.com/sql/)
  - [Tutoriales de Data Warehousing en W3Schools](https://www.w3schools.com/sql/)
  - [Ejercicios Interactivos en SQLZoo](https://sqlzoo.net/)

- **Libros y Cursos Recomendados**:
  - Kimball, R. & Ross, M., "The Data Warehouse Toolkit: The Definitive Guide to Dimensional Modeling"
  - Silberschatz, A., Korth, H.F., & Sudarshan, S., "Database System Concepts"
  - [Coursera: Data Warehousing for Business Intelligence Specialization](https://www.coursera.org/specializations/data-warehousing)
  - [edX: Introduction to Data Warehousing](https://www.edx.org/)

- **Comunidades y Foros**:
  - [Stack Overflow](https://stackoverflow.com/)
  - [Reddit Data Science Subreddit](https://www.reddit.com/r/datascience/)
  - [Discord Data Science Community](https://discord.com/invite/datascience)

Estos recursos son un punto de partida excelente para seguir explorando el mundo de los datos. Anima a tus estudiantes a sumergirse en estos materiales y a participar activamente en las comunidades en línea para continuar su desarrollo profesional en el ámbito del análisis de datos.

# Business challenge: Ejercicio de Diseño de Esquemas para Data Warehouse

## Escenario

Eres un Arquitecto de Data Warehouse trabajando para una compañía minorista internacional. La empresa busca construir un Data Warehouse para analizar patrones de ventas, la efectividad del marketing, la gestión de inventario y la lealtad del cliente.

## Requisitos del Negocio

- **Seguimiento de Ventas Diarias**: La compañía necesita rastrear las transacciones de ventas a nivel de producto, tienda y día.
- **Análisis de Campañas de Marketing**: Desean evaluar el impacto de las campañas de marketing en diversos canales.
- **Rendimiento del Inventario**: Es necesario correlacionar los niveles de inventario con los datos de ventas para optimizar el stock y la distribución.
- **Preferencias del Cliente**: Es crucial comprender las tendencias de compra y la lealtad de los clientes basándose en datos demográficos.

## Tarea

Tu tarea es diseñar un esquema para el Data Warehouse que satisfaga estos requisitos empresariales. Elige entre un **Star Schema** o un **Snowflake Schema** y justifica tu selección basándote en los requisitos de negocio proporcionados.

### Pasos:

1. **Identificar Fact Tables**: Determina cuál será el enfoque central del análisis.
2. **Definir Dimension Tables**: Enumera las dimensiones que se relacionan con la fact table y que son necesarias para los análisis requeridos por el negocio.
3. **Diseñar el Esquema**: Crea un diagrama esquemático que muestre cómo se organizarían las fact tables y las dimension tables. Si eliges un **Snowflake Schema**, asegúrate de normalizar las dimension tables.
4. **Justificación**: Proporciona una justificación para la elección de tu esquema y explica cómo cumple con los requisitos del negocio.

### Datos de Ejemplo

- **Fact Table**: Podría incluir claves que apunten a las dimension tables, cantidades vendidas y montos de ventas.
- **Dimension Tables**: Podrían incluir información sobre productos, tiendas, fechas, canales de marketing y demografía de clientes.

### Entregables

- Un diagrama esquemático de tu diseño de esquema.
- Una justificación escrita de tu elección de esquema y cómo aborda los requisitos empresariales.

Este ejercicio no solo te ayudará a entender los principios detrás del diseño de un Data Warehouse, sino que también te permitirá practicar cómo traducir los requisitos empresariales en una arquitectura de datos funcional.
