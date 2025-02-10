<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Walentynka</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 50px;
            background: url('walentynki-2021-kiedy-wypadaja-historia-walentynek-i-zyczenia.jpg') no-repeat center center fixed;
            background-size: cover;
            color: white;
            text-shadow: 2px 2px 5px black;
            overflow: hidden;
        }
        .hidden {
            display: none;
            opacity: 0;
            transition: opacity 1s ease-in-out;
        }
        .visible {
            display: block;
            opacity: 1;
        }
        .red {
            color: red;
            position: fixed;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            font-size: 18px;
            font-weight: bold;
            text-shadow: 2px 2px 5px black;
        }
        .final-text {
            position: fixed;
            top: 20%;
            left: 50%;
            transform: translate(-50%, -50%);
            text-align: center;
            color: white;
        }
        .final-text h1 {
            font-size: 32px;
            font-weight: bold;
        }
        .final-text p {
            font-size: 14px;
        }
        button {
            margin: 10px;
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
            border: none;
            border-radius: 5px;
            background-color: rgba(255, 255, 255, 0.8);
            transition: transform 0.3s ease, background-color 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        button:hover {
            transform: scale(1.1);
            background-color: rgba(255, 255, 255, 1);
        }
        .heart {
            position: absolute;
            font-size: 24px;
            color: red;
            left: 50%;
            transform: translateX(-50%);
            animation: floatUp 1s ease-out forwards;
        }
        @keyframes floatUp {
            0% { transform: translateY(0) scale(1); opacity: 1; }
            100% { transform: translateY(-70px) scale(1.5); opacity: 0; }
        }
    </style>
</head>
<body>

    <div id="pytanie1" class="visible">
        <h1>Zostaniesz moją WALENTYNKĄ?</h1>
        <button onclick="tak(event)">Tak.</button>
        <button onclick="nie(event)">Nie.</button>
    </div>

    <div id="odmowa" class="hidden">
        <h1>No chyba coś cię boli.</h1>
        <button onclick="cofnij()">Cofnij.</button>
    </div>

    <div id="pytanie2" class="hidden">
        <h1>No to co? Widzimy się w piątek.</h1>
        <button onclick="wybierzOpcje(event)">Tak.</button>
        <button onclick="wybierzOpcje(event)">Tak.</button>
    </div>

    <div id="wybor" class="hidden">
        <h1>Co byś chciała?</h1>
        <button onclick="final(event)">Upojny wieczór.</button>
        <button onclick="final(event)">Granie w Lego.</button>
        <button onclick="final(event)">Oglądanie Netflixa i kolacja.</button>
        <button onclick="final(event)">Wszystko.</button>
    </div>

    <div id="finalny" class="hidden">
        <div class="final-text">
            <h2>Piątek godzina 18 u Ciebie, MYSIU PYSIU.</h2>
            <h1>RA-ZCEQ58E6AQFTGLCM</h1>
            <p>Kup sobie ładnego skina do Kai'Sy.</p>
        </div>
        <p class="red">Nie wiem, co wybrałaś. Możesz napisać mi, ale nie musisz.  
        Ale jak nie napiszesz, musisz zrobić tak, żebym się domyślił, co wybrałaś.</p>
    </div>

    <script>
        function showSection(hideId, showId) {
            document.getElementById(hideId).classList.remove("visible");
            document.getElementById(hideId).classList.add("hidden");
            setTimeout(() => {
                document.getElementById(showId).classList.remove("hidden");
                document.getElementById(showId).classList.add("visible");
            }, 500);
        }

        function tak(event) { showSection("pytanie1", "pytanie2"); createHearts(event); }
        function nie(event) { showSection("pytanie1", "odmowa"); createHearts(event); }
        function wybierzOpcje(event) { showSection("pytanie2", "wybor"); createHearts(event); }
        function final(event) { showSection("wybor", "finalny"); createHearts(event); }

        function createHearts(event) {
            let button = event.target;
            for (let i = 0; i < 8; i++) { // Więcej serduszek
                let heart = document.createElement("div");
                heart.classList.add("heart");
                heart.innerHTML = "❤️";
                heart.style.top = "-10px";
                heart.style.animationDuration = `${0.8 + Math.random() * 0.7}s`;
                button.appendChild(heart);
                setTimeout(() => { heart.remove(); }, 1000);
            }
        }
    </script>
</body>
</html>
