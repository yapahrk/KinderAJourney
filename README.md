
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kinder A Journey - บันทึกการเดินทางของหนูน้อย</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Sarabun:wght@300;400;500;700&display=swap" rel="stylesheet">
    
    <style>
        :root {
            /* ชุดสีพาสเทล */
            --bg-color: #FDF6EC; /* ครีมอ่อน */
            --primary: #FFB7B2; /* ชมพูพาสเทล */
            --secondary: #B5EAD7; /* เขียวมิ้นท์ */
            --accent: #C7CEEA; /* ม่วงอ่อน */
            --text-dark: #555555;
            --text-light: #FFFFFF;
            --card-bg: #FFFFFF;
            --shadow: 0 8px 20px rgba(0,0,0,0.05);
            --radius: 20px;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: 'Sarabun', sans-serif;
            background-color: var(--bg-color);
            color: var(--text-dark);
            line-height: 1.6;
        }

        .container {
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
        }

        /* Header น่ารักๆ */
        header {
            text-align: center;
            padding: 40px 0;
            background: linear-gradient(135deg, #FF9AA2 0%, #FFB7B2 100%);
            border-radius: 0 0 30px 30px;
            margin-bottom: 30px;
            box-shadow: var(--shadow);
            color: white;
        }

        h1 {
            font-weight: 700;
            font-size: 2.5rem;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
        }
        
        h1 span {
            display: inline-block;
            animation: bounce 2s infinite;
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-5px); }
        }

        p.subtitle {
            font-size: 1.1rem;
            opacity: 0.9;
        }

        /* Card Design */
        .card {
            background: var(--card-bg);
            border-radius: var(--radius);
            padding: 30px;
            margin-bottom: 25px;
            box-shadow: var(--shadow);
            border: 2px solid white;
        }

        .card-header {
            display: flex;
            align-items: center;
            margin-bottom: 20px;
            color: #FF9AA2;
        }

        .card-header h2 {
            font-size: 1.5rem;
            margin-left: 10px;
        }

        /* Form Elements */
        .form-group {
            margin-bottom: 20px;
        }

        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #777;
        }

        input, select, textarea {
            width: 100%;
            padding: 12px 15px;
            border: 2px solid #EEE;
            border-radius: 15px;
            font-family: 'Sarabun', sans-serif;
            font-size: 1rem;
            transition: all 0.3s;
            background-color: #FAFAFA;
        }

        input:focus, select:focus, textarea:focus {
            border-color: var(--secondary);
            outline: none;
            background-color: white;
        }

        /* Custom Button */
        .btn-submit {
            background-color: var(--secondary);
            color: #558B78;
            border: none;
            padding: 12px 30px;
            border-radius: 50px;
            font-size: 1.1rem;
            font-weight: 700;
            cursor: pointer;
            width: 100%;
            transition: transform 0.2s, box-shadow 0.2s;
            font-family: 'Sarabun', sans-serif;
        }

        .btn-submit:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(181, 234, 215, 0.4);
        }

        /* History List */
        .history-item {
            background-color: #F9F9F9;
            border-left: 5px solid var(--accent);
            padding: 15px;
            margin-bottom: 15px;
            border-radius: 10px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .skill-tag {
            display: inline-block;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 600;
            margin-bottom: 5px;
        }

        .tag-logic { background-color: #E2F0CB; color: #6A8E2E; }
        .tag-lang { background-color: #FFDAC1; color: #A86A3D; }
        .tag-social { background-color: #FFB7B2; color: #8E3B3B; }
        .tag-create { background-color: #E0BBE4; color: #6A3B8E; }
        .tag-body { background-color: #957DAD; color: white; }

        .score-display {
            font-size: 1.2rem;
            color: #FFD700; /* Gold */
        }
        
        .empty-state {
            text-align: center;
            color: #AAA;
            padding: 20px;
        }

    </style>
</head>
<body>

    <header>
        <div class="container" style="padding:0;">
            <h1>🧸 Kinder A <span>Journey</span></h1>
            <p class="subtitle">ระบบบันทึกและส่งเสริมพัฒนาการเด็กปฐมวัยแบบองค์รวม</p>
        </div>
    </header>

    <div class="container">
        
        <div class="card">
            <div class="card-header">
                <span>📝</span>
                <h2>บันทึกกิจกรรมวันนี้</h2>
            </div>
            
            <form id="devForm">
                <div class="form-group">
                    <label>หัวข้อกิจกรรม / สิ่งที่เรียนรู้</label>
                    <input type="text" id="activity" placeholder="เช่น ต่อเลโก้รูปบ้าน, เล่านิทานเรื่องกระต่าย" required>
                </div>

                <div class="form-group">
                    <label>ด้านทักษะ (Skill Domain)</label>
                    <select id="skillDomain">
                        <option value="logic">🧮 สติปัญญาและการคิดวิเคราะห์ (Cognitive & Logic)</option>
                        <option value="lang">🗣️ ภาษาและการสื่อสาร (Language)</option>
                        <option value="social">🤗 อารมณ์และสังคม (Social & Emotional)</option>
                        <option value="create">🎨 จินตนาการและความคิดสร้างสรรค์ (Creativity)</option>
                        <option value="body">🏃 ร่างกายและการเคลื่อนไหว (Physical)</option>
                    </select>
                </div>

                <div class="form-group">
                    <label>ผลการประเมิน (Rating)</label>
                    <select id="rating">
                        <option value="5">⭐⭐⭐⭐⭐ ทำได้ดีเยี่ยม (Excellent)</option>
                        <option value="4">⭐⭐⭐⭐ ทำได้ดี (Very Good)</option>
                        <option value="3">⭐⭐⭐ ทำได้ตามเกณฑ์ (Good)</option>
                        <option value="2">⭐⭐ ควรเสริม (Needs Improvement)</option>
                        <option value="1">⭐ เริ่มต้นฝึกฝน (Beginner)</option>
                    </select>
                </div>

                <div class="form-group">
                    <label>บันทึกเพิ่มเติมจากผู้สอน/ผู้ปกครอง</label>
                    <textarea id="note" rows="3" placeholder="ข้อสังเกต หรือสิ่งที่เด็กพูดระหว่างทำกิจกรรม..."></textarea>
                </div>

                <button type="submit" class="btn-submit">บันทึกการเดินทาง ✨</button>
            </form>
        </div>

        <div class="card">
            <div class="card-header">
                <span>🌱</span>
                <h2>การเติบโตของหนู (History)</h2>
            </div>
            <div id="historyList">
                <div class="empty-state">ยังไม่มีข้อมูลการบันทึก... เริ่มต้นบันทึกกันเลย!</div>
            </div>
        </div>

    </div>

    <script>
        // JavaScript สำหรับจัดการข้อมูล
        const form = document.getElementById('devForm');
        const historyList = document.getElementById('historyList');

        // โหลดข้อมูลเก่าถ้ามี (ใช้ LocalStorage จำลอง Database)
        let records = JSON.parse(localStorage.getItem('kinderRecords')) || [];
        renderHistory();

        form.addEventListener('submit', function(e) {
            e.preventDefault();

            // รับค่าจากฟอร์ม
            const activity = document.getElementById('activity').value;
            const skill = document.getElementById('skillDomain').value;
            const rating = document.getElementById('rating').value;
            const note = document.getElementById('note').value;
            
            const newRecord = {
                id: Date.now(),
                date: new Date().toLocaleDateString('th-TH', { year: 'numeric', month: 'long', day: 'numeric', hour: '2-digit', minute:'2-digit'}),
                activity,
                skill,
                rating,
                note
            };

            // บันทึกลง Array
            records.unshift(newRecord); // ใส่ข้อมูลใหม่ไว้บนสุด
            localStorage.setItem('kinderRecords', JSON.stringify(records));

            // รีเซ็ตฟอร์มและแสดงผลใหม่
            form.reset();
            renderHistory();
            alert('บันทึกข้อมูลสำเร็จแล้วค่ะ! 🎈');
        });

        function renderHistory() {
            historyList.innerHTML = '';

            if (records.length === 0) {
                historyList.innerHTML = '<div class="empty-state">ยังไม่มีข้อมูลการบันทึก... เริ่มต้นบันทึกกันเลย!</div>';
                return;
            }

            records.forEach(record => {
                const item = document.createElement('div');
                item.className = 'history-item';

                // กำหนดชื่อ Skill และ Class สี
                let skillName = '';
                let skillClass = '';
                switch(record.skill) {
                    case 'logic': skillName = 'สติปัญญา & ตรรกะ'; skillClass = 'tag-logic'; break;
                    case 'lang': skillName = 'ภาษา & สื่อสาร'; skillClass = 'tag-lang'; break;
                    case 'social': skillName = 'อารมณ์ & สังคม'; skillClass = 'tag-social'; break;
                    case 'create': skillName = 'ความคิดสร้างสรรค์'; skillClass = 'tag-create'; break;
                    case 'body': skillName = 'ร่างกาย'; skillClass = 'tag-body'; break;
                }

                // แปลงคะแนนเป็นดาว
                let stars = '⭐'.repeat(record.rating);

                item.innerHTML = `
                    <div>
                        <span class="skill-tag ${skillClass}">${skillName}</span>
                        <h3 style="margin: 5px 0; color: #555;">${record.activity}</h3>
                        <p style="font-size: 0.9rem; color: #888;">📅 ${record.date}</p>
                        ${record.note ? `<p style="font-size: 0.9rem; margin-top:5px; color:#666; font-style:italic;">"${record.note}"</p>` : ''}
                    </div>
                    <div class="score-display">
                        ${stars}
                    </div>
                `;

                historyList.appendChild(item);
            });
        }
    </script>
</body>
</html># KinderAJourney
