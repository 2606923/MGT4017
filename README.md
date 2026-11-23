Talent Trade
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="theme-color" content="#f7f6f2" />
  <title>Talent Trade — Learn by sharing</title>
  <style>
    :root {
      --ink: #20231f;
      --muted: #73766f;
      --paper: #f7f6f2;
      --white: #fff;
      --green: #245c45;
      --green-light: #e5eee7;
      --orange: #e99360;
      --line: #e8e7e1;
      --shadow: 0 14px 40px rgba(32, 35, 31, .07);
      --radius: 20px;
    }

    * { box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body {
      margin: 0;
      color: var(--ink);
      background: var(--paper);
      font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    }
    button, input, select { font: inherit; }
    button { cursor: pointer; }
    a { color: inherit; text-decoration: none; }

    .shell { max-width: 1240px; margin: auto; padding: 0 32px; }
    .topbar {
      height: 76px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      border-bottom: 1px solid var(--line);
    }
    .brand { display: flex; align-items: center; gap: 10px; font-size: 19px; font-weight: 750; letter-spacing: -.5px; }
    .brand-mark {
      display: grid; place-items: center;
      width: 34px; height: 34px; border-radius: 11px;
      color: white; background: var(--green); font-size: 19px;
    }
    .nav { display: flex; gap: 30px; align-items: center; color: #5e625c; font-size: 14px; }
    .nav a:hover { color: var(--green); }
    .profile { display: flex; align-items: center; gap: 10px; font-size: 14px; font-weight: 650; }
    .avatar {
      display: grid; place-items: center; width: 36px; height: 36px;
      border-radius: 50%; background: #e9c7aa; color: #5f4231; font-weight: 750;
    }

    .hero {
      display: grid; grid-template-columns: 1.15fr .85fr; gap: 48px;
      align-items: center; padding: 66px 0 54px;
    }
    .eyebrow {
      display: inline-flex; align-items: center; gap: 8px;
      padding: 8px 12px; background: var(--green-light); color: var(--green);
      border-radius: 999px; font-size: 12px; font-weight: 750; letter-spacing: .04em;
      text-transform: uppercase;
    }
    h1 { margin: 18px 0 16px; max-width: 650px; font-size: clamp(42px, 5.2vw, 68px); line-height: 1.04; letter-spacing: -3.4px; }
    h1 span { color: var(--green); }
    .hero-copy { max-width: 550px; margin: 0; color: var(--muted); font-size: 17px; line-height: 1.7; }
    .hero-actions { display: flex; gap: 12px; margin-top: 28px; flex-wrap: wrap; }
    .btn {
      border: 0; border-radius: 12px; padding: 13px 18px;
      font-weight: 700; font-size: 14px; transition: .2s ease;
    }
    .btn-primary { color: white; background: var(--green); }
    .btn-primary:hover { background: #194733; transform: translateY(-1px); }
    .btn-secondary { background: white; color: var(--ink); border: 1px solid var(--line); }
    .btn-secondary:hover { border-color: #b7c8bb; }
    .hero-note { display: flex; align-items: center; gap: 9px; margin-top: 22px; color: var(--muted); font-size: 13px; }
    .mini-avatars { display: flex; }
    .mini-avatars span { display: grid; place-items: center; width: 26px; height: 26px; margin-right: -7px; border: 2px solid var(--paper); border-radius: 50%; font-size: 11px; background: #f1d2bf; }
    .mini-avatars span:nth-child(2) { background: #d7e4c9; }
    .mini-avatars span:nth-child(3) { background: #d9d4ee; }

    .hero-card {
      position: relative; min-height: 350px; padding: 26px; overflow: hidden;
      border-radius: 28px; background: #e9eee5; box-shadow: var(--shadow);
    }
    .hero-card::before, .hero-card::after {
      content: ""; position: absolute; border-radius: 50%;
      background: rgba(233, 147, 96, .24);
    }
    .hero-card::before { width: 220px; height: 220px; right: -55px; top: -50px; }
    .hero-card::after { width: 160px; height: 160px; left: -60px; bottom: -70px; background: rgba(36, 92, 69, .1); }
    .exchange-card {
      position: relative; z-index: 1; display: flex; flex-direction: column; gap: 16px;
      max-width: 360px; margin: 15px auto 0; padding: 22px;
      border: 1px solid rgba(255,255,255,.8); border-radius: 20px;
      background: rgba(255,255,255,.88); box-shadow: 0 12px 35px rgba(32,35,31,.08);
    }
    .exchange-top { display: flex; align-items: center; justify-content: space-between; }
    .exchange-title { color: var(--muted); font-size: 12px; font-weight: 700; text-transform: uppercase; letter-spacing: .07em; }
    .live-pill { color: var(--green); background: var(--green-light); border-radius: 99px; padding: 6px 9px; font-size: 11px; font-weight: 750; }
    .person-row { display: flex; align-items: center; gap: 12px; }
    .person-row .avatar { width: 42px; height: 42px; }
    .person-row strong { display: block; font-size: 14px; }
    .person-row small { display: block; margin-top: 3px; color: var(--muted); font-size: 12px; }
    .swap-line { display: flex; align-items: center; justify-content: center; gap: 12px; color: var(--green); font-size: 13px; font-weight: 750; }
    .swap-line::before, .swap-line::after { content: ""; height: 1px; flex: 1; background: var(--line); }
    .skill-chip { display: inline-flex; padding: 8px 11px; border-radius: 9px; background: #f4f3ef; font-size: 13px; font-weight: 650; }
    .floating-stat {
      position: absolute; z-index: 2; right: 12px; bottom: 20px;
      padding: 13px 16px; border-radius: 14px; background: var(--green); color: white;
      box-shadow: var(--shadow); font-size: 12px;
    }
    .floating-stat strong { display: block; margin-bottom: 3px; font-size: 20px; }

    .section { padding: 34px 0 54px; }
    .section-heading { display: flex; justify-content: space-between; align-items: end; gap: 20px; margin-bottom: 22px; }
    .section-heading h2 { margin: 0; font-size: 26px; letter-spacing: -.9px; }
    .section-heading p { margin: 7px 0 0; color: var(--muted); font-size: 14px; }
    .text-link { color: var(--green); font-size: 13px; font-weight: 750; }
    .grid { display: grid; gap: 16px; }
    .skill-grid { grid-template-columns: repeat(3, 1fr); }
    .card {
      border: 1px solid var(--line); border-radius: var(--radius);
      background: var(--white); box-shadow: 0 5px 18px rgba(32,35,31,.025);
    }
    .skill-card { padding: 20px; }
    .card-head { display: flex; justify-content: space-between; align-items: start; gap: 10px; }
    .skill-icon { display: grid; place-items: center; width: 44px; height: 44px; border-radius: 13px; background: #f3eee5; font-size: 21px; }
    .tag { padding: 6px 9px; border-radius: 99px; background: #f3f3ef; color: #656960; font-size: 11px; font-weight: 700; white-space: nowrap; }
    .skill-card h3 { margin: 16px 0 6px; font-size: 17px; }
    .skill-card p { margin: 0; color: var(--muted); font-size: 13px; line-height: 1.55; }
    .skill-meta { display: flex; align-items: center; justify-content: space-between; gap: 10px; margin-top: 18px; padding-top: 15px; border-top: 1px solid var(--line); }
    .skill-meta .person-row { gap: 8px; }
    .skill-meta .avatar { width: 30px; height: 30px; font-size: 12px; }
    .skill-meta strong { font-size: 12px; }
    .skill-meta small { font-size: 11px; }
    .small-btn { border: 1px solid #dfe6df; background: white; color: var(--green); padding: 9px 11px; border-radius: 9px; font-size: 12px; font-weight: 750; }
    .small-btn:hover { background: var(--green-light); }

    .lower-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; }
    .panel { padding: 23px; }
    .panel-head { display: flex; justify-content: space-between; align-items: center; margin-bottom: 18px; }
    .panel-head h2 { margin: 0; font-size: 20px; letter-spacing: -.5px; }
    .seminar { display: flex; gap: 14px; padding: 14px 0; border-top: 1px solid var(--line); }
    .date-box { flex: 0 0 52px; height: 58px; display: grid; align-content: center; justify-items: center; border-radius: 12px; background: #f6eee7; color: #8d5b3e; }
    .date-box b { font-size: 20px; line-height: 1; }
    .date-box small { margin-top: 5px; font-size: 10px; font-weight: 750; text-transform: uppercase; }
    .seminar-info { flex: 1; }
    .seminar-info strong { display: block; margin: 2px 0 5px; font-size: 14px; }
    .seminar-info small { color: var(--muted); font-size: 12px; }
    .register-btn { align-self: center; border: 0; background: transparent; color: var(--green); font-size: 12px; font-weight: 750; }
    .register-btn:hover { text-decoration: underline; }

    .progress-score { display: flex; align-items: center; gap: 13px; margin-bottom: 18px; padding: 15px; border-radius: 14px; background: #f5f7f3; }
    .score-circle { display: grid; place-items: center; width: 48px; height: 48px; border-radius: 50%; color: var(--green); background: white; font-size: 14px; font-weight: 800; border: 4px solid #d8e6d9; }
    .progress-score strong { font-size: 14px; }
    .progress-score small { display: block; margin-top: 4px; color: var(--muted); font-size: 12px; }
    .progress-item { padding: 13px 0; border-top: 1px solid var(--line); }
    .progress-label { display: flex; justify-content: space-between; gap: 12px; margin-bottom: 9px; font-size: 13px; }
    .progress-label span:last-child { color: var(--muted); font-size: 12px; }
    .bar { height: 7px; overflow: hidden; border-radius: 10px; background: #eeeee9; }
    .bar span { display: block; height: 100%; border-radius: inherit; background: var(--green); }

    .ai-section { padding-bottom: 70px; }
    .ai-card {
      display: grid; grid-template-columns: .85fr 1.15fr; gap: 30px; align-items: center;
      padding: 28px; border-radius: 24px; color: white; background: #203d32;
    }
    .ai-card h2 { margin: 13px 0 10px; font-size: 27px; letter-spacing: -.9px; }
    .ai-card p { color: #d1ddd4; font-size: 14px; line-height: 1.6; }
    .ai-label { color: #c3e3c9; font-size: 11px; text-transform: uppercase; font-weight: 750; letter-spacing: .09em; }
    .lesson-box { padding: 20px; border-radius: 16px; background: white; color: var(--ink); }
    .lesson-form { display: flex; gap: 9px; }
    .lesson-form input {
      min-width: 0; flex: 1; padding: 12px 13px; border: 1px solid var(--line);
      border-radius: 10px; outline: none;
    }
    .lesson-form input:focus { border-color: #8bab91; box-shadow: 0 0 0 3px #e5eee7; }
    .lesson-form .btn { padding: 11px 15px; white-space: nowrap; }
    .lesson-output { display: none; margin-top: 16px; padding: 15px; border-radius: 12px; background: #f5f7f3; }
    .lesson-output.show { display: block; }
    .lesson-output h3 { margin: 0 0 8px; font-size: 15px; }
    .lesson-output p, .lesson-output li { color: #5d645e; font-size: 13px; line-height: 1.55; }
    .lesson-output p { margin: 0 0 8px; }
    .lesson-output ul { margin: 7px 0 0; padding-left: 19px; }

    footer { border-top: 1px solid var(--line); padding: 22px 0 30px; color: var(--muted); font-size: 12px; }
    .footer-row { display: flex; justify-content: space-between; gap: 15px; flex-wrap: wrap; }

    .toast {
      position: fixed; right: 22px; bottom: 22px; z-index: 5;
      padding: 13px 17px; border-radius: 12px; color: white; background: var(--ink);
      box-shadow: var(--shadow); font-size: 13px; opacity: 0; transform: translateY(10px);
      pointer-events: none; transition: .25s ease;
    }
    .toast.show { opacity: 1; transform: translateY(0); }

    @media (max-width: 850px) {
      .nav { gap: 16px; }
      .hero { grid-template-columns: 1fr; gap: 28px; padding-top: 45px; }
      .hero-card { min-height: 315px; }
      .skill-grid { grid-template-columns: repeat(2, 1fr); }
      .ai-card { grid-template-columns: 1fr; }
    }
    @media (max-width: 620px) {
      .shell { padding: 0 18px; }
      .topbar { height: 66px; }
      .nav { display: none; }
      .profile span:last-child { display: none; }
      .hero { padding: 38px 0 34px; }
      h1 { letter-spacing: -2px; }
      .hero-copy { font-size: 15px; }
      .hero-card { padding: 18px; min-height: 300px; }
      .exchange-card { margin-top: 6px; padding: 17px; }
      .floating-stat { right: 8px; bottom: 10px; }
      .section { padding: 25px 0 38px; }
      .section-heading { align-items: start; }
      .section-heading h2 { font-size: 22px; }
      .skill-grid, .lower-grid { grid-template-columns: 1fr; }
      .panel { padding: 19px; }
      .ai-card { padding: 22px; }
      .lesson-form { flex-direction: column; }
      .footer-row { flex-direction: column; }
    }
  </style>
</head>
<body>
  <header class="shell">
    <div class="topbar">
      <a class="brand" href="#" aria-label="Talent Trade home">
        <span class="brand-mark">↗</span>
        <span>Talent Trade</span>
      </a>
      <nav class="nav" aria-label="Main navigation">
        <a href="#exchange">Skill exchange</a>
        <a href="#seminars">Seminars</a>
        <a href="#progress">My progress</a>
      </nav>
      <div class="profile">
        <span class="avatar">J</span>
        <span>Jordan Lee</span>
      </div>
    </div>
  </header>

  <main class="shell">
    <section class="hero">
      <div>
        <span class="eyebrow">✦ Learn together, grow together</span>
        <h1>Your skills are currency.<br /><span>Trade them wisely.</span></h1>
        <p class="hero-copy">
          Share what you know, learn what you love. Meet curious people, join expert-led
          seminars, and make progress one skill at a time.
        </p>
        <div class="hero-actions">
          <a class="btn btn-primary" href="#exchange">Explore skill exchanges <span aria-hidden="true">→</span></a>
          <button class="btn btn-secondary" id="shareSkillButton">＋ Share a skill</button>
        </div>
        <div class="hero-note">
          <div class="mini-avatars" aria-hidden="true"><span>M</span><span>A</span><span>S</span></div>
          <span>Join <strong>2,400+</strong> people learning from each other</span>
        </div>
      </div>

      <div class="hero-card" aria-label="Example of a skill exchange">
        <div class="exchange-card">
          <div class="exchange-top">
            <span class="exchange-title">A perfect trade</span>
            <span class="live-pill">● MATCHED</span>
          </div>
          <div class="person-row">
            <span class="avatar">M</span>
            <div><strong>Maya Chen</strong><small>Product designer</small></div>
          </div>
          <div class="swap-line">↕ &nbsp; skill for skill</div>
          <div><span class="skill-chip">🎨 Figma &amp; prototyping</span></div>
          <div class="person-row">
            <span class="avatar" style="background:#d9d4ee;color:#4e4773">J</span>
            <div><strong>Jordan Lee</strong><small>Curious about data</small></div>
          </div>
          <div><span class="skill-chip">📊 Intro to data analysis</span></div>
        </div>
        <div class="floating-stat"><strong>12 hrs</strong>shared this month</div>
      </div>
    </section>

    <section class="section" id="exchange">
      <div class="section-heading">
        <div>
          <h2>Find your next skill exchange</h2>
          <p>Learn something new from someone who loves teaching it.</p>
        </div>
        <a class="text-link" href="#exchange">Browse all skills →</a>
      </div>

      <div class="grid skill-grid">
        <article class="card skill-card">
          <div class="card-head"><span class="skill-icon">🎨</span><span class="tag">Creative</span></div>
          <h3>Figma &amp; UI prototyping</h3>
          <p>Build clean interfaces and turn early ideas into clickable prototypes.</p>
          <div class="skill-meta">
            <div class="person-row"><span class="avatar">M</span><div><strong>Maya Chen</strong><small>Offers design · wants Spanish</small></div></div>
            <button class="small-btn trade-button" data-name="Maya">Connect</button>
          </div>
        </article>

        <article class="card skill-card">
          <div class="card-head"><span class="skill-icon" style="background:#e8f0e5">📈</span><span class="tag">Business</span></div>
          <h3>Marketing analytics</h3>
          <p>Make sense of campaign data and find the story behind the numbers.</p>
          <div class="skill-meta">
            <div class="person-row"><span class="avatar" style="background:#d7e4c9;color:#43533b">A</span><div><strong>Andre Wilson</strong><small>Offers analytics · wants guitar</small></div></div>
            <button class="small-btn trade-button" data-name="Andre">Connect</button>
          </div>
        </article>

        <article class="card skill-card">
          <div class="card-head"><span class="skill-icon" style="background:#f1e9f4">💬</span><span class="tag">Communication</span></div>
          <h3>Confident public speaking</h3>
          <p>Practice clear storytelling, presentation structure, and delivery.</p>
          <div class="skill-meta">
            <div class="person-row"><span class="avatar" style="background:#f1d2bf;color:#714d3a">S</span><div><strong>Sam Rivera</strong><small>Offers speaking · wants Excel</small></div></div>
            <button class="small-btn trade-button" data-name="Sam">Connect</button>
          </div>
        </article>
      </div>
    </section>

    <div class="lower-grid">
      <section class="card panel" id="seminars">
        <div class="panel-head">
          <h2>Upcoming seminars</h2>
          <a class="text-link" href="#seminars">View calendar →</a>
        </div>

        <div class="seminar">
          <div class="date-box"><b>26</b><small>Nov</small></div>
          <div class="seminar-info"><strong>Building your personal brand</strong><small>With Priya Kapoor · 45 min · Online</small></div>
          <button class="register-btn">Join →</button>
        </div>
        <div class="seminar">
          <div class="date-box"><b>28</b><small>Nov</small></div>
          <div class="seminar-info"><strong>AI tools for everyday work</strong><small>With Marcus Reed · 60 min · Online</small></div>
          <button class="register-btn">Join →</button>
        </div>
        <div class="seminar">
          <div class="date-box"><b>03</b><small>Dec</small></div>
          <div class="seminar-info"><strong>Money basics for freelancers</strong><small>With Elena Torres · 50 min · Online</small></div>
          <button class="register-btn">Join →</button>
        </div>
      </section>

      <section class="card panel" id="progress">
        <div class="panel-head">
          <h2>Your progress board</h2>
          <span class="tag">This week</span>
        </div>
        <div class="progress-score">
          <div class="score-circle" id="scoreCircle">68%</div>
          <div><strong>You’re building a great habit!</strong><small id="scoreMessage">2 of 3 weekly goals completed</small></div>
        </div>
        <div class="progress-item">
          <div class="progress-label"><strong>Spanish conversation</strong><span>4 / 6 lessons</span></div>
          <div class="bar"><span style="width:66%"></span></div>
        </div>
        <div class="progress-item">
          <div class="progress-label"><strong>Data analysis basics</strong><span>2 / 5 lessons</span></div>
          <div class="bar"><span style="width:40%;background:#e99360"></span></div>
        </div>
        <div class="progress-item">
          <div class="progress-label"><strong>Teaching hours shared</strong><span>3 / 4 hours</span></div>
          <div class="bar"><span style="width:75%;background:#8da77e"></span></div>
        </div>
        <button class="small-btn" id="completeGoal" style="margin-top:16px">Mark a goal complete</button>
      </section>
    </div>

    <section class="section ai-section">
      <div class="ai-card">
        <div>
          <span class="ai-label">✦ Your personal learning companion</span>
          <h2>Turn curiosity into a lesson.</h2>
          <p>Enter a topic and get a bite-sized lesson plan to help you get started. Learn at your pace, then keep track of your progress.</p>
        </div>
        <div class="lesson-box">
          <form class="lesson-form" id="lessonForm">
            <input id="topicInput" type="text" placeholder="What would you like to learn? e.g. watercolor" aria-label="Topic you want to learn" required />
            <button class="btn btn-primary" type="submit">Create a lesson ✦</button>
          </form>
          <div class="lesson-output" id="lessonOutput" aria-live="polite"></div>
        </div>
      </div>
    </section>
  </main>

  <footer>
    <div class="shell footer-row">
      <span>© 2026 Talent Trade · Learn by sharing.</span>
      <span>Made for curious people, everywhere.</span>
    </div>
  </footer>

  <div class="toast" id="toast" role="status" aria-live="polite"></div>

  <script>
    const toast = document.getElementById("toast");
    let toastTimer;

    function showToast(message) {
      toast.textContent = message;
      toast.classList.add("show");
      clearTimeout(toastTimer);
      toastTimer = setTimeout(() => toast.classList.remove("show"), 2800);
    }

    document.querySelectorAll(".trade-button").forEach((button) => {
      button.addEventListener("click", () => {
        showToast(`Connection request sent to ${button.dataset.name}!`);
        button.textContent = "Requested";
        button.disabled = true;
      });
    });

    document.querySelectorAll(".register-btn").forEach((button) => {
      button.addEventListener("click", () => {
        button.textContent = button.textContent.includes("Joined") ? "Join →" : "Joined ✓";
        showToast(button.textContent.includes("Joined") ? "You're on the seminar list!" : "Seminar registration cancelled.");
      });
    });

    document.getElementById("shareSkillButton").addEventListener("click", () => {
      const skill = prompt("What skill would you like to share?");
      if (skill && skill.trim()) showToast(`Great! “${skill.trim()}” is ready to be added to your profile.`);
    });

    document.getElementById("completeGoal").addEventListener("click", () => {
      const button = document.getElementById("completeGoal");
      const circle = document.getElementById("scoreCircle");
      const message = document.getElementById("scoreMessage");
      const current = Number.parseInt(circle.textContent, 10);

      if (current < 100) {
        const updated = Math.min(current + 16, 100);
        circle.textContent = `${updated}%`;
        message.textContent = updated === 100 ? "All weekly goals completed — amazing work!" : "3 of 3 weekly goals completed";
        button.textContent = updated === 100 ? "All goals completed ✓" : "Goal completed ✓";
        if (updated === 100) button.disabled = true;
        showToast("Progress updated. Keep it up!");
      }
    });

    document.getElementById("lessonForm").addEventListener("submit", (event) => {
      event.preventDefault();
      const topic = document.getElementById("topicInput").value.trim();
      if (!topic) return;

      const output = document.getElementById("lessonOutput");
      output.innerHTML = `
        <h3>Your starter lesson: ${escapeHtml(topic)}</h3>
        <p><strong>Goal:</strong> Understand the basics and try one small exercise.</p>
        <ul>
          <li><strong>Explore (5 min):</strong> Write down what you already know about ${escapeHtml(topic)}.</li>
          <li><strong>Learn (10 min):</strong> Find one beginner-friendly example and identify its key steps.</li>
          <li><strong>Practice (10 min):</strong> Try a small project or exercise using what you learned.</li>
          <li><strong>Reflect (2 min):</strong> Note one thing you learned and one question to explore next.</li>
        </ul>
      `;
      output.classList.add("show");
    });

    function escapeHtml(value) {
      return value.replace(/[&<>"']/g, (char) => ({
        "&": "&amp;", "<": "&lt;", ">": "&gt;", '"': "&quot;", "'": "&#039;"
      })[char]);
    }
  </script>
</body>
</html>
