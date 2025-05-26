<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Mi Web para Adultos</title>
  <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
  <style>
    body {
      background-color: #0a0e1a;
      color: #ffffff;
    }
    .video-card {
      cursor: pointer;
      transition: transform 0.2s ease;
    }
    .video-card:hover {
      transform: scale(1.05);
      background-color: #1f2a44;
    }
  </style>
  <script>
    let usuarioAutenticado = false;

    function iniciarSesion(event) {
      event.preventDefault();
      usuarioAutenticado = true;
      alert('Sesión iniciada');
      document.getElementById('botonPremium').innerText = 'Acceso concedido';
      document.getElementById('botonPremium').disabled = true;
    }

    function subirComentario(event) {
      event.preventDefault();
      const comentario = document.getElementById('comentarioInput').value;
      const contenedor = document.getElementById('comentariosPublicados');
      if (comentario.trim() !== '') {
        const nuevoComentario = document.createElement('p');
        nuevoComentario.className = 'bg-gray-700 p-2 my-2 rounded';
        nuevoComentario.innerText = comentario;
        contenedor.appendChild(nuevoComentario);
        document.getElementById('comentarioInput').value = '';
      }
    }

    function subirVideo(event) {
      event.preventDefault();
      alert('Video subido correctamente (simulado)');
    }

    function abrirVideo(titulo) {
      const ventana = window.open('', '_blank');
      ventana.document.write(`
        <html>
          <head>
            <title>${titulo}</title>
            <style>
              body { margin: 0; background-color: #000; display: flex; justify-content: center; align-items: center; height: 100vh; }
              video { max-width: 90vw; max-height: 90vh; }
            </style>
          </head>
          <body>
            <video controls autoplay>
              <source src="https://www.w3schools.com/html/mov_bbb.mp4" type="video/mp4">
              Tu navegador no soporta el video.
            </video>
          </body>
        </html>
      `);
    }
  </script>
</head>
<body>
  <header class="bg-gradient-to-r from-indigo-900 to-blue-900 p-4 flex justify-between items-center">
    <h1 class="text-2xl font-bold">AdultFlix</h1>
    <nav class="space-x-4">
      <a href="#inicio" class="hover:underline">Inicio</a>
      <a href="#galeria" class="hover:underline">Galería</a>
      <a href="#modelos" class="hover:underline">Modelos</a>
      <a href="#premium" class="hover:underline">Premium</a>
      <a href="#comentarios" class="hover:underline">Comentarios</a>
      <a href="#subir" class="hover:underline">Subir Video</a>
      <a href="#login" class="hover:underline">Iniciar sesión</a>
    </nav>
  </header>

  <main class="p-6 space-y-10">
    <section id="inicio">
      <h2 class="text-3xl font-semibold mb-4">Bienvenido a AdultFlix</h2>
      <p>Explora contenido exclusivo con estilo y privacidad.</p>
    </section>

    <section id="galeria">
      <h2 class="text-2xl font-semibold mb-4">Galería</h2>
      <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
        <div onclick="abrirVideo('Video 1')" class="video-card bg-gray-900 rounded p-2 text-center">Video 1</div>
        <div onclick="abrirVideo('Video 2')" class="video-card bg-gray-900 rounded p-2 text-center">Video 2</div>
        <div onclick="abrirVideo('Video 3')" class="video-card bg-gray-900 rounded p-2 text-center">Video 3</div>
        <div onclick="abrirVideo('Video 4')" class="video-card bg-gray-900 rounded p-2 text-center">Video 4</div>
      </div>
    </section>

    <section id="modelos">
      <h2 class="text-2xl font-semibold mb-4">Modelos</h2>
      <p>Conoce a nuestras estrellas.</p>
    </section>

    <section id="premium">
      <h2 class="text-2xl font-semibold mb-4">Contenido Premium</h2>
      <div class="bg-purple-900 p-4 rounded text-center">
        <p class="mb-2">Solo usuarios registrados pueden acceder al contenido premium.</p>
        <button id="botonPremium" class="bg-white text-black font-bold px-4 py-2 rounded">Acceder (requiere cuenta)</button>
      </div>
    </section>

    <section id="comentarios">
      <h2 class="text-2xl font-semibold mb-4">Comentarios</h2>
      <form onsubmit="subirComentario(event)">
        <textarea id="comentarioInput" class="w-full p-2 text-black rounded" placeholder="Escribe tu comentario..."></textarea>
        <button type="submit" class="mt-2 bg-blue-600 px-4 py-2 rounded">Publicar</button>
      </form>
      <div id="comentariosPublicados" class="mt-4 space-y-2"></div>
    </section>

    <section id="subir">
      <h2 class="text-2xl font-semibold mb-4">Subir Video (Admin)</h2>
      <form class="space-y-4" onsubmit="subirVideo(event)">
        <input type="text" placeholder="Título del video" class="w-full p-2 text-black rounded" required />
        <input type="file" class="w-full p-2 text-black rounded" required />
        <button type="submit" class="bg-green-600 px-4 py-2 rounded">Subir</button>
      </form>
    </section>

    <section id="login">
      <h2 class="text-2xl font-semibold mb-4">Iniciar Sesión / Registro</h2>
      <form class="space-y-4" onsubmit="iniciarSesion(event)">
        <input type="email" placeholder="Correo" class="w-full p-2 text-black rounded" required />
        <input type="password" placeholder="Contraseña" class="w-full p-2 text-black rounded" required />
        <button type="submit" class="bg-purple-600 px-4 py-2 rounded">Entrar</button>
      </form>
    </section>
  </main>
</body>
</html>
