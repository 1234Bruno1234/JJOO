
# Normalización de Base de Datos de Laptops.

# Introduccion
#### Este repositorio contiene la documentacion necesaria para poder realizar la normalizacion de una Base de Datos a partir de un archivo CSV.
---------------------------------------------------------------------------------------------------------------
## Base de datos: Laptops
En esta base de datos encontraremos la informacion sobre las compañias, los nombre de los productos (Laptops), la ram, el Sistema Operativo, costo, GPU model, GPU company, CPU company, CPU model, etc. 

Elegimos esta base de datos porque nos parecio que era una muy completa y entretenida para normalizar. Comenzamos descargando la base de datos de la páguina Kaggle

Lo descargamos en un archivo CSV que es lo que te permite abrirlo en HeidiSQL.

## 1. Instalación

# Abrir HeidiSQL
Una vez abierto nuestro programa para base de datos, seguir las intrucciones para poder importarla correctamente.<p>
  Luego de haber entrado a nuestro lugar de trabajo, nos dirigimos a la parte superior izquierda donde se encuentra la ventana Herramientas, hacemos click y buscamos la opción de "Importar archivo CSV".<p>
![Importacion de datos](imagen/img/img1.jpg)

  Una vez abierto buscamos la carpeta y el archivo, nos dirigimos a la parte que dice base de datos y tabla, se creará la base de datos y apretamos el boton Importar.<p>

<h2><p>2. Uso</p></h2>

Una vez cargada la base de datos y creada todas las tablas, nos dirigiremos a la parte inferior para seguir los pasos y comprobar que funcione correctamente.

<h2>3. Diagrama de Relación de Entidad</h2> 

![Diagrama](imagen/laptop.png)

##4. CREACION DE TABLAS

<h2>Creamaos las tablas que usaremos en la base de datos a partir de la tabla principal.</h2>
  
### Creacion de la tabla compañia:
```sql
CREATE TABLE compañia ( com_code BIGINT PRIMARY KEY AUTO_INCREMENT NOT NULL,  com_nomb VARCHAR(50)); 
```

### Creacion de la tabla ram:
```sql    
CREATE TABLE ram (ram_code BIGINT PRIMARY KEY AUTO_INCREMENT NOT NULL,  
ram_tmño tinyint);
```

### Creacion de la tabla SO:
```sql    
CREATE TABLE so (sop_code BIGINT PRIMARY KEY AUTO_INCREMENT NOT NULL,  
sop_nomb VARCHAR(10));
```
### Creacion de la tabla Precio:
```sql  
CREATE TABLE precio (pre_code BIGINT PRIMARY KEY AUTO_INCREMENT NOT NULL, pre_cant BIGINT);
```

 ### Creacion de la tabla Comañia_CPU:
```sql
CREATE TABLE compañia_cpu (cpuc_code BIGINT PRIMARY KEY AUTO_INCREMENT NOT NULL,  cpuc_nomb VARCHAR(25));
```

### Creacion de la tabla Modelo_CPU:   
```sql
CREATE TABLE modelo_cpu (cpum_code BIGINT PRIMARY KEY AUTO_INCREMENT NOT NULL,  cpum_nomb VARCHAR(50));
```

### Creacion de la tabla Modelo_GPU:
```sql  
CREATE TABLE modelo_gpu (gpum_code BIGINT PRIMARY KEY AUTO_INCREMENT NOT NULL,  gpum_nomb VARCHAR(50));
```

### Creacion de la tabla Compañia_GPU: 
```sql
CREATE TABLE compañia_gpu (gpuc_code BIGINT PRIMARY KEY AUTO_INCREMENT NOT NULL,  gpuc_nomb VARCHAR(50));
```

# Importación de datos
#### Tabla compañia
```sql
    INSERT INTO compañia(com_nomb)
    SELECT DISTINCT company
    FROM lapt;
```
#### Tabla ram
```sql
    INSERT INTO ram(ram_tmño)
    SELECT DISTINCT Ram
    FROM lapt;
```
#### Tabla so
```sql
    INSERT INTO so(sop_nomb)
    SELECT DISTINCT os
    FROM lapt;
```
#### Tabla compañia_cpu
```sql
    INSERT INTO compañia_cpu(cpuc_nomb)
    SELECT DISTINCT cpu_company
    FROM lapt;
```
#### Tabla modelo_cpu
```sql
    INSERT INTO modelo_cpu(cpum_nomb)
    SELECT DISTINCT cpu_model
    FROM lapt;
```
#### Tabla modelo_gpu
```sql
    INSERT INTO modelo_gpu(gpum_nomb)
    SELECT DISTINCT gpu_model
    FROM lapt;
```
#### Tabla compañia_gpu
```sql
    INSERT INTO compañia_gpu(gpuc_nomb)
    SELECT DISTINCT gpu_company
    FROM lapt;
```

<h2>Consultas:</h2>
<p>1- Mostrar los productos que pertenecen a una cierta compañia y que tengan una ram menor a 16 y que el precio sea mayor a 2500 euros.</p>
```sql
   SELECT product AS producto, company AS compañia, price_euros AS precio_en_euros, ram AS ram 
FROM lapt
WHERE ram < 16 AND price_euros > 2500;
```

<p>2- Calcular el precio promedio de los laptops por compañía:</p>
```sql
SELECT company AS compañia, AVG(price_euros) AS precio_promedio
FROM lapt
GROUP BY company;
```
<p>3-Encontrar las compañías que tienen más de 10 modelos de laptops:</p>
```sql
SELECT company AS compañia, COUNT(*) AS cantidad_modelos
FROM lapt
GROUP BY company
HAVING COUNT(*) > 10;
```
<p>4- Todas las laptops con Sistema operativo Windows 10.</p>
```sql
SELECT l.Product AS Laptop, s.sop_nomb AS SistemaOperativo
FROM lapt l
JOIN so s ON l.OS = s.sop_code 
WHERE s.sop_nomb = 'Windows 10';
```
<p>5-Todos los productos de la compañia Dell.</p>
```sql
SELECT DISTINCT c.com_nomb AS Compañia, l.Product AS Producto
FROM lapt l
JOIN compañia c ON l.Company = c.com_code
WHERE c.com_nomb ='Dell';
```

<p>6- Mostrar compañía ‘Acer’, el modelo con la cantidad total de cada uno, la ram y el precio.</p>
```sql
SELECT c.com_nomb AS Compañia, l.Product AS Modelo, COUNT(l.Product) AS CantidadDeModelos, price_euros AS Precio, Ram AS ram
FROM lapt l
JOIN compañia c ON l.Company = c.com_code
WHERE l.Company = 3
GROUP BY c.com_nomb, l.Product;
```


<h2>Contribución

<h2>Licencia

<h2>Contacto
