<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Albúm de Videos :' </title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 50px;
        }

        #fileInput {
            display: none;
        }

        #fileLabel {
            padding: 10px;
            background-color: #4CAF50;
            color: white;
            cursor: pointer;
        }

        #videoList {
            margin-top: 20px;
            white-space: nowrap; /* Evita el retorno de línea en la lista de videos */
            overflow-x: auto; /* Agrega una barra de desplazamiento horizontal si es necesario */
        }
        .video-container {
            display: inline-block;
            vertical-align: top; /* Alinea los videos en la parte superior de la línea */
            margin-right: 10px; /* Espacio entre videos */
        }
    </style>
</head>
<body>
    <h1>Álbum de videos❤️</h1>

    <!-- Input para seleccionar archivos -->
    <input type="file" id="fileInput" accept="video/*" multiple>
    <label for="fileInput" id="fileLabel">Seleccionar Videos</label>

    <!-- Lista para mostrar archivos subidos -->
    <div id="videoList"></div>

    <script>
        // Función para manejar el evento de cambio en el input de archivos
        function handleFileSelect(event) {
            const fileList = event.target.files;
            const videoList = document.getElementById('videoList');

            for (const file of fileList) {
                if (file.type.startsWith('video/')) {
                    const videoContainer = document.createElement('div');
                    videoContainer.className = 'video-container';

                    const video = document.createElement('video');
                    video.src = URL.createObjectURL(file);
                    video.controls = true;

                    videoContainer.appendChild(video);
                    videoList.appendChild(videoContainer);
                }
            }
        }

        // Obtener referencias a los elementos DOM
        const fileInput = document.getElementById('fileInput');
        const fileLabel = document.getElementById('fileLabel');

        // Asignar el manejador de eventos al input de archivos
        fileInput.addEventListener('change', handleFileSelect);

        // Cambiar el texto del label al seleccionar archivos
        fileInput.addEventListener('change', function () {
            fileLabel.textContent = fileInput.files.length > 1
                ? `${fileInput.files.length} Archivos Seleccionados`
                : fileInput.files[0].name;
        });
    </script>
</body>
</html>
