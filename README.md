<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>aom789 - ร้านนวดแผนไทย</title>
    
    <link href="https://fonts.googleapis.com/css2?family=Mali:wght@400;600;700&family=Nunito:wght@800&display=swap" rel="stylesheet">
    
    <script type="module" src="https://unpkg.com/ionicons@7.1.0/dist/ionicons/ionicons.esm.js"></script>
    <script nomodule src="https://unpkg.com/ionicons@7.1.0/dist/ionicons/ionicons.js"></script>

    <style>
        :root {
            --primary-color: #8B5A2B; 
            --bg-color: #F5F5F7; /* ปรับพื้นหลังให้สีคล้าย Apple */
            --card-bg: #FFFFFF;
            --text-main: #4A3B32;
            --text-light: #8A7B72;
            --accent-color: #E2A76F;
            --box-blue: #5A9BFF; /* สีฟ้าของกรอบนาฬิกา */
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Mali', cursive;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-main);
            max-width: 480px;
            margin: 0 auto;
            position: relative;
            min-height: 100vh;
            padding-bottom: 80px;
            box-shadow: 0 0 20px rgba(0,0,0,0.05);
        }

        /* ส่วนหัว (Header) และ โลโก้ */
        .header {
            text-align: center;
            padding: 25px 20px;
            margin-bottom: 10px;
        }

        .logo {
            font-size: 28px;
            font-weight: 700;
            color: var(--primary-color);
            margin-bottom: 25px;
        }

        /* ----- วิดเจ็ตนาฬิกาสไตล์หน้าต่าง macOS ----- */
        .clock-widget {
            background-color: var(--card-bg);
            border-radius: 24px;
            padding: 20px;
            box-shadow: 0 8px 25px rgba(0,0,0,0.06);
            position: relative;
            margin: 0 auto;
            max-width: 240px;
            /* ลายจุดพื้นหลัง */
            background-image: radial-gradient(#E5E5E5 1.5px, transparent 1.5px);
            background-size: 14px 14px;
            background-position: center;
        }

        /* ปุ่ม แดง เหลือง เขียว */
        .mac-dots {
            display: flex;
            gap: 6px;
            margin-bottom: 20px;
        }
        .dot {
            width: 12px; height: 12px; border-radius: 50%;
        }
        .dot.red { background: #FF5F56; }
        .dot.yellow { background: #FFBD2E; }
        .dot.green { background: #27C93F; }

        /* กรอบสีฟ้าบอกเวลา */
        .time-bounding-box {
            border: 2px solid var(--box-blue);
            padding: 10px 5px;
            position: relative;
            margin-bottom: 15px;
            background: rgba(255, 255, 255, 0.6);
            backdrop-filter: blur(5px);
            z-index: 2;
        }

        /* จุดจับ (Handles) 4 มุมของกรอบ */
        .handle {
            width: 8px; height: 8px;
            border: 2px solid var(--box-blue);
            background: white;
            position: absolute;
        }
        .handle.tl { top: -5px; left: -5px; }
        .handle.tr { top: -5px; right: -5px; }
        .handle.bl { bottom: -5px; left: -5px; }
        .handle.br { bottom: -5px; right: -5px; }

        /* ตัวอักษรเวลา */
        .ampm-text {
            color: #FF5F56;
            font-weight: 700;
            font-size: 14px;
            margin-bottom: -2px;
            letter-spacing: 1px;
        }
        .time-text {
            font-size: 28px;
            font-weight: 800;
            color: #2D3436;
            font-family: 'Nunito', sans-serif; /* ใช้ฟอนต์ Nunito ให้ตัวเลขกลมสวย */
            letter-spacing: 1px;
            display: flex;
            justify-content: center;
            align-items: baseline;
        }
        .seconds-text {
            font-size: 16px;
            color: #636E72;
            margin-left: 4px;
        }

        /* ป้ายวันที่ด้านล่าง */
        .date-pill {
            background: linear-gradient(135deg, #EAC8EE, #F4A7B9);
            color: white;
            padding: 5px 18px;
            border-radius: 20px;
            font-weight: 700;
            font-size: 14px;
            position: absolute;
            bottom: -12px;
            left: 50%;
            transform: translateX(-50%);
            box-shadow: 0 4px 10px rgba(234, 200, 238, 0.6);
            white-space: nowrap;
            z-index: 3;
        }

        /* ของตกแต่ง (Decorations) */
        .weather-icon {
            position: absolute;
            top: -20px;
            right: -15px;
            font-size: 55px;
            filter: drop-shadow(0 4px 6px rgba(0,0,0,0.1));
            z-index: 3;
            transition: color 0.5s;
        }
        .weather-sun { color: #FFD166; }
        .weather-moon { color: #82CCDD; }

        .cursor-icon {
            position: absolute;
            bottom: -5px;
            left: 10px;
            font-size: 28px;
            color: #E83E8C;
            transform: rotate(-35deg);
            filter: drop-shadow(2px 3px 4px rgba(0,0,0,0.15));
            z-index: 4;
        }

        .star-icon {
            position: absolute;
            color: #FFD166;
            font-size: 16px;
            z-index: 1;
        }
        .star1 { top: 10px; left: -10px; }
        .star2 { bottom: 20px; right: 10px; font-size: 12px; }

        /* ----- ส่วนเนื้อหา (Pages) ----- */
        .page {
            display: none;
            padding: 0 20px;
            animation: fadeIn 0.4s ease;
        }
        .page.active { display: block; }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        h2 {
            font-size: 20px;
            margin-bottom: 15px;
            color: var(--primary-color);
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .service-card {
            background: var(--card-bg);
            border-radius: 16px;
            padding: 15px;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            box-shadow: 0 2px 10px rgba(0,0,0,0.03);
            transition: transform 0.2s;
        }
        .service-card:active { transform: scale(0.98); }
        .service-icon {
            font-size: 30px;
            color: var(--accent-color);
            margin-right: 15px;
            background: var(--bg-color);
            width: 50px;
            height: 50px;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 12px;
        }

        .advice-content {
            background: var(--card-bg);
            border-radius: 16px;
            padding: 20px;
            line-height: 1.6;
            box-shadow: 0 2px 10px rgba(0,0,0,0.03);
            font-size: 15px;
        }
        .advice-content h3 {
            color: var(--accent-color);
            margin-top: 15px; margin-bottom: 8px; font-size: 17px;
        }
        .advice-content ul { padding-left: 20px; margin-bottom: 15px; }

        /* ----- แถบเมนูด้านล่าง ----- */
        .bottom-nav {
            position: fixed;
            bottom: 0; left: 50%; transform: translateX(-50%);
            width: 100%; max-width: 480px; height: 70px;
            background: rgba(255, 255, 255, 0.85);
            backdrop-filter: blur(15px); -webkit-backdrop-filter: blur(15px);
            display: flex; justify-content: space-around; align-items: center;
            border-top: 1px solid rgba(0,0,0,0.05); z-index: 1000;
        }
        .nav-item {
            display: flex; flex-direction: column; align-items: center;
            color: var(--text-light); text-decoration: none; cursor: pointer;
            width: 60px; transition: all 0.3s;
        }
        .nav-item ion-icon {
            font-size: 24px; margin-bottom: 4px;
            transition: transform 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }
        .nav-item span { font-size: 12px; }
        .nav-item.active { color: var(--primary-color); }
        .nav-item.active ion-icon { transform: scale(1.2) translateY(-2px); }
        @keyframes pop {
            0% { transform: scale(1); }
            50% { transform: scale(0.8); }
            100% { transform: scale(1); }
        }
        .nav-item.clicked ion-icon { animation: pop 0.4s ease; }
    </style>
</head>
<body>

    <header class="header">
        <div class="logo">✨ aom789 ✨</div>
        
        <div class="clock-widget">
            <div class="mac-dots">
                <span class="dot red"></span>
                <span class="dot yellow"></span>
                <span class="dot green"></span>
            </div>
            
            <ion-icon name="partly-sunny" id="weather-icon" class="weather-icon weather-sun"></ion-icon>
            <ion-icon name="star" class="star-icon star1"></ion-icon>
            <ion-icon name="star" class="star-icon star2"></ion-icon>

            <div class="time-bounding-box">
                <div class="handle tl"></div>
                <div class="handle tr"></div>
                <div class="handle bl"></div>
                <div class="handle br"></div>
                
                <div class="ampm-text" id="ampm-display">AM</div>
                <div class="time-text">
                    <span id="time-display">00:00</span>
                    <span class="seconds-text" id="seconds-display">00</span>
                </div>
            </div>

            <ion-icon name="navigate" class="cursor-icon"></ion-icon>
            <div class="date-pill" id="date-display">-- ---</div>
        </div>
    </header>

    <main id="home-page" class="page active">
        <h2><ion-icon name="leaf-outline"></ion-icon> บริการของเรา</h2>
        
        <div class="service-card">
            <div class="service-icon"><ion-icon name="body-outline"></ion-icon></div>
            <div>
                <h3>นวดแผนไทย</h3>
                <p style="color: var(--text-light); font-size: 13px;">ผ่อนคลายกล้ามเนื้อ แก้อาการปวดเมื่อย</p>
            </div>
        </div>

        <div class="service-card">
            <div class="service-icon"><ion-icon name="water-outline"></ion-icon></div>
            <div>
                <h3>นวดน้ำมันอโรม่า</h3>
                <p style="color: var(--text-light); font-size: 13px;">กระตุ้นการไหลเวียนเลือด บำรุงผิว</p>
            </div>
        </div>

        <div class="service-card">
            <div class="service-icon"><ion-icon name="footsteps-outline"></ion-icon></div>
            <div>
                <h3>นวดฝ่าเท้า</h3>
                <p style="color: var(--text-light); font-size: 13px;">คลายความตึงเครียด กระตุ้นจุดสะท้อน</p>
            </div>
        </div>

        <div class="service-card">
            <div class="service-icon"><ion-icon name="flame-outline"></ion-icon></div>
            <div>
                <h3>ครอบแก้ว (Cupping)</h3>
                <p style="color: var(--text-light); font-size: 13px;">ปรับสมดุล ขับความชื้น คลายเส้น</p>
            </div>
        </div>
    </main>

    <main id="advice-page" class="page">
        <h2><ion-icon name="heart-half-outline"></ion-icon> ทริคแนะนำจากร้าน</h2>
        
        <div class="advice-content">
            <h3 style="color: #D9534F; font-size: 18px; margin-top:0;">ทำไมหลังครอบแก้วถึงอาบน้ำไม่ได้ทันที?</h3>
            <p>เหตุผลที่ “ยังไม่ควรอาบน้ำทันที” มีหลัก ๆ แบบนี้ค่ะ:</p>
            
            <h3>1. รูขุมขนยังเปิดอยู่</h3>
            <p>แรงดูดจากแก้วทำให้ผิวและรูขุมขนเปิดกว้าง ถ้าอาบน้ำทันที โดยเฉพาะน้ำเย็น ลมหรือความเย็นจะเข้าสู่ร่างกายได้ง่าย ทำให้ปวดเมื่อย หนาวในตัวได้</p>

            <h3>2. ผิวกำลังบอบบาง</h3>
            <p>จุดที่ครอบคือบริเวณที่เส้นเลือดฝอยถูกดึงขึ้นมา ถ้าโดนน้ำหรือถูแรง ๆ อาจทำให้ช้ำมากขึ้น</p>

            <h3>3. ระบบไหลเวียนกำลังทำงานหนัก</h3>
            <p>หลังครอบ ร่างกายกำลังเร่งไหลเวียนเลือด การอาบน้ำทันทีจะทำให้ระบบนี้สะดุด เหมือนเบรกกะทันหัน 🚫</p>

            <hr style="border: 0; border-top: 1px dashed #ccc; margin: 20px 0;">

            <h3>⏳ แล้วต้องรอกี่ชั่วโมงดี?</h3>
            <ul>
                <li>อย่างน้อย <strong>4–6 ชั่วโมง</strong></li>
                <li>ถ้าจะให้ดีจริง ๆ แนะนำให้รอ <strong>8 ชั่วโมง</strong> หรืออาบวันถัดไป</li>
            </ul>

            <h3>💡 ถ้าจำเป็นต้องอาบจริง ๆ</h3>
            <ul>
                <li>ใช้น้ำอุ่น (ไม่ใช่น้ำเย็นเด็ดขาด)</li>
                <li>หลีกเลี่ยงการขัดหรือถูบริเวณที่ครอบแก้ว</li>
                <li>อาบแบบเร็ว ๆ ไม่แช่น้ำนาน</li>
            </ul>
        </div>
    </main>

    <nav class="bottom-nav">
        <div class="nav-item active" onclick="switchPage('home', this)">
            <ion-icon name="home"></ion-icon>
            <span>Home</span>
        </div>
        <div class="nav-item" onclick="switchPage('advice', this)">
            <ion-icon name="heart-outline"></ion-icon>
            <span>Advice</span>
        </div>
    </nav>

    <script>
        // --- 1. ระบบวันและเวลาอัปเดตแบบ Real-time ตามเรฟเฟอเรนซ์ ---
        function updateDateTime() {
            const now = new Date();
            
            // จัดการเวลา 12 ชั่วโมง (AM/PM)
            let hours = now.getHours();
            let minutes = now.getMinutes();
            let seconds = now.getSeconds();
            const ampm = hours >= 12 ? 'PM' : 'AM';
            
            hours = hours % 12;
            hours = hours ? hours : 12; // ถ้า 0 ให้แสดงเป็น 12
            
            // เติมเลข 0 ข้างหน้าถ้าเป็นเลขหลักเดียว
            const hoursStr = hours < 10 ? '0' + hours : hours;
            const minutesStr = minutes < 10 ? '0' + minutes : minutes;
            const secondsStr = seconds < 10 ? '0' + seconds : seconds;
            
            document.getElementById('ampm-display').textContent = ampm;
            document.getElementById('time-display').textContent = hoursStr + ':' + minutesStr;
            document.getElementById('seconds-display').textContent = secondsStr;

            // เปลี่ยนไอคอนพระอาทิตย์/พระจันทร์ ตามเวลา (6 โมงเช้า - 6 โมงเย็นเป็นพระอาทิตย์)
            const weatherIcon = document.getElementById('weather-icon');
            if (now.getHours() >= 6 && now.getHours() < 18) {
                weatherIcon.name = 'partly-sunny';
                weatherIcon.classList.remove('weather-moon');
                weatherIcon.classList.add('weather-sun');
            } else {
                weatherIcon.name = 'moon';
                weatherIcon.classList.remove('weather-sun');
                weatherIcon.classList.add('weather-moon');
            }

            // จัดการวันที่ (ให้แสดงแบบสั้นๆ เช่น 16 ธ.ค. หรือ Dec 16 เพื่อให้พอดีกรอบ)
            const thaiMonths = ["ม.ค.", "ก.พ.", "มี.ค.", "เม.ย.", "พ.ค.", "มิ.ย.", "ก.ค.", "ส.ค.", "ก.ย.", "ต.ค.", "พ.ย.", "ธ.ค."];
            const dateStr = now.getDate() + ' ' + thaiMonths[now.getMonth()];
            document.getElementById('date-display').textContent = dateStr;
        }
        
        updateDateTime();
        setInterval(updateDateTime, 1000);


        // --- 2. ระบบเปลี่ยนหน้าและแอนิเมชันเมนู ---
        function switchPage(pageName, clickedElement) {
            const navItems = document.querySelectorAll('.nav-item');
            navItems.forEach(item => {
                item.classList.remove('active');
                item.classList.remove('clicked');
                const icon = item.querySelector('ion-icon');
                if(item.innerText.trim() === 'Home') icon.name = 'home-outline';
                if(item.innerText.trim() === 'Advice') icon.name = 'heart-outline';
            });

            clickedElement.classList.add('active');
            clickedElement.classList.add('clicked');
            
            const activeIcon = clickedElement.querySelector('ion-icon');
            if(pageName === 'home') activeIcon.name = 'home';
            if(pageName === 'advice') activeIcon.name = 'heart';

            setTimeout(() => { clickedElement.classList.remove('clicked'); }, 400);

            document.querySelectorAll('.page').forEach(page => {
                page.classList.remove('active');
            });

            document.getElementById(pageName + '-page').classList.add('active');
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }
    </script>

</body>
</html>
