<html>
<head>
<style>
* { margin:0; padding:0; box-sizing:border-box; }

body {
  background: #050505;
  color: #e6e6e6;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  overflow-x: hidden;
}

.starfield {
  position: fixed;
  inset: 0;
  pointer-events: none;
  z-index: 0;
}

.star {
  position: absolute;
  background: #fff;
  border-radius: 50%;
}

.star.s1 { width:1px; height:1px; opacity:0.5; }
.star.s2 { width:2px; height:2px; opacity:0.7; }
.star.s3 { width:3px; height:3px; opacity:0.9; box-shadow:0 0 4px rgba(255,255,255,0.6); }

.twinkle { animation: tw 4s ease-in-out infinite; }
@keyframes tw { 0%,100%{opacity:0.2;} 50%{opacity:1;} }

.shooting {
  position: absolute;
  width: 90px;
  height: 1px;
  background: linear-gradient(90deg, rgba(255,255,255,0.9), transparent);
  transform: rotate(-30deg);
  animation: shoot 6s linear infinite;
  opacity: 0;
}

@keyframes shoot {
  0% { opacity: 0; transform: translate(0,0) rotate(-30deg); }
  5% { opacity: 1; }
  15% { opacity: 0; transform: translate(-300px, 180px) rotate(-30deg); }
  100% { opacity: 0; }
}

.container {
  position: relative;
  z-index: 1;
  max-width: 860px;
  margin: 0 auto;
  padding: 90px 40px 60px;
}

.hero {
  text-align: center;
  margin-bottom: 70px;
}

.hero-name {
  font-size: 56px;
  font-weight: 700;
  letter-spacing: 6px;
  text-transform: uppercase;
  background: linear-gradient(180deg, #ffffff 0%, #8a8a8a 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  line-height: 1;
}

.hero-sub {
  margin-top: 14px;
  font-size: 13px;
  letter-spacing: 4px;
  text-transform: uppercase;
  color: #6b6b6b;
}

.hero-rule {
  width: 40px;
  height: 1px;
  background: rgba(255,255,255,0.25);
  margin: 28px auto 0;
}

.terminal {
  margin: 40px auto 0;
  max-width: 460px;
  border: 1px solid rgba(255,255,255,0.1);
  border-radius: 6px;
  background: rgba(255,255,255,0.015);
  padding: 14px 18px;
  font-family: 'Courier New', monospace;
  font-size: 13px;
  color: #9fdfff;
  text-align: left;
  min-height: 20px;
}

.cursor {
  display: inline-block;
  width: 7px;
  height: 13px;
  background: #9fdfff;
  margin-left: 2px;
  animation: blink 1s step-start infinite;
  vertical-align: middle;
}
@keyframes blink { 50% { opacity: 0; } }

.section {
  margin-bottom: 64px;
}

.section-label {
  font-size: 11px;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: #666;
  margin-bottom: 18px;
  display: flex;
  align-items: center;
  gap: 12px;
}

.section-label::after {
  content: '';
  flex: 1;
  height: 1px;
  background: rgba(255,255,255,0.08);
}

.bio-text {
  font-size: 15px;
  color: #a3a3a3;
  line-height: 1.85;
  max-width: 640px;
}

.bio-list {
  margin-top: 22px;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px 24px;
}

.bio-item {
  font-size: 13.5px;
  color: #8a8a8a;
  padding-left: 14px;
  position: relative;
}

.bio-item::before {
  content: '';
  position: absolute;
  left: 0;
  top: 8px;
  width: 4px;
  height: 4px;
  background: #555;
  transform: rotate(45deg);
}

.icon-row {
  display: flex;
  flex-wrap: wrap;
  gap: 22px;
  align-items: center;
  margin-bottom: 26px;
}

.icon-row img {
  width: 34px;
  height: 34px;
  opacity: 0.85;
  filter: grayscale(15%);
  transition: opacity 0.2s ease, transform 0.2s ease;
}

.icon-row img:hover {
  opacity: 1;
  transform: translateY(-2px);
}

.infra-line {
  font-size: 13px;
  color: #777;
  letter-spacing: 0.3px;
  padding-top: 16px;
  border-top: 1px solid rgba(255,255,255,0.06);
}

.infra-line span {
  color: #9fdfff;
}

.interests {
  font-size: 14px;
  color: #8f8f8f;
  line-height: 1.9;
  max-width: 640px;
}

.footer {
  text-align: center;
  margin-top: 70px;
  padding-top: 30px;
  border-top: 1px solid rgba(255,255,255,0.06);
}

.footer-star {
  font-size: 18px;
  color: #666;
  margin-bottom: 10px;
}

.footer-text {
  font-size: 12px;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: #555;
}

@media (max-width: 620px) {
  .hero-name { font-size: 38px; letter-spacing: 3px; }
  .bio-list { grid-template-columns: 1fr; }
}
</style>
</head>
<body>

<div class="starfield" id="starfield"></div>

<div class="container">

  <div class="hero">
    <div class="hero-name">fredo</div>
    <div class="hero-sub">systems in orbit, code on the ground</div>
    <div class="hero-rule"></div>
    <div class="terminal" id="terminal"><span class="cursor"></span></div>
  </div>

  <div class="section">
    <div class="section-label">who i am</div>
    <p class="bio-text">
      I build and run Discord bots and self-hosted web services end to end, from the code to the server they live on. Most of it runs on my own home server, orchestrated with PM2 and Docker Compose, sitting behind Caddy with Cloudflare handling DNS and tunneling.
    </p>
    <div class="bio-list">
      <div class="bio-item">Python and JavaScript as daily drivers</div>
      <div class="bio-item">Discord bots with discord.py and discord.js</div>
      <div class="bio-item">APIs and backends with FastAPI</div>
      <div class="bio-item">Linux administration and deployment pipelines</div>
    </div>
  </div>

  <div class="section">
    <div class="section-label">languages and tools</div>
    <div class="icon-row">
      <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" title="Python">
      <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/nodejs/nodejs-original-wordmark.svg" alt="nodejs" title="Node.js">
      <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/react/react-original-wordmark.svg" alt="react" title="React">
      <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/docker/docker-original-wordmark.svg" alt="docker" title="Docker">
      <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/linux/linux-original.svg" alt="linux" title="Linux">
      <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mongodb/mongodb-original-wordmark.svg" alt="mongodb" title="MongoDB">
      <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mysql/mysql-original-wordmark.svg" alt="mysql" title="MySQL">
      <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/postgresql/postgresql-original-wordmark.svg" alt="postgresql" title="PostgreSQL">
      <img src="https://www.vectorlogo.zone/logos/sqlite/sqlite-icon.svg" alt="sqlite" title="SQLite">
      <img src="https://www.vectorlogo.zone/logos/git-scm/git-scm-icon.svg" alt="git" title="Git">
      <img src="https://www.vectorlogo.zone/logos/gnu_bash/gnu_bash-icon.svg" alt="bash" title="Bash">
      <img src="https://www.vectorlogo.zone/logos/figma/figma-icon.svg" alt="figma" title="Figma">
    </div>
    <div class="infra-line">
      infra &mdash; <span>PM2</span> &middot; <span>Docker Compose</span> &middot; <span>Caddy</span> &middot; <span>Cloudflare</span>
    </div>
  </div>

  <div class="section">
    <div class="section-label">outside of code</div>
    <p class="interests">
      Deep in Discord server communities. Minecraft. Anime. The occasional blackjack strategy rabbit hole. Tinkering with robotics and 3D printing. Unapologetic LARP enjoyer.
    </p>
  </div>

  <div class="footer">
    <div class="footer-star">&#10022;</div>
    <div class="footer-text">always tinkering on fredoserver1</div>
  </div>

</div>

<script>
  function createStarfield() {
    const field = document.getElementById('starfield');
    const count = 140;
    for (let i = 0; i < count; i++) {
      const star = document.createElement('div');
      const r = Math.random();
      star.className = 'star ' + (r < 0.55 ? 's1' : r < 0.85 ? 's2' : 's3');
      if (Math.random() > 0.6) star.classList.add('twinkle');
      star.style.left = Math.random() * 100 + '%';
      star.style.top = Math.random() * 100 + '%';
      star.style.animationDelay = (Math.random() * 4) + 's';
      field.appendChild(star);
    }
    for (let i = 0; i < 3; i++) {
      const sh = document.createElement('div');
      sh.className = 'shooting';
      sh.style.top = (Math.random() * 40) + '%';
      sh.style.left = (60 + Math.random() * 30) + '%';
      sh.style.animationDelay = (i * 3.5) + 's';
      field.appendChild(sh);
    }
  }
  createStarfield();

  function typeTerminal() {
    const el = document.getElementById('terminal');
    const lines = [
      'building self-hosted services',
      'discord bots with discord.py + discord.js',
      'fastapi + pm2 + docker + caddy'
    ];
    let li = 0, ci = 0;
    const cursor = '<span class="cursor"></span>';

    function typeLine() {
      if (li >= lines.length) { li = 0; el.innerHTML = cursor; ci = 0; setTimeout(typeLine, 600); return; }
      const line = lines[li];
      if (ci <= line.length) {
        el.innerHTML = line.slice(0, ci) + cursor;
        ci++;
        setTimeout(typeLine, 45);
      } else {
        setTimeout(() => {
          li++; ci = 0;
          el.innerHTML = cursor;
          setTimeout(typeLine, 200);
        }, 1400);
      }
    }
    typeLine();
  }
  typeTerminal();
</script>

</body>
</html>
