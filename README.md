<!DOCTYPE html>
<html lang="en" data-theme="dark" style="color-scheme: dark;">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Ten Weeks of Science by Canaya Hans</title>
<link rel="preconnect" href="https://fonts.googleapis.com"><link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@500;600&display=swap" rel="stylesheet">
<style>
  :root{
    --paper:#EEE8DA; --folder:#D7C7A3; --folder-dark:#C6B287;
    --ink:#23303A; --rust:#B5622E; --orbit:#2E7D6B; --line:#c7bca0;
    --card-bg:#262119; --card-text:#d8d0bf;
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
    padding: max(2rem, env(safe-area-inset-top)) 1rem 3rem;
    background:
      repeating-linear-gradient(180deg,
        rgba(181,98,46,.02) 0 2px,
        transparent 2px 36px),
      var(--paper);
    transition: background .4s cubic-bezier(0.16, 1, 0.3, 1), color .4s ease;
  }

  .header-container{
    max-width:960px; margin:0 auto 2rem; position:relative;
    display:flex; flex-direction:column; align-items:center;
    padding-top: 0.5rem;
  }
  h1{
    font-size:2rem; font-weight:600; text-align:center;
    margin:0 0 .3rem; letter-spacing: -0.01em;
  }
  .sub{ text-align:center; opacity:.75; margin:0 0 .6rem; font-size:0.95rem; }
  .badge{
    display:inline-block; text-align:center; font-size:.75rem;
    opacity:.65; margin:0; letter-spacing:.04em; text-transform: uppercase;
    background: var(--folder); padding: 0.2rem 0.6rem; border-radius: 20px;
    border: 1px solid var(--line);
  }

  .theme-toggle{
    position:absolute; top:0; right:0;
    background:var(--folder); border:1px solid var(--line);
    color:var(--ink); padding:.4rem .8rem; border-radius:6px;
    cursor:pointer; font-family:inherit; font-size:0.8rem;
    transition: background .25s ease, transform .2s ease;
  }
  .theme-toggle:hover{ background:var(--folder-dark); transform: translateY(-1px); }

  .rack{
    display:grid;
    grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
    gap: 1.25rem 1rem;
    max-width: 960px;
    margin: 0 auto;
    width: 100%;
  }

  .folder-btn{
    position:relative;
    background: linear-gradient(180deg, var(--folder) 0%, var(--folder-dark) 100%);
    border:none;
    padding: 1.4rem 0.9rem 0.9rem;
    cursor:pointer;
    font-family:inherit;
    font-size:0.95rem;
    color:var(--ink);
    text-align:left;
    border-radius: 3px 10px 6px 6px;
    box-shadow: 0 4px 12px rgba(0,0,0,.08);
    transition: transform 0.3s cubic-bezier(0.2, 0.8, 0.2, 1), box-shadow 0.3s cubic-bezier(0.2, 0.8, 0.2, 1);
    display:flex; align-items:center; gap:.6rem;
    overflow: hidden;
    width: 100%;
    height: 78px;
  }
  .folder-btn::before{
    content:"";
    position:absolute; top:-10px; left:12px;
    width:42%; height:12px;
    background:var(--folder);
    border-radius:4px 6px 0 0;
    z-index:2;
  }
  .folder-btn::after{
    content:"";
    position:absolute; top:0; left:0; right:0; height:5px;
    background: linear-gradient(180deg, rgba(255,255,255,.35) 0%, transparent 100%);
    border-radius:3px 3px 0 0;
    z-index:4;
  }

  .paper-container {
    position: absolute;
    top: 5px; left: 12px; right: 12px; height: 0px;
    z-index: 1;
    pointer-events: none;
  }
  .paper {
    position: absolute;
    left: 4px; right: 4px; height: 18px;
    background: #ffffff; border: 1px solid #dcd6cd;
    border-radius: 3px 3px 0 0;
    box-shadow: 0 -2px 4px rgba(0,0,0,.04);
    bottom: 0px;
  }
  .paper.p1{ z-index: 1; }
  .paper.p2{ z-index: 2; }
  .paper.p3{ z-index: 3; }

  .folder-btn > svg, .folder-btn > .folder-txt{ position:relative; z-index:5; flex-shrink: 0; }
  .folder-txt {
    flex: 1 1 0;
    min-width: 0;
    overflow: hidden;
  }
  .folder-txt span.title-text {
    display: block;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  .folder-btn:hover{
    transform: translateY(-3px);
    box-shadow: 0 8px 20px rgba(0,0,0,.15);
  }
  .folder-btn:focus-visible{ outline:3px solid var(--rust); outline-offset:2px; }

  .atom{ flex:0 0 auto; opacity:.75; transition: opacity .3s ease; width: 22px; height: 22px; }
  .folder-btn:hover .atom{ opacity:1; }
  .atom circle.e{ fill:var(--rust); transition: fill .3s ease; }
  .atom ellipse{ stroke:var(--ink); transition: stroke .3s ease; }

  .wk{ display:block; font-size:.68rem; letter-spacing:.04em; opacity:.7; margin-bottom:.1rem; text-transform: uppercase;}

  .book-overlay {
    position: fixed; inset: 0;
    background: rgba(0, 0, 0, 0.75);
    backdrop-filter: blur(6px);
    display: flex; align-items: center; justify-content: center;
    z-index: 1000;
    padding: 0.75rem;
    opacity: 0; pointer-events: none;
    transition: opacity 0.3s ease;
  }
  .book-overlay.open { opacity: 1; pointer-events: auto; }

  .book-modal {
    background: var(--card-bg);
    border: 1px solid var(--line);
    border-radius: 10px;
    width: 100%; max-width: 1000px;
    height: auto; min-height: min(520px, 90vh); max-height: 92vh;
    display: flex; flex-direction: column;
    box-shadow: 0 30px 60px rgba(0,0,0,0.4);
    transform: scale(0.95) translateY(10px);
    transition: transform 0.35s cubic-bezier(0.16, 1, 0.3, 1);
    overflow: hidden;
  }
  .book-overlay.open .book-modal { transform: scale(1) translateY(0); }

  .book-header {
    display: flex; align-items: center; justify-content: space-between;
    padding: 0.75rem 1.5rem;
    border-bottom: 1px solid var(--line);
    background: rgba(181,98,46,0.03);
    flex-shrink: 0;
  }
  .book-header h2 { margin: 0; font-size: 1.2rem; color: var(--ink); font-weight: 600; }
  
  .close-btn {
    background: none; border: none; font-size: 1.4rem;
    cursor: pointer; color: var(--ink); opacity: 0.7;
    width: 32px; height: 32px; border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    transition: background 0.2s, opacity 0.2s;
  }
  .close-btn:hover { background: var(--folder); opacity: 1; }

  .book-body {
    display: grid;
    grid-template-columns: 1fr 1fr;
    flex: 1 1 auto;
    min-height: min(var(--book-h, 0px), calc(92vh - 115px));
    grid-template-rows: minmax(0, 1fr);
    overflow: hidden;
    position: relative;
    /* Removed the forced line grid background that caused vertical stretching gaps */
    background: var(--card-bg);
  }
  
  .book-body::after {
    content: "";
    position: absolute;
    top: 0; bottom: 0; left: 50%;
    width: 2px;
    background: linear-gradient(180deg, transparent, var(--line) 15%, var(--line) 85%, transparent);
    transform: translateX(-50%);
    pointer-events: none;
    z-index: 2;
  }

  .notebook-page {
    padding: 1.4rem 2rem 1.4rem 2.6rem;
    min-height: 0;
    overflow-y: auto;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
  }
  
  /* Book-style text: real bullets, hanging indents, tight spacing */
  .notebook-content {
    line-height: 1.5;
    color: var(--card-text);
    word-break: break-word;
    overflow-wrap: break-word;
    font-size: clamp(1rem, 1.05rem + 0.2vw, 1.2rem);
    margin: 0;
    width: 100%;
  }
  .notebook-content h3 {
    margin: 0 0 0.7rem; font-size: 1.25em; font-weight: 600;
    color: var(--ink); padding-bottom: 0.2rem;
    border-bottom: 1px solid var(--line);
  }
  .notebook-content ul { margin: 0; padding-left: 1.1rem; list-style: disc; }
  .notebook-content ul ul { list-style: circle; margin: 0.3rem 0 0; padding-left: 1.1rem; }
  .notebook-content li { margin: 0 0 0.3rem; padding-left: 0.1rem; }
  .notebook-content > ul > li { margin-bottom: 1.1rem; }
  .notebook-content > ul > li > b { color: var(--ink); }
  .notebook-content li::marker { color: var(--rust); }
  .notebook-content p { margin: 0 0 0.9rem; text-indent: 1.2em; }
  .notebook-content p.no-indent { text-indent: 0; }

  /* Scientist portraits: taped polaroid-style photo with a name label underneath */
  .notebook-content li.sci::after { content: ""; display: block; clear: both; }
  .portrait {
    float: right;
    width: 122px;
    margin: 0.15rem 0.3rem 0.5rem 1rem;
    padding: 6px 6px 7px;
    background: #f5f0e4;
    border: 1px solid #d9d0bb;
    border-radius: 2px;
    box-shadow: 0 6px 14px rgba(0,0,0,.28), 0 1px 2px rgba(0,0,0,.2);
    transform: rotate(2.5deg);
    transition: transform .35s cubic-bezier(0.2, 0.8, 0.2, 1), box-shadow .35s ease;
    position: relative;
  }
  li.sci:nth-child(even) .portrait { transform: rotate(-2.5deg); }
  .portrait:hover { transform: rotate(0deg) scale(1.05); box-shadow: 0 10px 22px rgba(0,0,0,.35); }
  .portrait::before {
    content: ""; position: absolute; top: -9px; left: 50%;
    width: 46px; height: 16px;
    transform: translateX(-50%) rotate(-3deg);
    background: rgba(181,98,46,.4);
    border: 1px solid rgba(181,98,46,.25);
  }
  .portrait img {
    display: block; width: 100%; aspect-ratio: 4 / 5; object-fit: cover;
    filter: sepia(.3) contrast(1.05);
    border: 1px solid rgba(0,0,0,.18);
  }
  .portrait figcaption {
    margin-top: 0.4rem; text-align: center;
    font-style: italic; font-size: 0.78rem; line-height: 1.15;
    color: #3b3226; letter-spacing: .01em;
  }
  .portrait figcaption::before {
    content: ""; display: block; width: 26px; height: 2px;
    margin: 0 auto 0.3rem; background: var(--rust); border-radius: 2px;
  }

  /* ---------- Week 1 study notes: numbered sections, chips, diagrams ---------- */
  .nt { font-size: 0.9em; line-height: 1.4; }
  .nt h3.sec {
    display: flex; align-items: center; gap: 0.55rem;
    margin: 0 0 0.5rem; font-size: 1.15em;
  }
  .nt h3.sec:not(:first-child) { margin-top: 0.9rem; }
  .num {
    flex: 0 0 auto; width: 1.6em; height: 1.6em; border-radius: 50%;
    background: var(--rust); color: #fff; font-size: 0.8em; font-weight: 700;
    display: inline-flex; align-items: center; justify-content: center;
    box-shadow: 0 2px 6px rgba(181,98,46,.4);
  }
  .notebook-content ul.pts > li { margin-bottom: 0.4rem; }
  .hl {
    color: var(--ink); font-weight: 600; white-space: nowrap;
    background: rgba(181,98,46,.22); border: 1px solid rgba(181,98,46,.5);
    padding: 0 0.45em; border-radius: 6px;
  }
  .ltr {
    display: inline-flex; align-items: center; justify-content: center;
    min-width: 1.5em; height: 1.5em; border-radius: 6px;
    background: var(--rust); color: #fff; font-weight: 700; font-style: italic;
    font-size: 0.9em; line-height: 1; box-shadow: 0 1px 3px rgba(0,0,0,.25);
  }
  .flow { display: flex; flex-wrap: wrap; align-items: center; gap: 0.3rem; margin: 0.4rem 0 0.1rem; }
  .flow i { font-style: normal; color: var(--rust); font-weight: 700; }
  .chip {
    color: var(--ink); background: rgba(46,125,107,.16);
    border: 1px solid rgba(46,125,107,.55); border-radius: 999px;
    padding: 0.1rem 0.65rem; font-size: 0.95em;
  }
  .chip small { opacity: .8; }

  .notebook-content ul.names {
    list-style: none; padding: 0; margin: 0.4rem 0 0;
    display: grid; grid-template-columns: 1fr 1fr; gap: 0.35rem 0.6rem;
  }
  .notebook-content ul.names > li {
    margin: 0; padding: 0.2rem 0.55rem; border-radius: 8px;
    border: 1px solid var(--line); background: rgba(127,127,127,.07);
    display: flex; align-items: center; gap: 0.5rem;
  }

  table.shells { width: 100%; border-collapse: separate; border-spacing: 3px; text-align: center; margin: 0.1rem 0 0; }
  table.shells th {
    text-align: left; font-size: 0.78em; font-weight: 600; opacity: .75;
    letter-spacing: .02em; padding-right: 0.3rem; white-space: nowrap; width: 1%;
  }
  table.shells td { background: rgba(46,125,107,.14); border-radius: 6px; padding: 0.1rem 0; color: var(--ink); }
  table.shells td.shell { background: var(--rust); color: #fff; font-weight: 700; }
  table.shells td.cap { background: rgba(181,98,46,.18); }

  .orb-rows { display: flex; flex-direction: column; gap: 0.4rem; margin-top: 0.2rem; }
  .orb-row { display: flex; flex-wrap: wrap; align-items: center; gap: 0.4rem 0.6rem; }
  .boxes { display: inline-flex; gap: 3px; flex: 0 0 auto; min-width: 178px; }
  .box {
    width: 23px; height: 23px; border: 1.5px solid var(--orbit); border-radius: 4px;
    background: rgba(46,125,107,.14); color: var(--ink);
    display: inline-flex; align-items: center; justify-content: center;
    font-size: 0.72em; line-height: 1;
  }
  .cap { font-size: 0.95em; }
  .hint { margin: 0.8rem 0 0; font-size: 0.8em; font-style: italic; opacity: .7; }

  .fig {
    margin: 0.7rem 0 0; padding: 0.45rem 0.6rem 0.35rem;
    border: 1px dashed var(--line); border-radius: 10px;
    background: rgba(127,127,127,.06);
  }
  .fig svg { display: block; width: 100%; height: auto; max-height: 175px; }
  .fig.big svg { max-height: 260px; }
  .diagram text { fill: var(--card-text); font-family: inherit; }
  .fig figcaption { text-align: center; font-style: italic; font-size: 0.78em; opacity: .7; margin-top: 0.2rem; }

  /* ---------- About page ---------- */
  .nt.about { font-size: 0.98em; line-height: 1.6; text-align: left; }
  .nt.about h3 { text-align: left; margin-bottom: 0.8rem; }
  .about p { margin: 0 0 0.9rem; text-indent: 0; }
  .about p + p { text-indent: 1.4em; }
  .about p.dropcap::first-letter {
    float: left; font-size: 3.2em; line-height: 0.82; font-weight: 700;
    padding: 0.06em 0.12em 0 0; color: var(--rust);
  }
  .about-side { padding-top: 0.4rem; }
  .sig {
    display: flex; align-items: center; gap: 0.8rem;
    font-style: italic; font-size: 1.3em; color: var(--ink); white-space: nowrap;
  }
  .sig::before, .sig::after { content: ""; flex: 1; height: 1px; background: var(--line); }
  .portrait.solo {
    float: none; width: min(240px, 72%); margin: 1.6rem auto 0.4rem;
    padding: 9px 9px 12px; transform: rotate(-2deg);
  }
  .portrait.solo img { filter: none; }
  .portrait.solo figcaption { font-size: 1rem; margin-top: 0.6rem; }
  .portrait.solo::before { width: 60px; height: 20px; top: -11px; }

  svg.spin { cursor: grab; touch-action: pan-y; user-select: none; }
  svg.spin.grabbing { cursor: grabbing; }

  .book-footer {
    display: flex; align-items: center; justify-content: space-between;
    padding: 0.6rem 1.5rem;
    border-top: 1px solid var(--line);
    background: rgba(181,98,46,0.02);
    flex-shrink: 0;
  }
  
  .page-nav-btn {
    background: var(--folder); border: 1px solid var(--line);
    color: var(--ink); padding: 0.4rem 1rem; border-radius: 6px;
    cursor: pointer; font-family: inherit; font-size: 0.85rem;
    display: flex; align-items: center; gap: 0.4rem;
    transition: background 0.2s, transform 0.2s, opacity 0.2s;
  }
  .page-nav-btn:hover:not(:disabled) { background: var(--folder-dark); transform: translateY(-1px); }
  .page-nav-btn:disabled { opacity: 0.3; cursor: not-allowed; }

  .page-indicator {
    font-size: 0.8rem; opacity: 0.7; letter-spacing: 0.05em;
    text-transform: uppercase;
  }

  @media (max-width: 768px) {
    body { padding: 1rem 0.75rem 2rem; }
    .rack { grid-template-columns: repeat(2, 1fr); gap: 0.85rem; }
    .book-modal { max-height: 90vh; width: 100%; }
    .book-body { grid-template-columns: 1fr; }
    .book-body::after { display: none; }
    .notebook-page { padding: 1rem 1.25rem 1rem 2.2rem; }
    .portrait { width: 100px; margin-left: 0.8rem; }
    .book-header { padding: 0.6rem 1rem; }
    .book-footer { padding: 0.5rem 1rem; }
  }

  /* ---------- Duck strip (decorative, non-interactive) ---------- */
  body{ padding-bottom: 7.5rem; }
  .duck-strip{
    position:fixed; left:0; right:0; bottom:0; height:96px;
    z-index:60; pointer-events:none; user-select:none; -webkit-user-select:none;
    overflow:hidden;
    --water-a:#8fd3df; --water-b:#4a9fb6;
    background: linear-gradient(180deg, transparent 0, color-mix(in srgb, var(--folder) 38%, transparent) 100%);
  }
  [data-theme="dark"] .duck-strip{ --water-a:#4a97a8; --water-b:#245a6b; }
  .duck-strip canvas{ position:absolute; left:0; bottom:0; width:100%; height:96px; }
  #wBack{ z-index:1; } #wFront{ z-index:4; }
  .duck{
    position:absolute; left:20%; bottom:12px; width:34px; height:30px; z-index:3;
    transform-origin: 50% 100%; will-change: transform;
  }
  .duck svg{ width:100%; height:100%; display:block; overflow:visible; }
  .noodle{ position:absolute; bottom:10px; z-index:2; will-change: transform; }
  .noodle svg{ display:block; overflow:visible; filter: drop-shadow(0 1px 1.5px rgba(0,0,0,.22)); }
  .duck-strip::after{
    content:""; position:absolute; inset:0; z-index:5; pointer-events:none;
    background: linear-gradient(90deg, var(--paper) 0, transparent 8%, transparent 92%, var(--paper) 100%);
    opacity:.9;
  }

  /* ---------- Island button (Review or Play) ---------- */
  .island-wrap{position:relative; margin-top:.9rem;}
  .island{--sand-a:#f8e6b8; --sand-b:#e2bf7a; --sea-a:#8fd3df; --sea-b:#4a9fb6;
    display:block; position:relative; width:250px; max-width:80vw; padding:0; border:0; background:none; cursor:pointer;
    -webkit-tap-highlight-color:transparent; transition:transform .3s cubic-bezier(.2,.8,.2,1), filter .3s;}
  [data-theme="dark"] .island{--sand-a:#d9bf88; --sand-b:#a98a52; --sea-a:#3f8fa1; --sea-b:#245a6b;}
  .island:hover{transform:translateY(-3px); filter:drop-shadow(0 8px 10px rgba(0,0,0,.2));}
  .island:focus-visible{outline:3px solid var(--rust); outline-offset:4px; border-radius:24px;}
  .island svg{display:block; width:100%; height:auto; overflow:visible; animation:isl-bob 3s ease-in-out infinite;}
  .island .palm{transform-box:fill-box; transform-origin:50% 100%; animation:isl-sway 3s ease-in-out infinite;}
  .isl-label{position:absolute; left:11%; width:55%; bottom:26%; text-align:center; pointer-events:none;
    font:700 .8rem/1 "Iowan Old Style",Georgia,serif; letter-spacing:.02em; color:#6a4620;}
  @keyframes isl-bob{50%{transform:translateY(-3px);}}
  @keyframes isl-sway{0%,100%{transform:rotate(-2deg);} 50%{transform:rotate(2.5deg);}}
  .island-menu{position:absolute; top:calc(100% + 4px); left:50%; transform:translateX(-50%); z-index:90;
    display:flex; gap:.35rem; padding:.35rem; background:var(--card-bg); border:1px solid var(--line);
    border-radius:99px; box-shadow:0 10px 24px rgba(0,0,0,.2);}
  .island-menu[hidden]{display:none;}
  .island-menu button{font:inherit; font-size:.85rem; padding:.45rem .95rem; border:0; border-radius:99px;
    background:transparent; color:var(--ink); cursor:pointer; white-space:nowrap; transition:background .2s;}
  .island-menu button:hover{background:var(--folder);}
  .island-menu button[aria-checked="true"]{background:var(--orbit); color:#fff;}

  /* ---------- Game HUD ---------- */
  .duck-strip.playing{pointer-events:auto; cursor:pointer; touch-action:none;}
  .duck-hud{position:fixed; left:0; right:0; bottom:102px; z-index:61; display:none; flex-wrap:wrap; justify-content:center;
    gap:.4rem; padding:0 .5rem; pointer-events:none; font:600 .78rem/1 "Iowan Old Style",Georgia,serif; color:var(--ink);}
  .duck-hud.on{display:flex;}
  .duck-hud span{background:var(--card-bg); border:1px solid var(--line); padding:.35rem .75rem; border-radius:99px; box-shadow:0 2px 8px rgba(0,0,0,.12);}
  .duck-hud span:empty{display:none;}

  /* ---------- Science cover (hides the stray title / DOCTYPE text above the page) ---------- */
  .sci-cover{position:absolute; top:0; left:0; right:0; z-index:50; display:flex; align-items:center; justify-content:center; gap:.8rem;
    overflow:hidden; user-select:none; -webkit-user-select:none; cursor:default; border-bottom:1px dashed var(--line);
    background:
      linear-gradient(rgba(46,125,107,.11) 1px,transparent 1px) 0 0/24px 24px,
      linear-gradient(90deg,rgba(46,125,107,.11) 1px,transparent 1px) 0 0/24px 24px,
      linear-gradient(180deg,#d9ebe4,var(--paper));}
  [data-theme="dark"] .sci-cover{background:
      linear-gradient(rgba(120,210,185,.09) 1px,transparent 1px) 0 0/24px 24px,
      linear-gradient(90deg,rgba(120,210,185,.09) 1px,transparent 1px) 0 0/24px 24px,
      linear-gradient(180deg,#123832,var(--paper));}
  .sci-cover svg{height:min(60px,72%); width:auto; flex:none;}
  .sci-cover .orb{transform-box:fill-box; transform-origin:center; animation:sci-spin 30s linear infinite;}
  .sci-cover-text{display:flex; align-items:baseline; flex-wrap:wrap; gap:.2rem .7rem; font-family:"Iowan Old Style",Georgia,serif; color:var(--ink); line-height:1.15;}
  .sci-cover-text b{font-size:1rem; font-weight:600; letter-spacing:.18em; text-transform:uppercase;}
  .sci-cover-text small{font-size:.72rem; opacity:.65; letter-spacing:.06em;}
  .sci-cover i{position:absolute; top:50%; transform:translateY(-50%); font:italic .95rem Georgia,serif; color:var(--orbit); opacity:.35;}
  /* Bottom cover: same look as the top one, flipped, hides the host's "This site is open source" footer */
  .sci-cover.bottom{top:auto; bottom:auto; border-bottom:none; border-top:1px dashed var(--line); min-height:64px;
    background:
      linear-gradient(rgba(46,125,107,.11) 1px,transparent 1px) 0 0/24px 24px,
      linear-gradient(90deg,rgba(46,125,107,.11) 1px,transparent 1px) 0 0/24px 24px,
      linear-gradient(0deg,#d9ebe4,var(--paper));}
  [data-theme="dark"] .sci-cover.bottom{background:
      linear-gradient(rgba(120,210,185,.09) 1px,transparent 1px) 0 0/24px 24px,
      linear-gradient(90deg,rgba(120,210,185,.09) 1px,transparent 1px) 0 0/24px 24px,
      linear-gradient(0deg,#123832,var(--paper));}
  .sci-cover.bottom svg{height:min(34px,60%);}
  @keyframes sci-spin{to{transform:rotate(360deg);}}
  @media (max-width:700px){ .sci-cover i{display:none;} }
  @media (prefers-reduced-motion:reduce){ .island svg,.island .palm,.sci-cover .orb{animation:none;} }


  .od{display:flex; flex-wrap:wrap; align-items:flex-start; gap:.4rem .7rem; margin:.2rem 0 .7rem;} .od-g{text-align:center;} .od-bx{display:flex;}
  .od-b{width:26px; height:26px; margin-right:-1.5px; border:1.5px solid currentColor; display:flex; align-items:center; justify-content:center; font-size:.8rem; line-height:1; font-weight:700; letter-spacing:0;}
  .od-g small{font-size:.65rem; opacity:.75;} .od-chip{font-weight:700; font-size:.8rem; line-height:26px;}
  .auf{display:grid; grid-template-columns:44px repeat(4,1fr); gap:3px; max-width:320px; text-align:center; font:600 .8rem Georgia,serif;}
  .auf>b{opacity:.7; font-size:.7rem; align-self:center;}
  .au-c{padding:.3rem 0; border-radius:6px; color:#1f2b33;} .au-c sup{font-size:.55rem; margin-left:1px; opacity:.7;}
  .au-c.s{background:#f6b89a;} .au-c.p{background:#9fd8c6;} .au-c.d{background:#a9c8ef;} .au-c.f{background:#cdb8ee;}
  .quiz-opts .od{margin:0; gap:.2rem .5rem;} .quiz-opts .od-b{width:20px; height:20px; font-size:.68rem;} .quiz-opts .od-g small{font-size:.58rem;}
  /* ---------- Periodic table ---------- */
  .fo{font:600 .82rem/1.7 "Iowan Old Style",Georgia,serif; padding:.5rem .7rem; border-radius:10px; background:rgba(127,127,127,.12);}
  .diag{margin:.4rem 0 0; padding:.5rem .8rem; border-radius:10px; background:rgba(127,127,127,.12); font:600 .8rem/1.5 ui-monospace,Menlo,monospace; display:inline-block;}
  .pt-info{display:flex; gap:.8rem; align-items:flex-start; padding:.6rem; border-radius:12px; background:rgba(127,127,127,.12); margin-bottom:.5rem; font-size:.82rem; line-height:1.45;}
  .pt-big{flex:none; width:74px; height:84px; border-radius:10px; color:#1f2b33; display:flex; flex-direction:column; align-items:center; justify-content:center; position:relative;}
  .pt-big i{position:absolute; top:5px; left:7px; font:600 .7rem Georgia,serif; font-style:normal;} .pt-big b{font-size:1.7rem;} .pt-big small{font-size:.65rem;}
  .pt-txt h4{margin:0 0 .2rem; font-size:1rem;} .pt-full{opacity:.7; font-size:.75rem;}
  .pt-leg{display:flex; gap:.3rem; margin-bottom:.4rem;} .pt-leg span,.pt-h{padding:.1rem .5rem; border-radius:99px; font:700 .68rem Georgia,serif; color:#1f2b33; text-align:center;}
  .pt-scroll{overflow-x:auto; padding-bottom:.4rem;}
  .pt-grid{display:grid; grid-template-columns:44px repeat(18,minmax(27px,1fr)); grid-template-rows:auto repeat(7,30px) 8px repeat(2,30px); gap:2px; min-width:560px;}
  .pt-r{font:600 .58rem Georgia,serif; opacity:.75; align-self:center; text-align:right; padding-right:4px;}
  .pt-c{position:relative; border:0; border-radius:4px; padding:0; cursor:pointer; color:#1f2b33; display:flex; align-items:center; justify-content:center; transition:transform .12s;}
  .pt-c i{position:absolute; top:1px; left:2px; font:.44rem Georgia,serif; font-style:normal; opacity:.7;} .pt-c b{font:700 .74rem Georgia,serif; margin-top:4px;}
  .pt-c:hover{transform:scale(1.18); z-index:2;} .pt-c.sel{outline:2px solid var(--rust); z-index:3;}

  /* ---------- Help screen + touch buttons ---------- */
  .duck-help{position:fixed; inset:0; z-index:94; display:flex; align-items:center; justify-content:center; padding:1rem; background:rgba(10,30,36,.45); backdrop-filter:blur(3px);}
  .duck-help[hidden]{display:none;}
  .dh-card{max-width:360px; width:100%; background:var(--card-bg); color:var(--card-text); border:1px solid var(--line); border-radius:20px; padding:1.1rem 1.3rem; text-align:center; font-family:"Iowan Old Style",Georgia,serif; box-shadow:0 24px 50px rgba(0,0,0,.35);}
  .dh-card h3{margin:0 0 .7rem; color:var(--ink);}
  .dh-row{display:flex; align-items:center; justify-content:space-between; gap:.8rem; padding:.45rem .2rem; border-bottom:1px dashed var(--line);}
  .dh-tc{display:none;}
  @media (pointer:coarse){ .dh-pc{display:none;} .dh-tc{display:flex;} }
  .dh-row em{font-style:normal; font-size:.9rem;}
  kbd{display:inline-block; min-width:1.9rem; margin-right:.25rem; padding:.2rem .5rem; border-radius:7px; background:var(--folder); color:var(--ink); border:1px solid var(--line); border-bottom-width:3px; font:700 .8rem Georgia,serif;}
  .dh-chip{padding:.25rem .8rem; border-radius:99px; color:#fff; font:700 .7rem Georgia,serif; letter-spacing:.12em; background:#2b7f9c;} .dh-chip.j{background:#e8961f;}
  .dh-legend{display:grid; gap:.3rem; margin:.8rem 0 .5rem; font-size:.82rem; text-align:left;}
  .dh-go{margin:.4rem 0 0; font-size:.75rem; opacity:.7;}
  .duck-btns{position:fixed; left:0; right:0; bottom:170px; z-index:62; display:none; justify-content:center; align-items:flex-end; gap:1.3rem; pointer-events:none;}
  .duck-btns.on{display:flex;}
  .beach.b2{filter:saturate(1.25) brightness(1.06);}
  .beach.b2::before{content:''; position:absolute; right:-4px; top:-40px; width:46px; height:46px; border-radius:50%; background:radial-gradient(circle,#fff6c2 0 38%,#ffcf5c 60%,rgba(255,190,80,0) 72%); animation:sunpulse 2.5s ease-in-out infinite;}
  @keyframes sunpulse{50%{transform:scale(1.1); opacity:.85;}}
  .dbtn{width:62px; height:62px; border-radius:50%; border:2px solid rgba(255,255,255,.9); pointer-events:auto; color:#fff; background:#2b7f9c; display:grid; place-content:center; justify-items:center; gap:1px;
    font:700 .56rem Georgia,serif; letter-spacing:.1em; touch-action:none; user-select:none; -webkit-user-select:none; -webkit-tap-highlight-color:transparent; box-shadow:0 3px 10px rgba(0,0,0,.25); transition:transform .1s;}
  .dbtn.jump{background:#e8961f;}
  .dbtn:active{transform:scale(.92);}
  .quiz-card.easy{border-color:var(--orbit); box-shadow:0 24px 50px rgba(46,125,107,.35);}

  /* ---------- Quiz card ---------- */
  .quiz-back{position:fixed; inset:0; z-index:95; display:none; align-items:center; justify-content:center; padding:1rem; background:rgba(10,20,20,.4); backdrop-filter:blur(3px);}
  .quiz-back.on{display:flex; animation:qfade .8s ease;}
  @keyframes qfade{from{opacity:0;}}
  .quiz-card{width:100%; max-width:440px; background:var(--card-bg); color:var(--card-text); border:1px solid var(--line); border-radius:16px; padding:1.1rem 1.2rem 1.2rem; box-shadow:0 24px 50px rgba(0,0,0,.35); font-family:"Iowan Old Style",Georgia,serif;}
  .quiz-tag{font-size:.72rem; letter-spacing:.08em; text-transform:uppercase; color:var(--orbit); font-weight:700; margin-bottom:.5rem;}
  .quiz-q{margin:0 0 .8rem; font-size:1.1rem; line-height:1.4; color:var(--ink);}
  .quiz-opts{display:grid; gap:.45rem;}
  .quiz-opts button{display:flex; gap:.6rem; align-items:center; text-align:left; font:inherit; font-size:.95rem; padding:.55rem .75rem; border:1px solid var(--line); border-radius:10px; background:transparent; color:var(--ink); cursor:pointer; transition:background .2s,border-color .2s;}
  .quiz-opts button b{flex:none; width:1.6rem; height:1.6rem; border-radius:50%; background:var(--folder); display:grid; place-items:center; font-size:.8rem;}
  .quiz-opts button:hover:not(:disabled){background:var(--folder);}
  .quiz-opts button:disabled{cursor:default;}
  .quiz-opts button.ok{background:rgba(46,125,107,.22); border-color:var(--orbit);}
  .quiz-opts button.no{background:rgba(181,98,46,.22); border-color:var(--rust);}
  .quiz-fb{min-height:1.2rem; margin:.7rem 0 .2rem; font-size:.9rem; color:var(--ink);}
  .quiz-next{font:inherit; font-size:.9rem; padding:.5rem 1.1rem; border:0; border-radius:99px; background:var(--orbit); color:#fff; cursor:pointer;}
  .quiz-next[hidden]{display:none;}

  .quiz-card.medium{border-color:#4a9fb6; box-shadow:0 24px 50px rgba(74,159,182,.38);}
  .quiz-card.medium .quiz-tag{color:#2a7fa0;}
  [data-theme="dark"] .quiz-card.medium .quiz-tag{color:#7cc4dc;}
  .gull{position:absolute; left:0; bottom:27px; width:46px; height:32px; z-index:3; will-change:transform; pointer-events:none;}
  .gull svg{display:block; overflow:visible; filter:drop-shadow(0 1px 1.5px rgba(0,0,0,.3));}
  .gull .wing{transform-origin:24px 18px; animation:gflap .5s ease-in-out infinite alternate;}
  @keyframes gflap{from{transform:scaleY(1);} to{transform:scaleY(-.55);}}
  @media (prefers-reduced-motion:reduce){ .gull .wing{animation:none;} }
  .quiz-card.hard{border-color:var(--rust); box-shadow:0 24px 50px rgba(181,98,46,.4);}
  .quiz-card.hard .quiz-tag{color:var(--rust);}
  .beach{position:absolute; bottom:8px; width:160px; z-index:2; display:none; pointer-events:none;}
  .beach.on{display:block; animation:beach-rise .8s cubic-bezier(.2,.8,.2,1) both;}
  .beach svg{display:block; width:100%; height:auto; overflow:visible;}
  .zz text{animation:zz 2.5s ease-in-out infinite;} .zz text:nth-child(2){animation-delay:.7s;}
  @keyframes beach-rise{from{transform:translateY(46px); opacity:0;}}
  @keyframes zz{0%,100%{opacity:.2;} 50%{opacity:1;}}
  .duck-hud .hb{pointer-events:auto; font:inherit; font-size:.78rem; padding:.35rem .9rem; border:0; border-radius:99px; background:var(--orbit); color:#fff; cursor:pointer;}
  .duck-hud .hb[hidden]{display:none;}
</style>
</head>
<body>

<div class="header-container">
  <button class="theme-toggle" id="theme-toggle">🌓 Theme</button>
  <h1>Ten Weeks of Science</h1>
  <p class="sub">by Canaya Hans &nbsp;·&nbsp; click a folder to open notes</p>
  <p class="badge">Laguna Science National High School Study Hub</p>
  <div class="island-wrap">
    <button class="island" id="islandBtn" aria-haspopup="true" aria-expanded="false" aria-controls="islandMenu" aria-label="Review or Play">
      <svg viewBox="0 0 260 110" aria-hidden="true">
        <defs>
          <linearGradient id="sandG" x1="0" y1="0" x2="0" y2="1"><stop offset="0" style="stop-color:var(--sand-a)"/><stop offset="1" style="stop-color:var(--sand-b)"/></linearGradient>
          <linearGradient id="seaG" x1="0" y1="0" x2="0" y2="1"><stop offset="0" style="stop-color:var(--sea-a)"/><stop offset="1" style="stop-color:var(--sea-b)"/></linearGradient>
        </defs>
        <ellipse cx="130" cy="94" rx="124" ry="13" fill="url(#seaG)"/>
        <path d="M12 94c22-2 30 4 52 2M196 100c20-2 34 3 54 0" stroke="#fff" stroke-opacity=".55" stroke-width="2" fill="none" stroke-linecap="round"/>
        <g class="palm" fill="none" stroke-linecap="round"><g stroke="#ff7f96" stroke-width="7"><path d="M50 80V46M50 64L36 50M50 56L64 42"/></g><g fill="#ffa8b8" stroke="none"><circle cx="50" cy="44" r="5"/><circle cx="35" cy="48" r="4.5"/><circle cx="65" cy="40" r="4.5"/></g></g>
        <g class="palm" style="animation-delay:-1s" fill="none" stroke-linecap="round"><g stroke="#ffb15c" stroke-width="7"><path d="M130 66V22M130 50L112 34M130 42L148 28"/></g><g fill="#ffd08a" stroke="none"><circle cx="130" cy="20" r="5"/><circle cx="111" cy="32" r="4.5"/><circle cx="149" cy="26" r="4.5"/></g></g>
        <g class="palm" style="animation-delay:-1.5s"><path d="M206 82L180 44Q206 22 232 44Z" fill="#b58cf0"/><path d="M206 82V34M206 82L190 42M206 82L222 42" stroke="#8f63d8" stroke-width="1.6" fill="none" stroke-linecap="round"/></g>
        <g fill="none" stroke="#fff" stroke-opacity=".7"><circle cx="92" cy="30" r="3"/><circle cx="99" cy="18" r="2"/><circle cx="168" cy="22" r="2.5"/></g>
        <path d="M22 92C40 64 90 60 130 60S220 66 238 92C206 101 54 101 22 92Z" fill="url(#sandG)"/>
        <path d="M56 78c16-8 40-11 62-11" stroke="#fff" stroke-opacity=".45" stroke-width="3" fill="none" stroke-linecap="round"/>
        <defs><filter id="lblShadow" x="-10%" y="-30%" width="120%" height="170%"><feDropShadow dx="0" dy="1.2" stdDeviation="0.8" flood-color="#6a2a3c" flood-opacity=".35"/></filter></defs>
        <g stroke="#ff7f96" stroke-width="2.4" fill="none" stroke-linecap="round" opacity=".8"><path d="M70 75v-6M70 72l-3-3M70 70l3-3"/><path d="M190 75v-6M190 72l-3-3M190 70l3-3"/></g>
        <g text-anchor="middle" filter="url(#lblShadow)" style="font-family:'Fredoka','Nunito','Trebuchet MS',system-ui,sans-serif; font-weight:600; font-size:20px; letter-spacing:.4px">
          <text x="130" y="90" fill="#fffaf0" stroke="#b8365f" stroke-width="4.2" paint-order="stroke" stroke-linejoin="round">Review or Play</text>
        </g>
      </svg>
    </button>
    <div class="island-menu" id="islandMenu" role="menu" hidden>
      <button role="menuitemradio" data-mode="review" aria-checked="true">📖 Review</button>
      <button role="menuitemradio" data-mode="play" aria-checked="false">🦆 Play</button>
    </div>
  </div>
</div>

<div class="rack" id="rack"></div>

<!-- Notebook Modal Overlay -->
<div class="book-overlay" id="bookOverlay">
  <div class="book-modal">
    <div class="book-header">
      <h2 id="bookTitle">Week Title</h2>
      <button class="close-btn" id="closeBook" title="Close notes">&times;</button>
    </div>
    <div class="book-body" id="bookBody">
      <div class="notebook-page"><div class="notebook-content" id="leftPage"></div></div>
      <div class="notebook-page"><div class="notebook-content" id="rightPage"></div></div>
    </div>
    <div class="book-footer">
      <button class="page-nav-btn" id="prevPageBtn">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M9 14L4 9l5-5"/><path d="M20 20v-7a4 4 0 00-4-4H4"/></svg>
        Previous
      </button>
      <span class="page-indicator" id="pageIndicator">Spread 1 of 1</span>
      <button class="page-nav-btn" id="nextPageBtn">
        Next
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M15 14l5-5-5-5"/><path d="M4 20v-7a4 4 0 014-4h12"/></svg>
      </button>
    </div>
  </div>
</div>

<script>
  const photos = {
    broglie: "data:image/jpeg;base64,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",
    heisenberg: "data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAYEBAUEBAYFBQUGBgYHCQ4JCQgICRINDQoOFRIWFhUSFBQXGiEcFxgfGRQUHScdHyIjJSUlFhwpLCgkKyEkJST/2wBDAQYGBgkICREJCREkGBQYJCQkJCQkJCQkJCQkJCQkJCQkJCQkJCQkJCQkJCQkJCQkJCQkJCQkJCQkJCQkJCQkJCT/wAARCAFFAQQDASIAAhEBAxEB/8QAHwAAAQUBAQEBAQEAAAAAAAAAAAECAwQFBgcICQoL/8QAtRAAAgEDAwIEAwUFBAQAAAF9AQIDAAQRBRIhMUEGE1FhByJxFDKBkaEII0KxwRVS0fAkM2JyggkKFhcYGRolJicoKSo0NTY3ODk6Q0RFRkdISUpTVFVWV1hZWmNkZWZnaGlqc3R1dnd4eXqDhIWGh4iJipKTlJWWl5iZmqKjpKWmp6ipqrKztLW2t7i5usLDxMXGx8jJytLT1NXW19jZ2uHi4+Tl5ufo6erx8vP09fb3+Pn6/8QAHwEAAwEBAQEBAQEBAQAAAAAAAAECAwQFBgcICQoL/8QAtREAAgECBAQDBAcFBAQAAQJ3AAECAxEEBSExBhJBUQdhcRMiMoEIFEKRobHBCSMzUvAVYnLRChYkNOEl8RcYGRomJygpKjU2Nzg5OkNERUZHSElKU1RVVldYWVpjZGVmZ2hpanN0dXZ3eHl6goOEhYaHiImKkpOUlZaXmJmaoqOkpaanqKmqsrO0tba3uLm6wsPExcbHyMnK0tPU1dbX2Nna4uPk5ebn6Onq8vP09fb3+Pn6/9oADAMBAAIRAxEAPwD3Dkd6UZPemrTuACT+lADWGeCaaQBxuJpW9TTWPagBf89aXOf/ANdRbsGnKw6UAOOCaAFwOTnJyO1JkMQOB9TTcrjgYNAAx54NB5PWm7qUGgCSLr1qwCdnWoEYGpSRgdaABumc1Uk69qsFgBzVRjzQAfjSEZ7mignFAAM9KXFNDU/sKAI2J6/hVS6lKo3XGPrVmZwgyTgVx/jXx/pPhK0eS6lV5wAy24bDuDxkUAUvEzhreQIckZ4zzXjGt4+0cgE8nNdXL8StH1iaeLzHgc/Ohfr9BXH6xdwXNw4SXAXBBI5JPpj8aAKDcqPfjikQEZ3Fgp6470Fhn6U7zAY+XZT0OB1HH+FADcfPkdBU2cqpznHXIqPzFKj5WVieQeRTkIX5igYjoD0/Ed6AJlYv0AH0oLjkDjtkfzqNZlwrB9rdG+Xj8PT6U/zA0OzCB1IPmBhuIwcgj06UAMQNLlT2OfrT1kVY2Qx4LdCCflpmWKFW2nODkjJGOlNJ+QnaMjtjpzQBZIWVQyHquCO+R3qdIiFALDIwOvJqvC7ojgOp7nIyfyq1FMfPjDuFjBG7jGR70ATpGiqP3jAnkggHB/OirCIkg3LIyD+6zLkUUAfUSn0pd2DzTVXFJjOTQANIGBFNJpSoA603HNACYBpy8UlGTQAhPNMcEg4wMc8040mKAGxlgCGwTnrT8gHFA4pM5NAEyVIenWo0yRUvagCNuhquetWCQy5HSoMZzQAwkjtRkHr/APqrN1LxDYaXbT3N5dwW8EI+Z3PT/wCv7V4d4w/aBu71JrHw/bm3MjFRcuTnb6getAHtPiHxdpHhy286+vYIADj5mGT+HWvNfEH7SWj2qtDotpNeS4+V5RsTP8zXgWsalqOpXBkvbqa4dhk7+fyHaq8NsTEASNvQHHT2+tAHrp/aW1mWT95o1iyYI+VjnNeb+KfFF/4q1WXU78gNINqxqMBF9BWcbYIw+YY4wMdagKEsEYnJzx3oAaXbcu04AHpVuHUvLT5iSfrzVTy1BdR5m5e56fyp5s2ZDuDLuBK56YFAGjb60YVkZ08wlgFOegxVhNbQR/vIigH8XXNYIjkX92IzwckHjFO2Oo+WMtuIJwOlAHSwXaXC74XDDPp0/CrMbllIkcfXGK5OM3EDh4ZNuOcZxmt7T9Ta6jWOZUEowvJ+9z/OgDQThwo5zU0UTMC24BTwRnn8qr4bcVb5COOtSQMVIIJ3DvQAzeInK4IzxUok3MecnFMKDGOg9qcQAMAjjvQBNBtMnGyLcMHA4p5PzrskxtA5FVsruHzHPHGKn3KCAqcdvxoAtmYMSWBJ7kDNFQogIyWx+BNFAH10M005A/Gn0nXNADMkikxR0ooADgdaTIPrQxzQKAG0YI4YEHuPSl25pxTueaAIyecUYp4UFuKd5fegB0Q45qc7fLJJ496jRflrL1+5ure2L2y7to3YBweB+tAFszqsohz94ErXO+NPFtt4T01ryeZUbkIh6u3YCuVPxXsPKMs6OskTcrnDDjrj0ryfxv4yuvGV815cKIoIQfIiHIHv9TQBg+L/ABdqvi6Vfts7+UgYpET8uc5Jx/Wuet7YFN7AbiDj/Gtd7eKQMGViyrwFXBPTI/WpP7PCwqpzGSPlz6H1oAxvsjyo6opYIC5AODir9haJBA7OruxO2NQOP94/jV2HSpGYxhG352crzWquhzQSFGibGVTpgbm6Y5HYUAcwbUpIDtwTgEnuT/8AqpBbb2VYwN56tjknv9AK6g6YtkgnlUtiUKiMvMhxkg9fYce9JJbR2ijzcpNJNhgP+WaAdM+pbj6CgDn7exjtiN2AgA3PjJJz6H16Uy4tWd95TaGOc+tbH2L7Qm6NAzZwg67UH8P6dabJCVtluyrK75424Cr0Ax270AZMdgXYgg/PyWb071YGkIQN0pVX5UZ4x61JbGRTvOzaMsQRnjv9aglvZHl3nDbvmAPAFACNpdoYyiSkEfxbcA/Sqo05YWM0U30DgdPUVPHNG67mQtnuZDn8quxWlu6hrh/4cbfT06UAVLbV2MMcE6YYdXB5J7fQVdjeN+ox9Tmo0QfNGIgUBI3Kpb/JqxHDZRI2LlHkPCqAykH+VADB1ADbh9KlKZXAIJ7EU0KVbpkHoRTo2wckMMetACBMjgj0681KuXIOcHbt3Y71GEUDqcH3qxE4VNrAAqBgE9KALCwyEDLpkdcsBRULupI2kAYHAFFAH1+BTDwaeKY3WgBhG400mngcmmspFADCaAeKMUvagBwI70vykYpooxQA8YB4NKSMUylzkc9qAGyvKY2WLbuxxnpXhvxo1vX7J1gu57W0idiY1tpGLOPRhXrfivW4PD2iXOozsypCm47cZ/DNfIfjfxXN4p1Wa/8ALlihlbCozByAOmaACDUGnmQySu7AEYzkkdMZrfsPDF9eW8ZSJVjY4DF8YPUA1heFNP8APdJgu0L8zEjGBXu3ha3FvFHHvY71xlVIG3r1/rQByWneAbqW0hlMbtIhZTEWGHUkc/pWvafDx/MUssfynIEnJZR1yPXmvSbSL90qg5Q87vx6fyrSS1gcb1UA4K5HpQBwOnfD6zuFQTWqxsBuYrnlickHtjpW3c+DALmGcqswViWY9CcADA/OuxgtUVVIjUHH51a8hV9KAPI7/wACv/aFvNHgtCXdFIwNxPX9aNO+E0ss7vdPG1ux3hQSGLnqTmvW/sqbt5UZ6VKEUDG0Y7jFAHmU3w9t4FjNjAkezJ3ldxbPfNVZvhravZsskfmSbsoDwDn/AAr1GSBGfdgcDj0qGW3QhigG8jjuPp9KAPm7W/CLWsr2lnG1xL8yjP3VIPJ4rjNV0ttNykoY4O18duM19M614fW5t5griN5gImPovc+xrzzxP4TsBpr3EUbrFghgPmLFcj69hQB4xb35tWJCws4BPTKoMdfrWzpt2s6fu5c8lpDI5O7jgfKPWsS7hCyiLHy55Ujt6H861tMsmMTBZpYXJJAjT5T+IoAs30BCCSF4X3DcVjYq6+2CKh0/ULO43Q6jFcLgfI+FI3dBn2qaSKO3kEdzOzoecoTxx15HIqIaZHMB5cjSRPwkhUHnsDg8UAT+U0aMu3KkfKT25zkVG5JV2PXIwB3FWZbWS1CwySsuAPvrjH60wIjK2QeBktnr+FAFcAkA4PBzU1ugeULjGQRSOuMDpkdKkiTkbRuJIPzdBQBOqhVAyF9j1oqwU28D+QooA+sA3NMZuelP20wr65oAAc0m4GlAxTSOaAELDsKTNBHNKBQAqt9aduHrTCMUfw596AHbhRuHc0ylAAFAHkP7Q2qPb+HBaq0mJZMHaOPxNfN+lac2oXUcfmoitg5O7/Cvav2mNZlkvLDSFykKoZWOPvN0/lXlegxpb28kpJDNhQR2GaAO40eOK3SO1hPzO2zKR53ehGcV6n4cg+eOQgxmKFYmXtt7V5r4Wjlku0k4ZFYFAP4SPYdBXq+ingMu0jG0vnJ/zmgDoYI+ARt6c4NW4c4254Haoo0PlADAGODV+GBVyQoz3oAkjOBwaduwNxJwKdHGD0GKeYwy7eCO9AEiMzAE80/YeuKdAoIA7irCpQBSlDDpUWcegNXJsAVTkAbgnAHTHegBwt0IKkblYYKnvWRrPh6zvLSaArtDg8qoGM1rRSYwMk/WotRy0ZbICKMk5xQB8j+ONBfRNamsWbdGCSCDnIPPSs7TpDAuRcMgJxhiUz+Ir174h+HrC7854reVriJ2LvB+8dQenB5IrxfVbV7SVljYuMZVmXbkfTtQB0N5LZ3isXEO7dlooWPB9iT/AJNU9MktNM1RIraSZ1kwzRyR85znjB5GKzdMuZowxlRJB/dmBxTtSeSG+hulEiBSGAOD+R7igDpLswy3EjwxtHGWJSMtnAJzUJBGGZZCp+U55P0qyvmSxLIRu35JJOSPrRG7BQgxgmgCnJCUiTLjOWLR46enzd80+1QMwHIGfWpJV3MPc0+FFRgp65xnFAGna2kLwKXdQRxy1FSRT+RGqNArn1Bb+hooA+olTPUU1o8GrAFNYZNAFcx47UxkzVmkIA5oArGPilKrwVGOO5zzUrACm0AREHPQUFeOKkoxigCHYeeaXZUu2gLQB86/tO6Y327Sr1VYiQNEefTn+teZadb+VaojAhjzzg17f+01bt/Yuj3HylVuSpUjPVev6V4taRNKIlV1xwCcYz+FAHe+DYZI3iRuMgYHc/5zXrGhRCGFsDaH6Adq838J2IEagkIw+ZCTlsjocY6dfzr1HR8vEAcsVOBx+lAGpbqxTI2jt0q/B5i5y27NRwr8oG3B64q4F6etABGHAqYAgjAHShcbQMYwOoPWnqqsRyaAFiZsngA1KZ2HG0fXNIqgU1pE6E4/CgCOSVT8pODUY4PtUmAzdQaa6kLwcGgCqrhnJHOCc+1PvED2zqSeRzjrUYAWU84759TTpC5QlCjHHQnrQB5h4kufI1cwwOIrqYlo2Ddcdc98iuF8deEmSwj1OA77onDR7RlzjJ/rXear9gufFsNrcxSJcmQGFz93GCRx69jXL+OdSgspxaGQF1hyjDoJYycjHb+hFAHnFuwn0+O8O2VIX2zRY5K9Me3t9KdYtp8eoTaNJMt1p8sbSW8roQ8Z6gZ9un8qpx30gv5LpMFZOHBHDk9z+WfepbqCM3VtLHEdwO9wnHft7Hr3oA6ZlSNIIN6MQoDlFxj8e+f6UyVER9gztQ4BPXFDxmMZVcgcHn8qGjbClkZCCCBgjj1oApyqsfKyIcdwasQqSqtlH44RDlj7VE0QIw+d3XG7t7VLa2xVwedrHoOfyoAs4L/NFGwQ9Bkf1oq4Ih2ii/FKKAPqUDNNYYqUcUx6AITkUxiakI5prDigCKnAcijBzTgOlADStJg+lSEDcKcQKAI8Y49aNvNOwOhwfejvQB5N+0nAsngiyY5yL5MEdsg14r4at57uaGOLbu4L59Afp6fzr3r9oa0e4+HjSICfs9zFIcdhnH9a8d8HCxhnWS9neFMnacDCn1PegD0rQ9PfYziFFYvg+WuOMcYJ65BzXc6fEdq5yGz7ViaXdW8lsklr9md9vLbxyMdccVfk1kWcSysIEA/6ajk+n1oA6JRgZ4qwp+UE9a5Oy8a2lzMYm+XsT05z/wDWrdi1GO4VFjcHNAGmoORU0aAkY5rLvdRt7XaXcZxkc9faqyeIC7sTEUQYx8wOc0AdAQBxnmmllQ4z+leb6t8VY7e7+yQmLcp/esWwqD1z3PtWvYeLLXUYl2alCWxlgzBMD8cUAdcdrkHIP1prrWRb6lDOokiu4nA6hZAa0Ir5XPlsCG6fNwaAIpI2HTGfeqxYIqlye4yPXFXmDbsnoB6VFJF5iEMOvpQBwfiaC2tJ0u7oEPJuRJRjAbHDAnoRgfWvIvF1xZ61LMrb0umkMpVk24Zh8yg9+mfxr2L4hwQS6fJDMyrEAX3HkqcYGPQ5wa+f76a5t7jF8rNIoADOcZGOCBQBkxwRSStEp+8Bnd179q29NRZr6Hy2+QRqv0/CsATKl7HKhIjHBwP0rqvDMFvdTqsaFZFQrubgMw6fnQBoLGcbkO44JKk4P1qEPvcZyC3G7utWZ1kVgj5BxhlIyOKhQAqqhSG7NjOB1oAQmMqFYPu6/dJ5/PFLAArYQHls8nFNljywIDbiMAdadEwjYYZdxGOnQ0AaSncMkY9MAn+lFJFHI8alsZAx1xRQB9S45pki8VKaY2MUAV8etBGaeAGUH1FIVxQBHt5o7U8imkUANPWndaNuRnNLigBCKAOaU0YoA80/aA1q10/wJJYTHM2oSpFEuAejAk185RRm9uXWS4EW4YG07cL6/SvVv2oHll1bw5b7gE2yHHvuA/OvIf7OkjlkuDNK204wO3OMZoA7LSdB8NnKNJeXU643ywXPkoh7jeTjOOeK1rvwbouqW6RaP4sgS5HzLbXGqGZQBzknGBUPw7+HsGprZ6rqk0X2aKWQSWMwKhge+en4H0rsNF+GcGn+II77QtcNvDLA1tcG1KMssTdiMfnQB5Zqk/iXwreKL2RnQ8xyo4kikPqrA4Nen/DLXbzXnieScyLEoB4IAOev61c+J3gOy0rTrVfD9kphtoRHe27gCOWIDG8ekgIzkdeetZHwCs2hiuXkLMhk2x8cH/PFAHsE2jSSRLIy7228k+tY95pl2FZLZkj3jDgjt9e1di0uxVQcd6zbm2S+DwF2ReCSp6nP60AeN6t4T8LWkrJdSz3axZaQzXCwQpnrliMsfYVNoWo/CuQxW89jYRSk/Kk0ssjOfVSVwfqK2G+H9zeeMYdX1R7KXT4SxjtnP3OeD0w3rz0q7438F2niTUrPVtG1ZbHULMo0U9nIoeLbxjHTHJoASPw94Ou5IbzRLmKxlcbY54HzBIfRiDjJ98Gtu0TUrKBUu1Mjxd1YsfbGeSKxtH+E9vpNvPNBqEsmo3MrPcSYDRXCHkrInRsnnI5Bro9M0+bS4fsc3meQAPKEjeZs9g/Xb6A9KAL9pfx3QVtsoLcFSOc1oAKOMce9UorXBJDHpxgVZQlOTQB5H8bYkE8DrNMr8L5athMccsPwNeV+KLqPVUMxdfMjQRkM/I2jpxxXpHx5eOCSKRjuaaMKVB7A964H4f8Aw7v/AIiamxMxt9Oh4mmUZA/2R6nHegDndF0LVde22mkadcXUjZfMa/KAPU9BXb2vhfVfD1uDqNhLbmRvvvjAOMV9CaP4btPDmjLZaBZW8aRJhR0BPqT1OTXE/wBqa9fa7N4Z8W6JaxxXsbG2u7Ul42wM4OeQaAPN2SO4l2FC3TOSF6evvjPsPxquYlj+VclFO0MQP1xQ8X2G7KKcrHIVweQSCRmiYncFhWBjjLOON2fXjj8KAIrld75GAAO4yDSyJIEVd3l5QE4IAz24Ht605UQt/rcbezZwandVycCDBAIBck/Tkc/SgB1vaXjxDythA4OSW5oqSPzJEBQHaOPu5xRQB9Rd6Q06kIoAiIGOnOfWmmpDUZ5NACMKTFKaTPFACY5p2MCk6UZ9aAAinUlKOaAPAv2nrVxeeGrsLlBK8ZY9B0Nc54P8Mw6pI0kwhkjhfKRMxbcSOpA+vFew/HDwv/wkfgS6aNN1xYkXUZHXK9f0ry34Y6hBC83mM+SC3qB2oA7fSfBMtkS9lqFxCkgBeJtjI3uQa6vTrea3UYmUDPAijVPl7Diord42gUgnIwDg/jUd/d+VCQX2qc5I4OO4oA5P4oeIY4rQ6fAyh7jKM5OcL6D+Vbfwo0QadosAG3LneWC43V5RfahJr3imeFH3xq6xqMcbcjtXv/hW3SysoRtwqqFA9KANG7IL+/Si2j3SFgOoqOYhpDzUtuSpGOfagDO1Lw/ceYZraVgDzsflfw9KjstOuLQEGzgIYjcwwf8ACuoR9wwabIg60AUYfMYDfEQPQYqV4ww5Wns2Peo0lyW64NADJFCocdqpFt3qRVqWQdCT0qqFHagDzL4t+CbnxD9lvbefd5AMbW5BO4HoV9TmtPSzb/CTwdYxTade3Cbh9rNpHuZSeWc+wrqHP2vUIYMN87g9Ow//AFV1BhjmEkboGRsqQR1FAGbpWv2Gr6SlzpU4mtpV3IQMY/Os2f8Ad51C42qbaJ3G4dMj1p+g6ZFpQvraHK26SNtXGAM84H51zfxL1b7JpcOmJIwlujlyp5EYoA8o1Yg3chkGQ7mUbCMc/wCRVHzmV1AXKY5w2DVm9jYkAht3qpyKhjs53DZiY4G4kYOB9KAEQyEl2JcKBk9KmEgl5GRgChIRyygoB2VRUsH3gHkbBPPygY/GgC5biEx5NksmT18wrRRDGGjG2eJQOMZzRQB9NZ5oIOKCOaU0ARHrSbfSnkUhGKAI2GKaBT3600UAJiilwaNmORQAU4Cm4py0AMvLSO+s5rWUZjlQo30IxXzLoFvHoHinUtId3xFcSQDuGA6D2r6hHavmrxORp3xO1+JrYSmaVvLycBGZVw/4ZNAHoelX48rbv+6c/NzjjGDz14qn4k1AW2nXFy4yqox2hh8xxwaxtM1KVo0ITGFwWPXOOc/pXKfEjU7poHt03kBB82eoPGKANP4Tafa6lq1205VpkYO2Tz/kHivedOsQ0ZXdgCvjTQ/GV94U1yPULeN8qNkisOGX0NfQ/hP4v6PrUEMQmkhupFx5TcfN6A96APQLm3eJztJJ9hTYJJI2Byfxri9T8d6xazObTwnrGpwIcGaJVTJ9FDEFh+FbXhvxBP4qhV00fUtObOJEvI9mz1+v4UAdUl4hIGQM1MzDGc1SuLDbBtTcWX+Km2czyJskBDDg5oAsSfMQQeKbjgnNP7dMUfjQBWnjDYOKrsSh49M1dkXNUL07UxnHPJoAh0uIyal5nBKKSBW3vlU/cArP0SPYJJs8ZCir15fW9lbvcTuqIg3Ek4AFAFa8eGxtZppn2xIDI7HvXguta7L4l1me/ZmRWG2JCOidsV0fjvx6Nfi+w2IY2ZJLkOV8zB6fSuHsXCOzZJG3A2nOM9uaAJZ14YOrsMgEqo4PfrVVogrsI+cdCFwR7j3qSSVXJVnQsDjb3GKdEuC2SM8d6AHLbmQFt0zbcc9qligKEHDD5sDgE0qmTO0MADgAj0POKmgVok+X+Lrj1oAmBZ1BKQ5xjmEGinCRYlCMCxA65xRQB9IHk0hGKU9aD0oAbTW604000ANIzSbadRQA0DnmnEcUUtACKPWggGlo5yPSgBVGOlfPvxp0+Sz+IKXSqQt5bJICO7Kdp/pX0IteW/H7Rnn8O2eu26nzdMuAZGH/ADybgn88UAcXo7KzN5gPmDG5SvGO/wD+uretaNa31qXkj3DGAR3ArmX1TdZCWI4ZypCx9QDwf0OcV02sXkNroSvNhFiXaCTwehH40AcsfhL9vuQFn2Qe49enNd34U+Emg6AUvXiN/OvIWQYCkdxU2neMNAn061aXU7ZHKK3zuBtIyMH35Nb2heL/AA9Pcizj1W2kuJFO1Q+c0AdfYTo8ShV24GMelXRNzjnNczFr2nae7m5uoo974+Y960YfEOkTDdHfwPzjhwOaANYyAn7p/OoWhTzRIox6iomulUAjawPoc05Z/MCkYx7UAWDzxio5BgZp4PGailOaAIm6cVm38xKkdAuelXmfA+vpWNqbFztX+I4+tAHMz3Xjm116Z9PNidGcK0fmg7lbv74ri/G+r67fapb297qD+WFcyww/Im4eo7ivZmcrblF6AAAfhXivjaKR/Fapu+ZUJ2+mT/8AWoAxJi2c7ANuQcZHGaWzVmDjcc4ycjBqw8TMpfcTuPO7kimQfdkKYYoNxIIBxQAQrHu8tnO/JxlQOvvSW4BYeaGlLEhnUkYP9aaoS5fzDNIqqeWHGB+Pepx+6cLI7EJlhtf1HtQBOpWYByOCc5wAQOmOtSD5TgMQDg8jvVJm3SIY0lA39VOQP61bUOQrYDHJ/i5PvigCyyK+DkD2PFFNEikfPGN3uuaKAPpLIBGQT9KGx2H6005Bp+MDNADTUfepgMimlaAGGkxSmkoAQdafikpcUAJ0o5paUjNACAcVU1bTINZ0q7025UNDcxNE2e2R1/lV3IApM+lAHyZZaZcad4guvDWoqwnhkaAMx4bHQ/liuu8YeEoT4fiM5ZrgER4hP3xgevfFb3x38ISQPbeMtOiJmtyI7rA/h/hf8On5Vz99rc/iPw1aT27ssyOH29CWAwR+VAHI6L8KtG1tbieG+vGCgqI8jejDrkHtWrpvwHunkiaz8Tz256rvhBK/jWhpc0cl2l5aO1vdS8SJvyjtjBBHrXaRapfWwE0cwVS3McwycY/M0Ac5Z/BbX5pkWbxvqPkOSZGRFU47101l8DNHtgRc6jqd+DywkuSvPqcda3dP1yW4hQysu4gHcg4PHpW7aXRKgncOxzQBiWXw10q2TalxfCPqEW6lGDjrndWzZW0mlqLd5nmjQfLLKcsfqe596upcqQFAOaSRfNGcnjmgCUPmPPtTHb5etMyUTHYVEzFyDgjHrQAyZgqNjqeM+lYcm+6v0jTDKmSTnkHitDU5zEmF+8eFH9aXTLHyI2lfJZuBnr7/AK0ASTJ5a8mvK/FOjs13f+JpXjjtIZBblyvccdfTJxXskGktdEvOTHEOnODXnfxa8aeGR4du/CtoFvJZQFfyWGyEg55PrkdvWgDzwmKQNJHIGHH3ecHA5xRtDp1VsnHoRjqf/rVg6XqWLtYRlYiCoUj7uO2e9dAjxGLYEZnGcMpPB+lAEV0q7X2zu2eAuSMk9uKpJJkbQiggbeB6f1q4940cZUqeTgFuef8AClsYzt82QAjJPAzmgCBX3OuwbcHPHetSJVEoyG2nvt5x/Sq0Vi/mGUqoGThQ+COM9K1LVPMjy24MSR1wOKAGrDlFY7QWGSCTRVz7KxVeAQBgbSDxRQB9AkDIpWHHWlYc0uOKAGdKRjmjknpS7aAIyM0mKfgc00cUAJilooxQAUuKAOaU0AJikA5pacoFAEF3ZW+o2k1ndxrLbzoY5EYcEGvmy/0Gf4d+MZNEnYSWjMJ7N3zkxnPf1B4NfTqgZxXjn7R+qeHodHsY57pE12KYPaInLsvG4H0Uj9RQBStPDdnfkXEflRM53ZRfTp06HrzW9ZaHIYzBJFxzn5sge4/xrkPA/iaDVdLigS4WOVEMZUDkjs2a9J0+YyIjqRlgByPSgCnp3htYAkiM/mEAHd/KtyOzkVQCMfSrMc8e7LnFWYriJ85BA9TQBWit9h3Fs1Uur6eCRI0tjIrkhnDYEfpkd81euJ44lXJ4747Vl3VzE6l34Tg5Jx06UAXhK23DEMx9Owpt1dRWkZLsM9h61ni9Z3CQwyyynhI0HzZ9+wFaNp4aDu2oa1KqhRuEAb5Ix6se5/SgCnpmn3Gp3LXLodme/cVpazrWkeFbcT6ncqH58uIcs30WuO8W/FmKztpLXw1GHVcr9qxlR2+Ud/rXjupanc31689xczTXMqqGkkbPJ9+30oA63xr8XdU15JLaz3adZYIKIcu/sx7DGeBXmF4QRuUbSvQevqP/AK9ahkjVWjUneTnLHPIrNuofmVwG2DjOO/0oArwStHIrI2RGQwU13OmCKRTNJAMOmCw45+lcKAsbO2SMkcgcmus8PXZMDxSnJLEpv5+b0PpQBNc7JZNqbSQT8vf649KLaI7txdCem0nBI9at3VmvKKroAAScjhsZ9aWBS6q0vzKw+7uCMTj9c+nQc0ANtkWOVU3HbjcQGyMZ/OtqFyIwiKMH5sfzqkkafKoxjuo6j0FalqY2CGQchcD2oAcY1BwYyP8AgWP0oqzG0TIGM8a57MeaKAPciOaU9KDSNQAlI3PelFBFAEZGBwaaBT2zQAOpIFADe9OUA0jYGTWPr3i7RvDVuZ9T1C3tVA48xwCfoKANgjk0Bc15NqH7R/hGzd1ha6uSO8UfB/E1h3H7VOjRAmPSb5/XOFoA91OFBJ4AFOTB6V88XH7WEKDMWgznJwMyCok/aruHjZl8OhTjgmbjPv3oA9V+LHxOsvhroD3LMk2ozgraW2eXbpuP+yK+QdL1TUPGHj61utUna6u7642yO3OM9gOw9qq+OfGWr+NNdn1bWJvMkk4RF+5EnZVHpV/4PQ/bPiFpSGMbEkMnTrwaANK6k1PwF4nnt2O14JCBkcFT0I9uelex+B/izo2qW8cF5MtpdqAPnHyv9D2rifjtqWjXOuQWu8reov72SPrGPQ+pFcH4L0Cfxlri6Np10ocgsZApBCjuaAPq5/EumPGJ0vIPLxnKyA9s1BF4v0x2KrqELbcZAfp+tcl4Z+BMFrEV1G4ub1mAyC21QPbHNddZfAnwom1pbBzjqnnvg4/GgCC+8baXaysiXP2ifjbDEN7ufRVHOelWdM0fxH4rkWS7g/sfT85KzkGeRf8Ad6J+OTXYaR4U0DwrC0ljp9nZKo3NIsYXAA6ljXmnj744lHOmeEdrsxZXv3QlRjrsH8X1/KgDudc8TeGfhxYBZ5R9oI+WBDuml9Op4+prxzxL8TNU8ZSFJn+xad0jtEP3j/eZh1/lXC3d1c38stzfXby3MzB2mdi+4++f6U15Vtoh5h+UkDAYECgDYl1RYi6LKTyc70zn3H+elZk8znBXmQNhjjG73BA6VT+0Fi025iwxhyeQOlOidVnXzGBjQ87ejelAFq6a3jYJbSSSrtA3yRhCrdxjJ496qF/NYgkgjLZHp6c0rzeYXA2KWPJYikkYhkQAYHqPvCgBFG1SjhDhg3zDkntUttqxsyGzEDuLZxknPU4/CqssjQL5oYDGc8dajtUWaNnYg5PDHnAoA9FDCcRzsVKMoIA6Akc5/pTGVWdmUZ564zg1xNrqt7YsqQXYEa8eW/T863dK8SC4kEF3EElx1BwjH/69AG8kTxsrhG3McYxz0rRtY5ZUUZbeN2VJ4A/Cq0CKZDJI7ltvAUYGfc+9WreZ2BVABzuXGRj1oAsRxkIBtBxwMiilWQ45Iz/vGigD3YilNFB5oATFHSlFBAPegBhGaparqFnpdnJdXskccEI3s0hAC470a5q1roWmXGoXcmyGBC7H2FfKXxC+KGq+OJ5IXk+z6aHJigTgsPVj3+lAHVePf2hb2+lls/DKCCAEqLtxlm91U9PrXjWq6jfazO1zqF5PdSnPzSNnB9vSomBBJ6n1qCYkgZNADGbcCSQcdR3zUHmlDvwuemCM05ztBOSQKbDA9+ypGrlfXHU0AJYwySzBk+ULzuArTNr5URygAA5wMZresNA+ywmR0Ea7cjf0P0rC1m8jUMiryvDc96AOb1OZEcKAcf0rZ8Da1JoWoPcW7fZ5pl8oXPVoFPVh71V0HTINT8QWcGosYLOWRFkcdI0JwT+teieNvhmvgXXTZSSrcwNGJIJgMebEejEdiOhoA4jVtGvkvp4tRM32kvud5wdxzyD9D2PSvpH9mT4e2GnaXN4qV0knvoxAEAz5W04fn3ODXF+NbjSPEPwwtfEKTQHVNJMdjdKG+aSPkIT36Cvcvgdpw034XaECu157f7S+Rg5clv5YoA7dIgp4ArI8UeL9G8H2RutVukjyP3cQ5eU+ir3ri/iF8bNO8PNNp2hmK/1FAQ8m7MMB6EEj7zf7IrwfW9Y1LWr2fVNUnkurh24eReApA4AP3R7CgDq/G3xU1fxndyWa4sdJPC2qkhpR6yHvj+7XDyyyC6wI1XbHuCjjbnvwPT+dELkSNtyBkxjHXpxz3qBHRJpi2NrHYDuyeAB+GKAJLhpSHVgDjjGOT0/+vRJMHTaCFYZOdow31pjtvQMRwp5xyT68Vb+yBI1baSrj92WPf8RQBGWjZiSp2fdLiQbc4+lRr+75SNnHOGbB57YNNufJBJTcTgKwYhfmz29hRLNGlqUQqjrgE5+Vvw/qKAFlmVly7Yl5wHQ/ifzo3NCDIxGzZuPAFV43FxIJJNpVeTzwPxFYuta3JfSva2gb7MjcvnBY+n0FADb3UmvJ8DBjBzuB7VNYXNzGhjjZtrfwgZGao20KqqmQFiR90Gr32x4QFiGwnOQvagBRdXRcMTuBHQgAGr1pfLcbhdIEdSDuB6j0I9azzJPMBztQDIA7irMVu/zYLKQuGBPfNAHc+GvEts6mzurmOJRzE7nr6jNdfbBSgkjdZA38SMCP0rx2KHfI6lkYqF4YZz9fbFaNkJLWQx28zwjJKvE7Ddj26YoA9ZdXYjdkHHfiivPv+Ey1uzAiM8M2ACGljO7Hvjr9aKAPrfvS0nWl6CgAFc/418Z6f4L0eXUL52AXhUUfM57AVN4p8XaV4R06S/1O6SGNRx3JPoK+bviR46fx9cC5iV4bKHiJWPJPr9aAI/G3xe1Xx3ayWvlCzsA2WjDZaT0BP9K4Bl3DODinQLIU8pSgyxJwuM025maMmNT/ABYA9fagCiZlJK8HBqB2AzgjA96kuB5TOsqMGB+Ze4PoRUMUL3D7IlDnOMHqT7UARQwSX8yqAHDHPy/xV2+meH49Jghnl67sbRg4OM9KraZZR6VayXLKHkxhVPb/ADg1FrGtmEBEfhQMnPU47elADta1/ZE0YZsDnaBnvVLwdZ6Tc60L3X7a5vYo23jT4OGlx/fb+Ef4VytzfzXM21WPmZKgcc16v4E+FHizVLFLiPSpba2lG57q+fyUI9f7x/SgBPGfiaw8U2kel2vhfStCgt33RS2ylpCMcKxGMjoawPEPjTV9b0DTtE1a2iupdNYpBe8iQxNwEJ7gYr0mPwx8PPDYlHibxzZvd5y0FlGZFUgdB1JrgtVttCudRkn02TVbi0Q/L5+Iy3GQQo5x9aAKnhjwH5ujtr3iOUW+n5YQQAkvdsP9kdQPWvSPEnxV1XVdEttB0dP7G02GFISsT5lkVQBy3YcdBXDxSKtrEiDbEE8sBicIvoOenNNHlEhWdWkYgYGcbc4zwaACOUoQynaNuC3pzT7lpWQtgKCcNuOSe44HaljhLXfloofAwQOnB/Q1XkkfcwBRflOV6kY6598d6AEtjIQzvGzIOXfd93AzxnrTYpCYM7F2OCS6j5gTyc1WkIkR5AECvhMH+HJ4I/nV8SxiLf5flbh8r5PLdO2R07UARpumT5THxgHHO7tVhLh7i2XMYYKhAAbOTnH1FU3uhCu5I1DKQxIH3j271SN08ygoRjPQjkg8/wA6AJtQ1DMwT522AEhQCM96ZCsi5uLk/IBnJ5PXoKbbWygySS9/wP05rI1LUzezm3hAWEHaQvOTnp9KAJL/AFOW7doLZikBOC2OW9h/jVdIQiKqc8fnRiK2ROhc8g9wB1/Cp4VJBZUPzc5bnIoAkgtXC5b5QoyQRwauQQQR5KhcqO/XmoFiuAsaSSkqfmKVZe3TCNvDYG5ip7+hoAmmYByjhGjUBRx0PcYp5GISGJ5OFTscd6rxQQpMGL7cZbdu7mpFSJTuzuyuF5yCaALxSJAuXJCtztHIGB+f096vi3QwwvlmcIzMFxxkHAz36daqRwqpBhJVdu3cCOf8+1WbaKRJUEMqqxZYyH4yAcnNAE0OmyTICpHAC8r7CitqGYQpgyCLJLAOucgnqMcYooA+pocsoz2rnvG3jXTvB+ly3V1IDIAdkYI3OfQDvW9JKlvE8jMFABNfJfxH8SXGv+JdTlmkd40lMcKnlVVf7tAFPx54t1Dxh/pt4+1AxMUI6RjP6nFYNxchdNiVT8xHQUkUrPaSQzLhk7N9aqxDcqscAUASwr5NvvJBZlzWdMy7i7Mfw5NXNQn3IoCkYGMA4rMZlkBGQoAOT6UANCSX04ChxuboMc812Wj6HDpVmstyrCdjwV6off8AQ/jUfhbR4YIX1C6XaFUiJXA5bAP4jmszXNfkvJzDDISinDSZ43DsKAJNZ1d2m8uOZm2t1DZHSuUuTcapqCWdlFLPcTNsjjQcljTtQvRGhCk+Zngepqjpl7dwTs0EjpLONjMn3gD2B6jPTigD0Dw9JpXw1mEy21vrPiaJzy58y1sm/lI4P4Cpde+JHiTxe5TVNWubkYBW3T91EPoiVnW3g2+05IpNaSawjmTfDb4H2iUE/e2fwr7nr2q/Y6JHbnYoRWT5mBYZOM+ncj+VAFCw0cvdGWZt0hG5E42ofx7+9bkBWJtzg7mYkjII/lx0qCDNtMMtGpYDIcdR2IH/ANfvQ3yAnKD58iNfvZGT+X8qAHn5kULD5TPja+SOn+TUESR+ZJPujO5AUZiQOo4PuTS3EhZ1jUYckBgpLbT1Jx600cB2Hz7EJ+bj0AI/E0AXY5LYeZyNwfBc5C5Pf14rJvbjfL5SIjNnI+Tjnofp9aW6mhDum9Wyu5iDyGPr/KmLEIgJGlHJKkA4z9T2oAleMCQqqrsxvIzyT04689TTZ5fMYNAhh2qCQuQCRx+Z71VK/M0skyJk8EAv9AffFRsyFAGaUqBuwOBg0AWXs5Ut/MkjXluBkfL3455qGWeKAqWU7ycAAZJ5+vaqZuRIGjjjYAZUAnPPtnpTblvsgjihVBfM2d2c7VPTg9CO3rmgB2q3rv8A6LEmJyPm5+6v59aggtxaAyyJ93GFPJyf51asdOWKOSWbqM+YXOWPeq6Ti5nM+AIMkRjqBnvigB1vbJLcNcScMx2hMfKorQCEghpAEJ4/2eOlV186XEaDaCOvQf8A1qVLQiJGmlO3Pc8Y9cUATJKBtQsGJGAVHSla4i3KjOQSdoJ6VAL7R7Vysrj3KnJqtceIdKeQtDBKwHYKTxQBpjUFB2kKerK23rinWsyu53Ix3YOGUY/SslfFEBSRfscyZxlVi+8M/pVi08XW0auj6fPhscGM0AbkawhC6ukSDkgnGc+3p9KmifZGSXO48gNySAexPQVkS+JNIuH2zblZh91j92tOwuLEyKba8DOUYMuOCO233oA2Rd+YOk42gLhQGA46A5ooSW6EasbY4cbgBHuxn3HU5zRQA/Wfix4u8QiUyXy2tu2VEMA28Hjqea5+9iKwLKeMnJbPQ0uoWcdu0SQFCCTsAGCBnoc9/eqt7cH7OV37j/ePY0AZUL+ZPJGjE72JYk5BNaMhW2g2kDAAI9fpVWwh8tZLpgUZ2wMjpzTJW84ncxCg/eHP0oArkG4m+Y7V7nPQZ4qbSrBNQv1s7YEjeCzE9TkcUyeSIRMikbevPU10ngCwYm5uk8jckTEO5AwcZ459KAHeJvEAa2XSrObMdsx6YIT+HC47cVxtzMIh5USB5jnjjp3pLu/2B0iALlyMnryTziksfCmtX9ut6tq6RSvsW4lXbGxPZSfvfh6UAUYdLuLzVU0vSwb6+m+UOCNsfrg9AMdTXovhvTtN8G7XsGgvNbjb59TIDRWxHUQqeGPUb24z0qnoHhuLQRJ5jAzSoQ5DEE89Meh9PetjZBLH/q8ZGBGy5QggZBUdx+lAEskc99c3GovcyXUsjgyTFss2eAWYnO047dKqhvLlARXjZxjG75mUZ9en86s243ogPkscFVG0BQo/iHH1+tVbQuzZXBaEZLYyeTwMdu9AFZ13TRFVOGG4lic46Lz2p8ZkeKTa4YxEgZY5POMfXOaW6iFxIONpL7uThsn1pjskQeVciR2ChQv3hjvg/wA/WgCvKVcSSZwgG3eOMknJ+vHGagMpceWSEZgQWYYxnngdyOKjZw6y5fDDOA3IXHUEngcelQ7vNQMI94QjJ/u5Hv8A1oAeV6fdyzFlDDoeh5601tzSADBB6Y74okIIX5WJHGc5Le1LMDHEiunl9wuMHHcGgCG8cqNgyJOhPZfpVW4jMcQCK3nlfmHfHbNQpObi7cbgAgGMnG45HA96t3QFnC12+HmkchUJyfqR2WgAONOgRRhrhuRGwwB/tE/ypltaAyfaJJJJJWbczsOCenPoPapLaxkumM0p+ZskyEEbv0pdcuFto1gtXVpj8gYenqR+dAEd/M80X2KFiS/Dt2C9809beKyTJKdOMnA/L6VXi8uxtsNISxAY5bOfWoisk5MtwSEBLbSP5ZoAV9QklyLUbVY43dSfoKiNjLdEedJI+TjaSQCKnWaOHCxRNwM5YfqKsRy7Npb0xigCG20m1iy3lAEnIx396vJp9vtypT5TwpByT6/SmeaJWCgbgw6e1WUhMrZjbBxlfagCFtKTcwEjDHoOWPpT49KMane5UHDH5jhfarKXMkAPmJk/cUMP1zVmxXcWSPfI3UAjg/h60AZzWcjki4tLeQkBssvT3z6VVGg6fcSt5fnWMucKUJ2H/wCt/hXVhYZJG3lomjUB0PzK2B7dqms7CO9ZllEbIoyXBI254xnFAHMf8VDpP+iJcecifdcEkEUV3sWhTEF7eeZ0Y5/d4IX2ooA4eed5H+8CgGEPT5RVK6d7iTy4wASemQABUU97s/d7t23OCVxkU6AZcynqcYFAE0reTEqHIAx361nuxfI5AByKfcSlm+YcHoPeot2MYPbkg0ARhjI3TcjZ6nBruPA48u1uiCmzY2RjnIHrXCPId4Ayq5xjGST2rtdB0i88qKC7XyYpsEwcgvjPLY/DjqaANTwtr2maZbJFoXg/SornlptX1RvtErt6op+UDnip7iS9vJZpL64mmkRSFaQgBAcH5VHAHTpipbcNHGv7sRBGOXMfBUDGQB0GOOKLoRRvi2jdmkIIZipIXnHB9sdfSgCrd78rID5gJ+6pxyRgZ9zVaNJJIAj5ZGQkAnkNnJ+vFWHZvI8yMRlzgCN/lVGHIHvxTYzEHRg7+UOWR1PBwQckHr7+9AFO2UOI4YfNZNrMPL5x2PNDRRNvgQkSMpVMN97aByST04qyIlh5WRF3bhlDgEdflzUEcRWf7TujMWTwxAUsOMdMkYFAFWaGOCYsZIm/hKJzg49P1NUb2Q7VUrE6qxLFFwAOv49elX9QmKRm3DFvMKOYgPvsM44POep+hrKJE11JkAfMCpYc/Q49+OOlAFUuDOAnnIGB3ZGACPT/ADmpo2j2gZYMUIAOcs3qfT6VILSCMl52bBXcvltlgT2z3+g7VDNFaLIB5szljlQMn8CT2oALmLypEEcrbgdu89CTzkii7nkVFRP9Yxw2TuPPWhzbyzA2xmAGeZG7/hUd7fwadCmIoXkbhFVjmT689KAIs2+kQ5kXzbluUXcMZzzn2qKxczkmdRI5U+o79vaqsayXcs004LNwd3YDso9vatkW/lwwuuI933jzg/8A16ALUMjKzN9miwBkblDYwPf6Vyx1M3F3PdNyQ5SPaoUnHv8AjXRX9zHb6fO4dzuXG5ug/CuK00JlXkf5V+YDBwKANy1uZwftM0rqiAgIG4Az39ajaf7VMFxIEA44PJ/pUUarftiZQIgCFGcbj6+4rRtZBaMRHH1AHPJz/SgCFIW2ldrHK4575q5HabEUBVYjBJA9+lOjmduiKFPOQKchkD7wFKggHNAGgsJRsqCpYZb3NEIRmYuMDGA/ZPeomZ3BBY+2STVpdhjCsTknJCnn8qAFWAc72Ozpz3xU4DRrE20qrYEZHfBqFwzbt0hO0DoMnHrinwu6H99tZMAYY4O3+hoAvtKUjKSRqru23KHBkHrjtV63urq7mhgtiZmjXEeRywB5BzycDpVKVzcxAFNzs2dy/wAAHfHrT7MywXKP5jRMp3AjgoB0xzwaAOjj1Ngi7bsIOwVwoPviiqdlZ/2lD5/mxqMlQsuCwA9aKAPLbxTM27jlsE+3pU6ttQKDwOBiobjG4OB91c4HeltGV7cndg7iTx6dv1oARgrEhfmJ9DUUUE1zNHb2cRlmdsCMck/X/GtHTdKudZu0s7GLzGc/Mf4UH94n+lei6Z4XsvDsQjh2SXjMGe4IDvn0C9hQBz2j+EYtO/f3oEtywGEAO2LsOfb1rcS5eeZYl+aNlOEL5BYHjGe+c0XSSlQ8kMu8ZUGQksee/TIPPHTpUW9kMi7HWOTaFJwE4JAyD0456/zoAVkMhkfBd42IUIx3OSPyAGDk+1NuLmdnQyGAurn5d258kbeev0/CnujzCO3RgyIrFFAI3HOGyBxwcdagPmR26uqGKMDew43AnOOeudooAhliPy4JLPGD5nOMA8/h0/KkeKNMqHKmY429ySPx70yLMV4fMn3qDhATyqhSelWZ1QwRSKHVguwAJjgnjB7n9aAI1xAiyDepQFV+bO8ew7DOfzNUpHVCGYOoz0xliM9uvHuaWRJVlBDLvCkERgncOxzVO5diSCwT5dp5xkf1oArtOPOkXDsxOGYdW+p747Cn2YVbcI4cxo2B5agHrkZz159Kosiy3B2upJ4OOBj39PpV5pFhjBRn24yQGG5h7jsB+dAEbSEYR22vnaV27dpHTPHv0HX2rOI3z4zu5BI/x/zxVvMjzFUY7eSCo/hyM9f/ANdQ3lyltK0VqRNIfmDEYCDucUAQXt5BpmFCLJO/KRDsf9qsuCN7q6a4nIL7C7en0HtUossyCWV2lZmLMSME/wCHNXYliERAADHCjHcdTQBYiRIoxhVG1hnA54B/CrEpVo+XQsQAQEwR6H61FHsbaM7gTk7TiquoTCMuCy46cdiKAMvxLdmSxaI7QASB61k2EMjQo6rvOeFzzUV3M1/OE3MyqxzxxitW3/dKrx4BAGM8UAXoIfKwSgzjHPvVyMojSDGQME85y3pVF7k/dJzzye4qSJ2lGRIuAfWgC9G6t90ABuAKd52wjIbqMdgfw/rUMChVcFxhhjnpVmGOB33s4bpkA9h2oAfvKKCy564J5z/+qp7RSqDJXe3c9SewqOZEZmCocD7qg5x7VMVbYwTLELkN0yfagC5sEvKPIhxhlYYIPp7j34qLc8crM8aFQB3zg4qDDv5Y+8SARk/pWhEY2k3o6YiOdr8ZbGMeuOtAE1uF3bWj3twXQHgjrjNWbaESsiNcRICSrNndhcfSkg06e7RbiN41TGGCnaW59T+NSOwtGbPmFz83J+Un69xQA8wyWzFDORk7sAdjRRFLdMgKjb69+aKAPO3JXzVJyRyDx+VR6MDcGKAtt86Tbu67emTRRQB7Zo2k23hqwt4LJAGuJDG8vRyecsT369Ks7GMMkgbYBu4jAB4GepzRRQBhi6867EO1kEkpiBRsFQMHP1OetUbi6FzJNvhQkbSSec57enb9aKKAGXJ8l2O6TzAx+dWxyNvNTSJHKondBvJdhjoMMfXPp+poooAgjCNMFEUfzfuyXUEnnOe3NPlQpKsLSSMuGKDIwhAGTjHORxRRQBnm5fzGgiCxGMgBwOSG7H8+tV2jSacqqBAAQc/MTjjqehoooAxZh5l2g+6rknA9jjrWrbKjwJHLGrROX+QAD5gMBiec4z0oooAxNXvHtFit4AI2lfBkHUcdvyrPt1Mb9c5OP60UUAWVcSYIQL0U9896ngwTHgAGQNz6YoooAlZjsY8ZXpxXN61cvFuHJ+poooAr6WipZ+bjLOMn86s21uJJcl2ILAYPIoooAvy28ayMCCxGTnpnApku2O4aJFA2459aKKANaKERorDBJHXAqRIE7jPtRRQAk1skRLoWDd/mq3ETZpK4O8+UGIfnPNFFAD7ObzoWLDBc4GOi/QVK7MyBGIwcDgY4oooAv2M8rW1wwfaI3KbccN6U/wAxoIs5JiA3LGOMY7Z96KKAL8FqJ4Uk8yRGYZbbt+Y+vIooooA//9k=",
    me: "data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAQDAwQDAwQEBAQFBQQFBwsHBwYGBw4KCggLEA4RERAOEA8SFBoWEhMYEw8QFh8XGBsbHR0dERYgIh8cIhocHRz/2wBDAQUFBQcGBw0HBw0cEhASHBwcHBwcHBwcHBwcHBwcHBwcHBwcHBwcHBwcHBwcHBwcHBwcHBwcHBwcHBwcHBwcHBz/wAARCAH0AZADASIAAhEBAxEB/8QAHwAAAQUBAQEBAQEAAAAAAAAAAAECAwQFBgcICQoL/8QAtRAAAgEDAwIEAwUFBAQAAAF9AQIDAAQRBRIhMUEGE1FhByJxFDKBkaEII0KxwRVS0fAkM2JyggkKFhcYGRolJicoKSo0NTY3ODk6Q0RFRkdISUpTVFVWV1hZWmNkZWZnaGlqc3R1dnd4eXqDhIWGh4iJipKTlJWWl5iZmqKjpKWmp6ipqrKztLW2t7i5usLDxMXGx8jJytLT1NXW19jZ2uHi4+Tl5ufo6erx8vP09fb3+Pn6/8QAHwEAAwEBAQEBAQEBAQAAAAAAAAECAwQFBgcICQoL/8QAtREAAgECBAQDBAcFBAQAAQJ3AAECAxEEBSExBhJBUQdhcRMiMoEIFEKRobHBCSMzUvAVYnLRChYkNOEl8RcYGRomJygpKjU2Nzg5OkNERUZHSElKU1RVVldYWVpjZGVmZ2hpanN0dXZ3eHl6goOEhYaHiImKkpOUlZaXmJmaoqOkpaanqKmqsrO0tba3uLm6wsPExcbHyMnK0tPU1dbX2Nna4uPk5ebn6Onq8vP09fb3+Pn6/9oADAMBAAIRAxEAPwD7mooozigTDtSDpQaBQMOtJS5NGOaAEp1NxiigBx5ptO+opvrQAoGaWkoB9aAAnNJTqTFACiikBozQAlFL2pBQA4Uho6dKO1ACUuaDSUAOpCKOlFACUoGaKM0CYY4pKU0dqBCU4UmKTpQULikpQaMj0oAM80uabS0ABpKXijigSADmlpBQTQAhopc5oFAxaQ0lOFADaXpxQc0lADqQijNBoASnU3mlxxQAppM0CkzQAuaXik60EYoEHWjHNApaAEzRRmkoGLR7UdaMUAANHWkooAdSUtJigBM0vWkoFAC4o6GlppoAXPFHakp2aAE6UZpetNoAXrS9KQUuM0ANopTSUAKKPejNLigBtGaUikoAXsKKUUmKAEooIpRQAtIaWg0ANpcUlKDzQAfhSU6kNACUuKKAaBXDFGaWm0BcXrS0gpaBjTRSmkoAXrR0pBTqAEB5o4pKKAHCkNLRigQlLSHtS5oGJ9aSlNJQAopaQdaU0ANNFKelJQA4UUgpetADaKU0lADhQelIOlKaBWG0opKBQMdSGlpDQAlKKSlFACmm06kIoASnCm04dKACm06m4oAUUtNpwoFYQikpTSUDFFBpBTutADaB1pcUlADqQ0A0tADaKUikoEOptO60mKAEpwpKOlAxTTadmkPrQAlOptKKAD60lOpKAFooHSlNAhMZpDxS0hoBBmgnmkpcUDD+dGaMUEUAL1pOKTNLjNABigUYNB4oAXNJjmjNAzQAYoJoxRmgAzSUvWjGKAFFJmkooAXrR0NHpS0AJS0maAaBABRnFLSUAGeKKSigAxSiijNAXFpuKUmgdaBiUvSgikoELmikpaBgKWk70Z5oEHWjFAo60DDOBRmgjikoAKKXrS4oATiiikzQAvQ0Clo6UAFIelJS5oABRmjFBoCwClpop1ACGkFB4ooAdSGgUtADaKU0lADqT60tFADaUGkooAdSEYoFBFACUopKUUABFJTqQ0AJS4NJSigGGKSnGm0XELnikopcc0XAMUlL2pKAClpBRQIKUUEYpKACiilxQMSlHSkoHWgYuKMUtIelArCUopKUUABpKdSGgYgp1Npw5oAQ0lOptACilNNHWnUAJigUYpKAHUhpaKBCCjNBozigBc02lzRjigYlOpMcUZxQAGkpeoooABxS0goyaAAjFJS9aCKAAGlptOHSgBtFKaMUALSEUtBpANpQM0lFACnrSHilwfQ0bT6H8qQCU6m4PoaXafQ4+lAB2ooIoxTASl6Cgig9KLisBOaSgClxQgEFGMUuMUUxCUCl4oxQMM0GijqKAuJRS9KCO9AC0hoGaWgY2lFAGaPpQAtIaMmgmgBKUGjvRQAtIRRR1NAABS0CkxQIKCDRiloGNpaMUA0AHakp1IaADNHWkoFAC/hQDS0hGKAAUA0lLxQAtNp1NNAC44zS02jNIANFFUda1rTvDtg99qt9BZ2qDJeZsZ9h6n6UgL6ruPt3rz/xR8ZfCfhme5tDe/bb6AZaC1IJB9Cema8Q+LP7SCatY3mkeG1lhsiRG94TtkfPZR2H618zX3i+dWukhLIEY7D39OT3NA7H1F4i/aYvVkddKIgfOPKmG/BJx97HbvisvTv2i9fuN8bXkbXAO2GQxhUkI6s49Ppivk1NXY3HmFiTnnJqWPVDHG0ccjAjjd6A9aZNkfakn7Rge3spLgOXZZiEjO0OQOCxHO0DPuTiuK/4Xd4iS/uJ7bWZT5dwd8O3dGYWG5Mg+h4OOtfNDeIJJI1QSsMcA/3R3/lSaVr88V1KHkJV4tnJ646fpQGh9yeEP2ldL1CxD6xbzLIAvz267kIJxu55HuK7OD46eDrpJZIrxxHCMuZRtP0A7mvzysfEIsdQkgSRxFIcjnjNaU+tSqWmhdw2M5Hp3BHepe5SVz9ONL1nT9ctEutNu4rqBxuDRtnirmK+CPhf8Y9Y8LRsNPlWRVwTazYKsO4B7Z9a+tfA/wAaPDXjeGNBciw1DA3210QhB9AehouKzPQhQeelKy4AIIKnoRSdO9MAo7Umc0UxCijoKSlpgw6ikpelJQIM0uM0lLmgYc0lOptAxRRn0pKUUCA9aM0GkoGKPSjpQKXFACCgUUDrQAtFFLxQIb9aWhqaDQAppKdmm0DAU6m04UANNFKaSgBQaWkFLQA2l4oNJQA6kIoFKaAG0UVwvxT+I9p8N/D0t5KgkvJFPkRk9x3I7/1NJuwWvoavjjx7o/w70qS/1iUElCYrdGHmSn2H9a+Cvij8WdT+KGvtqF0j2em26gQ2iPlYx/Vj1JrmvHHjnVfFmrPqepXMsk83CKzkqg9h046Vy2py+RbpEnGV3kVK1BWRHNf4TahJBbd16D/Gsy9uvvhf4mx9KickKC2cZ6+uP/r1TnctITnkcVVhtjxJtVhnOaDO27HbPNQKDz9aUA7vrzTJLSzklsjABpDMd644IAFVuQT+dSR/Ox7Z5BoBliZmlZnzgg7sntWzaXbOgJJMigZ5+9jj86w1Dx/e+9g1YtnZQZU4Axke1A07GvbXj2tzuiJBHzADv6iuuXWBbypfBXaFwDIobkf7QPtXCCTBZc57qfStbTp/Nt2gaTCg8Z/hJ9fbP86hotM+pPhD8fb3Q7q003VJWv8AQpW2CSViXtvx9PY19eQyJc28dxEyvDKAyMpyCDX5X6BO1lfeScqrHaQTwPT/APXX2J+zx8UN1nH4b1ORv3bmOIu2djdlz/dPapTsDjdXR9HUtBGDikrQzCilxxSUxi9aCKBQTQSJSikooGOpDS0hoGJTqbSg0AKabTqQ0AANLTaUGgANJTqTFAC0UUmcUCDrRxQKDQMOKP5UUdqAEp3SkxzQaAFNJigGigAIxR0pfrTaAFNJS9aMUAHSgnigikoAVTg59Oa+CP2j/Gt14k8bTQGRvIt/3ccXZQOAMfmfxr7m1/Uf7H0PUdQLKgt4HcM3QEDj9a/MjxVqTX+tT30zkvKS2Sck81DV2PY5uZt8pLfchKrVS+b7VI5XlWwoPtRdv5iqkZPmTTKGC+5zU00YjW4O0gqwVQBzgCqJKr2peJh1OQq/nWbLB85I6GuthKm0jUKu8Ac++MH+dZc9p++lAHYbcfjTAxVgyp9MZzSJCSc84roIdMd4gQmdy4/H/Iqmlo8aAFTlqVxtWKUcXHI4LYNRpF8+M9Cce9bkFpuDq3VgSBjuO9UXtyD/ANc2/Si4hIoRO5Bznyy3PqKfYR7nYfwehqYL5a79pDDj86nsYx8+zAZjt56HPSmIoNEybhgnaM/hVqzkKS5YkhgUfH8Q7H8KkhVpHkLKRu5AP8v8+lTyac0Usi4IbCkduelTfoX0LEzlJY7lTz0cdiR1/wAa9C8Nas0FzZ6lFIyScRyYPOR0NebRf6RDPE4AdT1rovDE+YjA33w3Hrn/AOsaUkOMj9IvAfiRPFfhWx1DeGuAojnA7SLwfz6/jXR184fsw+Ipp7jUtLYp5MsfnFB/DIuAcfUHNfR9NMUlZi9aMUZpaaEIaMUd6D1piYmKKWjFAgzS0hoBxQUJRS5oxQAUdvag0lAC4opR0oxQAmaBR0ooACKSl6dqMUCFFIetJTqBjelFKeBSUAOHSikFKeKAG0UGigB1NxinUUANpRSUUAOpppRSHrQB5V+0LqTWHw7ukE/li4cRhF+9M3932UdT+FfnpqU6T3cnOdn7tc/qa+5P2oLnU08LxGytkdIz87spJXnoD05wPcgV+fVxKyzPkks3FKwmzR0+08/VkOPkV9/5DAreutNMks4A4cfIf9rrUngDR5NTvxnLZIBr1W18BqqGW6ISGNw2SccDrWU6qi7G1Ok5K54/aWDLdRRIrMEzn8q0I9NMmv28RX93J8uB0ORXcXMmj6Vd3dxCjSyt90Zwq/WuYkvbmS7jurOOMkFSABnaR70ufmK9mkdangPOlWrRxneVBIz/ALfFcPqnhyTT7qBpImETuyr9QeP5V6Bp3jO/C/ZroFWxx8uOPb8a2Vgj8Q6c1nOAHBOCByDnINZqbW5q4qRxeq+BJ7S3ivIYN4RS+B6HsfauP1TQHitFuEj+WTMgOOq9/wAjX0tokCzaPa2dypbbCYXJ4zg4zXG6/wCHIrZXjjH7sNv2npkjnHsfSmqtiHRvseBGBJYCoO18j8elaFv4fuV06IopCyOQCfUDjH8q0NT0NbYs0KktuOfT2o02w1OeBCDKsUXzYz1b2rRzTV0ZqnZ2ZN4c8O3l9eFbqBkATeMrjJzzV3xfoxtNUmgWNyCgZcfh0/Kr2neJdS0yVBMpYLwN69B9a7Cw1qw1e6ie9iQFQRvI6EisHOSlzHRGnFx5Txm7gFq8km0hJQBn0Pf+dV9M1dbeZjuG7zF5/DB/kK9v1DwNZ31vJGFBR23oR9K8I8U+HpND1eS3IPqPpW9Kqp6HPVouGqPevhF4zXwx4ustQjIETMFlX++p4P6H9K+8VdJI45EIZJFDAjuCOK/KPw7qk8FxCC5+UjGOoI6V+pvh+b7R4d0aXGDJZxMRjGPlFa2szK9zQpeppKKEA6kPWloNMTG0opKBQApFJTqbQFwFOptKKBgaSnU2gBw6UGm06gBtFKelJQAuKOtHSlxigBMUCgijmgANJTqSgBKdTaUYoADSUpowKAAHFLSYpcigBtFKaKAAUGgUGgDmPiB4el8T+FL3TYZjD5oJd0GX2YOVX0JHH41+Xt1pDf2pJCyBWjcqRjG3BxX60gBvlYZU8Ee1fBPx7+H48H/FKdYY8WWpILyPC7VGWOVX2BpMVhfhl4eh07RZtQePLE/Lgc4q7qd3qGsTG3jiaO1B+6eC/wBfQV1/huxEOg2iKm0bAcCq9+9vYM8hHlr1YmuByXM2z0Ir3UjI03wTBeLtvlBU9E/h/Oty38C6HZowigVAeqg8V5/rXxV02ylaMamkESnBMa75G+g6D8a5e++OOkAOkNpqV04H+slmKk/gOlUlN7CbjHdnoepaNZRSt5SAMOlLotuqzkDg5ryG0+KtzcXInTTb6W0DYkUjewHqp6/zr3rQrOOSG2u0DlJ4w6712kAjuD0rGfNHc3i4SWh0NvabYRtHzHmuY1/ksG69K7+xVNyhsAYxjFcH4ihYXUgByMnFROQ4LU4iHSor67ZGT5O9dvpGk6RYwqJ/LVB0LkAVzEi3OkaHe31vZyXt6Dtht4xku56Z9h1NeaXmq/EjSJY5W0wXNzKNxcRmUx/7OOi/hWlJOS3IqtRPcr5NDmG1Ftn9gRya5e+0O2aUtbIEft6V5b/wknxAvD/xMPDzSqT0NsVNbejeItWgmVLjT7+GPPKvGXVPoeopyjJa3FCUZI9U8P2N7CVjfBjJ+6eR+B7V5p8bdH+y6vY3SoAs6Mp+oxXr3hLUI71URyTu6ZXFZvxu8Oi58M2V55YPkz849CprSjJOVzOqmo2PAPBXhy613V7KztIvMnlmVBH3JJr9RdKsv7N0jTrPGDb28cWM56LivkD9kXwQNQ16/wDEF3Zxy21kmyNn/glPQj14Br7KArtZwAaSnYxSd6EMWik6fSlpgNope9JQSOpDQKWgobSiggUlADqQ0Cg9aAEpQc0UGgBTzTTxS5paAExQTiik60AL1paOlFABSUmKKAFxSYpwooAQGjNJRQA7GKTpS0mKAAnNGKSlFAC02nU3FACjrXzp+0bPH4jaygitF36XIc3J+82eGX6d6+i1+8K+cfiaH074nT2QHmWGqRbpIm5AO3ll9DxWFeo4JNHRhqSqya8jP0qLbpNkSB80Ktx9KzdQ8GJ4kLfbJJvshH+qjYqG+uOa7CDTxb2llEP+WcKL9QBWjAA3yqOMYriktbo6ovSx5LP8JvC1iv7vRbZiP7y7j+Zqn/wiljHIRBo1kO2fJBP5mva205JF+YCqE1lFDyqqDReRVo9Uef6X4VSAKTBFCgH8CgZroBCq7UUHArRmmROGIH41CHjf7prOV2Xa2xJbwhRuJ6dK5PWrM+bJIDksea7VVxH71iavCBGWxUyWg4tIyNEERjeJ15P6Vdn8PzORLC4J/I1iQXsUE6EkjJruNPvI5VVkOQR604N2HI5GXQ9RllxI7Ee5zWnaeFAPnlOT7Cu4t4VlUsAPxqG6UJkUSVib9DmIfDUUEqywADnkAVf+I1gJfhleu6bnSSMe4ySP61qaaweYxnv3rU8UiNfAOsmRdwiEb7fUhxit6OicjCp7zSKP7NskelaJeaB8rTKBcsV6jJxg17gK8N/Z70qW1vvEd1Jk5KoCfc5r3I114eTlC7MMZTjTquMfIM8d6BSZpR1rc5haQ0vWm0AFKMUlKT7UCDFJmnGm0DFFGKQU6gBDxSDrSmkoAdSZNApaAG0ooNANABxQaPrQeaAAUtNpRQAGkp1NoAUUtNpwoAQ0lKaSgBRS0gpaAG0ClNJ0oAdQelAoPSgBo4NeW/FLw0tzrGma0M5SJ4WwPUGvUqy/EWn/ANp6Pcwhd0irvQe4rKrDmjY0o1HCd0eRucWNmSDuMKZ/KltbhVznpUOsTCO3gwcfuVPP0rnE1IgfeIrinodkNTrrvVI4Y/61xeueJ47dXIJLD3rI1bXpFt5DJhCCeA2eOxri9Liu/EuomR9wskbAHeQ/4Vm23ojdJLVnX6O11rl0ru5WNjhRnrXa/Y7eyiDSMPl965TVdMu7XTI5NLwtzb8hSOGHevE/EM/xPv7+RoXnjtlPypbr29881cYXIcr6n0s2u2cYIUBhjHNc1qGrwN+6DYXoOa8Fi8c+KtHAt9Y06ZuMCRUKtn3FYmoeLvFGr3B/syzniUfx7S7f4Cm4XGmj6Nm062ubM4YBiOD6Vzdlqd3pUrSKzyWyuVfHOCK8Z0zX/HcMvlSJczbvlHmRHj8q9z8N2LWeg28F7hrl13S7u7Hk1HJylcx3mieIobuAMjlgR61YutSVg3JyeK8uSObQr4NbsxtJDkpn7prefVlkj3ZwT6mk9gR00GpLHdIeeD2rstaQ6p4G1FIxzII8j6OteQW94XuFAavX9FLz+Er1QryMFUhEGSx3DpWlLVNGdXRpnX/DDThZaHcyEYeaXn8BiuzNY3hS2ns9Dt47mPy5ny7RnquTwD74rarupR5YJHBVlzTbY2gdaU0laGY6kNANKaAG0oxRSUCHUhpaMUDG04U2lFACmm06kxQAgOKdTaUGgANJTqTAoAOtLSUcigAoFA+tLQAmaMcUdKO1ABigcClpM0AGRRikpeTQAmMU6kxRmgA60lLmgCgAFKDSdqAaAA9aTkUvekPWgDx34mxrFrEqooVTGpwBgdK8qu5fJBANexfFa1I1GGYZxJBjPuOK8eurbzTg5rzq2kjvw+xzt7E90rZztra8KbLaDLELt4HtSy2gjhZR2FcFrfiyfw+k5trSS7lQbvLjXJrOO5tPVHskV1vOCy1HcavZ2zASXaLI2cKDnp1r5fsPif4l8Y6rLZW0P2YKAzg8FBkA8fjXrtj8EfFWoXtyk+tuIVhE0TRgfvM/1rZrl0M4qPVnfyX+g6tGkU89u4XqJlqlqOu+H9LtfItTEueohjAFUbL4A6gmiQ3L+I5lv3j3GN0GD7e1UIvgTLf6L5t3r9wNQcMUVQFQDt+NSX+6WqkRDXrGY4jukGezHBpj6ijFfnX2Oa52/wDgeLSTSSviKR/OidptzdWAz8teFav4g1rw9fCOK9L7i2wNzkA4FJU+bRCdSO6Po241RDKsZZSDTJJPbivNtDTxDLZ2t1rFssJlYFNv3se47V6a1oy2yE5zionHldioO5Npr5uI/rX0P8KiTH7bTXzxp0ZFzGK+kPhRbsNNknKnGAoP61rh9zLEv3T0TqaOaKO1egeeJS4pKXrQAUtJijNAB1NFGaKBBmlzimkUUDFxSUoo6dKADNANHakoAXFAFHNHSgBc0GkBFFAB1oJzQTmkoAUUtNFOoAaaKcabQA4dKKQGloAbS0EUlADqQ0ClIzQA2lFJRQA6m0ooNACUvGO9JSjrQwOX8e6MdY0OR4xme1BkXHUjuP8APpXgFxFtILcV9UHkEYyDxzXiHxK8JtpF39qt4/8AQp8kf7J9K5a8Lq5vh6lnZnnlzGpiZs5rE0Kxj/tW4uCoztwARWxBMDL5bjg1f/s6Nf30Xyv3HrXEm4s7m00ctd+E7GDWJtVtLeK31KeJommCjDA9cjoT0rc0uTxVZJJcS6lKwa1S0jdMALtz8+PU5q7NCzxH5Nw7gVj3U91Epjidgo6Ka6LqQQ5XpJHQWd948vLO3tLKaykeNQpnmiLOfQkZAz71RlsvHGk2aLea1ancDkm2G4c8jOa52LU9agYmLzAR/dPNQ3U+u3w3NG5A/vtVWRdoJ7KxWubRYrGayadv3j7xIHO5PUD0BrlbXwppUN6LqG0SW4jGFmm+YoPbPSui+w3hP79GJ9AKvQ6fKy7Qm1fSs3JRLlKFrRRVW3bUZYIfvBDuNa1zmOPa4xjpV7SLRLRZCRhm+8x7+1Z+ot9outkZyKwu5My2LegWb3V3EqqSzHoK+p/Cmkf2JoNrbMuJMb3+pry/4ReDfNkj1S6i/dQn5AejNXtJ5Nd9CFlc4cRPmdhRQRSgYoroRzjacOlNPFFMB1IRilpCKBCUoPFJSigYEZpKdSGgAFLTacOKAENJTqbQAoNLTacOlACEUlOPNNoAdRSijpQJjT2paKKAENJTqKBjaXrRgUZoACMUlO6000AKDilptLmgANJS5ooABQRRRigBMUdqXikNABVa/wBPttUs5bS7iEkEowQe3uPerNFJoR82+OfBV34VvCyqWsnOY5ex9j6GsnTdQWZRDI2DX0/qOnW2r2clneQrLbyDBVv5j3r5p8Y+GU0HWrqKymLJG5ChuuK46tHqjspVb6M0Y0QDaTnjqKclhA5O5cn1rm7PWmQbZM7l4NakeuJjhgKw1ibo3LXSrc8eWpPrUlxpsSnCoAB61zMnif7LyG/Gqb+LTIS29gfXNVz6DcLm1eWcW8ggCsq4MEC7VUZ9RWbd+J1PRsk1iz6tLcvhAeetZuLlsWrRWpo3t8I12Rt859K6z4b+BbjxRfCSSIraRnMsp6D2HvXNeHdKtZbhZtTlOM8Qr95v8K+k/AM8B06SC1jWOKPHyp0Ga6aVK25zVqrtodLZ2Nvp1pDaWsXlwxDCqKlpxOabXWtDiFFLTaUGqADSU6kOKAFBzRTelLmgBKKWigBQc0hoGfSloAbTgc0nJpKAHU2l70E0AJSjrSUtAC0mKKDQAoFLmkBooEFFFFACE0e1BpBQMXHFHSloIoAbmlpKKAHGm06kIxQAlKKSlx6UAJS5oxSUAFL2pKXNABikpSeKZJIkS7nOBSFcZdXAtbaSUnGBx9a+cPi5cPZX6Xsg/wBGum2Fx/C/bP1H8q9z1TUk1KCW3tQ26Mgtnv1rzvxh4ei8SaBeaXdLtEy/K/dG7Ee4ODV+y5otDjU5ZJnzzNrksDE/fUdA3UfjUDeKo+d6uv61zEl1PaareaLf5XUbF9kno47MPYjmmzq2Dn9K893i7M9FJNXRtT+JraUf8fBGfU1W/wCEjs1GDc/+PVyN9ACSQayJE2nNCsGp3b+K7OP7qySn0oPjCZ8CNRAP9nk/nXBqcDvUom8sbmOAKTfYaSe56Pp3isWTCSQuzE4AHViegr65+DU7w6KttdH/AE2f97Jz3POPw6fhXx38MfDsmuaiNYuf+PK0f9yp/jf1+g/nX1T4JivYb2K5x5cCnAzxmuilB7nNXktke0UnSmxyCSNXB4alrZHMKRRRmkpiF4oANJS5oAD6YpBRRQA6jFJRk0ABpKdTaBijmjFIKdQAmaOKDSUAL60DrQDS0AJ9aTNKTScUAOFKaBQaCRKKKBQAEU3FOooGIKWkpaBiGkpTSUAKKWkFGaAEooJxUZlI6L+tAXJeaSoGuHH8C4/3qga9k5/dpx/tGmkyOYvVHJMkYyTWZJqE2OPLC+mKpfaXmY5XP0NWqd9xORqSX5Y4QYqndXG2Mszbm9M9KgaQqQin5m6+1V7kL5TBsCNOSatRSJuwtbdUeWYdZQMj6Us8SyDDKCPenfcZFHACgYqTbuFaIlnzx+0J8JX1XTJPF2gRFNY0xd00SDJnh6nA9V6j2yK+eNJ11NQgUOQJscj1r9C2QbWRhlWGDXxF8avhhP4H8WzXunwv/Y2ou00O1eIW/iT2GTkexrkxVFNc6OzC1deRnL3YDDgc1lTQmp7a7aUBZRhsdTVl4NwziuDY77GQY/ereheF9Q8ZavDpmnxO2TuldRnYnc/0FS/YZrmaG2toJJbidxHHGgyWYnAAH1r64+Gfw/t/h14cFlhZdavCJbyYDOG/uA+i9Pfk10UKPO7vY569X2astw8E+CbXw5YW8MsSlogFSIdFHv6mu8i+XBxjHam21oEyz5LU25lCtgdK9DlUVZHBzNu7Op0q+82JoGPTkVq2l2J12nO8eveuO025+z/vGyAoycelatnqMa3G3LDnjKmsnC6KOmFFUp7rEayxkFT6U+3vUmHPBrOzQXLVFICCOKWkMKKKKBBSijFJTGOpDS0GgBtKKSlFAxabTqQ0AJTqbSigBcU2loxQA7FGKOlGaCRKKXFGKBiUUYxSe1AAaBRijpQMDSUUUAFQy3UcJwWBPoKztU1Tyj5MRG48EiskS9yTmrjTb1ZDkb7XwOcVA93WUJj3NBlyKrlsTcuvdEgc0zzt2QO9UDJmpoAeTTURXHStwaRCIocnqRQV3H2qGQ+dKsYHA61ohMmhBK7z95qr3I86eKDHycM359KvqAB7CqsS7pJX7k4FMQ6b/WKamU4qCXqPUU6eZLaLzZWCoO5700DJWGfrXOeNfD8HiTQprOfbu+8hIztYdDWV4m+IlvoKlcBZifliPMj/AEXt9TXL22k+I/GjfatT1C5061kIeGCPhiO2R/jWjp8y12CL5XdHj+o/DSyW4kinSS3uEJBC9M+o9qop8PkQ7VupWHQDbzX0XqOtW+j2wg1WO3u7mM7NxUfOB0JyOD7CuVl1ZLi7jfRdCU3h+6YUJx75PA+uK8yWBlzaS0PQWMVtUW/hn8JbPwj/AMTi+Yz6vKuIEcf8ewI5P+8fXtXo0NsVkLscueprytPFHi3wrfKmrW7yafIQQ4HmBB3w1en6ZqseoWi3MeyWBhkSxHI/EHkH2r0I0fZxsjgnNzd2T3UvlKQOtZaIZZMnOK1JLY3eJEYMp9DTlsmix8tZyY4jGTy4NoGdxA/DNOV9rI469abdOym3QjG5iT+A/wDr0ijPHuRSQ2bhzLD5kRCv/EOzfUVFFPLGTiNM/wC9TbGXZGAe4pWOSfepW9hvuXItVmRgDAhX/Zb/ABq2NVhZyrMY3HVWWsbds71LM5LK47rSlFAmbkd/A4/1q/yqwkiv911P0NcyJhnBqdHjHO0c9xUOC6DTOhNFZsFy3Gx9w/uuc/rV+KUSLnGD3HcVDTRRIKPoaSimCFNAoooGLmkzQaSgBaBRmg0ALmkpBSjmgB2aBS4pDQIWk70ZpaAENNPWnmmGgELSEUA0GgBDWTfajtLrGeF4z61c1C6FraswYB2+Va5BbxXDqsgLDkirpxvqTKQ0zGS6Y56Cn+YN3WqML5dj607zMMDmuixi2Xt2MGpC3HWqzHKginyNtTr2pFIdETIW9BV+MFY/rVK0X93nHWr/AGHoKAuRSy+UhPc0Wke1S7feNQOfPnC/wr1q0WCrgdqqwiRfuMajjUru471KP9SK5TXvFs2jyyW0UK+cq53Mcila4F7xF4j07wxaPdajcLGP4F7sfQV5YvjrV/Gl+sGjxyF5M7ZSMJbr6j3/ANo/hTb3RtT8eSma4lB2t80jj5UXsAK7jwX4Wj8MWbWUT+Zz5rORjk9v0rWNorUHoZHhn4dRWF0LzUXF7f53KScqp9eeprv4F8sKzdeoJ7UsC7V3DqDjNBIWRVPRhgGhyb3Iepxup+FYbi5lvo4BLcFiQOSOfqev0qfw5pwW7uJprbykAwFwQoPHArRmvpI5WiWJ9wJAYIW/kKsQ2lzKgLo65OQZDj9BmosyiSVI2RldVZCMEEZBFed65pGp+Frr+0PDsrLat801q3zKPfb3H6ivR5bYRo2ZCW4yFGKjhiQc7efXuatTsJI5HQ/HsF4sck4SyuycMkhxFJ+P8J/ya72w1SHUkPlSL5o58skZ/wACPcVxHjDwfZ6haSTWyCG8xkY4Vz6Ef1ryHTNQ17QNbjjhlltnVuY3GRj6VlOzNYrsfSGoxkSQMV2n5uPyqCIYP/AhXP8AhfxRfeJS8d2IlFuoOVHLZ4z7dK6IIQyjHfNQgZZjbav0NSCTmqzttBqQMMKaBE0pwoPvTnkzCOfumop+IwaCcDHYim1cEAbApj3BUdaap4qpeybFAzUtAmXrW/KuOe9bcF8shXDYbPH1rkrU7uattOYfLfOMMKUo6FKWp3EE6TpuXqOq+lPxiuXXUmtIxcRgMEba4z/D2rpILhLqCOaM5RxkVjaxaJRS02nYoGIaSnGm0CFHWlptOoGIaBRjNBGKAH0nWlooATFLSUDmgQtNNKaQ0AJmlByabVe+ufsdnLN3Awv17UWuD2OY8Rag0t40aH5Iht49e9YccaxSl0GCwwfep5Tu3EnJIPNQo26FG78V1QVlY55MSI8/jSyHaGNRYK5pznINWJ7lx2zAT+NSSnKKPXiqiuTZ/hVsDcI/pSKRegXARfbJqaV9i1FAM5NLKPMKr270WENtYyis5+81THkUDgYHakzmmBODmOuV1nwtDqWp/apJnRHUB0Udce9dPGc5FR3CkgHsDSAyYtNttMsPItY/LTdnrkk+5q7CgjYkfxKM1FdH5VHvU4+8P92hAwh5VhSsomTB6jke1Rwn94R2p44b2polgkZQfMST9aVmxjnimTzbOB1qqzs3emw2Qs7gowHrSQLkVG4xGOerVYhGBUFoz9Y+6i561QvPDVnrduqzpiVRhJV+8v8An0q5qJ8y5Ra0bdNsYFId7HL+GfDl7oOpS7yj2zpgSA9fTiuytl3NyMgVGBVq3GEJ9aaE2VbxAo44JNRlWjUZ6VNdfOwHvQQDwRRyiuR3MitEuKdIfkU1FdcBQBinP/qh7UikwRqzNSf51ANX0PFY9/Jm4RaQF6zGUpdRbZbn2IpLQYWoNSkBhYeuKfQXUfYXpDBXP7tsbgRwf8iur8M3EflGCNiYWy8W7qB3H4GvP/M8mKSTPRSB9a2vCl+Y/KQnJTEgB7jow/rWUomqZ6LSig+1JWRY6kIpaKAG04dKTFHSgBaKKKAHUgpaSgBfSikFLmgQhNN60ppooAd2rmfFF5zFbKeFG9vqeldI8ixozt91QWP4V55qF011NJKx5ds1dNXdyZsrByXNRQPiEr/dYj8jQDhs561DG/72dPfd+YroiYyLbj5TTD0FOibfGnqaJkIUetWQELbrZh6ZFaMHMUZ9hWRbttaVO+c1p6e++3j9uKks04/lWgHnNNJwKByKLCJN3NLUdPU8UxjkOD9afIAVNRZp+7cvvSBGZcklwO9We4/3aiu0IcMOlSZyoPtSW4MZAf3pqVuDVe2I3vzVhjxmrQrlabl8nnFMHOaMmRs471IqAf40EsgmP+rHpzViPoarTEeauOwqdWwhqDRbGVN894PatdDhQKyIhm4JrVU80IGyarS/JEKrRDcasStgYpksrty+aD1oBzzSGmK5BPyRT+TGajlPNKh4NKwyMttUk9hWC0nm3h9BWvdybI2+lYVnlpGY+tQ+xaNuJ9qVmX029woOMt1NWnl2IawL64LyKqtyTTCw+/nzA4H3QMDFaGizm2lt5eu0jI9R3FYd6xWAj3Fadm/7pcdqVrtlI9lRg8cbLypUEGnVheFb77XYCFid8PH1Fb3Wua1majaX3oNJQA6k9qUGigBOlOzTevFKBQJjjSfWlNJQMWkoHSkoEBFNpxpKAMbxHdeRZpED80xOfoK4qVs5FbGs3gvbxmHMaDatYEpIbit4KyMZO7EYkCqrMRchuzpj8QasM2V5qlK2JBn+Fs/nWkSDRtG4cehzU5ctxis+3k2yuOuRVuNgzYqyNStu8u/K9mWtPSW2h1PYmszUIihScfwnBq7prfO57Gky0bW4EinqQKrK351OKBEmc0oOKYppcigY7NCtikzSZoAe6h1IPQ1XYFFIPYVKHIptwRt/CgCrbH5zU7cKfpUEI2t9anf7h+lNCvqMUKAD7U2RuBSE9qjkIAphaxFJ/rR9BUrHEZz6VC4/fcegqWQ/uz7ioLRSsxl3PvWkoqnZpwfXNacUe0ZpJCZJGAq89aZI240rtUY5qkiRelNJPNKaidscCmBG55pFcA0xmqEvzSK6FbVZMRNjvWbYZEdT6o+4YFVYGCRn6Vn1KRJeXAVTxWIj+Zcr+dTahPmqenjzJ2OenFMbdkTak2Ag9SKv6e2Y+aydUkxPGPTmtLTj+4B9aS3DZI7Dwpf/AGXUlVj8kg2GvRBxXj0UpicOOo5r1bS7sX2n28w6suG+tY1F1NEW8U006kqCgFLTaUUALRRRQId0ooooATikpc9aaaBC1ieINR+zQiCM/vJBzz0FatzcpaQPM5GE/U+lcHfXD3U7SOcsxyfarhG7FN2VitIccdapycmp5Txis9nYNW5iSnoRVG4+Vxn6GrW8kVUufnU88iqQMjtZwbxUPUqa2IAd1c6j7Ly3bHU4rpokwAaolkF/KPJZMZ3Cl0yTMYPtVW6YNKadpzbVK+hxQwRvRvmrKvis+JqtK3FICzkE04HioQ3508OaAJM0Hmm7hRmgBcVFI+c5qXNV5O9NASJjHSnPxG30qBTzSXU222f1piIo2LscDOKcyk1xNxrV+7Xf2aZYha/eU9xkD8a6rSdQN/YxTuAHI5x0zQMtmFzMxHSpjblhhjT0kUY5pTOPapC4RxLEuAKc0mOBUJlLdKYKEFiXdmnBgKiBpCcd6YxzvUDt370rvVeR6AGSyYqnLNilnkHrWfPLnPIpFIJ5N7e1VJ7gRocU2WXaM5Fc7qmpeUhywqWMmubrzGxmrmlj908nvXGQag08ud3FdnbuItKj/vMM/nQhSelijfT+Zee3AFdBZDEKiuVJLXsYPc5NdXaHCCpLZbJ45rsvA2pBpJbJz23L9a4tj8tS6VfPYX6TqcFTmpmroaZ7JSGmQTLPDHKhysihhin5xWBoJRS9TmigAzS02nUAOpM0tIaAYEUmMmio5hIYnEJUSkfLu6ZoEc14hv8AzJ/IRgY4evu1c6x/OrF7FLbyNFMCsoOSD/OqbH3rpitDCRBM555qi03zdBU878VRBy9UBbyCuapXJIJI6d6uL92qk9UIzJmIKt6EEVvJqIWEA9cVhTjAIqyDuUfSmSydJmmmZj0qzaNtdh71Vh45qxFxzQ0NGxA/HWriNxWZBJ3q6jGhCZaV8d6erZ71WDetPDUwLIbNGTUIYil3e9KwEuSe9MbkUhI9aaxx0pgxagvc/ZyR1zUpfA9KguZN0YA9aYI5q58ORXtwLoSGJ3PzqVyGP9K6S3torS2jii+4oqGE9Qe9TPKMY70mDWo9T83HSpagU1JmpKHZ9KN2O9MJppagQ/f6Ub6hLYzSbxTAVmxVWWXrTpZOapzSYBFIZXuJuvIrNlm68iprh8A81mTzbQaTKQy7ugqHkdK4fVZpbycRRgtn0ra1O92qecZFO0OwWK2kupRmR8nnsKW472Oat1MXBUgg4xXdROBaqz8bVAArk7BWutTT92RHGd7ZHX0ro7yXERHrT6EvVle3Yy3+4npXVWxwork9N+aYt74rq7UZAqUUW2OEqIg7M05znApzDCYpMo9G8Fal9r0z7MxHmQfyNdLivKvCup/2bq0W4gRSfI2fQ16sefpXPJWZdxBS9aTvS0gG0ooNAFAxx6UGl60UCG01mCAsxwqjJPoKeaw/E999msPJRiJJzjjsvemld2E3ZHKanete300+MhzwPQdqz5JsCp+oxnHvVWWby/vKCK6lEwvcpzyZHAP5VXQMW6cU+5uxngYqqLhiRjNOwzQAcCq1xG5GQKckjYyc4pXkGOapAZUzYzxU8LZiX6UXIVwfWobV/wB3gdiRQQzQjHFTocAVBAC3Wps8UMaJ4ZdrYz1rQjkxjmsdCc1cjl7EmmBpK+T1qRWFUkfPNSq+KYWLe+jcKgWSnbxSsKxLvpN4JNRbxUZfk80ASO5JwDSKm4HNMGKWSUQxZ9aBK45VCE0113HrUKyM/PODQzkc5zSZRaTpTy1Qo3FDMB3pAPL8daZvHeomkHPPFRGSgZM0nvUauSOtQmT3qrqGsx6akSi2muJ5M4SMdAO5PagRalfrzVKaXg0yLVUu1y8LwtnoVPFNlxIDtYHPoaAKFzJnJzWLe3AUHmtia3kYng9ayLq0Ab966j29aLFXMBo2vJ0U/dzzXVvFHDaeWGwdvAArOgWONgY05/vMP5VYmbCSe6mpuG5n6NM1wJpmJPO0duntRqMhjRj/ABHpVuz2iHOMcVmX0hlnJJ4FN7CW5Z0kYCjvmustvljFcxo8ZZlbtXTpgrU7Fkqne/0qR+lQxcNU7c80FFVnKOGHUV654a1VdV0mGQsDKg2MPpXkM2SDW54P1ptPkkXcSoO/b6jv+n8qyqIpHrPvQDSJIkqK8bBkcAgjuKdisigPNA4o60dKBDqKQ0EYoGwNcr4vglJt5wpMKqVZh0U5711ZpjKrqVdQysMEEZyKafK7ktXPLs5qCbb3Ga67VvC5QtPY5Zeph7j6f4Vxl7ujYqysrDqCMV1RmpGDi7mdcsmeRj6VFHyeMU5o8tk1IgVOoq7ALuk7VG5fmpkPmSZ7UXDrGuVXOKYrmZPJjII5qCycHzQM8NVfUdWgjDDY2/FVNJu/PM5x0IPWiwWOqgYbafu4xVO2kyoqcMaQEydamB71BGc1OOlAEySVOjZ71TU1Kj4piLYfFLv96hDg0uaYybzMdqYGyajzTozjFLqJk2RTJfnAB5FITmlI4BoYIUAAfSopJAPWnEnmoXB6j1pMZYV+OTTXk96i3YFRM+aSGPaSo2kzTGb1qMt1pgPL4pqsGmBIzhOn41EXwKTzWXBC8YHPrQIWcjLc1RZ/L5BqGe7Ys2VbOao3FyyYGGz9KYDdSu5Dj944HscVlifPqQPWi6eSViPmAHPSo9jDCkEZ71nJlpF23JYAnIFOZzIsgHPFU42kuGCRqzEnaAKe7TQytEzIQODsOcH0NJAyff5UOB6day5TlsdSauySfJk9Kpx4eYGqYoo29Lj8uNeOa3I+FrLsR8orUVsjAFSUTxKc5qV+BUSkimSS4HJosO5BO2FOM9ajs7j7JcRSdgwz9O9I2+Y4A4qKWPK470nG4Jnr3hHUVlhlsHb95bcpn+JD0/Kukrz7wJsu7uO5Zj50cLRkevT+leg81zvRmiAdaXNJikpDJKQ80tFACfWkNKaSgQZqvdafb6kuy4t45eDgkc/nU+Kzte1dNB0TUdTfpawPIPc44H5kUm7ajtfQ+a/GPxSg8PeL9R0210o3WmW0nlCRJDvyPvY7EZzWjpfxE0DWgqrc/ZJm48q5BQ5+p4P515R5rzO8kvMjuzMT3JJJokIZSGUEVzxxs4vXU65YODR7wriNA6kMrdCGyDWdeXzkMM4GO1eIQ6nd6Q26yu54Oc7FfKn/AICeK1Y/iXfRLsubWC4/2gSh/TiuynjYSWuhyzwc47and3kqNxjmotOnWK4kRV+8v0ziuDuPiZGgLtpZIHYTf/Wry/xH8Y9W1Pxtodto9mLeGC5jBtw+TOzHaVY+mDXQq0HszF0pR1Z9cWRPkKxGN1WgarqnlpGgH3RipQ2KsyuWoeRU5wKgh+6KezY+lMLjwaep7VApqRT0oEycHmnbqiHIpcGhFEmR61KhzVWpon/OmJliiaQRgDvTd1V7nkigSHibPaoGcs49M9KQCojw4pMosbuKjZqC3FQu1SgB3qNmyKaScUwn1phYJG4p7sF3D/PSoGO44odshuO5psGUZmw54qtK2RnHIqSUZc01I/MYD1NIVyCVY44lmuZ1ghLbAzMAXb+6Ky9U1TStEhkudVvooYF+6NwyfavF/wBojxak+s6TothPKX0ebz5kHCFuCufWvMrW38QePr6W7YzXG0/vLiV9kMY9Nx4H0FJw05pOyKT6HtupftC6TZRXFvpel3BlZWSO498deT/SpfgpqN7qvhG9nv1kLi7dlmkbJkyefwFeB6hpGn6UJ1GtRXNxAuStshdC5PC7j1PvX0l8OrO40XwLpWn3CoLjZ5km33JI/nU81Nr3HcFe+p1DEuoA71bsbP5t7GmWKRzfe+8K27dEICpTsFyeBABxVuNSenSo4gEA4zUu/NNJDQ/oKaVBPIyKAd1ABBxTsMeQAuAMVXkwAfWplbjnrWvpvhLUdYYMkfkwE/62UYGPYdTSbS3Balr4aK8uq3QAOyJNzHtk8CvU6zNE0S20C0Nvb5ZnOZJCOXPrWmK5JO7uapCE0gpSKSpGSUUUdKAENNwafSGgQ2vKvj/qx0/wfa2SNh9QuVVv91RuP64r1U18/wD7R97u1fw9ZZGI4JJiPdiB/wCy1lWdoM1oq80jxZBUFw2M5NXI4tw5qC600SchmH0Neaj1DAvZSATxzWLLcsCM81tX+mzKCVkJ+orAns7lScoT+HFbRM5lLVNRCWzkEjA9KwfgdpTeJ/jFYySJvt7DfeyZGR8g+X/x4j8qs66lx9llBTA2+td5+yroghg8Ra+6kSTOtnGfZRub9Sv5V34ZXZ5+JbsfSUb7jUm6q8JwM4qQNk16BwGjD9wU5zTYeEFDnmgAXrUynj3FQA/NUq9TTETLzT6jXinZoNBcUmdvNLmmOeOlMlkkU2Tg1BcsfNPPFNAIORVa8nKSqu5Rk45oBFsE4qIA+ZkkVCbhJGZI50YLxle570saBXPzZOOaljLRYYqGQ+lKSKYxoQWGMeKjJz1pWOajLUDAH5h9aaRlDz1z0oU/NnsKjLbIxg/jTERmPJLEUJETKu0HqKnDZQEVFGxM6KDglgKQWPk34rm0l+KmtQz28riOHcQox5sirkZP93Hp6VxsV5NqOiMk155kUcuBaxHbFGPTaOv416F8Sb25v/iB4ozbq0aQRwrOoPCk8gHpk5P5V5ZDaWujWU7yzF5ppNuF5Krk4FeZiZym7X2OqlTfK2jeWyg+x62trCHXy4YyygDZufk/hz05r6dtkjh06LYxKCNFUnuNor5u8HCO/tRFKi7tRvUESMf9Z5Q5BPp8/P0r6TuFjgtgrMqIgGSTgA/4Vphr9TJxcXZmlYBYgpxnPPJreikAwRj6CuYhvbJIwZb60QAZy0oFRv410SxUhtQjmYdEgBcn+ldzlFbszUJN7Haq5IyMVIuGyfTrXlGp/Fm+RGTSdOhT0lu2z/46v+NcpY+KvEGq6tFJqOpvInmA+VGNkf02j+tYSxUFojoWFna7PpvT/DOq3+Ghs5BGeQ8nyj9a6mw+H4BDX12f9yEf1P8AhXXaZc/a9I06cMSJbeNv/HRVmpdWTI5bGbYeHdL04hoLRPMH8b/M361pkn1pKXrzWbd9ykhOtLRmjNAxc0mKDSigTFNKaKQnNAxRSGlHNIaBCV8u/tAXZl+IUMZORDZRKB6Zyf619Rda+T/joxb4l3YP8MEI/wDHK58R8B0YbWZx8J3VO3I6VBb9M1YYjAxXnnpmfcRAgmsi5iwDW/KDg1lXS5yParixNXRxHiG33W8mM8rXpX7PUaw/DuFAAHF5c7seu4f0xXFavFugYY4xXZfANwPDupW+f9TfSHHpuVTXpYOWtjzMZGyPYImwoqVWBb6VCpwop0R+frXonmmvEfkFNc0RnCj6UyRuKAuKpqdCMZzVNW5qwrflQBZzTt3rUG73oLdeaaLTJ91BAPeoA5FKH96ZMiZQqnPYVwvi27dJ4D5hWOeTYW/ujj/Gu1Zx5Tk9ga5s2ceoZiuYw8RIOD29x70mNbGT4StPL1O8MJc2JztJPXB4P867BCN77c9qjs7aK1QqmAO1KjYd+c0hkpNRs3p0pWbmo3OfYUDGlielRsSKcTTGOaAGltqOf9k1XnYqh571NJ/q2/D+dVLpuOppkliGYMgGRToPluQxPTmsyGby3x2q1vfzQwA2AZYn0xUvZj6nyxrkt81545NxIgS5PmR7HBUAOq7sdeFrzjU2tFWNIc4yMs38RCntXSXXiPSF8V69do0o025V7dkdSSSzHcw9BnJxVGw8LXH9rEXxCafZxmf7QR8kg/gAPck9utcSg3dy3NoyasWdNgZtV8HaTp80guoJAJggwVLtukOfpwfpXuXxH1RY9IaAHIuJVQD26/0rmvhDodpb+FP7ekiDardySoZ25KqGxhfTOOazvH2om61SxtEYEQIXbPZj0/QU52hGyNKK5pczKVskbqMov4itKFEX7qjHtWPbllxll/CtWCRcDkGvOl5npRsWJnypAo05yl3Gf9oUx/mHGMUy0JFwvPelHRly2sfevw9u/t3gbQJsgk2oU/Ucf0rpMVwnwbl8z4c6Rz90yL/48a70V3x2PKktRtFKaSqEKDSnmkFLQAlLRRQJjqCM0dKOtAxB0o7UGgUCDGRXyb8dwY/ibck8B7eFh7/J/wDWr6zr5T/aGj8v4kRHH37GE/8AoQ/pXPiPgN8M/wB4cNanK/WrmMis61bArQRsjFeceoQTfdxWXcfeNas4zmsqfgmmg6GFqifu3/Gt/wCA8m248TW+eFlikH4qR/SsPURlGrX+BoYa/wCJiPueXCPxy1ehg375wYxe7c9szxT7c5kqLOBUtqfmzXrnkmqv3QfamSNuX2pdwCYqJzgUhDVOO9TK/FV1bmng0AWt+KXfnvVbeaUN6mmNFjcfWjfgc1AXHrSGTjii4MkllJjc5+XFU0Ze1Wj/AKh/fFUl4Y0DWhYOSKZCcFs9c0ySYqvFR20pbcSepNId0XC3HWo2Y0hbjOahkk96YyUsMVE8lRNJgcGomk7ZpCJZXJjwD3FU7lvepJG4UZ6tVO6k5oJIXfjPpVhdRRIdzk7SCCPY8Gs+WbaCBVSGdcSRSjKHkChq6KaPnHx78MG8P6Lc6jBePdNLebVSJOBG5J7ZyelXPC3gTX/FrQy6zJNZ6YgGFK4eQDsi/wAP1PNe7XEkhMZSKFkAO+N14PPBGOhFILhUARE5PU1HPJaF8qZSuorHQdFjt7eNbfT7RDsQfwgDn8a8WgJ1e6nvZl+aZywz2Hb9K9G+Jt7JHoUEEeQbqYRsR/dAJP54FcXptuI41AFefiJWdjuw8NLk8GmRkj5c1qwabCAPkpbaMZFaKqAorhlI7oxM2e0jVTtBFZ8SCOda1bo4HWsZ5QJx9RUxlqNqx9tfBAZ+G2lN2Z5SP++q9D6Vw3wdg8j4Y+Gx3khaT83NdxXpx2R5Ut2OpccU0U7pVEMMcUlLmk5NAIKKTp9aWgBetGaKKAYE4pAc0UUCFHSvlr9o0Y+INiR1NhH/AOhNRRWNf4ToofGjza25NaK9KKK849Ia44rLuurUUULcb2MS/wDu4re+Bv8Ax/eJT33xD9Goor0MJ8Zw4v4T2MjjFTWo+YCiivUPJL57VG3FFFADFHNSUUUAFFFFACGhaKKAHt/qjVRetFFPoX0Ff0xUcPU0UUiSVyQtVWJJ5oooKI3JxUBY5oooJGzE5j/Gqc7Hd1oooBGfdk1V27sE9aKKCmSIASARTZIkVuFooqHuXE4f4jjNlYDt5/8A7LXLWXaiivNxHxM9DD/CbVuAfyq1ng0UVwyOyJn3JyCawJmIkz70UU4bimfoB8OY1i+HvhdVGALCM/mK6cUUV6kdkeU9xaDRRTJYmaUUUUCEPFGeKKKCj//Z",
    schrodinger: "data:image/jpeg;base64,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"
  };

  function scientist(name, photoKey, points) {
    return '<li class="sci">' +
      '<figure class="portrait"><img src="' + photos[photoKey] + '" alt="Portrait of ' + name + '">' +
      '<figcaption>' + name + '</figcaption></figure>' +
      '<b>' + name + '</b><ul>' + points.map(t => '<li>' + t + '</li>').join('') + '</ul></li>';
  }

  /* ---------- Note-page helpers (diagrams built as inline SVG) ---------- */
  const sec = (n, t) => `<h3 class="sec"><span class="num">${n}</span>${t}</h3>`;

  function atomDiagram() {
    // 3D electron-cloud points (Gaussian around the nucleus); JS rotates them
    let seed = 11;
    const rnd = () => (seed = (seed * 16807) % 2147483647) / 2147483647;
    const gauss = () => Math.sqrt(-2 * Math.log(rnd() + 1e-6)) * Math.cos(2 * Math.PI * rnd());
    let dots = '';
    let n = 0;
    while (n < 170) {
      const x = gauss() * 24, y = gauss() * 24, z = gauss() * 24;
      if (Math.sqrt(x * x + y * y + z * z) > 62) continue;
      const r = 1.1 + rnd() * 1.1;
      dots += `<circle class="el" data-x="${x.toFixed(1)}" data-y="${y.toFixed(1)}" data-z="${z.toFixed(1)}" data-r="${r.toFixed(2)}" cx="${(150 + x).toFixed(1)}" cy="${(95 + y).toFixed(1)}" r="${r.toFixed(2)}" fill="#2E7D6B" opacity=".8"/>`;
      n++;
    }
    return `<figure class="fig big"><svg class="diagram spin" id="atomCloud" viewBox="0 0 300 190" role="img" aria-label="An atom: a small nucleus at the center surrounded by a rotatable cloud of electrons">
      <defs>
        <radialGradient id="cloudG"><stop offset="0" stop-color="#2E7D6B" stop-opacity=".5"/><stop offset="1" stop-color="#2E7D6B" stop-opacity="0"/></radialGradient>
        <radialGradient id="nucG" cx=".35" cy=".35"><stop offset="0" stop-color="#eaa872"/><stop offset="1" stop-color="#B5622E"/></radialGradient>
      </defs>
      <circle cx="150" cy="95" r="86" fill="url(#cloudG)"/>
      <circle cx="150" cy="95" r="86" fill="none" stroke="#2E7D6B" stroke-opacity=".4" stroke-dasharray="3 4"/>
      ${dots}
      <circle cx="150" cy="95" r="13" fill="url(#nucG)"/>
      <path d="M58 27 L140 87" stroke="#B5622E" stroke-width="1.2" fill="none"/>
      <circle cx="140" cy="87" r="2" fill="#B5622E"/>
      <text x="6" y="22" font-size="12" font-weight="700">Nucleus</text>
      <path d="M208 153 L226 168" stroke="#2E7D6B" stroke-width="1.2" fill="none"/>
      <circle cx="208" cy="153" r="2" fill="#2E7D6B"/>
      <text x="294" y="182" font-size="12" font-weight="700" text-anchor="end">Electron cloud</text>
    </svg><figcaption>Fig. 1 · Drag the electron cloud to rotate it</figcaption></figure>`;
  }

  // Makes the electron cloud spin slowly and lets you drag to rotate it
  function initAtomSpin() {
    const svg = document.getElementById('atomCloud');
    if (!svg || svg._spin) return;
    svg._spin = true;
    const dots = [...svg.querySelectorAll('circle.el')];
    const pts = dots.map(c => ({ x: +c.dataset.x, y: +c.dataset.y, z: +c.dataset.z, r: +c.dataset.r }));
    const still = window.matchMedia('(prefers-reduced-motion: reduce)').matches;
    let ax = 0.35, ay = 0, dragging = false, lx = 0, ly = 0;

    function draw() {
      const cY = Math.cos(ay), sY = Math.sin(ay), cX = Math.cos(ax), sX = Math.sin(ax);
      for (let i = 0; i < pts.length; i++) {
        const p = pts[i];
        const x = p.x * cY + p.z * sY, z1 = -p.x * sY + p.z * cY;
        const y = p.y * cX - z1 * sX, z = p.y * sX + z1 * cX;
        const s = 1 + z / 300;
        const c = dots[i];
        c.setAttribute('cx', (150 + x * s).toFixed(1));
        c.setAttribute('cy', (95 + y * s).toFixed(1));
        c.setAttribute('r', (p.r * s).toFixed(2));
        c.setAttribute('opacity', Math.max(0.25, Math.min(1, 0.65 + z / 110)).toFixed(2));
      }
    }
    svg.addEventListener('pointerdown', e => {
      dragging = true; lx = e.clientX; ly = e.clientY;
      svg.setPointerCapture(e.pointerId); svg.classList.add('grabbing');
    });
    svg.addEventListener('pointermove', e => {
      if (!dragging) return;
      ay += (e.clientX - lx) * 0.012;
      ax = Math.max(-1.3, Math.min(1.3, ax + (e.clientY - ly) * 0.012));
      lx = e.clientX; ly = e.clientY;
      if (still) draw();
    });
    const stop = () => { dragging = false; svg.classList.remove('grabbing'); };
    svg.addEventListener('pointerup', stop);
    svg.addEventListener('pointercancel', stop);

    (function loop() {
      if (!svg.isConnected) return;               // page was turned; stop
      if (!bookOverlay.classList.contains('open')) { setTimeout(loop, 250); return; }
      if (!still && !dragging) ay += 0.006;       // gentle auto-spin
      if (!still || dragging) draw();
      requestAnimationFrame(loop);
    })();
    draw();
  }

  function shellTable() {
    const L = ['K', 'L', 'M', 'N', 'O', 'P', 'Q'];
    const row = (label, cells, cls = '') => `<tr><th>${label}</th>${cells.map(c => `<td class="${cls}">${c}</td>`).join('')}</tr>`;
    const ns = [1, 2, 3, 4, 5, 6, 7];
    return `<table class="shells">` +
      row('n', ns) + row('Shell', L, 'shell') + row('2n<sup>2</sup>', ns.map(n => 2 * n * n), 'cap') + `</table>`;
  }

  function shellDiagram() {
    const L = ['K', 'L', 'M', 'N', 'O', 'P', 'Q'];
    let rings = '';
    L.forEach((l, i) => {
      const r = 14 + i * 12.5;
      rings += `<circle cx="150" cy="95" r="${r}" fill="none" stroke="#2E7D6B" stroke-opacity="${(0.9 - i * 0.08).toFixed(2)}" stroke-width="1.4"${i === 6 ? ' stroke-dasharray="4 3"' : ''}/>` +
        `<circle cx="${150 + r}" cy="95" r="5.6" fill="#2E7D6B"/>` +
        `<text x="${150 + r}" y="98.3" font-size="8.5" font-weight="700" text-anchor="middle" style="fill:#fff">${l}</text>`;
    });
    return `<figure class="fig"><svg class="diagram" viewBox="0 0 300 190" role="img" aria-label="Seven concentric shells K to Q around the nucleus">
      <defs><radialGradient id="nucG2" cx=".35" cy=".35"><stop offset="0" stop-color="#eaa872"/><stop offset="1" stop-color="#B5622E"/></radialGradient></defs>
      ${rings}
      <circle cx="150" cy="95" r="7" fill="url(#nucG2)"/>
      <text x="6" y="22" font-size="11" font-weight="700">Nucleus</text>
      <path d="M46 26 L145 92" stroke="#B5622E" stroke-width="1.1" fill="none"/>
      <text x="6" y="176" font-size="10" font-style="italic" opacity=".8">K = closest, lowest energy</text>
      <text x="294" y="176" font-size="10" font-style="italic" opacity=".8" text-anchor="end">Q = farthest, highest</text>
    </svg><figcaption>Fig. 2 · Shells K to Q (n = 1 to 7), moving outward</figcaption></figure>`;
  }

  function capRows() {
    const data = [['s', 1, 2], ['p', 3, 6], ['d', 5, 10], ['f', 7, 14]];
    return `<div class="orb-rows">` + data.map(([l, o, e]) =>
      `<div class="orb-row"><span class="ltr">${l}</span>` +
      `<span class="boxes">${'<span class="box">↑↓</span>'.repeat(o)}</span>` +
      `<span class="cap"><b>${o}</b> orbital${o > 1 ? 's' : ''} · max <b>${e}</b> e⁻</span></div>`).join('') +
      `</div><p class="hint">Each box is one orbital and holds up to 2 electrons (↑↓).</p>`;
  }

  function shapesDiagram() {
    const petals = (cx, cy, angles, lens, ry) => angles.map((a, i) => {
      const L = Array.isArray(lens) ? lens[i % lens.length] : lens;
      return `<ellipse cx="${cx + L / 2}" cy="${cy}" rx="${L / 2}" ry="${ry}" transform="rotate(${a} ${cx} ${cy})" fill="url(#lobeG)" stroke="#2E7D6B" stroke-width="1.2"/>`;
    }).join('');
    const label = (cx, l, name) =>
      `<text x="${cx}" y="128" font-size="14" font-weight="700" text-anchor="middle">${l}</text>` +
      `<text x="${cx}" y="143" font-size="10" font-style="italic" text-anchor="middle" opacity=".8">${name}</text>`;
    const cy = 58;
    return `<figure class="fig"><svg class="diagram" viewBox="0 0 420 150" role="img" aria-label="Shapes of s, p, d and f orbitals">
      <defs><radialGradient id="lobeG"><stop offset="0" stop-color="#2E7D6B" stop-opacity=".95"/><stop offset="1" stop-color="#2E7D6B" stop-opacity=".3"/></radialGradient></defs>
      <circle cx="52" cy="${cy}" r="34" fill="url(#lobeG)" stroke="#2E7D6B" stroke-width="1.2"/>
      ${petals(157, cy, [90, 270], 56, 15)}
      ${petals(262, cy, [45, 135, 225, 315], 46, 12)}
      ${petals(367, cy, [0, 45, 90, 135, 180, 225, 270, 315], [48, 36], 8)}
      <circle cx="52" cy="${cy}" r="2.5" fill="#B5622E"/><circle cx="157" cy="${cy}" r="2.5" fill="#B5622E"/>
      <circle cx="262" cy="${cy}" r="2.5" fill="#B5622E"/><circle cx="367" cy="${cy}" r="2.5" fill="#B5622E"/>
      ${label(52, 's', 'spherical')}${label(157, 'p', 'peanut / dumbbell')}${label(262, 'd', 'clover leaf')}${label(367, 'f', 'flower')}
    </svg><figcaption>Fig. 3 · Orbital shapes (the dot marks the nucleus)</figcaption></figure>`;
  }

  const content = {
    "1": {
      "label": "No. 01",
      "title": "Week 1: Quantum Mechanics Pioneers",
      "pages": [
        "<h3>Scientists Mentioned</h3><ul>" +
          scientist("Louis de Broglie", "broglie", [
            "Proposed that electrons can behave like waves.",
            "Developed the matter-wave theory.",
            "His work helped explain wave-particle duality.",
            "Contributed to the quantum model of the atom.",
            "Helped explain electron behavior around nuclei."]) +
          scientist("Werner Heisenberg", "heisenberg", [
            "Developed an important form of quantum mechanics.",
            "Proposed the Heisenberg Uncertainty Principle.",
            "Stated position and momentum cannot both be known.",
            "Showed electrons don't move in simple fixed paths.",
            "Established modern understanding of electron behavior."]) +
        "</ul>",
        "<h3>Scientists Mentioned (Continued)</h3><ul>" +
          scientist("Erwin Schrödinger", "schrodinger", [
            "Developed the Schrödinger wave equation.",
            "Used mathematics to describe electron behavior.",
            "Introduced the concept of electron orbitals.",
            "Explained probabilities of finding electrons.",
            "Finalized the modern quantum mechanical model."]) +
        "</ul>",

        "<div class='nt'>" + sec(1, "Structure of an Atom") +
          "<ul class='pts'>" +
            "<li>The <b>nucleus</b> is at the center, surrounded by <b>electron clouds</b>.</li>" +
            "<li>Hierarchy order:<div class='flow'><span class='chip'>Energy level</span><i>→</i><span class='chip'>Subshell</span><i>→</i><span class='chip'>Orbital <small>(max 2 e⁻)</small></span></div></li>" +
          "</ul>" + atomDiagram() + "</div>",

        "<div class='nt'>" + sec(2, "Energy Levels (Shells)") +
          "<ul class='pts'>" +
            "<li><b>Principal quantum number (n):</b> tells the energy level (n), describes the size/energy of the orbital, and relative distance.</li>" +
            "<li>There are <b>7</b> periods (energy levels) discovered.</li>" +
            "<li>Each shell adds electrons based on the formula: <span class='hl'>2n<sup>2</sup></span></li>" +
            "<li>Shell list:</li>" +
          "</ul>" + shellTable() + shellDiagram() + "</div>",

        "<div class='nt'>" + sec(3, "Subshells (Sublevels)") +
          "<ul class='pts'>" +
            "<li>Each shell is divided into smaller regions called <b>subshells</b> or <b>sub-energy levels</b>.</li>" +
            "<li>The <b>4</b> sublevels and their names:" +
              "<ul class='names'>" +
                "<li><span class='ltr'>s</span> sharp</li>" +
                "<li><span class='ltr'>p</span> principal</li>" +
                "<li><span class='ltr'>d</span> diffuse</li>" +
                "<li><span class='ltr'>f</span> fundamental</li>" +
              "</ul></li>" +
          "</ul>" + sec(4, "Sublevel Capacities") + capRows() + "</div>",

        "<div class='nt'>" + sec(5, "Orbitals &amp; Shapes") +
          "<ul class='pts'>" +
            "<li>Orbitals are regions of space where the probability of finding an electron of an atom is highest.</li>" +
            "<li>Shape for <span class='ltr'>s</span>: <b>spherical</b></li>" +
            "<li>Shape for <span class='ltr'>p</span>: <b>peanut / dumbbell</b></li>" +
            "<li>Shape for <span class='ltr'>d</span>: <b>clover leaf</b></li>" +
            "<li>Shape for <span class='ltr'>f</span>: <b>flower</b></li>" +
          "</ul>" + shapesDiagram() + "</div>"

      ]
    },
    "2": { "label": "No. 02", "title": "Week 2", "pages": [
        "<div class='nt'><h3>The Periodic Table & Electron Configuration</h3>" +
          "<ul><li><b>Atomic number (Z)</b> = number of protons = number of electrons in a neutral atom.</li>" +
          "<li><b>Atomic mass</b> = average mass in u (amu). A value in ( ) is the mass number of the most stable isotope.</li>" +
          "<li><b>Period</b> (row) = energy level <span class='ltr'>n</span>. <b>Group</b> (column) = similar valence electrons.</li>" +
          "<li><b>Block</b> = where the last electron goes: <span class='ltr'>s</span> groups 1–2 (+He), <span class='ltr'>p</span> groups 13–18, <span class='ltr'>d</span> groups 3–12, <span class='ltr'>f</span> the two bottom rows.</li></ul>" +
          "<p><b>Filling order (Aufbau)</b> – follow the arrows:</p><div class='fo'>1s → 2s → 2p → 3s → 3p → 4s → 3d → 4p → 5s → 4d → 5p → 6s → 4f → 5d → 6p → 7s → 5f → 6d → 7p</div>" +
          "<p><b>Capacity:</b> <span class='ltr'>s</span> = 2 · <span class='ltr'>p</span> = 6 · <span class='ltr'>d</span> = 10 · <span class='ltr'>f</span> = 14 electrons.</p>" +
          aufChart() + "</div>",

        "<div class='nt'><h3>Interactive Periodic Table</h3><p class='ptnote'>Tap any element to see its atomic number, mass and electron configuration.</p><div id='ptMount'></div></div>",

        "<div class='nt'><h3>Reading Configurations</h3>" +
          "<ul><li><b>O (Z = 8):</b> 1s<sup>2</sup> 2s<sup>2</sup> 2p<sup>4</sup> — 2nd period, p-block.</li>" +
          "<li><b>Fe (Z = 26):</b> [Ar] 3d<sup>6</sup> 4s<sup>2</sup> — 4th period, d-block (3d).</li>" +
          "<li><b>[Noble gas] shorthand:</b> replace the inner electrons with the previous noble gas in brackets.</li>" +
          "<li><b>Exceptions:</b> Cr is [Ar] 3d<sup>5</sup> 4s<sup>1</sup> and Cu is [Ar] 3d<sup>10</sup> 4s<sup>1</sup> – half-filled and full d sublevels are extra stable.</li></ul>" +
          "<p><b>Where each sublevel lives</b></p>" +
          "<ul><li><span class='ltr'>s</span>: groups 1–2 (1s = period 1, 2s = period 2 …)</li>" +
          "<li><span class='ltr'>p</span>: groups 13–18 (2p = period 2, 3p = period 3 …)</li>" +
          "<li><span class='ltr'>d</span>: groups 3–12 (3d = period 4, 4d = period 5, 5d = period 6, 6d = period 7)</li>" +
          "<li><span class='ltr'>f</span>: the bottom rows (4f = lanthanides, 5f = actinides)</li></ul></div>",

        "<div class='nt'><h3>How to Do the Aufbau Principle</h3><p>Aufbau means “building up”: electrons fill the <b>lowest-energy</b> sublevel first.</p>" +
          "<ol><li>Find the atomic number <b>Z</b> – that is the number of electrons.</li>" +
          "<li>List the sublevels in order: 1s 2s 2p 3s 3p 4s 3d 4p 5s 4d 5p 6s 4f 5d 6p 7s 5f 6d 7p.</li>" +
          "<li>Fill each one up to its capacity (s = 2, p = 6, d = 10, f = 14).</li>" +
          "<li>Stop when all Z electrons are placed, then check that the superscripts add up to Z.</li></ol>" +
          "<p><b>Example: Chlorine (Z = 17)</b></p><ul><li>1s² → 2 used</li><li>2s² → 4</li><li>2p⁶ → 10</li><li>3s² → 12</li><li>3p⁵ → 17 ✓ (only 5 are left, so 3p is not full)</li></ul>" +
          "<p><b>1s² 2s² 2p⁶ 3s² 3p⁵</b> = [Ne] 3s² 3p⁵</p>" +
          "<p><b>Example: Iron (Z = 26)</b> → 1s² 2s² 2p⁶ 3s² 3p⁶ <b>4s² 3d⁶</b> (4s fills before 3d) = [Ar] 3d⁶ 4s²</p></div>",

        "<div class='nt'><h3>How to Do an Orbital Diagram</h3><ul>" +
          "<li>Draw one box per orbital: <b>s = 1</b>, <b>p = 3</b>, <b>d = 5</b>, <b>f = 7</b> boxes.</li>" +
          "<li><b>Aufbau:</b> fill the lowest sublevel first.</li>" +
          "<li><b>Pauli exclusion:</b> at most 2 electrons per box, with opposite spins (↑↓).</li>" +
          "<li><b>Hund's rule:</b> in a sublevel, put one ↑ in every box first, then pair them up.</li></ul>" +
          "<p><b>s example – Beryllium (Z = 4)</b></p>" + orbDiag([['1s',1,2],['2s',1,2]]) +
          "<p><b>p example – Nitrogen (Z = 7)</b> – three unpaired 2p electrons (Hund's rule)</p>" + orbDiag([['1s',1,2],['2s',1,2],['2p',3,3]]) +
          "<p><b>d example – Iron (Z = 26)</b></p>" + orbDiag([['[Ar]',0],['4s',1,2],['3d',5,6]]) +
          "<p><b>f example – Europium (Z = 63)</b> – half-filled 4f</p>" + orbDiag([['[Xe]',0],['6s',1,2],['4f',7,7]]) + "</div>"
      ] },
    "3": { "label": "No. 03", "title": "Week 3", "pages": ["Add your Week 3 notes or project links here."] },
    "4": { "label": "No. 04", "title": "Week 4", "pages": ["Add your Week 4 notes or project links here."] },
    "5": { "label": "No. 05", "title": "Week 5", "pages": ["Add your Week 5 notes or project links here."] },
    "6": { "label": "No. 06", "title": "Week 6", "pages": ["Add your Week 6 notes or project links here."] },
    "7": { "label": "No. 07", "title": "Week 7", "pages": ["Add your Week 7 notes or project links here."] },
    "8": { "label": "No. 08", "title": "Week 8", "pages": ["Add your Week 8 notes or project links here."] },
    "9": { "label": "No. 09", "title": "Week 9", "pages": ["Add your Week 9 notes or project links here."] },
    "10": { "label": "No. 10", "title": "Week 10", "pages": ["Add your Week 10 notes or project links here."] },
    "me": {
      "label": "About",
      "title": "Myself and My Experiences in Science",
      "pages": [
        "<div class='nt about'><h3>Welcome to My Study Hub!</h3>" +
          "<p class='dropcap'>Before taking the entrance exam, I thought Laguna Science National High School would be just like any ordinary school. But once I stepped onto the campus, my perspective changed. The engaging teaching style of the teachers made me feel right at home.</p>" +
          "<p>As I advanced to higher grade levels, science became even more enjoyable through exciting experiments and collaborative group tasks. That is why I created this website to serve as a helpful study guide and reviewer for my academic journey.</p></div>",

        "<div class='nt about-side'><div class='sig'>Hans Fredric F. Canaya</div>" +
          "<figure class='portrait solo'><img src='" + photos.me + "' alt='Portrait of Hans Fredric F. Canaya'>" +
          "<figcaption>Creator of this Study Hub</figcaption></figure></div>"
      ]
    }
  };

  const items = ["me", 1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
  const rack = document.getElementById('rack');
  const bookOverlay = document.getElementById('bookOverlay');
  const bookTitle = document.getElementById('bookTitle');
  const leftPage = document.getElementById('leftPage');
  const rightPage = document.getElementById('rightPage');
  const closeBookBtn = document.getElementById('closeBook');
  const bookBody = document.getElementById('bookBody');
  const prevPageBtn = document.getElementById('prevPageBtn');
  const nextPageBtn = document.getElementById('nextPageBtn');
  const pageIndicator = document.getElementById('pageIndicator');

  let currentKey = null;
  let currentSpreadIdx = 0;

  const currentTheme = localStorage.getItem('science_theme') || 'dark';
  document.documentElement.setAttribute('data-theme', currentTheme);

  document.getElementById('theme-toggle').addEventListener('click', () => {
    const nextTheme = document.documentElement.getAttribute('data-theme') === 'dark' ? 'light' : 'dark';
    document.documentElement.setAttribute('data-theme', nextTheme);
    localStorage.setItem('science_theme', nextTheme);
  });

  const atomSVG = `<svg class="atom" viewBox="0 0 26 26" fill="none">
    <ellipse cx="13" cy="13" rx="11" ry="4.5" stroke-width="1.1"/>
    <ellipse cx="13" cy="13" rx="11" ry="4.5" stroke-width="1.1" transform="rotate(60 13 13)"/>
    <ellipse cx="13" cy="13" rx="11" ry="4.5" stroke-width="1.1" transform="rotate(120 13 13)"/>
    <circle class="e" cx="13" cy="13" r="2.4"/>
  </svg>`;

  /* ---------- Periodic table (Week 2) ---------- */
  const PT_RAW='H Hydrogen 1.008|He Helium 4.0026|Li Lithium 6.94|Be Beryllium 9.0122|B Boron 10.81|C Carbon 12.011|N Nitrogen 14.007|O Oxygen 15.999|F Fluorine 18.998|Ne Neon 20.180|Na Sodium 22.990|Mg Magnesium 24.305|Al Aluminium 26.982|Si Silicon 28.085|P Phosphorus 30.974|S Sulfur 32.06|Cl Chlorine 35.45|Ar Argon 39.95|K Potassium 39.098|Ca Calcium 40.078|Sc Scandium 44.956|Ti Titanium 47.867|V Vanadium 50.942|Cr Chromium 51.996|Mn Manganese 54.938|Fe Iron 55.845|Co Cobalt 58.933|Ni Nickel 58.693|Cu Copper 63.546|Zn Zinc 65.38|Ga Gallium 69.723|Ge Germanium 72.630|As Arsenic 74.922|Se Selenium 78.971|Br Bromine 79.904|Kr Krypton 83.798|Rb Rubidium 85.468|Sr Strontium 87.62|Y Yttrium 88.906|Zr Zirconium 91.224|Nb Niobium 92.906|Mo Molybdenum 95.95|Tc Technetium (98)|Ru Ruthenium 101.07|Rh Rhodium 102.91|Pd Palladium 106.42|Ag Silver 107.87|Cd Cadmium 112.41|In Indium 114.82|Sn Tin 118.71|Sb Antimony 121.76|Te Tellurium 127.60|I Iodine 126.90|Xe Xenon 131.29|Cs Caesium 132.91|Ba Barium 137.33|La Lanthanum 138.91|Ce Cerium 140.12|Pr Praseodymium 140.91|Nd Neodymium 144.24|Pm Promethium (145)|Sm Samarium 150.36|Eu Europium 151.96|Gd Gadolinium 157.25|Tb Terbium 158.93|Dy Dysprosium 162.50|Ho Holmium 164.93|Er Erbium 167.26|Tm Thulium 168.93|Yb Ytterbium 173.05|Lu Lutetium 174.97|Hf Hafnium 178.49|Ta Tantalum 180.95|W Tungsten 183.84|Re Rhenium 186.21|Os Osmium 190.23|Ir Iridium 192.22|Pt Platinum 195.08|Au Gold 196.97|Hg Mercury 200.59|Tl Thallium 204.38|Pb Lead 207.2|Bi Bismuth 208.98|Po Polonium (209)|At Astatine (210)|Rn Radon (222)|Fr Francium (223)|Ra Radium (226)|Ac Actinium (227)|Th Thorium 232.04|Pa Protactinium 231.04|U Uranium 238.03|Np Neptunium (237)|Pu Plutonium (244)|Am Americium (243)|Cm Curium (247)|Bk Berkelium (247)|Cf Californium (251)|Es Einsteinium (252)|Fm Fermium (257)|Md Mendelevium (258)|No Nobelium (259)|Lr Lawrencium (266)|Rf Rutherfordium (267)|Db Dubnium (268)|Sg Seaborgium (269)|Bh Bohrium (270)|Hs Hassium (277)|Mt Meitnerium (278)|Ds Darmstadtium (281)|Rg Roentgenium (282)|Cn Copernicium (285)|Nh Nihonium (286)|Fl Flerovium (289)|Mc Moscovium (290)|Lv Livermorium (293)|Ts Tennessine (294)|Og Oganesson (294)';
  const PT=PT_RAW.split('|').map((r,i)=>{ const a=r.split(' '); return {z:i+1,sy:a[0],nm:a[1],ms:a[2]}; });
  const ORD=['1s','2s','2p','3s','3p','4s','3d','4p','5s','4d','5p','6s','4f','5d','6p','7s','5f','6d','7p'], CAP={s:2,p:6,d:10,f:14};
  const NOB=[[2,'He'],[10,'Ne'],[18,'Ar'],[36,'Kr'],[54,'Xe'],[86,'Rn']];
  const EXC={24:'3d5 4s1',29:'3d10 4s1',41:'4d4 5s1',42:'4d5 5s1',44:'4d7 5s1',45:'4d8 5s1',46:'4d10',47:'4d10 5s1',57:'5d1 6s2',58:'4f1 5d1 6s2',64:'4f7 5d1 6s2',78:'4f14 5d9 6s1',79:'4f14 5d10 6s1',89:'6d1 7s2',90:'6d2 7s2',91:'5f2 6d1 7s2',92:'5f3 6d1 7s2',93:'5f4 6d1 7s2',96:'5f7 6d1 7s2',103:'5f14 7s2 7p1',110:'5f14 6d9 7s1',111:'5f14 6d10 7s1'};
  const sup=t=>t.replace(/(\d[spdf])(\d+)/g,'$1<sup>$2</sup>');
  const okey=o=>(+o[0])*10+'spdf'.indexOf(o[1]);
  function fill(z,skip){ let e=0, r=[]; for(const o of ORD){ if(e>=z) break; const t=Math.min(CAP[o[1]],z-e); if(e>=skip) r.push([o,t]); e+=t; } return r; }
  const fmt=r=>r.slice().sort((a,b)=>okey(a[0])-okey(b[0])).map(x=>x[0]+x[1]).join(' ');
  function cfg(z){
    let core=null; for(const n of NOB) if(n[0]<z) core=n;
    const rem=EXC[z]||fmt(fill(z,core?core[0]:0));
    const full=((core?fmt(fill(core[0],0))+' ':'')+rem).split(' ').sort((x,y)=>okey(x)-okey(y)).join(' ');   // shell order: 4f before 5s
    const last=fill(z,0).pop()[0];
    return {short:(core?'['+core[1]+'] ':'')+sup(rem), full:sup(full), last:last, exc:!!EXC[z]};
  }
  function ptPos(z){
    if(z===1) return [1,1]; if(z===2) return [1,18];
    if(z>=57&&z<=70) return [9,z-54]; if(z>=89&&z<=102) return [10,z-86];
    if(z<=10) return [2,z<=4?z-2:z+8]; if(z<=18) return [3,z<=12?z-10:z-0];
    if(z<=54) return [z<=36?4:5, z-(z<=36?18:36)];
    if(z<=86) return [6, z<=56?z-54:z-68];
    return [7, z<=88?z-86:z-100];
  }
  const blockOf=(r,c,z)=>r>=9?'f':(z===2||c<=2)?'s':c<=12?'d':'p';
  const BG={s:'#f6b89a',p:'#9fd8c6',d:'#a9c8ef',f:'#cdb8ee'};
  let ptSel=8, ptCache='';
  function ptBuild(){
    const rows=['1s','2s 2p','3s 3p','4s 3d 4p','5s 4d 5p','6s 5d 6p','7s 6d 7p'];
    let h="<div class='pt-info' id='ptInfo'></div><div class='pt-leg'>"+['s','p','d','f'].map(b=>"<span style='background:"+BG[b]+"'>"+b+"-block</span>").join('')+"</div><div class='pt-scroll'><div class='pt-grid'>";
    h+="<span class='pt-h' style='grid-row:1;grid-column:2/4;background:"+BG.s+"'>s</span><span class='pt-h' style='grid-row:1;grid-column:4/14;background:"+BG.d+"'>d</span><span class='pt-h' style='grid-row:1;grid-column:14/20;background:"+BG.p+"'>p</span>";
    rows.forEach((t,i)=>{ h+="<span class='pt-r' style='grid-row:"+(i+2)+";grid-column:1'>"+t+"</span>"; });
    h+="<span class='pt-r' style='grid-row:10;grid-column:1'>4f</span><span class='pt-r' style='grid-row:11;grid-column:1'>5f</span>";
    PT.forEach(e=>{ const q=ptPos(e.z), r=q[0]>=9?q[0]+1:q[0]+1, c=q[1]+1, b=blockOf(q[0],q[1],e.z);
      h+="<button type='button' class='pt-c' data-z='"+e.z+"' style='grid-row:"+r+";grid-column:"+c+";background:"+BG[b]+"'><i>"+e.z+"</i><b>"+e.sy+"</b></button>"; });
    return h+"</div></div>";
  }
  function ptShow(){
    const e=PT[ptSel-1], q=ptPos(e.z), b=blockOf(q[0],q[1],e.z), c=cfg(e.z), f=q[0]>=9;
    const info=document.getElementById('ptInfo'); if(!info) return;
    info.innerHTML="<div class='pt-big' style='background:"+BG[b]+"'><i>"+e.z+"</i><b>"+e.sy+"</b><small>"+e.ms+"</small></div><div class='pt-txt'><h4>"+e.nm+"</h4>"+
      "<div><b>Atomic number:</b> "+e.z+"</div><div><b>Atomic mass:</b> "+e.ms.replace(/[()]/g,'')+" u"+(e.ms[0]==='('?" (most stable isotope)":"")+"</div>"+
      "<div><b>Configuration:</b> "+c.short+"</div><div class='pt-full'>"+c.full+"</div>"+
      "<div><b>Block:</b> "+b+" · <b>Period:</b> "+(f?(q[0]===9?6:7):q[0])+(f?'':" · <b>Group:</b> "+q[1])+"</div><div><b>Aufbau fills last:</b> "+c.last+(c.exc?" <i>(exception – see configuration)</i>":"")+"</div></div>";
    document.querySelectorAll('.pt-c').forEach(x=>x.classList.toggle('sel',+x.dataset.z===ptSel));
  }
  function ptInit(){ const m=document.getElementById('ptMount'); if(!m) return; if(!ptCache) ptCache=ptBuild(); m.innerHTML=ptCache; ptShow(); }
  window.ptData={PT:PT,cfg:cfg,ORD:ORD,CAP:CAP,okey:okey,orbDiag:orbDiag};
  document.addEventListener('click',e=>{ const b=e.target.closest&&e.target.closest('.pt-c'); if(b){ ptSel=+b.dataset.z; ptShow(); } });

  function aufChart(){
    const ord=['1s','2s','2p','3s','3p','4s','3d','4p','5s','4d','5p','6s','4f','5d','6p','7s','5f','6d','7p'];
    let h="<div class='auf'><span></span>"+'spdf'.split('').map(l=>"<b>"+l+"</b>").join('');
    for(let n=1;n<=7;n++){ h+="<b>n = "+n+"</b>"; for(const l of 'spdf'){ const k=ord.indexOf(n+l); h+=k<0?"<span></span>":"<span class='au-c "+l+"'>"+n+l+"<sup>"+(k+1)+"</sup></span>"; } }
    return h+"</div><p class='ptnote'>Small numbers = filling order (1st → 19th).</p>";
  }
  function orbDiag(gs){ return "<div class='od'>"+gs.map(g=>{ if(!g[1]) return "<span class='od-chip'>"+g[0]+"</span>";
    let a=Array(g[1]).fill(0); if(Array.isArray(g[2])) a=g[2]; else for(let i=0;i<g[2];i++) a[i%g[1]]++;
    return "<div class='od-g'><div class='od-bx'>"+a.map(n=>"<span class='od-b'>"+(n===2?'↑↓':n===1?'↑':'')+"</span>").join('')+"</div><small>"+g[0]+"</small></div>"; }).join('')+"</div>"; }

  function renderRack(){
    rack.innerHTML = '';
    items.forEach(key => {
      const c = content[key] || { label: "", title: "" };
      const papers = `<div class="paper-container"><span class="paper p1"></span><span class="paper p2"></span><span class="paper p3"></span></div>`;
      const btn = document.createElement('button');
      btn.className = 'folder-btn';
      btn.innerHTML = `${papers}${atomSVG}<div class="folder-txt"><span class="wk">${c.label}</span><span class="title-text">${key === 'me' ? 'Myself' : c.title}</span></div>`;
      btn.addEventListener('click', () => openFolder(key));
      rack.appendChild(btn);
    });
  }

  // Size the book to its tallest spread so it doesn't jump when turning pages
  function fitBook(){
    const c = content[currentKey];
    if (!c) return;
    bookBody.style.removeProperty('--book-h');
    const step = isMobile() ? 1 : 2;
    const total = Math.ceil(c.pages.length / step);
    const keep = currentSpreadIdx;
    let max = 0;
    for (let i = 0; i < total; i++) {
      currentSpreadIdx = i;
      updateBookContent();
      bookBody.querySelectorAll('.notebook-page').forEach(pg => {
        if (pg.style.display !== 'none') max = Math.max(max, pg.scrollHeight);
      });
    }
    currentSpreadIdx = keep;
    updateBookContent();
    bookBody.style.setProperty('--book-h', max + 'px');
  }

  function openFolder(key){
    currentKey = key;
    currentSpreadIdx = 0;
    fitBook();
    bookOverlay.classList.add('open');
  }

  function closeFolder(){
    bookOverlay.classList.remove('open');
  }

  function isMobile() {
    return window.innerWidth <= 768;
  }

  function updateBookContent() {
    const c = content[currentKey];
    if (!c) return;
    bookTitle.textContent = c.title;

    const mobile = isMobile();
    const step = mobile ? 1 : 2;
    const totalSpreads = Math.ceil(c.pages.length / step);

    const leftIdx = currentSpreadIdx * step;
    const rightIdx = leftIdx + 1;

    leftPage.innerHTML = c.pages[leftIdx] || '';
    
    if (!mobile) {
      rightPage.parentElement.style.display = 'flex';
      rightPage.innerHTML = c.pages[rightIdx] || '';
      pageIndicator.textContent = `Spread ${currentSpreadIdx + 1} of ${totalSpreads}`;
    } else {
      rightPage.parentElement.style.display = 'none';
      pageIndicator.textContent = `Page ${currentSpreadIdx + 1} of ${c.pages.length}`;
    }
    
    prevPageBtn.disabled = currentSpreadIdx === 0;
    nextPageBtn.disabled = currentSpreadIdx >= totalSpreads - 1;
    initAtomSpin();
    ptInit();
  }

  prevPageBtn.addEventListener('click', () => {
    if (currentSpreadIdx > 0) {
      currentSpreadIdx--;
      updateBookContent();
    }
  });

  nextPageBtn.addEventListener('click', () => {
    const c = content[currentKey];
    if (!c) return;
    const step = isMobile() ? 1 : 2;
    const totalSpreads = Math.ceil(c.pages.length / step);
    if (currentSpreadIdx < totalSpreads - 1) {
      currentSpreadIdx++;
      updateBookContent();
    }
  });

  window.addEventListener('resize', () => {
    if (bookOverlay.classList.contains('open')) {
      fitBook();
    }
  });

  closeBookBtn.addEventListener('click', closeFolder);
  bookOverlay.addEventListener('click', (e) => {
    if (e.target === bookOverlay) closeFolder();
  });

  document.addEventListener('keydown', (e) => {
    if (e.key === 'Escape') closeFolder();
  });

  renderRack();
</script>


<div class="quiz-back" id="quizBack" role="dialog" aria-modal="true" aria-labelledby="quizQ"><div class="quiz-card"><div class="quiz-tag"><span id="quizKind">🦆 Quick question</span> · <span id="quizWk"></span></div><p class="quiz-q" id="quizQ"></p><div class="quiz-opts" id="quizOpts"></div><p class="quiz-fb" id="quizFb"></p><button type="button" class="quiz-next" id="quizNext" hidden>Keep swimming →</button></div></div>
<div class="duck-hud" id="duckHud" aria-live="polite"><span class="hs"></span><span class="hm"></span><button type="button" class="hb" hidden>Play again</button></div>
<div class="duck-help" id="duckHelp" hidden><div class="dh-card"><h3>🦆 How to play</h3>
<div class="dh-row dh-pc"><span><kbd>Space</kbd><kbd>↑</kbd></span><em>Jump</em></div>
<div class="dh-row dh-pc"><span><kbd>S</kbd><kbd>↓</kbd></span><em>Dive under</em></div>
<div class="dh-row dh-tc"><span class="dh-chip j">JUMP</span><em>Tap to jump</em></div>
<div class="dh-row dh-tc"><span class="dh-chip">DIVE</span><em>Tap to dive under</em></div>
<div class="dh-legend"><span>🍡 Jump a noodle → easy question</span><span>🐦 Dive under a seagull → medium</span><span>🌊 Ride a big wave → hard</span></div>
<p class="dh-go">Press any key or tap to start</p></div></div>
<div class="duck-btns" id="duckBtns"><button type="button" class="dbtn" id="btnDive" aria-label="Dive"><svg width="22" height="22" viewBox="0 0 32 32" fill="none" stroke="#fff" stroke-width="2.4" stroke-linecap="round" stroke-linejoin="round"><path d="M3 11q3.25-4 6.5 0t6.5 0 6.5 0 6.5 0"/><path d="M16 16v10m-4-4l4 4 4-4"/></svg>DIVE</button><button type="button" class="dbtn jump" id="btnJump" aria-label="Jump"><svg width="22" height="22" viewBox="0 0 32 32" fill="none" stroke="#fff" stroke-width="2.4" stroke-linecap="round" stroke-linejoin="round"><path d="M16 27V9m-6 6l6-6 6 6"/><circle cx="6" cy="24" r="1.7" fill="#fff" stroke="none"/><circle cx="26" cy="21" r="1.7" fill="#fff" stroke="none"/></svg>JUMP</button></div>
<div class="duck-strip" aria-hidden="true" role="presentation">
  <canvas id="wBack"></canvas>
  <div class="beach" id="beach"><svg viewBox="0 0 220 70" aria-hidden="true">
    <path d="M6 64C30 34 80 26 110 26S190 34 214 64Z" fill="url(#sandG)"/>
    <path d="M40 52c20-10 50-14 78-14" stroke="#fff" stroke-opacity=".4" stroke-width="3" fill="none" stroke-linecap="round"/>
    <path d="M170 36C174 26 176 18 182 8" stroke="#8a5a2b" stroke-width="4.5" fill="none" stroke-linecap="round"/>
    <g stroke="#2f8f72" stroke-width="3.4" fill="none" stroke-linecap="round"><path d="M182 8Q168 -2 152 8"/><path d="M182 8Q170 8 158 22"/><path d="M182 8Q196 -2 212 8"/><path d="M182 8Q194 8 206 22"/></g>
    <path d="M52 44V14" stroke="#8a5a2b" stroke-width="2.5" stroke-linecap="round"/>
    <path d="M30 18Q52 -2 74 18Z" fill="#ff7f96"/><path d="M41 18Q52 4 52 18ZM52 18Q52 4 63 18Z" fill="#fff" fill-opacity=".55"/>
    <g class="zz" font-family="Georgia,serif" font-weight="700" fill="#5b7a8a"><text x="130" y="-2" font-size="11">z</text><text x="140" y="-12" font-size="14">z</text></g>
  </svg></div>
  <div class="duck" id="duck">
    <svg viewBox="0 0 34 30" xmlns="http://www.w3.org/2000/svg">
      <path d="M3 17c0-5 4-8 9-8h7c5 0 9 3 9 8 0 5-5 9-11 9h-3C7 26 3 22 3 17z" fill="#FFD23F"/>
      <path d="M5 15c-2-2-3-4-2-5 2 0 3 1 4 3z" fill="#FFD23F"/>
      <circle cx="23" cy="9" r="6.5" fill="#FFD23F"/>
      <path d="M28 8.5c3 0 5 1 5 2.2s-2 2.2-5 2.2z" fill="#F08A24"/>
      <circle cx="24.6" cy="7.6" r="1.25" fill="#2a2a2a"/>
      <circle cx="25" cy="7.2" r=".4" fill="#fff"/>
      <circle cx="21.2" cy="11" r="1.5" fill="#FF9AA8" opacity=".6"/>
      <path d="M10 15c2-2 8-2 10 1-1 4-8 5-10-1z" fill="#F2B824"/>
    </svg>
  </div>
  <canvas id="wFront"></canvas>
</div>
<script>
(function(){
  const strip=document.querySelector('.duck-strip');
  const duck=document.getElementById('duck');
  const cvB=document.getElementById('wBack'), cvF=document.getElementById('wFront');
  const cB=cvB.getContext('2d'), cF=cvF.getContext('2d');
  const H=96, BASE=17, DW=34, GAP_MIN=270, VW=850, A=36;
  let V=105;
  const PAL=['#ef7fa0','#f2b544','#5cc2a7','#8d8be0','#ee8a5a','#6bb6ea'];
  const rnd=(a,b)=>a+Math.random()*(b-a);
  const pick=a=>a[Math.floor(Math.random()*a.length)];

  let W=0, dpr=1, duckX=0, t=0, last=0;
  let noodles=[], spawnX=0;
  let gulls=[], gullT=4, duckT=0, duckHold=false, autoDuck=false;
  let y=0, vy=0, g=0, airborne=false, squash=0;
  let wst='idle', crestX=-999, wAmp=0, waveTimer=6+Math.random()*4;
  let duckPosX=0, carryOff=0, carryT=0, carryLift=0, crashT=0, retP=0, retFrom=0;
  let cA=[143,211,223], cBc=[74,159,182], colT=0;
  let mode='review', score=0, over=false, overT=0, quizOpen=false, pendingQ=false, qOk=0, qAsked=0, hardPending=false, beachT=0;
  let dvT=0, dSp=false, helpOpen=false, helpSeen=false, diveK=0, wasDive=false, parts=[];

  /* ---------- water ---------- */
  const LY=[{amp:3.2,wl:120,s:.6,ph:0},{amp:2.6,wl:70,s:-.9,ph:1.7},{amp:1.8,wl:44,s:1.3,ph:3.1}];
  const wv=(L,x)=>L.amp*Math.sin(x*6.2832/L.wl + t*L.s + L.ph);
  const off=x=>wv(LY[0],x)+wv(LY[1],x);
  function bump(x){
    if(wAmp<.01) return 0;
    const dx=x-crestX;   // gentle back slope, steep front face, small trough ahead of the swell
    return wAmp*((dx>0?Math.exp(-(dx*dx)/900):Math.exp(-(dx*dx)/9000))-.2*Math.exp(-((dx-40)*(dx-40))/500));
  }
  function splash(x,n,pw){ for(let i=0;i<n&&parts.length<140;i++) parts.push({x:x+rnd(-9,9),y:H-BASE-off(x)-2,vx:rnd(-55,55)*pw,vy:rnd(70,150)*pw,life:1,r:rnd(1,2.4)}); }
  const SEA=[{x:.04,k:0,c:'#ff7f96',s:16,p:.5},{x:.16,k:1,c:'#f2b544',s:13,p:.5},{x:.28,k:2,c:'#ffb86b',y:22,p:1.6},{x:.4,k:0,c:'#b98be0',s:12,p:.5},{x:.52,k:3,c:'#ee8a5a',s:6,p:.5},{x:.63,k:1,c:'#5cc2a7',s:15,p:.5},{x:.74,k:2,c:'#6bb6ea',y:30,p:1.2},{x:.86,k:0,c:'#ef7fa0',s:18,p:.5},{x:.95,k:4,c:'#fff',p:0}];
  function drawSea(c,k){
    c.save(); c.globalAlpha=k; c.lineCap='round';
    for(const o of SEA){
      const L=W+80, x=(((o.x*L-t*30*o.p)%L)+L)%L-40, b=H-3;
      c.fillStyle=c.strokeStyle=o.c;
      if(o.k===0){ c.lineWidth=3; for(let i=-1;i<=1;i++){ c.beginPath(); c.moveTo(x,b); c.quadraticCurveTo(x+i*o.s*.4,b-o.s*.6,x+i*o.s*.7,b-o.s); c.stroke(); c.beginPath(); c.arc(x+i*o.s*.7,b-o.s,2,0,6.3); c.fill(); } }
      else if(o.k===1){ c.globalAlpha=k*.8; c.beginPath(); c.arc(x,b,o.s,Math.PI,0); c.fill(); c.globalAlpha=k; }
      else if(o.k===2){ const fy=H-o.y+Math.sin(t*2+o.x*9)*3; c.beginPath(); c.ellipse(x,fy,7,4,0,0,6.3); c.fill(); c.beginPath(); c.moveTo(x+6,fy); c.lineTo(x+12,fy-4); c.lineTo(x+12,fy+4); c.fill(); }
      else if(o.k===3){ c.beginPath(); for(let i=0;i<10;i++){ const r=i%2?2.4:o.s, a=i*.6283-1.57; c.lineTo(x+Math.cos(a)*r,b-4+Math.sin(a)*r); } c.fill(); }
      else { c.lineWidth=1; for(let i=0;i<5;i++){ const by=((H-t*14*(1+i*.2)-i*20)%H+H)%H; c.globalAlpha=k*.6; c.beginPath(); c.arc(W*(.1+i*.2)+Math.sin(t+i)*4,by,1.5+i%2,0,6.3); c.stroke(); } }
    }
    c.restore();
  }
  const hex=h=>{h=h.trim().replace('#','');if(h.length===3)h=h.replace(/./g,'$&$&');return [0,2,4].map(i=>parseInt(h.substr(i,2),16));};
  const rgba=(c,a)=>'rgba('+c[0]+','+c[1]+','+c[2]+','+a+')';
  function fillLayer(ctx,fy,c1,c2){
    ctx.beginPath(); ctx.moveTo(0,H);
    for(let x=0;x<=W+4;x+=4) ctx.lineTo(x,fy(x));
    ctx.lineTo(W,H); ctx.closePath();
    const gr=ctx.createLinearGradient(0,H-BASE-44,0,H);
    gr.addColorStop(0,c1); gr.addColorStop(1,c2);
    ctx.fillStyle=gr; ctx.fill();
  }
  function drawWater(){
    cB.clearRect(0,0,W,H); cF.clearRect(0,0,W,H);
    const y0=x=>H-BASE-wv(LY[0],x)-.9*bump(x-14);
    const y1=x=>H-BASE-wv(LY[1],x)-wv(LY[0],x)*.4-bump(x);
    fillLayer(cB,y0,rgba(cA,.5),rgba(cBc,.65));
    fillLayer(cB,y1,rgba(cA,.72),rgba(cBc,.95));
    cB.beginPath();
    for(let x=0;x<=W+4;x+=4){ const yy=y1(x); x?cB.lineTo(x,yy):cB.moveTo(x,yy); }
    cB.strokeStyle='rgba(255,255,255,.3)'; cB.lineWidth=1.2; cB.stroke();
    if(diveK>.02) drawSea(cB,diveK);
    if(wAmp>2){
      const k=Math.min(1,wAmp/A), th=x=>1.5+5*k*Math.exp(-Math.pow((x-crestX)/26,2));
      cB.beginPath();
      for(let x=crestX-60;x<=crestX+26;x+=3){ const yy=y1(x)-th(x); x===crestX-60?cB.moveTo(x,yy):cB.lineTo(x,yy); }
      for(let x=crestX+26;x>=crestX-60;x-=3) cB.lineTo(x,y1(x)+2);
      cB.closePath(); cB.fillStyle='rgba(255,255,255,'+(.6*k)+')'; cB.fill();
      cB.beginPath();
      for(let x=crestX-60;x<=crestX+26;x+=3){ const yy=y1(x)-th(x); x===crestX-60?cB.moveTo(x,yy):cB.lineTo(x,yy); }
      cB.strokeStyle='rgba(255,255,255,'+(.9*k)+')'; cB.lineWidth=2; cB.lineCap='round'; cB.stroke();
    }
    fillLayer(cF,x=>H-9-wv(LY[2],x),rgba(cA,.3),rgba(cBc,.5));
    if(diveK>.02) fillLayer(cF,y1,rgba(cA,.5*diveK),rgba(cBc,.62*diveK));   // tint starts exactly at the visible waterline
    for(const p of parts){ cF.beginPath(); cF.arc(p.x,p.y,p.r,0,6.3); cF.fillStyle='rgba(255,255,255,'+(.85*p.life)+')'; cF.fill(); }
  }

  /* ---------- noodles ---------- */
  function makeNoodle(){
    const col=pick(PAL), col2=pick(PAL), r=Math.random();
    const hi='rgba(255,255,255,.4)', sh='rgba(0,0,0,.13)';
    let w,h,body;
    if(r<.34){ // straight, varied thickness + length
      const th=rnd(9,22); w=Math.max(rnd(30,70),th+10); h=th;
      body='<line x1="'+th/2+'" y1="'+th/2+'" x2="'+(w-th/2)+'" y2="'+th/2+'" stroke="'+col+'" stroke-width="'+th+'" stroke-linecap="round"/>'+
           '<line x1="'+(th/2+2)+'" y1="'+th*.3+'" x2="'+(w-th/2-2)+'" y2="'+th*.3+'" stroke="'+hi+'" stroke-width="'+th*.22+'" stroke-linecap="round"/>'+
           '<line x1="'+(th/2+2)+'" y1="'+th*.78+'" x2="'+(w-th/2-2)+'" y2="'+th*.78+'" stroke="'+sh+'" stroke-width="'+th*.2+'" stroke-linecap="round"/>';
    } else if(r<.54){ // arch
      const th=rnd(9,13); w=rnd(44,70); h=rnd(22,30);
      const d='M '+th/2+' '+(h-th/2)+' Q '+w/2+' '+(1.5*th-h)+' '+(w-th/2)+' '+(h-th/2);
      body='<path d="'+d+'" fill="none" stroke="'+col+'" stroke-width="'+th+'" stroke-linecap="round"/>'+
           '<path d="'+d+'" fill="none" stroke="'+hi+'" stroke-width="'+th*.22+'" stroke-linecap="round" transform="translate(0,'+(-th*.2)+')"/>';
    } else if(r<.69){ // ring
      const d=rnd(24,32), th=rnd(8,11), rr=(d-th)/2, c=6.2832*rr; w=d; h=d;
      body='<circle cx="'+d/2+'" cy="'+d/2+'" r="'+rr+'" fill="none" stroke="'+col+'" stroke-width="'+th+'"/>'+
           '<circle cx="'+d/2+'" cy="'+d/2+'" r="'+rr+'" fill="none" stroke="'+hi+'" stroke-width="'+th*.22+'" stroke-linecap="round" stroke-dasharray="'+c*.22+' '+c+'" transform="rotate(-125 '+d/2+' '+d/2+')"/>';
    } else if(r<.84){ // ramp / S-curve
      const th=rnd(9,11); w=rnd(56,78); h=rnd(24,30);
      const d='M '+th/2+' '+(h-th/2)+' C '+w*.32+' '+(h-th/2)+' '+w*.32+' '+th/2+' '+w*.6+' '+th/2+' L '+(w-th/2)+' '+th/2;
      body='<path d="'+d+'" fill="none" stroke="'+col+'" stroke-width="'+th+'" stroke-linecap="round"/>'+
           '<path d="'+d+'" fill="none" stroke="'+hi+'" stroke-width="'+th*.22+'" stroke-linecap="round" transform="translate(0,'+(-th*.2)+')"/>';
    } else { // stacked pair
      const th=rnd(9,12); w=rnd(38,60); h=2*th-3;
      const tw=w*.7, tx=(w-tw)/2;
      body='<line x1="'+th/2+'" y1="'+(h-th/2)+'" x2="'+(w-th/2)+'" y2="'+(h-th/2)+'" stroke="'+col+'" stroke-width="'+th+'" stroke-linecap="round"/>'+
           '<line x1="'+(tx+th/2)+'" y1="'+th/2+'" x2="'+(tx+tw-th/2)+'" y2="'+th/2+'" stroke="'+col2+'" stroke-width="'+th+'" stroke-linecap="round"/>'+
           '<line x1="'+(tx+th/2+2)+'" y1="'+th*.3+'" x2="'+(tx+tw-th/2-2)+'" y2="'+th*.3+'" stroke="'+hi+'" stroke-width="'+th*.22+'" stroke-linecap="round"/>';
    }
    return {w:Math.round(w),h:Math.round(h),svg:'<svg width="'+w+'" height="'+h+'" viewBox="0 0 '+w+' '+h+'" xmlns="http://www.w3.org/2000/svg">'+body+'</svg>'};
  }
  function spawn(){
    const n=makeNoodle();
    const el=document.createElement('div');
    el.className='noodle'; el.innerHTML=n.svg;
    strip.insertBefore(el,duck);
    const x=Math.max(spawnX,W+20);
    noodles.push({el,x,w:n.w,h:n.h,done:false,dead:false,gone:false});
    spawnX=x+n.w+(mode==='play'?430+Math.random()*250:GAP_MIN+Math.random()*180);
  }
  function washAway(){
    for(const n of noodles){
      if(n.dead) continue;
      n.dead=true; n.el.style.transition='opacity .6s ease'; n.el.style.opacity='0';
      setTimeout(()=>{n.gone=true;},650);
    }
    for(const g of gulls){
      if(g.dead) continue;
      g.dead=true; g.el.style.transition='opacity .6s ease'; g.el.style.opacity='0';
      setTimeout(()=>{g.gone=true;},650);
    }
  }

  /* ---------- seagulls (duck under them: S / ArrowDown, or swipe down) ---------- */
  const GULL_SVG='<svg width="46" height="32" viewBox="0 0 46 32" xmlns="http://www.w3.org/2000/svg">'+
    '<path d="M34 19L45 15L44 22Z" fill="#e9eef2" stroke="#b4bec8" stroke-width=".7"/>'+
    '<ellipse cx="24" cy="20" rx="12" ry="5.2" fill="#fff" stroke="#b4bec8" stroke-width=".8"/>'+
    '<path d="M14 22Q24 27 35 22Q24 25 14 22Z" fill="#dfe6ec"/>'+
    '<circle cx="11" cy="17" r="5" fill="#fff" stroke="#b4bec8" stroke-width=".8"/>'+
    '<path d="M6.6 16.4L0.6 18.2L6.8 19.6Z" fill="#F5A623"/>'+
    '<circle cx="9.6" cy="15.8" r="1" fill="#222"/>'+
    '<g class="wing"><path d="M20 18Q24 3 40 2Q31 9 30 19Z" fill="#f4f7fa" stroke="#9aa7b4" stroke-width="1" stroke-linejoin="round"/>'+
    '<path d="M40 2Q35 4 33 8" stroke="#3d4a57" stroke-width="2.2" fill="none" stroke-linecap="round"/></g></svg>';
  function spawnGull(){
    const el=document.createElement('div'); el.className='gull'; el.innerHTML=GULL_SVG;
    strip.insertBefore(el,duck);
    gulls.push({el,x:W+30,w:46,ph:Math.random()*6,scored:false,dead:false,gone:false});
  }
  function canSpawnGull(){
    if(gulls.some(g=>!g.dead&&g.x>W*.5)) return false;
    const Vn=Math.max(V,60), tg=(W+30-duckX)/(Vn+45);
    for(const n of noodles){ if(n.dead) continue; if(Math.abs((n.x+n.w/2-duckX)/Vn-tg)<1.5) return false; }
    if(Math.abs((spawnX-duckX)/Vn-tg)<1.5) return false;
    return true;
  }
  function ducking(){
    if(wst!=='idle'||airborne||over||mode==='beach') return false;
    return mode==='play' ? (duckHold||duckT>0||gulls.some(g=>g.safe&&!g.dead&&g.x<duckX+DW+20&&g.x+g.w>duckX-6)) : autoDuck;
  }

  /* ---------- main loop ---------- */
  const ease=p=>p<.5?2*p*p:1-Math.pow(-2*p+2,2)/2;
  function frame(now){
    const dt=Math.min((now-last)/1000||0,.05); last=now; t+=dt*1.9;
    V = mode==='beach' ? 0 : mode==='play' ? ((over||quizOpen||helpOpen)?0:Math.min(180,138+score*2)) : 150;
    if(over) overT+=dt;
    if(mode==='beach') beachT+=dt;
    if(++colT>40){ colT=0; const cs=getComputedStyle(strip); cA=hex(cs.getPropertyValue('--water-a')); cBc=hex(cs.getPropertyValue('--water-b')); }

    /* tidal wave state machine */
    if(wst==='idle'){
      if(!helpOpen&&!quizOpen&&!over) waveTimer-=dt;
      if(waveTimer<=0 && !airborne && !gulls.some(g=>!g.dead&&g.x<W)){
        if(mode==='review'){ if(Math.random()<.5){ wst='rise'; crestX=-140; wAmp=0; } else waveTimer=7+Math.random()*7; }
        else if(mode==='play'&&hDeck.length&&!pendingQ){ startWave(); waveTimer=rnd(8,13); }
        else if(mode==='play') waveTimer=4;
      }
    }
    if(wst==='rise'||wst==='carry'||wst==='crash'){
      crestX+=VW*dt;
      const target=wst==='crash'?0:A;
      wAmp+=(target-wAmp)*Math.min(1,dt*(wst==='crash'?4:5));
    }
    if(wst==='rise' && crestX>=duckX-10){ wst='carry'; carryOff=duckX-crestX; carryT=0; }
    if(wst==='carry'){
      carryOff*=Math.exp(-dt*8); carryT+=dt;
      duckPosX=crestX+carryOff+6;
      if(duckPosX>=W-70){ duckPosX=W-70; wst='crash'; crashT=0; washAway(); }
    } else if(wst==='crash'){
      crashT+=dt; carryLift*=Math.exp(-dt*5);
      if(crashT>1.1){ wst='return'; retP=0; retFrom=duckPosX; wAmp=0; crestX=-999; }
    } else if(wst==='return'){
      retP+=dt/1.7;
      if(retP>=1){ wst='idle'; duckPosX=duckX; waveTimer=mode==='play'?rnd(8,13):10+Math.random()*8; spawnX=W+80; if(hardPending){ hardPending=false; openQuiz('h'); } }
      else duckPosX=retFrom+(duckX-retFrom)*ease(retP);
    } else { duckPosX=duckX; }

    /* noodles */
    const calm=(wst==='idle');
    if(calm && mode!=='beach'){ spawnX-=V*dt; if(spawnX<W+10) spawn(); }
    const cx=duckX+DW/2;
    for(const n of noodles){
      n.x-=V*dt;
      const mid=n.x+n.w/2;
      n.el.style.transform='translate('+n.x.toFixed(1)+'px,'+(-(off(mid)*.9+bump(mid)*.1)).toFixed(2)+'px)';
      if(mode==='play' && !over && wst==='idle'){
        if(n.x+6<duckX+DW-8 && n.x+n.w-6>duckX+10 && y<n.h*.7) endGame();
        else if(!n.scored && n.x+n.w<duckX+8){ n.scored=true; score++; if(pendingQ!=='gull') pendingQ='noodle'; paint(); }
      }
      if(mode==='review' && calm && !airborne && !n.done && !n.dead && n.x>duckX){
        const T=(n.w+DW+18)/V, apex=n.h+9;
        if(mid-cx<=V*T/2){ n.done=true; airborne=true; g=8*apex/(T*T); vy=4*apex/T; splash(duckX+DW/2,7,.7); }
      }
    }
    noodles=noodles.filter(n=>{ if(n.gone||n.x+n.w<-20){n.el.remove();return false;} return true; });

    /* seagulls */
    const Vg=V>0?V+45:0;
    if(!airborne) duckT=Math.max(0,duckT-dt);
    if(mode==='play'&&duckHold&&!airborne&&!quizOpen&&!helpOpen) duckT=Math.max(duckT,.2);
    autoDuck=false;
    if(mode==='review') for(const g of gulls){ if(!g.dead && g.x<duckX+DW+Vg*.32 && g.x+g.w>duckX-4) autoDuck=true; }
    if(mode!=='beach' && calm && !over && !quizOpen){
      gullT-=dt;
      if(gullT<=0){ if(canSpawnGull()){ spawnGull(); gullT=mode==='play'?rnd(4.5,7.5):rnd(11,18); } else gullT=.4; }
    }
    for(const g of gulls){
      g.x-=Vg*dt;
      g.el.style.transform='translate('+g.x.toFixed(1)+'px,'+(Math.sin(t*2.2+g.ph)*2.5).toFixed(2)+'px)';
      if(mode==='play' && !over && wst==='idle' && !g.dead){
        if(g.x+8<duckX+DW-6 && g.x+g.w-8>duckX+8 && y<41 && !g.safe && !ducking()) endGame();
        else if(!g.scored && g.x+g.w<duckX+8){ g.scored=true; score++; pendingQ='gull'; paint(); }
      }
    }
    gulls=gulls.filter(g=>{ if(g.gone||g.x+g.w<-30){ g.el.remove(); return false; } return true; });

    /* duck jump */
    if(airborne){ vy-=g*dt; y+=vy*dt; if(y<=0){ y=0; vy=0; airborne=false; squash=1; splash(duckX+DW/2,11,1); } }
    squash=Math.max(0,squash-dt*5);
    if(mode==='play' && pendingQ && !airborne && !over && !quizOpen && wst==='idle') afterClear();
    let sx=1, sy=1, rot=0, flip=1, lift=0;
    if(airborne){ const k=Math.min(1,Math.abs(vy)/60); sx=1-.1*k; sy=1+.14*k; rot=-Math.max(-14,Math.min(14,vy*.16)); }
    else{ sx=1+.16*squash; sy=1-.2*squash+Math.sin(t*3)*.012; }
    const dn=ducking(); dvT=dn?dvT+dt:0;
    const tgt=(dn&&dvT>.12)?1:0; diveK+=(tgt-diveK)*Math.min(1,dt*(tgt?9:4.5));
    if(tgt&&!dSp){ splash(duckX+DW/2,10,.8); dSp=true; } if(!dn) dSp=false;
    let dx=0;
    if(dn&&dvT<.2){ lift+=10*Math.sin(Math.PI*dvT/.2); rot=-10; }   // small hop before the plunge
    if(diveK>.02){ const em=tgt?0:Math.sin(Math.PI*(1-diveK));       // em>0 only while surfacing
      sx=1+.08*diveK; sy=1-.1*diveK; rot=tgt?14*diveK:-18*em; lift+=-26*diveK+4*em; dx=tgt?0:14*em; }
    if(wst==='carry'){ const e=Math.min(1,carryT*4); carryLift=(32+.2*bump(duckPosX))*e; lift=carryLift; rot=7*e; }
    else if(wst==='crash'){ lift=carryLift; rot=7*carryLift/40; }
    else if(wst==='return'){ flip=-1; rot=Math.sin(t*3)*2; }
    if(mode==='beach'){ const k=Math.min(1,beachT/1.1), e=1-Math.pow(1-k,3); lift=25*e; rot=-8*(1-e); if(k>=1){ sx=1.08; sy=.8+Math.sin(t*2)*.02; rot=0; } }
    if(over){ rot=-28; lift=-3; }
    const bob=mode==='beach'?0:off(duckPosX+DW/2)*.8;
    duck.style.transform='translate('+(duckPosX-duckX+dx).toFixed(1)+'px,'+(-(y+lift+bob)).toFixed(2)+'px) rotate('+rot.toFixed(1)+'deg) scale('+(sx*flip).toFixed(3)+','+sy.toFixed(3)+')';

    if((wst==='rise'||wst==='carry')&&wAmp>8) for(let i=0;i<2;i++) parts.push({x:crestX+rnd(-6,14),y:H-BASE-wAmp-off(crestX),vx:rnd(30,90),vy:rnd(40,110),life:1,r:rnd(1,2.2)});
    for(const q of parts){ q.vy-=380*dt; q.x+=q.vx*dt; q.y-=q.vy*dt; q.life-=dt*1.5; }
    parts=parts.filter(q=>q.life>0&&q.y<H-BASE+6);
    drawWater();
    requestAnimationFrame(frame);
  }
  function resize(){
    W=strip.clientWidth; dpr=Math.min(window.devicePixelRatio||1,2);
    for(const c of [cvB,cvF]){ c.width=Math.round(W*dpr); c.height=Math.round(H*dpr); }
    cB.setTransform(dpr,0,0,dpr,0,0); cF.setTransform(dpr,0,0,dpr,0,0);
    duckX=duck.offsetLeft; if(wst==='idle') duckPosX=duckX;
    if(typeof beachEl!=='undefined'&&beachEl.classList.contains('on')) beachEl.style.left=(duckX+DW/2-80)+'px';
    if(!noodles.length) spawnX=W+40;
  }
  /* ---------- game mode (Review = duck plays itself, Play = you jump) ---------- */
  const hud=document.getElementById('duckHud'), hs=hud.querySelector('.hs'), hm=hud.querySelector('.hm'), hb=hud.querySelector('.hb'), beachEl=document.getElementById('beach');
  let best=0; try{ best=+localStorage.getItem('duckBest')||0; }catch(e){}
  function paint(msg){ hs.textContent='Score '+score+' · Best '+best+' · ✔ '+qOk+' · Q '+(QN-eDeck.length-mDeck.length-hDeck.length)+'/'+QN; if(msg!==undefined) hm.textContent=msg; }
  function reset(){
    noodles.forEach(n=>n.el.remove()); noodles=[];
    gulls.forEach(g=>g.el.remove()); gulls=[]; duckT=0; duckHold=false; gullT=mode==='play'?rnd(3.5,5.5):rnd(8,14);
    wst='idle'; wAmp=0; crestX=-999; carryLift=0; duckPosX=duckX;
    airborne=false; y=0; vy=0; score=0; over=false; overT=0; pendingQ=false; hardPending=false; closeQuiz(); spawnX=W+40; waveTimer=8+Math.random()*6;
  }
  function setMode(m){
    mode=m==='review'?'beach':m; beachT=0; reset(); beachEl.classList.remove('on','b2'); hb.hidden=true; if(m==='review') showBeach(false); if(m==='play') newRun();
    strip.classList.toggle('playing',m==='play');
    hud.classList.toggle('on',m==='play');
    if(m==='play') paint(matchMedia('(pointer:coarse)').matches?'JUMP noodles · DIVE under seagulls':'Space / ↑ jump · S / ↓ dive');
    btns.classList.toggle('on',m==='play'); if(m==='play'&&!helpSeen) openHelp(); else closeHelp();
  }
  const btns=document.getElementById('duckBtns'), helpEl=document.getElementById('duckHelp');
  function openHelp(){ helpOpen=true; helpEl.hidden=false; }
  function closeHelp(){ if(helpOpen) helpSeen=true; helpOpen=false; helpEl.hidden=true; }
  helpEl.addEventListener('pointerdown',e=>{ e.preventDefault(); closeHelp(); });
  function showBeach(v2){ beachEl.style.left=(duckX+DW/2-80)+'px'; beachEl.classList.toggle('b2',!!v2); beachEl.classList.add('on'); }
  function endGame(){
    over=true; overT=0;
    if(score>best){ best=score; try{ localStorage.setItem('duckBest',best); }catch(e){} }
    paint('Splash! Tap or press Space to retry');
  }
  function act(){
    if(mode!=='play'||quizOpen) return;
    if(helpOpen){ closeHelp(); return; }
    if(over){ if(overT>.5){ reset(); paint(''); } return; }
    if(!airborne){ airborne=true; duckT=0; g=520; vy=230; hm.textContent=''; splash(duckX+DW/2,8,.8); }
  }
  function duckDown(sec,touch){
    if(mode!=='play'||quizOpen||over||helpOpen) return;
    duckT=sec||.85;
    if(touch){ const gl=gulls.filter(g=>!g.dead&&g.x+g.w>duckX&&g.x<duckX+DW+520).sort((a,b)=>a.x-b.x)[0]; if(gl) gl.safe=true; }   // touch dive locks onto the next seagull
    if(airborne) vy=Math.min(vy,-260);   // fast-fall so you can duck mid-jump
  }
  let pStart=null;
  strip.addEventListener('pointerdown',e=>{
    e.preventDefault();
    if(mode!=='play') return;
    if(e.pointerType==='mouse'){ act(); return; }
    pStart={id:e.pointerId,x:e.clientX,y:e.clientY,swiped:false};
    try{ strip.setPointerCapture(e.pointerId); }catch(_){}
  });
  strip.addEventListener('pointermove',e=>{
    if(!pStart||e.pointerId!==pStart.id||pStart.swiped) return;
    const dy=e.clientY-pStart.y, dx=e.clientX-pStart.x;
    if(dy>16 && dy>Math.abs(dx)){ pStart.swiped=true; duckDown(0,true); }
  });
  const endP=e=>{
    if(!pStart||e.pointerId!==pStart.id) return;
    const sw=pStart.swiped; pStart=null;
    if(!sw && e.type==='pointerup') act();
  };
  strip.addEventListener('pointerup',endP);
  strip.addEventListener('pointercancel',endP);
  const isJump=e=>e.code==='Space'||e.key==='ArrowUp';
  const isDown=e=>e.code==='KeyS'||e.key==='ArrowDown'||e.key==='s'||e.key==='S';
  addEventListener('keydown',e=>{
    if(mode!=='play'||quizOpen||!(isJump(e)||isDown(e))) return;
    if(/^(A|INPUT|TEXTAREA|SELECT)$/.test(e.target.tagName)||e.target.closest('#islandMenu')) return;
    if(document.getElementById('bookOverlay').classList.contains('open')) return;
    e.preventDefault(); if(e.repeat) return;
    if(e.target.tagName==='BUTTON') e.target.blur();   // a focused button no longer swallows the hotkeys
    if(helpOpen){ closeHelp(); return; }
    if(isDown(e)){ duckHold=true; duckDown(); } else act();
  });
  addEventListener('keyup',e=>{ if(isDown(e)) duckHold=false; });
  addEventListener('blur',()=>{ duckHold=false; });
  const bj=document.getElementById('btnJump'), bd=document.getElementById('btnDive');
  bj.addEventListener('pointerdown',e=>{ e.preventDefault(); act(); });
  bd.addEventListener('pointerdown',e=>{ e.preventDefault(); if(helpOpen){ closeHelp(); return; } duckHold=true; duckDown(0,e.pointerType!=='mouse'); });
  ['pointerup','pointercancel','pointerleave'].forEach(v=>bd.addEventListener(v,()=>{ duckHold=false; }));
  /* ---------- quiz: one question after every noodle you clear ----------
     Add more rows any time: [week number, question, CORRECT answer, wrong, wrong, wrong] */
  const QM=[
    [1,"Who proposed that electrons can behave like waves?","Louis de Broglie","Isaac Newton","Marie Curie","Thomas Edison"],
    [1,"Which principle says we can't know an electron's position and momentum at the same time?","Heisenberg Uncertainty Principle","Newton's First Law","Archimedes' Principle","Boyle's Law"],
    [1,"Who developed the famous wave equation for electrons?","Erwin Schrödinger","Louis de Broglie","Werner Heisenberg","Galileo Galilei"],
    [1,"Wave-particle duality means electrons can act like…","both waves and particles","only rocks","only liquids","only light bulbs"],
    [1,"The Schrödinger model tells us the ______ of finding an electron.","probability","color","weight","name"],
    [1,"What sits at the center of an atom?","The nucleus","The electron cloud","A shell","An orbital"],
    [1,"Which order is correct?","Energy level → Subshell → Orbital","Orbital → Subshell → Energy level","Subshell → Energy level → Orbital","Orbital → Energy level → Subshell"],
    [1,"What is the most electrons one orbital can hold?","2","1","4","8"],
    [1,"How many energy levels (periods) have been discovered?","7","3","10","4"],
    [1,"Which formula gives the maximum electrons in a shell?","2n²","n + 2","n³","4n"],
    [1,"Which shell is closest to the nucleus?","K","Q","M","P"],
    [1,"What is the maximum number of electrons in shell n = 2 (the L shell)?","8","2","18","32"],
    [1,"What does the principal quantum number (n) tell you?","The energy level (shell)","The color of the atom","The atom's name","The number of neutrons"],
    [1,"How many sublevels (subshells) are there?","4","2","7","10"],
    [1,"What does the letter “s” stand for in sublevels?","sharp","simple","small","solid"],
    [1,"What does the letter “d” stand for?","diffuse","dense","dark","double"],
    [1,"What is the shape of an s orbital?","Spherical","Peanut / dumbbell","Clover leaf","Flower"],
    [1,"Which orbital has a peanut / dumbbell shape?","p","s","d","f"],
    [1,"Which orbital looks like a clover leaf?","d","s","p","f"],
    [1,"The f orbital looks like a…","flower","sphere","triangle","star"],
    [1,"How many electrons can the p sublevel hold in total?","6","2","10","14"],
    [1,"An orbital is a region where the chance of finding an electron is…","highest","zero","always 50%","never known"],
    [1,"How many orbitals does the d sublevel have?","5","3","7","1"],
    [1,"How many electrons can the d sublevel hold in total?","10","6","14","2"],
    [1,"How many electrons can the f sublevel hold in total?","14","10","6","7"],
    [1,"Which shell is the third energy level?","M","L","N","K"],
    [1,"Which model pictures electrons as a cloud of probability?","Quantum (Schrödinger) model","Plum pudding model","Solar-system model","Dalton's ball model"],
    [1,"Which sublevel is shaped like a clover leaf?","d","s","p","f"]
  ];
  const QE=[
    [1,"Which tiny particle has a negative charge?","Electron","Proton","Neutron","Nucleus"],
    [1,"Protons have a ______ charge.","positive","negative","neutral","rainbow"],
    [1,"Neutrons have ______ charge.","no (neutral)","positive","negative","double"],
    [1,"Where are electrons found in an atom?","Outside the nucleus","Inside a neutron","Inside a proton","Nowhere"],
    [1,"Which orbital is round like a ball?","s","p","d","f"],
    [1,"Which shell is the closest to the nucleus?","K","M","P","Q"],
    [1,"The K shell holds at most how many electrons?","2","8","18","1"],
    [1,"An atom is made of protons, neutrons and…","electrons","cells","crystals","molecules"],
    [1,"How many orbitals does the s sublevel have?","1","3","5","7"],
    [1,"How many orbitals does the p sublevel have?","3","1","5","7"],
    [1,"How many electrons can the s sublevel hold?","2","6","10","14"],
    [1,"What does the letter “f” stand for in sublevels?","fundamental","fast","flat","fluid"],
    [1,"An orbital can hold at most ___ electrons.","2","1","6","10"],
    [1,"The nucleus is at the ______ of the atom.","center","edge","top","bottom"]
  ];
  const QJ=[['Fun','Why did the duck swim across the sea?','To get to the other side!','To find the world\'s best bread','Because the tide told it a joke','To win the quack-athlon']];
  const QH=[
    [1,"What is the maximum number of electrons in the N shell (n = 4)?","32","16","18","8"],
    [1,"What is the maximum number of electrons in the M shell (n = 3)?","18","9","8","32"],
    [1,"How many orbitals does the f sublevel have?","7","5","3","14"],
    [1,"Which sublevel has 5 orbitals?","d","p","s","f"],
    [1,"How many electrons can the s and p sublevels hold together?","8","6","2","10"],
    [1,"Which match is correct?","f – fundamental – flower","d – sharp – spherical","p – diffuse – clover leaf","s – principal – dumbbell"],
    [1,"Which idea explains why electrons don't travel in simple fixed paths?","Heisenberg Uncertainty Principle","Newton's Laws of Motion","Boyle's Law","Law of Gravity"],
    [1,"Using 2n², how many electrons can the P shell (n = 6) hold?","72","36","12","98"],
    [1,"In the M shell (s, p and d sublevels), how many orbitals are there in total?","9","3","5","18"],
    [1,"Which scientist introduced electron orbitals and finalized the modern quantum model?","Erwin Schrödinger","Louis de Broglie","Werner Heisenberg","Niels Bohr"],
    [1,"Using 2n², how many electrons can the O shell (n = 5) hold?","50","25","32","18"],
    [1,"How many sublevels does the N shell (n = 4) have?","4","3","2","5"],
    [1,"How many orbitals are in the N shell (n = 4) in total?","16","9","7","32"],
    [1,"How many electrons can the p and d sublevels hold together?","16","8","12","20"],
    [1,"Which sublevels can the L shell (n = 2) have?","s and p","p and d","s and d","d and f"]
  ];
  const qEl=document.getElementById('quizBack'), qWk=document.getElementById('quizWk'), qQ=document.getElementById('quizQ'),
        qOpts=document.getElementById('quizOpts'), qFb=document.getElementById('quizFb'), qNext=document.getElementById('quizNext');
  const qKind=document.getElementById('quizKind'), qCard=qEl.firstElementChild;
  let jokeOn=false, bE=QE, bM=QM, bH=QH, eDeck=[], mDeck=[], hDeck=[], QN=0;
  const RUN_E=16, RUN_M=14, RUN_H=20;   // 50 questions per run   // questions per run (keeps it from feeling like too many)
  const SUPD='⁰¹²³⁴⁵⁶⁷⁸⁹', plain=h=>h.replace(/<sup>(\d+)<\/sup>/g,(m,n)=>[...n].map(d=>SUPD[d]).join(''));
  function elemQ(z){   // "full electron configuration of element Z", built from the periodic-table data
    const D=window.ptData, e=D.PT[z-1], w=[];
    for(const d of [1,-1,2,-2,3]){ const k=z+d; if(k>=1&&k<=118&&w.length<3) w.push(plain(D.cfg(k).full)); }
    return [2,'What is the full electron configuration of '+e.nm+' ('+e.sy+', Z = '+z+')?',plain(D.cfg(z).full)].concat(w);
  }
  function orbQ(z){   // "which orbital diagram is correct for element Z" – options are drawn diagrams
    const D=window.ptData, e=D.PT[z-1], R=D.orbDiag;
    const gs=k=>{ let n=0,r=[]; for(const o of D.ORD){ if(n>=k) break; const t=Math.min(D.CAP[o[1]],k-n); n+=t; r.push([o,{s:1,p:3,d:5,f:7}[o[1]],t]); } return r.sort((a,b)=>D.okey(a[0])-D.okey(b[0])); };
    const base=gs(z), L=base[base.length-1], ok=R(base), cand=[];
    if(L[1]>1&&L[2]>=2){ const a=Array(L[1]).fill(0); let r=L[2]; for(let i=0;i<L[1];i++){ const t=Math.min(2,r); a[i]=t; r-=t; } cand.push(R(base.slice(0,-1).concat([[L[0],L[1],a]]))); }   // breaks Hund's rule
    cand.push(R(gs(z+1)),R(gs(z-1)),R(gs(z+2)),R(gs(z-2)),R(gs(z+3)));
    const w=[]; for(const x of cand) if(x!==ok&&!w.includes(x)&&w.length<3) w.push(x);
    const q=[2,'Which orbital diagram is correct for '+e.nm+' ('+e.sy+', Z = '+z+')?',ok].concat(w); q.html=true; return q;
  }
  function newRun(){
    const zr=(a,b)=>Array.from({length:b-a+1},(_,i)=>elemQ(a+i));
    bE=QE.concat(zr(1,20)); bM=QM.concat(zr(21,40)); bH=QH.concat(zr(41,60),[5,6,7,8,9,10,12,14,15,16].map(orbQ));
    eDeck=shuf(bE.map((_,i)=>i)).slice(0,RUN_E); mDeck=shuf(bM.map((_,i)=>i)).slice(0,RUN_M); { const nb=bH.length-10, rg=(a,b)=>Array.from({length:b-a},(_,i)=>a+i);   // all 10 orbital-diagram questions + 10 others in each run
      hDeck=shuf(shuf(rg(nb,nb+10)).concat(shuf(rg(0,nb)).slice(0,RUN_H-10))); }
    QN=eDeck.length+mDeck.length+hDeck.length; qOk=0;
  }
  const shuf=a=>{ for(let i=a.length-1;i>0;i--){ const j=Math.floor(Math.random()*(i+1)); [a[i],a[j]]=[a[j],a[i]]; } return a; };
  function openQuiz(lv){
    pendingQ=false; quizOpen=true; duckHold=false;
    jokeOn=lv==='j'; const q=lv==='j'?QJ[0]:lv==='h'?bH[hDeck.pop()]:lv==='e'?bE[eDeck.pop()]:bM[mDeck.pop()];
    qKind.textContent=lv==='j'?'🏝️ Bonus joke!':lv==='h'?'🌊 Big wave! Hard question':lv==='e'?'🍡 Noodle cleared! Easy question':'🐦 Seagull dodged! Medium question';
    qCard.classList.toggle('hard',lv==='h'); qCard.classList.toggle('medium',lv==='m'); qCard.classList.toggle('easy',lv==='e'||lv==='j');
    qWk.textContent=lv==='j'?'Just for fun':'Week '+q[0]; qQ.textContent=q[1]; qFb.textContent=''; qNext.hidden=true; qOpts.innerHTML='';
    shuf(q.slice(2).map((t,i)=>({t,ok:i===0}))).forEach((o,i)=>{
      const b=document.createElement('button'), l=document.createElement('b'), tx=document.createElement('span');
      b.type='button'; b.dataset.ok=o.ok?'1':'0'; l.textContent='ABCD'[i]; if(q.html) tx.innerHTML=o.t; else tx.textContent=o.t;
      b.append(l,tx); b.onclick=()=>pickAns(b,o.ok); qOpts.appendChild(b);
    });
    qEl.classList.add('on');
  }
  function pickAns(b,ok){
    if(!jokeOn){ qAsked++; if(ok) qOk++; }
    [...qOpts.children].forEach(x=>{ x.disabled=true; if(x.dataset.ok==='1') x.classList.add('ok'); });
    if(!ok) b.classList.add('no');
    qFb.textContent=jokeOn?(ok?'Ha! Classic. 🦆 To get to the other side!':'Quack! The answer is: to get to the other side! 😄'):ok?'Correct! 🎉':'Not quite. The right answer is highlighted.';
    qNext.hidden=false; qNext.focus(); paint();
  }
  function closeQuiz(){ qEl.classList.remove('on'); quizOpen=false; }
  qNext.addEventListener('click',()=>{ closeQuiz(); qNext.blur(); if(mode==='play'&&!eDeck.length&&!mDeck.length&&!hDeck.length) victory(); });
  addEventListener('keydown',e=>{
    if(!quizOpen||!qNext.hidden||e.key.length!==1) return;
    const b=qOpts.children['abcd'.indexOf(e.key.toLowerCase())]; if(b) b.click();
  });
  function startWave(){ hardPending=true; wst='rise'; crestX=-140; wAmp=0; paint('🌊 Big wave! Hold on…'); }
  function afterClear(){
    const kind=pendingQ; pendingQ=false;
    if(!eDeck.length&&!mDeck.length&&!hDeck.length){ victory(); return; }
    if(kind==='gull'){ if(mDeck.length) openQuiz('m'); }   // seagull dodged → medium
    else if(eDeck.length) openQuiz('e');                  // noodle jumped → easy
  }
  function victory(){
    mode='beach'; beachT=0;
    noodles.forEach(n=>n.el.remove()); noodles=[];
    gulls.forEach(g=>g.el.remove()); gulls=[];
    wst='idle'; wAmp=0; crestX=-999; airborne=false; y=0; vy=0; over=false; pendingQ=false; hardPending=false;
    strip.classList.remove('playing'); btns.classList.remove('on');
    showBeach(true);
    hud.classList.add('on'); hb.hidden=false;
    paint('🏝️ You finished every question! Time to relax.');
    setTimeout(()=>{ if(mode==='beach'&&!hb.hidden&&!quizOpen) openQuiz('j'); },1500);
  }
  hb.addEventListener('click',()=>setMode('play'));
  window.duckGame={setMode:setMode};

  window.addEventListener('resize',resize);
  resize(); spawnX=W+40; setMode('review');
  requestAnimationFrame(t0=>{last=t0;frame(t0);});
})();
</script>
<script>
/* Island menu + science cover */
(function(){
  const btn=document.getElementById('islandBtn'), menu=document.getElementById('islandMenu');
  const items=[...menu.querySelectorAll('button')];
  const open=v=>{ menu.hidden=!v; btn.setAttribute('aria-expanded',v); };
  btn.addEventListener('click',e=>{ e.stopPropagation(); open(menu.hidden); });
  items.forEach(b=>b.addEventListener('click',()=>{
    if(window.duckGame) window.duckGame.setMode(b.dataset.mode);
    items.forEach(x=>x.setAttribute('aria-checked',x===b));
    open(false); b.blur(); btn.blur();
  }));
  document.addEventListener('click',e=>{ if(!menu.hidden && !menu.contains(e.target)) open(false); });
  document.addEventListener('keydown',e=>{ if(e.key==='Escape') open(false); });

  /* Science cover: sits over everything above the page header (site title link, stray DOCTYPE text).
     It is opaque and swallows clicks, so what is underneath can't be seen or clicked. */
  const head=document.querySelector('.header-container');
  const cover=document.createElement('div');
  cover.className='sci-cover'; cover.setAttribute('aria-hidden','true');
  cover.innerHTML='<i style="left:7%">H₂O</i><i style="left:19%">π</i><i style="right:19%">Δ</i><i style="right:7%">E=mc²</i>'+
    '<svg viewBox="0 0 64 64"><g class="orb" fill="none" stroke="#2E7D6B" stroke-width="1.6"><ellipse cx="32" cy="32" rx="28" ry="10"/><ellipse cx="32" cy="32" rx="28" ry="10" transform="rotate(60 32 32)"/><ellipse cx="32" cy="32" rx="28" ry="10" transform="rotate(120 32 32)"/><circle cx="60" cy="32" r="3" fill="#B5622E" stroke="none"/></g><circle cx="32" cy="32" r="5" fill="#B5622E"/></svg>'+
    '<div class="sci-cover-text"><b>Science Notes</b><small>Study Hub</small></div>';
  document.body.appendChild(cover);
  function fit(){
    const h=Math.round(head.getBoundingClientRect().top+window.scrollY);
    cover.style.height=h+'px'; cover.style.display=h>24?'flex':'none';
  }
  fit(); setTimeout(fit,300);
  addEventListener('load',fit); addEventListener('resize',fit);
  if(window.ResizeObserver) new ResizeObserver(fit).observe(document.body);

  /* Bottom cover: sits over the host's injected footer ("This site is open source. Improve this page").
     Opaque + swallows clicks so the link underneath can't be seen or clicked. */
  const foot=document.createElement('div');
  foot.className='sci-cover bottom'; foot.setAttribute('aria-hidden','true');
  foot.innerHTML='<i style="left:7%">λ</i><i style="left:19%">∑</i><i style="right:19%">∞</i><i style="right:7%">F=ma</i>'+
    '<svg viewBox="0 0 64 64"><g class="orb" fill="none" stroke="#2E7D6B" stroke-width="1.6"><ellipse cx="32" cy="32" rx="28" ry="10"/><ellipse cx="32" cy="32" rx="28" ry="10" transform="rotate(60 32 32)"/><ellipse cx="32" cy="32" rx="28" ry="10" transform="rotate(120 32 32)"/><circle cx="60" cy="32" r="3" fill="#B5622E" stroke="none"/></g><circle cx="32" cy="32" r="5" fill="#B5622E"/></svg>'+
    '<div class="sci-cover-text"><b>Keep Exploring</b><small>Science never stops</small></div>';
  foot.addEventListener('click',e=>{ e.preventDefault(); e.stopPropagation(); },true);
  document.body.appendChild(foot);
  function fitFoot(){
    foot.style.display='none';
    const total=Math.max(document.documentElement.scrollHeight,document.body.scrollHeight);
    const bodyBottom=Math.round(document.body.getBoundingClientRect().bottom+window.scrollY);
    // start a little above the end of the body so nothing peeks out, run to the very bottom of the page
    let top=Math.max(0,bodyBottom-24);
    let h=Math.max(total-top,64);
    foot.style.top=top+'px'; foot.style.height=h+'px'; foot.style.display='flex';
  }
  fitFoot(); setTimeout(fitFoot,300); setTimeout(fitFoot,1200); setTimeout(fitFoot,3000);
  addEventListener('load',fitFoot); addEventListener('resize',fitFoot);
  if(window.ResizeObserver){ const ro=new ResizeObserver(fitFoot); ro.observe(document.body); ro.observe(document.documentElement); }
  /* the host injects its footer after load, outside <body>: re-fit whenever anything is added to the page */
  if(window.MutationObserver) new MutationObserver(m=>{ if(m.some(r=>![...r.addedNodes].every(n=>n===foot||n===cover))) fitFoot(); })
    .observe(document.documentElement,{childList:true,subtree:false});
})();
</script>
</body>
</html>
