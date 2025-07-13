<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no" />
  <title>การ์ดวันเกิด</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Prompt&display=swap');
    html, body {
      margin: 0;
      padding: 0;
      background-color: #000;
      font-family: 'Prompt', sans-serif;
      overflow: hidden;
      height: 100%;
    }

    .wrapper {
      width: 1125px;
      height: 2436px;
      display: flex;
      justify-content: center;
      align-items: center;
      overflow: hidden;
      margin: 0 auto;
      border-radius: 20px;
      box-shadow: 0 0 30px rgba(0,0,0,0.3);
      background-color: #000;
      flex-direction: column;
      position: relative;
    }

    .page {
      width: 1125px;
      height: 2436px;
      background-size: cover;
      background-position: center;
      background-repeat: no-repeat;
      display: none;
      flex-direction: column;
      justify-content: space-between;
      align-items: center;
      padding: 100px 50px;
      border-radius: 20px;
      box-sizing: border-box;
      text-align: center;
      color: #fff;
      text-shadow: 2px 2px 5px #000;
    }

    .page.active {
      display: flex;
    }

    .message-line {
      font-size: 42px;
      color: #fff;
      text-shadow: 2px 2px 5px #000;
      margin: 20px 0;
      opacity: 0;
      animation: fadeIn 0.8s ease forwards;
    }

    @keyframes fadeIn {
      to {
        opacity: 1;
      }
    }

    button {
      padding: 24px 48px;
      font-size: 28px;
      background-color: #A5CBE2;
      color: #000;
      border: none;
      border-radius: 12px;
      cursor: pointer;
      margin-bottom: 100px;
      display: none;
      user-select: none;
      transition: background-color 0.3s ease;
    }

    button:hover {
      background-color: #89b8d6;
    }

    button.show {
      display: block !important;
    }

    h2 {
      font-size: 48px;
      color: white;
      text-shadow: 2px 2px 6px black;
      margin-top: 200px;
    }
  </style>
</head>
<body>
  <div class="wrapper">
    <!-- หน้า 1 -->
    <div class="page active" id="page1" style="background-image: url('happy-01.png');">
      <div style="flex: 1; display: flex; justify-content: center; align-items: center; flex-direction: column;">
        <div id="messageBox" style="text-align: center;"></div>
        <button id="startBtn" onclick="startExperience()">เริ่ม</button>
      </div>
    </div>

    <!-- หน้า 2 -->
    <div class="page" id="page2" style="background-image: url('happy-02.png');">
      <h2>อธิษฐานแล้วเป่าเทียนสิ 🎂</h2>
      <button class="show" onclick="goToPage(3)">เป่าเทียน</button>
    </div>

    <!-- หน้า 3 -->
    <div class="page" id="page3" style="background-image: url('happy-03.png');">
      <div></div>
      <button class="show" onclick="goToPage(4)">คำอวยพร</button>
    </div>

    <!-- หน้า 4 -->
    <div class="page" id="page4" style="background-image: url('happy-04.png');">
      <div></div>
      <button class="show" onclick="goToPage(5)">รับของขวัญ</button>
    </div>

    <!-- หน้า 5 -->
    <div class="page" id="page5" style="background-image: url('happy-05.png');">
      <div></div>
      <h2>สุขสันต์วันเกิด ขอให้วันนี้เป็นวันที่ดีที่สุด 🎉</h2>
    </div>
  </div>

  <audio id="bgMusic" loop>
    <source src="v10044g50000ct87a37og65l4b42lb40 (online-audio-converter.com).mp3" type="audio/mpeg" />
    <!-- เพิ่มไฟล์เสียงอื่น ๆ ตามต้องการ -->
  </audio>

  <script>
    function scaleToFit() {
      const designWidth = 1125;
      const designHeight = 2436;
      const wrapper = document.querySelector(".wrapper");

      const scaleX = window.innerWidth / designWidth;
      const scaleY = window.innerHeight / designHeight;
      const scale = Math.min(scaleX, scaleY);

      wrapper.style.transform = `scale(${scale})`;
      wrapper.style.transformOrigin = "top left";
      wrapper.style.width = `${designWidth}px`;
      wrapper.style.height = `${designHeight}px`;
    }

    window.addEventListener("resize", scaleToFit);
    window.addEventListener("load", () => {
      scaleToFit();

      const messages = [
        "จ๊ะเอ๋! งงไปเลยล่ะดิ",
        "นี่อะไรน้าาา~",
        "ไม่บอกอ่ะ แบร่~",
        "เดี๋ยวๆ อย่าเพิ่งตี ล้อเล่น!",
        "บอกก็ได้จ้าา~"
      ];

      const box = document.getElementById("messageBox");
      const startBtn = document.getElementById("startBtn");

      messages.forEach((msg, i) => {
        setTimeout(() => {
          const p = document.createElement("p");
          p.className = "message-line";
          p.textContent = msg;
          box.appendChild(p);

          if (i === messages.length - 1) {
            setTimeout(() => {
              startBtn.classList.add('show');
            }, 1000);
          }
        }, i * 1800);
      });
    });

    function goToPage(num) {
      document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
      document.getElementById('page' + num).classList.add('active');
    }

    const music = document.getElementById("bgMusic");

    function startExperience() {
      music.play().catch(() => {
        console.log("ผู้ใช้ต้องกดก่อนถึงจะเล่นเสียงได้");
      });
      goToPage(2);
    }
  </script>
</body>
</html>
