# Fundamentos de Bases de Datos - Primera Parte

## Duración Total: 2 horas

### Objetivos de Aprendizaje
Al final de esta sesión, los estudiantes podrán:
- Entender la definición y el propósito de las bases de datos.
- Identificar los diferentes tipos de modelos de bases de datos.
- Diferenciar entre bases de datos SQL y NoSQL.
- Comprender los principios básicos de diseño de bases de datos y normalización.

## Contenido

### Introducción a Bases de Datos (30 minutos)
- **Definición y Propósito:** Explicar qué es una base de datos y su rol en la gestión de datos.
- **Tipos de Usuarios:** Describir los diferentes perfiles que interactúan con las bases de datos: administradores de bases de datos, desarrolladores, analistas de datos y usuarios finales.

### Modelos de Datos (30 minutos)
- **Modelo Relacional:** Características y estructura de las bases de datos relacionales.
- **Modelo de Documentos:** Describir cómo funcionan las bases de datos basadas en documentos y cuándo son una opción adecuada.
- **Modelo Clave-Valor:** Explicar las bases de datos clave-valor y sus casos de uso típicos.
- **Modelo de Columnas Amplias:** Diferenciar el modelo de columnas amplias de otros modelos y discutir su utilidad.
- **Modelo de Grafos:** Presentar las bases de datos de grafos y sus ventajas para representar relaciones complejas.

### SQL vs NoSQL (30 minutos)
- **SQL:**
  - Definir SQL y discutir las características principales de las bases de datos SQL.
  - Discutir la escalabilidad vertical y las transacciones ACID.
  - Presentar ejemplos básicos de consultas SQL.
- **NoSQL:**
  - Introducir el concepto de NoSQL y explicar el teorema CAP.
  - Hablar sobre la escalabilidad horizontal.
  - Mostrar ejemplos de uso de bases de datos NoSQL.

### Diseño de Bases de Datos y Normalización (30 minutos)
- **Principios de Diseño:** Introducir los principios fundamentales del diseño de bases de datos, incluyendo tablas, filas, y columnas.
- **Normalización y Formas Normales:** Explicar qué es la normalización y para qué sirven las formas normales. Discutir cómo la normalización puede prevenir redundancias y mejorar la integridad de los datos.

## Introducción a Bases de Datos (30 minutos)

### ¿Qué es una Base de Datos?

Una base de datos es una colección de datos estructurados que se almacenan de forma organizada y eficiente para que puedan ser accedidos, gestionados y utilizados de forma eficiente. Las bases de datos se utilizan para almacenar una gran variedad de datos, desde información personal hasta datos científicos y empresariales.

**Artículos relevantes:**

* [What is a Database?](https://www.oracle.com/database/what-is-database/)
* [Introducción a las Bases de Datos](https://gestionbasesdatos.readthedocs.io/es/latest/Tema1/Teoria.html)

### Tipos de Usuarios de Bases de Datos

El ecosistema de las bases de datos incluye una variedad de roles, cada uno con responsabilidades únicas:

* **Administradores de Bases de Datos (DBAs):** Encargados de la salud y el rendimiento de la base de datos.
* **Desarrolladores de Bases de Datos:** Especializados en la creación de aplicaciones que se comunican con bases de datos.
* **Analistas de Datos:** Profesionales que interpretan datos para obtener insights y apoyar la toma de decisiones.
* **Usuarios Finales:** Personas que interactúan con los datos a través de una interfaz, sin necesidad de conocimientos técnicos sobre cómo funciona la base de datos.

**Artículos relevantes:**

* [Tipos de usuarios de bases de datos](https://barcelonageeks.com/diferentes-tipos-de-usuarios-de-bases-de-datos/)
* [Deep dive en roles de datos](https://www.springboard.com/blog/data-science/data-science-roles/)

### Diferencias entre Bases de Datos y Excel

Las bases de datos y las hojas de cálculo como Excel tienen propósitos y capacidades distintas. Excel es una herramienta excelente para análisis de datos y proyectos pequeños, pero no está diseñada para manejar grandes volúmenes de datos o realizar operaciones complejas.

**Diferencias clave:**

* **Estructura y Capacidad:** Las bases de datos están diseñadas para almacenar grandes cantidades de datos de manera eficiente, algo que Excel no puede hacer sin comprometer el rendimiento.
* **Funcionalidad:** Las bases de datos ofrecen funcionalidades avanzadas como transacciones, control de concurrencia, y seguridad de datos.
* **Consulta de Datos:** Las bases de datos utilizan lenguajes de consulta como SQL para realizar operaciones complejas, mientras que Excel se basa en fórmulas y funciones.
* **Integridad de Datos:** Las bases de datos mantienen la integridad de los datos a través de restricciones y reglas de negocio.
* **Escalabilidad:** Las bases de datos están diseñadas para escalar con el crecimiento de los datos, algo que Excel no maneja bien.

## Modelos de Datos (30 minutos)

En esta sección, exploraremos los diferentes modelos de bases de datos que son fundamentales para comprender cómo se estructuran y se pueden utilizar los datos en distintos contextos.

### Modelo Relacional

El modelo relacional es uno de los modelos de bases de datos más utilizados. Se basa en la teoría de conjuntos y utiliza una estructura de tabla donde los datos se organizan en filas y columnas. Cada fila representa un registro único y cada columna un campo de ese registro.

- **Características clave:**
  - Estructura tabular
  - Integridad de datos a través de claves primarias y foráneas
  - Operaciones basadas en el álgebra relacional
  - Uso de SQL para la manipulación y consulta de datos

- **Artículo relevante:**
  - [Understanding Relational Databases](https://cloud.google.com/learn/what-is-a-relational-database)

### Modelo Clave-Valor (Key-value)

Las bases de datos clave-valor son sistemas de almacenamiento de datos que utilizan un método simple de clave única para acceder a un valor de datos. Son extremadamente rápidas para consultas de recuperación y actualización y son muy escalables.

- **Casos de uso típicos:**
  - Almacenamiento de sesiones de usuario
  - Sistemas de caché
  - Aplicaciones que requieren alta disponibilidad y baja latencia

- **Artículo relevante:**
  - [Key-Value Databases, Explained](https://redis.com/nosql/key-value-databases/)

### Modelo de Documentos (document store, an evolution of Key-value)

Las bases de datos basadas en documentos almacenan y gestionan datos en formatos de documentos, como JSON, XML o BSON. Son ideales para aplicaciones que requieren una gran flexibilidad en la estructura de datos y donde los datos no se ajustan naturalmente a un esquema rígido.

- **Cuándo usarlas:**
  - Cuando los datos son semi-estructurados o no estructurados
  - Para aplicaciones que requieren agilidad en el desarrollo y cambios frecuentes en el esquema
  - En sistemas donde el rendimiento de lectura es crítico

- **Artículo relevante:**
  - [When to Use Document Databases](https://www.mongodb.com/document-databases)

### Modelo de Columnas Amplias (wide column store, an evolution of Key-value)

El modelo de columnas amplias almacena datos en columnas en lugar de filas, lo que es útil para consultas que deben leer grandes cantidades de datos de una columna específica. Es ideal para analizar grandes conjuntos de datos y para bases de datos que deben escalar horizontalmente.

- **Diferencias clave:**
  - Almacenamiento de datos por columnas en lugar de filas
  - Optimizado para consultas sobre grandes conjuntos de datos
  - Escalabilidad horizontal

- **Artículo relevante:**
  - [Wide-Column Store vs. Relational Database](https://www.scylladb.com/glossary/wide-column-database/)

### Modelo de Grafos

Las bases de datos de grafos están diseñadas para almacenar y navegar relaciones entre entidades de manera eficiente. Son ideales para representar datos complejos y conectados como redes sociales, sistemas de recomendación y más.

- **Ventajas:**
  - Representación intuitiva de relaciones y patrones
  - Eficiencia en la navegación y exploración de conexiones complejas
  - Flexibilidad para evolucionar sin un esquema predefinido

- **Artículo relevante:**
  - [Graph Databases for Beginners](https://neo4j.com/developer/graph-database/)

Cada modelo de datos tiene sus propias ventajas y es adecuado para diferentes tipos de aplicaciones. La elección del modelo de datos depende de los requisitos específicos del sistema y del tipo de operaciones que se realizarán con los datos.

## SQL vs NoSQL (30 minutos)

En esta sección, exploraremos las diferencias fundamentales entre las bases de datos SQL y NoSQL, dos paradigmas dominantes en el mundo de la gestión de datos.

### SQL

SQL (Structured Query Language) es el estándar para trabajar con bases de datos relacionales. Estas bases de datos están estructuradas para reconocer relaciones entre los datos almacenados en tablas.

- **Definición y características principales:**
  - SQL es un lenguaje de dominio específico utilizado en la programación y diseñado para administrar datos en un sistema de gestión de bases de datos relacionales.
  - Las bases de datos SQL son ideales para aplicaciones que requieren transacciones complejas y donde la integridad y la seguridad de los datos son críticas.
  - Son conocidas por su rigidez en los esquemas de datos, lo que puede ser una ventaja para garantizar la consistencia de los datos.

- **Escalabilidad vertical y transacciones ACID:**
  - La escalabilidad vertical implica aumentar la capacidad de un solo servidor, como agregar más memoria o un procesador más rápido.
  - Las bases de datos SQL siguen el modelo ACID para garantizar que todas las transacciones son procesadas de manera confiable.

### NoSQL

NoSQL es un término que engloba una variedad de tecnologías de bases de datos diseñadas para superar las limitaciones de las bases de datos SQL, ofreciendo modelos de datos más flexibles y escalabilidad horizontal.

- **Concepto y teorema CAP:**
  - NoSQL representa "not only SQL" y se refiere a bases de datos no relacionales.
  - El teorema CAP establece que un sistema de base de datos distribuida no puede garantizar simultáneamente la Coherencia (C), la Disponibilidad (A) y la Tolerancia a particiones de red (P) al 100%.
  - Las bases de datos NoSQL a menudo hacen concesiones entre estos tres aspectos según las necesidades específicas de la aplicación.

- **Escalabilidad horizontal:**
  - A diferencia de las bases de datos SQL, las NoSQL están diseñadas para escalar horizontalmente, lo que significa que pueden expandirse a través de múltiples servidores y ubicaciones.
  - Esta característica las hace particularmente adecuadas para aplicaciones en la nube y de gran escala que manejan enormes volúmenes de datos y tráfico.

- **Casos de uso de bases de datos NoSQL:**
  - Las bases de datos NoSQL son preferidas en situaciones donde los datos no son estructurados o donde la estructura de los datos puede cambiar con el tiempo.
  - Son ideales para almacenar datos de usuario para aplicaciones web, manejar grandes volúmenes de datos en tiempo real y para aplicaciones que requieren una rápida iteración del desarrollo.

Al comprender las diferencias entre SQL y NoSQL, los desarrolladores y arquitectos de bases de datos pueden tomar decisiones más informadas sobre qué tecnología se adapta mejor a las necesidades de su aplicación o proyecto.

[NoSQL vs SQL](https://www.geeksforgeeks.org/difference-between-sql-and-nosql/)

## Diseño de Bases de Datos y Normalización (30 minutos)

El diseño de bases de datos es un paso crítico en la creación de sistemas de información eficientes y confiables. Un buen diseño asegura que la base de datos sea capaz de manejar datos de manera eficiente y flexible. La normalización es una parte fundamental de este proceso.

### Principios de Diseño

Al diseñar una base de datos, es esencial comprender y aplicar ciertos principios fundamentales que guiarán la estructura y organización de los datos.

- **Tablas, Filas y Columnas:**
  - **Tablas:** También conocidas como relaciones, las tablas son la estructura principal en una base de datos relacional y deben diseñarse para almacenar información sobre un tipo de entidad.
  - **Filas:** Cada fila en una tabla representa una instancia única de la entidad definida por la tabla.
  - **Columnas:** Las columnas en una tabla, también conocidas como atributos, representan los diferentes datos que se guardan para cada instancia de la entidad.

### Normalización y Formas Normales

La normalización es el proceso de estructurar una base de datos relacional para reducir la redundancia y mejorar la integridad de los datos.

- **Qué es la Normalización:**
  - La normalización implica descomponer tablas en partes más pequeñas y manejables mientras se mantienen las relaciones entre ellas.
  - El objetivo es minimizar la duplicación de datos y evitar problemas de actualización de datos en la base de datos.

- **Propósito de las Formas Normales:**
  - Las formas normales son un conjunto de reglas para guiar el diseño de la base de datos.
  - Cada "forma normal" es un nivel de requisitos que una base de datos debe cumplir para considerarse normalizada.
  - Las primeras tres formas normales (1NF, 2NF, 3NF) son las más utilizadas y se centran en asegurar que cada tabla tenga una clave primaria y que los datos almacenados en una tabla se refieran solo a esa clave primaria.

- **Prevención de Redundancias:**
  - La normalización ayuda a prevenir redundancias al asegurar que cada pieza de información se almacene solo una vez.
  - Cuando los datos se actualizan, la normalización reduce el riesgo de inconsistencias, ya que cada dato tiene un único punto de actualización.

- **Mejora de la Integridad de los Datos:**
  - Al separar los datos en tablas lógicas y relacionadas, la normalización protege la integridad de los datos.
  - Las restricciones de integridad, como las claves foráneas, aseguran relaciones consistentes entre tablas.

La normalización es un equilibrio entre la eficiencia de acceso a los datos y la rapidez de actualización de los mismos. En algunos casos, especialmente en bases de datos de alto rendimiento, puede ser necesario desnormalizar ligeramente la estructura de la base de datos para optimizar el rendimiento de las consultas.

Al comprender y aplicar los principios de diseño y normalización, los diseñadores de bases de datos pueden crear sistemas robustos que manejen los datos de manera eficaz y eficiente.
[Database normalization](https://www.freecodecamp.org/news/database-normalization-1nf-2nf-3nf-table-examples/)
