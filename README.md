<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Amit Manmode — Full Stack Developer</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;700;800&family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;1,9..40,300&display=swap" rel="stylesheet" />
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #0a0a0f;
    --bg2: #111118;
    --bg3: #16161f;
    --border: rgba(255,255,255,0.07);
    --border-bright: rgba(255,255,255,0.14);
    --accent: #7c6af7;
    --accent2: #4fc3f7;
    --accent3: #f7c948;
    --accent4: #f76c6c;
    --green: #5af778;
    --text: #e8e8f0;
    --muted: #888899;
    --dimmer: #555566;
    --card: #13131a;
    --card2: #1a1a24;
    --mono: 'Space Mono', monospace;
    --display: 'Syne', sans-serif;
    --body: 'DM Sans', sans-serif;
    --glow: 0 0 40px rgba(124,106,247,0.15);
    --glow2: 0 0 20px rgba(79,195,247,0.12);
  }

  html { scroll-behavior: smooth; }
  body {
    font-family: var(--body);
    background: var(--bg);
    color: var(--text);
    line-height: 1.6;
    min-height: 100vh;
    overflow-x: hidden;
    font-size: 15px;
  }

  /* ---- GRID NOISE BG ---- */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image:
      linear-gradient(rgba(124,106,247,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(124,106,247,0.03) 1px, transparent 1px);
    background-size: 48px 48px;
    pointer-events: none;
    z-index: 0;
  }

  .wrap { max-width: 900px; margin: 0 auto; padding: 0 2rem; position: relative; z-index: 1; }

  /* ---- HERO ---- */
  .hero {
    padding: 5rem 0 3rem;
    position: relative;
  }
  .hero-badge {
    display: inline-flex; align-items: center; gap: 8px;
    font-family: var(--mono); font-size: 11px; letter-spacing: 0.1em;
    color: var(--accent); border: 1px solid rgba(124,106,247,0.3);
    padding: 5px 14px; border-radius: 100px;
    background: rgba(124,106,247,0.08);
    margin-bottom: 2rem;
    animation: fadein 0.6s ease both;
  }
  .hero-badge .dot {
    width: 6px; height: 6px; border-radius: 50%; background: var(--green);
    animation: pulse 2s infinite;
  }
  @keyframes pulse { 0%,100%{opacity:1;transform:scale(1)} 50%{opacity:.4;transform:scale(0.7)} }
  @keyframes fadein { from{opacity:0;transform:translateY(16px)} to{opacity:1;transform:translateY(0)} }
  @keyframes fadein2 { from{opacity:0;transform:translateY(20px)} to{opacity:1;transform:translateY(0)} }
  @keyframes slide-right { from{opacity:0;transform:translateX(-20px)} to{opacity:1;transform:translateX(0)} }

  .hero-name {
    font-family: var(--display);
    font-size: clamp(3.5rem, 9vw, 6.5rem);
    font-weight: 800;
    line-height: 1;
    letter-spacing: -0.03em;
    background: linear-gradient(135deg, #fff 30%, var(--accent) 70%, var(--accent2) 100%);
    -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
    margin-bottom: 1rem;
    animation: fadein 0.7s 0.1s ease both;
  }
  .hero-title {
    font-family: var(--mono); font-size: 13px; letter-spacing: 0.12em;
    color: var(--accent2); text-transform: uppercase;
    margin-bottom: 1.8rem;
    animation: fadein 0.7s 0.2s ease both;
  }
  .hero-desc {
    font-size: 17px; font-weight: 300; color: var(--muted);
    max-width: 560px; line-height: 1.75;
    animation: fadein 0.7s 0.3s ease both;
  }
  .hero-desc strong { color: var(--text); font-weight: 500; }

  .hero-actions {
    display: flex; align-items: center; gap: 12px; flex-wrap: wrap;
    margin-top: 2.5rem;
    animation: fadein 0.7s 0.4s ease both;
  }
  .btn {
    display: inline-flex; align-items: center; gap: 8px;
    padding: 11px 22px; border-radius: 8px;
    font-family: var(--mono); font-size: 12px; font-weight: 700; letter-spacing: 0.06em;
    cursor: pointer; text-decoration: none; transition: all 0.2s;
    border: 1px solid transparent;
  }
  .btn-primary {
    background: var(--accent); color: #fff;
    box-shadow: 0 0 24px rgba(124,106,247,0.4);
  }
  .btn-primary:hover { background: #9580ff; box-shadow: 0 0 36px rgba(124,106,247,0.6); transform: translateY(-2px); }
  .btn-outline {
    border-color: var(--border-bright); color: var(--text);
    background: rgba(255,255,255,0.03);
  }
  .btn-outline:hover { border-color: var(--accent); color: var(--accent); background: rgba(124,106,247,0.07); transform: translateY(-2px); }

  .hero-line {
    width: 100%; height: 1px;
    background: linear-gradient(90deg, transparent, var(--accent), var(--accent2), transparent);
    margin: 4rem 0 3rem; opacity: 0.25;
  }

  /* ---- SECTION LABEL ---- */
  .section-label {
    font-family: var(--mono); font-size: 11px; letter-spacing: 0.15em;
    color: var(--dimmer); text-transform: uppercase;
    display: flex; align-items: center; gap: 12px;
    margin-bottom: 2rem;
  }
  .section-label::before {
    content: ''; display: block; width: 24px; height: 1px; background: var(--accent); opacity: 0.6;
  }

  .section-title {
    font-family: var(--display); font-size: clamp(1.8rem, 4vw, 2.6rem);
    font-weight: 800; letter-spacing: -0.02em; margin-bottom: 0.5rem;
  }

  section { padding: 4rem 0; }

  /* ---- ABOUT CARD ---- */
  .about-grid {
    display: grid; grid-template-columns: 1fr 1fr; gap: 16px;
    margin-top: 2rem;
  }
  @media(max-width:600px){ .about-grid{grid-template-columns:1fr;} }
  .info-card {
    background: var(--card); border: 1px solid var(--border);
    border-radius: 12px; padding: 1.25rem 1.5rem;
    display: flex; align-items: flex-start; gap: 14px;
    transition: border-color 0.2s, transform 0.2s;
  }
  .info-card:hover { border-color: var(--border-bright); transform: translateY(-2px); }
  .info-icon {
    width: 36px; height: 36px; border-radius: 8px; flex-shrink: 0;
    display: flex; align-items: center; justify-content: center; font-size: 16px;
  }
  .info-icon.purple { background: rgba(124,106,247,0.15); color: var(--accent); }
  .info-icon.blue { background: rgba(79,195,247,0.12); color: var(--accent2); }
  .info-icon.yellow { background: rgba(247,201,72,0.12); color: var(--accent3); }
  .info-icon.red { background: rgba(247,108,108,0.12); color: var(--accent4); }
  .info-icon.green { background: rgba(90,247,120,0.1); color: var(--green); }
  .info-label { font-family: var(--mono); font-size: 10px; color: var(--dimmer); letter-spacing: 0.1em; margin-bottom: 3px; }
  .info-val { font-size: 14px; color: var(--text); font-weight: 400; }

  /* ---- TECH STACK ---- */
  .stack-categories { display: flex; flex-direction: column; gap: 2.5rem; margin-top: 1.5rem; }
  .stack-category-label {
    font-family: var(--mono); font-size: 10px; letter-spacing: 0.14em;
    color: var(--dimmer); text-transform: uppercase; margin-bottom: 1rem;
    display: flex; align-items: center; gap: 8px;
  }
  .stack-category-label::after { content:''; flex:1; height:1px; background:var(--border); }
  .tech-pills { display: flex; flex-wrap: wrap; gap: 8px; }
  .pill {
    display: inline-flex; align-items: center; gap: 7px;
    padding: 7px 14px; border-radius: 8px;
    border: 1px solid var(--border); background: var(--card);
    font-size: 12.5px; font-family: var(--body); font-weight: 400; color: var(--text);
    transition: all 0.2s; cursor: default; letter-spacing: 0.01em;
  }
  .pill:hover { border-color: var(--border-bright); background: var(--card2); transform: translateY(-2px); }
  .pill .dot { width: 7px; height: 7px; border-radius: 50%; flex-shrink:0; }
  .dot-purple{background:var(--accent);}
  .dot-blue{background:var(--accent2);}
  .dot-yellow{background:var(--accent3);}
  .dot-green{background:var(--green);}
  .dot-red{background:var(--accent4);}
  .dot-white{background:#ccc;}

  /* ---- FEATURED PROJECTS ---- */
  .projects-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; margin-top: 1.5rem; }
  @media(max-width:600px){.projects-grid{grid-template-columns:1fr;}}
  .project-card {
    background: var(--card); border: 1px solid var(--border);
    border-radius: 16px; padding: 1.75rem;
    transition: all 0.25s; position: relative; overflow: hidden;
    text-decoration: none; display: flex; flex-direction: column;
  }
  .project-card::before {
    content: ''; position: absolute; inset: 0;
    background: radial-gradient(ellipse at top left, rgba(124,106,247,0.06) 0%, transparent 60%);
    pointer-events: none;
  }
  .project-card.blue-tint::before { background: radial-gradient(ellipse at top left, rgba(79,195,247,0.07) 0%, transparent 60%); }
  .project-card:hover { border-color: var(--accent); transform: translateY(-4px); box-shadow: var(--glow); }
  .project-card.blue-tint:hover { border-color: var(--accent2); box-shadow: var(--glow2); }
  .project-tag {
    display: inline-flex; align-items: center; gap: 5px;
    font-family: var(--mono); font-size: 10px; letter-spacing: 0.1em;
    padding: 4px 10px; border-radius: 100px; margin-bottom: 1rem; width: fit-content;
  }
  .tag-purple { background: rgba(124,106,247,0.15); color: var(--accent); border: 1px solid rgba(124,106,247,0.25); }
  .tag-blue { background: rgba(79,195,247,0.1); color: var(--accent2); border: 1px solid rgba(79,195,247,0.2); }
  .project-name {
    font-family: var(--display); font-size: 1.3rem; font-weight: 700;
    color: var(--text); margin-bottom: 0.6rem; letter-spacing: -0.01em;
  }
  .project-desc { font-size: 13.5px; color: var(--muted); line-height: 1.6; flex: 1; }
  .project-techs { display: flex; flex-wrap: wrap; gap: 6px; margin-top: 1.5rem; }
  .mini-pill {
    font-family: var(--mono); font-size: 10px; padding: 3px 9px;
    border-radius: 4px; background: rgba(255,255,255,0.05); color: var(--muted);
    border: 1px solid var(--border);
  }
  .project-link-row { display: flex; align-items: center; gap: 8px; margin-top: 1.2rem; }
  .project-link {
    font-family: var(--mono); font-size: 10px; letter-spacing: 0.08em; color: var(--accent2);
    text-decoration: none; display: flex; align-items: center; gap: 4px;
    opacity: 0.8; transition: opacity 0.2s;
  }
  .project-link:hover { opacity: 1; }

  /* ---- GOALS ---- */
  .goals-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; margin-top: 1.5rem; }
  @media(max-width:600px){.goals-grid{grid-template-columns:1fr;}}
  .goal-item {
    display: flex; align-items: center; gap: 12px;
    padding: 1rem 1.25rem; border-radius: 10px;
    border: 1px solid var(--border); background: var(--card);
    font-size: 14px; color: var(--muted);
    transition: all 0.2s;
  }
  .goal-item:hover { border-color: var(--border-bright); color: var(--text); }
  .goal-status {
    width: 22px; height: 22px; border-radius: 50%; flex-shrink: 0;
    display: flex; align-items: center; justify-content: center; font-size: 11px;
  }
  .done { background: rgba(90,247,120,0.15); color: var(--green); border: 1px solid rgba(90,247,120,0.3); }
  .wip { background: rgba(247,201,72,0.12); color: var(--accent3); border: 1px solid rgba(247,201,72,0.3); }

  /* ---- CONNECT ---- */
  .connect-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(160px, 1fr)); gap: 12px; margin-top: 1.5rem; }
  .social-card {
    display: flex; align-items: center; gap: 12px;
    padding: 1rem 1.25rem; border-radius: 10px;
    background: var(--card); border: 1px solid var(--border);
    text-decoration: none; transition: all 0.2s;
  }
  .social-card:hover { transform: translateY(-3px); }
  .social-card.lk:hover { border-color: #0077b5; box-shadow: 0 0 20px rgba(0,119,181,0.2); }
  .social-card.gh:hover { border-color: #f0f6ff; box-shadow: 0 0 20px rgba(240,246,255,0.1); }
  .social-card.ig:hover { border-color: #e4405f; box-shadow: 0 0 20px rgba(228,64,95,0.2); }
  .social-card.em:hover { border-color: #ea4335; box-shadow: 0 0 20px rgba(234,67,53,0.2); }
  .social-card.lc:hover { border-color: #ffa116; box-shadow: 0 0 20px rgba(255,161,22,0.2); }
  .social-card.pt:hover { border-color: var(--accent); box-shadow: var(--glow); }
  .social-icon {
    width: 36px; height: 36px; border-radius: 8px; flex-shrink: 0;
    display: flex; align-items: center; justify-content: center;
    font-size: 17px; font-weight: 700;
  }
  .social-name { font-size: 13px; font-weight: 500; color: var(--text); }
  .social-handle { font-family: var(--mono); font-size: 10px; color: var(--dimmer); }

  /* ---- CODE BLOCK ---- */
  .code-box {
    background: #0d0d14; border: 1px solid var(--border);
    border-radius: 12px; overflow: hidden; margin-top: 1.5rem;
  }
  .code-bar {
    display: flex; align-items: center; gap: 8px;
    padding: 10px 16px; border-bottom: 1px solid var(--border);
    background: rgba(255,255,255,0.02);
  }
  .code-dot { width: 10px; height: 10px; border-radius: 50%; }
  .cd1{background:#ff5f57;} .cd2{background:#ffbd2e;} .cd3{background:#28ca41;}
  .code-filename { font-family: var(--mono); font-size: 11px; color: var(--dimmer); margin-left: 6px; }
  .code-inner { padding: 1.5rem 1.75rem; font-family: var(--mono); font-size: 13px; line-height: 2; overflow-x: auto; }
  .kw{color:#c792ea;} .str{color:#c3e88d;} .fn{color:#82aaff;} .prop{color:#f78c6c;} .cmt{color:#546e7a;font-style:italic;} .sym{color:#89ddff;} .num{color:#f78c6c;}
  .val{color:var(--accent2);}

  /* ---- QUOTE ---- */
  .quote-box {
    margin: 4rem 0 0;
    padding: 2rem 2.5rem;
    border-left: 3px solid var(--accent);
    background: linear-gradient(90deg, rgba(124,106,247,0.06) 0%, transparent 100%);
    border-radius: 0 12px 12px 0;
  }
  .quote-text { font-family: var(--display); font-size: 1.3rem; font-weight: 600; line-height: 1.5; color: var(--text); margin-bottom: 0.6rem; }
  .quote-attr { font-family: var(--mono); font-size: 11px; color: var(--dimmer); }

  /* ---- FOOTER ---- */
  footer {
    padding: 3rem 0 4rem; text-align: center;
    border-top: 1px solid var(--border);
    margin-top: 4rem;
  }
  .footer-name { font-family: var(--display); font-size: 1.4rem; font-weight: 800; letter-spacing: -0.02em; margin-bottom: 0.4rem; }
  .footer-sub { font-family: var(--mono); font-size: 11px; color: var(--dimmer); letter-spacing: 0.1em; }
  .footer-heart { color: var(--accent4); }

  /* ---- STATS ROW ---- */
  .stats-row {
    display: grid; grid-template-columns: repeat(3, 1fr); gap: 12px;
    margin-top: 1.5rem;
  }
  @media(max-width:500px){.stats-row{grid-template-columns:1fr;}}
  .stat-card {
    background: var(--card); border: 1px solid var(--border);
    border-radius: 12px; padding: 1.5rem 1.25rem; text-align: center;
    transition: all 0.2s;
  }
  .stat-card:hover { border-color: var(--border-bright); transform: translateY(-2px); }
  .stat-num {
    font-family: var(--display); font-size: 2.4rem; font-weight: 800;
    letter-spacing: -0.03em; line-height: 1;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
    margin-bottom: 4px;
  }
  .stat-label { font-family: var(--mono); font-size: 10px; letter-spacing: 0.1em; color: var(--dimmer); }

  /* ---- CURRENTLY LEARNING ---- */
  .learning-row { display: flex; flex-wrap: wrap; gap: 10px; margin-top: 1.5rem; }
  .learn-chip {
    display: flex; align-items: center; gap: 8px;
    padding: 8px 16px; border-radius: 100px;
    background: var(--card2); border: 1px solid var(--border);
    font-size: 13px; color: var(--text); transition: all 0.2s;
  }
  .learn-chip:hover { border-color: var(--accent); }
  .learn-chip .bar {
    width: 50px; height: 3px; border-radius: 100px; background: var(--border);
    position: relative; overflow: hidden;
  }
  .learn-chip .fill { height: 100%; border-radius: 100px; background: linear-gradient(90deg, var(--accent), var(--accent2)); }

  /* ---- SCROLLBAR ---- */
  ::-webkit-scrollbar{width:6px;height:6px;}
  ::-webkit-scrollbar-track{background:var(--bg2);}
  ::-webkit-scrollbar-thumb{background:var(--border-bright);border-radius:3px;}

  /* ---- ANIMATED BORDER ---- */
  @keyframes border-glow {
    0%,100%{box-shadow:0 0 0 0 rgba(124,106,247,0)}
    50%{box-shadow:0 0 20px 2px rgba(124,106,247,0.25)}
  }

  /* ---- SELECTION ---- */
  ::selection{background:rgba(124,106,247,0.3);}
</style>
</head>
<body>

<div class="wrap">

  <!-- HERO -->
  <section class="hero">
    <div class="hero-badge">
      <span class="dot"></span>
      AVAILABLE FOR OPPORTUNITIES
    </div>
    <h1 class="hero-name">Amit<br/>Manmode</h1>
    <p class="hero-title">Full Stack Developer &nbsp;/&nbsp; MERN Stack &nbsp;/&nbsp; Problem Solver</p>
    <p class="hero-desc">
      Building <strong>fast, scalable web applications</strong> from India 🇮🇳 — obsessed with clean code, great UX, and turning caffeine into ☕ deployable software.
    </p>
    <div class="hero-actions">
      <a class="btn btn-primary" href="https://amit-akm-22.github.io/Portfolio-Page/" target="_blank">View Portfolio ↗</a>
      <a class="btn btn-outline" href="mailto:amit.akm.18@gmail.com">Say Hello</a>
      <a class="btn btn-outline" href="https://github.com/Amit-akm-22" target="_blank">GitHub</a>
    </div>
  </section>

  <div class="hero-line"></div>

  <!-- STATS -->
  <section>
    <div class="section-label">AT A GLANCE</div>
    <div class="stats-row">
      <div class="stat-card">
        <div class="stat-num">10+</div>
        <div class="stat-label">PROJECTS BUILT</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">5+</div>
        <div class="stat-label">TECH STACKS</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">2026</div>
        <div class="stat-label">GRADUATING B.TECH</div>
      </div>
    </div>
  </section>

  <!-- ABOUT -->
  <section>
    <div class="section-label">ABOUT ME</div>
    <h2 class="section-title">Who I Am</h2>
    <p style="color:var(--muted);font-size:15px;max-width:620px;line-height:1.8;margin-bottom:0;">
      A full-stack developer pursuing B.Tech in Computer Science, currently deepening my expertise in Machine Learning and Data Structures. I love building products that are as performant as they are beautiful — from REST APIs to real-time apps with Socket.io.
    </p>
    <div class="about-grid">
      <div class="info-card">
        <div class="info-icon purple">🎓</div>
        <div>
          <div class="info-label">EDUCATION</div>
          <div class="info-val">B.Tech, Computer Science</div>
        </div>
      </div>
      <div class="info-card">
        <div class="info-icon blue">📍</div>
        <div>
          <div class="info-label">LOCATION</div>
          <div class="info-val">India 🇮🇳</div>
        </div>
      </div>
      <div class="info-card">
        <div class="info-icon yellow">💼</div>
        <div>
          <div class="info-label">FOCUS</div>
          <div class="info-val">MERN Stack · System Design · DSA</div>
        </div>
      </div>
      <div class="info-card">
        <div class="info-icon green">🌱</div>
        <div>
          <div class="info-label">EXPLORING</div>
          <div class="info-val">Machine Learning · Next.js · Google Auth</div>
        </div>
      </div>
      <div class="info-card">
        <div class="info-icon red">⚡</div>
        <div>
          <div class="info-label">FUN FACT</div>
          <div class="info-val">I debug with console.log() and I'm not ashamed 😄</div>
        </div>
      </div>
      <div class="info-card">
        <div class="info-icon blue">🚀</div>
        <div>
          <div class="info-label">GOAL 2026</div>
          <div class="info-val">Land a Software Developer Role</div>
        </div>
      </div>
    </div>
  </section>

  <!-- CURRENTLY LEARNING -->
  <section>
    <div class="section-label">IN PROGRESS</div>
    <h2 class="section-title">Currently Learning</h2>
    <div class="learning-row">
      <div class="learn-chip">Machine Learning <div class="bar"><div class="fill" style="width:55%"></div></div></div>
      <div class="learn-chip">Data Structures <div class="bar"><div class="fill" style="width:75%"></div></div></div>
      <div class="learn-chip">Next.js <div class="bar"><div class="fill" style="width:40%"></div></div></div>
      <div class="learn-chip">Docker <div class="bar"><div class="fill" style="width:25%"></div></div></div>
      <div class="learn-chip">AWS <div class="bar"><div class="fill" style="width:20%"></div></div></div>
      <div class="learn-chip">TypeScript <div class="bar"><div class="fill" style="width:60%"></div></div></div>
    </div>
  </section>

  <!-- TECH STACK -->
  <section>
    <div class="section-label">SKILLS</div>
    <h2 class="section-title">Tech Stack</h2>
    <div class="stack-categories">
      <div>
        <div class="stack-category-label">Frontend</div>
        <div class="tech-pills">
          <span class="pill"><span class="dot dot-red"></span>HTML5</span>
          <span class="pill"><span class="dot dot-blue"></span>CSS3</span>
          <span class="pill"><span class="dot dot-yellow"></span>JavaScript</span>
          <span class="pill"><span class="dot dot-blue"></span>TypeScript</span>
          <span class="pill"><span class="dot dot-blue"></span>React.js</span>
          <span class="pill"><span class="dot dot-purple"></span>Redux</span>
          <span class="pill"><span class="dot dot-blue"></span>Tailwind CSS</span>
          <span class="pill"><span class="dot dot-purple"></span>Bootstrap</span>
          <span class="pill"><span class="dot dot-purple"></span>Vite</span>
        </div>
      </div>
      <div>
        <div class="stack-category-label">Backend</div>
        <div class="tech-pills">
          <span class="pill"><span class="dot dot-green"></span>Node.js</span>
          <span class="pill"><span class="dot dot-white"></span>Express.js</span>
          <span class="pill"><span class="dot dot-green"></span>MongoDB</span>
          <span class="pill"><span class="dot dot-blue"></span>MySQL</span>
          <span class="pill"><span class="dot dot-white"></span>Socket.io</span>
          <span class="pill"><span class="dot dot-red"></span>REST APIs</span>
          <span class="pill"><span class="dot dot-yellow"></span>JWT Auth</span>
        </div>
      </div>
      <div>
        <div class="stack-category-label">Languages</div>
        <div class="tech-pills">
          <span class="pill"><span class="dot dot-yellow"></span>JavaScript</span>
          <span class="pill"><span class="dot dot-blue"></span>TypeScript</span>
          <span class="pill"><span class="dot dot-blue"></span>Python</span>
          <span class="pill"><span class="dot dot-blue"></span>C / C++</span>
        </div>
      </div>
      <div>
        <div class="stack-category-label">Tools & DevOps</div>
        <div class="tech-pills">
          <span class="pill"><span class="dot dot-red"></span>Git</span>
          <span class="pill"><span class="dot dot-white"></span>GitHub</span>
          <span class="pill"><span class="dot dot-blue"></span>VS Code</span>
          <span class="pill"><span class="dot dot-red"></span>Postman</span>
          <span class="pill"><span class="dot dot-white"></span>npm</span>
          <span class="pill"><span class="dot dot-white"></span>Vercel</span>
          <span class="pill"><span class="dot dot-blue"></span>Docker (learning)</span>
          <span class="pill"><span class="dot dot-yellow"></span>AWS (learning)</span>
        </div>
      </div>
    </div>
  </section>

  <!-- PROJECTS -->
  <section>
    <div class="section-label">WORK</div>
    <h2 class="section-title">Featured Projects</h2>
    <div class="projects-grid">
      <a class="project-card" href="https://github.com/Amit-akm-22/LinkedIn" target="_blank">
        <div class="project-tag tag-purple">★ FEATURED</div>
        <div class="project-name">LinkedIn Clone</div>
        <div class="project-desc">
          A full-featured professional networking platform replica — complete with authentication, real-time notifications, post feed, connections, and messaging built with the MERN stack.
        </div>
        <div class="project-techs">
          <span class="mini-pill">React</span>
          <span class="mini-pill">Node.js</span>
          <span class="mini-pill">MongoDB</span>
          <span class="mini-pill">Express</span>
          <span class="mini-pill">Socket.io</span>
          <span class="mini-pill">Tailwind</span>
        </div>
        <div class="project-link-row">
          <span class="project-link">View on GitHub ↗</span>
        </div>
      </a>

      <a class="project-card blue-tint" href="https://github.com/Amit-akm-22/WonderLust-akm-18" target="_blank">
        <div class="project-tag tag-blue">FULL STACK</div>
        <div class="project-name">WonderLust</div>
        <div class="project-desc">
          A travel-focused listing platform where users can discover, review, and list unique stays across beautiful locations — featuring maps, image uploads, and user reviews.
        </div>
        <div class="project-techs">
          <span class="mini-pill">Node.js</span>
          <span class="mini-pill">Express</span>
          <span class="mini-pill">MongoDB</span>
          <span class="mini-pill">EJS</span>
          <span class="mini-pill">Cloudinary</span>
          <span class="mini-pill">Mapbox</span>
        </div>
        <div class="project-link-row">
          <span class="project-link">View on GitHub ↗</span>
        </div>
      </a>
    </div>
  </section>

  <!-- CODE SNAPSHOT -->
  <section>
    <div class="section-label">IDENTITY</div>
    <h2 class="section-title">In Code</h2>
    <div class="code-box">
      <div class="code-bar">
        <div class="code-dot cd1"></div>
        <div class="code-dot cd2"></div>
        <div class="code-dot cd3"></div>
        <span class="code-filename">amit.js</span>
      </div>
      <div class="code-inner">
<span class="kw">const</span> <span class="fn">amit</span> <span class="sym">=</span> <span class="sym">{</span><br/>
&nbsp;&nbsp;<span class="prop">role</span><span class="sym">:</span>      <span class="str">"Full Stack Developer"</span><span class="sym">,</span><br/>
&nbsp;&nbsp;<span class="prop">location</span><span class="sym">:</span> <span class="str">"India 🇮🇳"</span><span class="sym">,</span><br/>
&nbsp;&nbsp;<span class="prop">education</span><span class="sym">:</span><span class="str">"B.Tech in Computer Science"</span><span class="sym">,</span><br/>
&nbsp;&nbsp;<span class="prop">focus</span><span class="sym">:</span>    <span class="sym">[</span><span class="str">"MERN Stack"</span><span class="sym">,</span> <span class="str">"System Design"</span><span class="sym">,</span> <span class="str">"DSA"</span><span class="sym">],</span><br/>
&nbsp;&nbsp;<span class="prop">expertise</span><span class="sym">:</span> <span class="sym">{</span><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="prop">frontend</span><span class="sym">:</span> <span class="sym">[</span><span class="str">"React"</span><span class="sym">,</span> <span class="str">"JavaScript"</span><span class="sym">,</span> <span class="str">"Tailwind"</span><span class="sym">],</span><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="prop">backend</span><span class="sym">:</span>  <span class="sym">[</span><span class="str">"Node.js"</span><span class="sym">,</span> <span class="str">"Express"</span><span class="sym">,</span> <span class="str">"MongoDB"</span><span class="sym">],</span><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="prop">tools</span><span class="sym">:</span>    <span class="sym">[</span><span class="str">"Git"</span><span class="sym">,</span> <span class="str">"GitHub"</span><span class="sym">,</span> <span class="str">"VS Code"</span><span class="sym">,</span> <span class="str">"Postman"</span><span class="sym">],</span><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="prop">learning</span><span class="sym">:</span> <span class="sym">[</span><span class="str">"Docker"</span><span class="sym">,</span> <span class="str">"AWS"</span><span class="sym">,</span> <span class="str">"Machine Learning"</span><span class="sym">],</span><br/>
&nbsp;&nbsp;<span class="sym">},</span><br/>
&nbsp;&nbsp;<span class="prop">funFact</span><span class="sym">:</span>  <span class="str">"I turn coffee into code! ☕"</span><span class="sym">,</span><br/>
<span class="sym">};</span><br/><br/>
<span class="cmt">// Always looking for new challenges 🚀</span>
      </div>
    </div>
  </section>

  <!-- GOALS -->
  <section>
    <div class="section-label">ROADMAP</div>
    <h2 class="section-title">2026 Goals</h2>
    <div class="goals-grid">
      <div class="goal-item"><div class="goal-status done">✓</div>Master MERN Stack Development</div>
      <div class="goal-item"><div class="goal-status wip">→</div>Contribute to 5+ Open Source Projects</div>
      <div class="goal-item"><div class="goal-status wip">→</div>Learn Machine Learning & Data Structures</div>
      <div class="goal-item"><div class="goal-status wip">→</div>Build & Deploy 10+ Full-Stack Projects</div>
      <div class="goal-item"><div class="goal-status wip">→</div>Land a Software Developer Role</div>
      <div class="goal-item"><div class="goal-status wip">→</div>Explore Docker, AWS & Microservices</div>
    </div>
  </section>

  <!-- CONNECT -->
  <section>
    <div class="section-label">LET'S TALK</div>
    <h2 class="section-title">Connect</h2>
    <div class="connect-grid">
      <a class="social-card lk" href="https://linkedin.com/in/amit-manmode" target="_blank">
        <div class="social-icon" style="background:rgba(0,119,181,0.15);color:#4fc3f7;">in</div>
        <div><div class="social-name">LinkedIn</div><div class="social-handle">/amit-manmode</div></div>
      </a>
      <a class="social-card gh" href="https://github.com/Amit-akm-22" target="_blank">
        <div class="social-icon" style="background:rgba(255,255,255,0.07);color:#f0f6ff;font-size:14px;">GH</div>
        <div><div class="social-name">GitHub</div><div class="social-handle">Amit-akm-22</div></div>
      </a>
      <a class="social-card ig" href="https://instagram.com/_amit__21" target="_blank">
        <div class="social-icon" style="background:rgba(228,64,95,0.15);color:#f76c6c;">📸</div>
        <div><div class="social-name">Instagram</div><div class="social-handle">_amit__21</div></div>
      </a>
      <a class="social-card em" href="mailto:amit.akm.18@gmail.com">
        <div class="social-icon" style="background:rgba(234,67,53,0.15);color:#f76c6c;">✉</div>
        <div><div class="social-name">Email</div><div class="social-handle">amit.akm.18@gmail.com</div></div>
      </a>
      <a class="social-card lc" href="https://leetcode.com/amit2156akm" target="_blank">
        <div class="social-icon" style="background:rgba(255,161,22,0.15);color:#f7c948;font-size:13px;">LC</div>
        <div><div class="social-name">LeetCode</div><div class="social-handle">amit2156akm</div></div>
      </a>
      <a class="social-card pt" href="https://amit-akm-22.github.io/Portfolio-Page/" target="_blank">
        <div class="social-icon" style="background:rgba(124,106,247,0.15);color:var(--accent);">🌐</div>
        <div><div class="social-name">Portfolio</div><div class="social-handle">View My Work</div></div>
      </a>
    </div>
  </section>

  <!-- QUOTE -->
  <div class="quote-box">
    <div class="quote-text">"Any fool can write code that a computer can understand. Good programmers write code that humans can understand."</div>
    <div class="quote-attr">— Martin Fowler</div>
  </div>

  <!-- FOOTER -->
  <footer>
    <div class="footer-name">Amit Manmode</div>
    <div class="footer-sub" style="margin-top:6px;margin-bottom:16px;">FULL STACK DEVELOPER · INDIA</div>
    <div style="font-size:13px;color:var(--dimmer);">Made with <span class="footer-heart">♥</span> and a lot of ☕</div>
    <div style="margin-top:8px;font-family:var(--mono);font-size:10px;color:var(--dimmer);letter-spacing:0.08em;">⭐ STAR MY REPOSITORIES IF YOU FIND THEM USEFUL ⭐</div>
  </footer>

</div>
</body>
</html>
