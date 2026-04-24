<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Yashraj Sahu — GitHub Profile</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:ital,wght@0,300;0,400;0,500;0,700;1,400&family=Fira+Code:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0d1117;
    --bg2: #161b22;
    --bg3: #21262d;
    --border: #30363d;
    --green: #39d353;
    --green2: #26a641;
    --green3: #006d32;
    --cyan: #79c0ff;
    --yellow: #e3b341;
    --red: #ff7b72;
    --purple: #d2a8ff;
    --orange: #ffa657;
    --white: #e6edf3;
    --muted: #8b949e;
    --prompt: #3fb950;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--white);
    font-family: 'JetBrains Mono', monospace;
    min-height: 100vh;
    padding: 24px;
    line-height: 1.6;
  }

  /* CRT scanline overlay */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,0,0,0.03) 2px,
      rgba(0,0,0,0.03) 4px
    );
    pointer-events: none;
    z-index: 999;
  }

  .terminal-window {
    max-width: 820px;
    margin: 0 auto;
    border: 1px solid var(--border);
    border-radius: 10px;
    overflow: hidden;
    box-shadow: 0 0 0 1px #000,
                0 20px 60px rgba(0,0,0,0.6),
                0 0 80px rgba(57,211,83,0.05);
    animation: fadeUp 0.6s ease both;
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  /* Title bar */
  .titlebar {
    background: var(--bg3);
    border-bottom: 1px solid var(--border);
    padding: 12px 16px;
    display: flex;
    align-items: center;
    gap: 12px;
    user-select: none;
  }

  .dots { display: flex; gap: 7px; }
  .dot {
    width: 12px; height: 12px;
    border-radius: 50%;
  }
  .dot.red    { background: #ff5f57; }
  .dot.yellow { background: #febc2e; }
  .dot.green  { background: #28c840; }

  .titlebar-text {
    flex: 1;
    text-align: center;
    font-size: 12px;
    color: var(--muted);
    letter-spacing: 0.04em;
  }

  /* Body */
  .terminal-body {
    background: var(--bg);
    padding: 28px 32px;
  }

  /* Header */
  .header {
    margin-bottom: 28px;
    animation: fadeUp 0.6s 0.1s ease both;
  }

  .header-name {
    font-size: 28px;
    font-weight: 700;
    color: var(--green);
    text-shadow: 0 0 20px rgba(57,211,83,0.4);
    letter-spacing: -0.02em;
  }

  .header-sub {
    font-size: 13px;
    color: var(--muted);
    margin-top: 4px;
  }

  .header-sub span { color: var(--cyan); }

  /* Divider */
  .divider {
    border: none;
    border-top: 1px solid var(--border);
    margin: 22px 0;
  }

  /* Section label */
  .section-label {
    font-size: 11px;
    font-weight: 500;
    color: var(--muted);
    letter-spacing: 0.12em;
    text-transform: uppercase;
    margin-bottom: 14px;
  }

  /* Command blocks */
  .cmd-block {
    margin-bottom: 20px;
    animation: fadeUp 0.5s ease both;
  }

  .prompt-line {
    display: flex;
    align-items: baseline;
    gap: 8px;
    margin-bottom: 4px;
  }

  .prompt-user { color: var(--green); font-weight: 600; }
  .prompt-at   { color: var(--muted); }
  .prompt-host { color: var(--cyan); font-weight: 500; }
  .prompt-path { color: var(--purple); }
  .prompt-sym  { color: var(--yellow); font-weight: 700; margin-right: 4px; }
  .prompt-cmd  { color: var(--white); }

  .cmd-flag  { color: var(--orange); }
  .cmd-val   { color: var(--yellow); }
  .cmd-str   { color: var(--green); }

  .output {
    padding: 12px 16px;
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 6px;
    font-size: 13.5px;
    color: var(--white);
    margin-top: 6px;
  }

  .output-row {
    display: flex;
    gap: 10px;
    padding: 3px 0;
    line-height: 1.5;
  }

  .out-key {
    color: var(--cyan);
    min-width: 90px;
    flex-shrink: 0;
  }

  .out-sep { color: var(--muted); }
  .out-val { color: var(--white); }
  .out-comment { color: var(--muted); font-style: italic; }

  /* Stack grid */
  .stack-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(170px, 1fr));
    gap: 10px;
    margin-top: 8px;
  }

  .stack-card {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 10px 14px;
    display: flex;
    align-items: center;
    gap: 10px;
    transition: border-color 0.2s, box-shadow 0.2s;
    cursor: default;
  }

  .stack-card:hover {
    border-color: var(--green3);
    box-shadow: 0 0 12px rgba(57,211,83,0.1);
  }

  .stack-icon {
    width: 22px;
    height: 22px;
    border-radius: 4px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 14px;
    flex-shrink: 0;
  }

  .stack-name { font-size: 13px; color: var(--white); font-weight: 500; }
  .stack-tag  { font-size: 11px; color: var(--muted); margin-top: 1px; }

  /* DSA progress */
  .progress-section { margin-top: 8px; }

  .topic-row {
    display: grid;
    grid-template-columns: 140px 1fr 45px;
    align-items: center;
    gap: 12px;
    padding: 6px 0;
    border-bottom: 1px solid rgba(48,54,61,0.5);
  }

  .topic-row:last-child { border-bottom: none; }

  .topic-name { font-size: 12.5px; color: var(--cyan); }

  .bar-track {
    height: 6px;
    background: var(--bg3);
    border-radius: 99px;
    overflow: hidden;
    border: 1px solid var(--border);
  }

  .bar-fill {
    height: 100%;
    border-radius: 99px;
    background: linear-gradient(90deg, var(--green3), var(--green));
    box-shadow: 0 0 6px rgba(57,211,83,0.4);
    width: 0;
    transition: width 1.2s cubic-bezier(0.4,0,0.2,1);
  }

  .bar-pct { font-size: 11px; color: var(--muted); text-align: right; }

  /* Contribution graph */
  .contrib-grid {
    display: grid;
    grid-template-columns: repeat(52, 1fr);
    gap: 2px;
    margin-top: 8px;
  }

  .contrib-cell {
    aspect-ratio: 1;
    border-radius: 2px;
    background: var(--bg3);
  }

  .c0 { background: var(--bg3); }
  .c1 { background: var(--green3); }
  .c2 { background: var(--green2); }
  .c3 { background: var(--green); box-shadow: 0 0 4px rgba(57,211,83,0.3); }
  .c4 { background: #56e368; box-shadow: 0 0 6px rgba(86,227,104,0.5); }

  /* Connect section */
  .connect-row {
    display: flex;
    gap: 10px;
    flex-wrap: wrap;
    margin-top: 8px;
  }

  .connect-link {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 8px 14px;
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 6px;
    text-decoration: none;
    color: var(--white);
    font-size: 13px;
    font-family: 'JetBrains Mono', monospace;
    transition: border-color 0.2s, color 0.2s;
  }

  .connect-link:hover { border-color: var(--cyan); color: var(--cyan); }

  /* Cursor blink */
  .cursor {
    display: inline-block;
    width: 9px;
    height: 16px;
    background: var(--green);
    border-radius: 1px;
    vertical-align: middle;
    margin-left: 2px;
    animation: blink 1.1s step-end infinite;
    box-shadow: 0 0 8px rgba(57,211,83,0.7);
  }

  @keyframes blink {
    0%, 100% { opacity: 1; }
    50%       { opacity: 0; }
  }

  /* Status bar */
  .statusbar {
    background: var(--green);
    padding: 4px 16px;
    display: flex;
    align-items: center;
    gap: 16px;
    font-size: 11.5px;
    color: #0d1117;
    font-weight: 600;
  }

  .status-seg { display: flex; align-items: center; gap: 5px; }
  .status-sep { color: rgba(0,0,0,0.35); }

  /* Animations staggered */
  .cmd-block:nth-child(1) { animation-delay: 0.15s; }
  .cmd-block:nth-child(2) { animation-delay: 0.25s; }
  .cmd-block:nth-child(3) { animation-delay: 0.35s; }
  .cmd-block:nth-child(4) { animation-delay: 0.45s; }
  .cmd-block:nth-child(5) { animation-delay: 0.55s; }
  .cmd-block:nth-child(6) { animation-delay: 0.65s; }
</style>
</head>
<body>

<div class="terminal-window">

  <!-- Title bar -->
  <div class="titlebar">
    <div class="dots">
      <div class="dot red"></div>
      <div class="dot yellow"></div>
      <div class="dot green"></div>
    </div>
    <div class="titlebar-text">yashraj@github — zsh — 82×28</div>
  </div>

  <!-- Body -->
  <div class="terminal-body">

    <!-- Header -->
    <div class="header">
      <div class="header-name">Yashraj Sahu</div>
      <div class="header-sub">
        <span>18</span> &nbsp;·&nbsp; Anime &nbsp;·&nbsp; Games &nbsp;·&nbsp; Draw &nbsp;·&nbsp; Code
      </div>
    </div>

    <hr class="divider">

    <!-- whoami -->
    <div class="cmd-block">
      <div class="prompt-line">
        <span class="prompt-user">yash</span>
        <span class="prompt-at">@</span>
        <span class="prompt-host">github</span>
        <span class="prompt-path">~</span>
        <span class="prompt-sym">$</span>
        <span class="prompt-cmd">whoami</span>
      </div>
      <div class="output">
        <div class="output-row">
          <span class="out-key">name</span>
          <span class="out-sep">→</span>
          <span class="out-val">Yashraj Sahu</span>
        </div>
        <div class="output-row">
          <span class="out-key">role</span>
          <span class="out-sep">→</span>
          <span class="out-val">Student Developer</span>
        </div>
        <div class="output-row">
          <span class="out-key">college</span>
          <span class="out-sep">→</span>
          <span class="out-val">LNCT Bhopal &nbsp;<span class="out-comment">// B.Tech Yr.1</span></span>
        </div>
        <div class="output-row">
          <span class="out-key">location</span>
          <span class="out-sep">→</span>
          <span class="out-val">Bhopal, India 🇮🇳</span>
        </div>
        <div class="output-row">
          <span class="out-key">status</span>
          <span class="out-sep">→</span>
          <span class="out-val">"Still compiling..."</span>
          <span class="cursor"></span>
        </div>
      </div>
    </div>

    <!-- learning -->
    <div class="cmd-block">
      <div class="prompt-line">
        <span class="prompt-user">yash</span>
        <span class="prompt-at">@</span>
        <span class="prompt-host">github</span>
        <span class="prompt-path">~</span>
        <span class="prompt-sym">$</span>
        <span class="prompt-cmd">cat <span class="cmd-flag">currently_learning.txt</span></span>
      </div>
      <div class="output">
        <div class="output-row"><span style="color:var(--yellow)">▸</span>&nbsp; JavaScript &nbsp;<span class="out-comment">// ES6+, DOM, Projects</span></div>
        <div class="output-row"><span style="color:var(--yellow)">▸</span>&nbsp; Data Structures &amp; Algorithms &nbsp;<span class="out-comment">// Java</span></div>
        <div class="output-row"><span style="color:var(--yellow)">▸</span>&nbsp; Web Development &nbsp;<span class="out-comment">// Frontend focus</span></div>
      </div>
    </div>

    <!-- stack -->
    <div class="cmd-block">
      <div class="prompt-line">
        <span class="prompt-user">yash</span>
        <span class="prompt-at">@</span>
        <span class="prompt-host">github</span>
        <span class="prompt-path">~</span>
        <span class="prompt-sym">$</span>
        <span class="prompt-cmd">ls <span class="cmd-flag">--stack</span> <span class="cmd-val">--verbose</span></span>
      </div>
      <div class="stack-grid">
        <div class="stack-card">
          <div class="stack-icon" style="background:#ED8B00">☕</div>
          <div><div class="stack-name">Java</div><div class="stack-tag">primary lang</div></div>
        </div>
        <div class="stack-card">
          <div class="stack-icon" style="background:#F7DF1E">JS</div>
          <div><div class="stack-name">JavaScript</div><div class="stack-tag">learning</div></div>
        </div>
        <div class="stack-card">
          <div class="stack-icon" style="background:#E34F26">H5</div>
          <div><div class="stack-name">HTML5</div><div class="stack-tag">solid</div></div>
        </div>
        <div class="stack-card">
          <div class="stack-icon" style="background:#1572B6">CS</div>
          <div><div class="stack-name">CSS3</div><div class="stack-tag">solid</div></div>
        </div>
        <div class="stack-card">
          <div class="stack-icon" style="background:#FFA116">LC</div>
          <div><div class="stack-name">LeetCode</div><div class="stack-tag">on streak 🔥</div></div>
        </div>
      </div>
    </div>

    <!-- DSA Progress -->
    <div class="cmd-block">
      <div class="prompt-line">
        <span class="prompt-user">yash</span>
        <span class="prompt-at">@</span>
        <span class="prompt-host">github</span>
        <span class="prompt-path">~</span>
        <span class="prompt-sym">$</span>
        <span class="prompt-cmd">./dsa-progress <span class="cmd-flag">--lang</span>=<span class="cmd-val">java</span> <span class="cmd-flag">--show</span>=<span class="cmd-val">topics</span></span>
      </div>
      <div class="output progress-section" id="progress-output">
        <div class="topic-row">
          <span class="topic-name">Arrays</span>
          <div class="bar-track"><div class="bar-fill" data-pct="82"></div></div>
          <span class="bar-pct">82%</span>
        </div>
        <div class="topic-row">
          <span class="topic-name">Binary Search</span>
          <div class="bar-track"><div class="bar-fill" data-pct="75"></div></div>
          <span class="bar-pct">75%</span>
        </div>
        <div class="topic-row">
          <span class="topic-name">Strings</span>
          <div class="bar-track"><div class="bar-fill" data-pct="60"></div></div>
          <span class="bar-pct">60%</span>
        </div>
        <div class="topic-row">
          <span class="topic-name">Linked Lists</span>
          <div class="bar-track"><div class="bar-fill" data-pct="40"></div></div>
          <span class="bar-pct">40%</span>
        </div>
        <div class="topic-row">
          <span class="topic-name">Recursion</span>
          <div class="bar-track"><div class="bar-fill" data-pct="50"></div></div>
          <span class="bar-pct">50%</span>
        </div>
        <div class="topic-row">
          <span class="topic-name">Sorting</span>
          <div class="bar-track"><div class="bar-fill" data-pct="65"></div></div>
          <span class="bar-pct">65%</span>
        </div>
      </div>
    </div>

    <!-- Contribution graph -->
    <div class="cmd-block">
      <div class="prompt-line">
        <span class="prompt-user">yash</span>
        <span class="prompt-at">@</span>
        <span class="prompt-host">github</span>
        <span class="prompt-path">~</span>
        <span class="prompt-sym">$</span>
        <span class="prompt-cmd">git log <span class="cmd-flag">--graph</span> <span class="cmd-flag">--since</span>=<span class="cmd-val">"1 year ago"</span></span>
      </div>
      <div class="output">
        <div style="font-size:11px; color:var(--muted); margin-bottom:8px;">contributions in the last year</div>
        <div class="contrib-grid" id="contrib-grid"></div>
        <div style="display:flex; gap:6px; align-items:center; margin-top:10px; font-size:11px; color:var(--muted);">
          Less
          <div style="width:10px;height:10px;border-radius:2px;background:var(--bg3);border:1px solid var(--border)"></div>
          <div style="width:10px;height:10px;border-radius:2px;background:var(--green3)"></div>
          <div style="width:10px;height:10px;border-radius:2px;background:var(--green2)"></div>
          <div style="width:10px;height:10px;border-radius:2px;background:var(--green)"></div>
          More
        </div>
      </div>
    </div>

    <!-- Connect -->
    <div class="cmd-block">
      <div class="prompt-line">
        <span class="prompt-user">yash</span>
        <span class="prompt-at">@</span>
        <span class="prompt-host">github</span>
        <span class="prompt-path">~</span>
        <span class="prompt-sym">$</span>
        <span class="prompt-cmd">open <span class="cmd-flag">--links</span></span>
      </div>
      <div class="connect-row">
        <a class="connect-link" href="https://linkedin.com/in/yashraj-sahu-588825375" target="_blank">
          <svg width="15" height="15" viewBox="0 0 24 24" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
          linkedin
        </a>
        <a class="connect-link" href="https://github.com" target="_blank">
          <svg width="15" height="15" viewBox="0 0 24 24" fill="currentColor"><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/></svg>
          github
        </a>
        <a class="connect-link" href="https://leetcode.com" target="_blank">
          <svg width="15" height="15" viewBox="0 0 24 24" fill="currentColor"><path d="M13.483 0a1.374 1.374 0 0 0-.961.438L7.116 6.226l-3.854 4.126a5.266 5.266 0 0 0-1.209 2.104 5.35 5.35 0 0 0-.125.513 5.527 5.527 0 0 0 .062 2.362 5.83 5.83 0 0 0 .349 1.017 5.938 5.938 0 0 0 1.271 1.818l4.277 4.193.039.038c2.248 2.165 5.852 2.133 8.063-.074l2.396-2.392c.54-.54.54-1.414.003-1.955a1.378 1.378 0 0 0-1.951-.003l-2.396 2.392a3.021 3.021 0 0 1-4.205.038l-.02-.019-4.276-4.193c-.652-.64-.972-1.469-.948-2.263a2.68 2.68 0 0 1 .066-.523 2.545 2.545 0 0 1 .619-1.164L9.13 8.114c1.058-1.134 3.204-1.27 4.43-.278l3.501 2.831c.593.48 1.461.387 1.94-.207a1.384 1.384 0 0 0-.207-1.943l-3.5-2.831c-.8-.647-1.766-1.045-2.774-1.202l2.015-2.158A1.384 1.384 0 0 0 13.483 0zm-2.866 12.815a1.38 1.38 0 0 0-1.38 1.382 1.38 1.38 0 0 0 1.38 1.382H20.79a1.38 1.38 0 0 0 1.38-1.382 1.38 1.38 0 0 0-1.38-1.382z"/></svg>
          leetcode
        </a>
      </div>
    </div>

  </div><!-- /terminal-body -->

  <!-- Status bar -->
  <div class="statusbar">
    <div class="status-seg">⬡ NORMAL</div>
    <div class="status-sep">|</div>
    <div class="status-seg">yashraj@github</div>
    <div class="status-sep">|</div>
    <div class="status-seg">README.md</div>
    <div class="status-sep">|</div>
    <div class="status-seg" style="margin-left:auto">Java · DSA · WebDev</div>
  </div>

</div><!-- /terminal-window -->

<script>
  // Animate progress bars on load
  window.addEventListener('load', () => {
    setTimeout(() => {
      document.querySelectorAll('.bar-fill').forEach(bar => {
        bar.style.width = bar.dataset.pct + '%';
      });
    }, 600);
  });

  // Generate contribution graph
  const grid = document.getElementById('contrib-grid');
  const levels = [0,0,0,1,0,0,1,2,0,1,0,0,0,1,1,0,2,1,0,0,1,0,3,2,1,0,0,2,1,0,
                  0,1,2,3,1,0,0,0,1,2,0,1,1,0,3,2,1,0,2,1,0,0,1,3,2,0,0,1,0,2,
                  1,0,0,0,1,2,3,1,0,2,0,1,0,0,1,2,0,0,1,0,3,2,1,4,0,1,2,0,0,1,
                  0,2,1,0,3,2,1,0,0,1,0,0,2,1,3,0,1,2,
