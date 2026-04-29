<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Emmanuel Moncada Alvarez</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Mono:wght@300;400&family=DM+Sans:ital,wght@0,300;0,400;1,300&display=swap" rel="stylesheet">
<style>
  :root {
    --navy: #020d1a;
    --deep: #041428;
    --mid: #082240;
    --blue: #0a4b8c;
    --bright: #1a7fd4;
    --ice: #4db8ff;
    --glow: #7dd4fc;
    --white: #e8f4ff;
    --muted: #7a9ab8;
    --accent: #00d4aa;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--navy);
    color: var(--white);
    font-family: 'DM Sans', sans-serif;
    font-weight: 300;
    line-height: 1.7;
    overflow-x: hidden;
  }

  /* ── Neural background canvas ── */
  #neural-bg {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    z-index: 0;
    opacity: 0.18;
  }

  /* ── Layout ── */
  .page {
    position: relative;
    z-index: 1;
    max-width: 900px;
    margin: 0 auto;
    padding: 0 2rem;
  }

  /* ── Nav ── */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    padding: 1.2rem 3rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: linear-gradient(to bottom, rgba(2,13,26,0.95), transparent);
    backdrop-filter: blur(6px);
  }

  .nav-logo {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 0.85rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--ice);
  }

  .nav-links {
    display: flex;
    gap: 2.5rem;
    list-style: none;
  }

  .nav-links a {
    font-family: 'DM Mono', monospace;
    font-size: 0.72rem;
    color: var(--muted);
    text-decoration: none;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    transition: color 0.2s;
  }

  .nav-links a:hover { color: var(--glow); }

  /* ── Hero ── */
  #hero {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding-top: 5rem;
    padding-bottom: 4rem;
  }

  .hero-label {
    font-family: 'DM Mono', monospace;
    font-size: 0.72rem;
    color: var(--accent);
    letter-spacing: 0.25em;
    text-transform: uppercase;
    margin-bottom: 1.5rem;
    opacity: 0;
    animation: fadeUp 0.8s 0.2s forwards;
  }

  h1 {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: clamp(3rem, 7vw, 5.5rem);
    line-height: 1.0;
    letter-spacing: -0.02em;
    margin-bottom: 0.3rem;
    opacity: 0;
    animation: fadeUp 0.8s 0.4s forwards;
  }

  .name-last {
    color: var(--ice);
    display: block;
  }

  .hero-role {
    font-family: 'DM Mono', monospace;
    font-size: 0.9rem;
    color: var(--muted);
    margin-top: 1.2rem;
    margin-bottom: 2rem;
    opacity: 0;
    animation: fadeUp 0.8s 0.6s forwards;
  }

  .hero-desc {
    max-width: 520px;
    font-size: 1rem;
    color: var(--white);
    opacity: 0;
    animation: fadeUp 0.8s 0.8s forwards;
    line-height: 1.8;
  }

  .hero-links {
    display: flex;
    gap: 1.2rem;
    margin-top: 2.5rem;
    flex-wrap: wrap;
    opacity: 0;
    animation: fadeUp 0.8s 1s forwards;
  }

  .btn {
    font-family: 'DM Mono', monospace;
    font-size: 0.72rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    text-decoration: none;
    padding: 0.65rem 1.5rem;
    border-radius: 2px;
    transition: all 0.25s;
  }

  .btn-primary {
    background: var(--bright);
    color: #fff;
    border: 1px solid var(--bright);
  }

  .btn-primary:hover {
    background: var(--ice);
    border-color: var(--ice);
    box-shadow: 0 0 24px rgba(77,184,255,0.4);
  }

  .btn-secondary {
    background: transparent;
    color: var(--muted);
    border: 1px solid rgba(122,154,184,0.3);
  }

  .btn-secondary:hover {
    color: var(--glow);
    border-color: var(--glow);
  }

  /* ── Sections ── */
  section {
    padding: 5rem 0;
    border-top: 1px solid rgba(122,154,184,0.08);
  }

  .section-label {
    font-family: 'DM Mono', monospace;
    font-size: 0.68rem;
    color: var(--accent);
    letter-spacing: 0.3em;
    text-transform: uppercase;
    margin-bottom: 2.5rem;
    display: flex;
    align-items: center;
    gap: 1rem;
  }

  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: rgba(0,212,170,0.2);
  }

  h2 {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 1.9rem;
    color: var(--white);
    margin-bottom: 2rem;
  }

  /* ── Research cards ── */
  .research-grid {
    display: grid;
    gap: 1px;
    background: rgba(122,154,184,0.08);
  }

  .research-item {
    background: var(--navy);
    padding: 1.8rem 0;
    display: grid;
    grid-template-columns: 3rem 1fr;
    gap: 1.2rem;
    align-items: start;
    transition: background 0.2s;
  }

  .research-item:hover { background: rgba(26,127,212,0.04); }

  .research-index {
    font-family: 'DM Mono', monospace;
    font-size: 0.65rem;
    color: var(--muted);
    padding-top: 0.2rem;
    letter-spacing: 0.05em;
  }

  .research-title {
    font-family: 'Syne', sans-serif;
    font-weight: 600;
    font-size: 1rem;
    color: var(--white);
    margin-bottom: 0.4rem;
    line-height: 1.4;
  }

  .research-desc {
    font-size: 0.88rem;
    color: var(--muted);
    line-height: 1.6;
  }

  /* ── Experience timeline ── */
  .timeline {
    display: flex;
    flex-direction: column;
    gap: 0;
  }

  .timeline-item {
    display: grid;
    grid-template-columns: 9rem 1fr;
    gap: 2rem;
    padding: 1.8rem 0;
    border-bottom: 1px solid rgba(122,154,184,0.06);
    position: relative;
  }

  .timeline-date {
    font-family: 'DM Mono', monospace;
    font-size: 0.7rem;
    color: var(--muted);
    padding-top: 0.15rem;
    line-height: 1.5;
  }

  .timeline-title {
    font-family: 'Syne', sans-serif;
    font-weight: 600;
    font-size: 1rem;
    color: var(--white);
    margin-bottom: 0.2rem;
  }

  .timeline-org {
    font-family: 'DM Mono', monospace;
    font-size: 0.72rem;
    color: var(--bright);
    margin-bottom: 0.8rem;
    letter-spacing: 0.05em;
  }

  .timeline-bullets {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 0.4rem;
  }

  .timeline-bullets li {
    font-size: 0.87rem;
    color: var(--muted);
    padding-left: 1.2rem;
    position: relative;
    line-height: 1.6;
  }

  .timeline-bullets li::before {
    content: '—';
    position: absolute;
    left: 0;
    color: rgba(77,184,255,0.4);
  }

  /* ── Publications ── */
  .pub-card {
    border: 1px solid rgba(122,154,184,0.1);
    border-left: 2px solid var(--bright);
    padding: 1.4rem 1.6rem;
    margin-bottom: 1rem;
    transition: border-color 0.2s;
  }

  .pub-card:hover { border-left-color: var(--ice); }

  .pub-title {
    font-family: 'Syne', sans-serif;
    font-weight: 600;
    font-size: 0.95rem;
    color: var(--white);
    margin-bottom: 0.4rem;
    line-height: 1.5;
  }

  .pub-meta {
    font-family: 'DM Mono', monospace;
    font-size: 0.7rem;
    color: var(--muted);
    letter-spacing: 0.05em;
  }

  .pub-link {
    font-family: 'DM Mono', monospace;
    font-size: 0.68rem;
    color: var(--accent);
    text-decoration: none;
    letter-spacing: 0.08em;
    margin-top: 0.5rem;
    display: inline-block;
  }

  /* ── Awards ── */
  .awards-list {
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }

  .award-item {
    display: flex;
    gap: 1.5rem;
    align-items: flex-start;
    padding: 1.2rem 0;
    border-bottom: 1px solid rgba(122,154,184,0.06);
  }

  .award-badge {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 0.7rem;
    color: var(--deep);
    background: var(--accent);
    padding: 0.2rem 0.5rem;
    white-space: nowrap;
    flex-shrink: 0;
    margin-top: 0.1rem;
  }

  .award-title {
    font-size: 0.92rem;
    color: var(--white);
    margin-bottom: 0.3rem;
    line-height: 1.5;
  }

  .award-event {
    font-family: 'DM Mono', monospace;
    font-size: 0.7rem;
    color: var(--muted);
  }

  /* ── Skills ── */
  .skills-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2rem;
  }

  .skill-group-label {
    font-family: 'DM Mono', monospace;
    font-size: 0.68rem;
    color: var(--accent);
    letter-spacing: 0.2em;
    text-transform: uppercase;
    margin-bottom: 1rem;
  }

  .skill-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
  }

  .tag {
    font-family: 'DM Mono', monospace;
    font-size: 0.68rem;
    color: var(--muted);
    border: 1px solid rgba(122,154,184,0.2);
    padding: 0.3rem 0.75rem;
    letter-spacing: 0.05em;
    transition: all 0.2s;
  }

  .tag:hover {
    color: var(--glow);
    border-color: rgba(77,184,255,0.4);
    background: rgba(77,184,255,0.04);
  }

  /* ── Contact ── */
  #contact {
    padding-bottom: 6rem;
  }

  .contact-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 0.5rem;
    margin-top: 1rem;
  }

  .contact-item {
    display: flex;
    align-items: center;
    gap: 1rem;
    padding: 1rem 0;
    text-decoration: none;
    border-bottom: 1px solid rgba(122,154,184,0.06);
    transition: all 0.2s;
    color: var(--muted);
  }

  .contact-item:hover { color: var(--glow); }

  .contact-label {
    font-family: 'DM Mono', monospace;
    font-size: 0.68rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--muted);
    min-width: 4rem;
  }

  .contact-value {
    font-size: 0.88rem;
    color: inherit;
  }

  /* ── Footer ── */
  footer {
    border-top: 1px solid rgba(122,154,184,0.08);
    padding: 2rem 0;
    text-align: center;
  }

  .footer-text {
    font-family: 'DM Mono', monospace;
    font-size: 0.65rem;
    color: rgba(122,154,184,0.35);
    letter-spacing: 0.1em;
  }

  /* ── Animations ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(18px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .reveal {
    opacity: 0;
    transform: translateY(20px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }

  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }

  /* ── Scrollbar ── */
  ::-webkit-scrollbar { width: 4px; }
  ::-webkit-scrollbar-track { background: var(--navy); }
  ::-webkit-scrollbar-thumb { background: var(--blue); border-radius: 2px; }

  @media (max-width: 640px) {
    nav { padding: 1rem 1.5rem; }
    .nav-links { display: none; }
    .timeline-item { grid-template-columns: 1fr; gap: 0.4rem; }
    .skills-grid { grid-template-columns: 1fr; }
    .contact-grid { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>

<canvas id="neural-bg"></canvas>

<nav>
  <span class="nav-logo">E · Moncada</span>
  <ul class="nav-links">
    <li><a href="#research">Research</a></li>
    <li><a href="#experience">Experience</a></li>
    <li><a href="#publications">Publications</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<main class="page">

  <!-- HERO -->
  <section id="hero">
    <p class="hero-label">Ph.D. Student · Neurotechnology & AI</p>
    <h1>
      Emmanuel
      <span class="name-last">Moncada Alvarez</span>
    </h1>
    <p class="hero-role">Tecnológico de Monterrey · NTLab · Zapopan, México</p>
    <p class="hero-desc">
      Building deep learning frameworks that decode the brain — from EEG and EMG signals to continuous biomarkers for early detection of neuromotor decline.
    </p>
    <div class="hero-links">
      <a href="mailto:A01649448@tec.mx" class="btn btn-primary">Get in touch</a>
      <a href="https://orcid.org" target="_blank" class="btn btn-secondary">ORCID →</a>
      <a href="https://linkedin.com" target="_blank" class="btn btn-secondary">LinkedIn →</a>
    </div>
  </section>

  <!-- RESEARCH -->
  <section id="research">
    <p class="section-label">Current research</p>
    <div class="research-grid reveal">
      <div class="research-item">
        <span class="research-index">01</span>
        <div>
          <p class="research-title">Motor Age — A continuous biomarker for neuromotor decline</p>
          <p class="research-desc">Multimodal deep learning framework integrating EEG, EMG, and force signals to estimate biological motor age as an early indicator of neuromotor deterioration.</p>
        </div>
      </div>
      <div class="research-item">
        <span class="research-index">02</span>
        <div>
          <p class="research-title">Multimodal EEG–EMG motor task classification</p>
          <p class="research-desc">Neural network architectures for joint classification of motor tasks from brain and muscle signals; modality contribution and utilization analysis.</p>
        </div>
      </div>
      <div class="research-item">
        <span class="research-index">03</span>
        <div>
          <p class="research-title">Precision grip force control & aging</p>
          <p class="research-desc">Investigating age-related changes in fine motor control using simultaneous EEG and behavioral force measurements during grip tasks.</p>
        </div>
      </div>
      <div class="research-item">
        <span class="research-index">04</span>
        <div>
          <p class="research-title">tDCS effects on motor performance</p>
          <p class="research-desc">ML-based biosignal analysis to quantify how transcranial direct current stimulation modulates motor task execution.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- EXPERIENCE -->
  <section id="experience">
    <p class="section-label">Experience</p>
    <div class="timeline">

      <div class="timeline-item reveal">
        <div class="timeline-date">2025 –<br>Present</div>
        <div>
          <p class="timeline-title">Ph.D. Researcher</p>
          <p class="timeline-org">Tecnológico de Monterrey · NTLab</p>
          <ul class="timeline-bullets">
            <li>Multimodal deep learning for Motor Age estimation from EEG, EMG, and force signals</li>
            <li>Modality contribution analysis in multimodal neural networks</li>
            <li>Advisor: Dr. Javier Mauricio Antelis Ortiz</li>
          </ul>
        </div>
      </div>

      <div class="timeline-item reveal">
        <div class="timeline-date">May –<br>Aug 2023</div>
        <div>
          <p class="timeline-title">Research Assistant · MITACS Globalink</p>
          <p class="timeline-org">University of New Brunswick, Canada</p>
          <ul class="timeline-bullets">
            <li>Development of a novel E-Textile sensor for EMG acquisition</li>
            <li>ML models applied to noisy biomedical time-series data</li>
          </ul>
        </div>
      </div>

      <div class="timeline-item reveal">
        <div class="timeline-date">May –<br>Aug 2023</div>
        <div>
          <p class="timeline-title">Research Assistant</p>
          <p class="timeline-org">Universidad Autónoma de Baja California Sur</p>
          <ul class="timeline-bullets">
            <li>ECG feature extraction for semiautomatic detection of atrial fibrillation</li>
            <li>Pipeline validation on real clinical data</li>
          </ul>
        </div>
      </div>

      <div class="timeline-item reveal">
        <div class="timeline-date">Jan –<br>Dec 2023</div>
        <div>
          <p class="timeline-title">Research Assistant</p>
          <p class="timeline-org">Universidad de Guadalajara</p>
          <ul class="timeline-bullets">
            <li>Image and signal processing pipelines for biomedical applications</li>
            <li>EMG artifact analysis</li>
          </ul>
        </div>
      </div>

      <div class="timeline-item reveal">
        <div class="timeline-date">May –<br>Aug 2022</div>
        <div>
          <p class="timeline-title">Research Assistant</p>
          <p class="timeline-org">Tecnológico de Monterrey</p>
          <ul class="timeline-bullets">
            <li>Brain–Computer Interface using visual evoked potentials</li>
            <li>EEG time-locked analysis of ERP components</li>
          </ul>
        </div>
      </div>

    </div>
  </section>

  <!-- PUBLICATIONS & PRESENTATIONS -->
  <section id="publications">
    <p class="section-label">Publications & Presentations</p>

    <div class="pub-card reveal">
      <p class="pub-title">ECG feature extraction for semiautomatic detection of atrial fibrillation</p>
      <p class="pub-meta">Moncada, E. et al. · IEEE EMBS R9 Conference · Guadalajara, Mexico · 2023</p>
      <a class="pub-link" href="https://ieeexplore.ieee.org" target="_blank">IEEE Xplore →</a>
    </div>

    <div class="pub-card reveal">
      <p class="pub-title">Modality Utilization Analysis of EEG–EMG Multimodal Neural Network</p>
      <p class="pub-meta">Conference Poster · SALA AI 2026 · Quito, Ecuador</p>
    </div>

    <br>
    <p class="section-label" style="margin-top: 1rem;">Awards</p>
    <div class="awards-list">
      <div class="award-item reveal">
        <span class="award-badge">1st</span>
        <div>
          <p class="award-title">Basic Sciences Category — Poster Presentation</p>
          <p class="award-event">CIAM 2026 — Congreso Internacional de Avances en Medicina · "Effect of Aging on Precision Grip Force Control"</p>
        </div>
      </div>
      <div class="award-item reveal">
        <span class="award-badge">3rd</span>
        <div>
          <p class="award-title">Poster Presentation</p>
          <p class="award-event">2nd Symposium on Aging · Tecnológico de Monterrey · "Effect of Aging on Precision Grip Force Control"</p>
        </div>
      </div>
    </div>
  </section>

  <!-- SKILLS -->
  <section id="skills">
    <p class="section-label">Skills</p>
    <div class="skills-grid reveal">
      <div>
        <p class="skill-group-label">Languages & Frameworks</p>
        <div class="skill-tags">
          <span class="tag">Python</span>
          <span class="tag">C</span>
          <span class="tag">C++</span>
          <span class="tag">PyTorch</span>
          <span class="tag">TensorFlow</span>
          <span class="tag">MATLAB</span>
          <span class="tag">MNE</span>
          <span class="tag">NumPy</span>
          <span class="tag">SciPy</span>
          <span class="tag">Pandas</span>
          <span class="tag">Scikit-learn</span>
        </div>
      </div>
      <div>
        <p class="skill-group-label">Expertise</p>
        <div class="skill-tags">
          <span class="tag">EEG · EMG signal processing</span>
          <span class="tag">Deep learning for biosignals</span>
          <span class="tag">Brain–Computer Interfaces</span>
          <span class="tag">Modality utilization analysis</span>
          <span class="tag">Feature extraction</span>
          <span class="tag">Spanish (native)</span>
          <span class="tag">English (advanced)</span>
        </div>
      </div>
    </div>
  </section>

  <!-- CONTACT -->
  <section id="contact">
    <p class="section-label">Contact</p>
    <h2>Let's connect.</h2>
    <div class="contact-grid reveal">
      <a class="contact-item" href="mailto:A01649448@tec.mx">
        <span class="contact-label">Email</span>
        <span class="contact-value">A01649448@tec.mx</span>
      </a>
      <a class="contact-item" href="tel:+523333973148">
        <span class="contact-label">Phone</span>
        <span class="contact-value">+52 33 3397 3148</span>
      </a>
      <a class="contact-item" href="https://linkedin.com" target="_blank">
        <span class="contact-label">LinkedIn</span>
        <span class="contact-value">emoncadaalvarez</span>
      </a>
      <a class="contact-item" href="https://orcid.org" target="_blank">
        <span class="contact-label">ORCID</span>
        <span class="contact-value">View profile →</span>
      </a>
    </div>
  </section>

</main>

<footer>
  <div class="page">
    <p class="footer-text">Emmanuel Moncada Alvarez · Neurotechnology & AI · Tecnológico de Monterrey · 2025–</p>
  </div>
</footer>

<!-- Neural network canvas animation -->
<script>
const canvas = document.getElementById('neural-bg');
const ctx = canvas.getContext('2d');

let W, H, nodes, animId;

function resize() {
  W = canvas.width  = window.innerWidth;
  H = canvas.height = window.innerHeight;
}

function initNodes() {
  nodes = Array.from({length: 60}, () => ({
    x: Math.random() * W,
    y: Math.random() * H,
    vx: (Math.random() - 0.5) * 0.25,
    vy: (Math.random() - 0.5) * 0.25,
    r: Math.random() * 2.2 + 0.6,
    pulse: Math.random() * Math.PI * 2
  }));
}

function draw() {
  ctx.clearRect(0, 0, W, H);
  const t = Date.now() * 0.001;

  // Update
  nodes.forEach(n => {
    n.x += n.vx;
    n.y += n.vy;
    n.pulse += 0.012;
    if (n.x < 0 || n.x > W) n.vx *= -1;
    if (n.y < 0 || n.y > H) n.vy *= -1;
  });

  // Edges
  for (let i = 0; i < nodes.length; i++) {
    for (let j = i + 1; j < nodes.length; j++) {
      const a = nodes[i], b = nodes[j];
      const d = Math.hypot(a.x - b.x, a.y - b.y);
      if (d < 140) {
        const alpha = (1 - d/140) * 0.35;
        ctx.strokeStyle = `rgba(26,127,212,${alpha})`;
        ctx.lineWidth = 0.5;
        ctx.beginPath();
        ctx.moveTo(a.x, a.y);
        ctx.lineTo(b.x, b.y);
        ctx.stroke();
      }
    }
  }

  // Nodes
  nodes.forEach(n => {
    const glow = 0.6 + 0.4 * Math.sin(n.pulse);
    ctx.fillStyle = `rgba(77,184,255,${glow * 0.7})`;
    ctx.beginPath();
    ctx.arc(n.x, n.y, n.r, 0, Math.PI * 2);
    ctx.fill();
  });

  animId = requestAnimationFrame(draw);
}

resize();
initNodes();
draw();
window.addEventListener('resize', () => { resize(); initNodes(); });

// Reveal on scroll
const reveals = document.querySelectorAll('.reveal');
const observer = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.classList.add('visible');
      observer.unobserve(e.target);
    }
  });
}, { threshold: 0.1 });
reveals.forEach(el => observer.observe(el));
</script>

</body>
</html>
