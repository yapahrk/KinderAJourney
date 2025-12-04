
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Kinder A Journey</title>
    <link href="https://fonts.googleapis.com/css2?family=Mali:wght@300;500;700&display=swap" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">

    <style>
        /* --- Global Reset --- */
        * {
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }

        :root {
            --primary-text: #555;
            --pastel-blue: #AEC6CF;
            --pastel-blue-light: #E8F4F8;
            --pastel-yellow: #FDFD96;
            --pastel-yellow-light: #FFFAE6;
            --pastel-pink: #FFB7B2;
            --pastel-pink-light: #FFF0F0;
            --pastel-green: #B0E57C;
            --pastel-green-light: #F0FFF0;
            --pastel-purple: #C3B1E1;
            --pastel-purple-light: #F3E5F5;
            --white: #ffffff;
            --shadow: 0 4px 15px rgba(0,0,0,0.08);
            --radius: 20px;
        }

        body {
            font-family: 'Mali', cursive;
            background-color: #F7F9FC;
            color: var(--primary-text);
            margin: 0;
            padding: 0;
            padding-bottom: 90px; /* Space for bottom nav */
            width: 100%;
            overflow-x: hidden;
        }

        /* --- Header (ส่วนหัวที่มีหมี - มีแค่อันเดียว) --- */
        header {
            background-color: var(--white);
            padding: 15px;
            text-align: center;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
            position: sticky;
            top: 0;
            left: 0;
            width: 100%;
            z-index: 1000; /* ให้ลอยอยู่ชั้นบนสุด */
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        /* CSS Drawing: Bear Logo */
        .logo-bear {
            width: 40px;
            height: 40px;
            background: #D2691E;
            border-radius: 50%;
            position: relative;
            flex-shrink: 0;
        }
        .logo-bear::before, .logo-bear::after {
            content: '';
            position: absolute;
            top: -5px;
            width: 15px;
            height: 15px;
            background: #D2691E;
            border-radius: 50%;
        }
        .logo-bear::before { left: 0; }
        .logo-bear::after { right: 0; }
        .logo-face {
            width: 30px;
            height: 25px;
            background: #FFDCB1;
            border-radius: 50%;
            position: absolute;
            bottom: 2px;
            left: 5px;
        }
        .logo-eye {
            width: 4px;
            height: 4px;
            background: #333;
            border-radius: 50%;
            position: absolute;
            top: 8px;
        }
        .logo-eye.left { left: 8px; }
        .logo-eye.right { right: 8px; }
        .logo-nose {
            width: 6px;
            height: 4px;
            background: #333;
            border-radius: 50%;
            position: absolute;
            bottom: 8px;
            left: 12px;
        }

        h1 {
            margin: 0;
            font-size: 1.3rem;
            color: #4A90E2;
            white-space: nowrap;
        }

        /* --- Container --- */
        .container {
            width: 100%;
            max-width: 600px;
            margin: 0 auto;
            padding: 20px;
        }

        /* --- Navigation --- */
        .bottom-nav {
            position: fixed;
            bottom: 0;
            left: 0;
            width: 100%;
            background: var(--white);
            display: flex;
            justify-content: space-around;
            padding: 10px 0;
            box-shadow: 0 -2px 10px rgba(0,0,0,0.05);
            z-index: 1000;
            padding-bottom: env(safe-area-inset-bottom);
        }

        .nav-item {
            text-align: center;
            font-size: 0.75rem;
            color: #aaa;
            cursor: pointer;
            transition: 0.3s;
            flex: 1;
        }

        .nav-item i {
            font-size: 1.3rem;
            margin-bottom: 4px;
            display: block;
        }

        .nav-item.active {
            color: #4A90E2;
            font-weight: bold;
        }

        /* --- Sections --- */
        .page { display: none; animation: fadeIn 0.4s ease-out; }
        .page.active { display: block; }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }

        /* --- Cards --- */
        .card {
            background: var(--white);
            border-radius: var(--radius);
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: var(--shadow);
            position: relative;
            overflow: hidden;
            width: 100%;
        }

        .card-header-text {
            font-size: 1.1rem;
            font-weight: bold;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        /* Themes */
        .theme-blue .card-header-text { color: #6CA0DC; }
        .theme-pink .card-header-text { color: #FF6961; }
        .theme-green .card-header-text { color: #77DD77; }
        .theme-yellow .card-header-text { color: #FDFD96; text-shadow: 0 0 1px #999; }
        .theme-purple .card-header-text { color: #B19CD9; }

        .theme-blue .card { border-left: 5px solid var(--pastel-blue); }
        .theme-pink .card { border-left: 5px solid var(--pastel-pink); }
        .theme-green .card { border-left: 5px solid var(--pastel-green); }
        .theme-yellow .card { border-left: 5px solid var(--pastel-yellow); }
        .theme-purple .card { border-left: 5px solid var(--pastel-purple); }

        /* Inputs & Buttons */
        input, select, textarea {
            width: 100%; padding: 12px; border: 2px solid #eee; border-radius: 12px;
            font-family: 'Mali', cursive; margin-bottom: 12px; font-size: 1rem; background: #fff;
        }
        input:focus, textarea:focus { outline: none; border-color: var(--pastel-blue); }

        .btn {
            background-color: var(--pastel-blue); color: white; border: none; padding: 12px 20px;
            border-radius: 20px; font-family: 'Mali', cursive; cursor: pointer; width: 100%;
            font-size: 1rem; transition: 0.2s; font-weight: bold;
        }
        .btn:active { transform: scale(0.98); }

        /* Checklist */
        .checklist-item {
            background: #f9f9f9; padding: 12px; border-radius: 12px; margin-bottom: 10px; border: 1px solid #eee;
        }
        .checklist-header { display: flex; align-items: flex-start; justify-content: space-between; }
        .checklist-label { display: flex; align-items: flex-start; gap: 10px; cursor: pointer; flex-grow: 1; padding-right: 10px; }
        .checklist-label span { line-height: 1.4; word-break: break-word; }
        .checklist-details { margin-top: 10px; padding-top: 10px; border-top: 1px dashed #ddd; display: none; }
        .checklist-details.show { display: block; }
        input[type="checkbox"] { width: 22px; height: 22px; margin: 0; margin-top: 2px; accent-color: var(--pastel-green); flex-shrink: 0; }

        /* Tabs */
        .age-tabs {
            display: flex; gap: 8px; margin-bottom: 15px; overflow-x: auto; padding-bottom: 5px;
            -webkit-overflow-scrolling: touch; padding-left: 2px;
        }
        .age-tab {
            background: #eee; padding: 6px 16px; border-radius: 20px; white-space: nowrap;
            cursor: pointer; font-size: 0.9rem; flex-shrink: 0;
        }
        .age-tab.active { background: var(--pastel-blue); color: white; box-shadow: 0 2px 5px rgba(174, 198, 207, 0.4); }

        /* Graph & Info */
        .chart-container { position: relative; height: 250px; width: 100%; }
        .info-card { background: #fff; border-radius: 12px; padding: 15px; margin-bottom: 12px; border: 1px solid #eee; }
        .info-card h4 { margin: 0 0 5px 0; color: #555; font-size: 1rem; }
        .info-card p { margin: 0; font-size: 0.9rem; color: #777; line-height: 1.5; }
    </style>
</head>
<body>

    <header>
        <div class="logo-bear">
            <div class="logo-face">
                <div class="logo-eye left"></div>
                <div class="logo-eye right"></div>
                <div class="logo-nose"></div>
            </div>
        </div>
        <h1>Kinder A Journey</h1>
    </header>

    <div class="container">
        <div id="page-home" class="page active theme-blue">
            <div class="card" style="background: var(--pastel-blue-light);">
                <div class="card-header-text"><i class="fas fa-baby"></i> ข้อมูลลูกน้อย</div>
                <label>ชื่อเล่น</label>
                <input type="text" id="child-name" placeholder="เช่น น้องมีดี">
                <label>วันเกิด</label>
                <input type="date" id="child-dob">
                <button class="btn" onclick="saveProfile()">บันทึกข้อมูล</button>
                <p id="age-display" style="text-align: center; margin-top: 15px; font-weight: bold; color: #4A90E2;"></p>
            </div>
            <div class="card">
                <div class="card-header-text"><i class="fas fa-chart-pie"></i> ภาพรวมพัฒนาการ</div>
                <div class="chart-container">
                    <canvas id="progressChart"></canvas>
                </div>
            </div>
        </div>

        <div id="page-development" class="page theme-pink">
            <div class="card" style="background: var(--pastel-pink-light);">
                <div class="card-header-text"><i class="fas fa-star"></i> ติดตามพัฒนาการ</div>
                <div class="age-tabs" id="dev-tabs"></div>
                <div id="dev-list"></div>
            </div>
        </div>

        <div id="page-vaccine" class="page theme-green">
            <div class="card" style="background: var(--pastel-green-light);">
                <div class="card-header-text"><i class="fas fa-syringe"></i> บันทึกวัคซีน</div>
                <div class="age-tabs" id="vac-tabs"></div>
                <div id="vac-list"></div>
            </div>
        </div>

        <div id="page-nutrition" class="page theme-yellow">
            <div class="card" style="background: var(--pastel-yellow-light);">
                <div class="card-header-text"><i class="fas fa-utensils"></i> โภชนาการตามวัย</div>
                <div class="age-tabs" id="nutri-tabs"></div>
                <div id="nutri-content"></div>
            </div>
        </div>

        <div id="page-activity" class="page theme-purple">
            <div class="card" style="background: var(--pastel-purple-light);">
                <div class="card-header-text"><i class="fas fa-shapes"></i> กิจกรรมเสริมทักษะ</div>
                <div class="age-tabs" id="act-tabs"></div>
                <div id="act-list"></div>
            </div>
        </div>
    </div>

    <nav class="bottom-nav">
        <div class="nav-item active" onclick="switchPage('home', this)">
            <i class="fas fa-home"></i> หน้าแรก
        </div>
        <div class="nav-item" onclick="switchPage('development', this)">
            <i class="fas fa-baby-carriage"></i> พัฒนาการ
        </div>
        <div class="nav-item" onclick="switchPage('vaccine', this)">
            <i class="fas fa-shield-virus"></i> วัคซีน
        </div>
        <div class="nav-item" onclick="switchPage('nutrition', this)">
            <i class="fas fa-apple-alt"></i> อาหาร
        </div>
        <div class="nav-item" onclick="switchPage('activity', this)">
            <i class="fas fa-puzzle-piece"></i> กิจกรรม
        </div>
    </nav>

    <script>
        // Data & Logic
        const ageGroups = ["0-6 เดือน", "6-12 เดือน", "1-2 ปี", "2-3 ปี"];
        const dataContent = {
            development: {
                "0-6 เดือน": ["ชันคอได้แข็งแรง", "ยิ้มทักทาย ส่งเสียงอูอา", "พลิกคว่ำพลิกหงาย", "คว้าของที่อยู่ใกล้"],
                "6-12 เดือน": ["นั่งได้เองมั่นคง", "คลานได้คล่อง", "เกาะยืน", "ใช้นิ้วหยิบของเล็กๆ", "เริ่มพูดคำที่มีความหมาย"],
                "1-2 ปี": ["เดินได้เอง", "ขีดเขียนเส้นยุ่งๆ", "พูดเป็นคำๆ ต่อกัน 2 คำ", "ทำตามคำสั่งง่ายๆ ได้"],
                "2-3 ปี": ["วิ่งได้คล่อง", "กระโดดสองขา", "พูดเป็นประโยค", "บอกชื่อตัวเองได้", "ขี่จักรยานสามล้อ"]
            },
            vaccines: {
                "0-6 เดือน": ["BCG (วัณโรค)", "ตับอักเสบบี (ครั้งที่ 1,2)", "คอตีบ-บาดทะยัก-ไอกรน (ครั้งที่ 1,2)", "โปลิโอ (ครั้งที่ 1,2)", "โรตา (หยอด)"],
                "6-12 เดือน": ["ตับอักเสบบี (ครั้งที่ 3)", "คอตีบ-บาดทะยัก-ไอกรน (ครั้งที่ 3)", "โปลิโอ (ครั้งที่ 3)", "ไข้หวัดใหญ่", "ไข้สมองอักเสบ JE"],
                "1-2 ปี": ["MMR (หัด-คางทูม-หัดเยอรมัน)", "ไข้สมองอักเสบ JE (เข็ม 2)", "DTP กระตุ้น (ครั้งที่ 4)"],
                "2-3 ปี": ["ไข้หวัดใหญ่ (ประจำปี)"]
            },
            nutrition: {
                "0-6 เดือน": [{title: "นมแม่", desc: "ควรทานนมแม่ล้วน ไม่ต้องดื่มน้ำ"}, {title: "การเริ่มอาหาร", desc: "เมื่อครบ 6 เดือน เริ่มอาหารบดละเอียด 1 มื้อ"}],
                "6-12 เดือน": [{title: "อาหารบด", desc: "เพิ่มความหยาบขึ้น บดหยาบ -> หั่นชิ้นเล็ก"}, {title: "มื้ออาหาร", desc: "2-3 มื้อ พร้อมผลไม้มื้อว่าง"}, {title: "สารอาหาร", desc: "เน้นตับ ไข่แดง ผักใบเขียว (ธาตุเหล็ก)"}],
                "1-2 ปี": [{title: "อาหารหลัก", desc: "อาหาร 3 มื้อ แบบผู้ใหญ่แต่รสอ่อน"}, {title: "นม", desc: "นมรสจืด วันละ 2-3 กล่อง/แก้ว"}, {title: "หลีกเลี่ยง", desc: "ขนมกรุบกรอบ น้ำหวาน อาหารรสจัด"}],
                "2-3 ปี": [{title: "ความหลากหลาย", desc: "ครบ 5 หมู่ เน้นโปรตีนและแคลเซียม"}, {title: "ฝึกวินัย", desc: "กินอาหารให้ตรงเวลา ไม่กินไปเล่นไป"}]
            },
            activities: {
                "0-6 เดือน": [{title: "โมบาย", desc: "แขวนโมบายสีสดใส กระตุ้นสายตา"}, {title: "คุยกับลูก", desc: "พูดคุย ร้องเพลง สบตา กระตุ้นการฟัง"}],
                "6-12 เดือน": [{title: "เล่นจ๊ะเอ๋", desc: "ฝึกเรื่องความคงอยู่ของวัตถุ"}, {title: "บล็อกหยอด", desc: "ฝึกกล้ามเนื้อมือและสายตา"}, {title: "นิทานภาพ", desc: "อ่านนิทานภาพใหญ่ๆ ให้ฟัง"}],
                "1-2 ปี": [{title: "ตัวต่อไม้", desc: "ต่อบล็อกไม้ 2-3 ชั้น"}, {title: "บทบาทสมมติ", desc: "เล่นทำกับข้าว เลี้ยงน้องตุ๊กตา"}, {title: "วิ่งไล่จับ", desc: "พัฒนากล้ามเนื้อมัดใหญ่"}],
                "2-3 ปี": [{title: "ร้อยลูกปัด", desc: "ลูกปัดขนาดใหญ่ ฝึกสมาธิ"}, {title: "ปั้นแป้งโดว์", desc: "พัฒนากล้ามเนื้อมือและจินตนาการ"}, {title: "ขี่รถขาไถ", desc: "ฝึกการทรงตัว"}]
            }
        };

        let appData = { name: "", dob: "", checks: {}, notes: {} };

        window.onload = function() { loadData(); setupTabs(); renderContent(); updateAge(); updateChart(); };

        function switchPage(pageId, navElement) {
            document.querySelectorAll('.page').forEach(el => el.classList.remove('active'));
            document.getElementById('page-' + pageId).classList.add('active');
            document.querySelectorAll('.nav-item').forEach(el => el.classList.remove('active'));
            navElement.classList.add('active');
            window.scrollTo(0, 0);
            if(pageId === 'home') updateChart();
        }

        function saveProfile() {
            appData.name = document.getElementById('child-name').value;
            appData.dob = document.getElementById('child-dob').value;
            saveData();
            updateAge();
            alert("บันทึกข้อมูลเรียบร้อยค่ะ");
        }
        function saveData() { localStorage.setItem('kinderJourneyData', JSON.stringify(appData)); updateChart(); }
        function loadData() {
            const stored = localStorage.getItem('kinderJourneyData');
            if (stored) {
                appData = JSON.parse(stored);
                document.getElementById('child-name').value = appData.name || "";
                document.getElementById('child-dob').value = appData.dob || "";
            }
        }
        function updateAge() {
            if (!appData.dob) return;
            const dob = new Date(appData.dob);
            const now = new Date();
            const diffTime = Math.abs(now - dob);
            const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24)); 
            const years = Math.floor(diffDays / 365);
            const months = Math.floor((diffDays % 365) / 30);
            let text = ""; if (years > 0) text += `${years} ปี `; text += `${months} เดือน`;
            document.getElementById('age-display').innerText = `อายุ: ${text}`;
        }
        function setupTabs() {
            const types = ['dev', 'vac', 'nutri', 'act'];
            types.forEach(type => {
                const container = document.getElementById(`${type}-tabs`);
                if (!container) return;
                ageGroups.forEach((age, index) => {
                    const tab = document.createElement('div');
                    tab.className = `age-tab ${index === 0 ? 'active' : ''}`;
                    tab.innerText = age;
                    tab.onclick = () => {
                        container.querySelectorAll('.age-tab').forEach(t => t.classList.remove('active'));
                        tab.classList.add('active');
                        if (type === 'dev') renderChecklist('development', age, 'dev-list');
                        if (type === 'vac') renderChecklist('vaccines', age, 'vac-list');
                        if (type === 'nutri') renderCards('nutrition', age, 'nutri-content');
                        if (type === 'act') renderChecklist('activities', age, 'act-list', true);
                    };
                    container.appendChild(tab);
                });
            });
        }
        function renderContent() {
            renderChecklist('development', ageGroups[0], 'dev-list');
            renderChecklist('vaccines', ageGroups[0], 'vac-list');
            renderCards('nutrition', ageGroups[0], 'nutri-content');
            renderChecklist('activities', ageGroups[0], 'act-list', true);
        }
        function renderChecklist(type, ageGroup, containerId) {
            const container = document.getElementById(containerId);
            container.innerHTML = "";
            const items = dataContent[type][ageGroup] || [];
            items.forEach((item, index) => {
                const itemText = typeof item === 'string' ? item : item.title + (item.desc ? ` (${item.desc})` : '');
                const key = `${type}_${ageGroup}_${index}`;
                const isChecked = appData.checks[key] || false;
                const noteData = appData.notes[key] || {date: '', text: ''};
                const div = document.createElement('div');
                div.className = 'checklist-item';
                div.innerHTML = `
                    <div class="checklist-header">
                        <label class="checklist-label">
                            <input type="checkbox" onchange="toggleCheck('${key}', this)" ${isChecked ? 'checked' : ''}>
                            <span>${itemText}</span>
                        </label>
                        <i class="fas fa-chevron-down" style="color:#ccc; cursor:pointer; padding: 5px;" onclick="toggleDetails(this)"></i>
                    </div>
                    <div class="checklist-details">
                        <label style="font-size:0.8rem;">วันที่ทำสำเร็จ/ได้รับ:</label>
                        <input type="date" value="${noteData.date}" onchange="updateNote('${key}', 'date', this.value)">
                        <label style="font-size:0.8rem;">หมายเหตุ:</label>
                        <textarea rows="2" placeholder="บันทึกเพิ่มเติม..." onchange="updateNote('${key}', 'text', this.value)">${noteData.text}</textarea>
                    </div>`;
                container.appendChild(div);
            });
        }
        function renderCards(type, ageGroup, containerId) {
            const container = document.getElementById(containerId);
            container.innerHTML = "";
            const items = dataContent[type][ageGroup] || [];
            items.forEach(item => {
                const div = document.createElement('div');
                div.className = 'info-card';
                div.innerHTML = `<h4>${item.title}</h4><p>${item.desc}</p>`;
                container.appendChild(div);
            });
        }
        function toggleCheck(key, checkbox) { appData.checks[key] = checkbox.checked; saveData(); }
        function updateNote(key, field, value) {
            if (!appData.notes[key]) appData.notes[key] = {date: '', text: ''};
            appData.notes[key][field] = value; saveData();
        }
        function toggleDetails(icon) {
            const details = icon.parentElement.nextElementSibling;
            const isHidden = getComputedStyle(details).display === 'none';
            if (isHidden) { details.style.display = 'block'; icon.className = 'fas fa-chevron-up'; }
            else { details.style.display = 'none'; icon.className = 'fas fa-chevron-down'; }
        }
        let myChart = null;
        function updateChart() {
            const ctx = document.getElementById('progressChart').getContext('2d');
            const calculatePercent = (type) => {
                let total = 0, checked = 0;
                for (const age in dataContent[type]) {
                    dataContent[type][age].forEach((item, index) => {
                        total++; if (appData.checks[`${type}_${age}_${index}`]) checked++;
                    });
                }
                return total === 0 ? 0 : Math.round((checked / total) * 100);
            };
            const devProgress = calculatePercent('development');
            const vacProgress = calculatePercent('vaccines');
            const actProgress = calculatePercent('activities');
            if (myChart) myChart.destroy();
            myChart = new Chart(ctx, {
                type: 'radar',
                data: {
                    labels: ['พัฒนาการ', 'วัคซีน', 'กิจกรรม'],
                    datasets: [{
                        label: 'ความสำเร็จ (%)',
                        data: [devProgress, vacProgress, actProgress],
                        backgroundColor: 'rgba(174, 198, 207, 0.5)', borderColor: '#AEC6CF', borderWidth: 2, pointBackgroundColor: ['#FFB7B2', '#B0E57C', '#C3B1E1']
                    }]
                },
                options: {
                    scales: { r: { angleLines: { display: true }, suggestedMin: 0, suggestedMax: 100, ticks: { display: false } } },
                    plugins: { legend: { display: false } }, maintainAspectRatio: false
                }
            });
        }
    </script>
</body>
</html>
