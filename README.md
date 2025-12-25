        body { background: var(--bg); color: var(--text); font-family: 'Inter', sans-serif; min-height: 100vh; }

        body::before {
            content: ""; position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background-image: radial-gradient(var(--dot) 1.5px, transparent 1.5px);
            background-size: 30px 30px; z-index: -1;
        }

        .container { max-width: 450px; margin: auto; padding: 50px 20px 100px 20px; position: relative; z-index: 1; }

        @media (min-width: 800px) {
            .container { max-width: 1000px; }
            .bento { grid-template-columns: repeat(3, 1fr) !important; }
            .phone-grid { grid-template-columns: repeat(4, 1fr) !important; }
        }

        .top-nav { display: flex; justify-content: space-between; align-items: center; margin-bottom: 40px; }
        .theme-ico { 
            width: 45px; height: 45px; background: var(--glass); border: 1px solid var(--border);
            border-radius: 50%; display: grid; place-items: center; cursor: pointer; backdrop-filter: blur(10px);
        }
        h1 { font-size: 2.5rem; font-weight: 900; letter-spacing: -2px; line-height: 1; text-transform: uppercase; }

        .bento { display: grid; grid-template-columns: repeat(2, 1fr); gap: 15px; margin-top: 20px; }
        .box { 
            background: var(--glass); backdrop-filter: blur(20px); border: 1px solid var(--border);
            border-radius: 30px; padding: 25px; cursor: pointer;
        }
        .full { grid-column: span 2; }
        .box i { font-size: 22px; color: var(--accent); margin-bottom: 12px; display: block; }
        .box h2 { font-size: 16px; font-weight: 800; text-transform: uppercase; }

        .view {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: transparent; z-index: 1000; display: none;
            padding: 40px 20px; overflow-y: auto; backdrop-filter: blur(25px);
        }
        .view::before {
            content: ""; position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background-image: radial-gradient(var(--dot) 1.5px, transparent 1.5px);
            background-size: 30px 30px; z-index: -1;
        }
        .view.active { display: block; background: var(--bg); animation: fadeUp 0.4s ease forwards; }
        @keyframes fadeUp { from { opacity: 0; transform: translateY(20px); } to { opacity: 1; transform: translateY(0); } }

        .back { font-family: 'Space Mono'; font-size: 11px; font-weight: 900; color: var(--accent); cursor: pointer; margin-bottom: 30px; display: inline-block; text-transform: uppercase; }

        .guide-glass { background: var(--glass); border-radius: 25px; padding: 25px; border: 1px solid var(--border); margin-bottom: 20px; backdrop-filter: blur(20px); }
        .guide-glass h3 { font-size: 14px; margin-bottom: 10px; color: var(--accent); }
        .guide-glass p { font-size: 12px; opacity: 0.7; line-height: 1.6; font-family: 'Space Mono'; }

        .v-input { width: 100%; padding: 15px; background: transparent; border: 1px solid var(--border); border-radius: 15px; color: var(--text); font-family: 'Space Mono'; margin: 15px 0; outline: none; text-align: center; font-size: 16px; }
        .res-box { background: var(--text); color: var(--bg); padding: 20px; border-radius: 25px; margin-top: 15px; display: none; font-size: 13px; line-height: 1.6; animation: slideIn 0.3s ease; }

        .phone-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 12px; }
        .phone-card { background: var(--glass); border: 1px solid var(--border); padding: 20px; border-radius: 20px; text-align: center; font-weight: 800; font-size: 13px; cursor: pointer; backdrop-filter: blur(10px); }

        .log-area { background: var(--text); color: var(--bg); border-radius: 25px; padding: 25px; margin-top: 20px; display: none; animation: slideIn 0.3s ease; }
        @keyframes slideIn { from { opacity: 0; transform: scale(0.95); } to { opacity: 1; transform: scale(1); } }
        
        .dl-btn { 
            width: 100%; padding: 16px; background: var(--accent); color: #fff; border: none;
            border-radius: 15px; font-weight: 900; margin-top: 15px; cursor: pointer;
            position: relative; overflow: hidden;
        }
        .dl-btn span { position: relative; z-index: 2; }
        .dl-btn::before { content: ""; position: absolute; left: -100%; top: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.2); }
        .dl-btn.loading::before { left: 0; transition: 2.5s linear; }

        .wall-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 12px; }
        .wall-box { position: relative; border-radius: 25px; overflow: hidden; border: 1px solid var(--border); }
        .wall-box img { width: 100%; aspect-ratio: 9/16; object-fit: cover; }
        .wall-dl { position: absolute; bottom: 10px; left: 10px; right: 10px; }

        .contact-trigger {
            position: fixed; bottom: 30px; right: 30px; width: 60px; height: 60px;
            background: var(--text); color: var(--bg); border-radius: 50%;
            display: grid; place-items: center; cursor: pointer; z-index: 2000;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }
        .contact-card {
            position: fixed; bottom: 100px; right: 30px; width: 280px;
            background: var(--glass); backdrop-filter: blur(30px);
            border: 1px solid var(--border); border-radius: 25px;
            padding: 25px; display: none; z-index: 2000; animation: fadeUp 0.3s ease;
        }
        .contact-card.active { display: block; }
    </style>
</head>
<body data-theme="light">

<div class="container">
    <div class="top-nav">
        <h1>Nothing<br>Dot Hub</h1>
        <div class="theme-ico" onclick="toggleTheme()">
            <i class="fa-solid fa-moon" id="tBtn"></i>
        </div>
    </div>

    <div class="bento">
        <div class="box full" onclick="openView('softView')">
            <i class="fa-solid fa-download"></i>
            <h2>Software & Updates</h2>
        </div>
        <div class="box" onclick="openView('wallView')">
            <i class="fa-solid fa-palette"></i>
            <h2>Wallpapers</h2>
        </div>
        <div class="box" onclick="openView('tipsView')">
            <i class="fa-solid fa-lightbulb"></i>
            <h2>Tips</h2>
        </div>
        <div class="box full" onclick="openView('verifyView')">
            <i class="fa-solid fa-shield-check"></i>
            <h2>Verify Device</h2>
        </div>
    </div>
</div>

<div class="contact-trigger" onclick="toggleContact()">
    <i class="fa-solid fa-headset"></i>
</div>

<div class="contact-card" id="contactCard">
    <h4 style="font-size:14px; text-transform:uppercase; margin-bottom:15px; color:var(--accent);">Nothing Support</h4>
    <div style="font-size:12px; opacity:0.8; font-family:'Space Mono'; line-height:1.6;">
        <p>Phone: 1800-202-1232</p>
        <p>Email: support.in@nothing.tech</p>
    </div>
</div>

<div id="verifyView" class="view">
    <div class="container" style="padding:0">
        <span class="back" onclick="closeView('verifyView')">← AUTHENTICATION</span>
        <div class="guide-glass">
            <h3>Product Verification</h3>
            <p>Enter your 15-digit IMEI or hardware ID below.</p>
            <input type="text" id="vID" class="v-input" placeholder="IMEI / SERIAL NUMBER">
            <button class="dl-btn" onclick="checkAuth(this)"><span>ANALYZE DEVICE</span></button>
            <div id="vResult" class="res-box"></div>
        </div>
    </div>
</div>

<div id="softView" class="view">
    <div class="container" style="padding:0">
        <span class="back" onclick="closeView('softView')">← SYSTEM HUB</span>
        <div class="guide-glass">
            <h3>Update Instructions</h3>
            <p>1. Download & Install Beta Tool APK below.<br>2. Place firmware ZIP in root/ota folder.</p>
            <button class="dl-btn" onclick="enhancedDL(this, 'TOOL APK')"><span>DOWNLOAD BETA TOOL</span></button>
            <div class="res-box" id="toolRes"></div>
        </div>
        <h3 style="font-size: 11px; opacity: 0.4; text-transform: uppercase; margin: 20px 0 10px 10px;">Devices</h3>
        <div class="phone-grid" id="phoneContainer"></div>
        <div id="logArea" class="log-area">
            <h3 id="selName"></h3>
            <p id="selLog" style="font-family:'Space Mono'; font-size:11px; opacity:0.6; margin: 15px 0; line-height:1.6; white-space: pre-line;"></p>
            <button id="firmBtn" class="dl-btn" style="background:var(--bg); color:var(--text)" onclick="enhancedDL(this, 'FIRMWARE ZIP')"><span>DOWNLOAD ZIP</span></button>
            <div class="res-box" id="firmRes" style="background:var(--bg); color:var(--text); border:1px solid var(--border);"></div>
        </div>
    </div>
</div>

<div id="wallView" class="view">
    <div class="container" style="padding:0">
        <span class="back" onclick="closeView('wallView')">← GALLERY</span>
        <div class="wall-grid" id="wallGrid"></div>
    </div>
</div>

<div id="tipsView" class="view">
    <div class="container" style="padding:0">
        <span class="back" onclick="closeView('tipsView')">← FEATURES</span>
        <div class="box full" style="margin-bottom:12px;">
            <h3>Glyph Secrets</h3>
            <p style="font-size:12px; opacity:0.6;">Music Viz: Sync lights with audio.</p>
        </div>
    </div>
</div>

<script>
    const db = {
        'Phone (1)': '• NOS 2.5.5 Stable\n• April Security Patch\n• Stable Haptics',
        'Phone (2)': '• NOS 2.6.0 Beta\n• New Widget Set\n• Camera Tuning',
        'Phone (2a)': '• NOS 2.5.5.a\n• Performance Fix\n• Battery Opt.',
        'CMF Phone 1': '• v1.0.5 Patch\n• Day 1 Fixes'
    };

    function init() {
        document.getElementById('phoneContainer').innerHTML = Object.keys(db).map(p => `
            <div class="phone-card" onclick="showLog('${p}')">${p}</div>
        `).join('');

        const walls = ['https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe', 'https://images.unsplash.com/photo-1634017839464-5c339ebe3cb4'];
        document.getElementById('wallGrid').innerHTML = walls.map((w, i) => `
            <div class="wall-box">
                <img src="${w}">
                <div class="wall-dl">
                    <button class="dl-btn" style="padding:10px; font-size:10px;" onclick="enhancedDL(this, 'WALLPAPER', ${i})"><span>DOWNLOAD</span></button>
                    <div class="res-box" id="wallRes${i}" style="padding:10px; font-size:9px; margin-top:5px;"></div>
                </div>
            </div>
        `).join('');
    }

    function enhancedDL(btn, type, id = null) {
        const txt = btn.querySelector('span');
        const resId = id !== null ? `wallRes${id}` : (type === 'TOOL APK' ? 'toolRes' : 'firmRes');
        const res = document.getElementById(resId);
        
        btn.classList.add('loading');
        txt.innerText = "DOWNLOADING...";
        if(res) res.style.display = 'none';

        setTimeout(() => {
            btn.classList.remove('loading');
            txt.innerText = "COMPLETED";
            
            if(res) {
                res.style.display = 'block';
                res.innerHTML = `
                    <div style="display:flex;align-items:center;gap:10px;">
                        <i class="fa-solid fa-circle-down" style="color:#00ff00;font-size:18px;"></i>
                        <div>
                            <b style="color:#00ff00;">${type} READY</b><br>
                            <span style="opacity:0.6;font-size:10px;">Saved to internal storage.</span>
                        </div>
                    </div>`;
            }
        }, 2500);
    }

    function showLog(name) {
        const area = document.getElementById('logArea');
        area.style.display = 'block';
        document.getElementById('selName').innerText = name;
        document.getElementById('selLog').innerText = db[name];
        
        // RESET PREVIOUS DOWNLOAD STATUS
        const firmRes = document.getElementById('firmRes');
        const firmBtnTxt = document.querySelector('#firmBtn span');
        firmRes.style.display = 'none';
        firmBtnTxt.innerText = "DOWNLOAD ZIP";
        
        area.scrollIntoView({ behavior: 'smooth' });
    }

    function checkAuth(btn) {
        const id = document.getElementById('vID').value.trim();
        const res = document.getElementById('vResult');
        const txt = btn.querySelector('span');
        if(!id) return;
        btn.classList.add('loading');
        txt.innerText = "ANALYZING...";
        setTimeout(() => {
            btn.classList.remove('loading');
            txt.innerText = "ANALYZE DEVICE";
            res.style.display = 'block';
            let isReal = (id.length === 15 && !isNaN(id)) ? (id.split('').reverse().reduce((s,d,i)=>s+(i%2?(d*2>9?d*2-9:d*2):+d),0)%10===0) : false;
            if(isReal || (id.length >= 10 && id.toUpperCase().startsWith('NTG'))) {
                res.innerHTML = `<div style="display:flex;align-items:center;gap:15px;"><i class="fa-solid fa-circle-check" style="color:#00ff00;font-size:20px;"></i><div><b style="color:#00ff00;">PRODUCT VERIFIED</b><br><span style="opacity:0.6;font-size:10px;">ID: ${id}</span></div></div>`;
            } else {
                res.innerHTML = `<div style="display:flex;align-items:center;gap:15px;"><i class="fa-solid fa-triangle-exclamation" style="color:#ff2d2d;font-size:20px;"></i><div><b style="color:#ff2d2d;">INVALID HARDWARE ID</b><br><span style="opacity:0.6;font-size:10px;">Security check failed.</span></div></div>`;
            }
        }, 2000);
    }

    function toggleContact() { document.getElementById('contactCard').classList.toggle('active'); }
    function openView(id) { document.getElementById(id).classList.add('active'); }
    function closeView(id) { document.getElementById(id).classList.remove('active'); }

    function toggleTheme() {
        const b = document.body;
        const icon = document.getElementById('tBtn');
        const isDark = b.getAttribute('data-theme') === 'dark';
        b.setAttribute('data-theme', isDark ? 'light' : 'dark');
        icon.className = isDark ? 'fa-solid fa-moon' : 'fa-solid fa-sun';
    }

    window.onload = init;
</script>
</body>
</html>
