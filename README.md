<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, minimum-scale=1, user-scalable=no, viewport-fit=cover">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="theme-color" content="#6200ee">
    <title>Business Register X</title>
    <!-- Google Fonts & Icons -->
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700&display=swap" rel="stylesheet">
    <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
    <!-- Tailwind for Layout Quick Utilities -->
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        :root {
            --primary: #6200ee;
            --primary-variant: #3700b3;
            --secondary: #03dac6;
            --background: #f5f5f7;
            --surface: #ffffff;
            --error: #b00020;
        }

        body {
            font-family: 'Roboto', sans-serif;
            background-color: var(--background);
            margin: 0;
            user-select: none;
            overflow-x: hidden;
        }

        .app-bar {
            background-color: var(--primary);
            color: white;
            padding: 1rem;
            box-shadow: 0 2px 4px rgba(0,0,0,0.2);
            position: sticky;
            top: 0;
            z-index: 50;
        }

        .nav-bottom {
            position: fixed;
            bottom: 0;
            width: 100%;
            background: var(--surface);
            display: flex;
            justify-content: space-around;
            padding: 0.5rem 0;
            box-shadow: 0 -2px 10px rgba(0,0,0,0.1);
            z-index: 50;
        }

        .nav-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            color: #757575;
            font-size: 0.75rem;
            cursor: pointer;
        }

        .nav-item.active {
            color: var(--primary);
        }

        .card {
            background: var(--surface);
            border-radius: 12px;
            padding: 1rem;
            margin-bottom: 1rem;
            box-shadow: 0 2px 8px rgba(0,0,0,0.05);
        }

        .fab {
            position: fixed;
            right: 1.5rem;
            bottom: 5rem;
            background: var(--primary);
            color: white;
            width: 56px;
            height: 56px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 4px 12px rgba(98, 0, 238, 0.4);
            z-index: 40;
        }

        .view {
            display: none;
            padding: 1rem;
            padding-bottom: 6rem;
        }

        .view.active {
            display: block;
            animation: fadeIn 0.3s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        input, select {
            width: 100%;
            padding: 0.75rem;
            margin: 0.5rem 0;
            border: 1px solid #ddd;
            border-radius: 8px;
            outline: none;
        }

        .btn-primary {
            background: var(--primary);
            color: white;
            padding: 0.75rem;
            border-radius: 8px;
            width: 100%;
            font-weight: 500;
        }

        .stat-val {
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--primary);
        }
    </style>
</head>
<body>

    <!-- Header -->
    <div class="app-bar flex justify-between items-center">
        <h1 class="text-xl font-bold tracking-tight">Business Register X</h1>
        <i class="material-icons">account_circle</i>
    </div>

    <!-- Main Views -->
    <main id="app">
        
        <!-- Dashboard View -->
        <section id="view-dashboard" class="view active">
            <h2 class="text-lg font-medium mb-4">Resumen de Hoy</h2>
            <div class="grid grid-cols-2 gap-4 mb-6">
                <div class="card flex flex-col items-center">
                    <span class="text-gray-500 text-sm">Ventas Totales</span>
                    <span id="stat-sales" class="stat-val">$0.00</span>
                </div>
                <div class="card flex flex-col items-center">
                    <span class="text-gray-500 text-sm">Transacciones</span>
                    <span id="stat-count" class="stat-val">0</span>
                </div>
            </div>
            
            <div class="card">
                <h3 class="font-bold mb-2">Actividad Reciente</h3>
                <div id="recent-list" class="divide-y">
                    <p class="text-gray-400 py-4 text-center">No hay registros recientes</p>
                </div>
            </div>
        </section>

        <!-- Inventory View -->
        <section id="view-inventory" class="view">
            <h2 class="text-lg font-medium mb-4">Inventario de Productos</h2>
            <div id="inventory-list">
                <!-- Items populate here -->
            </div>
        </section>

        <!-- Sales/Add View -->
        <section id="view-add" class="view">
            <div class="card">
                <h2 class="text-lg font-bold mb-4">Nueva Venta</h2>
                <label>Producto</label>
                <select id="sale-product"></select>
                <label>Cantidad</label>
                <input type="number" id="sale-qty" placeholder="0" min="1">
                <button onclick="processSale()" class="btn-primary mt-4">Registrar Venta</button>
            </div>

            <div class="card mt-4">
                <h2 class="text-lg font-bold mb-4">Nuevo Producto</h2>
                <input type="text" id="prod-name" placeholder="Nombre del producto">
                <input type="number" id="prod-price" placeholder="Precio ($)">
                <input type="number" id="prod-stock" placeholder="Stock inicial">
                <button onclick="addProduct()" class="btn-primary mt-4 bg-teal-500">Añadir al Inventario</button>
            </div>
        </section>

        <!-- Reports View -->
        <section id="view-reports" class="view">
            <h2 class="text-lg font-medium mb-4">Reportes Detallados</h2>
            <div class="card bg-purple-50">
                <p class="text-sm">Ventas del Mes</p>
                <div id="report-chart" class="h-32 flex items-end gap-2 mt-4">
                    <!-- Fake chart bars -->
                    <div class="bg-purple-300 w-full" style="height: 40%"></div>
                    <div class="bg-purple-400 w-full" style="height: 60%"></div>
                    <div class="bg-purple-300 w-full" style="height: 35%"></div>
                    <div class="bg-purple-600 w-full" style="height: 80%"></div>
                    <div class="bg-purple-500 w-full" style="height: 55%"></div>
                </div>
            </div>
            <button onclick="clearAllData()" class="text-red-500 text-sm mt-8 w-full text-center">Reiniciar base de datos</button>
        </section>

    </main>

    <!-- Navigation -->
    <nav class="nav-bottom">
        <div class="nav-item active" onclick="switchView('dashboard')">
            <i class="material-icons">dashboard</i>
            <span>Inicio</span>
        </div>
        <div class="nav-item" onclick="switchView('inventory')">
            <i class="material-icons">inventory_2</i>
            <span>Stock</span>
        </div>
        <div class="nav-item" onclick="switchView('add')">
            <i class="material-icons">add_box</i>
            <span>Añadir</span>
        </div>
        <div class="nav-item" onclick="switchView('reports')">
            <i class="material-icons">analytics</i>
            <span>Reportes</span>
        </div>
    </nav>

    <!-- Notification Toast -->
    <div id="toast" class="fixed bottom-24 left-1/2 transform -translate-x-1/2 bg-black text-white px-6 py-2 rounded-full opacity-0 transition-opacity pointer-events-none">
        Mensaje
    </div>

    <script>
        // State Management
        let data = {
            inventory: [],
            sales: []
        };

        // Initialize App
        window.onload = () => {
            const savedData = localStorage.getItem('business_register_x_data');
            if(savedData) {
                data = JSON.parse(savedData);
            } else {
                // Default mock data
                data.inventory = [
                    { id: 1, name: "Producto Ejemplo", price: 10.50, stock: 100 }
                ];
            }
            renderAll();
        };

        function saveData() {
            localStorage.setItem('business_register_x_data', JSON.stringify(data));
        }

        // Navigation Logic
        function switchView(viewId) {
            document.querySelectorAll('.view').forEach(v => v.classList.remove('active'));
            document.querySelectorAll('.nav-item').forEach(n => n.classList.remove('active'));
            
            document.getElementById(`view-${viewId}`).classList.add('active');
            event.currentTarget.classList.add('active');
            
            renderAll();
        }

        // Inventory Logic
        function addProduct() {
            const name = document.getElementById('prod-name').value;
            const price = parseFloat(document.getElementById('prod-price').value);
            const stock = parseInt(document.getElementById('prod-stock').value);

            if(!name || !price || isNaN(stock)) {
                showToast("Por favor rellena todos los campos");
                return;
            }

            const newProd = {
                id: Date.now(),
                name,
                price,
                stock
            };

            data.inventory.push(newProd);
            saveData();
            renderAll();
            showToast("Producto añadido");
            
            // Clear inputs
            document.getElementById('prod-name').value = '';
            document.getElementById('prod-price').value = '';
            document.getElementById('prod-stock').value = '';
        }

        // Sales Logic
        function processSale() {
            const prodId = document.getElementById('sale-product').value;
            const qty = parseInt(document.getElementById('sale-qty').value);

            if(!prodId || isNaN(qty) || qty <= 0) {
                showToast("Cantidad inválida");
                return;
            }

            const product = data.inventory.find(p => p.id == prodId);
            if(product.stock < qty) {
                showToast("Stock insuficiente");
                return;
            }

            product.stock -= qty;
            const sale = {
                id: Date.now(),
                productName: product.name,
                qty: qty,
                total: product.price * qty,
                date: new Date().toLocaleTimeString()
            };

            data.sales.unshift(sale);
            saveData();
            renderAll();
            showToast("Venta registrada con éxito");
            document.getElementById('sale-qty').value = '';
        }

        // UI Rendering
        function renderAll() {
            renderInventory();
            renderDashboard();
            updateProductSelect();
        }

        function renderInventory() {
            const container = document.getElementById('inventory-list');
            container.innerHTML = data.inventory.map(p => `
                <div class="card flex justify-between items-center">
                    <div>
                        <h4 class="font-bold text-gray-800">${p.name}</h4>
                        <p class="text-sm text-gray-500">$${p.price.toFixed(2)} | Stock: ${p.stock}</p>
                    </div>
                    <div class="${p.stock < 10 ? 'text-red-500' : 'text-green-500'}">
                        <i class="material-icons">${p.stock < 10 ? 'warning' : 'check_circle'}</i>
                    </div>
                </div>
            `).join('');
        }

        function renderDashboard() {
            const total = data.sales.reduce((acc, curr) => acc + curr.total, 0);
            document.getElementById('stat-sales').innerText = `$${total.toFixed(2)}`;
            document.getElementById('stat-count').innerText = data.sales.length;

            const recentContainer = document.getElementById('recent-list');
            if(data.sales.length === 0) {
                recentContainer.innerHTML = `<p class="text-gray-400 py-4 text-center">No hay registros hoy</p>`;
            } else {
                recentContainer.innerHTML = data.sales.slice(0, 5).map(s => `
                    <div class="py-3 flex justify-between">
                        <div>
                            <p class="font-medium">${s.productName}</p>
                            <p class="text-xs text-gray-400">${s.date}</p>
                        </div>
                        <p class="text-green-600 font-bold">+$${s.total.toFixed(2)}</p>
                    </div>
                `).join('');
            }
        }

        function updateProductSelect() {
            const select = document.getElementById('sale-product');
            select.innerHTML = data.inventory.map(p => `
                <option value="${p.id}">${p.name} ($${p.price})</p>
            `).join('');
        }

        function showToast(msg) {
            const t = document.getElementById('toast');
            t.innerText = msg;
            t.style.opacity = "1";
            setTimeout(() => t.style.opacity = "0", 2000);
        }

        function clearAllData() {
            if(confirm("¿Estás seguro de borrar todos los datos de Business Register X?")) {
                localStorage.clear();
                location.reload();
            }
        }
    </script>
</body>
</html>
