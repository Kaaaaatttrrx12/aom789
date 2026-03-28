<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>aom789 - ร้านนวดแผนไทย</title>
    
    <link href="https://fonts.googleapis.com/css2?family=Mali:wght@400;600;700&family=Nunito:wght@400;600;700;800&display=swap" rel="stylesheet">
    
    <script type="module" src="https://unpkg.com/ionicons@7.1.0/dist/ionicons/ionicons.esm.js"></script>
    <script nomodule src="https://unpkg.com/ionicons@7.1.0/dist/ionicons/ionicons.js"></script>

    <style>
        :root {
            --primary-color: #8B5A2B; 
            --bg-color: #F8F9FA; /* พื้นหลังสีสว่างขึ้นเล็กน้อยเพื่อให้ตัดกับแสงสี */
            --card-bg: #FFFFFF;
            --text-main: #4A3B32;
            --text-light: #8A7B72;
            --accent-color: #E2A76F;
            --bar-color: rgba(255, 255, 255, 0.9);
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
            padding-bottom: 130px;
        }

        /* ส่วนหัว (Header) และ โลโก้ */
        .header {
            text-align: center;
            padding: 20px 20px 0 20px;
        }

        .logo {
            font-size: 28px;
            font-weight: 700;
            color: var(--primary-color);
            margin-bottom: 15px;
        }

        /* ----- วิดเจ็ตปฏิทินสไตล์ Glassmorphism (ตามรูป) ----- */
        .widget-container {
            position: relative;
            margin: 0 auto 30px auto;
            width: 100%;
            max-width: 340px;
            height: 330px;
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: 'Nunito', sans-serif; /* ใช้ฟอนต์ Nunito ให้เหมือนรูป */
        }

        /* แสงออร่าด้านหลัง (วงกลมไล่สีเบลอๆ) */
        .widget-glow {
            position: absolute;
            width: 250px;
            height: 250px;
            background: radial-gradient(circle at center, #E94086 0%, #FF8A5B 65%, transparent 100%);
            filter: blur(35px);
            opacity: 0.9;
            z-index: 0;
            top: 55%;
            left: 50%;
            transform: translate(-50%, -50%);
        }

        /* กระจกเบลอครอบด้านหน้า */
        .glass-calendar {
            position: relative;
            width: 100%;
            height: 100%;
            background: rgba(255, 255, 255, 0.35);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border-radius: 32px;
            border: 1.5px solid rgba(255, 255, 255, 0.6);
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.08);
            z-index: 1;
            padding: 24px;
            display: flex;
            flex-direction: column;
            color: white;
            overflow: hidden; /* ไม่ให้เส้นโค้งทะลุกรอบ */
        }

        /* ส่วนหัวของปฏิทิน (Tabs & Gear) */
        .cal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .cal-tabs {
            display: flex;
            background: rgba(255, 255, 255, 0.25);
            border-radius: 12px;
            padding: 4px;
            width: 180px;
        }

        .cal-tab {
            flex: 1;
            text-align: center;
            padding: 8px 0;
            font-size: 13px;
            border-radius: 8px;
            color: rgba(255, 255, 255, 0.9);
            font-weight: 600;
        }

        .cal-tab.active {
            background: white;
            color: #1A1A1A;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
        }

        .cal-gear {
            width: 34px;
            height: 34px;
            background: rgba(255, 255, 255, 0.4);
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            color: #1A1A1A;
            font-size: 18px;
        }

        /* ส่วนชื่อเดือน และวันที่ตัวใหญ่ */
        .cal-title {
            display: flex;
            justify-content: space-between;
            align-items: baseline;
            margin-top: 30px;
            padding: 0 5px;
        }

        .cal-month {
            font-size: 42px;
            font-weight: 700;
            line-height: 1;
            text-shadow: 0 2px 15px rgba(233, 64, 134, 0.2);
        }

        .cal-date-big {
            font-size: 58px;
            font-weight: 800;
            line-height: 0.8;
            text-shadow: 0 2px 15px rgba(255, 138, 91, 0.2);
        }

        /* ส่วนวันในสัปดาห์แนวนอนแบบโค้ง */
        .cal-week-wrapper {
            position: relative;
            margin-top: 35px;
            height: 70px;
            display: flex;
            align-items: center;
        }

        /* เส้นโค้งโปร่งแสงด้านหลัง */
        .cal-curve {
            position: absolute;
            top: 22px;
            left: -15%;
            width: 130%;
            height: 60px;
            border-top: 1.5px solid rgba(255, 255, 255, 0.5);
            border-radius: 50%;
            z-index: 0;
        }
        
        .cal-curve-2 {
            top: 52px;
            border-top: 1px solid rgba(255, 255, 255, 0.15);
        }

        .cal-days {
            position: relative;
            z-index: 1;
            display: flex;
            justify-content: space-between;
            width: 100%;
            align-items: flex-start;
        }

        .cal-day {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 8px;
            transition: all 0.3s;
        }

        .cal-day-name {
            font-size: 12px;
            font-weight: 600;
        }

        .cal-day-num {
            width: 32px;
            height: 32px;
            display: flex;
            justify-content: center;
            align-items: center;
            border-radius: 50%;
            font-size: 14px;
            font-weight: 600;
        }

        /* ไฮไลท์สำหรับวันปัจจุบัน (วงกลมแดง-ส้ม) */
        .cal-day.active .cal-day-num {
            background: linear-gradient(135deg, #FF007F, #FF7B54);
            color: white;
            font-weight: 800;
            box-shadow: 0 4px 12px rgba(255, 0, 127, 0.3);
        }

        /* ส่วนท้าย (Add a note & New Event) */
        .cal-footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-top: auto;
        }

        .cal-note {
            font-size: 13px;
            color: rgba(255, 255, 255, 0.95);
            display: flex;
            align-items: center;
            gap: 6px;
            font-weight: 600;
        }

        .cal-new-btn {
            background: rgba(255, 255, 255, 0.9);
            color: #1A1A1A;
            padding: 8px 16px;
            border-radius: 20px;
            font-size: 13px;
            font-weight: 800;
            display: flex;
            align-items: center;
            gap: 4px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.05);
        }

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
        }
        .service-icon {
            font-size: 30px;
            color: var(--accent-color);
            margin-right: 15px;
            background: var(--bg-color);
            width: 50px; height: 50px;
            display: flex; align-items: center; justify-content: center;
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
        .advice-content h3 { color: var(--accent-color); margin-top: 15px; margin-bottom: 8px; font-size: 17px; }
        .advice-content ul { padding-left: 20px; margin-bottom: 15px; }

        /* ----- แถบเมนูด้านล่าง redesign เป็นเกาะลอยเบลอสูง ----- */
        .bottom-nav {
            position: fixed;
            bottom: 25px; 
            left: 50%; 
            transform: translateX(-50%);
            width: calc(100% - 40px); 
            max-width: 440px; 
            height: 85px; 
            background: var(--bar-color); 
            backdrop-filter: blur(25px); 
            -webkit-backdrop-filter: blur(25px);
            display: flex; 
            justify-content: space-around; 
            align-items: center;
            border-radius: 40px; 
            z-index: 1000;
            box-shadow: 0 10px 40px rgba(0,0,0,0.1); 
            padding: 10px 15px; 
        }

        .nav-item {
            display: flex; flex-direction: column; align-items: center;
            color: var(--text-light); cursor: pointer;
            width: 80px; position: relative; 
        }

        .nav-item ion-icon {
            font-size: 30px; margin-bottom: 2px;
            transition: transform 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            animation: dugDikJiggle 3s infinite linear; 
        }

        .nav-item span { font-size: 13px; font-weight: 600; color: #535353; font-family: 'Nunito', 'Mali', sans-serif; }
        .nav-item.active { color: #535353; }
        .nav-item.active ion-icon { transform: translateY(-2px); animation: dugDikJiggle 3s infinite linear; }
        .nav-item.active span { font-weight: 800; }

        @keyframes dugDikScale { 
            0% { transform: scale(1); }
            50% { transform: scale(1.15); }
            100% { transform: scale(1); }
        }
        @keyframes dugDikJiggle { 
            0% { transform: translate(0, 0) scale(1) rotate(0deg); }
            20% { transform: translate(1px, -1px) scale(1.02) rotate(1deg); }
            40% { transform: translate(-1px, 1px) scale(1.02) rotate(-1deg); }
            60% { transform: translate(1px, 1px) scale(1) rotate(1deg); }
            80% { transform: translate(-1px, -1px) scale(1) rotate(-1deg); }
            100% { transform: translate(0, 0) scale(1) rotate(0deg); }
        }
        .nav-item.clicked ion-icon { animation: dugDikScale 0.4s ease, dugDikJiggle 3s infinite linear; }

    </style>
</head>
<body>

    <header class="header">
        <div class="logo">✨ aom789 ✨</div>
        
        <div class="widget-container">
            <div class="widget-glow"></div>
            
            <div class="glass-calendar">
                
                <div class="cal-header">
                    <div class="cal-tabs">
                        <div class="cal-tab active">Weekly</div>
                        <div class="cal-tab">Monthly</div>
                    </div>
                    <div class="cal-gear">
                        <ion-icon name="settings-outline"></ion-icon>
                    </div>
                </div>
                
                <div class="cal-title">
                    <div class="cal-month" id="cal-month">August</div>
                    <div class="cal-date-big" id="cal-date-big">23</div>
                </div>
                
                <div class="cal-week-wrapper">
                    <div class="cal-curve"></div>
                    <div class="cal-curve cal-curve-2"></div>
                    <div class="cal-days" id="cal-days-container">
                        </div>
                </div>
                
                <div class="cal-footer">
                    <div class="cal-note"><ion-icon name="pencil-outline"></ion-icon> Add a note...</div>
                    <div class="cal-new-btn"><ion-icon name="add"></ion-icon> New Event</div>
                </div>
                
            </div>
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
            <span>Portfolio</span>
        </div>
    </nav>

    <script>
        // --- 1. ระบบอัปเดตปฏิทินให้อัตโนมัติ ---
        function updateCalendarWidget() {
            const now = new Date();
            
            // ชื่อเดือนภาษาอังกฤษเพื่อให้ความสวยงามตรงกับรูปต้นแบบ
            const monthNames = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
            
            // อัปเดตเดือนและวันที่ตัวใหญ่
            document.getElementById('cal-month').textContent = monthNames[now.getMonth()];
            document.getElementById('cal-date-big').textContent = now.getDate();

            const daysContainer = document.getElementById('cal-days-container');
            daysContainer.innerHTML = '';
            
            const dayNames = ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"];
            
            // สร้างวันในสัปดาห์ (ย้อนหลัง 3 วัน และล่วงหน้า 3 วัน เพื่อให้วันปัจจุบันอยู่ตรงกลาง)
            for(let i = -3; i <= 3; i++) {
                const d = new Date(now);
                d.setDate(now.getDate() + i);
                
                const dayEl = document.createElement('div');
                dayEl.className = 'cal-day' + (i === 0 ? ' active' : '');
                
                // การคำนวณโค้ง: ยิ่งอยู่ไกลจากตรงกลาง (i=0) ยิ่งขยับตำแหน่งแกน Y ลงด้านล่าง
                const yOffset = Math.abs(i) * 5; 
                dayEl.style.transform = `translateY(${yOffset}px)`;
                
                // ให้วันที่อยู่ขอบๆ ค่อยๆ จางลง
                if (Math.abs(i) === 3) dayEl.style.opacity = '0.4';
                else if (Math.abs(i) === 2) dayEl.style.opacity = '0.7';
                else if (Math.abs(i) === 1) dayEl.style.opacity = '0.9';
                
                dayEl.innerHTML = `
                    <div class="cal-day-name">${dayNames[d.getDay()]}</div>
                    <div class="cal-day-num">${d.getDate()}</div>
                `;
                daysContainer.appendChild(dayEl);
            }
        }
        
        // รันครั้งแรกเมื่อเปิดเว็บ
        updateCalendarWidget();
        // ตั้งให้รันเช็คการเปลี่ยนวันทุกๆ 1 ชั่วโมง (กันคนเปิดเว็บทิ้งไว้ข้ามวัน)
        setInterval(updateCalendarWidget, 3600000); 


        // --- 2. ระบบเปลี่ยนหน้าและแอนิเมชันเมนู (เหมือนเดิม) ---
        function switchPage(pageName, clickedElement) {
            const navItems = document.querySelectorAll('.nav-item');
            navItems.forEach(item => {
                item.classList.remove('active');
                item.classList.remove('clicked');
                const icon = item.querySelector('ion-icon');
                const text = item.querySelector('span').innerText.trim();
                if (text === 'Home') icon.name = 'home-outline';
                if (text === 'Portfolio') icon.name = 'heart-outline';
            });

            clickedElement.classList.add('active');
            clickedElement.classList.add('clicked');
            
            const activeIcon = clickedElement.querySelector('ion-icon');
            const activeText = clickedElement.querySelector('span').innerText.trim();
            if (activeText === 'Home') activeIcon.name = 'home';
            if (activeText === 'Portfolio') activeIcon.name = 'heart';

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
