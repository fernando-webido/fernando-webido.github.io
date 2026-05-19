<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Fernando Uribe — Senior UX/UI Designer</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400&family=DM+Mono:wght@300;400&family=Outfit:wght@300;400;600&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  :root {
    --bg: #0a0a08; --surface: #111110; --surface2: #1a1a18;
    --accent: #c8f04a; --accent2: #f0c84a;
    --text: #f0ede4; --muted: #7a7970; --border: rgba(240,237,228,0.08);
    --serif: 'Playfair Display', serif; --mono: 'DM Mono', monospace; --sans: 'Outfit', sans-serif;
  }
  html { scroll-behavior: smooth; }
  body { background: var(--bg); color: var(--text); font-family: var(--sans); font-weight: 300; overflow-x: hidden; cursor: none; }

  .cursor-dot { position: fixed; width: 8px; height: 8px; border-radius: 50%; background: var(--accent); pointer-events: none; z-index: 9999; transform: translate(-50%,-50%); mix-blend-mode: difference; }
  .cursor-ring { position: fixed; width: 40px; height: 40px; border-radius: 50%; border: 1px solid var(--accent); pointer-events: none; z-index: 9998; transform: translate(-50%,-50%); transition: width .25s, height .25s, opacity .25s; mix-blend-mode: difference; }
  .cursor-ring.big { width: 64px; height: 64px; opacity: .5; }

  nav { position: fixed; top: 0; left: 0; right: 0; z-index: 100; display: flex; justify-content: space-between; align-items: center; padding: 1.5rem 3rem; transition: background .3s, border-color .3s; border-bottom: 1px solid transparent; }
  nav.scrolled { background: rgba(10,10,8,.92); backdrop-filter: blur(12px); border-color: var(--border); }
  .nav-logo { font-family: var(--serif); font-size: 1.1rem; font-style: italic; color: var(--text); text-decoration: none; }
  .nav-links { display: flex; gap: 2rem; list-style: none; }
  .nav-links a { font-family: var(--mono); font-size: .72rem; letter-spacing: .12em; text-transform: uppercase; color: var(--muted); text-decoration: none; transition: color .2s; }
  .nav-links a:hover { color: var(--accent); }
  .nav-cta { font-family: var(--mono); font-size: .72rem; letter-spacing: .1em; text-transform: uppercase; color: var(--bg); background: var(--accent); padding: .55rem 1.4rem; border-radius: 2rem; text-decoration: none; transition: background .2s; }
  .nav-cta:hover { background: var(--accent2); }

  #hero { min-height: 100vh; display: grid; grid-template-columns: 1fr 1fr; align-items: center; padding: 8rem 3rem 5rem; position: relative; overflow: hidden; }
  .grid-bg { position: absolute; inset: 0; background-image: linear-gradient(var(--border) 1px, transparent 1px), linear-gradient(90deg, var(--border) 1px, transparent 1px); background-size: 80px 80px; pointer-events: none; }
  .hero-left { position: relative; z-index: 1; }
  .tag { font-family: var(--mono); font-size: .72rem; letter-spacing: .16em; text-transform: uppercase; color: var(--accent); display: flex; align-items: center; gap: .8rem; margin-bottom: 1.5rem; }
  .tag::before { content: ''; width: 2rem; height: 1px; background: var(--accent); }
  h1.hero-title { font-family: var(--serif); font-size: clamp(3rem, 5.5vw, 5rem); line-height: 1.08; font-weight: 400; margin-bottom: 2rem; }
  h1.hero-title em { font-style: italic; color: var(--accent); }
  .hero-desc { font-size: 1rem; color: var(--muted); line-height: 1.85; max-width: 44ch; margin-bottom: 3rem; }
  .hero-actions { display: flex; gap: 1.2rem; align-items: center; }
  .btn-primary { background: var(--accent); color: var(--bg); padding: .9rem 2.2rem; border-radius: 3rem; font-family: var(--mono); font-size: .75rem; letter-spacing: .1em; text-transform: uppercase; text-decoration: none; transition: background .2s, transform .15s; display: inline-block; }
  .btn-primary:hover { background: var(--accent2); transform: translateY(-2px); }
  .btn-ghost { color: var(--muted); font-family: var(--mono); font-size: .75rem; letter-spacing: .1em; text-transform: uppercase; text-decoration: none; display: flex; align-items: center; gap: .5rem; border-bottom: 1px solid var(--border); padding-bottom: 2px; transition: color .2s; }
  .btn-ghost:hover { color: var(--text); }

  .hero-right { position: relative; z-index: 1; display: flex; flex-direction: column; align-items: flex-end; gap: 1.5rem; padding-left: 4rem; }
  .hero-photo { width: 100%; max-width: 360px; aspect-ratio: 3/4; border-radius: 2px; overflow: hidden; border: 1px solid var(--border); background: var(--surface2); display: flex; flex-direction: column; align-items: center; justify-content: center; gap: 1rem; }
  .avatar-circle { width: 90px; height: 90px; border-radius: 50%; border: 2px solid var(--accent); display: flex; align-items: center; justify-content: center; font-family: var(--serif); font-size: 1.8rem; color: var(--accent); }
  .photo-hint { font-family: var(--mono); font-size: .68rem; color: var(--muted); letter-spacing: .1em; }
  .hero-stats { display: grid; grid-template-columns: 1fr 1fr; width: 100%; max-width: 360px; background: var(--border); gap: 1px; }
  .stat { background: var(--surface); padding: 1.3rem 1.5rem; }
  .stat-n { font-family: var(--serif); font-size: 2rem; color: var(--accent); line-height: 1; }
  .stat-l { font-family: var(--mono); font-size: .65rem; color: var(--muted); letter-spacing: .1em; text-transform: uppercase; margin-top: .3rem; }

  .marquee-bar { overflow: hidden; border-top: 1px solid var(--border); border-bottom: 1px solid var(--border); padding: 1.1rem 0; background: var(--surface); }
  .marquee-inner { display: flex; gap: 4rem; width: max-content; animation: slide 26s linear infinite; }
  .mq-item { font-family: var(--mono); font-size: .72rem; letter-spacing: .14em; text-transform: uppercase; color: var(--muted); white-space: nowrap; display: flex; align-items: center; gap: 1.5rem; }
  .mq-item::after { content: '✦'; color: var(--accent); font-size: .55rem; }
  @keyframes slide { from { transform: translateX(0); } to { transform: translateX(-50%); } }

  section { padding: 7rem 3rem; }
  .sec-tag { font-family: var(--mono); font-size: .72rem; letter-spacing: .16em; text-transform: uppercase; color: var(--accent); display: flex; align-items: center; gap: .8rem; margin-bottom: 1.2rem; }
  .sec-tag::before { content: ''; width: 1.5rem; height: 1px; background: var(--accent); }
  .sec-title { font-family: var(--serif); font-size: clamp(2rem, 4vw, 3.5rem); font-weight: 400; line-height: 1.15; }
  .sec-title em { font-style: italic; color: var(--accent); }

  #work { border-top: 1px solid var(--border); }
  .work-head { display: flex; justify-content: space-between; align-items: flex-end; margin-bottom: 4rem; }
  .work-count { font-family: var(--mono); font-size: .72rem; color: var(--muted); letter-spacing: .1em; }
  .proj-list { display: flex; flex-direction: column; }
  .proj { display: grid; grid-template-columns: 3ch 1fr 1fr auto; align-items: center; gap: 2rem; padding: 2rem 2.5rem; border: 1px solid var(--border); border-bottom: none; text-decoration: none; color: inherit; background: var(--surface); transition: background .25s, border-color .25s; position: relative; overflow: hidden; }
  .proj:last-child { border-bottom: 1px solid var(--border); }
  .proj::after { content: ''; position: absolute; left: 0; top: 0; bottom: 0; width: 0; background: var(--accent); transition: width .3s; }
  .proj:hover::after { width: 3px; }
  .proj:hover { background: var(--surface2); border-color: rgba(200,240,74,.2); }
  .proj-n { font-family: var(--mono); font-size: .72rem; color: var(--muted); }
  .proj-name { font-family: var(--serif); font-size: 1.45rem; font-weight: 400; margin-bottom: .5rem; transition: color .2s; }
  .proj:hover .proj-name { color: var(--accent); }
  .proj-tags { display: flex; gap: .5rem; flex-wrap: wrap; }
  .ptag { font-family: var(--mono); font-size: .62rem; letter-spacing: .1em; text-transform: uppercase; color: var(--muted); border: 1px solid var(--border); padding: .2rem .65rem; border-radius: 2rem; }
  .proj-impact { display: flex; flex-direction: column; gap: .5rem; padding-left: 1.5rem; border-left: 1px solid var(--border); }
  .impact-label { font-family: var(--mono); font-size: .62rem; color: var(--muted); letter-spacing: .1em; text-transform: uppercase; }
  .impact-val { font-family: var(--serif); font-size: 1.5rem; color: var(--accent); line-height: 1; }
  .impact-desc { font-size: .8rem; color: var(--muted); }
  .proj-yr { font-family: var(--mono); font-size: .72rem; color: var(--muted); text-align: right; }
  .proj-arr { color: var(--accent); opacity: 0; transform: translateX(-8px); transition: all .25s; display: block; margin-top: .4rem; font-size: 1.1rem; }
  .proj:hover .proj-arr { opacity: 1; transform: none; }

  #about { border-top: 1px solid var(--border); display: grid; grid-template-columns: 1fr 1fr; gap: 6rem; align-items: start; }
  .about-text p { font-size: .975rem; color: var(--muted); line-height: 1.9; margin-bottom: 1.3rem; }
  .about-text strong { color: var(--text); font-weight: 400; }
  .skill-row { display: flex; justify-content: space-between; align-items: center; padding: .9rem 0; border-bottom: 1px solid var(--border); }
  .skill-name { font-family: var(--mono); font-size: .78rem; }
  .skill-track { width: 120px; height: 2px; background: var(--border); }
  .skill-fill { height: 100%; background: var(--accent); width: 0; transition: width 1.2s ease; }
  .tools-section { margin-top: 2.5rem; }
  .tools-label { font-family: var(--mono); font-size: .7rem; color: var(--muted); letter-spacing: .12em; text-transform: uppercase; margin-bottom: .8rem; margin-top: 1.5rem; }
  .tools-wrap { display: flex; flex-wrap: wrap; gap: .5rem; }
  .tool { font-family: var(--mono); font-size: .68rem; color: var(--text); border: 1px solid var(--border); padding: .32rem .85rem; border-radius: 2rem; transition: border-color .2s, color .2s; }
  .tool:hover { border-color: var(--accent); color: var(--accent); }

  #experience { border-top: 1px solid var(--border); }
  .timeline { margin-top: 4rem; display: flex; flex-direction: column; }
  .exp-item { display: grid; grid-template-columns: 200px 1fr; gap: 3rem; padding: 2.5rem 0; border-bottom: 1px solid var(--border); }
  .exp-item:first-child { border-top: 1px solid var(--border); }
  .exp-period { font-family: var(--mono); font-size: .68rem; color: var(--accent); letter-spacing: .1em; text-transform: uppercase; margin-bottom: .5rem; }
  .exp-company { font-family: var(--serif); font-size: 1.1rem; }
  .exp-type { font-family: var(--mono); font-size: .65rem; color: var(--muted); margin-top: .3rem; }
  .exp-role { font-size: 1.1rem; font-weight: 600; margin-bottom: 1rem; }
  .exp-desc { font-size: .9rem; color: var(--muted); line-height: 1.75; list-style: none; }
  .exp-desc li { margin-bottom: .5rem; padding-left: 1rem; position: relative; }
  .exp-desc li::before { content: '—'; position: absolute; left: 0; color: var(--accent); font-size: .8rem; }
  .exp-tools { display: flex; flex-wrap: wrap; gap: .4rem; margin-top: 1.2rem; }
  .exp-tool { font-family: var(--mono); font-size: .62rem; color: var(--muted); border: 1px solid var(--border); padding: .2rem .6rem; border-radius: 2rem; }

  #bring { border-top: 1px solid var(--border); }
  .bring-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 1px; background: var(--border); margin-top: 4rem; }
  .bring-card { background: var(--bg); padding: 2.5rem; transition: background .25s; }
  .bring-card:hover { background: var(--surface); }
  .bring-icon { font-size: 1.8rem; margin-bottom: 1.2rem; }
  .bring-title { font-family: var(--serif); font-size: 1.3rem; margin-bottom: .8rem; }
  .bring-desc { font-size: .875rem; color: var(--muted); line-height: 1.75; }

  #contact { border-top: 1px solid var(--border); text-align: center; padding: 9rem 3rem; }
  .contact-title { font-family: var(--serif); font-size: clamp(2.8rem, 6vw, 5.5rem); font-weight: 400; line-height: 1.1; max-width: 18ch; margin: 1.5rem auto 2rem; }
  .contact-title em { font-style: italic; color: var(--accent); }
  .contact-email { display: block; font-family: var(--mono); font-size: 1rem; color: var(--muted); letter-spacing: .08em; margin-bottom: 3rem; text-decoration: none; transition: color .2s; }
  .contact-email:hover { color: var(--accent); }
  .contact-btns { display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap; margin-bottom: 3rem; }
  .socials { display: flex; gap: 2rem; justify-content: center; }
  .social { font-family: var(--mono); font-size: .72rem; letter-spacing: .12em; text-transform: uppercase; color: var(--muted); text-decoration: none; transition: color .2s; }
  .social:hover { color: var(--accent); }

  footer { border-top: 1px solid var(--border); padding: 2rem 3rem; display: flex; justify-content: space-between; align-items: center; }
  .foot-copy { font-family: var(--mono); font-size: .68rem; color: var(--muted); letter-spacing: .06em; }
  .foot-up { font-family: var(--mono); font-size: .68rem; color: var(--muted); text-decoration: none; transition: color .2s; }
  .foot-up:hover { color: var(--accent); }

  .reveal { opacity: 0; transform: translateY(28px); transition: opacity .7s ease, transform .7s ease; }
  .reveal.in { opacity: 1; transform: none; }
  .d1 { transition-delay: .1s; } .d2 { transition-delay: .2s; } .d3 { transition-delay: .3s; } .d4 { transition-delay: .4s; }

  @media (max-width: 960px) {
    #hero { grid-template-columns: 1fr; padding: 7rem 1.5rem 4rem; }
    .hero-right { align-items: flex-start; padding-left: 0; padding-top: 3rem; }
    #about { grid-template-columns: 1fr; gap: 3rem; }
    .bring-grid { grid-template-columns: 1fr; }
    nav { padding: 1.2rem 1.5rem; }
    section { padding: 5rem 1.5rem; }
    .nav-links { display: none; }
    .proj { grid-template-columns: 3ch 1fr auto; }
    .proj-impact { display: none; }
    .exp-item { grid-template-columns: 1fr; gap: 1rem; }
  }
</style>
</head>
<body>

<div class="cursor-dot" id="dot"></div>
<div class="cursor-ring" id="ring"></div>

<nav id="nav">
  <a href="#" class="nav-logo">Fernando Uribe.</a>
  <ul class="nav-links">
    <li><a href="#work">Work</a></li>
    <li><a href="#experience">Experience</a></li>
    <li><a href="#about">Skills</a></li>
    <li><a href="#bring">Value</a></li>
  </ul>
  <a href="#contact" class="nav-cta">Let's Talk</a>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="grid-bg"></div>
  <div class="hero-left">
    <div class="tag reveal">Senior UX/UI Designer · 8+ years of experience</div>
    <h1 class="hero-title reveal d1">
      Turning<br>complexity into<br><em>clarity</em>
    </h1>
    <p class="hero-desc reveal d2">
      I design interfaces that simplify complex workflows and deliver measurable results. From research to developer handoff — with a systems mindset and a coder's eye.
    </p>
    <div class="hero-actions reveal d3">
      <a href="#work" class="btn-primary">View my work</a>
      <a href="mailto:fosforopkv@gmail.com" class="btn-ghost">Get in touch →</a>
    </div>
  </div>
  <div class="hero-right">
    <div class="hero-photo reveal d2">
      <div class="avatar-circle">FU</div>
      <span class="photo-hint">Your photo here</span>
    </div>
    <div class="hero-stats reveal d3">
      <div class="stat"><div class="stat-n">8+</div><div class="stat-l">Years exp.</div></div>
      <div class="stat" style="border-left:1px solid var(--border)"><div class="stat-n">4</div><div class="stat-l">Industries</div></div>
      <div class="stat" style="border-top:1px solid var(--border)"><div class="stat-n">100+</div><div class="stat-l">DS Components</div></div>
      <div class="stat" style="border-top:1px solid var(--border);border-left:1px solid var(--border)"><div class="stat-n">55%</div><div class="stat-l">Steps reduced</div></div>
    </div>
  </div>
</section>

<!-- MARQUEE -->
<div class="marquee-bar">
  <div class="marquee-inner">
    <span class="mq-item">Design Thinking</span><span class="mq-item">Design Systems</span><span class="mq-item">User Research</span><span class="mq-item">Figma</span><span class="mq-item">Prototyping</span><span class="mq-item">A/B Testing</span><span class="mq-item">Double Diamond</span><span class="mq-item">SaaS · Enterprise</span><span class="mq-item">HTML · CSS · JS</span><span class="mq-item">Lean UX</span><span class="mq-item">Usability Testing</span><span class="mq-item">React · Vue</span>
    <span class="mq-item">Design Thinking</span><span class="mq-item">Design Systems</span><span class="mq-item">User Research</span><span class="mq-item">Figma</span><span class="mq-item">Prototyping</span><span class="mq-item">A/B Testing</span><span class="mq-item">Double Diamond</span><span class="mq-item">SaaS · Enterprise</span><span class="mq-item">HTML · CSS · JS</span><span class="mq-item">Lean UX</span><span class="mq-item">Usability Testing</span><span class="mq-item">React · Vue</span>
  </div>
</div>

<!-- WORK -->
<section id="work">
  <div class="work-head">
    <div>
      <div class="sec-tag reveal">Selected Projects</div>
      <h2 class="sec-title reveal d1">Measurable<br><em>results</em></h2>
    </div>
    <span class="work-count reveal">04 case studies</span>
  </div>
  <div class="proj-list">

    <a href="#" class="proj reveal">
      <span class="proj-n">01</span>
      <div>
        <div class="proj-name">Music Distribution Platform</div>
        <div class="proj-tags"><span class="ptag">UX Research</span><span class="ptag">Workflow Design</span><span class="ptag">SaaS</span><span class="ptag">Unosquare</span></div>
      </div>
      <div class="proj-impact">
        <span class="impact-label">Key impact</span>
        <span class="impact-val">−55%</span>
        <span class="impact-desc">Steps in artist publishing<br>workflow (9 → 4 steps)</span>
      </div>
      <div class="proj-yr">2022–2024<span class="proj-arr">→</span></div>
    </a>

    <a href="#" class="proj reveal d1">
      <span class="proj-n">02</span>
      <div>
        <div class="proj-name">Cloud & IT Enterprise Platform</div>
        <div class="proj-tags"><span class="ptag">Design System</span><span class="ptag">Enterprise</span><span class="ptag">Global</span><span class="ptag">Unosquare</span></div>
      </div>
      <div class="proj-impact">
        <span class="impact-label">Scale</span>
        <span class="impact-val">100+</span>
        <span class="impact-desc">Components adopted by<br>clients in US, Japan & beyond</span>
      </div>
      <div class="proj-yr">2022–2024<span class="proj-arr">→</span></div>
    </a>

    <a href="#" class="proj reveal d2">
      <span class="proj-n">03</span>
      <div>
        <div class="proj-name">Digital Bulletin Platform</div>
        <div class="proj-tags"><span class="ptag">UX Writing</span><span class="ptag">Automation</span><span class="ptag">Content Design</span><span class="ptag">Unosquare</span></div>
      </div>
      <div class="proj-impact">
        <span class="impact-label">Efficiency</span>
        <span class="impact-val">~100%</span>
        <span class="impact-desc">Reduction in content<br>creation time (30–60 min → instant)</span>
      </div>
      <div class="proj-yr">2022–2023<span class="proj-arr">→</span></div>
    </a>

    <a href="#" class="proj reveal d3">
      <span class="proj-n">04</span>
      <div>
        <div class="proj-name">Marival Group Booking Flow</div>
        <div class="proj-tags"><span class="ptag">Conversion Rate</span><span class="ptag">Trust UX</span><span class="ptag">Hospitality</span><span class="ptag">Frontend</span></div>
      </div>
      <div class="proj-impact">
        <span class="impact-label">Problem solved</span>
        <span class="impact-val">47%</span>
        <span class="impact-desc">Booking abandonment rate<br>addressed & resolved</span>
      </div>
      <div class="proj-yr">2016–2019<span class="proj-arr">→</span></div>
    </a>

  </div>
</section>

<!-- EXPERIENCE -->
<section id="experience">
  <div class="sec-tag reveal">Career</div>
  <h2 class="sec-title reveal d1">Professional<br><em>experience</em></h2>
  <div class="timeline">

    <div class="exp-item reveal">
      <div>
        <div class="exp-period">Jan 2022 → Present</div>
        <div class="exp-company">Unosquare</div>
        <div class="exp-type">Consulting · Remote</div>
      </div>
      <div>
        <div class="exp-role">Senior UX/UI Designer</div>
        <ul class="exp-desc">
          <li>Led UX/UI across 4 simultaneous client products in distinct verticals, owning the full design lifecycle from discovery through developer handoff.</li>
          <li>Redesigned artist publishing workflow, cutting steps from 9 → 4 (~55% reduction), directly driving new user adoption.</li>
          <li>Architected a 100+ component design system adopted by enterprise clients across the US, Japan, and globally.</li>
          <li>Improved usability of a data-intensive scientific platform at European scale using progressive disclosure to reduce cognitive load.</li>
          <li>Reduced content creation time from 30–60 min to near-instant by building a guided, auto-populated flow.</li>
        </ul>
        <div class="exp-tools"><span class="exp-tool">Figma</span><span class="exp-tool">Sketch</span><span class="exp-tool">Maze</span><span class="exp-tool">Abstract</span><span class="exp-tool">Agile / Scrum</span></div>
      </div>
    </div>

    <div class="exp-item reveal d1">
      <div>
        <div class="exp-period">Dec 2019 → Sep 2021</div>
        <div class="exp-company">Toca Soccer</div>
        <div class="exp-type">Sports Tech · United States</div>
      </div>
      <div>
        <div class="exp-role">UX/UI Designer</div>
        <ul class="exp-desc">
          <li>Led full mobile app and website redesign proposal for a multi-location soccer school with 100+ active users across the US.</li>
          <li>Ran competitive analysis that identified key opportunity areas and informed the product direction.</li>
          <li>Delivered a unified design system and component library covering mobile, web, and email touchpoints.</li>
        </ul>
      </div>
    </div>

    <div class="exp-item reveal d1">
      <div>
        <div class="exp-period">Sep 2021 → Nov 2021</div>
        <div class="exp-company">Agile Thought</div>
        <div class="exp-type">Client: Nagarro · Contract</div>
      </div>
      <div>
        <div class="exp-role">UX/UI Designer</div>
        <ul class="exp-desc">
          <li>Conducted user research, synthesized insights, and delivered wireframes and prototypes for stakeholder validation.</li>
        </ul>
        <div class="exp-tools"><span class="exp-tool">Figma</span><span class="exp-tool">Google Analytics</span><span class="exp-tool">Hotjar</span><span class="exp-tool">Maze</span></div>
      </div>
    </div>

    <div class="exp-item reveal d2">
      <div>
        <div class="exp-period">May 2016 → Dec 2019</div>
        <div class="exp-company">Marival Group</div>
        <div class="exp-type">Hospitality · Mexico</div>
      </div>
      <div>
        <div class="exp-role">UX/UI Designer · Front-end Developer</div>
        <ul class="exp-desc">
          <li>Addressed ~47% booking abandonment rate by redesigning the reservation flow with trust signals and UX improvements.</li>
          <li>Redesigned 10+ digital properties (5 hotel sites, 3 restaurant sites, 2 travel agency sites) using a consistent mobile-first design system.</li>
          <li>Bridged design and dev: implemented responsive UIs with HTML, CSS, JavaScript, Bootstrap, and Tailwind CSS.</li>
        </ul>
      </div>
    </div>

  </div>
</section>

<!-- ABOUT / SKILLS -->
<section id="about">
  <div class="about-text">
    <div class="sec-tag reveal">About</div>
    <h2 class="sec-title reveal d1" style="margin-bottom:2.5rem">Designer.<br><em>Developer.</em><br>Thinker.</h2>
    <div class="reveal d2">
      <p>I'm <strong>J. Fernando Uribe Urteaga</strong>, a Senior UX/UI Designer based in Mexico. For 8+ years I've been turning ambiguous, complex workflows into intuitive, scalable interfaces.</p>
      <p>My differentiator: I understand <strong>both design and code</strong>. That means precise handoffs, genuine collaboration with engineering teams, and interfaces that are built the way they were designed.</p>
      <p>I've worked across <strong>SaaS, hospitality, sports tech, and life sciences</strong>. I'm especially drawn to the challenge of making complex enterprise platforms feel effortless to the people who use them every day.</p>
      <p>English <strong>C1 Advanced</strong> · Native Spanish · Available for global remote projects.</p>
    </div>
  </div>
  <div>
    <div class="sec-tag reveal">Full Stack of Skills</div>
    <div id="skillsEl" class="reveal d1">
      <div class="skill-row"><span class="skill-name">UX Research & Strategy</span><div class="skill-track"><div class="skill-fill" data-w="95"></div></div></div>
      <div class="skill-row"><span class="skill-name">Interaction & Product Design</span><div class="skill-track"><div class="skill-fill" data-w="96"></div></div></div>
      <div class="skill-row"><span class="skill-name">Design Systems</span><div class="skill-track"><div class="skill-fill" data-w="93"></div></div></div>
      <div class="skill-row"><span class="skill-name">HTML · CSS · JavaScript</span><div class="skill-track"><div class="skill-fill" data-w="85"></div></div></div>
      <div class="skill-row"><span class="skill-name">Vue · React · Angular</span><div class="skill-track"><div class="skill-fill" data-w="75"></div></div></div>
      <div class="skill-row"><span class="skill-name">Usability Testing</span><div class="skill-track"><div class="skill-fill" data-w="90"></div></div></div>
    </div>
    <div class="tools-section reveal d2">
      <div class="tools-label">Design</div>
      <div class="tools-wrap">
        <span class="tool">Figma</span><span class="tool">Sketch</span><span class="tool">Adobe XD</span><span class="tool">Miro</span><span class="tool">FigJam</span><span class="tool">Overflow</span><span class="tool">Maze</span>
      </div>
      <div class="tools-label">Development</div>
      <div class="tools-wrap">
        <span class="tool">HTML/CSS/SCSS</span><span class="tool">JavaScript</span><span class="tool">Vue</span><span class="tool">React</span><span class="tool">Angular</span><span class="tool">Tailwind</span><span class="tool">Bootstrap</span>
      </div>
      <div class="tools-label">AI & Research</div>
      <div class="tools-wrap">
        <span class="tool">ChatGPT</span><span class="tool">Claude</span><span class="tool">Gemini</span><span class="tool">GitHub Copilot</span><span class="tool">Notion AI</span><span class="tool">Hotjar</span>
      </div>
      <div class="tools-label">Methodologies</div>
      <div class="tools-wrap">
        <span class="tool">Design Thinking</span><span class="tool">Design Sprint</span><span class="tool">Double Diamond</span><span class="tool">Lean UX</span><span class="tool">Agile/Scrum</span>
      </div>
    </div>
  </div>
</section>

<!-- WHAT I BRING -->
<section id="bring">
  <div class="sec-tag reveal">What sets me apart</div>
  <h2 class="sec-title reveal d1">My unique<br><em>value</em></h2>
  <div class="bring-grid">
    <div class="bring-card reveal">
      <div class="bring-icon">🧠</div>
      <div class="bring-title">Simplifies complexity</div>
      <p class="bring-desc">Turns dense, intricate workflows into intuitive interfaces that users actually complete. Fewer steps, less friction, more conversion.</p>
    </div>
    <div class="bring-card reveal d1">
      <div class="bring-icon">⚡</div>
      <div class="bring-title">Design ↔ Dev bridge</div>
      <p class="bring-desc">A front-end background (HTML, CSS, Vue, React) enables precise handoffs and faster, faithful implementation — no translation errors between teams.</p>
    </div>
    <div class="bring-card reveal d2">
      <div class="bring-icon">🏗️</div>
      <div class="bring-title">Systems thinker</div>
      <p class="bring-desc">Builds 100+ component design systems — not just isolated screens. Visual and interaction consistency at scale across real products.</p>
    </div>
    <div class="bring-card reveal d3">
      <div class="bring-icon">🌍</div>
      <div class="bring-title">Cross-industry adaptability</div>
      <p class="bring-desc">SaaS, hospitality, sports tech, life sciences, music — proven across completely different verticals with global remote teams.</p>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="sec-tag reveal" style="justify-content:center">Ready to collaborate?</div>
  <h2 class="contact-title reveal d1">Let's build something <em>extraordinary</em> together</h2>
  <a href="mailto:fosforopkv@gmail.com" class="contact-email reveal d2">fosforopkv@gmail.com</a>
  <div class="contact-btns reveal d3">
    <a href="mailto:fosforopkv@gmail.com" class="btn-primary">Send a message</a>
    <a href="https://linkedin.com/in/fernando-uribe-urteaga" class="btn-ghost">View LinkedIn →</a>
  </div>
  <div class="socials reveal d4">
    <a href="https://linkedin.com/in/fernando-uribe-urteaga" class="social">LinkedIn</a>
    <a href="#" class="social">Behance</a>
    <a href="#" class="social">Dribbble</a>
  </div>
</section>

<footer>
  <span class="foot-copy">© 2025 J. Fernando Uribe Urteaga · Senior UX/UI Designer · Mexico</span>
  <a href="#hero" class="foot-up">↑ Back to top</a>
</footer>

<script>
  const dot = document.getElementById('dot');
  const ring = document.getElementById('ring');
  let mx = 0, my = 0, rx = window.innerWidth/2, ry = window.innerHeight/2;
  document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; dot.style.left = mx+'px'; dot.style.top = my+'px'; });
  (function animRing() { rx += (mx-rx)*.13; ry += (my-ry)*.13; ring.style.left = rx+'px'; ring.style.top = ry+'px'; requestAnimationFrame(animRing); })();
  document.querySelectorAll('a,button,.tool,.ptag,.bring-card,.exp-item').forEach(el => { el.addEventListener('mouseenter', () => ring.classList.add('big')); el.addEventListener('mouseleave', () => ring.classList.remove('big')); });
  window.addEventListener('scroll', () => document.getElementById('nav').classList.toggle('scrolled', scrollY > 60));
  const obs = new IntersectionObserver(entries => entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('in'); }), { threshold: .1, rootMargin: '0px 0px -40px 0px' });
  document.querySelectorAll('.reveal').forEach(el => obs.observe(el));
  setTimeout(() => document.querySelectorAll('#hero .reveal').forEach(el => el.classList.add('in')), 80);
  const skillObs = new IntersectionObserver(entries => entries.forEach(e => { if (e.isIntersecting) e.target.querySelectorAll('.skill-fill').forEach(b => b.style.width = b.dataset.w+'%'); }), { threshold: .3 });
  const sk = document.getElementById('skillsEl');
  if (sk) skillObs.observe(sk);
</script>
</body>
</html>
