##About Me
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>GitHub Bio Generator</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;700&family=Syne:wght@400;700;800&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0a0f;
    --surface: #111118;
    --border: #1e1e2e;
    --accent: #00ff9d;
    --accent2: #ff6b6b;
    --accent3: #a78bfa;
    --text: #e2e8f0;
    --muted: #4a5568;
    --card: #13131f;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'JetBrains Mono', monospace;
    min-height: 100vh;
    padding: 40px 20px;
    position: relative;
    overflow-x: hidden;
  }

  body::before {
    content: '';
    position: fixed;
    top: -50%;
    left: -50%;
    width: 200%;
    height: 200%;
    background: radial-gradient(ellipse at 30% 20%, rgba(0,255,157,0.04) 0%, transparent 50%),
                radial-gradient(ellipse at 70% 80%, rgba(167,139,250,0.04) 0%, transparent 50%);
    pointer-events: none;
    z-index: 0;
  }

  .container {
    max-width: 720px;
    margin: 0 auto;
    position: relative;
    z-index: 1;
  }

  header {
    margin-bottom: 40px;
    animation: fadeDown 0.6s ease both;
  }

  .tag {
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 3px;
    text-transform: uppercase;
    margin-bottom: 12px;
    opacity: 0.8;
  }

  h1 {
    font-family: 'Syne', sans-serif;
    font-size: clamp(28px, 5vw, 42px);
    font-weight: 800;
    line-height: 1.1;
    color: var(--text);
  }

  h1 span {
    color: var(--accent);
    position: relative;
  }

  .subtitle {
    margin-top: 10px;
    color: var(--muted);
    font-size: 13px;
  }

  .form-section {
    display: flex;
    flex-direction: column;
    gap: 20px;
    margin-bottom: 32px;
    animation: fadeUp 0.6s 0.1s ease both;
  }

  .field {
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  label {
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 2px;
    text-transform: uppercase;
  }

  input, select {
    background: var(--card);
    border: 1px solid var(--border);
    color: var(--text);
    font-family: 'JetBrains Mono', monospace;
    font-size: 13px;
    padding: 12px 16px;
    border-radius: 8px;
    outline: none;
    transition: border-color 0.2s, box-shadow 0.2s;
    width: 100%;
  }

  input:focus, select:focus {
    border-color: var(--accent);
    box-shadow: 0 0 0 3px rgba(0,255,157,0.08);
  }

  input::placeholder { color: var(--muted); }

  select option { background: var(--card); }

  .chips-label {
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-bottom: 8px;
    display: block;
  }

  .chips {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .chip {
    padding: 6px 14px;
    border-radius: 100px;
    border: 1px solid var(--border);
    background: var(--card);
    color: var(--muted);
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    cursor: pointer;
    transition: all 0.15s;
    user-select: none;
  }

  .chip:hover { border-color: var(--accent3); color: var(--accent3); }
  .chip.active { background: rgba(0,255,157,0.08); border-color: var(--accent); color: var(--accent); }

  .generate-btn {
    background: var(--accent);
    color: #000;
    border: none;
    font-family: 'Syne', sans-serif;
    font-size: 15px;
    font-weight: 700;
    padding: 14px 32px;
    border-radius: 8px;
    cursor: pointer;
    width: 100%;
    letter-spacing: 1px;
    transition: transform 0.15s, box-shadow 0.15s;
    margin-top: 4px;
  }

  .generate-btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 24px rgba(0,255,157,0.25);
  }

  .generate-btn:active { transform: translateY(0); }

  .generate-btn:disabled {
    opacity: 0.4;
    cursor: not-allowed;
    transform: none;
    box-shadow: none;
  }

  .results {
    display: flex;
    flex-direction: column;
    gap: 16px;
    animation: fadeUp 0.4s ease both;
  }

  .results-header {
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-bottom: 4px;
  }

  .bio-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 20px;
    position: relative;
    transition: border-color 0.2s;
    animation: fadeUp 0.4s ease both;
  }

  .bio-card:hover { border-color: var(--accent3); }

  .bio-card-label {
    font-size: 10px;
    color: var(--accent3);
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-bottom: 12px;
  }

  .bio-text {
    font-size: 14px;
    color: var(--text);
    line-height: 1.7;
    white-space: pre-wrap;
  }

  .copy-btn {
    position: absolute;
    top: 16px;
    right: 16px;
    background: transparent;
    border: 1px solid var(--border);
    color: var(--muted);
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    padding: 4px 12px;
    border-radius: 6px;
    cursor: pointer;
    transition: all 0.15s;
    letter-spacing: 1px;
  }

  .copy-btn:hover { border-color: var(--accent); color: var(--accent); }
  .copy-btn.copied { border-color: var(--accent); color: var(--accent); }

  .loading {
    display: flex;
    align-items: center;
    gap: 12px;
    color: var(--muted);
    font-size: 13px;
    padding: 24px 0;
  }

  .dot-loader span {
    display: inline-block;
    width: 6px;
    height: 6px;
    background: var(--accent);
    border-radius: 50%;
    animation: bounce 1s infinite;
  }
  .dot-loader span:nth-child(2) { animation-delay: 0.15s; }
  .dot-loader span:nth-child(3) { animation-delay: 0.3s; }

  .char-counter {
    font-size: 11px;
    color: var(--muted);
    text-align: right;
    margin-top: 4px;
  }

  .char-counter.over { color: var(--accent2); }

  .divider {
    border: none;
    border-top: 1px solid var(--border);
    margin: 8px 0 24px;
  }

  @keyframes fadeDown { from { opacity: 0; transform: translateY(-16px); } to { opacity: 1; transform: none; } }
  @keyframes fadeUp { from { opacity: 0; transform: translateY(16px); } to { opacity: 1; transform: none; } }
  @keyframes bounce { 0%, 100% { transform: translateY(0); } 50% { transform: translateY(-6px); } }
</style>
</head>
<body>
<div class="container">
  <header>
    <p class="tag">// bio generator</p>
    <h1>Make your GitHub<br><span>actually cool</span></h1>
    <p class="subtitle">fill in the blanks. get a bio that doesn't suck.</p>
  </header>

  <div class="form-section">
    <div class="field">
      <label>your name / handle</label>
      <input type="text" id="name" placeholder="voidirl" maxlength="30" value="rishav">
    </div>

    <div class="field">
      <label>what are you building?</label>
      <input type="text" id="building" placeholder="a CLI tool, a game engine, my sanity..." maxlength="60">
    </div>

    <div class="field">
      <label>your main stack</label>
      <input type="text" id="stack" placeholder="TypeScript, Rust, Python..." maxlength="60">
    </div>

    <div class="field">
      <label>one thing you avoid</label>
      <input type="text" id="avoid" placeholder="CSS, meetings, touching grass..." maxlength="40">
    </div>

    <div class="field">
      <span class="chips-label">vibe</span>
      <div class="chips" id="vibe-chips">
        <div class="chip active" data-value="witty">witty</div>
        <div class="chip" data-value="mysterious">mysterious</div>
        <div class="chip" data-value="self-deprecating">self-deprecating</div>
        <div class="chip" data-value="chaotic">chaotic</div>
        <div class="chip" data-value="based">based</div>
      </div>
    </div>

    <div class="field">
      <span class="chips-label">emoji usage</span>
      <div class="chips" id="emoji-chips">
        <div class="chip active" data-value="some">some</div>
        <div class="chip" data-value="none">none</div>
        <div class="chip" data-value="chaotic amount">chaotic amount</div>
      </div>
    </div>

    <button class="generate-btn" id="gen-btn" onclick="generate()">generate bio →</button>
  </div>

  <div id="output"></div>
</div>

<script>
  // Chip selection
  document.querySelectorAll('.chips').forEach(group => {
    group.querySelectorAll('.chip').forEach(chip => {
      chip.addEventListener('click', () => {
        group.querySelectorAll('.chip').forEach(c => c.classList.remove('active'));
        chip.classList.add('active');
      });
    });
  });

  function getChipValue(id) {
    const active = document.querySelector(`#${id} .chip.active`);
    return active ? active.dataset.value : '';
  }

  async function generate() {
    const name = document.getElementById('name').value.trim();
    const building = document.getElementById('building').value.trim();
    const stack = document.getElementById('stack').value.trim();
    const avoid = document.getElementById('avoid').value.trim();
    const vibe = getChipValue('vibe-chips');
    const emoji = getChipValue('emoji-chips');

    const btn = document.getElementById('gen-btn');
    const output = document.getElementById('output');

    btn.disabled = true;
    output.innerHTML = `
      <div class="loading">
        <div class="dot-loader"><span></span><span></span><span></span></div>
        cooking something good...
      </div>`;

    const prompt = `Generate 3 GitHub profile "About" bio variants for a developer. Each should be short (1-3 lines max, ideally under 160 chars), witty, and memorable.

Details:
- Name/handle: ${name || 'a developer'}
- Start each bio with: "Hii, I'm ${name || 'rishav'} —" then continue naturally
- Currently building: ${building || 'something cool'}
- Tech stack: ${stack || 'various technologies'}
- Thing they avoid: ${avoid || 'boring stuff'}
- Vibe: ${vibe}
- Emoji usage: ${emoji}

Return ONLY a JSON array with exactly 3 objects, each with:
- "label": short style label (e.g. "dry wit", "chaotic energy", "mystery arc")
- "bio": the actual bio text

No markdown, no explanation, just raw JSON array.`;

    try {
      const res = await fetch("https://api.anthropic.com/v1/messages", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({
          model: "claude-sonnet-4-20250514",
          max_tokens: 1000,
          messages: [{ role: "user", content: prompt }]
        })
      });

      const data = await res.json();
      const raw = data.content.map(i => i.text || '').join('');
      const clean = raw.replace(/```json|```/g, '').trim();
      const bios = JSON.parse(clean);

      output.innerHTML = `<p class="results-header">// your bios</p><hr class="divider"><div class="results" id="bio-list"></div>`;
      const list = document.getElementById('bio-list');

      bios.forEach((b, i) => {
        const len = b.bio.length;
        const over = len > 160;
        const card = document.createElement('div');
        card.className = 'bio-card';
        card.style.animationDelay = `${i * 0.1}s`;
        card.innerHTML = `
          <p class="bio-card-label">${b.label}</p>
          <button class="copy-btn" onclick="copyBio(this, ${JSON.stringify(b.bio)})">copy</button>
          <p class="bio-text">${b.bio}</p>
          <p class="char-counter ${over ? 'over' : ''}">${len}/160 chars${over ? ' ⚠ a bit long' : ''}</p>`;
        list.appendChild(card);
      });

    } catch (e) {
      output.innerHTML = `<div class="loading" style="color:#ff6b6b">something broke. try again?</div>`;
    }

    btn.disabled = false;
  }

  function copyBio(btn, text) {
    navigator.clipboard.writeText(text).then(() => {
      btn.textContent = 'copied!';
      btn.classList.add('copied');
      setTimeout(() => { btn.textContent = 'copy'; btn.classList.remove('copied'); }, 2000);
    });
  }
</script>
</body>
</html>
## 🌐 Socials:
[![Instagram](https://img.shields.io/badge/Instagram-%23E4405F.svg?logo=Instagram&logoColor=white)](https://instagram.com/risahv_chambyal) [![LinkedIn](https://img.shields.io/badge/LinkedIn-%230077B5.svg?logo=linkedin&logoColor=white)](https://linkedin.com/in/rishav-rajput-213112361) [![email](https://img.shields.io/badge/Email-D14836?logo=gmail&logoColor=white)](mailto:rishavrajput204@gmail.com) 

# 💻 Tech Stack:
![C](https://img.shields.io/badge/c-%2300599C.svg?style=plastic&logo=c&logoColor=white) ![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=plastic&logo=openjdk&logoColor=white) ![C++](https://img.shields.io/badge/c++-%2300599C.svg?style=plastic&logo=c%2B%2B&logoColor=white) ![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=plastic&logo=javascript&logoColor=%23F7DF1E) ![Python](https://img.shields.io/badge/python-3670A0?style=plastic&logo=python&logoColor=ffdd54) ![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=plastic&logo=amazon-aws&logoColor=white) ![Flask](https://img.shields.io/badge/flask-%23000.svg?style=plastic&logo=flask&logoColor=white) ![Spring](https://img.shields.io/badge/spring-%236DB33F.svg?style=plastic&logo=spring&logoColor=white) ![Streamlit](https://img.shields.io/badge/Streamlit-%23FE4B4B.svg?style=plastic&logo=streamlit&logoColor=white) ![Apache Maven](https://img.shields.io/badge/Apache%20Maven-C71A36?style=plastic&logo=Apache%20Maven&logoColor=white) ![Apache Tomcat](https://img.shields.io/badge/apache%20tomcat-%23F8DC75.svg?style=plastic&logo=apache-tomcat&logoColor=black) ![MySQL](https://img.shields.io/badge/mysql-4479A1.svg?style=plastic&logo=mysql&logoColor=white) ![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=plastic&logo=pandas&logoColor=white) ![PyTorch](https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?style=plastic&logo=PyTorch&logoColor=white) ![scikit-learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=plastic&logo=scikit-learn&logoColor=white) ![TensorFlow](https://img.shields.io/badge/TensorFlow-%23FF6F00.svg?style=plastic&logo=TensorFlow&logoColor=white) ![Git](https://img.shields.io/badge/git-%23F05033.svg?style=plastic&logo=git&logoColor=white) ![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=plastic&logo=github&logoColor=white) ![Postman](https://img.shields.io/badge/Postman-FF6C37?style=plastic&logo=postman&logoColor=white)
# 📊 GitHub Stats:
![](https://github-readme-stats.vercel.app/api?username=voidirl&theme=cobalt&hide_border=false&include_all_commits=true&count_private=true)<br/>
![](https://nirzak-streak-stats.vercel.app/?user=voidirl&theme=cobalt&hide_border=false)<br/>
![](https://github-readme-stats.vercel.app/api/top-langs/?username=voidirl&theme=cobalt&hide_border=false&include_all_commits=true&count_private=true&layout=compact)

---
[![](https://visitcount.itsvg.in/api?id=voidirl&icon=0&color=0)](https://visitcount.itsvg.in)

<!-- Proudly created with GPRM ( https://gprm.itsvg.in ) -->
