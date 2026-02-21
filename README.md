<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Devantix Labs — Engineering AI for a Smarter Tomorrow</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet">
<style>
  :root {
    --black: #080b10;
    --dark: #0d1117;
    --panel: #111827;
    --border: rgba(255,255,255,0.07);
    --accent: #00c2ff;
    --accent2: #7c6cfa;
    --white: #f0f4ff;
    --muted: #7a8599;
    --grad: linear-gradient(135deg, #00c2ff 0%, #7c6cfa 100%);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--black);
    color: var(--white);
    font-family: 'DM Sans', sans-serif;
    font-weight: 300;
    line-height: 1.7;
    overflow-x: hidden;
  }

  /* NOISE TEXTURE */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.03'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 0;
  }

  /* GLOW ORBS */
  .orb {
    position: fixed;
    border-radius: 50%;
    filter: blur(120px);
    pointer-events: none;
    z-index: 0;
  }
  .orb-1 { width: 500px; height: 500px; background: rgba(0,194,255,0.07); top: -150px; right: -100px; }
  .orb-2 { width: 400px; height: 400px; background: rgba(124,108,250,0.07); bottom: 200px; left: -100px; }

  /* LAYOUT */
  .container { max-width: 960px; margin: 0 auto; padding: 0 2rem; position: relative; z-index: 1; }

  /* NAV */
  nav {
    padding: 1.75rem 0;
    border-bottom: 1px solid var(--border);
    position: relative; z-index: 10;
  }
  .nav-inner {
    display: flex;
    align-items: center;
    justify-content: space-between;
    max-width: 960px;
    margin: 0 auto;
    padding: 0 2rem;
  }
  .logo {
    display: flex;
    align-items: center;
    gap: 0.6rem;
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 1.2rem;
    letter-spacing: -0.02em;
    color: var(--white);
    text-decoration: none;
  }
  .logo-icon {
    width: 32px; height: 32px;
    background: var(--grad);
    border-radius: 8px;
    display: grid;
    place-items: center;
    font-size: 0.9rem;
  }
  .nav-link {
    font-size: 0.85rem;
    color: var(--muted);
    text-decoration: none;
    letter-spacing: 0.05em;
    text-transform: uppercase;
    font-weight: 500;
    transition: color 0.2s;
  }
  .nav-link:hover { color: var(--white); }
  .nav-cta {
    background: var(--grad);
    color: var(--white);
    padding: 0.5rem 1.2rem;
    border-radius: 6px;
    font-size: 0.85rem;
    font-weight: 500;
    text-decoration: none;
    transition: opacity 0.2s;
  }
  .nav-cta:hover { opacity: 0.85; }

  /* HERO */
  .hero {
    padding: 7rem 0 5rem;
    position: relative;
  }
  .eyebrow {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    font-size: 0.75rem;
    font-weight: 500;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--accent);
    border: 1px solid rgba(0,194,255,0.25);
    padding: 0.35rem 0.9rem;
    border-radius: 999px;
    margin-bottom: 2rem;
    animation: fadeUp 0.6s ease both;
  }
  .eyebrow::before {
    content: '';
    width: 6px; height: 6px;
    background: var(--accent);
    border-radius: 50%;
    animation: pulse 2s infinite;
  }
  @keyframes pulse {
    0%, 100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.5; transform: scale(0.8); }
  }

  h1 {
    font-family: 'Syne', sans-serif;
    font-size: clamp(2.4rem, 5vw, 4rem);
    font-weight: 800;
    line-height: 1.1;
    letter-spacing: -0.03em;
    margin-bottom: 1.5rem;
    animation: fadeUp 0.6s 0.1s ease both;
  }
  h1 span {
    background: var(--grad);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }

  .hero-desc {
    max-width: 580px;
    font-size: 1.05rem;
    color: #9aaabb;
    margin-bottom: 2.5rem;
    animation: fadeUp 0.6s 0.2s ease both;
  }

  .hero-actions {
    display: flex;
    gap: 1rem;
    align-items: center;
    animation: fadeUp 0.6s 0.3s ease both;
  }

  .btn-primary {
    background: var(--grad);
    color: var(--white);
    padding: 0.8rem 2rem;
    border-radius: 8px;
    font-weight: 500;
    font-size: 0.95rem;
    text-decoration: none;
    transition: opacity 0.2s, transform 0.2s;
  }
  .btn-primary:hover { opacity: 0.85; transform: translateY(-1px); }

  .btn-secondary {
    color: var(--muted);
    font-size: 0.9rem;
    text-decoration: none;
    display: flex;
    align-items: center;
    gap: 0.4rem;
    transition: color 0.2s;
  }
  .btn-secondary:hover { color: var(--white); }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* DIVIDER LINE */
  .divider {
    height: 1px;
    background: var(--border);
    margin: 0;
  }

  /* SECTION */
  section { padding: 5rem 0; }
  .section-label {
    font-size: 0.72rem;
    font-weight: 600;
    letter-spacing: 0.14em;
    text-transform: uppercase;
    color: var(--accent2);
    margin-bottom: 0.75rem;
  }
  .section-title {
    font-family: 'Syne', sans-serif;
    font-size: clamp(1.6rem, 3vw, 2.2rem);
    font-weight: 700;
    letter-spacing: -0.025em;
    margin-bottom: 1rem;
    line-height: 1.2;
  }
  .section-desc {
    color: var(--muted);
    max-width: 520px;
    font-size: 0.95rem;
  }
  .section-header { margin-bottom: 3rem; }

  /* SERVICES GRID */
  .services-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 1px;
    background: var(--border);
    border: 1px solid var(--border);
    border-radius: 16px;
    overflow: hidden;
  }
  .service-card {
    background: var(--dark);
    padding: 2rem;
    transition: background 0.25s;
    position: relative;
    overflow: hidden;
  }
  .service-card::after {
    content: '';
    position: absolute;
    inset: 0;
    background: var(--grad);
    opacity: 0;
    transition: opacity 0.3s;
  }
  .service-card:hover { background: var(--panel); }
  .service-card:hover::after { opacity: 0.04; }

  .service-icon {
    width: 42px; height: 42px;
    border-radius: 10px;
    background: rgba(0,194,255,0.1);
    border: 1px solid rgba(0,194,255,0.15);
    display: grid;
    place-items: center;
    font-size: 1.2rem;
    margin-bottom: 1rem;
    position: relative; z-index: 1;
  }
  .service-card h3 {
    font-family: 'Syne', sans-serif;
    font-size: 1rem;
    font-weight: 700;
    margin-bottom: 0.5rem;
    position: relative; z-index: 1;
  }
  .service-card p {
    font-size: 0.88rem;
    color: var(--muted);
    line-height: 1.6;
    position: relative; z-index: 1;
  }

  /* TECH STACK */
  .tech-section { background: var(--panel); border-top: 1px solid var(--border); border-bottom: 1px solid var(--border); }
  .tech-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 0.75rem;
  }
  .tech-tag {
    padding: 0.45rem 1rem;
    border: 1px solid var(--border);
    border-radius: 6px;
    font-size: 0.82rem;
    color: #8899aa;
    background: rgba(255,255,255,0.03);
    font-weight: 400;
    letter-spacing: 0.02em;
    transition: border-color 0.2s, color 0.2s;
  }
  .tech-tag:hover { border-color: rgba(0,194,255,0.3); color: var(--white); }

  /* TEAM */
  .team-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
    gap: 1.5rem;
  }
  .team-card {
    background: var(--panel);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 2rem;
    transition: border-color 0.25s, transform 0.25s;
  }
  .team-card:hover { border-color: rgba(124,108,250,0.3); transform: translateY(-3px); }

  .team-avatar {
    width: 52px; height: 52px;
    border-radius: 12px;
    background: var(--grad);
    display: grid;
    place-items: center;
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 1.1rem;
    color: white;
    margin-bottom: 1.25rem;
  }
  .team-card h3 {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 1rem;
    margin-bottom: 0.25rem;
  }
  .team-card .role {
    font-size: 0.82rem;
    color: var(--accent);
    font-weight: 500;
    letter-spacing: 0.02em;
  }

  /* CONTACT */
  .contact-section {
    background: var(--dark);
  }
  .contact-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
    align-items: start;
  }
  @media (max-width: 680px) {
    .contact-grid { grid-template-columns: 1fr; gap: 2rem; }
  }
  .contact-item {
    display: flex;
    gap: 1rem;
    margin-bottom: 1.5rem;
    align-items: flex-start;
  }
  .contact-icon {
    width: 40px; height: 40px; flex-shrink: 0;
    border: 1px solid var(--border);
    border-radius: 8px;
    display: grid;
    place-items: center;
    font-size: 1rem;
    background: var(--panel);
  }
  .contact-item h4 {
    font-size: 0.75rem;
    font-weight: 500;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 0.2rem;
  }
  .contact-item p, .contact-item a {
    font-size: 0.9rem;
    color: var(--white);
    text-decoration: none;
  }
  .contact-item a:hover { color: var(--accent); }

  /* SOCIAL */
  .social-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 0.75rem;
  }
  .social-link {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    padding: 0.8rem 1rem;
    border: 1px solid var(--border);
    border-radius: 10px;
    text-decoration: none;
    color: var(--muted);
    font-size: 0.88rem;
    font-weight: 500;
    background: var(--panel);
    transition: border-color 0.2s, color 0.2s, transform 0.2s;
  }
  .social-link:hover { border-color: rgba(0,194,255,0.3); color: var(--white); transform: translateY(-1px); }
  .social-link span:first-child { font-size: 1rem; }

  /* FOOTER */
  footer {
    border-top: 1px solid var(--border);
    padding: 2.5rem 0;
  }
  .footer-inner {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 1rem;
    font-size: 0.82rem;
    color: var(--muted);
  }
  .footer-quote {
    font-style: italic;
    font-size: 0.8rem;
    color: #566070;
    max-width: 420px;
  }

  /* RESPONSIVE NAV */
  @media (max-width: 640px) {
    nav .nav-links { display: none; }
    h1 { font-size: 2.2rem; }
  }
</style>
</head>
<body>

<div class="orb orb-1"></div>
<div class="orb orb-2"></div>

<!-- NAV -->
<nav>
  <div class="nav-inner">
    <a href="https://www.devantixlabs.com" class="logo">
      <div class="logo-icon">⬡</div>
      Devantix Labs
    </a>
    <div class="nav-links" style="display:flex; gap:2rem; align-items:center;">
      <a href="#services" class="nav-link">Services</a>
      <a href="#team" class="nav-link">Team</a>
      <a href="#contact" class="nav-link">Contact</a>
      <a href="mailto:contact@devantixlabs.com" class="nav-cta">Get in Touch</a>
    </div>
  </div>
</nav>

<!-- HERO -->
<div class="container">
  <div class="hero">
    <div class="eyebrow">AI-Powered Software Engineering</div>
    <h1>Engineering AI for a<br><span>Smarter Tomorrow</span></h1>
    <p class="hero-desc">We build scalable, intelligent software solutions — from Generative AI to Predictive Analytics — powering enterprises across the globe with systems that think, adapt, and deliver.</p>
    <div class="hero-actions">
      <a href="mailto:contact@devantixlabs.com" class="btn-primary">Start a Project</a>
      <a href="https://www.devantixlabs.com" class="btn-secondary">Visit Website →</a>
    </div>
  </div>
</div>

<div class="divider"></div>

<!-- SERVICES -->
<section id="services">
  <div class="container">
    <div class="section-header">
      <div class="section-label">What We Do</div>
      <h2 class="section-title">Intelligent Solutions,<br>End to End</h2>
      <p class="section-desc">From cutting-edge AI models to production-grade software, we engineer complete systems built for scale.</p>
    </div>
    <div class="services-grid">
      <div class="service-card">
        <div class="service-icon">🧠</div>
        <h3>Generative AI</h3>
        <p>Automate content creation, design workflows, and code generation with state-of-the-art generative models tailored to your business.</p>
      </div>
      <div class="service-card">
        <div class="service-icon">💬</div>
        <h3>Conversational AI</h3>
        <p>LLM-powered assistants for customer support, internal operations, and user engagement — intelligent, context-aware, always available.</p>
      </div>
      <div class="service-card">
        <div class="service-icon">🔍</div>
        <h3>Natural Language Processing</h3>
        <p>Advanced chatbots, document summarization, and sentiment analysis pipelines that turn unstructured language into actionable insight.</p>
      </div>
      <div class="service-card">
        <div class="service-icon">📊</div>
        <h3>Predictive Analytics</h3>
        <p>Forecast demand, model churn, and track KPIs with precision-built ML models that give your teams a decisive edge.</p>
      </div>
      <div class="service-card">
        <div class="service-icon">⚙️</div>
        <h3>Recommender Systems</h3>
        <p>Personalized content and product discovery engines that learn from behavior and drive measurable conversion outcomes.</p>
      </div>
      <div class="service-card">
        <div class="service-icon">🖥</div>
        <h3>Full Stack Development</h3>
        <p>Cloud-ready, AI-integrated applications built with modern architectures — performant, maintainable, and engineered to grow.</p>
      </div>
    </div>
  </div>
</section>

<!-- TECH STACK -->
<div class="tech-section">
  <div class="container" style="padding-top:3.5rem; padding-bottom:3.5rem;">
    <div style="display:flex; justify-content:space-between; align-items:center; flex-wrap:wrap; gap:2rem; margin-bottom:1.75rem;">
      <div>
        <div class="section-label">Technology</div>
        <h2 class="section-title" style="margin-bottom:0;">Our Tech Stack</h2>
      </div>
    </div>
    <div class="tech-grid">
      <span class="tech-tag">Python</span>
      <span class="tech-tag">PyTorch</span>
      <span class="tech-tag">TensorFlow</span>
      <span class="tech-tag">LangChain</span>
      <span class="tech-tag">OpenAI API</span>
      <span class="tech-tag">Hugging Face</span>
      <span class="tech-tag">FastAPI</span>
      <span class="tech-tag">Node.js</span>
      <span class="tech-tag">React</span>
      <span class="tech-tag">Next.js</span>
      <span class="tech-tag">PostgreSQL</span>
      <span class="tech-tag">MongoDB</span>
      <span class="tech-tag">Redis</span>
      <span class="tech-tag">AWS</span>
      <span class="tech-tag">GCP</span>
      <span class="tech-tag">Docker</span>
      <span class="tech-tag">Kubernetes</span>
      <span class="tech-tag">Terraform</span>
      <span class="tech-tag">Pinecone</span>
      <span class="tech-tag">MLflow</span>
    </div>
  </div>
</div>

<!-- TEAM -->
<section id="team">
  <div class="container">
    <div class="section-header">
      <div class="section-label">Our Team</div>
      <h2 class="section-title">The Minds Behind<br>Devantix</h2>
      <p class="section-desc">A tight-knit team of engineers and researchers passionate about building AI that matters.</p>
    </div>
    <div class="team-grid">
      <div class="team-card">
        <div class="team-avatar">AD</div>
        <h3>Abdullah Dar</h3>
        <div class="role">Founder & Chief AI Architect</div>
      </div>
      <div class="team-card">
        <div class="team-avatar">QM</div>
        <h3>Qaisar Mateen</h3>
        <div class="role">Lead Machine Learning Engineer</div>
      </div>
      <div class="team-card">
        <div class="team-avatar">UF</div>
        <h3>Usman Faisal</h3>
        <div class="role">Head of Engineering</div>
      </div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact" class="contact-section">
  <div class="container">
    <div class="section-header">
      <div class="section-label">Get in Touch</div>
      <h2 class="section-title">Let's Build Something<br>Remarkable</h2>
    </div>
    <div class="contact-grid">
      <div>
        <div class="contact-item">
          <div class="contact-icon">📍</div>
          <div>
            <h4>Office</h4>
            <p>Office #09, 3rd Floor, Vertex Mall<br>C Sector Commercial, Bahria Town<br>Lahore, Pakistan</p>
          </div>
        </div>
        <div class="contact-item">
          <div class="contact-icon">✉️</div>
          <div>
            <h4>Email</h4>
            <a href="mailto:contact@devantixlabs.com">contact@devantixlabs.com</a>
          </div>
        </div>
        <div class="contact-item">
          <div class="contact-icon">🌐</div>
          <div>
            <h4>Web</h4>
            <a href="https://www.devantixlabs.com" target="_blank">www.devantixlabs.com</a>
          </div>
        </div>
      </div>
      <div>
        <p style="font-size:0.82rem; color:var(--muted); text-transform:uppercase; letter-spacing:0.1em; font-weight:500; margin-bottom:1rem;">Follow Us</p>
        <div class="social-grid">
          <a href="#" class="social-link"><span>🔗</span> LinkedIn</a>
          <a href="#" class="social-link"><span>📸</span> Instagram</a>
          <a href="#" class="social-link"><span>📘</span> Facebook</a>
          <a href="#" class="social-link"><span>𝕏</span> X / Twitter</a>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="container">
    <div class="footer-inner">
      <div class="logo" style="font-family:'Syne',sans-serif; font-weight:800; font-size:1rem; color:var(--muted); display:flex; align-items:center; gap:0.5rem; text-decoration:none;">
        <div class="logo-icon" style="width:24px;height:24px;font-size:0.7rem;">⬡</div>
        Devantix Labs
      </div>
      <p class="footer-quote">"Creating AI that empowers enterprises — intelligently, ethically, and beautifully."</p>
      <span>© 2025 Devantix Labs</span>
    </div>
  </div>
</footer>

</body>
</html>
