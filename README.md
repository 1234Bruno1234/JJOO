<h1> Normalización de Base de Datos de Laptops.</h1><p>
<h2>Introduccion</h2> <p>
<h3>Este repositorio contiene la documentacion necesaria para poder realizar la normalizacion de una Base de Datos a partir de un archivo CSV.</h3> <p>
----------------------------------------------------------------------------------------------------------------------------------
<h5>Base de datos: Laptops</h5>

<h5>En esta base de datos encontraremos la informacion sobre las compañias, los nombre de los productos (Laptops), la ram, el Sistema Operativo, costo, GPU model, GPU company, CPU company, CPU model, ETC. </h5>

Elegimos esta base de datos porque nos parecio que era una muy completa y entretenida para normalizar. Comenzamos descargando la base de datos de la páguina Kaggle

Lo descargamos en un archivo CSV que es lo que te permite abrirlo en HeidiSQL.

<h2>Instalación
<h3>CREACION DE TABLAS</h3>
  
Creacion de la tabla compañia:
CREATE TABLE compañia ( com_code BIGINT PRIMARY KEY AUTO_INCREMENT NOT NULL,  com_nomb VARCHAR(50)); 
Creacion de la tabla ram:
CREATE TABLE ram (ram_code BIGINT PRIMARY KEY AUTO_INCREMENT NOT NULL,  
ram_tmño tinyint);

<h3><p>Creacion de la tabla ram:</p></h3>
    <h5>CREATE TABLE ram (ram_code BIGINT PRIMARY KEY AUTO_INCREMENT NOT NULL,  
	ram_tmño tinyint);</h5>

<h3><p>Creacion de la tabla SO:</p></h3>
    CREATE TABLE so (sop_code BIGINT PRIMARY KEY AUTO_INCREMENT NOT NULL,  
	sop_nomb VARCHAR(10));

<h3><p>Creacion de la tabla Precio:</p></h3>
    CREATE TABLE precio (pre_code BIGINT PRIMARY KEY AUTO_INCREMENT NOT NULL, 
    	pre_cant BIGINT);

<h3><p>Creacion de la tabla Comañia_CPU:</p></h3>
    CREATE TABLE compañia_cpu (cpuc_code BIGINT PRIMARY KEY AUTO_INCREMENT NOT NULL,  
    	cpuc_nomb VARCHAR(25));

<h3><p>Creacion de la tabla Modelo_CPU:</p></h3>   
    CREATE TABLE modelo_cpu (cpum_code BIGINT PRIMARY KEY AUTO_INCREMENT NOT NULL,  
    	cpum_nomb VARCHAR(50));
    
<h3><p>Creacion de la tabla Modelo_GPU:</p></h3>
    CREATE TABLE modelo_gpu (gpum_code BIGINT PRIMARY KEY AUTO_INCREMENT NOT NULL,  
    	gpum_nomb VARCHAR(50))

<h3><p>Creacion de la tabla Compañia_GPU:</p></h3> 
    CREATE TABLE compañia_gpu (gpuc_code BIGINT PRIMARY KEY AUTO_INCREMENT NOT NULL,  
    	gpuc_nomb VARCHAR(50));
<h1>Sacar tabla cpu y gpu</h1>
<h3><p>Creacion de la tabla CPU:</p></h3> 
    CREATE TABLE cpu (
    cpu_code INT PRIMARY KEY AUTO_INCREMENT NOT NULL,
    cpu_mode VARCHAR(50) NOT NULL,
    cpu_comp VARCHAR(50) NOT NULL);

<h3><p>Creacion de la tabla GPU:</p></h3>
    CREATE TABLE gpu (
    gpu_code INT PRIMARY KEY AUTO_INCREMENT NOT NULL,
    gpu_mode VARCHAR(50) NOT NULL,
    gpu_comp VARCHAR(50) NOT NULL
);



<h2>Uso

<h2>Contribución

<h2>Licencia

<h2>Contacto
