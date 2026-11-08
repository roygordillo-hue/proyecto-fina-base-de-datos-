## 💻 Código SQL

### 1. Definición de Datos (DDL)
```sql
DROP DATABASE IF EXISTS minimarket_db;
CREATE DATABASE minimarket_db;
USE minimarket_db;

CREATE TABLE CATEGORIA (
    id_categoria INT NOT NULL AUTO_INCREMENT,
    nombre_categoria VARCHAR(50) NOT NULL UNIQUE,
    descripcion VARCHAR(255),
    PRIMARY KEY (id_categoria)
);

CREATE TABLE PROVEEDOR (
    id_proveedor INT NOT NULL AUTO_INCREMENT,
    razon_social VARCHAR(100) NOT NULL,
    nombre_contacto VARCHAR(50) NOT NULL,
    telefono VARCHAR(20) NOT NULL,
    direccion VARCHAR(255),
    PRIMARY KEY (id_proveedor)
);

CREATE TABLE CLIENTE (
    id_cliente INT NOT NULL AUTO_INCREMENT,
    nombre VARCHAR(50) NOT NULL,
    apellido VARCHAR(50) NOT NULL,
    dni_ruc VARCHAR(20) NOT NULL UNIQUE,
    telefono VARCHAR(20),
    correo VARCHAR(100),
    direccion VARCHAR(255),
    PRIMARY KEY (id_cliente)
);

CREATE TABLE PRODUCTO (
    id_producto INT NOT NULL AUTO_INCREMENT,
    id_proveedor INT NOT NULL,
    id_categoria INT NOT NULL,
    nombre VARCHAR(150) NOT NULL,
    descripcion VARCHAR(255),
    precio_compra DECIMAL(10,2) NOT NULL CHECK (precio_compra >= 0),
    precio_venta DECIMAL(10,2) NOT NULL CHECK (precio_venta >= 0),
    stock_actual INT NOT NULL DEFAULT 0,
    stock_minimo INT NOT NULL DEFAULT 0,
    PRIMARY KEY (id_producto),
    FOREIGN KEY (id_proveedor) REFERENCES PROVEEDOR(id_proveedor),
    FOREIGN KEY (id_categoria) REFERENCES CATEGORIA(id_categoria)
);

CREATE TABLE VENTA (
    id_venta INT NOT NULL AUTO_INCREMENT,
    id_cliente INT NOT NULL,
    fecha_hora DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
    total DECIMAL(10,2) NOT NULL CHECK (total >= 0),
    metodo_pago VARCHAR(50) NOT NULL DEFAULT 'Efectivo',
    PRIMARY KEY (id_venta),
    FOREIGN KEY (id_cliente) REFERENCES CLIENTE(id_cliente)
);

CREATE TABLE DETALLE_VENTA (
    id_detalle INT NOT NULL AUTO_INCREMENT,
    id_venta INT NOT NULL,
    id_producto INT NOT NULL,
    cantidad INT NOT NULL CHECK (cantidad > 0),
    precio_unitario DECIMAL(10,2) NOT NULL CHECK (precio_unitario >= 0),
    subtotal DECIMAL(10,2) NOT NULL CHECK (subtotal >= 0),
    PRIMARY KEY (id_detalle),
    FOREIGN KEY (id_venta) REFERENCES VENTA(id_venta) ON DELETE CASCADE,
    FOREIGN KEY (id_producto) REFERENCES PRODUCTO(id_producto)
 );
```
<p align="center">
  <a href="./README.md">⬅️ Volver al README.md</a>
</p>
