<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8"/>
  <meta name="viewport" content="width=device-width,initial-scale=1.0"/>
  <title>تاتا دايت</title>
  <style>
    *{margin:0;padding:0;box-sizing:border-box}
    body{font-family:'Segoe UI',Tahoma,sans-serif;background:#f8fafc;direction:rtl}
    #auth-page{min-height:100vh;display:flex;align-items:center;justify-content:center;background:linear-gradient(135deg,#f0fdf4 0%,#dcfce7 40%,#f8fafc 100%);position:relative;overflow:hidden}
    #auth-page::before{content:'';position:absolute;top:-80px;right:-80px;width:320px;height:320px;border-radius:50%;background:radial-gradient(circle,#86efac55,transparent);filter:blur(40px)}
    #auth-page::after{content:'';position:absolute;bottom:-60px;left:-60px;width:280px;height:280px;border-radius:50%;background:radial-gradient(circle,#bbf7d055,transparent);filter:blur(40px)}
    .auth-card{background:white;border-radius:28px;padding:30px 28px;box-shadow:0 20px 60px rgba(0,0,0,0.08),0 4px 20px rgba(74,222,128,0.15);width:100%;max-width:460px;position:relative;z-index:1;animation:fadeUp 0.4s cubic-bezier(0.34,1.56,0.64,1);max-height:95vh;overflow-y:auto}
    @keyframes fadeUp{from{opacity:0;transform:translateY(30px) scale(0.96)}to{opacity:1;transform:translateY(0) scale(1)}}
    .logo-box{width:66px;height:66px;border-radius:18px;margin:0 auto 10px;background:linear-gradient(135deg,#16a34a,#4ade80);display:flex;align-items:center;justify-content:center;font-size:30px;box-shadow:0 8px 24px rgba(22,163,74,0.3)}
    .auth-title{font-size:24px;font-weight:800;color:#15803d;text-align:center}
    .auth-sub{color:#6b7280;font-size:13px;text-align:center;margin-top:4px;margin-bottom:18px}
    .tab-wrapper{display:flex;background:#f3f4f6;border-radius:12px;padding:4px;margin-bottom:16px}
    .tab-btn{flex:1;padding:9px;border-radius:9px;border:none;cursor:pointer;font-weight:600;font-size:14px;transition:all 0.25s;background:transparent;color:#9ca3af;font-family:inherit}
    .tab-btn.active{background:white;color:#16a34a;box-shadow:0 2px 8px rgba(0,0,0,0.1)}
    .form-group{display:flex;flex-direction:column;gap:9px}
    input[type="text"],input[type="email"],input[type="password"],input[type="tel"],input[type="number"],textarea,select{padding:10px 13px;border-radius:10px;border:1.5px solid #e5e7eb;font-size:13px;outline:none;font-family:inherit;text-align:right;transition:border-color 0.2s;background:#fafafa;width:100%}
    input:focus,textarea:focus,select:focus{border-color:#16a34a;background:white}
    .row-3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:9px}
    .field-wrap{display:flex;flex-direction:column}
    .field-label{font-size:11px;color:#6b7280;font-weight:600;margin-bottom:3px}
    .btn-primary{background:linear-gradient(135deg,#16a34a,#22c55e);color:white;border:none;border-radius:11px;padding:12px 18px;cursor:pointer;font-weight:700;font-size:14px;font-family:inherit;width:100%;box-shadow:0 4px 14px rgba(22,163,74,0.35);transition:transform 0.15s}
    .btn-primary:hover{transform:scale(1.02)}
    .auth-switch{text-align:center;margin-top:10px;font-size:13px;color:#9ca3af}
    .auth-switch span{color:#16a34a;cursor:pointer;font-weight:600}
    .pass-wrap{position:relative}
    .pass-wrap input{padding-left:38px}
    .toggle-pass{position:absolute;left:11px;top:50%;transform:translateY(-50%);cursor:pointer;font-size:14px;user-select:none}
    .strength-wrap{margin-top:2px}
    .strength-bar{height:4px;border-radius:4px;background:#e5e7eb;overflow:hidden}
    .strength-fill{height:100%;border-radius:4px;transition:all 0.3s}
    .strength-text{font-size:11px;margin-top:3px;font-weight:600}
    .alert-box{padding:8px 12px;border-radius:10px;font-size:13px;margin-bottom:8px;display:none;text-align:center}
    .alert-error{background:#fee2e2;color:#ef4444}
    .alert-success{background:#dcfce7;color:#16a34a}
    .lock-box{text-align:center;padding:14px 0}
    .lock-timer{font-size:36px;font-weight:900;color:#ef4444;letter-spacing:2px;margin:5px 0}
    .attempts-left{font-size:12px;color:#f59e0b;margin-top:4px;font-weight:600}
    .section-divider{font-size:11px;color:#9ca3af;font-weight:700;letter-spacing:0.5px;margin:4px 0 2px;padding-bottom:4px;border-bottom:1px solid #f3f4f6}
    /* male warning */
    .male-warning{background:#fff7ed;border:1.5px solid #fed7aa;border-radius:10px;padding:12px 14px;display:none;text-align:center}
    .male-warning p{color:#c2410c;font-weight:700;font-size:13px;margin-bottom:4px}
    .male-warning small{color:#9a3412;font-size:12px}

    /* DASHBOARD */
    #dashboard-page{display:none;min-height:100vh}
    header{background:white;border-bottom:1px solid #e5e7eb;padding:0 20px;height:62px;display:flex;align-items:center;justify-content:space-between;position:sticky;top:0;z-index:50;box-shadow:0 2px 12px rgba(0,0,0,0.05)}
    .header-logo{display:flex;align-items:center;gap:10px}
    .header-logo-icon{width:38px;height:38px;border-radius:10px;background:linear-gradient(135deg,#16a34a,#4ade80);display:flex;align-items:center;justify-content:center;font-size:18px;box-shadow:0 4px 12px rgba(22,163,74,0.25)}
    .header-logo h1{font-size:18px;font-weight:800;color:#15803d}
    .header-logo p{font-size:10px;color:#9ca3af}
    .header-actions{display:flex;align-items:center;gap:9px}
    #admin-badge{background:#dcfce7;color:#16a34a;padding:3px 9px;border-radius:20px;font-size:11px;font-weight:700;display:none}
    #user-greeting{font-size:13px;color:#374151;font-weight:600}
    .btn-logout{background:#f3f4f6;border:none;border-radius:9px;padding:6px 13px;cursor:pointer;color:#6b7280;font-weight:600;font-size:12px;font-family:inherit}
    .hero{background:linear-gradient(135deg,#15803d 0%,#16a34a 50%,#22c55e 100%);padding:38px 20px;text-align:center;position:relative;overflow:hidden}
    .hero-circles{position:absolute;inset:0;opacity:0.1;pointer-events:none}
    .hero-circles div{position:absolute;border-radius:50%;border:1px solid white;top:50%;left:50%;transform:translate(-50%,-50%)}
    .hero h2{color:white;font-size:26px;font-weight:800;margin-bottom:5px;position:relative}
    .hero p{color:#bbf7d0;font-size:14px;position:relative}
    .cards-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(250px,1fr));gap:18px;padding:20px;max-width:1200px;margin:0 auto}
    .section-card{background:white;border-radius:17px;padding:18px;box-shadow:0 4px 20px rgba(0,0,0,0.06);border:1px solid #f3f4f6;transition:transform 0.2s,box-shadow 0.2s}
    .section-card:hover{transform:translateY(-3px);box-shadow:0 10px 28px rgba(0,0,0,0.09)}
    .card-header{display:flex;align-items:center;gap:9px;margin-bottom:12px}
    .card-icon{width:40px;height:40px;border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:19px;flex-shrink:0}
    .card-title{font-size:15px;font-weight:800;color:#111827}
    .admin-badge-card{margin-right:auto;background:#fef9c3;color:#854d0e;font-size:10px;padding:2px 6px;border-radius:6px;font-weight:700;display:none}
    .pkg-row{background:#f0fdf4;border-radius:8px;padding:9px 11px;display:flex;justify-content:space-between;align-items:center;margin-bottom:7px}
    .pkg-name{font-weight:700;color:#15803d;font-size:12px}
    .pkg-price{background:#16a34a;color:white;border-radius:6px;padding:2px 8px;font-size:10px;font-weight:700}
    .lesson-row{background:#f0f9ff;border-radius:8px;padding:9px 11px;display:flex;align-items:center;gap:8px;margin-bottom:7px}
    .lesson-title{font-weight:700;color:#0e7490;font-size:11px}
    .lesson-dur{color:#6b7280;font-size:10px;margin-top:1px}
    .result-row{background:#fffbeb;border-radius:8px;padding:9px 11px;display:flex;gap:8px;margin-bottom:7px}
    .result-avatar{width:32px;height:32px;border-radius:50%;background:linear-gradient(135deg,#f59e0b,#fbbf24);display:flex;align-items:center;justify-content:center;color:white;font-weight:800;font-size:13px;flex-shrink:0;overflow:hidden}
    .result-avatar img{width:100%;height:100%;object-fit:cover;border-radius:50%}
    .result-name{font-weight:700;color:#92400e;font-size:11px}
    .result-lost{color:#16a34a}
    .result-review{color:#6b7280;font-size:10px;margin-top:2px}
    .btn-card{width:100%;padding:8px;border:none;border-radius:8px;cursor:pointer;font-weight:700;font-size:12px;color:white;font-family:inherit;margin-top:4px}
    footer{text-align:center;padding:18px 20px;border-top:1px solid #e5e7eb;color:#9ca3af;font-size:12px;background:white;display:flex;align-items:center;justify-content:center;position:relative;overflow:visible}
    .btn-admin{position:absolute;left:18px;top:50%;transform:translateY(-50%);background:#16a34a;border:none;color:white;font-size:12px;cursor:pointer;padding:7px 14px;border-radius:8px;font-weight:700;font-family:inherit;box-shadow:0 3px 10px rgba(22,163,74,0.3);transition:all 0.2s}
    .btn-admin:hover{background:#15803d}

    /* MODALS */
    .modal-overlay{position:fixed;inset:0;background:rgba(0,0,0,0.5);display:none;align-items:center;justify-content:center;z-index:1000;padding:14px}
    .modal-overlay.open{display:flex}
    .modal-box{background:white;border-radius:20px;padding:26px;width:100%;max-width:480px;max-height:90vh;overflow-y:auto;position:relative;box-shadow:0 25px 60px rgba(0,0,0,0.2);animation:fadeUp 0.3s ease}
    .modal-box.wide{max-width:720px}
    .modal-close{position:absolute;top:13px;left:13px;background:#f3f4f6;border:none;width:29px;height:29px;border-radius:50%;cursor:pointer;font-size:16px;line-height:1}
    .modal-title{font-size:19px;font-weight:800;color:#111827;margin-bottom:16px}
    .admin-form{background:#f0fdf4;border-radius:13px;padding:16px;margin-top:16px}
    .admin-form h4{color:#15803d;font-size:13px;margin-bottom:11px;font-weight:700}
    .admin-form input,.admin-form textarea,.admin-form select{margin-bottom:8px}
    .btn-add{background:linear-gradient(135deg,#16a34a,#22c55e);color:white;border:none;border-radius:10px;padding:10px 16px;cursor:pointer;font-weight:700;font-family:inherit;font-size:13px;width:100%;margin-top:6px;box-shadow:0 3px 10px rgba(22,163,74,0.3)}
    .btn-delete{background:#fee2e2;border:none;color:#ef4444;border-radius:7px;width:27px;height:27px;cursor:pointer;font-weight:700;font-size:13px;flex-shrink:0}
    .pkg-card{border:2px solid #dcfce7;border-radius:13px;padding:16px;margin-bottom:10px}
    .pkg-card-header{display:flex;justify-content:space-between;align-items:center;margin-bottom:9px}
    .pkg-card h3{color:#15803d;font-size:15px;font-weight:800}
    .pkg-features li{color:#4b5563;font-size:12px;line-height:2}

    /* LESSON CARD with media */
    .lesson-card{background:#f0f9ff;border-radius:12px;padding:13px 15px;margin-bottom:9px}
    .lesson-card-top{display:flex;gap:11px;align-items:flex-start}
    .lesson-icon{width:42px;height:42px;border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:19px;flex-shrink:0}
    .lesson-card h3{font-weight:700;color:#0e7490;font-size:13px}
    .lesson-card p{color:#6b7280;font-size:11px;margin-top:2px}
    .lesson-dur-tag{display:inline-block;margin-top:4px;background:#e0f2fe;color:#0369a1;font-size:10px;padding:2px 8px;border-radius:6px;font-weight:700}
    .lesson-media{margin-top:10px;border-radius:10px;overflow:hidden;background:#000}
    .lesson-media video{width:100%;max-height:220px;display:block}
    .lesson-media audio{width:100%;margin-top:4px}

    /* RESULT CARD with stars + image */
    .result-card{background:#fffbeb;border-radius:13px;padding:14px;display:flex;gap:11px;align-items:flex-start;margin-bottom:9px}
    .result-card-avatar{width:52px;height:52px;border-radius:50%;background:linear-gradient(135deg,#f59e0b,#fbbf24);display:flex;align-items:center;justify-content:center;color:white;font-weight:800;font-size:20px;flex-shrink:0;overflow:hidden}
    .result-card-avatar img{width:100%;height:100%;object-fit:cover;border-radius:50%}
    .result-badge{background:#dcfce7;color:#16a34a;font-size:10px;padding:2px 8px;border-radius:8px;font-weight:700}
    .result-card p{color:#6b7280;font-size:12px;line-height:1.6;margin-top:5px}
    .stars-display{color:#f59e0b;font-size:15px;letter-spacing:1px}
    .stars-row{display:flex;gap:4px;margin:8px 0 4px}
    .star-btn{background:none;border:none;cursor:pointer;font-size:22px;transition:transform 0.1s;line-height:1}
    .star-btn:hover{transform:scale(1.2)}

    /* USER REVIEW FORM */
    .user-review-form{background:#fffbeb;border-radius:13px;padding:16px;margin-top:16px;border:1.5px dashed #fde68a}
    .user-review-form h4{color:#92400e;font-size:13px;margin-bottom:11px;font-weight:700}
    .img-preview{width:60px;height:60px;border-radius:50%;object-fit:cover;border:2px solid #fde68a;margin-top:6px;display:none}

    /* CREDENTIALS CARD */
    .cred-card{background:#f5f3ff;border-radius:13px;padding:16px;margin-bottom:10px;border:1px solid #e9d5ff}
    .cred-card h3{color:#5b21b6;font-size:15px;font-weight:800;margin-bottom:4px}
    .cred-card p{color:#6b7280;font-size:12px;line-height:1.6}
    .cred-year{font-size:11px;color:#7c3aed;font-weight:700;margin-top:4px}
    .cred-preview{display:flex;flex-direction:column;gap:8px}
    .cred-row{background:#f5f3ff;border-radius:8px;padding:9px 11px;border:1px solid #e9d5ff}
    .cred-row-title{font-weight:700;color:#5b21b6;font-size:12px}
    .cred-row-sub{color:#6b7280;font-size:10px;margin-top:2px}

    /* WA */
    .wa-btn{display:block;background:#25d366;color:white;border-radius:12px;padding:13px;text-decoration:none;font-weight:800;font-size:16px;margin-bottom:12px;text-align:center}
    .btn-edit-wa{background:#fef9c3;color:#854d0e;border:none;border-radius:8px;padding:6px 13px;cursor:pointer;font-weight:700;font-size:12px;font-family:inherit;width:100%}
    .wa-card{text-align:center;padding-top:5px}
    .wa-card p{color:#6b7280;font-size:12px;line-height:1.6;margin-bottom:9px}

    /* ADMIN TABLE */
    .user-detail-row{padding:13px 15px;border-bottom:1px solid #f3f4f6}
    .user-detail-row:last-child{border-bottom:none}
    .user-info-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(110px,1fr));gap:7px;margin-top:8px}
    .user-info-chip{background:#f8fafc;border-radius:8px;padding:6px 9px;font-size:11px;border:1px solid #f1f5f9}
    .user-info-chip .lbl{color:#9ca3af;font-weight:600;display:block;margin-bottom:2px}
    .user-info-chip .val{color:#111827;font-weight:700}
    .stat-box{background:#f0fdf4;border-radius:11px;padding:13px;text-align:center;border:1px solid #bbf7d0}
    .stat-num{font-size:24px;font-weight:900}
    .stat-lbl{font-size:10px;color:#6b7280;margin-top:2px}

    #save-toast{position:fixed;bottom:20px;right:20px;background:#16a34a;color:white;padding:11px 18px;border-radius:11px;font-weight:700;font-size:13px;z-index:9999;display:none;box-shadow:0 6px 20px rgba(22,163,74,0.4);animation:slideIn 0.3s ease}
    @keyframes slideIn{from{transform:translateY(20px);opacity:0}to{transform:translateY(0);opacity:1}}

    .emoji-opt{background:#f3f4f6;border:2px solid transparent;border-radius:8px;width:36px;height:36px;font-size:18px;cursor:pointer;transition:all 0.15s;line-height:1}
    .emoji-opt:hover,.emoji-opt.active{border-color:#16a34a;background:#dcfce7;transform:scale(1.15)}
    .color-swatch{color:white;border:none;border-radius:9px;padding:7px 14px;cursor:pointer;font-weight:700;font-size:11px;font-family:inherit;transition:transform 0.15s;box-shadow:0 2px 8px rgba(0,0,0,0.15)}
    .color-swatch:hover{transform:scale(1.07)}
    .file-upload-label{display:flex;align-items:center;gap:8px;background:#f0f9ff;border:1.5px dashed #7dd3fc;border-radius:10px;padding:10px 13px;cursor:pointer;font-size:12px;color:#0369a1;font-weight:600;transition:background 0.2s}
    .file-upload-label:hover{background:#e0f2fe}
    .file-upload-label input{display:none}
    .tabs-mini{display:flex;gap:6px;margin-bottom:12px}
    .tab-mini{padding:5px 12px;border-radius:7px;border:1.5px solid #e5e7eb;background:white;cursor:pointer;font-size:12px;font-weight:600;color:#6b7280;font-family:inherit;transition:all 0.2s}
    .tab-mini.active{background:#16a34a;color:white;border-color:#16a34a}
  </style>

  <!-- ══ Firebase SDK ══ -->
  <script type="module">
    import{initializeApp}from"https://www.gstatic.com/firebasejs/10.12.2/firebase-app.js";
    import{getDatabase,ref,set,get,push,onValue,update,remove}from"https://www.gstatic.com/firebasejs/10.12.2/firebase-database.js";
    // ════════════════════════════════════════════
    // ضع هنا الـ Config اللي هتاخده من Firebase
    // ════════════════════════════════════════════
    const firebaseConfig={
      apiKey:"PASTE_YOUR_API_KEY",
      authDomain:"PASTE_YOUR_PROJECT.firebaseapp.com",
      databaseURL:"https://PASTE_YOUR_PROJECT-default-rtdb.firebaseio.com",
      projectId:"PASTE_YOUR_PROJECT",
      storageBucket:"PASTE_YOUR_PROJECT.appspot.com",
      messagingSenderId:"PASTE_YOUR_SENDER_ID",
      appId:"PASTE_YOUR_APP_ID"
    };
    const app=initializeApp(firebaseConfig);
    const db=getDatabase(app);
    window._FB={db,ref,set,get,push,onValue,update,remove};
    window._FB_READY=true;
    document.dispatchEvent(new Event("fb-ready"));
  </script>
</head>
<body>

<div id="save-toast">✅ تم الحفظ</div>
<div id="offline-banner" style="display:none;position:fixed;top:0;left:0;right:0;background:#f59e0b;color:white;text-align:center;padding:9px;font-size:12px;font-weight:700;z-index:9997;letter-spacing:.5px">⚡ وضع بدون إنترنت — البيانات محفوظة محلياً فقط</div>
<div id="sync-dot" style="display:none;position:fixed;bottom:20px;left:20px;background:#16a34a;color:white;border-radius:20px;padding:6px 14px;font-size:12px;font-weight:700;z-index:9998;box-shadow:0 4px 14px rgba(22,163,74,.4);align-items:center;gap:6px"><span style="animation:spin 1s linear infinite;display:inline-block">🔄</span> جارى المزامنة...</div>
<style>@keyframes spin{to{transform:rotate(360deg)}}</style>

<!-- ═══════════ AUTH ═══════════ -->
<div id="auth-page">
  <div class="auth-card">
    <div style="text-align:center">
      <div class="logo-box">🌿</div>
      <h1 class="auth-title">تاتا دايت</h1>
      <p class="auth-sub">رحلتك نحو جسم أكثر صحة تبدأ هنا</p>
    </div>
    <div class="tab-wrapper">
      <button class="tab-btn active" onclick="switchTab('login')" id="tab-login">تسجيل دخول</button>
      <button class="tab-btn" onclick="switchTab('register')" id="tab-register">إنشاء حساب</button>
    </div>
    <div class="alert-box alert-error" id="auth-error"></div>
    <div class="alert-box alert-success" id="auth-success"></div>
    <div id="lock-screen" style="display:none" class="lock-box">
      <div style="font-size:46px">🔒</div>
      <p style="font-weight:800;font-size:15px;color:#111827;margin:7px 0 3px">تم قفل الحساب مؤقتاً</p>
      <div class="lock-timer" id="lock-countdown">00:00</div>
      <p style="color:#6b7280;font-size:12px;line-height:1.6">تم رصد محاولات متعددة.<br>انتظر حتى انتهاء العداد.</p>
    </div>
    <div class="form-group" id="login-form">
      <input type="email" id="login-email" placeholder="البريد الإلكتروني" autocomplete="email"/>
      <div class="pass-wrap">
        <input type="password" id="login-pass" placeholder="كلمة المرور" autocomplete="current-password" onkeydown="if(event.key==='Enter')doLogin()"/>
        <span class="toggle-pass" onclick="togglePass('login-pass',this)">👁️</span>
      </div>
      <p class="attempts-left" id="attempts-left" style="display:none"></p>
      <button class="btn-primary" onclick="doLogin()">دخول 🚀</button>
    </div>
    <div class="form-group" id="register-form" style="display:none">
      <div class="section-divider">📋 البيانات الأساسية</div>
      <input type="text" id="reg-name" placeholder="الاسم الكامل"/>
      <input type="email" id="reg-email" placeholder="البريد الإلكتروني" autocomplete="email"/>
      <input type="tel" id="reg-phone" placeholder="رقم التليفون (مثال: 01012345678)"/>
      <div class="section-divider">🏥 البيانات الصحية</div>
      <div class="row-3">
        <div class="field-wrap"><span class="field-label">السن (سنة)</span><input type="number" id="reg-age" placeholder="25" min="10" max="100"/></div>
        <div class="field-wrap"><span class="field-label">الوزن (كجم)</span><input type="number" id="reg-weight" placeholder="70" min="20" max="300"/></div>
        <div class="field-wrap"><span class="field-label">الطول (سم)</span><input type="number" id="reg-height" placeholder="165" min="100" max="250"/></div>
      </div>
      <div class="field-wrap">
        <span class="field-label">النوع</span>
        <select id="reg-gender" onchange="checkMaleWarning(this.value)">
          <option value="">-- اختر النوع --</option>
          <option value="ذكر">👨 ذكر</option>
          <option value="أنثى">👩 أنثى</option>
        </select>
      </div>
      <!-- Male Warning -->
      <div class="male-warning" id="male-warning">
        <p>😔 للأسف حالياً مفيش دكتورة تغذية رجالي</p>
        <small>الخدمة متاحة للسيدات فقط في الوقت الحالي.<br>نتمنى نوسّع قريباً إن شاء الله! 🌿</small>
      </div>
      <div class="section-divider">🔐 كلمة المرور</div>
      <div class="pass-wrap">
        <input type="password" id="reg-pass" placeholder="كلمة المرور (8 أحرف على الأقل)" oninput="checkStrength(this.value)" autocomplete="new-password"/>
        <span class="toggle-pass" onclick="togglePass('reg-pass',this)">👁️</span>
      </div>
      <div class="strength-wrap" id="strength-wrap" style="display:none">
        <div class="strength-bar"><div class="strength-fill" id="strength-fill"></div></div>
        <p class="strength-text" id="strength-text"></p>
      </div>
      <div class="pass-wrap">
        <input type="password" id="reg-pass2" placeholder="تأكيد كلمة المرور" autocomplete="new-password" onkeydown="if(event.key==='Enter')doRegister()"/>
        <span class="toggle-pass" onclick="togglePass('reg-pass2',this)">👁️</span>
      </div>
      <button class="btn-primary" onclick="doRegister()">إنشاء الحساب ✨</button>
    </div>
    <p class="auth-switch" id="auth-switch">ليس لديك حساب؟ <span onclick="switchTab('register')">سجّل الآن</span></p>
    <p class="auth-switch" id="auth-switch2" style="display:none">لديك حساب؟ <span onclick="switchTab('login')">سجّل دخولك</span></p>
  </div>
</div>

<!-- ═══════════ DASHBOARD ═══════════ -->
<div id="dashboard-page">
  <header>
    <div class="header-logo">
      <div class="header-logo-icon">🌿</div>
      <div><h1>تاتا دايت</h1><p>نظام غذائي صحي متكامل</p></div>
    </div>
    <div class="header-actions">
      <span id="user-greeting"></span>
      <span id="admin-badge">⚙️ مود الإدارة</span>
      <button id="btn-exit-admin" onclick="exitAdminMode()" style="display:none;background:#fee2e2;border:none;border-radius:9px;padding:6px 13px;cursor:pointer;color:#ef4444;font-weight:700;font-size:12px;font-family:inherit">🚪 خروج من الإدارة</button>
      <button class="btn-logout" onclick="doLogout()">خروج</button>
    </div>
  </header>
  <div class="hero">
    <div class="hero-circles">
      <div style="width:80px;height:80px"></div><div style="width:160px;height:160px"></div>
      <div style="width:240px;height:240px"></div><div style="width:320px;height:320px"></div>
    </div>
    <h2 id="hero-welcome">أهلاً بك في تاتا دايت 🌱</h2>
    <p>اختر ما تريد واستمتع برحلتك الصحية</p>
    <button id="hero-admin-btn" onclick="if(isAdmin)openModal('admin-dashboard-modal');else openModal('admin-modal')" style="margin-top:16px;background:rgba(255,255,255,0.18);backdrop-filter:blur(6px);border:1.5px solid rgba(255,255,255,0.4);color:white;border-radius:20px;padding:8px 20px;cursor:pointer;font-weight:700;font-size:13px;font-family:inherit;transition:all 0.2s" onmouseenter="this.style.background='rgba(255,255,255,0.3)'" onmouseleave="this.style.background='rgba(255,255,255,0.18)'">⚙️ لوحة الإدارة</button>
  </div>
  <div class="cards-grid">
    <!-- Packages -->
    <div class="section-card">
      <div class="card-header">
        <div class="card-icon" style="background:#16a34a18">💎</div>
        <span class="card-title">أسعار الاشتراكات</span>
        <span class="admin-badge-card admin-visible">✏️ تحرير</span>
      </div>
      <div id="pkg-preview"></div>
      <button class="btn-card" style="background:#16a34a" onclick="openModal('packages-modal')">عرض كل الباقات ←</button>
    </div>
    <!-- Lessons -->
    <div class="section-card">
      <div class="card-header">
        <div class="card-icon" style="background:#0891b218">🎓</div>
        <span class="card-title">الدروس والبودكاست</span>
        <span class="admin-badge-card admin-visible">✏️ تحرير</span>
      </div>
      <div id="lesson-preview"></div>
      <button class="btn-card" style="background:#0891b2" onclick="openModal('lessons-modal')">المكتبة الكاملة ←</button>
    </div>
    <!-- Credentials -->
    <div class="section-card">
      <div class="card-header">
        <div class="card-icon" style="background:#7c3aed18">🎓</div>
        <span class="card-title">شهاداتي وخبراتي</span>
        <span class="admin-badge-card admin-visible">✏️ تحرير</span>
      </div>
      <div id="cred-preview"></div>
      <button class="btn-card" style="background:#7c3aed" onclick="openModal('credentials-modal')">عرض الكل ←</button>
    </div>
    <!-- Contact -->
    <div class="section-card">
      <div class="card-header">
        <div class="card-icon" style="background:#059b4518">💬</div>
        <span class="card-title">تواصل مع الدكتورة</span>
        <span class="admin-badge-card admin-visible">✏️ تحرير</span>
      </div>
      <div class="wa-card">
        <p>تواصل معنا مباشرة واحصل على استشارة غذائية متخصصة</p>
        <a id="wa-link-card" href="#" target="_blank" class="wa-btn">📱 واتساب الدكتورة</a>
        <div id="wa-num-display-card" style="background:#f0fdf4;border-radius:9px;padding:8px 12px;text-align:center;font-size:13px;color:#15803d;font-weight:700;margin-bottom:8px;border:1px solid #bbf7d0"></div>
        <button class="btn-edit-wa admin-visible" onclick="openModal('contact-modal')">✏️ تعديل رقم الواتساب</button>
      </div>
    </div>
    <!-- Results -->
    <div class="section-card" style="grid-column: span 1">
      <div class="card-header">
        <div class="card-icon" style="background:#d9770618">⭐</div>
        <span class="card-title">من قبلنا</span>
        <span class="admin-badge-card admin-visible">✏️ تحرير</span>
      </div>
      <div id="result-preview"></div>
      <button class="btn-card" style="background:#d97706" onclick="openModal('results-modal')">كل النتائج والآراء ←</button>
    </div>
    <!-- Social Media -->
    <div class="section-card">
      <div class="card-header">
        <div class="card-icon" style="background:#0ea5e918">🌐</div>
        <span class="card-title">حساباتي</span>
        <span class="admin-badge-card admin-visible">✏️ تحرير</span>
      </div>
      <div id="social-preview"></div>
      <button class="btn-card" style="background:#0ea5e9" onclick="openModal('social-modal')">تابعينا ←</button>
    </div>
    <!-- My Subscription -->
    <div class="section-card" id="my-sub-card">
      <div class="card-header">
        <div class="card-icon" style="background:#f59e0b18">👑</div>
        <span class="card-title">اشتراكي</span>
      </div>
      <div id="my-sub-preview"></div>
      <button class="btn-card" style="background:#f59e0b" onclick="openModal('packages-modal')">ترقية الاشتراك ←</button>
    </div>
    <!-- Inner Chat -->
    <div class="section-card">
      <div class="card-header">
        <div class="card-icon" style="background:#10b98118">💬</div>
        <span class="card-title">المحادثة المباشرة</span>
      </div>
      <p style="font-size:12px;color:#6b7280;margin-bottom:10px">تواصل مع الدكتورة مباشرة من داخل الموقع</p>
      <div id="chat-unread-badge" style="display:none;background:#ef4444;color:white;border-radius:8px;padding:4px 10px;font-size:11px;font-weight:700;text-align:center;margin-bottom:8px"></div>
      <button class="btn-card" style="background:#10b981" onclick="openModal('chat-modal')">💬 افتح المحادثة</button>
    </div>
  </div>
  <footer>
    <p>© 2025 تاتا دايت — جميع الحقوق محفوظة 🌿</p>
    <!-- زرار Admin مخفي — ضغط طويل -->
    <div id="admin-footer-btn" style="position:absolute;left:18px;top:50%;transform:translateY(-50%);width:36px;height:36px;border-radius:50%;cursor:pointer;opacity:0.07;transition:opacity 0.3s;background:#16a34a;display:flex;align-items:center;justify-content:center;font-size:14px;color:white;user-select:none" onmouseenter="this.style.opacity='0.22'" onmouseleave="this.style.opacity='0.07'">⚙</div>
    <!-- hazim@ designer tag -->
    <div id="hazim-tag" onclick="toggleHazimCard()" style="position:absolute;right:14px;top:50%;transform:translateY(-50%);cursor:pointer;font-size:11px;color:#9ca3af;font-weight:600;transition:color 0.2s;user-select:none" onmouseenter="this.style.color='#6b7280'" onmouseleave="this.style.color='#9ca3af'">hazim@</div>
    <!-- hazim contact card -->
    <div id="hazim-card" style="display:none;position:absolute;right:10px;bottom:52px;background:white;border-radius:14px;padding:14px 18px;box-shadow:0 8px 30px rgba(0,0,0,0.13);border:1px solid #f1f5f9;text-align:center;min-width:180px;animation:fadeUp 0.25s ease;z-index:200">
      <div style="font-size:11px;color:#9ca3af;font-weight:600;margin-bottom:4px">مصمم الموقع</div>
      <div style="font-size:16px;font-weight:900;color:#111827;margin-bottom:8px">hazim</div>
      <div id="hazim-contact-num" style="font-size:15px;font-weight:800;color:#16a34a;letter-spacing:1px;background:#f0fdf4;border-radius:8px;padding:6px 10px;border:1px solid #bbf7d0">—</div>
      <div style="font-size:10px;color:#9ca3af;margin-top:6px">للتواصل مع المصمم</div>
    </div>
  </footer>
</div>

<!-- ═══════════ MODALS ═══════════ -->

<!-- Admin Login -->
<div class="modal-overlay" id="admin-modal">
  <div class="modal-box" style="max-width:400px;text-align:center">
    <button class="modal-close" onclick="closeModal('admin-modal')">×</button>
    <div style="font-size:42px;margin-bottom:9px">🔐</div>
    <h3 style="font-size:17px;font-weight:800;color:#111827;margin-bottom:5px">لوحة الإدارة</h3>
    <p style="color:#6b7280;font-size:12px;margin-bottom:14px">أدخل كلمة المرور للوصول</p>
    <input type="password" id="admin-pass-input" placeholder="كلمة المرور" onkeydown="if(event.key==='Enter')doAdminLogin()"/>
    <p style="color:#ef4444;font-size:12px;margin-top:5px;display:none" id="admin-error">كلمة المرور غير صحيحة!</p>
    <button class="btn-primary" style="margin-top:8px" onclick="doAdminLogin()">دخول</button>
  </div>
</div>

<!-- Admin Dashboard -->
<div class="modal-overlay" id="admin-dashboard-modal">
  <div class="modal-box wide">
    <button class="modal-close" onclick="closeModal('admin-dashboard-modal')">×</button>
    <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:16px">
      <h2 style="font-size:19px;font-weight:800;color:#111827;margin:0">⚙️ لوحة تحكم الإدارة</h2>
      <button onclick="closeModal('admin-dashboard-modal');openNotifPanel()" style="position:relative;background:#fefce8;border:1.5px solid #fde68a;color:#854d0e;border-radius:10px;padding:7px 13px;cursor:pointer;font-weight:700;font-size:13px;font-family:inherit;display:flex;align-items:center;gap:5px">
        🔔 الإشعارات
        <span id="notif-badge-dash" style="background:#ef4444;color:white;font-size:9px;font-weight:800;border-radius:50%;min-width:16px;height:16px;display:none;align-items:center;justify-content:center;padding:0 2px"></span>
      </button>
    </div>
    <div style="display:grid;grid-template-columns:repeat(4,1fr);gap:9px;margin-bottom:18px">
      <div class="stat-box"><div class="stat-num" style="color:#16a34a" id="stat-total">0</div><div class="stat-lbl">إجمالي الحسابات</div></div>
      <div class="stat-box" style="background:#eff6ff;border-color:#bfdbfe"><div class="stat-num" style="color:#2563eb" id="stat-today">0</div><div class="stat-lbl">انضموا اليوم</div></div>
      <div class="stat-box" style="background:#fdf4ff;border-color:#e9d5ff"><div class="stat-num" style="color:#7c3aed" id="stat-female">0</div><div class="stat-lbl">إناث</div></div>
      <div class="stat-box" style="background:#fffbeb;border-color:#fde68a"><div class="stat-num" style="color:#d97706" id="stat-male">0</div><div class="stat-lbl">ذكور</div></div>
    </div>
    <h4 style="font-weight:800;color:#111827;margin-bottom:9px;font-size:13px">📋 الحسابات المسجلة</h4>
    <div id="admin-users-list" style="max-height:400px;overflow-y:auto;border:1px solid #e5e7eb;border-radius:11px"></div>
    <div style="margin-top:11px;display:flex;gap:8px;justify-content:space-between;flex-wrap:wrap">
      <button onclick="clearAllUsers()" style="background:#fee2e2;border:none;color:#ef4444;border-radius:8px;padding:6px 13px;cursor:pointer;font-weight:700;font-family:inherit;font-size:12px">🗑️ حذف كل الحسابات</button>
      <button onclick="openBrandingEditor()" style="background:linear-gradient(135deg,#7c3aed,#a855f7);border:none;color:white;border-radius:8px;padding:6px 14px;cursor:pointer;font-weight:700;font-family:inherit;font-size:12px">🎨 تخصيص هوية الموقع</button>
    </div>
    <!-- Payment Settings -->
    <div style="margin-top:16px;background:#fffbeb;border-radius:13px;padding:14px;border:1.5px solid #fde68a">
      <div style="font-weight:700;font-size:13px;color:#92400e;margin-bottom:10px">💳 إعدادات الدفع</div>
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:8px">
        <div>
          <div style="font-size:11px;color:#6b7280;font-weight:600;margin-bottom:3px">اسم طريقة الدفع</div>
          <input type="text" id="pay-name-input" placeholder="فودافون كاش" style="font-size:12px"/>
        </div>
        <div>
          <div style="font-size:11px;color:#6b7280;font-weight:600;margin-bottom:3px">رقم الاستلام</div>
          <input type="text" id="pay-num-input" placeholder="01234567890" style="font-size:12px"/>
        </div>
      </div>
      <button onclick="savePaymentSettings()" style="background:linear-gradient(135deg,#d97706,#f59e0b);color:white;border:none;border-radius:8px;padding:7px 16px;cursor:pointer;font-weight:700;font-family:inherit;font-size:12px;width:100%">💾 حفظ إعدادات الدفع</button>
      <div id="current-pay-info" style="margin-top:8px;font-size:11px;color:#6b7280;text-align:center"></div>
    </div>
    <!-- Hazim Contact -->
    <div style="margin-top:12px;background:#f0f9ff;border-radius:13px;padding:14px;border:1.5px solid #bae6fd">
      <div style="font-weight:700;font-size:13px;color:#0369a1;margin-bottom:8px">👨‍💻 رقم تواصل المصمم (hazim@)</div>
      <input type="text" id="hazim-num-input" placeholder="01xxxxxxxxx" style="font-size:13px;margin-bottom:8px"/>
      <button onclick="saveHazimNum()" style="background:linear-gradient(135deg,#0891b2,#06b6d4);color:white;border:none;border-radius:8px;padding:7px 16px;cursor:pointer;font-weight:700;font-family:inherit;font-size:12px;width:100%">💾 حفظ الرقم</button>
    </div>
  </div>
</div>

<!-- Packages -->
<div class="modal-overlay" id="packages-modal">
  <div class="modal-box wide">
    <button class="modal-close" onclick="closeModal('packages-modal')">×</button>
    <h2 class="modal-title">💎 أسعار الاشتراكات</h2>
    <div id="pkg-list"></div>
    <div class="admin-form admin-visible" id="pkg-add-form">
      <h4>إضافة باقة جديدة</h4>
      <input type="text" id="new-pkg-name" placeholder="اسم الباقة"/>
      <input type="text" id="new-pkg-price" placeholder="السعر (مثال: 299 جنيه / شهر)"/>
      <input type="text" id="new-pkg-features" placeholder="المميزات (افصل بـ ،)"/>
      <button class="btn-add" onclick="addPackage()">+ إضافة الباقة</button>
    </div>
  </div>
</div>

<!-- Lessons — with real media upload -->
<div class="modal-overlay" id="lessons-modal">
  <div class="modal-box wide">
    <button class="modal-close" onclick="closeModal('lessons-modal')">×</button>
    <h2 class="modal-title">🎓 الدروس والبودكاست</h2>
    <div id="lesson-list"></div>
    <div class="admin-form admin-visible" id="lesson-add-form">
      <h4>رفع محتوى جديد</h4>
      <div class="tabs-mini">
        <button class="tab-mini active" onclick="setLessonTab('video',this)">🎬 فيديو</button>
        <button class="tab-mini" onclick="setLessonTab('podcast',this)">🎙️ بودكاست</button>
      </div>
      <input type="hidden" id="new-lesson-type" value="video"/>
      <input type="text" id="new-lesson-title" placeholder="عنوان المحتوى"/>
      <input type="text" id="new-lesson-desc" placeholder="الوصف"/>
      <input type="text" id="new-lesson-dur" placeholder="المدة (مثال: 30 دقيقة)"/>
      <div class="field-wrap" style="margin-bottom:4px">
        <span class="field-label">🔒 مستوى الوصول</span>
        <select id="new-lesson-access">
          <option value="free">🆓 مجاني — للجميع</option>
          <option value="basic">💚 أساسي فأكثر</option>
          <option value="premium">💜 مميز فأكثر</option>
          <option value="vip">👑 VIP فقط</option>
        </select>
      </div>
      <label class="file-upload-label" id="lesson-file-label">
        <span id="lesson-file-icon">🎬</span>
        <span id="lesson-file-text">اختر ملف فيديو (MP4, MOV...)</span>
        <input type="file" id="new-lesson-file" accept="video/*,audio/*" onchange="onLessonFileChange(this)"/>
      </label>
      <div style="text-align:center;font-size:11px;color:#6b7280;margin:6px 0 2px;font-weight:600">— أو أدخل رابط (YouTube / SoundCloud / أي رابط مباشر) —</div>
      <input type="text" id="new-lesson-url" placeholder="https://youtube.com/watch?v=... أو رابط مباشر للملف"/>
      <button class="btn-add" style="background:linear-gradient(135deg,#0891b2,#06b6d4)" onclick="addLesson()">+ إضافة المحتوى</button>
    </div>
  </div>
</div>

<!-- Credentials -->
<div class="modal-overlay" id="credentials-modal">
  <div class="modal-box wide">
    <button class="modal-close" onclick="closeModal('credentials-modal')">×</button>
    <h2 class="modal-title">🎓 شهاداتي وخبراتي</h2>
    <div id="cred-list"></div>
    <div class="admin-form admin-visible" id="cred-add-form" style="background:#f5f3ff">
      <h4 style="color:#5b21b6">إضافة شهادة أو خبرة</h4>
      <input type="text" id="new-cred-title" placeholder="اسم الشهادة أو المؤسسة (مثال: جامعة القاهرة)"/>
      <input type="text" id="new-cred-year" placeholder="السنة (مثال: 2018)"/>
      <textarea id="new-cred-desc" placeholder="وصف الشهادة أو الخبرة" style="height:65px;resize:vertical"></textarea>
      <button class="btn-add" style="background:linear-gradient(135deg,#7c3aed,#a855f7)" onclick="addCredential()">+ إضافة</button>
    </div>
  </div>
</div>

<!-- Notifications Modal -->
<div class="modal-overlay" id="notif-modal">
  <div class="modal-box" style="max-width:440px;padding:0;overflow:hidden">
    <button class="modal-close" onclick="closeModal('notif-modal')" style="top:14px;left:14px;z-index:2">×</button>
    <div id="notif-list" style="max-height:85vh;overflow-y:auto"></div>
  </div>
</div>

<!-- Branding Editor -->
<div class="modal-overlay" id="branding-modal">
  <div class="modal-box" style="max-width:480px">
    <button class="modal-close" onclick="closeModal('branding-modal')">×</button>
    <h2 class="modal-title">🎨 تخصيص هوية الموقع</h2>
    <!-- Logo image upload -->
    <div style="margin-bottom:16px">
      <div class="field-label" style="font-size:12px;margin-bottom:8px;color:#374151;font-weight:700">🖼️ صورة اللوجو (ارفع صورة من جهازك)</div>
      <div style="display:flex;align-items:center;gap:12px">
        <div id="logo-current-preview" style="width:60px;height:60px;border-radius:14px;background:linear-gradient(135deg,#16a34a,#4ade80);display:flex;align-items:center;justify-content:center;font-size:26px;flex-shrink:0;overflow:hidden;box-shadow:0 4px 12px rgba(0,0,0,0.12)">🌿</div>
        <div style="flex:1">
          <label class="file-upload-label" style="margin-bottom:6px">
            📤 اختر صورة (PNG, JPG, SVG)
            <input type="file" accept="image/*" onchange="uploadLogoImage(this)" style="display:none"/>
          </label>
          <button onclick="clearLogoImage()" style="background:#fee2e2;border:none;color:#ef4444;border-radius:7px;padding:5px 11px;cursor:pointer;font-size:11px;font-weight:700;font-family:inherit;width:100%">🗑️ حذف الصورة والرجوع للإيموجي</button>
        </div>
      </div>
    </div>
    <div style="height:1px;background:#e5e7eb;margin:4px 0 14px"></div>
    <!-- Logo emoji -->
    <div style="margin-bottom:14px">
      <div class="field-label" style="font-size:12px;margin-bottom:6px;color:#374151;font-weight:700">🌿 أو اختر إيموجي (لو مفيش صورة)</div>
      <div style="display:flex;gap:8px;flex-wrap:wrap;margin-bottom:8px" id="emoji-picker">
        <button class="emoji-opt" onclick="setBrandEmoji('🌿')">🌿</button>
        <button class="emoji-opt" onclick="setBrandEmoji('🥗')">🥗</button>
        <button class="emoji-opt" onclick="setBrandEmoji('🍃')">🍃</button>
        <button class="emoji-opt" onclick="setBrandEmoji('💚')">💚</button>
        <button class="emoji-opt" onclick="setBrandEmoji('🌱')">🌱</button>
        <button class="emoji-opt" onclick="setBrandEmoji('🥦')">🥦</button>
        <button class="emoji-opt" onclick="setBrandEmoji('🫐')">🫐</button>
        <button class="emoji-opt" onclick="setBrandEmoji('⚕️')">⚕️</button>
        <button class="emoji-opt" onclick="setBrandEmoji('🩺')">🩺</button>
        <button class="emoji-opt" onclick="setBrandEmoji('✨')">✨</button>
      </div>
      <div style="display:flex;gap:8px;align-items:center">
        <input type="text" id="brand-emoji-custom" placeholder="أو اكتب إيموجي تاني هنا" style="flex:1"/>
        <button onclick="setBrandEmoji(document.getElementById('brand-emoji-custom').value)" style="background:#16a34a;color:white;border:none;border-radius:9px;padding:9px 13px;cursor:pointer;font-weight:700;font-family:inherit;font-size:13px">تطبيق</button>
      </div>
    </div>
    <!-- Site name -->
    <div style="margin-bottom:14px">
      <div class="field-label" style="font-size:12px;margin-bottom:6px;color:#374151;font-weight:700">📝 اسم الموقع</div>
      <div style="display:flex;gap:8px">
        <input type="text" id="brand-name" placeholder="تاتا دايت" style="flex:1"/>
        <button onclick="saveBrandName()" style="background:#16a34a;color:white;border:none;border-radius:9px;padding:9px 13px;cursor:pointer;font-weight:700;font-family:inherit;font-size:13px">حفظ</button>
      </div>
    </div>
    <!-- Tagline -->
    <div style="margin-bottom:14px">
      <div class="field-label" style="font-size:12px;margin-bottom:6px;color:#374151;font-weight:700">💬 الشعار / السطر التعريفي</div>
      <div style="display:flex;gap:8px">
        <input type="text" id="brand-tagline" placeholder="نظام غذائي صحي متكامل" style="flex:1"/>
        <button onclick="saveBrandTagline()" style="background:#16a34a;color:white;border:none;border-radius:9px;padding:9px 13px;cursor:pointer;font-weight:700;font-family:inherit;font-size:13px">حفظ</button>
      </div>
    </div>
    <!-- Color -->
    <div style="margin-bottom:14px">
      <div class="field-label" style="font-size:12px;margin-bottom:6px;color:#374151;font-weight:700">🎨 لون الموقع الأساسي</div>
      <div style="display:flex;gap:8px;flex-wrap:wrap">
        <button class="color-swatch" onclick="setBrandColor('#16a34a','#22c55e')" style="background:linear-gradient(135deg,#16a34a,#22c55e)">أخضر</button>
        <button class="color-swatch" onclick="setBrandColor('#0891b2','#06b6d4')" style="background:linear-gradient(135deg,#0891b2,#06b6d4)">أزرق</button>
        <button class="color-swatch" onclick="setBrandColor('#7c3aed','#a855f7')" style="background:linear-gradient(135deg,#7c3aed,#a855f7)">بنفسجي</button>
        <button class="color-swatch" onclick="setBrandColor('#db2777','#ec4899')" style="background:linear-gradient(135deg,#db2777,#ec4899)">وردي</button>
        <button class="color-swatch" onclick="setBrandColor('#d97706','#f59e0b')" style="background:linear-gradient(135deg,#d97706,#f59e0b)">ذهبي</button>
        <button class="color-swatch" onclick="setBrandColor('#dc2626','#ef4444')" style="background:linear-gradient(135deg,#dc2626,#ef4444)">أحمر</button>
      </div>
    </div>
    <!-- Preview -->
    <div style="background:#f8fafc;border-radius:12px;padding:12px;border:1px solid #e5e7eb;text-align:center">
      <div id="brand-preview-icon" style="width:50px;height:50px;border-radius:14px;margin:0 auto 7px;display:flex;align-items:center;justify-content:center;font-size:24px;background:linear-gradient(135deg,#16a34a,#4ade80)">🌿</div>
      <div id="brand-preview-name" style="font-size:16px;font-weight:800;color:#15803d">تاتا دايت</div>
      <div id="brand-preview-tag" style="font-size:11px;color:#9ca3af;margin-top:3px">نظام غذائي صحي متكامل</div>
    </div>
  </div>
</div>

<!-- Contact -->
<div class="modal-overlay" id="contact-modal">
  <div class="modal-box" style="text-align:center">
    <button class="modal-close" onclick="closeModal('contact-modal')">×</button>
    <div style="font-size:50px;margin-bottom:11px">💬</div>
    <h2 class="modal-title" style="text-align:center">تواصل مع الدكتورة</h2>
    <p style="color:#6b7280;font-size:13px;line-height:1.7;margin-bottom:16px">هل تحتاج استشارة؟ تواصل معنا مباشرة عبر واتساب وسنرد عليك في أقرب وقت.</p>
    <a id="wa-link-modal" href="#" target="_blank" class="wa-btn">📱 ابدأ المحادثة الآن</a>
    <div id="wa-num-display-modal" style="background:#f0fdf4;border-radius:9px;padding:8px 12px;text-align:center;font-size:14px;color:#15803d;font-weight:800;margin-bottom:12px;border:1px solid #bbf7d0;letter-spacing:1px"></div>
    <div class="admin-visible">
      <div style="display:flex;gap:8px;margin-top:8px">
        <input type="text" id="new-wa-num" placeholder="رقم واتساب (مثال: 201234567890)" style="flex:1"/>
        <button class="btn-primary" style="width:auto;padding:10px 13px" onclick="saveWa()">حفظ</button>
      </div>
    </div>
  </div>
</div>

<!-- Results -->
<div class="modal-overlay" id="results-modal">
  <div class="modal-box wide">
    <button class="modal-close" onclick="closeModal('results-modal')">×</button>
    <h2 class="modal-title">⭐ من قبلنا — نتائج وآراء</h2>
    <div id="result-list"></div>
    <!-- Admin add -->
    <div class="admin-form admin-visible" id="result-add-form" style="background:#fffbeb">
      <h4 style="color:#92400e">إضافة نتيجة (الأدمن)</h4>
      <input type="text" id="new-result-name" placeholder="اسم العميل"/>
      <input type="text" id="new-result-lost" placeholder="الوزن المفقود (مثال: 10 كيلو في شهرين)"/>
      <textarea id="new-result-review" placeholder="رأي العميل" style="height:60px;resize:vertical"></textarea>
      <button class="btn-add" style="background:linear-gradient(135deg,#d97706,#f59e0b)" onclick="addResult()">+ إضافة</button>
    </div>
    <!-- User review (logged in) -->
    <div class="user-review-form" id="user-review-section">
      <h4>✍️ أضف تقييمك أنت!</h4>
      <input type="text" id="ur-lost" placeholder="كم كيلو خسرت؟ (اختياري)"/>
      <textarea id="ur-review" placeholder="اكتب رأيك ومشاركتك..." style="height:65px;resize:vertical"></textarea>
      <!-- Star rating -->
      <div style="margin:6px 0 4px">
        <span style="font-size:12px;color:#92400e;font-weight:600">تقييمك: </span>
        <span id="star-display" style="font-size:13px;color:#6b7280">لم تختر بعد</span>
      </div>
      <div class="stars-row" id="stars-row">
        <button class="star-btn" onclick="setStar(1)">☆</button>
        <button class="star-btn" onclick="setStar(2)">☆</button>
        <button class="star-btn" onclick="setStar(3)">☆</button>
        <button class="star-btn" onclick="setStar(4)">☆</button>
        <button class="star-btn" onclick="setStar(5)">☆</button>
      </div>
      <!-- Photo upload -->
      <label class="file-upload-label" style="background:#fffbeb;border-color:#fde68a;color:#92400e;margin-top:6px">
        📷 ارفع صورتك (اختياري)
        <input type="file" accept="image/*" id="ur-photo" onchange="previewUserPhoto(this)" style="display:none"/>
      </label>
      <img id="ur-photo-preview" class="img-preview" src="" alt="preview"/>
      <button class="btn-add" style="background:linear-gradient(135deg,#d97706,#f59e0b);margin-top:8px" onclick="submitUserReview()">⭐ نشر تقييمي</button>
    </div>
  </div>
</div>

<!-- ═══ SOCIAL MEDIA MODAL ═══ -->
<div class="modal-overlay" id="social-modal">
  <div class="modal-box wide">
    <button class="modal-close" onclick="closeModal('social-modal')">×</button>
    <h2 class="modal-title">🌐 حساباتي على السوشيال ميديا</h2>
    <div id="social-list"></div>
    <div class="admin-form admin-visible" id="social-add-form">
      <h4>إضافة رابط سوشيال ميديا</h4>
      <select id="new-social-platform" style="margin-bottom:8px">
        <option value="youtube">🎬 يوتيوب</option>
        <option value="facebook">📘 فيسبوك</option>
        <option value="instagram">📸 إنستغرام</option>
        <option value="tiktok">🎵 تيك توك</option>
        <option value="twitter">🐦 تويتر / X</option>
        <option value="telegram">✈️ تيليجرام</option>
        <option value="snapchat">👻 سناب شات</option>
        <option value="other">🔗 رابط آخر</option>
      </select>
      <input type="text" id="new-social-label" placeholder="الاسم (مثال: قناتي على اليوتيوب)"/>
      <input type="text" id="new-social-url" placeholder="الرابط الكامل (https://...)"/>
      <button class="btn-add" style="background:linear-gradient(135deg,#0ea5e9,#38bdf8)" onclick="addSocial()">+ إضافة الرابط</button>
    </div>
  </div>
</div>

<!-- ═══ CHAT MODAL ═══ -->
<div class="modal-overlay" id="chat-modal">
  <div class="modal-box" style="max-width:500px;padding:0;display:flex;flex-direction:column;height:88vh;max-height:640px">
    <!-- Header -->
    <div style="padding:14px 16px;border-bottom:1px solid #e5e7eb;display:flex;align-items:center;gap:10px;flex-shrink:0;background:white;border-radius:20px 20px 0 0">
      <div id="chat-header-avatar" style="width:38px;height:38px;border-radius:50%;background:linear-gradient(135deg,#16a34a,#4ade80);display:flex;align-items:center;justify-content:center;font-size:17px;flex-shrink:0">🌿</div>
      <div style="flex:1;min-width:0">
        <div id="chat-header-name" style="font-weight:800;font-size:14px;color:#111827">الدكتورة</div>
        <div id="chat-header-sub" style="font-size:11px;color:#16a34a">● متاح للرد</div>
      </div>
      <button id="chat-back-btn" onclick="showChatInbox()" style="display:none;background:#f3f4f6;border:none;border-radius:8px;padding:5px 11px;cursor:pointer;font-size:12px;font-weight:700;font-family:inherit;color:#374151">← الكل</button>
      <button class="modal-close" onclick="closeModal('chat-modal')" style="position:static">×</button>
    </div>
    <!-- Body: inbox OR chat thread -->
    <div id="chat-body" style="flex:1;overflow-y:auto;background:#f8fafc"></div>
    <!-- Input -->
    <div id="chat-input-row" style="padding:12px;border-top:1px solid #e5e7eb;display:flex;gap:8px;flex-shrink:0;background:white;border-radius:0 0 20px 20px">
      <input type="text" id="chat-input" placeholder="اكتب رسالتك..." style="flex:1" onkeydown="if(event.key==='Enter')sendChatMsg()"/>
      <button onclick="sendChatMsg()" style="background:linear-gradient(135deg,#16a34a,#22c55e);color:white;border:none;border-radius:10px;padding:10px 16px;cursor:pointer;font-weight:700;font-family:inherit;font-size:13px">إرسال</button>
    </div>
  </div>
</div>

<!-- ═══ SUBSCRIBE CONFIRM MODAL ═══ -->
<div class="modal-overlay" id="subscribe-modal">
  <div class="modal-box" style="max-width:440px;text-align:center">
    <button class="modal-close" onclick="closeModal('subscribe-modal')">×</button>
    <div style="font-size:46px;margin-bottom:10px">💳</div>
    <h2 class="modal-title" style="text-align:center">تأكيد الاشتراك</h2>
    <div id="sub-pkg-info" style="background:#f0fdf4;border-radius:13px;padding:14px;margin-bottom:14px;border:2px solid #bbf7d0"></div>
    <div style="background:#fffbeb;border-radius:12px;padding:14px;margin-bottom:14px;border:1.5px solid #fde68a;text-align:right">
      <p style="font-size:13px;font-weight:700;color:#92400e;margin-bottom:6px">📲 خطوات الاشتراك:</p>
      <p style="font-size:12px;color:#6b7280;line-height:1.8" id="sub-payment-instructions">أرسل المبلغ على:</p>
    </div>
    <div style="background:#f0f9ff;border-radius:12px;padding:12px;border:1.5px solid #bae6fd;margin-bottom:14px">
      <p style="font-size:12px;color:#0369a1;font-weight:700">بعد الإرسال:</p>
      <p style="font-size:11px;color:#6b7280;margin-top:4px">أرسل لقطة شاشة للواتساب وسيتم تفعيل اشتراكك خلال ساعات قليلة ✅</p>
    </div>
    <a id="sub-wa-btn" href="#" target="_blank" class="wa-btn">📱 أرسل إثبات الدفع على الواتساب</a>
    <button onclick="closeModal('subscribe-modal')" style="background:#f3f4f6;border:none;border-radius:10px;padding:9px;width:100%;cursor:pointer;font-weight:600;font-size:13px;font-family:inherit;color:#6b7280">إغلاق</button>
  </div>
</div>

<!-- ═══ ACCESS LOCKED MODAL ═══ -->
<div class="modal-overlay" id="access-locked-modal">
  <div class="modal-box" style="max-width:400px;text-align:center">
    <button class="modal-close" onclick="closeModal('access-locked-modal')">×</button>
    <div style="font-size:52px;margin-bottom:10px">🔒</div>
    <h2 style="font-size:18px;font-weight:800;color:#111827;margin-bottom:8px">محتوى حصري</h2>
    <p style="color:#6b7280;font-size:13px;line-height:1.7;margin-bottom:16px" id="access-lock-msg">هذا المحتوى متاح للمشتركين فقط</p>
    <div id="access-lock-pkgs" style="margin-bottom:14px"></div>
    <button onclick="closeModal('access-locked-modal');openModal('packages-modal')" style="background:linear-gradient(135deg,#16a34a,#22c55e);color:white;border:none;border-radius:11px;padding:12px;width:100%;cursor:pointer;font-weight:700;font-size:14px;font-family:inherit">💎 اشترك الآن</button>
  </div>
</div>

<!-- ═══ JS ═══ -->
<script>
const ADMIN_PASSWORD="boctoer_ta3zeh"+String.fromCharCode(38)+"#**@?!";
let isAdmin=false,currentUser=null,selectedStars=0;
const K={USERS:'tata_users',DATA:'tata_data',ATT:'tata_att'};

// ═══ Firebase helpers ═══
function _fb(){return window._FB||null}
async function fbSet(path,val){const F=_fb();if(!F)return;try{await F.set(F.ref(F.db,path),val)}catch(e){}}
async function fbGet(path){const F=_fb();if(!F)return null;try{const s=await F.get(F.ref(F.db,path));return s.exists()?s.val():null}catch{return null}}
function fbKey(email){return btoa(unescape(encodeURIComponent(email))).replace(/[.#$/[\]]/g,'_')}

// ═══ USERS ═══
function loadUsers(){try{return JSON.parse(localStorage.getItem(K.USERS))||[]}catch{return[]}}
function saveUsers(arr){
  localStorage.setItem(K.USERS,JSON.stringify(arr));
  // Firebase: store as object keyed by encoded email
  const obj={};arr.forEach(u=>{obj[fbKey(u.email)]=u;});
  fbSet('users',obj);
}

// ═══ ATTEMPTS (local only — anti-brute-force per device) ═══
function loadAttempts(){try{return JSON.parse(localStorage.getItem(K.ATT))||{}}catch{return{}}}
function saveAttempts(){localStorage.setItem(K.ATT,JSON.stringify(loginAttempts))}

// ═══ APP DATA (packages, lessons, results…) ═══
function loadData(){try{const s=JSON.parse(localStorage.getItem(K.DATA));return s||defaultData()}catch{return defaultData()}}
function saveData(){
  localStorage.setItem(K.DATA,JSON.stringify(data));
  fbSet('appData',data);
  showToast();
}

// ═══ SYNC FROM FIREBASE on startup ═══
async function syncFromFirebase(){
  const F=_fb();if(!F)return;
  // Users
  const fbUsers=await fbGet('users');
  if(fbUsers){const arr=Object.values(fbUsers);localStorage.setItem(K.USERS,JSON.stringify(arr));users=arr;}
  // App data
  const fbData=await fbGet('appData');
  if(fbData){localStorage.setItem(K.DATA,JSON.stringify(fbData));data=fbData;renderAll();}
  // Brand
  const fbBrand=await fbGet('brand');
  if(fbBrand){localStorage.setItem('tata_brand',JSON.stringify(fbBrand));brand=fbBrand;applyBranding();}
  // Notifs
  const fbNotifs=await fbGet('notifs');
  if(fbNotifs&&Array.isArray(fbNotifs)){localStorage.setItem(K_NOTIF,JSON.stringify(fbNotifs));updateNotifBadge();}
}

// ═══ REAL-TIME LISTENERS ═══
function startFirebaseListeners(){
  const F=_fb();if(!F)return;
  // users → update admin panel in real-time
  F.onValue(F.ref(F.db,'users'),snap=>{
    if(!snap.exists())return;
    const arr=Object.values(snap.val());
    localStorage.setItem(K.USERS,JSON.stringify(arr));users=arr;
    if(currentUser){const u=arr.find(x=>x.email===currentUser.email);if(u){currentUser=u;renderMySubPreview();}}
    if(isAdmin)renderAdminUsers();
  });
  // appData → sync content changes across devices
  F.onValue(F.ref(F.db,'appData'),snap=>{
    if(!snap.exists())return;
    const d=snap.val();
    localStorage.setItem(K.DATA,JSON.stringify(d));data=d;renderAll();
  });
}

function defaultData(){return{
  packages:[
    {id:1,name:"الباقة الأساسية",price:"299 جنيه / شهر",access:"basic",features:["خطة غذائية مخصصة","متابعة أسبوعية","دعم واتساب","محتوى تعليمي أساسي"]},
    {id:2,name:"الباقة المميزة",price:"499 جنيه / شهر",access:"premium",features:["كل مميزات الأساسية","جلسة فيديو شهرية","دروس حصرية","بودكاست خاص"]},
    {id:3,name:"باقة VIP",price:"899 جنيه / شهر",access:"vip",features:["متابعة يومية","خطة تمارين","كل المحتوى الحصري","أولوية في الرد","بودكاست VIP"]},
  ],
  lessons:[
    {id:1,type:"video",title:"أسرار التخسيس السريع",desc:"حلقة كاملة عن كيفية فقدان الوزن بطريقة صحية",duration:"45 دقيقة",mediaUrl:null,access:"free"},
    {id:2,type:"podcast",title:"بودكاست الصحة والتغذية",desc:"نتكلم عن أهمية البروتين في الرجيم",duration:"30 دقيقة",mediaUrl:null,access:"basic"},
    {id:3,type:"video",title:"وجبات صحية سريعة",desc:"10 وجبات صحية في أقل من 20 دقيقة",duration:"25 دقيقة",mediaUrl:null,access:"premium"},
    {id:4,type:"podcast",title:"بودكاست VIP — أسرار التغذية",desc:"حلقة حصرية لأعضاء VIP فقط",duration:"60 دقيقة",mediaUrl:null,access:"vip"},
  ],
  credentials:[
    {id:1,title:"بكالوريوس تغذية وعلوم الأطعمة",year:"2015",desc:"جامعة القاهرة — كلية الاقتصاد المنزلي"},
    {id:2,title:"ماجستير التغذية العلاجية",year:"2018",desc:"معهد التغذية القومي — القاهرة"},
    {id:3,title:"دبلومة تغذية الرياضيين",year:"2020",desc:"الأكاديمية الدولية للتغذية الرياضية"},
  ],
  results:[
    {id:1,name:"سارة محمد",lost:"15 كيلو في 3 شهور",review:"الدكتورة غيرت حياتي تماماً، أنصح الجميع!",avatar:"س",stars:5,photo:null,byUser:false},
    {id:2,name:"نور أحمد",lost:"20 كيلو في 5 شهور",review:"أفضل استثمار في حياتي، النتائج فاقت توقعاتي",avatar:"ن",stars:5,photo:null,byUser:false},
    {id:3,name:"هدى علي",lost:"10 كيلو في شهرين",review:"النظام الغذائي سهل التطبيق ومناسب لحياتي",avatar:"ه",stars:4,photo:null,byUser:false},
  ],
  social:[
    {id:1,platform:"youtube",label:"قناتي على يوتيوب",url:"https://youtube.com"},
    {id:2,platform:"facebook",label:"صفحتي على فيسبوك",url:"https://facebook.com"},
    {id:3,platform:"instagram",label:"حسابي على إنستغرام",url:"https://instagram.com"},
  ],
  whatsapp:"201234567890",
  paymentNumber:"01234567890",
  paymentName:"فودافون كاش",
  chat:[]
}}

let users=loadUsers(),data=loadData(),loginAttempts=loadAttempts();
let lockTimerInterval=null;
const MAX_ATT=5,LOCK_MIN=2;

// ═══ HELPERS ═══
function showError(msg){const e=document.getElementById('auth-error');e.textContent=msg;e.style.display='block';document.getElementById('auth-success').style.display='none';setTimeout(()=>{e.style.display='none'},4500)}
function showSuccess(msg){const e=document.getElementById('auth-success');e.textContent=msg;e.style.display='block';document.getElementById('auth-error').style.display='none'}
function hideAlerts(){document.getElementById('auth-error').style.display='none';document.getElementById('auth-success').style.display='none'}
function showToast(msg){const t=document.getElementById('save-toast');t.textContent=msg||'✅ تم الحفظ — يظهر للجميع فور الدخول';t.style.display='block';setTimeout(()=>{t.style.display='none'},3000)}
function togglePass(id,icon){const i=document.getElementById(id);i.type=i.type==='password'?'text':'password';icon.textContent=i.type==='text'?'🙈':'👁️'}
function checkStrength(v){
  const wrap=document.getElementById('strength-wrap'),fill=document.getElementById('strength-fill'),text=document.getElementById('strength-text');
  if(!v){wrap.style.display='none';return}wrap.style.display='block';
  let s=0;if(v.length>=8)s++;if(/[A-Z]/.test(v))s++;if(/[0-9]/.test(v))s++;if(/[^A-Za-z0-9]/.test(v))s++;
  const l=[{w:'25%',c:'#ef4444',t:'⚠️ ضعيفة'},{w:'50%',c:'#f59e0b',t:'🟡 مقبولة'},{w:'75%',c:'#3b82f6',t:'🔵 جيدة'},{w:'100%',c:'#16a34a',t:'✅ قوية'}][Math.max(0,s-1)];
  fill.style.width=l.w;fill.style.background=l.c;text.textContent=l.t;text.style.color=l.c
}
function checkMaleWarning(v){document.getElementById('male-warning').style.display=v==='ذكر'?'block':'none'}

// ═══ STARS ═══
function setStar(n){
  selectedStars=n;
  const btns=document.querySelectorAll('.star-btn');
  btns.forEach((b,i)=>{b.textContent=i<n?'⭐':'☆'});
  document.getElementById('star-display').textContent='★'.repeat(n)+'☆'.repeat(5-n)+` (${n}/5)`;
}
function starsHtml(n){return'⭐'.repeat(n)+'☆'.repeat(5-n)}

// ═══ LESSON FILE TABS ═══
let currentLessonType='video';
function setLessonTab(type,btn){
  currentLessonType=type;
  document.getElementById('new-lesson-type').value=type;
  document.querySelectorAll('.tab-mini').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  const isVideo=type==='video';
  document.getElementById('lesson-file-icon').textContent=isVideo?'🎬':'🎙️';
  document.getElementById('lesson-file-text').textContent=isVideo?'اختر ملف فيديو (MP4, MOV...)':'اختر ملف صوتي (MP3, WAV...)';
  document.getElementById('new-lesson-file').accept=isVideo?'video/*':'audio/*';
}
function onLessonFileChange(input){
  if(input.files&&input.files[0]){
    document.getElementById('lesson-file-text').textContent='✅ '+input.files[0].name;
  }
}

// ═══ USER PHOTO PREVIEW ═══
function previewUserPhoto(input){
  if(input.files&&input.files[0]){
    const reader=new FileReader();
    reader.onload=e=>{
      const img=document.getElementById('ur-photo-preview');
      img.src=e.target.result;img.style.display='block';
    };
    reader.readAsDataURL(input.files[0]);
  }
}

// ═══ MEMBERSHIP LEVELS ═══
const ACCESS_LEVELS={free:0,basic:1,premium:2,vip:3};
const ACCESS_LABELS={free:'مجاني',basic:'أساسي',premium:'مميز',vip:'VIP'};
const ACCESS_COLORS={free:'#9ca3af',basic:'#16a34a',premium:'#7c3aed',vip:'#d97706'};
const ACCESS_ICONS={free:'🆓',basic:'💚',premium:'💜',vip:'👑'};

function userAccess(){
  if(!currentUser)return 0;
  return ACCESS_LEVELS[currentUser.membership||'free']||0;
}
function canAccess(requiredLevel){
  if(isAdmin)return true;
  return userAccess()>=ACCESS_LEVELS[requiredLevel||'free'];
}
function membershipLabel(m){return ACCESS_LABELS[m||'free']||'مجاني'}
function membershipColor(m){return ACCESS_COLORS[m||'free']||'#9ca3af'}
function membershipIcon(m){return ACCESS_ICONS[m||'free']||'🆓'}


function getAtt(email){if(!loginAttempts[email])loginAttempts[email]={count:0,lockedUntil:null};return loginAttempts[email]}
function isLocked(email){const a=getAtt(email);if(a.lockedUntil&&new Date()<new Date(a.lockedUntil))return true;if(a.lockedUntil&&new Date()>=new Date(a.lockedUntil)){a.count=0;a.lockedUntil=null;saveAttempts()}return false}
function startLock(until){
  if(lockTimerInterval)clearInterval(lockTimerInterval);
  document.getElementById('login-form').style.display='none';
  document.getElementById('lock-screen').style.display='block';
  document.getElementById('attempts-left').style.display='none';
  lockTimerInterval=setInterval(()=>{
    const r=Math.max(0,new Date(until)-new Date());
    if(r<=0){clearInterval(lockTimerInterval);document.getElementById('lock-screen').style.display='none';document.getElementById('login-form').style.display='flex';document.getElementById('lock-countdown').textContent='00:00';hideAlerts();return}
    document.getElementById('lock-countdown').textContent=String(Math.floor(r/60000)).padStart(2,'0')+':'+String(Math.floor((r%60000)/1000)).padStart(2,'0')
  },500)
}

// ═══ TABS ═══
function switchTab(mode){
  document.getElementById('tab-login').classList.toggle('active',mode==='login');
  document.getElementById('tab-register').classList.toggle('active',mode==='register');
  document.getElementById('login-form').style.display=mode==='login'?'flex':'none';
  document.getElementById('register-form').style.display=mode==='register'?'flex':'none';
  document.getElementById('lock-screen').style.display='none';
  document.getElementById('auth-switch').style.display=mode==='login'?'block':'none';
  document.getElementById('auth-switch2').style.display=mode==='register'?'block':'none';
  hideAlerts();
  document.getElementById('attempts-left').style.display='none';
  document.getElementById('strength-wrap').style.display='none';
  document.getElementById('male-warning').style.display='none';
}

// ═══ LOGIN ═══
function doLogin(){
  const email=document.getElementById('login-email').value.trim().toLowerCase();
  const pass=document.getElementById('login-pass').value;
  if(!email||!pass){showError('يرجى تعبئة جميع الحقول');return}
  if(isLocked(email)){startLock(getAtt(email).lockedUntil);return}
  users=loadUsers();
  const user=users.find(u=>u.email.toLowerCase()===email);
  if(!user||user.password!==pass){
    const a=getAtt(email);a.count++;saveAttempts();
    if(a.count>=MAX_ATT){
      const until=new Date(Date.now()+LOCK_MIN*60000).toISOString();
      a.lockedUntil=until;if(user){user.locked=true;saveUsers(users)}saveAttempts();
      showError(`❌ تم قفل الحساب لمدة ${LOCK_MIN} دقيقة`);
      setTimeout(()=>startLock(until),500)
    }else{
      showError('❌ البريد الإلكتروني أو كلمة المرور غير صحيحة');
      const el=document.getElementById('attempts-left');el.style.display='block';
      el.textContent=`⚠️ تبقى لك ${MAX_ATT-a.count} محاولة قبل القفل`
    }
    return
  }
  loginAttempts[email]={count:0,lockedUntil:null};saveAttempts();
  user.locked=false;
  // save login history
  if(!user.loginHistory)user.loginHistory=[];
  user.loginHistory.push(new Date().toISOString());
  saveUsers(users);currentUser=user;
  data=loadData();
  // notify admin
  sendLoginNotification(user);
  enterDashboard()
}

// ═══ REGISTER ═══
function doRegister(){
  const name=document.getElementById('reg-name').value.trim();
  const email=document.getElementById('reg-email').value.trim().toLowerCase();
  const phone=document.getElementById('reg-phone').value.trim();
  const age=document.getElementById('reg-age').value.trim();
  const weight=document.getElementById('reg-weight').value.trim();
  const height=document.getElementById('reg-height').value.trim();
  const gender=document.getElementById('reg-gender').value;
  const pass=document.getElementById('reg-pass').value;
  const pass2=document.getElementById('reg-pass2').value;
  if(!name){showError('يرجى كتابة الاسم الكامل');return}
  if(!email||!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email)){showError('يرجى إدخال بريد إلكتروني صحيح');return}
  if(!phone){showError('يرجى إدخال رقم التليفون');return}
  if(!age||!weight||!height){showError('يرجى إدخال السن والوزن والطول');return}
  if(!gender){showError('يرجى اختيار النوع');return}
  if(gender==='ذكر'){showError('😔 للأسف حالياً مفيش دكتورة تغذية رجالي — الخدمة للسيدات فقط');return}
  if(pass.length<8){showError('كلمة المرور يجب أن تكون 8 أحرف على الأقل');return}
  if(pass!==pass2){showError('كلمتا المرور غير متطابقتين');return}
  users=loadUsers();
  if(users.find(u=>u.email.toLowerCase()===email)){showError('هذا البريد الإلكتروني مسجل بالفعل');return}
  const h=+height/100,bmi=(+weight/(h*h)).toFixed(1);
  users.push({name,email,phone,age:+age,weight:+weight,height:+height,gender,bmi,password:pass,createdAt:new Date().toISOString(),locked:false});
  saveUsers(users);
  showSuccess(`✅ تم إنشاء الحساب بنجاح! مرحباً ${name} 🎉`);
  ['reg-name','reg-email','reg-phone','reg-age','reg-weight','reg-height','reg-pass','reg-pass2'].forEach(id=>document.getElementById(id).value='');
  document.getElementById('reg-gender').value='';
  document.getElementById('strength-wrap').style.display='none';
  document.getElementById('male-warning').style.display='none';
  setTimeout(()=>switchTab('login'),1800)
}

// ═══ DASHBOARD ═══
function enterDashboard(){
  document.getElementById('auth-page').style.display='none';
  document.getElementById('dashboard-page').style.display='block';
  if(currentUser){
    document.getElementById('user-greeting').textContent=`👋 ${currentUser.name}`;
    document.getElementById('hero-welcome').textContent=`أهلاً ${currentUser.name} في تاتا دايت 🌱`;
  }
  renderAll();
  document.getElementById('login-email').value='';
  document.getElementById('login-pass').value='';
}
function doLogout(){
  isAdmin=false;currentUser=null;
  document.getElementById('dashboard-page').style.display='none';
  document.getElementById('auth-page').style.display='flex';
  document.getElementById('admin-badge').style.display='none';
  document.getElementById('user-greeting').textContent='';
  document.getElementById('hero-welcome').textContent='أهلاً بك في تاتا دايت 🌱';
  document.querySelectorAll('.admin-visible').forEach(el=>el.style.display='none')
}

function exitAdminMode(){
  isAdmin=false;
  document.getElementById('admin-badge').style.display='none';
  document.getElementById('btn-exit-admin').style.display='none';
  document.querySelectorAll('.admin-visible').forEach(el=>el.style.display='none');
  renderAll();
  showToast('👤 تم الخروج من وضع الإدارة');
}

// ═══ ADMIN ═══
function doAdminLogin(){
  const pass=document.getElementById('admin-pass-input').value;
  const err=document.getElementById('admin-error');
  if(pass===ADMIN_PASSWORD){
    isAdmin=true;closeModal('admin-modal');
    document.getElementById('admin-pass-input').value='';err.style.display='none';
    document.getElementById('admin-badge').style.display='inline-block';
    document.getElementById('btn-exit-admin').style.display='inline-block';
    document.querySelectorAll('.admin-visible').forEach(el=>{el.style.display=el.tagName==='SPAN'?'inline-block':'block'});
    renderAll();setTimeout(()=>openModal('admin-dashboard-modal'),200)
  }else{err.style.display='block'}
}
function renderAdminUsers(){
  users=loadUsers();
  const today=new Date().toDateString();
  document.getElementById('stat-total').textContent=users.length;
  document.getElementById('stat-today').textContent=users.filter(u=>new Date(u.createdAt).toDateString()===today).length;
  document.getElementById('stat-female').textContent=users.filter(u=>u.gender==='أنثى').length;
  document.getElementById('stat-male').textContent=users.filter(u=>u.gender==='ذكر').length;
  const listEl=document.getElementById('admin-users-list');
  if(!users.length){listEl.innerHTML='<p style="text-align:center;color:#9ca3af;padding:18px;font-size:13px">لا يوجد حسابات مسجلة بعد</p>';return}
  // sort newest first
  const sorted=[...users].sort((a,b)=>new Date(b.createdAt)-new Date(a.createdAt));
  listEl.innerHTML=sorted.map((u,i)=>{
    const origIdx=users.indexOf(u);
    const bmiNum=parseFloat(u.bmi)||0;
    const bmiLabel=bmiNum<18.5?'نحيف جداً':bmiNum<25?'وزن طبيعي ✅':bmiNum<30?'زيادة وزن':bmiNum<35?'سمنة درجة 1':'سمنة مرتفعة';
    const bmiColor=bmiNum<18.5?'#3b82f6':bmiNum<25?'#16a34a':bmiNum<30?'#f59e0b':bmiNum<35?'#ef4444':'#7c2d12';
    const logins=u.loginHistory||[];
    const lastLogin=logins.length?new Date(logins[logins.length-1]).toLocaleString('ar-EG'):'لم يدخل بعد';
    const totalLogins=logins.length;
    return`
    <div style="border-bottom:1px solid #f3f4f6;padding:0">
      <!-- Header row — always visible -->
      <div style="padding:13px 15px;display:flex;align-items:center;gap:9px;cursor:pointer" onclick="toggleUserCard(${origIdx})">
        <div style="width:42px;height:42px;border-radius:50%;background:linear-gradient(135deg,#16a34a,#4ade80);display:flex;align-items:center;justify-content:center;color:white;font-weight:800;font-size:17px;flex-shrink:0">${u.name[0]}</div>
        <div style="flex:1;min-width:0">
          <div style="font-weight:700;font-size:13px;color:#111827;display:flex;align-items:center;gap:6px;flex-wrap:wrap">
            ${u.name}
            <span style="font-size:10px;color:white;background:${u.gender==='أنثى'?'#db2777':'#7c3aed'};padding:1px 6px;border-radius:8px;font-weight:700">${u.gender||'—'}</span>
            ${u.locked?'<span style="background:#fee2e2;color:#ef4444;font-size:10px;padding:1px 6px;border-radius:6px;font-weight:700">🔒</span>':'<span style="background:#dcfce7;color:#16a34a;font-size:10px;padding:1px 6px;border-radius:6px;font-weight:700">✅</span>'}
          </div>
          <div style="font-size:11px;color:#6b7280;white-space:nowrap;overflow:hidden;text-overflow:ellipsis">${u.email}</div>
        </div>
        <div style="display:flex;align-items:center;gap:6px;flex-shrink:0">
          <span style="font-size:18px;transition:transform 0.2s" id="chevron-${origIdx}">▾</span>
          <button onclick="event.stopPropagation();deleteUser(${origIdx})" style="background:#fee2e2;border:none;color:#ef4444;border-radius:6px;width:26px;height:26px;cursor:pointer;font-weight:700;font-size:13px">×</button>
        </div>
      </div>
      <!-- Expandable details -->
      <div id="usercard-${origIdx}" style="display:none;padding:0 15px 15px">
        <!-- Personal -->
        <div style="font-size:10px;color:#9ca3af;font-weight:700;letter-spacing:0.5px;margin-bottom:7px">📋 البيانات الشخصية</div>
        <div style="display:grid;grid-template-columns:repeat(auto-fill,minmax(130px,1fr));gap:6px;margin-bottom:12px">
          <div class="user-info-chip"><span class="lbl">📛 الاسم الكامل</span><span class="val">${u.name}</span></div>
          <div class="user-info-chip"><span class="lbl">📧 البريد</span><span class="val" style="font-size:10px;word-break:break-all">${u.email}</span></div>
          <div class="user-info-chip"><span class="lbl">📱 التليفون</span><span class="val">${u.phone||'—'}</span></div>
          <div class="user-info-chip"><span class="lbl">🚻 النوع</span><span class="val">${u.gender||'—'}</span></div>
          <div class="user-info-chip" style="background:#fef2f2;border-color:#fecaca">
            <span class="lbl">🔑 كلمة المرور</span>
            <span class="val" id="pass-chip-${origIdx}" data-pass="${u.password.replace(/"/g,'&quot;').replace(/'/g,'&#39;')}" style="color:#ef4444;font-family:monospace;font-size:11px;cursor:pointer;user-select:all" title="اضغط لإظهار/إخفاء" onclick="togglePassChip(${origIdx})">••••••••</span>
          </div>
        </div>
        <!-- Membership Control -->
        <div style="background:linear-gradient(135deg,#fefce8,#fffbeb);border:1.5px solid #fde68a;border-radius:11px;padding:12px 14px;margin-bottom:12px">
          <div style="font-size:10px;color:#92400e;font-weight:700;letter-spacing:0.5px;margin-bottom:8px">👑 إدارة الاشتراك</div>
          <div style="display:flex;align-items:center;gap:10px;flex-wrap:wrap">
            <div style="flex:1">
              <div style="font-size:12px;color:#6b7280;margin-bottom:4px">الحالة الحالية:</div>
              <div style="font-size:16px;font-weight:900;color:${membershipColor(u.membership||'free')}">${membershipIcon(u.membership||'free')} ${membershipLabel(u.membership||'free')}</div>
              ${u.membershipActivatedAt?`<div style="font-size:10px;color:#9ca3af;margin-top:2px">فُعّل: ${new Date(u.membershipActivatedAt).toLocaleDateString('ar-EG')}</div>`:''}
            </div>
            <div>
              <div style="font-size:11px;color:#6b7280;margin-bottom:4px;font-weight:600">تغيير الاشتراك:</div>
              <select onchange="changeMembership(${origIdx},this.value)" style="border:1.5px solid #fde68a;border-radius:8px;padding:6px 10px;font-family:inherit;font-size:12px;font-weight:700;background:white;cursor:pointer">
                <option value="free"${(u.membership||'free')==='free'?' selected':''}>🆓 مجاني</option>
                <option value="basic"${u.membership==='basic'?' selected':''}>💚 أساسي</option>
                <option value="premium"${u.membership==='premium'?' selected':''}>💜 مميز</option>
                <option value="vip"${u.membership==='vip'?' selected':''}>👑 VIP</option>
              </select>
            </div>
          </div>
        </div>
        <!-- Medical -->
        <div style="font-size:10px;color:#9ca3af;font-weight:700;letter-spacing:0.5px;margin-bottom:7px">🏥 البيانات الصحية</div>
        <div style="display:grid;grid-template-columns:repeat(auto-fill,minmax(130px,1fr));gap:6px;margin-bottom:12px">
          <div class="user-info-chip"><span class="lbl">📅 السن</span><span class="val">${u.age||'—'} سنة</span></div>
          <div class="user-info-chip"><span class="lbl">⚖️ الوزن</span><span class="val">${u.weight||'—'} كجم</span></div>
          <div class="user-info-chip"><span class="lbl">📏 الطول</span><span class="val">${u.height||'—'} سم</span></div>
          <div class="user-info-chip" style="background:#f0fdf4;border-color:#bbf7d0">
            <span class="lbl">🧮 BMI</span>
            <span class="val" style="color:${bmiColor}">${u.bmi||'—'}</span>
            <span style="font-size:9px;color:${bmiColor};font-weight:600;display:block">${u.bmi?bmiLabel:''}</span>
          </div>
        </div>
        <!-- Activity -->
        <div style="font-size:10px;color:#9ca3af;font-weight:700;letter-spacing:0.5px;margin-bottom:7px">📊 نشاط الحساب</div>
        <div style="display:grid;grid-template-columns:repeat(auto-fill,minmax(130px,1fr));gap:6px;margin-bottom:10px">
          <div class="user-info-chip"><span class="lbl">📆 تاريخ التسجيل</span><span class="val" style="font-size:10px">${new Date(u.createdAt).toLocaleString('ar-EG')}</span></div>
          <div class="user-info-chip"><span class="lbl">🔑 آخر دخول</span><span class="val" style="font-size:10px">${lastLogin}</span></div>
          <div class="user-info-chip"><span class="lbl">📈 إجمالي الدخول</span><span class="val">${totalLogins} مرة</span></div>
          <div class="user-info-chip"><span class="lbl">🔒 الحالة</span><span class="val" style="color:${u.locked?'#ef4444':'#16a34a'}">${u.locked?'مقفول':'نشط'}</span></div>
        </div>
        ${logins.length>1?`
        <details style="margin-top:4px">
          <summary style="font-size:11px;color:#7c3aed;font-weight:700;cursor:pointer;padding:4px 0">🕐 سجل الدخول (${logins.length} مرة)</summary>
          <div style="margin-top:7px;max-height:120px;overflow-y:auto;background:#f8fafc;border-radius:8px;padding:8px">
            ${logins.slice().reverse().map((t,li)=>`
              <div style="font-size:11px;color:#374151;padding:3px 0;border-bottom:1px solid #f1f5f9;display:flex;justify-content:space-between">
                <span>دخول رقم ${logins.length-li}</span>
                <span style="color:#6b7280">${new Date(t).toLocaleString('ar-EG')}</span>
              </div>`).join('')}
          </div>
        </details>`:''}
      </div>
    </div>`}).join('');
}
function toggleUserCard(i){
  const card=document.getElementById(`usercard-${i}`);
  const chev=document.getElementById(`chevron-${i}`);
  const open=card.style.display==='none';
  card.style.display=open?'block':'none';
  if(chev)chev.style.transform=open?'rotate(180deg)':'rotate(0deg)';
}
function savePaymentSettings(){
  const name=document.getElementById('pay-name-input').value.trim();
  const num=document.getElementById('pay-num-input').value.trim();
  if(!num){alert('يرجى إدخال رقم الدفع');return}
  data.paymentName=name||'فودافون كاش';
  data.paymentNumber=num;
  saveData();
  document.getElementById('current-pay-info').textContent=`✅ محفوظ: ${data.paymentName} — ${data.paymentNumber}`;
}

function togglePassChip(idx){
  const el=document.getElementById(`pass-chip-${idx}`);
  if(!el)return;
  if(el.textContent==='••••••••'){
    el.textContent=el.getAttribute('data-pass')||'—';
  } else {
    el.textContent='••••••••';
  }
}

const K_HAZIM='tata_hazim';
function loadHazimNum(){try{return localStorage.getItem(K_HAZIM)||''}catch{return''}}
function saveHazimNum(){
  const v=document.getElementById('hazim-num-input').value.trim();
  if(!v){alert('أدخل رقم التواصل');return}
  localStorage.setItem(K_HAZIM,v);
  document.getElementById('hazim-contact-num').textContent=v;
  showToast('✅ تم حفظ رقم المصمم');
}
function toggleHazimCard(){
  const card=document.getElementById('hazim-card');
  if(!card)return;
  const num=loadHazimNum();
  document.getElementById('hazim-contact-num').textContent=num||'لم يتم تعيين رقم بعد';
  const open=card.style.display==='none'||card.style.display==='';
  card.style.display=open?'block':'none';
  // close on outside click
  if(open){
    setTimeout(()=>{
      document.addEventListener('click',function handler(e){
        if(!card.contains(e.target)&&e.target.id!=='hazim-tag'){
          card.style.display='none';
          document.removeEventListener('click',handler);
        }
      });
    },10);
  }
}

function renderAdminDashboardExtras(){
  const pni=document.getElementById('pay-name-input');
  const pnu=document.getElementById('pay-num-input');
  const cpi=document.getElementById('current-pay-info');
  const hni=document.getElementById('hazim-num-input');
  if(pni)pni.value=data.paymentName||'';
  if(pnu)pnu.value=data.paymentNumber||'';
  if(cpi)cpi.textContent=data.paymentNumber?`الحالي: ${data.paymentName||'—'} — ${data.paymentNumber}`:'لم يتم ضبط رقم الدفع بعد';
  if(hni)hni.value=loadHazimNum();
}
function deleteUser(i){users=loadUsers();if(!confirm(`حذف حساب "${users[i].name}"؟`))return;users.splice(i,1);saveUsers(users);renderAdminUsers()}
function clearAllUsers(){if(!confirm('حذف جميع الحسابات؟ لا يمكن التراجع!'))return;saveUsers([]);users=[];renderAdminUsers()}
function changeMembership(idx,newLevel){
  users=loadUsers();
  if(!users[idx])return;
  users[idx].membership=newLevel;
  users[idx].membershipActivatedAt=newLevel!=='free'?new Date().toISOString():null;
  saveUsers(users);
  // update currentUser if it's them
  if(currentUser&&currentUser.email===users[idx].email){currentUser=users[idx];renderMySubPreview()}
  showToast(`✅ تم تغيير اشتراك ${users[idx].name} إلى ${membershipLabel(newLevel)}`);
  renderAdminUsers();
}

// ═══ MODALS ═══
function openModal(id){
  document.getElementById(id).classList.add('open');
  if(id==='branding-modal'){brand=loadBranding();applyBranding();document.querySelectorAll('.emoji-opt').forEach(b=>{b.classList.toggle('active',b.textContent===brand.emoji)})}
  if(id==='packages-modal')renderPackages();
  if(id==='lessons-modal')renderLessons();
  if(id==='credentials-modal')renderCredentials();
  if(id==='results-modal')renderResults();
  if(id==='social-modal')renderSocial();
  if(id==='chat-modal')renderChat();
  if(id==='contact-modal')updateWaLinks();
  if(id==='admin-dashboard-modal'){renderAdminUsers();renderAdminDashboardExtras()}
}
function closeModal(id){
  document.getElementById(id).classList.remove('open');
  if(id==='admin-modal'){document.getElementById('admin-error').style.display='none';document.getElementById('admin-pass-input').value=''}
}
document.querySelectorAll('.modal-overlay').forEach(o=>{o.addEventListener('click',e=>{if(e.target===o)o.classList.remove('open')})});

// ═══ RENDER ALL ═══
function renderAll(){
  renderPkgPreview();renderLessonPreview();renderCredPreview();renderResultPreview();renderSocialPreview();renderMySubPreview();updateWaLinks();updateChatBadge();
  if(!isAdmin)document.querySelectorAll('.admin-visible').forEach(el=>el.style.display='none')
}
function updateChatBadge(){
  if(!isAdmin)return;
  const idx=loadChatIndex();
  const total=idx.reduce((s,e)=>s+unreadForEmail(e),0);
  const el=document.getElementById('chat-unread-badge');
  if(el){el.style.display=total?'block':'none';el.textContent=`${total} رسالة جديدة غير مقروءة`;}
}
function updateWaLinks(){
  const h=`https://wa.me/${data.whatsapp}`;
  const displayNum=data.whatsapp?`📞 ${data.whatsapp}`:'لم يتم تعيين الرقم بعد';
  const waCard=document.getElementById('wa-link-card');
  const waNumCard=document.getElementById('wa-num-display-card');
  const waMod=document.getElementById('wa-link-modal');
  const waNumMod=document.getElementById('wa-num-display-modal');
  if(waCard)waCard.href=h;
  if(waMod)waMod.href=h;
  if(waNumCard)waNumCard.textContent=displayNum;
  if(waNumMod)waNumMod.textContent=displayNum;
}

// PREVIEW renders
function renderPkgPreview(){document.getElementById('pkg-preview').innerHTML=data.packages.slice(0,2).map(p=>`<div class="pkg-row"><span class="pkg-name">${p.name}</span><span class="pkg-price">${p.price}</span></div>`).join('')}
function renderLessonPreview(){document.getElementById('lesson-preview').innerHTML=data.lessons.slice(0,2).map(l=>`<div class="lesson-row"><span style="font-size:17px">${l.type==='video'?'🎬':'🎙️'}</span><div><div class="lesson-title">${l.title}</div><div class="lesson-dur">${l.duration}</div></div></div>`).join('')}
function renderResultPreview(){document.getElementById('result-preview').innerHTML=data.results.slice(0,2).map(r=>`
  <div class="result-row">
    <div class="result-avatar">${r.photo?`<img src="${r.photo}"/>`:(r.name[0]||'؟')}</div>
    <div>
      <div class="result-name">${r.name} — <span class="result-lost">${r.lost||''}</span></div>
      <div style="font-size:10px;color:#f59e0b">${'⭐'.repeat(r.stars||5)}</div>
      <div class="result-review">${r.review}</div>
    </div>
  </div>`).join('')}
function renderCredPreview(){
  document.getElementById('cred-preview').innerHTML=`<div class="cred-preview">`+data.credentials.slice(0,2).map(c=>`
    <div class="cred-row">
      <div class="cred-row-title">🎓 ${c.title}</div>
      <div class="cred-row-sub">${c.desc} — ${c.year}</div>
    </div>`).join('')+'</div>'
}

// FULL renders
function renderPackages(){
  const acCol={free:'#9ca3af',basic:'#16a34a',premium:'#7c3aed',vip:'#d97706'};
  const acLbl={free:'مجاني',basic:'أساسي',premium:'مميز',vip:'VIP'};
  document.getElementById('pkg-list').innerHTML=data.packages.map(p=>{
    const isCurrent=currentUser&&(currentUser.membership||'free')===(p.access||'basic');
    return`<div class="pkg-card" id="pkgcard-${p.id}" style="${isCurrent?'border-color:#fbbf24;background:#fffbeb':''}">
      <div class="pkg-card-header">
        ${isAdmin
          ?`<input type="text" value="${p.name}" onchange="updatePkgName(${p.id},this.value)" style="font-size:15px;font-weight:800;color:#15803d;border:1.5px dashed #86efac;border-radius:7px;padding:3px 7px;background:#f0fdf4;width:100%;font-family:inherit"/>`
          :`<h3 style="display:flex;align-items:center;gap:6px">${p.name}${isCurrent?'<span style="font-size:10px;color:#d97706;font-weight:700">← اشتراكك</span>':''}</h3>`}
        <div style="display:flex;align-items:center;gap:6px;flex-shrink:0">
          ${isAdmin
            ?`<select onchange="updatePkgAccess(${p.id},this.value)" style="font-size:10px;border-radius:6px;border:1px solid #e5e7eb;padding:2px 4px">${['free','basic','premium','vip'].map(a=>`<option value="${a}"${(p.access||'basic')===a?' selected':''}>${acLbl[a]}</option>`).join('')}</select>
              <input type="text" value="${p.price}" onchange="updatePkgPrice(${p.id},this.value)" style="font-size:11px;font-weight:700;color:white;border:none;border-radius:6px;padding:3px 8px;background:#16a34a;width:120px;text-align:center;font-family:inherit"/>
              <button class="btn-delete" onclick="deletePackage(${p.id})">×</button>`
            :`<span class="pkg-price" style="font-size:12px;padding:4px 11px">${p.price}</span>`}
        </div>
      </div>
      <ul style="padding-right:16px;list-style:none">
        ${p.features.map((f,fi)=>`
          <li style="display:flex;align-items:center;gap:6px;margin-bottom:5px">
            ${isAdmin
              ?`<input type="text" value="${f}" onchange="updatePkgFeature(${p.id},${fi},this.value)" style="flex:1;font-size:12px;border:1px dashed #d1fae5;border-radius:6px;padding:3px 7px;background:#f8fffe;font-family:inherit"/>
                <button onclick="deletePkgFeature(${p.id},${fi})" style="background:#fee2e2;border:none;color:#ef4444;border-radius:5px;width:22px;height:22px;cursor:pointer;font-size:11px;font-weight:700;flex-shrink:0">×</button>`
              :`<span style="color:#16a34a;font-size:13px">✅</span><span style="color:#4b5563;font-size:12px">${f}</span>`}
          </li>`).join('')}
        ${isAdmin?`<li style="margin-top:6px"><div style="display:flex;gap:6px"><input type="text" id="new-feat-${p.id}" placeholder="ميزة جديدة..." style="flex:1;font-size:12px;border:1.5px dashed #86efac;border-radius:7px;padding:5px 9px;background:#f0fdf4;font-family:inherit" onkeydown="if(event.key==='Enter')addPkgFeature(${p.id})"/><button onclick="addPkgFeature(${p.id})" style="background:linear-gradient(135deg,#16a34a,#22c55e);border:none;color:white;border-radius:7px;padding:5px 11px;cursor:pointer;font-weight:800;font-size:16px;font-family:inherit;line-height:1">+</button></div></li>`:''}
      </ul>
      ${!isAdmin&&!isCurrent?`<button onclick="closeModal('packages-modal');openSubscribeModal(${p.id})" style="background:linear-gradient(135deg,${acCol[p.access||'basic']},${acCol[p.access||'basic']}bb);color:white;border:none;border-radius:9px;padding:9px;width:100%;cursor:pointer;font-weight:700;font-size:13px;font-family:inherit;margin-top:10px">💳 اشترك في هذه الباقة</button>`:''}
      ${!isAdmin&&isCurrent?`<div style="background:#d97706;color:white;border-radius:9px;padding:8px;text-align:center;font-weight:700;font-size:12px;margin-top:10px">✅ اشتراكك الحالي</div>`:''}
    </div>`}).join('');
  document.getElementById('pkg-add-form').style.display=isAdmin?'block':'none'
}
function updatePkgName(id,v){const p=data.packages.find(x=>x.id===id);if(p){p.name=v;saveData();renderPkgPreview()}}
function updatePkgPrice(id,v){const p=data.packages.find(x=>x.id===id);if(p){p.price=v;saveData();renderPkgPreview()}}
function updatePkgAccess(id,v){const p=data.packages.find(x=>x.id===id);if(p){p.access=v;saveData();renderPackages()}}
function updatePkgFeature(id,fi,v){const p=data.packages.find(x=>x.id===id);if(p){p.features[fi]=v;saveData()}}
function deletePkgFeature(id,fi){const p=data.packages.find(x=>x.id===id);if(p){p.features.splice(fi,1);saveData();renderPackages()}}
function addPkgFeature(id){
  const inp=document.getElementById(`new-feat-${id}`);
  const v=inp.value.trim();if(!v)return;
  const p=data.packages.find(x=>x.id===id);if(p){p.features.push(v);saveData();renderPackages()}
}

function renderLessons(){
  const accessOrder={free:0,basic:1,premium:2,vip:3};
  const accessTag={free:'🆓 مجاني',basic:'💚 أساسي',premium:'💜 مميز',vip:'👑 VIP'};
  const accessColor={free:'#9ca3af',basic:'#16a34a',premium:'#7c3aed',vip:'#d97706'};
  document.getElementById('lesson-list').innerHTML=data.lessons.map(l=>{
    const hasAccess=canAccess(l.access||'free');
    let mediaHtml='';
    if(hasAccess&&l.mediaUrl){
      mediaHtml=l.type==='video'
        ?`<div class="lesson-media"><video controls src="${l.mediaUrl}"></video></div>`
        :`<div class="lesson-media" style="background:#f0f9ff;padding:10px"><audio controls src="${l.mediaUrl}" style="width:100%"></audio></div>`;
    }
    const accessLvl=l.access||'free';
    const lockOverlay=!hasAccess?`
      <div style="margin-top:10px;background:#f8fafc;border:1.5px dashed #e5e7eb;border-radius:10px;padding:12px;text-align:center">
        <div style="font-size:22px">🔒</div>
        <div style="font-size:12px;font-weight:700;color:#374151;margin:4px 0">محتوى حصري</div>
        <div style="font-size:11px;color:#9ca3af">يتطلب اشتراك <span style="color:${accessColor[accessLvl]};font-weight:700">${accessTag[accessLvl]}</span></div>
        <button onclick="showAccessLock('${accessLvl}')" style="margin-top:8px;background:linear-gradient(135deg,#16a34a,#22c55e);color:white;border:none;border-radius:8px;padding:6px 14px;cursor:pointer;font-size:12px;font-weight:700;font-family:inherit">اشترك الآن</button>
      </div>`:'';
    return`<div class="lesson-card">
      <div class="lesson-card-top">
        <div class="lesson-icon" style="background:${l.type==='video'?'#0891b2':'#7c3aed'}">${l.type==='video'?'🎬':'🎙️'}</div>
        <div style="flex:1">
          <h3>${l.title}</h3><p>${l.desc}</p>
          <span class="lesson-dur-tag">⏱ ${l.duration}</span>
          <span style="margin-right:5px;font-size:10px;color:${accessColor[accessLvl]};font-weight:700">${accessTag[accessLvl]}</span>
        </div>
        ${isAdmin?`
          <select onchange="updateLessonAccess(${l.id},this.value)" style="font-size:10px;border-radius:6px;border:1px solid #e5e7eb;padding:2px 4px;margin-left:4px">
            ${['free','basic','premium','vip'].map(a=>`<option value="${a}"${(l.access||'free')===a?' selected':''}>${accessTag[a]}</option>`).join('')}
          </select>
          <button class="btn-delete" onclick="deleteLesson(${l.id})">×</button>`:''
        }
      </div>
      ${hasAccess?mediaHtml:lockOverlay}
    </div>`
  }).join('');
  document.getElementById('lesson-add-form').style.display=isAdmin?'block':'none'
}

function showAccessLock(required){
  const pkg=data.packages.find(p=>p.access===required)||data.packages[0];
  document.getElementById('access-lock-msg').textContent=`هذا المحتوى متاح لمشتركي ${ACCESS_LABELS[required]} فقط`;
  document.getElementById('access-lock-pkgs').innerHTML=data.packages
    .filter(p=>(ACCESS_LEVELS[p.access||'free']||0)>=(ACCESS_LEVELS[required]||0))
    .map(p=>`<div style="background:#f0fdf4;border:1.5px solid #bbf7d0;border-radius:10px;padding:10px 13px;margin-bottom:7px;display:flex;justify-content:space-between;align-items:center;cursor:pointer" onclick="closeModal('access-locked-modal');openSubscribeModal(${p.id})">
      <span style="font-weight:700;color:#15803d;font-size:13px">${p.name}</span>
      <span style="background:#16a34a;color:white;border-radius:6px;padding:3px 9px;font-size:11px;font-weight:700">${p.price}</span>
    </div>`).join('');
  openModal('access-locked-modal');
}

function openSubscribeModal(pkgId){
  const pkg=data.packages.find(p=>p.id===pkgId)||data.packages[0];
  document.getElementById('sub-pkg-info').innerHTML=`
    <div style="font-size:18px;font-weight:900;color:#15803d;margin-bottom:4px">${pkg.name}</div>
    <div style="font-size:22px;font-weight:900;color:#16a34a;margin-bottom:8px">${pkg.price}</div>
    <ul style="list-style:none;text-align:right">${pkg.features.map(f=>`<li style="font-size:12px;color:#4b5563;margin-bottom:3px">✅ ${f}</li>`).join('')}</ul>`;
  const payName=data.paymentName||'فودافون كاش';
  const payNum=data.paymentNumber||'—';
  document.getElementById('sub-payment-instructions').innerHTML=
    `أرسل المبلغ على <strong style="color:#92400e">${payName}</strong>:<br>
    <span style="font-size:20px;font-weight:900;color:#111827;letter-spacing:2px">${payNum}</span><br>
    <span style="font-size:11px;color:#6b7280">باسم: الدكتورة / تاتا دايت</span>`;
  document.getElementById('sub-wa-btn').href=`https://wa.me/${data.whatsapp}?text=مرحباً، أريد الاشتراك في ${pkg.name} بسعر ${pkg.price}`;
  openModal('subscribe-modal');
}

function updateLessonAccess(id,access){const l=data.lessons.find(x=>x.id===id);if(l){l.access=access;saveData();renderLessons()}}

// ═══ SOCIAL MEDIA ═══
const SOCIAL_ICONS={youtube:'🎬',facebook:'📘',instagram:'📸',tiktok:'🎵',twitter:'🐦',telegram:'✈️',snapchat:'👻',other:'🔗'};
const SOCIAL_COLORS={youtube:'#ef4444',facebook:'#1d4ed8',instagram:'#e1306c',tiktok:'#010101',twitter:'#1da1f2',telegram:'#2ca5e0',snapchat:'#facc15',other:'#6b7280'};

function renderSocialPreview(){
  const el=document.getElementById('social-preview');
  if(!el)return;
  const links=(data.social||[]).slice(0,3);
  el.innerHTML=links.length?links.map(s=>`
    <a href="${s.url}" target="_blank" style="display:flex;align-items:center;gap:8px;background:${SOCIAL_COLORS[s.platform]||'#6b7280'}12;border-radius:8px;padding:7px 10px;margin-bottom:6px;text-decoration:none;border:1px solid ${SOCIAL_COLORS[s.platform]||'#6b7280'}30">
      <span style="font-size:16px">${SOCIAL_ICONS[s.platform]||'🔗'}</span>
      <span style="font-size:12px;font-weight:700;color:#111827">${s.label}</span>
    </a>`).join(''):'<p style="font-size:12px;color:#9ca3af;text-align:center;padding:10px">لا توجد روابط بعد</p>';
}

function renderSocial(){
  document.getElementById('social-list').innerHTML=(data.social||[]).map(s=>`
    <div style="display:flex;align-items:center;gap:9px;padding:10px 12px;background:${SOCIAL_COLORS[s.platform]||'#6b7280'}10;border-radius:11px;margin-bottom:8px;border:1px solid ${SOCIAL_COLORS[s.platform]||'#6b7280'}25">
      <span style="font-size:22px">${SOCIAL_ICONS[s.platform]||'🔗'}</span>
      <div style="flex:1">
        <div style="font-weight:700;font-size:13px;color:#111827">${s.label}</div>
        <a href="${s.url}" target="_blank" style="font-size:11px;color:#6b7280;word-break:break-all">${s.url}</a>
      </div>
      ${isAdmin?`
        <button onclick="likeSocial(${s.id})" style="background:#fdf2f8;border:none;border-radius:6px;padding:4px 8px;cursor:pointer;font-size:14px">${s.liked?'❤️':'🤍'}</button>
        <button onclick="deleteSocial(${s.id})" class="btn-delete">×</button>`:
        `<a href="${s.url}" target="_blank" style="background:${SOCIAL_COLORS[s.platform]||'#6b7280'};color:white;border-radius:8px;padding:5px 11px;font-size:11px;font-weight:700;text-decoration:none">زيارة</a>`}
    </div>`).join('');
  document.getElementById('social-add-form').style.display=isAdmin?'block':'none';
}

function addSocial(){
  const platform=document.getElementById('new-social-platform').value;
  const label=document.getElementById('new-social-label').value.trim();
  const url=document.getElementById('new-social-url').value.trim();
  if(!label||!url){alert('يرجى تعبئة الاسم والرابط');return}
  if(!data.social)data.social=[];
  data.social.push({id:Date.now(),platform,label,url,liked:false});
  saveData();['new-social-label','new-social-url'].forEach(id=>document.getElementById(id).value='');
  renderSocial();renderSocialPreview();
}
function deleteSocial(id){data.social=data.social.filter(s=>s.id!==id);saveData();renderSocial();renderSocialPreview()}
function likeSocial(id){const s=(data.social||[]).find(x=>x.id===id);if(s){s.liked=!s.liked;saveData();renderSocial()}}

// ═══ MY SUBSCRIPTION PREVIEW ═══
function renderMySubPreview(){
  const el=document.getElementById('my-sub-preview');
  if(!el||!currentUser)return;
  const m=currentUser.membership||'free';
  el.innerHTML=`
    <div style="text-align:center;padding:8px 0">
      <div style="font-size:30px">${membershipIcon(m)}</div>
      <div style="font-size:16px;font-weight:900;color:${membershipColor(m)};margin:4px 0">${membershipLabel(m)}</div>
      ${m==='free'?'<div style="font-size:11px;color:#9ca3af">اشترك للوصول للمحتوى الحصري</div>':'<div style="font-size:11px;color:#16a34a;font-weight:600">✅ اشتراكك فعال</div>'}
    </div>`;
  document.getElementById('my-sub-card').querySelector('.btn-card').style.display=m==='vip'?'none':'block';
}

// ═══ CHAT ═══
// ═══ CHAT SYSTEM ═══
// Each user has their own chat: key = tata_chat_USER_EMAIL
// Admin index: tata_chat_index = [email1, email2, ...]
const K_CHAT_IDX = 'tata_chat_index';
let activeChatEmail = null; // which conversation is open

function chatKey(email){ return 'tata_chat_' + email.replace(/[^a-zA-Z0-9_]/g,'_'); }

function loadChatMsgs(email){
  try{ return JSON.parse(localStorage.getItem(chatKey(email)))||[]; }catch{ return []; }
}
async function saveChatMsgs(email, msgs){
  localStorage.setItem(chatKey(email), JSON.stringify(msgs));
  try{
    let idx=JSON.parse(localStorage.getItem(K_CHAT_IDX))||[];
    if(!idx.includes(email)){idx.push(email);localStorage.setItem(K_CHAT_IDX,JSON.stringify(idx));}
  }catch{}
  // Firebase: store chat under chats/<safeKey>
  await fbSet('chats/'+fbKey(email), msgs);
  await fbSet('chatIdx/'+fbKey(email), {email,t:Date.now()});
}
function loadChatIndex(){
  try{ return JSON.parse(localStorage.getItem(K_CHAT_IDX))||[]; }catch{ return []; }
}
function unreadForEmail(email){
  return loadChatMsgs(email).filter(m=>m.from==='user'&&!m.readByAdmin).length;
}

function renderChat(){
  if(isAdmin){
    if(window._FB) syncChatIndexFromFirebase().then(()=>showChatInbox());
    else showChatInbox();
  } else {
    activeChatEmail=currentUser?currentUser.email:null;
    if(activeChatEmail&&window._FB)
      syncUserChatFromFirebase(activeChatEmail).then(()=>openChatThread(activeChatEmail));
    else openChatThread(activeChatEmail);
  }
}

function showChatInbox(){
  // Admin sees list of all conversations
  activeChatEmail = null;
  document.getElementById('chat-back-btn').style.display='none';
  document.getElementById('chat-header-name').textContent='المحادثات';
  document.getElementById('chat-header-sub').textContent='اختر محادثة للرد';
  document.getElementById('chat-header-avatar').textContent='💬';
  document.getElementById('chat-input-row').style.display='none';

  const idx = loadChatIndex();
  const body = document.getElementById('chat-body');

  if(!idx.length){
    body.innerHTML='<div style="text-align:center;padding:30px;color:#9ca3af;font-size:13px">لا توجد محادثات بعد</div>';
    return;
  }

  // Build inbox rows sorted by latest message
  const threads = idx.map(email=>{
    const msgs = loadChatMsgs(email);
    const last = msgs[msgs.length-1];
    const unread = unreadForEmail(email);
    const user = loadUsers().find(u=>u.email===email);
    return { email, msgs, last, unread, name: user ? user.name : email };
  }).sort((a,b)=> a.last&&b.last ? new Date(b.last.time)-new Date(a.last.time) : 0);

  body.innerHTML = '<div style="padding:8px">' + threads.map(t=>`
    <div onclick="openChatThread('${t.email}')" style="display:flex;align-items:center;gap:11px;padding:12px 13px;border-radius:12px;cursor:pointer;margin-bottom:5px;background:${t.unread?'#f0fdf4':'white'};border:1px solid ${t.unread?'#bbf7d0':'#f1f5f9'};transition:background 0.15s" onmouseenter="this.style.background='#f9fafb'" onmouseleave="this.style.background='${t.unread?'#f0fdf4':'white'}'">
      <div style="width:42px;height:42px;border-radius:50%;background:linear-gradient(135deg,#16a34a,#4ade80);display:flex;align-items:center;justify-content:center;color:white;font-weight:800;font-size:17px;flex-shrink:0">${t.name[0]||'?'}</div>
      <div style="flex:1;min-width:0">
        <div style="display:flex;align-items:center;gap:6px">
          <span style="font-weight:700;font-size:13px;color:#111827">${t.name}</span>
          ${t.unread?`<span style="background:#ef4444;color:white;border-radius:10px;font-size:10px;padding:1px 6px;font-weight:700">${t.unread}</span>`:''}
        </div>
        <div style="font-size:12px;color:#6b7280;white-space:nowrap;overflow:hidden;text-overflow:ellipsis">${t.last?t.last.text:'...'}</div>
      </div>
      <div style="font-size:10px;color:#9ca3af;flex-shrink:0">${t.last?new Date(t.last.time).toLocaleTimeString('ar-EG',{hour:'2-digit',minute:'2-digit'}):''}</div>
    </div>`).join('') + '</div>';
}

function openChatThread(email){
  if(!email) return;
  activeChatEmail = email;

  // Mark admin's messages as read
  if(isAdmin){
    const msgs = loadChatMsgs(email);
    msgs.forEach(m=>{ if(m.from==='user') m.readByAdmin=true; });
    saveChatMsgs(email, msgs);
  }

  const user = loadUsers().find(u=>u.email===email);
  const name = user ? user.name : email;

  document.getElementById('chat-header-name').textContent = isAdmin ? name : 'الدكتورة';
  document.getElementById('chat-header-sub').textContent = isAdmin ? email : '● متاح للرد';
  document.getElementById('chat-header-avatar').textContent = isAdmin ? (name[0]||'?') : '🌿';
  if(isAdmin) document.getElementById('chat-back-btn').style.display='inline-block';
  document.getElementById('chat-input-row').style.display='flex';

  renderChatThread(email);
}

function renderChatThread(email){
  const msgs = loadChatMsgs(email);
  const body = document.getElementById('chat-body');

  if(!msgs.length){
    body.innerHTML='<div style="text-align:center;padding:30px;color:#9ca3af;font-size:13px">ابدأ المحادثة 👋</div>';
    return;
  }

  body.innerHTML='<div style="padding:12px;display:flex;flex-direction:column;gap:8px">' + msgs.map(m=>{
    const sentByMe = (m.from==='user'&&!isAdmin)||(m.from==='admin'&&isAdmin);
    return`<div style="display:flex;justify-content:${sentByMe?'flex-end':'flex-start'};align-items:flex-end;gap:5px">
      ${!sentByMe?`<div style="width:28px;height:28px;border-radius:50%;background:linear-gradient(135deg,#16a34a,#4ade80);display:flex;align-items:center;justify-content:center;font-size:12px;flex-shrink:0">${sentByMe?'':isAdmin?(m.sender?m.sender[0]:'?'):'🌿'}</div>`:''}
      <div>
        <div style="max-width:260px;background:${sentByMe?'linear-gradient(135deg,#16a34a,#22c55e)':'white'};color:${sentByMe?'white':'#111827'};border-radius:${sentByMe?'16px 16px 4px 16px':'16px 16px 16px 4px'};padding:9px 13px;box-shadow:0 2px 8px rgba(0,0,0,0.07);font-size:13px;line-height:1.5">
          ${m.liked?'<div style="font-size:14px;margin-bottom:2px">❤️</div>':''}
          ${m.text}
        </div>
        <div style="font-size:10px;color:#9ca3af;margin-top:3px;${sentByMe?'text-align:right':'text-align:left'};display:flex;align-items:center;gap:5px;${sentByMe?'justify-content:flex-end':''}">
          ${new Date(m.time).toLocaleTimeString('ar-EG',{hour:'2-digit',minute:'2-digit'})}
          ${isAdmin&&m.from==='user'?`<button onclick="likeMsg('${email}',${m.id})" style="background:none;border:none;cursor:pointer;font-size:13px;padding:0;line-height:1">${m.liked?'❤️':'🤍'}</button>`:''}
        </div>
      </div>
    </div>`}).join('') + '</div>';
  body.scrollTop = body.scrollHeight;
}

async function sendChatMsg(){
  const inp=document.getElementById('chat-input');
  const text=inp.value.trim(); if(!text) return;
  const email = activeChatEmail || (currentUser ? currentUser.email : null);
  if(!email){ alert('يرجى تسجيل الدخول أولاً'); return; }
  const msgs=loadChatMsgs(email);
  msgs.push({
    id:Date.now(),
    from: isAdmin?'admin':'user',
    sender: isAdmin?'الدكتورة':(currentUser?.name||'زائر'),
    text,
    time:new Date().toISOString(),
    liked:false,
    readByAdmin: isAdmin
  });
  await saveChatMsgs(email, msgs);
  inp.value='';
  renderChatThread(email);
  if(!isAdmin){
    sendLoginNotification({
      name:(currentUser?.name||'زائر'),
      email:'chat',
      type:'chat',
      title:'💬 رسالة جديدة',
      body:`${currentUser?.name||'زائر'}: ${text.slice(0,40)}`
    });
  }
}

async function likeMsg(email, id){
  const msgs=loadChatMsgs(email);
  const m=msgs.find(x=>x.id===id);
  if(m){ m.liked=!m.liked; await saveChatMsgs(email,msgs); renderChatThread(email); }
}


// ═══ Firebase chat sync helpers ═══
async function syncUserChatFromFirebase(email){
  const F=window._FB;if(!F)return;
  try{
    const s=await F.get(F.ref(F.db,'chats/'+fbKey(email)));
    if(s.exists()&&Array.isArray(s.val()))
      localStorage.setItem(chatKey(email),JSON.stringify(s.val()));
  }catch{}
}
async function syncChatIndexFromFirebase(){
  const F=window._FB;if(!F)return;
  try{
    const s=await F.get(F.ref(F.db,'chatIdx'));
    if(s.exists()){
      const emails=Object.values(s.val()).map(v=>v.email);
      let local=JSON.parse(localStorage.getItem(K_CHAT_IDX)||'[]');
      emails.forEach(e=>{if(!local.includes(e))local.push(e);});
      localStorage.setItem(K_CHAT_IDX,JSON.stringify(local));
      for(const e of emails) await syncUserChatFromFirebase(e);
    }
  }catch{}
}

// ═══ Sync indicator (small spinning badge) ═══
function showSyncing(){
  const el=document.getElementById('sync-dot');
  if(el){el.style.display='flex';setTimeout(()=>el.style.display='none',1500);}
}

function renderCredentials(){
  document.getElementById('cred-list').innerHTML=data.credentials.map(c=>`
    <div class="cred-card">
      <div style="display:flex;justify-content:space-between;align-items:flex-start">
        <div>
          <h3>${c.title}</h3>
          <p>${c.desc}</p>
          <div class="cred-year">📅 ${c.year}</div>
        </div>
        ${isAdmin?`<button class="btn-delete" onclick="deleteCredential(${c.id})">×</button>`:''}
      </div>
    </div>`).join('');
  document.getElementById('cred-add-form').style.display=isAdmin?'block':'none'
}

function renderResults(){
  document.getElementById('result-list').innerHTML=data.results.map(r=>`
    <div class="result-card">
      <div class="result-card-avatar">${r.photo?`<img src="${r.photo}"/>`:(r.name[0]||'؟')}</div>
      <div style="flex:1">
        <div style="display:flex;align-items:center;gap:6px;flex-wrap:wrap">
          <span style="font-weight:800;color:#92400e;font-size:13px">${r.name}</span>
          ${r.lost?`<span class="result-badge">🎯 ${r.lost}</span>`:''}
          ${r.byUser?'<span style="background:#dbeafe;color:#1d4ed8;font-size:10px;padding:2px 6px;border-radius:6px;font-weight:700">✍️ عميل</span>':''}
          ${r.liked?'<span style="font-size:15px">❤️</span>':''}
        </div>
        <div class="stars-display" style="font-size:13px;margin:3px 0">${starsHtml(r.stars||5)}</div>
        <p>"${r.review}"</p>
      </div>
      <div style="display:flex;flex-direction:column;gap:5px;flex-shrink:0">
        ${isAdmin?`<button onclick="likeResult(${r.id})" style="background:#fdf2f8;border:none;border-radius:6px;padding:4px 7px;cursor:pointer;font-size:16px">${r.liked?'❤️':'🤍'}</button>
        <button class="btn-delete" onclick="deleteResult(${r.id})">×</button>`:''}
      </div>
    </div>`).join('');
  document.getElementById('result-add-form').style.display=isAdmin?'block':'none';
  const urf=document.getElementById('user-review-section');
  urf.style.display=currentUser?'block':'none'
}
function likeResult(id){const r=data.results.find(x=>x.id===id);if(r){r.liked=!r.liked;saveData();renderResults();renderResultPreview()}}

// ═══ ADD / DELETE ═══
function addPackage(){
  const name=document.getElementById('new-pkg-name').value.trim(),price=document.getElementById('new-pkg-price').value.trim(),feats=document.getElementById('new-pkg-features').value.trim();
  if(!name||!price){alert('يرجى تعبئة اسم الباقة والسعر');return}
  data.packages.push({id:Date.now(),name,price,features:feats?feats.split('،').map(f=>f.trim()):[]});
  saveData();['new-pkg-name','new-pkg-price','new-pkg-features'].forEach(id=>document.getElementById(id).value='');
  renderPackages();renderPkgPreview()
}
function deletePackage(id){data.packages=data.packages.filter(p=>p.id!==id);saveData('🗑️ تم حذف الباقة');renderPackages();renderPkgPreview()}

function addLesson(){
  const type=document.getElementById('new-lesson-type').value;
  const title=document.getElementById('new-lesson-title').value.trim();
  const desc=document.getElementById('new-lesson-desc').value.trim();
  const duration=document.getElementById('new-lesson-dur').value.trim();
  const access=document.getElementById('new-lesson-access').value||'free';
  const urlInput=document.getElementById('new-lesson-url');
  const urlVal=urlInput?urlInput.value.trim():'';
  const fileInput=document.getElementById('new-lesson-file');
  if(!title){alert('يرجى كتابة عنوان المحتوى');return}
  // Priority: file > url
  const file=fileInput.files&&fileInput.files[0];
  if(file){
    const reader=new FileReader();
    reader.onload=e=>{
      data.lessons.push({id:Date.now(),type,title,desc,duration,access,mediaUrl:e.target.result});
      saveData();clearLessonForm();renderLessons();renderLessonPreview()
    };
    reader.readAsDataURL(file)
  }else{
    data.lessons.push({id:Date.now(),type,title,desc,duration,access,mediaUrl:urlVal||null});
    saveData();clearLessonForm();renderLessons();renderLessonPreview()
  }
}
function clearLessonForm(){
  ['new-lesson-title','new-lesson-desc','new-lesson-dur'].forEach(id=>document.getElementById(id).value='');
  document.getElementById('new-lesson-file').value='';
  document.getElementById('lesson-file-text').textContent='اختر ملف فيديو (MP4, MOV...)';
  const ua=document.getElementById('new-lesson-access');if(ua)ua.value='free';
  const uu=document.getElementById('new-lesson-url');if(uu)uu.value='';
}
function deleteLesson(id){data.lessons=data.lessons.filter(l=>l.id!==id);saveData('🗑️ تم حذف الدرس');renderLessons();renderLessonPreview()}

function addCredential(){
  const title=document.getElementById('new-cred-title').value.trim();
  const year=document.getElementById('new-cred-year').value.trim();
  const desc=document.getElementById('new-cred-desc').value.trim();
  if(!title){alert('يرجى كتابة اسم الشهادة');return}
  data.credentials.push({id:Date.now(),title,year,desc});
  saveData();['new-cred-title','new-cred-year','new-cred-desc'].forEach(id=>document.getElementById(id).value='');
  renderCredentials();renderCredPreview()
}
function deleteCredential(id){data.credentials=data.credentials.filter(c=>c.id!==id);saveData('🗑️ تم الحذف');renderCredentials();renderCredPreview()}

function addResult(){
  const name=document.getElementById('new-result-name').value.trim(),lost=document.getElementById('new-result-lost').value.trim(),review=document.getElementById('new-result-review').value.trim();
  if(!name){alert('يرجى كتابة اسم العميل');return}
  data.results.push({id:Date.now(),name,lost,review,avatar:name[0]||'؟',stars:5,photo:null,byUser:false});
  saveData();['new-result-name','new-result-lost','new-result-review'].forEach(id=>document.getElementById(id).value='');
  renderResults();renderResultPreview()
}
function deleteResult(id){data.results=data.results.filter(r=>r.id!==id);saveData('🗑️ تم الحذف');renderResults();renderResultPreview()}

// USER SUBMIT REVIEW
function submitUserReview(){
  if(!currentUser){alert('يجب تسجيل الدخول أولاً');return}
  const lost=document.getElementById('ur-lost').value.trim();
  const review=document.getElementById('ur-review').value.trim();
  if(!review){alert('يرجى كتابة رأيك أولاً');return}
  if(!selectedStars){alert('يرجى اختيار عدد النجوم');return}
  const photoInput=document.getElementById('ur-photo');
  const finalize=(photoUrl)=>{
    data.results.push({id:Date.now(),name:currentUser.name,lost,review,avatar:currentUser.name[0],stars:selectedStars,photo:photoUrl||null,byUser:true});
    saveData('✅ تم نشر تقييمك!');
    document.getElementById('ur-lost').value='';
    document.getElementById('ur-review').value='';
    document.getElementById('ur-photo').value='';
    document.getElementById('ur-photo-preview').style.display='none';
    setStar(0);selectedStars=0;
    document.getElementById('star-display').textContent='لم تختر بعد';
    document.querySelectorAll('.star-btn').forEach(b=>b.textContent='☆');
    renderResults();renderResultPreview()
  };
  if(photoInput.files&&photoInput.files[0]){
    const reader=new FileReader();
    reader.onload=e=>finalize(e.target.result);
    reader.readAsDataURL(photoInput.files[0])
  }else{finalize(null)}
}

function saveWa(){
  const num=document.getElementById('new-wa-num').value.trim();if(!num)return;
  data.whatsapp=num;document.getElementById('new-wa-num').value='';
  saveData();showToast('📱 تم حفظ رقم الواتساب');updateWaLinks()
}

// ═══ ADMIN FOOTER — long press 3s ═══
(function(){
  let pressTimer=null;
  const btn=document.getElementById('admin-footer-btn');
  function startPress(){pressTimer=setTimeout(()=>{if(isAdmin)openModal('admin-dashboard-modal');else openModal('admin-modal');},1200)}
  function endPress(){clearTimeout(pressTimer)}
  btn.addEventListener('mousedown',startPress);
  btn.addEventListener('mouseup',endPress);
  btn.addEventListener('mouseleave',endPress);
  btn.addEventListener('touchstart',startPress,{passive:true});
  btn.addEventListener('touchend',endPress);
  btn.addEventListener('click',()=>{/* single click does nothing */});
})();

// ═══ BRANDING ═══
function loadBranding(){
  try{return JSON.parse(localStorage.getItem('tata_brand'))||{emoji:'🌿',name:'تاتا دايت',tagline:'نظام غذائي صحي متكامل',color1:'#16a34a',color2:'#22c55e'}}
  catch{return{emoji:'🌿',name:'تاتا دايت',tagline:'نظام غذائي صحي متكامل',color1:'#16a34a',color2:'#22c55e'}}
}
function saveBranding(){localStorage.setItem('tata_brand',JSON.stringify(brand));fbSet('brand',brand);applyBranding();showToast('🎨 تم حفظ هوية الموقع')}
let brand=loadBranding();
function applyBranding(){
  const {emoji,name,tagline,color1,color2,logoImg}=brand;
  const grad=`linear-gradient(135deg,${color1},${color2})`;
  // logos — image or emoji
  document.querySelectorAll('.logo-box,.header-logo-icon').forEach(el=>{
    el.style.background=logoImg?'transparent':grad;
    if(logoImg){
      el.innerHTML=`<img src="${logoImg}" style="width:100%;height:100%;object-fit:cover;border-radius:inherit"/>`;
    }else{
      el.innerHTML=emoji;
    }
  });
  // current preview in modal
  const cp=document.getElementById('logo-current-preview');
  if(cp){
    cp.style.background=logoImg?'transparent':grad;
    cp.innerHTML=logoImg?`<img src="${logoImg}" style="width:100%;height:100%;object-fit:cover;border-radius:14px"/>`:(emoji||'🌿');
  }
  // names
  document.querySelector('.auth-title').textContent=name;
  document.querySelector('.header-logo h1').textContent=name;
  document.title=name;
  // tagline
  document.querySelector('.header-logo p').textContent=tagline;
  // hero gradient
  document.querySelector('.hero').style.background=`linear-gradient(135deg,${color1}cc 0%,${color1} 50%,${color2} 100%)`;
  // brand color for text
  document.querySelectorAll('.auth-title,.header-logo h1').forEach(el=>{el.style.color=color1});
  // preview in modal
  const pi=document.getElementById('brand-preview-icon');
  const pn=document.getElementById('brand-preview-name');
  const pt=document.getElementById('brand-preview-tag');
  if(pi){
    pi.style.background=logoImg?'transparent':grad;
    pi.innerHTML=logoImg?`<img src="${logoImg}" style="width:100%;height:100%;object-fit:cover;border-radius:14px"/>`:emoji;
  }
  if(pn){pn.textContent=name;pn.style.color=color1}
  if(pt)pt.textContent=tagline;
  // fill inputs
  const ni=document.getElementById('brand-name'),ti=document.getElementById('brand-tagline');
  if(ni)ni.value=name;if(ti)ti.value=tagline;
}
function uploadLogoImage(input){
  if(!input.files||!input.files[0])return;
  const reader=new FileReader();
  reader.onload=e=>{brand.logoImg=e.target.result;saveBranding();showToast('🖼️ تم رفع صورة اللوجو!')};
  reader.readAsDataURL(input.files[0]);
}
function clearLogoImage(){brand.logoImg=null;saveBranding();showToast('✅ تم الرجوع للإيموجي')}
function setBrandEmoji(e){if(!e)return;brand.emoji=e;saveBranding();document.querySelectorAll('.emoji-opt').forEach(b=>{b.classList.toggle('active',b.textContent===e)})}
function saveBrandName(){const v=document.getElementById('brand-name').value.trim();if(!v)return;brand.name=v;saveBranding()}
function saveBrandTagline(){const v=document.getElementById('brand-tagline').value.trim();if(!v)return;brand.tagline=v;saveBranding()}
function setBrandColor(c1,c2){brand.color1=c1;brand.color2=c2;saveBranding()}
function openBrandingEditor(){closeModal('admin-dashboard-modal');openModal('branding-modal')}

// ═══ NOTIFICATIONS ═══
const K_NOTIF='tata_notifs';
function loadNotifs(){try{return JSON.parse(localStorage.getItem(K_NOTIF))||[]}catch{return[]}}
function saveNotif(n){const arr=loadNotifs();arr.unshift(n);if(arr.length>50)arr.length=50;localStorage.setItem(K_NOTIF,JSON.stringify(arr));fbSet('notifs',arr)}
function unreadCount(){return loadNotifs().filter(n=>!n.read).length}
function markAllRead(){const arr=loadNotifs();arr.forEach(n=>n.read=true);localStorage.setItem(K_NOTIF,JSON.stringify(arr));updateNotifBadge()}

function updateNotifBadge(){
  const cnt=unreadCount();
  let badge=document.getElementById('notif-badge');
  if(!badge){
    const heroBtn=document.getElementById('hero-admin-btn');
    if(!heroBtn)return;
    badge=document.createElement('span');
    badge.id='notif-badge';
    badge.style.cssText='position:absolute;top:-6px;right:-6px;background:#ef4444;color:white;font-size:9px;font-weight:800;border-radius:50%;min-width:17px;height:17px;display:flex;align-items:center;justify-content:center;pointer-events:none;padding:0 3px;box-shadow:0 1px 4px rgba(0,0,0,0.3)';
    heroBtn.style.position='relative';
    heroBtn.appendChild(badge);
  }
  badge.textContent=cnt>9?'9+':cnt;
  badge.style.display=cnt>0?'flex':'none';
}

function sendLoginNotification(user){
  const notif={id:Date.now(),type:'login',title:'🔑 دخول جديد',body:`${user.name} سجّل دخوله للتو`,detail:`${user.email} · ${user.gender||''} · BMI: ${user.bmi||'—'}`,time:new Date().toISOString(),read:false};
  saveNotif(notif);
  updateNotifBadge();
  if('Notification' in window){
    const fire=()=>new Notification('تاتا دايت 🌿',{body:`🔑 ${user.name} دخل الآن`,icon:'data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><text y=".9em" font-size="90">🌿</text></svg>'});
    if(Notification.permission==='granted'){fire()}
    else if(Notification.permission!=='denied'){Notification.requestPermission().then(p=>{if(p==='granted')fire()})}
  }
}

function openNotifPanel(){
  const notifs=loadNotifs();
  markAllRead();updateNotifBadge();
  let html='';
  if(!notifs.length){html='<p style="text-align:center;color:#9ca3af;padding:24px;font-size:13px">📭 لا توجد إشعارات بعد</p>'}
  else{html=notifs.map(n=>`
    <div style="padding:12px 16px;border-bottom:1px solid #f3f4f6;background:${n.read?'white':'#fefce8'}">
      <div style="font-size:13px;font-weight:700;color:#111827">${n.title}</div>
      <div style="font-size:12px;color:#374151;margin-top:2px">${n.body}</div>
      <div style="font-size:10px;color:#9ca3af;margin-top:2px">${n.detail}</div>
      <div style="font-size:10px;color:#d1d5db;margin-top:2px">${new Date(n.time).toLocaleString('ar-EG')}</div>
    </div>`).join('')}
  document.getElementById('notif-list').innerHTML=`
    <div style="padding:14px 18px 10px;border-bottom:1px solid #e5e7eb;display:flex;justify-content:space-between;align-items:center">
      <h3 style="font-size:16px;font-weight:800;color:#111827">🔔 الإشعارات</h3>
      <button onclick="clearNotifs()" style="background:#fee2e2;border:none;color:#ef4444;border-radius:7px;padding:4px 11px;cursor:pointer;font-size:11px;font-weight:700;font-family:inherit">مسح الكل</button>
    </div>${html}`;
  document.getElementById('notif-modal').classList.add('open');
}
function clearNotifs(){localStorage.setItem(K_NOTIF,JSON.stringify([]));openNotifPanel()}

applyBranding();
updateNotifBadge();

// ════════════════════════════════════════════════════
// FIREBASE STARTUP
// ════════════════════════════════════════════════════
function onFirebaseReady(){
  showSyncing();
  syncFromFirebase();
  startFirebaseListeners();
  // Hide offline banner
  const ob=document.getElementById('offline-banner');
  if(ob)ob.style.display='none';
}

if(window._FB_READY){
  onFirebaseReady();
}else{
  document.addEventListener('fb-ready',onFirebaseReady);
  // Offline fallback after 5s
  setTimeout(()=>{
    if(!window._FB_READY){
      const ob=document.getElementById('offline-banner');
      if(ob)ob.style.display='block';
      console.warn('Firebase not loaded — offline mode');
    }
  },5000);
}
</script>
</body>
</html>
