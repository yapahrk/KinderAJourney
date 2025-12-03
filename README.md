
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kinder A Journey V.3 - Ultimate Pastel</title>
    <link href="https://fonts.googleapis.com/css2?family=Sarabun:wght@300;400;600;800&display=swap" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

    <style>
        :root {
            --bg-gradient: linear-gradient(120deg, #fccb90 0%, #d57eeb 100%);
            --glass-bg: rgba(255, 255, 255, 0.85);
            --glass-border: rgba(255, 255, 255, 0.6);
            --shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.15);
            
            /* Pastel Palette */
            --p-pink: #FFB7B2;
            --p-green: #B5EAD7;
            --p-purple: #E0BBE4;
            --p-yellow: #FFDAC1;
            --p-blue: #C7CEEA;
            
            --text-main: #665D5D;
            --radius: 24px;
        }

        body {
            font-family: 'Sarabun', sans-serif;
            background-image: linear-gradient(to top, #a18cd1 0%, #fbc2eb 100%);
            background-attachment: fixed;
            color: var(--text-main);
            margin: 0;
            padding: 20px;
            min-height: 100vh;
        }

        .container {
            max-width: 1000px;
            margin: 0 auto;
        }

        /* --- Glassmorphism Card --- */
        .glass-card {
            background: var(--glass-bg);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border-radius: var(--radius);
            border: 1px solid var(--glass-border);
            box-shadow: var(--shadow);
            padding: 30px;
            margin-bottom: 30px;
        }

        /* --- Header --- */
        .header-flex {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 20px;
        }

        h1 { margin: 0; font-weight: 800; color: #845EC2; font-size: 2rem; }
        h1 span { color: #FF9671; }

        .profile-select {
            display: flex;
            align-items: center;
            gap: 10px;
            background: white;
            padding: 10px 20px;
            border-radius: 50px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.05);
        }

        .avatar { font-size: 2rem; animation: float 3s ease-in-out infinite; }
        @keyframes float { 0%,100% {transform: translateY(0);} 50% {transform: translateY(-5px);} }

        /* --- Grid Layout for Content --- */
        .dashboard-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 25px;
        }
        @media (max-width: 768px) { .dashboard-grid { grid-template-columns: 1fr; } }

        /* --- Chart Section --- */
        .chart-container { position: relative; height: 300px; width: 100%; }

        /* --- Badge Collection --- */
        .badge-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(80px, 1fr));
            gap: 15px;
            text-align: center;
        }
        .badge-item {
            opacity: 0.3; /* Lock state */
            filter: grayscale(100%);
            transition: all 0.5s;
        }
        .badge-item.unlocked {
            opacity: 1;
            filter: grayscale(0%);
            transform: scale(1.1);
        }
        .badge-icon { font-size: 2.5rem; display: block; margin-bottom: 5px; }
        .badge-name { font-size: 0.75rem; font-weight: bold; }

        /* --- Action Area (Selection) --- */
        .domain-btn {
            background: white;
            border: 2px solid transparent;
            padding: 15px;
            border-radius: 15px;
            cursor: pointer;
            text-align: left;
            display: flex;
            align-items: center;
            gap: 15px;
            transition: 0.3s;
            margin-bottom: 10px;
            width: 100%;
            font-family: 'Sarabun';
            font-size: 1rem;
        }
        .domain-btn:hover { transform: translateX(5px); }
        .domain-btn.active { border-color: #FF9671; background: #FFF5F5; }
        
        .domain-icon-box {
            width: 40px; height: 40px;
            display: flex; align-items: center; justify-content: center;
            border-radius: 10px;
            font-size: 1.2rem;
        }

        /* --- Form --- */
        .input-box {
            width: 100%; padding: 12px;
            border: 2px solid #EEE; border-radius: 12px;
            margin-bottom: 15px; font-family: 'Sarabun';
        }
        
        .btn-magic {
            width: 100%; padding: 15px;
            background: linear-gradient(45deg, #FF9A9E 0%, #FECFEF 99%, #FECFEF 100%);
            border: none; border-radius: 50px;
            color: white; font-weight: bold; font-size: 1.2rem;
            cursor: pointer; transition: 0.3s;
            box-shadow: 0 5px 15px rgba(255, 154, 158, 0.4);
        }
        .btn-magic:hover { transform: scale(1.02); filter: brightness(1.1); }

    </style>
</head>
<body>

    <div class="container">
        
        <div class="glass-card header-flex">
            <div>
                <h1>Kinder A <span>Journey</span></h1>
                <p style="margin:0; opacity:0.7;">บันทึกการเติบโตของเด็กปฐมวัยแบบองค์รวม</p>
            </div>
            <div class="profile-select">
                <div class="avatar">👧</div>
                <div>
                    <strong id="childNameDisplay">น้องมีใจ</strong>
                    <div style="font-size:0.8rem; color:#888;">Level 1: นักสำรวจตัวจิ๋ว</div>
                </div>
            </div>
        </div>

        <div class="dashboard-grid">
            
            <div>
                <div class="glass-card">
                    <h3 style="margin-top:0;">📊 ผังพัฒนาการรอบด้าน (Holistic View)</h3>
                    <div class="chart-container">
                        <canvas id="holisticChart"></canvas>
                    </div>
                </div>

                <div class="glass-card">
                    <h3 style="margin-top:0;">🏆 ถ้วยรางวัลของหนู</h3>
                    <div class="badge-grid" id="badgeContainer">
                        </div>
                </div>
            </div>

            <div>
                <div class="glass-card">
                    <h3 style="margin-top:0;">✨ วันนี้ทำกิจกรรมอะไรดีนะ?</h3>
                    
                    <div id="domainSelector">
                        <button class="domain-btn" onclick="setDomain('body', '#FFB7B2')">
                            <div class="domain-icon-box" style="background:#FFE5E5;">🏃</div>
                            <div>ร่างกายแข็งแรง (Physical)</div>
                        </button>
                        <button class="domain-btn" onclick="setDomain('brain', '#B5EAD7')">
                            <div class="domain-icon-box" style="background:#E5FFF5;">🧠</div>
                            <div>คิดวิเคราะห์ (Cognitive)</div>
                        </button>
                        <button class="domain-btn" onclick="setDomain('social', '#FFDAC1')">
                            <div class="domain-icon-box" style="background:#FFF0E5;">🤗</div>
                            <div>อารมณ์และสังคม (Social)</div>
                        </button>
                        <button class="domain-btn" onclick="setDomain('lang', '#E2F0CB')">
                            <div class="domain-icon-box" style="background:#F5FFE5;">🗣️</div>
                            <div>ภาษาและการสื่อสาร (Language)</div>
                        </button>
                        <button class="domain-btn" onclick="setDomain('create', '#C7CEEA')">
                            <div class="domain-icon-box" style="background:#E5EFFF;">🎨</div>
                            <div>ความคิดสร้างสรรค์ (Creative)</div>
                        </button>
                    </div>

                    <div id="inputSection" style="display:none; margin-top:20px; border-top:2px dashed #EEE; padding-top:20px;">
                        <h4 id="selectedTitle" style="color:#845EC2;"></h4>
                        
                        <select id="actSelect" class="input-box"></select>
                        
                        <label>ความสนุก / ผลประเมิน:</label>
                        <select id="ratingSelect" class="input-box">
                            <option value="5">⭐⭐⭐⭐⭐ ยอดเยี่ยมมาก (Excellent)</option>
                            <option value="4">⭐⭐⭐⭐ ทำได้ดี (Very Good)</option>
                            <option value="3">⭐⭐⭐ ทำได้ตามวัย (Good)</option>
                        </select>
                        
                        <textarea id="noteInput" class="input-box" rows="2" placeholder="บันทึกคำพูด หรือสิ่งที่น่ารักๆ..."></textarea>
                        
                        <button class="btn-magic" onclick="saveData()">บันทึกความสำเร็จ! 🎉</button>
                    </div>

                </div>

                <div class="glass-card" style="max-height: 300px; overflow-y: auto;">
                    <h3 style="margin-top:0;">📜 บันทึกล่าสุด</h3>
                    <div id="historyLog"></div>
                </div>
            </div>

        </div>
    </div>

    <script>
        // --- Configuration ---
        const badgesDB = [
            { id: 'b_body', icon: '🥇', name: 'นักกีฬาตัวน้อย', req: { domain: 'body', count: 3 } },
            { id: 'b_brain', icon: '🎓', name: 'หนูน้อยช่างคิด', req: { domain: 'brain', count: 3 } },
            { id: 'b_social', icon: '💖', name: 'เพื่อนแสนดี', req: { domain: 'social', count: 3 } },
            { id: 'b_lang', icon: '🦜', name: 'นักเจรจา', req: { domain: 'lang', count: 3 } },
            { id: 'b_create', icon: '🎨', name: 'ศิลปินเอก', req: { domain: 'create', count: 3 } }
        ];

        const activitiesDB = {
            body: ["วิ่งเก็บของ", "เดินทรงตัวบนเส้น", "ปั้นดินน้ำมัน", "ร้อยเชือกรองเท้า", "เต้นประกอบเพลง"],
            brain: ["ต่อจิ๊กซอว์", "แยกสีและรูปทรง", "เล่นเกมจับคู่", "สังเกตเงา", "นับเลข 1-10"],
            social: ["เล่นบทบาทสมมติ", "แบ่งขนมให้เพื่อน", "ช่วยเก็บของ", "บอกอารมณ์ตนเอง", "รอคิว"],
            lang: ["เล่านิทาน", "ร้องเพลง", "ตอบคำถามง่ายๆ", "ดูรูปแล้วเล่าเรื่อง", "รู้จักพยัญชนะ"],
            create: ["วาดรูประบายสี", "ประดิษฐ์ของเล่น", "เล่านิทานประกอบท่าทาง", "ปั้นแป้งโดว์อิสระ"]
        };

        let records = JSON.parse(localStorage.getItem('kinderV3Records')) || [];
        let currentDomain = '';
        let myChart = null;

        // --- Init ---
        renderBadges();
        initChart();
        updateLog();

        // --- Functions ---
        function setDomain(domain, color) {
            currentDomain = domain;
            
            // UI Toggle
            document.querySelectorAll('.domain-btn').forEach(b => b.classList.remove('active'));
            event.currentTarget.classList.add('active');

            // Show Form
            document.getElementById('inputSection').style.display = 'block';
            document.getElementById('selectedTitle').textContent = `กำลังบันทึก: ${domain.toUpperCase()}`;
            
            // Populate Select
            const select = document.getElementById('actSelect');
            select.innerHTML = '';
            activitiesDB[domain].forEach(act => {
                const opt = document.createElement('option');
                opt.textContent = act;
                opt.value = act;
                select.appendChild(opt);
            });
        }

        function saveData() {
            if(!currentDomain) return;

            const act = document.getElementById('actSelect').value;
            const rating = parseInt(document.getElementById('ratingSelect').value);
            const note = document.getElementById('noteInput').value;

            records.unshift({
                domain: currentDomain,
                activity: act,
                rating: rating,
                note: note,
                timestamp: new Date()
            });

            localStorage.setItem('kinderV3Records', JSON.stringify(records));

            // Effects
            fireConfetti();
            document.getElementById('inputSection').style.display = 'none';
            document.querySelectorAll('.domain-btn').forEach(b => b.classList.remove('active'));
            document.getElementById('noteInput').value = '';

            // Updates
            updateChartData();
            checkBadgeUnlocks();
            updateLog();
        }

        // --- Chart Logic ---
        function initChart() {
            const ctx = document.getElementById('holisticChart').getContext('2d');
            
            myChart = new Chart(ctx, {
                type: 'radar',
                data: {
                    labels: ['ร่างกาย', 'สติปัญญา', 'สังคม', 'ภาษา', 'สร้างสรรค์'],
                    datasets: [{
                        label: 'ระดับทักษะ (Skill Level)',
                        data: [0, 0, 0, 0, 0],
                        backgroundColor: 'rgba(255, 183, 178, 0.5)', // Pastel Pink Translucent
                        borderColor: 'rgba(255, 183, 178, 1)',
                        borderWidth: 2,
                        pointBackgroundColor: '#845EC2'
                    }]
                },
                options: {
                    scales: {
                        r: {
                            angleLines: { color: '#EEE' },
                            grid: { color: '#EEE' },
                            pointLabels: {
                                font: { family: 'Sarabun', size: 14, weight: 'bold' },
                                color: '#666'
                            },
                            suggestedMin: 0,
                            suggestedMax: 10
                        }
                    },
                    plugins: {
                        legend: { display: false }
                    }
                }
            });
            updateChartData();
        }

        function updateChartData() {
            // Count records per domain
            const counts = { body:0, brain:0, social:0, lang:0, create:0 };
            records.forEach(r => { if(counts[r.domain] !== undefined) counts[r.domain]++; });
            
            // Map to chart data order
            const data = [counts.body, counts.brain, counts.social, counts.lang, counts.create];
            
            myChart.data.datasets[0].data = data;
            myChart.update();
        }

        // --- Gamification Logic ---
        function checkBadgeUnlocks() {
            const counts = { body:0, brain:0, social:0, lang:0, create:0 };
            records.forEach(r => { if(counts[r.domain] !== undefined) counts[r.domain]++; });

            badgesDB.forEach(badge => {
                if (counts[badge.req.domain] >= badge.req.count) {
                    const el = document.getElementById(badge.id);
                    if (!el.classList.contains('unlocked')) {
                        el.classList.add('unlocked');
                        // Optional alert for new badge
                    }
                }
            });
        }

        function renderBadges() {
            const container = document.getElementById('badgeContainer');
            container.innerHTML = '';
            badgesDB.forEach(badge => {
                const div = document.createElement('div');
                div.id = badge.id;
                div.className = 'badge-item';
                div.innerHTML = `
                    <span class="badge-icon">${badge.icon}</span>
                    <div class="badge-name">${badge.name}</div>
                `;
                container.appendChild(div);
            });
            checkBadgeUnlocks(); // Check immediately on load
        }

        // --- Confetti Effect ---
        function fireConfetti() {
            var count = 200;
            var defaults = { origin: { y: 0.7 } };

            function fire(particleRatio, opts) {
                confetti(Object.assign({}, defaults, opts, {
                    particleCount: Math.floor(count * particleRatio)
                }));
            }

            fire(0.25, { spread: 26, startVelocity: 55, colors: ['#FFB7B2', '#B5EAD7'] });
            fire(0.2, { spread: 60, colors: ['#E0BBE4', '#FFDAC1'] });
            fire(0.35, { spread: 100, decay: 0.91, scalar: 0.8 });
            fire(0.1, { spread: 120, startVelocity: 25, decay: 0.92, scalar: 1.2 });
            fire(0.1, { spread: 120, startVelocity: 45 });
        }

        function updateLog() {
            const log = document.getElementById('historyLog');
            log.innerHTML = '';
            records.slice(0, 5).forEach(r => { // Show last 5
                const div = document.createElement('div');
                div.style.padding = '10px';
                div.style.borderBottom = '1px solid #EEE';
                div.style.fontSize = '0.9rem';
                div.innerHTML = `<b>${r.activity}</b> <span style="float:right">${'⭐'.repeat(r.rating)}</span>`;
                log.appendChild(div);
            });
        }
    </script>
</body>
</html>
