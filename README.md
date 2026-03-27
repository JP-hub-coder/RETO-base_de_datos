# RETO-base_de_datos

## Reto culminado para aprendizaje de manejo de base de datos

## Código para usar 
```SQL
DROP TABLE IF EXISTS Clientes;
DROP TABLE IF EXISTS Productos;
DROP TABLE IF EXISTS Pedidos;
DROP TABLE IF EXISTS Detalle_pedido;
DROP TABLE IF EXISTS Envios;

CREATE TABLE Clientes(
  id_cliente INT NOT NULL PRIMARY KEY,
  nombre_cliente VARCHAR(100) NOT NULL
);

CREATE TABLE Productos(
  id_producto INT NOT NULL PRIMARY KEY,
  nombre_producto VARCHAR(100) NOT NULL
);

CREATE TABLE Pedidos(
  numero_pedido INT NOT NULL PRIMARY KEY,
  fecha_pedido DATE NOT NULL,
  id_cliente INT NOT NULL,
  FOREIGN KEY(id_cliente) REFERENCES Clientes(id_cliente) 
);

CREATE TABLE Detalle_pedido(
  id_detalle INT NOT NULL PRIMARY KEY,
  numero_pedido INT NOT NULL,
  id_producto INT NOT NULL,
  cantidad INT NOT NULL,
  FOREIGN KEY(numero_pedido) REFERENCES Pedidos(numero_pedido),
  FOREIGN KEY(id_producto) REFERENCES Productos(id_producto)
);

CREATE TABLE Envios(
  id_envio INT NOT NULL PRIMARY KEY,
  numero_pedido INT NOT NULL,
  fecha_envio DATE NOT NULL,
  FOREIGN KEY(numero_pedido) REFERENCES Pedidos(numero_pedido)
);

--Insertar datos
-- pedido 1
INSERT INTO Clientes VALUES (1, 'Juan Pérez');

INSERT INTO Productos VALUES (101, 'Laptop');
INSERT INTO Productos VALUES (102, 'Mouse');

INSERT INTO Pedidos VALUES (1001, '2026-03-20', 1);

INSERT INTO Detalle_pedido VALUES (1, 1001, 101, 1);
INSERT INTO Detalle_pedido VALUES (2, 1001, 102, 2);

INSERT INTO Envios VALUES (5001, 1001, '2026-03-21');
```

## Diagrama 

<img width="1361" height="696" alt="image" src="https://github.com/user-attachments/assets/5c2bcebc-d5a9-4b1a-b9ba-0d1da611d156" />

