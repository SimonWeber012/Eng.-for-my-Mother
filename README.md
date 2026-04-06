# Eng.-for-my-Mother
<!DOCTYPE html>
<html lang="cs">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>🚀 Angličtina pro Maminku</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Fredoka+One&family=Nunito:wght@400;600;700;800&display=swap');
 
*, *::before, *::after { margin:0; padding:0; box-sizing:border-box; }
 
:root {
  --space:  #0a0520;
  --space2: #12082e;
  --purple: #7c3aed;
  --violet: #a855f7;
  --pink:   #ec4899;
  --cyan:   #22d3ee;
  --green:  #10b981;
  --yellow: #fbbf24;
  --orange: #f97316;
  --red:    #ef4444;
  --white:  #f0e6ff;
  --gold:   #ffd700;
}
 
html, body { height:100%; overflow:hidden; }
 
body {
  background: var(--space);
  color: var(--white);
  font-family: 'Nunito', sans-serif;
  user-select: none;
}
 
/* ══ CANVAS BG ══ */
#starCanvas {
  position:fixed; inset:0; z-index:0; pointer-events:none;
}
 
/* ══ SCREENS ══ */
.screen {
  position: fixed; inset:0; z-index:10;
  display: flex; flex-direction:column;
  align-items:center; justify-content:center;
  padding:1.5rem;
  display:none;
}
.screen.active { display:flex; }
 
/* ══ HOME SCREEN ══ */
#homeScreen {
  background: radial-gradient(ellipse at 50% 30%, #1a0840 0%, #0a0520 70%);
  gap:1.5rem;
}
 
.home-title {
  font-family:'Fredoka One',cursive;
  font-size:clamp(2.2rem,6vw,4rem);
  text-align:center;
  line-height:1.1;
  background: linear-gradient(135deg, var(--cyan), var(--violet), var(--pink));
  -webkit-background-clip:text; -webkit-text-fill-color:transparent;
  filter: drop-shadow(0 0 30px rgba(168,85,247,.5));
}
 
.home-sub {
  font-size:1rem; color:rgba(240,230,255,.6); text-align:center;
}
 
.rocket-anim {
  font-size:5rem;
  animation: rocketFloat 3s ease-in-out infinite;
  filter: drop-shadow(0 0 20px rgba(251,191,36,.6));
}
@keyframes rocketFloat {
  0%,100%{transform:translateY(0) rotate(-5deg);}
  50%{transform:translateY(-18px) rotate(5deg);}
}
 
.mode-cards {
  display:flex; gap:1rem; flex-wrap:wrap; justify-content:center;
  max-width:700px;
}
 
.mode-card {
  background: rgba(124,58,237,.15);
  border:2px solid rgba(168,85,247,.3);
  border-radius:20px;
  padding:1.5rem 1.8rem;
  text-align:center;
  cursor:pointer;
  transition: all .3s;
  flex:1; min-width:180px; max-width:220px;
}
.mode-card:hover {
  background: rgba(124,58,237,.35);
  border-color:var(--violet);
  transform:translateY(-6px) scale(1.02);
  box-shadow:0 12px 40px rgba(168,85,247,.4);
}
.mode-card .mc-icon { font-size:2.8rem; margin-bottom:.6rem; display:block; }
.mode-card h3 { font-family:'Fredoka One',cursive; font-size:1.2rem; color:var(--white); margin-bottom:.3rem; }
.mode-card p  { font-size:.75rem; color:rgba(240,230,255,.55); line-height:1.5; }
 
.home-stars {
  font-size:.85rem; color:var(--gold);
  display:flex; align-items:center; gap:.4rem;
}
 
/* ══ SPACE SHIP GAME ══ */
#spaceScreen {
  background: radial-gradient(ellipse at 50% 0%, #1a0840 0%, #050215 60%);
  justify-content:flex-start; padding-top:0; gap:0;
}
 
.game-header {
  width:100%; max-width:700px;
  display:flex; justify-content:space-between; align-items:center;
  padding:1rem 1.5rem;
  background:rgba(0,0,0,.3);
  border-bottom:1px solid rgba(168,85,247,.2);
  flex-shrink:0;
}
.gh-left { display:flex; flex-direction:column; gap:.1rem; }
.gh-title { font-family:'Fredoka One',cursive; font-size:1.1rem; color:var(--cyan); }
.gh-sub   { font-size:.68rem; color:rgba(240,230,255,.5); }
 
.lives { display:flex; gap:.3rem; }
.life  { font-size:1.2rem; transition:all .3s; }
.life.lost { opacity:.2; filter:grayscale(1); }
 
.score-badge {
  background:rgba(251,191,36,.15);
  border:1px solid rgba(251,191,36,.3);
  border-radius:20px;
  padding:.3rem .8rem;
  font-family:'Fredoka One',cursive;
  font-size:.9rem;
  color:var(--gold);
}
 
/* ship scene */
.space-scene {
  flex:1; width:100%; max-width:700px;
  position:relative; overflow:hidden;
  display:flex; flex-direction:column;
  align-items:center; justify-content:center;
  gap:1rem;
  padding:1rem;
}
 
/* rocket ship SVG */
.ship-wrap {
  position:relative;
  animation:shipIdle 2s ease-in-out infinite;
}
@keyframes shipIdle {
  0%,100%{transform:translateY(0);}
  50%{transform:translateY(-8px);}
}
.ship-wrap.escape {
  animation:shipEscape 1.2s ease-in forwards;
}
@keyframes shipEscape {
  0%{transform:translateY(0) scale(1);}
  30%{transform:translateY(-20px) scale(1.1);}
  100%{transform:translateY(-200px) scale(0.2);opacity:0;}
}
.ship-wrap.shake {
  animation:shipShake .5s ease;
}
@keyframes shipShake {
  0%,100%{transform:translateX(0);}
  20%{transform:translateX(-10px);}
  40%{transform:translateX(10px);}
  60%{transform:translateX(-8px);}
  80%{transform:translateX(8px);}
}
 
/* word card */
.word-card {
  background: rgba(10,5,32,.8);
  border:2px solid rgba(34,211,238,.3);
  border-radius:20px;
  padding:1.2rem 2rem;
  text-align:center;
  width:100%; max-width:420px;
  box-shadow:0 0 40px rgba(34,211,238,.1);
}
.wc-english {
  font-family:'Fredoka One',cursive;
  font-size:clamp(2rem,5vw,3rem);
  color:var(--cyan);
  text-shadow:0 0 20px rgba(34,211,238,.5);
  margin-bottom:.2rem;
}
.wc-phonetic {
  font-size:.85rem;
  color:rgba(240,230,255,.5);
  font-style:italic;
  margin-bottom:.5rem;
}
.wc-hint {
  font-size:.75rem;
  color:rgba(240,230,255,.4);
}
 
/* answer options */
.answers {
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:.6rem;
  width:100%; max-width:420px;
}
 
.ans-btn {
  background: rgba(124,58,237,.2);
  border:2px solid rgba(168,85,247,.25);
  border-radius:14px;
  padding:.8rem;
  font-family:'Nunito',sans-serif;
  font-size:.9rem;
  font-weight:700;
  color:var(--white);
  cursor:pointer;
  transition:all .25s;
  text-align:center;
}
.ans-btn:hover:not(:disabled) {
  background:rgba(168,85,247,.35);
  border-color:var(--violet);
  transform:scale(1.03);
}
.ans-btn.correct {
  background:rgba(16,185,129,.3);
  border-color:var(--green);
  color:#6ee7b7;
  animation:popCorrect .4s ease;
}
.ans-btn.wrong {
  background:rgba(239,68,68,.2);
  border-color:var(--red);
  color:#fca5a5;
  animation:popWrong .4s ease;
}
@keyframes popCorrect { 0%{transform:scale(1);}50%{transform:scale(1.12);}100%{transform:scale(1);} }
@keyframes popWrong   { 0%,100%{transform:scale(1);}50%{transform:scale(.95);} }
 
.ans-btn:disabled { cursor:default; }
 
.feedback-bar {
  height:36px;
  display:flex; align-items:center; justify-content:center;
  font-size:.9rem; font-weight:700;
  gap:.5rem;
}
 
/* progress bar */
.progress-wrap {
  width:100%; max-width:420px;
  height:8px;
  background:rgba(255,255,255,.1);
  border-radius:4px;
  overflow:hidden;
}
.progress-fill {
  height:100%;
  background:linear-gradient(90deg,var(--cyan),var(--violet));
  border-radius:4px;
  transition:width .5s ease;
}
 
/* ══ PATH GAME ══ */
#pathScreen {
  background: radial-gradient(ellipse at 50% 100%, #0a2010 0%, #050a05 70%);
  justify-content:flex-start; padding-top:0; gap:0;
}
 
/* path canvas */
#pathCanvas {
  position:absolute; inset:0; z-index:1;
}
 
.path-ui {
  position:relative; z-index:10;
  width:100%; max-width:700px;
  display:flex; flex-direction:column;
  height:100%;
  pointer-events:none;
}
 
.path-ui > * { pointer-events:all; }
 
.path-header {
  display:flex; justify-content:space-between; align-items:center;
  padding:1rem 1.5rem;
  background:rgba(0,0,0,.4);
  border-bottom:1px solid rgba(16,185,129,.2);
}
.ph-title { font-family:'Fredoka One',cursive; font-size:1.1rem; color:var(--green); }
 
.path-content {
  flex:1;
  display:flex;
  flex-direction:column;
  align-items:center;
  justify-content:flex-end;
  padding:1rem;
  gap:.8rem;
}
 
/* sentence builder */
.sentence-display {
  width:100%; max-width:500px;
  background:rgba(0,0,0,.5);
  border:2px solid rgba(16,185,129,.3);
  border-radius:16px;
  padding:1rem 1.2rem;
  text-align:center;
  min-height:56px;
  display:flex; flex-wrap:wrap; gap:.4rem;
  align-items:center; justify-content:center;
}
.sent-word {
  background:rgba(16,185,129,.2);
  border:1px solid rgba(16,185,129,.4);
  border-radius:8px;
  padding:.25rem .65rem;
  font-size:.9rem;
  font-weight:700;
  color:#6ee7b7;
  cursor:pointer;
  transition:all .2s;
}
.sent-word:hover { background:rgba(239,68,68,.2); border-color:var(--red); color:#fca5a5; }
 
.sentence-hint {
  font-size:.72rem;
  color:rgba(240,230,255,.4);
  text-align:center;
}
 
.phrase-card {
  width:100%; max-width:500px;
  background:rgba(5,20,8,.7);
  border:2px solid rgba(16,185,129,.25);
  border-radius:16px;
  padding:1rem 1.5rem;
  text-align:center;
}
.pc-label  { font-size:.65rem; letter-spacing:.2em; text-transform:uppercase; color:rgba(16,185,129,.6); margin-bottom:.3rem; }
.pc-cz     { font-size:1.1rem; font-weight:800; color:var(--white); margin-bottom:.2rem; }
.pc-phonetic { font-size:.78rem; color:rgba(240,230,255,.4); font-style:italic; margin-bottom:.5rem; }
 
.word-bank {
  display:flex; flex-wrap:wrap; gap:.5rem;
  justify-content:center;
  width:100%; max-width:500px;
}
.wb-word {
  background:rgba(124,58,237,.25);
  border:2px solid rgba(168,85,247,.3);
  border-radius:10px;
  padding:.4rem .9rem;
  font-size:.88rem;
  font-weight:700;
  color:var(--white);
  cursor:pointer;
  transition:all .2s;
}
.wb-word:hover:not(.used) {
  background:rgba(168,85,247,.4);
  border-color:var(--violet);
  transform:scale(1.05);
}
.wb-word.used { opacity:.25; cursor:default; pointer-events:none; }
 
.path-check-btn {
  background:linear-gradient(135deg,var(--green),#059669);
  border:none;
  border-radius:14px;
  padding:.75rem 2.5rem;
  font-family:'Fredoka One',cursive;
  font-size:1.1rem;
  color:white;
  cursor:pointer;
  transition:all .25s;
  box-shadow:0 4px 20px rgba(16,185,129,.4);
}
.path-check-btn:hover { transform:translateY(-2px); box-shadow:0 8px 28px rgba(16,185,129,.5); }
 
/* ══ PHRASES GAME ══ */
#phrasesScreen {
  background: radial-gradient(ellipse at 30% 50%, #1a1000 0%, #080500 70%);
  justify-content:flex-start; padding-top:0; gap:0;
}
 
.phrase-match {
  flex:1; width:100%; max-width:700px;
  display:flex; flex-direction:column;
  overflow:hidden;
}
 
.match-area {
  flex:1;
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:.8rem;
  padding:1rem 1.5rem;
  overflow-y:auto;
  align-content:start;
}
 
.match-col h4 {
  font-family:'Fredoka One',cursive;
  font-size:.85rem;
  color:rgba(240,230,255,.5);
  text-align:center;
  margin-bottom:.5rem;
  letter-spacing:.1em;
  text-transform:uppercase;
}
 
.match-item {
  background:rgba(251,191,36,.1);
  border:2px solid rgba(251,191,36,.2);
  border-radius:12px;
  padding:.7rem .9rem;
  font-size:.88rem;
  font-weight:700;
  cursor:pointer;
  transition:all .25s;
  text-align:center;
  line-height:1.4;
}
.match-item:hover:not(.done):not(.wrong-flash) {
  background:rgba(251,191,36,.25);
  border-color:var(--yellow);
  transform:scale(1.03);
}
.match-item.selected {
  background:rgba(251,191,36,.3);
  border-color:var(--gold);
  color:var(--gold);
}
.match-item.done {
  background:rgba(16,185,129,.2);
  border-color:var(--green);
  color:#6ee7b7;
  cursor:default;
}
.match-item.wrong-flash {
  animation:wrongFlash .5s ease;
}
@keyframes wrongFlash {
  0%,100%{background:rgba(251,191,36,.1);}
  50%{background:rgba(239,68,68,.3);border-color:var(--red);}
}
 
/* ══ RESULT SCREEN ══ */
#resultScreen {
  background: radial-gradient(ellipse at 50% 30%, #1a0840 0%, #050215 70%);
  gap:1.5rem; text-align:center;
}
 
.result-icon  { font-size:5rem; animation:rocketFloat 2s ease-in-out infinite; }
.result-title {
  font-family:'Fredoka One',cursive;
  font-size:clamp(2rem,5vw,3rem);
  background:linear-gradient(135deg,var(--gold),var(--orange));
  -webkit-background-clip:text; -webkit-text-fill-color:transparent;
}
.result-score {
  font-size:1.2rem; color:var(--white);
}
.result-score span { color:var(--gold); font-family:'Fredoka One',cursive; font-size:2rem; }
 
.btn-home {
  background:linear-gradient(135deg,var(--purple),var(--pink));
  border:none; border-radius:14px;
  padding:.9rem 2.5rem;
  font-family:'Fredoka One',cursive;
  font-size:1.2rem; color:white;
  cursor:pointer;
  box-shadow:0 6px 30px rgba(168,85,247,.5);
  transition:all .25s;
}
.btn-home:hover { transform:translateY(-3px) scale(1.04); box-shadow:0 10px 40px rgba(168,85,247,.6); }
 
.btn-back {
  background:transparent;
  border:2px solid rgba(240,230,255,.2);
  border-radius:12px;
  padding:.5rem 1.2rem;
  font-family:'Nunito',sans-serif;
  font-size:.82rem;
  font-weight:700;
  color:rgba(240,230,255,.5);
  cursor:pointer;
  transition:all .25s;
}
.btn-back:hover { border-color:rgba(240,230,255,.5); color:var(--white); }
 
/* ══ EXPLOSION PARTICLES ══ */
.particle {
  position:fixed;
  pointer-events:none;
  z-index:999;
  border-radius:50%;
  animation:particleFly var(--dur) ease-out forwards;
}
@keyframes particleFly {
  0%{transform:translate(0,0) scale(1);opacity:1;}
  100%{transform:translate(var(--dx),var(--dy)) scale(0);opacity:0;}
}
 
/* ══ TOAST ══ */
.toast {
  position:fixed;
  top:80px; left:50%; transform:translateX(-50%);
  z-index:999;
  background:rgba(0,0,0,.85);
  border-radius:14px;
  padding:.7rem 1.5rem;
  font-family:'Fredoka One',cursive;
  font-size:1.1rem;
  border:2px solid var(--green);
  color:#6ee7b7;
  animation:toastIn .3s ease, toastOut .3s ease 1.5s forwards;
  pointer-events:none;
  white-space:nowrap;
}
.toast.bad { border-color:var(--red); color:#fca5a5; }
@keyframes toastIn  { from{opacity:0;top:60px;}to{opacity:1;top:80px;} }
@keyframes toastOut { from{opacity:1;}to{opacity:0;} }
 
/* scrollbar */
*::-webkit-scrollbar { width:4px; }
*::-webkit-scrollbar-thumb { background:rgba(168,85,247,.3); border-radius:2px; }
 
/* ══ PATH WALKER SVG ══ */
.walker {
  position:absolute;
  z-index:8;
  font-size:2rem;
  transition:all 1s cubic-bezier(.4,0,.2,1);
  filter:drop-shadow(0 0 8px rgba(16,185,129,.8));
}
</style>
</head>
<body>
 
<canvas id="starCanvas"></canvas>
 
<!-- ══ HOME ══ -->
<div class="screen active" id="homeScreen">
  <div class="rocket-anim">🚀</div>
  <div class="home-title">Angličtina<br>pro Maminku!</div>
  <div class="home-sub">Uč se anglicky hraním her ✨</div>
 
  <div class="mode-cards">
    <div class="mode-card" onclick="startSpace()">
      <span class="mc-icon">🛸</span>
      <h3>Slovíčka</h3>
      <p>Uteč z vesmírné lodi! Uhodni správný překlad</p>
    </div>
    <div class="mode-card" onclick="startPath()">
      <span class="mc-icon">🌿</span>
      <h3>Věty</h3>
      <p>Projdi pohádkovou cestou! Sestav anglickou větu</p>
    </div>
    <div class="mode-card" onclick="startPhrases()">
      <span class="mc-icon">⭐</span>
      <h3>Fráze</h3>
      <p>Spoj anglické fráze s českými překlady</p>
    </div>
  </div>
 
  <div class="home-stars" id="totalStars">
    ⭐ Celkem hvězd: <strong id="starCount">0</strong>
  </div>
</div>
 
<!-- ══ SPACE SHIP ══ -->
<div class="screen" id="spaceScreen">
  <div style="width:100%;max-width:700px;display:flex;flex-direction:column;height:100%;">
    <div class="game-header">
      <div class="gh-left">
        <div class="gh-title">🛸 Útěk z vesmírné lodi</div>
        <div class="gh-sub">Uhodní překlad → raketa uletí!</div>
      </div>
      <div style="display:flex;align-items:center;gap:1rem;">
        <div class="lives" id="spaceLives"></div>
        <div class="score-badge">⭐ <span id="spaceScore">0</span></div>
      </div>
    </div>
 
    <div class="space-scene">
      <!-- Stars bg -->
      <div class="progress-wrap" style="position:absolute;top:70px;left:50%;transform:translateX(-50%);width:calc(100% - 3rem);max-width:420px;">
        <div class="progress-fill" id="spaceProg" style="width:0%"></div>
      </div>
 
      <!-- Ship -->
      <div class="ship-wrap" id="shipWrap">
        <svg width="90" height="110" viewBox="0 0 90 110" xmlns="http://www.w3.org/2000/svg">
          <!-- body -->
          <ellipse cx="45" cy="55" rx="28" ry="40" fill="#1e0a4a" stroke="#7c3aed" stroke-width="2"/>
          <!-- window -->
          <circle cx="45" cy="45" r="14" fill="#0a1628" stroke="#22d3ee" stroke-width="2"/>
          <circle cx="45" cy="45" r="9" fill="#0d2040" opacity=".8"/>
          <ellipse cx="40" cy="40" rx="4" ry="3" fill="rgba(255,255,255,.15)"/>
          <!-- fins -->
          <path d="M17 75 L5 100 L30 85Z" fill="#4c1d95" stroke="#7c3aed" stroke-width="1.5"/>
          <path d="M73 75 L85 100 L60 85Z" fill="#4c1d95" stroke="#7c3aed" stroke-width="1.5"/>
          <!-- nose -->
          <path d="M45 10 L65 45 L25 45Z" fill="#6d28d9" stroke="#a855f7" stroke-width="1.5"/>
          <path d="M45 14 L60 42 L30 42Z" fill="#7c3aed" opacity=".6"/>
          <!-- engine glow -->
          <ellipse cx="45" cy="93" rx="14" ry="7" fill="rgba(251,191,36,.3)"/>
          <ellipse cx="45" cy="96" rx="9" ry="5" fill="rgba(251,191,36,.5)"/>
          <ellipse cx="45" cy="99" rx="5" ry="3" fill="rgba(255,100,0,.7)"/>
          <!-- stars on body -->
          <circle cx="38" cy="58" r="1.5" fill="#22d3ee" opacity=".6"/>
          <circle cx="52" cy="62" r="1.5" fill="#a855f7" opacity=".6"/>
          <circle cx="44" cy="68" r="1" fill="#ec4899" opacity=".5"/>
        </svg>
      </div>
 
      <div class="word-card" id="wordCard">
        <div class="wc-english" id="wcWord">apple</div>
        <div class="wc-phonetic" id="wcPhonetic">[ˈæpl]</div>
        <div class="wc-hint">Vyber správný překlad 👇</div>
      </div>
 
      <div class="answers" id="answersGrid"></div>
      <div class="feedback-bar" id="spaceFeedback"></div>
    </div>
 
    <div style="padding:.8rem 1.5rem;display:flex;justify-content:center;">
      <button class="btn-back" onclick="goHome()">← Zpět domů</button>
    </div>
  </div>
</div>
 
<!-- ══ PATH GAME ══ -->
<div class="screen" id="pathScreen">
  <canvas id="pathCanvas"></canvas>
  <div class="path-ui">
    <div class="path-header">
      <div class="ph-title">🌿 Pohádková cesta</div>
      <div style="display:flex;align-items:center;gap:1rem;">
        <div class="score-badge">⭐ <span id="pathScore">0</span></div>
        <button class="btn-back" onclick="goHome()">← Domů</button>
      </div>
    </div>
 
    <div style="flex:1;position:relative;">
      <div class="walker" id="walker">🧙‍♀️</div>
    </div>
 
    <div class="path-content">
      <div class="phrase-card" id="pathPhraseCard">
        <div class="pc-label">Přelož do angličtiny</div>
        <div class="pc-cz" id="pathCzPhrase">Jak se jmenuješ?</div>
        <div class="pc-phonetic" id="pathPhonetic">What is your name?</div>
      </div>
 
      <div class="sentence-hint">Seřaď slova ve správném pořadí 👇 (klikni na slovo pro odebrání)</div>
      <div class="sentence-display" id="sentenceDisplay"></div>
      <div class="word-bank" id="wordBank"></div>
 
      <div style="display:flex;gap:.8rem;align-items:center;">
        <button class="path-check-btn" onclick="checkSentence()">✓ Zkontrolovat</button>
        <button class="btn-back" onclick="clearSentence()" style="border-color:rgba(251,191,36,.3);color:rgba(251,191,36,.6);">🔄 Reset</button>
      </div>
 
      <div class="feedback-bar" id="pathFeedback"></div>
    </div>
  </div>
</div>
 
<!-- ══ PHRASES GAME ══ -->
<div class="screen" id="phrasesScreen">
  <div class="phrase-match">
    <div class="game-header" style="border-bottom-color:rgba(251,191,36,.2);">
      <div class="gh-left">
        <div class="gh-title" style="color:var(--yellow);">⭐ Spoj fráze</div>
        <div class="gh-sub">Klikni na anglicky, pak na česky</div>
      </div>
      <div style="display:flex;align-items:center;gap:1rem;">
        <div class="score-badge">⭐ <span id="phrasesScore">0</span></div>
        <button class="btn-back" onclick="goHome()">← Domů</button>
      </div>
    </div>
    <div class="match-area" id="matchArea">
      <div class="match-col">
        <h4>🇬🇧 Anglicky</h4>
        <div id="engCol"></div>
      </div>
      <div class="match-col">
        <h4>🇨🇿 Česky</h4>
        <div id="czCol"></div>
      </div>
    </div>
    <div style="padding:.8rem;text-align:center;">
      <div class="feedback-bar" id="phrasesFeedback"></div>
    </div>
  </div>
</div>
 
<!-- ══ RESULT ══ -->
<div class="screen" id="resultScreen">
  <div class="result-icon" id="resultIcon">🎉</div>
  <div class="result-title" id="resultTitle">Skvělé!</div>
  <div class="result-score">Získala jsi <span id="resultPoints">0</span> hvězd!</div>
  <div id="resultMsg" style="font-size:.9rem;color:rgba(240,230,255,.6);max-width:300px;text-align:center;"></div>
  <button class="btn-home" onclick="goHome()">🏠 Zpět domů</button>
</div>
 
<script>
/* ══ STARS BACKGROUND ══ */
(function(){
  const c=document.getElementById('starCanvas'),ctx=c.getContext('2d');
  let W,H,stars=[];
  function resize(){W=c.width=innerWidth;H=c.height=innerHeight;}
  resize(); addEventListener('resize',()=>{resize();initStars();});
  function initStars(){
    stars=[];
    for(let i=0;i<220;i++){
      stars.push({x:Math.random()*W,y:Math.random()*H,r:Math.random()*1.8+.2,a:Math.random()*.8+.1,sp:Math.random()*.015+.003,ph:Math.random()*Math.PI*2,color:['#fff','#c4b5fd','#93c5fd','#fde68a','#fbcfe8'][Math.floor(Math.random()*5)]});
    }
  }
  initStars();
  let f=0;
  function draw(){
    ctx.clearRect(0,0,W,H); f+=.5;
    // nebula
    const g=ctx.createRadialGradient(W*.3,H*.4,0,W*.3,H*.4,W*.5);
    g.addColorStop(0,'rgba(124,58,237,.04)'); g.addColorStop(1,'rgba(0,0,0,0)');
    ctx.fillStyle=g; ctx.fillRect(0,0,W,H);
    const g2=ctx.createRadialGradient(W*.7,H*.7,0,W*.7,H*.7,W*.4);
    g2.addColorStop(0,'rgba(34,211,238,.03)'); g2.addColorStop(1,'rgba(0,0,0,0)');
    ctx.fillStyle=g2; ctx.fillRect(0,0,W,H);
    stars.forEach(s=>{
      const p=s.a+Math.sin(f*s.sp+s.ph)*.3;
      ctx.beginPath(); ctx.arc(s.x,s.y,s.r,0,Math.PI*2);
      ctx.fillStyle=s.color; ctx.globalAlpha=p; ctx.fill();
    });
    ctx.globalAlpha=1;
    requestAnimationFrame(draw);
  }
  draw();
})();
 
/* ══ DATA ══ */
const WORDS = [
  {en:'apple',ph:'[ˈæpl]',cz:'jablko',wrong:['pomeranč','banán','hruška']},
  {en:'water',ph:'[ˈwɔːtər]',cz:'voda',wrong:['káva','čaj','mléko']},
  {en:'hello',ph:'[həˈloʊ]',cz:'ahoj',wrong:['nashledanou','prosím','děkuji']},
  {en:'house',ph:'[haʊs]',cz:'dům',wrong:['auto','strom','zahrada']},
  {en:'cat',ph:'[kæt]',cz:'kočka',wrong:['pes','pták','ryba']},
  {en:'dog',ph:'[dɒɡ]',cz:'pes',wrong:['kočka','králík','had']},
  {en:'book',ph:'[bʊk]',cz:'kniha',wrong:['pero','papír','tužka']},
  {en:'bread',ph:'[brɛd]',cz:'chléb',wrong:['máslo','sýr','vejce']},
  {en:'sun',ph:'[sʌn]',cz:'slunce',wrong:['měsíc','hvězda','mrak']},
  {en:'beautiful',ph:'[ˈbjuːtɪfəl]',cz:'krásný/á',wrong:['ošklivý','malý','velký']},
  {en:'family',ph:'[ˈfæmɪli]',cz:'rodina',wrong:['přátelé','sousedi','kolegové']},
  {en:'morning',ph:'[ˈmɔːrnɪŋ]',cz:'ráno',wrong:['večer','noc','poledne']},
  {en:'please',ph:'[pliːz]',cz:'prosím',wrong:['díky','promiň','ahoj']},
  {en:'thank you',ph:'[θæŋk juː]',cz:'děkuji',wrong:['prosím','promiňte','nashledanou']},
  {en:'good',ph:'[ɡʊd]',cz:'dobrý/á',wrong:['špatný','rychlý','pomalý']},
  {en:'love',ph:'[lʌv]',cz:'láska',wrong:['naděje','víra','radost']},
  {en:'flower',ph:'[ˈflaʊər]',cz:'květina',wrong:['strom','tráva','keř']},
  {en:'music',ph:'[ˈmjuːzɪk]',cz:'hudba',wrong:['tanec','film','divadlo']},
  {en:'happy',ph:'[ˈhæpi]',cz:'šťastný/á',wrong:['smutný','unavený','naštvaný']},
  {en:'friend',ph:'[frɛnd]',cz:'přítel/ka',wrong:['kolega','soused','cizinec']},
];
 
const SENTENCES = [
  {cz:'Jak se jmenuješ?',en:['What','is','your','name','?'],ph:'What is your name?',extra:['When','How','my']},
  {cz:'Jmenuji se Marie.',en:['My','name','is','Marie','.'],ph:'My name is Marie.',extra:['Her','your','was']},
  {cz:'Jak se máš?',en:['How','are','you','?'],ph:'How are you?',extra:['What','is','do']},
  {cz:'Mám se dobře, díky.',en:['I','am','fine',',','thank','you','.'],ph:'I am fine, thank you.',extra:['She','was','great']},
  {cz:'Kde je záchod?',en:['Where','is','the','toilet','?'],ph:'Where is the toilet?',extra:['How','a','bathroom']},
  {cz:'Kolik to stojí?',en:['How','much','does','it','cost','?'],ph:'How much does it cost?',extra:['Many','is','price']},
  {cz:'Mluv pomaleji, prosím.',en:['Please','speak','more','slowly','.'],ph:'Please speak more slowly.',extra:['Talk','fast','quickly']},
  {cz:'Nerozumím.',en:['I','do','not','understand','.'],ph:'I do not understand.',extra:['She','can','know']},
  {cz:'Mluvíš anglicky?',en:['Do','you','speak','English','?'],ph:'Do you speak English?',extra:['Can','Czech','French']},
  {cz:'Kde je nádraží?',en:['Where','is','the','train','station','?'],ph:'Where is the train station?',extra:['How','airport','bus']},
];
 
const PHRASES_DATA = [
  {en:'Good morning!',cz:'Dobré ráno!',ph:'[ɡʊd ˈmɔːrnɪŋ]'},
  {en:'Good night!',cz:'Dobrou noc!',ph:'[ɡʊd naɪt]'},
  {en:'Excuse me.',cz:'Promiňte.',ph:'[ɪkˈskjuːz miː]'},
  {en:"I'm sorry.",cz:'Je mi líto.',ph:'[aɪm ˈsɒri]'},
  {en:'No problem!',cz:'Žádný problém!',ph:'[noʊ ˈprɒbləm]'},
  {en:'See you later!',cz:'Uvidíme se!',ph:'[siː juː ˈleɪtər]'},
  {en:"I don't know.",cz:'Nevím.',ph:'[aɪ doʊnt noʊ]'},
  {en:'Can you help me?',cz:'Můžete mi pomoci?',ph:'[kæn juː hɛlp miː]'},
  {en:"That's delicious!",cz:'To je výborné!',ph:'[ðæts dɪˈlɪʃəs]'},
  {en:"You're welcome!",cz:'Není zač!',ph:'[jʊər ˈwɛlkəm]'},
];
 
/* ══ STATE ══ */
let totalStars = parseInt(localStorage.getItem('totalStars')||'0');
let spaceScore=0, spaceLives=3, spaceIdx=0, spaceWords=[], spaceAnswering=true;
let pathScore=0, pathIdx=0, pathSentences=[], walkerStep=0;
let phrasesScore=0, selectedEng=null, matchedCount=0;
 
document.getElementById('starCount').textContent = totalStars;
 
function shuffle(a){return [...a].sort(()=>Math.random()-.5);}
 
/* ══ NAVIGATION ══ */
function showScreen(id){
  document.querySelectorAll('.screen').forEach(s=>s.classList.remove('active'));
  document.getElementById(id).classList.add('active');
}
 
function goHome(){
  showScreen('homeScreen');
  document.getElementById('starCount').textContent=totalStars;
}
 
/* ══ PARTICLES ══ */
function burst(x,y,color,count=16){
  for(let i=0;i<count;i++){
    const p=document.createElement('div');
    p.className='particle';
    const angle=Math.random()*360;
    const dist=Math.random()*120+40;
    const dur=(Math.random()*.6+.4)+'s';
    p.style.cssText=`left:${x}px;top:${y}px;width:${Math.random()*8+4}px;height:${Math.random()*8+4}px;background:${color};--dx:${Math.cos(angle*Math.PI/180)*dist}px;--dy:${Math.sin(angle*Math.PI/180)*dist}px;--dur:${dur};`;
    document.body.appendChild(p);
    setTimeout(()=>p.remove(), 1100);
  }
}
 
function showToast(msg,bad=false){
  const t=document.createElement('div');
  t.className='toast'+(bad?' bad':'');
  t.textContent=msg;
  document.body.appendChild(t);
  setTimeout(()=>t.remove(),1900);
}
 
/* ══ SPACE GAME ══ */
function startSpace(){
  spaceScore=0; spaceLives=3; spaceIdx=0;
  spaceWords=shuffle(WORDS).slice(0,12);
  document.getElementById('spaceScore').textContent=0;
  renderLives();
  showScreen('spaceScreen');
  showSpaceWord();
}
 
function renderLives(){
  const el=document.getElementById('spaceLives');
  el.innerHTML='';
  for(let i=0;i<3;i++){
    const d=document.createElement('div');
    d.className='life'+(i>=spaceLives?' lost':'');
    d.textContent='❤️';
    el.appendChild(d);
  }
}
 
function showSpaceWord(){
  if(spaceIdx>=spaceWords.length){endGame('space');return;}
  spaceAnswering=true;
  const w=spaceWords[spaceIdx];
  document.getElementById('wcWord').textContent=w.en;
  document.getElementById('wcPhonetic').textContent=w.ph;
  document.getElementById('spaceFeedback').innerHTML='';
  document.getElementById('spaceProg').style.width=(spaceIdx/spaceWords.length*100)+'%';
 
  // build answers
  const opts=shuffle([w.cz,...w.wrong]);
  const grid=document.getElementById('answersGrid');
  grid.innerHTML='';
  opts.forEach(opt=>{
    const btn=document.createElement('button');
    btn.className='ans-btn';
    btn.textContent=opt;
    btn.onclick=()=>answerSpace(opt,w.cz,btn);
    grid.appendChild(btn);
  });
 
  // reset ship
  const ship=document.getElementById('shipWrap');
  ship.className='ship-wrap';
}
 
function answerSpace(chosen,correct,btn){
  if(!spaceAnswering)return;
  spaceAnswering=false;
  const grid=document.getElementById('answersGrid');
  grid.querySelectorAll('.ans-btn').forEach(b=>b.disabled=true);
 
  if(chosen===correct){
    btn.classList.add('correct');
    spaceScore++;
    document.getElementById('spaceScore').textContent=spaceScore;
    document.getElementById('spaceFeedback').innerHTML='✅ Správně! <em>'+correct+'</em>';
 
    // burst + ship escape
    const rect=btn.getBoundingClientRect();
    burst(rect.left+rect.width/2,rect.top,['#22d3ee','#a855f7','#fbbf24'][Math.floor(Math.random()*3)]);
    showToast('🚀 Raketa uletěla! +1⭐');
 
    const ship=document.getElementById('shipWrap');
    ship.className='ship-wrap escape';
    setTimeout(()=>{
      spaceIdx++;
      showSpaceWord();
    },1300);
  } else {
    btn.classList.add('wrong');
    // highlight correct
    grid.querySelectorAll('.ans-btn').forEach(b=>{
      if(b.textContent===correct) b.classList.add('correct');
    });
    spaceLives--;
    renderLives();
    document.getElementById('spaceFeedback').innerHTML='❌ Správně bylo: <em>'+correct+'</em>';
    const ship=document.getElementById('shipWrap');
    ship.className='ship-wrap shake';
    setTimeout(()=>{
      if(spaceLives<=0){endGame('space');return;}
      spaceIdx++;
      showSpaceWord();
    },1400);
  }
}
 
/* ══ PATH GAME ══ */
function startPath(){
  pathScore=0; pathIdx=0; walkerStep=0;
  pathSentences=shuffle(SENTENCES).slice(0,8);
  document.getElementById('pathScore').textContent=0;
  showScreen('pathScreen');
  drawPathCanvas();
  positionWalker(0);
  showPathSentence();
}
 
function drawPathCanvas(){
  const c=document.getElementById('pathCanvas');
  const ctx=c.getContext('2d');
  c.width=c.offsetWidth||window.innerWidth;
  c.height=c.offsetHeight||window.innerHeight;
  const W=c.width, H=c.height;
 
  ctx.clearRect(0,0,W,H);
 
  // sky gradient
  const sky=ctx.createLinearGradient(0,0,0,H);
  sky.addColorStop(0,'#030f06');
  sky.addColorStop(.6,'#061a08');
  sky.addColorStop(1,'#041204');
  ctx.fillStyle=sky; ctx.fillRect(0,0,W,H);
 
  // stars
  for(let i=0;i<80;i++){
    ctx.beginPath();
    ctx.arc(Math.random()*W,Math.random()*H*.5,Math.random()*1.5+.3,0,Math.PI*2);
    ctx.fillStyle=`rgba(255,255,255,${Math.random()*.5+.1})`;
    ctx.fill();
  }
 
  // ground
  const gnd=ctx.createLinearGradient(0,H*.55,0,H);
  gnd.addColorStop(0,'#0d3b17');
  gnd.addColorStop(1,'#071a0b');
  ctx.fillStyle=gnd;
  ctx.fillRect(0,H*.55,W,H*.45);
 
  // path
  const totalSteps=pathSentences.length+1;
  ctx.lineWidth=28;
  ctx.strokeStyle='rgba(139,90,43,.4)';
  ctx.lineCap='round';
  ctx.lineJoin='round';
  ctx.beginPath();
  for(let i=0;i<=totalSteps;i++){
    const x=getStepX(i,W,totalSteps);
    const y=H*.68;
    if(i===0)ctx.moveTo(x,y); else ctx.lineTo(x,y);
  }
  ctx.stroke();
 
  // path highlight
  ctx.lineWidth=18;
  ctx.strokeStyle='rgba(180,120,60,.35)';
  ctx.beginPath();
  for(let i=0;i<=totalSteps;i++){
    const x=getStepX(i,W,totalSteps);
    const y=H*.68;
    if(i===0)ctx.moveTo(x,y); else ctx.lineTo(x,y);
  }
  ctx.stroke();
 
  // step markers
  for(let i=0;i<=totalSteps;i++){
    const x=getStepX(i,W,totalSteps);
    const y=H*.68;
    ctx.beginPath();
    ctx.arc(x,y,10,0,Math.PI*2);
    ctx.fillStyle=i<=walkerStep?'rgba(16,185,129,.8)':'rgba(139,90,43,.4)';
    ctx.fill();
    ctx.strokeStyle='rgba(255,255,255,.2)';
    ctx.lineWidth=1.5; ctx.stroke();
  }
 
  // trees
  const treeXs=[W*.08,W*.22,W*.38,W*.55,W*.7,W*.85,W*.95];
  treeXs.forEach(tx=>{
    const ty=H*.58;
    // trunk
    ctx.fillStyle='#4a2c0a';
    ctx.fillRect(tx-4,ty,8,28);
    // crown
    ctx.beginPath();
    ctx.arc(tx,ty-10,22,0,Math.PI*2);
    ctx.fillStyle='#155724';
    ctx.fill();
    ctx.beginPath();
    ctx.arc(tx-6,ty-4,16,0,Math.PI*2);
    ctx.fillStyle='#1a6b2e';
    ctx.fill();
    ctx.beginPath();
    ctx.arc(tx+5,ty-6,14,0,Math.PI*2);
    ctx.fillStyle='#0f4a1e';
    ctx.fill();
  });
 
  // flowers
  ['#ec4899','#fbbf24','#a855f7','#22d3ee','#f97316'].forEach((color,i)=>{
    const fx=W*.12+i*W*.18;
    const fy=H*.62;
    ctx.beginPath(); ctx.arc(fx,fy,5,0,Math.PI*2);
    ctx.fillStyle=color; ctx.globalAlpha=.7; ctx.fill();
    ctx.globalAlpha=1;
  });
 
  // castle at end
  const cx=W*.92, cy=H*.52;
  ctx.fillStyle='#1a0a3a';
  ctx.fillRect(cx-25,cy,50,35);
  ctx.fillRect(cx-30,cy-10,60,15);
  // towers
  ctx.fillRect(cx-32,cy-25,18,40);
  ctx.fillRect(cx+14,cy-25,18,40);
  // battlements
  for(let bi=0;bi<4;bi++){
    ctx.fillRect(cx-32+bi*8,cy-32,5,8);
    ctx.fillRect(cx+14+bi*8,cy-32,5,8);
  }
  // flag
  ctx.fillStyle='#ec4899';
  ctx.beginPath();
  ctx.moveTo(cx,cy-40); ctx.lineTo(cx+15,cy-32); ctx.lineTo(cx,cy-24);
  ctx.fill();
  // door
  ctx.fillStyle='#0a0520';
  ctx.beginPath();
  ctx.ellipse(cx,cy+24,8,12,0,Math.PI,0,true);
  ctx.fillRect(cx-8,cy+12,16,12);
  ctx.fill();
  // windows
  ctx.fillStyle='#fbbf24';
  ctx.globalAlpha=.6;
  ctx.beginPath(); ctx.arc(cx-22,cy-5,5,0,Math.PI*2); ctx.fill();
  ctx.beginPath(); ctx.arc(cx+22,cy-5,5,0,Math.PI*2); ctx.fill();
  ctx.globalAlpha=1;
}
 
function getStepX(i,W,total){
  return W*.06 + (W*.86/(total))*i;
}
 
function positionWalker(step){
  const c=document.getElementById('pathCanvas');
  const W=c.offsetWidth||window.innerWidth;
  const H=c.offsetHeight||window.innerHeight;
  const total=pathSentences.length+1;
  const x=getStepX(step,W,total);
  const y=H*.62;
  const walker=document.getElementById('walker');
  walker.style.left=(x-20)+'px';
  walker.style.top=(y-40)+'px';
}
 
function showPathSentence(){
  if(pathIdx>=pathSentences.length){endGame('path');return;}
  const s=pathSentences[pathIdx];
  document.getElementById('pathCzPhrase').textContent=s.cz;
  document.getElementById('pathPhonetic').textContent=s.ph;
  document.getElementById('pathFeedback').innerHTML='';
  document.getElementById('sentenceDisplay').innerHTML='';
 
  // word bank: correct words + extra, shuffled
  const bank=shuffle([...s.en,...(s.extra||[])]);
  const wb=document.getElementById('wordBank');
  wb.innerHTML='';
  bank.forEach(w=>{
    const btn=document.createElement('button');
    btn.className='wb-word';
    btn.textContent=w;
    btn.onclick=()=>addWordToSentence(w,btn);
    wb.appendChild(btn);
  });
}
 
let currentSentence=[];
 
function addWordToSentence(word,btn){
  if(btn.classList.contains('used'))return;
  btn.classList.add('used');
  currentSentence.push({word,btn});
  renderSentenceDisplay();
}
 
function renderSentenceDisplay(){
  const sd=document.getElementById('sentenceDisplay');
  sd.innerHTML='';
  if(currentSentence.length===0){
    sd.innerHTML='<span style="color:rgba(240,230,255,.3);font-size:.8rem;">Klikni na slova níže…</span>';
    return;
  }
  currentSentence.forEach((item,i)=>{
    const span=document.createElement('span');
    span.className='sent-word';
    span.textContent=item.word;
    span.onclick=()=>{
      item.btn.classList.remove('used');
      currentSentence.splice(i,1);
      renderSentenceDisplay();
    };
    sd.appendChild(span);
  });
}
 
function clearSentence(){
  currentSentence.forEach(item=>item.btn.classList.remove('used'));
  currentSentence=[];
  renderSentenceDisplay();
}
 
function checkSentence(){
  if(currentSentence.length===0)return;
  const s=pathSentences[pathIdx];
  const built=currentSentence.map(i=>i.word).join(' ');
  const correct=s.en.join(' ');
 
  if(built===correct){
    pathScore++;
    document.getElementById('pathScore').textContent=pathScore;
    document.getElementById('pathFeedback').innerHTML='✅ Perfektně! "'+correct+'"';
    walkerStep++;
    drawPathCanvas();
    positionWalker(walkerStep);
    burst(window.innerWidth/2,window.innerHeight*.6,'#10b981',20);
    showToast('🌟 Krok vpřed! +1⭐');
    currentSentence=[];
    pathIdx++;
    setTimeout(showPathSentence,1500);
  } else {
    document.getElementById('pathFeedback').innerHTML='❌ Zkus znovu! Správně: "'+correct+'"';
    showToast('Zkus to znovu! Správné pořadí jiné 🔄',true);
    clearSentence();
  }
}
 
/* ══ PHRASES GAME ══ */
function startPhrases(){
  phrasesScore=0; selectedEng=null; matchedCount=0;
  document.getElementById('phrasesScore').textContent=0;
  showScreen('phrasesScreen');
  renderPhrases();
}
 
function renderPhrases(){
  const subset=shuffle(PHRASES_DATA).slice(0,6);
  const engCol=document.getElementById('engCol');
  const czCol=document.getElementById('czCol');
  engCol.innerHTML=''; czCol.innerHTML='';
 
  const shuffledCz=shuffle(subset.map(p=>p.cz));
 
  subset.forEach(p=>{
    const eDiv=document.createElement('div');
    eDiv.className='match-item';
    eDiv.dataset.eng=p.en;
    eDiv.dataset.cz=p.cz;
    eDiv.innerHTML=`<div>${p.en}</div><div style="font-size:.65rem;color:rgba(240,230,255,.4);margin-top:.2rem;">${p.ph}</div>`;
    eDiv.onclick=()=>selectEng(eDiv);
    engCol.appendChild(eDiv);
  });
 
  shuffledCz.forEach(cz=>{
    const cDiv=document.createElement('div');
    cDiv.className='match-item';
    cDiv.dataset.cz=cz;
    cDiv.textContent=cz;
    cDiv.onclick=()=>selectCz(cDiv);
    czCol.appendChild(cDiv);
  });
 
  document.getElementById('phrasesFeedback').innerHTML='';
  matchedCount=0;
}
 
function selectEng(div){
  if(div.classList.contains('done'))return;
  document.querySelectorAll('#engCol .match-item').forEach(d=>d.classList.remove('selected'));
  selectedEng=div;
  div.classList.add('selected');
}
 
function selectCz(div){
  if(!selectedEng||div.classList.contains('done'))return;
  if(div.classList.contains('done'))return;
 
  if(selectedEng.dataset.cz===div.dataset.cz){
    // correct match
    selectedEng.classList.remove('selected');
    selectedEng.classList.add('done');
    div.classList.add('done');
    phrasesScore++;
    matchedCount++;
    document.getElementById('phrasesScore').textContent=phrasesScore;
    burst(div.getBoundingClientRect().left+50,div.getBoundingClientRect().top+20,'#fbbf24',14);
    showToast('⭐ Správně! +1⭐');
    document.getElementById('phrasesFeedback').innerHTML='✅ Skvěle!';
    selectedEng=null;
 
    const total=document.querySelectorAll('#engCol .match-item').length;
    if(matchedCount>=total) setTimeout(()=>endGame('phrases'),800);
  } else {
    // wrong
    selectedEng.classList.add('wrong-flash');
    div.classList.add('wrong-flash');
    setTimeout(()=>{
      selectedEng.classList.remove('wrong-flash','selected');
      div.classList.remove('wrong-flash');
      selectedEng=null;
    },600);
    document.getElementById('phrasesFeedback').innerHTML='❌ Zkus jinou kombinaci!';
    showToast('Hmm, zkus jinak! 🤔',true);
  }
}
 
/* ══ END GAME ══ */
function endGame(mode){
  let pts=0, icon='🎉', title='Skvělé!', msg='';
  if(mode==='space'){
    pts=spaceScore;
    if(pts>=10){icon='🚀🌟';title='Absolutní hvězda!';msg='Znáš všechna slovíčka jako profíček!';}
    else if(pts>=6){icon='🚀';title='Výborně!';msg='Rakety létají díky tobě!';}
    else{icon='💪';title='Pokračuj!';msg='Každé cvičení tě posune dál!';}
  } else if(mode==='path'){
    pts=pathScore;
    if(pts>=7){icon='🏰✨';title='Dobyla jsi hrad!';msg='Všechny věty perfektně!';}
    else if(pts>=4){icon='🌿';title='Pohádka pokračuje!';msg='Prošla jsi velkou část cesty!';}
    else{icon='👣';title='První kroky!';msg='Výborný začátek cesty!';}
  } else {
    pts=phrasesScore;
    icon='⭐🎊'; title='Mistr frází!'; msg='Znáš všechny důležité fráze!';
  }
 
  totalStars+=pts;
  localStorage.setItem('totalStars',totalStars);
 
  document.getElementById('resultIcon').textContent=icon;
  document.getElementById('resultTitle').textContent=title;
  document.getElementById('resultPoints').textContent=pts;
  document.getElementById('resultMsg').textContent=msg;
  showScreen('resultScreen');
 
  // mega burst
  for(let i=0;i<5;i++){
    setTimeout(()=>{
      burst(Math.random()*window.innerWidth,Math.random()*window.innerHeight*.5,
        ['#fbbf24','#a855f7','#22d3ee','#ec4899','#10b981'][Math.floor(Math.random()*5)],20);
    },i*200);
  }
}
 
/* ══ INIT ══ */
renderSentenceDisplay();
 
// resize path canvas when path screen activates
const pathObs=new MutationObserver(()=>{
  if(document.getElementById('pathScreen').classList.contains('active')){
    setTimeout(()=>{drawPathCanvas();positionWalker(walkerStep);},50);
  }
});
pathObs.observe(document.getElementById('pathScreen'),{attributes:true});
</script>
</body>
</html>
