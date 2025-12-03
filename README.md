
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kinder A Journey V.2 - ภารกิจพิชิตพัฒนาการ</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Sarabun:wght@300;400;500;700&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --bg-color: #FFF5F7;
            --card-bg: #FFFFFF;
            
            /* Theme Colors ตามหมวดหมู่ */
            --c-body: #FFB7B2;   /* Physical - ชมพู */
            --c-brain: #B5EAD7;  /* Cognitive - เขียวมิ้นท์ */
            --c-social: #FFDAC1; /* Social - ส้มพีช */
            --c-create: #C7CEEA; /* Creative - ม่วง */
            --c-lang: #E2F0CB;   /* Language - เหลืองมะนาว */

            --text-main: #555;
            --shadow: 0 10px 25px rgba(0,0,0,0.08);
            --radius: 25px;
        }

        body {
            font-family: 'Sarabun', sans-serif;
            background-color: var(--bg-color);
            color: var(--text-main);
            margin: 0;
            padding-bottom: 50px;
        }

        .container {
            max-width: 900px;
            margin: 0 auto;
            padding: 20px;
        }

        /* Header */
        header {
            text-align: center;
            padding: 30px 20px;
            background: white;
            border-radius: 0 0 var(--radius) var(--radius);
            box-shadow: var(--shadow);
            margin-bottom: 30px;
            position: relative;
            overflow: hidden;
        }

        header::before {
            content: '';
            position: absolute;
            top: 0; left: 0; width: 100%; height: 10px;
            background: linear-gradient(90deg, var(--c-body), var(--c-brain), var(--c-social), var(--c-create), var(--c-lang));
        }

        h1 {
            color: #666;
            margin: 0;
            font-size: 2rem;
        }

        h1 span { color: #FF9AA2; }

        /* Step 1: เลือกหมวดหมู่ (Grid) */
        .domain-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 15px;
            margin-bottom: 30px;
        }

        .domain-card {
            background: white;
            border-radius: 20px;
            padding: 20px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
            border: 3px solid transparent;
            box-shadow: 0 4px 10px rgba(0,0,0,0.05);
        }

        .domain-card:hover { transform: translateY(-5px); }
        .domain-card.active { border-color: #FF9AA2; transform: scale(1.05); box-shadow: var(--shadow); }

        .domain-icon { font-size: 3rem; display: block; margin-bottom: 10px; }
        .domain-title { font-weight: bold; display: block; }

        /* สีเฉพาะการ์ด */
        .d-body:hover, .d-body.active { background-color: #FFF0F0; }
        .d-brain:hover, .d-brain.active { background-color: #F0FFF9; }
        .d-social:hover, .d-social.active { background-color: #FFF8F0; }
        .d-create:hover, .d-create.active { background-color: #F4F6FF; }
        .d-lang:hover, .d-lang.active { background-color: #FAFFF0; }

        /* Step 2: เลือกกิจกรรม (ซ่อนอยู่ก่อน) */
        .activity-section {
            display: none; /* ซ่อนไว้ก่อน */
            background: white;
            padding: 30px;
            border-radius: var(--radius);
            box-shadow: var(--shadow);
            animation: slideDown 0.5s ease;
            margin-bottom: 30px;
        }

        @keyframes slideDown {
            from { opacity: 0; transform: translateY(-20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        select, textarea {
            width: 100%;
            padding: 15px;
            border: 2px solid #EEE;
            border-radius: 15px;
            font-family: 'Sarabun';
            font-size: 1rem;
            margin-bottom: 20px;
            background: #FAFAFA;
        }

        .rating-group {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-bottom: 20px;
        }

        .rating-btn {
            background: none;
            border: 2px solid #EEE;
            font-size: 1.5rem;
            padding: 10px;
            border-radius: 50%;
            cursor: pointer;
            transition: 0.2s;
        }
        
        .rating-btn:hover, .rating-btn.selected {
            background: #FFD700;
            border-color: #FFD700;
            color: white;
            transform: scale(1.1);
        }

        .btn-save {
            width: 100%;
            padding: 15px;
            background: linear-gradient(45deg, #FF9AA2, #FFB7B2);
            color: white;
            border: none;
            border-radius: 50px;
            font-size: 1.2rem;
            font-weight: bold;
            cursor: pointer;
            box-shadow: 0 5px 15px rgba(255, 154, 162, 0.4);
        }
        
        .btn-save:hover { filter: brightness(1.05); }

        /* Stats Bar */
        .
