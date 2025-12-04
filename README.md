
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kinder A Journey - ผู้ช่วยคุณพ่อคุณแม่</title>
    <link href="https://fonts.googleapis.com/css2?family=Mali:wght@300;500;700&display=swap" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">

    <style>
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
            --shadow: 0 4px 15px rgba(0,0,0,0.1);
            --radius: 20px;
        }

        body {
            font-family: 'Mali', cursive;
            background-color: #F7F9FC;
            color: var(--primary-text);
            margin: 0;
            padding: 0;
            padding-bottom: 80px; /* For bottom nav */
        }

        /* --- Header & Logo --- */
        header {
            background-color: var(--white);
            padding: 15px 20px;
            text-align: center;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
            position: sticky;
            top: 0;
            z-index: 100;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .logo-bear {
            width: 40px;
            height: 40px;
            background: #D2691E;
            border-radius: 50%;
            position: relative;
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
            font-size: 1.5rem;
            color: #4A90E2;
        }

        /* --- Container --- */
        .container {
            max-width: 600px;
            margin: 20px auto;
            padding: 0 20px;
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
        }

        .nav-item {
            text-align: center;
            font-size: 0.8rem;
            color: #aaa;
            cursor: pointer;
            transition: 0.3s;
        }

        .nav-item i {
            font-size: 1.4rem;
            margin-bottom: 2px;
            display: block;
        }

        .nav-item.active {
            color: #4A90E2;
            font-weight: bold;
        }

        /* --- Sections --- */
        .page {
            display: none;
            animation: fadeIn 0.5s;
        }
        .page.active {
            display: block;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* --- Cards & UI Elements --- */
        .card {
            background: var(--white);
            border-radius: var(--radius);
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: var(--shadow);
            position: relative;
            overflow: hidden;
        }

        .card-header {
            font-size: 1.2rem;
            font-weight: bold;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        /* Colors for specific pages */
        .theme-blue .card-header { color: #6CA0DC; }
        .theme-pink .card-header { color: #FF6961; }
        .theme-green .card-header { color: #77DD77; }
        .theme-yellow .card-header { color: #FDFD96; text-shadow: 0 0 1px #999; }
        .theme-purple .card-header { color: #B19CD9; }

        .theme-blue .card { border-left: 5px solid var(--pastel-blue); }
        .theme-pink .card { border-left: 5px solid var(--pastel-pink); }
        .theme-green .card { border-left: 5px solid var(--pastel-green); }
        .theme-yellow .card { border-left: 5px solid var(--pastel-yellow); }
        .theme-purple .card { border-left: 5px solid var(--pastel-purple); }

        /* Form Inputs */
        input, select, textarea {
            width: 100%;
            padding: 10px;
            border: 2px solid #eee;
            border-radius: 10px;
            font-family: 'Mali', cursive;
            margin-bottom: 10px;
            box-sizing: border-box;
        }
        input:focus, textarea:focus {
            outline: none;
            border-color: var(--pastel-blue);
        }

        .btn {
            background-color: var(--pastel-blue);
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 20px;
            font-family: 'Mali', cursive;
            cursor: pointer;
            width: 100%;
            font-size: 1rem;
            transition: 0.2s;
        }
        .btn:hover { opacity: 0.9; transform: scale(1.02); }

        /* Checklist Styles */
        .checklist-item {
            display: flex;
            flex-direction: column;
            background: #f9f9f9;
            padding: 10px;
            border-radius: 10px;
            margin-bottom: 8px;
            border: 1px solid #eee;
        }
        .checklist-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        .checklist-label {
            display: flex;
            align-items: center;
            gap: 10px;
            cursor: pointer;
            flex-grow: 1;
        }
        .checklist-details {
            margin-top: 10px;
            padding-top: 10px;
            border-top: 1px dashed #ddd;
            display: none; /* Hidden by default */
        }
        .checklist-details.show {
            display: block;
        }
        
        input[type="checkbox"] {
            width: 20px;
            height: 20px;
            margin: 0;
            accent-color: var(--pastel-green);
        }

        /* Age Selector Tabs */
        .age-tabs {
            display: flex;
            gap: 5px;
            margin-bottom: 15px;
            overflow-x: auto;
            padding-bottom: 5px;
        }
        .age-tab {
            background: #eee;
            padding: 5px 15px;
            border-radius: 15px;
            white-space: nowrap;
            cursor: pointer;
            font-size: 0.9rem;
        }
        .age-tab.active {
            background: var(--pastel-blue);
            color: white;
        }

        /* Graph Container */
        .chart-container {
            position: relative;
            height: 300px;
            width: 100%;
        }

        /* Nutrition & Activity Cards */
        .info-card {
            background: #fff;
            border-radius: 10px;
            padding: 15px;
            margin-bottom: 10px;
            border: 1px solid #eee;
        }
        .info-card h4 { margin: 0 0 5px 0; color: #555; }
        .info-card p { margin: 0; font-size: 0.9rem; color: #777; }

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
                <div class="card-header"><i class="fas fa-baby"></i> ข้อมูลลูกน้อย</div>
                <label>ชื่อเล่น</label>
                <input type="text" id="child-name" placeholder="เช่น น้องมีดี">
                <label>วันเกิด</label>
                <input type="date" id="child-dob">
                <button class="btn" onclick="saveProfile()">บันทึกข้อมูล</button>
                <p id="age-display" style="text-align: center; margin-top: 15px; font-weight: bold; color: #4A90E2;"></p>
            </div>

            <div class="card">
                <div class="card-header"><i class="fas fa-chart-pie"></i> ภาพรวมพัฒนาการ</div>
                <div class="chart-container">
                    <canvas id="progressChart"></canvas>
                </div>
            </div>
        </div>

        <div id="page-development" class="page theme-pink">
            <div class="card" style="background: var(--pastel-pink-light);">
                <div class="card-hea
