<script>
  import { onMount, onDestroy } from 'svelte';

  let scene;
  let isHovered = false;

  let mx = 0, my = 0;
  let smx = 0, smy = 0;
  let cx = 0, cy = 0;
  let curX = 0, curY = 0;
  let curRX = 0, curRY = 0;
  let rafId;

  function lerp(a, b, t) { return a + (b - a) * t; }

  function handleMouseMove(e) {
    const r = scene.getBoundingClientRect();
    mx = (e.clientX - r.left) / r.width * 2 - 1;
    my = (e.clientY - r.top)  / r.height * 2 - 1;
    cx = e.clientX;
    cy = e.clientY;
  }

  function handleMouseEnter() { isHovered = true; }

  function handleMouseLeave() {
    isHovered = false;
    mx = 0; my = 0;
  }

  let imgStyle   = '';
  let vigStyle   = '';
  let foreStyle  = '';
  let overStyle  = '';
  let curStyle   = '';
  let curRStyle  = '';

  function tick() {
    smx = lerp(smx, mx, 0.07);
    smy = lerp(smy, my, 0.07);
    curX  = lerp(curX,  cx, 0.18);
    curY  = lerp(curY,  cy, 0.18);
    curRX = lerp(curRX, cx, 0.09);
    curRY = lerp(curRY, cy, 0.09);

    // image moves slowest — tiny offset so it never leaves the frame
    imgStyle  = `transform: translate(calc(-50% + ${smx * -14}px), calc(-50% + ${smy * -9}px)) scale(1.08);`;
    vigStyle  = `transform: translate(${smx * -3}px, ${smy * -2}px);`;
    foreStyle = `transform: translate(${smx * 20}px, ${smy * 13}px);`;
    overStyle = `transform: translate(${smx * 9}px,  ${smy * 6}px);`;

    curStyle  = `left:${curX}px; top:${curY}px;`;
    curRStyle = `left:${curRX}px; top:${curRY}px;`;

    rafId = requestAnimationFrame(tick);
  }

  onMount(()  => { rafId = requestAnimationFrame(tick); });
  onDestroy(() => { cancelAnimationFrame(rafId); });
</script>

<div class="cursor"      class:hovered={isHovered} style={curStyle}></div>
<div class="cursor-ring" class:hovered={isHovered} style={curRStyle}></div>

<!-- svelte-ignore a11y-no-static-element-interactions -->
<div
  class="scene"
  class:hovered={isHovered}
  bind:this={scene}
  on:mousemove={handleMouseMove}
  on:mouseenter={handleMouseEnter}
  on:mouseleave={handleMouseLeave}
>

  <!-- Full-screen image — centered absolutely, scaled up so parallax shift never shows edges -->
  <img
    class="hero-img"
    style={imgStyle}
    src="https://raw.githubusercontent.com/OmkarpatilGithub/Omeva_store/main/static/hanging.jpg"
    alt="OMEVA T-shirts on rack"
  />

  <!-- Directional vignette -->
  <div class="layer-vignette" style={vigStyle}></div>

  <!-- Meta top-right only -->
  <div class="layer-foreground" style={foreStyle}>
    <div class="fore-meta">
      <div class="fore-meta-line">Drop 001</div>
      <div class="fore-meta-line">Rawprint</div>
      <div class="fore-meta-line">Pune — 2025</div>
    </div>
  </div>

  <!-- Hover reveal -->
  <div class="layer-overlay" style={overStyle}>
    <div class="overlay-content overlay-eyebrow">Heavyweight Cotton — Custom Print</div>
    <div class="fore-brand always-visible">OMEVA<em>.</em></div>
    <div class="overlay-content overlay-tag">WEAR YOUR<br /><em>STORY.</em></div>
    <div class="overlay-content overlay-sub">Zero middlemen. You design it, we print it.</div>
    <a
      href="https://wa.me/919270905007"
      target="_blank"
      rel="noopener noreferrer"
      class="overlay-content overlay-btn"
    >
      <span>Order on WhatsApp</span>
      <span class="ico">→</span>
    </a>
  </div>

  <div class="scene-tagline">Pune-born. Print-forward.</div>
</div>

<style>
  /* ── Cursor ── */
  .cursor {
    position: fixed;
    width: 10px; height: 10px;
    background: #CBB4E3;
    border-radius: 50%;
    pointer-events: none;
    z-index: 9999;
    transform: translate(-50%, -50%);
    transition: width 0.3s ease, height 0.3s ease;
  }
  .cursor.hovered { width: 6px; height: 6px; }

  .cursor-ring {
    position: fixed;
    width: 36px; height: 36px;
    border: 1.5px solid rgba(138,111,168,0.45);
    border-radius: 50%;
    pointer-events: none;
    z-index: 9998;
    transform: translate(-50%, -50%);
    transition: width 0.4s ease, height 0.4s ease, border-color 0.3s ease;
  }
  .cursor-ring.hovered {
    width: 56px; height: 56px;
    border-color: rgba(203,180,227,0.85);
  }

  /* ── Scene ── */
  .scene {
    position: relative;
    width: 100%;
    height: 100vh;
    overflow: hidden;
    cursor: none;
    background: #0D0B11;
  }

  /* ── Hero image — centered, scaled, parallax via transform ── */
  .hero-img {
    position: absolute;
    top: 50%;
    left: 50%;
    /* start centered; JS overrides with translate + scale */
    transform: translate(-50%, -50%) scale(1.08);
    /* fill viewport in both axes */
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center 18%;
    will-change: transform;
    display: block;
  }

  /* ── Vignette ── */
  .layer-vignette {
    position: absolute;
    inset: 0;
    will-change: transform;
    background:
      linear-gradient(to right, rgba(13,11,17,0.82) 0%, rgba(13,11,17,0.25) 52%, rgba(13,11,17,0.08) 100%),
      linear-gradient(to top,   rgba(13,11,17,0.70) 0%, transparent 46%);
    pointer-events: none;
  }

  /* ── Foreground meta (top-right only) ── */
  .layer-foreground {
    position: absolute;
    inset: 0;
    display: flex;
    align-items: flex-start;
    justify-content: flex-end;
    padding: 36px 7%;
    pointer-events: none;
    will-change: transform;
  }

  .fore-meta { text-align: right; }
  .fore-meta-line {
    font-family: 'JetBrains Mono', monospace;
    font-size: 10px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: rgba(245,242,247,0.4);
    line-height: 2.2;
  }

  /* OMEVA sits above tagline, always visible */
  .fore-brand {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(48px, 7vw, 88px);
    color: #F5F2F7;
    letter-spacing: 0.02em;
    line-height: 1;
    margin-bottom: 4px;
    opacity: 1;
    transition: opacity 0.4s ease;
  }
  .fore-brand em { color: #8A6FA8; font-style: normal; }

  /* dim brand slightly on hover so tagline takes focus */
  .scene.hovered .fore-brand { opacity: 0.55; }

  /* ── Hover overlay ── */
  .layer-overlay {
    position: absolute;
    inset: 0;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: flex-end;
    padding: 0 7% 7%;
    pointer-events: none;
    will-change: transform;
  }

  .overlay-content {
    opacity: 0;
    transform: translateY(32px);
    transition:
      opacity   0.55s cubic-bezier(0.16,1,0.3,1),
      transform 0.55s cubic-bezier(0.16,1,0.3,1);
  }
  .scene.hovered .overlay-content { opacity: 1; transform: translateY(0); }

  .overlay-eyebrow {
    font-family: 'JetBrains Mono', monospace;
    font-size: 10px;
    letter-spacing: 4px;
    text-transform: uppercase;
    color: rgba(203,180,227,0.8);
    margin-bottom: 14px;
    transition-delay: 0s;
  }

  .overlay-tag {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(52px, 8vw, 100px);
    line-height: 0.88;
    color: #F5F2F7;
    letter-spacing: 0.02em;
    margin-bottom: 10px;
    transition-delay: 0.07s;
  }
  .overlay-tag em { font-style: normal; color: #CBB4E3; }

  .overlay-sub {
    font-family: 'DM Sans', sans-serif;
    font-size: 13px;
    font-weight: 300;
    font-style: italic;
    color: rgba(245,242,247,0.55);
    letter-spacing: 0.5px;
    margin-bottom: 34px;
    transition-delay: 0.12s;
  }

  .overlay-btn {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    padding: 14px 32px;
    background: transparent;
    color: #F5F2F7;
    font-family: 'DM Sans', sans-serif;
    font-size: 11px;
    font-weight: 600;
    letter-spacing: 3px;
    text-transform: uppercase;
    text-decoration: none;
    border: 1.5px solid rgba(138,111,168,0.65);
    position: relative;
    overflow: hidden;
    pointer-events: all;
    cursor: pointer;
    transition-delay: 0.17s;
    transition:
      border-color  0.3s ease,
      opacity       0.55s cubic-bezier(0.16,1,0.3,1),
      transform     0.55s cubic-bezier(0.16,1,0.3,1);
  }

  .overlay-btn::before {
    content: '';
    position: absolute;
    inset: 0;
    background: #8A6FA8;
    transform: scaleX(0);
    transform-origin: left;
    transition: transform 0.4s cubic-bezier(0.16,1,0.3,1);
  }
  .overlay-btn:hover { border-color: #8A6FA8; }
  .overlay-btn:hover::before { transform: scaleX(1); }

  .overlay-btn span { position: relative; z-index: 1; }
  .overlay-btn .ico {
    position: relative; z-index: 1;
    display: inline-block;
    transition: transform 0.3s ease;
  }
  .overlay-btn:hover .ico { transform: translateX(5px); }

  /* ── Static tagline ── */
  .scene-tagline {
    position: absolute;
    bottom: 7%; right: 7%;
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(13px, 1.4vw, 18px);
    color: rgba(245,242,247,0.28);
    letter-spacing: 5px;
    text-transform: uppercase;
    transition: opacity 0.4s ease;
    pointer-events: none;
  }
  .scene.hovered .scene-tagline { opacity: 0; }
</style>
