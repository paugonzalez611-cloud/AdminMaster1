<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>AdminMaster — Inteligencia de Marca Integrada</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,500;0,700;1,400;1,500&family=Outfit:wght@200;300;400;500;600&display=swap" rel="stylesheet">
<style>
/* ───────────────────────────────────────────
   TOKENS
─────────────────────────────────────────── */
:root {
  --bg:       #0A0908;
  --bg-1:     #110F0D;
  --bg-2:     #171410;
  --bg-card:  rgba(255,255,255,0.035);
  --bg-card-h:rgba(255,255,255,0.06);
  --gold:     #C9A84C;
  --gold-2:   #E8C96A;
  --gold-dim: rgba(201,168,76,0.18);
  --gold-line:rgba(201,168,76,0.25);
  --cream:    #F2EDDF;
  --text:     #EAE5D8;
  --text-2:   #9B9589;
  --text-3:   #5A554D;
  --line:     rgba(255,255,255,0.07);
  --red:      #C0392B;
  --green:    #27AE60;
  --r:        4px;
  --shadow:   0 8px 40px rgba(0,0,0,0.5);
  --shadow-lg:0 24px 80px rgba(0,0,0,0.65);
}

*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth;font-size:16px}
body{
  font-family:'Outfit',sans-serif;
  background:var(--bg);
  color:var(--text);
  overflow-x:hidden;
  line-height:1.6;
  cursor:none;
}

/* ───────── CUSTOM CURSOR ───────── */
#cur-dot,#cur-ring{
  position:fixed;top:0;left:0;
  pointer-events:none;z-index:9999;
  transform:translate(-50%,-50%);
}
#cur-dot{
  width:6px;height:6px;
  background:var(--gold);border-radius:50%;
  transition:transform .08s;
}
#cur-ring{
  width:36px;height:36px;
  border:1.5px solid var(--gold);
  border-radius:50%;opacity:.5;
  transition:width .25s,height .25s,opacity .25s,transform .16s ease;
}
body:has(a:hover,button:hover,.ag-card:hover) #cur-ring{
  width:52px;height:52px;opacity:.9;
}

/* ───────── CANVAS BG ───────── */
#starCanvas{
  position:fixed;inset:0;z-index:0;
  pointer-events:none;opacity:.6;
}

/* ───────── NOISE OVERLAY ───────── */
body::before{
  content:'';position:fixed;inset:0;z-index:1;
  background-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.03'/%3E%3C/svg%3E");
  pointer-events:none;opacity:.4;
}

/* ───────── REVEAL ───────── */
.rv{opacity:0;transform:translateY(32px);transition:opacity .8s ease,transform .8s ease}
.rv.on{opacity:1;transform:none}
.rv.d1{transition-delay:.1s}.rv.d2{transition-delay:.2s}
.rv.d3{transition-delay:.3s}.rv.d4{transition-delay:.4s}
.rv.d5{transition-delay:.5s}.rv.d6{transition-delay:.6s}

/* ───────── NAV ───────── */
nav{
  position:fixed;top:0;left:0;right:0;z-index:200;
  height:68px;
  display:flex;align-items:center;justify-content:space-between;
  padding:0 56px;
  background:rgba(10,9,8,.8);
  backdrop-filter:blur(20px);
  border-bottom:1px solid var(--line);
  transition:box-shadow .3s;
}
nav.sc{box-shadow:0 4px 32px rgba(0,0,0,.6)}

.logo{
  font-family:'Playfair Display',serif;
  font-size:1.5rem;font-weight:500;
  color:var(--text);text-decoration:none;letter-spacing:.03em;
}
.logo span{color:var(--gold)}

.nav-links{display:flex;align-items:center;gap:36px;list-style:none}
.nav-links a{
  font-size:.78rem;font-weight:400;letter-spacing:.1em;
  text-transform:uppercase;color:var(--text-2);text-decoration:none;
  transition:color .2s;position:relative;padding-bottom:2px;
}
.nav-links a::after{
  content:'';position:absolute;bottom:0;left:0;
  width:0;height:1px;background:var(--gold);
  transition:width .3s;
}
.nav-links a:hover{color:var(--gold)}
.nav-links a:hover::after{width:100%}

.nav-badge{
  font-size:.68rem;font-weight:500;letter-spacing:.12em;
  text-transform:uppercase;
  background:linear-gradient(135deg,var(--gold),var(--gold-2));
  color:var(--bg);padding:8px 22px;border-radius:2px;
  border:none;cursor:none;
  transition:opacity .2s,transform .2s;
}
.nav-badge:hover{opacity:.88;transform:translateY(-1px)}

/* ───────── HERO ───────── */
.hero{
  min-height:100vh;
  display:flex;align-items:center;
  padding:120px 56px 80px;
  position:relative;z-index:2;
  overflow:hidden;
}

.hero-glow{
  position:absolute;
  width:800px;height:800px;
  background:radial-gradient(circle,rgba(201,168,76,.08) 0%,transparent 70%);
  top:50%;left:50%;transform:translate(-10%,-50%);
  pointer-events:none;
}

.hero-left{max-width:680px;position:relative}

.hero-sup{
  display:inline-flex;align-items:center;gap:10px;
  font-size:.7rem;font-weight:500;letter-spacing:.22em;
  text-transform:uppercase;color:var(--gold);margin-bottom:32px;
  opacity:0;animation:aUp .8s .2s forwards;
}
.hero-sup::before{
  content:'';width:28px;height:1px;background:var(--gold);
}

h1.hero-h{
  font-family:'Playfair Display',serif;
  font-size:clamp(3rem,6.5vw,5.8rem);
  font-weight:400;line-height:1.06;
  letter-spacing:-.02em;
  margin-bottom:28px;
  opacity:0;animation:aUp .9s .35s forwards;
}
h1.hero-h em{font-style:italic;color:var(--gold)}
h1.hero-h strong{font-weight:700}

.hero-body{
  font-size:1.05rem;font-weight:300;line-height:1.8;
  color:var(--text-2);max-width:500px;margin-bottom:48px;
  opacity:0;animation:aUp .9s .5s forwards;
}

.hero-btns{
  display:flex;gap:14px;align-items:center;
  opacity:0;animation:aUp .9s .65s forwards;
}

.btn-gold{
  background:linear-gradient(135deg,var(--gold),var(--gold-2));
  color:var(--bg);padding:14px 36px;border:none;
  border-radius:2px;font-family:'Outfit',sans-serif;
  font-size:.8rem;font-weight:600;letter-spacing:.1em;
  text-transform:uppercase;cursor:none;
  text-decoration:none;display:inline-block;
  transition:opacity .2s,transform .2s,box-shadow .2s;
}
.btn-gold:hover{
  opacity:.9;transform:translateY(-2px);
  box-shadow:0 8px 24px rgba(201,168,76,.3);
}
.btn-outline{
  color:var(--text-2);background:transparent;
  border:1px solid var(--line);
  padding:14px 32px;border-radius:2px;
  font-size:.8rem;font-weight:400;letter-spacing:.06em;
  cursor:none;text-decoration:none;display:inline-block;
  transition:border-color .2s,color .2s;
}
.btn-outline:hover{border-color:var(--gold-line);color:var(--gold)}

/* hero stats */
.hero-stats{
  display:flex;gap:52px;margin-top:72px;
  padding-top:40px;border-top:1px solid var(--line);
  opacity:0;animation:aUp .9s .8s forwards;
}
.hstat-n{
  font-family:'Playfair Display',serif;
  font-size:2.6rem;font-weight:400;color:var(--text);line-height:1;
}
.hstat-n span{color:var(--gold)}
.hstat-l{
  font-size:.68rem;letter-spacing:.14em;text-transform:uppercase;
  color:var(--text-3);margin-top:6px;
}

/* ───────── MARQUEE ───────── */
.marquee-wrap{
  position:relative;z-index:2;
  overflow:hidden;border-top:1px solid var(--line);
  border-bottom:1px solid var(--line);
  padding:18px 0;background:var(--bg-1);
}
.marquee-track{
  display:flex;gap:0;
  animation:marquee 28s linear infinite;
  width:max-content;
}
.marquee-item{
  font-size:.7rem;font-weight:400;letter-spacing:.18em;
  text-transform:uppercase;color:var(--text-3);
  padding:0 40px;white-space:nowrap;
  display:flex;align-items:center;gap:16px;
}
.marquee-item::after{
  content:'✦';color:var(--gold);font-size:.55rem;
}
@keyframes marquee{from{transform:translateX(0)}to{transform:translateX(-50%)}}

/* ───────── SECTION SHELL ───────── */
.section{padding:110px 56px;position:relative;z-index:2}
.section.dark{background:var(--bg-1)}
.section.darker{background:var(--bg-2)}

.sec-label{
  display:inline-flex;align-items:center;gap:10px;
  font-size:.68rem;font-weight:500;letter-spacing:.2em;
  text-transform:uppercase;color:var(--gold);margin-bottom:18px;
}
.sec-label::before{content:'';width:20px;height:1px;background:var(--gold)}

.sec-h{
  font-family:'Playfair Display',serif;
  font-size:clamp(2rem,4vw,3.4rem);
  font-weight:400;line-height:1.12;margin-bottom:16px;
}
.sec-h em{font-style:italic;color:var(--gold)}

.sec-p{
  font-size:.95rem;font-weight:300;color:var(--text-2);
  max-width:520px;line-height:1.85;margin-bottom:64px;
}

/* ───────── AGENTS GRID ───────── */
.ag-grid{
  display:grid;
  grid-template-columns:repeat(4,1fr);
  gap:1px;
  background:var(--line);
  border:1px solid var(--line);
  border-radius:var(--r);
  overflow:hidden;
}

.ag-card{
  background:var(--bg);
  padding:36px 32px;
  position:relative;overflow:hidden;
  cursor:none;
  transition:background .3s;
  display:flex;flex-direction:column;gap:0;
}
.ag-card::after{
  content:'';
  position:absolute;bottom:0;left:0;right:0;
  height:2px;
  background:linear-gradient(90deg,var(--gold),var(--gold-2));
  transform:scaleX(0);transform-origin:left;
  transition:transform .4s ease;
}
.ag-card:hover{background:var(--bg-1)}
.ag-card:hover::after{transform:scaleX(1)}

.ag-num{
  position:absolute;top:28px;right:28px;
  font-family:'Playfair Display',serif;
  font-size:3.2rem;font-weight:400;
  color:rgba(201,168,76,.08);line-height:1;
  transition:color .3s;
  pointer-events:none;
}
.ag-card:hover .ag-num{color:rgba(201,168,76,.13)}

.ag-icon{
  width:46px;height:46px;
  background:var(--gold-dim);
  border-radius:3px;
  display:flex;align-items:center;justify-content:center;
  margin-bottom:22px;
  flex-shrink:0;
  transition:background .3s;
}
.ag-card:hover .ag-icon{background:rgba(201,168,76,.28)}
.ag-icon svg{width:22px;height:22px;stroke:var(--gold);fill:none;stroke-width:1.5}

.ag-cat{
  font-size:.62rem;letter-spacing:.2em;text-transform:uppercase;
  color:var(--gold);font-weight:500;margin-bottom:8px;
}
.ag-name{
  font-family:'Playfair Display',serif;
  font-size:1.3rem;font-weight:400;
  color:var(--text);margin-bottom:10px;line-height:1.2;
}
.ag-desc{
  font-size:.82rem;font-weight:300;color:var(--text-2);
  line-height:1.7;flex:1;margin-bottom:24px;
}

.ag-pills{
  display:flex;flex-wrap:wrap;gap:6px;margin-bottom:22px;
}
.ag-pill{
  font-size:.6rem;letter-spacing:.1em;text-transform:uppercase;
  border:1px solid var(--line);border-radius:20px;
  padding:3px 10px;color:var(--text-3);
  transition:border-color .2s,color .2s;
}
.ag-card:hover .ag-pill{border-color:var(--gold-line);color:var(--text-2)}

.ag-btn{
  display:inline-flex;align-items:center;gap:8px;
  font-size:.72rem;font-weight:500;letter-spacing:.1em;
  text-transform:uppercase;color:var(--text-2);
  background:none;border:none;border-bottom:1px solid var(--text-3);
  padding-bottom:3px;cursor:none;
  transition:color .2s,border-color .2s;
}
.ag-btn svg{width:13px;height:13px;transition:transform .2s}
.ag-btn:hover{color:var(--gold);border-color:var(--gold)}
.ag-btn:hover svg{transform:translateX(3px)}

/* ───────── BRAND CORE ───────── */
.brand-layout{
  display:grid;grid-template-columns:1fr 1fr;
  gap:80px;align-items:center;
}

.brand-vis{
  position:relative;height:460px;
}

/* Hex grid visual */
.hex-container{
  position:absolute;top:50%;left:50%;
  transform:translate(-50%,-50%);
  width:320px;height:320px;
}
.hex{
  position:absolute;
  clip-path:polygon(50% 0%,100% 25%,100% 75%,50% 100%,0% 75%,0% 25%);
  display:flex;align-items:center;justify-content:center;
  transition:transform .3s;
}
.hex-center{
  width:96px;height:96px;
  background:linear-gradient(135deg,var(--gold),var(--gold-2));
  top:50%;left:50%;
  transform:translate(-50%,-50%);
}
.hex-center svg{width:36px;height:36px;stroke:var(--bg);fill:none;stroke-width:1.5}
.hex-orbit{
  width:64px;height:64px;
  background:var(--bg-2);
  border:1px solid var(--gold-line);
}
.hex-orbit svg{width:22px;height:22px;stroke:var(--gold);fill:none;stroke-width:1.5}

/* orbit positions */
.ho-1{top:0;left:50%;transform:translate(-50%,0)}
.ho-2{top:18%;right:0;transform:translate(0,0)}
.ho-3{bottom:18%;right:0;transform:translate(0,0)}
.ho-4{bottom:0;left:50%;transform:translate(-50%,0)}
.ho-5{bottom:18%;left:0;transform:translate(0,0)}
.ho-6{top:18%;left:0;transform:translate(0,0)}

.orbit-ring{
  position:absolute;top:50%;left:50%;
  transform:translate(-50%,-50%);
  border:1px dashed rgba(201,168,76,.2);
  border-radius:50%;
}
.or-1{width:200px;height:200px;animation:spin 25s linear infinite}
.or-2{width:290px;height:290px;animation:spin 40s linear infinite reverse}

.brand-list{display:flex;flex-direction:column;gap:14px}
.brand-item{
  display:flex;align-items:center;gap:16px;
  padding:18px 22px;
  background:var(--bg-card);
  border:1px solid var(--line);
  border-radius:3px;
  transition:border-color .25s,transform .25s;
}
.brand-item:hover{border-color:var(--gold-line);transform:translateX(5px)}
.bi-dot{
  width:8px;height:8px;border-radius:50%;
  background:var(--green);flex-shrink:0;
  box-shadow:0 0 8px rgba(39,174,96,.5);
  animation:blink 2.5s infinite;
}
.bi-dot.busy{background:var(--gold);box-shadow:0 0 8px rgba(201,168,76,.5)}
.bi-info{flex:1}
.bi-name{font-size:.88rem;font-weight:500;color:var(--text)}
.bi-role{font-size:.72rem;color:var(--text-3);margin-top:2px}
.bi-tag{
  font-size:.6rem;letter-spacing:.1em;text-transform:uppercase;
  padding:3px 10px;border-radius:2px;
  background:var(--gold-dim);color:var(--gold);
}

/* ───────── CASOS ───────── */
.upload-box{
  border:1px dashed rgba(201,168,76,.3);
  border-radius:var(--r);
  padding:64px 48px;text-align:center;
  background:rgba(201,168,76,.03);
  transition:border-color .3s,background .3s;
  cursor:none;
  position:relative;overflow:hidden;
}
.upload-box:hover{
  border-color:rgba(201,168,76,.6);
  background:rgba(201,168,76,.06);
}
.upload-ico{
  width:60px;height:60px;
  background:var(--gold-dim);border-radius:50%;
  display:flex;align-items:center;justify-content:center;
  margin:0 auto 20px;
}
.upload-ico svg{width:26px;height:26px;stroke:var(--gold);fill:none;stroke-width:1.5}
.upload-t{
  font-family:'Playfair Display',serif;
  font-size:1.6rem;font-weight:400;color:var(--text);margin-bottom:10px;
}
.upload-d{font-size:.85rem;color:var(--text-2);line-height:1.65}
.upload-chips{display:flex;gap:10px;justify-content:center;margin-top:20px}
.uchip{
  font-size:.65rem;letter-spacing:.14em;text-transform:uppercase;
  border:1px solid var(--gold-line);
  padding:4px 14px;border-radius:2px;color:var(--gold);
}

.feat-grid{
  display:grid;grid-template-columns:repeat(3,1fr);
  gap:1px;background:var(--line);
  border:1px solid var(--line);border-radius:3px;
  margin-top:48px;overflow:hidden;
}
.feat-item{
  padding:34px 30px;background:var(--bg);
  transition:background .3s;
}
.feat-item:hover{background:var(--bg-1)}
.feat-n{
  font-family:'Playfair Display',serif;
  font-size:2.8rem;font-weight:400;color:var(--gold);
  line-height:1;margin-bottom:14px;
}
.feat-t{font-size:.88rem;font-weight:500;color:var(--text);margin-bottom:8px}
.feat-d{font-size:.8rem;color:var(--text-3);line-height:1.65}

/* ───────── TESTIMONIALS ───────── */
.testi-grid{
  display:grid;grid-template-columns:repeat(3,1fr);gap:20px;
}
.testi-card{
  background:var(--bg-card);
  border:1px solid var(--line);
  border-radius:var(--r);
  padding:32px 28px;
  transition:border-color .25s,background .25s;
}
.testi-card:hover{
  border-color:var(--gold-line);
  background:var(--bg-card-h);
}
.testi-stars{color:var(--gold);font-size:.8rem;letter-spacing:2px;margin-bottom:16px}
.testi-q{
  font-family:'Playfair Display',serif;
  font-size:1rem;font-style:italic;color:var(--text);
  line-height:1.7;margin-bottom:22px;
}
.testi-divider{width:32px;height:1px;background:var(--gold-line);margin-bottom:18px}
.testi-author{display:flex;align-items:center;gap:12px}
.testi-avatar{
  width:38px;height:38px;border-radius:50%;
  background:var(--gold-dim);
  display:flex;align-items:center;justify-content:center;
  font-family:'Playfair Display',serif;
  font-size:1rem;color:var(--gold);
}
.testi-nm{font-size:.85rem;font-weight:500;color:var(--text)}
.testi-role{font-size:.72rem;color:var(--text-3)}

/* ───────── CTA ───────── */
.cta-block{
  background:linear-gradient(135deg,rgba(201,168,76,.12),rgba(201,168,76,.04));
  border:1px solid var(--gold-line);
  border-radius:var(--r);
  padding:80px 64px;
  text-align:center;
  position:relative;overflow:hidden;
}
.cta-block::before{
  content:'';
  position:absolute;top:-60%;left:50%;transform:translateX(-50%);
  width:400px;height:400px;
  background:radial-gradient(circle,rgba(201,168,76,.12),transparent 70%);
  pointer-events:none;
}
.cta-h{
  font-family:'Playfair Display',serif;
  font-size:clamp(2rem,4vw,3.2rem);
  font-weight:400;color:var(--text);
  margin-bottom:16px;
}
.cta-h em{font-style:italic;color:var(--gold)}
.cta-p{
  font-size:.95rem;font-weight:300;color:var(--text-2);
  max-width:440px;margin:0 auto 40px;line-height:1.8;
}

/* ───────── FOOTER ───────── */
footer{
  background:var(--bg-2);
  border-top:1px solid var(--line);
  padding:64px 56px 40px;
  position:relative;z-index:2;
}
.ft-top{
  display:grid;grid-template-columns:1.5fr repeat(3,1fr);
  gap:48px;margin-bottom:52px;
}
.ft-brand{
  font-family:'Playfair Display',serif;
  font-size:1.7rem;font-weight:400;color:var(--text);
}
.ft-brand span{color:var(--gold)}
.ft-tag{font-size:.8rem;color:var(--text-3);margin-top:8px;line-height:1.6;max-width:220px}

.ft-col h4{
  font-size:.65rem;letter-spacing:.2em;text-transform:uppercase;
  color:var(--gold);margin-bottom:18px;font-weight:500;
}
.ft-col ul{list-style:none}
.ft-col li{margin-bottom:10px}
.ft-col a{
  font-size:.82rem;color:var(--text-3);text-decoration:none;
  transition:color .2s;
}
.ft-col a:hover{color:var(--text)}

.ft-bottom{
  border-top:1px solid var(--line);
  padding-top:28px;
  display:flex;justify-content:space-between;align-items:center;
}
.ft-copy{font-size:.72rem;color:var(--text-3)}
.ft-legal{display:flex;gap:24px}
.ft-legal a{font-size:.7rem;color:var(--text-3);text-decoration:none}
.ft-legal a:hover{color:var(--text)}

/* ───────── MODAL ───────── */
.overlay{
  position:fixed;inset:0;z-index:500;
  background:rgba(0,0,0,.75);
  backdrop-filter:blur(12px);
  display:flex;align-items:center;justify-content:center;
  padding:20px;
  opacity:0;pointer-events:none;
  transition:opacity .3s;
}
.overlay.open{opacity:1;pointer-events:all}

.modal{
  background:var(--bg-1);
  border:1px solid var(--line);
  border-radius:var(--r);
  width:100%;max-width:660px;
  max-height:90vh;
  display:flex;flex-direction:column;
  box-shadow:var(--shadow-lg);
  transform:translateY(24px) scale(.97);
  transition:transform .35s cubic-bezier(.34,1.56,.64,1);
  overflow:hidden;
}
.overlay.open .modal{transform:none}

.modal-hd{
  padding:22px 26px;
  border-bottom:1px solid var(--line);
  display:flex;align-items:flex-start;justify-content:space-between;
  flex-shrink:0;
}
.modal-av{
  width:44px;height:44px;border-radius:50%;
  background:var(--gold-dim);border:1px solid var(--gold-line);
  display:flex;align-items:center;justify-content:center;
  flex-shrink:0;
}
.modal-av svg{width:20px;height:20px;stroke:var(--gold);fill:none;stroke-width:1.5}
.modal-ag-name{
  font-family:'Playfair Display',serif;
  font-size:1.2rem;font-weight:400;color:var(--text);
}
.modal-status{
  font-size:.68rem;color:var(--green);letter-spacing:.04em;
  display:flex;align-items:center;gap:5px;margin-top:2px;
}
.modal-status::before{
  content:'';width:6px;height:6px;
  background:var(--green);border-radius:50%;
  animation:blink 2s infinite;
}
.modal-close{
  background:none;border:none;cursor:none;
  width:32px;height:32px;border-radius:50%;
  color:var(--text-3);font-size:1.4rem;line-height:1;
  display:flex;align-items:center;justify-content:center;
  transition:background .2s,color .2s;
}
.modal-close:hover{background:var(--line);color:var(--text)}

.modal-ctx{
  padding:9px 26px;
  background:rgba(201,168,76,.06);
  border-bottom:1px solid var(--line);
  font-size:.72rem;color:var(--text-3);
  flex-shrink:0;
}
.modal-ctx strong{color:var(--gold)}

.chat-w{
  flex:1;overflow-y:auto;
  padding:18px 26px;
  display:flex;flex-direction:column;gap:12px;
  min-height:260px;
}
.chat-w::-webkit-scrollbar{width:3px}
.chat-w::-webkit-scrollbar-track{background:transparent}
.chat-w::-webkit-scrollbar-thumb{background:var(--line);border-radius:2px}

.cmsg{max-width:88%;animation:fadeM .3s ease}
@keyframes fadeM{from{opacity:0;transform:translateY(6px)}to{opacity:1;transform:none}}
.cmsg.u{align-self:flex-end}
.cmsg.a{align-self:flex-start}

.cbubble{
  padding:11px 15px;border-radius:3px;
  font-size:.875rem;line-height:1.65;
}
.cmsg.u .cbubble{
  background:linear-gradient(135deg,var(--gold),var(--gold-2));
  color:var(--bg);border-bottom-right-radius:0;
}
.cmsg.a .cbubble{
  background:var(--bg-2);color:var(--text-2);
  border:1px solid var(--line);border-bottom-left-radius:0;
}
.ctime{
  font-size:.62rem;color:var(--text-3);
  margin-top:4px;text-align:right;
}
.cmsg.a .ctime{text-align:left}

.typing{
  display:flex;gap:4px;align-items:center;
  padding:11px 15px;
  background:var(--bg-2);border:1px solid var(--line);
  border-radius:3px;border-bottom-left-radius:0;
  align-self:flex-start;width:fit-content;
}
.tdot{
  width:7px;height:7px;background:var(--text-3);
  border-radius:50%;animation:tb 1.2s infinite;
}
.tdot:nth-child(2){animation-delay:.2s}
.tdot:nth-child(3){animation-delay:.4s}

.chat-sugg{
  padding:8px 26px 0;
  display:flex;gap:7px;flex-wrap:wrap;flex-shrink:0;
}
.csugg{
  background:none;
  border:1px solid var(--line);border-radius:20px;
  padding:5px 13px;font-size:.73rem;
  color:var(--text-3);cursor:none;
  font-family:'Outfit',sans-serif;
  transition:border-color .2s,color .2s;
}
.csugg:hover{border-color:var(--gold-line);color:var(--gold)}

.chat-inp{
  padding:14px 26px 18px;
  border-top:1px solid var(--line);
  display:flex;gap:10px;align-items:flex-end;
  flex-shrink:0;
}
textarea.ci{
  flex:1;background:var(--bg-2);
  border:1px solid var(--line);border-radius:3px;
  padding:10px 14px;font-family:'Outfit',sans-serif;
  font-size:.875rem;color:var(--text);
  resize:none;height:44px;max-height:100px;
  outline:none;transition:border-color .2s;
}
textarea.ci:focus{border-color:var(--gold-line)}
textarea.ci::placeholder{color:var(--text-3)}

.csend{
  width:44px;height:44px;flex-shrink:0;
  background:linear-gradient(135deg,var(--gold),var(--gold-2));
  border:none;border-radius:3px;
  color:var(--bg);cursor:none;
  display:flex;align-items:center;justify-content:center;
  transition:opacity .2s,transform .15s;
}
.csend:hover{opacity:.88;transform:scale(1.04)}
.csend svg{width:15px;height:15px;stroke:currentColor;fill:none;stroke-width:2}

/* ───────── KEYFRAMES ───────── */
@keyframes aUp{from{opacity:0;transform:translateY(20px)}to{opacity:1;transform:none}}
@keyframes spin{from{transform:translate(-50%,-50%) rotate(0deg)}to{transform:translate(-50%,-50%) rotate(360deg)}}
@keyframes blink{0%,100%{opacity:1}50%{opacity:.3}}
@keyframes tb{0%,80%,100%{transform:translateY(0);opacity:.4}40%{transform:translateY(-7px);opacity:1}}

/* ───────── RESPONSIVE ───────── */
@media(max-width:1100px){.ag-grid{grid-template-columns:repeat(3,1fr)}}
@media(max-width:860px){
  nav{padding:0 24px}
  .nav-links{display:none}
  .hero{padding:100px 24px 72px}
  .hero-stats{gap:28px}
  .section{padding:72px 24px}
  .ag-grid{grid-template-columns:repeat(2,1fr)}
  .brand-layout{grid-template-columns:1fr}
  .brand-vis{height:300px}
  .feat-grid{grid-template-columns:1fr}
  .testi-grid{grid-template-columns:1fr}
  .ft-top{grid-template-columns:1fr 1fr;gap:32px}
  .ft-bottom{flex-direction:column;gap:12px}
  #cur-dot,#cur-ring{display:none}
  body{cursor:auto}
  a,button{cursor:pointer}
}
@media(max-width:540px){
  .ag-grid{grid-template-columns:1fr}
  .hero-stats{flex-direction:column;gap:20px}
  .cta-block{padding:48px 28px}
}
</style>
</head>
<body>

<!-- Canvas particles -->
<canvas id="starCanvas"></canvas>

<!-- Cursors -->
<div id="cur-ring"></div>
<div id="cur-dot"></div>

<!-- ═══════════════ NAV ═══════════════ -->
<nav id="nav">
  <a href="#" class="logo">Admin<span>Master</span></a>
  <ul class="nav-links">
    <li><a href="#agentes">Agentes</a></li>
    <li><a href="#memoria">Memoria</a></li>
    <li><a href="#casos">Análisis</a></li>
    <li><a href="#testimonios">Casos</a></li>
    <button class="nav-badge" onclick="openModal('publicidad')">Empezar Ahora</button>
  </ul>
</nav>

<!-- ═══════════════ HERO ═══════════════ -->
<section class="hero" id="inicio">
  <div class="hero-glow"></div>
  <div class="hero-left">
    <div class="hero-sup">Plataforma CIM · Inteligencia de Marca</div>
    <h1 class="hero-h">
      Domina la <em>Estrategia</em><br>
      de Marca con<br>
      <strong>IA Especializada</strong>
    </h1>
    <p class="hero-body">
      AdminMaster integra 12 agentes de inteligencia artificial que cubren
      todos los pilares de las Comunicaciones Integradas de Mercadeo.
      Una sola plataforma. Una voz de marca coherente. Resultados reales.
    </p>
    <div class="hero-btns">
      <a href="#agentes" class="btn-gold">Explorar los 12 Agentes</a>
      <a href="#casos" class="btn-outline">Ver Demo</a>
    </div>
    <div class="hero-stats">
      <div>
        <div class="hstat-n">12<span>+</span></div>
        <div class="hstat-l">Agentes IA</div>
      </div>
      <div>
        <div class="hstat-n">5<span>×</span></div>
        <div class="hstat-l">Pilares CIM</div>
      </div>
      <div>
        <div class="hstat-n">360<span>°</span></div>
        <div class="hstat-l">Visión de Marca</div>
      </div>
      <div>
        <div class="hstat-n">24<span>/7</span></div>
        <div class="hstat-l">Disponible</div>
      </div>
    </div>
  </div>
</section>

<!-- MARQUEE -->
<div class="marquee-wrap">
  <div class="marquee-track" id="marqueeTrack">
    <span class="marquee-item">Publicidad</span>
    <span class="marquee-item">Relaciones Públicas</span>
    <span class="marquee-item">Promoción de Ventas</span>
    <span class="marquee-item">Marketing Directo</span>
    <span class="marquee-item">Venta Personal</span>
    <span class="marquee-item">Estrategia Digital</span>
    <span class="marquee-item">Branding e Identidad</span>
    <span class="marquee-item">Marketing de Contenidos</span>
    <span class="marquee-item">E-Commerce</span>
    <span class="marquee-item">Análisis de Mercado</span>
    <span class="marquee-item">Experiencia del Cliente</span>
    <span class="marquee-item">Medición y Analytics</span>
    <span class="marquee-item">Publicidad</span>
    <span class="marquee-item">Relaciones Públicas</span>
    <span class="marquee-item">Promoción de Ventas</span>
    <span class="marquee-item">Marketing Directo</span>
    <span class="marquee-item">Venta Personal</span>
    <span class="marquee-item">Estrategia Digital</span>
    <span class="marquee-item">Branding e Identidad</span>
    <span class="marquee-item">Marketing de Contenidos</span>
    <span class="marquee-item">E-Commerce</span>
    <span class="marquee-item">Análisis de Mercado</span>
    <span class="marquee-item">Experiencia del Cliente</span>
    <span class="marquee-item">Medición y Analytics</span>
  </div>
</div>

<!-- ═══════════════ AGENTES ═══════════════ -->
<section class="section" id="agentes">
  <div class="rv">
    <div class="sec-label">12 Agentes Especializados</div>
    <h2 class="sec-h">Cada disciplina,<br>un <em>experto dedicado</em></h2>
    <p class="sec-p">Consulta en tiempo real con agentes entrenados en cada pilar de las CIM. Todos comparten la misma memoria de marca para garantizar coherencia total.</p>
  </div>

  <div class="ag-grid">

    <!-- 01 -->
    <div class="ag-card rv d1">
      <span class="ag-num">01</span>
      <div class="ag-icon"><svg viewBox="0 0 24 24"><polygon points="23 7 16 12 23 17 23 7"/><rect x="1" y="5" width="15" height="14" rx="2"/></svg></div>
      <div class="ag-cat">Pilar I · CIM</div>
      <div class="ag-name">Publicidad</div>
      <div class="ag-desc">Diseña campañas 360°, selecciona medios y genera briefs creativos con análisis de audiencias y presupuesto.</div>
      <div class="ag-pills"><span class="ag-pill">Campañas</span><span class="ag-pill">Medios</span><span class="ag-pill">Brief Creativo</span></div>
      <button class="ag-btn" onclick="openModal('publicidad')">Consultar <svg viewBox="0 0 24 24" stroke="currentColor" stroke-width="2"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg></button>
    </div>

    <!-- 02 -->
    <div class="ag-card rv d2">
      <span class="ag-num">02</span>
      <div class="ag-icon"><svg viewBox="0 0 24 24"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg></div>
      <div class="ag-cat">Pilar II · CIM</div>
      <div class="ag-name">Relaciones Públicas</div>
      <div class="ag-desc">Gestión de reputación, comunicados de prensa estratégicos y planes de manejo de crisis con voceros preparados.</div>
      <div class="ag-pills"><span class="ag-pill">Reputación</span><span class="ag-pill">Prensa</span><span class="ag-pill">Crisis</span></div>
      <button class="ag-btn" onclick="openModal('rrpp')">Consultar <svg viewBox="0 0 24 24" stroke="currentColor" stroke-width="2"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg></button>
    </div>

    <!-- 03 -->
    <div class="ag-card rv d3">
      <span class="ag-num">03</span>
      <div class="ag-icon"><svg viewBox="0 0 24 24"><polyline points="23 6 13.5 15.5 8.5 10.5 1 18"/><polyline points="17 6 23 6 23 12"/></svg></div>
      <div class="ag-cat">Pilar III · CIM</div>
      <div class="ag-name">Promoción de Ventas</div>
      <div class="ag-desc">Crea incentivos que convierten sin devaluar la marca. Loyalty programs, descuentos estratégicos y activaciones BTL.</div>
      <div class="ag-pills"><span class="ag-pill">Loyalty</span><span class="ag-pill">BTL</span><span class="ag-pill">ROI</span></div>
      <button class="ag-btn" onclick="openModal('promocion')">Consultar <svg viewBox="0 0 24 24" stroke="currentColor" stroke-width="2"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg></button>
    </div>

    <!-- 04 -->
    <div class="ag-card rv d4">
      <span class="ag-num">04</span>
      <div class="ag-icon"><svg viewBox="0 0 24 24"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg></div>
      <div class="ag-cat">Pilar IV · CIM</div>
      <div class="ag-name">Marketing Directo</div>
      <div class="ag-desc">Segmentación precisa, personalización y automatización de email, SMS y WhatsApp basados en comportamiento real.</div>
      <div class="ag-pills"><span class="ag-pill">Email</span><span class="ag-pill">Automatización</span><span class="ag-pill">CRM</span></div>
      <button class="ag-btn" onclick="openModal('directo')">Consultar <svg viewBox="0 0 24 24" stroke="currentColor" stroke-width="2"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg></button>
    </div>

    <!-- 05 -->
    <div class="ag-card rv d1">
      <span class="ag-num">05</span>
      <div class="ag-icon"><svg viewBox="0 0 24 24"><path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"/><circle cx="12" cy="7" r="4"/></svg></div>
      <div class="ag-cat">Pilar V · CIM</div>
      <div class="ag-name">Venta Personal</div>
      <div class="ag-desc">Coach de ventas con guiones, manejo de objeciones y simulaciones de negociación para equipos comerciales.</div>
      <div class="ag-pills"><span class="ag-pill">Pitch</span><span class="ag-pill">Objeciones</span><span class="ag-pill">Cierre</span></div>
      <button class="ag-btn" onclick="openModal('ventas')">Consultar <svg viewBox="0 0 24 24" stroke="currentColor" stroke-width="2"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg></button>
    </div>

    <!-- 06 -->
    <div class="ag-card rv d2">
      <span class="ag-num">06</span>
      <div class="ag-icon"><svg viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/><line x1="2" y1="12" x2="22" y2="12"/><path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"/></svg></div>
      <div class="ag-cat">Digital · Especial</div>
      <div class="ag-name">Estrategia Digital</div>
      <div class="ag-desc">Redes sociales, SEO y contenido interactivo integrados. Calendarios editoriales y análisis de tendencias en tiempo real.</div>
      <div class="ag-pills"><span class="ag-pill">Social Media</span><span class="ag-pill">SEO</span><span class="ag-pill">Contenido</span></div>
      <button class="ag-btn" onclick="openModal('digital')">Consultar <svg viewBox="0 0 24 24" stroke="currentColor" stroke-width="2"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg></button>
    </div>

    <!-- 07 -->
    <div class="ag-card rv d3">
      <span class="ag-num">07</span>
      <div class="ag-icon"><svg viewBox="0 0 24 24"><path d="M12 2L2 7l10 5 10-5-10-5z"/><path d="M2 17l10 5 10-5"/><path d="M2 12l10 5 10-5"/></svg></div>
      <div class="ag-cat">Identidad · Especial</div>
      <div class="ag-name">Branding e Identidad</div>
      <div class="ag-desc">Arquitectura de marca, naming, tono de voz y sistemas visuales que construyen percepción premium y diferenciación duradera.</div>
      <div class="ag-pills"><span class="ag-pill">Naming</span><span class="ag-pill">Tono de Voz</span><span class="ag-pill">Visual</span></div>
      <button class="ag-btn" onclick="openModal('branding')">Consultar <svg viewBox="0 0 24 24" stroke="currentColor" stroke-width="2"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg></button>
    </div>

    <!-- 08 -->
    <div class="ag-card rv d4">
      <span class="ag-num">08</span>
      <div class="ag-icon"><svg viewBox="0 0 24 24"><path d="M12 20h9"/><path d="M16.5 3.5a2.121 2.121 0 0 1 3 3L7 19l-4 1 1-4L16.5 3.5z"/></svg></div>
      <div class="ag-cat">Contenidos · Especial</div>
      <div class="ag-name">Marketing de Contenidos</div>
      <div class="ag-desc">Estrategia de contenido, storytelling de marca, blogs, videos y podcasts alineados al customer journey completo.</div>
      <div class="ag-pills"><span class="ag-pill">Storytelling</span><span class="ag-pill">Blog</span><span class="ag-pill">Video</span></div>
      <button class="ag-btn" onclick="openModal('contenidos')">Consultar <svg viewBox="0 0 24 24" stroke="currentColor" stroke-width="2"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg></button>
    </div>

    <!-- 09 -->
    <div class="ag-card rv d1">
      <span class="ag-num">09</span>
      <div class="ag-icon"><svg viewBox="0 0 24 24"><circle cx="9" cy="21" r="1"/><circle cx="20" cy="21" r="1"/><path d="M1 1h4l2.68 13.39a2 2 0 0 0 2 1.61h9.72a2 2 0 0 0 2-1.61L23 6H6"/></svg></div>
      <div class="ag-cat">Digital · Especial</div>
      <div class="ag-name">E-Commerce</div>
      <div class="ag-desc">Optimización de tiendas online, UX de conversión, estrategias de carrito abandonado y growth hacking para ventas digitales.</div>
      <div class="ag-pills"><span class="ag-pill">Conversión</span><span class="ag-pill">UX</span><span class="ag-pill">Growth</span></div>
      <button class="ag-btn" onclick="openModal('ecommerce')">Consultar <svg viewBox="0 0 24 24" stroke="currentColor" stroke-width="2"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg></button>
    </div>

    <!-- 10 -->
    <div class="ag-card rv d2">
      <span class="ag-num">10</span>
      <div class="ag-icon"><svg viewBox="0 0 24 24"><line x1="18" y1="20" x2="18" y2="10"/><line x1="12" y1="20" x2="12" y2="4"/><line x1="6" y1="20" x2="6" y2="14"/></svg></div>
      <div class="ag-cat">Inteligencia · Especial</div>
      <div class="ag-name">Análisis de Mercado</div>
      <div class="ag-desc">Interpreta datos de consumidores, tendencias de sector y benchmarks competitivos. Insights accionables basados en datos reales.</div>
      <div class="ag-pills"><span class="ag-pill">Datos</span><span class="ag-pill">Tendencias</span><span class="ag-pill">Benchmark</span></div>
      <button class="ag-btn" onclick="openModal('analisis')">Consultar <svg viewBox="0 0 24 24" stroke="currentColor" stroke-width="2"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg></button>
    </div>

    <!-- 11 -->
    <div class="ag-card rv d3">
      <span class="ag-num">11</span>
      <div class="ag-icon"><svg viewBox="0 0 24 24"><path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"/></svg></div>
      <div class="ag-cat">Experiencia · Especial</div>
      <div class="ag-name">Experiencia del Cliente</div>
      <div class="ag-desc">Mapeo del customer journey, diseño de touchpoints, NPS, retención y estrategias de fidelización basadas en emociones y datos.</div>
      <div class="ag-pills"><span class="ag-pill">Journey</span><span class="ag-pill">NPS</span><span class="ag-pill">Fidelización</span></div>
      <button class="ag-btn" onclick="openModal('cx')">Consultar <svg viewBox="0 0 24 24" stroke="currentColor" stroke-width="2"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg></button>
    </div>

    <!-- 12 -->
    <div class="ag-card rv d4">
      <span class="ag-num">12</span>
      <div class="ag-icon"><svg viewBox="0 0 24 24"><rect x="2" y="3" width="20" height="14" rx="2" ry="2"/><line x1="8" y1="21" x2="16" y2="21"/><line x1="12" y1="17" x2="12" y2="21"/></svg></div>
      <div class="ag-cat">Performance · Especial</div>
      <div class="ag-name">Medición y Analytics</div>
      <div class="ag-desc">KPIs, dashboards, atribución multicanal y reportes de ROI. Transforma datos en decisiones estratégicas con claridad meridiana.</div>
      <div class="ag-pills"><span class="ag-pill">KPIs</span><span class="ag-pill">ROI</span><span class="ag-pill">Dashboard</span></div>
      <button class="ag-btn" onclick="openModal('analytics')">Consultar <svg viewBox="0 0 24 24" stroke="currentColor" stroke-width="2"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg></button>
    </div>

  </div>
</section>

<!-- ═══════════════ BRAND MEMORY ═══════════════ -->
<section class="section dark" id="memoria">
  <div class="brand-layout">
    <div class="rv">
      <div class="sec-label">Memoria Centralizada</div>
      <h2 class="sec-h">Un solo <em>ADN</em>,<br>doce voces alineadas</h2>
      <p class="sec-p">Todos los agentes comparten una memoria de marca unificada. Las recomendaciones de publicidad nunca contradicen las de RR.PP. porque todos hablan desde el mismo núcleo estratégico.</p>
      <div class="brand-list">
        <div class="brand-item"><div class="bi-dot"></div><div class="bi-info"><div class="bi-name">Core de Marca</div><div class="bi-role">Propósito · Valores · Promesa · Personalidad</div></div><span class="bi-tag">Activo</span></div>
        <div class="brand-item"><div class="bi-dot"></div><div class="bi-info"><div class="bi-name">Sistema de Mensajes</div><div class="bi-role">Tono de voz · Key messages · Vocabulary</div></div><span class="bi-tag">Activo</span></div>
        <div class="brand-item"><div class="bi-dot busy"></div><div class="bi-info"><div class="bi-name">Contexto Competitivo</div><div class="bi-role">Benchmarks · Diferenciadores · Posicionamiento</div></div><span class="bi-tag">Sync</span></div>
        <div class="brand-item"><div class="bi-dot"></div><div class="bi-info"><div class="bi-name">Historial Estratégico</div><div class="bi-role">Decisiones pasadas · Aprendizajes · Restricciones</div></div><span class="bi-tag">Activo</span></div>
      </div>
    </div>
    <div class="rv d3">
      <div class="brand-vis">
        <div class="orbit-ring or-1"></div>
        <div class="orbit-ring or-2"></div>
        <div class="hex-container">
          <div class="hex hex-center">
            <svg viewBox="0 0 24 24"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/></svg>
          </div>
          <div class="hex hex-orbit ho-1"><svg viewBox="0 0 24 24"><polygon points="23 7 16 12 23 17 23 7"/><rect x="1" y="5" width="15" height="14" rx="2"/></svg></div>
          <div class="hex hex-orbit ho-2"><svg viewBox="0 0 24 24"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/></svg></div>
          <div class="hex hex-orbit ho-3"><svg viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/><line x1="2" y1="12" x2="22" y2="12"/></svg></div>
          <div class="hex hex-orbit ho-4"><svg viewBox="0 0 24 24"><line x1="18" y1="20" x2="18" y2="10"/><line x1="12" y1="20" x2="12" y2="4"/><line x1="6" y1="20" x2="6" y2="14"/></svg></div>
          <div class="hex hex-orbit ho-5"><svg viewBox="0 0 24 24"><path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"/></svg></div>
          <div class="hex hex-orbit ho-6"><svg viewBox="0 0 24 24"><path d="M12 20h9"/><path d="M16.5 3.5a2.121 2.121 0 0 1 3 3L7 19l-4 1 1-4L16.5 3.5z"/></svg></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ═══════════════ ANÁLISIS ═══════════════ -->
<section class="section" id="casos">
  <div class="rv">
    <div class="sec-label">Análisis de Casos Reales</div>
    <h2 class="sec-h">Sube tu plan de negocio,<br>recibe <em>retroalimentación</em> integrada</h2>
    <p class="sec-p">Los 12 agentes analizan tus estados financieros, planes de marketing o decks de presentación y entregan un diagnóstico estratégico completo basado en indicadores de rentabilidad.</p>
  </div>
  <div class="rv d1">
    <div class="upload-box" onclick="document.getElementById('fileIn').click()">
      <input type="file" id="fileIn" accept=".pdf,.xlsx,.csv,.docx,.pptx" style="display:none" onchange="handleFile(event)">
      <div class="upload-ico"><svg viewBox="0 0 24 24"><polyline points="16 16 12 12 8 16"/><line x1="12" y1="12" x2="12" y2="21"/><path d="M20.39 18.39A5 5 0 0 0 18 9h-1.26A8 8 0 1 0 3 16.3"/></svg></div>
      <div class="upload-t">Arrastra o selecciona tu documento</div>
      <p class="upload-d">PDF · Excel · CSV · Word · PowerPoint<br>Los agentes generarán un análisis CIM completo en segundos.</p>
      <div class="upload-chips">
        <span class="uchip">PDF</span><span class="uchip">Excel</span>
        <span class="uchip">CSV</span><span class="uchip">Word</span><span class="uchip">PPT</span>
      </div>
    </div>
  </div>
  <div class="feat-grid rv d2">
    <div class="feat-item">
      <div class="feat-n">01</div>
      <div class="feat-t">Análisis de Rentabilidad</div>
      <p class="feat-d">EBITDA, márgenes por línea de negocio y punto de equilibrio contrastados con benchmarks del sector.</p>
    </div>
    <div class="feat-item">
      <div class="feat-n">02</div>
      <div class="feat-t">Brechas de Comunicación</div>
      <p class="feat-d">Detecta inconsistencias entre el mensaje, el canal y el posicionamiento objetivo de tu marca.</p>
    </div>
    <div class="feat-item">
      <div class="feat-n">03</div>
      <div class="feat-t">Hoja de Ruta Integrada</div>
      <p class="feat-d">Plan priorizado por impacto/esfuerzo para los próximos 30, 60 y 90 días en cada pilar CIM.</p>
    </div>
  </div>
</section>

<!-- ═══════════════ TESTIMONIOS ═══════════════ -->
<section class="section darker" id="testimonios">
  <div class="rv">
    <div class="sec-label">Casos de Éxito</div>
    <h2 class="sec-h">Lo que dicen quienes<br>ya <em>dominan</em> las CIM</h2>
    <p class="sec-p">Emprendedores, directores de marketing y estudiantes que transformaron sus marcas con AdminMaster.</p>
  </div>
  <div class="testi-grid">
    <div class="testi-card rv d1">
      <div class="testi-stars">★★★★★</div>
      <div class="testi-q">"El Agente de Branding redefinió por completo nuestro tono de voz. En tres semanas nuestra tasa de engagement subió un 47%."</div>
      <div class="testi-divider"></div>
      <div class="testi-author">
        <div class="testi-avatar">V</div>
        <div><div class="testi-nm">Valentina Ríos</div><div class="testi-role">Fundadora · Studio Valr, Bogotá</div></div>
      </div>
    </div>
    <div class="testi-card rv d2">
      <div class="testi-stars">★★★★★</div>
      <div class="testi-q">"Jamás imaginé que un agente de IA pudiera entender tan bien la lógica de una negociación B2B. Mi equipo de ventas creció su tasa de cierre en un 32%."</div>
      <div class="testi-divider"></div>
      <div class="testi-author">
        <div class="testi-avatar">C</div>
        <div><div class="testi-nm">Carlos Mendoza</div><div class="testi-role">Director Comercial · InnoTech SAS</div></div>
      </div>
    </div>
    <div class="testi-card rv d3">
      <div class="testi-stars">★★★★★</div>
      <div class="testi-q">"Como estudiante de mercadeo fue como tener un mentor senior disponible 24/7. Presenté mi proyecto final con confianza total."</div>
      <div class="testi-divider"></div>
      <div class="testi-author">
        <div class="testi-avatar">S</div>
        <div><div class="testi-nm">Sara López</div><div class="testi-role">Estudiante · Universidad de los Andes</div></div>
      </div>
    </div>
  </div>
</section>

<!-- ═══════════════ CTA ═══════════════ -->
<section class="section" id="cta">
  <div class="cta-block rv">
    <div class="sec-label" style="justify-content:center">Comienza Hoy</div>
    <h2 class="cta-h">¿Listo para una marca<br><em>verdaderamente</em> integrada?</h2>
    <p class="cta-p">12 agentes especializados. Una memoria de marca compartida. Resultados coherentes en todos los canales. Sin contradicciones.</p>
    <div style="display:flex;gap:14px;justify-content:center">
      <button class="btn-gold" onclick="openModal('publicidad')">Hablar con un Agente</button>
      <a href="#agentes" class="btn-outline">Ver todos los Agentes</a>
    </div>
  </div>
</section>

<!-- ═══════════════ FOOTER ═══════════════ -->
<footer>
  <div class="ft-top">
    <div>
      <div class="ft-brand">Admin<span>Master</span></div>
      <p class="ft-tag">Plataforma educativa y profesional de Comunicaciones Integradas de Mercadeo con Inteligencia Artificial.</p>
    </div>
    <div class="ft-col">
      <h4>Agentes CIM</h4>
      <ul>
        <li><a href="#">Publicidad</a></li>
        <li><a href="#">Relaciones Públicas</a></li>
        <li><a href="#">Promoción de Ventas</a></li>
        <li><a href="#">Marketing Directo</a></li>
        <li><a href="#">Venta Personal</a></li>
      </ul>
    </div>
    <div class="ft-col">
      <h4>Agentes Especiales</h4>
      <ul>
        <li><a href="#">Estrategia Digital</a></li>
        <li><a href="#">Branding</a></li>
        <li><a href="#">Contenidos</a></li>
        <li><a href="#">E-Commerce</a></li>
        <li><a href="#">Analytics</a></li>
      </ul>
    </div>
    <div class="ft-col">
      <h4>Plataforma</h4>
      <ul>
        <li><a href="#">Memoria de Marca</a></li>
        <li><a href="#">Análisis de Casos</a></li>
        <li><a href="#">Recursos CIM</a></li>
        <li><a href="#">Contacto</a></li>
      </ul>
    </div>
  </div>
  <div class="ft-bottom">
    <div class="ft-copy">© 2025 AdminMaster. Todos los derechos reservados.</div>
    <div class="ft-legal">
      <a href="#">Privacidad</a>
      <a href="#">Términos</a>
      <a href="#">Cookies</a>
    </div>
  </div>
</footer>

<!-- ═══════════════ MODAL ═══════════════ -->
<div class="overlay" id="overlay">
  <div class="modal">
    <div class="modal-hd">
      <div style="display:flex;align-items:center;gap:14px">
        <div class="modal-av" id="mAv"><svg viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/></svg></div>
        <div>
          <div class="modal-ag-name" id="mName">Agente</div>
          <div class="modal-status">Activo · Memoria de marca cargada</div>
        </div>
      </div>
      <button class="modal-close" onclick="closeModal()">×</button>
    </div>
    <div class="modal-ctx" id="mCtx"><strong>Memoria de marca activa</strong> · 12 agentes sincronizados · Coherencia garantizada</div>
    <div class="chat-w" id="chatW"></div>
    <div class="chat-sugg" id="chatS"></div>
    <div class="chat-inp">
      <textarea class="ci" id="ci" placeholder="Escribe tu consulta estratégica…" onkeydown="hKey(event)" oninput="aResize(this)"></textarea>
      <button class="csend" onclick="send()">
        <svg viewBox="0 0 24 24"><line x1="22" y1="2" x2="11" y2="13"/><polygon points="22 2 15 22 11 13 2 9 22 2"/></svg>
      </button>
    </div>
  </div>
</div>

<!-- ═══════════════ SCRIPTS ═══════════════ -->
<script>
/* ── CANVAS PARTICLES ── */
const cv=document.getElementById('starCanvas');
const ctx2=cv.getContext('2d');
let stars=[];
function rsz(){cv.width=innerWidth;cv.height=innerHeight}
rsz();window.addEventListener('resize',rsz);
function mkStars(){
  stars=[];
  for(let i=0;i<120;i++){
    stars.push({
      x:Math.random()*cv.width,y:Math.random()*cv.height,
      r:Math.random()*1.2+.2,
      a:Math.random(),da:(Math.random()-.5)*.004,
      spd:Math.random()*.15+.05
    });
  }
}
mkStars();
function drawStars(){
  ctx2.clearRect(0,0,cv.width,cv.height);
  stars.forEach(s=>{
    s.a+=s.da;
    if(s.a<=0||s.a>=1)s.da*=-1;
    s.y-=s.spd;if(s.y<0)s.y=cv.height;
    ctx2.beginPath();
    ctx2.arc(s.x,s.y,s.r,0,Math.PI*2);
    ctx2.fillStyle=`rgba(201,168,76,${s.a*.5})`;
    ctx2.fill();
  });
  requestAnimationFrame(drawStars);
}
drawStars();

/* ── CURSOR ── */
const dot=document.getElementById('cur-dot');
const ring=document.getElementById('cur-ring');
let mx=0,my=0,rx=0,ry=0;
document.addEventListener('mousemove',e=>{mx=e.clientX;my=e.clientY});
(function animC(){
  if(dot){dot.style.left=mx+'px';dot.style.top=my+'px'}
  rx+=(mx-rx)*.12;ry+=(my-ry)*.12;
  if(ring){ring.style.left=rx+'px';ring.style.top=ry+'px'}
  requestAnimationFrame(animC);
})();

/* ── NAV SCROLL ── */
window.addEventListener('scroll',()=>{
  document.getElementById('nav').classList.toggle('sc',scrollY>40);
});

/* ── REVEAL ── */
const ro=new IntersectionObserver(e=>{
  e.forEach(x=>{if(x.isIntersecting)x.target.classList.add('on')});
},{threshold:.08});
document.querySelectorAll('.rv').forEach(el=>ro.observe(el));

/* ── AGENTS ── */
const AG={
  publicidad:{
    name:'Agente de Publicidad',
    icon:'<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><polygon points="23 7 16 12 23 17 23 7"/><rect x="1" y="5" width="15" height="14" rx="2"/></svg>',
    sys:`Eres el Agente de Publicidad de AdminMaster, plataforma educativa de CIM de élite.
Eres un Director Creativo y Estratega de Medios con 20 años de experiencia en agencias multinacionales.
Diseñas campañas 360°, defines mix de medios, redactas briefs creativos y estructuras de mensajes clave.
Compartes una memoria de marca unificada con 11 agentes especializados para garantizar coherencia total.
Responde siempre en español, con pensamiento estratégico, datos de referencia cuando sea útil y ejemplos concretos. Máximo 200 palabras. Usa viñetas cuando organices información.`,
    hi:'Hola, soy tu Agente de Publicidad. Diseño campañas que conectan con audiencias reales. ¿Qué marca o proyecto quieres activar hoy?',
    qs:['¿Cómo defino mi mix de medios?','Crea un brief creativo para mi producto','¿Qué KPIs medir en mi campaña?','Diferencias entre ATL, BTL y TTL']
  },
  rrpp:{
    name:'Agente de Relaciones Públicas',
    icon:'<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg>',
    sys:`Eres el Agente de Relaciones Públicas de AdminMaster. Experto en gestión de reputación, comunicados de prensa, media training, manejo de crisis y relaciones con stakeholders. Coordinado con los otros 11 agentes CIM para garantizar coherencia de mensaje. Responde en español, profesional y estratégico. Máximo 200 palabras.`,
    hi:'Hola, soy el Agente de RR.PP. Mi trabajo es construir y proteger la reputación de tu marca. ¿Hay algún tema de imagen o comunicación que necesitas resolver?',
    qs:['Redacta un comunicado de prensa','Plan de manejo de crisis','¿Cómo identificar voceros de marca?','Estrategia de relaciones con medios']
  },
  promocion:{
    name:'Agente de Promoción de Ventas',
    icon:'<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><polyline points="23 6 13.5 15.5 8.5 10.5 1 18"/><polyline points="17 6 23 6 23 12"/></svg>',
    sys:`Eres el Agente de Promoción de Ventas de AdminMaster. Especialista en mecánicas de incentivo, loyalty programs, concursos, activaciones BTL y estrategias de conversión sin erosionar el valor de marca. Trabajas en coordinación con los otros 11 agentes CIM. Responde en español con lógica financiera y creatividad comercial. Máximo 200 palabras.`,
    hi:'¡Bienvenido! Soy el Agente de Promoción de Ventas. Diseño incentivos que venden más sin comprometer el valor percibido de tu marca. ¿Qué objetivo de conversión quieres lograr?',
    qs:['Diseña un programa de lealtad','¿Cómo descuento sin dañar mi marca?','Activaciones BTL para retail','Mecánica de concurso en redes']
  },
  directo:{
    name:'Agente de Marketing Directo',
    icon:'<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>',
    sys:`Eres el Agente de Marketing Directo de AdminMaster. Experto en segmentación, automatización de marketing, CRM, email marketing, WhatsApp Business y funnels de conversión. Coordinado con los 11 agentes para coherencia de marca. Responde en español con enfoque en métricas y resultados. Máximo 200 palabras.`,
    hi:'Hola, soy el Agente de Marketing Directo. Diseño comunicaciones uno a uno que generan acción inmediata. ¿Qué canal o flujo de automatización quieres optimizar?',
    qs:['Secuencia de bienvenida por email','Segmentación de base de clientes','¿Cómo mido mi tasa de conversión?','Flujo de WhatsApp para leads']
  },
  ventas:{
    name:'Agente de Venta Personal',
    icon:'<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"/><circle cx="12" cy="7" r="4"/></svg>',
    sys:`Eres el Agente de Venta Personal de AdminMaster. Coach de ventas B2B y B2C con expertise en metodologías SPIN, Challenger Sale y consultative selling. Diseñas guiones, entrenas en manejo de objeciones y simulas escenarios de negociación. Coordinado con los 11 agentes CIM. Responde en español, directo y práctico. Máximo 200 palabras.`,
    hi:'¡Hola! Soy el Agente de Venta Personal. Puedo ayudarte a diseñar tu proceso comercial, mejorar tu pitch o practicar una negociación difícil. ¿Cómo podemos mejorar tus ventas hoy?',
    qs:['Simula una objeción de precio','Crea mi guion de ventas','Técnicas de cierre efectivas','¿Cómo hacer seguimiento sin ser invasivo?']
  },
  digital:{
    name:'Agente de Estrategia Digital',
    icon:'<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="12" cy="12" r="10"/><line x1="2" y1="12" x2="22" y2="12"/><path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"/></svg>',
    sys:`Eres el Agente de Estrategia Digital de AdminMaster. Experto en social media marketing, SEO, SEM, marketing de influencers, contenido para todas las plataformas y estrategia digital integrada. Analizas tendencias actuales y creas planes editoriales coherentes con el ADN de marca. Coordinado con los 11 agentes CIM. Responde en español con datos y ejemplos. Máximo 200 palabras.`,
    hi:'¡Hola! Soy el Agente Digital. Mi especialidad es construir presencia online coherente y con resultados. ¿Con qué plataforma o estrategia digital empezamos?',
    qs:['Calendario editorial mensual','¿Qué redes usar para mi marca?','Estrategia de influencer marketing','Cómo mejorar mi SEO orgánico']
  },
  branding:{
    name:'Agente de Branding e Identidad',
    icon:'<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M12 2L2 7l10 5 10-5-10-5z"/><path d="M2 17l10 5 10-5"/><path d="M2 12l10 5 10-5"/></svg>',
    sys:`Eres el Agente de Branding e Identidad de AdminMaster. Brand strategist con expertise en arquitectura de marca, brand positioning, naming, tono de voz, sistemas visuales y brand equity. Ayudas a construir marcas que generan valor premium y diferenciación duradera. Coordinado con los 11 agentes CIM. Responde en español con frameworks de marca reconocidos. Máximo 200 palabras.`,
    hi:'Hola, soy el Agente de Branding. Construyo marcas que perduran. Desde el propósito hasta la identidad visual, todo conectado. ¿Qué aspecto de tu marca necesita más claridad hoy?',
    qs:['Define el propósito de mi marca','¿Cómo crear un tono de voz único?','Arquitectura de marca para mi empresa','¿Qué hace a una marca premium?']
  },
  contenidos:{
    name:'Agente de Marketing de Contenidos',
    icon:'<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M12 20h9"/><path d="M16.5 3.5a2.121 2.121 0 0 1 3 3L7 19l-4 1 1-4L16.5 3.5z"/></svg>',
    sys:`Eres el Agente de Marketing de Contenidos de AdminMaster. Especialista en content strategy, storytelling de marca, SEO de contenidos, blogs, videos, podcasts y newsletters. Creas ecosistemas de contenido que atraen, educan y convierten audiencias a lo largo de todo el customer journey. Coordinado con los 11 agentes CIM. Responde en español con estrategias accionables. Máximo 200 palabras.`,
    hi:'¡Hola! Soy el Agente de Contenidos. El buen contenido no se crea, se diseña estratégicamente. ¿Qué tipo de contenido quieres construir para tu marca?',
    qs:['Estrategia de contenido B2C','Cómo estructurar un blog de marca','Ideas de contenido para LinkedIn','¿Podcast o video: qué elegir?']
  },
  ecommerce:{
    name:'Agente de E-Commerce',
    icon:'<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="9" cy="21" r="1"/><circle cx="20" cy="21" r="1"/><path d="M1 1h4l2.68 13.39a2 2 0 0 0 2 1.61h9.72a2 2 0 0 0 2-1.61L23 6H6"/></svg>',
    sys:`Eres el Agente de E-Commerce de AdminMaster. Experto en optimización de tiendas online, UX de conversión, estrategias de recuperación de carrito abandonado, product listing optimization, marketplace strategy y growth hacking para ventas digitales. Trabajas con la memoria de marca de los 11 agentes CIM. Responde en español con métricas y tácticas específicas. Máximo 200 palabras.`,
    hi:'¡Hola! Soy el Agente de E-Commerce. Optimizo cada punto del camino desde que alguien ve tu producto hasta que paga. ¿Cuál es el mayor reto de conversión en tu tienda?',
    qs:['Cómo reducir el carrito abandonado','Optimización de fichas de producto','Estrategia de marketplaces','¿Shopify vs WooCommerce vs VTEX?']
  },
  analisis:{
    name:'Agente de Análisis de Mercado',
    icon:'<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><line x1="18" y1="20" x2="18" y2="10"/><line x1="12" y1="20" x2="12" y2="4"/><line x1="6" y1="20" x2="6" y2="14"/></svg>',
    sys:`Eres el Agente de Análisis de Mercado de AdminMaster. Market research strategist experto en análisis competitivo, segmentación de consumidores, tendencias de industria, análisis de datos y business intelligence para tomar decisiones de marca fundamentadas. Compartis memoria con los 11 agentes CIM. Responde en español con frameworks analíticos y datos de referencia. Máximo 200 palabras.`,
    hi:'Hola, soy el Agente de Análisis de Mercado. Los datos son mi idioma nativo. ¿Qué segmento, competidor o tendencia quieres entender mejor hoy?',
    qs:['¿Cómo analizar a mi competencia?','Frameworks de segmentación de mercado','Tendencias de consumo 2025','¿Qué es el análisis PESTEL?']
  },
  cx:{
    name:'Agente de Experiencia del Cliente',
    icon:'<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"/></svg>',
    sys:`Eres el Agente de Experiencia del Cliente (CX) de AdminMaster. Customer experience designer experto en mapeo de customer journey, diseño de touchpoints, métricas de satisfacción (NPS, CSAT, CES), estrategias de retención y programas de fidelización emocional. Coordinado con los 11 agentes CIM. Responde en español con metodologías CX reconocidas. Máximo 200 palabras.`,
    hi:'¡Hola! Soy el Agente de CX. La experiencia del cliente es el verdadero diferenciador de las grandes marcas. ¿Qué momento del viaje de tu cliente quieres mejorar?',
    qs:['¿Cómo mapeo el customer journey?','Estrategia para mejorar el NPS','¿Cómo retener clientes activos?','Diseño de programa de fidelización']
  },
  analytics:{
    name:'Agente de Medición y Analytics',
    icon:'<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="2" y="3" width="20" height="14" rx="2" ry="2"/><line x1="8" y1="21" x2="16" y2="21"/><line x1="12" y1="17" x2="12" y2="21"/></svg>',
    sys:`Eres el Agente de Medición y Analytics de AdminMaster. Performance marketing analyst con expertise en definición de KPIs, modelo de atribución multicanal, Google Analytics, reportes de ROI y construcción de dashboards estratégicos. Transforma datos en decisiones claras. Coordinado con los 11 agentes CIM. Responde en español con métricas específicas y frameworks de medición. Máximo 200 palabras.`,
    hi:'Hola, soy el Agente de Analytics. Sin medición, todo es opinión. ¿Qué estás midiendo hoy y qué decisiones quieres tomar con esos datos?',
    qs:['¿Qué KPIs debería medir?','Modelos de atribución multicanal','¿Cómo medir el ROI de mi contenido?','Dashboard esencial para marketing']
  }
};

let curAg=null,hist=[];

function openModal(key){
  curAg=key;hist=[];
  const ag=AG[key];
  document.getElementById('mName').textContent=ag.name;
  document.getElementById('mAv').innerHTML=ag.icon;
  const cw=document.getElementById('chatW');cw.innerHTML='';
  addMsg('a',ag.hi);
  const cs=document.getElementById('chatS');cs.innerHTML='';
  ag.qs.forEach(q=>{
    const b=document.createElement('button');b.className='csugg';b.textContent=q;
    b.onclick=()=>{document.getElementById('ci').value=q;send()};
    cs.appendChild(b);
  });
  document.getElementById('overlay').classList.add('open');
  document.body.style.overflow='hidden';
}

function closeModal(){
  document.getElementById('overlay').classList.remove('open');
  document.body.style.overflow='';
}
document.getElementById('overlay').addEventListener('click',e=>{
  if(e.target===e.currentTarget)closeModal();
});

function addMsg(role,txt){
  const cw=document.getElementById('chatW');
  const m=document.createElement('div');
  m.className='cmsg '+(role==='u'?'u':'a');
  const t=new Date().toLocaleTimeString('es-CO',{hour:'2-digit',minute:'2-digit'});
  m.innerHTML=`<div class="cbubble">${txt.replace(/\n/g,'<br>')}</div><div class="ctime">${t}</div>`;
  cw.appendChild(m);cw.scrollTop=cw.scrollHeight;
  if(role==='a')hist.push({role:'assistant',content:txt});
}

function showTyping(){
  const cw=document.getElementById('chatW');
  const t=document.createElement('div');
  t.className='typing';t.id='typ';
  t.innerHTML='<div class="tdot"></div><div class="tdot"></div><div class="tdot"></div>';
  cw.appendChild(t);cw.scrollTop=cw.scrollHeight;
}
function hideTyping(){const t=document.getElementById('typ');if(t)t.remove()}

async function send(){
  const inp=document.getElementById('ci');
  const txt=inp.value.trim();
  if(!txt||!curAg)return;
  inp.value='';inp.style.height='44px';
  addMsg('u',txt);hist.push({role:'user',content:txt});
  document.getElementById('chatS').innerHTML='';
  showTyping();
  try{
    const ag=AG[curAg];
    const res=await fetch('https://api.anthropic.com/v1/messages',{
      method:'POST',
      headers:{'Content-Type':'application/json'},
      body:JSON.stringify({
        model:'claude-sonnet-4-20250514',
        max_tokens:1000,
        system:ag.sys,
        messages:hist.filter(h=>h.role!=='assistant'||true)
      })
    });
    const data=await res.json();
    hideTyping();
    if(data.content&&data.content[0])addMsg('a',data.content[0].text);
    else addMsg('a','Ocurrió un error. Por favor intenta de nuevo.');
  }catch(e){
    hideTyping();
    addMsg('a','Error de conexión. Verifica que el backend esté configurado correctamente.');
  }
}

function hKey(e){if(e.key==='Enter'&&!e.shiftKey){e.preventDefault();send()}}
function aResize(el){el.style.height='44px';el.style.height=Math.min(el.scrollHeight,100)+'px'}

function handleFile(e){
  const f=e.target.files[0];if(!f)return;
  openModal('analisis');
  setTimeout(()=>{
    document.getElementById('ci').value=`Acabo de subir el archivo "${f.name}". Analízalo desde todos los pilares CIM y dame un diagnóstico estratégico completo con indicadores de rentabilidad y recomendaciones prioritarias.`;
    send();
  },700);
}
</script>
</body>
</html>
