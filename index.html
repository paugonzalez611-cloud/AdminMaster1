<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>AdminMaster — Comunicaciones Integradas de Mercadeo</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">

<style>
:root {
  --cream: #F9F6F0;
  --cream-dark: #EDE8DF;
  --white: #FDFCFA;
  --gold: #B8963E;
  --gold-light: #D4AF5A;
  --gold-pale: #F0E6C8;
  --ink: #1A1714;
  --ink-soft: #3D3830;
  --gray: #8A8480;
  --gray-light: #C8C4BC;
  --gray-line: #E2DDD6;
  --shadow: rgba(26, 23, 20, 0.08);
  --shadow-md: rgba(26, 23, 20, 0.14);
}

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

html { scroll-behavior: smooth; }

body {
  font-family: 'DM Sans', sans-serif;
  background: var(--cream);
  color: var(--ink);
  overflow-x: hidden;
  line-height: 1.6;
}

/* ─── CURSOR ─── */
body { cursor: none; }
.cursor {
  position: fixed; top: 0; left: 0; pointer-events: none; z-index: 9999;
  mix-blend-mode: multiply;
}
.cursor-dot {
  width: 8px; height: 8px; background: var(--gold);
  border-radius: 50%;
  transform: translate(-50%, -50%);
  transition: transform 0.1s;
}
.cursor-ring {
  width: 32px; height: 32px;
  border: 1px solid var(--gold);
  border-radius: 50%;
  transform: translate(-50%, -50%);
  transition: transform 0.18s ease, width 0.2s, height 0.2s, opacity 0.2s;
  opacity: 0.6;
}
body:has(a:hover, button:hover, .module-card:hover) .cursor-ring {
  width: 48px; height: 48px; opacity: 0.9;
}

/* ─── SCROLL REVEAL ─── */
.reveal {
  opacity: 0;
  transform: translateY(28px);
  transition: opacity 0.7s ease, transform 0.7s ease;
}
.reveal.visible { opacity: 1; transform: none; }
.reveal-delay-1 { transition-delay: 0.1s; }
.reveal-delay-2 { transition-delay: 0.2s; }
.reveal-delay-3 { transition-delay: 0.3s; }
.reveal-delay-4 { transition-delay: 0.4s; }

/* ─── NAV ─── */
nav {
  position: fixed; top: 0; left: 0; right: 0; z-index: 100;
  display: flex; align-items: center; justify-content: space-between;
  padding: 0 48px;
  height: 72px;
  background: rgba(249, 246, 240, 0.88);
  backdrop-filter: blur(16px);
  border-bottom: 1px solid var(--gray-line);
  transition: box-shadow 0.3s;
}
nav.scrolled { box-shadow: 0 4px 24px var(--shadow); }

.nav-logo {
  font-family: 'Cormorant Garamond', serif;
  font-size: 1.5rem; font-weight: 600; letter-spacing: 0.04em;
  color: var(--ink); text-decoration: none;
}
.nav-logo span { color: var(--gold); }

.nav-links {
  display: flex; gap: 40px; list-style: none;
}
.nav-links a {
  font-size: 0.82rem; font-weight: 500; letter-spacing: 0.08em;
  text-transform: uppercase; color: var(--ink-soft); text-decoration: none;
  position: relative; padding-bottom: 3px;
  transition: color 0.2s;
}
.nav-links a::after {
  content: ''; position: absolute; bottom: 0; left: 0;
  width: 0; height: 1px; background: var(--gold);
  transition: width 0.3s ease;
}
.nav-links a:hover { color: var(--gold); }
.nav-links a:hover::after { width: 100%; }

.nav-cta {
  background: var(--ink); color: var(--cream) !important;
  padding: 9px 24px; border-radius: 2px;
  font-size: 0.78rem !important; letter-spacing: 0.1em !important;
  transition: background 0.2s !important;
}
.nav-cta:hover { background: var(--gold) !important; color: var(--white) !important; }
.nav-cta::after { display: none !important; }

/* ─── HERO ─── */
.hero {
  min-height: 100vh;
  display: flex; align-items: center;
  padding: 120px 48px 80px;
  position: relative;
  overflow: hidden;
}

.hero-bg {
  position: absolute; inset: 0;
  background: radial-gradient(ellipse 80% 60% at 70% 40%, var(--gold-pale) 0%, transparent 65%),
              radial-gradient(ellipse 50% 50% at 10% 80%, var(--cream-dark) 0%, transparent 60%);
}

.hero-grid-lines {
  position: absolute; inset: 0; opacity: 0.15;
  background-image:
    linear-gradient(var(--gray-line) 1px, transparent 1px),
    linear-gradient(90deg, var(--gray-line) 1px, transparent 1px);
  background-size: 80px 80px;
}

.hero-content {
  position: relative; z-index: 2;
  max-width: 760px;
}

.hero-eyebrow {
  display: inline-flex; align-items: center; gap: 12px;
  font-size: 0.72rem; font-weight: 500; letter-spacing: 0.18em;
  text-transform: uppercase; color: var(--gold);
  margin-bottom: 28px;
  opacity: 0;
  animation: fadeUp 0.8s 0.2s ease forwards;
}
.hero-eyebrow::before {
  content: ''; width: 32px; height: 1px; background: var(--gold);
}

.hero-title {
  font-family: 'Cormorant Garamond', serif;
  font-size: clamp(3.2rem, 7vw, 6rem);
  font-weight: 300; line-height: 1.05;
  color: var(--ink); letter-spacing: -0.01em;
  margin-bottom: 28px;
  opacity: 0;
  animation: fadeUp 0.9s 0.35s ease forwards;
}
.hero-title em { font-style: italic; color: var(--gold); }
.hero-title strong { font-weight: 600; }

.hero-desc {
  font-size: 1.05rem; font-weight: 300; line-height: 1.75;
  color: var(--ink-soft); max-width: 520px; margin-bottom: 48px;
  opacity: 0;
  animation: fadeUp 0.9s 0.5s ease forwards;
}

.hero-actions {
  display: flex; gap: 16px; align-items: center;
  opacity: 0;
  animation: fadeUp 0.9s 0.65s ease forwards;
}

.btn-primary {
  background: var(--ink); color: var(--cream);
  padding: 14px 36px; border: none; border-radius: 2px;
  font-family: 'DM Sans', sans-serif;
  font-size: 0.82rem; font-weight: 500; letter-spacing: 0.1em;
  text-transform: uppercase; cursor: none;
  text-decoration: none; display: inline-block;
  transition: background 0.25s, transform 0.2s;
}
.btn-primary:hover { background: var(--gold); transform: translateY(-1px); }

.btn-ghost {
  color: var(--ink-soft); background: transparent;
  border: 1px solid var(--gray-line);
  padding: 14px 32px; border-radius: 2px;
  font-size: 0.82rem; font-weight: 400; letter-spacing: 0.06em;
  cursor: none; text-decoration: none; display: inline-block;
  transition: border-color 0.25s, color 0.25s;
}
.btn-ghost:hover { border-color: var(--gold); color: var(--gold); }

.hero-stats {
  position: absolute; right: 80px; bottom: 80px;
  display: flex; gap: 48px; z-index: 2;
  opacity: 0;
  animation: fadeUp 1s 0.8s ease forwards;
}
.stat { text-align: center; }
.stat-num {
  font-family: 'Cormorant Garamond', serif;
  font-size: 2.4rem; font-weight: 300; color: var(--ink);
  line-height: 1;
}
.stat-num span { color: var(--gold); }
.stat-label {
  font-size: 0.7rem; letter-spacing: 0.12em;
  text-transform: uppercase; color: var(--gray); margin-top: 6px;
}

/* ─── SECTION COMMON ─── */
section { padding: 100px 48px; }

.section-label {
  font-size: 0.7rem; font-weight: 500; letter-spacing: 0.2em;
  text-transform: uppercase; color: var(--gold);
  display: flex; align-items: center; gap: 12px;
  margin-bottom: 20px;
}
.section-label::before { content: ''; width: 24px; height: 1px; background: var(--gold); }

.section-title {
  font-family: 'Cormorant Garamond', serif;
  font-size: clamp(2rem, 4vw, 3.2rem);
  font-weight: 300; line-height: 1.15;
  margin-bottom: 16px;
}
.section-title em { font-style: italic; color: var(--gold); }

.section-desc {
  font-size: 0.95rem; font-weight: 300;
  color: var(--ink-soft); max-width: 560px; line-height: 1.8;
  margin-bottom: 64px;
}

/* ─── MODULES / CIM GRID ─── */
#modulos { background: var(--white); }

.modules-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(340px, 1fr));
  gap: 1px;
  background: var(--gray-line);
  border: 1px solid var(--gray-line);
  border-radius: 4px;
  overflow: hidden;
}

.module-card {
  background: var(--white);
  padding: 40px;
  position: relative;
  transition: background 0.3s;
  cursor: none;
  overflow: hidden;
}
.module-card::before {
  content: ''; position: absolute; top: 0; left: 0;
  width: 3px; height: 0;
  background: var(--gold);
  transition: height 0.4s ease;
}
.module-card:hover { background: var(--cream); }
.module-card:hover::before { height: 100%; }

.module-icon {
  width: 48px; height: 48px;
  display: flex; align-items: center; justify-content: center;
  margin-bottom: 24px;
  position: relative;
}
.module-icon svg { width: 28px; height: 28px; stroke: var(--gold); fill: none; stroke-width: 1.5; }

.module-number {
  position: absolute; top: 40px; right: 40px;
  font-family: 'Cormorant Garamond', serif;
  font-size: 3.5rem; font-weight: 300;
  color: var(--gold-pale); line-height: 1;
  transition: color 0.3s;
}
.module-card:hover .module-number { color: var(--gold-pale); opacity: 0.7; }

.module-tag {
  font-size: 0.65rem; letter-spacing: 0.2em; text-transform: uppercase;
  color: var(--gold); font-weight: 500; margin-bottom: 10px;
}

.module-name {
  font-family: 'Cormorant Garamond', serif;
  font-size: 1.7rem; font-weight: 400; line-height: 1.2;
  margin-bottom: 12px; color: var(--ink);
}

.module-desc {
  font-size: 0.87rem; font-weight: 300; color: var(--gray);
  line-height: 1.7; margin-bottom: 28px;
}

.module-btn {
  display: inline-flex; align-items: center; gap: 8px;
  font-size: 0.75rem; font-weight: 500;
  letter-spacing: 0.1em; text-transform: uppercase;
  color: var(--ink); text-decoration: none;
  border-bottom: 1px solid var(--gray-line);
  padding-bottom: 4px;
  transition: color 0.2s, border-color 0.2s;
  cursor: none;
  background: none; border-top: none; border-left: none; border-right: none;
}
.module-btn:hover { color: var(--gold); border-color: var(--gold); }
.module-btn svg { width: 14px; height: 14px; transition: transform 0.2s; }
.module-btn:hover svg { transform: translateX(3px); }

/* ─── AGENT MODAL ─── */
.modal-overlay {
  position: fixed; inset: 0; z-index: 200;
  background: rgba(26, 23, 20, 0.6);
  backdrop-filter: blur(8px);
  display: flex; align-items: center; justify-content: center;
  opacity: 0; pointer-events: none;
  transition: opacity 0.3s;
  padding: 20px;
}
.modal-overlay.open { opacity: 1; pointer-events: all; }

.modal {
  background: var(--white);
  border-radius: 4px;
  width: 100%; max-width: 640px;
  max-height: 88vh;
  display: flex; flex-direction: column;
  box-shadow: 0 32px 80px rgba(26,23,20,0.22);
  transform: translateY(20px) scale(0.97);
  transition: transform 0.3s ease;
  overflow: hidden;
}
.modal-overlay.open .modal {
  transform: none;
}

.modal-header {
  padding: 24px 28px 20px;
  border-bottom: 1px solid var(--gray-line);
  display: flex; align-items: flex-start; justify-content: space-between;
  flex-shrink: 0;
}
.modal-agent-info { display: flex; align-items: center; gap: 14px; }
.modal-agent-avatar {
  width: 44px; height: 44px; border-radius: 50%;
  background: var(--gold-pale);
  display: flex; align-items: center; justify-content: center;
}
.modal-agent-avatar svg { width: 20px; height: 20px; stroke: var(--gold); fill: none; stroke-width: 1.5; }
.modal-agent-name {
  font-family: 'Cormorant Garamond', serif;
  font-size: 1.25rem; font-weight: 400; color: var(--ink);
}
.modal-agent-status {
  font-size: 0.72rem; color: #4CAF7A; letter-spacing: 0.04em;
  display: flex; align-items: center; gap: 5px;
}
.modal-agent-status::before {
  content: ''; width: 6px; height: 6px;
  background: #4CAF7A; border-radius: 50%;
  animation: pulse-dot 2s infinite;
}
.modal-close {
  background: none; border: none; cursor: none;
  width: 32px; height: 32px;
  display: flex; align-items: center; justify-content: center;
  border-radius: 50%;
  color: var(--gray);
  font-size: 1.4rem; line-height: 1;
  transition: background 0.2s, color 0.2s;
}
.modal-close:hover { background: var(--cream); color: var(--ink); }

.modal-context {
  padding: 10px 28px;
  background: var(--cream);
  border-bottom: 1px solid var(--gray-line);
  font-size: 0.75rem; color: var(--gray);
  flex-shrink: 0;
}
.modal-context strong { color: var(--gold); }

.chat-window {
  flex: 1; overflow-y: auto;
  padding: 20px 28px;
  display: flex; flex-direction: column; gap: 14px;
  min-height: 260px;
}
.chat-window::-webkit-scrollbar { width: 4px; }
.chat-window::-webkit-scrollbar-track { background: transparent; }
.chat-window::-webkit-scrollbar-thumb { background: var(--gray-line); border-radius: 2px; }

.chat-msg {
  max-width: 85%;
  animation: fadeMsg 0.3s ease;
}
@keyframes fadeMsg { from { opacity: 0; transform: translateY(6px); } to { opacity: 1; transform: none; } }

.chat-msg.user { align-self: flex-end; }
.chat-msg.agent { align-self: flex-start; }

.chat-bubble {
  padding: 12px 16px;
  border-radius: 3px;
  font-size: 0.875rem; line-height: 1.65;
}
.chat-msg.user .chat-bubble {
  background: var(--ink); color: var(--cream);
  border-bottom-right-radius: 0;
}
.chat-msg.agent .chat-bubble {
  background: var(--cream); color: var(--ink-soft);
  border-bottom-left-radius: 0;
  border: 1px solid var(--gray-line);
}
.chat-time {
  font-size: 0.65rem; color: var(--gray-light);
  margin-top: 4px;
  text-align: right;
}
.chat-msg.agent .chat-time { text-align: left; }

.typing-indicator {
  display: flex; gap: 4px; align-items: center;
  padding: 12px 16px;
  background: var(--cream); border: 1px solid var(--gray-line);
  border-radius: 3px; border-bottom-left-radius: 0;
  align-self: flex-start; width: fit-content;
}
.typing-dot {
  width: 7px; height: 7px; background: var(--gray-light);
  border-radius: 50%;
  animation: typingBounce 1.2s infinite;
}
.typing-dot:nth-child(2) { animation-delay: 0.2s; }
.typing-dot:nth-child(3) { animation-delay: 0.4s; }

.chat-suggestions {
  padding: 8px 28px 0;
  display: flex; gap: 8px; flex-wrap: wrap;
  flex-shrink: 0;
}
.chat-suggestion {
  background: none; border: 1px solid var(--gray-line);
  border-radius: 20px;
  padding: 5px 14px;
  font-size: 0.75rem; color: var(--gray); cursor: none;
  font-family: 'DM Sans', sans-serif;
  transition: border-color 0.2s, color 0.2s;
}
.chat-suggestion:hover { border-color: var(--gold); color: var(--gold-light); }

.chat-input-area {
  padding: 16px 28px 20px;
  border-top: 1px solid var(--gray-line);
  display: flex; gap: 10px; align-items: flex-end;
  flex-shrink: 0;
}
.chat-input {
  flex: 1;
  background: var(--cream); border: 1px solid var(--gray-line);
  border-radius: 3px;
  padding: 10px 14px;
  font-family: 'DM Sans', sans-serif;
  font-size: 0.875rem; color: var(--ink);
  resize: none; height: 44px; max-height: 100px; overflow-y: hidden;
  outline: none;
  transition: border-color 0.2s;
}
.chat-input:focus { border-color: var(--gold); }
.chat-input::placeholder { color: var(--gray-light); }

.chat-send {
  width: 44px; height: 44px; flex-shrink: 0;
  background: var(--ink); border: none; border-radius: 3px;
  color: var(--cream); cursor: none;
  display: flex; align-items: center; justify-content: center;
  transition: background 0.2s, transform 0.15s;
}
.chat-send:hover { background: var(--gold); transform: scale(1.04); }
.chat-send svg { width: 16px; height: 16px; }

/* ─── BRAND MEMORY ─── */
#memoria { background: var(--cream); }

.memory-layout {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 64px;
  align-items: center;
}

.memory-visual {
  position: relative; height: 420px;
}
.memory-ring {
  position: absolute;
  border-radius: 50%;
  border: 1px solid var(--gold-pale);
  top: 50%; left: 50%;
  transform: translate(-50%, -50%);
}
.ring-1 { width: 300px; height: 300px; animation: rotateSlow 20s linear infinite; }
.ring-2 { width: 220px; height: 220px; animation: rotateSlow 15s linear infinite reverse; border-color: var(--gold-light); opacity: 0.5; }
.ring-3 { width: 140px; height: 140px; background: var(--gold-pale); border: none; opacity: 0.4; }

.memory-center {
  position: absolute;
  top: 50%; left: 50%;
  transform: translate(-50%, -50%);
  width: 80px; height: 80px;
  background: var(--gold);
  border-radius: 50%;
  display: flex; align-items: center; justify-content: center;
  z-index: 2;
}
.memory-center svg { width: 30px; height: 30px; stroke: white; fill: none; stroke-width: 1.5; }

.ring-dot {
  position: absolute;
  width: 10px; height: 10px;
  background: var(--white);
  border: 2px solid var(--gold);
  border-radius: 50%;
}
.ring-1 .ring-dot:nth-child(1) { top: -5px; left: 50%; margin-left: -5px; }
.ring-1 .ring-dot:nth-child(2) { bottom: -5px; left: 50%; margin-left: -5px; }
.ring-1 .ring-dot:nth-child(3) { left: -5px; top: 50%; margin-top: -5px; }
.ring-1 .ring-dot:nth-child(4) { right: -5px; top: 50%; margin-top: -5px; }

.memory-agents {
  display: flex; flex-direction: column; gap: 16px;
}

.memory-agent-item {
  display: flex; align-items: center; gap: 16px;
  padding: 16px 20px;
  background: var(--white);
  border: 1px solid var(--gray-line);
  border-radius: 3px;
  transition: border-color 0.2s, transform 0.2s;
}
.memory-agent-item:hover { border-color: var(--gold); transform: translateX(4px); }

.ma-icon {
  width: 36px; height: 36px;
  background: var(--cream);
  border-radius: 50%;
  display: flex; align-items: center; justify-content: center;
  flex-shrink: 0;
}
.ma-icon svg { width: 16px; height: 16px; stroke: var(--gold); fill: none; stroke-width: 1.5; }

.ma-info { flex: 1; }
.ma-name { font-size: 0.85rem; font-weight: 500; color: var(--ink); }
.ma-role { font-size: 0.72rem; color: var(--gray); }

.ma-sync {
  width: 8px; height: 8px;
  background: #4CAF7A; border-radius: 50%;
  animation: pulse-dot 2.5s infinite;
}

/* ─── CASOS DE ANÁLISIS ─── */
#casos { background: var(--ink); color: var(--cream); }
#casos .section-label { color: var(--gold-light); }
#casos .section-label::before { background: var(--gold-light); }
#casos .section-title { color: var(--cream); }
#casos .section-desc { color: var(--gray-light); }

.upload-zone {
  border: 1px dashed rgba(184, 150, 62, 0.4);
  border-radius: 4px;
  padding: 60px 40px;
  text-align: center;
  background: rgba(184, 150, 62, 0.04);
  transition: border-color 0.3s, background 0.3s;
  cursor: none;
  position: relative;
  overflow: hidden;
}
.upload-zone:hover {
  border-color: var(--gold);
  background: rgba(184, 150, 62, 0.08);
}
.upload-icon {
  width: 56px; height: 56px;
  background: rgba(184, 150, 62, 0.1);
  border-radius: 50%;
  display: flex; align-items: center; justify-content: center;
  margin: 0 auto 20px;
}
.upload-icon svg { width: 24px; height: 24px; stroke: var(--gold); fill: none; stroke-width: 1.5; }
.upload-title {
  font-family: 'Cormorant Garamond', serif;
  font-size: 1.5rem; font-weight: 300;
  color: var(--cream); margin-bottom: 8px;
}
.upload-desc { font-size: 0.85rem; color: rgba(200,196,188,0.7); line-height: 1.6; }
.upload-formats {
  display: flex; gap: 10px; justify-content: center; margin-top: 20px;
}
.format-tag {
  font-size: 0.68rem; letter-spacing: 0.12em; text-transform: uppercase;
  border: 1px solid rgba(184, 150, 62, 0.3);
  padding: 4px 12px; border-radius: 2px; color: var(--gold-light);
}

.casos-features {
  display: grid; grid-template-columns: repeat(3, 1fr);
  gap: 1px; background: rgba(255,255,255,0.05);
  border: 1px solid rgba(255,255,255,0.06);
  border-radius: 3px; margin-top: 48px; overflow: hidden;
}
.cf-item {
  padding: 32px 28px;
  background: rgba(26,23,20,0.5);
  transition: background 0.3s;
}
.cf-item:hover { background: rgba(184, 150, 62, 0.06); }
.cf-num {
  font-family: 'Cormorant Garamond', serif;
  font-size: 2.5rem; font-weight: 300;
  color: var(--gold); line-height: 1; margin-bottom: 12px;
}
.cf-title {
  font-size: 0.88rem; font-weight: 500;
  color: var(--cream); margin-bottom: 8px;
}
.cf-desc { font-size: 0.8rem; color: var(--gray); line-height: 1.6; }

/* ─── FOOTER ─── */
footer {
  background: var(--ink);
  color: var(--gray);
  padding: 60px 48px 40px;
  border-top: 1px solid rgba(255,255,255,0.06);
}
.footer-top {
  display: flex; justify-content: space-between; align-items: flex-start;
  margin-bottom: 48px;
}
.footer-brand {
  font-family: 'Cormorant Garamond', serif;
  font-size: 2rem; font-weight: 300; color: var(--cream);
}
.footer-brand span { color: var(--gold); }
.footer-tagline { font-size: 0.8rem; color: var(--gray); margin-top: 6px; }

.footer-cols { display: flex; gap: 60px; }
.footer-col h4 {
  font-size: 0.7rem; letter-spacing: 0.18em;
  text-transform: uppercase; color: var(--gold);
  margin-bottom: 20px; font-weight: 500;
}
.footer-col ul { list-style: none; }
.footer-col li { margin-bottom: 10px; }
.footer-col a {
  font-size: 0.82rem; color: var(--gray); text-decoration: none;
  transition: color 0.2s;
}
.footer-col a:hover { color: var(--cream); }

.footer-bottom {
  border-top: 1px solid rgba(255,255,255,0.07);
  padding-top: 28px;
  display: flex; justify-content: space-between; align-items: center;
}
.footer-copy { font-size: 0.75rem; }
.footer-legal { display: flex; gap: 24px; }
.footer-legal a { font-size: 0.72rem; color: var(--gray); text-decoration: none; }
.footer-legal a:hover { color: var(--cream); }

/* ─── KEYFRAMES ─── */
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: none; }
}
@keyframes rotateSlow {
  from { transform: translate(-50%, -50%) rotate(0deg); }
  to { transform: translate(-50%, -50%) rotate(360deg); }
}
@keyframes pulse-dot {
  0%, 100% { opacity: 1; transform: scale(1); }
  50% { opacity: 0.4; transform: scale(0.7); }
}
@keyframes typingBounce {
  0%, 80%, 100% { transform: translateY(0); opacity: 0.4; }
  40% { transform: translateY(-6px); opacity: 1; }
}

/* ─── RESPONSIVE ─── */
@media (max-width: 900px) {
  nav { padding: 0 24px; }
  .nav-links { display: none; }
  .hero { padding: 100px 24px 80px; }
  .hero-stats { position: static; margin-top: 48px; justify-content: flex-start; }
  section { padding: 72px 24px; }
  .modules-grid { grid-template-columns: 1fr; }
  .memory-layout { grid-template-columns: 1fr; }
  .memory-visual { height: 280px; }
  .casos-features { grid-template-columns: 1fr; }
  footer { padding: 40px 24px; }
  .footer-top { flex-direction: column; gap: 32px; }
  .footer-bottom { flex-direction: column; gap: 16px; text-align: center; }
  .cursor, .cursor-dot, .cursor-ring { display: none; }
  body { cursor: auto; }
  a, button { cursor: pointer; }
}
</style>
</head>
<body>

<!-- Custom cursor -->
<div class="cursor" id="cursor">
  <div class="cursor-ring" id="cursorRing"></div>
  <div class="cursor-dot" id="cursorDot"></div>
</div>

<!-- NAV -->
<nav id="mainNav">
  <a href="#" class="nav-logo">Admin<span>Master</span></a>
  <ul class="nav-links">
    <li><a href="#modulos">Módulos CIM</a></li>
    <li><a href="#memoria">Memoria de Marca</a></li>
    <li><a href="#casos">Casos Reales</a></li>
    <li><a href="#" class="nav-cta">Comenzar</a></li>
  </ul>
</nav>

<!-- HERO -->
<section class="hero" id="inicio">
  <div class="hero-bg"></div>
  <div class="hero-grid-lines"></div>
  <div class="hero-content">
    <div class="hero-eyebrow">Plataforma Educativa · CIM</div>
    <h1 class="hero-title">
      Domina las <em>Comunicaciones</em><br>
      <strong>Integradas</strong> de Mercadeo
    </h1>
    <p class="hero-desc">
      AdminMaster reúne los cinco pilares de las CIM en una sola plataforma.
      Aprende, aplica y valida estrategias de marca con agentes de IA especializados
      que trabajan en sincronía.
    </p>
    <div class="hero-actions">
      <a href="#modulos" class="btn-primary">Explorar Módulos</a>
      <a href="#casos" class="btn-ghost">Ver Demo</a>
    </div>
  </div>
  <div class="hero-stats">
    <div class="stat">
      <div class="stat-num">5<span>+</span></div>
      <div class="stat-label">Pilares CIM</div>
    </div>
    <div class="stat">
      <div class="stat-num">4<span>×</span></div>
      <div class="stat-label">Agentes IA</div>
    </div>
    <div class="stat">
      <div class="stat-num">360<span>°</span></div>
      <div class="stat-label">Visión de Marca</div>
    </div>
  </div>
</section>

<!-- MÓDULOS CIM -->
<section id="modulos">
  <div class="reveal">
    <div class="section-label">Pilares CIM</div>
    <h2 class="section-title">Los cinco <em>ejes</em> de<br>la comunicación integrada</h2>
    <p class="section-desc">Cada módulo activa un agente especializado. Juntos, construyen una voz de marca coherente, omnicanal y medible.</p>
  </div>

  <div class="modules-grid">

    <!-- 1. Publicidad -->
    <div class="module-card reveal reveal-delay-1">
      <span class="module-number">01</span>
      <div class="module-icon">
        <svg viewBox="0 0 24 24"><polygon points="23 7 16 12 23 17 23 7"/><rect x="1" y="5" width="15" height="14" rx="2" ry="2"/></svg>
      </div>
      <div class="module-tag">Pilar I</div>
      <h3 class="module-name">Publicidad</h3>
      <p class="module-desc">Diseña campañas 360° y selecciona medios con precisión. El agente evalúa audiencias, presupuesto y objetivos para generar briefs creativos accionables.</p>
      <button class="module-btn" onclick="openModal('publicidad')">
        Consultar Agente
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg>
      </button>
    </div>

    <!-- 2. RR.PP. -->
    <div class="module-card reveal reveal-delay-2">
      <span class="module-number">02</span>
      <div class="module-icon">
        <svg viewBox="0 0 24 24"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg>
      </div>
      <div class="module-tag">Pilar II</div>
      <h3 class="module-name">Relaciones Públicas</h3>
      <p class="module-desc">Gestiona la reputación y produce comunicados de prensa estratégicos. El agente monitorea la narrativa de marca y sugiere respuestas ante crisis de imagen.</p>
      <button class="module-btn" onclick="openModal('rrpp')">
        Consultar Agente
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg>
      </button>
    </div>

    <!-- 3. Promoción de Ventas -->
    <div class="module-card reveal reveal-delay-3">
      <span class="module-number">03</span>
      <div class="module-icon">
        <svg viewBox="0 0 24 24"><polyline points="23 6 13.5 15.5 8.5 10.5 1 18"/><polyline points="17 6 23 6 23 12"/></svg>
      </div>
      <div class="module-tag">Pilar III</div>
      <h3 class="module-name">Promoción de Ventas</h3>
      <p class="module-desc">Crea incentivos que conviertan sin devaluar la marca. El agente genera estructuras de descuento, loyalty programs y mecánicas de activación con ROI positivo.</p>
      <button class="module-btn" onclick="openModal('promocion')">
        Consultar Agente
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg>
      </button>
    </div>

    <!-- 4. Marketing Directo -->
    <div class="module-card reveal reveal-delay-1">
      <span class="module-number">04</span>
      <div class="module-icon">
        <svg viewBox="0 0 24 24"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
      </div>
      <div class="module-tag">Pilar IV</div>
      <h3 class="module-name">Marketing Directo</h3>
      <p class="module-desc">Segmenta con precisión y personaliza cada punto de contacto. El agente diseña secuencias de email, SMS y automatizaciones basadas en comportamiento real del cliente.</p>
      <button class="module-btn" onclick="openModal('directo')">
        Consultar Agente
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg>
      </button>
    </div>

    <!-- 5. Venta Personal -->
    <div class="module-card reveal reveal-delay-2">
      <span class="module-number">05</span>
      <div class="module-icon">
        <svg viewBox="0 0 24 24"><path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"/><circle cx="12" cy="7" r="4"/></svg>
      </div>
      <div class="module-tag">Pilar V</div>
      <h3 class="module-name">Venta Personal</h3>
      <p class="module-desc">Potencia el equipo comercial con guiones, manejo de objeciones y técnicas de cierre. El agente simula escenarios de ventas y evalúa el pitch en tiempo real.</p>
      <button class="module-btn" onclick="openModal('ventas')">
        Consultar Agente
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg>
      </button>
    </div>

    <!-- 6. Estrategia Digital (Bonus) -->
    <div class="module-card reveal reveal-delay-3">
      <span class="module-number">06</span>
      <div class="module-icon">
        <svg viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/><line x1="2" y1="12" x2="22" y2="12"/><path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"/></svg>
      </div>
      <div class="module-tag">Agente Especial</div>
      <h3 class="module-name">Estrategia Digital</h3>
      <p class="module-desc">Redes sociales, contenido interactivo y SEO integrados. El agente analiza tendencias en tiempo real y co-crea calendarios editoriales alineados a la voz de marca.</p>
      <button class="module-btn" onclick="openModal('digital')">
        Consultar Agente
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg>
      </button>
    </div>

  </div>
</section>

<!-- MEMORIA DE MARCA -->
<section id="memoria">
  <div class="memory-layout">
    <div class="reveal">
      <div class="section-label">Memoria Centralizada</div>
      <h2 class="section-title">Una sola <em>voz</em>,<br>todos los canales</h2>
      <p class="section-desc">
        Los agentes comparten una memoria de marca unificada. Las recomendaciones de publicidad no contradicen a las de RR.PP. porque todos hablan desde el mismo ADN de marca.
      </p>
      <div class="memory-agents">
        <div class="memory-agent-item">
          <div class="ma-icon">
            <svg viewBox="0 0 24 24"><polygon points="23 7 16 12 23 17 23 7"/><rect x="1" y="5" width="15" height="14" rx="2"/></svg>
          </div>
          <div class="ma-info">
            <div class="ma-name">Agente de Publicidad</div>
            <div class="ma-role">Campañas · Medios · Creative Brief</div>
          </div>
          <div class="ma-sync"></div>
        </div>
        <div class="memory-agent-item">
          <div class="ma-icon">
            <svg viewBox="0 0 24 24"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg>
          </div>
          <div class="ma-info">
            <div class="ma-name">Agente de RR.PP.</div>
            <div class="ma-role">Reputación · Comunicados · Crisis</div>
          </div>
          <div class="ma-sync"></div>
        </div>
        <div class="memory-agent-item">
          <div class="ma-icon">
            <svg viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/><line x1="2" y1="12" x2="22" y2="12"/><path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10z"/></svg>
          </div>
          <div class="ma-info">
            <div class="ma-name">Agente Digital</div>
            <div class="ma-role">Social Media · Contenido · SEO</div>
          </div>
          <div class="ma-sync"></div>
        </div>
        <div class="memory-agent-item">
          <div class="ma-icon">
            <svg viewBox="0 0 24 24"><polyline points="23 6 13.5 15.5 8.5 10.5 1 18"/><polyline points="17 6 23 6 23 12"/></svg>
          </div>
          <div class="ma-info">
            <div class="ma-name">Agente de Análisis</div>
            <div class="ma-role">Datos · Tendencias · Rentabilidad</div>
          </div>
          <div class="ma-sync"></div>
        </div>
      </div>
    </div>
    <div class="reveal reveal-delay-2">
      <div class="memory-visual">
        <div class="memory-ring ring-1">
          <div class="ring-dot"></div>
          <div class="ring-dot"></div>
          <div class="ring-dot"></div>
          <div class="ring-dot"></div>
        </div>
        <div class="memory-ring ring-2"></div>
        <div class="memory-ring ring-3"></div>
        <div class="memory-center">
          <svg viewBox="0 0 24 24"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/></svg>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- CASOS DE ANÁLISIS -->
<section id="casos">
  <div class="reveal">
    <div class="section-label">Análisis Estratégico</div>
    <h2 class="section-title">Sube tu plan,<br>recibe <em>retroalimentación</em> real</h2>
    <p class="section-desc">Los agentes analizan tus estados financieros, planes de negocio y métricas de campaña para entregarte insights accionables basados en indicadores de rentabilidad.</p>
  </div>

  <div class="reveal reveal-delay-1">
    <div class="upload-zone" onclick="document.getElementById('fileInput').click()">
      <input type="file" id="fileInput" accept=".pdf,.xlsx,.csv,.docx" style="display:none" onchange="handleFile(event)">
      <div class="upload-icon">
        <svg viewBox="0 0 24 24"><polyline points="16 16 12 12 8 16"/><line x1="12" y1="12" x2="12" y2="21"/><path d="M20.39 18.39A5 5 0 0 0 18 9h-1.26A8 8 0 1 0 3 16.3"/></svg>
      </div>
      <div class="upload-title">Arrastra o selecciona tu documento</div>
      <p class="upload-desc">Los agentes procesarán tu archivo y generarán un análisis estratégico<br>integrado desde la perspectiva de cada pilar CIM.</p>
      <div class="upload-formats">
        <span class="format-tag">PDF</span>
        <span class="format-tag">Excel</span>
        <span class="format-tag">CSV</span>
        <span class="format-tag">Word</span>
      </div>
    </div>
  </div>

  <div class="casos-features reveal reveal-delay-2">
    <div class="cf-item">
      <div class="cf-num">01</div>
      <div class="cf-title">Análisis de Rentabilidad</div>
      <p class="cf-desc">EBITDA, márgenes por línea y punto de equilibrio contrastados con benchmarks del sector.</p>
    </div>
    <div class="cf-item">
      <div class="cf-num">02</div>
      <div class="cf-title">Brechas de Comunicación</div>
      <p class="cf-desc">Identifica inconsistencias entre el mensaje, el canal y el posicionamiento objetivo de la marca.</p>
    </div>
    <div class="cf-item">
      <div class="cf-num">03</div>
      <div class="cf-title">Hoja de Ruta Integrada</div>
      <p class="cf-desc">Plan de acción priorizado por impacto/esfuerzo para los próximos 30, 60 y 90 días.</p>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-top">
    <div>
      <div class="footer-brand">Admin<span>Master</span></div>
      <div class="footer-tagline">Comunicaciones Integradas de Mercadeo — Plataforma Educativa Profesional</div>
    </div>
    <div class="footer-cols">
      <div class="footer-col">
        <h4>Módulos</h4>
        <ul>
          <li><a href="#">Publicidad</a></li>
          <li><a href="#">Relaciones Públicas</a></li>
          <li><a href="#">Promoción de Ventas</a></li>
          <li><a href="#">Marketing Directo</a></li>
          <li><a href="#">Venta Personal</a></li>
        </ul>
      </div>
      <div class="footer-col">
        <h4>Plataforma</h4>
        <ul>
          <li><a href="#">Agentes IA</a></li>
          <li><a href="#">Memoria de Marca</a></li>
          <li><a href="#">Análisis de Casos</a></li>
          <li><a href="#">Recursos</a></li>
        </ul>
      </div>
    </div>
  </div>
  <div class="footer-bottom">
    <div class="footer-copy">© 2025 AdminMaster. Todos los derechos reservados.</div>
    <div class="footer-legal">
      <a href="#">Privacidad</a>
      <a href="#">Términos</a>
      <a href="#">Contacto</a>
    </div>
  </div>
</footer>

<!-- ─── AGENT MODAL ─── -->
<div class="modal-overlay" id="agentModal">
  <div class="modal">
    <div class="modal-header">
      <div class="modal-agent-info">
        <div class="modal-agent-avatar" id="modalAvatar">
          <svg viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/></svg>
        </div>
        <div>
          <div class="modal-agent-name" id="modalAgentName">Agente</div>
          <div class="modal-agent-status">En línea</div>
        </div>
      </div>
      <button class="modal-close" onclick="closeModal()">×</button>
    </div>
    <div class="modal-context" id="modalContext">
      <strong>Memoria de marca activa</strong> · Todos los agentes están sincronizados con el ADN de tu marca.
    </div>
    <div class="chat-window" id="chatWindow"></div>
    <div class="chat-suggestions" id="chatSuggestions"></div>
    <div class="chat-input-area">
      <textarea class="chat-input" id="chatInput" placeholder="Escribe tu consulta…" rows="1" onkeydown="handleKey(event)" oninput="autoResize(this)"></textarea>
      <button class="chat-send" onclick="sendMessage()">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="22" y1="2" x2="11" y2="13"/><polygon points="22 2 15 22 11 13 2 9 22 2"/></svg>
      </button>
    </div>
  </div>
</div>

<script>
// ─── CURSOR ───
const dot = document.getElementById('cursorDot');
const ring = document.getElementById('cursorRing');
let mx = 0, my = 0, rx = 0, ry = 0;
document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; });
function animateCursor() {
  if (dot) { dot.style.left = mx + 'px'; dot.style.top = my + 'px'; }
  rx += (mx - rx) * 0.12; ry += (my - ry) * 0.12;
  if (ring) { ring.style.left = rx + 'px'; ring.style.top = ry + 'px'; }
  requestAnimationFrame(animateCursor);
}
animateCursor();

// ─── NAV SCROLL ───
window.addEventListener('scroll', () => {
  document.getElementById('mainNav').classList.toggle('scrolled', window.scrollY > 40);
});

// ─── SCROLL REVEAL ───
const observer = new IntersectionObserver(entries => {
  entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
}, { threshold: 0.1 });
document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

// ─── AGENTS CONFIG ───
const agents = {
  publicidad: {
    name: 'Agente de Publicidad',
    icon: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><polygon points="23 7 16 12 23 17 23 7"/><rect x="1" y="5" width="15" height="14" rx="2"/></svg>',
    systemPrompt: `Eres el Agente de Publicidad de AdminMaster, una plataforma educativa sobre Comunicaciones Integradas de Mercadeo (CIM).
Eres un especialista senior en diseño de campañas publicitarias y selección de medios.
Tu función es ayudar a emprendedores y estudiantes a diseñar campañas efectivas, briefs creativos, estrategias de medios y mensajes publicitarios.
Compartes una memoria de marca con los demás agentes: Agente de RR.PP., Agente Digital y Agente de Análisis.
Responde siempre en español, de forma profesional pero accesible. Sé concreto y estratégico. Máximo 180 palabras por respuesta.`,
    welcome: '¡Hola! Soy tu Agente de Publicidad. Puedo ayudarte a diseñar campañas, seleccionar medios, definir mensajes clave y crear briefs creativos. ¿Con qué proyecto trabajamos hoy?',
    suggestions: ['¿Cómo defino mi mix de medios?', 'Crea un brief creativo para mi marca', '¿Qué KPIs medir en mi campaña?']
  },
  rrpp: {
    name: 'Agente de RR.PP.',
    icon: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg>',
    systemPrompt: `Eres el Agente de Relaciones Públicas de AdminMaster, plataforma educativa sobre CIM.
Eres experto en gestión de reputación corporativa, comunicados de prensa, manejo de crisis y relaciones con medios.
Tu misión es ayudar a construir y proteger la imagen de marca de emprendedores y estudiantes.
Compartes memoria de marca con los demás agentes CIM para garantizar coherencia en todas las comunicaciones.
Responde siempre en español, profesional y con ejemplos prácticos. Máximo 180 palabras.`,
    welcome: 'Hola, soy tu Agente de RR.PP. Mi especialidad es la reputación y las relaciones con públicos clave. Puedo ayudarte a redactar comunicados, preparar portavoces o diseñar un plan de gestión de crisis. ¿Cuál es el desafío de tu marca?',
    suggestions: ['Redacta un comunicado de prensa', 'Plan de manejo de crisis de reputación', '¿Cómo relacionarme con medios?']
  },
  promocion: {
    name: 'Agente de Promoción de Ventas',
    icon: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><polyline points="23 6 13.5 15.5 8.5 10.5 1 18"/><polyline points="17 6 23 6 23 12"/></svg>',
    systemPrompt: `Eres el Agente de Promoción de Ventas de AdminMaster, plataforma CIM educativa.
Diseñas estrategias de incentivos: descuentos, concursos, programas de lealtad, activaciones BTL y mecánicas de conversión.
Tu objetivo es maximizar el volumen de ventas sin erosionar el valor percibido de la marca.
Trabajas en coordinación con los demás agentes CIM para que las promociones sean coherentes con la narrativa de marca.
Responde siempre en español, con lógica financiera y creatividad comercial. Máximo 180 palabras.`,
    welcome: '¡Bienvenido! Soy el Agente de Promoción de Ventas. Diseño incentivos que convierten sin devaluar tu marca. Desde descuentos estratégicos hasta loyalty programs y activaciones. ¿Qué objetivo de ventas quieres alcanzar?',
    suggestions: ['Diseña un programa de lealtad', '¿Cómo descuento sin dañar mi marca?', 'Ideas de activaciones BTL para mi producto']
  },
  directo: {
    name: 'Agente de Marketing Directo',
    icon: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>',
    systemPrompt: `Eres el Agente de Marketing Directo de AdminMaster, plataforma educativa CIM.
Eres experto en segmentación, personalización y automatización de comunicaciones directas: email, SMS, WhatsApp, retargeting.
Ayudas a diseñar secuencias automatizadas, funnels de conversión y estrategias de nurturing basadas en comportamiento.
Mantienes coherencia con el ADN de marca gracias a la memoria compartida con los otros agentes.
Responde en español, con enfoque en resultados medibles. Máximo 180 palabras.`,
    welcome: 'Hola, soy el Agente de Marketing Directo. Diseño comunicaciones personalizadas que llegan a la persona correcta, en el momento exacto, con el mensaje adecuado. ¿Qué canal o secuencia quieres optimizar?',
    suggestions: ['Diseña una secuencia de bienvenida por email', 'Segmentación para mi lista de clientes', '¿Cómo medir mi tasa de conversión?']
  },
  ventas: {
    name: 'Agente de Venta Personal',
    icon: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"/><circle cx="12" cy="7" r="4"/></svg>',
    systemPrompt: `Eres el Agente de Venta Personal de AdminMaster, plataforma educativa CIM.
Eres coach de ventas B2B y B2C: guiones de venta, manejo de objeciones, técnicas de cierre y desarrollo de fuerza comercial.
Puedes simular escenarios de venta, evaluar pitches y entrenar equipos de ventas.
Trabajas con la memoria de marca compartida para que el equipo comercial sea coherente con los mensajes de publicidad y RR.PP.
Responde en español, directo y con técnicas probadas. Máximo 180 palabras.`,
    welcome: '¡Hola! Soy el Agente de Venta Personal. Puedo ayudarte a mejorar tu pitch, manejar objeciones o simular una negociación difícil. ¿Quieres practicar una venta o diseñar tu proceso comercial?',
    suggestions: ['Simula una objeción de precio', 'Crea mi guion de ventas', '¿Cómo hago seguimiento sin ser invasivo?']
  },
  digital: {
    name: 'Agente de Estrategia Digital',
    icon: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="12" cy="12" r="10"/><line x1="2" y1="12" x2="22" y2="12"/><path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"/></svg>',
    systemPrompt: `Eres el Agente de Estrategia Digital de AdminMaster, plataforma CIM educativa.
Eres experto en social media marketing, SEO, contenido interactivo, marketing de influencers y estrategia digital integrada.
Analizas tendencias, diseñas calendarios editoriales y creas estrategias de contenido alineadas con la voz de marca.
Compartes memoria con los otros agentes para garantizar coherencia omnicanal.
Responde en español, con datos, tendencias y ejemplos concretos. Máximo 180 palabras.`,
    welcome: '¡Hola! Soy el Agente de Estrategia Digital. Mi especialidad es construir presencia digital coherente y con resultados. Puedo ayudarte con tu estrategia en redes, SEO, contenido y más. ¿Por dónde empezamos?',
    suggestions: ['Crea un calendario editorial mensual', '¿Qué redes sociales usar para mi marca?', 'Estrategia de contenido para Instagram y LinkedIn']
  }
};

let currentAgent = null;
let chatHistory = [];

const avatarIcons = {
  publicidad: agents.publicidad.icon,
  rrpp: agents.rrpp.icon,
  promocion: agents.promocion.icon,
  directo: agents.directo.icon,
  ventas: agents.ventas.icon,
  digital: agents.digital.icon
};

function openModal(agentKey) {
  currentAgent = agentKey;
  chatHistory = [];
  const ag = agents[agentKey];
  document.getElementById('modalAgentName').textContent = ag.name;
  document.getElementById('modalAvatar').innerHTML = ag.icon;
  const chatWindow = document.getElementById('chatWindow');
  chatWindow.innerHTML = '';
  addMessage('agent', ag.welcome);
  const sugg = document.getElementById('chatSuggestions');
  sugg.innerHTML = '';
  ag.suggestions.forEach(s => {
    const btn = document.createElement('button');
    btn.className = 'chat-suggestion';
    btn.textContent = s;
    btn.onclick = () => { document.getElementById('chatInput').value = s; sendMessage(); };
    sugg.appendChild(btn);
  });
  document.getElementById('agentModal').classList.add('open');
  document.body.style.overflow = 'hidden';
}

function closeModal() {
  document.getElementById('agentModal').classList.remove('open');
  document.body.style.overflow = '';
}

document.getElementById('agentModal').addEventListener('click', e => {
  if (e.target === e.currentTarget) closeModal();
});

function addMessage(role, text) {
  const chatWindow = document.getElementById('chatWindow');
  const msg = document.createElement('div');
  msg.className = `chat-msg ${role}`;
  const now = new Date().toLocaleTimeString('es-CO', { hour: '2-digit', minute: '2-digit' });
  msg.innerHTML = `<div class="chat-bubble">${text.replace(/\n/g, '<br>')}</div><div class="chat-time">${now}</div>`;
  chatWindow.appendChild(msg);
  chatWindow.scrollTop = chatWindow.scrollHeight;
  if (role === 'agent') {
    chatHistory.push({ role: 'assistant', content: text });
  }
}

function showTyping() {
  const chatWindow = document.getElementById('chatWindow');
  const t = document.createElement('div');
  t.className = 'typing-indicator'; t.id = 'typingIndicator';
  t.innerHTML = '<div class="typing-dot"></div><div class="typing-dot"></div><div class="typing-dot"></div>';
  chatWindow.appendChild(t);
  chatWindow.scrollTop = chatWindow.scrollHeight;
}
function hideTyping() {
  const t = document.getElementById('typingIndicator');
  if (t) t.remove();
}

async function sendMessage() {
  const input = document.getElementById('chatInput');
  const text = input.value.trim();
  if (!text || !currentAgent) return;
  input.value = ''; input.style.height = '44px';
  addMessage('user', text);
  chatHistory.push({ role: 'user', content: text });
  document.getElementById('chatSuggestions').innerHTML = '';
  showTyping();

  try {
    const ag = agents[currentAgent];
    const response = await fetch('https://api.anthropic.com/v1/messages', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({
        model: 'claude-sonnet-4-20250514',
        max_tokens: 1000,
        system: ag.systemPrompt,
        messages: chatHistory
      })
    });
    const data = await response.json();
    hideTyping();
    if (data.content && data.content[0]) {
      addMessage('agent', data.content[0].text);
    } else {
      addMessage('agent', 'Lo siento, ocurrió un error. Por favor intenta de nuevo.');
    }
  } catch (err) {
    hideTyping();
    addMessage('agent', 'Hubo un problema de conexión. Verifica tu API key y vuelve a intentarlo.');
  }
}

function handleKey(e) {
  if (e.key === 'Enter' && !e.shiftKey) {
    e.preventDefault(); sendMessage();
  }
}
function autoResize(el) {
  el.style.height = '44px';
  el.style.height = Math.min(el.scrollHeight, 100) + 'px';
}

function handleFile(e) {
  const file = e.target.files[0];
  if (!file) return;
  openModal('digital');
  setTimeout(() => {
    document.getElementById('chatInput').value = `Acabo de subir el archivo "${file.name}". Por favor analízalo desde la perspectiva de las CIM y dame retroalimentación estratégica.`;
    sendMessage();
  }, 600);
}
</script>
</body>
</html>
