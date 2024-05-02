# Introducción a SQL con Snowflake

¡Bienvenido al mundo de SQL usando Snowflake! Esta guía te introducirá a los conceptos básicos de SQL y cómo utilizar Snowflake para gestionar y consultar datos.

## ¿Qué es SQL?
SQL (Lenguaje de Consulta Estructurada) es un lenguaje de programación estándar diseñado específicamente para gestionar datos almacenados en un sistema de gestión de bases de datos relacionales. Se utiliza para tareas como consultar, actualizar y gestionar datos.

## ¿Por qué Snowflake?
Snowflake es una plataforma de almacenamiento de datos basada en la nube que admite una amplia gama de características estándar de SQL. Su arquitectura única permite una escalabilidad, concurrencia y flexibilidad fáciles en el procesamiento y análisis de datos.

# Configuración de Snowflake

Para comenzar nuestro viaje con SQL y la gestión de datos, es esencial configurar una cuenta de Snowflake y familiarizarse con la Interfaz Web de Snowflake. Snowflake es una plataforma de datos basada en la nube que proporciona potentes capacidades de almacenamiento de datos y análisis.

## Creación de una Cuenta en Snowflake

Si aún no tienes una cuenta de Snowflake, sigue estos pasos:

1. **Visita el Sitio Web de Snowflake**: Ve al [sitio oficial de Snowflake](https://www.snowflake.com/).

2. **Regístrate para Obtener una Cuenta**: Busca la opción para registrarte o iniciar una prueba gratuita. Snowflake a menudo ofrece un período de prueba gratuito, que es excelente para comenzar.

3. **Completa el Registro**: Rellena los detalles requeridos como tu correo electrónico, nombre de la empresa (si aplica) y otra información necesaria.

4. **Verificación**: Después del registro, puede que necesites verificar tu dirección de correo electrónico para activar tu cuenta.

5. **Iniciar Sesión**: Una vez que tu cuenta esté configurada y verificada, inicia sesión para acceder a la Interfaz Web de Snowflake.

## Acceso a la Interfaz Web de Snowflake

La Interfaz Web de Snowflake es donde interactuarás con tu instancia de Snowflake. Es un entorno amigable donde puedes ejecutar consultas SQL, crear bases de datos y gestionar tus datos.

1. **Navega a la Interfaz Web**: Utiliza el enlace proporcionado durante la configuración de tu cuenta o ve a la [página de inicio de sesión de Snowflake](https://app.snowflake.com/).

2. **Introduce tus Credenciales**: Inicia sesión con tu nombre de usuario y contraseña de Snowflake.

## Creación de una Base de Datos y un Esquema en Snowflake

Una vez que hayas iniciado sesión, el siguiente paso es crear una base de datos y un esquema. Aquí es donde se almacenarán y organizarán tus datos.

1. **Iniciar Sesión en Snowflake**: Si aún no has iniciado sesión, ingresa a la Interfaz Web de Snowflake con tus credenciales.

2. **Crear Base de Datos**:
    Ejecuta el siguiente comando SQL en la interfaz de Snowflake para crear una nueva base de datos llamada 'ironhack_dapt'.

    ```sql
    CREATE DATABASE ironhack_dapt;
    ```

    Este comando crea una nueva base de datos donde puedes almacenar y gestionar tus datos.

3. **Crear Esquema**:
    En la base de datos 'ironhack_dapt' recién creada, crea un esquema llamado 'ironhack_class'.

    ```sql
    USE DATABASE ironhack_dapt;
    CREATE SCHEMA ironhack_class;
    ```

    Un esquema es como una carpeta dentro de tu base de datos. Ayuda a organizar y segregar diferentes tablas y objetos de datos.

Con tu cuenta de Snowflake configurada y tu base de datos y esquema listos, estás preparado para comenzar a crear tablas y explorar consultas SQL.

# Creación de Tablas en Snowflake

En esta sección, nos centraremos en crear tablas en Snowflake, que constituyen la base para almacenar y gestionar datos en una base de datos. Una tabla en una base de datos es similar a una tabla en una hoja de cálculo; almacena datos en filas y columnas. Cada tabla contiene datos sobre un tema particular, como clientes, productos o ventas.

Crear tablas es un primer paso crucial en la gestión de bases de datos. Implica definir el nombre de la tabla, las columnas que contiene y el tipo de datos que cada columna mantendrá. Esta estructura nos ayuda a organizar los datos de manera eficiente y permite la recuperación y manipulación efectiva de datos.

Para nuestra clase, crearemos tablas correspondientes a los conjuntos de datos proporcionados. Estos conjuntos de datos representan diferentes aspectos de un entorno empresarial típico, como información del cliente, detalles del producto, registros de ventas y más. Al crear tablas para cada conjunto de datos, tendremos una base de datos bien estructurada que imita escenarios de datos del mundo real.

Comenzaremos creando una tabla para cada conjunto de datos, especificando los tipos de datos apropiados para cada columna y asegurando que la estructura se alinee con los datos que tenemos. Una vez que estas tablas estén configuradas, exploraremos cómo insertar, actualizar, consultar y gestionar los datos dentro de ellas.

Comencemos creando nuestra primera tabla en Snowflake.

## Crear la Tabla de Clientes

Para crear la tabla 'Customer' en el esquema 'ironhack_class', utiliza el siguiente comando:

    ```sql
    USE SCHEMA ironhack_dapt.ironhack_class;
    CREATE TABLE Customer (
        CustomerID VARCHAR(50),
        CustomerName VARCHAR(100),
        Segment VARCHAR(50),
        Age INT,
        Country VARCHAR(50),
        City VARCHAR(50),
        State VARCHAR(50),
        PostalCode INT,
        Region VARCHAR(50)
    );
    ```

## Crear la Tabla de Productos

Usa este comando para crear la tabla 'Product' en el esquema 'ironhack_class'.

    ```sql
    CREATE TABLE Product (
        ProductID VARCHAR(50),
        Category VARCHAR(50),
        SubCategory VARCHAR(50),
        ProductName VARCHAR(200)
    );
    ```
## Crear la Tabla de Ventas

Aquí está el comando SQL para crear la tabla 'Sales':

    ```sql
    CREATE TABLE Sales (
        OrderLine INT,
        OrderID VARCHAR(50),
        OrderDate DATE,
        ShipDate DATE,
        ShipMode VARCHAR(50),
        CustomerID VARCHAR(50),
        ProductID VARCHAR(50),
        Sales DECIMAL,
        Quantity INT,
        Discount DECIMAL,
        Profit DECIMAL
    );
    ```

## Crear la Tabla de Estudiantes

Para crear la tabla 'Student', utiliza este comando:

    ```sql
    CREATE TABLE Student (
        EnrollmentNO INT,
        Name VARCHAR(100),
        ScienceMarks INT
    );
    ```

# Comprensión de las Primary y Foreign keys en SQL

En esta sección, profundizamos en los conceptos de Claves Primarias y Claves Foráneas, componentes esenciales de las bases de datos relacionales. Estas claves juegan un papel crucial en el mantenimiento de la integridad de los datos y el establecimiento de relaciones entre tablas.

## Claves Primarias

Una clave primaria identifica de manera única cada fila en una tabla. Es crucial para garantizar la unicidad de los registros y juega un papel vital en la indexación de la base de datos.

### Características de las Claves Primarias
- **Unicidad**: Ninguna fila puede tener el mismo valor de clave primaria.
- **No Nulidad**: Una clave primaria no puede ser NULL.

### Ejemplo en Contexto
En nuestra tabla 'Customer', la columna `CustomerID` sirve como la clave primaria. Cada cliente tiene un ID único.

```plaintext
| Customer ID | First Name | Last Name | Age |
|-------------|------------|-----------|-----|
| V_001       | Jay        | Pee       | 23  |
| V_002       | Kay        | Qu        | 23  |
| ...         | ...        | ...       | ... |
```


## Foreign Keys

Las claves foráneas establecen un vínculo crucial entre dos tablas en una base de datos relacional. Se refieren a la clave primaria en otra tabla, creando una relación entre las dos. Esta relación es fundamental para mantener la integridad referencial de tus datos.

### Ejemplo en Contexto
Considera la tabla 'Order' en nuestra base de datos. El campo `CustomerID` en esta tabla es una clave foránea que se refiere al `CustomerID` en la tabla 'Customer'. Esta conexión nos permite entender qué cliente realizó cada pedido.

```plaintext
| Order ID | Customer_ID | Product_key | Value |
|----------|-------------|-------------|-------|
| O_001    | V_001       | P_001_01    | 65    |
| O_002    | V_001       | P_001_02    | 23    |
| ...      | ...         | ...         | ...   |
```

En esta estructura, `Customer_ID` en la tabla 'Order' vincula cada pedido a un cliente específico en la tabla 'Customer', facilitando consultas que combinan datos de ambas tablas.

## Comprensión de las Relaciones entre Tablas

En las bases de datos relacionales, la forma en que las tablas están relacionadas entre sí es crucial para diseñar esquemas de bases de datos eficientes y escribir consultas SQL efectivas.

### Tipos de Relaciones
- **Uno a Uno**: Cada fila en una tabla corresponde exactamente a una fila en otra tabla. Esta relación es menos común pero importante en ciertos escenarios.
- **Uno a Muchos**: Una sola fila en una tabla puede corresponder a múltiples filas en otra tabla. Este es un tipo de relación muy común en las bases de datos.
- **Muchos a Muchos**: Las filas en una tabla pueden relacionarse con múltiples filas en otra tabla y viceversa. Típicamente, esta relación requiere una tabla intermedia para gestionar efectivamente las conexiones.

## Aplicación en Snowflake

La plataforma de Snowflake admite la definición y uso de claves primarias y foráneas, que son fundamentales para definir relaciones entre tablas.

### Claves Primarias y Foráneas en Snowflake
- Aunque Snowflake permite definir claves primarias y foráneas, no aplica restricciones de clave foránea. Esto significa que Snowflake no te impedirá ingresar datos inconsistentes.
- A pesar de esto, es crucial entender y usar estas claves para mantener la integridad de los datos y para escribir consultas efectivas, especialmente al realizar uniones entre tablas.

## Puntos Clave

- **Claves Primarias**: Esenciales para identificar de manera única cada fila en una tabla. Son la piedra angular de la integridad de la tabla.
- **Claves Foráneas**: Establecen relaciones entre tablas y son cruciales para las uniones en consultas SQL. Ayudan a mantener la integridad de los datos relacionales.
- **Comprensión de las Relaciones**: Comprender los conceptos de claves primarias y foráneas, y los tipos de relaciones que facilitan, es clave para entender cómo los datos están estructurados e interconectados en las bases de datos relacionales.

Apreciar estos conceptos te empoderará para diseñar esquemas de bases de datos más efectivos y escribir consultas SQL más eficientes, especialmente en una plataforma como Snowflake.

## Introducción a las Consultas SQL

SQL, o Lenguaje de Consulta Estructurada, es una herramienta poderosa utilizada en el mundo de la gestión y análisis de datos. Como el lenguaje estándar para interactuar con bases de datos relacionales, SQL te permite realizar de manera eficiente varias operaciones sobre los datos almacenados en bases de datos. En el ámbito de las plataformas de almacenamiento de datos en la nube como Snowflake, SQL juega un papel fundamental en la recuperación y manipulación de datos.

### ¿Qué es SQL?

SQL es un lenguaje específico de dominio utilizado en programación y gestión de datos almacenados en un sistema de gestión de bases de datos relacionales (RDBMS). Es particularmente útil para manejar datos estructurados, donde existen relaciones entre diferentes entidades/variables de los datos.

#### Características Clave de SQL
- **Versatilidad**: SQL se utiliza para consultar, insertar, actualizar y eliminar datos, lo que lo hace increíblemente versátil para diversas operaciones de datos.
- **Interactividad**: SQL permite la interacción en tiempo real con la base de datos, lo que permite obtener feedback y resultados inmediatos.
- **Estandarización**: SQL está estandarizado, lo que significa que sus comandos básicos se utilizan en diversos sistemas de bases de datos con mínimas variaciones.

### ¿Por qué SQL en Snowflake?

Snowflake es una plataforma de datos basada en la nube que ofrece una amplia gama de características para el almacenamiento, procesamiento y análisis de datos. Usar SQL en Snowflake te permite:

- Acceder y analizar grandes volúmenes de datos de manera eficiente.
- Aprovechar la potencia de cómputo de Snowflake para realizar consultas complejas.
- Utilizar la arquitectura única de Snowflake, que separa el almacenamiento y el cálculo, permitiendo un procesamiento de datos escalable y rentable.

## Sentencias SELECT: La Puerta de Entrada a la Recuperación de Datos

La sentencia SELECT es un componente fundamental de SQL, utilizado principalmente para la recuperación de datos de una base de datos. Es la herramienta más básica pero poderosa en SQL para consultar y extraer datos.

### Comprensión de las Sentencias SELECT

- **Propósito**: La sentencia SELECT se utiliza para seleccionar datos específicos de una o más tablas en una base de datos.
- **Flexibilidad**: Puedes optar por extraer todas las columnas de una tabla o especificar columnas particulares.
- **Combinación con Otras Cláusulas**: Las sentencias SELECT pueden combinarse con varias cláusulas (como WHERE, JOIN, ORDER BY) para refinar y personalizar la recuperación de datos.

### Sintaxis Básica

```sql
SELECT column_name1, column_name2 FROM table_name;
```

### Ejemplos
Seleccion un sola columna:
```sql
SELECT first_name FROM customer_table;
```
Selecciona multiples columnas:
```sql
SELECT first_name, last_name FROM customer_table;
```
Seleccion todas las columnas:
```sql
SELECT * FROM customer_table;
```

## Uso de DISTINCT

En SQL, la palabra clave `DISTINCT` juega un papel crucial en las operaciones de recuperación de datos, especialmente cuando necesitas eliminar entradas duplicadas en tu conjunto de resultados. Asegura que los resultados devueltos por tu consulta sean únicos, proporcionando claridad y precisión en el análisis de datos.

### ¿Qué es DISTINCT?

La palabra clave `DISTINCT` se usa junto con la sentencia `SELECT` en SQL. Su propósito principal es eliminar registros duplicados del conjunto de resultados y devolver solo entradas únicas.

### Características Clave de DISTINCT
- **Eliminación de Duplicados**: `DISTINCT` asegura que cada fila en tu conjunto de resultados sea diferente de todas las demás.
- **Mejora de la Claridad de los Datos**: Al eliminar duplicados, ofrece una vista más clara de los datos, lo que es particularmente útil en análisis y reportes.
- **Aplicabilidad**: Se puede aplicar a una o más columnas en tu consulta SQL.

### Sintaxis Básica
La sintaxis para usar DISTINCT es directa. Se coloca inmediatamente después de la palabra clave `SELECT`.

### Sintaxis

```sql
SELECT DISTINCT column_name FROM table_name;
```

### Ejemplo
Seleccionando valores distintos de una columna:
```sql
SELECT DISTINCT customer_name FROM customer_table;
```
Seleccionando valores distintos de multiples columna:
```sql
SELECT DISTINCT customer_name, age FROM customer_table;
```

## La Cláusula WHERE

La cláusula `WHERE` en SQL es una herramienta poderosa para filtrar datos. Te permite especificar condiciones que los datos deben cumplir para ser incluidos en los resultados de la consulta. Esta cláusula es esencial para refinar la recuperación de tus datos y hacer tus consultas más precisas.

### ¿Qué es la Cláusula WHERE?

En SQL, la cláusula `WHERE` se utiliza para filtrar registros de una tabla, una vista o una unión, basado en condiciones especificadas. Ayuda a reducir los datos que deseas recuperar o manipular.

#### Funcionalidad de la Cláusula WHERE
- **Filtrado Basado en Condiciones**: Solo las filas que cumplen con las condiciones especificadas son devueltas en el conjunto de resultados.
- **Mayor Precisión en las Consultas**: Al usar la cláusula `WHERE`, puedes evitar recuperar datos innecesarios, haciendo tus consultas más eficientes y tus resultados más relevantes.

### Sintaxis Básica
La cláusula `WHERE` sigue a la cláusula `FROM` en una declaración `SELECT`.

### Sintaxis
```sql
SELECT column_name FROM table_name WHERE condition;
```

### Ejemplo
Seleccionando con una condición:

```sql
SELECT first_name FROM customer_table WHERE age = 25;
```

## Operadores AND, OR y NOT

En SQL, los operadores AND, OR y NOT son esenciales para crear condiciones de consulta más complejas. Estos operadores lógicos te permiten combinar, negar o refinar múltiples condiciones en tus consultas, ofreciendo un mayor grado de control sobre los datos que recuperas.

### El Papel de los Operadores Lógicos

Los operadores lógicos en SQL se utilizan para mejorar las capacidades de la cláusula WHERE, permitiendo un filtrado de datos más sofisticado. Aquí hay una breve descripción de cada uno:

- **AND**: Utilizado para combinar múltiples condiciones, donde cada condición dentro del AND debe ser verdadera para que la fila sea incluida en el conjunto de resultados.
- **OR**: Utilizado para combinar múltiples condiciones, donde al menos una de las condiciones debe ser verdadera para que la fila sea incluida.
- **NOT**: Utilizado para negar una condición, lo que significa que se considera la condición opuesta a lo que se afirma.

### Uso de AND, OR y NOT en Consultas

#### Operador AND

El operador AND se utiliza cuando deseas recuperar registros que satisfacen todas las condiciones dadas.

### Sintaxis
Uso de AND:

```sql
SELECT column_name FROM table_name WHERE condition1 AND condition2;
```
Usando OR:
```sql
SELECT column_name FROM table_name WHERE condition1 OR condition2;
```
Usando NOT:
```sql
SELECT column_name FROM table_name WHERE NOT condition;
```

### Ejemplo
Usando AND para combinar condiciones:
```sql
SELECT first_name, last_name FROM customer_table WHERE age > 20 AND age < 30;
```
Usando OR para expandir condiciones:
```sql
SELECT first_name, last_name FROM customer_table WHERE age < 20 OR age > 30;
```
Usando NOT para negar condiciones:
```sql
SELECT first_name, last_name FROM customer_table WHERE NOT age = 25;
```

## Sentencia INSERT INTO

La sentencia `INSERT INTO` es una parte fundamental de SQL, utilizada para agregar nuevos registros (filas) a una tabla en una base de datos. Comprender cómo usar esta sentencia es crucial para gestionar y actualizar los datos en tus bases de datos.

### ¿Qué es la Sentencia INSERT INTO?

La sentencia `INSERT INTO` te permite insertar nuevos datos en una tabla. Cada fila en una tabla representa un registro, y con `INSERT INTO`, puedes agregar nuevos registros con valores especificados en las columnas.

#### Características Clave de INSERT INTO
- **Flexibilidad**: Puedes elegir insertar valores en todas las columnas o especificar en qué columnas insertar.
- **Integridad de los Datos**: Al insertar datos, es importante asegurar que los nuevos datos cumplan con las restricciones establecidas en el esquema de la tabla (como tipos de datos, restricciones NOT NULL, etc.).

### Sintaxis Básica
La sintaxis básica de la sentencia `INSERT INTO` varía ligeramente dependiendo de si estás insertando datos en todas las columnas o en columnas específicas.

### Sintaxis

```sql
INSERT INTO table_name (column1, column2) VALUES (value1, value2);
```

### Ejemplo
- Inserting una sola columna:
```sql
INSERT INTO customer_table (cust_id, first_name, age, email_id) VALUES (2, 'Dee', 22, 'd@xyz.com');
```
Insertando multples columnas:
```sql
INSERT INTO customer_table VALUES (1, 'Ee', 'Ef', 35, 'ef@xyz.com'), (1, 'Gee', 'Eh', 42, 'gh@xyz.com');
```
## Sentencia ALTER TABLE

La sentencia `ALTER TABLE` en SQL es un comando versátil utilizado para modificar la estructura de una tabla existente de diversas maneras. Te permite adaptar la estructura de la tabla a medida que cambian tus requisitos de datos con el tiempo.

La sentencia `ALTER TABLE` es esencial para cambiar la definición o estructura de una tabla sin necesidad de eliminarla y recrearla. Esta capacidad es crucial para mantener y actualizar bases de datos de manera dinámica.

### Sintáxis Básica
```sql
ALTER TABLE table_name
[Specify Actions];
```
### Acciones Posibles
- **Columnas**: Añadir, eliminar, modificar o renombrar columnas.
- **Restricciones**: Añadir o eliminar restricciones como NOT NULL, CHECK o FOREIGN KEY.
- **Índice**: Añadir o eliminar índices (no cubierto en esta conferencia).

### Modificar Columnas

#### Añadir una Columna
Para añadir una nueva columna a una tabla, especificas el nombre de la columna y su tipo de datos.

##### Sintaxis

```sql
ALTER TABLE table_name
ADD column_name Data_Type;
```
#### Eliminar una Columna
Para eliminar una columna de una tabla, especificas el nombre de la columna.

##### Sintaxis
```sql
ALTER TABLE table_name
DROP column_name;
```
### Modificar y Renombrar Columnas

#### Modificar el Tipo de Datos de una Columna
Para cambiar el tipo de datos de una columna, especificas la columna y el nuevo tipo de datos.

##### Sintaxis
```sql
ALTER TABLE table_name
ALTER COLUMN column_name TYPE New_Data_Type;
```
#### Renombrar una Columna
Para renombrar una columna, especificas el nombre actual de la columna y el nuevo nombre.

##### Sintaxis
```sql
ALTER TABLE table_name
RENAME COLUMN column_1 TO column_2;
```
### Añadir y Eliminar Restricciones

#### Establecer una Restricción NOT NULL
Para exigir que una columna no pueda tener valores NULL, usa la restricción SET NOT NULL.

##### Sintaxis
```sql
ALTER TABLE table_name ALTER COLUMN column_name SET NOT NULL;
```
#### Eliminar una Restricción NOT NULL
Para eliminar una restricción NOT NULL de una columna, utiliza DROP NOT NULL.

##### Sintaxis
```sql
ALTER TABLE table_name ALTER COLUMN column_name DROP NOT NULL;
```
#### Añadir una Restricción CHECK
Para añadir una condición que los datos en una columna deben cumplir, utiliza la restricción CHECK.

##### Sintaxis
```sql
ALTER TABLE table_name ADD CONSTRAINT column_name CHECK (column_name >= 100);
```
#### Establecer una Clave Primaria
Para designar una columna como clave primaria, utiliza la siguiente sintaxis.

##### Sintaxis
```sql
ALTER TABLE table_name ADD PRIMARY KEY (column_name);
```

### Añadir una Restricción de Clave Extranjera
Para crear una relación de clave extranjera con otra tabla, utiliza la restricción FOREIGN KEY.

#### Sintaxis

```sql
ALTER TABLE child_table ADD CONSTRAINT child_column
FOREIGN KEY (parent_column) REFERENCES parent_table;
```
## Sentencia IN
La condición `IN` en SQL es una herramienta poderosa para especificar múltiples valores en una cláusula `WHERE`. Es especialmente útil para simplificar consultas que de otro modo requerirían múltiples condiciones `OR`.
La condición `IN` en SQL te permite especificar una lista de valores con los cuales una columna puede coincidir para ser incluida en los resultados. Es una abreviatura de una serie de condiciones `OR`, haciendo que tus consultas sean más concisas y legibles.

### Sintaxis Básica de IN
```sql
SELECT column_name FROM table_name WHERE column_name IN (value1, value2, ...);
```

### Ejemplo de Uso de IN

**Condición Simple IN**:
```sql
SELECT * FROM customer WHERE city IN ('Philadelphia', 'Seattle');
```
Esta consulta selecciona todos los registros de la tabla `customer` donde la columna `city` tiene un valor de 'Philadelphia' o 'Seattle'.

### Beneficios de Usar IN
- **Simplicidad**: Reduce la complejidad en consultas que requerirían múltiples condiciones `OR`.
- **Legibilidad**: Hace que la consulta sea más legible y fácil de entender.
- **Eficiencia**: En algunos casos, usar `IN` puede ser más eficiente que usar múltiples condiciones `OR`.

## Cuándo Usar la Condición IN

- **Filtrado sobre Múltiples Valores**: Usa `IN` cuando necesites filtrar una columna sobre una lista de múltiples valores específicos.
- **Sustitución de Múltiples Condiciones OR**: Reemplaza múltiples condiciones `OR` con una cláusula `IN` para un código SQL más limpio y manejable.

### Comparación con Condiciones OR

La condición `IN` es funcionalmente similar a usar múltiples condiciones `OR`, pero con una mejora en la legibilidad y simplicidad. Por ejemplo:

### Usando OR

```sql
SELECT * FROM customer WHERE city = 'Philadelphia' OR city = 'Seattle';
```
### Usando IN
```sql
SELECT * FROM customer WHERE city IN ('Philadelphia', 'Seattle');
```
Ambas consultas producen el mismo resultado, pero la condición `IN` simplifica la consulta.

## Sentencia BETWEEN

La condición `BETWEEN` en SQL es una herramienta valiosa para filtrar registros basados en un rango de valores. Simplifica la sintaxis para especificar un rango en las consultas, haciendo tus declaraciones SQL más legibles y eficientes.

La condición `BETWEEN` te permite seleccionar datos que caen dentro de un rango especificado. Esto puede ser valores numéricos, valores de texto (basados en el orden alfabético) o fechas. Es un rango inclusivo, lo que significa que incluye los valores de inicio y fin especificados.

### Sintaxis Básica de BETWEEN

```sql
SELECT column_name FROM table_name WHERE column_name BETWEEN value1 AND value2;
```

### Ejemplos de Uso de BETWEEN
- **Rango Numérico**:
  ```sql
  SELECT * FROM customer WHERE age BETWEEN 20 AND 30;
  ```
Esta consulta devolverá todos los clientes cuya edad esté entre 20 y 30 años, incluyendo aquellos que tienen exactamente 20 o 30 años.

- **Rango de Fechas**:
  ```sql
  SELECT * FROM sales WHERE ship_date BETWEEN '2015-04-01' AND '2016-04-01';
  ```
Esta consulta recupera todos los registros de ventas con una fecha de envío entre el 1 de abril de 2015 y el 1 de abril de 2016.

### Usando NOT con BETWEEN
También puedes usar `NOT BETWEEN` para excluir un rango de valores.

#### Ejemplo
```sql
SELECT * FROM customer WHERE age NOT BETWEEN 20 AND 30;
```
Esta consulta devolverá clientes que tienen menos de 20 años o más de 30 años.

### Comparando BETWEEN con Operadores Estándar
La condición `BETWEEN` es equivalente a una combinación de los operadores `>=` y `<=`. Por ejemplo:

```sql
SELECT * FROM customer WHERE age BETWEEN 20 AND 30;
```

Es lo mismo que:

```sql
SELECT * FROM customer WHERE age >= 20 AND age <= 30;
```

### Beneficios de Usar BETWEEN
- **Simplicidad**: Reduce la complejidad de las consultas que involucran rangos.
- **Legibilidad**: Mejora la legibilidad de las consultas SQL, haciéndolas más fáciles de entender y mantener.
- **Versatilidad**: Puede usarse con varios tipos de datos, incluyendo números, fechas y cadenas.

## Sentencia LIKE

La condición `LIKE` en SQL es una herramienta increíblemente útil para realizar coincidencias de patrones en consultas. Es especialmente útil cuando quieres buscar datos con patrones específicos dentro de una columna.

La condición `LIKE` en SQL se utiliza para coincidencia de patrones y se emplea en una cláusula `WHERE` para buscar un patrón especificado en una columna.

### Sintaxis Básica de LIKE
```sql
SELECT column_name FROM table_name WHERE column_name LIKE pattern;
```

### Comodines en LIKE
Los comodines son caracteres especiales utilizados en la condición `LIKE` para representar uno o más caracteres en la coincidencia de patrones. Los comodines más utilizados son `%` y `_`.

- **Comodín %**: Representa cualquier secuencia de caracteres (incluyendo cero caracteres).
  - `A%` significa cualquier cadena que comience con 'A'.
  - `%A` significa cualquier cadena que termine con 'A'.
  - `A%B` significa cualquier cadena que comience con 'A' y termine con 'B'.

- **Comodín _**: Representa un único caracter.
  - `AB_C` significa cualquier cadena que comience con 'AB', seguido de cualquier caracter, y luego 'C'.

### Ejemplos de Uso de LIKE
**Comenzando con un Patrón Específico**:

```sql
SELECT * FROM customer_table WHERE first_name LIKE 'Jo%';
```
Esta consulta encontrará todos los registros donde el nombre comienza con 'Jo'.

**Conteniendo un Patrón Específico**:
```sql
SELECT * FROM customer_table WHERE first_name LIKE '%od%';
```
Esta consulta encontrará todos los registros donde el nombre contiene 'od'.

**Coincidencia con un Patrón Específico con un Solo Carácter**:
```sql
SELECT first_name, last_name FROM customer_table WHERE first_name LIKE 'Jas_n';
```
Esta consulta encontrará los registros donde el nombre coincide con el patrón 'Jas' seguido de cualquier carácter, y luego 'n'.

**Excluyendo un Patrón Específico**:
```sql
SELECT first_name, last_name FROM customer_table WHERE last_name NOT LIKE 'J%';
```
Esta consulta encontrará todos los registros donde el apellido no comienza con 'J'..

**Los Wildcards**:
```sql
SELECT * FROM customer_table WHERE last_name LIKE 'G\%';
```
Esta consulta encontrará todos los registros donde el apellido realmente comienza con 'G%'..

## Declaración de ORDER BY

La cláusula `ORDER BY` en SQL es una herramienta esencial para ordenar los registros en su conjunto de resultados. Se puede utilizar junto con las declaraciones `SELECT` para organizar los datos recuperados en un orden específico, ya sea ascendente o descendente.

La cláusula `ORDER BY` permite ordenar los datos devueltos por una consulta `SELECT` en orden ascendente (ASC) o descendente (DESC) basado en una o más columnas. Por defecto, `ORDER BY` ordena los datos en orden ascendente.

### Sintaxis Básica de ORDER BY

```sql
SELECT column_name FROM table_name [WHERE condition] ORDER BY column_name [ASC | DESC];
```

### Ordenar por Múltiples Columnas
Es posible ordenar datos basándose en más de una columna. Esto proporciona un ordenamiento multinivel donde los datos se ordenan primero por la primera columna, luego por la segunda y así sucesivamente.

#### Sintaxis para Múltiples Columnas

```sql
ORDER BY column_name1 [ASC | DESC], column_name2 [ASC | DESC];
```

### Ejemplos de Uso de ORDER BY
**Ordenando por una Columna Individual**:

```sql
SELECT * FROM customer WHERE state = 'California' ORDER BY Customer_name;
```
Esta consulta ordena a los clientes de California por sus nombres en orden ascendente (por defecto).

**Ordenando por Múltiples Columnas**:

```sql
SELECT * FROM customer WHERE age > 25 ORDER BY City ASC, Customer_name DESC;
```
Esta consulta ordena a los clientes mayores de 25 años primero por ciudad en orden ascendente y luego por nombre en orden descendente dentro de cada ciudad.

**Ordenando en Orden Descendente**:
```sql
SELECT * FROM customer ORDER BY age DESC;
```
Esta consulta ordena a todos los clientes por edad en orden descendente.

### Consejos para Usar ORDER BY
- **Orden Predeterminado**: Si no especificas ASC o DESC, el orden es ascendente por defecto.
- **Posición de la Columna**: También puedes usar posiciones de columnas en lugar de nombres, por ejemplo, `ORDER BY 1` ordenaría por la primera columna en la lista de selección.
- **Consideraciones de Rendimiento**: Ordenar puede ser intensivo en recursos, especialmente para grandes conjuntos de datos. Es importante usar `ORDER BY` con prudencia para asegurar un rendimiento eficiente de la consulta.

# Declaración de LIMIT

La declaración `LIMIT` en SQL es una herramienta simple pero poderosa para controlar el número de registros devueltos por una consulta. Esta característica es particularmente útil para gestionar grandes conjuntos de datos y optimizar el rendimiento de las consultas.

La declaración `LIMIT` restringe el número de filas devueltas por una consulta. Es especialmente útil cuando necesitas trabajar con un subconjunto de datos o al implementar características como la paginación en aplicaciones.

### Sintaxis Básica de LIMIT

```sql
SELECT column_names FROM table_name [WHERE conditions] [ORDER BY expression [ASC | DESC]] LIMIT row_count;
```
### Ejemplos de Uso de LIMIT
**Limitando el Número de Registros**:

```sql
SELECT * FROM customer WHERE age >= 25 ORDER BY age DESC LIMIT 8;
```
Esta consulta devolverá los 8 clientes más mayores que tengan al menos 25 años, ordenados en orden descendente por edad.

**Combinando LIMIT con ORDER BY**:
```sql
SELECT * FROM customer WHERE age >= 25 ORDER BY age ASC LIMIT 10;
```
Esta consulta devolverá los 10 clientes más jóvenes que tengan al menos 25 años, ordenados en orden ascendente por edad.

### Beneficios de Usar LIMIT
- **Rendimiento**: Reduce la carga en la base de datos limitando el número de filas procesadas y devueltas.
- **Eficiencia**: Útil para probar rápidamente consultas o cuando solo necesitas un número específico de filas.
- **Practicidad**: Esencial para implementar la paginación en aplicaciones que muestran grandes conjuntos de datos.

### Consejos para Usar LIMIT
- **Ordenación**: Combina `LIMIT` con `ORDER BY` para controlar qué subconjunto de filas se devuelve.
- **Pruebas**: Usa `LIMIT` para probar consultas en tablas grandes sin procesar toda la tabla.
- **Paginación**: Implementa la paginación en tus aplicaciones utilizando `LIMIT` con un desplazamiento.

## Declaración AS

La palabra clave `AS` en SQL es una característica simple pero poderosa que te permite asignar alias a columnas o tablas. Esto puede hacer que tus consultas sean más legibles y puede ser particularmente útil en consultas complejas que involucran múltiples tablas o subconsultas.

La palabra clave `AS` se utiliza para renombrar una columna o tabla dentro del alcance de una consulta SQL específica. Este cambio de nombre se conoce como alias y no afecta los nombres reales de las tablas o columnas en la base de datos.

### Sintaxis Básica de AS
```sql
SELECT column_name AS column_alias FROM table_name;
```

### Ejemplos de Uso de AS
**Asignando un Alias a una Columna**:

```sql
SELECT Cust_id AS 'Serial number', Customer_name AS name, Age AS Customer_age FROM Customer;
```
Esta consulta renombra la columna `Cust_id` como 'Número de serie', `Customer_name` como 'nombre' y `Age` como 'Edad del cliente' en la salida.

### Beneficios de Usar Alias
- **Claridad**: Hace que las consultas complejas sean más comprensibles, especialmente cuando las columnas o tablas tienen nombres largos o técnicos.
- **Necesidad en Uniones**: Esencial cuando se unen tablas con nombres de columnas que se superponen para evitar ambigüedad.
- **Formateo de Resultados**: Útil para formatear la salida de una consulta con fines de informe.

### Consejos para Usar AS
- **Legibilidad**: Elige alias que hagan claro el propósito de la consulta.
- **Sintaxis Opcional**: La palabra clave `AS` es opcional. Puedes simplemente usar el nombre del alias junto al nombre de la columna o tabla.
- **Sin Cambio Permanente**: Recuerda que usar un alias no cambia el nombre real de la columna o tabla en la base de datos; es solo para el ámbito de la consulta.

## Declaración COUNT

La función `COUNT` en SQL es una función agregada fundamental y ampliamente utilizada que devuelve el conteo de una expresión, típicamente el número de filas que coinciden con una condición específica.

La función `COUNT` se utiliza para determinar el número de filas en una tabla que satisfacen ciertos criterios. Se puede aplicar a cualquier columna, así como a toda la tabla, y es especialmente útil en análisis de datos e informes.

### Sintaxis Básica de COUNT
```sql
SELECT COUNT(column_name) FROM table_name;
```

### Ejemplos de Uso de COUNT
**Contando Todas las Filas en una Tabla**:

```sql
SELECT COUNT(*) FROM sales;
```
Esta consulta devuelve el número total de filas en la tabla `sales`.

**Contando Filas Específicas Basadas en una Condición**:

```sql
SELECT COUNT(order_line) AS 'Number of Products Ordered', COUNT(DISTINCT order_id) AS 'Number of Orders' FROM sales WHERE customer_id = 'CG-12520';
```
This query counts the number of product orders and the distinct number of orders made by a specific customer.

Esta consulta cuenta el número de pedidos de productos y el número distinto de pedidos realizados por un cliente específico.

### Cuándo Usar COUNT
- **Análisis de Datos**: Para determinar el tamaño de un conjunto de datos o el número de registros que cumplen ciertos criterios.
- **Informes**: Útil en la generación de informes donde se requieren totales y subtotales.
- **Verificación de Datos**: Para verificar el número de entradas en tablas, especialmente después de operaciones de manipulación de datos como INSERT o DELETE.

### Consejos para Usar COUNT
- **Rendimiento**: Aunque `COUNT(*)` es a menudo eficiente, ten en cuenta el rendimiento al contar grandes conjuntos de datos, especialmente cuando se usa `COUNT` en columnas específicas con condiciones.
- **Uso con DISTINCT**: Combina `COUNT` con `DISTINCT` para contar valores únicos en una columna.
- **Combinación con Otras Funciones**: `COUNT` puede combinarse con otras funciones agregadas de SQL como `SUM`, `AVG`, para un análisis de datos más completo.

## Declaración SUM

La función `SUM` en SQL es una función agregada crucial utilizada para calcular la suma total de una columna numérica. Es especialmente valiosa en análisis de datos para resumir y agregar datos.

La función `SUM` te permite sumar todos los valores en una columna específica, proporcionando una suma total de esos valores. Esta función se puede aplicar a campos numéricos y a menudo se utiliza en conjunto con otras cláusulas de SQL como `WHERE` y `GROUP BY`.

### Sintaxis Básica de SUM
```sql
SELECT SUM(aggregate_expression) FROM tables [WHERE conditions];
```

### Ejemplos de Uso de SUM
**Calculando el Beneficio Total**:

```sql
SELECT SUM(Profit) AS 'Total Profit' FROM sales;
```
Esta consulta calcula el beneficio total de todas las ventas.

**Sumando Valores Específicos Basados en una Condición**:

```sql
SELECT SUM(quantity) AS 'Total Quantity' FROM orders WHERE product_id = 'FUR-TA-10000577';
```
Esta consulta calcula la cantidad total de un producto específico vendido.

### Cuándo Usar SUM
- **Análisis de Datos e Informes**: Para calcular totales para datos financieros, ventas, inventarios, etc.
- **Agregación de Datos**: Útil en la generación de informes y perspectivas donde se necesita datos agregados.
- **Combinación con Agrupación**: A menudo se utiliza con `GROUP BY` para resumir datos en subgrupos.

### Consejos para Usar SUM
- **Tipo de Datos**: Asegúrate de que la columna que estás sumando sea de un tipo de datos numérico.
- **Combinar con Otras Funciones**: `SUM` puede combinarse con otras funciones agregadas como `COUNT`, `AVG`, para un análisis de datos más completo.
- **Consideraciones de Rendimiento**: Ten en cuenta el rendimiento al sumar grandes conjuntos de datos o consultas complejas.

## Declaración AVG

La función `AVG` en SQL es una función agregada importante utilizada para calcular el valor promedio de una expresión especificada. Se utiliza ampliamente en análisis de datos para obtener perspectivas significativas de datos numéricos.

La función `AVG` calcula el valor promedio de un conjunto de números. Se aplica a una columna y devuelve la media de los valores numéricos en esa columna. Esta función puede ser particularmente útil en análisis financiero, datos estadísticos y otras áreas donde los promedios son importantes.

### Sintaxis Básica de AVG
```sql
SELECT AVG(aggregate_expression) FROM tables [WHERE conditions];
```
### Ejemplos de Uso de AVG
**Calculando la Edad Promedio**:

```sql
SELECT AVG(age) AS 'Average Customer Age' FROM customer;
```
Esta consulta calcula la edad promedio de los clientes.

**Calculando el Promedio Basado en un Valor Calculado**:

```sql
SELECT AVG(sales * 0.10) AS 'Average Commission Value' FROM sales;
```
Esta consulta calcula el valor promedio de la comisión, asumiendo que la comisión es el 10% de las ventas.

### Cuándo Usar AVG
- **Análisis de Tendencias**: Para entender las tendencias en los datos, como las ventas promedio durante un período o la edad promedio de los clientes.
- **Análisis Comparativo**: Para comparar promedios entre diferentes grupos o categorías.
- **Informes Financieros**: Esencial en escenarios financieros para calcular ingresos, costos o beneficios promedio.

### Consejos para Usar AVG
- **Solo Datos Numéricos**: La función `AVG` se aplica solo a tipos de datos numéricos.
- **Combinación con GROUP BY**: A menudo se usa en conjunto con `GROUP BY` para cálculos promedio segmentados.
- **Valores NULOS**: `AVG` excluye automáticamente los valores NULOS del cálculo.

## Declaración MIN & MAX

- **Propósito**: Las funciones `MIN()` y `MAX()` son herramientas esenciales en SQL, utilizadas para extraer los valores más pequeños y más grandes de una columna seleccionada en una tabla de base de datos. Estas funciones son particularmente útiles en varios escenarios, como identificar extremos en conjuntos de datos, como los salarios, precios o puntuaciones más altos o más bajos.

- **Función MIN()**: 
  - La función `MIN()` devuelve el valor más pequeño encontrado en una columna especificada.
  - Es útil para identificar el valor "más bajo" o "mínimo" en un rango de datos.
  - Los casos de uso comunes incluyen encontrar el precio más bajo de un producto, la fecha más temprana o el valor numérico más pequeño en un conjunto de datos.

- **Función MAX()**: 
  - En contraste, la función `MAX()` devuelve el valor más grande en una columna especificada.
  - Ayuda a determinar el valor "más alto" o "máximo".
  - Las aplicaciones típicas incluyen encontrar el salario más alto, la fecha más reciente o el valor numérico máximo.

### Sintaxis y Uso

```sql
-- Syntax for MIN function
SELECT MIN(column_name) FROM table_name;

-- Syntax for MAX function
SELECT MAX(column_name) FROM table_name;
```

- **Nota**: Ambas funciones se pueden usar en la misma consulta SQL y a menudo se utilizan en conjunto con otras cláusulas SQL como `WHERE` para filtrar resultados.

### Consultas de Ejemplo con Explicación

1. **Encontrando el Salario Mínimo y Máximo**
   Consulta para encontrar el salario más bajo y más alto en una tabla de `employees`:
   ```sql
   SELECT MIN(salary) AS MinSalary FROM employees;
   SELECT MAX(salary) AS MaxSalary FROM employees;
   ```
   Estas consultas examinarán la columna `salary` en la tabla `employees` y devolverán los valores más pequeño y más grande, respectivamente.

2. **Usando MIN & MAX con la Cláusula WHERE**
   Filtrando resultados por departamento para encontrar valores mínimos y máximos específicos:
   ```sql
   SELECT MIN(salary) FROM employees WHERE department = 'Sales';
   SELECT MAX(salary) FROM employees WHERE department = 'Sales';
   ```
Estas consultas devolverán los salarios más bajo y más alto, pero solo para los empleados del departamento de 'Ventas', demostrando cómo se pueden usar `MIN` y `MAX` con lógica condicional.

## Declaración GROUP BY

La cláusula `GROUP BY` es una herramienta poderosa en SQL utilizada en una declaración `SELECT` para agrupar filas que tienen los mismos valores en columnas especificadas. A menudo se utiliza con funciones agregadas (COUNT, MAX, MIN, SUM, AVG) para realizar cálculos en cada grupo de filas.

### Sintaxis de `GROUP BY`

```sql
SELECT column_name1, aggregate_function(column_name2)
FROM table_name
GROUP BY column_name1;
```

### Ejemplos de Uso de `GROUP BY`

1. **Contando Clientes en Cada Región**

   ```sql
   SELECT region, COUNT(customer_id) AS customer_count
   FROM customer
   GROUP BY region;
   ```

   Esta consulta cuenta el número de clientes en cada región.

2. **Sumando la Cantidad Vendida por Producto**

   ```sql
   SELECT product_id, SUM(quantity) AS quantity_sold
   FROM sales
   GROUP BY product_id
   ORDER BY quantity_sold DESC;
   ```
   Aquí, se suma la cantidad total vendida para cada producto.

3. **Agregando Datos de Ventas por Cliente**

   ```sql
   SELECT customer_id,
          MIN(sales) AS min_sales,
          MAX(sales) AS max_sales,
          AVG(sales) AS average_sales,
          SUM(sales) AS total_sales
   FROM sales
   GROUP BY customer_id
   ORDER BY total_sales DESC
   LIMIT 5;
   ```
Esta consulta proporciona una agregación completa de los datos de ventas para cada cliente, mostrando las ventas mínimas, máximas, promedio y totales.

## Declaración HAVING

La cláusula `HAVING` en SQL se usa en combinación con la cláusula `GROUP BY`. Permite especificar una condición para las filas agrupadas que devuelve la cláusula `GROUP BY`. La cláusula `HAVING` es particularmente útil para filtrar grupos basados en el resultado de una función agregada.

### Sintaxis de `HAVING`

```sql
SELECT ColumnNames, aggregate_function(expression)
FROM tables
[WHERE conditions]
GROUP BY column1
HAVING condition;
```

### Ejemplo de Uso de `HAVING`

**Filtrando Grupos Basados en una Condición**

```sql
SELECT region, COUNT(customer_id) AS customer_count
FROM customer
GROUP BY region
HAVING COUNT(customer_id) > 200;
```

Este ejemplo demuestra el uso de la cláusula `HAVING` para filtrar las regiones que tienen menos de 200 clientes. Agrupa los datos por región y cuenta el número de clientes en cada región, incluyendo solo aquellas regiones donde el conteo es mayor a 200.
