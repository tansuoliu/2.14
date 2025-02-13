<情人节礼物>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>独一无二的情人节礼物</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #ff9a9e, #fad0c4);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            overflow: hidden;
        }
        .container {
            text-align: center;
            background: rgba(255, 255, 255, 0.8);
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
            max-width: 400px;
            width: 100%;
        }
        h1 {
            color: #ff6f61;
            font-size: 2.5em;
            margin-bottom: 20px;
        }
        input {
            width: 80%;
            padding: 10px;
            margin: 10px 0;
            border: 2px solid #ff6f61;
            border-radius: 5px;
            font-size: 1em;
        }
        button {
            background: #ff6f61;
            color: white;
            border: none;
            padding: 10px 20px;
            font-size: 1em;
            border-radius: 5px;
            cursor: pointer;
            transition: background 0.3s ease;
        }
        button:hover {
            background: #ff3b2f;
        }
        .message {
            margin-top: 20px;
            font-size: 1.2em;
            color: #333;
            opacity: 0;
            animation: fadeIn 2s forwards;
        }
        @keyframes fadeIn {
            to {
                opacity: 1;
            }
        }
        .heart {
            position: absolute;
            top: -10%;
            font-size: 2em;
            color: #ff6f61;
            animation: fall 5s linear infinite;
        }
        @keyframes fall {
            to {
                transform: translateY(110vh);
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>💖 情人节快乐！ 💖</h1>
        <p>请输入你们的名字，生成独一无二的祝福：</p>
        <input type="text" id="loverName" placeholder="你爱人的名字">
        <input type="text" id="yourName" placeholder="你的名字">
        <button onclick="generateMessage()">生成祝福</button>
        <div id="message" class="message"></div>
    </div>

    <!-- 动态爱心 -->
    <div id="hearts"></div>

    <script>
        function generateMessage() {
            const loverName = document.getElementById('loverName').value;
            const yourName = document.getElementById('yourName').value;
            const messageDiv = document.getElementById('message');

            if (!loverName || !yourName) {
                alert('请输入完整的名字哦！');
                return;
            }

            const messages = [
                `亲爱的${loverName}，`,
                `在这个特别的日子里，我想对你说：`,
                `你是我生命中最美好的存在，`,
                `每一天与你在一起都是幸福的时光。`,
                `无论未来如何，我都会一直爱你、珍惜你。`,
                `爱你的，${yourName} 💕`
            ];

            messageDiv.innerHTML = messages.join('<br>');
        }

        // 动态生成爱心
        function createHearts() {
            const heartsContainer = document.getElementById('hearts');
            for (let i = 0; i < 20; i++) {
                const heart = document.createElement('div');
                heart.className = 'heart';
                heart.innerHTML = '❤️';
                heart.style.left = `${Math.random() * 100}vw`;
                heart.style.animationDuration = `${Math.random() * 3 + 2}s`;
                heartsContainer.appendChild(heart);
            }
        }

        // 初始化爱心
        createHearts();
    </script>
</body>
</html>
