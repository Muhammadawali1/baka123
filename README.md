<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Satiii kesayangankuuu</title>
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap">
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            font-family: 'Poppins', sans-serif;
            position: relative;
            color: white;
        }

        body::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url('background.jpg');
            background-size: cover;
            background-position: center;
            z-index: -2;
        }

        body::after {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.1);
            z-index: -1;
        }

        .lyrics-container {
            text-align: center;
            white-space: pre;
            padding: 20px;
            font-size: 24px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.8);
            z-index: 1;
        }

        .line {
            display: block;
            margin-bottom: 5px;
        }
    </style>
</head>
<body>
    <div class="lyrics-container" id="lyricsContainer">
    </div>
    <audio autoplay>
        <source src="12.mp3" type="audio/mpeg">
        
    </audio>
    <script>
        const lyrics = [
        "Janganlah kau tinggalkan diri ku",
        "Tak kan mampu menghadapi semua",
        "Hanya bersamamu ku akan bisa",
        "Kau adalah darah ku",
        "Kau adalah jantung ku",
        "Kau adalah hidup ku lengkapi diri ku",
         "Oh sayangku kau begitu",
         "Sempurnaaaaaaaaaaaaaaaaa"
        ];

        const delays = [0.5, 0.1, 0.6, 0.6, 0.6, 0.6];
        const speeds = [ 0.1, 0.12, 0.11, 0.10, 0.10, 0.10, 0.1, 0.1];

        function animateText(text, container, speed) {
            return new Promise((resolve) => {
                let i = 0;
                function typeChar() {
                    if (i < text.length) {
                        container.innerHTML += text.charAt(i);
                        i++;
                        setTimeout(typeChar, speed * 1000);
                    } else {
                        resolve();
                    }
                }
                typeChar();
            });
        }

        async function singSong() {
            const lyricsContainer = document.getElementById('lyricsContainer');
            for (let i = 0; i < lyrics.length; i++) {
                await new Promise(resolve => setTimeout(resolve, delays[i] * 1000));
                const lineContainer = document.createElement('span');
                lineContainer.classList.add('line');
                lyricsContainer.appendChild(lineContainer);
                await animateText(lyrics[i], lineContainer, speeds[i]);
            }
        }

        singSong();
    </script>
</body>
</html>
