
# Normalización de Base de Datos de Laptops.

# Introduccion
#### Este repositorio contiene la documentacion necesaria para poder realizar la normalizacion de una Base de Datos a partir de un archivo CSV.
---------------------------------------------------------------------------------------------------------------
## Base de datos: Laptops
En esta base de datos encontraremos la informacion sobre las compañias, los nombre de los productos (Laptops), la ram, el Sistema Operativo, costo, GPU model, GPU company, CPU company, CPU model, etc. 

Elegimos esta base de datos porque nos parecio que era una muy completa y entretenida para normalizar. Comenzamos descargando la base de datos de la páguina Kaggle

Lo descargamos en un archivo CSV que es lo que te permite abrirlo en HeidiSQL.

# Instalación
## CREACION DE TABLAS
  
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

/// este es el diagrama de clases de la base de datos
![Diagrama](imagen/laptop.png)
<h2>Uso

<h2>Contribución

<h2>Licencia

<h2>Contacto
