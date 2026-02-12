# fish.githuib.io
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Will You Be My Valentine? 💕</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Comic Sans MS', 'Arial', sans-serif;
            background: #ffb3d9;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
        }

        .container {
            text-align: center;
            background: white;
            padding: 50px 40px;
            border-radius: 20px;
            border: 4px solid #ff69b4;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            position: relative;
            z-index: 10;
            max-width: 600px;
        }

        .fish-emoji {
            font-size: 5em;
            margin-bottom: 20px;
            animation: swim 2s ease-in-out infinite;
        }

        @keyframes swim {
            0%, 100% { transform: translateX(0) rotate(0deg); }
            50% { transform: translateX(10px) rotate(5deg); }
        }

        h1 {
            color: #ff1493;
            font-size: 2.5em;
            margin-bottom: 30px;
            font-weight: bold;
            line-height: 1.3;
        }

        .buttons {
            display: flex;
            gap: 20px;
            justify-content: center;
            align-items: center;
            margin-top: 30px;
        }

        button {
            font-family: 'Comic Sans MS', 'Arial', sans-serif;
            font-size: 1.8em;
            padding: 15px 35px;
            border: 3px solid #333;
            border-radius: 10px;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.3s ease;
            box-shadow: 5px 5px 0px #333;
        }

        button:active {
            box-shadow: 2px 2px 0px #333;
            transform: translate(3px, 3px);
        }

        #yesBtn {
            background: #4CAF50;
            color: white;
        }

        #yesBtn:hover {
            background: #45a049;
        }

        #noBtn {
            background: #f44336;
            color: white;
            font-size: 1.3em;
        }

        #noBtn:hover {
            background: #da190b;
        }

        .heart {
            position: fixed;
            font-size: 3em;
            animation: fall 3s linear;
            z-index: 1000;
            pointer-events: none;
        }

        @keyframes fall {
            to {
                transform: translateY(100vh) rotate(360deg);
                opacity: 0;
            }
        }

        .success-message {
            display: none;
            font-size: 2em;
            color: #ff1493;
            margin-top: 30px;
            font-weight: bold;
            animation: bounce 0.5s ease;
        }

        @keyframes bounce {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.2); }
        }

        .meme-text {
            font-size: 0.9em;
            color: #666;
            margin-top: 15px;
            font-style: italic;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="fish-emoji">🐟</div>
        <h1>Will u be my valentine fish? 💕</h1>
        <p class="meme-text">*nervously swimming around*</p>
        <div class="buttons">
            <button id="yesBtn">Yes</button>
            <button id="noBtn">No</button>
        </div>
        <div class="success-message" id="successMsg">OMG YES! 🐠💖 *happy fish noises*</div>
    </div>

    <script>
        const yesBtn = document.getElementById('yesBtn');
        const noBtn = document.getElementById('noBtn');
        const successMsg = document.getElementById('successMsg');
        let noClickCount = 0;
        let yesBtnScale = 1;

        yesBtn.addEventListener('click', () => {
            // Hide buttons
            yesBtn.style.display = 'none';
            noBtn.style.display = 'none';
            
            // Hide meme text
            document.querySelector('.meme-text').style.display = 'none';
            
            // Show success message
            successMsg.style.display = 'block';
            
            // Create heart shower
            createHeartShower();
        });

        const memeTexts = [
            '*nervously swimming around*',
            'pls this is awkward now 😳',
            '*sad fish noises* 🐠💔',
            'u really gonna do me like that? 😭',
            'ok fine im literally begging'
        ];

        noBtn.addEventListener('click', () => {
            noClickCount++;
            
            // Update meme text
            const memeTextElement = document.querySelector('.meme-text');
            if (noClickCount <= 5) {
                memeTextElement.textContent = memeTexts[noClickCount];
            }
            
            // Cycle through different messages
            if (noClickCount === 1) {
                noBtn.textContent = 'Are you sure?';
                yesBtnScale += 0.3;
            } else if (noClickCount === 2) {
                noBtn.textContent = 'Pleaseee? 🥺';
                yesBtnScale += 0.4;
            } else if (noClickCount === 3) {
                noBtn.textContent = 'I will cry if u dont say yes 😢';
                yesBtnScale += 0.5;
            } else if (noClickCount === 4) {
                noBtn.textContent = 'One last time please 🙏';
                yesBtnScale += 0.6;
            } else if (noClickCount >= 5) {
                noBtn.textContent = 'Yes';
                noBtn.style.background = '#4CAF50';
                noBtn.style.color = 'white';
                // Make it act like the yes button now
                noBtn.onclick = () => {
                    yesBtn.style.display = 'none';
                    noBtn.style.display = 'none';
                    successMsg.style.display = 'block';
                    document.querySelector('.meme-text').style.display = 'none';
                    createHeartShower();
                };
                yesBtnScale = 4;
            }
            
            yesBtn.style.transform = `scale(${yesBtnScale})`;
        });

        function createHeartShower() {
            const hearts = ['❤️', '💕', '💖', '💗', '💓', '💝', '💘', '💞'];
            
            // Create 100 hearts
            for (let i = 0; i < 100; i++) {
                setTimeout(() => {
                    const heart = document.createElement('div');
                    heart.className = 'heart';
                    heart.textContent = hearts[Math.floor(Math.random() * hearts.length)];
                    heart.style.left = Math.random() * 100 + 'vw';
                    heart.style.animationDuration = (Math.random() * 2 + 2) + 's';
                    heart.style.opacity = Math.random() * 0.5 + 0.5;
                    document.body.appendChild(heart);
                    
                    // Remove heart after animation
                    setTimeout(() => {
                        heart.remove();
                    }, 4000);
                }, i * 50);
            }
        }
    </script>
</body>
</html>
