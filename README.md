<!doctype html>
<html lang="vi">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>GitHub Profile</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Sofia+Sans:wght@400;450;500;700&display=swap" rel="stylesheet">
<style>
  /* Thiết kế theo DESIGN.md: nền kem ấm, hình viên thuốc, chân dung tròn, đường quỹ đạo cam */
  :root {
    --canvas: #F3F0EE;
    --lifted: #FCFBFA;
    --white: #FFFFFF;
    --ink: #141413;
    --charcoal: #262627;
    --slate: #696969;
    --dust: #D1CDC7;
    --ghost: #E8E2DA;
    --signal: #CF4500;
    --orange: #F37338;
    --link: #3860BE;
    --sh1: rgba(0,0,0,.04) 0 4px 24px 0;
    --sh2: rgba(0,0,0,.08) 0 24px 48px 0;
  }
  * { box-sizing: border-box; margin: 0; padding: 0; }
  html { scroll-behavior: smooth; }
  body {
    background: var(--canvas);
    color: var(--ink);
    font-family: "Sofia Sans", Arial, sans-serif;
    font-weight: 450;
    font-size: 16px;
    line-height: 1.4;
    overflow-x: hidden;
  }
  a { color: inherit; text-decoration: none; }
  .wrap { max-width: 1240px; margin: 0 auto; padding: 0 48px; }

  /* ---------- Thanh điều hướng nổi ---------- */
  .nav {
    position: fixed; top: 24px; left: 50%; transform: translateX(-50%); z-index: 50;
    width: min(1144px, calc(100% - 32px));
    display: flex; align-items: center; justify-content: space-between; gap: 24px;
    background: rgba(255,255,255,.88); backdrop-filter: blur(14px);
    border-radius: 999px; padding: 12px 12px 12px 32px; box-shadow: var(--sh1);
    animation: navIn .9s cubic-bezier(.2,.8,.2,1) both;
  }
  @keyframes navIn { from { opacity: 0; transform: translate(-50%, -30px); } }
  .brand { display: flex; align-items: center; gap: 10px; font-weight: 700; font-size: 20px; letter-spacing: -.4px; }
  .brand i { width: 14px; height: 14px; border-radius: 50%; background: var(--orange); display: inline-block; }
  .links { display: flex; gap: 40px; }
  .links a { font-weight: 500; letter-spacing: -.48px; position: relative; padding: 4px 0; }
  .links a::after {
    content: ""; position: absolute; left: 0; right: 0; bottom: -2px; height: 1.5px; background: var(--ink);
    transform: scaleX(0); transform-origin: right; transition: transform .35s ease;
  }
  .links a:hover::after { transform: scaleX(1); transform-origin: left; }

  /* ---------- Nút ---------- */
  .btn {
    display: inline-flex; align-items: center; gap: 10px;
    font: 500 16px/1 "Sofia Sans", Arial, sans-serif; letter-spacing: -.32px;
    padding: 14px 26px; border-radius: 20px; border: 1.5px solid var(--ink);
    background: var(--ink); color: var(--canvas); cursor: pointer;
    transition: transform .2s ease, background .25s, color .25s;
  }
  .btn:active { transform: scale(.97); }
  .btn .arr { transition: transform .3s ease; }
  .btn:hover .arr { transform: translateX(4px); }
  .btn.ghost { background: var(--white); color: var(--ink); font-weight: 450; }
  .btn.ghost:hover { background: var(--ink); color: var(--canvas); }
  .nav .btn { padding: 12px 22px; }

  /* ---------- Nhãn nhỏ có chấm ---------- */
  .eyebrow {
    display: inline-flex; align-items: center; gap: 10px;
    font-size: 14px; font-weight: 700; letter-spacing: .56px; text-transform: uppercase; line-height: 1;
  }
  .eyebrow::before { content: ""; width: 8px; height: 8px; border-radius: 50%; background: var(--signal); }

  h1 { font-size: 64px; font-weight: 500; line-height: 1; letter-spacing: -1.28px; }
  h2 { font-size: 36px; font-weight: 500; line-height: 44px; letter-spacing: -.72px; }
  h3 { font-size: 24px; font-weight: 500; line-height: 1.2; letter-spacing: -.48px; }

  /* ---------- Hero ---------- */
  .hero { position: relative; min-height: 100vh; display: flex; align-items: center; padding: 140px 0 80px; }
  .ghost-word {
    position: absolute; left: -2vw; bottom: 4vh; z-index: 0; pointer-events: none; white-space: nowrap;
    font-size: clamp(160px, 28vw, 420px); font-weight: 500; letter-spacing: -.04em; line-height: .8;
    color: var(--ghost); will-change: transform;
  }
  .hero-grid { position: relative; z-index: 1; width: 100%; display: grid; grid-template-columns: 1.1fr .9fr; gap: 48px; align-items: center; }
  .hero h1 { margin: 24px 0 24px; }
  .hero h1 .nm { display: block; font-size: clamp(72px, 10vw, 128px); letter-spacing: -.03em; }
  .typed { font-size: 20px; color: var(--charcoal); min-height: 28px; }
  .typed .cur { display: inline-block; width: 2px; height: 22px; background: var(--signal); margin-left: 3px; vertical-align: -4px; animation: blink 1s steps(1) infinite; }
  @keyframes blink { 50% { opacity: 0; } }
  .meta { display: flex; flex-wrap: wrap; gap: 10px; margin-top: 28px; }
  .chip { background: var(--white); border-radius: 999px; padding: 8px 18px; font-size: 14px; color: var(--charcoal); }
  .cta { display: flex; flex-wrap: wrap; gap: 12px; margin-top: 36px; }

  /* Chân dung tròn + quỹ đạo */
  .portrait-zone { position: relative; width: 100%; max-width: 460px; aspect-ratio: 1; justify-self: center; }
  .orbit { position: absolute; inset: -14%; width: 128%; height: 128%; overflow: visible; }
  .orbit .path { fill: none; stroke: var(--orange); stroke-width: 1.4; stroke-dasharray: 1600; stroke-dashoffset: 1600; animation: draw 2.4s .4s cubic-bezier(.6,.1,.2,1) forwards; }
  .orbit .path.p2 { stroke-width: 1; opacity: .55; animation-delay: .9s; }
  @keyframes draw { to { stroke-dashoffset: 0; } }
  .spin { transform-origin: 50% 50%; animation: spin 26s linear infinite; }
  .spin.rev { animation-duration: 40s; animation-direction: reverse; }
  @keyframes spin { to { transform: rotate(360deg); } }
  .portrait {
    position: absolute; inset: 9%; border-radius: 50%; overflow: hidden; background: var(--lifted);
    box-shadow: var(--sh2); animation: pop 1.1s .2s cubic-bezier(.2,.9,.2,1.15) both;
  }
  .portrait img { width: 100%; height: 100%; object-fit: cover; display: block; transition: transform .8s ease; }
  .portrait-zone:hover .portrait img { transform: scale(1.06); }
  @keyframes pop { from { opacity: 0; transform: scale(.7); } }
  .satellite {
    position: absolute; right: 8%; bottom: 10%; width: 72px; height: 72px; border-radius: 50%;
    background: var(--white); display: grid; place-items: center; font-size: 26px; z-index: 2;
    box-shadow: var(--sh1); transition: transform .3s ease, background .3s, color .3s;
    animation: pop .8s 1.2s cubic-bezier(.2,.9,.2,1.3) both;
  }
  .satellite:hover { background: var(--ink); color: var(--canvas); transform: rotate(-45deg); }
  .moon { position: absolute; width: 18px; height: 18px; border-radius: 50%; background: var(--orange); }

  /* ---------- Thống kê ---------- */
  .stats { display: grid; grid-template-columns: repeat(4, 1fr); gap: 16px; }
  .stat { background: var(--lifted); border-radius: 999px; padding: 26px 32px; display: flex; align-items: baseline; gap: 14px; justify-content: center; }
  .stat .num { font-size: 44px; font-weight: 500; letter-spacing: -1px; line-height: 1; }
  .stat .lbl { color: var(--slate); font-size: 15px; }

  /* ---------- Section ---------- */
  section.block { padding: 120px 0 0; }
  .head { display: grid; grid-template-columns: 1fr 1fr; gap: 48px; align-items: end; margin-bottom: 56px; }
  .head h2 { margin-top: 18px; }
  .head p { color: var(--slate); max-width: 440px; justify-self: end; }

  /* Kỹ năng: chòm sao các vòng tròn */
  .constellation { position: relative; display: flex; flex-wrap: wrap; justify-content: center; gap: 28px 40px; padding: 20px 0; }
  .constellation svg.arcs { position: absolute; inset: 0; width: 100%; height: 100%; pointer-events: none; overflow: visible; }
  .constellation svg.arcs path { fill: none; stroke: var(--orange); stroke-width: 1.2; stroke-dasharray: 6 8; opacity: .7; animation: dash 30s linear infinite; }
  @keyframes dash { to { stroke-dashoffset: -600; } }
  .skill {
    position: relative; z-index: 1; width: 148px; height: 148px; border-radius: 50%; background: var(--white);
    display: flex; flex-direction: column; align-items: center; justify-content: center; gap: 10px;
    font-weight: 500; font-size: 18px; letter-spacing: -.36px; box-shadow: var(--sh1);
    transition: transform .4s cubic-bezier(.2,.8,.2,1), box-shadow .4s;
  }
  .skill:nth-child(odd) { margin-top: 56px; }
  .skill .ic { width: 40px; height: 40px; border-radius: 50%; display: grid; place-items: center; color: #fff; font-size: 13px; font-weight: 700; }
  .skill:hover { transform: translateY(-10px) scale(1.05); box-shadow: var(--sh2); }
  .floaty { animation: floaty 6s ease-in-out infinite; }
  @keyframes floaty { 50% { translate: 0 -10px; } }

  /* Ngôn ngữ */
  .langbar { display: flex; height: 16px; border-radius: 999px; overflow: hidden; background: var(--white); margin-top: 48px; }
  .langbar div { width: 0; transition: width 1.4s cubic-bezier(.2,.8,.2,1); }
  .langlist { display: flex; flex-wrap: wrap; gap: 10px; margin-top: 16px; }

  /* Dự án */
  .projects { display: grid; grid-template-columns: repeat(auto-fill, minmax(340px, 1fr)); gap: 20px; }
  .card {
    position: relative; background: var(--lifted); border-radius: 40px; padding: 36px 36px 32px;
    display: flex; flex-direction: column; gap: 16px; min-height: 280px;
    transition: transform .45s cubic-bezier(.2,.8,.2,1), box-shadow .45s, background .3s;
  }
  .card:hover { transform: translateY(-8px); box-shadow: var(--sh2); background: var(--white); }
  .card .top { display: flex; align-items: center; justify-content: space-between; }
  .card .badge { width: 56px; height: 56px; border-radius: 50%; display: grid; place-items: center; color: #fff; font-weight: 700; font-size: 18px; }
  .card .go {
    width: 52px; height: 52px; border-radius: 50%; border: 1px solid var(--ink); display: grid; place-items: center; font-size: 20px;
    transition: background .3s, color .3s, transform .4s;
  }
  .card:hover .go { background: var(--ink); color: var(--canvas); transform: rotate(-45deg); }
  .card p { color: var(--slate); flex: 1; }
  .card .foot { display: flex; gap: 8px; flex-wrap: wrap; }
  .card .foot .chip { background: var(--canvas); }

  /* Hoạt động */
  .stadium { background: var(--white); border-radius: 40px; padding: 40px; overflow-x: auto; }
  .stadium img { display: block; min-width: 720px; width: 100%; }

  /* ---------- Footer ---------- */
  footer { background: var(--ink); color: #fff; margin-top: 140px; border-radius: 40px 40px 0 0; padding: 96px 0 64px; }
  footer h2 { font-size: clamp(36px, 5vw, 64px); line-height: 1.05; letter-spacing: -.02em; max-width: 760px; }
  .fgrid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 32px; margin-top: 72px; }
  .fgrid h5 { font-size: 13px; font-weight: 700; letter-spacing: .56px; text-transform: uppercase; color: #9a9a96; margin-bottom: 16px; }
  .fgrid a { display: block; font-size: 15px; padding: 6px 0; opacity: .9; transition: opacity .2s, transform .2s; }
  .fgrid a:hover { opacity: 1; transform: translateX(4px); }
  .fbottom { border-top: 1px solid rgba(255,255,255,.2); margin-top: 64px; padding-top: 24px; display: flex; justify-content: space-between; color: #9a9a96; font-size: 14px; flex-wrap: wrap; gap: 12px; }
  footer .btn { background: var(--canvas); color: var(--ink); border-color: var(--canvas); margin-top: 36px; }

  /* ---------- Hiện dần khi cuộn ---------- */
  .reveal { opacity: 0; transform: translateY(48px); transition: opacity .9s ease, transform .9s cubic-bezier(.2,.8,.2,1); }
  .reveal.show { opacity: 1; transform: none; }

  /* ---------- Tải / nhập tên ---------- */
  .center { min-height: 100vh; display: grid; place-items: center; text-align: center; padding: 16px; }
  .loader { width: 64px; height: 64px; border-radius: 50%; border: 1.5px solid var(--dust); border-top-color: var(--orange); animation: spin 1s linear infinite; margin: 0 auto 20px; }
  .ask input { font: inherit; font-size: 18px; padding: 14px 24px; border-radius: 999px; border: 1px solid rgba(20,20,19,.5); background: #fff; width: min(360px, 85vw); margin: 24px 0 16px; outline: none; }
  .ask input:focus { border-color: var(--ink); }
  .err { color: var(--signal); margin-top: 12px; }

  @media (max-width: 1023px) {
    .links { display: none; }
    .hero-grid { grid-template-columns: 1fr; text-align: center; }
    .hero-grid .meta, .hero-grid .cta { justify-content: center; }
    .portrait-zone { max-width: 340px; grid-row: 1; }
    .stats { grid-template-columns: repeat(2, 1fr); }
    .head { grid-template-columns: 1fr; }
    .head p { justify-self: start; }
  }
  @media (max-width: 767px) {
    .wrap { padding: 0 16px; }
    .nav { padding: 8px 8px 8px 22px; top: 16px; }
    .hero { padding-top: 120px; }
    .portrait-zone { max-width: 260px; margin: 24px auto 16px; }
    h2 { font-size: 30px; line-height: 36px; }
    .stats { grid-template-columns: 1fr 1fr; gap: 10px; }
    .stat { flex-direction: column; align-items: center; gap: 4px; padding: 20px; border-radius: 40px; }
    .stat .num { font-size: 34px; }
    .skill { width: 116px; height: 116px; font-size: 15px; }
    .skill:nth-child(odd) { margin-top: 0; }
    .constellation svg.arcs { display: none; }
    .projects { grid-template-columns: 1fr; }
    .card { border-radius: 32px; padding: 28px; }
    .stadium { padding: 24px; border-radius: 32px; }
    .fgrid { grid-template-columns: 1fr; }
    section.block { padding-top: 80px; }
  }
  @media (prefers-reduced-motion: reduce) {
    *, *::before, *::after { animation: none !important; transition: none !important; }
    .reveal { opacity: 1; transform: none; }
    .orbit .path { stroke-dashoffset: 0; }
  }
</style>
</head>
<body>
<div id="app"></div>

<script>
// ====== ĐIỀN TÊN TÀI KHOẢN GITHUB CỦA BẠN VÀO ĐÂY ======
const DEFAULT_USER = "Tuankiet-laptrinh";

// ====== TỰ THIẾT KẾ HỒ SƠ (để trống "" thì lấy từ GitHub) ======
const PROFILE = {
  name: "Kiệt",                       // Tên hiển thị lớn
  greeting: "Xin chào, tôi là",       // Dòng chữ nhỏ phía trên tên
  location: "Việt Nam",
  typed: [                            // Các câu tự gõ dưới tên
    "Sinh viên đang học lập trình 💻",
    "Code · Learn · Build 🚀"
  ],
  skills: ["HTML", "CSS", "JavaScript", "PHP", "Java", "C++"],
  // Dự án tự thêm, hiện cùng repo GitHub. link có thể để ""
  projects: [
    { name: "Bản đồ Việt Nam", desc: "Trang web bản đồ tương tác các tỉnh thành Việt Nam.", lang: "JavaScript", link: "" },
    { name: "Web giải thuật", desc: "Giao diện web minh hoạ các thuật toán sắp xếp và tìm kiếm.", lang: "HTML", link: "" },
  ]
};
// =======================================================

const LANG_COLORS = {
  JavaScript:"#E8B10E", TypeScript:"#3178c6", Python:"#3572A5", Java:"#b07219", "C#":"#178600",
  "C++":"#f34b7d", C:"#555555", PHP:"#4F5D95", HTML:"#e34c26", CSS:"#563d7c", SCSS:"#c6538c",
  Go:"#00ADD8", Rust:"#dea584", Kotlin:"#A97BFF", Swift:"#F05138", Dart:"#00B4AB", Ruby:"#701516",
  Vue:"#41b883", Shell:"#5a9e2a", "Jupyter Notebook":"#DA5B0B", Svelte:"#ff3e00", Lua:"#000080"
};
const SHORT = { JavaScript:"JS", TypeScript:"TS", Python:"Py", "C++":"C++", "C#":"C#", HTML:"</>", CSS:"{ }", PHP:"php" };
const app = document.getElementById("app");
const esc = s => String(s ?? "").replace(/[&<>"']/g, c => ({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c]));
const color = l => LANG_COLORS[l] || "#696969";
const short = l => SHORT[l] || String(l).slice(0, 2);

/* ---------- Màn hình nhập tên ---------- */
function askUser(msg){
  app.innerHTML = `
    <div class="center ask">
      <div>
        <span class="eyebrow">GitHub profile</span>
        <h1 style="margin-top:20px">Nhập tên GitHub</h1>
        <form id="f"><input id="u" placeholder="ví dụ: torvalds" autofocus><br>
        <button class="btn" type="submit">Xem hồ sơ <span class="arr">→</span></button></form>
        ${msg ? `<div class="err">${esc(msg)}</div>` : ""}
      </div>
    </div>`;
  document.getElementById("f").onsubmit = e => {
    e.preventDefault();
    const u = document.getElementById("u").value.trim();
    if (u) { history.replaceState(null, "", "?user=" + encodeURIComponent(u)); load(u); }
  };
}

/* ---------- Tải dữ liệu ---------- */
async function load(user){
  app.innerHTML = `<div class="center"><div><div class="loader"></div><div style="color:var(--slate)">Đang tải @${esc(user)}…</div></div></div>`;
  try {
    const [uRes, rRes] = await Promise.all([
      fetch(`https://api.github.com/users/${encodeURIComponent(user)}`),
      fetch(`https://api.github.com/users/${encodeURIComponent(user)}/repos?per_page=100&sort=updated`)
    ]);
    if (uRes.status === 404) return askUser(`Không tìm thấy tài khoản "${user}".`);
    if (!uRes.ok) throw new Error("rate limit");
    render(await uRes.json(), rRes.ok ? await rRes.json() : []);
  } catch (e) {
    // GitHub API lỗi hoặc hết lượt: vẫn hiện trang bằng thông tin tự khai báo
    render({ login: user, avatar_url: `https://github.com/${encodeURIComponent(user)}.png`, html_url: `https://github.com/${encodeURIComponent(user)}`,
             followers: 0, following: 0, public_repos: 0, created_at: null }, []);
  }
}

/* ---------- Dựng trang ---------- */
function render(u, repos){
  // Bỏ repo fork và repo README hồ sơ (trùng tên tài khoản)
  const own = repos.filter(r => !r.fork && r.name.toLowerCase() !== u.login.toLowerCase());
  const stars = own.reduce((s,r) => s + r.stargazers_count, 0);
  const langCount = {};
  own.forEach(r => { if (r.language) langCount[r.language] = (langCount[r.language]||0) + 1; });
  const langs = Object.entries(langCount).sort((a,b)=>b[1]-a[1]);
  const totalL = langs.reduce((s,[,n])=>s+n,0) || 1;
  const top = [...own].sort((a,b) => (b.stargazers_count - a.stargazers_count) || (new Date(b.pushed_at) - new Date(a.pushed_at))).slice(0, 9);
  const custom = (PROFILE.projects || []).map(p => ({
    name: p.name, description: p.desc, language: p.lang, html_url: p.link || u.html_url, stargazers_count: null, forks_count: null
  }));
  const cards = [...custom, ...top];
  const skills = PROFILE.skills?.length ? PROFILE.skills : langs.map(([l]) => l);
  const displayName = PROFILE.name || u.name || u.login;
  const location = PROFILE.location || u.location;
  const year = u.created_at ? new Date(u.created_at).getFullYear() : "";
  document.title = `${displayName} · GitHub`;

  app.innerHTML = `
  <nav class="nav">
    <a class="brand" href="#top"><i></i>${esc(displayName)}</a>
    <div class="links">
      <a href="#skills">Kỹ năng</a><a href="#projects">Dự án</a><a href="#activity">Hoạt động</a>
    </div>
    <a class="btn" href="${esc(u.html_url)}" target="_blank">GitHub <span class="arr">↗</span></a>
  </nav>

  <header class="hero" id="top">
    <div class="ghost-word" id="ghost">${esc(displayName)}</div>
    <div class="wrap hero-grid">
      <div class="reveal">
        <span class="eyebrow">${esc(PROFILE.greeting || "Xin chào, tôi là")}</span>
        <h1><span class="nm">${esc(displayName)}</span></h1>
        <div class="typed"><span id="typed"></span><span class="cur"></span></div>
        <div class="meta">
          <span class="chip">@${esc(u.login)}</span>
          ${location ? `<span class="chip">📍 ${esc(location)}</span>` : ""}
          ${u.company ? `<span class="chip">🏢 ${esc(u.company)}</span>` : ""}
          ${year ? `<span class="chip">Tham gia GitHub ${year}</span>` : ""}
        </div>
        <div class="cta">
          <a class="btn" href="#projects">Xem dự án <span class="arr">→</span></a>
          <a class="btn ghost" href="${esc(u.html_url)}" target="_blank">Hồ sơ GitHub</a>
        </div>
      </div>
      <div class="portrait-zone">
        <svg class="orbit" viewBox="0 0 400 400">
          <g class="spin"><path class="path" d="M200 18 C 320 22, 386 110, 382 205 C 378 300, 300 384, 196 382 C 92 380, 16 300, 20 196 C 24 96, 100 16, 200 18"/>
            <circle cx="382" cy="205" r="7" fill="#F37338"/></g>
          <g class="spin rev"><path class="path p2" d="M30 120 C 120 -10, 330 -20, 392 140"/>
            <circle cx="30" cy="120" r="4.5" fill="#141413"/></g>
        </svg>
        <div class="portrait"><img src="${esc(u.avatar_url)}" alt="${esc(displayName)}"></div>
        <a class="satellite" href="${esc(u.html_url)}" target="_blank" aria-label="Mở GitHub">→</a>
      </div>
    </div>
  </header>

  <div class="wrap">
    <div class="stats">
      ${[["Dự án", own.length + custom.length],["Kỹ năng", skills.length],["Followers", u.followers],["Stars", stars]]
        .map(([l,n]) => `<div class="stat reveal"><span class="num" data-to="${n}">0</span><span class="lbl">${l}</span></div>`).join("")}
    </div>

    ${skills.length ? `
    <section class="block" id="skills">
      <div class="head reveal">
        <div><span class="eyebrow">Kỹ năng</span><h2>Những công cụ tôi dùng hằng ngày</h2></div>
        <p>Các ngôn ngữ và công nghệ tôi đã học và dùng trong các dự án ở trường lẫn tự làm.</p>
      </div>
      <div class="constellation reveal" id="cons">
        <svg class="arcs" id="arcs"></svg>
        ${skills.map((s,i) => `<div class="skill floaty" style="animation-delay:${-i*1.1}s">
            <span class="ic" style="background:${color(s)}">${esc(short(s))}</span>${esc(s)}</div>`).join("")}
      </div>
      ${langs.length ? `
      <div class="reveal">
        <div class="langbar">${langs.map(([l,n]) => `<div data-w="${n/totalL*100}" style="background:${color(l)}" title="${esc(l)}"></div>`).join("")}</div>
        <div class="langlist">${langs.map(([l,n]) => `<span class="chip">${esc(l)} · ${Math.round(n/totalL*100)}%</span>`).join("")}</div>
      </div>` : ""}
    </section>` : ""}

    ${cards.length ? `
    <section class="block" id="projects">
      <div class="head reveal">
        <div><span class="eyebrow">Dự án</span><h2>Những thứ tôi đã xây dựng</h2></div>
        <p>${cards.length} dự án, từ bài tập trên lớp đến những ý tưởng tôi tự làm cho vui.</p>
      </div>
      <div class="projects">
        ${cards.map(r => `
          <a class="card reveal" href="${esc(r.html_url)}" target="_blank">
            <div class="top">
              <span class="badge" style="background:${color(r.language)}">${esc(short(r.language || "··"))}</span>
              <span class="go">→</span>
            </div>
            <h3>${esc(r.name)}</h3>
            <p>${esc(r.description || "Chưa có mô tả.")}</p>
            <div class="foot">
              ${r.language ? `<span class="chip">${esc(r.language)}</span>` : ""}
              ${r.stargazers_count != null ? `<span class="chip">★ ${r.stargazers_count}</span><span class="chip">⑂ ${r.forks_count}</span>` : ""}
            </div>
          </a>`).join("")}
      </div>
    </section>` : ""}

    <section class="block reveal" id="activity">
      <div class="head">
        <div><span class="eyebrow">Hoạt động</span><h2>Một năm viết code</h2></div>
        <p>Mỗi ô là một ngày, màu càng đậm là ngày đó tôi code càng nhiều.</p>
      </div>
      <div class="stadium"><img src="https://ghchart.rshah.org/F37338/${encodeURIComponent(u.login)}" alt="Biểu đồ đóng góp" onerror="this.closest('section').remove()"></div>
    </section>
  </div>

  <footer>
    <div class="wrap">
      <span class="eyebrow" style="color:#9a9a96">Liên hệ</span>
      <h2 style="margin-top:20px">Cùng nhau xây dựng điều gì đó thật hay nhé.</h2>
      <a class="btn" href="${esc(u.html_url)}" target="_blank">Theo dõi tôi trên GitHub <span class="arr">↗</span></a>
      <div class="fgrid">
        <div><h5>Trang này</h5><a href="#skills">Kỹ năng</a><a href="#projects">Dự án</a><a href="#activity">Hoạt động</a></div>
        <div><h5>GitHub</h5><a href="${esc(u.html_url)}" target="_blank">Hồ sơ ↗</a><a href="${esc(u.html_url)}?tab=repositories" target="_blank">Repositories ↗</a><a href="${esc(u.html_url)}?tab=stars" target="_blank">Stars ↗</a></div>
        <div><h5>Về tôi</h5><a href="#top">${esc(displayName)}</a>${location ? `<a href="#top">${esc(location)}</a>` : ""}</div>
      </div>
      <div class="fbottom"><span>© ${new Date().getFullYear()} ${esc(displayName)}</span><span>Dữ liệu lấy trực tiếp từ GitHub</span></div>
    </div>
  </footer>`;

  // Chữ tự gõ
  const lines = PROFILE.typed?.length ? PROFILE.typed : [u.bio, "Code · Learn · Build 🚀"].filter(Boolean);
  typeLoop(document.getElementById("typed"), lines);

  // Hiện dần khi cuộn
  const io = new IntersectionObserver(es => es.forEach(e => {
    if (!e.isIntersecting) return;
    const el = e.target;
    el.classList.add("show");
    el.querySelectorAll(".langbar div").forEach(d => d.style.width = d.dataset.w + "%");
    const num = el.querySelector(".num"); if (num) countUp(num);
    io.unobserve(el);
  }), { threshold: .15 });
  document.querySelectorAll(".reveal").forEach((el, i) => { el.style.transitionDelay = (i % 3) * 100 + "ms"; io.observe(el); });

  // Chữ mờ phía sau trôi theo cuộn
  const ghost = document.getElementById("ghost");
  addEventListener("scroll", () => { ghost.style.transform = `translateX(${scrollY * -0.25}px)`; }, { passive: true });

  // Đường quỹ đạo nối các vòng tròn kỹ năng
  drawArcs();
  addEventListener("resize", drawArcs);
}

function drawArcs(){
  const cons = document.getElementById("cons"), svg = document.getElementById("arcs");
  if (!cons || !svg) return;
  const box = cons.getBoundingClientRect();
  const pts = [...cons.querySelectorAll(".skill")].map(s => {
    const r = s.getBoundingClientRect();
    return [r.left - box.left + r.width / 2, r.top - box.top + r.height / 2];
  });
  let d = "";
  for (let i = 1; i < pts.length; i++) {
    const [x1,y1] = pts[i-1], [x2,y2] = pts[i];
    const bend = (i % 2 ? -1 : 1) * 60;
    d += `M${x1} ${y1} Q ${(x1+x2)/2} ${(y1+y2)/2 + bend} ${x2} ${y2} `;
  }
  svg.innerHTML = `<path d="${d}"/>`;
}

function countUp(el){
  const to = +el.dataset.to, t0 = performance.now(), dur = 1400;
  (function step(t){
    const p = Math.min(1, (t - t0) / dur), e = 1 - Math.pow(1 - p, 3);
    el.textContent = Math.round(to * e).toLocaleString("vi-VN");
    if (p < 1) requestAnimationFrame(step);
  })(t0);
}

function typeLoop(el, lines){
  let li = 0, ci = 0, del = false;
  (function tick(){
    const s = lines[li];
    el.textContent = s.slice(0, ci);
    if (!del && ci < s.length) { ci++; setTimeout(tick, 50); }
    else if (!del) { del = true; setTimeout(tick, 1800); }
    else if (ci > 0) { ci--; setTimeout(tick, 22); }
    else { del = false; li = (li + 1) % lines.length; setTimeout(tick, 300); }
  })();
}

const qUser = new URLSearchParams(location.search).get("user") || DEFAULT_USER;
qUser ? load(qUser) : askUser();
</script>
</body>
</html>

