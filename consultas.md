## 5. CONSULTA DE ÁLGEBRA RELACIONAL Y TRADUCIR A SQL

### Consulta 1: Control de inventario (Filtrado simple)
- Enunciado: Mostrar el nombre, stock actual y stock mínimo de los productos que necesitan reabastecimiento (cuyo stock actual es menor o igual al stock mínimo).
- Álgebra Relacional:
π nombre, stock_actual, stock_minimo (σ stock_actual <= stock_minimo (producto))
- SQL:
SELECT nombre, stock_actual, stock_minimo
FROM PRODUCTO
WHERE stock_actual <= stock_minimo;
- Resultado esperado: Se obtendrán los registros de los productos cuyo inventario disponible ha alcanzado o sobrepasado el límite de seguridad, mostrando sus columnas de nombre y niveles de stock.

---

### Consulta 2: Historial de compras (Cruce de 2 tablas)
- Enunciado: Obtener el nombre y apellido del cliente junto con la fecha y el total de sus respectivas compras.
- Álgebra Relacional:
π nombre, apellido, fecha_hora, total (cliente ⨝ venta)
- SQL:
SELECT c.nombre, c.apellido, v.fecha_hora, v.total
FROM CLIENTE c
INNER JOIN VENTA v ON c.id_cliente = v.id_cliente;
- Resultado esperado: Se mostrará un listado consolidado con las columnas nombre, apellido, fecha_hora y total, vinculando a cada cliente con sus ventas realizadas.

---

### Consulta 3: Catálogo por proveedor (Filtrado y cruce de 2 tablas)
- Enunciado: Listar la razón social del proveedor, el nombre del producto y su precio de compra, únicamente para los productos suministrados por 'Distribuidora Andina'.
- Álgebra Relacional:
π razon_social, nombre, precio_compra (σ razon_social == 'Distribuidora Andina' (proveedor ⨝ producto))
- SQL:
SELECT pr.razon_social, p.nombre, p.precio_compra
FROM PROVEEDOR pr
INNER JOIN PRODUCTO p ON pr.id_proveedor = p.id_proveedor
WHERE pr.razon_social = 'Distribuidora Andina';
- Resultado esperado: Se obtendrán las filas de los productos asociados a 'Distribuidora Andina', visualizando las columnas razon_social, nombre y precio_compra.

---

### Consulta 4: Detalles de facturación (Selección sobre cruce de 2 tablas)
- Enunciado: Mostrar la fecha, el método de pago, la cantidad de productos y el subtotal correspondientes a los detalles de la Venta número 2.
- Álgebra Relacional:
π fecha_hora, metodo_pago, cantidad, subtotal (σ id_venta == 2 (venta ⨝ detalle_venta))
- SQL:
SELECT v.fecha_hora, v.metodo_pago, dv.cantidad, dv.subtotal
FROM VENTA v
INNER JOIN DETALLE_VENTA dv ON v.id_venta = dv.id_venta
WHERE v.id_venta = 2;
- Resultado esperado: Se extraerá la información combinada de la cabecera y el desglose de artículos asociados a la Venta #2, desplegando los campos fecha_hora, metodo_pago, cantidad y subtotal.

---

### Consulta 5: Búsqueda de clientes por ubicación (Selección y Proyección)
- Enunciado: Extraer el nombre, apellido y teléfono de los clientes que tienen su domicilio registrado en el 'Barrio Centro'.
- Álgebra Relacional:
π nombre, apellido, telefono (σ direccion == 'Barrio Centro' (cliente))
- SQL:
SELECT nombre, apellido, telefono
FROM CLIENTE
WHERE direccion = 'Barrio Centro';
- Resultado esperado: Se obtendrá un directorio filtrado conteniendo únicamente el nombre, apellido y teléfono de los clientes con dirección en 'Barrio Centro'.
 

