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
  [data-theme="light"] { --paper:#f4f1ea; --folder:#e4d7b4; --folder-dark:#d1c29b; --line:#d3c8af; }
  [data-theme="dark"] { --paper:#1e1b16; --ink:#ede6d6; --folder:#4a3f2e; --folder-dark:#5a4c38; --line:#3a3326; --card-bg:#262119; --card-text:#d8d0bf; }
  *, *::before, *::after { box-sizing: border-box; }
  html { min-width: 0; }
  body {
    margin: 0; min-height: 100vh; padding: clamp(1.25rem, 4vw, 3rem) 1rem 3rem;
    color: var(--ink); font-family: "Iowan Old Style", Georgia, serif;
    background: var(--paper); transition: background .3s ease, color .3s ease;
  }
  .header-container, main { width: min(100%, 900px); margin: 0 auto; }
  .header-container { position: relative; margin-bottom: clamp(1.5rem, 4vw, 2.25rem); padding: 0 5rem; text-align: center; }
  h1 { margin: 0 0 .35rem; font-size: clamp(1.55rem, 5vw, 2.2rem); font-weight: 650; }
  .sub, .badge { margin: 0; opacity: .72; }
  .sub { font-size: clamp(.9rem, 2.5vw, 1rem); }
  .badge { margin-top: .45rem; font-size: .78rem; letter-spacing: .02em; }
  .theme-toggle { position: absolute; top: 0; right: 0; padding: .55rem .75rem; border: 1px solid var(--line); border-radius: 8px; background: var(--folder); color: var(--ink); cursor: pointer; font: inherit; font-size: .8rem; }
  .theme-toggle:hover { background: var(--folder-dark); }
  .rack { display: grid; grid-template-columns: repeat(auto-fit, minmax(min(100%, 170px), 1fr)); gap: 1rem; margin-bottom: 1.5rem; }
  .folder-btn {
    position: relative; display: flex; align-items: center; gap: .65rem; min-width: 0; min-height: 88px;
    padding: 1.2rem 1rem 1rem; overflow: hidden; border: 1px solid color-mix(in srgb, var(--ink) 12%, transparent);
    border-radius: 10px; background: linear-gradient(160deg, var(--folder), var(--folder-dark)); color: var(--ink);
    cursor: pointer; text-align: left; font: inherit; font-size: 1rem; box-shadow: 0 3px 8px rgba(0,0,0,.12);
    transition: transform .2s ease, box-shadow .2s ease;
  }
  .folder-btn:hover { transform: translateY(-2px); box-shadow: 0 6px 14px rgba(0,0,0,.18); }
  .folder-btn.active { color: var(--paper); background: linear-gradient(160deg, var(--orbit), #235c4f); box-shadow: 0 3px 8px rgba(0,0,0,.14); }
  .folder-btn:focus-visible { outline: 3px solid var(--rust); outline-offset: 3px; }
  .atom { flex: 0 0 26px; opacity: .8; }
  .folder-btn.active .atom { opacity: 1; }
  .atom circle { fill: var(--rust); } .atom ellipse { stroke: var(--ink); }
  .folder-btn.active .atom circle { fill: var(--paper); } .folder-btn.active .atom ellipse { stroke: var(--paper); }
  .folder-label { min-width: 0; overflow-wrap: anywhere; }
  .wk { display: block; margin-bottom: .15rem; opacity: .72; font-size: .73rem; letter-spacing: .02em; }
  .viewer { min-height: 180px; padding: clamp(1.25rem, 4vw, 2rem); border: 1px solid var(--line); border-radius: 10px; background: var(--card-bg); color: var(--card-text); box-shadow: 0 4px 12px rgba(0,0,0,.06); }
  .viewer-inner { animation: viewerIn .3s ease both; }
  .viewer h2 { margin: 0 0 .8rem; color: var(--ink); font-size: clamp(1.25rem, 4vw, 1.5rem); }
  .viewer p { margin: 0; line-height: 1.7; white-space: pre-wrap; overflow-wrap: anywhere; }
  @keyframes viewerIn { from { opacity: 0; transform: translateY(8px); } to { opacity: 1; transform: translateY(0); } }
  @media (max-width: 600px) {
    body { padding-left: .75rem; padding-right: .75rem; }
    .header-container { padding: 0; }
    .theme-toggle { position: static; display: block; margin: 0 auto 1rem; }
    .rack { grid-template-columns: repeat(2, minmax(0, 1fr)); gap: .7rem; }
    .folder-btn { min-height: 74px; padding: .9rem .7rem; font-size: .92rem; }
    .atom { flex-basis: 22px; width: 22px; height: 22px; }
  }
  @media (max-width: 360px) { .rack { grid-template-columns: 1fr; } }
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
  // Keep each note in a template literal so quotes and apostrophes in your text render correctly.
  const content = {
    1: { label: "Week 1", title: "Week 1", body: `Scientists mentioned:\n\n• Louis de Broglie\n– Proposed that electrons can behave like waves.\n– Developed the matter-wave theory.\n– His work helped explain wave-particle duality.` },
    2: { label: "Week 2", title: "Week 2", body: `Add your Week 2 notes or project links here.` },
    3: { label: "Week 3", title: "Week 3", body: `Add your Week 3 notes or project links here.` },
    4: { label: "Week 4", title: "Week 4", body: `Add your Week 4 notes or project links here.` },
    5: { label: "Week 5", title: "Week 5", body: `Add your Week 5 notes or project links here.` },
    6: { label: "Week 6", title: "Week 6", body: `Add your Week 6 notes or project links here.` },
    7: { label: "Week 7", title: "Week 7", body: `Add your Week 7 notes or project links here.` },
    8: { label: "Week 8", title: "Week 8", body: `Add your Week 8 notes or project links here.` },
    9: { label: "Week 9", title: "Week 9", body: `Add your Week 9 notes or project links here.` },
    10: { label: "Week 10", title: "Week 10", body: `Add your Week 10 notes or project links here.` },
    me: { label: "About", title: "Myself and My Experiences in Science", body: `Welcome to My Study Hub!\n\nBefore taking the entrance exam, I thought Laguna Science National High School would be just like any ordinary school. Once I stepped onto the campus, I discovered a new world of learning and science.` }
  };
  const items = ["me", 1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
  const rack = document.getElementById("rack");
  const viewer = document.getElementById("viewer");
  let activeKey = 1;
  const atomSVG = `<svg class="atom" width="26" height="26" viewBox="0 0 26 26" fill="none" aria-hidden="true"><ellipse cx="13" cy="13" rx="11" ry="4.5" stroke-width="1.1"/><ellipse cx="13" cy="13" rx="11" ry="4.5" stroke-width="1.1" transform="rotate(60 13 13)"/><ellipse cx="13" cy="13" rx="11" ry="4.5" stroke-width="1.1" transform="rotate(120 13 13)"/><circle cx="13" cy="13" r="2.4"/></svg>`;
  function renderRack() {
    rack.replaceChildren();
    items.forEach((key) => {
      const folder = content[key];
      const button = document.createElement("button");
      button.type = "button"; button.className = "folder-btn";
      button.setAttribute("aria-pressed", String(key === activeKey));
      if (key === activeKey) button.classList.add("active");
      button.innerHTML = atomSVG;
      const label = document.createElement("span"); label.className = "folder-label";
      const number = document.createElement("span"); number.className = "wk"; number.textContent = folder.label;
      label.append(number, document.createTextNode(key === "me" ? "Myself" : folder.title));
      button.append(label); button.addEventListener("click", () => openFolder(key)); rack.append(button);
    });
  }
  function openFolder(key) {
    activeKey = key; renderRack(); const folder = content[key]; viewer.replaceChildren();
    const inner = document.createElement("div"); inner.className = "viewer-inner";
    const heading = document.createElement("h2"); heading.textContent = folder.title;
    const body = document.createElement("p"); body.textContent = folder.body;
    inner.append(heading, body); viewer.append(inner);
  }
  const savedTheme = localStorage.getItem("science_theme");
  document.documentElement.dataset.theme = savedTheme === "light" ? "light" : "dark";
  document.getElementById("theme-toggle").addEventListener("click", () => {
    const nextTheme = document.documentElement.dataset.theme === "dark" ? "light" : "dark";
    document.documentElement.dataset.theme = nextTheme; localStorage.setItem("science_theme", nextTheme);
  });
  openFolder(activeKey);
</script>
</body>
</html>
