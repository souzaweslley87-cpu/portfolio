<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Portfólio | Social Media & Marketing Digital</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:wght@300;400;500;600&family=Playfair+Display:ital,wght@0,700;1,400&display=swap" rel="stylesheet">
<style>
  :root {
    --black: #0a0a0a;
    --white: #f5f0e8;
    --accent: #e8c547;
    --accent2: #c94a2f;
    --gray: #1e1e1e;
    --gray2: #2e2e2e;
    --muted: #6b6b6b;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--black);
    color: var(--white);
    font-family: 'DM Sans', sans-serif;
    font-weight: 300;
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom cursor */
  .cursor {
    width: 12px; height: 12px;
    background: var(--accent);
    border-radius: 50%;
    position: fixed;
    top: 0; left: 0;
    pointer-events: none;
    z-index: 9999;
    transition: transform 0.15s ease;
    mix-blend-mode: difference;
  }
  .cursor-ring {
    width: 36px; height: 36px;
    border: 1px solid rgba(232,197,71,0.5);
    border-radius: 50%;
    position: fixed;
    top: 0; left: 0;
    pointer-events: none;
    z-index: 9998;
    transition: all 0.3s ease;
  }

  /* NAV */
  nav {
    position: fixed; top: 0; left: 0; right: 0;
    z-index: 100;
    display: flex; justify-content: space-between; align-items: center;
    padding: 1.5rem 4rem;
    background: linear-gradient(to bottom, rgba(10,10,10,0.95), transparent);
    backdrop-filter: blur(4px);
  }
  .nav-logo {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.6rem;
    letter-spacing: 4px;
    color: var(--accent);
  }
  .nav-links { display: flex; gap: 2.5rem; }
  .nav-links a {
    text-decoration: none; color: var(--white);
    font-size: 0.78rem; letter-spacing: 2px;
    text-transform: uppercase; opacity: 0.7;
    transition: opacity 0.2s;
  }
  .nav-links a:hover { opacity: 1; color: var(--accent); }

  /* HERO */
  .hero {
    min-height: 100vh;
    display: flex; align-items: center;
    padding: 0 4rem;
    position: relative;
    overflow: hidden;
  }
  .hero-bg {
    position: absolute; inset: 0;
    background:
      radial-gradient(ellipse 60% 70% at 80% 50%, rgba(232,197,71,0.06) 0%, transparent 60%),
      radial-gradient(ellipse 40% 50% at 20% 80%, rgba(201,74,47,0.08) 0%, transparent 50%);
  }
  .hero-lines {
    position: absolute; inset: 0;
    background-image:
      linear-gradient(rgba(255,255,255,0.02) 1px, transparent 1px),
      linear-gradient(90deg, rgba(255,255,255,0.02) 1px, transparent 1px);
    background-size: 60px 60px;
  }
  .hero-content { position: relative; z-index: 2; max-width: 900px; }
  .hero-eyebrow {
    font-size: 0.7rem; letter-spacing: 4px;
    text-transform: uppercase; color: var(--accent);
    margin-bottom: 1.5rem;
    display: flex; align-items: center; gap: 1rem;
    opacity: 0; animation: fadeUp 0.8s 0.2s forwards;
  }
  .hero-eyebrow::before {
    content: ''; width: 40px; height: 1px; background: var(--accent);
  }
  .hero-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(4rem, 10vw, 9rem);
    line-height: 0.9;
    letter-spacing: 2px;
    opacity: 0; animation: fadeUp 0.8s 0.4s forwards;
  }
  .hero-title em {
    font-family: 'Playfair Display', serif;
    font-style: italic;
    color: var(--accent);
    font-size: 0.85em;
  }
  .hero-sub {
    margin-top: 2.5rem;
    font-size: 1.05rem;
    line-height: 1.7;
    color: rgba(245,240,232,0.65);
    max-width: 520px;
    opacity: 0; animation: fadeUp 0.8s 0.6s forwards;
  }
  .hero-cta {
    margin-top: 3rem;
    display: flex; gap: 1.5rem; align-items: center;
    opacity: 0; animation: fadeUp 0.8s 0.8s forwards;
  }
  .btn-primary {
    background: var(--accent);
    color: var(--black);
    padding: 1rem 2.5rem;
    font-size: 0.8rem; letter-spacing: 2px;
    text-transform: uppercase; font-weight: 600;
    text-decoration: none;
    transition: all 0.3s;
    clip-path: polygon(0 0, calc(100% - 12px) 0, 100% 12px, 100% 100%, 12px 100%, 0 calc(100% - 12px));
  }
  .btn-primary:hover { background: var(--white); transform: translateY(-2px); }
  .btn-ghost {
    color: var(--white); text-decoration: none;
    font-size: 0.78rem; letter-spacing: 2px;
    text-transform: uppercase;
    display: flex; align-items: center; gap: 0.8rem;
    opacity: 0.7; transition: opacity 0.2s;
  }
  .btn-ghost:hover { opacity: 1; }
  .btn-ghost::after { content: '→'; font-size: 1rem; }
  .hero-stats {
    position: absolute; right: 4rem; bottom: 5rem;
    display: flex; flex-direction: column; gap: 2rem; z-index: 2;
    opacity: 0; animation: fadeLeft 0.8s 1s forwards;
  }
  .stat-item { text-align: right; }
  .stat-num {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 3rem; line-height: 1;
    color: var(--accent);
  }
  .stat-label {
    font-size: 0.65rem; letter-spacing: 2px;
    text-transform: uppercase; opacity: 0.5;
  }
  .stat-divider {
    width: 40px; height: 1px;
    background: rgba(255,255,255,0.15);
    margin-left: auto;
  }

  /* SECTION COMMON */
  section { padding: 7rem 4rem; }
  .section-tag {
    font-size: 0.65rem; letter-spacing: 4px;
    text-transform: uppercase; color: var(--accent);
    margin-bottom: 1rem;
    display: flex; align-items: center; gap: 1rem;
  }
  .section-tag::before { content: '//'; opacity: 0.5; }
  .section-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(2.5rem, 5vw, 4.5rem);
    line-height: 1;
    letter-spacing: 1px;
    margin-bottom: 1rem;
  }
  .section-title span { color: var(--accent); }

  /* ABOUT */
  .about { background: var(--gray); }
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 6rem; align-items: center;
    margin-top: 4rem;
  }
  .about-text p {
    font-size: 1.05rem; line-height: 1.8;
    color: rgba(245,240,232,0.7);
    margin-bottom: 1.5rem;
  }
  .about-text strong { color: var(--white); font-weight: 500; }
  .skills-grid {
    display: grid; grid-template-columns: 1fr 1fr;
    gap: 0.8rem;
  }
  .skill-tag {
    padding: 0.7rem 1rem;
    border: 1px solid rgba(255,255,255,0.08);
    font-size: 0.75rem; letter-spacing: 1px;
    text-transform: uppercase;
    transition: all 0.3s;
    position: relative; overflow: hidden;
  }
  .skill-tag::before {
    content: ''; position: absolute;
    left: 0; top: 0; bottom: 0; width: 3px;
    background: var(--accent);
  }
  .skill-tag:hover { border-color: var(--accent); background: rgba(232,197,71,0.05); }

  /* CASES */
  .cases { background: var(--black); }
  .cases-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(340px, 1fr));
    gap: 1.5px;
    margin-top: 4rem;
    background: rgba(255,255,255,0.05);
  }
  .case-card {
    background: var(--black);
    padding: 2.5rem;
    transition: all 0.4s;
    position: relative;
    overflow: hidden;
    cursor: none;
  }
  .case-card::before {
    content: ''; position: absolute;
    inset: 0; opacity: 0;
    background: linear-gradient(135deg, rgba(232,197,71,0.05), transparent);
    transition: opacity 0.4s;
  }
  .case-card:hover { transform: translateY(-4px); }
  .case-card:hover::before { opacity: 1; }
  .case-num {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 4rem; line-height: 1;
    color: rgba(255,255,255,0.04);
    position: absolute; top: 1.5rem; right: 2rem;
  }
  .case-badge {
    display: inline-block;
    padding: 0.3rem 0.8rem;
    font-size: 0.6rem; letter-spacing: 2px;
    text-transform: uppercase;
    border: 1px solid;
    margin-bottom: 1.5rem;
  }
  .badge-b2b { border-color: var(--accent); color: var(--accent); }
  .badge-b2c { border-color: #7bb3c4; color: #7bb3c4; }
  .badge-ecom { border-color: #a78bfa; color: #a78bfa; }
  .case-name {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.8rem; letter-spacing: 2px;
    margin-bottom: 0.5rem;
  }
  .case-role {
    font-size: 0.72rem; letter-spacing: 2px;
    text-transform: uppercase; color: var(--muted);
    margin-bottom: 1.5rem;
  }
  .case-desc {
    font-size: 0.9rem; line-height: 1.7;
    color: rgba(245,240,232,0.6);
    margin-bottom: 2rem;
  }
  .case-results {
    display: flex; flex-wrap: wrap; gap: 0.8rem;
  }
  .result-chip {
    background: rgba(255,255,255,0.04);
    border: 1px solid rgba(255,255,255,0.08);
    padding: 0.4rem 0.9rem;
    font-size: 0.72rem;
    border-radius: 2px;
    transition: border-color 0.2s;
  }
  .case-card:hover .result-chip { border-color: rgba(232,197,71,0.3); }

  /* FEATURED CASE - MOTOBEL */
  .featured-case {
    background: var(--gray);
    padding: 7rem 4rem;
  }
  .featured-inner {
    display: grid;
    grid-template-columns: 1fr 1.4fr;
    gap: 6rem; align-items: center;
    margin-top: 4rem;
  }
  .feat-label {
    font-size: 0.65rem; letter-spacing: 3px;
    text-transform: uppercase; color: var(--accent2);
    margin-bottom: 1rem;
  }
  .feat-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(3rem, 6vw, 5.5rem);
    line-height: 0.95; letter-spacing: 1px;
    margin-bottom: 2rem;
  }
  .feat-desc {
    font-size: 1rem; line-height: 1.8;
    color: rgba(245,240,232,0.65);
    margin-bottom: 2.5rem;
  }
  .metrics-grid {
    display: grid; grid-template-columns: repeat(3, 1fr);
    gap: 1px; background: rgba(255,255,255,0.06);
  }
  .metric {
    background: var(--gray);
    padding: 2rem 1.5rem;
    text-align: center;
  }
  .metric-val {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 3.2rem; line-height: 1;
    color: var(--accent);
  }
  .metric-unit {
    font-size: 1.2rem; color: var(--accent2);
  }
  .metric-lbl {
    font-size: 0.65rem; letter-spacing: 1.5px;
    text-transform: uppercase; opacity: 0.5;
    margin-top: 0.5rem;
    line-height: 1.4;
  }
  .feat-tags { display: flex; flex-wrap: wrap; gap: 0.8rem; }
  .feat-tag {
    padding: 0.5rem 1.2rem;
    background: rgba(232,197,71,0.08);
    border: 1px solid rgba(232,197,71,0.2);
    font-size: 0.72rem; letter-spacing: 1px;
    text-transform: uppercase;
  }

  /* SERVICES */
  .services { background: var(--black); }
  .services-list {
    margin-top: 4rem;
    display: flex; flex-direction: column;
  }
  .service-row {
    display: grid;
    grid-template-columns: 60px 1fr 1fr auto;
    align-items: center;
    gap: 2rem; padding: 2rem 0;
    border-bottom: 1px solid rgba(255,255,255,0.06);
    transition: all 0.3s;
    cursor: none;
  }
  .service-row:hover { padding-left: 1rem; border-bottom-color: var(--accent); }
  .service-idx {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1rem; color: var(--muted);
    letter-spacing: 2px;
  }
  .service-name {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.8rem; letter-spacing: 2px;
    transition: color 0.3s;
  }
  .service-row:hover .service-name { color: var(--accent); }
  .service-desc {
    font-size: 0.85rem; line-height: 1.6;
    color: rgba(245,240,232,0.5);
  }
  .service-arrow {
    font-size: 1.5rem; color: var(--muted);
    transition: all 0.3s;
  }
  .service-row:hover .service-arrow { color: var(--accent); transform: translateX(6px); }

  /* NICHES */
  .niches { background: var(--gray); }
  .niches-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 1px; margin-top: 4rem;
    background: rgba(255,255,255,0.04);
  }
  .niche-item {
    background: var(--gray);
    padding: 2.5rem 2rem;
    transition: background 0.3s;
    text-align: center;
  }
  .niche-item:hover { background: rgba(232,197,71,0.06); }
  .niche-icon { font-size: 2rem; margin-bottom: 1rem; }
  .niche-name {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.1rem; letter-spacing: 2px;
    margin-bottom: 0.5rem;
  }
  .niche-type {
    font-size: 0.65rem; letter-spacing: 2px;
    text-transform: uppercase; color: var(--muted);
  }

  /* CTA */
  .cta-section {
    background: var(--black);
    padding: 10rem 4rem;
    text-align: center;
    position: relative; overflow: hidden;
  }
  .cta-bg {
    position: absolute; inset: 0;
    background: radial-gradient(ellipse 80% 60% at 50% 50%, rgba(232,197,71,0.07) 0%, transparent 60%);
  }
  .cta-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(3rem, 8vw, 7rem);
    line-height: 0.95; letter-spacing: 2px;
    position: relative; z-index: 2;
    margin-bottom: 2rem;
  }
  .cta-title span { color: var(--accent); }
  .cta-sub {
    font-size: 1rem; color: rgba(245,240,232,0.6);
    max-width: 500px; margin: 0 auto 3rem;
    line-height: 1.7; position: relative; z-index: 2;
  }
  .cta-btns {
    display: flex; gap: 1.5rem;
    justify-content: center; position: relative; z-index: 2;
  }
  .btn-large {
    background: var(--accent); color: var(--black);
    padding: 1.2rem 3rem;
    font-size: 0.85rem; letter-spacing: 2px;
    text-transform: uppercase; font-weight: 700;
    text-decoration: none;
    transition: all 0.3s;
    clip-path: polygon(0 0, calc(100% - 14px) 0, 100% 14px, 100% 100%, 14px 100%, 0 calc(100% - 14px));
  }
  .btn-large:hover { background: var(--white); transform: scale(1.03); }
  .btn-outline {
    border: 1px solid rgba(255,255,255,0.2);
    color: var(--white);
    padding: 1.2rem 3rem;
    font-size: 0.85rem; letter-spacing: 2px;
    text-transform: uppercase;
    text-decoration: none;
    transition: all 0.3s;
  }
  .btn-outline:hover { border-color: var(--accent); color: var(--accent); }

  /* FOOTER */
  footer {
    background: var(--gray);
    padding: 3rem 4rem;
    display: flex; justify-content: space-between; align-items: center;
    border-top: 1px solid rgba(255,255,255,0.05);
  }
  .footer-logo {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.4rem; letter-spacing: 4px; color: var(--accent);
  }
  .footer-copy {
    font-size: 0.72rem; letter-spacing: 1px;
    color: var(--muted);
  }
  .footer-links { display: flex; gap: 2rem; }
  .footer-links a {
    font-size: 0.72rem; letter-spacing: 1px;
    text-transform: uppercase; color: var(--muted);
    text-decoration: none; transition: color 0.2s;
  }
  .footer-links a:hover { color: var(--accent); }

  /* ANIMATIONS */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
  }
  @keyframes fadeLeft {
    from { opacity: 0; transform: translateX(30px); }
    to { opacity: 1; transform: translateX(0); }
  }
  .reveal {
    opacity: 0; transform: translateY(40px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .reveal.visible { opacity: 1; transform: translateY(0); }

  /* SCROLLBAR */
  ::-webkit-scrollbar { width: 4px; }
  ::-webkit-scrollbar-track { background: var(--black); }
  ::-webkit-scrollbar-thumb { background: var(--accent); }

  /* MOBILE */
  @media (max-width: 768px) {
    nav { padding: 1.2rem 1.5rem; }
    .nav-links { display: none; }
    section { padding: 5rem 1.5rem; }
    .hero { padding: 0 1.5rem; }
    .hero-stats { display: none; }
    .about-grid { grid-template-columns: 1fr; gap: 3rem; }
    .featured-inner { grid-template-columns: 1fr; gap: 3rem; }
    .metrics-grid { grid-template-columns: 1fr 1fr; }
    .service-row { grid-template-columns: 40px 1fr; gap: 1rem; }
    .service-desc, .service-arrow { display: none; }
    .cta-section { padding: 6rem 1.5rem; }
    .cta-btns { flex-direction: column; align-items: center; }
    footer { flex-direction: column; gap: 1.5rem; text-align: center; }
    .footer-links { display: none; }
  }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- NAV -->
<nav>
  <div class="nav-logo">WESLLEY SOUZA PORTFOLIO</div>
  <div class="nav-links">
    <a href="#cases">Cases</a>
    <a href="#servicos">Serviços</a>
    <a href="#motobel">Destaque</a>
    <a href="#contato">Contato</a>
  </div>
</nav>

<!-- HERO -->
<section class="hero" id="hero">
  <div class="hero-bg"></div>
  <div class="hero-lines"></div>
  <div class="hero-content">
    <div class="hero-eyebrow">Social Media & Marketing Digital</div>
    <h1 class="hero-title">
      Resultados<br>
      que <em>falam</em><br>
      por si
    </h1>
    <p class="hero-sub">
      8 anos construindo marcas, escalando conversões e transformando cliques em receita. Do varejo ao B2B, do e-commerce ao jurídico — estratégia com dados, criatividade com propósito.
    </p>
    <div class="hero-cta">
      <a href="#cases" class="btn-primary">Ver Portfólio</a>
      <a href="#contato" class="btn-ghost">Falar comigo</a>
    </div>
  </div>
  <div class="hero-stats">
    <div class="stat-item">
      <div class="stat-num">900+</div>
      <div class="stat-label">Leads qualificados</div>
    </div>
    <div class="stat-divider"></div>
    <div class="stat-item">
      <div class="stat-num">8+</div>
      <div class="stat-label">Clientes atendidos</div>
    </div>
    <div class="stat-divider"></div>
    <div class="stat-item">
      <div class="stat-num">15%</div>
      <div class="stat-label">Taxa média de conversão</div>
    </div>
  </div>
</section>

<!-- ABOUT -->
<section class="about" id="sobre">
  <div class="section-tag">Sobre mim</div>
  <h2 class="section-title">Estratégia,<br><span>criatividade</span> e conversão</h2>
  <div class="about-grid">
    <div class="about-text reveal">
      <p>Profissional com <strong>8 anos de experiência</strong> em marketing digital, social media e gestão de tráfego. Já atendi desde startups de inteligência artificial e hamburguerias locais até concessionárias multimarca e construtoras B2B.</p>
      <p>Minha abordagem une <strong>análise de dados com storytelling visual</strong> — cada campanha é construída para converter, não apenas para aparecer. Seja no orgânico ou no pago, nos marketplaces ou nas redes sociais.</p>
      <p>Domino todos os pilares do marketing moderno: <strong>identidade visual, tráfego pago, conteúdo, SEO de marketplace e estratégia comercial</strong> — sempre com foco em ROI real.</p>
    </div>
    <div class="skills-grid reveal">
      <div class="skill-tag">Gestão de Tráfego Pago</div>
      <div class="skill-tag">Social Media Orgânico</div>
      <div class="skill-tag">Identidade Visual</div>
      <div class="skill-tag">Marketing B2B</div>
      <div class="skill-tag">E-commerce & Marketplace</div>
      <div class="skill-tag">Edição de Vídeo</div>
      <div class="skill-tag">Design de Banners</div>
      <div class="skill-tag">Geração de Leads</div>
      <div class="skill-tag">Estratégia de Conteúdo</div>
      <div class="skill-tag">CRM & Pós-venda</div>
      <div class="skill-tag">Eventos & Networking B2B</div>
      <div class="skill-tag">Análise de Métricas (ROI, CTA)</div>
    </div>
  </div>
</section>

<!-- CASES -->
<section class="cases" id="cases">
  <div class="section-tag">Portfólio</div>
  <h2 class="section-title">Cases que<br><span>geraram resultado</span></h2>
  <div class="cases-grid">

    <div class="case-card reveal">
      <div class="case-num">01</div>
      <div class="case-badge badge-ecom">E-commerce</div>
      <div class="case-name">Shop UD</div>
      <div class="case-role">Marketing Digital & Social Media</div>
      <div class="case-desc">Implementação de estratégias completas de marketing para e-commerce e marketplaces, aliadas ao gerenciamento orgânico das redes sociais. Crescimento de audiência e conversões através de conteúdo estratégico de utilidades domésticas.</div>
      <div class="case-results">
        <span class="result-chip">E-commerce</span>
        <span class="result-chip">Marketplaces</span>
        <span class="result-chip">Social Orgânico</span>
        <span class="result-chip">Conteúdo</span>
      </div>
    </div>

    <div class="case-card reveal">
      <div class="case-num">02</div>
      <div class="case-badge badge-b2b">B2B</div>
      <div class="case-name">XMachina</div>
      <div class="case-role">Marketing B2B & Social Media</div>
      <div class="case-desc">Startup de IA disruptiva voltada a indústrias. Criação de vídeos, banners e estratégias de conversão B2B para grandes e pequenas indústrias. Participação ativa em eventos e negociações comerciais estratégicas.</div>
      <div class="case-results">
        <span class="result-chip">Indústrias</span>
        <span class="result-chip">Video Marketing</span>
        <span class="result-chip">Eventos B2B</span>
        <span class="result-chip">Conversão</span>
      </div>
    </div>

    <div class="case-card reveal">
      <div class="case-num">03</div>
      <div class="case-badge badge-b2c">B2C Local</div>
      <div class="case-name">Hambúrgueria</div>
      <div class="case-role">Identidade Visual, Social Media & Marketing</div>
      <div class="case-desc">Criação da identidade visual do zero e estratégia de marketing focada em conversão de leads regionais. Maior conquista: migrar clientes de plataformas como iFood para canal direto, reduzindo comissões e aumentando margem.</div>
      <div class="case-results">
        <span class="result-chip">Identidade Visual</span>
        <span class="result-chip">Leads Regionais</span>
        <span class="result-chip">Cliente Direto vs iFood</span>
      </div>
    </div>

    <div class="case-card reveal">
      <div class="case-num">04</div>
      <div class="case-badge badge-ecom">Marketplace</div>
      <div class="case-name">Casa das Capas</div>
      <div class="case-role">Analista de Marketing & Marketplace</div>
      <div class="case-desc">Pesquisa de tendências no nicho de casa e enxoval. Foco em conversão e otimização de marketplaces, responsáveis por 60% da operação. Análise constante de métricas para manutenção do posicionamento competitivo.</div>
      <div class="case-results">
        <span class="result-chip">60% via Marketplace</span>
        <span class="result-chip">Tendências de Nicho</span>
        <span class="result-chip">Otimização de Listagens</span>
      </div>
    </div>

    <div class="case-card reveal">
      <div class="case-num">05</div>
      <div class="case-badge badge-b2b">B2B</div>
      <div class="case-name">Alar Construtora</div>
      <div class="case-role">Identidade Visual & Estratégia Digital B2B</div>
      <div class="case-desc">Construção completa da identidade visual, site institucional e estratégia de captação digital B2B. Foco em parcerias com incorporadoras e engenharias de todos os portes. Posicionamento premium no segmento de serviços terceirizados para condomínios.</div>
      <div class="case-results">
        <span class="result-chip">Identidade Visual</span>
        <span class="result-chip">Site Institucional</span>
        <span class="result-chip">Parcerias B2B</span>
        <span class="result-chip">Incorporadoras</span>
      </div>
    </div>

    <div class="case-card reveal">
      <div class="case-num">06</div>
      <div class="case-badge badge-b2b">B2B Jurídico</div>
      <div class="case-name">Pablo Buarque Advogado</div>
      <div class="case-role">Social Media, Designer, Editor & Gestor de Tráfego</div>
      <div class="case-desc">Gestão 360° da presença digital de escritório jurídico especializado em recuperação judicial e trabalhista para empresas. Criação de conteúdo de autoridade, edição de vídeos e campanhas de tráfego pago focadas em empresas em dificuldades financeiras.</div>
      <div class="case-results">
        <span class="result-chip">Recuperação Judicial</span>
        <span class="result-chip">Tráfego Pago</span>
        <span class="result-chip">Autoridade Digital</span>
        <span class="result-chip">Edição de Vídeo</span>
      </div>
    </div>

  </div>
</section>

<!-- FEATURED: MOTOBEL -->
<section class="featured-case" id="motobel">
  <div class="section-tag">Case em destaque</div>
  <div class="featured-inner">
    <div>
      <div class="feat-label">Resultado acima da média regional</div>
      <h2 class="feat-title reveal">MOTOBEL<br><span style="color:var(--accent)">GRUPO</span></h2>
      <p class="feat-desc reveal">Analista de Marketing responsável por 6 concessionárias simultâneas nos nichos de automóveis (Honda), motocicletas (Bajaj) e empilhadeiras (Toyota). Gestão completa de tráfego pago, social media, roteirização e calendário editorial — com resultados expressivos acima da média da região.</p>
      <div class="feat-tags reveal">
        <span class="feat-tag">Tráfego Pago</span>
        <span class="feat-tag">6 Concessionárias</span>
        <span class="feat-tag">3 Nichos</span>
        <span class="feat-tag">2 Estados</span>
        <span class="feat-tag">ROI Otimizado</span>
        <span class="feat-tag">Pós-venda</span>
      </div>
    </div>
    <div class="reveal">
      <div class="metrics-grid">
        <div class="metric">
          <div class="metric-val">300</div>
          <div class="metric-lbl">Leads Qualificados<br>Honda (1 cidade)</div>
        </div>
        <div class="metric">
          <div class="metric-val">500</div>
          <div class="metric-lbl">Leads Qualificados<br>Bajaj (2 estados)</div>
        </div>
        <div class="metric">
          <div class="metric-val">100</div>
          <div class="metric-lbl">Leads Qualificados<br>Toyota Empilhadeiras</div>
        </div>
        <div class="metric">
          <div class="metric-val">10<span class="metric-unit">-15%</span></div>
          <div class="metric-lbl">Taxa Média de<br>Conversão</div>
        </div>
        <div class="metric">
          <div class="metric-val">6</div>
          <div class="metric-lbl">Concessionárias<br>Gerenciadas</div>
        </div>
        <div class="metric">
          <div class="metric-val">↑</div>
          <div class="metric-lbl">Acima da Média<br>Regional</div>
        </div>
      </div>
    </div>
  </div>
</section>
</section>

<!-- BEHANCE SECTION -->
<section class="behance-section">
  <div class="section-tag">Mais projetos</div>
  <h2 class="section-title">Veja meus trabalhos no <span>Behance</span></h2>
  <p style="color: var(--muted); margin-bottom: 3rem; font-size: 1.1rem;">Confira meu portfólio completo com detalhes de cada projeto e produções audiovisuais.</p>
  <a href="https://www.behance.net/weslleysouza2" target="_blank" class="behance-btn">
    Acessar Behance →
  </a>
</section>
<!-- SERVICES -->
<section class="services" id="servicos">
  <div class="section-tag">O que eu faço</div>
  <h2 class="section-title">Serviços<br><span>disponíveis</span></h2>
  <div class="services-list">
    <div class="service-row reveal">
   <span class="service-idx">01</span>
      <span class="service-name">SOCIAL MEDIA COMPLETO</span>
      <span class="service-desc">Calendário editorial, criação de conteúdo, design de posts e gestão de comunidade</span>
      <span class="service-arrow">→</span>
    </div>
    <div class="service-row reveal">
     <span class="service-idx">02</span>
      <span class="service-name">GESTÃO DE TRÁFEGO PAGO</span>
      <span class="service-desc">Meta Ads, Google Ads, campanhas otimizadas por CPA e ROAS com relatórios de performance</span>
      <span class="service-arrow">→</span>
    </div>
      <div class="service-row reveal">
      <span class="service-idx">03</span>
      <span class="service-name">EDIÇÃO DE VÍDEO & ROTEIRO</span>
      <span class="service-desc">Produção audiovisual para redes sociais, eventos, reels e campanhas institucionais</span>
      <span class="service-arrow">→</span>
    </div>
    <div class="service-row reveal">
      <span class="service-idx">04</span>
      <span class="service-name">IDENTIDADE VISUAL</span>
      <span class="service-desc">Branding, logotipo, paleta, tipografia e guia de marca do zero</span>
      <span class="service-arrow">→</span>
    </div>
    <div class="service-row reveal">
      <span class="service-idx">05</span>
      <span class="service-name">MARKETPLACE & E-COMMERCE</span>
      <span class="service-desc">Otimização de listagens, SEO de produto e estratégia de canais de venda</span>
    </div>
    <div class="service-row reveal">
      <span class="service-idx">06</span>
      <span class="service-name">ESTRATÉGIA B2B DIGITAL</span>
      <span class="service-desc">Funil de vendas consultivo, captação de parceiros e posicionamento corporativo</span>
      <span class="service-arrow">→</span>
    </div>
  </div>
</section>

<!-- NICHES -->
<section class="niches" id="nichos">
  <div class="section-tag">Nichos de atuação</div>
  <h2 class="section-title">Experiência em<br><span>múltiplos setores</span></h2>
  <div class="niches-grid reveal">
    <div class="niche-item">
      <div class="niche-icon">🏠</div>
      <div class="niche-name">Casa & Varejo</div>
      <div class="niche-type">B2C / E-commerce</div>
    </div>
    <div class="niche-item">
      <div class="niche-icon">🤖</div>
      <div class="niche-name">Tecnologia & IA</div>
      <div class="niche-type">B2B / Startup</div>
    </div>
    <div class="niche-item">
      <div class="niche-icon">🍔</div>
      <div class="niche-name">Food & Delivery</div>
      <div class="niche-type">B2C / Local</div>
    </div>
    <div class="niche-item">
      <div class="niche-icon">🚗</div>
      <div class="niche-name">Automotivo</div>
      <div class="niche-type">B2C / Concessionárias</div>
    </div>
    <div class="niche-item">
      <div class="niche-icon">🏗️</div>
      <div class="niche-name">Construção Civil</div>
      <div class="niche-type">B2B / Corporativo</div>
    </div>
    <div class="niche-item">
      <div class="niche-icon">⚖️</div>
      <div class="niche-name">Jurídico</div>
      <div class="niche-type">B2B / Advocacia</div>
    </div>
  </div>
</section>

<!-- CTA -->
<section class="cta-section" id="contato">
  <div class="cta-bg"></div>
  <h2 class="cta-title">Seu próximo<br><span>case</span><br>começa aqui</h2>
  <p class="cta-sub">Pronto para transformar sua presença digital em resultados mensuráveis? Vamos conversar sobre sua empresa.</p>
  <div class="cta-btns">
    <a href="https://wa.me/5591991407311" class="btn-large">💬 Chamar no WhatsApp</a>
    <a href="mailto:weslleysocialmidia16@gmail.com" class="btn-outline">Enviar E-mail</a>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">WESLLEY PORTFOLIO</div>
  <div class="footer-copy">© 2025 — Todos os direitos reservados</div>
  <div class="footer-links">
    <a href="#cases">Cases</a>
    <a href="#servicos">Serviços</a>
    <a href="#contato">Contato</a>
  </div>
</footer>

<script>
  // Custom cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;
  document.addEventListener('mousemove', e => {
    mx = e.clientX; my = e.clientY;
    cursor.style.left = (mx - 6) + 'px';
    cursor.style.top = (my - 6) + 'px';
  });
  function animateRing() {
    rx += (mx - rx - 18) * 0.12;
    ry += (my - ry - 18) * 0.12;
    ring.style.left = rx + 'px';
    ring.style.top = ry + 'px';
    requestAnimationFrame(animateRing);
  }
  animateRing();

  document.querySelectorAll('a, button, .case-card, .service-row').forEach(el => {
    el.addEventListener('mouseenter', () => cursor.style.transform = 'scale(2.5)');
    el.addEventListener('mouseleave', () => cursor.style.transform = 'scale(1)');
  });

  // Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if (e.isIntersecting) { e.target.classList.add('visible'); }
    });
  }, { threshold: 0.12 });
  reveals.forEach(el => observer.observe(el));
</script>
</body>
</html>
