<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Proyecto Musical Universitario</title>
    <style>
        body, html {
            margin: 0;
            padding: 0;
            height: 100%;
            overflow: hidden;
        }
        #background {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-size: cover;
            transition: background-image 1s ease-in-out;
            z-index: 1;
        }
        #controls {
            position: fixed;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            z-index: 1000;
        }
        #video-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 2;
        }
        video {
            width: 90%;
            height: 90%;
            object-fit: cover;
        }
    </style>
</head>
<body>
    <div id="background"></div>
    
    <div id="video-container">
        <video id="myVideo"muted>
            <source src="ssstik.io_@whoispinkman_1727131245794.mp4" type="video/mp4">
            Tu navegador no soporta el elemento de video.
        </video>
    </div>

    <div id="controls">
        <audio controls id="song">
            <source src="ssstik.io_1729655501671.mp3" type="audio/mpeg">
           
        </audio>
    </div>

    <script>
        const audio = document.getElementById('song');
        const background = document.getElementById('background');
        const video = document.getElementById('myVideo');
        const images = [
            'ruta_imagen1.jpg',
            'ruta_imagen2.jpg',
            'ruta_imagen3.jpg',
            // Añade más rutas de imágenes según sea necesario
        ];
        let currentImage = 0;

        // Intenta reproducir automáticamente
        window.addEventListener('load', function() {
            audio.play().catch(function(error) {
                console.log("La reproducción automática de audio fue bloqueada por el navegador.");
            });
            video.play().catch(function(error) {
                console.log("La reproducción automática de video fue bloqueada por el navegador.");
            });
        });

        audio.addEventListener('timeupdate', function() {
            // Cambia la imagen cada 5 segundos
            if (Math.floor(audio.currentTime) % 5 === 0) {
                background.style.backgroundImage = `url(${images[currentImage]})`;
                currentImage = (currentImage + 1) % images.length;
            }
        });

        // Sincroniza el video con el audio
        audio.addEventListener('play', function() {
            video.play();
        });

        audio.addEventListener('play', function() {
            video.play();
        });

        audio.addEventListener('seeked', function() {
            video.currentTime = audio.currentTime;
        });
    </script>
</body>
</html>
