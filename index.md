<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>68GB VIP TOOL - HOANGDZ</title>
    <style>
        :root { --neon: #00ffff; --gold: #ffcc00; --red: #ff4d4d; --green: #2ecc71; }
        * { margin:0; padding:0; box-sizing:border-box; -webkit-user-select:none; touch-action:none; }
        
        body { 
            background: radial-gradient(circle at center, #1a1a1a 0%, #000 100%);
            height: 100vh; display: flex; align-items: center; justify-content: center;
            font-family: 'Segoe UI', sans-serif; overflow: hidden;
        }

        /* BACKGROUND HIỆU ỨNG */
        .bg-glow {
            position: absolute; width: 300px; height: 300px;
            background: var(--neon); filter: blur(150px); opacity: 0.15; z-index: 0;
        }

        /* THÔNG BÁO POPUP */
        #overlay {
            position: fixed; inset: 0; background: rgba(0,0,0,0.95);
            z-index: 10001; display: flex; align-items: center; justify-content: center;
            backdrop-filter: blur(15px);
        }
        .popup {
            width: 85%; max-width: 400px; background: rgba(20,20,20,0.9);
            border: 2px solid var(--neon); border-radius: 30px; padding: 40px 20px;
            text-align: center; color: white; box-shadow: 0 0 50px rgba(0,255,255,0.2);
        }
        .popup h1 { font-size: 28px; color: var(--neon); text-shadow: 0 0 10px var(--neon); }
        .popup p { margin: 20px 0; color: #aaa; font-size: 14px; }
        .popup b { color: var(--gold); }
        .close-btn {
            background: var(--neon); color: #000; border: none; padding: 12px 50px;
            border-radius: 50px; font-weight: bold; cursor: pointer; transition: 0.3s;
        }

        /* GIAO DIỆN TOOL CHÍNH */
        #tool-container {
            position: relative; z-index: 10;
            background: rgba(255, 255, 255, 0.03); backdrop-filter: blur(30px);
            border: 1px solid rgba(255, 255, 255, 0.1); border-radius: 40px;
            padding: 40px; width: 90%; max-width: 450px;
            text-align: center; box-shadow: 0 25px 50px rgba(0,0,0,0.5);
            transform: scale(1) rotate(0deg); transition: 0.3s cubic-bezier(0.1, 0.7, 0.1, 1);
        }

        #robot { width: 80px; filter: drop-shadow(0 0 10px var(--neon)); margin-bottom: 15px; }
        
        .title-68 { font-size: 24px; font-weight: 900; color: #fff; letter-spacing: 2px; margin-bottom: 5px; }
        .title-68 span { color: var(--neon); }

        #phien-txt { font-size: 18px; color: var(--gold); font-weight: bold; margin-bottom: 20px; }

        .display-area {
            display: flex; justify-content: space-between; align-items: center;
            background: rgba(0,0,0,0.4); padding: 20px; border-radius: 25px;
            border: 1px solid rgba(0,255,255,0.2); margin-bottom: 25px;
        }

        .lamp { width: 65px; height: 65px; border-radius: 50%; border: 4px solid #111; transition: 0.5s; }
        .active-t { background: var(--green); box-shadow: 0 0 40px var(--green); border-color: #fff; animation: blink 0.5s infinite alternate; }
        .active-x { background: var(--red); box-shadow: 0 0 40px var(--red); border-color: #fff; animation: blink 0.5s infinite alternate; }
        @keyframes blink { from { opacity: 0.4; transform: scale(0.9); } to { opacity: 1; transform: scale(1.05); } }

        #status-txt { font-weight: bold; font-size: 14px; margin-top: 10px; }
        .scanning { color: var(--green); animation: pulse 0.7s infinite; }
        @keyframes pulse { 50% { opacity: 0.3; } }

        /* NÚT ĐIỀU KHIỂN DƯỚI TOOL */
        .controls { display: flex; gap: 10px; justify-content: center; margin-top: 20px; }
        .btn-ctrl {
            background: rgba(255,255,255,0.1); color: white; border: none;
            width: 45px; height: 45px; border-radius: 12px; font-weight: bold;
            display: flex; align-items: center; justify-content: center; cursor: pointer;
        }
        .btn-ctrl:active { background: var(--neon); color: #000; }
    </style>
</head>
<body>

    <div class="bg-glow"></div>

    <div id="overlay">
        <div class="popup">
            <h1>68 GAME BÀI</h1>
            <p>Phần mềm dự đoán của <b>TRẦN HOÀNG</b><br>Hệ thống tự động cộng phiên & soi cầu chuẩn.<br><br>Hỗ trợ: <b>@tranhoang2286</b></p>
            <button class="close-btn" onclick="document.getElementById('overlay').style.display='none'">KHỞI CHẠY TOOL</button>
        </div>
    </div>

    <div id="tool-container">
        <img id="robot" src="https://i.postimg.cc/rwkZQhxp/Robot.gif">
        <div class="title-68">TOOL <span>68GB</span> VIP</div>
        <div id="phien-txt">#PHIÊN_ĐANG_ĐỢI</div>

        <div class="display-area">
            <div style="text-align:center;"><b style="color:#666; font-size:10px; display:block;">TÀI</b><div id="lt" class="lamp"></div></div>
            
            <div id="center-info">
                <div id="status-txt" class="scanning" style="display:none;">🔎 ĐANG QUÉT...</div>
                <div id="result-box">
                    <div id="rate-txt" style="color:var(--neon); font-size:12px; font-weight:bold;">WIN: 0%</div>
                </div>
            </div>

            <div style="text-align:center;"><b style="color:#666; font-size:10px; display:block;">XỈU</b><div id="lx" class="lamp"></div></div>
        </div>

        <div class="controls">
            <button class="btn-ctrl" onclick="scaleTool(0.1)">➕</button>
            <button class="btn-ctrl" onclick="scaleTool(-0.1)">➖</button>
            <button class="btn-ctrl" onclick="rotateTool(90)">🔄</button>
            <button class="btn-ctrl" onclick="location.reload()">🔄</button>
        </div>
        <p style="color:#555; font-size:10px; margin-top:20px;">DESIGNED BY TRAN HOANG</p>
    </div>

    <script>
        let sc = 1, rt = 0;
        const tool = document.getElementById("tool-container");

        function scaleTool(v) { sc = Math.max(0.5, Math.min(1.5, sc + v)); updateStyle(); }
        function rotateTool(v) { rt = (rt === 90) ? 0 : 90; updateStyle(); }
        function updateStyle() { tool.style.transform = `scale(${sc}) rotate(${rt}deg)`; }

        async function sync() {
            try {
                const res = await fetch("http://127.0.0.1:3000/api/get-data");
                const d = await res.json();
                
                document.getElementById("phien-txt").innerText = "#PHIÊN: " + d.phien;
                
                const st = document.getElementById("status-txt"), rb = document.getElementById("result-box");
                const lt = document.getElementById("lt"), lx = document.getElementById("lx");

                if(d.is_analyzing) {
                    st.style.display = "block"; rb.style.display = "none";
                    lt.className = "lamp"; lx.className = "lamp";
                } else {
                    st.style.display = "none"; rb.style.display = "block";
                    document.getElementById("rate-txt").innerText = "XÁC SUẤT: " + d.rate;
                    
                    lt.className = "lamp"; lx.className = "lamp";
                    if(d.dudoan === "TÀI") lt.classList.add("active-t");
                    if(d.dudoan === "XỈU") lx.classList.add("active-x");
                    if(d.dudoan === "WAIT") { lt.className = "lamp"; lx.className = "lamp"; }
                }
            } catch(e) {}
        }
        setInterval(sync, 1000);
    </script>
</body>
</html>
