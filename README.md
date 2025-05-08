<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Phone Hack Prank</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            background: #000;
            color: #0f0;
            font-family: 'Courier New', monospace;
            overflow: hidden;
        }
        #canvas {
            position: absolute;
            top: 0;
            left: 0;
            z-index: -1;
        }
        #console {
            padding: 20px;
            font-size: 16px;
            line-height: 1.5;
            text-align: center;
        }
        .popup {
            position: absolute;
            background: #000;
            border: 2px solid #0f0;
            padding: 10px;
            color: #0f0;
            font-size: 14px;
            animation: blink 1s infinite;
        }
        @keyframes blink {
            50% { opacity: 0.5; }
        }
        #reveal {
            display: none;
            font-size: 24px;
            color: #ff0;
            text-align: center;
            margin-top: 20%;
        }
    </style>
</head>
<body>
    <canvas id="canvas"></canvas>
    <div id="console"></div>
    <div id="reveal">Gotcha! This was just a prank! 😜</div>

    <script>
        // Matrix digital rain effect
        const canvas = document.getElementById('canvas');
        const ctx = canvas.getContext('2d');
        canvas.height = window.innerHeight;
        canvas.width = window.innerWidth;
        const chars = '010101ABCDEFGHIJKLMNOPQRSTUVWXYZ';
        const fontSize = 14;
        const columns = canvas.width / fontSize;
        const drops = [];

        for (let x = 0; x < columns; x++) drops[x] = 1;

        function draw() {
            ctx.fillStyle = 'rgba(0, 0, 0, 0.05)';
            ctx.fillRect(0, 0, canvas.width, canvas.height);
            ctx.fillStyle = '#0F0';
            ctx.font = fontSize + 'px monospace';
            for (let i = 0; i < drops.length; i++) {
                const text = chars.charAt(Math.floor(Math.random() * chars.length));
                ctx.fillText(text, i * fontSize, drops[i] * fontSize);
                if (drops[i] * fontSize > canvas.height && Math.random() > 0.975)
                    drops[i] = 0;
                drops[i]++;
            }
        }
        setInterval(draw, 33);

        // Fake console messages
        const console = document.getElementById('console');
        const messages = [
            'Initializing hack...',
            'Bypassing firewall...',
            'Accessing device storage...',
            'Decrypting data...',
            'Uploading to server...',
            'System compromised!'
        ];
        let i = 0;
        function showMessage() {
            if (i < messages.length) {
                console.innerHTML += messages[i] + '<br>';
                i++;
            } else {
                console.innerHTML = 'Connection established.<br>';
            }
        }
        setInterval(showMessage, 3000);

        // Random pop-ups
        function createPopup() {
            const popup = document.createElement('div');
            popup.className = 'popup';
            popup.innerText = 'Alert: Unauthorized access detected!';
            popup.style.left = Math.random() * (window.innerWidth - 200) + 'px';
            popup.style.top = Math.random() * (window.innerHeight - 100) + 'px';
            document.body.appendChild(popup);
            setTimeout(() => popup.remove(), 2000);
        }
        setInterval(createPopup, 5000);

        // Reveal prank after 30 seconds
        setTimeout(() => {
            document.getElementById('reveal').style.display = 'block';
            console.style.display = 'none';
        }, 30000);
    </script>
</body>
</html>
