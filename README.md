1 contenedor apache
docker run -d -p 8088:80 -v ${PWD}:/var/www/html --name mi-contenedor-php php:apache-bullseye

2 instalar drivers 
docker exec -it mi-contenedor-php docker-php-ext-install mysqli
docker exec -it mi-contenedor-php docker-php-ext-enable mysqli


3 contenedor mysql 
docker run -d -p 3306:3306 --name mi-contenedor-mysql -e MYSQL_ROOT_PASSWORD=12345 -v D:\Contenedor_con_Apache_y_Mysql\db:/var/lib/mysql mysql:debian

para ingresar adentro del contenedor 
docker exec -it mi-contenedor-mysql mysql -u root -p

para crear la base de datos dentro del contenedor 
CREATE DATABASE IF NOT EXISTS prueba;
USE prueba;

CREATE TABLE IF NOT EXISTS alumnos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    apellidos VARCHAR(200),
    nombres VARCHAR(200),
    dni INT(11)
);

INSERT INTO alumnos (apellidos, nombres, dni) VALUES
    ('García', 'Juan', 345678901),
    ('López', 'María', 456789012),
    ('Martínez', 'Carlos', 367890123);



