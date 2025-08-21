# SistemaFacturacion-FondoMarino
Sistema de Facturación con Swing, utilizando MySQL y sockets
Sistema de Facturación – Fondo Marino

App de escritorio en Java (Swing) con MySQL y sockets.
Permite: gestión de clientes (BD), ver inventario (BD), facturar con IVA 13% y generar TXT, y prueba de redes por sockets.

Repo: https://github.com/meimora02/SistemaFacturacion-FondoMarino

Requisitos
	•	JDK 17+ (NetBeans recomendado)
	•	MySQL Server local
	•	Conector JDBC de MySQL (mysql-connector-j) agregado a Libraries

Configuración de la BD

Ejecuta este script en MySQL Workbench:
CREATE DATABASE IF NOT EXISTS facturacion;
USE facturacion;

CREATE TABLE IF NOT EXISTS clientes(
  cedula    VARCHAR(20) PRIMARY KEY,
  nombre    VARCHAR(100) NOT NULL,
  telefono  VARCHAR(30)  NOT NULL,
  direccion VARCHAR(200) NOT NULL
);

CREATE TABLE IF NOT EXISTS productos(
  codigo   VARCHAR(20) PRIMARY KEY,
  nombre   VARCHAR(100) NOT NULL,
  cantidad INT NOT NULL,
  precio   DOUBLE NOT NULL,
  gravado  TINYINT(1) NOT NULL DEFAULT 1
);

SET SQL_SAFE_UPDATES = 0;
DELETE FROM productos;

INSERT INTO productos (codigo, nombre, precio, gravado, cantidad) VALUES
('P001','Señuelo Rapala Original', 8900, 1, 50),
('P002','Caña Shimano FX 250',     55000,1, 20),
('P003','Hilo monofilamento 40 lb',7500, 1, 80),
('P004','Anzuelos Mustad N°6 (10u)',2500,1, 100),
('P005','Carnada artificial tipo PES',3200,1, 60),
('P006','Caja porta señuelos mediana',9800,1, 30),
('P007','Plomadas 1oz (par)',      900, 1, 120),
('P008','Guante antideslizante',   6500,1, 25),
('P009','Camisa pesca UV (M)',     14500,1, 15),
('P010','Cortador de alambre heavy',18000,1, 10);

Cómo ejecutar
	1.	Abrir el proyecto en NetBeans.
	2.	Verificar el conector mysql-connector-j en Libraries.
	3.	Ejecutar vista.VentanaSistema (Run File).
	4.	Pestañas:
	•	Clientes: guardar/listar (se persiste en MySQL).
	•	Inventario: Refrescar (BD) y seleccionar productos para factura.
	•	Facturación: ingresar cédula, agregar líneas, Generar TXT.
	•	Probar redes (socket): confirma comunicación local.

Dónde se guardan las facturas: carpeta facturas/ dentro del proyecto. Muestra la ruta completa al generar.



Autora 
Melissa Mora Gutierrez 
