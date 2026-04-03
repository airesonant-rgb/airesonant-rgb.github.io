<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Resoassit — AI Platform for Restaurants</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Instrument+Serif:ital@0;1&family=DM+Sans:wght@300;400;500;600&family=Syne:wght@700;800&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  :root {
    --cream: #FAF8F5;
    --ink: #1A1208;
    --coral: #FF4D6D;
    --coral-light: #FF8096;
    --amber: #FF9B3E;
    --violet: #6B21A8;
    --violet-soft: #E9D5FF;
    --muted: #8A7E72;
    --surface: #F0EDE8;
    --white: #FFFFFF;
    --gradient-hot: linear-gradient(135deg, #FF4D6D 0%, #FF9B3E 100%);
    --gradient-cool: linear-gradient(135deg, #6B21A8 0%, #FF4D6D 100%);
  }
  html { scroll-behavior: smooth; }
  body { font-family: 'DM Sans', sans-serif; background: var(--cream); color: var(--ink); overflow-x: hidden; line-height: 1.6; }

  /* NAV */
  nav { position: fixed; top: 0; width: 100%; z-index: 100; display: flex; align-items: center; justify-content: space-between; padding: 20px 60px; background: rgba(250,248,245,0.92); backdrop-filter: blur(16px); border-bottom: 1px solid rgba(26,18,8,0.07); }
  .nav-logo { font-family: 'Syne', sans-serif; font-size: 22px; font-weight: 800; letter-spacing: -0.5px; background: var(--gradient-hot); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; }
  .nav-links { display: flex; gap: 36px; list-style: none; }
  .nav-links a { text-decoration: none; color: var(--muted); font-size: 14px; font-weight: 500; transition: color .2s; }
  .nav-links a:hover { color: var(--ink); }
  .nav-cta { background: var(--ink); color: var(--cream); padding: 10px 22px; border-radius: 100px; font-size: 14px; font-weight: 600; text-decoration: none; transition: all .2s; border: none; cursor: pointer; }
  .nav-cta:hover { background: var(--coral); transform: translateY(-1px); }

  /* HERO */
  .hero { min-height: 100vh; display: flex; flex-direction: column; align-items: center; justify-content: center; padding: 140px 60px 80px; position: relative; text-align: center; overflow: hidden; }
  .hero-blob { position: absolute; border-radius: 50%; filter: blur(80px); opacity: 0.35; }
  .blob-1 { width: 600px; height: 600px; top: -100px; left: -150px; background: #FFD6DE; animation: drift1 8s ease-in-out infinite; }
  .blob-2 { width: 500px; height: 500px; top: 50px; right: -100px; background: #FFDBB8; animation: drift2 10s ease-in-out infinite; }
  .blob-3 { width: 400px; height: 400px; bottom: 0; left: 40%; background: #E9D5FF; animation: drift1 12s ease-in-out infinite reverse; }
  @keyframes drift1 { 0%,100%{transform:translate(0,0)} 50%{transform:translate(30px,-30px)} }
  @keyframes drift2 { 0%,100%{transform:translate(0,0)} 50%{transform:translate(-20px,20px)} }
  .hero-content { position: relative; z-index: 1; max-width: 920px; }
  .hero-badge { display: inline-flex; align-items: center; gap: 8px; background: var(--white); border: 1px solid rgba(255,77,109,0.2); padding: 6px 16px; border-radius: 100px; font-size: 13px; font-weight: 500; color: var(--coral); margin-bottom: 32px; box-shadow: 0 2px 16px rgba(255,77,109,0.1); }
  .badge-dot { width: 6px; height: 6px; background: var(--coral); border-radius: 50%; animation: pulse-dot 2s ease-in-out infinite; }
  @keyframes pulse-dot { 0%,100%{opacity:1;transform:scale(1)} 50%{opacity:.5;transform:scale(1.4)} }
  .hero h1 { font-family: 'Instrument Serif', serif; font-size: clamp(52px, 7vw, 92px); line-height: 1.05; font-weight: 400; letter-spacing: -2px; margin-bottom: 8px; }
  .hero h1 em { font-style: italic; color: var(--coral); }
  .hero h1 .outline-text { -webkit-text-stroke: 2px var(--ink); color: transparent; }
  .hero-sub { font-size: 19px; color: var(--muted); font-weight: 400; max-width: 580px; margin: 24px auto 48px; line-height: 1.65; }
  .hero-ctas { display: flex; gap: 14px; justify-content: center; flex-wrap: wrap; }
  .btn-primary { background: var(--gradient-hot); color: white; padding: 16px 36px; border-radius: 100px; font-size: 16px; font-weight: 600; text-decoration: none; transition: all .25s; border: none; cursor: pointer; box-shadow: 0 8px 32px rgba(255,77,109,0.3); display: inline-block; }
  .btn-primary:hover { transform: translateY(-2px); box-shadow: 0 14px 40px rgba(255,77,109,0.4); }
  .btn-secondary { background: var(--white); color: var(--ink); padding: 16px 36px; border-radius: 100px; font-size: 16px; font-weight: 600; text-decoration: none; border: 1.5px solid rgba(26,18,8,0.12); transition: all .25s; cursor: pointer; display: inline-block; }
  .btn-secondary:hover { border-color: var(--coral); color: var(--coral); transform: translateY(-2px); }
  .hero-stats { display: flex; gap: 48px; justify-content: center; margin-top: 64px; flex-wrap: wrap; }
  .stat { text-align: center; }
  .stat-num { font-family: 'Syne', sans-serif; font-size: 36px; font-weight: 800; background: var(--gradient-hot); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; }
  .stat-label { font-size: 13px; color: var(--muted); margin-top: 2px; }

  /* PHONE MOCKUP */
  .hero-phone { margin-top: 64px; position: relative; display: inline-block; }
  .phone-mockup { width: 280px; background: var(--ink); border-radius: 40px; padding: 16px; box-shadow: 0 40px 80px rgba(26,18,8,0.25); }
  .phone-notch { width: 80px; height: 24px; background: var(--ink); border-radius: 0 0 16px 16px; margin: 0 auto 16px; }
  .phone-screen { background: #F8F6F2; border-radius: 28px; padding: 20px; min-height: 360px; }
  .call-avatar { width: 72px; height: 72px; border-radius: 50%; background: var(--gradient-hot); margin: 16px auto 12px; display: flex; align-items: center; justify-content: center; font-size: 28px; }
  .call-name { font-family: 'Syne', sans-serif; font-size: 18px; font-weight: 800; color: var(--ink); text-align: center; }
  .call-status { font-size: 12px; color: var(--muted); margin: 4px 0 16px; text-align: center; }
  .wave-bars { display: flex; gap: 4px; justify-content: center; align-items: flex-end; height: 36px; margin: 12px 0; }
  .wave-bar { width: 4px; border-radius: 4px; background: var(--gradient-hot); }
  .wave-bar:nth-child(1){height:12px;animation:wave 1.2s .0s ease-in-out infinite alternate}
  .wave-bar:nth-child(2){height:24px;animation:wave 1.2s .1s ease-in-out infinite alternate}
  .wave-bar:nth-child(3){height:36px;animation:wave 1.2s .2s ease-in-out infinite alternate}
  .wave-bar:nth-child(4){height:28px;animation:wave 1.2s .3s ease-in-out infinite alternate}
  .wave-bar:nth-child(5){height:36px;animation:wave 1.2s .4s ease-in-out infinite alternate}
  .wave-bar:nth-child(6){height:20px;animation:wave 1.2s .5s ease-in-out infinite alternate}
  .wave-bar:nth-child(7){height:30px;animation:wave 1.2s .6s ease-in-out infinite alternate}
  @keyframes wave { from{transform:scaleY(.4);opacity:.6} to{transform:scaleY(1);opacity:1} }
  .bubble { border-radius: 16px 16px 16px 4px; padding: 10px 14px; font-size: 12px; margin-top: 10px; line-height: 1.4; }
  .bubble.ai { background: var(--gradient-hot); color: white; border-radius: 16px 16px 4px 16px; }
  .bubble.user { background: #EDEAE4; color: var(--ink); }

  /* SECTIONS */
  section { padding: 100px 60px; }
  .section-inner { max-width: 1100px; margin: 0 auto; }
  .section-tag { display: inline-block; font-size: 12px; text-transform: uppercase; letter-spacing: 2px; font-weight: 700; color: var(--coral); margin-bottom: 16px; }
  .section-title { font-family: 'Instrument Serif', serif; font-size: clamp(36px, 4vw, 56px); line-height: 1.1; letter-spacing: -1.5px; margin-bottom: 20px; }
  .section-title em { font-style: italic; color: var(--coral); }
  .section-sub { font-size: 18px; color: var(--muted); max-width: 560px; line-height: 1.65; }

  /* LOGOS BAR */
  .logos-bar { background: var(--surface); padding: 28px 60px; border-top: 1px solid rgba(26,18,8,0.07); border-bottom: 1px solid rgba(26,18,8,0.07); }
  .logos-inner { max-width: 1100px; margin: 0 auto; display: flex; align-items: center; gap: 48px; flex-wrap: wrap; justify-content: center; }
  .logos-label { font-size: 12px; color: var(--muted); text-transform: uppercase; letter-spacing: 1.5px; font-weight: 600; white-space: nowrap; }
  .logo-pill { background: var(--white); border: 1px solid rgba(26,18,8,0.08); padding: 8px 20px; border-radius: 100px; font-size: 13px; font-weight: 600; color: var(--muted); display: flex; align-items: center; gap: 8px; }

  /* PROBLEM */
  .problem { background: var(--ink); color: var(--cream); }
  .problem .section-title { color: var(--cream); }
  .problem .section-sub { color: #A89E94; }
  .problem .section-tag { color: var(--coral-light); }
  .problem-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 2px; margin-top: 60px; }
  .problem-card { background: rgba(255,255,255,0.04); padding: 40px 32px; position: relative; overflow: hidden; transition: background .3s; }
  .problem-card:hover { background: rgba(255,255,255,0.07); }
  .problem-card::before { content: ''; position: absolute; top: 0; left: 0; width: 100%; height: 2px; background: var(--gradient-hot); }
  .problem-icon { font-size: 32px; margin-bottom: 16px; }
  .problem-h { font-family: 'Syne', sans-serif; font-size: 20px; font-weight: 700; margin-bottom: 10px; }
  .problem-p { font-size: 15px; color: #A89E94; line-height: 1.65; }
  .problem-stat { margin-top: 24px; font-family: 'Syne', sans-serif; font-size: 36px; font-weight: 800; background: var(--gradient-hot); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; }
  .problem-stat-label { font-size: 12px; color: #A89E94; }

  /* SOLUTION */
  .solution-layout { display: grid; grid-template-columns: 1fr 1fr; gap: 80px; align-items: center; margin-top: 60px; }
  .sol-card { background: var(--white); border-radius: 24px; padding: 28px; box-shadow: 0 20px 60px rgba(26,18,8,0.08); border: 1px solid rgba(26,18,8,0.06); }
  .sol-step { display: flex; gap: 16px; align-items: flex-start; margin-bottom: 20px; }
  .sol-step:last-child { margin-bottom: 0; }
  .sol-dot { width: 40px; height: 40px; border-radius: 12px; background: var(--gradient-hot); display: flex; align-items: center; justify-content: center; font-size: 18px; flex-shrink: 0; }
  .sol-step-text h4 { font-family: 'Syne', sans-serif; font-size: 15px; font-weight: 700; margin-bottom: 4px; }
  .sol-step-text p { font-size: 13px; color: var(--muted); line-height: 1.5; }
  .sol-connector { width: 2px; height: 20px; background: linear-gradient(to bottom, #FF4D6D, #FF9B3E); margin: 0 0 0 19px; }
  .solution-list { list-style: none; margin-top: 32px; }
  .solution-list li { display: flex; gap: 12px; align-items: flex-start; margin-bottom: 18px; font-size: 16px; }
  .solution-list li::before { content: '✓'; width: 22px; height: 22px; border-radius: 50%; background: var(--gradient-hot); color: white; display: flex; align-items: center; justify-content: center; font-size: 11px; font-weight: 700; flex-shrink: 0; margin-top: 1px; }

  /* FEATURES */
  .features { background: var(--surface); }
  .features-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px; margin-top: 60px; }
  .feat-card { background: var(--white); border-radius: 20px; padding: 32px 28px; border: 1px solid rgba(26,18,8,0.06); transition: all .3s; }
  .feat-card:hover { transform: translateY(-4px); box-shadow: 0 20px 50px rgba(26,18,8,0.1); }
  .feat-card.highlight { background: var(--ink); color: var(--cream); border-color: transparent; }
  .feat-icon { font-size: 32px; margin-bottom: 20px; }
  .feat-card h3 { font-family: 'Syne', sans-serif; font-size: 18px; font-weight: 700; margin-bottom: 10px; }
  .feat-card p { font-size: 14px; color: var(--muted); line-height: 1.65; }
  .feat-card.highlight p { color: #A89E94; }
  .feat-tag { display: inline-block; margin-top: 16px; font-size: 11px; text-transform: uppercase; letter-spacing: 1px; font-weight: 700; background: var(--gradient-hot); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; }

  /* HOW IT WORKS */
  .steps-layout { display: grid; grid-template-columns: repeat(4, 1fr); gap: 0; margin-top: 60px; position: relative; }
  .steps-layout::before { content: ''; position: absolute; top: 40px; left: 10%; right: 10%; height: 2px; background: linear-gradient(to right, #FF4D6D, #FF9B3E); z-index: 0; }
  .step-item { text-align: center; padding: 0 20px; position: relative; z-index: 1; }
  .step-circle { width: 80px; height: 80px; border-radius: 50%; background: var(--gradient-hot); border: none; display: flex; align-items: center; justify-content: center; font-size: 28px; margin: 0 auto 24px; box-shadow: 0 8px 30px rgba(255,77,109,0.3); }
  .step-item h4 { font-family: 'Syne', sans-serif; font-size: 16px; font-weight: 700; margin-bottom: 8px; }
  .step-item p { font-size: 14px; color: var(--muted); line-height: 1.5; }

  /* BENEFITS */
  .benefits-layout { display: grid; grid-template-columns: 1fr 1fr; gap: 80px; align-items: center; }
  .benefit-items { display: flex; flex-direction: column; gap: 16px; margin-top: 32px; }
  .benefit-row { display: flex; gap: 16px; align-items: flex-start; padding: 20px; border-radius: 16px; border: 1px solid rgba(26,18,8,0.07); background: var(--white); transition: all .3s; }
  .benefit-row:hover { border-color: var(--coral); box-shadow: 0 8px 30px rgba(255,77,109,0.1); }
  .benefit-icon { font-size: 28px; flex-shrink: 0; }
  .benefit-row h4 { font-family: 'Syne', sans-serif; font-size: 15px; font-weight: 700; margin-bottom: 4px; }
  .benefit-row p { font-size: 13px; color: var(--muted); line-height: 1.5; }
  .metrics-card { background: var(--ink); color: var(--cream); border-radius: 24px; padding: 36px; }
  .metric-row { display: flex; justify-content: space-between; align-items: center; padding: 14px 0; border-bottom: 1px solid rgba(255,255,255,0.08); }
  .metric-row:last-child { border-bottom: none; }
  .metric-label { font-size: 14px; color: #A89E94; }
  .metric-val { font-family: 'Syne', sans-serif; font-size: 20px; font-weight: 800; background: var(--gradient-hot); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; }

  /* ─── ROADMAP ─── */
  .roadmap { background: var(--ink); color: var(--cream); padding: 100px 60px; }
  .roadmap .section-title { color: var(--cream); }
  .roadmap .section-sub { color: #A89E94; }
  .roadmap .section-tag { color: var(--coral-light); }
  .roadmap-timeline { margin-top: 72px; position: relative; }
  .roadmap-timeline::before { content: ''; position: absolute; left: 50%; top: 0; bottom: 0; width: 2px; background: linear-gradient(to bottom, #FF4D6D, #FF9B3E, #6B21A8); transform: translateX(-50%); }
  .roadmap-phase { display: grid; grid-template-columns: 1fr 60px 1fr; gap: 0; align-items: start; margin-bottom: 64px; }
  .roadmap-phase:last-child { margin-bottom: 0; }
  .roadmap-left { text-align: right; padding-right: 40px; padding-top: 8px; }
  .roadmap-right { text-align: left; padding-left: 40px; padding-top: 8px; }
  .roadmap-center { display: flex; flex-direction: column; align-items: center; position: relative; z-index: 2; }
  .phase-node { width: 60px; height: 60px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 22px; flex-shrink: 0; border: 3px solid var(--ink); }
  .phase-node.live { background: var(--gradient-hot); box-shadow: 0 0 0 6px rgba(255,77,109,0.2); }
  .phase-node.soon { background: linear-gradient(135deg,#FF9B3E,#FFD166); box-shadow: 0 0 0 6px rgba(255,155,62,0.15); }
  .phase-node.future { background: linear-gradient(135deg,#6B21A8,#9333EA); box-shadow: 0 0 0 6px rgba(107,33,168,0.15); }
  .phase-node.horizon { background: linear-gradient(135deg,#1e3a5f,#2563EB); box-shadow: 0 0 0 6px rgba(37,99,235,0.15); }
  .phase-label { font-size: 11px; font-weight: 700; text-transform: uppercase; letter-spacing: 1.5px; margin-top: 10px; }
  .phase-label.live-label { color: var(--coral-light); }
  .phase-label.soon-label { color: var(--amber); }
  .phase-label.future-label { color: #C084FC; }
  .phase-label.horizon-label { color: #93C5FD; }
  .phase-card { background: rgba(255,255,255,0.05); border-radius: 20px; padding: 28px; border: 1px solid rgba(255,255,255,0.08); transition: background .3s; }
  .phase-card:hover { background: rgba(255,255,255,0.08); }
  .phase-card h3 { font-family: 'Syne', sans-serif; font-size: 20px; font-weight: 800; margin-bottom: 8px; }
  .phase-card .phase-desc { font-size: 14px; color: #A89E94; line-height: 1.6; margin-bottom: 20px; }
  .phase-features { list-style: none; display: flex; flex-direction: column; gap: 10px; }
  .phase-features li { display: flex; gap: 10px; font-size: 14px; color: var(--cream); align-items: flex-start; }
  .phase-features li span:first-child { flex-shrink: 0; margin-top: 1px; }
  .phase-badge { display: inline-flex; align-items: center; gap: 6px; padding: 4px 12px; border-radius: 100px; font-size: 11px; font-weight: 700; text-transform: uppercase; letter-spacing: .5px; margin-bottom: 12px; }
  .badge-live { background: rgba(255,77,109,0.15); color: var(--coral-light); }
  .badge-soon { background: rgba(255,155,62,0.15); color: var(--amber); }
  .badge-future { background: rgba(192,132,252,0.15); color: #C084FC; }
  .badge-horizon { background: rgba(147,197,253,0.15); color: #93C5FD; }

  /* PRICING */
  .pricing-section { background: var(--cream); }
  .pricing-center { max-width: 560px; margin: 60px auto 0; }
  .price-card-single { background: var(--ink); border-radius: 28px; padding: 48px; text-align: center; position: relative; overflow: hidden; box-shadow: 0 30px 80px rgba(26,18,8,0.2); }
  .price-card-single::before { content: ''; position: absolute; top: -80px; right: -80px; width: 300px; height: 300px; border-radius: 50%; background: radial-gradient(circle, rgba(255,77,109,.2) 0%, transparent 70%); }
  .early-badge { display: inline-block; background: var(--gradient-hot); color: white; font-size: 12px; font-weight: 700; padding: 6px 18px; border-radius: 100px; text-transform: uppercase; letter-spacing: 1px; margin-bottom: 24px; }
  .price-card-single h3 { font-family: 'Syne', sans-serif; font-size: 28px; font-weight: 800; color: var(--cream); margin-bottom: 8px; }
  .price-card-single .price-desc { font-size: 15px; color: #A89E94; margin-bottom: 32px; line-height: 1.6; }
  .big-price { font-family: 'Syne', sans-serif; font-size: 72px; font-weight: 800; line-height: 1; background: var(--gradient-hot); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; }
  .price-per { font-size: 15px; color: #A89E94; margin-bottom: 36px; margin-top: 4px; }
  .price-divider { height: 1px; background: rgba(255,255,255,0.1); margin-bottom: 28px; }
  .single-features { list-style: none; text-align: left; display: flex; flex-direction: column; gap: 14px; margin-bottom: 36px; }
  .single-features li { display: flex; gap: 12px; font-size: 15px; color: var(--cream); align-items: flex-start; }
  .single-features li span:first-child { color: var(--coral-light); font-weight: 700; flex-shrink: 0; }
  .stripe-btn { display: block; width: 100%; text-align: center; padding: 20px; border-radius: 16px; font-size: 18px; font-weight: 700; text-decoration: none; background: var(--gradient-hot); color: white; box-shadow: 0 10px 40px rgba(255,77,109,0.4); transition: all .3s; border: none; cursor: pointer; font-family: 'DM Sans', sans-serif; }
  .stripe-btn:hover { transform: translateY(-3px); box-shadow: 0 18px 50px rgba(255,77,109,0.5); }
  .price-trust { font-size: 13px; color: #6B6057; margin-top: 16px; display: flex; align-items: center; justify-content: center; gap: 6px; }
  .price-access-note { background: rgba(255,77,109,0.1); border: 1px solid rgba(255,77,109,0.2); border-radius: 12px; padding: 16px; margin-top: 20px; font-size: 13px; color: var(--coral-light); line-height: 1.5; }

  /* DEMO */
  .demo { background: var(--ink); color: var(--cream); }
  .demo-inner { max-width: 700px; margin: 0 auto; text-align: center; }
  .demo-visual { background: rgba(255,255,255,0.05); border-radius: 24px; padding: 48px; margin-top: 48px; border: 1px solid rgba(255,255,255,0.08); display: flex; flex-direction: column; align-items: center; gap: 20px; }
  .play-btn { width: 80px; height: 80px; border-radius: 50%; background: var(--gradient-hot); display: flex; align-items: center; justify-content: center; font-size: 28px; cursor: pointer; transition: all .3s; animation: ring 2s ease-in-out infinite; border: none; }
  @keyframes ring { 0%{box-shadow:0 0 0 0 rgba(255,77,109,0.4)} 70%{box-shadow:0 0 0 20px rgba(255,77,109,0)} 100%{box-shadow:0 0 0 0 rgba(255,77,109,0)} }
  .demo-chat { width: 100%; max-width: 420px; display: flex; flex-direction: column; gap: 10px; }
  .chat-msg { padding: 12px 16px; border-radius: 16px; font-size: 14px; max-width: 80%; line-height: 1.45; }
  .chat-msg.user { background: rgba(255,255,255,0.1); color: var(--cream); align-self: flex-start; border-radius: 16px 16px 16px 4px; }
  .chat-msg.ai { background: var(--gradient-hot); color: white; align-self: flex-end; border-radius: 16px 16px 4px 16px; }
  .chat-typing { align-self: flex-end; display: flex; gap: 4px; align-items: center; padding: 12px 16px; background: rgba(255,77,109,0.2); border-radius: 16px 16px 4px 16px; }
  .typing-dot { width: 6px; height: 6px; border-radius: 50%; background: var(--coral-light); animation: type-dot 1.2s ease-in-out infinite; }
  .typing-dot:nth-child(2){animation-delay:.2s}.typing-dot:nth-child(3){animation-delay:.4s}
  @keyframes type-dot { 0%,100%{transform:translateY(0)} 50%{transform:translateY(-5px)} }

  /* TESTIMONIALS */
  .testimonials { background: var(--surface); }
  .testi-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px; margin-top: 48px; }
  .testi-card { background: var(--white); border-radius: 20px; padding: 32px 28px; border: 1px solid rgba(26,18,8,0.06); }
  .stars { color: var(--amber); font-size: 14px; margin-bottom: 16px; }
  .testi-quote { font-family: 'Instrument Serif', serif; font-size: 18px; line-height: 1.5; margin-bottom: 20px; font-style: italic; }
  .testi-author { display: flex; align-items: center; gap: 12px; }
  .testi-avatar { width: 44px; height: 44px; border-radius: 50%; background: var(--gradient-hot); display: flex; align-items: center; justify-content: center; font-size: 18px; }
  .testi-name { font-family: 'Syne', sans-serif; font-size: 14px; font-weight: 700; }
  .testi-role { font-size: 12px; color: var(--muted); }
  .testi-badge { display: inline-block; background: var(--violet-soft); color: var(--violet); font-size: 11px; font-weight: 700; padding: 4px 10px; border-radius: 100px; margin-top: 4px; text-transform: uppercase; letter-spacing: .5px; }

  /* FAQ */
  .faq-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; margin-top: 60px; }
  .faq-item { background: var(--white); border-radius: 16px; padding: 28px; border: 1px solid rgba(26,18,8,0.06); cursor: pointer; transition: all .3s; }
  .faq-item:hover { border-color: var(--coral); }
  .faq-q { font-family: 'Syne', sans-serif; font-size: 16px; font-weight: 700; margin-bottom: 10px; display: flex; justify-content: space-between; align-items: flex-start; gap: 12px; }
  .faq-q::after { content: '+'; color: var(--coral); font-size: 20px; flex-shrink: 0; }
  .faq-a { font-size: 14px; color: var(--muted); line-height: 1.65; }

  /* LEAD / SIGNUP */
  .lead { background: var(--cream); }
  .lead-box { background: var(--ink); border-radius: 32px; padding: 72px; display: grid; grid-template-columns: 1fr 1fr; gap: 80px; align-items: center; position: relative; overflow: hidden; }
  .lead-box::before { content: ''; position: absolute; top: -100px; right: -100px; width: 400px; height: 400px; border-radius: 50%; background: radial-gradient(circle, rgba(255,77,109,.2) 0%, transparent 70%); }
  .lead-box .section-title { color: var(--cream); }
  .lead-box .section-sub { color: #A89E94; }
  .form-group { margin-bottom: 16px; }
  .form-input { width: 100%; padding: 16px 20px; background: rgba(255,255,255,0.07); border: 1px solid rgba(255,255,255,0.12); border-radius: 12px; color: var(--cream); font-size: 15px; font-family: 'DM Sans', sans-serif; transition: border-color .2s; outline: none; }
  .form-input::placeholder { color: #6B6057; }
  .form-input:focus { border-color: var(--coral); }
  .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
  .form-submit { width: 100%; margin-top: 8px; background: var(--gradient-hot); color: white; padding: 18px; border-radius: 12px; font-size: 16px; font-weight: 700; border: none; cursor: pointer; transition: all .25s; font-family: 'DM Sans', sans-serif; }
  .form-submit:hover { transform: translateY(-2px); box-shadow: 0 12px 40px rgba(255,77,109,0.4); }
  .form-trust { font-size: 12px; color: #6B6057; text-align: center; margin-top: 12px; }
  .lead-features { list-style: none; margin-top: 32px; display: flex; flex-direction: column; gap: 14px; }
  .lead-features li { display: flex; gap: 12px; align-items: center; color: var(--cream); font-size: 15px; }

  /* FINAL CTA */
  .final-cta { background: var(--ink); padding: 120px 60px; text-align: center; }
  .final-cta .section-title { color: var(--cream); font-size: clamp(40px, 5vw, 72px); max-width: 700px; margin: 0 auto 24px; }
  .final-cta .section-sub { color: #A89E94; margin: 0 auto 48px; max-width: 480px; }
  .final-ctas { display: flex; gap: 14px; justify-content: center; flex-wrap: wrap; }

  /* INTEGRATIONS */
  .integrations { background: var(--surface); padding: 60px; }
  .int-inner { max-width: 1100px; margin: 0 auto; text-align: center; }
  .int-label { font-size: 13px; text-transform: uppercase; letter-spacing: 2px; color: var(--muted); font-weight: 600; margin-bottom: 24px; }
  .int-grid { display: flex; gap: 12px; justify-content: center; flex-wrap: wrap; }
  .int-badge { background: var(--white); border: 1px solid rgba(26,18,8,0.08); padding: 10px 20px; border-radius: 100px; font-size: 13px; font-weight: 600; color: var(--ink); display: flex; align-items: center; gap: 8px; }

  /* FOOTER */
  footer { background: var(--ink); color: #A89E94; padding: 60px; border-top: 1px solid rgba(255,255,255,0.06); }
  .footer-grid { max-width: 1100px; margin: 0 auto; display: grid; grid-template-columns: 2fr 1fr 1fr 1fr; gap: 48px; }
  .footer-logo { font-family: 'Syne', sans-serif; font-size: 22px; font-weight: 800; background: var(--gradient-hot); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; margin-bottom: 12px; }
  .footer-tagline { font-size: 14px; line-height: 1.6; max-width: 260px; margin-bottom: 24px; }
  .footer-socials { display: flex; gap: 10px; }
  .social-btn { width: 36px; height: 36px; border-radius: 10px; background: rgba(255,255,255,0.06); display: flex; align-items: center; justify-content: center; font-size: 16px; cursor: pointer; transition: background .2s; }
  .social-btn:hover { background: rgba(255,77,109,0.2); }
  .footer-col h5 { font-family: 'Syne', sans-serif; font-size: 13px; font-weight: 700; color: var(--cream); text-transform: uppercase; letter-spacing: 1px; margin-bottom: 16px; }
  .footer-col ul { list-style: none; display: flex; flex-direction: column; gap: 10px; }
  .footer-col ul li a { color: #A89E94; text-decoration: none; font-size: 14px; transition: color .2s; }
  .footer-col ul li a:hover { color: var(--cream); }
  .footer-bottom { max-width: 1100px; margin: 48px auto 0; padding-top: 24px; border-top: 1px solid rgba(255,255,255,0.06); display: flex; justify-content: space-between; align-items: center; font-size: 13px; flex-wrap: wrap; gap: 12px; }
  .gdpr-badge { display: flex; align-items: center; gap: 6px; font-size: 12px; }
  .gdpr-dot { width: 6px; height: 6px; border-radius: 50%; background: #4ADE80; }

  /* ANIMATIONS */
  .fade-up { opacity: 0; transform: translateY(30px); transition: opacity .7s ease, transform .7s ease; }
  .fade-up.visible { opacity: 1; transform: translateY(0); }
  .fade-up-delay-1 { transition-delay: .1s; }
  .fade-up-delay-2 { transition-delay: .2s; }
  .fade-up-delay-3 { transition-delay: .3s; }
  .fade-up-delay-4 { transition-delay: .4s; }
  .fade-up-delay-5 { transition-delay: .5s; }

  @media (max-width: 900px) {
    nav { padding: 16px 24px; }
    .nav-links { display: none; }
    section { padding: 72px 24px; }
    .hero { padding: 120px 24px 60px; }
    .problem-grid, .features-grid, .testi-grid, .faq-grid { grid-template-columns: 1fr; }
    .solution-layout, .benefits-layout, .lead-box, .footer-grid { grid-template-columns: 1fr; gap: 40px; }
    .steps-layout { grid-template-columns: 1fr 1fr; }
    .steps-layout::before { display: none; }
    .lead-box { padding: 40px 28px; }
    .form-row { grid-template-columns: 1fr; }
    footer { padding: 40px 24px; }
    .roadmap-timeline::before { left: 30px; }
    .roadmap-phase { grid-template-columns: 40px 1fr; gap: 20px; }
    .roadmap-left { display: none; }
    .roadmap-center { align-items: flex-start; }
    .roadmap-right { padding-left: 20px; }
    .phase-label { display: none; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-logo">Resoassit</div>
  <ul class="nav-links">
    <li><a href="#features">Features</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#pricing">Pricing</a></li>
    <li><a href="#faq">FAQ</a></li>
  </ul>
  <a href="#signup" class="nav-cta">Book a Demo</a>
</nav>

<!-- HERO -->
<section class="hero" id="home">
  <div class="hero-blob blob-1"></div>
  <div class="hero-blob blob-2"></div>
  <div class="hero-blob blob-3"></div>
  <div class="hero-content fade-up visible">
    <div class="hero-badge"><span class="badge-dot"></span> AI Restaurant Platform · Early Access Now Open</div>
    <h1>Your restaurant phone,<br><em>answered perfectly.</em><br><span class="outline-text">Every time.</span></h1>
    <p class="hero-sub">Resoassit is the AI platform built for restaurants — starting with a voice agent that handles every call, books reservations, and remembers your regulars automatically.</p>
    <div class="hero-ctas">
      <a href="#signup" class="btn-primary">Book a Free Demo →</a>
      <a href="#roadmap" class="btn-secondary">See the Roadmap</a>
    </div>
    <div class="hero-stats">
      <div class="stat"><div class="stat-num">100%</div><div class="stat-label">Calls Answered</div></div>
      <div class="stat"><div class="stat-num">2 hrs</div><div class="stat-label">Staff Time Saved / Day</div></div>
      <div class="stat"><div class="stat-num">30%</div><div class="stat-label">More Reservations</div></div>
      <div class="stat"><div class="stat-num">5+</div><div class="stat-label">Languages Supported</div></div>
    </div>
  </div>
  <div class="hero-phone fade-up visible" style="transition-delay:.3s">
    <div class="phone-mockup">
      <div class="phone-notch"></div>
      <div class="phone-screen">
        <div class="call-avatar">🎙️</div>
        <div class="call-name">Resoassit AI</div>
        <div class="call-status">Connected · 0:38</div>
        <div class="wave-bars">
          <div class="wave-bar"></div><div class="wave-bar"></div><div class="wave-bar"></div>
          <div class="wave-bar"></div><div class="wave-bar"></div><div class="wave-bar"></div><div class="wave-bar"></div>
        </div>
        <div class="bubble ai">"Good evening! Welcome to Bella Vista. How can I help you tonight?"</div>
        <div class="bubble user">"Table for two, Saturday 8pm please."</div>
        <div class="bubble ai">"Perfect — confirmed for Saturday at 8pm. Any dietary preferences I should note?"</div>
      </div>
    </div>
  </div>
</section>

<!-- LOGOS BAR -->
<div class="logos-bar">
  <div class="logos-inner">
    <span class="logos-label">Integrates with</span>
    <div class="logo-pill"><span>📅</span> Google Calendar</div>
    <div class="logo-pill"><span>💳</span> Square POS</div>
    <div class="logo-pill"><span>⚡</span> Lightspeed</div>
    <div class="logo-pill"><span>🍴</span> TheFork</div>
    <div class="logo-pill"><span>📊</span> OpenTable</div>
    <div class="logo-pill"><span>📨</span> Twilio SMS</div>
  </div>
</div>

<!-- PROBLEM -->
<section class="problem" id="problem">
  <div class="section-inner">
    <div class="fade-up">
      <span class="section-tag">The Problem</span>
      <h2 class="section-title">Every missed call is a <em>missed reservation</em></h2>
      <p class="section-sub">Restaurants lose thousands in revenue every week from unanswered calls, overwhelmed staff, and zero operational visibility.</p>
    </div>
    <div class="problem-grid">
      <div class="problem-card fade-up fade-up-delay-1">
        <div class="problem-icon">📵</div>
        <h3 class="problem-h">Missed Calls During Service</h3>
        <p class="problem-p">Your team is busy with guests at the table. The phone rings 20+ times a day and no one can answer. Those are bookings walking out the door.</p>
        <div class="problem-stat">62%</div>
        <div class="problem-stat-label">of restaurant calls go unanswered during peak hours</div>
      </div>
      <div class="problem-card fade-up fade-up-delay-2">
        <div class="problem-icon">😤</div>
        <h3 class="problem-h">Overwhelmed Staff</h3>
        <p class="problem-p">Your best people spend hours every shift answering the same questions about opening hours, menus, and availability. It kills morale and service quality.</p>
        <div class="problem-stat">2.5 hrs</div>
        <div class="problem-stat-label">average staff time lost to phone calls daily</div>
      </div>
      <div class="problem-card fade-up fade-up-delay-3">
        <div class="problem-icon">💸</div>
        <h3 class="problem-h">Lost Revenue, Every Night</h3>
        <p class="problem-p">Each missed call is €40–120 in lost revenue. No inventory visibility, no payroll overview, no event strategy — all costing you money daily.</p>
        <div class="problem-stat">€8,400</div>
        <div class="problem-stat-label">average annual revenue lost to missed calls alone</div>
      </div>
    </div>
  </div>
</section>

<!-- SOLUTION -->
<section id="solution" style="background:var(--cream)">
  <div class="section-inner">
    <div class="solution-layout">
      <div class="fade-up">
        <span class="section-tag">The Solution</span>
        <h2 class="section-title">Your AI host, <em>always on call</em></h2>
        <p class="section-sub">Resoassit connects to your restaurant's landline and handles every call automatically — from bookings to takeaway orders, in any language, any time of day.</p>
        <ul class="solution-list">
          <li>Answers every call instantly — no hold time, no voicemail</li>
          <li>Books reservations directly into your calendar</li>
          <li>Handles takeaway and pre-orders automatically</li>
          <li>Speaks English, German, French, Spanish & more</li>
          <li>Remembers your regulars and their preferences</li>
          <li>Sends SMS and email confirmations automatically</li>
        </ul>
        <a href="#signup" class="btn-primary" style="margin-top:36px">Get Early Access →</a>
      </div>
      <div class="solution-visual fade-up fade-up-delay-2">
        <div class="sol-card">
          <div class="sol-step">
            <div class="sol-dot">📞</div>
            <div class="sol-step-text">
              <h4>Customer Calls Your Restaurant</h4>
              <p>Your existing landline is connected to Resoassit. The AI picks up in under 2 seconds, every time.</p>
            </div>
          </div>
          <div class="sol-connector"></div>
          <div class="sol-step">
            <div class="sol-dot">🧠</div>
            <div class="sol-step-text">
              <h4>AI Understands the Intent</h4>
              <p>Resoassit detects language, greets the guest warmly, and handles reservations, orders or questions.</p>
            </div>
          </div>
          <div class="sol-connector"></div>
          <div class="sol-step">
            <div class="sol-dot">📅</div>
            <div class="sol-step-text">
              <h4>Books & Confirms Automatically</h4>
              <p>Reservation checked against your live calendar, booked, and confirmed — all in the same call.</p>
            </div>
          </div>
          <div class="sol-connector"></div>
          <div class="sol-step">
            <div class="sol-dot">📊</div>
            <div class="sol-step-text">
              <h4>You See Everything in Your Dashboard</h4>
              <p>Every call, booking, order, and customer insight is captured. Zero admin work required.</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- FEATURES -->
<section class="features" id="features">
  <div class="section-inner">
    <div class="fade-up" style="text-align:center">
      <span class="section-tag">Features</span>
      <h2 class="section-title">Everything your restaurant <em>needs to thrive</em></h2>
      <p class="section-sub" style="margin:0 auto">Built specifically for hospitality — not a generic chatbot repurposed for restaurants.</p>
    </div>
    <div class="features-grid">
      <div class="feat-card fade-up fade-up-delay-1">
        <div class="feat-icon">📅</div>
        <h3>Smart Reservations</h3>
        <p>Real-time availability checks, instant booking, automatic conflict prevention, and calendar sync. No double bookings, ever.</p>
        <div class="feat-tag">LIVE NOW</div>
      </div>
      <div class="feat-card highlight fade-up fade-up-delay-2">
        <div class="feat-icon">🌍</div>
        <h3>Multilingual by Default</h3>
        <p>Detects and switches languages mid-call. English, German, French, Spanish and more — your guests always feel at home.</p>
        <div class="feat-tag">LIVE NOW</div>
      </div>
      <div class="feat-card fade-up fade-up-delay-3">
        <div class="feat-icon">🍽️</div>
        <h3>Menu Recommendations</h3>
        <p>Knows your full menu, recommends dishes based on dietary preferences, allergies, and occasion. Upselling, automated.</p>
        <div class="feat-tag">LIVE NOW</div>
      </div>
      <div class="feat-card fade-up fade-up-delay-1">
        <div class="feat-icon">🥡</div>
        <h3>Takeaway & Pre-Orders</h3>
        <p>Handles complete takeaway order intake — items, quantities, timing, and payment preferences. Every order captured.</p>
        <div class="feat-tag">LIVE NOW</div>
      </div>
      <div class="feat-card fade-up fade-up-delay-2">
        <div class="feat-icon">👤</div>
        <h3>Regular Customer Memory</h3>
        <p>Recognizes returning callers by phone number, greets them by name, and loads their preferences automatically.</p>
        <div class="feat-tag">LIVE NOW</div>
      </div>
      <div class="feat-card fade-up fade-up-delay-3">
        <div class="feat-icon">📊</div>
        <h3>Owner Analytics Dashboard</h3>
        <p>Every call, booking, and customer insight in one place. Peak call times, no-show rates, popular dishes, revenue trends.</p>
        <div class="feat-tag">LIVE NOW</div>
      </div>
    </div>
  </div>
</section>

<!-- HOW IT WORKS -->
<section id="how" style="background:var(--cream)">
  <div class="section-inner">
    <div class="fade-up" style="text-align:center">
      <span class="section-tag">How It Works</span>
      <h2 class="section-title">Up and running in <em>under 48 hours</em></h2>
      <p class="section-sub" style="margin:0 auto">No technical setup required. We configure everything for your restaurant and you're live within two days.</p>
    </div>
    <div class="steps-layout">
      <div class="step-item fade-up fade-up-delay-1">
        <div class="step-circle">📋</div>
        <h4>1. Onboarding Call</h4>
        <p>30-minute setup call. We collect your menu, opening hours, and calendar access. No IT skills needed.</p>
      </div>
      <div class="step-item fade-up fade-up-delay-2">
        <div class="step-circle">⚙️</div>
        <h4>2. We Configure Resoassit</h4>
        <p>Our team trains the AI on your restaurant's voice, menu, policies and preferred tone of service.</p>
      </div>
      <div class="step-item fade-up fade-up-delay-3">
        <div class="step-circle">🧪</div>
        <h4>3. Shadow Launch</h4>
        <p>AI handles calls alongside your team while we tune everything to perfection over 2 weeks.</p>
      </div>
      <div class="step-item fade-up fade-up-delay-4">
        <div class="step-circle">🚀</div>
        <h4>4. Full Launch</h4>
        <p>Resoassit goes fully live. Your phone is always answered. Your team is free. Revenue grows.</p>
      </div>
    </div>
  </div>
</section>

<!-- BENEFITS -->
<section style="background:var(--cream)">
  <div class="section-inner">
    <div class="benefits-layout">
      <div class="fade-up">
        <span class="section-tag">Benefits</span>
        <h2 class="section-title">More bookings. Less <em>chaos.</em></h2>
        <p class="section-sub">Resoassit doesn't replace your team — it frees them to do what they do best: delivering an exceptional guest experience.</p>
        <div class="benefit-items">
          <div class="benefit-row">
            <div class="benefit-icon">📈</div>
            <div>
              <h4>30% More Reservations</h4>
              <p>Every call is answered, every booking captured. Restaurants see a consistent lift in monthly reservations.</p>
            </div>
          </div>
          <div class="benefit-row">
            <div class="benefit-icon">🌟</div>
            <div>
              <h4>Better Guest Experience</h4>
              <p>Instant answers, personalized greetings, and confirmation messages. First impressions that convert to return visits.</p>
            </div>
          </div>
          <div class="benefit-row">
            <div class="benefit-icon">⏱️</div>
            <div>
              <h4>2+ Hours Saved Per Day</h4>
              <p>Your staff stop fielding repetitive calls and focus on the room. Morale improves. Service quality rises.</p>
            </div>
          </div>
          <div class="benefit-row">
            <div class="benefit-icon">🔍</div>
            <div>
              <h4>Actionable Business Insights</h4>
              <p>Weekly reports on peak call times, popular dishes, customer demographics — data your competitors don't have.</p>
            </div>
          </div>
        </div>
      </div>
      <div class="fade-up fade-up-delay-2">
        <div class="metrics-card">
          <div style="font-family:'Syne',sans-serif;font-size:16px;font-weight:700;color:var(--cream);margin-bottom:20px">📊 Pilot Restaurant Results</div>
          <div class="metric-row"><span class="metric-label">Calls Answered</span><span class="metric-val">100%</span></div>
          <div class="metric-row"><span class="metric-label">Booking Accuracy</span><span class="metric-val">>98%</span></div>
          <div class="metric-row"><span class="metric-label">Staff Time Saved</span><span class="metric-val">2.5 hrs/day</span></div>
          <div class="metric-row"><span class="metric-label">Reservation Increase</span><span class="metric-val">+31%</span></div>
          <div class="metric-row"><span class="metric-label">Customer NPS</span><span class="metric-val">8.4 / 10</span></div>
          <div class="metric-row"><span class="metric-label">Owner Satisfaction</span><span class="metric-val">9.1 / 10</span></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- DEMO -->
<section class="demo" id="demo">
  <div class="section-inner">
    <div class="demo-inner">
      <div class="fade-up">
        <span class="section-tag">Live Demo</span>
        <h2 class="section-title" style="color:var(--cream)">Hear Resoassit <em>in action</em></h2>
        <p class="section-sub" style="color:#A89E94;margin:0 auto">Book a 20-minute walkthrough with our team to see it configured live for your restaurant.</p>
      </div>
      <div class="demo-visual fade-up fade-up-delay-2">
        <button class="play-btn">▶</button>
        <div style="color:#A89E94;font-size:14px">Sample Reservation Call — Live Demo</div>
        <div class="demo-chat">
          <div class="chat-msg user">Hi, table for 4 this Friday at 8pm?</div>
          <div class="chat-msg ai">Of course! Table for 4, Friday at 8pm — confirmed. May I take your name and note any dietary preferences?</div>
          <div class="chat-msg user">Sarah — one of us is vegetarian.</div>
          <div class="chat-msg ai">Perfect, Sarah! Vegetarian noted. You'll receive an SMS confirmation shortly. Anything else?</div>
          <div class="chat-typing"><div class="typing-dot"></div><div class="typing-dot"></div><div class="typing-dot"></div></div>
        </div>
        <a href="#signup" class="btn-primary">Schedule a Live Demo →</a>
      </div>
    </div>
  </div>
</section>

<!-- TESTIMONIALS -->
<section class="testimonials">
  <div class="section-inner">
    <div class="fade-up" style="text-align:center">
      <span class="section-tag">Early Results</span>
      <h2 class="section-title">Restaurant owners are <em>already impressed</em></h2>
    </div>
    <div class="testi-grid">
      <div class="testi-card fade-up fade-up-delay-1">
        <div class="stars">★★★★★</div>
        <div class="testi-quote">"We were missing 15–20 calls a night during service. Resoassit solved that completely. It sounds so natural our guests don't even realize it's AI."</div>
        <div class="testi-author">
          <div class="testi-avatar">🍕</div>
          <div><div class="testi-name">Marco R.</div><div class="testi-role">Owner, Osteria Milano</div><div class="testi-badge">PILOT · MUNICH</div></div>
        </div>
      </div>
      <div class="testi-card fade-up fade-up-delay-2">
        <div class="stars">★★★★★</div>
        <div class="testi-quote">"My front-of-house team was drowning in phone calls. Now they're focused entirely on guests in the restaurant. The atmosphere has completely changed."</div>
        <div class="testi-author">
          <div class="testi-avatar">🥘</div>
          <div><div class="testi-name">Sophie L.</div><div class="testi-role">Manager, Brasserie Lumière</div><div class="testi-badge">PILOT · BERLIN</div></div>
        </div>
      </div>
      <div class="testi-card fade-up fade-up-delay-3">
        <div class="stars">★★★★★</div>
        <div class="testi-quote">"The multilingual capability is brilliant. We serve a lot of international guests and the AI just handles it — in their language, seamlessly."</div>
        <div class="testi-author">
          <div class="testi-avatar">🍣</div>
          <div><div class="testi-name">James K.</div><div class="testi-role">Owner, Kibo Restaurant</div><div class="testi-badge">PILOT · LONDON</div></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ═══════════════════════════════════════════
     PRODUCT ROADMAP
════════════════════════════════════════════ -->
<section class="roadmap" id="roadmap">
  <div class="section-inner">
    <div class="fade-up" style="text-align:center">
      <span class="section-tag">Product Roadmap</span>
      <h2 class="section-title">Built to run your <em>entire restaurant</em></h2>
      <p class="section-sub" style="margin:0 auto;color:#A89E94">We're starting with AI voice — and we're not stopping there. Resoassit is growing into the all-in-one operating system for modern restaurants.</p>
    </div>

    <div class="roadmap-timeline">

      <!-- PHASE 1: LIVE -->
      <div class="roadmap-phase fade-up">
        <div class="roadmap-left">
          <div class="phase-card">
            <div class="phase-badge badge-live">✅ Live Now</div>
            <h3>Phase 1 — AI Voice Agent</h3>
            <p class="phase-desc">The foundation of Resoassit. Your restaurant's phone is answered by an intelligent AI host 24/7 — handling bookings, orders, and guest care automatically.</p>
            <ul class="phase-features">
              <li><span>📞</span><span>AI answers every inbound call instantly</span></li>
              <li><span>📅</span><span>Reservations with live calendar sync & conflict prevention</span></li>
              <li><span>🌍</span><span>Multilingual support (EN, DE, FR, ES, IT)</span></li>
              <li><span>🍽️</span><span>Menu recommendations & allergy capture</span></li>
              <li><span>🥡</span><span>Takeaway & pre-order intake</span></li>
              <li><span>🎂</span><span>Event & birthday reservations</span></li>
              <li><span>👤</span><span>Regular customer recognition & preference memory</span></li>
              <li><span>📊</span><span>Owner analytics dashboard</span></li>
              <li><span>📱</span><span>Automatic SMS & email confirmations</span></li>
              <li><span>🔒</span><span>GDPR-compliant data storage</span></li>
            </ul>
          </div>
        </div>
        <div class="roadmap-center">
          <div class="phase-node live">🎙️</div>
          <div class="phase-label live-label">Live Now</div>
        </div>
        <div class="roadmap-right"></div>
      </div>

      <!-- PHASE 2: COMING SOON -->
      <div class="roadmap-phase fade-up fade-up-delay-1">
        <div class="roadmap-left"></div>
        <div class="roadmap-center">
          <div class="phase-node soon">🧑‍🍳</div>
          <div class="phase-label soon-label">Coming Soon</div>
        </div>
        <div class="roadmap-right">
          <div class="phase-card">
            <div class="phase-badge badge-soon">🔜 Coming Soon</div>
            <h3>Phase 2 — Smart Order Management</h3>
            <p class="phase-desc">A complete in-restaurant ordering system that connects every employee, every table, and the kitchen in real time — with integrated payment collection.</p>
            <ul class="phase-features">
              <li><span>📱</span><span>Staff app — each employee has their own ordering device</span></li>
              <li><span>🖨️</span><span>Orders print automatically in the kitchen the moment they're placed</span></li>
              <li><span>💳</span><span>Payment collection system — take payment directly at the table</span></li>
              <li><span>🔄</span><span>Live order status tracking for kitchen and floor staff</span></li>
              <li><span>🛎️</span><span>Table management — assign, split, merge bills with one tap</span></li>
              <li><span>📊</span><span>Real-time sales data flowing into the owner dashboard</span></li>
            </ul>
          </div>
        </div>
      </div>

      <!-- PHASE 3: LOGISTICS -->
      <div class="roadmap-phase fade-up fade-up-delay-2">
        <div class="roadmap-left">
          <div class="phase-card">
            <div class="phase-badge badge-future">🔮 Future Phase</div>
            <h3>Phase 3 — Logistics & Revenue Intelligence</h3>
            <p class="phase-desc">Turn your sales data into smarter purchasing decisions and targeted events that fill tables on slow nights. Let your data work for you.</p>
            <ul class="phase-features">
              <li><span>🛒</span><span>Auto-generated weekly shopping list based on sales patterns</span></li>
              <li><span>📋</span><span>Pre-order suggestions sent to the owner dashboard every Monday</span></li>
              <li><span>📉</span><span>Low-revenue day detection with automated event suggestions</span></li>
              <li><span>🎉</span><span>AI-designed events for VIP & regular guests based on their dietary preferences (e.g. wine pairing evening for vegetarian regulars)</span></li>
              <li><span>💌</span><span>Personalised invitations sent automatically to the right guest segment</span></li>
              <li><span>📈</span><span>Month-on-month revenue trend analysis with actionable recommendations</span></li>
            </ul>
          </div>
        </div>
        <div class="roadmap-center">
          <div class="phase-node future">📦</div>
          <div class="phase-label future-label">Future Phase</div>
        </div>
        <div class="roadmap-right"></div>
      </div>

      <!-- PHASE 4: PAYROLL -->
      <div class="roadmap-phase fade-up fade-up-delay-3">
        <div class="roadmap-left"></div>
        <div class="roadmap-center">
          <div class="phase-node horizon">👥</div>
          <div class="phase-label horizon-label">On the Horizon</div>
        </div>
        <div class="roadmap-right">
          <div class="phase-card">
            <div class="phase-badge badge-horizon">🌐 On the Horizon</div>
            <h3>Phase 4 — Payroll & Staff Management</h3>
            <p class="phase-desc">The final piece of the puzzle — a fully synchronized employee management system that connects scheduling, ordering, performance, and payroll in one place.</p>
            <ul class="phase-features">
              <li><span>🗓️</span><span>Employee scheduling synced with reservation and booking data</span></li>
              <li><span>⏱️</span><span>Automatic time tracking via the staff ordering app</span></li>
              <li><span>💰</span><span>Payroll calculation integrated with hours worked and sales performance</span></li>
              <li><span>📑</span><span>Digital contracts, onboarding documents, and staff records</span></li>
              <li><span>📊</span><span>Staff performance analytics tied to table revenue and order speed</span></li>
              <li><span>🔗</span><span>Single dashboard for the entire team — from kitchen to management</span></li>
            </ul>
          </div>
        </div>
      </div>

    </div>

    <!-- ROADMAP SUMMARY BAR -->
    <div style="margin-top:72px;background:rgba(255,255,255,0.04);border-radius:20px;padding:32px 40px;border:1px solid rgba(255,255,255,0.08);display:flex;gap:0;flex-wrap:wrap;" class="fade-up">
      <div style="flex:1;min-width:200px;padding:16px 24px;border-right:1px solid rgba(255,255,255,0.08);text-align:center">
        <div style="font-size:28px;margin-bottom:8px">🎙️</div>
        <div style="font-family:'Syne',sans-serif;font-size:14px;font-weight:700;color:var(--cream)">AI Voice Agent</div>
        <div style="font-size:12px;color:var(--coral-light);margin-top:4px;font-weight:700">LIVE NOW</div>
      </div>
      <div style="flex:1;min-width:200px;padding:16px 24px;border-right:1px solid rgba(255,255,255,0.08);text-align:center">
        <div style="font-size:28px;margin-bottom:8px">🧑‍🍳</div>
        <div style="font-family:'Syne',sans-serif;font-size:14px;font-weight:700;color:var(--cream)">Order Management</div>
        <div style="font-size:12px;color:var(--amber);margin-top:4px;font-weight:700">COMING SOON</div>
      </div>
      <div style="flex:1;min-width:200px;padding:16px 24px;border-right:1px solid rgba(255,255,255,0.08);text-align:center">
        <div style="font-size:28px;margin-bottom:8px">📦</div>
        <div style="font-family:'Syne',sans-serif;font-size:14px;font-weight:700;color:var(--cream)">Logistics & Events</div>
        <div style="font-size:12px;color:#C084FC;margin-top:4px;font-weight:700">FUTURE PHASE</div>
      </div>
      <div style="flex:1;min-width:200px;padding:16px 24px;text-align:center">
        <div style="font-size:28px;margin-bottom:8px">👥</div>
        <div style="font-family:'Syne',sans-serif;font-size:14px;font-weight:700;color:var(--cream)">Payroll & Staff</div>
        <div style="font-size:12px;color:#93C5FD;margin-top:4px;font-weight:700">ON THE HORIZON</div>
      </div>
    </div>

  </div>
</section>

<!-- PRICING -->
<section class="pricing-section" id="pricing">
  <div class="section-inner">
    <div class="fade-up" style="text-align:center">
      <span class="section-tag">Pricing</span>
      <h2 class="section-title">One plan. <em>Zero complexity.</em></h2>
      <p class="section-sub" style="margin:0 auto">Start with Early Access today and get 2 weeks free. Then continue at €120/month with full access to every upcoming feature as we build it.</p>
    </div>
    <div class="pricing-center fade-up fade-up-delay-2">
      <div class="price-card-single">
        <div class="early-badge">🎉 Early Access — Limited Spots</div>
        <h3>Resoassit Early Access</h3>
        <p class="price-desc">Join now and be among the first restaurants to get Resoassit. Early access members are first to unlock every new feature as we launch it — at a locked-in rate.</p>
        <div class="big-price">€120</div>
        <div class="price-per">per restaurant / month · after your free 2-week trial</div>
        <div class="price-divider"></div>
        <ul class="single-features">
          <li><span>✓</span><span>Full AI Voice Agent — unlimited calls</span></li>
          <li><span>✓</span><span>Reservations + live calendar sync</span></li>
          <li><span>✓</span><span>Takeaway & pre-order handling</span></li>
          <li><span>✓</span><span>Multilingual (5+ languages)</span></li>
          <li><span>✓</span><span>Customer memory & preference tracking</span></li>
          <li><span>✓</span><span>Analytics dashboard</span></li>
          <li><span>✓</span><span>Priority onboarding within 48 hrs</span></li>
          <li><span>✓</span><span>Early access to all upcoming features (Order Mgmt, Logistics, Payroll)</span></li>
          <li><span>✓</span><span>Locked-in early adopter rate — price never increases</span></li>
        </ul>
        <a href="#signup" class="stripe-btn">Start Free 2-Week Trial →</a>
        <p class="price-trust">🔒 Secure payment via Stripe · Cancel anytime · No hidden fees</p>
        <div class="price-access-note">✨ Early access members get every new feature — Order Management, Logistics Intelligence, and Payroll — at no extra charge during the pilot programme.</div>
      </div>
    </div>
  </div>
</section>

<!-- INTEGRATIONS -->
<div class="integrations">
  <div class="int-inner">
    <div class="int-label">Integrates seamlessly with your existing tools</div>
    <div class="int-grid">
      <div class="int-badge"><span>📅</span> Google Calendar</div>
      <div class="int-badge"><span>💳</span> Square POS</div>
      <div class="int-badge"><span>⚡</span> Lightspeed</div>
      <div class="int-badge"><span>📱</span> Twilio SMS</div>
      <div class="int-badge"><span>🍴</span> TheFork</div>
      <div class="int-badge"><span>📊</span> OpenTable</div>
      <div class="int-badge"><span>🔗</span> Any landline / SIP</div>
    </div>
  </div>
</div>

<!-- LEAD CAPTURE -->
<section class="lead" id="signup">
  <div class="section-inner">
    <div class="lead-box">
      <div class="fade-up">
        <span class="section-tag" style="color:var(--coral-light)">Get Early Access</span>
        <h2 class="section-title">Start your <em>free trial</em> today</h2>
        <p class="section-sub">Join our early access programme. First 2 weeks completely free, then just €120/month. We set everything up — no tech skills needed.</p>
        <ul class="lead-features">
          <li><span>✅</span> 2-week free trial — no credit card to start</li>
          <li><span>✅</span> Setup completed within 48 hours</li>
          <li><span>✅</span> Personal onboarding call included</li>
          <li><span>✅</span> Early access to all upcoming features</li>
          <li><span>✅</span> Cancel anytime, no lock-in contracts</li>
          <li><span>✅</span> GDPR-compliant from day one</li>
        </ul>
      </div>
      <div class="fade-up fade-up-delay-2">
        <!-- SUCCESS STATE (hidden by default) -->
        <div id="form-success" style="display:none;text-align:center;padding:40px 20px">
          <div style="font-size:56px;margin-bottom:16px">🎉</div>
          <div style="font-family:'Syne',sans-serif;font-size:22px;font-weight:800;color:var(--cream);margin-bottom:8px">You're in!</div>
          <div style="font-size:15px;color:#A89E94;margin-bottom:28px">Your details have been saved. Redirecting you to book your demo...</div>
          <div style="width:48px;height:4px;background:var(--gradient-hot);border-radius:4px;margin:0 auto;animation:progress-bar 2s linear forwards"></div>
        </div>
        <!-- ERROR MESSAGE -->
        <div id="form-error" style="display:none;background:rgba(255,77,109,0.15);border:1px solid rgba(255,77,109,0.3);border-radius:12px;padding:14px 16px;font-size:14px;color:var(--coral-light);margin-bottom:16px">
          ⚠️ Something went wrong. Please try again or email us at <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="cea6aba2a2a18ebcabbda1afbdbda7bae0ada1a3">[email&#160;protected]</a>
        </div>
        <!-- THE FORM -->
        <div id="contact-form">
          <div class="form-group">
            <input id="f-restaurant" class="form-input" type="text" placeholder="Restaurant Name" required>
          </div>
          <div class="form-group">
            <input id="f-name" class="form-input" type="text" placeholder="Your Name" required>
          </div>
          <div class="form-group">
            <input id="f-email" class="form-input" type="email" placeholder="Email Address" required>
          </div>
          <div class="form-group">
            <input id="f-phone" class="form-input" type="tel" placeholder="Phone Number">
          </div>
          <div class="form-group">
            <select id="f-locations" class="form-input" style="appearance:none">
              <option value="" disabled selected>Number of locations</option>
              <option>1 location</option>
              <option>2–5 locations</option>
              <option>6–20 locations</option>
              <option>20+ locations</option>
            </select>
          </div>
          <button id="form-btn" class="form-submit" onclick="handleFormSubmit(event)">
            Book My Free Demo →
          </button>
          <p class="form-trust">🔒 Your data is secure and GDPR compliant. We never share your information.</p>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- FAQ -->
<section id="faq" style="background:var(--surface)">
  <div class="section-inner">
    <div class="fade-up" style="text-align:center">
      <span class="section-tag">FAQ</span>
      <h2 class="section-title">Frequently asked <em>questions</em></h2>
    </div>
    <div class="faq-grid">
      <div class="faq-item fade-up fade-up-delay-1">
        <div class="faq-q">Does the AI replace my staff?</div>
        <p class="faq-a">No — Resoassit handles phone calls so your team can focus on delivering exceptional in-person service. Think of it as a dedicated phone receptionist that never takes a break.</p>
      </div>
      <div class="faq-item fade-up fade-up-delay-2">
        <div class="faq-q">How does calendar integration work?</div>
        <p class="faq-a">We connect to your Google Calendar via OAuth during onboarding. The AI checks live availability in real time and creates bookings directly — no manual entry needed.</p>
      </div>
      <div class="faq-item fade-up fade-up-delay-3">
        <div class="faq-q">Can the AI speak multiple languages?</div>
        <p class="faq-a">Yes. Resoassit automatically detects the caller's language and responds accordingly. We support English, German, French, Spanish, and Italian — with more being added.</p>
      </div>
      <div class="faq-item fade-up fade-up-delay-4">
        <div class="faq-q">What if the AI can't handle a call?</div>
        <p class="faq-a">For complex edge cases, it can gracefully transfer the call to a staff member or offer to take a message. The vast majority of calls are handled end-to-end automatically.</p>
      </div>
      <div class="faq-item fade-up fade-up-delay-1">
        <div class="faq-q">Do we need to change our phone number?</div>
        <p class="faq-a">Not at all. We use SIP forwarding to connect Resoassit to your existing landline. Your restaurant number stays exactly the same — guests won't notice any difference.</p>
      </div>
      <div class="faq-item fade-up fade-up-delay-2">
        <div class="faq-q">What's included in early access?</div>
        <p class="faq-a">Early access members get the full AI Voice Agent today plus first access to every upcoming feature — Order Management, Logistics Intelligence, and Payroll — at the locked-in €120/month rate.</p>
      </div>
      <div class="faq-item fade-up fade-up-delay-3">
        <div class="faq-q">When does the free trial end?</div>
        <p class="faq-a">Your 2-week free trial starts from the date your Resoassit goes live in your restaurant. After that, you're billed €120/month. You can cancel before the trial ends with no charge.</p>
      </div>
      <div class="faq-item fade-up fade-up-delay-4">
        <div class="faq-q">Is my customer data safe?</div>
        <p class="faq-a">Absolutely. We're fully GDPR compliant. All data is encrypted, stored in the EU, and customers can request deletion at any time. We never sell data to third parties.</p>
      </div>
    </div>
  </div>
</section>

<!-- FINAL CTA -->
<section class="final-cta">
  <div class="fade-up">
    <span class="section-tag" style="color:var(--coral-light)">Ready to Start?</span>
    <h2 class="section-title">Your phone. <em>Always answered.</em><br>Your restaurant. Always growing.</h2>
    <p class="section-sub">Join the restaurants already using Resoassit. Start free for 2 weeks — no credit card, no commitment, no stress.</p>
    <div class="final-ctas">
      <a href="#signup" class="btn-primary">Start Free 2-Week Trial →</a>
      <a href="#demo" class="btn-secondary" style="background:rgba(255,255,255,0.08);color:var(--cream);border-color:rgba(255,255,255,0.2)">Watch Live Demo</a>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-grid">
    <div>
      <div class="footer-logo">Resoassit</div>
      <p class="footer-tagline">The AI platform built for restaurants. Starting with voice — growing into your full operating system.</p>
      <div class="footer-socials">
        <div class="social-btn">💼</div>
        <div class="social-btn">🐦</div>
        <div class="social-btn">📸</div>
      </div>
    </div>
    <div class="footer-col">
      <h5>Product</h5>
      <ul>
        <li><a href="#features">Features</a></li>
        <li><a href="#roadmap">Roadmap</a></li>
        <li><a href="#how">How It Works</a></li>
        <li><a href="#pricing">Pricing</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h5>Company</h5>
      <ul>
        <li><a href="#">About</a></li>
        <li><a href="#">Blog</a></li>
        <li><a href="#">Careers</a></li>
        <li><a href="#">Contact</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h5>Legal</h5>
      <ul>
        <li><a href="#">Privacy Policy</a></li>
        <li><a href="#">Terms of Service</a></li>
        <li><a href="#">GDPR Compliance</a></li>
        <li><a href="#">Cookie Policy</a></li>
      </ul>
    </div>
  </div>
  <div class="footer-bottom">
    <span>© 2025 Resoassit Technologies. All rights reserved.</span>
    <div style="display:flex;gap:24px;align-items:center">
      <div class="gdpr-badge"><div class="gdpr-dot"></div> GDPR Compliant</div>
      <div class="gdpr-badge"><div class="gdpr-dot"></div> EU Data Storage</div>
      <div class="gdpr-badge"><div class="gdpr-dot"></div> Stripe Secured</div>
    </div>
  </div>
</footer>

<style>
  @keyframes progress-bar { from{width:0} to{width:100%} }
  .form-submit:disabled { opacity:0.7; cursor:not-allowed; transform:none !important; box-shadow:none !important; }
  .spinner { display:inline-block; width:16px; height:16px; border:2px solid rgba(255,255,255,0.35); border-top-color:#fff; border-radius:50%; animation:spin .7s linear infinite; vertical-align:middle; margin-right:8px; }
  @keyframes spin { to { transform:rotate(360deg); } }
</style>

<script>
(function(){

  /* ─────────────────────────────────────────
     CONFIG
     IMPORTANT: Replace PASTE_YOUR_SUPABASE_ANON_KEY_HERE with your real
     anon key from: Supabase dashboard → Project Settings → API → anon/public
  ───────────────────────────────────────── */
  var SB_URL  = 'https://ryipaehetvckxxqgbbhq.supabase.co';
  var SB_KEY  = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InJ5aXBhZWhldHZja3h4cWdiYmhxIiwicm9sZSI6ImFub24iLCJpYXQiOjE3NzQ5NjY1MzgsImV4cCI6MjA5MDU0MjUzOH0.ye2cNenS2jgCUUFDYF-VF-CD7cZ-RekeaxEjGAg28Ao';
  var STRIPE  = 'https://buy.stripe.com/cNi7sLetIciGfAr2i008g01';

  /* ─────────────────────────────────────────
     FORM SUBMIT → save to Supabase → Stripe
  ───────────────────────────────────────── */
  window.handleFormSubmit = async function(e) {
    if (e) e.preventDefault();

    var restaurant = (document.getElementById('f-restaurant').value || '').trim();
    var name       = (document.getElementById('f-name').value || '').trim();
    var email      = (document.getElementById('f-email').value || '').trim();
    var phone      = (document.getElementById('f-phone').value || '').trim();
    var locations  = document.getElementById('f-locations').value || '';
    var errBox     = document.getElementById('form-error');
    var btn        = document.getElementById('form-btn');

    errBox.style.display = 'none';

    /* Validation */
    if (!restaurant){ showErr('Please enter your Restaurant Name.'); return; }
    if (!name)       { showErr('Please enter your Name.'); return; }
    if (!email || !email.includes('@')){ showErr('Please enter a valid Email Address.'); return; }

    /* Loading */
    btn.disabled = true;
    btn.innerHTML = '<span class="spinner"></span> Saving your details…';

    try {
      var res = await fetch(SB_URL + '/rest/v1/demo_leads', {
        method: 'POST',
        headers: {
          'Content-Type':  'application/json',
          'apikey':        SB_KEY,
          'Authorization': 'Bearer ' + SB_KEY,
          'Prefer':        'return=minimal'
        },
        body: JSON.stringify({
          restaurant_name: restaurant,
          contact_name:    name,
          email:           email,
          phone:           phone   || null,
          locations:       locations || null,
          source:          'landing_page',
          created_at:      new Date().toISOString()
        })
      });

      if (!res.ok) {
        var txt = await res.text();
        throw new Error(txt || 'HTTP ' + res.status);
      }

      /* ✅ Success */
      document.getElementById('contact-form').style.display = 'none';
      document.getElementById('form-success').style.display = 'block';
      setTimeout(function(){ window.location.href = STRIPE; }, 2000);

    } catch(err) {
      console.error('Submit error:', err);
      btn.disabled = false;
      btn.innerHTML = 'Book My Free Demo →';
      showErr('Something went wrong. Please try again or email hello@resoassit.com');
    }

    function showErr(msg){
      errBox.textContent = '⚠️ ' + msg;
      errBox.style.display = 'block';
      errBox.scrollIntoView({ behavior:'smooth', block:'center' });
    }
  };

  /* ─────────────────────────────────────────
     SCROLL ANIMATIONS
  ───────────────────────────────────────── */
  var io = new IntersectionObserver(function(entries){
    entries.forEach(function(e){ if(e.isIntersecting) e.target.classList.add('visible'); });
  }, { threshold: 0.08 });
  document.querySelectorAll('.fade-up').forEach(function(el){ io.observe(el); });

  window.addEventListener('scroll', function(){
    document.querySelector('nav').style.boxShadow =
      window.scrollY > 40 ? '0 2px 30px rgba(26,18,8,0.08)' : 'none';
  });

})();
</script>
</body>
</html>
