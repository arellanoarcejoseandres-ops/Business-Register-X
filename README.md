<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Business Register X v1.0 | José Andrés Arellano Arce</title>
    <style>
        /* CSS INTEGRADO */
        :root {
            --primary-color: #1a73e8;
            --secondary-color: #0d47a1;
            --bg-color: #f8f9fa;
            --text-color: #202124;
            --accent-color: #e8f0fe;
        }

        body {
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            line-height: 1.6;
            margin: 0;
            padding: 0;
            background-color: var(--bg-color);
            color: var(--text-color);
        }

        header {
            background-color: var(--primary-color);
            color: white;
            padding: 3rem 1rem;
            text-align: center;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }

        header h1 { margin: 0; font-size: 2.5rem; }
        header p { margin: 10px 0 0; font-size: 1.1rem; opacity: 0.9; }

        .container {
            max-width: 1000px;
            margin: 2rem auto;
            padding: 0 20px;
        }

        section {
            background: white;
            border-radius: 12px;
            padding: 2rem;
            margin-bottom: 2rem;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
        }

        h2 {
            color: var(--secondary-color);
            border-left: 5px solid var(--primary-color);
            padding-left: 15px;
            margin-top: 0;
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .card {
            border: 1px solid #ddd;
            border-radius: 8px;
            padding: 15px;
            background: var(--accent-color);
        }

        .card h3 { margin-top: 0; color: var(--primary-color); }

        .tech-tags span {
            display: inline-block;
            background: #e0e0e0;
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 0.9rem;
            margin: 5px;
        }

        .btn-download {
            display: inline-block;
            background: #28a745;
            color: white;
            padding: 12px 25px;
            text-decoration: none;
            border-radius: 6px;
            font-weight: bold;
            margin-top: 10px;
        }

        .btn-download:hover { background: #218838; }

        footer {
            text-align: center;
            padding: 2rem;
            font-size: 0.9rem;
            color: #666;
        }

        code {
            background: #272822;
            color: #f8f8f2;
            padding: 2px 5px;
            border-radius: 4px;
            font-family: monospace;
        }
    </style>
</head>
<body>

    <header>
        <h1>Business Register X <small>v1.0</small></h1>
        <p>Desarrollado por: <strong>José Andrés Arellano Arce</strong></p>
        <p>3° TDS - Tecnología en Desarrollo de Software</p>
    </header>

    <div class="container">
        
        <section>
            <h2>Entregables del Proyecto</h2>
            <div class="grid">
                <div class="card">
                    <h3>Aplicación Android</h3>
                    <p>Descarga el instalador APK para probar el sistema de inventario en tu dispositivo.</p>
                    <a href="TU_LINK_DE_GITHUB_AQUI" class="btn-download">⬇️ Descargar APK</a>
                </div>
                <div class="card">
                    <h3>Video Demostrativo</h3>
                    <p>Explicación técnica del código y funcionamiento de la base de datos.</p>
                    <a href="TU_LINK_DE_VIDEO_AQUI" style="color: var(--primary-color);">Ver Video en YouTube →</a>
                </div>
            </div>
        </section>

        <section>
            <h2>Stack Tecnológico</h2>
            <div class="tech-tags">
                <span>Kotlin</span>
                <span>Firebase Auth</span>
                <span>Realtime Database</span>
                <span>Android Jetpack</span>
                <span>Retrofit</span>
                <span>GitHub</span>
            </div>
        </section>

        <section>
            <h2>Conceptos de Programación Aplicados</h2>
            
            <div class="card" style="background: white; border: none; border-left: 4px solid #ffc107; margin-bottom: 15px;">
                <h3>1. Sentencias de Control</h3>
                <p>Se utilizaron estructuras <code>if-else</code> para la validación de formularios. Por ejemplo, antes de subir un producto a la nube, el sistema verifica que el campo de "Precio" no sea menor a cero y que el "Nombre" no esté vacío, garantizando la integridad de la base de datos.</p>
            </div>

            <div class="card" style="background: white; border: none; border-left: 4px solid #4caf50; margin-bottom: 15px;">
                <h3>2. Funciones y Métodos</h3>
                <p>La lógica se organizó en funciones modulares como <code>saveProductToCloud()</code> y <code>clearInputs()</code>. Esto permite que el código sea limpio y que la tarea de limpiar la interfaz se pueda invocar en cualquier momento sin repetir código.</p>
            </div>

            <div class="card" style="background: white; border: none; border-left: 4px solid #2196f3; margin-bottom: 15px;">
                <h3>3. Programación Orientada a Objetos (POO)</h3>
                <p>El proyecto utiliza <strong>Data Classes</strong> para representar objetos del mundo real. La clase <code>Product</code> encapsula los atributos (ID, nombre, cantidad, precio), permitiendo manipular cada registro como una instancia de objeto única que se mapea directamente a un JSON en Firebase.</p>
            </div>
        </section>

        <section>
            <h2>Galería de la Aplicación</h2>
            <p>Capturas de pantalla de la interfaz desarrollada con apoyo de IA:</p>
            <div class="grid">
                <div style="text-align: center;">
                    <div style="width: 100%; height: 200px; background: #ddd; display: flex; align-items: center; justify-content: center; border-radius: 8px;">
                        [Imagen: Formulario de Registro]
                    </div>
                    <p><small>Vista Principal de Registro</small></p>
                </div>
                <div style="text-align: center;">
                    <div style="width: 100%; height: 200px; background: #ddd; display: flex; align-items: center; justify-content: center; border-radius: 8px;">
                        [Imagen: Consola Firebase]
                    </div>
                    <p><small>Datos Sincronizados en la Nube</small></p>
                </div>
            </div>
        </section>

    </div>

    <footer>
        &copy; 2026 José Andrés Arellano Arce | Instituto Tecnológico Superior | 3° TDS
    </footer>

</body>
</html>
