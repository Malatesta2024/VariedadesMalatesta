<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tienda de Ropa y Zapatos</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f9f9f9;
        }
        header {
            background-color: #333;
            color: white;
            padding: 10px 20px;
            text-align: center;
        }
        .container {
            display: flex;
            flex-direction: column;
            align-items: center;
            margin: 20px;
        }
        .producto {
            background-color: white;
            border: 1px solid #ccc;
            border-radius: 5px;
            margin: 10px;
            padding: 15px;
            width: 200px;
            text-align: center;
        }
        .producto img {
            max-width: 100%;
            border-radius: 5px;
            height: 150px;
            object-fit: cover;
        }
        footer {
            text-align: center;
            padding: 20px;
            background-color: #333;
            color: white;
            position: relative;
            bottom: 0;
            width: 100%;
        }
        input[type="file"] {
            margin: 20px 0;
        }
    </style>
</head>
<body>
    <header>
        <h1>Tienda de Ropa y Zapatos</h1>
    </header>

    <div class="container">
        <input type="file" id="fileInput" accept="image/*" multiple>
        <div id="productosContainer"></div>
    </div>

    <footer>
        <p>&copy; 2024 Tienda de Ropa y Zapatos</p>
    </footer>

    <script>
        const fileInput = document.getElementById('fileInput');
        const productosContainer = document.getElementById('productosContainer');

        fileInput.addEventListener('change', (event) => {
            const files = event.target.files;
            productosContainer.innerHTML = ''; // Limpiar productos previos

            for (const file of files) {
                const reader = new FileReader();
                reader.onload = (e) => {
                    const productoDiv = document.createElement('div');
                    productoDiv.className = 'producto';
                    productoDiv.innerHTML = `
                        <img src="${e.target.result}" alt="${file.name}">
                        <h2>${file.name}</h2>
                        <p>Precio: $50.00</p>
                        <button onclick="agregarAlCarrito('${file.name}')">Agregar al Carrito</button>
                    `;
                    productosContainer.appendChild(productoDiv);
                };
                reader.readAsDataURL(file);
            }
        });

        function agregarAlCarrito(producto) {
            alert(`${producto} ha sido agregado al carrito.`);
        }
    </script>
</body>
</html>
