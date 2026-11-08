# chat-host
<html lang="id">
<head>
<meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Chat User - Chat rahasia</title>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700;800&display=swap" rel="stylesheet">
<style>
*{font-family:'Poppins',sans-serif;box-sizing:border-box}
:root{--bg1:#0f0f14;--bg2:#1a1630;--card:rgba(255,255,255,0.08);--me:linear-gradient(135deg,#a855f7,#ec4899);--meSolid:#a855f7;--meShadow:rgba(168,85,247,.45);--border:rgba(255,255,255,0.12);--glow1:#a855f7;--glow2:#ec4899;--bgDark:#0f0f14;--bgDark2:#1a1630;}
body[data-bubble="ungu"]{--me:linear-gradient(135deg,#a855f7,#ec4899);--meSolid:#a855f7;--meShadow:rgba(168,85,247,.45);--glow1:#a855f7;--glow2:#ec4899;--bgDark:#0f0f14;--bgDark2:#1a1630;--bg1:#f5f3ff;--bg2:#e9d5ff;--you:#6d28d9;--youLight:#ddd6fe;--youText:#4c1d95;--youShadow:rgba(109,40,217,.35)}
body[data-bubble="biru"]{--me:linear-gradient(135deg,#3b82f6,#06b6d4);--meSolid:#3b82f6;--meShadow:rgba(59,130,246,.45);--glow1:#3b82f6;--glow2:#06b6d4;--bgDark:#070f1f;--bgDark2:#0b1e3a;--bg1:#eff6ff;--bg2:#dbeafe;--you:#1d4ed8;--youLight:#bfdbfe;--youText:#1e40af;--youShadow:rgba(29,78,216,.35)}
body[data-bubble="hijau"]{--me:linear-gradient(135deg,#22c55e,#14b8a6);--meSolid:#22c55e;--meShadow:rgba(34,197,94,.45);--glow1:#22c55e;--glow2:#14b8a6;--bgDark:#07150d;--bgDark2:#0b2a1a;--bg1:#f0fdf4;--bg2:#dcfce7;--you:#15803d;--youLight:#bbf7d0;--youText:#166534;--youShadow:rgba(21,128,61,.35)}
body[data-bubble="orange"]{--me:linear-gradient(135deg,#f97316,#ef4444);--meSolid:#f97316;--meShadow:rgba(249,115,22,.45);--glow1:#f97316;--glow2:#ef4444;--bgDark:#1a0d05;--bgDark2:#2a1408;--bg1:#fff7ed;--bg2:#ffedd5;--you:#c2410c;--youLight:#fed7aa;--youText:#9a3412;--youShadow:rgba(194,65,12,.35)}
body[data-bubble="pink"]{--me:linear-gradient(135deg,#ec4899,#f43f5e);--meSolid:#ec4899;--meShadow:rgba(236,72,153,.45);--glow1:#ec4899;--glow2:#f43f5e;--bgDark:#1a0a12;--bgDark2:#2a0f1e;--bg1:#fdf2f8;--bg2:#fce7f3;--you:#be185d;--youLight:#fbcfe8;--youText:#9d174d;--youShadow:rgba(190,24,93,.35)}
body[data-bubble="hitam"]{--me:linear-gradient(135deg,#475569,#0f172a);--meSolid:#334155;--meShadow:rgba(0,0,0,.5);--glow1:#475569;--glow2:#0f172a;--bgDark:#050505;--bgDark2:#111827;--bg1:#f8fafc;--bg2:#e2e8f0;--you:#334155;--youLight:#cbd5e1;--youText:#1e293b;--youShadow:rgba(51,65,85,.35)}
body[data-bubble="kuning"]{--me:linear-gradient(135deg,#eab308,#f97316);--meSolid:#eab308;--meShadow:rgba(234,179,8,.45);--glow1:#eab308;--glow2:#f97316;--bgDark:#171204;--bgDark2:#2a1f08;--bg1:#fefce8;--bg2:#fef9c3;--you:#a16207;--youLight:#fef08a;--youText:#854d0e;--youShadow:rgba(161,98,7,.35)}

/* ===== FIX BACKGROUND KEGESER - MULAI DARI SINI ===== */
html,body{height:100%}
body{margin:0;min-height:100vh;min-height:100dvh;background:var(--bgDark);display:flex;justify-content:center;align-items:center;padding:16px;overflow-x:hidden;position:relative;transition:background-color .5s ease;}
/* Background diem di belakang, ga ikut scroll */
body::before{content:'';position:fixed;inset:0;z-index:-1;pointer-events:none;background:radial-gradient(900px 600px at 15% -10%, var(--glow1) 0%, transparent 55%),radial-gradient(700px 500px at 100% 110%, var(--glow2) 0%, transparent 55%),linear-gradient(180deg,var(--bgDark2),var(--bgDark));transition:.5s}
body.light{background:var(--bg1)}
body.light::before{background:radial-gradient(900px 600px at 15% -10%, var(--glow1) 0%, transparent 50%),radial-gradient(700px 500px at 100% 110%, var(--glow2) 0%, transparent 50%),linear-gradient(180deg,var(--bg2),var(--bg1))}
/* ===== FIX SELESAI ===== */
body.light{color:#111;--card:rgba(255,255,255,0.85);--border:rgba(0,0,0,0.1);}
.card{width:100%;max-width:420px;background:var(--card);backdrop-filter:blur(24px);border:1px solid var(--border);border-radius:28px;overflow:hidden;box-shadow:0 20px 60px rgba(0,0,0,0.4);position:relative;transition:.4s;flex-shrink:0}
.nama-error{display:none;align-items:center;gap:8px;background:rgba(239,68,68,.14);border:1px solid rgba(239,68,68,.45);color:#fca5a5;padding:10px 12px;border-radius:12px;font-size:12px;font-weight:500;text-align:left;margin:-4px 0 12px;animation:shake .35s ease, fadeIn .25s ease;}
body.light .nama-error{background:#fef2f2;color:#dc2626;border-color:#fecaca;}
.nama-error.show{display:flex}
.nama-error .icon{width:24px;height:24px;min-width:24px;background:#ef4444;color:#fff;border-radius:50%;display:grid;place-items:center;font-size:12px;font-weight:800;}
.input.error{border:2px solid #ef4444 !important;box-shadow:0 0 0 4px rgba(239,68,68,.2) !important;animation:shake .35s ease;}
@keyframes shake{0%,100%{transform:translateX(0)}25%{transform:translateX(-5px)}50%{transform:translateX(5px)}75%{transform:translateX(-3px)}}
@keyframes fadeIn{from{opacity:0;transform:translateY(-4px)}to{opacity:1;transform:translateY(0)}}
.mini-toast{position:fixed;bottom:20px;left:50%;transform:translateX(-50%) translateY(20px);background:#111;color:#fff;padding:11px 18px;border-radius:20px;font-size:12px;font-weight:600;box-shadow:0 10px 30px rgba(0,0,0,.4);opacity:0;pointer-events:none;transition:.3s;z-index:999;}
.mini-toast.show{opacity:1;transform:translateX(-50%) translateY(0)}
.mini-toast.error{background:#ef4444}
.mini-toast.success{background:#22c55e}
#pageLogin{padding:32px 24px;text-align:center;animation:pageIn .5s ease}
#pageChat{display:none;flex-direction:column;height:88vh;max-height:720px;position:relative}
#pageChat.show{animation:pageIn .45s cubic-bezier(.2,.9,.3,1.2)}
#pageChat.hide{animation:pageOut .3s ease forwards}
#pageLogin.hide{animation:pageOut .3s ease forwards}
@keyframes pageIn{from{opacity:0;transform:translateY(24px) scale(.96)}to{opacity:1;transform:translateY(0) scale(1)}}
@keyframes pageOut{from{opacity:1;transform:translateY(0) scale(1)}to{opacity:0;transform:translateY(-14px) scale(.97)}}
@keyframes float{0%,100%{transform:translateY(0)}50%{transform:translateY(-6px)}}
@keyframes pop{from{transform:scale(0.8);opacity:0}to{transform:scale(1);opacity:1}}
@keyframes slideUp{from{transform:translateY(20px) scale(.95);opacity:0}to{transform:translateY(0) scale(1);opacity:1}}
@keyframes bounceIn{0%{transform:scale(.5);opacity:0}70%{transform:scale(1.08)}100%{transform:scale(1);opacity:1}}
.logo{width:64px;height:64px;margin:0 auto 16px;background:var(--me);border-radius:18px;display:grid;place-items:center;font-size:28px;animation:float 3s infinite;transition:.3s}
.input{width:100%;background:rgba(0,0,0,0.25);border:1px solid var(--border);border-radius:14px;padding:14px 16px;color:inherit;outline:none;margin-bottom:12px;transition:.2s}
.input:focus{border-color:var(--meSolid);box-shadow:0 0 0 4px var(--meShadow)}
body.light .input{background:#fff}
.btn{width:100%;padding:14px;border:none;border-radius:14px;background:var(--me);color:#fff;font-weight:700;cursor:pointer;transition:.2s;box-shadow:0 8px 20px var(--meShadow)}
.btn:hover{transform:translateY(-2px);filter:brightness(1.1)}
.btn:active{transform:scale(0.97)}
.header{padding:14px 16px;background:rgba(0,0,0,0.2);display:flex;justify-content:space-between;align-items:center;gap:10px}
body.light .header{background:rgba(255,255,255,0.6)}
.actions{display:flex;gap:8px}
.iconBtn{width:40px;height:40px;border-radius:12px;border:1px solid var(--border);background:transparent;color:inherit;cursor:pointer;display:grid;place-items:center;font-size:16px;flex-shrink:0;transition:.2s}
.iconBtn:hover{transform:scale(1.08);background:rgba(255,255,255,.08)}
#chat{flex:1;overflow-y:auto;padding:16px;display:flex;flex-direction:column;gap:12px;scroll-behavior:smooth}
.bubble{max-width:82%;padding:10px 14px;border-radius:18px;font-size:13.5px;position:relative;word-wrap:break-word;animation:pop 0.25s ease;transition:background .3s, transform .2s}
.bubble:hover{transform:scale(1.01)}
.me{align-self:flex-end;background:var(--me);color:#fff;border-bottom-right-radius:6px;box-shadow:0 4px 14px var(--meShadow)}
.you{align-self:flex-start;background:var(--you);color:#fff;border-bottom-left-radius:6px;box-shadow:0 4px 14px var(--youShadow)}
body.light .you{background:var(--youLight);color:var(--youText);box-shadow:0 4px 14px rgba(0,0,0,.08)}
.replyTag{font-size:10px;opacity:0.7;border-left:2px solid currentColor;padding-left:6px;margin-bottom:4px}
.meta{font-size:9px;opacity:0.6;margin-top:4px;text-align:right}
.system{align-self:center;background:rgba(255,255,255,0.08);border:1px solid var(--meSolid);color:var(--meSolid);font-size:11px;padding:6px 14px;border-radius:20px;text-align:center;animation:bounceIn .3s ease}
.footer{padding:10px;background:rgba(0,0,0,0.25);display:flex;flex-direction:column;gap:8px;position:relative}
body.light .footer{background:rgba(255,255,255,0.7)}
.row{display:flex;gap:8px;align-items:center}
.footer input{flex:1;background:rgba(0,0,0,0.3);border:1px solid var(--border);border-radius:12px;padding:12px;color:inherit;outline:none;min-width:0}
.emojiBox{position:absolute;left:50%;transform:translateX(-50%);bottom:78px;width:280px;max-width:calc(100% - 20px);background:#2a2a35;border:1px solid var(--border);border-radius:18px;padding:12px;display:none;grid-template-columns:repeat(6,1fr);gap:8px;z-index:99;box-shadow:0 10px 30px rgba(0,0,0,0.5)}
body.light .emojiBox{background:#fff}
.emojiBox.show{display:grid;animation:bounceIn .25s ease}
.emojiItem{cursor:pointer;font-size:22px;text-align:center;padding:6px;border-radius:10px;transition:.15s}
.emojiItem:hover{background:rgba(168,85,247,0.2);transform:scale(1.2)}
.btnKirim{width:48px;height:48px;min-width:48px;border:none;border-radius:14px;background:var(--me);color:#fff;font-size:18px;cursor:pointer;display:grid;place-items:center;box-shadow:0 5px 15px var(--meShadow);flex-shrink:0;transition:.2s}
.btnKirim:hover{transform:scale(1.08) rotate(-8deg)}
.btnKirim:active{transform:scale(0.92)}
.toast{position:fixed;bottom:20px;left:50%;transform:translateX(-50%);background:#111;color:#fff;padding:10px 18px;border-radius:20px;font-size:12px;display:none;z-index:99;animation:slideUp .3s ease}
.toast.show{display:block}
#overlay{position:fixed;inset:0;background:rgba(0,0,0,0.6);display:none;align-items:center;justify-content:center;z-index:99}
#overlay.show{display:flex}
.modal{background:#1e1e2a;border-radius:18px;padding:20px;width:90%;max-width:320px;text-align:center;color:#fff;animation:bounceIn .3s ease}
.renameOverlay{position:fixed;inset:0;background:rgba(0,0,0,0.65);backdrop-filter:blur(6px);display:none;align-items:center;justify-content:center;z-index:200;padding:16px}
.renameOverlay.show{display:flex}
.renameCard{width:100%;max-width:360px;background:linear-gradient(180deg,#2a2340,#1c1830);border:1px solid rgba(168,85,247,0.35);border-radius:24px;padding:24px;box-shadow:0 25px 60px rgba(0,0,0,0.6);animation:slideUp .3s ease;color:#fff;position:relative;overflow:hidden}
body.light .renameCard{background:#fff;color:#111;border-color:#e9d5ff}
.renameCard::before{content:'';position:absolute;top:0;left:0;right:0;height:4px;background:var(--me)}
.renameIcon{width:64px;height:64px;margin:0 auto 12px;background:var(--me);border-radius:20px;display:grid;place-items:center;font-size:28px;box-shadow:0 10px 25px var(--meShadow)}
.renameBadge{display:inline-flex;align-items:center;gap:6px;background:rgba(255,255,255,.08);border:1px solid var(--meSolid);color:var(--meSolid);padding:6px 12px;border-radius:20px;font-size:11px;font-weight:600;margin:8px 0 16px}
.renamePreview{display:flex;align-items:center;justify-content:center;gap:10px;background:rgba(255,255,255,0.06);border:1px dashed rgba(255,255,255,0.2);border-radius:14px;padding:12px;margin:14px 0;font-size:13px}
body.light .renamePreview{background:#faf5ff;border-color:#d8b4fe}
.renameInput{width:100%;background:rgba(0,0,0,0.35);border:2px solid var(--meSolid);border-radius:14px;padding:14px 16px;color:#fff;outline:none;font-size:15px;font-weight:600;text-align:center;transition:.2s}
body.light .renameInput{background:#fff;color:#111}
.renameInput:focus{box-shadow:0 0 0 4px var(--meShadow)}
.renameWarn{background:rgba(239,68,68,0.12);border:1px solid rgba(239,68,68,0.3);color:#fca5a5;padding:10px 12px;border-radius:12px;font-size:11px;line-height:1.5;text-align:left;margin:14px 0;display:flex;gap:8px}
body.light .renameWarn{background:#fef2f2;color:#dc2626}
.renameBtnRow{display:flex;gap:10px;margin-top:6px}
.btnCancel{flex:1;padding:13px;border:1px solid rgba(255,255,255,0.2);background:transparent;color:#fff;border-radius:14px;font-weight:600;cursor:pointer}
body.light .btnCancel{color:#111;border-color:#ddd}
.btnSave{flex:2;padding:13px;border:none;background:var(--me);color:#fff;border-radius:14px;font-weight:700;cursor:pointer;box-shadow:0 8px 20px var(--meShadow)}
.btnSave:disabled{opacity:.5;cursor:not-allowed;box-shadow:none}
.progressDots{display:flex;gap:6px;justify-content:center;margin:10px 0}
.dot{width:22px;height:6px;border-radius:10px;background:rgba(255,255,255,0.15);transition:.3s}
body.light .dot{background:#e5e7eb}
.dot.active{background:var(--me)}
.dot.used{background:#ef4444}
.colorOverlay{position:fixed;inset:0;background:rgba(0,0,0,0.65);backdrop-filter:blur(6px);display:none;align-items:center;justify-content:center;z-index:200;padding:16px}
.colorOverlay.show{display:flex}
.colorCard{width:100%;max-width:340px;background:linear-gradient(180deg,#2a2340,#1c1830);border:1px solid rgba(168,85,247,.35);border-radius:24px;padding:22px;box-shadow:0 25px 60px rgba(0,0,0,.6);animation:bounceIn .3s ease;color:#fff;text-align:center;position:relative;overflow:hidden}
body.light .colorCard{background:#fff;color:#111}
.colorCard::before{content:'';position:absolute;top:0;left:0;right:0;height:4px;background:var(--me)}
.colorGrid{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin:16px 0}
.colorOpt{border:2px solid transparent;border-radius:16px;padding:10px;cursor:pointer;transition:.2s;background:rgba(255,255,255,.05)}
body.light .colorOpt{background:#f9fafb}
.colorOpt.active{border-color:var(--meSolid);transform:scale(1.05);box-shadow:0 8px 20px var(--meShadow)}
.colorOpt:hover{transform:scale(1.05)}
.colorCircle{width:42px;height:42px;border-radius:50%;margin:0 auto 6px;box-shadow:0 4px 12px rgba(0,0,0,.3)}
.colorPreview{padding:10px 14px;border-radius:18px;border-bottom-right-radius:6px;background:var(--me);color:#fff;font-size:13px;max-width:220px;margin:12px auto 0;box-shadow:0 4px 14px var(--meShadow);animation:pop .3s ease}
.colorBgPreview{height:54px;border-radius:14px;margin-top:12px;border:1px solid var(--border);display:grid;place-items:center;font-size:11px;font-weight:600;color:#fff;transition:.4s;background:radial-gradient(200px at 20% 0%, var(--glow1) 0%, transparent 60%),radial-gradient(200px at 100% 100%, var(--glow2) 0%, transparent 60%),linear-gradient(180deg,var(--bgDark2),var(--bgDark))}
</style>
</head>
<body>
<div class="card">
  <div id="pageLogin">
    <div class="logo">💬</div>
    <div style="font-weight:700;font-size:22px">Chat dengan Host</div>
    <div style="font-size:12px;opacity:0.7;margin:6px 0 20px"> Web ini bisa di gunakan untuk saran, kritik, dan chat pribadi tanpa di ketahui host</div>
    <input id="inputNama" class="input" placeholder="Nama kamu (min 3 huruf)">
    <div id="namaError" class="nama-error"><span class="icon">!</span><span id="namaErrorText">Nama minimal 3 huruf ya!</span></div>
    <div id="miniToast" class="mini-toast"></div>
    <button class="btn" onclick="masuk()">Masuk ke Room Privat</button>
    <div style="margin-top:14px;display:flex;justify-content:center;gap:10px">
      <button class="iconBtn" onclick="toggleTheme()">🌗</button>
      <button class="iconBtn" title="Warna Tema" onclick="openColorModal()">🎨</button>
      <span id="statusConn" style="font-size:10px;opacity:0.6;line-height:40px">Menghubungkan...</span>
    </div>
    <div id="infoRename" style="font-size:11px;opacity:0.6;margin-top:10px"></div>
    <div style="margin-top:14px"><div style="font-size:11px;opacity:.6;margin-bottom:6px">Preview bubble kamu:</div><div class="colorPreview" style="margin:0 auto">Halo, ini warna chatku! ✨</div></div>
  </div>
  <div id="pageChat">
    <div class="header">
      <div style="display:flex;gap:10px;align-items:center;min-width:0">
        <div id="avatar" style="width:38px;height:38px;border-radius:12px;background:var(--me);display:grid;place-items:center;font-weight:700;color:#fff;flex-shrink:0">A</div>
        <div style="min-width:0"><b id="namaAktif">-</b><div id="onlineCount" style="font-size:10px;color:#4ade80">● host online</div><div id="sisaRename" style="font-size:9px;opacity:0.6"></div></div>
      </div>
      <div class="actions">
        <button class="iconBtn" title="Ganti Tema + Background" onclick="openColorModal()">🎨</button>
        <button class="iconBtn" title="Ganti Nama" onclick="openRenameModal()">✏️</button>
        <button class="iconBtn" onclick="document.getElementById('searchBox').style.display=document.getElementById('searchBox').style.display==='none'?'block':'none'">🔍</button>
        <button class="iconBtn" onclick="toggleTheme()">🌗</button>
        <button class="iconBtn" onclick="logout()">↪️</button>
      </div>
    </div>
    <div id="searchBox" style="display:none;padding:8px 12px"><input id="inputSearch" class="input" style="margin:0" placeholder="Cari pesan..." oninput="tampilkan()"></div>
    <div id="chat"></div>
    <div class="footer">
      <div id="replyPreview" style="display:none;background:rgba(168,85,247,0.15);border-left:3px solid #a855f7;padding:6px 10px;border-radius:8px;font-size:11px"><span id="replyText"></span><span style="float:right;cursor:pointer" onclick="cancelReply()">✕</span></div>
      <div class="row">
        <button class="iconBtn" onclick="document.getElementById('fileInput').click()">📎</button>
        <input id="pesan" placeholder="Ketik pesan...">
        <button class="iconBtn" onclick="toggleEmoji()">😊</button>
        <button class="btnKirim" onclick="kirim()">➤</button>
      </div>
      <div id="emojiBox" class="emojiBox"></div>
    </div>
  </div>
</div>
<div id="colorOverlay" class="colorOverlay" onclick="if(event.target===this) closeColorModal()">
  <div class="colorCard">
    <div style="font-size:32px">🎨</div>
    <h3 style="margin:8px 0 4px;font-size:19px;font-weight:800">Warna Tema + Background</h3>
    <p style="font-size:12px;opacity:.65;margin:0">Bubble + background langsung berubah!</p>
    <div class="colorGrid" id="colorGrid"></div>
    <div class="colorPreview" id="colorPreview">Halo, ini warna baruku! ✨</div>
    <div class="colorBgPreview" id="colorBgPreview">PREVIEW BACKGROUND</div>
    <button class="btn" style="margin-top:16px" onclick="closeColorModal()">Selesai ✓</button>
  </div>
</div>
<div id="renameOverlay" class="renameOverlay" onclick="if(event.target===this) closeRenameModal()">
  <div class="renameCard">
    <div class="renameIcon">✏️</div>
    <h3 style="margin:0;font-size:19px;font-weight:800">Ganti Nama</h3>
    <p style="font-size:12px;opacity:.65;margin:6px 0 0">Ubah identitas chat kamu</p>
    <div class="renameBadge" id="renameBadge">✨ Sisa 2x hari ini</div>
    <div class="progressDots" id="progressDots"><div class="dot"></div><div class="dot"></div></div>
    <div class="renamePreview"><span id="oldNamePreview" style="opacity:.6;text-decoration:line-through">Lama</span><span>➜</span><b id="newNamePreview" style="color:#c084fc">Nama Baru</b></div>
    <input id="renameInput" class="renameInput" placeholder="Ketik nama baru..." maxlength="20" oninput="updatePreview()">
    <div style="font-size:10px;opacity:.55;margin-top:8px;text-align:left">Minimal 3 huruf • Maksimal 20 huruf</div>
    <div class="renameWarn"><span>⚠️</span><span><b>Perhatian!</b> Chat lama kamu akan <b>kehapus</b> dan kontak lama kamu di Host akan hilang. Nama baru akan langsung aktif.</span></div>
    <div class="renameBtnRow"><button class="btnCancel" onclick="closeRenameModal()">Batal</button><button class="btnSave" id="btnSaveRename" onclick="confirmRename()" disabled>Simpan Nama ✨</button></div>
  </div>
</div>
<div id="overlay" onclick="this.classList.remove('show')"><div class="modal" onclick="event.stopPropagation()"><h3>Hapus Pesan?</h3><p style="font-size:11px;opacity:0.7">Akan dihapus untuk kamu</p><button class="btn" style="background:#ff1a1a;margin-top:10px" onclick="confirmDelete()">Hapus</button></div></div>
<div id="toast" class="toast"></div>
<input type="file" id="fileInput" hidden accept="image/*" onchange="kirimGambar(this)">
<script>
const TOPIC="vortexsione_chat_2026_host_user";
let akunAktif=null, akunLower=null, semuaPesan=[], deleteKey=null, es=null, replyTo=null;
const BUBBLE_COLORS=[{id:'ungu', name:'Ungu Pink', grad:'linear-gradient(135deg,#a855f7,#ec4899)'},{id:'biru', name:'Biru Cyan', grad:'linear-gradient(135deg,#3b82f6,#06b6d4)'},{id:'hijau', name:'Hijau Mint', grad:'linear-gradient(135deg,#22c55e,#14b8a6)'},{id:'orange', name:'Orange', grad:'linear-gradient(135deg,#f97316,#ef4444)'},{id:'pink', name:'Pink', grad:'linear-gradient(135deg,#ec4899,#f43f5e)'},{id:'hitam', name:'Hitam', grad:'linear-gradient(135deg,#475569,#0f172a)'},{id:'kuning', name:'Kuning', grad:'linear-gradient(135deg,#eab308,#f97316)'}];
function norm(s){return (s||'').toString().trim().toLowerCase()}
function showToast(m){let t=document.getElementById('toast');t.innerText=m;t.classList.add('show');setTimeout(()=>t.classList.remove('show'),2000)}
function toggleTheme(){document.body.classList.toggle('light');localStorage.setItem('theme',document.body.className)}
if(localStorage.getItem('theme')) document.body.className=localStorage.getItem('theme');
function showMiniToast(pesan, type='error'){const t=document.getElementById('miniToast');if(!t) return;t.textContent=pesan;t.className='mini-toast show '+type;clearTimeout(t._timer);t._timer=setTimeout(()=> t.className='mini-toast', 2500);}
function validasiNama(nama){const input=document.getElementById('inputNama');const box=document.getElementById('namaError');const teks=document.getElementById('namaErrorText');nama=(nama||'').trim();if(!nama){if(input) input.classList.add('error');if(box) box.classList.add('show');if(teks) teks.textContent='Nama tidak boleh kosong!';showMiniToast('⚠️ Nama tidak boleh kosong!', 'error');return false;}if(nama.length<3){if(input) input.classList.add('error');if(box) box.classList.add('show');if(teks) teks.textContent=`Nama "${nama}" kurang! Minimal 3 huruf, kamu baru ${nama.length} huruf.`;showMiniToast(`❌ Nama kurang! Baru ${nama.length} huruf, minimal 3 huruf`, 'error');return false;}if(input) input.classList.remove('error');if(box) box.classList.remove('show');return true;}
function applyBubble(id){document.body.setAttribute('data-bubble', id);localStorage.setItem('bubbleColor', id);document.querySelectorAll('.colorOpt').forEach(el=>el.classList.toggle('active', el.dataset.id===id));let prev=document.getElementById('colorPreview'); if(prev){prev.style.animation='none'; prev.offsetHeight; prev.style.animation='';}}
function openColorModal(){let cur=localStorage.getItem('bubbleColor')||'ungu';let grid=document.getElementById('colorGrid');grid.innerHTML=BUBBLE_COLORS.map(c=>`<div class="colorOpt ${c.id===cur?'active':''}" data-id="${c.id}" onclick="applyBubble('${c.id}')"><div class="colorCircle" style="background:${c.grad}"></div><div style="font-size:11px;font-weight:600">${c.name}</div></div>`).join('');document.getElementById('colorOverlay').classList.add('show');}
function closeColorModal(){document.getElementById('colorOverlay').classList.remove('show'); showToast('🎨 Tema + background tersimpan!');}
if(localStorage.getItem('bubbleColor')) document.body.setAttribute('data-bubble', localStorage.getItem('bubbleColor')); else document.body.setAttribute('data-bubble','ungu');
function getRenameToday(){let today=new Date().toDateString();let arr=JSON.parse(localStorage.getItem('rename_history')||'[]');return arr.filter(x=>new Date(x).toDateString()===today);}
function updateSisaRename(){let used=getRenameToday().length; let sisa=2-used;let el=document.getElementById('sisaRename'); if(el) el.innerText='Ganti nama tersisa: '+sisa+'x';let el2=document.getElementById('infoRename'); if(el2) el2.innerText='Sisa ganti nama hari ini: '+sisa+'x (max 2x/hari)';let dots=document.querySelectorAll('#progressDots .dot');dots.forEach((d,i)=>{d.className='dot '+(i<used?'used':i<2?'active':'')});let badge=document.getElementById('renameBadge');if(badge) badge.innerText = sisa>0 ? '✨ Sisa '+sisa+'x hari ini' : '🚫 Habis! Coba besok';}
function openRenameModal(){let used=getRenameToday().length; updateSisaRename();if(used>=2){showToast('🚫 Udah 2x ganti nama hari ini, besok lagi ya!'); return;}document.getElementById('oldNamePreview').innerText=akunAktif;document.getElementById('newNamePreview').innerText='Nama Baru';document.getElementById('renameInput').value='';document.getElementById('btnSaveRename').disabled=true;document.getElementById('renameOverlay').classList.add('show');setTimeout(()=>document.getElementById('renameInput').focus(),100);}
function closeRenameModal(){document.getElementById('renameOverlay').classList.remove('show');}
function updatePreview(){let v=document.getElementById('renameInput').value.trim();document.getElementById('newNamePreview').innerText=v||'Nama Baru';document.getElementById('btnSaveRename').disabled = v.length<3 || norm(v)===akunLower;}
function confirmRename(){let baru=document.getElementById('renameInput').value.trim(); if(baru.length<3) return;let used=getRenameToday().length; if(used>=2){alert('Udah habis jatah hari ini!'); closeRenameModal(); return;}let lama=akunAktif;let all=JSON.parse(localStorage.getItem('rename_history')||'[]'); all.push(Date.now());localStorage.setItem('rename_history', JSON.stringify(all));publish({nama:'system',from:'system',type:'rename',oldNama:lama,newNama:baru,pesan:'🔄 '+lama+' ganti nama jadi '+baru+' | Kontak lama dihapus',jam:new Date().toLocaleTimeString('id-ID',{hour:'2-digit',minute:'2-digit'}),deletedBy:[]});semuaPesan=semuaPesan.filter(m=>!(m.from==='pengirim' && norm(m.nama)===norm(lama)) && !(m.from==='penerima' && norm(m.to)===norm(lama)));localStorage.setItem('pesan_'+TOPIC, JSON.stringify(semuaPesan));akunAktif=baru; akunLower=norm(baru); localStorage.setItem('akunAktif',baru); localStorage.setItem('last_login_nama',baru);document.getElementById('namaAktif').innerText=baru;document.getElementById('avatar').innerText=baru[0].toUpperCase();closeRenameModal(); updateSisaRename(); tampilkan(); showToast('✅ Nama diganti jadi '+baru);}
function handleRename(msg){if(!msg.oldNama || !msg.newNama) return;let oldL=norm(msg.oldNama); if(oldL===akunLower) return;semuaPesan=semuaPesan.filter(m=>{if(m.from==='pengirim' && norm(m.nama)===oldL) return false; if(m.from==='penerima' && norm(m.to)===oldL) return false; return true;});localStorage.setItem('pesan_'+TOPIC, JSON.stringify(semuaPesan)); tampilkan();}
function gantiNama(){openRenameModal();}
function masuk(){let nama=document.getElementById('inputNama').value.trim();if(!validasiNama(nama)) return;let namaTerakhir = localStorage.getItem('last_login_nama') || localStorage.getItem('akunAktif') || '';let isGantiNamaLogin = namaTerakhir && norm(namaTerakhir) !== norm(nama);if(isGantiNamaLogin){let used = getRenameToday().length;if(used >= 2){let input=document.getElementById('inputNama');let box=document.getElementById('namaError');let teks=document.getElementById('namaErrorText');if(input) input.classList.add('error');if(box) box.classList.add('show');if(teks) teks.textContent = `🚫 Kamu sudah ganti nama 2x hari ini! Pakai nama "${namaTerakhir}" atau tunggu besok.`;showMiniToast(`🚫 Jatah ganti nama habis! Pakai "${namaTerakhir}" lagi`, 'error');updateSisaRename();return;}let all = JSON.parse(localStorage.getItem('rename_history')||'[]'); all.push(Date.now());localStorage.setItem('rename_history', JSON.stringify(all));window._renameDariLogin = {oldNama: namaTerakhir, newNama: nama};}akunAktif=nama; akunLower=norm(nama); localStorage.setItem('akunAktif',nama); localStorage.setItem('last_login_nama',nama);let login=document.getElementById('pageLogin'); login.classList.add('hide');setTimeout(()=>{login.style.display='none'; login.classList.remove('hide');let chat=document.getElementById('pageChat'); chat.style.display='flex'; chat.classList.remove('hide'); chat.classList.add('show');document.getElementById('namaAktif').innerText=nama;document.getElementById('avatar').innerText=nama[0].toUpperCase();semuaPesan=JSON.parse(localStorage.getItem('pesan_'+TOPIC)||'[]');if(window._renameDariLogin){let r = window._renameDariLogin;semuaPesan = semuaPesan.filter(m=>!(m.from==='pengirim' && norm(m.nama)===norm(r.oldNama)) && !(m.from==='penerima' && norm(m.to)===norm(r.oldNama)));localStorage.setItem('pesan_'+TOPIC, JSON.stringify(semuaPesan));window._renameDariLogin = null;}buildEmoji(); tampilkan(); connectNtfy(); updateSisaRename();if(isGantiNamaLogin){setTimeout(()=>{publish({nama:'system',from:'system',type:'rename',oldNama:namaTerakhir,newNama:nama,pesan:'🔄 '+namaTerakhir+' ganti nama jadi '+nama+' (lewat login) | Kontak lama dihapus',jam:new Date().toLocaleTimeString('id-ID',{hour:'2-digit',minute:'2-digit'}),deletedBy:[]});}, 500);showMiniToast('✅ Nama diganti jadi '+nama, 'success');}},280);}
function connectNtfy(){document.getElementById('statusConn').innerText='✅ Terhubung';if(es) es.close();es=new EventSource('https://ntfy.sh/'+TOPIC+'/sse');es.onopen=()=>document.getElementById('onlineCount').innerText='🟢 host online - siap';es.onmessage=(e)=>{try{let outer=JSON.parse(e.data); if(!outer.message) return;let msg=JSON.parse(outer.message);if(semuaPesan.find(m=>m.id===msg.id)) return;if(msg.type==='delete'){let t=semuaPesan.find(x=>x.id===msg.targetId); if(t){if(!t.deletedBy) t.deletedBy=[]; t.deletedBy.push(msg.deleter);}}else if(msg.type==='rename'){ semuaPesan.push(msg); handleRename(msg); }else{msg.namaLower=norm(msg.nama); msg.toLower=norm(msg.to); semuaPesan.push(msg); new Audio('https://cdn.pixabay.com/audio/2022/03/15/audio_c8c8a73467.mp3').play().catch(()=>{});}localStorage.setItem('pesan_'+TOPIC, JSON.stringify(semuaPesan.slice(-500)));tampilkan();}catch{}};es.onerror=()=>{document.getElementById('onlineCount').innerText='🔴 reconnect...'; setTimeout(connectNtfy,3000);}}
function isRelevant(msg){if(!akunLower) return false;if(msg.from==='system') return true;if(msg.from==='pengirim' && norm(msg.nama)===akunLower) return true;if(msg.from==='penerima'){let to=norm(msg.to); if(to===akunLower||to==='all'||to==='semua'||!msg.to) return true;}return false;}
function tampilkan(){let box=document.getElementById('chat'); box.innerHTML='';let q=norm(document.getElementById('inputSearch').value);let filtered=semuaPesan.filter(m=>{if(m.deletedBy && m.deletedBy.includes(akunAktif)) return false;if(m.deletedBy && m.deletedBy.map(norm).includes(akunLower)) return false;if(q && norm(m.pesan).indexOf(q)===-1) return false;return isRelevant(m);});filtered.sort((a,b)=>a.timestamp-b.timestamp);filtered.forEach(item=>{if(item.from==='system'){box.innerHTML+=`<div style="width:100%;display:flex;justify-content:center"><div class="system">${item.pesan}</div></div>`;}else{let isMe=item.from==='pengirim';let replyHtml2=item.reply?`<div class="replyTag">↪ ${item.reply}</div>`:'';let imgHtml=item.image?`<img src="${item.image}" style="max-width:100%;border-radius:12px;margin-top:6px">`:'';box.innerHTML+=`<div style="width:100%;display:flex;${isMe?'justify-content:flex-end':'justify-content:flex-start'}"><div class="bubble ${isMe?'me':'you'}" onclick="setReply('${item.id}','${(item.pesan||'').replace(/'/g,'')}')" oncontextmenu="openDel('${item.id}');return false;">${replyHtml2}${item.pesan}${imgHtml}<div class="meta">${item.jam} ${isMe?'✓✓':''}</div></div></div>`;}});if(filtered.length===0) box.innerHTML=`<div style="text-align:center;opacity:0.4;margin-top:40px">Belum ada chat, sapa host dulu 👋</div>`;box.scrollTop=box.scrollHeight;}
function publish(msg){msg.id=Date.now()+'_'+Math.random().toString(36).substr(2,6); msg.timestamp=Date.now();fetch('https://ntfy.sh/'+TOPIC,{method:'POST',body:JSON.stringify(msg)});semuaPesan.push(msg); localStorage.setItem('pesan_'+TOPIC, JSON.stringify(semuaPesan.slice(-500))); tampilkan();}
function kirim(){let p=document.getElementById('pesan').value.trim(); if(!p) return;publish({nama:akunAktif,pesan:p,jam:new Date().toLocaleTimeString('id-ID',{hour:'2-digit',minute:'2-digit'}),from:'pengirim',to:'host',reply:replyTo,deletedBy:[]});document.getElementById('pesan').value=''; cancelReply();}
function kirimGambar(input){let file=input.files[0]; if(!file) return;let r=new FileReader(); r.onload=()=>{publish({nama:akunAktif,pesan:'📷 Gambar',image:r.result,jam:new Date().toLocaleTimeString('id-ID',{hour:'2-digit',minute:'2-digit'}),from:'pengirim',to:'host',deletedBy:[]})}; r.readAsDataURL(file);}
function buildEmoji(){let e=["😀","😂","❤️","🔥","👍","😭","😍","🙏","✨","💀","😎","🥺"]; let box=document.getElementById('emojiBox'); box.innerHTML=e.map(x=>`<span class="emojiItem" onclick="addEmoji('${x}')">${x}</span>`).join('');}
function toggleEmoji(){document.getElementById('emojiBox').classList.toggle('show')}
function addEmoji(e){document.getElementById('pesan').value+=e; toggleEmoji(); document.getElementById('pesan').focus()}
function setReply(id,text){replyTo=text.slice(0,40); document.getElementById('replyText').innerText='Balas: '+replyTo; document.getElementById('replyPreview').style.display='block';}
function cancelReply(){replyTo=null; document.getElementById('replyPreview').style.display='none'}
function openDel(id){deleteKey=id; document.getElementById('overlay').classList.add('show')}
function confirmDelete(){let idx=semuaPesan.findIndex(m=>m.id===deleteKey);if(idx>-1){if(!semuaPesan[idx].deletedBy) semuaPesan[idx].deletedBy=[]; semuaPesan[idx].deletedBy.push(akunAktif,akunLower);publish({nama:'system',from:'system',type:'delete',targetId:deleteKey,deleter:akunAktif,pesan:akunAktif+' menghapus',jam:new Date().toLocaleTimeString('id-ID'),deletedBy:[],timestamp:Date.now(),id:Date.now()+'_del'})}localStorage.setItem('pesan_'+TOPIC, JSON.stringify(semuaPesan.slice(-500)));document.getElementById('overlay').classList.remove('show'); showToast('Dihapus'); tampilkan();}
function logout(){let chat=document.getElementById('pageChat'); chat.classList.add('hide');setTimeout(()=>{akunAktif=null; if(es) es.close();chat.style.display='none'; chat.classList.remove('hide','show');let login=document.getElementById('pageLogin'); login.style.display='block'; login.style.animation='pageIn .45s ease';if(localStorage.getItem('last_login_nama')) document.getElementById('inputNama').value = localStorage.getItem('last_login_nama');updateSisaRename();},280);}
document.getElementById('pesan').addEventListener('keydown',e=>{if(e.key==='Enter') kirim()});
document.getElementById('renameInput').addEventListener('keydown',e=>{if(e.key==='Enter') confirmRename()});
document.getElementById('inputNama').addEventListener('input',function(){if(this.value.trim().length>=3){this.classList.remove('error');document.getElementById('namaError')?.classList.remove('show');}});
document.getElementById('inputNama').addEventListener('keydown',e=>{if(e.key==='Enter') masuk()});
document.addEventListener('click',e=>{let box=document.getElementById('emojiBox'); if(box && box.classList.contains('show') && !e.target.closest('#emojiBox') && !e.target.closest('.iconBtn')) box.classList.remove('show')});
window.onload=()=>{let s=localStorage.getItem('last_login_nama') || localStorage.getItem('akunAktif'); if(s){document.getElementById('inputNama').value=s} updateSisaRename();}
</script>
</body>
</html>
