<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Performance Pickleball, Documentary Outline v3.1</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Barlow+Condensed:ital,wght@0,400;0,600;0,700;1,400&family=Nunito+Sans:wght@300;400;600&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    /* Court palette */
    --court-deep:    #081C24;
    --court-dark:    #0C2A36;
    --court-mid:     #103848;
    --court-surface: #154458;
    --line:          rgba(220,240,248,0.12);
    --line-bright:   rgba(220,240,248,0.5);

    /* Pickleball yellow-green */
    --pickle:        #C2E040;
    --pickle-dark:   #8AAA1A;
    --pickle-dim:    rgba(194,224,64,0.15);
    --pickle-border: rgba(194,224,64,0.3);

    /* Text */
    --text-primary:  #E2F0F6;
    --text-muted:    #6A94A8;
    --text-faint:    #2E5060;

    /* Conflict — warm amber */
    --conflict:      #E07830;
    --conflict-bg:   rgba(224,120,48,0.08);
    --conflict-border:rgba(224,120,48,0.25);

    /* Resolution — bright teal */
    --resolve:       #38C8A0;
    --resolve-bg:    rgba(56,200,160,0.08);
    --resolve-border:rgba(56,200,160,0.25);

    /* Emotional heart — pickle gold */
    --heart-bg:      rgba(194,224,64,0.06);
    --heart-border:  rgba(194,224,64,0.2);
  }

  body {
    background: var(--court-deep);
    color: var(--text-primary);
    font-family: 'Nunito Sans', sans-serif;
    font-weight: 300;
    line-height: 1.6;
    min-height: 100vh;
  }

  /* ─── COURT LINE BACKGROUND ─── */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    pointer-events: none;
    z-index: 0;
    background-image:
      /* Vertical sidelines */
      linear-gradient(90deg, var(--line) 1px, transparent 1px),
      /* Horizontal baselines */
      linear-gradient(0deg, var(--line) 1px, transparent 1px),
      /* Kitchen line — thicker, slightly brighter */
      linear-gradient(0deg, transparent 33.3%, var(--line) 33.3%, var(--line) calc(33.3% + 1px), transparent calc(33.3% + 1px)),
      linear-gradient(0deg, transparent 66.6%, var(--line) 66.6%, var(--line) calc(66.6% + 1px), transparent calc(66.6% + 1px));
    background-size:
      120px 120px,
      120px 120px,
      100% 300px,
      100% 300px;
    opacity: 0.4;
  }

  /* Pickleball ball watermark */
  body::after {
    content: '';
    position: fixed;
    top: -120px;
    right: -120px;
    width: 400px;
    height: 400px;
    border-radius: 50%;
    border: 30px solid rgba(194,224,64,0.04);
    box-shadow:
      inset 0 0 0 30px transparent,
      0 0 0 30px rgba(194,224,64,0.025),
      0 0 0 60px rgba(194,224,64,0.015);
    pointer-events: none;
    z-index: 0;
  }

  * { position: relative; z-index: 1; }

  /* ─── HERO ─── */
  .hero {
    padding: 70px 64px 56px;
    border-bottom: 1px solid var(--line-bright);
    background: linear-gradient(160deg, rgba(21,68,88,0.6) 0%, transparent 60%);
    overflow: hidden;
  }

  .hero-top {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    margin-bottom: 28px;
  }

  .hero-eyebrow {
    font-family: 'Barlow Condensed', sans-serif;
    font-size: 12px;
    letter-spacing: 6px;
    color: var(--text-muted);
    text-transform: uppercase;
    font-weight: 400;
  }

  .draft-tag {
    font-family: 'Barlow Condensed', sans-serif;
    font-size: 11px;
    letter-spacing: 4px;
    color: var(--pickle);
    text-transform: uppercase;
    font-weight: 600;
    padding: 4px 14px;
    border: 1px solid var(--pickle-border);
    border-radius: 2px;
    background: var(--pickle-dim);
  }

  .hero-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(60px, 10vw, 120px);
    line-height: 0.9;
    letter-spacing: 3px;
    color: var(--text-primary);
    margin-bottom: 4px;
  }
  .hero-title .accent { color: var(--pickle); }

  .hero-sub {
    font-family: 'Barlow Condensed', sans-serif;
    font-size: 16px;
    letter-spacing: 3px;
    color: var(--text-muted);
    text-transform: uppercase;
    font-weight: 400;
    margin-top: 8px;
  }

  .hero-meta {
    display: flex;
    gap: 0;
    margin-top: 40px;
    padding-top: 28px;
    border-top: 1px solid var(--line-bright);
    flex-wrap: wrap;
  }
  .meta-item {
    padding-right: 40px;
    margin-right: 40px;
    border-right: 1px solid var(--line-bright);
  }
  .meta-item:last-child { border-right: none; }
  .meta-item label {
    display: block;
    font-family: 'Barlow Condensed', sans-serif;
    font-size: 10px;
    letter-spacing: 4px;
    color: var(--text-faint);
    text-transform: uppercase;
    margin-bottom: 5px;
    font-weight: 600;
  }
  .meta-item span {
    font-family: 'Barlow Condensed', sans-serif;
    font-size: 17px;
    letter-spacing: 1px;
    color: var(--text-primary);
    font-weight: 600;
  }
  .meta-item span.hi { color: var(--pickle); }

  /* ─── LOGLINE BAR ─── */
  .logline-bar {
    padding: 18px 64px;
    background: rgba(194,224,64,0.05);
    border-bottom: 1px solid var(--pickle-border);
    display: flex;
    align-items: baseline;
    gap: 18px;
  }
  .logline-label {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 13px;
    letter-spacing: 4px;
    color: var(--pickle);
    white-space: nowrap;
  }
  .logline-bar p {
    font-family: 'Barlow Condensed', sans-serif;
    font-size: 16px;
    font-style: italic;
    color: var(--text-muted);
    letter-spacing: 0.4px;
    font-weight: 400;
    line-height: 1.5;
  }

  /* ─── REVISION NOTE ─── */
  .revision-note {
    padding: 12px 64px;
    background: var(--conflict-bg);
    border-bottom: 1px solid var(--conflict-border);
    font-family: 'Nunito Sans', sans-serif;
    font-size: 12px;
    color: var(--conflict);
    letter-spacing: 0.3px;
  }
  .revision-note strong { font-weight: 600; }

  /* ─── MAIN LAYOUT ─── */
  .main {
    max-width: 1120px;
    margin: 0 auto;
    padding: 64px 64px 100px;
  }

  /* ─── SECTION LABEL ─── */
  .section-label {
    display: flex;
    align-items: center;
    gap: 16px;
    margin-bottom: 28px;
    font-family: 'Bebas Neue', sans-serif;
    font-size: 14px;
    letter-spacing: 6px;
    color: var(--pickle);
    text-transform: uppercase;
  }
  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--line-bright);
  }

  /* ─── ACT DIVIDERS ─── */
  .act-label {
    display: flex;
    align-items: center;
    gap: 14px;
    margin-bottom: 16px;
    margin-top: 52px;
  }
  .act-label:first-child { margin-top: 0; }

  .act-pill {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 13px;
    letter-spacing: 4px;
    padding: 5px 16px;
    border-radius: 2px;
    white-space: nowrap;
  }
  .act-1 .act-pill { background: rgba(56,200,160,0.15); color: var(--resolve); border: 1px solid var(--resolve-border); }
  .act-2 .act-pill { background: var(--conflict-bg); color: var(--conflict); border: 1px solid var(--conflict-border); }
  .act-3 .act-pill { background: var(--pickle-dim); color: var(--pickle); border: 1px solid var(--pickle-border); }

  .act-desc {
    font-family: 'Barlow Condensed', sans-serif;
    font-size: 13px;
    color: var(--text-faint);
    letter-spacing: 1px;
    font-style: italic;
  }
  .act-line { flex: 1; height: 1px; background: var(--line-bright); }

  /* ─── SCENES ─── */
  .scenes { display: flex; flex-direction: column; gap: 3px; }

  .scene {
    background: rgba(15,56,72,0.5);
    border: 1px solid rgba(220,240,248,0.08);
    border-left: 3px solid transparent;
    overflow: hidden;
    transition: background 0.25s, border-color 0.25s;
    backdrop-filter: blur(4px);
  }
  .scene:hover { background: rgba(21,68,88,0.6); border-color: rgba(220,240,248,0.15); }

  .scene.heart {
    background: var(--heart-bg);
    border-color: var(--heart-border);
    border-left-color: var(--pickle);
  }
  .scene.conflict {
    background: var(--conflict-bg);
    border-color: var(--conflict-border);
    border-left-color: var(--conflict);
  }
  .scene.resolve {
    background: var(--resolve-bg);
    border-color: var(--resolve-border);
    border-left-color: var(--resolve);
  }

  .scene-header {
    display: grid;
    grid-template-columns: 80px 1fr auto;
    align-items: start;
    padding: 26px 30px;
    gap: 24px;
  }

  .scene-number {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 52px;
    line-height: 1;
    color: var(--text-faint);
    letter-spacing: 2px;
    transition: color 0.25s;
    padding-top: 2px;
  }
  .scene:hover .scene-number { color: rgba(220,240,248,0.2); }
  .scene.heart .scene-number  { color: rgba(194,224,64,0.25); }
  .scene.conflict .scene-number { color: rgba(224,120,48,0.25); }
  .scene.resolve .scene-number  { color: rgba(56,200,160,0.25); }

  .scene-title {
    font-family: 'Barlow Condensed', sans-serif;
    font-size: 24px;
    font-weight: 700;
    letter-spacing: 1px;
    color: var(--text-primary);
    margin-bottom: 6px;
    text-transform: uppercase;
  }
  .scene-timing {
    font-family: 'Nunito Sans', sans-serif;
    font-size: 12px;
    color: var(--text-muted);
  }
  .scene-timing .dur {
    color: var(--pickle);
    font-weight: 600;
  }

  .scene-badges {
    display: flex;
    flex-direction: column;
    gap: 6px;
    align-items: flex-end;
  }
  .badge {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 11px;
    letter-spacing: 3px;
    padding: 4px 12px;
    border-radius: 2px;
    white-space: nowrap;
  }
  .badge-broll     { background: rgba(56,200,160,0.12); color: var(--resolve); border: 1px solid var(--resolve-border); }
  .badge-interview { background: var(--pickle-dim); color: var(--pickle); border: 1px solid var(--pickle-border); }
  .badge-combined  { background: rgba(106,148,168,0.12); color: #8ab8cc; border: 1px solid rgba(106,148,168,0.25); }
  .badge-heart     { background: var(--pickle-dim); color: var(--pickle); border: 1px solid var(--pickle-border); font-size: 10px; }
  .badge-conflict  { background: var(--conflict-bg); color: var(--conflict); border: 1px solid var(--conflict-border); font-size: 10px; }
  .badge-resolve   { background: var(--resolve-bg); color: var(--resolve); border: 1px solid var(--resolve-border); font-size: 10px; }

  /* ─── SCENE BODY ─── */
  .scene-body { padding: 0 30px 26px 134px; }

  .scene-description {
    font-size: 14px;
    color: #8AAABB;
    line-height: 1.75;
    margin-bottom: 20px;
  }

  /* Interview question blocks */
  .interview-qs {
    background: rgba(8,28,36,0.5);
    border: 1px solid rgba(220,240,248,0.06);
    padding: 14px 18px;
    margin-bottom: 10px;
    border-radius: 0 2px 2px 0;
  }
  .interview-qs.founders  { border-left: 3px solid var(--pickle); }
  .interview-qs.mums      { border-left: 3px solid var(--resolve); }
  .interview-qs.tension   { border-left: 3px solid var(--conflict); }
  .interview-qs.resolution{ border-left: 3px solid var(--resolve); }

  .interview-qs h5 {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 11px;
    letter-spacing: 4px;
    text-transform: uppercase;
    margin-bottom: 10px;
    font-weight: 400;
  }
  .interview-qs.founders h5  { color: var(--pickle); }
  .interview-qs.mums h5      { color: var(--resolve); }
  .interview-qs.tension h5   { color: var(--conflict); }
  .interview-qs.resolution h5{ color: var(--resolve); }

  .interview-qs ul { list-style: none; }
  .interview-qs li {
    font-size: 13px;
    color: var(--text-muted);
    padding: 5px 0 5px 18px;
    position: relative;
    line-height: 1.5;
  }
  .interview-qs li::before {
    content: '—';
    position: absolute;
    left: 0;
    color: var(--text-faint);
  }

  /* Shot pills */
  .shots {
    display: flex;
    flex-wrap: wrap;
    gap: 7px;
    margin-top: 14px;
  }
  .shot {
    font-family: 'Barlow Condensed', sans-serif;
    font-size: 12px;
    letter-spacing: 0.5px;
    color: var(--text-faint);
    background: rgba(8,28,36,0.7);
    border: 1px solid rgba(220,240,248,0.07);
    padding: 4px 12px;
    border-radius: 2px;
  }

  /* ─── RUNTIME BAR ─── */
  .timeline { margin-top: 64px; }
  .tl-bar {
    display: flex;
    height: 10px;
    border-radius: 2px;
    overflow: hidden;
    margin: 20px 0 12px;
    gap: 2px;
  }
  .tl-open    { background: rgba(56,200,160,0.5); flex: 0.4; }
  .tl-found   { background: rgba(56,200,160,0.7); flex: 0.8; }
  .tl-heart   { background: var(--pickle);         flex: 1.2; }
  .tl-conflict{ background: var(--conflict);       flex: 1.0; }
  .tl-resolve { background: var(--resolve);        flex: 0.9; }

  .tl-labels {
    display: flex;
    gap: 2px;
    font-family: 'Barlow Condensed', sans-serif;
  }
  .tl-lbl {
    color: var(--text-muted);
    flex: 1;
    font-size: 12px;
    letter-spacing: 0.5px;
    line-height: 1.4;
    padding-right: 6px;
  }
  .tl-lbl span { display: block; color: var(--text-faint); font-size: 11px; margin-top: 2px; }
  .tl-lbl.xs { flex: 0.4; }
  .tl-lbl.sm { flex: 0.8; }
  .tl-lbl.lg { flex: 1.2; }

  /* ─── PADDLE DIVIDER ─── */
  .paddle-divider {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 20px;
    margin: 60px 0 0;
    color: var(--text-faint);
  }
  .paddle-divider::before,
  .paddle-divider::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--line-bright);
  }
  /* SVG paddle icon inline */
  .paddle-icon {
    width: 28px;
    height: 28px;
    opacity: 0.3;
  }

  /* ─── PRODUCTION NOTES ─── */
  .notes-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 3px;
    margin-top: 28px;
  }
  .note-card {
    background: rgba(15,56,72,0.4);
    border: 1px solid rgba(220,240,248,0.07);
    padding: 28px;
    border-top: 2px solid var(--pickle-border);
  }
  .note-card h4 {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 14px;
    letter-spacing: 4px;
    color: var(--pickle);
    text-transform: uppercase;
    margin-bottom: 12px;
    font-weight: 400;
  }
  .note-card p {
    font-size: 13px;
    color: var(--text-muted);
    line-height: 1.7;
  }

  /* ─── COURT FOOTER ─── */
  .doc-footer {
    margin-top: 64px;
    padding: 24px 0;
    border-top: 1px solid var(--line-bright);
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  /* Ball graphic in footer */
  .doc-footer::before {
    display: none;
  }
  .doc-footer span {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 12px;
    letter-spacing: 4px;
    color: var(--text-faint);
  }
  .doc-footer .ball {
    width: 18px;
    height: 18px;
    border-radius: 50%;
    background: var(--pickle);
    opacity: 0.3;
    /* Pickleball has holes — simulate with shadow pattern */
    box-shadow:
      3px 3px 0 -1px rgba(0,0,0,0.4),
      -3px -3px 0 -1px rgba(0,0,0,0.4),
      3px -3px 0 -1px rgba(0,0,0,0.4),
      -3px 3px 0 -1px rgba(0,0,0,0.4);
  }

  @media (max-width: 720px) {
    .hero, .main { padding: 40px 24px; }
    .logline-bar, .revision-note { padding: 14px 24px; }
    .scene-header { grid-template-columns: 60px 1fr; }
    .scene-badges { display: none; }
    .scene-body { padding-left: 84px; }
    .notes-grid { grid-template-columns: 1fr; }
    .tl-labels { display: none; }
    .hero-meta { gap: 20px; }
    .meta-item { padding-right: 20px; margin-right: 20px; }
  }
</style>
</head>
<body>

<!-- ═══════════════════════════════ HERO ═══════════════════════════════ -->
<div class="hero">
  <div class="hero-top">
    <div class="hero-eyebrow">Script Outline, Canon Cinematic Short</div>
    <div class="draft-tag">Draft V3.1</div>
  </div>
  <h1 class="hero-title">PERFORMANCE<br><span class="accent">PICKLEBALL</span></h1>
  <div class="hero-sub">A story of sport, community &amp; the people who keep playing</div>
  <div class="hero-meta">
    <div class="meta-item"><label>Format</label><span>Short Documentary</span></div>
    <div class="meta-item"><label>Client</label><span>Canon</span></div>
    <div class="meta-item"><label>Runtime</label><span class="hi">3–4 Minutes</span></div>
    <div class="meta-item"><label>Tone</label><span class="hi">Heartwarming, Inspiring, Authentic</span></div>
  </div>
</div>

<!-- ═══════════════════════════════ LOGLINE ═══════════════════════════════ -->
<div class="logline-bar">
  <span class="logline-label">Logline</span>
  <p>What started as a son watching his mother move freely on a court for the first time in years became a mission to build a sports community in Singapore where every generation belongs.</p>
</div>

<div class="revision-note" style="background: rgba(194,224,64,0.05); border-bottom: 1px solid rgba(194,224,64,0.15); color: var(--text-muted);">
  <strong style="color: var(--pickle);">Film Specifications &nbsp;&nbsp;</strong>
  Format: Short Documentary Film &nbsp;&nbsp;·&nbsp;&nbsp;
  Runtime: 3–4 mins &nbsp;&nbsp;·&nbsp;&nbsp;
  Tone: Heartwarming, Inspiring, Authentic &nbsp;&nbsp;·&nbsp;&nbsp;
  Footage: Sit-down interviews, Staged B-Roll, Archival materials
</div>

<!-- ═══════════════════════════════ MAIN ═══════════════════════════════ -->
<div class="main">

  <!-- ══ ACT 1 ══ -->
  <div class="act-label act-1">
    <span class="act-pill">Act 1: Setup</span>
    <span class="act-desc">Who they are and why it started</span>
    <div class="act-line"></div>
  </div>

  <div class="scenes">

    <!-- SCENE 01 -->
    <div class="scene">
      <div class="scene-header">
        <div class="scene-number">01</div>
        <div class="scene-info">
          <div class="scene-title">Cold Open: The Court</div>
          <div class="scene-timing">No dialogue &nbsp;·&nbsp; <span class="dur">~10–15 sec</span></div>
        </div>
        <div class="scene-badges">
          <span class="badge badge-broll">B-Roll Only</span>
        </div>
      </div>
      <div class="scene-body">
        <p class="scene-description">We open without words. Just the sport doing what it does best. Slow-motion and cinematic montage of a pickleball rally: stroke of a paddle, arc of the ball, squeaking of sneakers on a bright green court. The game is lively and warm.</p>
        <div class="shots">
          <span class="shot">Macro paddle &amp; ball</span>
          <span class="shot">Slow-mo rally</span>
          <span class="shot">Mixed-age players visible</span>
          <span class="shot">Golden hour wide court</span>
        </div>
      </div>
    </div>

    <!-- SCENE 02 -->
    <div class="scene">
      <div class="scene-header">
        <div class="scene-number">02</div>
        <div class="scene-info">
          <div class="scene-title">Meet the Founders</div>
          <div class="scene-timing">Sit-down interview + b-roll &nbsp;·&nbsp; <span class="dur">~30–40 sec</span></div>
          <div class="scene-timing" style="margin-top:6px;"><span style="color:var(--resolve);">📍 Punggol</span> &nbsp;·&nbsp; <span style="color:var(--pickle);">Jeremy, Jeovenne</span></div>
        </div>
        <div class="scene-badges">
          <span class="badge badge-combined">Interview + B-Roll</span>
        </div>
      </div>
      <div class="scene-body">
        <p class="scene-description">We learn who they are, get a sense of their relationship, and hear a short account of them first discovering pickleball: what struck them and what excited them.</p>
        <div class="interview-qs founders">
          <h5>Jeremy and Jeovenne: Suggested Prompts</h5>
          <ul>
            <li>How did you two come to start this together as a couple?</li>
            <li>What was your first experience playing pickleball?</li>
            <li>What made it feel different from other sports?</li>
          </ul>
        </div>
        <div class="shots">
          <span class="shot">Talking head / interview</span>
          <span class="shot">B-Roll: candid scenes of Jeremy and Jeovenne at work</span>
        </div>
      </div>
    </div>

  </div><!-- /act 1 scenes -->

  <!-- ══ ACT 2 ══ -->
  <div class="act-label act-2">
    <span class="act-pill">Act 2: Conflict</span>
    <span class="act-desc">The mission, the mums, and the cost of building</span>
    <div class="act-line"></div>
  </div>

  <div class="scenes">

    <!-- SCENE 03 -->
    <div class="scene heart">
      <div class="scene-header">
        <div class="scene-number">03</div>
        <div class="scene-info">
          <div class="scene-title">The Moms: Inspiration &amp; Insight</div>
          <div class="scene-timing">Sit-down interviews (founders + mums) + b-roll &nbsp;·&nbsp; <span class="dur">~40–60 sec</span></div>
          <div class="scene-timing" style="margin-top:6px;"><span style="color:var(--resolve);">📍 Punggol (live class)</span> &nbsp;·&nbsp; <span style="color:var(--pickle);">The Moms</span></div>
        </div>
        <div class="scene-badges">
          <span class="badge badge-heart">★ Emotional Heart</span>
          <span class="badge badge-combined">Interview + B-Roll</span>
        </div>
      </div>
      <div class="scene-body">
        <p class="scene-description">The founding of Performance Pickleball goes beyond the love of the game, it was also deeply personal. It was the sport that got their own moms active and healthy again. They describe the moment they saw their mothers moving freely and joyfully and how that crystallised everything for them.</p>
        <div class="interview-qs mums">
          <h5>Moms: Suggested Prompts</h5>
          <ul>
            <li>How did you first get involved? (Jeremy as your first coach)</li>
            <li>How does your body feel now compared to before you started?</li>
            <li>What keeps you coming back every week?</li>
          </ul>
        </div>
        <div class="interview-qs founders">
          <h5>Jeremy and Jeovenne: Suggested Prompts</h5>
          <ul>
            <li>Was there a moment you thought this is what you are building towards?</li>
          </ul>
        </div>
        <div class="shots">
          <span class="shot">Sit-down interview</span>
          <span class="shot">B-Roll: moms playing with Jeremy and Jeovenne</span>
          <span class="shot">B-Roll: candid scene of moms at class learning pickleball</span>
        </div>
      </div>
    </div>

    <!-- SCENE 04 -->
    <div class="scene conflict">
      <div class="scene-header">
        <div class="scene-number">04</div>
        <div class="scene-info">
          <div class="scene-title">The Hard Part: Building With Nothing</div>
          <div class="scene-timing">Sit-down interviews (founders + mums) &nbsp;·&nbsp; <span class="dur">~60–80 sec</span></div>
          <div class="scene-timing" style="margin-top:6px;"><span style="color:var(--resolve);">📍 Punggol</span> &nbsp;·&nbsp; <span style="color:var(--pickle);">Jeremy, Jeovenne</span></div>
        </div>
        <div class="scene-badges">
          <span class="badge badge-conflict">▲ Conflict</span>
          <span class="badge badge-interview">Interview</span>
        </div>
      </div>
      <div class="scene-body">
        <p class="scene-description">Jeremy and Jeovenne are honest and raw about how hard the early days were. Though they may be an outfit of 30 people now, they started with no staff, no infrastructure, just the two of them running everything. And the people helping them? Their moms. The same people who inspired the whole thing also played an important role keeping things going especially when times were tough.</p>
        <div class="interview-qs tension">
          <h5>Moms: Suggested Prompts</h5>
          <ul>
            <li>What was your reaction when they first started out?</li>
            <li>How were you involved in the early days?</li>
          </ul>
        </div>
        <div class="interview-qs tension">
          <h5>Jeremy and Jeovenne: Suggested Prompts</h5>
          <ul>
            <li>Were there moments you thought this might not work?</li>
            <li>What did it mean to have your moms around?</li>
            <li>Did you know at the time how worried they were about you?</li>
          </ul>
        </div>
        <div class="shots">
          <span class="shot">B-Roll: Jeremy and Jeovenne alone doing maintenance and building up the space at Punggol (staged)</span>
        </div>
      </div>
    </div>

  </div><!-- /act 2 scenes -->

  <!-- ══ ACT 3 ══ -->
  <div class="act-label act-3">
    <span class="act-pill">Act 3: Resolution</span>
    <span class="act-desc">The community arrives. It was worth it.</span>
    <div class="act-line"></div>
  </div>

  <div class="scenes">

    <!-- SCENE 05 -->
    <div class="scene resolve">
      <div class="scene-header">
        <div class="scene-number">05</div>
        <div class="scene-info">
          <div class="scene-title">The Community: It Finally Clicked</div>
          <div class="scene-timing">Sit-down interview + community b-roll &nbsp;·&nbsp; <span class="dur">~40–50 sec</span></div>
          <div class="scene-timing" style="margin-top:6px;"><span style="color:var(--resolve);">📍 Changi Club</span> &nbsp;·&nbsp; <span style="color:var(--pickle);">Jeremy, Jeovenne, Moms, Full Community</span></div>
        </div>
        <div class="scene-badges">
          <span class="badge badge-resolve">◎ Resolution</span>
          <span class="badge badge-combined">Interview + B-Roll</span>
        </div>
      </div>
      <div class="scene-body">
        <p class="scene-description">The community didn't happen overnight, it took time. Jeremy and Jeovenne recount how the community at Performance Pickleball grew together and how they were there for each other in small and big ways, even through life milestones.</p>
        <div class="interview-qs resolution">
          <h5>Jeremy and Jeovenne: Suggested Prompts</h5>
          <ul>
            <li>When did it start to feel like a real community? Was there a particular moment or interaction?</li>
            <li>What does it feel like now to step back?</li>
            <li>How would you describe PP to someone who has never been there before?</li>
          </ul>
        </div>
        <div class="shots">
          <span class="shot">B-Roll: scenes of Jeremy and Jeovenne playing with the whole community</span>
        </div>
      </div>
    </div>

  </div><!-- /act 3 scenes -->

  <!-- ══ RUNTIME BAR ══ -->
  <div class="timeline">
    <div class="section-label">Runtime Distribution</div>
    <div class="tl-bar">
      <div class="tl-open"    title="Cold Open"></div>
      <div class="tl-found"   title="Founders"></div>
      <div class="tl-heart"   title="The Mums"></div>
      <div class="tl-conflict"title="Conflict"></div>
      <div class="tl-resolve" title="Resolution"></div>
    </div>
    <div class="tl-labels">
      <div class="tl-lbl xs">01, Cold Open<span>~12s</span></div>
      <div class="tl-lbl sm">02, Founders<span>~35s</span></div>
      <div class="tl-lbl lg">03, The Mums<span>~50s</span></div>
      <div class="tl-lbl">04, Hard Part<span>~70s</span></div>
      <div class="tl-lbl">05, Community<span>~45s</span></div>
    </div>
  </div>

  <!-- ══ PADDLE DIVIDER ══ -->
  <div class="paddle-divider">
    <!-- Pickleball paddle SVG -->
    <svg class="paddle-icon" viewBox="0 0 40 56" fill="none" xmlns="http://www.w3.org/2000/svg">
      <ellipse cx="20" cy="20" rx="17" ry="18" fill="currentColor" opacity="0.6"/>
      <rect x="17" y="36" width="6" height="18" rx="3" fill="currentColor" opacity="0.4"/>
      <!-- Holes pattern on paddle face -->
      <circle cx="14" cy="14" r="1.5" fill="var(--court-deep)" opacity="0.8"/>
      <circle cx="20" cy="14" r="1.5" fill="var(--court-deep)" opacity="0.8"/>
      <circle cx="26" cy="14" r="1.5" fill="var(--court-deep)" opacity="0.8"/>
      <circle cx="14" cy="21" r="1.5" fill="var(--court-deep)" opacity="0.8"/>
      <circle cx="20" cy="21" r="1.5" fill="var(--court-deep)" opacity="0.8"/>
      <circle cx="26" cy="21" r="1.5" fill="var(--court-deep)" opacity="0.8"/>
    </svg>
  </div>

  <!-- ══ PRODUCTION NOTES ══ -->
  <div style="margin-top: 20px;">
    <div class="section-label">Production Notes</div>
    <div class="notes-grid">
      <div class="note-card">
        <h4>The Irony to Protect</h4>
        <p>The mums inspired the mission, then showed up every day to help build it, all while quietly worrying whether their children were okay. The conflict isn't commercial doubt; it's parental love in tension with letting go. Preserve that distinction in the edit, it's warmer and more universally relatable than a fear of failure.</p>
      </div>
      <div class="note-card">
        <h4>Mums on Camera, Two Modes</h4>
        <p>Interview them in two registers: reflective (sitting, talking about their fears and their pride) and physical (playing on court, full of life). The contrast between the two is itself part of the story. The same person who was worried is the same person winning points.</p>
      </div>
      <div class="note-card">
        <h4>Canon Visual Direction</h4>
        <p>Shift the visual temperature through the acts: warmer and looser in Act 1, tighter and more intimate in the conflict scene, opening back up in the resolution. The camera's changing relationship to space mirrors the emotional journey.</p>
      </div>
      <div class="note-card">
        <h4>Editing the Conflict Scene</h4>
        <p>Resist the urge to soften Scene 4 too quickly. A beat of genuine discomfort, like a mum admitting she nearly asked them to slow down, will make the resolution in Scene 5 feel earned rather than easy. Documentary audiences reward honesty.</p>
      </div>
    </div>
  </div>

  <!-- ══ FOOTER ══ -->
  <div class="doc-footer">
    <span>Performance Pickleball / Outline V3.1</span>
    <div class="ball"></div>
    <span>For Canon</span>
  </div>

</div><!-- /main outline -->

<!-- ═══════════════════════════════════════════════════════════
     FULL SCRIPT
═══════════════════════════════════════════════════════════ -->

<style>
  /* Script section styles */
  .script-wrapper {
    border-top: 3px solid var(--pickle);
    margin-top: 0;
  }

  .script-header {
    padding: 70px 64px 56px;
    border-bottom: 1px solid var(--line-bright);
    background: linear-gradient(160deg, rgba(194,224,64,0.05) 0%, transparent 60%);
  }
  .script-header-top {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    margin-bottom: 20px;
  }
  .script-eyebrow {
    font-family: 'Barlow Condensed', sans-serif;
    font-size: 12px;
    letter-spacing: 6px;
    color: var(--text-muted);
    text-transform: uppercase;
  }
  .script-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(48px, 8vw, 96px);
    line-height: 0.9;
    letter-spacing: 3px;
  }
  .script-title .accent { color: var(--pickle); }
  .script-meta {
    display: flex;
    gap: 0;
    margin-top: 36px;
    padding-top: 24px;
    border-top: 1px solid var(--line-bright);
    flex-wrap: wrap;
  }
  .script-meta .meta-item {
    padding-right: 36px;
    margin-right: 36px;
    border-right: 1px solid var(--line-bright);
  }
  .script-meta .meta-item:last-child { border-right: none; }

  /* Script body */
  .script-body {
    max-width: 1120px;
    margin: 0 auto;
    padding: 64px 64px 100px;
  }

  /* Script act divider */
  .script-act {
    display: flex;
    align-items: center;
    gap: 14px;
    margin-bottom: 20px;
    margin-top: 60px;
  }
  .script-act:first-child { margin-top: 0; }
  .script-act-pill {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 13px;
    letter-spacing: 4px;
    padding: 5px 16px;
    border-radius: 2px;
    white-space: nowrap;
  }
  .script-act-1 .script-act-pill { background: rgba(56,200,160,0.15); color: var(--resolve); border: 1px solid var(--resolve-border); }
  .script-act-2 .script-act-pill { background: var(--conflict-bg); color: var(--conflict); border: 1px solid var(--conflict-border); }
  .script-act-3 .script-act-pill { background: var(--pickle-dim); color: var(--pickle); border: 1px solid var(--pickle-border); }
  .script-act-desc {
    font-family: 'Barlow Condensed', sans-serif;
    font-size: 13px;
    color: var(--text-faint);
    letter-spacing: 1px;
    font-style: italic;
  }
  .script-act-line { flex: 1; height: 1px; background: var(--line-bright); }

  /* Scene block */
  .script-scene {
    background: rgba(15,56,72,0.4);
    border: 1px solid rgba(220,240,248,0.07);
    border-left: 3px solid transparent;
    margin-bottom: 3px;
    overflow: hidden;
  }
  .script-scene.s-open    { border-left-color: rgba(56,200,160,0.5); }
  .script-scene.s-heart   { border-left-color: var(--pickle); background: rgba(194,224,64,0.03); }
  .script-scene.s-conflict{ border-left-color: var(--conflict); background: var(--conflict-bg); }
  .script-scene.s-resolve { border-left-color: var(--resolve); background: var(--resolve-bg); }

  .script-scene-slug {
    display: flex;
    align-items: center;
    gap: 20px;
    padding: 18px 28px;
    border-bottom: 1px solid rgba(220,240,248,0.06);
    background: rgba(8,28,36,0.3);
  }
  .slug-num {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 13px;
    letter-spacing: 3px;
    color: var(--text-faint);
  }
  .slug-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 15px;
    letter-spacing: 4px;
    color: var(--text-primary);
    text-transform: uppercase;
  }
  .slug-divider { color: var(--text-faint); font-size: 12px; }
  .slug-note {
    font-family: 'Barlow Condensed', sans-serif;
    font-size: 12px;
    letter-spacing: 2px;
    color: var(--text-muted);
    text-transform: uppercase;
    margin-left: auto;
  }

  /* Script content rows */
  .script-content { padding: 0 28px 28px; }

  .script-row {
    display: grid;
    grid-template-columns: 120px 1fr;
    gap: 24px;
    padding: 16px 0;
    border-bottom: 1px solid rgba(220,240,248,0.04);
  }
  .script-row:last-child { border-bottom: none; }

  .row-type {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 11px;
    letter-spacing: 3px;
    padding-top: 2px;
    text-transform: uppercase;
  }
  .type-action    { color: var(--text-faint); }
  .type-vo        { color: var(--pickle); }
  .type-interview { color: var(--resolve); }
  .type-direction { color: var(--conflict); }

  .row-content { }

  .row-speaker {
    font-family: 'Barlow Condensed', sans-serif;
    font-size: 11px;
    letter-spacing: 3px;
    color: var(--text-faint);
    text-transform: uppercase;
    margin-bottom: 4px;
    font-weight: 600;
  }

  .row-text {
    font-family: 'Nunito Sans', sans-serif;
    font-size: 14px;
    line-height: 1.75;
  }
  .type-action + .row-content .row-text    { color: var(--text-muted); font-style: italic; }
  .type-vo + .row-content .row-text        { color: var(--text-primary); }
  .type-interview + .row-content .row-text { color: #a8d8e8; }
  .type-direction + .row-content .row-text { color: var(--conflict); font-size: 12px; font-family: 'Barlow Condensed', sans-serif; letter-spacing: 1px; text-transform: uppercase; }

  /* Legend */
  .script-legend {
    display: flex;
    gap: 28px;
    margin-bottom: 36px;
    padding: 14px 20px;
    background: rgba(8,28,36,0.4);
    border: 1px solid rgba(220,240,248,0.06);
    border-radius: 2px;
    flex-wrap: wrap;
  }
  .legend-item {
    display: flex;
    align-items: center;
    gap: 8px;
    font-family: 'Barlow Condensed', sans-serif;
    font-size: 12px;
    letter-spacing: 2px;
    color: var(--text-muted);
    text-transform: uppercase;
  }
  .legend-dot {
    width: 8px; height: 8px;
    border-radius: 1px;
  }
  .ld-vo        { background: var(--pickle); }
  .ld-interview { background: var(--resolve); }
  .ld-action    { background: var(--text-faint); }
  .ld-direction { background: var(--conflict); }

  .script-footer {
    margin-top: 64px;
    padding-top: 24px;
    border-top: 1px solid var(--line-bright);
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .script-footer span {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 12px;
    letter-spacing: 4px;
    color: var(--text-faint);
  }
  .script-footer .ball {
    width: 18px; height: 18px;
    border-radius: 50%;
    background: var(--pickle);
    opacity: 0.3;
    box-shadow: 3px 3px 0 -1px rgba(0,0,0,0.4), -3px -3px 0 -1px rgba(0,0,0,0.4), 3px -3px 0 -1px rgba(0,0,0,0.4), -3px 3px 0 -1px rgba(0,0,0,0.4);
  }

  @media (max-width: 720px) {
    .script-header, .script-body { padding: 40px 24px; }
    .script-row { grid-template-columns: 80px 1fr; gap: 14px; }
    .script-legend { gap: 14px; }
  }
</style>

<div class="script-wrapper">

  <!-- SCRIPT HEADER -->
  <div class="script-header">
    <div class="script-header-top">
      <div class="script-eyebrow">Full Script, Canon Cinematic Short</div>
      <div class="draft-tag">Script Draft 1</div>
    </div>
    <div class="script-title">FULL<br><span class="accent">SCRIPT</span></div>
    <div class="script-meta">
      <div class="meta-item"><label>Narration Split</label><span class="hi">70% VO / 30% Interview</span></div>
      <div class="meta-item"><label>Runtime</label><span class="hi">3–4 Minutes</span></div>
      <div class="meta-item"><label>Tone</label><span>Heartwarming, Inspiring, Authentic</span></div>
    </div>
  </div>

  <!-- SCRIPT BODY -->
  <div class="script-body">

    <!-- LEGEND -->
    <div class="script-legend">
      <div class="legend-item"><div class="legend-dot ld-vo"></div>Voiceover (Subject, over B-Roll)</div>
      <div class="legend-item"><div class="legend-dot ld-interview"></div>Interview (On Camera)</div>
      <div class="legend-item"><div class="legend-dot ld-action"></div>Action / B-Roll</div>
      <div class="legend-item"><div class="legend-dot ld-direction"></div>Direction</div>
    </div>

    <!-- ══ ACT 1 ══ -->
    <div class="script-act script-act-1">
      <span class="script-act-pill">Act 1: Setup</span>
      <span class="script-act-desc">Who they are and why it started</span>
      <div class="script-act-line"></div>
    </div>

    <!-- SCENE 01 -->
    <div class="script-scene s-open">
      <div class="script-scene-slug">
        <span class="slug-num">01</span>
        <span class="slug-divider">/</span>
        <span class="slug-title">Cold Open: The Court</span>
        <span class="slug-note">B-Roll / No Dialogue / ~10–15s &nbsp;·&nbsp; 📍 Changi Club &nbsp;·&nbsp; Jeremy, Jeovenne</span>
      </div>
      <div class="script-content">
        <div class="script-row">
          <span class="row-type type-action">Action</span>
          <div class="row-content">
            <div class="row-text">We open without words. Just the sport doing what it does best. Slow-motion shots of a rally in progress, the satisfying crack of a paddle, a ball arcing through warm light, sneakers squeaking on the court, faces caught mid-point.</div>
          </div>
        </div>
        <div class="script-row">
          <span class="row-type type-direction">Direction</span>
          <div class="row-content">
            <div class="row-text">No narration. No music yet, or something very sparse. Let the ambient sounds of the court breathe. Hold on these images longer than feels comfortable.</div>
          </div>
        </div>
        <div class="script-row">
          <span class="row-type type-action">Action</span>
          <div class="row-content">
            <div class="row-text">Pull back to a wide golden shot of the full court. Players of all ages visible in the frame. Music begins to swell gently as we cut to black for the title card.</div>
          </div>
        </div>
      </div>
    </div>

    <!-- SCENE 02 -->
    <div class="script-scene">
      <div class="script-scene-slug">
        <span class="slug-num">02</span>
        <span class="slug-divider">/</span>
        <span class="slug-title">Meet the Founders</span>
        <span class="slug-note">VO + Interview / ~30–40s &nbsp;·&nbsp; 📍 Punggol &nbsp;·&nbsp; Jeremy, Jeovenne</span>
      </div>
      <div class="script-content">
        <div class="script-row">
          <span class="row-type type-action">Action</span>
          <div class="row-content">
            <div class="row-text">B-roll of the founders on court, coaching a session, easy and in their element. Warm, observational. We watch them before we hear them.</div>
          </div>
        </div>
        <div class="script-row">
          <span class="row-type type-vo">Voiceover</span>
          <div class="row-content">
            <div class="row-speaker">Jeremy / Jeovenne</div>
            <div class="row-text">"We kept coming back to this one thing. Anyone can play. It doesn't matter how old you are, how fit you are. You just pick up a paddle and you're in."</div>
          </div>
        </div>
        <div class="script-row">
          <span class="row-type type-vo">Voiceover</span>
          <div class="row-content">
            <div class="row-speaker">Jeremy / Jeovenne</div>
            <div class="row-text">"That was what got us. We looked at this sport and thought, nobody else in Singapore is really building something around this yet. So why not us?"</div>
          </div>
        </div>
        <div class="script-row">
          <span class="row-type type-interview">Interview</span>
          <div class="row-content">
            <div class="row-speaker">Jeremy / Jeovenne</div>
            <div class="row-text">"When we first picked up a paddle, we just saw something that no one else was really talking about yet. This sport doesn't care how old you are. You can be twenty or sixty and you're both genuinely in the game."</div>
          </div>
        </div>
        <div class="script-row">
          <span class="row-type type-action">Action</span>
          <div class="row-content">
            <div class="row-text">Cut to b-roll of mixed age players in a lively rally. Wide shot showing the range of generations on the same court.</div>
          </div>
        </div>
      </div>
    </div>

    <!-- ══ ACT 2 ══ -->
    <div class="script-act script-act-2">
      <span class="script-act-pill">Act 2: Conflict</span>
      <span class="script-act-desc">The mission, the mums, and the cost of building</span>
      <div class="script-act-line"></div>
    </div>

    <!-- SCENE 03 -->
    <div class="script-scene s-heart">
      <div class="script-scene-slug">
        <span class="slug-num">03</span>
        <span class="slug-divider">/</span>
        <span class="slug-title">The Moms: Inspiration and Insight</span>
        <span class="slug-note">VO + Interview / ~40–60s &nbsp;·&nbsp; 📍 Punggol (live class) &nbsp;·&nbsp; The Moms</span>
      </div>
      <div class="script-content">
        <div class="script-row">
          <span class="row-type type-vo">Voiceover</span>
          <div class="row-content">
            <div class="row-speaker">Jeremy / Jeovenne</div>
            <div class="row-text">"But honestly, the moment that really made everything click for us didn't happen on a court. It happened at home."</div>
          </div>
        </div>
        <div class="script-row">
          <span class="row-type type-vo">Voiceover</span>
          <div class="row-content">
            <div class="row-speaker">Jeremy / Jeovenne</div>
            <div class="row-text">"My mum had kind of stepped back from being active for a while. And then she tried pickleball, and she just didn't stop."</div>
          </div>
        </div>
        <div class="script-row">
          <span class="row-type type-interview">Interview</span>
          <div class="row-content">
            <div class="row-speaker">Jeremy / Jeovenne</div>
            <div class="row-text">"Watching my mum move like that, genuinely competing, laughing out there. I hadn't seen that kind of energy from her in a really long time. And I thought, if this sport can do that for her, it can do that for a lot of people."</div>
          </div>
        </div>
        <div class="script-row">
          <span class="row-type type-action">Action</span>
          <div class="row-content">
            <div class="row-text">Cut to the mums in a sit-down interview. Warm framing, court softly visible behind them.</div>
          </div>
        </div>
        <div class="script-row">
          <span class="row-type type-interview">Interview</span>
          <div class="row-content">
            <div class="row-speaker">Mom</div>
            <div class="row-text">"I thought, how hard can this be? And then I was completely hooked. My body feels so much better now. I sleep better. I feel stronger. And I have friends here now."</div>
          </div>
        </div>
        <div class="script-row">
          <span class="row-type type-action">Action</span>
          <div class="row-content">
            <div class="row-text">Cut to the mums actually playing. Dynamic, energetic shots. Full of life. Let the footage speak for itself for a beat before the VO returns.</div>
          </div>
        </div>
        <div class="script-row">
          <span class="row-type type-vo">Voiceover</span>
          <div class="row-content">
            <div class="row-speaker">Jeremy / Jeovenne</div>
            <div class="row-text">"That was the proof for us. Age was never the point. It was always about movement. About feeling like you belong somewhere."</div>
          </div>
        </div>
      </div>
    </div>

    <!-- SCENE 04 -->
    <div class="script-scene s-conflict">
      <div class="script-scene-slug">
        <span class="slug-num">04</span>
        <span class="slug-divider">/</span>
        <span class="slug-title">The Hard Part: Building With Nothing</span>
        <span class="slug-note">VO + Interview / ~60–80s &nbsp;·&nbsp; 📍 Punggol &nbsp;·&nbsp; Jeremy, Jeovenne</span>
      </div>
      <div class="script-content">
        <div class="script-row">
          <span class="row-type type-vo">Voiceover</span>
          <div class="row-content">
            <div class="row-speaker">Jeremy / Jeovenne</div>
            <div class="row-text">"The early days were not pretty. No team, no budget, no guarantee that anyone was going to show up. It was just the two of us doing everything."</div>
          </div>
        </div>
        <div class="script-row">
          <span class="row-type type-vo">Voiceover</span>
          <div class="row-content">
            <div class="row-speaker">Jeremy / Jeovenne</div>
            <div class="row-text">"Every session, every setup, every teardown. And when we needed an extra pair of hands, we called our mums."</div>
          </div>
        </div>
        <div class="script-row">
          <span class="row-type type-action">Action</span>
          <div class="row-content">
            <div class="row-text">B-roll: a mum helping set up equipment, laying out paddles, carrying gear. Candid and real, not staged.</div>
          </div>
        </div>
        <div class="script-row">
          <span class="row-type type-interview">Interview</span>
          <div class="row-content">
            <div class="row-speaker">Mom</div>
            <div class="row-text">"I was happy to be there and help. But I was also watching them very closely. Were they eating? Were they sleeping properly? They were putting so much of themselves into this and I just wanted to make sure they were okay."</div>
          </div>
        </div>
        <div class="script-row">
          <span class="row-type type-vo">Voiceover</span>
          <div class="row-content">
            <div class="row-speaker">Mom</div>
            <div class="row-text">"I never said anything to them about it. I didn't want to make it harder. But yes, I was worried. Not about the business. About them."</div>
          </div>
        </div>
        <div class="script-row">
          <span class="row-type type-interview">Interview</span>
          <div class="row-content">
            <div class="row-speaker">Jeremy / Jeovenne</div>
            <div class="row-text">"I don't think we really knew at the time how much they were carrying. They just kept showing up. Every single time."</div>
          </div>
        </div>
      </div>
    </div>

    <!-- ══ ACT 3 ══ -->
    <div class="script-act script-act-3">
      <span class="script-act-pill">Act 3: Resolution</span>
      <span class="script-act-desc">The community arrives. It was worth it.</span>
      <div class="script-act-line"></div>
    </div>

    <!-- SCENE 05 -->
    <div class="script-scene s-resolve">
      <div class="script-scene-slug">
        <span class="slug-num">05</span>
        <span class="slug-divider">/</span>
        <span class="slug-title">The Community: It Finally Clicked</span>
        <span class="slug-note">VO + Interview + B-Roll / ~40–50s &nbsp;·&nbsp; 📍 Changi Club &nbsp;·&nbsp; Jeremy, Jeovenne, Moms, Full Community</span>
      </div>
      <div class="script-content">
        <div class="script-row">
          <span class="row-type type-vo">Voiceover</span>
          <div class="row-content">
            <div class="row-speaker">Jeremy / Jeovenne</div>
            <div class="row-text">"It didn't happen overnight. But slowly, people started coming back. And then they started bringing their friends."</div>
          </div>
        </div>
        <div class="script-row">
          <span class="row-type type-vo">Voiceover</span>
          <div class="row-content">
            <div class="row-speaker">Jeremy / Jeovenne</div>
            <div class="row-text">"Strangers became regulars. Regulars became friends. At some point it stopped feeling like we were building something and started feeling like it was already there."</div>
          </div>
        </div>
        <div class="script-row">
          <span class="row-type type-action">Action</span>
          <div class="row-content">
            <div class="row-text">Wide shots of the court fully alive. Mixed ages in every direction. Laughter, rallies, people talking between points. Let this run for a moment before the interview cuts in.</div>
          </div>
        </div>
        <div class="script-row">
          <span class="row-type type-interview">Interview</span>
          <div class="row-content">
            <div class="row-speaker">Jeremy / Jeovenne</div>
            <div class="row-text">"There was this one session where I looked around and just thought, okay, this is it. This is exactly what we were trying to build. It took a while to get here but it was worth every single bit of it."</div>
          </div>
        </div>
        <div class="script-row">
          <span class="row-type type-vo">Voiceover</span>
          <div class="row-content">
            <div class="row-speaker">Mom</div>
            <div class="row-text">"All that worrying I did. I look at what they've built now and I think, yeah. They were going to be just fine."</div>
          </div>
        </div>
        <div class="script-row">
          <span class="row-type type-interview">Interview</span>
          <div class="row-content">
            <div class="row-speaker">Mom</div>
            <div class="row-text">"Now I just feel proud. Very proud of them."</div>
          </div>
        </div>
        <div class="script-row">
          <span class="row-type type-action">Action</span>
          <div class="row-content">
            <div class="row-text">Echo of the cold open: the same court, now loaded with meaning. A mum mid-rally. A founder watching from the side. The ball in the air. Hold on this.</div>
          </div>
        </div>
        <div class="script-row">
          <span class="row-type type-vo">Voiceover</span>
          <div class="row-content">
            <div class="row-speaker">Jeremy / Jeovenne</div>
            <div class="row-text">"This is what we always wanted. A place where it doesn't matter how old you are, where you're from, how good you are. Everyone's welcome. Everyone belongs here."</div>
          </div>
        </div>
        <div class="script-row">
          <span class="row-type type-direction">Direction</span>
          <div class="row-content">
            <div class="row-text">Fade to black. Title card: PERFORMANCE PICKLEBALL. Hold. Canon logo.</div>
          </div>
        </div>
      </div>
    </div>

    <!-- SCRIPT FOOTER -->
    <div class="script-footer">
      <span>Performance Pickleball / Full Script Draft 1</span>
      <div class="ball"></div>
      <span>For Canon</span>
    </div>

  </div><!-- /script-body -->
</div><!-- /script-wrapper -->

</body>
</html>
