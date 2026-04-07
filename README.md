# abconcrete.co
Concrete Website
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Above & Beyond Concrete</title>
  <link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Barlow:wght@300;400;500;600&family=Barlow+Condensed:wght@500;700&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --bg:        #0d0d0d;
      --surface:   #141414;
      --card:      #1a1a1a;
      --border:    #2a2a2a;
      --gold:      #c8972a;
      --gold-light:#e0b84a;
      --white:     #f0ede8;
      --muted:     #888;
      --text:      #d4d0ca;
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    html { scroll-behavior: smooth; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: 'Barlow', sans-serif;
      font-weight: 300;
      overflow-x: hidden;
    }

    /* ── NAV ── */
    nav {
      position: fixed; top: 0; left: 0; right: 0; z-index: 100;
      display: flex; align-items: center; justify-content: space-between;
      padding: 0 5%;
      height: 72px;
      background: rgba(13,13,13,0.92);
      backdrop-filter: blur(12px);
      border-bottom: 1px solid var(--border);
      transition: background 0.3s;
    }
    .nav-logo {
      display: flex; flex-direction: column; line-height: 1;
    }
    .nav-logo span:first-child {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 1.55rem;
      color: var(--white);
      letter-spacing: 0.04em;
    }
    .nav-logo span:last-child {
      font-family: 'Barlow Condensed', sans-serif;
      font-size: 0.65rem;
      letter-spacing: 0.22em;
      text-transform: uppercase;
      color: var(--gold);
    }
    .nav-links {
      display: flex; gap: 2.4rem; list-style: none;
    }
    .nav-links a {
      color: var(--muted);
      text-decoration: none;
      font-size: 0.78rem;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      font-weight: 500;
      transition: color 0.2s;
    }
    .nav-links a:hover { color: var(--gold); }

    .nav-cta {
      background: var(--gold);
      color: #000;
      padding: 0.5rem 1.3rem;
      font-family: 'Barlow Condensed', sans-serif;
      font-size: 0.8rem;
      font-weight: 700;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      text-decoration: none;
      border: none;
      cursor: pointer;
      transition: background 0.2s, transform 0.1s;
    }
    .nav-cta:hover { background: var(--gold-light); transform: translateY(-1px); }

    /* hamburger */
    .hamburger { display: none; flex-direction: column; gap: 5px; cursor: pointer; }
    .hamburger span {
      display: block; width: 24px; height: 2px;
      background: var(--white); transition: 0.3s;
    }

    /* ── HERO ── */
    #hero {
      min-height: 100vh;
      display: flex; align-items: center;
      position: relative; overflow: hidden;
      padding: 0 5%;
    }
    .hero-bg {
      position: absolute; inset: 0; z-index: 0;
      background:
        radial-gradient(ellipse 70% 60% at 80% 50%, rgba(200,151,42,0.08) 0%, transparent 70%),
        repeating-linear-gradient(
          0deg,
          transparent,
          transparent 59px,
          rgba(255,255,255,0.02) 60px
        ),
        repeating-linear-gradient(
          90deg,
          transparent,
          transparent 59px,
          rgba(255,255,255,0.02) 60px
        );
    }
    .hero-bg::after {
      content: '';
      position: absolute; inset: 0;
      background: linear-gradient(135deg, rgba(13,13,13,0.7) 40%, transparent 100%);
    }
    .hero-content {
      position: relative; z-index: 1;
      max-width: 720px;
    }
    .hero-tag {
      display: inline-block;
      font-family: 'Barlow Condensed', sans-serif;
      font-size: 0.72rem;
      letter-spacing: 0.28em;
      text-transform: uppercase;
      color: var(--gold);
      border: 1px solid var(--gold);
      padding: 0.3rem 0.9rem;
      margin-bottom: 1.8rem;
      opacity: 0; animation: fadeUp 0.7s 0.2s forwards;
    }
    .hero-title {
      font-family: 'Bebas Neue', sans-serif;
      font-size: clamp(3.8rem, 9vw, 8rem);
      line-height: 0.92;
      color: var(--white);
      letter-spacing: 0.01em;
      margin-bottom: 1.6rem;
      opacity: 0; animation: fadeUp 0.7s 0.4s forwards;
    }
    .hero-title em {
      font-style: normal;
      color: var(--gold);
    }
    .hero-sub {
      font-size: 1.05rem;
      font-weight: 300;
      color: var(--muted);
      line-height: 1.7;
      max-width: 500px;
      margin-bottom: 2.6rem;
      opacity: 0; animation: fadeUp 0.7s 0.6s forwards;
    }
    .hero-btns {
      display: flex; gap: 1rem; flex-wrap: wrap;
      opacity: 0; animation: fadeUp 0.7s 0.8s forwards;
    }
    .btn-primary {
      background: var(--gold);
      color: #000;
      padding: 0.85rem 2.2rem;
      font-family: 'Barlow Condensed', sans-serif;
      font-size: 0.85rem;
      font-weight: 700;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      text-decoration: none;
      transition: background 0.2s, transform 0.1s;
    }
    .btn-primary:hover { background: var(--gold-light); transform: translateY(-2px); }
    .btn-outline {
      border: 1px solid var(--border);
      color: var(--white);
      padding: 0.85rem 2.2rem;
      font-family: 'Barlow Condensed', sans-serif;
      font-size: 0.85rem;
      font-weight: 700;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      text-decoration: none;
      transition: border-color 0.2s, color 0.2s;
    }
    .btn-outline:hover { border-color: var(--gold); color: var(--gold); }

    .hero-stats {
      position: absolute; bottom: 3rem; right: 5%;
      display: flex; gap: 3rem;
      opacity: 0; animation: fadeUp 0.7s 1s forwards;
    }
    .stat { text-align: center; }
    .stat-num {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 2.6rem;
      color: var(--gold);
      line-height: 1;
    }
    .stat-label {
      font-size: 0.68rem;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      color: var(--muted);
      margin-top: 0.2rem;
    }

    /* ── SECTION COMMON ── */
    section { padding: 7rem 5%; }
    .section-tag {
      font-family: 'Barlow Condensed', sans-serif;
      font-size: 0.72rem;
      letter-spacing: 0.28em;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: 0.8rem;
    }
    .section-title {
      font-family: 'Bebas Neue', sans-serif;
      font-size: clamp(2.2rem, 5vw, 3.8rem);
      color: var(--white);
      line-height: 1.05;
      letter-spacing: 0.02em;
      margin-bottom: 1.2rem;
    }
    .section-desc {
      color: var(--muted);
      font-size: 1rem;
      line-height: 1.75;
      max-width: 520px;
    }
    .divider {
      width: 48px; height: 2px;
      background: var(--gold);
      margin: 1.4rem 0;
    }

    /* ── SERVICES ── */
    #services { background: var(--surface); }
    .services-header {
      display: flex; justify-content: space-between;
      align-items: flex-end; flex-wrap: wrap; gap: 2rem;
      margin-bottom: 4rem;
    }
    .services-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 1.5px;
      background: var(--border);
    }
    .service-card {
      background: var(--card);
      padding: 2.4rem 2rem;
      position: relative;
      overflow: hidden;
      transition: background 0.3s;
    }
    .service-card::before {
      content: '';
      position: absolute; top: 0; left: 0; right: 0;
      height: 2px;
      background: var(--gold);
      transform: scaleX(0); transform-origin: left;
      transition: transform 0.35s ease;
    }
    .service-card:hover { background: #1f1f1f; }
    .service-card:hover::before { transform: scaleX(1); }
    .service-icon {
      font-size: 2rem;
      margin-bottom: 1.2rem;
      display: block;
    }
    .service-num {
      position: absolute; top: 1.6rem; right: 1.8rem;
      font-family: 'Bebas Neue', sans-serif;
      font-size: 3.5rem;
      color: rgba(200,151,42,0.07);
      line-height: 1;
      pointer-events: none;
    }
    .service-name {
      font-family: 'Barlow Condensed', sans-serif;
      font-size: 1.25rem;
      font-weight: 700;
      letter-spacing: 0.06em;
      text-transform: uppercase;
      color: var(--white);
      margin-bottom: 0.7rem;
    }
    .service-desc {
      color: var(--muted);
      font-size: 0.88rem;
      line-height: 1.7;
    }

    /* ── WORK ── */
    #work { background: var(--bg); }
    .work-header { margin-bottom: 3rem; }
    .work-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      grid-template-rows: 260px 260px;
      gap: 1.5px;
      background: var(--border);
    }
    .work-item {
      position: relative; overflow: hidden;
      background: var(--card);
      cursor: pointer;
    }
    .work-item:first-child {
      grid-row: span 2;
    }
    .work-placeholder {
      width: 100%; height: 100%;
      display: flex; flex-direction: column;
      align-items: center; justify-content: center;
      gap: 0.6rem;
      background: linear-gradient(135deg, var(--card) 0%, #222 100%);
      transition: transform 0.4s ease;
    }
    .work-item:hover .work-placeholder { transform: scale(1.03); }
    .work-placeholder-icon {
      font-size: 2.4rem;
      opacity: 0.25;
    }
    .work-placeholder-text {
      font-family: 'Barlow Condensed', sans-serif;
      font-size: 0.72rem;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--muted);
    }
    .work-overlay {
      position: absolute; inset: 0;
      background: linear-gradient(to top, rgba(0,0,0,0.85) 0%, transparent 55%);
      display: flex; flex-direction: column;
      justify-content: flex-end;
      padding: 1.4rem;
      opacity: 0; transition: opacity 0.3s;
    }
    .work-item:hover .work-overlay { opacity: 1; }
    .work-label {
      font-family: 'Barlow Condensed', sans-serif;
      font-size: 1rem;
      font-weight: 700;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      color: var(--white);
    }
    .work-sub {
      font-size: 0.75rem;
      color: var(--gold);
      letter-spacing: 0.14em;
      text-transform: uppercase;
      margin-top: 0.2rem;
    }
    .work-note {
      text-align: center;
      margin-top: 2rem;
      color: var(--muted);
      font-size: 0.82rem;
      letter-spacing: 0.08em;
      font-style: italic;
    }

    /* ── PROCESS ── */
    #process { background: var(--surface); }
    .process-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 0;
      margin-top: 4rem;
      position: relative;
    }
    .process-grid::before {
      content: '';
      position: absolute;
      top: 2.2rem; left: 0; right: 0;
      height: 1px;
      background: var(--border);
    }
    .process-step {
      padding: 0 2rem 2rem 0;
      position: relative;
    }
    .step-num {
      width: 44px; height: 44px;
      border: 1px solid var(--gold);
      border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      font-family: 'Bebas Neue', sans-serif;
      font-size: 1.1rem;
      color: var(--gold);
      background: var(--surface);
      position: relative; z-index: 1;
      margin-bottom: 1.6rem;
    }
    .step-title {
      font-family: 'Barlow Condensed', sans-serif;
      font-size: 1.05rem;
      font-weight: 700;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      color: var(--white);
      margin-bottom: 0.6rem;
    }
    .step-desc {
      font-size: 0.85rem;
      color: var(--muted);
      line-height: 1.7;
    }

    /* ── WHY US ── */
    #why { background: var(--bg); }
    .why-inner {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 6rem;
      align-items: center;
    }
    .why-visual {
      position: relative;
      height: 420px;
    }
    .why-block {
      position: absolute;
      background: var(--card);
      border: 1px solid var(--border);
    }
    .why-block:nth-child(1) {
      top: 0; left: 0; right: 60px; bottom: 60px;
      display: flex; align-items: center; justify-content: center;
      flex-direction: column; gap: 0.4rem;
    }
    .why-block:nth-child(2) {
      bottom: 0; right: 0;
      width: 180px; height: 180px;
      border-color: var(--gold);
      display: flex; align-items: center; justify-content: center;
      flex-direction: column;
    }
    .why-block-num {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 4rem;
      color: var(--gold);
      line-height: 1;
    }
    .why-block-label {
      font-size: 0.72rem;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      color: var(--muted);
    }
    .why-block-icon {
      font-size: 3.5rem;
      opacity: 0.12;
    }
    .why-list {
      list-style: none;
      margin-top: 2.5rem;
      display: flex; flex-direction: column; gap: 1rem;
    }
    .why-item {
      display: flex; gap: 1rem; align-items: flex-start;
    }
    .why-check {
      width: 22px; height: 22px;
      min-width: 22px;
      background: rgba(200,151,42,0.15);
      border: 1px solid var(--gold);
      display: flex; align-items: center; justify-content: center;
      font-size: 0.7rem;
      color: var(--gold);
      margin-top: 0.1rem;
    }
    .why-text {
      font-size: 0.9rem;
      color: var(--text);
      line-height: 1.6;
    }
    .why-text strong {
      color: var(--white);
      font-weight: 600;
    }

    /* ── CONTACT ── */
    #contact { background: var(--surface); }
    .contact-inner {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 5rem;
      align-items: start;
    }
    .contact-info { padding-top: 0.5rem; }
    .contact-item {
      display: flex; gap: 1.2rem;
      align-items: flex-start;
      margin-bottom: 2rem;
    }
    .contact-icon {
      width: 42px; height: 42px; min-width: 42px;
      border: 1px solid var(--border);
      display: flex; align-items: center; justify-content: center;
      font-size: 1.1rem;
      color: var(--gold);
    }
    .contact-detail-label {
      font-family: 'Barlow Condensed', sans-serif;
      font-size: 0.68rem;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--muted);
      margin-bottom: 0.2rem;
    }
    .contact-detail-val {
      color: var(--white);
      font-size: 0.95rem;
    }
    .contact-form { display: flex; flex-direction: column; gap: 1rem; }
    .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; }
    .form-group { display: flex; flex-direction: column; gap: 0.4rem; }
    .form-label {
      font-size: 0.68rem;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      color: var(--muted);
    }
    .form-input, .form-select, .form-textarea {
      background: var(--card);
      border: 1px solid var(--border);
      color: var(--white);
      padding: 0.75rem 1rem;
      font-family: 'Barlow', sans-serif;
      font-size: 0.9rem;
      outline: none;
      transition: border-color 0.2s;
      width: 100%;
    }
    .form-input::placeholder, .form-textarea::placeholder { color: #444; }
    .form-input:focus, .form-select:focus, .form-textarea:focus {
      border-color: var(--gold);
    }
    .form-select { appearance: none; cursor: pointer; }
    .form-textarea { resize: vertical; min-height: 120px; }
    .form-submit {
      background: var(--gold);
      color: #000;
      border: none;
      padding: 1rem 2rem;
      font-family: 'Barlow Condensed', sans-serif;
      font-size: 0.9rem;
      font-weight: 700;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      cursor: pointer;
      transition: background 0.2s, transform 0.1s;
      align-self: flex-start;
    }
    .form-submit:hover { background: var(--gold-light); transform: translateY(-2px); }

    /* ── FOOTER ── */
    footer {
      background: #0a0a0a;
      border-top: 1px solid var(--border);
      padding: 2.4rem 5%;
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      gap: 1rem;
    }
    .footer-logo span:first-child {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 1.3rem;
      color: var(--white);
      letter-spacing: 0.04em;
    }
    .footer-logo span:last-child {
      font-family: 'Barlow Condensed', sans-serif;
      font-size: 0.6rem;
      letter-spacing: 0.22em;
      text-transform: uppercase;
      color: var(--gold);
      display: block;
    }
    .footer-copy {
      font-size: 0.75rem;
      color: var(--muted);
      letter-spacing: 0.05em;
    }
    .footer-links {
      display: flex; gap: 2rem; list-style: none;
    }
    .footer-links a {
      font-size: 0.72rem;
      letter-spacing: 0.14em;
      text-transform: uppercase;
      color: var(--muted);
      text-decoration: none;
      transition: color 0.2s;
    }
    .footer-links a:hover { color: var(--gold); }

    /* ── ANIMATIONS ── */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(24px); }
      to   { opacity: 1; transform: translateY(0); }
    }
    .reveal {
      opacity: 0; transform: translateY(30px);
      transition: opacity 0.7s ease, transform 0.7s ease;
    }
    .reveal.visible { opacity: 1; transform: none; }

    /* ── MOBILE ── */
    @media (max-width: 768px) {
      .nav-links, .nav-cta { display: none; }
      .hamburger { display: flex; }
      .hero-stats { position: static; flex-wrap: wrap; gap: 2rem; margin-top: 3rem; justify-content: flex-start; }
      .work-grid { grid-template-columns: 1fr 1fr; grid-template-rows: auto; }
      .work-item:first-child { grid-row: auto; }
      .why-inner, .contact-inner { grid-template-columns: 1fr; gap: 3rem; }
      .why-visual { height: 260px; }
      .form-row { grid-template-columns: 1fr; }
      footer { flex-direction: column; text-align: center; }
      .process-grid::before { display: none; }
    }
  </style>
</head>
<body>

  <!-- NAV -->
  <nav>
    <div class="nav-logo">
      <span>A&amp;B Concrete</span>
      <span>Above &amp; Beyond</span>
    </div>
    <ul class="nav-links">
      <li><a href="#services">Services</a></li>
      <li><a href="#work">Our Work</a></li>
      <li><a href="#process">Process</a></li>
      <li><a href="#why">Why Us</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
    <a href="#contact" class="nav-cta">Get a Quote</a>
    <div class="hamburger" onclick="toggleMenu()">
      <span></span><span></span><span></span>
    </div>
  </nav>

  <!-- HERO -->
  <section id="hero">
    <div class="hero-bg"></div>
    <div class="hero-content">
      <div class="hero-tag">Hamilton &amp; Surrounding Areas</div>
      <h1 class="hero-title">
        Concrete<br><em>Built to</em><br>Last.
      </h1>
      <p class="hero-sub">
        From residential patios and driveways to industrial warehouse floors —
        we pour precision into every project, every time.
      </p>
      <div class="hero-btns">
        <a href="#contact" class="btn-primary">Get a Free Quote</a>
        <a href="#work" class="btn-outline">View Our Work</a>
      </div>
    </div>
    <div class="hero-stats">
      <div class="stat">
        <div class="stat-num">10+</div>
        <div class="stat-label">Years Experience</div>
      </div>
      <div class="stat">
        <div class="stat-num">500+</div>
        <div class="stat-label">Projects Done</div>
      </div>
      <div class="stat">
        <div class="stat-num">100%</div>
        <div class="stat-label">Satisfaction</div>
      </div>
    </div>
  </section>

  <!-- SERVICES -->
  <section id="services">
    <div class="services-header reveal">
      <div>
        <div class="section-tag">What We Do</div>
        <h2 class="section-title">Our Services</h2>
        <div class="divider"></div>
        <p class="section-desc">
          Residential or industrial — we bring the same level of craftsmanship
          and attention to detail to every pour.
        </p>
      </div>
    </div>
    <div class="services-grid reveal">
      <div class="service-card">
        <span class="service-num">01</span>
        <span class="service-icon">🏠</span>
        <div class="service-name">Concrete Pads</div>
        <p class="service-desc">Garage pads, shed bases, equipment pads — built solid and level from the ground up.</p>
      </div>
      <div class="service-card">
        <span class="service-num">02</span>
        <span class="service-icon">🪨</span>
        <div class="service-name">Patios</div>
        <p class="service-desc">Custom stamped, brushed, or exposed aggregate patios that transform your outdoor space.</p>
      </div>
      <div class="service-card">
        <span class="service-num">03</span>
        <span class="service-icon">🚗</span>
        <div class="service-name">Driveways</div>
        <p class="service-desc">Durable, clean driveways engineered for heavy loads and long-term performance.</p>
      </div>
      <div class="service-card">
        <span class="service-num">04</span>
        <span class="service-icon">🏭</span>
        <div class="service-name">Warehouse Floors</div>
        <p class="service-desc">High-strength industrial slabs built to handle forklifts, racking systems, and heavy daily use.</p>
      </div>
      <div class="service-card">
        <span class="service-num">05</span>
        <span class="service-icon">🏗️</span>
        <div class="service-name">Commercial &amp; Industrial</div>
        <p class="service-desc">Large-scale concrete work for commercial developments, loading docks, and industrial facilities.</p>
      </div>
      <div class="service-card">
        <span class="service-num">06</span>
        <span class="service-icon">🔧</span>
        <div class="service-name">Repairs &amp; Resurfacing</div>
        <p class="service-desc">Cracked or deteriorating concrete? We restore and resurface to like-new condition.</p>
      </div>
    </div>
  </section>

  <!-- WORK -->
  <section id="work">
    <div class="work-header reveal">
      <div class="section-tag">Portfolio</div>
      <h2 class="section-title">Our Work</h2>
      <div class="divider"></div>
      <p class="section-desc">A sample of the projects we're proud of. Photos coming soon.</p>
    </div>
    <div class="work-grid reveal">
      <div class="work-item">
        <div class="work-placeholder">
          <div class="work-placeholder-icon">📷</div>
          <div class="work-placeholder-text">Photo Coming Soon</div>
        </div>
        <div class="work-overlay">
          <div class="work-label">Residential Driveway</div>
          <div class="work-sub">Exposed Aggregate Finish</div>
        </div>
      </div>
      <div class="work-item">
        <div class="work-placeholder">
          <div class="work-placeholder-icon">📷</div>
          <div class="work-placeholder-text">Photo Coming Soon</div>
        </div>
        <div class="work-overlay">
          <div class="work-label">Stamped Patio</div>
          <div class="work-sub">Backyard Renovation</div>
        </div>
      </div>
      <div class="work-item">
        <div class="work-placeholder">
          <div class="work-placeholder-icon">📷</div>
          <div class="work-placeholder-text">Photo Coming Soon</div>
        </div>
        <div class="work-overlay">
          <div class="work-label">Warehouse Floor</div>
          <div class="work-sub">Industrial — 12,000 sq ft</div>
        </div>
      </div>
      <div class="work-item">
        <div class="work-placeholder">
          <div class="work-placeholder-icon">📷</div>
          <div class="work-placeholder-text">Photo Coming Soon</div>
        </div>
        <div class="work-overlay">
          <div class="work-label">Garage Pad</div>
          <div class="work-sub">Double Garage — Broom Finish</div>
        </div>
      </div>
      <div class="work-item">
        <div class="work-placeholder">
          <div class="work-placeholder-icon">📷</div>
          <div class="work-placeholder-text">Photo Coming Soon</div>
        </div>
        <div class="work-overlay">
          <div class="work-label">Commercial Loading Dock</div>
          <div class="work-sub">Heavy-Duty Industrial</div>
        </div>
      </div>
    </div>
    <p class="work-note reveal">More photos coming soon — check back or follow us on social media.</p>
  </section>

  <!-- PROCESS -->
  <section id="process">
    <div class="reveal">
      <div class="section-tag">How It Works</div>
      <h2 class="section-title">Our Process</h2>
      <div class="divider"></div>
      <p class="section-desc">We keep things simple, transparent, and on schedule.</p>
    </div>
    <div class="process-grid reveal">
      <div class="process-step">
        <div class="step-num">1</div>
        <div class="step-title">Free Consultation</div>
        <p class="step-desc">We come to your site, assess the project, and answer all your questions — no obligation.</p>
      </div>
      <div class="process-step">
        <div class="step-num">2</div>
        <div class="step-title">Quote &amp; Plan</div>
        <p class="step-desc">You receive a detailed, transparent quote with timelines. No hidden fees or surprises.</p>
      </div>
      <div class="process-step">
        <div class="step-num">3</div>
        <div class="step-title">Prep &amp; Pour</div>
        <p class="step-desc">We prepare the base, set forms, and pour to spec — clean, efficient, and professional.</p>
      </div>
      <div class="process-step">
        <div class="step-num">4</div>
        <div class="step-title">Finish &amp; Cure</div>
        <p class="step-desc">Proper finishing and curing ensures your concrete looks great and lasts for decades.</p>
      </div>
    </div>
  </section>

  <!-- WHY US -->
  <section id="why">
    <div class="why-inner">
      <div class="why-visual reveal">
        <div class="why-block">
          <div class="why-block-icon">🏗️</div>
        </div>
        <div class="why-block">
          <div class="why-block-num">A+</div>
          <div class="why-block-label">Quality</div>
        </div>
      </div>
      <div class="reveal">
        <div class="section-tag">Why Choose Us</div>
        <h2 class="section-title">Above &amp; Beyond Every Time</h2>
        <div class="divider"></div>
        <p class="section-desc">
          We don't cut corners. Every job gets the same attention and quality —
          whether it's a backyard patio or a 20,000 sq ft industrial floor.
        </p>
        <ul class="why-list">
          <li class="why-item">
            <div class="why-check">✓</div>
            <div class="why-text"><strong>Locally Owned &amp; Operated</strong> — we're your neighbours, and we take pride in our community's infrastructure.</div>
          </li>
          <li class="why-item">
            <div class="why-check">✓</div>
            <div class="why-text"><strong>Fully Insured</strong> — residential and commercial coverage so you're always protected.</div>
          </li>
          <li class="why-item">
            <div class="why-check">✓</div>
            <div class="why-text"><strong>On-Time Delivery</strong> — we respect your schedule and stick to agreed timelines.</div>
          </li>
          <li class="why-item">
            <div class="why-check">✓</div>
            <div class="why-text"><strong>Quality Materials</strong> — we source the right mix for every application, residential or industrial.</div>
          </li>
          <li class="why-item">
            <div class="why-check">✓</div>
            <div class="why-text"><strong>Fair, Transparent Pricing</strong> — you know exactly what you're paying for before we start.</div>
          </li>
        </ul>
      </div>
    </div>
  </section>

  <!-- CONTACT -->
  <section id="contact">
    <div class="contact-inner">
      <div class="reveal">
        <div class="section-tag">Get In Touch</div>
        <h2 class="section-title">Request a Free Quote</h2>
        <div class="divider"></div>
        <p class="section-desc">
          Ready to start your project? Reach out and we'll get back to you within 24 hours.
        </p>
        <div class="contact-info" style="margin-top:2.5rem;">
          <div class="contact-item">
            <div class="contact-icon">📞</div>
            <div>
              <div class="contact-detail-label">Phone</div>
              <div class="contact-detail-val">Add your number here</div>
            </div>
          </div>
          <div class="contact-item">
            <div class="contact-icon">✉️</div>
            <div>
              <div class="contact-detail-label">Email</div>
              <div class="contact-detail-val">Add your email here</div>
            </div>
          </div>
          <div class="contact-item">
            <div class="contact-icon">📍</div>
            <div>
              <div class="contact-detail-label">Service Area</div>
              <div class="contact-detail-val">Hamilton &amp; Surrounding Areas</div>
            </div>
          </div>
        </div>
      </div>
      <div class="reveal">
        <form class="contact-form" onsubmit="handleSubmit(event)">
          <div class="form-row">
            <div class="form-group">
              <label class="form-label">First Name</label>
              <input type="text" class="form-input" placeholder="John" required />
            </div>
            <div class="form-group">
              <label class="form-label">Last Name</label>
              <input type="text" class="form-input" placeholder="Smith" required />
            </div>
          </div>
          <div class="form-group">
            <label class="form-label">Email</label>
            <input type="email" class="form-input" placeholder="john@email.com" required />
          </div>
          <div class="form-group">
            <label class="form-label">Phone</label>
            <input type="tel" class="form-input" placeholder="(905) 555-0000" />
          </div>
          <div class="form-group">
            <label class="form-label">Service Needed</label>
            <select class="form-select form-input">
              <option value="" disabled selected>Select a service…</option>
              <option>Concrete Pad</option>
              <option>Patio</option>
              <option>Driveway</option>
              <option>Warehouse / Industrial Floor</option>
              <option>Commercial Project</option>
              <option>Repair / Resurfacing</option>
              <option>Other</option>
            </select>
          </div>
          <div class="form-group">
            <label class="form-label">Project Details</label>
            <textarea class="form-textarea" placeholder="Tell us about your project — size, location, timeline…"></textarea>
          </div>
          <button type="submit" class="form-submit">Send Message →</button>
        </form>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <div class="footer-logo">
      <span>A&amp;B Concrete</span>
      <span>Above &amp; Beyond Concrete</span>
    </div>
    <ul class="footer-links">
      <li><a href="#services">Services</a></li>
      <li><a href="#work">Work</a></li>
      <li><a href="#process">Process</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
    <p class="footer-copy">© 2025 Above &amp; Beyond Concrete. All rights reserved.</p>
  </footer>

  <script>
    // Scroll reveal
    const reveals = document.querySelectorAll('.reveal');
    const io = new IntersectionObserver((entries) => {
      entries.forEach(e => {
        if (e.isIntersecting) { e.target.classList.add('visible'); io.unobserve(e.target); }
      });
    }, { threshold: 0.12 });
    reveals.forEach(r => io.observe(r));

    // Form
    function handleSubmit(e) {
      e.preventDefault();
      const btn = e.target.querySelector('.form-submit');
      btn.textContent = 'Message Sent ✓';
      btn.style.background = '#2a7a2a';
      btn.style.color = '#fff';
      setTimeout(() => { btn.textContent = 'Send Message →'; btn.style.background = ''; btn.style.color = ''; }, 3000);
    }

    // Mobile menu toggle (basic)
    function toggleMenu() {
      const links = document.querySelector('.nav-links');
      const cta = document.querySelector('.nav-cta');
      if (links.style.display === 'flex') {
        links.style.display = ''; cta.style.display = '';
      } else {
        links.style.display = 'flex';
        links.style.flexDirection = 'column';
        links.style.position = 'fixed';
        links.style.top = '72px'; links.style.left = '0'; links.style.right = '0';
        links.style.background = '#0d0d0d';
        links.style.padding = '1.5rem 5%';
        links.style.borderBottom = '1px solid #2a2a2a';
        cta.style.display = 'block';
      }
    }
  </script>
</body>
</html>
