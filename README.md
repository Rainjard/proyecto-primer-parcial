# Mi_primera_pagina_web

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
        }

        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; margin: 0; line-height: 1.6; color: #333; }
        
        header { background: var(--primary); color: white; padding: 2rem; text-align: center; }
        
        nav { background: #1a252f; padding: 0.5rem; text-align: center; position: sticky; top: 0; }
        nav a { color: white; margin: 0 15px; text-decoration: none; font-weight: bold; }
        nav a:hover { color: var(--secondary); }

        .container { max-width: 1000px; margin: auto; padding: 20px; }
        
        section { padding: 40px 0; border-bottom: 1px solid #ddd; }
        
        .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; }
        
        .card { background: white; border: 1px solid #ddd; padding: 20px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.1); }
        .card h3 { color: var(--secondary); border-bottom: 2px solid var(--secondary); padding-bottom: 10px; }

        .mantenimiento-img { width: 100%; height: 200px; background: #ccc; display: flex; align-items: center; justify-content: center; margin-bottom: 15px; border-radius: 5px; overflow: hidden; }
        .mantenimiento-img img { width: 100%; height: 100%; object-fit: cover; }

        footer { background: var(--primary); color: white; text-align: center; padding: 20px; margin-top: 40px; }
        
        .badge { background: var(--accent); color: white; padding: 5px 10px; border-radius: 4px; font-size: 0.8rem; }
    </style>
</head>
<body>

<header>
    <h1>Integración Web - Segundo Parcial</h1>
    <p>Dominio: [TU_USUARIO].github.io</p>
</header>

<nav>
    <a href="#inicio">Inicio</a>
    <a href="#sesiones">Sesiones</a>
    <a href="#mantenimiento">Mantenimiento</a>
</nav>

<div class="container">
    
    <section id="inicio">
        <h2>Bienvenida</h2>
        <p>Este sitio web representa la integración de los conocimientos adquiridos durante el segundo cuatrimestre, fusionando el diseño web con los servicios de soporte técnico informático.</p>
    </section>

    <section id="sesiones">
        <h2>Sesiones Desarrolladas</h2>
        <div class="grid">
            <div class="card">
                <h3>Sesión 1: Maquetación</h3>
                <p>Definición de estructura semántica y boceto inicial del sitio.</p>
            </div>
            <div class="card">
                <h3>Sesión 2: Estilos CSS</h3>
                <p>Implementación de colores, tipografías y diseño responsivo.</p>
            </div>
            <div class="card">
                <h3>Sesión 3: Hosting y Dominio</h3>
                <p>Configuración del entorno de producción y despliegue en GitHub Pages.</p>
            </div>
        </div>
    </section>

    <section id="mantenimiento">
        <h2>Servicios de Mantenimiento Preventivo</h2>
        <p>Protocolos aplicados en el Taller de Informática para la optimización de equipos.</p>
        
        <div class="grid">
