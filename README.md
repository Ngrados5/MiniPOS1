# Sistema Web de Facturación (Mini POS)

## Descripción
Aplicativo web desarrollado en **JavaScript**, **HTML** y **CSS** que permite registrar productos, calcular subtotales, IVA y total de compra. Incluye funciones para agregar y eliminar productos del carrito en tiempo real y aplicar cupones de descuento.

## Funcionalidades
- Registro de productos (nombre, precio, cantidad).
- Cálculo automático de subtotal por producto y subtotal general.
- Aplicación de IVA (19%).
- Total final de compra.
- Agregar y eliminar productos del carrito.
- Persistencia con localStorage (el carrito se guarda aunque se cierre el navegador).
- Aplicación de cupones de descuento:
  - `DESC10`: 10% si el total supera $100.000.
  - `DESC20`: 20% si se compran 5 o más productos.

## Tecnologías utilizadas
- HTML5
- CSS3
- JavaScript (ES6)

## Ejecución
1. Clonar el repositorio o descargar el archivo `.zip`.
2. Abrir `index.html` en un navegador.
3. Ingresar productos y aplicar descuentos.

## Autor
Nicolás Arturo Granados Arévalo

