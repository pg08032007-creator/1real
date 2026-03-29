<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pergunta Séria!</title>
    <style>
        * { margin: 0; padding: 0; box-box-sizing: border-box; }

        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: radial-gradient(circle, #2c3e50, #000000);
            font-family: 'Arial', sans-serif;
            color: white;
            overflow: hidden;
        }

        #painel {
            text-align: center;
            background: rgba(255, 255, 255, 0.1);
            padding: 40px;
            border-radius: 20px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            box-shadow: 0 0 30px rgba(0,0,0,0.5);
            max-width: 400px;
            width: 90%;
        }

        img {
            width: 150px;
            border-radius: 50%;
            margin-bottom: 20px;
            border: 4px solid #f1c40f;
        }

        h1 {
            font-size: 1.8rem;
            margin-bottom: 30px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
        }

        .botoes {
            display: flex;
            justify-content: space-around;
            align-items: center;
            height: 60px;
        }

        button {
            padding: 12px 25px;
            font-size: 1.1rem;
            font-weight: bold;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        #sim {
            background-color: #27ae60;
            color: white;
            box-shadow: 0 4px 15px rgba(39, 174, 96, 0.4);
        }

        #sim:hover { transform: scale(1.1); background-color: #2ecc71; }

        #nao {
            background-color: #e74c3c;
            color: white;
            position: absolute; /* Necessário para a fuga */
            transition: 0.1s ease;
        }
    </style>
</head>
<body>

    <div id="painel">
        <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExNHJidWJycXN1bmR1dzR6bmZ3bmZ3bmZ3bmZ3bmZ3bmZ3bmZ3bmZ3JmVwPXYxX2ludGVybmFsX2dpZl9ieV9pZCZjdD1n/3o751XDbTvRZ9iFEQg/giphy.gif" alt="Dinheiro">
        <h1>E aí, você tem um real? 🧐</h1>
        <div class="botoes">
            <button id="sim">SIM!</button>
            <button id="nao">NÃO</button>
        </div>
    </div>

    <script>
        const btnNao = document.getElementById('nao');
        const btnSim = document.getElementById('sim');

        // Função que faz o botão fugir
        function desvia() {
            // Calcula posições aleatórias, mas mantendo o botão dentro da área visível
            const maxX = window.innerWidth - btnNao.offsetWidth - 20;
            const maxY = window.innerHeight - btnNao.offsetHeight - 20;

            const randomX = Math.floor(Math.random() * maxX);
            const randomY = Math.floor(Math.random() * maxY);

            btnNao.style.left = randomX + 'px';
            btnNao.style.top = randomY + 'px';
        }

        // Eventos para Desktop e Mobile
        btnNao.addEventListener('mouseover', desvia);
        btnNao.addEventListener('touchstart', (e) => {
            e.preventDefault(); // Evita o clique no celular
            desvia();
        });

        btnSim.addEventListener('click', () => {
            document.getElementById('painel').innerHTML = `
                <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExNHJidWJycXN1bmR1dzR6bmZ3bmZ3bmZ3bmZ3bmZ3bmZ3bmZ3bmZ3JmVwPXYxX2ludGVybmFsX2dpZl9ieV9pZCZjdD1n/l0Ex6kAKAoFRsFh6M/giphy.gif">
                <h1>Sabia! Manda o PIX então! 💸</h1>
                <p style="margin-top:10px">Obrigado pela humildade.</p>
            `;
        });
    </script>
</body>
</html>
