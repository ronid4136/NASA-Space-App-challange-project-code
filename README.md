<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ASTROFORGE — Left Behind, Not Forgotten | NASA Space Apps Challenge</title>

<!-- Fonts & Three.js -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@700;800;900&family=Inter:wght@400;500;600;700;800&family=Space+Grotesk:wght@500;600;700&display=swap" rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<script>window.__threeReady=typeof THREE!=='undefined';</script>
<script>if(typeof THREE==='undefined'){document.write('<script src="https://cdn.jsdelivr.net/npm/three@0.128.0/build/three.min.js"><\/script>');}</script>

<style>
:root {
    --bg-dark: #020610;
    --panel-bg: rgba(11, 22, 40, 0.95);
    --panel-border: rgba(99, 202, 255, 0.35);
    --neon-blue: #38bdf8;
    --orange: #fb923c;
    --green: #4ade80;
    --red: #f87171;
    --purple: #c084fc;
    --gold: #facc15;
    --text-main: #f8fafc;
    --text-muted: #cbd5e1;
}

* { box-sizing: border-box; margin: 0; padding: 0; }

body {
    background-color: var(--bg-dark);
    color: var(--text-main);
    font-family: 'Space Grotesk', sans-serif;
    overflow-x: hidden;
    line-height: 1.6;
    font-size: 17px;
}

.audience-banner {
    text-align: center;
    padding: 8px 15px 0 15px;
    font-size: 11px;
    font-weight: 700;
    letter-spacing: 1.2px;
    color: var(--text-muted);
    font-family: 'Orbitron', sans-serif;
    opacity: 0.85;
}

header {
    position: sticky;
    top: 0;
    height: 75px;
    z-index: 1000;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0 3%;
    background: rgba(2, 6, 16, 0.95);
    backdrop-filter: blur(15px);
    border-bottom: 1px solid var(--panel-border);
}

.logo { 
    font-family: 'Orbitron', sans-serif;
    font-size: 22px; 
    font-weight: 900; 
    letter-spacing: 2px; 
    color: #ffffff;
}
.logo span { color: var(--neon-blue); }

nav { 
    display: flex; 
    gap: 12px; 
    align-items: center; 
    overflow-x: auto;
    padding: 5px 0;
}

nav a { 
    color: var(--text-muted); 
    text-decoration: none; 
    font-size: 12px; 
    font-weight: 700; 
    transition: 0.3s; 
    text-transform: uppercase;
    font-family: 'Inter', sans-serif;
    display: inline-flex;
    align-items: center;
    gap: 5px;
    white-space: nowrap;
}
nav a:hover { color: var(--neon-blue); }

.control-box { display: flex; align-items: center; gap: 10px; flex-shrink: 0; }

.audio-btn {
    background: rgba(248, 113, 113, 0.15);
    border: 1px solid var(--red);
    color: var(--red);
    padding: 6px 12px;
    border-radius: 20px;
    font-size: 11px;
    font-weight: 800;
    cursor: pointer;
    font-family: 'Orbitron', sans-serif;
}
.audio-btn.on {
    background: rgba(56, 189, 248, 0.15);
    border-color: var(--neon-blue);
    color: var(--neon-blue);
}

.lang-selector {
    background: var(--panel-bg);
    color: var(--neon-blue);
    border: 1px solid var(--panel-border);
    padding: 6px 8px;
    border-radius: 6px;
    font-size: 12px;
    font-weight: 700;
    outline: none;
    cursor: pointer;
}

/* HERO SECTION */
.hero-wrapper {
    display: grid;
    grid-template-columns: 1fr 340px;
    gap: 30px;
    max-width: 1350px;
    margin: 0 auto;
    padding: 25px 20px 35px 20px;
    align-items: start;
}

.hero-main { 
    background: radial-gradient(circle at top left, rgba(56, 189, 248, 0.08), transparent 70%);
    padding: 24px;
    border-radius: 20px;
    border: 1px solid rgba(56, 189, 248, 0.15);
}

.badge-group { display: flex; gap: 12px; margin-bottom: 14px; flex-wrap: wrap; }
.badge {
    background: rgba(56, 189, 248, 0.12);
    border: 1px solid var(--neon-blue);
    color: var(--neon-blue);
    font-size: 12px;
    padding: 5px 14px;
    border-radius: 20px;
    text-transform: uppercase;
    font-weight: 800;
    font-family: 'Orbitron', sans-serif;
}
.badge-stem { background: rgba(192, 132, 252, 0.12); border-color: var(--purple); color: var(--purple); }

h1 { 
    font-family: 'Inter', sans-serif;
    font-size: clamp(18px, 2.4vw, 30px); 
    font-weight: 800;
    line-height: 1.3;
    margin-bottom: 14px; 
    color: #ffffff;
    text-transform: uppercase;
}
h1 span { 
    background: linear-gradient(90deg, #38bdf8, #c084fc, #fb923c); 
    -webkit-background-clip: text; 
    -webkit-text-fill-color: transparent; 
}

.hero-main p { color: var(--text-muted); font-size: 16px; margin-bottom: 20px; font-weight: 500; }

.solar-canvas-box {
    width: 100%;
    height: 310px;
    background: rgba(0, 0, 0, 0.95);
    border: 1.5px solid var(--panel-border);
    border-radius: 16px;
    position: relative;
    margin-bottom: 22px;
    overflow: hidden;
    box-shadow: 0 0 35px rgba(56, 189, 248, 0.3);
}
#solarCanvas { width: 100%; height: 100%; }

.cta-group { display: flex; gap: 12px; flex-wrap: wrap; }
.btn { 
    padding: 12px 22px; 
    border-radius: 8px; 
    font-weight: 800; 
    font-size: 13px; 
    cursor: pointer; 
    border: none; 
    transition: 0.2s; 
    text-decoration: none; 
    display: inline-flex; 
    align-items: center; 
    justify-content: center;
    gap: 8px; 
    font-family: 'Orbitron', sans-serif;
}
.btn-primary { background: var(--neon-blue); color: #000; }
.btn-primary:hover { opacity: 0.9; transform: translateY(-2px); }
.btn-outline { background: transparent; color: var(--text-main); border: 1px solid var(--panel-border); }
.btn-outline:hover { border-color: var(--neon-blue); color: var(--neon-blue); background: rgba(56, 189, 248, 0.1); }

/* SIDE PANEL (MOON/MARS 3D CARDS) */
.side-3d-panel {
    background: var(--panel-bg);
    border: 1px solid var(--panel-border);
    border-radius: 16px;
    padding: 18px;
    display: flex;
    flex-direction: column;
    gap: 16px;
}
.side-3d-card {
    background: rgba(0, 0, 0, 0.6);
    border: 1px solid rgba(255,255,255,0.12);
    border-radius: 12px;
    padding: 15px;
    text-align: center;
    cursor: pointer;
    transition: 0.3s;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 10px;
}
.side-3d-card:hover {
    border-color: var(--neon-blue);
    transform: translateY(-2px);
}
.side-mini-canvas {
    width: 110px;
    height: 110px;
    border-radius: 50%;
    overflow: hidden;
    background: #000;
    border: 2px solid var(--neon-blue);
    box-shadow: 0 0 15px rgba(56, 189, 248, 0.4);
}
.side-3d-title { 
    font-family: 'Orbitron', sans-serif; 
    font-size: 14px; 
    font-weight: 800; 
    color: var(--neon-blue); 
    margin-bottom: 2px; 
}
.side-click-hint { font-size: 11px; color: var(--orange); font-weight: 700; }

section { padding: 50px 4%; max-width: 1350px; margin: 0 auto; border-bottom: 1px solid rgba(255,255,255,0.08); }
.section-head { text-align: center; margin-bottom: 30px; }
.section-head h2 { font-family: 'Orbitron', sans-serif; font-size: 24px; margin-bottom: 8px; color: var(--text-main); }
.section-head p { color: var(--text-muted); font-size: 15px; }

.hardware-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(340px, 1fr)); gap: 20px; }

.card-inline {
    background: var(--panel-bg);
    border: 1px solid var(--panel-border);
    border-radius: 14px;
    cursor: pointer;
    display: flex;
    flex-direction: column;
    padding: 24px;
    gap: 14px;
    transition: 0.3s;
}
.card-inline:hover { transform: translateY(-3px); border-color: var(--neon-blue); }

.card-content-side { flex-grow: 1; }
.card-title { font-family: 'Orbitron', sans-serif; font-size: 17px; font-weight: 800; color: #ffffff; margin-bottom: 8px; }
.card-sub { font-size: 11px; color: var(--orange); font-weight: 800; margin-bottom: 6px; font-family: 'Orbitron', sans-serif; }
.card-desc { font-size: 14px; color: #cbd5e1; margin-bottom: 14px; font-weight: 500; }


/* HARDWARE EXPLORER - SIMPLE CARD + FULL DETAIL MODAL */
.card-inline { overflow:hidden; padding:0; gap:0; }
.card-inline .card-content-side { padding:18px 18px 20px; }
.hardware-photo-wrap { height:235px; margin:0; border-radius:14px 14px 0 0; }
.hardware-photo { transition:transform .45s ease; }
.card-inline:hover .hardware-photo { transform:scale(1.045); }

/* COMPACT HARDWARE CARDS */
.card-inline{min-height:0 !important}
.card-inline .hardware-photo-wrap{height:175px !important}
.card-inline .card-content-side{padding:10px 12px 12px !important}
.card-inline .card-sub{font-size:9px !important;margin-bottom:4px !important}
.card-inline .card-title{font-size:15px !important;line-height:1.25 !important;margin-bottom:5px !important}
.card-inline .hardware-simple-desc{font-size:11px !important;line-height:1.4 !important;display:-webkit-box;-webkit-line-clamp:2;-webkit-box-orient:vertical;overflow:hidden;margin-bottom:7px !important}
.card-inline .detail-btn{padding:7px 10px !important;font-size:10px !important;width:100%}

.hardware-simple-desc { color:#cbd5e1; font-size:13px; line-height:1.55; margin:8px 0 12px; }
.detail-btn { width:100%; justify-content:center; }
.modal-hardware-photo-wrap { width:100%; height:360px; margin:4px 0 18px; position:relative; overflow:hidden; border-radius:12px; border:1px solid var(--panel-border); background:#020610; }
.modal-hardware-photo { width:100%; height:100%; object-fit:cover; display:block; }
.modal-photo-credit { position:absolute; left:12px; bottom:12px; background:rgba(0,0,0,.78); color:#fff; border:1px solid rgba(255,255,255,.2); padding:6px 10px; border-radius:7px; font-size:10px; font-family:'Orbitron',sans-serif; font-weight:800; }
.modal-overview { background:linear-gradient(135deg,rgba(56,189,248,.10),rgba(192,132,252,.07)); border:1px solid rgba(56,189,248,.22); border-radius:10px; padding:14px 16px; margin-bottom:16px; color:#e2e8f0; font-size:14px; line-height:1.65; }
.modal-overview strong { color:var(--neon-blue); font-family:'Orbitron',sans-serif; font-size:11px; display:block; margin-bottom:5px; }
@media(max-width:700px){ .hardware-photo-wrap{height:210px;} .modal-hardware-photo-wrap{height:240px;} }


/* FINAL COMPACT HARDWARE LAYOUT */
.hardware-grid{grid-template-columns:repeat(auto-fit,minmax(280px,1fr)) !important;gap:14px !important;max-width:1120px;margin-left:auto;margin-right:auto}
.card-inline .card-sub{display:none !important}
.card-inline .hardware-photo-wrap{height:165px !important}
.card-inline .card-content-side{padding:9px 11px 11px !important}
.card-inline .card-title{font-size:14px !important;line-height:1.25 !important;margin-bottom:4px !important}
.card-inline .hardware-simple-desc{font-size:10.5px !important;line-height:1.35 !important;-webkit-line-clamp:2;margin:4px 0 7px !important}
.card-inline .detail-btn{padding:6px 9px !important;font-size:10px !important}

/* HARDWARE IMAGE GALLERY */
.gallery-toolbar{display:flex;align-items:center;justify-content:space-between;gap:14px;flex-wrap:wrap;margin:0 auto 20px;max-width:1100px;padding:12px 14px;border:1px solid rgba(56,189,248,.18);background:rgba(8,18,34,.72);border-radius:12px}
.gallery-live{font-family:'Orbitron',sans-serif;font-size:11px;font-weight:800;color:var(--green);letter-spacing:.8px;display:flex;align-items:center;gap:8px}
.hardware-gallery-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(190px,1fr));gap:12px;max-width:1120px;margin:0 auto}
.gallery-hw-card{position:relative;overflow:hidden;min-height:225px;border:1px solid var(--panel-border);border-radius:14px;background:linear-gradient(180deg,rgba(12,24,44,.98),rgba(4,10,20,.98));cursor:pointer;transition:.3s;box-shadow:0 12px 30px rgba(0,0,0,.25)}
.gallery-hw-card:hover{transform:translateY(-5px);border-color:var(--neon-blue);box-shadow:0 16px 38px rgba(56,189,248,.14)}
.gallery-hw-photo{width:100%;height:125px;object-fit:cover;display:block;background:#020610}
.gallery-hw-body{padding:13px 14px 15px}
.gallery-hw-tag{font-size:10px;font-weight:800;color:var(--orange);font-family:'Orbitron',sans-serif;letter-spacing:.6px;margin-bottom:6px}
.gallery-hw-name{font-family:'Orbitron',sans-serif;color:#fff;font-size:13px;line-height:1.45;font-weight:800}
.gallery-hw-click{margin-top:10px;font-size:11px;color:var(--neon-blue);font-weight:800}
.gallery-hw-loading{height:125px;display:flex;align-items:center;justify-content:center;color:#64748b;font-size:11px;font-family:'Orbitron',sans-serif;padding:10px;text-align:center}
.add-hardware-content{max-width:650px}
.add-hw-form{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.add-hw-form input,.add-hw-form select,.add-hw-form textarea{width:100%;box-sizing:border-box;background:#07111f;border:1px solid rgba(148,163,184,.25);color:#fff;border-radius:8px;padding:11px;font-family:inherit;font-size:13px}
.add-hw-form textarea{grid-column:1/-1;min-height:90px;resize:vertical}
@media(max-width:650px){.add-hw-form{grid-template-columns:1fr}.add-hw-form textarea{grid-column:auto}.gallery-toolbar{align-items:stretch}.gallery-toolbar .btn{width:100%}}


/* STUDENT-FIRST HARDWARE VIDEO EXPERIENCE */
.hardware-video-zone{max-width:1120px;margin:24px auto 0;padding:20px;border:1px solid rgba(56,189,248,.18);border-radius:18px;background:linear-gradient(135deg,rgba(7,17,31,.96),rgba(8,13,28,.92));box-shadow:0 18px 45px rgba(0,0,0,.22);position:relative;overflow:hidden}
.hardware-video-zone:before{content:"";position:absolute;inset:-80px auto auto -80px;width:190px;height:190px;background:radial-gradient(circle,rgba(56,189,248,.16),transparent 70%);pointer-events:none}
.hardware-video-zone.mars-zone:before{background:radial-gradient(circle,rgba(249,115,22,.16),transparent 70%)}
.video-zone-head{display:flex;align-items:center;justify-content:space-between;gap:12px;flex-wrap:wrap;margin-bottom:15px;position:relative;z-index:1}
.video-zone-title{font-family:'Orbitron',sans-serif;color:#fff;font-size:16px;font-weight:900}
.video-zone-sub{color:#94a3b8;font-size:11px;margin-top:3px}
.video-zone-pill{font-family:'Orbitron',sans-serif;font-size:9px;color:var(--green);border:1px solid rgba(34,197,94,.25);background:rgba(34,197,94,.07);padding:7px 10px;border-radius:999px;font-weight:800;letter-spacing:.5px}
.hardware-video-grid{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:12px;position:relative;z-index:1}
.hardware-video-card{min-width:0;border:1px solid rgba(148,163,184,.16);border-radius:14px;overflow:hidden;background:rgba(2,6,23,.72);transition:.28s;box-shadow:0 10px 28px rgba(0,0,0,.18)}
.hardware-video-card:hover{transform:translateY(-4px);border-color:rgba(56,189,248,.48);box-shadow:0 16px 34px rgba(56,189,248,.10)}
.video-thumb{height:125px;position:relative;background-size:cover;background-position:center;overflow:hidden}
.video-thumb:after{content:"";position:absolute;inset:0;background:linear-gradient(180deg,rgba(0,0,0,.08),rgba(0,0,0,.7))}
.video-play{position:absolute;left:50%;top:50%;transform:translate(-50%,-50%);width:48px;height:48px;border-radius:50%;display:flex;align-items:center;justify-content:center;background:rgba(2,6,23,.78);border:1px solid rgba(255,255,255,.28);color:#fff;font-size:20px;box-shadow:0 0 22px rgba(56,189,248,.25);z-index:2}
.video-thumb-label{position:absolute;left:9px;bottom:8px;z-index:2;font-size:9px;color:#fff;font-family:'Orbitron',sans-serif;font-weight:800;background:rgba(2,6,23,.72);padding:5px 7px;border-radius:6px}
.video-card-body{padding:11px 12px 12px}
.video-card-title{font-family:'Orbitron',sans-serif;color:#fff;font-size:11px;font-weight:800;line-height:1.4;min-height:31px}
.video-card-status{font-size:10px;color:#94a3b8;margin:6px 0 9px;line-height:1.4}
.video-watch-btn{width:100%;padding:7px 9px!important;font-size:10px!important;justify-content:center}
.hardware-status-row{display:flex;gap:6px;flex-wrap:wrap;margin:5px 0 7px}
.hw-status-badge{font-size:9px;font-family:'Orbitron',sans-serif;font-weight:900;border-radius:999px;padding:4px 7px;border:1px solid rgba(148,163,184,.18);background:rgba(148,163,184,.06);color:#cbd5e1}
.hw-status-badge.active{color:#86efac;border-color:rgba(34,197,94,.28);background:rgba(34,197,94,.08)}
.hw-status-badge.inactive{color:#fca5a5;border-color:rgba(239,68,68,.25);background:rgba(239,68,68,.07)}
.hw-status-badge.passive{color:#7dd3fc;border-color:rgba(56,189,248,.25);background:rgba(56,189,248,.07)}
.modal-video-panel{margin-top:16px;padding:13px;border-radius:12px;border:1px solid rgba(56,189,248,.18);background:rgba(56,189,248,.045)}
.modal-video-panel .modal-video-title{font-family:'Orbitron',sans-serif;color:#fff;font-size:12px;font-weight:800;margin-bottom:9px}
.modal-video-frame{width:100%;aspect-ratio:16/9;border:0;border-radius:9px;background:#000;display:block}
.modal-status-strip{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin:12px 0}
.modal-status-chip{padding:9px 10px;border-radius:9px;background:#07111f;border:1px solid rgba(148,163,184,.16)}
.modal-status-chip span{display:block;font-size:9px;color:#64748b;font-family:'Orbitron',sans-serif;font-weight:800;margin-bottom:3px}
.modal-status-chip strong{font-size:12px;color:#e2e8f0}
@media(max-width:850px){.hardware-video-grid{grid-template-columns:1fr 1fr}}
@media(max-width:560px){.hardware-video-grid{grid-template-columns:1fr}.hardware-video-zone{padding:14px}.modal-status-strip{grid-template-columns:1fr}}

/* ROBUST 3D SOLAR SYSTEM */
.solar-canvas-box { min-height:310px; background:radial-gradient(circle at 50% 50%,rgba(12,28,55,.9),rgba(0,0,0,.98) 72%); }
#solarCanvas { width:100%; height:310px; min-height:310px; position:relative; }
#solarCanvas canvas { display:block; width:100% !important; height:100% !important; }
.solar-fallback { position:absolute; inset:0; display:flex; align-items:center; justify-content:center; text-align:center; color:#94a3b8; font-size:13px; padding:20px; }

/* MODALS */
.modal {
    position: fixed; top: 0; left: 0; width: 100%; height: 100%;
    background: rgba(0,0,0,0.92); backdrop-filter: blur(15px);
    display: none; justify-content: center; align-items: center; z-index: 2000; padding: 20px;
}
.modal-content {
    background: #091322; border: 1.5px solid var(--neon-blue);
    border-radius: 16px; max-width: 900px; width: 100%; max-height: 90vh;
    overflow-y: auto; padding: 25px; position: relative;
}
.close-modal { position: absolute; top: 14px; right: 20px; font-size: 32px; color: var(--text-muted); cursor: pointer; }
.close-modal:hover { color: var(--red); }

.modal-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr)); gap: 16px; margin-top: 18px; }
.modal-field { background: rgba(15, 23, 42, 0.9); padding: 18px; border-radius: 10px; border-left: 4px solid var(--neon-blue); }
.modal-field label { font-family: 'Orbitron', sans-serif; font-size: 11px; text-transform: uppercase; color: var(--neon-blue); font-weight: 800; display: block; margin-bottom: 6px; }
.modal-field p { font-size: 14px; color: #ffffff; font-weight: 500; line-height: 1.5; }

/* 3D HARDWARE CANVAS IN MODAL */
.modal-hardware-photo-wrap { width:100%; height:360px; margin-bottom:18px; position:relative; overflow:hidden; border-radius:14px; border:1px solid var(--panel-border); background:#020610; }
.modal-hardware-photo { width:100%; height:100%; object-fit:cover; display:block; }
.modal-photo-credit { position:absolute; left:12px; bottom:12px; background:rgba(0,0,0,.75); color:#fff; border:1px solid rgba(255,255,255,.2); padding:6px 10px; border-radius:7px; font-size:10px; font-family:'Orbitron',sans-serif; font-weight:800; }
.hardware-info-strip { display:grid; grid-template-columns:repeat(2,minmax(0,1fr)); gap:8px; margin-top:10px; margin-bottom:4px; }
.hardware-info-chip { background:rgba(56,189,248,.07); border:1px solid rgba(56,189,248,.18); border-radius:8px; padding:8px 10px; font-size:12px; color:#dbeafe; }
.hardware-info-chip strong { color:var(--neon-blue); font-family:'Orbitron',sans-serif; font-size:10px; display:block; margin-bottom:2px; }
@media(max-width:600px){ .modal-hardware-photo-wrap{height:240px;} .hardware-info-strip{grid-template-columns:1fr;} }

.modal-actions { display: flex; gap: 12px; flex-wrap: wrap; margin-bottom: 18px; }


/* COMPACT MISSION TIMELINE */
.timeline-compact-box{
    background:var(--panel-bg); border:1px solid var(--panel-border);
    border-radius:12px; padding:20px; text-align:center; max-width:760px; margin:0 auto;
}
.timeline-compact-box p{color:var(--text-muted); font-size:14px; margin:6px 0 16px;}
.mission-modal-grid{display:grid; grid-template-columns:repeat(auto-fit,minmax(260px,1fr)); gap:16px; margin-top:18px;}
.mission-card{background:rgba(15,23,42,.92); border:1px solid var(--panel-border); border-radius:12px; overflow:hidden;}
.mission-card img{width:100%; height:150px; object-fit:cover; display:block; background:#020617;}
.mission-card-body{padding:14px;}
.mission-card-body .mission-year{font-family:'Orbitron',sans-serif; color:var(--orange); font-size:11px; font-weight:800;}
.mission-card-body h3{font-family:'Orbitron',sans-serif; color:var(--neon-blue); font-size:15px; margin:5px 0;}
.mission-card-body p{font-size:13px; color:#fff; line-height:1.5; margin:5px 0;}
.mission-card-body .mission-meta{color:var(--text-muted); font-size:12px;}

.timeline { position: relative; border-left: 2px solid var(--panel-border); margin: 10px 0 0 10px; padding-left: 18px; }
.timeline-item { margin-bottom: 22px; position: relative; }
.timeline-item::before {
    content: ''; position: absolute; left: -25px; top: 5px; width: 14px; height: 14px;
    border-radius: 50%; background: var(--neon-blue); border: 2px solid var(--bg-dark);
}
.timeline-content { background: var(--panel-bg); border: 1px solid var(--panel-border); padding: 18px; border-radius: 10px; }

.telemetry-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 18px; }
.telemetry-card { background: var(--panel-bg); border: 1px solid var(--panel-border); border-radius: 12px; padding: 20px; }

.game-container { background: var(--panel-bg); border: 1px solid var(--purple); border-radius: 14px; padding: 25px; max-width: 850px; margin: 0 auto; }
.game-step { display: none; }
.game-step.active { display: block; }
.option-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(160px, 1fr)); gap: 14px; margin-top: 18px; }
.option-card {
    background: rgba(255,255,255,0.03); border: 1px solid var(--panel-border);
    padding: 16px; border-radius: 8px; text-align: center; cursor: pointer;
}
.option-card:hover, .option-card.selected { border-color: var(--purple); background: rgba(192, 132, 252, 0.18); }

.quiz-container { background: var(--panel-bg); border: 1px solid var(--panel-border); border-radius: 14px; padding: 25px; max-width: 800px; margin: 0 auto; }
.quiz-opt { width: 100%; padding: 12px 16px; margin-top: 10px; background: rgba(255,255,255,0.03); border: 1px solid var(--panel-border); color: #ffffff; border-radius: 8px; text-align: left; cursor: pointer; font-size: 15px; font-weight: 600; }
.quiz-opt:hover { border-color: var(--neon-blue); background: rgba(56, 189, 248, 0.15); }

footer { text-align: center; padding: 30px 4%; border-top: 1px solid var(--panel-border); color: var(--text-muted); font-size: 14px; }
.team-simple-btn { background: transparent; color: var(--neon-blue); border: none; font-size: 14px; font-weight: 600; cursor: pointer; margin-top: 8px; text-decoration: underline; }

.team-leader-center {
    text-align: center; background: rgba(56, 189, 248, 0.12);
    border: 1.5px solid var(--neon-blue); padding: 16px; border-radius: 12px; margin-bottom: 18px;
}
.team-leader-center h3 { font-family: 'Orbitron', sans-serif; font-size: 18px; color: #ffffff; margin-bottom: 4px; }
.team-leader-center p { font-size: 12px; color: var(--gold); font-weight: 800; letter-spacing: 1px; }

.team-members-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
.team-member-card { background: rgba(15, 23, 42, 0.8); padding: 12px 14px; border-radius: 8px; border-left: 3.5px solid var(--purple); font-size: 14px; color: #ffffff; }

.live-indicator {
    display: inline-flex; align-items: center; gap: 6px; background: rgba(74, 222, 128, 0.15);
    border: 1px solid var(--green); color: var(--green); padding: 4px 10px; border-radius: 12px; font-size: 11px; font-weight: 800; font-family: 'Orbitron', sans-serif;
}
.live-dot { width: 8px; height: 8px; background: var(--green); border-radius: 50%; box-shadow: 0 0 10px var(--green); animation: pulse 1s infinite ease-in-out; }
@keyframes pulse { 0% { opacity: 1; transform: scale(1); } 50% { opacity: 0.3; transform: scale(0.8); } 100% { opacity: 1; transform: scale(1); } }

.highlight-text { background: rgba(250, 204, 21, 0.3); border-bottom: 2px solid var(--gold); transition: 0.2s; }

/* ===== PHOTO-ENHANCED HARDWARE CARDS ===== */
.hardware-photo-wrap{
    position:relative;
    width:100%;
    height:210px;
    overflow:hidden;
    border-radius:14px;
    background:
      radial-gradient(circle at 50% 20%, rgba(56,189,248,.18), transparent 55%),
      #02050b;
    border:1px solid rgba(56,189,248,.20);
}
.hardware-photo{
    width:100%;
    height:100%;
    display:block;
    object-fit:cover;
    object-position:center;
    opacity:.96;
    transform:scale(1.01);
    transition:transform .55s ease, opacity .35s ease, filter .35s ease;
}
.card-inline:hover .hardware-photo{
    transform:scale(1.07);
    opacity:1;
    filter:saturate(1.12) contrast(1.04);
}
.photo-shade{
    position:absolute;
    inset:0;
    background:linear-gradient(180deg, rgba(2,6,16,.04) 25%, rgba(2,6,16,.82) 100%);
    pointer-events:none;
}
.photo-badge{
    position:absolute;
    top:11px;
    left:11px;
    z-index:2;
    padding:5px 9px;
    border-radius:999px;
    font:800 10px 'Orbitron',sans-serif;
    letter-spacing:.6px;
    color:#fff;
    background:rgba(2,6,16,.72);
    border:1px solid rgba(255,255,255,.25);
    backdrop-filter:blur(8px);
}
.photo-credit{
    position:absolute;
    right:10px;
    bottom:9px;
    z-index:2;
    padding:4px 7px;
    border-radius:6px;
    font:700 9px 'Inter',sans-serif;
    color:rgba(255,255,255,.82);
    background:rgba(2,6,16,.55);
    backdrop-filter:blur(5px);
}
.card-inline .card-content-side{padding-top:2px;}
.card-inline .card-title{line-height:1.35;}
.photo-loading{
    display:flex;
    align-items:center;
    justify-content:center;
    height:100%;
    color:var(--text-muted);
    font:700 10px 'Orbitron',sans-serif;
    letter-spacing:.7px;
}
.photo-error{
    display:flex;
    align-items:center;
    justify-content:center;
    height:100%;
    padding:20px;
    text-align:center;
    color:var(--text-muted);
    font-size:12px;
}
.nasa-photo-link{
    display:inline-flex;
    align-items:center;
    gap:6px;
    margin-top:8px;
    color:var(--neon-blue);
    font-size:11px;
    font-weight:800;
    text-decoration:none;
}
.nasa-photo-link:hover{text-decoration:underline;}


@media (max-width: 700px){
    .hardware-photo-wrap{height:190px;}
}



/* ===== COMPACT HERO + 2D EARTH/MOON/MARS ORBIT MAP ===== */
.student-hero{display:grid;grid-template-columns:minmax(0,1fr) 300px;align-items:center;gap:28px;padding:34px 34px 30px;}
.student-hero-copy{position:relative;z-index:2;max-width:760px;}
.hero-mini-title{font:700 13px 'Orbitron',sans-serif;letter-spacing:1.8px;color:#cbd5e1;margin-top:16px;text-transform:uppercase;}
.hero-mini-title span{color:var(--neon-blue);}
.student-hero h1{font-size:clamp(32px,4.6vw,56px);line-height:1.04;margin:9px 0 10px;letter-spacing:-1.5px;}
.student-hero p{font-size:14px;line-height:1.6;margin-bottom:18px;max-width:560px;}
.mini-solar-card{position:relative;z-index:2;border:1px solid rgba(56,189,248,.20);border-radius:22px;padding:13px;background:linear-gradient(145deg,rgba(10,22,40,.94),rgba(2,7,16,.98));box-shadow:0 15px 40px rgba(0,0,0,.32),inset 0 0 35px rgba(56,189,248,.035);}
.mini-solar-head{display:flex;align-items:center;justify-content:space-between;padding:2px 4px 8px;font:800 9px 'Orbitron',sans-serif;letter-spacing:1px;color:#e2e8f0;}
.mini-solar-head small{font:600 8px Inter,sans-serif;letter-spacing:0;color:#64748b;}
.mini-solar-system{height:245px;position:relative;overflow:hidden;border-radius:16px;background:radial-gradient(circle at 50% 50%,rgba(251,191,36,.07),transparent 23%),radial-gradient(circle at 50% 50%,#071222 0,#020611 68%,#01030a 100%);}
.mini-solar-system:before,.mini-solar-system:after{content:'';position:absolute;border-radius:50%;border:1px solid rgba(255,255,255,.035);inset:18px 38px;transform:rotate(12deg);}
.mini-solar-system:after{inset:42px 68px;transform:rotate(-8deg);}
.orbit{position:absolute;left:50%;top:50%;border:1px dashed rgba(148,163,184,.27);border-radius:50%;transform:translate(-50%,-50%);}
.orbit-mars{width:214px;height:170px;}
.orbit-earth{width:148px;height:116px;}
.orbit-moon{width:82px;height:64px;border-color:rgba(226,232,240,.20);}
.planet{position:absolute;right:-5px;top:50%;transform:translateY(-50%);font:700 7px Inter,sans-serif;color:#cbd5e1;white-space:nowrap;display:flex;align-items:center;gap:4px;}
.planet em{display:block;width:10px;height:10px;border-radius:50%;box-shadow:0 0 10px currentColor;}
.mars-dot em{background:#ef6b3a;color:#ef6b3a;}
.earth-dot em{background:#38bdf8;color:#38bdf8;}
.moon-dot em{background:#e5e7eb;color:#e5e7eb;}
.solar-center{position:absolute;left:50%;top:50%;transform:translate(-50%,-50%);display:flex;flex-direction:column;align-items:center;color:#fbbf24;font-size:24px;text-shadow:0 0 18px rgba(251,191,36,.7);}
.solar-center small{font:700 7px Inter,sans-serif;color:#94a3b8;text-shadow:none;margin-top:-2px;}
.mini-solar-note{font-size:9px;color:#64748b;text-align:center;padding:8px 3px 1px;}
@media(max-width:760px){.student-hero{grid-template-columns:1fr;padding:28px 22px 22px;gap:20px}.mini-solar-card{max-width:360px;width:100%;margin:0 auto}.mini-solar-system{height:210px}.orbit-mars{width:188px;height:150px}.orbit-earth{width:130px;height:102px}.orbit-moon{width:72px;height:56px}.hero-mini-title{font-size:10px}.student-hero h1{font-size:34px;}}

/* ===== PROGRESSIVE STUDENT-FIRST HOME ===== */
.student-home{max-width:1180px;margin:0 auto;padding:34px 3% 18px;}
.student-hero{position:relative;overflow:hidden;border:1px solid rgba(56,189,248,.22);border-radius:28px;padding:46px 34px 34px;background:radial-gradient(circle at 75% 20%,rgba(56,189,248,.12),transparent 32%),radial-gradient(circle at 15% 90%,rgba(192,132,252,.10),transparent 30%),linear-gradient(145deg,rgba(8,18,35,.97),rgba(2,6,16,.98));box-shadow:0 22px 70px rgba(0,0,0,.35);}
.student-hero:before{content:"";position:absolute;inset:-60%;background:repeating-radial-gradient(circle at 50% 50%,transparent 0 75px,rgba(56,189,248,.035) 76px 77px);animation:heroOrbit 35s linear infinite;pointer-events:none;}
@keyframes heroOrbit{to{transform:rotate(360deg)}}
.student-hero-inner{position:relative;z-index:1;max-width:820px;}
.student-kicker{display:inline-flex;align-items:center;gap:8px;padding:7px 12px;border:1px solid rgba(56,189,248,.28);border-radius:999px;background:rgba(56,189,248,.08);font:800 10px 'Orbitron',sans-serif;letter-spacing:1px;color:var(--neon-blue);}
.student-hero h1{font:900 clamp(38px,6vw,72px) 'Orbitron',sans-serif;line-height:1.02;margin:17px 0 12px;letter-spacing:-2px;}
.student-hero h1 span{color:var(--neon-blue);text-shadow:0 0 28px rgba(56,189,248,.35);}
.student-hero p{max-width:690px;color:var(--text-muted);font-size:16px;line-height:1.75;margin-bottom:22px;}
.student-start-row{display:flex;gap:10px;flex-wrap:wrap;}
.student-start-row .btn{padding:11px 16px;}
.student-choice-wrap{max-width:1180px;margin:18px auto 0;padding:0 3%;}
.student-choice-title{display:flex;align-items:end;justify-content:space-between;gap:15px;margin-bottom:12px;}
.student-choice-title h2{font:800 18px 'Orbitron',sans-serif;color:#fff;}
.student-choice-title span{font-size:11px;color:var(--text-muted);}
.student-choices{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;}
.student-choice{position:relative;min-height:142px;padding:20px;border-radius:20px;border:1px solid rgba(255,255,255,.10);background:linear-gradient(145deg,rgba(11,22,40,.96),rgba(4,10,20,.96));cursor:pointer;overflow:hidden;transition:.3s;}
.student-choice:hover{transform:translateY(-4px);border-color:rgba(56,189,248,.45);box-shadow:0 16px 38px rgba(0,0,0,.3),0 0 25px rgba(56,189,248,.08);}
.student-choice .choice-icon{font-size:34px;margin-bottom:10px;display:block;}
.student-choice h3{font:800 15px 'Orbitron',sans-serif;margin-bottom:5px;}
.student-choice p{font-size:12px;color:var(--text-muted);max-width:280px;}
.student-choice .choice-arrow{position:absolute;right:17px;bottom:15px;color:var(--neon-blue);font-weight:900;}
.student-choice.mars{border-color:rgba(251,146,60,.16)}
.student-choice.mars:hover{border-color:rgba(251,146,60,.5)}
.student-choice.deep{border-color:rgba(192,132,252,.16)}
.student-choice.deep:hover{border-color:rgba(192,132,252,.5)}
.home-3d-drawer{max-width:1180px;margin:14px auto 0;padding:0 3%;}
.home-3d-drawer details{border:1px solid rgba(56,189,248,.16);border-radius:16px;background:rgba(7,15,28,.72);overflow:hidden;}
.home-3d-drawer summary{cursor:pointer;padding:13px 16px;color:var(--text-muted);font:700 11px 'Orbitron',sans-serif;letter-spacing:.5px;list-style:none;}
.home-3d-drawer summary::-webkit-details-marker{display:none}.home-3d-drawer summary:after{content:'＋';float:right;color:var(--neon-blue);font-size:16px}.home-3d-drawer details[open] summary:after{content:'−'}
.home-3d-canvas{height:230px;margin:0 12px 12px;border-radius:13px;overflow:hidden;background:#020610;}
/* compact planet sections */
.progressive-section{max-width:1180px;margin:20px auto;padding:0 3%;}
.progressive-panel{border:1px solid rgba(255,255,255,.10);border-radius:24px;background:linear-gradient(145deg,rgba(9,19,35,.97),rgba(2,7,15,.98));overflow:hidden;box-shadow:0 15px 50px rgba(0,0,0,.22);}
.progressive-head{display:flex;align-items:center;justify-content:space-between;gap:15px;padding:20px 22px;border-bottom:1px solid rgba(255,255,255,.07);}
.progressive-head h2{font:800 19px 'Orbitron',sans-serif}.progressive-head p{font-size:12px;color:var(--text-muted);margin-top:3px}.progressive-count{font:800 10px 'Orbitron',sans-serif;color:var(--text-muted);white-space:nowrap;}
.progressive-tabs{display:flex;gap:8px;padding:12px 14px;border-bottom:1px solid rgba(255,255,255,.06);overflow:auto;}
.progressive-tab{border:1px solid rgba(255,255,255,.10);background:rgba(255,255,255,.03);color:var(--text-muted);padding:8px 12px;border-radius:999px;font:800 10px 'Inter',sans-serif;cursor:pointer;white-space:nowrap;transition:.25s;}
.progressive-tab.active{background:rgba(56,189,248,.12);border-color:rgba(56,189,248,.45);color:var(--neon-blue);}
.progressive-content{min-height:205px;padding:20px 22px;}
.progressive-intro{display:grid;grid-template-columns:1fr auto;gap:20px;align-items:center;}
.progressive-big-icon{font-size:70px;filter:drop-shadow(0 0 18px rgba(255,255,255,.08));}
.progressive-content h3{font:800 16px 'Orbitron',sans-serif;margin-bottom:8px;color:#fff}.progressive-content p{font-size:13px;color:var(--text-muted);line-height:1.7;max-width:720px;}
.progressive-next{margin-top:14px;display:flex;gap:8px;flex-wrap:wrap;}
.flow-hardware-grid,.flow-video-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;}
.flow-hw-card{padding:14px;border-radius:16px;border:1px solid rgba(255,255,255,.09);background:rgba(255,255,255,.025);transition:.25s;}
.flow-hw-card:hover{border-color:rgba(56,189,248,.32);transform:translateY(-2px);}
.flow-hw-icon{font-size:28px}.flow-hw-year{font:700 9px 'Orbitron',sans-serif;color:var(--neon-blue);margin:7px 0 3px}.flow-hw-card h4{font-size:12px;line-height:1.4;margin-bottom:5px}.flow-hw-card p{font-size:11px;line-height:1.55;min-height:50px}.flow-hw-actions{display:flex;gap:6px;margin-top:9px}.flow-hw-actions button{font-size:9px;padding:7px 9px;}
.flow-video-card{border:1px solid rgba(255,255,255,.09);border-radius:16px;overflow:hidden;background:rgba(255,255,255,.025);}.flow-video-thumb{height:125px;background-size:cover;background-position:center;position:relative;cursor:pointer}.flow-video-thumb:after{content:'▶';position:absolute;left:50%;top:50%;transform:translate(-50%,-50%);width:44px;height:44px;border-radius:50%;display:grid;place-items:center;background:rgba(2,6,16,.78);border:1px solid rgba(255,255,255,.35);color:#fff;font-size:16px}.flow-video-body{padding:11px}.flow-video-body h4{font-size:12px;margin-bottom:4px}.flow-video-body p{font-size:10px;min-height:32px}.flow-video-body button{margin-top:8px;font-size:9px;padding:7px 10px;}
.flow-note{padding:11px 13px;border-left:3px solid var(--neon-blue);background:rgba(56,189,248,.05);border-radius:8px;color:var(--text-muted);font-size:11px;line-height:1.6;}
@media(max-width:760px){.student-hero{padding:32px 22px 26px;border-radius:20px}.student-choices{grid-template-columns:1fr}.progressive-intro{grid-template-columns:1fr}.progressive-big-icon{display:none}.flow-hardware-grid,.flow-video-grid{grid-template-columns:1fr}.progressive-head{align-items:flex-start;flex-direction:column}.student-hero h1{letter-spacing:-1px}.home-3d-canvas{height:190px;}}


/* ===== STUDENT FRIENDLY HOME + RUNNING 2D SPACE MAP ===== */
.hardware-orbit-img{width:22px;height:22px;border-radius:50%;object-fit:cover;border:1px solid rgba(255,255,255,.75);box-shadow:0 0 9px rgba(56,189,248,.75);display:block;}

.student-friendly-line{display:inline-flex;align-items:center;gap:7px;margin:5px 0 8px;padding:7px 11px;border-radius:999px;background:rgba(56,189,248,.08);border:1px solid rgba(56,189,248,.22);color:#c7d2fe;font:700 10px Inter,sans-serif;letter-spacing:.8px;}
.student-hero h1{font-size:clamp(28px,3.7vw,46px)!important;line-height:1.08!important;margin:5px 0 9px!important;}
.hero-mini-title{font-size:10px!important;letter-spacing:1.3px!important;opacity:.78;}
.mini-solar-card{background:linear-gradient(145deg,rgba(8,24,45,.97),rgba(2,7,16,.99));border-color:rgba(56,189,248,.32);}
.running-orbit{height:245px!important;box-shadow:inset 0 0 35px rgba(56,189,248,.06);}
.running-orbit .orbit{animation:orbitSpin 12s linear infinite;transform:translate(-50%,-50%) rotate(0deg);}
.running-orbit .orbit-earth{animation-duration:16s;}
.running-orbit .planet{animation:counterSpin 12s linear infinite;}
.running-orbit .orbit-earth .planet{animation-duration:16s;}
@keyframes orbitSpin{to{transform:translate(-50%,-50%) rotate(360deg)}}
@keyframes counterSpin{to{transform:translateY(-50%) rotate(-360deg)}}
/* Moon stays physically grouped with Earth instead of becoming a separate solar orbit. */
.earth-moon-system{position:absolute;right:-14px;top:50%;width:34px;height:34px;transform:translateY(-50%);}
.earth-moon-system .moon-label{position:absolute;left:50%;top:0;width:22px;height:22px;border:1px dotted rgba(226,232,240,.35);border-radius:50%;transform:translate(-50%,-50%);}
.earth-moon-system .moon-label em{position:absolute;right:-3px;top:50%;width:7px;height:7px;border-radius:50%;background:#e5e7eb;box-shadow:0 0 8px #e5e7eb;transform:translateY(-50%);}
.earth-moon-system .moon-word{position:absolute;right:-14px;top:50%;font:700 6px Inter,sans-serif;color:#cbd5e1;transform:translateY(-50%);}
.earth-moon-system{animation:moonSystem 4s linear infinite;}
@keyframes moonSystem{to{transform:translateY(-50%) rotate(360deg)}}
/* Hardware is displayed outside the planetary orbits, as small reference objects. */
.hardware-orbit-shelf{position:absolute;right:7px;bottom:8px;display:flex;gap:5px;align-items:center;z-index:5;}
.hardware-pod{position:relative;left:auto;top:auto;width:25px;height:25px;border-radius:6px;padding:2px;background:rgba(2,6,16,.92);border:1px solid rgba(255,255,255,.22);box-shadow:0 0 9px rgba(56,189,248,.22);}
.hardware-orbit-img{width:100%;height:100%;object-fit:cover;border-radius:4px;display:block;}

.orbit-legend{position:absolute;left:8px;bottom:7px;display:flex;gap:7px;font:700 7px Inter,sans-serif;color:#94a3b8;}
.explorer-progressive .progressive-panel{background:radial-gradient(circle at 80% 0,rgba(192,132,252,.08),transparent 30%),linear-gradient(145deg,rgba(8,18,35,.98),rgba(2,6,16,.99));}
.explorer-step-grid{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:12px;}
.explorer-choice-card{padding:18px;border:1px solid rgba(255,255,255,.1);border-radius:16px;background:rgba(255,255,255,.025);cursor:pointer;transition:.25s;text-align:center;}
.explorer-choice-card:hover{transform:translateY(-3px);border-color:var(--neon-blue);background:rgba(56,189,248,.06);}
.explorer-choice-card .big-icon{font-size:28px;display:block;margin-bottom:8px;}
.explorer-choice-card h3{font:800 13px Orbitron,sans-serif;margin-bottom:5px;}
.explorer-choice-card p{font-size:11px;color:#94a3b8;}
.explorer-mini-card{display:grid;grid-template-columns:120px 1fr;gap:14px;align-items:center;padding:13px;border:1px solid rgba(255,255,255,.1);border-radius:15px;background:rgba(255,255,255,.025);}
.explorer-mini-card img{width:120px;height:85px;object-fit:cover;border-radius:10px;}
.explorer-mini-card h3{font:800 13px Orbitron,sans-serif;margin-bottom:5px;}
.explorer-mini-card p{font-size:11px;color:#94a3b8;margin-bottom:8px;}
.explorer-step-actions{display:flex;gap:8px;flex-wrap:wrap;margin-top:14px;}
@media(max-width:700px){.explorer-step-grid{grid-template-columns:1fr}.explorer-mini-card{grid-template-columns:90px 1fr}.explorer-mini-card img{width:90px;height:72px}.student-friendly-line{font-size:9px;}.running-orbit{height:210px!important}}


/* Compact student-friendly hero title */
.compact-hero-title{font-family:'Orbitron',sans-serif!important;font-weight:900!important;font-size:clamp(18px,2vw,25px)!important;line-height:1!important;letter-spacing:1px!important;margin:7px 0 7px!important;color:#67e8f9!important;text-shadow:0 0 14px rgba(56,189,248,.24),0 3px 12px rgba(0,0,0,.28);}
.compact-hero-title span{color:#c4b5fd!important;font-family:'Orbitron',sans-serif!important;font-weight:900!important;text-shadow:0 0 14px rgba(167,139,250,.28);}
.compact-hero-title::after{content:none;}
@media(max-width:760px){.compact-hero-title{font-size:21px!important;}}
/* Tiny real-hardware orbit previews */
.hardware-pod{position:absolute;z-index:3;width:30px;height:30px;border-radius:8px;padding:2px;background:rgba(2,6,16,.9);border:1px solid rgba(255,255,255,.25);box-shadow:0 0 12px rgba(56,189,248,.28);transform:translate(50%,-50%);}
.hardware-orbit-img{width:100%;height:100%;object-fit:cover;border-radius:6px;display:block;}
.pod-mars{right:18px;top:23%;}.pod-moon{right:8px;top:18%;}
.orbit-legend{position:absolute;left:8px;bottom:7px;display:flex;gap:7px;font:700 7px Inter,sans-serif;color:#94a3b8;}

/* Reliable NASA hardware image presentation */
.hardware-photo,.gallery-hw-photo,.modal-hardware-photo,.explorer-mini-card img{background:radial-gradient(circle at 50% 45%,rgba(56,189,248,.10),rgba(2,6,16,.95));object-fit:cover;}
.photo-loading,.gallery-hw-loading{display:flex;align-items:center;justify-content:center;min-height:150px;padding:18px;text-align:center;}
.modal-hardware-photo{max-height:360px;width:100%;border-radius:14px;}

.hero-3d-solar-card{position:relative;z-index:2;border:1px solid rgba(56,189,248,.30);border-radius:22px;padding:13px;background:linear-gradient(145deg,rgba(8,24,45,.97),rgba(2,7,16,.99));box-shadow:0 15px 40px rgba(0,0,0,.32),inset 0 0 35px rgba(56,189,248,.045);}
.hero-solar-box{height:245px!important;min-height:245px!important;margin:0!important;border-radius:16px!important;box-shadow:inset 0 0 45px rgba(56,189,248,.07)!important;}
.hero-solar-box #solarCanvas{height:245px;min-height:245px;}
@media(max-width:760px){.hero-solar-box{height:220px!important;min-height:220px!important}.hero-solar-box #solarCanvas{height:220px;min-height:220px;}}

/* ===== FINAL VISUAL UPDATE ===== */

.planet-photo-strip{display:grid;grid-template-columns:repeat(5,minmax(0,1fr));gap:8px;margin-top:15px;}
.planet-photo-card{position:relative;overflow:hidden;border:1px solid rgba(56,189,248,.16);border-radius:13px;background:rgba(255,255,255,.025);min-height:112px;}
.planet-photo-card img{width:100%;height:108px;object-fit:cover;display:block;background:linear-gradient(145deg,#0b1628,#020611);}
.planet-photo-card .planet-photo-caption{position:absolute;left:0;right:0;bottom:0;padding:20px 6px 6px;background:linear-gradient(transparent,rgba(0,0,0,.92));font:700 8px Inter,sans-serif;color:#fff;}
.planet-photo-card .planet-photo-tag{position:absolute;top:6px;left:6px;padding:3px 5px;border-radius:999px;background:rgba(2,6,16,.78);border:1px solid rgba(255,255,255,.12);font:700 6px Inter,sans-serif;color:#bae6fd;letter-spacing:.5px;}
.quiz-correct-pop{display:flex!important;align-items:center;justify-content:center;gap:7px;min-height:38px;padding:8px 12px;border-radius:12px;background:linear-gradient(90deg,rgba(34,197,94,.10),rgba(56,189,248,.12));border:1px solid rgba(34,197,94,.28);animation:correctPop .55s cubic-bezier(.2,.8,.2,1);}
@keyframes correctPop{0%{transform:scale(.82);opacity:0}65%{transform:scale(1.06)}100%{transform:scale(1);opacity:1}}
@media(max-width:760px){planet-photo-strip{grid-template-columns:1fr 1fr}.planet-photo-card:last-child{grid-column:1/-1}.compact-hero-title{font-size:19px!important;}}
/* FINAL COMPACT HOME + NASA EYES */
.student-home{padding:14px 3% 8px!important;}
.student-hero{grid-template-columns:minmax(0,1fr) 280px!important;gap:18px!important;padding:18px 20px 16px!important;border-radius:18px!important;}
.student-hero-copy{max-width:610px!important;}
.student-kicker{font-size:8px!important;padding:5px 8px!important;}
.student-friendly-line{font-size:8px!important;padding:5px 8px!important;margin:3px 0 5px!important;}
.compact-hero-title{font-family:'Rajdhani','Inter',sans-serif!important;font-size:clamp(15px,1.65vw,21px)!important;line-height:1.02!important;margin:5px 0 5px!important;letter-spacing:.35px!important;white-space:normal!important;font-weight:800!important;color:#f8fafc!important;text-shadow:0 0 12px rgba(56,189,248,.20)!important;} .compact-hero-title span{color:#67e8f9!important;font-weight:800!important;text-shadow:0 0 13px rgba(103,232,249,.25)!important;}
.student-hero p{font-size:10px!important;line-height:1.4!important;margin-bottom:9px!important;}
.student-start-row{gap:6px!important;}
.student-start-row .btn{font-size:8px!important;padding:6px 9px!important;}
.hero-3d-solar-card{padding:7px!important;border-radius:14px!important;}
.hero-solar-box{height:190px!important;min-height:190px!important;border-radius:10px!important;}
.hero-solar-box #solarCanvas{height:190px!important;min-height:190px!important;}
.mini-solar-head{font-size:8px!important;margin-bottom:5px!important;}
.mini-solar-head small{font-size:6px!important;}
.mini-solar-note{font-size:6px!important;margin-top:4px!important;}
.solar-live-actions{display:flex;gap:4px;margin-top:5px;flex-wrap:wrap;}
.solar-live-btn{flex:1;min-width:0;min-height:34px;border:1px solid rgba(56,189,248,.28);background:rgba(56,189,248,.07);color:#bae6fd;border-radius:999px;padding:8px 9px;font:800 8px Inter,sans-serif;cursor:pointer;white-space:nowrap;}
.solar-live-btn:hover{background:rgba(56,189,248,.14);border-color:rgba(56,189,248,.55);}
.solar-live-btn.roman{border-color:rgba(167,139,250,.28);background:rgba(167,139,250,.07);color:#ddd6fe;}
.solar-hardware-actions{position:absolute;left:8px;bottom:8px;display:flex;gap:5px;z-index:20;}
.solar-hardware-actions button{border:1px solid rgba(56,189,248,.42);background:rgba(2,6,16,.86);color:#e0f2fe;border-radius:8px;padding:6px 8px;font:800 8px Inter,sans-serif;cursor:pointer;backdrop-filter:blur(6px);transition:.2s;}
.solar-hardware-actions button:hover{background:rgba(56,189,248,.18);border-color:#38bdf8;transform:translateY(-1px);}
.solar-hardware-actions button:last-child{border-color:rgba(249,115,22,.45);color:#ffedd5;}
.solar-hardware-actions button:last-child:hover{background:rgba(249,115,22,.16);border-color:#fb923c;}
@media(max-width:760px){.solar-hardware-actions{left:6px;bottom:6px}.solar-hardware-actions button{font-size:7px;padding:5px 6px;}}
@media(max-width:760px){.student-home{padding:10px 3% 6px!important}.student-hero{grid-template-columns:1fr!important;padding:14px 14px 12px!important;gap:10px!important}.hero-3d-solar-card{max-width:340px;width:100%;margin:0 auto}.hero-solar-box,.hero-solar-box #solarCanvas{height:175px!important;min-height:175px!important}.compact-hero-title{font-size:18px!important;white-space:nowrap!important}.solar-live-btn{font-size:7px!important;padding:7px 5px!important;min-height:32px}}
.space-live-modal{max-width:1100px!important;}
.space-eyes-frame{width:100%;height:62vh;min-height:420px;border:1px solid rgba(56,189,248,.22);border-radius:12px;background:#020611;display:block;}
.space-live-actions{display:flex;gap:8px;flex-wrap:wrap;margin-top:10px;}
.space-live-actions .btn{font-size:9px!important;padding:8px 10px!important;}
.roman-live-card{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin:14px 0;padding:12px;border:1px solid rgba(167,139,250,.18);border-radius:12px;background:rgba(167,139,250,.05);}
.roman-live-card div{padding:10px;border-radius:9px;background:rgba(2,6,16,.55);}
.roman-live-card span{display:block;color:#64748b;font:800 8px Orbitron,sans-serif;margin-bottom:4px;}
.roman-live-card strong{color:#e2e8f0;font-size:11px;}
@media(max-width:700px){.space-eyes-frame{height:55vh;min-height:320px}.roman-live-card{grid-template-columns:1fr;}}
</style>

<style id="astroforge-final-polish">
/* Final title styling: force the new look after earlier responsive overrides */
.compact-hero-title{font-family:'Orbitron',sans-serif!important;font-size:clamp(13px,1.35vw,17px)!important;line-height:1.04!important;letter-spacing:.25px!important;font-weight:700!important;color:#f8fafc!important;text-shadow:0 0 10px rgba(56,189,248,.16)!important;margin:5px 0 6px!important;white-space:nowrap!important;}
.compact-hero-title span{color:#ffb84d!important;font-family:'Orbitron',sans-serif!important;font-weight:700!important;text-shadow:0 0 12px rgba(255,184,77,.25)!important;}
.solar-live-btn{font-size:8px!important;padding:7px 6px!important;min-height:32px!important;border-radius:9px!important;font-weight:800!important;letter-spacing:-.15px!important;}
@media(max-width:760px){.compact-hero-title{font-size:14px!important;white-space:nowrap!important;}.solar-live-btn{font-size:7px!important;padding:6px 4px!important;min-height:30px!important;letter-spacing:-.25px!important;}}
.quiz-wrong-react{animation:quizWrongReact .48s ease!important;border-color:#ef4444!important;box-shadow:0 0 18px rgba(239,68,68,.42)!important;}
@keyframes quizWrongReact{0%,100%{transform:translateX(0)}20%{transform:translateX(-7px)}40%{transform:translateX(7px)}60%{transform:translateX(-5px)}80%{transform:translateX(5px)}}
</style>
</head>
<body>

<div class="audience-banner">🎓 EXCLUSIVELY DESIGNED FOR STEM STUDENTS — NASA SPACE APPS CHALLENGE</div>

<header>
    <div class="logo">ASTRO<span>FORGE</span></div>
    <nav>
        <a href="#hero"><span>🌌</span><span>Orbit</span></a>
        <a href="#moon"><span>🌕</span><span>Moon</span></a>
        <a href="#mars"><span>🔴</span><span>Mars</span></a>
        <a href="#explorer"><span>🔧</span><span>Hardware</span></a>
        <a href="#timeline"><span>🚀</span><span>Timeline</span></a>
        <a href="#telemetry"><span>📡</span><span>Live Data</span></a>
        <a href="#game"><span>🎮</span><span>Game</span></a>
        <a href="#quiz"><span>🧠</span><span>Quiz</span></a>
        <a href="#archive"><span>🔍</span><span>Live Search</span></a>
    </nav>
    <div class="control-box">
        <button class="audio-btn" id="audioToggleBtn" onclick="toggleGlobalAudio()">🔇 Voice: OFF</button>
        <select class="lang-selector" id="langSelect">
            <option value="en-US">English 🇺🇸</option>
            <option value="bn-BD">বাংলা 🇧🇩</option>
        </select>
    </div>
</header>

<!-- STUDENT-FIRST HOME -->
<div class="student-home" id="hero">
    <div class="student-hero">
        <div class="student-hero-copy">
            <div class="student-kicker">🚀 NASA SPACE APPS • STUDENT EXPLORER</div>
            <div class="hero-mini-title">LEFT BEHIND, <span>NOT FORGOTTEN</span></div>
            <div class="student-friendly-line">🌌 Learn • Explore • Imagine</div><h1 class="compact-hero-title">Explore the Machines<br><span>Beyond Earth</span></h1>
            <p id="heroDesc">Discover real Moon & Mars hardware — one click at a time.</p>
            <div class="student-start-row">
                <a href="#moon" class="btn btn-primary">🌕 Explore Moon</a>
                <a href="#mars" class="btn btn-outline">🔴 Explore Mars</a>
            </div>
        </div>
        <div class="hero-3d-solar-card">
            <div class="mini-solar-head"><span>3D SOLAR SYSTEM</span><small>Earth • Moon • Mars</small></div>
            <div class="solar-canvas-box hero-solar-box"><div id="solarCanvas" aria-label="Interactive 3D solar system"></div><div class="solar-hardware-actions" aria-label="Solar system hardware shortcuts"><button type="button" onclick="openSolarHardware('moon')">🌕 Moon Hardware</button><button type="button" onclick="openSolarHardware('mars')">🔴 Mars Hardware</button></div></div>
            <div class="solar-live-actions">
                <button class="solar-live-btn" type="button" onclick="openEyesSpace()">👁 Eyes • Track Hardware</button>
                <button class="solar-live-btn roman" type="button" onclick="openRomanSpace()">🛰 Roman • Space Hardware</button>
            </div>
            <div class="mini-solar-note">Interactive 3D view — Earth carries the Moon in its own orbit.</div>
        </div>
    </div>
</div>

<div class="student-choice-wrap">
    <div class="student-choice-title"><h2>Choose your first stop</h2><span>Click • Explore • Learn</span></div>
    <div class="student-choices">
        <div class="student-choice" onclick="document.getElementById('moon').scrollIntoView({behavior:'smooth'})">
            <span class="choice-icon">🌕</span><h3>MOON</h3><p>Apollo hardware, rovers and laser ranging.</p><span class="choice-arrow">→</span>
        </div>
        <div class="student-choice mars" onclick="document.getElementById('mars').scrollIntoView({behavior:'smooth'})">
            <span class="choice-icon">🔴</span><h3>MARS</h3><p>Rovers, landing systems and powered flight.</p><span class="choice-arrow">→</span>
        </div>
        <div class="student-choice deep" onclick="document.getElementById('explorer').scrollIntoView({behavior:'smooth'})">
            <span class="choice-icon">🛰️</span><h3>HARDWARE</h3><p>Open the complete deep-space hardware archive.</p><span class="choice-arrow">→</span>
        </div>
    </div>
</div>


<!-- MOON SECTION: PROGRESSIVE DISCOVERY -->
<section id="moon" class="progressive-section">
    <div class="progressive-panel">
        <div class="progressive-head">
            <div><h2>🌕 Moon Exploration</h2><p>Start small — reveal the lunar story step by step.</p></div>
            <span class="progressive-count">STEP 1 → 4</span>
        </div>
        <div class="progressive-tabs" id="moonTabs">
            <button class="progressive-tab active" onclick="showPlanetStep('moon',1)">01 • Overview</button>
            <button class="progressive-tab" onclick="showPlanetStep('moon',2)">02 • Hardware</button>
            <button class="progressive-tab" onclick="showPlanetStep('moon',3)">03 • How It Works</button>
            <button class="progressive-tab" onclick="showPlanetStep('moon',4)">04 • See Video</button>
        </div>
        <div class="progressive-content" id="moonFlowContent"></div>
    </div>
</section>

<!-- MARS SECTION: PROGRESSIVE DISCOVERY -->
<section id="mars" class="progressive-section">
    <div class="progressive-panel">
        <div class="progressive-head">
            <div><h2>🔴 Mars Exploration</h2><p>Follow the machines from landing to science.</p></div>
            <span class="progressive-count">STEP 1 → 4</span>
        </div>
        <div class="progressive-tabs" id="marsTabs">
            <button class="progressive-tab active" onclick="showPlanetStep('mars',1)">01 • Overview</button>
            <button class="progressive-tab" onclick="showPlanetStep('mars',2)">02 • Hardware</button>
            <button class="progressive-tab" onclick="showPlanetStep('mars',3)">03 • How It Works</button>
            <button class="progressive-tab" onclick="showPlanetStep('mars',4)">04 • See Video</button>
        </div>
        <div class="progressive-content" id="marsFlowContent"></div>
    </div>
</section>

<!-- HARDWARE IMAGE GALLERY -->
<section id="hardwareGallery">
    <div class="section-head">
        <h2>🛰️ Deep-Space Hardware Gallery</h2>
        <p>Real NASA hardware images • Click any hardware to open full mission details</p>
    </div>
    <div class="gallery-toolbar">
        <span class="gallery-live"><span class="live-dot"></span> REAL NASA ARCHIVE IMAGES</span>
        <button class="btn btn-primary" type="button" onclick="openAddHardwareModal()">➕ Add Hardware</button>
    </div>
    <div class="hardware-gallery-grid" id="hardwareGalleryGrid"></div>
</section>

<!-- MASTER HARDWARE EXPLORER -->
<section id="explorer" class="progressive-section explorer-progressive">
    <div class="progressive-panel">
        <div class="progressive-head">
            <div><h2>🔧 Master Hardware Explorer</h2><p>Discover space hardware step by step — no information overload.</p></div>
            <span class="progressive-count">STEP 1 → 4</span>
        </div>
        <div class="progressive-tabs" id="explorerTabs">
            <button class="progressive-tab active" onclick="showExplorerStep(1)">01 • Choose</button>
            <button class="progressive-tab" onclick="showExplorerStep(2)">02 • Hardware</button>
            <button class="progressive-tab" onclick="showExplorerStep(3)">03 • How It Works</button>
            <button class="progressive-tab" onclick="showExplorerStep(4)">04 • Watch</button>
        </div>
        <div class="progressive-content" id="explorerFlowContent"></div>
    </div>
</section>

<!-- TIMELINE -->
<section id="timeline">
    <div class="section-head">
        <h2>🚀 Planetary Mission Timeline</h2>
        <p>Explore the major missions and their stories without filling the homepage.</p>
    </div>
    <div class="timeline-compact-box">
        <div style="font-size:34px; margin-bottom:4px;">🛰️🌕🔴</div>
        <h3 style="font-family:'Orbitron',sans-serif; color:var(--neon-blue); font-size:18px;">Mission Archive</h3>
        <p>Click below to open the complete timeline with mission images, dates, objectives and key events.</p>
        <button class="btn btn-primary" onclick="openMissionTimeline()">🔭 See Mission Timeline & Details</button>
    </div>
</section>


<!-- MISSION TIMELINE DETAIL MODAL -->
<div class="modal" id="missionTimelineModal">
    <div class="modal-content">
        <span class="close-modal" onclick="closeMissionTimeline()">&times;</span>
        <h2 style="color:var(--neon-blue); font-family:'Orbitron',sans-serif; font-size:22px;">🚀 Planetary Mission Timeline</h2>
        <p style="color:var(--text-muted); margin-top:6px;">Click through the archive below to explore mission history and real NASA imagery.</p>
        <div class="mission-modal-grid" id="missionTimelineGrid"></div>
    </div>
</div>

<!-- REALTIME TELEMETRY -->
<section id="telemetry">
    <div class="section-head">
        <h2>📡 Live Planetary Hardware Telemetry</h2>
        <p>Real-time continuous deep-space environmental and payload tracking</p>
    </div>
    <div class="telemetry-grid">
        <div class="telemetry-card">
            <div style="margin-bottom:8px;"><span class="live-indicator"><span class="live-dot"></span> LIVE MOON RELIC</span></div>
            <h3 style="font-family:'Orbitron',sans-serif; font-size:16px; color:var(--neon-blue); margin-bottom:10px;">🌕 Apollo LRRR Array</h3>
            <p style="font-size:14px; color:var(--text-muted);">Earth-Moon Distance: <strong id="liveMoonDist" style="color:var(--neon-blue)">384,402.18 km</strong></p>
            <p style="font-size:14px; color:var(--text-muted); margin-top:4px;">Laser Pulse Return: <strong style="color:var(--green)">Active (Optic Clean)</strong></p>
        </div>
        <div class="telemetry-card">
            <div style="margin-bottom:8px;"><span class="live-indicator"><span class="live-dot"></span> LIVE MARS HARDWARE</span></div>
            <h3 style="font-family:'Orbitron',sans-serif; font-size:16px; color:var(--orange); margin-bottom:10px;">🔴 Jezero Surface Station</h3>
            <p style="font-size:14px; color:var(--text-muted);">Surface Temp: <strong style="color:var(--orange)">-64.2°C</strong></p>
            <p style="font-size:14px; color:var(--text-muted); margin-top:4px;">Ingenuity Battery: <strong style="color:var(--gold)">Solar Float (Idle)</strong></p>
        </div>
        <div class="telemetry-card">
            <div style="margin-bottom:8px;"><span class="live-indicator"><span class="live-dot"></span> LIVE DEEP SPACE</span></div>
            <h3 style="font-family:'Orbitron',sans-serif; font-size:16px; color:var(--purple); margin-bottom:10px;">🌌 Voyager 1 Link</h3>
            <p style="font-size:14px; color:var(--text-muted);">Distance: <strong id="voyagerDist" style="color:var(--purple)">24,385,120,400 km</strong></p>
            <p style="font-size:14px; color:var(--text-muted); margin-top:4px;">Signal Roundtrip: <strong style="color:var(--neon-blue)">22.5 Hours</strong></p>
        </div>
    </div>
</section>

<!-- GAME -->
<section id="game">
    <div class="section-head">
        <h2>🎮 Mission Control Game</h2>
        <p>Design a planetary mission and deploy payload</p>
    </div>
    <div class="game-container">
        <div class="game-step active" id="gStep1">
            <h3 style="color:var(--purple); font-family:'Orbitron',sans-serif; font-size:16px;">Select Target Body</h3>
            <div class="option-grid">
                <div class="option-card" onclick="selectGameOption('target', 'Moon', this)"><h4>🌕 Moon</h4></div>
                <div class="option-card" onclick="selectGameOption('target', 'Mars', this)"><h4>🔴 Mars</h4></div>
            </div>
            <button class="btn btn-primary" style="margin-top:22px;" onclick="nextGameStep(2)">Next Step ➔</button>
        </div>
        <div class="game-step" id="gStep2">
            <h3 style="color:var(--purple); font-family:'Orbitron',sans-serif; font-size:16px;">Select Hardware Payload</h3>
            <div class="option-grid">
                <div class="option-card" onclick="selectGameOption('payload', 'Laser Retroreflector', this)"><h4>📡 Laser Array</h4></div>
                <div class="option-card" onclick="selectGameOption('payload', 'Aerial Drone System', this)"><h4>🚁 Aerial Drone</h4></div>
            </div>
            <button class="btn btn-primary" style="margin-top:22px;" onclick="nextGameStep(3)">Launch Mission 🚀</button>
        </div>
        <div class="game-step" id="gStep3">
            <h3 style="color:var(--green); font-family:'Orbitron',sans-serif;" id="gameResultTitle">Mission Successful!</h3>
            <p id="gameResultDesc" style="margin-top:12px; font-size:15px; color:#ffffff;"></p>
            <button class="btn btn-outline" style="margin-top:22px;" onclick="resetGame()">🔄 Reset Mission</button>
        </div>
    </div>
</section>

<!-- QUIZ -->
<section id="quiz">
    <div class="section-head">
        <h2>🧠 STEM Quiz (30 Questions)</h2>
        <p>Test your comprehensive knowledge on space hardware & missions</p>
    </div>
    <div class="quiz-container">
        <div style="display:flex; justify-content:space-between; margin-bottom:12px; font-size:13px; font-weight:800; font-family:'Orbitron',sans-serif;">
            <span id="qProgress" style="color:var(--neon-blue)">Question 1 of 30</span>
            <span style="color:var(--green)">Score: <span id="qScore">0</span> / 300</span>
        </div>
        <h3 id="qText" style="font-size:17px; margin-bottom:14px; color:#ffffff;">Question Loading...</h3>
        <div id="qOptions"></div>
        <div id="quizFeedback" style="margin-top:12px; font-weight:700; display:none; font-size:15px;"></div>
    </div>
</section>

<!-- LIVE SEARCH ARCHIVE SECTION -->
<section id="archive">
    <div class="archive-highlight-box" style="background: radial-gradient(circle, rgba(56,189,248,0.1) 0%, rgba(2,6,16,0.95) 80%); border: 2px solid var(--neon-blue); border-radius: 16px; padding: 30px; box-shadow: 0 0 25px rgba(56,189,248,0.25);">
        <div class="section-head" style="margin-bottom:15px;">
            <div style="margin-bottom:8px;"><span class="live-indicator"><span class="live-dot"></span> LIVE NASA DATABASE SEARCH</span></div>
            <h2>Click & Search Hardware Photo</h2>
            <p>Type any hardware name or explore live NASA imagery instantly</p>
        </div>
        <div style="display:flex; justify-content:center; gap:12px; margin-bottom:22px; flex-wrap:wrap;">
            <input type="text" id="nasaQuery" style="padding:12px 16px; border-radius:8px; border:1px solid var(--panel-border); background:var(--panel-bg); color:#fff; width:100%; max-width:340px; font-size:15px;" value="Apollo Retroreflector">
            <button class="btn btn-primary" id="liveSearchBtn" onclick="searchNASA()">🔴 Live Search</button>
            <button class="btn btn-outline" id="googleSearchBtn" onclick="openGoogleSearch()">🌐 Google Search</button>
        </div>
        <div class="hardware-grid" id="nasaResults"></div>
    </div>
</section>

<footer>
    <p>AstroForge — Left Behind, Not Forgotten | NASA Space Apps Challenge</p>
    <button class="team-simple-btn" onclick="openTeamModal()">Team AstroForge Members</button>
</footer>

<!-- TEAM MODAL -->
<div class="modal" id="teamModal">
    <div class="modal-content" style="max-width:580px;">
        <span class="close-modal" onclick="closeTeamModal()">&times;</span>
        <h2 style="color:var(--neon-blue); font-size:22px; font-family:'Orbitron',sans-serif; text-align:center; margin-bottom:16px;">Team AstroForge</h2>
        
        <div class="team-leader-center">
            <h3>Roni Das</h3>
            <p>TEAM LEADER & DEVELOPER</p>
        </div>

        <div style="text-align:center; font-size:12px; color:var(--orange); font-weight:800; margin-bottom:12px; letter-spacing:1px; font-family:'Orbitron',sans-serif;">TEAM MEMBERS</div>
        
        <div class="team-members-grid">
            <div class="team-member-card"><strong>Sajid Mahmud</strong><br><span style="font-size:12px; color:var(--text-muted)">Content Writer</span></div>
            <div class="team-member-card"><strong>Md. Milon Sarker</strong><br><span style="font-size:12px; color:var(--text-muted)">Space Science & Physics</span></div>
            <div class="team-member-card"><strong>Sanchari Karmakar</strong><br><span style="font-size:12px; color:var(--text-muted)">UI/UX & Illustrator</span></div>
            <div class="team-member-card"><strong>Jobair Ahmed</strong><br><span style="font-size:12px; color:var(--text-muted)">Animator & Voice Artist</span></div>
        </div>
    </div>
</div>

<!-- HARDWARE VIDEO MODAL -->
<div class="modal" id="hardwareVideoModal">
    <div class="modal-content" style="max-width:920px;">
        <span class="close-modal" onclick="closeHardwareVideo()">&times;</span>
        <div id="videoModalSub" style="font-size:10px;color:var(--orange);font-family:'Orbitron',sans-serif;font-weight:800;margin-bottom:6px;">NASA / JPL VIDEO</div>
        <h2 id="videoModalTitle" style="color:var(--neon-blue);font-size:20px;font-family:'Orbitron',sans-serif;margin-bottom:13px;"></h2>
        <iframe id="hardwareVideoFrame" class="modal-video-frame" title="NASA hardware video" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
        <div class="modal-video-panel"><div class="modal-video-title">💡 What to notice</div><div id="videoModalDescription" style="color:#cbd5e1;font-size:12px;line-height:1.6;"></div></div>
        <div style="margin-top:10px;text-align:center;color:#64748b;font-size:10px;">🎬 Video plays directly inside ASTROFORGE</div>
    </div>
</div>

<!-- ADD HARDWARE MODAL -->
<div class="modal" id="addHardwareModal">
    <div class="modal-content add-hardware-content">
        <span class="close-modal" onclick="closeAddHardwareModal()">&times;</span>
        <h2 style="color:var(--neon-blue); font-family:'Orbitron',sans-serif; font-size:21px; margin-bottom:6px;">➕ Add Hardware</h2>
        <p style="color:var(--text-muted); font-size:13px; margin-bottom:18px;">Add your own hardware and photo. Your custom hardware is saved in this browser and can be deleted later.</p>
        <div class="add-hw-form">
            <input id="addHwName" placeholder="Hardware name" />
            <select id="addHwTarget"><option value="moon">🌕 Moon</option><option value="mars">🔴 Mars</option></select>
            <input id="addHwYear" placeholder="Year" />
            <input id="addHwMission" placeholder="Mission" />
            <input id="addHwImage" placeholder="Real image URL (optional)" />
            <div class="add-hw-file">
                <input id="addHwImageFile" type="file" accept="image/*" />
            </div>
            <div class="add-hw-photo-note">You can use an image URL or upload a photo. Uploaded photos are compressed and saved in this browser.</div>
            <textarea id="addHwSummary" placeholder="Short information"></textarea>
        </div>
        <button class="btn btn-primary" style="width:100%; margin-top:14px;" onclick="addCustomHardware()">💾 Save Hardware</button>
    </div>
</div>

<!-- HARDWARE MODAL WITH REAL NASA HARDWARE PHOTO -->
<div class="modal" id="hwModal">
    <div class="modal-content">
        <span class="close-modal" onclick="closeModal()">&times;</span>
        <h2 id="mTitle" style="color:var(--neon-blue); font-size:22px; font-family:'Orbitron',sans-serif; margin-bottom:6px;"></h2>
        <div id="mSub" style="font-size:12px; color:var(--orange); font-weight:800; margin-bottom:16px;"></div>
        

        <!-- REAL NASA HARDWARE PHOTO -->
        <div id="modalPhotoWrap" class="modal-hardware-photo-wrap" style="display:none;">
            <img id="modalHardwarePhoto" class="modal-hardware-photo" alt="NASA hardware photo">
            <div class="modal-photo-credit">NASA ARCHIVE • REAL HARDWARE PHOTO</div>
        </div>
        
        <div class="modal-overview" id="mOverview"><strong>QUICK OVERVIEW</strong><span></span></div>
        <div class="modal-status-strip">
            <div class="modal-status-chip"><span>MISSION STATUS</span><strong id="mStatus">—</strong></div>
            <div class="modal-status-chip"><span>USABLE TODAY?</span><strong id="mUsable">—</strong></div>
        </div>
        <div class="modal-actions">
            <button class="btn btn-primary" id="modalVideoBtn" type="button">▶ See Video</button>
            <button class="btn btn-primary" id="modalLiveSearchBtn">🌐 Live NASA Archive Search</button>
            <button class="btn btn-outline" id="modalListenBtn" onclick="listenModalContent()">🔊 Listen & Mark</button>
        </div>
        
        <div class="modal-grid">
            <div class="modal-field"><label>🚀 Mission & Launch Details</label><p id="mMission"></p></div>
            <div class="modal-field"><label>📍 Exact Landing Coordinates</label><p id="mLoc"></p></div>
            <div class="modal-field"><label>🎯 Operational Purpose</label><p id="mPurpose"></p></div>
            <div class="modal-field"><label>⚙️ Detailed Mechanical Engineering</label><p id="mHow"></p></div>
            <div class="modal-field"><label>📖 Current Modern Status</label><p id="mHappened"></p></div>
            <div class="modal-field"><label>🛑 Structural Reason Left Behind</label><p id="mWhy"></p></div>
            <div class="modal-field" style="grid-column: 1 / -1; border-left-color:var(--green);"><label>🔬 Enduring Scientific Legacy</label><p id="mScience"></p></div>
        </div>
    </div>
</div>

<!-- NASA EYES / ROMAN SPACE MODALS -->
<div class="modal" id="spaceEyesModal">
  <div class="modal-content space-live-modal">
    <span class="close-modal" onclick="closeEyesSpace()">&times;</span>
    <h2 style="color:var(--neon-blue);font-family:'Orbitron',sans-serif;font-size:20px;">👁 NASA Eyes on the Solar System</h2>
    <p style="color:var(--text-muted);margin:6px 0 12px;">Real-time 3D mission visualization. NASA Eyes lets you explore the same mission environment behind this project — spacecraft, rovers, landing systems and other deep-space hardware in context.</p>
    <iframe id="spaceEyesFrame" class="space-eyes-frame" title="NASA Eyes on the Solar System" src="about:blank" allowfullscreen></iframe>
    <div class="space-live-actions">
      <button class="btn btn-primary" type="button" onclick="window.open('https://eyes.nasa.gov/apps/solar-system/','_blank','noopener,noreferrer')">🚀 Open NASA Eyes</button>
      <button class="btn btn-outline" type="button" onclick="closeEyesSpace()">Close</button>
    </div>
  </div>
</div>

<div class="modal" id="romanSpaceModal">
  <div class="modal-content space-live-modal">
    <span class="close-modal" onclick="closeRomanSpace()">&times;</span>
    <h2 style="color:#c4b5fd;font-family:'Orbitron',sans-serif;font-size:20px;">🛰 Nancy Grace Roman Space Telescope</h2>
    <p style="color:var(--text-muted);line-height:1.6;margin:8px 0;">Roman is part of the project’s space-hardware story: a real spacecraft designed for wide-field infrared astronomy. Use NASA Eyes to place the spacecraft in its mission environment and connect the hardware to where it operates.</p>
    <div class="roman-live-card">
      <div><span>MISSION</span><strong>Roman Space Telescope</strong></div>
      <div><span>DESTINATION</span><strong>Sun-Earth L2</strong></div>
      <div><span>MODE</span><strong>Interactive 3D tracking</strong></div>
    </div>
    <div class="space-live-actions">
      <button class="btn btn-primary" type="button" onclick="openRomanEyes()">👁 Track Roman in NASA Eyes</button>
      <a class="btn btn-outline" href="https://science.nasa.gov/mission/roman-space-telescope/" target="_blank" rel="noopener noreferrer">NASA Roman Mission</a>
      <button class="btn btn-outline" type="button" onclick="closeRomanSpace()">Close</button>
    </div>
  </div>
</div>

<script>
let isAudioOn = false;
let availableVoices = [];

function loadSpeechVoices(){
    if(!('speechSynthesis' in window)) return;
    availableVoices = window.speechSynthesis.getVoices() || [];
}
if('speechSynthesis' in window){
    loadSpeechVoices();
    window.speechSynthesis.onvoiceschanged = loadSpeechVoices;
}

function preferredVoice(lang){
    const voices = availableVoices.length ? availableVoices : window.speechSynthesis.getVoices();
    const exact = voices.find(v => v.lang === lang);
    if(exact) return exact;
    const base = lang.split('-')[0].toLowerCase();
    return voices.find(v => v.lang && v.lang.toLowerCase().startsWith(base));
}

function currentSpeechLang(){
    return document.getElementById('langSelect')?.value || 'en-US';
}

function toggleGlobalAudio() {
    isAudioOn = !isAudioOn;
    const btn = document.getElementById('audioToggleBtn');
    if (isAudioOn) {
        btn.innerText = "🔊 Voice: ON";
        btn.classList.add('on');
        speakText(currentSpeechLang().startsWith('bn') ? 'ভয়েস চালু হয়েছে। অ্যাস্ট্রোফোর্জে স্বাগতম।' : 'Voice is on. Welcome to ASTROFORGE.');
    } else {
        btn.innerText = "🔇 Voice: OFF";
        btn.classList.remove('on');
        if ('speechSynthesis' in window) window.speechSynthesis.cancel();
    }
}

function speakText(text) {
    if (!isAudioOn || !('speechSynthesis' in window) || !text) return;
    window.speechSynthesis.cancel();
    const lang = currentSpeechLang();
    const utterance = new SpeechSynthesisUtterance(text);
    utterance.lang = lang;
    const voice = preferredVoice(lang);
    if(voice) utterance.voice = voice;
    utterance.rate = 0.9;
    utterance.pitch = 1;
    window.speechSynthesis.speak(utterance);
}

function listenModalContent() {
    if (!isAudioOn) {
        const btn=document.getElementById('audioToggleBtn');
        if(btn) btn.click();
        return;
    }
    const title = document.getElementById('mTitle')?.innerText || '';
    const purpose = document.getElementById('mPurpose')?.innerText || '';
    speakText(`${title}. Purpose: ${purpose}`);
    const purposeEl = document.getElementById('mPurpose');
    if(purposeEl){ purposeEl.classList.add('highlight-text'); setTimeout(()=>purposeEl.classList.remove('highlight-text'),1500); }
}

function openEyesSpace(){
    const modal=document.getElementById('spaceEyesModal');
    const frame=document.getElementById('spaceEyesFrame');
    frame.src='https://eyes.nasa.gov/apps/solar-system/';
    modal.style.display='flex';
}
function closeEyesSpace(){
    const frame=document.getElementById('spaceEyesFrame');
    frame.src='about:blank';
    document.getElementById('spaceEyesModal').style.display='none';
}
function openRomanSpace(){
    const modal=document.getElementById('romanSpaceModal');
    modal.style.display='flex';
}
function closeRomanSpace(){
    document.getElementById('romanSpaceModal').style.display='none';
}
function openRomanEyes(){
    window.open('https://eyes.nasa.gov/apps/solar-system/','_blank','noopener,noreferrer');
}

const hardwareData = [
    {
        id: "apollo11-lrrr",
        photoQueries: ["Apollo 11 laser retroreflector", "Apollo 11 retroreflector"],
        name: "Apollo 11 Laser Ranging Retroreflector",
        target: "moon",
        year: "1969",
        mission: "Apollo 11",
        loc: "Sea of Tranquility (0.67408° N, 23.47297° E)",
        summary: "A passive optical experiment that lets scientists measure the Earth–Moon distance with extraordinary precision.",
        purpose: "Reflect ground lasers back to Earth to calculate lunar distance precisely with millimeter accuracy.",
        how: "Constructed with an aerospace-grade aluminum panel housing 100 precision quartz corner-cube prisms that bounce incoming light directly back to its exact source regardless of angle of incidence.",
        happened: "Fully operational today after over 5 decades of continuous exposure to harsh lunar vacuum and thermal extremes, continuously receiving laser pulses from global ranging facilities.",
        why: "Passive optical architecture requiring zero electrical power, designed for indefinite standalone deployment without battery maintenance.",
        science: "Proved conclusively that the Moon has a molten liquid outer core, confirmed Einstein's Theory of General Relativity with unprecedented precision, and mapped complex lunar orbital secular acceleration dynamics."
    },
    {
        id: "apollo15-lrv",
        photoQueries: ["Apollo 15 Lunar Roving Vehicle", "Lunar Roving Vehicle Apollo 15"],
        name: "Lunar Roving Vehicle (LRV-1)",
        target: "moon",
        year: "1971",
        mission: "Apollo 15",
        loc: "Hadley-Apennine (26.1322° N, 3.6339° E)",
        summary: "The first Apollo lunar rover, built to extend astronauts’ travel range and geological exploration on the Moon.",
        purpose: "Provide astronaut surface transportation to vastly expand geological sample collection range across volcanic rilles.",
        how: "Built with a foldable 2219 aluminum alloy chassis, silver-zinc potassium hydroxide non-rechargeable batteries, independent solid-rotor wheel drive motors, and a T-bar steering controller.",
        happened: "Parked permanently at Hadley Base after successfully logging 27.9 kilometers across extremely rugged, boulder-strewn volcanic highlands.",
        why: "Ascent Module weight restrictions and strict payload capacity constraints on the lunar module descent stage mandated abandoning the vehicle.",
        science: "Revolutionized off-world rover engineering, establishing baseline parameters for thermal vacuum mobility, dust mitigation, and electric drive endurance in low gravity."
    },
    {
        id: "ingenuity",
        photoQueries: ["Ingenuity Mars Helicopter", "NASA Ingenuity helicopter Mars"],
        fixedPhoto: "https://d2pn8kiwq2w21t.cloudfront.net/original_images/jpegPIA23882.jpg",
        name: "Ingenuity Mars Helicopter",
        target: "mars",
        year: "2021",
        mission: "Mars 2020",
        loc: "Jezero Crater, Mars (18.4447° N, 77.4508° E)",
        summary: "A small autonomous helicopter that demonstrated powered, controlled flight on another planet for the first time.",
        purpose: "Demonstrate powered controlled atmospheric flight in the ultra-thin 1 percent Martian atmosphere.",
        how: "Dual counter-rotating carbon-fiber composite blades spinning at approximately 2,400 RPM powered by high-efficiency solar-recharged lithium-ion cells and autonomous inertial navigation.",
        happened: "Completed 72 historic flights over 3 Earth years before sustaining carbon-fiber rotor tip damage during a hard descent landing.",
        why: "Mission lifetime and mechanical stress limits exceeded by over 300 percent before hardware blade fracture permanently halted further aerial scouting hops.",
        science: "Proved definitively that powered planetary aerial reconnaissance is completely viable and highly effective on thin-atmosphere terrestrial worlds, opening new paradigms for planetary exploration."
    },
    {
        id: "skycrane",
        photoQueries: ["Curiosity sky crane", "Mars Science Laboratory descent stage"],
        fixedPhoto: "https://www.nasa.gov/wp-content/uploads/2024/08/2-ksc-2011-7087large.jpg?w=1024",
        name: "MSL Curiosity Sky Crane System",
        target: "mars",
        year: "2012",
        mission: "Mars Science Laboratory",
        loc: "Gale Crater, Mars (4.5895° S, 137.4417° E)",
        summary: "A rocket-powered descent stage that lowered Curiosity onto Mars, then flew away for a controlled crash.",
        purpose: "Lower the heavy 900kg Curiosity Rover gently and directly onto its wheels without dangerous rocket exhaust dust contamination.",
        how: "Fully autonomous descent stage equipped with throttleable hydrazine monopropellant rocket engines, radar altimeters, and high-strength nylon bridle lowering cables.",
        happened: "Executed a programmed controlled flyaway maneuver immediately after payload deployment, safely impacting the Martian surface 650 meters away from the rover.",
        why: "Single-use landing infrastructure designed deliberately to sacrifice itself upon payload touchdown release.",
        science: "Pioneered heavy-payload entry descent landing mechanics which laid the essential technical foundation utilized for subsequent massive Mars rover and hardware payloads."
    },
    {
        id: "apollo17-lrv",
        photoQueries: ["Apollo 17 Lunar Roving Vehicle", "Apollo 17 lunar rover NASA"],
        name: "Lunar Roving Vehicle (LRV-3)",
        target: "moon",
        year: "1972",
        mission: "Apollo 17",
        loc: "Taurus-Littrow Valley, Moon",
        summary: "The final Apollo lunar rover, used to travel farther from the lunar module and collect geological samples.",
        purpose: "Extend astronaut mobility and support geological field exploration during Apollo 17.",
        how: "A lightweight electric rover with four independently driven wheels, steering, wire-mesh wheels, batteries, navigation equipment, and a foldable chassis.",
        happened: "Used by astronauts Eugene Cernan and Harrison Schmitt during Apollo 17 surface excursions and left at the landing site after the mission.",
        why: "The rover was designed as surface mobility hardware and was not intended to return to Earth with the lunar module ascent stage.",
        science: "Enabled longer traverses and helped astronauts investigate the Taurus-Littrow Valley, including sampling and field observations beyond walking range."
    },
    {
        id: "apollo14-lr3",
        photoQueries: ["Apollo 14 laser ranging retroreflector", "Apollo 14 retroreflector NASA"],
        name: "Apollo 14 Laser Ranging Retroreflector",
        target: "moon",
        year: "1971",
        mission: "Apollo 14",
        loc: "Fra Mauro Highlands, Moon",
        summary: "A passive array of corner-cube reflectors installed on the Moon for precision laser-ranging experiments.",
        purpose: "Return laser pulses toward their source so scientists can precisely measure lunar distance and motion.",
        how: "A panel containing precision corner-cube reflectors uses optical geometry to send incoming laser light back toward the observing station.",
        happened: "Remains on the lunar surface and is part of the long-running lunar laser-ranging experiment.",
        why: "It is a passive scientific instrument intended to remain at the lunar site for long-term measurements.",
        science: "Supports measurements of lunar orbit, Earth-Moon dynamics, and tests of gravitational physics using extremely precise timing."
    },
    {
        id: "apollo11-eagle",
        photoQueries: ["Apollo 11 lunar module Eagle Moon", "Apollo 11 Lunar Module NASA"],
        name: "Apollo 11 Lunar Module Eagle",
        target: "moon",
        year: "1969",
        mission: "Apollo 11",
        loc: "Sea of Tranquility, Moon",
        summary: "The lunar module that carried astronauts from lunar orbit to the Moon's surface during the first crewed lunar landing.",
        purpose: "Provide the crewed descent and ascent vehicle for Apollo astronauts operating on the lunar surface.",
        how: "A two-stage spacecraft used a descent propulsion system for landing and an ascent stage for returning the astronauts to lunar orbit.",
        happened: "The descent stage remains at the Apollo 11 landing site while the ascent stage departed the Moon.",
        why: "Only the ascent stage was required for the return to lunar orbit; the descent stage was left on the Moon as part of the mission architecture.",
        science: "The vehicle enabled the first human lunar surface operations and deployment of early Apollo scientific experiments."
    },
    {
        id: "curiosity-rover",
        photoQueries: ["Curiosity rover Mars NASA", "Mars Science Laboratory Curiosity rover"],
        name: "Mars Science Laboratory Curiosity Rover",
        target: "mars",
        year: "2012",
        mission: "Mars Science Laboratory",
        loc: "Gale Crater, Mars (4.5895° S, 137.4417° E)",
        summary: "A car-sized mobile laboratory exploring Gale Crater to study Martian geology, climate, and past habitability.",
        purpose: "Analyze rocks and soil, investigate the environment, and assess whether Mars ever had conditions favorable for microbial life.",
        how: "Uses six-wheel rocker-bogie mobility, a robotic arm, drill and sample-handling hardware, cameras, spectrometers, and a radioisotope power system.",
        happened: "Landed in Gale Crater in August 2012 and continues surface science operations with its mission extended through NASA programs.",
        why: "Curiosity is a surface science rover designed for long-duration operation on Mars rather than return to Earth.",
        science: "Its measurements have documented ancient aqueous environments and helped reconstruct the geological and environmental history of Gale Crater."
    },
    {
        id: "perseverance-rover",
        photoQueries: ["Perseverance rover Mars NASA", "Mars 2020 Perseverance rover"],
        name: "Perseverance Mars Rover",
        target: "mars",
        year: "2021",
        mission: "Mars 2020",
        loc: "Jezero Crater, Mars (18.4447° N, 77.4508° E)",
        summary: "A Mars rover built to search for signs of ancient microbial life and collect scientifically selected samples for possible future return.",
        purpose: "Study Jezero's ancient environments, characterize rocks and regolith, and cache samples for future missions.",
        how: "Combines six-wheel mobility with a robotic sampling system, advanced cameras, spectrometers, environmental sensors, and the PIXL and SHERLOC instruments.",
        happened: "Landed in Jezero Crater in February 2021 and has been conducting surface science and sample-caching operations.",
        why: "The rover is designed as a long-duration surface platform and remains on Mars after each mission activity.",
        science: "Provides detailed geological evidence from an ancient lake-and-delta environment and preserves samples intended to support future Mars exploration."
    },
    {
        id: "insight-lander",
        photoQueries: ["NASA InSight lander Mars", "InSight Mars lander surface"],
        name: "InSight Mars Lander",
        target: "mars",
        year: "2018",
        mission: "InSight",
        loc: "Elysium Planitia, Mars (4.5024° N, 135.6234° E)",
        summary: "A stationary Mars lander built to study the planet's interior, seismic activity, and heat flow.",
        purpose: "Measure marsquakes, internal structure, and thermal properties to understand how rocky planets form and evolve.",
        how: "Used a sensitive seismometer, heat-flow experiment, pressure and weather sensors, and a robotic deployment arm on a stationary lander platform.",
        happened: "Operated on Mars from 2018 until its mission ended after solar-panel dust accumulation reduced available power.",
        why: "InSight was a stationary scientific platform intended to perform measurements at one carefully selected landing site.",
        science: "Returned the first comprehensive seismic observations from Mars and revealed new information about the planet's crust, mantle, and core."
    }
];

const hardwareStatus = {
    "apollo11-lrrr": {status:"ACTIVE • PASSIVE", usable:"YES — laser ranging", cls:"passive", video:"fPCAfiGfv08", title:"Apollo 11 Moonwalk & Lunar Surface", desc:"See the Apollo 11 surface operation and understand the context in which the lunar instruments were deployed. The retroreflector itself is passive: it needs no battery or motor."},
    "apollo15-lrv": {status:"INACTIVE • HISTORICAL", usable:"NO — left on Moon", cls:"inactive", video:"J22hKd8SZp8", title:"Apollo 15: Lunar Rover in Action", desc:"Watch the Lunar Roving Vehicle extend astronaut mobility across the Moon. Focus on the four-wheel layout, steering and how the crew used it for geological exploration."},
    "apollo17-lrv": {status:"INACTIVE • HISTORICAL", usable:"NO — left on Moon", cls:"inactive", video:"FcSwFq3AAgA", title:"Apollo 17 Lunar Roving Vehicle", desc:"See the final Apollo lunar rover and how astronauts used electric mobility to travel farther from the lunar module."},
    "apollo14-lr3": {status:"ACTIVE • PASSIVE", usable:"YES — laser ranging", cls:"passive", video:"fPCAfiGfv08", title:"Apollo Lunar Surface Operations", desc:"Apollo surface footage provides context for the deployment of passive lunar experiments such as laser retroreflectors."},
    "apollo11-eagle": {status:"INACTIVE • HISTORICAL", usable:"NO — historic artifact", cls:"inactive", video:"fPCAfiGfv08", title:"Apollo 11 Lunar Module on the Moon", desc:"Historic Apollo 11 footage shows the lunar module, surface operations and the engineering environment around the landing site."},
    "curiosity-rover": {status:"ACTIVE MISSION", usable:"YES — science operations", cls:"active", video:"P4boyXQuUIw", title:"Mars Science Laboratory — Curiosity", desc:"NASA JPL's mission animation explains Curiosity's entry, descent, landing and rover architecture, including the sky-crane concept."},
    "perseverance-rover": {status:"ACTIVE MISSION", usable:"YES — science operations", cls:"active", video:"TgcI8ur72x0", title:"Perseverance & Ingenuity Arrive at Mars", desc:"See the Mars 2020 landing sequence and how Perseverance carried Ingenuity to Jezero Crater for its flight demonstration."},
    "ingenuity": {status:"MISSION COMPLETE", usable:"NO — flight ended", cls:"inactive", video:"wMnOo2zcjXA", title:"Ingenuity's First Powered Flight", desc:"Actual rover-camera footage shows Ingenuity's first powered, controlled flight on another planet on April 19, 2021."},
    "skycrane": {status:"MISSION COMPLETE", usable:"NO — single-use", cls:"inactive", video:"P4boyXQuUIw", title:"Curiosity Sky Crane Landing", desc:"This NASA JPL animation explains the powered descent and sky-crane architecture used to place Curiosity safely on Mars."},
    "insight-lander": {status:"MISSION COMPLETE", usable:"NO — mission ended", cls:"inactive", video:"P4boyXQuUIw", title:"Mars Landing & Surface Engineering", desc:"Use the video as a visual introduction to robotic Mars mission architecture and compare it with InSight's stationary science platform."}
};

const videoCollections = {
    moon: [
        {hw:"apollo11-lrrr", label:"Apollo 11", thumb:"https://i.ytimg.com/vi/fPCAfiGfv08/hqdefault.jpg"},
        {hw:"apollo15-lrv", label:"Apollo 15 LRV", thumb:"https://i.ytimg.com/vi/J22hKd8SZp8/hqdefault.jpg"},
        {hw:"apollo17-lrv", label:"Apollo 17 LRV", thumb:"https://i.ytimg.com/vi/FcSwFq3AAgA/hqdefault.jpg"}
    ],
    mars: [
        {hw:"curiosity-rover", label:"Curiosity / MSL", thumb:"https://i.ytimg.com/vi/P4boyXQuUIw/hqdefault.jpg"},
        {hw:"perseverance-rover", label:"Perseverance + Ingenuity", thumb:"https://i.ytimg.com/vi/TgcI8ur72x0/hqdefault.jpg"},
        {hw:"ingenuity", label:"Ingenuity Flight", thumb:"https://i.ytimg.com/vi/wMnOo2zcjXA/hqdefault.jpg"}
    ]
};

function getHardwareStatus(item){
    return hardwareStatus[item.id] || {status:"CUSTOM ENTRY", usable:"CHECK DETAILS", cls:"", video:null, title:item.name, desc:"No video is attached to this custom entry yet."};
}

function openHardwareVideo(id){
    const item=hardwareData.find(h=>h.id===id);
    const info=getHardwareStatus(item||{id});
    if(!info.video){
        openModal(id); return;
    }
    document.getElementById('videoModalTitle').innerText=info.title || item.name;
    document.getElementById('videoModalSub').innerText=`${item ? item.name : 'NASA HARDWARE'} • ${item ? item.target.toUpperCase() : 'SPACE'} VIDEO`;
    document.getElementById('videoModalDescription').innerText=info.desc;
    const frame=document.getElementById('hardwareVideoFrame');
    frame.src=`https://www.youtube.com/embed/${info.video}?rel=0&modestbranding=1`;
    document.getElementById('hardwareVideoModal').style.display='flex';
}
function closeHardwareVideo(){
    const frame=document.getElementById('hardwareVideoFrame');
    frame.src='';
    document.getElementById('hardwareVideoModal').style.display='none';
}

function renderHardwareVideoZones(){
    ['moon','mars'].forEach(target=>{
        const grid=document.getElementById(target+'VideoGrid');
        if(!grid) return;
        grid.innerHTML=videoCollections[target].map(v=>{
            const item=hardwareData.find(h=>h.id===v.hw);
            if(!item) return '';
            const info=getHardwareStatus(item);
            return `<div class="hardware-video-card">
                <div class="video-thumb" style="background-image:url('${v.thumb}')" onclick="openHardwareVideo('${item.id}')">
                    <div class="video-play">▶</div><div class="video-thumb-label">${v.label}</div>
                </div>
                <div class="video-card-body">
                    <div class="video-card-title">${info.title}</div>
                    <div class="video-card-status">${info.status} • ${info.usable}</div>
                    <button class="btn btn-outline video-watch-btn" type="button" onclick="openHardwareVideo('${item.id}')">▶ See Video</button>
                </div>
            </div>`;
        }).join('');
    });
}

function renderCards(dataset, gridId) {
    const grid = document.getElementById(gridId);
    if(!grid) return;
    grid.innerHTML = dataset.map(item => `
        <div class="card-inline" data-hw-id="${item.id}" onclick="openModal('${item.id}')">
            <div class="hardware-photo-wrap">
                <div class="photo-loading" id="photo-${item.id}">LOADING REAL NASA PHOTO…</div>
                <img class="hardware-photo" id="img-${item.id}" alt="${item.name}" style="display:none;">
                <div class="photo-shade"></div>
                <div class="photo-badge">${item.target === 'moon' ? '🌕 MOON' : '🔴 MARS'} • ${item.year}</div>
                <div class="photo-credit">NASA ARCHIVE</div>
            </div>
            <div class="card-content-side">
                <div class="card-sub">📅 ${item.year} | ${item.target.toUpperCase()} HARDWARE</div>
                <div class="card-title">${item.name}</div>
                <div class="hardware-simple-desc">${item.summary || item.purpose}</div>
                <div class="hardware-status-row"><span class="hw-status-badge ${getHardwareStatus(item).cls}">${getHardwareStatus(item).status}</span><span class="hw-status-badge">${getHardwareStatus(item).usable}</span></div>
                <button class="btn btn-outline detail-btn" type="button" onclick="event.stopPropagation(); openModal('${item.id}')">🔍 See Details</button>
                <button class="btn btn-primary detail-btn" type="button" onclick="event.stopPropagation(); openHardwareVideo('${item.id}')">▶ See Video</button>
            </div>
        </div>
    `).join('');
    loadHardwarePhotos(dataset);
}

async function loadHardwarePhotos(dataset = hardwareData) {
    const usedUrls = new Set(Array.from(document.querySelectorAll('.hardware-photo')).map(img => img.src).filter(Boolean));
    for (const item of dataset) {
        const img = document.getElementById(`img-${item.id}`);
        const loading = document.getElementById(`photo-${item.id}`);
        if (!img || !loading) continue;
        try {
            if (item.fixedPhoto) {
                img.src = item.fixedPhoto;
                await new Promise(resolve => { img.onload = resolve; img.onerror = resolve; });
                if (img.naturalWidth > 0) { loading.style.display='none'; img.style.display='block'; usedUrls.add(item.fixedPhoto); }
                else loading.innerHTML='NASA PHOTO UNAVAILABLE';
                continue;
            }
            const queries = item.photoQueries || [item.photoQuery || item.name];
            let chosenUrl = null;
            for (const query of queries) {
                const res = await fetch(`https://images-api.nasa.gov/search?q=${encodeURIComponent(query)}&media_type=image&page_size=30`);
                const data = await res.json();
                const candidates = (data?.collection?.items || []).filter(x => x.links?.some(l => l.render === 'image' || l.href));
                if (!candidates.length) continue;
                const nameTokens = query.toLowerCase().split(/\s+/).filter(t => t.length > 3);
                candidates.sort((a,b) => {
                    const score = x => {
                        const title = String(x.data?.[0]?.title || '').toLowerCase();
                        const desc = String(x.data?.[0]?.description || '').toLowerCase();
                        return nameTokens.reduce((n,w)=>n+(title.includes(w)?4:0)+(desc.includes(w)?1:0),0);
                    };
                    return score(b)-score(a);
                });
                const fresh = candidates.find(x => {
                    const l=x.links?.find(v=>v.render==='image')||x.links?.[0];
                    return l?.href && !usedUrls.has(l.href);
                });
                const any = candidates.find(x => (x.links?.find(v=>v.render==='image')||x.links?.[0])?.href);
                const chosen = fresh || any;
                const link = chosen?.links?.find(l=>l.render==='image') || chosen?.links?.[0];
                if (link?.href) { chosenUrl=link.href; break; }
            }
            if (chosenUrl) {
                img.src=chosenUrl;
                await new Promise(resolve => { img.onload=resolve; img.onerror=resolve; });
                if (img.naturalWidth > 0) { loading.style.display='none'; img.style.display='block'; usedUrls.add(chosenUrl); }
                else loading.innerHTML='NASA PHOTO UNAVAILABLE';
            } else loading.innerHTML='NASA PHOTO NOT FOUND';
        } catch (err) { loading.innerHTML='NASA PHOTO OFFLINE'; }
    }
}

function renderHardwareGallery() {
    const grid = document.getElementById('hardwareGalleryGrid');
    if (!grid) return;
    grid.innerHTML = hardwareData.map(item => `
        <div class="gallery-hw-card" onclick="openModal('${item.id}')">
            ${item.custom ? `<button class="gallery-delete-btn" type="button" onclick="event.stopPropagation(); deleteCustomHardware('${item.id}')">🗑 Remove</button>` : ''}
            <div id="gallery-photo-${item.id}" class="gallery-hw-loading">LOADING PHOTO…</div>
            <img id="gallery-img-${item.id}" class="gallery-hw-photo" alt="${item.name}" style="display:none;" />
            <div class="gallery-hw-body">
                <div class="gallery-hw-tag">${item.target === 'moon' ? '🌕 MOON' : '🔴 MARS'} • ${item.year}</div>
                <div class="gallery-hw-name">${item.name}</div>
                <div class="gallery-hw-click">🔍 See Details</div>
            </div>
        </div>
    `).join('');

    hardwareData.forEach(async item => {
        const img = document.getElementById(`gallery-img-${item.id}`);
        const loading = document.getElementById(`gallery-photo-${item.id}`);
        if (!img || !loading) return;
        try {
            if (item.fixedPhoto) {
                img.src = item.fixedPhoto;
                img.onload = () => { loading.style.display='none'; img.style.display='block'; };
                img.onerror = () => { loading.innerText='PHOTO UNAVAILABLE'; };
                return;
            }
            const queries = item.photoQueries || [item.name];
            let chosen = null;
            for (const query of queries) {
                const res = await fetch(`https://images-api.nasa.gov/search?q=${encodeURIComponent(query)}&media_type=image&page_size=12`);
                const data = await res.json();
                const items = data?.collection?.items || [];
                const candidates = items.filter(x => x.links?.some(l => l.render === 'image' || l.href));
                if (candidates.length) { chosen = candidates[0]; break; }
            }
            const link = chosen?.links?.find(l => l.render === 'image') || chosen?.links?.[0];
            if (link?.href) {
                img.src = link.href;
                img.onload = () => { loading.style.display='none'; img.style.display='block'; };
                img.onerror = () => { loading.innerText='PHOTO UNAVAILABLE'; };
            } else loading.innerText='PHOTO NOT FOUND';
        } catch(e) { loading.innerText='PHOTO OFFLINE'; }
    });
}

function saveCustomHardware() {
    const custom = hardwareData.filter(h => h.custom);
    try {
        localStorage.setItem('astroforge_custom_hardware_v2', JSON.stringify(custom));
        return true;
    } catch (e) {
        alert('Storage is full. Please use a smaller image.');
        return false;
    }
}

function loadCustomHardware() {
    try {
        const saved = JSON.parse(localStorage.getItem('astroforge_custom_hardware_v2') || '[]');
        if (!Array.isArray(saved)) return;
        saved.forEach(item => {
            if (item && item.id && item.custom && !hardwareData.some(h => h.id === item.id)) {
                hardwareData.push(item);
            }
        });
    } catch (e) {
        console.warn('Could not load saved custom hardware.', e);
    }
}

function deleteCustomHardware(id) {
    const item = hardwareData.find(h => h.id === id);
    if (!item || !item.custom) return;
    if (!confirm(`Delete "${item.name}" from your saved hardware gallery?`)) return;
    const index = hardwareData.findIndex(h => h.id === id);
    if (index >= 0) hardwareData.splice(index, 1);
    saveCustomHardware();
    initGrids();
    renderHardwareGallery();
    renderTimeline();
}

function compressUploadedImage(file) {
    return new Promise((resolve, reject) => {
        const reader = new FileReader();
        reader.onload = () => {
            const img = new Image();
            img.onload = () => {
                const maxSide = 1000;
                const scale = Math.min(1, maxSide / Math.max(img.width, img.height));
                const canvas = document.createElement('canvas');
                canvas.width = Math.max(1, Math.round(img.width * scale));
                canvas.height = Math.max(1, Math.round(img.height * scale));
                const ctx = canvas.getContext('2d');
                ctx.drawImage(img, 0, 0, canvas.width, canvas.height);
                resolve(canvas.toDataURL('image/jpeg', 0.78));
            };
            img.onerror = reject;
            img.src = reader.result;
        };
        reader.onerror = reject;
        reader.readAsDataURL(file);
    });
}

function openAddHardwareModal(){ document.getElementById('addHardwareModal').style.display='flex'; }
function closeAddHardwareModal(){ document.getElementById('addHardwareModal').style.display='none'; }

async function addCustomHardware(){
    const name = document.getElementById('addHwName').value.trim();
    const target = document.getElementById('addHwTarget').value;
    const year = document.getElementById('addHwYear').value.trim() || '—';
    const mission = document.getElementById('addHwMission').value.trim() || 'Custom Entry';
    const imageUrl = document.getElementById('addHwImage').value.trim();
    const imageFile = document.getElementById('addHwImageFile').files[0];
    const summary = document.getElementById('addHwSummary').value.trim() || 'Custom hardware entry added by the visitor.';

    if (!name) { alert('Please enter a hardware name.'); return; }
    if (!imageUrl && !imageFile) { alert('Please add a hardware photo URL or upload a photo.'); return; }

    let fixedPhoto = imageUrl || '';
    if (imageFile) {
        try {
            fixedPhoto = await compressUploadedImage(imageFile);
        } catch (e) {
            alert('Could not read that image. Please try another photo.');
            return;
        }
    }

    const id = 'custom-' + Date.now();
    hardwareData.push({
        id, custom:true, name, target, year, mission,
        loc: 'Custom entry — location not specified',
        summary,
        purpose: summary,
        how: 'Custom entry — engineering details not specified.',
        happened: 'Custom hardware entry saved in this browser.',
        why: 'Custom entry — reason left behind not specified.',
        science: 'Custom entry — scientific legacy not specified.',
        fixedPhoto,
        photoQueries: []
    });

    if (!saveCustomHardware()) {
        hardwareData.pop();
        return;
    }
    closeAddHardwareModal();
    ['addHwName','addHwYear','addHwMission','addHwImage','addHwSummary'].forEach(id => document.getElementById(id).value='');
    document.getElementById('addHwImageFile').value = '';
    initGrids();
    renderHardwareGallery();
    renderTimeline();
}

function initGrids() {
    if (!window.__customHardwareLoaded) { loadCustomHardware(); window.__customHardwareLoaded = true; }

    renderCards(hardwareData.filter(h => h.target === 'moon'), 'moonGrid');
    renderCards(hardwareData.filter(h => h.target === 'mars'), 'marsGrid');
    renderCards(hardwareData, 'explorerGrid');
    renderHardwareVideoZones();
}

function filterHardware(type) {
    if (type === 'all') renderCards(hardwareData, 'explorerGrid');
    else renderCards(hardwareData.filter(h => h.target === type), 'explorerGrid');
}

function openSolarHardware(target){
    const section=document.getElementById(target);
    if(!section) return;
    section.scrollIntoView({behavior:'smooth',block:'start'});
    setTimeout(()=>showPlanetStep(target,2),450);
}

function initSolarSystem() {
    const box = document.getElementById('solarCanvas');
    if (!box) return;
    box.innerHTML = '';
    if (typeof THREE === 'undefined') {
        box.innerHTML = '<div class="solar-fallback">⚠️ 3D engine could not load.<br><small>Open ASTROFORGE with an internet connection and refresh.</small></div>';
        return;
    }
    const width=Math.max(box.clientWidth,320), height=Math.max(box.clientHeight,310);
    const scene=new THREE.Scene();
    const camera=new THREE.PerspectiveCamera(42,width/height,.1,1000);
    const renderer=new THREE.WebGLRenderer({antialias:true,alpha:true,powerPreference:'high-performance'});
    renderer.setPixelRatio(Math.min(window.devicePixelRatio||1,2));
    renderer.setSize(width,height,false);
    renderer.domElement.style.width='100%'; renderer.domElement.style.height='100%';
    box.appendChild(renderer.domElement);

    scene.add(new THREE.AmbientLight(0x9fc8ff,.72));
    const sunLight=new THREE.PointLight(0xffd38a,3.6,100); sunLight.position.set(0,0,0); scene.add(sunLight);

    // Deep-space star field
    const starGeo=new THREE.BufferGeometry(), starCount=1100, starPos=new Float32Array(starCount*3);
    for(let i=0;i<starCount;i++){
        starPos[i*3]=(Math.random()-.5)*52;
        starPos[i*3+1]=(Math.random()-.5)*30;
        starPos[i*3+2]=(Math.random()-.5)*52;
    }
    starGeo.setAttribute('position',new THREE.BufferAttribute(starPos,3));
    scene.add(new THREE.Points(starGeo,new THREE.PointsMaterial({color:0xffffff,size:.035,transparent:true,opacity:.82})));

    // Sun + soft corona
    const sun=new THREE.Mesh(new THREE.SphereGeometry(1.12,40,40),new THREE.MeshBasicMaterial({color:0xffb300}));
    scene.add(sun);
    const corona1=new THREE.Mesh(new THREE.SphereGeometry(1.32,32,32),new THREE.MeshBasicMaterial({color:0xff8a00,transparent:true,opacity:.10,depthWrite:false}));
    const corona2=new THREE.Mesh(new THREE.SphereGeometry(1.55,32,32),new THREE.MeshBasicMaterial({color:0xffc928,transparent:true,opacity:.045,depthWrite:false}));
    scene.add(corona1,corona2);

    const earthR=3.45,marsR=5.85;
    function orbit(r,c){
        const g=new THREE.RingGeometry(r-.018,r+.018,160),m=new THREE.MeshBasicMaterial({color:c,side:THREE.DoubleSide,transparent:true,opacity:.42});
        const o=new THREE.Mesh(g,m); o.rotation.x=Math.PI/2; scene.add(o);
    }
    orbit(earthR,0x38bdf8); orbit(marsR,0xfb7b45);

    const earthGroup=new THREE.Group();
    const earth=new THREE.Mesh(new THREE.SphereGeometry(.50,36,36),new THREE.MeshPhongMaterial({color:0x1976d2,emissive:0x062a46,emissiveIntensity:.38,shininess:35}));
    earthGroup.add(earth);
    const moonOrbit=new THREE.Mesh(new THREE.RingGeometry(.72,.73,64),new THREE.MeshBasicMaterial({color:0xcbd5e1,side:THREE.DoubleSide,transparent:true,opacity:.25}));
    moonOrbit.rotation.x=Math.PI/2; earthGroup.add(moonOrbit);
    const moon=new THREE.Mesh(new THREE.SphereGeometry(.145,22,22),new THREE.MeshPhongMaterial({color:0xd1d5db,emissive:0x343b46,emissiveIntensity:.22,shininess:12}));
    earthGroup.add(moon); scene.add(earthGroup);

    const mars=new THREE.Mesh(new THREE.SphereGeometry(.42,36,36),new THREE.MeshPhongMaterial({color:0xc94d2f,emissive:0x4d170d,emissiveIntensity:.32,shininess:12}));
    scene.add(mars);

    camera.position.set(0,7.9,11.8); camera.lookAt(0,0,0);
    let angle=0;
    function animate(){
        requestAnimationFrame(animate);
        angle+=.0048;
        earthGroup.position.set(Math.cos(angle)*earthR,0,Math.sin(angle)*earthR);
        earth.rotation.y+=.010;
        const ma=angle*7.2;
        moon.position.set(Math.cos(ma)*.73,0,Math.sin(ma)*.73);
        mars.position.set(Math.cos(angle*.52)*marsR,0,Math.sin(angle*.52)*marsR);
        mars.rotation.y+=.008;
        sun.rotation.y+=.0025;
        corona1.scale.setScalar(1+Math.sin(angle*9)*.018);
        corona2.scale.setScalar(1+Math.sin(angle*6+1)*.028);
        renderer.render(scene,camera);
    }
    animate();
    const resize=()=>{const w=Math.max(box.clientWidth,320),h=Math.max(box.clientHeight,310);camera.aspect=w/h;camera.updateProjectionMatrix();renderer.setSize(w,h,false);};
    window.addEventListener('resize',resize); setTimeout(resize,120);
}

function initMiniSpinners() {
    if(typeof THREE === 'undefined') return;
    const moonBox = document.getElementById('miniMoonCanvas');
    if(moonBox) {
        moonBox.innerHTML = '';
        const mScene = new THREE.Scene();
        const mCamera = new THREE.PerspectiveCamera(45, 1, 0.1, 100);
        const mRenderer = new THREE.WebGLRenderer({ antialias: true, alpha: true });
        mRenderer.setSize(110, 110);
        moonBox.appendChild(mRenderer.domElement);
        mScene.add(new THREE.AmbientLight(0xffffff, 1.4));
        const moonMesh = new THREE.Mesh(new THREE.SphereGeometry(1.6, 32, 32), new THREE.MeshPhongMaterial({ color: 0xd1d5db, emissive: 0x4b5563, emissiveIntensity: 0.3, shininess: 30 }));
        mScene.add(moonMesh);
        mCamera.position.z = 4;
        function animMoon() {
            requestAnimationFrame(animMoon);
            moonMesh.rotation.y += 0.012;
            mRenderer.render(mScene, mCamera);
        }
        animMoon();
    }

    const marsBox = document.getElementById('miniMarsCanvas');
    if(marsBox) {
        marsBox.innerHTML = '';
        const marScene = new THREE.Scene();
        const marCamera = new THREE.PerspectiveCamera(45, 1, 0.1, 100);
        const marRenderer = new THREE.WebGLRenderer({ antialias: true, alpha: true });
        marRenderer.setSize(110, 110);
        marsBox.appendChild(marRenderer.domElement);
        marScene.add(new THREE.AmbientLight(0xffffff, 1.4));
        const marsMesh = new THREE.Mesh(new THREE.SphereGeometry(1.6, 32, 32), new THREE.MeshPhongMaterial({ color: 0xf97316, emissive: 0x991b1b, emissiveIntensity: 0.3, shininess: 20 }));
        marScene.add(marsMesh);
        marCamera.position.z = 4;
        function animMars() {
            requestAnimationFrame(animMars);
            marsMesh.rotation.y += 0.012;
            marRenderer.render(marScene, marCamera);
        }
        animMars();
    }
}

async function openModal(id) {
    const item = hardwareData.find(h => h.id === id) || hardwareData[0];
    document.getElementById('mTitle').innerText = item.name;
    document.getElementById('mSub').innerText = `${item.target.toUpperCase()} HARDWARE | ${item.mission} • ${item.year}`;
    document.querySelector('#mOverview span').innerText = item.summary || item.purpose;
    document.getElementById('mMission').innerText = `${item.mission} (${item.year})`;
    document.getElementById('mLoc').innerText = item.loc;
    document.getElementById('mPurpose').innerText = item.purpose;
    document.getElementById('mHow').innerText = item.how;
    document.getElementById('mHappened').innerText = item.happened;
    document.getElementById('mWhy').innerText = item.why;
    document.getElementById('mScience').innerText = item.science;
    const statusInfo=getHardwareStatus(item);
    document.getElementById('mStatus').innerText=statusInfo.status;
    document.getElementById('mUsable').innerText=statusInfo.usable;
    document.getElementById('modalVideoBtn').onclick=()=>openHardwareVideo(item.id);
    document.getElementById('modalVideoBtn').style.display=statusInfo.video ? 'inline-flex' : 'none';

    const modalPhotoWrap = document.getElementById('modalPhotoWrap');
    const modalPhoto = document.getElementById('modalHardwarePhoto');
    const sourceImg = document.getElementById(`img-${item.id}`);
    modalPhotoWrap.style.display = 'block';
    modalPhoto.removeAttribute('src');
    modalPhoto.alt = item.name;
    modalPhotoWrap.querySelector('.modal-photo-credit').textContent = 'NASA ARCHIVE • REAL HARDWARE PHOTO • LOADING…';
    await loadHardwarePhotos([item]);
    const refreshedImg = document.getElementById(`img-${item.id}`);
    const photoSrc = item.fixedPhoto || (refreshedImg && refreshedImg.src ? refreshedImg.src : '');
    if (photoSrc && photoSrc !== location.href) {
        modalPhoto.src = photoSrc;
        modalPhoto.onload = () => { modalPhotoWrap.querySelector('.modal-photo-credit').textContent = 'NASA ARCHIVE • REAL HARDWARE PHOTO'; };
        modalPhoto.onerror = () => { modalPhotoWrap.querySelector('.modal-photo-credit').textContent = 'NASA PHOTO UNAVAILABLE'; };
    } else {
        modalPhotoWrap.style.display = 'none';
    }

    document.getElementById('modalLiveSearchBtn').onclick = () => {
        closeModal();
        document.getElementById('nasaQuery').value = item.name;
        document.location.hash = '#archive';
        searchNASA();
    };

    document.getElementById('hwModal').style.display = 'flex';
    speakText(`Inspecting ${item.name}. ${item.purpose}`);
}

function openTeamModal() { document.getElementById('teamModal').style.display = 'flex'; }
function closeTeamModal() { document.getElementById('teamModal').style.display = 'none'; }
function closeModal() { document.getElementById('hwModal').style.display = 'none'; }
window.addEventListener('click', function(e){
    const missionModal=document.getElementById('missionTimelineModal');
    const videoModal=document.getElementById('hardwareVideoModal');
    if(e.target===missionModal) closeMissionTimeline();
    if(e.target===videoModal) closeHardwareVideo();
});


function openGoogleSearch() {
    const query = document.getElementById('nasaQuery').value || 'NASA space hardware relics';
    window.open(`https://www.google.com/search?q=${encodeURIComponent(query)}`, '_blank');
}


const planetFlow = {
  moon: {
    icon:'🌕', title:'The Moon',
    overview:'Human missions left scientific instruments and mobility hardware across the lunar surface. Start with the mission story, then open individual hardware.',
    how:'Apollo-era lunar hardware had to survive vacuum, extreme temperature swings, low gravity and strict mass limits. Passive instruments such as retroreflectors need no power, while the Lunar Roving Vehicle used electric drive and steering.',
    note:'Tip for students: open Hardware first, then See Video to connect the engineering design with real mission footage.',
    hardware:['apollo11-lrrr','apollo15-lrv','apollo17-lrv','apollo14-lr3','apollo11-eagle'],
    videos:['apollo11-lrrr','apollo15-lrv','apollo17-lrv']
  },
  mars: {
    icon:'🔴', title:'Mars',
    overview:'Mars exploration combines autonomous rovers, landing systems and experimental aircraft. Explore the hardware in small steps instead of reading everything at once.',
    how:'Mars hardware must operate with communication delay, dusty terrain, low temperatures and a thin atmosphere. Rovers use autonomous systems for navigation and science, while Ingenuity demonstrated powered flight in the Martian atmosphere.',
    note:'Tip for students: compare the rover, sky-crane and helicopter to see three very different engineering solutions for Mars.',
    hardware:['curiosity-rover','perseverance-rover','ingenuity','skycrane','insight-lander'],
    videos:['curiosity-rover','perseverance-rover','ingenuity']
  }
};

function flowItem(id){ return hardwareData.find(h=>h.id===id); }
async function loadPlanetIntroPhotos(target){
  const box=document.getElementById(target+'IntroPhotos'); if(!box)return;
  const imgs=[...box.querySelectorAll('img[data-planet-photo]')];
  for(const img of imgs){
    const h=flowItem(img.dataset.planetPhoto); if(!h)continue;
    if(h.fixedPhoto){ img.src=h.fixedPhoto; img.onerror=()=>fetchPlanetPhoto(img,h); } else { await fetchPlanetPhoto(img,h); }
  }
}
async function fetchPlanetPhoto(img,h){
  try{ const q=(h.photoQueries||[h.name])[0]; const r=await fetch(`https://images-api.nasa.gov/search?q=${encodeURIComponent(q)}&media_type=image&page_size=8`); const d=await r.json(); const item=d?.collection?.items?.find(v=>v.links?.some(l=>l.render==='image'||l.href)); const link=item?.links?.find(v=>v.render==='image')||item?.links?.[0]; if(link?.href){img.src=link.href;return;} }catch(e){}
  img.src='https://images-assets.nasa.gov/image/PIA23882/PIA23882~orig.jpg';
}

function showPlanetStep(target,step){
  const cfg=planetFlow[target], box=document.getElementById(target+'FlowContent'), tabs=document.querySelectorAll('#'+target+'Tabs .progressive-tab');
  if(!cfg||!box)return;
  tabs.forEach((b,i)=>b.classList.toggle('active',i===step-1));
  if(step===1){
    const photoIds=cfg.hardware;
    box.innerHTML=`<div class="progressive-intro"><div><h3>${cfg.icon} ${cfg.title} — Start Here</h3><p>${cfg.overview}</p><div class="progressive-next"><button class="btn btn-primary" onclick="showPlanetStep('${target}',2)">Next: Hardware →</button><button class="btn btn-outline" onclick="showPlanetStep('${target}',4)">▶ Jump to Video</button></div></div><div class="progressive-big-icon">${cfg.icon}</div></div><div class="planet-photo-strip" id="${target}IntroPhotos">${photoIds.map(id=>{const h=flowItem(id);return `<div class="planet-photo-card"><span class="planet-photo-tag">NASA HARDWARE</span><img data-planet-photo="${id}" src="${h?.fixedPhoto||''}" alt="${h?.name||'NASA hardware'}"><div class="planet-photo-caption">${h?.name||''}</div></div>`}).join('')}</div>`;
    loadPlanetIntroPhotos(target);
  } else if(step===2){
    const cards=cfg.hardware.map(id=>{const h=flowItem(id);if(!h)return '';const st=getHardwareStatus(h);return `<div class="flow-hw-card"><div class="flow-hw-icon">${target==='moon'?'🛰️':'🤖'}</div><div class="flow-hw-year">${h.year} • ${h.mission}</div><h4>${h.name}</h4><p>${h.summary}</p><div class="flow-hw-actions"><button class="btn btn-outline" onclick="openModal('${h.id}')">🔍 Details</button><button class="btn btn-primary" onclick="openHardwareVideo('${h.id}')">▶ Video</button></div></div>`}).join('');
    box.innerHTML=`<h3>🔧 Key Hardware</h3><p style="margin-bottom:13px;">Only a few important examples are shown here. Open <b>Details</b> for the engineering and <b>Video</b> for real mission footage.</p><div class="flow-hardware-grid">${cards}</div><div class="progressive-next"><button class="btn btn-primary" onclick="showPlanetStep('${target}',3)">Next: How It Works →</button></div>`;
  } else if(step===3){
    box.innerHTML=`<h3>⚙️ How the Hardware Works</h3><div class="flow-note">${cfg.how}</div><div class="progressive-next"><button class="btn btn-primary" onclick="showPlanetStep('${target}',4)">Next: See Real Video →</button><button class="btn btn-outline" onclick="showPlanetStep('${target}',2)">← Back to Hardware</button></div>`;
  } else {
    const vids=cfg.videos.map(id=>{const h=flowItem(id), st=getHardwareStatus(h);if(!h||!st.video)return '';const vc=videoCollections[target].find(v=>v.hw===id);return `<div class="flow-video-card"><div class="flow-video-thumb" style="background-image:url('${vc?.thumb||''}')" onclick="openHardwareVideo('${id}')"></div><div class="flow-video-body"><h4>${h.name}</h4><p>${st.status} • ${st.usable}</p><button class="btn btn-primary" onclick="openHardwareVideo('${id}')">▶ See Video</button></div></div>`}).join('');
    box.innerHTML=`<h3>🎥 Real Mission Footage</h3><p style="margin-bottom:13px;">Click any video to watch it inside ASTROFORGE. Start with one — you can explore the others later.</p><div class="flow-video-grid">${vids}</div><div class="progressive-next"><button class="btn btn-outline" onclick="showPlanetStep('${target}',1)">↺ Start Again</button></div>`;
  }
}

async function openPlanetModal(target) {
    const cfg = planetFlow[target];
    const modalPhotoWrap = document.getElementById('modalPhotoWrap');
    const modalPhoto = document.getElementById('modalHardwarePhoto');
    const firstHardware = flowItem(cfg.hardware[0]);
    document.querySelector('#mOverview span').innerText = target === 'moon'
        ? 'Explore the historic lunar hardware represented in this section, including Apollo-era laser ranging and surface mobility systems.'
        : 'Explore the Mars hardware represented in this section, including powered flight and the sky-crane landing architecture.';
    modalPhotoWrap.style.display='block';
    modalPhoto.alt = firstHardware?.name || `${target} hardware`;
    modalPhoto.src = firstHardware?.fixedPhoto || explorerImage(firstHardware) || '';
    modalPhotoWrap.querySelector('.modal-photo-credit').textContent = 'NASA ARCHIVE • REAL HARDWARE PHOTO';
    if(firstHardware && !modalPhoto.src){ await loadHardwarePhotos([firstHardware]); }
    if(firstHardware && firstHardware.fixedPhoto){ modalPhoto.src = firstHardware.fixedPhoto; }
    modalPhoto.onerror = async () => { if(firstHardware){ await loadHardwarePhotos([firstHardware]); const img=document.getElementById(`img-${firstHardware.id}`); if(img?.src) modalPhoto.src=img.src; } };
    document.getElementById('mTitle').innerText = target === 'moon' ? 'Moon Exploration & Orbital Hub' : 'Mars Exploration & Surface Hub';
    document.getElementById('mSub').innerText = `${target.toUpperCase()} DEEP ARCHIVE & TELEMETRY HUB`;
    document.getElementById('mMission').innerText = target === 'moon' ? 'Multiple Lunar Landings (Apollo 11, 15)' : 'Mars 2020 & Curiosity Missions';
    document.getElementById('mLoc').innerText = target === 'moon' ? 'Lunar Surface Coordinates (Multi-site)' : 'Martian Crater Basins (Jezero & Gale)';
    document.getElementById('mPurpose').innerText = target === 'moon' ? 'Comprehensive lunar surface artifact tracking, laser ranging telemetry, and retroreflector arrays.' : 'Advanced Martian atmospheric flight demonstration, soil sampling, and heavy rover descent systems.';
    document.getElementById('mHow').innerText = target === 'moon' ? 'Utilizes passive quartz corner-cube optical prisms reflecting 532nm laser beams sent directly from Earth observatories.' : 'Employs autonomous rotorcraft aerodynamics, rocket-powered sky-cranes, and nuclear radioisotope thermoelectric power.';
    document.getElementById('mHappened').innerText = target === 'moon' ? 'All historical lunar retroreflectors and rovers remain fully preserved in ultra-low vacuum and zero moisture.' : 'Rovers and helicopters continue scientific monitoring or rest in stable dry dust sediment.';
    document.getElementById('mWhy').innerText = 'Mass constraints during lunar and martian ascent stages prevent return transport of heavy landing brackets and base structures.';
    document.getElementById('mScience').innerText = target === 'moon' ? 'Provides absolute millimeter-precision measurements of earth-moon gravitational recession and internal lunar core dynamics.' : 'Unlocks atmospheric physics of thin CO2 worlds and paves the way for safe crewed Martian colonization.';
    
    document.getElementById('hwModal').style.display = 'flex';
}

const missionTimelineData = [
    {
        year:"1969", target:"Moon", mission:"Apollo 11",
        title:"First Crewed Moon Landing",
        query:"Apollo 11 Moon landing",
        objective:"Land humans on the Moon, conduct surface exploration, deploy experiments and return safely to Earth.",
        key:"Launched July 16, 1969; lunar landing July 20, 1969; splashdown July 24, 1969."
    },
    {
        year:"1971", target:"Moon", mission:"Apollo 15",
        title:"First Apollo Lunar Rover Mission",
        query:"Apollo 15 Lunar Roving Vehicle",
        objective:"Explore the Hadley-Apennine region with greater surface mobility and conduct lunar science experiments.",
        key:"Launched July 26, 1971; first Apollo mission to use the Lunar Roving Vehicle."
    },
    {
        year:"1972", target:"Moon", mission:"Apollo 17",
        title:"Final Apollo Lunar Landing",
        query:"Apollo 17 Moon rover",
        objective:"Carry out the final Apollo lunar surface exploration and collect extensive geological samples.",
        key:"Launched December 7, 1972; final Apollo mission to land humans on the Moon."
    },
    {
        year:"2012", target:"Mars", mission:"Mars Science Laboratory",
        title:"Curiosity & Sky Crane Landing",
        query:"Curiosity rover sky crane Mars",
        objective:"Deliver the Curiosity rover safely to Gale Crater using the powered sky-crane landing architecture.",
        key:"Curiosity landed in Gale Crater on August 6, 2012."
    },
    {
        year:"2021", target:"Mars", mission:"Mars 2020",
        title:"Perseverance & Ingenuity",
        query:"Perseverance Ingenuity Mars",
        objective:"Search for signs of ancient life, collect samples, and demonstrate powered flight on another planet.",
        key:"Perseverance and Ingenuity landed in Jezero Crater in February 2021; Ingenuity's first powered flight was April 19, 2021."
    }
];

function missionFallbackImage(target){
    return target === "Moon"
        ? "https://images-assets.nasa.gov/image/AS11-40-5903/AS11-40-5903~orig.jpg"
        : "https://images-assets.nasa.gov/image/PIA26344/PIA26344~orig.jpg";
}

async function getMissionImage(query, target){
    try{
        const res = await fetch(`https://images-api.nasa.gov/search?q=${encodeURIComponent(query)}&media_type=image&page_size=10`);
        const data = await res.json();
        const items = data.collection && data.collection.items ? data.collection.items : [];
        for(const item of items){
            const href = item.links && item.links[0] ? item.links[0].href : "";
            if(href && /^https?:\/\//i.test(href)) return href;
        }
    }catch(e){}
    return missionFallbackImage(target);
}

function openMissionTimeline(){
    const modal=document.getElementById('missionTimelineModal');
    const grid=document.getElementById('missionTimelineGrid');
    if(!modal || !grid) return;
    modal.style.display='flex';
    grid.innerHTML=missionTimelineData.map((m,i)=>`
        <article class="mission-card">
            <img id="missionImg${i}" src="${missionFallbackImage(m.target)}" alt="${m.mission} mission">
            <div class="mission-card-body">
                <div class="mission-year">📅 ${m.year} • ${m.target.toUpperCase()}</div>
                <h3>${m.mission}</h3>
                <p><strong>${m.title}</strong></p>
                <p>${m.objective}</p>
                <div class="mission-meta">🔎 ${m.key}</div>
            </div>
        </article>
    `).join('');
    missionTimelineData.forEach(async (m,i)=>{
        const img=await getMissionImage(m.query,m.target);
        const el=document.getElementById(`missionImg${i}`);
        if(el && img) el.src=img;
    });
}

function closeMissionTimeline(){
    const modal=document.getElementById('missionTimelineModal');
    if(modal) modal.style.display='none';
}

function renderTimeline() {
    /* Timeline is intentionally compact on the homepage.
       Full mission details are opened with See Mission Timeline & Details. */
}

setInterval(() => {
    const distEl = document.getElementById('voyagerDist');
    if (distEl) {
        let curr = parseInt(distEl.innerText.replace(/,/g, ''));
        distEl.innerText = (curr + 17).toLocaleString() + ' km';
    }
}, 1000);

let gameState = { target: '', payload: '' };
function selectGameOption(key, val, el) {
    gameState[key] = val;
    el.parentNode.querySelectorAll('.option-card').forEach(c => c.classList.remove('selected'));
    el.classList.add('selected');
}
function nextGameStep(step) {
    document.querySelectorAll('.game-step').forEach(s => s.classList.remove('active'));
    document.getElementById(`gStep${step}`).classList.add('active');
    if (step === 3) {
        document.getElementById('gameResultTitle').innerText = `🚀 Mission Successful on ${gameState.target}!`;
        document.getElementById('gameResultDesc').innerText = `Your ${gameState.payload} payload has been successfully deployed on ${gameState.target}.`;
    }
}
function resetGame() {
    gameState = { target: '', payload: '' };
    document.querySelectorAll('.option-card').forEach(c => c.classList.remove('selected'));
    nextGameStep(1);
}

// 30 STEM Quiz Questions
const quizData = [
    { q: "1. What equipment left by Apollo 11 allows laser ranging measurements from Earth?", opts: ["Seismometer Dome", "Retroreflector Array", "Lunar Rover", "Solar Panel"], ans: 1 },
    { q: "2. How many corner-cube silica glass prisms are on Apollo 11's retroreflector?", opts: ["50", "100", "200", "500"], ans: 1 },
    { q: "3. What helicopter completed 72 operational flights on Mars?", opts: ["Curiosity", "Ingenuity", "Perseverance", "Opportunity"], ans: 1 },
    { q: "4. How is Curiosity lowered onto Mars' surface before the Sky Crane crashes?", opts: ["Airbags", "Parachute", "Nylon Tethers", "Magnetic Rails"], ans: 2 },
    { q: "5. Which Apollo mission introduced the Lunar Roving Vehicle (LRV-1)?", opts: ["Apollo 11", "Apollo 13", "Apollo 15", "Apollo 17"], ans: 2 },
    { q: "6. What is the primary material used for the Apollo 15 LRV chassis?", opts: ["Titanium Steel", "2219 Aluminum Alloy", "Carbon Fiber", "Lead Composite"], ans: 1 },
    { q: "7. In which Martian crater did Ingenuity and Perseverance land?", opts: ["Gale Crater", "Jezero Crater", "Gusev Crater", "Endeavour Crater"], ans: 1 },
    { q: "8. What gas primarily makes up the Martian atmosphere?", opts: ["Oxygen", "Nitrogen", "Carbon Dioxide", "Hydrogen"], ans: 2 },
    { q: "9. Approximately what percentage of Earth's atmospheric pressure is Mars' atmosphere?", opts: ["1%", "10%", "50%", "80%"], ans: 0 },
    { q: "10. What power source drives the Ingenuity Mars Helicopter?", opts: ["Nuclear RTG", "Solar-recharged Lithium-ion batteries", "Hydrogen Fuel Cells", "Thermal Plugs"], ans: 1 },
    { q: "11. What is the approximate speed of Ingenuity's counter-rotating blades?", opts: ["1,200 RPM", "2,400 RPM", "5,000 RPM", "800 RPM"], ans: 1 },
    { q: "12. Which spacecraft holds the record for furthest human-made object from Earth?", opts: ["Pioneer 10", "Voyager 1", "New Horizons", "Cassini"], ans: 1 },
    { q: "13. What landing mechanism did the Mars Science Laboratory use in 2012?", opts: ["Airbag Bounce", "Sky Crane System", "Direct Skids", "Hovercrafting"], ans: 1 },
    { q: "14. What is the main purpose of lunar laser retroreflectors?", opts: ["To communicate with aliens", "To measure Earth-Moon distance precisely", "To generate solar power", "To melt lunar ice"], ans: 1 },
    { q: "15. Which Apollo mission first landed humans on the Moon?", opts: ["Apollo 8", "Apollo 11", "Apollo 12", "Apollo 16"], ans: 1 },
    { q: "16. What is the name of the landing site of Apollo 11?", opts: ["Sea of Tranquility", "Ocean of Storms", "Sea of Serenity", "Crater Tycho"], ans: 0 },
    { q: "17. What type of mirrors are inside the Apollo laser retroreflectors?", opts: ["Concave glass", "Corner-cube quartz prisms", "Flat metallic sheets", "Convex silicon lenses"], ans: 1 },
    { q: "18. Why are old rovers and descent stages left behind on planetary bodies?", opts: ["They are radioactive", "Return weight and launch payload limits", "They melt over time", "International space laws ban returns"], ans: 1 },
    { q: "19. Which rover landed on Mars alongside the Sky Crane system in 2012?", opts: ["Spirit", "Opportunity", "Curiosity", "Sojourner"], ans: 2 },
    { q: "20. What chemical propellant powered the MSL descent stage rockets?", opts: ["Hydrazine", "Liquid Methane", "Kerosene", "Liquid Hydrogen"], ans: 0 },
    { q: "21. Approximately how far is the Moon from Earth on average?", opts: ["150,000 km", "384,400 km", "1,200,000 km", "42,000 km"], ans: 1 },
    { q: "22. Which space agency operated the Ingenuity helicopter?", opts: ["ESA", "NASA", "ISRO", "Roscosmos"], ans: 1 },
    { q: "23. How many total flights did Ingenuity complete before retirement?", opts: ["5 flights", "25 flights", "50 flights", "72 flights"], ans: 3 },
    { q: "24. What caused Ingenuity's eventual end of mission?", opts: ["Ran out of sunlight", "Rotor tip blade damage during landing", "Extreme core overheating", "Communication antenna failure"], ans: 1 },
    { q: "25. Which theory was tested with high precision using lunar retroreflectors?", opts: ["Quantum Entanglement", "General Theory of Relativity", "String Theory", "Plate Tectonics"], ans: 1 },
    { q: "26. What is the primary advantage of passive optical retroreflectors?", opts: ["They require zero electrical power", "They transmit voice data", "They move around autonomously", "They heat up the lunar soil"], ans: 0 },
    { q: "27. In what year did Apollo 15 land on the Moon?", opts: ["1969", "1971", "1972", "1975"], ans: 1 },
    { q: "28. What geological region was explored by Apollo 15?", opts: ["Hadley-Apennine volcanic rille", "Crater Copernicus", "Fra Mauro highlands", "South Pole-Aitken basin"], ans: 0 },
    { q: "29. What is the approximate weight of the Curiosity rover lowered by the sky crane?", opts: ["300 kg", "900 kg", "2,500 kg", "50 kg"], ans: 1 },
    { q: "30. What is the primary science goal of studying deep space and planetary relics?", opts: ["To preserve historical legacy and understand space engineering limits", "To mine gold on Mars", "To build space hotels", "To clean up space debris"], ans: 0 }
];

let qIdx = 0; let qScore = 0;
function renderQuiz() {
    const q = quizData[qIdx];
    const qText = document.getElementById('qText');
    if(!qText) return;
    document.getElementById('qProgress').innerText = `Question ${qIdx + 1} of 30`;
    qText.innerText = q.q;
    const optsBox = document.getElementById('qOptions');
    optsBox.innerHTML = q.opts.map((opt, i) => `
        <button class="quiz-opt" onclick="answerQuiz(${i})">${opt}</button>
    `).join('');
}
function playQuizWrongSound(){
    try{
        const AC=window.AudioContext||window.webkitAudioContext;
        if(!AC) return;
        const ctx=new AC();
        const osc=ctx.createOscillator(), gain=ctx.createGain();
        osc.type='square'; osc.frequency.setValueAtTime(180,ctx.currentTime);
        osc.frequency.exponentialRampToValueAtTime(95,ctx.currentTime+0.18);
        gain.gain.setValueAtTime(0.055,ctx.currentTime);
        gain.gain.exponentialRampToValueAtTime(0.001,ctx.currentTime+0.22);
        osc.connect(gain); gain.connect(ctx.destination); osc.start(); osc.stop(ctx.currentTime+0.22);
        setTimeout(()=>ctx.close(),300);
    }catch(e){}
}
function answerQuiz(selected) {
    const q = quizData[qIdx];
    const feedback = document.getElementById('quizFeedback');
    const optionButtons = document.querySelectorAll('.quiz-opt');
    feedback.style.display = 'block';
    optionButtons.forEach((b,i)=>b.classList.remove('quiz-wrong-react'));
    if (selected === q.ans) {
        qScore += 10;
        document.getElementById('qScore').innerText = qScore;
        feedback.innerHTML = "🎉✨ <strong>Correct!</strong> 🚀 Great job — you got it right!"; feedback.style.color = "var(--green)"; feedback.classList.add("quiz-correct-pop");
    } else {
        if(optionButtons[selected]) optionButtons[selected].classList.add('quiz-wrong-react');
        feedback.innerHTML = `❌ <strong>Wrong!</strong> Correct Answer: ${q.opts[q.ans]}`; feedback.style.color = "var(--red)";
        playQuizWrongSound();
    }
    setTimeout(() => {
        feedback.style.display = 'none';
        feedback.classList.remove('quiz-correct-pop');
        qIdx++;
        if (qIdx < quizData.length) renderQuiz();
        else {
            document.getElementById('qText').innerText = `🎉 Quiz Finished! Score: ${qScore}/300`;
            document.getElementById('qOptions').innerHTML = `<button class="btn btn-primary" onclick="resetQuiz()">🔄 Restart Quiz</button>`;
        }
    }, 1200);
}
function resetQuiz() { qIdx = 0; qScore = 0; document.getElementById('qScore').innerText = 0; renderQuiz(); }

async function searchNASA() {
    const query = document.getElementById('nasaQuery').value || 'Apollo Retroreflector';
    const box = document.getElementById('nasaResults');
    box.innerHTML = '<p style="color:var(--neon-blue); text-align:center; grid-column:1/-1;">🔴 LIVE SEARCH ACTIVE: Fetching NASA Archives...</p>';

    const matchedInternal = hardwareData.filter(h => h.name.toLowerCase().includes(query.toLowerCase()) || h.purpose.toLowerCase().includes(query.toLowerCase()));
    let htmlContent = '';

    if (matchedInternal.length > 0) {
        htmlContent += matchedInternal.map(item => `
            <div class="card-inline" style="border-color:var(--purple);" onclick="openModal('${item.id}')">
                <div class="card-content-side">
                    <div class="card-sub">PROJECT MATCH | ${item.target.toUpperCase()}</div>
                    <div class="card-title">${item.name}</div>
                    <div class="card-desc">${item.purpose}</div>
                    <button class="btn btn-outline" style="padding:8px 16px; font-size:11px; margin-top:6px;">🔍 Inspect Relic Details</button>
                </div>
            </div>
        `).join('');
    }

    try {
        const res = await fetch(`https://images-api.nasa.gov/search?q=${encodeURIComponent(query)}&media_type=image`);
        const data = await res.json();
        const items = data.collection.items.slice(0, 4);

        if (items && items.length > 0) {
            htmlContent += items.map(item => {
                const title = item.data[0]?.title || 'NASA Space Hardware';
                const desc = item.data[0]?.description ? item.data[0].description.substring(0, 75) + '...' : 'NASA open repository item.';
                const date = item.data[0]?.date_created ? item.data[0].date_created.substring(0, 10) : 'Archive';
                const imgUrl = item.links && item.links[0] ? item.links[0].href : '';

                return `
                    <div class="card-inline" onclick="openModalById(${JSON.stringify(imgUrl)}, ${JSON.stringify(title)})">
                        ${imgUrl ? `<img style="width:100%; height:160px; object-fit:cover; border-radius:8px; margin-bottom:10px; border:1px solid var(--panel-border);" src="${imgUrl}" alt="${title}">` : ''}
                        <div class="card-content-side">
                            <div class="card-sub">📅 ${date} | LIVE NASA API</div>
                            <div class="card-title" style="font-size:15px;">${title}</div>
                            <div class="card-desc">${desc}</div>
                        </div>
                    </div>
                `;
            }).join('');
        }
        box.innerHTML = htmlContent || '<p style="color:var(--orange); text-align:center; grid-column:1/-1;">No live results found.</p>';
    } catch(e) {
        box.innerHTML = htmlContent || '<p style="color:var(--red); text-align:center; grid-column:1/-1;">Unable to connect to live NASA API.</p>';
    }
}

function openModalById(imgUrl, title) {
    document.getElementById('mTitle').innerText = title;
    document.getElementById('mSub').innerText = "NASA ARCHIVE REPOSITORY ITEM";
    document.getElementById('mMission').innerText = "Deep Space Historical Archival Record";
    document.getElementById('mLoc').innerText = "Extraterrestrial / Deep Space Coordinates";
    document.getElementById('mPurpose').innerText = "Preserve historical visual telemetry and documentation of human space exploration hardware.";
    document.getElementById('mHow').innerText = "Captured via optical and digital space telescopes or surface lander camera payloads.";
    document.getElementById('mHappened').innerText = "Archived permanently in official global space databases.";
    document.getElementById('mWhy').innerText = "Permanent record of space engineering milestones.";
    document.getElementById('mScience').innerText = "Inspires future generations of STEM researchers and aerospace engineers.";
    document.getElementById('hwModal').style.display = 'flex';
}


function explorerImage(h){
 const fixed={
  'ingenuity':'https://d2pn8kiwq2w21t.cloudfront.net/original_images/jpegPIA23882.jpg',
  'skycrane':'https://www.nasa.gov/wp-content/uploads/2024/08/2-ksc-2011-7087large.jpg?w=1024',
  'apollo15-lrv':'https://images-assets.nasa.gov/image/as15-88-11901/as15-88-11901~orig.jpg',
  'apollo11-lrrr':'https://images-assets.nasa.gov/image/AS11-40-5950/AS11-40-5950~orig.jpg'
 };
 return h.fixedPhoto||fixed[h.id]||'';
}
function showExplorerStep(step){
 const box=document.getElementById('explorerFlowContent'); if(!box) return;
 document.querySelectorAll('#explorerTabs .progressive-tab').forEach((b,i)=>b.classList.toggle('active',i===step-1));
 const moon=hardwareData.filter(h=>h.target==='moon'); const mars=hardwareData.filter(h=>h.target==='mars');
 if(step===1){box.innerHTML=`<div class="explorer-step-grid">
  <div class="explorer-choice-card" onclick="showExplorerStep(2);setExplorerFilter('moon')"><span class="big-icon">🌕</span><h3>MOON</h3><p>Apollo rovers, modules & science hardware</p></div>
  <div class="explorer-choice-card" onclick="showExplorerStep(2);setExplorerFilter('mars')"><span class="big-icon">🔴</span><h3>MARS</h3><p>Rovers, helicopters & landing systems</p></div>
  <div class="explorer-choice-card" onclick="showExplorerStep(2);setExplorerFilter('all')"><span class="big-icon">🛰️</span><h3>ALL HARDWARE</h3><p>Explore the complete collection</p></div></div>`; return;}
 const selected=window.__explorerFilter||'all'; const data=selected==='all'?hardwareData:selected==='moon'?moon:mars;
 if(step===2){box.innerHTML=`<div class="explorer-step-grid">${data.slice(0,6).map(h=>{const src=explorerImage(h); return `<div class="explorer-mini-card" data-hwid="${h.id}"><img src="${src}" alt="${h.name}" data-query="${(h.photoQueries||[h.name])[0].replace(/"/g,'&quot;')}" onerror="this.dataset.failed='1'"><div><h3>${h.name}</h3><p>${h.summary||h.purpose||'Space exploration hardware.'}</p><span class="hw-status-badge ${getHardwareStatus(h).cls}">${getHardwareStatus(h).status}</span></div></div>`;}).join('')}</div><div class="explorer-step-actions"><button class="btn btn-primary" onclick="showExplorerStep(3)">Next: How It Works →</button></div>`; loadExplorerImages(); return;}
 if(step===3){const h=(selected==='all'?hardwareData:data)[0]; const src=explorerImage(h); box.innerHTML=`<div class="explorer-mini-card"><img src="${src}" alt="${h.name}" data-query="${(h.photoQueries||[h.name])[0].replace(/"/g,'&quot;')}" onerror="this.dataset.failed='1'"><div><h3>${h.name}</h3><p><strong>How:</strong> ${h.how||h.purpose||'Designed to support planetary exploration.'}</p><p><strong>Why:</strong> ${h.why||'Built for a specific mission environment.'}</p></div></div><div class="explorer-step-actions"><button class="btn btn-primary" onclick="showExplorerStep(4)">Next: See Video →</button></div>`; loadExplorerImages(); return;}
 const h=(selected==='all'?hardwareData:data)[0]; const src=explorerImage(h); box.innerHTML=`<div class="explorer-mini-card"><img src="${src}" alt="${h.name}" data-query="${(h.photoQueries||[h.name])[0].replace(/"/g,'&quot;')}" onerror="this.dataset.failed='1'"><div><h3>${h.name}</h3><p>See the real hardware in action and understand its mission.</p><button class="btn btn-primary" onclick="openHardwareVideo('${h.id}')">▶ See Video</button></div></div>`; loadExplorerImages();
}
async function loadExplorerImages(){
 const imgs=document.querySelectorAll('#explorerFlowContent img[data-query]');
 for(const img of imgs){ if(img.src && !img.dataset.failed) continue; try{ const q=img.dataset.query; const r=await fetch(`https://images-api.nasa.gov/search?q=${encodeURIComponent(q)}&media_type=image&page_size=8`); const d=await r.json(); const x=d?.collection?.items?.find(v=>v.links?.some(l=>l.render==='image'||l.href)); const l=x?.links?.find(v=>v.render==='image')||x?.links?.[0]; if(l?.href){img.src=l.href; img.dataset.failed='';}}catch(e){} }
}

function setExplorerFilter(type){window.__explorerFilter=type;showExplorerStep(2);}


async function initOrbitHardwarePhotos(){
 const pairs=[['orbitMoonHw',hardwareData.find(h=>h.id==='apollo15-lrv')],['orbitMarsHw',hardwareData.find(h=>h.id==='ingenuity')]];
 for(const [id,item] of pairs){ const img=document.getElementById(id); if(!img||!item) continue; try{ const q=(item.photoQueries||[item.name])[0]; const r=await fetch(`https://images-api.nasa.gov/search?q=${encodeURIComponent(q)}&media_type=image&page_size=5`); const d=await r.json(); const x=d?.collection?.items?.find(v=>v.links?.some(l=>l.render==='image'||l.href)); const l=x?.links?.find(v=>v.render==='image')||x?.links?.[0]; if(l?.href) img.src=l.href; }catch(e){} }
}

function attachImageRecovery(){
    const fallbackSvg='data:image/svg+xml;charset=UTF-8,'+encodeURIComponent('<svg xmlns="http://www.w3.org/2000/svg" width="800" height="500"><rect width="100%" height="100%" fill="#06111f"/><text x="50%" y="46%" fill="#38bdf8" font-family="Arial" font-size="28" text-anchor="middle">NASA SPACE HARDWARE</text><text x="50%" y="57%" fill="#94a3b8" font-family="Arial" font-size="18" text-anchor="middle">Image unavailable — try Live NASA Archive</text></svg>');
    const bind=()=>document.querySelectorAll('img').forEach(img=>{
        if(img.dataset.recoveryBound) return;
        img.dataset.recoveryBound='1';
        img.addEventListener('error',async()=>{
            if(img.dataset.recoveryTried){img.src=fallbackSvg;return;}
            img.dataset.recoveryTried='1';
            const q=img.alt||img.dataset.query||'NASA space hardware';
            try{
                const r=await fetch(`https://images-api.nasa.gov/search?q=${encodeURIComponent(q)}&media_type=image&page_size=10`);
                const d=await r.json();
                const item=d?.collection?.items?.find(v=>v.links?.some(l=>l.render==='image'||l.href));
                const link=item?.links?.find(v=>v.render==='image')||item?.links?.[0];
                if(link?.href) img.src=link.href; else img.src=fallbackSvg;
            }catch(e){img.src=fallbackSvg;}
        },{once:false});
    });
    bind();
    if(!window.__imageRecoveryObserver){
        window.__imageRecoveryObserver=new MutationObserver(()=>bind());
        window.__imageRecoveryObserver.observe(document.body,{childList:true,subtree:true});
    }
}

window.onload = function() {
    showPlanetStep('moon', 1);
    showPlanetStep('mars', 1);
    initGrids();
    renderHardwareGallery();
    showExplorerStep(1);
    initSolarSystem();
    const orbitDetails = document.querySelector('.home-3d-drawer details');
    if (orbitDetails) orbitDetails.addEventListener('toggle', () => setTimeout(() => window.dispatchEvent(new Event('resize')), 50));
    initMiniSpinners();
    renderTimeline();
    renderQuiz();
    searchNASA();
    attachImageRecovery();
};
</script>
</body>
</html>
