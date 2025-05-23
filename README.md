<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Mundo Cuento</title>
    <link href="https://fonts.googleapis.com/css2?family=Quicksand:wght@400;600&display=swap" rel="stylesheet">
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: 'Quicksand', sans-serif;
            background: linear-gradient(180deg, #f9f9f9, #e0f7fa);
            color: #333;
            padding-bottom: 80px;
        }

        header {
            background-color: #00acc1;
            color: white;
            padding: 30px 20px;
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }

        header h1 {
            font-size: 2.2em;
            font-weight: 600;
        }

        .busqueda {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            align-items: center;
        }

        .busqueda input {
            padding: 10px 15px;
            border: none;
            border-radius: 30px;
            width: 240px;
            transition: all 0.3s ease;
        }

        .busqueda input:focus {
            outline: none;
            box-shadow: 0 0 8px rgba(0, 172, 193, 0.6);
        }

        .busqueda button {
            background-color: #007c91;
            color: white;
            border: none;
            border-radius: 30px;
            padding: 10px 20px;
            cursor: pointer;
            font-weight: bold;
            transition: background 0.3s ease;
        }

        .busqueda button:hover {
            background-color: #005e6b;
        }

        main {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            padding: 30px 20px;
            gap: 20px;
        }

        .card {
            background-color: white;
            border-radius: 20px;
            overflow: hidden;
            width: 280px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            cursor: pointer;
        }

        .card:hover {
            transform: translateY(-8px);
            box-shadow: 0 8px 30px rgba(0, 0, 0, 0.15);
        }

        .card img {
            width: 100%;
            height: 200px;
            object-fit: cover;
        }

        .card-title {
            padding: 15px;
            font-size: 1.2em;
            font-weight: 600;
            text-align: center;
        }

        .contenido-cuento {
            display: none;
            background-color: #ffffff;
            padding: 30px;
            max-width: 800px;
            margin: 30px auto;
            border-radius: 20px;
            box-shadow: 0 8px 20px rgba(0,0,0,0.1);
            line-height: 1.8;
            animation: fadeIn 0.5s ease-in-out;
        }

        .contenido-cuento.activo {
            display: block;
        }

        .contenido-cuento h2 {
            margin-bottom: 10px;
        }

        .contenido-cuento img {
            width: 100%;
            max-height: 300px;
            object-fit: cover;
            border-radius: 15px;
            margin-bottom: 20px;
        }

        .mensaje-error {
            text-align: center;
            color: red;
            font-weight: bold;
            margin-top: 20px;
            display: none;
        }

        footer {
            background-color: #004d57;
            color: white;
            text-align: center;
            padding: 15px;
            position: fixed;
            width: 100%;
            bottom: 0;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @media (max-width: 600px) {
            header {
                flex-direction: column;
                text-align: center;
            }

            .busqueda {
                flex-direction: column;
                align-items: center;
            }

            .busqueda input {
                width: 90%;
            }
        }
    </style>
</head>
<body>

<header>
    <h1>Mundo Cuento</h1>
    <div class="busqueda">
        <input type="text" id="busqueda-input" placeholder="Buscar cuento..." oninput="buscarCuento()">
        <button onclick="buscarCuento()">Buscar</button>
    </div>
</header>

<main id="galeria">
    <div class="card" onclick="mostrarCuento('caperucita-roja')" data-cuento="Caperucita Roja">
        <img src="https://losresumenes.com/wp-content/uploads/2023/11/Hermanos-Grimm-Caperucita-Roja-Imagen-1.jpg" alt="Caperucita Roja">
        <div class="card-title">Caperucita Roja</div>
    </div>
    <div class="card" onclick="mostrarCuento('tres-chanchitos')" data-cuento="Los Tres Chanchitos">
        <img src="https://i1.sndcdn.com/artworks-000412660605-3xgsjx-t1080x1080.jpg" alt="Los Tres Chanchitos">
        <div class="card-title">Los Tres Chanchitos</div>
    </div>
    <div class="card" onclick="mostrarCuento('hada-dientes')" data-cuento="El Hada de los Dientes">
        <img src="https://images.cdn1.buscalibre.com/fit-in/360x360/b7/ed/b7edbff90292aaf25e23ae6fd96c2053.jpg" alt="El Hada de los Dientes">
        <div class="card-title">El Hada de los Dientes</div>
    </div>
</main>

<p class="mensaje-error" id="mensaje-error">No se encontró ningún cuento con ese nombre.</p>

<!-- CUENTOS -->
<section id="caperucita-roja" class="contenido-cuento">
    <h2>Caperucita Roja</h2>
    <img src="https://losresumenes.com/wp-content/uploads/2023/11/Hermanos-Grimm-Caperucita-Roja-Imagen-1.jpg" alt="Caperucita Roja">
    <p>Había una vez una niña llamada Caperucita Roja...</p>
    <p>Un lobo la engañó y se comió a su abuelita, pero un valiente cazador las rescató.</p>
</section>

<section id="tres-chanchitos" class="contenido-cuento">
    <h2>Los Tres Chanchitos</h2>
    <img src="https://i1.sndcdn.com/artworks-000412660605-3xgsjx-t1080x1080.jpg" alt="Los Tres Chanchitos">
    <p>Los tres cerditos construyeron casas de paja, madera y ladrillo...</p>
    <p>El lobo derribó las más débiles, pero no pudo con la casa fuerte de ladrillo.</p>
</section>

<section id="hada-dientes" class="contenido-cuento">
    <h2>El Hada de los Dientes</h2>
    <img src="https://images.cdn1.buscalibre.com/fit-in/360x360/b7/ed/b7edbff90292aaf25e23ae6fd96c2053.jpg" alt="El Hada de los Dientes">
    <p>Sofía dejó su diente bajo la almohada, y el hada le dejó una moneda brillante.</p>
    <p>Desde ese día, cuida sus dientes esperando otra visita mágica.</p>
</section>

<footer>
    <p>&copy; 2025 Mundo Cuento - JHOEL AGUILAR</p>
</footer>

<script>
    function mostrarCuento(id) {
        document.querySelectorAll('.contenido-cuento').forEach(c => c.classList.remove('activo'));
        document.getElementById(id).classList.add('activo');
        document.getElementById('mensaje-error').style.display = 'none';
        window.scrollTo({ top: 0, behavior: 'smooth' });
    }

    function buscarCuento() {
        const input = document.getElementById('busqueda-input').value.toLowerCase();
        const cards = document.querySelectorAll('.card');
        const cuentos = document.querySelectorAll('.contenido-cuento');
        let encontrado = false;

        // Ocultar todos
        cards.forEach(card => card.style.display = 'none');
        cuentos.forEach(cont => cont.classList.remove('activo'));

        cards.forEach(card => {
            const titulo = card.getAttribute('data-cuento').toLowerCase();
            const id = card.getAttribute('onclick').match(/'([^']+)'/)[1];
            if (titulo.includes(input)) {
                card.style.display = 'block';
                document.getElementById(id).classList.add('activo');
                encontrado = true;
            }
        });

        document.getElementById('mensaje-error').style.display = (!encontrado && input) ? 'block' : 'none';
    }
</script>

</body>
</html>
