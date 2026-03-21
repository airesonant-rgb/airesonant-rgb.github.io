
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Resonant — AI Voice Agent for Restaurants</title>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700;800;900&family=Lato:wght@300;400;700&display=swap" rel="stylesheet"/>
<style>
  :root {
    --coral:   #FF4D6D;
    --orange:  #FF8C42;
    --pink:    #E91E8C;
    --purple:  #7B2FBE;
    --deep:    #2D1B69;
    --light:   #F5F3FF;
    --white:   #FFFFFF;
    --grad: linear-gradient(135deg, var(--orange) 0%, var(--coral) 35%, var(--pink) 65%, var(--purple) 100%);
    --grad-soft: linear-gradient(135deg, #fff0eb 0%, #fce4f5 50%, #ede0ff 100%);
  }
  *, *::before, *::after { margin:0; padding:0; box-sizing:border-box; }
  html { scroll-behavior: smooth; }
  body { font-family: 'Lato', sans-serif; background: var(--white); color: var(--deep); overflow-x: hidden; }

  /* ── NAV ── */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 1rem 4rem;
    background: rgba(255,255,255,0.92);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid rgba(123,47,190,0.08);
    transition: box-shadow .3s;
  }
  nav.scrolled { box-shadow: 0 4px 24px rgba(123,47,190,0.12); }
  .nav-logo { display:flex; align-items:center; gap:.6rem; }
  .nav-logo svg { width:38px; height:38px; }
  .nav-logo span { font-family:'Poppins',sans-serif; font-weight:800; font-size:1.35rem;
    background: var(--grad); -webkit-background-clip:text; -webkit-text-fill-color:transparent; }
  .nav-links { display:flex; gap:2.2rem; list-style:none; }
  .nav-links a { text-decoration:none; color:var(--deep); font-weight:600; font-size:.92rem;
    letter-spacing:.02em; transition:color .2s; }
  .nav-links a:hover { color: var(--pink); }
  .nav-cta { background: var(--grad); color:#fff; border:none; padding:.65rem 1.6rem;
    border-radius:50px; font-family:'Poppins',sans-serif; font-weight:700; font-size:.9rem;
    cursor:pointer; transition:opacity .2s, transform .2s; box-shadow: 0 4px 18px rgba(233,30,140,.3); }
  .nav-cta:hover { opacity:.9; transform:translateY(-1px); }

  /* ── HERO ── */
  #hero {
    min-height: 100vh; display:flex; flex-direction:column; align-items:center; justify-content:center;
    text-align:center; padding: 7rem 2rem 4rem;
    background: var(--grad-soft);
    position:relative; overflow:hidden;
  }
  .hero-blob {
    position:absolute; border-radius:50%; filter:blur(80px); opacity:.35; pointer-events:none;
  }
  .blob1 { width:520px; height:520px; background:var(--orange); top:-120px; left:-100px; animation: drift 9s ease-in-out infinite alternate; }
  .blob2 { width:420px; height:420px; background:var(--pink); bottom:-80px; right:-80px; animation: drift 12s ease-in-out infinite alternate-reverse; }
  .blob3 { width:300px; height:300px; background:var(--purple); top:40%; left:55%; animation: drift 7s ease-in-out infinite alternate; }
  @keyframes drift { from{transform:translate(0,0) scale(1);} to{transform:translate(30px,20px) scale(1.06);} }

  .hero-badge {
    display:inline-flex; align-items:center; gap:.5rem;
    background:rgba(233,30,140,.1); border:1px solid rgba(233,30,140,.25);
    color: var(--pink); padding:.4rem 1rem; border-radius:50px;
    font-size:.8rem; font-weight:700; letter-spacing:.08em; text-transform:uppercase;
    margin-bottom:1.6rem; position:relative; z-index:2;
  }
  .hero-badge span { width:8px; height:8px; border-radius:50%; background:var(--pink);
    display:inline-block; animation: pulse 1.6s ease-in-out infinite; }
  @keyframes pulse { 0%,100%{opacity:1;transform:scale(1);} 50%{opacity:.5;transform:scale(1.4);} }

  h1 {
    font-family:'Poppins',sans-serif; font-weight:900; font-size:clamp(2.6rem,6vw,5.2rem);
    line-height:1.08; max-width:900px; position:relative; z-index:2;
    color: var(--deep);
  }
  h1 .grad-text { background:var(--grad); -webkit-background-clip:text; -webkit-text-fill-color:transparent; }
  .hero-sub { margin-top:1.4rem; font-size:clamp(1rem,2vw,1.22rem); color:#5a4a7a; max-width:620px;
    line-height:1.7; position:relative; z-index:2; }

  .hero-actions { display:flex; gap:1rem; margin-top:2.4rem; flex-wrap:wrap; justify-content:center; position:relative; z-index:2; }
  .btn-primary { background:var(--grad); color:#fff; border:none; padding:.9rem 2.2rem;
    border-radius:50px; font-family:'Poppins',sans-serif; font-weight:700; font-size:1rem;
    cursor:pointer; transition:all .25s; box-shadow:0 6px 28px rgba(233,30,140,.35); }
  .btn-primary:hover { transform:translateY(-3px); box-shadow:0 10px 36px rgba(233,30,140,.45); }
  .btn-outline { background:transparent; color:var(--purple); border:2px solid var(--purple);
    padding:.88rem 2.2rem; border-radius:50px; font-family:'Poppins',sans-serif; font-weight:700;
    font-size:1rem; cursor:pointer; transition:all .25s; }
  .btn-outline:hover { background:var(--purple); color:#fff; transform:translateY(-3px); }

  /* Waveform animation */
  .waveform { display:flex; align-items:center; gap:4px; margin:2.4rem auto 0;
    position:relative; z-index:2; }
  .waveform .bar {
    width:5px; border-radius:10px;
    background: var(--grad);
    animation: wave 1.2s ease-in-out infinite;
  }
  .waveform .bar:nth-child(1){height:18px;animation-delay:0s;}
  .waveform .bar:nth-child(2){height:32px;animation-delay:.1s;}
  .waveform .bar:nth-child(3){height:46px;animation-delay:.2s;}
  .waveform .bar:nth-child(4){height:58px;animation-delay:.3s;}
  .waveform .bar:nth-child(5){height:72px;animation-delay:.1s;}
  .waveform .bar:nth-child(6){height:62px;animation-delay:.25s;}
  .waveform .bar:nth-child(7){height:50px;animation-delay:.15s;}
  .waveform .bar:nth-child(8){height:38px;animation-delay:.35s;}
  .waveform .bar:nth-child(9){height:28px;animation-delay:.05s;}
  .waveform .bar:nth-child(10){height:44px;animation-delay:.2s;}
  .waveform .bar:nth-child(11){height:60px;animation-delay:.3s;}
  .waveform .bar:nth-child(12){height:74px;animation-delay:.1s;}
  .waveform .bar:nth-child(13){height:62px;animation-delay:.2s;}
  .waveform .bar:nth-child(14){height:48px;animation-delay:.0s;}
  .waveform .bar:nth-child(15){height:30px;animation-delay:.15s;}
  @keyframes wave {
    0%,100%{transform:scaleY(1);}
    50%{transform:scaleY(.4);}
  }

  /* stats strip */
  .stats-strip {
    display:flex; justify-content:center; gap:4rem; padding:2.4rem;
    background: rgba(255,255,255,0.7); backdrop-filter:blur(8px);
    border-top:1px solid rgba(123,47,190,.1); border-bottom:1px solid rgba(123,47,190,.1);
    flex-wrap:wrap;
  }
  .stat { text-align:center; }
  .stat-num { font-family:'Poppins',sans-serif; font-weight:900; font-size:2rem;
    background:var(--grad); -webkit-background-clip:text; -webkit-text-fill-color:transparent; }
  .stat-label { font-size:.82rem; color:#7a6a9a; font-weight:600; text-transform:uppercase; letter-spacing:.06em; margin-top:.2rem; }

  /* ── SECTIONS ── */
  section { padding: 6rem 2rem; }
  .section-inner { max-width:1140px; margin:0 auto; }
  .section-label { font-size:.78rem; font-weight:800; text-transform:uppercase; letter-spacing:.12em;
    color:var(--pink); margin-bottom:.8rem; }
  h2 { font-family:'Poppins',sans-serif; font-weight:800; font-size:clamp(1.8rem,3.5vw,2.9rem);
    line-height:1.15; color:var(--deep); }
  h2 .grad-text { background:var(--grad); -webkit-background-clip:text; -webkit-text-fill-color:transparent; }
  .section-sub { margin-top:1rem; color:#5a4a7a; font-size:1.05rem; line-height:1.7; max-width:580px; }

  /* ── FEATURES GRID ── */
  #features { background: #fafafe; }
  .features-grid {
    display:grid; grid-template-columns:repeat(auto-fit, minmax(290px,1fr)); gap:1.6rem; margin-top:3.5rem;
  }
  .feat-card {
    background:#fff; border-radius:20px; padding:2rem 1.8rem;
    border:1.5px solid rgba(123,47,190,.1);
    transition: transform .3s, box-shadow .3s, border-color .3s;
    position:relative; overflow:hidden;
  }
  .feat-card::before {
    content:''; position:absolute; top:0; left:0; right:0; height:3px;
    background: var(--grad); transform:scaleX(0); transform-origin:left;
    transition:transform .35s;
  }
  .feat-card:hover { transform:translateY(-5px); box-shadow:0 16px 48px rgba(123,47,190,.14); border-color:rgba(123,47,190,.2); }
  .feat-card:hover::before { transform:scaleX(1); }
  .feat-icon { width:52px; height:52px; border-radius:14px; background:var(--grad-soft);
    display:flex; align-items:center; justify-content:center; margin-bottom:1.2rem; font-size:1.6rem; }
  .feat-card h3 { font-family:'Poppins',sans-serif; font-weight:700; font-size:1.05rem; margin-bottom:.5rem; color:var(--deep); }
  .feat-card p { font-size:.9rem; color:#7a6a9a; line-height:1.65; }

  /* ── HOW IT WORKS ── */
  #how { background: var(--white); }
  .steps { display:grid; grid-template-columns:repeat(auto-fit, minmax(220px,1fr)); gap:2rem; margin-top:3.5rem; counter-reset:step; }
  .step { position:relative; padding:2rem; background:var(--grad-soft); border-radius:20px; }
  .step-num {
    font-family:'Poppins',sans-serif; font-weight:900; font-size:3.5rem; line-height:1;
    background:var(--grad); -webkit-background-clip:text; -webkit-text-fill-color:transparent;
    margin-bottom:.6rem;
  }
  .step h3 { font-family:'Poppins',sans-serif; font-weight:700; font-size:1.05rem; margin-bottom:.5rem; color:var(--deep); }
  .step p { font-size:.88rem; color:#6a5a8a; line-height:1.6; }
  .step-connector { display:none; }

  /* ── DEMO / CTA BLOCK ── */
  #demo {
    background: var(--deep);
    position:relative; overflow:hidden;
  }
  #demo::before {
    content:''; position:absolute; inset:0;
    background: radial-gradient(ellipse at 20% 50%, rgba(233,30,140,.25) 0%, transparent 60%),
                radial-gradient(ellipse at 80% 50%, rgba(123,47,190,.3) 0%, transparent 60%);
  }
  .demo-inner { position:relative; z-index:2; display:grid; grid-template-columns:1fr 1fr; gap:4rem; align-items:center; }
  .demo-inner h2, .demo-inner .section-label { color:#fff; }
  .demo-inner .section-sub { color:rgba(255,255,255,.7); }
  .demo-phone {
    background:rgba(255,255,255,.06); border:1px solid rgba(255,255,255,.12);
    border-radius:24px; padding:2rem; backdrop-filter:blur(8px);
  }
  .demo-msg { display:flex; gap:.8rem; align-items:flex-start; margin-bottom:1.2rem; }
  .demo-avatar { width:36px; height:36px; border-radius:50%; flex-shrink:0;
    display:flex; align-items:center; justify-content:center; font-size:1rem; }
  .avatar-ai { background:var(--grad); }
  .avatar-user { background:rgba(255,255,255,.2); }
  .demo-bubble {
    background:rgba(255,255,255,.1); border-radius:12px 12px 12px 0;
    padding:.7rem 1rem; color:rgba(255,255,255,.9); font-size:.88rem; line-height:1.5;
  }
  .demo-bubble.user-bubble { background:rgba(233,30,140,.25); border-radius:12px 12px 0 12px; }
  .typing { display:flex; gap:4px; padding:.7rem 1rem; }
  .typing span { width:7px; height:7px; border-radius:50%; background:rgba(255,255,255,.5);
    animation: typing 1.2s ease-in-out infinite; }
  .typing span:nth-child(2){animation-delay:.2s;} .typing span:nth-child(3){animation-delay:.4s;}
  @keyframes typing{0%,60%,100%{transform:translateY(0);}30%{transform:translateY(-6px);}}

  /* ── PRICING ── */
  #pricing { background:#fafafe; }
  .pricing-grid { display:grid; grid-template-columns:repeat(auto-fit, minmax(280px,1fr)); gap:1.8rem; margin-top:3.5rem; }
  .price-card {
    background:#fff; border-radius:22px; padding:2.4rem 2rem;
    border:1.5px solid rgba(123,47,190,.12);
    transition:transform .3s, box-shadow .3s;
  }
  .price-card.featured {
    background:var(--grad); color:#fff; border-color:transparent;
    box-shadow:0 20px 60px rgba(233,30,140,.35); transform:translateY(-8px);
  }
  .price-card:not(.featured):hover { transform:translateY(-4px); box-shadow:0 12px 40px rgba(123,47,190,.12); }
  .price-tier { font-size:.78rem; font-weight:800; letter-spacing:.1em; text-transform:uppercase;
    color:var(--pink); margin-bottom:.8rem; }
  .price-card.featured .price-tier { color:rgba(255,255,255,.8); }
  .price-amount { font-family:'Poppins',sans-serif; font-weight:900; font-size:3rem; line-height:1; }
  .price-amount sup { font-size:1.2rem; vertical-align:super; }
  .price-amount sub { font-size:.9rem; font-weight:400; }
  .price-desc { margin:.6rem 0 1.6rem; font-size:.88rem; color:#7a6a9a; line-height:1.6; }
  .price-card.featured .price-desc { color:rgba(255,255,255,.75); }
  .price-features { list-style:none; display:flex; flex-direction:column; gap:.65rem; margin-bottom:2rem; }
  .price-features li { font-size:.88rem; display:flex; align-items:center; gap:.6rem; color:var(--deep); }
  .price-card.featured .price-features li { color:#fff; }
  .price-features li::before { content:'✓'; font-weight:900; color:var(--pink); flex-shrink:0; }
  .price-card.featured .price-features li::before { color:rgba(255,255,255,.9); }
  .btn-plan { width:100%; padding:.85rem; border-radius:50px; font-family:'Poppins',sans-serif;
    font-weight:700; font-size:.92rem; cursor:pointer; transition:all .25s; border:none; }
  .btn-plan-outline { background:transparent; border:2px solid var(--purple); color:var(--purple); }
  .btn-plan-outline:hover { background:var(--purple); color:#fff; }
  .btn-plan-white { background:#fff; color:var(--pink); }
  .btn-plan-white:hover { transform:translateY(-2px); box-shadow:0 6px 20px rgba(0,0,0,.15); }

  /* ── LANGUAGES ── */
  #languages { background:#fff; }
  .lang-grid { display:flex; flex-wrap:wrap; gap:1rem; margin-top:2.5rem; }
  .lang-chip {
    background:var(--grad-soft); border:1.5px solid rgba(123,47,190,.15);
    border-radius:50px; padding:.55rem 1.4rem;
    font-family:'Poppins',sans-serif; font-weight:600; font-size:.92rem; color:var(--deep);
    display:flex; align-items:center; gap:.5rem;
    transition:all .25s;
  }
  .lang-chip:hover { background:var(--grad); color:#fff; border-color:transparent; transform:translateY(-2px); }

  /* ── ANALYTICS PREVIEW ── */
  #analytics { background:#fafafe; }
  .analytics-grid { display:grid; grid-template-columns:1fr 1fr; gap:2rem; margin-top:3rem; }
  .analytics-card { background:#fff; border-radius:18px; padding:1.6rem;
    border:1.5px solid rgba(123,47,190,.1); }
  .analytics-card h4 { font-family:'Poppins',sans-serif; font-weight:700; font-size:.92rem; margin-bottom:1rem; color:var(--deep); }
  .chart-bar-row { display:flex; align-items:center; gap:.8rem; margin-bottom:.6rem; }
  .chart-bar-label { font-size:.78rem; color:#7a6a9a; width:70px; flex-shrink:0; }
  .chart-bar-track { flex:1; background:#f0edf8; border-radius:10px; height:10px; overflow:hidden; }
  .chart-bar-fill { height:100%; border-radius:10px; background:var(--grad); transition:width 1s ease; }
  .kpi-row { display:grid; grid-template-columns:1fr 1fr; gap:1rem; }
  .kpi { background:var(--grad-soft); border-radius:14px; padding:1rem; text-align:center; }
  .kpi-val { font-family:'Poppins',sans-serif; font-weight:800; font-size:1.6rem;
    background:var(--grad); -webkit-background-clip:text; -webkit-text-fill-color:transparent; }
  .kpi-lbl { font-size:.72rem; color:#7a6a9a; font-weight:600; margin-top:.2rem; text-transform:uppercase; letter-spacing:.05em; }

  /* ── TESTIMONIALS ── */
  #testimonials { background:var(--white); }
  .testi-grid { display:grid; grid-template-columns:repeat(auto-fit,minmax(280px,1fr)); gap:1.6rem; margin-top:3rem; }
  .testi-card { background:var(--grad-soft); border-radius:20px; padding:2rem; border:1.5px solid rgba(123,47,190,.1); }
  .testi-stars { color:var(--orange); font-size:1rem; margin-bottom:.8rem; letter-spacing:.05em; }
  .testi-quote { font-size:.95rem; line-height:1.7; color:var(--deep); margin-bottom:1.2rem; font-style:italic; }
  .testi-author { font-family:'Poppins',sans-serif; font-weight:700; font-size:.88rem; color:var(--purple); }
  .testi-role { font-size:.78rem; color:#7a6a9a; }

  /* ── GDPR ── */
  #gdpr { background:var(--deep); position:relative; overflow:hidden; }
  #gdpr::before { content:''; position:absolute; inset:0;
    background:radial-gradient(circle at 70% 50%, rgba(123,47,190,.3) 0%, transparent 60%); }
  .gdpr-inner { position:relative; z-index:2; display:flex; gap:4rem; align-items:center; flex-wrap:wrap; }
  .gdpr-text h2, .gdpr-text .section-label { color:#fff; }
  .gdpr-text .section-sub { color:rgba(255,255,255,.7); }
  .gdpr-badges { display:grid; grid-template-columns:1fr 1fr; gap:1rem; flex-shrink:0; }
  .gdpr-badge {
    background:rgba(255,255,255,.07); border:1px solid rgba(255,255,255,.15);
    border-radius:16px; padding:1.2rem 1.4rem;
    display:flex; align-items:center; gap:.8rem; color:#fff;
    font-size:.88rem; font-weight:600;
  }
  .gdpr-badge-icon { font-size:1.6rem; }

  /* ── FINAL CTA ── */
  #final-cta {
    background:var(--grad); text-align:center; padding:7rem 2rem;
    position:relative; overflow:hidden;
  }
  #final-cta h2 { color:#fff; font-family:'Poppins',sans-serif; font-weight:900;
    font-size:clamp(2rem,4.5vw,3.6rem); margin-bottom:1.2rem; }
  #final-cta p { color:rgba(255,255,255,.85); font-size:1.1rem; margin-bottom:2.4rem; }
  .btn-white { background:#fff; color:var(--pink); border:none; padding:1rem 2.5rem;
    border-radius:50px; font-family:'Poppins',sans-serif; font-weight:700; font-size:1rem;
    cursor:pointer; box-shadow:0 8px 30px rgba(0,0,0,.2); transition:all .25s; }
  .btn-white:hover { transform:translateY(-3px); box-shadow:0 14px 40px rgba(0,0,0,.25); }

  /* ── FOOTER ── */
  footer {
    background:var(--deep); border-top:1px solid rgba(255,255,255,.08);
    padding:3rem 4rem; display:flex; justify-content:space-between; align-items:center;
    flex-wrap:wrap; gap:1.5rem;
  }
  footer .logo-text { font-family:'Poppins',sans-serif; font-weight:800; font-size:1.2rem;
    background:var(--grad); -webkit-background-clip:text; -webkit-text-fill-color:transparent; }
  footer .footer-tagline { color:rgba(255,255,255,.5); font-size:.82rem; margin-top:.2rem; }
  footer .footer-links { display:flex; gap:1.8rem; }
  footer .footer-links a { color:rgba(255,255,255,.55); text-decoration:none; font-size:.85rem; transition:color .2s; }
  footer .footer-links a:hover { color:#fff; }
  footer .footer-copy { color:rgba(255,255,255,.35); font-size:.78rem; }

  /* ── RESPONSIVE ── */
  @media(max-width:768px){
    nav { padding:1rem 1.5rem; }
    .nav-links { display:none; }
    .demo-inner { grid-template-columns:1fr; }
    .analytics-grid { grid-template-columns:1fr; }
    .gdpr-inner { flex-direction:column; }
    footer { flex-direction:column; text-align:center; padding:2rem; }
    .footer-links { flex-direction:column; gap:.8rem; align-items:center; }
  }

  /* scroll reveal */
  .reveal { opacity:0; transform:translateY(28px); transition:opacity .7s ease, transform .7s ease; }
  .reveal.visible { opacity:1; transform:translateY(0); }
</style>
</head>
<body>

<!-- NAV -->
<nav id="navbar">
  <div class="nav-logo">
    <svg viewBox="0 0 60 60" fill="none" xmlns="http://www.w3.org/2000/svg">
      <defs><linearGradient id="lg" x1="0" y1="0" x2="60" y2="60" gradientUnits="userSpaceOnUse">
        <stop offset="0%" stop-color="#FF8C42"/>
        <stop offset="50%" stop-color="#E91E8C"/>
        <stop offset="100%" stop-color="#7B2FBE"/>
      </linearGradient></defs>
      <circle cx="30" cy="36" r="14" fill="url(#lg)" opacity=".15"/>
      <rect x="25" y="12" width="10" height="22" rx="5" fill="url(#lg)"/>
      <path d="M18 28c0 6.627 5.373 12 12 12s12-5.373 12-12" stroke="url(#lg)" stroke-width="2.5" stroke-linecap="round" fill="none"/>
      <line x1="30" y1="40" x2="30" y2="47" stroke="url(#lg)" stroke-width="2.5" stroke-linecap="round"/>
      <line x1="22" y1="47" x2="38" y2="47" stroke="url(#lg)" stroke-width="2.5" stroke-linecap="round"/>
      <!-- sound bars -->
      <rect x="6" y="26" width="4" height="10" rx="2" fill="url(#lg)" opacity=".7"/>
      <rect x="12" y="22" width="4" height="18" rx="2" fill="url(#lg)" opacity=".9"/>
      <rect x="44" y="22" width="4" height="18" rx="2" fill="url(#lg)" opacity=".9"/>
      <rect x="50" y="26" width="4" height="10" rx="2" fill="url(#lg)" opacity=".7"/>
    </svg>
    <span>Resonant</span>
  </div>
  <ul class="nav-links">
    <li><a href="#features">Features</a></li>
    <li><a href="#how">How It Works</a></li>
    <li><a href="#pricing">Pricing</a></li>
    <li><a href="#analytics">Analytics</a></li>
    <li><a href="#languages">Languages</a></li>
  </ul>
  <button class="nav-cta" onclick="document.getElementById('final-cta').scrollIntoView({behavior:'smooth'})">Book a Demo</button>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="hero-blob blob1"></div>
  <div class="hero-blob blob2"></div>
  <div class="hero-blob blob3"></div>

  <div class="hero-badge"><span></span> Now live in 5 languages</div>

  <h1>Your Restaurant's <br><span class="grad-text">AI Voice Concierge</span><br>Never Misses a Call</h1>
  <p class="hero-sub">Resonant answers every call, books reservations, takes pre-orders, recommends dishes, and delights your guests — 24/7, automatically.</p>

  <div class="hero-actions">
    <button class="btn-primary" onclick="document.getElementById('demo').scrollIntoView({behavior:'smooth'})">▶ Hear It In Action</button>
    <button class="btn-outline" onclick="document.getElementById('pricing').scrollIntoView({behavior:'smooth'})">View Pricing</button>
  </div>

  <div class="waveform">
    <div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div>
    <div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div>
    <div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div>
    <div class="bar"></div><div class="bar"></div><div class="bar"></div>
  </div>
</section>

<!-- STATS STRIP -->
<div class="stats-strip">
  <div class="stat"><div class="stat-num">0%</div><div class="stat-label">Missed Calls</div></div>
  <div class="stat"><div class="stat-num">24/7</div><div class="stat-label">Always Answering</div></div>
  <div class="stat"><div class="stat-num">5+</div><div class="stat-label">Languages</div></div>
  <div class="stat"><div class="stat-num">+32%</div><div class="stat-label">More Reservations</div></div>
  <div class="stat"><div class="stat-num">€300+</div><div class="stat-label">Avg. Monthly ROI</div></div>
</div>

<!-- FEATURES -->
<section id="features">
  <div class="section-inner">
    <div class="section-label reveal">Core Features</div>
    <h2 class="reveal">Everything Your Restaurant <span class="grad-text">Needs, Automated</span></h2>
    <p class="section-sub reveal">Resonant acts as your digital host, concierge, and sales assistant — handling every inbound call with the warmth of a 5-star restaurant.</p>

    <div class="features-grid">
      <div class="feat-card reveal">
        <div class="feat-icon">📞</div>
        <h3>Inbound Call Handling</h3>
        <p>Connects to your existing restaurant landline. Answers every call instantly — no hold music, no missed opportunities.</p>
      </div>
      <div class="feat-card reveal">
        <div class="feat-icon">📅</div>
        <h3>Smart Reservations</h3>
        <p>Books tables in real-time with calendar integration. Prevents double-bookings automatically. Sends confirmations via SMS or email.</p>
      </div>
      <div class="feat-card reveal">
        <div class="feat-icon">🍽️</div>
        <h3>Menu Intelligence</h3>
        <p>Recommends dishes and drinks based on your actual menu, guest mood, occasion, and dietary preferences.</p>
      </div>
      <div class="feat-card reveal">
        <div class="feat-icon">🌿</div>
        <h3>Allergy & Dietary Filtering</h3>
        <p>Proactively asks about allergies and dietary needs. Filters recommendations to ensure every guest is safe and satisfied.</p>
      </div>
      <div class="feat-card reveal">
        <div class="feat-icon">🎁</div>
        <h3>Pre-orders & Takeaway</h3>
        <p>Takes complete pre-orders and takeaway orders over the phone. Sends order summaries directly to your kitchen or POS system.</p>
      </div>
      <div class="feat-card reveal">
        <div class="feat-icon">🎂</div>
        <h3>Event Reservations</h3>
        <p>Handles birthday dinners, anniversaries, corporate events — collects all details and notifies your team instantly.</p>
      </div>
      <div class="feat-card reveal">
        <div class="feat-icon">💬</div>
        <h3>Multilingual Support</h3>
        <p>Speaks English, German, French, Spanish and more. Automatically detects the caller's language and switches seamlessly.</p>
      </div>
      <div class="feat-card reveal">
        <div class="feat-icon">⭐</div>
        <h3>Feedback Collection</h3>
        <p>Collects post-visit feedback via follow-up calls or SMS. Surfaces actionable insights for your team in the dashboard.</p>
      </div>
      <div class="feat-card reveal">
        <div class="feat-icon">👤</div>
        <h3>Regular Guest Recognition</h3>
        <p>Remembers returning customers, their preferences, past orders, and favourite tables for a truly personalised experience.</p>
      </div>
      <div class="feat-card reveal">
        <div class="feat-icon">🏷️</div>
        <h3>Promotions & Discounts</h3>
        <p>Automatically offers relevant promotions based on day, time, guest history, and your marketing campaigns.</p>
      </div>
      <div class="feat-card reveal">
        <div class="feat-icon">📊</div>
        <h3>Owner Analytics Dashboard</h3>
        <p>Track call volume, reservation rates, popular dishes, peak hours, and revenue impact — all in one dashboard.</p>
      </div>
      <div class="feat-card reveal">
        <div class="feat-icon">🔒</div>
        <h3>GDPR Compliance</h3>
        <p>Customer data stored securely with full consent management, right-to-deletion, and EU-compliant privacy controls.</p>
      </div>
    </div>
  </div>
</section>

<!-- HOW IT WORKS -->
<section id="how">
  <div class="section-inner">
    <div class="section-label reveal">Process</div>
    <h2 class="reveal">Up & Running in <span class="grad-text">Under 2 Hours</span></h2>
    <p class="section-sub reveal">No hardware. No technical team. Just connect your landline and Resonant handles the rest.</p>

    <div class="steps">
      <div class="step reveal">
        <div class="step-num">01</div>
        <h3>Connect Your Landline</h3>
        <p>Forward your existing restaurant number to Resonant. No new hardware needed — works with any phone system.</p>
      </div>
      <div class="step reveal">
        <div class="step-num">02</div>
        <h3>Upload Your Menu</h3>
        <p>Share your menu, opening hours, and booking rules. Resonant learns your restaurant in minutes using AI.</p>
      </div>
      <div class="step reveal">
        <div class="step-num">03</div>
        <h3>Customise Your Agent</h3>
        <p>Choose voice, language, personality, and greeting. Your AI host should feel like part of your team.</p>
      </div>
      <div class="step reveal">
        <div class="step-num">04</div>
        <h3>Go Live</h3>
        <p>Resonant answers every call from day one. Monitor performance live via your owner dashboard.</p>
      </div>
    </div>
  </div>
</section>

<!-- DEMO BLOCK -->
<section id="demo">
  <div class="section-inner demo-inner">
    <div>
      <div class="section-label reveal">Live Demo</div>
      <h2 class="reveal" style="color:#fff;">Hear How Resonant Handles a <span style="background:var(--grad);-webkit-background-clip:text;-webkit-text-fill-color:transparent;">Real Call</span></h2>
      <p class="section-sub reveal" style="color:rgba(255,255,255,.7);">A real conversation between Resonant and a restaurant guest — handling a reservation, allergy check, and meal recommendation in one call.</p>
      <div style="margin-top:2rem;" class="reveal">
        <button class="btn-primary">▶ Play Sample Call</button>
      </div>
    </div>
    <div class="demo-phone reveal">
      <div class="demo-msg">
        <div class="demo-avatar avatar-ai">🤖</div>
        <div class="demo-bubble">Ciao! Thank you for calling Trattoria Milano. I'm Aria, your AI host. How can I help you today?</div>
      </div>
      <div class="demo-msg" style="flex-direction:row-reverse;">
        <div class="demo-avatar avatar-user">👤</div>
        <div class="demo-bubble user-bubble">Hi, I'd like to book a table for 4 this Saturday at 7pm. It's my wife's birthday.</div>
      </div>
      <div class="demo-msg">
        <div class="demo-avatar avatar-ai">🤖</div>
        <div class="demo-bubble">How lovely! I'd be delighted to arrange something special. Before I confirm, does anyone in your party have any allergies or dietary requirements?</div>
      </div>
      <div class="demo-msg" style="flex-direction:row-reverse;">
        <div class="demo-avatar avatar-user">👤</div>
        <div class="demo-bubble user-bubble">Yes, one guest is gluten-free.</div>
      </div>
      <div class="demo-msg">
        <div class="demo-avatar avatar-ai">🤖</div>
        <div class="demo-bubble">Perfect — I've noted that and flagged our gluten-free menu options. Your table for 4 is confirmed for Saturday 7pm. 🎂 Shall I also note a birthday surprise for your chef?</div>
      </div>
      <div class="typing" style="background:rgba(255,255,255,.05);border-radius:12px;display:inline-flex;margin-top:.4rem;">
        <span></span><span></span><span></span>
      </div>
    </div>
  </div>
</section>

<!-- LANGUAGES -->
<section id="languages">
  <div class="section-inner">
    <div class="section-label reveal">Global Ready</div>
    <h2 class="reveal">Speaks Your <span class="grad-text">Guests' Language</span></h2>
    <p class="section-sub reveal">Resonant auto-detects the caller's language and responds naturally — no configuration needed.</p>
    <div class="lang-grid reveal">
      <div class="lang-chip">🇬🇧 English</div>
      <div class="lang-chip">🇩🇪 German</div>
      <div class="lang-chip">🇫🇷 French</div>
      <div class="lang-chip">🇪🇸 Spanish</div>
      <div class="lang-chip">🇮🇹 Italian</div>
      <div class="lang-chip">🇵🇹 Portuguese</div>
      <div class="lang-chip">🇳🇱 Dutch</div>
      <div class="lang-chip">🇵🇱 Polish</div>
      <div class="lang-chip">➕ More coming</div>
    </div>
  </div>
</section>

<!-- ANALYTICS -->
<section id="analytics">
  <div class="section-inner">
    <div class="section-label reveal">Intelligence</div>
    <h2 class="reveal">Your Restaurant's <span class="grad-text">Data Dashboard</span></h2>
    <p class="section-sub reveal">Every call, reservation, and customer interaction is tracked and turned into actionable insights for your restaurant.</p>
    <div class="analytics-grid reveal">
      <div class="analytics-card">
        <h4>📞 Call Performance This Week</h4>
        <div class="chart-bar-row"><div class="chart-bar-label">Monday</div><div class="chart-bar-track"><div class="chart-bar-fill" style="width:62%"></div></div></div>
        <div class="chart-bar-row"><div class="chart-bar-label">Tuesday</div><div class="chart-bar-track"><div class="chart-bar-fill" style="width:45%"></div></div></div>
        <div class="chart-bar-row"><div class="chart-bar-label">Wednesday</div><div class="chart-bar-track"><div class="chart-bar-fill" style="width:78%"></div></div></div>
        <div class="chart-bar-row"><div class="chart-bar-label">Thursday</div><div class="chart-bar-track"><div class="chart-bar-fill" style="width:55%"></div></div></div>
        <div class="chart-bar-row"><div class="chart-bar-label">Friday</div><div class="chart-bar-track"><div class="chart-bar-fill" style="width:95%"></div></div></div>
        <div class="chart-bar-row"><div class="chart-bar-label">Saturday</div><div class="chart-bar-track"><div class="chart-bar-fill" style="width:100%"></div></div></div>
        <div class="chart-bar-row"><div class="chart-bar-label">Sunday</div><div class="chart-bar-track"><div class="chart-bar-fill" style="width:80%"></div></div></div>
      </div>
      <div class="analytics-card">
        <h4>📊 Key Performance Metrics</h4>
        <div class="kpi-row">
          <div class="kpi"><div class="kpi-val">98%</div><div class="kpi-lbl">Calls Answered</div></div>
          <div class="kpi"><div class="kpi-val">+34%</div><div class="kpi-lbl">Reservations Up</div></div>
          <div class="kpi"><div class="kpi-val">4.8★</div><div class="kpi-lbl">Avg. Guest Rating</div></div>
          <div class="kpi"><div class="kpi-val">0</div><div class="kpi-lbl">Missed Calls</div></div>
        </div>
        <div style="margin-top:1rem;padding:1rem;background:var(--grad-soft);border-radius:12px;">
          <div style="font-size:.78rem;font-weight:700;color:var(--purple);margin-bottom:.4rem;">TOP REQUESTED DISH THIS WEEK</div>
          <div style="font-family:'Poppins',sans-serif;font-weight:700;color:var(--deep);">🍝 Truffle Pasta — 47 enquiries</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- PRICING -->
<section id="pricing">
  <div class="section-inner">
    <div class="section-label reveal">Pricing</div>
    <h2 class="reveal">Simple, <span class="grad-text">Restaurant-Friendly</span> Plans</h2>
    <p class="section-sub reveal">Start free. Scale as you grow. No setup fees, no long-term contracts.</p>

    <div class="pricing-grid">
      <div class="price-card reveal">
        <div class="price-tier">Starter</div>
        <div class="price-amount"><sup>€</sup>149<sub>/mo</sub></div>
        <p class="price-desc">Perfect for independent restaurants getting started with AI voice.</p>
        <ul class="price-features">
          <li>Up to 300 calls/month</li>
          <li>Reservations & calendar sync</li>
          <li>2 languages</li>
          <li>Menu recommendations</li>
          <li>Basic analytics</li>
          <li>Email support</li>
        </ul>
        <button class="btn-plan btn-plan-outline">Get Started</button>
      </div>
      <div class="price-card featured reveal">
        <div class="price-tier">Growth</div>
        <div class="price-amount" style="color:#fff;"><sup>€</sup>249<sub>/mo</sub></div>
        <p class="price-desc">Our most popular plan for busy restaurants and bistros.</p>
        <ul class="price-features">
          <li>Unlimited calls</li>
          <li>Reservations + pre-orders</li>
          <li>5 languages</li>
          <li>Allergy & preference tracking</li>
          <li>Regular guest recognition</li>
          <li>Full analytics dashboard</li>
          <li>Promotions & upselling</li>
          <li>Priority support</li>
        </ul>
        <button class="btn-plan btn-plan-white">Start Free Trial</button>
      </div>
      <div class="price-card reveal">
        <div class="price-tier">Enterprise</div>
        <div class="price-amount">Custom</div>
        <p class="price-desc">For restaurant groups, chains, and hospitality brands.</p>
        <ul class="price-features">
          <li>Multi-location support</li>
          <li>White-label voice persona</li>
          <li>POS & CRM integration</li>
          <li>Custom AI training</li>
          <li>SLA & dedicated manager</li>
          <li>Outbound reactivation calls</li>
        </ul>
        <button class="btn-plan btn-plan-outline">Contact Sales</button>
      </div>
    </div>
  </div>
</section>

<!-- TESTIMONIALS -->
<section id="testimonials">
  <div class="section-inner">
    <div class="section-label reveal">Social Proof</div>
    <h2 class="reveal">Restaurants <span class="grad-text">Love Resonant</span></h2>
    <div class="testi-grid">
      <div class="testi-card reveal">
        <div class="testi-stars">★★★★★</div>
        <p class="testi-quote">"We used to miss 20–30 calls a week during service. Since Resonant, every call is handled perfectly. Our bookings are up 40%."</p>
        <div class="testi-author">Marco Bianchi</div>
        <div class="testi-role">Owner, Trattoria Milano · Berlin</div>
      </div>
      <div class="testi-card reveal">
        <div class="testi-stars">★★★★★</div>
        <p class="testi-quote">"The AI speaks perfect French to our guests. It even remembered one regular customer's nut allergy from a previous visit. Incredible."</p>
        <div class="testi-author">Sophie Laurent</div>
        <div class="testi-role">Manager, Café Lumière · Paris</div>
      </div>
      <div class="testi-card reveal">
        <div class="testi-stars">★★★★★</div>
        <p class="testi-quote">"Setup was done in 90 minutes. The dashboard gives me data I never had before — busiest times, most requested dishes, guest feedback scores."</p>
        <div class="testi-author">James O'Brien</div>
        <div class="testi-role">Director, The Borough Kitchen · London</div>
      </div>
    </div>
  </div>
</section>

<!-- GDPR -->
<section id="gdpr">
  <div class="section-inner gdpr-inner">
    <div class="gdpr-text">
      <div class="section-label reveal">Privacy & Security</div>
      <h2 class="reveal" style="color:#fff;">Built for <span style="background:var(--grad);-webkit-background-clip:text;-webkit-text-fill-color:transparent;">European Standards</span></h2>
      <p class="section-sub reveal" style="color:rgba(255,255,255,.7);">Every customer interaction is handled with full GDPR compliance, secure EU-based storage, and transparent consent management. Your guests' trust is our priority.</p>
    </div>
    <div class="gdpr-badges reveal">
      <div class="gdpr-badge"><span class="gdpr-badge-icon">🇪🇺</span>EU Data Storage</div>
      <div class="gdpr-badge"><span class="gdpr-badge-icon">🔒</span>End-to-End Encrypted</div>
      <div class="gdpr-badge"><span class="gdpr-badge-icon">✅</span>GDPR Compliant</div>
      <div class="gdpr-badge"><span class="gdpr-badge-icon">🗑️</span>Right to Deletion</div>
    </div>
  </div>
</section>

<!-- FINAL CTA -->
<section id="final-cta">
  <h2>Ready to Never Miss Another Call?</h2>
  <p>Join the restaurants transforming guest experience with Resonant AI.</p>
  <button class="btn-white">Book a Free Demo Today</button>
  <p style="margin-top:1.2rem;color:rgba(255,255,255,.6);font-size:.85rem;">No credit card. No setup fee. Live in 2 hours.</p>
</section>

<!-- FOOTER -->
<footer>
  <div>
    <div class="logo-text">Resonant</div>
    <div class="footer-tagline">AI Voice Agent for Restaurants · Built on Vapi.ai · Powered by GPT-4o</div>
  </div>
  <div class="footer-links">
    <a href="#">Features</a>
    <a href="#">Pricing</a>
    <a href="#">Privacy Policy</a>
    <a href="#">GDPR</a>
    <a href="#">Contact</a>
  </div>
  <div class="footer-copy">© 2025 Resonant. All rights reserved.</div>
</footer>

<script>
  // Nav scroll effect
  const nav = document.getElementById('navbar');
  window.addEventListener('scroll', () => {
    nav.classList.toggle('scrolled', window.scrollY > 40);
  });

  // Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((e, i) => {
      if (e.isIntersecting) {
        setTimeout(() => e.target.classList.add('visible'), i * 80);
        observer.unobserve(e.target);
      }
    });
  }, { threshold: 0.12 });
  reveals.forEach(el => observer.observe(el));
</script>
</body>
</html>
