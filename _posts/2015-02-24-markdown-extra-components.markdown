---
title: "Proyecto SQL y Power BI: Sistema de Gestión de Ventas"
layout: post
date: 2024-09-10 18:46
image: /assets/images/markdown.jpg
headerImage: false
tag:
- sql
- powerbi
- gestion de ventas
category: blog
author: Álvaro López Hurtado
description: Gestión de una Tienda minorista
---

## Proyecto de Sistema Gestión de Ventas para una Tienda

En este proyecto desarrollé un sistema de gestión de datos para una tienda minorista, incluyendo la administración de clientes, proveedores, productos, ventas e inventario. La base de datos está diseñada para optimizar el seguimiento de las transacciones (diarias, semanales o mensuales), mostrar los productos más vendidos, generar reportes detallados que faciliten la toma de decisiones y mantener un control preciso del inventario.

Las herramientas utilizadas en este proyecto son **MySQL** para la gestión de la base de datos y **Power BI** para la visualización de datos.

### Tablas:

- **Clientes**: Almacena la información de los clientes que realizan compras en la tienda.
  - Campos: `cliente_id`, `nombre`, `apellido`, `email`, `telefono`.

- **Proveedores**: Registra los datos de contacto de los proveedores de productos.
  - Campos: `proveedor_id`, `nombre_proveedor`, `contacto_proveedor`.

- **Productos**: Contiene el catálogo de productos disponibles para la venta.
  - Campos: `producto_id`, `nombre`, `precio`, `categoria`, `stock`, `proveedor_id`.

- **Ventas**: Registra cada transacción realizada en la tienda, vinculando a los clientes con los productos comprados y el monto total de la venta.
  - Campos: `venta_id`, `cliente_id`, `producto_id`, `fecha_venta`, `total_venta`.

- **Inventario**: Permite llevar un control detallado del stock de cada producto, con un registro del stock inicial y las actualizaciones tras cada venta.
  - Campos: `inventario_id`, `producto_id`, `stock_inicial`, `stock_actualizado`, `fecha_actualizado`.

### Creación de la base de datos

A continuación, se muestra el código para la creación de la base de datos y las tablas correspondientes:

```sql
-- Creación de la base de datos Tienda
create database if not exists Tienda;

-- Usamos la base de datos Tienda
use Tienda;

-- Tabla Clientes
create table Clientes (
    cliente_id int auto_increment primary key,
    nombre varchar(255) not null,
    apellido varchar(255),
    email varchar(255) not null unique,
    telefono varchar(20)
);

-- Tabla Proveedores
create table Proveedores (
    proveedor_id int auto_increment primary key,
    nombre_proveedor varchar(255) not null,
    contacto_proveedor varchar(255) not null
);

-- Tabla Productos
create table Productos (
    producto_id int auto_increment primary key,
    nombre varchar(255) not null,
    precio decimal(10,2) not null,
    categoria varchar(255),
    stock int check (stock >= 0),
    proveedor_id int not null
);

-- Tabla Ventas
create table Ventas (
    venta_id int auto_increment primary key,
    cliente_id int not null,
    producto_id int not null,
    fecha_venta date,
    total_venta decimal(10,2),
    foreign key (cliente_id) references Clientes(cliente_id),
    foreign key (producto_id) references Productos(producto_id)
);

-- Tabla Inventario
create table Inventario (
    inventario_id int auto_increment primary key,
    producto_id int not null,
    stock_inicial int not null check (stock_inicial >= 0),
    stock_actualizado int not null check (stock_actualizado >= 0),
    fecha_actualizado date,
    foreign key (producto_id) references Productos(producto_id)
);
```
![Descripción de la imagen](/assets/images/SQL/CreacionDB_1.png)
![Descripción de la imagen](/assets/images/SQL/CreacionDB_2.png)
![Descripción de la imagen](/assets/images/SQL/CreacionDB_3.png)

```sql
-- Datos para la tabla Clientes
insert into Clientes (nombre, apellido, email, telefono) values
('Juan', 'Pérez', 'juan.perez@gmail.com', '123456789'),
('Ana', 'García', 'ana.garcia@gmail.com', '987654321'),
('Luis', 'Fernández', 'luis.fernandez@outlook.com', '192837465'),
('Marta', 'López', 'marta.lopez@outlook.com', '981276345');

-- Datos para la tabla Proveedores
insert into Proveedores (nombre_proveedor, contacto_proveedor) values
('Proveedor A', 'contactoA@gmail.com'),
('Proveedor B', 'contactoB@outlook.com'),
('Proveedor C', 'contactoC@outlook.com');

-- Datos para la tabla Productos
insert into Productos (nombre, precio, categoria, stock, proveedor_id) values
('Portátil', 1000.00, 'Electrónica', 10, 1),
('Teléfono', 500.00, 'Electrónica', 15, 1),
('Mesa', 200.00, 'Muebles', 5, 2),
('Silla', 50.00, 'Muebles', 20, 2),
('Cámara', 300.00, 'Fotografía', 8, 3);

-- Datos para la tabla Ventas
insert into Ventas (cliente_id, producto_id, fecha_venta, total_venta) values
(1, 1, '2024-09-01', 1000.00),
(2, 2, '2024-09-02', 500.00),
(3, 3, '2024-09-05', 200.00),
(4, 4, '2024-09-06', 50.00),
(1, 5, '2024-09-10', 300.00);

-- Datos para la tabla Inventario
insert into Inventario (producto_id, stock_inicial, stock_actualizado, fecha_actualizado) values
(1, 10, 9, '2024-09-01'),
(2, 15, 14, '2024-09-02'),
(3, 5, 4, '2024-09-05'),
(4, 20, 19, '2024-09-06'),
(5, 8, 7, '2024-09-10');
```
![Descripción de la imagen](/assets/images/SQL/Datos_db1.png)
![Descripción de la imagen](/assets/images/SQL/Datos_db2.png)

Una vez creada la base de datos con sus respectivas tablas, gestionaremos la
información almacenada a través de consultas SQL avanzadas para poder realizar
análisis eficientes. Estas consultas permitirán generar reportes clave que faciliten la 
toma de decisiones estratégicas.

### Consulta 1: Obtener total de ventas diarias, semanales y mensuales
La primera consulta abordará el análisis de las respectivas ventas en distintos 
periodos de tiempo, específicamente en ventas diarias, semanales y mensuales. 
Facilitar total a la evaluación del rendimiento de la tienda a lo largo del tiempo.

#### Diarias
```sql
select
sum(_venta) as 'Venta Total',
day(fecha_venta) as 'Dia del mes'
from ventas
where month(fecha_venta) =09 and year(fecha_venta)=2024
group by day(fecha_venta)
order by day(fecha_venta)
```
![Descripción de la imagen](/assets/images/SQL/Consulta_dias.png)

#### Semanal
```sql
select
sum(total_venta) as 'Venta Total',
floor((day(fecha_venta) - 1) / 7) + 1 as 'Semana del mes'
from ventas
where month(fecha_venta) =9 and year(fecha_venta)=2024
group by floor((day(fecha_venta) - 1) / 7) + 1
order by floor((day(fecha_venta) - 1) / 7) + 1
```
![Descripción de la imagen](/assets/images/SQL/Semanal.png)

#### Mensual
```sql
select
sum(total_venta) as 'Venta Total',
month(fecha_venta) as 'Mes'
from ventas
where month(fecha_venta) =9 and year(fecha_venta)
group by month(fecha_venta)
order by month(fecha_venta)
```
![Descripción de la imagen](/assets/images/SQL/Mensual.png)


### Consulta 2: Ranking de productos más vendidos
La segunda consulta visualizara un ranking de productos más vendidos de la tienda, el 
cual ayudara a saber las tendencias de consumo. Este análisis permitirá tomar
decisiones sobre el inventario y las estrategias de marketing.

```sql
with Producto_Ventas as (
select productos.nombre as Producto, count(ventas.producto_id) as Ventas
from productos
join ventas on productos.producto_id=ventas.producto_id
group by productos.nombre
)
select Producto, Ventas,
row_number() over (order by Ventas desc) as 'Ranking de productos más vendidos'
from Producto_Ventas
```
![Descripción de la imagen](/assets/images/SQL/ranking.png)


### Consulta 3: Generar reportes de ventas por clientes o proveedor
La tercera consulta generaremos los reportes de ventas por cliente o proveedor. Estos 
reportes permitirán analizar el comportamiento de compra de los clientes y el 
desempeño de los proveedores, proporcionando información valiosa para optimizar las 
relaciones comerciales y mejorar la gestión del inventario.

#### Reportes por clientes
```sql
select 
cli.nombre as 'Nombre del Cliente',
cli.apellido as 'Apellido del Cliente',
count(ven.venta_id) as 'Cantidad de Ventas',
sum(ven.total_venta) as 'Total Ventas'
from clientes cli
join ventas ven on cli.cliente_id=ven.cliente_id
group by cli.cliente_id, cli.nombre, cli.apellido
order by sum(ven.total_venta) desc
```
![Descripción de la imagen](/assets/images/SQL/Reporte_por_cliente.png)

#### Reportes por proveedores
```sql
select
proo.nombre_proveedor as 'Nombre del Proveedor',
count(ven.venta_id) as 'Cantidad de Ventas',
sum(ven.total_venta) as 'Total Ventas'
from Proveedores proo
join Productos prod on proo.proveedor_id = prod.proveedor_id
join Ventas ven on prod.producto_id = ven.producto_id
group by proo.proveedor_id, proo.nombre_proveedor
order by sum(ven.total_venta) desc;
```
![Descripción de la imagen](/assets/images/SQL/Reporte_por_proveedor.png)

### Consulta 4: Actualización automática del inventario despues de cada venta
La cuarta consulta implementara una actualización automática del inventario 
después de cada venta. Mediante el uso de un trigger, el sistema ajustara el stock de 
los productos vendidos a tiempo real, garantizando un control preciso del inventario.

```sql
delimiter //
create trigger Actualizar_Inventario
after insert on Ventas
for each row
begin
-- Actualiza la tabla inventario
update Inventario
set 
stock_actualizado=stock_actualizado - 1,
fecha_actualizado=new.fecha_venta
where producto_id = new.producto_id;
-- Actualiza la tabla Productos
update Productos
set
stock=stock - 1
where producto_id=new.producto_id;
end //
delimiter ;
```
![Descripción de la imagen](/assets/images/SQL/Trigger.png)

### Visualización en Power BI
Una vez hecha las consultas, para finalizar, conectamos la base de datos “Tienda” hacia el programa Power BI para la visualización de los datos. En este abarcaremos las preguntas para contestarlas en gráficos:
- **Mostrar las tendencias de ventas en diferentes periodos, en este caso, ventas diarias**
- **Visualizar la proporción de las ventas por producto. Mostrando el ranking.**
- **Mostrar las tendencias de las ventas del mercado.**
- **Visualizar las ventas por clientes y proveedor.**

![Descripción de la imagen](/assets/images/SQL/graficas.png)