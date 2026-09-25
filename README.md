# CANAYA.WATSON.SCIENCE8

<!doctype html>
<html lang="en" data-theme="dark">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Ten Weeks of Science by Canaya Hans</title>
<style>
  :root {
    --paper: #eee8da;
    --folder: #d7c7a3;
    --folder-dark: #c6b287;
    --ink: #23303a;
    --rust: #b5622e;
    --orbit: #2e7d6b;
    --line: #c7bca0;
    --card-bg: #fff;
    --card-text: #3a3a3a;
  }
  [data-theme="light"] {
    --paper: #f4f1ea;
    --folder: #e4d7b4;
    --folder-dark: #d1c29b;
    --line: #d3c8af;
  }
  [data-theme="dark"] {
    --paper: #1e1b16;
    --ink: #ede6d6;
    --folder: #4a3f2e;
    --folder-dark: #5a4c38;
    --line: #3a3326;
    --card-bg: #262119;
    --card-text: #d8d0bf;
  }
  * { box-sizing: border-box; }
  body {
    margin: 0;
    min-height: 100vh;
    padding: max(2rem, env(safe-area-inset-top)) 1.5rem 3rem;
    color: var(--ink);
    font-family: "Iowan Old Style", Georgia, serif;
    background: repeating-linear-gradient(180deg, rgba(181,98,46,.03) 0 2px, transparent 2px 34px), var(--paper);
    transition: background .3s ease, color .3s ease;
  }
  .header-container, .rack, .viewer { max-width: 900px; margin-left: auto; margin-right: auto; }
  .header-container { position: relative; margin-bottom: 2rem; text-align: center; }
  h1 { margin: 0 0 .3rem; font-size: clamp(1.5rem, 5vw, 1.8rem); font-weight: 600; }
  .sub { margin: 0 0 .5rem; opacity: .7; font-size: .95rem; }
  .badge { margin: 0; opacity: .7; font-size: .75rem; letter-spacing: .02em; }
  .theme-toggle {
    position: absolute; top: 0; right: 0; padding: .4rem .8rem;
    border: 1px solid var(--line); border-radius: 4px; background: var(--folder);
    color: var(--ink); cursor: pointer; font: inherit; font-size: .8rem;
  }
  .theme-toggle:hover { background: var(--folder-dark); }
  .rack {
    display: grid; grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
    gap: 1.5rem 1rem; margin-bottom: 2rem;
  }
  .folder-btn {
    position: relative; display: flex; align-items: center; gap: .6rem;
    min-height: 76px; padding: 1.6rem 1rem 1rem; overflow: visible;
    border: 0; border-radius: 2px 8px 4px 4px;
    background: linear-gradient(180deg, var(--folder), var(--folder-dark));
    color: var(--ink); cursor: pointer; text-align: left; font: inherit; font-size: 1.05rem;
    box-shadow: 0 4px 8px rgba(0,0,0,.15);
    transition: transform .25s ease, box-shadow .25s ease;
  }
  .folder-btn::before {
    content: ""; position: absolute; z-index: 2; top: -10px; left: 12px;
    width: 46%; height: 14px; border-radius: 4px 6px 0 0; background: var(--folder);
  }
  .folder-btn::after {
    content: ""; position: absolute; z-index: 4; top: 0; left: 0; right: 0; height: 6px;
    border-radius: 3px 3px 0 0; background: linear-gradient(rgba(255,255,255,.3), transparent);
  }
  .folder-btn:hover { transform: translateY(-2px); box-shadow: 0 6px 12px rgba(0,0,0,.2); }
  .folder-btn.active {
    transform: translateY(4px); color: var(--paper);
    background: linear-gradient(180deg, var(--orbit), #235c4f);
    box-shadow: 0 2px 4px rgba(0,0,0,.1);
  }
  .folder-btn.active::before { background: var(--orbit); }
  .folder-btn:focus-visible { outline: 3px solid var(--rust); outline-offset: 2px; }
  .atom { flex: 0 0 auto; opacity: .8; }
  .folder-btn.active .atom { opacity: 1; }
  .atom circle { fill: var(--rust); }
  .atom ellipse { stroke: var(--ink); }
  .folder-btn.active .atom circle { fill: var(--paper); }
  .folder-btn.active .atom ellipse { stroke: var(--paper); }
  .folder-label { position: relative; z-index: 5; min-width: 0; }
  .wk { display: block; margin-bottom: .1rem; opacity: .7; font-size: .75rem; letter-spacing: .02em; }
  .paper-container { position: absolute; z-index: 1; top: 6px; left: 12px; right: 12px; height: 0; pointer-events: none; }
  .paper { position: absolute; left: 4px; right: 4px; bottom: 0; height: 20px; border: 1px solid #dcd6cd; border-radius: 2px 2px 0 0; background: #fff; }
  .paper.p1 { z-index: 1; transform: translateY(-10px); }
  .paper.p2 { z-index: 2; transform: translateY(-15px); }
  .paper.p3 { z-index: 3; transform: translateY(-20px); }
  .viewer {
    min-height: 180px; padding: 2rem; border: 1px solid var(--line); border-radius: 6px;
    background: var(--card-bg); color: var(--card-text); box-shadow: 0 4px 12px rgba(0,0,0,.05);
  }
  .viewer-inner { animation: viewerIn .4s ease both; }
  .viewer h2 { margin: 0 0 .6rem; color: var(--ink); font-size: 1.4rem; }
  .viewer p { margin: 0; line-height: 1.65; white-space: pre-wrap; overflow-wrap: anywhere; }
  @keyframes viewerIn { from { opacity: 0; transform: translateY(12px); } to { opacity: 1; transform: translateY(0); } }
  @media (max-width: 560px) {
    body { padding-left: 1rem; padding-right: 1rem; }
    .theme-toggle { position: static; margin-bottom: 1rem; }
    .viewer { padding: 1.25rem; }
  }
</style>
</head>
<body>
<header class="header-container">
  <button class="theme-toggle" id="theme-toggle" type="button">🌓 Theme</button>
  <h1>Ten Weeks of Science</h1>
  <p class="sub">by Canaya Hans · click a folder to open that week</p>
  <p class="badge">Published science study hub</p>
</header>

<main>
  <nav class="rack" id="rack" aria-label="Science folders"></nav>
  <section class="viewer" id="viewer" aria-live="polite"></section>
</main>

<script>
  // Edit this content in the repository, then commit and publish the change.
  // There is intentionally no owner login or browser editing: everyone sees
  // the same published content, and visitors cannot change the website.
  const content = {
    1: {
      label: "No. 01",
      title: "Week 1",
      body: "Scientists mentioned:\n\n• Louis de Broglie\n– Proposed that electrons can behave like waves.\n– Developed the matter-wave theory.\n– His work helped explain wave-particle duality."
    },
    2: { label: "No. 02", title: "Week 2", body: "Add your Week 2 notes or project links here." },
    3: { label: "No. 03", title: "Week 3", body: "Add your Week 3 notes or project links here." },
    4: { label: "No. 04", title: "Week 4", body: "Add your Week 4 notes or project links here." },
    5: { label: "No. 05", title: "Week 5", body: "Add your Week 5 notes or project links here." },
    6: { label: "No. 06", title: "Week 6", body: "Add your Week 6 notes or project links here." },
    7: { label: "No. 07", title: "Week 7", body: "Add your Week 7 notes or project links here." },
    8: { label: "No. 08", title: "Week 8", body: "Add your Week 8 notes or project links here." },
    9: { label: "No. 09", title: "Week 9", body: "Add your Week 9 notes or project links here." },
    10: { label: "No. 10", title: "Week 10", body: "Add your Week 10 notes or project links here." },
    me: {
      label: "About",
      title: "Myself and My Experiences in Science",
      body: "Welcome to My Study Hub!\n\nBefore taking the entrance exam, I thought Laguna Science National High School would be just like any ordinary school. Once I stepped onto the campus, I discovered a community that encouraged curiosity, discipline, and a love of science."
    }
  };

  const items = ["me", 1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
  const rack = document.getElementById("rack");
  const viewer = document.getElementById("viewer");
  let activeKey = 1;

  const atomSVG = `<svg class="atom" width="26" height="26" viewBox="0 0 26 26" fill="none" aria-hidden="true">
    <ellipse cx="13" cy="13" rx="11" ry="4.5" stroke-width="1.1"/>
    <ellipse cx="13" cy="13" rx="11" ry="4.5" stroke-width="1.1" transform="rotate(60 13 13)"/>
    <ellipse cx="13" cy="13" rx="11" ry="4.5" stroke-width="1.1" transform="rotate(120 13 13)"/>
    <circle cx="13" cy="13" r="2.4"/>
  </svg>`;

  function renderRack() {
    rack.replaceChildren();
    items.forEach((key) => {
      const folder = content[key];
      const button = document.createElement("button");
      button.type = "button";
      button.className = "folder-btn";
      button.setAttribute("aria-pressed", String(String(key) === String(activeKey)));
      if (String(key) === String(activeKey)) button.classList.add("active");
      button.innerHTML = `<div class="paper-container"><span class="paper p1"></span><span class="paper p2"></span><span class="paper p3"></span></div>${atomSVG}`;

      const label = document.createElement("span");
      label.className = "folder-label";
      const number = document.createElement("span");
      number.className = "wk";
      number.textContent = folder.label;
      label.append(number, document.createTextNode(key === "me" ? "Myself" : folder.title));
      button.appendChild(label);
      button.addEventListener("click", () => openFolder(key));
      rack.appendChild(button);
    });
  }

  function openFolder(key) {
    activeKey = key;
    renderRack();
    const folder = content[key];
    viewer.replaceChildren();
    const inner = document.createElement("div");
    inner.className = "viewer-inner";
    const heading = document.createElement("h2");
    heading.textContent = folder.title;
    const body = document.createElement("p");
    body.textContent = folder.body;
    inner.append(heading, body);
    viewer.appendChild(inner);
  }

  const savedTheme = localStorage.getItem("science_theme");
  document.documentElement.dataset.theme = savedTheme === "light" ? "light" : "dark";
  document.getElementById("theme-toggle").addEventListener("click", () => {
    const nextTheme = document.documentElement.dataset.theme === "dark" ? "light" : "dark";
    document.documentElement.dataset.theme = nextTheme;
    localStorage.setItem("science_theme", nextTheme);
  });

  openFolder(activeKey);
</script>
</body>
</html>
