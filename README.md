<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Soporte Técnico & Integración Web</title>
    <style>
        :root {
            --primary: #2c3e50;
            --secondary: #3498db;
            --accent: #e74c3c;
            --light: #ecf0f1;
            --success: #27ae60;
        }

        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; margin: 0; line-height: 1.6; color: #333; background-color: #f4f7f6; }
        
        header { background: var(--primary); color: white; padding: 2rem; text-align: center; }
        
        nav { background: #1a252f; padding: 0.5rem; text-align: center; position: sticky; top: 0; z-index: 100; }
        nav a { color: white; margin: 0 15px; text-decoration: none; font-weight: bold; cursor: pointer; }
        nav a:hover { color: var(--secondary); }

        .container { max-width: 1000px; margin: auto; padding: 20px; }
        
        section { padding: 40px 20px; border-bottom: 1px solid #ddd; background: white; margin-bottom: 20px; border-radius: 8px; }
        
        .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; }
        
        .card { background: white; border: 1px solid #ddd; padding: 20px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.1); }
        .card h3 { color: var(--secondary); border-bottom: 2px solid var(--secondary); padding-bottom: 10px; }

        /* Estilos Login y Sesiones */
        #status-sesion { padding: 10px; background: var(--light); border-radius: 5px; margin-top: 10px; font-weight: bold; }
        .btn-login { background: var(--secondary); color: white; border: none; padding: 10px 20px; border-radius: 5px; cursor: pointer; }
        .lista-sesiones { list-style: none; padding: 0; }
        .lista-sesiones li { padding: 5px; border-bottom: 1px solid #eee; font-size: 0.9rem; }

        /* Estilos Mantenimiento */
        .selector-errores { width: 100%; padding: 12px; border-radius: 5px; border: 1px solid var(--secondary); margin-bottom: 15px; }
        #solucion-box { padding: 15px; background: #e8f4fd; border-left: 5px solid var(--secondary); display: none; }

        footer { background: var(--primary); color: white; text-align: center; padding: 20px; margin-top: 40px; }
    </style>
</head>
<body>

<header>
    <h1>Integración Web - Segundo Parcial</h1>
    <p>Dominio: yo </p>
    <div id="user-display" style="color: var(--secondary); font-weight: bold;"></div>
</header>

<nav>
    <a href="#inicio">Inicio</a>
    <a href="#caracteristicas">Características</a>
    <a href="#mantenimiento">Mantenimiento</a>
    <a onclick="toggleLogin()" id="nav-login">Iniciar Sesión</a>
</nav>

<div class="container">
    
    <section id="inicio">
        <h2>Bienvenida</h2>
        <p>Ordinario</p>
        <div id="login-area">
            <button class="btn-login" onclick="login()">Simular Login (Invitado)</button>
        </div>
    </section>

    <section id="caracteristicas">
        <h2>Características del Sistema</h2>
        <div class="grid">
            <div class="card">
                <h3>Gestión de Usuarios</h3>
                <p>Permite el registro simulado de sesiones y control de acceso en tiempo real para usuarios invitados.</p>
            </div>
            <div class="card">
                <h3>Diagnóstico Inteligente</h3>
                <p>Módulo de mantenimiento interactivo que ofrece soluciones rápidas a problemas técnicos comunes.</p>
            </div>
            <div class="card">
                <h3>Diseño Responsivo</h3>
                <p>Interfaz adaptativa construida con CSS Grid para una visualización óptima en móviles y escritorio.</p>
            </div>
        </div>
    </section>

    <section id="sesiones">
        <h2>Control de Accesos</h2>
        <div class="grid">
            <div class="card">
                <h3>Sesiones Recientes</h3>
                <p>Usuarios que han ingresado al sistema:</p>
                <ul id="registro-sesiones" class="lista-sesiones">
                    <li><em>No hay sesiones registradas hoy.</em></li>
                </ul>
            </div>
            <div class="card">
                <h3>Estado del Sistema</h3>
                <div id="status-sesion">Estado: Desconectado</div>
            </div>
        </div>
    </section>

    <section id="mantenimiento">
        <h2>Diagnóstico de Errores Comunes</h2>
        <p>Selecciona un problema técnico para ver la solución recomendada:</p>
        
        <select id="errorSelect" class="selector-errores" onchange="mostrarSolucion()">
            <option value="">-- Selecciona un error --</option>
            <option value="lento">El equipo está muy lento</option>
            <option value="pantalla">Pantallazo (BSOD)</option>
            <option value="usuario">se puso mal el usuario</option>
            <option value="wifi">No conecta a Internet</option>
        </select>

        <div id="solucion-box">
            <h4 id="error-titulo"></h4>
            <p id="error-desc"></p>
        </div>
    </section>

</div>

<footer>
    <p>&copy; 2026 Paseme profe Esau - Trabajo Parcial</p>
</footer>

<script>
    // --- LÓGICA DE SESIONES ---
    let sesiones = [];

    function login() {
        const nombre = prompt("Ingresa tu nombre de usuario:");
        if (nombre) {
            const ahora = new Date();
            const tiempo = ahora.toLocaleTimeString();
            
            // Guardar sesión
            sesiones.push(`${nombre} - ${tiempo}`);
            
            // Actualizar Interfaz
            document.getElementById('status-sesion').innerText = "Estado: Conectado como " + nombre;
            document.getElementById('status-sesion').style.color = "var(--success)";
            document.getElementById('user-display').innerText = "Bienvenido, " + nombre;
            document.getElementById('nav-login').innerText = "Cerrar Sesión";
            document.getElementById('nav-login').onclick = logout;
            
            actualizarListaSesiones();
        }
    }

    function logout() {
        document.getElementById('status-sesion').innerText = "Estado: Desconectado";
        document.getElementById('status-sesion').style.color = "black";
        document.getElementById('user-display').innerText = "";
        document.getElementById('nav-login').innerText = "Iniciar Sesión";
        document.getElementById('nav-login').onclick = login;
        alert("Sesión cerrada correctamente.");
    }

    function actualizarListaSesiones() {
        const lista = document.getElementById('registro-sesiones');
        lista.innerHTML = "";
        sesiones.forEach(s => {
            const li = document.createElement('li');
            li.innerText = "✅ Session iniciada por: " + s;
            lista.appendChild(li);
        });
    }

    // --- LÓGICA DE MANTENIMIENTO ---
    function mostrarSolucion() {
        const select = document.getElementById('errorSelect');
        const box = document.getElementById('solucion-box');
        const titulo = document.getElementById('error-titulo');
        const desc = document.getElementById('error-desc');

        const soluciones = {
            "lento": {
                t: "Equipo Lento",
                d: "Cierra los demas procesos."
            },
            "pantalla": {
                t: "ME sale error 454",
                d: "Reinicia la pagina."
            },
            "usuario": {
                t: "problemas con el inico de secion",
                d: "talves pusiste el usuario incorrecto."
            },
            "wifi": {
                t: "Fallo de Conexión",
                d: "Sugerencia: Reiniciar el adaptador de red, verificar el interruptor físico de Wi-Fi o reinstalar el controlador de red."
            }
        };

        if (select.value !== "") {
            const info = soluciones[select.value];
            titulo.innerText = info.t;
            desc.innerText = info.d;
            box.style.display = "block";
        } else {
            box.style.display = "none";
        }
    }
</script>

</body>
</html>
