<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>I LOVE YOU</title>
<style>
  :root{
    --wine:#2b0a1e;
    --plum:#4a1233;
    --rose:#ff4f7b;
    --blush:#ffd9e2;
    --gold:#f6c177;
  }
  *{box-sizing:border-box;margin:0;padding:0}
  html,body{height:100%}
  body{
    background:radial-gradient(ellipse at 50% 30%, var(--plum), var(--wine) 70%);
    color:var(--blush);
    font-family:"Segoe UI","Noto Naskh Arabic",Tahoma,sans-serif;
    display:flex;align-items:center;justify-content:center;
    overflow-x:hidden;
  }
  .screen{width:100%;max-width:420px;padding:24px;text-align:center}
  h1{
    font-family:Georgia,"Times New Roman",serif;
    font-style:italic;
    font-weight:400;
    font-size:clamp(2.2rem,9vw,3.2rem);
    letter-spacing:.04em;
    direction:ltr;
    margin:8px 0 6px;
  }
  .sub{opacity:.75;margin-bottom:28px;font-size:1rem}

  /* heart lock */
  .heart{width:150px;height:140px;margin:0 auto;display:block;overflow:visible}
  .heart path{fill:transparent;stroke:var(--rose);stroke-width:3;transition:fill .8s ease, filter .8s ease}
  .heart.open path{fill:var(--rose);filter:drop-shadow(0 0 22px var(--rose))}
  .heart.open{animation:beat 1.1s ease-in-out infinite}
  @keyframes beat{0%,100%{transform:scale(1)}15%{transform:scale(1.12)}30%{transform:scale(1)}45%{transform:scale(1.08)}}

  form{display:flex;gap:10px;margin-top:6px}
  input{
    flex:1;min-width:0;
    padding:14px 16px;border-radius:12px;
    border:1.5px solid rgba(255,217,226,.35);
    background:rgba(255,255,255,.06);
    color:var(--blush);font-size:1.1rem;text-align:center;
    letter-spacing:.2em;direction:ltr;
  }
  input::placeholder{letter-spacing:normal;color:rgba(255,217,226,.45)}
  input:focus-visible,button:focus-visible{outline:3px solid var(--gold);outline-offset:2px}
  button{
    padding:14px 22px;border:0;border-radius:12px;
    background:var(--rose);color:#fff;font-size:1rem;font-weight:600;cursor:pointer;
  }
  button:hover{filter:brightness(1.08)}
  .error{min-height:1.5em;margin-top:12px;color:var(--gold);font-size:.95rem}
  .shake{animation:shake .4s}
  @keyframes shake{0%,100%{transform:translateX(0)}25%{transform:translateX(-8px)}75%{transform:translateX(8px)}}

  /* unlocked */
  #content{display:none}
  .message{
    margin-top:26px;font-size:1.25rem;line-height:2;
    animation:fade 1.6s ease both;
  }
  @keyframes fade{from{opacity:0}to{opacity:1}}

  .float{position:fixed;bottom:-40px;pointer-events:none;color:var(--rose);opacity:.8;animation:rise linear forwards}
  @keyframes rise{to{transform:translateY(-110vh) rotate(25deg);opacity:0}}

  @media (prefers-reduced-motion:reduce){
    .heart.open,.shake,.message{animation:none}
    .float{display:none}
  }
</style>
</head>
<body>

<main class="screen">
  <svg id="heart" class="heart" viewBox="0 0 100 92" aria-hidden="true">
    <path d="M50 88 C12 58 4 36 4 24 C4 11 14 3 26 3 C36 3 45 9 50 18 C55 9 64 3 74 3 C86 3 96 11 96 24 C96 36 88 58 50 88 Z"/>
  </svg>

  <h1>I LOVE YOU</h1>

  <section id="gate">
    <p class="sub">أدخلي كلمة السر للدخول</p>
    <form id="form" autocomplete="off">
      <input id="pw" type="password" placeholder="كلمة السر" aria-label="كلمة السر" autofocus>
      <button type="submit">دخول</button>
    </form>
    <p id="error" class="error" role="alert"></p>
  </section>

  <section id="content">
    <p class="message">
      أنتِ أجمل ما حدث لي.<br>
      كل يوم معكِ يشبه البداية من جديد.<br>
      أحبكِ.
    </p>
  </section>
</main>

<script>
  const PASSWORD = "LOVE";
  const form = document.getElementById("form");
  const pw = document.getElementById("pw");
  const err = document.getElementById("error");
  const heart = document.getElementById("heart");

  form.addEventListener("submit", e => {
    e.preventDefault();
    if (pw.value.trim().toUpperCase() === PASSWORD) {
      document.getElementById("gate").style.display = "none";
      document.getElementById("content").style.display = "block";
      heart.classList.add("open");
      for (let i = 0; i < 24; i++) setTimeout(spawn, i * 180);
    } else {
      err.textContent = "كلمة السر غير صحيحة، حاولي مرة أخرى.";
      form.classList.remove("shake");
      void form.offsetWidth;
      form.classList.add("shake");
      pw.select();
    }
  });

  function spawn() {
    const h = document.createElement("div");
    h.className = "float";
    h.textContent = "♥";
    h.style.left = Math.random() * 100 + "vw";
    h.style.fontSize = 14 + Math.random() * 26 + "px";
    h.style.animationDuration = 5 + Math.random() * 5 + "s";
    document.body.appendChild(h);
    setTimeout(() => h.remove(), 11000);
  }
</script>
</body>
</html>
# I-LOVE-YUO
MY IOVE
