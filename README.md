# dominicmartin.github.io
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Your Name — Web Designer</title>
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet" />
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --yellow: #F5E642;
      --pink: #FF4D8D;
      --blue: #1A1AFF;
      --orange: #FF6B2B;
      --black: #0D0D0D;
      --white: #F9F7F0;
      --gray: #E8E5DC;
      --font-display: 'Syne', sans-serif;
      --font-body: 'DM Sans', sans-serif;
    }

    html { scroll-behavior: smooth; }

    body {
      font-family: var(--font-body);
      background: var(--white);
      color: var(--black);
      overflow-x: hidden;
      cursor: none;
    }

    /* Custom cursor */
    .cursor {
      width: 12px; height: 12px;
      background: var(--pink);
      border-radius: 50%;
      position: fixed;
      pointer-events: none;
      z-index: 9999;
      transform: translate(-50%, -50%);
      transition: transform 0.1s, width 0.2s, height 0.2s, background 0.2s;
    }
    .cursor-ring {
      width: 36px; height: 36px;
      border: 1.5px solid var(--black);
      border-radius: 50%;
      position: fixed;
      pointer-events: none;
      z-index: 9998;
      transform: translate(-50%, -50%);
      transition: transform 0.18s ease, width 0.2s, height 0.2s;
    }
    body:hover .cursor { opacity: 1; }

    /* NAV */
    nav {
      position: fixed; top: 0; left: 0; right: 0;
      z-index: 100;
      padding: 1.2rem 4vw;
      display: flex; align-items: center; justify-content: space-between;
      mix-blend-mode: multiply;
    }
    .nav-logo {
      font-family: var(--font-display);
      font-weight: 800;
      font-size: 1.15rem;
      letter-spacing: -0.03em;
      color: var(--black);
      text-decoration: none;
    }
    .nav-links { display: flex; gap: 2rem; list-style: none; }
    .nav-links a {
      font-size: 0.82rem;
      font-weight: 500;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      color: var(--black);
      text-decoration: none;
      position: relative;
    }
    .nav-links a::after {
      content: '';
      position: absolute; bottom: -2px; left: 0;
      width: 0; height: 1.5px;
      background: var(--pink);
      transition: width 0.25s;
    }
    .nav-links a:hover::after { width: 100%; }

    /* HERO */
    #hero {
      min-height: 100vh;
      background: var(--black);
      display: flex; flex-direction: column;
      justify-content: flex-end;
      padding: 0 4vw 5vh;
      position: relative;
      overflow: hidden;
    }
    .hero-bg-shapes {
      position: absolute; inset: 0; pointer-events: none;
    }
    .shape {
      position: absolute;
      border-radius: 50%;
      animation: floatShape 10s ease-in-out infinite alternate;
    }
    .shape-1 { width: 420px; height: 420px; background: var(--yellow); top: -100px; right: -80px; animation-delay: 0s; opacity: 0.9; border-radius: 60% 40% 50% 60% / 50% 60% 40% 50%; }
    .shape-2 { width: 220px; height: 220px; background: var(--pink); top: 30%; left: -60px; animation-delay: -3s; opacity: 0.85; }
    .shape-3 { width: 140px; height: 140px; background: var(--orange); bottom: 120px; right: 20%; animation-delay: -6s; opacity: 0.8; border-radius: 30% 70% 60% 40% / 50% 40% 60% 50%; }
    @keyframes floatShape {
      from { transform: translateY(0) rotate(0deg); }
      to { transform: translateY(-30px) rotate(8deg); }
    }

    .hero-tag {
      display: inline-block;
      background: var(--yellow);
      color: var(--black);
      font-size: 0.75rem;
      font-weight: 500;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      padding: 0.35rem 0.9rem;
      border-radius: 100px;
      margin-bottom: 1.5rem;
      width: fit-content;
      animation: fadeUp 0.8s ease both;
    }
    .hero-headline {
      font-family: var(--font-display);
      font-size: clamp(4rem, 12vw, 11rem);
      font-weight: 800;
      line-height: 0.9;
      letter-spacing: -0.04em;
      color: var(--white);
      animation: fadeUp 0.8s 0.1s ease both;
    }
    .hero-headline span { color: var(--yellow); }
    .hero-headline em {
      font-style: italic;
      color: var(--pink);
      font-weight: 700;
    }
    .hero-sub {
      margin-top: 2rem;
      display: flex; align-items: center; gap: 2rem;
      animation: fadeUp 0.8s 0.25s ease both;
    }
    .hero-sub p {
      font-size: 1rem;
      color: rgba(249,247,240,0.6);
      max-width: 300px;
      line-height: 1.6;
    }
    .hero-cta {
      display: inline-flex; align-items: center; gap: 0.6rem;
      background: var(--yellow);
      color: var(--black);
      font-family: var(--font-display);
      font-weight: 700;
      font-size: 0.9rem;
      letter-spacing: -0.01em;
      padding: 0.85rem 1.8rem;
      border-radius: 100px;
      text-decoration: none;
      white-space: nowrap;
      transition: transform 0.2s, background 0.2s;
    }
    .hero-cta:hover { background: var(--pink); color: var(--white); transform: scale(1.04); }
    .hero-cta-arrow { font-size: 1.1rem; transition: transform 0.2s; }
    .hero-cta:hover .hero-cta-arrow { transform: translate(3px, -3px); }

    .hero-scroll {
      position: absolute; right: 4vw; bottom: 5vh;
      display: flex; flex-direction: column; align-items: center; gap: 8px;
      animation: fadeUp 0.8s 0.5s ease both;
    }
    .hero-scroll span {
      font-size: 0.7rem; letter-spacing: 0.15em; text-transform: uppercase;
      color: rgba(249,247,240,0.4);
      writing-mode: vertical-rl;
    }
    .scroll-line {
      width: 1px; height: 60px;
      background: linear-gradient(to bottom, rgba(249,247,240,0.4), transparent);
      animation: scrollPulse 2s ease-in-out infinite;
    }
    @keyframes scrollPulse { 0%,100%{opacity:0.3} 50%{opacity:1} }

    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(30px); }
      to { opacity: 1; transform: translateY(0); }
    }

    /* SECTION COMMON */
    section { padding: 7rem 4vw; }
    .section-label {
      font-size: 0.72rem;
      font-weight: 500;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: var(--pink);
      margin-bottom: 1rem;
      display: flex; align-items: center; gap: 0.7rem;
    }
    .section-label::before {
      content: '';
      display: inline-block;
      width: 28px; height: 1.5px;
      background: var(--pink);
    }
    .section-title {
      font-family: var(--font-display);
      font-size: clamp(2.4rem, 5vw, 4.5rem);
      font-weight: 800;
      letter-spacing: -0.04em;
      line-height: 1;
    }

    /* ABOUT */
    #about { background: var(--white); }
    .about-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 6rem;
      margin-top: 4rem;
      align-items: start;
    }
    .about-visual {
      position: relative;
      aspect-ratio: 3/4;
      background: var(--gray);
      border-radius: 2rem;
      overflow: hidden;
    }
    .about-visual-placeholder {
      width: 100%; height: 100%;
      display: flex; flex-direction: column;
      align-items: center; justify-content: center;
      gap: 0.8rem;
      color: rgba(13,13,13,0.3);
      font-size: 0.85rem;
      letter-spacing: 0.05em;
    }
    .about-visual-placeholder .avatar-icon {
      width: 72px; height: 72px;
      background: rgba(13,13,13,0.08);
      border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      font-size: 2rem;
    }
    .about-sticker {
      position: absolute; bottom: -16px; right: -16px;
      width: 110px; height: 110px;
      background: var(--yellow);
      border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      font-family: var(--font-display);
      font-weight: 800;
      font-size: 0.7rem;
      text-align: center;
      letter-spacing: 0.04em;
      text-transform: uppercase;
      color: var(--black);
      line-height: 1.3;
      animation: spin 12s linear infinite;
    }
    @keyframes spin { to { transform: rotate(360deg); } }
    .about-content { padding-top: 1rem; }
    .about-content p {
      font-size: 1.08rem;
      line-height: 1.75;
      color: rgba(13,13,13,0.7);
      margin-bottom: 1.4rem;
    }
    .about-stats {
      display: grid; grid-template-columns: repeat(3, 1fr);
      gap: 1.5rem; margin-top: 2.5rem;
    }
    .stat {
      border-top: 2px solid var(--black);
      padding-top: 1rem;
    }
    .stat-num {
      font-family: var(--font-display);
      font-size: 2.8rem;
      font-weight: 800;
      letter-spacing: -0.04em;
      color: var(--black);
      line-height: 1;
    }
    .stat-num span { color: var(--pink); }
    .stat-label {
      font-size: 0.78rem;
      color: rgba(13,13,13,0.5);
      letter-spacing: 0.04em;
      margin-top: 0.3rem;
    }

    /* SKILLS */
    #skills { background: var(--black); color: var(--white); }
    #skills .section-label { color: var(--yellow); }
    #skills .section-label::before { background: var(--yellow); }
    #skills .section-title { color: var(--white); }
    .skills-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 1.5px;
      margin-top: 4rem;
      border: 1.5px solid rgba(249,247,240,0.08);
      border-radius: 1.5rem;
      overflow: hidden;
    }
    .skill-card {
      padding: 2.2rem 2rem;
      background: rgba(249,247,240,0.03);
      transition: background 0.25s;
      position: relative;
      overflow: hidden;
    }
    .skill-card::before {
      content: '';
      position: absolute; inset: 0;
      background: var(--skill-color, var(--yellow));
      opacity: 0;
      transition: opacity 0.3s;
    }
    .skill-card:hover::before { opacity: 0.06; }
    .skill-card:hover { background: rgba(249,247,240,0.06); }
    .skill-icon {
      font-size: 2rem;
      margin-bottom: 1.2rem;
    }
    .skill-name {
      font-family: var(--font-display);
      font-size: 1.15rem;
      font-weight: 700;
      letter-spacing: -0.02em;
      color: var(--white);
      margin-bottom: 0.5rem;
    }
    .skill-tags {
      display: flex; flex-wrap: wrap; gap: 0.4rem;
      margin-top: 1rem;
    }
    .skill-tag {
      font-size: 0.7rem;
      letter-spacing: 0.06em;
      text-transform: uppercase;
      padding: 0.25rem 0.7rem;
      background: rgba(249,247,240,0.08);
      border-radius: 100px;
      color: rgba(249,247,240,0.6);
    }

    /* PROJECTS */
    #projects { background: var(--white); }
    .projects-header {
      display: flex; align-items: flex-end; justify-content: space-between;
      margin-bottom: 4rem;
    }
    .projects-grid {
      display: grid;
      grid-template-columns: repeat(12, 1fr);
      gap: 1.5rem;
    }
    .project-card {
      border-radius: 1.5rem;
      overflow: hidden;
      position: relative;
      background: var(--gray);
      cursor: none;
    }
    .project-card:nth-child(1) { grid-column: span 7; }
    .project-card:nth-child(2) { grid-column: span 5; }
    .project-card:nth-child(3) { grid-column: span 5; }
    .project-card:nth-child(4) { grid-column: span 7; }

    .project-img {
      aspect-ratio: 16/10;
      display: flex; align-items: center; justify-content: center;
      font-size: 0.8rem;
      color: rgba(13,13,13,0.3);
      letter-spacing: 0.05em;
      position: relative;
      overflow: hidden;
      transition: transform 0.4s ease;
    }
    .project-card:hover .project-img { transform: scale(1.03); }
    .project-img-bg {
      position: absolute; inset: 0;
      transition: transform 0.4s ease;
    }
    .project-card:nth-child(1) .project-img-bg { background: #FFE0EC; }
    .project-card:nth-child(2) .project-img-bg { background: #E0F0FF; }
    .project-card:nth-child(3) .project-img-bg { background: #FFF5D6; }
    .project-card:nth-child(4) .project-img-bg { background: #E0FFE8; }

    .project-img-label {
      position: relative; z-index: 1;
      font-size: 0.75rem; letter-spacing: 0.08em;
      color: rgba(13,13,13,0.35);
      text-transform: uppercase;
    }
    .project-info {
      padding: 1.4rem 1.6rem 1.6rem;
      display: flex; align-items: center; justify-content: space-between;
    }
    .project-meta {}
    .project-num {
      font-size: 0.68rem;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: var(--pink);
      margin-bottom: 0.3rem;
    }
    .project-name {
      font-family: var(--font-display);
      font-size: 1.15rem;
      font-weight: 700;
      letter-spacing: -0.02em;
      color: var(--black);
    }
    .project-type {
      font-size: 0.78rem;
      color: rgba(13,13,13,0.45);
      margin-top: 0.2rem;
    }
    .project-link {
      width: 42px; height: 42px;
      border-radius: 50%;
      background: var(--black);
      color: var(--white);
      display: flex; align-items: center; justify-content: center;
      font-size: 1.1rem;
      text-decoration: none;
      transition: background 0.2s, transform 0.2s;
      flex-shrink: 0;
    }
    .project-link:hover { background: var(--pink); transform: scale(1.1); }

    /* EXPERIENCE */
    #experience { background: var(--yellow); }
    #experience .section-label { color: var(--black); }
    #experience .section-label::before { background: var(--black); }
    .exp-list { margin-top: 4rem; }
    .exp-item {
      display: grid;
      grid-template-columns: 1fr 2fr auto;
      gap: 2rem;
      align-items: start;
      padding: 2.2rem 0;
      border-top: 1.5px solid rgba(13,13,13,0.15);
      transition: padding-left 0.25s;
    }
    .exp-item:last-child { border-bottom: 1.5px solid rgba(13,13,13,0.15); }
    .exp-item:hover { padding-left: 1rem; }
    .exp-period {
      font-size: 0.78rem;
      font-weight: 500;
      letter-spacing: 0.06em;
      color: rgba(13,13,13,0.5);
      text-transform: uppercase;
      padding-top: 0.2rem;
    }
    .exp-role {
      font-family: var(--font-display);
      font-size: 1.4rem;
      font-weight: 700;
      letter-spacing: -0.03em;
      color: var(--black);
      margin-bottom: 0.3rem;
    }
    .exp-company {
      font-size: 0.85rem;
      color: rgba(13,13,13,0.6);
      margin-bottom: 0.8rem;
    }
    .exp-desc {
      font-size: 0.88rem;
      line-height: 1.65;
      color: rgba(13,13,13,0.65);
      max-width: 480px;
    }
    .exp-badge {
      font-size: 0.7rem;
      letter-spacing: 0.06em;
      text-transform: uppercase;
      padding: 0.3rem 0.8rem;
      border-radius: 100px;
      background: var(--black);
      color: var(--yellow);
      white-space: nowrap;
      height: fit-content;
    }

    /* CONTACT */
    #contact {
      background: var(--black);
      text-align: center;
      padding: 8rem 4vw;
    }
    #contact .section-label { justify-content: center; }
    #contact .section-label::before { display: none; }
    .contact-headline {
      font-family: var(--font-display);
      font-size: clamp(3rem, 8vw, 7.5rem);
      font-weight: 800;
      letter-spacing: -0.04em;
      color: var(--white);
      line-height: 0.95;
      margin: 1.5rem 0 3rem;
    }
    .contact-headline span { color: var(--yellow); display: block; }
    .contact-email {
      display: inline-block;
      font-family: var(--font-display);
      font-size: clamp(1rem, 2.5vw, 1.5rem);
      font-weight: 700;
      color: var(--white);
      text-decoration: none;
      border-bottom: 2px solid var(--pink);
      padding-bottom: 0.2rem;
      transition: color 0.2s;
      letter-spacing: -0.02em;
      margin-bottom: 3rem;
    }
    .contact-email:hover { color: var(--pink); }
    .contact-social {
      display: flex; justify-content: center; gap: 1.2rem;
      margin-top: 4rem;
      flex-wrap: wrap;
    }
    .social-link {
      display: inline-flex; align-items: center; gap: 0.5rem;
      font-size: 0.78rem;
      font-weight: 500;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: rgba(249,247,240,0.5);
      text-decoration: none;
      padding: 0.6rem 1.2rem;
      border: 1px solid rgba(249,247,240,0.1);
      border-radius: 100px;
      transition: color 0.2s, border-color 0.2s;
    }
    .social-link:hover { color: var(--yellow); border-color: var(--yellow); }

    /* FOOTER */
    footer {
      background: var(--black);
      border-top: 1px solid rgba(249,247,240,0.06);
      padding: 1.8rem 4vw;
      display: flex; align-items: center; justify-content: space-between;
    }
    footer p {
      font-size: 0.75rem;
      color: rgba(249,247,240,0.25);
      letter-spacing: 0.04em;
    }

    /* REVEAL ANIMATION */
    .reveal {
      opacity: 0;
      transform: translateY(40px);
      transition: opacity 0.7s ease, transform 0.7s ease;
    }
    .reveal.visible {
      opacity: 1;
      transform: translateY(0);
    }

    /* RESPONSIVE */
    @media (max-width: 900px) {
      .about-grid { grid-template-columns: 1fr; gap: 3rem; }
      .about-visual { aspect-ratio: 1; max-height: 360px; }
      .project-card:nth-child(1),
      .project-card:nth-child(2),
      .project-card:nth-child(3),
      .project-card:nth-child(4) { grid-column: span 12; }
      .exp-item { grid-template-columns: 1fr; gap: 0.5rem; }
      .projects-header { flex-direction: column; align-items: flex-start; gap: 1rem; }
      nav { padding: 1rem 5vw; }
      .nav-links { gap: 1.2rem; }
    }
    @media (max-width: 600px) {
      .nav-links { display: none; }
      section { padding: 5rem 5vw; }
      .about-stats { grid-template-columns: 1fr 1fr; }
    }
  </style>
</head>
<body>

  <!-- Custom cursor -->
  <div class="cursor" id="cursor"></div>
  <div class="cursor-ring" id="cursorRing"></div>

  <!-- NAV -->
  <nav>
    <a href="#hero" class="nav-logo">YourName.</a>
    <ul class="nav-links">
      <li><a href="#about">About</a></li>
      <li><a href="#skills">Skills</a></li>
      <li><a href="#projects">Projects</a></li>
      <li><a href="#experience">Experience</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
  </nav>

  <!-- HERO -->
  <section id="hero">
    <div class="hero-bg-shapes">
      <div class="shape shape-1"></div>
      <div class="shape shape-2"></div>
      <div class="shape shape-3"></div>
    </div>

    <div class="hero-tag">Available for freelance work</div>
    <h1 class="hero-headline">
      Your<br>
      <em>Name</em><br>
      <span>Here.</span>
    </h1>
    <div class="hero-sub">
      <p>Web Designer crafting bold, purposeful digital experiences that leave a mark.</p>
      <a href="#projects" class="hero-cta">
        View my work <span class="hero-cta-arrow">↗</span>
      </a>
    </div>

    <div class="hero-scroll">
      <div class="scroll-line"></div>
      <span>Scroll</span>
    </div>
  </section>

  <!-- ABOUT -->
  <section id="about">
    <div class="section-label">About me</div>
    <div class="about-grid">
      <div>
        <div class="about-visual reveal">
          <div class="about-visual-placeholder">
            <div class="avatar-icon">👤</div>
            <span>Your Photo Here</span>
          </div>
          <div class="about-sticker">Avail&shy;able<br>for Work ✦</div>
        </div>
      </div>
      <div class="about-content reveal">
        <div class="section-title" style="margin-bottom:2rem;">
          I design with<br>intention &amp; <em style="font-style:italic;color:var(--pink);">soul.</em>
        </div>
        <p>Hi, I'm <strong>Your Name</strong> — a Web Designer based in [Your City]. I specialize in creating visually striking, user-centered digital experiences that communicate clearly and convert beautifully.</p>
        <p>With a passion for bold typography, thoughtful color, and smooth interaction, I bring brand visions to life across web, product, and digital platforms. I believe great design is both art and strategy.</p>
        <p>When I'm not designing, you'll find me [your hobby], [another hobby], or exploring the latest in digital art and emerging tools.</p>
        <div class="about-stats">
          <div class="stat">
            <div class="stat-num">3<span>+</span></div>
            <div class="stat-label">Years of experience</div>
          </div>
          <div class="stat">
            <div class="stat-num">20<span>+</span></div>
            <div class="stat-label">Projects completed</div>
          </div>
          <div class="stat">
            <div class="stat-num">10<span>+</span></div>
            <div class="stat-label">Happy clients</div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- SKILLS -->
  <section id="skills">
    <div class="section-label">What I do</div>
    <h2 class="section-title">Skills &amp; Tools</h2>
    <div class="skills-grid reveal">
      <div class="skill-card" style="--skill-color: var(--pink);">
        <div class="skill-icon">🎨</div>
        <div class="skill-name">UI / UX Design</div>
        <p style="font-size:0.85rem;color:rgba(249,247,240,0.5);line-height:1.6;">Wireframes, prototypes, and polished interfaces that users love.</p>
        <div class="skill-tags">
          <span class="skill-tag">Figma</span>
          <span class="skill-tag">Sketch</span>
          <span class="skill-tag">Adobe XD</span>
        </div>
      </div>
      <div class="skill-card" style="--skill-color: var(--yellow);">
        <div class="skill-icon">💻</div>
        <div class="skill-name">Frontend Dev</div>
        <p style="font-size:0.85rem;color:rgba(249,247,240,0.5);line-height:1.6;">Translating pixel-perfect designs into responsive, living code.</p>
        <div class="skill-tags">
          <span class="skill-tag">HTML</span>
          <span class="skill-tag">CSS</span>
          <span class="skill-tag">JavaScript</span>
        </div>
      </div>
      <div class="skill-card" style="--skill-color: var(--orange);">
        <div class="skill-icon">✦</div>
        <div class="skill-name">Branding</div>
        <p style="font-size:0.85rem;color:rgba(249,247,240,0.5);line-height:1.6;">Visual identities that tell a story and stick in the mind.</p>
        <div class="skill-tags">
          <span class="skill-tag">Illustrator</span>
          <span class="skill-tag">Photoshop</span>
          <span class="skill-tag">Logo Design</span>
        </div>
      </div>
      <div class="skill-card" style="--skill-color: var(--blue);">
        <div class="skill-icon">🚀</div>
        <div class="skill-name">Web Strategy</div>
        <p style="font-size:0.85rem;color:rgba(249,247,240,0.5);line-height:1.6;">Turning goals into digital products that grow businesses.</p>
        <div class="skill-tags">
          <span class="skill-tag">CRO</span>
          <span class="skill-tag">Analytics</span>
          <span class="skill-tag">SEO Basics</span>
        </div>
      </div>
      <div class="skill-card" style="--skill-color: var(--pink);">
        <div class="skill-icon">📱</div>
        <div class="skill-name">Responsive Design</div>
        <p style="font-size:0.85rem;color:rgba(249,247,240,0.5);line-height:1.6;">Flawless experiences from mobile to widescreen and everything between.</p>
        <div class="skill-tags">
          <span class="skill-tag">Mobile-first</span>
          <span class="skill-tag">Flexbox</span>
          <span class="skill-tag">CSS Grid</span>
        </div>
      </div>
      <div class="skill-card" style="--skill-color: var(--yellow);">
        <div class="skill-icon">⚡</div>
        <div class="skill-name">Motion & Animation</div>
        <p style="font-size:0.85rem;color:rgba(249,247,240,0.5);line-height:1.6;">Bringing interfaces to life with purposeful movement.</p>
        <div class="skill-tags">
          <span class="skill-tag">CSS Animations</span>
          <span class="skill-tag">GSAP</span>
          <span class="skill-tag">Lottie</span>
        </div>
      </div>
    </div>
  </section>

  <!-- PROJECTS -->
  <section id="projects">
    <div class="projects-header">
      <div>
        <div class="section-label">Selected work</div>
        <h2 class="section-title">Projects</h2>
      </div>
      <a href="#contact" class="hero-cta" style="font-size:0.82rem;padding:0.7rem 1.4rem;">
        Start a project ↗
      </a>
    </div>
    <div class="projects-grid reveal">
      <div class="project-card">
        <div class="project-img">
          <div class="project-img-bg"></div>
          <span class="project-img-label">Project Screenshot</span>
        </div>
        <div class="project-info">
          <div class="project-meta">
            <div class="project-num">01</div>
            <div class="project-name">Project Alpha</div>
            <div class="project-type">Brand Identity · Web Design</div>
          </div>
          <a href="#" class="project-link">↗</a>
        </div>
      </div>
      <div class="project-card">
        <div class="project-img">
          <div class="project-img-bg"></div>
          <span class="project-img-label">Project Screenshot</span>
        </div>
        <div class="project-info">
          <div class="project-meta">
            <div class="project-num">02</div>
            <div class="project-name">Project Beta</div>
            <div class="project-type">UI/UX · Mobile App</div>
          </div>
          <a href="#" class="project-link">↗</a>
        </div>
      </div>
      <div class="project-card">
        <div class="project-img">
          <div class="project-img-bg"></div>
          <span class="project-img-label">Project Screenshot</span>
        </div>
        <div class="project-info">
          <div class="project-meta">
            <div class="project-num">03</div>
            <div class="project-name">Project Gamma</div>
            <div class="project-type">E-commerce · Frontend</div>
          </div>
          <a href="#" class="project-link">↗</a>
        </div>
      </div>
      <div class="project-card">
        <div class="project-img">
          <div class="project-img-bg"></div>
          <span class="project-img-label">Project Screenshot</span>
        </div>
        <div class="project-info">
          <div class="project-meta">
            <div class="project-num">04</div>
            <div class="project-name">Project Delta</div>
            <div class="project-type">Dashboard · Web App</div>
          </div>
          <a href="#" class="project-link">↗</a>
        </div>
      </div>
    </div>
  </section>

  <!-- EXPERIENCE -->
  <section id="experience">
    <div class="section-label">My journey</div>
    <h2 class="section-title">Experience</h2>
    <div class="exp-list">
      <div class="exp-item reveal">
        <div class="exp-period">2023 — Present</div>
        <div>
          <div class="exp-role">Senior Web Designer</div>
          <div class="exp-company">Company Name · Full-time</div>
          <div class="exp-desc">Led the visual redesign of the company's flagship product, improving conversion rates by 35%. Collaborated closely with dev teams to ensure pixel-perfect implementation of design systems.</div>
        </div>
        <div><span class="exp-badge">Current</span></div>
      </div>
      <div class="exp-item reveal">
        <div class="exp-period">2021 — 2023</div>
        <div>
          <div class="exp-role">UI/UX Designer</div>
          <div class="exp-company">Another Company · Full-time</div>
          <div class="exp-desc">Designed end-to-end user experiences for web and mobile clients across industries including fintech, e-commerce, and healthcare. Owned the design process from research to delivery.</div>
        </div>
        <div></div>
      </div>
      <div class="exp-item reveal">
        <div class="exp-period">2020 — 2021</div>
        <div>
          <div class="exp-role">Freelance Designer</div>
          <div class="exp-company">Self-employed · Remote</div>
          <div class="exp-desc">Worked with startups and small businesses to establish their visual identity and online presence. Delivered branding, landing pages, and marketing assets.</div>
        </div>
        <div></div>
      </div>
      <div class="exp-item reveal">
        <div class="exp-period">2019 — 2020</div>
        <div>
          <div class="exp-role">Junior Designer</div>
          <div class="exp-company">Creative Studio · Internship</div>
          <div class="exp-desc">Assisted senior designers on branding projects, built component libraries, and helped maintain design systems for enterprise clients.</div>
        </div>
        <div></div>
      </div>
    </div>
  </section>

  <!-- CONTACT -->
  <section id="contact">
    <div class="section-label">Let's talk</div>
    <h2 class="contact-headline">
      Got a project?<br>
      <span>Let's make it</span>
      happen.
    </h2>
    <a href="mailto:hello@yourname.com" class="contact-email">hello@yourname.com</a>
    <br>
    <a href="mailto:hello@yourname.com" class="hero-cta" style="display:inline-flex;margin-top:1rem;">
      Send me a message ↗
    </a>
    <div class="contact-social">
      <a href="#" class="social-link">↗ LinkedIn</a>
      <a href="#" class="social-link">↗ GitHub</a>
      <a href="#" class="social-link">↗ Dribbble</a>
      <a href="#" class="social-link">↗ Behance</a>
      <a href="#" class="social-link">↗ Twitter / X</a>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <p>© 2025 Your Name. All rights reserved.</p>
    <p>Designed &amp; built with ♥</p>
  </footer>

  <script>
    // Custom cursor
    const cursor = document.getElementById('cursor');
    const ring = document.getElementById('cursorRing');
    let mouseX = 0, mouseY = 0;
    let ringX = 0, ringY = 0;

    document.addEventListener('mousemove', e => {
      mouseX = e.clientX; mouseY = e.clientY;
      cursor.style.left = mouseX + 'px';
      cursor.style.top = mouseY + 'px';
    });

    function animateRing() {
      ringX += (mouseX - ringX) * 0.12;
      ringY += (mouseY - ringY) * 0.12;
      ring.style.left = ringX + 'px';
      ring.style.top = ringY + 'px';
      requestAnimationFrame(animateRing);
    }
    animateRing();

    document.querySelectorAll('a, button').forEach(el => {
      el.addEventListener('mouseenter', () => {
        cursor.style.width = '20px';
        cursor.style.height = '20px';
        cursor.style.background = 'var(--yellow)';
        ring.style.width = '52px';
        ring.style.height = '52px';
      });
      el.addEventListener('mouseleave', () => {
        cursor.style.width = '12px';
        cursor.style.height = '12px';
        cursor.style.background = 'var(--pink)';
        ring.style.width = '36px';
        ring.style.height = '36px';
      });
    });

    // Scroll reveal
    const reveals = document.querySelectorAll('.reveal');
    const observer = new IntersectionObserver(entries => {
      entries.forEach((entry, i) => {
        if (entry.isIntersecting) {
          setTimeout(() => {
            entry.target.classList.add('visible');
          }, i * 80);
          observer.unobserve(entry.target);
        }
      });
    }, { threshold: 0.12 });
    reveals.forEach(el => observer.observe(el));

    // Nav background on scroll
    const nav = document.querySelector('nav');
    window.addEventListener('scroll', () => {
      if (window.scrollY > 60) {
        nav.style.background = 'rgba(13,13,13,0.9)';
        nav.style.backdropFilter = 'blur(12px)';
        nav.style.mixBlendMode = 'normal';
        nav.querySelectorAll('a').forEach(a => a.style.color = '#F9F7F0');
      } else {
        nav.style.background = '';
        nav.style.backdropFilter = '';
        nav.style.mixBlendMode = 'multiply';
        nav.querySelectorAll('a').forEach(a => a.style.color = '');
      }
    });
  </script>
</body>
</html>