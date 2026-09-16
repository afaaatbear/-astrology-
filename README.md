<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>占星室｜她們</title>
    <style>
        /* 基礎樣式重置與字體設定 */
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'PingFang TC', 'Microsoft JhengHei', sans-serif;
        }

        body {
            background: radial-gradient(circle at center, #1b1035 0%, #090514 100%);
            color: #f3e9ff;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
            position: relative;
        }

        /* 占星背景：閃爍星空動畫 */
        .stars {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            background: 
                radial-gradient(1.5px 1.5px at 20px 30px, #fff, rgba(0,0,0,0)),
                radial-gradient(2px 2px at 40px 70px, #e3b6ff, rgba(0,0,0,0)),
                radial-gradient(1px 1px at 90px 40px, #fff, rgba(0,0,0,0)),
                radial-gradient(2px 2px at 160px 120px, #ffd166, rgba(0,0,0,0)),
                radial-gradient(1.5px 1.5px at 230px 190px, #fff, rgba(0,0,0,0));
            background-repeat: repeat;
            background-size: 250px 250px;
            animation: starsSparkle 4s infinite alternate ease-in-out;
            opacity: 0.6;
        }

        @keyframes starsSparkle {
            0% { opacity: 0.3; transform: scale(1); }
            100% { opacity: 0.8; transform: scale(1.02); }
        }

        /* 主容器與頁面切換 */
        .container {
            width: 90%;
            max-width: 480px;
            padding: 40px 30px;
            background: rgba(20, 12, 38, 0.65);
            backdrop-filter: blur(16px);
            border: 1px solid rgba(199, 146, 234, 0.25);
            border-radius: 24px;
            box-shadow: 0 0 40px rgba(138, 43, 226, 0.25), inset 0 0 15px rgba(255, 255, 255, 0.05);
            text-align: center;
            position: relative;
            z-index: 10;
        }

        .step {
            display: none;
            opacity: 0;
            transition: opacity 0.8s ease, transform 0.8s ease;
            transform: translateY(15px);
        }

        .step.active {
            display: block;
            opacity: 1;
            transform: translateY(0);
        }

        /* 標題與內文樣式 */
        h1 {
            font-size: 1.8rem;
            letter-spacing: 4px;
            color: #ebd0ff;
            margin-bottom: 24px;
            text-shadow: 0 0 12px rgba(216, 180, 254, 0.6);
            font-weight: 500;
        }

        p.text-line {
            font-size: 1.05rem;
            line-height: 1.8;
            color: #d8c4eb;
            letter-spacing: 1.5px;
            margin-bottom: 25px;
        }

        /* 3D 水晶球外層容器 */
        .crystal-ball-container {
            position: relative;
            width: 170px;
            height: 170px;
            margin: 20px auto 30px;
        }

        /* 玻璃球頂層高光與立體陰影 */
        .crystal-ball-glass {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            border-radius: 50%;
            pointer-events: none;
            box-shadow: 
                0 0 30px rgba(168, 85, 247, 0.6),
                inset 0 0 25px rgba(255, 255, 255, 0.4),
                inset -12px -12px 25px rgba(15, 3, 30, 0.9);
            background: radial-gradient(circle at 30% 25%, rgba(255, 255, 255, 0.45) 0%, rgba(255, 255, 255, 0) 50%);
            animation: orbPulse 3s infinite alternate ease-in-out;
        }

        @keyframes orbPulse {
            0% { box-shadow: 0 0 25px rgba(168, 85, 247, 0.5), inset 0 0 20px rgba(255, 255, 255, 0.3), inset -12px -12px 25px rgba(15, 3, 30, 0.9); }
            100% { box-shadow: 0 0 50px rgba(216, 180, 254, 0.8), inset 0 0 35px rgba(255, 255, 255, 0.6), inset -12px -12px 25px rgba(15, 3, 30, 0.9); }
        }

        canvas#crystalCanvas {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            display: block;
            background: radial-gradient(circle at center, #2e1052 0%, #0d041a 100%);
        }

        .input-group {
            margin-top: 20px;
        }

        input[type="text"] {
            width: 100%;
            padding: 12px 20px;
            background: rgba(255, 255, 255, 0.07);
            border: 1px solid rgba(199, 146, 234, 0.4);
            border-radius: 30px;
            color: #fff;
            font-size: 1rem;
            text-align: center;
            outline: none;
            transition: all 0.3s ease;
            letter-spacing: 2px;
        }

        input[type="text"]:focus {
            border-color: #d8b4fe;
            box-shadow: 0 0 15px rgba(216, 180, 254, 0.4);
            background: rgba(255, 255, 255, 0.12);
        }

        input[type="text"]::placeholder {
            color: rgba(216, 196, 235, 0.5);
            letter-spacing: 1px;
        }

        /* 按鈕樣式 */
        .btn-submit {
            margin-top: 25px;
            width: 100%;
            padding: 14px;
            background: linear-gradient(135deg, #7c3aed 0%, #4c1d95 100%);
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 30px;
            color: #fff;
            font-size: 1rem;
            letter-spacing: 3px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(124, 58, 237, 0.4);
        }

        .btn-submit:hover {
            background: linear-gradient(135deg, #8b5cf6 0%, #5b21b6 100%);
            box-shadow: 0 6px 20px rgba(139, 92, 246, 0.6);
            transform: translateY(-2px);
        }

        /* 選項按鈕列表 (頁面 2) */
        .target-name-display {
            font-size: 1.2rem;
            color: #f3d5ff;
            margin-bottom: 25px;
            font-weight: bold;
            letter-spacing: 2px;
            text-shadow: 0 0 8px rgba(243, 213, 255, 0.5);
        }

        .options-list {
            display: flex;
            flex-direction: column;
            gap: 16px;
        }

        .option-card {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(199, 146, 234, 0.3);
            padding: 16px 20px;
            border-radius: 16px;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            justify-content: space-between;
            align-items: center;
            text-align: left;
        }

        .option-card:hover {
            background: rgba(139, 92, 246, 0.25);
            border-color: #d8b4fe;
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(139, 92, 246, 0.3);
        }

        .option-main {
            font-size: 1.05rem;
            color: #ffffff;
            letter-spacing: 1px;
        }

        .option-tag {
            font-size: 0.85rem;
            color: #c084fc;
            padding: 4px 10px;
            background: rgba(192, 132, 252, 0.15);
            border-radius: 12px;
            border: 1px solid rgba(192, 132, 252, 0.3);
            white-space: nowrap;
        }

        .btn-back {
            margin-top: 25px;
            background: transparent;
            border: none;
            color: rgba(216, 196, 235, 0.6);
            font-size: 0.9rem;
            cursor: pointer;
            letter-spacing: 1px;
            text-decoration: underline;
        }

        .btn-back:hover {
            color: #fff;
        }
    </style>
</head>
<body>

    <!-- 背景星空效果 -->
    <div class="stars"></div>

    <!-- 主內容區 -->
    <div class="container">
        
        <!-- 第一頁：召喚與輸入 -->
        <div class="step active" id="step1">
            <h1>歡迎來到占星室</h1>
            
            <!-- 3D 自轉 + 閃爍星光與流星水晶球 -->
            <div class="crystal-ball-container">
                <canvas id="crystalCanvas" width="170" height="170"></canvas>
                <div class="crystal-ball-glass"></div>
            </div>

            <p class="text-line">
                今天，宇宙允許妳靠近一個人的秘密<br>
            </p>

            <div class="input-group">
                <input type="text" id="targetName" placeholder="請對著水晶球，輸入她的名字..." autocomplete="off">
            </div>

            <button class="btn-submit" onclick="goToStep2()">開啟命運之門</button>
        </div>

        <!-- 第二頁：三大情報選擇 -->
        <div class="step" id="step2">
            <h1>星軌的指引</h1>
            <div class="target-name-display" id="displayName"></div>

            <div class="options-list">
                <!-- 選項 ① -->
                <div class="option-card" onclick="selectOption('人物情報')">
                    <span class="option-main">①「我想更了解她」</span>
                    <span class="option-tag">人物情報</span>
                </div>

                <!-- 選項 ② -->
                <div class="option-card" onclick="selectOption('匿名信情報')">
                    <span class="option-main">②「我想知道她的心意」</span>
                    <span class="option-tag">匿名信情報</span>
                </div>

                <!-- 選項 ③ -->
                <div class="option-card" onclick="selectOption('秘密大冒險')">
                    <span class="option-main">③「讓宇宙替妳勇敢一次」</span>
                    <span class="option-tag">秘密大冒險</span>
                </div>
            </div>

            <button class="btn-back" onclick="goToStep1()">← 重新對水晶球許願</button>
        </div>

    </div>

    <script>
        // 頁面轉場邏輯
        function goToStep2() {
            const nameInput = document.getElementById('targetName').value.trim();
            
            if (!nameInput) {
                alert('請先輸入妳最想了解的那個人的名字...');
                return;
            }

            document.getElementById('displayName').innerText = `關於「${nameInput}」`;

            document.getElementById('step1').classList.remove('active');
            setTimeout(() => {
                document.getElementById('step2').classList.add('active');
            }, 300);
        }

        function goToStep1() {
            document.getElementById('step2').classList.remove('active');
            setTimeout(() => {
                document.getElementById('step1').classList.add('active');
            }, 300);
        }

        function selectOption(type) {
            const name = document.getElementById('targetName').value.trim();
            alert(`【${type}】已經為妳解鎖，宇宙正在讀取關於 ${name} 的星象訊息...`);
        }

        /* --------------------------------------------------
           Canvas 3D 自轉 + 閃爍星光與隨機流星動畫
        -------------------------------------------------- */
        const canvas = document.getElementById('crystalCanvas');
        const ctx = canvas.getContext('2d');
        const width = canvas.width;
        const height = canvas.height;
        const centerX = width / 2;
        const centerY = height / 2;
        const globeRadius = width / 2 - 6;

        const starCount = 80;
        const stars = [];
        const colors = ['#ffffff', '#ebd0ff', '#c084fc', '#fef08a', '#93c5fd'];

        // 1. 3D 自轉球體閃爍星光
        class SphereStar {
            constructor() {
                this.theta = Math.random() * Math.PI * 2; // 經度
                this.phi = Math.acos((Math.random() * 2) - 1); // 緯度

                this.size = 0.8 + Math.random() * 1.8;
                this.color = colors[Math.floor(Math.random() * colors.length)];
                
                this.alpha = Math.random();
                this.twinkleSpeed = 0.015 + Math.random() * 0.03;
                this.twinkleDir = Math.random() > 0.5 ? 1 : -1;
            }

            update(rotationAngle) {
                // 水平沿 Y 軸自轉 (地球式自轉)
                const currentTheta = this.theta + rotationAngle;
                
                this.x3d = globeRadius * Math.sin(this.phi) * Math.cos(currentTheta);
                this.y3d = globeRadius * Math.cos(this.phi);
                this.z3d = globeRadius * Math.sin(this.phi) * Math.sin(currentTheta);

                this.canvasX = centerX + this.x3d;
                this.canvasY = centerY + this.y3d;

                // 閃爍效果
                this.alpha += this.twinkleSpeed * this.twinkleDir;
                if (this.alpha >= 1) {
                    this.alpha = 1;
                    this.twinkleDir = -1;
                } else if (this.alpha <= 0.1) {
                    this.alpha = 0.1;
                    this.twinkleDir = 1;
                }
            }

            draw() {
                if (this.z3d < -10) return; // 隱藏過深的背面星光

                const depthAlpha = Math.max(0, (this.z3d + 10) / (globeRadius + 10));
                const finalAlpha = this.alpha * depthAlpha;

                ctx.save();
                ctx.beginPath();
                ctx.arc(this.canvasX, this.canvasY, this.size, 0, Math.PI * 2);
                ctx.fillStyle = this.color;
                ctx.globalAlpha = finalAlpha;
                ctx.shadowBlur = 6;
                ctx.shadowColor = this.color;
                ctx.fill();
                ctx.restore();
            }
        }

        // 2. 水晶球內部隨機劃過的流星 (Shooting Star)
        class Meteor {
            constructor() {
                this.reset();
            }

            reset() {
                // 從水晶球左上方/頂部隨機位置生成
                this.x = centerX + (Math.random() - 0.7) * globeRadius;
                this.y = centerY - (0.5 + Math.random() * 0.5) * globeRadius;
                
                this.length = 25 + Math.random() * 30; // 流星尾巴長度
                this.speed = 3 + Math.random() * 2.5;  // 流星速度
                this.angle = Math.PI / 4 + (Math.random() - 0.5) * 0.2; // 斜向下 45 度劃過

                this.dx = Math.cos(this.angle) * this.speed;
                this.dy = Math.sin(this.angle) * this.speed;

                this.alpha = 1;
                this.active = false; // 是否在劃過狀態
                this.timer = Math.random() * 150; // 隨機觸發等待時間
            }

            update() {
                if (!this.active) {
                    this.timer--;
                    if (this.timer <= 0) {
                        this.active = true;
                    }
                    return;
                }

                this.x += this.dx;
                this.y += this.dy;
                this.alpha -= 0.02; // 漸漸消失

                // 超出球體範圍或完全透明時重置
                const dist = Math.hypot(this.x - centerX, this.y - centerY);
                if (dist > globeRadius - 5 || this.alpha <= 0) {
                    this.reset();
                }
            }

            draw() {
                if (!this.active || this.alpha <= 0) return;

                const tailX = this.x - Math.cos(this.angle) * this.length;
                const tailY = this.y - Math.sin(this.angle) * this.length;

                ctx.save();
                ctx.beginPath();
                ctx.moveTo(this.x, this.y);
                ctx.lineTo(tailX, tailY);

                // 流星漸層尾巴 (頭部亮白，尾部漸隱紫)
                const grad = ctx.createLinearGradient(this.x, this.y, tailX, tailY);
                grad.addColorStop(0, `rgba(255, 255, 255, ${this.alpha})`);
                grad.addColorStop(0.4, `rgba(216, 180, 254, ${this.alpha * 0.8})`);
                grad.addColorStop(1, `rgba(139, 92, 246, 0)`);

                ctx.strokeStyle = grad;
                ctx.lineWidth = 1.8;
                ctx.lineCap = 'round';
                ctx.shadowBlur = 8;
                ctx.shadowColor = '#ebd0ff';
                ctx.stroke();
                ctx.restore();
            }
        }

        // 初始化星光與流星
        for (let i = 0; i < starCount; i++) {
            stars.push(new SphereStar());
        }

        // 同時維持 2 顆流星在宇宙中輪流劃過
        const meteors = [new Meteor(), new Meteor()];

        let globeAngle = 0;

        function animate() {
            ctx.clearRect(0, 0, width, height);

            // 畫水晶球內部背景漸層
            const bgGradient = ctx.createRadialGradient(centerX, centerY, 5, centerX, centerY, globeRadius);
            bgGradient.addColorStop(0, '#3b1568');
            bgGradient.addColorStop(0.7, '#1b0836');
            bgGradient.addColorStop(1, '#090214');
            ctx.fillStyle = bgGradient;
            ctx.fillRect(0, 0, width, height);

            // 地球自轉 (由左向右)
            globeAngle += 0.007;

            // 按 Z 軸深度排序繪製星光
            stars.sort((a, b) => a.z3d - b.z3d);
            stars.forEach(star => {
                star.update(globeAngle);
                star.draw();
            });

            // 繪製與更新流星
            meteors.forEach(meteor => {
                meteor.update();
                meteor.draw();
            });

            requestAnimationFrame(animate);
        }

        animate();
    </script>
</body>
</html>
# -astrology-
⁠astrology⁠ room
