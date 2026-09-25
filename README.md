<!DOCTYPE html>
<html lang="en" data-theme="dark" style="color-scheme: dark;">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Ten Weeks of Science by Canaya Hans</title>
<style>
  :root{
    --paper:#EEE8DA; --folder:#D7C7A3; --folder-dark:#C6B287;
    --ink:#23303A; --rust:#B5622E; --orbit:#2E7D6B; --line:#c7bca0;
    --card-bg:#ffffff; --card-text:#3a3a3a;
  }
  [data-theme="light"]{
    --paper:#F4F1EA; --ink:#23303A; --folder:#E4D7B4; --folder-dark:#D1C29B;
    --line:#d3c8af; --card-bg:#ffffff; --card-text:#3a3a3a;
  }
  [data-theme="dark"]{
    --paper:#1E1B16; --ink:#EDE6D6; --folder:#4A3F2E; --folder-dark:#5A4C38;
    --line:#3a3326; --card-bg:#262119; --card-text:#d8d0bf;
  }

  *{box-sizing:border-box;}
  body{
    margin:0; color:var(--ink);
    font-family:"Iowan Old Style","Georgia",serif;
    padding: max(2rem, env(safe-area-inset-top)) 1.5rem 3rem;
    background:
      repeating-linear-gradient(180deg,
        rgba(181,98,46,.03) 0 2px,
        transparent 2px 34px),
      var(--paper);
    transition: background .3s ease, color .3s ease;
  }

  .header-container{
    max-width:900px; margin:0 auto 2rem; position:relative;
    display:flex; flex-direction:column; align-items:center;
  }
  h1{
    font-size:1.8rem; font-weight:600; text-align:center;
    margin:0 0 .3rem;
  }
  .sub{ text-align:center; opacity:.7; margin:0 0 .5rem; font-size:.95rem; }
  .badge{
    display:block; text-align:center; font-size:.75rem;
    opacity:.7; margin:0; letter-spacing:.02em;
  }

  .theme-toggle{
    position:absolute; top:0; right:0;
    background:var(--folder); border:1px solid var(--line);
    color:var(--ink); padding:.4rem .8rem; border-radius:4px;
    cursor:pointer; font-family:inherit; font-size:.8rem;
    transition: background .2s ease;
  }
  .theme-toggle:hover{ background:var(--folder-dark); }

  .rack{
    display:grid;
    grid-template-columns:repeat(auto-fill, minmax(150px,1fr));
    gap: 1.5rem 1rem;
    max-width: 900px;
    margin: 0 auto 2rem;
  }

  .folder-btn{
    position:relative;
    background: linear-gradient(180deg, var(--folder) 0%, var(--folder-dark) 100%);
    border:none;
    padding: 1.6rem 1rem 1rem;
    cursor:pointer;
    font-family:inherit;
    font-size:1.05rem;
    color:var(--ink);
    text-align:left;
    border-radius: 2px 8px 4px 4px;
    box-shadow: 0 4px 8px rgba(0,0,0,.15);
    transition: transform .25s cubic-bezier(0.2, 0.8, 0.2, 1), box-shadow .25s ease;
    display:flex; align-items:center; gap:.6rem;
    overflow: visible;
  }
  .folder-btn::before{
    content:"";
    position:absolute; top:-10px; left:12px;
    width:46%; height:14px;
    background:var(--folder);
    border-radius:4px 6px 0 0;
    z-index:2;
  }
  .folder-btn::after{
    content:"";
    position:absolute; top:0; left:0; right:0; height:6px;
    background: linear-gradient(180deg, rgba(255,255,255,.3) 0%, transparent 100%);
    border-radius:3px 3px 0 0;
    z-index:4;
  }

  .paper-container {
    position: absolute;
    top: 6px; left: 12px; right: 12px; height: 0px;
    z-index: 1;
    pointer-events: none;
  }
  .paper {
    position: absolute;
    left: 4px; right: 4px; height: 20px;
    background: #ffffff; border: 1px solid #dcd6cd;
    border-radius: 2px 2px 0 0;
    box-shadow: 0 -1px 2px rgba(0,0,0,.05);
    bottom: 0px;
    transform: translateY(0);
    transition: transform 0.4s cubic-bezier(0.16, 1, 0.3, 1);
  }
  .paper.p1{ z-index: 1; }
  .paper.p2{ z-index: 2; }
  .paper.p3{ z-index: 3; }

  .folder-btn > svg, .folder-btn > span{ position:relative; z-index:5; }

  .folder-btn:hover{
    transform: translateY(-2px);
    box-shadow: 0 6px 12px rgba(0,0,0,.2);
  }

  .folder-btn.active{
    background: linear-gradient(180deg, var(--orbit) 0%, #235c4f 100%);
    color:var(--paper);
    transform: translateY(4px); 
    box-shadow: 0 2px 4px rgba(0,0,0,.1);
  }
  .folder-btn.active::before{ background:var(--orbit) !important; }

  .folder-btn.active .paper.p1{ transform: translateY(-10px); }
  .folder-btn.active .paper.p2{ transform: translateY(-15px); }
  .folder-btn.active .paper.p3{ transform: translateY(-20px); }

  .folder-btn:focus-visible{ outline:3px solid var(--rust); outline-offset:2px; }

  .atom{ flex:0 0 auto; opacity:.8; }
  .folder-btn.active .atom{ opacity:1; }
  .atom circle.e{ fill:var(--rust); }
  .folder-btn.active .atom circle.e{ fill:var(--paper); }
  .atom ellipse{ stroke:var(--ink); }
  .folder-btn.active .atom ellipse{ stroke:var(--paper); }

  .wk{ display:block; font-size:.75rem; letter-spacing:.02em; opacity:.7; margin-bottom:.1rem;}

  .viewer{
    max-width:900px; margin:0 auto;
    background:var(--card-bg); border:1px solid var(--line);
    border-radius:6px; padding:2rem;
    min-height:180px; box-shadow: 0 4px 12px rgba(0,0,0,.05);
    transition: background .3s ease, border-color .3s ease;
  }
  .viewer h2{ margin:0 0 .6rem; font-size:1.4rem; color:var(--ink); }
  .viewer p{ 
    line-height:1.65; 
    color:var(--card-text); 
    white-space: pre-wrap; 
  }

  .viewer-inner{ animation: viewerIn .4s ease .1s both; }
  @keyframes viewerIn{
    from{ opacity:0; transform:translateY(12px); }
    to{ opacity:1; transform:translateY(0); }
  }
</style>
</head>
<body>

<div class="header-container">
  <button class="theme-toggle" id="theme-toggle">🌓 Theme</button>
  <h1>Ten Weeks of Science</h1>
  <p class="sub">by Canaya Hans &nbsp;·&nbsp; click a folder to open that week</p>
  <p class="badge">Laguna Science National High School Study Hub</p>
</div>

<div class="rack" id="rack"></div>

<div class="viewer" id="viewer"></div>

<script>
  // Content Data Source
  const content = {
    "1": {
      "label": "No. 01",
      "title": "Week 1",
      "body": "Scientists mentioned:\n\n• Louis de Broglie\n– Proposed that electrons can behave like waves.\n– Developed the matter-wave theory.\n– His work helped explain the wave-particle duality of electrons.\n– Contributed to the development of the quantum mechanical model of the atom.\n– Helped scientists understand how electrons behave around the nucleus.\n\n• Werner Heisenberg\n– Developed an important form of quantum mechanics.\n– Proposed the Heisenberg Uncertainty Principle.\n– Stated that the exact position and momentum of an electron cannot both be known at the same time.\n– Showed that electrons do not move in simple, fixed paths.\n– Helped establish the modern understanding of electron behavior.\n\n• Erwin Schrödinger\n– Developed the Schrödinger equation.\n– Used mathematics to describe the behavior of electrons.\n– Introduced the concept of electron orbitals.\n– Explained the probability of finding an electron in a certain region around the nucleus.\n– His work helped develop the modern quantum mechanical model of the atom."
    },
    "2": { "label": "No. 02", "title": "Week 2", "body": "Add your Week 2 notes or project links here." },
    "3": { "label": "No. 03", "title": "Week 3", "body": "Add your Week 3 notes or project links here." },
    "4": { "label": "No. 04", "title": "Week 4", "body": "Add your Week 4 notes or project links here." },
    "5": { "label": "No. 05", "title": "Week 5", "body": "Add your Week 5 notes or project links here." },
    "6": { "label": "No. 06", "title": "Week 6", "body": "Add your Week 6 notes or project links here." },
    "7": { "label": "No. 07", "title": "Week 7", "body": "Add your Week 7 notes or project links here." },
    "8": { "label": "No. 08", "title": "Week 8", "body": "Add your Week 8 notes or project links here." },
    "9": { "label": "No. 09", "title": "Week 9", "body": "Add your Week 9 notes or project links here." },
    "10": { "label": "No. 10", "title": "Week 10", "body": "Add your Week 10 notes or project links here." },
    "me": {
      "label": "About",
      "title": "Myself and My Experiences in Science",
      "body": "Welcome to My Study Hub!\n\nBefore taking the entrance exam, I thought Laguna Science National High School would be just like any ordinary school. But once I stepped onto the campus, my perspective changed. The engaging teaching style of the teachers made me feel right at home. As I advanced to higher grade levels, science became even more enjoyable through exciting experiments and collaborative group tasks. That is why I created this website to serve as a helpful study guide and reviewer for my academic journey.\n\n— Hans Fredric F. Canaya"
    }
  };

  const items = ["me", 1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
  const rack = document.getElementById('rack');
  const viewer = document.getElementById('viewer');
  
  let activeKey = 1;

  // Theme Handling
  const currentTheme = localStorage.getItem('science_theme') || 'dark';
  document.documentElement.setAttribute('data-theme', currentTheme);

  document.getElementById('theme-toggle').addEventListener('click', () => {
    const nextTheme = document.documentElement.getAttribute('data-theme') === 'dark' ? 'light' : 'dark';
    document.documentElement.setAttribute('data-theme', nextTheme);
    localStorage.setItem('science_theme', nextTheme);
  });

  const atomSVG = `<svg class="atom" width="26" height="26" viewBox="0 0 26 26" fill="none">
    <ellipse cx="13" cy="13" rx="11" ry="4.5" stroke-width="1.1"/>
    <ellipse cx="13" cy="13" rx="11" ry="4.5" stroke-width="1.1" transform="rotate(60 13 13)"/>
    <ellipse cx="13" cy="13" rx="11" ry="4.5" stroke-width="1.1" transform="rotate(120 13 13)"/>
    <circle class="e" cx="13" cy="13" r="2.4"/>
  </svg>`;

  function renderRack(){
    rack.innerHTML = '';
    items.forEach(key => {
      const c = content[key] || { label: "", title: "" };
      const papers = `<div class="paper-container"><span class="paper p1"></span><span class="paper p2"></span><span class="paper p3"></span></div>`;
      const btn = document.createElement('button');
      btn.className = 'folder-btn';
      if (String(key) === String(activeKey)) btn.classList.add('active');
      btn.innerHTML = `${papers}${atomSVG}<span><span class="wk">${c.label}</span>${key === 'me' ? 'Myself' : c.title}</span>`;
      btn.addEventListener('click', () => openFolder(key));
      rack.appendChild(btn);
    });
  }

  function openFolder(key){
    activeKey = key;
    renderRack();
    const c = content[key];
    viewer.innerHTML = `<div class="viewer-inner"><h2>${c.title}</h2><p>${c.body}</p></div>`;
  }

  // Initialize App on load
  renderRack();
  openFolder(activeKey);
</script>

</body>
</html>
