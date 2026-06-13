<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>NYTRIXX — Anubhav Singh</title>
<meta name="description" content="Anubhav Singh — 15-year-old web developer, AI builder, and future entrepreneur. Building modern digital experiences under the NYTRIXX brand.">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@100;200;300;400;500;600;700;900&family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400;1,900&family=Space+Grotesk:wght@300;400;500;700&display=swap" rel="stylesheet">
<style>
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

:root {
  --bg: #000000;
  --bg2: #0D0D0D;
  --card: rgba(255,255,255,0.04);
  --border: rgba(255,255,255,0.08);
  --text: #FFFFFF;
  --muted: #A0A0A0;
  --faint: rgba(255,255,255,0.03);
}

html { scroll-behavior: smooth; }

body {
  background: var(--bg);
  color: var(--text);
  font-family: 'Space Grotesk', sans-serif;
  overflow-x: hidden;
  cursor: none;
}

/* ── LOADER ── */
#loader {
  position: fixed; inset: 0; z-index: 9999;
  background: #000;
  display: flex; flex-direction: column;
  align-items: center; justify-content: center;
  gap: 32px;
}
#loader-brand {
  font-family: 'Inter', sans-serif;
  font-weight: 900;
  font-size: clamp(28px, 6vw, 60px);
  letter-spacing: 0.25em;
  opacity: 0;
  animation: loaderBrandIn 0.8s 0.3s forwards;
}
#loader-line {
  width: 0; height: 1px;
  background: rgba(255,255,255,0.4);
  animation: loaderLine 1.4s 0.8s ease-out forwards;
}
#loader-sub {
  font-size: 11px; letter-spacing: 0.3em;
  color: var(--muted); text-transform: uppercase;
  opacity: 0;
  animation: loaderBrandIn 0.6s 1.6s forwards;
}
@keyframes loaderBrandIn { to { opacity: 1; } }
@keyframes loaderLine { to { width: 180px; } }
#loader.out {
  animation: loaderOut 0.7s 2.6s ease-in forwards;
}
@keyframes loaderOut {
  to { opacity: 0; pointer-events: none; }
}

/* ── CUSTOM CURSOR ── */
#cursor {
  width: 12px; height: 12px;
  border-radius: 50%;
  background: #fff;
  position: fixed; top: 0; left: 0;
  pointer-events: none; z-index: 9998;
  transform: translate(-50%,-50%);
  transition: transform 0.08s, width 0.3s, height 0.3s, background 0.3s;
  mix-blend-mode: difference;
}
#cursor-ring {
  width: 40px; height: 40px;
  border-radius: 50%;
  border: 1px solid rgba(255,255,255,0.3);
  position: fixed; top: 0; left: 0;
  pointer-events: none; z-index: 9997;
  transform: translate(-50%,-50%);
  transition: all 0.18s ease;
}
body.hovering #cursor { width: 20px; height: 20px; }
body.hovering #cursor-ring { width: 60px; height: 60px; border-color: rgba(255,255,255,0.6); }

/* ── SCROLL PROGRESS ── */
#progress {
  position: fixed; top: 0; left: 0;
  height: 2px; background: #fff;
  width: 0%; z-index: 9990;
  transition: width 0.1s;
}

/* ── MOUSE GLOW ── */
#glow {
  position: fixed;
  width: 600px; height: 600px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(255,255,255,0.04) 0%, transparent 70%);
  pointer-events: none; z-index: 1;
  transform: translate(-50%,-50%);
  transition: all 0.3s ease;
}

/* ── NAVBAR ── */
nav {
  position: fixed; top: 0; left: 0; right: 0; z-index: 100;
  padding: 20px 48px;
  display: flex; align-items: center; justify-content: space-between;
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  background: rgba(0,0,0,0.6);
  border-bottom: 1px solid var(--border);
  transition: all 0.3s;
}
.nav-logo {
  font-family: 'Inter', sans-serif;
  font-weight: 900;
  font-size: 18px;
  letter-spacing: 0.18em;
  text-decoration: none;
  color: #fff;
}
.nav-links { display: flex; gap: 40px; list-style: none; }
.nav-links a {
  text-decoration: none; color: var(--muted);
  font-size: 12px; letter-spacing: 0.15em; text-transform: uppercase;
  font-weight: 400;
  transition: color 0.3s;
  position: relative;
}
.nav-links a::after {
  content: ''; position: absolute; bottom: -4px; left: 0;
  width: 0; height: 1px; background: #fff;
  transition: width 0.3s;
}
.nav-links a:hover { color: #fff; }
.nav-links a:hover::after { width: 100%; }
.nav-hamburger { display: none; flex-direction: column; gap: 5px; cursor: pointer; }
.nav-hamburger span { display: block; width: 22px; height: 1px; background: #fff; }

/* ── PARTICLES ── */
#particles {
  position: fixed; inset: 0; z-index: 0;
  pointer-events: none;
}

/* ── SECTIONS ── */
section { position: relative; z-index: 2; }

/* ── HERO ── */
#hero {
  min-height: 100vh;
  display: flex; flex-direction: column; justify-content: center;
  padding: 120px 48px 80px;
  overflow: hidden;
}
.hero-ghost-text {
  position: absolute;
  font-family: 'Inter', sans-serif;
  font-weight: 900;
  font-size: clamp(100px, 18vw, 280px);
  color: rgba(255,255,255,0.025);
  letter-spacing: -0.03em;
  white-space: nowrap;
  pointer-events: none;
  user-select: none;
  line-height: 1;
}
.hero-ghost-1 { top: 10%; left: -5%; animation: floatH 18s ease-in-out infinite; }
.hero-ghost-2 { bottom: 5%; right: -8%; animation: floatH 22s ease-in-out infinite reverse; }
.hero-ghost-3 { top: 50%; left: 20%; transform: translateY(-50%); animation: floatH 25s ease-in-out infinite 4s; }
@keyframes floatH {
  0%,100% { transform: translateY(0) translateX(0); }
  33% { transform: translateY(-20px) translateX(10px); }
  66% { transform: translateY(15px) translateX(-8px); }
}

.hero-eyebrow {
  font-size: 11px; letter-spacing: 0.35em; text-transform: uppercase;
  color: var(--muted); margin-bottom: 32px;
  opacity: 0; animation: fadeUp 0.8s 3s forwards;
}
.hero-name {
  font-family: 'Inter', sans-serif;
  font-weight: 900;
  font-size: clamp(72px, 14vw, 200px);
  line-height: 0.88;
  letter-spacing: -0.04em;
  margin-bottom: 48px;
  opacity: 0; animation: fadeUp 0.9s 3.15s forwards;
}
.hero-name span { display: block; }
.hero-roles {
  display: flex; gap: 40px; flex-wrap: wrap;
  margin-bottom: 48px;
  opacity: 0; animation: fadeUp 0.8s 3.3s forwards;
}
.hero-role {
  font-size: 13px; letter-spacing: 0.2em; text-transform: uppercase;
  color: var(--muted);
  display: flex; align-items: center; gap: 12px;
}
.hero-role::before {
  content: '';
  width: 24px; height: 1px; background: rgba(255,255,255,0.3);
}
.hero-desc {
  max-width: 480px;
  font-size: 16px; line-height: 1.7;
  color: var(--muted);
  margin-bottom: 56px;
  opacity: 0; animation: fadeUp 0.8s 3.45s forwards;
}
.hero-btns {
  display: flex; gap: 16px; flex-wrap: wrap;
  opacity: 0; animation: fadeUp 0.8s 3.6s forwards;
}
.btn {
  display: inline-flex; align-items: center; gap: 10px;
  padding: 16px 32px;
  font-size: 12px; letter-spacing: 0.18em; text-transform: uppercase;
  font-family: 'Space Grotesk', sans-serif;
  font-weight: 500;
  text-decoration: none;
  border-radius: 2px;
  transition: all 0.3s;
  position: relative; overflow: hidden;
  cursor: none;
}
.btn-primary {
  background: #fff; color: #000;
  border: 1px solid #fff;
}
.btn-primary:hover { background: transparent; color: #fff; }
.btn-ghost {
  background: transparent; color: #fff;
  border: 1px solid var(--border);
}
.btn-ghost:hover { border-color: rgba(255,255,255,0.4); background: rgba(255,255,255,0.04); }
.hero-scroll-hint {
  position: absolute; bottom: 40px; left: 48px;
  font-size: 10px; letter-spacing: 0.3em; text-transform: uppercase; color: var(--muted);
  display: flex; align-items: center; gap: 16px;
  opacity: 0; animation: fadeUp 0.8s 3.9s forwards;
}
.hero-scroll-hint::before {
  content: ''; width: 40px; height: 1px; background: rgba(255,255,255,0.2);
}

@keyframes fadeUp {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}

/* ── DIVIDER ── */
.divider {
  width: 100%; height: 1px;
  background: var(--border);
  margin: 0 48px;
  width: calc(100% - 96px);
}

/* ── SECTION LABEL ── */
.section-label {
  font-size: 10px; letter-spacing: 0.4em; text-transform: uppercase;
  color: var(--muted); margin-bottom: 24px;
  display: flex; align-items: center; gap: 20px;
}
.section-label::before {
  content: ''; width: 32px; height: 1px; background: rgba(255,255,255,0.3);
}

/* ── ABOUT ── */
#about {
  padding: 140px 48px;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 80px;
  align-items: center;
}
.about-left { }
.about-title {
  font-family: 'Inter', sans-serif;
  font-weight: 900;
  font-size: clamp(48px, 8vw, 100px);
  line-height: 0.9;
  letter-spacing: -0.03em;
  margin-bottom: 48px;
}
.about-body {
  font-size: 17px; line-height: 1.85;
  color: var(--muted);
  margin-bottom: 32px;
}
.about-body strong { color: #fff; font-weight: 500; }
.about-stat-row {
  display: flex; gap: 48px;
  margin-top: 48px;
  padding-top: 40px;
  border-top: 1px solid var(--border);
}
.about-stat-num {
  font-family: 'Inter', sans-serif;
  font-weight: 900; font-size: 48px;
  line-height: 1;
  letter-spacing: -0.03em;
}
.about-stat-label {
  font-size: 11px; letter-spacing: 0.2em; text-transform: uppercase;
  color: var(--muted); margin-top: 8px;
}
.about-right {
  display: flex; align-items: center; justify-content: center;
}
.about-img-frame {
  width: 100%; max-width: 420px;
  aspect-ratio: 3/4;
  border: 1px solid var(--border);
  border-radius: 4px;
  background: var(--card);
  backdrop-filter: blur(10px);
  display: flex; flex-direction: column;
  align-items: center; justify-content: center;
  overflow: hidden;
  position: relative;
}
.about-img-placeholder {
  font-family: 'Inter', sans-serif;
  font-weight: 900;
  font-size: clamp(60px, 12vw, 120px);
  letter-spacing: -0.04em;
  color: rgba(255,255,255,0.08);
  line-height: 1;
}
.about-img-label {
  position: absolute; bottom: 24px; left: 24px;
  font-size: 10px; letter-spacing: 0.3em; text-transform: uppercase; color: var(--muted);
}
.about-img-corner {
  position: absolute; top: 16px; right: 16px;
  width: 32px; height: 32px;
  border-top: 1px solid rgba(255,255,255,0.2);
  border-right: 1px solid rgba(255,255,255,0.2);
}
.about-img-corner-bl {
  position: absolute; bottom: 16px; left: 16px;
  width: 32px; height: 32px;
  border-bottom: 1px solid rgba(255,255,255,0.2);
  border-left: 1px solid rgba(255,255,255,0.2);
}

/* ── SKILLS ── */
#skills { padding: 140px 48px; }
.skills-header {
  display: flex; justify-content: space-between; align-items: flex-end;
  margin-bottom: 80px;
}
.skills-title {
  font-family: 'Inter', sans-serif;
  font-weight: 900;
  font-size: clamp(40px, 7vw, 90px);
  line-height: 0.9;
  letter-spacing: -0.03em;
}
.skills-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 2px;
}
.skill-col {
  background: var(--card);
  border: 1px solid var(--border);
  padding: 40px;
  transition: background 0.4s;
}
.skill-col:hover { background: rgba(255,255,255,0.07); }
.skill-col-label {
  font-size: 10px; letter-spacing: 0.35em; text-transform: uppercase;
  color: var(--muted); margin-bottom: 32px;
  padding-bottom: 20px;
  border-bottom: 1px solid var(--border);
}
.skill-list { list-style: none; }
.skill-item {
  padding: 12px 0;
  font-size: 15px; font-weight: 300;
  color: rgba(255,255,255,0.8);
  border-bottom: 1px solid rgba(255,255,255,0.04);
  display: flex; align-items: center; gap: 12px;
  transition: color 0.3s, transform 0.3s;
}
.skill-col:hover .skill-item { color: #fff; }
.skill-item:hover { transform: translateX(6px); }
.skill-item::before {
  content: ''; width: 4px; height: 4px;
  border-radius: 50%; background: rgba(255,255,255,0.3);
  flex-shrink: 0;
}

/* ── PROJECTS ── */
#projects { padding: 140px 48px; }
.projects-header {
  display: grid; grid-template-columns: 1fr auto;
  align-items: flex-end;
  margin-bottom: 80px;
}
.projects-title {
  font-family: 'Inter', sans-serif;
  font-weight: 900;
  font-size: clamp(40px, 7vw, 90px);
  line-height: 0.9; letter-spacing: -0.03em;
}
.projects-count {
  font-family: 'Inter', sans-serif;
  font-weight: 900; font-size: 120px;
  line-height: 0.8; letter-spacing: -0.06em;
  color: rgba(255,255,255,0.06);
}
.projects-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 2px;
}
.project-card {
  background: var(--card);
  border: 1px solid var(--border);
  overflow: hidden;
  position: relative;
  cursor: none;
  transition: background 0.4s;
  text-decoration: none;
  display: block;
}
.project-card:hover { background: rgba(255,255,255,0.07); }
.project-preview {
  width: 100%; height: 220px;
  background: var(--bg2);
  position: relative; overflow: hidden;
  border-bottom: 1px solid var(--border);
}
.project-iframe-wrap {
  width: 200%; height: 200%;
  position: absolute;
  top: 0; left: 0;
  transform: scale(0.5);
  transform-origin: top left;
  pointer-events: none;
}
.project-iframe-wrap iframe {
  width: 100%; height: 100%;
  border: none;
}
.project-overlay {
  position: absolute; inset: 0;
  background: linear-gradient(to bottom, transparent 40%, rgba(0,0,0,0.85));
  display: flex; align-items: flex-end;
  padding: 20px;
  opacity: 0;
  transition: opacity 0.4s;
}
.project-card:hover .project-overlay { opacity: 1; }
.project-arrow {
  font-size: 11px; letter-spacing: 0.2em; text-transform: uppercase;
  color: #fff;
}
.project-body { padding: 32px; }
.project-num {
  font-size: 10px; letter-spacing: 0.3em; text-transform: uppercase;
  color: var(--muted); margin-bottom: 16px;
}
.project-name {
  font-family: 'Inter', sans-serif;
  font-weight: 700;
  font-size: 22px; letter-spacing: -0.02em;
  margin-bottom: 12px;
}
.project-desc {
  font-size: 14px; line-height: 1.7;
  color: var(--muted);
}
.project-link-row {
  display: flex; align-items: center; justify-content: space-between;
  margin-top: 24px; padding-top: 20px;
  border-top: 1px solid var(--border);
}
.project-visit {
  font-size: 11px; letter-spacing: 0.2em; text-transform: uppercase;
  color: var(--muted);
  display: flex; align-items: center; gap: 8px;
  transition: color 0.3s;
}
.project-card:hover .project-visit { color: #fff; }
.project-visit-arrow { font-size: 14px; transition: transform 0.3s; }
.project-card:hover .project-visit-arrow { transform: translate(4px,-4px); }

/* ── JOURNEY ── */
#journey { padding: 140px 48px; }
.journey-inner {
  display: grid; grid-template-columns: 1fr 1fr;
  gap: 120px;
  align-items: start;
}
.journey-left { }
.journey-title {
  font-family: 'Inter', sans-serif;
  font-weight: 900;
  font-size: clamp(40px, 7vw, 90px);
  line-height: 0.9; letter-spacing: -0.03em;
  margin-bottom: 48px;
}
.journey-intro {
  font-size: 16px; line-height: 1.8; color: var(--muted);
}
.journey-right { }
.timeline { position: relative; }
.timeline::before {
  content: '';
  position: absolute; left: 0; top: 0; bottom: 0;
  width: 1px; background: var(--border);
}
.timeline-item {
  padding: 0 0 56px 40px;
  position: relative;
}
.timeline-item::before {
  content: '';
  position: absolute; left: -4px; top: 6px;
  width: 9px; height: 9px;
  border-radius: 50%;
  background: #000;
  border: 1px solid rgba(255,255,255,0.4);
  transition: background 0.3s, border-color 0.3s;
}
.timeline-item:hover::before {
  background: #fff;
}
.timeline-year {
  font-size: 10px; letter-spacing: 0.35em; text-transform: uppercase;
  color: var(--muted); margin-bottom: 20px;
}
.timeline-events { list-style: none; }
.timeline-event {
  font-size: 15px; font-weight: 300;
  color: rgba(255,255,255,0.75);
  padding: 8px 0;
  border-bottom: 1px solid rgba(255,255,255,0.04);
  display: flex; align-items: center; gap: 12px;
}
.timeline-event::before {
  content: '→'; color: rgba(255,255,255,0.2);
  font-size: 12px; flex-shrink: 0;
}

/* ── PLANS ── */
#plans { padding: 140px 48px; }
.plans-header { margin-bottom: 80px; }
.plans-title {
  font-family: 'Inter', sans-serif;
  font-weight: 900;
  font-size: clamp(40px, 7vw, 90px);
  line-height: 0.9; letter-spacing: -0.03em;
}
.plans-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 2px;
}
.plan-card {
  background: var(--card);
  border: 1px solid var(--border);
  padding: 56px 48px;
  transition: background 0.4s;
  position: relative; overflow: hidden;
}
.plan-card::before {
  content: '';
  position: absolute;
  top: -100%; left: -100%;
  width: 300%; height: 300%;
  background: radial-gradient(circle, rgba(255,255,255,0.04) 0%, transparent 60%);
  opacity: 0; transition: opacity 0.5s;
  pointer-events: none;
}
.plan-card:hover::before { opacity: 1; }
.plan-card:hover { background: rgba(255,255,255,0.06); }
.plan-tag {
  font-size: 10px; letter-spacing: 0.35em; text-transform: uppercase;
  color: var(--muted); margin-bottom: 40px;
  display: flex; align-items: center; gap: 16px;
}
.plan-tag::before {
  content: ''; width: 24px; height: 1px; background: rgba(255,255,255,0.3);
}
.plan-card-title {
  font-family: 'Inter', sans-serif;
  font-weight: 700;
  font-size: 32px; letter-spacing: -0.02em;
  margin-bottom: 36px;
}
.plan-list { list-style: none; }
.plan-item {
  padding: 14px 0;
  font-size: 15px; font-weight: 300;
  color: rgba(255,255,255,0.75);
  border-bottom: 1px solid rgba(255,255,255,0.05);
  display: flex; gap: 16px; align-items: flex-start;
}
.plan-item-marker {
  color: var(--muted); font-size: 11px; margin-top: 3px;
  flex-shrink: 0;
}

/* ── PHILOSOPHY ── */
#philosophy {
  padding: 160px 48px;
  border-top: 1px solid var(--border);
  border-bottom: 1px solid var(--border);
}
.philosophy-label {
  font-size: 10px; letter-spacing: 0.4em; text-transform: uppercase;
  color: var(--muted); margin-bottom: 80px;
  display: flex; align-items: center; gap: 20px;
}
.philosophy-label::before {
  content: ''; width: 32px; height: 1px; background: rgba(255,255,255,0.3);
}
.philosophy-items {
  display: flex; flex-direction: column;
  gap: 0;
}
.philosophy-item {
  padding: 40px 0;
  border-bottom: 1px solid var(--border);
  display: flex; align-items: baseline;
  gap: 48px;
  transition: background 0.3s;
  cursor: default;
}
.philosophy-item:last-child { border-bottom: none; }
.philosophy-item-num {
  font-size: 11px; color: var(--muted); letter-spacing: 0.15em;
  width: 32px; flex-shrink: 0;
}
.philosophy-item-text {
  font-family: 'Inter', sans-serif;
  font-weight: 700;
  font-size: clamp(28px, 5vw, 64px);
  line-height: 1; letter-spacing: -0.03em;
  transition: color 0.3s;
}
.philosophy-item:hover .philosophy-item-text { color: rgba(255,255,255,0.6); }

/* ── QUOTE ── */
#quote {
  padding: 120px 48px;
  text-align: center;
  background: var(--bg2);
  overflow: hidden;
}
.quote-big {
  font-family: 'Inter', sans-serif;
  font-weight: 900;
  font-size: clamp(60px, 13vw, 180px);
  line-height: 0.88;
  letter-spacing: -0.04em;
  display: block;
  margin-bottom: 8px;
}
.quote-sub {
  font-family: 'Playfair Display', serif;
  font-style: italic;
  font-size: clamp(18px, 3vw, 36px);
  color: var(--muted);
  margin-top: 40px;
  letter-spacing: 0.02em;
}

/* ── CONTACT ── */
#contact { padding: 160px 48px; }
.contact-top {
  margin-bottom: 80px;
}
.contact-title {
  font-family: 'Inter', sans-serif;
  font-weight: 900;
  font-size: clamp(36px, 7vw, 90px);
  line-height: 0.9; letter-spacing: -0.03em;
  margin-bottom: 24px;
}
.contact-desc {
  font-size: 16px; color: var(--muted); line-height: 1.7;
  max-width: 400px;
}
.contact-cards {
  display: grid; grid-template-columns: repeat(3, 1fr);
  gap: 2px;
}
.contact-card {
  background: var(--card);
  border: 1px solid var(--border);
  padding: 48px 40px;
  text-decoration: none;
  color: #fff;
  transition: background 0.4s;
  position: relative; overflow: hidden;
  cursor: none;
}
.contact-card:hover { background: rgba(255,255,255,0.07); }
.contact-card-icon {
  font-size: 28px; margin-bottom: 24px;
  display: block;
  transition: transform 0.3s;
}
.contact-card:hover .contact-card-icon { transform: scale(1.1); }
.contact-card-label {
  font-size: 10px; letter-spacing: 0.3em; text-transform: uppercase;
  color: var(--muted); margin-bottom: 12px;
}
.contact-card-value {
  font-size: 18px; font-weight: 500;
}
.contact-card-arrow {
  position: absolute; bottom: 24px; right: 24px;
  font-size: 18px;
  color: var(--muted);
  transition: transform 0.3s, color 0.3s;
}
.contact-card:hover .contact-card-arrow { transform: translate(4px,-4px); color: #fff; }

/* ── FOOTER ── */
footer {
  padding: 64px 48px;
  border-top: 1px solid var(--border);
  display: flex; justify-content: space-between; align-items: flex-end;
  flex-wrap: wrap; gap: 32px;
}
.footer-left {}
.footer-brand {
  font-family: 'Inter', sans-serif;
  font-weight: 900; font-size: 28px;
  letter-spacing: 0.1em;
  margin-bottom: 8px;
}
.footer-name {
  font-size: 13px; color: var(--muted);
  letter-spacing: 0.1em;
}
.footer-desc {
  font-size: 12px; color: rgba(255,255,255,0.35);
  margin-top: 8px; max-width: 320px; line-height: 1.7;
}
.footer-right {
  text-align: right;
}
.footer-copy {
  font-size: 11px; color: var(--muted); letter-spacing: 0.15em;
}
.footer-copy-sub {
  font-size: 11px; color: rgba(255,255,255,0.25);
  margin-top: 4px;
}

/* ── REVEAL ── */
.reveal {
  opacity: 0; transform: translateY(40px);
  transition: opacity 0.9s cubic-bezier(0.16,1,0.3,1), transform 0.9s cubic-bezier(0.16,1,0.3,1);
}
.reveal.visible { opacity: 1; transform: none; }
.reveal-delay-1 { transition-delay: 0.1s; }
.reveal-delay-2 { transition-delay: 0.2s; }
.reveal-delay-3 { transition-delay: 0.3s; }
.reveal-delay-4 { transition-delay: 0.4s; }

/* ── RESPONSIVE ── */
@media (max-width: 1024px) {
  .skills-grid { grid-template-columns: repeat(2, 1fr); }
  .about-img-frame { max-width: 320px; }
}
@media (max-width: 900px) {
  nav { padding: 18px 24px; }
  .nav-links { display: none; }
  .nav-hamburger { display: flex; }
  #hero, #about, #skills, #projects, #journey,
  #plans, #philosophy, #quote, #contact { padding-left: 24px; padding-right: 24px; }
  #about { grid-template-columns: 1fr; gap: 48px; }
  .about-right { order: -1; }
  .about-img-frame { max-width: 100%; aspect-ratio: 4/3; }
  .projects-grid { grid-template-columns: 1fr; }
  .plans-grid { grid-template-columns: 1fr; }
  .journey-inner { grid-template-columns: 1fr; gap: 60px; }
  .contact-cards { grid-template-columns: 1fr; }
  .skills-grid { grid-template-columns: 1fr 1fr; }
  .about-stat-row { gap: 32px; }
  footer { flex-direction: column; align-items: flex-start; }
  .footer-right { text-align: left; }
  .projects-header { grid-template-columns: 1fr; }
  .projects-count { font-size: 80px; }
  .hero-roles { flex-direction: column; gap: 16px; }
}
@media (max-width: 600px) {
  .skills-grid { grid-template-columns: 1fr; }
  .about-stat-row { flex-direction: column; gap: 24px; }
  .philosophy-item { flex-direction: column; gap: 8px; }
  .philosophy-item-num { display: none; }
}

/* Mobile nav open */
.nav-mobile-open .nav-links {
  display: flex; flex-direction: column;
  position: fixed; inset: 0; background: rgba(0,0,0,0.97);
  backdrop-filter: blur(20px);
  align-items: center; justify-content: center;
  gap: 32px; z-index: 200;
}
.nav-mobile-open .nav-links a { font-size: 16px; }
</style>
</head>
<body>

<!-- LOADER -->
<div id="loader">
  <div id="loader-brand">NYTRIXX</div>
  <div id="loader-line"></div>
  <div id="loader-sub">Anubhav Singh — Portfolio</div>
</div>

<!-- CURSOR -->
<div id="cursor"></div>
<div id="cursor-ring"></div>

<!-- PROGRESS -->
<div id="progress"></div>

<!-- MOUSE GLOW -->
<div id="glow"></div>

<!-- PARTICLES -->
<canvas id="particles"></canvas>

<!-- NAVBAR -->
<nav id="navbar">
  <a href="#hero" class="nav-logo">NYTRIXX</a>
  <ul class="nav-links" id="navLinks">
    <li><a href="#hero">Home</a></li>
    <li><a href="#about">About</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#journey">Journey</a></li>
    <li><a href="#plans">Plans</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <div class="nav-hamburger" id="hamburger">
    <span></span><span></span><span></span>
  </div>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="hero-ghost-text hero-ghost-1">CREATE</div>
  <div class="hero-ghost-text hero-ghost-2">BUILD</div>
  <div class="hero-ghost-text hero-ghost-3">LEARN</div>

  <div class="hero-eyebrow">Web Developer &amp; Future Entrepreneur — India, 2026</div>
  <h1 class="hero-name">
    <span>ANUBHAV</span>
    <span>SINGH</span>
  </h1>
  <div class="hero-roles">
    <div class="hero-role">15-Year-Old Developer</div>
    <div class="hero-role">AI Website Builder</div>
    <div class="hero-role">Future Entrepreneur</div>
  </div>
  <p class="hero-desc">Building modern websites and exploring the future through creativity and technology.</p>
  <div class="hero-btns">
    <a href="#projects" class="btn btn-primary">View Projects</a>
    <a href="#about" class="btn btn-ghost">About Me</a>
    <a href="#contact" class="btn btn-ghost">Contact Me</a>
  </div>
  <div class="hero-scroll-hint">Scroll to explore</div>
</section>

<!-- ABOUT -->
<section id="about">
  <div class="about-left">
    <div class="section-label reveal">About</div>
    <h2 class="about-title reveal reveal-delay-1">WHO<br>I AM</h2>
    <p class="about-body reveal reveal-delay-2">
      I'm <strong>Anubhav Singh</strong>, a <strong>15-year-old developer</strong> passionate about creating modern websites and exploring the future of AI.
    </p>
    <p class="about-body reveal reveal-delay-2">
      I enjoy building clean interfaces, experimenting with new ideas and continuously improving myself through learning and creating.
    </p>
    <p class="about-body reveal reveal-delay-3">
      <strong>I believe consistency matters more than age.</strong>
    </p>
    <div class="about-stat-row reveal reveal-delay-4">
      <div>
        <div class="about-stat-num">57+</div>
        <div class="about-stat-label">Projects Built</div>
      </div>
      <div>
        <div class="about-stat-num">1+</div>
        <div class="about-stat-label">Year Learning</div>
      </div>
      <div>
        <div class="about-stat-num">∞</div>
        <div class="about-stat-label">Ideas Remaining</div>
      </div>
    </div>
  </div>
  <div class="about-right reveal">
    <div class="about-img-frame">
      <div class="about-img-placeholder">AS</div>
      <div class="about-img-corner"></div>
      <div class="about-img-corner-bl"></div>
      <div class="about-img-label">Anubhav Singh — NYTRIXX</div>
    </div>
  </div>
</section>

<!-- SKILLS -->
<section id="skills">
  <div class="skills-header">
    <div>
      <div class="section-label reveal">Capabilities</div>
      <h2 class="skills-title reveal reveal-delay-1">SKILLS &amp;<br>TOOLS</h2>
    </div>
  </div>
  <div class="skills-grid">
    <div class="skill-col reveal">
      <div class="skill-col-label">Frontend</div>
      <ul class="skill-list">
        <li class="skill-item">HTML</li>
        <li class="skill-item">CSS</li>
        <li class="skill-item">JavaScript</li>
        <li class="skill-item">Responsive Design</li>
        <li class="skill-item">Tailwind CSS</li>
      </ul>
    </div>
    <div class="skill-col reveal reveal-delay-1">
      <div class="skill-col-label">Design</div>
      <ul class="skill-list">
        <li class="skill-item">UI/UX</li>
        <li class="skill-item">Wireframing</li>
        <li class="skill-item">Modern Interfaces</li>
        <li class="skill-item">Minimal Design</li>
      </ul>
    </div>
    <div class="skill-col reveal reveal-delay-2">
      <div class="skill-col-label">AI Tools</div>
      <ul class="skill-list">
        <li class="skill-item">Claude</li>
      </ul>
    </div>
    <div class="skill-col reveal reveal-delay-3">
      <div class="skill-col-label">Tools</div>
      <ul class="skill-list">
        <li class="skill-item">VS Code</li>
        <li class="skill-item">Git</li>
        <li class="skill-item">GitHub</li>

      </ul>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <div class="projects-header">
    <div>
      <div class="section-label reveal">Work</div>
      <h2 class="projects-title reveal reveal-delay-1">SELECTED<br>PROJECTS</h2>
    </div>
    <div class="projects-count reveal">04</div>
  </div>
  <div class="projects-grid">

    <a href="https://singhvansh2462-byte.github.io/electric-shop-demo-/" target="_blank" rel="noopener" class="project-card reveal">
      <div class="project-preview">
        <div class="project-iframe-wrap">
          <iframe src="https://singhvansh2462-byte.github.io/electric-shop-demo-/" loading="lazy" title="Electric Shop Website" sandbox="allow-same-origin allow-scripts"></iframe>
        </div>
        <div class="project-overlay"><span class="project-arrow">↗ Visit Project</span></div>
      </div>
      <div class="project-body">
        <div class="project-num">Project 01</div>
        <div class="project-name">Electric Shop Website</div>
        <p class="project-desc">Modern business website with clean layouts and responsive design.</p>
        <div class="project-link-row">
          <span class="project-visit">Visit Live <span class="project-visit-arrow">↗</span></span>
        </div>
      </div>
    </a>

    <a href="https://singhvansh2462-byte.github.io/demo-saloon/" target="_blank" rel="noopener" class="project-card reveal reveal-delay-1">
      <div class="project-preview">
        <div class="project-iframe-wrap">
          <iframe src="https://singhvansh2462-byte.github.io/demo-saloon/" loading="lazy" title="Salon Website" sandbox="allow-same-origin allow-scripts"></iframe>
        </div>
        <div class="project-overlay"><span class="project-arrow">↗ Visit Project</span></div>
      </div>
      <div class="project-body">
        <div class="project-num">Project 02</div>
        <div class="project-name">Salon Website</div>
        <p class="project-desc">Luxury and modern salon website with premium layouts.</p>
        <div class="project-link-row">
          <span class="project-visit">Visit Live <span class="project-visit-arrow">↗</span></span>
        </div>
      </div>
    </a>

    <a href="https://singhvansh2462-byte.github.io/demo-webside-/" target="_blank" rel="noopener" class="project-card reveal reveal-delay-2">
      <div class="project-preview">
        <div class="project-iframe-wrap">
          <iframe src="https://singhvansh2462-byte.github.io/demo-webside-/" loading="lazy" title="Clothing Store Website" sandbox="allow-same-origin allow-scripts"></iframe>
        </div>
        <div class="project-overlay"><span class="project-arrow">↗ Visit Project</span></div>
      </div>
      <div class="project-body">
        <div class="project-num">Project 03</div>
        <div class="project-name">Clothing Store Website</div>
        <p class="project-desc">Minimal and elegant shopping website experience.</p>
        <div class="project-link-row">
          <span class="project-visit">Visit Live <span class="project-visit-arrow">↗</span></span>
        </div>
      </div>
    </a>

    <a href="https://singhvansh2462-byte.github.io/demo-bakery/" target="_blank" rel="noopener" class="project-card reveal reveal-delay-3">
      <div class="project-preview">
        <div class="project-iframe-wrap">
          <iframe src="https://singhvansh2462-byte.github.io/demo-bakery/" loading="lazy" title="Bakery Website" sandbox="allow-same-origin allow-scripts"></iframe>
        </div>
        <div class="project-overlay"><span class="project-arrow">↗ Visit Project</span></div>
      </div>
      <div class="project-body">
        <div class="project-num">Project 04</div>
        <div class="project-name">Bakery Website</div>
        <p class="project-desc">Modern bakery website with stylish layouts and clean design.</p>
        <div class="project-link-row">
          <span class="project-visit">Visit Live <span class="project-visit-arrow">↗</span></span>
        </div>
      </div>
    </a>

  </div>
</section>

<!-- JOURNEY -->
<section id="journey">
  <div class="journey-inner">
    <div class="journey-left">
      <div class="section-label reveal">Timeline</div>
      <h2 class="journey-title reveal reveal-delay-1">MY<br>JOURNEY</h2>
      <p class="journey-intro reveal reveal-delay-2">
        Every great story starts somewhere. Mine started with an idea, a laptop, and the desire to build something real.
      </p>
    </div>
    <div class="journey-right">
      <div class="timeline">
        <div class="timeline-item reveal">
          <div class="timeline-year">2025</div>
          <ul class="timeline-events">
            <li class="timeline-event">Started learning web development</li>
            <li class="timeline-event">Learned HTML, CSS and JavaScript</li>
            <li class="timeline-event">Built first projects</li>
          </ul>
        </div>
        <div class="timeline-item reveal reveal-delay-1">
          <div class="timeline-year">2026</div>
          <ul class="timeline-events">
            <li class="timeline-event">Created professional website demos</li>
            <li class="timeline-event">Started exploring AI tools</li>
            <li class="timeline-event">Focused on UI/UX design</li>
            <li class="timeline-event">Improved development skills</li>
          </ul>
        </div>
        <div class="timeline-item reveal reveal-delay-2">
          <div class="timeline-year">Future</div>
          <ul class="timeline-events">
            <li class="timeline-event">Build NYTRIXX into a digital brand</li>
            <li class="timeline-event">Work with people worldwide</li>
            <li class="timeline-event">Create products</li>
            <li class="timeline-event">Build meaningful experiences</li>
            <li class="timeline-event">Never stop learning</li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- PLANS -->
<section id="plans">
  <div class="plans-header">
    <div class="section-label reveal">Vision</div>
    <h2 class="plans-title reveal reveal-delay-1">PLANS &amp;<br>GOALS</h2>
  </div>
  <div class="plans-grid">
    <div class="plan-card reveal">
      <div class="plan-tag">Short Term</div>
      <div class="plan-card-title">Right Now</div>
      <ul class="plan-list">
        <li class="plan-item"><span class="plan-item-marker">01</span>Improve frontend skills</li>
        <li class="plan-item"><span class="plan-item-marker">02</span>Learn React</li>
        <li class="plan-item"><span class="plan-item-marker">03</span>Build better projects</li>
        <li class="plan-item"><span class="plan-item-marker">04</span>Work with clients</li>
      </ul>
    </div>
    <div class="plan-card reveal reveal-delay-1">
      <div class="plan-tag">Long Term</div>
      <div class="plan-card-title">The Vision</div>
      <ul class="plan-list">
        <li class="plan-item"><span class="plan-item-marker">01</span>Build NYTRIXX into a brand</li>
        <li class="plan-item"><span class="plan-item-marker">02</span>Launch a digital agency</li>
        <li class="plan-item"><span class="plan-item-marker">03</span>Create digital products</li>
        <li class="plan-item"><span class="plan-item-marker">04</span>Work globally</li>
        <li class="plan-item"><span class="plan-item-marker">05</span>Build impactful experiences</li>
      </ul>
    </div>
  </div>
</section>

<!-- PHILOSOPHY -->
<section id="philosophy">
  <div class="philosophy-label reveal">What I Believe</div>
  <div class="philosophy-items">
    <div class="philosophy-item reveal">
      <span class="philosophy-item-num">—</span>
      <span class="philosophy-item-text">Age doesn't define vision.</span>
    </div>
    <div class="philosophy-item reveal reveal-delay-1">
      <span class="philosophy-item-num">—</span>
      <span class="philosophy-item-text">Learning never stops.</span>
    </div>
    <div class="philosophy-item reveal reveal-delay-2">
      <span class="philosophy-item-num">—</span>
      <span class="philosophy-item-text">Consistency beats talent.</span>
    </div>
    <div class="philosophy-item reveal reveal-delay-3">
      <span class="philosophy-item-num">—</span>
      <span class="philosophy-item-text">Small steps become great journeys.</span>
    </div>
    <div class="philosophy-item reveal reveal-delay-4">
      <span class="philosophy-item-num">—</span>
      <span class="philosophy-item-text">Create something meaningful.</span>
    </div>
  </div>
</section>

<!-- QUOTE -->
<section id="quote">
  <div class="reveal">
    <span class="quote-big">LEARNING.</span>
    <span class="quote-big">BUILDING.</span>
    <span class="quote-big">GROWING.</span>
  </div>
  <div class="quote-sub reveal reveal-delay-2">Age doesn't define vision.</div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="contact-top">
    <div class="section-label reveal">Get In Touch</div>
    <h2 class="contact-title reveal reveal-delay-1">LET'S BUILD<br>SOMETHING<br>GREAT</h2>
    <p class="contact-desc reveal reveal-delay-2">Open to collaborations, creative projects and learning opportunities.</p>
  </div>
  <div class="contact-cards">
    <a href="https://www.instagram.com/nytrixxofficial/" target="_blank" rel="noopener" class="contact-card reveal">
      <span class="contact-card-icon">◈</span>
      <div class="contact-card-label">Instagram</div>
      <div class="contact-card-value">@nytrixx</div>
      <span class="contact-card-arrow">↗</span>
    </a>
    <a href="mailto:nytrixxofficial@gmail.com" class="contact-card reveal reveal-delay-1">
      <span class="contact-card-icon">✉</span>
      <div class="contact-card-label">Email</div>
      <div class="contact-card-value">nytrixxofficial@gmail.com</div>
      <span class="contact-card-arrow">↗</span>
    </a>
    <a href="mailto:nytrixxofficial@gmail.com" class="contact-card reveal reveal-delay-2">
      <span class="contact-card-icon">◎</span>
      <div class="contact-card-label">Let's Collaborate</div>
      <div class="contact-card-value">Start a Project</div>
      <span class="contact-card-arrow">↗</span>
    </a>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-left">
    <div class="footer-brand">NYTRIXX</div>
    <div class="footer-name">ANUBHAV SINGH — 15-Year-Old Web Developer</div>
    <div class="footer-desc">Building ideas, learning every day, and creating modern digital experiences.</div>
  </div>
  <div class="footer-right">
    <div class="footer-copy">© 2026 NYTRIXX</div>
    <div class="footer-copy-sub">Designed &amp; Built by Anubhav Singh</div>
  </div>
</footer>

<script>
// ── LOADER
const loader = document.getElementById('loader');
setTimeout(() => {
  loader.classList.add('out');
  setTimeout(() => loader.style.display = 'none', 700);
}, 2600);

// ── CURSOR
const cursor = document.getElementById('cursor');
const ring = document.getElementById('cursor-ring');
let mx = -100, my = -100, rx = -100, ry = -100;
document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; });
(function animCursor() {
  rx += (mx - rx) * 0.15;
  ry += (my - ry) * 0.15;
  cursor.style.left = mx + 'px';
  cursor.style.top = my + 'px';
  ring.style.left = rx + 'px';
  ring.style.top = ry + 'px';
  requestAnimationFrame(animCursor);
})();
document.querySelectorAll('a, button, .skill-item, .philosophy-item').forEach(el => {
  el.addEventListener('mouseenter', () => document.body.classList.add('hovering'));
  el.addEventListener('mouseleave', () => document.body.classList.remove('hovering'));
});

// ── GLOW
const glow = document.getElementById('glow');
document.addEventListener('mousemove', e => {
  glow.style.left = e.clientX + 'px';
  glow.style.top = e.clientY + 'px';
});

// ── PROGRESS
const bar = document.getElementById('progress');
document.addEventListener('scroll', () => {
  const pct = window.scrollY / (document.body.scrollHeight - window.innerHeight);
  bar.style.width = (pct * 100) + '%';
});

// ── PARTICLES
const canvas = document.getElementById('particles');
const ctx = canvas.getContext('2d');
let W, H, pts = [];
function resize() {
  W = canvas.width = window.innerWidth;
  H = canvas.height = window.innerHeight;
}
resize();
window.addEventListener('resize', resize);
for (let i = 0; i < 80; i++) {
  pts.push({
    x: Math.random() * W, y: Math.random() * H,
    vx: (Math.random() - 0.5) * 0.3,
    vy: (Math.random() - 0.5) * 0.3,
    r: Math.random() * 1.2 + 0.3,
    a: Math.random() * 0.5 + 0.1
  });
}
(function animParts() {
  ctx.clearRect(0, 0, W, H);
  pts.forEach(p => {
    p.x += p.vx; p.y += p.vy;
    if (p.x < 0) p.x = W;
    if (p.x > W) p.x = 0;
    if (p.y < 0) p.y = H;
    if (p.y > H) p.y = 0;
    ctx.beginPath();
    ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2);
    ctx.fillStyle = `rgba(255,255,255,${p.a})`;
    ctx.fill();
  });
  requestAnimationFrame(animParts);
})();

// ── REVEAL ON SCROLL
const revealEls = document.querySelectorAll('.reveal');
const io = new IntersectionObserver((entries) => {
  entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('visible'); io.unobserve(e.target); } });
}, { threshold: 0.12 });
revealEls.forEach(el => io.observe(el));

// ── HAMBURGER
const hamburger = document.getElementById('hamburger');
const navLinks = document.getElementById('navLinks');
hamburger.addEventListener('click', () => {
  document.body.classList.toggle('nav-mobile-open');
});
navLinks.querySelectorAll('a').forEach(a => {
  a.addEventListener('click', () => document.body.classList.remove('nav-mobile-open'));
});

// ── NAVBAR SCROLL EFFECT
const navbar = document.getElementById('navbar');
window.addEventListener('scroll', () => {
  if (window.scrollY > 60) {
    navbar.style.padding = '14px 48px';
  } else {
    navbar.style.padding = '20px 48px';
  }
});

// ── PARALLAX HERO GHOST TEXT
document.addEventListener('scroll', () => {
  const y = window.scrollY;
  const g1 = document.querySelector('.hero-ghost-1');
  const g2 = document.querySelector('.hero-ghost-2');
  const g3 = document.querySelector('.hero-ghost-3');
  if (g1) g1.style.transform = `translateY(${y * 0.15}px)`;
  if (g2) g2.style.transform = `translateY(${-y * 0.1}px)`;
  if (g3) g3.style.transform = `translateY(calc(-50% + ${y * 0.08}px))`;
});
</script>
</body>
</html>
