`````sql

--1. Cargar el respaldo de la base de datos unidad2.sql.

C:\Program Files\PostgreSQL\10\bin>psql -U postgres -h localhost -p 5432 unidad2 < C:\Users\tbtha\OneDrive\Escritorio\unidad2.sql.sql

--2.El cliente usuario01 ha realizado la siguiente compra:

begin;
insert into compra (id,cliente_id,fecha)
values (33,1,'20200622');

insert into detalle_compra(id,producto_id,compra_id,cantidad)
values(43,9,33,5);

update producto 
set stock = stock - 5
where descripcion = 'producto9';

commit;

select * from producto;

--3. El cliente usuario02 ha realizado la siguiente compra:

begin;
--compra producto1
insert into compra (id,cliente_id,fecha)
values (34,2,'20211212');

insert into detalle_compra(id,producto_id,compra_id,cantidad)
values(44,1,34,3);

update producto 
set stock = stock - 3
where descripcion = 'producto1';

--compra producto2
insert into detalle_compra(id,producto_id,compra_id,cantidad)
values(45,2,34,3);

update producto 
set stock = stock - 3
where descripcion = 'producto2';

--compra producto8
insert into detalle_compra(id,producto_id,compra_id,cantidad)
values(46,8,34,3);

update producto 
set stock = stock - 3
where descripcion = 'producto8';

commit;

rollback;

select * from producto;

--4.realizar consultar con el autocommit deshabilitado

a. \echo :AUTOCOMMIT
b. insert into cliente (id,nombre,email)
values (11,'usuario11','usuario11@gmail.com');
c. select * from cliente;
d. rollback;
e. select * from cliente ;
f. \set AUTOCOMMIT off


````