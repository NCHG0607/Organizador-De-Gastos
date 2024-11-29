<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Organizador de Gastos</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f0f0f0;
        }
        header {
            background-color: #333;
            color: white;
            padding: 10px 0;
            text-align: center;
        }
        main {
            padding: 20px;
        }
        section {
            background-color: white;
            padding: 20px;
            margin: 20px 0;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        form label {
            display: block;
            margin-top: 10px;
        }
        form input, form button {
            width: 100%;
            padding: 10px;
            margin: 5px 0;
            border-radius: 4px;
            border: 1px solid #ccc;
        }
        button {
            background-color: #000080;
            color: white;
            border: none;
            cursor: pointer;
        }
        table {
            width: 100%;
            border-collapse: collapse;
        }
        th, td {
            border: 1px solid black;
            padding: 8px;
            text-align: left;
        }
        th {
            background-color: #f2f2f2;
        }
        .button-delete {
            background-color: #ff4c4c;
            color: white;
            border: none;
            padding: 5px 10px;
            cursor: pointer;
            border-radius: 4px;
        }
        .button-delete:hover {
            background-color: #ff0000;
        }
    </style>
</head>
<body>
    <header>
        <h1>Organizador de Gastos</h1>
    </header>
    <main>
        <section id="add-expense">
            <h2>Agregar Gasto</h2>
            <form id="expense-form">
                <label for="date">Fecha:</label>
                <input type="date" id="date" required>
                <label for="description">Descripción:</label>
                <input type="text" id="description" required>
                <label for="amount">Monto:</label>
                <input type="number" id="amount" step="0.01" required>
                <button type="submit">Agregar</button>
            </form>
        </section>
        <section id="expense-list">
            <h2>Lista de Gastos</h2>
            <table>
                <thead>
                    <tr>
                        <th>Fecha</th>
                        <th>Descripción</th>
                        <th>Monto</th>
                        <th>Acciones</th>
                    </tr>
                </thead>
                <tbody id="expenses-tbody">
                    <!-- Los gastos se agregarán aquí -->
                </tbody>
            </table>
        </section>
    </main>
    <footer>
        <p>&copy; 2024 Organizador de Gastos. Todos los derechos reservados.</p>
    </footer>
    <script>
        document.getElementById('expense-form').addEventListener('submit', function(event) {
            event.preventDefault();
            const date = document.getElementById('date').value;
            const description = document.getElementById('description').value;
            const amount = document.getElementById('amount').value;
            if (date && description && amount) {
                // Crear una nueva fila para la tabla de gastos
                const newRow = document.createElement('tr');
                newRow.innerHTML = `
                    <td>${date}</td>
                    <td>${description}</td>
                    <td>${amount}</td>
                    <td><button class="button-delete">Eliminar</button></td>
                `;
                document.getElementById('expenses-tbody').appendChild(newRow);
                newRow.querySelector('.button-delete').addEventListener('click', function() {
                    newRow.remove();
                });
                document.getElementById('expense-form').reset();
            } else {
                alert('Por favor, completa todos los campos.');
            }
        });
    </script>
</body>
</html>
