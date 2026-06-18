let productos = [];
const IVA = 0.19; // 19% típico en Colombia

function agregarProducto() {
    let nombre = document.getElementById("nombre").value;
    let precio = parseFloat(document.getElementById("precio").value);
    let cantidad = parseInt(document.getElementById("cantidad").value);

    if (nombre && precio > 0 && cantidad > 0) {
        productos.push({ nombre, precio, cantidad });
        mostrarCarrito();
    } else {
        alert("Por favor ingresa datos válidos.");
    }
}

function eliminarProducto(index) {
    productos.splice(index, 1);
    mostrarCarrito();
}

function mostrarCarrito() {
    let tbody = document.querySelector("#carrito tbody");
    tbody.innerHTML = "";

    let subtotalGeneral = 0;

    productos.forEach((p, i) => {
        let subtotal = p.precio * p.cantidad;
        subtotalGeneral += subtotal;

        tbody.innerHTML += `
            <tr>
                <td>${p.nombre}</td>
                <td>${p.precio.toFixed(2)}</td>
                <td>${p.cantidad}</td>
                <td>${subtotal.toFixed(2)}</td>
                <td><button onclick="eliminarProducto(${i})">Eliminar</button></td>
            </tr>
        `;
    });

    let iva = subtotalGeneral * IVA;
    let total = subtotalGeneral + iva;

    document.getElementById("totales").innerHTML = `
        Subtotal: $${subtotalGeneral.toFixed(2)} <br>
        IVA (19%): $${iva.toFixed(2)} <br>
        Total: $${total.toFixed(2)}
    `;
}

function aplicarDescuento() {
    let cupon = document.getElementById("cupon").value;
    let totales = document.getElementById("totales").innerHTML;

    let subtotalGeneral = productos.reduce((acc, p) => acc + p.precio * p.cantidad, 0);
    let iva = subtotalGeneral * IVA;
    let total = subtotalGeneral + iva;

    if (cupon === "DESC10" && total > 100000) {
        total *= 0.9; // 10% descuento
    } else if (cupon === "DESC20" && productos.length >= 5) {
        total *= 0.8; // 20% descuento
    }

    document.getElementById("totales").innerHTML = `
        Subtotal: $${subtotalGeneral.toFixed(2)} <br>
        IVA (19%): $${iva.toFixed(2)} <br>
        Total con descuento: $${total.toFixed(2)}
    `;
}

