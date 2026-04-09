# recovery-companion-app
Free wellness app by a Project Recovery Specialist. Daily check-in, nervous system tools, quit trackers, health education &amp; free Canadian mental health links. No login. No account. Your data stays on your device. Open in any browser. 💚<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Recovery Companion — broadvirtualo.com</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
:root {
  --sage:    #5a9e7a;
  --teal:    #1d9e75;
  --teal-dk: #0f6e56;
  --mint:    #a8d5ba;
  --bg:      #0d1a14;
  --bg2:     #142018;
  --card:    #1a2e22;
  --card2:   #213328;
  --border:  #2a4535;
  --white:   #eef8f2;
  --muted:   #7aab8e;
  --dim:     #3a5a45;
  --warm:    #c8a050;
  --orange:  #e07830;
  --red:     #c84848;
  --blue:    #4a90d8;
  --purple:  #8a6ab8;
  --gold:    #d4a820;
  --font-head: 'DM Serif Display', Georgia, serif;
  --font-body: 'DM Sans', system-ui, sans-serif;
}
* { box-sizing: border-box; margin: 0; padding: 0; }
html, body { height: 100%; font-family: var(--font-body); background: var(--bg); color: var(--white); font-size: 16px; }

/* ── NAV ── */
#app { display: flex; flex-direction: column; height: 100vh; overflow: hidden; }
#topbar { background: var(--bg2); border-bottom: 1px solid var(--border); padding: 10px 16px; display: flex; align-items: center; justify-content: space-between; flex-shrink: 0; }
#topbar h1 { font-family: var(--font-head); font-size: 1.2rem; color: var(--teal); font-style: italic; }
#topbar .week-badge { background: var(--card); border: 1px solid var(--border); border-radius: 20px; padding: 4px 12px; font-size: 0.75rem; color: var(--muted); }
#nav { display: flex; overflow-x: auto; background: var(--bg2); border-bottom: 1px solid var(--border); scrollbar-width: none; flex-shrink: 0; }
#nav::-webkit-scrollbar { display: none; }
.nav-btn { padding: 10px 14px; font-size: 0.78rem; font-weight: 500; color: var(--muted); border: none; background: none; cursor: pointer; white-space: nowrap; border-bottom: 2px solid transparent; transition: all 0.2s; flex-shrink: 0; }
.nav-btn.active { color: var(--teal); border-bottom-color: var(--teal); }
.nav-btn:hover { color: var(--white); }
#content { flex: 1; overflow-y: auto; padding: 16px; }

/* ── SECTIONS ── */
.section { display: none; }
.section.active { display: block; }

/* ── CARDS ── */
.card { background: var(--card); border: 1px solid var(--border); border-radius: 14px; padding: 16px; margin-bottom: 14px; }
.card-title { font-family: var(--font-head); font-size: 1.1rem; color: var(--white); margin-bottom: 6px; }
.card-sub { font-size: 0.8rem; color: var(--muted); margin-bottom: 12px; }
.tag { display: inline-block; padding: 3px 10px; border-radius: 20px; font-size: 0.72rem; font-weight: 600; margin: 2px; }
.tag-teal { background: rgba(29,158,117,0.15); color: var(--teal); border: 1px solid rgba(29,158,117,0.3); }
.tag-warm { background: rgba(200,160,80,0.15); color: var(--warm); border: 1px solid rgba(200,160,80,0.3); }
.tag-orange { background: rgba(224,120,48,0.15); color: var(--orange); border: 1px solid rgba(224,120,48,0.3); }
.tag-blue { background: rgba(74,144,216,0.15); color: var(--blue); border: 1px solid rgba(74,144,216,0.3); }
.tag-purple { background: rgba(138,106,184,0.15); color: var(--purple); border: 1px solid rgba(138,106,184,0.3); }
.tag-gold { background: rgba(212,168,32,0.15); color: var(--gold); border: 1px solid rgba(212,168,32,0.3); }
.btn { display: inline-block; padding: 9px 18px; border-radius: 8px; font-size: 0.85rem; font-weight: 500; cursor: pointer; border: none; transition: all 0.15s; }
.btn-teal { background: var(--teal); color: #fff; }
.btn-teal:hover { background: var(--teal-dk); }
.btn-outline { background: transparent; border: 1px solid var(--border); color: var(--muted); }
.btn-outline:hover { border-color: var(--teal); color: var(--teal); }
.btn-full { width: 100%; text-align: center; display: block; }
h2 { font-family: var(--font-head); font-size: 1.4rem; color: var(--white); margin-bottom: 4px; }
h3 { font-size: 0.95rem; font-weight: 600; color: var(--sage); margin-bottom: 8px; }
p { font-size: 0.88rem; color: var(--muted); line-height: 1.6; margin-bottom: 8px; }
ul { padding-left: 18px; }
li { font-size: 0.85rem; color: var(--muted); line-height: 1.7; }
li strong { color: var(--white); }
.divider { border: none; border-top: 1px solid var(--border); margin: 14px 0; }
.grid2 { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
.grid3 { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 10px; }
@media(max-width:480px) { .grid2 { grid-template-columns: 1fr; } .grid3 { grid-template-columns: 1fr 1fr; } }

/* ── QUICK TOOL TIMER ── */
.timer-ring { display: flex; flex-direction: column; align-items: center; margin: 16px 0; }
.timer-circle { width: 140px; height: 140px; border-radius: 50%; border: 4px solid var(--border); display: flex; align-items: center; justify-content: center; position: relative; }
.timer-circle svg { position: absolute; top: 0; left: 0; transform: rotate(-90deg); }
.timer-num { font-family: var(--font-head); font-size: 2.8rem; color: var(--white); z-index: 1; }
.timer-label { font-size: 0.75rem; color: var(--muted); margin-top: 6px; letter-spacing: 0.08em; text-transform: uppercase; }
.phase-display { font-size: 1.1rem; font-weight: 600; color: var(--teal); text-align: center; margin: 8px 0; }
.phase-cue { font-size: 0.82rem; color: var(--muted); text-align: center; margin-bottom: 12px; }

/* ── TRACKER INPUTS ── */
.track-row { display: flex; align-items: center; justify-content: space-between; padding: 10px 0; border-bottom: 1px solid var(--border); }
.track-row:last-child { border-bottom: none; }
.track-label { font-size: 0.85rem; color: var(--white); }
.track-sub { font-size: 0.72rem; color: var(--muted); }
.rating-btns { display: flex; gap: 4px; }
.rating-btn { width: 32px; height: 32px; border-radius: 6px; border: 1px solid var(--border); background: var(--card2); color: var(--muted); font-size: 0.8rem; cursor: pointer; display: flex; align-items: center; justify-content: center; transition: all 0.15s; }
.rating-btn.sel { background: var(--teal); border-color: var(--teal); color: #fff; }
.num-input { width: 70px; background: var(--card2); border: 1px solid var(--border); color: var(--white); border-radius: 6px; padding: 6px 8px; font-size: 0.85rem; text-align: center; }
.checkbox-row { display: flex; align-items: center; gap: 10px; padding: 8px 0; cursor: pointer; }
.checkbox-row input[type=checkbox] { width: 18px; height: 18px; accent-color: var(--teal); cursor: pointer; }

/* ── PROGRESS BAR ── */
.prog-bar { background: var(--card2); border-radius: 20px; height: 8px; overflow: hidden; margin: 8px 0; }
.prog-fill { height: 100%; border-radius: 20px; background: var(--teal); transition: width 0.4s; }

/* ── STREAK ── */
.streak-row { display: flex; gap: 6px; flex-wrap: wrap; margin: 10px 0; }
.streak-dot { width: 28px; height: 28px; border-radius: 50%; border: 2px solid var(--border); display: flex; align-items: center; justify-content: center; font-size: 0.65rem; color: var(--dim); }
.streak-dot.done { background: var(--teal); border-color: var(--teal); color: #fff; }
.streak-dot.today { border-color: var(--teal); color: var(--teal); }

/* ── ACCORDION ── */
.accordion { border: 1px solid var(--border); border-radius: 10px; margin-bottom: 8px; overflow: hidden; }
.accordion-head { padding: 12px 14px; cursor: pointer; display: flex; justify-content: space-between; align-items: center; background: var(--card); font-size: 0.88rem; font-weight: 500; color: var(--white); }
.accordion-head:hover { background: var(--card2); }
.accordion-body { display: none; padding: 12px 14px; background: var(--bg2); border-top: 1px solid var(--border); }
.accordion-body.open { display: block; }
.accordion-arrow { transition: transform 0.2s; color: var(--muted); }
.accordion-arrow.open { transform: rotate(180deg); }

/* ── SECTION HEADERS ── */
.section-header { margin-bottom: 16px; }
.section-header h2 { font-size: 1.6rem; }
.section-header p { font-size: 0.85rem; }

/* ── PREMIUM LOCK ── */
.premium-lock { background: linear-gradient(135deg, rgba(212,168,32,0.08), rgba(29,158,117,0.08)); border: 1px solid rgba(212,168,32,0.25); border-radius: 12px; padding: 14px; text-align: center; margin-bottom: 14px; }
.premium-lock .lock-icon { font-size: 1.8rem; margin-bottom: 6px; }
.premium-lock h3 { color: var(--gold); margin-bottom: 4px; }

/* ── BREATHING ANIMATION ── */
@keyframes breathe-in { from { transform: scale(0.6); } to { transform: scale(1.0); } }
@keyframes breathe-hold { from { transform: scale(1.0); } to { transform: scale(1.0); } }
@keyframes breathe-out { from { transform: scale(1.0); } to { transform: scale(0.6); } }
.breath-circle { width: 100px; height: 100px; border-radius: 50%; background: radial-gradient(circle, var(--teal), var(--teal-dk)); margin: 0 auto 10px; transition: transform 1s ease-in-out; }

/* ── ZONE CARDS ── */
.zone-card { border-radius: 10px; padding: 12px; margin-bottom: 8px; }
.zone1 { background: rgba(29,158,117,0.12); border: 1px solid rgba(29,158,117,0.25); }
.zone2 { background: rgba(200,160,80,0.12); border: 1px solid rgba(200,160,80,0.25); }
.zone3 { background: rgba(200,80,80,0.12); border: 1px solid rgba(200,80,80,0.25); }

/* ── MENTAL HEALTH LINKS ── */
.mh-link { display: flex; align-items: center; justify-content: space-between; padding: 12px; border: 1px solid var(--border); border-radius: 10px; margin-bottom: 8px; background: var(--card); text-decoration: none; transition: border-color 0.2s; }
.mh-link:hover { border-color: var(--teal); }
.mh-link-info h4 { font-size: 0.88rem; font-weight: 600; color: var(--white); margin-bottom: 2px; }
.mh-link-info p { font-size: 0.75rem; color: var(--muted); margin: 0; }
.mh-arrow { color: var(--teal); font-size: 1.1rem; }

/* ── SELECT / TEXTAREA ── */
select, textarea { background: var(--card2); border: 1px solid var(--border); color: var(--white); border-radius: 8px; padding: 8px 10px; font-size: 0.85rem; font-family: var(--font-body); width: 100%; }
select:focus, textarea:focus { outline: none; border-color: var(--teal); }
label { font-size: 0.8rem; color: var(--muted); display: block; margin-bottom: 4px; margin-top: 10px; }

/* ── TOOL ICON GRID ── */
.tool-grid { display: grid; grid-template-columns: repeat(3,1fr); gap: 10px; margin-bottom: 14px; }
.tool-btn { background: var(--card); border: 1px solid var(--border); border-radius: 12px; padding: 14px 8px; text-align: center; cursor: pointer; transition: all 0.2s; }
.tool-btn:hover { border-color: var(--teal); background: var(--card2); }
.tool-btn .tool-icon { font-size: 1.6rem; margin-bottom: 6px; }
.tool-btn .tool-name { font-size: 0.72rem; font-weight: 500; color: var(--muted); line-height: 1.3; }
.tool-panel { display: none; }
.tool-panel.active { display: block; }

/* ── RESPONSIVE ── */
@media(min-width:768px) {
  #content { max-width: 760px; margin: 0 auto; }
  .tool-grid { grid-template-columns: repeat(4,1fr); }
}
</style>
</head>
<body>
<div id="app">

<!-- TOP BAR -->
<div id="topbar">
  <h1>Recovery Companion</h1>
  <span class="week-badge" id="week-badge">Week 1 of 12</span>
</div>

<!-- NAV -->
<nav id="nav">
  <button class="nav-btn active" onclick="showSection('home')">🏠 Home</button>
  <button class="nav-btn" onclick="showSection('assess')">📋 Assess</button>
  <button class="nav-btn" onclick="showSection('tracker')">📊 Track</button>
  <button class="nav-btn" onclick="showSection('tools')">⚡ Quick Tools</button>
  <button class="nav-btn" onclick="showSection('sessions')">🎯 Sessions</button>
  <button class="nav-btn" onclick="showSection('education')">🧠 Learn</button>
  <button class="nav-btn" onclick="showSection('quit')" aria-label="Habit Support section">💪 Habit Support</button>
  <button class="nav-btn" onclick="showSection('shopping')">🛒 Shopping</button>
  <button class="nav-btn" onclick="showSection('about')">🌿 About</button>
  <button class="nav-btn" onclick="showSection('report')">📋 Weekly Report</button>
</nav>

<div id="content">

<!-- ═══════════════════════════════════════════════════════ HOME -->
<div class="section active" id="sec-home">
  <div class="section-header">
    <h2>Good morning 🌿</h2>
    <p>Your personal 90-day recovery system. Built with care by a Project Recovery Specialist.</p>
  </div>

  <!-- Streak -->
  <div class="card">
    <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:10px;">
      <div class="card-title">Your Streak</div>
      <span class="tag tag-teal" id="streak-count">Day 1</span>
    </div>
    <div class="streak-row" id="streak-dots"></div>
    <div class="prog-bar"><div class="prog-fill" id="streak-prog" style="width:2%"></div></div>
    <p style="font-size:0.75rem;text-align:center;margin-top:4px;color:var(--dim)">90-day journey — consistency is everything</p>
  </div>

  <!-- Daily Check-In -->
  <div class="card">
    <div class="card-title">Today's Check-In</div>
    <div class="card-sub">30 seconds — log your day</div>
    <div class="track-row">
      <div><div class="track-label">💩 Bowel movement</div></div>
      <div class="rating-btns">
        <button class="rating-btn" onclick="rate(this,'bm','no')">No</button>
        <button class="rating-btn" onclick="rate(this,'bm','yes')">Yes</button>
      </div>
    </div>
    <div class="track-row">
      <div><div class="track-label">🌡 Bloating</div></div>
      <div class="rating-btns">
        <button class="rating-btn" onclick="rate(this,'bloat','1')">Low</button>
        <button class="rating-btn" onclick="rate(this,'bloat','2')">Mid</button>
        <button class="rating-btn" onclick="rate(this,'bloat','3')">Hi</button>
      </div>
    </div>
    <div class="track-row">
      <div><div class="track-label">⚡ Energy</div></div>
      <div class="rating-btns">
        <button class="rating-btn" onclick="rate(this,'energy','1')">1</button>
        <button class="rating-btn" onclick="rate(this,'energy','2')">2</button>
        <button class="rating-btn" onclick="rate(this,'energy','3')">3</button>
        <button class="rating-btn" onclick="rate(this,'energy','4')">4</button>
        <button class="rating-btn" onclick="rate(this,'energy','5')">5</button>
      </div>
    </div>
    <div class="track-row">
      <div><div class="track-label">🧠 Mood</div></div>
      <div class="rating-btns">
        <button class="rating-btn" onclick="rate(this,'mood','😔')">😔</button>
        <button class="rating-btn" onclick="rate(this,'mood','😐')">😐</button>
        <button class="rating-btn" onclick="rate(this,'mood','🙂')">🙂</button>
        <button class="rating-btn" onclick="rate(this,'mood','😊')">😊</button>
      </div>
    </div>
    <div class="track-row">
      <div><div class="track-label">💧 Water (oz)</div></div>
      <input class="num-input" type="number" id="water-oz" placeholder="0" min="0" max="200" onchange="saveInput('water',this.value)">
    </div>
    <button class="btn btn-teal btn-full" style="margin-top:12px" onclick="saveCheckin()">Save Today ✓</button>
  </div>

  <!-- Quick Tools shortcut -->
  <div class="card">
    <div class="card-title">Quick Tools — 1 to 3 min</div>
    <div class="card-sub">Tap to reset your nervous system fast</div>
    <div class="tool-grid">
      <div class="tool-btn" onclick="showSection('tools');openTool('478')"><div class="tool-icon">🌬</div><div class="tool-name">4-7-8 Breathing</div></div>
      <div class="tool-btn" onclick="showSection('tools');openTool('hum')"><div class="tool-icon">🎵</div><div class="tool-name">Hum & Shake</div></div>
      <div class="tool-btn" onclick="showSection('tools');openTool('box')"><div class="tool-icon">⬜</div><div class="tool-name">Box Breathing</div></div>
      <div class="tool-btn" onclick="showSection('tools');openTool('belly')"><div class="tool-icon">🤲</div><div class="tool-name">Belly Massage</div></div>
      <div class="tool-btn" onclick="showSection('tools');openTool('shake')"><div class="tool-icon">🫨</div><div class="tool-name">Shake It Off</div></div>
      <div class="tool-btn" onclick="showSection('tools');openTool('tram')"><div class="tool-icon">🦘</div><div class="tool-name">Mini Trampoline</div></div>
    </div>
  </div>

  <!-- Today's tip -->
  <div class="card" style="border-color:var(--teal);background:rgba(29,158,117,0.06)">
    <div class="card-title" style="color:var(--teal)">Today's Reminder 💚</div>
    <p id="daily-tip" style="color:var(--white);font-size:0.92rem;font-style:italic">"Consistency beats perfection every single time."</p>
  </div>

  <a href="https://www.youtube.com/@broadvirtualo-wellness2024/videos" target="_blank" class="mh-link" style="border-color:var(--teal);background:rgba(29,158,117,0.05);margin-bottom:4px">
    <div class="mh-link-info">
      <h4 style="color:var(--teal)">▶ Recovery Companion Series — YouTube</h4>
      <p>Free guided videos · New sessions every week · Breathing · Strength · Stretching · Nervous system</p>
    </div>
    <span class="mh-arrow" style="color:var(--teal)">▶</span>
  </a>
</div>

<!-- ═══════════════════════════════════════════════════════ ASSESSMENT -->
<div class="section" id="sec-assess">
  <div class="section-header">
    <h2>Health Assessment 📋</h2>
    <p>Understand where you are today. No judgment — just data.</p>
  </div>

  <div class="card">
    <div class="card-title">Where I Am Today 🌿</div>
    <div class="card-sub">Check all that apply. No judgment — this is just your starting point.</div>

    <div style="font-size:0.78rem;font-weight:600;color:var(--muted);letter-spacing:0.05em;text-transform:uppercase;margin:10px 0 6px">Smoking</div>
    <div class="checkbox-row"><input type="checkbox" id="h-smoke-1" name="smoke-status" onchange="saveHabitLevel('smoke','current')"><label for="h-smoke-1" style="cursor:pointer;color:var(--white);margin:0">I currently smoke</label></div>
    <div class="checkbox-row"><input type="checkbox" id="h-smoke-2" name="smoke-status" onchange="saveHabitLevel('smoke','cutting')"><label for="h-smoke-2" style="cursor:pointer;color:var(--white);margin:0">I am seeking to cut down on smoking</label></div>
    <div class="checkbox-row"><input type="checkbox" id="h-smoke-3" name="smoke-status" onchange="saveHabitLevel('smoke','quit')"><label for="h-smoke-3" style="cursor:pointer;color:var(--white);margin:0">I have quit smoking</label></div>

    <div style="font-size:0.78rem;font-weight:600;color:var(--muted);letter-spacing:0.05em;text-transform:uppercase;margin:14px 0 6px">Alcohol</div>
    <div class="checkbox-row"><input type="checkbox" id="h-alc-1" onchange="saveHabitLevel('alcohol','current')"><label for="h-alc-1" style="cursor:pointer;color:var(--white);margin:0">I currently drink alcohol regularly</label></div>
    <div class="checkbox-row"><input type="checkbox" id="h-alc-2" onchange="saveHabitLevel('alcohol','cutting')"><label for="h-alc-2" style="cursor:pointer;color:var(--white);margin:0">I am seeking to cut down on alcohol</label></div>
    <div class="checkbox-row"><input type="checkbox" id="h-alc-3" onchange="saveHabitLevel('alcohol','quit')"><label for="h-alc-3" style="cursor:pointer;color:var(--white);margin:0">I have quit alcohol</label></div>

    <div style="font-size:0.78rem;font-weight:600;color:var(--muted);letter-spacing:0.05em;text-transform:uppercase;margin:14px 0 6px">Substances</div>
    <div class="checkbox-row"><input type="checkbox" id="h-sub-1" onchange="saveHabitLevel('substance','current')"><label for="h-sub-1" style="cursor:pointer;color:var(--white);margin:0">I currently use substances (cannabis, other)</label></div>
    <div class="checkbox-row"><input type="checkbox" id="h-sub-2" onchange="saveHabitLevel('substance','cutting')"><label for="h-sub-2" style="cursor:pointer;color:var(--white);margin:0">I am seeking to cut down on substance use</label></div>
    <div class="checkbox-row"><input type="checkbox" id="h-sub-3" onchange="saveHabitLevel('substance','quit')"><label for="h-s
