<div align="center">

##  Modelo Entidad-Relación (E-R)

![Diagrama Entidad-Relación](URL_DE_TU_IMAGEN_AQUI.png)


<img width="1619" height="942" alt="diagram" src="https://github.com/user-attachments/assets/7e15d729-bdf2-437c-8699-d7444c1bded2" />


*Figura 1. Diagrama Entidad-Relación del sistema de minimarket.*

##  codigo (E-R)

@startchen

entity CLIENTE {
  ID_Cliente <<key>>
  Apellido
  Nombre
  RUC
  Telefono <<multi>>
}

entity VENTA {
  ID_Venta <<key>>
  Fecha_Hora
  Total <<derived>>
}

entity DETALLE_VENTA {
  ID_Detalle <<key>>
  Cantidad
  Precio_Unitario
  Subtotal <<derived>>
}

entity PRODUCTO {
  ID_Producto <<key>>
  Nombre
  Precio_Venta
  Stock_Actual
}

entity CATEGORIA {
  ID_Categoria <<key>>
  Nombre
  Descripcion
}

entity PROVEEDOR {
  ID_Proveedor <<key>>
  Razon_Social
  Contacto
  Telefono <<multi>>
}

relationship realiza {
}
relationship contiene {
}
relationship se_registra_en {
}
relationship clasifica {
}
relationship suministra {
}

CLIENTE -1- realiza
realiza -N- VENTA

VENTA -1- contiene
contiene -N- DETALLE_VENTA

PRODUCTO -1- se_registra_en
se_registra_en -N- DETALLE_VENTA

CATEGORIA -1- clasifica
clasifica -N- PRODUCTO

PROVEEDOR -1- suministra
suministra -N- PRODUCTO

@endchen


</div>

<p align="center">
  <a href="./README.md">⬅️ Volver al README.md</a>
</p>
